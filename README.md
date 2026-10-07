# interop-skills

*English version: [README.en.md](README.en.md)*

Skills d'interopérabilité en santé en France, packagés comme plugin [Claude Code](https://claude.com/claude-code) et utilisables par tout assistant IA compatible (Claude, Mistral, ...), maintenus par l'ANS (Agence du Numérique en Santé).

## À quoi ça sert ?

Si vous implémentez ou produisez des ressources FHIR en France (API, serveur FHIR, stockage, batch...), ces skills aident votre assistant IA (Claude, Mistral, ou autre) à trouver **la bonne spec au bon moment** : version FHIR à utiliser, IG existant pour votre cas d'usage, terminologies françaises, gouvernance CI-SIS — plutôt que de réinventer une solution déjà spécifiée ou de partir sur une base obsolète.

## Skills disponibles

- **[fhir-france](fhir-france/SKILL.md)** — Pour les développeurs qui implémentent ou produisent des ressources FHIR (API, serveur FHIR, stockage, batch...) : quelle version FHIR utiliser (R4/R5/R6, alignement EHDS), catalogue des IGs publiés (FR Core, guides ANS, OSIRIS...), terminologies (SMT, NOS, conventions TRE_/JDV_/ASS_), gouvernance CI-SIS. Ne couvre pas la rédaction/publication d'IG (FSH/SUSHI, release) — voir la roadmap ci-dessous.
- **[fhir-france-en](fhir-france-en/SKILL.md)** — Doublon anglais synchronisé de `fhir-france`, même contenu, mêmes sources.

## À venir

- **ig-builder** — skill destiné aux auteurs/éditeurs d'IG FHIR français : rédaction FSH/SUSHI, process de release (`sushi-config.yaml`/`publication-request.json`), conventions d'alias, workflow GitHub des repos d'IG. S'appuiera notamment sur la documentation bonnes pratiques déjà rédigée sur <https://interop.esante.gouv.fr/ig/documentation/>.

## Installation

### Via le marketplace de plugins Claude Code (recommandé)

```
claude plugin marketplace add ansforge/interop-skills
claude plugin install fhir-france@interop-skills
```

Ou, dans une session Claude Code interactive :

```
/plugin marketplace add ansforge/interop-skills
/plugin install fhir-france@interop-skills
```

### Installation manuelle (sans plugin)

Clonez ou copiez le dossier `fhir-france/` dans votre répertoire de skills Claude Code :

- Pour tous vos projets : `~/.claude/skills/fhir-france/`
- Pour un projet donné : `<votre-projet>/.claude/skills/fhir-france/`

## Contribuer

Un cas d'usage non couvert par un IG existant ? Avant de concevoir une solution ad hoc, écrivez une **expression de besoin** auprès de l'ANS — c'est le point d'entrée officiel du processus de gouvernance CI-SIS (voir `fhir-france/references/gouvernance-cisis.md`).

Une spec référencée ici pose un problème concret (ambiguïté, question d'implémentation, suggestion) ? Les retours sont les bienvenus via les **issues GitHub du repo concerné** (ex. `github.com/ansforge/<repo>/issues`).

Pour proposer une amélioration de ces skills eux-mêmes, ouvrez une issue ou une PR sur ce dépôt.
