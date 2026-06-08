# OPERATIONS MANUAL — Inspekcje termowizyjne farm fotowoltaicznych UAV

### Operator – Diagnosta – Analityk – Konsultant

**Syllabus V5 (wersja ostateczna — gotowa do pisania treści)**
Zgodny z praktyką O&M i normą IEC TS 62446-3:2017

---

## Status dokumentu i co zmieniono względem V4

Niniejsza wersja zamraża strukturę przed rozpoczęciem pisania treści. Względem V4 wprowadzono:

1. **Rozdziały 28–31 (interpretacja) otrzymały jednozdaniowe wyłączenia zakresu** — każdy ma teraz jasno zapisane, czego *nie* opisuje, żeby autorzy nie powielali biblioteki usterek.
2. **Rozdział 30 przemianowany** z „Diagnostyka elektryczna" na „Termografia a inne metody diagnostyczne" — z wyraźnym zastrzeżeniem, że operator UAV tych pomiarów nie wykonuje, tylko interpretuje ich wyniki.
3. **Rozdział 34 (Analiza ΔT)** — doprecyzowano, że wykładnik korekcji *x* nie jest stały (zakres 1–2) i jego dobór wymaga uzasadnienia. Usunięto sugestię jednej „domyślnej" wartości.
4. **Rozdział 13** — dodano podrozdział o pyranometrze, w tym procedurę dla inspekcji bez pyranometru.
5. **Rozdział 24** — wzmocniono rozróżnienie: inspekcja UAV ≠ Detailed Inspection w rozumieniu IEC.
6. **Rozdział 41 (Metrologia i obrona raportu)** — przypisano perspektywę (patrz Ustalenia merytoryczne, pkt 5).
7. **Dodano rozdział 45 „Inspekcja rewidująca i monitoring trendu"** (re-inspekcja rok do roku) — luka zgłoszona przy V3.
8. **Glosariusz** — podniesiono limit z ~400 do ~1000 słów.
9. **Plan pisania** — rozdzielono czasochłonność rozdziałów technicznych (15–20 h) od operacyjnych (~10 h).
10. **Próg soiling ≤10%** oznaczony jako rekomendacja autorów, nie wymóg normy.

---

## Ustalenia merytoryczne (do uwzględnienia przez autorów)

Te decyzje rozstrzygają punkty sporne z poprzednich rewizji. Autor każdego rozdziału jest nimi związany.

**1. Wykładnik korekcji ΔT (rozdz. 34).** IEC 62446-3 podaje wykładnik *x* w zakresie **1–2** zależnie od typu defektu (punktowy → bliżej 2, powierzchniowy → bliżej 1). Wartość **nie jest stała** i jej dobór musi być w raporcie uzasadniony, ponieważ wprost wpływa na klasyfikację CoA i obronność raportu gwarancyjnego. Tabele przykładowe w podręczniku prezentujemy jako **ilustracyjne**, z wyraźnym zastrzeżeniem, a nie jako gotowe współczynniki do bezkrytycznego stosowania.

**2. Screening vs Detailed (rozdz. 24).** Inspekcja UAV jest klasyfikowana jako **screening (inspekcja uproszczona)**. Termin „inspekcja szczegółowa" używany w kontekście dronowym oznacza zagęszczony przelot podejrzanego obszaru — **nie jest** to *Detailed Inspection* w rozumieniu IEC, która wymaga bezwzględnych pomiarów temperatury, kontaktu z modułem i wyższego poziomu certyfikacji. Każde użycie terminu „szczegółowa" w częściach V–VI musi nieść to zastrzeżenie.

