---
layout: post
title: "Code Debugging"
summary: "Utilisation basique du debug dans VScode"
author: laurent
date: '2022-02-09 14:35:23 +0530'
category: ['PowerShell', 'Niv100']
thumbnail: /assets/img/header/Coding_1436x500.png
keywords: PowerShell, Niv100, Debugging, VSCode
permalink: /blog/CodeDebug/
usemathjax: true
---

## C'est quoi le debugging ?

Le débogage est le processus de détection et de suppression des erreurs existantes et potentielles (également appelées «bogues») dans un code logiciel qui peuvent provoquer un comportement inattendu ou un plantage.

Pour déboguer un programme, l'utilisateur doit c

Les outils de débogage (appelés débogueurs) sont utilisés pour identifier les erreurs de codage à différentes étapes de développement. Ils sont utilisés pour reproduire les conditions dans lesquelles l'erreur s'est produite, puis examiner l'état du programme à ce moment et localiser la cause de l'erreur.

Les programmeurs peuvent suivre l'exécution du programme étape par étape en évaluant la valeur des variables et arrêter l'exécution si nécessaire pour obtenir la valeur des variables ou réinitialiser les variables du programme

Dans cet article je vais m'attarder au débogage dans le langage PowerShell dans Visual Studio Code.

Si tu ne connais pas Visual Studio Code je t'invite à l'installer immédiatement en allant sur le [site](https://code.visualstudio.com/).

C'est à mon avis le meilleur éditeur du moment pour coder

## Debugging dans VSCode

### Les points d'arrêt

Le point d'arrêt, comme son non l'indique, est un point que l'on va poser dans notre code pour stopper l'execution du code a un endroit.

Dans VSCode il y a plusieurs façons de définir un point d'arrêt. Le point d'arrêt se visualise par un point rouge apparaissant dans la barre de défilement du code.

* la touche F9

Se placer sur la ligne de code et faire F9. (un nouvel appui sur F9 supprime le point d'arrêt)
![Point d'Arrêt F9](/assets/img/posts/20220209/pointarretF9.png "Point d'Arrêt F9")

* la palette de commande

Se placer sur la ligne de code et faire F1 puis chercher ```Toggle Breakpoint```
![Point d'Arrêt F9](/assets/img/posts/20220209/pointarretpalette.png "Point d'Arrêt F9")

## mode Debug

une fois le (ou les points d'arrêt) placé(s), on peut démarrer le débogage

* En appuyant sur F5

* En cliquant sur le menu ```Run``` puis ```Start Debugging```

L'execution du script va se faire et il va se mettre en pause sur le premier point d'arrêt qu'il rencontre

Plusieurs éléments apparaissent dans VSCode en mode Debug

* Une barre de menu sur le haut de l'écran

![Debug Bar](/assets/img/posts/20220209/debugbar.png "Debug Bar")

* une série de pallette sur le coté (droit ou gauche selon votre configuration)

![Palette](/assets/img/posts/20220209/palette.png "Palette")

### la barre de debug

Sur la barre de debug, on peut voir les informations suivantes :

![Continue](/assets/img/posts/20220209/BarDebugRestart.png) Continue/Pause [F5] => Cette commande reprend le programme et continue de l'exécuter normalement, sans s'arrêter à moins qu'il n'atteigne un autre point d'arrêt.

![Step Over](/assets/img/posts/20220209/BarDebugStepOver.png) Step Over [F10] => La commande Step Over prend une seule étape. Il exécute la ligne actuellement en surbrillance, puis s'arrête à nouveau

![Step Into](/assets/img/posts/20220209/BarDebugStepInto.png) Step Into [F11] => La commande Step Into fonctionne de la même manière que Step Over, sauf lorsqu'elle touche une fonction. Sur une fonction, Step Into entre dans cette fonction et s'arrête sur la première ligne à l'intérieur

![Step Out](/assets/img/posts/20220209/BarDebugStepOut.png) Step Out [Shift+F11] => La commande Step Out exécute tout le code de la fonction en cours, puis s'arrête à l'instruction suivante (s'il y en a une). En d'autres termes, cela vous permet de sortir de la fonction actuelle en un seul grand saut

![Restart](/assets/img/posts/20220209/BarDebugRestart.png) Restart [Ctrl+Shift+F5] => relance le debug du script

![Stop](/assets/img/posts/20220209/BarDebugStop.png) Stop [Shift+F5] => stop le mode debug