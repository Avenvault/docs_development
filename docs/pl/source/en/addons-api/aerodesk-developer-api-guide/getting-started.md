# Rozpoczęcie

Aby uzyskać API dla bota, musisz mieć w swoim `pom.xml`

Dołącz to do swojego projektu:

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

Najnowsze wydanie [here](https://maven.plugins.avenvault.com/) można znaleźć w AeroDesk-API
