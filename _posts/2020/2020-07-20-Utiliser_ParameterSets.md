---
title: Utiliser Parameter Sets !
excerpt: Utiliser des jeux de paramètres pour simplifier les commandes PowerShell
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

## Fonction avec un fichier en entrée

Dans ce cas nous allons reprendre la même fonction mais avec en entrée la liste des noms dans un fichier csv.

```powershell
function New-MyADUser {
    param (
        [System.String]$FilePath
    )

    $UserName = Import-Csv -Path $FilePath

    foreach ($User in $UserName) {
        New-ADUser -name $User.UserName -GivenName ($User.UserName.Split(".")[0]) -Surname ($User.UserName.Split(".")[1]) -Server srv-ad101 -Credential $CredAdmin
    }

}
```

Ensuite je peux lancer la création de mes utilisateurs

```powershell
New-MyADUser -FilePath '.\Utiliser les Parameter Sets\Utilisateurs.csv'
```

Donc maintenant nous avons 2 fonctions différentes mais qui font sensiblement la même chose : créer des utilisateurs dans l'Active Directory

C'est la que rentre en jeu les jeux de paramètre. Nous allons immédiatement voir ca :-)

## Fonction avec un fichier ou un utilisateur en entrée (ParameterSet)

Le but donc est de combiner ces 2 fonctions en une seule mais acceptant les 2 types de paramètre en entrée.

