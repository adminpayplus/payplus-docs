# AGENTS.md

## 1. Purpose and Authority

This file is the PayPlus repository Operating Contract and Routing Layer for AI assistants.

It defines durable repository boundaries, source precedence, concept and document ownership, task routing, approval boundaries, and safe operating rules. It tells an agent which authority, workflow, procedure, framework, guide, and domain owner to use.

This file is not a Documentation Lifecycle and must not define or duplicate lifecycle stages, gates, or procedures. The sole canonical owner of the Documentation Lifecycle is:

`docs/00-foundation/payplus-documentation-development-workflow.md`

All documentation work must be routed through that Documentation Development Workflow. Parallel work and specialist guides extend the canonical workflow only when their triggers apply.

## 2. PayPlus Repository Context and Product Boundary

PayPlus is a controlled bill, fee, rent, and approved-payee payment application.

The product supports eligible real-world bills and approved payment obligations with evidence, payer authorization, payee verification, risk controls, auditability, reconciliation, and operational oversight.

PayPlus must not be casually described, specified, prototyped, or implemented as:

- a wallet or stored-value account;
- an unrestricted peer-to-peer transfer product;
- a cashout or remittance product;
- a lending or cash-advance product;
- an open money-request marketplace.

Any feature that may move PayPlus toward one of these models must be treated as a risk or unresolved decision. An agent must not convert it into accepted scope without the required Founder decision and source-document update through the canonical workflow.

## 3. Source-of-Truth Authority

`docs/00-foundation/doc-00-documentation-governance.md` is the sole owner of the ranked source-of-truth hierarchy. Apply the hierarchy defined in DOC-00 whenever sources conflict; this operating contract does not restate or independently rank those sources.

Operationally:

- use each current formal document for the concept it owns;
- treat Founder Working Baselines according to the status and limited authority assigned by DOC-00;
- use technical, traceability, diagram, prototype, AI-execution, supporting, backup, and chat material only at the authority level assigned by DOC-00;
- do not let a derived or supporting artifact override its formal owner.

An explicit current Founder instruction controls the task scope and authorization boundary. Material product or governance decisions must still be returned to and recorded by the correct formal owner through the canonical workflow.

## 4. Documentation Layers

PayPlus documentation must be developed in this order:

```text
Human source documents
-> technical and operational specifications
-> AI build-execution documents
-> implementation tasks
-> code, tests, migrations, configuration, and release evidence
-> traceability updates
```

Do not reverse this order unless the Founder explicitly authorizes the exception.

- `DOC-00` to `DOC-15` and related domain documents form the active human-readable product and control baseline.
- `DOC-16` to `DOC-22` define technical architecture, integrations, data, security, testing, operations, and admin specifications when drafted.
- Placeholder technical documents do not authorize an agent to infer missing implementation detail.
- AI execution material may be generated only when the human and technical source set is sufficiently accepted for conversion.

## 5. Workflow Routing Matrix

The Documentation Development Workflow is the canonical lifecycle owner for every row below. The other entries are conditional authorities or specialist extensions, not competing workflows.

