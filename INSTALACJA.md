# ZK Most 0.52 — instalacja i aktualizacje

Uruchom ZKMost-Setup-0.52.exe po zamknięciu BricsCAD. Instalacja dla bieżącego użytkownika, bez praw administratora: %LOCALAPPDATA%/ZKProjekt/Most. Menu Start → ZK Most → ustawienia i aktualizacje. Instalator nie zmienia istniejących skryptów startowych ani ustawień zabezpieczeń CAD.

Wymagania: Windows x64, BricsCAD V26 Pro/BIM/Mechanical i .NET Desktop Runtime 8 x64. Sam instalator nie doinstalowuje środowiska .NET. Pakiet nie jest podpisany certyfikatem wydawcy.

Bundle w %APPDATA%/Bricsys/ApplicationPlugins/ZKMost.bundle wskazuje loader. Po ponownym uruchomieniu CAD powinna pojawić się wstążka ZK Most. Jeżeli automatyczne ładowanie jest wyłączone, wczytaj %LOCALAPPDATA%/ZKProjekt/Most/ZKMost-start.lsp przez APPLOAD i ewentualnie dodaj go do autostartu w CAD. Nie obniżaj ustawień bezpieczeństwa. Mechanizm bundle wymaga sprawdzenia na danym profilu CAD; kompilacja nie zastępuje tej próby.

ZKMOSTSUPPORT otwiera wspólny formularz ZK Support. Program niczego nie wysyła automatycznie; zgłoszenie wysyła użytkownik przyciskiem formularza. ZKMOSTUPDATE otwiera ustawienia i sprawdzanie aktualizacji.

## Aktualizacje

Przy uruchomieniu dodatku w BricsCAD aktualizator sprawdza opublikowane stabilne wydania. Wybiera najwyższy numer instalatora, porównuje go z zainstalowaną wersją i pobiera nowszy plik. Przed instalacją sprawdza rozmiar, SHA-256 z GitHuba i wersję zapisaną w EXE. Zapisz rysunki i zamknij wszystkie instancje BricsCAD w dogodnym momencie. Aktualizacja zainstaluje się automatycznie, a nowa wersja załaduje się przy następnym otwarciu CAD.

W oknie oczekiwania można anulować instalację. W poleceniu **ZKMOSTUPDATE** możesz wyłączyć automatyczną instalację i pozostawić powiadomienia albo wyłączyć sprawdzanie przy starcie. Przycisk **Sprawdź aktualizacje** pozwala ręcznie wybrać instalację po zamknięciu CAD.

## Publikacja kolejnego instalatora

W [GitHub Releases](https://github.com/kidznok/ZK-Mosty/releases) dodaj gotowy plik o nazwie np. **ZKMost-Setup-0.53.exe** do nowego lub istniejącego stabilnego wydania i zapisz je jako opublikowane. Numer w nazwie powinien odpowiadać wersji produktu wewnątrz EXE. Możesz używać stałego tagu i zostawić starsze instalatory. Wystarczy sam EXE.

Wersja 0.51 rozpoznaje wydanie przejściowe **v0.52**. Użytkownik 0.51 wybiera w **ZKMOSTUPDATE** instalację po zamknięciu CAD. Następne aktualizacje obsłuży już nowy mechanizm.

Szczegóły sprawdzenia w BricsCAD V26 zawiera TESTY-CAD.md.
