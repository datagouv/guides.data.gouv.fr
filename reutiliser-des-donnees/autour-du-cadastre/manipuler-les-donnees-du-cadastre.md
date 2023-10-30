# Manipuler les données du cadastre

{% hint style="success" %}
Dans cette section, nous vous guidons dans la manipulation des données du cadastre. Nous vous indiquons notamment comment :
- **télécharger les données**
- **rechercher des parcelles**
- **accéder aux fonds de plan du cadastre**
- **parser les données Edigeo**
- **faire l'intégration métiers parcelle et MAJIC (Fichiers des locaux et des parcelles des personnes morales)**
{% endhint %}

> Si vous avez d'autres questions, ou si vous souhaitez que nous vous aidions sur d'autres aspects de l'utilisation du cadastre, **[n'hésitez pas à nous l'indiquer ici](https://tally.so/r/wgdoJl) pour que nous puissions compléter ce guide**.

## Télécharger les données

{% hint style="info" %} **Les versions du plan cadastral**

Il existe aujourd'hui **trois versions** des données du plan cadastral :
- **la version de la Direction générale des finances publiques (DGFiP)** : Disponible en prenant les fichiers *Edigeo*, *Edigeo-cc*, *DXF*, *DXF-cc* et *TIFF* sur [cadastre.data.gouv.fr](https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise).
    - Elle est mise à jour tous les 3 mois environ, théoriquement aux 01/01, 01/04, 01/07 et 01/10 (il s'agit plutôt des dates d'extraction et les données sont réellement mises à disposition quelques jours après). Dans le cadre du [service public de la donnée (SPD)](https://www.data.gouv.fr/fr/pages/spd/reference/), la Direction interministérielle du numérique (DINUM) est le diffuseur de ces données pour le compte de la DGFiP ;
- **la version d'Etalab** : elle consiste en un assemblage de données, qui s'appuie sur les données Edigeo (Plan Cadastral Informatisé issu de la DGFiP, ci-dessus) et les données de Strasbourg (hors PCI). Les formats proposés sont du *GeoJSON* et du *SHP*. Il s'agit d'un produit DINUM. Il présente quelques erreurs en particulier du fait de l'interprétation des géométries issues du format Edigeo. Cette version étant dépendante de la version précédente mais nécessitant plus de traitement, il nous faut dans les faits quelques semaines pour les mettre à disposition réellement.
- **la version de l'IGN** : proposée via le produit PCI Express. La mise à jour n'est pas alignée avec celle des données Edigéo mises à disposition sur cadastre.data.gouv.fr, l'IGN nous a indiqué penser à augmenter sa fréquence de mise à jour en particulier avec son travail en collaboration avec le cadastre dans le cadre de [la RPCU (Représentation Parcellaire Cadastrale Unique)](https://geoservices.ign.fr/rpcu). {% endhint %}

Pour télécharger les données, vous pouvez vous rendre sur :
- [https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise](https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise), pour la version de la DGFiP ;
- [cadastre.data.gouv.fr](https://cadastre.data.gouv.fr/data/etalab-cadastre/), pour la version d'Etalab ;
- [la page "PARCELLAIRE EXPRESS (PCI)" du site Geoservices IGN](https://geoservices.ign.fr/parcellaire-express-pci), pour la version de l'IGN.

## Rechercher des parcelles

Il est possible de passer par [le module Cadastre de l'API Carto](https://apicarto.ign.fr/api/doc/cadastre#/Parcelle/get_cadastre_parcelle). C'est une surcouche qui au WFS de l'IGN qui se traduit côté code par <https://github.com/IGNF/apicarto/blob/master/middlewares/gpuWfsClient.js#L14> qui utilise les données cadastre de PCI Express ou de la BD Parcellaire (produit historique non maintenu depuis 2019).

Un exemple est le suivant :

[![Recherche parcelles API carto](images/exemple-recherche-parcelles.png)](https://apicarto.ign.fr/api/cadastre/parcelle?code_insee=44109&section=EX&numero=0080)

Vous pouvez aussi ouvrir [le lien pour voir le résultat dans un navigateur](https://apicarto.ign.fr/api/cadastre/parcelle?code_insee=44109&section=EX&numero=0080)

{% hint style="danger" %} **Limites**

Il existe un décalage dans le temps de mise à jour entre les parcelles PCI Express et les données du cadastre que nous mettons à disposition sur <https://cadastre.data.gouv.fr>. {% endhint %}

## Accéder aux fonds de plan du cadastre

Plusieurs solutions sont disponibles pour accéder aux fonds de plan du cadastre, parmi lesquelles :

- [WMS accès cadastre DGFiP](https://www.cadastre.gouv.fr/scpc/pdf/Guide_WMS_fr.pdf). La principale limitation de ce WMS est qu'il faut demander des images dont la taille doit être comprise entre 100x100 et au maximum 1280x1024. Il est possible de passer par un TMS via l'url `http://tms.cadastre.openstreetmap.fr/*/tout/{z}/{x}/{y}.png` (voir https://lists.openstreetmap.org/pipermail/talk-fr/2015-February/075223.html)

![Un aperçu de la configuration du TMS dans QGIS](images/connexion-xyz-qgis-cadastre.png)

- les tuiles vectorielles que nous mettons à disposition. Elles contiennent les géométries du produit Cadastre Etalab. Un tutoriel existant décrit comment les exploiter dans le cadre Web https://guides.etalab.gouv.fr/apis-geo/3-tuiles-vecteur.html#l-alternative-des-tuiles-vecteur-de-l-ign. Il est aussi possible depuis la version 3.14 du [logiciel bureautique SIG OpenSource nommé QGIS](https://www.qgis.org/fr/site/) comme illustré ci-dessous.

![Un aperçu de la configuration de la connexion aux tuiles vectorielles dans QGIS](images/connexion-tuiles-vectorielles-cadastre-qgis.png)

- IGN WMS cadastre

La couche principale est `CADASTRALPARCELS.PARCELLAIRE_EXPRESS` du service WMS https://wxs.ign.fr/essentiels/geoportail/r/wms. Cette couche s'appuie sur le produit PCI Express.

Il existe de nombreuses autres couches d'information liées aux cadastre proposées par l'IGN. Nous vous invitons à les chercher depuis la page https://geoservices.ign.fr/documentation/services en prenant les CSV des géoservices et de la Géoplateforme qui remplacera dans les mois à venir les services OGC de l'IGN.

Une autre couche intéressante est celle de "Décalage de la representation cadastrale" `CADASTRALPARCELS.HEATMAP` disponible sur le WMS https://wxs.ign.fr/parcellaire/geoportail/r/wms et consultable aussi sur [le Géoportail](https://www.geoportail.gouv.fr/carte?c=-1.0309918634157356,46.551302493795134&z=6&l0=ORTHOIMAGERY.ORTHOPHOTOS::GEOPORTAIL:OGC:WMTS(1)&l1=GEOGRAPHICALGRIDSYSTEMS.PLANIGNV2::GEOPORTAIL:OGC:WMTS(1)&l2=CADASTRALPARCELS.HEATMAP::GEOPORTAIL:OGC:WMTS(0.9)&l3=CADASTRALPARCELS.PARCELLAIRE_EXPRESS::GEOPORTAIL:OGC:WMTS(1)&permalink=yes) qui permet de voir le décalage entre les contours des parcelles et le terrain. Cette couche ne couvre pas l'ensemble du territoire même si elle le couvre en grande partie. Beaucoup croient à tort que le contour des parcelles est très fiable alors qu'il ne s'agit que d'une représentation graphique imprécise qui servait à se repérer, seul les actes de vente ayant une valeur juridique, et qui a été établie avant que les photos aériennes soit généralisées et de grande précision. Il faut aussi noter que les parcelles aux limites entre communes se recoupent ou donnent un "no man land" car historiquement, chaque commune gérait séparément ses parcelles, aucune ne se préoccupait de la limite exacte avec les communes limitrophes de son territoire.

Voici un exemple de décalage de parcelles avec différents niveaux de précision

![Décalage parcellaire. Exemple sur le 73](images/exemple-decalage-parcellaire.png)

## Parser les données Edigeo

### Rappel

EDIGEO veut dire "Échange de données informatisées dans le domaine de l'information géographique". C'est une norme. C'est principalement la norme d'échange des données du Plan Cadastral Informatisé (PCI). Pour aller plus loin, voir [l'article Wikipedia associé](https://fr.wikipedia.org/wiki/EDIGEO) et [la documentation "STANDARD D’ÉCHANGE DES OBJETS DU PLAN CADASTRAL INFORMATISÉ FONDÉ SUR LA NORME EDIGéO" datant de 2013](https://raw.githubusercontent.com/etalab/edigeo-parser/master/resources/standard_edigeo_2013.pdf)

### Logiciels/bibliothèques pour les exploiter

Pour parser les données Edigeo, plusieurs méthodes sont possibles. Vous pouvez notamment :
- [Parser en Javascript. C'est ce parser qui est utilisé pour produire les données Etalab cadastre](https://github.com/etalab/edigeo-parser)
- [Utiliser GDAL](https://gdal.org/drivers/vector/edigeo.html)
- [Utiliser cet outil edigeoToGeojson](https://github.com/DoFabien/edigeoToGeojson)
- [Parser en Dotnet. Ce parser est utilisé par le GIRTEC pour son intégration en base de données](https://github.com/ChristopheVergon/Integrateur_edigeo)
- Parser MAJIC fourni par le connecteur MAJIC associé [au logiciel propriétaire FME](https://www.veremes.com/produits/majic)

## Faire l'intégration métier parcelles et MAJIC

Il faut distinguer les données PCI des données MAJIC. Les données PCI sont la représentation graphique des parcelles mais aucune information associée aux propriétaires n'est fournie. Les données MAJIC (on parle aussi de matrice cadastrale) contiennent elles les données liées aux bâtiments, aux propriétaires. Elles sont à caractère personnel donc pas ouvertes sauf exception des personnes morales qui sont elles ouvertes. Elles peuvent être utile selon votre usage mais si vous êtes en particulier une collectivité, vous voudrez les données non ouvertes car vous aurez besoin d'un base exhaustive liée à la propriété.

Le [**jeu de données "Fichiers des locaux et des parcelles des personnes morales" (MAJIC)**](https://www.data.gouv.fr/fr/datasets/fichiers-des-locaux-et-des-parcelles-des-personnes-morales/) contient trois fichiers principaux :
- Les fichiers des personnes morales recensent au niveau départemental les personnes morales qui apparaissent dans la documentation cadastrale, en situation du 1er janvier de l'année de référence (n ou n-1 selon la date de téléchargement), comme détentrices de droits réels sur des immeubles, à l'exception des sociétés unipersonnelles et des entrepreneurs individuels ;
- Les fichiers des propriétés bâties (locaux) restituent les références cadastrales et l'adresse des locaux, complétés du code droit, de la dénomination et de la forme juridique des personnes morales propriétaires ;
- Les fichiers des propriétés non bâties (parcelles) restituent les références cadastrales, l'adresse, la contenance et la nature de culture des parcelles, complétées du code droit, de la dénomination et de la forme juridique des personnes morales propriétaires.

**Il est possible de réaliser une intégration métier parcelles et MAJIC. Plusieurs solutions sont possibles**

### Open Source

Vous pouvez utiliser le [Plugin cadastre QGIS](https://github.com/3liz/QgisCadastrePlugin) et [récupérer les données du cadastre via ce plugin depuis des codes INSEE](https://github.com/3liz/QgisCadastrePlugin/blob/master/docs/extension-qgis/donnees.md).


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

### Propriétaires

Deux outils sont possibles :

- [ESRI (produits ArcGIS)](https://www.arcopole.fr/content/cadastre)
- [FME MAJIC](https://www.veremes.com/produits/majic)

[https://www.impots.gouv.fr/particulier/questions/comment-puis-je-acceder-la-documentation-cadastrale]

## Les données et produits gravitant autour des parcelles de l'IGN

- [les données Demandes de Valeurs Foncières (DVF) géolocalisées](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres-geolocalisees/)
- [le produit BAN PLUS](https://geoservices.ign.fr/ban-plus) qui permet de lier l'adresse au bâti. Vous pouvez aussi regarder sur le même sujet [la Base de Données Nationale des Bâtiments (BDNB)](https://www.data.gouv.fr/fr/datasets/base-de-donnees-nationale-des-batiments/)
- le [Registre Parcellaire Graphique (RPG)](https://geoservices.ign.fr/rpg), utilisé pour les instructions des aides européennes de la Politique Agricole Commune (PAC). Vous pouvez aussi aller voir les données des [Parcelles en Agriculture Biologique (AB) déclarées à la PAC](https://www.data.gouv.fr/fr/datasets/parcelles-en-agriculture-biologique-ab-declarees-a-la-pac/)
- les parcelles protégées du Conservatoire du littoral. Elles sont disponibles sous forme WFS dans les services proposés par l'IGN (voir les CSV déjà mentionnés)
- [les délimitations parcellaires AOC viticoles (INAO)](https://www.data.gouv.fr/fr/datasets/delimitation-parcellaire-des-aoc-viticoles-de-linao/)
- [le Géoportail de l'urbanisme](https://www.geoportail-urbanisme.gouv.fr/) dont les PLU s'appuient sur les parcelles du cadastre.
