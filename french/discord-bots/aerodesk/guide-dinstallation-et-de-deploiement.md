---
icon: desktop-arrow-down
---

# Guide d'installation et de déploiement

Mettre en place et exécuter Enterprise Ticket System sur votre machine d'hébergement (VPS, serveur dédié ou panneau Pterodactyl) est un processus simple. Suivez attentivement ces étapes pour garantir un déploiement fluide.

#### 📋 Prérequis

Avant de commencer, assurez-vous que votre environnement d'hébergement dispose des éléments suivants :

* [ ] Java 17 ou supérieur (requis pour les versions modernes de JDA).
* [ ] Une solution de base de données (cluster MongoDB, base de données SQL ou accès au stockage local pour JSON).
*   [ ] Un jeton de bot Discord (Bot Token) (obtenu depuis le [Discord Developer Portal](https://discord.com/developers/applications/)).



#### **Étape 1 : Configuration de l'application Discord**

1. Accédez au Discord Developer Portal et créez une nouvelle application (_New Application_).
2. Naviguez vers l'onglet Bot et cliquez sur Add Bot.
3. Important : Dans la section Bot, faites défiler jusqu'à Privileged Gateway Intents et activez :
   * Server Members Intent (nécessaire pour vérifier les rôles).
   * Message Content Intent (nécessaire pour la détection des mots-clés de la FAQ).
4. Enregistrez vos modifications et copiez votre jeton de bot (_Bot Token_). Gardez-le secret !
5. Invitez le bot sur votre serveur en allant dans OAuth2, puis faites défiler jusqu'à OAuth2 URL Generator. Veillez à cocher à la fois `bot` et `applications.commands` (requis pour les commandes Slash), cochez `Administrator` dans _General Permissions_, puis collez dans votre navigateur l'URL fournie sous _Generated URL_.

#### **Étape 2 : Préparation du serveur**

1. Créez un nouveau dossier sur votre machine d'hébergement pour le bot (par ex. `AeroDesk`).
2. Téléchargez la dernière version et placez-la dans ce dossier.
3.  Lancez le bot une première fois pour générer les fichiers de configuration :

    <pre><code>java -jar <a data-footnote-ref href="#user-content-fn-1">[NAME]</a>.jar
    </code></pre>
4. Le bot s'arrêtera automatiquement et vous informera qu'un fichier `config.yml` a été généré.

#### **Étape 3 : Configuration**

1. Ouvrez le fichier `config.yml` nouvellement généré.
2. Collez votre jeton de bot (_Bot Token_) et votre identifiant personnel d'utilisateur Discord (_Owner ID_).
3. Configurez l'URI de votre base de données (si vous utilisez MongoDB ou SQL).
4. Remplissez les paramètres spécifiques à votre serveur, notamment les identifiants de rôles, de salons et vos configurations de catégories (consultez le guide de [configuration pour](configuration-guide.md) plus de détails).
5. Enregistrez le fichier.

#### **Étape 4 : Démarrage final**

Démarrez à nouveau le bot à l'aide de votre script de démarrage préféré, de `screen` ou de votre panneau Pterodactyl :

<pre><code>java -Xms1G -Xmx2G -jar <a data-footnote-ref href="#user-content-fn-1">[NAME]</a>.jar
</code></pre>

Si la configuration est correcte, la console affichera une connexion réussie à la base de données et confirmera que vos commandes Slash ont été enregistrées à l'échelle globale.

[^1]: Change this to the name of the jar
