# Démarrer un nouvel IG FHIR français

## Repo modèle : hors ANS vs ANS vs Interop-Santé

Pour créer un IG (y compris un IG minimal de test ou de reproduction de bug), ne jamais construire une structure de projet à la main — toujours partir d'un repo squelette maintenu, dont le choix dépend du périmètre de l'IG :

- **IG hors écosystème ANS/Interop-Santé** : partir du repo d'exemple officiel HL7 **`FHIR/sample-ig`** (<https://github.com/FHIR/sample-ig/>) — c'est le point de départ maintenu par HL7 International pour tout nouvel IG, structure de dossiers et scripts de génération inclus.
- **IG ANS/ansforge** : partir du repo **`ansforge/IG-modele`** (<https://github.com/ansforge/IG-modele>) — squelette de base ANS (`ig.ini` avec le template `ans.fr.template#current`, `sushi-config.yaml`, scripts `_genonce`/`_updatePublisher`), à ne pas confondre avec `ansforge/interop-IG-style` qui ne fournit que le style ANS (logos, CSS) à intégrer dans l'IG, pas un squelette complet.
- **IG Interop-Santé** : partir du repo **`Interop-Sante/hl7.ig.fr.sample`** (<https://github.com/Interop-Sante/hl7.ig.fr.sample>) — squelette de base maintenu par l'association Interopsanté HL7 France pour les IGs de ce périmètre (ex. `hl7.fhir.fr.core`).

## Template

Pour un IG parti de `FHIR/sample-ig`, le choix du template se fait dans `ig.ini` (`template = ...`), avec deux options maintenues par HL7 International :

- **`fhir.base.template`** — template de base neutre, sans logo HL7/FHIR, explicitement conçu par HL7 comme socle pour la plupart des IGs **non-HL7** (c'est le choix par défaut à privilégier ici).
- **`hl7.fhir.template`** — hérite de `fhir.base.template` et ajoute le logo et la charte graphique FHIR/HL7 ; source : <https://github.com/HL7/fhir-ig-template>. À utiliser seulement si l'apparence officielle HL7 est explicitement souhaitée.

Référence complète sur les templates disponibles : <https://build.fhir.org/ig/FHIR/ig-guidance/using-templates.html>.

## Structure de `sushi-config.yaml`

- Les menus de navigation de l'IG se déclarent dans la clé `menu:` de `sushi-config.yaml` — **jamais** via un fichier `menu.xml` séparé.
- Après toute modification de `sushi-config.yaml`, lancer `sushi .` et corriger toutes les erreurs avant de committer ou pousser (voir `conventions-fsh.md`).
- Les champs `version`, `status` et `releaseLabel` de ce fichier doivent correspondre au statut CI-SIS visé — voir le tableau de correspondance dans `preparation-release.md`, à ne jamais déduire par analogie.

## Pages de contenu (`input/pagecontent/`)

Règle de heading level pour tous les fichiers `.md` des IGs (et uniquement ceux d'IGs) : ils doivent commencer au niveau `###`. Les niveaux `#` et `##` sont générés automatiquement par l'IG Publisher — un fichier qui commence à `#` ou `##` produira une hiérarchie de titres incorrecte dans l'IG publié.

## Vérification

- [ ] Le projet a bien été initialisé à partir du bon repo squelette selon le périmètre — `FHIR/sample-ig` hors ANS/Interop-Santé, `ansforge/IG-modele` pour un IG ANS/ansforge, `Interop-Sante/hl7.ig.fr.sample` pour un IG Interop-Santé (ou en conserve la structure — `ig.ini`, `sushi-config.yaml`, scripts de génération).
- [ ] Pour un IG hors ANS, le template déclaré dans `ig.ini` est `fhir.base.template` (neutre) sauf besoin explicite de l'apparence HL7 (`hl7.fhir.template`) — pas un style ANS imposé par défaut. Pour un IG ANS, le template est `ans.fr.template#current`.
- [ ] Aucun `menu.xml` n'existe dans le projet — le menu est dans `sushi-config.yaml`.
- [ ] Les fichiers `.md` de `input/pagecontent/` commencent tous à `###`.
