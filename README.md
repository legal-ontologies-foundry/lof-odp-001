# LOF-ODP-001: Legal Act and Legal Document

| | |
|---|---|
| **Status** | Draft 0.1.0, for review by the LOF founding coordinators |
| **IRI** | https://w3id.org/lof/odp-001.owl |
| **Specification** | https://legal-ontologies-foundry.github.io/odp/odp-001/ |
| **License** | [CC BY 4.0](LICENSE) |
| **Contact** | David R. Koepsell (drkoepsell@tamu.edu) |

## Scope

Covers the distinction between a legal act (a process), the legal content it establishes (a generically dependent continuant), and the legal documents that carry that content (material entities), together with the relations among them. Excludes the internal structure of legal content (provisions, clauses) and the positions and roles that content creates, which are covered by LOF-ODP-002 and LOF-ODP-003.

## Competency questions

1. Which legal act established this legal content, and when?
2. Which persons or organizations participated in that act?
3. Under what pre-existing legal content (enabling statute, procedural rule) was the act performed?
4. Which documents carry this legal content?
5. Do these two documents carry the same legal content?

## BFO grounding (LOF-P-004)

| Term | BFO category | Rationale |
|---|---|---|
| legal act | process (BFO:0000015) | Unfolds in time and has temporal parts; outlived by what it establishes. |
| legal content | generically dependent continuant (BFO:0000031) | Concretized in many copies; survives the loss of any one copy. |
| legal document | material entity (BFO:0000040) | The particular paper or stored file; digital documents treated as patterns in material media. |

## Alignment (LOF-P-015)

Legal content corresponds to the Work and Expression levels of FRBR-derived legal standards (Akoma Ntoso, ELI); legal document corresponds to the Item level. Legal content is a close match to IAO information content entity (IAO:0000030). IAO 'document' (IAO:0000310) is itself an information content entity and so corresponds to legal content, not to legal document.

## Files

| Path | Contents |
|---|---|
| `lof-odp-001.owl` | Full release: merged with imports and reasoned |
| `lof-odp-001-base.owl` | Base release: this pattern's own axioms only (import this) |
| `src/ontology/lof-odp-001-edit.owl` | Editors' file (OWL functional syntax; edit in Protégé) |
| `src/ontology/lof-odp-001-idranges.owl` | Term ID ranges (ODP001_0001000 to 0001999: first editor) |
| `src/sparql/` | QC checks run by `make test` |

## Building and testing

```
cd src/ontology
make test                    # HermiT consistency + seven SPARQL QC checks + ROBOT report
make release VERSION=0.1.0   # writes the two release files to the repo root
```

Requires Java 11 or later; ROBOT is downloaded on first use. The same checks
run on every pull request (`.github/workflows/qc.yml`).

## Citation

Koepsell, D. R. (2026). *LOF-ODP-001: Legal Act and Legal Document*, version 0.1.0 (draft). Legal Ontologies
Foundry. https://w3id.org/lof/odp-001/releases/0.1.0/lof-odp-001.owl
