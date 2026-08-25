---
icon: gear
---

# Configuration Guide

Le bot est entièrement piloté par un seul fichier `config.yml`. Cela rend le déploiement et les mises à jour incroyablement rapides. Vous trouverez ci-dessous un exemple de configuration, suivi d'une explication des concepts clés.

#### Exemple de `config.yml`

```
# ========================================== #
#     Paramètres principaux du bot           #
# ========================================== #

# Votre jeton de bot issu du Discord Developer Portal.
# Ne partagez JAMAIS ce jeton avec quiconque !
botToken: "YOUR_DISCORD_BOT_TOKEN"

# L'identifiant utilisateur Discord du propriétaire du bot (Vous).
# Pour l'obtenir, activez le mode développeur dans Discord et faites un clic droit sur votre profil.
ownerId: "YOUR_USER_ID"

# Utilisateurs Discord qui sont gestionnaires du bot
# Séparez les identifiants multiples par des virgules (ex. "12345, 73517")
managerUserIds

# ------------------------------------------
# Paramètres de la base de données
# ------------------------------------------
database:
# Quelle base de données le bot doit-il utiliser ?
# Options valides : "json", "mongodb", "postgres", "mysql"
activeDatabase: "json"

# Si vous utilisez "mongodb", collez votre URI de connexion ici.
mongoUri: "mongodb://localhost:27017"

# Si vous utilisez une base de données SQL ("postgres" ou "mysql"), remplissez ces champs.
sqlHost: "localhost"
sqlUser: "root"
sqlPassword: "password123"

# ========================================== #
#     Paramètres globaux des tickets         #
# ========================================== #
tickets:
  maxTicketsPerUser: 1
  ticketCooldownSeconds: 300
  logsChannelId: "102938475610293847"
  staffRoleId: "888888888888888888" # Rôle général de l'équipe (par défaut)

# ========================================== #
#     Configuration des catégories           #
# ========================================== #
categories:
  general:
    embedTitle: "General Support"
    welcomeMessage: "Welcome! Please describe your issue. A staff member will be with you shortly."
    staffRoleId: "888888888888888888"
    bypassRoleId: "999999999999999999" # Rôle Admin/Gestion
    enableClaimRemoval: true
  billing:
    embedTitle: "Billing & Purchases"
    welcomeMessage: "Please provide your Transaction ID and Tebex email."
    staffRoleId: "777777777777777777" # Équipe dédiée à la facturation
    bypassRoleId: "999999999999999999"
    enableClaimRemoval: true

# ========================================== #
#     Niveaux VIP & Limites                  #
# ========================================== #
ticketTiers:
  booster:
    roleId: "444444444444444444"
    priority: 1
    maxTickets: 3

# ========================================== #
#     Réponses FAQ automatisées             #
# ========================================== #
keywordFaqs:
  "forgot password": "To reset your password, please visit our website and click 'Forgot Password' on the login screen."
  "apply for staff": "Staff applications are currently open! Check out the #announcements channel for the application link."
```

#### **Comprendre les paramètres de catégorie**

La section `categories` est le cœur de votre système de routage. Bien que la plupart des paramètres soient explicites, voici les deux configurations les plus critiques pour le flux de travail de votre équipe:

* bypassRoleId : Il s'agit de l'identifiant de rôle (généralement la direction ou les administrateurs du serveur) qui outrepasse toutes les permissions des tickets. Même si un ticket est pris en charge et verrouillé pour un membre spécifique de l'équipe, les utilisateurs possédant le `bypassRoleId` conserveront toujours l'accès en lecture et en écriture pour superviser l'interaction.
* enableClaimRemoval : Accepte `true` (vrai) ou `false` (faux).
  * Si réglé sur `true` (Mode Verrouillage) : Lorsqu'un membre de l'équipe clique sur le bouton « Prendre en charge » (Claim), le bot retire l'accès du rôle général `staffRoleId` au salon. Seuls l'utilisateur, le membre de l'équipe ayant pris le ticket et le `bypassRoleId` peuvent voir le ticket. C'est idéal pour la confidentialité et pour éviter que les membres de l'équipe ne se coupent la parole.
  * Si réglé sur `false` : Prendre en charge un ticket attribue simplement le nom du membre de l'équipe à l'embed et à la base de données, mais tous les autres membres de l'équipe peuvent toujours lire le salon et y répondre.
