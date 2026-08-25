# Proxy-Netzwerk und IP-Weiterleitung (Velocity / BungeeCord)

Server sind fast immer Teil eines größeren Proxy-Netzwerks. Konfiguriere deine Backend-Server für den Empfang weitergeleiteter Daten. So erkennen unsere Plugins Spieler korrekt und vermeiden Fehlalarme durch das Proxy-Routing.

### ⚙️ Spigot-/Paper-Backend-Server konfigurieren

#### Bei Verwendung von BungeeCord oder Waterfall

1. Öffne `spigot.yml` auf deinem Backend-Spielserver.
2.  Suche die Einstellung `bungeecord` und setze sie auf `true`:

    YAML

    ```
    settings:
      bungeecord: true
    ```
3. Öffne `server.properties` und stelle sicher, dass `online-mode` auf `false` gesetzt ist.
4. **Wichtig:** Die Proxy-Firewall muss direkte Verbindungen zum Backend-Port verhindern.

#### Bei Verwendung von Velocity (Modern Forwarding)

Moderne Paper-Server unterstützen Velocitys sichere Weiterleitung nativ.

1. Öffne `config/paper-global.yml` auf deinem Backend-Server.
2.  Suche den Velocity-Konfigurationsblock:

    YAML

    ```
    proxies:
      velocity-support:
        enabled: true
        online-mode: true
        secret: "YOUR_VELOCITY_SECRET_HERE"
    ```
3. Füge das von deinem Velocity-Proxy erzeugte Secret in das Feld `secret` ein.
4. Stelle sicher, dass `online-mode` in `server.properties` auf `false` gesetzt ist.
