---
icon: question
---

# Frequently Asked Questions (FAQ)

Here are the most common issues server administrators run into and how to solve them.

#### Setup & Configuration

Q: How do I find Role IDs and Channel IDs for the config?&#x20;

A: You need to enable Developer Mode in Discord.

1. Go to Discord Settings > Advanced > Toggle Developer Mode on.
2. Right-click any role, channel, or user, and click Copy Channel ID or Copy Role ID at the bottom of the menu.

Q: I invited the bot, but I don't see `/ticketpanel` or `/stats`?&#x20;

A: Slash commands require specific scopes to register.

1. Ensure you invited the bot with the `applications.commands` scope checked in the OAuth2 URL generator.
2. Kick the bot and re-invite it with the correct URL. Note: You can try pressing F5 but global slash commands can sometimes take up to an hour to sync across all Discord servers natively, though they usually appear instantly.

#### 🛠️ Functionality & Errors

Q: The bot throws a `MongoTimeoutException` in the console and crashes.&#x20;

A: This means the bot cannot reach your MongoDB database.

* Check your `config.yml` to ensure the `database.uri` is formatted correctly.
* If you are using MongoDB Atlas (Cloud), ensure you have whitelisted your server's IP address (or set it to `0.0.0.0/0` to allow all IPs) in the Network Access tab.

Q: When a staff member claims a ticket, the channel doesn't lock down!&#x20;

A: This is almost always a Discord role hierarchy or permission issue.

1. Ensure `enableClaimRemoval: true` is set in your configuration for that category.
2. Ensure the Bot's highest role is placed above the staff roles in your Discord Server Settings. The bot cannot remove permissions from roles that are higher than itself.
3. Ensure the bot has the `Manage Channels` and `Manage Roles` permissions but `Administrator` permission is recommended.

Q: Why aren't the HTML transcripts generating a link?

A: The bot uploads the generated HTML file directly to Discord's CDN via the `logsChannelId` specified in your config. If the bot does not have permission to `Attach Files` or `Send Messages` in that specific hidden log channel, the upload will fail, and no link can be generated. Check the channel permissions!
