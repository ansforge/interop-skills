# Gouvernance du CI-SIS

## Doctrine

- **Source** : <https://interop.esante.gouv.fr/ig/doctrine/> (repo `ansforge/IG-doctrine-ci-sis`), v0.1.0, trial-implementation, generated 2025-06-30, basé sur FHIR 4.0.1.
- **Fondements** : loi "pour une République Numérique" (2016), principes FAIR (Findable, Accessible, Interoperable, Reusable), 5-star Open Data, bonnes pratiques de génie logiciel (UML, conception modulaire).
- **Standard privilégié** : FHIR (IGs stables ou profils IHE adaptés) comme base de référence pour les artefacts de connaissance médicale, avec R4 comme version d'information retenue (voir `versions-fhir.md`).

## Comitologie — 3 niveaux

### COPIL (Comité de Pilotage)

- **Rôle** : décisionnel, fixe la stratégie et les priorités.
- **Fréquence** : 3 réunions par an.
- **Composition** : ANAP, ANS, ANSM, ATIH, CNAMTS, CNSA, DGOS, DGS, DSS, DNS, HAS, HDH, INCa.

### Comité de Concertation

- **Rôle** : consultatif, recommande des priorités par valeur ajoutée.
- **Fréquence** : 1 réunion par an (juin/juillet).
- **Composition** : fédérations industrie (ASINHPA, FEIMA, Interop'Santé, LESSIS, SNITEM, SYNTEC) + représentants des utilisateurs (réseaux de santé, ordres professionnels, sociétés savantes).

### Comité d'Instruction

- **Rôle** : opérationnel — préparation des dossiers, analyse des besoins, exécution des process, support au COPIL.
- **Composition** : experts interopérabilité ANS + DNS.

### Processus

Expression de besoin → filtrage par le Comité d'Instruction contre des critères stratégiques → décision de priorisation par le COPIL → publication des IGs.

**Si aucun IG ne couvre un cas d'usage donné**, c'est ce processus qu'il faut déclencher : rédiger une expression de besoin auprès de l'ANS plutôt que de concevoir une solution ad hoc hors gouvernance. C'est le point d'entrée officiel pour faire émerger une nouvelle spec FHIR française.

## Page "bonnes pratiques"

- **Source** : <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html> (v0.1.11, final-text, generated 2026-06-18 ; repo `ansforge/interop-IG-documentation`).
- **Contenu** :
  1. Critères de qualité/maturité des IGs.
  2. Comment rédiger les ressources de conformance (profils, extensions, ressources de terminologie).
  3. Conventions de nommage pour tous les types d'artefacts FHIR.
  4. Processus de release d'IG FHIR, mappé aux statuts CI-SIS (voir tableau ci-dessous), avec référence à la doc HL7 Confluence (`confluence.hl7.org/pages/viewpage.action?pageId=35718826`).
  5. Conventions de gestion des alias FSH/SUSHI.
  6. Règles de workflow GitHub pour les repos d'IG.
  7. Recommandation R4 par défaut (voir `versions-fhir.md`).
  8. Pointeur vers les conventions de nommage des terminologies (voir `terminologies.md`).

## Tableau de correspondance statut CI-SIS ↔ configuration d'IG

| Statut CI-SIS | `sushi-config.yaml` > `status` | `sushi-config.yaml` > `releaseLabel` | `publication-request.json` > `status` | `publication-request.json` > `mode` |
|---|---|---|---|---|
| draft | `draft` | `ci-build` | `ci-build` | N/A |
| public-comment | `draft` | `ballot` | `ballot` | `working` |
| for implementation | `active` | `trial-use` | `trial-use` | `milestone` |
| final-text | `active` | `final-text` | `final-text` | `milestone` |
| withdrawn/deprecated | `retired` | N/A | `withdrawn` ou `retired` | `withdrawal` |

**Source faisant autorité** : <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html#release-dun-ig-fhir>. Ce tableau est une copie de confort pour que ce skill reste autonome ; en cas de doute ou de divergence apparente (y compris avec une copie du même tableau dans une config locale type CLAUDE.md), c'est la page ANS ci-dessus qui fait foi, pas cette copie.

Ce tableau est repris ici pour que le skill reste autonome pour tout utilisateur du dépôt partagé `interop-skills` (il recoupe celui déjà utilisé en interne pour les process de release — voir les skills `release`/`release-ig` si disponibles dans ton environnement).

## Sources

- Doctrine : <https://interop.esante.gouv.fr/ig/doctrine/doctrine.html>
- Comitologie : <https://interop.esante.gouv.fr/ig/doctrine/comitologie.html>
- Trajectoire interopérabilité : <https://interop.esante.gouv.fr/ig/doctrine/0.1.0-ballot/trajectoire-iop.html>
- Bonnes pratiques : <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html>
- Documentation publication-request (HL7) : <https://confluence.hl7.org/spaces/FHIR/pages/144970227/IG+Publication+Request+Documentation>
