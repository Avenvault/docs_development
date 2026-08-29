# 数据库和配置同步方法

管理活跃的数据库连接并同步您整个系统的配置变化。 通过API直接修改后，记住保存您的配置。

- 检查Active DB: `getApi().getBotConfig().database.activeDatabase;` _(返回 "MySQL", "SQLite", "MongoDB"等)_
- 检索DB 主机: `getApi().getBotConfig().database.host;`
- 保存配置更改: `getApi().saveConfig();` _(确保任何通过 API 做的编辑都保存在数据库/YAML)_
- 重新加载配置: `getApi().reloadConfig();` _(强制机器人从数据库中拉新数据)_
