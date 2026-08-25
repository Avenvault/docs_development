# Die Kernverbindung (ausgehender Datenverkehr)

Damit ein Discord-Bot online gehen, Nachrichten senden und Gateway-Ereignisse empfangen kann, muss der Host ausgehende Internetverbindungen herstellen dürfen.

Benötigt mein Bot eine Portweiterleitung? Nein. Standardmäßige Discord-Bots benötigen keine eingehende Portweiterleitung.

Was du freigeben musst: Die Firewall deines VPS, Containers oder Hosts muss ausgehenden TCP-Datenverkehr auf Port 443 (HTTPS) und Port 80 (HTTP) erlauben.

Wenn dein Host ausgehenden Datenverkehr blockiert, startet der Bot nicht. Das ist oft in Unternehmens- oder Schulnetzwerken der Fall. Dabei tritt einer der folgenden Fehler auf:

* `java.net.UnknownHostException` (Java)
* `Error: getaddrinfo ENOTFOUND discord.com` (Node.js)
* `WebSocket connection refused`

So behebst du das Problem: Stelle sicher, dass die Host-Firewall ausgehenden Datenverkehr erlaubt. Beispiele sind UFW und Windows Defender. Bei den meisten Linux-VPS-Anbietern ist ausgehender Datenverkehr standardmäßig geöffnet. Weitere Informationen findest du [hier](https://plugins.avenvault.com/docs/network-and-firewall-guides/allowing-port-443).
