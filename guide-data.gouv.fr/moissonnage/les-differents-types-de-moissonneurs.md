# Les différents types de moissonneurs

## Les différents moissonneurs

Aujourd’hui, data.gouv.fr peut moissonner les plateformes ou formats suivants :

* **DCAT** (GeoNetwork, OpenDataSoft, etc.)
* **CKAN**
* **DKAN**, une variante du moissonneur CKAN

{% tabs %}
{% tab title="DCAT" %}
### DCAT <a href="#dcat" id="dcat"></a>

[DCAT](https://www.w3.org/TR/vocab-dcat/) est un vocabulaire RDF pour décrire des jeux de données. La Commission européenne a publié son extension de DCAT, appelée [DCAT-AP](https://joinup.ec.europa.eu/release/dcat-ap/11).

#### Spécificités techniques <a href="#specificites-techniques" id="specificites-techniques"></a>

Ce moissonneur attend l’URL d’un **catalogue** DCAT (`dcat:Catalog`).

Plusieurs formats sont supportés et découvrables à travers la négociation de contenu :

* `RDF XML`
* `JSON-LD`
* `Turtle`
* `N3`
* `NT`
* `Trig`

La pagination est supportée via l’ontologie [Hydra](https://www.w3.org/community/hydra/wiki/Pagination) (ainsi que l’ancienne version).

#### Correspondance des champs du modèle <a href="#correspondance-des-champs-du-modele" id="correspondance-des-champs-du-modele"></a>

**Jeu de données**

La notion équivalente au jeu de données sur data.gouv.fr (`Dataset`) est un noeud de type `dcat:Dataset` en RDF.

<table><thead><tr><th width="128"></th><th width="148">DATA.GOUV.FR</th><th width="186">RDF</th><th>NOTES</th></tr></thead><tbody><tr><td>Titre</td><td><code>title</code></td><td><code>dct:title</code></td><td></td></tr><tr><td>Acronyme</td><td><code>acronym</code></td><td><code>skos:altLabel</code></td><td></td></tr><tr><td>Description</td><td><code>description</code></td><td><code>dct:description</code> + <code>dct:abstract</code></td><td>Éventuellement HTML transformé en Markdown. <code>dct:description</code> est à privilégier</td></tr><tr><td>Mots-clés</td><td><code>tags</code></td><td><code>dcat:keyword</code> + <code>dcat:theme</code></td><td>Les <code>RdfResource</code> ne sont pas supportées pour le champ <code>dcat:theme</code>. <code>dcat:keyword</code> est à privilégier</td></tr><tr><td>Licence</td><td><code>license</code></td><td><code>dct:license</code> et <code>dct:right</code> depuis <code>dcat:distributions</code></td><td><a href="les-differents-types-de-moissonneurs.md#detection-des-licences-par-le-moissonnage">Détection des licences</a></td></tr><tr><td>Couverture spatiale</td><td><code>spatial > geom</code></td><td><code>DCT.spatial</code></td><td>Uniquement les couverture géométriques sont supportées pour l'instant. Soit un Polygon en tant que littéral WKT (<a href="https://w3c.github.io/dxwg/dcat/#ex-spatial-coverage-geometry">exemple</a>), soit un GeoJSON directement (datatype <code>application/vnd.geo+json</code>).</td></tr><tr><td>Granularité géographique</td><td><code>spatial > granularity</code></td><td>❌</td><td>Non supporté</td></tr><tr><td>Couverture temporelle</td><td><code>temporal_coverage</code></td><td><code>dct:temporal</code></td><td>Séparé par <code>/</code> dans le cas de dates de début et de fin, ex: 2011-01-01/2011-12-31</td></tr><tr><td>Fréquence de mise à jour</td><td><code>frequency</code></td><td><code>dct:accrualPeriodicity</code></td><td><a href="http://dublincore.org/groups/collections/frequency/">Dublin Core Frequency</a> ou un équivalent au plus proche des <a href="https://publications.europa.eu/en/web/eu-vocabularies/at-dataset/-/resource/dataset/frequency">Fréquences Européennes</a></td></tr></tbody></table>

**Autres métadonnées**

Certaines propriétés additionnelles sont conservées dans l’attribut `harvest` par soucis de traçabilité. Les informations de date sont sauvegardées dans ces métadonnées.

<table><thead><tr><th width="149"></th><th width="243">DATA.GOUV.FR HARVEST</th><th width="127">RDF</th><th>NOTES</th></tr></thead><tbody><tr><td>Identifiant distant</td><td><code>remote_id</code></td><td><code>dct:identifier</code></td><td>Conservé aussi sous <code>dct:identifier</code></td></tr><tr><td>URI</td><td><code>uri</code></td><td>ID du noeud</td><td><code>URIRef</code></td></tr><tr><td>URL de consultation</td><td><code>remote_url</code></td><td><code>dcat:landingPage</code> ou l’identifier RDF s’il s’agit d’une URI</td><td></td></tr><tr><td>Date de création</td><td><code>created_at</code></td><td><code>dct.issued</code></td><td></td></tr><tr><td>Date de modification</td><td><code>modified_at</code></td><td><code>dct.modified</code></td><td></td></tr></tbody></table>

**Ressource**

La notion équivalente à la ressource sur data.gouv.fr (`Resource`) est un noeud de type `dcat:Distribution` en RDF.

<table><thead><tr><th width="140"></th><th>DATA.GOUV.FR</th><th>RDF</th><th>NOTES</th></tr></thead><tbody><tr><td>Titre</td><td><code>title</code></td><td><code>dct:title</code></td><td>Propriété facultative, un nom est généré sinon</td></tr><tr><td>Description</td><td><code>description</code></td><td><code>dct:description</code></td><td>Éventuellement HTML transformé en Markdown</td></tr><tr><td>URL</td><td><code>url</code></td><td><code>dcat:downloadURL</code> et <code>dcat:accessURL</code></td><td>Priorité à <code>dcat:downloadURL</code></td></tr><tr><td>Taille</td><td><code>filesize</code></td><td><code>dcat:byteSize</code></td><td></td></tr><tr><td>Type MIME</td><td><code>mime</code></td><td><code>dcat:mediaType</code></td><td></td></tr><tr><td>Format</td><td><code>format</code></td><td><code>dct:format</code></td><td></td></tr><tr><td>Somme de contrôle</td><td><code>checksum</code></td><td><code>spdx:checksum</code> (<code>spdx:algorithm</code> + <code>spdx:checksumValue</code>)</td><td></td></tr></tbody></table>

**Autres métadonnées**

Certaines propriétés sont conservées dans l’attribut `harvest` par souci de traçabilité :

<table><thead><tr><th width="173"></th><th>DATA.GOUV.FR RESOURCE HARVEST</th><th>RDF</th><th>NOTES</th></tr></thead><tbody><tr><td>Identifiant distant</td><td><code>dct:identifier</code></td><td><code>dct:identifier</code></td><td></td></tr><tr><td>URI</td><td><code>uri</code></td><td><code>dct:identifier</code></td><td>Si <code>dct:identifier</code> est un <code>URIRef</code></td></tr><tr><td>Date de création</td><td><code>created_at</code></td><td><code>dct.issued</code></td><td></td></tr><tr><td>Date de modification</td><td><code>modified_at</code></td><td><code>dct.modified</code></td><td></td></tr></tbody></table>

#### Logiciels supportés <a href="#logiciels-supportes" id="logiciels-supportes"></a>

La plupart des logiciels exposant du DCAT (v3 à date) devraient être compatibles _a minima_ avec le moissonneur DCAT de data.gouv.fr. Ci-dessous quelques exemples de logiciels supportés.

**GeoNetwork**

Si vous avez une instance de Geonetwork, vous pouvez publier sur data.gouv.fr.

Une documentation détaillée est précisée sur la [page du moissonnage des données géographiques](moissonnage-des-plateformes-geographiques.md#configurer-un-portail-geonetwork).

**OpenDataSoft**

[Opendatasoft](https://www.opendatasoft.com/) est un service en PaaS permettant de mettre en œuvre ce qu’on appelle un datastore et le portail de données associé.

Le moissonneur utilise l'export au format DCAT de chaque portail OpenDataSoft pour récupérer les métadonnées.

**Spécifications techniques** : Ce moissonneur attend l’URL publique d'export DCAT de votre portail Opendatasoft. Ce sera par exemple `https://data.ma-compagnie.com/api/explore/v2.1/catalog/exports/dcat/`. Il est possible (et souvent nécessaire) de renseigner dans l'URL les filtres des jeux de données cibles à moissonner (afin par exemple de moissonner les jeux de données du producteur X avec le mot clé Y). Vous trouverez plus d'information sur la mise en place d'un moissonneur DCAT pour un portail OpenDataSoft sur la [documentation dédiée d'OpenDataSoft](https://user-guide.opendatasoft.com/fr/articles/2032322).

**Attention**: OpenDataSoft utilise le slug (la portion identifiant le jeu de données dans les URLs) comme identifiant technique. L’outil laisse la possibilité de changer ce slug ce qui pose un vrai problème de pérennité des identifiants. Ayez donc à l’esprit que ce changement d’identifiant créera des doublons au moissonnage.

**Isogeo**

Les portails Isogeo exposent du DCAT et sont donc moissonnables par data.gouv.fr.

Cette [documentation officielle](https://help.isogeo.com/admin/fr/features/publish/harvest_datagouv_fr.html) explique en détail la mise en place d’un moissonneur DCAT pour un portail Isogeo.

#### Namespaces utilisés <a href="#correspondance-des-champs-du-modele" id="correspondance-des-champs-du-modele"></a>

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

#### Contribuer <a href="#contribuer" id="contribuer"></a>

Ce moissonneur fait partie du coeur de `udata`, [son code est disponible sur github](https://github.com/opendatateam/udata/blob/master/udata/harvest/backends/dcat.py). Vous pouvez donc soumettre des améliorations ou signaler des anomalies.
{% endtab %}

{% tab title="CKAN" %}
### CKAN <a href="#ckan" id="ckan"></a>

[CKAN](https://ckan.org/) est un logiciel libre permettant de mettre en oeuvre des portails de données.

Le moissonneur utilise l’API de CKAN pour récupérer les métadonnées.

#### Spécifications techniques <a href="#specifications-techniques" id="specifications-techniques"></a>

Ce moissonneur attend l’URL racine de l’instance CKAN et non du portail (dans le cas où CKAN est couplé à Drupal par exemple).

Comme le moissonneur utilise l’API de CKAN, il nécessite que celle-ci soit accessible.

Ce moissonneur n’est pas compatible avec les changements de modèles qui peuvent être effectués par certains plugins. Les champs d’un jeu de données doivent rester les mêmes, et le format de leur contenu aussi.

Les champs additionnels du modèle sont ignorés.

#### Correspondance des champs du modèle <a href="#correspondance-des-champs-du-modele" id="correspondance-des-champs-du-modele"></a>

**Jeu de données**

La notion équivalente au jeu de données sur data.gouv.fr (`Dataset`) est le `Package` dans CKAN.

<table><thead><tr><th width="137"></th><th width="161">DATA.GOUV.FR</th><th width="216">CKAN</th><th>NOTES</th></tr></thead><tbody><tr><td>Slug</td><td><code>slug</code></td><td><code>name</code></td><td>Création uniquement, si disponible</td></tr><tr><td>Titre</td><td><code>title</code></td><td><code>title</code></td><td></td></tr><tr><td>Acronyme</td><td><code>acronym</code></td><td>❌</td><td></td></tr><tr><td>Description</td><td><code>description</code></td><td><code>notes</code></td><td></td></tr><tr><td>Mots-clés</td><td><code>tags</code></td><td><code>tags.name</code></td><td></td></tr><tr><td>Date de création</td><td><code>created_at</code></td><td><code>metadata_created</code></td><td></td></tr><tr><td>Date de mise à jour</td><td><code>last_modified</code></td><td><code>metadata_modified</code></td><td></td></tr><tr><td>Licence</td><td><code>license</code></td><td><code>license_id</code> et <code>license_title</code></td><td>deviné</td></tr><tr><td>Couverture spatiale</td><td><code>spatial</code></td><td><code>extras.spatial</code> et <code>extras.spatial-test</code></td><td>deviné</td></tr><tr><td>Couverture temporelle</td><td><code>temporal_coverage</code></td><td><code>extras.temporal_start</code> et <code>extras.temporal_end</code></td><td></td></tr><tr><td>Fréquence de mise à jour</td><td><code>frequency</code></td><td><code>extras.frequency</code></td><td><a href="http://dublincore.org/groups/collections/frequency/">Dublin Core Frequency</a></td></tr></tbody></table>

**Autres métadonnées**

Certaines propriétés additionnelles sont conservées dans l’attribut `harvest` par soucis de traçabilité. Les informations de date sont sauvegardées dans ces métadonnées.

<table><thead><tr><th width="149"></th><th>DATA.GOUV.FR HARVEST</th><th width="105">CKAN</th><th>NOTES</th></tr></thead><tbody><tr><td>Identifiant distant</td><td><code>remote_id</code></td><td><code>id</code></td><td></td></tr><tr><td>Slug</td><td><code>ckan_name</code></td><td><code>name</code></td><td>Car <code>slug</code> peut déjà être pris</td></tr><tr><td>URL de consultation</td><td><code>remote_url</code></td><td><code>url</code></td><td>Conservé dans <code>ckan:source</code> si URL invalide</td></tr></tbody></table>

Tous les attributs `extras` de CKAN qui ne font pas l’objet d’un traitement particulier sont aussi conservés dans l’attribut `extras`.

**Ressource**

La notion équivalente à la ressource sur data.gouv.fr (`Resource`) est aussi la `Resource` dans CKAN.

<table data-full-width="true"><thead><tr><th width="127"></th><th>DATA.GOUV.FR</th><th>CKAN</th><th>NOTES</th></tr></thead><tbody><tr><td>Identifiant</td><td><code>id</code></td><td><code>id</code></td><td>Un UUID valide</td></tr><tr><td>Titre</td><td><code>title</code></td><td><code>name</code></td><td></td></tr><tr><td>Description</td><td><code>description</code></td><td><code>description</code></td><td></td></tr><tr><td>URL</td><td><code>url</code></td><td><code>url</code></td><td></td></tr><tr><td>Type</td><td><code>filetype</code></td><td><code>resource_type</code></td><td><code>api</code> ou <code>remote</code></td></tr><tr><td>Type MIME</td><td><code>mime</code></td><td><code>mimetype</code></td><td></td></tr><tr><td>Format</td><td><code>format</code></td><td><code>format</code></td><td></td></tr><tr><td>Date de création</td><td><code>harvest.created_at</code></td><td><code>created</code></td><td></td></tr><tr><td>Date de mise à jour</td><td><code>harvest.modified_at</code></td><td><code>last_modified</code></td><td></td></tr></tbody></table>

### Filtrage <a href="#filtrage" id="filtrage"></a>

La filtrage donne la possibilité d’inclure ou d’exclure un sous-ensemble de jeux de données du moissonnage.

Lorsqu’un ou plusieurs filtres sont déclarés, seuls les jeux de données remplissant **toutes** les conditions (**ET**) seront traités.

#### **Portail multiproducteur : restriction à une organisation**

![Exemple de restriction à une seule organisation](https://doc.data.gouv.fr/img/moissonnage/harvest-filter-include.png)

#### **Exclusion de mots-clés**

![Exemple d'exclusion de mots-clés](https://doc.data.gouv.fr/img/moissonnage/harvest-filter-exclude.png)

#### **Combinaisons multiples**

![Exemple de combinaison de filtres](https://doc.data.gouv.fr/img/moissonnage/harvest-filter-combined.png)

#### Contribuer <a href="#contribuer" id="contribuer"></a>

Le moissonneur CKAN est publié sur github dans le plugin [`udata-ckan`](https://github.com/opendatateam/udata-ckan). Vous pouvez donc soumettre des améliorations ou signaler des anomalies.
{% endtab %}
{% endtabs %}

#### Métadonnées communes <a href="#metadonnees-communes" id="metadonnees-communes"></a>

Les jeux de données moissonnés possèdent les attributs suivants dans leur champ `extras` pour la traçabilité :

| ATTRIBUT              | CONTENU                               |
| --------------------- | ------------------------------------- |
| `harvest:domain`      | Nom de domaine moissonné              |
| `harvest:source_id`   | Identifiant technique du moissonneur  |
| `harvest:remote_id`   | Identifiant distant du jeu de données |
| `harvest:last_update` | Date du dernier moissonnage           |

## Détection des licences par le moissonnage

Lors du moissonnage, la liste de référence de data.gouv.fr, [disponible ici au format json](https://www.data.gouv.fr/api/1/datasets/licenses/), est utilisée pour détecter la licence du jeu de données distant.

Cette détection utilise les attributs suivants :

* `id`
* `title`
* `alternate_titles`
* `url`
* `alternate_urls`

Le meilleur moyen d’assurer une compatibilité parfaite est d’utiliser l’`id` sur le flux distant lorsque c’est possible.
