---
description: Principes et expérimentations menés par l’équipe data.gouv.fr autour de l’IA.
icon: brain-circuit
---

# Notre approche de l’intelligence artificielle sur data.gouv.fr

L’équipe data.gouv.fr expérimente l’intelligence artificielle, en particulier les [grands modèles de langage](https://fr.wikipedia.org/wiki/Grand_mod%C3%A8le_de_langage) (LLM), pour faciliter l’accès aux données publiques et leurs usages.

Ces fonctionnalités sont encore en construction. Nous les faisons évoluer à partir de vos retours.

{% hint style="info" %}
## Nos expérimentations en cours

* Génération automatique de descriptions courtes, pour aider à rédiger des présentations claires et accessibles ;
* Suggestion de mots-clés ;&#x20;
* L'ouverture d'un **serveur [Model Context Protocol](https://modelcontextprotocol.io/docs/getting-started/intro) (MCP)** en ligne. Ce serveur standardisé permet de connecter directement data.gouv.fr à votre chatbot pour qu'il puisse chercher et analyser des données en lauguage naturel depuis votre chatbot. Retrouvez comment configurer votre outil (Claude, ChatGPT, Mistral...) sur le dépôt [datagouv-mcp](https://github.com/datagouv/datagouv-mcp)
* La mise à disposition d'un [**skill data.gouv.fr**](https://github.com/datagouv/datagouv-skill) via un dépôt collaboratif. Il s'agit d'une documentation structurée à destination des LLMs pour leur apprendre à utiliser nativement les APIs de la plateforme (catalogue, métriques et données tabulaires).
{% endhint %}

Ces expérimentations reposent sur quelques principes simples.

**L’IA comme aide, pas comme arbitre**

L’IA propose. Elle ne décide pas à votre place. Vous restez libre d’accepter, de modifier ou de rejeter ses suggestions.

**Une démarche expérimentale**

Nous testons, apprenons et corrigeons. Certaines propositions seront utiles. D’autres le seront moins. Vos retours nous aident à progresser.

**Respect de vos données**

Nous ne collectons ni ne stockons de données personnelles via ces fonctionnalités. Les traitements reposent sur des modèles hébergés par l’État, sans transfert vers des services externes. Les retours sont traités de manière anonyme pour améliorer le service.

**Une fiabilité relative**

Les suggestions des LLM peuvent être incomplètes, approximatives ou erronées. Elles doivent toujours être relues et validées par un humain.

**Sobriété et impact écologique**

L’IA consomme des ressources importantes. Nous cherchons donc à en faire un usage mesuré et à limiter l’empreinte environnementale de nos expérimentations.

**Utilisation avec précaution**

Nous utilisons l’IA là où elle apporte une aide concrète, sans complexifier l’expérience. Son rôle n’est pas de tout automatiser.

**Ouverture et transparence**

Nous privilégions des modèles ouverts, adaptés par l’équipe Etalab, notamment [Albert](https://www.numerique.gouv.fr/offre-accompagnement/expertise-albert-ia-etat/). Dans le service public, l’IA doit se construire de façon transparente, dans la confiance et avec la participation de tous.
