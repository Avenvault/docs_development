# Nøgleord Ofte Stillede Spørgsmål Og Eskaleringsniveauer

Administrer nøgleords-udløst auto-svar og billet-eskalering kæder direkte via config ved hjælp af `getApi()` krog.

- Tilføj FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Åbn venligst en billet for refunderinger");`
- Hent FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
- Rediger FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Den nye tilbagebetalingspolitik anvendes.");`
- Slet FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refund");`
- Hent Opskalering: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Tilføj Eskalering: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager anmeldelse", "fakturering", "1122334455")));`
- Slet Eskalering: `getApi().getConfig().tickets.escalationLevels.removeIf(level -> level.levelName.equals("Manager anmeldelse"));`
