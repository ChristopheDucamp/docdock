+++
draft = false
title = "Déploiements Automatisés avec Wercker"
description = ""

[menu.main]
parent = ""
identifier = "deploiement"
weight = 45


creatordisplayname = "xtof"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"

+++

{{%warning title="Attention"%}}Rédaction et traduction en cours et images manquantes.{{% /warning %}}
Dans ce tutoriel nous réglerons un projet basique Hugo, et nous le configurerons ensuite avec un outil gratuit appelé Wercker pour déployer automatiquement le site généré à chaque fois que nous y ajoutons un article. Nous le déploierons sur GitHub pages car c'est le moyen le plus facile pour paramétrer, mais vous verrez que vous pouvez utiliser tout ce que vous voudrez. Ce tutoriel vous emmène sur chaque étape du processus, complété d'impressions écrans et il est plutôt long.

Les hypothèses pour ce tutoriel sont que vous savez utiliser git pour le contrôle de version et que vous disposez d'un compte chez GitHub. Si vous n'êtes pas à l'aise avec ça, regardez la [section help](https://help.github.com/articles/set-up-git/) GitHub qui a une explication sur la façon d'installer et utiliser git. Et vous pouvez aussi facilement vous créer un compte chez GitHub.

## Créer un site basique Hugo

Il existe déjà des [pages](http://gohugo.io/overview/quickstart/) dédiées pour décrire comment installer un site Hugo, par conséquent nous étudierons les étapes les plus basiques requises pour faire tourner un site et le lancer avant de plonger dans la configuration de Wercker. Tout le travail pour installer le projet est fait en utilisant la ligne de commande, et maintenu aussi simple que possible.

Créez le nouveau site en utilisant la commande `hugo new site` et nous nous déplacerons à l'intérieur.

```bash
hugo new site exemple-hugo-wercker
cd exemple-hugo-wercker
```

Ajoutez le thème herring-cove en le clonant à l'intérieur du répertoire `themes` en utilisant les commandes suivantes.

```bash
cd themes
git clone https://github.com/spf13/herring-cove.git
```

Cloner ainsi le projet provoquera un conflit avec notre propre contrôle de version, par conséquent nous retirerons la configuration externe git.

```bash
rm -rf herring-cove/.git
```

Ajoutons une page rapide **about**.

```bash
hugo new about.md
```

Maintenant, nous modifierons contents/about.md pour nous assurer que ce n'est plus un draft (ébauche) et y ajouterons un peu de texte.

```bash
hugo undraft content/about.md
```

Une fois terminé, c'est toujours une bonne idée de faire une vérification rapide pour voir si tout fonctionne en le lançant

```bash
hugo server --theme=herring-cove
```

Si tout fonctionne, vous devriez pouvoir voir quelque chose d'équivalent à l'image en-dessous si vous tapez  `localhost:1313` dans la barre d'URL de votre navigateur.

{{%warning title="Attention"%}}Ajouter image site.{{% /warning %}}

![][1]

[1]: /img/creer-site-basique-hugo.png

## Paramétrer le contrôle de version

Ajouter git à notre projet se fait en lançant la commande `git init` à partir du répertoire racine du projet.

```bash
git init
```

Lancer `git status` à ce stade vous présentera vos entrées : le fichier **config.toml**, le répertoire  **themes**, le répertoire **contents**, et le répertoire **public**. Nous ne voulons pas que le répertoire **public** soit sous contrôle de version, car nous utiliserons wercker pour générer cela plus tard. Par conséquent, nous ajoutons un fichier `gitignore` qui exclura ça en utilisant la commande qui suit

```bash
echo "/public" >> .gitignore
```

Comme nous n'avons pas encore de fichiers statiques en dehors du répertoire themes, , Wercker pourrait se plaindre quand nous essaierons de construire le site plus tard. 
Pour éviter cela, nous devons simplement ajouter n'importe quel fichier au répertoire statique. Pour rester simple à ce stade, nous ajouterons un fichier `robots.txt` qui donnera un plein accès au site à tous les moteurs de recherche quand il sera construit.

```bash
echo "User-agent: *\nDisallow:" > static/robots.txt
```

Après ça, nous pouvons ajouter tout au repo.

```bash
git commit -a -m "Initial commit"
```

## Ajouter le projet à GitHub

Premièrement, nous créerons un nouveau dépôt. Vous pouvez faire ça en cliquant sur le signe **+** tout en haut et à droite, ou en allant sur https://github.com/new

Nous choisissons ensuite un nom pour le projet (**exemple-hugo-wercker**). Au moment de cliquer sur "create repository", GitHub affiche les commandes pour ajouter un projet existant au site. Les commandes sont celles utilisées pour ce site, si vous suivez vous devrez utiliser celles indiquées par GitHub. Une fois que nous aurons exécuté ces commandes, le projet se trouve dans GitHub et nous pouvons passer à la configuration de Wercker.

```bash
git remote add origin git@github.com:VotreNomUtilisateurGitHub/exemple-hugo-wercker.git
git push -u origin master
```

![][2]

[2]: /img/tutorials/automated-deployments/adding-the-project-to-github.png

## Bienvenue sur wercker

Commençons par créer un compte sur Wercker. Pour faire ceci, nous allons sur http://wercker.com et cliquons sur le bouton **Sign up**.

![][3]

[3]: /img/tutorials/automated-deployments/wercker-sign-up.png

## Enregistrement

Pour nous simplifier la vie, nous nous enregistrons en utilisant GitHub. Si vous n'avez pas de compte GitHub, ou si vous ne voulez pas l'utiliser pour votre compte, vous pouvez bien sûr vous enregistrer tout aussi bien avec un nom d'utilisateur et un mot de passe.

![][4]

[4]: /img/tutorials/automated-deployments/wercker-sign-up-page.png

## Connexion GitHub/Bitbucket

Après vous être enregistré.e, vous devrez lier votre compte  GitHub et/ou Bitbucket à Wercker. Vous faites ça en allant sur vos réglages de profil, et ensuite "Git connections". Si vous vous êtes enregistré.e en utilisant GitHub, cela ressemblera à l'image du dessous. Pour connecter un service manquant, cliquez simplement sur le bouton connect qui vous enverra ensuite soit sur GitHub ou Bitbucket où vous pourriez avoir besoin de vous connecter et d'approuver l'accès vers votre compte.

![][5]

[5]: /img/tutorials/automated-deployments/wercker-git-connections.png

## Ajouter votre projet

Now that we've got all the preliminaries out of the way, it's time to set up our application. For this we click on the **+ Create** button next to Applications. Create a new application, and choose to use GitHub.

![][6]

[6]: /img/tutorials/automated-deployments/wercker-add-app.png

## Select a repository

Clicking this will make Wercker show you all the repositories you have on GitHub, but you can easily filter them as well. So we search for our repository, select it, and then click on "Use selected repo".

![][7]

[7]: /img/tutorials/automated-deployments/wercker-select-repository.png

## Configurer l'accès

As Wercker doesn't access to check out your private projects by default, it will ask you what you want to do. When your project is public, as needs to be the case if you wish to use GitHub Pages, the top choice is recommended. When you use this it will simply check out the code in the same way anybody visiting the project on GitHub can do.

![][8]

[8]: /img/tutorials/automated-deployments/wercker-access.png

## Public or not

This is a personal choice; you can make an app public so that everyone can see more details about it. This doesn't give you any real benefits either way in general, although as part of the tutorial I have of course made this app public so you can see it in action [yourself](https://app.wercker.com/#applications/5586dcbdaf7de9c51b02b0d5).

![][9]

[9]: /img/tutorials/automated-deployments/public-or-not.png

## Wercker.yml

Choose Default for your programming language. Wercker will now attempt to create an initial *wercker.yml* file for you. Or rather, it will create the code you can copy into it yourself. Because there is nothing special about our project according to Wercker, we will simply get the `debian` box. So what we do now is create a *wercker.yml* file in the local root of our project that contains the provided configuration, and after we finish setting up the app we will expand this file to make it actually do something.

![][10]

[10]: /img/tutorials/automated-deployments/werckeryml.png

## And we've got an app

The application is added now, and Wercker will be offering you the chance to trigger a build. As we haven't pushed up the **wercker.yml** file however, we will politely decline this option. Wercker has automatically added a build pipeline to your application.

## Adding build step

And now we're going to add the build step to the build pipeline. First, we go to the "Registry" action in the top menu and then search for "hugo build". Find the **Hugo-Build** task by Arjen and select it.

![][11]

[11]: /img/tutorials/automated-deployments/wercker-search.png

## Using Hugo-Build

Inside the details of this step you will see how to use it. At the top is a summary for very basic usage, but when scrolling down you go through the README of the step which will usually contain more details about the advanced options available and a full example of using the step.

We're not going to use any of the advanced features in this tutorial, so we'll return to our project and add the details we need to our wercker.yml file so that it looks like below: 

```yaml
box: debian
build:
  steps:
    - install-packages:
        packages: git
    - script:
        name: download theme
        code: |
            $(git clone https://github.com/spf13/herring-cove ./themes/herring-cove)
    - arjen/hugo-build:
        version: "0.14"
        theme: herring-cove
        flags: --buildDrafts=true
```

As you can see, we have two steps in the build pipeline. The first step downloads the theme, and the second step runs arjen's hugo-build step. To use a different theme, you can replace the link to the herring-cove source with another theme's repository - just make sure the name of the folder you download the theme to (./themes/your-theme-name) matches the theme name you tell arjen/hugo-build to use (theme: your-theme-name). Now we'll test that it all works as it should by pushing up our wercker.yml file to GitHub and seeing the magic at work.

```bash
git commit -a -m "Add wercker.yml"
git push origin master
```

Once completed a nice tick should have appeared in front of your first build, and if you want you can look at the details by clicking on it. However, we're not done yet as we still need to deploy it to GitHub Pages.

![][12]

[12]: /img/tutorials/automated-deployments/using-hugo-build.png

## Adding a deploy pipeline

In order to deploy to GitHub Pages we need to add a deploy pipeline. 

1. First, go to your Wercker application's page. Go to the "Workflows" tab and click on "Add new pipeline." Name it whatever you want; "deploy-production" or "deploy" works fine. For your YML Pipeline name, type in "deploy" without quotes. Leave the hook type as "Default" and hit the Create button. 

2. Now you need to link the deploy pipeline to your build pipeline. In the workflow editor, click on the + next to your build pipeline and add the deploy pipeline you've just made. Now the deploy pipeline will be run automatically whenever the build pipeline is completed successfully.

![][13]

[13]: /img/tutorials/automated-deployments/adding-a-deploy-pipeline.png

## Adding a deploy step

Next, we need to add a step to our deploy pipeline that will deploy the Hugo-built website to your GitHub pages repository. Once again searching through the Steps registry, we find that the most popular step is the **lukevevier/gh-pages** step so we add the configuration for that to our wercker.yml file. Additionally, we need to ensure that the box we run on has git and ssh installed. We can do this using the **install-packages** command, which then turns the wercker.yml file into this:

```yaml
box: debian
build:
  steps:
    - arjen/hugo-build:
        version: "0.14"
        theme: herring-cove
        flags: --buildDrafts=true
deploy:
  steps:
    - install-packages:
        packages: git ssh-client
    - lukevivier/gh-pages@0.2.1:
        token: $GIT_TOKEN
        domain: hugo-wercker.ig.nore.me
        basedir: public
```

How does the GitHub Pages configuration work? We've selected a couple of things, first the domain we want to use for the site. Configuring this here will ensure that GitHub Pages is aware of the domain you want to use.

Secondly we've configured the basedir to **public**, this is the directory that will be used as the website on GitHub Pages.

And lastly, you can see here that this has a **$GIT_TOKEN** variable. This is used for pushing our changes up to GitHub and we will need to configure this before we can do that. To do this, go to your application page and click on the "Environment" tab. Under Application Environment Variables, put **$GIT_TOKEN** for the Key. Now you'll need to create an access token in GitHub. How to do that is described on a [GitHub help page](https://help.github.com/articles/creating-an-access-token-for-command-line-use/). Copy and paste the access token you generated from GitHub into the Value box. **Make sure you check Protected** and then hit Add. 

![][14]

[14]: /img/tutorials/automated-deployments/adding-a-deploy-step.png

With the deploy step configured in Wercker, we can push the updated wercker.yml file to GitHub and it will create the GitHub pages site for us. The example site we used here is accessible under hugo-wercker.ig.nore.me

## Conclusion

From now on, any time you want to put a new post on your blog all you need to do is push your new page to GitHub and the rest will happen automatically. The source code for the example site used here is available on [GitHub](https://github.com/ArjenSchwarz/hugo-wercker-example), as is the [Hugo Build step](https://github.com/ArjenSchwarz/wercker-step-hugo-build) itself.

If you want to see an example of how you can deploy to S3 instead of GitHub pages, take a look at [Wercker's documentation](http://devcenter.wercker.com/docs/deploy/s3.html) about how to set that up.
