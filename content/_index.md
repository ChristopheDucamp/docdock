+++
draft = false
title = "Accueil"
description = ""
date = "2017-05-01T20:34:24+02:00"


creatordisplayname = "Christophe Ducamp"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"

+++

<span id="sidebar-toggle-span">
<a href="#" id="sidebar-toggle" data-sidebar-toggle=""><i class="fa fa-bars"></i></a>
</span>

<div id="top-github-link">
  <a class="github-link" href="https://github.com/ChristopheDucamp/docdock/edit/master/content/_index.md" target="blank">
    <i class="fa fa-code-fork"></i> Modifiez cette page</a>
</div>

# Documentation Thème Hugo docDock
[Hugo-theme-docdock {{%icon fa-github%}}](https://github.com/vjeantet/hugo-theme-docdock) est un thème pour Hugo, un moteur de site web rapide et moderne écrit en Go. Là où Hugo est souvent utilisé pour les blogs, ce thème est complètement conçu pour la documentation.

Ce thème est une adaptation partielle du [thème Learn de matcornic {{%icon fa-github%}}](https://github.com/matcornic/hugo-theme-learn), un CMS moderne écrit en PHP.

Cette démo actuelle a été générée statiquement avec Hugo en une simple commande : `hugo -t docdock` -- Le code source est [disponible ici sur GitHub {{%icon fa-github%}}](https://github.com/vjeantet/hugo-theme-docDock-doc)



{{% panel theme="success" header="Déploiements automatiques" footer="Netlify construit, déploie et héberge les frontends." %}}
La documentation actuelle est automatiquement publié grâce à [Netlify](https://www.netlify.com/).
Pour en savoir plus, lisez [Automated deployments with Wercker on gohugo.io](https://gohugo.io/tutorials/automated-deployments/)
{{% /panel %}}

## Le thème Dodock
Ce thème supporte une structure d'arborescence de page pour afficher et organiser les pages.

{{%panel%}}**organisation du contenu** : Tous les contenus sont des pages qui appartiennent à d'autres pages. [Lire plus à ce sujet]({{%relref "organisation.md"%}}) {{%/panel%}}

## Fonctionnalités
Voici les principales fonctionnalités :

* [Chercher]({{%relref "search.md" %}})
* Gérer 5 niveaux de documentation
* [Générer une présentation RevealJS]({{%relref "page-slide.md"%}}) à partir de markdown (embarquée ou page plein écran)
* [Fichiers Attachés]({{%relref "shortcode/attachments.md" %}})
* [Lister les pages enfants]({{%relref "shortcode/children.md" %}})
* [Extraction]({{%relref "shortcode/excerpt.md"%}}) ! Inclure un segment de contenu provenant d'une page dans une autre
* Boutons automatiques suivant/précédent pour naviguer dans les entrées de menu
* [Icônes]({{%relref "shortcode/icon.md" %}}), [Boutons]({{%relref "shortcode/button.md" %}}), [Alertes]({{%relref "shortcode/alert.md" %}}), [Panels]({{%relref "shortcode/panel.md" %}}), [Truc/Note/Info/Boîtes Alertes]({{%relref "shortcode/notice.md" %}})
* [Retaillage d'Image, ombres...]({{%relref "shortcode/image.md" %}})
* Tags

![](https://raw.githubusercontent.com/vjeantet/hugo-theme-docdock/master/images/tn.png?width=33pc&classes=border,shadow)

## Contribuez à cette documentation
Sentez-vous libre de mettre à jour ce contenu, envoyez simplement un "Modifier une page" et un pullrequest, votre modification sera déployée automatiquement une fois fusionnée.

Utilisez le lien "Modifiez cette page" que vous trouverez en haut et à droite de chaque page.