# ZK Most 0.18 — widoczny numer załadowanej wersji

Numer wersji jest widoczny w nagłówku i pasku tytułu edytora mostu, przepustu, listy obiektów, podglądu i aktualizatora. Numer pochodzi ze wspólnej stałej kompilowanej z programem, a nie z pliku instalatora na dysku. Dzięki temu okno wskazuje wersję faktycznie załadowanego modułu.

Jeżeli po instalacji nadal widzisz dawny układ osobnych kart Skrzydła i stożki / Przyczółek i dojazd, BricsCAD prawdopodobnie ładuje starszą paczkę. Zamknij wszystkie procesy CAD, zainstaluj aktualną paczkę i używaj loadera z %LOCALAPPDATA%/ZKProjekt/Most/ZKMost-start.lsp zamiast kopii ze starego folderu.

# ZK Most 0.17 — aktualizacja po zamknięciu BricsCAD i ponawianie 504

Sprawdź i zainstaluj aktualizację: jedno kliknięcie sprawdza wersję, pobiera instalator i weryfikuje rozmiar oraz SHA-256. Jeżeli BricsCAD jest otwarty, aktualizator pozostaje uruchomiony i czeka. Po zamknięciu wszystkich procesów BricsCAD uruchamia cichą instalację bez drugiego kliknięcia i bez ponownego otwierania aktualizatora. Pozostaw okno aktualizatora otwarte. Anuluj lub zamknięcie tego okna przerywa oczekiwanie i nie uruchamia instalacji.

Ponawianie po HTTP 504, 502, 503, 500, 408, 429 i błędach połączenia: maksymalnie cztery próby z przerwami 1, 2 i 4 s. Obsługiwany jest też Retry-After serwera, ograniczony do 10 s. Sprawdzenie odpowiedzi ma limit 30 s na próbę. Ponawianie dotyczy metadanych wydania oraz odpowiedzi pobierania instalatora. Stałe błędy (np. 404) nie są ponawiane. Po wyczerpaniu prób pojawia się czytelny komunikat zamiast surowego błędu HTTP.

Automat w tle korzysta z tego samego oczekiwania na CAD. Błąd pobierania nie przesuwa kolejnego sprawdzenia o 12 godzin. Instalator blokuje równoległe uruchomienie dwóch instalacji, np. z ręcznego i automatycznego aktualizatora.

Uwaga dotycząca pierwszego przejścia: aktualizator w starszej wersji 0.16 zachowuje dotychczasowy sposób działania do czasu zainstalowania 0.17. Można zainstalować paczkę 0.17 ręcznie po zamknięciu CAD; kolejne aktualizacje będą już używać nowego przebiegu.

Testy obejmują 504→502→200, cztery nieudane próby 504, brak ponawiania 404, weryfikację pliku po ponowieniu, oczekiwanie na CAD, pojedyncze uruchomienie instalatora oraz anulowanie. W testach instalator nie jest uruchamiany na komputerze.

# ZK Most 0.16 — poprawki rysunków i wspólna karta przyczółka

Numeracja wydań od tej paczki: 0.16, 0.17 itd. Instalator, tag GitHub i wersja aktualizatora używają dwóch członów.

Pomost: osobne szerokości jezdni L/P. Szerokość płyty jest sumą obu jezdni i kap. Zwiększenie kapy poszerza obiekt bez zabierania szerokości jezdni. Obsługiwany jest przekrój asymetryczny względem osi: płyta, kapy, krawężniki, wyposażenie, skrzydła i opisy korzystają z właściwych odległości od osi. Przy otwieraniu starego obiektu szerokości jezdni są wyznaczane z jego dotychczasowej szerokości, bez zmiany geometrii.

Przyczółki: jedna karta ze wspólnym schematem korpusu, fundamentu, skrzydła, płyty przejściowej i nasypu. Wybierz element z listy lub kliknij schemat; jego parametry pojawiają się obok. Dotychczasowe dwie osobne karty skrzydeł i dojazdu nie występują w głównej nawigacji. Filary mają osobną kartę i nie mieszają się z przyczółkami.

