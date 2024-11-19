---
description: Ce guide référence la doctrine des API dans les administrations.
---

# Doctrine des API



{% hint style="info" %}
### <mark style="color:blue;">Pourquoi une doctrine pour les API ?</mark>&#x20;

Élaboré par la DINUM avec les administrateurs ministériels des données, des algorithmes et des codes sources (AMDAC), ce cadre de recommandations précise le cadre d’action et identifie les bonnes pratiques à poursuivre en matière d’usage et d’exposition d’API par les administrations. L’objectif : favoriser le partage de données entre elles et ainsi faciliter les démarches des usagers.

[👉 Voir le cadre interministériel d’administration de la donnée, publié en septembre 2021](https://www.numerique.gouv.fr/actualites/donnees-algorithmes-codes-sources-mobilisation-generale-sans-precedent-15-feuilles-de-route-ministerielles/)
{% endhint %}

### 6 enjeux stratégiques

**6 enjeux stratégiques ont été identifiés afin de répondre au mieux aux besoins des utilisateurs, qu’il s’agisse d’administrations ou d’usagers, tout en s’intéressant à la gestion du service proposé.**

* [**🔭 Découvrabilité**](doctrine-des-api.md#decouvrabilite) - Catalogue de données et services disponibles
* [**🔑 Accès à la donnée**](doctrine-des-api.md#acces-a-la-donnee)
  * Gestion des habilitations d'accès aux API à accès restreint - [Reco. 3 & 4](doctrine-des-api.md#recommandation-3).
  * Bac à sable d'expérimentation public - [Reco. 5](doctrine-des-api.md#recommandation-5)
* **👷🏻‍♂️**[ **Exploitation des données**](doctrine-des-api.md#exploitation-des-donnees)
  * Utilisation des standards technologiques du moment pour faciliter l'interopérabilité - Reco. 6
  * Stabilité du modèle d'interfaces - [Reco. 7, 8 & 9](doctrine-des-api.md#recommandation-7)
* [**👌 Qualité de service**](doctrine-des-api.md#qualite-de-service)
  * Indication du temps de réponse et de la tenue en charge - [Reco. 10 & 11](doctrine-des-api.md#recommandation-10)
  * Transparence sur la disponibilité de l'API - [Reco. 12](doctrine-des-api.md#recommandation-10)
  * Suivi des consommations des données et services - [Reco. 13](doctrine-des-api.md#recommandation-13)
* [**🩺 Curation de la donnée**](doctrine-des-api.md#curation-de-la-donnee)
* [**💶 Modèle économique**](doctrine-des-api.md#modele-economique) - gratuité de la donnée et de l'exposition

***

### 🔭 Découvrabilité&#x20;

Cette partie concerne à la fois la visibilité de l'API qui doit être exposée dans les catalogues de données adéquats, ainsi que la découvrabilité de la donnée elle-même qui doit être documentée pour être réellement accessible.

#### <mark style="background-color:yellow;">**Recommandation 1**</mark>

En complément de la description, les données et services publiquement accessibles sont visibles sur un catalogue exposé sur Internet, référencé sur les moteurs de recherche usuels et intelligibles (la description des API au sein du catalogue ou de l’API manager propose un contenu destiné aux opérationnels, fonctionnels comme techniques).

La description d’une donnée doit référencer les API qui l’exposent. L’exemple ci-dessous présente les API disponibles pour la [base Sirene des entreprises et de leurs établissements](https://www.data.gouv.fr/fr/datasets/base-sirene-des-entreprises-et-de-leurs-etablissements-siren-siret/), sur la page correspondant à ce jeu de données sur data.gouv.fr :

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Exemples:

* [Data.gouv.fr/dataservices](https://www.data.gouv.fr/fr/dataservices/) (_anciennement API.gouv.fr_) vise à référencer toutes les API publiques de l’État ;
* [API Impôt Particulier](https://api.gouv.fr/les-api/impot-particulier) vise à référencer toute la verticale métier des finances publiques.
* [API Entreprise](https://entreprise.api.gouv.fr/) vise à référencer toutes les API délivrant des données administratives des entreprises et des associations. De même pour[ API Particulier](https://particulier.api.gouv.fr/), pour les données administratives des particuliers.

#### <mark style="background-color:yellow;">**Recommandation 2**</mark>

Pour chaque API exposée, sont disponibles :

* **Une documentation fonctionnelle** présentant la sémantique des données, leur qualité ainsi que leur source et leurs propriétés usuelles. Elle explicite également le processus de demande d’accès et l’éligibilité des réutilisateurs. Si un catalogue existe, un lien vers la description de la donnée est proposé ;
* **Une documentation technique** présentant les modalités d’interrogation et de récupération de la donnée ;
* **Les conditions générales d’utilisation** précisant les conditions contractuelles d’accès à l’API ;

La description d’une API décrit également **les périodes de validité de l’interface** (cf. recommandation s 7 & 8) et son niveau de service (cf. recommandations 10 & 11).

### 🔑Accès à la donnée

#### <mark style="background-color:yellow;">**Recommandation 3**</mark>

L’accès aux API à accès restreint se fait par demande du réutilisateur (administrations, éditeurs, entreprises…).

Les API peuvent s’appuyer sur un mécanisme d’authentification de l’utilisateur final assurant une gestion des droits au sein de la plateforme qui les fournit. Les dispositifs d’authentification des citoyens, des agents ou des personnes morales conçus par les pouvoirs publics pourront être utilisés, en particulier lorsque le consentement de l’utilisateur est nécessaire pour faire circuler la donnée :

* Pour les personnes physiques : FranceConnect, ProConnect, EduConnect

#### <mark style="background-color:yellow;">**Recommandation 4**</mark>

Si le droit d’accès n’est pas préétabli, le processus de demande se fait de la manière la plus simple possible pour le réutilisateur.

Dans le cadre de demandes d’accès prévues par la loi et si le demandeur est éligible, une réponse sera transmise aux réutilisateurs **dans un délai recommandé de 15 jours calendaires.** Le code des relations entre le public et l’administration prévoit un délai légal maximum de 30 jours pour répondre à une demande [(article R311-13)](https://www.legifrance.gouv.fr/codes/article\_lc/LEGIARTI000031370409).

**Ressource utile :** [🔎 DataPass : Délivrer des habilitations juridiques d'accès aux données de l'État](datapass-outil-dhabilitations.md)

#### <mark style="background-color:yellow;">**Recommandation 5**</mark>

A chaque API devrait correspondre une version “bac à sable”, accessible en fonction du caractère des données ouvertes ou en accès restreint, exposant une version fictive des données et présentant les mêmes modalités techniques d’exposition.

Pour les API ouvertes, le bac à sable potentiel est accessible au grand public, sans demande préalable du réutilisateur. Pour les API à accès restreint, le bac à sable contenant des données fictives pourrait être accessible au réutilisateur après demande d’un jeton au fournisseur de données, bien que cette pratique ne soit pas recommandée.

### 👷🏻‍♂️ Exploitation des données

#### <mark style="background-color:yellow;">**Recommandation 6**</mark>

Les données et services sont exposés selon des standards techniques communément partagés et adoptés afin de faciliter l'interopérabilité.

En 2022, le principe d’architecture et d’encodage le plus connu et pratiqué est le **standard REST Json** pour les API synchrones. Il est utilisé par exemple pour les spécifications du standard OpenAPI ([https://spec.openapis.org/oas/v3.1.0](https://spec.openapis.org/oas/v3.1.0)) ou les standards "API" de l'OGC ([https://ogcapi.ogc.org](https://ogcapi.ogc.org)). Concernant les API asynchrones, le principe AsyncAPI est le plus répandu.

> _**👍 Bonne pratique :**_ _L’approche « contract first », par opposition à l’approche « code first », est recommandée dans le développement de nouvelles interfaces car elle permet de les stabiliser et de faire travailler plusieurs équipes en parallèle au sein d’une même architecture._

#### <mark style="background-color:yellow;">**Recommandation 7**</mark>

Les données et services sont exposés selon une interface (modalités d’appel et structuration des données échangées) définie pour une période donnée.

Les développements Agile ou nécessitant une évolution prévisible seront rendus identifiables et préciseront une période de validité courte de 1 à 2 mois.

#### <mark style="background-color:yellow;">**Recommandation 8**</mark>

**Ces périodes de validité de l’interface sont explicitement présentées aux réutilisateurs dans la documentation.** Les modifications prévisibles s’accompagneront de l’actualisation préalable des informations descriptives intégrant des liens vers des communications et guides permettant aux réutilisateurs d’anticiper les évolutions.

Les réutilisateurs pourront basculer durant une période définie et communiquée sur la version modifiée de l’interface. Durant ce laps de temps, deux interfaces cohabiteront, la version précédente dépréciée et la nouvelle version.

Le détail de ces informations sera présenté en détail dans les conditions générales d’utilisation de l’API.

#### <mark style="background-color:yellow;">**Recommandation 9**</mark>

Toute modification non rétro-compatible pose un versionning en tant que version majeure et une cohabitation de l’ancien et du nouveau modèle pendant une période de recouvrement. **Celle-ci doit être communiquée à l’avance en diffusant le nouveau contrat d’interface de l’API.** A défaut d’information préalable ou d’accord des réutilisateurs, la période de cohabitation sera comprise entre 6 mois et 1 an.

Si une évolution de la donnée interdit le maintien de l’ensemble des fonctionnalités de l’API (exemple : modification d’un schéma avec abandon de certaines informations), il sera indiqué quelles requêtes ou parties du protocole seront maintenues.

### 👌 Qualité de service

#### <mark style="background-color:yellow;">**Recommandation 10**</mark>

La charge admise par une API est consultable en toute transparence par les réutilisateurs :

**1. Dans le cas d’une API authentifiée,** la charge est exprimée sous forme de métriques propres à chaque réutilisateur, comme le nombre d’appels sur une période donnée par exemple ;

**2. Dans le cas d’une API non authentifiée,** la charge tenable est exprimée dans son ensemble, tous réutilisateurs confondus ;

**3. Dans le cas d’une infrastructure permettant, via une API, des requêtes complexes, ou servant de nombreuses données,** la charge tenable estimée indiquera les critères utilisés et le caractère estimatif de cette évaluation ;

**4. Dans le cas d’une API sujette à des fortes évolutions en fonction de la saisonnalité,** le temps de réponse maximal sera précisé ainsi que les risques de rupture de service.

#### <mark style="background-color:yellow;">**Recommandation 11**</mark>

Les temps de réponse moyens et maximaux sont présentés dans la documentation de l’API. Les temps de réponse mesurés ou estimés sont fournis à titre indicatif et non contractuel. Tout autre démarche relève d’un d’accord entre le fournisseur d’API et les réutilisateurs en fonction de leurs cas d’usages.

#### <mark style="background-color:yellow;">**Recommandation 12**</mark>

L’état de l’API représente sa capacité à être appelée dans les conditions réelles par un réutilisateur. Il est rendu accessible aux réutilisateurs et consultable en temps réel sous forme d’une URL, indiquée dans la description de l’API, permettant de tester que l'API se déclare disponible et requetable. En complément, il est souhaitable de permettre de consulter un historique entre 6 mois et une année.

<details>

<summary>Exemple pour l'API Particulier</summary>

La disponibilité de l'API Particulier est accessible à cette page : [https://status.particulier.api.gouv.fr/](https://status.particulier.api.gouv.fr/)

![](../../../.gitbook/assets/image.png)

</details>

#### <mark style="background-color:yellow;">**Recommandation 13**</mark>

Les consommations des API sont enregistrées pour être ensuite restituées aux bénéficiaires (réutilisateur, producteur, API managers ou exploitants).

> _**👍 Bonne pratique :**_ _les bénéficiaires ont accès à travers un portail à une restitution en temps réel ou ponctuelle de ces statistiques de consommation des données ainsi que celles des autres bénéficiaires._

### 🩺 Curation de la donnée

#### <mark style="background-color:yellow;">**Recommandation 14**</mark>

Les réutilisateurs disposent d’un moyen technique ou organisationnel leur permettant de faire des retours sur la qualité des données vers leur gestionnaire ou via la description des données au sein de leur catalogue d’origine.

Les réutilisateurs disposent également d’un moyen technique ou organisationnel leur permettant de faire des retours sur la qualité des API exposées vers leur fournisseur ou via la description de l’API.

> 💡 _**Exemple :**_ _Le dispositif Datapass pouvant être utilisé par les API en accès restreint permet de faire un retour sur la qualité des données disponibles via celles-ci._

### 💶 Modèle économique

#### <mark style="background-color:yellow;">**Recommandation 15**</mark>

L’accès à la donnée et aux services doit être égalitaire. Les fournisseurs de données cherchent à adapter les modalités d’accès aux besoins des réutilisateurs.

#### <mark style="background-color:yellow;">**Recommandation 16**</mark>

Les données ainsi que les API sont mises à disposition gratuitement, pour les réutilisateurs uniquement, sauf exceptions devant faire l’objet d’une justification par l’administration productrice.

> 💡 _**Exemple :**_ _Dans le cas où des usages nécessiteraient une qualité de service au-dessus de ce que la multitude d’utilisateurs a couramment besoin, comme par exemple une bande passante élevée pour de la donnée temps-réel volumineuse desservie sur quelques organismes, il sera possible d’organiser un système freemium avec une égalité d’accès à des APIs par défaut et des APIs faisant l’objet de redevances pour les usages les plus exigeants._
