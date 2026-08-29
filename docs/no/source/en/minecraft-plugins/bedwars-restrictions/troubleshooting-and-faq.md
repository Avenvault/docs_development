---
icon: question
tags:
  - faq
---

# Feilsøking og ofte stilte spørsmål

Spm: Konsollen min sier "FATAL: Invalid License Key" og pluginet deaktiverer seg selv.

Svar: Dette betyr at RSA-256 skyautentiseringen avviste nøkkelen din.

1. Sjekk `config.yml` for å sikre at det ikke er noen ekstra mellomrom på slutten av nøkkelen din.
2. Bekreft at abonnementet/lisensen din ikke har utløpt i premiumportalen.
3. Sørg for at du bruker nøyaktig det formatet som er oppgitt (f.eks. 1234-5678-9012).
4. Sørg for at du bruker nøyaktig det formatet som er oppgitt (f.eks. 1234-5678-9012).

Spm: Konsollen sier "License Server Unreachable" under oppstart.

Svar: Pluginet krever en aktiv internettilkobling for å bekrefte integriteten sin. Sørg for at verten/maskinen din tillater utgående tilkoblinger på port 443 (HTTPS), og at brannmuren din ikke blokkerer trafikk til autentiseringsserverne våre.

Spm: Spillere kan fortsatt bygge utenfor arenagrensene!

Svar: Først, bekreft at den aktuelle spilleren ikke er en administrator (OP) og ikke har tillatelsesnoden `bwr.bypass`. For det andre, dobbeltsjekk min- og max-koordinatene dine i `config.yml` for å sikre at den matematiske avgrensningsboksen (bounding box) er satt opp riktig (min-verdier skal alltid være lavere enn max-verdier).

Spm: Er dette pluginet kompatibelt med ViaVersion/Geyser?

Svar: Ja! Fordi BedwarsRestrictions håndterer avgrensningsbokser på servernivå, er det 100 % kompatibelt med Bedrock-spillere via Geyser og klienter som bruker andre versjoner via ViaVersion.

**Trenger du ytterligere hjelp?** [**Kontakt oss**](https://plugins.avenvault.com/contact) **med lisensnøkkelen din (for verifisering) eller bli med på vår Discord og verifiser lisensen din for å få støtte!**
