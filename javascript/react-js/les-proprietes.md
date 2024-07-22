# Les propriétés

Les `props` (propriétés) en React sont un moyen de passer des données d'un composant parent à un composant enfant. Elles rendent les composants réutilisables et dynamiques.

## Utilisation des Props

Pour définir une prop, vous devez d'abord l'ajouter comme attribut au composant enfant dans le composant parent. Ensuite, vous récupérerez cette prop dans le composant enfant via l'objet `props`.

Ici, `nom` est la prop définie dans le composant parent et utilisée dans le composant enfant.

```jsx
function Parent() {
  return <Enfant nom="Alice" />;
}
```

```jsx
function Enfant(props) {
  return <h1>Bonjour, {props.nom}!</h1>;
}
```

Pour définir des props dans un composant React, ajoutez-les comme attributs au composant enfant dans le composant parent et récupérez-les via l'objet `props`. Par exemple, dans le composant parent, définissez `<Enfant nom="Alice" />` et utilisez `props.nom` dans l'enfant.&#x20;

Vous pouvez également définir des valeurs par défaut pour les props et les rendre obligatoires avec `PropTypes`.

## Types de Props

### Props par défaut

Les props par défaut permettent de définir des valeurs par défaut pour les propriétés d'un composant lorsqu'elles ne sont pas fournies. Cela garantit que le composant fonctionne correctement même si certaines props sont manquantes.

Voici comment définir des props par défaut dans un composant React :

```jsx
function Enfant({ nom = "Invité" }) {
  return <h1>Bonjour, {nom}!</h1>;
}
```

{% hint style="info" %}
Dans cet exemple, si la prop `nom` n'est pas passée au composant `Enfant`, elle prendra la valeur par défaut "Invité".
{% endhint %}

### Props obligatoires avec PropTypes

Les `PropTypes` sont un mécanisme de type-checking intégré à React qui permet de valider les types des props passées à un composant.&#x20;

{% hint style="info" %}
L'utilisation de `PropTypes` aide à détecter les bugs potentiels en s'assurant que les composants reçoivent les bonnes données sous les bons formats.
{% endhint %}

Voici pourquoi il est bénéfique d'utiliser les `PropTypes` :

* **Validation des données**: Ils permettent de vérifier que les props reçues par un composant sont du bon type.
* **Documentation**: Ils servent de documentation pour les autres développeurs, en indiquant clairement quelles props sont attendues et de quel type elles doivent être.
* **Développement robuste**: En alertant des erreurs potentielles lors du développement, ils aident à rendre vos composants plus fiables et robustes.

Le composant utilise `PropTypes` pour s'assurer que la prop `nom` est bien fournie et qu'il s'agit d'une chaîne de caractères (`string`). L'exigence de cette prop est spécifiée avec `isRequired`, garantissant que le composant ne fonctionnera pas correctement sans cette prop. Voici un résumé du code :

1. Importation de `PropTypes` depuis la bibliothèque `prop-types`.
2. Définition du composant `Enfant` qui prend la prop `nom` et renvoie un élément `h1` affichant "Bonjour, {nom}!".
3. Définition des `propTypes` pour le composant `Enfant`, spécifiant que `nom` doit être une chaîne de caractères et est obligatoire.

```jsx
import PropTypes from 'prop-types';

function Enfant({ nom }) {
  return <h1>Bonjour, {nom}!</h1>;
}

Enfant.propTypes = {
  nom: PropTypes.string.isRequired,
};
```

Ce code définit un composant React nommé `Enfant` qui affiche un message de salutation. La prop `nom` est utilisée pour personnaliser ce message.

{% hint style="info" %}
Les `props` sont essentiels pour créer des composants React flexibles et modulaires. Ils permettent de transmettre des données et de configurer les composants de manière dynamique.
{% endhint %}
