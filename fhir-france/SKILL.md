---
name: fhir-france
description: Explique l'écosystème FHIR en France pour l'ANS et les porteurs de projets d'interopérabilité en santé : version FHIR à utiliser (R4 vs R5 vs R6), catalogue des IGs FHIR publiés (FR Core, guides référentiels et guides projet ANS/ansforge, travaux Interop-Santé), terminologies françaises (SMT, NOS, conventions TRE_/JDV_/ASS_) et gouvernance CI-SIS (doctrine, comitologie, statuts de publication). Utilise ce skill proactivement dès que l'utilisateur pose une question sur FHIR en France — quelle version choisir, quels IGs existent, où trouver les terminologies, comment est gouverné le CI-SIS — même si la question est formulée de façon générale ou si aucun IG n'est nommé explicitement. Le contenu date vite : vérifie toujours le bloc de date en tête du SKILL.md avant de répondre, et revérifie les sources si la date est ancienne.
---

# FHIR en France

> **Dernière mise à jour du contenu : 2026-10-01**
> Ce paysage évolue vite (nouveaux IGs, changements de statut, versions de terminologies). Si cette date a plus de quelques mois, revérifie au moins les points ci-dessous avant de répondre avec certitude.

## Ce qui bouge vite (à revérifier en priorité)

1. **Statuts et versions des IGs** — <https://interop.esante.gouv.fr/ig/fhir/> (catalogue officiel) et le dernier tag de `Interop-Sante/hl7.fhir.fr.core`.
2. **Décision R4 vs R5/R6** — la concertation ANS "FHIR R5 ou R4" (25/10/2023 → 25/01/2024) a été consultée intégralement ; le choix R4 est confirmé et sourcé (voir `references/versions-fhir.md`). Reste à vérifier si une concertation/doctrine R6 a été publiée depuis (la page d'origine annonçait une concertation R6 "attendue mi-2024").
3. **Version des terminologies NOS** — <https://interop.esante.gouv.fr/terminologies>

## Checklist de rafraîchissement

À exécuter lors d'une revue périodique de ce skill — pas à chaque question posée par un utilisateur, ce qui annulerait l'intérêt du skill (répondre vite sans recherche web systématique) :

- [ ] Comparer <https://interop.esante.gouv.fr/ig/fhir/> à `references/catalogue-igs.md`
- [ ] Vérifier le dernier tag de `Interop-Sante/hl7.fhir.fr.core`
- [ ] Vérifier si une concertation/doctrine FHIR R6 a été publiée depuis (le choix R4 vs R5 est déjà tranché, voir ci-dessous)
- [ ] Vérifier le numéro de version NOS
- [ ] Revisiter la section "Zones d'incertitude" plus bas et tenter de lever chaque point
- [ ] Mettre à jour la date en tête de ce fichier une fois la vérification faite, même si rien n'a changé — cela indique à un futur lecteur que le contenu reste fiable

## 1. Quelle version FHIR utiliser en France

**R4 (4.0.1) est la version à utiliser par défaut.** Ce n'est pas qu'une recommandation de bonnes pratiques : c'est un choix de doctrine explicitement tranché par l'ANS à l'issue d'une concertation publique dédiée ("FHIR R5 ou R4", 25/10/2023 → 25/01/2024), dont le contenu intégral a été vérifié.

Pourquoi R4 et pas R5 :
- Tout l'écosystème français est déjà en R4 : FrCore (Interop'Santé), les volets CI-SIS (agenda, mesures, cercle de soins, cahier de liaison...), les projets nationaux (Mon Espace Santé, Annuaire Santé, ROR, SAS, SMT), et la majorité des pays voisins/projets européens (HL7 Europe, UK, Allemagne, Suisse, IHE).
- R5 n'est **pas rétrocompatible** avec R4 — migrer engendrerait des coûts de migration élevés, un risque de coexistence R4/R5 dans l'écosystème (double maintenance pour les établissements), et des délais très longs (créer/publier un IG prend des mois à des années).
- Même Grahame Grieve (directeur produit FHIR) n'encourage pas particulièrement le passage à R5 ; les USA n'y passent pas non plus, sauf cas marginaux.
- R5 reste intéressant ponctuellement : documentation améliorée, et certaines ressources ayant beaucoup gagné en maturité (ex. produits médicamenteux).

Trajectoire retenue par l'ANS : rester en R4 par défaut (avec, si utile, des extensions R4 imitant des attributs R5 pour préparer la transition) ; évaluer R5 au cas par cas quand la pertinence est claire (ressource très évoluée en R5, besoin d'échange international nécessitant R5, possibilité de s'affranchir de l'héritage R4) ; et anticiper R6 dès sa sortie, avec FrCore comme priorité.

**R6** : au moment de la concertation R5/R4, une concertation R6 était annoncée "attendue mi-2024" — à vérifier si elle a eu lieu et ce qu'elle a conclu (voir checklist ci-dessus).

Détail complet, sources et citations exactes : `references/versions-fhir.md`.

## 2. Panorama des IGs FHIR français

Deux organisations principales publient des IGs FHIR pour la France :

- **Interop'Santé** (association HL7 France, `github.com/Interop-Sante`) maintient notamment **FR Core** (`hl7.fhir.fr.core`), le socle de profils de base (Patient, Practitioner, Organization, Encounter, Observation...), les identifiants français (INS, RPPS, ADELI, FINESS) et les terminologies de référence (CIM-10, CCAM, NABM). Version publiée actuelle : 2.2.0, final-text, active depuis 2026-03-25.
- **ANS** (`github.com/ansforge`) publie et maintient un catalogue organisé en **guides référentiels** (volets transversaux, réutilisables par plusieurs métiers — ex. Partage de Documents de Santé en mobilité/PDSm, Mesures de santé, Cercle de Soins, Cahier de Liaison) et **guides projet** (spécifiques à un périmètre métier — ex. Annuaire Santé, ROR, ECLAIRE, SAS, MSSanté).

Plusieurs IGs sont actuellement en statut Draft/WIP du fait du calendrier **EHDS** (European Health Data Space), qui impose la production de 6 documents de santé en FHIR — dont le VSM/Patient Summary (`interop-ig-fhir-document-patient-summary`, successeur FHIR direct du VSM aujourd'hui en CDA R2).

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

- **Concertation R6** : la décision R4 vs R5 est tranchée et sourcée (voir ci-dessus), mais une éventuelle concertation ou doctrine publiée depuis sur R6 reste à vérifier.
- **IGs biologie / imagerie / cancérologie** : seule la biologie est confirmée nommément (`interop-ig-document-cr-bio`, compte-rendu biologie). Pas de repo identifié avec certitude sous un nom équivalent pour l'imagerie ou la cancérologie — à rechercher directement sur `github.com/ansforge` avant d'affirmer qu'ils n'existent pas.
- **Les 5 autres documents EHDS-FHIR** : l'EHDS (European Health Data Space) impose la production de 6 documents de santé en FHIR, dont le VSM/Patient Summary (confirmé, voir `references/catalogue-igs.md`) — mais les 5 autres documents ne sont pas identifiés avec certitude ici. Ne pas deviner leur nom ; les rechercher avant de répondre si la question porte dessus.

## 6. Comment mettre à jour ce skill

Suis la checklist de rafraîchissement en tête de ce fichier. Même si aucune information n'a changé, mets à jour la date en tête : cela indique à un futur lecteur (humain ou agent) que le contenu a été vérifié récemment et reste fiable tel quel.
