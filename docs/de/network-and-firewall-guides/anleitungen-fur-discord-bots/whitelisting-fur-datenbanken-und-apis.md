# Whitelisting für Datenbanken und APIs

Fast alle modernen Discord-Bots speichern Nutzerdaten in externen Datenbanken. Beispiele sind MongoDB, MySQL und PostgreSQL. Manche Bots rufen Daten von externen APIs ab, etwa YouTube, Spotify oder OpenAI.

Wenn die Datenbank auf einem anderen System als dein Bot läuft, musst du die IP-Adresse des Bots whitelisten. Das gilt beispielsweise für MongoDB Atlas oder verwaltete AWS-Datenbanken.

Externen Datenbankzugriff konfigurieren:

1. Ermittle die öffentliche IPv4-Adresse des Systems, auf dem dein Discord-Bot läuft.
2. Melde dich im Dashboard deines Datenbankanbieters an. Beispiele sind MongoDB Atlas und AWS RDS.
3. Öffne **Network Access** oder **Security Groups**.
4. Erstelle eine eingehende Regel für die konkrete IP-Adresse deines Bots.
5. _Hinweis zu dynamischen IPs:_ Bei häufig wechselnden Heimnetz-IP-Adressen musst du möglicherweise Verbindungen von überall erlauben (`0.0.0.0/0`). Verwende dann ein starkes, eindeutiges Datenbankpasswort. Bewahre es in Bitwarden oder einem anderen Passwortmanager auf.
