# Focus : Lier des données à un référentiel

{% hint style="info" %}
Il est important d'intégrer dans vos jeux de données des données pivots relevant d'un référentiel (cf. section "Structurer un jeu de données" - Cas 1 - La structure de vos données ne correspond à aucun schéma de données).
{% endhint %}

> **Exemple** : Mon jeu de données est une liste d'actions culturelles menées par ma région. Certaines de ces actions sont gérées par des associations. Il peut être intéressant de publier un jeu de données recensant ces actions avec un champ correspondant à l'identification des associations. Cet identifiant existe et est standardisé, il s'agit du numéro RNA, identifiant national des associations dont le répertoire est opéré par le ministère de l'intérieur.

## Pourquoi intégrer des données pivots dans un jeu de données ? <a href="#avantages" id="avantages"></a>

L'intégration dans un jeu de données de données pivots qui correspondent à un référentiel présente plusieurs avantages :

* **Une meilleure formalisation** : en se basant sur un référentiel, le producteur de données a l'assurance d'utiliser un format de données standard et partagé par un grand nombre de jeux de données ;
* **Une meilleure synthèse** : en se basant sur un référentiel, le producteur évite l’abondance de détails et va à l’essentiel. L’obtention d’informations complémentaires se fera par le biais de la consultation du référentiel lui-même ;
* **Une meilleure compréhension** : en intégrant dans son jeu de données des données correspondant à un référentiel, le producteur facilite la compréhension de celui-ci par les utilisateurs car il se réfère à un standard largement adopté ;
* **Une meilleure réutilisation** : intégrer des données liées à un référentiel facilitera la réutilisation du jeu de données et permettra son enrichissement avec d'autres données partageant la même donnée pivot ;
* **Une meilleure interopérabilité** : intégrer des données pivots facilite le lien avec des données de référence fiables et à jour.

## Quels référentiels utiliser pour intégrer des données pivots ? <a href="#exemples-de-referentiels" id="exemples-de-referentiels"></a>

Voici une liste non exhaustive de référentiels sur lesquels il est possible de s'appuyer pour l'intégration de variables pivots :

### Le service public de la donnée <a href="#le-service-public-de-la-donnee" id="le-service-public-de-la-donnee"></a>

