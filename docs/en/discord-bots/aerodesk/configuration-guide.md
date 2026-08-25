---
icon: gear
---

# Configuration Guide

The bot is entirely driven by a single `config.yml` file. This makes deployment and updates incredibly fast. Below is an example configuration, followed by a breakdown of the core concepts.

#### Example `config.yml`



```
# ========================================== #
#          Bot Core Settings                 #
# ========================================== #

# Your bot token from the Discord Developer Portal.
# NEVER share this with anyone!
botToken: "YOUR_DISCORD_BOT_TOKEN"

# The Discord User ID of the person who owns the bot (You).
# To get this, enable Developer Mode in Discord and right click your profile.
ownerId: "YOUR_USER_ID"

# Discord Users that are managers of the bot
# Seperate multiple User IDs with commas (e.g., "12345, 73517")
managerUserIds

# ------------------------------------------
# Database Settings
# ------------------------------------------
database:
# Which database should the bot use?
# Valid options: "json", "mongodb", "postgres", "mysql"
activeDatabase: "json"
                  
# If using "mongodb", paste your connection URI here.
mongoUri: "mongodb://localhost:27017"
                  
# If using an SQL database ("postgres" or "mysql"), fill these out.
sqlHost: "localhost"
sqlUser: "root"
sqlPassword: "password123"

# ========================================== #
#          Global Ticket Settings            #
# ========================================== #
tickets:
  maxTicketsPerUser: 1
  ticketCooldownSeconds: 300
  logsChannelId: "102938475610293847"
  staffRoleId: "888888888888888888" # Fallback/General staff role

# ========================================== #
#          Category Configuration            #
# ========================================== #
categories:
  general:
    embedTitle: "General Support"
    welcomeMessage: "Welcome! Please describe your issue. A staff member will be with you shortly."
    staffRoleId: "888888888888888888"
    bypassRoleId: "999999999999999999" # Admin/Management role
    enableClaimRemoval: true
  billing:
    embedTitle: "Billing & Purchases"
    welcomeMessage: "Please provide your Transaction ID and Tebex email."
    staffRoleId: "777777777777777777" # Dedicated billing team
    bypassRoleId: "999999999999999999"
    enableClaimRemoval: true

# ========================================== #
#          VIP Tiers & Limits                #
# ========================================== #
ticketTiers:
  booster:
    roleId: "444444444444444444"
    priority: 1
    maxTickets: 3

# ========================================== #
#          Automated FAQ Responses           #
# ========================================== #
keywordFaqs:
  "forgot password": "To reset your password, please visit our website and click 'Forgot Password' on the login screen."
  "apply for staff": "Staff applications are currently open! Check out the #announcements channel for the application link."
```

#### Understanding Category Settings

The `categories` section is the heart of your routing system. While most settings are self-explanatory, here are the two most critical configurations for your staff workflow:

* `bypassRoleId`: This is the role ID (usually Management or Server Admins) that overrides all ticket permissions. Even if a ticket is claimed and locked to a specific staff member, users with the `bypassRoleId` will always retain view and chat access to oversee the interaction.
* `enableClaimRemoval`: Accepts `true` or `false`.
  * If set to `true` (Lockdown Mode): When a staff member clicks the "Claim" button, the bot removes the general `staffRoleId`'s access to the channel. Only the user, the claiming staff member, and the `bypassRoleId` can see the ticket. This is excellent for privacy and preventing staff members from talking over one another.
  * If set to `false`: Claiming a ticket simply assigns the staff member's name to the embed and database, but all other staff members can still read and reply to the channel.
