# Starting a new French FHIR IG

## Skeleton repo: outside ANS vs. ANS

To create an IG (including a minimal test or bug-reproduction IG), never build a project structure by hand — always start from a maintained skeleton repo, chosen according to the IG's scope:

- **IG outside the ANS ecosystem**: start from the official HL7 example repo **`FHIR/sample-ig`** (<https://github.com/FHIR/sample-ig/>) — this is the starting point maintained by HL7 International for any new IG, folder structure and generation scripts included.
- **ANS/ansforge IG**: start from the **`ansforge/IG-modele`** repo (<https://github.com/ansforge/IG-modele>) — the ANS base skeleton (`ig.ini` with the `ans.fr.template#current` template, `sushi-config.yaml`, `_genonce`/`_updatePublisher` scripts), not to be confused with `ansforge/interop-IG-style`, which only provides the ANS style (logos, CSS) to integrate into the IG, not a complete skeleton.

## Template

For an IG started from `FHIR/sample-ig`, the template is chosen in `ig.ini` (`template = ...`), with two options maintained by HL7 International:

- **`fhir.base.template`** — neutral base template, no HL7/FHIR logo, explicitly designed by HL7 as a base for most **non-HL7** IGs (this is the default choice to prefer here).
- **`hl7.fhir.template`** — inherits from `fhir.base.template` and adds the FHIR/HL7 logo and visual identity; source: <https://github.com/HL7/fhir-ig-template>. Use only if the official HL7 look is explicitly wanted.

Full reference on available templates: <https://build.fhir.org/ig/FHIR/ig-guidance/using-templates.html>.

## `sushi-config.yaml` structure

- The IG's navigation menus are declared in the `menu:` key of `sushi-config.yaml` — **never** via a separate `menu.xml` file.
- After any change to `sushi-config.yaml`, run `sushi .` and fix all errors before committing or pushing (see `conventions-fsh.md`).
- The `version`, `status`, and `releaseLabel` fields of this file must match the targeted CI-SIS status — see the mapping table in `preparation-release.md`, never infer by analogy.

## Content pages (`input/pagecontent/`)

Heading level rule for all `.md` files in IGs (and only IG files): they must start at level `###`. Levels `#` and `##` are generated automatically by the IG Publisher — a file that starts at `#` or `##` will produce an incorrect heading hierarchy in the published IG.

## Verification

- [ ] The project was correctly initialized from the right skeleton repo for its scope — `FHIR/sample-ig` outside ANS, `ansforge/IG-modele` for an ANS/ansforge IG (or retains its structure — `ig.ini`, `sushi-config.yaml`, generation scripts).
- [ ] For an IG outside ANS, the template declared in `ig.ini` is `fhir.base.template` (neutral) unless the official HL7 look is explicitly needed (`hl7.fhir.template`) — not an ANS style imposed by default. For an ANS IG, the template is `ans.fr.template#current`.
- [ ] No `menu.xml` exists in the project — the menu is in `sushi-config.yaml`.
- [ ] All `.md` files in `input/pagecontent/` start at `###`.
