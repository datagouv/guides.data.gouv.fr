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

Plusieurs métadonnées sont obligatoires dans le cadre des données de forte valeur.&#x20;

{% tabs %}
{% tab title="Pour les jeux de données" %}
1. **Une métadonnée identifiant le jeu de données comme étant un HVD** via l'utilisation d'un mot clé "**hvd**"\*.&#x20;
2.  **Une métadonnée identifiant la catégorie HVD à laquelle la donnée appartient**

    via les mots clés suivant\* :&#x20;

    _Météorologiques_

    _Entreprises et propriété d'entreprises_

    _Géospatiales_

    _Mobilité_\
    _Observation de la terre et environnement_\
    _Statistiques_\
    Les mots clés sur data.gouv.fr sont automatiquement normalisés (mis en minuscule, etc.).
3. **La licence des données**. Celle-ci doit être équivalente ou moins restrictive que la [CC BY 4.0 DEED](https://creativecommons.org/licenses/by/4.0/). Nous recommandons la [licence ouverte 2.0](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf). \
   En savoir plus sur les [licences utilisables par les administrations](https://www.data.gouv.fr/fr/pages/legal/licences/) ou sur les [conditions de réutilisations qui s'appliquent si aucune licence n'est indiquée](https://www.legifrance.gouv.fr/codes/article\_lc/LEGIARTI000032255220).&#x20;

**\*Si vous publiez via moissonnage à partir de plateformes géographiques** supportant les thèmes de vocabulaires contrôlés (ex: GeoNetwork) **les mots clés sont déduits**  \
**via une URI du vocabulaire issue du** [**référentiel européen**](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/high-value-dataset-category) ([exemple pour la catégorie météorologique](http://data.europa.eu/bna/c\_164e0bf5)).

{% hint style="info" %}
**Si vous publiez par moissonnage** il est préconisé de suivre les bonnes pratiques DCAT-AP, [précisé ici dans le contexte des données de forte valeur](https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/#c2) pour disposer d'un **identifiant stable dans le temps**.
{% endhint %}
{% endtab %}

{% tab title="Pour les API" %}
1. **Une métadonnée identifiant le jeu de données comme étant un HVD** via l'utilisation d'un mot clé "**hvd**".\*
2.  **Une métadonnée identifiant la catégorie HVD à laquelle la donnée appartient**

    via les mots clés suivant:&#x20;

    _Météorologiques\*_

    _Entreprises et propriété d'entreprises_

    _Géospatiales_

    _Mobilité_\
    _Observation de la terre et environnement_\
    _Statistiques_\
    Les mots clés sur data.gouv.fr sont automatiquement normalisés (mis en minuscule, etc.).
3. **Un point de contact de l'API** : adresse mail ou formulaire de contact.&#x20;
4. **La licence des données**. Celle-ci doit être équivalente ou moins restrictive que la [CC BY 4.0 DEED](https://creativecommons.org/licenses/by/4.0/). Nous recommandons la [licence ouverte 2.0](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf). \
   En savoir plus sur les [licences utilisables par les administrations](https://www.data.gouv.fr/fr/pages/legal/licences/) ou sur les [conditions de réutilisations qui s'appliquent si aucune licence n'est indiquée](https://www.legifrance.gouv.fr/codes/article\_lc/LEGIARTI000032255220).&#x20;
5. **Un lien vers une page web de description de la qualité de service de cette API**. Par exemple un lien vers un SLA (service-level agreement).
6. **Un lien vers la documentation dans un format standard** pour les machines ou les utilisateurs humains, par exemple au format OpenAPI est aussi fortement recommandé.

**\*Si vous publiez via moissonnage à partir de plateformes géographiques** supportant les thèmes de vocabulaires contrôlés (ex: GeoNetwork) **les mots clés sont déduits**  \
**via une URI du vocabulaire issue du** [**référentiel européen**](https://op.europa.eu/en/web/eu-vocabularies/dataset/-/resource?uri=http://publications.europa.eu/resource/dataset/high-value-dataset-category) ([exemple pour la catégorie météorologique](http://data.europa.eu/bna/c\_164e0bf5)).

{% hint style="info" %}
**Si vous publiez par moissonnage** il est préconisé de suivre les bonnes pratiques DCAT-AP, [précisé ici dans le contexte des données de forte valeur](https://semiceu.github.io/DCAT-AP/releases/2.2.0-hvd/#c2) pour disposer d'un **identifiant stable dans le temps**.
{% endhint %}

{% hint style="warning" %}
**Aujourd’hui,** [**data.gouv.fr**](http://data.gouv.fr) **ne permet pas de modéliser et de moissonner les métadonnées d'API comme attendu dans le cadre des HVD.** [Des travaux](https://github.com/etalab/data.gouv.fr/issues/1294) sont en cours sur le sujet.
{% endhint %}
{% endtab %}
{% endtabs %}

## Les modalités de rapportage à la Commission européenne depuis [data.gouv.fr](http://data.gouv.fr)

Les Etats membres de l'Union européenne sont soumis à une obligation de rapportage tous les deux ans auprès de la Commission européenne, dans le cadre du [règlement d'exécution](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=PI\_COM:C\(2022\)9562) (article 5).

**Les producteurs de données ne sont pas responsables de ce rapportage. Celui-ci se base sur le catalogue** [**data.europa.eu**](https://data.europa.eu/) **qui moissonne les informations depuis** [**data.gouv.fr**](http://data.gouv.fr) **via un vocabulaire spécifique** [**Data Catalogue Vocabulary**](https://w3c.github.io/dxwg/dcat/) **(DCAT) HVD**.&#x20;

Avec les données correctement remontées au niveau européen, [data.europa.eu](https://data.europa.eu/) a une vision générale des HVDs par Etat Membre ([exemple pour la France](https://data.europa.eu/data/datasets?locale=en\&minScoring=0\&is\_hvd=true\&page=1\&dataScope=countryData\&country=fr)). Afin de faciliter la création du rapport, data.europa.eu propose des requêtes Sparql pour construire l'ensemble des métadonnées attendues (les ensembles de données, les licences, les liens API, etc.) à partir des informations disponibles sur [data.europa.eu](https://data.europa.eu/).

[Voir plus d'information sur ces outils de rapportage via data.europa.eu](https://dataeuropa.gitlab.io/data-provider-manual/hvd/Reporting\_guidelines\_for\_HVDs/).

Nous avons préparé un premier [tableau de bord](http://reporting-hvd.dataeng.etalab.studio/) afin de donner un aperçu des métadonnées disponibles par producteur sur [data.europa.eu](https://data.europa.eu/). Nous allons itérer pour intégrer l'entièreté des requêtes et donc métadonnées attendues pour le rapportage.

### Chronologie

* **Avant le 10 décembre 2024,** les organisations/ministères doivent s’assurer que leurs jeux de données HVD sont :
  * accessibles via API
  * accompagnés des métadonnées attendues
  * directement consultables depuis la fiche associée
  * correctement renseignés sur [tableau de bord du rapportage](http://reporting-hvd.dataeng.etalab.studio/) (basé sur [data.europa.eu](https://data.europa.eu/))
* A partir du 10 décembre 2024, l’équipe data.gouv.fr
  * commence à constituer le rapport basé sur les données HVD collectées depuis [data.europa.eu](http://data.europa.eu/)
  * vérifie en parallèle un par un que les jeux de données respectent bien les exigences
* A partir de fin décembre, l'équipe data.gouv.fr&#x20;
  * fige le rapport
  * complète avec les autres infos demandées par la Commission (analyse d’impact, documentation d’orientation sur la publication, réutilisation, etc.)
  * envoi le rapport complet à l’Europe

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
