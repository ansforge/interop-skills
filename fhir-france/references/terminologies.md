# Terminologies françaises pour FHIR

## SMT — Serveur Multi-Terminologies

- **URL** : <https://smt.esante.gouv.fr/fhir>
- **Rôle** : serveur de terminologie national officiel de l'ANS, exposant les terminologies de santé françaises en FHIR.
- **Confirmation indépendante** : référencé dans le registre officiel de la HL7 FHIR Foundation (`ansforge/ig-registry`, fichier `hl7-fr-tx-servers.json`) :
  ```
  code: "ans-fr-tx"
  name: "Agence du Numérique en Santé (ANS) Terminology Server"
  url: "https://smt.esante.gouv.fr/fhir"
  fhirVersions: [{"version": "R4", "url": "https://smt.esante.gouv.fr/fhir"}]
  ```
- **Autoritatif pour** : les terminologies publiées sous `https://mos.esante.gouv.fr/*` et `https://smt.esante.gouv.fr/*`, ainsi que l'extension française de SNOMED CT (`http://snomed.info/sct/11000315107*`).

## IG Terminologies / NOS

- **URL** : <https://interop.esante.gouv.fr/terminologies>
- **Rôle** : publie des versions figées des **NOS (Nomenclatures des Objets de Santé)** — une sorte de "snapshot" stable de ce qui existe sur le SMT, utile quand on a besoin d'une référence versionnée plutôt que de l'état courant du serveur.
- **Formats disponibles** : PDF, CSV, XML, SVS, XML/FHIR, JSON/FHIR.
- **Version observée à la date de MAJ de ce fichier (2026-10-01)** : v1.7.0 (à revérifier — ce numéro évolue régulièrement).
- **IG associé** : `IG-NOS` / `ans.fhir.fr.nos` (versions observées jusqu'à 1.5.0), documente les value sets NOS en forme FHIR-native, avec notes de migration "NOS vers SMT".
- **Outillage complémentaire** : `ansforge/interop-conversion-smt-csv-fhir` (conversion CSV ↔ FHIR), `ansforge/interop-outil-fhir-terminology-server` (serveur de terminologie de sandbox préconfiguré avec les terminologies françaises, fork de FHIRSmith).

## Convention de nommage des artefacts terminologiques

Documentée sur <https://interop.esante.gouv.fr/terminologies/convention.html>. Trois familles de préfixes :

| Préfixe | Signification | Type FHIR correspondant | Exemple |
|---|---|---|---|
| `TRE_` | Terminologie de Référence | CodeSystem | `TRE_R75_InseeNAFrev2Niveau5` (codes INSEE NAF rev2 niveau 5), `TRE_A03-ClasseDocument` |
| `JDV_` | Jeu De Valeurs — value set extrait d'une ou plusieurs TRE | ValueSet | `JDV_J07_XdsTypeCode_CISIS`, `JDV_J105_EnsembleDiplome_RASS` |
| `ASS_` | Table d'ASSociation — correspondance entre ≥2 TRE/JDV | ConceptMap | `ASS_A23_ASR_ActiviteModaliteForme` |

**Format général** : `<TYPE>_<code>_<label>`, par exemple `TRE_A03-ClasseDocument` (noter que le séparateur entre code et label peut varier — tiret ou underscore selon les artefacts existants, vérifier l'exemple le plus récent avant de reproduire le motif).

## Pour comparaison : terminologies internationales

- Registre HL7 international des terminologies : <https://terminology.hl7.org/en>
- Serveur de terminologie FHIR international (tx.fhir.org) : <https://tx.fhir.org/>
- SNOMED CT (racine internationale, dont dérive l'extension française) : géré par SNOMED International

## TODO de vérification

- [ ] Revérifier le numéro de version NOS courant sur <https://interop.esante.gouv.fr/terminologies>
- [ ] Confirmer si `IG-NOS`/`ans.fhir.fr.nos` a dépassé la version 1.5.0 observée
