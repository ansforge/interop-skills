# FHIR version in France — details and sources

## Conclusion

**R4 (4.0.1)** is the default mandated/recommended version for any French FHIR IG. This choice was explicitly debated and settled by the ANS through a dedicated public consultation, not simply inferred from internal best practices.

## The ANS "FHIR R5 ou R4" consultation

- **Period**: October 25, 2023 → January 25, 2024
- **URL**: <https://participez.esante.gouv.fr/project/fhir-r5-ou-r4/presentation/presentation> (JavaScript-rendered page, hard to retrieve via a simple automated fetch — open it in a browser if you need to re-quote the exact text)
- **Context**: FHIR R5 was published in March 2023. This release offers improved documentation, increased maturity for some resources, and 2000+ minor changes — but no major new feature or paradigm shift.

### ANS rationale (faithful summary of the consultation's content)

FHIR core was designed to be fundamentally generic (very few mandatory fields, no fixed terminology, free use of extensions) to ease deployment — which means it must be adapted for each country and each use case via implementation guides. The question is therefore not "R4 or R5 in the abstract" but "is migrating worth the cost, given that the whole French ecosystem is already on R4?"

**The entire French FHIR ecosystem is on R4** at the time of the consultation:
- Profiles: FrCore (Interop'Santé), CI-SIS volets (agenda, measurements, circle of care, liaison booklet)
- National projects: Mon Espace Santé, Annuaire Santé, the ROR, the SAS, the SMT
- European projects and neighboring countries, mostly on R4: HL7 Europe, UK, Germany, Switzerland, IHE

**Why not migrate to R5 (at the time of the consultation)**:
- R5 is **not backward-compatible** with R4 → high migration costs (both specifications and implementations).
- Risk of R4/R5 coexistence in the ecosystem: double-maintenance costs for healthcare institutions, confusion for newcomers to interoperability (should they use R4 or R5?).
- Very long timelines to migrate existing work or obtain the first R5 specifications — creating/updating an IG is an iterative cycle spanning months/years: (1) identifying the functional need, (2) creating/updating the IG, (3) a 3-month consultation, (4) processing comments, (5) release, (6) implementation, (7) feedback/continuous improvement.
- External opinion: Grahame Grieve (FHIR product director, HL7) does not particularly encourage moving to R5. The US also has no plans to move to R5, except for a few marginal use cases.

**Why R5 remains occasionally useful**:
- Improved documentation (worth consulting for clarification on specific points).
- Certain use cases whose resources have changed significantly between R4 and R5 — the example cited: medicinal products.

**Chosen trajectory**:
1. Continue using R4 by default; where relevant, use R4 extensions that mimic new R5 attributes/resources, to ease a future transition.
2. Assess R5 relevance case by case: have the relevant resources gained significant maturity? Is there a need for international exchanges requiring R5? Can the R4 ecosystem legacy be set aside for this specific use case?
3. **Above all, align with the EHDS's position** — this is the criterion that outweighs any standalone ANS consideration for a possible move to R5/R6 (see EHDS section below).

This is no longer a matter of standalone ANS-centered monitoring: the position to follow is the **EHDS's**, which mandates R4 for its implementing acts (see below) — it is this European alignment that dictates the French trajectory, not a standalone ANS R6 consultation.

**Cross-version R5↔R4 IG** (<https://hl7.org/fhir/uv/xver-r5.r4>): this international HL7 implementation guide further reduces the appeal of migrating to R5 or R6, since it allows carrying new R5 attributes/resources into R4 via standardized extensions — exactly the mechanism envisioned in point 1 above, but now tooled by a dedicated IG rather than ad hoc extensions.

**Methodological point reiterated by the ANS**: interoperability is not primarily a version or technical standard issue — it is above all a data modeling issue, requiring collective work to identify priority use cases and the essential data to exchange.

### Sources cited by the consultation page

- <https://confluence.hl7.org/display/FHIRI/FHIR+IG+version+support>
- <https://fire.ly/blog/fhir-r5-is-finally-on-the-shelves-but-should-you-implement-it>
- <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10148270>
- <https://www.hl7.org/fhir/diff.html>
- <https://wiki.ihe.net/index.php/Guidance_on_writing_Profiles_of_FHIR>
- <https://wiki.ihe.net/index.php/Profiles>

## European alignment (EHDS) — the signal to follow for R4/R5/R6

The European EHDS (European Health Data Space) regulation currently also bases its implementing acts on FHIR R4. **The French position follows this European alignment rather than an ANS-specific timeline**: to know if/when to move to R5 or R6, it is the EHDS's position that must be monitored as a priority (see checklist in `SKILL.md`), not a possible standalone ANS R6 consultation.

Beyond the FHIR version, the EHDS also mandates the production of **6 categories of health documents in FHIR** (source: <https://esante.gouv.fr/espace-europeen-donnees-sante>):

1. Patient Summary (European equivalent of the Volet de Synthèse Médicale)
2. Electronic prescription
3. Electronic dispensation
4. Laboratory report
5. Hospital discharge letter
6. Medical imaging report and medical images

This timeline obligation explains why several French IGs are currently in Draft/WIP status. Mapping with known French IGs, and repos still to be identified for some of these documents: see `catalogue-igs.md`.

## Other ANS sources confirming R4 as the norm

- ANS "best practices" page: <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html> — recommends "favoring the use of R4" for any new IG, any other version requiring explicit justification.
- CI-SIS doctrine: <https://interop.esante.gouv.fr/ig/doctrine/doctrine.html> — FHIR R4 chosen as the standard information model for medical knowledge artifacts.
- CI-SIS interoperability trajectory: <https://interop.esante.gouv.fr/ig/doctrine/0.1.0-ballot/trajectoire-iop.html> — restates the consultation's rationale (avoiding a double transition R4→R5 then R5→R6).

## Verification TODO

- [ ] Check whether the EHDS has changed its position on the mandated FHIR version (currently R4) — this is the signal that matters most for a possible move to R5/R6.
- [ ] Revisit the consultation page directly in a browser if an exact/full quote is needed (automated fetch only returns the title, as the page is JavaScript-rendered).