Rysunki: poprawiono kolejność ustawiania stylu wymiarów po SetDatabaseDefaults. Wymiary otrzymują własną skalę, wysokość tekstu, wielkość znaków, przelicznik m → cm i wyłączoną anotatywność. Poprawka działa po odświeżeniu istniejących widoków. Dodano natywną próbę ZKMOSTTEST weryfikującą rzeczywiste właściwości wymiaru.

Warstwy 2D: podział według elementu i rodzaju krawędzi, np. M-01_RYS_PRZEKROJ_1_BELKI_PRZEKROJ, M-01_RYS_BOK_2_SLUPY_WIDOCZNE. Osobne warstwy: WYMIARY, OPISY, RZEDNE, SPADKI, OSIE, TEREN i wypełnienia poszczególnych elementów. Podział jest stosowany także do prostych starszych widoków przy ich regeneracji.

Podział funkcjonalny w Rysunki dotyczy opisów, nie geometrii. Domyślne opisy wynikają teraz z jezdni L/P i kap. Własny podział pozostaje opcją do niestandardowego opisu; jego szerokości nadal muszą sumować się do szerokości płyty.

# Dalsze zmiany 0.16 — wyraźne podświetlenie w kolorze ZK

Poprawiono przezroczystość grafiki tymczasowej: podświetlenie jest teraz nieprzezroczyste i używa niebieskiego AccentBrush wspólnej palety ZK. Dodano wyraźny obrys krawędzi bez szwów triangulacji. Karta Podpory wyróżnia konkretnie podporę wybraną na liście (np. P2), a nie wszystkie podpory naraz. Kolory i warstwy rzeczywistych obiektów nie są zmieniane.

Gzymsy i bariery: opcja Wspólne stacje słupków łączy rozstaw linii przy jezdni i przy krawędzi kapy na wybranej stronie. Bez niej obie linie zachowują niezależne wartości Rozstaw słupków [m]. Wspólne stacje oznaczają punkty względem tej samej osi; na łuku odległości mierzone po różnych odsuniętych liniach mogą być różne. Rysunki odświeżają się jak dotychczas.

Kompilacja i testy Core/WPF są wykonywane automatycznie. Ostateczna ocena kontrastu i grubości obrysu w stylach wizualnych BricsCAD wymaga próby w otwartym CAD.

# ZK Most 0.15.0 — obiekty w DWG i geometria dojazdów

Nowy obiekt (ZKMOSTNEW) otwiera wybór Most / Przepust. Edytuj (ZKMOST) wyświetla listę mostów i przepustów zapisanych w DWG. Obsługiwanych jest wiele mostów, a zapis starego pojedynczego mostu jest zachowywany i dołączany do listy. ZKPRZEPUST nadal działa jako skrót. Pierwsza karta zawiera nazwę, oś, źródło niwelety i teren. Dotychczasowe publiczne polecenia pozostają bez numerów.

Oś: ZK Droga, polilinia 2D ze stałą rzędną lub osobnym profilem, otwarta polilinia 3D z odcinków prostych. Kilometraż osi 3D jest mierzony w planie, wysokość jest interpolowana z jej wierzchołków. Odcinki pionowe / zerowe w planie są odrzucane. Dla przepustu Cała polilinia aktualizuje zakres po skróceniu i wydłużeniu osi. Przy Na żywo zmiana obserwowanej osi / profilu / polilinii skrzydła wywołuje przebudowę po zakończeniu polecenia CAD. Bez Na żywo użyj Przelicz teraz.

Przepust: cztery niezależne skrzydła A-L, A-P, B-L, B-P. Przebieg z kąta i długości albo ze wskazanej otwartej polilinii 2D (proste odcinki, bez bulge). Bliższy koniec jest początkiem; przebieg zostaje przesunięty tak, aby zaczynał się przy narożniku ściany. Z polilinii pobierany jest przebieg XY, rzędne wynikają z góry ściany, obniżenia końca i głębokości podstawy. Każde skrzydło ma własną grubość. Zmiana polilinii jest odczytywana ponownie przy przeliczeniu.

