# Metody synchronizacji bazy danych i konfiguracji

Zarządzaj aktywnym połączeniem z bazą danych i natychmiast synchronizuj zmiany konfiguracji w systemie. Pamiętaj, aby zapisać konfigurację po dokonaniu bezpośrednich modyfikacji przez API.

- Sprawdź aktywny DB: `getApi().getBotConfig().database.activeDatabase;` _(Returns "MySQL", "SQLite", "MongoDB" itp.)_
- Pobierz DB Host: `getApi().getBotConfig().database.host;`
- Zapisz zmiany konfiguracji: `getApi().saveConfig();` _(Wymaguje wszelkie zmiany dokonane przez API są zapisywane w bazie danych/YAML)_
- Przeładuj konfigurację: `getApi().reloadConfig();` _(Zmusza bota do wyciągnięcia świeżych danych z bazy danych)_
