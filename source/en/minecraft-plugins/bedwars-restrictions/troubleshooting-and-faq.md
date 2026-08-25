---
icon: question
---

# Troubleshooting & FAQ

Q: My console says "FATAL: Invalid License Key" and the plugin disables itself.&#x20;

A: This means the RSA-256 cloud authentication rejected your key.

1. Check your `config.yml` to ensure there are no trailing spaces around your key.
2. Verify that your subscription/license has not expired on the premium portal.
3. Ensure you are using the exact format provided (e.g., 1234-5678-9012).



Q: The console says "License Server Unreachable" during startup.&#x20;

A: The plugin requires an active internet connection to verify its integrity. Ensure that your host/machine allows outbound connections on Port 443 (HTTPS) and that your firewall is not blocking traffic to our auth servers.

Q: Players are still able to build outside the arena boundaries!&#x20;

A: First, verify that the player in question is not an Administrator (OP) or does not have the `bwr.bypass` permission node. Second, double-check your `min` and `max` coordinates in `config.yml` to ensure the mathematical bounding box is drawn correctly (min values should always be lower than max values).

Q: Is this plugin compatible with ViaVersion/Geyser?&#x20;

A: Yes! Because BedwarsRestrictions handles bounding boxes at the server level, it is 100% compatible with bedrock players via Geyser and clients using different versions via ViaVersion.

_**Need further assistance?**_ [_**Contact us**_](https://plugins.avenvault.com/contact) _**with your license key (to verify) or join our discord and verify your license to get support!**_