Most: automatyczny dobór prowadzenia belek jest domyślnie aktywny dla nowych obiektów. Łuk / zmiana kierunku daje prowadzenie po odsuniętej osi. Ręczny wybór prowadzenia wyłącza automat; można go ponownie włączyć w Belki. Proste prefabrykaty pozostają dostępnym wyborem.

Podpory: kilometraż osi km+m, stacja od początku osi, odległość od początku obiektu i wskazanie w CAD są powiązane. Nowa podpora trafia w największą wolną lukę. Początek zakresu przesuwa kolidujący koniec o 1 m dalej (dla przepustu z ograniczeniem do długości osi).

Poprzecznice: na podporach, w środku przęseł, co zadany odstęp od A1, własne stacje wpisane średnikami lub wskazane w CAD. Dodatkowe poprzecznice mogą mieć wspólny zadany skos. Powtarzające się stacje są scalane.

Przyczółek i dojazd: wariant ścianowy lub słupowy w nasypie, skrzydło pełne, podcięte lub podwieszone. Podwieszone skrzydło nie generuje fundamentu. Płyta przejściowa jest osobno włączana przy każdym przyczółku: długość, grubość, zagłębienie pod niweletą i spadek od przyczółka. Stożek ma teraz także połączoną koronę i skarpę wzdłuż skrzydła, zamiast samego wachlarza za końcem ściany. Stopy skarp mogą nadal wynikać z terenu TIN / 3DFACE w XREF.

Karty podświetlają właściwe elementy zielonymi grafikami tymczasowymi, bez zmiany właściwości obiektów. Przy wyposażeniu wyróżniana jest wybrana strona. Strzałka A → B pokazuje rosnący kilometraż; L/P wynikają z tego kierunku, niezależnie od obrotu widoku.

Warstwy i arkusze mają prefiks z nazwy obiektu, np. M-01_Pomost, M-01_Ustroj, M-01_Podpory, M-01_RYS_RZUT_1. Nazwy o jednakowym prefiksie są odrzucane, aby nie mieszać warstw różnych obiektów. Przy przebudowie istniejące warstwy elementów modelu są przemianowywane na czytelne. Poprawiono przycięte cyfry w polach i wyświetlanie nazw podpór.

Rysunki nadal korzystają ze wspólnej wynikowej geometrii i są odświeżane z przebudową. Wskazane rozwiązania geometrii są konfigurowalne: nie wykonują obliczeń nośności ani automatycznego wymiarowania konstrukcyjnego.

Źródło odniesienia dla skrzydeł, nasypu i płyt przejściowych: Ministerstwo Infrastruktury, WR-M-11, wersja 01 z 2021-03-02, rozdziały 6.3.2 i 7.2: https://www.gov.pl/attachment/2e6cbd2f-fa3d-497b-a384-9295cf7da368 . Domyślne wymiary są parametrami modelera, a nie sprawdzeniem zgodności projektu z wytycznymi.

Weryfikacja 0.15.0: 295/295 Core, 32/32 WPF, 14/14 aktualizatora offline; kompilacja bez ostrzeżeń. Weryfikacja natywnych funkcji CAD (grafiki tymczasowe, reakcja na uchwyty, zapis wielu obiektów i bryły po podcięciu) wymaga prób w BricsCAD V26. ZKMOSTTEST rozszerzono o oś 3D i zapis dwóch niezależnych mostów; test wycofuje swoją transakcję.

# ZK Most 0.14.0 — graficzny przepust i praca bez zamykania okna

ZKPRZEPUST otwiera graficzny edytor w stylu ZK: Oś i profil, Rura i półki, Ściany i teren, Model i rysunki. Wybierz oś, ustaw zakres i rzędne dna przy schemacie, potem przekrój i ściany. Wskazywanie w CAD dotyczy geometrii, nie wpisywania parametrów. Edycja istniejącego przepustu: ZKELEMENT i wskazanie elementu.

