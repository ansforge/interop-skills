---
name: fhir-france
description: Explique l'écosystème FHIR en France pour l'ANS et les porteurs de projets d'interopérabilité en santé : version FHIR à utiliser (R4 vs R5 vs R6), catalogue des IGs FHIR publiés (FR Core, guides référentiels et guides projet ANS/ansforge, travaux Interop-Santé), terminologies françaises (SMT, NOS, conventions TRE_/JDV_/ASS_) et gouvernance CI-SIS (doctrine, comitologie, statuts de publication). Utilise ce skill proactivement dès que l'utilisateur pose une question sur FHIR en France — quelle version choisir, quels IGs existent, où trouver les terminologies, comment est gouverné le CI-SIS — même si la question est formulée de façon générale ou si aucun IG n'est nommé explicitement. Le contenu date vite : vérifie toujours le bloc de date en tête du SKILL.md avant de répondre, et revérifie les sources si la date est ancienne.
---

# FHIR en France

> **Dernière mise à jour du contenu : 2026-10-01**
> Ce paysage évolue vite (nouveaux IGs, changements de statut, versions de terminologies). Si cette date a plus de quelques mois, revérifie au moins les points ci-dessous avant de répondre avec certitude.

## Objectif de ce skill

Aider à trouver **la bonne spec au bon moment** : face à une question FHIR France, orienter rapidement vers le bon IG, la bonne terminologie ou la bonne doctrine plutôt que de laisser l'utilisateur chercher seul ou réinventer une solution déjà spécifiée. Plus ces specs sont effectivement utilisées, mieux l'écosystème français d'interopérabilité fonctionne — ce skill existe pour accroître leur adoption, pas seulement pour archiver de l'information.

**Si aucun IG existant ne couvre le cas d'usage recherché** : ne pas inventer une solution ad hoc. Conseiller d'écrire une **expression de besoin** auprès de l'ANS, point d'entrée du processus de gouvernance CI-SIS (Comité d'Instruction → priorisation par le COPIL → publication d'un nouvel IG — voir `references/gouvernance-cisis.md`). C'est la voie officielle pour faire émerger une nouvelle spec plutôt que de contourner l'absence de standard.

## Ce qui bouge vite (à revérifier en priorité)

1. **Statuts et versions des IGs** — <https://interop.esante.gouv.fr/ig/fhir/> (catalogue officiel), le flux machine-lisible <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml>, et le dernier tag de `Interop-Sante/hl7.fhir.fr.core`.
2. **Décision R4 vs R5/R6** — la concertation ANS "FHIR R5 ou R4" (25/10/2023 → 25/01/2024) a été consultée intégralement ; le choix R4 est confirmé et sourcé (voir `references/versions-fhir.md`). La stratégie de suivi n'est plus de traquer une éventuelle concertation R6 ANS isolément : la France aligne sa position sur celle de l'**EHDS**, qui impose R4 — c'est donc le signal EHDS qu'il faut surveiller, pas un calendrier R6 propre à l'ANS.
3. **Version des terminologies NOS** — <https://interop.esante.gouv.fr/terminologies>

## Checklist de rafraîchissement

À exécuter lors d'une revue périodique de ce skill — pas à chaque question posée par un utilisateur, ce qui annulerait l'intérêt du skill (répondre vite sans recherche web systématique) :

- [ ] Comparer <https://interop.esante.gouv.fr/ig/fhir/> (ou le flux machine-lisible <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml>) à `references/catalogue-igs.md`
- [ ] Vérifier le dernier tag de `Interop-Sante/hl7.fhir.fr.core`
- [ ] Vérifier si l'EHDS a changé sa position sur la version FHIR à utiliser (R4 actuellement) — c'est le signal qui prime, pas une veille isolée sur une concertation R6 de l'ANS
- [ ] Vérifier le numéro de version NOS
- [ ] Vérifier si un IG FHIR français a depuis été créé pour la "lettre de sortie d'hospitalisation" ou le "compte-rendu d'imagerie médicale" (2 des 6 documents EHDS, pas encore créés à la date de MAJ) — en vérifiant précisément pour le cas d'usage visé (ex. le cas d'usage EHDS), un IG au nom similaire pouvant déjà exister sans couvrir ce périmètre
- [ ] Revisiter la section "Zones d'incertitude" plus bas et tenter de lever chaque point
- [ ] Mettre à jour la date en tête de ce fichier une fois la vérification faite, même si rien n'a changé — cela indique à un futur lecteur que le contenu reste fiable

