# Local Environment Port Forwarding & Tunnels

Si vous êtes développeur ou propriétaire de serveur et que vous testez nos plugins sur un réseau domestique local avant de les déployer chez un hébergeur public, vous devrez peut-être exposer votre serveur à Internet pour vérifier le jeu avec des amis.

#### **Option A : Redirection de port sur le routeur**

1. Connectez-vous à l'interface d'administration de votre routeur (généralement 192.168.1.1 ou 10.0.0.1).
2. Localisez la section « Transfert de port » ou « Serveurs virtuels ».
3. Créez une nouvelle règle pointant vers l'adresse IPv4 locale de votre ordinateur.
4. Réglez le port interne et le port externe sur 25565 (ou sur le port utilisé par votre serveur).
5. Réglez le protocole sur TCP/UDP.
6. Enregistrez et appliquez. Les joueurs peuvent désormais se connecter en utilisant votre adresse IP publique.

#### **Option B : Services de tunneling (aucun transfert de port requis)**

Si vous ne pouvez pas accéder à votre routeur ou si votre fournisseur d'accès à Internet utilise le CGNAT (Carrier-Grade NAT), vous pouvez recourir à des services de tunneling pour exposer votre serveur local.

* [Playit.gg](https://playit.gg): Un proxy mondial gratuit spécialement conçu pour le jeu vidéo. Téléchargez l'agent, exécutez-le en parallèle de votre serveur, et il vous fournira automatiquement une adresse IP publique ainsi qu'un port.
* [Ngrok](https://ngrok.com/): Un outil de tunnelisation généralisé.

```
ngrok tcp 25565
```

(Remarque : la version gratuite de Ngrok attribue un port aléatoire à chaque redémarrage.)

