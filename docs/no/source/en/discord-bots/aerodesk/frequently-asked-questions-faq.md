---
icon: question
tags:
  - faq
---

# Ofte stilte spørsmål (FAQ)

Her er de vanligste problemene serveradministratorer støter på, og hvordan de kan løses.

Oppsett og konfigurasjon

Spørsmål: Hvordan finner jeg rolle-ID-er og kanal-ID-er for konfigurasjonen? Svar: Du må aktivere Utviklermodus (Developer Mode) i Discord.

* Gå til Discord-innstillinger > Avansert (Advanced) > Slå på Utviklermodus (Developer Mode).
* Høyreklikk på en hvilken som helst rolle, kanal eller bruker, og klikk på «Kopier kanal-ID» (Copy Channel ID) eller «Kopier rolle-ID» (Copy Role ID) nederst på menyen.

Spørsmål: Jeg inviterte boten, men jeg ser ikke `/ticketpanel` eller `/stats`? Svar: Slash-kommandoer krever spesifikke omfang (scopes) for å registrere seg.

* Sørg for at du inviterte boten med `applications.commands`-omfanget krysset av i OAuth2 URL Generator.
* Spark ut boten og inviter den på nytt med riktig URL. _Merk:_ Du kan prøve å trykke på F5, men globale slash-kommandoer kan noen ganger ta opptil en time å synkronisere på tvers av alle Discord-servere naturlig, selv om de vanligvis dukker opp umiddelbart.

🛠️ Funksjonalitet og feil

Spørsmål: Boten kaster en `MongoTimeoutException` i konsollen og krasjer. Svar: Dette betyr at boten ikke når MongoDB-databasen din.

* Sjekk `config.yml` for å sikre at `database.uri` er formatert riktig.
* Hvis du bruker MongoDB Atlas (skybasert), må du sørge for at du har hvitelistet serverens IP-adresse (eller satt den til `0.0.0.0/0` for å tillate alle IP-er) under _Network Access_-fanen.

Spørsmål: Når et stabmedlem tar en sak (claim), låses ikke kanalen! Svar: Dette skyldes nesten alltid et problem med Discord-rollehierarki eller tillatelser.

* Sørg for at `enableClaimRemoval: true` er satt i konfigurasjonen for den spesifikke kategorien.
* Sørg for at botens høyeste rolle er plassert over stabsrollene i serverinnstillingene dine på Discord. Boten kan ikke fjerne tillatelser fra roller som er høyere enn dens egen.
* Sørg for at boten har tillatelsene _Manage Channels_ (Administrer kanaler) og _Manage Roles_ (Administrer roller), selv om _Administrator_-tillatelse anbefales.

Spørsmål: Hvorfor genererer ikke HTML-transkripsjonene en lenke? Svar: Boten laster opp den genererte HTML-filen direkte til Discords CDN via `logsChannelId` som er spesifisert i konfigurasjonen din. Hvis boten ikke har tillatelse til å legge ved filer (_Attach Files_) eller sende meldinger (_Send Messages_) i den spesifikke skjulte loggkanalen, vil opplastingen mislykkes, og ingen lenke kan genereres. Sjekk kanaltillatelsene!