Okna mostu i przepustu nie blokują CAD. Na żywo przelicza po krótkiej pauzie; Przelicz teraz wymusza przebudowę również bez zmiany parametrów. Zmiany odświeżają zapisane widoki. Wyłącz Na żywo, jeśli chcesz zebrać kilka zmian przed przebudową. Błąd przebudowy jest pokazywany w oknie; poprzednia transakcja modelu pozostaje zachowana.

Wstążka ma kolumny po trzy rzędy. Publiczne polecenia pozostają bez numerów. Zakres przepustu można wskazać w dowolnej kolejności; dwa wskazania tego samego miejsca są odrzucane. Poprawiono samoprzecięcia segmentów płyty na załamaniach osi: płyta, kapa i krawężnik korzystają z rzeczywistej geometrii odsunięć.

Weryfikacja: 258/258 geometrii, 21/21 interfejsu WPF, 14/14 aktualizatora offline; kompilacja bez ostrzeżeń. Praca okien modeless, kolejka wskazywania, natywna wstążka i odświeżanie po operacjach CAD wymagają testu w BricsCAD V26. Testy automatyczne nie zastępują próby w otwartym CAD.

# ZK Most 0.13.1 — standard rysunku ogólnego

Na podstawie przekazanego przykładu dodano: przekrój z łańcuchami wymiarowymi, rzędnymi i spadkami; bok z osiami podpór, wymiarami, nazwami kierunków i wypełnieniami; plan na rzeczywistym podkładzie WCS oraz arkusz A1/A2 z niezależnymi skalami rzutni. Ograniczono szwy geometrii i ukryte wnętrze ustroju.

ZKMOST → Rysunki; ZKMOSTPODGLAD — podgląd; ZKMOSTARKUSZ — skład arkusza. W zakładce Rysunki przycisk Ujednolić istniejące widoki przekształca starsze widoki bez zmiany ich miejsca. Szczegóły: RYSUNKI.md.

Testy geometrii i WPF obejmują rysunki i podglądy; natywne wymiary, wypełnienia, arkusz PDF i XREF wymagają prób w rzeczywistym CAD. Prześwit z TIN jest minimum próbkowanym, nie kontrolą normową. Instalator pozostaje bez podpisu wydawcy.

# ZK Most 0.12.0 — instalator, wygląd ZK i aktualizacje

Instalator: https://github.com/kidznok/ZK-Mosty/releases/latest

Wspólna paleta ZK AutoDWG, przełączniki, zaokrąglone kontrolki i belka ZK Support / Co nowego / Pomoc / Ustawienia. Formularz ZK Support pochodzi ze wspólnej biblioteki ZK.UI.Wpf, z wariantami net8 dla CAD oraz net10 dla aplikacji desktopowych.

Aktualizator obsługuje numerowane instalatory. Gotowy plik wgrany do katalogu głównego repozytorium main jest publikowany automatycznie przez workflow jako stabilne Release. Program sprawdza rozmiar i SHA-256, następnie czeka na zamknięcie BricsCAD i instaluje aktualizację. Przełącznik pozwala wyłączyć automat. Szczegóły: INSTALACJA.md.

Weryfikacja: 227/227 geometrii, 17/17 WPF, 16/16 aktualizatora (w tym rzeczywiste pobranie opublikowanego EXE i kontrola SHA-256, bez uruchamiania instalacji). NSIS i DLL kompilują się bez błędów i ostrzeżeń. Pełnej instalacji i cyklu aktualizacji w rzeczywistym CAD jeszcze nie wykonano. Instalator nie ma podpisu certyfikatem wydawcy.

# Aktualizacja: modelowanie po osi, przepusty i trwałe cięcia

