+++
draft = false
title = "Configuration Rapide Hugo"
description = ""

[menu.main]
parent = "start"
identifier = "quickstart hugo"
weight = 2

+++

## Pré-requis

  * Golang installé
  * GOPATH configuré

## Installation
    
    go get -v github.com/spf13/hugo
    
Une fois le `get` terminé, vous devriez trouver l'exécutable  `hugo` à l'intérieur de `$GOPATH/bin/`. Pour mettre à jour les dépendances d'Hugo, utilisez `go get` avec l'option `-u`.
    
    go get -u -v github.com/spf13/hugo
    

## Créer votre Site

Naviguez vers un endroit adéquat sur votre système de fichier et créez un nouveau site Hugo `monsite` en exécutant la commande suivante.
    
    hugo new site monsite
    

## Structure Créée

  * **archetypes** : Vous pouvez créer de novueaux fichiers de contenus dans Hugo en utilisant la commande `hugo new`. Quand vous lancez cette commande, cela ajoute quelques propriétés de configuration au post comme la date et le title. [Archetype](https://gohugo.io/content/archetypes/) vous permet de définir vos propres propriétés de configuration qui seront ajoutées au front matter du post à chaque fois qu'une commande `hugo new` est utilisée.
  * **config.toml** : Chaque site web devrait avoir un fichier de configuration à la racine. Par défaut, le fichier de configuration utilise le format `TOML` mais vous pouvez aussi utiliser aussi bien les formats `YAML` ou `JSON`. [TOML](https://github.com/toml-lang/toml) est le fichier minimal de configuration qui soit facile à lire du fait d'une sémantique évidente. Les réglages de configuration mentionnés dans le fichier `config.toml` sont appliqués sur l'ensemble du site. Ces réglages de configuration comprennent `baseURL` et `title` du site web.
  * **content** : C'est là où vous stockerez le contenu du site web. Dans le contenu, vous créerez des sous-répertoires pour différentes sections. Supposons que votre site web ait trois sections – `blog`, `article` et `tutorial` alors vous aurez trois répertoires différents pour chacun d'eux à l'intérieur du répertoire `content`. Le nom de la section par ex. `blog`, `article`, ou `tutorial` sera utilisé par Hugo pour appliquer un layout spécifique applicable à cette section.
  * **data** : Ce répertoire est utilisé pour stocker les fichiers de configuration qui peuvent être utilisés par Hugo au moment de générer votre site web. Vous pouvez écrire ces fichiers en format YAML, JSON, ou  TOML.
  * **layouts** : Le contenu à l'intérieur de ce répertoire est utilisé pour spécifier comment votre contenu sera converti à l'intérieur du site web statique.
  * **static** : Ce répertoire est utilisé pour stocker tout le contenu statique dont aura besoin votre site web comme images, CSS, JavaScript ou tout autre contenu statique.
  * **themes** : C'est là où vous créerez un thème pour votre site à utiliser. Les thèmes fournissent le layout et les templates qui restituent le contenu. Il existe une large varité de thèmes open source à télécharger et utiliser mais vous pouvez aussi créer le vôtre si vous préférez.
  
## Installer un Thème
    
    cd themes
    git clone https://github.com/yoshiharuyamashita/blackburn.git
    

## Configurer le Site

Copiez le fichier config.toml à partir du template exampleSite Blackburn vers la racine du site Hugo.
    
    baseurl = "http://www.willowbot.com/"
    languageCode = "en-us"
    title = "WillowBot Sandbox"
    theme = "blackburn"
    author = "WillowBot Team"
    copyright = "&copy; 2017. All rights reserved."
    canonifyurls = false
    paginate = 10
    
    [indexes]
      tag = "tags"
      topic = "topics"
    
    [params]
      # Shown in the home page
      subtitle = "a more formal napkin"
      brand = "WillowBot"
      googleAnalytics = "UA-11111111-1"
      disqus = ""
      # CSS name for highlight.js
      highlightjs = "androidstudio"
      dateFormat = "Jan 02, 2006, 15:04"
      
    [permalinks]
      post = "/:slug/"
    
    [menu]
      # Shown in the side menu.
      [[menu.main]]
        name = "Home"
        pre = "<i class='fa fa-home fa-fw'></i>"
        weight = 0
        identifier = "home"
        url = "/"
      [[menu.main]]
        name = "Projects"
        pre = "<i class='fa fa-rocket fa-fw'></i>"
        weight = 1
        identifier = "projects"
        url = "/projects/"
      [[menu.main]]
        name = "Posts"
        pre = "<i class='fa fa-database fa-fw'></i>"
        weight = 1
        identifier = "post"
        url = "/post/"
      [[menu.main]]
        name = "Quotes"
        pre = "<i class='fa fa-quote-left fa-fw'></i>"
        weight = 1
        identifier = "quotes"
        url = "/quotes/"
      [[menu.main]]
        name = "About"
        pre = "<i class='fa fa-user fa-fw'></i>"
        weight = 2
        identifier = "about"
        url = "/about/"
    

Copiez le fichier default.md à partir de blackburn/archetypes vers le répertoire archetypes à la racine d'hugo.
    
    +++
    title = ""
    slug = ""
    draft = true
    tags = []
    topics = []
    description = ""
    
    +++
    

## Créer le Contenu

À partir du répertoire racine du site, exécutez
    
    hugo new post/2017/0412-hello-world.md
    

Ceci créera un nouveau fichier prêt pour le contenu. Réglez les détails du frontmatter comme convenu.

    +++
    date = "2017-04-12T14:03:36-04:00"
    description = ""
    draft = true
    slug = "hello-world"
    tags = []
    title = "Hello World"
    topics = []
    
    +++
    

Les nouveaux posts par défaut sont réglés sur des brouillons (draft). Pour faire que votre ébauche soit publique, soit vous lancez la commande ci-dessous ou vous modifiez manuellement le statut draft dans le post en  `false`.
    
    hugo undraft content/post/2017/0412-hello-world.md
    

Écrivez l'article en utilisant [markdown](https://en.support.wordpress.com/markdown-quick-reference/)…

## Vérifier le Contenu

Exécutez la ligne du dessous pour démarrer le serveur local qui sert le site. Remarquez que la commande doit être exécutée à partir du répertoire où existe la racine du site.
    
    hugo server --theme=blackburn --buildDrafts
    

Pour visualiser le site, naviguez sur [http://localhost:1313/.](http://localhost:1313/) Le serveur hugo supporte le rafraîchissement live, par conséquent les modifications faites sur les posts, le fichier config, etc. sont automatiquement renvoyées sur les pages web servies.

## Genérer le Site Web

Pour finir et générer les pages web statiques, lancez la commande ci-dessous.
    
    hugo --theme=blackburn
    

Après avoir lancé la commande `hugo`, un répertoire `/public` est créé contenant tous les fichiers sources du site web généré  all prêts à être téléversés “online”. Le site est hébergé sur [Google Cloud Storage](https://cloud.google.com/). Les détails sur la façon de faire suivront.

[__](http://www.willowbot.com/hello-world)

  

