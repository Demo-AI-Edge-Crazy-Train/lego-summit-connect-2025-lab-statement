---
title: "OpenShift Environment"
weight: 4
---

## OpenShift Cluster

⚠️ There is a **dedicated OpenShift user** for each of you. The workshop facilitator will provide you with the relevant information. Throughout the lab, please use the username you have been assigned instead of **userX**. ⚠️

* **OCP Cluster console URL :** `{{< param ocpConsole >}}`

* **OCP Cluster API URL :** `{{< param ocpApi >}}`

To connect to your OpenShift cluster, go to the console URL and enter your username and password under the `WorkshopUser` authentication.  
You can access the **Web Terminal** by clicking the **>_** icon in the top-right corner. The Web Terminal gives you access to the *oc* client.  
The username for the **MinIO object storage** is the same (**userX**), and the password is `{{< param minioPass >}}`.

## Red Hat Edge Manager

You also have access to the Red Hat Edge Manager console, which enables you to manage your fleet of Edge devices.

* **Red Hat Edge Manager console URL:** `{{< param flightctlUi >}}`

* **Red Hat Edge Manager API URL:** `{{< param flightctlApi >}}`

To connect to Red Hat Edge Manager, [click on this link]({{< param flightctlUi >}}) and enter your username and password.
