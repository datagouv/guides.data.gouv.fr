---
hidden: true
icon: browsers
---

# Créer une verticale thématique de data.gouv.fr

### 1. Qu'est-ce que [data.gouv.fr](https://data.gouv.fr) ?

[data.gouv.fr](https://data.gouv.fr) est la plateforme nationale de la donnée publique, opérée par la DINUM.\
Elle a pour mission de permettre à tous — administrations, entreprises, chercheurs, citoyens — d’accéder, partager et réutiliser les données publiques.

La plateforme repose sur le logiciel [**udata**](https://github.com/opendatateam/udata), un projet open source maintenu en collaboration avec l’Open Data Team.

***

### 2. Qu'est-ce qu'une verticale thématique ?

Une **verticale thématique** est une **surcouche spécialisée** de data.gouv.fr :\
elle s’appuie sur la même base technique et les mêmes données, mais propose une **expérience thématique**, ciblée sur un domaine précis (écologie, transport, météo, culture, logistique, etc.).

Les verticales :

* ne dupliquent **aucune donnée** ;
* exposent des jeux de données **hébergés sur data.gouv.fr** ;
* permettent de **fédérer une communauté** autour d’un domaine spécifique ;
* offrent des **fonctionnalités avancées** adaptées à leur sujet.

Exemples actuels :

* 🌿 [ecologie.data.gouv.fr](https://ecologie.data.gouv.fr)
* ☀️ [meteo.data.gouv.fr](https://meteo.data.gouv.fr)
* 🚆 [transport.data.gouv.fr](https://transport.data.gouv.fr)
* 🎭 [culture.data.gouv.fr](https://culture.data.gouv.fr)
* [🚛 logistique.data.gouv.fr](https://logistique.data.gouv.fr)

***

### 3. Philosophie et partenariats

Les verticales sont nées d’un partenariat entre **data.gouv.fr** (DINUM) et plusieurs acteurs publics, notamment le **CGDD** (Commissariat général au développement durable, Ministère de la transition écologique) et **l’Ecolab**, dans le cadre du projet **Ecosphères**.

L’objectif :

> mutualiser une infrastructure technique commune pour créer des portails thématiques, cohérents, durables et interopérables.

***

### 4. Architecture technique

#### 4.1. Socle commun

* Back-office et données : **hébergés sur data.gouv.fr** (même instance udata).
* Front-office : basé sur [**udata-front-kit**](https://github.com/opendatateam/udata-front-kit).
* API, moteur de recherche, authentification : partagés avec data.gouv.fr.

#### 4.2. Configuration

Les verticales sont configurées via un **fichier YAML**, placé dans le répertoire de configuration du front kit :\
👉 [Exemples de configurations](https://github.com/opendatateam/udata-front-kit/tree/main/configs)

Ce fichier définit :

* l’identité visuelle (logo, couleurs, favicon)
* les filtres de données (organisations, schémas, thèmes, tags)
* la page d’accueil et les contenus éditoriaux
* les topics (playlists de données)

***

### 5. Sélection des données

Les verticales n’hébergent pas de données : elles **sélectionnent et exposent** celles déjà présentes sur data.gouv.fr.\
La sélection se fait principalement par :

* **liste d’organisations** (ministères, opérateurs, établissements publics) ;
* **tags**, **schémas** ou **thématiques** spécifiques.

Les gestionnaires peuvent également créer des **topics** (playlists de données) pour éditorialiser leur portail.

***

### 6. Personnalisation et fonctionnalités

#### 6.1. Ce qui est personnalisable

* La page d’accueil
* Les contenus éditoriaux
* Les playlists de données (topics)
* Le branding (nom, logo, bannière, couleurs)

#### 6.2. Fonctionnalités spécifiques

Chaque verticale peut ajouter des fonctionnalités propres à son domaine :

* 🔔 Notifications en temps réel pour les données de transport
* 🌦️ Recherche avancée sur les séries météorologiques
* 🧭 Visualisations ou cartes adaptées à la thématique

L’objectif est de **mutualiser le socle**, tout en **permettant des enrichissements ciblés**.

***

### 7. Gouvernance

#### 7.1. Qui peut créer une verticale ?

Le code est **ouvert à tous** : toute organisation peut créer sa verticale sur la base de data.gouv.fr.\
Cependant, pour utiliser un **domaine officiel `*.data.gouv.fr`**, il faut :

* obtenir l’accord de la **DINUM** ;
* respecter les **principes de la charte data.gouv.fr** :\
  [Charte de data.gouv.fr](https://www.data.gouv.fr/pages/legal/charter)
* signer, le cas échéant, une **convention de délégation de gestion**.

#### 7.2. Gouvernance partagée

* **DINUM / data.gouv.fr** : responsable du socle technique et du pilotage global.
* **Porteur de verticale** : responsable éditorial et fonctionnel de sa thématique.
* **Club utilisateurs** : espace d’échange entre gestionnaires de verticales et l’équipe data.gouv.fr pour co-construire les évolutions.

***

### 8. Accompagnement

#### 8.1. Qui peut accompagner ?

L’équipe **data.gouv.fr (DINUM)** accompagne les porteurs à toutes les étapes :

* cadrage du projet ;
* configuration et déploiement ;
* communication et lancement.

#### 8.2. Est-ce qu’il faut une équipe technique ?

* **Non, pas forcément.**\
  La plupart des paramètres sont configurables sans développement.
* **Oui, si besoin d’aller plus loin**, par exemple pour :
  * intégrations spécifiques ;
  * nouvelles fonctionnalités métier ;
  * personnalisation avancée du front.

#### 8.3. Coût

Le socle technique et l’hébergement sont mutualisés.\
Des coûts peuvent exister pour :

* le design ou la communication spécifique ;
* des développements ou intégrations additionnelles.

***

### 9. Migration et alimentation

#### 9.1. Migration depuis un portail existant

Si un portail thématique existe déjà :

* l’équipe data.gouv.fr peut accompagner à la migration ;
* audit et alignement des métadonnées ;
* import automatique possible via API ou scripts.

#### 9.2. Publication des données

Les producteurs publient **directement sur data.gouv.fr**.\
Les données apparaissent sur la verticale si elles correspondent aux filtres définis dans sa configuration.

#### 9.3. Synchronisation

Les verticales sont automatiquement synchronisées avec data.gouv.fr : aucune double publication n’est nécessaire.

***

### 10. Développement et contribution

#### 10.1. Organisation du code

* Les verticales utilisent [**udata-front-kit**](https://github.com/opendatateam/udata-front-kit)
* Chaque verticale peut avoir son propre dépôt de configuration ou de personnalisation.
* Le code source de toutes les verticales est open source.

#### 10.2. Proposer des fonctionnalités

* Ouvrir une **issue GitHub** sur le dépôt concerné ;
* Décrire le besoin et l’intérêt pour la communauté ;
* Les propositions sont discutées lors du **club utilisateurs** et arbitrées collectivement.

***

### 11. Gouvernance partagée et communauté

Les verticales et data.gouv.fr forment un **bouquet cohérent** :\
un écosystème d’instances reliées, partageant une même infrastructure, un design homogène et une gouvernance ouverte.

Le **club utilisateurs** réunit régulièrement les gestionnaires de verticales et l’équipe data.gouv.fr pour :

* partager les retours d’expérience ;
* décider des priorités de développement ;
* mutualiser les outils et bonnes pratiques.

***

### 12. Verticales existantes

| Nom                                                      | Thématique                                       | Porteur                                 |
| -------------------------------------------------------- | ------------------------------------------------ | --------------------------------------- |
| [transport.data.gouv.fr](https://transport.data.gouv.fr) | Mobilité et transport public                     | DINUM / Ministère chargé des Transports |
| [ecologie.data.gouv.fr](https://ecologie.data.gouv.fr)   | Données environnementales                        | CGDD / Ecolab                           |
| [meteo.data.gouv.fr](https://meteo.data.gouv.fr)         | Données climatiques et météorologiques           | Météo-France / DINUM                    |
| [culture.data.gouv.fr](https://culture.data.gouv.fr)     | Données culturelles                              | Ministère de la Culture / DINUM         |
| [logistique.dtg](https://logistique.dtg)                 | Données logistiques et transport de marchandises | DINUM / DGITM                           |

***

### 13. FAQ

**Puis-je créer ma propre verticale ?**\
Oui, le code est ouvert. Pour utiliser un domaine officiel `*.data.gouv.fr`, une validation de la DINUM est nécessaire.

**Ai-je besoin d’un développeur ?**\
Non, pour une configuration standard ; oui, pour des fonctionnalités avancées.

**Combien de temps pour la mise en place ?**\
Quelques jours à quelques semaines selon la complexité et la disponibilité des données.

**Puis-je ajouter des données locales ?**\
Oui, à condition qu’elles soient publiées sur data.gouv.fr.

**Comment rejoindre la communauté ?**\
En contactant l’équipe data.gouv.fr et en participant au club utilisateurs.
