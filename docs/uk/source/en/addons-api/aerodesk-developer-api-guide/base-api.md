# Базовий API

Щоб під'єднатися до системи, основний клас повинен розширити `AeroDeskAddon`. Ось базова реалізація, яка демонструє основні основні методи обробки рідин:

```java
пакет com.example.myaddon;

імпортувати com.avenvault.discord.api. eroDeskAddon;

публічний клас MyCustomAddon подовжує AeroDeskAddon {

    @Override
    публічне анулювання onEnable() {
        // Друкує користувальницькі повідомлення журналу, попередньо закріплені за назвою addon's name,
        getLogger(). nfo("Аддон підключений та зачепився в Аеродеск! );
        
        // Оновлює весь об'єкт BotConfig
        getApi(). etConfig(); 
        
        // Швидкий ярлик всередині додатку, щоб захопити конфігурацію
        getLogger(). nfo("Префікс поточного бота: " + getConfig().prefix);
    }
}
```

або

```java
package com.example.myaddon;

import com.avenvault.discord.api.AeroDeskAddon;

public class HelloWorldMain2 extends AeroDeskAddon {

    @Override
    public void onEnable() {
        System.out.println("=================================");
        System.out.println("👋 HELLO WORLD ADDON ENABLED! 👋");

        try {
            if (getApi() != null && getApi().getConfig() != null) {
                String dbType = getApi().getConfig().database.activeDatabase;
                // dbType returns what is selected e.g MySQL
                System.out.println("The bot is currently using database: " + dbType);
            } else {
                System.out.println("The bot API or config was not ready yet, but addon loaded!");
            }
        } catch (Exception e) {
            // This will print the exact reason if something goes wrong here
            System.err.println("Error reading config in HelloWorld2:");
            e.printStackTrace();
        }

        System.out.println("=================================");
    }

    @Override
    public void onDisable() {
        System.out.println("🛑 Hello World2 Addon Shutting Down!");
    }
}
```

###
