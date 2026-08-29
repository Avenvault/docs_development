---
icon: desktop-arrow-down
tags:
  - guides
---

# Veiledning for installasjon og distribusjon

Å få Enterprise Ticket System opp og gå på vertsmaskinen din (VPS, dedikert server eller Pterodactyl Panel) er en grei prosess. Følg disse trinnene nøye for å sikre en problemfri utrulling.

📋 Forutsetninger

Før du begynner, må du sørge for at vertsmiljøet ditt har følgende installert:

* Java 17 eller nyere (kreves for moderne JDA-versjoner).
* En databaseløsning (MongoDB-klynge, SQL-database, eller tilgang til lokal lagring for JSON).
* En Discord Bot Token (hentes fra Discord Developer Portal).

Trinn 1: Oppsett av Discord-applikasjon

* Gå til Discord Developer Portal og opprett en ny applikasjon (New Application).
* Naviger til Bot-fanen og klikk på Add Bot.
* Kritisk: Rull ned til Privileged Gateway Intents og aktiver:
  * Server Members Intent (Nødvendig for å sjekke roller).
  * Message Content Intent (Nødvendig for å oppdage nøkkelord for FAQ).
* Lagre endringene dine og kopier Bot Tokenen din. Hold denne hemmelig!
* Inviter boten til serveren din ved å gå til OAuth2 og rulle ned til OAuth2 URL Generator. Sørg for at du krysser av for både `bot` og `applications.commands` (kreves for Slash-kommandoer), kryss av for Administrator under _General Permissions_, og lim inn nettadressen som oppgis under _Generated URL_ i nettleseren din.

Trinn 2: Serverforberedelser

* Opprett en ny mappe på vertsmaskinen din for boten (f.eks. TicketBot).
* Last ned den nyeste utgivelsen (release) og legg den i mappen.
* Kjør boten for første gang for å generere konfigurasjonsfilene:

Bash

<pre><code>java -jar [<a data-footnote-ref href="#user-content-fn-1">NAME</a>].jar
</code></pre>

* Boten vil automatisk slå seg av og informere deg om at filen `config.yml` har blitt generert.

Trinn 3: Konfigurasjon

* Åpne den nylig genererte `config.yml`.
* Lim inn din Bot Token og din personlige Discord Owner ID.
* Konfigurer Database URI (hvis du bruker MongoDB eller SQL).
* Fyll ut dine server-spesifikke innstillinger, inkludert Role IDs, Channel IDs og dine kategori-konfigurasjoner (se [konfigurasjonsguiden](configuration-guide.md) for detaljer).
* Lagre filen.

Trinn 4: Siste oppstart

Start boten på nytt ved hjelp av ditt foretrukne oppstartsskript, screen eller Pterodactyl-panel:

Bash

<pre><code>java -Xms1G -Xmx2G -jar [<a data-footnote-ref href="#user-content-fn-1">NAME</a>].jar
</code></pre>

Hvis konfigurasjonen er riktig, vil konsollen logge en vellykket databasetilkobling og bekrefte at Slash-kommandoene dine har blitt registrert globalt.

[^1]: Endre dette til navnet på jar-filen.
