# Jeux de données

{% hint style="info" %}
**Qu'est-ce qu'un jeu de données sur data.gouv.fr ?**

Un jeu de donnée sur data.gouv.fr est un ensemble de ressources ou d’informations (fichiers de données, fichiers d’explications, API, lien...) et de métadonnées (description, producteur, date de publication, mots-clefs, couverture géographique temporelle...) sur un thème donné.
{% endhint %}

### &#x20;<a href="#definir-qui-publie-le-jeu-de-donnees" id="definir-qui-publie-le-jeu-de-donnees"></a>

Plusieurs modes de mises en ligne sont possible :&#x20;

* Par upload direct
* Par API
* Par moissonnage

{% tabs %}
{% tab title="Directement sur data.gouv.fr" %}
Mise à disposition directe sur data.gouv.fr

Vous avez la possibilité d’importer vos ressources directement depuis la plateforme data.gouv.fr. Les étapes de cette publication reprend les étapes précédemment citées:

![Création d'un jeu de données](https://guides.etalab.gouv.fr/assets/img/nouveau\_jeu\_de\_donnees.84fe2272.jpg)

Lors de l’étape “Ajoutez vos ressources”, deux options vous sont proposées:

1. Vous pouvez télécharger vos ressources depuis votre ordinateur vers le serveur de data.gouv.fr. Vos ressources seront alors hébergées sur les serveurs de data.gouv.fr.
2. Vous pouvez créer un lien vers une ressource distante existante. Les informations contenues dans le fichier resteront hébergées sur le serveur distant fléché.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Par API" %}
### Mise à disposition par API <a href="#mise-a-disposition-par-api" id="mise-a-disposition-par-api"></a>

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
### Publier un catalogue de données existant par moissonnage <a href="#publier-un-catalogue-de-donnees-existant-par-moissonnage" id="publier-un-catalogue-de-donnees-existant-par-moissonnage"></a>

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

**Pour en savoir plus consultez le** [**guide moissonage**](moissonage/)**.**
{% endtab %}
{% endtabs %}



### Définir qui publie le jeu de données <a href="#definir-qui-publie-le-jeu-de-donnees" id="definir-qui-publie-le-jeu-de-donnees"></a>

Un jeu de données peut être publié sous le nom de votre compte utilisateur ou sous la bannière d’une organisation.

{% hint style="info" %}
**Quand est-il conseillé de publier sous le nom de votre compte utilisateur ?**\
Nous vous conseillons de publier un jeu de données sous le nom de votre compte utilisateur seulement s’il n’a pas été produit dans le cadre des activités d’une organisation à laquelle vous êtes rattaché.
{% endhint %}





### Décrire le jeu de données <a href="#decrire-le-jeu-de-donnees" id="decrire-le-jeu-de-donnees"></a>

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-type="content-ref"></th></tr></thead><tbody><tr><td>Voir le guide qualité sur la documentation des données</td><td></td><td></td><td><a href="../guide-qualite/documenter-les-donnees.md">documenter-les-donnees.md</a></td></tr></tbody></table>



{% content-ref url="../guide-qualite/documenter-les-donnees.md" %}
[documenter-les-donnees.md](../guide-qualite/documenter-les-donnees.md)
{% endcontent-ref %}





Plusieurs modes de&#x20;







L'étape de description est cruciale pour que vos jeux de données soient bien référencés et facilité la réutilisation.



Lors de la création de la page de votre jeu de données, vous avez la possibilité de renseigner les informations suivantes:

| Information                                                                                                                          | Description de l'information                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Titre\* ](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#titre)                                                | Le titre de votre jeu de données doit être le plus précis et spécifique possible. Il doit également correspondre au vocabulaire employé par les utilisateurs. Ces derniers recherchent les données le plus souvent dans un moteur de recherche.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| [Sigle](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#sigle)                                                   | Vous avez la possibilité d’apposer un sigle à votre jeu de données. Les lettres qui composent ce sigle n’ont pas besoin d’être séparées par des points.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| [Description](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#description)\*                                     | La description de votre jeu de données permet aux personnes qui le consultent d’obtenir des informations sur le contenu et la structure des ressources publiées, le contexte de production des données, les contacts producteurs etc. C’est généralement la première chose que les utilisateurs lisent quand ils découvrent votre jeu de données.                                                                                                                                                                                                                                                                                                                                                                                         |
| [Licence](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#licence)                                               | Les licences définissent les règles de réutilisation des jeux de données publiés. En choisissant une licence de réutilisation, vous vous assurez que le jeu de données publié sera réutilisé selon les conditions d’usage que vous avez définies.Afin d’éviter la multiplication des licences, la[ loi pour une République numérique](https://www.legifrance.gouv.fr/affichTexteArticle.do?cidTexte=JORFTEXT000033202746\&idArticle=JORFARTI000033203004\&categorieLien=cid) a prévu la création d’une liste de licences qui peuvent être utilisées par les administrations. Le site data.gouv.fr[ a référencé la liste des licences applicables](https://www.data.gouv.fr/fr/licences) aux informations publiques (données, documents…). |
| [Fréquence de mise à jour](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#fr%C3%A9quence-de-mise-%C3%A0-jour)\* | La fréquence de mise à jour correspond à la fréquence à laquelle vous prévoyez de mettre à jour les données publiées. Cette fréquence de mise à jour reste indicative.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| [Mots clés](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#mots-clefs)                                          | Les mots clés caractérisent votre jeu de données. Ils apparaissent sur la page de présentation et apportent un meilleur référencement du jeu de données lors d’une recherche utilisateur. L’apposition d’un mot clé permet également de classer votre jeu de données dans des thématiques. À partir de chaque mot clé, vous pouvez obtenir la liste des jeux de données pour lesquels le mot clé a également été assigné.                                                                                                                                                                                                                                                                                                                 |
| [Couverture temporelle](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#couverture-temporelle)                   | La couverture temporelle indique la portée dans le temps des données publiées                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [Granularité spatiale](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#granularit%C3%A9-spatiale)                | La granularité spatiale indique le niveau de détail géographique le plus fin que peut couvrir vos données.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [Mode privé](https://doc.data.gouv.fr/jeux-de-donnees/publier-un-jeu-de-donnees/#priv%C3%A9)                                         | L’activation du mode privé permet de ne pas mettre en ligne le jeu de données. Cela laisse la possibilité de l’éditer avant sa publication.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

_Il est obligatoire de renseigner ces informations._

### Ajouter les ressources <a href="#ajouter-les-ressources" id="ajouter-les-ressources"></a>

{% hint style="info" %}
**Qu’est-ce qu’une ressource ?**

Une ressource est un fichier téléchargeable. Il s'agit des données en elles même.&#x20;

Un jeu de données peut contenir plusieurs ressources (données mises à jour, données historisées, documentation, code source, API, lien, etc.).
{% endhint %}

Vous avez la possibilité d’importer vos ressources sur data.gouv.fr selon différents modes de mise à disposition.
