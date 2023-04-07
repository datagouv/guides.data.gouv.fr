# Gestion d'un jeu de données par l'API

Cette page documente les principales interactions que vous pouvez avoir avec un jeu de données par l’API.

Il est recommandé d’avoir lu [l’introduction](https://doc.data.gouv.fr/api/intro/) avant de consulter cette page.

Tous les exemples qui suivent sont réalisés avec un compte :

* qui est actif
* dont la clé d’API est `my-api-key`
* qui est membre d’une organization dont l’identifiant est `5bbb6d6cff66bd4dc17bfd5a`.

Les exemples portants sur un jeu de données existant utilisent l’identifiant `5bc04b2cff66bd680e499f4a`. Ceux portants sur une ressource existante de ce jeu de données utilisent l’identifiant `54d47250-1daf-483b-965a-3013f8c76617`.

Pour simplifier la lecture de ces exemples, il y sera fait référence par les variables suivantes pour chaque language:

CURL

```bash
# Tous les examples CURL sont executés avec cette convention
# CURL doit être installé
export API = 'https://www.data.gouv.fr/api/1'
export API_KEY = 'my-api-key'
export ORG = '5bbb6d6cff66bd4dc17bfd5a'
export DATASET = '5bc04b2cff66bd680e499f4a'
export RESOURCE = '54d47250-1daf-483b-965a-3013f8c76617'
```

HTTPiePython

### Création d’un jeu de données <a href="#creation-dun-jeu-de-donnees" id="creation-dun-jeu-de-donnees"></a>

Pour créer un jeu de données, nous allons utiliser l’API de [création de jeu de données](https://doc.data.gouv.fr/api/reference/#/datasets/create\_dataset).

CURL

```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "my title", "description": "My description", "organization": "$ORG"}' \
     -X POST $API/datasets/
```

HTTPiePython

La réponse en JSON contient les metadonnées du jeu de données créé, en particulier l’identifiant et le slug.

La fiche du jeu de données est maintenant créée et il est maintenant possible d’y ajouter des ressources.

**Attention** : par défaut, un jeu de données créé via l’API est public. Afin de créer et maintenir un jeu de données en privé, il faut mettre l’attribut `private: true` dans chaque appel à l’API. Sinon, chaque modification d’un jeu de données par l’API va le passer en public.

#### Ajout d’une ressource <a href="#ajout-dune-ressource" id="ajout-dune-ressource"></a>

Pour créer une ressource, nous allons utiliser l’API [création d’une ressource](https://doc.data.gouv.fr/api/reference/#/datasets/create\_resource).

Il existe 2 cas de création de ressource :

* avec envoi d’un fichier, dit ressource locale ;
* avec référencement d’un fichier distant, dit ressource distante.

**En envoyant un fichier**

Nous allons utiliser l’API d’[envoi de ressource](https://doc.data.gouv.fr/api/reference/#/datasets/upload\_new\_dataset\_resource) pour envoyer le fichier.

CURL

```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -F "file=@/chemin/vers/le/fichier" \
     -X POST $API/datasets/$DATASET/upload/
```

HTTPiePython

La ressource est automatiquement créée et il est possible de modifier _a posteriori_ les metadonnées avec l’[API de mise à jour de ressource](https://doc.data.gouv.fr/api/reference/#/datasets/update\_resource) comme décrit [plus bas](https://doc.data.gouv.fr/api/dataset-workflow/#mise-%C3%A0-jour-des-m%C3%A9tadonn%C3%A9es-dune-ressource)

**En référençant une URL existante**

L’API de [création de ressource](https://doc.data.gouv.fr/api/reference/#/datasets/create\_resource) permet de créer une ressource distante. Dans notre cas, un fichier csv hébergé sur l’URL [https://url.to/ressource.csv](https://url.to/ressource.csv).

CURL

```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "my title", "description": "My description", "type": "main", filetype: "remote", "format": "csv",  "url": "https://url.to/ressource.csv"}' \
     -X POST $API/datasets/$DATASET/resources/
```

HTTPiePython

### Modification d’un jeu de données <a href="#modification-dun-jeu-de-donnees" id="modification-dun-jeu-de-donnees"></a>

La suite des opérations s’appliquent sur le même jeu de données dont l’identifiant est `5bc04b2cff66bd680e499f4a` sur lequel vous avez les permissions nécéssaires à la modification. Ce jeu de données possède une ressource `54d47250-1daf-483b-965a-3013f8c76617` qui est soit distante soit locale suivant les exemples.

#### Mise à jour des metadonnées de la fiche <a href="#mise-a-jour-des-metadonnees-de-la-fiche" id="mise-a-jour-des-metadonnees-de-la-fiche"></a>

Cette requête permet de mettre à jour les métadonnées d’un jeu de données en utilisant [l’API de mise à jour de jeu de données](https://doc.data.gouv.fr/api/reference/#/datasets/update\_dataset)

CURL

```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "Nouveau titre", "description": "Nouvelle description"}' \
     -X PUT $API/datasets/$DATASET/
```

HTTPiePython

#### Mise à jour des métadonnées d’une ressource <a href="#mise-a-jour-des-metadonnees-dune-ressource" id="mise-a-jour-des-metadonnees-dune-ressource"></a>

Cette requête permet de mettre à jour les métadonnées d’une ressource en utilisant [l’API de mise à jour de ressource](https://doc.data.gouv.fr/api/reference/#/datasets/update\_resource)

CURL

```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "Nouveau titre", "description": "Nouvelle description"}' \
     -X PUT $API/datasets/$DATASET/resources/$RESOURCE/
```

HTTPiePython

#### Remplacer un fichier de ressource <a href="#remplacer-un-fichier-de-ressource" id="remplacer-un-fichier-de-ressource"></a>

Dans le cas d’une mise à jour de fichier de ressource locale (correction, ajout de données…),il est possible d’utiliser [l’API de mise à jour de fichier](https://doc.data.gouv.fr/api/reference/#/datasets/upload\_dataset\_resource). L’ancien fichier sera supprimé.

CURL

```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -F "file=@/chemin/vers/le/nouveau/fichier" \
     -X POST $API/datasets/$DATASET/resources/$RESOURCE/upload/
```

HTTPiePython

#### Signaler une mise à jour de fichier distant <a href="#signaler-une-mise-a-jour-de-fichier-distant" id="signaler-une-mise-a-jour-de-fichier-distant"></a>

Dans le cas d’une ressource distante, lorsque le fichier distant est mis à jour, il est important de le signaler afin que la fiche soit mise à jour et que les usagers le sache.

**🚧 Bientôt 🚧**

#### Suppression d’une ressource <a href="#suppression-dune-ressource" id="suppression-dune-ressource"></a>

[l’API de suppression de ressource](https://doc.data.gouv.fr/api/reference/#/datasets/delete\_resource) permet de supprimer une ressource de la fiche d’un jeu de données. Le fichier associé est aussi supprimé.

CURL

```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -X DELETE $API/datasets/$DATASET/resources/$RESOURCE
```

HTTPiePython

### Suppression d’un jeu de données <a href="#suppression-dun-jeu-de-donnees" id="suppression-dun-jeu-de-donnees"></a>

Pour supprimer un jeu de données, il suffit d’utiliser l’API de [suppression de jeu de données](https://doc.data.gouv.fr/api/reference/#/datasets/delete\_dataset):

CURL

```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -X DELETE $API/datasets/$DATASET/
```

HTTPiePython

Le jeu de données est maintenant **marqué comme supprimé**, il reste visible uniquement par vous et les membres de votre organisation, ainsi que par l’équipe d’administrateur de data.gouv.fr. Il sera purgé (supprimé définitivement de la plateforme), d’ici la fin de la journée.

#### Restauration d’un jeu de données supprimé par erreur <a href="#restauration-dun-jeu-de-donnees-supprime-par-erreur" id="restauration-dun-jeu-de-donnees-supprime-par-erreur"></a>

Tant que le jeu de données n’a pas été purgé, vous avez la possibilité de le restaurer:

**🚧 Bientôt 🚧**
