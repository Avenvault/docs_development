# Base de datos y Config Sync Methods

Administre la conexión de base de datos activa y sincronice los cambios de configuración en su sistema al instante. Recuerde guardar su configuración después de hacer modificaciones directas a través de la API.

- Revise Active DB: `getApi().getBotConfig().database.activeDatabase;` _(Returns "MySQL", "SQLite", "MongoDB", etc.)_
- Recuperar host DB: `getApi().getBotConfig().database.host;`
- Guardar Cambios de Config: `getApi().saveConfig();` _(asegura que cualquier edición realizada a través de la API se guardan en la base de datos/YAML)_
- Recargar Config: `getApi().reloadConfig();` _(Forza al bot a extraer datos nuevos de la base de datos)_
