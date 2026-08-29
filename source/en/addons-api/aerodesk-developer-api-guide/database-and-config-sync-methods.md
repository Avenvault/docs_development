# Database & Config Sync Methods

Manage the active database connection and synchronize configuration changes across your system instantly. Remember to save your config after making direct modifications via the API.

* Check Active DB: `getApi().getBotConfig().database.activeDatabase;` _(Returns "MySQL", "SQLite", "MongoDB", etc.)_
* Retrieve DB Host: `getApi().getBotConfig().database.host;`
* Save Config Changes: `getApi().saveConfig();` _(Ensures any edits made via the API are saved to the database/YAML)_
* Reload Config: `getApi().reloadConfig();` _(Forces the bot to pull fresh data from the database)_
