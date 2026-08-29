# Часто задаваемые вопросы и уровни эскалации

Управление автоответчиками ключевого слова и цепочками эскалации заявок напрямую через конфигурацию, используя `getApi()` хук.

- Добавить FAQ: `getApi().getConfig().tickets.keywordFaqs.put("Возвращайте", "Пожалуйста, откройте заявку для возврата средств.");`
- Получить FAQ: `getApi().getConfig().tickets.keywordFaqs.get("возмещение");`
- Редактировать FAQ: `getApi().getConfig().tickets.keywordFaqs.put("возмещение", "Новая политика возврата средств.");`
- Удалить FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("возмещение");`
- Получение эскалации: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Добавить Escalation: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Обзор менеджера", "billing", "1122334455");`
- Удалить эскалацию: `getApi().getConfig().tickets.escalationLevels.removeIf(уровень -> level.levelName.equals("Обзор менеджера");`
