# Категорії та Рівні підтримки

Організовуйте запити підтримки та класифікуйте пріоритетні рівні безшовно без оголошення проміжних змінних.

- Отримати категорію: `getApi().getConfig().tickets.categories.get("bug");`
- Додати категорію: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory("Звіти про помилку", "Привітальне повідомлення тут", "123456789");`
- Редагувати категорію: `getApi().getConfig().tickets.categories.get("bug").embedbed Title";`
- Видалити категорію: `getApi().getConfig().tickets.categories.remove("bug");`
- Отримати Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Додати Tier: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("VIP підтримка", "987654321");`
- Редагувати Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Базова підтримка";`
- Видалити Tier: `getApi().getConfig().tickets.removeIf(tier -> tier.name.equals("VIP Support");`
