---
description: Installer le skill data.gouv.fr pour votre assistant IA.
icon: markdown
---

# Le skill data.gouv.fr

Le [skill data.gouv.fr](https://github.com/datagouv/datagouv-skill) est une documentation structurée pour aider un assistant IA à utiliser plus efficacement les APIs de la plateforme ([catalogue](../api-de-data.gouv.fr/reference/README.md), [métriques](https://metric-api.data.gouv.fr/api/doc) et [données tabulaires](https://tabular-api.data.gouv.fr/api/doc)).

{% hint style="info" %}
[Le skill](https://github.com/datagouv/datagouv-skill) est encore **expérimental**. Le contenu, les usages et la configuration peuvent évoluer.\
[Vos retours](https://tally.so/r/KYMboX) sont les bienvenus !
{% endhint %}

{% hint style="warning" %}
Comme pour tout usage de LLM, les réponses peuvent être incomplètes, erronées ou inclure des **hallucinations** (informations inventées par le modèle). Vérifiez toujours les résultats avant réutilisation.

Pour des usages sérieux (applications, visualisations, traitements automatisés), privilégiez l'utilisation directe des [APIs de data.gouv.fr](../api-de-data.gouv.fr/prise-en-main/README.md) : elles offrent des réponses structurées, traçables et reproductibles.
{% endhint %}

## Installation

Installez le skill en suivant la procédure correspondant à votre assistant.

{% hint style="info" %}
Les commandes ci-dessous sont prévues pour macOS/Linux.  
Si vous utilisez Windows, suivez la documentation officielle de votre assistant pour adapter les chemins et commandes.
{% endhint %}

Le skill est maintenu dans le dépôt [datagouv-skill](https://github.com/datagouv/datagouv-skill).  
Pour les détails complets d'installation et de structure (`SKILL.md`), consultez la [section Installation du README](https://github.com/datagouv/datagouv-skill?tab=readme-ov-file#%EF%B8%8F-installation).

<details>

<summary>Claude Code</summary>

Consultez la [documentation Claude Code (Skills)](https://code.claude.com/docs/en/skills).

```shell
# Installation personnelle
mkdir -p ~/.claude/skills/datagouv-apis
cp SKILL.md ~/.claude/skills/datagouv-apis/

# Installation dans le projet
mkdir -p .claude/skills/datagouv-apis
cp SKILL.md .claude/skills/datagouv-apis/
```

</details>

<details>

<summary>Cursor</summary>

Consultez la [documentation Cursor (Skills)](https://cursor.com/docs/context/skills).

Option 1 (recommandée) : ajouter une règle distante GitHub dans `Settings` > `Rules` > `Project Rules` > `Add Rule` > `Remote Rule (Github)`, puis renseigner le dépôt `datagouv/datagouv-skill`.

Option 2 (copie locale) :

```shell
# Installation personnelle
mkdir -p ~/.cursor/skills/datagouv-apis
cp SKILL.md ~/.cursor/skills/datagouv-apis/

# Installation dans le projet
mkdir -p .cursor/skills/datagouv-apis
cp SKILL.md .cursor/skills/datagouv-apis/
```

</details>

<details>

<summary>Claude Desktop</summary>

```shell
# macOS
mkdir -p ~/Library/Application\ Support/Claude/skills/datagouv-apis
cp SKILL.md ~/Library/Application\ Support/Claude/skills/datagouv-apis/

# Linux
mkdir -p ~/.config/claude/skills/datagouv-apis
cp SKILL.md ~/.config/claude/skills/datagouv-apis/
```

</details>

<details>

<summary>Mistral Vibe</summary>

Consultez la [documentation Mistral (Agents & Skills)](https://docs.mistral.ai/mistral-vibe/agents-skills/).

Les chemins ci-dessous correspondent à la configuration actuellement documentée dans le dépôt du skill. Vérifiez la documentation Mistral si votre version utilise une structure différente.

```shell
# Installation globale
mkdir -p ~/.vibe/skills/datagouv-apis
cp SKILL.md ~/.vibe/skills/datagouv-apis/

# Installation dans le projet
mkdir -p .vibe/skills/datagouv-apis
cp SKILL.md .vibe/skills/datagouv-apis/
```

</details>

<details>

<summary>Codex CLI</summary>

Consultez la [documentation Codex (Skills)](https://developers.openai.com/codex/skills).

```shell
# Installation utilisateur
mkdir -p ~/.agents/skills/datagouv-apis
cp SKILL.md ~/.agents/skills/datagouv-apis/

# Installation dans le projet
mkdir -p .agents/skills/datagouv-apis
cp SKILL.md .agents/skills/datagouv-apis/
```

</details>

<details>

<summary>ChatGPT</summary>

Collez le contenu de `SKILL.md` au début de la conversation, ou pointez vers la version brute :

`https://raw.githubusercontent.com/datagouv/datagouv-skill/main/SKILL.md`

</details>

<details>

<summary>Autres assistants</summary>

Copiez `SKILL.md` dans un dossier reconnu par votre client comme dossier de skills, par exemple `datagouv-apis/SKILL.md`.

</details>

Après installation, redémarrez votre assistant si nécessaire.

## Vérifier l’installation

Une fois le skill installé :

1. Testez une demande simple portant sur data.gouv.fr (jeu de données, API, métriques ou ressource tabulaire).
2. Vérifiez que les réponses sont plus précises, mieux structurées et cohérentes avec la documentation de la plateforme.
3. Validez systématiquement les résultats avant réutilisation.

## Pour aller plus loin

Ce guide couvre l’installation du skill. Pour les détails complets (cas particuliers, formats et mises à jour), consultez le [README du dépôt datagouv-skill](https://github.com/datagouv/datagouv-skill?tab=readme-ov-file).
