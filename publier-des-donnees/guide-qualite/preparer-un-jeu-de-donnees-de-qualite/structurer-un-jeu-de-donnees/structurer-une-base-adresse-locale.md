# Structurer une Base Adresse Locale

{% hint style="info" %}
**Lexique : Base Adresse Locale**\
Fichier géré par une collectivité locale (habituellement une commune ou un EPCI) et contenant toutes ses adresses géolocalisées. Elle respecte le schéma Base Adresse Locale et une gouvernance qui prévoit que la commune est au centre du dispositif. Cette base est publiée sous sa responsabilité, ce qui lui confère un caractère officiel.\
\
Depuis 2019, les Bases Adresses Locales sont prioritaires dans la Base Adresse Nationale : une commune qui publie sa Base Adresse Locale devient la seule source d'adresses sur son territoire.\
\

{% endhint %}

<figure><img src="../../../../.gitbook/assets/schema-donnees-ban.681a4c32.svg" alt=""><figcaption><p>Schéma de constitution de la BAN</p></figcaption></figure>

## Respecter le schéma de données

Les Bases Adresses Locales correspondent à un [schéma de données établi](https://schema.data.gouv.fr/etalab/schema-bal/). Il est conseillé de le suivre au plus près.&#x20;

Ce format garantit une intégration réussie des Bases Adresses Locales dans la Base Adresse Nationale.

Une seule Base Adresse Locale est publiée par commune.

Il est important de veiller à la mise à jour régulière des adresses.

{% hint style="success" %}
Toute commune peut vérifier que son fichier d'adresses est conforme au schéma et qu'il pourra être intégré à la Base Adresse Nationale grâce au [validateur](https://adresse.data.gouv.fr/bases-locales/validateur) proposé par adresse.data.gouv.fr.\
\
Il suffit de glisser le fichier contenant toutes les adresses au format .csv pour obtenir la liste des erreurs à corriger impérativement (en rouge) et des anomalies (problèmes non bloquants mais réduisant la qualité des adresses et leur utilisation).
{% endhint %}

{% hint style="info" %}
Un outil est mis à disposition pour permettre à toutes les communes de gérer directement leurs adresses/bases adresses locales en respectant les normes sans besoin de compétences techniques : [**l'éditeur "Mes Adresses"**](https://mes-adresses.data.gouv.fr/). Il permet à la fois de publier et de modifier sa Base Adresse Locale. La transmission des adresses à la Base Adresse Nationale se fait en temps réel.&#x20;

\
Celui-ci est gratuit, open source et simple d'utilisation.&#x20;
{% endhint %}

## Suivre les bonnes pratiques&#x20;

* [ ] **voie\_nom, numero, suffixe** : le nom de la voie et de son complément sont rédigés en toutes lettres, **en minuscules accentuées**, la première lettre de la voie et du nom seulement étant écrites en majuscules. Le complément est réservé aux hameaux et lieux-dits historiques. Il est conseillé de **limiter le champ suffixe** aux indices de répétition du type bis, ter.&#x20;
* [ ] **cad\_parcelles** : la commune délivrant un certificat de numérotage associe une numérotation à une parcelle. Le registre de filiation parcellaire de DGFiP, disponible en open data, permet de connaître les parcelles associées à une adresse.
* [ ] **Voies sans adresse** : le numéro attendu pour les voies sans adresse est 99999.

Pour aller plus loin, [un guide des bonnes pratiques de l'adressage](https://guide-bonnes-pratiques.adresse.data.gouv.fr/) ("Comment constituer et établir une adresse ?") est disponible. Il détaille les règles et les normes en vigueur.
