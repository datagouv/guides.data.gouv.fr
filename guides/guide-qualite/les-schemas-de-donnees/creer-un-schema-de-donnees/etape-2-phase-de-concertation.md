# Etape 2 : Phase de concertation

{% hint style="info" %}
**Lexique : Phase de concertation**

La phase de concertation est la phase centrale de la création d’un schéma de données.&#x20;



C'est l’étape où plusieurs parties prenantes (producteurs, réutilisateurs, experts métiers et techniques) se rassemblent pour définir et spécifier les éléments essentiels à la constitution du schéma.
{% endhint %}

## Comment spécifier un schéma de données ?

Pour spécifier un schéma de données, il est nécessaire de définir :

* [ ] **les champs** ;
* [ ] **les types associés de ces champs** (une date, un nombre, une chaîne de caractère, etc.) ;
* [ ] **les contraintes de chaque champ** (entier positif, texte dans une liste fermée, etc.) ;
* [ ] **la description de chaque champ** ;
* [ ] **une documentation associée** au schéma de données décrivant le contexte, les acteurs, les cas d’usage.

Pour obtenir ce résultat, il peut être utile de réaliser au préalable un [modèle de données](https://guides.etalab.gouv.fr/qualite/documenter-les-donnees/#description-du-modele-de-donnees) qui présente la structuration des informations. La modélisation ne prend pas en compte les contraintes d'implémentation, elle est un outil de dialogue entre les différents intervenants.

## Comment organiser la collaboration entre les différentes parties prenantes autour d'un schéma de données ? <a href="#procedure-de-collaboration" id="procedure-de-collaboration"></a>

Il est conseillé de :&#x20;

* [ ] **travailler sur un document partagé**, accessible en ligne, tel qu'un Framapad ou Google Doc : l'important est que plusieurs contributeurs puissent contribuer (modifier ou mettre des commentaires) sans avoir besoin d'être présents physiquement ou de recevoir des versions intermédiaires par email.&#x20;
* [ ] en complément du document partagé, **organiser plusieurs réunions** afin de débattre du schéma de données à produire (et de l'éventuel modèle de données construit).
* [ ] **impliquer une multitude d'acteurs** : vous devez rassembler des producteurs, experts métiers, experts techniques et réutilisateurs. La richesse des profils et des enjeux permettra d’aboutir à la solution la plus adaptée.

{% hint style="info" %}
**Référencer votre schéma**

Référencer votre schéma sur [schema.data.gouv.fr](https://schema.data.gouv.fr/) vous permettra de bénéficier de conseils de la part d’Etalab et de ses partenaires institutionnels et associatifs. La marche à suivre pour référencer votre schéma est détaillée ici.
{% endhint %}

## Comment construire un schéma de données de qualité ? <a href="#grands-principes" id="grands-principes"></a>

Pour construire un schéma de données de qualité, il est conseillé de :&#x20;

* [ ] **Construire un** [**modèle de données**](https://guides.etalab.gouv.fr/qualite/documenter-les-donnees/#description-du-modele-de-donnees)**.** Il est important de disposer d'un outil visuel qui présente les entités "métier" mais surtout les dépendances et relations entre ces "entités". Ce modèle peut être enrichi de tous les attributs nécessaires au fur et à mesure de la concertation.
* [ ] **Profiter de l’existant.** De nombreux standards existent déjà, qu’ils concernent des formats de données ou des formats de champs. Certains standards sont devenus incontournables aujourd’hui, comme [ISO-8601](https://fr.wikipedia.org/wiki/ISO\_8601) pour les dates ou [WGS 84](https://fr.wikipedia.org/wiki/WGS\_84) pour les coordonnées géographiques.
* [ ] **Identifier et associer l’écosystème.** Les personnes/organisations que vous associez sont la meilleure garantie d’un schéma de données efficace et largement adopté, permettant d'aboutir à un véritable standard :&#x20;

<!---->

* D'un côté les producteurs, qui connaissent la réalité de leurs données, de la collecte, etc. et qui ont leurs propres usages.
* De l'autre les réutilisateurs, avec leurs besoins et leurs difficultés, qu’ils soient déjà connus, « sous le radar » ou en devenir.

<!---->

* [ ] **Prendre le temps.** Un schéma de données est susceptible de concerner beaucoup de producteurs et d’usagers. Sa modification peut avoir un impact important. Il est donc crucial de prendre le temps d’obtenir tous les retours avant de publier un schéma utilisable par le plus grand nombre. Un schéma de données devrait être publié quand il est prêt, non pas en fonction d’un impératif de délai.
* [ ] **Lever les implicites et les ambiguïtés.** Toutes les spécifications d’un schéma de données doivent être les plus claires possibles, y compris pour des cas/données qui n’existent pas encore mais pourraient apparaître à l’avenir.
* [ ] **Éviter la redondance mais sans l’exclure absolument.** Trois champs pour définir une latitude et une longitude (`latitude`, `longitude`, `lat-lon`) est inutilement redondant. Toutefois, préciser le nom d’une commune en plus de son code INSEE rend les données plus faciles à lire et à exploiter.
* [ ] **Utiliser des données pivot relevant d’un référentiel ouvert** pour relier les données à d’autres données, par exemple l’utilisation du numéro SIREN pour identifier des organisations. Ce principe permet aussi d’éviter l’abondance de détails et d’aller à l’essentiel : l’obtention d’informations complémentaires se fera par le biais d’un autre référentiel.

{% hint style="info" %}
**Exemples à votre disposition**

Il est possible de retrouver des fichiers de schémas sur [schema.data.gouv.fr](https://schema.data.gouv.fr/) (exemple : [le schéma des lieux de stationnement](https://schema.data.gouv.fr/etalab/schema-stationnement/latest.html)).&#x20;

En complément, le[ guide dédié à la préparation de jeux de données](https://guides.etalab.gouv.fr/qualite/) pourrait être utile pour définir votre schéma.
{% endhint %}

## Points de sortie <a href="#points-de-sortie" id="points-de-sortie"></a>

À l’issue de cette phase, vous devriez :

* Avoir réuni différents partenaires afin de collaborer sur votre schéma de données ;
* Avoir décidé des différents champs de votre schéma de données, leurs types et définitions et produit une documentation associée.
