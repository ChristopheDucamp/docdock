+++
draft = false
title = "Configuration"
description = ""

[menu.main]
parent = "start"
identifier = "configuration"
weight = 2

+++

Au moment de créer le site web, vous pouvez paramétrer un thème en utilisant l'option `--theme`. Nous vous suggérons de modifier votre fichier de configuration et de paramétrer le thème par défaut. Exemple avec le format `config.toml`.

```
theme = "docdock"
```

## Génération d'un Index de Recherche

Ajoutez la ligne suivante dans le même fichier de configuration.

```
[outputs]
home = [ "HTML", "RSS", "JSON"]
```

Le fichier d'index de recherche LUNRJS sera généré sur les modifications de contenus.

## Votre contenu de site web

Regardez comment [créer]({{%relref "page.md"%}}) et [organiser votre contenu]({{%relref "organisation.md"%}}) rapidement et intuitivement.