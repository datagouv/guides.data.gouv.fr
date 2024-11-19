# Récupérer des données

Vous avez trouvé un jeu de données qui vous intéresse (cf. "[Trouver des données](trouver-des-donnees.md)") et confirmé qu’il correspondait bien à votre besoin (cf. "[Prendre connaissance et évaluer la qualité de données](prendre-connaissance-et-evaluer-la-qualite-de-donnees.md)"). Vous souhaitez désormais récupérer les données.

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
API : Outil informatique qui permet à un site internet ou à un logiciel de communiquer avec un autre ordinateur et échanger de la donnée.
{% endhint %}

Il est possible d’accéder à des données en utilisant une API. Pour cela, [**vous pouvez utiliser les API référencées sur api.gouv.fr**](https://api.gouv.fr/), une plateforme qui référence les API du service public (APIs ouvertes et APIs sous habilitation) :

* [API Adresse](https://api.gouv.fr/les-api/base-adresse-nationale) : permet d'interroger facilement la Base Adresse Nationale ;
* [API Recherche d’entreprises](https://api.gouv.fr/les-api/api-recherche-entreprises) : permet à tout le monde de rechercher et de trouver une entreprise française ;
* [API Sirene](https://api.gouv.fr/les-api/sirene\_v3) : donne accès aux informations concernant les entreprises ;
* [API Géorisques](https://api.gouv.fr/les-api/api-georisques) : permet d'afficher pour un territoire donné la liste des données et documents relatifs aux risques naturels et technologiques existants ;
* etc.

Les documentations de chaque API sont à retrouver sur leurs pages respectives sur [api.gouv.fr](http://api.gouv.fr).

## Utiliser l’API de [data.gouv.fr](http://data.gouv.fr)

Pour récupérer des données en utilisant l'API de data.gouv.fr, nous vous invitons à consulter **la documentation de la plateforme** :&#x20;

{% content-ref url="../../guide-data.gouv.fr/api-1/" %}
[api-1](../../guide-data.gouv.fr/api-1/)
{% endcontent-ref %}
