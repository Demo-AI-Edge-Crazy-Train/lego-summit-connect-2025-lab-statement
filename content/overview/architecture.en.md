---
title: "Architecture Overview"
weight: 2
---

## 🏗️ Detailed Technical Architecture

![global architecture](/images/architecture-global.png)

Our Edge AI solution is a sophisticated **hybrid cloud-edge architecture** that brings enterprise-grade AI capabilities directly to the field. Here's how each component works together to create an intelligent, autonomous system:

## 🚂 At the Edge: the LEGO Train

### Physical Components
- **LEGO Technic Motor**: Provides precise movement control
- **LEGO Hub**: Central control unit receiving commands via **Bluetooth Low Energy (BLE)**
- **On-board Camera**: Captures real-time video feed for AI processing
- **Portable Battery**: Powers the entire duration of the mission

### Edge Computing Brain
The heart of our edge system is the **NVIDIA Jetson Orin** - a powerful System on Chip (SoC) that combines:

| Component | Specification | Purpose |
|-----------|---------------|---------|
| **CPU** | ARM Cortex-A78AE | System control & coordination |
| **GPU** | NVIDIA Ampere | AI inference acceleration |
| **Memory** | Up to 64GB LPDDR5 | High-speed data processing |
| **Storage** | NVMe SSD | Model storage & caching |

### Edge Software Stack
```
┌─────────────────────────────────────┐
│         Red Hat Device Edge         │  ← Enterprise Edge OS
├─────────────────────────────────────┤
│             MicroShift              │  ← Lightweight Kubernetes
├─────────────────────────────────────┤
│          Microservices Edge         │  ← AI & Control Logic
└─────────────────────────────────────┘
```

**Red Hat Device Edge** provides:
- **Security**: Enterprise-grade security features
- **OTA Updates**: Over-the-air (OTA) deployment capabilities
- **Performance**: Optimized for resource-constrained environments
- **Reliability**: Production-ready edge computing platform

**MicroShift** enables:
- **Container Orchestration**: Kubernetes at the edge
- **Service Management**: Automated deployment and scaling
- **Self-healing**: Automatic recovery from failures
- **Monitoring**: Real-time system health tracking

## ☁️ In the Cloud: the OpenShift Cluster

### Infrastructure Components
Located in **AWS Cloud** with **5G connectivity** to the edge:

```
┌─────────────────────────────────────┐
│          OpenShift Cluster          │
├─────────────────────────────────────┤
│ ┌───────────────┐ ┌───────────────┐ │
│ │   OpenShift   │ │     CI/CD     │ │
│ │       AI      │ │   Pipelines   │ │
│ └───────────────┘ └───────────────┘ │
│ ┌───────────────┐ ┌───────────────┐ │
│ │     Video     │ │     GitOps    │ │
│ │   Monitoring  │ │   Deployment  │ │
│ └───────────────┘ └───────────────┘ │
└─────────────────────────────────────┘
```

### Cloud Services

#### OpenShift AI Platform 🤖
- **Data Science Projects**: Isolated environments for ML development
- **Jupyter Notebooks**: Interactive development experience
- **Pipeline Servers**: Automated ML workflow execution
- **Model Serving**: REST API endpoints for inference
- **GPU Clusters**: High-performance training infrastructure

#### CI/CD Pipeline Infrastructure 🔄
- **Multi-architecture Builds**: Support for x86_64 and ARM64
- **Tekton Pipelines**: Cloud-native CI/CD workflows
- **Container Registry**: Secure image storage and distribution
- **Automated Testing**: Quality assessment at every step

#### Video Surveillance System 📹
- **Real-time Streaming**: Live camera feed from the train
- **Kafka Brokers**: High-throughput message streaming
- **Web Interface**: Remote monitoring capabilities
- **Alert System**: Immediate notifications for anomalies

## 📊 Data Flow

{{< mermaid >}}
graph TD
    A[Train Camera] -->|Video Stream| B[Jetson Orin]
    B -->|AI Inference| C[Traffic Sign Detection]
    C -->|Control Commands| D[LEGO Hub]
    B -->|5G Connection| E[OpenShift Cluster]
    E -->|Training Data| F[OpenShift AI]
    F -->|Updated Models| B
    E -->|Monitoring| G[Dashboard]
    E -->|GitOps| H[Deployment]
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#e3f2fd
    style F fill:#f1f8e9
    style G fill:#fce4ec
    style H fill:#fff8e1
{{< /mermaid >}}

### Real-time Processing Pipeline
1. **Image Capture**: Camera captures traffic sign images
2. **AI Inference**: Jetson processes images using trained model
3. **Decision Making**: AI determines appropriate action (stop/go)
4. **Command Transmission**: BLE commands sent to LEGO Hub
5. **Feedback Loop**: Results sent to cloud for continuous learning

## 🏢 Multi-Architecture Support

### Build Infrastructure
Our system supports **heterogeneous** computing environments:

| Architecture | Use Case | Platform |
|-------------|----------|----------|
| **x86_64** | Development & Training | OpenShift Cluster |
| **ARM64** | Edge Deployment | Jetson Orin |
| **Multi-arch** | Universal Images | Container Registry |

### Deployment Strategy
- **Cloud Development**: Models trained on powerful x86_64 clusters
- **Cross-compilation**: Applications built for ARM64
- **Edge Deployment**: Lightweight containers deployed to Jetson
- **Continuous Integration**: Automated testing across all architectures

## 🛡️ Security & Reliability

### Edge Security
- **Secure Boot**: Verified system startup
- **Container Security**: Isolated execution environments
- **Certificate Management**: Mutual TLS authentication
- **Network Isolation**: Segmented communication channels

### Cloud Security
- **RBAC**: Role-based access control
- **Secrets Management**: Encrypted credential storage
- **Audit Logging**: Comprehensive activity tracking
- **Network Policies**: Micro-segmentation

This architecture demonstrates how **Red Hat's Edge AI stack** enables sophisticated AI applications in resource-constrained environments while maintaining enterprise-grade security, reliability, and scalability!
