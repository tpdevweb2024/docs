# L'orienté composant

Le développement orienté composant est une approche où les applications sont construites à partir de composants réutilisables et indépendants. Chaque composant encapsule une partie spécifique de l'interface utilisateur et de la logique d'application.

## Le composant : l'élément de base

Les composants représentent les éléments de base de l'application, similaires aux briques LEGO qui peuvent être assemblées pour créer des structures complexes.

## Avantages de l'approche Orientée Composant

* **Réutilisabilité**: Les composants peuvent être réutilisés dans différentes parties de l'application.
* **Modularité**: Facilite la maintenance et l'évolutivité.
* **Isolation**: Les composants sont isolés les uns des autres, ce qui réduit les risques de bugs.

## React: Un exemple paradigmatique

### React comme bibliothèque de composants

React est une bibliothèque JavaScript qui incarne parfaitement le paradigme du développement orienté composant. Il permet de construire des interfaces utilisateur en décomposant l'interface en composants isolés et autonomes.

#### Exemple de composant React

```jsx
import React from 'react';

function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

export default Greeting;
```

Ce simple composant `Greeting` affiche un message de salutation et peut être réutilisé dans différente parties d'une application React.

{% hint style="info" %}
L'approche orientée composant, illustrée par des bibliothèques comme React, permet de créer des applications plus modulaires, maintenables et réutilisables.
{% endhint %}
