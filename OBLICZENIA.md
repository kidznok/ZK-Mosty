# ZK Most — Obliczenia 0.1

Moduł w ZK Most 0.25 wykonuje obliczenia statyczne pojedynczej belki.

## Uruchomienie bez CAD

Program samodzielny można zbudować z projektu `analysis-app/ZKMost.Obliczenia.csproj`. Wymagany .NET Desktop Runtime 8 x64. Program otwiera przykład dwóch równych przęseł 10 + 10 m.

1. Wpisz długość i EI w kNm². EI nie jest wyznaczane z geometrii CAD.
2. Podaj podpory, np. `0;10;20`. Przemieszczenie pionowe każdej podpory jest zablokowane. Obrót jest swobodny; `0!` oznacza utwierdzenie. Belka ma ciągłość obrotu nad podporami pośrednimi. Przeguby wewnętrzne i oddzielne belki swobodnie podparte nie są automatycznie modelowane.
3. Obciążenia skupione: `5:100;15:80` oznacza 100 kN w x=5 m i 80 kN w x=15 m. Obciążenia równomierne odcinkowe: `0:20:10` oznacza 10 kN/m na całej długości. Dodatnie obciążenia są skierowane w dół. Puste pole oznacza brak obciążeń danego rodzaju. Przecinek dziesiętny jest obsługiwany; separatorem wierszy jest średnik.
4. Zatwierdź schemat i oblicz. M dodatni oznacza zginanie przęsłowe, V jest dodatnie na lewej ścianie elementu zgodnie z równowagą pokazanych wykresów, u dodatnie w górę. Reakcje dodatnie w górę, momenty reakcji dodatnie przeciwnie do ruchu wskazówek zegara.
5. Dla przejazdu podaj osie jako `odsunięcie:siła`, np. `0:100;1.2:100`. To pojazd użytkownika, nie automatycznie wyznaczony LM1. Położenie pojazdu określa x osi o odsunięciu 0. Zmień znaki odsunięć, aby przeanalizować drugi kierunek. Obciążenia wpisane wyżej pozostają stałą bazą przejazdu.
6. Obwiednia obejmuje dyskretne pozycje oraz przejścia osi przez podpory i przekroje obserwacji. Sprawdź zbieżność, zmniejszając krok. Miarodajne pozycje są w CSV. Uwzględniono również stan bez pojazdu.
7. Dla linii wpływu wpisz przekrój x. Program przesuwa siłę 1 kN w dół, pomijając bazowe obciążenia; prezentuje M, obie strony V oraz u.
8. Eksport HTML tworzy samodzielny raport z wykresami SVG i danymi, a obok CSV statyki, reakcji oraz — dla przejazdu — obwiedni. Wartości globalnych ekstremów wykresów są próbkowane.

Zmiana danych usuwa poprzednie wyniki z ekranu i uniemożliwia eksport nieaktualnego wyniku. Model belki i dane pojazdu można zapisać i ponownie odczytać w JSON.

## BricsCAD V26

Zainstaluj wspólny pakiet ZK Most dla BricsCAD V26 x64. Wstążka i polecenia korzystają z loadera instalatora.

Otwórz istniejący most i wybierz **Obliczenia** w stopce edytora lub uruchom `ZKMOSTOBLICZENIA`. Importuje się długość i stacje podpór względem początku mostu. EI=1 000 000 kNm² jest wartością przykładową wymagającą ustalenia przez użytkownika. Obciążenia po imporcie są puste. Ciągłość trzeba zweryfikować: CAD przechowuje geometrię belek i podpór, nie rozstrzyga schematu statycznego. Mosty skośne i belki prowadzone po osi są odrzucane przez ten uproszczony import. Prosta belka na zakrzywionym moście nadal wymaga ustalenia właściwej długości obliczeniowej — stacje osi są jedynie wstępnymi danymi.

Zmiany w CAD po otwarciu okna analizy nie aktualizują jego danych. Okno stanowi osobny, opisany schemat; po zmianie mostu otwórz je ponownie. Model obliczeniowy zapisuj do JSON; wyników nie zapisuje się jeszcze w Xrecord DWG. Wykresy są w oknie i raporcie, bez wstawiania do DWG.

## Metoda i zakres

Macierz sztywności belki Eulera–Bernoulliego, dwa stopnie swobody na węzeł, stałe dodatnie EI. Węzły w podporach, siłach i końcach obciążeń odcinkowych; zgodne obciążenia węzłowe. Siły i przemieszczenia odtwarzane z wielomianu równowagi elementu; obwiednia korzysta z odtworzenia w dokładnej współrzędnej przekroju. Eliminacja z wyborem elementu głównego po skalowaniu diagonalnym. Odrzucane są układy niestateczne, niepoprawne i nadmiernie gęste węzły. Przemieszczenia podpór są zerowe.

Nie wdrożono jeszcze: normowego generatora LM1/LM2 i pasów, współczynników alfa/gamma/psi, kombinacji SGN/SGU, niekorzystnego odcinkowego rozstawienia UDL, ciężaru własnego z modelu, zmiennej sztywności, przegubów wewnętrznych, rusztu i płyt MES, geometrii przestrzennej, sił osiowych, temperatury, sprężenia, faz budowy, zarysowania, pełzania, skurczu, wymiarowania oraz kontroli rys i zmęczenia.

Ta wersja nie potwierdza zgodności z Eurokodami i nie dobiera zbrojenia. Następny etap wymaga ustalenia konkretnych wydań norm i polskich załączników krajowych oraz tabeli reguł i źródeł. Materiał referencyjny: [WR-M-22, przykłady mostowe według Eurokodów](https://www.gov.pl/web/infrastruktura/wr-m). Obecne testy wykorzystują rozwiązania analityczne, a nie pełne przykłady WR-M.
