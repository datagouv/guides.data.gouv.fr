# Gérer un bouquet via l’API data.gouv.fr

### Utilisation de l’API data.gouv.fr

#### Documentation de l’API [data.gouv.fr](http://data.gouv.fr)

* [https://guides.data.gouv.fr/guide-data.gouv.fr/readme-1](https://guides.data.gouv.fr/guide-data.gouv.fr/readme-1)
* [https://www.data.gouv.fr/api/2/](https://www.data.gouv.fr/api/2/)

#### URLs d’accès à l’API

* environnement de démo (fortement recommandé pour tests) : `https://demo.data.gouv.fr/api/2`, alimente [https://demo.ecologie.data.gouv.fr](https://demo.ecologie.data.gouv.fr)
* production : `https://www.data.gouv.fr/api/2`, alimente [https://ecologie.data.gouv.fr](https://ecologie.data.gouv.fr)

On utilisera l’environnement de démo dans les exemples ci-dessous.

#### Authentification et gestion des droits

* L’utilisation de l’API nécessite une clé passée en tant que header `x-api-key` (cf documentation)
* Il est recommandé de publier un bouquet en tant qu’organisation plutôt qu’en tant qu’individu. Il faut donc que le compte dont on utilise la clé d’API soit rattaché à l’organisation cible (cf documentation). L’identifiant technique de l’organisation est disponible sur la page de l’organisation sur [data.gouv.fr](http://data.gouv.fr), dans l’onglet Informations, sous la section “Informations techniques” (ex : [https://www.data.gouv.fr/organizations/ecolab-1/information](https://www.data.gouv.fr/organizations/ecolab-1/information) → `67884b4da4fca9c97bbef479`)

On utilisera cette organisation de rattachement dans les exemples ci-dessous.

#### Requêtes

L’API de [data.gouv.fr](http://data.gouv.fr) est de type JSON-REST. Dans la suite du document, on utilisera le formalisme suivant :

* `POST {url}` pour indiquer une requête de type POST vers url
* Un bloc de code de type `jsonc` pour documenter le corps JSON de la requête. Les commentaires `// xxx` doivent être omis dans une requête réelle.

```json
{
  // exemple d'attribut (commentaire)
  "data": []
}
```

### Création d’un bouquet

Un bouquet est représenté par un object `Topic` sur [data.gouv.fr](http://data.gouv.fr), on utilise donc l’API correspondante `/api/2/topics`.

`POST <https://demo.data.gouv.fr/api/2/topics/`

```json
{
	"name": "Mon bouquet de test (sujet)",
	"description": "La description de mon bouquet de test (objectif)",	
	// tags obligatoires
	"tags": [
		"ecospheres",
		"univers-ecospheres",
		// tag correspondant à une thématique, voir la liste de référence ci-dessous
		"ecospheres-theme-mieux-preserver-valoriser-ecosystemes"
	],
	// couverture territoriale (facultatif), ici "France"
	// utiliser l'id de la zone depuis https://www.data.gouv.fr/api/1/spatial/zones/suggest/?q=france
	"spatial": {
		"zones": ["country:fr"]
	},
	// statut brouillon, `false` pour publier
	"private": true,
	// organisation de rattachement (id technique)
	"organization": "67884b4da4fca9c97bbef479",
	"extras": {
		"ecospheres": {}
	}
}
```

La réponse contient un champ `id`  qu’on utilisera plus tard pour modifier le bouquet (exemple 68e37680328504830a326804).&#x20;

Liste des thématiques et tag associés :

| Thématique                                   | Tag                                                    |
| -------------------------------------------- | ------------------------------------------------------ |
| Mieux consommer                              | ecospheres-theme-mieux-consommer                       |
| Mieux produire                               | ecospheres-theme-mieux-produire                        |
| Mieux préserver et valoriser nos ecosystèmes | ecospheres-theme-mieux-preserver-valoriser-ecosystemes |
| Mieux se déplacer                            | ecospheres-theme-mieux-se-deplacer                     |
| Mieux se loger                               | mieux-se-loger                                         |
| Mieux se nourrir                             | ecospheres-theme-mieux-se-nourrir                      |
| Autre                                        | ecospheres-theme-autre                                 |

### Ajout d’un facteur (jeu de données) à un bouquet

Un facteur est représenté par un `element` rattaché à un `Topic` sur [data.gouv.fr](http://data.gouv.fr). On utilise donc l’API correspondante `/api/2/topics/{topic_id}/elements/`.

L’exemple ci-dessous crée plusieurs facteurs, un pour chaque type possible :

* pointe vers un jeu de données référencé sur [data.gouv.fr](http://data.gouv.fr)
* pointe vers un jeu de données non référencé sur [data.gouv.fr](http://data.gouv.fr) (ie une URL)
* jeu de données “non trouvé” (Je n'ai pas trouvé la donnée)
* jeu de données “non cherché” (Je n'ai pas cherché la donnée)

`POST <https://demo.data.gouv.fr/api/2/topics/68e37680328504830a326804/elements/`

```json
[
  // facteur pointant vers un jeu de données sur data.gouv.fr
  {
	  "title": "Libellé du jeu de données depuis data.gouv.fr",
	  "description": "Raison d'utilisation dans ce bouquet",
	  "element": {
		  "class": "Dataset",
		  // identifiant technique du jeu de données sur data.gouv.fr (onglet Informations)
		  "id": "67a497a30f69225d739b8b5b"
		},
		"extras": {
	    "ecospheres": {
        "availability": "available",
        // construit avec le même identifiant de jeu de données que plus haut
        "uri": "/datasets/67a497a30f69225d739b8b5b",
        "group": "Mon regroupement"
	    }
	  }
  },
  // facteur pointant vers un jeu de données externe
  {
	  "title": "Libellé du jeu de données externe",
	  "description": "Raison d'utilisation dans ce bouquet",
	  "element": null,
	  "extras": {
	    "ecospheres": {
	        "availability": "url available",
	        "uri": "http://example.com",
	        "group": "Mon regroupement"
	    }
		}
  },
  // facteur "non trouvé"
  {
	  "title": "Libellé du jeu de données non trouvé",
	  "description": "Raison d'utilisation dans ce bouquet",
	  "element": null,
	  "extras": {
		  "ecospheres": {
		    "availability": "missing",
		    "uri": null,
		    "group": "Mon regroupement"
		  }
		}
  },
  // facteur "non cherché"
  {
	  "title": "Libellé du jeu de données non cherché",
	  "description": "Raison d'utilisation dans ce bouquet",
	  "element": null,
	  "extras": {
		  "ecospheres": {
		    "availability": "not available",
		    "uri": null,
		    "group": "Mon regroupement"
		  }
		}
  }  
]
```

Dans cet exemple, chacun des facteurs est associé à un regroupement “Mon regroupement”. Cette valeur est libre et peut également être omise totalement (y compris l’attribut `group`) si on ne souhaite pas utiliser de regroupement pour un facteur.

La réponse contient un tableau d’objets avec pour chacun un champ `id` qu’on utilisera plus tard pour modifier un des facteurs (exemple `68e37f9311f7009c05fb333b`).

### Modification d’un facteur

Dans cet exemple, on modifie le regroupement d’un facteur existant. Il n’est pas nécessaire de reprendre les champs inchangés (titre, description…), on les garde toutefois pour référence dans cet exemple.

`PUT <https://demo.data.gouv.fr/api/2/topics/68e37680328504830a326804/elements/68e37f9311f7009c05fb333b/`>

```json
{
  "title": "Libellé du jeu de données depuis data.gouv.fr",
  "description": "Raison d'utilisation dans ce bouquet",
  "element": {
    "class": "Dataset",
    "id": "67a497a30f69225d739b8b5b"
  },
  "extras": {
    "ecospheres": {
        "availability": "available",
        "uri": "/datasets/67a497a30f69225d739b8b5b",
        "group": "Nouveau regroupement"
      }
    }
}
```

### Suppression d’un facteur

`DELETE <https://demo.data.gouv.fr/api/2/topics/68e37680328504830a326804/elements/68e37f9311f7009c05fb333b/`>

### Modification ou création d’un bouquet avec ses facteurs

Il est possible de manipuler un bouquet avec ses facteurs associés (`POST <https://demo.data.gouv.fr/api/2/topics/` dans le cas d’une création, `PUT <https://demo.data.gouv.fr/api/2/topics/{topic_id}` dans le cas d’une modification).

Dans le cas d’une modification, il est recommandé d’utiliser des opérations atomiques sur les éléments / facteurs afin de bénéficier du suivi des modifications sur les facteurs d’un bouquet (l’interface affichera “le facteur xxx a été modifié par untel à tel date”).

```json
{
	"name": "Mon bouquet de test (sujet)",
	"description": "La description de mon bouquet de test (objectif)",	
	"tags": [
		"ecospheres",
		"univers-ecospheres",
		"ecospheres-theme-mieux-preserver-valoriser-ecosystemes"
	],
	"spatial": {
		"zones": ["country:fr"]
	},
	"private": true,
	"organization": "67884b4da4fca9c97bbef479",
	"extras": {
		"ecospheres": {}
	},
	// facteur(s) associé(s)
	"elements": [
		{
		  "title": "Libellé du jeu de données depuis data.gouv.fr",
		  "description": "Raison d'utilisation dans ce bouquet",
		  "element": {
		    "class": "Dataset",
		    "id": "67a497a30f69225d739b8b5b"
		  },
		  "extras": {
		    "ecospheres": {
	        "availability": "available",
	        "uri": "/datasets/67a497a30f69225d739b8b5b",
	        "group": "Nouveau regroupement"
	      }
	    }
	  }
	]
} 
```
