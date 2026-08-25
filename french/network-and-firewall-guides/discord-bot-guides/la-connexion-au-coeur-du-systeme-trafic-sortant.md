# La connexion au cœur du système (trafic sortant)

For a Discord bot to come online, send messages, and receive gateway events, the host machine must be allowed to make outbound connections to the internet.

Does my bot need port forwarding? No. Standard Discord bots do not require inbound port forwarding.

What you need to allow: Your VPS, container, or host machine's firewall must allow Outbound TCP Traffic on Port 443 (HTTPS) and Port 80 (HTTP).

If your host rigidly blocks outbound traffic (common on strict enterprise networks or school networks), the bot will fail to start and throw one of the following errors:

* `java.net.UnknownHostException` (Java)
* `Error: getaddrinfo ENOTFOUND discord.com` (Node.js)
* `WebSocket connection refused`

#### Comment résoudre le problème

Assurez-vous que le pare-feu de votre hôte (comme UFW sous Linux ou le pare-feu Windows Defender) autorise le trafic sortant. Chez la plupart des fournisseurs de VPS Linux classiques (Ubuntu, Debian), le trafic sortant est autorisé par défaut. Vous avez un doute ? Consultez la documentation correspondante [ici](../autoriser-le-port-443.md) !

