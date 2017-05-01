+++
draft = false
title = "excerpt"
description = ""

[menu.main]
parent = "shortcodes"
identifier = "excerpt"
+++

Le code raccourci Excerpt est utilisé pour marquer une page de contenu d'une page pour ré-utilisation. Définir un excerpt permet d'autres shortcodes, comme le shortcode excerpt-include shortcode, pour affichier le contenu marqué ailleurs.

{{%alert warning%}}Vous ne pouvez définir seulement qu'un excerpt par page. En d'autres mots, vous ne pouvez seulement ajouter le shortcode Excerpt qu'une fois par page.{{%/alert%}}


## Usage

| Paramètre | Par défaut | Description |
|:--|:--|:--|
| hidden | "false" | Contrôle si le contenu de la page contenu dans l'emplacement du shortcode Excerpt est affiché sur la page.{{%alert warning%}}Notez que cette option n'affecte que la page qui contient le shortcode Excerpt. Cela n'affecte pas les pages où le contenu est réutilisé.{{%/alert%}} |

## Démo

	{{%/*excerpt*/%}}
	Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
	tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
	quis nostrud exercitation **ullamco** laboris nisi ut aliquip ex ea commodo
	consequat. Duis aute irure dolor in _reprehenderit in voluptate_
	cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
	proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
	{{%/* /excerpt*/%}}

{{%excerpt%}}
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation **ullamco** laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in _reprehenderit in voluptate_
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
{{% /excerpt%}}



{{%alert info%}}Voir l'exemple de ré-utilisation avec [excerpt-include shortcode]({{%relref "shortcode/excerpt-include.md"%}}){{%/alert%}}