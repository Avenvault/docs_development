---
icon: gear
tags:
  - guides
---

# Konfigurasjon (config.yml)

I `config.yml` definerer du arenaene dine, tilpasser spillermeldinger og legger inn lisensnøkkelen din.

### **Eksempelkonfigurasjon**

```
# ========================================== #
#      BedwarsRestrictions Konfigurasjon     #
# ========================================== #

# ------------------------------------------ #
# Lisensautentisering
# ------------------------------------------ #
license-key: ENTER-YOUR-KEY-HERE

# ------------------------------------------ #
# Optimalisering & System
# ------------------------------------------ #
# Sett denne til false for å deaktivere bStats-målinger spesifikt for dette pluginet.
# Merk: Servereiere kan også deaktivere bStats globalt i /plugins/bStats/config.yml
metrics: true

# Bytt til true for å se blokkoordinater og arena-valideringstrinn i chatten (kun for OP)
debug: false

# ------------------------------------------ #
# Arenagrenser (Soner)
# ------------------------------------------ #
# Definer de beskyttede områdene dine her. Spillere vil ikke kunne plassere/ødelegge blokker
# UTENFOR området definert av min-cord og max-cord.
# Pluginet vil automatisk sette verdenen og sette min, max når du bruker /bwr set [NAME]
# etter å ha valgt POS1 og POS2
zones:
  hypixel_map:
    green_base:
      min: [-200, 64, 45]
      max: [-175, 90, 70]
    yellow_base:
      min: [-150, 124, 100]
      max: [-90, 158, 140]
  hypixel_map_2:
    red_base:
      min: [-12, 91, 72]
      max: [-1, 12, 50]
    custom_base_1:
      min: [100, 89, 81]
      max: [150, 134, 101]
```

Gjennomgang av konfigurasjon

* `license-key`: Den kryptografiske nøkkelen som knytter serveren din til kjøpet ditt. Pluginet gjør en forespørsel til autentiseringsserveren på nettet ved hjelp av denne nøkkelen.
* `zones`: Dette er en liste over de beskyttede sonene dine. En sone krever et verdensnavn og koordinater (minimum og maksimum). Disse koordinatene skaper en usynlig 3D-boks. Spillere kan ikke plassere eller ødelegge blokker inne i denne boksen.
* > ⚠️ Merk: BedwarsRestrictions vil gjøre dette automatisk, men hvis du ønsker å gjøre det selv, er du hjertelig velkommen til det.
