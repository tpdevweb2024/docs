# Le type any

## Pourquoi utiliser `any` ?

Le type `any` en TypeScript permet de désactiver le vérificateur de type pour une variable. Cela peut être utile lorsque :

* On migre une base de code JavaScript vers TypeScript.
* On manipule une donnée dont le type est inconnu ou variable.
* On intègre des bibliothèques externes non typées.

## Comment utiliser `any` ?

Pour déclarer une variable de type `any`, utilisez la syntaxe suivante :

```typescript
let variable: any;
```

## Pourquoi éviter `any` ?

L'utilisation excessive de `any` peut annuler les avantages de TypeScript, comme la vérification stricte des types. Il est préférable de :

* Utiliser des types spécifiques ou des types d'union.
* Utiliser des types génériques.
* Écrire des types personnalisés pour les données complexes.
