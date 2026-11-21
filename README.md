# LOF-ODP-001: Legal Act and Legal Document

| | |
|---|---|
| **Status** | Draft 0.2.0, for review by the LOF founding coordinators |
| **IRI** | https://w3id.org/lof/odp-001.owl |
| **Specification** | https://legal-ontologies-foundry.github.io/odp/odp-001/ |
| **License** | [CC BY 4.0](LICENSE) |
| **Contact** | David R. Koepsell (drkoepsell@tamu.edu) |

## Scope

Covers the distinction between a legal act (a process), the legal content it establishes (a generically dependent continuant), and the legal documents that carry that content (material entities), together with the relations among them. Distinguishes three kinds of legal content (legal norms, legal definitions, and legal designators) but excludes the finer internal structure of legal content (articles, clauses, numbering) and the positions and roles that content creates, which are covered by LOF-ODP-002 and LOF-ODP-003.

## Competency questions

1. Which legal act established this legal content, and when?
2. Which persons or organizations participated in that act?
3. Under what pre-existing legal content (enabling statute, procedural rule) was the act performed?
4. Which documents carry this legal content?
5. Do these two documents carry the same legal content?
6. Was this act performed by means of a document, and if so which one?
7. Which documents evidence this act, and does any act stand behind this document at all?
8. Which parts of this legal content are norms, which are definitions, and which designate it?

## BFO grounding (LOF-P-004)

| Term | BFO category | Rationale |
|---|---|---|
| legal act | process (BFO:0000015) | Unfolds in time and has temporal parts; outlived by what it establishes. |
| legal content | generically dependent continuant (BFO:0000031) | Concretized in many copies; survives the loss of any one copy. |
| legal norm, legal definition, legal designator | generically dependent continuant, as kinds of legal content | A statute has parts of all three kinds, so the statute as a whole is none of them. |
| legal document | material entity (BFO:0000040) | The particular paper or stored file; digital documents treated as patterns in material media. |

## Documents as instruments and as evidence

Documents do not act; persons and organizations do. A document takes part in a legal act in one of two ways:

- **Instrument** (`performed by means of`): the act is performed by means of the document, as in executing a deed or signing a statutory form before witnesses. The law makes the writing part of the act.
- **Evidence** (`evidences`): the document records or attests to an act performed independently of it, and may be created afterward. Evidencing is not participation.

The two come apart in both directions: an act can occur with no document (an oral contract), and a document can exist with no act behind it (a forgery, or a record generated without anyone's act). The pattern never infers an act, role, or position from the existence of a document alone. An instrument usually also evidences its act, so the relations are not disjoint.

## Alignment (LOF-P-015)

Legal content corresponds to the Work and Expression levels of FRBR-derived legal standards (Akoma Ntoso, ELI); legal document corresponds to the Item level. Legal content is a close match to IAO information content entity (IAO:0000030). IAO 'document' (IAO:0000310) is itself an information content entity and so corresponds to legal content, not to legal document. In the Common Core Ontologies, legal content is an information content entity, legal document an information bearing entity, and legal norm, legal definition, and legal designator correspond to process regulation, descriptive ICE, and designative ICE; these alignments are stated in the LOF to CCO bridge, so the pattern itself stays grounded directly in BFO.

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
make release VERSION=0.2.0   # writes the two release files to the repo root
```

Requires Java 11 or later; ROBOT is downloaded on first use. The same checks
run on every pull request (`.github/workflows/qc.yml`).

## Citation

Koepsell, D. R. (2026). *LOF-ODP-001: Legal Act and Legal Document*, version 0.2.0 (draft). Legal Ontologies
Foundry. https://w3id.org/lof/odp-001/releases/0.2.0/lof-odp-001.owl
