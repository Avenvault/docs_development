---
icon: gear
---

# Configuration (config.yml)

Le fichier `config.yml` vous permet de définir vos arènes, de personnaliser les messages affichés aux joueurs et de renseigner votre clé de licence.

#### **Exemple de configuration**

```
# ========================================== #
#     Configuration BedwarsRestrictions      #
# ========================================== #

# ------------------------------------------ #
# Authentification de la licence
# ------------------------------------------ #
license-key: ENTER-YOUR-KEY-HERE

# ------------------------------------------ #
# Optimisation & Système
# ------------------------------------------ #
# Réglez ceci sur false pour désactiver les métriques bStats spécifiquement pour ce plugin.
# Remarque : Les propriétaires de serveurs peuvent également désactiver bStats globalement dans /plugins/bStats/config.yml
metrics: true

# Passez à true pour voir les coordonnées des blocs et les étapes de validation de l'arène dans le chat (OPs uniquement)
debug: false

# ------------------------------------------ #
# Limites de l'arène (Zones)
# ------------------------------------------ #
# Définissez vos zones protégées ici. Les joueurs ne pourront pas placer ou casser de blocs
# EN DEHORS de la zone définie par min-cord et max-cord.
# Le plugin définira automatiquement le monde ainsi que min et max lorsque vous utilisez /bwr set [NOM]
# après avoir sélectionné POS1 et POS2
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

#### **Détail de la configuration :**

* `license-key`: La clé cryptographique liant votre serveur à votre achat. Le plugin interroge le serveur web d'authentification en utilisant cette clé.
* `zones`: Il s'agit de la liste de vos zones protégées. Une zone nécessite un nom de monde et des coordonnées (minimum et maximum). Ces coordonnées créent une boîte 3D invisible. Les joueurs ne peuvent pas placer ou casser de blocs à l'intérieur de cette boîte.
* > ⚠️ Remarque : BedwarsRestrictions effectuera cela automatiquement, mais si vous préférez le faire vous-même, vous êtes tout à fait libre de le faire.
