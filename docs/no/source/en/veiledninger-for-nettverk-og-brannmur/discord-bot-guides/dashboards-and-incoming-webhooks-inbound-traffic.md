---
tags:
  - guides
  - discord
---

# Dashbord og innkommende webhooks (innkommende trafikk)

Mens noen av botene våre bare bruker utgående tilkoblinger, krever boten din innkommende nettverkskonfigurasjon hvis den inkluderer en av følgende funksjoner:

* Et nettbasert kontrollpanel (Web Dashboard): Et kontrollpanel (som vanligvis kjører på Express.js eller Flask) der brukere logger inn via en nettleser for avstemming eller for å konfigurere boten.
* Avstemmingswebhooks (Voting Webhooks): Mottak av sanntids POST-forespørsler fra nettsider med bot-lister (som Top.gg) når en bruker stemmer opp boten din.

#### Slik konfigurerer du innkommende trafikk

Hvis boten din er vert for en webserver, må du åpne innkommende porter på vertsmaskinen din for at brukere og webhooks skal nå den.

* Åpne innkommende porter: Tillat trafikk på porten webserveren din bruker (f.eks. `8080` eller `3000`).
  * _Linux (UFW):_ `sudo ufw allow 8080/tcp`
* Sett opp en omvendt proxy (Reverse Proxy - Anbefalt): I stedet for å gi brukere en IP-adresse og port (f.eks. `[http://192.168.1.5:8080](http://192.168.1.5:8080)`), bør du installere en omvendt proxy som Nginx eller Apache.
  * Konfigurer Nginx til å lytte på standard port `443` (HTTPS) og rute trafikken internt til botens lokale port (`8080`).
  * Dette lar deg knytte et domenenavn (`dashboard.dinbot.no`) og et SSL-sertifikat (via Let's Encrypt) til for å holde brukerdata sikre.
