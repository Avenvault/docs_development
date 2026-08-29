# API Base

Para conectar con el sistema, su clase principal debe extender `AeroDeskAddon`. Aquí hay una implementación básica que demuestra los métodos básicos de una manera fluida:

```java
paquete com.example.myaddon;

importar com.avenvault.discord.api. eroDesk;

public class MyCustomAddon extends AeroDeskAddon {

    @Override
    public void onEnable() {
        // Imprime mensajes de registro personalizados con el prefijo
        getLogger(). nfo("¡Complemento activado y conectado al AeroDesk! );
        
        // Obtiene todo el objeto BotConfig
        getApi(). etConfig(); 
        
        // Un atajo rápido dentro del complemento para obtener la configuración
        getLogger(). nfo("Current bot prefix is: " + getConfig().prefix);
    }
}
```

o

```java
paquete com.example.myaddon;

importar com.avenvault.discord.api. eroDesk;

public class HelloWorldMain2 extends AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println("=================================");
        System.out. rintln("👋 ¡HELLO WORLD ADDON ENABLADO! 👋");

        prueba {
            if (getApi() ! null && getApi(). etConfig() != null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // dbType devuelve lo que es seleccionado e. MySQL
                System.out. rintln("El bot está usando actualmente la base de datos: " + dbType);
            } else {
                System. ut. rintln("El bot API o configuración no estaba listo todavía, pero el addon cargado! );
            }
        } catch (Exception e) {
            // Esto imprimirá la razón exacta si algo sale mal aquí
            System. rr.println("Error leyendo configuración en HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln("=========================================");
    }

    @Override
    public void onDisable() {
        System. ut.println("🛑 Hola World2 Addon Cerrando hacia abajo!");
    }
}
```

###
