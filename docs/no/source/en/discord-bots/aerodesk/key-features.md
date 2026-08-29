---
icon: circle-star
tags:
  - info
---

# Hovedegenskaper

* Interaktive ticket-paneler: Rull ut stilrene nedtrekksmenyer (`/ticketpanel`) som lar brukere intuitivt velge sin spesifikke supportkategori.
* Dynamisk ruting og kategorier: Videresend spesifikke problemer (f.eks. Fakturering, Generelt) til dedikerte stabsroller med tilpassede velkomstmeldinger for hver kategori.
* Avansert tildeling (Claiming) og kanallåsing: Når et stabmedlem gjør krav på en ticket, fjerner boten automatisk lese- og skrivetilgang for resten av teamet, og låser kanalen eksklusivt for personen som tok saken og autoriserte administratorer.
* Smarte nedkjølingsperioder (Cooldowns) og nivåbaserte grenser: Forhindre ticket-spam med globale nedkjølingsperioder, og belønn VIP-er eller Server Boosters med høyere ticket-grenser ved hjelp av rollebaserte nivåer.
* Automatisk FAQ-deteksjon: Boten overvåker aktivt tickets for forhåndsdefinerte nøkkelord og svarer umiddelbart med automatiserte løsninger, samtidig som den logger utløsermetrikker i bakgrunnen.
* Omfattende analyse: Spor globale metrikker inkludert totalt antall åpnede tickets, lukkede tickets og besvarte FAQ-er. Se sanntidsdata ved hjelp av `/stats`-kommandoen.
* HTML-transkripsjoner og skylagring: Ved stenging (med valgfrie popup-vinduer for begrunnelse av lukking), genererer boten en oversiktlig HTML-transkripsjon, laster den opp til en skjult loggkanal for Discord CDN-hosting, og arkiverer nettadressen i databasen din.
* Vurderinger etter avsluttet sak: Sender automatisk en interaktiv nedtrekksmeny med 1-5 stjerner til brukere via direktemelding (DM) slik at de kan vurdere supportopplevelsen sin.
