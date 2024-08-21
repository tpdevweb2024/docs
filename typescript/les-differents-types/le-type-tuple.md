# Le type tuple

Le type tuple en TypeScript permet de définir un tableau dont les éléments ont des types bien spécifiques et souvent variés. Un tuple est défini en spécifiant les types des éléments entre crochets, séparés par des virgules.

## Syntaxe de Base

```typescript
let tuple: [string, number];
tuple = ["hello", 10]; // Correct
tuple = [10, "hello"]; // Incorrect
```

## Avantages des Tuples

* Permet de définir des ensembles de valeurs hétérogènes.
* Offre une meilleure vérification de type lors du développement.

### Exemple d'Utilisation

```typescript
let user: [number, string, boolean];
user = [1, "John Doe", true];
```

{% hint style="info" %}
Les tuples sont particulièrement utiles lorsque vous avez besoin d'un ensemble fixe de valeurs de types différents.
{% endhint %}
