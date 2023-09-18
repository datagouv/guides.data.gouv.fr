# Comprendre les données ouvertes du cadastre

## Définition

Le cadastre est un document administratif qui recense et identifie les propriétés foncières (immeuble, maison, terrain, etc.) de chaque commune afin de permettre le calcul des impôts locaux (Ministère de l'économie, des finances et de la souveraineté industrielle et numérique).

## Les données en open data

Les données ouvertes sont celles du **plan cadastral** : parcelles, sections, bâti et éléments d'habillage.

Elles sont produites et publiées par la **Direction générale des finances publiques** et font partie [des données de référence du service public de la donnée](https://www.data.gouv.fr/fr/pages/spd/reference/).

Le plan cadastral est une représentation graphique d'une commune qui dresse l'inventaire de ses propriétés foncières ainsi que l'emprise au sol des bâtiments qui les occupent. Il peut aussi indiquer certains détails facilitant sa compréhension tels que les voies de communication principale, cours d'eau, fossés, etc. (Ministère de l'économie, des finances et de la souveraineté industrielle et numérique)

Le plan cadastral est découpé en plusieurs *sections cadastrales* (identifiées par une lettre). Chaque section est ensuite composée de *parcelles cadastrales* (identifiées par un numéro).

{% hint style="info" %} **Lexique**

Parcelle cadastrale : Portion de terrain appartenant à un même propriétaire. {% endhint %}

![Capture d'écran plan cadastral](https://user-images.githubusercontent.com/72090652/268529403-e350b687-a132-4b5a-934c-05f132b0e92a.png)

## Les usages possibles

Les données du plan cadastral constituent **des données géographiques de référence**, qui peuvent être utilisées dans tous types de cartographie. Vous pouvez notamment : 
- Construire des zonages basés sur des données parcellaires ;
- Intégrer les références cadastrales dans des applications ou des formulaires en ligne.

Pour inspiration, ces données ont par exemple été utilisées pour développer des solutions permettant de : 
- [Connaître le prix de vente des biens immobiliers](https://www.data.gouv.fr/fr/pages/onboarding/dvf/) ;
- [Réaliser l'état des risques d'un bien immobilier](https://www.data.gouv.fr/fr/pages/onboarding/errial/).

## Comment accéder aux données

Pour consulter et télécharger les données cadastrales, vous pouvez vous rendre sur (selon votre besoin) : 
- [**cadastre.data.gouv.fr**](https://cadastre.data.gouv.fr/)
- [**cadastre.gouv.fr**](https://www.cadastre.gouv.fr/scpc/accueil.do)

<table><thead><tr><th width="156.33333333333331">Caractéristiques</th><th width="454">cadastre.data.gouv.fr</th><th width="454">cadastre.gouv.fr</th></tr></thead><tbody><tr><td>Porteur</td><td>Maintenu par data.gouv.fr</td><td>Maintenu par la Direction générale des finances publiques</td></tr><tr><td>Mise à jour</td><td>Mise à jour tous les 3 mois (selon la livraison par la DGFiP)</td><td>Mise à jour en continu</td></tr><tr><td>Recherche</td><td>Recherche par adresse rapide, pas de recherche par numéro de parcelle</td><td>Recherche par adresse et par numéro de parcelle</td></tr><tr><td>Autres</td><td>- Référencement d'une parcelle par URL possible - Quelques parcelles ne sont pas bien récupérées lors du passage du format d'échange Edigéo vers les formats GeoJSON et SIG (type shp)</td><td>- Possibilité de générer un PDF - Possibilité de voir la mitoyenneté quand renseignée - Demande de rechercher à chaque fois plutôt que de partager le lien</td></tr>
