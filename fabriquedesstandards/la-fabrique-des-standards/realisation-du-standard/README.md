---
cover: ../../.gitbook/assets/Gitbook bandereau6.png
coverY: 0
---

# Réalisation du standard

**Le groupe de travail a pour mission d'organiser un travail collaboratif pour élaborer un standard qui fasse consensus.**

***

## <mark style="background-color:purple;">Actions de la phase</mark>

{% stepper %}
{% step %}
### <mark style="color:purple;">PROCESSUS D'ÉLABORATION DU STANDARD</mark>

* Le standard prend la forme d'**un document** sur la base du modèle de standard proposé par le CNIG dans [les ressources utiles de cette page](./#modele-de-standard-propose-par-le-cnig). Il est accompagné d'un dépôt Github suivant [le modèle proposé](https://github.com/cnigfr/cnig-template), et il peut éventuellement contenir un schéma au format attendu par le site schema.data.gouv, comme décrit par [ce modèle](https://github.com/cnigfr/cnig-template/blob/345df0c460fe2bcaa6b1377eeec97d069cce2890/schema/schema.json).
* **Les modalités de travail** pour la rédaction du standard sont libres. Généralement, il s’agit de réunions plénières et régulières lors desquelles les avancées sont présentées et les points de fond sont discutés. Entre ces réunions, les membres contribuent à la rédaction du document de leur côté ou lors de réunions organisées en sous-groupes.
* **Les comptes-rendus** des travaux réalisés en groupe de travail doivent être publiés à la suite de chaque réunion plénière sur [le site du CNIG](https://cnig.gouv.fr/les-standards-cnig-a18959.html#H_Standards-CNIG-et-reglementation). L’animateur du groupe de travail veille à leur bonne publication. Cela n’est pas obligatoire pour les réunions en sous-groupes : les conclusions de ces réunions sont généralement présentées lors des réunions plénières du GT et figurent donc dans leur compte-rendus.&#x20;
* **Des tests** peuvent être réalisés en cours d’élaboration du standard.\
  Un dispositif de prototypage est alors créé par des membres du groupe de travail grâce à la création de jeux de données et d'un protocole pour tester les standards auprès des personnes qui les consultent. Certains outils comme [Validata ](https://validata.fr/)(créé par OpenDataFrance et Etalab) peuvent être utiles lors de cette phase.&#x20;
* Si besoin, **des points d’étapes** peuvent être faits en commission des standards.

{% hint style="info" %}
**Comment nommer un standard ?**&#x20;

Le CNIG impose uniquement que le nom du standard soit au format "standard CNIG \<nom de la thématique>". Ce format insiste sur le fait qu'il s'agit d'un standard, c'est à dire qu'il résulte d'un consensus, et qu'il a été adopté par le CNIG. Le nom de la thématique est libre, mais il convient de garder en tête qu'il doit :&#x20;

* être suffisamment **évocateur** pour être facilement retrouvé,&#x20;
* reprendre les termes communs sur la thématique pour faciliter la **découvrabilité** du standard (en reprenant le nom d'un plan national, d'un texte réglementaire, d'un système d'information, etc.),&#x20;
* être assez **clair** pour que l'on comprenne de quoi il s'agit.&#x20;

**Versionner un standard**&#x20;

La réflexion sur la gestion des versions doit avoir lieu dès la réalisation du standard. Vous pouvez vous inspirer de la méthodologie de gestion sémantique des versions [Semver](https://semver.org/lang/fr/) utilisée par schema.data.gouv.
{% endhint %}

### <mark style="background-color:green;">Quelques conseils sur …</mark>

<table data-card-size="large" data-view="cards" data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>... <mark style="color:green;"><strong>Le travail de rédaction</strong></mark></td><td><ul class="contains-task-list"><li><input type="checkbox">Considérer le présentiel lorsque c’est possible, cela peut aider à mobiliser les participants, </li></ul></td><td><ul class="contains-task-list"><li><input type="checkbox">Se focaliser sur les priorités (modèle conceptuel de données, cas d'usage, outils), notamment en cas de ressources limitées,</li><li><input type="checkbox">Détailler le contexte de mise en œuvre du standard et les points d'attention à avoir,</li><li>Veiller à la cohérence avec le « métier » et prendre garde à un excès de rigorisme sur la modélisation des données,</li><li>Mettre à disposition un guichet unique et une plateforme de recueil des besoins,</li><li>Recourir aux expérimentations sur les premières versions, tenir compte des retours du terrain et être réactif dans les corrections à apporter.</li></ul></td></tr><tr><td>... <mark style="color:green;"><strong>Les sujets techniques</strong></mark></td><td><ul class="contains-task-list"><li><input type="checkbox">Conserver une certaine souplesse dans la conception du modèle de données afin de s'adapter aux différents SI,</li></ul></td><td><ul class="contains-task-list"><li><input type="checkbox">Ne pas dupliquer les référentiels, mais s'appuyer sur eux (via des clés externes),</li><li><input type="checkbox">Faire preuve de pragmatisme : il peut être préférable de renoncer à certaines données au profit d'autres plus essentielles,</li></ul><ul class="contains-task-list"><li>Illustrer les utilisations du modèle par des cas d'usage et du code informatique pour en faciliter l'appropriation,</li><li>Prendre en compte les contraintes des systèmes d'information, notamment géographiques, des producteurs et gestionnaires de données,</li><li>Encourager le développement de l'initiative privée tout en favorisant les solutions open source.</li></ul></td></tr></tbody></table>

{% hint style="info" %}
### La cohérence sémantique : une évolution à prendre en compte

Il s’agit ici de répondre au besoin d'**interopérabilité sémantique**. Il convient d’urbaniser les standards de données, dans l’objectif de résoudre les conflits et incompatibilités avec d’autres standards ou logiciels métiers développés pour manipuler des données dont la modélisation est conforme à certains standards.&#x20;

En effet, le rôle de chaque organisation métier est de produire des modélisations de données propres à leurs vues métiers. Mais les standards ont vocation aussi à structurer une connaissance partagée de manière transverse aux métiers, et à en organiser la traduction dans les différentes modélisations  (bases de données relationnelles, classes d’objet et données attributives, modèle clé-valeur, etc.) présentes au sein des infrastructures de données afin d’en faciliter le partage, la circulation et la réutilisation.

S'arrêter à une seule vue métier ne permet pas une réelle capitalisation de la connaissance entre standards, ni ne permet de mesurer ou minimiser pour un métier particulier les surcoûts liés une modélisation unifiée.

> _Par exemple, mettre en évidence qu’un point de prélèvement d’eau en nappe est en même temps : un équipement pouvant faire l’objet d’une description technique et d’un acte administratif, un point d’alimentation en eau potable, objet de surveillance sanitaire, et un générateur de servitudes, objet d’actes réglementaires, permet d’articuler de manière optimum la gestion et l’utilisation des données issues de ces différents points de vue métiers, qui nomment et structurent différemment la même réalité._&#x20;

La démarche de standardisation doit donc permettre de faire converger ou articuler plusieurs standards en s’appuyant sur une analyse sémantique. Cette démarche s'appuie sur des référentiels sémantiques (des vocabulaires et des ontologies normalisés) aidant à l’analyse et à la conception des relations et des propriétés dans les modèles.

Le niveau sémantique ajouté en chapeau du niveau conceptuel (modélisation UML, ou équivalent) permettra de communiquer, capitaliser et mettre en cohérence les standards (mise en évidence des redondances, des concepts sous-entendus, des choix d’agrégation et de représentation implicites, etc.).&#x20;

Concrètement il s’agit de décrire la correspondance entre les informations structurelles de chaque entité. Cette correspondance ne se limite pas à un simple renommage des propriétés, mais explicite les liens entre informations qui peuvent être réparties différemment dans les entités. On peut aller jusqu'à déterminer des règles de transformation ou de calcul pour certaines propriétés.

En contrôlant grâce à cette méthode la réversibilité de l’information entre différents modèles métier (la préservation de la sémantique), il devient également possible de détecter et gérer les incohérences entre modèles, de mesurer les impacts en cas d’évolution d’un modèle, et de décider d’une renormalisation directe ou différée.&#x20;

Une fois cette étape réalisée, il devient possible de garantir que les ensembles de données provenant de différentes sources conformément aux différents standards urbanisés puissent être combinés et utilisés de manière cohérente.&#x20;

L'adoption des principes de données liées à l'aide de normes du Web sémantique telles que RDF (Ressource Description Framework), SPARQL et OWL (Web Ontology Language) permettra de rendre les ensembles de données standardisés lisibles par machine et interconnectés, facilitant ainsi une intégration plus poussée et la découverte automatisée des données.

Pour aller plus loin : voir [les ressources du SEMIC](https://interoperable-europe.ec.europa.eu/collection/semic-support-centre) (Semantic Interoperability Community de l'Union Européenne).
{% endhint %}

### <mark style="background-color:blue;">Bonnes pratiques bonus :</mark>&#x20;

* Concevoir le standard de telle sorte à ce qu’il permette de limiter l’empreinte environnementale des données (en utilisant une maille géographique et un pas temporel adaptés, en évitant les champs redondants, en utilisant des types de données frugaux, etc.). Plus d’informations dans [le référentiel GreenData d’OpenDataFrance](https://opendatafrance.gitbook.io/greendata-pour-un-impact-maitrise-des-donnees),
* Documenter les étapes en vue de la présentation à la Commission des standards où un retour sur la démarche sera attendu (cela permettra de cibler les étapes où cette procédure peut être améliorée).
{% endstep %}

{% step %}
### <mark style="color:purple;">CAHIER DES CHARGES A RESPECTER</mark>

Le standard doit respecter le modèle proposé (cf. les ressources utiles de cette page) et suivre les indications qui y sont données. Plus généralement, voici plusieurs recommandations ci-dessous.

**Les standards du CNIG doivent obligatoirement détailler :**&#x20;

* [ ] Leur raison d’être (enjeux, objectifs, réglementation, etc.),
* [ ] La méthodologie d’élaboration suivie (composition du GT, étapes suivies, etc.),&#x20;
* [ ] Leurs conditions d’utilisation (destinataires, cas d’usage, applications, etc.),
* [ ] Les concepts utilisés (définitions, ontologies, standards liés, systèmes de référence, etc.),&#x20;
* [ ] Le modèle conceptuel de données suivant le formalisme UML,
* [ ] Les règles concernant les données et métadonnées (qualité, application d’INSPIRE, etc.).

**Additionnellement, le standard peut être complété par :**&#x20;

* [ ] un schéma de données,&#x20;
* [ ] des éléments méthodologiques sur la collecte et l’utilisation des données,&#x20;
* [ ] des bonnes pratiques liées à la qualité des données et métadonnées,&#x20;
* [ ] tout autre sujet pertinent.
{% endstep %}

{% step %}
### <mark style="color:purple;">PROCESSUS DE RÉFÉRENCEMENT DU STANDARD</mark>

Dès son lancement, **un standard peut être référencé sur le site du CNIG et sur le site schema.data.douv.fr .**&#x20;

Pour être référencé, le standard doit être identifié sur [schema.data.gouv.fr ](https://schema.data.gouv.fr)avec le label "en construction".
{% endstep %}
{% endstepper %}

### <mark style="background-color:blue;">**Le rôle du secrétariat général du CNIG**</mark>

Lors du cadrage du GT, le secrétariat général vous accompagne pour :&#x20;

* la création du dépôt Github (si besoin),&#x20;
* le maintien de la page du GT sur le site du CNIG (publication des compte-rendus, annonce des réunions, etc.).

***



## <mark style="background-color:purple;">Ressources utiles</mark>

### Modèle de standard proposé par le CNIG

{% file src="../../.gitbook/assets/GT CNIG - Modèle de standard.docx" %}
_Modèle de standard_&#x20;
{% endfile %}

### Modèle de compte rendu de réunion&#x20;

{% file src="../../.gitbook/assets/GT CNIG - Modèle de CR de réunion (1).docx" %}
_Modèle de compte-rendu de réunion de GT_
{% endfile %}

### Exemple de données de test

Les schémas répertoriés sur schema.data.gouv sont généralement pourvu d'un échantillon de données de test, comme c'est le cas pour le [schéma Friches](https://schema.data.gouv.fr/cnigfr/schema-friches/).

{% embed url="https://github.com/cnigfr/schema-friches/blob/main/fichier-valide.csv" %}
_Exemple de données de test pour le standard Friches_
{% endembed %}

***

## <mark style="background-color:purple;">Foire aux questions</mark> ↓

<details>

<summary>Comment référencer le standard sur schema.data.gouv ?</summary>

L'annonce sur schéma.data.gouv n’est pas automatique. Il est nécessaire de demander à l’équipe de la DINUM de le réaliser en suivant les étapes suivantes :&#x20;

* Sur la page Github de schema.data.gouv, [créer une “issue”](https://github.com/datagouv/schema.data.gouv.fr/issues/new/choose), et sélectionner “Référencer un schéma”,&#x20;
* Remplir le modèle fourni (sans modifier les titres indiqués par les symboles #),

{% hint style="info" %}
**Note** : pour vous familiariser avec la syntaxe markdown, [ce guide publié par Github ](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)peut être utile.
{% endhint %}

* Cliquer sur “Create”,
* Attendre le retour de la DINUM en commentaire de l’issue créée et prendre en compte les suggestions (il peut être nécessaire de mettre à jour votre abonnement aux alertes de Github dans l'onglet "Notifications" des paramètres de votre compte, ou de vous connecter régulièrement au site).

</details>

<details>

<summary>Comment publier un compte rendu (CR) de réunion ?</summary>

Le compte rendu de réunion est rédigé par l'animateur du GT quelques jours après la réunion (voir le modèle proposé plus haut). Il est d'abord soumis au groupe de travail pour relecture sous un délai raisonnable (une semaine convient) à indiquer aux membres.&#x20;

{% hint style="info" %}
A l'heure actuelle le CNIG ne propose pas d’outils de travail collaboratif en ligne. Les outils gratuits de type suite bureautique en ligne ou autres permettent généralement de répondre aux besoins des GT lorsque les institutions d’appartenance des animateurs ne peuvent pas mettre ces services à disposition (en prêtant attention à la protection des données confidentielles avec ces outils).
{% endhint %}

Après avoir tenu compte les retours de ses relecteurs, le CR est publié dans sa version finale dans l'espace de travail du GT (Github ou autre espace partagé) et sur la page du GT du site du CNIG, par le secrétariat général du CNIG à qui il aura été transmis

L'animateur informe ensuite sur la publication du CR :&#x20;

* le GT,&#x20;
* les personnes à informer au sein du CNIG,&#x20;
* les personnes externes concernées (comme la hiérarchie des animateurs).

</details>

***



## Retour à la page d'accueil ↓

{% content-ref url="../../" %}
[..](../../)
{% endcontent-ref %}

## Page précédente et page suivante ↓
