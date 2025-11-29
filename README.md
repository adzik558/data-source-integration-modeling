# Projektowanie modeli łączenia źródeł danych (BIOD)

Projekt przedstawia pełny proces budowy modelu regresji liniowej na podstawie
danych ekonomicznych z GUS dotyczących średnich cen wybranych produktów nabiałowych
i tłuszczowych w latach 2010–2021.  
Celem było zbadanie zależności pomiędzy cenami produktów spożywczych a poziomem inflacji
oraz stworzenie modelu pozwalającego na predykcję wskaźnika CPI.

Projekt realizowany w ramach studiów – Inżynieria i Analiza Danych.


## Cele projektu

- integracja danych z wielu źródeł (ceny produktów z GUS + wskaźnik inflacji),
- selekcja istotnych zmiennych poprzez eliminację quasi–stałych,
- budowa modelu regresji liniowej,
- ocena jakości modelu,
- analiza reszt,
- testy statystyczne i diagnostyczne,
- ocena normalności, współliniowości i autokorelacji reszt.

Dokładna dokumentacja znajduje się w pliku PDF w repozytorium.

---

## Dane wejściowe

Zgodnie z dokumentacją projektu :contentReference[oaicite:1]{index=1}, analizie poddano roczne ceny 10 produktów:

- słonina,
- smalec wieprzowy (kostki 250g),
- olej rzepakowy rafinowany,
- masło świeże 82.5%,
- mleko 1.5–2%,
- jajka (sztuki),
- mleko UHT 3–3.5%,
- śmietana 18%,
- ser twarogowy półtłusty,
- ser żółty typu „Gouda”.

Zmienną objaśnianą (Y) był **wskaźnik cen towarów i usług konsumpcyjnych (inflacja)**.

---

## Eliminacja quasi-stałych

Usunięto zmienne o niskiej zmienności (< 10%).  
Z 10 zmiennych pozostało 5 — te o najwyższej zmienności i potencjalnym wpływie na CPI
(zaobserwowane w tabeli na str. 4 PDF).

Pozwoliło to uprościć model i poprawić jakość estymacji.

---

## Analiza korelacji

Macierz korelacji (str. 5 PDF) pokazała wyłącznie **dodatnie zależności** między cenami produktów —  
zgodnie z oczekiwaniem, ponieważ poziom cen rośnie wraz z inflacją.

Zmienne o najwyższej korelacji zostały wybrane do modelu regresyjnego.

---

## Metoda Hellwiga – selekcja zmiennych

Przeanalizowano indywidualne i integralne pojemności informacyjne
(kolumny tabeli na str. 6 PDF).  
Zmienna o największej pojemności informacyjnej była dalej traktowana jako najistotniejsza.

Na tej podstawie do modelu wybrano zestaw X1, X2, X4, X6, X8.

---

## Regresja liniowa

Model regresji został wyestymowany na podstawie zmiennych wybranych metodą Hellwiga.

Wyniki (str. 8 PDF):

- R² ≈ 0.549  
- Standard error ≈ 6.16  
- Test F istotny (model jako całość jest statystycznie istotny)

Dla każdej zmiennej X wygenerowano wykres dopasowania (scatter + linia regresji).

---

## Analiza reszt i diagnostyka modelu

Przeprowadzono wszystkie kluczowe testy:

### Test symetrii  
Reszty dodatnie = reszty ujemne → rozkład *symetryczny* (str. 11 PDF).

### Variance Inflation Factor (VIF)  
Wszystkie VIF < 4 → **brak współliniowości** (str. 12 PDF).

### Test Goldfelda–Quandta  
Brak heteroskedastyczności → wariancja stabilna (str. 12 PDF).

### Test Shapiro–Wilka  
W = wartość obliczona < W krytyczne → odrzucenie H0 (str. 13 PDF).  
Rozkład reszt odbiega od normalnego.

### Test Jarque–Bera  
Wskazuje na normalność reszt (str. 13 PDF).  
(Wyniki się różnią – omówione w dokumentacji).

### Test autokorelacji reszt (Durbin–Watson)  
Wynik w obszarze niekonkluzywnym (str. 14 PDF).  
Model nie rozstrzyga autokorelacji jednoznacznie.

---

## Wnioski z projektu

- Model spełnia większość założeń regresji, oprócz pełnej normalności reszt.  
- Zależności produktów spożywczych od inflacji są **statystycznie potwierdzone**.  
- Zestaw zmiennych X1, X2, X4, X6, X8 okazał się najbardziej informacyjny.  


