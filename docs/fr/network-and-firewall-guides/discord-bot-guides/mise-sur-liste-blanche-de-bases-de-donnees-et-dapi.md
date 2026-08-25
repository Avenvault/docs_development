# Mise sur liste blanche de bases de données et d'API

La quasi-totalité des bots Discord modernes s'appuient sur une base de données externe (MongoDB, MySQL, PostgreSQL) pour stocker les données utilisateur, ou récupèrent des informations depuis des API externes (comme YouTube, Spotify ou OpenAI).

Si votre base de données est hébergée sur une machine différente de celle de votre bot (par exemple MongoDB Atlas ou une base de données administrée sur AWS), vous devez ajouter l'adresse IP de votre bot à la liste blanche (_whitelist_).

#### Comment configurer l'accès à une base de données externe

1. Trouvez l'adresse IPv4 publique de la machine hébergeant votre bot Discord.
2. Connectez-vous au tableau de bord de votre fournisseur de base de données (ex. MongoDB Atlas, AWS RDS).
3. Naviguez vers la section _Network Access_ (Accès Réseau) ou _Security Groups_ (Groupes de sécurité).
4. Ajoutez une règle d'entrée autorisant les connexions provenant de l'adresse IP spécifique de votre bot.

{% hint style="info" %}
Remarque pour les adresses IP dynamiques : Si vous hébergez le bot sur votre réseau domestique où l'adresse IP change fréquemment, vous devrez peut-être autoriser les connexions depuis n'importe quelle adresse (`0.0.0.0/0`). Cependant, cela nécessite un mot de passe extrêmement robuste pour votre base de données. Il est fortement recommandé d'utiliser la longueur maximale autorisée par votre fournisseur de base de données et de conserver ce mot de passe dans un gestionnaire sécurisé comme Bitwarden !
{% endhint %}

