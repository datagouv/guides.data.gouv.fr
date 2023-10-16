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

Il existe aujourd'hui trois versions des données du plan cadastral :
- **la version de la Direction générale des finances publiques (DGFiP)** : elle est disponible en prenant les fichiers Edigeo, Edigeo-cc, DXF, DXF-cc et TIFF sur [cadastre.data.gouv.fr](https://cadastre.data.gouv.fr/). La DINUM est le diffuseur des données pour le compte de la DGFIP dans le cadre du Service public de la donnée (SPD). Elle est mise à jour tous les 3 mois environ. Cette version est mise à jour tous les 3 mois, théoriquement Au 1er janvier, 1er avril, 1er juillet et 1er octobre. En fait, il faut plutôt considérer ces dates comme celle d'extraction mais il nous faut dans les faits quelques jours après réception des données de la DGFIP pour les mettre à disposition réellement;
- **la version d'Etalab** : elle consiste en un assemblage des données qui s'appuie sur les données Edigeo (PCI issu de la DGFIP) et les données de Strasbourg (hors PCI). Les formats de sortie sont du GeoJSON et du SHP, des formats usuels alors que le format natif de la DGFIP, l'Edigeo est plus difficile à réutiliser. Il s'agit d'un produit DINUM. Il présente quelques erreurs en particulier du fait de l'interprétation des géométries issues du format Edigeo. Cette version étant dépendante de la version précédente mais nécessitant plus de traitement, il nous faut dans les faits quelques semaines pour les mettre à disposition réellement.
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

- [WMS accès cadastre DGFIP](https://www.cadastre.gouv.fr/scpc/pdf/Guide_WMS_fr.pdf). La principale limitation de ce WMS est qu'il faut demander des images dont la taille doit être comprise entre 100x100 et au maximum 1280x1024. Il est possible de passer par un TMS via l'url `http://tms.cadastre.openstreetmap.fr/*/tout/{z}/{x}/{y}.png` (voir https://lists.openstreetmap.org/pipermail/talk-fr/2015-February/075223.html)

![Un aperçu de la configuration du TMS dans QGIS](images/connexion-xyz-qgis-cadastre.png)

- les tuiles vectorielles que nous mettons à disposition. Elles contiennent les géométries du produit Cadastre Etalab. Un tutoriel existant décrit comment les exploiter dans le cadre Web https://guides.etalab.gouv.fr/apis-geo/3-tuiles-vecteur.html#l-alternative-des-tuiles-vecteur-de-l-ign. Il est aussi possible depuis la version 3.14 du [logiciel bureautique SIG OpenSource nommé QGIS](https://www.qgis.org/fr/site/) comme illustré ci-dessous.

![Un aperçu de la configuration de la connexion aux tuiles vectorielles dans QGIS](images/connexion-tuiles-vectorielles-cadastre-qgis.png)

- IGN WMS cadastre

Produits liant l'adresse au bâti

WFS
- Base Adresse Nationale BAN (DATA.GOUV.FR)
- BAN PLUS Lien adresse_support
- BAN PLUS Lien adresse_parcelle
- BAN PLUS Lien bati_parcelle
- BAN PLUS Lien adresse_bati
- BAN PLUS Lien adresse

- Parcellaire Express (PCI) parcelle
- Parcelles cadastrales
- PARCELLE
- Parcellaire Express (PCI) parcelle
- Decalage de la representation cadastrale
- Parcellaire Express (PCI)

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


```
processing.run("cadastre:telechargeur_edigeo_communal", {'LISTE_CODE_INSEE':'44109,44143,44162,44026,44190,44215','FILTRE':'','DOSSIER':'/tmp/cadastre-out','DATE':'latest','URL_TEMPLATE':'https://cadastre.data.gouv.fr/data/dgfip-pci-vecteur/{date}/edigeo/feuilles/{departement}/{commune}/'})
```

### Propriétaires

Deux outils sont possibles :

- [ESRI (produits ArcGIS)](https://www.arcopole.fr/content/cadastre)
- [FME MAJIC](https://www.veremes.com/produits/majic)

[https://www.impots.gouv.fr/particulier/questions/comment-puis-je-acceder-la-documentation-cadastrale]
