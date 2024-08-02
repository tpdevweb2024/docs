# L'upload de fichier

Uploader un fichier sous Laravel consiste à utiliser le storage path, celui-ci étant décomposé en 2 parties :

* Le local path disponible dans le dossier **storage** puis **app**
* Le public path disponible dans le dossier **storage** -> **app** puis **public**

Il faut bien distinguer l'utilité de ces dossiers, l'un permettra aux internautes de stocker et de visualiser les fichiers, au travers d'une image ou d'un DL, l'autre aura quant à lui pour but de stocker simplement un fichier.

## Modification du formulaire

Pour permettre l'Upload, tout comme en HTML, il faut **ajouter à votre balise form l'enctype "multipart/form-data"**, et ce formulaire devra être soumis en POST :

```markup
<form action="{{ route("car.store") }}" method="post" enctype="multipart/form-data">
    @csrf
    <input type="text" name="title" value="" required>
    <br>
    <textarea name="content" id="content" cols="30" rows="10"></textarea>
    <br>
    <input type="file" name="picture" id="picture">
    <br>
    <input type="submit" value="Créer">
</form>
```

## Modification du Controller

Une fois le formulaire prêt à envoyer nos fichiers, vient le tour de notre Controller :

```php
    public function store(Request $request)
    {
        $name = Storage::disk('local')->put('folderName', $request->picture);
        dd($name);
    }
```

Laravel se chargera tout seul de donner un nom à notre fichier. C'est ce nom de fichier qu'il sera nécessaire de stocker en base afin de pouvoir ensuite récupérer ces fichiers.

Remarquons l'utilisation de la classe Storage, native de Laravel, et permettant de d'abord, au travers de la méthode "disk", spécifier le dossier de stockage, dans ce cas à la racine du dossier **storage/app,** dans lequel nous allons créer un dossier **folderName**, qui comprendra le nom de l'image.

{% hint style="warning" %}
Si nous avions spécifier le disk("public"), nos documents se seraient alors stocké dans le dossier **storage/app/public, puis le dossier folderName et le nom du fichier** et non dans le dossier public à la racine de notre site.
{% endhint %}

## Récupération de l'URL du fichier

Pour récupérer l'URL de l'un de nos fichiers et l'afficher dans notre \<img src=""> par exemple, nous pourrions alors utiliser la classe Storage avec la méthode url() :

```php
$url = Storage::url($nomdufichier);
// il s'agit bel et bien du nom du fichier stocké en base

// output : "/storage/folderName/QT9oVLFeiMKRP6Ktu8Ged6xAdA2SWh1Qq476ZM39.jpg"
```

## Permettre le téléchargement&#x20;

&#x20;Assez similaire à l'obtention de l'URL ci-dessus, le Download s'effectue quant à lui ainsi :

```php
return Storage::download($nomdufichier);
// il s'agit bel et bien du nom du fichier stocké en base

// il ne faut pas stocker le download dans une variable puisque
// lancera le téléchargement forcé dans le navigateur
```
