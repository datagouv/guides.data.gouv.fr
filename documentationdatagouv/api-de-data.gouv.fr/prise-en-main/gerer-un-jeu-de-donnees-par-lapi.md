---
icon: arrow-down-arrow-up
---

# Gérer un jeu de données par l'API

Cette page documente les principales interactions que vous pouvez avoir avec un jeu de données par l’API.

Il est recommandé d’avoir lu l'[introduction](/broken/pages/Q9seeEdFUuGFGyWy4TKX) et la page [prise en main de l'API](/broken/pages/fWVTUwz2ZdQFY6vY4wlL) avant de consulter cette page.

Tous les exemples qui suivent sont réalisés avec un compte :

* qui est actif
* dont la clé d’API est `my-api-key`
* qui est membre d’une organisation dont l’identifiant est `5bbb6d6cff66bd4dc17bfd5a`.

Les exemples portants sur un jeu de données existant utilisent l’identifiant `5bc04b2cff66bd680e499f4a`. Ceux portants sur une ressource existante de ce jeu de données utilisent l’identifiant `54d47250-1daf-483b-965a-3013f8c76617`.

Pour simplifier la lecture de ces exemples, il y sera fait référence par les variables suivantes pour chaque langage:

{% tabs %}
{% tab title="CURL" %}
```bash
# Tous les examples CURL sont executés avec cette convention
# CURL doit être installé
export API = 'https://www.data.gouv.fr/api/1'
export API_KEY = 'my-api-key'
export ORG = '5bbb6d6cff66bd4dc17bfd5a'
export DATASET = '5bc04b2cff66bd680e499f4a'
export RESOURCE = '54d47250-1daf-483b-965a-3013f8c76617'
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
# Tous les examples HTTPie sont executés avec cette convention
# HTTPie doit être installé
export API = 'https://www.data.gouv.fr/api/1'
export API_KEY = 'my-api-key'
export ORG = '5bbb6d6cff66bd4dc17bfd5a'
export DATASET = '5bc04b2cff66bd680e499f4a'
export RESOURCE = '54d47250-1daf-483b-965a-3013f8c76617'
```
{% endtab %}

{% tab title="Python" %}
```python
# Tous les exemples Python sont executés avec cette convention

import requests  # installé avec `pip install requests`

API = 'https://www.data.gouv.fr/api/1'
API_KEY = 'my-api-key'
ORG = '5bbb6d6cff66bd4dc17bfd5a'
DATASET = '5bc04b2cff66bd680e499f4a'
RESOURCE = '54d47250-1daf-483b-965a-3013f8c76617'
HEADERS = {
    'X-API-KEY': API_KEY,
}


def api_url(path):
    return ''.join(API, path)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
# Tous les exemples Python sont executés avec cette convention

from datagouv import Client, Dataset, Resource  # installé avec `pip install datagouv-client`

# vous devez avoir les droits sur les objets que vous souhaitez modifier modifier
ORG = "5bbb6d6cff66bd4dc17bfd5a"
DATASET = "5bc04b2cff66bd680e499f4a"
RESOURCE = "54d47250-1daf-483b-965a-3013f8c76617"
client = Client(
    environment="www",  # pour cibler la plateforme de production, également possible de cibler demo ou dev
    api_key="my-api-key",  # utilisez bien la clé API de la plateforme spécifiée ci-dessus
)
```
{% endtab %}
{% endtabs %}

## Création d’un jeu de données <a href="#creation-dun-jeu-de-donnees" id="creation-dun-jeu-de-donnees"></a>

