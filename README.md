# Corsi

Archivio personale dei materiali didattici del corso di laurea in Ingegneria Elettronica e delle Telecomunicazioni (Università di Bologna).

## Struttura

Ogni directory corrisponde a un insegnamento. All'interno si trovano generalmente:

| Sottodirectory | Contenuto |
|---|---|
| `Prof/` | Slide, dispense ed esercizi del docente (PDF) |
| `Lab/` | Materiale di laboratorio e relazioni |
| `Altro/` | Materiale supplementare (articoli, video, riferimenti) |
| `Software/` | Software, installer, tarball specifici del corso |
| `Datasheet/` | Datasheet di componenti elettronici |
| `LaTeX/` | Sorgenti TeX/LaTeX per relazioni o appunti |
| `Relazione/` | Relazioni di progetto |
| `Esercitazioni/` | Esercitazioni e temi d'esame |

## Elenco degli insegnamenti

### Analisi e Matematica Applicata
- `anmat1` — Analisi Matematica 1
- `anmat2` — Analisi Matematica 2
- `anmat3` — Analisi Matematica 3
- `appmat` — Applicazioni di Matematica (Matematica Applicata)
- `calnum` — Calcolo Numerico
- `geomal` — Geometria e Algebra Lineare
- `memat` — Metodi Matematici
- `menum` — Metodi Numerici

### Fisica e Chimica
- `fis1` — Fisica Generale 1
- `fis2` — Fisica Generale 2
- `chim` — Chimica
- `compfis` — Complementi di Fisica
- `fss` — Fisica dello Stato Solido (potenziali periodici, modello di Kronig-Penney)

### Elettronica e Microelettronica
- `ele1` — Elettronica 1
- `ele2` — Elettronica 2
- `eledig` — Elettronica Digitale
- `elesdig1` — Elettronica dei Sistemi Digitali 1
- `elesdig2` — Elettronica dei Sistemi Digitali 2
- `eletlc1` — Elettronica delle Telecomunicazioni 1 (mixer, filtri, LNA, PA, linearizzazione)
- `eletlc2` — Elettronica delle Telecomunicazioni 2 (radar e SAR, tecniche di interconnessione digitale)
- `eleind` — Elettronica Industriale (amplificatori di potenza, convertitori DC-DC)
- `dispele` — Dispositivi Elettronici (fisica dei semiconduttori, trasporto)
- `microele` — Microelettronica (~2188 file, progetti CAD EDA completi)
- `optel1` — Optoelettronica 1
- `optel2` — Optoelettronica 2

### Elettrotecnica ed Energetica
- `elettind` — Elettrotecnica Industriale
- `eltcind` — Elettrotecnica Industriale (fotovoltaico, pannelli solari)

### Teoria dei Circuiti ed Elettromagnetismo
- `tecir1` — Teoria dei Circuiti 1
- `tecir2` — Teoria dei Circuiti 2
- `compem1` — Compatibilità Elettromagnetica 1
- `compem2` — Compatibilità Elettromagnetica 2

### Telecomunicazioni
- `comel1` — Comunicazioni Elettriche 1 (analisi segnali, inviluppo complesso)
- `comel2` — Comunicazioni Elettriche 2 (modulazioni numeriche)
- `retel` — Reti di Telecomunicazioni (IEEE 802, LAN/MAN)
- `sitel` — Sistemi di Telecomunicazioni
- `tel` — Telematica
- `ciaw` — Comunicazioni Wireless (ZigBee, IEEE 802.15.4)

### Antenne, Microonde e Radar
- `ant1` — Antenne 1 (radiatori elementari, parametri fondamentali)
- `ant2` — Antenne 2 (microstriscia, Sommerfeld, equazioni integrali)
- `antprop` — Antenne e Propagazione (FDFD, cavità risonanti)
- `scaf` — Campi Elettromagnetici e Antenne (guide d'onda, AWR Microwave Office)
- `ttmomm` — Tecniche e Tecnologie per Microonde e Onde Millimetriche (filtri, antenne planari)
- `sirad` — Sistemi Radar (SAR, radar meteorologici)
- `terad` — Tecniche Radar
- `siteleriv` — Sistemi di Telerilevamento (remote sensing)

### Segnali e Sistemi
- `ens1` — Elaborazione Numerica dei Segnali (DSP, trasformata Zeta)
- `assd` — Analisi dei Sistemi Dinamici (diagrammi di Bode, controllo)

### Controlli e Automazione
- `faut` — Fondamenti di Automatica
- `sensriv` — Sensori e Rivelatori

### Informatica e Sistemi Operativi
- `finf1` — Fondamenti di Informatica 1 (MATLAB, basi di programmazione)
- `finf2` — Fondamenti di Informatica 2 (algoritmi, strutture dati, grafi)
- `sisop` — Sistemi Operativi (memoria virtuale, processi, sincronizzazione)
- `calcel` — Calcolatori Elettronici (CPU, sistemi di numerazione)
- `labtel` — Laboratorio di Telematica (PHP, sessioni web)

### Progettazione e Laboratori
- `cadsisem` — CAD per Sistemi Elettronici (~5315 file, il corso più corposo)
- `labprogaf` — Laboratorio di Progettazione a Radiofrequenza (modulazioni, matching)
- `misel` — Misure Elettroniche

### Altri insegnamenti
- `afcq1` — Affidabilità e Controllo Qualità (FMEA, FMECA, QFD, statistica)
- `disp` — Materiali raccolti da più corsi (dispense)
- `ecorgaz` — Economia e Organizzazione Aziendale
- `fem` — Fisica Elettromagnetica (carta di Smith)
- `orgpoleur` — Organizzazione Politica Europea
- `orprof` — Orientamento Professionale
- `stat` — Statistica
- `sten` — Sistemi Termici ed Energetici (termodinamica, cicli a vapore)
- `tbecu` — Tecnologie Biomediche (diagnostica per immagini, colorimetria)
- `teretel` — Tecniche di Rete di Telecomunicazioni

## Tipi di file

| Estensione | Qtà approx | Descrizione |
|---|---|---|
| `.pdf` | ~1500 | Dispense, slide, esercizi, datasheet, articoli |
| `.tvz`, `.tvc`, `.cdb`, `.hdb`, `.nvc` | ~755 | File progetto CAD EDA (Cadence), tutti in `microele/Prof/` |
| `.m` | ~150 | Script e funzioni MATLAB (soprattutto in `cadsisem/` e `sirad/`) |
| `.ppt`/`.pptx` | ~120 | Presentazioni PowerPoint |
| `.zip`/`.rar` | ~100 | Archivi compressi di materiali e software |
| `.tex` | ~12 | Sorgenti LaTeX per relazioni e appunti (`labprogaf/`, `scaf/`) |
| `.mp4`, `.avi` | ~12 | Video, tutti in `sirad/` (simulazioni radar) |

## Dimensioni totali

~5 GB distribuiti su 67 directory. Le directory più grandi sono `disp` (401 MB), `optel2` (307 MB), `ttmomm` (304 MB), `elesdig2` (262 MB) e `sten` (251 MB). `cadsisem` è scesa a 202 MB (309 file) dopo la rimozione degli artefatti di simulazione.
