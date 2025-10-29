---
title: "OpenShift Environment"
weight: 4
---

## OpenShift Cluster

* **OCP Cluster console URL :** `{{< param ocpConsole >}}`

* **OCP Cluster API URL :** `{{< param ocpApi >}}`

There is a dedicated OpenShift user for each of you.
On your table you will find a poster with the relevant information.  
To connect to your OpenShift cluster, [click on this link]({{< param ocpConsole >}}) and fill in your username and password. You will have acces to the Web Terminal by clicking on the **>_** icon on the top right. The Web Terminal provides the *oc* client.

Throughout the lab, please do not use **userX** but the user you have been assigned. 
The username for the MinIO object storage is the same (**userX**), and the password is: **minio123**.

## Red Hat Edge Manager

You also have access to the Red Hat Edge Manager console, which enables you to manage your fleet of Edge devices.

* **Red Hat Edge Manager console URL:** `{{< param flightctlUi >}}`

* **Red Hat Edge Manager API URL:** `{{< param flightctlApi >}}`

To connect to Red Hat Edge Manager, [click on this link]({{< param flightctlUi >}}) and enter your username and password.
