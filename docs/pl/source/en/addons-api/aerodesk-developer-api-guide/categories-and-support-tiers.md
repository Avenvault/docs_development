# Kategorie i poziomy wsparcia

Organizowanie wniosków o wsparcie i bezproblemowe klasyfikowanie poziomów priorytetów, bez deklarowania zmiennych pośrednich.

- Pobierz kategorię: `getApi().getConfig().tickets.categories.get("bug");`
- Dodaj kategorię: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Raporty błędów", "Welcome message here", "123456789"));`
- Edytuj kategorię: `getApi().getConfig().tickets.categories.get("bug").embedTytuł = "New Embed Title";`
- Usuń kategorię: `getApi().getConfig().tickets.categories.remove("bug");`
- Pobierz Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Dodaj Tier: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321"));`
- Edytuj Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Basic Support";`
- Usuń Tier: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support"));`