Pour créer un jeu de données, nous allons utiliser l’API de création de jeu de données.

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "my title", "description": "My description", "organization": "$ORG"}' \
     -X POST $API/datasets/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http POST $API/datasets/ \
     X-Api-Key:$API_KEY \
     title="Mon titre" \
     description="Ma description" \
     organization=$ORG
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/')
response = requests.post(url, json={
    'title': 'Mon titre',
    'description': 'Ma description',
    'organization': ORG,
}, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
dataset = client.dataset().create(
    {
        "title": "Mon titre", 
        "description": "Ma description",
        "organization": ORG,
    },
)
```
{% endtab %}
{% endtabs %}

La réponse en JSON contient les métadonnées du jeu de données créé, en particulier l’identifiant et le slug.

La fiche du jeu de données est maintenant créée et il est maintenant possible d’y ajouter des ressources.

{% hint style="warning" %}
Par défaut, un jeu de données créé via l’API est public. Afin de créer et maintenir un jeu de données en brouillon, il faut mettre l’attribut `private: true` dans chaque appel à l’API. Sinon, chaque modification d’un jeu de données par l’API va le passer en public.
{% endhint %}

## Ajout d’une ressource <a href="#ajout-dune-ressource" id="ajout-dune-ressource"></a>

Pour créer une ressource, nous allons utiliser l’API création d’une ressource.

Il existe 2 cas de création de ressource :

* avec envoi d’un fichier, dit ressource locale ;
* avec référencement d’un fichier distant, dit ressource distante.

### **En envoyant un fichier**

Nous allons utiliser l’API d’envoi de ressource pour envoyer le fichier.

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -F "file=@/chemin/vers/le/fichier" \
     -X POST $API/datasets/$DATASET/upload/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http -f POST $API/datasets/$DATASET/upload/ \
     X-Api-Key:$API_KEY \
     file@/chemin/vers/le/fichier
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/upload/'.format(DATASET))
response = requests.post(url, files={
    'file': open('/chemin/vers/le/fichier', 'rb'),
}, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```
resource = client.resource().create_static(
    file_to_upload="/chemin/vers/le/fichier",
    payload={
        "title": "Nouvelle ressource",
        "type": "main",  # optionnel, "main" par défaut
    },
    dataset_id=DATASET,
)

# ou alternativement au sein du dataset
dataset = client.dataset(DATASET)
resource = dataset.create_static(
    file_to_upload="/chemin/vers/le/fichier",
    payload={
        "title": "Nouvelle ressource",
        "type": "main",  # optionnel, "main" par défaut
    },
)
```
{% endtab %}
{% endtabs %}

La ressource est automatiquement créée et il est possible de modifier _a posteriori_ les métadonnées avec l’API de mise à jour de ressource comme décrit [plus bas](gerer-un-jeu-de-donnees-par-lapi.md#mise-a-jour-des-metadonnees-dune-ressource).

### **En référençant une URL existante**

L’API de création de ressource permet de créer une ressource distante. Dans notre cas, un fichier csv hébergé sur l’URL [https://url.to/ressource.csv](https://url.to/ressource.csv).

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "my title", "description": "My description", "type": "main", filetype: "remote", "format": "csv",  "url": "https://url.to/ressource.csv"}' \
     -X POST $API/datasets/$DATASET/resources/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http POST $API/datasets/$DATASET/ressources/ \
     X-Api-Key:$API_KEY \
     title="Mon titre" \
     description="Ma description" \
     url="https://url.to/ressource.csv" \
     type="main" filetype="remote" format="csv"
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/resources/'.format(DATASET))
response = requests.post(url, json={
    'title': 'Mon titre',
    'description': 'Ma description',
    'url': 'https://url.to/ressource.csv',
    'type': 'main',
    'filetype': 'remote',
    'format': 'csv',
}, headers=HEADERS)

```
{% endtab %}

{% tab title="datagouv-client" %}
<pre class="language-python"><code class="lang-python">resource = client.resource().create_remote(
    payload={
        "url": "https://url.to/ressource.csv",
        "title": "Nouvelle ressource distante",
        "type": "main",  # optionnel, "main" par défaut
    },
    dataset_id=DATASET,
)

# ou alternativement au sein du dataset
dataset = client.dataset(DATASET)
<strong>resource = dataset.create_remote(
</strong>    payload={
        "url": "https://url.to/ressource.csv",
        "title": "Nouvelle ressource distante",
        "type": "main",  # optionnel, "main" par défaut
    },
)
</code></pre>
{% endtab %}
{% endtabs %}

## Modification d’un jeu de données <a href="#modification-dun-jeu-de-donnees" id="modification-dun-jeu-de-donnees"></a>

La suite des opérations s’appliquent sur le même jeu de données dont l’identifiant est `5bc04b2cff66bd680e499f4a` sur lequel vous avez les permissions nécéssaires à la modification. Ce jeu de données possède une ressource `54d47250-1daf-483b-965a-3013f8c76617` qui est soit distante soit locale suivant les exemples.

### Mise à jour des metadonnées de la fiche <a href="#mise-a-jour-des-metadonnees-de-la-fiche" id="mise-a-jour-des-metadonnees-de-la-fiche"></a>

Cette requête permet de mettre à jour les métadonnées d’un jeu de données en utilisant l’API de mise à jour de jeu de données

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "Nouveau titre", "description": "Nouvelle description"}' \
     -X PUT $API/datasets/$DATASET/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http PUT $API/datasets/$DATASET/ \
     X-Api-Key:$API_KEY \
     title="Nouveau titre" \
     description="Nouvelle description"
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/'.format(DATASET))
response = requests.put(url, json={
    'title': 'Nouveau titre',
    'description': 'Nouvelle description',
}, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
dataset = client.dataset(DATASET)
dataset.update(
    {
        "title": "Nouveau titre",
        "description": "Nouvelle description",
    },
)
```
{% endtab %}
{% endtabs %}

### Mise à jour des métadonnées d’une ressource <a href="#mise-a-jour-des-metadonnees-dune-ressource" id="mise-a-jour-des-metadonnees-dune-ressource"></a>

Cette requête permet de mettre à jour les métadonnées d’une ressource en utilisant l’API de mise à jour de ressource

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Content-Type:application/json" \
     -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     --data '{"title": "Nouveau titre", "description": "Nouvelle description"}' \
     -X PUT $API/datasets/$DATASET/resources/$RESOURCE/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http PUT $API/datasets/$DATASET/resources/$RESOURCE/ \
     X-Api-Key:$API_KEY \
     title="Nouveau titre" \
     description="Nouvelle description"
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/resources/{}/'.format(DATASET, RESOUCE))
response = requests.put(url, json={
    'title': 'Nouveau titre',
    'description': 'Nouvelle description',
}, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
resource = client.resource(
    id=RESOURCE,
    dataset_id=DATASET,  # optionnel, il est récupéré si non renseigné 
)
resource.update(
    {
        "title": "Nouveau titre",
        "description": "Nouvelle description",
    },
)
```
{% endtab %}
{% endtabs %}

### Remplacer un fichier de ressource <a href="#remplacer-un-fichier-de-ressource" id="remplacer-un-fichier-de-ressource"></a>

Dans le cas d’une mise à jour de fichier de ressource locale (correction, ajout de données…),il est possible d’utiliser l’API de mise à jour de fichier. L’ancien fichier sera supprimé.

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -F "file=@/chemin/vers/le/nouveau/fichier" \
     -X POST $API/datasets/$DATASET/resources/$RESOURCE/upload/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http -f POST $API/datasets/$DATASET/resources/$RESOURCE/upload/ \
     X-Api-Key:$API_KEY \
     file@/chemin/vers/le/nouveau/fichiers
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/resources/{}/upload/'.format(DATASET, RESOURCE))
response = requests.post(url, files={
    'file': open('/chemin/vers/le/nouveau/fichier', 'rb'),
}, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
resource = client.resource(
    id=RESOURCE,
    dataset_id=DATASET,  # optionnel, il est récupéré si non renseigné 
)
resource.update(
    file_to_upload="/chemin/vers/le/nouveau/fichier"
)
```
{% endtab %}
{% endtabs %}

### Signaler une mise à jour de fichier distant <a href="#signaler-une-mise-a-jour-de-fichier-distant" id="signaler-une-mise-a-jour-de-fichier-distant"></a>

Dans le cas d’une ressource distante, lorsque le fichier distant est mis à jour, il est important de le signaler afin que la fiche soit mise à jour et que les usagers le sache.

**🚧 A venir 🚧**

### Suppression d’une ressource <a href="#suppression-dune-ressource" id="suppression-dune-ressource"></a>

l’API de suppression de ressource permet de supprimer une ressource de la fiche d’un jeu de données. Le fichier associé est aussi supprimé.

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -X DELETE $API/datasets/$DATASET/resources/$RESOURCE
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http DELETE $API/datasets/$DATASET/ressources/$RESOURCE/ X-Api-Key:$API_KEY
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/resources/{}/'.format(DATASET, RESOURCE))
response = requests.delete(url, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
resource = client.resource(
    id=RESOURCE,
    dataset_id=DATASET,  # optionnel, il est récupéré si non renseigné 
)
resource.delete()
```
{% endtab %}
{% endtabs %}

## Suppression d’un jeu de données <a href="#suppression-dun-jeu-de-donnees" id="suppression-dun-jeu-de-donnees"></a>

Pour supprimer un jeu de données, il suffit d’utiliser l’API de suppression de jeu de données:

{% tabs %}
{% tab title="CURL" %}
```bash
curl -H "Accept:application/json" \
     -H "X-Api-Key:$API_KEY" \
     -X DELETE $API/datasets/$DATASET/
```
{% endtab %}

{% tab title="HTTPie" %}
```bash
http DELETE $API/datasets/$DATASET/ X-Api-Key:$API_KEY
```
{% endtab %}

{% tab title="Python" %}
```python
url = api_url('/datasets/{}/'.format(DATASET))
response = requests.delete(url, headers=HEADERS)
```
{% endtab %}

{% tab title="datagouv-client" %}
```python
dataset = client.dataset(DATASET)
dataset.delete()
```
{% endtab %}
{% endtabs %}

Le jeu de données est maintenant **marqué comme supprimé**, il reste visible uniquement par vous et les membres de votre organisation, ainsi que par l’équipe d’administrateur de data.gouv.fr. Il sera purgé (supprimé définitivement de la plateforme), d’ici la fin de la journée.

### Restauration d’un jeu de données supprimé par erreur <a href="#restauration-dun-jeu-de-donnees-supprime-par-erreur" id="restauration-dun-jeu-de-donnees-supprime-par-erreur"></a>

Tant que le jeu de données n’a pas été purgé, vous avez la possibilité de le restaurer:

**🚧 A venir 🚧**