Gotowe do prób w BricsCAD V26: uniwersalny przekrój po osi z przekrojami na stacjach, rozmieszczanie bloków, przepusty, zapisane docięcia oraz niezależne punkty oparcia i obrót belek mostu.

Wczytaj ponownie **ZKMost-start.lsp**. Dotychczasowe polecenia pozostają bez numerów. Na wstążce ZK Most są panele „Modelowanie po osi” i „Przepusty i obróbka”. Kilka obiektów po osi i przepustów może współistnieć z mostem w jednym DWG.

Sprawdzone poza CAD: **227/227** testów geometrii i projekcji, **17/17** kontroli WPF; kompilacja bez błędów i ostrzeżeń. Test natywnego CAD pozostaje do uruchomienia: **ZKMOSTTEST**. Próba uruchomienia aplikacji przez narzędzie sterowania wygasła na etapie dostępu do aplikacji; nie ma wyniku testu natywnego.

Instrukcja: **NOWE-NARZEDZIA.md**. Scenariusze prób: **TESTY-CAD.md**.

Dwie niezależne linie wyposażenia na każdej stronie: „Przy krawędzi kapy” i „Przy jezdni”. Wybierz linię w zakładce Gzymsy i bariery, a następnie jej typ, wysokość i odsunięcie. Obie linie mogą działać jednocześnie. Odsunięcia mierzone są do środka od zewnętrznej krawędzi pomostu; dla bariery przy jezdni domyślnie szerokość kapy minus 0,15 m. Wysokości liczone są od lokalnej góry kapy, z osobnym przesunięciem podstawy. Zastosuj aktualizuje model oraz wszystkie zapisane widoki 2D. Polecenia pozostają bez zmian.

Weryfikacja: 171/171 testów obliczeń i projekcji, 15/15 kontroli WPF, kompilacja bez ostrzeżeń i błędów. Nie wykonano testu wewnątrz BricsCAD.

# Wyposażenie krawędzi pomostu

Nowa zakładka **Gzymsy i bariery**, osobno dla L/P: gzyms prostokątny/trapezowy, balustrada, bariera stalowa/betonowa albo brak. Wszystko podąża za osią i profilem i jest uwzględniane w rysunkach. Szczegóły: [GZYMSY-I-BARIERY.md](GZYMSY-I-BARIERY.md).

# Nowość: stopy stożków z terenu w XREF

Dostępny jest wybór 3DFACE / siatki z odnośnika oraz automatyczne przecięcie skarpy z TIN. Nie trzeba wpisywać Z stopy. Instrukcja: [TEREN-Z-ODNOSNIKA.md](TEREN-Z-ODNOSNIKA.md). Poniższe opisy ręcznej Z dotyczą trybu po wyłączeniu **Stopa z terenu**.

# ZK Most — dokładność belek, lekki podgląd i stałe polecenia

## Uruchomienie

Wczytaj **ZKMost-start.lsp** przez APPLOAD. Loader podpina nową implementację pod te same polecenia: **ZKMOST**, **ZKMOSTBUILD**, **ZKMOSTRIBBON** i pozostałe nazwy bez końcówek. Zastępuje wejścia poleceń również wtedy, gdy w procesie są starsze DLL. Wstążka używa stałych nazw i usuwa wcześniejsze zakładki wersji 0.1–0.4.

Sam loader nie przebudowuje geometrii. Otwórz istniejący obiekt poleceniem **ZKMOST**, wybierz parametry i kliknij **Zastosuj · model i rysunki**. Bieżące biblioteki są w `plugin/current`; numer w nazwie wewnętrznego pliku DLL nie jest częścią poleceń użytkownika.

## Poprawione powiązanie skrzydła i stożka

Poprzedni wachlarz stożka zaczynał się przy narożniku przyczółka i mógł przecinać skrzydło. Teraz przy włączonym skrzydle korona stożka znajduje się za jego końcem, na zewnętrznej stronie ściany. Cały sektor pozostaje po zewnętrznej stronie płaszczyzny skrzydła i poza jego końcem; położenie uwzględnia A1/A2, L/P, grubość i kąt skrzydła. Bez skrzydła stożek znajduje się za ścianą przyczółka, po stronie nasypu.

