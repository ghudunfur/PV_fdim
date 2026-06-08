# Inspekcje termowizyjne farm PV UAV — podręcznik

Repozytorium książki pisanej w modelu „książka-jako-kod". Rozdziały w markdown,
jedna centralna baza źródeł, automatyczna kompilacja przez GitHub Actions.

## Struktura

```
.
├── rozdzialy/              # treść książki, pliki numerowane wg kolejności
│   └── 00_wprowadzenie.md
├── bibliografia.bib        # JEDNA centralna baza źródeł (single source of truth)
├── ieee.csl                # styl cytowań (numeryczny IEEE)
├── docs/
│   ├── syllabus.md         # plan całości (Syllabus V5)
│   └── README_bibliografia.md   # konwencja cytowań i przypisów
└── .github/workflows/
    └── build.yml           # kompilacja PDF + DOCX przy każdym pushu
```

## Jak pisać

1. Każdy rozdział to osobny plik w `rozdzialy/` z numerem w nazwie
   (`01_rola_termografii.md`, `02_budowa_systemu_pv.md`…). Numer decyduje o kolejności
   w złożonej książce.
2. Źródła cytuj kluczem z `bibliografia.bib`, np. `[@iec62446-3]`. Nowe źródło → dopisz
   wpis do `bibliografia.bib`. Szczegóły: `docs/README_bibliografia.md`.
3. Przypis objaśniający (komentarz autora) → `^[treść...]`. Numeracja przypisów i lista
   literatury powstają automatycznie przy kompilacji — nie wpisuj numerów ręcznie.

## Kompilacja

**Automatyczna:** każdy push uruchamia `build.yml`; gotowe `ksiazka.pdf` i `ksiazka.docx`
pobierzesz z zakładki *Actions → ostatni przebieg → Artifacts*. Można też uruchomić
ręcznie (*Actions → build-book → Run workflow*).

**Lokalnie (opcjonalnie):**

```bash
pandoc rozdzialy/*.md --citeproc \
  --bibliography=bibliografia.bib --csl=ieee.csl \
  --toc -V lang=pl -o ksiazka.pdf
```

## Praca wieloautorska

Rozdział = gałąź + pull request. `bibliografia.bib` to jedyny plik współdzielony przez
wszystkich — przy konflikcie scalaj ręcznie, zachowując oba nowe wpisy.

## Przed publikacją

Zob. listę kontrolną na końcu `docs/README_bibliografia.md` (weryfikacja wydań norm,
status rewizji ISO 15469, ujednolicenie pisowni „okta").