| Task category or trigger | Canonical owner | Required or conditional specialist reference |
| --- | --- | --- |
| Any documentation review, proposal, drafting, restructuring, alignment, validation, approval request, Git action, records treatment, or completion report | Documentation Development Workflow | `DOC-00` plus the primary owning document |
| Parallel agents, a review swarm, multiple workstreams, or worktrees are explicitly requested | Documentation Development Workflow | Parallel-Agent Documentation Procedure |
| Interactive prototype, route prototype, wireframe, UI proof of concept, prototype review, or prototype-status change | Documentation Development Workflow | Prototype Design and Validation Specialist Guide |
| DOC-07 Outcome, Resolution, Message, disclosure, copy, or CTA authoring | Documentation Development Workflow | DOC-07 Design Specification Specialist Guide plus Outcome Framework |
| Material decision, outcome, recovery/unavailable path, protected continuation, message/CTA relationship, or notification relationship | Owning route/domain document through the Documentation Development Workflow | Platform Design Principles plus Outcome Framework |
| Product route, destination, screen, entry point, return behavior, or route-family structure | Applicable product/UX owner | Route register, transition tables, and governed hierarchical diagrams |
| Bills, rent, tenancy, evidence UI, reminder UI, or bill-specific activity | Applicable DOC-06 family owner, normally DOC-06C | Relevant payment, evidence, privacy, notification, and acceptance owners |
| Payment request, checkout, funding, authorization, or payment instruction | DOC-09 | DOC-06 route owner plus applicable payout, evidence, risk, privacy, notification, and acceptance owners |
| Notification ID, recipient, channel, template, preference, delivery, retry, or notification evidence | DOC-08 | Outcome Framework; DOC-07 only for owned user-facing mapping |
| Evidence, OCR, extraction, bill verification, or payee verification | DOC-12 | Applicable UX, payment, risk, privacy, data, and acceptance owners |
| Promotion, coupon, voucher, referral, membership, or offer logic | DOC-13 | Applicable UX, checkout, accounting, risk, notification, and acceptance owners |
| AML, anti-cashout, fraud, or dynamic risk control | DOC-14 | DOC-03/DOC-04 foundation context plus applicable product, payment, privacy, security, admin, and testing owners |
| Privacy classification, masking, retention, visibility, or approved-purpose access | DOC-15 | The directly affected product/domain owner must also be updated |
| Status, event taxonomy, audit, lineage, reporting, or AI-ready signal | DOC-18 when drafted; current domain owner remains authoritative meanwhile | Status-display matrix and affected UX/notification owners |
| Authentication, token, session, rate limit, access, or security control | DOC-19 when drafted; current security owner remains authoritative meanwhile | Applicable route, privacy, outcome, operations, and testing owners |
| Acceptance, UAT, go-live, monitoring, incident, support, or admin operations | DOC-20, DOC-21, or DOC-22 according to concern | Owning human requirement and relevant traceability |
| Formal-document metadata, status, version, ownership, review, approval, numbering, or source hierarchy | DOC-00 | Formal document owner |
| Conversion into AI coding/execution material | Owning human and technical documents through the Documentation Development Workflow | `docs/09-ai-build-execution/` only after conversion is authorized |

### Routing Rules

- Start every documentation task with the Documentation Development Workflow and the primary owning document.
- Load only the specialist references whose triggers are present.
- The Parallel Procedure controls distribution and consolidation only.
- The Prototype Guide controls prototype-specific methods and checks only.
- The DOC-07 Guide controls DOC-07-specific authoring and checks only.
- Platform Design Principles provide cross-platform design doctrine; they do not own product requirements or lifecycle rules.
- The Outcome Framework provides the Outcome/Resolution/Message/CTA/Notification/Event separation and traceability model; it does not own route rules, approved copy, notification delivery, status taxonomy, or lifecycle rules.
- A specialist finding that changes product meaning must return to the applicable owner through the canonical workflow.
- If routing or ownership remains unclear, stop expansion and identify the likely owner, conflicting sources, and required Founder decision.

## 6. Foundation Document Ownership Matrix

This matrix covers every Markdown document currently located in `docs/00-foundation/`.

