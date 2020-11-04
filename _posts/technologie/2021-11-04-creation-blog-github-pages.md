---
layout: post
title:  "Créer son blog avec Github Pages"
author: yowie
categories: [ technologie ]
tags: [ technologie, github, github pages ]
# image: assets/images/2020-dix-pour-cent.jpg
description: "Mes notes pour la création d'un site internet statique avec Github Pages et Jekyll."
toc: true
---

## Créer un compte Github et activer Github Pages

Ouvrir un compte sur Github.

## Jekyll : générateur de site statique

### Installation de Jekyll

Pour utiliser Jekyll, le plus simple est d'aller sur <a href="https://jekyllrb.com/docs/" target="_blank">le site consacré à Jekyll</a> et de suivre les instructions pour installer Ruby, RubyGems, GCC et Make, puis Jekyll.

<!-- ### Choisir un thème et modifier le site -->

### Générer et tester le site en local

Dans une fenêtre de commande au niveau de l'emplacement des fichiers du site, générer le code du site. Pour pouvoir l'afficher en local pour vérifier que tout fonctionne, il suffit de lancer le serveur avec la commande suivante :
```
bundle exec jekyll serve --watch
```
Lorsque le serveur est lancé, le site web est visionnable via un navigateur avec l'adresse suivante : <a href="http://localhost:4000/" target="_blank">http://localhost:4000/</a>

Pour information, sur Github Pages, la génération du code se fait automatiquement sans avoir à générer le site au préalable avant de le pousser sur le dépôt Github. En effet, Github Pages utilise Jekyll pour la génération du site, c'est pourquoi le dossier `_site` n'a pas besoin d'être transféré sur le dépôt Github.

<!-- ## Transférer le site sur Github -->

## Mettre en place le nom de domaine

<!-- Les manip' cheloues et compliquées -->

![Declaration_de_github_en_pages]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-source.PNG)

![Parametres_du_fournisseur_de_nom_de_domaine]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-dns.PNG)

![exemple_de_redirection]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-redirection.PNG)

![Parametre_de_github_pages]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-redirection-https.PNG)


## Planifier ses articles en avance

Pour ce faire, j'ai suivi <a href="https://seankilleen.com/2020/02/how-to-deploy-github-pages-on-a-schedule-to-publish-future-posts/" target="_blank">ce lien</a>.
