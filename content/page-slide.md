+++
draft = false
title = "Présenter une Slide"
description = ""
date = "2017-05-01T12:32:24+02:00"

creatordisplayname = "xtof"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"

[menu.main]
parent = "page"
identifier = "page-slide"
weight = 21

+++

Une page basique de contenu md peut être restituée comme une présentation plein écran reveal.js.

{{%alert info%}}Vous pouvez aussi, **embarquer une présentation dans une page** sous forme de petite boîte, en utilisant le shortcode [revealjs]({{% relref "shortcode/revealjs.md"%}}) dans votre fichier md.{{%/alert%}}


## Mise en Page
Utilisez votre syntaxe commune Markdown que vous utilisez dans Hugo, n'oubliez pas que vous pouvez aussi placer des balises HTML.

{{%notice info%}}La syntaxe spéciale (en commentaire html) est disponible pour ajouter des attribut aux éléments Markdown. Ceci est utile entre autre pour les fragments.{{%/notice%}}

Lisez SVP la [{{%icon book%}} doc d'hakimel](https://github.com/hakimel/reveal.js/#instructions)


## Options
Dans le frontmatter de votre fichier page, réglez les paramètres **type** et **revealOptions**.

Votre contenu sera servi sous forme de présentation plein écran et revealOptions sera utilisé pour ajuster son comportement.

	+++
	title = "Dia Test"
	type="slide"

	theme = "league"
	[revealOptions]
	transition= 'concave'
	controls= true
	progress= true
	history= true
	center= true
	+++

[Lisez plus ici sur les options reveal](https://github.com/hakimel/reveal.js/#configuration)


## Délimiteurs de Slide
Au moment de créer le contenu de votre diaporama pour votre présentation dans le fichier de contenu markdown, vous devez pouvoir distinguer entre une dia et la suivante. Ceci peut être réaliser simplement en utilisant une convention dans le Markdown qui indique le démarrage de chaque nouvelle slide.

Le fait que les slides horizontales et verticales soient supportées par reveal.js, chacune d'entre elles a son propre et unique délimiteur.

Pour indiquer le démarrage d'une slide horizontale, ajoutez simplement le délimiteur suivant dans votre Markdown :

	---


Pour indiquer le démarrage d'une slide verticale, ajoutez simplement le délimiteur suivant dans votre Markdown :
	
	___

En utilisant une combinaison de slides horizontales et verticales, vous pouvez personnaliser la navigation dans votre présentation du diaporama. Généralement, les slides verticales sont utilisées pour présenter l'information sous une slide horizontale du niveau le plus haut.

Par exemple, une présentation de diaporama simple peut être créée comme suit : 

```
+++
draft = false
title = "test"
date = "2017-04-24T18:36:24+02:00"
type="slide"

theme = "league"
[revealOptions]
transition= 'concave'
controls= true
progress= true
history= true
center= true
+++

# Le matin 

___

## Se lever

- Éteindre le réveil
- Sortir du lit

___

## Petit déjeuner

- Manger des oeufs
- Boire du café

---

# Dans la soirée

___

## Dîner

- Manger des courgettes
- Boire du vin

___

## Aller dormir

- Aller au lit
- Compter les moutons

```

[{{%icon expand%}}Cliquez ici pour visualiser le rendu de cette page]({{%relref "myslide.md"%}})