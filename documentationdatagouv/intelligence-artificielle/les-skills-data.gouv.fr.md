---
description: >-
  Comprendre le rôle des skills data.gouv.fr et savoir dans quels cas
  l’utiliser.
icon: markdown
---

# Les skills data.gouv.fr

Les skills data.gouv.fr sont une expérimentation de l’équipe data.gouv.fr autour des grands modèles de langage.

Il prend la forme d’un dépôt collaboratif qui rassemble une documentation structurée pour aider un LLM à utiliser plus efficacement les APIs de la plateforme.

L’objectif est de permettre à un assistant d’interagir plus nativement avec data.gouv.fr, en particulier pour le catalogue, les métriques et les données tabulaires.

{% hint style="info" %}
Le skill est encore **expérimental**. Son contenu et son périmètre peuvent évoluer.
{% endhint %}

### À quoi sert les skills ?

Le skill fournit un cadre documentaire pensé pour les assistants IA.

Il aide le modèle à mieux comprendre :

* les capacités offertes par data.gouv.fr ;
* les APIs disponibles ;
* les cas d’usage autour du catalogue ;
* l’accès aux métriques ;
* la manipulation de données tabulaires.

L’idée est simple : au lieu de laisser un modèle deviner comment utiliser la plateforme, on lui fournit une base structurée et explicite.

### Quand l’utiliser ?

Le skill est utile si vous souhaitez améliorer la qualité des interactions d’un assistant avec data.gouv.fr.

Il est particulièrement pertinent pour :

* guider un LLM dans l’usage des APIs ;
* réduire les approximations sur les points d’entrée disponibles ;
* prototyper des assistants orientés données publiques ;
* documenter des usages récurrents de manière réutilisable.

### En quoi est-ce différent du serveur MCP ?

Le skill et le serveur MCP répondent à deux besoins différents.

Le [serveur MCP de data.gouv.fr](le-serveur-mcp-de-data.gouv.fr.md) fournit une interface standardisée pour connecter un client compatible à la plateforme.

Le skill, lui, apporte surtout un **contexte structuré** pour aider le modèle à comprendre comment utiliser data.gouv.fr.

En pratique :

* le **MCP** sert à connecter un assistant à des capacités ;
* le **skill** sert à mieux orienter le modèle dans l’usage de ces capacités.

### Mise en place

La mise en place dépend de l’environnement dans lequel vous utilisez votre assistant.

Le [dépôt du projet](https://github.com/datagouv/datagouv-skill) documente la structure du skill et la manière de le réutiliser dans vos expérimentations.

1. Consultez le dépôt des skills.
2. Identifiez les cas d’usage qui vous intéressent.
3. Réutilisez cette documentation structurée dans votre environnement.
4. Testez les réponses produites par le modèle.
5. Vérifiez les résultats avant réutilisation.

{% hint style="warning" %}
Un skill améliore le contexte fourni au modèle, mais ne garantit pas l’exactitude des réponses. Une validation humaine reste nécessaire.
{% endhint %}
