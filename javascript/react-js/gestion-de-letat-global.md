# Gestion de l'état global

## **Lever l'état (Lifting state up)**

**Concepts à couvrir :**

* Partager l'état entre plusieurs composants en remontant l'état à leur plus proche ancêtre commun.
* Illustrer comment lever l'état permet de synchroniser les données entre différents composants.

**Contenu :**

1. **Exemple de code pour lever l'état :**

```jsx
import React, { useState } from 'react';

// Composant enfant
function TemperatureInput({ temperature, onTemperatureChange }) {
  return (
    <fieldset>
      <legend>Entrez la température en Celsius :</legend>
      <input
        value={temperature}
        onChange={e => onTemperatureChange(e.target.value)}
      />
    </fieldset>
  );
}

// Composant parent
function Calculator() {
  const [temperature, setTemperature] = useState('');

  return (
    <div>
      <TemperatureInput 
        temperature={temperature} 
        onTemperatureChange={setTemperature} 
      />
      <BoilingVerdict celsius={parseFloat(temperature)} />
    </div>
  );
}

// Composant pour afficher le verdict
function BoilingVerdict({ celsius }) {
  if (celsius >= 100) {
    return <p>L'eau bout.</p>;
  }
  return <p>L'eau ne bout pas.</p>;
}

export default Calculator;
```

**Explication :**

* **TemperatureInput** : Composant enfant qui affiche un champ de saisie.
* **Calculator** : Composant parent qui contient l'état `temperature` et passe cet état ainsi que la fonction pour le mettre à jour au composant enfant via des props.
* **BoilingVerdict** : Composant qui utilise l'état pour afficher un message basé sur la température.

## Comprendre le Prop Drilling

**Concepts à couvrir :**

* Prop drilling : Problème de devoir passer des props à travers plusieurs niveaux de composants.
* Solutions potentielles : Utilisation de Context API pour éviter le prop drilling.

**Contenu :**

1. **Exemple de prop drilling :**

```jsx
import React, { useState } from 'react';

// Composant de niveau 3
function LevelThree({ data }) {
  return <div>Niveau 3: {data}</div>;
}

// Composant de niveau 2
function LevelTwo({ data }) {
  return <LevelThree data={data} />;
}

// Composant de niveau 1
function LevelOne({ data }) {
  return <LevelTwo data={data} />;
}

// Composant parent
function App() {
  const [data, setData] = useState('Données partagées');

  return (
    <div>
      <LevelOne data={data} />
    </div>
  );
}

export default App;
```

**Explication :**

* L'état `data` est créé dans le composant `App` et est passé à travers plusieurs niveaux de composants jusqu'à `LevelThree`.
* Cela peut devenir difficile à gérer lorsque l'arborescence des composants devient profonde.

## Introduction à Context API

**Concepts à couvrir :**

* Utilisation de Context API pour la gestion de l'état global.
* Création et utilisation d'un contexte.

**Contenu :**

1. **Création d'un contexte :**

```jsx
import React, { useState, createContext, useContext } from 'react';

// Créer le contexte
const DataContext = createContext();

// Fournisseur de contexte
function DataProvider({ children }) {
  const [data, setData] = useState('Données partagées');

  return (
    <DataContext.Provider value={{ data, setData }}>
      {children}
    </DataContext.Provider>
  );
}

// Composant de niveau 3
function LevelThree() {
  const { data } = useContext(DataContext);
  return <div>Niveau 3: {data}</div>;
}

// Composant de niveau 2
function LevelTwo() {
  return <LevelThree />;
}

// Composant de niveau 1
function LevelOne() {
  return <LevelTwo />;
}

// Composant parent
function App() {
  return (
    <DataProvider>
      <LevelOne />
    </DataProvider>
  );
}

export default App;
```

**Explication :**

* **DataContext** : Création d'un contexte pour partager l'état `data`.
* **DataProvider** : Composant fournisseur qui utilise `DataContext.Provider` pour passer l'état et sa fonction de mise à jour à ses descendants.
* **useContext** : Utilisation du hook `useContext` dans `LevelThree` pour accéder à l'état `data`.
