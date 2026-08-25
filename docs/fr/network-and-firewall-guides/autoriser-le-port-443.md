# Autoriser le port 443

Notre système de licence de plugins nécessite une communication active via le port 443 (HTTPS) pour authentifier votre licence auprès de nos serveurs web. Si le pare-feu de votre système, le groupe de sécurité cloud ou votre hébergeur bloque les connexions sortantes sur le port 443, le plugin ne pourra pas se charger.

Ce guide fournit des instructions étape par étape pour vous assurer que le port 443 est débloqué sur votre serveur hôte.

#### Windows Server / Windows OS

Sur Windows, le trafic sortant du port 443 est généralement ouvert par défaut, mais les politiques de pare-feu locales ou les logiciels antivirus peuvent parfois le bloquer.

**Méthode 1 : Pare-feu Windows Defender (GUI)**

1. Appuyez sur Win + R, tapez `wf.msc` et appuyez sur Entrée pour ouvrir le Pare-feu Windows Defender avec fonctions avancées de sécurité.
2. Cliquez sur Règles de trafic sortant dans le panneau de gauche.
3. Dans le panneau de droite, cliquez sur Nouvelle règle...
4. Sélectionnez Port et cliquez sur Suivant.
5. Choisissez TCP, sélectionnez Ports distants spécifiques, et tapez `443`. Cliquez sur Suivant.
6. Sélectionnez Autoriser la connexion et cliquez sur Suivant.
7. Conservez tous les profils cochés (Domaine, Privé, Public) et cliquez sur Suivant.
8. Nommez la règle (par ex., _BedwarsRestrictions - Port 443 Outbound_) et cliquez sur Terminer.

**Méthode 2 : PowerShell (Administrateur)**

Ouvrez PowerShell en tant qu'administrateur et exécutez la commande suivante pour créer automatiquement la règle de sortie :

```
New-NetFirewallRule -DisplayName "Allow Outbound HTTPS 443" -Direction Outbound -Action Allow -Protocol TCP -RemotePort 443
```

#### Linux (Ubuntu, Debian, CentOS, RHEL)

La plupart des serveurs dédiés Linux ou des instances VPS utilisent des pare-feu locaux tels que UFW ou firewalld.

**1. Ubuntu / Debian (ufw)**

Vérifiez le statut actuel de votre UFW et autorisez le trafic HTTPS sortant/entrant :

```
# Vérifier le statut de UFW
sudo ufw status

# Autoriser le trafic HTTPS (Port 443)
sudo ufw allow 443/tcp
sudo ufw allow out 443/tcp

# Recharger les règles du pare-feu
sudo ufw reload
```

**2. CentOS / RHEL / AlmaLinux (firewalld)**

Si votre système utilise `firewalld` :

```
# Autoriser le service HTTPS de façon permanente
sudo firewall-cmd --permanent --add-service=https

# Autoriser explicitement le port 443 TCP
sudo firewall-cmd --permanent --add-port=443/tcp

# Recharger les paramètres du pare-feu
sudo firewall-cmd --reload
```

**3. iptables natif**

Si vous gérez directement des règles iptables brutes :

```
# Autoriser le trafic TCP sortant sur le port 443
sudo iptables -A OUTPUT -p tcp --dport 443 -j ACCEPT

# Sauvegarder les règles (varie selon la distribution de l'OS)
sudo service iptables save
```

#### macOS Server / macOS

Si vous exécutez un serveur de test local sur macOS, le trafic peut être autorisé via les Réglages Système ou l'outil Packet Filter (`pf`).

**Méthode 1 : Réglages Système (GUI)**

1. Ouvrez Réglages système > Réseau > Pare-feu.
2. Cliquez sur Options...
3. Assurez-vous que l'option Bloquer toutes les connexions entrantes est DÉSACTIVÉE.
4. Assurez-vous que votre binaire Java (ou le terminal de votre serveur Minecraft) est configuré sur Autoriser les connexions entrantes.

**Méthode 2 : Terminal (pfctl)**

Pour autoriser le trafic via le filtre de paquets intégré à macOS :

1. Ouvrez le Terminal.
2.  Vérifiez si `pf` est en cours d'exécution :

    ```
    sudo pfctl -s info
    ```
