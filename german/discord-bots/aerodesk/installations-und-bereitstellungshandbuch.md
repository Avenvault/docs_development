---
icon: desktop-arrow-down
---

# Installations- und Bereitstellungshandbuch

Das Einrichten des Enterprise-Ticket-Systems auf deinem Host-System (VPS, Dedicated Server oder Pterodactyl-Panel) ist ein einfacher Prozess. Befolge diese Schritte sorgfältig, um ein reibungsloses Deployment zu gewährleisten.

#### 📋 Voraussetzungen

Stelle vor dem Start sicher, dass auf deiner Hosting-Umgebung Folgendes installiert ist:

* [ ] Java 17 oder höher (erforderlich für moderne JDA-Versionen).
* [ ] Eine Datenbank-Lösung (MongoDB-Cluster, SQL-Datenbank oder lokaler Speicherzugriff für JSON).
* [ ] Ein Discord-Bot-Token (erhältlich im [Discord Developer Portal](https://discord.com/developers/applications)).

#### **Schritt 1: Discord-Anwendungs-Einrichtung**

1. Gehe zum Discord Developer Portal und erstelle eine neue Anwendung („New Application“).
2. Navigiere zum Reiter Bot und klicke auf Add Bot.
3. Wichtig: Scrolle nach unten zu Privileged Gateway Intents und aktiviere:
   * Server Members Intent (wird zum Überprüfen von Rollen benötigt).
   * Message Content Intent (wird für die FAQ-Schlüsselwort-Erkennung benötigt).
4. Speichere deine Änderungen und kopiere dein Bot-Token. Halte dieses geheim!
5. Lade den Bot auf deinen Server ein, indem du zu OAuth2 gehst und zum OAuth2 URL Generator hinunterscrollst. Stelle sicher, dass du sowohl `bot` als auch `applications.commands` (erforderlich für Slash-Befehle) aktivierst. Wähle `Administrator` unter _General Permissions_ aus und füge die URL aus dem Feld _Generated URL_ in deinen Browser ein.

#### **Schritt 2: Server-Vorbereitung**

1. Erstelle einen neuen Ordner auf deinem Host-System für den Bot (z. B. `AeroDesk`).
2. Lade die neueste Version herunter und platziere sie in diesem Ordner.
3.  Führe den Bot zum ersten Mal aus, um die Konfigurationsdateien zu generieren:

    <pre><code>java -jar <a data-footnote-ref href="#user-content-fn-1">[NAME]</a>.jar
    </code></pre>
4. Der Bot wird sich automatisch beenden und dich darüber informieren, dass eine `config.yml` generiert wurde.

#### **Schritt 3: Konfiguration**

1. Öffne die neu generierte `config.yml`.
2. Füge dein Bot-Token und deine persönliche Discord-Owner-ID ein.
3. Konfiguriere deine Datenbank-URI (falls du MongoDB oder SQL verwendest).
4. Trage deine serverspezifischen Einstellungen ein, einschließlich Rollen-IDs, Kanal-IDs und deinen Kategorie-Konfigurationen (details dazu findest du im [Konfigurations-Guide](konfigurationshandbuch.md)).
5. Speichere die Datei.

#### **Schritt 4: Finaler Start**

Starte den Bot erneut mit deinem bevorzugten Start-Skript, Screen oder Pterodactyl-Panel:

<pre><code>java -Xms1G -Xmx2G -jar <a data-footnote-ref href="#user-content-fn-1">[NAME]</a>.jar
</code></pre>

Bei korrekter Konfiguration protokolliert die Konsole eine erfolgreiche Datenbankverbindung und bestätigt, dass deine Slash-Befehle global registriert wurden.

[^1]: Change this to the name of the jar
