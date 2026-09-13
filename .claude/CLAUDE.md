# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

See `README.md` for the full course listing, directory structure, and file type breakdown.

This is a personal archive of Italian university engineering course materials (~5 GB working tree, ~67 courses, ~4700 tracked files). Most content is PDFs (lecture notes, exercises, datasheets), plus EDA project files, MATLAB/Scilab scripts, and LaTeX sources. There is no build system, test suite, or software project structure — this is a document storage repo. There is nothing to build, lint, or test.

**Always measure sizes with `.git` excluded.** `du -sh .` reports 9.7 GB here, but 4.5 GB of that is the object database; the working tree is 5.1 GB. Quote `du -sh --exclude=.git .` (per-course `du -sh <course>/` needs no exclusion). Comparing a `.git`-inclusive total against the README's `.git`-exclusive `~5 GB` reads as a false discrepancy.

## Conventions that aren't obvious from the tree

**Every course has a consolidated `<course>/<course>.pdf` at its root.** E.g. `retel/retel.pdf` (90 MB), `sirad/sirad.pdf` (86 MB). These merged full-course PDFs are the largest files in the repo and are usually the right thing to read first or grep for a topic, before descending into `Prof/`. They account for most of the disk footprint.

**Course directory conventions.** Each course contains a subset of: `Prof/`, `Lab/`, `Altro/`, `Software/`, `Datasheet/`, `LaTeX/`, `Relazione/`, `Esercitazioni/`. Not every course has all of them; `Prof/` is near-universal.

**Topics are searchable by abbreviation:** `eleind` = industrial electronics, `elesdig` = digital systems electronics, `tecir` = circuit theory, `comel` = electrical communications, `compem` = EMC, `ant`/`antprop` = antennas & propagation, `ttmomm` = microwave/mm-wave, `sirad`/`terad` = radar, `ens1` = signals & systems, `fss` = fisica dello stato solido, `finf` = computer science, `faut`/`assd` = control systems, `scaf` = campi elettromagnetici e antenne, `eletlc` = elettronica delle telecomunicazioni, `siteleriv` = remote sensing.

## EDA and scripting tooling

Tool projects are confined to a few courses; knowing which tool lives where saves a lot of hunting.

| Tool | Where | Artifacts |
|---|---|---|
| Cadence (Virtuoso) | `microele/Prof/` | `.cdb`, `.hdb` cell libraries (~750 files) |
| Intel/Altera Quartus | `microele/` | `.qpf`, `.qsf`, `.qws`, `.pof`, `.pin`, `.rpt`, `.summary` |
| AWR Microwave Office | `scaf/`, `ttmomm/` | `.emp`, `.ads` |
| Ansys HFSS | `cadsisem/Lab/HFSS_simulations/` | simulation artifacts (see cleanup note) |
| Scilab | `microele/` | 64 `.sci` files |
| MATLAB | `cadsisem/` (138 `.m`), `sirad/` (6), scattered elsewhere | `.m` |
| LaTeX | `labprogaf/`, `scaf/`, `ttmomm/`, `cadsisem/` | `.tex` |

## Commit workflow

Course materials were staged in **deliberately sized batches of roughly 500 MB**, with commit messages of the form `Add course materials: <courses> — batch N/M, <size>`. Follow this when adding large amounts of material: keep individual commits near that size rather than committing a whole course tree at once. No file in the repo exceeds 100 MB (the current maximum is 90 MB), which is worth preserving — GitHub rejects pushes containing files over 100 MB.

There is **no git-lfs** — binary assets are stored directly in the object database.

**Cleanup is expected, not just addition.** Recent history removes redundant top-level `.zip` archives, `Prof/` backup zips, and EDA simulation artifacts. When adding material, prefer removing the redundant archive or raw simulation output over committing both it and its extracted/derived form.

## File-size awareness

Directories `cadsisem/` (202 MB) and `microele/` (103 MB, 2188 files) contain large EDA tool projects. Avoid exhaustive scans of these without a specific target — a recursive grep over them will hit thousands of generated `.cdb`/`.hdb`/`.rpt` files.

