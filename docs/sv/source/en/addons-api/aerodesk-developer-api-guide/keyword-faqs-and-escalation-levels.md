# Nyckelord Vanliga frågor och skalningsnivåer

Hantera nyckelordsutlösta automatiska svar och ärendeeskaleringskedjor direkt via konfigurationen med `getApi()` hook.

- Lägg till vanliga frågor: `getApi().getConfig().tickets.keywordFaqs.put("återbetalning", "Vänligen öppna en biljett för återbetalningar");`
- Hämta FAQ: `getApi().getConfig().tickets.keywordFaqs.get("återbetalning");`
- Redigera FAQ: `getApi().getConfig().tickets.keywordFaqs.put("återbetalning", "Ny återbetalningspolicy tillämpad.");`
- Ta bort FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("återbetalning");`
- Hämta Escalation: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Lägg till Escalation: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "fakturering", "1122334455"));`
- Ta bort Escalation: `getApi().getConfig().tickets.escalationLevels.removeIf(nivå -> level.levelName.equals("Manager Review");`
