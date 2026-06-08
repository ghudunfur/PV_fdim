# Rozdział 0. Wprowadzenie

## 0.1 Cel podręcznika

Rozwój energetyki fotowoltaicznej wymusił zmianę sposobu, w jaki ocenia się stan techniczny instalacji. Farma licząca dziesiątki czy setki tysięcy modułów nie daje się skontrolować ręcznie w rozsądnym czasie — klasyczna inspekcja wizualna jest zbyt wolna i zbyt kosztowna, a do tego nie wykrywa większości uszkodzeń elektrycznych, które nie zostawiają śladu widocznego gołym okiem.

Termografia lotnicza z bezzałogowych statków powietrznych (dalej: BSP) odpowiada na ten problem. Pozwala przebadać całą farmę w jednej sesji i wskazać moduły, stringi oraz połączenia, których temperatura odbiega od otoczenia — a więc te, w których najprawdopodobniej zachodzi nieprawidłowe zjawisko elektryczne lub mechaniczne. W praktyce O&M jest to dziś jedna z najczęściej stosowanych metod przesiewowych w eksploatacji elektrowni PV.

Podręcznik przedstawia kompletną metodykę takiej inspekcji — od przygotowania misji, przez pozyskanie danych, po interpretację wyników i raport techniczny. Adresujemy go do praktyków: operatorów BSP, inspektorów i inżynierów O&M, diagnostów oraz osób odpowiedzialnych za ocenę stanu technicznego farm fotowoltaicznych.

## 0.2 Miejsce termografii w diagnostyce farm fotowoltaicznych

Trzeba to powiedzieć na wstępie, bo jest źródłem najczęstszych nieporozumień z klientem: **termografia nie mierzy sprawności modułu.** Wykrywa anomalie cieplne — różnice temperatury, które *mogą* wskazywać na uszkodzenie, wadę produkcyjną, błąd montażowy albo degradację. Sama anomalia nie jest jeszcze diagnozą; jest sygnałem, że dane miejsce wymaga uwagi.

Termografia jest więc jednym z elementów szerszego procesu diagnostycznego, na który składają się także:

- inspekcja wizualna (w tym przelot RGB dronem),
- pomiary elektryczne i charakterystyki I-V,
- analiza danych z systemów monitoringu (SCADA),
- testy elektroluminescencyjne (EL),
- ocena wydajności instalacji.

Termografia jest w tym zestawie metodą **przesiewową** — szybką i tanią w przeliczeniu na moduł, ale orientacyjną. Jej rolą jest zawęzić obszar, który warto zbadać dokładniej innymi metodami, a nie zastąpić te metody.

## 0.3 Zakres podręcznika i świadome wyłączenia

Podręcznik obejmuje inspekcję termowizyjną modułów fotowoltaicznych wykonywaną z BSP. Omawiamy:

- podstawy fizyki promieniowania podczerwonego,
- zjawiska cieplne w modułach PV i mechanizmy powstawania anomalii,
- wymagania normatywne i ich przełożenie na praktykę dronową,
- wyposażenie pomiarowe i jego kalibrację,
- planowanie i wykonanie misji UAV,
- kontrolę jakości i interpretację danych termicznych,
- klasyfikację uszkodzeń według IEC 62446-3,
- raportowanie wyników oraz źródła błędów i niepewności pomiarowej.

Procedury opisujemy przede wszystkim dla wielkoskalowych instalacji naziemnych (utility-scale), ale większość zasad przenosi się na instalacje komercyjne i dachowe.

**Czego podręcznik nie obejmuje.** Świadomie pozostawiamy poza zakresem trzy metody, które bywają mylone z termografią dronową lub łączone z nią w jednym zleceniu:

- **elektroluminescencję (EL)** — wymaga innego sprzętu, zwykle zaciemnienia lub pracy nocnej i kontaktu z modułem;
- **pełne pomiary charakterystyk I-V** — to pomiar kontaktowy, wykonywany na poziomie stringu przez serwis elektryczny;
- **analitykę SCADA** — to domena monitoringu i Asset Managementu, nie inspekcji terenowej.

