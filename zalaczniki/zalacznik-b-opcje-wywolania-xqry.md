# Załącznik B - opcje wywołania xqry

Program xqry jest integralną częścią systemu. Dzieli z systemem xretractor wspólny obszar w pamięci używany do komunikacji. Narzędzie xqry służy do komunikacji z procesem przetwarzania planów realizacji zapytań i odbierania danych z pętli zapytań.

Po wywołaniu programu za pomocą polecenia -h przedstawi się nam następujący obraz:

```
$ xqry -h
xqry - data query tool.

Usage: xqry [option]

Allowed options:
  -s [ --select ] arg         show this stream
  -t [ --detail ] arg         show details of this stream
  -a [ --adhoc ] arg          adhoc query mode
  -m [ --tlimitqry ] arg (=0) limit of elements, 0 - no limit
  -l [ --hello ]              diagnostic - hello db world
  -k [ --kill ]               kill xretractor server
  -d [ --dir ]                list of queries
  -y [ --diryaml ]            list of queries in yaml format
  -r [ --raw ]                raw output mode (default)
  -g [ --graphite ]           graphite output mode
  -f [ --influxdb ]           influxDB output mode
  -p [ --gnuplot ] arg        x,y - gnuplot output mode
  -h [ --help ]               produce help message
  -c [ --needctrlc ]          force ctl+c for stop this tool
Branch: issue_31-doc:2707ce0, Code compiler: GNU Ver. 13.3.0, Build time: 2512211449, Type: Debug
Log: /tmp/xqry.log
This software is licensed under the MIT License and is provided ‘as is’,
without warranty of any kind. For more information, see the LICENSE file.
```

Poniższa tabela przestawia opisz poszczególnych opcji.

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Opcja</td><td valign="top">Znaczenie</td></tr><tr><td valign="top">select</td><td valign="top">Odebrania danych z danego strumienia udostępnianego przez proces xretractor</td></tr><tr><td valign="top">detail</td><td valign="top"><p>Przedstawienie szczegółów na temat danego strumienia danych.</p><p>Przykładowa odpowiedź:</p><p>---<br>apiVersion: xqry/v1<br>stream:<br>  name: str4<br>  delta: 1<br>query: SELECT (str4[0]+1)*2 STREAM str4 FROM core0>1<br>fields:<br>  str4.str4_0:<br>    type: INTEGER</p></td></tr><tr><td valign="top">adhoc</td><td valign="top">Dołączenie zapytania do systemu w biegu</td></tr><tr><td valign="top">tlimitqry</td><td valign="top">Ograniczenie ilościowe odbieranych od systemu rezultatów. Bardzo potrzebna funkcjonalność w złączeniu z opcją -k do celów testowych</td></tr><tr><td valign="top">hello</td><td valign="top">Weryfikacja funkcji kanału komunikacyjnego z systemem</td></tr><tr><td valign="top">kill</td><td valign="top">Żądanie zatrzymania działania procesu xretractor</td></tr><tr><td valign="top">dir</td><td valign="top">Wylistowanie wszystkich zapytań realizowanych w procesie realizacji zapytań przez system xretractor w formie tekstowej</td></tr><tr><td valign="top">diryaml</td><td valign="top">Wylistowanie wszystkich zapytań realizowanych w procesie realizacji zapytań przez system xretractor w formacie yaml</td></tr><tr><td valign="top">raw</td><td valign="top">Tryb tekstowy odpowiedzi systemu. Dane prezentowane są bez zbędnych dekoracji</td></tr><tr><td valign="top">graphite</td><td valign="top">Tryb odpowiedzi przygotowujący dane dla systemu graphite</td></tr><tr><td valign="top">influxdb</td><td valign="top">Tryb odpowiedzi przygotowujący dane dla systemu influxdb</td></tr><tr><td valign="top">gnuplot</td><td valign="top">Przygotowanie agregatów dla bezpośredniego wywoływania strumienia danych dla programu gnuplot</td></tr><tr><td valign="top">help</td><td valign="top">Wyświetlenie tekstu pomocy</td></tr><tr><td valign="top">needctrlc</td><td valign="top">W normlanym trybie pracy – dowolny klawisz zatrzyma proces odbioru danych. W tym trybie, konieczne jest użycie ctrl+c</td></tr></tbody></table>

&#x20;

Informacje poniżej listy dostępnych opcji narzędzia są identyczne z tymi opisywanymi w poprzednim załączniku dla narzędzia xretractor.
