# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this repository.

## What this repository is

This is a personal archive of Italian university engineering course materials (University of Bologna, Ingegneria Elettronica e delle Telecomunicazioni): ~5.2 GB working tree (always measure with `.git` excluded — the object database adds ~4.5 GB), 68 course directories, ~4,830 tracked files. Content is mostly PDFs (lecture notes, exercises, datasheets), plus EDA project files, MATLAB/Scilab scripts, and LaTeX sources.

**This is not a software project.** There is no build system, no test suite, no linter, and nothing to run. Do not invent `make`, `npm test`, pytest, or similar commands. All work here is retrieval and organization: searching, reading, moving, adding, or removing materials.

## Commonly used commands

These are the "development" commands for this repo:

- Search text across courses: `grep -r "Kronig-Penney" fss/` or `rg -i "fourier" ens1/`.
  - Avoid recursive greps over `cadsisem/` and `microele/` — they contain thousands of generated EDA files (`.cdb`, `.hdb`, `.rpt`, `.summary`).
- Search inside a PDF: `pdftotext retel/retel.pdf - | grep -i "topic"` (poppler), or read the PDF directly — Claude can read PDFs.
- Inspect a course: `ls -la microele/`; find MATLAB scripts: `find cadsisem -name "*.m" -type f`.
- Sizes (always exclude `.git`): `du -sh --exclude=.git .` for the whole tree (~5.2 GB working tree); `du -sh <course>/` for a single course (no exclusion needed).
- List courses: top-level `ls` shows the 68 course directories; `README.md` (Italian) is the human-facing course index, reconciled against the tree on 2026-09-11.

## High-level architecture and structure

1. **Top level**: one directory per course (e.g. `retel/`, `sirad/`, `cadsisem/`), plus `README.md` and this file.
2. **Per course**: a subset of `Prof/` (slides, handouts, exercises — near-universal), `Lab/`, `Altro/`, `Software/`, `Datasheet/`, `LaTeX/`, `Relazione/`, `Esercitazioni/`. Not every course has all of them.
3. **Consolidated resource**: every course has a single `<course>/<course>.pdf` at its root (e.g. `retel/retel.pdf`, 90 MB; `sirad/sirad.pdf`, 86 MB). These merged full-course PDFs are usually the largest files and the right place to start a topic search before descending into `Prof/`.
4. **Specialized tooling by course** (knowing where each tool lives avoids exhaustive scans):
   - Cadence (Virtuoso): `microele/Prof/` — `.cdb`, `.hdb` cell libraries (~750 files)
   - Intel/Altera Quartus: `microele/` — `.qpf`, `.qsf`, `.qws`, `.pof`, `.pin`, `.rpt`, `.summary`
   - AWR Microwave Office: `scaf/`, `ttmomm/` — `.emp`, `.ads`
   - Ansys HFSS: `cadsisem/Lab/HFSS_simulations/`
   - Scilab: `microele/` — 64 `.sci` files
   - MATLAB: `cadsisem/` (138 `.m`), `sirad/` (6), scattered elsewhere
   - LaTeX: `labprogaf/`, `scaf/`, `ttmomm/`, `cadsisem/`

## Course abbreviations (topic search shortcuts)

`eleind` industrial electronics · `elesdig` digital systems electronics · `tecir` circuit theory · `comel` electrical communications · `compem` EMC · `ant`/`antprop` antennas & propagation · `ttmomm` microwave/mm-wave · `sirad`/`terad` radar · `ens1` signals & systems · `fss` solid-state physics · `finf` computer science · `faut`/`assd` control systems · `scaf` electromagnetic fields & antennas · `eletlc` telecommunication electronics · `siteleriv` remote sensing. Directory names follow these codes; `README.md` maps each code to its full course name.

## Directory sizes worth knowing

Largest: `disp` (401 MB), `optel2` (307 MB), `ttmomm` (304 MB), `elesdig2` (262 MB), `sten` (251 MB). Heavy EDA directories: `cadsisem/` (202 MB, 309 files), `microele/` (103 MB, 2188 files). No file exceeds 100 MB (current max 90 MB) — GitHub rejects pushes with files over 100 MB.

## Commit workflow

Course materials were staged in deliberately sized batches of roughly 500 MB, with messages like `Add course materials: <courses> — batch N/M, <size>`. Follow this for large additions: keep individual commits near that size rather than committing a whole course tree at once. Cleanup is expected, not just addition — when adding material, prefer removing the redundant archive or raw simulation output over committing both it and its derived form. There is no git-lfs; binaries live directly in the object database.

## Keeping README.md in sync

`README.md` (Italian, human-facing index) and this file (English, agent-facing) are both edited by hand — nothing enforces agreement. Update both when you add or remove a course, or when a course's dominant topic changes.
