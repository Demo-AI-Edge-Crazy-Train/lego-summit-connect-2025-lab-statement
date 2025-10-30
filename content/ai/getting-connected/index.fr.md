+++
title = "Connexion"
draft= false
weight= 1
[[resources]]
  src = '**.png'
+++

## Informations sur l'environnement

Pour les besoins de cet atelier, nous avons provisionné un seul cluster OpenShift, avec OpenShift AI déployé dessus.  
Chaque participant dispose d'un utilisateur unique pour effectuer son travail.

## Connexion à l'environnement

1. Dans une nouvelle fenêtre ou un nouvel onglet, ouvrez l'URL du tableau de bord OpenShift AI : [https://rhods-dashboard-redhat-ods-applications.apps.{{< param openshift_domain >}}](https://rhods-dashboard-redhat-ods-applications.apps.{{< param openshift_domain >}}).
2. Entrez vos informations d'identification. Le résultat devrait ressembler à ceci :  
![02-01-login1](02-01-login1.png)  
3. Puisque le mot de passe est simple, votre navigateur peut afficher un avertissement :  
![02-01-login-scary](02-01-login-scary.png)  
Vous pouvez ignorer ce message s'il apparaît.  
Après l'authentification, l'affichage devrait ressembler à ceci :  
![02-01-rhoai-front-page](02-01-rhoai-front-page.png)

Si vous êtes arrivé jusque-là, félicitations ! Vous êtes maintenant correctement connecté au tableau de bord OpenShift AI.
