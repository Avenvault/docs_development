# Podstawowe API

Aby zaczepić do systemu, Twoja główna klasa musi rozszerzać `AeroDeskAddon`. Oto podstawowa implementacja pokazująca podstawowe metody bazowe w sposób płynny:

```java
pakiet com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

klasa publiczna MyCustomAddon rozszerza AeroDeskAddon {

    @Override
    public void onEnable() {
        // Drukuje niestandardowe komunikaty dziennika poprzedzone nazwą dodatku
        getLogger(). nfo("Dodatek włączony i zaczepiony do AeroDesk! );
        
        // pobiera cały obiekt BotConfig
        getApi(). etConfig(); 
        
        // Szybki skrót wewnątrz dodatku do przechwytywania config
        getLogger(). nfo("Bieżący prefiks bota to: " + getConfig().prefiks;
    }
}
```

lub

```java
pakiet com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

klasa publiczna HelloWorldMain2 extends AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println("======================================");
        System.out. rintln("👋 ŚWIATA HELLO WŁĄCZONE! 👋");

        spróbuj {
            jeśli (getApi()! null && getApi(). etConfig() != null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // dbType zwraca to, co jest zaznaczone. MySQL
                System.out. rintln("Bot obecnie używa bazy danych: " + dbType);
            } else {
                System. ob rintln("API bota lub konfiguracja nie były jeszcze gotowe, ale dodatek załadowany! );
            }
        } chwyt (Exception e) {
            // To wydrukuje dokładny powód, jeśli coś pójdzie nie tak tutaj
            System. rr.println("Błąd odczytu konfiguracji w HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln("======================================");
    }

    @Override
    public void onDisable() {
        System. ut.println("🛑 Hello World2 Addon Shutting down!");
    }
}
```

###
