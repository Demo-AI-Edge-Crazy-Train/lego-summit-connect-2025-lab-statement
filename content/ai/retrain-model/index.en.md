+++
title = "Model Training"
draft= false
weight= 4
[[resources]]
  src = '**.png'
+++

In this section, you will:  
- Explore the Python code used to retrain the model.  
- Automate the execution of the different steps using a Pipeline.  
- Visualize the Pipeline and its results in the OpenShift AI dashboard.

⚠️ **WARNING**:  
You will only run the initial steps of model training in the Jupyter development environment.  
The full training will be executed outside of Jupyter via a Pipeline to avoid an **OOM Killed** error (insufficient memory).  
If an error occurs, your pod will be automatically deleted and recreated. Nothing serious, but your development environment will be temporarily unavailable for a few minutes.

## Navigating the Model Training Code

You have previously cloned a Git repository. In the file browser on the left, you should see a folder named after the Git project: *{{< param gitRepoName >}}*.

1. Click on *{{< param gitRepoName >}}* to open the folder. Inside, you will find several items:  
- The Notebook *labeling-extraction.ipynb* retrieves the data annotated with Label Studio, downloading both the images and their corresponding annotations with **bounding boxes**.  
- The Notebook *synthetic-data.ipynb* generates random synthetic data to enrich the training dataset.  
- The Notebook *transfer-learning.ipynb* contains the model training code.  
- The Notebook *comparison.ipynb* compares the base model (which does not recognize the LEGO traffic signs) with the retrained model (which, hopefully, does).  
- The file *traffic-signs.pipeline* is a Pipeline generated with Elyra. **Elyra** provides a graphical interface that allows you to drag and drop Notebooks or Python scripts for each step and connect them to create workflows. You can run this Pipeline in OpenShift AI directly through the Jupyter interface.  
- The folder *inference/* contains materials to query the models after deployment.  
- The folder *utils/* contains utility functions and dependencies for model training.

### Extracting Images and Annotations

1. Click on *labeling-extraction.ipynb* and explore the Notebook content.

2. Run the entire Notebook using the double-arrow icon ▶▶ in the toolbar at the top. Click *Restart* when prompted (see below):  
![run-notebook](run-notebook.png)
![restart-kernel](restart-kernel.png)
You may have noticed that these scripts created a *dataset* directory. This directory contains two subfolders: *images* and *labels*, which hold the images and their corresponding annotations respectively.

3. In the same Notebook, scroll down to the section *Select a random image and display its bounding boxes*. Then, re-run the first cell just below by clicking on it, and then clicking the arrow icon ▶ in the toolbar at the top.  
This cell selects a random image from the *dataset/images* folder and overlays the corresponding **bounding boxes** from *dataset/labels*, i.e. rectangles indicating the coordinates of the objects detected in the image.

### Generating Synthetic Data

1. Open the Notebook *synthetic-data.ipynb*.  
This Notebook generates **synthetic data**, i.e. artificial data used to enrich the model's training dataset.  
To do this, we take photos of the tracks from the train's point of view and randomly overlay cut-out traffic signs, simulating the various real-world conditions the train might encounter.

2. Run the entire Notebook as explained previously. Take time to review the code and observe the visualization examples.

3. You can rerun the visualization step to display other examples of synthetic data.

### Examining the Model Training Step

⚠️ **Do not run this Notebook!** Executing it would crash your environment, as the RAM available for each participant is limited.

Simply open the *transfer-learning.ipynb* Notebook and review the code to understand its functionality.

### Examining the Comparison Step

⚠️ **Do not run this Notebook!** Executing it would crash your environment, as the RAM available for each participant is limited.

Simply open the *comparison.ipynb* Notebook and review the code to understand its functionality.

## Running the Data Science Pipeline

In this step, you will prepare the Data Science Pipeline to run outside of the Jupyter development environment and to use a **GPU** to accelerate model training. In our cluster, a few small shared GPUs have already been deployed and will be used to run this Pipeline.

### Completing the Pipeline

1. Open the Pipeline *traffic-signs.pipeline*.  
You will see the Elyra graphical interface, which allows you to create and run Data Science Pipelines. Our Pipeline was built by dragging and dropping the Notebooks from the file explorer on the left.  
This Pipeline currently has 4 steps and only 2 connections, so there is a missing link between the third step (*transfer-learning*) and the fourth (*comparison*).

2. To create this connection, click on the black dot on the right side of the third step (*transfer-learning*).

3. Hold and drag it to the black dot on the left side of the fourth step (*comparison*).  
You should then have the complete Pipeline as shown below:  
![full-pipeline](full-pipeline.png)

### Examining Step Properties

1. Right-click the second step of the Pipeline (*synthetic-data*).  
2. In the menu, click *Open Properties*. Properties appear in the right panel.  
3. Scroll down to see the main properties:  
- **Runtime Image**: container image used to execute the Python code for this step.  
- **CPU request**: amount of CPU reserved for this step.  
- **RAM limit**: maximum RAM allowed for this step.  
- **Pipeline Parameters**: globally declared Pipeline parameters that can be enabled for this step.  
- **File Dependencies**: files required during execution inside the container. Here, the entire *utils/* directory is required.  
- **Output Files**: files generated during execution, accessible by subsequent steps.  
- **Kubernetes Secrets**: secrets mounted in the container. Here, object storage credentials are available as environment variables during execution.

At the top of the properties panel, you will find three tabs: *Pipeline Properties*, *Pipeline Parameters*, and *Node Properties*. Feel free to explore them.

### Requesting a GPU for the *transfer-learning* Step

1. Close the properties panel of the previous step.  
![close-properties](close-properties.png)

2. Now modify the **third step** of the Pipeline (*transfer-learning*). Do not touch the previous step.  
Right-click the third step (*transfer-learning*) and select *Open Properties*. Properties appear in the right panel.

3. Locate the *GPU* property and enter `1` to request a GPU for model training.  
![full-pipeline-gpu-count](full-pipeline-gpu-count.png)

4. Scroll to the bottom of the configuration panel.  
Nodes with GPUs have **taints**, which by default prevent containers from running on them. To allow this step to use a GPU, add a **toleration**:  
Click *Add* under *Kubernetes Tolerations* and fill in the fields as follows:
- **Key**: `nvidia.com/gpu`  
- **Operator**: *Exists*  
- **Effect**: *NoSchedule*

5. At the end, your configuration should look like this:  
![full-pipeline-toleration](full-pipeline-toleration.png)

### Running the Pipeline

Now it's time to run the Pipeline on OpenShift AI.  

1. Click the *Run Pipeline* button (arrow icon) in the top toolbar:  
![elyra-run](elyra-run.png)

2. If a popup warns that the Pipeline is unsaved, click *Save and Submit*.

3. In the Pipeline configuration, set the value `10` for the *epochs* parameter.  
![elyra-run-config](elyra-run-config.png)  
An **epoch** corresponds to one full pass of the algorithm over the training dataset.  
Choosing the **number of epochs** is crucial for good performance:
- Too few epochs: the model will not have learned enough and will remain ineffective.  
- Too many epochs: the model may **overfit**, meaning it becomes too close to the training data and fails to generalize to new data.

4. After a few moments, a success popup will appear. Click *Run Details* to view the Pipeline execution details.  
![elyra-run-success](elyra-run-success.png)

## Viewing Your Results

### Checking Pipeline Runs

1. **If you missed the shortcut in the Elyra popup**, follow these steps to locate your Pipeline execution info. Otherwise, skip to the next step.  

   1a. Go back to the OpenShift AI dashboard:  
   [https://rhods-dashboard-redhat-ods-applications.apps.{{< param openshift_domain >}}](https://rhods-dashboard-redhat-ods-applications.apps.{{< param openshift_domain >}})

   1b. In the left menu, click *Experiments*, then *Experiments and runs*.

2. Select the experiment associated with your Pipeline.  
   If you kept the default name, it is called *traffic-signs* and appears first.  
   ![experiments-and-runs](experiments-and-runs.png)

3. Click the current run to view the execution status. It usually appears first in the list, with the same name as the Pipeline plus a number.

4. Clicking a Pipeline step opens a side panel on the right showing details, including *logs* in the *Logs* tab.

5. Select *Main* from the dropdown to see the logs from the main container for that step.  
![pipeline-run-logs](pipeline-run-logs.png)

6. Wait until all Pipeline steps are complete and marked in green.  
You should get a result similar to this:  
![pipeline-run-succedded](pipeline-run-succedded.png)

### Retrieving Pipeline Outputs

All Pipeline outputs are saved in **MinIO** object storage.

1. Click this link to the MinIO console: [{{< param minioConsole >}}]({{< param minioConsole >}}).  

2. Log in with the same username assigned at the start of the workshop. The password is `{{< param minioPass >}}`.

3. You should see several buckets. Click the one matching your username:  
   - You will find a *results.csv* file containing metrics from model training, which you can download.  
   - You will also find a folder corresponding to your Pipeline, starting with *traffic-sign*.

4. Open this folder. You will find HTML files, Notebooks (*.ipynb*), and archives.

5. Click the *comparison.html* file. A menu will appear on the right. Click *Download* and open the file locally in your browser.  
Compare the base model results with the new model. In this example, we lost some accuracy on classical traffic signs in the original dataset, but the new model can now detect LEGO signs that were previously unrecognized.
![output-base-model](output-base-model.png)  
![output-new-model](output-new-model.png)
