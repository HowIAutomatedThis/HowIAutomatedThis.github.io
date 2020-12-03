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

### Récupérer le nom du fichier sans le .docx.

![Nom du fichier avec extension](\assets\images\post\2020-12-03-remplir_un_tableau_excel\FileNameWithExtension.png "Nom du fichier avec extension")

Après avoir récupérer le nom du fichier avec son extension, j'utilise la fonction _split()_ pour enlever l'extension

![Nom du fichier sans extension](\assets\images\post\2020-12-03-remplir_un_tableau_excel\FileNameWithoutExtension.png "Nom du fichier sans extension")

La fonction utilisé est :
<p style="text-align: center;">split(variables('FileNameWithExtension'), '.')[0]</p>

dernière étape, je découpe le nom du fichier sans extension dans un tableau pour pouvoir utiliser chaque information indépendamment.

![Tableau de chaîne](\assets\images\post\2020-12-03-remplir_un_tableau_excel\ArrayFileNameSplit.png "Tableau de chaîne")

La fonction utilisé est :
<p style="text-align: center;">split(variables('FileNameWithoutExtension'), '_')</p>

### Création des variables

Maintenant que nous avons un tableau contenant toutes les informations nécessaire, nous allons initialiser les variables qui seront écrites dans Excel plus tard

![Variable ARRRIVEE](\assets\images\post\2020-12-03-remplir_un_tableau_excel\VariableArrivee.png "Variable ARRRIVEE")

La fonction utilisé est :
<p style="text-align: center;">variables('ArrayFileNameSplit')[0]</p>

je fais de même pour toutes les variables 

![Liste Variable](\assets\images\post\2020-12-03-remplir_un_tableau_excel\ListeVariable.png "Liste Variable")

Il n'y a que pour la variable date de reception qu'il y a une petite astuce.

En effet la date dans le nom du fichier est sous la forme _07072020_. Évidement dans mon fichier Excel j'aimerais qu'elle apparaisse sous la forme _07/07/2020_.

Pour faire cela j'utilise à la fois la fonction _concat()_ et la fonction _substring()_

<p style="text-align: center;">concat(substring(variables('ArrayFileNameSplit')[1],0,2),'/',substring(variables('ArrayFileNameSplit')[1],2,2),'/',substring(variables('ArrayFileNameSplit')[1],4,4))</p>

## Mettre à jour le fichier excel

EN COURS DE REDACTION :-)