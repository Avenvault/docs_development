# Allowing Port 443

Our plugins licensing system requires active communication over Port 443 (HTTPS) to authenticate your license with our web servers. If your system firewall, cloud security group, or host blocks outbound connections on Port 443, the plugin will fail to load.

This guide provides step-by-step instructions to ensure Port 443 is unblocked on your host server.

### Windows Server / Windows OS

On Windows, Port 443 outbound traffic is usually open by default, but local firewall policies or anti-virus software can sometimes block it.

#### Method 1: Windows Defender Firewall (GUI)

1. Press `Win + R`, type `wf.msc`, and press Enter to open Windows Defender Firewall with Advanced Security.
2. Click on Outbound Rules in the left panel.
3. In the right panel, click New Rule...
4. Select Port and click Next.
5. Choose TCP, select Specific remote ports, and type `443`. Click Next.
6. Select Allow the connection and click Next.
7. Keep all profiles checked (Domain, Private, Public) and click Next.
8. Name the rule (e.g., `BedwarsRestrictions - Port 443 Outbound`) and click Finish.

#### Method 2: PowerShell (Administrator)

Open PowerShell as Administrator and run the following command to automatically create the outbound rule:

```
New-NetFirewallRule -DisplayName "Allow Outbound HTTPS 443" -Direction Outbound -Action Allow -Protocol TCP -RemotePort 443
```

### Linux (Ubuntu, Debian, CentOS, RHEL)

Most Linux dedicated servers or VPS instances utilize local firewalls such as `UFW` or `firewalld`.

#### 1. Ubuntu / Debian (`ufw`)

Check your current UFW status and allow outbound/inbound HTTPS traffic:

```
# Check UFW status
sudo ufw status

# Allow HTTPS (Port 443) traffic
sudo ufw allow 443/tcp
sudo ufw allow out 443/tcp

# Reload firewall rules
sudo ufw reload
```

#### 2. CentOS / RHEL / AlmaLinux (`firewalld`)

If your system uses `firewalld`:

```
# Allow HTTPS service permanently
sudo firewall-cmd --permanent --add-service=https

# Allow Port 443 TCP explicitly
sudo firewall-cmd --permanent --add-port=443/tcp

# Reload firewall settings
sudo firewall-cmd --reload
```

#### 3. Native `iptables`

If you manage raw `iptables` rules directly:

```
# Allow outbound TCP traffic on port 443
sudo iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# Save rules (varies by OS distribution)
sudo service iptables save
```

### macOS Server / macOS

If you are running a local test server on macOS, traffic can be allowed via System Settings or the Packet Filter (`pf`) tool.

#### Method 1: System Settings (GUI)

1. Open System Settings > Network > Firewall.
2. Click Options...
3. Ensure Block all incoming connections is OFF.
4. Ensure your Java binary (or Minecraft server terminal) is set to Allow incoming connections.

#### Method 2: Terminal (`pfctl`)

To allow traffic through the built-in macOS packet filter:

1. Open Terminal.
2. Check if `pf` is running:

    ```
    sudo pfctl -s info
    ```
3. To add a temporary pass rule for port 443:

    ```
    echo "pass out proto tcp to any port 443" | sudo pfctl -a custom -f -
    ```

### Cloud Hosting / VPS Providers

If you host your server on cloud providers (such as AWS, DigitalOcean, Linode, or Google Cloud), operating system firewalls are often supplemented by External Cloud Firewalls / Security Groups although normally its enabled by default or asks on creation of instance.

#### **Google Cloud Platform (GCP)**

1. Go to the **VPC network** section in your GCP Console by clicking `.` .
2. Click on **Firewall** in the left menu, then click **Create Firewall Rule**.
3. **Name:** `allow-https-outbound`
4. **Direction of traffic:** Select **Egress** (Outbound).
5. **Action on match:** Select **Allow**.
6. **Targets:** Select _Specified target tags_ and add the tag assigned to your VM (e.g., `allow-https`).
7. **Destination filter:** IPv4 ranges -> Set to `0.0.0.0/0`.
8. **Protocols and ports:** Check **TCP** and type `443`.
9. Click **Create**.

#### **AWS EC2**

1. Go to your **EC2 Dashboard** and click on your Instance.
2. Select the **Security** tab and click on your **Security Group**.
3. Click **Edit Outbound Rules** ( do not change Inbound rules).
4. Click **Add Rule**:
   - **Type:** HTTPS
   - **Protocol:** TCP
   - **Port Range:** 443
   - **Destination:** Anywhere-IPv4 (`0.0.0.0/0`)
5. Click **Save rules**.

#### **DigitalOcean**

1. Go to **Networking** > **Firewalls**.
2. Select the firewall attached to your Droplet.
3. Scroll down to **Outbound Rules** and click **Add Rule**.
4. Select **Secure Web (HTTPS)** from the dropdown (this automatically sets TCP Port 443 to All IPv4/IPv6).
5. Click **Save**.

#### **Linode (Akamai Connected Cloud)**

1. Go to the **Linode Cloud Manager** dashboard and select **Firewalls** from the left-hand navigation menu.
2. Click on the firewall attached to your Linode instance (or click **Create Firewall** if you haven’t set one up yet).
3. Select the **Outbound Rules** tab.
4. Click **Add Rule** and configure the settings:

- **Label**: `allow-https-outbound`
- **Type**: `HTTPS` (Selecting this automatically sets the Protocol to TCP and Port Range to 443)
- **Action**: `Accept`
- **Sources**: `All` (or `Anywhere-IPv4` / `0.0.0.0/0`)\
  Click **Save** on the rule drawer, then click **Save Changes** at the top right of the main page to apply the firewall configuration.

#### **Game Panel Hosts (Pterodactyl / Apex / Bisect)**

Most shared Minecraft hosts leave outbound Port 443 open by default. If you still encounter connection errors, contact your hosting provider's support team to verify that outbound HTTPS requests are not restricted by network proxies or panel firewalls.

### How to Test Port 443 Connectivity

To verify whether your server can reach external HTTPS services on Port 443, run one of the following diagnostic commands from your server terminal:

#### On Linux / macOS:

```
curl -v https://google.com
```

_If you see a successful connection response (even a 404 or JSON response), Port 443 outbound is fully functional._

#### On Windows (PowerShell):

```
Test-NetConnection -ComputerName google.com -Port 443
```

_If `TcpTestSucceeded : True` is returned, outbound Port 443 traffic is open._
