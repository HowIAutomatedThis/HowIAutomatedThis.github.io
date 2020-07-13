﻿---
title: Utiliser Parameter Sets !
excerpt: Utiliser des jeux de paramètres pour simplifier les commandes PowerShell
classes: wide
toc_sticky: false
tags:
  - Powershell
  - Fonctions Avancées
categories:
  - Powershell
header:
  teaser: /assets/images/header/Coding_1436x500.png
  overlay_image: /assets/images/header/Coding_1436x500.png
  overlay_filter: 0.5
---

## Définition

Les jeux de paramètres permettent de définir un ensemble de paramètre qui doivent être utiliser par une fonction.

Cela permet par exemple de définir pour une même fonction 2 paramètres différents en entrée. Dans cette article nous allons voir comment, par exemple, faire une fonction New-MyADUser avec comme paramètre soit un ensemble de nom soit un fichier.

## Fonction avec utilisateur en entrée

Cette fonction est assez basique. Elle va prendre en paramètre d'entrée une liste de nom d'utilisateur a créer.

```powershell
function New-MyADUser {
    param (
        [System.String[]]$UserName
    )

    foreach($User in $UserName) {
        New-ADUser -Name $User -GivenName ($User.Split(".")[0]) -Surname ($User.Split(".")[1])
    }

}
```

Ensuite je peux lancer la création de mes utilisateurs

```powershell
New-MyADUser -UserName "Utilisateur1.Test","Utilisateur2.Test","Utilisateur3.Test"
```
