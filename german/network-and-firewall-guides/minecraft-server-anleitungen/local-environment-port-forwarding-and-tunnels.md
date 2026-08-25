# Local Environment Port Forwarding & Tunnels

Wenn du als Entwickler oder Serverbesitzer unsere Plugins vor der Bereitstellung auf einem öffentlichen Host im lokalen Heimnetz testest, musst du deinen Server möglicherweise im Internet freigeben. So kannst du das Gameplay mit Freunden testen.

### Option A: Portweiterleitung im Router

1. Melde dich im Adminbereich deines Routers an. Typische Adressen sind `192.168.1.1` oder `10.0.0.1`.
2. Suche nach **Portweiterleitung** oder **Virtuelle Server**.
3. Erstelle eine neue Regel für die lokale IPv4-Adresse deines Computers.
4. Setze **Interner Port** und **Externer Port** auf `25565`. Verwende den Port deines Servers, falls er abweicht.
5. Setze das Protokoll auf TCP/UDP.
6. Speichere und übernimm die Änderung. Spieler können sich jetzt über deine öffentliche IP-Adresse verbinden.

### Option B: Tunneling-Dienste (keine Portweiterleitung erforderlich)

Wenn du nicht auf deinen Router zugreifen kannst oder dein Internetanbieter Carrier-Grade NAT (CGNAT) verwendet, kannst du deinen lokalen Server über Tunneling-Dienste freigeben.

* [Playit.gg](https://playit.gg): Ein kostenloser, globaler Proxy für Gaming. Lade den Agenten herunter und führe ihn neben deinem Server aus. Er stellt automatisch eine öffentliche IP-Adresse und einen Port bereit.
* [Ngrok](https://ngrok.com/): Ein allgemeines Tunneling-Tool.

```
ngrok tcp 25565
```

_(Hinweis: Der kostenlose Tarif von Ngrok weist bei jedem Neustart einen zufälligen Port zu.)_
