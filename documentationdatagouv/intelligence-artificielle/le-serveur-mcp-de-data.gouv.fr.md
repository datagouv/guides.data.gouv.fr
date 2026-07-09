---
description: Connecter votre chatbot au serveur MCP (connecteur) data.gouv.fr.
icon: mcp
---

# Le serveur MCP de data.gouv.fr

[Le serveur MCP de data.gouv.fr](https://github.com/datagouv/datagouv-mcp) est une expérimentation de l’équipe data.gouv.fr autour du protocole [**Model Context Protocol**](https://modelcontextprotocol.io/docs/getting-started/intro). Il permet à un assistant conversationnel compatible MCP de rechercher des jeux de données, d’explorer le catalogue et d’analyser des ressources en langage naturel. Selon l’outil, on parle indifféremment de **serveur MCP** ou de **connecteur** — les deux désignent la même connexion à data.gouv.fr. Une instance publique est disponible pour tous, sans restriction d’accès.

{% hint style="info" %}
[Le serveur MCP](https://github.com/datagouv/datagouv-mcp) est encore **expérimental**. Le périmètre, les usages et la configuration peuvent évoluer.\
[Vos retours](https://tally.so/r/KYMboX) sont les bienvenus !
{% endhint %}

{% hint style="warning" %}
Comme pour tout usage de LLM, les réponses peuvent être incomplètes, erronées ou inclure des **hallucinations** (informations inventées par le modèle). Vérifiez toujours les résultats avant réutilisation.

Pour des usages sérieux (applications, visualisations, traitements automatisés), privilégiez les [APIs de data.gouv.fr](../api-de-data.gouv.fr/prise-en-main/README.md) : elles offrent des réponses structurées, traçables et reproductibles.
{% endhint %}

## Connexion

Connectez data.gouv.fr à votre chatbot en quelques étapes. Vous ajouterez un serveur MCP ou un connecteur selon le vocabulaire de votre outil.

| | |
| --- | --- |
| **URL du serveur** | `https://mcp.data.gouv.fr/mcp` |
| **Authentification** | Aucune clé requise (outils en lecture seule) |
| **Self-host** | Voir la section [Run locally](https://github.com/datagouv/datagouv-mcp#%EF%B8%8F-run-locally) du dépôt GitHub |

Ouvrez la section correspondant à votre outil. Chaque bloc reprend le libellé affiché dans l’interface (serveur MCP, connecteur, etc.) :

<details>

<summary>AnythingLLM</summary>

1. Ouvrez le fichier `anythingllm_mcp_servers.json` :
   * **Linux** : `~/.config/anythingllm-desktop/storage/plugins/anythingllm_mcp_servers.json`
   * **macOS** : `~/Library/Application Support/anythingllm-desktop/storage/plugins/anythingllm_mcp_servers.json`
   * **Windows** : `C:\Users\<user>\AppData\Roaming\anythingllm-desktop\storage\plugins\anythingllm_mcp_servers.json`
2. Ajoutez la configuration suivante :

```json
{
  "mcpServers": {
    "datagouv": {
      "type": "streamable",
      "url": "https://mcp.data.gouv.fr/mcp"
    }
  }
}
```

3. Redémarrez AnythingLLM si nécessaire.

</details>

<details>

<summary>ChatGPT</summary>

*Disponible sur les plans payants uniquement (Plus, Pro, Team et Enterprise). ChatGPT parle de **connecteurs** plutôt que de serveurs MCP.*

1. Ouvrez ChatGPT dans votre navigateur, allez dans `Settings` > `Apps and connectors`.
2. Dans `Advanced settings`, activez le **Developer mode**.
3. Retournez dans `Settings` > `Connectors` > `Browse connectors`, puis cliquez sur **Add a new connector**.
4. Renseignez l’URL `https://mcp.data.gouv.fr/mcp` et enregistrez pour activer le connecteur MCP data.gouv.fr.

</details>

<details>

<summary>Claude Code</summary>

Exécutez la commande suivante :

```shell
claude mcp add --transport http datagouv https://mcp.data.gouv.fr/mcp
```

</details>

<details>

<summary>Claude Desktop</summary>

1. Ouvrez `claude_desktop_config.json` :
   * **Linux** : `~/.config/Claude/claude_desktop_config.json`
   * **macOS** : `~/Library/Application Support/Claude/claude_desktop_config.json`
   * **Windows** : `%APPDATA%\Claude\claude_desktop_config.json`
2. Ajoutez dans `mcpServers` (section « serveurs MCP » de Claude Desktop) :

```json
{
  "mcpServers": {
    "datagouv": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://mcp.data.gouv.fr/mcp"
      ]
    }
  }
}
```

3. Relancez Claude Desktop.

**Sous Windows :** si le serveur apparaît dans la liste mais ne se connecte pas, ajoutez `"isUsingBuiltInNodeForMcp": false` à la racine du fichier de configuration, puis relancez Claude Desktop. Voir [issue #69](https://github.com/datagouv/datagouv-mcp/issues/69).

</details>

<details>

<summary>Cursor</summary>

1. Ouvrez les paramètres Cursor.
2. Recherchez « MCP » ou « Model Context Protocol ».
3. Ajoutez un serveur MCP avec la configuration suivante (Cursor emploie le terme « serveur MCP », et non « connecteur ») :

```json
{
  "mcpServers": {
    "datagouv": {
      "url": "https://mcp.data.gouv.fr/mcp",
      "transport": "http"
    }
  }
}
```

</details>

<details>

<summary>Gemini CLI</summary>

1. Ouvrez `~/.gemini/settings.json` (Windows : `%USERPROFILE%\.gemini\settings.json`).
2. Ajoutez :

```json
{
  "mcpServers": {
    "datagouv": {
      "httpUrl": "https://mcp.data.gouv.fr/mcp"
    }
  }
}
```

</details>

<details>

<summary>HuggingChat</summary>

1. Dans l’interface de chat, cliquez sur **+**, sélectionnez `MCP Servers`, puis `Manage MCP Servers`.
2. Cliquez sur **Add Server**.
3. Renseignez un nom (par ex. « Data Gouv ») et l’URL `https://mcp.data.gouv.fr/mcp`, puis enregistrez.
4. Cliquez sur **Health Check** pour vérifier que le statut est **Connected**, puis activez le serveur MCP.

</details>

<details>

<summary>IBM Bob</summary>

1. Cliquez sur l’icône de paramètres dans le panneau Bob.
2. Sélectionnez l’onglet MCP.
3. Ouvrez la configuration globale (`mcp_settings.json`) ou projet (`.bob/mcp.json`).
4. Ajoutez :

```json
{
  "mcpServers": {
    "datagouv": {
      "url": "https://mcp.data.gouv.fr/mcp",
      "type": "streamable-http"
    }
  }
}
```

</details>

<details>

<summary>Kiro CLI</summary>

1. Ouvrez `~/.kiro/settings/mcp.json` (Windows : `%USERPROFILE%\.kiro\settings\mcp.json`).
2. Ajoutez :

```json
{
  "mcpServers": {
    "datagouv": {
      "url": "https://mcp.data.gouv.fr/mcp"
    }
  }
}
```

</details>

<details>

<summary>Kiro IDE</summary>

1. Ouvrez `.kiro/settings/mcp.json` dans votre espace de travail, ou `~/.kiro/settings/mcp.json` pour une configuration globale (Windows : `%USERPROFILE%\.kiro\settings\mcp.json`).
2. Ajoutez :

```json
{
  "mcpServers": {
    "datagouv": {
      "url": "https://mcp.data.gouv.fr/mcp"
    }
  }
}
```

</details>

<details>

<summary>Le Chat (Mistral)</summary>

*Disponible sur tous les plans, y compris gratuit. Le Chat (Mistral) parle de **connecteurs**.*

1. Ouvrez Mistral dans votre navigateur, puis allez dans `Intelligence` > `Connectors`.
2. Cliquez sur `Add connector` > `Custom MCP Connector`, donnez un nom (par ex. `DataGouv`) et renseignez l’URL `https://mcp.data.gouv.fr/mcp`.
3. Laissez l’authentification désactivée.
4. Cliquez sur **Create**.

</details>

<details>

<summary>Mistral Vibe CLI</summary>

1. Éditez `~/.vibe/config.toml` (Windows : `%USERPROFILE%\.vibe\config.toml`).
2. Ajoutez :

```toml
[[mcp_servers]]
name = "datagouv"
transport = "streamable-http"
url = "https://mcp.data.gouv.fr/mcp"
```

Voir la [documentation Vibe](https://github.com/mistralai/mistral-vibe?tab=readme-ov-file#mcp-server-configuration) pour les options complètes.

</details>

<details>

<summary>OpenCode</summary>

1. Éditez `opencode.json` (par ex. `~/.config/opencode/opencode.json` ou à la racine de votre projet).
2. Ajoutez :

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "datagouv": {
      "type": "remote",
      "url": "https://mcp.data.gouv.fr/mcp",
      "enabled": true
    }
  }
}
```

Voir la [documentation OpenCode](https://opencode.ai/docs/mcp-servers/) pour plus de détails.

</details>

<details>

<summary>VS Code</summary>

1. Ouvrez `mcp.json` via la palette de commandes (**MCP: Open User Configuration**) :
   * **Linux** : `~/.config/Code/User/mcp.json`
   * **macOS** : `~/Library/Application Support/Code/User/mcp.json`
   * **Windows** : `%APPDATA%\Code\User\mcp.json`
2. Ajoutez :

```json
{
  "servers": {
    "datagouv": {
      "url": "https://mcp.data.gouv.fr/mcp",
      "type": "http"
    }
  }
}
```

</details>

<details>

<summary>Windsurf</summary>

1. Ouvrez `~/.codeium/windsurf/mcp_config.json` (Windows : `%USERPROFILE%\.codeium\windsurf\mcp_config.json`).
2. Ajoutez :

```json
{
  "mcpServers": {
    "datagouv": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.data.gouv.fr/mcp"
      ]
    }
  }
}
```

3. Relancez Windsurf si nécessaire.

</details>

## Pour aller plus loin

Ce guide couvre la connexion des principaux chatbots. Pour plus de détails (outils, cas particuliers, self-host), consultez le [README du dépôt datagouv-mcp](https://github.com/datagouv/datagouv-mcp?tab=readme-ov-file).
