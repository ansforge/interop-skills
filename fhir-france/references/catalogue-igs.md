# Catalogue des IGs FHIR français

> Catalogue non-exhaustif, construit par recherche sur GitHub (`ansforge`, `Interop-Sante`) et sur le catalogue officiel. **Le site <https://interop.esante.gouv.fr/ig/fhir/> fait foi** — vérifier en priorité là-bas avant de citer un statut ou une version comme certain.

## Sommaire

- [FR Core](#fr-core)
- [Guides référentiels (ANS)](#guides-référentiels-ans)
- [Guides projet (ANS)](#guides-projet-ans)
- [Autres / transversaux](#autres--transversaux)
- [Repos Interop'Santé](#repos-interopsanté)

## FR Core

| Élément | Détail |
|---|---|
| Repo | `Interop-Sante/hl7.fhir.fr.core` |
| IG publié | <https://hl7.fr/ig/fhir/core> (CI build : <https://build.fhir.org/ig/Interop-Sante/hl7.fhir.fr.core/>) |
| Mainteneur | Interop'Santé (HL7 France), développé conjointement avec l'ANS |
| Dernière version formelle | 2.2.0, statut final-text, active depuis 2026-03-25 (confirmé sur hl7.fr/ig/fhir/core) |
| Historique | 2.1.0 (2024-09-06), voir le "Directory of published versions" de l'IG pour l'historique complet |
| Base FHIR | R4 |
| Contenu | Profils de base (Patient, Practitioner, Organization, Encounter, Observation...), usage des identifiants INS/RPPS/ADELI/FINESS, terminologies françaises (CIM-10, CCAM, NABM) liées comme value sets |
| Rôle | Base générique recommandée pour toute implémentation FHIR française |

## Guides référentiels (ANS)

Volets transversaux, réutilisables par plusieurs métiers. Org GitHub : `ansforge`.

| IG | Repo | Statut/version connue | Description |
|---|---|---|---|
| Partage de Documents de Santé en mobilité (PDSm) | `IG-fhir-partage-de-documents-de-sante` | — | Partage de documents basé sur le profil IHE MHD ; alimente Mon espace santé / DMP |
| Mesures de santé | `interop-IG-fhir-mesures-de-sante` | v3.2.0 | Fréquence cardiaque, tension, pas, douleur, IMC, poids, taille, température, glycémie... |
| Gestion d'Agendas Partagés (GAP) | `interop-IG-fhir-gestion-agendas-partages` | — | Partage d'agendas entre professionnels de santé |
| Gestion du Cercle de Soins | `interop-IG-fhir-cercle-de-soins` | v2.0.0 | Gestion du cercle de soins autour d'un patient |
| Cahier de Liaison | `IG-fhir-cahier-de-liaison` | v3.0.0 | Carnet de coordination des soins |
| Traçabilité des Événements (TDE) | `interop-ig-fhir-tracabilite-evenements` / `IG-FHIR-tracabilite-evenements` | — | Spécification générique d'échange de traces d'événements |
| Notification d'Événements (NDE) | `interop-ig-fhir-notification-evenements` | — | Notifications d'événements |
| ePrescription | `interop-ig-fhir-ePrescription` | Draft | Fork de `hl7.fhir.fr.medication` ; prescription électronique (FR Medication Request, dispensation) |
| eDispensation | `interop-ig-fhir-edispensation` | — | Dispensation électronique, compagnon de l'ePrescription |
| Référentiel Médicament | `interop-ig-fhir-referentiel-medicament` | — | Données de référence médicamenteuses |

## Guides projet (ANS)

Spécifiques à un périmètre métier donné.

| IG | Repo | Statut/version connue | Description |
|---|---|---|---|
| Annuaire Santé | `IG-fhir-annuaire` | — | Données publiques de l'annuaire santé (RPPS/FINESS) via FHIR |
| Annuaire Santé (nouvelle API) | `annuaire-sante-fhir-documentation` | — | Documentation de l'API FHIR Annuaire Santé plus récente ("IRIS DP") |
| Répertoire Offre et Ressources en santé (ROR) | `IG-fhir-repertoire-offre-ressources-sante` (+ variante `-me24`) | — | Répertoire national de l'offre et des ressources en santé/médico-social |
| ECLAIRE (essais cliniques) | `IG-fhir-essais-cliniques` | v0.3.0, TU (technical update) | API REST pour essais cliniques accessibles interconnectés |
| Service d'Accès aux Soins (SAS) | `IG-fhir-service-acces-aux-soins` | — | Orientation des patients vers une offre de soins disponible |
| MSSanté (API Messagerie Sécurisée de Santé) | `interop-ig-fhir-api-messagerie-securisee-sante` | Draft | API FHIR pour la messagerie sécurisée de santé |

## Autres / transversaux

| IG | Repo | Description |
|---|---|---|
| EDS Socle Commun | `IG-FHIR-EDS-SOCLE-COMMUN` | Socle commun pour les Entrepôts de Données de Santé (EDS) — v0.1.0 |
| Télésurveillance | `IG-fhir-telesurveillance` | Suivi à distance (questionnaires/observations) |
| Médico-social — transfert DUI | `IG-fhir-medicosocial-transfert-donnees-dui` | Transfert de données entre systèmes médico-sociaux (Dossier Usager Informatisé) |
| Médico-social — suivi décisions d'orientation (SDO) | `IG-fhir-medicosocial-suivi-decisions-orientation` | Suivi des décisions MDPH vers les DUI |
| Traçabilité DMI | `interop-ig-fhir-tracabilite-dmi` | Traçabilité des Dispositifs Médicaux Implantables |
| Veille sanitaire | `IG-fhir-veille-sanitaire` | Surveillance sanitaire |
| Document Core (famille) | `interop-IG-metier-document-core`, `interop-IG-fhir-document-core`, `interop-IG-cda-document-core` | Modélisation générique de document (métier/FHIR/CDA), socle pour les comptes-rendus |
| Compte-rendu biologie | `interop-ig-document-cr-bio` | Compte-rendu de biologie — seul CR nommément confirmé à ce jour (imagerie/cancérologie : voir zones d'incertitude dans SKILL.md) |
| Patient Summary (FHIR) | `interop-ig-fhir-document-patient-summary` | Repo actif. ⚠️ **Ne pas confondre** avec `interop-ig-document-patient-summary` (ancien nom de repo, remplacé — ne plus citer comme repo courant). Reste à confirmer si cet IG porte la trajectoire FHIR du Volet de Synthèse Médicale (VSM, aujourd'hui en CDA R2) ou s'il s'agit d'un IG distinct de type International Patient Summary (IPS) — voir section "Zones d'incertitude" du SKILL.md |

## Repos Interop'Santé

Org GitHub : `Interop-Sante`.

| Repo | Statut | Description |
|---|---|---|
| `hl7.fhir.fr.core` | Publié (voir ci-dessus) | FR Core |
| `hl7.fhir.fr.structure` | — | Échange de données de structure interne des établissements de santé |
| `hl7.fhir.fr.medication` | WIP | Base du fork ePrescription ANS |
| `hl7.fhir.fr.preadmission` | — | Pré-admission en ligne |
| `hl7.fhir.fr.analyse-pharma` | WIP | Analyse pharmaceutique |

## TODO de vérification

- [ ] Rechercher sur `github.com/ansforge` des IGs imagerie/cancérologie sous des noms non évidents (168 repos au total, recherche par mot-clé uniquement effectuée à ce jour).
- [ ] Clarifier le statut exact de `interop-ig-fhir-document-patient-summary` vis-à-vis du VSM.
- [ ] Revérifier tous les statuts/versions listés ci-dessus contre <https://interop.esante.gouv.fr/ig/fhir/>.
