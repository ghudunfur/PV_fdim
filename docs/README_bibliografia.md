# System cytowań i bibliografii — instrukcja

Podręcznik używa **Pandoc + BibTeX** w stylu numerycznym (IEEE). Numeracja przypisów
i lista literatury powstają **automatycznie przy kompilacji** — autorzy nie wpisują numerów ręcznie.

## Jedno źródło prawdy

Wszystkie źródła żyją w jednym pliku: **`bibliografia.bib`**. To jedyne miejsce, gdzie
przechowujemy dane bibliograficzne. Nie utrzymujemy żadnej drugiej, ręcznej listy literatury
— renderowana bibliografia jest generowana z `.bib` i pojawia się na końcu skompilowanej książki.

Plik `bibliografia.bib` należy do repozytorium książki (po stronie autorów). Każdy autor
dopisuje swoje pozycje i commituje.

## Dwa różne strumienie

| Strumień | Co to | Jak zapisać w tekście | Gdzie żyje |
|---|---|---|---|
| **Cytowanie źródła** | odwołanie do normy/dokumentu | `[@iec62446-3]` | klucz w `bibliografia.bib` |
| **Przypis objaśniający** | komentarz autora | `^[treść przypisu...]` | inline, w treści rozdziału |

Cytowanie renderuje się jako `[1]`, `[2]`… (styl numeryczny).
Przypis objaśniający renderuje się jako automatyczny numer górny — **etykiety nie podajemy**,
Pandoc numeruje sam, ciągle przez całą książkę.

Przypis może zawierać cytowanie, np.:
`^[Norma odsyła do ISO 15469 [@iso15469], co jest jednak nieścisłe...]`

## Konwencja klucza cytowania

`{organ}{numer}` — małe litery, bez spacji. Przykłady: `iec62446-3`, `iec61724-1`,
`wmo306`, `wmo8`, `wmo407`, `iso15469`, `iso9060`, `iso9847`.

## Kompilacja całej książki

Z katalogu repozytorium (zakładając rozdziały w `rozdzialy/` w kolejności nazw plików):

```bash
pandoc rozdzialy/*.md \
  --citeproc \
  --bibliography=bibliografia.bib \
  --csl=ieee.csl \
  --metadata link-citations=true \
  -o ksiazka.pdf
```

- `--citeproc` włącza przetwarzanie cytowań.
- `ieee.csl` to plik stylu — pobrać z repozytorium stylów CSL
  (`citation-style-language/styles` na GitHub). Zmiana stylu = podmiana tego jednego pliku.
- Zmiana kolejności rozdziałów → przy następnej kompilacji numeracja przelicza się sama.

Dla wyjścia Word: zamień `-o ksiazka.pdf` na `-o ksiazka.docx`.

## Do weryfikacji przed publikacją

- Wydania/lata norm względem oficjalnych katalogów IEC/ISO/WMO (część dat w `.bib` wymaga potwierdzenia).
- Status rewizji ISO 15469 (następca: ISO/CIE 15469).
- Ujednolicić pisownię „okta" w całym tekście (IEC zapisuje „okta", nie „octa").
- Doprecyzować konkretny dokument operacyjny IECRE przy faktycznym cytowaniu.
