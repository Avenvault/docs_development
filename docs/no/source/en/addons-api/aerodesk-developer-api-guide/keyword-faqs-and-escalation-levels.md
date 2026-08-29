# Nøkkelord FAQs & skaleringsnivåer

Behandle nøkkelord-utløste autosvar og billetteskaleringskjeder direkte via konfigurasjonen med `getApi()`-kroken.

- Legg til FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Vennligst åpne en billett for refusjon.");`
- Hent FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refunder");`
- Rediger FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refundert", "Ny refusjonspolicy benyttet.");`
- Slett FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refundert);`
- Hente Eskalering: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Legg til Eskalering: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "fakturering", "1122334455"));`
- Slett Eskalering: `getApi().getConfig().tickets.escalationLevels.removeIf(level -> level.levelName.equals("Manager Review"));`
