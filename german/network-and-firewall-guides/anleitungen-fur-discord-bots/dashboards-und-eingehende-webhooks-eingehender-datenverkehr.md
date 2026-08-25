# Dashboards und eingehende Webhooks (eingehender Datenverkehr)

Einige unserer Bots verwenden nur ausgehende Verbindungen. Dein Bot benötigt eine eingehende Netzwerkkonfiguration, wenn er eine der folgenden Funktionen enthält:

1. **Web-Dashboard:** Ein Bedienfeld, meist mit Express.js oder Flask. Nutzer melden sich im Browser an und konfigurieren den Bot.
2. **Voting-Webhooks:** Der Bot empfängt Echtzeit-POST-Anfragen von Botlisten wie Top.gg. Sie werden ausgelöst, wenn Nutzer für deinen Bot abstimmen.

Eingehenden Datenverkehr konfigurieren: Wenn dein Bot einen Webserver bereitstellt, _musst_ du eingehende Ports auf dem Host öffnen. So können Nutzer und Webhooks ihn erreichen.

1. **Eingehende Ports öffnen:** Erlaube Datenverkehr auf dem Port deines Webservers. Beispiele sind `8080` und `3000`.
   * _Linux (UFW):_ `sudo ufw allow 8080/tcp`
2. **Reverse Proxy einrichten (empfohlen):** Gib Nutzern nicht direkt eine IP-Adresse und einen Port, etwa `http://192.168.1.5:8080`. Installiere stattdessen einen Reverse Proxy wie Nginx oder Apache.
   * Konfiguriere Nginx für Standardport 443 (HTTPS). Leite den Datenverkehr intern an den lokalen Bot-Port `8080` weiter.
   * Verwende einen Domainnamen wie `dashboard.yourbot.com` und ein SSL-Zertifikat von Let's Encrypt. So schützt du Nutzerdaten.
