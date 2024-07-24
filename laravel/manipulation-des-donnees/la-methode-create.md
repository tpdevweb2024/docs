# La méthode create()

Cette méthode n'est en réalité que l'affichage d'une vue comprenant un formulaire de saisie, vous avez tout loisir de créer cette page comme vous le souhaitez.

Néanmoins, il est fortement recommandé, pour des questions de gestion des données, de données des name pertinents à vos différents inputs.

Prenons alors un formulaire simple que nous allons ajouter à notre page create.

## Refactoring

{% hint style="info" %}
Et si nous prenions le temps de retravailler quelque peu notre stockage de vues ?
{% endhint %}

Toujours pour des questions de convention, il est très apprécié dans le monde des dev Laravel, de créer des répertoires destinées à nos vues, ainsi nous pourrions créer un dossier cars, qui contiendrait notre index déjà existant, mais aussi nos futures vues, comme la vue create, ce qui nous donnerait une structure telle que :&#x20;

```
laracars
└─  📂 resources/
    └─  📂 views/
        └─  📂 cars/
            📇 create.blade.php
            📇 index.blade.php
            📇 ...
```

{% hint style="success" %}
**Plus clair non ?** :smile:&#x20;

Oui mais attention à retravailler au sein de notre méthode index du CarController la vue à utiliser qui ne sera plus "index" mais "cars.index".
{% endhint %}

## Composition du formulaire

Créons ensemble notre formulaire de création de véhicule :&#x20;

```php
@extends("layouts.app")

@section("content")
    <h1>Ajouter une voiture</h1>
    <form action={{ route("cars.store") }} method="POST">
        @csrf
        <div>
            <label for="brand_id">Marque</label>
            <select id="brand_id" name="brand_id" required>
                @foreach($brands as $brand)
                    <option value="{{ $brand->id }}">{{ $brand->name }}</option>
                @endforeach
            </select>
        </div>
        <div>
            <label for="serie_id">Modele</label>
            <select id="serie_id" name="serie_id" required  />
                @foreach($series as $serie)
                    <option value="{{ $serie->id }}">{{ $serie->name }}</option>
                @endforeach
            </select>
        </div>
        <div>
            <label for="price">Prix</label>
            <input type="number" step="0.01" id="price" name="price" required value="{{ old("price") }}" />
            @error("price")
                Remplis mieux que ça !
            @enderror
        </div>
        <div>
            <label for="color">Couleur</label>
            <input type="number" id="color" name="color" required value="{{ old("color") }}" />
            @error("color")
                Remplis mieux que ça !
            @enderror
        </div>
        <div>
            <label for="power_dyn">Puissance dynamique</label>
            <input type="number" id="power_dyn" name="power_dyn" required value="{{ old("power_dyn") }}"/>
            @error("power_dyn")
                Remplis mieux que ça !
            @enderror
        </div>
        <div>
            <label for="power_fisc">Puissance fiscale</label>
            <input type="number" id="power_fisc" name="power_fisc"  value="{{ old("power_fisc") }}" required />
            @error("power_fisc")
                Remplis mieux que ça !
            @enderror
        </div>
        <div>
            <input type="submit" value="Créer ma voiture">
        </div>
    </form>
@endsection
```

## Le Controller

```php
public function create()
{
    $brands = Brand::all();
    $series = Serie::all();
    return view("cars.create", compact("brands", "series");
}
```
