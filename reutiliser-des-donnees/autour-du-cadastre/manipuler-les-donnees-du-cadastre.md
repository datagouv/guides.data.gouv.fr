# Manipuler les données du cadastre

{% hint style="success" %}
Dans cette section, nous vous guidons dans la manipulation des données du cadastre. Nous vous indiquons notamment comment :

* **télécharger les données**
* **rechercher des parcelles**
* **accéder aux fonds de plan du cadastre**
* **parser les données Edigeo**
* **faire l'intégration métiers parcelle et MAJIC (Fichiers des locaux et des parcelles des personnes morales)**
{% endhint %}

> Si vous avez d'autres questions, ou si vous souhaitez que nous vous aidions sur d'autres aspects de l'utilisation du cadastre, [**n'hésitez pas à nous l'indiquer ici**](https://tally.so/r/wgdoJl) **pour que nous puissions compléter ce guide**.

## Télécharger les données

{% hint style="info" %}
**Les versions du plan cadastral**

Il existe aujourd'hui **trois versions** des données du plan cadastral :

*   **la version de la Direction générale des finances publiques (DGFiP)**

    Elle est mise à jour tous les 3 mois environ, théoriquement aux 01/01, 01/04, 01/07 et 01/10 (il s'agit plutôt des dates d'extraction, les données sont réellement mises à disposition quelques jours après). Dans le cadre du [service public de la donnée (SPD)](https://www.data.gouv.fr/fr/pages/spd/reference/), la Direction interministérielle du numérique (DINUM) diffuse ces données pour le compte de la DGFiP. Plus d'informations sont disponibles sur [cette page](https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise) ;
*   **la version d'Etalab**

    Elle consiste en un assemblage de données, qui s'appuie sur les données Edigeo (Plan Cadastral Informatisé issu de la DGFiP, ci-dessus) et les données de Strasbourg (hors PCI). Elle peut présenter quelques erreurs, en particulier du fait de l'interprétation des géométries issues du format Edigeo. Les formats proposés sont du _GeoJSON_ et du _SHP_. Cette version étant dépendante de la version précédente mais nécessitant plus de traitement, elle requiert plusieurs semaines pour sa mise à disposition, à partir de la réception des données transmises par la DGFiP. Il s'agit d'un produit de la Direction interministérielle du numérique (DINUM). Plus d'informations sont disponibles sur [cette page](https://cadastre.data.gouv.fr/datasets/cadastre-etalab) ;
*   **la version de l'Institut national de l'information géographique et forestière (IGN)** : proposée via le produit PCI Express.

    La mise à jour est effectuée après la mise à disposition des données Edigeo sur [cadastre.data.gouv.fr](https://github.com/etalab/guides.data.gouv.fr/blob/main/reutiliser-des-donnees/autour-du-cadastre/cadastre.data.gouv.fr).
{% endhint %}

Pour télécharger les données, vous pouvez vous rendre sur :

* **Pour la version de la DGFiP** : [cadastre.data.gouv.fr/datasets/plan-cadastral-informatise](https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise) (formats _Edigeo_, _Edigeo-cc_, _DXF-PCI_, _DXF-PCI-cc_, _TIFF_) ;
* **Pour la version d'Etalab** : [cadastre.data.gouv.fr/data/etalab-cadastre](https://cadastre.data.gouv.fr/data/etalab-cadastre/) (formats _GeoJSON_ et _SHP_). Pour comprendre les identifiants des parcelles utilisés, passez par [cette documentation](https://gist.github.com/ThomasG77/a9b39677d302e2405c18cfe9bc8e462b);
* **Pour la version de l'IGN** : [la page "Parcellaire Express (PCI)" du site Geoservices de l'IGN](https://geoservices.ign.fr/parcellaire-express-pci).

## Focus sur les différentes manières de consommer les données DINUM issues de la DGFIP

### Dans les données version  DGFiP

Vous pouvez prendre les données:
- en choisissant par millésime et par types de fichiers souhaités https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise#millesimes-disponibles-telechargement-direct
- en passant par l'aide au téléchargement qui permet de chercher les données par nom de ressource plutôt qu'avec des codes. L'outil permet aussi de témécharger une commune complète ou un EPCI complet sans devoir prendre chaque feuille de chaque commune

### Dans les données version Etalab

Il existe exactement le même principe que pour les données versions DGFIP avec 
- le téléchargement direct https://cadastre.data.gouv.fr/datasets/cadastre-etalab#millesimes-disponibles-telechargement-direct
- l'aide au téléchargement https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise#aide-au-telechargement

Derrière ces outils se cachent deux URLs:

- la première pour les données les plus récentes, de 2022/2023 à aujourd'hui https://cadastre.data.gouv.fr/data/
- les autres pour les données les plus anciennes, avant 2022 https://files.data.gouv.fr/cadastre/

La bascule de l'un à l'autre est lié au fait qu'on souhaite pouvoir gagner de l'espace disque sur le serveur mettant à disposition les données récentes.
Cette bascule permet de supprimer un certain nombre de jeu de données redondant qui facilite certes la consommation mais qui fait plus que doubler la taille des données pour un millésime.
Nous avons commencé pour des raisons de sauvegarde et d'espace disque à basculer certaines données sur un bucket Minio. Ainsi, à terme https://files.data.gouv.fr/cadastre/ sera amené à disparaitre.

### Accès aux anciennes données via Minio

Comme évoqué, cette manière de récupérer les données s'appuie sur Minio.

Vous pouvez passer par une interface graphique navigable https://object.infra.data.gouv.fr/browser/cadastre/ pour télécharger. L'inconvénient est que l'interface ne permet pas de copier/coller une URL, vous devez cliquer de manière répétée sur chaque fichier souhaité. Cela n'est pas pratique pour automatiser.

Nous vous proposons deux choix pour cela:
- passez par des métadonnées qui listent toutes les URLs directes
- passez par le protocole S3 pour lister et copier les fichiers

#### Approche métadonnées

Pour avoir une liste complète pour un millésime, prenez les fichiers metadata-cadastre-XXXX-XX-XX.csv.gz et metadata-cadastre-XXXX-XX-XX.json.gz

Pour cela, l'URL sera https://object.data.gouv.fr/cadastre/ suivi du nom de fichier soit les URLs suivantes:


|   Année    |                                   CSV                                    |                                    JSON                                    |
|------------|--------------------------------------------------------------------------|----------------------------------------------------------------------------|
| 2017-07-06 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2017-07-06.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2017-07-06.json.gz  |
| 2017-10-12 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2017-10-12.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2017-10-12.json.gz  |
| 2018-01-02 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-01-02.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-01-02.json.gz  |
| 2018-04-03 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-04-03.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-04-03.json.gz  |
| 2018-06-29 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-06-29.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-06-29.json.gz  |
| 2018-10-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-10-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2018-10-01.json.gz  |
| 2019-01-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-01-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-01-01.json.gz  |
| 2019-04-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-04-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-04-01.json.gz  |
| 2019-07-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-07-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-07-01.json.gz  |
| 2019-10-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-10-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2019-10-01.json.gz  |
| 2020-01-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2020-01-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2020-01-01.json.gz  |
| 2020-07-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2020-07-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2020-07-01.json.gz  |
| 2020-10-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2020-10-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2020-10-01.json.gz  |
| 2021-02-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-02-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-02-01.json.gz  |
| 2021-04-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-04-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-04-01.json.gz  |
| 2021-07-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-07-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-07-01.json.gz  |
| 2021-10-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-10-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2021-10-01.json.gz  |
| 2022-01-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2022-01-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2022-01-01.json.gz  |
| 2022-07-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2022-07-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2022-07-01.json.gz  |
| 2022-10-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2022-10-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2022-10-01.json.gz  |
| 2023-01-01 | https://object.data.gouv.fr/cadastre/metadata-cadastre-2023-01-01.csv.gz | https://object.data.gouv.fr/cadastre/metadata-cadastre-2023-01-01.json.gz  |

Sous Linux ou MacOS, il est possible de décompresser les fichiers gz par défaut. Si vous êtes sous Windows, nous vous recommandons d'installer le logiciel libre 7zip en le récupérant depuis https://www.7-zip.fr

En ligne de commande, vous pouvez accéder à la donnée ainsi

```bash
curl -s https://object.data.gouv.fr/cadastre/metadata-cadastre-2017-07-06.csv.gz | zcat - | head
curl -s https://object.data.gouv.fr/cadastre/metadata-cadastre-2023-01-01.csv.gz | zcat - | grep departement
```

#### Approche protocole S3

Pour héberger les données plus anciennes, nous utilisons un produit nommé Minio Server qui permet d'utiliser le protocole S3 défini par Amazon mais sans dépendre d'un hébergeur.
Pour pouvoir facilement consommer les données, vous devez d'abord installer le client qui lui correspond, minio-client ici.
Il vous faudra ensuite suivre les instructions d'installation sur https://min.io/docs/minio/linux/reference/minio-mc.html#quickstart

Attention, la manière de définir l'alias est pour Linux

```bash
mc alias set cadastre_gouv_no_authent https://object.data.gouv.fr '' ''
mc ls cadastre_gouv_no_authent/cadastre/
# Pour lister les années possibles selon les dossiers
mc tree -d 1 cadastre_gouv_no_authent/cadastre
# Liste par type d'entrée
mc ls cadastre_gouv_no_authent/cadastre/etalab-cadastre/
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-image/

# Obtenir les statistiques pour savoir la place que vont prendre les fichiers si on souhaite les télécharger
mc du cadastre_gouv_no_authent/cadastre/dgfip-pci-image/2023-01-01/

# Copier un fichier spécifique
mc cp cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/2021-10-01/edigeo/feuilles/44/44109/edigeo-44109000XC01.tar.bz2 .

# Copier un dossier complet
mc cp --recursive cadastre_gouv_no_authent/cadastre/dgfip-pci-image/2023-01-01/ .

# Faire une recherche
# Marche mais à éviter car plutôt lent de faire une recherche sur un répertoire avec des millions de fichiers
mc find cadastre_gouv_no_authent/cadastre --name "*02001*"
# Choisir plutôt
mc find cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/2021-10-01/edigeo/feuilles/ --name "*02001*"

# Les principaux points d'entrée pour une année
year=2022-01-01

# SHP
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/etalab-cadastre/${year}/shp/departements/
# Retourne une liste de fichiers pour un département
mc ls cadastre_gouv_no_authent/cadastre/etalab-cadastre/${year}/shp/departements/44/
# Retourne une liste de fichiers pour la France
mc ls cadastre_gouv_no_authent/cadastre/etalab-cadastre/${year}/shp/france/

# GeoJSON
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/etalab-cadastre/${year}/geojson/communes/
# Retourne une liste de fichiers pour une commune selon son code département, son code insee
# avec un dossier raw pour les données extraites du cadastre "moins importantes"
mc ls cadastre_gouv_no_authent/cadastre/etalab-cadastre/${year}/geojson/communes/44/44109/

# TIFF
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-image/${year}/tiff/feuilles/
# Retourne une liste de fichiers pour une commune selon son code département, son code insee
# Attention, il n'y a presque plus de fichiers de ce type car ils sont supplantés par les fichiers
# vecteur quand le cadastre est vectorisé
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-image/${year}/tiff/feuilles/08/08462/

# DXF
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/dxf/feuilles/
# Retourne une liste de fichiers pour une commune selon son code département, son code insee
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/dxf/feuilles/73/73065/
# Vous pouvez filtrer cette liste avec une recherche sur une feuille
mc find cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/dxf/feuilles/73/73065/ --name '*DL*'

# DXF-CC
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/dxf-cc/feuilles/
# Retourne une liste de fichiers pour une commune selon son code département, son code insee
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/dxf-cc/feuilles/73/73008/

# EDIGEO
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/edigeo/feuilles/
# Retourne une liste de fichiers pour une commune selon son code département, son code insee
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/edigeo/feuilles/38/38027/

# EDIGEO-CC
# Retourne des dossiers
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/edigeo-cc/feuilles/
# Retourne une liste de fichiers pour une commune selon son code département, son code insee
mc ls cadastre_gouv_no_authent/cadastre/dgfip-pci-vecteur/${year}/edigeo-cc/feuilles/69/69266/
```


Vous pouvez aussi avoir besoin d'automatiser avec un language de programmation. Voici ci-dessous un exemple en Python dont la documentation est disponible sur https://min.io/docs/minio/linux/developers/python/minio-py.html. Il existe d'autres librairies/SDK, en Java, Javascript, .Net, Haskell, C++ pour accéder aux données https://min.io/docs/minio/linux/developers/minio-drivers.html


```python
#!/usr/bin/env python

import minio

from minio import Minio

client = Minio(
    'object.files.data.gouv.fr',
    access_key='',
    secret_key='',
    secure=True
)

print(client.list_buckets())

bucket_name = 'cadastre'
for i in client.list_objects(bucket_name):
    print(i.metadata, i.is_dir, i.object_name, i.size)

# Obtenir des informations
for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/"):
    print(i.metadata, i.is_dir, i.object_name, i.size)

# Pour avoir la liste des fichiers/dossiers qui sont dans l'arborescence
print([i.object_name for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/")])
print([i.object_name for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/2023-01-01/")])
print([i.object_name for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/2023-01-01/tiff/")])
print([i.object_name for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/2023-01-01/tiff/feuilles/")])
# Même principe mais en rajoutant des retours à la ligne pour la lisibilité
print('\n'.join([i.object_name for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/2023-01-01/tiff/feuilles/08/")]))

# Listing recursive d'un dossier puis copie avec la même structure
for i in client.list_objects(bucket_name, prefix="dgfip-pci-image/2023-01-01/tiff/", recursive=True):
    if not i.is_dir:
        print(i.object_name, i.size)
        # first i.object_name is for the object name, the second is to copy with the same structure
        client.fget_object(bucket_name, i.object_name, i.object_name)
```


## Rechercher des parcelles

### Module Cadastre de l'API Carto

Pour rechercher des parcelles, il est possible de passer par [**le module Cadastre de l'API Carto**](https://apicarto.ign.fr/api/doc/cadastre#/Parcelle/get\_cadastre\_parcelle).

Il s'agit d'une surcouche au WFS de l'IGN qui facilite l'utilisation. Ce service s'appuie sur les données de PCI Express ou de [la BD Parcellaire](https://geoservices.ign.fr/bdparcellaire) (produit historique non maintenu depuis 2019).

Si vous êtes intéressé par le code de la surcouche, vous pouvez consulter le projet sur [https://github.com/IGNF/apicarto/](https://github.com/IGNF/apicarto/).

<figure><img src="../../.gitbook/assets/exemple-recherche-parcelles.png" alt=""><figcaption><p>Un exemple de recherche de parcelles avec l'API Carto</p></figcaption></figure>

_Vous pouvez aussi ouvrir_ [_ce lien pour voir le résultat dans un navigateur_](https://apicarto.ign.fr/api/cadastre/parcelle?code\_insee=44109\&section=EX\&numero=0080).

### Alternative au module Cadastre de l'API Carto

Il est aussi de nos jours possible de passer par le géocodeur https://geoservices.ign.fr/documentation/services/services-geoplateforme/geocodage qui fait la recherche d'adresses, de POI (Points d'intérêts) et de parcelles cadastrales.

Pour cela, il vous faudra renseigner les champs `index` à `parcelle`, le champ `departmentcode` avec le code du département, celui `municipalitycode` avec les 3 chiffres du code INSEE après le département, la `section` pour la section et le `number` pour le numéro de parcelle. Le retour de cet appel retourne un GeoJSON dont la représentation pour la parcelle est un point et pas un contour. Si vous souhaitez obtenir le contour, vous devrez passez l'option `returntruegeometry` à `true`. Attention car dans ce cas de figure, le GeoJSON restera un point mais un nouveau champ `truegeometry` dans les "properties" du GeoJSON sera retourné. Si vous voulee que votre GeoJSON contienne uniquement le contour, vous allez devoir faire un appel puis écraser la géométrie ponctuelle du GeoJSON avec celle du champ `truegeometry`.

Cela se traduit en code JavaScript par exemple avec

 ```javascript
const params = new URLSearchParams({
  'index': 'parcel',
  'limit': 10,
  'returntruegeometry': true,
  'departmentcode': '44',
  'municipalitycode': '109',
  'section': 'EX',
  'number': 68
})

const apiUrl = `https://data.geopf.fr/geocodage/search?${params}`;

fetch(apiUrl)
  .then(response => response.json())
  .then(data => {
    console.log('GeoJSON point', data)
    data.features.forEach(feature => {
        feature.geometry = feature.properties.truegeometry
        delete feature.properties.truegeometry
    })
    console.log(data)
  })
  .catch(error => {
    console.log('GeoJSON polygon', error)
  });
```


{% hint style="danger" %}
**Limites**

Il existe un léger décalage dans le temps de mise à jour entre les parcelles PCI Express et les données du cadastre que nous mettons à disposition sur [cadastre.data.gouv.fr](https://cadastre.data.gouv.fr).
{% endhint %}

## Accéder aux fonds de plan du cadastre

Plusieurs solutions sont disponibles pour accéder aux fonds de plan du cadastre, parmi lesquelles :

* [**WMS accès cadastre DGFiP**](https://www.cadastre.gouv.fr/scpc/pdf/Guide\_WMS\_fr.pdf). La limitation principale de ce WMS est qu'il n'est possible de demander que des images dont la taille est comprise entre _100x100_ et _au maximum 1280x1024_. Il est possible de passer par un TMS via l'url `http://tms.cadastre.openstreetmap.fr/*/tout/{z}/{x}/{y}.png` pour contourner cette limitation (voir https://lists.openstreetmap.org/pipermail/talk-fr/2015-February/075223.html).

![Un aperçu de la configuration du TMS dans QGIS](../../.gitbook/assets/connexion-xyz-qgis-cadastre.png)

* **les tuiles vectorielles mises à disposition par la Direction interministérielle du numérique (DINUM)**. Elles contiennent les géométries du produit Cadastre Etalab. Un [tutoriel](https://guides.etalab.gouv.fr/apis-geo/3-tuiles-vecteur.html#l-alternative-des-tuiles-vecteur-de-l-ign) détaille comment les exploiter dans le cadre Web. Il est aussi possible d'accéder aux tuiles vectorielles depuis la version 3.14 du [logiciel bureautique SIG OpenSource nommé QGIS](https://www.qgis.org/fr/site/) comme illustré ci-dessous.

![Un aperçu de la configuration de la connexion aux tuiles vectorielles dans QGIS](../../.gitbook/assets/connexion-tuiles-vectorielles-cadastre-qgis.png)

* **IGN WMS cadastre**. La couche principale est `CADASTRALPARCELS.PARCELLAIRE_EXPRESS` du [service WMS](https://wxs.ign.fr/essentiels/geoportail/r/wms). Celle-ci s'appuie sur le produit PCI Express.

Il existe de nombreuses autres couches d'information liées aux cadastre proposées par l'IGN. Il est possible de les chercher depuis la [page de documentation de Geoservices](https://geoservices.ign.fr/documentation/services), en prenant les fichiers CSV des géoservices de la Géoplateforme.

{% hint style="danger" %}
#### Attention

Contrairement à une croyance commune, **le contour des parcelles n'est pas fiable** : il ne s'agit que d'une représentation graphique imprécise, établie avant que les photos aériennes soient généralisées et de grande précision. **Seuls les actes de vente ont une valeur juridique.**

Il faut aussi noter que les parcelles aux limites entre communes se recoupent ou donnent un "no man land" car historiquement, chaque commune gérait séparément ses parcelles et aucune ne se préoccupait de la limite exacte avec les communes limitrophes de son territoire.

Pour évaluer ce décalage entre les contours des parcelles et le terrain, il est possible d'utiliser la couche "**Décalage de la representation cadastrale**" `CADASTRALPARCELS.HEATMAP` disponible sur [le WMS](https://wxs.ign.fr/parcellaire/geoportail/r/wms) et aussi consultable sur [le Géoportail](https://www.geoportail.gouv.fr/carte?c=-1.0309918634157356,46.551302493795134\&z=6\&l0=ORTHOIMAGERY.ORTHOPHOTOS::GEOPORTAIL:OGC:WMTS\(1\)\&l1=GEOGRAPHICALGRIDSYSTEMS.PLANIGNV2::GEOPORTAIL:OGC:WMTS\(1\)\&l2=CADASTRALPARCELS.HEATMAP::GEOPORTAIL:OGC:WMTS\(0.9\)\&l3=CADASTRALPARCELS.PARCELLAIRE\_EXPRESS::GEOPORTAIL:OGC:WMTS\(1\)\&permalink=yes). Cette couche couvre une grande partie du territoire, mais pas son ensemble.
{% endhint %}

<figure><img src="../../.gitbook/assets/exemple-decalage-parcellaire.png" alt=""><figcaption><p>Un exemple de décalage de parcelles avec différents niveaux de précision</p></figcaption></figure>

## Parser les données Edigeo

EDIGEO signifie "_Échange de données informatisées dans le domaine de l'information géographique_". Il s'agit d'une norme. C'est principalement la norme d'échange des données du Plan Cadastral Informatisé (PCI).

> Pour aller plus loin, vous pouvez consulter [l'article Wikipedia associé](https://fr.wikipedia.org/wiki/EDIGEO) et [la documentation "Standard d'échange des objets du Plan Cadastral Informatisé fondé sur la norme EDIGéO" datant de 2013](https://raw.githubusercontent.com/etalab/edigeo-parser/master/resources/standard\_edigeo\_2013.pdf).

### Logiciels/Bibliothèques pour les exploiter

Pour parser les données Edigeo, plusieurs méthodes sont possibles. Vous pouvez notamment :

* [Parser en Javascript](https://github.com/etalab/edigeo-parser) : c'est ce parser qui est utilisé pour produire les données Etalab Cadastre ;
* [Utiliser GDAL](https://gdal.org/drivers/vector/edigeo.html) ;
* [Utiliser cet outil edigeoToGeojson](https://github.com/DoFabien/edigeoToGeojson) ;
* [Parser en Dotnet](https://github.com/ChristopheVergon/Integrateur\_edigeo) : ce parser est utilisé par le GIRTEC pour son intégration en base de données ;
* Parser MAJIC fourni par le connecteur MAJIC associé [au logiciel propriétaire FME](https://www.veremes.com/produits/majic).

## Faire l'intégration métier parcelles et MAJIC

{% hint style="info" %}
Il est nécessaire de distinguer les données Plan Cadastral Informatisé (PCI) des données MAJIC :

* **Les données PCI** sont la représentation graphique des parcelles, mais aucune information associée aux propriétaires n'est fournie.
* **Les données MAJIC** (on parle aussi de matrice cadastrale) contiennent les données liées aux bâtiments, aux propriétaires. Elles sont à caractère personnel donc non ouvertes (à l'exception de celles se rapportant aux personnes morales, disponibles en open data). Elles peuvent être utiles, mais certains types d'acteurs qui ont besoin d'une base exhaustive liée à la propriété (comme les collectivités) peuvent souhaiter avoir accès aux données non ouvertes.
{% endhint %}

Le [**jeu de données "Fichiers des locaux et des parcelles des personnes morales" (MAJIC)**](https://www.data.gouv.fr/fr/datasets/fichiers-des-locaux-et-des-parcelles-des-personnes-morales/) contient trois fichiers principaux :

* Les fichiers des personnes morales recensent au niveau départemental les personnes morales qui apparaissent dans la documentation cadastrale, en situation du 1er janvier de l'année de référence (n ou n-1 selon la date de téléchargement), comme détentrices de droits réels sur des immeubles, à l'exception des sociétés unipersonnelles et des entrepreneurs individuels ;
* Les fichiers des propriétés bâties (locaux) restituent les références cadastrales et l'adresse des locaux, complétés du code droit, de la dénomination et de la forme juridique des personnes morales propriétaires ;
* Les fichiers des propriétés non bâties (parcelles) restituent les références cadastrales, l'adresse, la contenance et la nature de culture des parcelles, complétées du code droit, de la dénomination et de la forme juridique des personnes morales propriétaires.

**Pour réaliser une intégration métier parcelles et MAJIC, plusieurs solutions sont mises à disposition :**

### Solutions open source

Il est possible d'utiliser le [**Plugin cadastre QGIS**](https://github.com/3liz/QgisCadastrePlugin) et de [récupérer les données du cadastre via ce plugin depuis des codes INSEE](https://github.com/3liz/QgisCadastrePlugin/blob/master/docs/extension-qgis/donnees.md).

Depuis QGIS, dans la console PyQGIS,

```python
import processing

processing.run("cadastre:telechargeur_edigeo_communal", {'LISTE_CODE_INSEE':'44109,44143,44162,44026,44190,44215','FILTRE':'','DOSSIER':'/tmp/cadastre-out','DATE':'latest','URL_TEMPLATE':'https://cadastre.data.gouv.fr/data/dgfip-pci-vecteur/{date}/edigeo/feuilles/{departement}/{commune}/'})
```

En ligne de commande si le plugin cadastre est installé

```bash

qgis_process run cadastre:telechargeur_edigeo_communal -- LISTE_CODE_INSEE=44109,44143,44162,44026,44190,44215 FILTRE= DOSSIER=/tmp/cadastre-out DATE=latest URL_TEMPLATE=https://cadastre.data.gouv.fr/data/dgfip-pci-vecteur/{date}/edigeo/feuilles/{departement}/{commune}/

# déduit de la commande suivante en s'appuyant sur https://docs.qgis.org/3.28/fr/docs/user_manual/processing/standalone.html
qgis_process help cadastre:telechargeur_edigeo_communal
```

### Solutions propriétaires

Deux outils sont disponibles :

* [ESRI (produits ArcGIS)](https://www.arcopole.fr/content/cadastre)
* [FME MAJIC](https://www.veremes.com/produits/majic)
