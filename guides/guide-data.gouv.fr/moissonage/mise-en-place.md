# Mise en place

{% tabs %}
{% tab title="DCAT" %}
### DCAT <a href="#dcat" id="dcat"></a>

[DCAT](https://www.w3.org/TR/vocab-dcat/) est une ontologie RDF pour décrire des jeux de données.

L’Europe a publié son extension de DCAT, appelée [DCAT-AP](https://joinup.ec.europa.eu/release/dcat-ap/11).

### Spécificités techniques <a href="#specificites-techniques" id="specificites-techniques"></a>

Ce moissonneur attend l’URL d’un **catalogue** DCAT (`dcat:Catalog`).

Plusieurs formats sont supportés et découvrables à travers la négociation de contenu :

* `RDF XML`
* `JSON-LD`
* `Turtle`
* `N3`
* `NT`
* `Trig`

La pagination est supportée via l’ontologie [Hydra](https://www.w3.org/community/hydra/wiki/Pagination) (ainsi que l’ancienne version)

### Correspondance des champs du modèle <a href="#correspondance-des-champs-du-modele" id="correspondance-des-champs-du-modele"></a>

Par souci de lisibilité, les namespaces suivants sont déclarés :

* `dcat` ⇨ `http://www.w3.org/ns/dcat#`
* `dct` ⇨ `http://purl.org/dc/terms/`
* `foaf` ⇨ `http://xmlns.com/foaf/0.1/`
* `hydra` ⇨ `http://www.w3.org/ns/hydra/core#`
* `rdfs` ⇨ `http://www.w3.org/2000/01/rdf-schema#`
* `scv` ⇨ `http://purl.org/NET/scovo#`
* `skos` ⇨ `http://www.w3.org/2004/02/skos/core#`
* `vcard` ⇨ `http://www.w3.org/2006/vcard/ns#`
* `xsd` ⇨ `http://www.w3.org/2001/XMLSchema#`
* `freq` ⇨ `http://purl.org/cld/freq/`

#### Jeu de données <a href="#jeu-de-donnees" id="jeu-de-donnees"></a>

La notion équivalente au jeu de données sur data.gouv.fr (`Dataset`) est un noeud de type `dcat:Dataset` en RDF.

|                          | DATA.GOUV.FR        | RDF                                                      | NOTES                                                                                                                                                                                                                                    |
| ------------------------ | ------------------- | -------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Titre                    | `title`             | `dct:title`                                              |                                                                                                                                                                                                                                          |
| Acronyme                 | `acronym`           | `skos:altLabel`                                          |                                                                                                                                                                                                                                          |
| Description              | `description`       | `dct:description` + `dct:abstract`                       | Éventuellement HTML transformé en Markdown. `dct:description` est à privilégier                                                                                                                                                          |
| Mots-clés                | `tags`              | `dcat:keyword` + `dcat:theme`                            | Les `RdfResource` ne sont pas supportées pour le champ `dcat:theme`. `dcat:keyword` est à privilégier                                                                                                                                    |
| Licence                  | `license`           | `dct:license` et `dct:right` depuis `dcat:distributions` | [Détection des licences](https://doc.data.gouv.fr/moissonnage/licences/)                                                                                                                                                                 |
| Couverture spatiale      | `spatial`           | ❌                                                        |                                                                                                                                                                                                                                          |
| Couverture temporelle    | `temporal_coverage` | `dct:temporal`                                           | Séparé par `/` dans le cas de dates de début et de fin, ex: 2011-01-01/2011-12-31                                                                                                                                                        |
| Fréquence de mise à jour | `frequency`         | `dct:accrualPeriodicity`                                 | [Dublin Core Frequency](http://dublincore.org/groups/collections/frequency/) ou un équivalent au plus proche des [Fréquences Européennes](https://publications.europa.eu/en/web/eu-vocabularies/at-dataset/-/resource/dataset/frequency) |

**Autres métadonnées**

Certaines propriétés additionnelles sont conservées dans l’attribut `harvest` par soucis de traçabilité. Les informations de date sont sauvegardées dans ces métadonnées.

|                      | DATA.GOUV.FR `HARVEST` | RDF                                                          | NOTES                                |
| -------------------- | ---------------------- | ------------------------------------------------------------ | ------------------------------------ |
| Identifiant distant  | `remote_id`            | `dct:identifier`                                             | Conservé aussi sous `dct:identifier` |
| URI                  | `uri`                  | ID du noeud                                                  | `URIRef`                             |
| URL de consultation  | `remote_url`           | `dcat:landingPage` ou l’identifier RDF s’il s’agit d’une URI |                                      |
| Date de création     | `created_at`           | `dct.issued`                                                 |                                      |
| Date de modification | `modified_at`          | `dct.modified`                                               |                                      |

#### Ressource <a href="#ressource" id="ressource"></a>

La notion équivalente à la ressource sur data.gouv.fr (`Resource`) est un noeud de type `dcat:Distribution` en RDF.

|                   | DATA.GOUV.FR  | RDF                                                       | NOTES                                          |
| ----------------- | ------------- | --------------------------------------------------------- | ---------------------------------------------- |
| Titre             | `title`       | `dct:title`                                               | Propriété facultative, un nom est généré sinon |
| Description       | `description` | `dct:description`                                         | Éventuellement HTML transformé en Markdown     |
| URL               | `url`         | `dcat:downloadURL` et `dcat:accessURL`                    | Priorité à `dcat:downloadURL`                  |
| Taille            | `filesize`    | `dcat:bytesSize`                                          |                                                |
| Type MIME         | `mime`        | `dcat:mediaType`                                          |                                                |
| Format            | `format`      | `dct:format`                                              |                                                |
| Somme de contrôle | `checksum`    | `spdx:checksum` (`spdx:algorithm` + `spdx:checksumValue`) |                                                |

**Autres métadonnées**

Certaines propriétés sont conservées dans l’attribut `harvest` par souci de traçabilité :

|                      | DATA.GOUV.FR RESOURCE `HARVEST` | RDF              | NOTES                               |
| -------------------- | ------------------------------- | ---------------- | ----------------------------------- |
| Identifiant distant  | `dct:identifier`                | `dct:identifier` |                                     |
| URI                  | `uri`                           | `dct:identifier` | Si `dct:identifier` est un `URIRef` |
| Date de création     | `created_at`                    | `dct.issued`     |                                     |
| Date de modification | `modified_at`                   | `dct.modified`   |                                     |

### Logiciels supportés <a href="#logiciels-supportes" id="logiciels-supportes"></a>

La plupart des logiciels exposant du DCAT (v1 à date) devraient être compatibles _a minima_ avec le moissonneur DCAT de data.gouv.fr. Ci-dessous quelques exemples de logiciels supportés.

#### Geonetwork <a href="#geonetwork" id="geonetwork"></a>

Si vous avez une instance de Geonetwork, vous pouvez publier sur data.gouv.fr.

En effet, il existe un endpoint DCAT alternatif au endpoint CSW habituellement utilisé comme [documenté sur la doc Geonetwork officielle](https://geonetwork-opensource.org/manuals/3.10.x/en/api/rdf-dcat.html).

Ainsi [https://geosas.fr/geonetwork/srv/fre/csw](https://geosas.fr/geonetwork/srv/fre/csw) deviendra [https://geosas.fr/geonetwork/srv/fre/rdf.search](https://geosas.fr/geonetwork/srv/fre/rdf.search) par exemple.

GeoNetwork v4 n’est pas encore supporté au moissonnage. Voir [ces discussions](https://github.com/etalab/data.gouv.fr/issues/913).

### Contribuer <a href="#contribuer" id="contribuer"></a>

Ce moissonneur fait partie du coeur de `udata`, [son code est disponible sur github](https://github.com/opendatateam/udata/blob/master/udata/harvest/backends/dcat.py). Vous pouvez donc soumettre des améliorations ou signaler des anomalies.
{% endtab %}

{% tab title="CKAN" %}
### CKAN <a href="#ckan" id="ckan"></a>

[CKAN](https://ckan.org/) est un logiciel libre permettant de mettre en oeuvre des portails de données.

Le moissonneur utilise l’API de CKAN pour récupérer les métadonnées.

### Spécifications techniques <a href="#specifications-techniques" id="specifications-techniques"></a>

Ce moissonneur attend l’URL racine de l’instance CKAN et non du portail (dans le cas où CKAN est couplé à Drupal par exemple).

Comme le moissonneur utilise l’API de CKAN, il nécessite que celle-ci soit accessible.

Ce moissonneur n’est pas compatible avec les changements de modèles qui peuvent être effectués par certains plugins. Les champs d’un jeu de données doivent rester les même, et le format de leur contenu aussi.

Les champs additionnels du modèle sont ignorés.

### Correspondance des champs du modèle <a href="#correspondance-des-champs-du-modele" id="correspondance-des-champs-du-modele"></a>

#### Jeu de données <a href="#jeu-de-donnees" id="jeu-de-donnees"></a>

La notion équivalente au jeu de données sur data.gouv.fr (`Dataset`) est le `Package` dans CKAN.

|                          | DATA.GOUV.FR        | CKAN                                             | NOTES                                                                        |
| ------------------------ | ------------------- | ------------------------------------------------ | ---------------------------------------------------------------------------- |
| Slug                     | `slug`              | `name`                                           | Création uniquement, si disponible                                           |
| Titre                    | `title`             | `title`                                          |                                                                              |
| Acronyme                 | `acronym`           | ❌                                                |                                                                              |
| Description              | `description`       | `notes`                                          |                                                                              |
| Mots-clés                | `tags`              | `tags.name`                                      |                                                                              |
| Date de création         | `created_at`        | `metadata_created`                               |                                                                              |
| Date de mise à jour      | `last_modified`     | `metadata_modified`                              |                                                                              |
| Licence                  | `license`           | `license_id` et `license_title`                  | deviné                                                                       |
| Couverture spatiale      | `spatial`           | `extras.spatial` et `extras.spatial-test`        | deviné                                                                       |
| Couverture temporelle    | `temporal_coverage` | `extras.temporal_start` et `extras.temporal_end` |                                                                              |
| Fréquence de mise à jour | `frequency`         | `extras.frequency`                               | [Dublin Core Frequency](http://dublincore.org/groups/collections/frequency/) |

**Autres métadonnées**

Certaines propriétés additionnelles sont conservées dans l’attribut `harvest` par soucis de traçabilité. Les informations de date sont sauvegardées dans ces métadonnées.

|                     | DATA.GOUV.FR `HARVEST` | CKAN   | NOTES                                       |
| ------------------- | ---------------------- | ------ | ------------------------------------------- |
| Identifiant distant | `remote_id`            | `id`   |                                             |
| Slug                | `ckan_name`            | `name` | Car `slug` peut déjà être pris              |
| URL de consultation | `remote_url`           | `url`  | Conservé dans `ckan:source` si URL invalide |

Tous les attributs `extras` de CKAN qui ne font pas l’objet d’un traitement particulier sont aussi conservés dans l’attribut `extras`.

#### Ressource <a href="#ressource" id="ressource"></a>

La notion équivalente à la ressource sur data.gouv.fr (`Resource`) est aussi la `Resource` dans CKAN.

|                     | DATA.GOUV.FR          | CKAN            | NOTES             |
| ------------------- | --------------------- | --------------- | ----------------- |
| Identifiant         | `id`                  | `id`            | Un UUID valide    |
| Titre               | `title`               | `name`          |                   |
| Description         | `description`         | `description`   |                   |
| URL                 | `url`                 | `url`           |                   |
| Type                | `filetype`            | `resource_type` | `api` ou `remote` |
| Type MIME           | `mime`                | `mimetype`      |                   |
| Format              | `format`              | `format`        |                   |
| Date de création    | `harvest.created_at`  | `created`       |                   |
| Date de mise à jour | `harvest.modified_at` | `last_modified` |                   |

### Contribuer <a href="#contribuer" id="contribuer"></a>

Le moissonneur CKAN est publié sur github dans le plugin [`udata-ckan`](https://github.com/opendatateam/udata-ckan). Vous pouvez donc soumettre des améliorations ou signaler des anomalies.
{% endtab %}

{% tab title="Opendatasoft" %}
### Opendatasoft <a href="#opendatasoft" id="opendatasoft"></a>

[Opendatasoft](https://www.opendatasoft.com/) est un service en PaaS permettant de mettre en œuvre ce qu’on appelle un datastore et le portail de données associé.

Le moissonneur utilise l’API de chaque portail Opendatasoft pour récupérer les métadonnées.

### Spécifications techniques <a href="#specifications-techniques" id="specifications-techniques"></a>

Ce moissonneur attend l’URL racine de votre portail Opendatasoft. C’est bien l’URL publique (`https://data.ma-compagnie.com`) qui est attendue, et non l’URL noire Opendatasoft (`https://ma-compagnie.opendatasoft.com`).

**Attention**: Opendatasoft utilise le slug (la portion identifiant le jeu de données dans les URLs) comme identifiant technique. L’outil laisse la possibilité de changer ce slug ce qui pose un vrai problème de pérénité des identifiants. Ayez donc à l’esprit que ce changement d’identifiant créera des doublons au moissonnage.

#### Inspire <a href="#inspire" id="inspire"></a>

Il est possible de filtrer les jeu de données identifiés comme venant d’Inspire par Opendatasoft (propriété `interop_metas.inspire`). Pour cela il suffit de cocher ou non l’option **Inspire** du moissonneur. Cela permettra d’éviter des doublons pour les jeux de données déjà moissonnés par ailleurs. Il n’y a pas de règle universelle à son usage, c’est du cas par cas et il est de votre responsabilité de vérifier si ces jeux de données sont déjà pris en charge par une autre source de moissonnage.

### Correspondance des champs du modèle <a href="#correspondance-des-champs-du-modele" id="correspondance-des-champs-du-modele"></a>

#### Jeu de données <a href="#jeu-de-donnees" id="jeu-de-donnees"></a>

|                          | DATA.GOUV.FR        | OPENDATASOFT          | NOTES                            |
| ------------------------ | ------------------- | --------------------- | -------------------------------- |
| Title                    | `title`             | `title`               |                                  |
| Acronyme                 | `acronym`           | ❌                     |                                  |
| Description              | `description`       | `description`         | HTML converti en Markdown        |
| Mots-clés                | `tags`              | `keywords` + `themes` |                                  |
| Licence                  | `license`           | `license`             | champ libre: deviné sinon `LOv2` |
| Couverture spatiale      | `spatial`           | ❌                     |                                  |
| Couverture temporelle    | `temporal_coverage` | ❌                     |                                  |
| Fréquence de mise à jour | `frequency`         | ❌                     |                                  |

**Autres métadonnées**

Certaines propriétés additionnelles sont conservées dans l’attribut `harvest` par soucis de traçabilité. Les informations de date sont sauvegardées dans ces métadonnées.

|                      | DATA.GOUV.FR `HARVEST` | OPENDATASOFT                        | NOTES                     |
| -------------------- | ---------------------- | ----------------------------------- | ------------------------- |
| Identifiant distant  | `harvest:remote_id`    | `datasetid`                         | ⚠ Attention au changement |
| URL de consultation  | `ods_url`              | `site`/explore/dataset/`datasetid`/ |                           |
| Référence interne    | `ods_reference`        | `reference`                         |                           |
| Présence de données  | `ods_has_records`      | `has_records`                       |                           |
| Données spatiales    | `ods_geo`              | `features.geo`                      |                           |
| Date de modification | `modified_at`          | `metas.modified`                    |                           |

#### Ressources <a href="#ressources" id="ressources"></a>

Il existe 3 types de ressources identifiés chez Opendatasoft :

* l’API de données qui donnera lieu à plusieurs ressource sur data.gouv.fr :
  * un export au format `CSV`
  * un export au format `JSON`
  * un export au format `GeoJSON` dans le cas de données spatiales
  * un export au format `Shapefile` dans le cas de données spatiales
* les pièces jointes (`attachments` dans l’API Opendatasoft) qui seront chacune reconnue comme une ressource
* les exports alternatifs (`alternative_exports` dans l’API Opendatasoft) qui seront chacun reconnu comme une ressource

### Contribuer <a href="#contribuer" id="contribuer"></a>

Le moissonneur Opendatasoft est publié sur github dans le plugin [`udata-ods`](https://github.com/opendatateam/udata-ods). Vous pouvez donc soumettre des améliorations ou signaler des anomalies.
{% endtab %}
{% endtabs %}
