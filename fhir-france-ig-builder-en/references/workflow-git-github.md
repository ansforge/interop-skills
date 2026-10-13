# Git/GitHub workflow for an ANS IG repo

## General rules

- **Never edit directly on `main`**: create a dedicated branch and a PR for each change, unless the user explicitly says otherwise.
- **Always confirm the target branch and exact repository** (organization + repo name) with the user before starting a Git operation (branch creation, push, PR) — never assume `main` or a default repo.

## Pull Request template (ANS)

Before creating a PR on an ANS repo, read the target repo's `.github/pull_request_template.md` and use that exact format if it matches. For `ansforge` repos, the standard template is:

```
## Description des changements

* 
* 

## Type de changement

- [ ] Nouveau contenu (profil, extension, page, exemple)
- [ ] Correction (erreur dans un profil, une page, une dépendance)
- [ ] Refactoring (pas de changement fonctionnel)
- [ ] Release

## Checklist

- [ ] `sushi-config.yaml` : `releaseLabel` est bien `ci-build` pour une version en développement
- [ ] `change-log.md` mis à jour
- [ ] La branche est à jour avec `main`

## Preview

https://ansforge.github.io/[nom-du-repo]/[ajouter_nom_de_la_branche]/ig
```

Replace `[nom-du-repo]` and `[ajouter_nom_de_la_branche]` with the actual values. **If a different template exists in the target repo, prioritize it** over this standard template.

## After a push: check the QA

The IG site deploys via GitHub Pages after a push — the URL follows the format `https://[org].github.io/[repo-name]/[branch-name]/ig/`, and the QA page `https://[org].github.io/[repo-name]/[branch-name]/ig/qa.html`. **Wait for the GitHub Pages deployment to finish before reading `qa.html`** — reading it too early returns a stale version or a 404, not an actual absence of errors.

## Verification

- [ ] The work is done on a dedicated branch, never directly on `main`.
- [ ] The target branch and repository were confirmed with the user before any Git operation.
- [ ] The PR description follows the target repo's template (`.github/pull_request_template.md` as priority, otherwise the standard template above).
- [ ] The GitHub Pages deployment is finished before any reading of `qa.html`.
