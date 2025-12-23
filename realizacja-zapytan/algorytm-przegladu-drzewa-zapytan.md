# Algorytm przeglądu drzewa zapytań

W momencie w którym mamy przygotowaną siatkę oraz minimalny zbiór odstępów czasu możemy przejść do realizacji algorytmu przeglądu drzewa zapytań. Pobieramy ze zbioru zapytań wszystkie zapytania, które zaczynają się od momentu 0. Oczywistym jest fakt że to wszystkie zapytania realizowanie w systemie. Wyznaczamy wartości krotek opisanych listą argumentów we wszystkich zapytaniach w kolejności istniejących zależności pomiędzy zapytaniami.

Zapisujemy lub przekazujemy do zapisu dane na dysku, oraz umieszczamy dane w zarejestrowanych kolejkach pamięci współdzielonej. Odczekujemy kolejny interwał czasu wyznaczony przez minimalny zbiór interwałów. Tym razem w przypadku bardziej skomplikowanych zapytań nie wchodzą już wszystkie istniejące zapytania. Pobieramy dane, liczymy, zapisujemy. Algorytm zapętlamy.

Tak w ogólnym zarysie wygląda algorytm przeglądu drzewa zapytań. Drzewo ustalane jest zależnością czasową oraz zależnością od dostępności istniejących danych. Nie wybudujemy krotek strumienia z danych, które jeszcze nie nadeszły. Proces szeregowania i budowy drzewa podlega zależnościom generowanym przez równania opracowanej algebry.
