# Le routeur avec react-router

React-router est un outil essentiel pour les développeurs qui créent des applications Web avec React. Il facilite la création d'applications monopages (SPA) en gérant efficacement la navigation entre les différents composants.&#x20;

React-router prend en charge le routage dynamique côté client, ce qui permet de mettre à jour les URL et de modifier le contenu sans avoir à actualiser les pages standard. Il en résulte une expérience utilisateur fluide, semblable à celle d'une application.&#x20;

## Qu'est-ce que React Router ? <a href="#what-is-react-router" id="what-is-react-router"></a>

React-router est un outil qui gère le comportement d'une application React lorsque l'utilisateur interagit avec la barre d'adresse du navigateur.&#x20;

Lors de la navigation sur des sites Web, cliquer sur différents liens entraîne généralement le chargement d'une nouvelle page. Mais React-router permet des transitions fluides et rapides entre différentes « pages » ou sections d'un site Web sans avoir à recharger la page entière à chaque clic. C'est similaire à la navigation dans les pages d'un livre au lieu de changer de livre pour chaque nouvelle page. Cette fonctionnalité rend les sites Web plus rapides et offre une expérience plus proche de celle d'une application.

{% hint style="success" %}
Pour les sites Web comportant plusieurs sections ou pages fonctionnant comme une seule application, React-router est particulièrement utile. Il garde une trace de la « page » que vous consultez actuellement, vous permettant de rester sur la bonne page même après avoir actualisé le navigateur.&#x20;
{% endhint %}

### Installation de React Router <a href="#installing-react-router" id="installing-react-router"></a>

Pour commencer à utiliser React-router dans votre projet, vous devez l'installer. Pour ce faire, exécutez la commande suivante dans votre terminal, s'il n'est pas déjà installé :

```bash
npm install react-router-dom
```

L'exécution de cette commande ajoute le package `react-router-dom` à votre projet. Ce package fournit les composants nécessaires au routage dans les applications Web.

Après l'installation, confirmez son ajout en vérifiant votre `package.json.` Recherchez une entrée dans `dependencies` qui ressemble à ceci :

```javascript
"dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.20.1"
  },
```

{% hint style="success" %}
Si vous voyez cela, cela signifie que le `react-router-dom`a été installé avec succès dans votre application.
{% endhint %}

### Comprendre les composants de React Router <a href="#understanding-react-routers-components" id="understanding-react-routers-components"></a>

React-router utilise différents composants pour définir et gérer les routes au sein de votre application :

* **Routeur** : c'est le composant principal qui encapsule et fournit un contexte pour tous les autres composants de routage.
* **Routes** : agit comme un conteneur pour `Route`les composants, définissant les chemins possibles et les composants correspondants.
* **Route** : il représente un chemin unique et le composant à restituer lorsque ce chemin est accessible.

Après avoir installé React-router, importez-le dans votre application.&#x20;

Ajoutez la ligne ci-dessous à votre `App.jsx`:

```javascript
import { BrowserRouter as Router, Route } from 'react-router-dom';
```

```javascript
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";
import Home from './components/Home';
import About from './components/About';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" component={Home} />
        <Route path="/about" component={About} />
      </Routes>
    </Router>
  );
}

export default App;
```

Dans l'exemple, `BrowserRouter`est renommé `Router`pour des raisons de simplicité. À l'intérieur du composant `App`, un composant `Router`est renvoyé en tant que wrapper pour toutes les routes de l'application. Le composant `Routes` définit les différentes routes de l'application, agissant comme un conteneur pour tous les composants `Route`.

Deux `Route`sont spécifiés dans `Routes`. Chaque `Route` représente un itinéraire ou une page différente dans l'application. Pour illustrer diverses pages de navigation, créez le fichier `Home.jsx`et  `About.jsx`.

* La première `Route`, avec un chemin de `/`, est associé au composant `Home`, indiquant que `Home`apparaîtra lorsque les utilisateurs visiteront l'URL racine (/).

```javascript
import React from "react";

const Home = () => {
  return (
    <div className="flex items-center justify-center h-full w-full mt-40">
      <p className="text-[24px] font-bold">Hi, I am home now</p>
    </div>
  );
};

export default Home;
```

