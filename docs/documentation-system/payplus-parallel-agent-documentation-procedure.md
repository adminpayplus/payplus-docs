# PayPlus Parallel-Agent Documentation Procedure

## 1. Purpose

This procedure governs how parallel AI agents and Git worktrees may be used within PayPlus documentation work. It defines parallel-execution mechanics only: orchestration, task decomposition, work packets, role assignment, worktree isolation, consolidation, conflict handling, and parallel review.

The PayPlus Documentation Development Workflow in `payplus-documentation-development-workflow.md` is the sole canonical owner of the Documentation Lifecycle, including Proposal, Founder Decision and Approval, Drafting, Integration and Alignment, Validation, Commit, Records Commit, Push, and Completion. This procedure supplements that lifecycle and **MUST NOT** redefine, duplicate, weaken, bypass, or replace any lifecycle stage, owner, or gate.

Parallel execution may be invoked only from an applicable stage of the canonical lifecycle. When the assigned parallel work is consolidated, this procedure returns control to the canonical lifecycle at the stage named by the Orchestrator. Nothing in this procedure independently authorizes editing, a product decision, document approval, a commit, a records update, a push, or completion.

The procedure is intended to improve analysis speed, specialist coverage, and review quality without creating conflicting requirements, duplicated ownership, or uncontrolled edits.

## 2. Authority and Boundaries

- Founder decision and approval authority remains defined by the canonical Documentation Development Workflow and [`DOC-00`](../00-foundation/doc-00-documentation-governance.md).
- The lead agent in the active task acts as Orchestrator / Integration Lead unless the founder appoints another owner.
- Formal source documents remain authoritative according to `DOC-00`.
- Parallel-agent findings are inputs to the canonical lifecycle, not accepted requirements or lifecycle decisions.
- Agents must not silently resolve open product, regulatory, compliance, risk, privacy, payment, or operational decisions.
- Human source documents must be completed to a sufficient baseline before technical specifications and AI execution documents are derived.
- Lifecycle approval, validation, commit, records, push, and completion rules are not owned by this procedure.

## 3. Standard Roles

Use only the roles needed for the task, subject to the canonical Workflow's mandatory material Stage 5 and Stage 8 responsibility and coverage contract.

| Role | Responsibility | Default access |
| --- | --- | --- |
| Founder | Supplies decisions or authorization only through the applicable canonical lifecycle gate. | Decision authority defined by the canonical workflow |
| Orchestrator / Integration Lead | Receives the invocation stage, decomposes work, implements the Manager-recorded material assignments or assigns proportionate non-material roles, controls context and file ownership, consolidates findings, resolves execution conflicts, and returns control to the canonical lifecycle. | Controlled orchestration access |
| Drafting Agent | Produces the assigned analysis or content contribution within the work packet. | Read-only by default; any write access must come from the canonical lifecycle scope |
| Product Reviewer | Checks the charter, PRD, MVP scope, actors, user intent, and PayPlus boundaries. | Read-only |
| Domain Reviewer | Checks the relevant payment, accounting, compliance, risk, privacy, data, UX, security, or operations requirements. | Read-only |
| Consistency Reviewer | Checks ownership, terminology, stable IDs, references, duplication, contradictions, and affected documents. | Read-only |
| Acceptance Reviewer | Checks that accepted behavior is testable and can map to acceptance criteria and traceability. | Read-only |

The Orchestrator must not merely combine agent responses. It must identify agreements, conflicts, unsupported assumptions, and matters that must return to the applicable canonical lifecycle decision gate.

### 3.1 Adaptive Role Coverage and Temporary Specialist Roles

Before parallel work begins, the coverage owner identified by the canonical Workflow must assess whether the proposed role allocation provides sufficient:

- domain expertise for the approved scope;
- independent review coverage proportionate to materiality and risk;
- primary and handoff document-ownership coverage; and
- integration and consolidation capability.