## 1. Quelle version FHIR utiliser en France

**R4 (4.0.1) est la version à utiliser par défaut.** Ce n'est pas qu'une recommandation de bonnes pratiques : c'est un choix de doctrine explicitement tranché par l'ANS à l'issue d'une concertation publique dédiée ("FHIR R5 ou R4", 25/10/2023 → 25/01/2024), dont le contenu intégral a été vérifié.

Pourquoi R4 et pas R5 :
- Tout l'écosystème français est déjà en R4 : FrCore (Interop'Santé), les volets CI-SIS (agenda, mesures, cercle de soins, cahier de liaison...), les projets nationaux (Mon Espace Santé, Annuaire Santé, ROR, SAS, SMT), et la majorité des pays voisins/projets européens (HL7 Europe, UK, Allemagne, Suisse, IHE).
- R5 n'est **pas rétrocompatible** avec R4 — migrer engendrerait des coûts de migration élevés, un risque de coexistence R4/R5 dans l'écosystème (double maintenance pour les établissements), et des délais très longs (créer/publier un IG prend des mois à des années).
- Même Grahame Grieve (directeur produit FHIR) n'encourage pas particulièrement le passage à R5 ; les USA n'y passent pas non plus, sauf cas marginaux.
- R5 reste intéressant ponctuellement : documentation améliorée, et certaines ressources ayant beaucoup gagné en maturité (ex. produits médicamenteux).
- L'IG HL7 international **cross-version R5↔R4** (<https://hl7.org/fhir/uv/xver-r5.r4>) réduit encore l'intérêt de migrer : il permet de porter de nouveaux attributs/ressources R5 en R4 via des extensions standardisées.

