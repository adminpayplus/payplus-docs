# PayPlus Parallel-Agent Documentation Workflow

## 1. Purpose

This procedure governs the use of parallel AI agents and Git worktrees for PayPlus documentation work. It supplements `DOC-00` and `AGENTS.md`; it does not replace their source-of-truth, product-drafting, approval, or Git rules. Accepted changes must also pass `payplus-document-change-integration-workflow.md` before commit readiness.

The workflow is intended to improve drafting speed and review quality without creating conflicting requirements, duplicated ownership, or uncontrolled edits.

## 2. Authority and Boundaries

- The founder remains the product decision and approval authority.
- The lead agent in the active task acts as Orchestrator / Integration Lead unless the founder appoints another owner.
- Formal source documents remain authoritative according to `DOC-00`.
- Parallel-agent findings are recommendations until accepted and recorded in the owning document.
- Agents must not silently resolve open product, regulatory, compliance, risk, privacy, payment, or operational decisions.
- Human source documents must be completed to a sufficient baseline before technical specifications and AI execution documents are derived.

## 3. Standard Roles

Use only the roles needed for the task.

| Role | Responsibility | Default access |
| --- | --- | --- |
| Founder | Confirms product decisions, scope, and commit/push approval. | Decision authority |
| Orchestrator / Integration Lead | Classifies the task, assigns roles, controls context and ownership, consolidates findings, manages canonical edits, and reports the result. | Controlled integration access |
| Drafting Agent | Produces a proposal or drafts approved content in the primary owning document. | Read-only during proposal; limited write access after approval |
| Product Reviewer | Checks the charter, PRD, MVP scope, actors, user intent, and PayPlus boundaries. | Read-only |
| Domain Reviewer | Checks the relevant payment, accounting, compliance, risk, privacy, data, UX, security, or operations requirements. | Read-only |
| Consistency Reviewer | Checks ownership, terminology, stable IDs, references, duplication, contradictions, and affected documents. | Read-only |
| Acceptance Reviewer | Checks that accepted behavior is testable and can map to acceptance criteria and traceability. | Read-only |

The Orchestrator must not merely combine agent responses. It must identify agreements, conflicts, unsupported assumptions, and decisions that require founder confirmation.

## 4. Work Classification

Before assigning agents, the Orchestrator must classify the proposed work:

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
11. stopping and approval conditions;
12. downstream alignment or integration dependencies.

The minimum reading package normally includes `AGENTS.md`, relevant `DOC-00` governance, relevant `DOC-05` requirements, the parent `DOC-06` ownership map where UX is involved, the primary owning document, applicable traceability registers, and each material handoff owner.

## 6. Level 1: One Task, Parallel Analysis and Review

Level 1 is the default parallel-agent workflow. It does not require Git worktrees.

### 6.1 Proposal Stage

1. The founder identifies one bounded task.
2. The Orchestrator checks the workspace, Git state, ownership, dependencies, and current source documents.
3. The Orchestrator prepares one common work packet and role-specific instructions.
4. The Drafting Agent, Product Reviewer, relevant Domain Reviewer, and Consistency Reviewer work in parallel as read-only agents.
5. The Orchestrator consolidates their findings into the Founder Review Pack defined below.
6. The founder confirms, rejects, or amends the recommendation.

### 6.2 Founder Review Pack

The Orchestrator's consolidated proposal must be compact but decision-complete. It must provide enough detail for the founder to assess each material proposal without reading separate agent outputs or inferring missing behavior.

Keep the proposal structured, concise, and easy to scan. Do not over-compress material route behavior, business rules, document ownership, reviewer disagreements, affected-document changes, alternatives, or open questions to the point that the founder cannot assess or approve the proposal confidently. Avoid repeating the same conclusion across sections; use tables and numbered proposal IDs where they improve reviewability.

Include, as applicable:

1. **Task and decision boundary:** what is in scope, out of scope, and presented for decision.
2. **Current repository position:** existing definitions, incomplete areas, contradictions, and likely superseded content.
3. **Numbered proposed decisions:** a stable proposal ID, recommended decision, and concise rationale for each material item.
4. **Proposed structure:** routes, screens, views, sections, components, actions, statuses, data objects, or policy rules, clearly classified under `AGENTS.md`.
5. **User-facing behavior:** actor, first view, material information shown, actions, destinations, return behavior, empty state, action-required state, and failure or unavailable behavior.
6. **Material business and system rules:** eligibility, authorization, evidence, limits, status effects, privacy, risk, admin configurability, notification, or operational dependencies required to understand the proposal.
7. **Ownership and handoffs:** one primary owning document for each concept and the documents that reference or consume it.
8. **Exact proposed document changes:** file and section-level change intent, including documents expected to be checked but unchanged.
9. **Replacement and consistency effects:** definitions to replace, references to redirect, concepts that must remain separate, and areas deliberately unchanged.
10. **Reviewer findings:** material agreements, contradictions found, unsupported assumptions, and disagreements that the Orchestrator resolved or returned for founder decision.
11. **Meaningful alternatives considered:** only alternatives that materially affect product structure, ownership, scope, or user behavior, with concise reasons for the recommendation.
12. **Open questions and deferred details:** decisions required now, items that may remain `TBC`, and details deferred to technical, admin, visual-design, or AI execution layers.
13. **Founder approval checklist:** each material proposal ID with a clear accept, amend, reject, or defer decision point.

