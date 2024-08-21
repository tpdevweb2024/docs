# Premiers pas en TypeScript

TypeScript est un sur-ensemble de JavaScript qui apporte des fonctionnalités de typage statique. Il permet aux développeurs de détecter les erreurs lors de l'écriture du code et de le maintenir plus facilement.

## Installation

Pour commencer avec TypeScript, il est nécessaire de l'installer via npm :

```bash
npm install -g typescript
```

## Configuration

Créez un fichier `tsconfig.json` à la racine de votre projet pour configurer le compilateur TypeScript.

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true
  }
}
```

{% hint style="info" %}
On peut également le créer automatiquement avec la commande `tsc --init`
{% endhint %}

## Votre 1er fichier TypeScript

Créez un fichier `index.ts` avec le contenu suivant :

```typescript
function greet(name: string): string {
  return `Hello, ${name}!`;
}

const message = greet("World");
console.log(message);
```

## Compilation

Pour compiler votre fichier TypeScript en JavaScript, utilisez la commande :

```bash
tsc index.ts
```

{% hint style="success" %}
Félicitations, vous venez de faire vos premiers pas en TypeScript ! Continuez à explorer les fonctionnalités pour améliorer la qualité et la maintenabilité de votre code.
{% endhint %}
