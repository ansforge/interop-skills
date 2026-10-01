# Version FHIR en France — détail et sources

## Conclusion

**R4 (4.0.1)** est la version mandatée/recommandée par défaut pour tout IG FHIR français. Ce choix a été explicitement débattu et tranché par l'ANS via une concertation publique dédiée, et non simplement déduit de bonnes pratiques internes.

## La concertation ANS "FHIR R5 ou R4"

- **Période** : 25 octobre 2023 → 25 janvier 2024
- **URL** : <https://participez.esante.gouv.fr/project/fhir-r5-ou-r4/presentation/presentation> (page en JavaScript, difficile à récupérer par un simple fetch automatisé — ouvrir dans un navigateur si besoin de re-citer le texte exact)
- **Contexte** : FHIR R5 a été publié en mars 2023. Cette release propose une documentation améliorée, une maturité accrue pour certaines ressources, et 2000+ changements mineurs — mais aucune nouvelle fonctionnalité ni nouveau paradigme majeur.

### Argumentaire de l'ANS (synthèse fidèle du contenu de la concertation)

FHIR core a été conçu comme foncièrement générique (très peu de champs obligatoires, pas de terminologie fixée, usage libre des extensions) pour faciliter son déploiement — ce qui implique qu'il doit être adapté pour chaque pays et chaque cas d'usage via des guides d'implémentation. La question n'est donc pas "R4 ou R5 dans l'absolu" mais "est-ce que migrer vaut le coût, vu que tout l'écosystème français est déjà en R4 ?"

**Tout l'écosystème FHIR France est en R4** au moment de la concertation :
- Les profils : FrCore (Interop'Santé), les volets du CI-SIS (agenda, mesures, cercle de soins, cahier de liaison)
- Les projets nationaux : Mon Espace Santé, Annuaire Santé, le ROR, le SAS, le SMT
- Les projets européens et pays frontaliers, majoritairement en R4 : HL7 Europe, UK, Allemagne, Suisse, IHE

**Pourquoi ne pas migrer vers R5 (au moment de la concertation)** :
- R5 n'est **pas rétrocompatible** avec R4 → coûts de migration élevés (spécifications ET implémentations).
- Risque de coexistence R4/R5 dans l'écosystème : coûts de double maintenance pour les établissements de santé, confusion pour les nouveaux entrants dans l'interopérabilité (faut-il utiliser R4 ou R5 ?).
- Délais très longs pour migrer l'existant ou obtenir les premières spécifications en R5 — créer/mettre à jour un IG est un cycle itératif de plusieurs mois/années : (1) identification du besoin fonctionnel, (2) création/MAJ de l'IG, (3) concertation de 3 mois, (4) traitement des commentaires, (5) release, (6) implémentation, (7) retours/amélioration continue. Le temps d'arriver aux premières implémentations R5, la concertation pour **R6** serait probablement déjà lancée (annoncée "attendue mi-2024" dans la page d'origine — à vérifier si elle a eu lieu).
- Avis externe : Grahame Grieve (directeur produit FHIR, HL7) n'encourage pas particulièrement le passage à R5. Les USA n'ont pas prévu de passer à R5 non plus, sauf quelques cas d'usage marginaux.

**Pourquoi R5 reste intéressant ponctuellement** :
- Documentation améliorée (à regarder pour éclaircissements sur des points précis).
- Certains cas d'usage dont les ressources ont beaucoup évolué entre R4 et R5 — exemple cité : les produits médicamenteux (medicinal products).

**Trajectoire retenue par l'ANS** :
1. Continuer à utiliser R4 par défaut ; utiliser, le cas échéant, des extensions R4 qui imitent les nouveaux attributs R5, pour faciliter une transition future.
2. Étudier la pertinence de R5 au cas par cas : les ressources concernées ont-elles beaucoup gagné en maturité ? Y a-t-il un besoin d'échanges internationaux nécessitant R5 ? Peut-on se passer de l'héritage de l'écosystème R4 pour ce cas d'usage précis ?
3. Anticiper l'usage de R6 dès sa sortie, avec un focus sur FrCore en R6 et la mise à jour/déploiement de nouveaux guides d'implémentation en R6.

**Point de méthode rappelé par l'ANS** : l'interopérabilité n'est pas d'abord une problématique de version ou de standard technique — c'est avant tout une problématique de modélisation de données, qui nécessite un travail collectif pour identifier les cas d'usage prioritaires et les données essentielles à échanger.

### Sources citées par la page de concertation
- <https://confluence.hl7.org/display/FHIRI/FHIR+IG+version+support>
- <https://fire.ly/blog/fhir-r5-is-finally-on-the-shelves-but-should-you-implement-it>
- <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10148270>
- <https://www.hl7.org/fhir/diff.html>
- <https://wiki.ihe.net/index.php/Guidance_on_writing_Profiles_of_FHIR>
- <https://wiki.ihe.net/index.php/Profiles>

## Alignement européen (EHDS)

Le règlement européen EHDS (European Health Data Space) base actuellement ses actes d'exécution sur FHIR R4 également — ce choix pourrait évoluer, à surveiller en parallèle du choix français.

Au-delà de la version FHIR, l'EHDS impose aussi la production de **6 documents de santé en FHIR**, dont le VSM/Patient Summary (porté en France par `interop-ig-fhir-document-patient-summary`, statut WIP — voir `catalogue-igs.md`). Cette obligation de calendrier explique pourquoi plusieurs IGs français sont actuellement en statut Draft/WIP. Les 5 autres documents imposés par l'EHDS ne sont pas identifiés avec certitude ici — à rechercher avant d'affirmer lesquels ils sont.

## Autres sources ANS confirmant R4 comme norme

- Page "bonnes pratiques" ANS : <https://interop.esante.gouv.fr/ig/documentation/mod_bonnes_pratiques.html> — recommande de "privilégier l'usage de R4" pour tout nouvel IG, toute autre version nécessitant une justification explicite.
- Doctrine CI-SIS : <https://interop.esante.gouv.fr/ig/doctrine/doctrine.html> — FHIR R4 choisi comme modèle d'information standard pour les artefacts de connaissance médicale.
- Trajectoire interopérabilité CI-SIS : <https://interop.esante.gouv.fr/ig/doctrine/0.1.0-ballot/trajectoire-iop.html> — reprend l'argumentaire de la concertation (éviter une double transition R4→R5 puis R5→R6).

## TODO de vérification

- [ ] Vérifier si une concertation ou une doctrine publiée sur R6 existe désormais (annoncée "mi-2024" dans la page d'origine).
- [ ] Revisiter la page de concertation directement dans un navigateur si une citation exacte/complète est nécessaire (le fetch automatisé ne restitue que le titre, la page étant en JavaScript).
