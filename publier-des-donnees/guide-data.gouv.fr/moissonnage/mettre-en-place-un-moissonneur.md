# Mettre en place un moissonneur

## Comment mettre en place un moissonneur ?

Le principe du moissonnage sur data.gouv.fr se décompose en plusieurs étapes :

1. Vous créez un moissonneur sur data.gouv.fr afin que data.gouv.fr suive l’activité de votre plateforme ;
2. Vous publiez des données sur votre plateforme open data ;
3. Vous demandez la validation de votre moissonneur sur [le support data.gouv.fr](https://support.data.gouv.fr/collectivite-territoriale/referencement/moissonnage#support-tree) ;
4. La configuration du moissonneur est validée par l’équipe en charge de data.gouv.fr ;
5. Le moissonneur de data.gouv.fr vient automatiquement récupérer les données de votre plateforme ;
6. Les données de votre plateforme sont référencées et visibles sur data.gouv.fr. :tada:

{% hint style="info" %}
Si vous souhaitez tester la mise en place d'un moissonneur et observer le résultat du moissonnage avant une mise en production sur [data.gouv.fr](https://www.data.gouv.fr/), vous pouvez le créer sur la plateforme de démo [https://demo.data.gouv.fr/](https://demo.data.gouv.fr/fr/) pour effectuer vos tests dans un premier temps. L'ensemble des étapes sont les mêmes que celles décrites sur cette page.
{% endhint %}

## Créer un moissonneur <a href="#creer-un-moissonneur" id="creer-un-moissonneur"></a>

La création d’un moissonneur sur data.gouv.fr nécessite la création d’un compte gratuit.

Pour créer un nouveau moissonneur :

1. [Connectez-vous à votre compte](https://www.data.gouv.fr/fr/login) ;
2. Rendez-vous sur [votre tableau de bord](https://www.data.gouv.fr/fr/admin/), en cliquant sur **Administration** en haut à droite de votre écran ;
3. Cliquez sur l’icône en forme de plus (`+`) qui se trouve à gauche de votre avatar ;
4. Cliquez sur **Un moissonneur**.

À partir de là, la création du moissonneur se déroule en 3 étapes.

## 1. Définir qui publie les données moissonnées <a href="#1-definir-qui-publie-les-donnees-moissonnees" id="1-definir-qui-publie-les-donnees-moissonnees"></a>

Une fois moissonnées, c’est-à-dire récupérées sur votre plateforme, vos données sont publiées sur data.gouv.fr. L’étape 1 vous permet de choisir le compte qui sera associé à la publication sur data.gouv.fr des données moissonnées sur votre site.

Il peut s’agir de :

* votre propre compte, pour une publication à titre individuel, sous votre propre nom ;
* le compte d’une organisation dont vous êtes membre, pour une publication à titre collectif.

Si vous êtes membre d’une organisation, nous vous conseillons de publier vos jeux de données en son nom. Une fois votre choix effectué, cliquez sur le bouton **Suivant** pour accéder à l’étape 2.

## 2. Configurer le moissonneur <a href="#2-configurer-le-moissonneur" id="2-configurer-le-moissonneur"></a>

L’étape 2 vous permet de configurer votre moissonneur. Cette étape est importante pour que les données récupérées par data.gouv.fr soient aussi complètes que celles publiées sur votre plateforme à l’origine.

### **Nom**

Donnez un nom à votre moissonneur. Il s’agit d’une référence interne, qui vous permet de vous y retrouver si vous créez plusieurs moissonneurs. Le nom de votre moissonneur ne sera pas public.

* **Mauvais nom** : Moissonneur de mon portail
* **Bon nom** : Plateforme open data Grand Lyon

Le nom du moissonneur est obligatoire.

### Description <a href="#description" id="description"></a>

Vous pouvez ajouter des précisions sur votre moissonneur dans le champ description. Là encore, il s’agit d’une référence interne qui n’a de valeur que pour vous.

La description est facultative.

### URL <a href="#url" id="url"></a>

Saisissez ici l’URL du portail à moissonner. Il s’agit généralement de l’URL de la page d’accueil de votre portail d’open data. L’URL permet au moissonneur de parcourir et récupérer tous vos jeux de données.

* **Mauvaise source** : `data.angers.fr`
* **Bonne source** : `https://data.angers.fr`

L’URL est obligatoire.

### Implémentation <a href="#implementation" id="implementation"></a>

Choisissez ici le format des métadonnées associées aux jeux de données publiés sur votre plateforme. Ce format permet au moissonneur de savoir comment lire et interpréter vos métadonnées, pour bien les retranscrire sur data.gouv.fr.

Certaines implémentations permettent d’ajouter des filtres, dans le but d’inclure ou d’exclure certains jeux de données du moissonnage. Consultez [la section dédiée à votre implémentation dans la documentation de moissonnage](les-differents-types-de-moissonneurs.md).

Le type d’implémentation est obligatoire.

### Actif <a href="#actif" id="actif"></a>

Cochez la case pour que votre moissonneur se mette au travail dès qu’il aura été validé par l’équipe en charge de data.gouv.fr. Laissez-la décochée pour activer votre moissonneur à la main.

Ce champ est obligatoire.

Une fois tous les champs obligatoires remplis, cliquez sur le bouton **Suivant** pour terminer la création de votre moissonneur.

## 3. Demander la validation du moissonneur <a href="#3-demander-la-validation-du-moissonneur" id="3-demander-la-validation-du-moissonneur"></a>

Une fois votre moissonneur configuré, demandez validation de votre moissonneur sur [le support data.gouv.fr](https://support.data.gouv.fr/collectivite-territoriale/referencement/moissonnage#support-tree). Il va être examiné par l’équipe en charge de data.gouv.fr, pour vérifier qu’il est bien réglé. Si c’est le cas, le moissonneur sera validé et vous recevrez une notification.

De votre côté, vous pouvez vérifier que votre moissonneur moissonne correctement votre site. Pour ce faire :

1. Cliquez sur le bouton **Voir dans l’administration** une fois votre moissonneur créé ;
2. Cliquez sur le bouton **Prévisualiser** ;
3. Vérifiez que le moissonneur récupère bien des jeux de données.

Tant que votre moissonneur n’est pas validé, il ne référence aucun jeu de données sur data.gouv.fr.
