# Evaluer le niveau de qualité d'un jeu de données

## Définir la qualité d'un jeu de données

Pour une donnée, **la notion de qualité dépend grandement de l'usage qui en est fait**.&#x20;

Les jeux de données publiés sont généralement produits dans un contexte propre à un processus métier et pour un usage particulier. Cet environnement métier n'est pas toujours familier aux tiers, qu'ils soient internes ou externes à l'organisation.&#x20;

> Exemple : [La _base de données des demandes de valeur foncière_](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres/) est historiquement produite par la Direction générale des finances publiques pour tenir un fichier immobilier et collecter l'impôt.

Les réutilisateurs peuvent alors rencontrer des difficultés lorsqu'ils souhaitent s'approprier des données ouvertes :&#x20;

* **Difficultés dans la compréhension de la structure du jeu de données** ;
* **Difficultés dans la compréhension des données elles-mêmes** ;&#x20;
* **Qualité non adaptée aux usages voulus** (mise à jour, documentation insuffisante ou inexacte, etc.).

Il est donc indispensable de **prendre en compte les pratiques des réutilisateurs** en amont de la production des jeux de données.&#x20;

## Evaluer le niveau de qualité d'un jeu de données

Plusieurs critères permettent d'évaluer le niveau de qualité d'un jeu de données, notamment :&#x20;

<details>

<summary><strong>Des éléments sur les données elles-mêmes et leur structure</strong></summary>

* **Le format de fichier,** qui doit permettre de facilement récupérer les données pour les réutiliser de la manière souhaitée (CSV, JSON plutôt que des formats propriétaires comme Excel) ;
* **La structure du fichier**, avec notamment des propriétés au nom explicite, compréhensible rapidement et interprétable facilement par des machines ;&#x20;
* **Le contenu**, qui doit être le plus épuré possible, avec un type de donnée simple (un nombre, un pourcentage, une chaîne de caractère, une date, etc.) et un sens "métier" le plus clair possible.&#x20;

</details>

<details>

<summary><strong>Des éléments attestant du potentiel de réutilisation et de croisement des données</strong></summary>

* **Le respect de standards**, référentiels et schémas déjà établis ;
* **La présence de données et colonnes pivots** pour lier les données à un référentiel (par exemple le SIRET).

</details>

<details>

<summary><strong>Des éléments qui accompagnent les données</strong></summary>

* **Une documentation** claire et rigoureuse avec des métadonnées sur le format du fichier, les versions et les référentiels ;
* **La gestion des versions et des mises à jour des données** ;
* **Des échanges entre producteurs et réutilisateurs du jeu de données** avec si possible des mécanismes de contribution aux données.

</details>
