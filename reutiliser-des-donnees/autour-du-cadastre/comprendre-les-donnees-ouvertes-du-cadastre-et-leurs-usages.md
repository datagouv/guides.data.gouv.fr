# Comprendre les données ouvertes du cadastre et leurs usages

## Qu'est-ce que le cadastre ?

Le cadastre est un document administratif qui recense et identifie les propriétés foncières (immeuble, maison, terrain, etc.) de chaque commune afin de permettre le calcul des impôts locaux (Ministère de l'économie, des finances et de la souveraineté industrielle et numérique).

## Quelles données en open data ?

Les données ouvertes sont celles du **plan cadastral** : parcelles, sections, bâti et éléments d'habillage.

Elles sont produites et publiées par la **Direction générale des finances publiques** (DGFiP) et font partie [des données de référence du service public de la donnée](https://www.data.gouv.fr/fr/pages/spd/reference/).

Le plan cadastral est une représentation graphique d'une commune qui dresse l'inventaire de ses propriétés foncières ainsi que l'emprise au sol des bâtiments qui les occupent. Il peut aussi indiquer certains détails facilitant sa compréhension tels que les voies de communication principale, cours d'eau, fossés, etc. (Ministère de l'économie, des finances et de la souveraineté industrielle et numérique). Le plan cadastral est découpé en plusieurs *sections cadastrales* (identifiées par une lettre). Chaque section est ensuite composée de *parcelles cadastrales* (identifiées par un numéro).

[Ce document](https://bofip.impots.gouv.fr/bofip/5359-PGP.html/identifiant=BOI-CAD-DIFF-10-20191105) détaille notamment les éléments qui figurent dans le plan cadastral (tel que publié par la DGFiP sur cadastre.gouv.fr).

Il est possible de **consulter** [**la carte du cadastre**](https://cadastre.data.gouv.fr/map?style=ortho).

{% hint style="info" %} 

**Lexique**

Parcelle cadastrale : Portion de terrain appartenant à un même propriétaire. {% endhint %}

![Illustration du plan cadastral](https://user-images.githubusercontent.com/72090652/268529403-e350b687-a132-4b5a-934c-05f132b0e92a.png)

## Quels usages possibles ?

Les données du plan cadastral constituent **des données géographiques de référence**, qui peuvent être utilisées dans tous types de cartographie. Vous pouvez notamment : 
- Construire des zonages basés sur des données parcellaires ;
- Intégrer les références cadastrales dans des applications ou des formulaires en ligne.

### Croiser les données du cadastre avec d'autres données
Le plan cadastral peut notamment être croisé avec des données qui s'inscrivent à une maille parcellaire, comme par exemple (liste non exhaustive) :
- [Les données "Demandes de Valeurs Foncières" (DVF) géolocalisées](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres-geolocalisees/) ;
- [Le produit BAN PLUS](https://geoservices.ign.fr/ban-plus), qui permet de lier l'adresse au bâti. Sur le même sujet, il existe également [la Base de Données Nationale des Bâtiments (BDNB)](https://www.data.gouv.fr/fr/datasets/base-de-donnees-nationale-des-batiments/) ;
- [Le Registre Parcellaire Graphique (RPG)](https://geoservices.ign.fr/rpg), utilisé pour les instructions des aides européennes de la Politique Agricole Commune (PAC). Vous pouvez aussi consulter les données des [Parcelles en Agriculture Biologique (AB) déclarées à la PAC](https://www.data.gouv.fr/fr/datasets/parcelles-en-agriculture-biologique-ab-declarees-a-la-pac/) ;
- Les parcelles protégées du Conservatoire du littoral, disponibles sous forme WFS dans les services proposés par l'IGN ;
- [Les délimitations parcellaires AOC viticoles](https://www.data.gouv.fr/fr/datasets/delimitation-parcellaire-des-aoc-viticoles-de-linao/) ;
- [Le Géoportail de l'urbanisme](https://www.geoportail-urbanisme.gouv.fr/), dont les PLU s'appuient sur les parcelles du cadastre.

### S'inspirer de projets existants
Pour inspiration, le plan cadastral a été utilisé pour développer des solutions permettant de : 
- [Connaître le prix de vente des biens immobiliers](https://www.data.gouv.fr/fr/pages/onboarding/dvf/) ;
- [Réaliser l'état des risques d'un bien immobilier](https://www.data.gouv.fr/fr/pages/onboarding/errial/) ;
- [S'informer sur les règles d'urbanisme d'un territoire](https://www.data.gouv.fr/fr/reuses/iudo-app/).

## Comment accéder aux données ?

Pour consulter et télécharger les données cadastrales, vous pouvez vous rendre (selon votre besoin) sur : 
- [**cadastre.data.gouv.fr**](https://cadastre.data.gouv.fr/)
- [**cadastre.gouv.fr**](https://www.cadastre.gouv.fr/scpc/accueil.do)

<table><thead><tr><th width="156.33333333333331">Caractéristiques</th><th width="454">cadastre.data.gouv.fr</th><th width="454">cadastre.gouv.fr</th></tr></thead><tbody><tr><td>Porteur</td><td>Maintenu par la Direction interministérielle du numérique</td><td>Maintenu par la Direction générale des finances publiques</td></tr><tr><td>Mise à jour</td><td>Mise à jour tous les 3 mois (selon la livraison par la DGFiP)</td><td>Mise à jour en continu</td></tr><tr><td>Recherche</td><td>Recherche par adresse rapide, pas de recherche par numéro de parcelle</td><td>Recherche par adresse et par numéro de parcelle</td></tr><tr><td>Autres</td><td><ul><li>Référencement d'une parcelle par URL possible</li><li>Quelques parcelles ne sont pas bien récupérées lors du passage du format d'échange Edigéo vers les formats GeoJSON et SIG (type shp)</li></ul></td><td><ul><li>Possibilité de générer un PDF</li><li>Possibilité de voir la mitoyenneté quand renseignée</li><li>Demande de rechercher à chaque fois plutôt que de partager le lien</li></ul></td></tr>