Automatyczna korona leży domyślnie 0,15 m poniżej góry końca skrzydła. Pole „Korona pod końcem” zmienia tę różnicę. Nie jest już brana niezależna rzędna jezdni przy przyczółku. Ręczna korona powyżej końca skrzydła jest odrzucana.

Automatyczna wysokość skrzydła uwzględnia niweletę dojazdu w miejscu końca, a nie samą rzędną początkową. Początek i koniec korzystają z odniesienia do tej samej bocznej linii drogi, z zadanym obniżeniem. W rzucie końca na oś uwzględniana jest geometria osi, jeśli adapter udostępnia takie rzutowanie. Poza końcem osi niweleta jest przedłużana liniowo jej skrajnym spadkiem — to jawne założenie, nie odczyt terenu.

W zakładce Skrzydła i stożki:
- „Ręczne Z ściany” pozwala wpisać Z początku, Z końca oraz Z dołu ściany. Fundament skrzydła jest pod tym dołem, z grubością fundamentu przyczółka.
- „Korona Z ręcznie” pozwala wpisać osobną rzędną korony stożka.
- „Stopa stożka Z” nadal jest rzędną podawaną przez użytkownika. Nie istnieje automatyczne dopasowanie stopy do powierzchni terenu. Błędnie podana Z stopy nadal oznacza błędne położenie względem faktycznego gruntu.

Wartości ręczne są wartościami bezwzględnymi w układzie wysokościowym rysunku; po włączeniu trybu trzeba ustawić właściwe rzędne projektu. Nie należy traktować liczb domyślnych jako pomierzonych rzędnych terenu.

Testy kontrolują brak przecięcia z całym skrzydłem w planie dla A1/A2 i L/P, wysokość korony względem końca, wpływ niwelety dojazdu, ręczne rzędne i odrzucenie korony ponad ścianą. Nie odczytano DWG użytkownika i nie wykonano tej poprawki w BricsCAD. Natywne zachowanie i faktyczne rzędne terenu wymagają sprawdzenia na rysunku. Wariant lekki oraz aktualizacja rysunków pozostają aktywne.

## Wskazywanie zakresu na osi

Na zakładce **Pomost** przy A1 i A2 są przyciski **Wskaż na osi**, a pośrodku **Wskaż zakres**. Okno jest czasowo oddawane do interakcji CAD. Kliknięte miejsce jest rzutowane na najbliższy punkt zapisanej osi mostu; pole dostaje odległość od początku tej osi. W wierszu poleceń podawany jest również kilometraż z uwzględnieniem początku kilometrażu.

Wskaż zakres pobiera dwa punkty i dopiero po ich poprawnym wskazaniu zmienia oba końce. Esc podczas wyboru zachowuje dotychczasowe wartości. Zakres musi być rosnący i mieć co najmniej 0,1 m. Skrajne przyczółki podążają za wybranym początkiem i końcem; podpory pośrednie zachowują własne stacje. Po zmianie zakresu należy je w razie potrzeby dostosować przed Zastosuj. Przebudowa nadal odświeża zapisane rysunki.

## Dokładność belek

W zakładce **Belki**:

- **Dokładność [mm]** — tolerancja adaptacyjnego podziału. Większa liczba dopuszcza większą odchyłkę i zwykle wymaga mniej przekrojów. Zakres 0,1–1000 mm; domyślnie 20 mm.
- **Maks. krok belki [m]** — niezależny krok belki, bez zmieniania płyty i wyposażenia. Zakres 0,25–20 m; domyślnie 5 m.

Punkty charakterystyczne osi i niwelety nadal obowiązują. Maksymalny krok nie gwarantuje jednakowej odległości przekrojów: silnik dodaje punkty wymagane przez geometrię i dokładność. Stara stała tolerancja 5 mm została usunięta. Wybrana dokładność dotyczy obliczanej geometrii belek oraz rysunków 2D.