The standard roles above are responsibility sets, not fixed agent headcount for work outside the canonical Workflow's material Stage 5 and Stage 8 contract. One agent may combine compatible roles when capacity is limited for proportionate non-material work, but the work packet must disclose the combination and its conflict controls. For material work, apply the Workflow's distinct-seat, coverage, continuity, and independence requirements by reference; this procedure records and implements them without redefining their counts or authority. The Founder role and reserved authority must not be assumed by an agent. If required coverage or independence is unavailable, the review remains `Not performed` or `Unresolved` rather than being self-certified.

When the canonical Workflow permits a material coverage exception, the Manager owns and records that decision; the Orchestrator implements only the resulting assignment mechanics. The gap record identifies the uncovered decision, interface, owner, or capability; reassignment assessment; added profile and assigned scope; known limitation; and cost. It must point to any unresolved authority or decision routing in the Workflow rather than resolving it here.

If coverage remains insufficient under the canonical Workflow, the coverage owner must:

1. identify the specific responsibility, ownership, review, or expertise gap;
2. determine whether an existing agent can safely cover it without an incompatible duty or unsupported claim of expertise;
3. when necessary and permitted by the canonical Workflow, recommend or record a task-scoped temporary specialist role for implementation by the Orchestrator;
4. define the temporary role's scope, required inputs, expected output, authority boundary, handoff recipient, and completion condition in the work packet; and
5. report any material gap that cannot be covered.

Examples include Security Reviewer, Compliance Reviewer, UX Reviewer, Backend Architecture Reviewer, Outcome Framework Reviewer, Prototype Reviewer, or another role narrowly defined for the current task. These examples do not create permanent roles or require every task to use them.

A temporary specialist role must not:

- redefine or independently operate the Documentation Lifecycle;
- approve a material Founder decision;
- authorize Commit, Records Commit, Push, or Completion;
- expand the approved task or writable-file scope;
- override a canonical document owner; or
- become a permanent governance role without a separate accepted proposal.

If no suitably capable agent is available, the Orchestrator must:

- complete only the general or non-specialist work that remains supportable;
- mark the affected specialist review or validation `Not performed` or `Unresolved`;
- identify the missing capability, affected scope, risk, and required next owner; and
- return control to the applicable canonical lifecycle gate without claiming full review, validation, readiness, or completion.

Repeated evidence of the same durable capability gap may support a proposal to change the permanent role model. That proposal must proceed through the canonical Documentation Development Workflow and requires Founder approval before this procedure or its standard roles are changed.

### 3.2 Minimum Role-Coverage Record

The work packet or parallel execution plan must record:

| Coverage concern | Assigned role or agent | Independence or combination note | Required output | Gap status |
| --- | --- | --- | --- | --- |
| Domain expertise | Named standard or temporary role | Relevant expertise and any limitation | Domain finding or contribution | Covered / Unresolved |
| Independent review | Named reviewer | Must identify separation from the material author | Review findings | Covered / Not performed |
| Document ownership | Primary writer and handoff reviewers | Writable owner and read-only dependencies | Owned draft or ownership findings | Covered / Unresolved |
| Integration | Orchestrator / Integration Lead | Conflicting duties and controls, if any | Consolidated pack and return-control record | Covered / Unresolved |

For material Stage 5 and Stage 8, extend this record with every selected participant and profile; assigned decisions, owners, sources, and handoffs; every material cross-domain interface and its two distinct Specialist lenses; authority and capability limits; continuity or replacement evidence; and the separately independent Whole-Draft Completeness Reviewer. Use stable task-context pointers instead of repeating the same source narrative.

## 4. Work Classification

Before assigning agents, the Orchestrator must classify the requested work:

| Classification | Treatment |
| --- | --- |
| Independent | May be drafted in parallel when files and concept ownership are disjoint. |
| Related | Analysis and review may run in parallel; canonical drafting remains controlled. |
| Dependent | Draft in dependency order, while non-blocking reviews may run in parallel. |
| Tightly coupled | Keep product decisions and canonical editing serial under one integration lead. |

