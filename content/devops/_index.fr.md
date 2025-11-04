+++
title = "IA à l'Edge (30min)"
weight = 3
chapter = true
pre = "<b>3. </b>"
+++

### Partie 3

# Intelligence Artificielle à l'Edge

Dans cette section finale, vous implémenterez les pratiques modernes de CI/CD et GitOps pour des déploiements de modèles d'IA à l'Edge.

Cette section comprend :
- **Pipelines CI** : Construire des images de conteneurs multi-architecture avec les pipelines Tekton
  - Déployer des pipelines pour les architectures x86_64 et ARM64
  - Comprendre comment construire des images pour les dispositifs Edge (Nvidia Jetson Orin)
  - Travailler avec les registres de conteneurs et les manifestes multi-architecture
- **Pipelines CD pour le Edge** : Construire des images de conteneurs bootc avec les pipelines Tekton
  - Construire des images bootc pour la carte Jetson Orin
  - Déployer l'image bootc sur la carte Jetson Orin
  - Gérer les dispositifs Edge à travers une solution de gestion de flotte

Vous vivrez le cycle de vie complet du modèle d'IA au déploiement en production, comprenant comment les applications Edge AI modernes sont construites, testées et déployées à travers différentes architectures.

## Votre espace de travail

Vous allez utiliser OpenShift Dev Spaces. OpenShift Dev Spaces utilise Kubernetes et les conteneurs pour fournir un environnement de développement cohérent, sécurisé et sans configuration, accessible depuis une fenêtre de navigateur.

Utilisez le lien suivant pour générer votre environnement OpenShift Dev Spaces :

[![Contribute](https://www.eclipse.org/che/contribute.svg)](https://devspaces.apps.{{< param openshift_domain >}}/f?url={{< param gitAppRepoUrl >}})

Connectez-vous avec vos identifiants OpenShift (userX/mot-de-passe). Si c'est la première fois que vous accédez à Dev Spaces, vous devez autoriser Dev Spaces à accéder à votre compte. Dans la fenêtre Autoriser l'accès, cliquez sur Autoriser les permissions sélectionnées.

Cela ouvre l'espace de travail, qui vous semblera assez familier si vous avez l'habitude de travailler avec VS Code. Avant d'ouvrir l'espace de travail, une fenêtre contextuelle peut apparaître pour vous demander si vous avez confiance dans le contenu de l'espace de travail. Cliquez sur Oui, je fais confiance aux auteurs pour continuer.

![trust-authors](/images/dev-section/trust-authors.png)

Attendez que l'espace de travail soit disponible, ce qui prend quelques minutes pour mettre en place un environnement de développement complexe avec plusieurs services (**Kafka**, **Zookeeper**, **Mosquitto**), les outils (**OpenShift CLI**, **Maven**, **Python**, **Node.js**), et s'assurer que toutes les dépendances nécessaires sont installées (comme **OpenCV**).

Dans l'explorateur de projets situé à gauche de l'espace de travail, naviguez jusqu'au dossier `summitconnect2025-app` et regardez les différents projets.

![espace de travail](/images/dev-section/workspace.png)
