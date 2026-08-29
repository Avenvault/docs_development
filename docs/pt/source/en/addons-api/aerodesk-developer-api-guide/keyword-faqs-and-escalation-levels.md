# FAQs & Níveis de Escalação de Palavra-Chave

Gerenciar respostas automáticas acionadas por palavra-chave e combinações de escalonamento de tickets diretamente através da configuração usando o `getApi()` hook.

- Adicionar FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Por favor, abra um ticket para reembolsos.");`
- Recuperar FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
- Editar FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Nova política de reembolso aplicada.");`
- Delete FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("refund");`
- Recuperar Escalonamento: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Adicionar Escalonamento: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Revisão do Gestor", "billing", "1122334455"));`
- Excluir Escalação: `getApi().getConfig().tickets.escalationLevels.removeIf(nível -> level.levelName.equals("Revisão do Gestor"));`
