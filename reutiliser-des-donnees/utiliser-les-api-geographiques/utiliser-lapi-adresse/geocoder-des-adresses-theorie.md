# Géocoder des adresses - la théorie

## Qu'est-ce que le géocodage ?

{% hint style="info" %}
**Lexique : Géocodage**\
Le géocodage consiste à affecter des coordonnées géographiques (longitude/latitude) à une adresse postale (Wikipédia).

Il permet ainsi de positionner des adresses sur une carte ou encore de trouver les points de départ et d’arrivée pour déterminer votre trajet lorsque vous voyagez par exemple.
{% endhint %}

### Les indispensables pour réaliser un géocodage

Pour réaliser un géocodage, il est nécessaire de disposer :

* [ ] des **données de référence** contenant numéro, nom de rue, [code INSEE](https://www.data.gouv.fr/en/datasets/code-officiel-geographique-cog/), code postal, nom de commune ;
* [ ] des **coordonnées géographiques** x et y qui sont généralement la longitude(x) et la latitude(y) ;
* [ ] une **entrée correspondant à l’adresse recherchée**.

### Le fonctionnement d'un géocodeur <a href="#comment-fonctionne-un-geocodeur" id="comment-fonctionne-un-geocodeur"></a>

Un géocodeur transforme une donnée textuelle des données de référence en utilisant des algorithmes qui séparent l’adresse en syllabes, mots et groupes de mots.

Les différents éléments sont indexés, puis en s’appuyant sur des algorithmes relatifs à du traitement textuel, le géocodeur compare la similarité entre les mots constituant l’adresse à rechercher et ceux qui sont indexés depuis les données de référence.

Un algorithme permet généralement d’ordonner les résultats. Il s’agit par exemple de faire apparaitre en premier les résultats ayant les coordonnées fixes les plus proches ou encore ceux dont la population est la plus forte.

Il est également possible de filtrer selon des critères comme le pays (si le géocodeur a une vocation internationale, comme [Nominatim](https://nominatim.openstreetmap.org/)) ou encore par type de résultat.

En pratique, un certain nombre de géocodeurs visent à réaliser des recherches de communes et de POIs (Points Of Interest ou points d’intérêts) et pas seulement des adresses.

Le **géocodage peut aussi se faire de façon inverse**, c’est-à-dire retourner une adresse en envoyant une coordonnée. Dans ce cas de figure, il s’agit de trouver la donnée de référence la plus proche des coordonnées envoyées.

### Les limites du géocodage <a href="#les-limites-du-geocodage" id="les-limites-du-geocodage"></a>

Nous nous concentrons ici sur les cas liés aux adresses, le géocodeur utilisé par [adresse.data.gouv.fr](http://adresse.data.gouv.fr/) étant spécifiquement conçu pour répondre à ce besoin.

**La qualité des données de référence**

Les données textuelles de l’adresse de référence ne sont pas toujours uniformes.&#x20;

> Exemple : "rue" peut être représenté par les lettres "r" ou "R" ou "rue" ou "Rue".

Il s’agit donc en premier lieu d’uniformiser les différentes manières de décrire le type de voie.

Il s’agit également d’omettre les articles lors d’une comparaison.&#x20;

> Exemple : chercher "rue métanies" au lieu de "rue des métanies".

D’un autre côté, les coordonnées géographiques peuvent manquer de précision. Dans certains cas, il arrive de disposer uniquement du centroïde de la commune, de la voie ou du lieu dit (point d’une zone géographique choisi au voisinage de son centre de gravité et dont les coordonnées servent de localisant pour cette zone).

Dans d’autres cas, les coordonnées peuvent avoir été interpolées : les adresses ont été positionnées en fonction du nombre de numéros dans une voie et la longueur de celle-ci.

#### Les principales problématiques liées aux adresses

<details>

<summary><strong>Plusieurs communes pour un code postal</strong>.</summary>

Cette problématique se pose par exemple lorsqu’on met le nom de la commune dans une adresse. En effet, 68,9% des codes postaux sont associés à plus d’une commune et jusqu’à 46 communes sont rattachées à un même code postal.

</details>

<details>

<summary><strong>Plusieurs codes postaux pour une commune</strong>.</summary>

1,5% des communes ont plus d’un seul code postal sur leur territoire. On compte même jusqu’à 9 codes postaux pour une même commune pour le cas extrême !

</details>

<details>

<summary><strong>Des communes ont des noms identiques</strong>.</summary>

10,6% des communes ont une ou plusieurs communes homonymes.

</details>

<details>

<summary><strong>Des codes postaux n’ont pas le même code que celui du département</strong>.</summary>

Ces cas de figure sont très rares (quelques dizaines).

</details>

<details>

<summary><strong>Plusieurs noms de voie avec un nom identique sont situés à différents endroits pour une même commune</strong>.</summary>

Cette situation s’explique en particulier avec la création des communes nouvelles qui a encouragé le regroupement de communes. Ce problème peut être réglé en ajoutant le nom de la commune déléguée dans l’adresse postale, en renumérotant les rues ou en les renommant. Or les géocodeurs ne gèrent pas forcément bien (voir pas du tout) l’ajout d’adresse de la commune déléguée.

</details>

<details>

<summary><strong>Plusieurs coordonnées pour une même adresse.</strong></summary>

* Il peut exister des différences liées à la vision sur la position du numéro de l’adresse (entrée principale, boîte aux lettres, bâtiment, cage d’escalier, logement, parcelle, position dérivée du segment de la voie de rattachement, point d’accès technique, etc.) ;

<!---->

* Des référentiels différents selon les acteurs même si la BAN (Base Adresse Nationale) et les BAL (Bases Adresses Locales) amènent à une amélioration et une uniformisation des référentiels : données héritées de la Poste, de l’IGN, du cadastre, des opérateurs réseaux (fibre, etc.).

</details>
