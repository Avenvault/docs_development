---
tags:
  - guides
  - minecraft
---

# Veiledning for DNS og vertsnavnoppslag

Hvis serverkonsollen din viser en `java.net.UnknownHostException` under oppstart, klarer ikke serveren din å oversette domenenavnet til lisensserveren vår til en IP-adresse.

Dette er et problem med vertens DNS-oppløserkonfigurasjon.

### Slik løser du DNS-oppløsningsproblemer

#### Endre DNS-oppløsere (Linux)

Du kan tvinge serveren din til å bruke pålitelige, offentlige DNS-oppløsere som Cloudflare (`1.1.1.1`) eller Google (`8.8.8.8`).

1.  Åpne `resolv.conf`-filen din:

    ```
    sudo nano /etc/resolv.conf
    ```
2.  Legg til følgende linjer helt øverst i filen:

    ```
    nameserver 1.1.1.1
    nameserver 8.8.8.8
    ```
3. Lagre og avslutt (`Ctrl+O`, `Enter`, `Ctrl+X`). Start Minecraft-serveren på nytt.

#### Endre DNS-oppløsere (Windows Server)

1. Åpne Kontrollpanel (Control Panel) > Nettverk og internett (Network and Internet) > Nettverks- og delingssenter (Network and Sharing Center).
2. Klikk på din aktive tilkobling og velg Egenskaper (Properties).
3. Velg Internet Protocol Version 4 (TCP/IPv4) og klikk Egenskaper.
4. Kryss av for Bruk følgende DNS-serveradresser (Use the following DNS server addresses) og skriv inn:
   * Foretrukket DNS-server: `1.1.1.1`
   * Alternativ DNS-server: `8.8.8.8`
5. Klikk OK og start Minecraft-serveren på nytt.
