# PayPlus Documentation Management Roadmap

## 1. Control and Purpose

| Field | Value |
| --- | --- |
| Coordination surface | `PayPlus Documentation Manager` task |
| Status | Active coordination tracker |
| Last updated | 2026-08-06 |
| Canonical lifecycle | [PayPlus Documentation Development Workflow](../documentation-system/payplus-documentation-development-workflow.md) |
| Governance authority | [DOC-00 Documentation Governance](../00-foundation/doc-00-documentation-governance.md) |
| Repository operating contract | [AGENTS.md](../../AGENTS.md) |

This file is the programme-level coordination and progress tracker for PayPlus documentation work. It records work allocation, current lifecycle stage, dependencies, reports, decision queues, integration readiness, and completion evidence.

It is a supporting traceability artifact. It is not a formal `DOC-XX`, product requirement, source of product truth, lifecycle owner, approval record, or substitute for the canonical documents, registers, changelog, decision log, Git history, or Founder instructions.

## 2. Manager Role and Boundaries

The `PayPlus Documentation Manager` task acts as the continuing coordination surface for the active Documentation Lead and, where applicable, Change Integrator roles assigned by the canonical workflow.

The manager may:

- classify and register bounded documentation work;
- identify the current lifecycle stage and primary owning document;
- issue manager assignments that embed or reference the canonical workflow task contract;
- identify dependencies, handoff owners, writable scope, exclusions, and stop conditions;
- receive and check stage, blocker, decision, validation, Git, and completion reports;
- maintain this roadmap and its queues;
- coordinate Review, Align, Validate, Integrate, Commit preparation, Record, Push, and Completion only through the canonical workflow;
- report consolidated programme progress to the Founder.

The manager must not:

- define, replace, duplicate, weaken, or bypass the PayPlus Documentation Development Workflow;
- treat this roadmap or any conversation as a formal source of product truth;
- approve a material product decision, document status, commit, or push on behalf of the Founder;
- infer approval from task progress, silence, a general instruction, or another task's self-assessment;
- allow an execution task to redefine another document's owned concept;
- mark work integrated, commit-ready, pushed, or complete without the evidence required by the canonical workflow;
- duplicate detailed requirements that belong in formal owning documents;
- overwrite, stage, discard, or absorb unrelated worktree changes.

The Founder retains all reserved decision, scope-acceptance, document-approval, commit-authorization, and push-authorization powers.

## 3. Execution-Task Model

Use one separate execution task for each bounded subject or workstream. Keep related lifecycle work in the same task where practical so its evidence and context remain available. Do not create a separate task merely for every small stage transition.

Each execution task:

- follows the canonical workflow for its assigned stage;
- works only within its issued task contract and authority boundary;
- uses one primary owner for each material concept;
- stops at the stated Founder, review, scope, commit, or push gate;
- returns the stage output required by the canonical workflow whenever its assigned stage ends;
- returns immediately when a blocker, material conflict, scope expansion, or Founder decision is required;
- returns the canonical Stage 20 completion report only after the applicable completion conditions are met.

An execution task's report is evidence for manager review. It does not by itself change the canonical stage, approve a decision, or establish completion.

## 4. Manager Routing and Handoff

The manager routes every work item through the [PayPlus Documentation Development Workflow](../documentation-system/payplus-documentation-development-workflow.md). That workflow supplies the task contract, stage sequence, required outputs, result terms, return stages, approval gates, validation authority, Git treatment, records treatment, push treatment, and completion rules.

The roadmap records the assigned task, current canonical stage, returned workflow output, evidence, queue position, and next action permitted by that workflow. It does not add a stage, gate, verdict, approval, or completion procedure.

Execution tasks must return their workflow-required output unchanged through the available task-handoff mechanism. The manager may attach only the short tracking metadata defined in Sections 10 to 12.

## 5. Work-Item Identification and Tracking

Use coordination IDs in the form `PDM-WI-NNN`. These IDs identify management work items only. They are not document IDs, route IDs, requirement IDs, decision IDs, outcome IDs, event IDs, or implementation identifiers.

Every registered work item should contain:

