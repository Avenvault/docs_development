---
icon: desktop-arrow-down
tags:
  - guides
---

# Installasjonsveiledning

Det er raskt og enkelt å sette opp Bedwars Restrictions i nettverket ditt. Sørg for at du har lisensnøkkelen fra kjøpet klar før du begynner.

1. Last ned pluginen: Last ned den nyeste `BedwarsRestrictions.jar` fra leverandøren din.
2. Last opp til serveren: Dra og slipp `.jar`-filen inn i serverens `/plugins/`-mappe.
3. Første oppstart (generering av filer): Start eller start serveren på nytt. Plugin-modulen vil generere en standard `config.yml` i `/plugins/BedwarsRestrictions/` og deretter deaktivere seg selv midlertidig (dette er normalt).
4. Angi lisensnøkkel: Åpne den genererte `config.yml`-filen og lim inn den kjøpte lisensnøkkelen i feltet for `license-key`.
5. Siste omstart: Start serveren på nytt!

> ⚠️ Merk: BedwarsRestrictions vil ikke laste inn uten en gyldig lisensnøkkel. Innlasting på nytt via Plugman eller /reload støttes ikke for den første autentiseringen. Vennligst utfør en full omstart av serveren.
