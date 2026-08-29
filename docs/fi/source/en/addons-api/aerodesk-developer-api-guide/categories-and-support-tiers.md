# Kategoriat & Tukitasot

Järjestä tukipyynnöt ja luokitella prioriteettitasot saumattomasti ilmoittamatta välimuuttujia.

- Hae kategoria: `getApi().getConfig().tickets.categories.get ("bug");`
- Lisää kategoria: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Bug Reports", "Welcome message here", "123456789"));`
- Muokkaa kategoriaa: `getApi().getConfig().tickets.categories.get ("bug").embedTitle = "New Embed Title";`
- Poista kategoria: `getApi().getConfig().tickets.categories.remove("bug");`
- Nouda tasoitti: `getApi().getConfig().tickets.ticketTiers.get(0)`
- Lisää otsikko: `getApi().getConfig().ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321");`
- Muokkaa tasoa: `getApi().getConfig().tickets.ticketTiers.get(0).nimi = "Basic Support";`
- Poista taso: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support");`
