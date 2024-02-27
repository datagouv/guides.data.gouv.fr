---
description: Précisions pratiques pour les producteurs de données de forte valeur
---

# Données de forte valeur : métadonnées obligatoires et modalités de rapportage

{% hint style="info" %}
**Rappel juridique**

La "Directive Open Data" ([Directive 2019/1024](https://eur-lex.europa.eu/legal-content/FR/TXT/HTML/?uri=CELEX:32019L1024)) définit les données de forte valeur comme les "_documents détenus par un organisme du secteur public, dont la réutilisation est associée à des bénéfices importants pour la société, l'environnement et l'économie_". Il s'agit alors de les mettre à disposition avec un minimum de restrictions légales et techniques afin d'augmenter leur potentiel de réutilisation et leur impact.\
\
[Un règlement d'exécution (2023/138)](https://eur-lex.europa.eu/legal-content/FR/TXT/HTML/?uri=CELEX:32023R0138) établit la liste des ensembles de données de forte valeur.\
\
Les données de forte valeur devront être mises à disposition gratuitement en vue de leur réutilisation pour le **9 juin 2024**.
{% endhint %}

Les données de forte valeur (HVD) ont vocation à remonter sur la plateforme data.gouv.fr dans le cadre des obligations de rapportage établies dans [le règlement d'exécution](https://eur-lex.europa.eu/legal-content/FR/TXT/HTML/?uri=CELEX:32023R0138). Les modalités techniques définies ici font l'objet d'un travail concerté et itératif avec plusieurs parties prenantes, notamment dans le cadre de groupes de travail portés par le CNIG. Des discussions sont en cours sur ces modalités techniques et de nouvelles précisions sont à venir.

Ce guide présente :

* [Le processus global de remontée des données sur data.gouv.fr ;](donnees-de-forte-valeur-modalites-de-rapportage.md#processus-global-de-remontee-des-fiches-de-donnees-sur-data.gouv.fr)
* [Les métadonnées obligatoires à renseigner pour les données de forte valeur ;](donnees-de-forte-valeur-modalites-de-rapportage.md#metadonnees-obligatoires-pour-les-donnees-de-forte-valeur)
* [Les modalités de rapportage à la Commission européenne ; ](donnees-de-forte-valeur-modalites-de-rapportage.md#les-modalites-de-rapportage-a-la-commission-europeenne-depuis-data.gouv.fr)
* [L'articulation entre la directive INSPIRE et le règlement d'exécution relatif aux données de forte valeur.](donnees-de-forte-valeur-modalites-de-rapportage.md#larticulation-entre-la-directive-inspire-et-le-reglement-dexecution-relatif-aux-donnees-de-forte-val)

Il a vocation à être enrichi au gré des nouvelles précisions. Une foire aux questions sera également alimentée.

## Processus global de remontée des fiches de données sur data.gouv.fr

Pour les producteurs concernés (cf. [ouverture.data.gouv.fr](https://ouverture.data.gouv.fr/)), la remontée des données de forte valeur sur data.gouv.fr se déroule selon les étapes suivantes :

1. Les données sont identifiées comme étant de forte valeur et sont classées dans l’une des 6 grandes catégories précisées dans les 6 annexes du règlement d'exécution (géospatiales, météorologiques, etc.). Selon la catégorie associée, les conditions de mise à disposition et les métadonnées obligatoires diffèrent.
2. Les données ainsi identifiées remontent au niveau national en étant :
   * soit moissonnées sur [data.gouv.fr](http://data.gouv.fr/) (cf. [Moissonnage](../guide-data.gouv.fr/moissonnage/)) et éventuellement le [geocatalogue](https://www.geocatalogue.fr/) selon leur nature ;
   * soit publiées directement sur [data.gouv.fr](https://www.data.gouv.fr/).
3. Les données sont moissonnées par [data.europa.eu](https://data.europa.eu/en) pour proposer un catalogue européen des données de forte valeur.

## Métadonnées obligatoires pour les données de forte valeur

Il y a 5 métadonnées obligatoires à renseigner à minima pour les données de forte valeur.

Nous considérons différents cas de publications des données sur data.gouv.fr :

1️⃣ Publication directe sur data.gouv.fr (manuelle ou par API).\
2️⃣ Publication via moissonnage de plateformes open data (ex: CKAN / ODS).\
3️⃣ Publication via moissonnage des plateformes géographiques supportant les thèmes de vocabulaires contrôlés (ex: GeoNetwork).

**La liste des métadonnées obligatoires pour les données de forte valeur est la suivante :**

1. Une métadonnée identifiant le jeu de données comme étant un HVD
   * Dans le cas 1️⃣ et 2️⃣, via l'utilisation d'un mot clé "**hvd**".
   * Dans le cas 3️⃣, cette métadonnée est directement déduite de la catégorie HVD via son URI (voir point suivant).
2.  Une métadonnée identifiant la catégorie HVD à laquelle la donnée appartient

    * Dans le cas 1️⃣ et 2️⃣, l'information est remplie via les mots clés. La liste des libellés est la suivante :
      * **Météorologiques**
      * **Entreprises et propriété d'entreprises**
      * **Géospatiales**
      * **Mobilité**
      * **Observation de la terre et environnement**
      * **Statistiques**
    * Dans le cas 3️⃣, cette métadonnée doit être renseignée via une URI du vocabulaire issue du [référentiel européen](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/high-value-dataset-category) (ex: [http://data.europa.eu/bna/c\_164e0bf5](http://data.europa.eu/bna/c\_164e0bf5) pour la catégorie météorologique).

    :information\_source: Les mots clés sur data.gouv.fr sont automatiquement normalisés (mis en minuscule, etc.).
3. **Dans le cadre d’une API**, une page web de description de la qualité de service de cette API est attendue.
   * Il peut par exemple s’agir d’un lien vers un SLA (service-level agreement).
4.  **Dans le cadre d’une API**, un lien vers la documentation de l’API est aussi fortement recommandé

    * Dans un format standard pour les machines ou les utilisateurs humains, par exemple au format OpenAPI.

    :information\_source: Aujourd’hui, [data.gouv.fr](http://data.gouv.fr) ne permet pas de modéliser et de moissonner les métadonnées d'API comme attendu dans le cadre des HVD. [Des travaux](https://github.com/etalab/data.gouv.fr/issues/1294) sont en cours sur le sujet.
5. Un point de contact des données ou API
   * Il peut prendre la forme d’une adresse mail ou d’un formulaire de contact. Il est **obligatoire dans le cas d’une API** mais **optionnel pour les données en téléchargement**.
6. Une métadonnée décrivant la licence utilisée (équivalente [licence Creative Commons BY 4.0](https://creativecommons.org/licenses/by/4.0/) ou moins restrictive)
   * Identifiant [la licence ouverte Etalab 2.0](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf) (LOv2) ou l’une des [licences supportées sur data.gouv.fr](https://www.data.gouv.fr/api/1/datasets/licenses/). Plus d’informations [sur cette page](https://www.data.gouv.fr/fr/pages/legal/licences/) sur les licences utilisables par les administrations.
   * L'URL à utiliser pour la LOv2 dans le cadre d'un moissonnage est [https://www.etalab.gouv.fr/licence-ouverte-open-licence](https://www.etalab.gouv.fr/licence-ouverte-open-licence).
   * Aujourd’hui, aucune licence en dehors de celles supportées ne sera correctement moissonnée par [data.gouv.fr](http://data.gouv.fr).
   * En l’absence de licence indiquée, le Code des Relations entre le Public et l'Administration précise les [conditions de réutilisations qui s'appliquent](https://www.legifrance.gouv.fr/codes/article\_lc/LEGIARTI000032255220).
7. Un identifiant stable dans le temps. Il est préconisé qu’il suive les bonnes pratiques DCAT-AP, [précisé ici dans le contexte des données de forte valeur](https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/#c2).
   * Dans le cas 1️⃣, l'identifiant est géré par data.gouv.fr et les producteurs n'ont pas à s'en inquiéter.
   * Dans les cas 2️⃣ et 3️⃣, l'identifiant est géré par la plateforme d'origine et est moissonné par data.gouv.fr.

## Les modalités de rapportage à la Commission européenne depuis [data.gouv.fr](http://data.gouv.fr)

Les Etats membres de l'Union européenne sont soumis à une obligation de rapportage auprès de la Commission européenne, dans le cadre du règlement d'exécution.

**Les producteurs de données ne sont pas responsables de ce rapportage. Celui-ci se fait par le catalogue** [**data.gouv.fr**](http://data.gouv.fr) **via** [**Data Catalogue Vocabulary**](https://w3c.github.io/dxwg/dcat/) **(DCAT)**.&#x20;

Les [nouvelles lignes directrices](https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/) pour la description en DCAT de ces jeux de données de forte valeur ont fait l'objet d’un travail concerté au niveau européen et des Etats membres.

Aujourd’hui, certaines des métadonnées demandées ne sont pas correctement modélisées ou moissonnées dans [data.gouv.fr](http://data.gouv.fr). C’est le cas des informations de description de service pour les APIs. **Ces points sont bien identifiés et seront résolus en amont de l’application du règlement relatif aux données de forte valeur**. Ils font l'objet de discussions lors du [groupe de travail métadonnées du CNIG](https://cnig.gouv.fr/gt-metadonnees-a958.html).

## L'articulation entre la Directive INSPIRE et le règlement d'exécution relatif aux données de forte valeur&#x20;

{% hint style="info" %}
**INSPIRE** est une directive qui vise à établir une infrastructure d'information géographique pour l'environnement, à l'échelle européenne. \


**"Données de forte valeur"** découle de la directive Open Data et est un label attribué à des données dont la mise en open data peut générer un impact économique, social et environnemental significatif.
{% endhint %}

La remontée des données INSPIRE se fait via le [géocatalogue](https://www.geocatalogue.fr/), portail national géré par le Bureau de recherches géologiques et minières (BRGM) et dédié aux données géographiques.

La remontée des données de forte valeur, quant à elle, se fait via [data.gouv.fr](https://www.data.gouv.fr/fr/), la plateforme nationale des données publiques françaises, gérée par la Direction interministérielle du numérique (DINUM).

Cependant, pour 3 catégories d'ensembles de données de forte valeur, [la Directive INSPIRE](https://eur-lex.europa.eu/legal-content/FR/ALL/?uri=celex%3A32007L0002) et le règlement d'exécution se rapportant aux données de forte valeur se recoupent et se renforcent :&#x20;

* **Les données géospatiales**
* **Les données sur l’observation de la Terre et l’environnement**
* **Les données de mobilité**

**Dans ce cas, les métadonnées doivent également respecter le cadre défini par** [**la Directive INSPIRE**](https://eur-lex.europa.eu/legal-content/FR/ALL/?uri=celex%3A32007L0002)**.**

Pour éviter une double saisie, les producteurs de données ne produisent et ne maintiennent qu'une seule fiche, répondant aux deux législations. La remontée se fait ensuite de manière automatique au niveau européen pour répondre à ces deux obligations.

Voici **une proposition de schéma de rapportage** dans le cas de jeux de données concernés à la fois par la directive INSPIRE et le règlement d'exécution se rapportant aux données de forte valeur :

![Schéma de remontées d'une fiche de données HVD et INSPIRE à l'Europe](https://raw.githubusercontent.com/etalab/guides.data.gouv.fr/main/.gitbook/assets/sch%C3%A9ma%20remont%C3%A9e%20hvd.png)

Pour qu’une même fiche de données soit doublement moissonnée mais ne soit pas créée de manière dupliquée au niveau européen, il est important que **l’identifiant de la fiche de données soit stable dans le temps et correctement préservé au cours des différents moissonnages**.

Les producteurs de données doivent donc être particulièrement vigilants lors de la mise en place des différents moissonnages.

La question des identifiants fait l’objet d’[un point et d'une recommandation](https://github.com/cnigfr/metadonnee/issues/28) lors du [groupe de travail métadonnées du CNIG](https://cnig.gouv.fr/gt-metadonnees-a958.html).
