# Wyrażenia algebraiczne

Zdefiniowana algebra pociąga za sobą możliwość definicji wyrażeń algebraicznych. Typowe wyrażenia algebraiczne w zbiorze liczb wymiernych to materiał przerabiany w szkole podstawowej. Wyrażenia algebraiczne w systemie RetractorDB występują w dwóch formach. Na liście pól polecenia SELECT – mamy wyrażenia typowe, znane ze szkoły podstawowej. Na liście argumentów polecenia SELECT w klauzuli FROM mamy wyrażenie algebraiczne zbudowane w oparciu o nową, zdefiniowaną algebrę.

Oznacza to że na liście pól po klauzuli SELECT operator plus oznacza jedno a w klauzuli FROM – oznacza zupełnie coś innego. Niewinnie wyglądające zapytanie z definicji łączy dwa zupełnie inne światy i pojęcia. Jeden algebry opartej na liczbach drugiej opartej na regularnych seriach czasowych.

Przykład. Jako przykład przedstawione zostanie wyrażenie algebraiczne zbudowane w zbiorze regularnych serii czasowych (zwanych dalej strumieniami). Zakładając istnienie dwóch strumieni:  A(a<sub>1</sub> int, a<sub>2</sub> int),1 oraz B(b<sub>1</sub> int),½ – gdzie,

\- A oznacza strumień zawierający w każdym rekordzie dwa pola o wartościach typu int – a<sub>1</sub> oraz a<sub>2</sub>, napływające raz na sekundę, oraz

\- B zawierający w każdym rekordzie pole typu int o nazwie b<sub>1</sub> napływające dwa razy na sekundę.

To wyrażenie algebraiczne postaci C=A+B stworzy strumień danych o polach C(a<sub>1</sub> int, a<sub>2</sub> int, b<sub>1</sub> int),½.

Aby dokonać przeplotu strumienia danych zbiory  A i B powinny posiadać te same schematy danych. Załóżmy więc że istnieje strumień D(d<sub>1</sub> int),1 – napływający podobnie jak strumień A – raz na sekundę.

To wyrażenie algebraiczne postaci E=B#D stworzy strumień:  E(e<sub>1</sub> int),⅓. Szybkość ⅓ bierze się ze wzoru (1\*½)/(1+½)

Wzór znajdziesz przy definicji operacji przeplotu.

W tak zdefiniowanych strumieniach nadal poprawne jest wyrażenie:

F=((B#D)+A)>2

I takie argumenty mogą się pojawić jako poprawne wyrażenia algebry szeregów czasowych w treści zapytania.

### Reprezentacja graficzna

Na Rys. 1 przedstawiono schematycznie zależności pomiędzy opracowanymi operatorami algebry serii czasowych. Na rysunku połączyłem zależności opracowanych operatorów, ich symboliczne oznaczenia stosowane w języku zapytań oraz kierunki przetwarzania danych.

Przedstawiony rysunek stanowi też  graficzne podsumowanie treści zaprezentowanych w tym rozdziale. Przedstawiony graficzny sposób reprezentacji mam nadzieję ułatwi przyswojenie zasad panujących pomiędzy wprowadzonymi operatorami. Dla czytelności pominięte zostały operatory agregacji i serializacji oraz przesunięcia czasowego. Należy mieć świadomość że do pełnego obrazu brakuje ich na tym schemacie.

