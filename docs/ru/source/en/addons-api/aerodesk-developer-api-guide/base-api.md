# Базовый API

Чтобы встать в систему, ваш главный класс должен расширить `AeroDeskAddon`. Ниже приводится базовая практика, свидетельствующая о том, что базовые методы являются гибкими:

```java
package com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

public class MyCustomAddon extends AeroDeskAddon {

    @Override
    public void onEnable() {
        // Выводит пользовательские журнальные сообщения, префиксные с именем аддона
        getLogger(). nfo("Дополнение включено и подключено к AeroDesk! );
        
        // Извлекает весь объект BotConfig
        getApi(). etConfig(); 
        
        // Быстрый ярлык внутри аддона, чтобы захватить конфигурацию
        getLogger(). nfo("Текущий префикс бота: " + getConfig().prefix);
    }
}
```

или

```java
package com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

public class HelloWorldMain2 extends AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println("===================================");
        Система.out. rintln("👋 HELLO WORLD ADDON ENABLED! 👋");

        try {
            if (getApi() ! null && getApi(). etConfig() != null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // Возвращает то, что выбрано. MySQL
                System.out. rintln("Бот использует базу данных: " + dbType);
            } else {
                System. ut. rintln("Бот API или конфигурация еще не готовы, но аддон загружен! );
            }
        } catch (Exception e) {
            // Это выведет точную причину, если что-то пойдет не так здесь
            Система. rr.println("Ошибка чтения конфигурации в HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln("=======================================");
    }

    @Override
    public void onDisable() {
        System. ut.println("🛑 Hello World2 Addon Shutting Down!");
    }
}
```

###
