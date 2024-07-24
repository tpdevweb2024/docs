# Structure du projet

## Le projet de base Laravel

Après avoir effectué notre première installation de Laravel, nous allons maintenant analyser la structure de l'application laracars précédemment générée :&#x20;

```
laracars
└─  📂 app/
└─  📂 bootstrap/
└─  📂 config/
└─  📂 database/
└─  📂 lang/
└─  📂 node_modules/
└─  📂 public/
└─  📂 resources/
└─  📂 routes/
└─  📂 storage/
└─  📂 tests/
└─  📂 vendor/
📇 .editorconfig
📇 .env
📇 .env.example
📇 .gitattributes 
📇 .gitignore
📇 .styleci.yml
📇 artisan 
📇 composer.json
📇 composer.lock
📇 package-lock.json
📇 package.json
📇 php-unit.xml
📇 README.md 
📇 vite.config.js
```

## Le fichier d'environnement

A la racine de tous projets Laravel (ainsi que d'autres projets), nous pouvons remarquer la présence d'un fichier .env et d'un fichier .env.example.

Il faut bien dissocier les deux fichiers, le fichier **.env est votre fichier local**, celui qui permettra la configuration de votre poste actuel.

Le fichier **.env.example est lui la "trame" à suivre** si nous instancions ce projet depuis un clone /pull de github par exemple. Il faudra alors dans ce contexte le renommer en fichier .env et lui attribuer les valeurs souhaitées.

{% hint style="info" %}
Remarquez dans notre .gitignore la présence du fichier .env qui pourrait contenir des informations confidentielles telles que les mots de passe de base de données, etc...
{% endhint %}

Concernant les réglages, voici précisément les réglages que nous allons configurés afin de permettre au framework d'utiliser la base de données MySQL que nous avons préparé [au préalable](broken-reference).

```
// Veillez à remplacer vos identifiants de connexion à votre BDD
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laracars
DB_USERNAME=root
DB_PASSWORD=
```
