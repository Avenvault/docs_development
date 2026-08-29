# Getting Started

In order to get the API for the bot you need to have in your `pom.xml`

Include this in your project:

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

You can find the latest release [here](https://maven.plugins.avenvault.com/) under AeroDesk-API