## Lekki podgląd

W zakładce **Oś i widoczność**:

- **Model w CAD → Lekki podgląd (siatka)** — domyślny tryb. Zastępuje natywne loftowanie i wyciąganie Solid3d lekkimi PolyFaceMesh. Każda część ma własną siatkę i zachowuje identyfikator oraz poziom pracy.
- **Krok lekkiego podglądu [m]** — gęstość przekrojów widocznej siatki belek. Zakres 1–25 m, domyślnie 8 m. Zmienia tylko podgląd 3D.
- **Model w CAD → Pełne bryły 3D** — przy następnym Zastosuj powstają ponownie bryły, w tym loft belek. Jest to kosztowniejszy tryb do pracy z bryłami.
- Dotychczasowy krok modelowania ma teraz nazwę **Krok płyty i wyposażenia [m]**.

Siatka podglądu nie jest zamkniętą bryłą do obliczania objętości. Pokazuje powierzchnie boczne, może mieć otwarte czoła i pomija część przekrojów pośrednich. Dla bardzo dużej liczby przekrojów dodatkowo ogranicza liczbę wierzchołków do bezpiecznego zakresu PolyFaceMesh. Nie stosuj jej do przedmiaru brył.

## Rysunki pozostają aktualne

Zarówno **Zastosuj · model i rysunki**, jak i **ZKMOSTBUILD** regenerują zapisane widoki w tej samej transakcji co model. Rzut, bok, rozwinięcie i przekroje zawsze korzystają z pełnego obliczonego ciągu przekrojów według ustawionej dokładności belek. Nie korzystają z rzadszej siatki podglądu. Zachowują położenie i kilometraże.

Testy porównują rysunki z trybu pełnego i lekkiego przy tych samych parametrach: wyniki są identyczne. Zmiana dokładności belek może zmienić również rysunki — jest to świadoma zmiana dokładności geometrii. Zmiana samego kroku lekkiego podglądu nie zmienia rysunków.

## Dodatkowe usprawnienia

Odległości wierzchołków osi źródłowej i odsuniętych osi belek są buforowane raz na przebudowę. Wyznaczanie punktów nie powtarza już dla każdego przekroju natywnych odczytów odległości i konwersji parametru. Odsunięte krzywe są zwalniane po zakończeniu pracy.

Po przebudowie w wierszu poleceń pojawiają się tryb, dokładność, liczba przekrojów obliczeniowych i podglądu oraz osobne czasy obliczeń i zapisu CAD/rysunków. Pozwala to rozróżnić koszt geometrii od kosztu natywnego rysowania. Nie wykonano pomiaru przyspieszenia w rzeczywistym BricsCAD.

## Sprawdzenie

- Kompilacja SDK BricsCAD V26/.NET 8: 0 błędów, 0 ostrzeżeń.
- **171/171** testów obliczeń/projekcji. Dodatkowo sprawdzono wpływ tolerancji i kroku na liczbę przekrojów, redukcję podglądu, brak modyfikacji geometrii rysunkowej i identyczność wszystkich typów rysunków pomiędzy trybami.
- **15/15** kontroli WPF. Nowe pola, przeliczenie mm na metry, wybór obu trybów i zapis parametrów działają w niezależnym uruchomieniu WPF.
- Obejrzano rendery obu zakładek z nowymi ustawieniami.
- Sprawdzono składnię nawiasów loadera oraz zgodność wszystkich 17 stałych nazw poleceń z wewnętrznymi wejściami DLL.

Nie wykonano APPLOAD, tworzenia PolyFaceMesh, nadpisania poleceń LISP ani pełnej przebudowy w BricsCAD. Natywny wybór punktów przez EditorUserInteraction także nie był wykonany. Ich zachowanie i rzeczywisty czas wymagają potwierdzenia w aplikacji. Logi: `build-results-current.txt`, `test-results-current.txt`, `ui-results-current.txt`.




