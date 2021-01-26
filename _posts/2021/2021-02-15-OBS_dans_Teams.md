---
title: "OBS dans Teams"
excerpt: "Comment diffuser la sortie OBS dans un call Teams"
tags:
  - OBS
  - Teams
  - Streaming
  - Niv100
categories:
  - Streaming
header:
  teaser: /assets/images/header/OBS-Logo.png
  overlay_image: /assets/images/header/OBS-Bandeau.png
  overlay_filter: 0.5
---

## Introduction

Le but recherché maintenant que nous savons mettre un [fond vert virtuel dans OBS](https://www.howiautomatedthis.com/2021/02/Fond_vert_viruel_OBS.html) et de récupérer ce que nous montons dans OBS pour le diffuser dans Teams lors d'un Meetup par exemple.

Pour ce faire je vais utiliser les produits suivant :

* [OBS](https://obsproject.com/fr/)
* [OBS NDI Plugin](https://obsproject.com/forum/resources/obs-ndi-newtek-ndi%E2%84%A2-integration-into-obs-studio.528/)
* [Microsoft Teams](https://www.microsoft.com/fr-fr/microsoft-teams/group-chat-software)
* [NDI Tools](https://ndi.tv/tools/#download-tools)

## Première étape : Installer tous les logiciels

Je ne vais pas m'étaler sur cette partie. On execute le fichier et suivant, suivant .... OK 👍

## Seconde étape : Configurer NDI dans OBS

Dans le menu d'OBS choisir Tools puis NDI Output settings

![NDI Menu](\assets\images\post\2021-02-15-OBS_dans_Teams\OBS-NDI-MENU.png "NDI Menu")

Cocher la case Main Output et changer le nom si vous le souhaitez. Ce nom va être réutilisé plus tard il faudra s'en souvenir. Moi je vais laisser OBS

![NDI Activation](\assets\images\post\2021-02-15-OBS_dans_Teams\OBS-NDI-ACTIVATION.png "NDI Activation")

## Troisième étape : Configurer le NDI sur Teams

Pour pouvoir utiliser un périphérique NDI, il faut d'abord dans Teams activé cette option. Cela se fait dans les paramètres

![Paramètre Teams](\assets\images\post\2021-02-15-OBS_dans_Teams\TEAMS-PARAM.png "Paramètre Teams")

puis dans le menu Autorisations

![Autorisation Teams](\assets\images\post\2021-02-15-OBS_dans_Teams\TEAMS-AUTORISATION.png "Autorisation Teams")