---
description: >-
  Comprendre le rôle des skills data.gouv.fr et savoir dans quels cas
  l’utiliser.
icon: markdown
---

# Les skills data.gouv.fr

[Les skills data.gouv.fr](https://github.com/datagouv/datagouv-skill) sont une expérimentation de l’équipe data.gouv.fr autour des grands modèles de langage.

Il prend la forme d’un dépôt collaboratif qui rassemble une documentation structurée pour aider un LLM à utiliser plus efficacement les APIs de la plateforme.

L’objectif est de permettre à un assistant d’interagir plus nativement avec data.gouv.fr, en particulier pour le catalogue, les métriques et les données tabulaires.

{% hint style="info" %}
[Le skill](https://github.com/datagouv/datagouv-skill) est encore **expérimental**. Son contenu et son périmètre peuvent évoluer.
{% endhint %}

### À quoi servent [les skills](https://github.com/datagouv/datagouv-skill) ?

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

[Le skill](https://github.com/datagouv/datagouv-skill) et le [serveur MCP](https://github.com/datagouv/datagouv-mcp) répondent à deux besoins différents.

Le [serveur MCP de data.gouv.fr](le-serveur-mcp-de-data.gouv.fr.md) fournit une interface standardisée pour connecter un client compatible à la plateforme.

[Le skill](https://github.com/datagouv/datagouv-skill), lui, apporte un **contexte structuré** pour aider le modèle à comprendre comment utiliser data.gouv.fr.

En pratique :

* le **MCP** sert à connecter un assistant à des capacités ;
* le [**skill**](https://github.com/datagouv/datagouv-skill) sert à mieux orienter le modèle dans l’usage de ces capacités.

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
