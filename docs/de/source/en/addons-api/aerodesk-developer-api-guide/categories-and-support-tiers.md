# Kategorien & Support-Stufen

Organisieren Sie Supportanfragen und ordnen Sie Prioritätsebenen nahtlos ein, ohne Zwischenvariablen zu deklarieren.

- Kategorie abrufen: `getApi().getConfig().tickets.categories.get("bug");`
- Kategorie hinzufügen: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Bug Reports", "Welcome message here", "123456789");`
- Kategorie bearbeiten: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "Neuer Einbetttitel";`
- Kategorie löschen: `getApi().getConfig().tickets.categories.remove("bug");`
- Rufe Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Füge Tier: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321");`
- Bearbeite Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Basic Support";`
- Lösche Tier: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support");`
