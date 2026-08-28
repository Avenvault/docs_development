---
icon: desktop-arrow-down
---

# Installation & Deployment Guide

Getting the Enterprise Ticket System up and running on your host machine (VPS, Dedicated Server, or Pterodactyl Panel) is a straightforward process. Follow these steps carefully to ensure a smooth deployment.

#### 📋 Prerequisites

Before you begin, ensure your hosting environment has the following installed:

- Java 17 or higher (Required for modern JDA versions).
- A database solution (MongoDB cluster, SQL database, or local storage access for JSON).
- A Discord Bot Token (obtained from the [Discord Developer Portal](https://www.google.com/search?q=https://discord.com/developers/applications)).

#### Step 1: Discord Application Setup

1. Go to the Discord Developer Portal and create a New Application.
2. Navigate to the Bot tab and click Add Bot.
3. Critical: Select Bot and scroll down to Privileged Gateway Intents and enable:
   - `Server Members Intent` (Needed for checking roles).
   - `Message Content Intent` (Needed for FAQ keyword detection).
4. Save your changes and copy your Bot Token. Keep this secret!
5. Invite the bot to your server by going to OAuth2 and scroll down to the OAuth2 URL Generator. Make sure you check both `bot` and `applications.commands` (required for Slash Commands), check `Administrator` under General Permissions and paste in the browser the URL that is provided under Generated URL.

#### Step 2: Server Preparation

1. Create a new folder on your host machine for the bot (e.g., `TicketBot`).
2. Download the latest release and place it inside the folder.
3. Run the bot for the first time to generate the configuration files:

   <pre><code>java -jar <a data-footnote-ref href="#user-content-fn-1">[NAME]</a>.jar
   </code></pre>
4. The bot will automatically shut down and inform you that a `config.yml` has been generated.

#### Step 3: Configuration

1. Open the newly generated `config.yml`.
2. Paste your Bot Token and your personal Discord Owner ID.
3. Configure your Database URI (if using MongoDB or SQL).
4. Fill out your server-specific settings, including Role IDs, Channel IDs, and your Category configurations (refer to the [Configuration Guide](https://www.google.com/search?q=%23) for details).
5. Save the file.

#### Step 4: Final Boot

Start the bot again using your preferred startup script, `screen`, or Pterodactyl panel:

<pre><code>java -Xms1G -Xmx2G -jar <a data-footnote-ref href="#user-content-fn-1">[NAME]</a>.jar
</code></pre>

_If configured correctly, the console will log a successful database connection and confirm that your Slash Commands have been registered globally._

[^1]: Change this to the name of the jar
