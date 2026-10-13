# CI-SIS governance

## Doctrine

- **Source**: <https://interop.esante.gouv.fr/ig/doctrine/> (repo `ansforge/IG-doctrine-ci-sis`), v0.1.0, trial-implementation, generated 2025-06-30, based on FHIR 4.0.1.
- **Foundations**: the French "République Numérique" law (2016), FAIR principles (Findable, Accessible, Interoperable, Reusable), 5-star Open Data, software engineering best practices (UML, modular design).
- **Preferred standard**: FHIR (stable IGs or adapted IHE profiles) as the reference foundation for medical knowledge artifacts, with R4 as the chosen information version (see `versions-fhir.md`).

## Committee structure — 3 levels

### COPIL (Comité de Pilotage / Steering Committee)

- **Role**: decision-making, sets strategy and priorities.
- **Frequency**: 3 meetings per year.
- **Composition**: ANAP, ANS, ANSM, ATIH, CNAMTS, CNSA, DGOS, DGS, DSS, DNS, HAS, HDH, INCa.

### Comité de Concertation (Consultation Committee)

- **Role**: advisory, recommends priorities by added value.
- **Frequency**: 1 meeting per year (June/July).
- **Composition**: industry federations (ASINHPA, FEIMA, Interop'Santé, LESSIS, SNITEM, SYNTEC) + user representatives (health networks, professional bodies, learned societies).

### Comité d'Instruction (Review Committee)

- **Role**: operational — preparing files, needs analysis, process execution, support to the COPIL.
- **Composition**: ANS interoperability experts + DNS.

### Process

Statement of need (*expression de besoin*) → screening by the Comité d'Instruction against strategic criteria → prioritization decision by the COPIL → publication of IGs.

**If no IG covers a given use case**, this is the process to trigger: write a statement of need to the ANS rather than designing an ad hoc solution outside of governance. This is the official entry point for bringing a new French FHIR spec into existence.

## "Best practices" page

- **Source**: <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html> (v0.1.11, final-text, generated 2026-06-18; repo `ansforge/interop-IG-documentation`).
- **Content relevant to a developer producing FHIR resources** (what this page covers that helps produce conformant resources):
  1. IG quality/maturity criteria — useful for knowing what to expect from a still-Draft/immature IG (resources that may change, fewer implementation reports). **Maturity is not a reason to dismiss an IG**: even an immature IG remains preferable to a proprietary solution for interoperability — see the "no ad hoc solution" principle in `SKILL.md`.
  2. Naming conventions for all FHIR artifact types — useful for recognizing/locating profiles, extensions, value sets within an IG.
  3. R4-by-default recommendation (see `versions-fhir.md`).
  4. Pointer to terminology naming conventions (see `terminologies.md`).
- **Content reserved for IG authors/editors** (out of scope for this skill — see the [`ig-builder`](../../ig-builder/SKILL.md) skill, currently French-only): how to write conformance resources (profiles, extensions, terminology resources), the FHIR IG release process mapped to CI-SIS statuses, FSH/SUSHI alias management conventions, GitHub workflow rules for IG repos.

## CI-SIS status ↔ IG configuration mapping (out of scope for this skill)

The ANS publishes a mapping table between CI-SIS statuses (draft, public-comment, for implementation, final-text, withdrawn/deprecated) and the `sushi-config.yaml`/`publication-request.json` fields of an FSH/SUSHI project (`status`, `releaseLabel`, `mode`...). This table concerns who **publishes** an IG (configuration choices at release time), not who **produces** resources conformant to that IG in an implementation — it is therefore not reproduced here.

**Authoritative source**: <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html#release-dun-ig-fhir>.

This table, along with the rest of the IG authoring/publishing best practices, is covered by the [`ig-builder`](../../ig-builder/SKILL.md) skill for IG authors/editors (currently French-only) — see `ig-builder/references/preparation-release.md`.

## Sources

- Doctrine: <https://interop.esante.gouv.fr/ig/doctrine/doctrine.html>
- Committee structure: <https://interop.esante.gouv.fr/ig/doctrine/comitologie.html>
- Interoperability trajectory: <https://interop.esante.gouv.fr/ig/doctrine/0.1.0-ballot/trajectoire-iop.html>
- Best practices: <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html>
- HL7 publication-request documentation: <https://confluence.hl7.org/spaces/FHIR/pages/144970227/IG+Publication+Request+Documentation>
