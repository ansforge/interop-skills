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

## For comparison: international terminologies

- International HL7 terminology registry: <https://terminology.hl7.org/en>
- International FHIR terminology server (tx.fhir.org): <https://tx.fhir.org/>
- SNOMED CT (international root, from which the French extension derives): managed by SNOMED International

## Verification TODO

- [ ] Recheck the current NOS version number at <https://interop.esante.gouv.fr/terminologies>
- [ ] Confirm whether `IG-NOS`/`ans.fhir.fr.nos` has moved past the observed version 1.5.0
