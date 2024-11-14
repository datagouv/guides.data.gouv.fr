# Catalogage de données - GRIST

## Objectif

L'objectif principal du catalogage des données avec Grist est de **simplifier la gestion et la publication des données par les administrations**. Actuellement, les producteurs de données gèrent souvent leurs données de manière redondante, avec des catalogues internes distincts de leurs publications sur data.gouv.fr. L'outil Grist proposé par la DINUM vise à créer **un catalogue unique et collaboratif** pour une gestion plus efficace et une fonction de publication directe sur data.gouv.fr.

## Enjeux juridiques

Le catalogage des données répond à des obligations légales importantes :

* **Data Governance Act (art. 8 §2) :** Le point d'information unique doit fournir une liste de toutes les ressources de données disponibles, y compris des informations sur le format, la taille et les conditions de réutilisation.
* **Code de la Relation entre le Public et l'Administration (art. L322-6) :** Le catalogue de données est un document administratif communicable.

De plus, le catalogage peut servir à :

* Gérer les politiques publiques basées sur les données en offrant une vue d'ensemble des données détenues par les administrations.
* Faciliter la proactivité en identifiant les données nécessaires aux dispositifs et au “Dites le nous une fois”.
* Simplifier la constitution du registre de traitement des données à caractère personnel pour les DPO.
* Améliorer le partage de données dans le cadre du Data Governance Act.

## Fonctionnalités et mise en place

#### Fonctionnalités

Grist offre plusieurs fonctionnalités pour gérer un catalogue de données :

* **Créer des tables et partager de vues personnalisées** pour organiser le catalogue de données selon vos besoins
* **Marquer les jeux de données comme "publics" ou "non publics"** pour gérer la publication sur data.gouv.fr.
* **Gérer les droits d'accès des membres** avec différents rôles : lecteur, éditeur, administrateur.
* **Créer des tableaux de bord paramétrables** pour le suivi des données (tables, graphiques, listes thématiques).
* **Intégration avec data.gouv.fr** pour la publication directe des jeux de données.

#### Liste des champs

La table principale permet de renseigner plusieurs champs relatifs à chaque jeu de données :

* Public (oui / non) : indique si les métadonnées du jeu de données peuvent être publiées en open data
* Titre, description, mots clés
* Organisation, service, système d'information
* Contacts (service et personne), commentaires
* Date de publication, date de mise à jour, fréquence de mise à jour
* Couverture géographique, URL, format, licence
* Thématique, données ouvertes, URL Open Data, volumétrie

#### Droits

Grist permet de gérer les droits d'accès des membres de l'organisation. Trois rôles sont disponibles :

* **Lecteur :** Peut consulter les données du catalogue.
* **Éditeur :** Peut modifier les données du catalogue.
* **Administrateur :** Possède tous les droits, y compris la gestion des utilisateurs et des droits d'accès.

#### Étapes de mise en place

L’outil de catalogage propose une mise en place en 5 étapes de votre catalogue de données :

1. **Renseigner les tables de référence :** Nom de l'organisation, SIRET, services, contacts, systèmes d'information (SI) et thématiques.
2. **Ajouter les jeux de données** au catalogue.
3. **Qualifier les jeux de données :** Marquer comme "publics" ou "non publics".
4. **Gérer les droits des membres :** Attribuer les rôles de lecteur, éditeur ou administrateur.
5. **Créer vos outils de suivi :** Tableaux de bord personnalisés pour la gestion des données.

## Avantages de la solution Grist

* **Sécurité et confidentialité :** Hébergé en France par la DINUM.
* **Open Source :** Code source ouvert et transparent.
* **Intégration :** Publication directe sur data.gouv.fr.
* **Portabilité des données :** Exportation facile dans des formats courants.
* **Facilité d'utilisation :** Conçu pour être accessible aux utilisateurs sans expertise technique.
* **Partage et collaboration :** Partage facile et contrôle d'accès précis.
* **Extensibilité :** Extension possible via des API.
* **Documentation complète :** Documentation exhaustive pour guider les utilisateurs.

## Partenaires et accompagnement

