# Freigabe von Port 443

Das Lizenzsystem unserer Plugins benötigt eine aktive Verbindung über Port 443 (HTTPS). Damit wird Ihre Lizenz bei unseren Webservern authentifiziert. Blockiert Ihre System-Firewall, Cloud-Sicherheitsgruppe oder Ihr Hoster ausgehende Verbindungen auf Port 443, lädt das Plugin nicht.

Diese Anleitung erklärt Schritt für Schritt, wie Sie Port 443 auf Ihrem Hostserver freigeben.

### Windows Server / Windows

Unter Windows ist ausgehender Datenverkehr über Port 443 normalerweise standardmäßig erlaubt. Lokale Firewallrichtlinien oder Antivirensoftware können ihn jedoch blockieren.

#### Methode 1: Windows Defender Firewall (GUI)

1. Drücken Sie `Win + R`, geben Sie `wf.msc` ein und drücken Sie die Eingabetaste. Dadurch öffnen Sie die Windows Defender Firewall mit erweiterter Sicherheit.
2. Klicken Sie im linken Bereich auf **Ausgehende Regeln**.
3. Klicken Sie im rechten Bereich auf **Neue Regel...**.
4. Wählen Sie **Port** und klicken Sie auf **Weiter**.
5. Wählen Sie **TCP**, dann **Bestimmte Remoteports**, und geben Sie `443` ein. Klicken Sie auf **Weiter**.
6. Wählen Sie **Verbindung zulassen** und klicken Sie auf **Weiter**.
7. Lassen Sie alle Profile aktiviert: **Domäne**, **Privat** und **Öffentlich**. Klicken Sie auf **Weiter**.
8. Benennen Sie die Regel, zum Beispiel `BedwarsRestrictions - Port 443 Outbound`, und klicken Sie auf **Fertig stellen**.

#### Methode 2: PowerShell (Administrator)

Öffnen Sie PowerShell als Administrator. Führen Sie dann diesen Befehl aus, um die ausgehende Regel automatisch zu erstellen:

```
New-NetFirewallRule -DisplayName "Allow Outbound HTTPS 443" -Direction Outbound -Action Allow -Protocol TCP -RemotePort 443
```

### Linux (Ubuntu, Debian, CentOS, RHEL)

Die meisten dedizierten Linux-Server und VPS-Instanzen nutzen lokale Firewalls wie `UFW` oder `firewalld`.

#### 1. Ubuntu / Debian (`ufw`)

Prüfen Sie den Status von UFW. Erlauben Sie dann ein- und ausgehenden HTTPS-Datenverkehr:

```
# UFW-Status prüfen
sudo ufw status

# HTTPS-Datenverkehr über Port 443 erlauben
sudo ufw allow 443/tcp
sudo ufw allow out 443/tcp

# Firewallregeln neu laden
sudo ufw reload
```

#### 2. CentOS / RHEL / AlmaLinux (`firewalld`)

Wenn Ihr System `firewalld` verwendet:

```
# HTTPS-Dienst dauerhaft erlauben
sudo firewall-cmd --permanent --add-service=https

# TCP-Port 443 ausdrücklich erlauben
sudo firewall-cmd --permanent --add-port=443/tcp

# Firewalleinstellungen neu laden
sudo firewall-cmd --reload
```

#### 3. Natives `iptables`

Wenn Sie rohe `iptables`-Regeln direkt verwalten:

```
# Ausgehenden TCP-Datenverkehr über Port 443 erlauben
sudo iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# Regeln speichern (je nach Linux-Distribution)
sudo service iptables save
```

### macOS Server / macOS

Wenn Sie einen lokalen Testserver unter macOS betreiben, können Sie Datenverkehr über die Systemeinstellungen oder Packet Filter (`pf`) erlauben.

#### Methode 1: Systemeinstellungen (GUI)

1. Öffnen Sie **Systemeinstellungen** → **Netzwerk** → **Firewall**.
2. Klicken Sie auf **Optionen...**.
3. Stellen Sie sicher, dass **Alle eingehenden Verbindungen blockieren** deaktiviert ist.
4. Stellen Sie sicher, dass Ihre Java-Binärdatei oder das Minecraft-Server-Terminal eingehende Verbindungen erlauben darf.

#### Methode 2: Terminal (`pfctl`)

So erlauben Sie Datenverkehr über den integrierten macOS-Paketfilter:

1. Öffnen Sie Terminal.
2.  Prüfen Sie, ob `pf` läuft:

    ```
    sudo pfctl -s info
    ```
3.  Fügen Sie eine temporäre Durchlassregel für Port 443 hinzu:

    ```
    echo "pass out proto tcp to any port 443" | sudo pfctl -a custom -f -
    ```

