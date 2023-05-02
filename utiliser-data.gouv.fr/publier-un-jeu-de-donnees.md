# Jeux de données

{% hint style="info" %}
**Qu'est-ce qu'un jeu de données sur data.gouv.fr ?**

Un jeu de donnée sur data.gouv.fr est un ensemble de ressources ou d’informations (fichiers de données, fichiers d’explications, API etc.) et de métadonnées (description, producteur, date de publication, mots-clefs, couverture géographique temporelle etc.) sur un thème donné.
{% endhint %}

## Comment publier des données ?  <a href="#definir-qui-publie-le-jeu-de-donnees" id="definir-qui-publie-le-jeu-de-donnees"></a>

Plusieurs modes de mises en ligne sont possible sur data.gouv.fr :&#x20;

* Par upload direct
* Par API
* Par moissonnage

{% hint style="info" %}
En amont de la publication il est important de bien préparer le jeu de données. \
Voir notre [guide qualité](../guide-qualite/preparer-le-jeu-de-donnees.md).&#x20;
{% endhint %}

{% tabs %}
{% tab title="Directement sur data.gouv.fr" %}
## Mise à disposition directe sur data.gouv.fr <a href="#mise-a-disposition-directe-sur-data-gouv-fr" id="mise-a-disposition-directe-sur-data-gouv-fr"></a>

### 1. Définir qui publie le jeu de données&#x20;

Un jeu de données peut être publié sous le nom de votre compte utilisateur ou sous la bannière d’une organisation.

Nous vous conseillons de publier un jeu de données sous le nom de votre compte utilisateur seulement s’il n’a pas été produit dans le cadre des activités d’une organisation à laquelle vous êtes rattaché.

### 2. Décrire le jeu de données

L'étape de description est cruciale pour que vos jeux de données soient bien référencés et faciliter la réutilisation.

| Information                                                                                                                          | Description de l'information                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Titre\* ](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#titre)                                                | Le titre de votre jeu de données doit être le plus précis et spécifique possible. Il doit également correspondre au vocabulaire employé par les utilisateurs. Ces derniers recherchent les données le plus souvent dans un moteur de recherche.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [Sigle](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#sigle)                                                   | Vous avez la possibilité d’apposer un sigle à votre jeu de données. Les lettres qui composent ce sigle n’ont pas besoin d’être séparées par des points.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [Description](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#description)\*                                     | La description de votre jeu de données permet aux personnes qui le consultent d’obtenir des informations sur le contenu et la structure des ressources publiées, le contexte de production des données, les contacts producteurs etc.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [Licence](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#licence)                                               | Les licences définissent les règles de réutilisation des jeux de données publiés. En choisissant une licence de réutilisation, vous vous assurez que le jeu de données publié sera réutilisé selon les conditions d’usage que vous avez définies.Afin d’éviter la multiplication des licences, la[ loi pour une République numérique](https://www.legifrance.gouv.fr/affichTexteArticle.do?cidTexte=JORFTEXT000033202746\&idArticle=JORFARTI000033203004\&categorieLien=cid) a prévu la création d’une liste de licences qui peuvent être utilisées par les administrations. Le site data.gouv.fr[ a référencé la liste des licences applicables](https://www.data.gouv.fr/fr/licences) aux informations publiques (données, documents…). |
| [Fréquence de mise à jour](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#fr%C3%A9quence-de-mise-%C3%A0-jour)\* | La fréquence de mise à jour correspond à la fréquence à laquelle vous prévoyez de mettre à jour les données publiées. Cette fréquence de mise à jour reste indicative.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [Mots clés](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#mots-clefs)                                          | Les mots clés caractérisent votre jeu de données. Ils apparaissent sur la page de présentation et apportent un meilleur référencement du jeu de données lors d’une recherche utilisateur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [Couverture temporelle](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#couverture-temporelle)                   | La couverture temporelle indique la portée dans le temps des données publiées.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [Granularité spatiale](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#granularit%C3%A9-spatiale)                | La granularité spatiale indique le niveau de détail géographique le plus fin que peut couvrir vos données.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [Mode privé](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#priv%C3%A9)                                         | L’activation du mode privé permet de ne pas mettre en ligne le jeu de données. Cela laisse la possibilité de l’éditer avant sa publication.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

_Il est obligatoire de renseigner ces informations._

### 3. Ajouter des fichiers

{% hint style="info" %}
Un jeu de données peut contenir plusieurs types de fichiers (données mises à jour, données historisées, documentation, code source, API, lien, etc.).
{% endhint %}

Vous avez la possibilité d’importer vos fichiers sur data.gouv.fr selon différents modes de mise à disposition.

Lors de l’étape “Ajoutez vos ressources”, deux options vous sont proposées:

1. Vous pouvez télécharger vos ressources depuis votre ordinateur vers le serveur de data.gouv.fr. Vos ressources seront alors hébergées sur les serveurs de data.gouv.fr.
2. Vous pouvez créer un lien vers une ressource distante existante. Les informations contenues dans le fichier resteront hébergées sur le serveur distant fléché.



<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="API" %}
## Mise à disposition par API <a href="#mise-a-disposition-par-api" id="mise-a-disposition-par-api"></a>

