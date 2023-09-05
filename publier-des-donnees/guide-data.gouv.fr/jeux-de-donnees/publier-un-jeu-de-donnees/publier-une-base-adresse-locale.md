# Publier une Base Adresse Locale

{% hint style="info" %}
**Lexique : Base Adresse Locale**\
Fichier géré par une collectivité locale (habituellement une commune ou un EPCI) et contenant toutes ses adresses géolocalisées. Une Base Adresse Locale publiée et à jour garantit une meilleure prise en compte des adresses dans les différents systèmes d’information des acteurs, qu’ils soient privés ou publics.\
\
Depuis 2019, les Bases Adresses Locales sont prioritaires dans la Base Adresse Nationale : une commune qui publie sa Base Adresse Locale devient la seule source d'adresses sur son territoire.
{% endhint %}

## Marche à suivre

Deux méthodes de publication d'une Base Adresse Locale pour intégration dans la [Base Adresse Nationale](https://www.data.gouv.fr/fr/datasets/base-adresse-nationale/) sont possibles sur data.gouv.fr :

{% tabs %}
{% tab title="Publication manuelle" %}
## Publication manuelle

Pour publier manuellement une Base Adresse Locale sur data.gouv.fr :&#x20;

1. **Vérifiez vos fichiers .csv dans le** [**validateur**](https://adresse.data.gouv.fr/bases-locales/validateur) pour vous assurer qu'ils sont conformes et qu'ils pourront être intégrés à la Base Adresse Nationale ;

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2023-09-04 à 18.39.07.png" alt=""><figcaption><p>Validateur BAL</p></figcaption></figure>

2. Suivez ensuite la [procédure standard de publication de données sur data.gouv.fr](./#directement-sur-data.gouv.fr), en veillant à **ajouter le mot clé "base-adresse-locale".**
{% endtab %}

{% tab title="Moissonnage" %}
## Moissonnage

Pour publier une Base Adresse Locale sur data.gouv.fr par moissonnage, les étapes à suivre sont les suivantes :&#x20;

* [Demandez à data.gouv.fr de moissonner votre site](../../moissonnage/mettre-en-place-un-moissonneur.md), **en veillant à ajouter le mot clé "base-adresse-locale"** ;
* Avant d'automatiser, **vérifiez votre fichier .csv dans le** [**validateur**](https://adresse.data.gouv.fr/bases-locales/validateur) pour vous assurer qu'il est conforme et qu'il pourra être intégré à la Base Adresse Nationale.

<figure><img src="../../../../.gitbook/assets/Capture d’écran 2023-09-04 à 18.39.07 (1).png" alt=""><figcaption><p>Validateur BAL</p></figcaption></figure>

La [documentation en ligne](https://github.com/BaseAdresseNationale/moissonneur-bal/wiki/Fonctionnement-du-moissonneur-bal) précise toutes les spécificités de cette méthode de publication.
{% endtab %}
{% endtabs %}

## Autres méthodes de publication

D'autres méthodes permettent de publier une Base Adresse Locale pour intégration dans la [Base Adresse Nationale](https://www.data.gouv.fr/fr/datasets/base-adresse-nationale/).

**Il est notamment recommandé d'utiliser** [**l'éditeur "Mes Adresses"**](https://mes-adresses.data.gouv.fr/)**.** "Mes Adresses" permet de gérer en ligne (gratuitement), sur un simple navigateur web, une Base Adresse Locale communale et de transmettre des modifications en temps réel à la Base Adresse Nationale.&#x20;

Elle ne requiert :&#x20;

* Aucune gestion de fichier
* Aucune compétence technique

<figure><img src="../../../../.gitbook/assets/Sep-04-2023 18-35-27.gif" alt=""><figcaption><p>Interface de l'éditeur "Mes Adresses"</p></figcaption></figure>

Si vous utilisez votre propre outil, il est également possible de publier via :&#x20;

* Un formulaire de dépôt sur [adresse.data.gouv.fr](https://adresse.data.gouv.fr/) ;
* L'API de dépôt.&#x20;

Pour en savoir plus, nous vous invitons à consulter [la documentation](https://doc.adresse.data.gouv.fr/mettre-a-jour-sa-base-adresse-locale/publier-une-base-adresse-locale) proposée par adresse.data.gouv.fr.
