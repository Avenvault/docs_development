# Datenbank & Konfigurationssynchronen

Verwalten Sie die aktive Datenbankverbindung und synchronisieren Sie die Konfigurationsänderungen auf Ihrem System sofort. Denken Sie daran, Ihre Konfiguration zu speichern, nachdem Sie direkte Änderungen über die API vorgenommen haben.

- Überprüfe Active DB: `getApi().getBotConfig().database.activeDatabase;` _(Returns "MySQL", "SQLite", "MongoDB", etc.)_
- DB Host abrufen: `getApi().getBotConfig().database.host;`
- Konfigurationsänderungen speichern: `getApi().saveConfig();` _(sichert alle über die API gemachten Änderungen werden in der Datenbank/YAML)_ gespeichert
- Konfiguration neu laden: `getApi().reloadConfig();` _(zwingt den Bot, frische Daten aus der Datenbank zu ziehen)_
