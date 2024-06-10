# Débuter en PHP

## Insérer du PHP dans une page web <a href="#inserer-du-php-dans-une-page-web" id="inserer-du-php-dans-une-page-web"></a>

Pour inclure du PHP dans un bloc HTML, il suffit d’utiliser les balises ci-contre.​

`<?php echo "texte" ; ?>​`

`<?= "texte" ?>​`

```php
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,
    initial-scale=1.0">
    <title>PHP</title>
</head>
    <body>
    <?php echo "Cette ligne est écrite en PHP"; ?>
    <?= "Cette ligne est aussi écrite en PHP" ?>
    </ body>
</html>
```

{% hint style="info" %}
**Bon à savoir :​** Le code inclut dans ces balises ne sera jamais visible dans le code source d’une page web
{% endhint %}
