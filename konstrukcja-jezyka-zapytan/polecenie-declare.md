# Polecenie DECLARE

Polecenie DECLARE służy do zadeklarowania źródła danych.

Jego składnia opisana jest następująco:

```
DECLARE pole typ [, pole typ]
STREAM nazwa, szybkość
FILE źródło
[DISPOSABLE]
[ONESHOT]
```

System RetractorDB działając pod kontrolą systemu Linux pobiera i zapisuje dane do plików. W systemie Linux dostęp do większości zasobów jest reprezentowany w postaci różnego rodzaju plików. Takie rozwiązanie ujednolica sposób dostępu do danych.

Przykładem polecenia tworzącego w systemie RetractorDB obiekt zwracający wartości przypadkowe ze strumienia /dev/random 10 razy na sekundę o wartościach typu int wygląda następująco

```
DECLARE pole_przypadkowe INTEGER
STREAM random_stream, 0.1
FILE ‘/dev/random’
```

Wspominane w poleceniu źródło jeśli zostanie zadeklarowane jako plik tekstowy z rozszerzeniem .txt zostanie zinterpretowane przez system jako ciągły i nieskończony tekstowy plik danych czytany wiersz po wierszu w kółko. Ta funkcjonalność została wbudowana w system RetractorDB. Zapewnione jest podstawowe wsparcie dla formatu – jeśli podamy dwa pola całkowite w deklaracji a w pliku po spacji podamy dwie wartości całkowite – wartości te trafią jako kolejne elementy czytanego rekordu.

```
DECLARE pole_1 INTEGER
STREAM cykliczny_stream, 0.1
FILE ‘plik.txt’
```

Aby prasowanie pliku nastąpiło automatycznie, plik musi nosić rozszerzenie .txt. Na chwilę ta funkcjonalność została zaimplementowane na stałe i nie podlega parametryzacji.

Jeśli plik danych wejściowych będzie nosić rozszerzenie .dat – plik ten zostanie potraktowany jako plik binarny a odczyt danych z niego zostanie również zapętlony. Zapętlenie polega na tym że po przeczytaniu ostatniej wartości z pliku źródłowego, pozycja odczytu pliku kierowana jest na początek. Dane z takiego pliku czytane są w nieskończonej pętli, po zakończeniu wracając do  początku.

Kwestia zapętlenia bądź zaniechania tej funkcjonalności kontrolowana jest dyrektywą ONESHOT. Dodanie jej na końcu polecenia DECLARE spowoduje że plik z danymi przeczyta się tylko raz a po przesłaniu zostaną przedstawione w strumieniu wartości 0.

Dyrektywa DISPOSABLE powstała w celu usunięcia pliku z danymi oraz jego metadanych po przesłaniu ich do strumienia. Jeśli doda ją się na końcu polecenia, system po zakończeniu pracy – usunie zadeklarowane źródło danych.
