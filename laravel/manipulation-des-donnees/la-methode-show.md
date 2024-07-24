# La méthode show()

Le but de la méthode show() est d'afficher, comme son nom l'indique, une voiture en particulier.

Ainsi, cela en fait le Controller le plus simple à paramétrer :&#x20;

```php
/**
 * Display the specified resource.
 *
 * @param  App\Model\Car $car
 * @return \Illuminate\Http\Response
 */
public function show(Car $car)
{
    return view("cars.show", [
        "car" => $car
    ]);
}
```

Côté routes, on lui passe simplement un Tag, qui a le même nom que le paramètre, en l'occurence $car :&#x20;

```php
Route::get("/cars/{car}", [CarController::class, "show"]);
```
