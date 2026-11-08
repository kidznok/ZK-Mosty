# ZK Most 0.13.0 — rysunek ogólny

Pierwszy standard na podstawie przekazanego przykładu: plan sytuacyjny, przekrój poprzeczny i widok boczny / rozwinięty. Wartości są wyliczane z modelu; przykład nie jest odrysowany z wpisanymi na sztywno wymiarami.

## Najkrótsza ścieżka

1. ZKMOST → zakładka Rysunki: skale planu, przekroju i boku; wymiary, rzędne, spadki, wypełnienia, linie zasłonięte i kierunek patrzenia.
2. Wpisz opcjonalne nazwy kierunków, np. nazwy ulic. Własny podział funkcjonalny pozwala nazwać i zwymiarować pasy, chodnik i drogę rowerową. Suma szerokości musi odpowiadać szerokości płyty. Dla strefy można wybrać kierunek ruchu: do początku lub końca osi; pojawi się symbol i odpowiednia nazwa kierunku. To podział opisowy — nie przebudowuje kap ani nawierzchni.
3. ZKMOSTPODGLAD: biały podgląd rysunków, bez podkładu mapowego. Przełącz zakładki RZUT / PRZEKROJ / BOK / ROZWINIECIE.
4. ZKMOSTARKUSZ: wybierz A1 lub A2, bok rzeczywisty lub rozwinięty i kilometraż przekroju. Powstaje układ: plan po lewej, przekrój u góry po prawej, bok poniżej. Model pozostaje w metrach 1:1; arkusz jest w mm, rzutnie mają przelicznik 1000 / mianownik skali.
5. Sprawdź urządzenie i format w ustawieniach wydruku. Jeśli dostępne jest urządzenie PDF i pasujący format ISO, program wybierze je automatycznie; konfiguracje drukarek różnią się między stanowiskami.

Nowy arkusz sprawdza, czy widoki mieszczą się przy wybranych skalach. Jeśli nie, wybierz większy mianownik w zakładce Rysunki lub większy format. Przy późniejszej zmianie modelu rysunki odświeżą się nawet wtedy, gdy zaczną wychodzić poza rzutnię — program ostrzeże o potrzebie zmiany skali.

## Widoki pojedyncze

Dotychczasowe ZKMOSTPLAN, ZKMOSTSECTION, ZKMOSTSIDE i ZKMOSTDEVELOP pytają o standard Ogolny / Krawedzie. Ogolny tworzy dokumentację, Krawedzie zachowuje poprzedni widok geometrii. Aby przekształcić istniejące widoki bez ich ponownego wstawiania: Rysunki → Ujednolić istniejące widoki → Zastosuj.

## Co jest generowane

- Usuwanie szwów próbkowania i wspólnych ścian stykających się segmentów.
- Obrys widoczny, grubsza linia cięcia, linie zasłonięte i osie na osobnych warstwach. Domyślnie nie pokazuje się ukrytego wnętrza ustroju, aby nie tworzyć gęstej siatki; dodatkowy przełącznik je przywraca.
- Wypełnienia przekrojów i podpór w szarości, nasypów na zielono, oznaczenia skarp.
- Natywne wymiary CAD: szerokość całkowita, łańcuchy stref, rozstaw belek, długości charakterystyczne. Równomierny układ belek dostaje zapis typu 18×90. Domyślne jednostki wymiarów to cm.
- Rzędne na osi i kapach; przekrój opcjonalnie względny w cm względem niwelety w osi, bok bezwzględny w metrach.
- Strzałki spadków wyliczane z powierzchni drogi; numery / nazwy osi podpór, nazwy kierunków, tytuły i skale.
- Umowne symbole pieszych i rowerów, zależne od nazwy strefy. Nie są elementami modelu ani katalogiem bloków branżowych.
- Jeśli jest wybrany TIN: profil terenu i próbkowany prześwit do spodu ustroju (belek / poprzecznic / płyty). Oznaczenie „min. prób.” jest minimum próbek, nie dowodem normowego prześwitu. Brak terenu nie jest zastępowany wymyśloną rzędną.

BOK to rzut prostopadły — długość opisuje się Lrz. Przy obiekcie w łuku ROZWINIECIE pokazuje długość po osi jako Lc i jest domyślnym bokiem na arkuszu. Funkcja nie wymyśla długości między łożyskami ani rozpiętości konstrukcyjnej, jeśli takich punktów nie ma w modelu.

## Plan na podkładzie

Na arkuszu plan pozostaje w oryginalnych XY WCS, dlatego korzysta z rzeczywistego podkładu / XREF w DWG. Nie kopiuje mapy ani nie przekształca jej układu współrzędnych. Warstwy modelu mostu oraz innych jego widoków są wygaszane tylko w odpowiednich rzutniach. Przełącznik Szary podkład mapowy nadaje warstwom BYLAYER szary kolor tylko w rzutni planu; po wyłączeniu zachowywane są kolory warstw. obiekty ze sztywnym kolorem mogą zachować własny wygląd. W podglądzie WPF podkład nie jest odczytywany.

W przekroju i boku rzutnie pokazują warstwy danego rysunku, bez pozostałego modelu i mapy. Wygenerowane źródła 2D są umieszczane obok modelu, a nie w odległości wielu kilometrów.

## Aktualizacja i własne dopiski

Zastosuj / ZKMOSTBUILD odświeża geometrię, wymiary, rzędne, spadki i rzutnie w tej samej transakcji. Nazwy kierunków i podział stref zapisują się w DWG. Położenie widoku jest odczytywane z jego tytułu — przesuwaj cały widok razem z tytułem. Przesunięcie samego tytułu zostanie potraktowane jako przesunięcie widoku.

Własne obiekty, które nie są oznaczone jako wygenerowane przez program, nie są kasowane. Dopiski na arkuszu pozostają na miejscu. Dopiski w modelu umieszczaj na odpowiedniej warstwie ANNOTATION danego widoku, żeby były widoczne w jego rzutni. Ręczne poprawki wygenerowanych wymiarów i opisów zostaną odtworzone z parametrów przy przebudowie.

Rzutnie zachowują położenie i rozmiar na arkuszu; ich skala oraz centrowanie wynikają z ustawień widoku. Format A1/A2 i urządzenie wydruku są ustawiane podczas tworzenia arkusza, nie przy każdej przebudowie modelu.

## Granice tej wersji

Widoczność obliczana jest na aproksymacji powierzchni modelu; to nie pełny silnik dokumentacji ACIS. Pozostaje sprawdzenie natywnego wymiarowania, wypełnień, rzutni, PDF i konkretnego XREF w BricsCAD. Nie ma automatycznej dokumentacji zbrojeniowej, wymiarowania wszystkich detali, katalogowych sylwetek ani odtwarzania oznaczeń mapy z obrazu. Geometria i wartości mają odpowiadać faktycznemu modelowi.

ZKMOSTTEST rozszerzono o natywne wymiary i wypełnienia rysunku ogólnego; oczekiwane 12/12. Automatyczna próba nie tworzy układu papieru — arkusz i PDF należy przetestować osobno.
