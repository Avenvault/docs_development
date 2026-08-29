---
icon: gear
tags:
  - guides
---

# Konfigurasjonsguiden

Boten drives utelukkende av én enkelt `config.yml`-fil. Dette gjør utrulling og oppdateringer utrolig raskt. Nedenfor er et eksempel på en konfigurasjon, etterfulgt av en gjennomgang av kjernekonseptene.

### Eksempel på `config.yml`

```
# ========================================== #
#          Kjerneinnstillinger for Bot       #
# ========================================== #

# Din bot token fra Discord Developer Portal.
# ALDRI del denne med noen!
botToken: "YOUR_DISCORD_BOT_TOKEN"

# Discord bruker-ID-en til personen som eier boten (deg).
# For å finne denne, aktiver Utviklermodus (Developer Mode) i Discord og høyreklikk på profilen din.
ownerId: "YOUR_USER_ID"

# Discord-brukere som er ledere/administratorer for boten
# Separer flere bruker-ID-er med komma (f.eks. "12345, 73517")
managerUserIds: ""

# ------------------------------------------
# Databaseinnstillinger
# ------------------------------------------
database:
# Hvilken database skal boten bruke?
# Gyldige alternativer: "json", "mongodb", "postgres", "mysql"
activeDatabase: "json"
                  
# Hvis du bruker "mongodb", lim inn tilkoblings-URI-en din her.
mongoUri: "mongodb://localhost:27017"
                  
# Hvis du bruker en SQL-database ("postgres" eller "mysql"), fyll ut disse.
sqlHost: "localhost"
sqlUser: "root"
sqlPassword: "password123"

# ========================================== #
#          Globale Ticket-innstillinger      #
# ========================================== #
tickets:
  maxTicketsPerUser: 1
  ticketCooldownSeconds: 300
  logsChannelId: "102938475610293847"
  staffRoleId: "888888888888888888" # Standard / Generell stabsrolle

# ========================================== #
#          Kategorikonfigurasjon             #
# ========================================== #
categories:
  general:
    embedTitle: "Generell Support"
    welcomeMessage: "Velkommen! Vennligst beskriv problemet ditt. En medarbeider vil hjelpe deg om kort tid."
    staffRoleId: "888888888888888888"
    bypassRoleId: "999999999999999999" # Admin-/Lederrolle
    enableClaimRemoval: true
  billing:
    embedTitle: "Fakturering og Kjøp"
    welcomeMessage: "Vennligst oppgi transaksjons-ID-en din og e-postadressen for Tebex."
    staffRoleId: "777777777777777777" # Dedikert faktureringsteam
    bypassRoleId: "999999999999999999"
    enableClaimRemoval: true

# ========================================== #
#          VIP-nivåer og Grenser             #
# ========================================== #
ticketTiers:
  booster:
    roleId: "444444444444444444"
    priority: 1
    maxTickets: 3

# ========================================== #
#          Automatiske FAQ-svar              #
# ========================================== #
keywordFaqs:
  "glemt passord": "For å tilbakestille passordet ditt, besøk nettsiden vår og klikk på 'Glemt Passord' på innloggingsskjermen."
  "søke om stab": "Stabssøknader er for tiden åpne! Sjekk ut #kunngjøringer-kanalen for lenke til søknaden."
```

### Forstå Kategoriinnstillingene

Kategori-delen er hjertet i ruting-systemet ditt. Selv om de fleste innstillingene er selvforklarende, er her de to mest kritiske konfigurasjonene for arbeidsflyten til staben din:

* bypassRoleId: Dette er rolle-ID-en (vanligvis ledelse eller serveradministratorer) som overstyrer alle ticket-tillatelser. Selv om en sak er gjort krav på og låst til et bestemt stabmedlem, vil brukere med `bypassRoleId` alltid beholde lese- og skrivetilgang for å kunne overvåke interaksjonen.
* enableClaimRemoval: Godtar `true` eller `false`.
  * _Hvis satt til `true` (Låsemodus):_ Når et stabmedlem klikker på "Claim"-knappen, fjerner boten den generelle `staffRoleId` sin tilgang til kanalen. Bare brukeren, stabmedlemmet som tok saken, og `bypassRoleId` kan se ticketen. Dette er utmerket for personvern og for å forhindre at stabmedlemmer snakker i munnen på hverandre.
  * _Hvis satt til `false`:_ Å gjøre krav på en ticket tildeler bare stabmedlemmets navn til informasjonsboksen (embed) og databasen, men alle andre stabmedlemmer kan fortsatt lese og svare i kanalen.
