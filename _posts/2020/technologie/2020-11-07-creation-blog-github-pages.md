---
title:  "Créer son blog avec Github Pages"
categories: 
  - technologie
tags: 
  - technologie
  - github
  - github pages
  - site statique
  - jekyll
header:
  teaser: assets/images/2020-github_logo.png
description: "Mes notes pour la création d'un site internet statique avec Github Pages et Jekyll."
toc: true
---

La création d'un site sur Github Pages et le passage par un générateur de site statique est assez technique et il faut s'accrocher un peu pour ne pas abandonner. Pour ceux qui n'ont pas le temps à passer sur la logistique du site, le plus simple reste d'utiliser Wordpress et de l'installer sur un fournisseur d'espace web avec un nom de domaine.

## Créer un compte Github et activer Github Pages

Ouvrir un compte sur <a href="http://Github.com" target="_blank">Github</a>.
La documentation de Github Pages est assez fournie sur le sujet <a href="https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/creating-a-github-pages-site" target="_blank">ici</a>.

## Jekyll : générateur de site statique
### Installation de Jekyll

Pour utiliser Jekyll, le plus simple est d'aller sur <a href="https://jekyllrb.com/docs/" target="_blank">le site consacré à Jekyll</a> et de suivre les instructions pour installer Ruby, RubyGems, GCC et Make, puis Jekyll.
Ensuite, comme indiqué <a href="https://jekyllrb.com/docs/" target="_blank">ici</a>, il y a des commandes à envoyer pour :
+ installer Jekyll et les gems,
![installation_de_gem]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-install-gem.PNG)
+ créer un nouveau site Jekyll dans le répertoire `myblog`,
![creation_site_jekyll]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-build-myblog.PNG)

Voici comment les fichiers créés se présentent dans l'explorateur :
![creation_site_jekyll]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-explorer.PNG)

### Générer et tester le site en local

Le code du site est généré dans le dossier `_site`. Pour pouvoir générer le site et l'afficher en local pour vérifier que tout fonctionne, il suffit de lancer le serveur dans la fenêtre de commande avec l'instruction suivante :
```
bundle exec jekyll serve --watch
```
![serveur_jekyll]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-launch-server.PNG)

Lorsque le serveur est lancé, le site web est visionnable via un navigateur avec l'adresse suivante : <a href="http://localhost:4000/" target="_blank">http://localhost:4000/</a>
![illustration_site_de_base_jekyll]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-site-web.PNG)

Pour information, sur Github Pages, la génération du code se fait automatiquement sans avoir à générer le site au préalable avant de le pousser sur le dépôt Github. En effet, Github Pages utilise Jekyll pour la génération du site, c'est pourquoi le dossier `_site` n'a pas besoin d'être transféré sur le dépôt Github. Cela explique la raison pour laquelle le dossier est inclus dans le `.gitignore`.

<!-- ### Choisir un thème et modifier le site -->
<!-- ## Transférer le site sur Github -->
## Mettre en place le nom de domaine

Ce que j'ai trouvé compliqué lors de la création de mon site a été la redirection sur le dépôt de Github Pages avec le nom de domaine. J'ai trouvé la réponse en regroupant les informations de plusieurs sites pour comprendre <a href="https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site" target="_blank">l'aide de Github sur la redirection d'un nom de domaine</a>. De plus, il est important d'avoir un site en https et pas seulement http pour des raisons de sécurité.

Pour paramétrer sa redirection, vérifier que Github Pages est activé. Pour ce faire:
+ aller dans les paramètres :
![Declaration_de_github_en_pages]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-settings.PNG)
+ Sélectionner la branche qui comportera le site, dans cet exemple, c'est `main` dans la `Branch` puis cliquer sur `Save`
![Declaration_de_github_en_pages]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-source.PNG)
+ Si vous revenez au même emplacement, le chemin du site est présenté. C'est ce chemin que l'on va récupérer pour y renvoyer la redirection du nom de domaine.
![Declaration_de_github_en_pages]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-settings-path.PNG)

Avant cela, il faut mettre en place des paramètres du côté du fournisseur du nom de domaine (mon exemple est fait chez Gandi mais tout autre fournisseur devrait avoir les mêmes paramètres):
+ paramétrer le DNS avec les valeurs suivantes pour toutes les adresses listées (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`) avec `@` pour le nom, `A` pour le Type et 1800 pour `TTL`,
+ rajouter une ligne pour un type `CNAME` avec `www` pour le nom, `1800` pour `TTL` et `VOTRE-NOM-DE-DEPOT-GITHUB.github.io.` pour la `valeur` (ne pas oublier le `.` à la fin).
![Parametres_du_fournisseur_de_nom_de_domaine]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-dns.PNG)
+ paramétrer la 'redirection WEB' en `https` et un certificat SSL sera délivré ultérieurement (j'ai reçu les miens dans l'heure qui a suivi): 
![exemple_de_redirection]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-redirection.PNG)

Une fois que tout est paramétré, retourner aux paramètres du site sur Github Pages et ajouter le nom de domaine, cliquer sur `Save` puis cocher `Enforce HTTPS` :
![Parametre_de_github_pages]({{ site.baseurl }}/assets/images/2020-tuto-github-pages-jekyll-redirection-https.PNG)

## Planifier ses articles en avance

Pour ne pas avoir tous ses articles publiés dès leur transfert sur Github, on peut faire en sorte que le site soit reconstruit à intervalles réguliers. Lorsque la date de l'article correspond à la journée, l'article sera publié. Pour ce faire, j'ai suivi <a href="https://seankilleen.com/2020/02/how-to-deploy-github-pages-on-a-schedule-to-publish-future-posts/" target="_blank">ce lien</a>.

J'espère que cet article aura été utile. N'hésitez pas à me faire un retour.
