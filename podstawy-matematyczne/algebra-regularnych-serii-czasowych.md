# Algebra regularnych serii czasowych

Algebra – rozumiana jako konstrukcja w postaci zdefiniowanego zbioru i zdefiniowanych operacji na nim stanowi podstawę dla deklaratywnego język zapytań. W dalszej części pracy odnosząc się do Algebry (bez dodatkowego przymiotnika) i będę ją rozumiał jako Algebrę regularnych serii czasowych. Jeśli będę chciał odwołać się do Algebry Relacji – jasno wyspecyfikuję przymiotnik.

Zaproponowałem \[3] następującą definicje regularnej serii czasowej (tzw. Modelu danych) oraz następujące operacje i definicje.

{% hint style="success" %}
Przez strumień danych rozumiemy uporządkowaną parę S := (s<sub>n</sub>,∆) – gdzie pierwszy element to uporządkowania seria danych a drugi, oznaczony symbolem delty to regularny odstęp czasu pomiędzy kolejnymi elementami serii danych.
{% endhint %}

Tak zdefiniowaną serię danych w systemie określam jako strumień danych. Taki regularnie przepływający przez system zestaw danych, zazwyczaj opisany schematem danych zawiera pola różnych typów. Każdy odczyt występuje w równym odstępie czasu pomiędzy kolejnymi pomiarami. Taka konstrukcja bardziej przypomina sygnał cyfrowy niż nieregularny strumień danych – jednak oznaczenie jej jako strumień w dalszej części prac badawczych okaże się uzasadnione.

{% hint style="info" %}
Uwaga: Pojęcie strumień i Seria czasowa w tej pracy używane są zamiennie i oznaczają to samo. Formalnie w literaturze naukowej strumień oznaczany jest jako zbiór par (a,t) – gdzie a oznacza krotkę, a czast oznacza jej moment zarejestrowania lub wystąpienia. W strumieniu dopuszczalne są krotki, których czas t pokrywa się dla różnych krotek. W przypadku serii czasowej rozróżniamy dwa typy serii – regularne i nieregularne. W przypadku serii nieregularnych – seria to sekwencja uporządkowanych krotek w czasie  – {a<sub>t</sub>,t<sub>n</sub>}, gdzie czas t<sub>n</sub>  jest unikalny w zbiorze dla każdej krotki. Natomiast seria regularnej serii czasowej może zostać opisana sekwencją krotek i regularnym odstępem czasu pomiędzy ich występowaniem – ({a<sub>t</sub>},D) – i to ta ostatnia definicja jest bazą dalszych operacji w opracowanym systemie.
{% endhint %}

Operacje jakie możemy na takim zbiorze danych wykonać zdefiniowałem następująco:

* przeplot i rozplątanie
* suma i różnica
* przesunięcie sekwencji
* agregacja i serializacja

W operacji przeplotu biorą dwa różnie strumienie danych.

Definiujemy ją następująco:

<p align="center"><img src="../.gitbook/assets/unknown (4).png" alt=""></p>

<p align="center"><img src="../.gitbook/assets/unknown (5).png" alt=""></p>

Argumentem operacji splątania są dwa strumienie danych A i B, każdy z własną szybkością napływu danych. Wynikiem jest strumień wynikowy C – z nową różną od dwóch poprzednich szybkością napływu wyznaczoną wzorem powyżej.

Operację będziemy oznaczać symbolem #.

Operację rozplątania definiujemy poprzez dwie operacje.

1\. Rozplątanie lewostronne jako strumień A w postaci:

<p align="center"><img src="../.gitbook/assets/unknown (6).png" alt=""></p>

2. Rozplątanie prawostronne jako strumień B w postaci:

<p align="center"><img src="../.gitbook/assets/unknown (7).png" alt=""></p>

Operacje rozplątania 1 i 2 będziemy oznaczać symbolami % i &.

Argumentem operacji rozplątania jest splątany strumień danych oraz wymierna liczba określająca szybkość napływu odplątywanego strumienia danych. W wyniku operacji otrzymujemy strumień danych z wyznaczoną szybkością wzorem powyżej.

Operacje splątania i rozplątania są komplementarne. Oznacza to że przypominają operacje mnożenia i dzielenia w zbiorze liczb naturalnych. W wyniku mnożenia otrzymujemy pewien wynik natomiast w wyniku dzielenia – czasem dochodzi reszta, istotne jest również to co przez co dzielimy i w jakiej kolejności.

Operacje sumy zdefiniowałem następująco:

<p align="center"><img src="../.gitbook/assets/unknown (8).png" alt=""></p>

