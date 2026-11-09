# Changelog

Tutte le modifiche rilevanti a questo progetto sono documentate in questo file.

Il formato segue [Keep a Changelog](https://keepachangelog.com/it/1.1.0/)
e il progetto adotta il [Semantic Versioning](https://semver.org/lang/it/).

## [Unreleased]

## [1.2.0] - 2026-11-09

### Aggiunto
- Versione dell'app in un'unica costante `APP_VERSION`, mostrata nella sidebar.
- Il backup JSON esportato include `appVersion`, `schemaVersion` ed `exportedAt`; il nome file contiene la data.
- Validazione e normalizzazione dei dati caricati da localStorage o importati da JSON (file non validi o creati da versioni future vengono rifiutati con un messaggio chiaro).
- Conferma prima di eliminare un conto.
- Validazione del form: data fine non precedente alla data inizio, intervallo personalizzato ≥ 1 giorno.

### Corretto
- **Sfasamento di un giorno** nelle date: il parsing `new Date('YYYY-MM-DD')` e `toISOString()` lavoravano in UTC, quindi in Italia movimenti e saldi noti risultavano spostati di un giorno (e "oggi" poteva essere ieri tra mezzanotte e le 2).
- **Ricorrenze mensili che slittano**: un movimento il 31 diventava il 28 dopo febbraio e restava al 28 per sempre; ora ogni occorrenza è calcolata dalla data di inizio.
- **Ricorrenze giornaliere troncate** dopo circa 27 anni (limite fisso di 10.000 iterazioni) con orizzonti lunghi.
- Annulla/Ripeti modificava il tema salvato senza applicarlo e annullava anche il cambio di conto selezionato.
- Modificare un movimento rimosso nel frattempo (es. con Annulla) lo faceva sparire senza salvarlo.
- Import JSON: il conto selezionato poteva puntare a un conto inesistente (UI bloccata) e non era possibile reimportare lo stesso file due volte di seguito.
- Nomi di conti e descrizioni venivano inseriti come HTML (possibile iniezione di codice da un JSON importato).
- Rinominare un conto non aggiornava il titolo in alto.
- Classe CSS `.mt` usata ma non definita.

### Rimosso
- Dipendenze inutilizzate jsPDF e html2canvas.

## [1.1.0] - 2026-09-27

- Prima versione tracciata nel repository.

[Unreleased]: ../../compare/v1.2.0...HEAD
[1.2.0]: ../../compare/v1.1.0...v1.2.0
[1.1.0]: ../../releases/tag/v1.1.0
