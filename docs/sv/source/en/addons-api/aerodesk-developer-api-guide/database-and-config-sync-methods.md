# Databas och konfiguration synkroniseringsmetoder

Hantera den aktiva databasanslutningen och synkronisera konfigurationsändringarna i ditt system omedelbart. Kom ihåg att spara din konfiguration efter direkta ändringar via API:et.

- Kontrollera aktiv DB: `getApi().getBotConfig().database.activeDatabase;` _(Returnerar "MySQL", "SQLite", "MongoDB", etc.)_
- Hämta DB Host: `getApi().getBotConfig().database.host;`
- Spara konfigurationsändringar: `getApi().saveConfig();` _(Säkerställer att eventuella ändringar som görs via API:et sparas i databasen/YAML)_
- Ladda om konfiguration: `getApi().reloadConfig();` _(Tvingar boten att dra färska data från databasen)_
