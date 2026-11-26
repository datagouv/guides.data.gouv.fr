# Flux Candidat - Soumission des Candidatures

## Vue d'ensemble

Le flux candidat dans Passe Marché permet aux plateformes de marchés publics de créer des candidatures pour leurs entreprises utilisatrices, puis de les rediriger vers une interface dédiée pour compléter leur dossier de candidature. Ce processus garantit la conformité réglementaire tout en simplifiant l'expérience utilisateur.

## Environnements

Les exemples de ce document utilisent `${BASE_URL}` comme placeholder. Consultez la [documentation des environnements](08_environnements.md) pour les URLs spécifiques à chaque environnement.

## Architecture du Flux

```
┌─────────────────┐    1. Token d'accès      ┌─────────────────┐
│   Plateforme    │ ◄────────────────────────│   Authentification │
│   Éditeur       │                          │   OAuth2           │
└─────────────────┘                          └─────────────────┘

┌─────────────────┐    2. Création candidature ┌─────────────────┐
│   Plateforme    │ ──────────────────────────▶│   API Voie      │
│   Éditeur       │◄────────────────────────── │   Rapide        │
└─────────────────┘    3. URL candidature     └─────────────────┘

┌─────────────────┐    4. Redirection         ┌─────────────────┐
│   Candidat      │ ──────────────────────────▶│   Interface     │
│   Entreprise    │◄────────────────────────── │   Candidature   │
└─────────────────┘    5. Formulaire dynamique└─────────────────┘

┌─────────────────┐    6. Finalisation        ┌─────────────────┐
│   Candidat      │ ──────────────────────────▶│   Génération    │
│   Entreprise    │◄────────────────────────── │   Documents     │
└─────────────────┘    7. Attestation/Dossier └─────────────────┘

┌─────────────────┐    8. Notification        ┌─────────────────┐
│   Plateforme    │ ◄────────────────────────  │   Webhook       │
│   Éditeur       │                          │   Complétion    │
└─────────────────┘                          └─────────────────┘
```

## Étapes Détaillées du Flux

### 1. Prérequis d'Authentification

**Token OAuth requis** : Token d'accès valide obtenu via le flux Client Credentials.

Consultez la [Documentation OAuth](02_authentification_oauth.md) pour l'implémentation.

### 2. Création de la Candidature

#### Endpoint

`POST /api/v1/public_markets/{market_identifier}/market_applications`

#### Requête

```http
POST /api/v1/public_markets/VR-2024-A1B2C3D4E5F6/market_applications HTTP/1.1
Host: ${BASE_URL}
Authorization: Bearer {access_token}
Content-Type: application/json

{
  "market_application": {
    "siret": "12345678901234"
  }
}
```

#### Paramètres

| Champ                           | Type   | Description                                          | Contraintes                                                                             |
| ------------------------------- | ------ | ---------------------------------------------------- | --------------------------------------------------------------------------------------- |
| `market_identifier`             | string | Identifiant du marché public                         | Requis, format VR-YYYY-XXXXXXXXXXXX                                                     |
| `siret`                         | string | Numéro SIRET de l'entreprise                         | Optionnel à la création, 14 chiffres                                                    |
| `provider_user_id`              | string | Identifiant de l'utilisateur côté éditeur (candidat) | Optionnel, max 255 caractères                                                           |
| <p><code>lot_ids</code><br></p> | array  | Lots choisis par le candidat sur la plateforme       | Optionnel, tableau non vide d'entiers : les `id` des lots du webhook `market.completed` |
| `application_mode`              | string | Type de candidature choisi sur la plateforme         | Obligatoire si `lot_ids` est transmis : `"solo"` ou `"groupement"`                      |

**Note importante** : Le SIRET peut être fourni à la création ou lors de l'étape d'identification dans l'interface candidat.

#### Réponse de Succès (201 Created / 200 OK)

* `201 Created` : une nouvelle candidature a été créée
* `200 OK` : une candidature existe déjà pour ce SIRET sur ce marché, elle est renvoyée (voir ci-dessous)

Le corps de la réponse est identique dans les deux cas.

```json
{
  "identifier": "FT20240615A1B2C3D4",
  "application_url": "${BASE_URL}/candidate/market_applications/FT20240615A1B2C3D4/company_identification"
}
```

**Paramètres de Réponse** :

* `identifier` : Identifiant unique de la candidature (format FT + date + hash)
* `application_url` : URL vers l'interface de candidature

#### **Transmettre les lots choisis sur la plateforme**

