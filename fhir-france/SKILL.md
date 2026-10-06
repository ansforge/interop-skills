---
name: fhir-france
description: "Oriente les développeurs qui implémentent ou produisent des ressources FHIR en France (API, serveur FHIR, stockage, batch...) — quelle version FHIR utiliser (R4 vs R5 vs R6), catalogue des IGs publiés à implémenter (FR Core, guides ANS/ansforge, travaux Interop-Santé), terminologies françaises (SMT, NOS, conventions TRE_/JDV_/ASS_) et gouvernance CI-SIS (doctrine, comitologie, comment faire émerger une spec manquante). Ne couvre pas la rédaction/publication d'un IG (FSH/SUSHI, release) — réservé à un futur skill pour auteurs d'IG. Utilise ce skill proactivement dès qu'un développeur pose une question sur FHIR en France pour produire des ressources conformes — quelle version choisir, quels IGs existent, où trouver les terminologies, comment est gouverné le CI-SIS. Le contenu date vite : vérifie le bloc de date en tête du SKILL.md, et revérifie les sources si la date est ancienne."
---

# FHIR en France pour les développeurs qui produisent des ressources FHIR

> **Dernière mise à jour du contenu : 2026-10-01**
> Ce paysage évolue vite (nouveaux IGs, changements de statut, versions de terminologies). Si cette date a plus de quelques mois, revérifie au moins les points ci-dessous avant de répondre avec certitude.

## Objectif de ce skill

Ce skill s'adresse aux **développeurs qui implémentent ou produisent des ressources FHIR** dans un système français (API, serveur FHIR, entrepôt/stockage, batch de génération de données...) — pas aux auteurs d'Implementation Guides. Il aide à trouver **la bonne spec au bon moment** : face à une question FHIR France, orienter rapidement vers le bon IG, la bonne terminologie ou la bonne doctrine plutôt que de laisser l'utilisateur chercher seul ou réinventer une solution déjà spécifiée. Plus ces specs sont effectivement utilisées, mieux l'écosystème français d'interopérabilité fonctionne — ce skill existe pour accroître leur adoption, pas seulement pour archiver de l'information.

**Hors périmètre** : la rédaction d'un IG (FSH/SUSHI), son process de release (`sushi-config.yaml`, `publication-request.json`) et le workflow GitHub des repos d'IG ne sont pas couverts ici — ce sont des sujets pour un futur skill dédié aux auteurs/éditeurs d'IG.

**Si aucun IG existant ne couvre le cas d'usage recherché** : ne pas inventer une solution ad hoc. Conseiller d'écrire une **expression de besoin** auprès de l'ANS, point d'entrée du processus de gouvernance CI-SIS (Comité d'Instruction → priorisation par le COPIL → publication d'un nouvel IG — voir `references/gouvernance-cisis.md`). C'est la voie officielle pour faire émerger une nouvelle spec plutôt que de contourner l'absence de standard.

**Si un IG existe mais semble peu mûr (Draft, trial-use)** : l'utiliser quand même plutôt que de construire une solution propriétaire. Pour l'interopérabilité, un IG encore jeune reste préférable à l'absence de standard commun — la maturité influence la prudence à adopter (ressources susceptibles d'évoluer), pas la décision de l'utiliser ou non.

## Ce qui bouge vite (à revérifier en priorité)

1. **Statuts et versions des IGs** — <https://interop.esante.gouv.fr/ig/fhir/> (catalogue officiel), le flux machine-lisible <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml>, et le dernier tag de `Interop-Sante/hl7.fhir.fr.core`.
2. **Décision R4 vs R5/R6** — confirmée et sourcée (voir section 1 ci-dessous et `references/versions-fhir.md`). Le signal à surveiller est la position de l'EHDS, pas une concertation R6 ANS isolée.
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

**R4 (4.0.1) est la version à utiliser par défaut.** Choix tranché par l'ANS à l'issue d'une concertation publique dédiée ("FHIR R5 ou R4", 25/10/2023 → 25/01/2024) : R5 n'est pas rétrocompatible et migrer coûterait cher pour un bénéfice limité, d'autant que l'IG HL7 international **cross-version R5↔R4** (<https://hl7.org/fhir/uv/xver-r5.r4>) permet déjà de porter de nouveaux attributs/ressources R5 en R4 via des extensions standardisées.

**Le signal à suivre pour une évolution future n'est pas une concertation R6 propre à l'ANS, mais la position de l'EHDS** (European Health Data Space, qui impose R4 pour ses actes d'exécution) — voir la checklist de rafraîchissement ci-dessus.

Argumentaire complet, sources et citations exactes : `references/versions-fhir.md`.

## 2. Panorama des IGs FHIR français

