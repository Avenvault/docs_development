# Comenzando

Para obtener la API para el bot necesitas tener en tu `pom.xml`

Incluye esto en tu proyecto:

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

Puede encontrar la última versión [here](https://maven.plugins.avenvault.com/) en AeroDesk-API
