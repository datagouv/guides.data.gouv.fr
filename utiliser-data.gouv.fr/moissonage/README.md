# Moissonage

### Rapport de moissonnage <a href="#rapport-de-moissonnage" id="rapport-de-moissonnage"></a>

Chaque moissonnage donne lieu à un rapport accessible depuis l’[interface d’administration de data.gouv.fr](https://www.data.gouv.fr/admin/).

Il vous permet de comprendre ce qu’il se passe et, le cas échéant, de corriger les erreurs existantes. Il vous permettra aussi de vérifier que le filtrage se fait bien si vous en avez saisi un.

#### Vue synthétique <a href="#vue-synthetique" id="vue-synthetique"></a>

![Vue synthétique du rapport de moissonnage](https://doc.data.gouv.fr/img/moissonnage/admin-harvest-summary.png)

#### Détails d’un jeu de données <a href="#details-dun-jeu-de-donnees" id="details-dun-jeu-de-donnees"></a>

![Détails d'un jeu de données du rapport de moissonnage](https://doc.data.gouv.fr/img/moissonnage/admin-harvest-dataset-modal.png)

#### En cas d’erreur <a href="#en-cas-derreur" id="en-cas-derreur"></a>

![Erreur sur un jeu de données du rapport de moissonnage](https://doc.data.gouv.fr/img/moissonnage/admin-harvest-dataset-error-modal.png)

* **1** correspond à l’erreur **technique** formulée de façon compréhensible pour un humain
* **2** contient la “**stacktrace**” de l’erreur qui servira à ceux qui développent des moissonneurs ou contribuent aux existants.

### Limites <a href="#limites" id="limites"></a>

Le moissonnage n’a aucune connaissance de l’usage que vous faites du modèle de données. Il s’appuie uniquement sur les spécifications de chaque protocole ou plateforme pour récupérer les informations.

Il y a donc certaines limitations techniques liées aux spécificités de chaque plateforme (décrites sur la page de chaque moissonneur).

Certaines limitations sont communes et détaillées ci-dessous.

#### Correspondances des métadonnées <a href="#correspondances-des-metadonnees" id="correspondances-des-metadonnees"></a>

Certains champs du modèle de data.gouv.fr possèdent un équivalent qui peut être sous-spécifis dans certains protocoles ou sur certaines plateformes, ou bien alors être spécifié différement, sur plusieurs champs… Dans ce cas, la valeur du champ est récupérée en “best effort’, c’est-à-dire qu’elle va être devinée en fonction des élements à disposition. Se référer à la page de chaque moissonneur pour savoir lesquels sont dans ce cas pour chaque implémentation.

#### Suppression à la source <a href="#suppression-a-la-source" id="suppression-a-la-source"></a>

Pour le moment, les moissonneurs ne gèrent pas la suppression à la source et ce pour éviter les suppressions en masse par erreur, ce qui entrainerait une perte des statistiques, des discussions et des ressources communautaires de chaque jeu de données.

Dans le cas d’une suppression ponctuelle, nous vous invitons à supprimer manuellement le jeu de données moissonné qui a perdu sa source.

Dans le cas d’une suppression massive de jeu de données, veuillez nous contacter afin de trouver une solution satisfaisante.

#### Changement d’identifiant <a href="#changement-didentifiant" id="changement-didentifiant"></a>

Les moissonneurs utilisent les identifiants de jeu de données distants pour retrouver leurs données entre deux moissonnages. Il est donc important de veiller à ce qu’un jeu de données conserve son identifiant au fil du temps et des modification successives. Dans le cas contraire, cela donnera lieu à la création d’un doublon.

Il faut donc aussi veiller à ne pas supprimer puis recréer un jeu de données ou une ressource pour faire sa mise à jour.
