# Słowo kluczowe FAQ i poziomy eskalacji

Zarządzaj automatycznymi odpowiedziami i sieciami eskalacji zgłoszeń wyzwalanymi przez słowo kluczowe bezpośrednio za pomocą konfiguracji za pomocą zaczepu `getApi()`.

- Dodaj FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Please open a ticket for refunds.");`
- Pobierz FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
- Edytuj FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "New refund policy applied ied.");`
- Usuń FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refund");`
- Pobierz Eskalation: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Dodaj skalowanie: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "billing", "1122334455"));`
- Usuń skalowanie: `getApi().getConfig().tickets.escalationLevels.removeIf(poziom -> poziom.levelName.equals("Manager Review"));`
