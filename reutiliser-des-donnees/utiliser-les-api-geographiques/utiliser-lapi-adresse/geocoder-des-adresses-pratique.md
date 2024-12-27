# Géocoder des adresses - cas pratiques <a href="#cas-pratiques" id="cas-pratiques"></a>

## Comment faire de l’**autocomplétion d’adresse ?** <a href="#comment-faire-de-l-autocompletion-d-adresse" id="comment-faire-de-l-autocompletion-d-adresse"></a>

Il existe plusieurs solutions pour faire de l’autocomplétion dans un outil web.

Vous pouvez vous appuyer sur de nombreuses bibliothèques, celles-ci étant généralement liées à des bibliothèques cartographiques.

#### **Solutions basées sur Leaflet**

* [https://github.com/entrepreneur-interet-general/leaflet-geocoder-ban](https://github.com/entrepreneur-interet-general/leaflet-geocoder-ban)
* [https://github.com/komoot/leaflet.photon](https://github.com/komoot/leaflet.photon)
* [https://github.com/perliedman/leaflet-control-geocoder](https://github.com/perliedman/leaflet-control-geocoder) qui implémente plusieurs geocodeurs dont "Photon" qui permet d'interagir avec l'API BAN

> **Exemples :**
>
> * [https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_control.html](https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_control.html)
> * [https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_search\_bar.html](https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_search\_bar.html)
> * [https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-leaflet-photon.html](https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-leaflet-photon.html)
> * [leaflet-control-geocoder Photon avec BAN](https://cyrille37.github.io/leaflet-control-geocoder-banfrance/demo_photon-with-ban.html)

#### **Solutions basées sur OpenLayers**

* [https://github.com/webgeodatavore/photon-geocoder-autocomplete](https://github.com/webgeodatavore/photon-geocoder-autocomplete)
* [https://viglino.github.io/ol-ext/examples/search/map.control.searchban.html](https://viglino.github.io/ol-ext/examples/search/map.control.searchban.html)

> **Exemples :**
>
> * [https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-ol.html](https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-ol.html)

#### **Solutions indépendantes de bibliothèques cartographiques**

* [https://github.com/webgeodatavore/photon-geocoder-autocomplete](https://github.com/webgeodatavore/photon-geocoder-autocomplete)

> **Exemples :**
>
> * [Exemple avec Maplibre, mais non lié à Maplibre](https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-maplibre.html)
> * [Exemple avec OpenLayers, mais non lié à OpenLayers](https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-openlayers.html)
> * [Formulaire exemple 1](https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-no-map.html)
> * [Formulaire exemple 2](https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-form-only-alternate.html)

## Comment faire du **géocodage par adresse unitaire ?** <a href="#comment-faire-du-geocodage-par-adresse-unitaire" id="comment-faire-du-geocodage-par-adresse-unitaire"></a>

Avec Python, pour faire des appels unitaires, vous pouvez :&#x20;

* **utiliser** [**le code de ce script**](https://gist.githubusercontent.com/ThomasG77/32329a8557135f11cb5656e3bfd4d35c/raw/9bd7883be31d2c9758d4393d72e9dc1ae4c5bed3/geocode-addok-unit-call.py) ;
* **passer par** [**Geopy**](https://geopy.readthedocs.io/en/stable/#installation) : il existe une [classe `BANFrance` pour ce besoin](https://geopy.readthedocs.io/en/stable/#banfrance).

En JavaScript, vous pouvez utiliser [ces exemples](https://addok.readthedocs.io/en/latest/examples/#using-javascript-client-side) que ce soit pour un usage côté navigateur ou côté serveur (Node.js/deno).

## Comment réaliser un géocodage massif ? <a href="#geocodage-massif" id="geocodage-massif"></a>

Lorsqu'on choisit cette option, on privilégie l'appel par le endpoint CSV de l'API.&#x20;

Il faut préalablement s'assurer que son CSV est bien formaté : il s'avère que le géocodage peut ponctuellement dysfonctionner si le CSV n'est pas bien formaté.

#### **Option manuelle** <a href="#option-manuelle" id="option-manuelle"></a>

Il existe une interface graphique pour envoyer des fichiers CSV sur [https://adresse.data.gouv.fr/csv](https://adresse.data.gouv.fr/csv) dont la taille maximum est de 50Mo.&#x20;

Pour tester, téléchargeons [le fichier exemple](https://gist.githubusercontent.com/ThomasG77/32329a8557135f11cb5656e3bfd4d35c/raw/9bd7883be31d2c9758d4393d72e9dc1ae4c5bed3/annuaire-des-debits-de-tabac-2018-utf8-20lines.csv) puis suivez l'exemple en utilisant le GIF animé ci-dessous.

<img src="../../../.gitbook/assets/geocodage-csv-manuel.gif" alt="">

Pour réaliser un géocodage massif, il faut généralement vérifier le formatage de votre CSV.

#### **Python seul**

* Solution partant d'appels unitaires plutôt que des appels CSV :  [https://github.com/MTES-MCT/bulk-geocoding-python-client](https://github.com/MTES-MCT/bulk-geocoding-python-client)
* Solution partant d'appels à l'API CSV. Il suffit de récupérer [le zip](https://gist.github.com/ThomasG77/32329a8557135f11cb5656e3bfd4d35c/archive/9bd7883be31d2c9758d4393d72e9dc1ae4c5bed3.zip), de décompresser le fichier. Ensuite, il vous suffit de lancer le script Python avec `python chunk-csv-python.py`. Cela permettra de faire l'appel vers l'API CSV soit en une fois, soit en plusieurs phases. On obtiendra ainsi le fichier `annuaire-des-debits-de-tabac-2018-utf8-20lines.geocoded.csv` qui est la version géocodée par l'API CSV d'un fichier de 20 lignes ainsi que `myresults.csv` qui est une version qui résulte d'une phase de découpage d'un gros fichier en plusieurs morceaux, d'appels à l'API CSV à partir de chacun de ces fichiers, puis du réassemblage des fichiers ainsi retournés. Vous n'avez plus qu'à adapter le code du fichier `chunk-csv-python.py`.
* [https://github.com/MTES-MCT/bulk-geocoding-python-client](https://github.com/MTES-MCT/bulk-geocoding-python-client) (attention, la solution fait des appels unitaires plutôt que des appels CSV)

#### **JavaScript** <a href="#javascript" id="javascript"></a>

* Géocodage massif avec une solution en ligne de commande utilisant Node.js :  [https://github.com/jdesboeufs/addok-geocode-stream](https://github.com/jdesboeufs/addok-geocode-stream)

#### **Autres outils utilisant la BAN** <a href="#autres-outils-utilisant-la-ban" id="autres-outils-utilisant-la-ban"></a>

**--> Vous faites du SIG, néophyte comme expert et utilisez le logiciel SIG QGIS ?**

* Recherchez des adresses : [https://oslandia.gitlab.io/qgis/french\_locator\_filter/](https://oslandia.gitlab.io/qgis/french\_locator\_filter/)
* Géocodez des tables depuis une table dans QGIS QBano : [https://www.data.gouv.fr/en/reuses/plugin-experimental-qbano-pour-qgis/](https://www.data.gouv.fr/en/reuses/plugin-experimental-qbano-pour-qgis/). À ce jour, le plug-in est mal maintenu, il vaut mieux récupérer [ce zip](https://labs.webgeodatavore.com/partage/QBano.zip) puis installer le plug-in depuis celui-ci.
* Avec PyQGIS, vous pouvez aussi géocoder en partant de : [https://gis.stackexchange.com/a/395415/638](https://gis.stackexchange.com/a/395415/638)

**--> Vous utilisez d’autres outils?**

* Vous faites du R ? [https://cran.r-project.org/web/packages/banR/index.html](https://cran.r-project.org/web/packages/banR/index.html)
* Vous souhaitez intégrer la recherche dans le CMS SPIP ? [http://plugins.spip.net/gisban.html](http://plugins.spip.net/gisban.html)

## Que faire lorsqu'on est un gros consommateur de l’API [api-adresse.data.gouv.fr](http://api-adresse.data.gouv.fr/) ? <a href="#gros-consommateurs-de-l-api-api-adresse-data-gouv-fr" id="gros-consommateurs-de-l-api-api-adresse-data-gouv-fr"></a>

Si vous êtes un organisme public, vous pouvez faire une demande pour augmenter les quotas par défaut sur l’API publique [api-adresse.data.gouv.fr](http://api-adresse.data.gouv.fr/).&#x20;

Si ce n’est pas le cas, vous pouvez vous autohéberger.&#x20;

* Dans ce cas, le plus simple est de passer par l’utilisation de Docker : [https://github.com/etalab/addok-docker#readme](https://github.com/etalab/addok-docker#readme).&#x20;
* Il est possible aussi de regarder du côté de Addok, le logiciel open source derrière l’API Adresse si vous avez des besoins plus spécifiques au niveau de votre installation ou de la personnalisation de la recherche : [https://github.com/addok/addok](https://github.com/addok/addok).&#x20;

## Quels autres géocodeurs est-il possible d'utiliser ? <a href="#geocodeurs-alternatifs" id="geocodeurs-alternatifs"></a>

Même si nous avons abordé l’usage du géocodeur Addok, utilisé par adresse.data.gouv.fr, il existe d'autres possibilités pour géocoder.&#x20;

Leurs principaux intérêts sont de pouvoir chercher des POIs (un centre commercial, une enseigne, etc.) ainsi que de marcher sur des données internationales, contrairement à [l'instance publique de Addok](https://adresse.data.gouv.fr/api-doc/adresse).

Il est ainsi possible d'installer des solutions OpenSource comme :&#x20;

* [Pelias](https://github.com/pelias/pelias)
* [Photon](https://github.com/komoot/photon)
* [Nominatim](https://github.com/osm-search/Nominatim)

Il est aussi possible de détourner Addok pour lui faire effectuer d’autres types de recherche, par exemple des POIs en utilisant le projet [https://github.com/osm-fr/osmpoi4addok](https://github.com/osm-fr/osmpoi4addok) par exemple.

Une instance alternative d'Addok (http://demo.addok.xyz) est mise à disposition et contient des données venant de la BANO, des POIs d'OpenStreetMap ainsi que des intersections de rues/routes.

Vous pouvez aussi vous appuyer sur les services mis à disposition par l’IGN pour le géocodage : [https://geoservices.ign.fr/services-web-experts-calcul](https://geoservices.ign.fr/services-web-experts-calcul) (voir les sections "Services de géocodage" et "Service de recherche Look4"). Vous pouvez aussi regarder [leur nouveau service de géocodage.](https://geoservices.ign.fr/documentation/services/services-beta/nouveau-service-de-geocodage-demonstrateur)
