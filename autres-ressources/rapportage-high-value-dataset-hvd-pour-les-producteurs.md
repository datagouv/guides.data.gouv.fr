---
description: Précisions pratiques pour les producteurs de données HVD
---

# 🇪🇺 Rapportage High Value Dataset (HVD) pour les producteurs

Dans le cadre de la mise en place du règlement sur les données de haute valeur (HVD), nous souhaitons apporter des précisions sur le processus de remontée des données et quelles actions à prendre en compte en tant que producteurs. Cet article complète notre précédente publication, [l'essentiel sur les données de forte valeur](https://www.data.gouv.fr/fr/posts/lessentiel-sur-les-donnees-de-forte-valeur/).

### Processus global de remontée des fiches de données

Au niveau des producteurs concernés, le processus de remontée des données HVD suit plusieurs étapes.

1. les données sont identifiées comme étant de hautes valeurs et sont catégorisées dans l’une des 6 grandes catégories faisant l'objet des 6 annexes du règlement (géospatiales, environnementales, etc.). Selon la catégorie associée, les contraintes de mise à disposition et les métadonnées obligatoires diffèrent. Nous revenons en détail sur ce point dans la section suivante.
2. Ensuite, ces données doivent remonter au niveau national en étant :
   * soit moissonnées (voir [qu’est-ce que le moissonnage](https://guides.data.gouv.fr/publier-des-donnees/guide-data.gouv.fr/moissonnage)) sur [data.gouv.fr](http://data.gouv.fr/) et éventuellement le [geocatalogue](https://www.geocatalogue.fr/) selon leur nature ;
   * soit publiées directement sur [data.gouv.fr](https://www.data.gouv.fr/).
3. Enfin, ces données sont elles-mêmes moissonnées par l’Europe pour proposer un catalogue européen des données de haute valeur.

### Métadonnées obligatoires pour les HVD

A côté des obligations propres aux jeux de données concernés par la directive INSPIRE (voir section suivante), les obligations minimales de description des données pour les HVD sont les suivantes :

* Un identifiant stable dans le temps. Il est préconisé qu’il suive les bonnes pratiques DCAT-AP (ex: une URI déréférençable). Voir le détail dans le cadre HVD : [https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/#c2](https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/#c2).
* Une métadonnée identifiant la donnée comme HVD
  * Proposition [data.gouv.fr](http://data.gouv.fr) : ajout d’un mot clé “**hvd**”
* Une métadonnée identifiant la catégorie HVD à laquelle la donnée appartient
  * Proposition [data.gouv.fr](http://data.gouv.fr) : ajout de l’un des mots clé suivants:
    * **hvd-geospatial**
    * **hvd-earth**
    * **hvd-meteorological**
    * **hvd-statistics**
    * **hvd-companies**
    * **hvd-mobility**
  * Le mapping vers [les codes du référentiel européen](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/high-value-dataset-category) se fait par [data.gouv.fr](http://data.gouv.fr).
* La description de service pour les API
  * Dans le cadre d’une API, une page web de description de la qualité de service de cette API est attendue, il peut par exemple s’agir d’un lien vers un SLA (service-level agreement).
  * Un lien vers la documentation de l’API (dans un format standard pour les machines ou les utilisateurs humains) est aussi fortement recommandée.
* Un point de contact des données ou APIs
  * Il peut prendre la forme d’une adresse mail ou d’un formulaire de contact. Il est obligatoire dans le cas d’APIs mais **optionnel pour les données en téléchargement**.
* Une métadonnée décrivant la licence utilisée (équivalente [licence Creative Commons BY 4.0](https://creativecommons.org/licenses/by/4.0/) ou moins restrictive)
  * identifiant [la licence ouverte Etalab 2.0](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf) (LOv2) ou l’une des [licences supportées sur data.gouv.fr](https://www.data.gouv.fr/api/1/datasets/licenses/). Plus d’info [sur cette page](https://www.data.gouv.fr/fr/pages/legal/licences/) sur les licences utilisables par les administrations.
  * L'URL identifiante à utiliser pour la LOv2 dans le cadre d'un moissonnage est [https://www.etalab.gouv.fr/licence-ouverte-open-licence](https://www.etalab.gouv.fr/licence-ouverte-open-licence).
  * Aujourd’hui, aucune licence en dehors de celles supportées ne sera correctement moissonnée par [data.gouv.fr](http://data.gouv.fr).
  * En l’absence de licence indiquée, le Code des Relations entre le Public et l'Administration précise les [conditions de réutilisations qui s'appliquent](https://www.legifrance.gouv.fr/codes/article\_lc/LEGIARTI000032255220).

### Articulation entre INSPIRE et HVD

Bien que les initiatives INSPIRE et HVD visent toutes deux à améliorer l'accès aux données, elles présentent des différences notables. INSPIRE est un cadre législatif qui vise à établir une infrastructure d'information géographique dans l'Europe pour l'environnement. HVD, en revanche, est un label attribué à des données dont la mise en open data peut générer un impact économique, social et environnemental significatif.

La remontée INSPIRE se fait via le [géocatalogue](https://www.geocatalogue.fr/), portail national géré par le BRGM et dédié aux données géographiques. En parallèle, [data.gouv.fr](http://data.gouv.fr/), la plateforme générale d'accès aux données publiques françaises gérée par la DINUM, s’occupe de la remontée HVD.

Cependant, le cadre de ces deux directives se recoupent et se renforcent sur 3 des catégories de HVD, dont les métadonnées doivent respecter la directive INSPIRE :

* **Les données géospatiales**
* **Les données sur l’observation de la Terre et l’environnement**
* **Les données de mobilité**

Afin d’éviter une double saisie de la part des producteurs de données et afin de satisfaire à la fois la directive INSPIRE et le règlement HVD pour les données concernées, une seule fiche doit donc être produite et maintenue par les producteurs, répondant aux deux obligations.

La remontée se fait ensuite de manière automatique au niveau européen pour répondre à ces deux obligations. Voici une proposition de schéma de rapportage dans le cas de jeux de données concernés à la fois par la directive INSPIRE et les HVD :

![schéma de remontées d'une fiche de données HVD et INSPIRE à l'Europe](<../.gitbook/assets/schéma remontée hvd.png>)

Pour qu’une même fiche de données soit doublement moissonnée mais ne soit pas créée de manière dupliquée au niveau européen, il est important que **l’identifiant de la fiche de données soit stable dans le temps et correctement préservé au cours des différents moissonnages**.

Cette question des identifiants doit être spécifiée en détail et pourra faire l’objet d’un point lors d’un prochain [groupe de travail métadonnées du CNIG](https://cnig.gouv.fr/gt-metadonnees-a958.html).

Du côté des producteurs, il s’agira surtout d’un point de vigilance lors de la mise en place des différents moissonnages.

### Rapportage au niveau européen depuis [data.gouv.fr](http://data.gouv.fr)

Le rapportage des données dans le cadre du règlement HVD se fait par le catalogue [data.gouv.fr](http://data.gouv.fr) via [Data Catalogue Vocabulary](https://w3c.github.io/dxwg/dcat/) (DCAT). Les producteurs de données ne sont pas responsables du rapportage lui-même.

Les [nouvelles lignes directrices](https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/) pour la description en DCAT de ces jeux de données répondant au règlement HVD sont l’objet d’un travail concerté au niveau européen et des états membres et sont toujours en cours de discussion, avec [un certain nombre de points toujours ouverts](https://github.com/SEMICeu/DCAT-AP/issues?q=is%3Aissue+is%3Aopen+label%3AHVD).

Aujourd’hui, certaines des métadonnées demandées ne sont pas correctement modélisées ou moissonnées dans [data.gouv.fr](http://data.gouv.fr). C’est le cas de la notion de point de contact ou des informations de description de service pour les APIs. Ces points sont bien identifiés et seront résolus en amont de l’application du règlement HVD. Ils pourront faire l'objet de discussions lors du [groupe de travail métadonnées du CNIG](https://cnig.gouv.fr/gt-metadonnees-a958.html).
