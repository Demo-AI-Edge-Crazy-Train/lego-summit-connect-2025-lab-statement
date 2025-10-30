---
title: "Vue d'ensemble de l'architecture"
weight: 2
---

![global architecture](/images/architecture-global.png)

Notre solution Edge AI est une **architecture hybride cloud-edge** sophistiquée qui apporte des capacités IA de qualité professionnelle directement sur le terrain. Voici comment tous les composants fonctionnent ensemble pour créer un système intelligent et autonome :

## 🚂 À l'edge : le train LEGO

### Composants physiques
- **Moteur LEGO Technic** : Fournit un contrôle de mouvement précis
- **Hub LEGO** : Unité de contrôle centrale recevant les commandes via **Bluetooth Low Energy (BLE)**
- **Caméra embarquée** : Capture le flux vidéo en temps réel pour le traitement IA
- **Batterie portable** : Alimente toute la durée de la mission

### Cerveau Edge Computing
Le cœur de notre système edge est le **NVIDIA Jetson Orin**, un puissant System on Chip (SoC) qui combine :

| Composant | Spécification | Objectif |
|-----------|---------------|----------|
| **CPU** | ARM Cortex-A78AE | Contrôle système & coordination |
| **GPU** | NVIDIA Ampere | Accélération de l'inférence IA |
| **Mémoire** | Jusqu'à 64GB LPDDR5 | Traitement de données haute vitesse |
| **Stockage** | SSD NVMe | Stockage de modèles & cache |

### Pile logicielle Edge
```
┌─────────────────────────────────────┐
│         Red Hat Device Edge         │  ← Système d'exploitation Edge d'entreprise
├─────────────────────────────────────┤
│             MicroShift              │  ← Kubernetes léger
├─────────────────────────────────────┤
│          Microservices Edge         │  ← Logique IA & contrôle
└─────────────────────────────────────┘
```

**Red Hat Device Edge** fournit :
- **Performance** : Optimisé pour les environnements à ressources limitées
- **Fiabilité** : Plateforme d'edge computing prête pour la production
- **Sécurité** : Fonctionnalités de sécurité de qualité professionnelle
- **Mises-à-jour OTA** : Capacités de déploiement over-the-air (OTA)

**MicroShift** permet :
- **Orchestration de conteneurs** : Plateforme Kubernetes à l'edge
- **Gestion de services** : Déploiement et mise à l'échelle automatisés
- **Auto-réparation** : Récupération automatique en cas de défaillances
- **Surveillance** : Suivi de l'état du système en temps réel

## ☁️ Dans le Cloud : le cluster OpenShift

### Composants d'infrastructure
Situé dans le **cloud AWS** avec **connectivité 5G** vers l'edge :

```
┌─────────────────────────────────────┐
│          Cluster OpenShift          │
├─────────────────────────────────────┤
│ ┌───────────────┐ ┌───────────────┐ │
│ │   OpenShift   │ │   Pipelines   │ │
│ │       AI      │ │     CI/CD     │ │
│ └───────────────┘ └───────────────┘ │
│ ┌───────────────┐ ┌───────────────┐ │
│ │  Surveillance │ │  Déploiement  │ │
│ │     Video     │ │     GitOps    │ │
│ └───────────────┘ └───────────────┘ │
└─────────────────────────────────────┘
```

### Services cloud

#### Plateforme OpenShift AI 🤖
- **Projets Data Science** : Environnements isolés pour le développement ML
- **Jupyter Notebooks** : Expérience de développement interactive
- **Serveurs de pipeline** : Exécution automatisée de workflows ML
- **Service de modèles** : Points d'accès API REST pour l'inférence
- **Clusters GPU** : Infrastructure d'entraînement haute performance

#### Infrastructure pipeline CI/CD 🔄
- **Builds multi-architecture** : Support pour x86_64 et ARM64
- **Pipelines Tekton** : Workflows CI/CD cloud-natifs
- **Registry de conteneurs** : Stockage et distribution d'images sécurisés
- **Tests automatisés** : Évaluation de la qualité à chaque étape

#### Système de vidéosurveillance 📹
- **Streaming temps réel** : Flux caméra en direct depuis le train
- **Brokers Kafka** : Streaming de messages haute débit
- **Interface web** : Capacités de surveillance à distance
- **Système d'alerte** : Notifications immédiates pour les anomalies

## 📊 Flux de données

{{< mermaid >}}
graph TD
    A[Caméra du train] -->|Flux vidéo| B[Jetson Orin]
    B -->|Inférence IA| C[Détection de panneaux]
    C -->|Commandes de contrôle| D[Hub LEGO]
    B -->|Connexion 5G| E[Cluster OpenShift]
    E -->|Données d'entraînement| F[OpenShift AI]
    F -->|Modèles mis-à-jour| B
    E -->|Surveillance| G[Tableau de bord]
    E -->|GitOps| H[Déploiement]
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#e3f2fd
    style F fill:#f1f8e9
    style G fill:#fce4ec
    style H fill:#fff8e1
{{< /mermaid >}}

### Pipeline de traitement temps réel
1. **Capture d'image** : La caméra capture les images de panneaux
2. **Inférence IA** : Le Jetson traite les images avec le modèle entraîné
3. **Prise de décision** : L'IA détermine l'action appropriée (arrêt/marche)
4. **Transmission commande** : Commandes BLE envoyées au Hub LEGO
5. **Boucle de rétroaction** : Résultats envoyés au cloud pour l'apprentissage en continu

## 🏢 Support Multi-Architecture

### Infrastructure du build
Notre système supporte les environnements de calcul **hétérogènes** :

| Architecture | Cas d'usage | Plateforme |
|-------------|-------------|------------|
| **x86_64** | Développement & entraînement | Cluster OpenShift |
| **ARM64** | Déploiement edge | Jetson Orin |
| **Multi-arch** | Images universelles | Registry de conteneurs |

### Stratégie de déploiement
- **Développement cloud** : Modèles entraînés sur des clusters x86_64 puissants
- **Compilation croisée** : Applications construites pour ARM64
- **Déploiement edge** : Conteneurs légers déployés sur Jetson
- **Intégration continue** : Tests automatisés sur toutes les architectures

## 🛡️ Sécurité & fiabilité

### Sécurité edge
- **Démarrage sécurisé** : Démarrage système vérifié
- **Sécurité conteneurs** : Environnements d'exécution isolés
- **Gestion certificats** : Authentification TLS mutuelle
- **Isolation réseau** : Canaux de communication segmentés

### Sécurité cloud
- **RBAC** : Contrôle d'accès basé sur les rôles
- **Gestion des secrets** : Stockage d'identifiants chiffrés
- **Journalisation et audit** : Suivi d'activité complet
- **Politiques réseau** : Micro-segmentation

Cette architecture démontre comment la **stack Edge AI de Red Hat** permet des applications IA sophistiquées dans des environnements à ressources limitées tout en maintenant une sécurité, une fiabilité et une scalabilité de qualité professionnelle !
