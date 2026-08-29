# 关键字常见问题和升级级别

使用 `getApi()` 钩直接通过配置管理关键字触发的自动响应和服务单升级链。

- 添加常见问题: `getApi().getConfig().tickets.keywordFaqs.put("退款", 请打开工单以退款。");`
- 获取常见问题: `getApi().getConfig().tickets.keywordFaqs.get("退款");`
- 编辑常见问题: `getApi().getConfig().tickets.keywordFaqs.put("退款", "新退款政策应用");`
- 删除常见问题: `getApi().getConfig().tickets.keywordFaqs.remove("退款");`
- 检索升级： `getApi().getConfig().tickets.scripationLevels.get(0);`
- 添加升级： `getApi().getConfig().tickets.scrapationLevels.add(new EscalationLevel("Manager Review", "billing", "1122334455");`
- 删除升级： `getApi().getConfig().tickets.scrapationLevels.removeIf(level -> level.levelName.equals("Manager Review"));`
