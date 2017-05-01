+++
draft = false
title = "button"
description = "s"

[menu.main]
parent = "shortcodes"
identifier = "button"
+++

Affiche un bouton actionnable dans votre page.

{{<button align="center" href="#" theme="warning" >}} Ceci est un bouton d'avertissement {{< /button >}}

## Usage 

| Paramètre | Par défaut | Description |
|:--|:--|:--|
| href | "" | The location href to link to |
| align | "center" | horizontal align button on page |
| theme | `primary` | `default`, `primary` , `success`,`info`,`warning`,`danger` |

Le texte que vous placez à l'intérieur en short code sera affiché comme le _texte du bouton_

## Démo

	{{</* button href="https://google.com" */>}} aller sur google {{</* /button */>}}
	{{</* button href="https://google.com" theme="success" */>}} Succès {{</* /button */>}}
	{{</* button href="https://google.com" theme="info" */>}} Info {{</* /button */>}}
	{{</* button href="https://google.com" theme="warning" */>}} Attention {{</* /button */>}}
	{{</* button href="https://google.com" theme="danger" */>}} Danger ! {{</* /button */>}}
	{{</* button href="https://google.com" theme="default" */>}} Danger ! {{</* /button */>}}
    
{{<button href="https://google.com" >}} go to google {{< /button >}}
{{<button href="https://google.com" theme="success">}} Success {{< /button >}}
{{<button href="https://google.com" theme="info">}} Info {{< /button >}}
{{<button href="https://google.com" theme="warning">}} Warning {{< /button >}}
{{<button href="https://google.com" theme="danger">}} Danger ! {{< /button >}}
{{<button href="https://google.com" theme="default">}} Danger ! {{< /button >}}