La DINUM finance la solution Grist et l’équipe [data.gouv.fr](http://data.gouv.fr) propose un accompagnement aux administrations qui souhaitent le mettre en place. Plusieurs administrations utilisent déjà ou sont en cours d'intégration de Grist, notamment le CEREMA, le Ministère de l'Agriculture et de l'Alimentation, l'ADEME et la Gendarmerie.

Pour obtenir Grist, vous pouvez contacter l’équipe afin de démarrer une expérimentation : un accès à l'outil et une session d'initiation.

# FAQ

<details>
  <summary>Puis-je utiliser Grist pour gérer des jeux de données provenant de différentes sources, y compris des sources externes à mon organisation ?</summary>
Oui, Grist peut être utilisé pour gérer des jeux de données provenant de différentes sources, y compris des sources externes à votre organisation.  Vous pouvez ajouter des jeux de données manuellement ou les importer depuis data.gouv.fr.  De plus, vous pouvez spécifier si un jeu de données est "interne" ou "externe" à votre organisation en utilisant une colonne dédiée dans Grist.  Ceci permet de filtrer les jeux de données lors de la publication sur data.gouv.fr ou sur une plateforme thématique.

</details>

 <details>
  <summary>Est-il possible de connecter Grist à d'autres plateformes de données ?</summary>
 Oui, il est possible de connecter Grist à d'autres plateformes de données via des API. La plateforme en question doit cependant développer un plugin pour se connecter à Grist et permettre l'échange de données entre les deux plateformes.  Cependant, la DINUM encourage la centralisation des données sur data.gouv.fr pour des raisons de budget et d'efficacité.
</details>
    
<details>
<summary>Comment puis-je gérer la publication de données sensibles qui ne doivent pas être rendues publiques sur data.gouv.fr ?</summary>
Vous pouvez marquer les jeux de données sensibles comme "non publics" dans Grist pour empêcher leur publication sur data.gouv.fr. Cependant, les métadonnées de ces jeux de données seront tout de même visibles sur data.gouv.fr, conformément aux exigences légales. Vous pouvez également utiliser Grist pour gérer les demandes d'accès à ces données sensibles en interne.
</details>

<details>
<summary>Puis-je utiliser Grist pour gérer un catalogue de données interne sans le publier sur data.gouv.fr ?</summary>
Oui, vous pouvez utiliser Grist pour gérer un catalogue de données interne sans le publier sur data.gouv.fr. L'outil peut être utilisé de manière autonome pour organiser et documenter vos données. Vous pouvez ensuite choisir de publier les données sur data.gouv.fr et sur une plateforme thématique lorsque vous êtes prêt.
</details>

<details>
<summary>Puis-je personnaliser Grist pour répondre aux besoins spécifiques de mon organisation ?</summary>
Oui, Grist est un outil open source, ce qui signifie que vous pouvez modifier le code source pour l'adapter à vos besoins. Vous pouvez également ajouter des colonnes et des tables personnalisées à votre catalogue de données Grist. De plus, vous pouvez créer des vues personnalisées et des tableaux de bord pour organiser et analyser vos données de manière spécifique à votre organisation. Attention néanmoins à ne pas modifier le modèle des champs déjà existants pour le catalogage.
</details>

<details>
<summary>Puis-je utiliser Grist pour gérer la qualité des données et suivre les métadonnées ?</summary>
Oui, Grist peut être utilisé pour gérer la qualité des données et suivre les métadonnées. Vous pouvez ajouter des colonnes pour suivre des informations telles que la qualité des données, les problèmes rencontrés, les commentaires des utilisateurs, et les dates de mise à jour. Vous pouvez également utiliser les tableaux de bord Grist pour visualiser la qualité des données et identifier les jeux de données qui nécessitent une attention particulière.
</details>

<details>
<summary>Comment puis-je assurer la sécurité et la confidentialité des données stockées dans Grist ?</summary>
Grist est hébergé en France par la DINUM, ce qui garantit un niveau de sécurité et de confidentialité élevé. De plus, vous pouvez gérer les droits d'accès des utilisateurs à votre catalogue de données Grist pour contrôler qui peut consulter, modifier ou administrer les données. Vous pouvez également ajouter des mesures de sécurité supplémentaires, telles que l'authentification à deux facteurs, pour renforcer la protection de vos données.
</details>

<details>
<summary>Est-il possible d'exporter les données du catalogue Grist vers d'autres formats ?</summary>
Oui, Grist permet d'exporter les données du catalogue vers des formats courants tels que CSV, Excel, et JSON. Ceci vous permet de partager facilement les données de votre catalogue avec d'autres utilisateurs ou de les utiliser dans d'autres applications.
</details>

### Questions complémentaires

<details>
<summary>Quel est l'objectif principal du catalogage de données avec Grist ?</summary>
L'objectif principal du catalogage des données avec Grist est de **simplifier la gestion et la publication des données par les administrations**. Actuellement, les producteurs de données gèrent souvent leurs données de manière redondante, avec des catalogues internes distincts de leurs publications sur data.gouv.fr. L'outil Grist proposé par la DINUM vise à créer **un catalogue unique et collaboratif** pour une gestion plus efficace et une fonction de publication directe sur data.gouv.fr.
</details>

<details>
<summary>Quels sont les enjeux juridiques liés au catalogage de données ?</summary>
Le catalogage des données répond à des obligations légales importantes :
- **Data Governance Act (art. 8 §2) :** Le point d'information unique doit fournir une liste de toutes les ressources de données disponibles, y compris des informations sur le format, la taille et les conditions de réutilisation.
- **Code de la Relation entre le Public et l'Administration (art. L322-6) :** Le catalogue de données est un document administratif communicable.

De plus, le catalogage peut servir à :
- Gérer les politiques publiques basées sur les données en offrant une vue d'ensemble des données détenues par les administrations.
- Faciliter la proactivité en identifiant les données nécessaires aux dispositifs et au “Dites le nous une fois”.
- Simplifier la constitution du registre de traitement des données à caractère personnel pour les DPO.
- Améliorer le partage de données dans le cadre du Data Governance Act.
</details>

<details>
<summary>Quelles sont les fonctionnalités offertes par Grist pour la gestion d'un catalogue de données ?</summary>
Grist offre plusieurs fonctionnalités pour gérer un catalogue de données :
- **Créer des tables et partager de vues personnalisées** pour organiser le catalogue de données selon vos besoins.
- **Marquer les jeux de données comme "publics" ou "non publics"** pour gérer la publication sur data.gouv.fr.
- **Gérer les droits d'accès des membres** avec différents rôles : lecteur, éditeur, administrateur.
- **Créer des tableaux de bord paramétrables** pour le suivi des données (tables, graphiques, listes thématiques).
- **Intégration avec data.gouv.fr** pour la publication directe des jeux de données.
</details>

<details>
<summary>Quels sont les champs de données que l'on peut renseigner dans la table principale de Grist ?</summary>
La table principale permet de renseigner plusieurs champs relatifs à chaque jeu de données :
- **Public (oui / non) :** indique si les métadonnées du jeu de données peuvent être publiées en open data.
- **Titre, description, mots clés**
- **Organisation, service, système d'information**
- **Contacts (service et personne), commentaires**
- **Date de publication, date de mise à jour, fréquence de mise à jour**
- **Couverture géographique, URL, format, licence**
- **Thématique, données ouvertes, URL Open Data, volumétrie**
</details>

<details>
<summary>Comment Grist gère-t-il les droits d'accès des utilisateurs ?</summary>
Grist permet de gérer les droits d'accès des membres de l'organisation. Trois rôles sont disponibles :
- **Lecteur :** Peut consulter les données du catalogue.
- **Éditeur :** Peut modifier les données du catalogue.
- **Administrateur :** Possède tous les droits, y compris la gestion des utilisateurs et des droits d'accès.
</details>

<details>
<summary>Quelles sont les étapes à suivre pour mettre en place un catalogue de données avec Grist ?</summary>
L’outil de catalogage propose une mise en place en 5 étapes de votre catalogue de données :
- **Renseigner les tables de référence :** Nom de l'organisation, SIRET, services, contacts, systèmes d'information (SI) et thématiques.
- **Ajouter les jeux de données** au catalogue.
- **Qualifier les jeux de données :** Marquer comme "publics" ou "non publics".
- **Gérer les droits des membres :** Attribuer les rôles de lecteur, éditeur ou administrateur.
- **Créer vos outils de suivi :** Tableaux de bord personnalisés pour la gestion des données.
</details>

<details>
<summary>Quels sont les avantages de la solution Grist pour le catalogage de données ?</summary>
Grist offre plusieurs avantages pour le catalogage de données :
- **Sécurité et confidentialité :** Hébergé en France par la DINUM.
- **Open Source :** Code source ouvert et transparent.
- **Intégration :** Publication directe sur data.gouv.fr.
- **Portabilité des données :** Exportation facile dans des formats courants.
- **Facilité d'utilisation :** Conçu pour être accessible aux utilisateurs sans expertise technique.
- **Partage et collaboration :** Partage facile et contrôle d'accès précis.
- **Extensibilité :** Extension possible via des API.
- **Documentation complète :** Documentation exhaustive pour guider les utilisateurs.
</details>

<details>
<summary>Quelles administrations utilisent déjà Grist pour le catalogage de données ?</summary>
Plusieurs administrations utilisent déjà ou sont en cours d'intégration de Grist, notamment le CEREMA, le Ministère de l'Agriculture et de l'Alimentation, l'ADEME et la Gendarmerie.
</details>

<details>
<summary>Comment puis-je obtenir Grist et bénéficier d'un accompagnement pour sa mise en place ?</summary>
Pour obtenir Grist, vous pouvez contacter l’équipe data.gouv.fr afin de démarrer une expérimentation qui comprend un accès à l'outil et une session d'initiation.
</details>
