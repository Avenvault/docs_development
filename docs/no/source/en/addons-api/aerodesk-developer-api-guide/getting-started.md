# Komme i gang

For å få API for boten må du ha i din `pom.xml`

Inkluder dette i prosjektet ditt:

```xml
    <repositories>
        <repository>
            <id>avenvault-discord</id>
            <url>https://maven.plugins.avenvault.com/discord/</url>
        </repository>
    </repositories>
    
    <dependencies>
        <dependency>
            <groupId>com.avenvault.discord</groupId>
            <artifactId>AeroDesk-API</artifactId>
            <version>1.0.3</version>      <!-- Change to latest version when an update is available  -->
            <scope>provided</scope>
        </dependency>
    </dependencies>
```

Du finner den siste utgivelsen [here](https://maven.plugins.avenvault.com/) under AeroDesk-API
