# Le type null et undefined

## Le type `null` et `undefined` en TypeScript

En TypeScript, `null` et `undefined` sont deux types distincts représentant l'absence de valeur.

* `null` : Utilisé pour indiquer qu'une variable est intentionnellement vide.
* `undefined` : Indique qu'une variable a été déclarée mais n'a pas encore reçu de valeur.

```typescript
let a: null = null;
let b: undefined = undefined;
```

## Union types

Vous pouvez utiliser les types `null` et `undefined` dans des unions pour permettre à une variable de contenir une de ces valeurs en plus d'autres types.

```typescript
let c: string | null = null;
let d: number | undefined = undefined;
```

## Strict Null Checks

En activant `strictNullChecks`, TypeScript n'autorisera pas l'utilisation de `null` ou `undefined` sauf s'ils sont explicitement mentionnés dans le type.

```typescript
let e: string = "Hello";
// e = null; // Erreur si `strictNullChecks` est activé
```

{% hint style="info" %}
Pour activer cette option, ajoutez `"strictNullChecks": true` dans votre `tsconfig.json`.
{% endhint %}
