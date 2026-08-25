# Guide Java SSL/TLS et magasin de certificats de confiance

Si la console de votre serveur affiche une erreur `javax.net.ssl.SSLHandshakeException` ou `PKIX path building failed` lorsque nos plugins tentent de se charger, cela signifie que l'environnement d'exécution Java (JRE) de votre serveur ne fait pas confiance au certificat SSL de notre serveur de licence.

Cela se produit généralement sur des versions obsolètes de Java, des conteneurs Docker personnalisés ou des distributions Linux minimales ne disposant pas de certificats racines (Root CA) à jour.

#### 🛠️ Comment résoudre les erreurs SSL/TLS

**Solution 1 : Mettre à jour votre version de Java (Recommandé)**

Le moyen le plus simple de résoudre les problèmes de certificat est de mettre à jour votre installation Java vers la dernière version de votre branche principale (par exemple, mettre à jour votre installation de Java 17 vers la dernière mise à jour mineure). Les JDK modernes incluent par défaut des magasins de certificats racines à jour.

* Nous vous recommandons d'utiliser Adoptium (Temurin) ou Amazon Corretto.

**Solution 2 : Mettre à jour les certificats du système (Linux VPS/Dédié)**

Si vous gérez la machine hôte, vous pouvez mettre à jour le magasin de certificats racines du système.

Ubuntu / Debian :

```
sudo apt-get update
sudo apt-get install --reinstall ca-certificates
sudo update-ca-certificates
```

CentOS / RHEL / AlmaLinux :

```
sudo yum install ca-certificates
sudo update-ca-trust force-enable
sudo update-ca-trust extract
```

**Solution 3 : Importer manuellement le certificat (`keytool`)**

Si vous ne pouvez pas mettre à jour Java, vous devez importer manuellement le certificat SSL dans le magasin de clés `cacerts` de votre installation Java.

1. Téléchargez le certificat racine depuis l'URL de licence à l'aide d'un navigateur web.
2. Exécutez la commande suivante dans votre terminal (remplacez les chemins de manière appropriée) :

```
keytool -import -trustcacerts -keystore /chemin/vers/java/lib/security/cacerts -storepass changeit -noprompt -alias bwr-license -file /chemin/vers/certificat/telecharge.crt
```
