# Les promesses et l'API fetch

L'asynchrone est essentiel pour créer des applications web réactives et performantes. Cependant, la gestion du code asynchrone avec les callbacks peut rapidement devenir complexe.&#x20;

Les promesses, introduites dans ES6, offrent une solution élégante pour gérer le code asynchrone de manière lisible et modulaire.

## Qu'est-ce que l'asynchrone ?

Un appel asynchrone fait référence à une opération exécutée en parallèle du thread principal de l'application, sans bloquer l'exécution du code. Cela permet à l'application de rester réactive pendant que l'opération asynchrone est en cours.

### **Différence avec le fonctionnement synchrone**

* **Synchrone** : Les instructions sont exécutées séquentiellement. Une opération longue peut bloquer l'application.
* **Asynchrone** : Le code n'attend pas la fin de l'opération longue et continue son exécution. Les opérations asynchrones enregistrent une fonction de rappel (callback) qui sera exécutée une fois l'opération terminée.

### **Exemples d'opérations asynchrones**

* **setTimeout et setInterval** : Planifient l'exécution d'une fonction à un moment ultérieur ou à intervalles réguliers.
* **Requêtes réseau** : Les requêtes HTTP avec l'API Fetch ou XMLHttpRequest.
* **Événements** : Gestion des clics de souris, des événements de clavier, etc.

## Problèmes avec les callbacks

### **Le Callback Hell (Pyramide de callbacks imbriqués)**

Les callbacks imbriqués peuvent rendre le code difficile à lire, comprendre et maintenir, conduisant à une "Pyramide de Doom".

### **Gestion des erreurs complexe**

Chaque callback doit vérifier et transmettre les erreurs au callback suivant, entraînant une duplication de code et une logique de gestion des erreurs dispersée.

***

## Les promesses

### **Création d'une promesse**

Les promesses en JavaScript sont créées avec le constructeur `Promise`, prenant une fonction exécutrice en argument, laquelle reçoit deux fonctions : `resolve` et `reject`.

### **Exemple de promesse**

```javascript
const maPromesse = new Promise((resolve, reject) => {
    let succès = true;
    if (succès) {
        resolve("Opération réussie");
    } else {
        reject("Opération échouée");
    }
});
```

### **Chaîner les promesses avec `.then()`**

La méthode `.then()` permet de chaîner plusieurs opérations asynchrones.

### **Gérer les erreurs avec `.catch()`**

La méthode `.catch()` est utilisée pour gérer les erreurs dans une chaîne de promesses.

***

## L'utilisation de fetch

### **Qu'est-ce que Fetch() ?**

`fetch` est une API moderne pour effectuer des requêtes réseau en JavaScript. Elle retourne une promesse et permet de récupérer des ressources à partir d'un serveur.

### **Faire une requête GET**

```javascript
fetch('https://api.exemple.com/données')
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Erreur:', error));
```

### **Envoyer des données avec POST**

```javascript
fetch('https://api.exemple.com/utilisateurs', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({
        nom: 'John Doe',
        email: 'john.doe@example.com'
    })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Erreur:', error));
```

{% hint style="info" %}
L'utilisation des promesses et de l'API Fetch simplifie grandement la gestion des opérations asynchrones en JavaScript, rendant le code plus lisible et maintenable.
{% endhint %}
