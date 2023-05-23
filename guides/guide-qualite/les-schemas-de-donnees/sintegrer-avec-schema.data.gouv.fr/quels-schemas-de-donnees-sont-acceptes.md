# Quels schémas de données sont acceptés ?

## Schémas de données acceptés sur schema.data.gouv.fr

[schema.data.gouv.fr](https://schema.data.gouv.fr/) accepte :&#x20;

* **des schémas de données décrivant des données publiques**

{% hint style="info" %}
Les schémas de données sont acceptés dès lors que leur l’existence est justifiée par voie :

* **réglementaire** : c'est une disposition réglementaire qui est à l'origine de la définition du schéma de données ;
* **d’usage** : la réutilisation des données décrites par le schéma bénéficie à un grand nombre ou de nombreux producteurs sont amenés à utiliser ce schéma de données.
{% endhint %}

* **des schémas de données décrits par un standard technique** (cf. page ["Phase de construction"](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction)) : les schémas de données décrits uniquement par de la documentation textuelle ou des tableaux ne sont pas acceptés.

{% hint style="info" %}
**Standards techniques supportés**

Les standards techniques de schémas de données actuellement supportés sont les suivants :

* [**Table Schema**](https://frictionlessdata.io/specs/table-schema/) : adapté pour la description de données tabulaires (sous forme de tableurs ou de CSV). Ce standard technique utilise le format JSON.
* [**JSON Schema**](https://json-schema.org/) : adapté pour la description de données avec une notion de hiérarchie. Ce standard utilise le format JSON.
* [**XML Schema Definition (XSD)**](https://www.w3.org/TR/xmlschema11-1/) : adapté pour la description de données avec une notion de hiérarchie. Ce standard utilise le format XML.
{% endhint %}

## Prérequis de validation des schémas de données sur schema.data.gouv.fr <a href="#prerequis-de-validation-des-schemas-de-donnees" id="prerequis-de-validation-des-schemas-de-donnees"></a>

{% hint style="info" %}
**Lexique : Validation d’un schéma de données**

La validation d’un schéma de données est l’étape qui permet de vérifier si celui-ci est conforme au standard technique sélectionné et aux prérequis de [schema.data.gouv.fr](https://schema.data.gouv.fr/). Cette étape s’intéresse uniquement au schéma de données et à la façon dont il est publié.

Il ne faut pas confondre la validation d’un schéma avec le fait de vérifier que des données correspondent à un schéma.
{% endhint %}

Pour tous les types de schéma de données, il faut que :&#x20;

* [ ] **le schéma de données soit sur un dépôt Git, à raison d’un dépôt par schéma**. Ce dépôt doit pouvoir être cloné depuis Internet sans authentification préalable ;
* [ ] **le dépôt Git doit comporter des tags indiquant les versions du schéma de données**. Ces versions doivent respecter la [gestion sémantique de version semver](https://semver.org/lang/fr/), sous la forme `1.3.2` par exemple ;
* [ ] **le dépôt doit comporter un fichier `README.md` à la racine** contenant une documentation du schéma de données indiquant par exemple le contexte de production, la gouvernance ;
* [ ] **passer avec succès les tests spécifiques au type de schéma de données que le dépôt contient.**

{% hint style="info" %}
**Critères complets de validation**

Cette page présente les grands principes de validation des schémas de données.&#x20;

Le détail des prérequis propres à chaque type de schéma de données, ainsi que des exemples, sont disponibles [ici](https://schema.data.gouv.fr/validation.html).&#x20;
{% endhint %}

Etalab se réserve le droit de refuser l’ajout de schémas en motivant son refus. Il est encouragé d'[initier une discussion](https://github.com/etalab/schema.data.gouv.fr/issues) préalablement à l’ouverture d’une _pull request_.