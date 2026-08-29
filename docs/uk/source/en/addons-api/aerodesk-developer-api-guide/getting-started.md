# З чого почати

Щоб отримати API для бота, вам необхідно мати в вашому `pom.xml`

Включити це до вашого проекту:

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

Ви можете знайти останній випуск [here](https://maven.plugins.avenvault.com/) під AeroDesk-API
