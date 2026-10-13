# interop-skills

*Version française : [README.md](README.md)*

Health interoperability skills for France, packaged as a [Claude Code](https://claude.com/claude-code) plugin and usable by any compatible AI assistant (Claude, Mistral, ...), maintained by the ANS (Agence du Numérique en Santé / French Digital Health Agency).

## What is this for?

If you implement or produce FHIR resources in France (API, FHIR server, storage, batch...), these skills help your AI assistant (Claude, Mistral, or other) find **the right spec at the right time**: which FHIR version to use, existing IG for your use case, French terminologies, CI-SIS governance — rather than reinventing a solution that already has a specification, or building on an outdated one.

## Available skills

- **[fhir-france-en](fhir-france-en/SKILL.md)** — For developers who implement or produce FHIR resources (API, FHIR server, storage, batch...): which FHIR version to use (R4/R5/R6, EHDS alignment), catalogue of published IGs (FR Core, ANS guides, OSIRIS...), terminologies (SMT, NOS, TRE_/JDV_/ASS_ conventions), CI-SIS governance. Does not cover IG authoring/publishing (FSH/SUSHI, release) — see `ig-builder` below.
- **[fhir-france](fhir-france/SKILL.md)** — Synchronized French twin of `fhir-france-en`, same content, same sources.
- **[ig-builder](ig-builder/SKILL.md)** — *French only for now.* For French FHIR IG authors/editors: starting an IG from the ANS template repo, FSH/SUSHI conventions (naming, aliases, bindings), Git/GitHub workflow (branch + PR, ANS template), release preparation (CI-SIS status ↔ `sushi-config.yaml`/`publication-request.json` mapping, change-log, milestones). Does not cover consuming already-published FHIR resources — see `fhir-france-en` above.

## Installation

### Via the Claude Code plugin marketplace (recommended)

```
claude plugin marketplace add ansforge/interop-skills
claude plugin install fhir-france-en@interop-skills
```

Or, in an interactive Claude Code session:

```
/plugin marketplace add ansforge/interop-skills
/plugin install fhir-france-en@interop-skills
```

### Manual installation (without the plugin system)

Clone or copy the `fhir-france-en/` folder into your Claude Code skills directory:

- For all your projects: `~/.claude/skills/fhir-france-en/`
- For a given project: `<your-project>/.claude/skills/fhir-france-en/`

## Contributing

A use case not covered by an existing IG? Before designing an ad hoc solution, write a **statement of need** (*expression de besoin*) to the ANS — the official entry point of the CI-SIS governance process (see `fhir-france-en/references/gouvernance-cisis.md`).

A spec referenced here has a concrete problem (ambiguity, implementation question, suggestion)? Feedback is welcome via the **GitHub issues of the relevant repo** (e.g. `github.com/ansforge/<repo>/issues`).

To suggest an improvement to these skills themselves, open an issue or a PR on this repository.
