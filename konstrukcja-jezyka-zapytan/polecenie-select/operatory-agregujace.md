# Operatory agregujące i funkcje wyrażeń

## Agregaty okna (MIN, MAX, AVG, SUMC)

Operatory agregujące działają na strumieniu posiadającym wiele pól — typowo strumieniu wynikowym operatora `@(k,w)` (okno danych). Redukują wszystkie pola rekordu do jednej wartości.

### Składnia

```
FROM AGREGATOR(wyrażenie_strumieniowe)
```

gdzie `AGREGATOR` to jedno z:

| Słowo kluczowe | Działanie |
|----------------|-----------|
| `min`  / `MIN` | minimum ze wszystkich pól rekordu |
| `max`  / `MAX` | maksimum ze wszystkich pól rekordu |
| `avg`  / `AVG` | średnia arytmetyczna pól rekordu |
| `sumc` / `SUMC`| suma wszystkich pól rekordu |

Słowa kluczowe akceptowane są zarówno małymi, jak i wielkimi literami. Są zastrzeżone, dlatego strumień nie może nazywać się `min`, `MAX`, `avg` ani `SUMC`.

Argumentem może być całe wyrażenie strumieniowe, nie tylko pojedyncza nazwa. Dzięki temu okno i redukcję można zapisać bez pomocniczego zapytania:

```rql
SELECT * STREAM total FROM SUMC(src@(1,5))
```

Postać przyrostkowa `strumień.min`, `.max`, `.avg` i `.sumc` pozostaje zgodna wstecz, ale jest wygaszana. Parser emituje ostrzeżenie i zaleca postać funkcyjną. Dotychczasowy zapis `src@(1,5).sumc` jest poprawny, lecz nowe zapytania powinny używać `SUMC(src@(1,5))`.

### Interwał wyjściowy

Agregaty nie zmieniają częstotliwości strumienia — interwał wyniku jest taki sam jak źródła:

\\[\Delta_{wynik} = \Delta_{strumień}\\]

### Typ wyniku

Wszystkie cztery reduktory dają pole typu `RATIONAL`, niezależnie od typu pól wejściowych.
Dotyczy to także `MIN` i `MAX`, które zwracają wartość obecną w rekordzie, oraz przypadku,
w którym wynik jest liczbą całkowitą — średnia z trzech siódemek to pole `RATIONAL`
o wartości `7/1`, a nie pole `INTEGER`.

