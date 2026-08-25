---
icon: question
---

# Häufig gestellte Fragen (FAQ)

Hier sind die häufigsten Probleme, auf die Server-Administratoren stoßen, und wie du sie löst.

#### **Einrichtung & Konfiguration**

F: Wie finde ich Rollen-IDs und Kanal-IDs für die Konfiguration?

A: Du musst den Entwicklermodus in Discord aktivieren.

1. Gehe zu den Discord-Einstellungen > Erweitert > Aktiviere den Entwicklermodus.
2. Mache einen Rechtsklick auf eine beliebige Rolle, einen Kanal oder einen Benutzer und klicke ganz unten im Menü auf Kanal-ID kopieren oder Rollen-ID kopieren.

F: Ich habe den Bot eingeladen, aber ich sehe `/ticketpanel` oder `/stats` nicht?

A: Slash-Befehle benötigen bestimmte Berechtigungsbereiche (Scopes), um registriert zu werden.

1. Stelle sicher, dass du den Bot mit aktiviertem `applications.commands`-Scope im OAuth2-URL-Generator eingeladen hast.
2. Werfe den Bot vom Server und lade ihn mit der korrekten URL erneut ein. Hinweis: Du kannst versuchen F5 zu drücken, aber globale Slash-Befehle können manchmal bis zu einer Stunde brauchen, um sich nativ über alle Discord-Server zu synchronisieren, obwohl sie normalerweise sofort erscheinen.

#### 🛠️ Funktionalität & Fehler

F: Der Bot gibt eine `MongoTimeoutException` in der Konsole aus und stürzt ab.

&#x20;A:&#x20;

Das bedeutet, dass der Bot deine MongoDB-Datenbank nicht erreichen kann.

1. Überprüfe deine `config.yml`, um sicherzustellen, dass die `database.uri` korrekt formatiert ist.
2. Wenn du MongoDB Atlas (Cloud) verwendest, stelle sicher, dass du die IP-Adresse deines Servers im Reiter „Network Access“ auf die Whitelist gesetzt hast (oder richte sie auf `0.0.0.0/0` ein, um alle IPs zuzulassen).

F: Wenn ein Teammitglied ein Ticket übernimmt, wird der Kanal nicht gesperrt!

Das ist fast immer ein Problem mit der Discord-Rollenhierarchie oder den Berechtigungen.

1. Stelle sicher, dass `enableClaimRemoval: true` in deiner Konfiguration für diese Kategorie eingestellt ist.
2. Stelle sicher, dass die höchste Rolle des Bots in deinen Discord-Servereinstellungen über den Team-Rollen platziert ist. Der Bot kann keine Berechtigungen von Rollen entfernen, die höher als seine eigene sind.
3. Stelle sicher, dass der Bot über die Berechtigungen „Kanäle verwalten“ und „Rollen verwalten“ verfügt (die Berechtigung „Administrator“ wird jedoch empfohlen).

F: Warum generieren die HTML-Transkripte keinen Link?

A: Der Bot lädt die generierte HTML-Datei über die in deiner Konfiguration angegebene `logsChannelId` direkt auf das Discord-CDN hoch. Wenn der Bot in diesem speziellen verdeckten Log-Kanal nicht über die Berechtigung „Dateien anhängen“ oder „Nachrichten senden“ verfügt, schlägt der Upload fehl und es kann kein Link generiert werden. Überprüfe die Kanalberechtigungen!
