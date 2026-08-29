# API de base

Pour vous connecter au système, votre classe principale doit étendre `AeroDeskAddon`. Voici une implémentation de base démontrant les méthodes de base principales de manière fluide :

```java
paquet com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

la classe publique MyCustomAddon extends AeroDeskAddon {

    @Override
    public void onEnable() {
        // Affiche les messages de log personnalisés préfixés par le nom de l'extension
        getLogger(). nfo("Addon activé et branché sur AeroDesk! );
        
        // Récupère l'ensemble de l'objet BotConfig
        getApi(). et(); 
        
        // Un raccourci rapide dans l'addon pour récupérer la configuration
        getLogger(). nfo("Préfixe de bot actuel est: " + getConfig().prefix);
    }
}
```

ou

```java
paquet com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

la classe publique HelloWorldMain2 étend AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println("=========================================");
        System.out. rintln("👋 ADDON HELLO WORLD ACTIVÉ ! 👋");

        essayer {
            if (getApi() ! null && getApi(). etConfig() != null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // dbType retourne ce qui est sélectionné. MySQL
                System.out. rintln("Le bot utilise actuellement la base de données: " + dbType);
            } else {
                System. ut. rintln("The bot API or config was not ready yet, but addon loaded! );
            }
        } catch (Exception e) {
            // Ceci affichera la raison exacte si quelque chose ne va pas ici
            System. rr.println("Erreur de lecture de la configuration dans HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln ("=========================================");
    }

    @Override
    public void onDisable() {
        System. ut.println("🛑 Hello World2 Addon Shutting Down!");
    }

```

###
