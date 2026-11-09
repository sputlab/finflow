# FinFlow

Web app single-file (HTML/CSS/JS) per la proiezione del saldo e la pianificazione del cashflow.

## Uso

Apri `index.html` nel browser. Non serve build né server.

Per usarla online puoi attivare GitHub Pages (Settings → Pages → branch `main`, cartella `/root`).

## Dipendenze (via CDN)

- Chart.js 4.4.1 + chartjs-plugin-zoom 2.0.1

## Dati

I salvataggi JSON esportati dall'app contengono dati personali e sono esclusi dal repository (`.gitignore`).

## Versioni

Il progetto segue il [Semantic Versioning](https://semver.org/lang/it/) (`MAJOR.MINOR.PATCH`):

- **PATCH** – correzioni di bug senza nuove funzioni.
- **MINOR** – nuove funzioni retrocompatibili (i backup JSON esistenti restano importabili).
- **MAJOR** – modifiche incompatibili (es. backup vecchi non più importabili senza conversione).

Per rilasciare una nuova versione:

1. Aggiorna `APP_VERSION` in `index.html` (e `SCHEMA_VERSION` solo se cambia la struttura dei dati).
2. Sposta le voci di `[Unreleased]` in una nuova sezione di [CHANGELOG.md](CHANGELOG.md).
3. Committa e crea il tag: `git tag -a vX.Y.Z -m "FinFlow vX.Y.Z"` e `git push --follow-tags`.
