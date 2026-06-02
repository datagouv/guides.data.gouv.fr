# Bénéficier des conversions automatiques

En publiant des données dans certains formats, vous pouvez bénéficier de conversions automatiques vers d'autres formats. Cette section détaille les modalités de ces réexpositions.

## Données tabulaires

Sur data.gouv.fr, l'appellation "tabulaire" regroupe plusieurs formats de données, qui ont pour point commun de présenter les données sous la forme d'un tableau (X lignes et Y colonnes). Généralement, chaque ligne représente une observation, et chaque colonne une variable observée. Les formats tabulaires qui peuvent bénéficier de conversions automatiques sur data.gouv.fr sont :

* le format **csv** : le format tabulaire le plus commun, dans lequel chaque ligne est représentée par un un retour à la ligne, et les colonnes sont séparées par un caractère défini (généralement la virgule ou le point-virgule, parfois le pipe \`|\`). Ce format est idéal car très interopérable et lisible par presque n'importe quel logiciel, d'un outil de traitement de texte à un tableur.\
  NB : pour des volumes de données conséqents (à partir d'environ 1Go) il peut être pertinent de _gunzipper_ le fichier, qui devient alors un **csv.gz**, souvent beaucoup plus léger. Il garde toutes ses caractéristiques fondamentales, mais sa lecture nécessite une phase de dézippage.
* le format **xlsx** (ou **xls** dans ses anciennes versions) : le format d'export par défaut d'Excel, souvent moins volumineux que le csv (à quantité de données égale), mais qui nécessite un logiciel spécifique pour être ouvert (Excel, LibreOffice, un langage de programmation...). C'est un format propriétaire, donc par essence moins interopérable que le csv.
* le format [**parquet**](https://fr.wikipedia.org/wiki/Apache_Parquet) : un format beaucoup plus récent, particulièrement adapté au stockage de gros volumes de données. Il a l'avantage de stocker les colonnes avec un type associé (nombre, date, chaîne de caractères...) et est souvent beaucoup plus compact pour le même volume de données que des équivalents csv ou xlsx. C'est un format plus technique, qui nécessite d'être manipulé avec un langage de programmation, mais qui offre la possibilité d'être ouvert "par morceaux" : on peut par exemple lui demander "toutes les lignes pour lesquelles la colonne \`date\_mutation\` est inférieure au 28/01/2025", et les données seront renvoyées de façon optimisées, sans avoir à lire l'entièreté du fichier.

Les fichiers csv et xls(x) sont traités de la même façon par data.gouv.fr et, sous réserve de bonne structure (pas de lignes parasites, même nombre de colonnes pour chaque ligne...), ces fichiers sont convertis automatiquement :

* en parquet (s'ils comportent assez de lignes, le format parquet étant réellement intéressant pour des gros volumes) ; les types de colonnes sont détectés par [notre brique d'analyse](https://github.com/datagouv/csv-detective).
* en une table en base de données, qui est ensuite exposée par API (voir la documentation de [l'API tabulaire](https://www.data.gouv.fr/dataservices/673b0e6774a23d9eac2af8ce)) ; cette conversion est utilisée pour afficher la prévisualisation des données dans l'onglet "Aperçu" d'une ressource.
* si notre brique d'analyse détecte des coordonnées géographiques (deux colonnes `latitude` et `longitude`, ou une seule colonne `latitude+longitude`), en GeoJSON, puis en PMTiles (voir les détails de ces formats ci-dessous).

Les fichiers parquet sont uniquement convertis en une table en base de données pour exposition par l'API tabulaire.

Cela permet aux producteurs de données de se focaliser sur la production d'un unique fichier de qualité, sans avoir à implémenter des conversions ou une API "maison".

## Données géographiques

Il existe de nombreux formats pour exposer de la donnée géographique. L'équipe de data.gouv.fr a fait le choix de s'interfacer prioritairement avec [le format GeoJSON](https://fr.wikipedia.org/wiki/GeoJSON), qui est un formalisme particulier du format libre et interopérable JSON. Concrètement, un fichier GeoJSON expose des observations géolocalisées sous la forme d'une liste avec d'un côté les éléments géographiques (coordonnées, polygones...) de l'observation et de l'autre le reste de ses caractéristiques (nom, relevé d'un mesure…).

Lorsqu'un fichier GeoJSON est publié, il est convertit automatiquement au format [PMTiles](https://github.com/protomaps/PMTiles), qui est utilisé pour afficher une visualisation cartographique dans l'onglet "Carte" d'une ressource (également présent si un fichier tabulaire a été converti en GeoJSON puis en PMTiles).

## Précautions particulières

Ces conversions sont automatiques dans la limite d'une taille maximale du fichier :&#x20;

* csv et csv.gz : 100Mo
* xls : 50Mo
* xlsx : 12.5Mo
* parquet : 50Mo
* GeoJSON : 100Mo

> NB : si vous publiez une ressource qui dépasse la limite du format associé, vous pouvez nous faire une demande de passage en exception via [notre support](https://www.data.gouv.fr/support/help/api/apitabulaire/#support-tree) pour qu'elle bénéficie des conversions automatiques.

Lorsqu'une ressource a été convertie, il est possible de télécharger les versions alternatives dans son onglet "Téléchargement".
