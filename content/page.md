+++
draft = false
title = "Créer une Page"
description = ""
date = "2017-05-01T12:22:24+02:00"
tags = ["tag1","tag2"]

creatordisplayname = "xtof"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"



[menu.main]
parent = ""
identifier = "page"
weight = 10
pre ="<i class='fa fa-edit'></i> "
+++


Hugo-theme-docdock définit deux types de pages. _Default_ et  _Slide_.

* **Default** est la page commune comme celle que vous êtes en train de lire.
* **Slide** est une page qui utilise le plein écran pour afficher son contenu en markdown comme une [présentation reveals.js](http://lab.hakim.se/reveal-js/).
* **HomePage** est un contenu spécial qui s'affichera comme un contenu de page d'accueil.

Pour dire à Hugo-theme-docdock de considérer une page comme un diapo, ajoutez simplement dedans un `type="slide"` dans le frontmatter de votre fichier. [{{%icon circle-arrow-right%}}lisez ceci pour en savoir plus sur la page comme slide]({{%relref "page-slide.md"%}})


Hugo-theme-docdock fournit des archétypes pour vous aider à créer ce type de page.


## Front Matter
Chaque page Hugo doit définir un Front Matter en yaml, toml ou json.

Hugo-theme-docdock utilise les paramètres suivants tout en haut de ceux existants :

	+++
	# Nom Affiché de l'Auteur
	creatordisplayname = "Christophe Ducamp"
	# Email de l'Auteur
	creatoremail = "christophe@ducamp.me"
	# Nom Affiché du Dernier Correcteur
	lastmodifierdisplayname = "Christophe Ducamp"
	# Email du Dernier Correcteur
	lastmodifieremail = "christophe@ducamp.me"
	# Type de contenu, réglez sur "slide" pour l'afficher en plein écran avec reveal.js
	type="page"

	# Menu de configuration
	[menu.main]
	# identifiant de page (s'il est vide l'entrée du menu ne s'affichera pas pour cette page)
	identifier="page-id" 
	# identifiiant de la page parent (si vide, la page sera rattachée à la page racine)
	parent="parent-page-id" 
	# Ordre d'entrée de la page dans le menu
	weight = 1 
	+++


## Ordonner les Pages

Hugo fournit un moyen flexible pour gérer l'ordre de vos pages.

Le moyen de plus simple est d'utiliser le paramètre `weight` dans le front matter de votre page.

Soyez conscient.e que `weight` s'applique séparément pour chaque niveau de menu. 

[{{%icon circle-arrow-right%}}En savoir plus sur l'organisation du contenu]({{%relref "organisation.md"%}})
