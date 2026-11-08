# Próby wydania 0.22 w BricsCAD V26

- W układzie trzech rzutni na kopii mostu M-01 z terenem w XREF kliknięto przycisk w karcie Belki. Widocznych było pięć belek spośród 833 elementów modelu. Po przeliczeniu w otwartym edytorze porównano obraz cieniowanej rzutni z rysunkiem zawierającym tylko pięć belek. W przebiegu końcowym różnił się jeden piksel z ponad pięciu milionów.
- Zmiana karty na Pomost w trakcie izolacji pokazała 594 elementy pomostu. Po kliknięciu Pokaż cały obiekt porównano włączenie, zamrożenie i blokadę warstw ze stanem wyjściowym.
- Osobno sprawdzono starszą siatkę ze składowymi na zablokowanej warstwie pomostu. Po izolacji i przebudowie składowe belek miały warstwę belek.

# Próby wydania 0.21 w BricsCAD V26

- Na kopii ZB-01-plyta.dwg sprawdzono 324 osie prętów 3D i 324 osie w rzucie oraz zestawienie. Po wyłączeniu dolnej siatki pozostały 162 pręty. Kolejne przebudowy i ponowne otwarcie zapisanego DWG zachowały liczbę i ustawienia.
- Widok boczny przyczółka aktualizuje wymiar po wydłużeniu skrzydła z 5 do 7 m. Po obu przebudowach istnieje jeden tytuł widoku.
- W przyciętym, skalowanym i obróconym odnośniku sprawdzono odczyt terenu wewnątrz i poza obwiednią na rzędnej 102 m. Suma kontrolna źródłowego DWG pozostała taka sama.
- W aktywnej rzutni wykonano powiększenie do geometrii obiektu oraz izolację pomostu z kontrolą widoczności warstw wierzchołków i ścian siatek.
- Sprawdzono 349 warunków geometrii i rysunków, 40 kontroli interfejsu oraz 25 kontroli aktualizatora. Dwa zestawy testów natywnych V26 zaliczyły 18 i 9 prób.

# Walidacja 0.20

Automatyczne testy w oddzielnym, niezapisanym rysunku BricsCAD V26: ZKMOSTTEST 18/18 i ZKSESSIONTEST 9/9. Sprawdzono bryły i siatki przepustu, filtr obwiedni obróconego bloku i odczyt TIN, usunięcie filtra, izolację warstw oraz trzy rzutnie z geometrią przekroju i znacznikiem.

Do próby na rzeczywistym projekcie: wskazywanie terenu we własnym XREF, edycja obwiedni, zmiana stacji przekroju i rzędnej osi, powrót z izolacji po przebudowie oraz geometria stożków przy skośnych podporach.

# Próby 0.19 w BricsCAD V26

1. Po aktualizacji sprawdź napis ZK MOST 0.19. Przelicz istniejący przepust. W lekkim trybie wybierz rurę oraz ścianę z otworem: każda ma być jednym obiektem. W trybie pełnym sprawdź typ Bryła 3D i zachowany otwór. ZKMOSTTEST zawiera próby łączenia korpusów; jeszcze nie wykonano ich na działającym CAD.
2. Belki → Wyizoluj element: inne elementy i podkład mają zniknąć. Powiększ do elementu dopasowuje widok bez obrotu. Pokaż cały obiekt oraz zamknięcie edytora przywracają pierwotną widoczność. Przebuduj belki przy aktywnej izolacji.
3. Edytuj: wybierz obiekt na liście. Po prawej obraca się podgląd jego zapisanej geometrii CAD. Powiększ do obiektu pozostawia listę otwartą.
4. Nowy przyczółek: włącz skrzydło i skos podpory. Kąt 0 oznacza prostopadłość do ściany. Ustaw podcięcie i wskaż prostą dwuwierzchołkową polilinię; zmiana jej długości ma aktualizować skrzydło oraz istniejące widoki 2D. Sprawdź osobno A1/A2 i L/P.
5. Sprawdź z WR-M → Sprawdź geometrię. Płyta 0,20 m ma zgłaszać uwagę, 0,30 m — sprawdzony warunek grubości; brak danych o posadowieniu nie może dawać ogólnego wyniku zgodny.
6. Pomost: wpisz kapę L=3 m, P=1 m, pochylenia L=2%, P=-1%. Sprawdź górne powierzchnie, oparcie na płycie, krawężniki, podstawy barierek i odświeżone przekroje. Podpory: na liście mają być A1/A2 nawet bez filara pośredniego.
7. Instalator, deinstalator i okna mają ikonę ZK, aktualizator pokazuje 0.19.