**3. Granica zakresu rozdziałów interpretacyjnych (28–31):**
- **Rozdz. 28 (Biblioteka)** — jak usterka *wygląda termicznie* (wzorzec, ΔT, CoA, rekomendacja).
- **Rozdz. 29 (Mechanizmy)** — *dlaczego* usterka powstaje (fizyka/elektryka). NIE opisuje wzorców termicznych — te są w 28.
- **Rozdz. 30 (Inne metody)** — czego termografia *nie zmierzy* i jak to uzupełniają IV, SCADA, testy izolacji. NIE opisuje wzorców termicznych ani mechanizmów degradacji.
- **Rozdz. 31 (Zarządzanie degradacją)** — *decyzja O&M*: tolerować / naprawić / wymienić. NIE opisuje mechanizmów (te są w 7 i 29).

**4. EL i pomiary I-V — poza zakresem.** Elektroluminescencja i pełne krzywe I-V są świadomie wyłączone z podręcznika (inny sprzęt, inny zakres certyfikacji). Wyłączenie deklarujemy wprost w rozdz. 0 i ponownie w 37. W rozdz. 30 omawiamy je tylko jako *metody odniesienia*, nie jako procedury do wykonania przez operatora UAV.

**5. Perspektywa rozdz. 41 (obrona raportu).** Perspektywa podstawowa: **inspektor broniący własnego raportu** — co udokumentować, żeby raport był obronny metrologicznie i prawnie. Perspektywa wtórna (osobny podrozdział): jak inspektor wspiera klienta w roszczeniu gwarancyjnym do producenta modułów. Dwie narracje, ale rozdzielone, nie zmieszane.

**6. Soiling ≤10%.** IEC mówi o „czystych modułach" bez progu liczbowego. Próg ≤10% w naszej tabeli GO/NO GO to **rekomendacja operacyjna autorów**, oznaczona jako taka, nie wymóg normy.

**7. Pyranometr.** Wymagany przez IEC do dokumentacji irradiancji. Rozdz. 13 musi zawierać: gdzie ustawiać, jak często odczytywać, oraz **co zrobić, gdy pyranometru nie ma** (typowe przy małych farmach) — jakie źródła zastępcze i jakie ograniczenia raportu to powoduje.

---

# STRUKTURA ROZDZIAŁÓW

Legenda: **✔** = obowiązkowy dla operatora terenu · **–** = pogłębiony, dla analityka/konsultanta · długość orientacyjna w słowach.

## Wprowadzenie

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 0 | **Wprowadzenie** | Zakres, cele, grupa docelowa, jak korzystać z podręcznika, wyłączenia (EL, I-V, analityka SCADA), wymagania wstępne czytelnika — dla wszystkich. | ✔ | ~1000 | Ustawia oczekiwania; deklaruje wyłączenia. |

## CZĘŚĆ I — Fundamenty fizyczne i diagnostyczne

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 1 | **Rola termografii w diagnostyce PV** | Cel i wartość termografii, miejsce w procesie diagnostycznym — dla operatora/klienta. | ✔ | ~800 | Blok „dlaczego to ważne". |
| 2 | **Budowa systemu PV (od ogniwa do sieci)** | Elementy od ogniwa przez falownik po transformator — podstawy dla inspektora bez tła elektrycznego. | ✔ | ~1200 | Diagram przepływu prądu/energii. |
| 3 | **Fizyka termografii dla PV** | Emisyjność szkła, kąt padania, inercja cieplna, prawo Kirchhoffa, temperatura odbita — dla diagnosty. | – | ~1200 | Rozdział techniczny (czasochłonny). |
| 4 | **Geometria i jakość pomiaru** | IFOV, GSD termiczne, wymóg 5×5 px/ogniwo, kąt obserwacji, motion blur, prędkość lotu a jakość. | ✔ | ~1000 | Kompromis 3 vs 5 cm/px z uzasadnieniem. |
| 5 | **Rozdzielczość i detekcja termiczna** | NETD, minimalna wykrywalna anomalia, wpływ wysokości lotu, weryfikacja rozdzielczości w terenie. | – | ~800 | Tabela NETD. |

