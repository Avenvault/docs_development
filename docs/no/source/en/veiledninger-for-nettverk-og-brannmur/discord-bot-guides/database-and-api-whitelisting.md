---
tags:
  - guides
  - discord
---

# Hvitelisting for database og API

Nesten alle moderne Discord-boter er avhengige av en ekstern database (MongoDB, MySQL, PostgreSQL) for å lagre brukerdata, eller de henter data fra eksterne API-er (som YouTube, Spotify eller OpenAI).

Hvis databasen din er hostet på en annen maskin enn boten din (f.eks. MongoDB Atlas eller en administrert AWS-database), må du hvitliste botens IP-adresse.

Slik konfigurerer du tilgang til ekstern database:

* Finn den offentlige IPv4-adressen til maskinen som hoster Discord-boten din.
* Logg inn på dashbordet til databaseleverandøren din (f.eks. MongoDB Atlas, AWS RDS).
* Naviger til nettverkstilgang (Network Access) eller sikkerhetsgrupper (Security Groups).
* Legg til en innkommende regel (inbound rule) som tillater tilkoblinger fra botens spesifikke IP-adresse.
* _Merk for dynamiske IP-er:_ Hvis du hoster boten på et hjemmenettverk der IP-adressen endrer seg ofte, må du kanskje tillate tilkoblinger fra hvor som helst (`0.0.0.0/0`), selv om dette krever sterke databasepassord for sikkerhet – det anbefales å følge databaseleverandørens grenser for passord og sørge for å lagre dette i et notat i BitWarden eller en passordbehandler!
