---
description: >-
  Comment ouvrir un jeu de données ou un bouquet vers QGIS depuis
  ecologie.data.gouv.fr.
---

# Ouvrir dans QGIS

Depuis la page d'un bouquet, il est possible de :

* Ouvrir un jeu de données dans QGIS ;
* Ouvrir un bouquet et ses jeux de données dans QGIS.

### Ouvrir un jeu de données dans QGIS

Lorsqu'un jeu de données est rattaché à un bouquet et qu'il contient des services WFS et/ou WMS, il est possible de l'ouvrir directement dans QGIS en cliquant sur le bouton "Ouvrir dans QGIS" sur la carte du jeu de données.

<figure><img src="../../.gitbook/assets/Capture d’écran 2026-01-27 à 08.53.01.png" alt=""><figcaption></figcaption></figure>

Le bouton déclenche le téléchargement d'un [fichier QLR](https://docs.qgis.org/3.40/en/docs/user_manual/appendices/qgis_file_formats.html#qlr-the-qgis-layer-definition-file). En ouvrant ce fichier, la ou les couches WMS/WFS associées au jeu de données sont chargées dans QGIS.

<figure><img src="../../.gitbook/assets/Capture d’écran 2026-01-27 à 08.57.47.png" alt=""><figcaption></figcaption></figure>

Pour éviter des chargements trop longs ou non nécessaires, les couches sont décochées par défaut. Cochez la couche qui vous intéresse pour déclencher son chargement.

<figure><img src="../../.gitbook/assets/Capture d’écran 2026-01-27 à 09.14.11.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Quels jeux de données sont éligibles à l'ouverture dans QGIS ?**

Un jeu de données pointant via ses fichiers (ressources) sur data.gouv.fr vers un service WFS et/ou WMS est éligible. Les métadonnées des fichiers doivent être suffisamment précises pour que le système les reconnaisse. Idéalement, les fichiers portent la métadonnée `format` avec la valeur `ogc:wms` ou `ogc:wfs`.
{% endhint %}

{% hint style="info" %}
**Quel fichier est priorisé quand un jeu de données pointe vers plusieurs services WMS/WFS ?**

Lorsqu'un jeu de données pointe via ses fichiers (ressources) sur data.gouv.fr vers plusieurs services WFS et/ou WMS, le système priorise :

* WFS plutôt que WMS ;
* Le premier service trouvé dans la liste des fichiers (ressources).
{% endhint %}

{% hint style="info" %}
**Comment les noms de couches sont-ils détectés ?**

Le système tente de détecter les noms de couches dans :

* L'URL du service (eg `typeName=ma_couche`) — c'est le cas idéal ;
* Le nom du fichier (ressource) sur data.gouv.fr.

Si aucun nom crédible n'est détecté, le système :

* Ignore le fichier pour un service WMS ;
* Ouvre toutes les couches pour un service WFS.

Il est possible qu'un nom de couche invalide (non existant) sur le serveur soit déclaré dans le fichier QLR généré.
{% endhint %}

### Ouvrir un bouquet dans QGIS

De manière similaire au jeu de données, il est possible d'ouvrir l'intégralité des jeux de données éligibles d'un bouquet dans QGIS. Le bouton "Ouvrir le bouquet dans QGIS" en bas du bouquet déclenche la génération du fichier QLR correspondant.

<figure><img src="../../.gitbook/assets/Capture d’écran 2026-01-27 à 09.12.10.png" alt=""><figcaption></figcaption></figure>

Les données / couches sont organisées de manière arborescente pour refléter la structure du bouquet :

* Nom du bouquet
  * Nom du groupe contenant le jeu de données
    * Libellé de l'association du jeu de données au bouquet
      * Nom du fichier (ressource) sur data.gouv.fr

<figure><img src="../../.gitbook/assets/Capture d’écran 2026-01-27 à 09.19.57.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Quelles règles sont appliquées pour l'éligibilité, la sélection et la détection des couches d'un jeu de données ?**

Les mêmes règles que pour un jeu de données unitaire sont appliquées à la liste des jeux de données d'un bouquet (voir plus haut).
{% endhint %}