## CZĘŚĆ II — Moduły i mechanizmy uszkodzeń

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 6 | **Jak powstają anomalie termiczne** | Straty rezystancyjne, efekt Joule'a, nierównomierność prądu, powstawanie hotspotów. | ✔ | ~1000 | Podstawa do biblioteki usterek. Rozdział techniczny. |
| 7 | **Mechanizmy degradacji modułów PV** | PID, LID, LeTID, mikropęknięcia, snail trails, delaminacja, korozja — fizyka procesów. | – | ~1200 | Rozdział techniczny. |
| 8 | **Uszkodzenia eksploatacyjne** | Transport, montaż, obciążenia mechaniczne, grad, śnieg, błędy serwisowe. | – | ~1000 | Ilustracje uszkodzeń. |
| 9 | **Technologie modułów PV** | Mono/poli, TOPCon, HJT, bifacjalne, glass-glass, thin film, CIS, CdTe — różnice termiczne. | ✔ | ~1000 | Sygnalizować odmienną specyfikę PID/LeTID TOPCon i HJT. |

## CZĘŚĆ III — Przygotowanie inspekcji

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 10 | **Rozmowa z klientem i dokumentacja** | Cele, zakres odpowiedzialności, layout, string map, schemat jednokreskowy, historia awarii, dane SCADA. | ✔ | ~800 | Checklisty pytań. |
| 11 | **Planowanie inspekcji** | Szerokość/długość geograficzna, wysokość słońca, azymut i nachylenie modułów, dobór terminu i zasobów. | ✔ | ~800 | Kalendarz inspekcji. |
| 12 | **Okno termiczne** | Stabilność warunków, cloud edging, pamięć i bezwładność cieplna, czas stabilizacji po chmurze. | ✔ | ~600 | Progi czasowe. |
| 13 | **Warunki środowiskowe pomiaru** | GO/NO GO: irradiancja, wiatr (Beaufort), zachmurzenie (okta), steady state, soiling, zacienienie. **+ podrozdział: pyranometr (użycie, odczyt, brak pyranometru).** | ✔ | ~1400 | Tabela GO/NO GO. Soiling ≤10% = rekomendacja autorów. |
| 14 | **Organizacja dnia inspekcji** | Procedury wejścia, BHP, komunikacja z obsługą farmy: kto wyłącza, kto potwierdza warunki, kto daje dostęp. | ✔ | ~800 | Schemat procedury i ról. |
| 15 | **String map w praktyce** | Weryfikacja i uzupełnianie mapy, postępowanie przy braku/błędzie mapy (typowe ~40% inspekcji). | – | ~800 | Przykłady błędnej dokumentacji. |

## CZĘŚĆ IV — Sprzęt inspekcyjny

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 16 | **Platformy UAV** | Mavic 3T, M30T, M3T, M300/350/400 RTK; dobór platformy do wielkości farmy, redundancja. | ✔ | ~800 | Tabela porównawcza. |
| 17 | **Kamery termowizyjne i foto** | Wymagania IEC (8–14 µm, NETD, kalibracja co 2 lata, sync czasu), radiometria, R-JPEG, obowiązek zdjęcia RGB anomalii. | ✔ | ~1000 | Tabela wymagań IEC. |
| 18 | **Kalibracja polowa** | Emisyjność (w tym bifacjale/glass-glass), Trefl / temperatura odbita, weryfikacja ustawień, powtarzalność. | ✔ | ~800 | Formularz kalibracji. |
| 19 | **FFC i stabilność radiometryczna** | Zasada FFC, FFC mid-mission, dryft termiczny sensora, wpływ na misje automatyczne i ortomozaiki. | ✔ | ~800 | Przykłady efektu FFC na ortofotomapie. |
| 20 | **Bezpieczeństwo operacyjne** | EMI od falowników, zakłócenia GNSS/RTK/kompasu/RC, **minimalne odległości** od linii SN/WN i transformatorów, procedury awaryjne. | ✔ | ~800 | Tabela odległości/zakłóceń (liczby, nie ogólniki). |

