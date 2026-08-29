# Banco de Dados e Métodos de Sincronização Config

Gerencie a conexão da base de dados ativa e sincronize as alterações de configuração em seu sistema instantaneamente. Lembre-se de salvar sua configuração após fazer modificações diretas através da API.

- Verifique Active DB: `getApi().getBotConfig().database.activeDatabase;` _(Retorna "MySQL", "SQLite", "MongoDB", etc.)_
- Recuperar DB Host: `getApi().getBotConfig().database.host;`
- Salvar Configurações Alterações: `getApi().saveConfig();` _(Garante qualquer edição feita via API são salvas no banco de dados/YAML)_
- Recarregar configuração: `getApi().reloadConfig();` _(Força o bot a puxar dados frescos do banco de dados)_
