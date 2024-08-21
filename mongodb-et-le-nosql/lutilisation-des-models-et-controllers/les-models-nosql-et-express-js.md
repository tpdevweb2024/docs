# Les models NoSQL et Express JS

Un modèle Mongoose est une représentation d'une collection MongoDB dans une application Express. Il définit la structure des documents (données) qui vont être stockés dans cette collection.

## **Définir un schéma Mongoose**

Un schéma Mongoose détermine la structure de chaque document, y compris les types de données, les validations, et d'autres comportements. Par exemple, si vous voulez créer un modèle pour un utilisateur, vous commencerez par définir un schéma `UserSchema` :

```javascript
new Schema({
    name: {
        type: String,
        required: true, // Ce champ est obligatoire
    },
    email: {
        type: String,
        required: true,
        unique: true, // Les emails doivent être uniques
    },
    password: {
        type: String,
        required: true,
    },
    dateCreated: {
        type: Date,
        default: Date.now, // Par défaut, la date actuelle est utilisée
    }
})
```

## **Créer un modèle Mongoose**

Nous allons alors créer un modèle `userModel` qui utilisera le schéma ci-dessus, utilisons le code suivant :

```javascript
// models/userModel.js

const mongoose = require("mongoose");
const { Schema } = require("mongoose");

const userModel = mongoose.model('User', new Schema({
    name: {
        type: String,
        required: true, 
    },
    email: {
        type: String,
        required: true,
        unique: true,
    },
    password: {
        type: String,
        required: true,
    },
    dateCreated: {
        type: Date,
        default: Date.now,
    }
}), "users");

module.exports = { userModel };
```

{% hint style="info" %}
Le modèle `userModel` permet d'effectuer des opérations CRUD (Create, Read, Update, Delete) sur les documents de la collection `users` dans MongoDB.
{% endhint %}
