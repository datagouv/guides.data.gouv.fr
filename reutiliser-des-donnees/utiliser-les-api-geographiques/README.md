---
description: >-
  Ce guide a vocation à vous accompagner dans l'usage des API géographiques
  principalement opérées par Etalab.
---

# Utiliser les API géographiques

{% hint style="danger" %}
[La Base Adresse Nationale est désormais portée par l'IGN](https://www.numerique.gouv.fr/espace-presse/la-base-adresse-nationale-ban-franchit-de-nouvelles-etapes-en-poursuivant-son-action-au-sein-de-lign/).&#x20;
{% endhint %}

Ce guide propose d'explorer des cas pratiques d'utilisation des API géographiques mises à votre disposition pour vous accompagner dans leur utilisation, que vous soyez en train de construire une carte ou que vous souhaitiez récupérer des données géographiques.

Ce guide s'adresse donc à plusieurs types de profils :

* Néophytes dans l'utilisation des APIs ;
* Intégrateurs web ;&#x20;
* Spécialistes du secteur géospatial.&#x20;

Il s'agit d'un outil évolutif et ouvert. Vous pouvez contribuer à l'améliorer en proposant une modification sur [GitHub](https://github.com/etalab/guides.etalab.gouv.fr/edit/master/apis-geo/) ou en [contactant directement](mailto:geo@data.gouv.fr) l'équipe Géo d'Etalab.&#x20;

{% hint style="info" %}
**Quelles sont les API géographiques dont il est question dans ce guide ?**&#x20;

* **API Adresse (Base Adresse Nationale - BAN)**

L'API Adresse permet d'interroger la Base Adresse Nationale, base de données de l’intégralité des adresses du territoire français. \
En intégrant l'API dans votre système d'information, vous pouvez facilement rechercher une adresse et notamment faire de l'autocomplétion et de la vérification d'adresse,  géolocaliser une adresse sur une carte ou encore faire une recherche géographique inversée (trouver la rue la plus proche de coordonnées géographiques).

* **API Découpage administratif (API Geo)**

L'API Découpage Administratif permet d'interroger les référentiels géographiques plus facilement. \
En intégrant l'API dans votre système d'information, vous pouvez notamment rechercher une commune par nom, code postal ou coordonnées géographiques, rechercher un département par son nom ou encore rechercher une région par son nom.&#x20;

* **Les tuiles vectorielles openmaptiles.geo.data.gouv.fr**

L'API permet de mettre à disposition des tuiles vectorielles qui sont affichables sur des cartes géographiques interactives. \
Elles servent principalement à afficher des fonds de plan mais aussi les contours cadastraux et les limites administratives en France. \
Cela permet de vous affranchir d'APIs cartographiques comme Google Maps.
{% endhint %}

{% hint style="success" %}
**Recommandations logiciels**

Il est recommandé d'avoir un navigateur web en ayant installé [l'extension JSONView](https://jsonview.com/) pour faciliter la compréhension des retours JSON.

Vous pouvez aussi installer un éditeur de texte plus agréable à utiliser que le Bloc-Notes/Notepad par défaut si vous êtes sous Windows. Il vous permettra en particulier lorsque vous faites des tests sur les URLs de les modifier avant de les copier dans la barre d'adresse de votre navigateur. Il peut s'agir de [Notepad++](https://notepad-plus-plus.org/downloads/) si vous êtes sous Windows ou bien de [Microsoft Visual Studio Code](https://code.visualstudio.com/) quel que soit votre système d'exploitation. Une liste plus complète d'éditeurs de texte est disponible [ici](https://fr.wikipedia.org/wiki/%C3%89diteur\_de\_texte#%C3%89diteurs\_de\_texte\_couramment\_utilis%C3%A9s).&#x20;
{% endhint %}

Dans ce guide, vous apprendrez comment :&#x20;

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Utiliser l'API Adresse</strong> </td><td><a href="utiliser-lapi-adresse/">utiliser-lapi-adresse</a></td></tr><tr><td><strong>Utiliser l'API Découpage administratif</strong></td><td><a href="utiliser-lapi-decoupage-administratif.md">utiliser-lapi-decoupage-administratif.md</a></td></tr><tr><td><strong>Utiliser les tuiles vectorielles</strong></td><td><a href="utiliser-les-tuiles-vectorielles.md">utiliser-les-tuiles-vectorielles.md</a></td></tr></tbody></table>
