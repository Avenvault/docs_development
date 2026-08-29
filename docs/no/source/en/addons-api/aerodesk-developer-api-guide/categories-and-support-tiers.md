# Kategorier og støtte erfaringer

Organiser forespørsler og klassifisere prioritetsnivåer sømløst uten å deklarere mellomvariabler.

- Hent kategori: `getApi().getConfig().tickets.categories.get("bug");`
- Legg til kategori: `getApi().getConfig().tickets.categories.put("bug", nye TicketCategory("Bug Reports", "Velkommen melding her", "123456789"));`
- Redigere kategori: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "New Embed Title";`
- Slett kategori: `getApi().getConfig().tickets.categories.remove("bug");`
- Hent Tier: `getApi().getConfig().).tickets.ticketTiers.get(0);`
- Legg til Tier: `getApi().getConfig().tickets.ticketTiers.add(ny BotConfig.TicketTier("VIP Support", "987654321"));`
- Rediger Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Basic Support";`
- Slette Tier: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support");`
