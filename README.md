# 🚂 Mission: Impossible - Crazy Train Lab
## Red Hat Summit Connect 2025 - Edge AI Workshop

[![Netlify Status](https://api.netlify.com/api/v1/badges/bf353b9e-7ba7-40e6-9127-308c80c35b74/deploy-status)](https://app.netlify.com/projects/lego-workshop-summit-connect-2025/deploys)

> **🎬 CLASSIFIED TRANSMISSION**  
> *"The train is running mad at full speed and has no driver! Your mission, should you choose to accept it, is to train and deploy an AI model at the edge to stop the train before it crashes..."*

🌐 **Live Workshop**: [Red Hat Summit Connect 2025 - Workshop Lego](https://lego-workshop-summit-connect-2025.netlify.app/)

---

## 🎯 Workshop Overview

This interactive workshop combines **Edge AI**, **Computer Vision**, and **LEGO robotics** to create an engaging learning experience around Red Hat's Edge Computing and AI/ML technologies. Participants will train and deploy AI models to control an autonomous LEGO train system.

### 🎪 Mission Scenario
- **Setting**: Mission Impossible-themed adventure
- **Challenge**: Stop a runaway LEGO train using Edge AI
- **Technologies**: OpenShift AI, Jetson Orin, Red Hat Device Edge
- **Duration**: 2 hours hands-on experience

---

## 🏗️ Architecture Overview

Our **hybrid cloud-edge architecture** demonstrates enterprise-grade AI capabilities at the edge:

```
┌────────────────────────────────────────────────────────────────┐
│                           Cloud (AWS)                          │
├────────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐ │
│  │  OpenShift AI   │  │  CI/CD Pipeline │  │  GitOps         │ │
│  │  - Model Train  │  │  - Multi-arch   │  │  - ArgoCD       │ │
│  │  - MLOps        │  │  - Tekton       │  │  - Auto Deploy  │ │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘ │
└────────────────────────────────────────────────────────────────┘
                                │
                                │   5G Connection
                                │
┌────────────────────────────────────────────────────────────────┐
│                        Edge (LEGO Train)                       │
├────────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐ │
│  │  Jetson Orin    │  │  Camera Vision  │  │  LEGO Hub       │ │
│  │  - AI Inference │  │  - Real-time    │  │  - BLE Control  │ │
│  │  - Device Edge  │  │  - Traffic Sign │  │  - Motor Ctrl   │ │
│  │  - MicroShift   │  │  - Detection    │  │  - Sensors      │ │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘ │
└────────────────────────────────────────────────────────────────┘
```

---

## 🤖 Technology Stack

### **Edge Computing**
- **NVIDIA Jetson Orin**: ARM64 SoC with GPU acceleration
- **Red Hat Device Edge**: Enterprise-grade edge OS
- **MicroShift**: Lightweight Kubernetes for edge
- **Computer Vision**: Real-time traffic sign detection

### **Cloud Platform**
- **OpenShift AI (RHOAI)**: ML/AI development platform
- **OpenShift Container Platform**: Kubernetes orchestration
- **Tekton Pipelines**: Cloud-native CI/CD
- **ArgoCD**: GitOps deployment automation

### **AI/ML Components**
- **Transfer Learning**: Pre-trained model adaptation
- **ONNX Models**: Cross-platform AI model format
- **Multi-architecture Support**: x86_64 and ARM64
- **Real-time Inference**: Sub-second decision making

### **Hardware Integration**
- **LEGO Technic Train**: Physical demonstration platform
- **Bluetooth Low Energy**: Wireless control protocol
- **5G Connectivity**: Cloud-edge communication
- **Camera Sensors**: Real-time video capture

---

## 📚 Workshop Modules

### 🎨 **1. Presentation (15min)**
- Mission briefing and scenario introduction
- Architecture overview and technology stack
- Learning objectives and success criteria

### 🤖 **2. Artificial Intelligence (1h)**
- **Getting Connected**: Access OpenShift AI platform
- **Creating Project**: Set up ML development environment  
- **Creating Workbench**: Jupyter notebook workspace
- **Model Training**: Train traffic sign detection model
- **Model Serving**: Deploy AI model for inference

### ⚙️ **3. DevOps (30min)**
- **CI/CD Pipelines**: Multi-architecture container builds
- **GitOps Deployment**: Automated application delivery
- **Edge Integration**: Deploy to Jetson Orin device

---

## 🚀 Getting Started

### Prerequisites
- Access to OpenShift AI cluster
- GitHub account for GitOps workflows
- Basic knowledge of containers and Kubernetes

### Quick Start
1. **Access Workshop**: Navigate to [workshop site](https://lego-workshop-summit-connect-2025.netlify.app/)
2. **Choose Language**: Select English or French version
3. **Follow Modules**: Complete hands-on exercises step-by-step
4. **Deploy Model**: See your AI control the LEGO train!

---

## 🛠️ Development Setup

### Local Development
```bash
# Clone the repository
git clone https://github.com/Demo-AI-Edge-Crazy-Train/lego-summit-connect-2025-lab-statement.git
cd lego-summit-connect-2025-lab-statement

# Initialize Hugo theme submodule
git submodule update --init --recursive

# Start Hugo development server
hugo server --port 1313
```

### Site Configuration
- **Hugo Version**: 0.143.1 or later
- **Theme**: hugo-theme-learn
- **Languages**: French (default) and English
- **Mermaid Diagrams**: Enabled for architecture visualization

---

## 🌍 Multilingual Support

This workshop supports both **French** and **English**:

- **French**: Default language (`/fr/` routes)
- **English**: Secondary language (`/en/` routes)
- **Navigation**: Automatic language switching
- **Content**: Fully translated exercises and documentation

---

## 🔗 Related Repositories

- **AI Model Training**: [workshop-model-training](https://github.com/Demo-AI-Edge-Crazy-Train/workshop-model-training)
- **Application Code**: [opentour2025-app](https://github.com/Demo-AI-Edge-Crazy-Train/opentour2025-app)
- **Lab Infrastructure**: Private repositories for OpenShift setup

---

## 📊 Workshop Success Metrics

By completing this workshop, participants will have:

- ✅ **Trained an AI model** capable of detecting LEGO traffic signs
- ✅ **Deployed the model** on edge computing platform
- ✅ **Built CI/CD pipelines** for multi-architecture deployments
- ✅ **Implemented GitOps** for automated application delivery
- ✅ **Controlled a real LEGO train** using Edge AI! 🎉

---

## 🤝 Contributing

We welcome contributions to improve this workshop:

1. Fork the repository
2. Create a feature branch
3. Make your improvements
4. Submit a pull request

### Documentation Standards
- Use Hugo markdown format
- Maintain multilingual consistency
- Include practical examples
- Follow Red Hat style guidelines

---

## 📄 License

This workshop content is developed for Red Hat Summit Connect 2025 educational purposes.

---

## 📞 Support

For workshop support and questions:
- **Event**: Red Hat Summit Connect 2025
- **Technology**: Red Hat Edge AI Stack
- **Community**: Red Hat Developer Program

**Ready, Agent? Your mission starts now! 🚀**
