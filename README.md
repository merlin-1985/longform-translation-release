# Longform Translation Release

A model-agnostic workflow skill for high-confidence long-form translation, independent review, evidence verification, controlled revision, and release QA.

**Status: v0.1.0.** Architecture review, isolated synthetic smoke testing, and packaging/frontmatter validation have passed. The release is workflow-only; no automation code is bundled.

## What it solves

Long translations need more than fluent sentences. This skill makes review findings traceable to actual source evidence, limits revision to an authorized change set, and binds the final deliverable to the version that passed QA.

## When to use it

Use it for books, technical documents, research reports, or other long PDF, DOCX, or EPUB projects that require independent review and auditable delivery. It also supports resuming an existing project at its last verified stage. A short, one-off passage usually does not need this lifecycle.

## Workflow overview

Source Freeze → Translation Bible → Primary Translation → Internal QA → Independent Review → Cross-check → Evidence Integrity Audit → Adjudication → Controlled Revision → Regression QA → Release Closeout.

FINAL_AUTHORITY is the external authorization source. Any capable model or agent may fill the execution roles below, but must not appoint itself as FINAL_AUTHORITY:

| Role | Responsibility |
|---|---|
| FINAL_AUTHORITY | External authority for scope, authorization, disputed evidence versions, and final delivery |
| PRIMARY_TRANSLATOR | Source preparation, Bible, translation units, and assembly |
| INTERNAL_QA_AGENT | Internal source/translation and consistency checks |
| INDEPENDENT_REVIEWER | Review in a context isolated from internal QA conclusions |
| ADJUDICATION_AGENT | Cross-check, evidence audit, decisions, and bounded scope |
| REVISION_AGENT | Authorized edits, regression QA, and release closeout |

One agent may fill multiple execution roles, but independent review still requires demonstrable information isolation. Using a different model alone does not establish independence.

## Major gates

| Gate | Success status |
|---|---|
| G1 | TRANSLATION BASELINE FROZEN |
| G2 | INDEPENDENT REVIEW COMPLETE |
| G3 | READY FOR REVISION |
| G4 | POST-REVISION QA PASS |
| G5 | FINAL RELEASE QA PASS |

Other stages use checkpoints. Gate criteria and mandatory STOP behavior are defined in [RELEASE_GATES.md](references/RELEASE_GATES.md).

## Core safety and evidence principles

- **Question-Specific Evidence Authority:** Original Source is authoritative for source wording and meaning; Frozen Translation Baseline for what the reviewed translation contained; Translation Bible for approved translation policy; Reviewer Evidence for what a reviewer claimed, subject to verification. Agent Judgment must not override the authoritative artifact for that question.
- A reviewer finding is a claim to verify. Recheck source quote, translation quote, location, context, root cause, and scope before revision.
- Separate SOURCE concerns from TRANSLATION defects. Do not silently correct the author's facts or add annotations.
- Preserve frozen evidence. Record reviewer errors through ERRATA and preserve superseded digest metadata when correcting a manifest.
- Adjudication does not edit the translation. Only authorized ACCEPT/MODIFY changes may be applied; a gate does not grant authorization.
- Resolve ambiguous names and terms by occurrence and source entity. Do not default to blind global replacement.
- Require actual artifacts, cross-format content evidence, reproducible artifact identity, and unexpected substantive diff = 0 before release.

**Reproducible Artifact Identity:** Every gated artifact MUST be bound to the exact reviewed version. For byte-addressable artifacts, record a persistent path/resource ID, version where applicable, and SHA-256 of the exact bytes. For provider-native artifacts without directly addressable source bytes, record the provider identity, persistent resource ID, and stable revision/version ID sufficient to reopen that exact revision. If exported later, also record export format, originating provider revision, and SHA-256 of the exported bytes. A mutable current-document link alone is insufficient.

## Repository structure

```text
.
├── README.md
├── LICENSE
├── SKILL.md
├── references/
│   ├── REVIEW_POLICY.md
│   └── RELEASE_GATES.md
├── templates/
│   ├── TRANSLATION_BIBLE.md
│   ├── FINDINGS.md
│   ├── FINAL_ADJUDICATION.md
│   ├── REVISION_CHANGE_LOG.md
│   └── FINAL_RELEASE_MANIFEST.md
└── docs/
    └── DESIGN_NOTES.md
```

## How to use the skill

1. Load [SKILL.md](SKILL.md) as the execution contract. Its identifier is `longform-translation-release`; this repository's name is `longform-translation-release`.
2. Confirm source, target language/locale, audience, scope, output formats, and existing authorization. Resume at the earliest unmet checkpoint.
3. Read the linked policy or gate section when it applies. Copy the needed templates into the translation project's own workspace and fill them with actual evidence. Do not overwrite this repository's templates with project records.
4. Before a gate, verify that its artifacts exist, can be read, and are bound to their current versions. A statement that a file was generated is insufficient.
5. At G5, return the final SSOT, actual deliverables, and manifest paths, then STOP.

The execution policy and templates are primarily in Simplified Chinese, with stable English role and status identifiers. The workflow is not limited to a particular target language. Format extraction, OCR, rendering, and comparison use the execution environment's existing capabilities; no implementation is bundled here.

Publication enhancement, typesetting redesign, index rebuild, new annotation campaigns, new fact-check campaigns, and literary rewriting require a separate workflow and authorization.

This workflow governs translation-quality release artifacts. It does not grant copyright, translation, publication, or distribution rights. If public distribution is intended, FINAL_AUTHORITY must confirm any required rights or permissions.

## Current status and roadmap

v0.1.0 is **workflow-only**. Architecture review, isolated synthetic smoke testing, and official `quick_validate.py` packaging/frontmatter validation passed. Automation is intentionally deferred; no scripts, schemas, CI, or workflow engine are included in this release.

Future work may consider artifact checks, traceability checks, occurrence-map assistance, diff guards, and document/visual evidence binding after separate review. No scripts, schemas, CI, or workflow engine are included. See [DESIGN_NOTES.md](docs/DESIGN_NOTES.md) for design choices and limitations.

## License

The workflow instructions, policies, templates, and documentation in this repository are available under the [MIT License](LICENSE). This repository contains no source books, translated manuscripts, or third-party review evidence; the license grants no rights to material supplied to a future translation project.
