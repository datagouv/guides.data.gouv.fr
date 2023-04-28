# Etape 4 : Phase de promotion et de maintien

{% hint style="info" %}
**Lexique : Phase de maintien et de promotion**

La phase de maintien est la dernière phase du cycle de vie d'un schéma. Elle consiste à itérer sur la version actuelle en prenant en compte des évolutions du terrain et des retours des producteurs et des réutilisateurs pour peaufiner la structure du schéma. \
Elle est étroitement liée à la promotion du schéma qui permettra, grâce à son adoption par le plus grand nombre de parties prenantes, une montée en qualité et en quantité d'utilisations.



Modifier ou commenter un schéma contribue à faire vivre l'écosystème open data et permettra de vous identifier comme contributeur.rice sur un schéma spécifique.
{% endhint %}

## Promouvoir un schéma de données <a href="#promouvoir-votre-schema-de-donnees" id="promouvoir-votre-schema-de-donnees"></a>

De nouveaux acteurs peuvent vouloir publier des données qui rentrent dans le cadre de votre schéma, mais peuvent ne pas en avoir connaissance, ou ne pas avoir les compétences techniques pour se l'approprier.

Pour faciliter l'adoption d'un schéma de données, il est possible de par exemple :&#x20;

* [ ] **diffuser ses travaux à ses partenaires et au grand public**, sur ses réseaux sociaux ou newsletters, pour mettre en valeur sa proactivité et susciter de l'intérêt ;
* [ ] **utiliser son réseau de connaissances pour inciter d'autres parties prenantes à publier leurs données**, par exemple via la plateforme [publier.etalab.studio](https://publier.etalab.studio/), que ce soit sous son schéma ou dans d'autres domaines, qui pourront donner lieu à d'autres schémas ;
* [ ] **aider des acteurs souhaitant utiliser son schéma**, en leur faisant bénéficier de son expérience, par exemple en leur répondant directement dans les commentaires sur [data.gouv.fr](https://www.data.gouv.fr/) ;
* [ ] **interagir avec les réutilisateurs** afin de mieux cerner leurs besoins, suggérer des améliorations ou des champs d'investigation.

Des scripts ont été mis au point par les équipes d'Etalab pour permettre de vérifier et d'agréger toutes les données publiées par type de schéma et ainsi créer des fichiers consolidés à l'échelle nationale (i.e.[ données IRVE](https://www.data.gouv.fr/fr/datasets/fichier-consolide-des-bornes-de-recharge-pour-vehicules-electriques/)). Cela permet à des solutions à grande échelle d'émerger.&#x20;

## Maintenir un schéma de données <a href="#maintenir-votre-schema-de-donnees" id="maintenir-votre-schema-de-donnees"></a>

Aussi exhaustive qu'ait été la phase de concertation, il est probable que des corrections ou des évolutions du schéma soient nécessaires afin de le rendre plus précis ou plus accessible par exemple.&#x20;

**Clarifications de la documentation, corrections d’erreurs, évolutions du cadre réglementaire, etc. sont autant de raisons où il est indispensable de mettre en œuvre une nouvelle version.**

[schema.data.gouv.fr](https://schema.data.gouv.fr/) récupère le contenu de votre dépôt via des `releases` de celui-ci, c'est à dire des versions packagées de votre code (schéma + documentation). Avec ce système, il est alors possible pour schema.data.gouv.fr de suivre l'évolution formelle de votre schéma et d'en référencer les différentes versions au cours du temps. Cela permet également aux contributeurs de considérer les branches du dépôt Github qui héberge le schéma (`main` ou autre) comme un espace de développement participatif qui reste dissocié du référencement sur schema.data.gouv.fr tant qu'une nouvelle version n'est pas publiée.

Une fois que l'état de votre branche principale, `main` par exemple, vous conviendra, vous pourrez sur Github ou Gitlab créer une release. Pour cela, il suffit d'ajouter un tag et une version correspondant à la nouvelle version que vous souhaitez publier. Celle-ci sera par la suite automatiquement récupérée par schema.data.gouv.fr et publiée (généralement sous 24h).

Si un schéma que vous maintenez doit être modifié, la marche à suivre peut être la suivante :&#x20;

1. **faire une nouvelle** [**phase de concertation**](https://guides.etalab.gouv.fr/producteurs-schemas/phase-concertation) afin d'évoquer les problématiques qui imposent un changement et de trouver la solution la plus adaptée. Si vous n'avez pas d'espace pour cela, nous vous conseillons de publier une [`issue` sur le dépôt Github de schema.data.gouv.fr](https://github.com/etalab/schema.data.gouv.fr/issues).
2. lorsqu'un accord est trouvé, **mettre à jour techniquement le schéma** lui-même (cf. le paragraphe ci-après);
3. **mettre à jour la documentation du schéma** ;
4. **déployer les mises à jour sous un nouveau tag de version** ;
5. **communiquer sur cette mise à jour**.

Lorsque les modifications à faire à un schéma font consensus, il est nécessaire de les implémenter et de déployer une nouvelle version. La marche à suivre peut être la suivante :&#x20;

1. **répertorier tous les changements à faire avant de les implémenter** : anticiper l'impact sur les fichiers techniques et sur la documentation (notamment l'incrémentation de la version)
2. **faire les modifications listées à l'étape précédente** :
   * en local, puis pousser les changements avec les commandes git (add, commit et push)
   * ou directement sur Github
3. **créer une release (nouvelle version)** :
   * sur la page Github de votre schéma, cliquer sur `X tags` (à côté des branches) : ici sont listées toutes les versions du schéma
   * cliquer sur `Releases` puis `Draft a new release`
   * indiquer le nom de la nouvelle version dans `Choose a tag` : par exemple si la version actuelle est v1.0.1, la nouvelle sera v1.0.2 (dans certains cas, il sera opportun de passer en 1.1.1 ou en 2.0.1)
   * la branche cible (`target`) doit être la branche principale, si des développements ont été faits sur d'autres branches, il est nécessaire de les fusionner - `merge` - avec la branche principale via une [`pull request`](https://docs.github.com/fr/pull-requests) (après validation des modifications)
   * documenter la nouvelle version : ajouter un titre et une description exhaustive des changements dans les champs dédiés, juste avant la publication
   * publier la release (`Publish release`)

Que ce soit pour des considérations techniques ou "conceptuelles", il est possible de solliciter [les équipes d’Etalab](https://www.etalab.gouv.fr/contact) qui pourront vous accompagner dans le processus de mise à jour de votre schéma.

## Points de sortie <a href="#points-de-sortie" id="points-de-sortie"></a>

À l’issue de cette phase, vous devriez :

* Comprendre l'importance de la proactivité dans la promotion, la diffusion et le maintien d'un schéma ;
* Avoir des pistes d'actions concrètes pour porter un schéma auprès d'autres parties prenantes ;
* Savoir pourquoi, quand et comment mettre à jour un schéma de données.
