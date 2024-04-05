# Moissonnage des plateformes géographiques

Il est possible de faire moissonner les données de sa plateforme géographique par [data.gouv.fr](https://www.data.gouv.fr/).\


{% hint style="info" %}
**Qu'est-ce que le moissonnage sur data.gouv.fr ?**\
Le moissonnage est un mécanisme permettant de collecter les métadonnées sur un catalogue distant et de les stocker sur une autre plateforme afin de proposer un second point d’accès aux données.
{% endhint %}

{% hint style="warning" %}
Historiquement, le moissonnage des métadonnées géographiques se faisait via [geo.data.gouv.fr](https://geo.data.gouv.fr/). La plateforme est aujourd'hui éteinte. Vous retrouverez plus d’informations à propos de [l'extinction de geo.data.gouv.fr ici](https://www.data.gouv.fr/fr/posts/extinction-de-geo-data-gouv-fr/).
{% endhint %}

1. La plateforme [data.gouv.fr](https://www.data.gouv.fr/fr/posts/extinction-de-geo-data-gouv-fr/www.data.gouv.fr) a vocation à accueillir l’ensemble des données géographiques en open data.
2. Le moissonnage direct des plateformes géographiques par [data.gouv.fr](https://www.data.gouv.fr/fr/posts/extinction-de-geo-data-gouv-fr/www.data.gouv.fr) est maintenant possible et n’oblige plus à passer par une plateforme intermédiaire.
3. Des travaux sont en cours pour moissonner automatiquement les données mises à disposition  [catalogue GeoIDE](http://catalogue.geo-ide.developpement-durable.gouv.fr/catalogue/srv/fre/catalog.search#/home) au nom des différentes organisations productrices.
4. Le rôle de la plateforme Geocatalogue gérée par le BRGM (Service Géologique National) est concentré sur le périmètre des données [INSPIRE](https://knowledge-base.inspire.ec.europa.eu/index\_en) pour le rapportage au niveau européen.
5. Un double moissonnage est possible pour que les données INSPIRE soient référencées à la fois sur le Geocatalogue et data.gouv.fr. Cela nécessite néanmoins de créer deux points de moissonnage distincts à date.
6. Des moyens sont mis en œuvre de manière continue par les équipe de [data.gouv.fr](https://www.data.gouv.fr/fr/posts/extinction-de-geo-data-gouv-fr/www.data.gouv.fr) et l'équipe Écosphères du MTECT (Ministère de la Transistion Ecologique et de la Cohésion des Territoires) pour tendre vers la complétude du moissonnage des métadonnées des catalogues des plateformes géographiques.

### Mettre en place un moissonneur géographique

Le moissonnage des plateformes géographiques se fait avec transformation des fiches ISO-19139 en [DCAT](les-differents-types-de-moissonneurs.md#dcat), l'un des vocabulaires de moissonnage supportés par data.gouv.fr.

Les fiches moissonnées étant associées à l'organisation qui a configuré le moissonneur sur [data.gouv.fr](https://www.data.gouv.fr/), il est important de préparer les points de moissonnage pour que les fiches retournées correspondent à celles de l'organisation cible.

Dans le cas d'une plateforme référençant des données de différentes organisations, il est donc nécessaire de créer des CSW virtuels (filtrés par organisation cible).

[Une documentation est disponible sur GeoNetwork](https://geonetwork-opensource.org/manuals/3.12.x/fra/users/administrator-guide/configuring-the-catalog/portal-configuration.html#configuring-a-sub-portal) pour configurer des sous-portails.

Une documentation est disponible sur les étapes générales de configuration d'un point de moissonnage dans [cette page dédiée](mettre-en-place-un-moissonneur.md). Il faut choisir le moissonneur `csw-iso-19139` au niveau de l'implémentation.

{% hint style="info" %}
Toutes les métadonnées ne sont pas encore correctement transformés par ce convertisseur ISO-19139 vers DCAT. En lien avec les équipes du projet Ecosphères, nous travaillons à augmenter régulièrement le périmètre des métadonnées moissonnées.
{% endhint %}

### Configurer un portail GeoNetwork

data.gouv.fr peut moissonner un endpoint CSW avec sortie ISO-19139 en appliquant par la suite [une transformation en DCAT](https://github.com/SEMICeu/iso-19139-to-dcat-ap). Ce moissonnage est fonctionnel sur les différentes versions de GeoNetwork.

Une requête POST est effectuée par le moissonneur sur le endpoint CSW renseigné (ex [https://geosas.fr/geonetwork/srv/fre/csw](https://geosas.fr/geonetwork/srv/fre/csw)) avec le contenu suivant :

```
<csw:GetRecords xmlns:csw="http://www.opengis.net/cat/csw/2.0.2"
                xmlns:gmd="http://www.isotc211.org/2005/gmd"
                service="CSW" version="2.0.2" resultType="results"
                startPosition="1" maxPosition="10"
                outputSchema="http://www.isotc211.org/2005/gmd">
      <csw:Query typeNames="csw:Record">
        <csw:ElementSetName>full</csw:ElementSetName>
        <csw:Constraint version="1.1.0">
            <ogc:Filter xmlns:ogc="http://www.opengis.net/ogc">
                <ogc:PropertyIsEqualTo>
                    <ogc:PropertyName>dc:type</ogc:PropertyName>
                    <ogc:Literal>dataset</ogc:Literal>
                </ogc:PropertyIsEqualTo>
            </ogc:Filter>
        </csw:Constraint>
    </csw:Query>
</csw:GetRecords>
```

#### Moissonnage historique

{% hint style="warning" %}
Ces solutions de moissonnage ne sont plus recommandées dans le cas général.
{% endhint %}

En version 2 ou 3, il existait un endpoint DCAT alternatif au endpoint CSW habituellement utilisé comme [documenté sur la doc Geonetwork officielle](https://geonetwork-opensource.org/manuals/3.12.x/en/api/rdf-dcat.html).

Ainsi [https://geosas.fr/geonetwork/srv/fre/csw](https://geosas.fr/geonetwork/srv/fre/csw) devenait [https://geosas.fr/geonetwork/srv/fre/rdf.search](https://geosas.fr/geonetwork/srv/fre/rdf.search) par exemple. Le moissonneur utilisé était donc l'implémentation `dcat` simple.

En version 4, il est possible de récupérer le contenu [CSW avec format DCAT en sortie](https://github.com/geonetwork/core-geonetwork/wiki/DCAT-enhancements). La conversion des fiches par GeoNetwork est cependant moins satisfaisante que par récupération du contenu en ISO-19139 et conversion à posteriori.
