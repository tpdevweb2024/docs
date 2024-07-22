# Les écouteurs d'évènement

Dans React, les écouteurs d'événements gèrent les interactions des utilisateurs telles que les clics sur les boutons, les soumissions de formulaires ou les mouvements de la souris.&#x20;

Vous pouvez les utiliser pour répondre à ces événements et modifier l'état de votre application ou effectuer d'autres actions. Cette rubrique vous montre comment gérer les événements dans React.

## Comment ils fonctionnent <a href="#how-they-work" id="how-they-work"></a>

Les écouteurs et gestionnaires d'événements sont essentiels au développement Web. Un écouteur d'événements est une fonction ou un morceau de code qui « écoute » un événement spécifique. Il est connecté à un élément HTML et attend que cet élément déclenche l'événement. Lorsque l'événement se produit, l'écouteur exécute le gestionnaire d'événements connecté.

De l'autre côté, un gestionnaire d'événements est une fonction ou un bloc de code qui s'exécute en réponse à un événement spécifique. Il décrit l'action à entreprendre lorsque l'événement se produit. Les gestionnaires d'événements sont liés aux écouteurs d'événements et sont déclenchés lorsque l'événement correspondant se produit.

{% hint style="info" %}
Avec les composants fonctionnels de React, vous pouvez configurer des écouteurs d'événements à l'aide de gestionnaires d'événements en ligne ou en transmettant des gestionnaires d'événements en tant qu'accessoires.
{% endhint %}

## Gestionnaires d'événements en ligne <a href="#inline-event-handlers" id="inline-event-handlers"></a>

Les gestionnaires d'événements en ligne sont positionnés directement dans le code JSX du composant. Vous pouvez attacher un écouteur d'événements à un élément à l'aide de l'attribut `on<Event>` , où `<Event>`se trouve l'événement que vous souhaitez gérer.&#x20;

Pour gérer un événement de clic sur un bouton, par exemple, vous pouvez utiliser l'attribut `onClick` :

Regardons cet événement :

```javascript
import React from 'react';

function Clicker() {
  const handleClick = () => {
    console.log('Button clicked!');
  };

  return (
    <button onClick={handleClick}>Click Me</button>
  );
}

export default Clicker;
```

Dans cet exemple, la fonction `handleClick` est configurée dans le composant et transmise à l'élément bouton. Lorsque le bouton est cliqué, React appelle la fonction `handleClick`.

N'oubliez pas que dans React, les gestionnaires d'événements suivent généralement les conventions de dénomination camelCase, telles que `onClick`, `onMouseEnter`, etc., au lieu des noms d'événements en minuscules traditionnels en JavaScript.

Vous pouvez également faire du gestionnaire d'événements une fonction de flèche en ligne dans l'attribut `onClick` :

```javascript
import React from 'react';

function Clicker() {
  return (
    <button onClick={() => console.log('Button clicked!')}>Click Me</button>
  );
}

export default Clicker;
```

Les gestionnaires d'événements en ligne peuvent être utiles pour les cas de gestion d'événements simples ou lorsque vous n'avez pas besoin de réutiliser la fonction de gestionnaire d'événements n'importe où dans votre composant ou votre application.&#x20;

Cependant, gardez à l'esprit que cette approche peut entraîner des problèmes de performances, car chaque rendu du composant crée une nouvelle fonction.

Lorsque vous transmettez une fonction en tant que gestionnaire d'événements dans React, assurez-vous de transmettre la fonction elle-même, et non de l'appeler immédiatement. Cela signifie que vous ne devez pas inclure de parenthèses `()`lorsque vous transmettez la fonction à un gestionnaire d'événements :

```javascript
<button onClick={handleClick}>	// correct 
<button onClick={handleClick()}> // incorrect 
```

Cette règle s'applique également aux fonctions en ligne ; vous devez utiliser une fonction de rappel, c'est à dire une callback :

```javascript
<button onClick={() => console.log('OK')}> // OK!
<button onClick={console.log('NOT OK')}> // NOT OK!
```

### Passer des gestionnaires d'événements en tant que props <a href="#passing-event-handlers-as-props" id="passing-event-handlers-as-props"></a>

Vous pouvez également transmettre des gestionnaires d'événements en tant que propriétés entre les composants.&#x20;

Par exemple, si un composant parent restitue un composant enfant et que vous souhaitez que le composant enfant gère un événement, vous pouvez transmettre le gestionnaire d'événements en tant que props.

```javascript
import React from 'react';

function ChildComponent({ onClick }) {
  return <button onClick={onClick}>Click Me</button>;
}

function ParentComponent() {
  const handleClick = () => {
    console.log('Button clicked!')
  };

  return <ChildComponent onClick={handleClick} />;
}
```

Dans cet exemple, `ParentComponent`configure `handleClick` et la transmet comme propriété `onClick` à `ChildComponent`. Il utilise ensuite cette props pour attacher l'écouteur d'événements à l'élément bouton. Lorsque le bouton est cliqué, React appelle la fonction `handleClick`dans le `ParentComponent`.

### Utilisation des props dans les gestionnaires d'événements <a href="#using-props-in-event-handlers" id="using-props-in-event-handlers"></a>

Vous pouvez transmettre des données supplémentaires aux gestionnaires d'événements à l'aide des props. Supposons que vous ayez une liste d'éléments et que vous souhaitiez gérer un événement de clic sur chaque élément :

```javascript
import React from 'react';

function Item({ name, onClick }) {

  return <li onClick={() => onClick(name)}>{name}</li>;
}

function ItemList() {
  const handleItemClick = (itemName) => {
    console.log(`Clicked item: ${itemName}`);
  };

  return (
    <ul>
      <Item name="Item 1" onClick={handleItemClick} />
      <Item name="Item 2" onClick={handleItemClick} />
      <Item name="Item 3" onClick={handleItemClick} />
    </ul>
  );
}
```

Dans cet exemple, le composant `Item` reçoit la prop  `name`et la prop `onClick`. Il appelle la fonction`onClick` passée en tant que prop et passe la prop `name`comme argument lorsque l'élément est cliqué. La`handleItemClick` du composant parent reçoit cet argument et l'enregistre dans la console.

### Événements fréquemment utilisés <a href="#commonly-used-events" id="commonly-used-events"></a>

En tant qu'apprenant en développement Web, il est essentiel de se familiariser avec les événements récurrents dans JavaScript et React. Voici quelques événements principaux que vous devez connaître :

* **onClick** : Cet événement se produit lorsqu'un élément, comme un bouton ou un lien, est cliqué.
* **onChange** : cet événement se produit lorsque la valeur d'un élément d'entrée, tel qu'un champ de texte ou une liste déroulante, change.
* **onSubmit** : cet événement se produit lorsque quelqu'un soumet un formulaire, généralement en appuyant sur la touche Entrée ou en cliquant sur un bouton d'envoi.

Ce ne sont là que quelques exemples d'événements récurrents. Il existe de nombreux autres événements disponibles, en fonction des éléments et des interactions spécifiques auxquels vous faites face.

{% hint style="info" %}
Les interactions utilisateur sont au cœur de toute application Web, il est donc essentiel de pouvoir gérer correctement ces interactions avec des gestionnaires d'événements. Dans React, vous pouvez définir des gestionnaires d'événements à l'aide de gestionnaires d'événements en ligne ou en transmettant des gestionnaires d'événements en tant qu'accessoires aux composants.&#x20;
{% endhint %}
