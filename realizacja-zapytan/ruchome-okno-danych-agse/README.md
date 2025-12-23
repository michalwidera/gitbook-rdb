# Ruchome okno danych AGSE

Ruchome okno danych to pojęcie powszechnie stosowane w systemach przetwarzających strumienie lub serie czasowe. Idea polega na grupowaniu danych w oknach czasowych, dając możliwość użytkownikowi możliwość przetwarzania w zamrożonych migawkach.&#x20;

RetractorDB również wspiera ten model przetwarzania danych. Prezentację rozpoczniemy od przykładu. Jednak do pełnego zrozumienia tego operatora konieczna jest znajomość jego argumentów. Operator Agse oznaczany znakiem @ ma on dwa argumenty i oparty jest na strumieniu. Pierwszym argumentem jest skok okna, drugim jest jego rozmiar. Co ważne, rozmiar okna może być ujemny. Takie oznaczanie dotyczy agregacji lustrzanej. O agregacji lustrzanej opowiemy wraz z prezentacją jednego z przykładów.

Na początku rozważymy proces serializacji w operatorze Agregacji i Serializacji – AgSe.
