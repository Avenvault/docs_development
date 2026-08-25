# Tableaux de bord et webhooks entrants (trafic entrant)

Bien que certains de nos bots utilisent uniquement des connexions sortantes, votre bot nécessite une configuration réseau entrante s'il inclut l'une des fonctionnalités suivantes :

* Un tableau de bord Web : Un panneau de contrôle (fonctionnant généralement sous Express.js ou Flask) où les utilisateurs se connectent via un navigateur pour configurer le bot.
* Webhooks de vote : Réception de requêtes POST en temps réel provenant de sites de listes de bots (comme Top.gg) lorsqu'un utilisateur vote pour votre bot.

#### Comment configurer le trafic entrant

Si votre bot héberge un serveur web, vous devez ouvrir les ports entrants sur votre machine hôte pour permettre aux utilisateurs et aux webhooks d'y accéder.

* Ouvrir les ports entrants : Autorisez le trafic sur le port utilisé par votre serveur web (par ex., `8080` ou `3000`).
  * Linux (UFW) : `sudo ufw allow 8080/tcp`
* Configurer un proxy inverse (Recommandé) : Au lieu de fournir aux utilisateurs une adresse IP et un port (par ex., `[http://192.168.1.5:8080](http://192.168.1.5:8080)`), installez un proxy inverse (_reverse proxy_) comme Nginx ou Apache.
  1. Configurez Nginx pour écouter sur le port standard 443 (HTTPS) et router le trafic en interne vers le port local de votre bot (8080).
  2. Cela vous permet d'associer un nom de domaine (`dashboard.votrebot.com`) et un certificat SSL (via Let's Encrypt) pour garantir la sécurité des données de vos utilisateurs.
