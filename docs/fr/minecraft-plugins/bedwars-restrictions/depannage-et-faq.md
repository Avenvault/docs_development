---
icon: question
---

# Dépannage et FAQ

Q : Ma console affiche « FATAL: Invalid License Key » et le plugin se désactive.

R : Cela signifie que l'authentification cloud RSA-256 a rejeté votre clé.

* Vérifiez votre `config.yml` pour vous assurer qu'il n'y a pas d'espaces inutiles autour de votre clé.
* Vérifiez que votre abonnement/licence n'a pas expiré sur le portail premium.
* Assurez-vous d'utiliser le format exact fourni (par ex., 1234-5678-9012).

Q : La console affiche « License Server Unreachable » lors du démarrage.

R : Le plugin nécessite une connexion Internet active pour vérifier son intégrité. Assurez-vous que votre hôte/machine autorise les connexions sortantes sur le port 443 (HTTPS) et que votre pare-feu ne bloque pas le trafic vers nos serveurs d'authentification.

Q : Les joueurs peuvent toujours construire en dehors des limites de l'arène !

R : Tout d'abord, vérifiez que le joueur en question n'est pas un administrateur (OP) ou ne possède pas la permission `bwr.bypass`. Deuxièmement, vérifiez à nouveau vos coordonnées min et max dans le `config.yml` pour vous assurer que la zone 3D est correctement définie (les valeurs min doivent toujours être inférieures aux valeurs max).

Q : Ce plugin est-il compatible avec ViaVersion/Geyser ?

R : Oui ! Comme BedwarsRestrictions gère les zones de limite au niveau du serveur, il est 100 % compatible avec les joueurs Bedrock via Geyser et les clients utilisant différentes versions via ViaVersion.

**Besoin d'aide supplémentaire ?** [_**Contactez-nous**_](https://plugins.avenvault.com/contact) **avec votre clé de licence (pour vérification) ou rejoignez notre Discord et vérifiez votre licence pour obtenir du support !**
