# Les controllers et les routes

Maintenant que le modèle est créé, vous pouvez l'utiliser dans vos routes Express pour manipuler les données.

## **Créer un nouvel utilisateur**

Dans le fichier de routes, vous pouvez définir une route pour créer un nouvel utilisateur :

{% code overflow="wrap" %}
```javascript
const express = require('express');
const router = express.Router();
const { userModel } = require('../models/userModel'); // Assure-toi de bien spécifier le chemin vers ton modèle

// Route pour créer un utilisateur
router.post('/register', async (req, res) => {
    try {
        const { name, email, password } = req.body;
        
        // Créer une nouvelle instance de l'utilisateur
        const newUser = new userModel({ name, email, password });
        
        // Sauvegarder l'utilisateur dans la base de données
        await newUser.save();
        
        res.status(201).json(newUser);
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la création de l\'utilisateur' });
    }
});

module.exports = router;
```
{% endcode %}

## **Lire des données**

Pour récupérer des utilisateurs depuis la base de données, vous pouvez utiliser une route en GET :

{% code overflow="wrap" %}
```javascript
// Route pour obtenir tous les utilisateurs
router.get('/users', async (req, res) => {
    try {
        const users = await userModel.find(); // Récupérer tous les utilisateurs
        res.json(users);
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la récupération des utilisateurs' });
    }
});
```
{% endcode %}

## Ajouter plusieurs utilisateurs

Pour ajouter plusieurs utilisateurs, vous pouvez définir une route utilisant la méthode POST comme suit :

{% code overflow="wrap" %}
```javascript
// Route pour créer plusieurs utilisateurs
router.post('/register/multiple', async (req, res) => {
    try {
        const users = req.body;
        
        // Créer et sauvegarder plusieurs instances d'utilisateurs
        const newUsers = await userModel.insertMany(users);
        
        res.status(201).json(newUsers);
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la création des utilisateurs' });
    }
});
```
{% endcode %}

## Récupérer les utilisateurs par filtre

Pour récupérer les utilisateurs dont le nom est "Martin", vous pouvez définir une route utilisant la méthode GET comme suit :

{% code overflow="wrap" %}
```javascript
// Route pour obtenir les utilisateurs par nom
router.get('/users/name/:name', async (req, res) => {
    try {
        const name = req.params.name;
        const users = await userModel.find({ name: name });
        res.json(users);
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la récupération des utilisateurs' });
    }
});
```
{% endcode %}

{% hint style="info" %}
Ensuite, vous pouvez accéder à cette route en utilisant une URL comme `/users/name/Martin`.
{% endhint %}

## Visualiser un utilisateur

Pour visualiser les détails d'un utilisateur spécifique, vous pouvez définir une route utilisant la méthode GET comme suit :

```javascript
// Route pour obtenir les détails d'un utilisateur par ID
router.get('/users/:id', async (req, res) => {
    try {
        const userId = req.params.id;
        const user = await userModel.findById(userId);
        res.json(user);
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la récupération de l\'utilisateur' });
    }
});
```

{% hint style="info" %}
Vous pouvez accéder à cette route en utilisant une URL comme `/users/<id>` pour obtenir les détails de l'utilisateur avec l'ID spécifié.
{% endhint %}

## Mettre à jour un utilisateur

Pour modifier un utilisateur existant, vous pouvez définir une route utilisant la méthode PUT comme suit :

{% code overflow="wrap" %}
```javascript
// Route pour mettre à jour l'email d'un utilisateur
router.put('/users/:id', async (req, res) => {
    try {
        const userId = req.params.id;
        const newEmail = req.body.email;

        // Mettre à jour l'email de l'utilisateur
        const updatedUser = await userModel.findByIdAndUpdate(
            userId, 
            { email: newEmail }, 
            { new: true }
        );
        
        res.json(updatedUser);
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la mise à jour de l\'utilisateur' });
    }
});
```
{% endcode %}

{% hint style="info" %}
Ensuite, vous pouvez accéder à cette route en utilisant une URL comme `/users/<id>` en effectuant une requête PUT et en fournissant le nouvel email dans le corps de la requête.
{% endhint %}

## Supprimer un utilisateur

Pour supprimer un utilisateur existant, vous pouvez définir une route utilisant la méthode DELETE comme suit :

{% code overflow="wrap" %}
```javascript
// Route pour supprimer un utilisateur
router.delete('/users/:id', async (req, res) => {
    try {
        const userId = req.params.id;
        await userModel.findByIdAndDelete(userId);
        res.json({ message: 'Utilisateur supprimé avec succès' });
    } catch (err) {
        res.status(500).json({ error: 'Une erreur est survenue lors de la suppression de l\'utilisateur' });
    }
});
```
{% endcode %}