Si le candidat a déjà choisi ses lots sur votre plateforme, transmettez-les dans `lot_ids`. Il n'aura pas à les choisir une deuxième fois dans Passe Marché.

Cette transmission concerne uniquement les **candidatures individuelles**.

**D'où viennent les identifiants**

Les lots que vous envoyez à la création du marché sont enregistrés par Passe Marché, qui leur attribue un `id`. Le webhook `market.completed` vous renvoie tous les lots du marché, dans l'ordre où vous les avez créés, avec cet `id` (`market.lots[].id`). Renvoyez-nous les `id` des lots choisis par le candidat. N'utilisez ni le numéro ni le nom du lot.

**Format attendu**

* `application_mode` est obligatoire dès que `lot_ids` est transmis : `"solo"` ou `"groupement"`.
* `lot_ids` est un tableau JSON non vide d'entiers.
* Un identifiant envoyé deux fois n'est pris en compte qu'une fois.

```json
{
  "market_application": {
    "siret": "12345678901234",
    "application_mode": "solo",
    "lot_ids": [101, 103]
  }
}
```

**Candidature individuelle (`"solo"`)**

* La candidature est créée en individuel. Le candidat ne peut pas la transformer en groupement dans Passe Marché.
* L'écran de sélection des lots ne lui est pas proposé. Ses lots sont affichés en lecture seule pendant tout le parcours (préparation du dossier, synthèse, attestation).
* Un message l'invite à modifier ses lots sur votre plateforme.

**Groupement (`"groupement"`)**

En groupement, le choix des lots se fait dans Passe Marché. Le mandataire y sélectionne les lots du groupement, puis chaque co-traitant y indique les lots auxquels il participe. Cette répartition dépend de la composition du groupement.

**Erreurs**

En cas d'erreur, la réponse est `422` et la candidature n'est ni créée ni modifiée.

| Cas                                                                   | Champ                     | Message                                                                                                                  |
| --------------------------------------------------------------------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| `lot_ids` transmis sans `application_mode`, ou avec une autre valeur  | `errors.application_mode` | « Le type de candidature (application\_mode) est obligatoire quand des lots sont transmis : « solo » ou « groupement » » |
| `[]`, `null`, un nombre seul (`101`) ou un objet                      | `errors.lot_ids`          | « Vous devez sélectionner au moins un lot »                                                                              |
| Une valeur qui n'est pas un identifiant entier (`"abc"`, `1.5`, `-3`) | `errors.lot_ids`          | « Un ou plusieurs identifiants de lot ne sont pas valides »                                                              |
| Un identifiant inconnu, ou celui d'un lot d'un autre marché           | `errors.lot_ids`          | « Un ou plusieurs lots sélectionnés n'appartiennent pas à ce marché »                                                    |

Le tableau `errors.lot_ids` peut contenir plusieurs messages.

**Changer les lots**

Rappelez l'API avec le même SIRET, `"application_mode": "solo"` et la nouvelle liste `lot_ids`. La réponse est `200`.

* La nouvelle liste remplace l'ancienne. Les réponses déjà saisies sont conservées, sauf celles qui ne concernent que des types de lots retirés.
* Si vous ajoutez un lot d'un nouveau type, les champs correspondants sont ajoutés au dossier et les données récupérées automatiquement sont relancées. Un message prévient le candidat jusqu'à sa transmission.
* Une fois la date limite passée, `lot_ids` est ignoré pour une candidature déjà transmise : la réponse est `200` et les lots déposés ne changent pas.

**Si `lot_ids` n'est pas transmis**

* À la création, le parcours est inchangé : le candidat choisit son type de candidature et ses lots dans Passe Marché.
* Lors d'un rappel, les lots déjà transmis sont conservés et le candidat ne peut toujours pas les modifier.

#### Comportement en cas de re-candidature

Une entreprise dispose d'une seule candidature par marché. Elle n'est jamais remise à blanc : chaque nouveau dépôt met à jour la candidature existante.

Si une candidature complétée existe déjà pour le même SIRET sur ce marché et que la date limite n'est pas dépassée, l'appel rouvre automatiquement la candidature existante :

* Les **réponses du candidat** sont conservées (formulaire pré-rempli)
* Les **données issues des API** sont mises à jour lors du parcours candidat
* La **sélection des lots** reste modifiable :
  * si le candidat a choisi ses lots dans Passe Marché, il peut les modifier dans Passe Marché ;
  * si votre plateforme a transmis les lots, seul un nouvel appel avec `"application_mode": "solo"` et `lot_ids` permet de les modifier. Le candidat ne peut pas les changer dans Passe Marché.
