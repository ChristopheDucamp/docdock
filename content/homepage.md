+++
draft = false
title = "Page d'Accueil"
description = ""
date = "2017-05-01T12:33:24+02:00"
creatordisplayname = "xtof"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"
tags = ["tag1","tag2"]

[menu.main]
parent = "page"
identifier = "home"
weight = 1

+++

Pour dire à Hugo-theme-docdock de considérer une page comme du contenu pour la page d'accueil, créez simplement un fichier appelé `_index.md` dans le répertoire du contenu.

{{%panel theme="danger" header="**Considération pour la Page d'Accueil**"%}}Ne pas régler [menu.main] dans le frontmatter de votre fichier _index.md{{%/panel%}}
