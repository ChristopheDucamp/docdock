+++
title = "attachments"
description = "Le shortcode Attachments affiche une liste de fichiers attachés à une page."

[menu.main]
parent = "shortcodes"
identifier = "attachments"
+++

Le shortcode Attachments affiche une liste de fichiers attachés à une page.
Exemple :
{{%alert success%}}
{{%attachments  /%}}
{{%/alert%}}
## Usage 

Le raccourci liste les fichiers trouvés dans un **répertoire** appelé comme votre page et finissant par **.files**.

When your page is named "mypage.md", create a folder named mypage**.files** and place your files in it. that's all !

{{%alert info%}}**Tip** : Look at this documentation source code on github{{%/alert%}}

### paramètres

| Paramètre | Par défaut | Description |
|:--|:--|:--|
| titre | "Attachments" | titre de liste  |
| pattern | ".*" | Une expression regulière, utilisée pour filtrer les pièces jointes par nom de fichier. <br/><br/>{{%alert warning%}}La valeur du paramètre **pattern** doit être une [regular expressions](https://en.wikipedia.org/wiki/Regular_expression). 

Par exemple :

* Pour correspondre à un suffixe de fichier de 'jpg', utilisez  **.*jpg** (pas *.jpg).
* Pour correspondre à des noms de fichiers finissant par 'jpg' ou 'png', utilisez **.*(jpg|png)**

{{%/alert%}}|






## Démo
### Liste de pièces jointes finissant par pdf ou mp4

	{{%/*attachments title="Related files" pattern=".*(pdf|mp4)"/*/%}}

donne ceci

{{%attachments title="Related files" pattern=".*(pdf|mp4)"/%}}

