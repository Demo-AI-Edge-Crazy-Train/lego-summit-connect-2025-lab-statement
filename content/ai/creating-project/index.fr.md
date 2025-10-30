+++
title = "Préparation de l'environnement"
draft= false
weight= 2
[[ressources]]
  src = '**.png'
+++

## Introduction

Il est important de comprendre les principaux concepts que nous allons utiliser autour de l'IA.

* **OpenShift AI** est une plateforme intégrée qui facilite la gestion de projets d'IA dans un environnement cloud-natif basé sur OpenShift.
* Chaque participant travaillera dans un **Data Science Project**, qui sert d'espace isolé pour organiser ses ressources (données, notebooks, modèles, pipelines…).  
* Le **Workbench** fournit un environnement de développement interactif basé sur Jupyter, dans lequel les data scientists peuvent écrire, exécuter et tester leur code.  
* Le **Pipeline Server** est le moteur de workflow qui exécute et trace les différentes étapes du traitement des données et de l'entraînement des modèles.  
* Une **Data Connection** permet de relier la plateforme à une source de stockage (par exemple S3 ou Ceph) afin de sauvegarder et partager les artefacts produits dans un Workbench ou un Pipeline. 
* Enfin, le **repo Git** contient le code source du projet, garantissant une bonne reproductibilité et favorisant la collaboration autour du même ensemble de scripts et de notebooks.

Ces composants interagissent pour offrir une chaîne complète, du développement expérimental jusqu'à la mise en production des modèles.

## Connexion à un projet

1. Dans le tableau de bord OpenShift AI, naviguez vers le menu *Data Science Projects* sur la gauche :  
![02-02-ds-proj-nav](02-02-ds-proj-nav.png)

2. Un identifiant unique vous a été attribué au début de l'atelier. Un projet portant le **même nom** a été créé pour vous. Cliquez dessus pour l’ouvrir. Vous devriez arriver sur une page similaire :  
![project-empty-state](project-empty-state.png)

## Création d'une Data Connection

Nous avons déployé une instance Minio pour gérer le stockage objet dans le cluster. Vous devrez **ajouter une Data Connection** pointant vers ce stockage.

1. Faites défiler jusqu'au bas de la page du projet et cliquez sur *Data Connections* :  
![02-02-add-dc.png](02-02-add-dc.png)
Pour l'instant, la page est vide.

2. Cliquez sur *Add data connection* et saisissez les informations suivantes :
- **Name** :  
```pipelines```
- **Access Key** :  
```userX```  **⏪ REMPLACEZ PAR VOTRE IDENTIFIANT**
- **Secret Key** :  
```{{< param minioPass >}}```
- **Endpoint** :  
```{{< param minioEndpoint >}}```
- **Region** :  
```none```
- **Bucket** :  
```userX```  **⏪ REMPLACEZ PAR VOTRE IDENTIFIANT**

Le résultat devrait ressembler à ceci :  
![data-connection.png](data-connection.png)

3. Une fois le formulaire rempli, cliquez sur *Add data connection* pour valider.

## Création d'un Pipeline Server

Il est fortement recommandé de créer votre Pipeline Server avant de créer le Workbench. C'est ce que nous allons faire maintenant :

1. Dans le menu en haut, ouvrez l'onglet *Pipelines* et cliquez ensuite sur *Configure pipeline server*.  
![02-02-pipelineserver01.png](02-02-pipelineserver01.png)

2. Dans le menu déroulant avec l'icône de clé, sélectionnez la Data Connection créée précédemment (nommée *pipelines*) pour remplir automatiquement le formulaire avec les informations enregistrées et cliquez sur le bouton *Configure pipeline server*.  
![02-02-pipelineserver02.png](02-02-pipelineserver02.png)

3. Attendez que le Pipeline Server termine sa création. Lorsque celui-ci est prêt, votre écran devrait ressembler à ceci :  
![02-02-pipelineserver03.png](02-02-pipelineserver03.png)

À ce stade, votre Pipeline Server est prêt et déployé.

⚠️ Il est impératif d'attendre la fin de la création du Pipeline Server. Si celui-ci est encore en cours, patientez jusqu'à son achèvement.