3.  Pour ajouter une règle d'autorisation temporaire pour le port 443 :

    ```
    echo "pass out proto tcp to any port 443" | sudo pfctl -a custom -f -
    ```

#### Hébergeurs Cloud / Fournisseurs VPS

Si vous hébergez votre serveur chez des fournisseurs cloud (tels qu'AWS, DigitalOcean, Linode ou Google Cloud), les pare-feu des systèmes d'exploitation sont souvent complétés par des pare-feu cloud externes / groupes de sécurité (bien qu'ils soient normalement activés par défaut ou demandés lors de la création de l'instance).

**Google Cloud Platform (GCP)**

1. Accédez à la section Réseau VPC de votre console GCP.
2. Cliquez sur Pare-feu dans le menu de gauche, puis sur Créer une règle de pare-feu.
3. Nom : `allow-https-outbound`
4. Sens du trafic : Sélectionnez Sortant (Egress).
5. Action en cas de correspondance : Sélectionnez Autoriser.
6. Cibles : Sélectionnez Tags de cible spécifiés et ajoutez le tag attribué à votre VM (par ex., `allow-https`).
7. Filtre de destination : Plages IPv4 -> Réglez sur `0.0.0.0/0`.
8. Protocole et ports : Cochez tcp et tapez `443`.
9. Cliquez sur Créer.

**AWS EC2**

1. Accédez à votre tableau de bord EC2 et cliquez sur votre Instance.
2. Sélectionnez l'onglet Sécurité et cliquez sur votre Groupe de sécurité.
3. Cliquez sur Modifier les règles de trafic sortant (ne modifiez pas les règles d'entrée).
4. Cliquez sur Ajouter une règle :
   * Type : HTTPS
   * Protocole : TCP
   * Plage de ports : 443
   * Destination : N'importe où-IPv4 (`0.0.0.0/0`)
5. Cliquez sur Enregistrer les règles.

**DigitalOcean**

1. Accédez à Networking > Firewalls.
2. Sélectionnez le pare-feu attaché à votre Droplet.
3. Faites défiler jusqu'à Outbound Rules et cliquez sur Add Rule.
4. Sélectionnez Secure Web (HTTPS) dans le menu déroulant (cela configure automatiquement le port TCP 443 vers All IPv4/IPv6).
5. Cliquez sur Save.

**Linode (Akamai Connected Cloud)**

1. Accédez au tableau de bord Linode Cloud Manager et sélectionnez Firewalls dans le menu de navigation de gauche.
2. Cliquez sur le pare-feu attaché à votre instance Linode (ou cliquez sur Create Firewall si vous n'en avez pas encore configuré un).
3. Sélectionnez l'onglet Outbound Rules.
4. Cliquez sur Add Rule et configurez les paramètres :
   * Label : `allow-https-outbound`
   * Type : HTTPS (sélectionner ceci configure automatiquement le protocole sur TCP et la plage de ports sur 443)
   * Action : Accept
   * Sources : All (ou Anywhere-IPv4 / `0.0.0.0/0`)
5. Cliquez sur Save dans le panneau de règle, puis cliquez sur Save Changes en haut à droite de la page principale pour appliquer la configuration du pare-feu.

#### Hébergeurs de panneaux de jeu (Pterodactyl / Apex / Bisect)

La plupart des hébergeurs Minecraft mutualisés laissent le port sortant 443 ouvert par défaut. Si vous rencontrez toujours des erreurs de connexion, contactez l'équipe d'assistance de votre hébergeur pour vérifier que les requêtes HTTPS sortantes ne sont pas restreintes par des proxys réseau ou les pare-feu des panneaux.

#### Comment tester la connectivité du port 443

Pour vérifier si votre serveur peut atteindre des services HTTPS externes sur le port 443, exécutez l'une des commandes de diagnostic suivantes depuis le terminal de votre serveur :

Sur Linux / macOS :

```
curl -v https://google.com
```

Si vous voyez une réponse de connexion réussie (même un code 404 ou une réponse JSON), le port 443 sortant est pleinement fonctionnel.

Sur Windows (PowerShell) :

```
Test-NetConnection -ComputerName google.com -Port 443
```

Si `TcpTestSucceeded : True` est renvoyé, le trafic sortant sur le port 443 est ouvert.
