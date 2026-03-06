---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/nSrS1oz2N9yTlykjBxxZ/reutiliser-des-donnees/guide-traitement-et-analyse-de-donnees/recuperer-des-donnees
---

# Récupérer des données

Vous avez trouvé un jeu de données qui vous intéresse (cf. "[Trouver des données](trouver-des-donnees.md)") et confirmé qu’il correspondait bien à votre besoin (cf. "[Prendre connaissance et évaluer la qualité de données](prendre-connaissance-et-evaluer-la-qualite-de-donnees.md)" et "[Explorer des données](explorer-des-donnees.md)"). Vous souhaitez désormais récupérer les données.

Pour cela, il est possible de :&#x20;

<figure><img src="../../.gitbook/assets/Group 2882 (2).png" alt=""><figcaption></figcaption></figure>

## Télécharger un fichier d’un jeu de données

Sur [data.gouv.fr](http://data.gouv.fr), pour télécharger le ou les fichiers associés à un jeu de données :

* Rendez-vous sur la page du jeu de données ;
* Dans l’onglet “Fichiers” et la catégorie “Fichiers principaux”, identifiez la ressource que vous souhaitez télécharger ;
* Cliquez sur l’icône de téléchargement (flèche vers le bas) associé à la ressource.

Il est possible de télécharger la documentation associée aux données de la même manière (si elle existe), dans la catégorie “Documentation” de l’onglet “Fichiers”.

{% hint style="success" %}
Il n’est pas nécessaire de disposer d’un compte sur [data.gouv.fr](http://data.gouv.fr) pour y télécharger des données.
{% endhint %}

<figure><img src="../../.gitbook/assets/Bandeaux-[copy] (3).gif" alt=""><figcaption><p>Télécharger un fichier sur data.gouv.fr</p></figcaption></figure>

💡 Les extensions des fichiers peuvent vous donner une idée du format de fichier que vous allez télécharger :

| Type de données                          | Extensions                                       |
| ---------------------------------------- | ------------------------------------------------ |
| Données tabulaires                       | csv, xls, xlsx, ods, txt, dbf, pq                |
| Données géographiques - Données vecteurs | dwg, shp, shz, GeoJSON, kml, kmz, gpx, gpkg, dxf |
| Données géographiques - Données raster   | tiff, ecw, grib2, jp2                            |
| Fichiers en bases de données             | sql, db                                          |
| Fichiers compressés                      | tar, gz, tgz, rar, zip, 7z, xz, bz2              |
| Autres formats                           | json, xml, xsd, pdf, odt, docx                   |

## Utiliser une API

{% hint style="info" %}
API (_Application Programming Interface_) : Outil informatique qui permet à un site internet ou à un logiciel de communiquer avec un autre ordinateur et échanger de la donnée.
{% endhint %}

Les API sont un mode d'accès aux données en expansion : plutôt que de laisser l'utilisateur consulter directement des bases de données, les API proposent de formuler une requête qui est traitée par le serveur hébergeant la base de données, puis de recevoir des données en réponse à sa requête. Elles s'avèrent notamment précieuses pour récupérer de petits volumes de données, typiquement pour des interfaces interactives et récupérer des données transformées complexes, typiquement issues d'inférence de modèles (_Lino Galiana, Insee_).

La plateforme data.gouv.fr propose [**un large catalogue d'API**](https://www.data.gouv.fr/fr/dataservices/) (API ouvertes et API sous habilitation), telles que :&#x20;

* [API Adresse](https://api.gouv.fr/les-api/base-adresse-nationale) : permet d'interroger facilement la Base Adresse Nationale ;
* [API Recherche d’entreprises](https://api.gouv.fr/les-api/api-recherche-entreprises) : permet à tout le monde de rechercher et de trouver une entreprise française ;
* [API Sirene](https://api.gouv.fr/les-api/sirene_v3) : donne accès aux informations concernant les entreprises ;
* [API Géorisques](https://api.gouv.fr/les-api/api-georisques) : permet d'afficher pour un territoire donné la liste des données et documents relatifs aux risques naturels et technologiques existants ;
* etc.

Les documentations de chaque API sont à retrouver sur leurs pages respectives sur data.gouv.fr.&#x20;

{% hint style="success" %}
Pour aller plus loin, il est possible de consulter **l'**[**atelier pour découvrir la récupération de données via des API**](https://inseefrlab.github.io/ssphub-ateliers/sessions/api.html), proposé par l'Insee.
{% endhint %}

## Utiliser l’API de [data.gouv.fr](http://data.gouv.fr)

Pour récupérer des données en utilisant l'API de data.gouv.fr, nous vous invitons à consulter **la documentation de la plateforme** :&#x20;

{% content-ref url="/broken/pages/Q9seeEdFUuGFGyWy4TKX" %}
[Broken link](/broken/pages/Q9seeEdFUuGFGyWy4TKX)
{% endcontent-ref %}
