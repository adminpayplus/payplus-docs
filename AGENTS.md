# AGENTS.md

## Purpose

This file gives AI assistants working in this repository a shared operating guide.

PayPlus documentation must be developed in layers:

1. Human-readable source-of-truth documentation.
2. Technical and operational specifications derived from the human docs.
3. AI-coding-friendly execution documentation derived from the human and technical specs.
4. Implementation code, tests, migrations, configuration, and release evidence.

Do not reverse this order unless the founder explicitly approves it.

## Repository Context

PayPlus is a controlled bill, fee, rent, and approved-payee payment application.

The product is intended to support eligible real-world bills or approved payment obligations, with evidence, payer authorization, payee verification, risk controls, auditability, reconciliation, and operational oversight.

PayPlus must not be casually described or designed as:

- a wallet;
- a stored-value account;
- an unrestricted peer-to-peer transfer app;
- a cashout product;
- a remittance product;
- a lending product;
- a cash advance product;
- an open money-request marketplace.

If any future feature appears to move PayPlus toward one of those models, flag it as a risk or open question instead of treating it as approved scope.

## Source of Truth

Use `docs/00-foundation/doc-00-documentation-governance.md` as the primary documentation governance guide.

When sources conflict, follow the source-of-truth hierarchy in `DOC-00`.

In general:

1. Approved formal `DOC-XX` documents win.
2. Draft formal documents guide discussion but are not final authority.
3. AI build-execution files support implementation but must not override human source documents.
4. Backup files are not authoritative.
5. Chat history is useful context but must not override repository documents.

## Current Documentation Strategy

The intended documentation flow is:

```text
Human source docs -> technical specs -> AI execution docs -> implementation tasks -> code/tests/evidence -> traceability updates
```

Use these repository areas as follows:

- `docs/00-foundation/`: governance, product positioning, business model, regulatory and compliance foundation.
- `docs/01-product/`: product requirements, user journeys, disclosures, notifications, and user-facing behavior.
- `docs/02-payment-domain/`: payment, funding, payout, reconciliation, refund, cancellation, and chargeback behavior.
- `docs/03-bill-verification/`: bill categories, evidence, document AI/OCR, and payee verification.
- `docs/04-growth-ecosystem/`: promotions, coupons, referrals, memberships, and growth features.
- `docs/05-risk-compliance-privacy/`: AML, anti-cashout, fraud, privacy, data classification, masking, approved-purpose access, and retention.
- `docs/06-engineering/`: architecture, APIs, data model, field metadata, lineage, transaction states, and audit events.
- `docs/07-security-access-control/`: security, tokenization, authentication, access control, and admin controls.
- `docs/08-qa-release-operations/`: testing, UAT, go-live, monitoring, incidents, and operations.
- `docs/09-ai-build-execution/`: AI build-execution materials derived from human docs.
- `docs/99-isms-policies/`: ISMS and security policy library.
- `docs/traceability/`: requirements, controls, tests, decisions, and open-question linkage.

## Documentation Layering

Human source documents should remain readable, decisive, and reviewable by the founder and professional advisers. Do not overload foundation, product, payment-domain, risk, compliance, or growth documents with full database schemas, API contracts, implementation tickets, or code-level tasks unless the founder explicitly asks.

Use the layers as follows:

1. `DOC-00` to `DOC-15` and related domain documents define business intent, product rules, payment behavior, compliance boundaries, user journeys, risk boundaries, and human-readable source requirements.
2. `DOC-16` to `DOC-22` define technical architecture, API and partner integration, data model, transaction states, audit events, security, testing, monitoring, and admin operations.
3. `docs/09-ai-build-execution/` contains AI-agent execution materials generated from the human and technical specifications.
4. Code, migrations, tests, and implementation artifacts must trace back to the source documents and technical specs.

When drafting early human docs, include enough structure for later specification work, but leave detailed schema, endpoint, test-case, and implementation-ticket detail to the technical and AI execution layers.

At the current founding-stage baseline, `DOC-00` to `DOC-15` are the active human source baseline and `DOC-16` to `DOC-22` may be planned, placeholder, or partial until drafted. Do not infer missing technical detail from placeholders.

DOC-15 owns the cross-document privacy, data classification, masking, retention, role-based visibility, and approved-purpose access baseline. When DOC-15 affects a product, payment, risk, evidence, promotion, engineering, security, or operations requirement, update the owning document directly instead of only adding a note in DOC-15.

