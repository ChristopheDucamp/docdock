+++
draft = false
title = "panel"
description = ""

[menu.main]
parent = "shortcodes"
identifier = "panel"
+++



{{% panel theme="success" header="Le raccourci panel" %}}Vous permet de mettre en valeur l'information ou la placer dans une boîte. Cela crée une boîte colorée entourant votre texte{{% /panel %}}


## Usage 

| Paramètre | par défaut | Description |
|:--|:--|:--|
| header | none | Le titre du panel. Si spécifié, ce titre sera affiché dans sa propre ligne de titre. |
| footer | none | le pied de page du panel. Si spécifié, ce texte sera affiché dans sa propre ligne. |
| theme | `primary` | `default`,`primary`,`info`,`success`,`warning`,`danger` |

## Exemple basique : 

Par défaut :

	{{%/* panel */%}}ceci est un texte panel{{%/* /panel */%}}

{{%panel%}}ceci est un texte panel{{%/panel%}}

## Panel avec titre

Ajoutez facilement un conteneur de titre à votre panel avec le paramètre `header`. Vous pouvez appliquer n'importe quel thème.

	{{%/* panel theme="danger" header="titre panel" */%}}ceci est un texte panel{{%/* /panel */%}}

{{%/* panel theme="danger" header="titre panel" */%}}ceci est un texte panel{{%/* /panel */%}}

	{{%/* panel theme="success" header="titre panel" */%}}ceci est un texte panel{{%/* /panel */%}}

{{% panel theme="success" header="titre panel" %}}ceci est un texte panel{{% /panel %}}

## Panel avec footer
Emballe un texte secondaire dans le footer.

	{{%/* panel footer="panel footer" */%}}Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.{{%/* /panel */%}}

{{% panel footer="pied de panel" %}}
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
{{% /panel %}}

## Thèmes

{{% panel theme="success" header="thème Success" %}}ceci est un texte panel{{% /panel %}}
{{% panel theme="default" header="thème default" %}}ceci est un texte panel{{% /panel %}}
{{% panel theme="info" header="thème info" %}}ceci est un texte panel{{% /panel %}}
{{% panel theme="warning" header="thème warning" %}}ceci est un texte panel{{% /panel %}}
{{% panel theme="danger" header="thème danger" %}}ceci est un texte panel{{% /panel %}}