| Field | Required record |
| --- | --- |
| Work Item ID | Stable `PDM-WI-NNN` coordination identifier |
| Subject | Exact route, domain, document, or bounded documentation concern |
| Primary owner | Canonical owning document |
| Handoff owners | Material dependent or consuming documents |
| Current lifecycle stage | Exact stage from the canonical workflow |
| Coordination status | `Planned`, `Active`, `Waiting for Founder`, `Blocked`, or `Complete` |
| Execution task | Task title or available task reference |
| Authorized scope | Read-only or exact writable-file boundary |
| Dependencies | Prior decisions, documents, reviews, providers, or work items |
| Last stage report | Date and report type |
| Next permitted action | Action allowed after the current gate |
| Git state | No Git authority, commit pending/complete, records pending/complete, push pending/complete |
| Evidence | Document links, validation result, commit identifiers, or push result where applicable |

Coordination status is a management aid only. It must not be used as a document status, route-completion status, domain status, lifecycle outcome, or substitute for a canonical workflow stage.

## 6. Programme Roadmap

| Sequence | Workstream | Current position | Dependency or gate | Next coordination action |
| --- | --- | --- | --- | --- |
| 1 | Documentation governance and workflow | Current operating baseline established; ongoing maintenance only | Founder-approved governance and workflow changes | Apply as authority; do not reopen without evidence and scope |
| 2 | DOC-09 Payment Domain Architecture | Version `1.1.0` is a pushed `Founder Working Baseline` | None for the accepted architecture baseline | Use as the payment-domain authority for downstream UX and technical work |
| 3 | DOC-06 family route and UI/UX definition | Broad human-readable baseline established; selected routes remain partial | Primary-owner and handoff boundaries in DOC-06 and the route register | Continue bounded route work in Founder-prioritized order |
| 4 | `PAYMENT-CHECKOUT` UI/UX | Explore completed; Proposal has not started | Founder instruction to enter Proposal | Prepare a decision-ready Proposal without reopening DOC-09 architecture |
| 5 | Checkout presentation handoffs | Planned after an accepted checkout UX direction | Accepted `PAYMENT-CHECKOUT` Proposal, primary-owner Draft, and Stage 9 Review gate pass | Begin the Stage 10 Change Impact Manifest and determine affected Outcome, notification, promotion, privacy, acceptance, diagram, and technical handoffs |
| 6 | Remaining partially defined destinations | Backlog; priority not assigned | Founder prioritization and owner-specific task contracts | Address as separate bounded work items |
| 7 | DOC-16 to DOC-22 technical and operational specifications | Future drafting programme; placeholders do not authorize inference | Sufficiently accepted human requirements and separate Founder instructions | Draft by domain owner through the canonical workflow |
| 8 | AI build-execution conversion | Deferred | Accepted human and technical source set plus conversion authorization | Generate only after the documentation baseline is sufficiently complete |

## 7. Active Work Register

| Work Item ID | Subject | Primary owner | Current stage | Coordination status | Last stage report | Next permitted action | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `PDM-WI-001` | DOC-09 Payment Domain Architecture baseline | DOC-09 | Stage 20 complete | Complete | Completion and push completed before this tracker was established | Use as canonical payment-domain input | Commits `200bc0e`, `0586c84`, and `883cecd`; version `1.1.0`, `Founder Working Baseline` |
| `PDM-WI-002` | `PAYMENT-CHECKOUT` UI/UX | DOC-06B for route-level UX; DOC-09 for domain architecture | Stage 4 Explore complete | Waiting for Founder | Explore Pack, 2026-08-01 | Stage 5 Proposal only on explicit Founder instruction | `PAYMENT-CHECKOUT` remains `Partially defined`; OQ-XDOC-015 remains open |

## 8. Current Route-Definition Snapshot

The canonical inventory remains the [Route Register](route-register.md). This snapshot is for roadmap prioritization and must be refreshed from that owner rather than edited independently.

| Measure | Current snapshot |
| --- | --- |
| Registered destinations | 74 |
| Defined baseline | 69 |
| Partially defined | 5 |