# Próby aktualizatora 0.17

1. Po zainstalowaniu 0.17, przy dostępnym nowszym wydaniu, otwórz Aktualizacje i kliknij raz Sprawdź i zainstaluj aktualizację. Po pobraniu pozostaw aktualizator otwarty i zamknij BricsCAD. Instalator ma uruchomić się sam, bez ponownego kliknięcia.
2. Anuluj w trakcie oczekiwania: po zamknięciu CAD instalator nie może wystartować.
3. Gdy serwer odpowiada 504, komunikat powinien wskazywać kolejną próbę. Po czterech nieudanych próbach ma pojawić się czytelna informacja o niedostępnym GitHubie.
4. Testy automatyczne symulują proces CAD i błędy HTTP; pełne nadpisanie plików instalacji na rzeczywistym CAD pozostaje próbą instalacyjną użytkownika.

# Próby 0.16

1. Podświetlenie: Filary → wybierz P2; tylko P2 ma być w pełnym niebieskim kolorze ZK z wyraźnym obrysem. Obróć widok, przełącz kartę i zamknij okno — grafika tymczasowa ma zniknąć bez zmiany kolorów modelu.
2. Pomost: wpisz jezdnię L=5 m i P=3 m, kapy=2 m. Płyta ma 12 m, od osi 7 m w lewo i 5 m w prawo. Zwiększenie kapy nie zmienia obu jezdni. Sprawdź krawężniki, wyposażenie i rysunek przekroju.
3. Przyczółki: wybierz A1, klikaj korpus, skrzydło, płytę i nasyp na wspólnym schemacie. Zmieniaj długości i wysokości, sprawdź model i bok. Karty skrzydeł i dojazdu nie powinny być osobnymi kartami głównymi.
4. Rysunki: odśwież widoki przez Przelicz teraz. W skali 1:100 tekst wymiaru ma 0,25 jednostki modelu (m), DIMLFAC=100 i DIMSCALE=1. Sprawdź niezależność od bieżącego stylu wymiarowego CAD oraz brak ogromnych grotów i tekstów.
5. Właściwości linii rysunku: nazwa warstwy zawiera nazwę obiektu, rodzaj widoku, element (BELKI / SLUPY / KAPY itd.) i rodzaj krawędzi. Wymiary i opisy są oddzielnie.
6. Gzymsy i bariery: osobne rozstawy są zachowane; Wspólne stacje słupków wyrównuje obie linie na wybranej stronie. Zmiana jednej strony nie zmienia drugiej.
7. ZKMOSTTEST: dodatkowo sprawdza wymiar po nadaniu domyślnych ustawień bazy. Próba jest wycofywana; wynik natywny CAD raportuj oddzielnie od testów Core/WPF.

# Próby 0.15.0

