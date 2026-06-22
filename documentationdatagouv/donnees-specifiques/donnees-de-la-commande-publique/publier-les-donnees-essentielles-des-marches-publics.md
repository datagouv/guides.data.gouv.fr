---
description: >-
  Publier les données essentielles d’attribution, choisir la bonne structure et
  déposer les ressources sur data.gouv.fr.
---

# Publier les données essentielles des marchés publics

Les acheteurs publics doivent publier les données essentielles d’attribution de leurs marchés.

Cette page résume le cadre, les formats attendus et les modalités de publication sur data.gouv.fr.

### Obligation légale

Depuis le 1er octobre 2018, les acheteurs publics doivent publier les données d’attribution de leurs marchés au plus tard deux mois après la notification.

La publication sur data.gouv.fr est obligatoire à partir du 1er janvier 2024.

### Structure des données à publier

Deux versions du schéma existent selon la période de publication :

* jusqu’au 31 décembre 2023 : [schéma 1.5.0](https://schema.data.gouv.fr/139bercy/format-commande-publique/1.5.0/) ;
* à partir du 1er janvier 2024 : [schéma 2.0.0](https://schema.data.gouv.fr/139bercy/format-commande-publique/2.0.0/).

Pour le cadre réglementaire et les précisions métier, consultez aussi :

* [la page de la direction des affaires juridiques](https://www.economie.gouv.fr/daj/ouverture-des-donnees-commande-publique) ;
* [l’article de data.gouv.fr sur les données essentielles](https://www.data.gouv.fr/fr/posts/le-point-sur-les-donnees-essentielles-de-la-commande-publique/).

### Sources des données publiées

Les données essentielles visibles sur data.gouv.fr peuvent provenir de trois sources :

1. **DGFiP** : transmission via Hélios et [PES Marché](https://www.collectivites-locales.gouv.fr/protocole-dechange-standard-pes-0), puis mise à disposition par Etalab ;
2. **AIFE** : publication des données issues de ses places de marchés, notamment [PLACE](https://www.marches-publics.gouv.fr/?page=entreprise.AccueilEntreprise) ;
3. **Profils d’acheteurs** : publication via l’API de data.gouv.fr ou via un catalogue DCAT moissonnable.

### Publier via l’API de data.gouv.fr

La documentation de l’API est disponible sur [data.gouv.fr](https://www.data.gouv.fr/fr/apidoc).

Pour créer un jeu de données, consultez aussi la documentation de l’endpoint de création : [création d’un jeu de données](https://www.data.gouv.fr/fr/apidoc/#!/datasets/create_dataset).

Deux structures de publication sont possibles :

1. **Structure plateforme** : un jeu de données par plateforme de marchés, identifiée par son SIRET ;
2. **Structure acheteur** : un jeu de données par acheteur public, identifié par son SIRET.

{% hint style="info" %}
Pour l’archivage et la pérennité, le téléversement direct des fichiers sur data.gouv.fr est préférable à un lien vers un serveur externe.
{% endhint %}

#### Champs recommandés pour le jeu de données

**Nom**

Utilisez l’un des formats suivants :

* plateforme : `Données essentielles des marchés publics - {nom de la plateforme}` ;
* acheteur : `Données essentielles des marchés publics - {nom de l’acheteur}`.

Exemple :

> Données essentielles des marchés publics - Conseil régional de Bretagne

**Description**

La description doit présenter :

* le contexte de publication ;
* le cadre réglementaire ;
* les liens utiles ;
* éventuellement un lien vers l’interface de consultation du profil d’acheteur.

Vous pouvez y rappeler que les données sont publiées au titre des arrêtés encadrant les données essentielles de la commande publique.

**Mots-clés**

Ajoutez au minimum :

* `données-essentielles` ;
* `commande-publique`.

**Extras**

Si le jeu de données correspond à un **acheteur** et non à une plateforme, ajoutez `siret` dans `extras`.

```json
{
  "title": "Données essentielles des marchés publics - Conseil régional de Bretagne",
  "extras": {
    "siret": "89764547841001"
  }
}
```

Si le jeu de données correspond à une **plateforme**, ne renseignez pas `extras.siret`.

**Licence**

Renseignez la licence ouverte : `fr-lo`.

**Organisation**

Indiquez l’identifiant de l’organisation data.gouv.fr qui publie les données.

L’utilisateur qui publie doit appartenir à cette organisation.

**Fréquence**

Renseignez la fréquence prévue de mise à jour.

#### Ajouter une ressource

Une fois le jeu de données créé, ajoutez une ou plusieurs ressources.

La documentation de l’ajout de ressource est disponible ici : [ajouter une ressource à un jeu de données](https://www.data.gouv.fr/fr/apidoc/#!/datasets/upload_new_dataset_resource).

Exemple de commande :

```bash
curl --request POST \
  --url https://data.gouv.fr/api/1/datasets/<dataset-id>/upload/ \
  --header "content-type: multipart/form-data" \
  --header "x-api-key: <api-key>" \
  --form "file=@<chemin-du-fichier>"
```

**Nom du fichier**

Utilisez le format suivant :

`DECP-{SIRET}-{année}-{mois}-{jour}-{numéro-de-séquence}.{extension}`

Avec :

* `DECP` pour données essentielles de la commande publique ;
* `SIRET` de la plateforme ou de l’acheteur ;
* `année`, `mois`, `jour` de publication sur data.gouv.fr ;
* `numéro-de-séquence` sur deux chiffres, à incrémenter en cas de plusieurs publications le même jour ;
* `extension` : `xml` ou `json`.

Exemple :

> DECP-89764547841001-2018-11-28-01.xml

**Métadonnées de la ressource**

* `url` : à renseigner seulement si le fichier reste hébergé à l’extérieur ;
* `title` : identique au nom du fichier ;
* `filetype` : `xml` ou `json` ;
* `mime` : `application/xml` ou `application/json` ;
* `type` : `main`.

### Récupérer les données transmises par la DGFiP

#### Via le serveur de fichiers

Les données transmises par la DGFiP peuvent être récupérées depuis le serveur de fichiers opéré par Etalab.

Ce mode est particulièrement adapté si un acheteur publie un volume important de marchés.

Format d’URL :

`http://files.data.gouv.fr/decp/{siret}/{année}/{mois}/{jour}/DECP-{siret}-{année}-{mois}-{jour}-{seq}.xml`

Avec :

* `siret` : SIRET de l’acheteur ;
* `année`, `mois`, `jour` : date de réception par Etalab ;
* `seq` : numéro de séquence sur deux chiffres.

Exemple :

> http://files.data.gouv.fr/decp/21440036800012/2019/01/18/DECP-21440036800012-2019-01-18-01.xml

#### Via l’API

Les fichiers transmis par la DGFiP ne sont pas le mode de consultation le plus naturel via l’API, car ils sont avant tout exposés sur le serveur de fichiers.

En pratique, privilégiez donc [files.data.gouv.fr/decp](https://files.data.gouv.fr/decp).

Si vous devez lister les ressources d’un jeu de données référencé sur data.gouv.fr, utilisez :

```bash
curl https://data.gouv.fr/api/1/datasets/<dataset-id-ou-slug>
```

Exemples :

> https://data.gouv.fr/api/1/datasets/56cc6d6988ee385864fa79d0

> https://data.gouv.fr/api/1/datasets/referentiel-de-donnees-marches-publics