* Une nouvelle attestation horodatée est générée à la nouvelle transmission
* L'identifiant de la candidature reste le même

Si une candidature en cours (non complétée) existe, elle est retournée telle quelle.

#### Traçabilité des dépôts

Chaque changement de `completed_at` (soumission ou réouverture) est historisé via PaperTrail. L'historique des versions permet de retrouver les dates de chaque dépôt et de chaque re-candidature.

#### Vérification de la date limite

Si la date limite est dépassée et qu'une candidature complétée existe, l'API retourne la candidature existante sans la rouvrir : elle n'est plus modifiable. La création et la poursuite d'une candidature en cours restent possibles même après la date limite.

Côté interface candidat, un candidat dont la candidature est complétée et dont le marché est fermé voit une page dédiée indiquant que la modification n'est plus possible.

#### Réponses d'Erreur

**Marché non trouvé (404)** :

```json
{
  "error": "Public market not found"
}
```

**Marché non accessible par l'éditeur (403)** :

```json
{
  "error": "Forbidden"
}
```

**Marché non encore publié (422)** :

```json
{
  "error": "La consultation n'est pas encore publiée, vous ne pouvez pas candidater à ce marché."
}
```

**SIRET invalide si fourni (422)** :

```json
{
  "errors": {
    "siret": ["n'est pas valide"]
  }
}
```

### 3. Interface de Candidature

La plateforme de marchés publics redirige l'entreprise vers l'URL fournie. L'interface s'adapte dynamiquement selon la configuration du marché public.

#### Génération Dynamique des Étapes

Les étapes sont générées automatiquement selon les champs configurés par l'acheteur :

```
company_identification → [catégories_configurées] → summary
```

**Exemple pour un marché "supplies + services"** :

```
company_identification → capacite_economique_financiere →
capacite_technique_professionnelle → summary
```

#### Étape 1 : Identification Entreprise

* **URL** : `/candidate/market_applications/{identifier}/company_identification`
* **Objectif** : Validation de l'identité de l'entreprise
* **Champs** :
  * SIRET (si non fourni à la création)
  * Nom de l'entreprise
  * Forme juridique
  * Adresse du siège social

#### Étapes Intermédiaires : Champs Métier

Chaque catégorie configurée par l'acheteur génère une étape :

**Capacité Économique et Financière** :

* Chiffre d'affaires des 3 dernières années
* Résultat net
* Capitaux propres
* Ratios financiers

**Capacité Technique et Professionnelle** :

* Effectifs
* Encadrement technique
* Certifications
* Références clients

**Autres Catégories** (selon configuration) :

* Assurances
* Sous-traitance
* Développement durable
* Innovation

#### Étape Finale : Résumé et Validation

* **URL** : `/candidate/market_applications/{identifier}/summary`
* **Objectif** : Validation finale et soumission
* **Actions** :
  * Récapitulatif de toutes les informations
  * Vérification de cohérence
  * Confirmation de soumission

### 4. Sécurité des fichiers déposés

Tous les fichiers déposés par les candidats sont automatiquement analysés par un antivirus avant d'être inclus dans le dossier de candidature.

* **Moteur** : ClamAV (open-source, maintenu par Cisco Talos, standard de référence pour le scan serveur)
* **Scan automatique** : chaque fichier est analysé en arrière-plan dès son upload
* **Statuts visibles** : un badge indique l'état du scan (vérifié, en cours, non vérifié, malware détecté)
* **Blocage des menaces** : un fichier identifié comme malveillant est bloqué et ne sera pas inclus dans le dossier final

Ce mécanisme garantit que les documents transmis aux acheteurs publics sont exempts de virus et de malware.

### 5. Processus de Complétion

#### Validation et Génération

Lors de la soumission finale :

1. **Validation des Données** : Vérification de la cohérence et complétude
2. **Vérification de sécurité** : Contrôle que tous les fichiers ont été scannés et sont sains
3. **Marquage Complété** : Passage en statut `completed`
4. **Génération de l'Attestation** : PDF officiel avec horodatage
5. **Création du Dossier** : Archive ZIP avec tous les éléments
6. **Déclenchement Webhook** : Notification vers la plateforme de marchés publics

#### Types de Documents Générés

**Attestation PDF** :

* Document officiel de soumission
* Horodatage légal
* Résumé des informations clés
* QR code de vérification

**Dossier Documents ZIP** :

