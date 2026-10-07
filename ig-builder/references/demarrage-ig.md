# Démarrer un nouvel IG FHIR français

## Repo modèle ANS

Pour créer un IG (y compris un IG minimal de test ou de reproduction de bug), partir du modèle **`ansforge/IG-modele`** (<https://github.com/ansforge/IG-modele>) plutôt que de construire une structure de projet à la main :

- `ig.ini` — utilise le template `ans.fr.template#current`.
- `sushi-config.yaml` — `parameters`, i18n français/anglais, `pages`, `menu` renseigné directement dans ce fichier (voir plus bas).
- Scripts `_genonce` / `_updatePublisher` — pour générer l'IG localement et maintenir à jour l'IG Publisher.

Ne pas confondre ce repo avec **`ansforge/interop-IG-style`** (<https://github.com/ansforge/interop-IG-style>) : ce second repo ne contient **que** le style ANS (logos, CSS) à intégrer dans un IG — ce n'est pas un squelette de projet complet, il ne faut pas en partir pour créer un nouvel IG.

## Structure de `sushi-config.yaml`

- Les menus de navigation de l'IG se déclarent dans la clé `menu:` de `sushi-config.yaml` — **jamais** via un fichier `menu.xml` séparé.
- Après toute modification de `sushi-config.yaml`, lancer `sushi .` et corriger toutes les erreurs avant de committer ou pousser (voir `conventions-fsh.md`).
- Les champs `version`, `status` et `releaseLabel` de ce fichier doivent correspondre au statut CI-SIS visé — voir le tableau de correspondance dans `preparation-release.md`, à ne jamais déduire par analogie.

## Pages de contenu (`input/pagecontent/`)

Règle de heading level pour tous les fichiers `.md` des IGs (et uniquement ceux d'IGs) : ils doivent commencer au niveau `###`. Les niveaux `#` et `##` sont générés automatiquement par l'IG Publisher — un fichier qui commence à `#` ou `##` produira une hiérarchie de titres incorrecte dans l'IG publié.

## Vérification

- [ ] Le projet a bien été initialisé à partir de `ansforge/IG-modele` (ou en conserve la structure — `ig.ini`, `sushi-config.yaml`, scripts de génération).
- [ ] Le style ANS, s'il est utilisé, provient de `ansforge/interop-IG-style` et a été intégré, pas recopié à la main.
- [ ] Aucun `menu.xml` n'existe dans le projet — le menu est dans `sushi-config.yaml`.
- [ ] Les fichiers `.md` de `input/pagecontent/` commencent tous à `###`.
