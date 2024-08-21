# Le type object

Le type `object` en TypeScript est utilisé pour représenter les valeurs non primitives, c'est-à-dire les valeurs qui ne sont ni `number`, ni `string`, ni `boolean`, ni `symbol`, ni `null`, ni `undefined`.

Le type `object` peut être utilisé lorsque nous voulons spécifiquement travailler avec des objets, mais sans contrainte particulière sur leur structure. C'est un type très général et flexible.

```typescript
let obj: object;
obj = { name: "Alice", age: 30 }; // Valide
obj = [1, 2, 3]; // Valide
obj = function() {}; // Valide
obj = new Date(); // Valide
```

Cependant, pour créer des objets avec une structure définie, il est préférable d'utiliser des types ou des interfaces spécifiques :

```typescript
interface Person {
    name: string;
    age: number;
}

let person: Person;
person = { name: "Alice", age: 30 }; // Valide
person = { name: "Bob" }; // Erreur : Age manquant
```

{% hint style="warning" %}
Le type `object` offre une grande souplesse, mais à utiliser avec précaution pour garantir la clarté et la maintenabilité du code.
{% endhint %}
