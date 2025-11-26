# Ouvrir des données

Vous avez téléchargé des données, et souhaitez désormais ouvrir le fichier.

Pour cela :

* **Identifiez le format du fichier** (notamment grâce à l’extension du fichier) ;
* **Suivez les indications associées ci-dessous** (proposées pour différents formats de fichiers usuels).

{% tabs %}
{% tab title="CSV" %}
## Qu'est-ce que c'est ?

Un fichier CSV (_Comma Separated Values_) est un fichier texte qui stocke des données sous forme de tableau et utilise des virgules (ou des point virgules, des tabulations, etc.) pour séparer les valeurs.

## A quoi ressemble un fichier CSV ?

Dans un fichier CSV :

* Chaque ligne du texte correspond à une ligne d’un tableau, et les virgules (ou les point virgules, etc.) correspondent aux séparations entre les colonnes.
* La première ligne est souvent utilisée comme ligne d’en-tête contenant le nom des colonnes.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2024-05-29 à 09.58.54 (2).png" alt=""><figcaption><p><em>Exemple de fichier au format CSV (Wikipedia)</em></p></figcaption></figure>

## Comment ouvrir un fichier CSV ?

### Avec un logiciel de tableur (LibreOffice Calc, Excel, etc.)

**Libre Office Calc**

* Ouvrez “LibreOffice Calc”, puis allez dans “Fichier”>”Ouvrir”
*   Une boîte de dialogue apparaît, choisissez pour :

    * Jeu de caractères : “Unicode (UTF-8)”
    * Options de séparateur : Séparé par \[le bon séparateur] (selon le cas, il s’agira de la virgule, du point virgule ou de la tabulation)
    * Cliquez sur “OK” et le fichier s’ouvrira

    <figure><img src="../../../.gitbook/assets/May-29-2024 10-23-02.gif" alt=""><figcaption><p>Ouvrir un CSV avec LibreOffice Calc</p></figcaption></figure>

{% hint style="success" %}
La marche à suivre est similaire pour d'autres logiciels de tableur comme Excel.
{% endhint %}

### **Avec un éditeur de texte**

**Notepad++**

* Ouvrez Notepad++ et sélectionnez “Fichier” > “Ouvrir”
* Choisissez le fichier CSV à ouvrir
* Notepad++ affichera le contenu du fichier en texte brut

**Visual Studio Code**

* Ouvrez Visual Studio Code et utilisez “File” > “Open File” pour sélectionner votre fichier
* Visual Studio Code affichera le contenu du fichier en texte brut

### **Avec un langage de programmation** : Python, R, etc.
{% endtab %}

{% tab title="JSON" %}
## Qu'est-ce que c'est ?

Un fichier JSON (JavaScript Object Notation) est un format de texte dérivé de la notation des objets du langage JavaScript (mais il est indépendant du langage).

## A quoi ressemble un fichier JSON  ?

La lecture d’un fichier JSON est relativement intuitive.

Dans un fichier JSON : Les données sont présentées sous forme de paires clé/valeur :

* Une paire est écrite en accolades.
* Un objet JSON est un ensemble de paires clé/valeur, séparées par une virgule.
* Un tableau JSON est une suite de valeurs, sous forme de chaînes de caractères, associés à une clé unique. Les valeurs sont écrites entre crochets et séparées par une virgule.
* Les objets JSON peuvent être imbriqués pour représenter la structure des données.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2024-08-08 à 11.12.23.png" alt=""><figcaption><p>Exemple de fichier JSON (Wikipedia)</p></figcaption></figure>

## Comment ouvrir un fichier JSON ?

### Avec un éditeur de texte

**Notepad++**

* Ouvrez Notepad++ et sélectionnez "Fichier" > "Ouvrir"
* Choisissez le fichier JSON à ouvrir
* Notepad++ affiche le contenu du fichier en texte brut

**Visual Studio Code**

* Ouvrez Visual Studio Code et utilisez "File" > "Open File" pour sélectionner votre fichier JSON
* Visual Studio Code offre une coloration syntaxique et un repli de code pour une lecture plus facile

### Avec un langage de programmation

Python avec json, R avec jsonlite, etc.
{% endtab %}

{% tab title="XML" %}
## Qu'est-ce que c'est ?&#x20;

Un fichier XML (_eXtensible Markup Language_) est un document texte qui contient des données organisées selon une syntaxe prédéfinie. Sa structure est basée sur des balises qui définissent les éléments et leur hiérarchie.

