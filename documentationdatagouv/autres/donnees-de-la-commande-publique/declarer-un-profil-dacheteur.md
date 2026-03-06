---
description: >-
  Déclarer un profil d’acheteur sur data.gouv.fr avec le bon format de fichier
  et les étapes de dépôt.
---

# Déclarer un profil d’acheteur

Un profil d’acheteur peut être déclaré sur data.gouv.fr par l’acheteur ou par une personne habilitée.

L’éditeur du profil d’acheteur peut aussi effectuer cette déclaration. Cela simplifie la démarche pour les acheteurs publics.

Si l’éditeur ne peut pas la prendre en charge, l’administrateur du profil d’acheteur ou l’acheteur peut la faire directement.

### Qui doit déclarer

La déclaration peut être faite par :

* l’acheteur ;
* une personne habilitée par l’acheteur ;
* l’éditeur du profil d’acheteur.

### Préparer le fichier de déclaration

Les éditeurs de profils d’acheteurs doivent créer un fichier CSV.

Ce fichier doit contenir les colonnes suivantes :

* `siretAcheteur` : le SIRET de l’acheteur ;
* `urlProfilAcheteur` : l’URL du profil d’acheteur ;
* `urlDCAT` : l’URL du catalogue DCAT qui référence les données ;
* `coordonnees` : les coordonnées du ou des acheteurs concernés.

Un modèle de fichier CSV est disponible sur [data.gouv.fr](https://www.data.gouv.fr/fr/datasets/structure-du-fichier-de-declaration-de-profil-dacheteur/).

{% hint style="info" %}
Ajoutez le tag `decp` au jeu de données. Il permet de centraliser les déclarations liées aux données essentielles de la commande publique.
{% endhint %}

### Déposer le fichier sur data.gouv.fr

{% stepper %}
{% step %}
### Créer un compte individuel

Créez un compte sur [data.gouv.fr](https://www.data.gouv.fr/fr/register).
{% endstep %}

{% step %}
### Valider le compte et créer une organisation

Après validation du compte par e-mail, créez une organisation correspondant à votre profil d’acheteur depuis [l’espace d’administration](https://www.data.gouv.fr/fr/admin/organization/new/).
{% endstep %}

{% step %}
### Créer un jeu de données

Créez un jeu de données depuis [l’espace de publication](https://www.data.gouv.fr/fr/admin/dataset/new/).

À l’étape **Choisissez qui publie**, sélectionnez l’organisation créée à l’étape précédente.
{% endstep %}

{% step %}
### Décrire le jeu de données

Renseignez un titre.

Ajoutez, si besoin, d’autres métadonnées comme la couverture spatiale ou la fréquence de mise à jour.

Ajoutez le tag `decp`.
{% endstep %}

{% step %}
### Ajouter la ressource CSV

À l’étape **Ajouter vos premières ressources**, téléversez le fichier CSV.
{% endstep %}
{% endstepper %}

### Bonnes pratiques

* Vérifiez que chaque SIRET est valide ;
* utilisez une URL de profil d’acheteur accessible publiquement ;
* vérifiez que l’URL `urlDCAT` pointe bien vers un catalogue exploitable ;
* gardez des coordonnées à jour pour faciliter les échanges.
