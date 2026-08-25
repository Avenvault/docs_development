# Local Environment Port Forwarding & Tunnels

If you are a developer or server owner testing our plugins on a local home network before deploying to a public host, you may need to expose your server to the internet to verify gameplay with friends.

### Option A: Router Port Forwarding

1. Log into your router's admin panel (typically `192.168.1.1` or `10.0.0.1`).
2. Locate the Port Forwarding or Virtual Servers section.
3. Create a new rule pointing to the local IPv4 address of your computer.
4. Set both the Internal Port and External Port to `25565` (or whatever port your server runs on).
5. Set the protocol to TCP/UDP.
6. Save and apply. Players can now connect using your public IP address.

### Option B: Tunneling Services (No Port Forwarding Required)

If you cannot access your router or your ISP uses Carrier-Grade NAT (CGNAT), you can use tunneling services to expose your local server.

* [Playit.gg](https://playit.gg): A free global proxy specifically designed for gaming. Download the agent, run it alongside your server, and it provides a public IP and port automatically.
* [Ngrok](https://ngrok.com/): A generalized tunneling tool.

```
ngrok tcp 25565
```

_(Note: Ngrok's free tier assigns a randomized port every time you restart it.)_

