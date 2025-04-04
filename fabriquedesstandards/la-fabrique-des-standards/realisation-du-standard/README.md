---
cover: ../../.gitbook/assets/Gitbook bandereau6.png
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: true
---

# Réalisation du standard

**Le groupe de travail a pour mission d'organiser un travail collaboratif pour élaborer un standard qui fasse consensus.**

***

## <mark style="background-color:purple;">Actions de la phase</mark>

{% stepper %}
{% step %}
### <mark style="color:purple;">PROCESSUS D'ÉLABORATION DU STANDARD</mark>

* Le standard prend la forme d'**un document** sur la base du modèle de standard proposé par le CNIG (cf. les ressources utiles de cette page), il peut éventuellement contenir un schéma au format attendu par le site schema.data.gouv (voir [le modèle proposé](https://github.com/cnigfr/cnig-template) sur Github).
* **Les modalités de travail** pour la rédaction du standard sont libres. Généralement, il s’agit de réunions plénières et régulières lors desquelles les avancées sont présentées et les points de fond sont discutés. Entre ces réunions, les membres contribuent à la rédaction du document de leur côté ou lors de réunions organisées en sous-groupes.
* **Les comptes-rendus** des travaux réalisés en groupe de travail doivent être publiés à la suite de chaque réunion plénière sur [le site du CNIG](https://cnig.gouv.fr/les-standards-cnig-a18959.html#H_Standards-CNIG-et-reglementation). L’animateur du groupe de travail veille à leur bonne publication. Cela n’est pas obligatoire pour les réunions en sous-groupes : les conclusions de ces réunions sont généralement présentées lors des réunions plénières du GT et figurent donc dans leur compte-rendus.&#x20;
* **Des tests** peuvent être réalisés en cours d’élaboration du standard.\
  Un dispositif de prototypage est alors créé par des membres du groupe de travail grâce à la création de jeux de données et d'un protocole pour tester les standards auprès des personnes qui les consultent. Certains outils comme [Validata ](https://validata.fr/)(OpenDataFrance) peuvent être utiles lors de cette phase.&#x20;
* Si besoin, **des points d’étapes** peuvent être faits en commission des standards.

{% hint style="info" %}
**Comment nommer un standard ?**&#x20;

Le CNIG impose uniquement que le nom du standard soit au format "standard CNIG \<nom de la thématique>". Ce format insiste sur le fait qu'il s'agit d'un standard, c'est à dire qu'il résulte d'un consensus, et qu'il a été adopté par le CNIG. Le nom de la thématique est libre, mais il convient de garder en tête qu'il doit :&#x20;

* être suffisamment **évocateur** pour être facilement retrouvé,&#x20;
* reprendre les termes communs sur la thématique pour faciliter la **découvrabilité** du standard (en reprenant le nom d'un plan national, d'un texte réglementaire, d'un système d'information, etc.),&#x20;
* être assez **clair** pour que l'on comprenne de quoi il s'agit.&#x20;
{% endhint %}

### <mark style="background-color:green;">Quelques conseils sur …</mark>

<table data-card-size="large" data-view="cards" data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td>... <mark style="color:green;"><strong>Le travail de rédaction</strong></mark></td><td><ul class="contains-task-list"><li><input type="checkbox">Considérer le présentiel lorsque c’est possible, cela peut aider à mobiliser les participants, </li></ul></td><td><ul class="contains-task-list"><li><input type="checkbox">Se focaliser sur les priorités (modèle conceptuel de données, cas d'usage, outils), notamment en cas de ressources limitées,</li><li><input type="checkbox">Détailler le contexte de mise en œuvre du standard et les points d'attention à avoir,</li><li>Veiller à la cohérence avec le « métier » et prendre garde à un excès de rigorisme sur la modélisation des données,</li><li>Mettre à disposition un guichet unique et une plateforme de recueil des besoins,</li><li>Recourir aux expérimentations sur les premières versions, tenir compte des retours du terrain et être réactif dans les corrections à apporter.</li></ul></td></tr><tr><td>... <mark style="color:green;"><strong>Les sujets techniques</strong></mark></td><td><ul class="contains-task-list"><li><input type="checkbox">Conserver une certaine souplesse dans la conception du modèle de données afin de s'adapter aux différents SI,</li></ul></td><td><ul class="contains-task-list"><li><input type="checkbox">Ne pas dupliquer les référentiels, mais s'appuyer sur eux (via des clés externes),</li><li><input type="checkbox">Faire preuve de pragmatisme : il peut être préférable de renoncer à certaines données au profit d'autres plus essentielles,</li></ul><ul class="contains-task-list"><li>Illustrer les utilisations du modèle par des cas d'usage et du code informatique pour en faciliter l'appropriation,</li><li>Prendre en compte les contraintes des systèmes d'information, notamment géographiques, des producteurs et gestionnaires de données,</li><li>Encourager le développement de l'initiative privée tout en favorisant les solutions open source.</li></ul></td></tr></tbody></table>

### <mark style="background-color:blue;">Bonnes pratiques bonus :</mark>&#x20;

* Concevoir le standard de telle sorte à ce qu’il permette de limiter l’empreinte environnementale des données (en utilisant une maille géographique et un pas temporel adaptés, en évitant les champs redondants, en utilisant des types de données frugaux, etc.). Plus d’informations dans [le référentiel GreenData d’OpenDataFrance](https://opendatafrance.gitbook.io/greendata-pour-un-impact-maitrise-des-donnees),
* Documenter la durée des étapes en vue de la présentation à la Commission des standards où un retour sur la démarche sera attendu (cela permettra de cibler les étapes où cette procédure peut être améliorée).
{% endstep %}

{% step %}
### <mark style="color:purple;">CAHIER DES CHARGES A RESPECTER</mark>

**Les standards du CNIG doivent obligatoirement détailler :**&#x20;

* [ ] Leur raison d’être (enjeux, objectifs, réglementation, etc.),
* [ ] La méthodologie d’élaboration suivie (composition du GT, étapes suivies, etc.),&#x20;
* [ ] Leurs conditions d’utilisation (destinataires, cas d’usage, applications, etc.),
* [ ] Les concepts utilisés (définitions, ontologies, standards liés, systèmes de référence, etc.),&#x20;
* [ ] Le modèle conceptuel de données,
* [ ] Les règles concernant les données et métadonnées (qualité, application d’INSPIRE, etc.).

**Additionnellement, le standard peut contenir :**&#x20;

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

***



## <mark style="background-color:purple;">Ressources utiles</mark>

### \[:construction:] Modèle de standard proposé par le CNIG

_\[En cours de construction . Le document de travail est accessible ici :_ [_modèle de standard_](https://drive.google.com/drive/folders/1OxxgZdZpFHihiYwPq-HMMM5tA68w3JKj?usp=drive_link)_]_

### Modèle de compte rendu de réunion&#x20;

{% file src="../../.gitbook/assets/GT CNIG - Modèle de CR de réunion.docx" %}
_\[Le document de travail peut être trouvé ici :_ [_modèle de CR_](https://docs.google.com/document/d/1mrHyk5EQ4-D4WEwLUXU3g-6jt-JE3VW5/edit?usp=drive_link\&ouid=116276220921119561432\&rtpof=true\&sd=true)_]_
{% endfile %}

### Exemple de données de test

Les schémas répertoriés sur schema.data.gouv sont généralement pourvu d'un échantillon de données de test, comme c'est le cas pour le [schéma Friches](https://schema.data.gouv.fr/cnigfr/schema-friches/).

{% embed url="https://github.com/cnigfr/schema-friches/blob/main/fichier-valide.csv" %}

### \[:construction:] Autres outils proposés par la Dinum

{% embed url="https://www.numerique.gouv.fr/dinum/" %}

###

***

## <mark style="background-color:purple;">Foire aux questions</mark> ↓

<details>

<summary>Comment référencer le standard sur schema.data.gouv ?</summary>

Le référencement sur schéma.data.gouv n’est pas automatique. Il est nécessaire de demander à l’équipe de la DINUM de le réaliser en suivant les étapes suivantes :&#x20;

* Sur la page Github de schema.data.gouv, [créer une “issue”](https://github.com/datagouv/schema.data.gouv.fr/issues/new/choose), et sélectionner “Référencer un schéma”,&#x20;
* Remplir le modèle fourni (sans modifier les titres indiqués par les symboles #),

{% hint style="info" %}
**Note** : pour vous familiariser avec la syntaxe markdown, [ce guide publié par Github ](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)peut être utile.

* Cliquer sur “Create”,
* Attendre le retour de la DINUM en commentaire de l’issue créée et prendre en compte les suggestions (il peut être nécessaire de mettre à jour votre abonnement aux alertes de github, ou de vous connecter régulièrement au site).
{% endhint %}

</details>

<details>

<summary>Comment publier un compte rendu (CR) de réunion ?</summary>

Le compte rendu de réunion est rédigé par les animateurs du GT quelques jours après la réunion (voir le modèle proposé plus haut). Il est d'abord soumis au groupe de travail pour relecture sous un délai raisonnable (une semaine convient) à indiquer aux membres.&#x20;

{% hint style="info" %}
A noter que le CNIG ne propose pas d’outils de travail collaboratif en ligne. Les outils gratuits permettent généralement de répondre aux besoins des GT lorsque les institutions d’appartenance des animateurs ne peuvent pas mettre ces services à disposition (en prêtant attention à la protection des données confidentielles avec ces outils).
{% endhint %}

Après avoir tenu compte des retours, le CR est publié dans sa version finale dans l'espace de travail du GT (Github ou autre espace partagé) et sur la page du GT du site du CNIG. Pour cela, le CR doit être envoyé au secrétariat général du CNIG. &#x20;

Les animateurs informent ensuite sur la publication du CR :&#x20;

* le GT,&#x20;
* les personnes à informer au sein du CNIG,&#x20;
* les personnes externes concernées (comme la hiérarchie des animateurs),
* le secrétariat général si cela n'a pas déjà été fait (notamment pour proposer que l'information soit relayée dans l'infolettre du CNIG).

</details>

<details>

<summary>[<span data-gb-custom-inline data-tag="emoji" data-code="1f6a7">🚧</span>] Qui crée le dispositif de prototypage ? </summary>

#### _\[_:construction: _en construction_ :construction:_]_ <a href="#comment-gerer-github" id="comment-gerer-github"></a>

</details>

<details>

<summary>[<span data-gb-custom-inline data-tag="emoji" data-code="1f6a7">🚧</span>] Comment créer le dispositif de prototypage ? </summary>

#### _\[_:construction: _en construction_ :construction:_]_ <a href="#comment-gerer-github" id="comment-gerer-github"></a>

</details>

***



## Retour à la page d'accueil ↓

{% content-ref url="../" %}
[..](../)
{% endcontent-ref %}

## Page précédente et page suivante ↓
