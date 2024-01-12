# Comprendre les limites du moissonnage

{% hint style="warning" %}
Le moissonnage n’a aucune connaissance de l’usage que vous faites du modèle de données. Il s’appuie uniquement sur les spécifications de chaque protocole ou plateforme pour récupérer les informations. Il y a donc certaines limitations techniques liées aux spécificités de chaque plateforme. Certaines limitations sont communes et détaillées ci-dessous.
{% endhint %}

## Correspondances des métadonnées <a href="#correspondances-des-metadonnees" id="correspondances-des-metadonnees"></a>

Certains champs du modèle de data.gouv.fr possèdent un équivalent qui peut être sous spécifié dans certains protocoles ou sur certaines plateformes, ou bien alors être spécifié différemment, sur plusieurs champs. Dans ce cas, la valeur du champ est récupérée en “best effort’, c’est-à-dire qu’elle va être devinée en fonction des éléments à disposition. Se référer à la page de chaque moissonneur pour savoir lesquels sont dans ce cas pour chaque implémentation.

## Suppression à la source et archivage <a href="#suppression-a-la-source" id="suppression-a-la-source"></a>

Lors d'une suppression à la source (un ou plusieurs jeux de données qui ne sont plus présents sur la plateforme moissonnée), data.gouv.fr conserve les jeux de données sur sa plateforme. Le but est d'éviter les suppressions en masse par erreur, ce qui entraînerait une perte des statistiques, des discussions et des ressources communautaires de chaque jeu de données.

Au bout d'une période de 7 jours, ils sont marqués comme archivés. L'archivage des jeux de données implique qu'ils ne soient plus indexés ou visibles dans les statistiques des producteurs, mais bien accessibles par lien direct pour les utilisateurs qui souhaiteraient continuer à y accéder.

Dans le cas d’une suppression ponctuelle, nous vous invitons à supprimer manuellement le jeu de données moissonné qui a perdu sa source.&#x20;

Dans le cas d’une suppression massive de jeu de données, veuillez nous contacter afin de trouver une solution satisfaisante.

## Changement d’identifiant <a href="#changement-didentifiant" id="changement-didentifiant"></a>

Les moissonneurs utilisent les identifiants de jeu de données distants pour retrouver leurs données entre deux moissonnages. Il est donc important de veiller à ce qu’un jeu de données conserve son identifiant au fil du temps et des modification successives. Dans le cas contraire, cela donnera lieu à la création d’un doublon.

Il faut donc aussi veiller à ne pas supprimer puis recréer un jeu de données ou une ressource pour faire sa mise à jour.