![Page d'accueil](https://ucarecdn.com/2851e4a9-b55c-4a33-9d78-316d3769aeba/)

* La deuxième `Route`, avec un chemin `/about`, est associée à `About`. Cela signifie que le composant `About` sera rendu lorsque les utilisateurs accèderont à `/about`.

```javascript
import React from "react";

const About = () => {
  return (
    <div className="flex items-center justify-center h-full w-full mt-40">
      <p className="text-[24px] font-bold">Now this is all about me</p>
    </div>
  );
};

export default About;
```

![À propos de la page](https://ucarecdn.com/b4d899ed-c1f4-4e00-8475-1b5d308b71a4/)

### Comprendre l'attribut exact <a href="#understanding-the-exact-prop" id="understanding-the-exact-prop"></a>

Dans les versions de React Router antérieures à la v6, la propriété `exact` est utilisée dans le composant `Route`pour garantir que le composant ne se charge que lorsque le chemin d'URL correspond parfaitement à la route spécifiée.&#x20;

Ceci est important car React Router utilise un algorithme de correspondance qui, par défaut, effectue une correspondance partielle. Sans `exact`, une route définie avec le chemin `/`correspondrait à n'importe quelle URL, puisque toutes les URL commencent par `/`.&#x20;

Regardons ces routes par exemple :

```javascript
<Route path="/" component={<Home />} />
<Route path="/about" component={<About />} />
```

Sans le `exact`, les deux routes correspondraient au chemin URL `/about`; cela conduirait au rendu des composants Home et About. Mais si nous ajoutons `exact` à la première route :

```javascript
<Route exact path="/" component={Home} />
```

Désormais, le composant  `Home`s'affiche uniquement lorsque le chemin de l'URL correspond exactement à `/`, et non lorsqu'il est `/about`.

L'utilisation de `exact` peut être très utile lorsque vous souhaitez éviter le rendu de plusieurs composants pour des itinéraires étroitement liés et que vous souhaitez garantir que seul le bon composant se charge pour le chemin d'URL exact.

### Avantages de React-Router <a href="#benefits-of-react-router" id="benefits-of-react-router"></a>

React-router améliore considérablement l'expérience utilisateur et le processus de développement des applications Web avec plusieurs fonctionnalités clés :

* **Navigation fluide** : React-router vous permet de vous déplacer entre différentes sections ou « vues » d'une application sans recharger complètement la page, ce qui permet des transitions plus fluides similaires à celles des applications de bureau natives.
* **Chargement de contenu dynamique** : en chargeant dynamiquement le contenu en fonction de votre chemin de navigation, les applications semblent plus interactives et efficaces.
* **Routage côté client** : React-router fonctionne côté client, permettant des réponses instantanées aux actions de l'utilisateur et contournant le processus plus lent du routage côté serveur. Cette méthode améliore l'expérience utilisateur avec des interactions plus rapides, tout en réduisant la charge du serveur et le trafic réseau.
* **Préservation de l'état** : React-router permet de préserver l'état de l'application lorsque vous naviguez dans l'application. En d'autres termes, vos actions et les données de l'application restent cohérentes et intactes tout au long de votre parcours.

{% hint style="info" %}
En utilisant ces avantages, React-router sert de solution robuste pour le développement d'applications monopage riches en fonctionnalités et conviviales.
{% endhint %}

## Comprendre les itinéraires imbriqués <a href="#understanding-nested-routes" id="understanding-nested-routes"></a>

Le routage imbriqué, également appelé routage enfant, implique la définition d'itinéraires au sein d'autres itinéraires.&#x20;

Cette approche hiérarchique du routage reflète la structure des composants de l'application et est utile pour créer des interfaces utilisateur complexes avec plusieurs couches de navigation. Par exemple, imaginez une application de commerce électronique qui possède un composant de produit principal. Dans ce composant, il peut y avoir des itinéraires imbriqués pour des catégories de produits individuelles, telles que l'électronique, les vêtements et les livres. Chaque catégorie peut en outre contenir des itinéraires imbriqués pour des articles spécifiques.

Voici un exemple simple de routage imbriqué dans une application React utilisant React Router :

```javascript
import {
  BrowserRouter as Router,
  Route,
  Routes,
  Outlet,
} from "react-router-dom";
import Home from "./Home";
import About from "./About";
import Dashboard from "./Dashboard";
import Settings from "./Settings";
import Profile from "./Profile";

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/dashboard" element={<DashboardOutlet />}>
          <Route index element={<Dashboard />} />
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
      </Routes>
    </Router>
  );
}

function DashboardOutlet() {
  return (
    <>
      <Outlet />
    </>
  );
}
export default App;
```

* `<Route path="/dashboard" element={<DashboardOutlet />}>`: Il s'agit de la route parente. Elle correspond au chemin d'accès de l'URL `/dashboard`et restitue le `DashboardOutlet`composant. Le `DashboardOutlet`composant est responsable du rendu des composants des routes imbriquées.
* `<Route index element={<Dashboard />} />`: Il s'agit d'une route imbriquée. L'attribut `index` indique que cette route correspond au chemin de base de sa route parente, qui est `/dashboard`dans ce cas. Si un utilisateur navigue vers `/dashboard`, le `Dashboard`sera rendu à l'intérieur du composant `DashboardOutlet.`

![Page d'index du routage imbriqué](https://ucarecdn.com/4dc98721-53cd-4b8a-96d8-80575a885af6/)

* `Route path="settings" element={<Settings />} />`: De même, cette route imbriquée correspond au chemin d'accès de l'URL `/dashboard/settings`. Lorsqu'un utilisateur accède à ce chemin, le composant  `Settings`s'affiche à l'intérieur du `DashboardOutlet`.

![Page de paramètres du routage imbriqué](https://ucarecdn.com/0d8dda5b-d3dd-4617-ab38-ce555cce7e4e/)

* `DashboardOutlet`est un composant fonctionnel qui renvoie un `Outlet`. Le `Outlet`est un composant spécial fourni par React-router qui restitue le composant de route enfant approprié en fonction de l'URL actuelle. Dans cet exemple, si l'URL est `/dashboard/settings`, le `Outlet`restituera le composant `Settings`.

{% hint style="info" %}
Le routage imbriqué est très utile pour organiser les sous-sections d'une application, comme un tableau de bord avec des vues distinctes pour le profil et les paramètres d'un utilisateur.
{% endhint %}

## Itinéraires dynamiques <a href="#dynamic-routes" id="dynamic-routes"></a>

Le routage dynamique dans React fait référence à la capacité de gérer des itinéraires qui ne sont pas fixes mais dépendent de conditions ou de paramètres variables. Il permet la création de chemins flexibles dans la structure d'URL de votre application, où des segments de l'URL agissent comme des variables.

Le routage dynamique est couramment utilisé dans les applications Web pour afficher du contenu ou des données spécifiques à un identifiant unique, tel qu'un ID utilisateur ou un ID produit.&#x20;

Plutôt que de créer un itinéraire distinct pour chaque ID, le routage dynamique vous permet de créer un itinéraire unique pour gérer un nombre infini de possibilités.

### Implémentation du routage dynamique avec react-router <a href="#implementing-dynamic-routing-with-react-router" id="implementing-dynamic-routing-with-react-router"></a>

React-router est une bibliothèque populaire pour la gestion du routage dans les applications React.&#x20;

Elle fournit un ensemble d'outils qui simplifient la mise en œuvre du routage dynamique. Pour y parvenir, React-router utilise des paramètres de routage, qui sont indiqués par deux points ( `:`) suivis du nom du paramètre dans la chaîne de chemin.

Lorsqu'une URL correspond à un modèle de route contenant ces paramètres, React-router capture les valeurs et les transmet comme accessoires au composant concerné. Ce processus permet au composant d'accéder à ces valeurs et de les utiliser de manière dynamique.

Pour démontrer le routage dynamique, vous allez configurer une application React simple avec les composants suivants :

* `App`: Le composant racine qui configure le routeur et définit les routes.
* `ItemList`: Un composant qui affiche une liste d'éléments, chacun avec un lien cliquable pour afficher plus de détails.
* `ItemDetail`: Un composant qui affiche les détails d'un élément individuel en fonction du paramètre d'URL dynamique.

Tout d'abord, assurez-vous que React-router est installé dans votre projet. Ensuite, explorons chaque composant et son rôle dans le routage dynamique.

`App.jsx`: Il s'agit du point d'entrée principal de l'application. Il permet de configurer les routes de notre application.

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import ItemList from './ItemList';
import ItemDetail from './ItemDetail';


const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<ItemList />} />
        <Route path="/item/:itemId" element={<ItemDetail/> } />
      </Routes>
    </Router>
  );
};

export default App;
```

`<Route path="/item/:itemId">`: Ceci définit un itinéraire dynamique pour les détails des éléments individuels.  `:itemId`est un paramètre d'URL qui sera remplacé par l'ID d'élément réel lors de la navigation vers cet itinéraire.

```javascript
import React from 'react';
import { Link } from 'react-router-dom';

const ItemList = () => {
  const items = [
    { id: 1, name: 'Item 1' },
    { id: 2, name: 'Item 2' },
    { id: 3, name: 'Item 3' },
  ];

  return (
    <div>
      <h1>Item List</h1>
      <ul>
        {items.map((item) => (
          <li key={item.id}>
            <Link to={`/item/${item.id}`}>{item.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default ItemList;
```

`ItemList`restitue une liste d'éléments à l'aide d'un tableau d'objets, chacun avec un `id`et un `name`. La fonction `.map()` est utilisée pour parcourir le tableau et générer une liste de `Link`.

![Liste des liens cliquables](https://ucarecdn.com/d33f3338-7a5c-4874-8a9b-c1b33dee9436/)

Chaque `Link`navigue vers l'itinéraire dynamique `/item/:itemId`lorsqu'il est cliqué, avec le `itemId`remplacé par l'ID réel de l'élément cliqué.

```javascript
import React from 'react';
import { useParams } from 'react-router-dom';

const ItemDetail = () => {
  let { itemId } = useParams();

  // Here you would fetch item details from an API or data source based on the itemId
  // For demonstration purposes, we'll just display the itemId

  return (
    <div>
      <h1>Item Detail</h1>
      <p>You are viewing details for item ID: {itemId}</p>
    </div>
  );
};

export default ItemDetail;
```

`ItemDetail.jsx`: Ce composant affiche les détails de l’élément sur lequel l’utilisateur a cliqué.

![page itemId du routage dynamique](https://ucarecdn.com/23141731-bc72-4025-89a9-f74824886a27/)

Le composant utilise le hook `useParams` de React-router pour extraire le `itemId`de l'URL. La route définie dans le composant `App` ( `/item/:itemId`) spécifie qu'il s'agit d'une partie dynamique du chemin.&#x20;

Lorsqu'un utilisateur navigue vers une URL comme `/item/2`, React-router fait correspondre cette URL avec la route définie, extrait la dynamique `itemId`(2 dans ce cas) et la transmet au composant `ItemDetail`.

C'est pourquoi on l'appelle routage « dynamique » : car l'itinéraire `/item/:itemId`peut correspondre à une large gamme d'URL, telles que `/item/1`, `/item/2`, `/item/42`, etc., le `itemId`prenant la valeur du segment correspondant de l'URL.

Les principaux avantages du routage dynamique sont les suivants :

* **Évolutivité** : une seule définition d'itinéraire peut gérer plusieurs chemins, prenant en charge une large gamme d'ID ou de paramètres.
* **Flexibilité** : Le composant rendu par la route peut afficher un contenu qui varie en fonction des paramètres dynamiques reçus.
* **Code plus propre** : le routage dynamique permet d'éviter la prolifération d'itinéraires similaires, conduisant à une base de code plus organisée et plus facile à maintenir.

### Page non trouvée <a href="#handling-page-not-found" id="handling-page-not-found"></a>

Dans les applications React, les utilisateurs peuvent accéder à des itinéraires qui ne correspondent à aucun de vos composants. Dans ces cas, un composant « Page non trouvée » ou d'erreur 404 est utile. Il est essentiel de fournir des commentaires aux utilisateurs lorsqu'ils tentent d'accéder à un itinéraire inexistant dans votre application.

**Implémentation d'un composant d'erreur 404**

Pour gérer ces situations, vous pouvez créer un composant spécial qui affiche un message « Page non trouvée ». Ce composant peut être ajouté au bas de votre configuration de routage pour intercepter les routes non définies :

```javascript
// App.jsx

import React from 'react';
import { BrowserRouter as Router, Routes, Route, Outlet } from 'react-router-dom';
import Home from './Home';
import DashboardLayout from './DashboardLayout';
import Profile from './Profile';
import Settings from './Settings';
import NotFound from './NotFound';

function DashboardLayout() {
  // ... (same as before)
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/dashboard" element={<DashboardLayout />}>
          <Route index element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
        {/* Catch-all route for undefined paths */}
        <Route path="*" element={<NotFound />} />
      </Routes>
    </Router>
  );
}

export default App;
```

Créez un nouveau composant appelé `NotFound`qui sera affiché lors de l'accès à une route non définie :

```javascript
// NotFound.jsx

import React from 'react';

const NotFound = () => {
  return (
    <div>
      <h1>404 - Page Not Found</h1>
      <p>The page you are looking for doesn't exist or has been moved.</p>
    </div>
  );
};

export default NotFound;
```

Le composant `NotFound` est un composant fonctionnel simple qui affiche un message indiquant que la page est introuvable. Vous pouvez styliser ce composant comme vous le souhaitez ou inclure des liens pour rediriger les utilisateurs vers les pages principales de votre application.

Dans le composant `App` nous ajoutons une nouvelle `Route`en bas de nos `Routes`qui utilise le chemin `*`. Ce chemin générique correspondra à toute URL qui ne correspond pas aux autres routes définies.

Lorsqu'un utilisateur tente de naviguer vers un itinéraire qui n'existe pas, React-router rendra le composant`NotFound`, affichant le message d'erreur personnalisé.

![Page d'erreur de la page non trouvée](https://ucarecdn.com/d317c40f-0968-4376-af27-f4ccefb9a93c/)

{% hint style="info" %}
En plaçant la `NotFound`route en dernier, vous vous assurez qu'elle n'attrape que les URL qui ne correspondent à aucune autre route, agissant ainsi comme une solution de secours. Il s'agit d'un moyen efficace de gérer les erreurs 404 dans une application React.
{% endhint %}