| Foundation document | Purpose and responsibility | Owns | MUST NOT own |
| --- | --- | --- | --- |
| `doc-00-documentation-governance.md` | Documentation governance authority | Source hierarchy; document status; metadata; ownership/review/approval model; change control; IDs; templates; traceability governance | Product behavior; domain requirements; specialist authoring methods; Documentation Lifecycle execution |
| `doc-01-project-charter-product-positioning.md` | Product charter, overview, positioning, actors, MVP intent, and high-level boundaries | PayPlus product identity; market problem; target users; MVP framing; prohibited-product positioning | Detailed payment/evidence/risk behavior; technical design; specialist procedures; lifecycle rules |
| `doc-02-business-model-unit-economics.md` | Commercial model, fee principles, costs, unit economics, subsidies, reserves, and viability | Commercial intent and economic assumptions; pricing and viability governance at business level | Detailed transaction implementation; final regulatory conclusions; accounting schemas; lifecycle rules |
| `doc-03-regulatory-psp-acquirer-assessment.md` | Regulatory, PSP, acquirer, partner-model assessment and open professional-review items | Product-model assessment; regulatory boundaries and risks; required external assessment questions | Final legal advice; invented partner approval; detailed product mechanics owned elsewhere; lifecycle rules |
| `doc-04-compliance-certification-roadmap-control-framework.md` | Foundation compliance-control objectives, tiers, categories, and readiness roadmap | Cross-domain compliance-control baseline and launch-readiness control expectations | Detailed domain implementation; final certification claims; technical control design owned elsewhere; lifecycle rules |
| `payplus-platform-design-principles.md` | Durable cross-platform product and system design doctrine | Navigation-context protection; revalidation; explicit resolution; security-first usability; modular capability gating; idempotency; auditability; traceability principles | Documentation governance; lifecycle stages/gates; detailed domain requirements; APIs, schemas, or code architecture |
| `payplus-outcome-message-notification-framework.md` | Cross-frontend/backend result and signal architecture | Separation and traceability of Business Rule, Decision, Outcome, Resolution, Message, CTA, Notification, Event/Audit, and Acceptance | Route/domain business rules; approved DOC-07 copy; DOC-08 delivery policy; DOC-18 status/event schema; lifecycle stages/gates |
| `payplus-documentation-development-workflow.md` | Sole canonical Documentation Development Workflow | Entire Documentation Lifecycle and all lifecycle stages, roles, gates, validation authority, Git/records treatment, and completion rules | Product/domain requirements; specialist prototype methods; DOC-07 content method; parallel execution mechanics |
| `payplus-parallel-agent-documentation-procedure.md` | Optional Parallel-Agent Documentation Procedure | Orchestration; task decomposition; work packets; parallel roles; worktree isolation; consolidation; execution conflicts; parallel review | Lifecycle stages/gates; product decisions; general validation authority; commit/records/push/completion authority |
| `payplus-prototype-design-validation-specialist-guide.md` | Prototype Design and Validation Specialist Guide | Prototype classification/status; planning inputs; build method; interaction matrix; functional, visual, responsive, product, and accessibility checks; artifact handoff evidence | Product source requirements; lifecycle stages/gates; general approval/validation; commit/records/push/completion authority |
| `payplus-doc-07-design-specification-specialist-guide.md` | DOC-07 Design Specification Specialist Guide | DOC-07 slice inputs; mandatory matrix; Outcome/Resolution/Message/CTA authoring; disclosure and risk review; specialist validation and maintenance | Source route/domain rules; notification delivery; status/event schema; lifecycle stages/gates; Git or completion authority |

When a new foundation document is introduced, update this matrix in the same accepted change so its unique responsibility and prohibited ownership remain explicit.

## 7. Durable Product-Thinking Rules

### 7.1 Classify Before Designing

Classify the subject before creating structure. Distinguish at minimum:

- route;
- screen;
- view or filter;
- sheet or modal;
- card or component;
- button or user action;
- persistent status;
- user-facing status label;
- operation outcome;
- resolution strategy;
- backend event or audit signal;
- data object;
- policy rule;
- admin setting;
- notification;
- report or reconciliation artifact.

Do not create a new route, module, status, data object, or document section when the subject is only a view, filter, state, entry point, or contextual action.

### 7.2 Preserve Concept Separation

- A request is not a payment.
- A shortcut is an entry point, not a feature owner.
- A route is not a view, filter, tab, or internal mode.
- A bill or rent record is not evidence.
- Evidence status is not payment readiness.
- A notification is not a status or domain event.
- A user-facing label is not necessarily the system state.
- An outcome is not a persistent status.
- A resolution strategy is not an outcome, message, CTA, route, or status.
- A reminder is not automatically a deferred payment instruction.
- A user action is not a backend event or audit record.

For status-display work, use `docs/traceability/status-display-reference-matrix.md` as the display-alignment reference while preserving the underlying domain owner.

### 7.3 Keep One Primary Owner

Assign one primary owner for each material concept. Reference and handoff documents must link to that owner rather than reproduce its detailed rule.

Common ownership:

- `DOC-06B`: global non-Bills route shells, navigation, entry points, route taxonomy, and route-level UX;
- `DOC-06C`: Bills/rent/tenancy UX, cards, details, evidence entry, reminders, and bill activity;
- `DOC-07`: approved user-facing Outcome/Message/CTA mappings, disclosure, copy, and presentation;
- `DOC-08`: notification identity, recipients, channels, templates, preferences, and delivery;
- `DOC-09`: payment request, checkout, funding, authorization, instructions, and payment states;
- `DOC-10`: payout and reconciliation;
- `DOC-11`: refund, cancellation, dispute, and chargeback;
- `DOC-12`: evidence, OCR/extraction, and verification;
- `DOC-13`: promotions, offers, referrals, and membership logic;
- `DOC-14`: AML, anti-cashout, fraud, and risk controls;
- `DOC-15`: privacy classification, masking, retention, visibility, and approved-purpose access;
- `DOC-18`: future canonical data, status/event, audit, lineage, and reporting specification;
- `DOC-19`: future canonical authentication, session, token, access, rate-limit, and security specification;
- `DOC-20`: detailed testing, UAT, and release evidence;
- `DOC-21`: monitoring, incidents, support, and operational escalation;
- `DOC-22`: admin workflow, configuration, queues, review, and controlled overrides.

