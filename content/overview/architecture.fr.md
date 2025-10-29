---
title: "Vue d'ensemble de l'architecture"
weight: 2
---

## 🏗️ Architecture technique détaillée

![global architecture](/images/architecture-global.png)

Notre solution Edge AI représente une **architecture hybride cloud-edge** sophistiquée qui apporte les capacités IA de niveau entreprise directement sur le terrain. Voici comment chaque composant fonctionne ensemble pour créer un système intelligent et autonome :

## 🚂 À l'edge : le train LEGO

### Composants Physiques
- **Moteur LEGO Technic** : Fournit un contrôle de mouvement précis
- **Hub LEGO** : Unité de contrôle centrale recevant les commandes via **Bluetooth Low Energy (BLE)**
- **Caméra embarquée** : Capture le flux vidéo en temps réel pour le traitement IA
- **Batterie portable** : Alimente toute la durée de la mission

### Cerveau Edge Computing
Le cœur de notre système edge est le **NVIDIA Jetson Orin** - un puissant System on Chip (SoC) qui combine :

| Composant | Spécification | Objectif |
|-----------|---------------|----------|
| **CPU** | ARM Cortex-A78AE | Contrôle système & coordination |
| **GPU** | NVIDIA Ampere | Accélération d'inférence IA |
| **Mémoire** | Jusqu'à 64GB LPDDR5 | Traitement de données haute vitesse |
| **Stockage** | SSD NVMe | Stockage de modèles & cache |

## 🌐 Pile logicielle Edge

### Couche Système d'Exploitation
```
┌─────────────────────────────────────┐
│        Red Hat Device Edge          │  ← OS Edge Entreprise
├─────────────────────────────────────┤
│           MicroShift               │  ← Kubernetes Léger
├─────────────────────────────────────┤
│     Microservices Edge             │  ← Logique IA & Contrôle
└─────────────────────────────────────┘
```

**Red Hat Device Edge** fournit :
- 🔒 **Sécurité** : Fonctionnalités de sécurité de niveau entreprise
- 🔄 **Mises à jour OTA** : Capacités de déploiement over-the-air
- ⚡ **Performance** : Optimisé pour les environnements à ressources limitées
- 🛡️ **Fiabilité** : Plateforme edge computing prête pour la production

**MicroShift** permet :
- 🎛️ **Orchestration de conteneurs** : Kubernetes à la périphérie
- 📦 **Gestion de services** : Déploiement et mise à l'échelle automatisés
- 🔄 **Auto-guérison** : Récupération automatique des pannes
- 📊 **Surveillance** : Suivi de l'état du système en temps réel

## ☁️ Le Cloud : Cluster OpenShift

### Composants d'Infrastructure
Situé dans le **Cloud AWS** avec **connectivité 5G** vers l'edge :

```
┌─────────────────────────────────────┐
│         Cluster OpenShift          │
├─────────────────────────────────────┤
│  ┌─────────────┐ ┌─────────────────┐│
│  │ OpenShift   │ │   Pipelines     ││
│  │     AI      │ │    CI/CD        ││
│  └─────────────┘ └─────────────────┘│
├─────────────────────────────────────┤
│  ┌─────────────┐ ┌─────────────────┐│
│  │ Surveillance│ │   Déploiement   ││
│  │    Vidéo    │ │    GitOps       ││
│  └─────────────┘ └─────────────────┘│
└─────────────────────────────────────┘
```

### Services Cloud

#### 🤖 Plateforme OpenShift AI
- **Projets Data Science** : Environnements isolés pour le développement ML
- **Jupyter Notebooks** : Expérience de développement interactive
- **Serveurs de Pipeline** : Exécution automatisée de workflows ML
- **Service de Modèles** : Points d'accès API REST pour l'inférence
- **Clusters GPU** : Infrastructure d'entraînement haute performance

#### 🔄 Infrastructure Pipeline CI/CD
- **Builds Multi-architecture** : Support pour x86_64 et ARM64
- **Pipelines Tekton** : Workflows CI/CD cloud-native
- **Registry de Conteneurs** : Stockage et distribution d'images sécurisés
- **Tests Automatisés** : Assurance qualité à chaque étape

#### 📹 Système de Vidéosurveillance
- **Streaming Temps Réel** : Flux caméra en direct depuis le train
- **Brokers Kafka** : Streaming de messages haute débit
- **Interface Web** : Capacités de surveillance à distance
- **Système d'Alerte** : Notifications immédiates pour les anomalies

## 🔄 Architecture de Flux de Données

{{< mermaid >}}
graph TD
    A[Camera Train] -->|Flux Video| B[Jetson Orin]
    B -->|Inference IA| C[Detection Panneaux]
    C -->|Commandes Controle| D[Hub LEGO]
    B -->|Connexion 5G| E[Cluster OpenShift]
    E -->|Donnees Entrainement| F[OpenShift AI]
    F -->|Modeles Mis a Jour| B
    E -->|Surveillance| G[Dashboard]
    E -->|GitOps| H[Deploiement]
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#e3f2fd
    style F fill:#f1f8e9
    style G fill:#fce4ec
    style H fill:#fff8e1
{{< /mermaid >}}

### Pipeline de Traitement Temps Réel
1. **📸 Capture d'Image** : La caméra capture les images de panneaux
2. **🔍 Inférence IA** : Le Jetson traite les images avec le modèle entraîné
3. **⚡ Prise de Décision** : L'IA détermine l'action appropriée (arrêt/marche)
4. **📡 Transmission Commande** : Commandes BLE envoyées au Hub LEGO
5. **🔄 Boucle de Rétroaction** : Résultats envoyés au cloud pour apprentissage continu

## 🏢 Support Multi-Architecture

### Infrastructure de Build
Notre système supporte les environnements de **calcul hétérogènes** :

| Architecture | Cas d'Usage | Plateforme |
|-------------|-------------|------------|
| **x86_64** | Développement & Entraînement | Cluster OpenShift |
| **ARM64** | Déploiement Edge | Jetson Orin |
| **Multi-arch** | Images Universelles | Registry de Conteneurs |

### Stratégie de Déploiement
- **🏭 Développement Cloud** : Modèles entraînés sur clusters x86_64 puissants
- **📦 Compilation Croisée** : Applications construites pour cible ARM64
- **🚀 Déploiement Edge** : Conteneurs légers déployés sur Jetson
- **🔄 Intégration Continue** : Tests automatisés à travers les architectures

## 🛡️ Sécurité & Fiabilité

### Sécurité Edge
- **🔐 Démarrage Sécurisé** : Démarrage système vérifié
- **🔒 Sécurité Conteneurs** : Environnements d'exécution isolés
- **📜 Gestion Certificats** : Authentification TLS mutuelle
- **🛡️ Isolation Réseau** : Canaux de communication segmentés

### Sécurité Cloud
- **🔑 RBAC** : Contrôle d'accès basé sur les rôles
- **🔐 Gestion Secrets** : Stockage d'identifiants chiffrés
- **📊 Journalisation Audit** : Suivi d'activité complet
- **🛡️ Politiques Réseau** : Micro-segmentation

Cette architecture démontre comment **la stack Edge AI de Red Hat** permet des applications IA sophistiquées dans des environnements à ressources limitées tout en maintenant la sécurité, la fiabilité et la scalabilité de niveau entreprise ! 🚀
