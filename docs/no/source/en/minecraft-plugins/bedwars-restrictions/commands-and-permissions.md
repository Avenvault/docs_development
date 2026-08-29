---
icon: terminal
tags:
  - commands
---

# Kommandoer og tillatelser

Bedwars Restrictions er utviklet for å kjøre automatisk i bakgrunnen, men inkluderer noen få administrative kommandoer for løpende administrasjon.

| **Kommando**         | **Beskrivelse**                                                                                     | **Tillatelse** |
| -------------------- | --------------------------------------------------------------------------------------------------- | -------------- |
| `/bwr help`          | Viser hjelpemenyen for administratorer.                                                             | `bwr.admin`    |
| `/bwr reload`        | Laster inn `config.yml` (sonekoordinater) på nytt uten å starte serveren på nytt.                   | `bwr.admin`    |
| `/bwr wand`          | Gir en tryllestav for valg av område.                                                               | `bwr.admin`    |
| `/bwr set base-name` | Lagrer gjeldende utvalg til konfigurasjonen og hindrer plassering eller ødeleggelse innenfor sonen. | `bwr.admin`    |

(Merk: Spillere med Server OP-status arver automatisk alle rettigheter)
