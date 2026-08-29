# Kategorier & Support Tiers

Organisera supportförfrågningar och klassificera prioriterade nivåer sömlöst utan att deklarera mellanliggande variabler.

- Hämta Kategori: `getApi().getConfig().tickets.categories.get("bug");`
- Lägg till Kategori: `getApi().getConfig().tickets.categories.put("bug", ny TicketCategory("Bug Reports", "Välkommen meddelande här", "123456789"));`
- Redigera kategori: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "New Embed Title";`
- Ta bort Kategori: `getApi().getConfig().tickets.categories.remove("bug");`
- Hämta Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Lägg till Tier: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321");`
- Redigera Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Basic Support";`
- Ta bort Tier: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support");`
