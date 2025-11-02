+++
title = "Déploiement du modèle"
draft= false
weight= 6
[[ressources]]
  src = '**.png'
+++

Dans cette section, vous allez déployer le modèle que vous venez de créer sur le serveur de modèles d'OpenShift AI.

**Remarque** : si quelque chose s'est mal passé lors de l'entraînement du modèle dans la section précédente, vous pouvez toujours suivre cette section en commençant par la première partie intitulée **FALLBACK**.

## FALLBACK – Vous pouvez passer cette section si vous avez entraîné votre modèle avec succès

1. Dans le tableau de bord OpenShift AI, ouvrez le menu de gauche et cliquez sur *Data Science Projects*.

2. Cliquez sur le projet correspondant à votre nom d'utilisateur.

3. Sélectionnez l'onglet *Data connections*.

4. Cliquez sur *Add data connection* et saisissez les informations suivantes :
- **Name** :  
```Model Registry```
- **Access key** :  
```userX```  **⏪ REMPLACEZ PAR VOTRE IDENTIFIANT**
- **Secret key** :  
```{{< param minioPass >}}```
- **Endpoint** :  
```{{< param minioEndpoint >}}```
- **Region** :  
```none```
- **Bucket** :  
```{{< param baseModelBucket >}}```

## Créer un serveur de modèles

1. Dans le tableau de bord OpenShift AI, ouvrez le menu de gauche et cliquez sur *Data Science Projects*.

2. Cliquez sur le projet correspondant à votre nom d'utilisateur.

3. Sélectionnez l'onglet *Models*.
![go-to-models](go-to-models.png)

4. Cliquez sur *Add model server*
![add-model-server.png](add-model-server.png)

5. Saisissez les informations suivantes :
- **Model server name** : ```{{< param newModelServerName >}}```
- **Serving runtime** : sélectionnez *OpenVINO Model Server*
- **Number of model server replicas to deploy** : ```1```
- **Model server size** : sélectionnez *{{< param newModelServerSize >}}*
- **Model route** : décoché
- **Token authentication** : décoché

Le résultat devrait ressembler à ceci :
![add-model-server-config.png](add-model-server-config.png)

6. Cliquez sur *Add* pour valider la création du serveur de modèles.

## Déployer le modèle

1. Sous *Models and model servers*, à droite du serveur de modèles que vous venez de créer, cliquez sur *Deploy model*.
![select-deploy-model.png](select-deploy-model.png)

2. Saisissez les informations suivantes :
- **Model deployment name** : ```{{< param newModelName >}}```
- **Model server** : ```{{< param newModelServerName >}}``` qui devrait déjà être automatiquement sélectionné
- **Model framework (name - version)** : sélectionnez *onnx - 1*
- **Existing data connection** - **Name** : sélectionnez *{{< param newModelDataConnection >}}* (ou *Model Registry* pour ceux qui ont fait le FALLBACK)
- **Existing data connection** - **Path** : ```{{< param newModelPath >}}``` (ou ```default/model.onnx``` pour ceux qui ont fait le FALLBACK)

Le résultat devrait ressembler à ceci :
![deploy-a-model.png](deploy-a-model.png)

3. Cliquez sur *Deploy* pour valider le déploiement du modèle.

4. Patientez quelques instants. Si le modèle est déployé avec succès, son statut passera au vert après quelques secondes.
![model-deployed-success.png](model-deployed-success.png)

Nous allons maintenant vérifier que le modèle fonctionne correctement en l'interrogeant !

## Interroger le modèle deployé

Une fois que le modèle est servi, nous pouvons l'utiliser comme un endpoint qui peut être requêté. Nous envoyons une requête REST ou gRPC au modèle et obtenons un résultat. Cela s'applique à toute personne travaillant au sein de notre cluster. Il peut s'agir de collègues ou d'applications.

* Tout d'abord, nous devons obtenir l'URL du serveur de modèle.
* Pour ce faire, cliquez sur le lien **Internal Service** dans la colonne **Inference endpoint**.
* Dans le popup, vous verrez quelques URLs pour notre serveur de modèle.
![inference-url.png](inference-url.png)

* Notez ou copiez le **RestUrl**, qui devrait être quelque chose comme `http://modelmesh-serving.{userX}:8008`

Nous allons maintenant utiliser cette URL pour interroger le modèle. Retournez dans votre workbench, c'est-à-dire dans l'environnement jupyter notebooks.

- Dans votre workbench, naviguez vers le notebook `inference/inference.ipynb`. **Mettez à jour la variable** "RestUrl" avec l'url copié précédemment dans votre presse papier.
- Exécutez les cellules du notebook, et assurez-vous que vous comprenez ce qui se passe.

La première section interroge le modèle de base qui a été déployé globalement pour tout le monde. La deuxième section prend endpoint RestUrl et interroge le modèle que vous avez formé et déployé. Vous devriez constater qu'avec le modèle de base, seuls les panneaux de signalisation de limitation de vitesse sont reconnus. Après le réapprentissage du modèle, vous avez maintenant un modèle qui peut mieux détecter les panneaux de signalisation Lego. Félicitations !
