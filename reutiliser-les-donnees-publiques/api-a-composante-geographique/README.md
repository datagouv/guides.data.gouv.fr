# API à composante géographique

## Que contient ce guide ? <a href="#que-contient-ce-guide" id="que-contient-ce-guide"></a>

Ce guide vise à vous accompagner dans l'usage des API géographiques principalement opérées par Etalab, la [Base Adresse Nationale étant désormais portée par l'IGN](https://www.numerique.gouv.fr/espace-presse/la-base-adresse-nationale-ban-franchit-de-nouvelles-etapes-en-poursuivant-son-action-au-sein-de-lign/).

{% hint style="info" %}
[API Adresse (Base Adresse Nationale - BAN)](https://guides.etalab.gouv.fr/apis-geo/1-api-adresse)

L'API Adresse permet d'interroger la Base Adresse Nationale, base de données de l’intégralité des adresses du territoire français. En intégrant l'API dans votre système d'information, vous pouvez facilement rechercher une adresse et notamment :

* faire de l'autocomplétion et de la vérification d'adresse ;
* géolocaliser une adresse sur une carte ;
* faire une recherche géographique inversée (trouver la rue la plus proche de coordonnées géographiques).
{% endhint %}

{% hint style="info" %}
[API Découpage Administratif - (API Geo)](https://guides.etalab.gouv.fr/apis-geo/2-api-decoupage-administratif)

L'API Découpage Administratif permet d'interroger les référentiels géographiques plus facilement. En intégrant l'API dans votre système d'information, vous pouvez notamment :

* rechercher une commune par nom, code postal ou coordonnées géographiques
* rechercher un département par son nom
* rechercher une région par son nom
{% endhint %}

{% hint style="info" %}
[Les tuiles vectorielles openmaptiles.geo.data.gouv.fr](https://guides.etalab.gouv.fr/apis-geo/3-tuiles-vecteur)

Cette API permet de mettre à disposition des tuiles vectorielles qui sont affichables sur des cartes géographiques interactives. Elles servent principalement à afficher des fonds de plan mais aussi les contours cadastrales et les limites administratives en France. Cela permet de vous affranchir d'APIs cartographiques comme Google Maps.
{% endhint %}

### À quoi sert ce guide ? <a href="#a-quoi-sert-ce-guide" id="a-quoi-sert-ce-guide"></a>

Ce guide propose d'explorer des cas pratiques d'utilisations des API géographiques mises à votre disposition pour vous accompagner dans leurs utilisations, que vous soyez en train de construire une carte ou que vous souhaitiez récupérer des données géographiques.

### À qui s'adresse ce guide ? <a href="#a-qui-s-adresse-ce-guide" id="a-qui-s-adresse-ce-guide"></a>

Ce guide s'adresse à plusieurs types de profils:

* Néophytes dans l'utilisation des APIs
* Intégrateur web
* Spécialiste du secteur géospatial

### Recommandations logiciels <a href="#recommandations-logiciels" id="recommandations-logiciels"></a>

Il est recommandé d'avoir un navigateur web en ayant installé [l'extension JSONView](https://jsonview.com/) pour faciliter la compréhension des retours JSON.

Vous pouvez aussi installer un éditeur de texte plus agréable à utiliser que le Bloc-Notes/Notepad par défaut si vous êtes sous Windows. Il vous permettra en particulier lorsque vous faites des tests sur les URLs de les modifier avant de les copier dans la barre d'adresse de votre navigateur. Il peut s'agit de [Notepad++](https://notepad-plus-plus.org/downloads/) si vous êtes sous Windows ou bien de [Microsoft Visual Studio Code](https://code.visualstudio.com/) quel que soit votre système d'exploitation. Une liste plus complète d'éditeurs de texte est disponible [ici](https://fr.wikipedia.org/wiki/%C3%89diteur\_de\_texte#%C3%89diteurs\_de\_texte\_couramment\_utilis%C3%A9s).&#x20;

### Sommaire <a href="#sommaire" id="sommaire"></a>

Ce guide est composé de trois parties:

1. [Utiliser l'API adresse pour récupérer les coordonnées depuis une liste d'adresse ou récupérer les adresses depuis des coordonnées](https://guides.etalab.gouv.fr/apis-geo/1-api-adresse.html)
2. [Utiliser l'API découpage administratif](https://guides.etalab.gouv.fr/apis-geo/2-api-decoupage-administratif.html)
3. [Consommer des tuiles vectorielles](https://guides.etalab.gouv.fr/apis-geo/3-tuiles-vecteur.html)

### Comment contribuer ? <a href="#comment-contribuer" id="comment-contribuer"></a>

Ce document est un outil évolutif et ouvert. Vous pouvez contribuer à l'améliorer en proposant une modification sur [GitHub](https://github.com/etalab/guides.etalab.gouv.fr/edit/master/apis-geo/) ou en [contactant directement](mailto:geo@data.gouv.fr) l'équipe Géo d'Etalab
