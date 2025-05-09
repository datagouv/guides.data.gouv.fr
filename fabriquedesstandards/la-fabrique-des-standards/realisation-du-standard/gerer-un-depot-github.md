---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Gérer un dépôt Github

## <mark style="background-color:purple;">Pourquoi un dépôt Github</mark>

Utiliser un dépôt github est nécessaire pour que le standard soit référencé sur le site schema.data.gouv, qu’il contienne un schéma de données ou non. C’est donc obligatoire pour la publication d’un standard CNIG. Les étapes à suivre pour créer le dépôt et l’alimenter sont décrites dans \[le modèle de dépôt Github]\([https://github.com/cnigfr/cnig-template](https://github.com/cnigfr/cnig-template)).&#x20;

Github peut également être un outil collaboratif utile pour la réalisation du standard. Il est prévu pour travailler en commun sur du code informatique principalement, mais il est tout à fait pertinent pour travailler sur des documents texte, à condition d’utiliser le format markdown, qui est le mieux géré par l’outil (les formats textuels habituels comme le word ou le pdf sont sauvegardés au format binaire, ce qui rend plus difficile la gestion des versions). Sa prise en main n’est pas très exigeante lorsqu’on est à l’aise avec l’informatique, mais cette option est tout de même déconseillée sans un minimum d'initiation ou de formation pour un animateur qui n’aurait jamais utilisé Github.&#x20;

Voici quelques conseils pour la prise en main.

## <mark style="background-color:purple;">Comment fonctionne Github</mark>

Github propose à titre gratuit (à condition de respecter une limite de mémoire) l’hébergement et le suivi de fichiers en ligne. Il s’agit d’un gestionnaire de version collaborative, c'est-à-dire qu’il permet de travailler en communauté sur des fichiers dont les modifications sont traçables et réversibles. Les fichiers sont mis à jour version par version, sur proposition de la communauté et après approbation des administrateurs d’un dépôt. Il permet également de réaliser des tests automatisés (procédure d’intégration et de développement continus, ou “CI/CD pipeline” en anglais) et s’intègre très bien avec un grand nombre d’outils informatiques.&#x20;

Il est nécessaire de créer un compte pour créer un dépôt Github ou y contribuer (voir [la procédure documentée par Github](https://docs.github.com/fr/get-started/onboarding/getting-started-with-your-github-account)).

{% hint style="warning" %}
**Important :** toutes les modifications apportées doivent être validées par un “commit”. Les commits sont des actions réversibles qu’il est possible de tracer dans le temps. C’est pourquoi il est utile de les décrire autant que possible dans leur titre et dans leur description. Pour une utilisation simple de Github (une seule branche de travail), le niveau de connaissance sur le versionnage nécessaire est très faible (le contenu de cette page devrait suffire). Pour une utilisation plus poussée, il peut être utile de se référer à une documentation plus complète comme [celle de Github sur les demandes de tirage](https://docs.github.com/fr/pull-requests) (ou pull request en anglais).
{% endhint %}

## <mark style="background-color:purple;">Créer un dépôt</mark>

Il est généralement conseillé de partir de l’existant pour créer un dépôt Github, en utilisant un modèle (comme [le modèle de dépôt du CNIG](https://github.com/cnigfr/cnig-template)) ou en repartant d’un dépôt existant de manière incrémentale (une “fork”, comme décrit [sur cette page](https://docs.github.com/fr/get-started/exploring-projects-on-github/contributing-to-a-project)).&#x20;

Le dépôt possède un fichier README.md où il est décrit. Son organisation est laissée libre après cela. L’utilisation de Github peut se faire en ligne sur l’interface Web, via des éditeurs intégrant Github, ou encore par ligne de commande (mais cela est réservé aux utilisateurs avancés et généralement réservé aux dépôts de code).&#x20;

### Créer ou modifier un fichier

Plusieurs méthodes existent pour créer un fichier. Il est possible d’en créer un de toutes pièces pour les formats de fichier simples (textuels comme .md, .txt, etc. ou d’échange de données comme .json, .yaml, etc.), en précisant le format du fichier en suffixe de son nom lors de sa création. Les fichiers peuvent également être importés. Dans les deux cas, il faudra cliquer sur le bouton “Add a file” après s’être placé dans le dossier de destination, sélectionner l’option souhaitée (“Create” ou “Import”), réaliser l’action et la valider par un commit.

### Créer un dossier

Github ne supporte pas les dossiers vides. L’unique solution pour créer un dossier est donc de créer un fichier. Pour créer un fichier dans un nouveau dossier, il faut cliquer sur “Add a file”, puis “Create”, et enfin créer le nouveau dossier dans le nom du fichier. Dans le nom du fichier, commencer par taper le nom du nouveau dossier “Dossier1”, puis faites suivre ce nom d’une barre oblique “/”. L’interface devrait interpréter directement ce symbole et vous verrez qu’un dossier a été ajouté dans le chemin conduisant au fichier.&#x20;

Une bonne pratique est de créer un fichier “README.md” pour chaque dossier.&#x20;

### Déplacer un fichier

Les fichiers ne peuvent être déplacés que via l’interface d’édition de fichier. Il faut donc cliquer sur “Edit” sur le fichier cible, et modifier le chemin vers le fichier dans son nom (la touche retour arrière permet d’éditer le chemin précédent le nom du fichier).

## <mark style="background-color:purple;">Gérer un dépôt</mark>

[La documentation de Github pour la gestion de projet ](https://docs.github.com/fr/issues/planning-and-tracking-with-projects/learning-about-projects/best-practices-for-projects)est une référence utile, à compléter au cas par cas par des recherches en ligne, sur des forums dédiés par exemple.&#x20;

### La gestion des droits&#x20;

Par défaut, un dépôt public ne peut être modifié que par son administrateur bien qu’il soit visible de tous. Pour permettre à un co-animateur, par exemple, de le modifier, il faut l’ajouter en tant que contributeur (Settings/Access/Contributors/Add people). Il est recommandé de privilégier les “issues” pour les membres du GT moins familiers avec Github, où ils peuvent faire des retours sous la forme de commentaires. Il n’est pas nécessaire de les inscrire en tant que “contributeurs” pour cela.&#x20;

### La gestion des contributions

Les membres de la communauté n'ayant pas de droit de modification sur le dépôt peuvent utiliser deux méthodes pour proposer des modifications :&#x20;

* les “issues” (ou "contribution"), sous la forme de commentaires libres, et&#x20;
* les “pull requests” (ou "demande de tirage"), où les modifications sont réalisées dans une version de travail des fichiers.&#x20;

Pour les besoins d’un standard, les issues sont généralement suffisantes, mais les pull requests peuvent permettre de proposer des modifications plus précises. Le rôle de l’administrateur est de relire ces issues et pull requests et d’en vérifier le contenu. L’administrateur modifie les fichiers pour prendre en compte une issue. Pour une pull request, il n’a pas besoin de prendre la plume et peut directement accepter les suggestions (ce qui entraîne une modification des fichiers, bien qu’elle soit toujours réversible) ou les refuser.&#x20;

## <mark style="background-color:purple;">Maintenir un dépôt</mark>

Après la publication initiale, une maintenance peut être assurée pour prendre en compte les retours lors de l’appel à commentaires, mais aussi sur le plus long terme si le standard doit être mis à jour.&#x20;

Il est recommandé de ne mettre à jour la branche principale “master” (c’est-à-dire la version utilisée par le public) que lorsqu’une nouvelle version est prête pour publication. Le nom du commit doit alors indiquer le numéro de version correspondant.&#x20;

Les modifications sont automatiquement répercutées sur schema.data.gouv, il faut donc être prudent dans les changements apportés. Il est nécessaire de communiquer sur la publication d’une nouvelle version pour s’assurer que celle-ci est prise en compte par les utilisateurs.&#x20;
