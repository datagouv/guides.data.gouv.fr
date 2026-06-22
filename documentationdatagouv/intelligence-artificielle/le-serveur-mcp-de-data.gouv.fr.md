---
description: Comprendre le rôle du serveur MCP de data.gouv.fr et savoir quand l’utiliser.
icon: mcp
---

# Le serveur MCP de data.gouv.fr

[Le serveur MCP de data.gouv.fr](https://github.com/datagouv/datagouv-mcp) est une expérimentation de l’équipe data.gouv.fr autour du protocole [**Model Context Protocol**](https://modelcontextprotocol.io/docs/getting-started/intro).

Son objectif est simple : permettre à un agent conversationnel compatible MCP d’interroger data.gouv.fr avec un cadre standardisé.

Concrètement, votre assistant peut chercher des jeux de données, explorer des métadonnées et vous aider à analyser les ressources disponibles en langage naturel.

{% hint style="info" %}
[Le serveur MCP](https://github.com/datagouv/datagouv-mcp) est encore **expérimental**. Le périmètre, les usages et la configuration peuvent évoluer.\
[Vos retours](https://tally.so/r/KYMboX) sont les bienvenus !
{% endhint %}

### À quoi sert le MCP ?

Un serveur MCP fournit une façon standard de relier un assistant IA à une source d’information ou à un service.

Dans le cas de data.gouv.fr, cela permet de connecter un client compatible MCP à la plateforme sans développer une intégration spécifique pour chaque outil.

Cette approche facilite notamment :

* la recherche de données publiques en langage naturel ;
* l’exploration du catalogue data.gouv.fr depuis un assistant ;
* l’analyse guidée de jeux de données et de leurs ressources ;
* la réutilisation de la même interface avec plusieurs clients compatibles.

### Quand l’utiliser ?

[Le serveur MCP](https://github.com/datagouv/datagouv-mcp) est utile si vous souhaitez travailler avec data.gouv.fr depuis un assistant conversationnel.

Il est particulièrement adapté si vous voulez :

* gagner du temps dans l’exploration du catalogue ;
* guider un utilisateur non spécialiste dans la recherche de données ;
* prototyper de nouveaux usages autour des données ouvertes ;
* tester des interactions en langage naturel avec la plateforme.

Si vous avez besoin d’automatisations robustes, rejouables et finement contrôlées, l’[API de data.gouv.fr](../api-de-data.gouv.fr/prise-en-main/) reste le point d’entrée le plus adapté.

### Mise en place

La configuration dépend du client utilisé.

Le [dépôt du projet](https://github.com/datagouv/datagouv-mcp) documente la mise en place avec plusieurs outils, dont Claude, ChatGPT et Mistral.

1. Choisissez un client compatible MCP (liste [ici](https://github.com/datagouv/datagouv-mcp?tab=readme-ov-file#-connect-your-chatbot-to-the-mcp-server)).
2. Suivez la [procédure de configuration du client](https://github.com/datagouv/datagouv-mcp?tab=readme-ov-file#-connect-your-chatbot-to-the-mcp-server)
3. Connectez-le au serveur MCP de data.gouv.fr à l'adresse https://mcp.data.gouv.fr/mcp.
4. Testez vos premiers cas d’usage en langage naturel.

{% hint style="warning" %}
Comme pour tout usage de LLM, les réponses peuvent être incomplètes ou erronées. Vérifiez toujours les résultats avant réutilisation.
{% endhint %}
