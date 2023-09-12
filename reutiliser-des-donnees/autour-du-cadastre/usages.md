# Usages

## Cadastre vs cadastre vs cadastre

Trois versions dans la nature:

- Celle de la DGFIP: soit sur cadastre.gouv.fr soit les fichiers Edigeo et Edigeo-cc sur cadastre.data.gouv.fr
- Celle d'Etalab, données Edigeo et DXF + données de Strasbourg (hors PCI). Produit Etalab Cadastre dérivé des données de la DGFIP mais quelles erreurs lors de la transformation des données (liés à notre pile technique). MAJ tous les 3 mois.
- Celle de l'IGN via le produit PCI Express (pas d'idée du suivi/alignement avec les données Edigéo mises à disposition sur cadastre.data.gouv.fr)

## Modalités de téléchargement du cadastre

Les URLs

## Recherche de parcelles

Services disponibles

- https://apicarto.ign.fr/api/doc/cadastre#/Parcelle/get_cadastre_parcelle qui est une surcouche au WFS de l'IGN https://github.com/IGNF/apicarto/blob/master/middlewares/gpuWfsClient.js#L14 qui utilise les données cadastre de PCI Express

Limites: décalage entre les parcelles PCI Express et cadastre: nous ne savons pas comment et quand sont faites les MAJ par rapport à la mise à disposition Edigeo et Cadastre Etalab

## Parser les données Edigeo

- Parser en Javascript utilisé pour produire les données Etalab cadastre https://github.com/etalab/edigeo-parser
- GDAL https://gdal.org/drivers/vector/edigeo.html
- https://github.com/DoFabien/edigeoToGeojson
- Parser en Dotnet utilisé par le GIRTEC pour son intégration en base de données https://github.com/ChristopheVergon/Integrateur_edigeo

## Intégration métier parcelles et MAJIC

### Open Source

- Plugin cadastre QGIS https://github.com/3liz/QgisCadastrePlugin

Récupérer les données du cadastre via ce plugin depuis des codes INSEE https://github.com/3liz/QgisCadastrePlugin/blob/master/docs/extension-qgis/donnees.md

```
processing.run("cadastre:telechargeur_edigeo_communal", {'LISTE_CODE_INSEE':'44109,44143,44162,44026,44190,44215','FILTRE':'','DOSSIER':'/tmp/cadastre-out','DATE':'latest','URL_TEMPLATE':'https://cadastre.data.gouv.fr/data/dgfip-pci-vecteur/{date}/edigeo/feuilles/{departement}/{commune}/'})
```

### Propriétaires

- ESRI (produits ArcGIS) https://www.arcopole.fr/content/cadastre
- FME MAJIC https://www.veremes.com/produits/majic

[https://www.impots.gouv.fr/particulier/questions/comment-puis-je-acceder-la-documentation-cadastrale

## Accès aux fonds de plan du cadastre

- WMS accès cadastre https://www.cadastre.gouv.fr/scpc/pdf/Guide_WMS_fr.pdf
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