## CZĘŚĆ V — Pozyskiwanie danych

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 21 | **Projektowanie misji** | Wysokość, GSD, overlap, prędkość, kierunek lotu, pozycja względem słońca, kąt kamery. | ✔ | ~800 | Przykładowe mapy tras. |
| 22 | **Farmy z trackerami** | Ruchoma geometria w czasie misji, synchronizacja kąta gimbala z nachyleniem modułu, niemożność lotu przy niskim słońcu. | – | ~700 | Zalecenia dopasowania gimbala. |
| 23 | **Checklisty operacyjne** | Pre-flight / in-flight / post-flight, backup danych, metadane. | ✔ | ~800 | Gotowe wzory checklist. |
| 24 | **Screening vs inspekcja szczegółowa** | Workflow dwustopniowy i **hybrydowy jednodniowy**. Wyraźne zastrzeżenie: UAV = screening; „szczegółowa" ≠ *Detailed* wg IEC. | ✔ | ~900 | Schemat hybrydowy + ramka ostrzegawcza IEC. |
| 25 | **Kontrola jakości danych** | Ostrość, ekspozycja, pokrycie, geotagi, RTK, radiometria, kompletność projektu. | ✔ | ~600 | Proces QC. |
| 26 | **Ortofotomapy termiczne** | Kiedy mają sens, kiedy nie; workflow; FFC mid-mission; maskowanie refleksów; ograniczenia dokładności. | – | ~800 | Diagram workflow. |

## CZĘŚĆ VI — Interpretacja termogramów

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 27 | **Fałszywe anomalie i błędy interpretacyjne** | Refleksy nieba/chmur/słońca/drona/operatora/konstrukcji, wilgoć, moduły po myciu, cienie, przejściowe zachmurzenie. | ✔ | ~900 | Galerie termogram vs RGB. |
| 28 | **Biblioteka usterek PV** | Dla każdej: RGB, termogram, mechanizm, ΔT, klasyfikacja IEC/CoA, wpływ na produkcję, ryzyko, zalecenie. Karty 28.1–28.25 (poniżej). | – | ~2500 | Jednolita struktura kart. **Zakres: jak wygląda termicznie.** |
| 29 | **Mechanizmy i symptomy usterek** | *Dlaczego* usterka powstaje — detale elektryczne i materiałowe. **NIE opisuje wzorców termicznych (te w rozdz. 28).** | – | ~1000 | Odwołania do norm. |
| 30 | **Termografia a inne metody diagnostyczne** | Czego termografia nie zmierzy; rola IV-curve, SCADA, testów izolacji, EL. **Operator UAV tych pomiarów nie wykonuje — interpretuje wyniki.** NIE opisuje wzorców ani mechanizmów. | – | ~800 | Tabela porównania metod. |
| 31 | **Zarządzanie degradacją modułów** | Decyzja O&M: tolerować / naprawić / wymienić; KPI degradacji w cyklu życia farmy. **NIE opisuje mechanizmów (rozdz. 7, 29).** | – | ~800 | Przykładowe KPI. |

**Biblioteka usterek (rozdz. 28) — karty:**
28.1 Open Circuit Module · 28.2 Short Circuit Module · 28.3 Open Circuit Substring · 28.4 Short Circuit Substring · 28.5 Single Hot Cell · 28.6 Multi Cell Hotspot · 28.7 Transfer Resistance · 28.8 Heated Junction Box · 28.9 Bypass Diode Failure · 28.10 MC4 Overheating · 28.11 String Failure · 28.12 PID · 28.13 LID · 28.14 LeTID · 28.15 Ribbon Failure · 28.16 Delamination · 28.17 Corrosion · 28.18 Soiling · 28.19 Shading · 28.20 Broken Glass · 28.21 Arc Fault · 28.22 Ground Fault · 28.23 Water Ingress · 28.24 Bifacial Anomalies · 28.25 Tracker-Related Anomalies

