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

Quand votre page est nommée "mypage.md", créez un répertoire nommé mypage**.files** et placez vos fichiers à l'intérieur. c'est tout !

{{%alert info%}}**Truc** : Regardez ce codes source de documentation sur github{{%/alert%}}

### paramètres

| Paramètre | Par défaut | Description |
|:--|:--|:--|
| titre | "Attachments" | titre de liste  |
| pattern | ".*" | Une expression regulière, utilisée pour filtrer les pièces jointes par nom de fichier. <br/><br/>{{%alert warning%}}La valeur du paramètre **pattern** doit être une [expression rationnelle](https://fr.wikipedia.org/wiki/Expression_rationnelle). 

Par exemple :

* Pour correspondre à un suffixe de fichier de 'jpg', utilisez  **.*jpg** (pas *.jpg).
* Pour correspondre à des noms de fichiers finissant par 'jpg' ou 'png', utilisez **.*(jpg|png)**

{{%/alert%}}|






## Démo
### Liste de pièces jointes finissant par pdf ou mp4

	{{%/*attachments title="Fichiers en rapport" pattern=".*(pdf|mp4)"/*/%}}

donne ceci

{{%attachments title="Fichiers en rapport" pattern=".*(pdf|mp4)"/%}}

