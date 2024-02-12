# Prendre en main l'API "Adresse" portée par l'IGN

Ce guide a vocation à accompagner les utilisateurs de l'API "Adresse", dans le cadre de son transfert de la DINUM à l'IGN.

Il présente :&#x20;

* [Le transfert de l'API "Adresse" de la Base Adresse Nationale, de la DINUM à l'IGN](prendre-en-main-lapi-adresse-portee-par-lign.md#transfert-de-lapi-adresse-de-la-base-adresse-nationale-de-la-dinum-a-lign) ;
* [Les modalités d’évaluation de l’API “Adresse” portée par l’IGN](prendre-en-main-lapi-adresse-portee-par-lign.md#modalites-devaluation-de-lapi-adresse-portee-par-lign) ;
* [Comment utiliser l'API "Adresse" portée par l'IGN et les différences avec l'API "Adresse" portée par la DINUM](prendre-en-main-lapi-adresse-portee-par-lign.md#utilisation-de-lapi-adresse-portee-par-lign-et-les-differences-avec-lapi-adresse-portee-par-la-dinum).

## Transfert de l’API “Adresse” de la Base Adresse Nationale, de la DINUM à l’IGN

La Base Adresse Nationale (BAN) est la base de données ouverte d’adresses officiellement reconnues par l’administration. Elle figure parmi les 9 données de référence du [service public de la donnée](https://www.data.gouv.fr/fr/pages/spd/reference/).

Elle est disponible en téléchargement et via une API ([licence ouverte Etalab 2.0](https://www.etalab.gouv.fr/wp-content/uploads/2017/04/ETALAB-Licence-Ouverte-v2.0.pdf)) sur :

* [adresse.data.gouv.fr](https://adresse.data.gouv.fr/)
* [www.data.gouv.fr/fr/datasets/base-adresse-nationale](https://www.data.gouv.fr/fr/datasets/base-adresse-nationale/)

L’API “Adresse” adossée à la BAN était initialement opérée par la Direction interministérielle du numérique (DINUM).

**Elle a entamé en décembre 2023 sa transition pour être dorénavant gérée par l’Institut de l’information géographique et forestière (IGN) au sein de la Géoplateforme.** Elle rejoint ainsi les API géographiques de l’IGN. Ce transfert garantit l’intégration de nouvelles fonctionnalités telles que la recherche par points d’intérêt (POI) et selon les parcelles cadastrales.

Ce nouveau portage s’inscrit dans le cadre du transfert de la BAN initié en mars 2022, de la DINUM à l’IGN.

{% hint style="info" %}
**Geoplateforme** : Espace public de l’information géographique visant à optimiser la production et la diffusion des géodatas au service de la décision publique.
{% endhint %}

Une période minimum de transition est mise en place pendant les 6 premiers mois de l’année 2024, au cours de laquelle “l’API DINUM” et “l’API IGN” coexisteront. **A partir du début 2024, l’IGN sera le point de contact principal pour les questions relatives à l’API “Adresse”.**

## Modalités d’évaluation de l’API “Adresse” portée par l’IGN

Dans le cadre du transfert, les performances de l’API « Adresse » gérée par l’IGN seront évaluées par la DINUM 3 mois après la mise en production : le service doit être iso-fonctionnel avec l’API “Adresse” de la DINUM.

Si cet audit s’avère satisfaisant, l’API BAN de la DINUM sera décommissionnée mi-2024.

L’évaluation sera réalisée selon le protocole suivant :

### **Documentation**

* Code publié en open source[https://gitlab.gpf-tech.ign.fr/geoplateforme/geocodage/geocodeur/](https://gitlab.gpf-tech.ign.fr/geoplateforme/geocodage/geocodeur/)
* Documentation claire sur les réglages effectués sur Addok (joue sur le ranking et le scoring)

Actuellement on a `addok.conf` qui contient

```python
ATTRIBUTION = "BAN"
LICENCE = "ETALAB-2.0"
EXTRA_FIELDS = [
    {"key": "citycode"},
    {"key": "oldcitycode"},
    {"key": "oldcity"},
    {"key": "district"},
]
FILTERS = ["type", "citycode", "postcode"]
QUERY_PROCESSORS_PYPATHS = [
    "addok.helpers.text.check_query_length",
    "addok_france.extract_address",
    "addok_france.clean_query",
    "addok_france.remove_leading_zeros",
]
SEARCH_RESULT_PROCESSORS_PYPATHS = [
    "addok.helpers.results.match_housenumber",
    "addok_france.make_labels",
    "addok.helpers.results.score_by_importance",
    "addok.helpers.results.score_by_autocomplete_distance",
    "addok.helpers.results.score_by_ngram_distance",
    "addok.helpers.results.score_by_geo_distance",
]
PROCESSORS_PYPATHS = [
    "addok.helpers.text.tokenize",
    "addok.helpers.text.normalize",
    "addok_france.glue_ordinal",
    "addok_france.fold_ordinal",
    "addok_france.flag_housenumber",
    "addok.helpers.text.synonymize",
    "addok_fr.phonemicize",
]
SQLITE_DB_PATH = '/home/debian/addok-data/addok.db'
```

* Documentation détaillée de l’architecture pour la possibilité d’un déploiement iso par un tiers [https://gitlab.gpf-tech.ign.fr/geoplateforme/geocodage/geocodeur/-/blob/main/docs/user/installation.md](https://gitlab.gpf-tech.ign.fr/geoplateforme/geocodage/geocodeur/-/blob/main/docs/user/installation.md)

### **Gouvernance**

* Maintenance du code et des dépendances de l’API (pérennité) : quelle réactivité suite aux sollicitations de la communauté ?
* Organisation mise en place
* Nom de domaine de l’API simple à utiliser « [sous-domaine.domaine.ign.fr](http://sous-domaine.domaine.ign.fr) »:
* Gestion des droits spéciaux : comment sont gérés les droits des tiers de confiance dont on lève la limitation de consommation
* Evaluation du coût d’hébergement de l’API
* Vérification que la fréquence de mise à jour des données et sources soit a minima hebdomadaire

### **Migration**

* Evaluation des modifications des payloads de l’API actuelle pour assurer la continuité de service
* Routes disponibles :
  * Adresse unitaire
  * Geocoding CSV
* Evaluation du parsing CSV (actuellement, l’API BAN effectue un pré-traitement de données avant appel à Addok)
* Suivi de la migration des gros acteurs publics (ANTS, Ameli, Pôle Emploi, etc.)

### **Performance de l’API**

* Evaluation de la tenue de la charge de l’API : doit pouvoir atteindre plusieurs centaines de millions d’appels par mois
* Temps de réponse moyen d’un appel unitaire inférieur à 100ms
* Nombre, durée des incidents, temps de rétablissement et/ou redéploiement du fait de la criticité de l’API

## Utilisation de l’API “Adresse” portée par l’IGN et les différences avec l’API “Adresse” portée par la DINUM

**L’API “Adresse” portée par l’IGN est rétrocompatible/iso-fonctionnelle avec celle jusqu’alors portée par la DINUM** pour la recherche via les points d’entrée `/search/` et `/reverse/` qui se font en GET.

**Nous vous invitons donc à consulter la documentation “**[**Utiliser l’API Adresse**](utiliser-les-api-geographiques/utiliser-lapi-adresse/)**” des guides de** [**data.gouv.fr**](http://data.gouv.fr)**.**

{% hint style="danger" %}
**La fonction géocodage CSV fortement utilisée n’est pas implémentée et reste un point majeur pour la rétrocompatibilité avec les fonctionnalités existantes.**
{% endhint %}

Des fonctionnalités ont été rajoutées mais elles ne concernent pas la recherche d’adresse à l’exception très limitée de rechercher par nom de commune avec l’option `city` qui fonctionne sur les `address` et les `poi`.

Elle supporte les options historiques :

* `limit`
* `autocomplete`
* `lat` et `lon`
* `type`
* `postcode`
* `citycode`

Il est possible de rechercher des POIs ou des parcelles en passant par l’option `index`. On peut combiner les options que sont `parcel`, `poi` et `address`.

Les options `postcode` et `citycode` fonctionnent aussi avec l’index des `poi` et pas seulement avec les `address`.

### **Spécifique à la recherche de POIs**

`category`: Il faut passer par les options relatives à `category` dans le `getCapabilities` disponible sur [https://data.geopf.fr/geocodage/getCapabilities](https://data.geopf.fr/geocodage/getCapabilities) pour connaître les possibilités de filtre.

> Exemple : [https://data.geopf.fr/geocodage/search?index=poi\&q=nantes\&category=administratif\&returntruegeometry=true](https://data.geopf.fr/geocodage/search?index=poi\&q=nantes\&category=administratif\&returntruegeometry=true)

### **Spécifique à la recherche de parcelles**

* `departmentcode`
* `municipalitycode`
* `oldmunicipalitycode`
* `districtcode`
* `section`
* `number`
* `sheet`

> Exemple : [https://data.geopf.fr/geocodage/search?index=parcel\&departmentcode=44\&municipalitycode=109\&section=EX\&number=8\&returntruegeometry=true](https://data.geopf.fr/geocodage/search?index=parcel\&departmentcode=44\&municipalitycode=109\&section=EX\&number=8\&returntruegeometry=true)

### **Autres remarques**

Il existe une option `returntruegeometry` assez intéressante mais encore plutôt inconsistante (elle est sérialisée ou pas selon le type d’index)

* Pour les parcelles : elle présente l’avantage de retourner la géométrie polygonale. Attention, cette géométrie est une propriété dans le GeoJSON retourné. La géométrie reste un point par ailleurs.
* Pour les POIs : on retourne la chaine échappée de la géométrie polygonale et comme pour les parcelles, le GeoJSON reste de type point.
* Pour les adresses : l’intérêt est limité, on retourne la chaine échappée de la géométrie ponctuelle qui est déjà dans le GeoJSON retourné.
