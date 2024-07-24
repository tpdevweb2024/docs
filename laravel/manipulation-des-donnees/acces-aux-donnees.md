# Accès aux données

## Le rôle du Controller

Comme nous l'avons vu précédemment, **la table cars est parfaitement créée**, et comme dans toute application, **nous aurons l'utilité du CRUD** dans notre logique métier. Ainsi, Laravel nous propose comme à son habitude une solution pour simplifier l'utilisation du CRUD dans son ergonomie orientée Framework.



**Car** étant considéré comme un modèle ou une entité de notre structure, nous avions créer un Controller dédié, cependant ne l'ayant pas fait au moment de sa création, nous allons donc recréer notre Controller avec un flag resources :&#x20;

{% hint style="warning" %}
Après avoir supprimé le fichier CarController.php situé dans app/Http/Controllers, nous allons entrer la commande suivante :&#x20;
{% endhint %}

```shell
php artisan make:controller CarController -r
```

Analysez maintenant le fichier nouvellement créé :&#x20;

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class CarController extends Controller
{
    /**
     * Display a listing of the resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function index()
    {
        //
    }

    /**
     * Show the form for creating a new resource.
     *
     * @return \Illuminate\Http\Response
     */
    public function create()
    {
        //
    }

    /**
     * Store a newly created resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return \Illuminate\Http\Response
     */
    public function store(Request $request)
    {
        //
    }

    /**
     * Display the specified resource.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function show($id)
    {
        //
    }

    /**
     * Show the form for editing the specified resource.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function edit($id)
    {
        //
    }

    /**
     * Update the specified resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function update(Request $request, $id)
    {
        //
    }

    /**
     * Remove the specified resource from storage.
     *
     * @param  int  $id
     * @return \Illuminate\Http\Response
     */
    public function destroy($id)
    {
        //
    }
}
```
