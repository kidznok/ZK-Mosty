# ZK-Mosty

Mosty, przepusty i modelowanie przekrojów po osi w BricsCAD V26 x64.

## Pobieranie

Gotowe instalatory są w [Releases](https://github.com/kidznok/ZK-Mosty/releases/latest). Instalacja dla bieżącego użytkownika, bez administratora. Zamknij BricsCAD przed instalacją. Wymagany .NET Desktop Runtime 8 x64. Obecna paczka testowa nie jest podpisana certyfikatem wydawcy.

Po instalacji uruchom BricsCAD. Gdy profil ma wyłączone automatyczne ładowanie bundle, dodaj przez APPLOAD `%LOCALAPPDATA%/ZKProjekt/Most/ZKMost-start.lsp`. Nie zmieniaj ustawień bezpieczeństwa. `ZKMOSTRIBBON` odtwarza wstążkę, `ZKMOSTSUPPORT` otwiera wspólny formularz zgłoszeń, `ZKMOSTUPDATE` otwiera ustawienia aktualizacji.

## Kolejne wersje

Wgraj na gałąź **main** gotowy plik **ZKMost-Setup-0.13.0.exe**, potem kolejny z wyższym numerem. Workflow automatycznie:

1. wybierze najwyższy numer spośród instalatorów w katalogu głównym;
2. porówna nazwę z ProductVersion pliku EXE;
3. utworzy stabilne GitHub Release z odpowiednim tagiem i instalatorem.

Starsze pliki mogą pozostać. Nie zmieniaj samej nazwy starszego instalatora. Nowe EXE muszą rzeczywiście zawierać nową wersję programu. Jeśli GitHub Actions są wyłączone, opublikuj Release ręcznie: np. tag `v0.13.0`, plik `ZKMost-Setup-0.13.0.exe`.

## Aktualizator

Domyślnie sprawdza stabilne Releases w tle po uruchomieniu dodatku (nie częściej niż co 12 godzin). Pobiera nowszy instalator, sprawdza rozmiar i SHA-256 z GitHub, czeka na zamknięcie wszystkich procesów BricsCAD i uruchamia instalację. Nie zamyka rysunków. Przełącznik w ustawieniach wyłącza aktualizacje automatyczne.

## Wersja 0.13.1 — rysunek ogólny

Wygląd w rodzinie ZK AutoDWG, przełączniki, ZK Support; belki proste lub po osi, ręczne punkty oparcia i obrót; przekroje zmienne na stacjach, zapisane cięcia, odłączanie do obróbki CAD, rozmieszczanie bloków; przepusty kołowe, skrzynkowe i owalne z półkami oraz ścianami czołowymi z odniesieniem do TIN w XREF; aktualizowane widoki 2D.

255 testów geometrii/projekcji, 19 kontroli WPF oraz 16 testów aktualizatora (w tym rzeczywiste pobranie opublikowanego EXE i weryfikacja SHA-256, bez uruchamiania instalacji). Kompilacja nie zastępuje prób instalacji, natywnego modelera CAD i XREF na rzeczywistym stanowisku. W CAD polecenie `ZKMOSTTEST` wykonuje próbę bez zapisywania geometrii testowej. To wersja testowa, bez obliczeń konstrukcyjnych i hydraulicznych.

## Rysunek ogólny 0.13.1

Nowe: ZKMOSTPODGLAD i ZKMOSTARKUSZ. Przekrój z wymiarami, rzędnymi i spadkami; bok z osiami podpór, wypełnieniami i kierunkami; plan na rzeczywistym podkładzie WCS; arkusz A1/A2 z niezależnymi skalami rzutni. Ustawienia w ZKMOST → Rysunki. Instrukcja: [RYSUNKI.md](RYSUNKI.md). Układ papieru i wydruk PDF wymagają próby na konkretnym stanowisku BricsCAD.


