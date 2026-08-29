---
tags:
  - guides
  - minecraft
---

# Proxy-nettverk og IP-videresending (Velocity / BungeeCord)

Servere er nesten alltid en del av et større proxy-nettverk. For å sikre at pluginet vårt identifiserer spillere korrekt og ikke utløser falske positive på grunn av proxy-ruting, må du konfigurere backend-serverne dine til å akseptere videresendt data på riktig måte.

⚙️ Konfigurere Spigot- / Paper-backend-servere

Hvis du bruker BungeeCord eller Waterfall:

1. Åpne `spigot.yml` på backend-spillserveren din.
2.  Finn `bungeecord`-innstillingen og sett den til `true`:

    ```
    settings:
      bungeecord: true
    ```
3. Åpne `server.properties` og sørg for at `online-mode` er satt til `false`.
4. _Viktig:_ Sørg for at proxy-brannmuren din forhindrer spillere i å koble seg direkte til backend-porten.

Hvis du bruker Velocity (modern videresending): Moderne Paper-servere støtter native sikker videresending fra Velocity.

1. Åpne `config/paper-global.yml` på backend-serveren din.
2.  Finn Velocity-konfigurasjonsblokken:

    ```
    proxies:
      velocity-support:
        enabled: true
        online-mode: true
        secret: "YOUR_VELOCITY_SECRET_HERE"
    ```
3. Lim inn hemmeligheten (secret) som ble generert av Velocity-proxyen din i `secret`-feltet.
4. Sørg for at `online-mode` er satt til `false` i `server.properties`.
