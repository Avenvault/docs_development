---
icon: gear
---

# Konfigurationshandbuch

Der Bot wird vollständig über eine einzige `config.yml`-Datei gesteuert. Das macht Bereitstellung und Updates extrem schnell. Nachfolgend findest du eine Beispielkonfiguration, gefolgt von einer Aufschlüsselung der wichtigsten Konzepte.

#### Beispiel `config.yml`

```
# ========================================== #
#          Bot-Kerneinstellungen             #
# ========================================== #

# Dein Bot-Token aus dem Discord Developer Portal.
# Teile dies NIEMALS mit irgendwem!
botToken: "YOUR_DISCORD_BOT_TOKEN"

# Die Discord User-ID der Person, der der Bot gehört (Du).
# Um diese zu erhalten, aktiviere den Entwicklermodus in Discord und klicke mit der rechten Maustaste auf dein Profil.
ownerId: "YOUR_USER_ID"

# Discord-Benutzer, die Manager des Bots sind
# Trenne mehrere Benutzer-IDs mit Kommas (z. B. "12345, 73517")
managerUserIds

# ------------------------------------------
# Datenbank-Einstellungen
# ------------------------------------------
database:
# Welche Datenbank soll der Bot verwenden?
# Gültige Optionen: "json", "mongodb", "postgres", "mysql"
activeDatabase: "json"

# Wenn du "mongodb" verwendest, füge hier deine Verbindungs-URI ein.
mongoUri: "mongodb://localhost:27017"

# Wenn du eine SQL-Datenbank ("postgres" oder "mysql") verwendest, fülle diese aus.
sqlHost: "localhost"
sqlUser: "root"
sqlPassword: "password123"

# ========================================== #
#          Globale Ticket-Einstellungen      #
# ========================================== #
tickets:
  maxTicketsPerUser: 1
  ticketCooldownSeconds: 300
  logsChannelId: "102938475610293847"
  staffRoleId: "888888888888888888" # Fallback/Allgemeine Team-Rolle

# ========================================== #
#          Kategorie-Konfiguration           #
# ========================================== #
categories:
  general:
    embedTitle: "General Support"
    welcomeMessage: "Welcome! Please describe your issue. A staff member will be with you shortly."
    staffRoleId: "888888888888888888"
    bypassRoleId: "999999999999999999" # Admin/Management-Rolle
    enableClaimRemoval: true
  billing:
    embedTitle: "Billing & Purchases"
    welcomeMessage: "Please provide your Transaction ID and Tebex email."
    staffRoleId: "777777777777777777" # Dediziertes Abrechnungsteam
    bypassRoleId: "999999999999999999"
    enableClaimRemoval: true

# ========================================== #
#          VIP-Stufen & Limits               #
# ========================================== #
ticketTiers:
  booster:
    roleId: "444444444444444444"
    priority: 1
    maxTickets: 3

# ========================================== #
#          Automatisierte FAQ-Antworten      #
# ========================================== #
keywordFaqs:
  "forgot password": "To reset your password, please visit our website and click 'Forgot Password' on the login screen."
  "apply for staff": "Staff applications are currently open! Check out the #announcements channel for the application link."
```

#### **Kategorie-Einstellungen verstehen**

Der Abschnitt `categories` ist das Herzstück deines Routing-Systems. Während die meisten Einstellungen selbsterklärend sind, sind hier die zwei wichtigsten Konfigurationen für deinen Team-Workflow:

* bypassRoleId: Dies ist die Rollen-ID (in der Regel Management oder Server-Admins), die alle Ticket-Berechtigungen überschreibt. Selbst wenn ein Ticket übernommen und für ein bestimmtes Teammitglied gesperrt wird, behalten Benutzer mit der `bypassRoleId` immer Lese- und Schreibzugriff, um die Interaktion zu beaufsichtigen.
* enableClaimRemoval: Akzeptiert `true` oder `false`.
  * Wenn auf `true` gesetzt (Sperrmodus): Wenn ein Teammitglied auf die Schaltfläche „Beanpruchen“ (Claim) klickt, entfernt der Bot den Zugriff der allgemeinen `staffRoleId` auf den Kanal. Nur der Benutzer, das übernehmende Teammitglied und die `bypassRoleId` können das Ticket sehen. Das ist hervorragend für die Privatsphäre und verhindert, dass Teammitglieder durcheinanderreden.
  * Wenn auf `false` gesetzt: Das Übernehmen eines Tickets ordnet lediglich den Namen des Teammitglieds dem Embed und der Datenbank zu, aber alle anderen Teammitglieder können den Kanal weiterhin lesen und darin antworten.
