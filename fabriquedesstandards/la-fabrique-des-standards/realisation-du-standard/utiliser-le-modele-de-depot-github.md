# Utiliser le modèle de dépôt Github

Tout d'abord, pour accéder au modèle de dépôt, suivez le lien suivant :&#x20;

{% embed url="https://github.com/cnigfr/cnig-template" %}
_lien vers le modèle de dépôt_
{% endembed %}

Le modèle de dépôt Github du CNIG contient les fichiers nécessaires pour démarrer la création d'un dépôt de standard, il est également conforme à ce qui est demandé par schema.data.gouv pour un schéma au format [Table Schema](https://specs.frictionlessdata.io/table-schema/). A noter que la création d'un schéma n'est pas obligatoire pour la création d'un standard CNIG. En revanche, il est obligatoire de créer un dépôt Github afin que le standard soit référencé sur schema.data.gouv. Dans le cas où un standard possède différent profils, il sera nécessaire de créer un dépôt par profil (le site schema.data.gouv ne permettant pas de référencer plusieurs schémas ou standards à partir d'un seul dépôt).

## <mark style="background-color:purple;">Utiliser le modèle</mark>

Si vous créez votre dépôt sur GitHub, il vous suffit d'appuyer sur le bouton vert "Use this template" en haut à droite (consultez [la documentation](https://docs.github.com/fr/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) de github pour plus d'infos à ce sujet). Pour un standard CNIG, voici quelques recommandations spécifiques :