| Partially defined destination | Primary owner | Roadmap treatment |
| --- | --- | --- |
| `HOME-ROOT` | DOC-06B | Backlog; final route/UI detail remains open |
| `BILLS-LINKING` | DOC-06C | Backlog; unscheduled |
| `SUPPORT-ROOT` | DOC-06B / DOC-21 | Backlog; lower priority unless required by a blocked flow |
| `ABOUT-ROOT` | DOC-06B | Backlog; lower priority |
| `TERMS-ROOT` | DOC-06B / DOC-07 | Backlog; lower priority unless required by compliance or launch acceptance |

## 9. Management Queues

### 9.1 Founder Decision Queue

| Work Item | Decision pack | Blocking effect | Status |
| --- | --- | --- | --- |
| `PDM-WI-002` | No Stage 5 Proposal has been prepared; no decision request is open | Drafting cannot begin | Not opened |

### 9.2 Review and Integration Queue

| Work Item | Reviewed primary draft | Alignment status | Validation status | Commit readiness |
| --- | --- | --- | --- | --- |
| None | - | - | - | - |

### 9.3 Git Queue

| Work Item | Substantive commit | Records commit | Push | Status |
| --- | --- | --- | --- | --- |
| None pending | - | - | - | Empty |

## 10. Manager Assignment Header

The canonical task contract remains defined only by the PayPlus Documentation Development Workflow. The manager may add this tracking header when issuing that contract to a separate execution task:

```text
Work Item ID:
Execution task:
Canonical workflow task contract: attached below / linked
Current canonical stage:
Manager queue:
Roadmap entry:
Return destination: PayPlus Documentation Manager
```

The tracking header does not replace or shorten the canonical task contract and grants no authority by itself.

## 11. Manager Stage-Handoff Summary

The execution task must first return the complete stage output and exact result terminology required by the canonical workflow. The following optional summary may then accompany that output for roadmap updating:

```text
Work Item ID:
Execution task:
Canonical stage output:
Canonical result term, where applicable:
Evidence location:
Manager queue:
Next action stated by the canonical workflow output:
Founder action stated by the canonical workflow output:
```

The summary must copy, not reinterpret, the stage result and return instruction. Where the canonical stage has no verdict term, the summary must not invent one.

## 12. Manager Exception-Handoff Summary

When a canonical workflow output reports a blocker, material decision, failed gate, or return stage, the manager may record only this tracking summary after preserving the full returned output:

```text
Work Item ID:
Execution task:
Canonical returned output:
Affected workstream:
Return stage stated by the canonical workflow output:
Founder action stated by the canonical workflow output:
Unaffected tracked work that may continue:
```

This summary must not diagnose, redesign, or reclassify the issue independently.

## 13. Completion Tracking

Stage 20 completion meaning and reporting remain owned exclusively by the canonical workflow. After receiving and checking the canonical Stage 20 report, the manager may record:

```text
Work Item ID:
Canonical Stage 20 report:
Content completion evidence:
Substantive commit:
Records commit:
Push result:
Final coordination status:
Next tracked work item:
```

This tracking entry cannot establish completion. Content completion, commit completion, records completion, push completion, and programme completion remain separate facts governed by the canonical workflow.

## 14. Roadmap Update Rules

The manager must:

- update a work item only after checking its returned report and available evidence;
- preserve the exact canonical stage and distinguish it from coordination status;
- record the primary owner and dependencies before assigning work;
- keep Founder decisions, open questions, review findings, integration status, and Git status separate;
- link to authoritative documents instead of copying their detailed requirements;
- refresh route counts and route status only from the route register;
- record exact commit identifiers only after the commits exist;
- keep unrelated and pre-existing worktree changes outside every task boundary;
- retain unresolved items with an owner and next return stage;
- preserve the exact workflow-required stage output and result terminology without replacing them with a manager verdict;
- mark a work item `Complete` only when its intended scope has met all applicable canonical completion conditions.

The manager should report programme progress using three views:

1. completed and evidenced work;
2. active or waiting work with its exact stage and gate;
3. planned or blocked work with its dependency and next permitted action.

## 15. Immediate Coordination Position

The next documentation action is not automatically authorized by this roadmap.

For `PDM-WI-002`, the permitted next stage is a read-only `PAYMENT-CHECKOUT` UI/UX Proposal after explicit Founder instruction. The Proposal must preserve DOC-09 Payment Domain architecture and recommend the route-level UX direction, ownership handoffs, affected-document boundary, and remaining Founder decisions without editing files.
