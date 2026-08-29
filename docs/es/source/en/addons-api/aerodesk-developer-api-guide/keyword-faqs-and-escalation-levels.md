# Preguntas frecuentes sobre palabras clave y niveles de escala

Administrar auto-respuestas y cadenas de escalación de tickets activadas por palabras clave directamente a través del gancho `getApi()`.

- Añadir preguntas frecuentes: `getApi().getConfig().tickets.keywordFaqs.put("reembolso", "Por favor, abra un ticket para reembolsos.");`
- Recuperar FAQ: `getApi().getConfig().tickets.keywordFaqs.get("refund");`
- Editar FAQ: `getApi().getConfig().tickets.keywordFaqs.put("refund", "Nueva política de reembolso aplicada.");`
- Eliminar FAQ: `getApi().getConfig().tickets.keywordFaqs.remove("reembolso");`
- Recuperar Escalation: `getApi().getConfig().tickets.escalationLevels.get(0);`
- Add Escalation: `getApi().getConfig().tickets.escalationLevels.add(new EscalationLevel("Manager Review", "billing", "1122334455"));`
- Eliminar escalación: `getApi().getConfig().tickets.escalationLevels.removeIf(level -> level.levelName.equals("Manager Review"));`
