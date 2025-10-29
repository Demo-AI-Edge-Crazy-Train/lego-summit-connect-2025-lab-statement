+++
title = "Environment Setup"
draft= false
weight= 2
[[resources]]
  src = '**.png'
+++

## Introduction

It is important to understand the key concepts we will be working with in this OpenShift AI workshop.

OpenShift AI is an integrated platform that simplifies the development, deployment, and management of Data Science and AI projects in a cloud-native environment based on OpenShift.

Each participant will work within a **Data Science project**, which serves as an isolated space to organize resources such as models, data, notebooks, and pipelines.
A **Data Connection** allows the platform to connect to a storage source (for example, S3 or Ceph) to save and share artifacts produced by pipelines.
The **pipeline server** is the orchestration engine that executes and tracks the various stages of data processing and model training workflows.
The **Workbench** provides an interactive Jupyter-based environment where data scientists can write, run, and test their code.
Finally, the **Git repository** contains the project’s source code, ensuring reproducibility and collaboration around the same set of scripts and notebooks.

These components interact to provide a complete workflow, from experimental development to production deployment of models.

The instructions below will guide you through these steps. Follow them carefully.

## Connecting to a Project

* First, in the OpenShift AI Dashboard application, navigate to the Data Science Projects menu on the left:

![02-02-ds-proj-nav](02-02-ds-proj-nav.png)

* A project with the **same name** as your user id has been created for you. You have been assigned a unique user ID at the begining of the lab. Remember this user ID for the instances creation. 

Click on the available project project. You should land on a similar page:
![project-empty-state](project-empty-state.png)

## Create a Data Connection for the pipeline server

* We have deployed an instance of Minio in the cluster to act as a simple Object Storage for our purposes.
* You will need to **Add data connection** that points to it. Scroll down to the bottom of data science project page and click on "Data Connections":
![02-02-add-dc.png](02-02-add-dc.png)

* You will land to and empty state page. Click on "Add data connection". Here are the information you need to enter:
- Name:  
```pipelines```
- Access Key - **REPLACE WITH YOUR USER ID**:  
```userX```
- Secret Key:  
```{{< param minioPass >}}```
- Endpoint:  
```{{< param minioEndpoint >}}```
- Region:  
```none```
- Bucket - **REPLACE WITH YOUR USER ID**:  
```userX```

**IMPORTANT**: Once again, the bucket you will use has to match with the user ID you were provided

* The result should look like:
![data-connection.png](data-connection.png)

## Create a Pipeline Server

It is highly recommended to create your pipeline server before creating a workbench. So let's do that now!

* On the top menu click on "Pipelines". Then click on "Configure pipeline server"

![02-02-pipelineserver01.png](02-02-pipelineserver01.png)

* Select the Data Connection created earlier (**pipelines**) and click the **Configure pipeline server** button:
![02-02-pipelineserver02.png](02-02-pipelineserver02.png)

* Wait for the pipeline server to finish its creation. When your pipeline server is ready, your screen will look like the following:
![02-02-pipelineserver03.png](02-02-pipelineserver03.png)

At this point, your pipeline server is ready and deployed.

IMPORTANT: You need to **wait** until that screen is ready. If it's still spinning, wait for it to complete. If you continue and create your workbench **before** the pipeline server is ready, your workbench will not be able to submit pipelines to it.
