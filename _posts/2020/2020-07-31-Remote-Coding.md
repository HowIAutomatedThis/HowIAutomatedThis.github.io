---
title: "Remote Coding"
excerpt: "Exploration de la possiblité de coder sur des environnements distants"
tags:
  - Powershell
  - Code
  - Remote
categories:
  - Powershell
header:
  teaser: /assets/images/header/Coding_1436x500.png
  overlay_image: /assets/images/header/Coding_1436x500.png
  overlay_filter: 0.5
---

## Introduction

Lors de ma reprise du développement, il y a quelques temps, après des années de repos je me suis très vite lancé sur le Powershell ce qui me semblait le plus naturel par rapport a mon activité professionnelle.

Je me suis très vite intéressé a d'autre langage comme le Javascript, le GO mais également un petit retour au source avec le C++.

La question de faire co-exister tout ces environnements c'est très vite posé.

Je me suis lassé, très rapidement, des machines virtuelles qui nécessitent quand meme d'avoir une machine hôte assez puissante pour tout faire tourner. De plus je trouvais ces environnements trop isolés les uns des autres.

Étant un utilisateur de Visual Studio Code je me suis vite tourné du coté des extensions proposées et j'ai découvert l'extension [```Remote Development```](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

## Remote Development

### Présentation

Le pack ```Remote Development``` vous permet d'ouvrir n'importe quel dossier dans un conteneur, sur une machine distante ou dans le sous-système Windows pour Linux (WSL) et de profiter de l'ensemble complet des fonctionnalités de VS Code.

Ce pack contient en réalité 3 extensions :
1. Remote - SSH
2. Remote - Containers
3. Remote - WSL

Je ne parlerais ici que de ```Remote - Containers``` n'ayant pas encore joué avec les 2 autres ;-)

### Remote - Containers

En découvrant ```Remote - Containers``` j'ai trouvé ça magique. Réellement !

Imaginez donc pouvoir, directement depuis Visual Studio Code, lancer votre espace de développement dans un container avec tout ce qu'il faut de pré-configuré.

Cette solution étant basée sur l'utilisation des containers, je vous mets le lien sur [Docker](https://www.docker.com/products/docker-desktop) qui est un pré-requis nécessaire a l'utilisation de cette extension.

Je ne prétends pas tout maîtriser dans la technologie des ```Containers``` mais c'est la qu'intervient la magie. Avec de simple connaissance de base je vais vous montrer comment j'ai pu par exemple faire mes débuts sur ```GO```

## GO (Golang)

### Installation

Alors je ne sais pas pourquoi GO, au cours de mes navigations sur différentes supports, j'ai très souvent entendu parler de ce langage.

Après quelques recherches, certains points m'ont bien plus comme le fait :
1. que la syntaxe est proche du C
2. que c'est cross-platform

Afin de pouvoir tester GO il faut lancer un container contenant la configuration nécessaire a son execution.

Après avoir ajouter l'extension ```Remote Developement``` l'icône suivante apparaît dans VSCode

![Remote Development](\assets\images\post\2020-07-31-Remote-Coding\RemoteDevelopment.png "Remote Development")

Après avoir cliquer sur cette icône un menu apparaît proposant plusieurs choix nous allons prendre

![Remote Development Menu](\assets\images\post\2020-07-31-Remote-Coding\RemoteDevelopmentMenu.png "Remote Development Menu")

Je vais ouvrir un dossier que j'avais précédemment créé sur mon disque :

![Dossier](\assets\images\post\2020-07-31-Remote-Coding\Dossier.png "Dossier")

Dans le menu suivant on me demande dans quel environnement je veux executer l'ouverture du dossier précédemment sélectionné

![GOContainer](\assets\images\post\2020-07-31-Remote-Coding\GOContainer.png "GO Container")

Dans notre cas nous choisissons GO

Après quelques instants nécessaire au lancement du container on se retrouve dans VSCode avec un dossier (local n'oubliez pas) mais ouvert dans un container GO ! Magique je vous l'avez dit :-)

On retrouve dans le dossier ```.devcontainer``` :
- decontainer.json qui est le fichier de configuration de l'extension Remote Development pour l'environnement GO
- Dockerfile qui est le fichier de configuration du Container Docker

La configuration avancée de Docker ou des Container n'est pas le sujet de l'article.

Nous voila donc avec un environnement de développement GO complet et fonctionnelle sans aucune configuration particulière

Il ne nous reste plus qu'a faire nos premières lignes de code pour découvrir ce nouveau langage ;-)