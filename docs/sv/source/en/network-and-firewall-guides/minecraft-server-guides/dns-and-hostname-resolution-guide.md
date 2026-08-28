# DNS & Hostname Resolution Guide

If our plugins displays a `java.net.UnknownHostException` in the console during startup, your server is failing to translate our licensing server's domain name into an IP address.

This is an issue with your host's DNS resolver configuration.

### How to Fix DNS Resolution Issues

#### Changing Your DNS Resolvers (Linux)

You can force your server to use reliable, public DNS resolvers like Cloudflare (`1.1.1.1`) or Google (`8.8.8.8`).

1. Open your `resolv.conf` file:

    ```
    sudo nano /etc/resolv.conf
    ```
2. Add the following lines at the very top of the file:

    ```
    nameserver 1.1.1.1
    nameserver 8.8.8.8
    ```
3. Save and exit (Ctrl+O, Enter, Ctrl+X). Restart your Minecraft server.

#### Changing Your DNS Resolvers (Windows Server)

1. Open Control Panel > Network and Internet > Network and Sharing Center.
2. Click on your active connection and select Properties.
3. Select Internet Protocol Version 4 (TCP/IPv4) and click Properties.
4. Check Use the following DNS server addresses and enter:
   - Preferred: `1.1.1.1`
   - Alternate: `8.8.8.8`
5. Click OK and restart your Minecraft server.

