# ZK Most 0.21 — instalacja i aktualizacje

Uruchom ZKMost-Setup-0.21.exe po zamknięciu BricsCAD. Instalacja dla bieżącego użytkownika, bez praw administratora: %LOCALAPPDATA%/ZKProjekt/Most. Menu Start → ZK Most → ustawienia i aktualizacje. Instalator nie zmienia istniejących skryptów startowych ani ustawień zabezpieczeń CAD.

Wymagania: Windows x64, BricsCAD V26 Pro/BIM/Mechanical i .NET Desktop Runtime 8 x64. Sam instalator nie doinstalowuje środowiska .NET. Pakiet nie jest podpisany certyfikatem wydawcy.

Bundle w %APPDATA%/Bricsys/ApplicationPlugins/ZKMost.bundle wskazuje loader. Po ponownym uruchomieniu CAD powinna pojawić się wstążka ZK Most. Jeżeli automatyczne ładowanie jest wyłączone, wczytaj %LOCALAPPDATA%/ZKProjekt/Most/ZKMost-start.lsp przez APPLOAD i ewentualnie dodaj go do autostartu w CAD. Nie obniżaj ustawień bezpieczeństwa. Mechanizm bundle wymaga sprawdzenia na danym profilu CAD; kompilacja nie zastępuje tej próby.

ZKMOSTSUPPORT otwiera wspólny formularz ZK Support. Program niczego nie wysyła automatycznie; zgłoszenie wysyła użytkownik przyciskiem formularza. ZKMOSTUPDATE otwiera ustawienia i sprawdzanie aktualizacji.

Repozytorium wydań programu: https://github.com/kidznok/ZK-Mosty. Po załadowaniu dodatku do CAD uruchamia się niewidoczny aktualizator. Sprawdza stabilne GitHub Releases maksymalnie raz na 12 godzin. Pobiera nowszy instalator, kontroluje rozmiar i SHA-256 z metadanych GitHub, czeka na zamknięcie wszystkich procesów BricsCAD, następnie instaluje w trybie cichym. Nie zamyka rysunków ani CAD. Przełącznik w ustawieniach wyłącza ten mechanizm. Błędy automatycznego sprawdzania zapisują się w update-last.log, bez przerywania pracy w CAD.

Przy aktualizacji instalator czeka na zakończenie uruchamiającego go procesu aktualizatora. Stare biblioteki pozostają w katalogach wcześniejszych generacji do czasu odinstalowania. Ustawienia i cache aktualizacji pozostają po odinstalowaniu. Odinstalowanie z Windows → Zainstalowane aplikacje → ZK Most usuwa program i jego bundle.

## Publikacja kolejnego instalatora

W repozytorium główna gałąź main ma workflow. Wgraj do katalogu głównego gotowy instalator np. ZKMost-Setup-0.21.exe. Numer w nazwie musi odpowiadać rzeczywistej wersji ProductVersion pliku EXE. Workflow utworzy tag v0.21 i stabilne GitHub Release z instalatorem. Można pozostawić poprzednie pliki. Nie wystarczy zmiana nazwy starszego instalatora.

Obsługiwane nazwy: ZKMost-Setup-0.21.exe i ZKMost-0.21-Setup.exe. Numer instalatora musi odpowiadać tagowi wydania. Użytkownicy z włączonymi aktualizacjami odbiorą nowe wydanie przy kolejnym sprawdzeniu. Sam plik wrzucony do repozytorium nie jest źródłem pobierania dla aplikacji — workflow automatycznie publikuje go w Releases. Jeśli Actions są wyłączone, utwórz Release ręcznie i dołącz EXE.

Szczegóły sprawdzenia w BricsCAD V26 zawiera TESTY-CAD.md.