Do not dump raw agent responses into the Founder Review Pack. Preserve material evidence and disagreement while removing repetition and non-decision commentary.

### 6.3 Canonical Editing Stage

1. One canonical writer edits the primary owning document after founder confirmation.
2. Other agents must not create competing edits to the same formal document.
3. Related documents are edited only where necessary for alignment and only within the approved scope.
4. Shared governance, index, diagram, and traceability files remain under the Orchestrator's control.
5. The Orchestrator applies `payplus-document-change-integration-workflow.md`, including impact search, superseded-definition replacement, shared-file checks, and route visualization where applicable.

### 6.4 Post-Edit Review

Reviewers may check the completed diff in parallel for:

- scope compliance and preservation of unrelated content;
- product and domain alignment;
- PayPlus boundary compliance;
- contradictions, duplication, terminology, route IDs, and references;
- missing affected-document alignment;
- testability and acceptance coverage where applicable.

The Orchestrator reports findings and applies only approved or non-material corrective edits. Material product decisions return to the founder.

### 6.5 Completion Gate

Before any commit, the Orchestrator completes the Documentation Change Integration and Commit Workflow and reports:

1. files changed;
2. exact changes made;
3. checks performed;
4. reviewer findings and their resolution;
5. remaining open questions;
6. cross-document alignment status;
7. commit readiness.

Commit and push actions require explicit founder approval.

## 7. Level 2: Multiple Workstreams and Worktrees

Level 2 is available only when the founder explicitly requests it. The Orchestrator must first propose the workstreams, dependencies, ownership, write scopes, integration order, and review gates. Do not create worktrees merely because several topics are mentioned.

### 7.1 Preconditions

- The starting repository state must be understood and deliberately baselined in a commit.
- Every worktree must start from the same named baseline or approved integration commit.
- Each workstream must have one primary owner and an exclusive writable-file allowlist.
- Shared files must be locked to the Integration Lead.
- Dependencies and merge order must be defined before drafting begins.

### 7.2 Worktree Rules

1. Use one worktree and one primary writer per workstream.
2. Review agents remain read-only and must not create competing patches.
3. Agents commit only allowlisted files on their workstream branch.
4. Agents do not merge, rebase, resolve cross-domain decisions, or update shared registers independently.
5. Workstream branches merge into a dedicated integration branch, not directly into `main`.
6. The Integration Lead merges in dependency order and performs a global consistency review.
7. Only founder-approved integrated changes reach `main`.

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

After branch integration, apply `payplus-document-change-integration-workflow.md` to the combined result before requesting founder commit or merge approval.

## 8. Stop Conditions

An agent must stop and report to the Orchestrator when it encounters:

- conflicting authoritative requirements;
- unclear or overlapping ownership;
- a proposed new route, status, module, data object, or product boundary not already approved;
- an unresolved founder decision;
- a legal, regulatory, compliance, PSP, card-network, payout, privacy, or security conclusion requiring professional assessment;
- overlapping writable files;
- a stale, dirty, or unclear Git baseline that affects the task;
- a dependency that invalidates the assigned work packet.

## 9. Reusable Invocation Prompts

### Level 1 Proposal Only

```text
Apply the PayPlus Level 1 parallel-agent workflow to [task].
Use the necessary drafting and review roles.
Proposal and review only. Return a compact but decision-complete Founder Review
Pack. Do not over-compress material behavior, business rules, ownership,
reviewer disagreements, affected-document changes, alternatives, or open
questions. Do not edit, commit, or push.
```

### Level 1 With Approval-Gated Editing

```text
Apply the PayPlus Level 1 parallel-agent workflow to [task].
First provide a compact but decision-complete Founder Review Pack. Do not
over-compress material behavior, rules, ownership, reviewer findings,
affected-document changes, alternatives, or open questions.
Edit only after my confirmation. Do not commit or push without separate approval.
```

### Level 2 Planning

```text
Apply the PayPlus Level 2 worktree workflow to [drafting wave].
First propose workstreams, dependencies, concept and file ownership,
write scopes, integration order, and review gates. Do not create worktrees yet.
```

## 10. Workflow Review

After the first Level 1 pilot and before activating Level 2, review whether the workflow reduced drafting time, repeated findings, conceptual drift, founder correction, and integration effort. Update this procedure only through an approved governance change.
