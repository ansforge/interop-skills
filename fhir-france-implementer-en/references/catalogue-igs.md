# French FHIR IG catalogue

> Non-exhaustive catalogue, built by searching GitHub (`ansforge`, `Interop-Sante`) and the official catalogue. **The site <https://interop.esante.gouv.fr/ig/fhir/> is authoritative** — check there first before citing a status or version as certain. For an up-to-date, machine-readable list of published FHIR packages (name, version, canonical URL), see the feed <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml> — handy to quickly check whether an IG or version has been added since the last review.

## Contents

- [EHDS priority documents (France)](#ehds-priority-documents-france)
- [FR Core](#fr-core)
- [Reference guides (ANS)](#reference-guides-ans)
- [Project guides (ANS)](#project-guides-ans)
- [Other / cross-cutting](#other--cross-cutting)
- [Interop'Santé repos](#interopsanté-repos)

## EHDS priority documents (France)

The EHDS (European Health Data Space) mandates the production of 6 categories of health documents in FHIR. Source: <https://esante.gouv.fr/espace-europeen-donnees-sante>. Mapping with known French IGs:

| EHDS document | Corresponding French IG / repo | Status | Note |
|---|---|---|---|
| Patient Summary (European equivalent of the Volet de Synthèse Médicale) | `interop-ig-fhir-document-patient-summary` | WIP | See VSM note below |
| Electronic prescription | `interop-ig-fhir-ePrescription` | Draft | — |
| Electronic dispensation | `interop-ig-fhir-edispensation` | — | — |
| Laboratory report | `interop-ig-document-cr-bio` | — | To confirm: natively FHIR or still CDA |
| Hospital discharge letter | — | Not yet created as of last update | — |
| Medical imaging report and medical images | — | Not yet created as of last update | — |

## FR Core

| Item | Detail |
|---|---|
| Repo | `Interop-Sante/hl7.fhir.fr.core` |
| Published IG | <https://hl7.fr/ig/fhir/core> (CI build: <https://build.fhir.org/ig/Interop-Sante/hl7.fhir.fr.core/>) |
| Maintainer | Interop'Santé (HL7 France), developed jointly with the ANS |
| Latest formal version | 2.2.0, final-text status, active since 2026-03-25 (confirmed on hl7.fr/ig/fhir/core) |
| History | 2.1.0 (2024-09-06), see the IG's "Directory of published versions" for full history |
| FHIR base | R4 |
| Content | Base profiles (Patient, Practitioner, Organization, Encounter, Observation...), use of INS/RPPS/ADELI/FINESS identifiers, French terminologies (CIM-10, CCAM, NABM) bound as value sets |
| Role | Recommended generic foundation for any French FHIR implementation |

## Reference guides (ANS)

Cross-cutting volets, reusable across several business domains. GitHub org: `ansforge`.

| IG | Repo | Known status/version | Description |
|---|---|---|---|
| Mobility Health Document Sharing (PDSm) | `IG-fhir-partage-de-documents-de-sante` | — | Document sharing based on the IHE MHD profile; feeds Mon espace santé / DMP |
| Health measurements | `interop-IG-fhir-mesures-de-sante` | v3.2.0 | Heart rate, blood pressure, steps, pain, BMI, weight, height, temperature, glycemia... |
| Shared Agenda Management (GAP) | `interop-IG-fhir-gestion-agendas-partages` | — | Agenda sharing between healthcare professionals |
| Circle of Care Management | `interop-IG-fhir-cercle-de-soins` | v2.0.0 | Management of a patient's circle of care |
| Liaison Booklet | `IG-fhir-cahier-de-liaison` | v3.0.0 | Care coordination booklet |
| Event Traceability (TDE) | `interop-ig-fhir-tracabilite-evenements` / `IG-FHIR-tracabilite-evenements` | — | Generic specification for exchanging event traces |
| Event Notification (NDE) | `interop-ig-fhir-notification-evenements` | — | Event notifications |
| ePrescription | `interop-ig-fhir-ePrescription` | Draft | Fork of `hl7.fhir.fr.medication`; electronic prescription (FR Medication Request, dispensation) |
| eDispensation | `interop-ig-fhir-edispensation` | — | Electronic dispensation, companion to ePrescription |
| Medication Reference | `interop-ig-fhir-referentiel-medicament` | — | Reference medication data |

## Project guides (ANS)

Specific to a given business scope.

| IG | Repo | Known status/version | Description |
|---|---|---|---|
| Health Directory (Annuaire Santé) | `IG-fhir-annuaire` | — | Public health directory data (RPPS/FINESS) via FHIR |
| Health Directory (new API) | `annuaire-sante-fhir-documentation` | — | Documentation for the newer Annuaire Santé FHIR API ("IRIS DP") |
| Health Offer and Resource Directory (ROR) | `IG-fhir-repertoire-offre-ressources-sante` (+ `-me24` variant) | — | National directory of health/medico-social offers and resources |
| ECLAIRE (clinical trials) | `IG-fhir-essais-cliniques` | v0.3.0, TU (technical update) | REST API for interconnected, accessible clinical trials |
| Healthcare Access Service (SAS) | `IG-fhir-service-acces-aux-soins` | — | Directing patients towards available care offers |
| MSSanté (Secure Health Messaging API) | `interop-ig-fhir-api-messagerie-securisee-sante` | Draft | FHIR API for secure health messaging |

## Other / cross-cutting

| IG | Repo | Description |
|---|---|---|
| EDS Common Core | `IG-FHIR-EDS-SOCLE-COMMUN` | Common foundation for Health Data Warehouses (EDS) — v0.1.0 |
| Remote monitoring (Télésurveillance) | `IG-fhir-telesurveillance` | Remote follow-up (questionnaires/observations) |
| Medico-social — DUI data transfer | `IG-fhir-medicosocial-transfert-donnees-dui` | Data transfer between medico-social systems (Dossier Usager Informatisé) |
| Medico-social — orientation decision follow-up (SDO) | `IG-fhir-medicosocial-suivi-decisions-orientation` | Follow-up of MDPH decisions towards DUI systems |
| Implantable Medical Device traceability | `interop-ig-fhir-tracabilite-dmi` | Traceability of Implantable Medical Devices |
| Health surveillance (Veille sanitaire) | `IG-fhir-veille-sanitaire` | Health surveillance |
| OSIRIS (oncology) | <https://ig-osiris.cancer.fr/ig/osiris/> | Standardization of oncology data (demographics, tumor pathology events, treatments, sequencing, radiotherapy/radiomics) for precision oncology medicine. Maintained by the INCa (Institut National du Cancer), developed with Institut Curie, Institut Bergonié, Centre Léon Bérard and Arkhn. Version 1.1.0, trial-implementation, FHIR R4 base |
| Document Core (family) | `interop-IG-metier-document-core`, `interop-IG-fhir-document-core`, `interop-IG-cda-document-core` | Generic document modeling (business/FHIR/CDA), foundation for clinical reports |
| Laboratory report | `interop-ig-document-cr-bio` | Laboratory report — EHDS document, see "EHDS priority documents" table above |
| Patient Summary / VSM (FHIR) | `interop-ig-fhir-document-patient-summary` | WIP status. This is the FHIR trajectory of the **Volet de Synthèse Médicale** (VSM, still in CDA R2 today), driven by the EHDS obligation to produce this document in FHIR. ⚠️ **Do not confuse** with `interop-ig-document-patient-summary` (old repo name, replaced — no longer cite as the current repo) |

## Interop'Santé repos

GitHub org: `Interop-Sante`.

| Repo | Status | Description |
|---|---|---|
| `hl7.fhir.fr.core` | Published (see above) | FR Core |
| `hl7.fhir.fr.structure` | — | Exchange of internal structural data for healthcare institutions |
| `hl7.fhir.fr.medication` | WIP | Base of the ANS ePrescription fork |
| `hl7.fhir.fr.preadmission` | — | Online pre-admission |
| `hl7.fhir.fr.analyse-pharma` | WIP | Pharmaceutical analysis |

## Verification TODO

- [ ] Check whether a French FHIR IG has since been created for the "hospital discharge letter" or "medical imaging report and medical images" (2 of the 6 EHDS documents, not yet created as of last update — see table above). Verify precisely for the targeted use case (e.g. the EHDS use case) — a similarly named French IG may already exist without covering this specific scope (cross-border European exchange), and vice versa.
- [ ] Confirm whether `interop-ig-document-cr-bio` is natively FHIR or still carried in CDA.
- [ ] Recheck all statuses/versions listed above against <https://interop.esante.gouv.fr/ig/fhir/>.