Te metody pojawiają się w podręczniku wyłącznie jako **metody odniesienia** — pokazujemy, gdzie termografia się kończy i co ją uzupełnia (rozdz. 30), oraz wracamy do tego wyłączenia przy omawianiu granic normy (rozdz. 37). Nie podajemy procedur ich wykonania.

## 0.4 Standaryzacja inspekcji i podstawa normatywna

Skuteczność inspekcji termowizyjnej zależy nie tylko od jakości kamery, lecz w równym stopniu od warunków środowiskowych, parametrów lotu, geometrii obserwacji, sposobu przetwarzania danych oraz doświadczenia osoby interpretującej wyniki. Inspekcja wykonana niepoprawnie potrafi zaszkodzić w dwie strony naraz: przeoczyć rzeczywiste uszkodzenie i jednocześnie zgłosić anomalię, która nie ma żadnego znaczenia eksploatacyjnego. Dlatego inspekcję prowadzimy według uznanych procedur, a nie według wyczucia operatora.

Podstawą metodyczną podręcznika są:

- **IEC TS 62446-3:2017** [@iec62446-3] — wymagania dla termografii w podczerwieni instalacji PV. To dokument kluczowy dla tej książki. Ma status *Technical Specification* (TS), a nie pełnej normy IEC — różnica ta i jej praktyczne skutki są omówione w rozdz. 32.
- **IEC 61724-1** [@iec61724-1] — monitoring wydajności systemów PV.
- **IEC TS 61724-3** [@iec61724-3] — ocena produkcji energii i wydajności instalacji.
- **wytyczne IECRE** [@iecre] (IEC System for Certification to Standards Relating to Equipment for Use in Renewable Energy Applications) — schemat certyfikacji i raportowania w energetyce odnawialnej.
- **dokumenty WMO** — podstawa oceny warunków atmosferycznych istotnych dla decyzji GO/NO GO. Skalę okta zachmurzenia definiują WMO-No. 306 (Code Table 2700) [@wmo306] oraz WMO-No. 8 [@wmo8], a klasyfikację typów chmur — rozróżnienie cumulus/cirrus, którym posługuje się IEC 62446-3 — WMO-No. 407 (Międzynarodowy atlas chmur) [@wmo407].^[IEC TS 62446-3:2017 w definicji zachmurzenia (pkt 3.5 i nota do Tab. 3) odsyła do ISO 15469:2004 [@iso15469]. Norma ta dotyczy jednak rozkładu luminancji nieba (*CIE Standard General Sky*), a nie skali okta. Właściwą podstawą definicyjną są dokumenty WMO; odniesienie do ISO 15469 zachowujemy wyłącznie jako cytowanie używane przez samą normę IEC, dla śledzalności względem dokumentu nadrzędnego.]
- wymagania kontraktowe operatorów farm i inwestorów, które w praktyce bywają ostrzejsze niż norma.

Powyższe dokumenty opisują, **jak** wykonać wiarygodną inspekcję, i mają charakter
wytycznych technicznych — nie są prawem powszechnie obowiązującym, ale bez ich spełnienia
inspekcja nie zostanie uznana za zgodną z dobrą praktyką inżynierską. Odrębną warstwą,
**prawnie wiążącą**, są przepisy regulujące samą operację lotniczą oraz ochronę osób i danych:

* **Rozporządzenie wykonawcze (UE) 2019/947 [@ue2019-947]** i **delegowane (UE) 2019/945
  [@ue2019-945]**, a w zakresie krajowym **Prawo lotnicze [@pllotnicze2002]** — określają
  warunki wykonywania operacji BSP, wymagania wobec operatora i pilota oraz oznakowanie
  sprzętu. Ich stronę operacyjną (minimalne odległości, zakłócenia, procedury awaryjne)
  rozwijamy w rozdz. 20. Dokument operacyjny składany do organu nadzoru lotniczego
  (koncepcja operacji wraz z oceną ryzyka SORA) jest osobnym opracowaniem — **ten podręcznik
  go nie zastępuje** i nie jest instrukcją operacyjną w rozumieniu przepisów lotniczych.
