# Rédaction et contrôles

Dans le luxe, un message raté coûte plus cher qu'un message non envoyé. La rédaction est donc encadrée trois fois :
- avant le modèle, le code bloque une fiche incomplète ;
- pendant, la consigne limite ce que le modèle peut dire ;
- après, 9 contrôles vérifient ce qu'il a écrit.

## Ce que le modèle reçoit

Le modèle ne lit **que** la fiche compte, transmise en JSON :
- la civilité, le nom, le poste et la fonction du contact ;
- le fait vérifié, sans son URL ;
- l'hypothèse ;
- l'angle et le ton imposés ;
- le niveau de discrétion sur l'IA ;
- la phrase de preuve ;
- les messages déjà envoyés à la maison ;
- pour une relance, le message précédent.

Il lui est interdit d'inventer un chiffre, un projet, une citation ou une référence. S'il manque un élément, il doit écrire « [À COMPLÉTER] », ce qui bloque le brouillon.

## Structure d'un premier message

1. Objet court, lié au signal.
2. « Chère Madame » ou « Cher Monsieur », suivi du nom de famille ; vouvoiement.
3. Accroche : le fait vérifié, reformulé, sans flatterie.
4. Lecture de l'enjeu : l'hypothèse, sous forme de question ouverte.
5. Valeur : une expertise du studio reliée à l'enjeu, selon l'angle imposé.
6. Preuve : la phrase de la bibliothèque, telle quelle.
7. Proposition d'un échange de 20 minutes, sans pression.
8. Signature.

Le premier message fait de 90 à 140 mots. Il se termine par une mention d'information sur le traitement des coordonnées et le moyen de s'opposer.

## Angle selon la fonction du contact

La fonction est déduite du poste par mots-clés. Deux contacts d'une même maison ne reçoivent jamais le même angle.

| Fonction | Angle de valeur |
|---|---|
| Image (image, artistique, création) | Cohérence des codes, qualité de la direction créative |
| Marketing (marketing, CMO, direction générale) | Impact business d'une campagne, rythme de production |
| Brand (brand, marque) | Plateforme de marque, repositionnement |
| Digital (digital, innovation, numérique) | IA générative maîtrisée au service du désir |
| Communication (communication, presse, PR) | Éditorial, prises de parole, activations |

## Ton selon l'univers

| Catégorie | Ton |
|---|---|
| Mode & Maroquinerie | Élégant, tourné vers l'image et le savoir-faire |
| Joaillerie & Horlogerie | Raffiné, précis, patrimoine et exception |
| Beauté & Parfumerie | Sensoriel, moderne |
| Vins & Spiritueux, Hospitality & Lifestyle | Chaleureux, art de recevoir |
| Lifestyle premium | Élégant et sobre |
| Prescripteurs | Direct et confraternel, toujours au vouvoiement |

## Discrétion sur l'IA

Toutes les maisons ne veulent pas entendre parler d'IA. Le champ « Discrétion IA » fixe le niveau, compte par compte :

| Valeur | Effet |
|---|---|
| Absente (par défaut) | Aucune mention de l'IA ; un contrôle le vérifie |
| Évoquée | « De nouveaux outils de création », sans le mot IA |
| Présentée | L'IA comme laboratoire d'exploration |

## Les 9 contrôles automatiques

| Contrôle | Règle |
|---|---|
| Formule d'appel | Le message commence par « Chère Madame » ou « Cher Monsieur » selon la civilité |
| Vouvoiement | Aucun « tu », « te », « toi », « ton », « ta », « tes » |
| Mots interdits | Leads, ROI, solution, booster, scaler, automatisation, gain de temps, synergie, formules génériques, flatterie, superlatifs |
| Ponctuation | Aucun tiret d'incise, aucun point d'exclamation |
| Texte à compléter | Aucun passage entre crochets |
| Longueur | 90 à 140 mots pour un premier message, 40 à 90 pour une relance |
| Mention de l'IA | Conforme au niveau de discrétion |
| Phrases reprises | Aucune phrase commune avec un message déjà envoyé à la maison |
| Similarité | Moins de 30 % de mots en commun (indice de Jaccard) avec chaque message de la maison |

Le rapport de contrôle est écrit en note sur l'affaire, que le brouillon soit déposé ou non.

## Relances

Les relances sont préparées à J+5, J+12 et J+25 (jours ouvrés) et passent par les mêmes contrôles. Chacune change d'angle :

| Relance | Contenu |
|---|---|
| 1 | Nouvel angle ou nouvelle preuve ; jamais « je me permets de vous relancer » seul |
| 2 | Un point de vue du studio lié à l'enjeu |
| 3 | Message de clôture court, qui laisse la porte ouverte |

## Classement des réponses

Gemini classe chaque réponse ; une désinscription et un retour d'erreur sont reconnus par le code, sans dépendre du modèle.

| Catégorie | Effet sur l'affaire | Autres actions |
|---|---|---|
| Positive | Conversation ouverte | Tâche « Préparer le rendez-vous et répondre sous 24 h », brouillon de réponse avec le lien de prise de rendez-vous, alerte aux fondatrices avec une note de préparation |
| Pas le moment | En pause | Motif enregistré, réactivation dans 6 mois |
| Pas de besoin | Perdue | Motif enregistré, réactivation dans 12 mois |
| Déjà un partenaire | Perdue | Motif enregistré, réactivation dans 12 mois |
| Désinscription | Perdue | Opposition datée sur la personne, tout envoi futur bloqué, alerte |
| Email invalide | Retour à « À rechercher » | Email marqué « Erronée » ; aucun envoi à une autre personne |
| Absence | Inchangée | Séquence suspendue jusqu'au lendemain ouvré du retour, ou 10 jours ouvrés |
| Doute | Conversation ouverte | Alerte : une personne lit la réponse |

La note de préparation du rendez-vous reprend :
- le contexte de la maison ;
- le signal, avec sa date et son URL ;
- le décideur ;
- l'historique des échanges ;
- trois questions à poser ;
- les références à montrer ;
- deux sujets sensibles à anticiper : les droits sur les images générées, la part du geste humain.
