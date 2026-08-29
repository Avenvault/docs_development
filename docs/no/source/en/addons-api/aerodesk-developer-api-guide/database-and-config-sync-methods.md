# Synk. av database & Konfigurasjon

Administrer den aktive databasekoblingen og synkroniser konfigurasjonsendringene på tvers av systemet umiddelbart. Husk å lagre konfigurasjonen etter å ha gjort direkte endringer via API.

- Sjekk Active DB: `getApi().getBotConfig().database.activeDatabase;` _(Returns "MySQL", "SQLite", "MongoDB", etc.)_
- Hent DB Vert: `getApi().getBotConfig().database.host;`
- Lagre Konfigurasjonsendringer: `getApi().saveConfig();` _(Sikrer alle endringer som er gjort via API-et, lagres i databasen/YAML)_
- Last inn konfigurasjon: `getApi().reloadConfig();` _(tvinger botten til å hente nye data fra databasen)_
