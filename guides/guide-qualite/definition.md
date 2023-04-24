# Définition

{% hint style="info" %}
La qualité des données est un élément essentiel du succès de l'open data : l'ouverture de données n'entraîne pas directement leur réutilisation. Ainsi, il a été constaté que seuls certains jeux de données publiés sur data.gouv.fr étaient régulièrement réutilisés.
{% endhint %}

## Comment définir la qualité d'un jeu de données ?

Pour une donnée, la notion de qualité dépend grandement de l'usage qui en est fait.&#x20;

Les jeux de données publiés sont généralement produits dans un contexte propre à un processus métier et pour un usage particulier. A titre d'exemple, la _base de données des demandes de valeur foncière_ est historiquement produite par la Direction générale des finances publiques pour tenir un fichier immobilier et collecter l'impôt. Cet environnement métier n'est pas toujours familier aux tiers, qu'ils soient internes ou externes à l'organisation.&#x20;

Les réutilisateurs peuvent alors rencontrer des difficultés lorsqu'ils souhaitent s'approprier des données ouvertes :&#x20;

* Difficultés dans la compréhension de la structure du jeu de données ;
* Difficultés dans la compréhension des données elles-mêmes ;&#x20;
* Qualité non adaptée à leurs usages (mise à jour, documentation insuffisante ou inexacte, etc.).

Il est donc indispensable de prendre en compte les pratiques des réutilisateurs en amont de la production des jeux de données. Pour ce faire, une réflexion sur leur structure, sur le format des fichiers ou encore sur la documentation doit être menée systématiquement. Cette réflexion facilitera l'appropriation des données par les tiers et fera gagner du temps à l'organisation productrice, qui n'aura plus à répondre à de nombreuses questions. &#x20;

## Comment évaluer le niveau de qualité d'un jeu de données ?

Plusieurs critères permettent d'évaluer le niveau de qualité d'un jeu de données, notamment :&#x20;

1. **Des éléments sur les données elles-mêmes et leur structure**&#x20;

* Le format de fichier, qui doit permettre de facilement récupérer les données pour les réutiliser de la manière souhaitée (CSV, JSON plutôt que des formats propriétaires comme Excel par exemple) ;
* La structure du fichier, avec notamment le nom des propriétés explicite, compréhensible rapidement et interprétable facilement par des machines ;&#x20;
* Le contenu, qui doit être le plus épuré possible, avec un type de donnée simple (un nombre, un pourcentagne, une chaîne de caractère, une date, etc.) et un sens "métier" le plus clair possible.&#x20;

2. **Des éléments attestant du potentiel de réutilisation et de croisement des données**&#x20;

* Le respect de standards, référentiels et schémas déjà établis
* La présence de données et colonnes pivots pour lier les données à un référentiel (i.e. code SIRET ou SIREN)

3. **Des éléments qui accompagnent les données**

* Une documentation claire et rigoureuse avec des métadonnées sur le format du fichier, les versions et les référentiels ;
* La gestion des versions et des mises à jour des données ;
* Des échanges entre producteurs et réutilisateurs du jeu de données avec si possible des mécanismes de contribution aux données
