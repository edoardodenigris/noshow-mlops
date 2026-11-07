```markdown
| Data | Decisione | Perché | Alternative scartate |
|---|---|---|---|
| 2026-10-06 | Regione us-central1 | Free tier, dati pubblici | europe-west1 (free tier ridotto) |
| 2026-10-06 | Budget alert 10 € | Nessun credito trial | — |
| 2026-10-06 | Cloud Shell per lo sviluppo iniziale | Zero setup locale | VS Code locale (più avanti) |
| 2026-11-07 | Dataform via CLI in Cloud Shell, codice in `dataform/` nel repo | Un solo repo versionato; in futuro eseguibile da GitHub Actions | Dataform gestito in console (token in Secret Manager, UI non necessaria ora) |
| 2026-11-07 | Sorgente raw dichiarata (declaration) e letta con `ref()` | Lineage completo, un solo punto da cambiare, errori scoperti al compile | Indirizzo della tabella scritto a mano nella query |
| 2026-11-07 | Tabelle in `noshow_clean`, test in `noshow_assertions` | Separazione raw/clean leggibile in BigQuery | Dataset di default `dataform` |
| 2026-11-07 | ID (paziente, appuntamento) come STRING | Sono identificativi, non numeri; il FLOAT perde precisione | Lasciarli numerici |
| 2026-11-07 | AppointmentDay → DATE; nuova colonna `lead_time_days` | L'orario era sempre 00:00 (finto); il lead time è la feature candidata principale | Tenere il timestamp |
| 2026-11-07 | Escluse Age < 0 (1 riga) e lead time negativo (5 righe) → 110.521 righe | Dati impossibili; perdita verificata con i conteggi | Correggere o imputare i valori |
| 2026-11-07 | Age > 100 mantenuti | Rari ma plausibili | Cap o esclusione |
| 2026-11-07 | Handcap → `handicap_level` intero (0-4) | È un livello, non un flag; trasformazione rimandata al feature engineering | Convertirlo in booleano |
| 2026-11-07 | SMS_received mantenuto nella tabella clean | Pulire ≠ scegliere le feature; si decide dopo l'analisi del leakage | Escluderlo subito |
| 2026-11-07 | Credenziali Dataform via ADC, file in `.gitignore` | Nessuna chiave da gestire, repo pubblico | Chiave JSON di service account |
| 2026-11-07 | Push con token GitHub classico (scope `repo`, 90 gg) | Nel token fine-grained non era disponibile il permesso Contents | Token fine-grained limitato al repo |
```


