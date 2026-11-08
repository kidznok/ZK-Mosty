# ZK Most 0.14.0 — graficzny przepust i praca bez zamykania okna

ZKPRZEPUST otwiera graficzny edytor w stylu ZK: Oś i profil, Rura i półki, Ściany i teren, Model i rysunki. Wybierz oś, ustaw zakres i rzędne dna przy schemacie, potem przekrój i ściany. Wskazywanie w CAD dotyczy geometrii, nie wpisywania parametrów. Edycja istniejącego przepustu: ZKELEMENT i wskazanie elementu.

Okna mostu i przepustu nie blokują CAD. Na żywo przelicza po krótkiej pauzie; Przelicz teraz wymusza przebudowę również bez zmiany parametrów. Zmiany odświeżają zapisane widoki. Wyłącz Na żywo, jeśli chcesz zebrać kilka zmian przed przebudową. Błąd przebudowy jest pokazywany w oknie; poprzednia transakcja modelu pozostaje zachowana.

Wstążka ma kolumny po trzy rzędy. Publiczne polecenia pozostają bez numerów. Zakres przepustu można wskazać w dowolnej kolejności; dwa wskazania tego samego miejsca są odrzucane. Poprawiono samoprzecięcia segmentów płyty na załamaniach osi: płyta, kapa i krawężnik korzystają z rzeczywistej geometrii odsunięć.

Weryfikacja: 258/258 geometrii, 21/21 interfejsu WPF, 14/14 aktualizatora offline; kompilacja bez ostrzeżeń. Praca okien modeless, kolejka wskazywania, natywna wstążka i odświeżanie po operacjach CAD wymagają testu w BricsCAD V26. Testy automatyczne nie zastępują próby w otwartym CAD.

# Narzędzia po osi i przepusty

## Uruchomienie

Wczytaj przez APPLOAD ten sam ZKMost-start.lsp. Loader wskazuje nową generację DLL, nie trzeba zastępować plików załadowanych przez poprzednią sesję. Nazwy poleceń są stałe, bez numerków. ZKMOSTRIBBON odtwarza wstążkę.

| Polecenie | Działanie |
|---|---|
| ZKPRZEKROJ | Własny przekrój po osi, przejścia między stacjami |
| ZKROZMIESC | Wystąpienia bloku wzdłuż osi |
| ZKPRZEPUST | Nowy przepust |
| ZKELEMENT | Edycja wybranego obiektu po osi / przepustu / układu bloków |
| ZKELEMENTBUILD | Przebudowa obiektu oraz jego zapisanych rysunków |
| ZKELEMENTVIEW | Rzut, przekrój, bok albo rozwinięcie |
| ZKDOCIECIE | Zapisanie pionowej płaszczyzny cięcia po linii w planie |
| ZKCIECIA | Włączanie i wyłączanie zapisanych cięć |
| ZKODLACZ | Odłączenie obiektu po osi od generatora do ręcznej obróbki |
| ZKPRZYPISZ | Dołączenie nowych ręcznych brył do odłączonego obiektu i jego rysunków |
| ZKMOSTTEST | Próba natywnego CAD w transakcji bez zapisu |

## Przekrój po osi

1. Narysuj otwartą polilinię osi w planie XY WCS. Łuki polilinii są obsługiwane.
2. Narysuj zamkniętą polilinię przekroju w XY WCS. X oznacza kierunek poprzeczny (+L), Y oznacza wysokość do góry. Wskaż punkt bazowy przekroju; nie musi być jego narożnikiem.
3. ZKPRZEKROJ: wybierz oś i wskaż początek oraz koniec na osi. Podaj odsunięcie, odniesienie wysokości i obrót.
4. Wybierz profil: rzędna na stacji 0 + spadek, własny profil rysowany albo profil z ZK Droga. Wariant Droga wymaga tej samej zarejestrowanej osi; odczytuje też reguły spadków poprzecznych. Własny profil: X to odległość od początku osi, Y to rzędna przeskalowana. Wskaż punkt stacji 0 o znanej rzędnej i podaj skalę pionową. Profil musi obejmować cały zakres i mieć rosnące X.
5. Wybierz przekrój A, opcjonalne stacje pośrednie i przekrój B. Na kolejnej stacji można ponownie użyć źródła i zmienić mnożnik szerokości / wysokości — np. 5 × 1 m na A, 5 × 3 m na B.
6. Sprawdź podgląd (rzut / aksonometria), zatwierdź. Anulowanie pozostawia wcześniejszy model i dane.