## A quoi ressemble un fichier XML ?&#x20;

Dans un fichier XML :

* Les balises représentent un type de données particulier. Chaque occurrence d’une balise est considérée comme un élément, et ces éléments sont organisés en une structure hiérarchique.
* La balise supérieure est appelée “racine” tandis que les balises suivantes sont considérées comme des “enfants”.
* L’ensemble forme une structure arborescente.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2024-05-29 à 10.34.16.png" alt=""><figcaption><p>Exemple de fichier XML (Source : Cours CentraleSupélec)</p></figcaption></figure>

## Comment ouvrir un fichier XML ?

### Avec un éditeur de texte

**Notepad++**

* Ouvrez Notepad++ et sélectionnez "Fichier" > "Ouvrir".
* Choisissez le fichier XML à ouvrir
* Notepad++ affiche le contenu du fichier en texte brut

**Visual Studio Code**

* Ouvrez Visual Studio Code et utilisez "File" > "Open File" pour sélectionner votre fichier XML

### Avec un langage de programmation

Python avec ElementTree, R avec XML, etc.
{% endtab %}

{% tab title="GeoJSON" %}
## Qu'est-ce que c'est ?

Le format GeoJSON est un format ouvert d’échange de données géospatiales qui utilise la norme JSON.

## A quoi ressemble un fichier GeoJSON ?

Une fichier GeoJSON est constitué d’objets JSON, où chaque objet représente une entité géographique. Les principaux types d’objets incluent :

* Point : Représente une position unique dans l’espace.
* LineString : Représente une série de points connectés par des segments de ligne. Il est utilisé pour représenter des lignes ou des chemins.
* Polygon : Représente une surface fermée avec des limites définies par une série de points.
* Feature : Représente un objet géographique qui peut contenir une géométrie (point, ligne, polygone, etc.) et des propriétés supplémentaires
* FeatureCollection : Représente une collection d’objets “Feature”

<figure><img src="../../../.gitbook/assets/Capture d’écran 2024-07-25 à 14.53.45.png" alt=""><figcaption><p>Exemple de fichier GeoJSON (Wikipedia)</p></figcaption></figure>

## Comment ouvrir un fichier GeoJSON ?

### Avec le Géoportail de l'IGN

