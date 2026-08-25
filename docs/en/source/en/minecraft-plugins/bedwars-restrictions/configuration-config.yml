---
icon: gear
---

# Configuration (config.yml)

The `config.yml` is where you define your arenas, customize player messages, and input your license key.

#### Example Configuration

```
# ========================================== #
#      BedwarsRestrictions Configuration     #
# ========================================== #

# ------------------------------------------ #
# License Authentication
# ------------------------------------------ #
license-key: ENTER-YOUR-KEY-HERE

# ------------------------------------------ #
# Optimization & System
# ------------------------------------------ #
# Set this to false to disable bStats metrics specifically for this plugin.
# Note: Server owners can also disable bStats globally in /plugins/bStats/config.yml
metrics: true

# Toggle to true to see block coordinates and arena validation steps in chat (OPs only)
debug: false

# ------------------------------------------ #
# Arena Boundaries (Zones)
# ------------------------------------------ #
# Define your protected areas here. Players will not be able to place/break blocks
# blocks OUTSIDE the area defined by min-cord and max-cord.
# The plugin will automatically set the world and set min, max when you use /bwr set [NAME]
# after selecting POS1 and POS2
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

#### Configuration Breakdown

- `license-key`: The cryptographic key linking your server to your purchase. The plugin queries the authentication web server using this key.
- `zones`: This is a list of your protected zones. A zone requires a `world` name and coordinates (minimum and maximum). These coordinates create an invisible 3D box. Players cannot place or blocks _inside_ this box.&#x20;

  > ⚠️ Notice: BedwarsRestrictions will automatically do this but if you want to do it yourself you are more than welcome to.