Deux organisations principales publient des IGs FHIR pour la France :

- **Interop'Santé** (association HL7 France, `github.com/Interop-Sante`) maintient notamment **FR Core** (`hl7.fhir.fr.core`), le socle de profils de base (Patient, Practitioner, Organization, Encounter, Observation...), les identifiants français (INS, RPPS, ADELI, FINESS) et les terminologies de référence (CIM-10, CCAM, NABM, SNOMED, ...). Version publiée actuelle : 2.2.0, final-text, active depuis 2026-03-25.
- **ANS** (`github.com/ansforge`) publie et maintient un catalogue organisé en **guides référentiels** (volets transversaux, réutilisables par plusieurs métiers — ex. Partage de Documents de Santé en mobilité/PDSm, Mesures de santé, Cercle de Soins, Cahier de Liaison) et **guides projet** (spécifiques à un périmètre métier — ex. Annuaire Santé, ROR, ECLAIRE, SAS, MSSanté).

Plusieurs IGs sont actuellement en statut Draft/WIP du fait du calendrier **EHDS** (European Health Data Space), qui impose la production de 6 catégories de documents de santé en FHIR : Patient Summary (VSM), prescription électronique, dispensation électronique, compte-rendu de biologie, lettre de sortie d'hospitalisation, compte-rendu d'imagerie médicale et images médicales. Informations détaillées des IG français : `references/catalogue-igs.md`.

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

Composition complète des comités et processus de priorisation : `references/gouvernance-cisis.md`. Comprendre cette gouvernance aide à situer pourquoi une spec a tel statut et où adresser une expression de besoin si rien n'existe pour ton cas d'usage — ce fichier mentionne aussi, pour mémoire, un tableau de correspondance statut CI-SIS ↔ configuration d'IG qui concerne la publication d'un IG, pas la production de ressources conformes.

## 5. Valider la conformité d'une ressource à un profil

Avant de considérer une ressource FHIR (exemple, instance de test, donnée produite par une implémentation) comme conforme à un profil d'un IG français, valide-la avec un **FHIR validator** plutôt que de te fier à une relecture visuelle — une ressource qui « a l'air bonne » peut violer une cardinalité, un binding ou un invariant du profil sans que ce soit visible à l'œil :

- **MCP `matchbox`** (si disponible dans l'environnement) — `mcp__matchbox__validate-fhir-resource`, en identifiant au préalable le(s) profil(s) visé(s) via `list-fhir-profiles-to-validate-for` ou `get-profiles-for-document-bundle`. Rapide, aucune installation requise.
- **`validator_cli.jar`** (HL7, officiel) — pour reproduire ce que fait l'IG Publisher en CI, ou quand `matchbox` n'est pas disponible :
  `java -jar validator_cli.jar <resource.json> -ig <package>#<version> -profile <url-du-profil>`
  Doc : <https://confluence.hl7.org/display/FHIR/Using+the+FHIR+Validator>

## 6. Zones d'incertitude connues (à vérifier, pas des faits établis)

Cette liste s'adresse à qui met à jour ce skill (revue périodique), pas à chaque utilisation ponctuelle : pour répondre à une question FHIR, tu peux t'appuyer sur le contenu de ce skill tel quel, mais signale ces points précis comme non confirmés si la question les touche directement.

Aucune incertitude factuelle majeure n'est connue à la date de MAJ (les points précédemment ouverts — décision R4/R5, trajectoire du VSM, IG cancérologie, documents EHDS — ont été levés et sourcés). Il reste des TODO de vérification **routinière** (pas des doutes factuels) dans chaque fichier de référence — ex. statut FHIR natif vs CDA de `interop-ig-document-cr-bio` (`catalogue-igs.md`), numéro de version NOS exact (`terminologies.md`) : à recontrôler lors de la revue périodique, voir la checklist en tête de ce fichier. Si tu identifies une vraie incertitude factuelle en répondant à une question, ajoute-la ici plutôt que de la laisser non documentée.

## 7. Comment mettre à jour ce skill

Suis la checklist de rafraîchissement en tête de ce fichier. Même si aucune information n'a changé, mets à jour la date en tête : cela indique à un futur lecteur (humain ou agent) que le contenu a été vérifié récemment et reste fiable tel quel.

## 8. Retours sur les specs

Si une spec citée ici pose problème (ambiguïté, question d'implémentation, suggestion d'amélioration), les retours sont très appréciés via les **issues GitHub du repo concerné** (ex. `github.com/ansforge/<repo>/issues` ou `github.com/Interop-Sante/<repo>/issues`) — encourage l'utilisateur à les utiliser plutôt que de contourner la spec en silence : c'est ce qui fait progresser l'écosystème.
