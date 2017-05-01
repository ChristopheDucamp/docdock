+++
draft = false
title = "alert"
description = ""
[menu.main]
parent = "shortcodes"
identifier = "alert"
+++

Le shortcode `alert` vous permet de mettre en valeur l'information dans votre page. Il crée une boîte colorée entourant votre texte, comme ceci :

{{%alert%}}**Ceci est** une alerte !{{%/alert%}}
## Usage 

| Paramètre | Par défaut | Description |
|:--|:--|:--|
| theme | `info` | `success`, `info`,`warning`,`danger` |

{{%alert info%}}
**Trucs :** régler seulement le thème comme argument fonctionne aussi : 
`{{%/*alert warning*/%}}`  au lieu de `{{%/*alert theme="warning"*/%}}`
{{%/alert%}}

## Exemples basiques

	{{%/* alert theme="info" */%}}**ceci** est un texte {{%/* /alert */%}}
	{{%/* alert theme="success" */%}}**Yeahhh !** est un texte{{%/* /alert */%}}
	{{%/* alert theme="warning" */%}}**Soyez prudent** est un  texte{{%/* /alert */%}}
	{{%/* alert theme="danger" */%}}**Attention !** est un texte{{%/* /alert */%}}

{{% alert theme="info"%}}**ceci** est une info{{% /alert %}}
{{% alert theme="success" %}}**Yeahhh !** est un success{{% /alert %}}
{{% alert theme="warning" %}}**Be carefull** est un warning{{% /alert %}}
{{% alert theme="danger" %}}**Attention !** est un danger{{% /alert %}}