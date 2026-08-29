# Méthodes de synchronisation de base de données et de configuration

Gérez la connexion à la base de données active et synchronisez instantanément les changements de configuration sur votre système. N'oubliez pas de sauvegarder votre configuration après avoir fait des modifications directes via l'API.

- Vérifier la base de données active: `getApi().getBotConfig().database.activeDatabase;` _(Retourne "MySQL", "SQLite", "MongoDB", etc.)_
- Récupérer l'hôte DB : `getApi().getBotConfig().database.host;`
- Enregistrer les modifications de configuration : `getApi().saveConfig();` _(assure que toutes les modifications faites via l'API sont enregistrées dans la base de données/YAML)_
- Recharger la configuration : `getApi().reloadConfig();` _(Force le bot à extraire les données de la base de données)_
