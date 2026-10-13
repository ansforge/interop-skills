# French terminologies for FHIR

## SMT — Serveur Multi-Terminologies (Multi-Terminology Server)

- **URL**: <https://smt.esante.gouv.fr/fhir>
- **Role**: the ANS's official national terminology server, exposing French health terminologies in FHIR.
- **Independent confirmation**: referenced in the official HL7 FHIR Foundation registry (`ansforge/ig-registry`, file `hl7-fr-tx-servers.json`):

  ```json
  code: "ans-fr-tx"
  name: "Agence du Numérique en Santé (ANS) Terminology Server"
  url: "https://smt.esante.gouv.fr/fhir"
  fhirVersions: [{"version": "R4", "url": "https://smt.esante.gouv.fr/fhir"}]
  ```

- **Authoritative for**: terminologies published under `https://mos.esante.gouv.fr/*` and `https://smt.esante.gouv.fr/*`, as well as the French extension of SNOMED CT (`http://snomed.info/sct/11000315107*`).

## IG Terminologies / NOS

- **URL**: <https://interop.esante.gouv.fr/terminologies>
- **Role**: publishes frozen versions of the **NOS (Nomenclatures des Objets de Santé / Health Object Nomenclatures)** — a kind of stable "snapshot" of what exists on the SMT, useful when a versioned reference is needed rather than the server's current state.
- **Available formats**: PDF, CSV, XML, SVS, XML/FHIR, JSON/FHIR.
- **Version observed as of this file's last update (2026-10-01)**: v1.7.0 (to re-verify — this number changes regularly).
- **Associated IG**: `ansforge/IG-terminologie-de-sante` / package `ans.fr.terminologies` (version 1.14.0, `final-text`, active), documents the NOS value sets in native FHIR form. Replaces the former `ansforge/IG-NOS` / `ans.fhir.fr.nos` (archived, last observed version 1.5.0) — no longer cite it as the current IG.

## Terminology artifact naming convention

Documented at <https://interop.esante.gouv.fr/terminologies/convention.html>. Three prefix families:

| Prefix | Meaning | Corresponding FHIR type | Example |
|---|---|---|---|
| `TRE_` | Terminologie de Référence (Reference Terminology) | CodeSystem | `TRE_R75_InseeNAFrev2Niveau5` (INSEE NAF rev2 level 5 codes), `TRE_A03-ClasseDocument` |
| `JDV_` | Jeu De Valeurs (Value Set), extracted from one or more TRE | ValueSet | `JDV_J07_XdsTypeCode_CISIS`, `JDV_J105_EnsembleDiplome_RASS` |
| `ASS_` | Table d'ASSociation (Association table) — mapping between ≥2 TRE/JDV | ConceptMap | `ASS_A23_ASR_ActiviteModaliteForme` |

**General format**: `<TYPE>_<code>_<label>`, e.g. `TRE_A03-ClasseDocument` (note that the separator between code and label can vary — hyphen or underscore depending on the existing artifact — check the most recent example before reproducing the pattern).

## For comparison: international terminologies

- International HL7 terminology registry: <https://terminology.hl7.org/en>
- International FHIR terminology server (tx.fhir.org): <https://tx.fhir.org/>
- SNOMED CT (international root, from which the French extension derives): managed by SNOMED International

## Verification TODO

- [ ] Recheck the current NOS version number at <https://interop.esante.gouv.fr/terminologies>
- [ ] Confirm whether `IG-NOS`/`ans.fhir.fr.nos` has moved past the observed version 1.5.0
