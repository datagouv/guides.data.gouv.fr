# Structurer un jeu de données

{% hint style="success" %}
Les jeux de données qui ont vocation à circuler seront réutilisés par des acteurs tiers qui ne connaissent pas l’environnement de votre organisation.&#x20;

Il est nécessaire de proposer une structure de jeu de données compréhensible et appropriable par tous.
{% endhint %}

Deux approches sont possibles pour structurer un jeu de données, selon le cas de figure dans lequel la structure se situe :&#x20;

* **Cas 1 : La structure de vos données ne correspond à aucun schéma de données existant** : un travail de modélisation est nécessaire en amont de la création du jeu de données.
* **Cas 2 : La structure de vos données correspond à un schéma de données existant.**

{% tabs %}
{% tab title="Cas 1" %}
## Cas 1 : La structure de vos données ne correspond à aucun schéma de données existant <a href="#cas-2-la-structure-de-vos-donnees-ne-correspond-a-aucun-schema-de-donnees-existant" id="cas-2-la-structure-de-vos-donnees-ne-correspond-a-aucun-schema-de-donnees-existant"></a>

Il est nécessaire de réfléchir en amont à la meilleure structure pour vos données.

{% hint style="info" %}
Tant que les données de votre structure sont dans un environnement logiciel, leur usage reste adapté à des problématiques métiers spécifiques.

L’ouverture de ces données en dehors de leur environnement impose de **structurer le jeu de données en fonction des attentes des réutilisateurs** et non plus en fonction des besoins propres à l’organisation.
{% endhint %}

Quelques bonnes pratiques vous permettront de bien structurer votre jeu de données :&#x20;

### Soigner le contenu du jeu de données <a href="#le-contenu-du-jeu" id="le-contenu-du-jeu"></a>

#### Les champs du jeu de données <a href="#le-titre-du-jeu-de-donnees" id="le-titre-du-jeu-de-donnees"></a>

Il est conseillé de :&#x20;