* Attestation acheteur (PDF officiel)
* Documents des candidats issus de tous les types de champs permettant l'attachement de fichiers :
  * `FileUpload` : Fichiers téléchargés standard
  * `InlineFileUpload` : Fichiers téléchargés en ligne
  * `CheckboxWithDocument` : Fichiers conditionnels aux cases à cocher
  * `RadioWithFileAndText` : Fichiers avec sélection radio
  * `RadioWithJustificationRequired` : Justifications obligatoires
  * `RadioWithJustificationOptional` : Justifications optionnelles
  * `FileOrTextarea` : Fichiers ou texte
  * `PresentationIntervenants` : CV des intervenants
  * `RealisationsLivraisons` : Attestations de réalisations
  * `CapacitesTechniquesProfessionnellesOutillageEchantillons` : Échantillons et outillage
* Nom de fichiers structuré : `{index_réponse}_{index_document}_{clé_champ}_{nom_original}`
* Exemple : `01_01_kbis_Kbis_Entreprise.pdf`

### 6. Statuts de la Candidature

| Statut            | Description          | Actions Disponibles          |
| ----------------- | -------------------- | ---------------------------- |
| `pending`         | En cours de saisie   | Modification, progression    |
| `completed`       | Finalisée et validée | Consultation, téléchargement |
| `sync_pending`    | Attente notification | -                            |
| `sync_processing` | Webhook en cours     | -                            |
| `sync_completed`  | Notification réussie | -                            |
| `sync_failed`     | Échec notification   | Retry disponible             |

### 7. Webhook de Complétion

#### Déclenchement Automatique

Le webhook est envoyé automatiquement lors de la finalisation de la candidature.

#### Payload du Webhook

```json
{
  "event": "market_application.completed",
  "timestamp": "2024-06-15T16:45:30Z",
  "market_identifier": "VR-2024-A1B2C3D4E5F6",
  "market_application": {
    "identifier": "FT20240615A1B2C3D4",
    "siret": "12345678901234",
    "company_name": "ACME Solutions SARL",
    "completed_at": "2024-06-15T16:45:30Z",
    "attestation_url": "${BASE_URL}/api/v1/market_applications/FT20240615A1B2C3D4/attestation",
    "documents_package_url": "${BASE_URL}/api/v1/market_applications/FT20240615A1B2C3D4/documents_package"
  }
}
```

#### Paramètres du Payload

| Champ                                      | Description                                       |
| ------------------------------------------ | ------------------------------------------------- |
| `event`                                    | Type d'événement (`market_application.completed`) |
| `market_identifier`                        | Identifiant du marché public                      |
| `market_application.identifier`            | Identifiant de la candidature                     |
| `market_application.siret`                 | SIRET de l'entreprise candidate                   |
| `market_application.attestation_url`       | URL de téléchargement de l'attestation            |
| `market_application.documents_package_url` | URL de téléchargement du dossier                  |

#### Transmissions successives

