# Faire une recherche SPARQL

{% hint style="info" %}
## Qu'est-ce qu'une recherche SPARQL ?

SPARQL (SPARQL Protocol and RDF Query Language) est un langage de requête utilisé pour interroger des bases de données RDF (Resource Description Framework). RDF est un modèle standardisé pour représenter les informations sur le web. SPARQL permet d'extraire et de manipuler les données stockées sous ce format, permettant de naviguer efficacement dans les informations interconnectées du web sémantique.
{% endhint %}

## Comment faire une recherche SPARQL ?

Il n’existe actuellement pas de point d’accès SPARQL directement sur [data.gouv.fr](http://data.gouv.fr/). Pour répondre à vos besoins en matière de recherche et d’interrogation des données ouvertes françaises, nous vous recommandons d’utiliser [data.europa.eu](http://data.europa.eu/). Cette plateforme européenne moissonne régulièrement le catalogue de [data.gouv.fr](http://data.gouv.fr/), ce qui vous permet d’accéder aux données françaises et toutes les autres données européennes via leur endpoint SPARQL.

Pour effectuer une recherche SPARQL sur [**data.europa.eu**](http://data.europa.eu/), en particulier sur le catalogue français [**data.gouv.fr**](http://data.gouv.fr/) (appelé **Plateforme ouverte des données publiques françaises** sur [data.europa.eu](http://data.europa.eu/)), suivez ces étapes :

### Étape 1 : Accéder à l'interface de requête SPARQL

* Rendez-vous sur l'interface SPARQL de [**data.europa.eu**](http://data.europa.eu/) à l'adresse suivante : [https://data.europa.eu/data/sparql?locale=fr](https://data.europa.eu/data/sparql?locale=fr).
* Vous accéderez à une interface graphique où vous pouvez saisir vos requêtes SPARQL.

### Étape 2 : Comprendre les éléments de base d'une requête SPARQL

Les principaux éléments d'une requête SPARQL sont :

*   **PREFIX** : Déclare les préfixes utilisés pour éviter de répéter les URI complètes dans la requête. Par exemple :

    ```sparql
    PREFIX dcat: <http://www.w3.org/ns/dcat#>

    ```
*   **SELECT** : Indique les variables que vous souhaitez récupérer dans les résultats. Par exemple :

    ```sparql
    SELECT ?title ?description

    ```
*   **WHERE** : Spécifie les motifs de correspondance pour restreindre les informations à extraire. Par exemple :

    ```sparql
    WHERE {
      ?dataset dcat:title ?title ;
               dcat:description ?description .
    }

    ```
*   **LIMIT** : Limite le nombre de résultats retournés. Par exemple :

    ```sparql
    LIMIT 10

    ```

### Étape 3 : Exemple de requête SPARQL pour interroger le catalogue [**data.gouv.fr**](http://data.gouv.fr/)

Pour interroger les jeux de données du catalogue français [**data.gouv.fr**](http://data.gouv.fr/), utilisez la requête suivante :

```sparql
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX fo: <http://www.w3.org/1999/XSL/Format#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX dcat: <http://www.w3.org/ns/dcat#>
PREFIX dcterms: <http://purl.org/dc/terms/>

SELECT ?dataset ?title ?description ?publisher
WHERE {
  <http://data.europa.eu/88u/catalogue/plateforme-ouverte-des-donnees-publiques-francaises> dcat:dataset ?dataset .
  ?dataset dct:title ?title ;
           dct:description ?description ;
           dct:publisher ?publisher .
  FILTER(lang(?title) = '') .
  FILTER(lang(?description) = '') .
}
LIMIT 10
```

Cette requête sélectionne les jeux de données publiés par la "Plateforme ouverte des données publiques françaises" en récupérant leur titre et leur description.

### Étape 4 : Exécuter la requête

* Collez la requête dans l'éditeur SPARQL sur la page de [data.europa.eu](http://data.europa.eu/).
* Exécuter la requête.
* Les résultats s'afficheront sous forme de tableau, listant les jeux de données avec leurs titres et descriptions.

### Étape 5 : Exporter et utiliser les résultats

Vous pouvez exporter les résultats obtenus dans différents formats (CSV, JSON, XML) pour les analyser ou les intégrer dans d'autres systèmes.

### En savoir plus

Pour en savoir plus vous pouvez vous référer à la [documentation sur data.europa](https://data.europa.eu/en/about/sparql).