Legacy files under `docs/09-ai-build-execution/context/`, including `project-continuation-context.md`, are non-authoritative unless explicitly refreshed from current formal documents.

## PayPlus Product Drafting Method

When drafting, reviewing, or restructuring any PayPlus document, apply this product-thinking method before proposing structure or edits.

### Concept Classification

Classify the subject before designing it. Be explicit about whether the item is a:

- route;
- screen;
- view or filter;
- sheet or modal;
- card or component;
- button or user action;
- status or user-facing status label;
- backend event or audit signal;
- data object;
- policy rule;
- admin setting;
- notification;
- report or reconciliation artifact.

Do not create a new route, module, status, data object, or document section when the item is only a view, filter, state, entry point, or contextual action.

### Concept Separation

Keep similar concepts separate unless the source documents clearly combine them. In particular:

- a request is not a payment;
- a shortcut is an entry point, not a feature owner;
- a route is not the same as a view, filter, or tab;
- a bill/rent record is not the same as evidence;
- evidence status is not the same as payment readiness, although it may affect readiness;
- a notification is not the same as a status;
- a user-facing label is not always the same as the underlying system state;
- a Pay+ action is not automatically a standalone route;
- a reminder is not automatically a deferred payment instruction;
- a user action is not the same as a backend event or audit record.

When drafting or editing user-facing status labels, activity labels, checkout/result status, receipt or statement wording, notification wording, or admin status display, check `docs/traceability/status-display-reference-matrix.md`. That matrix is the status-display alignment reference; domain documents still own the underlying system status meaning and DOC-18 remains the future canonical status/event taxonomy owner.

### User-First Flow Check

Before recommending a flow or editing a UX/product document, answer the practical user questions:

1. Who is the user: payer, payee, landlord, business payee, admin, or system?
2. What does the user want to do?
3. What does the user see first?
4. What button or action can the user take?
5. Where does the action route?
6. What happens after the action?
7. How can the user return to the prior context?
8. What is hidden, masked, or admin-only?
9. What happens if the counterparty is not a PayPlus user or is not linked?
10. What happens if evidence, verification, risk, payout, privacy, or authorization gates fail?

### Simplicity and Structure Rule

Prefer the simplest structure that preserves product control, compliance boundaries, future implementation clarity, and user understanding.

- If several items render the same list with different selection criteria, treat them as views or filters unless a materially different screen is required.
- If a button only opens another area, treat it as an entry point, not a new feature owner.
- If detailed behavior belongs in another document, reference that owner instead of duplicating the rule.
- If the user experience would be confusing because of internal terminology, use user-facing wording and keep internal terms for technical docs.
- If a future admin, data, API, or operations detail is needed, mark the future owning document instead of overloading the human source document.

### Route and Destination Naming Rule

Product route and destination IDs must describe the product area and remain independent of the document that currently owns them. Do not add `DOC-XX`, `06B`, or another document number to a product destination solely because that document defines it.

- Reserve `*-ROOT` for the main screen of an independent product area, such as `OFFERS-ROOT`, `REWARDS-ROOT`, or `REFERRAL-ROOT`.
- Use a clear child-screen suffix for subordinate destinations, such as `OFFERS-CARD-LIST` or `OFFER-DETAIL`.
- Keep requirement, acceptance, control, and test IDs document-scoped where needed for traceability.
- Record ordinary navigation through a transition table containing source, user action, destination, and return behavior. Do not create a permanent entry-point ID for every button, card, notification, or deeplink.
- Maintain a route register with each destination's parent, type, purpose, owning document, and definition status so undefined intermediate screens remain visible.
- Leave backend event names, analytics events, deeplink contracts, and implementation paths to their technical owning documents; they must map back to the product destinations without renaming them.

### Hierarchical Route-Diagram Rule

Use hierarchical Mermaid maps for route visualization:

- the app-level map stops at primary navigation destinations and direct global entry points;
- each material route family owns its detailed parent/child, handoff, and return map;
- a parent diagram should link to a child route family but must not duplicate that child's full tree;
- trivial leaf screens do not require separate diagrams unless their navigation is material or easy to misunderstand;
- `docs/traceability/route-register.md` remains the canonical destination inventory and definition-status source;
- route diagrams are visual alignment aids and must not introduce destinations or behavior absent from the owning documents;
- when replacing a current map, preserve the prior governed map as a dated, clearly superseded, non-authoritative snapshot and update `docs/diagrams/README.md`.

