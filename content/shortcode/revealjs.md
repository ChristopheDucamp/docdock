+++
draft = false
title = "revealjs"
slug = "revealjs"
description = "présente le contenu sous forme d'une slide reveal.js"

[menu.main]
parent = "shortcodes"
identifier = "revealjs"
weight = 1
+++

Ce raccourci code met en forme le markdown embarqué pour le restituer avec [reveal.js](http://lab.hakim.se/reveal-js/) en  runtime (côté-client)

Lisez en plus à ce sujet sur le [dépôt github revealjs](https://github.com/hakimel/reveal.js/#markdown).

## Usage

`revealjs` peut utiliser les paramètres nommés suivants : 

* theme
* transition
* controls
* progress
* history
* center


{{%warning title="Important" %}}Même si le contenu entouré est du markdown, utilisez la notation shortcode `<` au lieu de la notation `%` {{%/warning %}}

### Mise en page du contenu et délimiteur de slides

[en savoir plus ici]({{% relref "page-slide.md"%}})

## Démo

{{<revealjs theme="moon" progress="true">}}

# Le matin

___


## Se lever

- Éteindre le réveil
- Sortir du lit

___

## Breakfast

- Manger deux oeufs
- Boire du café

---

# Soirée

___

## Dîner

- Manger un spaghetti
- Boire du vin

___

## Aller dormir

- Aller au lit
- Compter les moutons

{{</revealjs>}}

## Source :

* [{{%icon "sunglasses" %}} cliquez ici pour voir le contenu brut](https://github.com/vjeantet/hugo-docdock-doc/blob/master/content/shortcode/revealjs.md)


