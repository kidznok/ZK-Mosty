# ZK Most 0.52

Automatyczne aktualizacje z GitHub Releases. [Pobierz instalator 0.52 dla BricsCAD V26](https://github.com/kidznok/ZK-Mosty/releases/download/v0.52/ZKMost-Setup-0.52.exe).

# ZK Most 0.51

W oknie obiektów podgląd 3D ma stały kadr. Kółkiem myszy lub przyciskami + i − możesz powiększyć detal, a przyciskiem „Całość” wrócić do widoku całego obiektu. [Pobierz instalator 0.51 dla BricsCAD V26](https://github.com/kidznok/ZK-Mosty/releases/download/v0.51/ZKMost-Setup-0.51.exe).

# ZK Most 0.25

W edytorze mostu kliknij **Obliczenia** lub wpisz `ZKMOSTOBLICZENIA`. Moduł importuje długość i stacje podpór. Użytkownik ustala schemat statyczny i sztywność EI. [Instrukcja obliczeń](OBLICZENIA.md).

Karta **Belki** pokazuje dwa schematy. Widocznością elementu steruje przełącznik izolacji, a powiększenie ma osobny przycisk. Wspólny instalator zawiera też zbrojenie płyty i obu kap. [Pobierz instalator 0.25 dla BricsCAD V26](https://github.com/kidznok/ZK-Mosty/releases/download/v0.25/ZKMost-Setup-0.25.exe).

# ZK Most 0.23

W karcie **Przyczółki** ustawisz długość płyty przejściowej przy jej przełączniku, także podczas edycji skrzydła. **Pokaż cały obiekt** przywraca pełną widoczność wybranego modelu i zapisuje ten wybór w DWG. [Instalator dla BricsCAD V26](https://github.com/kidznok/ZK-Mosty/releases/download/v0.23/ZKMost-Setup-0.23.exe) · [Wyniki prób](TESTY-CAD.md).

# ZK Most 0.22

Po wybraniu **Belki → Wyizoluj element** widok pokazuje same belki również po przeliczeniu mostu. **Pokaż cały obiekt** przywraca wcześniejszą widoczność warstw. [Pobierz instalator dla BricsCAD V26](https://github.com/kidznok/ZK-Mosty/releases/download/v0.22/ZKMost-Setup-0.22.exe).

# ZK Most 0.21

[Pobierz wspólny instalator dla BricsCAD V26](https://github.com/kidznok/ZK-Mosty/releases/download/v0.21/ZKMost-Setup-0.21.exe).

Wpisz **ZKMOST**, otwórz most, wybierz **Zbrojenie płyty** i włącz **Modeluj zbrojenie płyty**. Model, rzuty i zestawienie aktualizują się po zmianie parametrów. [Obsługa zbrojenia](ZBROJENIE-PLYTY.md).

W karcie **Przyczółki** wybierz przyczółek i stronę. Przycisk **Wstaw widok boczny przyczółka** generuje rysunek w DWG. Opcja **Synchronizuj strony** łączy parametry skrzydeł i stożków danego przyczółka. [Pozostałe zmiany](ZMIANY-AKTUALNE.md) · [Wyniki prób](TESTY-CAD.md).

# ZK Most 0.20

[Instalator ZKMost-Setup-0.20.exe](https://github.com/kidznok/ZK-Mosty/releases/download/v0.20/ZKMost-Setup-0.20.exe).

Rzędne posadowienia podpór pozostają stałe przy zmianie rzędnej osi. Nawigacja boczna, poprawiony podgląd i zoom listy obiektów, stabilna izolacja warstw, stożki ku przyczółkowi, naprawa eVertexAfterFace, wartości do dwóch miejsc, zakres terenu z polilinii i trzy rzutnie z przekrojem.

Walidacja: 330 testów geometrii, 39 interfejsu, 25 aktualizatora; BricsCAD V26: 18 + 9 testów natywnych. [Szczegóły zmian](ZMIANY-AKTUALNE.md), [próby na projekcie](TESTY-CAD.md). Kontrola WR-M ma zakres częściowy.

# ZK Most 0.19

Aktualny instalator: [ZKMost-Setup-0.19.exe](https://github.com/kidznok/ZK-Mosty/releases/download/v0.19/ZKMost-Setup-0.19.exe).

Wydanie dodaje osobne szerokości i pochylenia kap L/P, pełną listę podpór, nasyp rosnący ku końcowi skrzydła, podgląd przyczółka z geometrii modelu, pojedyncze korpusy przepustu, izolowanie i powiększanie z kart oraz obracający się podgląd listy obiektów. Logo i ikona pochodzą z rodziny ZK.

Karta Sprawdź z WR-M wykonuje częściową kontrolę geometrii; zakres i braki: [WRM-AUDYT.md](WRM-AUDYT.md). Obliczenia konstrukcyjne, geotechniczne i hydrauliczne nie są automatycznie sprawdzane. Testy natywnych operacji w BricsCAD pozostają do wykonania: [TESTY-CAD.md](TESTY-CAD.md).

# ZK-Mosty

Mosty, przepusty i modelowanie przekrojów po osi w BricsCAD V26 x64.

## Pobieranie

Gotowe instalatory są w [Releases](https://github.com/kidznok/ZK-Mosty/releases/latest). Instalacja dla bieżącego użytkownika, bez administratora. Zamknij BricsCAD przed instalacją. Wymagany .NET Desktop Runtime 8 x64. Obecna paczka testowa nie jest podpisana certyfikatem wydawcy.

Po instalacji uruchom BricsCAD. Gdy profil ma wyłączone automatyczne ładowanie bundle, dodaj przez APPLOAD `%LOCALAPPDATA%/ZKProjekt/Most/ZKMost-start.lsp`. Nie zmieniaj ustawień bezpieczeństwa. `ZKMOSTRIBBON` odtwarza wstążkę, `ZKMOSTSUPPORT` otwiera wspólny formularz zgłoszeń, `ZKMOSTUPDATE` otwiera ustawienia aktualizacji.

## Kolejne wersje

W [GitHub Releases](https://github.com/kidznok/ZK-Mosty/releases) dodaj gotowy instalator, np. **ZKMost-Setup-0.53.exe**, jako załącznik do nowego lub istniejącego stabilnego wydania. Opublikuj lub zapisz wydanie. Możesz zachować tag i starsze pliki. Numer w nazwie pliku odpowiada wersji produktu wewnątrz EXE.

## Aktualizator

Od wersji 0.52 przy uruchomieniu dodatku ZK Most wybiera najwyższy numer instalatora spośród stabilnych wydań. Przy ustawieniach domyślnych pobiera nowszy plik, weryfikuje go i instaluje po zamknięciu wszystkich instancji BricsCAD. W **ZKMOSTUPDATE** można osobno wyłączyć instalowanie lub sprawdzanie przy starcie.

## Wersja 0.13.1 — rysunek ogólny

Wygląd w rodzinie ZK AutoDWG, przełączniki, ZK Support; belki proste lub po osi, ręczne punkty oparcia i obrót; przekroje zmienne na stacjach, zapisane cięcia, odłączanie do obróbki CAD, rozmieszczanie bloków; przepusty kołowe, skrzynkowe i owalne z półkami oraz ścianami czołowymi z odniesieniem do TIN w XREF; aktualizowane widoki 2D.

255 testów geometrii/projekcji, 19 kontroli WPF oraz 16 testów aktualizatora (w tym rzeczywiste pobranie opublikowanego EXE i weryfikacja SHA-256, bez uruchamiania instalacji). Kompilacja nie zastępuje prób instalacji, natywnego modelera CAD i XREF na rzeczywistym stanowisku. W CAD polecenie `ZKMOSTTEST` wykonuje próbę bez zapisywania geometrii testowej. To wersja testowa, bez obliczeń konstrukcyjnych i hydraulicznych.

## Rysunek ogólny 0.13.1

Nowe: ZKMOSTPODGLAD i ZKMOSTARKUSZ. Przekrój z wymiarami, rzędnymi i spadkami; bok z osiami podpór, wypełnieniami i kierunkami; plan na rzeczywistym podkładzie WCS; arkusz A1/A2 z niezależnymi skalami rzutni. Ustawienia w ZKMOST → Rysunki. Instrukcja: [RYSUNKI.md](RYSUNKI.md). Układ papieru i wydruk PDF wymagają próby na konkretnym stanowisku BricsCAD.


