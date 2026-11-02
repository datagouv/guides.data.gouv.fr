---
icon: map
---

# Synchronisation avec cartes.gouv.fr

Transformez un fichier géographique de votre jeu de données en services cartographiques (WFS, WMS, tuiles vectorielles...) sur [cartes.gouv.fr](https://cartes.gouv.fr), puis retrouvez-les automatiquement sur [data.gouv.fr](https://data.gouv.fr).

{% hint style="warning" %}
**Cette fonctionnalité est une première version.** Elle comporte plusieurs limitations, listées en bas de page, et va évoluer. N'hésitez pas à nous faire part de vos retours via le [support data.gouv.fr](https://support.data.gouv.fr/).
{% endhint %}

### Avant de commencer

Vous avez besoin :

* d'un fichier au format **GeoPackage (`.gpkg`)** parmi les ressources de votre jeu de données (taille maximale : 1 Go) ;
* d'un compte sur cartes.gouv.fr, rattaché à un **espace de travail** (entrepôt) disposant des droits de dépôt, de traitement et de diffusion ;
* d'être autorisé à modifier le jeu de données sur [data.gouv.fr](https://data.gouv.fr).

### Envoyer un fichier vers cartes.gouv.fr

**1. Ouvrir l'onglet cartes.gouv.fr du jeu de données**

Depuis l'espace d'administration de votre jeu de données, ouvrez l'onglet dédié à cartes.gouv.fr.

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.24.51.png" alt=""><figcaption><p>Onglet cartes.gouv.fr sur l'administration d'un jeu de données</p></figcaption></figure>

**2. Connecter votre compte cartes.gouv.fr**

Au premier usage, data.gouv.fr vous redirige vers la Géoplateforme pour vous identifier et autoriser l'accès. Les envois sont toujours réalisés **en votre nom**, avec vos droits sur la Géoplateforme. Vous pouvez vous déconnecter à tout moment.

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.25.47.png" alt=""><figcaption><p>Bandeau avant connexion</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.26.19 (1).png" alt=""><figcaption><p>Bandeau après connexion</p></figcaption></figure>

**3. Choisir l'espace de travail**

Choisissez l'entrepôt cartes.gouv.fr dans lequel les données seront déposées. Ce choix est **définitif pour le jeu de données** : tous les envois suivants iront dans le même espace.

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.28.49.png" alt=""><figcaption><p>Sélection d'un entrepôt</p></figcaption></figure>

**4. Lancer l'envoi**

Lancez l'envoi du fichier GeoPackage. Le traitement dure de quelques instants à plusieurs dizaines de minutes selon la taille du fichier, vous pouvez quitter la page. Le statut de l'envoi (en cours, terminé, en erreur) est affiché sur la page. Si l'envoi est réussi, vous recevrez aussi un email de la part de cartes.gouv.fr.

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.29.35.png" alt=""><figcaption><p>Fichier avant envoi</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.29.44 (1).png" alt=""><figcaption><p>Fichier en cours d'envoi</p></figcaption></figure>

Une fois l'envoi terminé, un lien vers la **fiche de données** correspondante sur cartes.gouv.fr est disponible.

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.36.53.png" alt=""><figcaption><p>Fichier synchronisé et lien vers la fiche sur cartes.gouv.fr</p></figcaption></figure>

{% hint style="info" %}
Les métadonnées du jeu de données (titre, description, mots-clés, contact) sont envoyées en même temps, au format ISO 19115. Elles sont générées à partir de la fiche data.gouv.fr : pensez à les renseigner soigneusement. Les adresses e-mail de contact sont reprises d'un point de contact du jeu de données, s'il en existe un. La thématique ISO 19115 est déduite des mots-clés lorsque c'est possible.
{% endhint %}

### Récupérer les services créés sur cartes.gouv.fr

Une fois vos données envoyées, vous pouvez créer sur cartes.gouv.fr des services de diffusion (WFS, WMS, WMTS, tuiles vectorielles...) à partir de celles-ci. N'hésitez à vous référer à la [documentation de cartes.gouv.fr relative aux services](https://cartes.gouv.fr/aide/fr/guides-producteur/publier-des-donnees-via-cartes-gouv/choisir-son-flux/).

Ces services peuvent ensuite être ajoutés comme ressources de votre jeu de données sur data.gouv.fr : depuis la page cartes.gouv.fr du jeu de données, lancez la **récupération des services**. Les ressources correspondantes sont créées, mises à jour ou supprimées pour refléter l'état actuel des services sur cartes.gouv.fr.

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.36.58.png" alt=""><figcaption><p>Bouton "Récupérer les services"</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.55.10.png" alt=""><figcaption><p>Liste des services synchronisés</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Capture d’écran 2026-11-02 à 16.55.49.png" alt=""><figcaption><p>Vue "front" data.gouv.fr avec le fichier envoyé et le service synchronisé</p></figcaption></figure>

### Limites actuelles

* Seul le format **GeoPackage** est, pour l'instant, pris en charge.
* **Un fichier ne peut être envoyé qu'une seule fois.** De plus, si vous modifiez la ressource sur data.gouv.fr, la mise à jour n'est pas répercutée sur cartes.gouv.fr.&#x20;
* Un jeu de données ne peut être associé qu'à **un seul entrepôt cartes.gouv.fr**.
* L'envoi et la récupération des services sont **déclenchés manuellement** : il n'y a pas de synchronisation automatique.
* La thématique ISO 19115 est déduite des mots-clés et peut être absente ou imprécise.

### Contraintes cartes.gouv.fr

Le fichier GeoPackage doit respecter les contraintes de cartes.gouv.fr, sans quoi il risque d'être refusé :

* les noms de tables ne peuvent contenir que des lettres sans accent, des chiffres, des espaces et des tirets bas (`_`), et ne doivent pas commencer par un chiffre ou un espace ;
* toutes les couches doivent utiliser le même système de projection.

L'interface data.gouv.fr affiche l'erreur renvoyée par cartes.gouv.fr, le cas échéant.&#x20;
