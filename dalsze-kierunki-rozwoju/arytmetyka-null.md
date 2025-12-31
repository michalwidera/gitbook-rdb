# Arytmetyka NULL

Na chwilę obecną system nie wspiera wartości NULL w polach. Jest to jednak pożądana właściwość systemu.&#x20;

Stoję w  tym miejscu przed koniecznością znalezienia właściwego rozwiązania problemu. W chwili obecnej przetwarzane struktury danych przechowują dane w postaci binarnych struktur danych (tzw. payload) mapujących bezpośrednio dane na typy binarne stosowane w języku C++. W tych typach nie ma wydzielonych wartości dla typów NULL. Oczywiście nie ma przeszkody aby stworzyć programowo tego typu zachowanie - problem się może pojawić w przypadku, kiedy wszystkie wartości są użytkowane i użycie wartości std::min lub std::max danego typu wpływnie na efektywną możliwość przetwarzania danych.

Inną opcją jest dołożenie zmiennej typu metadanych do każdej krotki, która będzie inforować, które wartości niosą wartość typu NULL.

W praktyce - problem nadal rozważam, która droga będzie najbardziej efektywna i użyteczna.&#x20;