### Cloud-Hosting / VPS-Anbieter

Bei Cloud-Anbietern wie AWS, DigitalOcean, Linode oder Google Cloud ergänzen externe Cloud-Firewalls oder Sicherheitsgruppen oft die Betriebssystem-Firewall. Ausgehender HTTPS-Datenverkehr ist normalerweise bereits erlaubt oder wird beim Erstellen der Instanz abgefragt.

#### **Google Cloud Platform (GCP)**

1. Öffnen Sie in der GCP Console den Bereich **VPC network**.
2. Klicken Sie im linken Menü auf **Firewall** und dann auf **Create Firewall Rule**.
3. **Name:** `allow-https-outbound`
4. **Direction of traffic:** Wählen Sie **Egress** (ausgehend).
5. **Action on match:** Wählen Sie **Allow**.
6. **Targets:** Wählen Sie _Specified target tags_. Fügen Sie das Ihrer VM zugewiesene Tag hinzu, zum Beispiel `allow-https`.
7. **Destination filter:** Wählen Sie IPv4-Bereiche. Setzen Sie den Wert auf `0.0.0.0/0`.
8. **Protocols and ports:** Aktivieren Sie **TCP** und geben Sie `443` ein.
9. Klicken Sie auf **Create**.

#### **AWS EC2**

1. Öffnen Sie Ihr **EC2 Dashboard** und wählen Sie Ihre Instanz aus.
2. Öffnen Sie den Tab **Security** und klicken Sie auf Ihre **Security Group**.
3. Klicken Sie auf **Edit Outbound Rules**. Ändern Sie keine eingehenden Regeln.
4. Klicken Sie auf **Add Rule**:
   * **Type:** HTTPS
   * **Protocol:** TCP
   * **Port Range:** 443
   * **Destination:** Anywhere-IPv4 (`0.0.0.0/0`)
5. Klicken Sie auf **Save rules**.

#### **DigitalOcean**

1. Öffnen Sie **Networking** → **Firewalls**.
2. Wählen Sie die Firewall aus, die Ihrem Droplet zugeordnet ist.
3. Scrollen Sie zu **Outbound Rules** und klicken Sie auf **Add Rule**.
4. Wählen Sie **Secure Web (HTTPS)** aus der Liste. Dadurch wird TCP-Port 443 automatisch für alle IPv4- und IPv6-Adressen festgelegt.
5. Klicken Sie auf **Save**.

#### **Linode (Akamai Connected Cloud)**

1. Öffnen Sie das Dashboard von **Linode Cloud Manager**. Wählen Sie im linken Navigationsmenü **Firewalls**.
2. Klicken Sie auf die Firewall Ihrer Linode-Instanz. Klicken Sie auf **Create Firewall**, falls noch keine Firewall existiert.
3. Öffnen Sie den Tab **Outbound Rules**.
4. Klicken Sie auf **Add Rule** und konfigurieren Sie die Einstellungen:

* **Label**: `allow-https-outbound`
* **Type**: `HTTPS` — dadurch werden **Protocol** auf TCP und **Port Range** auf 443 gesetzt.
* **Action**: `Accept`
* **Sources**: `All`, alternativ `Anywhere-IPv4` oder `0.0.0.0/0`\
  Klicken Sie im Regelbereich auf **Save**. Klicken Sie dann oben rechts auf **Save Changes**, um die Firewallkonfiguration anzuwenden.

#### **Game-Panel-Hoster (Pterodactyl / Apex / Bisect)**

Die meisten Shared-Minecraft-Hoster erlauben ausgehenden Datenverkehr über Port 443 standardmäßig. Treten weiterhin Verbindungsfehler auf, kontaktieren Sie den Support Ihres Hosters. Lassen Sie prüfen, ob Netzwerk-Proxys oder Panel-Firewalls ausgehende HTTPS-Anfragen einschränken.

### Verbindung über Port 443 testen

Führen Sie einen der folgenden Diagnosebefehle im Serverterminal aus. Damit prüfen Sie, ob Ihr Server externe HTTPS-Dienste über Port 443 erreicht.

#### Unter Linux / macOS

```
curl -v https://google.com
```

_Eine erfolgreiche Verbindungsantwort bestätigt, dass ausgehender Datenverkehr über Port 443 funktioniert. Auch eine 404- oder JSON-Antwort gilt als erfolgreich._

#### Unter Windows (PowerShell)

```
Test-NetConnection -ComputerName google.com -Port 443
```

_Wird `TcpTestSucceeded : True` zurückgegeben, ist ausgehender Datenverkehr über Port 443 erlaubt._
