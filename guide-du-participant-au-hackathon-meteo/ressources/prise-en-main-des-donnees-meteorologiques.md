# Prise en main des données météorologiques

## Récupérer les données météorologiques en utilisant l’API de data.gouv.fr

[data.gouv.fr](https://data.gouv.fr) est souvent uniquement assimilé à un site web. Or, il permet aussi :

* de moissonner des ressources distantes comme des catalogues ;
* de consulter via une API les pages, les jeux de données associés à des pages, les organisations, leurs jeux de données, les réutilisations, etc.
* de mettre à jour les jeux de données via l'API.

Il existe une référence à ce propos sur [https://doc.data.gouv.fr/api/reference/](https://doc.data.gouv.fr/api/reference/). Un guide est disponible sur https://guides.data.gouv.fr/guide-data.gouv.fr/api.

Nous allons, dans ce cas précis, aborder des exemples spécifiques aux données publiées par Météo-France.

Nos exemples sont réalisés soit en ligne de commande en Bash, soit en Python.

Pour les exemples Bash, il faut disposer de [curl](https://curl.se/), [wget](https://www.gnu.org/software/wget/), [jq](https://jqlang.github.io/jq/) et [xsv](https://github.com/BurntSushi/xsv?tab=readme-ov-file#installation) installés sur votre machine.

### Lister les ressources et les jeux de données d'une organisation

On cible ici Météo-France.

**En bash**, on passe en CSV.

```bash

# Nous trichons un peu : nous savons qu'il n'y a que 106 jeux de données pour le moment et cela nous évite de paginer ici.
curl '<https://www.data.gouv.fr/api/1/organizations/534fff8ba3a7292c64a77ed4/datasets/?page=1&page_size=200>' | jq . >| meteo-france-organization.json
echo '"ds_id","ds_title","ds_page","id","title","format","filetype","mime","type","url"' >| datasets_organization_meteo_france.csv
jq -r '.data[] | .page as $ds_page | .title as $ds_title| .id as $ds_id | .resources[] | [$ds_id, $ds_title, $ds_page, .id, .title, .format, .filetype, .mime, .["type"], .url] | @csv' meteo-france-organization.json >> datasets_organization_meteo_france.csv
```

En Python, on récupère les données.

```python
import csv
import urllib.request
import json

start = 1
page_size = 10
organization_id = '534fff8ba3a7292c64a77ed4'
api_url = f'<https://www.data.gouv.fr/api/1/organizations/{organization_id}/datasets/?page={start}&page_size={page_size}>'

def get_all_organisations_datasets(initial_url):
    api_url = initial_url
    data = []
    while api_url is not None:
        with urllib.request.urlopen(api_url) as resp:
            response_json = json.load(resp)
        api_url = response_json.get('next_page')
        data = data + response_json.get('data')
    return data

results = get_all_organisations_datasets(api_url)

infos = []
field_names = ["ds_id","ds_title","ds_page","id","title","format","filetype","mime","type","url"]
infos.append(field_names)
for result in results:
    ds_id = result.get('id')
    ds_title = result.get('title')
    ds_page = result.get('page')
    for resource in result.get('resources'):
        infos.append([
            ds_id,
            ds_title,
            ds_page,
            resource.get('id'),
            resource.get('title'),
            resource.get('format'),
            resource.get('filetype'),
            resource.get('mime'),
            resource.get('type'),
            resource.get('url')
        ])

with open('datasets_organization_meteo_france.csv', 'w') as csvfile:
    writer = csv.writer(csvfile, quoting=csv.QUOTE_ALL)
    writer.writerows(infos)

print(len(results))
```

Il est aussi possible de passer par les fichiers du catalogue de données de data.gouv.fr pour obtenir un contenu similaire. Le lien web est : [https://www.data.gouv.fr/fr/datasets/catalogue-des-donnees-de-data-gouv-fr/#/resources](https://www.data.gouv.fr/fr/datasets/catalogue-des-donnees-de-data-gouv-fr/#/resources)

{% hint style="info" %}
**Inconvénient** : il est mis à jour tous les jours, cette fréquence bien qu'importante ne convient pas forcément à tous les utilisateurs.

**Avantage** : les fichiers sont exploitables via des logiciels de type tableur
{% endhint %}

```bash
url_catalogue=$(curl <https://www.data.gouv.fr/api/1/datasets/5d13a8b6634f41070a43dff3/> | jq -r '.resources[] | select(.title | startswith("export-resource"))| .url')

wget $url_catalogue
local_file=$(echo "${url_catalogue##*/}")
xsv search -d ';' -s "dataset.organization_id" '534fff8ba3a7292c64a77ed4' $local_file >| datasets_organization_meteo_france_from_catalogue.csv
xsv search -d ';' -s "dataset.organization" 'Météo-France' $local_file >| datasets_organization_meteo_france_from_catalogue_alt.csv
```

### Récupérer les jeux de données d'un dataset

Il s'agit de pages de jeux de données comme [https://www.data.gouv.fr/fr/datasets/donnees-climatologiques-de-base-horaires/](https://www.data.gouv.fr/fr/datasets/donnees-climatologiques-de-base-horaires/)

#### En Bash

```bash

curl https://www.data.gouv.fr/api/1/datasets/6569b4473bedf2e7abad3b72/ | jq -r '.resources[] | select(.type != "documentation")| .url'
```

#### En Python

```python
import urllib.request
import json

dataset_id = '6569b4473bedf2e7abad3b72'
url = f'<https://www.data.gouv.fr/api/1/datasets/{dataset_id}/>'

# Start of datasets infos ressources retrieval
with urllib.request.urlopen(url) as resp:
    json_content = json.load(resp)

urls = [resource.get('url') for resource in json_content.get('resources') if resource.get('type') != 'documentation']
print(urls)
```

### Récupérer les id des organisations ("organizations") ou des jeux de données ("datasets")

#### Pour récupérer les id des organisations

1. Passez par [data.gouv.fr](http://data.gouv.fr/) ;
2. Cherchez l'organisation Météo-France et rendez-vous sur sa page ;
3. Allez dans l'onglet "Informations" ;
4. Descendez en bas pour voir mentionné l'id comme sur : [https://www.data.gouv.fr/fr/organizations/meteo-france/#/information](https://www.data.gouv.fr/fr/organizations/meteo-france/#/information)

Vous pouvez réexploiter cette `id` via une URL du type [https://www.data.gouv.fr/api/1/organizations/534fff8ba3a7292c64a77ed4/datasets/?page=1\&page\_size=10](https://www.data.gouv.fr/api/1/organizations/534fff8ba3a7292c64a77ed4/datasets/?page=1\&page\_size=10) pour l'organisation `534fff8ba3a7292c64a77ed4`

{% hint style="danger" %}
Il existe pour les organisations un système de pagination. Ainsi, il faut vérifier si dans le retour de l'URL précédente si `next_page` contient une URL. Il faut alors l'appeler et répéter l'opération autant de fois que nécessaire.
{% endhint %}

#### Pour récupérer les id des jeux de données

1. Allez sur un jeu de données des "Données climatologiques de base - horaires", [https://www.data.gouv.fr/fr/datasets/donnees-climatologiques-de-base-horaires/](https://www.data.gouv.fr/fr/datasets/donnees-climatologiques-de-base-horaires/)
2. Rendez-vous dans l'onglet "Informations" pour retrouver l'`id` du jeu de données.

Ensuite, il faudra entrer comme URL [https://www.data.gouv.fr/api/1/datasets/6569b4473bedf2e7abad3b72/](https://www.data.gouv.fr/api/1/datasets/6569b4473bedf2e7abad3b72/) avec l'id `6569b4473bedf2e7abad3b72` pour accéder au json des ressources associées au jeu de données.

### Le "raccourci" possible

Nous avons tendance à préférer les identifiants techniques mais un autre moyen plus rapide est **de passer le slug de la page ou de l'organisation**.

{% hint style="success" %}
Le slug correspond à du texte qui s'appuie sur le titre de l'organisation ou du jeu de données en remplaçant les espaces par des tirets et les lettres accentuées en lettres sans accents avec des minuscules partout dans l'URL.
{% endhint %}

Pour l'organisation [https://www.data.gouv.fr/fr/organizations/meteo-france/](https://www.data.gouv.fr/fr/organizations/meteo-france/), il suffit de copier la partie meteo-france de l'url et d'ouvrir la page [https://www.data.gouv.fr/api/1/organizations/meteo-france/datasets/?page=1\&page\_size=10](https://www.data.gouv.fr/api/1/organizations/meteo-france/datasets/?page=1\&page\_size=10) pour avoir le même résultat que [https://www.data.gouv.fr/api/1/organizations/534fff8ba3a7292c64a77ed4/datasets/?page=1\&page\_size=10](https://www.data.gouv.fr/api/1/organizations/534fff8ba3a7292c64a77ed4/datasets/?page=1\&page\_size=10).

Pour le jeu de données [https://www.data.gouv.fr/fr/datasets/donnees-climatologiques-de-base-horaires/](https://www.data.gouv.fr/fr/datasets/donnees-climatologiques-de-base-horaires/), les URLs [https://www.data.gouv.fr/api/1/datasets/donnees-climatologiques-de-base-horaires/](https://www.data.gouv.fr/api/1/datasets/donnees-climatologiques-de-base-horaires/) ou [https://www.data.gouv.fr/api/1/datasets/6569b4473bedf2e7abad3b72/](https://www.data.gouv.fr/api/1/datasets/6569b4473bedf2e7abad3b72/) sont équivalentes.

### meteo.data.gouv.fr : les "topics"

Derrière [meteo.data.gouv.fr](http://meteo.data.gouv.fr) se cache un site dérivé de [data.gouv.fr](http://data.gouv.fr/).

L'API de [data.gouv.fr](http://data.gouv.fr/) expose ce que l’on appelle des "topics", qui sont des regroupements de données et qui sont consommés via le front de meteo.data.gouv.fr.

3 topics sont actuellement utilisés sur [meteo.data.gouv.fr](http://meteo.data.gouv.fr/) :

* Données climatologiques de base
* Données climatologiques de référence pour le changement climatique
* Données de prévision numérique du temps (PNT)

**Boucler sur les topics**

```bash
>| topics.ndjson
url="<https://www.data.gouv.fr/api/1/topics/?page=1&page_size=10>"
while true ; do
  result=$(curl -s $url);
  echo $result | jq -r -c .data[] >> topics.ndjson
  url=$(echo $result | jq -r -c .next_page)
  echo $url
  if [[ $(echo $result | jq '.next_page') == 'null' ]];
    then break; # Exit the loop
  fi;
done;
jq -c -r --slurp '.[] | .page as $to_page | .name as $to_name | .id as $to_id | .datasets[] | [$to_id, $to_name, $to_page, .id, .title, .page, .uri] | @csv' topics.ndjson
jq -r -c '. | [.id, .name] | @csv' topics.ndjson

```

Il est ensuite possible de retrouver les correspondances entre noms des topics sur [meteo.data.gouv.fr](http://meteo.data.gouv.fr/).

Ainsi, on a la correspondance suivante :

```
"65e0c82c2da27c1dff5fa66f","Données de Prévision Numérique du Temps (PNT)"
"6571f2db0273fc306408f265","Données climatologiques de référence pour le changement climatique"
"6571f26dc009674feb726be9","Données climatologiques de base"

```

Si on veut toutes les données du portail [meteo.data.gouv.fr](http://meteo.data.gouv.fr/), voici un recette en bash :

```bash
topic_ids_meteo=("65e0c82c2da27c1dff5fa66f" "6571f2db0273fc306408f265" "6571f26dc009674feb726be9")

echo "to_id,to_name,to_page,id,title,page,uri" >| topics_datasets.csv
for id in ${topic_ids_meteo[@]};
  do echo "<https://www.data.gouv.fr/api/1/topics/${id}/>";
     curl "<https://www.data.gouv.fr/api/1/topics/${id}/>" | jq -c -r '.page as $to_page | .name as $to_name | .id as $to_id | .datasets[] | [$to_id, $to_name, $to_page, .id, .title, .page, .uri] | @csv' >> topics_datasets.csv
done;

```

## Utiliser les données météorologiques

Les formats de données météorologiques sont **des formats multidimensionnels**, en particulier pour les données liées aux satellites car ils nécessitent de gérer les coordonnées soit ponctuelles soit associées à une grille (déjà 2 dimensions), des dates d'acquisition (une autre dimension) et des mesures diverses (encore une dimension).

Pour cela, plusieurs formats sont utilisés. On stocke généralement les données brutes sous forme de fichiers dits GRIB, un format standardisé par l'OMM (Organisation Mondiale de la Météorologie). Vous pouvez en savoir plus en passant par [la page Wikipédia GRIB](https://fr.wikipedia.org/wiki/GRIB).

### Manipuler les formats de fichiers grib2

#### Inspection en Bash

```bash
wget <https://object.data.gouv.fr/meteofrance-pnt/pnt/2024-04-02T12:00:00Z/arome/001/HP1/arome__001__HP1__01H__2024-04-02T12:00:00Z.grib2>
# On va généralement inspecter avec less ou filtrer avec des outils type grep
gdalinfo arome__001__HP1__01H__2024-04-02T12\\:00\\:00Z.grib2
# On a une sortie JSON potentiellement plus facilement exploitable avec par exemple jq
gdalinfo -json arome__001__HP1__01H__2024-04-02T12\\:00\\:00Z.grib2
```

#### Inspection en Python

```python
import pygrib

openpath='arome__001__HP1__01H__2024-04-02T12:00:00Z.grib2'
grbs = pygrib.open(openpath)
grbs.seek(0)
for grb in grbs:
    print(grb)
```

Pour l'exemple ci-dessous, passez par conda avec `conda install --channel conda-forge xarray cfgrib eccodes -y`

```python
import numpy as np
import xarray as xr
import matplotlib.pyplot as plt

openpath = 'arome__001__HP1__01H__2024-04-02T12:00:00Z.grib2'
# Below commeneted due to https://github.com/meteofrance/meteonet/issues/20
# ds = xr.open_dataset(openpath,engine='cfgrib',backend_kwargs={'indexpath': ''})
meteodata = xr.open_dataset(openpath, engine='cfgrib',
                            backend_kwargs={'filter_by_keys': {'cfVarName': 'ws'}})
                            backend_kwargs={'filter_by_keys': {'name': 'Relative humidity'}})
print(meteodata['ws'])
ds_heightAboveGround50 = meteodata.sel(heightAboveGround=50)
plt.contourf(ds_heightAboveGround50['ws'])
plt.colorbar()
plt.savefig('ds_heightAboveGround50.png')
```

#### Inspection dans QGIS

![Inspection grib2 dans Qgis](https://raw.githubusercontent.com/thanhhale7/images/main/open-grib-qgis-resized.gif)

### Mettre les données en bases de données

Cela peut surtout s'avérer utile pour mettre des données attributaires comme les stations ou les mesures associées prises sur les stations. Il est ensuite plus facile de les manipuler si vous avez des connaissances en SQL. Néanmoins, rien ne vous empêche selon vos préférences de faire tous vos traitements dans des dataframes en Python ou en R.

#### SQLite

C'est un format de fichier qui contient une base de données relationnelle ne nécessitant aucune installation.

En utilisant l’utilitaire `sqlite-utils`, installable via `pip install sqlite-utils`

```bash
sqlite-utils insert meteo_hor.db meteo_hor <(zcat H_01_1850-1859.csv.gz) --delimiter=";”
```

Pour exploiter le fichier généré, vous pouvez lancer une commande du type

```bash
sqlite-utils query meteo_hor.db "SELECT * FROM meteo_hor" --csv
```

Pour en savoir plus, lire [la documentation sur la partie ligne de commande](https://sqlite-utils.datasette.io/en/stable/cli.html#sqlite-utils-command-line-tool)

#### GPKG

C'est un format qui s'appuie sur la base de données SQLite. La particularité est qu'il permet de gérer de la donnée géographique en intégrant des fonctionnalités spatiales du type "recherche toutes stations à moins de 10 km de chez moi".

```bash
ogr2ogr -f GPKG meteo_hor.gpkg -dialect SQLite -sql "SELECT *, MakePoint(cast(LON AS REAL), cast(LAT AS REAL), 4326) AS geometry FROM \"H_01_latest-2023-2024\"" /vsigzip/H_01_latest-2023-2024.csv.gz -nln csv_hor
# Une alternative à l'exemple ci-dessus de passer une fichier pour la requête SQL
# qui évite d'avoir à échapper les guillemets
# Editer le fichier query.sql avec le contenu suivant
# SELECT *, MakePoint(cast(LON AS REAL), cast(LAT AS REAL), 4326) AS geometry FROM "H_01_latest-2023-2024"
ogr2ogr -f GPKG meteo_hor.gpkg -dialect SQLite -sql @query.sql /vsigzip/H_01_latest-2023-2024.csv.gz -nln csv_hor
```

#### Parquet

Ce format permet des sélections rapides même en passant par des fichiers distants, évitant par exemple des téléchargements complets sur votre machine. Il existe une variation dite GeoParquet qui permet de stocker les données géographiques.

L'outil pour facilement manipuler ces fichiers est [l'outil duckdb](https://duckdb.org/) qui peut être appelé en R, Python, dans le navigateur comme en ligne de commande.

```bash
ogr2ogr -f Parquet meteo_hor.parquet -dialect SQLite -sql "SELECT *, MakePoint(cast(LON AS REAL), cast(LAT AS REAL), 4326) AS geometry FROM \"H_01_latest-2023-2024\"" /vsigzip/H_01_latest-2023-2024.csv.gz
```

La différence notable est que la taille du GPKG généré est de l’ordre de 20 fois plus gros que le fichier GeoParquet.

#### PostgreSQL/PostGIS

PostgreSQL est une base de données client/serveur. Elle nécessite une installation sur votre machine ou un serveur distant. Elle peut gérer de très gros volumes de données, étant en concurrence avec des SGBD type Oracle ou MySQL Server.

Si vous manipulez de la donnée géographique, vous ne pourrez pas passer à côté de sa cartouche spatiale PostGIS qui est à ce jour la meilleure du marché dans les SGBD existants.

Vous pouvez si nécessaire consulter [un guide d'installation](https://data.sigea.educagri.fr/download/sigea/supports/PostGIS/distance/initiation/PostGIS\_Installation/co/PostGIS\_Installation.html).

Charger les données dans PostgreSQL avec le client psql (fourni dès l'installation de PostgreSQL/PostGIS) en ligne de commande

```bash
# Les types pourraient être améliorés dans le CREATE TABLE...
# Attention, on passe ici par un service pour la connexion mais il est possible de
# passer la connexion à la base via une connexion de la forme suivante
# psql 'postgres://YourUserName:YourPassword@YourHostname:5432/YourDatabaseName'
psql service=meteo -c "CREATE TABLE IF NOT EXISTS csv_meteo_hor(NUM_POSTE text, NOM_USUEL text, LAT double precision, LON double precision, ALTI integer, AAAAMMJJHH bigint, RR1 text, QRR1 integer, DRR1 text, QDRR1 integer, FF text, QFF integer, DD text, QDD integer, FXY text, QFXY integer, DXY text, QDXY integer, HXY text, QHXY integer, FXI text, QFXI integer, DXI text, QDXI integer, HXI text, QHXI integer, FF2 text, QFF2 integer, DD2 text, QDD2 integer, FXI2 text, QFXI2 integer, DXI2 text, QDXI2 integer, HXI2 text, QHXI2 integer, FXI3S text, QFXI3S integer, DXI3S text, QDXI3S integer, HFXI3S text, QHFXI3S integer, T text, QT integer, TD text, QTD integer, TN text, QTN integer, HTN text, QHTN integer, TX text, QTX integer, HTX text, QHTX integer, DG text, QDG integer, T10 text, QT10 integer, T20 text, QT20 integer, T50 text, QT50 integer, T100 text, QT100 integer, TNSOL text, QTNSOL integer, TN50 text, QTN50 integer, TCHAUSSEE text, QTCHAUSSEE integer, DHUMEC text, QDHUMEC integer, U text, QU integer, UN text, QUN integer, HUN text, QHUN integer, UX text, QUX integer, HUX text, QHUX integer, DHUMI40 text, QDHUMI40 integer, DHUMI80 text, QDHUMI80 integer, TSV text, QTSV integer, PMER text, QPMER integer, PSTAT text, QPSTAT integer, PMERMIN text, QPERMIN integer, GEOP text, QGEOP integer, N text, QN integer, NBAS text, QNBAS integer, CL text, QCL integer, CM text, QCM integer, CH text, QCH integer, N1 text, QN1 integer, C1 text, QC1 integer, B1 text, QB1 integer, N2 text, QN2 integer, C2 text, QC2 integer, B2 text, QCB2 integer, N3 text, QN3 integer, C3 text, QC3 integer, B3 text, QB3 integer, N4 text, QN4 integer, C4 text, QC4 integer, B4 text, QB4 integer, VV text, QVV integer, DVV200 text, QDVV200 integer, WW text, QWW integer, W1 text, QW1 integer, W2 text, QW2 integer, SOL text, QSOL integer, SOLNG text, QSOLNG integer, TMER text, QTMER integer, VVMER text, QVVMER integer, ETATMER text, QETATMER integer, DIRHOULE text, QDIRHOULE integer, HVAGUE text, QHVAGUE integer, PVAGUE text, QPVAGUE integer, HNEIGEF text, QHNEIGEF integer, NEIGETOT text, QNEIGETOT integer, TSNEIGE text, QTSNEIGE integer, TUBENEIGE text, QTUBENEIGE integer, HNEIGEFI3 text, QHNEIGEFI3 integer, HNEIGEFI1 text, QHNEIGEFI1 integer, ESNEIGE text, QESNEIGE integer, CHARGENEIGE text, QCHARGENEIGE integer, GLO text, QGLO integer, GLO2 text, QGLO2 integer, DIR text, QDIR integer, DIR2 text, QDIR2 integer, DIF text, QDIF integer, DIF2 text, QDIF2 integer, UV text, QUV integer, UV2 text, QUV2 integer, UV_INDICE text, QUV_INDICE integer, INFRAR text, QINFRAR integer, INFRAR2 text, QINFRAR2 integer, INS text, QINS integer, INS2 text, QINS2 integer, TLAGON text, QTLAGON integer, TVEGETAUX text, QTVEGETAUX integer, ECOULEMENT text, QECOULEMENT integer);"
zcat H_01_1850-1859.csv.gz | psql service=meteo -c "COPY csv_meteo_hor (NUM_POSTE, NOM_USUEL, LAT, LON, ALTI, AAAAMMJJHH, RR1, QRR1, DRR1, QDRR1, FF, QFF, DD, QDD, FXY, QFXY, DXY, QDXY, HXY, QHXY, FXI, QFXI, DXI, QDXI, HXI, QHXI, FF2, QFF2, DD2, QDD2, FXI2, QFXI2, DXI2, QDXI2, HXI2, QHXI2, FXI3S, QFXI3S, DXI3S, QDXI3S, HFXI3S, QHFXI3S, T, QT, TD, QTD, TN, QTN, HTN, QHTN, TX, QTX, HTX, QHTX, DG, QDG, T10, QT10, T20, QT20, T50, QT50, T100, QT100, TNSOL, QTNSOL, TN50, QTN50, TCHAUSSEE, QTCHAUSSEE, DHUMEC, QDHUMEC, U, QU, UN, QUN, HUN, QHUN, UX, QUX, HUX, QHUX, DHUMI40, QDHUMI40, DHUMI80, QDHUMI80, TSV, QTSV, PMER, QPMER, PSTAT, QPSTAT, PMERMIN, QPERMIN, GEOP, QGEOP, N, QN, NBAS, QNBAS, CL, QCL, CM, QCM, CH, QCH, N1, QN1, C1, QC1, B1, QB1, N2, QN2, C2, QC2, B2, QCB2, N3, QN3, C3, QC3, B3, QB3, N4, QN4, C4, QC4, B4, QB4, VV, QVV, DVV200, QDVV200, WW, QWW, W1, QW1, W2, QW2, SOL, QSOL, SOLNG, QSOLNG, TMER, QTMER, VVMER, QVVMER, ETATMER, QETATMER, DIRHOULE, QDIRHOULE, HVAGUE, QHVAGUE, PVAGUE, QPVAGUE, HNEIGEF, QHNEIGEF, NEIGETOT, QNEIGETOT, TSNEIGE, QTSNEIGE, TUBENEIGE, QTUBENEIGE, HNEIGEFI3, QHNEIGEFI3, HNEIGEFI1, QHNEIGEFI1, ESNEIGE, QESNEIGE, CHARGENEIGE, QCHARGENEIGE, GLO, QGLO, GLO2, QGLO2, DIR, QDIR, DIR2, QDIR2, DIF, QDIF, DIF2, QDIF2, UV, QUV, UV2, QUV2, UV_INDICE, QUV_INDICE, INFRAR, QINFRAR, INFRAR2, QINFRAR2, INS, QINS, INS2, QINS2, TLAGON, QTLAGON, TVEGETAUX, QTVEGETAUX, ECOULEMENT, QECOULEMENT) FROM STDIN WITH DELIMITER ';' CSV HEADER;"
psql service=meteo -c "SELECT AddGeometryColumn('public','csv_meteo_hor','geom',4326,'POINT',2);"
psql service=meteo -c "UPDATE csv_meteo_hor SET geom = ST_SetSRID(ST_MakePoint(LON, LAT), 4326)"
psql service=meteo -c "CREATE TABLE IF NOT EXISTS stations_meteo_hor AS SELECT DISTINCT num_poste, nom_usuel, lat, lon, alti FROM csv_meteo_hor;"
psql service=meteo -c "SELECT AddGeometryColumn('public','stations_meteo_hor','geom',4326,'POINT',2);"
psql service=meteo -c "UPDATE stations_meteo_hor SET geom = ST_SetSRID(ST_MakePoint(LON, LAT), 4326)"
```

#### PostgreSQL/PostGIS - Python avec Psycopg2

```python
import gzip
import psycopg2

# Possibility 1: use PGSERVICE. Use PGPASSFILE also PGSERVICEFILE
# export PGSERVICE=geodata
# with psycopg2.connect() as conn:
# connexion string is of the form postgres://YourUserName:YourPassword@YourHostname:5432/YourDatabaseName
connexion = 'postgres://user:password@localhost:5432/meteo'
create_table = """CREATE TABLE IF NOT EXISTS csv_meteo_hor(NUM_POSTE text, NOM_USUEL text, LAT double precision, LON double precision, ALTI integer, AAAAMMJJHH bigint, RR1 text, QRR1 integer, DRR1 text, QDRR1 integer, FF text, QFF integer, DD text, QDD integer, FXY text, QFXY integer, DXY text, QDXY integer, HXY text, QHXY integer, FXI text, QFXI integer, DXI text, QDXI integer, HXI text, QHXI integer, FF2 text, QFF2 integer, DD2 text, QDD2 integer, FXI2 text, QFXI2 integer, DXI2 text, QDXI2 integer, HXI2 text, QHXI2 integer, FXI3S text, QFXI3S integer, DXI3S text, QDXI3S integer, HFXI3S text, QHFXI3S integer, T text, QT integer, TD text, QTD integer, TN text, QTN integer, HTN text, QHTN integer, TX text, QTX integer, HTX text, QHTX integer, DG text, QDG integer, T10 text, QT10 integer, T20 text, QT20 integer, T50 text, QT50 integer, T100 text, QT100 integer, TNSOL text, QTNSOL integer, TN50 text, QTN50 integer, TCHAUSSEE text, QTCHAUSSEE integer, DHUMEC text, QDHUMEC integer, U text, QU integer, UN text, QUN integer, HUN text, QHUN integer, UX text, QUX integer, HUX text, QHUX integer, DHUMI40 text, QDHUMI40 integer, DHUMI80 text, QDHUMI80 integer, TSV text, QTSV integer, PMER text, QPMER integer, PSTAT text, QPSTAT integer, PMERMIN text, QPERMIN integer, GEOP text, QGEOP integer, N text, QN integer, NBAS text, QNBAS integer, CL text, QCL integer, CM text, QCM integer, CH text, QCH integer, N1 text, QN1 integer, C1 text, QC1 integer, B1 text, QB1 integer, N2 text, QN2 integer, C2 text, QC2 integer, B2 text, QCB2 integer, N3 text, QN3 integer, C3 text, QC3 integer, B3 text, QB3 integer, N4 text, QN4 integer, C4 text, QC4 integer, B4 text, QB4 integer, VV text, QVV integer, DVV200 text, QDVV200 integer, WW text, QWW integer, W1 text, QW1 integer, W2 text, QW2 integer, SOL text, QSOL integer, SOLNG text, QSOLNG integer, TMER text, QTMER integer, VVMER text, QVVMER integer, ETATMER text, QETATMER integer, DIRHOULE text, QDIRHOULE integer, HVAGUE text, QHVAGUE integer, PVAGUE text, QPVAGUE integer, HNEIGEF text, QHNEIGEF integer, NEIGETOT text, QNEIGETOT integer, TSNEIGE text, QTSNEIGE integer, TUBENEIGE text, QTUBENEIGE integer, HNEIGEFI3 text, QHNEIGEFI3 integer, HNEIGEFI1 text, QHNEIGEFI1 integer, ESNEIGE text, QESNEIGE integer, CHARGENEIGE text, QCHARGENEIGE integer, GLO text, QGLO integer, GLO2 text, QGLO2 integer, DIR text, QDIR integer, DIR2 text, QDIR2 integer, DIF text, QDIF integer, DIF2 text, QDIF2 integer, UV text, QUV integer, UV2 text, QUV2 integer, UV_INDICE text, QUV_INDICE integer, INFRAR text, QINFRAR integer, INFRAR2 text, QINFRAR2 integer, INS text, QINS integer, INS2 text, QINS2 integer, TLAGON text, QTLAGON integer, TVEGETAUX text, QTVEGETAUX integer, ECOULEMENT text, QECOULEMENT integer)"""

with psycopg2.connect(connexion) as conn:
    cur = conn.cursor()
    cur.execute("""SELECT * FROM pg_catalog.pg_tables WHERE schemaname != 'pg_catalog' AND schemaname != 'information_schema';""")

    for record in cur:
        print(record)
    cur.execute(create_table)
    with gzip.open('H_01_1850-1859.csv.gz','rb') as infile:
        cur.copy_expert("COPY csv_meteo_hor (NUM_POSTE, NOM_USUEL, LAT, LON, ALTI, AAAAMMJJHH, RR1, QRR1, DRR1, QDRR1, FF, QFF, DD, QDD, FXY, QFXY, DXY, QDXY, HXY, QHXY, FXI, QFXI, DXI, QDXI, HXI, QHXI, FF2, QFF2, DD2, QDD2, FXI2, QFXI2, DXI2, QDXI2, HXI2, QHXI2, FXI3S, QFXI3S, DXI3S, QDXI3S, HFXI3S, QHFXI3S, T, QT, TD, QTD, TN, QTN, HTN, QHTN, TX, QTX, HTX, QHTX, DG, QDG, T10, QT10, T20, QT20, T50, QT50, T100, QT100, TNSOL, QTNSOL, TN50, QTN50, TCHAUSSEE, QTCHAUSSEE, DHUMEC, QDHUMEC, U, QU, UN, QUN, HUN, QHUN, UX, QUX, HUX, QHUX, DHUMI40, QDHUMI40, DHUMI80, QDHUMI80, TSV, QTSV, PMER, QPMER, PSTAT, QPSTAT, PMERMIN, QPERMIN, GEOP, QGEOP, N, QN, NBAS, QNBAS, CL, QCL, CM, QCM, CH, QCH, N1, QN1, C1, QC1, B1, QB1, N2, QN2, C2, QC2, B2, QCB2, N3, QN3, C3, QC3, B3, QB3, N4, QN4, C4, QC4, B4, QB4, VV, QVV, DVV200, QDVV200, WW, QWW, W1, QW1, W2, QW2, SOL, QSOL, SOLNG, QSOLNG, TMER, QTMER, VVMER, QVVMER, ETATMER, QETATMER, DIRHOULE, QDIRHOULE, HVAGUE, QHVAGUE, PVAGUE, QPVAGUE, HNEIGEF, QHNEIGEF, NEIGETOT, QNEIGETOT, TSNEIGE, QTSNEIGE, TUBENEIGE, QTUBENEIGE, HNEIGEFI3, QHNEIGEFI3, HNEIGEFI1, QHNEIGEFI1, ESNEIGE, QESNEIGE, CHARGENEIGE, QCHARGENEIGE, GLO, QGLO, GLO2, QGLO2, DIR, QDIR, DIR2, QDIR2, DIF, QDIF, DIF2, QDIF2, UV, QUV, UV2, QUV2, UV_INDICE, QUV_INDICE, INFRAR, QINFRAR, INFRAR2, QINFRAR2, INS, QINS, INS2, QINS2, TLAGON, QTLAGON, TVEGETAUX, QTVEGETAUX, ECOULEMENT, QECOULEMENT) FROM STDIN WITH DELIMITER ';' CSV HEADER;", infile)
    # Dumb here. As there is time series, as much geometry as time.
    # Could report stations in another table
    cur.execute("SELECT AddGeometryColumn('public','csv_meteo_hor','geom',4326,'POINT',2);")
    cur.execute("UPDATE csv_meteo_hor SET geom = ST_SetSRID(ST_MakePoint(LON, LAT), 4326)")
    # Other solution with station in another table
    cur.execute("SELECT AddGeometryColumn('public','stations_meteo_hor','geom',4326,'POINT',2);")
    cur.execute("UPDATE stations_meteo_hor SET geom = ST_SetSRID(ST_MakePoint(LON, LAT), 4326)")
```

#### PostgreSQL/PostGIS - Python avec Pandas

Voir [https://pandas.pydata.org/docs/user\_guide/io.html#insertion-method](https://pandas.pydata.org/docs/user\_guide/io.html#insertion-method)

### Manipuler les données : quelques outils

#### En ligne de commande

Quelques utilitaires intéressants :

* Pour récupérer les données : curl/wget
* Pour manipuler du JSON : jq
* Pour manipuler du CSV : xsv/csvkit
* Pour manipuler des données géographiques vecteur ou raster : ogrinfo/ogr2ogr/gdalinfo/gdalwarp fournis par GDAL
* Pour manipuler des données csv ou passer par du parquet facilement : duckdb

#### En Python

Pensez à passer par des Notebooks Jupyter. Utilisez conda/mamba et des environnements virtuels

Les bibliothèques qui pourraient vous être utiles :

* pandas avec son module “géo” geopandas
* xarray, cfgrib, eccodes pour manipuler les grib2 type Arome ou Arpège
* matplotlib avec cartopy et basemap

Un bon point d’entrée pour des exemples (en particulier pour les données type Arome/Arpege) : [https://github.com/meteofrance/meteonet/](https://github.com/meteofrance/meteonet/tree/master).

#### Logiciel SIG QGIS

Pour une analyse visuelle rapide, vous pouvez passer par QGIS qui permet de gérer les WMS, les CSV et les GeoJSON.

Vous pouvez vous référer pour un tuto rapide à [https://tutoqgis.cnrs.fr](https://tutoqgis.cnrs.fr/).

Vous pouvez également vous référer à [la documentation officielle du projet QGIS](https://www.qgis.org/fr/docs/index.html).

### Utiliser les API de Météo-France

Bien que les données soient ouvertes sous licence Etalab, les APIs nécessitent de créer un compte sur [https://portail-api.meteofrance.fr](https://portail-api.meteofrance.fr/) (pour éviter les abus et pouvoir suivre les usages).

Après création d’un compte, il est possible souscrire à des APIs. Par défaut, le compte ne permet rien sauf de souscrire à des APIs. Quand on a choisi une API, on peut souscrire puis commencer à utiliser pour son usage.

La page d’accueil du site reproduite ci-dessous est très claire à ce propos.

![Page d'accueil du site des API de Météo-France](https://raw.githubusercontent.com/thanhhale7/images/main/Se%CC%81lection\_999\(025\).png)

#### Exemple avec QGIS

Ajout de WMS Arome

![Exemple d'ajout de WMS Arome](https://raw.githubusercontent.com/thanhhale7/images/main/qgis-arome-wms-resized-1280w.gif)