1. Nowy obiekt → Most, nadaj nazwę, wybierz 2D / 3D / ZK Droga i teren. Utwórz drugi most i przepust; Edytuj ma pokazać wszystkie. Zamknij i otwórz DWG, powtórz edycję.
2. Przepust → Cała polilinia + Na żywo: skróć / wydłuż oś uchwytem. Sprawdź model, zakres i istniejące rysunki po zakończeniu polecenia.
3. Skrzydła przepustu: włącz A-L, A-P, B-L, B-P; ustaw różne kąty, a jedno poprowadź polilinią z trzech prostych odcinków. Przesuń wierzchołek źródła, sprawdź przebudowę.
4. Most po łuku: automat belek wybiera po osi; wybór ręczny Prosto wyłącza automat. Przełączaj karty i sprawdzaj zielone wyróżnienie; przy wyposażeniu zmieniaj L/P względem strzałki A→B.
5. + Podpora kilka razy: nie powinna trafiać na istniejącą. Wpisz kilometraż 1+240, odległość od początku obiektu i wskaż miejsce na osi; wszystkie odczyty mają być zgodne.
6. Poprzecznice: wyłącz podpory, włącz odstęp 8 m, dodaj stacje 25;35 i skos. Sprawdź model i rzut.
7. Przyczółek i dojazd: słupowy, skrzydło podwieszone / podcięte, płyta przejściowa. Sprawdź bok, przekrój, brak fundamentu pod skrzydłem podwieszonym i połączenie skarpy ze stożkiem.
8. Zmień nazwę M-01 na MD-02, przelicz: nowe prefiksy warstw, model i rysunki tego samego obiektu. Zduplikowana nazwa powinna być odrzucona bez utraty modelu.
9. ZKMOSTTEST: nowe próby osi 3D i wielu obiektów; wszystkie dane testowe są wycofywane. Wynik natywnego CAD raportuj oddzielnie od testów Core/WPF.

# Próby wersji 0.14.0

1. ZKPRZEPUST powinien od razu otworzyć okno. Wybierz oś, wskaż dwa końce w odwrotnej kolejności i sprawdź zakres.
2. Zmień rzędne dna A/B, średnicę, półki i ściany. Model powinien odświeżyć się bez zamykania okna; obróć widok CAD przy otwartym oknie.
3. Wstaw widoki przez Model i rysunki. Zmień średnicę i sprawdź rzut, bok i przekrój.
4. Wyłącz Na żywo: model powinien poczekać na Przelicz teraz. Zmień teren XREF bez zmiany parametrów i użyj Przelicz teraz.
5. ZKMOST: otwarte okno mostu pozwala obracać model. Zmiana szerokości i przekroju belek odświeża widoki.
6. Podczas LINE kliknięcie Wybierz oś powinno poprosić o zakończenie polecenia, bez wysyłania wyboru do LINE. Przełącz DWG: edytor poprzedniego rysunku ma być nieaktywny.
7. ZKMOSTRIBBON: przyciski w kolumnach po trzy rzędy. Wszystkie dawne publiczne polecenia działają.

# Próby w BricsCAD V26

Wyniki wykonane poza CAD: 255/255 testów obliczeń/projekcji oraz 19/19 kontroli WPF. Zrzuty interfejsu zostały wyrenderowane i obejrzane. Kompilacja DLL: zero błędów i ostrzeżeń.

Test natywny nie został wykonany w tej sesji — narzędzie sterowania nie uzyskało dostępu do aplikacji przed upływem czasu. Nie należy traktować kompilacji ani testów core jako potwierdzenia działania ACIS i wyborów w rzeczywistym DWG.

## 1. Automatyczna próba natywna

Po wczytaniu ZKMost-start.lsp wpisz ZKMOSTTEST. Polecenie sprawdza loft zmiennego przekroju po łuku, SLICE i zachowaną stronę, dodatnią objętość, odczyt bryły do rysunków, cztery widoki, zapis źródeł i cięć, lekką siatkę, przepust skrzynkowy ze ścianami i półkami oraz blok z bryłą i obrotem. Cała geometria i rekordy próbne są w transakcji bez Commit; po próbie znikają przez wycofanie transakcji. Wynik w historii F2: PASS albo TEST FAIL / komunikat błędu. Oczekiwane 12/12.

## 2. Własny przekrój

Narysuj oś z łukiem i prostokąt 5 × 1 m w XY. ZKPRZEKROJ, wskaż zakres 0–40 m, profil rzędna 100 + 1%, pierwszy przekrój ze skalą wysokości 1, końcowy ten sam ze skalą 3. Wybierz pełne bryły. W podglądzie porównaj rzut i aksonometrię, zatwierdź. Sprawdź przekrój A 5 × 1 i B 5 × 3, zmianę Z oraz ciągłość łuku.