## CZĘŚĆ VII — Metodyka IEC 62446-3

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 32 | **Norma IEC 62446-3 w praktyce** | Zakres normy, jakie wymagania musi spełnić inspekcja UAV. | ✔ | ~800 | Lista obowiązków. |
| 33 | **Klasyfikacja anomalii (CoA)** | Klasy CoA1–CoA3, przypisane działania, poziom modułu/stringu/systemu. | ✔ | ~600 | Tabela CoA. |
| 34 | **Analiza ΔT według IEC** | ΔT moduł–moduł vs ΔT wewnątrz modułu; anomalie punktowe vs powierzchniowe; normalizacja do 1000 W/m²; **wykładnik x ∈ [1,2] — nie stały, wymaga uzasadnienia**; wpływ wiatru i temp. otoczenia. | ✔ | ~1200 | Tabela normalizacji jako ilustracja z zastrzeżeniem. Rozdział techniczny. |
| 35 | **Kwalifikacje personelu** | ITC L1–3 / ISO 9712; kto może podpisać raport; relacja certyfikat ↔ uprawnienie do raportu. | ✔ | ~600 | Tabela certyfikatów. |
| 36 | **Raportowanie zgodne z IEC** | Wymagana dokumentacja warunków, Trefl, emisyjność, lokalizacja usterek, zdjęcia, certyfikaty. | ✔ | ~800 | Przykłady stron raportu. |
| 37 | **Ograniczenia normy i praktyka terenowa** | Co poza normą (EL, odbiór jakościowy), uwagi polowe; ponowna deklaracja wyłączeń. | ✔ | ~600 | Podsumowanie doświadczeń. |

## CZĘŚĆ VIII — Analiza danych

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 38 | **Workflow diagnostyczny** | Od danych surowych do usterki: kontrola → ocena warunków → wyszukiwanie → grupowanie → ocena produkcji → CoA → priorytety. | ✔ | ~800 | Diagram (mermaid). |
| 39 | **Oprogramowanie** | DJI TAT, PIX4Dinspect, DroneDeploy, Raptor Maps, Sitemark, DataSee — zalety/wady. | – | ~600 | Lista narzędzi. |
| 40 | **AI w inspekcjach PV** | Automatyczna detekcja, walidacja, **konkretne typy anomalii regularnie mylonych przez algorytmy** (np. refleks chmury = hotspot). | – | ~700 | Przykłady pułapek AI. |
| 41 | **Metrologia i obrona raportu** | Perspektywa podstawowa: **obrona własnego raportu** (niepewność, wzorcowanie, dowody). Podrozdział wtórny: wsparcie roszczenia gwarancyjnego klienta. | ✔ | ~900 | Checklist metrologiczny. |

## CZĘŚĆ IX — Raportowanie

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 42 | **Profesjonalny raport termowizyjny** | Metodyka, warunki, wyniki, klasyfikacja, zalecenia; struktura i styl. | ✔ | ~800 | Wzór raportu. |
| 43 | **Wnioski i rekomendacje** | Język raportów, sformułowania defensywne, stopień pilności, kategoryzacja prac, rekomendacje dalszych badań. | – | ~800 | Przykładowe zalecenia. |

## CZĘŚĆ X — Praktyka zawodowa

