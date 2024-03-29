---
layout: post
title: "Break point VS Code"
summary: "Les différents types de Break Point dans Visual Studio Code"
author: laurent
date: '2022-02-10 06:00:00 +0530'
category: ['VSCode', 'Niv200']
thumbnail: /assets/img/header/Coding_1436x500.png
keywords: VSCode, Niv200, Debugging, Break Point
permalink: /blog/BreakPointVSCode/
usemathjax: true
---

## Les différents types de Break Point dans Visual Studio Code

Dans Visual Studio Code, il existe plusieurs types de Break Point.

* Conditional Breakpoint
* Inline Breakpoint
* Function Breakpoint
* Logpoint

Pour ajouter l'un de ces Break Point, il faut se placer sur la ligne de code et cliquer sur ```Run``` puis ```New Breakpoint```

![Point d'Arrêt F9](/assets/img/posts/20220210/AddOtherBP.png "Point d'Arrêt F9")

Pour la mise en situation je vais utiliser ce bout de code

```powershell
$pathToUse = "C:\MyDev\New folder"

$docs = @(
    'chm', 'doc', 'docm', 'docx', 'dot', 'dotx', 'eml', 'eps',
    'hwp', 'log', 'm3u', 'odt', 'pages', 'pdf', 'pub', 'rtf',
    'sxw', 'txt', 'wpd', ' wps', 'xml', 'xps'
)

$files = Get-ChildItem -Path $pathToUse

Foreach ($x in $files) {
    if ($docs.Contains($x.Extension.TrimStart('.').ToLower())) {
        New-Item -ItemType Directory -Path $pathToUse -Name "Documents" -ErrorAction Ignore
        Move-Item -Path $x.FullName -Destination $pathToUse/"Documents"
    }
}
```

Dans la suite de l'article nous allons passer en revue ces différents types de Break Point.

### 1 - Conditional Breakpoint

Comme son nom l'indique ce break point va arrêter l'execution du code si la condition qu'on lui définie est vraie.

Pour expliquer le fonctionnement je vais appliquer un Conditional Break Point sur la ligne  12 de mon code.

La condition sera si ```$x.name``` est égal à ```Stop mon BreakPoint.docx```.

![Conditional Breakpoint](/assets/img/posts/20220210/AjoutConditionalBP.png "Conditional Breakpoint")

![Conditional Breakpoint](/assets/img/posts/20220210/AjoutConditionalBP1.png "Conditional Breakpoint")

Après avoir saisie la condition appuyer sur ``Enter``` pour valider.

Ensuite il suffit de lancer le mode debug et de patienter jusqu'à ce que le break point soit atteint. Une fois atteint, l'execution du code se met en pause et si on vérifie la valeur de ```$x.name``` nous verrons que c'est bien ```Stop mon BreakPoint.docx```.

![Conditional Breakpoint](/assets/img/posts/20220210/AjoutConditionalBP2.png "Conditional Breakpoint")

### 2 - Inline Breakpoint

Ce type de breakpoint est utilisé quand vous utilisez l'écriture dite inline c'est a dire qu'au lieu de bien indenter votre code, vous l'écrivez sur une seule ligne.

Dans mon code je peux par exemple écrire ca pour afficher le nom de chacun des documents contenus dans mon dossier

```powershell
Get-ChildItem -Path $pathToUse | ForEach-Object {Write-output $_.Name}
```

Pour ajouter un Break Point sur la commande ```Write-Ouput``` je vais utiliser les Inline Breakpoint

Pour cela il faut se positionner sur le début de la commande ```Write-Ouput``` et ajouter le Inline Breakpoint en passant par le menu ``Run```

![Inline Breakpoint](/assets/img/posts/20220210/AjoutInlineBP.png "Inline Breakpoint")

Le Inline Breakpoint se matérialise par un point rouge apparraissant a l'endroit de la ligne ou on l'a défini.

![Inline Breakpoint](/assets/img/posts/20220210/AjoutInlineBP1.png "Inline Breakpoint")

On lance le mode debug, qui va stopper en arrivant sur le break point

![Inline Breakpoint](/assets/img/posts/20220210/AjoutInlineBP2.png "Inline Breakpoint")

### 3 - Function Breakpoint

Ce type de breakpoint permettra d'arrêter l'execution du code à l'appel d'une fonction.

Dans mon code par exemple je peux définir un Function Breakpoint sur l'appelle de la fonction ```Move-Item``` par exemple.

Pour ce faire passer par me menu ```Run``` puis ```New Breakpoint``` et enfin ```Function Breakpoint```

![Function Breakpoint](/assets/img/posts/20220210/AjoutFunctionBP.png "Function Breakpoint")

La pallette ```Breakpoint``` apparait et permet de définir le nom de la fonction sur laquelle faire le break point. Saisir le nom de la fonction est faire ```Enter```

![Function Breakpoint](/assets/img/posts/20220210/AjoutFunctionBP1.png "Function Breakpoint")

Lancer ensuite le mode debug qui va automatiquement se mettre en pause sur la fonction ```Move-Item```

![Function Breakpoint](/assets/img/posts/20220210/AjoutFunctionBP2.png "Function Breakpoint")

### 4 - Logpoint

Les logpoint sont une autre variante utile des points d'arrêt. Au lieu de s'introduire dans votre débogueur, ils enregistrent des messages sur votre console et servent d'instructions de trace temporaires

Les logpoint peuvent être un excellent dispositif d'injection lorsque vous déboguez un serveur de production qui ne peut pas être arrêté ou mis en pause

Malheureusement, et sauf erreur de ma part, ils ne sont pas supportés en Powershell