Le [service public de la donnée (SPD)](https://www.data.gouv.fr/fr/pages/spd/reference/) vise à mettre à disposition avec un haut niveau de qualité les jeux de données de référence qui présentent un fort impact économique et social.&#x20;

À ce jour, 9 jeux de données ont été identifiés comme des données de référence :&#x20;

| Nom du jeu de données                                                                                                                                                                             | Variable(s) pivot(s) | Description                                                                                                                                                                       | Producteur                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [Base SIRENE](https://www.data.gouv.fr/fr/datasets/base-sirene-des-entreprises-et-de-leurs-etablissements-siren-siret/)                                                                           | SIRET, SIREN         | Liste des établissements (SIRET) et unités légales (SIREN) françaises                                                                                                             | [INSEE](https://www.data.gouv.fr/fr/organizations/institut-national-de-la-statistique-et-des-etudes-economiques-insee/)      |
| [Base Adresse Nationale (BAN)](https://www.data.gouv.fr/fr/datasets/base-adresse-nationale/)                                                                                                      | BAN                  | Référencement de l'intégralité des adresses du territoire français                                                                                                                | [BAN](https://www.data.gouv.fr/fr/organizations/base-adresse-nationale/)                                                     |
| [Code Officiel Géographique (COG)](https://www.data.gouv.fr/fr/datasets/code-officiel-geographique-cog/)                                                                                          | Codes et libellés    | Liste des communes, cantons, arrondissements, départements, régions, pays et territoires étrangers                                                                                | [INSEE](https://www.data.gouv.fr/fr/organizations/institut-national-de-la-statistique-et-des-etudes-economiques-insee/)      |
| [Plan Cadastral Informatisé (PCI)](https://www.data.gouv.fr/fr/datasets/plan-cadastral-informatise/)                                                                                              | Identifiant          | Représentation de chacune des sections du cadastre français                                                                                                                       | [Ministère de l'Économie et des Finances](https://www.data.gouv.fr/fr/organizations/ministere-de-leconomie-et-des-finances/) |
| [Registre parcellaire graphique (RPG)](https://www.data.gouv.fr/fr/datasets/registre-parcellaire-graphique-rpg-contours-des-parcelles-et-ilots-culturaux-et-leur-groupe-de-cultures-majoritaire/) | Identifiant          | Base de données géographique de référence pour l'instruction des aides de la politique agricole commune (PAC)                                                                     | [IGN](https://www.data.gouv.fr/fr/organizations/institut-national-de-l-information-geographique-et-forestiere/)              |
| [Référentiel de l'organisation administrative de l'Etat](https://www.data.gouv.fr/fr/datasets/referentiel-de-lorganisation-administrative-de-letat/)                                              | Identifiant          | Liste des institutions régies par la Constitution de la Ve république ainsi que les administrations qui en dépendent                                                              | [DILA](https://www.data.gouv.fr/fr/organizations/premier-ministre/)                                                          |
| [Référentiel à grande échelle (RGE)](https://www.data.gouv.fr/fr/datasets/referentiel-a-grande-echelle-rge/)                                                                                      | Identifiant          | Composantes orthophotographique, topographique et adresse, parcellaire et altimétrique des territoires de l'Etat français                                                         | [IGN](https://www.data.gouv.fr/fr/organizations/institut-national-de-l-information-geographique-et-forestiere/)              |
| [Répertoire National des Associations (RNA)](https://www.data.gouv.fr/fr/datasets/repertoire-national-des-associations/)                                                                          | N° RNA / N° Waldec   | Ensemble des associations relevant de la loi du 1er juillet 1901 relative au contrat d’association, dont le siège est en France                                                   | [Ministère de l'Intérieur](https://www.data.gouv.fr/fr/organizations/ministere-de-l-interieur/)                              |
| [Répertoire Opérationnel des Métiers et des Emplois (ROME)](https://www.data.gouv.fr/fr/datasets/repertoire-operationnel-des-metiers-et-des-emplois-rome/)                                        | Code ROME            | Inventaire des dénominations d’emplois/métiers les plus courantes, analyse des activités et compétences, regroupement des emplois selon un principe d’équivalence ou de proximité | [Pôle Emploi](https://www.data.gouv.fr/fr/organizations/pole-emploi/)                                                        |

> **Exemple :** Afin de lister l'ensemble des actions culturelles de ma région, nous avons vu que le numéro RNA pouvait être utile pour identifier les associations. Grâce à celui-ci, il est également possible de récupérer le numéro SIRET de l'association si celle-ci en possède un. Il est également possible de détailler dans le jeu de données le code commune et le code département de chaque action. Pour cela, il convient de se référer au Code officiel géographique. Attention à bien respecter celui-ci. Par exemple, le code département de l'Ariège est le "09" et pas le "9". Ce type d'erreur pourrait entraîner des difficultés lors de la réutilisation des données.

### Autres référentiels <a href="#les-autres-referentiels" id="les-autres-referentiels"></a>

Des jeux de données standardisées et communément partagées avec le plus grand nombre peuvent aussi être utilisés comme référentiels.

> **Exemple** : L'identifiant unique d'une certification professionnelle est le [numéro RNCP](https://www.data.gouv.fr/fr/datasets/repertoire-national-des-certifications-professionnelles-et-repertoire-specifique/). Ce jeu de données ne fait pas partie du service public de la donnée mais est largement partagé par les acteurs du domaine de la formation professionnelle.

#### Référentiels métiers

| Nom du jeu de données                                                                                                                                                                                                                                                                                           | Variable(s) pivot(s)    | Description                                                                                                                                      | Producteur                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Nomenclature d’activités française (NAF)](https://www.data.gouv.fr/fr/datasets/nomenclature-dactivites-francaise-naf/)                                                                                                                                                                                         | Code NAF                | Nomenclature des activités économiques productives, principalement élaborée pour faciliter l'organisation de l'information économique et sociale | [INSEE](https://www.data.gouv.fr/fr/organizations/institut-national-de-la-statistique-et-des-etudes-economiques-insee/)                                            |
| [Répertoire National des Certifications Professionnelles (RNCP) et Répertoire Spécifique (RS)](https://www.data.gouv.fr/fr/datasets/repertoire-national-des-certifications-professionnelles-et-repertoire-specifique/)                                                                                          | N°RNCP / N°RS           | Répertoire des certifications officielles inscrites au RNCP et au RS                                                                             | [France Compétences](https://www.data.gouv.fr/fr/organizations/france-competences/)                                                                                |
| [Fichier FANTOIR des voies et lieux-dits](https://www.data.gouv.fr/fr/datasets/fichier-fantoir-des-voies-et-lieux-dits/)                                                                                                                                                                                        | N° FANTOIR              | Nom des lieux-dits et des voies pour chaque commune, y compris celles situées dans les lotissements et les copropriétés                          | [Ministère de l'Économie et des Finances](https://www.data.gouv.fr/fr/organizations/ministere-de-leconomie-et-des-finances/)                                       |
| [Etats et capitales du monde](https://www.data.gouv.fr/fr/datasets/etats-et-capitales-du-monde/#\_)                                                                                                                                                                                                             | Code Pays               | Liste des états indépendants reconnus par la France                                                                                              | [Ministère de l'Europe et des Affaires Etrangères](https://www.data.gouv.fr/fr/organizations/ministere-des-affaires-etrangeres-et-du-developpement-international/) |
| [Nomenclatures des professions et catégories socioprofessionnelles](https://www.insee.fr/fr/information/2406153)                                                                                                                                                                                                | Code PCS / Code PCS-ESE | Nomenclatures des professions et catégories socioprofessionnelles                                                                                | [INSEE](https://www.data.gouv.fr/fr/organizations/institut-national-de-la-statistique-et-des-etudes-economiques-insee/)                                            |
| <p><a href="https://www.data.gouv.fr/fr/datasets/etablissements-denseignement-superieur-2/">Liste des établissements d'enseignements supérieurs</a><br><br><a href="https://www.data.gouv.fr/fr/datasets/etablissements-denseignement-secondaire/">Liste des établissements d'enseignements secondaires</a></p> | N°UAI                   | Liste des unités administratives immatriculées                                                                                                   | [ONISEP](https://www.data.gouv.fr/fr/organizations/office-national-d-information-sur-les-enseignements-et-les-professions/)                                        |

**Référentiels techniques**

Les référentiels techniques n'ont pas de significations métiers mais ils permettent de décrire une donnée de manière standardisée. Ces standards permettent aux utilisateurs et aux algorithmes de pouvoir interpréter automatiquement la donnée de manière correcte.&#x20;

Voici deux exemples de référentiels techniques :&#x20;

| Nom du référentiel | Description                                        | Information                                          |
| ------------------ | -------------------------------------------------- | ---------------------------------------------------- |
| WGS84              | Coordonnées géodésiques d'un lieu                  | [Wikipedia](https://fr.wikipedia.org/wiki/WGS\_84)   |
| ISO8601            | Représentation numérique d'une date et d'une heure | [Wikipedia](https://fr.wikipedia.org/wiki/ISO\_8601) |

### Partager ses propres référentiels <a href="#partager-ses-propres-referentiels" id="partager-ses-propres-referentiels"></a>

{% hint style="info" %}
**Cadre Commun d'Architecture des référentiels de données de l'État**

Le [Cadre Commun d'Architecture des référentiels de données de l'État](https://references.modernisation.gouv.fr/sites/default/files/Cadre%20Commun%20d'Architecture%20des%20R%C3%A9f%C3%A9rentiel%20de%20donn%C3%A9es%20v1.0\_0.pdf) fait spécifiquement mention de l'importance des variables pivots dans le partage et la publication de données. Il stipule notamment que :

* Les données sont un bien, un actif de l’État, elles doivent être gérées et valorisées en conséquence ;
* Les données doivent être standardisées, définies sur la base d’un vocabulaire commun, contextualisées, et combinables les unes aux autres ;
* Les données doivent être facilement réutilisables, partageables et accessibles à travers les frontières des administrations ;
* Les données publiques doivent être mises à disposition librement et ouvertement sur internet ;
* La sécurité et l'archivage des données doit être assuré.
{% endhint %}

Les acteurs sont encouragés à mettre en place leurs propres référentiels internes ou à les partager s'ils existent déjà pour favoriser au mieux le partage et l'interopérabilité des données.

Il est pertinent de diffuser, en même temps qu'un jeu de données, la liste des valeurs possibles correspondant à votre propre référentiel métier. Celui-ci sera connu et potentiellement réutilisé par d'autres acteurs.

La mise en place de référentiels fait partie d'une stratégie de montée en qualité de la donnée. Néanmoins ce n'est souvent pas suffisant : il est ensuite nécessaire de diffuser, former et vérifier que les données produites intègrent ces référentiels et n'en dérivent pas (à partir d'un contrôle humain ou de tests automatiques).

> **Exemple** : J'utilise en interne un numéro unique permettant d'identifier chaque type d'action culturelle (arts du spectacle, cirque, arts plastiques...). Il peut être pertinent de diffuser en parallèle à la diffusion de mon jeu de données la liste de mon référentiel. Des communes de ma région pourraient potentiellement le réutiliser pour décrire leurs actions culturelles à une maille plus fine.

## Comment intégrer des adresses dans un jeu de données ? <a href="#le-cas-specifique-des-adresses" id="le-cas-specifique-des-adresses"></a>

Il existe des référentiels pour décrire une adresse de manière unique.&#x20;

Le référentiel officiel d'adresse est **la** [**base d'adresse nationale (ou BAN précédemment listé)**](https://www.data.gouv.fr/fr/datasets/base-adresse-nationale/).&#x20;

* Si vous partez de zéro pour constituer un jeu de données, il est pertinent de partir de la base adresse national pour décrire vos adresses.
* Si vous travaillez sur un jeu de données qui contient déjà des adresses saisies, il peut s'avérer fastidieux de corriger manuellement l'ensemble des adresses erronées et vous pouvez obtenir une base d'adresse normalisée grâce à la méthode décrite ci-dessous.

### Le géocodage <a href="#le-geocodage" id="le-geocodage"></a>

{% hint style="info" %}
**Lexique : Géocodage**

Le géocodage consiste à affecter des coordonnées géographiques à une adresse postale.&#x20;
{% endhint %}

Le géocodage peut être en partie automatisé grâce à des outils proposés par Etalab.

**Le site** [**https://adresse.data.gouv.fr/**](https://adresse.data.gouv.fr/) permet de géocoder une liste d'adresse via un appel à une API ou par le dépôt de fichier csv.

Il permet aussi, à partir d'un jeu de données contenant des adresses déjà saisies, de retourner un jeu de données enrichi :

* de coordonnées géographiques (longitude/latitude) ;
* des adresses « corrigées » récupérées de la BAN.

Le site [adresse.data.gouv.fr](https://adresse.data.gouv.fr/) est limité à des utilisations ponctuelles et des volumétries de données considérées faibles (moins d'un million de lignes).&#x20;

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-28 à 16.24.45.png" alt=""><figcaption><p>Page d'accueil d'adresse.data.gouv.fr</p></figcaption></figure>

Pour géocoder davantage de données (plusieurs millions de lignes), il est recommandé d'installer votre propre environnement de géocodage, en utilisant par exemple le géocodeur [Addok](https://addok.readthedocs.io/fr/latest/). Des ressources sont disponibles sur [GitHub](https://github.com/etalab/addok-docker) pour vous aider dans l'installation de votre environnement.

Quelle que soit la méthode utilisée, le processus de géocodage retournera une liste d'adresses standardisées avec leurs coordonnées géographiques associées. Il donne aussi accès à une information `geo_score` correspondant au score de confiance que le géocodeur accorde à l'adresse retournée. Cet indicateur peut être utile à garder dans un jeu de données final, il donnera une indication aux utilisateurs sur la performance du géocodage de chaque adresse.
