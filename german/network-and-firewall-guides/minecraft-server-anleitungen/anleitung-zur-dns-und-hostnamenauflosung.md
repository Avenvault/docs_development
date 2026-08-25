# Anleitung zur DNS- und Hostnamenauflösung

Wenn unsere Plugins beim Start `java.net.UnknownHostException` in der Konsole anzeigen, kann dein Server den Domainnamen unseres Lizenzservers nicht in eine IP-Adresse auflösen.

Die Ursache liegt in der DNS-Resolver-Konfiguration deines Hosts.

### Probleme bei der DNS-Auflösung beheben

#### DNS-Resolver ändern (Linux)

Du kannst deinen Server zur Verwendung öffentlicher, zuverlässiger DNS-Resolver zwingen. Beispiele sind Cloudflare (`1.1.1.1`) und Google (`8.8.8.8`).

1.  Öffne die Datei `resolv.conf`:

    ```
    sudo nano /etc/resolv.conf
    ```
2.  Füge diese Zeilen ganz oben in der Datei ein:

    ```
    nameserver 1.1.1.1
    nameserver 8.8.8.8
    ```
3. Speichere und schließe die Datei (`Strg+O`, `Enter`, `Strg+X`). Starte deinen Minecraft-Server neu.

#### DNS-Resolver ändern (Windows Server)

1. Öffne **Systemsteuerung** → **Netzwerk und Internet** → **Netzwerk- und Freigabecenter**.
2. Klicke auf deine aktive Verbindung und wähle **Eigenschaften**.
3. Wähle **Internetprotokoll, Version 4 (TCP/IPv4)** und klicke auf **Eigenschaften**.
4. Aktiviere **Folgende DNS-Serveradressen verwenden** und gib Folgendes ein:
   * Bevorzugter DNS-Server: `1.1.1.1`
   * Alternativer DNS-Server: `8.8.8.8`
5. Klicke auf **OK** und starte deinen Minecraft-Server neu.
