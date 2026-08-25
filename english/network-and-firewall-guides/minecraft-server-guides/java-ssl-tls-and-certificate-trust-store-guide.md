# Java SSL/TLS & Certificate Trust Store Guide

If your server console is throwing a `javax.net.ssl.SSLHandshakeException` or `PKIX path building failed` error when our plugins attempts to load, it means your server's Java Runtime Environment (JRE) does not trust the SSL certificate of our licensing server.

This typically happens on outdated Java versions, customized Docker containers, or minimal Linux distributions missing up-to-date Root CA certificates.

### 🛠️ How to Fix SSL/TLS Errors

#### Solution 1: Update Your Java Version (Recommended)

The easiest way to resolve certificate issues is to update your Java installation to the latest build of your current major version (e.g., updating your Java 17 installation to the latest minor release). Modern JDKs include updated root trust stores by default.

* We recommend using Adoptium (Temurin) or Amazon Corretto.

#### Solution 2: Update System Certificates (Linux VPS/Dedicated)

If you are managing the host machine, you can update the system's root certificate store.

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

#### Solution 3: Manually Import the Certificate (`keytool`)

If you cannot update Java, you must manually import the SSL certificate into your Java `cacerts` keystore.

1. Download the root certificate from the licensing URL using a web browser.
2. Run the following command via terminal (replace paths appropriately):

```
keytool -import -trustcacerts -keystore /path/to/java/lib/security/cacerts -storepass changeit -noprompt -alias bwr-license -file /path/to/downloaded/certificate.crt
```