* **ISO 21384-3:2023 [@iso21384-3]** — struktura i treść procedur operacyjnych dla
  bezzałogowych systemów powietrznych.
* **ISO 45001 [@iso45001]** — zarządzanie bezpieczeństwem i higieną pracy; istotne ze względu
  na zagrożenia elektryczne w pobliżu pracujących falowników i infrastruktury SN/WN.
* **RODO — rozporządzenie (UE) 2016/679 [@ue2016-679]** — przetwarzanie danych osobowych,
  jeśli rejestrowany materiał obejmuje wizerunki osób, numery seryjne modułów lub inne dane
  umożliwiające identyfikację.

Normy inspekcyjne PV traktujemy więc jako wytyczne techniczne, a przepisy lotnicze i ochrony
danych — jako wymagania bezwzględnie obowiązujące. Rozróżnienie to wraca przy omawianiu
odpowiedzialności inspektora (rozdz. 48).

## 0.5 Jak korzystać z podręcznika

Podręcznik obsługuje trzy role, które często łączy jedna osoba, ale które wymagają różnej wiedzy:

- **Operator w terenie** — planuje i wykonuje lot, ocenia warunki GO/NO GO, dba o jakość danych. Rozdziały kluczowe dla tej roli oznaczono w spisie treści symbolem **✔**; zawierają konkretne progi, procedury i checklisty.
- **Diagnosta / analityk przy komputerze** — interpretuje termogramy, odróżnia artefakty od rzeczywistych usterek, klasyfikuje anomalie. Dla tej roli najważniejsza jest część VI (interpretacja) i VII (metodyka IEC).
- **Konsultant przy raporcie** — formułuje wnioski, broni raportu przed klientem, doradza w kwestiach gwarancyjnych i prawnych. Tę rolę obsługują części IX i X.

Każdy rozdział zaczyna się krótkim blokiem „Dlaczego to ważne w praktyce", żeby czytelnik wiedział, po co go czyta, zanim zacznie. Rozdziały oznaczone **✔** to minimum dla personelu terenowego; rozdziały bez tego oznaczenia są pogłębione i adresowane do diagnostów oraz konsultantów.

## 0.6 Wymagania wstępne

Podręcznik nie jest kursem pilotażu ani podstaw elektrotechniki. Zakładamy, że czytelnik:

- posiada uprawnienia do wykonywania operacji BSP wymagane w jego jurysdykcji i zna zasady bezpiecznego latania,
- rozumie podstawy budowy obwodu elektrycznego (napięcie, prąd, rezystancja, połączenia szeregowe i równoległe),
- zna elementarną obsługę posiadanego sprzętu dronowego i oprogramowania do planowania misji.

Czytelnikom bez tła w termografii podręcznik daje potrzebne podstawy fizyczne (część I); nie zastępuje jednak certyfikowanego szkolenia termograficznego, którego relację do uprawnień do podpisania raportu omawiamy w rozdz. 35.

## 0.7 Odpowiedzialność inspektora

Zadaniem inspektora nie jest „ocena obrazów termicznych". Jest nim poprawne pozyskanie danych, rzetelna ocena ich jakości, identyfikacja potencjalnych nieprawidłowości i przedstawienie wyników tak, by właściciel lub operator instalacji mógł na ich podstawie podjąć decyzję techniczną.

Raport z inspekcji jest elementem procesu diagnostycznego, a nie samodzielnym potwierdzeniem uszkodzenia. Znaczna część wykrytych anomalii wymaga weryfikacji innymi metodami, zanim stanie się podstawą decyzji o naprawie, wymianie czy roszczeniu gwarancyjnym. Inspektor, który o tym pamięta i dokumentuje granice swojej metody, chroni jednocześnie klienta i siebie — do tej zasady wracamy w rozdziałach o metrologii i obronie raportu (rozdz. 41) oraz odpowiedzialności prawnej (rozdz. 48).
