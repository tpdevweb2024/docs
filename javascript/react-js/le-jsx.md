# Le JSX

React fournit une syntaxe spéciale appelée **JSX** qui rend la création de composants plus simple. Ces composants génèrent des éléments React pour définir ce qui doit être affiché sur la page. La rubrique explique comment travailler avec JSX.

## Qu'est-ce que JSX ? <a href="#what-is-jsx" id="what-is-jsx"></a>

JSX est un élément essentiel de React. Il permet d'écrire facilement **du HTML** et **du JavaScript** ensemble dans React.

React ne nécessite pas l'utilisation de JSX : c'est simplement une façon plus simple de créer des éléments React.

Le JSX ressemble à du HTML mais n'est ni du HTML ni une chaîne. Il s'agit d'une extension de syntaxe de type HTML pour JavaScript qui vous permet d'écrire du HTML en JavaScript.&#x20;

```javascript
const element = <h1 className="title">Introduction au JSX</h1>;
```

Cet exemple montre comment écrire du JSX dans React. Cependant, les navigateurs ne reconnaissent pas cette syntaxe. En arrière-plan, JSX est compilé en `React.createElement()`appels, qui renvoient des éléments React.&#x20;

L'exemple ci-dessus est donc équivalent à :

```javascript
const element = React.createElement(
  'h1',
  { className: 'title' },
  'Introduction to JSX'
);
```

