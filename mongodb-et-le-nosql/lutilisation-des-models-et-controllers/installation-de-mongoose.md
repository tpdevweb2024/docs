# Installation de Mongoose

Avant de créer des modèles, assurez-vous d'avoir installé Mongoose dans votre projet Express.js.&#x20;

Vous pouvez l'installer via npm :

```bash
npm install mongoose
```

Ensuite, configurez Mongoose pour se connecter à MongoDB dans le fichier principal (généralement `app.js` ou `server.js`) :

```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost:27017/nom_de_ta_base_de_donnees')
.then(() => console.log('Connexion à MongoDB réussie !'))
.catch((err) => console.error('Connexion à MongoDB échouée :', err));
```

{% hint style="success" %}
La connexion à MongoDB est maintenant réussie ! Bravo.
{% endhint %}
