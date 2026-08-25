---
icon: question
---

# Fehlerbehebung & FAQ

F: Meine Konsole zeigt „FATAL: Invalid License Key“ an und das Plugin deaktiviert sich selbst.

A: Das bedeutet, dass die RSA-256-Cloud-Authentifizierung deinen Schlüssel abgelehnt hat.

1. Überprüfe deine `config.yml`, um sicherzustellen, dass sich keine nachstehenden Leerzeichen um deinen Schlüssel befinden.
2. Überprüfe im Premium-Portal, ob dein Abonnement/deine Lizenz abgelaufen ist.
3. Stelle sicher, dass du das exakte vorgegebene Format verwendest (z. B. 1234-5678-9012).



F: Die Konsole zeigt beim Start „License Server Unreachable“ an

A: Das Plugin benötigt eine aktive Internetverbindung, um seine Integrität zu überprüfen. Stelle sicher, dass dein Host/Server ausgehende Verbindungen über Port 443 (HTTPS) zulässt und deine Firewall den Verkehr zu unseren Authentifizierungsserver nicht blockiert.

**F**: Spieler können immer noch außerhalb der Arena-Begrenzungen bauen!

A: Überprüfe zuerst, ob der betreffende Spieler kein Administrator (OP) ist oder nicht über das Berechtigungs-Node `bwr.bypass` verfügt. Überprüfe zweitens deine Min- und Max-Koordinaten in der `config.yml`, um sicherzustellen, dass die mathematische Begrenzungskiste korrekt gezogen wurde (Min-Werte sollten immer kleiner als Max-Werte sein).

**F**: Ist dieses Plugin mit ViaVersion/Geyser kompatibel?

**A**: Ja! Da BedwarsRestrictions Begrenzungen auf Serverebene verarbeitet, ist es zu 100 % kompatibel mit Bedrock-Spielern über Geyser und Clients, die verschiedene Versionen über ViaVersion nutzen.

**Brauchst du weitere Hilfe?** [_**Kontaktiere uns**_](https://plugins.avenvault.com/contact) **mit deinem Lizenzschlüssel (zur Überprüfung) oder tritt unserem Discord bei und verifiziere deine Lizenz, um Support zu erhalten!**
