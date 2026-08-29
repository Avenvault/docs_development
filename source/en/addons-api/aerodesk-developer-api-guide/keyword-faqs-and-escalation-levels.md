# Keyword FAQs & Escalation Levels

Manage keyword-triggered auto-responses and ticket escalation chains directly via the config using the `getApi()` hook.

* Add FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Please open a ticket for refunds.");`
* Retrieve FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
* Edit FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "New refund policy applied.");`
* Delete FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refund");`
* Retrieve Escalation: `getApi().getConfig().tickets.escalationLevels.get(0);`
* Add Escalation: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "billing", "1122334455"));`
* Delete Escalation: `getApi().getConfig().tickets.escalationLevels.removeIf(level -> level.levelName.equals("Manager Review"));`
