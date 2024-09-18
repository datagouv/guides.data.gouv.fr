# Prendre connaissance et évaluer la qualité de données

Vous avez trouvé le jeu de données qui vous intéresse (cf. "[Trouver des données](trouver-des-donnees.md)") et souhaitez confirmer qu’il correspond bien à votre besoin.

Pour cela, il est possible d'utiliser les méthodes suivantes :

<figure><img src="../../.gitbook/assets/Group 2882.png" alt=""><figcaption></figcaption></figure>

## S’informer sur un jeu de données grâce aux métadonnées et à la documentation

### Consulter les métadonnées

{% hint style="info" %}
Métadonnée : Donnée qui décrit ou définit une autre donnée.
{% endhint %}

Les métadonnées fournissent **les renseignements de base sur les données, le contexte qui permet de comprendre leur nature et ce qu’elles couvrent**.

Sur [data.gouv.fr](http://data.gouv.fr), les principales métadonnées disponibles pour les jeux de données sont les suivantes :

* Titre
* Sigle
* Description
* Licence
* Fréquence de mise à jour
* Mots clés
* Couverture temporelle
* Couverture spatiale
* Granularité spatiale

Grâce aux métadonnées, vous pouvez par exemple savoir et vérifier :

* [ ] Sur quoi porte le jeu de données
* [ ] Qui a produit les données
* [ ] Quand la donnée a été produite
* [ ] Quand les données ont été mises à jour et à quelle fréquence elles sont mises à jour
* [ ] La couverture spatiale des données
* [ ] Comment le jeu de données peut être utilisé (licence)

Sur [data.gouv.fr](http://data.gouv.fr), **les métadonnées sont disponibles sur la page du jeu de données** :

* dans la description principale ;
* dans l’onglet “Informations”.

<figure><img src="../../.gitbook/assets/Sep-16-2024 14-10-54.gif" alt=""><figcaption><p>Trouver les métadonnées d'un jeu de données sur data.gouv.fr</p></figcaption></figure>

{% hint style="success" %}
Pour identifier plus facilement les jeux de données de qualité sur [data.gouv.fr](http://data.gouv.fr), il est possible de se référer **au score de qualité des métadonnées**.\
\
Pour chaque jeu de données, il évalue le remplissage de plusieurs métadonnées (description des données, mise à jour, licence, métadonnées des ressources, couverture spatiale et couverture temporelle) et donne ainsi **une première indication sur la qualité des données**.
{% endhint %}

### Consulter la documentation

Les producteurs de données sont encouragés à associer une documentation aux jeux de données qu’ils publient en open data.

La documentation d’un jeu de données **décrit les données et la structure des fichiers publiés** (par exemple la description des colonnes, la méthode de production des données, etc.). Elle a une visée pédagogique et facilite la réutilisation.

Sur [data.gouv.fr](http://data.gouv.fr), la documentation **est mise à disposition dans l’onglet “Fichiers”, dans la catégorie “Documentation”**.

<figure><img src="../../.gitbook/assets/Sep-16-2024 14-14-19.gif" alt=""><figcaption><p>Trouver la documentation d'un jeu de données sur data.gouv.fr</p></figcaption></figure>

## Evaluer le contenu d’un jeu de données par la prévisualisation

Pour se faire une idée du contenu, de la complétude et de la qualité d’un jeu de données avant de l’exploiter, il est possible de le prévisualiser.

La prévisualisation permet :

* **d’avoir un aperçu des données ;**
* **d’examiner les attributs des données (colonnes, etc.) ;**
* **d’identifier les limites et les manques**.

> Exemple :\
> \- Si vous avez besoin de données couvrant une période particulière, vous pouvez vérifier que les données sur la période sont disponibles.\
> \- Vous pouvez vérifier que les données que vous vous attendiez à trouver dans le fichier y figurent, et que vous comprenez bien les différents libellés.

{% hint style="danger" %}
Cette fonctionnalité n’est pas disponible pour tous les jeux de données. **Elle n’est disponible que pour les jeux de données tabulaires de 100 Mo maximum.**
{% endhint %}

Sur [data.gouv.fr](http://data.gouv.fr), 2 options sont à votre disposition pour prévisualiser les données tabulaires :&#x20;

1. **Prévisualiser directement le fichier sur la page du jeu de données**. Pour cela :&#x20;

* Rendez-vous sur la page du jeu de données ;
* Identifiez le fichier que vous souhaitez prévisualiser ;
* Cliquez dessus ;
* Vous aurez alors accès à la prévisualisation. Vous pouvez visualiser les cinq premières lignes du fichier (avec la possibilité de trier) ;
* Vous pouvez également accéder à des informations sur la structure des données dans l’onglet “Structure des données”.

<figure><img src="../../.gitbook/assets/Sep-16-2024 14-19-08.gif" alt=""><figcaption><p>Prévisualiser un jeu de données directement sur la page du jeu de données</p></figcaption></figure>

2. **Prévisualiser le fichier sur** [**explore.data.gouv.fr**](http://explore.data.gouv.fr)

* Rendez-vous sur la page du jeu de données ;
* Identifiez le fichier que vous souhaitez prévisualiser ;
* Cliquez dessus ;
* Cliquez sur “Explorer les données” ;
* Vous atterrissez sur l’explorateur de données développé par l’équipe de [data.gouv.fr](http://data.gouv.fr).

<figure><img src="../../.gitbook/assets/Sep-16-2024 14-21-11.gif" alt=""><figcaption><p>Prévisualiser un jeu de données sur explore.data.gouv.fr</p></figcaption></figure>

## Consulter les retours des autres réutilisateurs dans les discussions

Sur [data.gouv.fr](http://data.gouv.fr), les réutilisateurs peuvent échanger avec les producteurs de données pour notamment :

* leur poser des questions sur les données ;
* faire des retours sur la qualité des données.

Ces questions et retours peuvent donner des indications sur la qualité des données et les limites déjà identifiées. Sur [data.gouv.fr](http://data.gouv.fr), vous pouvez les consulter dans l’onglet “Discussions” du jeu de données.

<figure><img src="../../.gitbook/assets/Sep-16-2024 14-23-42.gif" alt=""><figcaption><p>Accéder aux discussions d'un jeu de données sur data.gouv.fr</p></figcaption></figure>

{% hint style="success" %}
Il est possible que d’autres réutilisateurs de données aient déjà identifié des problèmes de qualité sur les données, décidé de les retraiter et de publier leurs travaux sur [data.gouv.fr](http://data.gouv.fr). Vous pouvez alors retrouver ces données retravaillées dans l’onglet **“Ressources communautaires”** du jeu de données.
{% endhint %}

## Evaluer l’intérêt d’un jeu de données par sa popularité

Pour identifier les bons jeux de données, et notamment ceux qui font référence sur un sujet spécifique, la dimension communautaire peut s’avérer importante. Pour sonder la popularité d’un jeu de données, **vous pouvez en consulter l’activité**.

Sur [data.gouv.fr](http://data.gouv.fr), ces statistiques sont disponibles sur les pages de jeu de données, dans l’onglet “Informations” dans la catégorie “Statistiques des 12 derniers mois”. [Pour en savoir plus](../../guide-data.gouv.fr/statistiques.md).

<figure><img src="../../.gitbook/assets/Sep-16-2024 14-25-49.gif" alt=""><figcaption><p>Consulter les statistiques des jeux de données sur data.gouv.fr</p></figcaption></figure>

## Ressources externes pour aller plus loin

* [Cours Open Data : Accès au terrain et repérages - Cerema Med (Mathieu Rajerison)](https://datagistips.github.io/cours-data-ente/presentations/session2/session2\_2\_acceder\_prendre\_connaissance.html#1)
* D’autres outils pour prévisualiser des données tabulaires :
  * [CSV Lint](https://csvlint.io/) : permet de téléverser un fichier pour prendre connaissance de ses colonnes et valeurs
  * [WTFcsv](https://databasic.io/en/wtfcsv/) : permet de prendre connaissance du contenu des données.