| Nr | Tytuł | Rola i odbiorca | Obow. | Dł. | Uwagi |
|----|-------|-----------------|:-----:|----:|-------|
| 44 | **Współpraca z O&M** | Koordynacja harmonogramu i działań naprawczych z zespołem O&M. | ✔ | ~600 | Wskazówki praktyczne. |
| 45 | **Inspekcja rewidująca i monitoring trendu** | Re-inspekcja rok do roku: porównanie termogramów, dokumentacja postępu degradacji, spójność warunków między wizytami. | – | ~700 | **Nowy rozdział.** KPI trendu. |
| 46 | **Współpraca z Asset Managerem** | Wykorzystanie wyników do monitoringu portfela. | – | ~600 | Modelowa prezentacja danych. |
| 47 | **EPC, inwestorzy, ubezpieczyciele** | Raport jako narzędzie przy gwarancji i reklamacji. | – | ~600 | Scenariusze roszczeń. |
| 48 | **Odpowiedzialność techniczna i prawna** | Uprawnienia inspektora, odpowiedzialność za błąd/awarię, standardy branżowe. | – | ~800 | Standardy i przykłady. |
| 49 | **Studium przypadków** | ~50 rzeczywistych inspekcji (anonimizowanych): obraz, diagnoza, lekcja; błędy operatorów, fałszywe anomalie, realne awarie, błędne diagnozy, wzorcowe raporty. | – | ~2500 | Decyzja redakcyjna: 50 przypadków, anonimizacja, źródła własne/licencjonowane. |
| 50 | **Glosariusz terminów i skrótów** | IFOV, MFOV, GSD, NETD, FFC, PID, LID, LeTID, CoA, MPPT, MC4, Trefl, ReflAppTemp, EVA, EL, okta, Bft i in. | ✔ | ~1000 | Uzupełniany na bieżąco. |

---

# WYTYCZNE REDAKCYJNE

**Struktura każdego rozdziału:**
1. Blok „**Dlaczego to ważne w praktyce**" (1–2 zdania, kontekst terenowy).
2. Treść w podrozdziałach, dla procedur — w krokach (1, 2, 3…).
3. Tabela/checklista/diagram, gdy pasuje.
4. Podsumowanie lub checklista końcowa.

**Ton i język:** Bezpośredni, rzeczowy, do praktyka. Tryb rozkazujący w procedurach („Sprawdź warunki", „Włącz kamerę"). Unikać strony biernej i akademizmu. Zwroty „inspektor powinien" / „należy".

**Długość:** Operacyjne (planowanie, sprzęt, GO/NO GO) ~600–800 sł. Techniczne (fizyka, ΔT, biblioteka) 1000–2500 sł. Limity orientacyjne.

**Obowiązkowe tabele/grafiki:** GO/NO GO; normalizacja ΔT (ilustracyjna, z zastrzeżeniem o *x*); wymagania kamer IEC; certyfikaty (rozdz. 35); odległości bezpieczeństwa (rozdz. 20); zestawienia termogram↔RGB (rozdz. 27–28); diagram przepływu energii (rozdz. 2); workflow diagnostyczny (rozdz. 38).

**Ilustracje:** Realne instalacje lub własne zdjęcia/symulacje — wymagana licencja lub materiał własny. Każda anomalia w bibliotece: para RGB + termogram tego samego obszaru.

---

# PLAN PISANIA — najpierw rozdziały 0–9

Kolejność: 0 → 1 → 2 → 4 → 13 → 24 → 6 → 3 → 9 → 7.
(Najpierw ramy i fundamenty operacyjne potrzebne do reszty, potem rozdziały ciężkie merytorycznie.)

**Czasochłonność — rozdzielona wg typu:**

| Typ rozdziału | Przykłady | Research | Pisanie | Korekta | Łącznie |
|---------------|-----------|---------:|--------:|--------:|--------:|
| Operacyjny / proceduralny | 11, 13, 14, 21, 23, 24 | 2–3 h | 3–4 h | 2 h | **~8–10 h** |
| Techniczny / obliczeniowy | 3, 4, 6, 7, 34 | 5–7 h | 6–8 h | 3 h | **~15–20 h** |
| Biblioteka / case studies | 28, 49 | — | — | — | osobny harmonogram (najdłuższe) |

**Profil autora — zastrzeżenie:** do rozdziałów metrologicznych i raportowych (13, 18, 19, 34, 36, 41) autor musi mieć doświadczenie w **dokumentowaniu** inspekcji zgodnych z IEC, nie tylko w ich **wykonywaniu**. Sam staż operatorski nie wystarcza.

**Pętla review:** każdy rozdział po szkicu → peer review → jeśli odrzucony, wraca do autora z uwagami (pętla zwrotna); jeśli zaakceptowany → iteracja i finalizacja.