The following normally remain tightly controlled: request versus payment behavior; route versus view ownership; evidence status versus payment readiness; payment instruction, partial funding, settlement, and payout; system status versus user-facing labels; promotion effects on checkout and accounting; privacy and participant linking; stable IDs; and shared traceability registers.

## 5. Required Work Packet

Before an agent begins, the Orchestrator must provide a task-scoped work packet containing:

1. task and intended outcome;
2. work classification;
3. concept classification under `AGENTS.md`;
4. primary owning document;
5. required reading and reference-only documents;
6. confirmed requirements and PayPlus boundaries;
7. assumptions, examples, and open questions;
8. writable-file allowlist;
9. read-only dependencies and locked shared files;
10. expected output;
11. stopping conditions and the canonical lifecycle gate that controls any decision or write;
12. downstream consolidation dependencies;
13. the canonical lifecycle stage from which the procedure was invoked;
14. the canonical lifecycle stage to which control must return.

The minimum reading package normally includes `AGENTS.md`, relevant `DOC-00` governance, relevant `DOC-05` requirements, the parent `DOC-06` ownership map where UX is involved, the primary owning document, applicable traceability registers, and each material handoff owner.

For material Stage 5, the work packet must also provide one common evidence reference to the Lead and every selected Specialist, the complete decision universe, the profile-specific review assignments, and the Round 1, triggered Round 2, and Lead consolidation return points defined by the canonical Workflow.

For material Stage 8, the work packet must also identify the canonical Writer; the same selected Stage 5 Specialists or the recorded continuity exception and replacement onboarding; each Specialist's complete-Draft lens and assigned deep-source universe; two distinct lenses for every material cross-domain interface; the separately independent Whole-Draft Completeness Reviewer; the writable and broader read-only assessment scopes; and the exact snapshot and stopping conditions.

### 5.1 Task-Context Draft Control Record

For material Stage 8, maintain one logically separable task-context Draft Control Record. It may combine the Draft Plan, Decision Coverage, finding and disposition, correction and closure, Acceptance Criteria and traceability, residual, and final-identity evidence required by the canonical Workflow. It is not a repository artifact, permanent Evidence Pack, new documentation layer, or source of lifecycle authority.

Keep the record compact by using stable IDs and pointers. It must make these obligations separately inspectable:

1. approved decisions and authoritative evidence identity;
2. assessment scope, mutation scope, and Draft representation;
3. selected participants, profiles, independence, limitations, coverage assignments, and material interface lenses;
4. review findings, classifications, owners, dispositions, and the frozen finding-set identity;
5. correction identity, semantic or non-semantic classification evidence, and affected closure;
6. Acceptance Criteria and downstream traceability, owner-backed open or deferred treatment, residuals, dependencies, and qualifications; and
7. baseline, frozen review snapshots, and exact final-artifact identity.

This list defines task-packet mechanics, not a second lifecycle gate or a mandatory file format. The canonical Workflow alone determines whether the obligations are sufficient for Stage 8 exit and later Stage 9 input.

## 6. Level 1: Parallel Analysis and Review for One Canonical Task

Level 1 is the default parallel execution mode. It does not require Git worktrees and does not create a separate lifecycle.

### 6.1 Invocation, Parallel Work, and Return

1. The canonical Documentation Development Workflow identifies a bounded task, current lifecycle stage, applicable decision or write boundary, and required return stage.
2. The Orchestrator checks that the workspace, Git state, ownership, dependencies, sources, and recorded agent scopes are sufficient for parallel execution; for material work, it does not reselect the Manager-recorded participants or coverage.
3. The Orchestrator prepares one common work packet and role-specific instructions from the controlling task contract and recorded assignments.
4. The necessary agents perform disjoint analysis or review in parallel. They remain read-only unless the work packet contains write authority already granted through the canonical lifecycle.
5. The Orchestrator consolidates agreements, conflicts, unsupported assumptions, file impacts, and decision points into the parallel review pack.
6. The Orchestrator returns the consolidated result to the named canonical lifecycle stage. Any material decision, edit authorization, validation conclusion, or Git action occurs only there.

