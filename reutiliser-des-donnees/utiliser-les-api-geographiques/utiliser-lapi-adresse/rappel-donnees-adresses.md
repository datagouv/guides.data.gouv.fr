# Rappel sur les données adresses

## Comment les données d’adresses sont-elles constituées ? <a href="#comment-les-donnees-d-adresses-sont-elles-constituees" id="comment-les-donnees-d-adresses-sont-elles-constituees"></a>

La donnée adresse qui compose la Base Adresse Nationale (BAN) est soit :

* issue de données provenant d’acteurs historiques de l’adresse (IGN, Cadastre, etc.) ;
* issue des Bases Adresses Locales (BAL) qui sont l’inventaire des adresses créé par les communes.

À terme, ces dernières devraient devenir la seule source. La commune doit certifier ces adresses, c’est-à-dire valider que les adresses saisies sont justes.

L’image ci-dessous résume la situation pour consolider les données adresses :

<figure><img src="../../../.gitbook/assets/schema-donnees-ban.681a4c32.svg" alt=""><figcaption><p>Schéma explicatif de la consolidation des données d'adresses</p></figcaption></figure>

## **Quels sont les usages de l’API Adresse ?** <a href="#quels-sont-les-usages-de-l-api-adresse" id="quels-sont-les-usages-de-l-api-adresse"></a>

L'API Adresse est utilisée principalement pour :

* trouver par un formulaire une adresse pour la corriger et/ou récupérer des coordonnées en ayant une liste de choix pour trouver le résultat : c’est l’autocomplétion;
* fournir un fichier tabulaire pour obtenir en retour une version enrichie des coordonnées et d’autres informations.

## Comment accéder aux données d’adresses ? <a href="#comment-acceder-aux-donnees-d-adresses" id="comment-acceder-aux-donnees-d-adresses"></a>

Pour accéder aux données d'adresses, il est possible de :

* **Récupérer directement les données**. Cette méthode s’adresse à des utilisateurs avancés. Vous avez 2 choix
  * prendre les données au niveau départements ou France via https://adresse.data.gouv.fr/donnees-nationales
  * récupérer les communes à une échelle EPCI ou communes en passant par https://adresse.data.gouv.fr/deploiement-bal Vous pouvez vous référer à [cet article du site Geotribu](https://geotribu.fr/articles/2021/2021-09-07_traiter_fichiers_adresse_gdal_csv_vrt/#introduction) pour un exemple d'intégration
* **Utiliser l’API de recherche**. Cette API peut rechercher des adresses soit via un appel unique par adresse soit en mode "_batch_" : on passe un fichier avec une liste d’adresse, une par ligne et on retourne la première adresse retournée pour chacune des lignes.

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-06-19 à 11.20.02.png" alt=""><figcaption><p>Page d'accueil d'adresse.data.gouv.fr</p></figcaption></figure>
