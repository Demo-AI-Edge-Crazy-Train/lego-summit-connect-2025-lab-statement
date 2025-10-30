+++
title = "Workbench Creation"
draft= false
weight= 3
[[resources]]
  src = '**.png'
+++

## Launch a Workbench

Once the Data Connection and the Pipeline Server have been fully created, you can proceed to create the Workbench, which will serve as the main environment for AI development.

1. Click on the *Workbenches* tab, then click the *Create workbench* button.  
![02-03-create-wb.png](02-03-create-wb.png)

2. Fill in the following settings in the form:  
- **Name**: choose a name, for example `My Workbench`  
- **Image selection**: *CUSTOM Crazy train lab*  
- **Container size**: *Small*  
- **Use a data connection**: check this option, then select *Use existing data connection*. From the dropdown, choose the *pipelines* Data Connection you created earlier.  

The result should look like this:  
![02-02-launch-workbench-01.png](02-02-launch-workbench-01.png)  
![02-02-launch-workbench-02.png](02-02-launch-workbench-02.png)

3. Click *Create workbench* to confirm, and wait for the blue *Starting* status to turn green *Running*.

4. Once the Workbench is created, click the *Open* link to access it.  
![02-03-open-link.png](02-03-open-link.png)

5. Log in using the same credentials as before.

6. You will be prompted to accept some settings. Click *Allow selected permissions*.  
![02-02-accept.png](02-02-accept.png)  

You should now see the following interface:  
![02-02-jupyter.png](02-02-jupyter.png)

## Clone the Git Repository

We will clone the content of our Git repository so that you can access all the materials needed for AI model training.

1. Open the tab with the Git icon in the left menu and click *Clone a Repository*:  
![git-clone-1.png](git-clone-1.png)

2. Enter the Git repository URL: ``{{< param gitAIRepoUrl >}}``. Also check *Download the repository*, then click *Clone*:  
![git-clone-2.png](git-clone-2.png)

At this stage, your Jupyter environment is ready to start working.
