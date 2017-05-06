+++
draft = false
title = "Héberger sur GitHub"
description = "Page voulue"
date = "2017-05-02T10:22:24+02:00"
tags = ["github", "git", "déploiement", "hébergement"]

creatordisplayname = "xtof"
creatoremail = "christophe@ducamp.me"
lastmodifierdisplayname = "Christophe Ducamp"
lastmodifieremail = "christophe@ducamp.me"

[menu.main]
parent = ""
identifier = "deploiement GitHub"
weight = 46


+++

{{%warning title="Attention"%}}Page voulue à traduire https://hugodocs.info/hosting-and-deployment/hosting-on-github/{{% /warning %}}


GitHub fournit un hébergement gratuit et rapide sur SSL pour les pages personnelles, d'organisation ou projet directement à partir d'un dépôt GitHub via son [service GitHub Pages](https://help.github.com/articles/what-is-github-pages/).

## Hypothèses

  1. You have Git 2.5 or greater [installed on your machine](https://git-scm.com/downloads).
  2. You have a GitHub account. [Signing up](https://github.com/join) for GitHub is free.
  3. You have a ready-to-publish Hugo website or have at least completed the [Quick Start](https://hugodocs.info/getting-started/quick-start/).

If you are working within an Organization account or want to set up a User website on GitHub and would like more information, refer to the [GitHub Pages documentation](https://help.github.com/articles/user-organization-and-project-pages/#user--organization-pages).

Make sure your `baseURL` key-value in your [site configuration](https://hugodocs.info/getting-started/configuration/) reflects the full URL of your GitHub pages repository if you’re using the default GH Pages URL (e.g., `username.github.io/myprojectname/`) and not a custom domain.

## Déploiement via répertoire `/docs` Folder sur la Branche Master

[As described in the GitHub Pages documentation](https://help.github.com/articles/configuring-a-publishing-source-for-github-pages/#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch), you can deploy from a folder called `docs/` on your master branch. To effectively use this feature with Hugo, you need to change the Hugo publish directory in your [site’s](https://hugodocs.info/getting-started/configuration/)`config.toml` and `config.yaml`, respectively:
    
    publishDir: docs
    
    
    publishDir = "docs"
    

Après avoir lancé `hugo`, poussez votre branche master vers le repo distant et choisissez le répertoire `docs/` comme le site web source de votre repo. Faites ce qui suit à partir de votre projet GitHub :

  1. Go to **Settings** → **GitHub Pages**
  2. From **Source**, select “master branch /docs folder”. If the option isn’t enabled, you likely do not have a `docs/` folder in the root of your project.

The `docs/` option is the simplest approach but requires you set a publish directory in your site configuration. You cannot currently configure GitHub pages to publish from another directory on master, and not everyone prefers the output site live concomitantly with source files in version control.

## Déploiement à Partir de votre Branche `gh-pages`

You can also tell GitHub pages to treat your `master` branch as the published site or point to a separate `gh-pages` branch. The latter approach is a bit more complex but has some advantages:

  * It keeps your source and generated website in different branches and therefore maintains version control history for both.
  * Unlike the preceding `docs/` option, it uses the default `public` folder.

### [__](https://hugodocs.info/hosting-and-deployment/hosting-on-github/#preparations-for-gh-pages-branch)Preparations for `gh-pages` Branch

These steps only need to be done once. Replace `upstream` with the name of your remote; e.g., `origin`:

#### Add the Public Folder

First, add the `public` folder to your `.gitignore` file at the project root so that the directory is ignored on the master branch:
    
    echo "public" >> .gitignore
    

#### Initialiser votre branche `gh-pages`

You can now initialize your `gh-pages` branch as an empty [orphan branch](https://git-scm.com/docs/git-checkout/#git-checkout---orphanltnewbranchgt):
    
    git checkout --orphan gh-pages
    git reset --hard
    git commit --allow-empty -m "Initializing gh-pages branch"
    git push upstream gh-pages
    git checkout master
    

### Construction et Déploiement

Now check out the `gh-pages` branch into your `public` folder using git’s [worktree feature](https://git-scm.com/docs/git-worktree). Essentially, the worktree allows you to have multiple branches of the same local repository to be checked out in different directories:
    
    rm -rf public
    git worktree add -B gh-pages public upstream/gh-pages
    

Regenerate the site using the `hugo` command and commit the generated files on the `gh-pages` branch:

commit-gh-pages-files.sh

__ COPY
    
    hugo
    cd public && git add --all && git commit -m "Publishing to gh-pages" && cd ..
    

If the changes in your local `gh-pages` branch look alright, push them to the remote repo:
    
    git push upstream gh-pages
    

#### Setting `gh-pages` as Your Publish Branch

In order to use your `gh-pages` branch as your publishing branch, you’ll need to configure the repository within the GitHub UI. This will likely happen automatically once GitHub realizes you’ve created this branch. You can also set the branch manually from within your GitHub project:

  1. Go to **Settings** → **GitHub Pages**
  2. From **Source**, select “gh-pages branch” and then **Save**. If the option isn’t enabled, you likely have not created the branch yet OR you have not pushed the branch from your local machine to the hosted repository on GitHub.

After a short while, you’ll see the updated contents on your GitHub Pages site.

### Putting it Into a Script

To automate these steps, you can create a script with the following contents:

publish_to_ghpages.sh

__ COPY
    
    #!/bin/sh
    
    DIR=$(dirname "$0")
    
    cd $DIR/..
    
    if [[ $(git status -s) ]]
    then
        echo "The working directory is dirty. Please commit any pending changes."
        exit 1;
    fi
    
    echo "Deleting old publication"
    rm -rf public
    mkdir public
    git worktree prune
    rm -rf .git/worktrees/public/
    
    echo "Checking out gh-pages branch into public"
    git worktree add -B gh-pages public upstream/gh-pages
    
    echo "Removing existing files"
    rm -rf public/*
    
    echo "Generating site"
    hugo
    
    echo "Updating gh-pages branch"
    cd public && git add --all && git commit -m "Publishing to gh-pages (publish.sh)"
    

This will abort if there are pending changes in the working directory and also makes sure that all previously existing output files are removed. Adjust the script to taste, e.g. to include the final push to the remote repository if you don’t need to take a look at the gh-pages branch before pushing. Or adding `echo yourdomainname.com >> CNAME` if you set up for your gh-pages to use customize domain.

## [__](https://hugodocs.info/hosting-and-deployment/hosting-on-github/#deployment-from-your-master-branch)Deployment From Your `master` Branch

To use `master` as your publishing branch, you’ll need your rendered website to live at the root of the GitHub repository. Steps should be similar to that of the `gh-pages` branch, with the exception that you will create your GitHub repository with the `public` directory as the root. Note that this does not provide the same benefits of the `gh-pages` branch in keeping your source and output in separate, but version controlled, branches within the same repo.

You will also need to set `master` as your publishable branch from within the GitHub UI:

  1. Go to **Settings** → **GitHub Pages**
  2. From **Source**, select “master branch” and then **Save**.

## [__](https://hugodocs.info/hosting-and-deployment/hosting-on-github/#hosting-github-user-or-organization-pages)Hosting GitHub User or Organization Pages

As mentioned [in this GitHub Help article](https://help.github.com/articles/user-organization-and-project-pages/), you can host a user/organization page in addition to project pages. Here are the key differences in GitHub Pages websites for Users and Organizations:

  1. You must use the `<USERNAME>.github.io` naming scheme for your GitHub repo.
  2. Content from the `master` branch will be used to publish your GitHub Pages site.

It becomes much simpler in this case: we’ll create two separate repos, one for Hugo’s content, and a git submodule with the `public` folder’s content in it.

### [__](https://hugodocs.info/hosting-and-deployment/hosting-on-github/#step-by-step-instructions)Step-by-step Instructions

  1. Create a `<YOUR-PROJECT>` git repository on GitHub. This repository will contain Hugo’s content and other source files.
  2. Create a `<USERNAME>.github.io` GitHub repository. This is the repository that will contain the fully rendered version of your Hugo website.
  3. `git clone <YOUR-PROJECT-URL> && cd <YOUR-PROJECT>`
  4. Make your website work locally (`hugo server` or `hugo server -t <YOURTHEME>`) and open your browser to [http://localhost:1313](http://localhost:1313/).
  5. Once you are happy with the results:
    * Press Ctrl+C to kill the server
    * `rm -rf public` to completely remove the `public` directory if there
  6. `git submodule add -b master git@github.com:<USERNAME>/<USERNAME>.github.io.git public`. This creates a git [submodule](https://github.com/blog/2104-working-with-submodules). Now when you run the `hugo` command to build your site to `public`, the created `public` directory will have a different remote origin (i.e. hosted GitHub repository). You can automate some of these steps with the following script.

#### Putting it Into a Script

You’re almost done. You can also add a `deploy.sh` script to automate the preceding steps for you. You can also make it executable with `chmod +x deploy.sh`.

The following are the contents of the `deploy.sh` script:
    
    #!/bin/bash
    
    echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"
    
    # Build the project.
    hugo # if using a theme, replace with `hugo -t <YOURTHEME>`
    
    # Go To Public folder
    cd public
    # Add changes to git.
    git add .
    
    # Commit changes.
    msg="rebuilding site `date`"
    if [ $# -eq 1 ]
      then msg="$1"
    fi
    git commit -m "$msg"
    
    # Push source and build repos.
    git push origin master
    
    # Come Back up to the Project Root
    cd ..
    

You can then run `./deploy.sh "Your optional commit message"` to send changes to `<USERNAME>.github.io`. Note that you likely will want to commit changes to your `<YOUR-PROJECDT>` repository as well.

That’s it! Your personal page should be up and running at `https://yourusername.github.io` within a couple minutes.

## Utiliser un Domaine Personnalisé

If you’d like to use a custom domain for your GitHub Pages site, create a file `static/CNAME`. Your custom domain name should be the only contents inside `CNAME`. Since it’s inside `static`, the published site will contain the CNAME file at the root of the published site, which is a requirements of GitHub Pages.

Refer to the [official documentation for custom domains](https://help.github.com/articles/using-a-custom-domain-with-github-pages/) for further information.

