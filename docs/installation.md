# Installation

Compter environ une heure pour l'installation et les tests. Les intitulés de l'interface n8n sont donnés en anglais, langue par défaut de l'outil.

## Prérequis

- Une instance n8n (n8n Cloud ou auto-hébergée)
- Un compte Pipedrive avec accès à l'API
- Une clé API Google AI Studio (Gemini)
- Une boîte Gmail dédiée à la prospection
- Pour l'identification des contacts : LinkedIn Sales Navigator et Dropcontact (intégration Pipedrive)

## 1. Préparer Pipedrive

1. Créer un pipeline nommé exactement **Prospection Résonance**.
2. Y créer les 8 étapes, dans cet ordre et avec ces noms exacts : `À rechercher`, `À qualifier`, `Prêt à contacter`, `Contacté`, `À relancer`, `Conversation ouverte`, `Rendez-vous`, `En pause`.
3. Récupérer le token API : avatar en haut à droite > **Paramètres personnels** > **API** > copier **Votre jeton API personnel**.

Les 35 champs personnalisés n'ont pas à être créés à la main : le workflow 0 s'en charge.

## 2. Créer les trois identifiants dans n8n

Dans n8n : **Overview** > onglet **Credentials** > **Create credential**.

| Nom à donner | Type à chercher | Champs |
|---|---|---|
| Pipedrive — token API | Query Auth | Name : `api_token` · Value : le token Pipedrive |
| Gemini — clé API | Header Auth | Name : `x-goog-api-key` · Value : la clé Google AI Studio |
| Gmail — boîte Résonance | Gmail OAuth2 API | Se connecter avec la boîte dédiée (**Sign in with Google**) |

## 3. Lancer l'installation Pipedrive

1. **Create workflow** > menu **...** en haut à droite > **Import from File...** > `workflows/00_installation_pipedrive.json`.
2. Ouvrir les 4 nœuds HTTP (`Étapes`, `Champs affaires`, `Champs personnes`, `Créer le champ`). Dans **Credential for Query Auth**, choisir **Pipedrive — token API**.
3. Cliquer **Execute workflow** (ou **Test workflow** selon la version).
4. Ouvrir le nœud **Bilan**. Il doit afficher la liste des champs créés et « Les 8 étapes sont correctes ». Le workflow peut être relancé sans risque : les champs existants sont ignorés.

## 4. Importer les sept agents

Importer les fichiers `01` à `06` de la même façon. Dans chaque workflow :

1. Ouvrir chaque nœud HTTP signalé en rouge et choisir l'identifiant correspondant :
   - les nœuds qui appellent `api.pipedrive.com` : **Pipedrive — token API** ;
   - les nœuds `Gemini · …` : **Gemini — clé API** ;
   - les nœuds qui appellent `gmail.googleapis.com` : **Gmail — boîte Résonance**.

   Le nœud `Lire la page source` de l'agent 2 n'a pas besoin d'identifiant.
2. Ouvrir le nœud **CONFIG** et remplir les valeurs. La configuration doit être **identique dans les sept workflows** : la remplir une fois, puis la copier-coller dans les autres.

| Valeur | À saisir |
|---|---|
| `gemini_model` | Un ou plusieurs modèles disponibles dans Google AI Studio, séparés par des virgules |
| `signataire` | Prénom et nom de la personne qui signe |
| `emails_fondatrices` | Adresses qui reçoivent les alertes et l'arbitrage du lundi (vide = la boîte connectée) |
| `lien_rdv` | Lien de prise de rendez-vous (Calendly ou équivalent) |
| `flux_rss` | URL des flux de veille |
| `preuves` | La bibliothèque de preuves validée par les fondatrices |

## 5. Configurer la veille

- **Google Alertes** : sur google.com/alerts, créer une alerte par thème. Cliquer **Afficher les options** > **Distribuer à** > **Flux RSS** > **Créer l'alerte**. Copier ensuite l'URL du flux (icône RSS) dans `flux_rss`.
- **Newsletters et alertes Sales Navigator** : dans Gmail, créer le libellé `veille` et un filtre qui l'applique automatiquement aux expéditeurs concernés.

## 6. Tester dans l'ordre

Chaque workflow a un déclencheur **Lancer maintenant (test)**. Tester dans l'ordre du parcours :

1. **Agent 1** : vérifier qu'une affaire « À rechercher » apparaît, avec sa note de signal. Si rien n'est retenu, le message d'erreur liste le motif de chaque rejet.
2. Associer à cette affaire un contact avec email, civilité (F ou M) et poste.
3. **Agent 2** : lire la note « Fiche compte » ; l'affaire passe à « À qualifier » si le fait est vérifié.
4. **Agent 3** : lire la note de score.
5. Passer **Activer** à `Oui`, puis lancer l'**agent 4** : le brouillon doit apparaître dans Gmail, et la note de contrôle sur l'affaire.
6. Envoyer le brouillon à une adresse de test, passer l'affaire à « Prêt à contacter », lancer l'**agent 5a** : l'affaire passe à « Contacté ».
7. Répondre depuis l'adresse de test, lancer l'**agent 5b** : la réponse est classée et l'affaire mise à jour.
8. **Agent 6** : vérifier la réception de l'email du lundi et des deux fichiers CSV.

## 7. Mettre en service

Activer chaque workflow avec l'interrupteur **Active** (ou **Publish** selon la version), en commençant par l'agent 6 et en terminant par l'agent 1. Le workflow 0 reste inactif.

## En cas d'erreur

| Message | Cause | Correction |
|---|---|---|
| `À créer dans Pipedrive (noms exacts) : …` | Champ ou étape absent, ou nom différent | Relancer le workflow 0, ou corriger le nom indiqué |
| `Signaux rejetés : …` | Aucun article ne contient de signal exploitable | Normal en test ; élargir les flux de veille si cela se répète |
| Note « Brouillon non déposé » | Un contrôle a échoué | Corriger la cause indiquée dans la note, puis vider « Brouillon généré » |
| Fait « À vérifier manuellement » | Page payante ou extrait reformulé | Remplacer l'URL ou l'extrait, puis vider « Fait vérifié » |
| Erreur 429 sur un nœud Gemini | Quota du modèle atteint | Ajouter un second modèle dans `gemini_model` |
