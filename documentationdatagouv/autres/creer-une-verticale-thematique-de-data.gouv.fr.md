---
icon: browser
---

# Créer une verticale thématique de data.gouv.fr

### Qu'est-ce que data.gouv.fr ?

[data.gouv.fr](https://data.gouv.fr/) est la plateforme nationale de la donnée publique, opérée par la DINUM.\
Elle a pour mission de permettre à tous, administrations, entreprises, chercheurs et citoyens, d’accéder, partager et réutiliser les données publiques.

***

### Qu'est-ce qu'une verticale thématique ?

Une **verticale thématique** est une **surcouche spécialisée** de data.gouv.fr.\
Elle s’appuie sur la même base technique et les mêmes données, mais propose une **expérience thématique**, ciblée sur un domaine précis.

Les verticales :

* ne dupliquent **aucune donnée** ;
* exposent des jeux de données **hébergés sur data.gouv.fr** ;
* permettent de **fédérer une communauté** autour d’un domaine spécifique ;
* offrent des **fonctionnalités avancées** adaptées à leur sujet.

Exemples actuels :

* 🌿 [ecologie.data.gouv.fr](https://ecologie.data.gouv.fr/)
* ☀️ [meteo.data.gouv.fr](https://meteo.data.gouv.fr/)
* 🚆 [transport.data.gouv.fr](https://transport.data.gouv.fr/)
* 🎭 [culture.data.gouv.fr](https://culture.data.gouv.fr/)
* 🚛 [logistique.data.gouv.fr](https://logistique.data.gouv.fr/)

Les verticales sont nées d’un partenariat entre **data.gouv.fr** (DINUM) et plusieurs acteurs publics, notamment le **CGDD** (Commissariat général au développement durable, Ministère de la transition écologique) et **l’Ecolab**.

L’objectif est de mutualiser une infrastructure technique commune pour créer des portails thématiques, cohérents, durables et interopérables.

***

### Sélection des données

Les verticales n’hébergent pas de données. Elles **sélectionnent et exposent** celles déjà présentes sur data.gouv.fr.\
La sélection se fait principalement par :

* **liste d’organisations** (ministères, opérateurs, établissements publics) ;
* **tags**, **schémas** ou **thématiques** spécifiques.

Les gestionnaires peuvent également créer des **topics** (playlists de données) pour éditorialiser leur portail.

***

### Personnalisation et fonctionnalités

#### Ce qui est personnalisable

* La page d’accueil
* Les contenus éditoriaux
* Les playlists de données (topics)
* Le branding (nom, logo, bannière, couleurs)

#### Fonctionnalités spécifiques

Chaque verticale peut ajouter des fonctionnalités propres à son domaine, par exemple :

* Notifications en temps réel pour les données de transport
* Recherche avancée sur les séries météorologiques
* Visualisations ou cartes adaptées à la thématique

L’objectif est de **mutualiser le socle**, tout en **permettant des enrichissements ciblés**.

***

### Gouvernance

#### Qui peut créer une verticale ?

Le code est **ouvert à tous**. Toute organisation peut créer sa verticale sur la base de data.gouv.fr.\
Cependant, pour utiliser un **domaine officiel** `*.data.gouv.fr`, il faut :

* obtenir l’accord de la **DINUM** ;
* respecter les principes de la [**charte data.gouv.fr**](https://www.data.gouv.fr/pages/legal/charter) ;
* en fonction des modalités de partenariat, signer une **convention de délégation de gestion**.

#### Gouvernance partagée

* **DINUM / data.gouv.fr** : responsable du socle technique et du pilotage global.
* **Porteur de verticale** : responsable éditorial et fonctionnel de sa thématique.
* **Club utilisateurs** : espace d’échange entre gestionnaires de verticales et l’équipe data.gouv.fr pour co-construire les évolutions.

***

### Accompagnement

#### Qui peut accompagner ?

L’équipe **data.gouv.fr (DINUM)** accompagne les porteurs à toutes les étapes :

* cadrage du projet ;
* configuration et déploiement ;
* communication et lancement.

#### Est-ce qu’il faut une équipe technique ?

* **Non, pas forcément.**\
  La plupart des paramètres sont configurables sans développement.
* **Oui, si besoin d’aller plus loin**, par exemple pour :
  * intégrations spécifiques ;
  * nouvelles fonctionnalités métier ;
  * personnalisation avancée du front.

#### Combien ça coûte ?

Le socle technique et l’hébergement sont mutualisés.\
Des coûts peuvent exister pour :

* le design ou la communication spécifique ;
* des développements ou intégrations additionnelles.

***

### Migration et alimentation depuis un portail existant

Si un portail thématique existe déjà :

* l’équipe data.gouv.fr peut accompagner à la migration ;
* audit et alignement des métadonnées ;
* import automatique possible via API ou scripts.

Les producteurs publient **directement sur data.gouv.fr**. Les données apparaissent sur la verticale si elles correspondent aux filtres définis dans sa configuration. Les verticales sont automatiquement synchronisées avec data.gouv.fr. Aucune double publication n’est nécessaire.

***

### Architecture technique

#### Socle commun

* Back-office et données : **hébergés sur data.gouv.fr**
* Front-office : basé sur [**udata-front-kit**](https://github.com/opendatateam/udata-front-kit)
* API, moteur de recherche, authentification : partagés avec data.gouv.fr.

#### Configuration

Les verticales sont configurées via un **fichier YAML**, placé dans le répertoire de configuration du front kit. [Voir des exemples de configuration](https://github.com/opendatateam/udata-front-kit/tree/main/configs)

Ce fichier définit notamment :

* l’identité visuelle (logo, couleurs, favicon)
* les filtres de données (organisations, schémas, thèmes, tags)
* la page d’accueil et les contenus éditoriaux

ℹ️ [Voir la documentation complète de l'architecture de `udata-front-kit`](https://github.com/opendatateam/udata-front-kit/blob/main/doc/architecture.md) pour une explication plus approfondie du fonctionnement technique d'un portail thématique.

***

### Développement et contribution

#### Organisation du code

* Les verticales utilisent [**udata-front-kit**](https://github.com/opendatateam/udata-front-kit)
* Chaque verticale peut avoir son propre dépôt de configuration ou de personnalisation.
* Le code source de toutes les verticales est open source.

#### Proposer des fonctionnalités

* Ouvrir une **issue GitHub** sur le dépôt concerné ;
* Décrire le besoin et l’intérêt pour la communauté ;
* Les propositions sont discutées lors du **club utilisateurs** et arbitrées collectivement.
