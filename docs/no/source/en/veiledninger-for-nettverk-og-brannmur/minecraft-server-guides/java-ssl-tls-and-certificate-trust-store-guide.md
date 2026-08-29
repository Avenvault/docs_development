---
tags:
  - guides
  - minecraft
---

# Veiledning for Java SSL/TLS og sertifikat-tillitslager (Trust Store)

Hvis serverkonsollen din kaster en `javax.net.ssl.SSLHandshakeException` eller `PKIX path building failed`-feil når pluginene våre prøver å laste inn, betyr det at serverens Java Runtime Environment (JRE) ikke stoler på SSL-sertifikatet til lisensieringsserveren vår.

Dette skjer vanligvis på utdaterte Java-versjoner, tilpassede Docker-beholdere eller minimale Linux-distribusjoner som mangler oppdaterte rot-CA-sertifikater.

🛠️ Slik løser du SSL/TLS-feil

#### Løsning 1: Oppdater Java-versjonen din (Anbefalt)

Den enkleste måten å løse sertifikatproblemer på er å oppdatere Java-installasjonen din til den nyeste bygget av din nåværende hovedversjon (f.eks. oppdatere Java 17-installasjonen din til den nyeste mindre utgivelsen). Moderne JDK-er inkluderer oppdaterte rottillitslagre som standard.

* Vi anbefaler å bruke Adoptium (Temurin) eller Amazon Corretto.

#### Løsning 2: Oppdater systemets sertifikater (Linux VPS / Dedikert)

Hvis du administrerer vertsmaskinen, kan du oppdatere systemets rot-sertifikatlager.

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

#### Løsning 3: Importer sertifikatet manuelt (keytool)

Hvis du ikke kan oppdatere Java, må du manuelt importere SSL-sertifikatet til Java sitt `cacerts`-nøkkellager.

1. Last ned rotsertifikatet fra lisensierings-URL-en ved hjelp av en nettleser.
2. Kjør følgende kommando via terminalen (bytt ut banene etter behov):

```
keytool -import -trustcacerts -keystore /path/to/java/lib/security/cacerts -storepass changeit -noprompt -alias bwr-license -file /path/to/downloaded/certificate.crt
```
