# Base API

For å hekke inn i systemet må din hovedklasse utvide `AeroDeskAddon`. Her er en grunnleggende gjennomføring som demonstrerer kjernebasemetodene på en væskemetode:

```java
pakke com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

offentlig klasse MyCustomAddon utvider AeroDeskAddon {

    @Override
    offentlig void onEnable() {
        // Prints custom log messages prefikset med addon's navn
        getLogger(). nfo("Tillegg aktivert og koblet til AeroDesk! );
        
        // Henter hele BotKonfigurasjon-objektet
        getApi(). etConfig(); 
        
        / En hurtigsnarvei i addonen for å gripe config
        getLogger(). nfo(«Nåværende bot prefix er: » + getConfig().prefiks);
    }
}
```

eller

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