Wybór typu nie jest kosmetyczny: rachunek redukcji idzie po liczbach wymiernych, więc
`AVG` nie traci reszty z dzielenia, a wynik pozostaje dokładny. Kosztem jest to, że
artefakt z agregatem wymaga od czytelnika znajomości układu pary licznik-mianownik
(→ [Układ pola RATIONAL](../../architektura-systemu-przetwarzania-danych/format-zapisu-danych/pliki.md#układ-pola-rational))
albo przepuszczenia wartości przez `to_string`, `to_double` lub `to_integer`.

### Przykład: średnia ruchoma

```
DECLARE val INTEGER STREAM src, 1 FILE 'data.txt'

-- okno 5-elementowe przesuwane o 1
-- średnia z okna 5-elementowego przesuwanego o 1
SELECT * STREAM ma5 FROM AVG(src@(1,5))
```

Strumień `ma5` zawiera w każdej chwili średnią z pięciu kolejnych próbek `src`.

### Przykład: filtr sygnałowy (sumc)

Fragment z przykładu implementacji filtru sygnałowego:

```rql
SELECT source[_] * filter[_] STREAM accRow FROM source@(1,25)+filter
SELECT accRow[0] STREAM output FROM SUMC(accRow)
```

Okno znajduje się bezpośrednio w `FROM`, więc nie wymaga osobnego zapytania. `source[_]` rozwija się zgodnie z 25 slotami, które `source@(1,25)` wnosi do rekordu wejściowego. `SUMC(accRow)` sumuje wszystkie pola rekordu `accRow` — iloczyny próbek sygnału przez współczynniki filtru — produkując wyjście filtru FIR.

### Przykład: MIN i MAX

```
DECLARE v INTEGER STREAM src, 0.1 FILE '/dev/urandom'
SELECT * STREAM min10 FROM MIN(src@(1,10))
SELECT * STREAM max10 FROM MAX(src@(1,10))
```

> **_NOTE:_** Opisana funkcjonalność ma pokrycie w testach: `simple_max`, `Pattern4` opisanych w załączniku pt. [Testy Integracyjne](../../zalaczniki/testy-integracyjne.md).

---

## Funkcja to_string

Funkcja `to_string` konwertuje wyrażenie liczbowe na ciąg tekstowy o zadanej szerokości. Wynik trafia do pola typu STRING w strumieniu wynikowym.

### Składnia

```
to_string(wyrażenie : szerokość)
to_string(wyrażenie)
```

Parametr `szerokość` (liczba naturalna po dwukropku `:`) określa szerokość pola wyjściowego w bajtach. Pominięcie parametru daje domyślną szerokość 32 bajtów.

> **ℹ Info**
>
> Separator argumentów to dwukropek `:`, nie przecinek `,`. Przecinek jest separatorem listy SELECT — użycie przecinka w `to_string(x, n)` spowoduje błąd parsowania.


### Przykład

```
DECLARE v INTEGER STREAM src, 1 FILE 'data.txt'

SELECT to_string(src[0]:10) STREAM labels FROM src
```

Strumień `labels` zawiera wartości `src` sformatowane jako tekst w polu 10-bajtowym.

### Konkatenacja z literałem

Ciąg wynikowy można łączyć z literałem stringowym operatorem `+`:

```
SELECT to_string(src[0]:8) + '_ok' STREAM tagged FROM src
```

Rozmiar pola wynikowego: 8 (z `to_string`) + 3 (literal `_ok`) = 11 bajtów.

### Zastosowanie

`to_string` przydaje się przy eksporcie do systemów przyjmujących dane tekstowe (Graphite, InfluxDB przez `xqry`) lub przy tworzeniu etykiet zdarzeń łączonych z wyjściem `DO DUMP`.

> **_NOTE:_** Opisana funkcjonalność ma pokrycie w testach: `issue121_isnull`, `issue128_numeric_to_string`, `issue128_string_to_numeric` opisanych w załączniku pt. [Testy Integracyjne](../../zalaczniki/testy-integracyjne.md).

---

## Funkcja to_integer

Funkcja `to_integer` konwertuje wyrażenie liczbowe na pole typu `INTEGER`. Jest podstawową
drogą odczytu artefaktu z agregatem: pole `RATIONAL` zamienia na liczbę całkowitą, którą
czytelnik odczyta bez znajomości układu pary licznik-mianownik.

### Składnia

```
to_integer(wyrażenie)
```

### Zaokrąglenie

> **⚠️ Ostrzeżenie**
>
> `to_integer` **obcina w stronę zera**, a nie podłoguje. Dla wartości ujemnych wynik różni
> się od podłogi o jeden.

Reguła jest ta sama dla argumentu wymiernego i zmiennoprzecinkowego — w obu przypadkach
część ułamkowa jest odrzucana, a znak zachowany:

| Wartość wejściowa | `to_integer` | podłoga (dla porównania) |
| ----------------- | ------------ | ------------------------ |
| `8/3`             | `2`          | `2`                      |
| `-8/3`            | `-2`         | `-3`                     |
| `-4/3`            | `-1`         | `-2`                     |
| `-2.6666…`        | `-2`         | `-3`                     |

Wartość `NULL` przechodzi przez funkcję bez zmiany — `to_integer(NULL)` daje `NULL`, a nie zero.

### Pułapka przy przenoszeniu na Pythona

Operator `//` w Pythonie **podłoguje**, więc naiwne przepisanie zapytania rozjeżdża się
z silnikiem na każdej wartości ujemnej:

```python
>>> -8 // 3        # Python: podłoga
-3
>>> int(-8 / 3)    # to samo, co robi to_integer
-2
```

Model odtwarzający zachowanie silnika musi liczyć średnią obciętą jawnie:

```python
def truncated_mean(values):
    """Obcięcie w stronę zera, tak jak rzutowanie średniej wymiernej."""
    total = sum(values)
    quotient = abs(total) // len(values)
    return quotient if total >= 0 else -quotient
```

Ten sam problem dotyczy każdego języka, w którym dzielenie całkowite podłoguje.

### Zastosowanie

`to_integer` jest właściwe tam, gdzie odbiorca artefaktu ma przyjąć liczbę całkowitą i część
ułamkowa nie jest potrzebna. Tam, gdzie wartość ma pozostać dokładna, właściwe jest
`to_string`, które zapisuje ułamek jako tekst `licznik/mianownik`, albo odczyt pary wprost
(→ [Układ pola RATIONAL](../../architektura-systemu-przetwarzania-danych/format-zapisu-danych/pliki.md#układ-pola-rational)).

> **_NOTE:_** Opisana funkcjonalność ma pokrycie w testach: `issue128_string_to_numeric` opisanym w załączniku pt. [Testy Integracyjne](../../zalaczniki/testy-integracyjne.md), oraz w testach jednostkowych `ut_payload` i `ut_convertTypes`, przypinających układ pola `RATIONAL` i regułę zaokrąglenia.
