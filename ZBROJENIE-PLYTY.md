# Zbrojenie płyty pomostowej · ZK Most 0.21

W BricsCAD V26 wpisz **ZKMOST**, otwórz most i wybierz **Zbrojenie płyty**. Włącz **Modeluj zbrojenie płyty**. Parametry dotyczą wyłącznie edytowanego mostu i zapisują się w DWG po przeliczeniu. Starsze modele otwierają się z wyłączonym zbrojeniem.

Włącz siatkę górną, dolną lub obie. Podaj otulinę, średnice i rozstawy w milimetrach. W każdej siatce pręty podłużne leżą bliżej powierzchni betonu, a poprzeczne podążają za przekrojem płyty. Pręty mają postać polilinii 3D po osiach. **Wyizoluj element** w tej karcie pokazuje zbrojenie.

**Wskaż miejsce rzutu i zestawienia** umieszcza osobny rzut dla każdej włączonej siatki i opis dla każdego kierunku. Wskaż lewy dolny narożnik pierwszego rzutu. Zmiana parametrów aktualizuje geometrię, liczbę sztuk, sumę długości osi i teoretyczną masę stali przy gęstości 7850 kg/m³. Ponowne wskazanie przenosi rzut. **Usuń rzut** usuwa tylko rysunek z zestawieniem. Przy wyłączonym trybie **Na żywo** użyj **Przelicz teraz**.

Program rozmieszcza pręty równomiernie między pozycjami skrajnymi. Rozstaw podłużnych jest mierzony w parametrze szerokości przekroju, a poprzecznych po stacji osi w planie. Na łuku rozstaw mierzony wzdłuż krawędzi zależy od jej promienia. Odległość od boków i czół odmierzana jest w tych samych współrzędnych. Odległość pionowa od góry i spodu uwzględnia największe nachylenie trójkątów płyty, aby zachować zadaną otulinę na spadku. Góra betonu leży pod nawierzchnią.

Pierwsza wersja modeluje zadane siatki ciągłe na płycie bez docięć. Zestawienie opisuje geometrię modelu bez podziału na długości handlowe, zakładów i haków. Średnice i rozstawy dobiera projektant. Dane w przykładzie ZB-01 służą do sprawdzenia działania.

## Budowa ze źródeł

Uruchom skrypt **installer/Build-Installer.ps1** w PowerShell. Projekt korzysta z .NET 8, z bibliotek BricsCAD V26 pl_PL i ze wspólnego projektu ZK.UI.Wpf w folderze Documents/Codex/ZK Support. Instalator wymaga NSIS. Testy modułu uruchamia polecenie **dotnet run --project tests/ZKMost.Tests.csproj -- --rebar**.