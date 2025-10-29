---
title: "Environnement OpenShift"
weight: 4
---

## Cluster OpenShift

* **URL de la console du cluster OCP :** `{{< param ocpConsole >}}`

* **URL de l'API du cluster OCP :** `{{< param ocpApi >}}`

Un utilisateur OpenShift dédié est créé pour chacun d'entre vous.
Vous trouverez sur votre table une affiche reprenant toutes les informations de connexion (identifiant et mot de passe).
Pour vous connecter à votre cluster Openshift, [cliquez sur ce lien]({{< param ocpConsole >}}) et renseignez votre nom d'utilisateur et votre mot de passe. Vous aurez accès au *Terminal Web* en cliquant sur l'icône **>_** en haut à droite. Le Terminal Web fournit le client *oc*.

Tout au long du lab, merci de ne pas utiliser **userX** mais l'utilisateur qu'on vous a attribué. 
L'utilisateur du stockage objet (**Minio**) est le même que celui décrit ci-dessus, le mot de passe est : **minio123**.

## Red Hat Edge Manager

Vous avez également accès à la console Red Hat Edge Manager qui vous permettra de gérer votre flotte de devices Edge.

* **URL de la console Red Hat Edge Manager :** `{{< param flightctlUi >}}`

* **URL de l'API Red Hat Edge Manager :** `{{< param flightctlApi >}}`

Pour vous connecter à Red Hat Edge Manager, [cliquez sur ce lien]({{< param flightctlUi >}}) et renseignez votre nom d'utilisateur et votre mot de passe.