Do not infer missing technical detail from placeholder owners.

### 7.4 User and Route Discipline

For user-facing behavior, identify the actor, intent, first view, available action, destination, result, return behavior, hidden or masked information, non-member/unlinked behavior, and failed evidence/verification/risk/privacy/authorization path.

Product destination IDs must describe the product area and remain independent of document numbers.

- Reserve `*-ROOT` for the main screen of an independent product area.
- Use clear child-screen names for subordinate destinations.
- Record ordinary navigation through source/action/destination/return transitions.
- Keep `docs/traceability/route-register.md` as the destination inventory.
- Use hierarchical route diagrams as visual projections, not independent authority.

### 7.5 Simplicity and Layering

Prefer the simplest structure that preserves product control, compliance boundaries, user understanding, and future implementation clarity.

- Treat shared lists with different selection criteria as views or filters unless a materially different screen is required.
- Treat a button that opens another area as an entry point, not a new feature owner.
- Reference another document's owned detail instead of duplicating it.
- Use user-facing language in product documents and implementation terminology in the proper technical layer.
- Mark unresolved details `TBD`, `Open`, or `To be confirmed` with an owner.

## 8. Approval and Authorization Boundaries

- The Founder remains the reserved decision owner for material product, governance, ownership, scope, commit, and push authorization unless explicitly delegated.
- Formal document owners, reviewers, approvers, statuses, and version rules are governed by `DOC-00`.
- The Documentation Development Workflow exclusively defines how approvals and lifecycle gates operate.
- `AGENTS.md`, specialist guides, frameworks, diagrams, prototypes, chat, and AI output cannot independently approve a requirement or Git action.
- Review or analysis requests do not authorize edits.
- Edit authorization does not automatically authorize a commit, push, approval status, or product decision beyond the accepted scope.
- When authority is unclear, preserve completed in-scope work and return the unresolved decision through the canonical workflow.

## 9. Repository Safety and Operating Discipline

Before repository work, verify the current workspace, repository visibility, relevant source documents, `AGENTS.md`, and working-tree state.

- Treat existing modifications and untracked files as user-owned unless proven otherwise.
- Never discard, revert, overwrite, stage, move, or delete unrelated changes.
- Use the exact writable-file scope authorized for the task.
- Read the primary owner and material handoff owners before changing governed content.
- Preserve useful existing content and stable IDs unless the accepted change requires replacement.
- Replace superseded definitions rather than leaving two active meanings.
- Keep broad searches batched and proportionate; repeat them only when scope changes or validation finds an unexpected conflict.
- Route all lifecycle reporting, validation authority, commit/records handling, and completion decisions to the Documentation Development Workflow.
- Do not commit, push, open a pull request, or mark a document Approved without explicit authority.
- Before handing back work, state the files changed, checks performed, material unresolved items, and whether any Git action occurred.

## 10. Writing, Risk, and AI Operating Rules

Write clear, professional, human-readable Markdown with precise payments, fintech, risk, privacy, security, compliance, and operations language.

- Use tables when they materially improve reviewability.
- Use stable IDs where traceability requires them.
- Distinguish product intent from legal or regulatory conclusions.
- Use `requires assessment`, `subject to approval`, or `to be confirmed` for unresolved professional-review matters.
- Do not invent partner capabilities, regulatory approval, legal advice, security constants, technical values, statuses, routes, notifications, admin permissions, or implementation facts.
- Avoid unsupported claims such as `fully compliant` or `bank-grade`.
- Keep evidence, payer authorization, payee verification, anti-cashout, auditability, reconciliation, masking, and retention visible where relevant.
- Preserve exact source IDs and route names in derived documents.
- Keep assumptions and examples visibly separate from accepted requirements.
- Keep open questions visible through downstream technical and AI execution work.
- Require future code and tests to trace back to accepted human and technical sources.

Formal `DOC-XX` metadata and presentation must follow `DOC-00`. YAML is the metadata source of truth; any human-readable Document Control table is its exact presentation mirror.
