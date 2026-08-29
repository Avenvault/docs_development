# Base API

Koukkuaksesi järjestelmään pääluokan täytyy ulottaa `AeroDeskAddon`. Tässä on perustavanlaatuinen täytäntöönpano osoittaa ydin perusmenetelmiä nestemäisellä tavalla:

```java
package com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

public class MyCustomAddon extends AeroDeskAddon {

    @Override
    public void onEnable() {
        // Tulostaa mukautettuja lokiviestejä etukäteen lisäosan nimellä
        getLogger(). nfo("Addon käytössä ja koukussa AeroDeskiin! );
        
        // Hae koko pullonConfig objekti
        getApi(). etConfig(); 
        
        // Pikakuvake lisäosan sisällä napataksesi config
        getLogger(). nfo("Nykyinen botin etuliite on: " + getConfig().prefix);
    }
}
```

tai

```java
package com.example.myaddon;

import com.avenvault.discord.api. eroDeskAddon;

public class HelloWorldMain2 extends AeroDeskAddon {

    @Override
    public void onEnable() {
        System. ut.println("================================");
        System.out. rintln ("👋 HELLO WORLD ADDON ENABLED! 👋");

        kokeile {
            jos (getApi() ! null &getApi(). etConfig() != null) {
                String dbType = getApi(). etConfig().database.activeDatabase;
                // dbType palauttaa mitä on valittu e. MySQL
                System.out. rintln("Botti käyttää tällä hetkellä tietokantaa: " + dbType);
            } muu {
                System. uut. rintln("Botti API tai config ei ollut vielä valmis, mutta lisäosa ladattu! );
            }
        } saalis (Exception e) {
            // Tämä tulostaa tarkan syyn jos jotain menee pieleen tässä
            System. rr.println ("Virhe luettaessa config HelloWorld2:");
            e. rintStackTrace();
        }

        System.out. rintln ("=====================================");
    }

    @Override
    public void onDisable() {
        System. ut.println ("🛑 Hei World2 Addon Shutting Down!");
    }
}
```

###
