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
