# Grundläggande API

För att kroka in i systemet måste din huvudklass förlänga `AeroDeskAddon`. Här är en grundläggande implementering som visar de grundläggande basmetoderna på ett flytande sätt:

```java
paket com.example.myaddon;

importera com.avenvault.discord.api. eroDeskAddon;

public class MyCustomAddon förlänger AeroDeskAddon {

    @Åsidosätt
    public void onEnable() {
        // Skriver ut anpassade loggmeddelanden prefixade med tilläggens namn
        getLogger(). nfo("Addon aktiverad och ansluten till AeroDesk! );
        
        // Hämtar hela BotConfig objektet
        getApi(). etConfig() 
        
        // En snabb genväg inuti tillägget för att ta tag i konfigurationen
        getLogger(). nfo("Nuvarande bot prefix är: " + getConfig().prefix);
    }
}
```

eller

```java
paket com.example.myaddon;

importera com.avenvault.discord.api. eroDeskAddon;

public class HelloWorldMain2 förlänger AeroDeskAddon {

    @Åsidosätt
    public void onEnable() {
        System. Utskrift.Utskrift("======================================);
        Utskrift. rintln ("👋 HELLO WORLD ADDON ENABLED! 👋");

        Prova {
            om (getApi() ! noll && getApi(). etConfig() != noll) {
                Sträng dbType = getApi(). etConfig().database.activeDatabase;
                // dbType returnerar vad som är valt e. MySQL
                System.out. rintln("Boten använder för närvarande databasen: " + dbType)
            } else {
                System. Ö. rintln ("bot API eller config var inte redo ännu, men addon laddad! );
            }
        } catch (Undantag e) {
            // Detta kommer att skriva ut den exakta anledningen om något går fel här
            System. rr.println("Fel vid läsning av konfigurationen i HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln("=====================================");
    }

    @Åsidosätt
    public void onDisable() {
        System. ut.println("🛑 Hello World2 Addon stängs av!");
    }
}
```

###
