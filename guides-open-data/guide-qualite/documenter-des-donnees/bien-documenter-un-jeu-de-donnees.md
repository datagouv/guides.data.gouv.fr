# Bien documenter un jeu de données

{% hint style="success" %}
La bonne documentation d'un jeu de données recouvre, entre autres : &#x20;

* une description générale du jeu de données
* une description du mode de production des données
* une description du modèle de données
* une description du schéma de données
* une description des métadonnées
* une description des changements majeurs&#x20;
{% endhint %}

## Description générale du jeu de données <a href="#description-generale-du-jeu-de-donnees" id="description-generale-du-jeu-de-donnees"></a>

Il est conseillé de commencer la documentation par une **description synthétique du jeu de données** qui donne un aperçu rapide des informations mises à disposition.

La description générale peut couvrir les points suivants :&#x20;

* [ ] **Une description générale des données** ;
* [ ] **La liste des fichiers mis à disposition** ;
* [ ] **La description du format des fichiers** ;
* [ ] **La fréquence de mise à jour**.

> **Exemple** : Description générale du [jeu de données du Répertoire national des élus](https://www.data.gouv.fr/fr/datasets/repertoire-national-des-elus-1/)&#x20;

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>Description générale du <a href="https://www.data.gouv.fr/fr/datasets/repertoire-national-des-elus-1/">jeu de données du Répertoire national des élus</a> </p></figcaption></figure>

## Description du mode de production des données <a href="#description-du-mode-de-production-des-donnees" id="description-du-mode-de-production-des-donnees"></a>

La structure d'un jeu de données et son contenu sont liés au contexte de production des données. La description de l'environnement métier est donc indispensable.&#x20;

La description du mode de production du jeu de données permet au réutilisateur de comprendre la structure du jeu, la nature des données et les possibles manques ou incohérences du fichier.

Il est donc conseillé de préciser :&#x20;

* [ ] **comment les données ont été produites** (saisie manuelle, collecte automatique, etc.) ;&#x20;
* [ ] **qui sont les acteurs producteurs des données** et si les données sont produites par plusieurs acteurs, le modèle de gouvernance mis en place pour centraliser les données ;&#x20;
* [ ] **si les données sont exhaustives et si elles présentent des limites dans leur qualité** ;
* [ ] **les points d'attention et précautions d'usage** pour manipuler ces données.

{% hint style="info" %}
Certains jeux de données ne peuvent pas être utilisés à certaines fins ou possèdent des limitations qui rendent impossible certaines analyses.&#x20;

Par exemple, [l’article R112 A-3 du Livre des procédures fiscale](https://www.legifrance.gouv.fr/affichCodeArticle.do?idArticle=LEGIARTI000038001715\&cidTexte=LEGITEXT000006069583\&dateTexte=20181231) précise que la réutilisation du jeu de données « [Demandes de valeurs foncières](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres/) » ne peut avoir ni pour objet ni pour effet de permettre la ré-identifications des personnes liés à des transactions immobilières.
{% endhint %}

## Description du modèle de données <a href="#description-du-modele-de-donnees" id="description-du-modele-de-donnees"></a>

{% hint style="info" %}
**Eclairage : Schéma de données VS Modèle de données**

S'ils peuvent être utilisés dans des contextes proches, les termes "schéma" et "modèle" sont bien différents :

* un schéma décrit la structure d'un fichier (ses champs et leur format).
* un modèle décrit la structure logique du jeu de données sous la forme d'objets (ou entités) et de relations (ou associations). Les objets sont définis par une liste d'attributs.&#x20;

Les champs d'un schéma sont la traduction physique des attributs des entités du modèle. Le modèle de données est avant tout un outil de dialogue entre les différents intervenants.&#x20;
{% endhint %}

> Exemple : Dans le [jeu de données des IRVE](https://schema.data.gouv.fr/etalab/schema-irve-statique/) (infrastructures de recharge des véhicules électriques), on peut identifier que:
>
> * les champs "id\_station\_itinerance" et "nom\_station" correspondent à des attributs d'une même entité "station",
> * les champs "id\_pdc\_itinerance" et "puissance nominale" correspondent à des attributs d'une même entité "point de charge".
>
> Une "station" contient un ou plusieurs "point de charge" (relation entre les deux entités).

Il est conseillé de :&#x20;

* [ ] **Faire apparaître le modèle de données à l’aide de schémas et de tableaux**
* [ ] Si le jeu de données se compose de plusieurs entités, **faire apparaître les relations entre elles**.

Une fois le modèle établi, il convient de définir le découpage en fichiers. Il est possible de :&#x20;

* regrouper des entités dans un même fichier
* créer un fichier par entité

> **Exemple** : [La documentation](https://mtes-mct.github.io/secmar-documentation/schema.html) du [jeu de données des opérations de sauvetage en mer](https://www.data.gouv.fr/fr/datasets/operations-coordonnees-par-les-cross/) décrit le modèle de données utilisé. Ce modèle de données permet de comprendre rapidement les relations qui unissent les différentes entités du jeu de données. Dans cet exemple, il a été choisi d'associer un fichier par entité.

<figure><img src="https://guides.etalab.gouv.fr/assets/img/schema_secmar.37dd98f3.png" alt=""><figcaption><p>Modèle de données du jeu de données des opérations de sauvetage en mer</p></figcaption></figure>

## Description du schéma de données <a href="#description-du-schema-de-donnees" id="description-du-schema-de-donnees"></a>

Si vous publiez des données tabulaires, il est conseillé de produire un tableau récapitulatif indiquant, pour chaque colonne :&#x20;

* [ ] **le nom de la colonne**
* [ ] **son type de données** (entier, chaîne de caractères, nombre décimal, etc.)
* [ ] **la description de la donnée contenue dans cette colonne**
* [ ] **une ou plusieurs valeurs d’exemple**

Cela constituera une base solide en vue de la création d'un schéma de données, dont le processus est détaillé [ici](../maitriser-les-schemas-de-donnees/creer-un-schema-de-donnees/).

> **Exemple :** La documentation du [jeu de données des opérations de sauvetage en mer](https://www.data.gouv.fr/fr/datasets/operations-coordonnees-par-les-cross/) présente un tableau récapitulatif des différentes colonnes. La description des champs permet de faire le lien avec le fichier de données, ce qui facilite la lecture des données.&#x20;

<figure><img src="https://guides.etalab.gouv.fr/assets/img/table_secmar.561dfb7c.png" alt=""><figcaption><p>Description du schéma de données du jeu de données des opérations de sauvetage en mer</p></figcaption></figure>

Les termes employés dans un jeu de données sont propres à un environnement métier.&#x20;

S’il existe des termes complexes ou des énumérations, il est conseillé de :&#x20;

* **Fournir un lexique de ces valeurs**

Cet effort de définition fait gagner un temps considérable au réutilisateur et permet de prévenir des contre-sens dans l’exploitation des données.

> **Exemple :** La base de données de [demande de valeur foncière](https://www.data.gouv.fr/fr/datasets/demandes-de-valeurs-foncieres/) recense l’ensemble des transactions immobilières intervenues au cours des cinq dernières années. \
> Le vocabulaire utilisé dans ce jeu de données est issu d’un environnement administratif, parfois difficile à appréhender. La Direction générale des Finances publiques met à disposition une [documentation](https://static.data.gouv.fr/resources/demande-de-valeurs-foncieres/20190419-091745/notice-descriptive-du-fichier-dvf.pdf) qui comprend notamment un lexique de définition des termes rencontrés. Ce lexique facilite l’appropriation et la réutilisation des données par des acteurs tiers. ![Lexique des données du jeu de données Demande de valeur foncière](https://guides.etalab.gouv.fr/assets/img/lexique_dvf.64d1e5cc.png)

## Description des métadonnées <a href="#description-des-metadonnees" id="description-des-metadonnees"></a>

{% hint style="info" %}
**Lexique : Métadonnée**

Une métadonnée est une donnée qui décrit ou définit une autre donnée.&#x20;

Dans la vie courante, l’étiquette d’un produit fournit des informations/métadonnées sur le produit (origine, composition, date de péremption, etc.). Appliqué aux jeux de données, les métadonnées sont des descriptions normalisées du contenu du jeu.
{% endhint %}

Des formats standards de métadonnées existent afin de faciliter leur collecte, leur recherche et leur traitement automatique.&#x20;

Sur data.gouv.fr, il est possible de renseigner directement les métadonnées d’un jeu de données. Les métadonnées retenues sont les suivantes :

* Titre
* Sigle
* Description
* Licence
* Fréquence de mise à jour
* Mots clés
* Couverture temporelle
* Couverture spatiale
* Granularité spatiale
* Mode brouillon

La description des métadonnées apportera à un jeu de données une meilleure visibilité sur les catalogues.

## Description des changements majeurs <a href="#description-des-changements-majeurs" id="description-des-changements-majeurs"></a>

En pratique, il est souhaitable que le modèle de données et la nature de vos données n’évoluent pas au fil du temps.&#x20;

Toutefois, des changements dans la structure des données, dans le mode de collecte ou dans les dispositions réglementaires peuvent affecter le jeu de données.&#x20;

Dans cette situation, il est conseillé de **tenir une liste de ces changements**

Cette liste peut faire figurer :&#x20;

* la date
* la version des données (si vous versionnez vos données)
* la nature du changement

Si nécessaire, il est possible d’indiquer des liens, comme par exemple lorsque des changements sont introduits par une modification du code de transformation des données.

> **Exemple :** [La documentation](https://mtes-mct.github.io/secmar-documentation/CHANGELOG.html) du [jeu de données des opérations de sauvetage en mer](https://www.data.gouv.fr/fr/datasets/operations-coordonnees-par-les-cross/) comporte une section “Changement sur le jeu de données”. Cette section référence les changements du jeu de données en renseignant les informations suivantes :
>
> * La date du changement
> * La nature du changement
> * Les liens associés au changement
>
> &#x20;![Liste des modifications réalisées sur le jeu de données SECMAR](https://guides.etalab.gouv.fr/assets/img/maj_secmar.02c31ca5.png)

## Points de contact <a href="#points-de-contact" id="points-de-contact"></a>

Les réutilisateurs des données peuvent avoir des questions à propos des fichiers mis à disposition.

Il est conseillé de **proposer un espace d’échange entre les producteurs et réutilisateurs des données** : il est préférable que cet espace d’échange soit public afin qu’il puisse bénéficier aux personnes qui auraient des questions similaires.&#x20;

La collecte des retours d’usage permettra d’améliorer votre documentation de manière incrémentale.
