---
description: >-
  Comprendre le rôle du skill data.gouv.fr et savoir dans quels cas
  l’utiliser.
icon: markdown
---

# Le skill data.gouv.fr

[Le skill data.gouv.fr](https://github.com/datagouv/datagouv-skill) est une expérimentation de l’équipe data.gouv.fr autour des grands modèles de langage.

Il prend la forme d’un dépôt collaboratif qui rassemble une documentation structurée pour aider un LLM à utiliser plus efficacement les APIs de la plateforme.

L’objectif est de permettre à un assistant d’interagir plus nativement avec data.gouv.fr, en particulier pour le catalogue, les métriques et les données tabulaires.

{% hint style="info" %}
[Le skill](https://github.com/datagouv/datagouv-skill) est encore **expérimental**. Son contenu et son périmètre peuvent évoluer.
{% endhint %}

### À quoi sert [le skill data.gouv.fr](https://github.com/datagouv/datagouv-skill) ?

[Le skill](https://github.com/datagouv/datagouv-skill) fournit un cadre documentaire pensé pour les assistants IA.

Il aide le modèle à mieux comprendre :

* les capacités offertes par data.gouv.fr ;
* les APIs disponibles ;
* les cas d’usage autour du catalogue ;
* l’accès aux métriques ;
* la manipulation de données tabulaires.

L’idée est simple : au lieu de laisser un modèle deviner comment utiliser la plateforme, on lui fournit une base structurée et explicite.

### Quand l’utiliser ?

[Le skill](https://github.com/datagouv/datagouv-skill) est utile si vous souhaitez améliorer la qualité des interactions d’un assistant avec data.gouv.fr.

Il est particulièrement pertinent pour :

* guider un LLM dans l’usage des APIs ;
* réduire les approximations sur les points d’entrée disponibles ;
* prototyper des assistants orientés données publiques ;
* documenter des usages récurrents de manière réutilisable.

### En quoi est-ce différent du [serveur MCP](https://github.com/datagouv/datagouv-mcp) ?

[Le skill](https://github.com/datagouv/datagouv-skill) est une **documentation** : du texte et une structure (fichiers, règles) que le LLM lit pour savoir **comment** appeler les APIs data.gouv.fr (endpoints, paramètres, bonnes pratiques). Le modèle reste responsable de formuler les requêtes HTTP lui-même (ou via le code qu’il produit).

Le [serveur MCP de data.gouv.fr](le-serveur-mcp-de-data.gouv.fr.md) expose des **outils** au client : le LLM ne « devine » pas l’API sous forme de texte libre, il est **guidé** par des appels d’outils nommés et typés que le serveur MCP exécute. C’est le MCP qui relie l’assistant aux capacités concrètes de la plateforme.

En résumé :

* [**Skill**](https://github.com/datagouv/datagouv-skill) : documenter l’usage des APIs pour le modèle ;
* **MCP** : orchestrer l’usage via des outils intégrés au flux de l’assistant.

Les deux ne s’excluent pas : vous pouvez activer le [serveur MCP](https://github.com/datagouv/datagouv-mcp) et le [skill](https://github.com/datagouv/datagouv-skill) en parallèle.

Les deux relèvent d’**expérimentations** : l’**efficacité comparative** du skill et du MCP n’a pas encore été **évaluée** par les équipes data.gouv.fr, mais ce travail est **en cours**.

### Mise en place

La mise en place dépend de l’environnement dans lequel vous utilisez votre assistant.

La marche à suivre (chemins, commandes, options par outil) est décrite dans la [**section Installation du README**](https://github.com/datagouv/datagouv-skill?tab=readme-ov-file#%EF%B8%8F-installation) du dépôt [datagouv-skill](https://github.com/datagouv/datagouv-skill). Le fichier `SKILL.md` et la structure du dépôt y sont détaillés.

1. Ouvrez le [guide d’installation](https://github.com/datagouv/datagouv-skill?tab=readme-ov-file#%EF%B8%8F-installation) et repérez la procédure correspondant à votre outil.
2. Appliquez la configuration indiquée (emplacement des skills, règle distante, copie de fichiers, etc.).
3. Redémarrez le client si sa documentation le recommande.
4. Testez vos cas d’usage en langage naturel.
5. Vérifiez les résultats avant réutilisation.

{% hint style="warning" %}
[Un skill](https://github.com/datagouv/datagouv-skill) améliore le contexte fourni au modèle, mais ne garantit pas l’exactitude des réponses. Une validation humaine reste nécessaire.
{% endhint %}
