# Les schémas de données

{% hint style="info" %}
**Lexique : Schéma de données**

Les schémas de données (ou simplement schémas) permettent de décrire la structure d'un fichier d'un jeu de données.&#x20;

Ils indiquent clairement quels sont les différents champs, comment sont représentées les données, quelles sont les valeurs possibles, leur format, etc.
{% endhint %}

{% hint style="info" %}
Ce guide résulte d'une co-rédaction entre les équipes d'[Etalab](https://www.etalab.gouv.fr/) et d'[OpenDataFrance](https://www.opendatafrance.net/).\
\
Il s'inspire du contenu rédigé par de nombreux partenaires, listés par ordre alphabétique :

* [Charles Nepote](https://twitter.com/charlesnepote)
* [Datactivist](https://datactivist.coop/)
* [La FING](https://fing.org/)
* [OpenDataFrance](http://www.opendatafrance.net/)

Merci à eux !
{% endhint %}

## Pourquoi créer des données en conformité avec un schéma ?

La création de données en conformité avec un schéma de données existant apporte plusieurs bénéfices :

* Les données créées peuvent être facilement croisées avec d’autres données conformes au schéma de données utilisé ;
* L’interopérabilité des données et leur croisement est simplifié ;
* Si le jeu de données que vous créez est une agrégation de plusieurs fichiers produits par différents acteurs, la formalisation et le partage d’un schéma de données facilite le travail d’agrégation des données - ce schéma devient donc un standard pour votre communauté ;
* La formalisation d’un schéma de données assure une pérennité des fichiers dans le temps ;
* La documentation d’un schéma de données existant est déjà rédigée et accessible.
* La présence d'un schéma de données existant peut faciliter l'ouverture des données, les producteurs ayant directement une procédure claire à suivre.

Il est également possible de vérifier la conformité d'un fichier vis-à-vis d'un schéma de données, ce qui permet de valider un premier niveau de qualité. Par ailleurs, il est aussi possible de générer des jeux de données d’exemple ou de proposer des formulaires de saisie standardisés.