Une même candidature peut être transmise plusieurs fois avant la date limite (ajout d'un lot, correction…). Chaque transmission déclenche un webhook avec le même `identifier` et un nouveau `completed_at`.

* Chaque transmission remplace la précédente : à traiter comme une nouvelle version de la même candidature
* Les URLs de l'attestation et du dossier ne changent pas mais pointent vers les documents à jour : à retélécharger-les à chaque webhook

### 8. Téléchargement des Documents

Une fois la candidature finalisée, la plateforme de marchés publics peut télécharger les documents générés.

#### Téléchargement de l'Attestation

**Endpoint** : `GET /api/v1/market_applications/{identifier}/attestation`

```http
GET /api/v1/market_applications/FT20240615A1B2C3D4/attestation HTTP/1.1
Host: ${BASE_URL}
Authorization: Bearer {access_token}
```

**Réponse** : Fichier PDF en binaire

```http
HTTP/1.1 200 OK
Content-Type: application/pdf
Content-Disposition: attachment; filename="attestation_FT20240615A1B2C3D4.pdf"
Content-Length: 245760

[Binary PDF content]
```

#### Téléchargement du Dossier Complet

**Endpoint** : `GET /api/v1/market_applications/{identifier}/documents_package`

```http
GET /api/v1/market_applications/FT20240615A1B2C3D4/documents_package HTTP/1.1
Host: ${BASE_URL}
Authorization: Bearer {access_token}
```

**Réponse** : Archive ZIP en binaire

```http
HTTP/1.1 200 OK
Content-Type: application/zip
Content-Disposition: attachment; filename="documents_package_FT20240615A1B2C3D4.zip"
Content-Length: 1048576

[Binary ZIP content]
```

#### Conditions de Téléchargement

* Candidature en statut `completed`
* Token d'accès valide de l'éditeur propriétaire
* Documents générés et disponibles

#### Réponses d'Erreur pour Téléchargement

**Candidature non finalisée (422)** :

```json
{
  "error": "Application not completed"
}
```

**Document non disponible (404)** :

```json
{
  "error": "Attestation not available"
}
```

## Champs de Candidature Dynamiques

### Types de Champs Supportés

#### Champs de Base

* **Texte libre** : Descriptions, commentaires
* **Nombre entier** : Effectifs, quantités
* **Nombre décimal** : Montants, ratios
* **Date** : Échéances, créations
* **Oui/Non** : Certifications, capacités
* **Choix unique** : Sélection dans une liste
* **Choix multiple** : Sélections multiples

#### Champs Composites Métier

* **Chiffre d'affaires annuel** : 3 années + pourcentages marché
* **Références client** : Nom, montant, période, contact
* **Assurances** : Compagnie, garantie, montant, période
* **Certifications** : Organisme, norme, validité

### Validation des Données

#### Validation Frontend

* Contrôles en temps réel
* Messages d'erreur contextuels
* Prévention de soumission incomplète

#### Validation Backend

* Vérification de cohérence
* Validation métier (SIRET, dates)
* Contrôles d'intégrité

### Exemple de Champ Composite : Chiffre d'Affaires

```json
{
  "field_type": "capacite_economique_financiere_chiffre_affaires_global_annuel",
  "value": {
    "year_1": {
      "turnover": 1500000,
      "market_percentage": 75,
      "fiscal_year_end": "2023-12-31"
    },
    "year_2": {
      "turnover": 1350000,
      "market_percentage": 80,
      "fiscal_year_end": "2022-12-31"
    },
    "year_3": {
      "turnover": 1200000,
      "market_percentage": 70,
      "fiscal_year_end": "2021-12-31"
    }
  }
}
```

## Gestion des Erreurs et Cas Limites

### Candidature Déjà Finalisée

* Redirection vers page de statut
* Affichage des informations de complétion
* Liens de téléchargement si disponibles

### Session Expirée

* Sauvegarde automatique de la progression
* Reprise à la dernière étape validée
* Conservation des données 7 jours

### Erreurs de Validation

* Messages d'erreur détaillés par champ
* Préservation des données saisies
* Navigation facilitée vers les erreurs

### Marché Expiré

* Vérification de la date limite
* Blocage de soumission si dépassée
* Message informatif avec détails

## Monitoring et Observabilité

### Métriques de Performance

* **Taux de complétion** : Candidatures démarrées vs finalisées
* **Temps de saisie** : Durée moyenne par étape
* **Taux d'abandon** : Abandons par étape et raison
* **Erreurs de validation** : Fréquence par type de champ

### Logs Applicatifs

**Éléments recommandés à logger** :

* Création de candidatures (identifiant, marché, SIRET)
* Webhooks reçus (événement, statut, documents disponibles)
* Téléchargements de documents (type, taille)
* Erreurs de validation et d'API

**🔗 Scripts de logging** : [Scripts de Référence - Logging candidatures](99_scripts_reference.md#logging-candidatures)

## Bonnes Pratiques d'Intégration

### Côté Plateforme de Marchés Publics

1. **Validation Préalable** : Vérifier la validité du marché avant création
2. **Gestion du SIRET** : Permettre saisie ultérieure si non disponible
3. **Webhook Idempotent** : Gérer les réceptions multiples du même événement et les transmissions successives d'une même candidature
4. **Stockage Sécurisé** : Protéger les URLs de téléchargement
5. **UX Cohérente** : Intégrer harmonieusement les redirections

### Scripts d'Automatisation

**Fonctionnalités disponibles** :

* Gestionnaire complet de candidatures (création, webhooks, téléchargements)
* Cache local des candidatures créées
* Gestion d'erreurs et logging détaillé
* Téléchargement automatique des documents (PDF/ZIP)
* Statistiques et monitoring des opérations

**🔗 Scripts complets** : [Scripts de Référence - Gestionnaire de candidatures](99_scripts_reference.md#gestionnaire-de-candidatures---script-complet)

Ce flux candidat assure une expérience utilisateur optimisée tout en maintenant la conformité réglementaire et la traçabilité requises pour les marchés publics.