#### 6.1.1 Material Stage 5 Convergence Mechanics

For material Stage 5, distribute one common evidence reference and require the Lead and every selected Specialist to return an independent concise Decision Position before sharing. The Orchestrator then creates one exception ledger from the complete decision universe. Trigger cross-challenge for conflict, high risk, unsupported assertions, owner ambiguity, weak evidence, Founder-reserved decisions, or material omissions; record a concise no-trigger disposition for adequately evidenced rows.

The same selected team receives the exception ledger and may add a supported material omission. Retain accepted and rejected challenge reasons, unresolved assumptions, and material disagreement, but do not require all-to-all debate for no-trigger rows. Only the Lead produces the integrated Proposal. These mechanics supply evidence to the canonical Workflow and do not decide the Founder gate.

### 6.2 Consolidated Parallel Review Pack

The Orchestrator's consolidated pack must be compact but decision-complete. It must provide enough detail for the canonical Documentation Lead and, where the canonical lifecycle requires it, the Founder to assess each material matter without reading separate agent outputs or inferring missing behavior.

Keep the pack structured, concise, and easy to scan. Do not over-compress material route behavior, business rules, document ownership, reviewer disagreements, affected-document changes, alternatives, or open questions. Avoid repeating the same conclusion across sections; use tables and stable item IDs where they improve reviewability.

This pack is a parallel consolidation artifact, not the canonical Proposal, Founder Decision, Approval, Validation, or Completion stage. It supplies evidence and recommendations to the applicable canonical lifecycle stage.

Include, as applicable:

1. **Task and decision boundary:** what is in scope, out of scope, and presented for decision.
2. **Current repository position:** existing definitions, incomplete areas, contradictions, and likely superseded content.
3. **Numbered decision items:** a stable item ID, recommended treatment, and concise rationale for each material item.
4. **Recommended structure:** routes, screens, views, sections, components, actions, statuses, data objects, or policy rules, clearly classified under `AGENTS.md`.
5. **User-facing behavior:** actor, first view, material information shown, actions, destinations, return behavior, empty state, action-required state, and failure or unavailable behavior.
6. **Material business and system rules:** eligibility, authorization, evidence, limits, status effects, privacy, risk, admin configurability, notification, or operational dependencies required to understand the matter.
7. **Ownership and handoffs:** one primary owning document for each concept and the documents that reference or consume it.
8. **Exact recommended document changes:** file and section-level change intent, including documents expected to be checked but unchanged.
9. **Replacement and consistency effects:** definitions to replace, references to redirect, concepts that must remain separate, and areas deliberately unchanged.
10. **Reviewer findings:** material agreements, contradictions found, unsupported assumptions, and disagreements that the Orchestrator resolved as execution matters or returned to the canonical lifecycle.
11. **Meaningful alternatives considered:** only alternatives that materially affect product structure, ownership, scope, or user behavior, with concise reasons for the recommendation.
12. **Open questions and deferred details:** decisions required now, items that may remain `TBC`, and details deferred to technical, admin, visual-design, or AI execution layers.
13. **Decision handoff checklist:** each material item that requires a canonical lifecycle decision, with the decision owner and required return stage identified.

For a route or reusable-flow review, present each material flow as: modes or invocation contexts; a screen-sequence table with reviewable screen detail; rules; status/action mapping; failure and return behavior; and owning/reference documents. Do not compress a multi-screen flow into one row or create route IDs for internal modes and screen states.

Do not dump raw agent responses into the consolidated pack. Preserve material evidence and disagreement while removing repetition and non-decision commentary.

