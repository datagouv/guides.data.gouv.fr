# Phase de construction

Lexique : Phase de construction

La phase de construction consiste à implémenter techniquement le schéma de données obtenu après la phase de concertation. Pour cela, il est nécessaire de choisir un standard technique, créer les fichiers requis, les tester et les diffuser.

Durant cette phase, vous devez mobiliser des personnes possédant des compétences techniques. Cette phase consiste à transcrire les décisions prises lors de la phase de concertation en un ou plusieurs schémas de données suivant le découpage en fichiers retenu.

### [#](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction/#choisir-un-standard-technique-pour-la-description-de-votre-schema-de-donnees)Choisir un standard technique pour la description de votre schéma de données <a href="#choisir-un-standard-technique-pour-la-description-de-votre-schema-de-donnees" id="choisir-un-standard-technique-pour-la-description-de-votre-schema-de-donnees"></a>

Lexique : Standard

On utilise les termes « normes » et « standards » pour décrire un référentiel commun et documenté destiné à harmoniser l’activité d’un secteur.

Il existe plusieurs standards techniques pour les schémas de données. Le standard est à choisir en fonction de la nature des données concernées et des habitudes de l’écosystème produisant ou réutilisant les données liées au schéma.

Les principaux standards techniques sont les suivants :

* [Table Schema](https://frictionlessdata.io/specs/table-schema/) : adapté pour la description de données tabulaires (sous forme de tableurs ou de CSV). Ce standard technique utilise le format JSON
* [JSON Schema](https://json-schema.org/) : adapté pour la description de données avec une notion de hiérarchie. Ce standard utilise le format JSON
* [XML Schema Definition (XSD)](https://www.w3.org/TR/xmlschema11-1/) : adapté pour la description de données avec une notion de hiérarchie. Ce standard utilise le format XML

Notez que tous ces standards techniques sont supportés par [schema.data.gouv.fr](https://schema.data.gouv.fr/).

Aller au-delà de la documentation texte

Un schéma de données décrit uniquement par du texte ou par un tableau se prive de nombreux avantages, notamment celui de l'interopérabilité entre différents systèmes informatiques.

Les schémas de données décrits par des standards techniques permettent, en plus d’une documentation textuelle ou sous forme d’un tableau, de valider que des données correspondent à un modèle de données, d’agréger des données similaires, de générer automatiquement des données respectant un schéma.

### [#](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction/#creer-votre-schema-de-donnees)Créer votre schéma de données <a href="#creer-votre-schema-de-donnees" id="creer-votre-schema-de-donnees"></a>

Une fois un standard technique choisi, il faudra créer les fichiers requis pour modéliser vos données. La documentation de chaque standard technique décrit le contenu des fichiers à renseigner. Reportez-vous aux documentations respectives pour tirer parti des fonctionnalités avancées offertes : types de données et contraintes sur les valeurs en particulier.

Il est souvent possible de vérifier qu’un fichier correspond à un standard à l’aide d’outils en ligne ou en ligne de commande. Utilisez ces outils pour vérifier que vos productions correspondent au standard.

Exemples à votre disposition

Pour un schéma au format Table Schema, nous mettons à votre disposition [un modèle de départ](https://github.com/etalab/tableschema-template) pour créer un dépôt Git contenant un schéma au format Table Schema.

Pour les autres formats de schémas, nous vous recommandons de consulter les schémas et dépôts Git listés sur [schema.data.gouv.fr](https://schema.data.gouv.fr/).

### [#](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction/#documenter-votre-schema-de-donnees)Documenter votre schéma de données <a href="#documenter-votre-schema-de-donnees" id="documenter-votre-schema-de-donnees"></a>

En complément du fichier du schéma de données, nous vous conseillons de rédiger a minima deux documents complémentaires :

* **une documentation générale** : vous indiquerez le contexte, les modalités de production des données, le cadre juridique, la finalité, les cas d’usage etc. Ce fichier est traditionnellement rédigé en Markdown et nommé `README.md` ;
* **un fichier répertoriant les changements** : permettant de suivre les modifications, d’une version à une autre. Ce fichier est traditionnellement rédigé en Markdown et nommé `CHANGELOG.md`.

La présence de ces fichiers représente un package complet (documentation, liste des changements et schéma de données décrit dans un standard technique), apprécié des réutilisateurs. [schema.data.gouv.fr](https://schema.data.gouv.fr/) se repose sur ces éléments pour intégrer votre documentation et votre liste de changements sur une page web.

Exemples à votre disposition

Vous pouvez consulter [la documentation](https://github.com/etalab/schema-stationnement/blob/master/README.md) et [la liste des changements](https://github.com/etalab/schema-stationnement/blob/master/CHANGELOG.md) du schéma des lieux de stationnement.

### [#](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction/#publier-et-diffuser-votre-schema-de-donnees)Publier et diffuser votre schéma de données <a href="#publier-et-diffuser-votre-schema-de-donnees" id="publier-et-diffuser-votre-schema-de-donnees"></a>

Une fois votre schéma de données créé, il est nécessaire de le publier et de le diffuser pour que d’autres personnes puissent en bénéficier. Nous vous recommandons de publier vos schémas de données en tant que logiciels libres, sur votre forge de développement ou par le biais de [GitLab](https://about.gitlab.com/) ou [GitHub](https://github.com/).

Vous bénéficierez alors des avantages habituels des dépôts de code Git en ligne : historique des modifications, fonctionnalités de tickets ou de demandes de modifications. Utilisez un compte d’organisation (dédié à votre entreprise, direction, service, ministère) et non votre compte personnel afin d’assurer une URL stable dans le temps.

Exemples à votre disposition

Vous trouverez plusieurs dépôts Git de schémas sur [schema.data.gouv.fr](https://schema.data.gouv.fr/). Consultez par exemple [le dépôt Git décrivant les lieux de stationnement](https://github.com/etalab/schema-stationnement) à l’aide d’un schéma TableSchema sur GitHub.

### [#](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction/#referencer-votre-schema-de-donnees-sur-schema-data-gouv-fr)Référencer votre schéma de données sur schema.data.gouv.fr <a href="#referencer-votre-schema-de-donnees-sur-schema-data-gouv-fr" id="referencer-votre-schema-de-donnees-sur-schema-data-gouv-fr"></a>

Pour faciliter la découverte de votre schéma de données et des données sous-jacentes, nous vous recommandons de le faire référencer sur [schema.data.gouv.fr](https://schema.data.gouv.fr/). Nous avons rédigé [une page dédiée](https://guides.etalab.gouv.fr/producteurs-schemas/integration-schema-datagouv) à ce sujet décrivant les plus-values, prérequis et démarches à suivre.

### [#](https://guides.etalab.gouv.fr/producteurs-schemas/phase-construction/#points-de-sortie)Points de sortie <a href="#points-de-sortie" id="points-de-sortie"></a>

À l’issue de cette phase, vous devriez :

* Avoir implémenté votre schéma de données dans un des standards reconnus ;
* Avoir publié votre travail en ligne, dans un répetoire Git dédié ;
* Avoir pris contact avec les équipes de schema.data.gouv.fr dans le but de référencer votre schéma de données si nécessaire.
