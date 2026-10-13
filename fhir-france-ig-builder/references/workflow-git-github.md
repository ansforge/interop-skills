# Workflow Git/GitHub pour un repo d'IG ANS

## Règles générales

- **Ne jamais éditer directement sur `main`** : créer une branche dédiée et une PR pour chaque changement, sauf instruction contraire explicite de l'utilisateur.
- **Toujours confirmer avec l'utilisateur la branche cible et le dépôt exact** (organisation + nom de repo) avant de démarrer une opération Git (création de branche, push, PR) — ne jamais supposer `main` ou un repo par défaut.

## Template de Pull Request (ANS)

Avant de créer une PR sur un repo ANS, lire `.github/pull_request_template.md` du repo cible et utiliser ce format exact s'il correspond. Pour les repos `ansforge`, le template standard est :

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

Remplacer `[nom-du-repo]` et `[ajouter_nom_de_la_branche]` par les valeurs réelles. **Si un template différent existe dans le repo cible, lui donner la priorité** sur ce template standard.

## Après un push : vérifier le QA

Le site de l'IG se déploie via GitHub Pages après un push — l'URL suit le format `https://[org].github.io/[nom-repo]/[nom-branche]/ig/`, et la page QA `https://[org].github.io/[nom-repo]/[nom-branche]/ig/qa.html`. **Attendre la fin du déploiement GitHub Pages avant de lire `qa.html`** — le lire trop tôt renvoie une version obsolète ou une 404, pas une absence réelle d'erreur.

## Vérification

- [ ] Le travail se fait sur une branche dédiée, jamais directement sur `main`.
- [ ] La branche cible et le dépôt ont été confirmés avec l'utilisateur avant toute opération Git.
- [ ] La description de la PR suit le template du repo cible (`.github/pull_request_template.md` en priorité, sinon le template standard ci-dessus).
- [ ] Le déploiement GitHub Pages est terminé avant toute lecture de `qa.html`.