* **Occulter l’ensemble des colonnes dont les champs contiennent des données couvertes par un secret légal** (cf. [guide juridique](https://guides.etalab.gouv.fr/juridique)) ;
* **Occulter l’ensemble des colonnes dont les champs contiennent des données à caractère personnel** dont la publication n’est pas nécessaire à l’information du public (cf. [guide juridique](https://guides.etalab.gouv.fr/juridique)) ;
* **Privilégier la présence de variables pivots** : ces variables proposent des identifiants communs qui permettent de lier plusieurs jeux de données entre eux (ex. le numéro SIRET de la base Sirene) (cf. page [Lier les données à un référentiel](https://guides.etalab.gouv.fr/qualite/lier-les-donnees-a-un-referentiel)).

#### L’entête des colonnes (pour le format tabulaire) <a href="#l-entete-des-colonnes-pour-le-format-tabulaire" id="l-entete-des-colonnes-pour-le-format-tabulaire"></a>

{% hint style="info" %}
Dans un fichier tabulaire, la première ligne du fichier peut être utilisée pour nommer chaque colonne et donner des informations sur les données associées.&#x20;
{% endhint %}

Il est conseillé de&#x20;

* Donner **un nom de colonne explicite** ;&#x20;
* Donner **un nom de colonne sans majuscule, abréviation, accents, ni espaces** (préférez le caractère `_`) afin de faciliter la manipulation des fichiers.

#### Gestion des champs non attribués <a href="#gestion-des-champs-non-attribues" id="gestion-des-champs-non-attribues"></a>

Il est possible que certaines occurrences d’un champ d'un fichier ne soit pas attribuées.&#x20;

Il convient de :&#x20;

* **Laisser ces occurrences vides plutôt que d’attribuer la valeur 0** (ou une autre valeur par défaut) : le zéro correspond à une valeur, qui peut dénaturer le sens de votre fichier.

#### Le titre du jeu de données <a href="#le-titre-du-jeu-de-donnees" id="le-titre-du-jeu-de-donnees"></a>

Il est recommandé de choisir un titre qui doit pouvoir renseigner n’importe quel réutilisateur sur le contenu du fichier. Pour cela, il est recommandé de :&#x20;

* **Ne pas donner un titre trop générique** qui obligerait le réutilisateur à ouvrir le jeu de données pour comprendre son contenu (i.e. “liste.csv” ou encore “balance comptable” sans indiquer l’organisation concernée) ;
* **Ne pas donner un titre trop long** qui rendrait la manipulation du fichier difficile (i.e. le titre du jeu de données “Fichiers consolidés des données essentielles de la commande publique” est suffisamment générique pour ne pas revenir sur toutes les sources de données utilisées pour agréger le jeu de données) ;
* **Ne pas donner un titre contenant des accents ou caractères spéciaux** qui poseraient des problèmes d’interopérabilité des fichiers ;
* **Ne pas donner de titre trop technique** issu de nomenclatures métier.

#### L’encodage du fichier <a href="#l-encodage-du-fichier" id="l-encodage-du-fichier"></a>

{% hint style="info" %}
**Lexique : Encodage**

L’encodage d’un fichier est la norme utilisée pour coder chaque caractère par une suite de 0 et de 1 compréhensible par une machine.

Lorsque l’encodage est mal choisi, le réutilisateur des données est souvent contraint de convertir le fichier, notamment afin de faire apparaître les accents et caractères spéciaux.
{% endhint %}

**Il est conseillé de :**&#x20;

* **Utiliser l’encodage UTF-8** : il permet d’encoder l’ensemble des caractères du répertoire universel de caractères codés (notamment les caractères contenant des accents ou des caractères spéciaux).

#### Le séparateur (pour le format tabulaire) <a href="#le-separateur-pour-le-format-tabulaire" id="le-separateur-pour-le-format-tabulaire"></a>

{% hint style="info" %}
Dans un fichier tabulaire, le séparateur permet de structurer les données sous forme de cellules.&#x20;
{% endhint %}

Il est conseillé d'**utiliser la virgule comme séparateur**

{% hint style="warning" %}
**Séparateurs décimaux**

Dans un fichier CSV, la virgule n’est pas considérée comme un séparateur décimal. Si votre fichier contient des valeurs décimales, il est nécessaire d’encapsuler chaque champ entre des guillemets.&#x20;

La plupart des tableurs (Excel, OpenOffice Calc, etc) proposent l’encapsulement des champs entre guillemets.&#x20;

Une seconde solution consiste à convertir l’ensemble des virgules utilisées pour des valeurs décimales par un point.
{% endhint %}

#### Granularité du jeu de données

Il est important de mener une réflexion sur la granularité du jeu de données.

_Faut-il proposer des données fines ou agrégées ? Faut-il proposer un export quotidien, mensuel, trimestriel ou annuel ?_ Ces questions doivent être posées en amont de l’automatisation des exports.&#x20;

Il est conseillé de **mener un dialogue avec les réutilisateurs afin de comprendre leurs besoins** : certains utilisateurs peuvent souhaiter manipuler des données granulaires tandis que d’autres préfèrent disposer d’agrégats qui permettent une réutilisation simple et rapide. A minima, il est conseillé de proposer un fichier complet unique qui contient l’ensemble des données historiques.

### Choisir le format du jeu de données <a href="#le-choix-du-format-du-jeu-de-donnees" id="le-choix-du-format-du-jeu-de-donnees"></a>

Afin qu'un maximum d’utilisateurs puisse s’approprier les données, il est conseillé de les faire circuler dans un format :&#x20;

* **ouvert** : un format ouvert n’impose pas de spécifications techniques qui entraveraient l’exploitation des données (i.e. l’utilisation d’un logiciel payant) ;
* **aisément réutilisable** : un format aisément réutilisable sous-entend que toute personne ou machine peut réutiliser facilement le jeu de données ;
* **exploitable par un système de traitement automatisé** : un système de traitement automatisé permet de réaliser des opérations par des moyens automatiques, relatifs à l’exploitation des données (i.e. un fichier CSV est aisément exploitable par un système de traitement automatisé contrairement à un fichier PDF).

Il est possible de choisir parmi les formats ouverts et communément acceptés suivants :&#x20;

| Type de données                | Formats conseillés                                                                                                                          | Description                                                                                                                                                                                                                             | Documentation                                                                                                                     |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Données tabulaires             | CSV                                                                                                                                         | Un fichier CSV est constitué de lignes de données, où chaque champ est séparé par une virgule. Ce format est le standard le plus réutilisable, car ouvert et facilement exploitable par une machine.                                    | [Ici](https://opendatafrance.gitbook.io/odl-ressources/fiches-pratiques/premiers-pas/produire-un-fichier-csv-de-qualite#contexte) |
| Données statiques de transport | GTFS/NeTEx                                                                                                                                  | Le format GTFS est le format le plus utilisé en France par les services de mobilité d’information voyageur. Le format NeTEx est le format de référence européen qui vise l’interopérabilité des données entre États membres.            | [Ici](https://transport.data.gouv.fr/guide)                                                                                       |
| Données géographiques          | GeoJSON, Shapefile, MapInfo MIF/MID, MapInfo TAB et GML, pour les vecteurs / ECW, JPEG2000 et GeoTIFF, pour les données pixelisées (raster) | Les données géographiques sont organisées sous forme d’ensemble de données hiérarchisées. Les formats proposés sont conçus spécifiquement pour être largement exploitables et être intégrés facilement dans des outils de cartographie. | [Ici](https://geo.data.gouv.fr/fr/doc/publish-your-data)                                                                          |
| Données hiérarchiques          | JSON / XML / YAML                                                                                                                           | Les données hiérarchiques décrivent des relations hiérarchiques entre différentes données. Le format JSON est préconisé lorsque les données sont liées entre elles sous forme d’arbres verticaux.                                       | indisponible                                                                                                                      |
{% endtab %}

{% tab title="Cas 2" %}
## Cas 2 : La structure des données correspond à un schéma de données existant

{% hint style="info" %}
**Lexique : Schéma de données**

Un schéma de données est un document qui permet de décrire de manière précise et univoque les différents champs et valeurs possibles qui composent un fichier.

Il permet notamment de valider qu’un fichier est conforme à une structure communément partagée, de générer de la documentation automatiquement, de générer des jeux de données d’exemple ou de proposer des formulaires de saisie standardisés.&#x20;

Ces schémas facilitent la montée en qualité et le croisement des données proposées en open data, surtout lorsque plusieurs producteurs de données sont amenés à produire un même jeu de données.



➡️ **Pour plus de détails sur les schémas de données, consultez la section "Les schémas de données"**
{% endhint %}

### **Identifier un schéma de données déjà existant**

Il est possible d'identifier un schéma de données déjà existant **en consultant le site schema.data.gouv.fr**, qui référence une liste de schémas de données existants. Le site offre aussi la possibilité à tout utilisateur de soumettre de nouveaux schémas de données.&#x20;

Lorsque les données que vous souhaitez faire circuler correspondent à un schéma existant, **il est conseillé de l’appliquer au plus près**.

### **Produire des données conforme à un schéma de données identifié**

Si les données ne sont pas extraites d’un système d’information mais saisies manuellement, **il est possible d'utiliser** [**l’outil publier.etalab.studio**](https://publier.etalab.studio/) qui permet, à partir d’un schéma de données sélectionné, de saisir les valeurs de chaque information et ainsi de produire un fichier exhaustif et conforme.

{% hint style="info" %}
**Guide : Utiliser publier.etalab.studio pour saisir, valider et publier des données de qualité**

Cet outil vous permet de créer un fichier CSV en vous assurant qu'il est conforme à un schéma, c'est-à-dire que ses données sont complètes, valides et structurées.



Les étapes à suivre sont les suivantes :&#x20;

1. **Sélectionnez le schéma** qui vous intéresse dans la liste déroulante (les schémas disponibles sont ceux référencés sur [schema.data.gouv.fr](https://schema.data.gouv.fr/)).
2. **Produisez vos données. Trois modes de production sont possibles :**&#x20;
   * **Téléversez (uploadez)** votre fichier si les données sont déjà consolidées au bon format ;&#x20;
   * **Saisissez vos données dans un formulaire** à l'aide des descriptions des différents champs et des valeurs d'exemples : les champs indiqués par un astérisque rouge doivent obligatoirement être renseignés au moment de la saisie
     * Une fois votre formulaire valide, les valeurs apparaissent sous la forme d'une ligne dans un tableau récapitulatif
     * Vous pouvez alors choisir d'ajouter une ou plusieurs lignes ou télécharger le fichier CSV correspondant au tableau récapitulatif
   * **Saisissez vos données sur un tableur en ligne**
3. La conformité de vos données par rapport au schéma choisi est vérifiée/validée. En cas d'erreur de validation, vous pouvez les **corriger**.
4. Une fois les données conforme au schéma correspondant, **publiez-les sur data.gouv.fr** grâce à un formulaire de publication simplifié permettant une authentification tierce.&#x20;


{% endhint %}

<figure><img src="../../../.gitbook/assets/Capture d’écran 2023-04-25 à 18.05.30 (1).png" alt=""><figcaption></figcaption></figure>

### **Valider la conformité d’un fichier avec un schéma de données**

Pour valider la conformité d'un fichier avec un schéma de données, il est possible de :&#x20;

* **Utiliser la solution** [**Validata**](https://validata.fr/) : vous pouvez valider la conformité de votre fichier à un schéma parmi la liste déroulante ou via une URL. Vous pouvez ensuite faire valider ce fichier, soit en l'important au format csv, soit en renseignant également son URL.

![Capture d'écran du menu de validata](https://guides.etalab.gouv.fr/assets/img/validata.f6a9dd72.png)

Sur l'interface d'administration de data.gouv.fr, il est possible d'indiquer que votre fichier correspond à un schéma.&#x20;

* Lorsque vous déposez ou éditez une ressource, vous pouvez sélectionner le schéma correspondant à vos données dans une liste déroulante.

![Capture d'écran de la sélection d'un schéma depuis l'interface d'administration de data.gouv.fr](https://guides.etalab.gouv.fr/assets/img/selection-schema.d958a2c6.png)

* Le fait d'indiquer que votre ressource est censée respecter un schéma permet de bénéficier de vérifications de la qualité des données, d'indiquer aux réutilisateurs que vos données respectent un référentiel, ainsi que de contribuer aux fichiers agrégés (i.e. [pour les données IRVE](https://www.data.gouv.fr/fr/datasets/fichier-consolide-des-bornes-de-recharge-pour-vehicules-electriques/)).

![Capture d'écran de data.gouv.fr des informations disponibles sur la page d'un jeu de données lorsqu'un schéma est spécifié sur une ressource](https://guides.etalab.gouv.fr/assets/img/modal-schema.7ecaa269.png)

D'autres solutions en dehors de data.gouv.fr existent : des solutions disponibles en anglais comme [goodtables.io](http://goodtables.io/) ou [CSV Lint](https://csvlint.io/) proposent des validateurs de jeux de données.&#x20;

Il est aussi possible d’intégrer une fonction de validation d’un jeu directement dans la procédure de publication (exemple : les données d’adresses locales qui font l’objet d’une validation directement sur le site [adresse.data.gouv.fr](https://adresse.data.gouv.fr/)).&#x20;
{% endtab %}
{% endtabs %}