---

# ANEKS — Źródła

## Inspekcja i diagnostyka PV (podstawa metodyczna)
- **IEC TS 62446-3:2017** — Outdoor infrared thermography (dokument kluczowy). Status: Technical Specification, nie pełna norma — zaznaczyć w rozdz. 32. **ED2 w opracowaniu.**
- **IEC 61724-1 / IEC TS 61724-3** — monitoring wydajności i ocena produkcji energii.
- **IEC 60891** — korekcja charakterystyk I-V do warunków referencyjnych (kontekst normalizacji ΔT).
- **ISO 9712** — kwalifikacja personelu badań nieniszczących (rozdz. 35).
- **Dokumenty WMO (No. 306, No. 8, No. 407)** — okta i klasyfikacja chmur dla decyzji GO/NO GO.
- **ISO 15469** — przywoływana przez IEC 62446-3; dotyczy rozkładu luminancji nieba (CIE General Sky), **nie** skali okta — zachować tylko jako cytowanie śledzalne (patrz przypis w rozdz. 0).
- **ISO 9060 / ISO 9847** — klasy i wzorcowanie pyranometrów (rozdz. 13, 17, 18).

## Przepisy lotnicze i procedury operacyjne BSP (warstwa prawna)
- **Rozporządzenie wykonawcze (UE) 2019/947** oraz **delegowane (UE) 2019/945** — operacje BSP w UE; kategoria szczególna, oznakowanie klas C. Cytować tekst skonsolidowany + AMC/GM (**SORA 2.5**, ED Decision 2025/018/R, 2025).
- **Prawo lotnicze** (ustawa z 3 lipca 2002) + rozporządzenia ULC — wymagania krajowe; cytować aktualny tekst jednolity.
- **ISO 21384-3:2023** — procedury operacyjne BSP (zastępuje wycofane wyd. 2019).

> Uwaga zakresowa: dokument operacyjny do ULC (ConOps + SORA) to osobne opracowanie; podręcznik nie jest instrukcją operacyjną w rozumieniu przepisów lotniczych.

## BHP i ochrona danych
- **ISO 45001** — zarządzanie BHP (zastępuje wycofaną PN-N-18001; krajowo PN-ISO 45001).
- **RODO — (UE) 2016/679** — przetwarzanie danych przy rejestracji wizerunków/numerów seryjnych.

## Metody odniesienia (poza zakresem — tylko jako kontekst)
- **IEC TS 62446-4** — Outdoor electroluminescence imaging. **W opracowaniu (projekt, stan 2025).** Dotyczy EL, nie UAS. EL świadomie wyłączona — wyłącznie jako metoda odniesienia w rozdz. 30.

## Metrologia kamery termowizyjnej (opcjonalnie)
- **VDI/VDE 5585** (Blatt 1: charakterystyka metrologiczna; Blatt 2: wzorcowanie) — pomiar temperatury kamerami IR; przydatne w rozdz. 18, 19, 34, 41. To norma metrologii kamer, **nie** inspekcji PV.

## Źródła branżowe i OEM (nieformalne)
- O&M best practices: IEA PVPS, SolarPower Europe.
- Materiały OEM dronów (DJI, Wingtra) i karty kamer — tabele porównawcze sprzętu.
- Materiały branżowe (Raptor Maps, Sitemark) — kompromisy dronowe i pułapki AI.

> Do weryfikacji przed publikacją: aktualne wydania/lata norm względem katalogów IEC/ISO/WMO; status ED2 IEC TS 62446-3 - IEC 62446-3 ma status TS (Technical Specification), nie pełnej normy — warto to zaznaczyć w rozdz. 32.; status projektu IEC TS 62446-4; ewentualna nowa rewizja ISO 21384-3; aktualna wersja pakietu SORA. Klucze cytowań w aneksie muszą odpowiadać kluczom w `bibliografia.bib`.
