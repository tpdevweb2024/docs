# Etat et cycle de vie

## Gestion de l'état local

Un état local dans React est un objet qui permet à un composant de garder en mémoire des informations entre les rendus. Il est utilisé pour stocker des valeurs qui peuvent changer au fil du temps, comme les entrées utilisateurs, les compteurs, les sélections, etc.&#x20;

{% hint style="info" %}
L'état local est géré à l'aide du hook `useState` dans les composants fonctionnels, permettant ainsi de mettre à jour l'interface utilisateur en réponse aux interactions utilisateur.
{% endhint %}

### **Création de l'état**

Voyons maintenant comment créer et gérer l'état local dans un composant fonctionnel React à l'aide du hook `useState`.&#x20;

Voici un exemple simple d'un compteur qui s'incrémente à chaque clic :

```jsx
// Importation de useState depuis React
import React, { useState } from 'react';

// Création d'un composant fonctionnel
function Counter() {
  // Déclaration d'une variable d'état "count" avec une valeur initiale de 0
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Le compteur est à : {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
    </div>
  );
}

export default Counter;
```

**Explication :**

* `useState` est un hook qui permet de gérer l'état local dans un composant fonctionnel.
* La syntaxe `[count, setCount]` utilise la déstructuration de tableau pour créer une variable d'état `count` et une fonction `setCount` pour la mettre à jour.
* La valeur initiale de `count` est 0.

### **Mise à jour de l'état**

Le code suivant montre comment ajouter des fonctionnalités supplémentaires à un compteur de base en React.&#x20;

{% hint style="info" %}
En plus d'incrémenter la valeur du compteur, l'utilisateur sera également capable de décrémenter et de réinitialiser la valeur du compteur à zéro.&#x20;
{% endhint %}

Ces fonctionnalités sont implémentées à l'aide de boutons supplémentaires et de la méthode `setCount` du hook `useState`.

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Le compteur est à : {count}</p>
      <button onClick={() => setCount(count + 1)}>Incrémenter</button>
      <button onClick={() => setCount(count - 1)}>Décrémenter</button>
      <button onClick={() => setCount(0)}>Réinitialiser</button>
    </div>
  );
}

export default Counter;
```

**Explication :**

* Trois boutons sont ajoutés pour incrémenter, décrémenter et réinitialiser le compteur.
* Chaque bouton utilise `setCount` pour mettre à jour la valeur de `count`.

## Le cycle de vie des composants

### **Introduction à `useEffect`**

Dans cette section, nous allons explorer l'utilisation du hook `useEffect` pour gérer des effets secondaires dans les composants fonctionnels React.&#x20;

Le code suivant montre comment mettre en place un minuteur simple qui incrémente automatiquement un compteur toutes les secondes, et effectue le nettoyage nécessaire lorsque le composant est démonté.

```jsx
import React, { useState, useEffect } from 'react';

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // Effet secondaire : incrémenter le compteur toutes les secondes
    const interval = setInterval(() => {
      setCount(count => count + 1);
    }, 1000);

    // Nettoyage de l'effet : arrêter l'intervalle lorsque le composant est démonté
    return () => clearInterval(interval);
  }, []); // Le tableau vide signifie que cet effet s'exécute une seule fois

  return (
    <div>
      <p>Le compteur est à : {count}</p>
    </div>
  );
}

export default Timer;
```

### Explication détaillée du fonctionnement du Hook

1.  **Création de l'effet avec `useEffect` :**

    `useEffect` est un hook qui permet d'exécuter des effets secondaires dans les composants fonctionnels. Dans cet exemple, l'effet crée un intervalle qui incrémente la variable `count` toutes les secondes.
2.  **Fonction de nettoyage :**

    L'effet retourne une fonction de nettoyage qui s'exécute lorsque le composant est démonté ou que l'effet est ré-exécuté. Cette fonction de nettoyage est essentielle pour éviter les fuites de mémoire et pour arrêter les tâches asynchrones ou les abonnements (comme les intervals, les timeouts, les abonnements à des WebSocket, etc.).
3.  **`setInterval` :**

    `setInterval` est une fonction JavaScript qui appelle une fonction ou exécute un bout de code, à des intervalles de temps réguliers spécifiés en millisecondes. Ici, `setInterval` appelle la fonction qui incrémente `count` toutes les secondes (1000 millisecondes).
4.  **`clearInterval` :**

    `clearInterval` est une fonction JavaScript qui annule un intervalle précédemment établi par `setInterval`. En retournant une fonction de nettoyage dans `useEffect`, React sait qu'il doit exécuter cette fonction lorsque le composant est démonté ou lorsque les dépendances de l'effet changent. Dans notre cas, `clearInterval(interval)` arrête l'intervalle lorsque le composant `Timer` est démonté, empêchant ainsi l'incrémentation continue de `count` et libérant les ressources associées.
5.  **Dépendances de l'effet :**

    Le tableau vide `[]` passé en second argument à `useEffect` signifie que l'effet ne s'exécute qu'une seule fois, après le premier rendu du composant (équivalent à `componentDidMount`).

    _Si on avait inclus des variables dans ce tableau, l'effet se ré-exécuterait chaque fois que l'une de ces variables change._

### Importance du nettoyage

* **Prévenir les fuites de mémoire :**
  * Les intervalles et les timeouts créés avec `setInterval` ou `setTimeout` continuent à s'exécuter même après que le composant est démonté, ce qui peut entraîner des fuites de mémoire si on ne les nettoie pas.
  * Utiliser `clearInterval` dans la fonction de nettoyage permet de s'assurer que ces tâches sont correctement arrêtées.
*   **Gérer correctement les effets secondaires :**

    En nettoyant les effets, on garantit que les ressources sont libérées et que le composant ne continue pas à exécuter des tâches inutiles ou potentiellement problématiques après son démontage.

{% hint style="info" %}
Cette gestion avec `useEffect` et `clearInterval` est cruciale pour créer des composants React performants et sans bogues, en particulier lorsqu'ils impliquent des tâches asynchrones ou des abonnements qui peuvent persister au-delà de la durée de vie du composant.
{% endhint %}

## **Points clés à retenir**

1. **useState** : Utilisé pour créer une variable d'état locale dans un composant fonctionnel et une fonction pour la mettre à jour.
2. **useEffect** : Permet d'effectuer des effets secondaires comme des abonnements ou des minuteries dans les composants fonctionnels.
3. **Nettoyage d'effet** : Toujours retourner une fonction de nettoyage dans `useEffect` pour éviter des fuites de mémoire ou des comportements inattendus.

{% hint style="success" %}
En résumant, `useEffect` associé à `useState` offre un moyen puissant de gérer les effets secondaires dans les composants fonctionnels de React de manière propre et efficace.
{% endhint %}
