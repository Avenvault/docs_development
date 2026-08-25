---
icon: gear
---

# Konfiguration (config.yml)

In der `config.yml` definierst du deine Arenen, passt Spielernachrichten an und gibst deinen Lizenzschlüssel ein.

#### **Beispielkonfiguration**

```
# ========================================== #
#      BedwarsRestrictions Konfiguration    #
# ========================================== #

# ------------------------------------------ #
# Lizenz-Authentifizierung
# ------------------------------------------ #
license-key: ENTER-YOUR-KEY-HERE

# ------------------------------------------ #
# Optimierung & System
# ------------------------------------------ #
# Setze dies auf false, um bStats-Metriken speziell für dieses Plugin zu deaktivieren.
# Hinweis: Serverbesitzer können bStats auch global in /plugins/bStats/config.yml deaktivieren.
metrics: true

# Auf true setzen, um Block-Koordinaten und Arena-Validierungsschritte im Chat zu sehen (nur für OPs)
debug: false

# ------------------------------------------ #
# Arena-Begrenzungen (Zonen)
# ------------------------------------------ #
# Definiere hier deine geschützten Bereiche. Spieler können keine Blöcke AUßERHALB des
# Bereichs platzieren/abgeben, der durch min-cord und max-cord definiert ist.
# Das Plugin setzt automatisch die Welt sowie min und max, wenn du /bwr set [NAME]
# nach dem Auswählen von POS1 und POS2 verwendest.
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

#### **Aufschlüsselung der Konfiguration:**

* `license-key`: Der kryptografische Schlüssel, der deinen Server mit deinem Kauf verknüpft. Das Plugin fragt den Authentifizierungsserver mit diesem Schlüssel ab.
* `zones`: Dies ist eine Liste deiner geschützten Zonen. Eine Zone erfordert einen Weltnamen und Koordinaten (Minimum und Maximum). Diese Koordinaten erstellen einen unsichtbaren 3D-Kasten. Spieler können innerhalb dieses Kastens keine Blöcke platzieren oder abbauen.
* > ⚠️ Hinweis: BedwarsRestrictions erledigt dies automatisch, aber wenn du es selbst tun möchtest, kannst du das natürlich gerne machen.