### PayPlus Boundary Check

Every proposed feature, route, flow, data rule, promotion, notification, or admin control must preserve PayPlus boundaries:

- evidence-backed bill, fee, rent, tenancy, or approved obligation context;
- payer authorization remains central;
- payee-created requests require payer acceptance before payment authorization;
- payer-created payments may proceed without payee acceptance where evidence, verification, risk, payout, compliance, and authorization gates pass;
- optional party linking creates shared visibility or communication, not payment authorization;
- no open money request marketplace;
- no wallet, stored-value, cashout, remittance, lending, cash advance, or unrestricted P2P behavior;
- no automatic user-to-user matching unless later approved with privacy, security, and compliance controls.

### Source Ownership Rule

Assign one primary owner before drafting. Other documents may reference or hand off, but should not redefine the same behavior.

Common ownership baseline:

- `DOC-06B`: navigation, global non-Bills route shells and human-readable route-level UX behavior, entry points, route taxonomy, and dashboard placement;
- `DOC-06C`: Bills/rent/tenancy UX, cards, details, evidence UI entry, reminder UI, bill-specific activity;
- `DOC-08`: notification IDs, channels, templates, preferences, and delivery rules;
- `DOC-09`: payment request mechanics, checkout, funding, authorization, payment instructions, payment states;
- `DOC-10`: payout and reconciliation;
- `DOC-11`: refund, cancellation, dispute, chargeback;
- `DOC-12`: evidence, document AI/OCR, field extraction, verification;
- `DOC-13`: promotions, coupons, vouchers, referrals, membership, offers logic;
- `DOC-14`: AML, anti-cashout, fraud, dynamic risk controls;
- `DOC-15`: privacy, data classification, masking, retention, approved-purpose access;
- `DOC-18`: data model, event taxonomy, audit events, lineage, reporting;
- `DOC-22`: admin operations, dashboard workflow, configurable controls, manual review operations.

If ownership is unclear, identify the likely primary owner and list reference documents before editing.

### Recommended Pre-Edit Output

For any new feature, route, workflow, policy, status model, or cross-document change, provide this summary before editing unless the founder has already approved the exact change:

1. concept classification;
2. recommended structure;
3. why the structure is not over-complicated;
4. primary owning document and reference documents;
5. user-facing flow;
6. affected documents;
7. open questions or `TBC` items.

For route or reusable-flow proposals, use this presentation where applicable:

1. modes or invocation contexts;
2. a screen-sequence table with enough detail to review each screen;
3. product and security rules;
4. status-to-action mapping;
5. failure, interruption, and return behavior;
6. owning and reference documents.

Do not compress an entire multi-screen flow into one table row. Modes and screen states must not be promoted into new routes unless they are independently navigable destinations.

## Agent Workflow Rules

### Parallel-Agent Documentation Workflow

When the founder requests parallel agents, multi-agent drafting, a review swarm, or worktree-based documentation work, read and apply `docs/00-foundation/payplus-parallel-agent-drafting-workflow.md`.

The lead agent in the active task acts as Orchestrator / Integration Lead unless the founder appoints another owner. Do not create worktrees or begin parallel editing until the workflow's classification, ownership, baseline, and approval gates have been satisfied.

### Prototype Design and Validation Workflow

When the founder requests an interactive prototype, route prototype, wireframe implementation, UI proof of concept, or prototype review, read and apply `docs/00-foundation/payplus-prototype-design-validation-workflow.md`.

Treat source documents as authoritative and the prototype as a visual or interaction aid. Do not introduce product behavior through prototype code alone. Return material product discoveries to the primary owning document, validate the prototype at the required functional and visual states, and obtain founder approval before committing it as a current reference.

### Documentation Change Integration and Commit Workflow

For any material documentation change, read and apply `docs/00-foundation/payplus-document-change-integration-workflow.md` after the product decision and edit scope are accepted.

Before editing, prepare one task-level Change Impact Manifest covering the primary owner, superseded wording, potentially affected domain and parent documents, traceability, status/route registers, glossary, diagrams, prototypes, indexes, and deferred technical or AI layers. Use that manifest to perform one coordinated owner-first edit pass. Do not repeatedly rescan the whole repository after every individual file.

The workflow requires the primary owner to be updated first, followed by only necessary alignment of governing documents, product requirements, references, traceability, indexes, `AGENTS.md`, README files, hierarchical route diagrams, and current governed prototypes. When a child or module document changes materially, synchronize its parent overview, family status, route/requirement register, and acceptance coverage where affected. This rule applies to every modular document family, not only DOC-06.

