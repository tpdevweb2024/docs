# L'utilisation des interfaces

En TypeScript, les interfaces sont un outil puissant qui permet de définir des contrats pour les objets.&#x20;

Elles spécifient la structure qu'un objet doit respecter, ce qui facilite la vérification des types, améliore la lisibilité du code, et contribue à la robustesse du développement.

## **Définition d'une interface**

Une interface en TypeScript est utilisée pour décrire la forme d'un objet. Elle définit les propriétés que l'objet doit avoir, ainsi que leurs types. Voici comment tu peux déclarer une interface simple :

```typescript
interface Person {
    name: string;
    age: number;
}
```

Dans cet exemple :

* **`interface`** : Le mot-clé `interface` est utilisé pour définir une nouvelle interface.
* **`Person`** : Le nom de l'interface est `Person`. Cette interface décrit un objet qui doit avoir deux propriétés : `name` et `age`.
* **`name: string`** : La propriété `name` est de type `string`, ce qui signifie que cette propriété doit toujours contenir une chaîne de caractères.
* **`age: number`** : La propriété `age` est de type `number`, ce qui impose que cette propriété contienne un nombre.

## **Utilisation d'une interface**

Une fois qu'une interface est définie, elle peut être utilisée pour typer des objets, des paramètres de fonctions, ou même des classes. Voici un exemple d'utilisation de l'interface `Person` :

```typescript
const logPerson = (person: Person) => {
    console.log(`${person.name} is ${person.age} years old.`);
};

const person: Person = {
    name: "Alice",
    age: 30
};

logPerson(person);
```

Dans cet exemple :

* **`person: Person`** : L'objet `person` est typé avec l'interface `Person`, ce qui signifie qu'il doit avoir les propriétés `name` et `age` avec les types correspondants.
* **`logPerson(person)`** : La fonction `logPerson` prend un paramètre de type `Person`. TypeScript vérifiera que l'objet passé à cette fonction respecte bien la structure définie par l'interface `Person`.

## **Avantages des interfaces**

### **Vérification des types**

Les interfaces permettent à TypeScript de vérifier que les objets respectent une certaine structure, ce qui prévient les erreurs courantes liées aux types de données. Par exemple, si tu essaies de passer un objet qui ne respecte pas l'interface `Person`, TypeScript te signalera une erreur :

```typescript
const person = {
    name: "Alice",
    // age manquant ici
};

logPerson(person); // Erreur : La propriété 'age' est manquante dans le type
```

### **Réutilisation du code**

Les interfaces facilitent la réutilisation du code, car elles peuvent être étendues et combinées pour créer de nouvelles interfaces. Cela permet de maintenir une structure cohérente tout en évitant la duplication de code.

### **Auto-complétion et Intellisense**

Comme avec les types, les interfaces permettent aux éditeurs de code de fournir une auto-complétion intelligente. Lors de la manipulation d'objets conformes à une interface, l'éditeur peut suggérer automatiquement les propriétés disponibles.

## **Extension des interfaces**

Une interface peut étendre une ou plusieurs autres interfaces, ce qui permet de créer des interfaces plus complexes à partir d'autres interfaces existantes. Cela encourage la réutilisation et la modularité du code.

```typescript
interface Named {
    name: string;
}

interface Aged {
    age: number;
}

interface Employee extends Named, Aged {
    employeeId: number;
}

const employee: Employee = {
    name: "Bob",
    age: 45,
    employeeId: 12345
};
```

Dans cet exemple :

* **`Named` et `Aged`** : Ce sont des interfaces de base qui définissent des propriétés individuelles.
* **`Employee extends Named, Aged`** : L'interface `Employee` étend les interfaces `Named` et `Aged`, ce qui signifie qu'un `Employee` doit avoir les propriétés `name`, `age`, et `employeeId`.
* **`employee`** : L'objet `employee` doit maintenant respecter la structure définie par l'interface `Employee`.

## **Interfaces vs types**

En TypeScript, les interfaces et les types (`type`) sont similaires, mais ils ont quelques différences subtiles :

* **Interfaces** : Sont mieux adaptées pour définir la structure des objets et sont extensibles. Les interfaces peuvent être fusionnées (déclaration ouverte), ce qui permet de les enrichir à travers plusieurs déclarations.
* **Types** : Sont plus flexibles et peuvent être utilisés pour des unions, des intersections, et d'autres types plus complexes. Cependant, les types ne peuvent pas être étendus de la même manière que les interfaces.

## **Implémentation dans les classes**

Les interfaces peuvent aussi être utilisées pour définir les contrats que les classes doivent respecter. Une classe qui implémente une interface doit définir toutes les propriétés et méthodes de cette interface.

```typescript
interface Logger {
    log(message: string): void;
}

class ConsoleLogger implements Logger {
    log(message: string): void {
        console.log(message);
    }
}

const logger = new ConsoleLogger();
logger.log("Logging a message");
```

Dans cet exemple :

* **`Logger`** : Une interface avec une méthode `log` qui accepte un message de type `string`.
* **`ConsoleLogger implements Logger`** : La classe `ConsoleLogger` implémente l'interface `Logger`, ce qui signifie qu'elle doit avoir une méthode `log` conforme à la signature définie dans `Logger`.

{% hint style="info" %}
Les interfaces améliorent la robustesse, la lisibilité, et la réutilisation du code en imposant des contrats clairs pour les objets, et en offrant des fonctionnalités telles que l'extension d'interfaces et l'implémentation dans les classes.&#x20;
{% endhint %}
