# Comprendre la récupération des métadonnées via geo.data.gouv.fr

{% hint style="warning" %}
[geo.data.gouv.fr](https://geo.data.gouv.fr/) n’est plus activement maintenu.\
Plus d’informations à propos [de l’extinction de geo.data.gouv.fr sont disponibles ici](https://www.data.gouv.fr/fr/posts/extinction-de-geo-data-gouv-fr/).
{% endhint %}

En plus du moissonnage et de l’utilisation de l’API, il existait un autre moyen automatisé de récupération des métadonnées sur data.gouv.fr : [geo.data.gouv.fr](https://geo.data.gouv.fr/), anciennement inspire.data.gouv.fr. Ce site pivot permettait de récupérer les métadonnées de jeux de données exposées selon [la directive européenne Inspire](https://inspire.ec.europa.eu/) (obligation légale de publication des metadonnées geographiques selon le modèle de données **ISO 19115**, au format de données **ISO 19139**).

**Du fait de l’extinction de la plateforme geo.data.gouv.fr, vous pouvez au choix** :

* attendre que le Geocatalogue publie directement des flux DCAT depuis vos flux Inspire ;&#x20;
* si vous utilisez Geonetwork, utilisez [son endpoint DCAT alternatif](https://doc.data.gouv.fr/moissonnage/dcat/#geonetwork) ;&#x20;
* utiliser [le moissonnage DCAT](https://doc.data.gouv.fr/moissonnage/dcat) avec un grand nombre de logiciels compatibles ou avec un flux à façon ;&#x20;
* enfin, nous supportons également le moissonnage des plateformes [CKAN](https://doc.data.gouv.fr/moissonnage/ckan) et [OpenDataSoft](https://doc.data.gouv.fr/moissonnage/ods).
