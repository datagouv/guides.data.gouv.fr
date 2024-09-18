# Croiser des données

Dans le cadre de vos travaux, il peut s’avérer intéressant de croiser plusieurs jeux de données entre eux, et ainsi créer des jeux de données enrichis.

**Le croisement de données consiste à joindre des jeux de données distincts en utilisant un attribut commun.**

## Liste de variables pivots communes

Voici une liste non exhaustive de variables pivots qu’il est possible d’utiliser pour croiser des données.

| Variable pivot             | Description                                                                                                                          | Jeu de données référentiel associé                                                                                                                                                                                     |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SIREN, SIRET               | Identifiant des entreprises françaises et de leurs établissements                                                                    | [Base SIRENE des entreprises et de leurs établissements](https://www.data.gouv.fr/fr/datasets/base-sirene-des-entreprises-et-de-leurs-etablissements-siren-siret/)                                                     |
| BAN                        | Adresses du territoire français                                                                                                      | [Base Adresse Nationale](https://www.data.gouv.fr/fr/datasets/base-adresse-nationale/)                                                                                                                                 |
| Code Officiel Géographique | Codes et libellés des communes, des cantons, des arrondissements, des départements, des régions et des pays et territoires étrangers | [Code Officiel Géographique](https://www.data.gouv.fr/fr/datasets/code-officiel-geographique-cog/)                                                                                                                     |
| Plan Cadastral Informatisé | Identifiant des parcelles cadastrales                                                                                                | [Plan Cadastral Informatisé](https://www.data.gouv.fr/fr/datasets/plan-cadastral-informatise/)                                                                                                                         |
| N°RNA                      | Identifiant des associations françaises                                                                                              | [Répertoire National des Associations](https://www.data.gouv.fr/fr/datasets/repertoire-national-des-associations/)                                                                                                     |
| Code ROME                  | Identifiant des métiers et des emplois                                                                                               | [Répertoire Opérationnel des Métiers et des Emplois](https://www.data.gouv.fr/fr/datasets/repertoire-operationnel-des-metiers-et-des-emplois-rome/)                                                                    |
| Code NAF                   | Nomenclature des activités économiques productives                                                                                   | [Nomenclature d'activités française (NAF)](https://www.data.gouv.fr/fr/datasets/nomenclature-dactivites-francaise-naf/)                                                                                                |
| N°RNCP/N°RS                | Identifiant des certifications professionnelles                                                                                      | [Répertoire National des Certifications Professionnelles (RNCP) et Répertoire Spécifique (RS)](https://www.data.gouv.fr/fr/datasets/repertoire-national-des-certifications-professionnelles-et-repertoire-specifique/) |
| N°Fantoir                  | Identifiant des lieux-dits et des voies pour chaque commune                                                                          | [Fichier FANTOIR des voies et lieux-dits](https://www.data.gouv.fr/fr/datasets/fichier-fantoir-des-voies-et-lieux-dits/)                                                                                               |

{% hint style="info" %}
Pour en savoir plus, nous vous invitons à consulter la section “[Lier des données à un référentiel](../../../guides-open-data/guide-qualite/preparer-un-jeu-de-donnees-de-qualite/lier-des-donnees-a-un-referentiel.md)” du guide qualité.
{% endhint %}

## Exemple : Croiser deux jeux de données avec le logiciel de tableur LibreOffice Calc

### Données d’exemple

#### Jeu de données 1 : Données de produits

| Référence produit | Nom du produit | Prix |
| ----------------- | -------------- | ---- |
| 201               | Plante         | 10   |
| 202               | Chaise         | 60   |
| 203               | Enceinte       | 100  |

#### Jeu de données 2 : Données de vente

| Référence produit | Quantité vendue |
| ----------------- | --------------- |
| 201               | 100             |
| 202               | 50              |
| 203               | 30              |

Dans cet exemple, “Référence produit” est la variable pivot qui permettra de croiser les deux jeux de données.

### La fonction RECHERCHEV

{% hint style="info" %}
La fonction RECHERCHEV permet de rechercher une valeur dans une autre table en fonction d’une clé.
{% endhint %}

Syntaxe de RECHERCHEV : =RECHERCHEV(valeur\_cherchée; table; index\_colonne)

où :

* valeur\_cherchée : la valeur à rechercher dans la colonne de la table de référence
* table : la plage de cellules dans laquelle effectuer la recherche
* index\_colonne : le numéro de colonne dans la plage où se trouve la valeur à retourner (par rapport à la première colonne de la table de référence)

### Tutoriel

Les deux jeux de données que vous souhaitez croiser sont sur deux feuilles différentes. Votre variable pivot est le champ “Référence produit”.

1. Allez dans une nouvelle colonne à côté de votre premier tableau ;
2. Vous êtes sur la première ligne de données du jeu de données 1, utilisez la formule suivante pour ajouter la quantité vendue provenant du jeu de données 2 en fonction de la “Référence Produit” : =RECHERCHEV(A2; Feuille2.$A$1;$B$4; 2; FAUX)

où :

* A2 : fait référence à la “Référence Produit” du premier tableau ;
* Feuille2.$A$1:$B$4 : Plage de cellules contenant les données du second tableau (où effectuer la recherche) ;
* 2 : signifie que la deuxième colonne de la plage contient la quantité vendue que vous souhaitez récupérer.

3. LibreOffice Calc remplira la cellule avec la quantité vendue correspondant à la référence produit.
4. Glissez la formule vers le bas pour remplir toutes les lignes.

Vous devriez obtenir le tableau suivant :

| Référence produit | Nom du produit | Prix | Quantité vendue |
| ----------------- | -------------- | ---- | --------------- |
| 201               | Plante         | 10   | 100             |
| 202               | Chaise         | 60   | 50              |
| 203               | Enceinte       | 100  | 30              |
