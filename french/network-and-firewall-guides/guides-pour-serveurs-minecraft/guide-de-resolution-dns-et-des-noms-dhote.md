# Guide de résolution DNS et des noms d'hôte

Si votre plugin affiche une erreur `java.net.UnknownHostException` dans la console lors du démarrage, cela signifie que votre serveur ne parvient pas à traduire le nom de domaine de notre serveur de licence en adresse IP.

Il s'agit d'un problème lié à la configuration du résolveur DNS de votre hébergeur.

#### Comment résoudre les problèmes de résolution DNS

**Modifier vos résolveurs DNS (Linux)**

Vous pouvez forcer votre serveur à utiliser des résolveurs DNS publics et fiables comme Cloudflare (`1.1.1.1`) ou Google (`8.8.8.8`).

1.  Ouvrez votre fichier `resolv.conf` :

    ```
    sudo nano /etc/resolv.conf
    ```
2.  Ajoutez les lignes suivantes tout en haut du fichier :

    ```
    nameserver 1.1.1.1
    nameserver 8.8.8.8
    ```
3. Enregistrez et quittez (`Ctrl+O`, `Entrée`, `Ctrl+X`). Redémarrez votre serveur Minecraft.

**Modifier vos résolveurs DNS (Windows Server)**

1. Ouvrez le Panneau de configuration > Réseau et Internet > Centre Réseau et partage.
2. Cliquez sur votre connexion active et sélectionnez Propriétés.
3. Sélectionnez Protocole Internet version 4 (TCP/IPv4) et cliquez sur Propriétés.
4. Cochez Utiliser l'adresse de serveur DNS suivante et saisissez :
   * Serveur DNS préféré : `1.1.1.1`
   * Serveur DNS auxiliaire : `8.8.8.8`
5. Cliquez sur OK et redémarrez votre serveur Minecraft.

