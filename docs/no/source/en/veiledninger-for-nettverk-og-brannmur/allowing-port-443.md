---
tags:
  - guides
  - discord
  - minecraft
---

# Tillate port 443

Lisensieringssystemet til pluginet vårt krever aktiv kommunikasjon over port 443 (HTTPS) for å autentisere lisensen din med webserverne våre. Hvis systemets brannmur, sky-sikkerhetsgruppe eller vert blokkerer utgående tilkoblinger på port 443, vil ikke pluginet laste inn.

Denne guiden gir trinnvise instruksjoner for å sikre at port 443 er åpnet på vertsserveren din.

### Windows Server / Windows OS

På Windows er utgående trafikk på port 443 vanligvis åpen som standard, men lokale brannmurregler eller antivirusprogramvare kan noen ganger blokkere den.

#### Metode 1: Windows Defender Brannmur (GUI)

1. Trykk på Win + R, skriv `wf.msc` og trykk Enter for å åpne Windows Defender-brannmur med avansert sikkerhet.
2. Klikk på Utgående regler (Outbound Rules) i venstre panel.
3. I høyre panel klikker du på Ny regel... (New Rule...)
4. Velg Port og klikk Neste.
5. Velg TCP, velg Spesifikke eksterne porter (Specific remote ports), og skriv `443`. Klikk Neste.
6. Velg Tillat tilkoblingen (Allow the connection) og klikk Neste.
7. Hold alle profiler avkrysset (Domene, Privat, Offentlig) og klikk Neste.
8. Gi regelen et navn (f.eks. `BedwarsRestrictions - Port 443 Outbound`) og klikk Fullfør.

#### Metode 2: PowerShell (Administrator)

Åpne PowerShell som Administrator og kjør følgende kommando for automatisk å opprette den utgående regelen:

```
New-NetFirewallRule -DisplayName "Allow Outbound HTTPS 443" -Direction Outbound -Action Allow -Protocol TCP -RemotePort 443
```

### Linux (Ubuntu, Debian, CentOS, RHEL)

De fleste dedikerte Linux-servere eller VPS-instanser bruker lokale brannmurer som UFW eller firewalld.

#### 1. Ubuntu / Debian (ufw)

Sjekk gjeldende UFW-status og tillat utgående/innkommende HTTPS-trafikk:

```
# Sjekk UFW-status
sudo ufw status

# Tillat HTTPS-trafikk (port 443)
sudo ufw allow 443/tcp
sudo ufw allow out 443/tcp

# Last inn brannmurreglene på nytt
sudo ufw reload
```

#### 2. CentOS / RHEL / AlmaLinux (firewalld)

Hvis systemet ditt bruker firewalld:

```
# Tillat HTTPS-tjenesten permanent
sudo firewall-cmd --permanent --add-service=https

# Tillat port 443 TCP eksplisitt
sudo firewall-cmd --permanent --add-port=443/tcp

# Last inn brannmurinnstillingene på nytt
sudo firewall-cmd --reload
```

#### 3. Native iptables

Hvis du administrerer rå iptables-regler direkte:

```
# Tillat utgående TCP-trafikk på port 443
sudo iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# Lagre regler (varierer mellom ulike OS-distribusjoner)
sudo service iptables save
```

### macOS Server / macOS

Hvis du kjører en lokal testserver på macOS, kan trafikk tillates via Systeminnstillinger eller Packet Filter (pf)-verktøyet.

#### Metode 1: Systeminnstillinger (GUI)

1. Åpne Systeminnstillinger (System Settings) > Nettverk (Network) > Brannmur (Firewall).
2. Klikk på Alternativer... (Options...)
3. Forsikre deg om at Blokker alle innkommende tilkoblinger (Block all incoming connections) er AV.
4. Forsikre deg om at Java-binæren din (eller Minecraft-serverterminalen) er satt til Tillat innkommende tilkoblinger (Allow incoming connections).

#### Metode 2: Terminal (pfctl)

Slik tillater du trafikk gjennom det innebygde macOS-pakkefilteret:

1. Åpne Terminal.
2. Sjekk om pf kjører:

```
sudo pfctl -s info
```

3. Legg til en midlertidig tillatelsesregel for port 443:

```
echo "pass out proto tcp to any port 443" | sudo pfctl -a custom -f -
```

