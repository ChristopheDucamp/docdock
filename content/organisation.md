+++
draft = false
title = "Organisation du Contenu"
description = ""

[menu.main]
parent = ""
identifier = "organisation"
weight = 20

+++

Avec **Hugo**, les pages sont le coeur de votre site. Organisez votre site comme tout autre projet Hugo. **La magie se passe dans le frontmatter de chaque contenu**.


# Menu
Hugo dispose d'un [système de menu](https://gohugo.io/extras/menus/) simple et puissant qui permet au contenu d'être placé dans les menus avec un bon niveau de contrôle sans trop de travail, dans les pages de contenus.

**Chaque page de contenu compose le menu**, elles façonnent la structure de votre site web.

Pour lier les pages entre elles : 

* Dans le frontmatter de chaque page de contenu ;
	* Réglez l'identifiant `parent`.
	* Réglez l'identifiant `identifier` de votre contenu.


{{%alert info %}} **identifier** doit être une étiquette unique dans tout votre contenu {{%/alert%}}

{{%alert warning %}} si **parent** est vide, le contenu sera placé au niveau racine (enfant de la page d'accueil) {{%/alert%}}

Dans cet exemple, "Ma page Papa" sera rattachée à la racine, menu de niveau 1.

	+++
	title = "Ma page Papa"

	[menu.main]
	identifier = "daddy"
	+++


Dans cet exemple "Ma page Enfant" sera rattachée à la page "daddy", et affichée sous un menu de niveau 2.

	+++
	title = "Ma page Enfant"

	[menu.main]
	identifier = "child"
	parent="daddy"
	+++

### Ajouter une icône à l'entrée de menu

dans le frontmatter de la page, ajoutez un param `pre` pour insérer tout code HTML avant l'étiquette de menu : 

exemple pour afficher une icône github

	+++
	[menu.main]
	parent = ""
	identifier = "repo"
	pre ="<i class='fa fa-github'></i> "
	+++

![dsf](/menu-entry-icon.png?height=40px&classes=shadow)

### Personnaliser une étiquette d'entrée de menu

Ajoutez un param `name` à côté de `[menu.main]`

	+++
	[menu.main]
	parent = ""
	identifier = "repo"
	pre ="<i class='fa fa-github'></i> "
	name = "Github repo"
	+++

### Créer une redirection de page 
Ajoutez un param `url` à côté de `[menu.main]`

	+++
	[menu.main]
	parent = "page"
	identifier = "page-images"
	weight = 23
	url = "/shortcode/image/"
	+++

{{%alert info%}}Regardez le menu "Créer une Page/À Propos des images" qui redirige vers "Shortcodes/image"{{%/alert%}}

### Ordre des entrée menu/page frères et soeurs

dans le [menu.main] ajoutez le param `weight` avec un numéro pour trier.

	+++
	[menu.main]
	identifier = "child"
	parent="dady"
	weight = 4
	+++


### Cacher une entrée de menu

Ne configurez pas l'identifier pour masquer une entrée provenant du ... menu.
Votre contenu reste joint à sa page parent.


### Structure de répertoire et nom de fichier

L'organisation du contenu n'est pas votre structure de répertoire.
Sentez-vous libre de sauvegarder votre fichier .md comme vous voulez, il peut ne pas refléter forcément votre organisation de menu.

### Page d'Accueil

Découvrez comment [personnaliser votre page d'accueil]({{%relref "homepage.md"%}}) 



