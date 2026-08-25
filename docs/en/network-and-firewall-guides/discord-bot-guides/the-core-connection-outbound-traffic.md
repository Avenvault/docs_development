# The Core Connection (Outbound Traffic)

For a Discord bot to come online, send messages, and receive gateway events, the host machine must be allowed to make outbound connections to the internet.

Does my bot need port forwarding? No. Standard Discord bots do not require inbound port forwarding.

What you need to allow: Your VPS, container, or host machine's firewall must allow Outbound TCP Traffic on Port 443 (HTTPS) and Port 80 (HTTP).

If your host rigidly blocks outbound traffic (common on strict enterprise networks or school networks), the bot will fail to start and throw one of the following errors:

* `java.net.UnknownHostException` (Java)
* `Error: getaddrinfo ENOTFOUND discord.com` (Node.js)
* `WebSocket connection refused`

How to fix: Ensure your host firewall (like UFW or Windows Defender) allows outgoing traffic. On most standard Linux VPS providers (Ubuntu, Debian), outbound traffic is open by default. Unsure? Check out the document for it [here](https://plugins.avenvault.com/docs/network-and-firewall-guides/allowing-port-443)!

