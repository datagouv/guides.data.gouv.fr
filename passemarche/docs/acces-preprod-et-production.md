# Accès Preprod et Production

L'accès aux environnements avec données réelles se fait en deux temps : d'abord la Preprod pour la recette, puis la Production. L'équipe Passe Marché accompagne ce processus.

**Étapes** : Staging → demande d'accès Preprod → recette avec données réelles → Production

Pour le détail des URLs et caractéristiques de chaque environnement, voir [08\_environnements.md](08_environnements.md "mention").

***

### Prérequis pour accéder à Preprod

Les points suivants doivent être validés sur Staging avant de faire la demande d'accès :

* [ ] Authentification OAuth2 (obtention du token)
* [ ] Création d'un marché avec un SIRET valide
* [ ] Soumission d'une candidature de bout en bout
* [ ] Webhooks opérationnels (voir [07\_webhooks.md](07_webhooks.md "mention"))
* [ ] Gestion des erreurs HTTP (401, 422, 500…)
* [ ] Retour utilisateur vers votre plateforme après complétion

> **Attention** : Les données en Preprod sont des données réelles d'entreprises françaises — les mêmes précautions qu'en production s'appliquent.

***

### Réception des identifiants

Les identifiants seront transmis via un canal sécurisé certifié ANSSI avec chiffrement bout en bout. Un lien sécurisé sera envoyé pour les télécharger. Une confirmation de bonne réception permettra à l'équipe de supprimer le fichier du serveur.

***

### Stockage des identifiants

Les identifiants ne doivent pas apparaître dans le code source, les fichiers de configuration versionnés ou les logs. L'injection par variables d'environnement est la pratique standard :

```bash
PASSEMARCHE_CLIENT_ID=votre_client_id
PASSEMARCHE_CLIENT_SECRET=votre_client_secret
PASSEMARCHE_WEBHOOK_SECRET=votre_webhook_secret
PASSEMARCHE_URL=https://preprod.passemarche.data.gouv.fr
```

Pour le stockage en équipe, un gestionnaire de mots de passe ou un coffre-fort de secrets est recommandé.

***

### Contact

Pour toute demande d'accès, contacter l'équipe Passe Marché via les coordonnées reçues lors de votre enregistrement.