Complete one integrated validation pass and pre-commit report after the coordinated edits. Additional scans are required only when validation reveals a conflict, the scope changes, or a new founder decision is introduced.

After every substantive documentation commit, update `docs/changelog/changelog.md` and `docs/decision-log/decisionlog.md` with the substantive commit identifier and actual delivered scope, then create the immediate records-only follow-up commit required by the workflow. Do not push or report completion before both commits exist. Records-only follow-up commits are exempt from self-referential recording unless they introduce another substantive decision.

Before making broad documentation changes:

1. Check the current workspace path.
2. Check `git status --short --branch`.
3. Review the relevant source documents before editing.
4. Identify whether the requested work is review-only, drafting, rewriting, or AI-execution conversion.
5. Preserve existing useful content.
6. Flag contradictions, missing decisions, and open questions.
7. Ask for founder confirmation before committing changes.
8. Update affected index, README, traceability, and reference files when broad documentation changes alter navigation, ownership, or source-of-truth assumptions.

Do not commit, push, create pull requests, or mark documents as approved unless the founder explicitly asks for that action.

## Writing Standards

Write PayPlus documents in clear, professional, human-readable Markdown.

Prefer:

- precise fintech, payments, compliance, risk, security, and operations language;
- concise paragraphs;
- tables where they improve scanability;
- stable IDs for requirements, risks, controls, decisions, tests, and open questions;
- explicit `TBD`, `Open`, or `To be confirmed` markers where facts are unknown;
- practical launch-readiness and implementation-readiness language.

Avoid:

- unsupported regulatory conclusions;
- invented partner capabilities;
- invented legal advice;
- vague claims such as "fully compliant" or "bank-grade" unless supported by formal review;
- moving unapproved assumptions into requirements;
- treating AI build files as source-of-truth documents.

## Formal Document Expectations

Formal `DOC-XX` files should generally follow `DOC-00` governance and include:

- canonical YAML front matter where the document already uses it or where a new formal document is being created;
- a human-readable `Document Control` table immediately below the H1 title that mirrors the YAML metadata;
- document ID;
- title;
- version;
- status;
- owner;
- reviewers;
- approvers;
- last updated date;
- classification;
- related documents;
- purpose;
- scope;
- requirements, rules, controls, or flows as appropriate;
- open questions;
- acceptance criteria;
- version history.

YAML is the metadata source of truth. The Document Control table is a presentation mirror and must not introduce different values. Whenever metadata changes, update and verify both representations in the same edit. Empty placeholder documents are exempt until formal drafting begins; backup files must not be mechanically reformatted.

When editing an existing document, preserve its established format unless the task is specifically to standardize format.

## Compliance and Risk Caution

PayPlus is a payments-adjacent product with regulatory, card network, PSP/acquirer, AML, privacy, security, fraud, chargeback, and consumer-protection implications.

Agents must:

- distinguish product intent from legal conclusion;
- use "requires assessment", "subject to approval", or "to be confirmed" where decisions are unresolved;
- flag jurisdiction, PSP/acquirer, card network, payout, KYC/KYB, AML, privacy, PCI, and retention questions;
- avoid giving final legal, regulatory, tax, or compliance advice;
- keep evidence, authorization, payee verification, anti-cashout, audit, and reconciliation controls visible in relevant docs.

## Human Docs Before AI Coding Docs

Do not start converting documents into AI-coding-friendly implementation prompts until the founder confirms that the human-readable documentation set is complete enough.

When conversion is approved, AI execution docs must:

- cite or link back to their human source documents;
- preserve product boundaries and prohibited behaviors;
- keep open questions visible;
- separate confirmed requirements from assumptions;
- include test and traceability expectations.

## Recommended Review Output

When asked to review documentation, provide:

1. High-priority issues.
2. Cross-document inconsistencies.
3. Missing documents or empty placeholders.
4. Recommended drafting order.
5. Suggested edits or rewrite scope.
6. Open questions for the founder.

Do not make large rewrites unless the founder asks for direct file edits.

## Git and Change Safety

This repository may contain user edits.

Agents must not discard or revert user changes unless explicitly asked.

Before finishing any edit session, report:

- files changed;
- checks performed;
- material recommendations;
- whether changes were committed.

Commits require explicit founder confirmation.
