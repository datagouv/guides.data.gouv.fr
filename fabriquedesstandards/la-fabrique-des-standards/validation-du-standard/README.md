---
cover: ../../.gitbook/assets/Bandereau87.png
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

# Validation du standard

**Avant sa publication le standard doit encore franchir différentes étapes, décrites ci-dessous.**

***

## <mark style="background-color:purple;">Actions de la phase</mark>

{% stepper %}
{% step %}
### <mark style="color:purple;">TEST DU STANDARD (facultatif)</mark>

Identifier un acteur volontaire pour tester concrètement le standard. Il est conseillé de vérifier que le test permet de vérifier de bout en bout l’efficacité et la clarté du standard (sa compréhension par les équipes métier, son implémentation par les équipes numérique, son intégration dans les outils, etc.). Ces tests doivent permettre de vérifier que le stade de “produit minimum viable” a été atteint, mais ne permettront pas de vérifier des objectifs plus poussés (comme des améliorations dans la découvrabilité des données, la réplicabilité des solutions, etc.). Les résultats de ces tests doivent être documentés.&#x20;

**Exemples :**&#x20;

* le standard risques - profil applicatif PPR testé par la DDT de l’Isère (voir ce [retour d’expérience dans une présentation](https://youtu.be/1-OFlNQiGtw?feature=shared\&t=3504)),
* le standard paysage testé par plusieurs collectivités (voir le [Compte-rendu GT du 19 mars 2024](https://cnig.gouv.fr/IMG/pdf/240319_cr_gt6_standard_paysages_diffusion.pdf) sur [la page du GT Paysages](https://cnig.gouv.fr/gt-paysages-a25941.html)). Plusieurs documents de travail du GT peuvent être utiles à titre d'exemple :&#x20;
  * [une présentation à destination des testeurs](https://github.com/cnigfr/schema-paysage/blob/main/test%20standard/2023.11.13%20Pr%C3%A9sentation%20Standard%20Paysage%20pour%20tests%20v1.3.pdf), leur donnant notamment des consignes,
  * [un modèle de rapport pour les testeurs ](https://github.com/cnigfr/schema-paysage/blob/main/test%20standard/231113_Rapport%20de%20test%20-%20formulaire%20v2023-11.pdf)visant à recueillir les résultats.
{% endstep %}

{% step %}
### <mark style="color:purple;">APPEL A COMMENTAIRES</mark>

L’appel à commentaires est une consultation publique. Il s'agit d'une étape indispensable avant la validation du standard par la commission des standards. L'appel à commentaires CNIG ne peut se dérouler qu’à la fin de la phase de rédaction du standard et des autres livrables éventuels (schéma, Github, annexes, documentation, etc.). L’appel à commentaires doit viser un public large, en s’assurant que les principaux intéressés en sont informés (parfois avant même le lancement pour s’assurer que cela sera pris en compte dans leur calendrier). Le traitement des commentaires peut représenter une charge importante pour les animateurs qu’il est préférable d’anticiper.

La démarche à suivre est détaillée dans [une page dédiée](https://app.gitbook.com/o/w6D6SnLwCXQaMMSzcTvp/s/weZQRU1RV5So9WzNyxlW/~/changes/17/la-fabrique-des-standards/validation-du-standard/realiser-un-appel-a-commentaires).
{% endstep %}

{% step %}
### <mark style="color:purple;">DERNIÈRES VÉRIFICATIONS</mark>

{% hint style="success" %}
#### Faire valider un standard : synthèse des conditions à respecter   <a href="#docs-internal-guid-665f0eed-7fff-c85b-bb50-7167a0448e9e" id="docs-internal-guid-665f0eed-7fff-c85b-bb50-7167a0448e9e"></a>

S’il est impossible de donner tous les critères de validation d’un standard étant donné la particularité de chacune des situations, une “obligation de moyens” est à respecter. Ces obligations sont les suivantes :&#x20;

* le **respect de la procédure** du CNIG décrite ici ;&#x20;
* **l’ouverture** et **la représentativité** du groupe de travail et **l’atteinte d’un consensus** sur le standard obtenu ;
* la soumission du standard à **un appel à commentaires** et la prise en compte des retours ;
* **l’utilisation** (conforme) **des méthodes et modèles** proposés par la Fabrique des standards ;
* plusieurs conditions additionnelles :&#x20;
  * publication des documents de travail du GT (mandat, CR des réunions, etc.),&#x20;
  * publication du standard sur le site du CNIG sous une licence ouverte,
  * publication sur schema.data.gouv.
{% endhint %}
{% endstep %}

{% step %}
### <mark style="color:purple;">VALIDATION DU STANDARD</mark>

Le projet de standard est soumis à validation à la **Commission des Standards** puis au **Conseil plénier du CNIG.**&#x20;

* **Présentation à la commission des standards**

[La commission des standards ](https://cnig.gouv.fr/commission-des-standards-a640.html)se réunit environ une fois par trimestre, il est donc préférable d’anticiper la date visée dans votre calendrier. Une fois la date identifiée, la commission doit être contactée pour inscrire la présentation du standard à son ordre du jour. Pour cela, il convient d’envoyer une demande à la présidente de la commission ou au secrétariat général en indiquant le lien vers le standard. Il sera également demandé de préparer une présentation. Aucun modèle n'est proposé pour cette présentation car nous vous encourageons à utiliser une identité visuelle pour le standard, ou à utiliser celle de votre institution d'appartenance. Voici les informations qu'il est conseillé de faire figurer dans cette présentation :&#x20;

* <mark style="background-color:blue;">Le contexte</mark>
  * **Définir les termes** si cela est nécessaires à la compréhension du sujet,
  * Présenter **le sujet**, **le contexte réglementaire**,&#x20;
  * Indiquer si la thématique possède un lien avec [**la directive INSPIRE**](https://cnig.gouv.fr/presentation-de-la-directive-a8991.html),
  * Exposer **les enjeux, problématiques et objectifs opérationnels** du standard.
* <mark style="background-color:blue;">Le groupe de travail</mark>&#x20;
  * Présenter **le pilote, les animateurs, les participants et les autres acteurs** impactés par la thématique,
  * Revenir sur **le déroulement des travaux du GT** et le calendrier suivi en donnant les dates les plus importantes (saisie du CNIG, passage dans les différentes commissions, appel à commentaire etc.),&#x20;
  * Présenter succinctement **les outils** utilisés.

{% hint style="success" %}
**Utiliser les phases détaillée dans cette documentation** dans la mesure du possible (émergence d'un besoin, exploration de l'existant, etc. jusqu'à la validation du standard). Cela permettra de vérifier leur pertinence, de donner des indications sur la durée de chacune des phases, et d'améliorer la procédure.
{% endhint %}

* <mark style="background-color:blue;">Le projet de standard</mark>&#x20;
  * Décrire **le standard**, à qui il s'adresse et ses cas d'usage,
  * Lister **les interactions** avec les standards et normes existants ou en projet,&#x20;
  * Indiquer **les limitations** du standard (ce qu'il ne couvre pas par exemple),
  * Présenter **le** **modèle conceptuel de données** dans les grandes lignes, **le catalogue d'objet**, **le schéma** de données éventuel, **l'éventuel jeu de données de test** construit et comment trouver ces documents,
  * Indiquer les ressources documentaires complémentaires.
* <mark style="background-color:blue;">La démarche suivie et les suites prévues</mark>
  * Décrire les **décisions et partis pris** par le GT lors de l'élaboration du standard présentant un intérêt pour la commission,&#x20;
  * Revenir sur **l'appel à commentaire** en décrivant la démarche suivie, les retours obtenus (leur nombre, leur contenu) et les conclusions tirées,
  * Donner les **perspectives** du GT pour la suite (comme les projets à venir fondés sur le standard, le travail de maintenance du standard, l'accompagnement au déploiement, etc.).

Suite à la présentation, la commission vote l’adoption du standard ou demande à ce que certaines modifications soient effectuées. Ces modifications ne nécessitent pas toujours un nouveau passage devant la commission avant la présentation au plénier (n’entraînant ainsi pas de retard pour l’adoption finale).&#x20;

* **Présentation au conseil plénier du CNIG**

Le standard doit être validé par [le conseil plénier](https://cnig.gouv.fr/conseil-plenier-a972.html) pour être formellement adopté par le CNIG. Lors du plénier, le standard n’est pas toujours présenté, mais il doit être décrit dans un dossier transmis en amont au conseil. Ce dossier est rédigé par le secrétariat général en lien avec l'animateur du GT (il se présente sous la forme du [modèle proposé plus bas](./#modele-de-dossier-de-presentation-en-plenier) pour information). Ce dossier sera transmis au conseil plénier par le secrétariat du CNIG, avec l'ensemble des pièces, 2 semaines avant la séance.&#x20;

Des questions ou demandes peuvent être formulées à l’oral par les membres du conseil. S'ils participent au conseil plénier, les animateurs du GT sont invités à répondre aux questions à ce moment-là, ou à prendre note des demandes pour modification ultérieure. Ici encore, si la présentation a été suffisamment anticipée, les retours du conseil ne bloquent généralement pas l’adoption du standard.
{% endstep %}

{% step %}
### <mark style="color:purple;">PUBLICATION DU STANDARD</mark>

Une fois validé par la Commission des Standards, **le standard est publié** comme standard validé sur le [site du CNIG](https://cnig.gouv.fr/les-standards-cnig-a18959.html#H_Tableau-et-liste-des-standards-CNIG).

Il est également référencé sur [schema.data.gouv.fr](https://schema.data.gouv.fr) sous le label « publié » qui remplace le label « en construction ». Pour cela, le dépôt Github doit être finalisé avant de solliciter l'équipe de schema.data.gouv qui réalisera le référencement.&#x20;
{% endstep %}
{% endstepper %}

### <mark style="background-color:blue;">Le rôle du secrétariat général du CNIG</mark>

Lors de la validation du standard, le secrétariat général vous accompagne pour :&#x20;

* la coordination avec la commission des standards pour la validation du standard (si besoin),&#x20;
* la rédaction du dossier de présentation au plénier en lien avec les animateurs,&#x20;
* la présentation au plénier.&#x20;

***



## <mark style="background-color:purple;">Ressources utiles</mark>

### Modèle de dossier de présentation en plénier

Ce modèle de document vise à indiquer les informations attendues par le plénier, mais c'est au Secrétariat Général et non à l'animateur du GT de le remplir.

{% file src="../../.gitbook/assets/GT CNIG - Modèle de dossier de présentation au plénier.docx" %}
_Modèle de dossier de présentation pour le conseil plénier_
{% endfile %}

***



## Retour à la page d'accueil ↓

{% content-ref url="../" %}
[..](../)
{% endcontent-ref %}

## Page précédente et page suivante ↓
