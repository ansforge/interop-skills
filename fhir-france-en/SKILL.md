---
name: fhir-france-en
description: "Guides developers who implement or produce FHIR resources in France (API, FHIR server, storage, batch...) — which FHIR version to use (R4 vs R5 vs R6), catalogue of published Implementation Guides to implement (FR Core, ANS/ansforge guides, Interop-Santé work), French terminologies (SMT, NOS, TRE_/JDV_/ASS_ conventions) and CI-SIS governance (doctrine, committee structure, how to request a missing spec). Does not cover writing/publishing an IG (FSH/SUSHI, release) — see the `ig-builder` skill for IG authors/editors. Use this skill proactively whenever a developer asks a question about FHIR in France to produce conformant resources — which version to choose, which IGs exist, where to find terminologies, how CI-SIS is governed. Content ages fast: check the date block at the top of SKILL.md, and re-verify sources if the date is old."
---

# FHIR in France for developers producing FHIR resources

> **Content last updated: 2026-10-01**
> This landscape moves fast (new IGs, status changes, terminology versions). Systematically check whether newer versions of the points below exist before answering with certainty.

**Synchronized French twin**: `fhir-france/SKILL.md` is the reference version. Any content update here must be mirrored there (and vice versa).

## Purpose of this skill

This skill is aimed at **developers who implement or produce FHIR resources** in a French system (API, FHIR server, data warehouse/storage, data-generation batch...) — not at Implementation Guide authors. It helps find **the right spec at the right time**: when faced with a FHIR France question, quickly point to the right IG, terminology, or doctrine rather than leaving the user to search alone or reinvent a solution that already has a specification. The more these specs are actually used, the better the French interoperability ecosystem works — this skill exists to increase their adoption, not just to archive information.

**Out of scope**: writing an IG (FSH/SUSHI), its release process (`sushi-config.yaml`, `publication-request.json`) and the GitHub workflow of IG repos are not covered here — see the [`ig-builder`](../ig-builder/SKILL.md) skill, dedicated to IG authors/editors (currently French-only).

