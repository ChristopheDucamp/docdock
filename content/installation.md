+++
draft = false
title = "Installation"
description = ""

[menu.main]
parent = "start"
identifier = "installation"
weight = 1

+++



Les étapes qui suivent sont là pour vous aider à initialiser votre nouveau site web. Si vous ne connaissez pas du tout Hugo, nous vous suggérons de vous entraîner en suivant cette [documentation pour débutants](https://gohugo.io/overview/quickstart/).


## Créez votre Documentation

Hugo fournit une commande `new` pour créer un nouveau site web.

	$ hugo new site <nouveau_site_web>

## Installer le Thème

Installez le thème **Hugo-theme-docdock** en suivant ceci  

Déplacez-vous dans le répertoire thème et téléchargez le thème 

	$ cd themes
	$ git clone https://github.com/vjeantet/hugo-theme-docdock.git docdock

Alternativement, vous pouvez [{{%icon download%}} télécharger le thème sous fichier .zip](https://github.com/vjeantet/hugo-theme-docdock/archive/master.zip) et l'extraire dans le répertoire themes.

## Configuration Basique

[Suivez ici les instructions]({{%relref "configuration.md"%}})