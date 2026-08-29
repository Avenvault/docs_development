---
tags:
  - guides
  - discord
---

# Kjerneforbindelsen (utgående trafikk)

For at en Discord-bot skal komme online, sende meldinger og motta gateway-hendelser, må vertsmaskinen ha tillatelse til å gjøre utgående tilkoblinger til internett.

Trenger boten din port-videresending? Nei. Standard Discord-boter krever ikke innkommende port-videresending.

Hva du må tillate: Brannmuren til din VPS, beholder eller vertsmaskin må tillate utgående TCP-trafikk på port 443 (HTTPS) og port 80 (HTTP).

Hvis verten din blokkerer utgående trafikk strengt (vanlig på strenge bedriftsnettverk eller skoleverk), vil boten mislykkes i å starte og kaste en av følgende feilmeldinger:

* `java.net.UnknownHostException` (Java)
* `Error: getaddrinfo ENOTFOUND discord.com` (Node.js)
* WebSocket-tilkobling avvist

Slik fikser du det: Sørg for at vertsbrannmuren din (som UFW eller Windows Defender) tillater utgående trafikk. På de fleste standard Linux VPS-leverandører (Ubuntu, Debian) er utgående trafikk åpen som standard. Usikker? Sjekk dokumentet for det [her](../allowing-port-443.md)!