{% hint style="info" %}
JSX empêche également les attaques [Cross-Site Scripting (XSS)](https://owasp.org/www-community/attacks/xss/) . Toute valeur insérée dans JSX sera convertie en chaîne avant d'être rendue. Cela signifie que seuls les éléments écrits par votre propre application seront exécutés.
{% endhint %}

## Comment écrire du JSX <a href="#how-to-write-jsx" id="how-to-write-jsx"></a>

Il y a quelques règles à suivre lors de l'écriture de JSX :&#x20;

Vous pouvez placer n'importe quelle expression JavaScript valide entre accolades dans JSX :

```javascript
const user = {
  firstName: 'John',
  lastName: 'Smith'
};

function getUserName(user) {
  return user.firstName + ' ' + user.lastName;
}

const element = <p>{ getUserName(user) }</p>
```

Les attributs JSX utilisent la convention de naming **camelCase** :

```javascript
const buttonElement = (
  <button
    type="button"
    onClick={() => alert('Confirmed')}
  >
    Confirm
  </button>
);
```

Notez que `onClick`ici est le même que l'attribut HTML `onclick`.

JSX nécessite des balises de fermeture explicites. Il est possible d'omettre la balise de fermeture dans certains balisages HTML, comme `<input type="text">`. Mais dans JSX, vous devez ajouter la balise de fermeture. Par exemple :

```javascript
const element = <input type="text" />;
```

JSX doit être encapsulé dans une seule balise de niveau supérieur. Le JSX ci-dessous est incorrect car il comporte deux `h1`balises de niveau supérieur :

```javascript
const element = (
  <h1>Title 1</h1>
  <h1>Title 2</h1>
);
```

Nous pouvons corriger cela en enveloppant les deux `h1`balises dans une seule `div`, comme ceci :

```javascript
const element = (
  <div>
    <h1>Title 1</h1>
    <h1>Title 2</h1>
  </div>
);
```

## Extension de fichier <a href="#file-extension" id="file-extension"></a>

Comme mentionné ci-dessus, le code écrit avec la syntaxe JSX ne peut pas s'exécuter seul dans le navigateur. Par conséquent, cela ne fonctionnera pas si vous le mettez dans la `<script>`balise.

Dans React, nous écrivons généralement des composants dans `.jsx`des fichiers pour indiquer que les fichiers contiennent de la syntaxe JSX.&#x20;

Il n'est pas obligatoire d'utiliser `.jsx`des fichiers, vous pouvez toujours utiliser `.js`des fichiers pour écrire des composants, mais l' `.jsx`extension le rend plus clair.

{% hint style="info" %}
Comprendre JSX facilite la création de composants React en toute fluidité. N'oubliez pas que JSX protège également nativement votre application contre les attaques XSS pour vous aider à créer des sites Web sécurisés.
{% endhint %}

## Les régles du JSX

### Règle de l'élément à racine unique <a href="#single-root-element-rule" id="single-root-element-rule"></a>

Chaque expression JSX doit avoir un seul élément racine. cette règle garantit la cohérence de la structure des composants et simplifie le processus de rendu. React a besoin d'un point d'entrée unique pour réconcilier efficacement les modifications.

En d'autres termes, lorsque vous renvoyez du JSX à partir d'un composant, il doit avoir un seul élément parent le plus externe. Cette règle garantit la cohérence et la simplicité de la structure de vos composants.

```javascript
// Invalid JSX without a single root element

const InvalidComponent = () => {
  return (
    <h1>Hello</h1>
    <p>JSX Rules</p>
  );
};
```

Dans cet exemple, React se plaindrait d'avoir plusieurs éléments racines. Les encapsuler dans un parent `<div>`résout le problème.

```javascript
// Valid JSX with a single root element

const ValidComponent = () => {
  return (
    <div>
      <h1>Hello</h1>
      <p>JSX Rules</p>
    </div>
  );
};
```

Pour éviter d'inclure un élément supplémentaire `<div>`dans votre balisage, vous avez la possibilité d'utiliser les fragments `<>`et `</>`à la place.

### Règle de nom de classe <a href="#class-name-rule" id="class-name-rule"></a>

Utiliser `className`à la place de `class`pour définir les classes CSS dans JSX. Le `class`mot clé est réservé dans JavaScript, c'est pourquoi JSX opte pour `className`éviter les conflits. Le respect de cette règle garantit que votre code s'aligne sur la syntaxe de React et évite les erreurs inattendues.

```javascript
// JSX using className instead of class

const StyledDiv = () => {
  return <div className="styled-container">Styled Content</div>;
};
```

Ici, `className`attribut est utilisé pour appliquer la classe CSS, en maintenant la compatibilité avec React.

### Règle de fermeture de toutes les balises <a href="#close-all-the-tags-rule" id="close-all-the-tags-rule"></a>

Fermez toutes les balises JSX, même si elles se ferment automatiquement.

Pourquoi : la cohérence dans la fermeture des balises garantit une structure prévisible dans vos composants. Cela évite également les problèmes potentiels lors de l'utilisation de certaines fonctionnalités React ou d'autres outils qui analysent JSX.

```javascript
// JSX with closed self-closing tags

const SelfClosingComponent = () => {
  return (
    <div>
      <img src="example.jpg" alt="Example" />
      <input type="text" />
    </div>
  );
};
```

{% hint style="info" %}
Ici, les balises `<img>`et `<input>`sont toutes deux auto-fermées, conformément à la règle.
{% endhint %}

### Le camel case est la meilleure convention de naming <a href="#camel-case-most-of-the-things-rule" id="camel-case-most-of-the-things-rule"></a>

Utilisez camelCase pour nommer les attributs JSX, les gestionnaires d'événements et les variables.

C'est une convention dans JavaScript et React, qui garantit l'uniformité de votre base de code. Elle s'aligne également sur les meilleures pratiques du langage, améliorant ainsi la lisibilité du code.

Lorsque vous écrivez du JSX dans React, il est converti en JavaScript et les attributs que vous utilisez dans JSX deviennent des clés dans les objets JavaScript. Lorsque vous travaillez avec vos composants, vous souhaiterez peut-être utiliser ces attributs comme variables. Cependant, JavaScript a certaines règles pour les noms de variables : par exemple, ils ne peuvent pas contenir de tirets ou être des mots réservés comme « classe ».

Pour contourner ce problème, React écrit souvent les attributs HTML et SVG en camelCase. Cela signifie qu'au lieu d'utiliser « class-name », vous utiliserez « className » dans React. Voici un exemple :

```javascript
// JSX with camelCase attributes and event handlers

const CamelCaseComponent = () => {
  const handleClick = () => {
    console.log('Button clicked!');
  };

  return (
    <button onClick={handleClick} disabled={false}>
      Click Me
    </button>
  );
};
```

### Règle d'interpolation d'expression <a href="#expression-interpolation-rule" id="expression-interpolation-rule"></a>

Utilisez des accolades `{}`pour incorporer des expressions JavaScript dans JSX. L'interpolation d'expression permet un rendu de contenu dynamique, facilitant ainsi l'injection de variables ou du résultat de fonctions dans votre JSX.

```javascript
// Using expression interpolation in JSX

const user = { name: 'John', age: 25 };

const UserInfo = () => {
  return (
    <div>
      <p>Name: {user.name}</p>
      <p>Age: {user.age}</p>
    </div>
  );
};
```
