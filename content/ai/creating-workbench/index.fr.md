+++
title = "Création du workbench"
draft= false
weight= 3
[[ressources]]
  src = '**.png'
+++

## Lancer un Workbench

* Une fois que la Data Connection et le Pipeline Server ont été entièrement créés, vous pouvez passer à la création du Workbench. Cliquez sur l'onglet `Workbenches` puis `Create workbench`.
![02-03-create-wb.png](02-03-create-wb.png)
* Assurez-vous de remplir les caractéristiques suivantes :  
    * Choisissez un nom, comme par exemple : `My Workbench`  
    * Sélectionnez l'image : `CUSTOM Crazy train lab`
    * Taille du conteneur : `Small`
    * Conservez les paramètres de stockage par défaut.
    * En bas, cochez `Use a data connection`.
    * Faites défiler vers le bas jusqu'à `Use existing data connection`
    * Sélectionnez dans la liste la Data Connection `pipelines` que vous avez précédemment créée.
    * Cela devrait ressembler à ce qui suit :
![02-02-launch-workbench-01.png](02-02-launch-workbench-01.png)
![02-02-launch-workbench-02.png](02-02-launch-workbench-02.png)
* Cliquez sur `Create workbench` pour valider et attendez que son statut bleu `Starting` passe en vert `Running`.
* Une fois que le Workbench est créé, cliquez sur le lien `Open` pour vous y connecter.
![02-03-open-link.png](02-03-open-link.png)

* Authentifiez-vous avec les mêmes informations que précédemment.
* Il vous sera demandé d'accepter les paramètres suivants :
![02-02-accept.png](02-02-accept.png)

* CLiquez sur `Allow selected permissions`.
* Vous devriez maintenant voir ceci :
![02-02-jupyter.png](02-02-jupyter.png)

## Cloner le repo Git de l'atelier

Nous allons cloner le contenu de notre repo Git afin que vous puissiez accéder à tout le matériel nécessaire à l'entrainement du modèle d'IA.

* Ouvrez l'onglet avec l'icône Git dans le menu de gauche :
![git-clone-1.png](git-clone-1.png)
* Cliquez sur `Clone a Repository`.
* Entrez l'URL du repo Git : ``{{< param gitAIRepoUrl >}}``. Sélectionnez également `Download the repository` puis validez avec `Clone`.
![git-clone-2.png](git-clone-2.png)

À ce stade, votre environnement Jupyter est prêt pour le travail que nous voulons y faire.
