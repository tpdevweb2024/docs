---
description: >-
  La fonction store() est quant à elle destinée à la création d'un nouvel Objet
  en base de données, d'une nouvelle ligne dans notre table.
---

# La méthode store()

Pour cela, nous récupèrerons les données envoyées en toute logique par le formulaire créé dans la vue create() précédente, et nous viendrons définir un objet sur la base du Model correspondant à la table.

Ce qui pourrait donner, dans le cas où nous stockons toujours une Annonce :&#x20;

```php

    /**
     * Store a newly created resource in storage.
     *
     * @param  \Illuminate\Http\Request  $request
     * @return \Illuminate\Http\Response
     */
    public function store(Request $request)
    {
        $request->validate([
             "brand_id" => "required",
             "serie_id" => "required",
             "price" => "required",
             "color" => "required",
             "power_dyn" => "required",
             "power_fisc" => "required",
         ]);
    
        // On créé une instance de Car
        $car = new Car();
        
        // On définit les valeurs de l'objet à insérer
        $car->brand_id = $request->brand_id;
        $car->serie_id = $request->serie_id;
        $car->power_fisc= $request->power_fisc;
        $car->power_dyn= $request->power_dyn;
        $car->price = $request->price;
        $car->color= $request->etat;
        
        // On envoit les données en base sous la forme du Model 
        $car->save();
        
        return redirect()->route("cars.index");
        
    }
```

{% hint style="warning" %}
Dans le cas de l'utilisation de Laravel en mode MVC, il est alors conseillé de rediriger notre utilisateur vers l'une de nos vues. Dans le cas d'une utilisation API, alors peut être simplement retourner un code ainsi qu'un message en fonction de réussite ou d'échec de l'appel.
{% endhint %}
