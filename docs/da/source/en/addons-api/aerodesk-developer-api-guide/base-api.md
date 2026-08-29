# Base API

For at tilslutte sig systemet, skal din hovedklasse udvide `AeroDeskAddon`. Her er en grundlæggende implementering, der viser de grundlæggende basismetoder i en flydende måde:

```java
pakke com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

public class MyCustomAddon extenends AeroDeskAddon {

    @Override
    public void onEnable() {
        // Prints custom log messages prefixed with the addon's name
        getLogger(). nfo("Addon aktiveret og hooked ind i AeroDesk! );
        
        // Henter hele BotConfig objektet
        getApi(). etConfig(); 
        
        // En hurtig genvej inde i tilføjelsen for at få fat i config
        getLogger(). nfo("Nuværende bot præfiks er: " + getConfig().prefix);
    }
}
```

eller

```java
pakke com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

public class HelloWorldMain2 extenends AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println ("===================================");
        System.out. rintln ("👋 HELLO WORLD ADDON ENABLED! 👋");

        prøv {
            if (getApi() ! null && getApi(). etConfig()!= null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // dbType returnerer hvad der er valgt e. MySQL
                System.out. rintln ("The bot is currently using database: " + dbType);
            } ellers {
                System. ut. rintln "Den bot API eller config var ikke klar endnu, men addon indlæst! );
            }
        } Fangst (Undtagelse e) {
            // Dette vil udskrive den nøjagtige grund, hvis noget går galt her
            System. rr.println ("Fejl ved læsning af config i HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln ("===================================");
    }

    @Override
    public void onDisable() {
        System. ut.println ("🛑 Hej World2 Addon Shutting Down!");
    }
}
```

###