{% hint style="info" %}
**Qu’est-ce qu’une API ?**

Une API est une interface, un contrat passé entre deux systèmes informatiques pour leur permettre de communiquer. Cette solution informatique permet d’automatiser des tâches depuis votre ordinateur ou vos serveurs.
{% endhint %}

A partir de l’API de data.gouv.fr, vous pouvez réaliser les mêmes actions que sur la plateforme :

* Créer un jeu de données au nom de votre compte utilisateur ou au nom de votre organisation ;
* Décrire votre jeu de données et les ressources associées ;
* Ajouter ou supprimer une ressource ou un jeu de données.

L’API de data.gouv.fr propose également des fonctionnalité complémentaires à la publication de jeux de données comme la possibilité de récupérer les métadonnées des jeux de données ou de fichiers ou encore accéder au contenu des fichiers d’un jeu de données.

#### Quand utiliser l’API de data.gouv.fr ? <a href="#quand-utiliser-l-api-de-data-gouv-fr" id="quand-utiliser-l-api-de-data-gouv-fr"></a>

À la différence du mode de mise à disposition directe des données sur data.gouv.fr, l’utilisation de l’API permet de réaliser des actions de manière automatisée depuis votre ordinateur ou vos serveurs. Il est par conséquent conseillé d’utiliser une API lorsque la fréquence de publication d’un jeu de données est régulière.

#### Comment utiliser l’API de data.gouv.fr ? <a href="#comment-utiliser-l-api-de-data-gouv-fr" id="comment-utiliser-l-api-de-data-gouv-fr"></a>

L’utilisation de l’API de data.gouv.fr se fait par le point d’entrée racine de l’API. Afin de pouvoir exécuter des opérations d’écriture, il est nécessaire d’obtenir une clé API. Cette clé est accessible depuis les paramètres de votre profil administrateur.

