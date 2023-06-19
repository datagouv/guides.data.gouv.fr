# Géocoder des adresses

## Qu'est-ce que le géocodage ?

{% hint style="info" %}
**Lexique : Géocodage**\
Le géocodage consiste à affecter des coordonnées géographiques (longitude/latitude) à une adresse postale (Wikipédia).

Il permet ainsi de positionner des adresses sur une carte ou encore de trouver les points de départ et d’arrivée pour déterminer votre trajet lorsque vous voyagez par exemple.
{% endhint %}

### Les indispensables pour réaliser un géocodage

Pour réaliser un géocodage, il est nécessaire de disposer :

* [ ] des **données de référence** contenant numéro, nom de rue, [code INSEE](https://www.data.gouv.fr/en/datasets/code-officiel-geographique-cog/), code postal, nom de commune ;
* [ ] des **coordonnées géographiques** x et y qui sont généralement la longitude(x) et la latitude(y) ;
* [ ] une **entrée correspondant à l’adresse recherchée**.

### Le fonctionnement d'un géocodeur <a href="#comment-fonctionne-un-geocodeur" id="comment-fonctionne-un-geocodeur"></a>

Un géocodeur transforme une donnée textuelle des données de référence en utilisant des algorithmes qui séparent l’adresse en syllabes, mots et groupes de mots.

Les différents éléments sont indexés, puis en s’appuyant sur des algorithmes relatifs à du traitement textuel, le géocodeur compare la similarité entre les mots constituant l’adresse à rechercher et ceux qui sont indexés depuis les données de référence.

Un algorithme permet généralement d’ordonner les résultats. Il s’agit par exemple de faire apparaitre en premier les résultats ayant les coordonnées fixes les plus proches ou encore ceux dont la population est la plus forte.

Il est également possible de filtrer selon des critères comme le pays (si le géocodeur a une vocation internationale, comme [Nominatim](https://nominatim.openstreetmap.org/)) ou encore par type de résultat.

En pratique, un certain nombre de géocodeurs visent à réaliser des recherches de communes et de POIs (Points Of Interest ou points d’intérêts) et pas seulement des adresses.

Le **géocodage peut aussi se faire de façon inverse**, c’est-à-dire retourner une adresse en envoyant une coordonnée. Dans ce cas de figure, il s’agit de trouver la donnée de référence la plus proche des coordonnées envoyées.

### Les limites du géocodage <a href="#les-limites-du-geocodage" id="les-limites-du-geocodage"></a>

Nous nous concentrons ici sur les cas liés aux adresses, le géocodeur utilisé par [adresse.data.gouv.fr](http://adresse.data.gouv.fr/) étant spécifiquement conçu pour répondre à ce besoin.

**La qualité des données de référence**

Les données textuelles de l’adresse de référence ne sont pas toujours uniformes.&#x20;

> Exemple : "rue" peut être représenté par les lettres "r" ou "R" ou "rue" ou "Rue".

Il s’agit donc en premier lieu d’uniformiser les différentes manières de décrire le type de voie.

Il s’agit également d’omettre les articles lors d’une comparaison.&#x20;

> Exemple : chercher "rue métanies" au lieu de "rue des métanies".

D’un autre côté, les coordonnées géographiques peuvent manquer de précision. Dans certains cas, il arrive de disposer uniquement du centroïde de la commune, de la voie ou du lieu dit (point d’une zone géographique choisi au voisinage de son centre de gravité et dont les coordonnées servent de localisant pour cette zone).

Dans d’autres cas, les coordonnées peuvent avoir été interpolées : les adresses ont été positionnées en fonction du nombre de numéros dans une voie et la longueur de celle-ci.

#### Les principales problématiques liées aux adresses

<details>

<summary><strong>Plusieurs communes pour un code postal</strong>.</summary>

Cette problématique se pose par exemple lorsqu’on met le nom de la commune dans une adresse. En effet, 68,9% des codes postaux sont associés à plus d’une commune et jusqu’à 46 communes sont rattachées à un même code postal.

</details>

<details>

<summary><strong>Plusieurs codes postaux pour une commune</strong>.</summary>

1,5% des communes ont plus d’un seul code postal sur leur territoire. On compte même jusqu’à 9 codes postaux pour une même commune pour le cas extrême !

</details>

<details>

<summary><strong>Des communes ont des noms identiques</strong>.</summary>

10,6% des communes ont une ou plusieurs communes homonymes.

</details>

<details>

<summary><strong>Des codes postaux n’ont pas le même code que celui du département</strong>.</summary>

Ces cas de figure sont très rares (quelques dizaines).

</details>

<details>

<summary><strong>Plusieurs noms de voie avec un nom identique sont situés à différents endroits pour une même commune</strong>.</summary>

Cette situation s’explique en particulier avec la création des communes nouvelles qui a encouragé le regroupement de communes. Ce problème peut être réglé en ajoutant le nom de la commune déléguée dans l’adresse postale, en renumérotant les rues ou en les renommant. Or les géocodeurs ne gèrent pas forcément bien (voir pas du tout) l’ajout d’adresse de la commune déléguée.

</details>

<details>

<summary><strong>Plusieurs coordonnées pour une même adresse.</strong></summary>

* Il peut exister des différences liées à la vision sur la position du numéro de l’adresse (entrée principale, boîte aux lettres, bâtiment, cage d’escalier, logement, parcelle, position dérivée du segment de la voie de rattachement, point d’accès technique, etc.) ;

<!---->

* Des référentiels différents selon les acteurs même si la BAN (Base Adresse Nationale) et les BAL (Bases Adresses Locales) amènent à une amélioration et une uniformisation des référentiels : données héritées de la Poste, de l’IGN, du cadastre, des opérateurs réseaux (fibre, etc.).

</details>

## Cas pratiques <a href="#cas-pratiques" id="cas-pratiques"></a>

### Comment faire si une recherche d’adresse ne fonctionne pas ? <a href="#comment-faire-si-une-recherche-d-adresse-ne-fonctionne-pas" id="comment-faire-si-une-recherche-d-adresse-ne-fonctionne-pas"></a>

* Vérifier en utilisant l’[autocomplétion](https://adresse.data.gouv.fr/base-adresse-nationale#4.4/46.9/1.7) :
  * Tapez votre adresse. Par exemple, "20 avenue de Ségur". Si le numéro est bien proposé et que la commune est la bonne pour le premier résultat, c’est la manière dont vous avez récupéré l’adresse qui est en cause. Si vous êtes en mode "batch", la première adresse retournée peut être mauvaise et c’est la 2ème ou 3ème adresse que vous attendiez.
  * Imaginons que vous pensiez que le numéro existe, mais ne le trouvez pas dans votre résultat de géocodage. Essayez alors de trouver la rue. Essayons "87 avenue de Ségur". On ne voit que des rues qui sont retournées suite à la recherche. Cliquez sur la rue qui semble correspondre à votre recherche. Cela va zoomer. Vous allez pouvoir voir s’il y a des adresses et lesquelles sont inventoriées.
* La donnée de référence n’est pas présente : c’est un oubli ou personne ne l’a encore produite.&#x20;
* Le résultat est une adresse BAL. Votre commune est entrée dans une démarche de recensement et valorisation de ces adresses.&#x20;
  * Vous pouvez confirmer si l'adresse existe en allant sur [https://adresse.data.gouv.fr/deploiement-bal](https://adresse.data.gouv.fr/deploiement-bal).&#x20;
    * Zoomez sur la carte pour trouver votre commune ou l'organisme qui porte votre BAL, par exemple un intercommunalité.&#x20;
    * Cliquez sur le polygone. Allons par exemple à [la communauté d'agglomération Arles Crau Camargue Montagnette](https://adresse.data.gouv.fr/bases-locales/jeux-de-donnees/601402f5818a575b16081fe3).&#x20;
    * Descendons et recherchons une commune puis cliquons dessus, par exemple [Arles](https://adresse.data.gouv.fr/base-adresse-nationale/13004).&#x20;
    * On peut maintenant chercher par nom de voie ou lieu dit pour vérifier que la voie existe. Prenons [l'allée des Manades](https://adresse.data.gouv.fr/base-adresse-nationale/13004\_2865#15.05/43.66235/4.6205).&#x20;
    * Nous pouvons ensuite vérifier dans la liste l'existence du numéro.
* Adresse IGN vs adresse cadastre vs adresse BAL.&#x20;
* La donnée est présente, mais les termes de recherche ne permettent pas de la trouver.&#x20;

{% hint style="success" %}
Vous êtes un particulier ? Vous pouvez récupérer les coordonnées de votre commune pour lui faire part de vos retours en passant par [https://adresse.data.gouv.fr/contribuer](https://adresse.data.gouv.fr/contribuer) puis en cherchant votre commune.
{% endhint %}

## Comment faire de l’**autocomplétion d’adresse ?** <a href="#comment-faire-de-l-autocompletion-d-adresse" id="comment-faire-de-l-autocompletion-d-adresse"></a>

Il existe plusieurs solutions pour faire de l’autocomplétion dans un outil web.

Vous pouvez vous appuyer sur de nombreuses bibliothèques, celles-ci étant généralement liées à des bibliothèques cartographiques.

{% tabs %}
{% tab title="Solutions basées sur Leaflet" %}
## **Solutions basées sur Leaflet**

* [https://github.com/entrepreneur-interet-general/leaflet-geocoder-ban](https://github.com/entrepreneur-interet-general/leaflet-geocoder-ban)
* [https://github.com/komoot/leaflet.photon](https://github.com/komoot/leaflet.photon)

> **Exemples :**
>
> * [https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_control.html](https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_control.html)
> * [https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_search\_bar.html](https://entrepreneur-interet-general.github.io/leaflet-geocoder-ban/demo/demo\_search\_bar.html)
> * [https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-leaflet-photon.html](https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-leaflet-photon.html)
{% endtab %}

{% tab title="Solutions basées sur OpenLayers" %}
## **Solutions basées sur OpenLayers**

* [https://github.com/webgeodatavore/photon-geocoder-autocomplete](https://github.com/webgeodatavore/photon-geocoder-autocomplete)
* [https://viglino.github.io/ol-ext/examples/search/map.control.searchban.html](https://viglino.github.io/ol-ext/examples/search/map.control.searchban.html)

> **Exemples :**
>
> * [https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-ol.html](https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-ol.html)
{% endtab %}

{% tab title="Solutions indépendantes de bibliothèques cartographiques" %}
## **Solutions indépendantes de bibliothèques cartographiques**

* [https://github.com/webgeodatavore/photon-geocoder-autocomplete](https://github.com/webgeodatavore/photon-geocoder-autocomplete)

> **Exemples :**
>
> * [Exemple avec Maplibre, mais non lié à Maplibre](https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-maplibre.html)
> * [Exemple avec OpenLayers, mais non lié à OpenLayers](https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-openlayers.html)
> * [Formulaire exemple 1](https://raw.githack.com/webgeodatavore/photon-geocoder-autocomplete/master/demo/index-no-map.html)
> * [Formulaire exemple 2](https://gist.githack.com/ThomasG77/0b99013795f76699c5c9a0d7daf4411e/raw/a6b65c033efa73cecb3ea8473ba83aabc973d373/demo-ban-form-only-alternate.html)
{% endtab %}
{% endtabs %}

## Comment faire du **géocodage par adresse unitaire ?** <a href="#comment-faire-du-geocodage-par-adresse-unitaire" id="comment-faire-du-geocodage-par-adresse-unitaire"></a>

Avec Python, pour faire des appels unitaires, vous pouvez :&#x20;

* **utiliser** [**le code de ce script**](https://gist.githubusercontent.com/ThomasG77/32329a8557135f11cb5656e3bfd4d35c/raw/9bd7883be31d2c9758d4393d72e9dc1ae4c5bed3/geocode-addok-unit-call.py) ;
* **passer par** [**Geopy**](https://geopy.readthedocs.io/en/stable/#installation) : il existe une [classe `BANFrance` pour ce besoin](https://geopy.readthedocs.io/en/stable/#banfrance).

En JavaScript, vous pouvez utiliser [ces exemples](https://addok.readthedocs.io/en/latest/examples/#using-javascript-client-side) que ce soit pour un usage côté navigateur ou côté serveur (Node.js/deno).

## Comment réaliser un géocodage massif ? <a href="#geocodage-massif" id="geocodage-massif"></a>

Lorsqu'on choisit cette option, on privilégie l'appel par le endpoint CSV de l'API.&#x20;

Il faut préalablement s'assurer que son CSV est bien formaté : il s'avère que le géocodage peut ponctuellement dysfonctionner si le CSV n'est pas bien formaté.

{% tabs %}
{% tab title="Option manuelle" %}
## Option manuelle <a href="#option-manuelle" id="option-manuelle"></a>

Il existe une interface graphique pour envoyer des fichiers CSV sur [https://adresse.data.gouv.fr/csv](https://adresse.data.gouv.fr/csv) dont la taille maximum est de 50Mo.&#x20;

Pour tester, téléchargeons [le fichier exemple](https://gist.githubusercontent.com/ThomasG77/32329a8557135f11cb5656e3bfd4d35c/raw/9bd7883be31d2c9758d4393d72e9dc1ae4c5bed3/annuaire-des-debits-de-tabac-2018-utf8-20lines.csv) puis suivez l'exemple en utilisant le GIF animé ci-dessous.

![](https://guides.etalab.gouv.fr/assets/img/geocodage-csv-manuel.ecc04ebd.gif)

Pour réaliser un géocodage massif, il faut généralement vérifier le formatage de votre CSV.
{% endtab %}

{% tab title="Python seul" %}
## **Python seul** <a href="#python-seul" id="python-seul"></a>

* Solution partant d'appels unitaires plutôt que des appels CSV :  [https://github.com/MTES-MCT/bulk-geocoding-python-client](https://github.com/MTES-MCT/bulk-geocoding-python-client)
* Solution partant d'appels à l'API CSV. Il suffit de récupérer [le zip](https://gist.github.com/ThomasG77/32329a8557135f11cb5656e3bfd4d35c/archive/3681bd0c070540abfdae55e6ff0bf9a41795cf42.zip), de décompresser le fichier. Ensuite, il vous suffit de lancer le script Python avec `python chunk-csv-python.py`. Cela permettra de faire l'appel vers l'API CSV soit en une fois, soit en plusieurs phases. On obtiendra ainsi le fichier `annuaire-des-debits-de-tabac-2018-utf8-20lines.geocoded.csv` qui est la version géocodée par l'API CSV d'un fichier de 20 lignes ainsi que `myresults.csv` qui est une version qui résulte d'une phase de découpage d'un gros fichier en plusieurs morceaux, d'appels à l'API CSV à partir de chacun de ces fichiers, puis du réassemblage des fichiers ainsi retournés. Vous n'avez plus qu'à adapter le code du fichier `chunk-csv-python.py`.
* [https://github.com/MTES-MCT/bulk-geocoding-python-client](https://github.com/MTES-MCT/bulk-geocoding-python-client) (attention, la solution fait des appels unitaires plutôt que des appels CSV)
{% endtab %}

{% tab title="JavaScript" %}
## **JavaScript** <a href="#javascript" id="javascript"></a>

* Géocodage massif avec une solution en ligne de commande utilisant Node.js :  [https://github.com/jdesboeufs/addok-geocode-stream](https://github.com/jdesboeufs/addok-geocode-stream)
{% endtab %}

{% tab title="Autres outils utilisant la BAN" %}
## Autres outils utilisant la BAN <a href="#autres-outils-utilisant-la-ban" id="autres-outils-utilisant-la-ban"></a>

**--> Vous faites du SIG, néophyte comme expert et utilisez le logiciel SIG QGIS ?**

* Recherchez des adresses : [https://oslandia.gitlab.io/qgis/french\_locator\_filter/](https://oslandia.gitlab.io/qgis/french\_locator\_filter/)
* Géocodez des tables depuis une table dans QGIS QBano : [https://www.data.gouv.fr/en/reuses/plugin-experimental-qbano-pour-qgis/](https://www.data.gouv.fr/en/reuses/plugin-experimental-qbano-pour-qgis/). À ce jour, le plug-in est mal maintenu, il vaut mieux récupérer [ce zip](https://labs.webgeodatavore.com/partage/QBano.zip) puis installer le plug-in depuis celui-ci.
* Avec PyQGIS, vous pouvez aussi géocoder en partant de : [https://gis.stackexchange.com/a/395415/638](https://gis.stackexchange.com/a/395415/638)

**--> Vous utilisez d’autres outils?**

* Vous faites du R ? [https://cran.r-project.org/web/packages/banR/index.html](https://cran.r-project.org/web/packages/banR/index.html)
* Vous souhaitez intégrer la recherche dans le CMS SPIP ? [http://plugins.spip.net/gisban.html](http://plugins.spip.net/gisban.html)
{% endtab %}
{% endtabs %}

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
