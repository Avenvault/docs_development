# Database & API Whitelisting

Almost all modern Discord bots rely on an external database (MongoDB, MySQL, PostgreSQL) to store user data, or they fetch data from external APIs (like YouTube, Spotify, or OpenAI).

If your database is hosted on a different machine than your bot (e.g., MongoDB Atlas or a managed AWS database), you must whitelist the bot's IP address.

How to configure external database access:

1. Find the Public IPv4 Address of the machine hosting your Discord bot.
2. Log into your database provider's dashboard (e.g., MongoDB Atlas, AWS RDS).
3. Navigate to Network Access or Security Groups.
4. Add an inbound rule allowing connections from your bot's specific IP address.
5. _Note for dynamic IPs:_ If you are hosting the bot on a home network where the IP changes frequently, you may need to allow connections from anywhere (`0.0.0.0/0`), though this requires strong database passwords for security we recommended is what the database provider's limit on the password and be sure to save this to an note in BitWarden or an Password manager!