### Skyhosting / VPS-leverandører

Hvis du hoster serveren din hos skyleverandører (som AWS, DigitalOcean, Linode eller Google Cloud), blir operativsystemets brannmurer ofte supplert av eksterne skybrannmurer / sikkerhetsgrupper (selv om det normalt er aktivert som standard eller forespørres ved oppretting av instans).

#### Google Cloud Platform (GCP)

1. Gå til VPC-nettverk-seksjonen i GCP-konsollen din.
2. Klikk på Brannmur (Firewall) i venstre meny, og klikk deretter på Opprett brannmurregel (Create Firewall Rule).
3. Navn: `allow-https-outbound`
4. Retning for trafikk (Direction of traffic): Velg Utgående (Egress).
5. Handling ved treff (Action on match): Velg Tillat (Allow).
6. Mål (Targets): Velg Angitte måletagger (Specified target tags) og legg til taggen som er tilordnet den virtuelle maskinen din (f.eks. `allow-https`).
7. Destinasjonsfilter (Destination filter): IPv4-områder -> Sett til `0.0.0.0/0`.
8. Protokoller og porter (Protocols and ports): Kryss av for TCP og skriv `443`.
9. Klikk Opprett (Create).

#### AWS EC2

1. Gå til EC2-dashbordet ditt og klikk på Instansen din.
2. Velg Sikkerhet (Security)-fanen og klikk på Sikkerhetsgruppen din (Security Group).
3. Klikk Rediger utgående regler (Edit Outbound Rules) (ikke endre innkommende regler).
4. Klikk Legg til regel (Add Rule):
   * Type: HTTPS
   * Protokoll: TCP
   * Portområde: 443
   * Destinasjon: Hvor som helst-IPv4 (Anywhere-IPv4 / 0.0.0.0/0)
5. Klikk Lagre regler (Save rules).

#### DigitalOcean

1. Gå til Nettverk (Networking) > Brannmurer (Firewalls).
2. Velg brannmuren som er knyttet til Dropletten din.
3. Rull ned til Utgående regler (Outbound Rules) og klikk Legg til regel (Add Rule).
4. Velg Secure Web (HTTPS) fra nedtrekksmenyen (dette setter automatisk TCP-port 443 til Alle IPv4/IPv6).
5. Klikk Lagre (Save).

#### Linode (Akamai Connected Cloud)

1. Gå til Linode Cloud Manager-dashbordet og velg Brannmurer (Firewalls) fra navigasjonsmenyen til venstre.
2. Klikk på brannmuren som er knyttet til Linode-instansen din (eller klikk _Opprett brannmur_ hvis du ikke har satt opp en ennå).
3. Velg fanen Utgående regler (Outbound Rules).
4. Klikk Legg til regel (Add Rule) og konfigurer innstillingene:
   * Etikett (Label): `allow-https-outbound`
   * Type: HTTPS (Dette setter automatisk protokoll til TCP og portområde til 443)
   * Handling (Action): Godta (Accept)
   * Kilder (Sources): Alle (All) eller Anywhere-IPv4 / `0.0.0.0/0`
5. Klikk Lagre på regelskuffen, og klikk deretter Lagre endringer (Save Changes) øverst til høyre på hovedsiden for å aktivere brannmurkonfigurasjonen.

### Spillpanelverter (Pterodactyl / Apex / Bisect)

De fleste delte Minecraft-verter lar utgående port 443 være åpen som standard. Hvis du fremdeles opplever tilkoblingsfeil, kan du kontakte hostingleverandørens supportteam for å bekrefte at utgående HTTPS-forespørsler ikke er begrenset av nettverksproxyer eller panelbrannmurer.

### Slik tester du tilkobling til port 443

For å bekrefte om serveren din kan nå eksterne HTTPS-tjenester på port 443, kan du kjøre en av følgende diagnostiske kommandoer fra serverterminalen din:

På Linux / macOS:

```
curl -v https://google.com
```

Hvis du ser et vellykket tilkoblingssvar (selv en 404- eller JSON-respons), fungerer utgående port 443 som den skal.

På Windows (PowerShell):

```
Test-NetConnection -ComputerName google.com -Port 443
```

Hvis `TcpTestSucceeded : True` returneres, er utgående trafikk på port 443 åpen.
