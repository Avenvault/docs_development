# Kategorier Og Supportniveauer

Organiser support anmodninger og klassificere prioriterede niveauer problemfrit uden at erklære mellemliggende variabler.

- Hent Kategori: `getApi().getConfig().tickets.categories.get("bug");`
- Tilføj kategori: `getApi().getConfig().tickets.categories.put("bug", ny TicketCategory("Fejlrapporter", "Velkommen besked her", "123456789"));`
- Rediger Kategori: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "Ny Embed Title";`
- Slet Kategori: `getApi().getConfig().tickets.categories.remove("bug");`
- Hent Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Tilføj Niveau: `getApi().getConfig().tickets.ticketTiers.add(ny BotConfig.TicketTier ("VIP Support", "987654321"));`
- Rediger Niveau: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Basic Support";`
- Slet niveau: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support"));`
