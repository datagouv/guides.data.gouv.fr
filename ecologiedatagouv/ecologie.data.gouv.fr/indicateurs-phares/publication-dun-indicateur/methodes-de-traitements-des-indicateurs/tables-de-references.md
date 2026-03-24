---
description: >-
  Description de la construction des tables de références utilisées dans
  l'ensemble des indicateurs
---

# Tables de références

Nous avons souhaité disposer d'un ensemble de **tables de références** afin de standardiser les fichiers d'indicateurs pour en faciliter la réutilisation.

Les tables de références utilisées dans la totalité où une partie de nos indicateurs sont les suivantes:

* Un **référentiel géographique** à la maille communale, avec l'ensemble des communes, leur EPCI, département et région associée.
* Un **référentiel de population** à la maille communale
* Un **référentiel de surface** à la maille communale
* Une **table de passage**, permettant de passer d'un millésime géographique d'une commune à un autre

### Le référentiel géographique&#x20;

#### **Contexte**&#x20;

* Chaque indicateur publié est associé à des métadonnées géographiques standardisées et de qualité correspondant à ou aux mailles géographiques auxquels l'indicateur est publié
* Afin de garantir une homogénéité&#x20;

#### **Source**

Pour construire notre référentiel géographique nous utilisons la source des [Code officiel géographique au 1er janvier 2025 | Insee](https://www.insee.fr/fr/information/8377162)

<details>

<summary>Les communes métropolitaines</summary>

**Contenu**

Le jeu de données des **communes depuis 1943 à 2025** (42 314 lignes) : Liste de tous les couples code-libellé de commune ou d’arrondissement municipal ayant existé depuis 1943 avec la période durant laquelle le code correspondait au libellé.

Le jeu de données contient :

* la liste des codes commune
* la liste des libellés commune
* la date de début/création de la commune (1943 pour celles crées avant)
* la date de fin de la commune (nulle pour les communes n’ayant pas subi de fusion/scission)

**Nettoyage**

* Union des tables d’appartenance et de celles des arrondissement de chaque année
* Ordre des codes communes dans l’ordre décroissant de leur année de millésime
* Conservation des codes géographiques (com, dpt, reg, epci) les plus récents pour chaque commune

On obtient la table de toutes les communes uniques existantes et ayant existées depuis 2008.

</details>

<details>

<summary>Les communes d’outre-mer</summary>

**Contenu**

Le jeu de données des **communes d’outre-mer au millésime 2025** (95 lignes) : Liste des collectivités et territoires français d’outre-mer au 1er janvier 2025

Le jeu de données contient :

* la liste des codes commune
* la liste des libellés commune
* la liste des codes département
* la liste des libelles département

**Nettoyage**

Le nettoyage de la table des communes d’outre mer consiste simplement en :

* Imputer `'SO'` comme valeur de code epci et de libellé epci
* Imputer `‘0’` comme valeur de code région
* Imputer `'Collectivités d''outre-mer'` comme libellé region
* Imputer `‘2025’` comme année de millésime

</details>

<details>

<summary>Les EPCI</summary>

**Source**

[Intercommunalité | Insee](https://www.insee.fr/fr/information/2510634)

**Contenu**

Les établissements publics de coopération intercommunale (EPCI) sont des regroupements de communes ayant pour objet l'élaboration de « projets communs de développement au sein de périmètres de solidarité ». Ils sont soumis à des règles communes, homogènes et comparables à celles de collectivités locales.

* Tous les Excels depuis 2012 ont été récupérés (pour avoir un historique des codes-libellés EPCI)
*   Les jeux de données utilisés sont ceux de la sheet “EPCI” de l’Excel

    Chaque jeu de données contient :

    * la liste des codes EPCI
    * la liste des libellés EPCI

**Nettoyage**

* Union des tables d'EPCI de chaque année
* Ordre des EPCIs dans l’ordre décroissant de leur année de millésime
* Conservation des codes géographiques (com, dpt, reg, epci) les plus récents pour chaque EPCI

On obtient la table de toutes les EPCI uniques existantes et ayant existées depuis 2012.

</details>

<details>

<summary>Les départements</summary>

**Contenu**

Le jeu de données des **départements au millésime 2025** (101 lignes)

Le jeu de données contient :

* la liste des codes département
* la liste des libelles département

**Nettoyage**

Le nettoyage de la table des départements consiste simplement à changer le type du champ des codes régions en texte et d’ajouter un 0 avant les codes inférieurs à 10

```sql
select
    dep as geocode_departement
    , libelle as libelle_departement
    , lpad(reg::text, 2, '0') as geocode_region
from {{ source('extract__insee__code_geo_dep', 'departements') }}
```

</details>

<details>

<summary>Les régions</summary>

**Contenu**

Le jeu de données des **régions au millésime 2025** (18 lignes)

Le jeu de données contient :

* la liste des codes régions
* la liste des libelles régions

**Nettoyage**

Le nettoyage de la table des régionsconsiste simplement à changer le type du champ des codes régions en texte et d’ajouter un 0 avant les codes inférieurs à 10

```sql
select
    lpad(reg::text, 2, '0') as geocode_region
    , libelle as libelle_region
from {{ source('extract__insee__code_geo_reg', 'regions') }}
```

</details>

### La table de passage d'un COG au plus récent

#### **Contexte**&#x20;

* Il a été décidé que les indicateurs seraient publiés en suivant le **Code Officiel Géographique (COG) le plus récent (2025 aujourd'hui)**
* La plupart des sources de données utilisées aujourd’hui n’utilisent pas le COG le plus récent. Il faut donc dans chaque cas trouver un moyen de passer de l'ancien code au plus récent, en tenant de compte de la diversité des sources (format, millésime du COG, etc.)
* C'est pourquoi nous avons créer une table de passage qui nous permet de passer d'un COG à un autre facilement.

#### **Source**

Pour construire ce référentiel, nous nous basons sur la [Table d’appartenance géographique des communes ](https://www.insee.fr/fr/information/7671844) de l'INSEE.

#### **Construction**

La **table d’appartenance géographique** est un fichier fourni pour toutes les communes et le code géographique des niveaux géographiques supérieurs auxquels elles appartiennent (région, département, arrondissement, canton ville, zone d'emploi, bassin de vie, unité urbaine, aire d'attraction des villes).

* Tous les Excels depuis 2008 ont été récupérés (pour avoir un historique des communes et de leur appartenance la plus ancienne possible)
* Les jeux de données utilisés pour les communes sont ceux des sheets “COM”
*   Pour les arrondissements, le jeu de données de la sheet “ARM” de l’Excel 2025 a été récupéré (afin d’avoir également l’appartenance géo des arrondissements)

    Chaque jeu de données contient :

    * la liste des codes communes
    * la liste des codes départements
    * la liste des codes régions
    * la liste des codes EPCIs

{% hint style="info" %}
_Pour les arrondissements, seul le jeu de données de 2025 a été utilisé car ils n’ont pas subi de changement notable depuis leur création_
{% endhint %}

### Le référentiel de population

#### **Contexte**&#x20;

Plusieurs indicateurs sont disponibles tels quels ainsi que rapportés au nombre d'habitants. Nous avons souhaité avoir un référentiel unique pour faire la division de l'indicateur par le nombre d'habitants, afin d'avoir des informations cohérentes quel que soit l'indicateur calculé.

#### Source

Pour construire ce référentiel, nous nous basons sur[ Historique des populations communales Recensements de la population 1876-2022](https://www.insee.fr/fr/statistiques/3698339) de l'INSEE.

Cette base fournit les données de populations de 1876 à 2022 pour les communes de France continentale, de 1936 à 2022 pour les communes de Corse et de 1954 ou 1962 à 2022 pour les communes des DOM (hors Mayotte).

{% hint style="info" %}
Les résultats des recensements depuis 2006 ne se comparent correctement entre eux que sur des périodes espacées d’au moins 5 ans.
{% endhint %}

{% hint style="info" %}
En raison du report de l’enquête annuelle 2021 (sauf à Mayotte) lié à la situation sanitaire de la Covid-19, les résultats des millésimes 2019 à 2023 doivent exceptionnellement être comparés avec ceux de millésimes antérieurs distants d’au moins 6 ans.
{% endhint %}

Les données sont diffusées à la maille communale selon la géographie en vigueur au **1er janvier 2024** et nous les convertissons au dernier millésime grasse à notre table de passage.

Chaque année, la table est mise à jour. Un nouveau champ est créé et renseigné avec les données du dernier recensement de la population municipale.&#x20;

### Le référentiel de surface

#### **Contexte**&#x20;

Plusieurs indicateurs sont disponibles tels quels ainsi que rapportés à la surface. Nous avons souhaité avoir un référentiel unique pour faire la division de l'indicateur par la surface de la commune, afin d'avoir des informations cohérentes quel que soit l'indicateur calculé

#### Source

Pour construire ce référentiel, nous nous basons sur le [Découpage administratif communal français issu d'OpenStreetMap](https://www.data.gouv.fr/datasets/decoupage-administratif-communal-francais-issu-d-openstreetmap/).

{% hint style="info" %}
Les données proviennent de la base de données cartographiques OpenStreetMap.\
Celles-ci ont été constituées à partir du cadastre mis à disposition par la DGFiP sur cadastre.gouv.fr.\
En complément sur Mayotte où le cadastre n'est pas disponible sur cadastre.gouv.fr, ce sont les limites du GEOFLA de l'IGN qui ont été utilisées ainsi que le tracé des côtes à partir des images aériennes de Bing.
{% endhint %}
