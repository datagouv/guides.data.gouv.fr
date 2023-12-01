---
description: Consultez et téléchargez les statistiques de vos publications
---

# 🆕 Statistiques

Comment accéder aux statistiques sur data.gouv.fr.\
\
VIDEO TUTORIEL&#x20;

{% tabs %}
{% tab title="Organisations" %}
Vous trouverez les statistiques dans l’onglet "Informations".

Les statistiques suivantes sont affichées sur l’année en cours et elles sont mises à jour quotidiennement :

* Des statistiques générales
  * Nombre de jeux de données publiés par l’organisation
  * Nombre de réutilisations publiées par l’organisation
* Des statistiques sur les jeux de données de l'organisation
  * Nombre de visites sur l’ensemble des jeux de données
  * Nombre total de téléchargements des ressources
  * Nombre de réutilisations référencées sur les jeux de données de l’organisation
  * Nombre d’utilisateurs ayant placé des jeux de données de l’organisation parmi leur favoris
* Des statistiques sur les réutilisations publiées par l’organisation
  * Nombre de visites sur l’ensemble des réutilisations publiées par l’organisation
  * Nombre d’utilisateurs ayant placé des réutilisations de l’organisation parmi leur favoris

Pour chacune des statistiques :

* Un graphique donne une idée générale de l’évolution sur l’année
* Une indication de la variation sur le mois en cours est fournie

Il est possible de télécharger les statistiques au format csv (tabulaire). Celles-ci sont disponibles avec les colonnes suivantes :

| Nom de la colonne             | Description                                                                                          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------- |
| _\_\_id_                      | Identifiant technique                                                                                |
| _organization\_id_            | Identifiant de l’organisation                                                                        |
| _metric\_month_               | Mois durant lequel la mesure a été effectuée                                                         |
| _monthly\_visit\_dataset_     | Nombre de visites sur l’ensemble des jeux de données sur le mois en question                         |
| _monthly\_download\_resource_ | Nombre de téléchargements sur l’ensemble des fichiers sur le mois en question (manuel et automatisé) |
| _monthly\_visit\_reuse_       | Nombre de visites sur l’ensemble des réutilisations sur le mois en question                          |



Exemple avec [l’organisation du Ministère de l'Intérieur et des Outre-Mer](https://www.data.gouv.fr/fr/organizations/ministere-de-linterieur-et-des-outre-mer/#/information) au 1er décembre 2023&#x20;

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

**IMAGE**

* Statistiques générales
  * 681 jeux de données
  * 3 réutilisations
* Statistiques des jeux de données
  * 1,5 millions de visites de x à x
    * Dont
* xxxx téléchargements de x à x
* xxxx réutilisations référencées sur les jeux de données de l’organisation
* xxxx favoris sur les jeux de données
* Statistiques des réutilisations
  * x visites
  * x favoris

{% hint style="info" %}
Si vous souhaitez accéder au détail des statistiques sur l’ensemble de vos jeux de données, vous pouvez [télécharger votre catalogue](organisation/suivre-lactivite-et-modifier-son-organisation.md#comment-telecharger-et-explorer-le-catalogue-de-donnees-dune-organisation). Vous aurez alors accès aux statistiques consolidées depuis juillet 2022.
{% endhint %}
{% endtab %}

{% tab title="Jeux de données" %}
Vous trouverez les statistiques dans l’onglet "Informations".

Les statistiques suivantes sont affichées sur l’année en cours et elles sont mises à jour quotidiennement :

* Nombre de visites
* Nombre de téléchargements (manuel et automatisé) des fichiers et ressources
* Nombre de réutilisations référencées sur ce jeu de données
* Nombre d’utilisateurs ayant placé ce jeu de données parmi leurs favoris

Pour chacune des statistiques :

* Un graphique donne une idée générale de l’évolution sur l’année
* une indication de la variation sur le mois en cours est fournie

Il est possible de télécharger les statistiques au format csv (tabulaire). Celles-ci sont disponibles avec les colonnes suivantes :

| Nom de la colonne | Description                                  |
| ----------------- | -------------------------------------------- |
| _\_\_id_          | Identifiant technique                        |
| _reuse\_id_       | Identifiant de la réutilisation              |
| _metric\_month_   | Mois durant lequel la mesure a été effectuée |
| _monthly\_visit_  | Nombre de visites sur le mois en question    |

**IMAGE**

Exemple avec le jeu de données X au mois de novembre 2023 :&#x20;

* xxxx visites de x à x
  * Dont
* xxxx téléchargements de x à x
  * Dont
* xxxx réutilisations référencées
  * Dont
* xxxx favoris
{% endtab %}

{% tab title="Réutilisations" %}
Vous trouverez les statistiques en dessous de la liste des jeux de données associés à la réutilisation.

Les statistiques suivantes sont affichées sur l’année en cours et elles sont mises à jour quotidiennement :

* Nombre de visites
* Nombre d’utilisateurs ayant placé cette réutilisation parmi leurs favoris

Pour chacune des statistiques :

* Un graphique donne une idée générale de l’évolution sur l’année
* Une indication de la variation sur le mois en cours est fournie

Il est possible de télécharger les statistiques au format csv (tabulaire). Celles-ci sont disponibles avec les colonnes suivantes :&#x20;

| Nom de la colonne | Description                                  |
| ----------------- | -------------------------------------------- |
| _\_\_id_          | Identifiant technique                        |
| _reuse\_id_       | Identifiant de la réutilisation              |
| _metric\_month_   | Mois durant lequel la mesure a été effectuée |
| _monthly\_visit_  | Nombre de visites sur le mois en question    |

**IMAGE**

Exemple avec la réutilisation X au mois de novembre 2023 :&#x20;

* xxxx visites de x à x
  * Dont
* xxxx téléchargements de x à x
* xxxx réutilisations référencées
* xxxx favoris
{% endtab %}

{% tab title="Plateforme data.gouv.fr" %}
Un [tableau de bord](https://www.data.gouv.fr/fr/dashboard/) sur l’ensemble de [data.gouv.fr](http://data.gouv.fr/) est également disponible. Celui-ci présente les statistiques de la plateforme sur l’année en cours, elles sont mise à jour quotidiennement.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

