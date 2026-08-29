# Categorias e Assistência Níveis

Organizar pedidos de apoio e classificar os níveis prioritários de forma harmoniosa sem a declaração de variáveis intermediárias.

- Recuperar Categoria: `getApi().getConfig().tickets.categories.get("bug");`
- Adicionar Categoria: `getApi().getConfig().tickets.categories.put("bug", new Ticket Category("Bug Reports", "Bem-vindo mensagem aqui", "123456789"));`
- Editar Categoria: `getApi().getConfig().tickets.categories.get("bug").embedTitle = "Novo Título de Incorporação";`
- Excluir Categoria: `getApi().getConfig().tickets.categories.remove("bug");`
- Recuperar o Tier: `getApi().getConfig().tickets.ticketTiers.get(0);`
- Adicionar Nível: `getApi().getConfig().tickets.ticketTiers.add(new BotConfig.TicketTier("Suporte VIP", "987654321"));`
- Editar Tier: `getApi().getConfig().tickets.ticketTiers.get(0).name = "Suporte Básico";`
- Excluir Tier: `getApi().getConfig().tickets.ticketTiers.removeIf(tier -> tier.name.equals("Suporte VIP"));`
