# Etape 3 : Phase de construction

{% hint style="info" %}
**Lexique : Phase de construction**

La phase de construction consiste à implémenter techniquement le schéma de données obtenu après la phase de concertation. Pour cela, il est nécessaire de choisir un standard technique, créer les fichiers requis, les tester et les diffuser.

Durant cette phase, il est nécessaire de mobiliser des personnes possédant des compétences techniques. Cette phase consiste à transcrire les décisions prises lors de la phase de concertation en un ou plusieurs schémas de données suivant le découpage en fichiers retenu.
{% endhint %}

## Choisir un standard technique pour la description d'un schéma de données <a href="#choisir-un-standard-technique-pour-la-description-de-votre-schema-de-donnees" id="choisir-un-standard-technique-pour-la-description-de-votre-schema-de-donnees"></a>

{% hint style="info" %}
**Lexique : Standard**

On utilise les termes « normes » et « standards » pour décrire un référentiel commun et documenté destiné à harmoniser l’activité d’un secteur.
{% endhint %}

Il existe plusieurs standards techniques pour les schémas de données.&#x20;

Le standard est à choisir en fonction :&#x20;

* **de la nature des données concernées** ;&#x20;
* **des habitudes de l’écosystème** produisant ou réutilisant les données liées au schéma.

Les principaux standards techniques sont les suivants :

* [**Table Schema**](https://frictionlessdata.io/specs/table-schema/) : adapté pour la description de données tabulaires (sous forme de tableurs ou de CSV). Ce standard technique utilise le format JSON ;
* [**JSON Schema**](https://json-schema.org/) : adapté pour la description de données avec une notion de hiérarchie. Ce standard utilise le format JSON ,
* [**XML Schema Definition (XSD)**](https://www.w3.org/TR/xmlschema11-1/) : adapté pour la description de données avec une notion de hiérarchie. Ce standard utilise le format XML.

Tous ces standards techniques sont supportés par [schema.data.gouv.fr](https://schema.data.gouv.fr/).

{% hint style="info" %}
**Conseil : Aller au-delà de la documentation texte**

Un schéma de données décrit uniquement par du texte ou par un tableau se prive de nombreux avantages, notamment celui de l'interopérabilité entre différents systèmes informatiques.

Les schémas de données décrits par des standards techniques permettent, en plus d’une documentation textuelle ou sous forme d’un tableau, de valider que des données correspondent à un modèle de données, d’agréger des données similaires, de générer automatiquement des données respectant un schéma.
{% endhint %}

## Créer un schéma de données <a href="#creer-votre-schema-de-donnees" id="creer-votre-schema-de-donnees"></a>

Une fois un standard technique choisi, **il faudra créer les fichiers requis pour modéliser les données**.&#x20;

La documentation de chaque standard technique décrit le contenu des fichiers à renseigner. Reportez-vous aux documentations respectives pour tirer parti des fonctionnalités avancées offertes : types de données et contraintes sur les valeurs en particulier.

Il est possible de vérifier qu’un fichier correspond à un standard à l’aide d’outils en ligne ou en ligne de commande. Utilisez ces outils pour vérifier que vos productions correspondent au standard.

{% hint style="info" %}
**Exemples à votre disposition**

Pour un schéma au format Table Schema, [un modèle de départ](https://github.com/etalab/tableschema-template) est mis à disposition pour créer un dépôt Git contenant un schéma au format Table Schema.

Pour les autres formats de schémas, il est conseillé de consulter les schémas et dépôts Git listés sur [schema.data.gouv.fr](https://schema.data.gouv.fr/).
{% endhint %}

## Documenter un schéma de données <a href="#documenter-votre-schema-de-donnees" id="documenter-votre-schema-de-donnees"></a>

En complément du fichier du schéma de données, il est recommandé de rédiger a minima deux documents complémentaires :

* **Une documentation générale** qui indique le contexte, les modalités de production des données, le cadre juridique, la finalité, les cas d’usage etc. Ce fichier est traditionnellement rédigé en Markdown et nommé `README.md` ;
* **Un fichier répertoriant les changements** permettant de suivre les modifications, d’une version à une autre. Ce fichier est traditionnellement rédigé en Markdown et nommé `CHANGELOG.md`.

La présence de ces fichiers représente un package complet (_documentation, liste des changements et schéma de données décrit dans un standard technique_), apprécié des réutilisateurs. [schema.data.gouv.fr](https://schema.data.gouv.fr/) se repose sur ces éléments pour intégrer votre documentation et votre liste de changements sur une page web.

{% hint style="info" %}
**Exemples à votre disposition**

L[a documentation](https://github.com/etalab/schema-stationnement/blob/master/README.md) et [la liste des changements](https://github.com/etalab/schema-stationnement/blob/master/CHANGELOG.md) du schéma des lieux de stationnement.
{% endhint %}

## Publier et diffuser un schéma de données <a href="#publier-et-diffuser-votre-schema-de-donnees" id="publier-et-diffuser-votre-schema-de-donnees"></a>

Une fois votre schéma de données créé, il est nécessaire de le publier et de le diffuser pour que d’autres personnes puissent en bénéficier.&#x20;

**Il est recommandé de publier vos schémas de données en tant que logiciels libres, sur votre forge de développement ou par le biais de** [**GitLab**](https://about.gitlab.com/) **ou** [**GitHub**](https://github.com/)**.**

Vous bénéficierez alors des avantages habituels des dépôts de code Git en ligne :&#x20;

* Historique des modifications
* Fonctionnalités de tickets
* Demandes de modifications.&#x20;
* etc.

Il est conseillé d'utiliser un compte d’organisation (dédié à votre entreprise, direction, service, ministère) et non un compte personnel afin d’assurer une URL stable dans le temps.

{% hint style="info" %}
**Exemples à votre disposition**

Plusieurs dépôts Git de schémas sont disponibles sur [schema.data.gouv.fr](https://schema.data.gouv.fr/) (exemple : [le dépôt Git décrivant les lieux de stationnement](https://github.com/etalab/schema-stationnement) à l’aide d’un schéma TableSchema sur GitHub).&#x20;
{% endhint %}

Pour faciliter la découverte de votre schéma de données et des données sous-jacentes, il est recommandé de le faire référencer sur [schema.data.gouv.fr](https://schema.data.gouv.fr/). La marche à suivre est détaillée [ici](../../../../guide-qualite/les-schemas-de-donnees/integration-avec-schema.data.gouv.fr.md).&#x20;

## Points de sortie <a href="#points-de-sortie" id="points-de-sortie"></a>

À l’issue de cette phase, vous devriez :

* Avoir implémenté votre schéma de données dans un des standards reconnus ;
* Avoir publié votre travail en ligne, dans un répertoire Git dédié ;
* Avoir pris contact avec les équipes de [schema.data.gouv.fr](https://schema.data.gouv.fr/) dans le but de référencer votre schéma de données si nécessaire.
