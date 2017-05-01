+++
draft = false
title = "image"
description = ""

[menu.main]
parent = "shortcodes"
identifier = "image"
+++

Les images ont une syntaxe similaire aux liens mais sont précédées d'un point d'exclamation.

	![agence](https://github.com/vjeantet/vjeantet.fr/raw/master/static/images/sgthon/C.jpg)

![agence](https://github.com/vjeantet/vjeantet.fr/raw/master/static/images/sgthon/C.jpg)

## Retailler une image

Ajoutez des paramètres HTTP `width` et/ou `height` au lien image  pour retailler l'image. Les valeurs sont des valeurs CSS (par défaut `auto`).


	![Hackathon](https://github.com/vjeantet/vjeantet.fr/raw/master/static/images/sgthon/C.jpg?height=80px)

![agence](https://github.com/vjeantet/vjeantet.fr/raw/master/static/images/sgthon/C.jpg?height=80px)


## Ajout de classes CSS 

Ajoutez un param HTTP `classes` au lien image pour ajouter des classes CSS. `shadow` et `border` sont disponibles mais vous pourriez en définir d'autres.

	![agence](https://github.com/vjeantet/vjeantet.fr/raw/master/static/images/sgthon/C.jpg?classes=border,shadow)

![agence](https://github.com/vjeantet/vjeantet.fr/raw/master/static/images/sgthon/C.jpg?classes=border,shadow)