For material Stage 5, retain the independent Decision Positions by stable pointer and consolidate only the decision universe, triggered challenges, no-trigger dispositions, accepted and rejected reasons, assumptions, disagreements, and Lead synthesis needed by the canonical Workflow. Do not create a separate Proposal Challenger or competing full Proposal narratives.

#### 6.2.1 Optional Decision-Complete Behavior Pattern

Use the following pattern where material route, screen, state, exception, or failure behavior would become ambiguous if reduced to topic-only bullets. It is a drafting aid, not a mandatory format for every task. Simple policy decisions, narrow wording changes, metadata updates, reference corrections, or other work that remains clear without this structure should use the shortest suitable presentation.

When applicable, describe enough behavior for a professional reviewer or later AI agent to understand the decision without relying on chat history. Cover:

1. what the situation or screen means;
2. what the user sees;
3. what actions are available;
4. where each action leads;
5. what materially changes in the system;
6. what must remain unchanged;
7. cancellation, interruption, failure, and return behavior;
8. the primary owning document and relevant handoff documents.

A compact table may be used:

| Situation / screen | Meaning | User-facing behavior | Actions and destination | System effect / boundary |
| --- | --- | --- | --- | --- |
| Material case | Concise domain meaning | Information and state presented to the user | Available actions, destinations, and return behavior | Material state effect, preserved boundary, or owning-document handoff |

Do not move exact technical values, schemas, event payloads, security constants, approved message copy, or admin procedures into a human-readable product document when another document owns them. Mark the detail `TBC` or deferred, name the owner, and include enough local context to keep the current document understandable.

Before using this pattern in a consolidated pack or assigned content contribution, check that:

- no confirmed decision has been reduced to an ambiguous summary;
- no material screen, exception, action, destination, or return rule is missing;
- user-facing outcomes remain separate from backend states, events, and notifications;
- concepts with separate ownership remain distinct;
- each decision has one source of truth and reference documents do not redefine it.

The Orchestrator decides whether this pattern materially improves the task. Do not apply it mechanically, repeat the same behavior across documents, or expand a simple change merely to satisfy the table structure.

### 6.3 Parallel Contribution During Canonical Drafting

This procedure does not create or approve a Drafting stage. When the canonical Documentation Development Workflow invokes parallel support during its Drafting stage:

1. One canonical Writer controls the primary owning document and produces one complete Draft; no Specialist produces a competing Draft.
2. Every selected material Specialist receives the complete frozen Draft and complete diff and inspects them through the assigned professional lens.
3. Deep source reading is allocated by accepted decisions, owners, handoffs, and interfaces rather than duplicated universally; every material cross-domain interface has two distinct named Specialist lenses.
4. Specialists remain read-only, verify faithful expression of accepted meaning, record concise findings and limitations, and do not reopen Proposal alternatives.
5. Any other contributing agent stays within an exclusive writable-file allowlist or returns a read-only recommendation.
6. Shared governance, index, diagram, traceability, decision, and record files remain locked to the designated canonical Writer or Change Integrator.
7. The Orchestrator consolidates contributions and returns the result to the canonical Workflow for the applicable Stage 8 exit determination. This procedure does not advance the work to Stage 9 or Alignment.

### 6.4 Parallel Review Service

When the canonical lifecycle requests parallel review, reviewers may check the assigned draft or diff for:

- scope compliance and preservation of unrelated content;
- product and domain alignment;
- PayPlus boundary compliance;
- contradictions, duplication, terminology, route IDs, and references;
- missing affected-document alignment;
- testability and acceptance coverage where applicable.

For material Stage 8, use these mechanics:

