# Categories & Support Tiers

Organize support requests and classify priority levels seamlessly without declaring intermediate variables.

* Retrieve Category: `getApi().getConfig().tickets.categories.get("bug");`
* Add Category: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Bug Reports", "Welcome message here", "123456789"));`
* Edit Category: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "New Embed Title";`
* Delete Category: `getApi().getConfig().tickets.categories.remove("bug");`
* Retrieve Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
* Add Tier: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321"));`
* Edit Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Basic Support";`
* Delete Tier: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support"));`
