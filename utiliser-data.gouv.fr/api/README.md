# API

{% hint style="info" %}
**Qu’est-ce qu’une API ?**

Une API est une interface, un contrat passé entre deux systèmes informatiques pour leur permettre de communiquer. Cette solution informatique permet d’automatiser des tâches depuis votre ordinateur ou vos serveurs.
{% endhint %}

A partir de l’API de data.gouv.fr, vous pouvez réaliser les mêmes actions que sur la plateforme :

* **Créer un jeu de données au nom de votre compte utilisateur ou au nom de votre organisation** ;
* **Décrire votre jeu de données et les ressources associées** ;
* **Ajouter ou supprimer une ressource ou un jeu de données**.

L’API de data.gouv.fr propose également des fonctionnalité complémentaires à la publication de jeux de données comme la possibilité de récupérer les métadonnées des jeux de données ou de fichiers ou encore d'accéder au contenu des fichiers d’un jeu de données.

{% hint style="info" %}
#### Quand utiliser l’API de data.gouv.fr ? <a href="#quand-utiliser-l-api-de-data-gouv-fr" id="quand-utiliser-l-api-de-data-gouv-fr"></a>

À la différence du mode de mise à disposition directe des données sur data.gouv.fr, l’utilisation de l’API permet de réaliser des actions de manière automatisée depuis votre ordinateur ou vos serveurs. \
Il est par conséquent conseillé d’utiliser une API lorsque la fréquence de publication d’un jeu de données est régulière.\
Voir la différence entre [API et moissonnage](../../publier-des-donnees/guide-data.gouv.fr/publier-et-gerer-un-jeu-de-donnees/publier-un-jeu-de-donnees.md).&#x20;
{% endhint %}

L’utilisation de l’API de data.gouv.fr se fait par le point d’entrée racine de l’API. Afin de pouvoir exécuter des opérations d’écriture, il est nécessaire d’obtenir une clé API. Cette clé est accessible depuis les paramètres de votre profil administrateur.

![Générer une clé d'API](https://guides.etalab.gouv.fr/assets/img/cle\_api.f5378a97.jpg)

Les appels à l’API sont soumis aux mêmes permissions que l’interface web. Par exemple, si vous souhaitez publier ou modifier un jeu de données au nom d’une organisation, vous devez appartenir à cette organisation.