ZKELEMENTVIEW: wstaw kolejno rzut, bok, przekrój i rozwinięcie. Zmień wierzchołek źródłowej polilinii przekroju, ZKELEMENTBUILD: wszystkie cztery widoki powinny się odświeżyć bez przesunięcia punktów wstawienia.

## 3. Trwałe cięcie

Narysuj ukośną LINE na początku elementu, tak aby przecinała całą szerokość. ZKDOCIECIE: wskaż bryłę, linię, zachowaną stronę. Po zatwierdzeniu koniec i rysunki powinny odpowiadać cięciu. Zmień końcową skalę przekroju przez ZKELEMENT albo przesuń linię cięcia i przelicz. Cięcie ma pozostać. Dodaj drugie cięcie. ZKCIECIA: wyłącz pierwsze, sprawdź odzyskanie fragmentu.

Powtórz na belce istniejącego mostu: ZKDOCIECIE, a następnie zmiana jej przekroju w ZKMOST. Wróć ZKCIECIA i wyłącz operację.

## 4. Ręczna obróbka

Nowy element po osi w pełnych bryłach → ZKODLACZ. Przytnij / obróć / połącz bryłę narzędziami CAD. ZKELEMENTBUILD: obróbka pozostaje, rysunki odświeżają się. Jeśli operacja stworzyła nową bryłę bez oznaczeń, dodaj ją przez ZKPRZYPISZ, wskazując najpierw pozostający element odłączonego obiektu.

## 5. Belki prefabrykowane

W istniejącym moście wybierz proste belki T. Oparcie i obrót: podpora A1, B3, własny Z, potem A2, B3 z innym Z. Sprawdź prostą w planie i profilu oraz właściwe położenie łożysk. Obrót 0° ma dawać pionowy przekrój niezależnie od spadków płyty. Zadaj np. 5°, sprawdź model i przekrój. Przełącz na „Po osi”: wraca śledzenie niwelety, ręczne oparcia są ignorowane; po powrocie na proste nadal są zapisane.

## 6. Przepust i XREF

Podepnij teren jako odnośnik z 3DFACE / trójkątami. Narysuj oś przepustu i profil dna. ZKPRZEPUST: koło, średnica 1,5 m, grubość 0,2 m, ściany czołowe, wybierz teren z odnośnika, obie półki. Sprawdź pusty otwór, rzędną dna, poziom ścian oraz półki w świetle. Wstaw widoki. ZKELEMENT: zmień średnicę / poziom półek, zatwierdź i sprawdź aktualizację widoków. Powtórz ze skrzynką i owalem. Przesuń odnośnik terenu, przelicz: rzędne ścian mają zostać odczytane ponownie.

Brak pokrycia TIN lub zbyt szeroka półka ma zgłosić błąd i zachować poprzedni model.

## 7. Bloki i zapis

ZKROZMIESC: wskaż blok latarni, oś, zakres i rozstaw. Sprawdź styczną w łuku, skalę bloku i rzędne. ZKELEMENT: zmień rozstaw, przelicz. Zapisz DWG, zamknij i otwórz; po wczytaniu loadera sprawdź ZKELEMENTBUILD, rysunki i zapisane cięcia.

## Do zgłoszenia po próbie

Podaj polecenie, etap, pełny komunikat z F2 i czy wybrany był lekki model czy pełne bryły. Przy błędzie geometrycznym przyda się mały DWG z osią, przekrojem i linią cięcia; dla problemu terenu także odpowiedni odnośnik.

## 8. Rysunek ogólny i arkusz

ZKMOST → Rysunki → Ujednolić istniejące widoki. Zastosuj: sprawdź wymiary i rzędne w dotychczasowych położeniach. ZKMOSTARKUSZ: A1, rozwinięty, kilometraż środka. Porównaj skale rzutni, plan na istniejącym XREF, przekrój i bok. Zmień szerokość, przekrój belki lub rzędną oparcia: wartości i rzutnie mają się odświeżyć, nazwy kierunków pozostać. Przy niewystarczającej skali ma pojawić się ostrzeżenie, a nie utrata modelu. Sprawdź PDF i ustawienia urządzenia na swoim stanowisku.
