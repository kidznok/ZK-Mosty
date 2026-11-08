# Zbrojenie kap chodnikowych

Wpisz **ZKMOST**, wybierz most i w edytorze przejdź do **Zbrojenie kap**. Włącz kapę lewą, prawą albo obie. Strony wynikają z kierunku osi mostu. Dla każdej strony możesz podać osobno otulinę, średnice, rozstawy oraz promień osi gięcia U. Wszystkie pola na karcie są w milimetrach.

Pręty podłużne biegną górą i dołem wewnątrz poprzecznych U. Górne i dolne ramię U łączą się przy zewnętrznej krawędzi kapy. Wolne końce leżą przy jezdni. Układ korzysta z przekrojów betonu generowanych przez model. Zmiana geometrii kapy lub jej parametrów przebudowuje zbrojenie. W trybie ręcznym użyj **Przelicz teraz**. Polecenie **Wyizoluj element** na karcie pokazuje pręty kap.

Na karcie **Generuj rysunki 2D** wybierz **Przekroje zbrojenia kap z zestawieniami** i kliknij **Wstaw zaznaczone rysunki**. Program wstawia jeden przekrój każdej włączonej kapy w miejscu pręta U najbliższego środka mostu. Na rysunku widzisz stronę, kilometraż, beton, oba gięcia U i pręty podłużne. Zestawienie obejmuje wszystkie pręty danej kapy. Ponowne generowanie odświeża rysunek w zapisanym miejscu. **Usuń przekroje i zestawienia kap** usuwa przekroje i zestawienia, zachowując zbrojenie 3D.

Osie prętów są poliliniami 3D. Rozstaw U jest wyrównywany po stacji osi, a podłużnych po dostępnej szerokości między skrajnymi pozycjami. Program aproksymuje łuki gięcia odcinkami o kącie do 5°. Długości i masy dotyczą geometrii tych osi (7850 kg/m³). Kształt jest otwarty od jezdni, bez haków końcowych i zakładów. Parametry, zakotwienia i podział na długości handlowe ustala projektant.

W starszym wariancie beton składa się z prostych segmentów. Tam, gdzie ich przekroje końcowe się rozchodzą, pręty kończą się z otuliną i rozpoczynają w następnym segmencie. Moduł obsługuje kapy bez ręcznych docięć. Obie kapy w starszym DWG mają domyślnie wyłączone zbrojenie.

W przykładzie **K-01-kapy.dwg** model zawiera kapy na łuku, o szerokościach 1,60 i 1,00 m, z różnymi spadkami i rozstawami poprzecznymi. Lewa ma 83 pręty, prawa 55. Wymiary w przykładzie służą do prób działania programu.