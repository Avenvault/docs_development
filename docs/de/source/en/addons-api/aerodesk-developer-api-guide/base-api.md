# Basis-API

Um in das System einzugreifen, muss Ihre Hauptklasse `AeroDeskAddon` erweitern. Hier ist eine grundlegende Implementierung, die die grundlegenden Basis-Methoden in flüssiger Weise demonstriert:

```java
package com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

öffentliche Klasse MyCustomAddon erweitert AeroDeskAddon {

    @Override
    public void onEnable() {
        // Gibt benutzerdefinierte Logmeldungen aus, die mit dem Namen des Addons
        getLogger(). nfo("Addon aktiviert und gehackt in AeroDesk! );
        
        // Holt das gesamte BotConfig-Objekt
        getApi(). etConfig(); 
        
        // Eine Schnellverknüpfung innerhalb des Addons, um die Konfiguration
        getLogger(). nfo("Aktueller Bot-Präfix ist: " + getConfig().prefix);
    }
}
```

oder

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
