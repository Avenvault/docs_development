# Tillate port 443

Lisensieringssystemet for våre utvidelser krever aktiv kommunikasjon via port 443 (HTTPS) for å autentisere lisensen din mot våre webservere. Hvis systemets brannmur, skysikkerhetsgruppe eller vert blokkerer utgående tilkoblinger på port 443, vil ikke plugin-modulen kunne lastes inn.

Denne veiledningen gir trinnvise instruksjoner for å sikre at port 443 er åpnet på vertsserveren din.

### Windows Server / Windows OS

I Windows er utgående trafikk på port 443 vanligvis åpen som standard, men lokale brannmurregler eller antivirusprogramvare kan noen ganger blokkere den.

#### Metode 1: Windows Defender-brannmur (GUI)

1. Trykk på `Win + R`, skriv inn `wf.msc` og trykk på Enter for å åpne Windows Defender-brannmur med avansert sikkerhet.
2. Klikk på Utgående regler i panelet til venstre.
3. Klikk på Ny regel... i panelet til høyre.
4. Velg port og klikk på Neste.
5. Velg TCP, velg spesifikke eksterne porter, og skriv inn `443`. Klikk på Neste.
6. Velg «Tillat tilkoblingen» og klikk på «Neste».
7. La alle profiler være valgt (Domene, Privat, Offentlig) og klikk på Neste.
8. Gi regelen et navn (f.eks. `Plugin - Port 443 Outbound`) og klikk på Fullfør.

#### Metode 2: PowerShell (administrator)

Åpne PowerShell som administrator og kjør følgende kommando for å opprette utgående regel automatisk:

```
New-NetFirewallRule -DisplayName "Tillat utgående HTTPS 443" -Retning utgående -Handling Tillat -Protokoll TCP -Eksternport 443
```

### Linux (Ubuntu, Debian, CentOS, RHEL)

De fleste dedikerte Linux-servere eller VPS-instanser benytter lokale brannmurer som `UFW` eller `firewalld`.

#### 1. Ubuntu / Debian (`ufw`)

Sjekk gjeldende UFW-status og tillat utgående/innkommende HTTPS-trafikk:

```
# Sjekk UFW-status
sudo ufw status

# Tillat HTTPS-trafikk (port 443)
sudo ufw allow 443/tcp
sudo ufw allow out 443/tcp

# Last inn brannmurregler på nytt
sudo ufw reload
```

#### 2. CentOS / RHEL / AlmaLinux (`firewalld`)

Hvis systemet ditt bruker `firewalld`:

```
# Tillat HTTPS-tjeneste permanent
sudo firewall-cmd --permanent --add-service=https

# Tillat port 443 TCP eksplisitt
sudo firewall-cmd --permanent --add-port=443/tcp

# Last inn brannmurinnstillinger på nytt
sudo firewall-cmd --reload
```

#### 3. Innebygd `iptables`

Hvis du administrerer rå `iptables`-regler direkte:

```
# Tillat utgående TCP-trafikk på port 443
sudo iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# Lagre regler (varierer avhengig av OS-distribusjon)
sudo service iptables save
```

### macOS Server / macOS

Hvis du kjører en lokal testserver på macOS, kan trafikk tillates via Systeminnstillinger eller verktøyet Packet Filter (`pf`).

#### Metode 1: Systeminnstillinger (GUI)

1. Åpne Systeminnstillinger > Nettverk > Brannmur.
2. Klikk på Alternativer...
3. Sørg for at «Blokker alle innkommende tilkoblinger» er slått av.
4. Sørg for at Java-kjørefilen (eller terminalen for Minecraft-serveren) er innstilt til å tillate innkommende tilkoblinger.

#### Metode 2: Terminal (`pfctl`)

For å tillate trafikk gjennom det innebygde pakkefilteret i macOS:

1. Åpne Terminal.
2. Sjekk om `pf` kjører:

    ```
    sudo pfctl -s info
    ```
3. For å legge til en midlertidig tillatelsesregel for port 443:

    ```
    echo "send proto tcp til hvilken som helst port 443" | sudo pfctl -a custom -f -
    ```

### Leverandører av skyhosting / VPS

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

De fleste leverandører av delt Minecraft-hosting lar utgående port 443 være åpen som standard. Hvis du fortsatt opplever tilkoblingsfeil, bør du kontakte kundestøtten hos leverandøren av webhotell for å bekrefte at utgående HTTPS-forespørsler ikke blokkeres av nettverksproxyer eller brannmurer i kontrollpanelet.

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
