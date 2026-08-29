# Ключові питання та рівні масштабів

Керуйте ключовим словом авто-відповіді та ланцюжками ескалації тікетів безпосередньо через конфігурацію, використовуючи гак "getApi()".

- Додати FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Будь ласка, відкрийте заявку для повернення коштів.");`
- Отримати FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
- Редагувати FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Застосовано нову політику повернення коштів.");`
- Видалити FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refund");`
- Отримати ескалацію: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Додати Escalation: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "billing", "billing", "1122334455"));`
- Видалити Escalation: `getApi().getConfig().tickets.escalationLevels.removeIf(рівень -> level.levelName.equals("Manager Review");`
