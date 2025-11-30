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

<img width="760" height="314" alt="image" src="https://github.com/user-attachments/assets/2f512f96-5d87-49d3-9c2e-9be4baf6027e" />


---

## Analiza korelacji

Macierz korelacji (str. 5 PDF) pokazała wyłącznie **dodatnie zależności** między cenami produktów —  
zgodnie z oczekiwaniem, ponieważ poziom cen rośnie wraz z inflacją.

Zmienne o najwyższej korelacji zostały wybrane do modelu regresyjnego.

<img width="552" height="214" alt="image" src="https://github.com/user-attachments/assets/37fc192c-4b45-4ef2-8aa0-fba76a9dc523" />


---

## Metoda Hellwiga – selekcja zmiennych

Przeanalizowano indywidualne i integralne pojemności informacyjne
(kolumny tabeli na str. 6 PDF).  
Zmienna o największej pojemności informacyjnej była dalej traktowana jako najistotniejsza.

Na tej podstawie do modelu wybrano zestaw X1, X2, X4, X6, X8.

<img width="768" height="656" alt="image" src="https://github.com/user-attachments/assets/0c4de571-0cb2-43cf-9330-9905b27351fc" />


---

## Regresja liniowa

Model regresji został wyestymowany na podstawie zmiennych wybranych metodą Hellwiga.

Wyniki (str. 8 PDF):

- R² ≈ 0.549  
- Standard error ≈ 6.16  
- Test F istotny (model jako całość jest statystycznie istotny)

<img width="717" height="507" alt="image" src="https://github.com/user-attachments/assets/8eda274b-4a27-46b7-aad6-2afc8c79f36c" />


Dla każdej zmiennej X wygenerowano wykres dopasowania (scatter + linia regresji).

<img width="1205" height="410" alt="image" src="https://github.com/user-attachments/assets/0eafc1cf-8ad5-439f-9670-e16839ea60f8" />


---

## Analiza reszt i diagnostyka modelu
<img width="1406" height="594" alt="image" src="https://github.com/user-attachments/assets/d73f7e73-e4dd-4881-a669-166ed0f36ffb" />


Przeprowadzono wszystkie kluczowe testy:

### Test symetrii  
Reszty dodatnie = reszty ujemne → rozkład *symetryczny* (str. 11 PDF).  

<img width="584" height="450" alt="image" src="https://github.com/user-attachments/assets/1ad597d0-c5a3-4316-a125-8ef69f6bda08" />


### Variance Inflation Factor (VIF)  
Wszystkie VIF < 4 → **brak współliniowości** (str. 12 PDF).  

<img width="910" height="370" alt="image" src="https://github.com/user-attachments/assets/309bc979-073b-4c02-8fa3-f7793bb92432" />


### Test Goldfelda–Quandta  
Brak heteroskedastyczności → wariancja stabilna (str. 12 PDF).  

<img width="920" height="267" alt="image" src="https://github.com/user-attachments/assets/b1c820fa-469f-4023-8538-2a0cd0bf25d1" />


### Test Shapiro–Wilka  
W = wartość obliczona < W krytyczne → odrzucenie H0 (str. 13 PDF).  
Rozkład reszt odbiega od normalnego.  

<img width="1404" height="543" alt="image" src="https://github.com/user-attachments/assets/405503ee-5652-4a8c-a11c-9cc155a905c2" />


### Test Jarque–Bera  
Wskazuje na normalność reszt (str. 13 PDF).  

<img width="1414" height="367" alt="image" src="https://github.com/user-attachments/assets/5b276bb1-cb3f-4d83-9807-c0c6480dec32" />


### Test autokorelacji reszt (Durbin–Watson)  
Wynik w obszarze niekonkluzywnym (str. 14 PDF).  
Model nie rozstrzyga autokorelacji jednoznacznie.

<img width="1401" height="622" alt="image" src="https://github.com/user-attachments/assets/a4d7f7ea-caec-41e4-a675-82a524c3f6a6" />



---

## Wnioski z projektu

- Model spełnia większość założeń regresji, oprócz pełnej normalności reszt.  
- Zależności produktów spożywczych od inflacji są **statystycznie potwierdzone**.  
- Zestaw zmiennych X1, X2, X4, X6, X8 okazał się najbardziej informacyjny.  


