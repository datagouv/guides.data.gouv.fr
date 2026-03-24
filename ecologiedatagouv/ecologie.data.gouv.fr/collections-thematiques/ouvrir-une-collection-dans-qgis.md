---
description: Comment ouvrir une collection vers QGIS depuis ecologie.data.gouv.fr ?
---

# Ouvrir une collection dans QGIS

### Ouvrir une collection dans QGIS

De manière similaire à [un jeu de données](https://app.gitbook.com/o/w6D6SnLwCXQaMMSzcTvp/s/K56ETHxhBea8DHmbPCgt/~/edit/~/changes/15/ecologie.data.gouv.fr/toutes-les-donnees/ouvrir-un-jeu-de-donnees-dans-qgis), il est possible d'ouvrir l'**intégralité des jeux de données éligibles d'une collection** dans QGIS. Le bouton "Ouvrir la collection dans QGIS (WFS/WMS)" **en bas de la collection** déclenche la génération du fichier QLR correspondant.

<figure><img src="../../.gitbook/assets/export_collection (2).png" alt=""><figcaption></figcaption></figure>

Les données / couches sont organisées de manière arborescente pour refléter la structure de la collection :

* Nom de la collection
  * Nom du groupe contenant le jeu de données
    * Libellé de l'association du jeu de données à la collection
      * Nom du fichier (ressource) sur data.gouv.fr

<figure><img src="../../.gitbook/assets/Capture d’écran 2026-01-27 à 09.19.57.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Quelles règles sont appliquées pour l'éligibilité, la sélection et la détection des couches d'un jeu de données ?**

Les mêmes règles que pour un jeu de données unitaire sont appliquées à la liste des jeux de données d'une collection (voir [Ouvrir un jeu de données dans QGIS](https://app.gitbook.com/o/w6D6SnLwCXQaMMSzcTvp/s/K56ETHxhBea8DHmbPCgt/~/edit/~/changes/15/ecologie.data.gouv.fr/toutes-les-donnees/ouvrir-un-jeu-de-donnees-dans-qgis)).
{% endhint %}
