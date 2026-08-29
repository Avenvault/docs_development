# Stichwort-FAQs & Eskalationsstufen

Verwalten Sie Keyword-ausgelöste Auto-Antworten und Ticket-Eskalationsketten direkt über die Konfiguration mit dem Hook `getApi()`.

- FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Bitte ein Ticket für Erstattungen öffnen.");`
- FAQ: `getApi().getConfig().tickets.keyword Faqs.get("refund");`
- FAQ bearbeiten: `getApi().getConfig().tickets.keyword Faqs.put("refund", "New refund policy applied.");`
- FAQ löschen: `getApi().getConfig().tickets.keyword Faqs.remove("refund");`
- Escalation: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Eskalation: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "Abrechnung", "1122334455");`
- Löschen Escalation: `getApi().getConfig().tickets.escalationLevels.removeIf(level -> level.levelName.equals("Manager Review"));`
