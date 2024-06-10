# Les types de serveur

### Serveur web mutualisé

Un **serveur web mutualisé** représente une solution d'hébergement où un seul serveur physique héberge plusieurs sites web. Les ressources de ce serveur, telles que le processeur, la mémoire, l'espace de stockage et la bande passante, sont partagées entre tous les sites. Cette mutualisation impacte les performances individuelles de chaque site en fonction de la charge globale sur le serveur.

Cet arrangement rend l'hébergement mutualisé plus abordable par rapport à d'autres options, puisque les coûts sont divisés entre plusieurs clients. Il convient pour divers types de sites web, tels que Wordpress, PHP, ou des sites statiques en HTML.

{% hint style="info" %}
L'utilisation de cPanel pour la gestion des serveurs web est courante, surtout pour l'hébergement mutualisé. cPanel facilite la gestion des sites web en offrant une interface utilisateur simple pour administrer les comptes d'hébergement, créer des bases de données, gérer les fichiers web, et installer des logiciels comme WordPress.
{% endhint %}

### Serveur cloud

Un serveur cloud est une solution virtuelle s'appuyant sur les ressources de plusieurs serveurs physiques. Cette architecture permet d'ajuster les ressources allouées selon les besoins spécifiques d'un site web, garantissant ainsi une flexibilité et une capacité d'évolution supérieures. En cas de défaillance d'un serveur physique, le système peut reconfigurer automatiquement les ressources, assurant une haute disponibilité. Bien que potentiellement plus onéreux que l'hébergement mutualisé, en raison de la scalabilité (mise à l'échelle) des ressources, les serveurs cloud représentent une solution performante pour les applications exigeantes telles que React, VueJs, NextJS, Nuxt, entre autres.

Voici quelques exemples de serveurs cloud populaires :

* **Amazon Web Services (AWS)** - Propose une large gamme de services de calcul cloud, y compris EC2, qui permet aux utilisateurs de lancer des instances virtuelles avec différentes configurations de ressources.
* **Microsoft Azure** - Offre des services de cloud computing pour le développement, le test, le déploiement et la gestion d'applications et services via les centres de données gérés par Microsoft.
* **Google Cloud Platform (GCP)** - Fournit des services d'hébergement cloud qui permettent de lancer des instances de machines virtuelles dans l'infrastructure de Google.
* **IBM Cloud** - Propose des services cloud, notamment IaaS, PaaS, et SaaS, qui utilisent à la fois des environnements virtuels et dédiés.
* **DigitalOcean** - Populaire auprès des développeurs pour sa simplicité, il offre des serveurs cloud appelés "droplets" qui peuvent être déployés rapidement pour différentes charges de travail.

{% hint style="success" %}
Pour les serveurs basés sur le cloud et leurs gestions, des plateformes comme AWS Management Console et Google Cloud Console proposent des outils avancés.&#x20;

Ces outils permettent un déploiement, une surveillance, et une gestion fine et technique des ressources dans le cloud.
{% endhint %}



{% hint style="info" %}
Lors de la sélection d'un type d'hébergement pour votre site web ou application, il est crucial de prendre en compte vos besoins spécifiques en termes de trafic, coût, flexibilité, sécurité et maintenance. Les serveurs mutualisés peuvent être un choix judicieux pour des projets plus petits ou des sites avec un trafic modéré, en raison de leur coût réduit. En revanche, pour les sites à fort trafic ou nécessitant une grande flexibilité et sécurité, les serveurs dédiés ou les serveurs cloud offrent des solutions plus adaptées, bien que généralement à un coût plus élevé. La décision finale dépendra donc de l'équilibre entre ces différents facteurs et des priorités spécifiques de votre projet.
{% endhint %}