* Rendez-vous sur le [Géoportail](https://www.geoportail.gouv.fr/) ;
* Choisissez un fond de carte ;
* Cliquez sur la clé à molette > “Importer des données” > Choisissez le format “GeoJSON” ;
* Recherchez votre fichier et importez ;
* Les données s’affichent sur la carte.

<figure><img src="../../../.gitbook/assets/May-29-2024 10-52-21.gif" alt=""><figcaption><p>Ouvrir un fichier GeoJSON avec le Géoportail de l'IGN</p></figcaption></figure>

### Avec uMap

[**Version institutionnelle**](https://umap.incubateur.anct.gouv.fr/fr/) **et** [**grand public**](https://umap.openstreetmap.fr/fr/)

* Rendez-vous sur uMap ;
* Cliquez sur “Créer une carte” ;
* Cliquez sur l’icône d’import de données (flèche) ;
* Sélectionnez votre fichier et cliquez sur “Importer” ;
* Les données s’affichent sur la carte.

<figure><img src="../../../.gitbook/assets/May-29-2024 11-01-47.gif" alt=""><figcaption><p>Ouvrir un fichier GeoJSON avec uMap</p></figcaption></figure>

### Avec l'outil geojson.io

* Rendez-vous sur [geojson.io](http://geojson.io) ;
* Cliquez sur “Open” et choisissez votre fichier.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2024-05-29 à 11.32.21.png" alt=""><figcaption><p>Ouvrir un fichier GeoJSON avec geojson.io</p></figcaption></figure>

### Avec le logiciel de cartographie QGIS&#x20;

* Ouvrez [QGIS](https://www.qgis.org/) et allez dans "Layer" > "Add Layer" > "Add Vector Layer" ;
* Sélectionnez le fichier GeoJSON à ouvrir ;
* QGIS affiche les données géographiques sur la carte.

### Avec un langage de programmation

Python avec GeoPandas, JavaScript avec Leaflet, R avec sf, etc.
{% endtab %}

{% tab title="shapefile" %}
## Qu'est-ce que c'est ?

Le format shapefile est un format de fichier géospatial largement utilisé pour stocker des données géographiques vectorielles telles que des points, des lignes et des polygones.

Un shapefile n’est pas un fichier unique, mais une collection de plusieurs fichiers connexes qui, ensemble, décrivent des objets géographiques et leurs attributs :

* .shp : contient la géométrie des entités (formes) ;
* .shx : contient l’index des formes pour un accès rapide ;
* .dbf : contient les attributs des entités dans un format tabulaire.

## A quoi ressemble un fichier shapefile ?

Un fichier shapefile contient toute l’information liée à la géométrie des objets décrits, qui peuvent être :

* des points ;
* des lignes ;
* des polygones.

## Comment ouvrir un fichier shapefile ?

### Un logiciel de cartographie comme QGIS

* Ouvrez [QGIS](https://www.qgis.org/) et allez dans "Layer" > "Add Layer" > "Add Vector Layer"
* Sélectionnez le fichier .shp
* QGIS charge les fichiers associés et affiche les données

### Un langage de programmation

Python avec GeoPandas, R avec sf, etc.
{% endtab %}

{% tab title="KML" %}
## Qu'est-ce que c'est ?

Un fichier KML (_Keyhole Markup Language_) est un fichier basé sur du XML utilisé pour représenter des données géospatiales. Il permet de stocker et de visualiser des points, des lignes, de polygones et des images superposées.

## A quoi ressemble un fichier KML ?

Un fichier KML est un document XML avec une structure hiérarchique, où chaque élément représente une entité géographique ou un style. Les éléments courants incluent :

* \<Point> : Définit un point géographique par des coordonnées de latitude et de longitude, et parfois une altitude.
* \<LineString> : Représente une série de segments de ligne connectés par une séquence de coordonnées. Cet élément est couramment utilisé pour afficher des routes, des sentiers, ou des frontières.
* \<Polygon> : Définit une surface fermée, comme un lac, une parcelle de terrain, ou une région. Un polygone est décrit par une ou plusieurs frontières définies par une séquence de coordonnées.
* \<Style> : Définit l'apparence des éléments géographiques, comme les couleurs, les largeurs de ligne, les icônes, etc.
* \<Placemark> : Représente un lieu géographique identifiable. Il peut contenir des informations telles que le nom, la description, et les coordonnées géographiques du lieu. Un `<Placemark>` peut également inclure des éléments géométriques comme `<Point>`, `<LineString>`, ou `<Polygon>`, ainsi que des styles pour personnaliser son apparence.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2024-07-25 à 15.02.04.png" alt=""><figcaption><p>Exemple de fichier KML (Wikipedia)</p></figcaption></figure>

## Comment ouvrir un fichier KML ?

### Avec le Géoportail de l'IGN

* Rendez-vous sur le [Géoportail](https://www.geoportail.gouv.fr/) ;
* Choisissez un fond de carte ;
* Cliquez sur la clé à molette > “Importer des données” > Choisissez le format “KML”
* Recherchez votre fichier et importez

<figure><img src="../../../.gitbook/assets/May-29-2024 11-40-18.gif" alt=""><figcaption><p>Ouvrir un fichier KML avec le Géoportail de l'IGN</p></figcaption></figure>

### Avec uMap

[**Version institutionnelle**](https://umap.incubateur.anct.gouv.fr/fr/) **et** [**grand public**](https://umap.openstreetmap.fr/fr/)

* Rendez-vous sur uMap ;
* Cliquez sur “Créer une carte” ;
* Cliquez sur l’icône d’import de données (flèche) ;
* Sélectionnez votre fichier et cliquez sur “Importer”
* Les données s’affichent sur la carte.

<figure><img src="../../../.gitbook/assets/May-29-2024 11-41-35.gif" alt=""><figcaption><p>Ouvrir un fichier KML avec uMap</p></figcaption></figure>

### Avec le logiciel de cartographie QGIS

* Ouvrez [QGIS](/broken/spaces/aR5Xnbp0nwO8PvuTp9dy/pages/8GJ565HuLsqkoAer7IO9) et allez dans "Layer" > "Add Layer" > "Add Vector Layer"
* Sélectionnez le fichier KML.
* QGIS charge les fichiers KML et affiche les données géospatiales sur la carte

### Avec un langage de programmation

Python avec fastkml, R avec sf, etc.
{% endtab %}
{% endtabs %}

## Ressources externes pour aller plus loin

* [Cours Open Data : Avant de vous présenter à la data - Cerema Med (Mathieu Rajerison)](https://datagistips.github.io/cours-data-ente/presentations/session1/session1_5_avant_data.html#1)
