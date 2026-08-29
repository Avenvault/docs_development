# Категории и Уровни поддержки

Организуйте запросы поддержки и классифицируйте уровни приоритетов, не объявляя промежуточных переменных.

- Получить категорию: `getApi().getConfig().tickets.categories.get("bug");`
- Добавить категорию: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Сообщения об ошибках", "Приветственное сообщение здесь", "123456789");`
- Редактировать категорию: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "New Embed Title";`
- Удалить категорию: `getApi().getConfig().tickets.categories.remove("bug");`
- Получить уровень: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Добавить Тик: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321");`
- Редактировать уровень: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Базовая поддержка";`
- Удалить Тик: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("VIP Support");`
