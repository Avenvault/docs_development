# Questions fréquentes et niveaux d'escalade

Gérez les réponses automatiques déclenchées par les mots clés et les chaînes d'escalade de tickets directement via la configuration en utilisant le crochet `getApi()`.

- Ajouter FAQ: `getApi().getConfig().tickets.keywordFaqs.put("remboursement", "Veuillez ouvrir un ticket pour les remboursements.");`
- Récupérer FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
- Modifier FAQ: `getApi().getConfig().tickets.keywordFaqs.put("remboursement", "Nouvelle politique de remboursement appliqué.");`
- Supprimer FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refund");`
- Récupérer l'escalade: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Ajouter Escalade: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevels.add("Manager Review", "billing", "1122334455"));`
- Supprimer l'escalade : `getApi().getConfig().tickets.escalationLevels.removeIf(niveau -> level.levelName.equals("Manager Review"));`
