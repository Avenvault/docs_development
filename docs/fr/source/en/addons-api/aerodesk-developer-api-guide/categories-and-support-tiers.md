# Catégories et paliers de soutien

Organiser les demandes de support et classer les niveaux de priorité de façon transparente sans déclarer les variables intermédiaires.

- Récupérer la catégorie: `getApi().getConfig().tickets.categories.get("bug");`
- Ajouter une catégorie: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Bug Reports", "Welcome message here", "123456789"));`
- Modifier la catégorie: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "New Embed Title";`
- Supprimer la catégorie: `getApi().getConfig().tickets.categories.remove("bug");`
- Récupérer le niveau : `getApi().getConfig().tickets.ticketTiers.get(0);`
- Ajouter un niveau : `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321"));`
- Modifier le niveau : `getApi().getConfig().tickets.ticketTiers.get(0).name = "Support de base";`
- Supprimer le niveau : `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("Support VIP"));`
