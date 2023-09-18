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
- **la version de la Direction générale des finances publiques (DGFiP)** : elle est disponible en prenant les fichiers Edigeo, Edigeo-cc, DXF, DXF-cc et TIFF sur [cadastre.data.gouv.fr](https://cadastre.data.gouv.fr/). La DINUM est le diffuseur des données pour le compte de la DGFIP dans le cadre du Service public de la donnée (SPD);
- **la version d'Etalab** : elle consiste en un assemblage des données qui s'appuie sur les données Edigeo (PCI issu de la DGFIP) et les données de Strasbourg (hors PCI). Les formats de sortie sont du GeoJSON et du SHP, des formats usuels alors que le format natif de la DGFIP, l'Edigeo et difficile à réutiliser. Il s'agit d'un produit Etalab. Il présente quelques erreurs en particulier du fait de l'interprétation des géométries issues du format Edigeo. Cette version est mise à jour tous les 3 mois.
- **la version de l'IGN** : proposée via le produit PCI Express (aucune indication sur l'alignement avec les données Edigéo mises à disposition sur cadastre.data.gouv.fr) {% endhint %}

Pour télécharger les données, vous pouvez vous rendre sur : 
- [https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise](https://cadastre.data.gouv.fr/datasets/plan-cadastral-informatise), pour la version de la DGFiP ;
- [cadastre.data.gouv.fr](https://cadastre.data.gouv.fr/), pour la version d'Etalab ;
- [le site Geoservices IGN](https://geoservices.ign.fr/parcellaire-express-pci), pour la version de l'IGN.

## Rechercher des parcelles

Pour rechercher des parcelles, plusieurs services sont disponibles. Vous pouvez notamment utiliser [**ce module**](https://apicarto.ign.fr/api/doc/cadastre#/Parcelle/get_cadastre_parcelle). Il s'agit d'une surcouche au [WFS de l'IGN](https://github.com/IGNF/apicarto/blob/master/middlewares/gpuWfsClient.js#L14) qui utilise les données de PCI express.

{% hint style="danger" %} **Limites**

Il peut exister un décalage entre les parcelles PCI Express et le plan cadastral. En effet, il n'y a aucune indication sur les mises à jour réalisées dans le PCI Express par rapport à la mise à disposition des données Edigeo et du Cadastre Etalab. {% endhint %}

## Accéder aux fonds de plan du cadastre 

Plusieurs solutions sont disponibles pour accéder aux fonds de plan du cadastre, parmi lesquelles :

- [WMS accès cadastre](https://www.cadastre.gouv.fr/scpc/pdf/Guide_WMS_fr.pdf)
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

Pour parser les données Edigeo, plusieurs méthodes sont possibles. Vous pouvez notamment :
- [Parser en Javascript. C'est ce parser qui est utilisé pour produire les données Etalab cadastre](https://github.com/etalab/edigeo-parser)
- [Utiliser GDAL](https://gdal.org/drivers/vector/edigeo.html)
- [Utiliser cet outil edigeoToGeojson](https://github.com/DoFabien/edigeoToGeojson)
- [Parser en Dotnet. Ce parser est utilisé par le GIRTEC pour son intégration en base de données](https://github.com/ChristopheVergon/Integrateur_edigeo)

## Faire l'intégration métier parcelles et MAJIC

Il faut distinguer les données PCI des données MAJIC. Les données PCI sont la représentation graphique des parcelles mais aucune information associée aux propriétaires n'est fournie. Les données MAJIC (on parle aussi de matrice cadastrale) contiennent elles les données liées aux bâtiments, aux propriétaires. Elles sont à caractère personnel donc pas ouvertes sauf exception des personnes morales qui sont elles ouvertes. Elles peuvent être utile selon votre usage mais si vous êtes en particulier une collectivité, vous voudrez les données non ouvertes car vous aurez besoin d'un base exhaustive liée à la propriété.

Le [**jeu de données "Fichiers des locaux et des parcelles des personnes morales" (MAJIC)**](https://www.data.gouv.fr/fr/datasets/fichiers-des-locaux-et-des-parcelles-des-personnes-morales/) contient trois fichiers principaux :
- Les fichiers des personnes morales recensent au niveau départemental les personnes morales qui apparaissent dans la documentation cadastrale, en situation du 1er janvier de l'année de référence (n ou n-1 selon la date de téléchargement), comme détentrices de droits réels sur des immeubles, à l'exception des sociétés unipersonnelles et des entrepreneurs individuels ;
- Les fichiers des propriétés bâties (locaux) restituent les références cadastrales et l'adresse des locaux, complétés du code droit, de la dénomination et de la forme juridique des personnes morales propriétaires ;
- Les fichiers des propriétés non bâties (parcelles) restituent les références cadastrales, l'adresse, la contenance et la nature de culture des parcelles, complétées du code droit, de la dénomination et de la forme juridique des personnes morales propriétaires.

**Il est possible de réaliser une intégration métier parcelles et MAJIC.**

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
