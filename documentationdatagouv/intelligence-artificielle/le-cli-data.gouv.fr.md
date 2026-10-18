---
description: Installer et utiliser l’outil en ligne de commande data.gouv.fr.
icon: terminal
---

# Le CLI data.gouv.fr

[`datagouv-cli`](https://github.com/datagouv/datagouv-cli) est l’outil en ligne de commande de [data.gouv.fr](https://www.data.gouv.fr). La commande s’appelle `datagouv`. Elle permet de consulter et de modifier des jeux de données, des organisations, des ressources et des thématiques depuis un terminal, sur Linux, macOS et Windows.

Vous lancez les commandes vous-même. Un assistant capable d’exécuter des commandes peut aussi s’en servir. Voir aussi le [serveur MCP](le-serveur-mcp-de-data.gouv.fr.md) et le [skill](le-skill-data.gouv.fr.md).

La lecture du catalogue de production ne demande ni configuration ni clé d’API. Pour créer ou modifier des contenus, il faut une [clé d’API](https://www.data.gouv.fr/admin/me/profile) et les mêmes droits que sur le site.

## Installation

Aucune autre dépendance n’est nécessaire : l’installation fournit un programme prêt à l’emploi.

### Installation rapide (Linux et macOS)

```bash
curl -fsSL https://raw.githubusercontent.com/datagouv/datagouv-cli/main/scripts/install.sh | bash
```

### Autres méthodes

<details>

<summary>Archive à installer soi-même</summary>

Téléchargez l’archive de votre système depuis les [versions publiées](https://github.com/datagouv/datagouv-cli/releases), puis placez `datagouv` sur le `PATH`.

Sur Linux ou macOS, ces commandes choisissent l’archive adaptée à la machine :

```bash
curl -LO https://github.com/datagouv/datagouv-cli/releases/latest/download/datagouv-$(uname -s | tr '[:upper:]' '[:lower:]' | sed 's/darwin/macos/')-$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/').tar.gz
tar -xzf datagouv-*.tar.gz
sudo install -d /usr/local/lib/datagouv
sudo cp -a datagouv/. /usr/local/lib/datagouv/
sudo ln -sf /usr/local/lib/datagouv/datagouv /usr/local/bin/datagouv
```

Sur Windows (PowerShell) :

```powershell
Invoke-WebRequest -Uri https://github.com/datagouv/datagouv-cli/releases/latest/download/datagouv-windows-amd64.zip -OutFile datagouv-windows-amd64.zip
Expand-Archive datagouv-windows-amd64.zip -DestinationPath .
$installDir = "$env:LOCALAPPDATA\Programs\datagouv"
New-Item -ItemType Directory -Force -Path $installDir | Out-Null
Copy-Item -Recurse -Force datagouv\* $installDir
$env:Path += ";$installDir"
[Environment]::SetEnvironmentVariable("Path", $env:Path, "User")
```

</details>

<details>

<summary>APT (Debian et Ubuntu)</summary>

```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://datagouv.github.io/datagouv-cli/datagouv.gpg \
  | sudo gpg --dearmor -o /etc/apt/keyrings/datagouv.gpg
echo "deb [signed-by=/etc/apt/keyrings/datagouv.gpg] https://datagouv.github.io/datagouv-cli stable main" \
  | sudo tee /etc/apt/sources.list.d/datagouv.list
sudo apt update && sudo apt install datagouv
```

</details>

<details>

<summary>Homebrew (macOS)</summary>

```bash
brew tap datagouv/datagouv-cli https://github.com/datagouv/datagouv-cli.git
brew trust datagouv/datagouv-cli
brew install datagouv
```

</details>

<details>

<summary>Chocolatey (Windows)</summary>

Depuis une [version publiée](https://github.com/datagouv/datagouv-cli/releases), remplacez `vX.Y.Z` par le numéro souhaité :

```powershell
choco install datagouv --source="https://github.com/datagouv/datagouv-cli/releases/download/vX.Y.Z"
```

</details>

Vérifiez l’installation :

```bash
datagouv --help
```

## Configuration

`datagouv setup` demande la plateforme à utiliser et, si besoin, votre clé d’API. Les réponses sont enregistrées dans votre dossier personnel (`~/.datagouv_config.json`).

```bash
datagouv setup
```

| Plateforme | Valeur à indiquer |
| ---------- | ----------------- |
| Production ([data.gouv.fr](https://www.data.gouv.fr)) | `prod` (`www` convient aussi) |
| Démonstration ([demo.data.gouv.fr](https://demo.data.gouv.fr)) | `demo` |
| Développement | `dev` |

La clé doit être celle de la plateforme choisie. Vous pouvez la laisser vide si vous ne faites que lire des données.

Pour revenir à zéro, supprimez ce fichier :

```bash
datagouv delete-config
```

Vous pouvez aussi ignorer `setup` pour lire le catalogue de production : c’est la cible par défaut.

## Consulter

Quatre familles d’objets sont disponibles : `dataset` (jeu de données), `organization` (organisation), `resource` (ressource) et `topic` (thématique). Chacune propose les mêmes deux commandes de lecture.

`display` affiche les principaux champs, un par un :

```bash
datagouv organization display "534fff81a3a7292c64a77e5c"
```

```text
badges: [{'kind': 'public-service'}, {'kind': 'certified'}]
────────────────────
business_number_id: 12002701600563
────────────────────
created_at: 2014-04-17T18:21:21.523000+00:00
...
```

`get` renvoie toutes les métadonnées en JSON, telles que les fournit l’API. La sortie se prête à `jq` :

```bash
datagouv organization get "534fff81a3a7292c64a77e5c" | jq .name
```

```text
"Institut national de la statistique et des études économiques (Insee)"
```

## Modifier

Les commandes d’écriture exigent une clé d’API et les droits correspondants sur la plateforme. L’option `--set` ajoute ou remplace un champ. Vous pouvez la répéter.

{% hint style="warning" %}
Un jeu de données créé ainsi est **public** par défaut. Pour le garder en brouillon, passez `--set private=true` à la création et à chaque mise à jour. Sans cela, une modification peut le publier. Le détail est dans la [prise en main de l’API](../api-de-data.gouv.fr/prise-en-main/README.md).
{% endhint %}

Le titre et la description se donnent dans cet ordre. Indiquez `--organization-id` ou `--owner-id`, selon que le jeu appartient à une organisation ou à votre compte. La commande affiche ensuite l’identifiant à réutiliser.

```bash
datagouv dataset create "Nouveau jeu de données" "Une description claire" --organization-id "<identifiant-organisation>"
datagouv dataset update "<identifiant-jeu>" --set title="Nouveau titre" --set private=true
datagouv resource create "<identifiant-jeu>" "Première ressource" --file-to-upload fichier.csv --set type=main
datagouv resource delete "<identifiant-ressource>"
```

Pour une ressource déjà en ligne, remplacez `--file-to-upload` par `--url` et l’adresse du fichier. Pour récupérer un fichier en local :

```bash
datagouv resource download "<identifiant-ressource>" ./fichier.csv
```

Les autres objets suivent le même schéma (`create`, `update`, `delete`). Un jeu de données a en plus `sort-resources` pour réordonner ses fichiers, par exemple `title.asc`.

## Aide

`--help` existe pour chaque commande et chaque objet :

```bash
datagouv dataset --help
datagouv resource create --help
```

## Pour aller plus loin

Ce guide couvre l’installation et les usages courants. La référence des options, la contribution et les publications sont dans le [README de datagouv-cli](https://github.com/datagouv/datagouv-cli?tab=readme-ov-file).

Pour appeler l’API depuis un programme Python, utilisez [`datagouv-client`](https://github.com/datagouv/datagouv-client). Les mêmes opérations sont décrites, avec des exemples, dans [Gérer un jeu de données par l’API](../api-de-data.gouv.fr/prise-en-main/gerer-un-jeu-de-donnees-par-lapi.md).