**If no existing IG covers the use case being sought**: do not invent an ad hoc solution. Advise writing a **statement of need** (*expression de besoin*) to the ANS, the entry point of the CI-SIS governance process (Comité d'Instruction → prioritization by the COPIL → publication of a new IG — see `references/gouvernance-cisis.md`). This is the official path to bring a new spec into existence rather than working around the absence of a standard.

**If an IG exists but seems immature (Draft, trial-use)**: use it anyway rather than building a proprietary solution. For interoperability, a young IG remains preferable to the absence of a common standard — maturity affects the caution to apply (resources may still change), not the decision to use it or not.

## What moves fast (check these first)

1. **IG statuses and versions** — <https://interop.esante.gouv.fr/ig/fhir/> (official catalogue), the machine-readable feed <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml>, and the latest tag of `Interop-Sante/hl7.fhir.fr.core`.
2. **R4 vs R5/R6 decision** — confirmed and sourced (see section 1 below and `references/versions-fhir.md`). The signal to watch is the EHDS's position, not a standalone ANS R6 consultation.
3. **NOS terminology version** — <https://interop.esante.gouv.fr/terminologies>

## Refresh checklist

To run during a periodic review of this skill — not on every user question, which would defeat the purpose of the skill (answering quickly without systematic web research):

- [ ] Compare <https://interop.esante.gouv.fr/ig/fhir/> (or the machine-readable feed <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml>) against `references/catalogue-igs.md`
- [ ] Check the latest tag of `Interop-Sante/hl7.fhir.fr.core`
- [ ] Check whether the EHDS has changed its position on the FHIR version to use (currently R4) — this is the signal that matters, not standalone monitoring of an ANS R6 consultation
- [ ] Check the NOS version number
- [ ] Check whether a French FHIR IG has since been created for the "hospital discharge letter" or "medical imaging report" (2 of the 6 EHDS documents, not yet created as of the last update) — verify precisely for the targeted use case (e.g. the EHDS use case), as a similarly named IG may already exist without covering this particular scope
- [ ] Revisit the "Known areas of uncertainty" section below and try to resolve each point
- [ ] Update the date at the top of this file once the check is done, even if nothing changed — this tells a future reader the content remains reliable

## 1. Which FHIR version to use in France

**R4 (4.0.1) is the default version to use.** This choice was settled by the ANS following a dedicated public consultation ("FHIR R5 ou R4", 25/10/2023 → 25/01/2024): R5 is not backward-compatible and migrating would be costly for limited benefit, especially since the international HL7 **cross-version R5↔R4** IG (<https://hl7.org/fhir/uv/xver-r5.r4>) already makes it possible to carry new R5 attributes/resources into R4 via standardized extensions.

**The signal to watch for a future evolution is not a standalone ANS R6 consultation, but the EHDS's position** (European Health Data Space, which mandates R4 for its implementing acts) — see the refresh checklist above.

Full rationale, sources and exact citations: `references/versions-fhir.md`.

## 2. Overview of French FHIR IGs

Two main organizations publish FHIR IGs for France:

- **Interop'Santé** (HL7 France association, `github.com/Interop-Sante`) maintains in particular **FR Core** (`hl7.fhir.fr.core`), the base profile foundation (Patient, Practitioner, Organization, Encounter, Observation...), French identifiers (INS, RPPS, ADELI, FINESS) and reference terminologies (CIM-10, CCAM, NABM, SNOMED, ...). Current published version: 2.2.0, final-text, active since 2026-03-25.
- **ANS** (`github.com/ansforge`) publishes and maintains a catalogue organized into **reference guides** (cross-cutting IGs reusable across several business domains — e.g. mobility document sharing/PDSm, health measurements, circle of care, liaison booklet) and **project guides** (specific to one business scope — e.g. Health Directory, ROR, ECLAIRE, SAS, MSSanté).

Several IGs are currently in Draft/WIP status due to the **EHDS** (European Health Data Space) timeline, which mandates the production of 6 categories of health documents in FHIR: Patient Summary (VSM), electronic prescription, electronic dispensation, lab report, hospital discharge letter, medical imaging report and medical images. Detailed information on French IGs: `references/catalogue-igs.md`.

Catalogue (non-exhaustive — statuses, versions, maintainers, URLs): `references/catalogue-igs.md`. If the IG you're looking for isn't listed there, check the official catalogue <https://interop.esante.gouv.fr/ig/fhir/> or the feed <https://interop.esante.gouv.fr/ig/fhir/package-feed.xml> before concluding that no IG exists for that use case.

## 3. French terminologies

- **SMT (Serveur Multi-Terminologies / Multi-Terminology Server)** — <https://smt.esante.gouv.fr/fhir> — national terminology server, in FHIR R4, referenced as authoritative in the official HL7 FHIR Foundation registry (code `ans-fr-tx`) for ANS terminologies (mos.esante.gouv.fr), the SMT itself, and the French extension of SNOMED CT.
- **IG Terminologies** — <https://interop.esante.gouv.fr/terminologies> — publishes frozen versions of the **NOS** (Nomenclatures des Objets de Santé / Health Object Nomenclatures), in PDF/CSV/XML/SVS/FHIR formats.
- **Naming convention**: `TRE_` (Reference Terminology), `JDV_` (Value Set, extracted from one or more TRE), `ASS_` (ASSociation table / ConceptMap between ≥2 TRE/JDV). General format: `<TYPE>_<code>_<label>`.

Details, real examples and full conventions: `references/terminologies.md`.

## 4. CI-SIS governance

The **Cadre d'Interopérabilité des Systèmes d'Information de Santé (CI-SIS / French Health Information Systems Interoperability Framework)** is governed by a 3-level committee structure:
- **COPIL** (Comité de Pilotage / Steering Committee) — decision-making, 3x/year.
- **Comité de Concertation** (Consultation Committee) — advisory (industry federations + user representatives), 1x/year.
- **Comité d'Instruction** (Review Committee) — operational (ANS + DNS), prepares files for the COPIL.

CI-SIS doctrine is grounded in the French "République Numérique" law (2016), the FAIR principles and 5-star Open Data, and favors FHIR (stable IGs or adapted IHE profiles) as the reference standard.

Full committee composition and prioritization process: `references/gouvernance-cisis.md`. Understanding this governance helps situate why a spec has a given status and where to send a statement of need if nothing exists for your use case — this file also mentions, for reference, a CI-SIS status ↔ IG configuration mapping table that concerns publishing an IG, not producing conformant resources.

## 5. Validating a resource's conformance to a profile

Before considering a FHIR resource (example, test instance, data produced by an implementation) conformant to a profile from a French IG, validate it with a **FHIR validator** rather than relying on visual review — a resource that "looks right" can violate a cardinality, a binding, or an invariant of the profile without this being visible to the eye:

- **`matchbox` MCP** (if available in the environment) — `mcp__matchbox__validate-fhir-resource`, after first identifying the target profile(s) via `list-fhir-profiles-to-validate-for` or `get-profiles-for-document-bundle`. Fast, no installation required.
- **`validator_cli.jar`** (HL7, official) — to reproduce what the IG Publisher does in CI, or when `matchbox` isn't available:
  `java -jar validator_cli.jar <resource.json> -ig <package>#<version> -profile <profile-url>`
  Docs: <https://confluence.hl7.org/display/FHIR/Using+the+FHIR+Validator>

## 6. Known areas of uncertainty (to verify, not established facts)

This list is for whoever updates this skill (periodic review), not for every single use: to answer a FHIR question, you can rely on this skill's content as-is, but flag these specific points as unconfirmed if the question touches them directly.

No major factual uncertainty is known as of the last update (previously open points — the R4/R5 decision, the VSM trajectory, the oncology IG, the EHDS documents — have been resolved and sourced). There remain **routine** verification TODOs (not factual doubts) in each reference file — e.g. native-FHIR-vs-CDA status of `interop-ig-document-cr-bio` (`catalogue-igs.md`), the exact NOS version number (`terminologies.md`): to recheck during the periodic review, see the checklist at the top of this file. If you identify a genuine factual uncertainty while answering a question, add it here rather than leaving it undocumented.

## 7. How to update this skill

Follow the refresh checklist at the top of this file. Even if nothing has changed, update the date at the top: this tells a future reader (human or agent) that the content was recently verified and remains reliable as-is.

Remember to mirror any content change in the synchronized French twin, `fhir-france/SKILL.md` (and conversely, bring over any change made there).

## 8. Feedback on specs

If a spec referenced here has a problem (ambiguity, implementation question, improvement suggestion), feedback is very welcome via the **GitHub issues of the relevant repo** (e.g. `github.com/ansforge/<repo>/issues` or `github.com/Interop-Sante/<repo>/issues`) — encourage the user to use them rather than silently working around the spec: that's what moves the ecosystem forward.
