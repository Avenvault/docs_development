# 基础 API

要连接到系统中，您的主类必须扩展 "AeroDeskAddon" 。 以下是基本的实施，以流畅的方式展示核心基本方法：

```java
包 com.example.myaddon;

导入 com.avenvault.discord.api。 演示文稿；

公共类 MyCustomAddon extends Aeroon AeroDeskAddon Advanced

    @Override
    public invent onEnable() public invent
        // 打印预置于addon名称
        getLogger() nfo("启用附加组件并将其绑定到AeroDesk! );
        
        // 获取整个BotConfig 对象
        getApi(). etConfig(); 
        
        // 插件内快速快捷键来抓取配置
        getLogger()。 nfo("当前机器人前缀为：" + getConfig().prefix)；
    }
}
```

或

```java
package com.example.myaddon;

import com.avenvault.discord.api.AeroDeskAddon;

public class HelloWorldMain2 extends AeroDeskAddon {

    @Override
    public void onEnable() {
        System.out.println("=================================");
        System.out.println("👋 HELLO WORLD ADDON ENABLED! 👋");

        try {
            if (getApi() != null && getApi().getConfig() != null) {
                String dbType = getApi().getConfig().database.activeDatabase;
                // dbType returns what is selected e.g MySQL
                System.out.println("The bot is currently using database: " + dbType);
            } else {
                System.out.println("The bot API or config was not ready yet, but addon loaded!");
            }
        } catch (Exception e) {
            // This will print the exact reason if something goes wrong here
            System.err.println("Error reading config in HelloWorld2:");
            e.printStackTrace();
        }

        System.out.println("=================================");
    }

    @Override
    public void onDisable() {
        System.out.println("🛑 Hello World2 Addon Shutting Down!");
    }
}
```

###
