# Base API

To hook into the system, your main class must extend `AeroDeskAddon`. Here is a basic implementation demonstrating the core base methods in a fluid manner:

```java
package com.example.myaddon;

import com.avenvault.discord.api.AeroDeskAddon;

public class MyCustomAddon extends AeroDeskAddon {

    @Override
    public void onEnable() {
        // Prints custom log messages prefixed with the addon's name
        getLogger().info("Addon enabled and hooked into AeroDesk!");
        
        // Fetches the entire BotConfig object
        getApi().getConfig(); 
        
        // A quick shortcut inside the addon to grab the config
        getLogger().info("Current bot prefix is: " + getConfig().prefix);
    }
}
```

or

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
