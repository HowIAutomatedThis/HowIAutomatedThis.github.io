---
title: "Remote - Containers"
excerpt: "Exploration de la possibilité de coder sur des environnements distants"
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

Si comme moi vous testez des tas de choses sur votre machine on se retrouve rapidement avec une machine qui n'a plus vraiment un environnement de travail maîtrisé ;-)

Vous vous êtes sûrement poser la question

```
Comment être sur de travailler sur un environnement de développement maîtrisé ?
```

Au début je tournais avec des machines virtuelles HyperV sur mon portable mais je me suis très vite retrouvé limité par les ressources de ma machine.

Je faisais tourner une VM windows 10 compléte pour faire du développement Powershell par exemple ou pour tester d'autre langage comme GO ou Javascript.

Je cherchais une solution qui soit :

* légère a deployer
* maîtrisée - invariable dans le temps
* facilement réutilisable

Après quelques recherches sur Internet, je suis tombé par hasard sur une vidéo présentant l'extension Visual Studio Code ```Remote Development```

```Remote Development``` est en fait un pack contenant les extensions :
* Remote - SSH
* Remote - WSL
* Remote - Containers

la partie qui va nous intéresser aujourd'hui est ```Remote - Containers```

## Remote - Containers

### Installation

{% capture mynote%}
Je ne vais pas expliquer dans cette article ce qu'est docker ou les containers ce n'est pas le sujet de l'article
{% endcapture %}
{{mynote}}{: .notice--info}

Ma machine de travail étant sous Windows 10 il faut installer en pré-requis  [DOCKER](https://www.docker.com/products/docker-desktop)

Une fois l'installation de Docker effectuée, il faut installer l'extension ```Remote - Development``` dans Visual Studio Code :

![Installation Extension](\assets\images\post\2020-07-31-Remote _Containers\InstallationExtension.png "Installation Extension")

Une fois installé, on retrouve bien les 3 extensions contenues dans le pack

![Liste Extension](\assets\images\post\2020-07-31-Remote _Containers\ListeExtension.png "Liste Extension")

### Test

L'extension possède un mode de test que nous allons utiliser tout de suite pour vérifier l'installation.

Pour tester il suffit de cliquer sur l'icône apparue en bas a gauche dans VSCode

![Icône Extension](\assets\images\post\2020-07-31-Remote _Containers\IconeExtension.png "Icône Extension")

De choisir dans le menu ```Try a sample```

![Test Extension](\assets\images\post\2020-07-31-Remote _Containers\TryExtension.png "Test Extension")

On va prendre l'environnement ```Node``` pour tester

![Test Node](\assets\images\post\2020-07-31-Remote _Containers\NodeEnv.png "Test Node")

Une fois l'environnement choisi, VSCode va se rouvrir et démarrer automatiquement un container avec toute la configuration nécessaire

![Start Node](\assets\images\post\2020-07-31-Remote _Containers\StartNodeEnv.png "Start Node")

Dans le terminal on peut vérifier que nous sommes bien dans une environnement Node

![Node Version](\assets\images\post\2020-07-31-Remote _Containers\NodeVersion.png "Node Version")

Pour quitter cette environnement de travail il faut de nouveau cliquer sur l'icone en bas a gauche de VSCode et chossir ```Close remote Connection``` dans le menu

![Close Node](\assets\images\post\2020-07-31-Remote _Containers\CloseNodeEnv.png "Close Node")

### Powershell

Ok maintenant que l'on a vu comment installer l'extension et qu'on a vérifié que tout fonctionne nous allons voir comment configurer un environnement de développement pour Powershell

![Test Extension](\assets\images\post\2020-07-31-Remote _Containers\TryExtension.png "Test Extension")

Dans cette capture d'écran nous voyons 3 possibilité qui sont assez claire :
* Open folder (ouvrir un dossier existant dans un container)
* Open Workspace (ouvrir un workspace VSCode dans un container)
* Open repository (ouvrir un dépot GIT dans un container)

Je vais utiliser la première dans cette article. Pour se faire je créé un répertoire dans mon arborescence qui va me servir de test

![PS DEMO](\assets\images\post\2020-07-31-Remote _Containers\PSDemo.png "PS Demo")

Comme pour les tests, je clique sur l'icone en bas a gauche dans VSCode et je choisis ```Open folder in container``` et choisir le dossier précédemment crée.

Une fenêtre de selection d'environnement un peu plus étoffée que la précédente apparaît

![Selection Env](\assets\images\post\2020-07-31-Remote _Containers\SelectionEnv.png "Selection Env")

Dans cette fenêtre rechercher ```Powershell``` et le lancer

Première remarque : nous sommes dans une machine sous linux

```powershell
root@5056e6336fe2:/workspaces/POWERSHELL# uname
Linux
```

ce qui m'amène a la seconde remarque : nous sommes sur la dernière version de PS CORE ;-)

```powershell
root@5056e6336fe2:/workspaces/POWERSHELL# pwsh
PowerShell 7.0.3
Copyright (c) Microsoft Corporation. All rights reserved.

https://aka.ms/powershell
Type 'help' to get help.
```


