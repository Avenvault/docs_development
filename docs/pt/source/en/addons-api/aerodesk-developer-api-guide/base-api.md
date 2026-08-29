# API Base

Para ligar ao sistema, sua classe principal deve estender `AeroDeskAddon`. Aqui está uma implementação básica que demonstra os métodos base básicos de forma fluida:

```java
package com.exemplo.myaddon;

importe com.avenvault.discord.api. eroDeskAddon;

classe pública MyCustomAddon estende AeroDeskAddon {

    @Override
    public void onEnable() {
        // Imprime mensagens de log personalizadas prefixadas com o nome do addon's
        getLogger(). nfo("Addon habilitado e ligado na AeroDesk! );
        
        // Busca todo o objeto BotConfig
        getApi(). etConfig(); 
        
        // Um atalho rápido dentro da extensão para pegar a configuração
        getLogger(). nfo("Prefixo do bot atual é: " + getConfig().prefix);
    }
}
```

ou

```java
package com.exemplo.myaddon;

importe com.avenvault.discord.api. eroDeskAddon;

classe pública HelloWorldMain2 estende AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println("=================================");
        System.out. rintln("👋 HELLO WORLD ADICIONADO HABILITADO! 👋");

        tente {
            if (getApi() ! null && getApi(). etConfig() != null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // dbType retorna o que está selecionado. MySQL
                System.out. rintln("O bot está usando o banco de dados: " + dbType);
            } else {
                System. vrs. rintln("A API ou configuração do bot ainda não estavam prontas, mas adicione-se! );
            }
        } catch (Exceção e) {
            // Isto irá imprimir a razão exata se algo der errado aqui Sistema
            . r.println("Erro lendo a configuração em HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln("================================);
    }

    @Override
    public void onDisable() {
        System. ut.println("🛑 Olá World2 Addon Fechando para baixo!");
    }
}
```

###
