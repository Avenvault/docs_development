---
icon: question
---

# Foire aux questions (FAQ)

Voici les problèmes les plus courants rencontrés par les administrateurs de serveurs et la manière de les résoudre.

#### **Configuration & Installation**

Q : Comment trouver les identifiants de rôles (Role IDs) et de salons (Channel IDs) pour la configuration ?

R : Vous devez activer le mode développeur dans Discord.

1. Allez dans les Paramètres de Discord > Avancés > Activez le Mode développeur.
2. Faites un clic droit sur n'importe quel rôle, salon ou utilisateur, puis cliquez sur Copier l'identifiant du salon ou Copier l'identifiant du rôle en bas du menu.

Q : J'ai invité le bot, mais je ne vois pas `/ticketpanel` ni `/stats` ?

R : Les commandes Slash nécessitent des autorisations (scopes) spécifiques pour s'enregistrer.

1. Assurez-vous d'avoir invité le bot en cochant le scope `applications.commands` dans le générateur d'URL OAuth2.
2. Expulsez le bot et réinvitez-le avec la bonne URL. Remarque : Vous pouvez essayer d'appuyer sur F5, mais les commandes Slash globales peuvent parfois prendre jusqu'à une heure pour se synchroniser nativement sur tous les serveurs Discord, bien qu'elles apparaissent généralement instantanément.

#### **🛠️ Fonctionnalités & Erreurs**

Q : Le bot affiche une erreur `MongoTimeoutException` dans la console et plante.

R : Cela signifie que le bot ne parvient pas à joindre votre base de données MongoDB.

1. Vérifiez votre fichier `config.yml` pour vous assurer que l'URI de la base de données (`database.uri`) est correctement formatée.
2. Si vous utilisez MongoDB Atlas (Cloud), assurez-vous d'avoir ajouté l'adresse IP de votre serveur à la liste blanche (ou définissez-la sur `0.0.0.0/0` pour autoriser toutes les IP) dans l'onglet Network Access.

Q : Lorsqu'un membre de l'équipe prend en charge un ticket, le salon ne se verrouille pas !

R : Il s'agit presque toujours d'un problème de hiérarchie des rôles Discord ou de permissions.

1. Assurez-vous que `enableClaimRemoval: true` est bien activé dans votre configuration pour cette catégorie.
2. Assurez-vous que le rôle le plus élevé du Bot est placé au-dessus des rôles de l'équipe dans les paramètres de votre serveur Discord. Le bot ne peut pas retirer les permissions des rôles situés plus haut que le sien.
3. Assurez-vous que le bot dispose des permissions « Gérer les salons » et « Gérer les rôles », bien que la permission « Administrateur » soit recommandée.

Q : Pourquoi les transcriptions HTML ne génèrent-elles pas de lien ?

R : Le bot télécharge le fichier HTML généré directement sur le CDN de Discord via le `logsChannelId` spécifié dans votre configuration. Si le bot ne dispose pas de la permission « Joindre des fichiers » ou « Envoyer des messages » dans ce salon de journaux masqué spécifique, le téléchargement échouera et aucun lien ne pourra être généré. Vérifiez les permissions du salon !
