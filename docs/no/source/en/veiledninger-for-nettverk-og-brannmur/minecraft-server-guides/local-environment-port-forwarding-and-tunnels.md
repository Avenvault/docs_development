---
tags:
  - guides
  - minecraft
---

# Lokal portvideresending og tunneler

Hvis du er utvikler eller servereier som tester pluginene våre på et lokalt hjemmenettverk før du ruller ut til en offentlig vert, kan det hende du må eksponere serveren din for internett for å verifisere spilling med venner.

#### Alternativ A: Port-videresending i ruter (Router Port Forwarding)

1. Logg inn på ruterens administrasjonspanel (vanligvis `192.168.1.1` eller `10.0.0.1`).
2. Finn avdelingen for Port Forwarding eller Virtual Servers.
3. Opprett en ny regel som peker til datamaskinens lokale IPv4-adresse.
4. Sett både intern og ekstern port til `25565` (eller hvilken port serveren din kjører på).
5. Sett protokollen til TCP/UDP.
6. Lagre og aktiver. Spillere kan nå koble til ved hjelp av din offentlige IP-adresse.

#### Alternativ B: Tunneleringstjenester (Ingen port-videresending kreves)

Hvis du ikke har tilgang til ruteren din eller internettleverandøren din bruker _Carrier-Grade NAT (CGNAT)_, kan du bruke tunneleringstjenester for å eksponere din lokale server.

* Playit.gg: En gratis global proxy som er spesielt designet for gaming. Last ned agenten, kjør den sammen med serveren din, og den gir automatisk en offentlig IP og port.
* Ngrok: Et generelt verktøy for tunnelering.

```
ngrok tcp 25565
```

_(Merk: Ngroks gratisversjon tildeler en tilfeldig port hver gang du starter den på nytt.)_
