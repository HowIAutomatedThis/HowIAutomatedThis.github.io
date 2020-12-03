---
title: "Remplir un tableau Excel"
excerpt: "Ajouter une ligne dans Excel en récupérant les informations dans le nom d'un fichier"
tags:
  - Power Automate
  - Flow
  - Excel
  - Niv200
categories:
  - Power Platform
header:
  teaser: /assets/images/header/PowerAutomate.png
  overlay_image: /assets/images/header/PowerAutomateBandeau.png
  overlay_filter: 0.5
---

## Introduction

## Demande Initiale

Mon but, dans la mise en place de ce flow Power Automate, était d'automatiser une tâche de suivie des réponses faite a des courriers.

Voici les différentes étapes :
* Arrivée d'un nouveau courrier
* La personne en charge commence a rédiger la réponse (document Word)
* La personne en charge ajoute une entrée dans un fichier Excel avec les infos suivantes :
  * N° d'arrivée (un ID unique)
  * La date d'arrivée au format DDMMYYYY (07072020 par exemple)
  * Le nom de l'émetteur
  * l'objet du courrier
  * La personne a qui le courrier doit-être transmis
* Une fois la réponse finalisée, le document est envoyé à l'émetteur.
* La personne en charge modifie la ligne Excel correspondante pour ajouter les informations suivantes :
  * Date de réponse
  * N° de départ
  
La partie automatisation concerne tous ce qui touche au remplissage des informations dans Excel

## Le déclencheur

La première étape est de définir une action qui va déclencher notre flow.

Dans ce cas j'ai choisi de mettre un déclencheur sur la création d'un fichier (la réponse au courrier) dans un répertoire _Nouvelles Réponses_

![Déclencheur](\assets\images\post\2020-12-03-remplir_un_tableau_excel\Declencheur.png "Déclencheur")

## Les variables

Les variables sont les éléments qui vont contenir les informations que l'on va devoir écrire dans le fichier Excel.

Pour pouvoir récupérer les informations, une nomenclature pour le document Word de réponse a été définie :
<p style="text-align: center;">ARRIVEE_DATE_EMETTEUR_OBJECT_TRANSMIS.docx</p>

Grâce a cette nomenclature nous avons toutes les informations nécessaire à insérer dans Excel.

Première étape : Récupérer le nom du fichier sans le .docx.

![Nom du fichier avec extension](\assets\images\post\2020-12-03-remplir_un_tableau_excel\FileNameWithExtension.png "Nom du fichier avec extension")

Après avoir récupérer le nom du fichier avec son extension, j'utilise la fonction _split()_ pour enlever l'extension

![Nom du fichier sans extension](\assets\images\post\2020-12-03-remplir_un_tableau_excel\FileNameWithoutExtension.png "Nom du fichier sans extension")

La fonction utilisé est :
<p style="text-align: center;">split(variables('FileNameWithExtension'), '.')[0]</p>
