+++
title = "Environment Setup"
draft= false
weight= 2
[[resources]]
  src = '**.png'
+++

## Introduction

It is important to understand the key concepts we will be working with in this OpenShift AI workshop.

**OpenShift AI** is an integrated platform that simplifies the management of AI projects in a cloud-native environment based on OpenShift.

Each participant will work within a **Data Science Project**, which serves as an isolated space to organize resources such as data, notebooks, models, and pipelines.  
A **Data Connection** allows the platform to connect to a storage source (for example, S3 or Ceph) to save and share artifacts produced by pipelines.  
The **Pipeline Server** is the orchestration engine that executes and tracks the various stages of data processing and model training.  
The **Workbench** provides an interactive Jupyter-based development environment where data scientists can write, run, and test their code.  
Finally, the **Git repository** contains the project’s source code, ensuring reproducibility and collaboration around the same set of scripts and notebooks.

These components interact to provide a complete workflow, from experimental development to production deployment of models.

The instructions below will guide you through these steps. Follow them carefully.

## Connecting to a Project

* First, in the OpenShift AI dashboard, navigate to the `Data Science Projects` menu on the left:
![02-02-ds-proj-nav](02-02-ds-proj-nav.png)

* A unique ID was assigned to you at the start of the workshop. A project with the **same name** as your ID has been created for you. Click on this project. You should arrive at a page similar to this:
![project-empty-state](project-empty-state.png)

## Create a Data Connection for the Pipeline Server

* We have deployed a Minio instance to manage object storage in the cluster.
* You will need to **add a Data Connection** that points to this storage. Scroll to the bottom of the project page and click on `Data Connections`:
![02-02-add-dc.png](02-02-add-dc.png)

* You will arrive at an empty page for now. Click on `Add data connection`. Here is the information you need to enter:
- Name:  
```pipelines```
- Access Key:  
```userX```  **⏪ REPLACE WITH YOUR ID**
- Secret Key:  
```{{< param minioPass >}}```
- Endpoint:  
```{{< param minioEndpoint >}}```
- Region:  
```none```
- Bucket:  
```userX```  **⏪ REPLACE WITH YOUR ID**

* The result should look like this:
![data-connection.png](data-connection.png)

* Once you have filled out the form, click on `Add data connection` to confirm.

## Create a Pipeline Server

It is highly recommended to create your Pipeline Server before creating the Workbench. This is what we will do now:

* In the top menu, click on `Pipelines`. Then click on `Configure pipeline server`.
![02-02-pipelineserver01.png](02-02-pipelineserver01.png)

* In the dropdown menu with the key icon, select the Data Connection you created earlier (named `pipelines`) and click the `Configure pipeline server` button.
![02-02-pipelineserver02.png](02-02-pipelineserver02.png)

* Wait for the Pipeline Server to finish creating. When your Pipeline Server is ready, your screen will look like this:
![02-02-pipelineserver03.png](02-02-pipelineserver03.png)

At this stage, your Pipeline Server is ready and deployed.

**IMPORTANT**: You must wait for the Pipeline Server creation to complete. If it is still in progress, please wait until it finishes.