* "Include all branches" : laisser décoché,
* "Repository name" : le nom choisi doit commencer par "Standard" suivi d'un espace et du nom du standard,
* "Public/Pivate" : choisir "Public" pour que le dépôt soit visible par tous (vous seul pouvez le modifier pour le moment, mais il vous sera possible d'ajouter des collaborateurs comme décrit plus bas).

### L'organisation du dépôt

Ce dépôt contient un ensemble de dossiers et fichiers utiles pour le dépôt d'un standard.

* `README.md` est le point d'arrivée sur le dépôt, c'est un fichier terme au format markdown. Dans le modèle de dépôt, il s'agit d'un modèle de fichier à adapter, mais à terme, il devra présenter votre standard ;
* `schema` est le dossier où l'on peut trouver le schéma au format [Table Schema](https://specs.frictionlessdata.io/table-schema/), ainsi qu'une documentation pour la rédaction du schéma. Ce dossier peut être supprimé si le standard ne possède pas de schéma. Dans ce cas, il faut conserver le fichier schema.yml suivant ;
* `schema.yml` est un fichier qui remplace le schéma de données lorsque le standard ne possède pas de schéma. Il doit être supprimé si le standard possède un schéma. Sinon, il doit être complété ;
* `ressources` contient les fichiers utiles pour l'utilisation du standard élaborés par le groupe de travail ou provenant de sources tierces ;
* `groupe_de_travail_CNIG` est le dossier de travail du GT, dans lequel peuvent être référencés les comptes-rendus de réunion et tous les documents de travail (ce dossier peut être supprimé si le GT choisit un autre outil que github pour collaborer) ;
* `CHANGELOG.md` contient la liste des changements entre les différentes versions de votre standard ;
* `exemple-valide.csv` est un fichier CSV d'exemple conforme ;
* `LICENSE.md` est le fichier de licence du dépôt. Nous recommandons d'utiliser la [Licence Ouverte](https://www.etalab.gouv.fr/licence-ouverte-open-licence), cette licence est recommandée par l'administration française pour le partage de données et de documents ;
* `requirements.txt` liste les dépendances Python nécessaires pour effectuer des tests en intégration continue sur votre dépôt (il n'est pas nécessaire de modifier ce fichier) ;
* `.gitignore` : fichier généré automatiquement par github pour le suivi des versions de documents. Vous pouvez ignorer ce fichier.

{% hint style="info" %}
**A noter :** Il est conseillé de se familiariser avec la syntaxe markdown utilisée dans les documents ".md" avant de se lancer dans leur rédaction (pour cela, [la documentation de Github](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) peut être utile).
{% endhint %}

## <mark style="background-color:purple;">Étapes à suivre</mark>

Nous détaillons ci-dessous les étapes que nous vous conseillons de suivre après avoir créé votre dépôt Github, tout en utilisant les fichiers d'exemples.

* [ ] Ajouter des collaborateurs en vous rendant dans l'onglet "Settings", puis Access/Collaborators, puis "Add people" (à limiter aux animateurs et aux membres du GT familiers avec Github, pour les autres membres, privilégier les contributions via les "issues") ;
* [ ] Modifier le fichier d'exemple CSV avec des données conformes. L'outil [frictionless](https://pypi.org/project/frictionless/) permet de vérifier que vos fichiers sont conformes au schéma json en ligne de commande `frictionless validate --schema schema.json exemple-valide.csv` ;
* [ ] Modifier le fichier `CHANGELOG.md` pour indiquer la publication initiale. Le contenu de ce fichier sera visible depuis l'onglet "Changements" de la page du schéma sur schema.data.gouv ;
* [ ] Vérifier que la licence ouverte vous convient. Si vous devez utiliser une autre licence, modifier le fichier `LICENSE.md` et indiquer la licence dans le fichier `schema.json`, dans la clé `licenses` ;
* [ ] Modifier le modèle fichier `README.md`. Consulter plusieurs dépôt de standards CNIG (comme [ceux référencés sur le dépôt du CNIG](https://github.com/cnigfr)) et schémas sur [schema.data.gouv.fr](https://schema.data.gouv.fr) pour découvrir quelles informations sont pertinentes à indiquer.

**Si votre standard ne possède pas de schéma**

* [ ] Expliquer dans le README pourquoi un schéma de données n'est pas pertinent dans votre cas ;
* [ ] Compléter le modèle de schéma au format YAML et le placer à la racine du dépôt.

**Si votre standard possède un schéma**

* [ ] Décrire votre schéma dans le fichier `schema.json` en respectant la spécification Table Schema. Le fichier d'exemple comprend des valeurs d'exemples pour toutes les métadonnées possibles. Notez que les champs d'exemple ne comprennent qu'une petite partie des types, formats et contraintes disponibles, référez-vous à [la documentation](https://specs.frictionlessdata.io/table-schema/#types-and-formats) pour toutes les valeurs possibles. Si certaines métadonnées ne sont pas nécessaires pour votre projet, vous pouvez les supprimer. Pour vérifier que votre schéma est conforme, vous pouvez utiliser l'outil [tableschema](https://pypi.org/project/tableschema/) en ligne de commande : `tableschema validate schema.json`.

## <mark style="background-color:purple;">Intégration continue</mark>

Ce dépôt est configuré pour utiliser de l'intégration continue, si vous utilisez GitHub. À chaque commit, une suite de tests sera lancée via [GitHub Actions](https://github.com/features/actions) afin de vérifier :

* que votre schéma est valide à la spécification Table Schema ;
* que vos fichiers d'exemples sont conformes au schéma.

Si vous n'utilisez pas GitHub, vous pouvez lancer ces tests sur votre machine ou sur un autre service d'intégration continue comme Gitlab CI, Jenkins, Circle CI, Travis etc. Consultez la configuration utilisée dans `.github/workflows/test.yml`.

Localement, voici la procédure à suivre pour installer l'environnement de test et lancer les tests :

```bash
# Création d'un environnement virtuel en Python 3
python3 -m venv venv
source venv/bin/activate

# Installation des dépendances
pip install -r requirements.txt

# Test de la validité du schéma
frictionless validate --type schema schema.json

# Test de la conformité des fichiers d'exemples
frictionless validate --schema schema.json exemple-valide.csv
```

## <mark style="background-color:purple;">Lien avec la page sur Schema.data.gouv</mark>

Le dépôt github est la source depuis laquelle la page sur schema.data.gouv prend son contenu. Les correspondances suivantes sont effectuées :

* le fichier README.md apparaît dans l'onglet d'accueil "Informations",
* le fichier CHANGELOG.md apparaît dans l'onglet "Changements",
* les onglets "Documentation" et "Réglementation" sont générés automatiquement.

Les boutons au sommet de la description du standard permettent de réaliser plusieurs actions :

* "Saisir ou valider mes données" : renvoi vers la page "publier.etalab.studio" qui accompagne l'utilisateur pour la production de données conformes à votre standard,
* "Schéma" : renvoie vers une visualisation du schéma au format JSON (ou YAML quand le standard ne possède pas de schéma de données),
* "Données" : renvoie vers la page de data.gouv référençant toutes les données conformes au schéma qui y sont publiées,
* "RSS" : permet de s'abonner au flux RSS lié au schéma par lequel des informations sur ses évolutions peuvent être communiquées,
* "Git" : renvoie vers ce dépôt Github.

## <mark style="background-color:purple;">Documentation</mark>

Pour vous aider dans la construction de votre dépôt, nous vous recommandons de vous référer à :

* [Le guide pour la création de schémas](https://guides.data.gouv.fr/guides-open-data/guide-qualite/maitriser-les-schemas-de-donnees/creer-un-schema-de-donnees)
* [Le guide pour l'intégration de schémas à schema.data.gouv](https://guides.data.gouv.fr/guides-open-data/guide-qualite/maitriser-les-schemas-de-donnees/integrer-un-schema-de-donnees-a-schema.data.gouv.fr)
* [la documentation de Github pour le langage markdown utilisé dans les fichiers ".md", comme ce README.md](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [La documentation de schema.data.gouv.fr](https://schema.data.gouv.fr/validation.html)
* [La spécification Table Schema](https://specs.frictionlessdata.io/table-schema/)
* [Les règles Semver de numérotation des versions](https://semver.org/lang/fr/)
