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
- **Contenu pertinent pour un développeur qui produit des ressources FHIR** (ce que cette page couvre et qui aide à produire des ressources conformes) :
  1. Critères de qualité/maturité des IGs — utile pour juger si un IG est assez mûr pour produire des ressources en production.
  2. Conventions de nommage pour tous les types d'artefacts FHIR — utile pour reconnaître/retrouver profils, extensions, value sets dans un IG.
  3. Recommandation R4 par défaut (voir `versions-fhir.md`).
  4. Pointeur vers les conventions de nommage des terminologies (voir `terminologies.md`).
- **Contenu réservé aux auteurs/éditeurs d'IG** (hors périmètre de ce skill, prévu pour un futur skill `ig-builder`) : comment rédiger les ressources de conformance (profils, extensions, ressources de terminologie), le processus de release d'IG FHIR mappé aux statuts CI-SIS, les conventions de gestion des alias FSH/SUSHI, les règles de workflow GitHub des repos d'IG.

## Correspondance statut CI-SIS ↔ configuration d'IG (hors périmètre de ce skill)

L'ANS publie un tableau de correspondance entre les statuts CI-SIS (draft, public-comment, for implementation, final-text, withdrawn/deprecated) et les champs `sushi-config.yaml`/`publication-request.json` d'un projet FSH/SUSHI (`status`, `releaseLabel`, `mode`...). Ce tableau concerne qui **publie** un IG (choix de configuration au moment de la release), pas qui **produit des ressources** conformes à cet IG dans une implémentation — il n'est donc pas reproduit ici.

**Source faisant autorité** : <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html#release-dun-ig-fhir>.

Ce tableau, ainsi que le reste des bonnes pratiques de rédaction/publication d'IG, a vocation à vivre dans un futur skill `ig-builder` destiné aux auteurs/éditeurs d'IG.

## Sources

- Doctrine : <https://interop.esante.gouv.fr/ig/doctrine/doctrine.html>
- Comitologie : <https://interop.esante.gouv.fr/ig/doctrine/comitologie.html>
- Trajectoire interopérabilité : <https://interop.esante.gouv.fr/ig/doctrine/0.1.0-ballot/trajectoire-iop.html>
- Bonnes pratiques : <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html>
- Documentation publication-request (HL7) : <https://confluence.hl7.org/spaces/FHIR/pages/144970227/IG+Publication+Request+Documentation>
