+++
draft = false
title = "notice"
description = ""

[menu.main]
parent = "shortcodes"
identifier = "notice"
+++

Le raccourci notice montre 4 types d'avertissement pour vous aider à structurer votre page.


## Note

	{{%/* notice note */%}}
	Un avertissement
	{{%/* /notice */%}}

donne

{{% notice note %}}
Un avertissement
{{% /notice %}}


## Info

	{{%/* notice info */%}}
	Un avertissement d'information
	{{%/* /notice */%}}

donne

{{% notice info %}}
Un avertissement d'information
{{% /notice %}}



## Tip

	{{%/* notice tip */%}}
	Un avertissement pour un truc
	{{%/* /notice */%}}

renders as

{{% notice tip %}}
Un avertissement pour un truc
{{% /notice %}}



## Warning

	{{%/* notice warning */%}}
	Un avertissement / warning
	{{%/* /notice */%}}

donne

{{% notice warning %}}
Un avertissement / warning
{{% /notice %}}

