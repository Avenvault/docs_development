# Dashboards & Incoming Webhooks (Inbound Traffic)

While some of our bots only use outbound connections, your bot requires inbound network configuration if it includes either of the following features:

1. A Web Dashboard: A control panel (usually running on Express.js or Flask) where users log in via a browser to configure the bot.
2. Voting Webhooks: Receiving real-time POST requests from bot list websites (like Top.gg) when a user upvotes your bot.

How to configure inbound traffic: If your bot hosts a web server, you _must_ open inbound ports on your host machine to allow users and webhooks to reach it.

1. Open Inbound Ports: Allow traffic on the port your web server uses (e.g., `8080` or `3000`).
   * _Linux (UFW):_ `sudo ufw allow 8080/tcp`
2. Set up a Reverse Proxy (Recommended): Instead of giving users an IP and port (e.g., `http://192.168.1.5:8080`), install a reverse proxy like Nginx or Apache.
   * Configure Nginx to listen on standard Port 443 (HTTPS) and route the traffic internally to your bot's local port (8080).
   * This allows you to attach a domain name (`dashboard.yourbot.com`) and an SSL certificate (via Let's Encrypt) to keep user data secure.