<p align="center"><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAALQAAAAhCAMAAABHuHHwAAAAAXNSR0IArs4c6QAAAJlQTFRFAAAAAAAAAAA6AABmADpmADqQAGa2OgAAOgA6OgBmOjoAOjo6OmZmOmaQOma2OpC2OpDbZgAAZjoAZjo6ZmZmZmaQZpC2ZpDbZrbbZrb/kDoAkDo6kGYAkGZmkLbbkNv/tmYAtmY6tpA6trZmttv/tv//25A625Bm27Zm27aQ2//b2////7Zm/7aQ/9uQ/9u2/9vb//+2///b8xTnqwAAAAF0Uk5TAEDm2GYAAAAJcEhZcwAAFiUAABYlAUlSJPAAAAAZdEVYdFNvZnR3YXJlAE1pY3Jvc29mdCBPZmZpY2V/7TVxAAAC3ElEQVRYR+1X7XKbMBBE2I76FbfgtLVpmtA0IaZQKLz/w/WkkwQSkiyGdiaZwf88Ot2uVrenI4rW36rAqsCqwMtWoEw/LSRYbO8WZpi5vc/i5Yhluqt03JycZhKZEd4lGlwIli2mzzZPY9Sa/BvSObFUgQEWgmWP0Q/fJcSGNkNMDIUyuJ9uqrXcIViumGIsbbH5Sa5mUwzcYAgdguWKGUvd0FP9/0g3dKxHCJY7Jh9uMt9VDTWt6dfx/I7AhjMl2/uoTUnMbCwvdVjjvim06gjBcscMuWqg7yANhhj9hmM+76uCHH8cgdHVeQ9H5r7uEhbB1064xkhrjcCDpVTy8hG31iXg+C7R28nles3j9yAvnGqvdqskco0haOYMwfLFKG0LRnc26T7jt16T0W6ZEtYYXfSJRjoEyxcjEaDqnc3Ko7c4JTZmYWPZ29SamTkEyxsjSPcZd6C9w3pIY08Q24Q/ZPVqa6PMIVh6DNyZVraCNKt6jm59El1GlD0BG6fgpRoynkFe5WBEPxYqZMT0mfZ+4JXyqp94/LINRU+QSbgcyiVIU7Z+1aZCsMwY9R8pYa5cqi+nhvZAiO0tNs4hyhaTqJJGVbSSZmcRYk2wypSQDwd20+ptM2NA+Gcaf5Xo/HFp6NCGueRn8rFq3mrDlFV2oarStH/YM+T+AbIMa+03kFxWzQSLnbjFVitJT2M2N3f9rVQWqzEfPR1Mj4aKarlUIFpdgCHiLxXzRXyEpIIBEMC5XTQVK5aoWUnajIm4tIW8em1gUhTV7VwiPWfdnIPFXo4latbOhi0zKSUrYy4XeQyvzmHmi7WCYW/DZtEl8Kzafrxpiy6o6mxiL3awP8ZXzXLuts8tLqL0s6soeWHU2I1LurV6DS7yMSrfWAb5pcTL1Pyc67PtU/v5dvfruwcuh/GxxO5TOz9sYcok149LGYbt/03JNcyDMNs6f93hhoK5w/KtUasCr1WBv9zIUY8v7H+gAAAAAElFTkSuQmCC" alt=""></p>

Natomiast różnicę opisuje wzór:

<p align="center"><img src="../.gitbook/assets/unknown (9).png" alt=""></p>

Te operacje oznaczać będziemy znakami + oraz -.

Operacja przesunięcia sekwencji zawiera argument w postaci opóźnienia dostępu do danych o daną ilość odstępów czasu pomiędzy kolejnymi elementami.  I tak np. dane napływające co sekundę ze strumienia źródłowego po wykonaniu operacji przesunięcia o 3 – pojawią się jako wynik opóźnione o 3 sekundy.

Operację przesunięcia oznaczać będę za pomocą >.

Ostatnią operacją w ramach zdefiniowanej algebry jest operacja agregacji i serializacji – w skrócie Agse. O ile wydaje się że to dwie oddzielne operacje, zdefiniowałem dwuargumentowy operator implementujący logikę ruchomego okna danych. Pierwszym argumentem jest skok okna, drugim jest jego szerokość. Skok jest liczbą naturalną o ile ruchome okno danych należy przesunąć nad strumieniem. Zakładamy że źródłowy strumień danych rozbity zostaje względem schematu danych, modyfikując jego szybkość napływu. Szerokość okna jest liczbą całkowitą, różną od zera. Wartości ujemne szerokości przenoszą kolejność tworzonych elementów w odbiciu lustrzanym. Wartości dodatnie – zachowują sekwencyjny charakter tworzonych ruchomych okien danych.

Operację Agse oznaczać będę znakiem @.

Podsumowując, algebra będąca podstawą dla deklaratywnego języka zapytań prezentuje się następująco:

<p align="center"><img src="../.gitbook/assets/unknown (10).png" alt=""></p>

Gdzie pierwszy element pary definiującej algebrę to model danych a drugi to zdefiniowane formalnie na tym modelu danych operacje.

