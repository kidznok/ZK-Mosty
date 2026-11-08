# Kontrola zakresu WR-M — ZK Most 0.19

Stan przeglądu: 08.11.2026. To przegląd funkcji modelera i częściowa kontrola geometrii, nie ocena zgodności projektu konstrukcyjnego.

Źródła: [aktualny wykaz MI](https://www.gov.pl/web/infrastruktura/wr-m), [WR-M-11 v02](https://www.gov.pl/attachment/4cea4d93-2c35-4de7-8b8a-a88f4d73ea5a), [WR-M-12](https://www.gov.pl/attachment/d3ee08e2-3bec-4621-a39c-fcb3eb783936).

## Kontrole zaimplementowane

Karta Sprawdź z WR-M: przyczółki, długość skrzydeł (6.3), promień i nachylenie stożków, grubość oraz szerokość płyt przejściowych (6.6). Długość płyty wymaga znajomości posadowienia i Hpp; spadek wymaga porównania z niweletą. Wynik rozróżnia sprawdzony parametr, uwagę i brak danych.

W nowych przyczółkach kierunek skrzydła jest odniesiony do ściany, także skośnej; podcięcie jest edytowalne. Obrys użytkownika nie jest narzuconym przez WR-M szablonem konstrukcyjnym. Stare skrzydła zachowują dotychczasowe odniesienie. Promień korony nowych przyczółków: 1 m; kontrola przewiduje wyjątek przy schodach. Źródłem jest wersja 02 z 07.07.2026, nie archiwalna wersja 01.

## Przegląd wszystkich obszarów modułu

| Obszar | Stan i granica funkcji |
|---|---|
| Oś, niweleta, odsunięcie | Modelowanie geometrii 2D/3D; bez pełnego sprawdzenia parametrów drogi i skrajni. |
| Pomost i kapy | Niezależne szerokości jezdni L/P; bez klasy drogi brak doboru przekroju funkcjonalnego. |
| Belki i poprzecznice | Prosta między oparciami albo przebieg po osi. Automatyczne wykrycie łuku jest wyborem geometrycznym, nie kwalifikacją prefabrykatu. Dla prefabrykatów prostych trzeba wybrać prowadzenie proste; brak obliczeń nośności i katalogu producenta. |
| Filary, fundamenty, łożyska | Model geometrii; brak obliczeń geotechnicznych, doboru łożysk i sprawdzenia podpór na oddziaływania. |
| Przyczółki i skrzydła | Obrys i kierunek edytowalne; brak doboru dylatacji ścian, schematu statycznego oraz zbrojenia. |
| Nasypy i stożki | Stopa dopasowywana do TIN z XREF. Brak pełnej kontroli obsypania ściany, stateczności i umocnienia. |
| Płyty przejściowe | Geometria mostowa i podstawowe kontrole wymiarów. Brak pełnego detalu oparcia, izolacji i drenażu; w generatorze przepustów jeszcze brak płyt. |
| Bariery, balustrady i gzymsy | Modele schematyczne. Brak doboru certyfikowanego systemu, kotew, odkształceń i stref pracy. Katalog WR-M-71 wymaga odrębnego szczegółowego porównania. |
| Przepust | Przewód i każda ściana z otworem jako jeden obiekt CAD; bez obliczeń WR-M-12, spiętrzenia, rozmycia i wypadu. |
| Półki dla zwierząt | Geometria półki; brak oceny przyrodniczej, doboru gatunkowego i ciągłości przejścia. Nie przypisujemy fałszywie wymiarów półki do WR-M-51. |
| Rysunki | Powiązana geometria i warstwy. Brak automatycznego potwierdzenia kompletności projektu wykonawczego. |
| Zbrojenie i trwałość | Brak projektu zbrojenia i kontroli trwałości według WR-M-31/32; nie są oznaczane jako sprawdzone. |

Przegląd nie obejmuje pełnej analizy katalogów WR-M-21/22 i WR-M-71 ani obliczeń według Eurokodów. Te obszary pozostają jawnie niesprawdzone. Zmiana geometrii wymaga ponownego naciśnięcia Sprawdź geometrię; raport nie zapisuje certyfikatu zgodności.