![Générer une clé d'API](https://guides.etalab.gouv.fr/assets/img/cle\_api.f5378a97.jpg)

Les appels à l’API sont soumis aux mêmes permissions que l’interface web. Par exemple, si vous souhaitez publier ou modifier un jeu de données au nom d’une organisation, vous devez appartenir à cette organisation.

**Pour en savoir plus consulter le** [**guide API**](api/)**.**
{% endtab %}

{% tab title="Moissonage" %}
## Publier un catalogue de données existant par moissonnage <a href="#publier-un-catalogue-de-donnees-existant-par-moissonnage" id="publier-un-catalogue-de-donnees-existant-par-moissonnage"></a>

{% hint style="info" %}
**Qu’est-ce que le moissonnage ?**

Le moissonnage est un mécanisme permettant de collecter les métadonnées sur un catalogue distant et de les stocker sur une autre plateforme afin de proposer un second point d’accès aux données.
{% endhint %}

Le service de moissonnage mis à votre disposition permet de référencer sur data.gouv.fr les jeux de données publiés sur d’autres catalogues de données en ligne. De cette manière, vous n’avez pas besoin d’importer à la main sur data.gouv.fr les jeux de données que vous avez déjà importés sur votre propre plateforme.

#### Quand utiliser le service de moissonnage ? <a href="#quand-utiliser-le-service-de-moissonnage" id="quand-utiliser-le-service-de-moissonnage"></a>

Si vous mettez en ligne des données publiques sur une plateforme ouverte, dans un format dont les métadonnées correspondent à la syntaxe ODS, CKAN, ou DCAT vous pouvez les référencer automatiquement sur data.gouv.fr en utilisant notre service de moissonnage.

#### Comment utiliser le service de moissonnage ? <a href="#comment-utiliser-le-service-de-moissonnage" id="comment-utiliser-le-service-de-moissonnage"></a>

Il est possible de demander au moissonneur d’importer l’ensemble des données ou de ne sélectionner que certains jeux de données au moyen de filtres. Il n’est pas nécessaire de créer un moissonneur par jeu de données à importer, un seul moissonneur par portail suffit.

Le principe du moissonnage sur data.gouv.fr se décompose en plusieurs étapes :

1. Vous [créez un moissonneur sur data.gouv.fr](https://doc.data.gouv.fr/jeux-de-donnees/demander-a-datagouvfr-de-moisonner-votre-site/) afin que data.gouv.fr suive l’activité de votre plateforme ;
2. Vous publiez des données sur votre plateforme d’open data ;
3. Vous demandez validation de votre moissonneur sur [le support data.gouv.fr](https://support.data.gouv.fr/collectivite-territoriale/referencement/moissonnage#support-tree) ;
4. La configuration du moissonneur est validée par l’équipe en charge de data.gouv.fr ;
5. Le moissonneur de data.gouv.fr vient automatiquement récupérer les données de votre plateforme ;
6. Les données de votre plateforme sont référencées et visibles sur data.gouv.fr. :tada:

**Pour en savoir plus consultez le** [**guide moissonage**](../guides/guide-data.gouv.fr/moissonage.md)**.**
{% endtab %}
{% endtabs %}



## Gérer son jeu de donnée <a href="#definir-qui-publie-le-jeu-de-donnees" id="definir-qui-publie-le-jeu-de-donnees"></a>

## Faire vivre son jeu de données <a href="#faire-vivre-son-jeu-de-donnees" id="faire-vivre-son-jeu-de-donnees"></a>



* Répondre aux discussions&#x20;
* Publier une réutilisation



#### Obtenir des informations à propos de votre jeu de données <a href="#obtenir-des-informations-a-propos-de-votre-jeu-de-donnees" id="obtenir-des-informations-a-propos-de-votre-jeu-de-donnees"></a>

Afin de suivre la vie de votre jeu de données sur data.gouv.fr, vous avez la possibilité de suivre ses statistiques d’utilisation depuis votre compte administrateur. Un tableau de bord centralise les informations relatives au jeu de données :

* Sa couverture temporelle, sa fréquence de mise à jour et ses mots-clés ; sa couverture spatiale ;
* son statut de disponibilité et les téléchargements associés à chaque ressource publiée ;
* ses réutilisations ;
* ses anomalies ;
* ses abonnés ;
* ses ressources communautaires.

Des statistiques d’audience et de téléchargement sont disponibles sur le tableau de bord de votre compte administrateur.

**Qualité du jeu de données**

La qualité de votre jeu de données est fondamentale pour qu’il soit réutilisé par le plus d’utilisateurs possible. Afin de vous guider, un encart “Qualité” est mis à votre disposition dans le tableau de bord de chaque jeu de données. L’objectif est de vous aider à améliorer la qualité des (méta)données à partir de six critères :

* Le jeu de données possède t-il une description ?
* Des mots clés sont-ils associés à votre jeu de données ?
* Le format du jeu de données est-il ouvert ?
* Des discussions à propos du jeu ont-elles été ouvertes ?
* Le jeu de donnée est-il à jour ?
* Les ressources du jeu de données sont-elles accessibles ?



### <mark style="background-color:blue;">Mettre à jour ou modifier un jeu de données et/ou une ressource</mark> <a href="#mettre-a-jour-ou-modifier-un-jeu-de-donnees-et-ou-une-ressource" id="mettre-a-jour-ou-modifier-un-jeu-de-donnees-et-ou-une-ressource"></a>

Les données publiées sur data.gouv.fr peuvent être [mises à jour après leur publication](https://doc.data.gouv.fr/jeux-de-donnees/mettre-a-jour-un-jeu-de-donnees-ou-une-ressource/), que la modification porte sur un jeu de données (sa description, ses tags, etc.) ou sur l’une des ressources qu’il contient.

Un producteur qui s’engage dans une logique de publication de ses données a intérêt à actualiser les ressources publiées le plus souvent possible. Ce critère de fraîcheur est critique pour les réutilisateurs qui fondent leurs services et produits sur les données publiées sur data.gouv.fr.



### Répondre aux discussions <a href="#transferer-un-jeu-de-donnees" id="transferer-un-jeu-de-donnees"></a>

Lorsque vous publiez un jeu de données tout utilisateur qui dispose d’un compte data.gouv.fr peut ouvrir des discussions sur la page du jeu de données. Ces discussions permettent aux réutilisateurs des données de poser des questions au producteur, de faire remonter des erreurs constatées dans le jeu de données ou de proposer des améliorations.

Vous avez la possibilité de [récupérer le lien d’une discussion ou d’un commentaire, d’ajouter un commentaire et de fermer une discussion](https://doc.data.gouv.fr/reutilisations-et-discussions/moderer-une-discussion/). Les discussions publiées sont visibles par tous les visiteurs de data.gouv.fr.

{% embed url="https://www.loom.com/share/f098242f1a7e417bb8c272a9297402e6" %}

### Transférer un jeu de données <a href="#transferer-un-jeu-de-donnees" id="transferer-un-jeu-de-donnees"></a>

Un jeu de données publié au nom d’un individu ou d’une organisation peut être [transféré vers un autre individu ou une autre organisation](https://doc.data.gouv.fr/jeux-de-donnees/transferer-un-jeu-de-donnees/).

<details>

<summary>Comment transférer un jeu de donnée </summary>

Pour transférer un jeu de données publié avec votre propre compte, à titre personnel :

1. [Connectez-vous à votre compte](https://www.data.gouv.fr/fr/login) ;
2. Rendez-vous sur [votre tableau de bord](https://www.data.gouv.fr/fr/admin/), en cliquant sur **Administration** en haut à droite de votre écran ;
3. Allez sur [la page de suivi de votre compte](https://www.data.gouv.fr/fr/admin/me/edit), en cliquant sur **Profil**, dans la colonne de gauche ;
4. Naviguez jusqu’à la section **Jeux de données** située en milieu de page ;
5. Cliquez sur le jeu de données que vous souhaitez transférer ;
6. Cliquez sur la flèche située à côté du bouton **Éditer**, en haut à droite de votre écran, puis sur **Transférer** dans le menu déroulant qui apparaît alors ;
7. Sélectionnez le type de compte vers lequel vous souhaitez transférer le jeu de données (individu ou organisation) ;
8. Saisissez le nom de l’utilisateur ou de l’organisation vers lequel vous souhaitez transférer les données, puis cliquez sur son profil quand il apparaît à l’écran ;
9. Indiquez une raison éventuelle pour ce transfert dans la zone **Raison** puis cliquez sur **Confirmer** pour valider la demande de transfert ;
10. Votre destinataire reçoit alors une notification. Une fois la demande de transfert acceptée par votre destinataire, le jeu de données lui est effectivement transféré.

</details>

{% embed url="https://www.loom.com/share/8ea87da546f64d41b72535ada8d728cb" %}

**Accepter une demande de transfert**

Pour accepter une demande de transfert vers votre compte :

1. [Connectez-vous à votre compte](https://www.data.gouv.fr/fr/login) ;
2. Rendez-vous sur [votre tableau de bord](https://www.data.gouv.fr/fr/admin/), en cliquant sur **Administration** en haut à droite de votre écran ;
3. Cliquez sur l’enveloppe située en haut à droite de votre écran, puis sur le message dont le titre est **Demande de transfert en attente** ;
4. Vérifiez que le jeu de données que vous êtes sur le point d’accepter est le bon puis cliquez sur **Accepter** pour confirmer le transfert.



### Supprimer un jeu de données ou une ressource <a href="#supprimer-un-jeu-de-donnees-ou-une-ressource" id="supprimer-un-jeu-de-donnees-ou-une-ressource"></a>

Vous pouvez [supprimer un jeu de données, ou l’une des ressources qui le compose](https://doc.data.gouv.fr/jeux-de-donnees/mettre-a-jour-un-jeu-de-donnees-ou-une-ressource/), si vous êtes l’auteur du jeu de données en question, ou si vous appartenez à l’organisation qui en est à l’origine. La suppression d’un jeu de données ou d’une ressource est irréversible.

{% hint style="warning" %}
**Conservation des anciennes ressources**

Il est conseillé de supprimer le moins de ressources possibles de la plateforme data.gouv.fr. Même si vos données ne sont plus mises à jour il est possible que des utilisateurs utilisent tout de même ces données. De plus, la suppression de certaines ressources peut entraîner la maintenance de nombreux services ou produits qui reposent sur l’exploitation des données publiées.
{% endhint %}

{% embed url="https://www.loom.com/share/83b80a106f7940ebbf01a79cf63e363c" %}

### &#x20;<a href="#partager-son-jeu-de-donnees-et-ses-ressources" id="partager-son-jeu-de-donnees-et-ses-ressources"></a>



