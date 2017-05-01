+++
title = "Entrée menu supplémentaires"
date = "2017-05-01T13:22:24+02:00"

creatordisplayname = "Christophe Ducamp"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"

[menu.main]
name = "Entrées supplémentaires du menu"
parent = "organisation"
identifier = "extra-menu"
weight = 21

+++

Vous pouvez définir des entrées de menu supplémentaires dans le menu de navigation sans quelque lien vers le contenu.

Modifiez la configuration du site web `config.toml` et ajoutez une entrée `[[menu.shortcuts]]` pour chaque lien que vous voulez ajouter.


Exemple pour le site web actuel, **remarquez le param  `pre`** qui vous permet d'insérer du code HTML et utilisé ici pour séparer le contenu du menu de ce menu "statique"  

	[[menu.shortcuts]]
	pre = "<h3>Plus</h3>"
	name = "<i class='fa fa-github'></i> Dépôt Github"
	identifier = "ds"
	url = "https://github.com/ChristopheDucamp/docdock"
	weight = 1

	[[menu.shortcuts]]
	name = "<i class='fa fa-bookmark'></i> Documentation Hugo"
	identifier = "hugodoc"
	url = "https://gohugo.io/"
	weight = 2


[{{%icon circle-arrow-right%}} Lire ceci ici concernant Hugo et le menu](https://gohugo.io/extras/menus/)