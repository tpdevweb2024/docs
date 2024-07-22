# Notre premier composant

Un composant React est une fonction JavaScript qui retourne du JSX.&#x20;

{% hint style="info" %}
JSX est une extension de JavaScript qui permet d'écrire du HTML dans du JavaScript.
{% endhint %}

## **Création d'un composant simple**

1. Ouvrez votre projet dans votre éditeur de code préféré (par exemple, Visual Studio Code).
2. Dans le dossier `src`, créez un nouveau fichier appelé `MyFirstComponent.js`.
3. Écrivez le code suivant dans `MyFirstComponent.js` :&#x20;

```jsx
import React from 'react';

// Déclaration d'un composant fonctionnel
function MyFirstComponent() {
  return (
    <div>
      <h1>Bonjour, monde !</h1>
      <p>Ceci est mon premier composant React.</p>
    </div>
  );
}

export default MyFirstComponent;
```

**Explication :**

* `import React from 'react';` : Importation de la bibliothèque React.
* `function MyFirstComponent() { ... }` : Déclaration d'un composant fonctionnel appelé `MyFirstComponent`.
* `return (...)` : Le composant retourne un élément JSX. JSX ressemble à du HTML mais s'écrit en JavaScript.
* `export default MyFirstComponent;` : Exportation du composant pour pouvoir l'utiliser dans d'autres parties de l'application.

## Import du composant

Ouvrez `src/App.js` et remplacez le contenu par :

```jsx
import React from 'react';
import MyFirstComponent from './MyFirstComponent';

function App() {
  return (
    <div className="App">
      <MyFirstComponent />
    </div>
  );
}

export default App;
```

\
**Explication :**

* `import MyFirstComponent from './MyFirstComponent';` : Importation de votre composant personnalisé.
* `<MyFirstComponent />` : Utilisation de votre composant dans le rendu de `App`.

{% hint style="info" %}
Enregistrez tous les fichiers et assurez-vous que l'application tourne toujours (dans le terminal avec `npm start`).
{% endhint %}
