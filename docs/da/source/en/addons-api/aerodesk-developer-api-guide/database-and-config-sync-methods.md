# Database & Config Sync Methods

Administrer den aktive database forbindelse og synkronisere konfigurationsændringer på tværs af dit system med det samme. Husk at gemme din config efter at have foretaget direkte ændringer via API.

- Kontroller Aktiv DB: `getApi().getBotConfig().database.activeDatabase;` _(Returnerer "MySQL", "SQLite", "MongoDB", etc.)_
- Hent DB Vært: `getApi().getBotConfig().database.host;`
- Gem Config Ændringer: `getApi().saveConfig();` _(Herrer eventuelle redigeringer foretaget via API gemmes i databasen/YAML)_
- Genindlæs konfiguration: `getApi().reloadConfig();` _(Kræver botten for at hente friske data fra databasen)_