Przekroje muszą mieć 3–256 wierzchołków, identyczną liczbę wierzchołków, zgodny obieg i odpowiadający pierwszy wierzchołek. Samoprzecięcia są odrzucane. Przekroje i profil rysowany korzystają z prostych odcinków — łuki przekroju należy wcześniej podzielić na odcinki. Źródłowe polilinie są odczytywane ponownie podczas przebudowy. Punkt bazowy przekroju jest zapamiętany w WCS: przesunięcie całego źródła względem niego zmienia położenie przekroju.

„Spód płyty” to profil minus zadana grubość płyty i nawierzchni. Przy własnym profilu grubość jest parametrem elementu, nie automatycznym odczytem bryły płyty. Nie ma jeszcze ogólnego wiązania do dowolnej powierzchni bryły.

Dokładność 0,1–1000 mm steruje adaptacyjnymi przekrojami; maksymalny krok 0,1–50 m ogranicza odległość między nimi. Punkty charakterystyczne osi, profilu i stacje przekrojów są zachowane. Limit 4001 przekrojów zatrzymuje nieciągłą lub nadmiernie złożoną geometrię zamiast tworzyć błędną bryłę.

## Obróbka i zapisane cięcia

ZKDOCIECIE obsługuje zarówno nowe obiekty po osi i przepusty, jak i wskazany element istniejącego mostu, np. belkę. Wskaż LINE lub polilinię z dwoma wierzchołkami, a potem stronę do zachowania. Powstaje pionowa płaszczyzna cięcia. Źródłowa linia, kierunek zachowanej półprzestrzeni i aktywność operacji zapisują się w DWG. Można dodać kilka cięć. Po zmianie osi / przekroju odtworzy je przebudowa. Przesunięcie źródłowej linii zmienia cięcie przy następnym przeliczeniu.

ZKCIECIA pozwala wyłączyć operację i odzyskać pełny kształt. Dla mostu po wskazaniu elementu dostępne są zapisane cięcia mostu, także te dotyczące fragmentu, który został całkowicie odcięty. Cięcie usuwa geometrię z już wygenerowanego zakresu; nie przedłuża bryły. Jeśli linia leży poza końcem, najpierw wydłuż zakres.

Zapisane cięcia są odtwarzane przez generator. Inne ręczne operacje CAD na powiązanej bryle nie są rejestrowane: do dowolnej obróbki nowych obiektów użyj ZKODLACZ. Przed odłączeniem wybierz pełne bryły, jeżeli chcesz używać operacji bryłowych. ZKODLACZ dotyczy nowych obiektów po osi/przepustów/bloków, nie pojedynczych części parametrycznego mostu.

Odłączony obiekt zostaje w CAD. ZKELEMENTBUILD nie generuje go ponownie — odczytuje aktualne bryły/siatki/bloki i odświeża zapisane rysunki. Nową bryłę powstałą po podziale można dodać przez ZKPRZYPISZ. Zachowaj oś jako odniesienie dla boku, przekrojów i rozwinięcia. Ręczne operacje tworzące nowe encje mogą nie przenieść oznaczenia własności: wtedy użyj ZKPRZYPISZ. Krzywe odczytane z natywnych brył do rysunków są aproksymowane odcinkami.

## Rozmieszczanie

