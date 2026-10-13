# Documentation sources for writing/publishing IGs

## FHIR documentation, publisher, and implementation guide guidance

- <https://confluence.hl7.org> — HL7 documentation (process, FHIR IG version support, publication request...).
- <https://build.fhir.org/ig/FHIR/ig-guidance> — official HL7 guidance for writing IGs.
- <https://chat.fhir.org> — HL7 FHIR chat, useful for specific writing/publishing questions.
- <https://www.argentixinfo.com/ig/howtopub> — practical IG publishing guide.
- <https://smart.who.int/ig-starter-kit> — WHO starter kit for starting an IG.

## FSH grammar (FHIR Shorthand)

- <https://build.fhir.org/ig/HL7/fhir-shorthand> — full specification of the FSH grammar used by SUSHI.

## Tool source code

- <https://github.com/hapifhir/org.hl7.fhir.core> — HL7's reference Java library (validation, FHIR core).
- <https://github.com/HL7/fhir> — the FHIR specification itself.
- <https://github.com/HL7/fhir-ig-publisher> — IG Publisher, the tool that generates IG websites.
- <https://github.com/FHIR/sushi> — SUSHI, the FSH → FHIR compiler.

## Example repo and templates

- <https://github.com/FHIR/sample-ig/> — official HL7 example repo, recommended starting point for an IG outside the ANS ecosystem (see `demarrage-ig.md`).
- <https://github.com/HL7/fhir-ig-template> — source of the `hl7.fhir.template` template (official HL7/FHIR look).
- <https://build.fhir.org/ig/FHIR/ig-guidance/using-templates.html> — full reference on available IG Publisher templates, including the neutral `fhir.base.template`.
- <https://github.com/ansforge/IG-modele> — ANS base skeleton, recommended starting point for an ANS/ansforge IG (see `demarrage-ig.md`).
- <https://github.com/ansforge/interop-IG-style> — ANS style only (logos, CSS) to integrate into the IG, not a complete skeleton — not to be confused with `IG-modele`.

## Reference GitHub organizations

### ANS (Agence du Numérique en Santé)

<https://github.com/ansforge> — the ANS's official organization, containing French Implementation Guides and FHIR resources (référentiel guides and project guides).

### Interop-Santé (HL7 France association)

<https://github.com/Interop-Sante> — Interopsanté HL7 France association, health interoperability work and standards in France (notably `hl7.fhir.fr.core`).

## Going further

For questions that don't concern writing/publishing an IG but rather consuming it (which FHIR version to use, which IGs already exist, French terminologies, CI-SIS governance), see the `fhir-france-implementer-en` skill and its `references/catalogue-igs.md` file for the catalogue of existing French IGs.
