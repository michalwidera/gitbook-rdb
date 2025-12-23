# Elementy składowe

System zbudowany jest w oparciu o 3 programy dostępne jako polecenia systemowe. Pierwszym jest kompilator oraz system realizujący plany zapytań. Drugim jest klient dostępu do danych bieżących, trzecim jest program umożliwiający dostęp zrzutów binarnych. Ich nazwy to kolejno:

* xretractor
* xqry
* xtrdb

Program xretractor tworzy główny proces systemu RetractorDB. Program xqry tworzy procesy komunikujące się z systemem RetractorDB. Komunikacja zachodzi za pomocą wspólnego obszaru w pamięci. Program xtrdb służy do analizy danych i metadanych zapisywanych w plikach bazy danych.&#x20;