Trajectoire retenue par l'ANS : rester en R4 par défaut (avec, si utile, des extensions R4 imitant des attributs R5 — voir l'IG cross-version ci-dessus) ; évaluer R5 au cas par cas quand la pertinence est claire (ressource très évoluée en R5, besoin d'échange international nécessitant R5, possibilité de s'affranchir de l'héritage R4) ; et, surtout, s'aligner sur la position de l'**EHDS** — c'est ce signal européen qui prime sur toute considération ANS isolée.

**R6** : ce n'est plus un sujet de veille autonome pour ce skill. La position à suivre est celle de l'**EHDS** (European Health Data Space), qui impose R4 pour ses actes d'exécution — c'est cet alignement européen qui dicte la trajectoire française, pas une concertation R6 propre à l'ANS.

Détail complet, sources et citations exactes : `references/versions-fhir.md`.

## 2. Panorama des IGs FHIR français

Deux organisations principales publient des IGs FHIR pour la France :

- **Interop'Santé** (association HL7 France, `github.com/Interop-Sante`) maintient notamment **FR Core** (`hl7.fhir.fr.core`), le socle de profils de base (Patient, Practitioner, Organization, Encounter, Observation...), les identifiants français (INS, RPPS, ADELI, FINESS) et les terminologies de référence (CIM-10, CCAM, NABM). Version publiée actuelle : 2.2.0, final-text, active depuis 2026-03-25.
- **ANS** (`github.com/ansforge`) publie et maintient un catalogue organisé en **guides référentiels** (volets transversaux, réutilisables par plusieurs métiers — ex. Partage de Documents de Santé en mobilité/PDSm, Mesures de santé, Cercle de Soins, Cahier de Liaison) et **guides projet** (spécifiques à un périmètre métier — ex. Annuaire Santé, ROR, ECLAIRE, SAS, MSSanté).

Plusieurs IGs sont actuellement en statut Draft/WIP du fait du calendrier **EHDS** (European Health Data Space), qui impose la production de 6 catégories de documents de santé en FHIR : Patient Summary (VSM), prescription électronique, dispensation électronique, compte-rendu de biologie, lettre de sortie d'hospitalisation, compte-rendu d'imagerie médicale et images médicales. Mappage détaillé avec les IGs français : `references/catalogue-igs.md`.

Table complète (IGs, statuts, versions, mainteneurs, URLs) : `references/catalogue-igs.md`.

## 3. Terminologies françaises

- **SMT (Serveur Multi-Terminologies)** — <https://smt.esante.gouv.fr/fhir> — serveur de terminologie national, en FHIR R4, référencé comme autoritatif dans le registre officiel HL7 FHIR Foundation (code `ans-fr-tx`) pour les terminologies ANS (mos.esante.gouv.fr), SMT lui-même, et l'extension française de SNOMED CT.
- **IG Terminologies** — <https://interop.esante.gouv.fr/terminologies> — publie des versions figées des **NOS** (Nomenclatures des Objets de Santé), aux formats PDF/CSV/XML/SVS/FHIR.
- **Convention de nommage** : `TRE_` (Terminologie de Référence), `JDV_` (Jeu De Valeurs, value set extrait d'une ou plusieurs TRE), `ASS_` (table d'ASSociation / ConceptMap entre ≥2 TRE/JDV). Format général : `<TYPE>_<code>_<label>`.

Détails, exemples réels et conventions complètes : `references/terminologies.md`.

## 4. Gouvernance CI-SIS

Le **Cadre d'Interopérabilité des Systèmes d'Information de Santé (CI-SIS)** est gouverné par une comitologie à 3 niveaux :
- **COPIL** (Comité de Pilotage) — décisionnel, 3x/an.
- **Comité de Concertation** — consultatif (fédérations industrie + représentants usagers), 1x/an.
- **Comité d'Instruction** — opérationnel (ANS + DNS), prépare les dossiers pour le COPIL.

La doctrine CI-SIS s'appuie sur la loi République Numérique (2016), les principes FAIR et le 5-star Open Data, et privilégie FHIR (IGs stables ou profils IHE adaptés) comme standard de référence.

Composition complète des comités, tableau de correspondance statut CI-SIS ↔ `sushi-config.yaml`/`publication-request.json` : `references/gouvernance-cisis.md`. Si tu prépares une release d'IG, ce tableau recoupe celui déjà utilisé par les skills `release`/`release-ig`.

## 5. Zones d'incertitude connues (à vérifier, pas des faits établis)

Cette liste s'adresse à qui met à jour ce skill (revue périodique), pas à chaque utilisation ponctuelle : pour répondre à une question FHIR, tu peux t'appuyer sur le contenu de ce skill tel quel, mais signale ces points précis comme non confirmés si la question les touche directement.

Aucune zone d'incertitude connue à la date de MAJ en tête de ce fichier (toutes celles identifiées lors des revues précédentes ont été levées). Si tu en identifies une nouvelle en répondant à une question, ajoute-la ici plutôt que de la laisser non documentée.

## 6. Comment mettre à jour ce skill

Suis la checklist de rafraîchissement en tête de ce fichier. Même si aucune information n'a changé, mets à jour la date en tête : cela indique à un futur lecteur (humain ou agent) que le contenu a été vérifié récemment et reste fiable tel quel.

## 7. Retours sur les specs

Si une spec citée ici pose problème (ambiguïté, question d'implémentation, suggestion d'amélioration), les retours sont très appréciés via les **issues GitHub du repo concerné** (ex. `github.com/ansforge/<repo>/issues` ou `github.com/Interop-Sante/<repo>/issues`) — encourage l'utilisateur à les utiliser plutôt que de contourner la spec en silence : c'est ce qui fait progresser l'écosystème.
