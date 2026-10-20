# Schéma Pipedrive

Les agents retrouvent les champs et les étapes **par leur nom exact**, accents et majuscules compris. Le workflow 0 crée automatiquement les champs manquants et signale les étapes absentes ou mal écrites.

## Pipeline « Prospection Résonance »

Les 8 étapes, dans l'ordre :

| Étape | Qui y fait entrer l'affaire |
|---|---|
| À rechercher | Agent 1 (nouveau signal) ou agent 5b (email invalide) |
| À qualifier | Agent 2 (fait vérifié) |
| Prêt à contacter | Humain, après relecture et envoi du brouillon |
| Contacté | Agent 5a (envoi constaté dans Gmail) |
| À relancer | Agent 5a (relance préparée) |
| Conversation ouverte | Agent 5b (réponse positive ou ambiguë) |
| Rendez-vous | Humain |
| En pause | Agent 3 (score archivé) ou agent 5b (« pas le moment ») |

## Champs de l'affaire (29)

Type « texte long » pour les champs marqués *, « texte » pour les autres.

| Champ | Écrit par | Contenu |
|---|---|---|
| Type de signal | Agent 1 | L'un des 6 types retenus |
| URL source | Agent 1 | Lien de l'article |
| Date de publication | Agent 1 | AAAA-MM-JJ |
| Extrait source * | Agent 1 | Citation mot pour mot, moins de 30 mots |
| Résumé du signal * | Agent 1 | Une phrase factuelle |
| Catégorie | Agent 1 | Segment de la maison (7 valeurs) |
| Taille budget | Humain | Barème du critère 5 |
| Porte d'entrée | Humain | Barème du critère 7 |
| Adéquation expertises | Agent 2 | Barème du critère 2 |
| Fait vérifié * | Agent 2 | « Vérifié : », « À vérifier manuellement : » ou « Échec : » |
| Hypothèse * | Agent 2 | Commence par « Hypothèse : » |
| Preuve A&L | Agent 2 | Identifiant d'une preuve de la configuration |
| Score Résonance | Agent 3 | Note sur 100 |
| Détail du score * | Agent 3 | Points par critère |
| Motif du score * | Agent 3 | Une phrase |
| Niveau | Agent 3 | A · Priorité, B · Réserve, C · Veille, Archivé |
| Angle | Agent 3, puis 4 | Angle de valeur selon la fonction |
| Prochaine action | Agent 3 | Action recommandée selon le niveau |
| Activer | Humain | « Oui » pour lancer la rédaction |
| Discrétion IA | Humain | Absente (défaut), Évoquée, Présentée |
| Brouillon généré | Agent 4 | Date, type et identifiant du brouillon, ou « Bloqué » |
| Texte du dernier message * | Agent 4 | Corps du dernier message rédigé |
| Date premier envoi | Agent 5a | Date constatée dans Gmail |
| Nb relances | Agent 5a | 0 à 3 |
| Tâche LinkedIn | Agent 5a | Date de création de la tâche |
| Reprise le | Agents 4 et 5b | Date avant laquelle la séquence est suspendue |
| Date de réactivation | Agent 5b | Date à partir de laquelle recontacter |
| Motif de refus | Agents 5a et 5b | Pas le moment, Pas de besoin, Déjà un partenaire, Sans réponse |
| Fin de conservation | Agent 2 | Date du jour plus 36 mois |

## Champs de la personne (6)

| Champ | Écrit par | Contenu |
|---|---|---|
| Civilité | Humain | F ou M (bloque la rédaction si vide) |
| Poste | Humain | Intitulé exact, utilisé pour déduire la fonction |
| Niveau de décision | Agent 2, si vide | Direction, Head / VP, Manager, Chef de projet, Hors cible |
| Opposition | Agent 5b | « Oui » suivi de la date |
| Provenance coordonnées | Agent 2, si vide | Source et date de collecte |
| Fiabilité email | Agents 2 et 5b | À confirmer, Manquant, Erronée |

## Notes

Chaque agent laisse une note datée sur l'affaire. Elle récapitule les données utilisées, la décision prise et, le cas échéant, ce qu'il faut corriger. L'historique d'une affaire se lit donc comme un journal, sans ouvrir n8n.