1. Freeze the first-review Draft, complete diff, Draft Control Record, and common evidence identity before review begins.
2. Every Specialist completes the entire assigned review universe before requesting correction. Keep preliminary findings internal.
3. Consolidate, deduplicate, classify, and owner-assign all Specialist findings, then freeze one Specialist Correction Pack.
4. The Writer groups shared root causes and applies one accepted-scope correction batch wherever practical, then freezes the corrected snapshot.
5. Route semantic or governance corrections to affected Specialists for closure. If normalization is claimed as non-semantic, record logical-text equivalence and scope and diff evidence; otherwise treat it as semantic. Supported non-semantic Specialist reinspection may be `N/A`.
6. Give the independent Whole-Draft Completeness Reviewer the integrated Draft and complete diff, Draft Control Record, frozen Specialist findings, Writer dispositions, semantic and non-semantic inventories, closure evidence, residuals, and current artifact identity. The Reviewer completes the whole assigned universe before issuing one consolidated pack.
7. When Reviewer findings exist, the Writer applies one correction batch and affected Specialists close changed meaning. Whether or not findings exist, the Reviewer inspects the actual final bytes.

A new post-freeze finding is allowed only for a correction-introduced regression, a previously hidden contradiction that could not reasonably have been identified before the frozen pack, or an objective blocker. Record it as one bounded delta; restart affected closure; do not reopen unrelated review or create a drip-feed loop.

If the review input is wrong, incomplete, inaccessible, outside scope, or otherwise unsafe, impossible, or evidentially invalid to continue, record the blocker and unfinished universe instead of issuing a partial Correction Pack. Correct the input, freeze a valid snapshot, and restart affected initial review. Severity alone does not authorize interruption or piecemeal correction.

The Orchestrator records each finding's routing classification and any affected Specialist challenge under the categories and decision roles owned by the canonical Workflow, then returns unresolved classification to that Workflow. This procedure does not restate or decide the substantive routing boundary.

The Orchestrator returns the completed review and closure evidence to the canonical Workflow. This procedure does not issue a Stage 8 or Stage 9 result, declare validation passed, authorize any later lifecycle action, or claim the documentation complete.

### 6.5 Prospective Material-Task Supplement Mechanics

When the canonical Workflow permits a bounded pre-Stage-9 compliance supplement for an in-flight material Draft, append task-context evidence only for the accepted scope. Identify the exact Draft snapshot, controls actually performed, selected participants and replacements, evidence unavailable from earlier work, remaining material gaps, and the current return point. Do not reconstruct historical independence or coverage, expand writable scope, restart unrelated work, or treat the supplement as a permanent artifact. Return the supplement to the canonical Workflow for its Stage 8 determination.

### 6.6 Return-Control Contract

Every Level 1 invocation must end with a return-control record containing:

1. the lifecycle stage from which Level 1 was invoked;
2. parallel roles used and work completed;
3. consolidated findings or contributions;
4. execution conflicts resolved by the Orchestrator;
5. material conflicts or decisions not resolved;
6. files touched, or confirmation that all work was read-only;
7. the canonical lifecycle stage receiving control;
8. any gate that remains unsatisfied.

The Orchestrator must not represent this return as lifecycle approval, validation, commit readiness, completion, or authorization. Those determinations belong only to the canonical Documentation Development Workflow.

## 7. Level 2: Multiple Workstreams and Worktrees

Level 2 is available only when the canonical Documentation Development Workflow has recorded explicit Founder authorization for worktree-based execution. The Orchestrator then defines workstreams, dependencies, ownership, write scopes, consolidation order, and return points. Do not create worktrees merely because several topics are mentioned.

### 7.1 Preconditions

- The starting repository state must be understood and identified by one immutable baseline commit.
- Every worktree must start from that same named baseline or another baseline explicitly supplied by the canonical lifecycle.
- Each workstream must have one primary owner and an exclusive writable-file allowlist.
- Shared files must be locked to the Integration Lead.
- Dependencies and merge order must be defined before drafting begins.

### 7.2 Worktree Rules

