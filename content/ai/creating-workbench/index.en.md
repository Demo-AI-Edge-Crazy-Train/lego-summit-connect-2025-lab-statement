+++
title = "Workbench Creation"
draft= false
weight= 3
[[resources]]
  src = '**.png'
+++

## Launch a Workbench

* Once the Data Connection and Pipeline Server have been fully created, you can proceed to create the Workbench. Click on the `Workbenches` tab and then `Create workbench`.

![02-03-create-wb.png](02-03-create-wb.png)

* Make sure to fill in the following settings:  
    * Choose a name, for example: `My Workbench`  
    * Select the image: `CUSTOM Crazy train lab`  
    * Container size: `Small`  
    * Keep the default storage settings.  
    * At the bottom, check `Use a data connection`.  
    * Scroll down to `Use existing data connection`  
    * Select the `pipelines` Data Connection you created earlier from the list.  
    * It should look like this:  
![02-02-launch-workbench-01.png](02-02-launch-workbench-01.png)  
![02-02-launch-workbench-02.png](02-02-launch-workbench-02.png)

* Click `Create workbench` to confirm and wait for its blue `Starting` status to turn green `Running`.

* Once the Workbench is created, click the `Open` link to connect to it.

![02-03-open-link.png](02-03-open-link.png)

* Authenticate using the same credentials as before.

* You will be asked to accept the following settings:

![02-02-accept.png](02-02-accept.png)

* Click on `Allow selected permissions`.

* You should now see this:

![02-02-jupyter.png](02-02-jupyter.png)

## Clone the Workshop Git Repository

We will clone the content of our Git repository so that you can access all the materials needed to train the AI model.

* Open the tab with the Git icon in the left menu and click `Clone a Repository`:  
![git-clone-1.png](git-clone-1.png)

* Enter the Git repository URL: ``{{< param gitAIRepoUrl >}}``. Also select `Download the repository` and confirm with `Clone`:  
![git-clone-2.png](git-clone-2.png)

At this stage, your Jupyter environment is ready for the work we want to do.