## Keeping README.md in sync

`README.md` is the human-facing index and is written in Italian; this file is the agent-facing one, in English. They are both edited by hand, so nothing enforces agreement. The README was reconciled against the tree on 2026-09-11 — all 67 course directories are listed, and the size and file-count figures match. Update it when you add or remove a course, or when a course's dominant topic changes.

## Commonly used commands for Claude Code

Since this is a document storage repository with no code to build or test, typical Claude Code usage focuses on:
- **Searching content**: Use `grep -r` or `rg` to find topics across PDFs and text files
  - Example: `grep -r "Kronig-Penney" fss/` to find Kronig-Penney model in solid state physics
  - Example: `rg -i "fourier" ens1/` (if ripgrep is available) for signals and systems
- **Reading consolidated PDFs**: Start with `<course>/<course>.pdf` for each course
  - Example: `open retel/retel.pdf` (on macOS) or use any PDF viewer
- **Navigating course structure**: Use standard directory listing commands
  - Example: `ls -la microele/` to see what's in the microelectronics course
  - Example: `find cadsisem -name "*.m" -type f` to find MATLAB scripts
- **Getting course overviews**: Check each course's README if present, or look at the main README.md
- **PDF text extraction**: For searching within PDFs, consider using `pdftotext` (if available) or Claude's PDF reading capability
  - Example: `pdftotext fss/fss.pdf - | grep -i "band gap"` (requires poppler utilities)

## High-level architecture and structure

The repository follows a simple course-based organization:
1. **Top-level**: 67 directories, each representing a university course
2. **Per-course**: Standard subdirectories for different material types (slides, labs, software, etc.)
3. **Consolidated resources**: Each course typically has a single comprehensive PDF at its root
4. **Specialized tools**: Certain courses host specific EDA or software tool projects:
   - Microelectronics (`microele/`): Cadence, Quartus, Scilab projects
   - CAD for Electronic Systems (`cadsisem/`): MATLAB scripts, HFSS simulations, LaTeX
   - Radar (`sirad/`): MATLAB scripts, video files
   - Electromagnetic Fields and Antennas (`scaf/`): AWR Microwave Office projects, LaTeX
   - Microwave/mm-wave Technologies (`ttmomm/`): AWR Microwave Office projects

This structure reflects the archival nature of the repository - it's organized for reference and retrieval of educational materials rather than software development.

## Working with different file types

- **PDFs**: Best for initial topic exploration via the consolidated course PDFs
- **MATLAB (.m)**: Found primarily in `cadsisem/` and `sirad/`; can be viewed or executed if MATLAB is available
- **Scilab (.sci)**: Located in `microele/`; require Scilab to run
- **EDA projects**: 
  - Cadence: `.cdb`, `.hdb` files in `microele/Prof/`
  - Quartus: `.qpf`, `.qsf`, etc. in `microele/`
  - AWR: `.emp`, `.ads` files in `scaf/` and `ttmomm/`
- **LaTeX (.tex)**: Source files in `labprogaf/`, `scaf/`, `ttmomm/`, `cadsisem/` for document compilation
- **Other**: ZIP/RAR archives, video files (.mp4, .avi), PowerPoint presentations

## Important notes for Claude Code usage

1. **No execution environment**: This repository doesn't contain executable software projects, so there's nothing to "run" in the traditional sense
2. **Focus on retrieval**: The value comes from finding and referencing educational materials
3. **Large binary files**: Many PDFs are large (50-100 MB range); use course PDFs for broad searches before diving into specialized directories
4. **Course abbreviations**: Learn the standard abbreviations used in directory names for efficient navigation
5. **Cross-referencing**: Topics often span multiple courses (e.g., Fourier analysis appears in both signals/systems and electronics courses)

When adding new material:
- Follow the existing directory structure for the course
- Consider creating/updating the consolidated course PDF if significant new content is added
- Adhere to the ~500 MB commit batch guideline for large additions
- Remove redundant files (like simulation outputs) when keeping derived versions