ZKROZMIESC: wybierz oś, zakres, profil i przykładowe wystąpienie bloku. Generator korzysta z jego definicji oraz skali XYZ. Podaj rozstaw i dodatkowy obrót. Oś X bloku jest prowadzona po stycznej osi w planie; wysokość wynika z profilu i przesunięcia. Koniec jest wstawiany tylko, jeśli wypada na pełnym rozstawie. Maksymalnie 10001 wystąpień. Nie wprowadza się nachylenia bloku zgodnego ze spadkiem podłużnym. Bloki korzystają ze wspólnej definicji CAD.

## Przepusty

ZKPRZEPUST prowadzi po własnej osi i profilu:

- rurę kołową: średnica wewnętrzna i grubość;
- przepust skrzynkowy: szerokość, wysokość w świetle i grubość;
- przekrój owalny: szerokość i wysokość w świetle oraz powiększenie półosi o grubość.

Profil oznacza rzędną wewnętrznego dna. Otwór pozostaje pusty. Koło i owal są aproksymowane 32 odcinkami, a ścianki stanowią osobne segmenty geometryczne. Owal nie jest matematycznym odsunięciem elipsy o stałą grubość po normalnej. W tej wersji typ rury określa geometrię; nie ma katalogu producentów ani obliczeń hydraulicznych / nośności.

Ściana czołowa na początku i na końcu jest włączana osobno. Ma otwór odpowiadający światłu przepustu. Wspólne parametry: szerokość, grubość i wysokość. Przy dopasowaniu do TIN pobierana jest najwyższa rzędna spośród 9 próbek na szerokości ściany + 0,20 m, co najmniej ponad otworem i grubością. Góra pozostaje pozioma; nie jest schodkowym odwzorowaniem terenu. Wybór 3DFACE / siatki trójkątowej w zagnieżdżonym XREF wykorzystuje istniejący mechanizm terenu. Brak pokrycia jest błędem, nie zerową rzędną.

Półki dla zwierząt: niezależne włączenie L/P, wspólna szerokość, poziom nad dnem i grubość. Geometria nie pozwala na półkę szerszą niż dostępne światło rury na zadanej wysokości. Nie ma jeszcze dojść do półek poza przepustem ani umocnień koryta.

## Belki istniejącego mostu

ZKMOST → Oparcie i obrót. Wybierz podporę i numer belki. Własny punkt oparcia ma X/Y/Z; można go wskazać w CAD. Dla danej belki ustawiasz niezależnie koniec na każdej podporze. Wyłączenie własnego punktu przywraca automatyczne odniesienie do płyty na podporze.

Belka prosta jest wyciągnięciem między końcami: prosta w planie i profilu. Nie śledzi niwelety między podporami. Belka po osi śledzi odsuniętą oś i spód płyty; zachowane ręczne punkty oparcia są w tym wariancie ignorowane. Obrót przekroju jest niezależnym parametrem całego zestawu belek, 0° oznacza pion; spadek poprzeczny go nie zmienia. Nie ma jeszcze osobnego obrotu dla każdej belki.

Generator sprawdza obrys i kolizję belek prostych z płytą. Przy pochyleniu lub niekorzystnej niwelecie trzeba obniżyć oparcia / zwiększyć odstęp. Nadbeton wyrównawczy nie jest automatycznie wyliczany ani modelowany jako osobna bryła.

## Rysunki i zapis

Rzut, bok, przekrój i rozwinięcie korzystają z geometrii po cięciach. Przebudowa obiektu odświeża wszystkie jego zapisane widoki w tej samej transakcji i zachowuje ich położenia. Model i rysunki aktualizują się po Zastosuj / ZKELEMENTBUILD / ZKMOSTBUILD; bez przebudowy zmiana źródła w CAD nie uruchamia generatora w tle.

Widoki pokazują krawędzie widoczne i zasłonięte. To rysunki geometryczne 1:1, bez automatycznego usuwania linii zasłoniętych i dokumentacji zbrojeniowej. Lekka siatka służy do pracy z geometrią, pełne bryły do operacji CAD. Zapis w DWG obejmuje źródła, stacje, parametry, cięcia i widoki.
