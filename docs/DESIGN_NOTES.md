# Design Notes

Status: PUBLIC DRAFT CANDIDATE v0.1. These notes describe the workflow design; they do not contain project execution records or replace the runtime policy.

## Design rationale

The workflow separates translation, independent review, source-grounded adjudication, controlled revision, and release QA. This makes a proposed change traceable from its finding to its source evidence, decision, actual edit, regression result, and final deliverable.

The core invariants carry most of the control: question-specific evidence authority, finding verification, SOURCE/TRANSLATION separation, preserved evidence, separated adjudication and revision, occurrence-aware replacement, and provable release artifacts. Source wording and meaning, reviewed translation content, and approved translation policy each have their own authoritative artifact rather than a total ordering.

## Model-agnostic roles

Roles describe responsibilities rather than vendors or model capabilities. One agent may fill several execution roles, provided the independent reviewer receives an isolated context. A different model is neither required nor sufficient for isolation. Internal conclusions become available for cross-check only after independent review is complete.

The FINAL_AUTHORITY is the external source of scope and authorization; an executing agent must not appoint itself to that role. G3 confirms evidence and a bounded change set; it does not create permission. Existing authorization remains valid within its scope.

## Generalized lessons

- A confident review can contain a source-quote mismatch. Verify the actual source and baseline; preserve the original record and add ERRATA when needed.
- A shared target-language name can refer to different source entities. Resolve each affected occurrence, including exclusions and substring collisions, before executing replacements.
- An artifact mentioned in a conversation may never have been materialized. Check actual paths or persistent IDs, readability, reproducible exact-version identities, and completed remote writes before a gate.
- A digest may describe a temporary snapshot rather than the authoritative artifact. Determine version authority, preserve superseded metadata, and rebind the actual bytes instead of guessing or reverting content to fit a hash.
- Updating QA fields can change a log's byte digest or provider revision without changing its edit instructions. Preserve the execution-time version and explain its relationship to the final record.
- A file hash or stable provider revision identifies an artifact version; it does not by itself prove that a formatted deliverable contains the final SSOT. Keep content-transfer and structural evidence alongside reproducible identities. Exact bytes require SHA-256; native cloud documents require provider/resource/revision identity that reopens the reviewed version, and exports record their format, originating revision, and exact-byte digest.
- QA applies to the artifact actually checked. Regeneration requires rebinding and rechecking affected evidence. A byte-identical rename can preserve the same content QA when the path relationship is recorded.

## Portability decisions

Unit counts, page counts, languages, edit counts, and document tools are project inputs. The workflow does not prescribe a fixed directory layout for translation projects.

Source locations use the format's appropriate stable references: page systems for PDFs, version-bound paragraphs or anchors for DOCX, and spine/section/anchor references for EPUB. Reflow documents do not acquire a fictitious fixed page count.

For fixed-layout outputs, required visual QA must cover the whole output. Previously inspected page images may be reused only when exact image identity and current artifact binding are proven; changed pages need fresh inspection. The report must distinguish reused evidence from newly viewed pages.

## Complexity guard

There are five major gates, four severity levels, four finding types, six adjudication dispositions, and five reusable templates. EDITORIAL_ONLY and PRE_FIXED do not authorize new body edits. SOURCE dispositions are separate from revision decisions.

Conditional evidence, such as occurrence maps or ERRATA, can live in clearly identified sections of project reports. Frozen historical records still require separate correction material. This avoids adding a template or formal gate for every possible edge case.

Parallel work is optional and requires clear ownership and a merge responsibility. Shared Bible and SSOT files should not be edited concurrently. A confirmed single occurrence can be handled without an unnecessary full occurrence map when the rationale is recorded.

## Validation boundary and limitations

The candidate has undergone static architecture and scenario review. This is not a claim that an automated toolchain, platform loader, or end-to-end translation deployment has been validated.

The policies rely on the executing agents to maintain honest evidence records. They cannot technically enforce isolated context or immutable storage. Missing extraction, rendering, or verification capabilities must be reported rather than replaced with an unsupported PASS.

Template placeholders are intentional and must be replaced with measured evidence before use. Installation and loader-specific naming compatibility are outside this bootstrap. The skill identifier remains `longform-translation-release`.

## Future Work

Possible work after separate authorization and review:

- Artifact materialization and digest/version checks.
- Finding-to-adjudication-to-change traceability and count reconciliation.
- Authorized edit assertions and PRE/POST diff classification.
- Occurrence-map assistance with human verification.
- Cross-format content transfer and visual coverage records.

These are candidates, not implemented features. Automation scripts, schemas, CI, additional gates, and a workflow engine are intentionally deferred.

## Review focus

Architecture review should examine portability, overfitting, governance burden, executability, STOP behavior, evidence authority, protection against reviewer hallucinations, and blind-replacement prevention. The workflow ends at FINAL RELEASE QA PASS; further editorial or publication work is a separate assignment.
