# Réseau de proxies et transfert d'IP (Velocity / BungeeCord)

Les serveurs font presque toujours partie d'un réseau proxy plus vaste. Pour vous assurer que nos plugins identifient correctement les joueurs et ne déclenchent pas de faux positifs en raison du routage du proxy, vous devez configurer vos serveurs backend pour qu'ils acceptent correctement les données transmises.

#### ⚙️ Configuration des serveurs backend Spigot / Paper

**Si vous utilisez BungeeCord ou Waterfall :**

1. Ouvrez le fichier `spigot.yml` sur votre serveur de jeu backend.
2.  Localisez le paramètre `bungeecord` et réglez-le sur `true` :

    ```
    settings:
      bungeecord: true
    ```
3. Ouvrez le fichier `server.properties` et assurez-vous que `online-mode` est réglé sur `false`.
4. Important : Assurez-vous que le pare-feu de votre proxy empêche les joueurs de se connecter directement au port backend.

**Si vous utilisez Velocity (Transfert moderne) :**

Les serveurs Paper modernes prennent en charge nativement le transfert sécurisé de Velocity.

1. Ouvrez le fichier `config/paper-global.yml` sur votre serveur backend.
2.  Localisez le bloc de configuration Velocity :

    ```
    proxies:
      velocity-support:
        enabled: true
        online-mode: true
        secret: "VOTRE_SECRET_VELOCITY_ICI"
    ```
3. Collez la clé secrète générée par votre proxy Velocity dans le champ `secret`.
4. Assurez-vous que `online-mode` est réglé sur `false` dans votre fichier `server.properties`.