1. Use one worktree and one primary writer per workstream.
2. Review agents remain read-only and must not create competing patches.
3. Agents change only allowlisted files. This procedure does not authorize a workstream commit; any Git authorization must come from the canonical lifecycle.
4. Agents do not merge, rebase, resolve cross-domain decisions, or update shared registers independently.
5. When branch integration is authorized through the canonical lifecycle, workstream branches consolidate through the designated integration branch rather than directly into `main`.
6. The Integration Lead merges in dependency order and performs a global consistency review.
7. The Integration Lead returns the consolidated branch state to the canonical lifecycle; this procedure does not authorize movement to `main`.

### 7.3 Shared Files

Unless a work packet explicitly states otherwise, only the Integration Lead edits shared governance and consolidation files, including:

- `DOC-00`;
- `DOC-05`;
- parent `DOC-06`;
- `docs/README.md`;
- traceability and open-question registers;
- status-display references;
- route diagrams;
- glossary, decision log, and changelog;
- cross-domain AI execution or external handoff documents.

Workstream agents must report required shared-file alignment rather than editing those files.

### 7.4 Cross-Worktree Alignment

Worktrees prevent filesystem collisions but do not prevent logical conflicts. The Integration Lead must therefore:

1. enforce one primary owner per concept;
2. define the inputs consumed and outputs supplied by each workstream;
3. prevent reference documents from redefining another owner's rules;
4. merge the most authoritative behavior owner first;
5. recheck later branches against decisions introduced by earlier merges;
6. run contradiction, duplication, terminology, status, route, privacy, and traceability reviews after integration.

After authorized branch consolidation, return the combined result to the canonical Documentation Development Workflow at the Change Impact Manifest and Integration stages. Lifecycle Alignment, Validation, Commit, Records Commit, Push, and Completion remain outside this procedure.

## 8. Stop Conditions

An agent must stop and report to the Orchestrator when it encounters:

- conflicting authoritative requirements;
- unclear or overlapping ownership;
- a new route, status, module, data object, or product boundary not already accepted through the canonical lifecycle;
- an unresolved founder decision;
- a legal, regulatory, compliance, PSP, card-network, payout, privacy, or security conclusion requiring professional assessment;
- overlapping writable files;
- a stale, dirty, or unclear Git baseline that affects the task;
- a dependency that invalidates the assigned work packet.

## 9. Reusable Procedure Invocation Prompts

### Level 1 Parallel Analysis

```text
Within the PayPlus Documentation Development Workflow, invoke the Level 1
Parallel-Agent Documentation Procedure for [bounded task] during canonical
Stage [stage]. Use only the necessary analysis and review roles. Return one
consolidated, decision-complete pack to canonical Stage [return stage].
Do not make lifecycle decisions or perform actions outside the supplied scope.
```

### Level 1 Parallel Drafting Support

```text
Within canonical Documentation Development Workflow Stage 8, invoke the
Level 1 Parallel-Agent Documentation Procedure for [bounded contribution].
Use one canonical Writer, exclusive file scopes, the selected read-only
Specialists, and the separate independent Whole-Draft Completeness Reviewer.
Consolidate the result and return control to the canonical Workflow for its
Stage 8 exit determination. This procedure does not issue a Stage 8 or Stage 9
result or authorize any later lifecycle gate or Git action.
```

### Level 2 Worktree Execution Planning

```text
Within canonical Documentation Development Workflow Stage [stage], plan a
Level 2 parallel worktree execution for [drafting wave]. Define workstreams,
dependencies, concept and file ownership, write scopes, locked shared files,
consolidation order, conflict handling, and the canonical return stage.
Do not create worktrees until the canonical lifecycle records authorization.
```

## 10. Procedure Review

After the first Level 1 pilot and before activating Level 2, review whether the procedure reduced drafting time, repeated findings, conceptual drift, founder correction, and consolidation effort without competing with the canonical lifecycle. Update this procedure only through the canonical Documentation Development Workflow.
