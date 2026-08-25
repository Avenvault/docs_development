# Anleitung für Java-SSL/TLS und Zertifikats-TrustStore

Wenn die Serverkonsole beim Laden unserer Plugins den Fehler `javax.net.ssl.SSLHandshakeException` oder `PKIX path building failed` ausgibt, vertraut die Java Runtime Environment (JRE) deines Servers dem SSL-Zertifikat unseres Lizenzservers nicht.

Dies tritt meist bei veralteten Java-Versionen, angepassten Docker-Containern oder schlanken Linux-Distributionen ohne aktuelle Root-CA-Zertifikate auf.

### 🛠️ SSL/TLS-Fehler beheben

#### Lösung 1: Java-Version aktualisieren (empfohlen)

Aktualisiere deine Java-Installation auf den neuesten Build deiner aktuellen Hauptversion. Aktualisiere beispielsweise Java 17 auf das neueste Minor Release. Moderne JDKs enthalten standardmäßig aktuelle Root-TrustStores.

* Wir empfehlen Adoptium (Temurin) oder Amazon Corretto.

#### Lösung 2: Systemzertifikate aktualisieren (Linux-VPS/Dedicated Server)

Wenn du den Host verwaltest, kannst du den Root-Zertifikatsspeicher des Systems aktualisieren.

Ubuntu / Debian:

```
sudo apt-get update
sudo apt-get install --reinstall ca-certificates
sudo update-ca-certificates
```

CentOS / RHEL / AlmaLinux:

```
sudo yum install ca-certificates
sudo update-ca-trust force-enable
sudo update-ca-trust extract
```

#### Lösung 3: Zertifikat manuell importieren (`keytool`)

Wenn du Java nicht aktualisieren kannst, musst du das SSL-Zertifikat manuell in deinen Java-Keystore `cacerts` importieren.

1. Lade das Root-Zertifikat über die Lizenz-URL in einem Browser herunter.
2. Führe den folgenden Befehl im Terminal aus. Ersetze die Pfade entsprechend.

Bash

```
keytool -import -trustcacerts -keystore /path/to/java/lib/security/cacerts -storepass changeit -noprompt -alias bwr-license -file /path/to/downloaded/certificate.crt
```
