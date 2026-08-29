# 类别和支持级别

组织支持请求并无缝分类优先级，而不申报中间变量。

- 获取类别: `getApi().getConfig().tickets.categories.get("bug");`
- 添加类别: `getApi().getConfig().tickets.categories.put("bug", new TicketCategory", "Bug Reports", "Welcome message here", "123456789");`
- 编辑类别: \`getApi().getConfig().tickets.categories.get("bug").embedTitle = "新嵌入标题";"
- 删除类别: `getApi().getConfig().tickets.categories.remove("bug");`
- 获取层级: `getApi().getConfig().ticketTiers.get(0);`
- 添加层级: `getApi().getConfig().ticketTiers.add(new BotConfig.TicketTier("VIP Support", "987654321");`
- 编辑层级: `getApi().getConfig().ticketTiers.get(0).name = "基本支持";`
- 删除层级: `getApi().getConfig().ticketTiers.removeIf(阶级-> tier.name.equals("VIP Support"));`
