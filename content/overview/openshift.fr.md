---
title: "Environnement OpenShift"
weight: 4
---

## Cluster OpenShift

⚠️ Chaque participant dispose d’un **utilisateur OpenShift dédié**. L’animateur de l’atelier vous fournira les informations nécessaires. Tout au long de l’atelier, veuillez utiliser le nom d’utilisateur qui vous a été attribué à la place de *userX*. ⚠️

* **URL de la console du cluster OCP :** [{{< param ocpConsole >}}]({{< param ocpConsole >}})

* **URL de l'API du cluster OCP :** `{{< param ocpApi >}}`

Pour vous connecter à votre cluster OpenShift, rendez-vous sur l’URL de la console et saisissez votre nom d’utilisateur et votre mot de passe sous l’authentification `WorkshopUser`.  
Vous pouvez accéder au **Terminal Web** en cliquant sur l’icône **>_** dans le coin supérieur droit. Le Terminal Web vous donne accès au client *oc*.  
Le nom d’utilisateur pour le **stockage objet MinIO** est le même (*userX*), et le mot de passe est `{{< param minioPass >}}`.

## Red Hat Edge Manager

Vous avez également accès à la console Red Hat Edge Manager qui vous permettra de gérer votre flotte de périphériques Edge.

* **URL de la console Red Hat Edge Manager :** `{{< param flightctlUi >}}`

* **URL de l'API Red Hat Edge Manager :** `{{< param flightctlApi >}}`

Pour vous connecter à Red Hat Edge Manager, rendez-vous sur l’URL de la console et saisissez votre nom d’utilisateur et votre mot de passe.

