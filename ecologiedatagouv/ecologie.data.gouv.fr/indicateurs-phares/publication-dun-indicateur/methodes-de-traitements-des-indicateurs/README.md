---
description: >-
  Description des méthodes de traitements appliqués aux indicateurs avant de les
  partager
---

# Méthodes de Traitements des indicateurs

Le développement des indicateurs territoriaux s’inscrit dans une volonté croissante d'améliorer l’évaluation et la gestion des politiques publiques locales. Et il est essentiel de disposer de données **fiables**, **harmonisées** et **comparables** entre les différentes entités territoriales. Toutefois, l'hétérogénéité des sources de données mises à disposition en Open Data rendent cette tâche complexe.

Afin de pouvoir fournir des fichiers d'indicateurs de qualité, standardisés et facilement réexploitables nous avons

* créé un ensemble de **tables de références**
* défini un ensemble de **transformations de données** appliquées à l'ensemble des indicateurs
* Mis en place des **tests de qualité** tout au long de la chaîne de traitement&#x20;

### Mise à jour des indicateurs

La mise à jour des indicateurs sur [**ecologie.data.gouv.fr**](http://ecologie.data.gouv.fr) repose sur une approche planifiée et adaptée aux contraintes des sources de données. Dans ce cadre, **l’objectif** de cette stratégie est de recenser et décrire nos méthodes de mise à jour, d’établir un calendrier cohérent avec les besoins des utilisateurs et les disponibilités des producteurs, et de prioriser les partenariats pour faciliter l’accès aux données.

La planification des mises à jour s’appuie ainsi sur une compréhension précise des contraintes et des caractéristiques de chaque source. Le temps nécessaire pour actualiser un indicateur dépend, en effet, de plusieurs facteurs :

* **Disponibilité des informations sur la mise à jour** : dates et fréquences, changements méthodologiques, communication du millésime, etc.
* **Découvrabilité et stabilité des nouvelles données** : facilité à trouver la nouvelle version, liens stables, accès fiable, etc.
* **Complexité d’intégration** : modification du schéma de données, adaptation du code, transformations des données nécessaires, etc.

En tenant compte de ces éléments, l’équipe du projet s’engage à réaliser la mise à jour des indicateurs de façon trimestrielle.\
Pour chaque sources d'un indicateurs, l'équipe identifie la date de leur future mise à jour et s'engage à mettre à jour les indicateurs concernés par cette source **avant la fin du trimestre de mise à jour de la source**, sous réserve que toutes les informations nécessaires soient disponibles.

Pour plus de transparence sur l’actualisation de nos indicateurs, un **tableau de bord public** présente le calendrier prévisionnel de leur mise à jour.

👉 **Consulter** [**le tableau de bord des mises à jour**](http://metabase.indicateurs.ecologie.gouv.fr/public/dashboard/909f1e12-2d96-431b-a8e4-619e0e8fe63e)**.**

### **Code source**

Afin d’apporter plus de transparence aux traitements faits avant de publier les indicateurs Territoriaux, nous avons fait le choix d'ouvrir publiquement notre code source.

Dans ce [dépôt gitlab public](https://gitlab-forge.din.developpement-durable.gouv.fr/pub/ecolab/indicateurs-territoriaux-de-transition-ecologique/hub-indicateurs-territoriaux), vous trouverez le code utilisé pour:

* **Extraire** les sources de données utilisées pour calculer les indicateurs (en python),
* **Transformer** les données en indicateurs (en dbt),
* **Publier** ces indicateurs sur notre API (CubeJS),
* **Publier** ces indicateurs sur [ecologie.data.gouv.fr](http://ecologie.data.gouv.fr),
* **Orchestrer** les différents scripts (Airflow).

Ce dépôt est un “**miroir public”** du dépôt de développement privé interne à l’Ecolab. Les modifications de codes sont effectuées dans le dépôt interne. Elles sont restreintes à l’équipe et sont synchronisées automatiquement vers ce dépôt public.

Vous pouvez vous référer aux différents fichiers README.MD pour comprendre comment naviguer dans le dépôt.
