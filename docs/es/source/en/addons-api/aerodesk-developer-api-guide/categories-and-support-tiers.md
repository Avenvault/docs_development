# Categorías y niveles de soporte

Organizar solicitudes de soporte y clasificar los niveles de prioridad sin tener que declarar variables intermedias.

- Recuperar Categoría: `getApi().getConfig().tickets.categories.get("bug");`
- Añadir Categoría: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("informes de errores", "Mensaje de bienvenida aquí", "123456789"));`
- Editar Categoría: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "Nuevo título de inserción";`
- Eliminar Categoría: `getApi().getConfig().tickets.categories.remove("bug");`
- Recuperar Tier: `getApi().getConfig().tickets.tickets.ticketTiers.get(0);`
- Añadir nivel: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("Soporte VIP", "987654321"));`
- Editar nivel: `getApi().getConfig().tickets.tickets.ticketTiers.get(0).name = "Soporte Básico";`
- Eliminar nivel: `getApi().getConfig().tickets.tickets.removeIf(tier -> tier.name.equals("Soporte VIP"));`
