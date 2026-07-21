---
change_request_id: CR-DOC-06-MODULARIZATION-ID-ALIGNMENT
title: DOC-06 Modularization and ID Alignment Plan
status: Implemented
authority: Non-authoritative change-planning note
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
created_date: 2026-06-25
last_updated: 2026-07-17
classification: Internal
affected_documents:
  - DOC-00 Documentation Governance
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint (proposed)
  - DOC-06B Navigation, IA & Route Taxonomy (proposed)
  - DOC-06C Bills, Rent & Tenancy UX Module (proposed)
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix (proposed)
  - DOC-08 Notification, Receipt & Communication Specification
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-15 Privacy, Data Protection & Record Retention Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-22 Admin Management Dashboard & Operations Workflow
---

> Historical ID note: the document-scoped `ROUTE-06B-*` and `ROUTE-06C-*` proposal in this implemented planning record is superseded by DOC-00 and the current DOC-06 family rule. Semantic product destination IDs such as `BILLS-PAY`, `OFFERS-ROOT`, and `OFFERS-CARD-LIST` are now stable; document-scoped IDs are retained only where needed for traceability.

# CR-DOC-06-MODULARIZATION-ID-ALIGNMENT - DOC-06 Modularization and ID Alignment Plan

| Document Control | Details |
| --- | --- |
| **Change Request ID** | `CR-DOC-06-MODULARIZATION-ID-ALIGNMENT` |
| **Title** | DOC-06 Modularization and ID Alignment Plan |
| **Status** | Implemented |
| **Authority** | Non-authoritative change-planning note |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Created Date** | `2026-06-25` |
| **Last Updated** | `2026-07-17` |
| **Classification** | Internal |
| **Affected Documents** | DOC-00 Documentation Governance<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint (proposed)<br>DOC-06B Navigation, IA & Route Taxonomy (proposed)<br>DOC-06C Bills, Rent & Tenancy UX Module (proposed)<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix (proposed)<br>DOC-08 Notification, Receipt & Communication Specification<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-22 Admin Management Dashboard & Operations Workflow |

---

## 1. Purpose

This change request records the controlled restructuring of DOC-06 into smaller, linked companion documents.

The purpose is to make PayPlus user journey, UX flow, navigation, route, screen, component, and acceptance documentation easier to manage, review, and later convert into AI build-execution materials.

This change request covers three related changes:

1. splitting DOC-06 into a parent document and DOC-06A to DOC-06D child documents;
2. modularizing UX responsibilities so journeys, navigation, route taxonomy, Bills/rent/tenancy UX, and acceptance/test mapping are clearly separated;
3. introducing stable ID alignment rules for UX requirements, routes, screens, components, actions, states, events, test cases, and open questions.

This change request does not approve implementation work, does not create AI build-execution files, and does not change any previously documented PayPlus product, payment, risk, privacy, compliance, or operational decision.

---

## 2. Current Problem

DOC-06 has grown into a large combined document covering:

- product journey summary;
- payer, payee, admin, and system journeys;
- account journeys;
- dashboard navigation;
- Pay+ action sheet behavior;
- route IA workplan;
- Bills tab IA;
- Bills route IDs;
- bill, rent, tenancy, activity, reminder, and evidence UX details;
- payer-created and payee-created payment flows;
- evidence upload and review;
- clarification, dispute, authorization, status, visibility, permission, notification, receipt, error, exception, and prohibited journey controls;
- UX scope;
- non-functional UX requirements;
- acceptance criteria;
- open questions;
- dependencies;
- decision summary;
- revision history.

The current content is valuable, but the single-document structure creates management and execution risks:

| Risk | Description |
| --- | --- |
| Review burden | Reviewers must process journeys, IA, route behavior, component behavior, and acceptance criteria in one long document. |
| Execution ambiguity | Developers and future AI coding agents may not know whether a section describes a route, screen, tab, sheet, component, flow, action, or system touchpoint. |
| Uneven detail | The Bills route is specified in much more detail than other navigation areas, which is acceptable but should be isolated as a module. |
| ID gaps | Many requirements are prose-based and not yet mapped to stable IDs, routes, actions, states, events, and tests. |
| Traceability friction | Later AI build-execution work will need stable references that survive edits and document splitting. |
| Context overload | A future AI agent may need only route taxonomy, only Bills UX, or only journey rules, but the current file requires loading the whole document. |

---

## 3. Guiding Principles

The split must follow these principles:

| Principle | Rule |
| --- | --- |
| No decision change | The split must preserve existing DOC-06 decisions unless a separate approved change request changes them. |
| Source-of-truth clarity | The parent DOC-06 remains the entry point and source map for the DOC-06 family. |
| Human docs before AI execution | The split creates human-readable formal/source documents, not AI build-execution prompts. |
| Clear ownership | Each child document must have a clear subject boundary and related-doc dependency list. |
| No hidden deletion | Existing useful content must be moved, summarized, or explicitly marked as superseded; it must not disappear silently. |
| No duplication drift | Shared rules should live in one owning document and be referenced from others. |
| Stable IDs before implementation | Buildable requirements should receive stable IDs before AI build-execution conversion. |
| Route clarity | Routes, screens, tabs/views, sheets/modals, components, flows, actions, and system touchpoints must be distinguished. |
| Cross-document traceability | Child docs should link back to DOC-05, DOC-06 parent, and owning downstream docs such as DOC-08, DOC-09, DOC-12, DOC-15, DOC-18, and DOC-22. |
| Gated baseline, not scope reduction | Baseline capabilities may remain broad, provided feature/module enablement remains gated by controls, launch phase, category, payee type, user type, jurisdiction, risk state, and operational readiness. |

---

## 4. Execution Guardrails for Future AI Assistants

Future AI assistants must treat this change request as a restructuring plan only.

When executing this plan, assistants must:

- preserve existing DOC-06 product decisions, scope conclusions, route decisions, prohibited behavior controls, and open questions;
- move, summarize, or cross-reference content without silently deleting useful content;
- not simplify, narrow, reinterpret, or reduce PayPlus scope unless the founder explicitly approves;
- not resolve open questions unless the resolution already appears in an authoritative formal document or the founder explicitly confirms it;
- keep route shorthand IDs such as `BILLS-PAY`, `BILLS-RECEIVE`, `BILLS-ACTIVITY`, `BILLS-EVIDENCE-DETAIL`, and `BILLS-REMINDER-LIST` unless mapping them to stable traceability IDs;
- keep checkout behavior owned by DOC-09 and evidence verification owned by DOC-12;
- keep privacy, masking, approved-purpose access, and retention detail owned by DOC-15;
- keep data objects, event taxonomy, lineage, audit events, and reporting definitions owned by DOC-18;
- keep admin workflow, review queues, overrides, and operational configuration owned by DOC-22;
- report apparent contradictions instead of choosing one side silently;
- update cross-links, open-question references, traceability, and version history when moving content;
- keep the human-readable documentation layer separate from later AI build-execution materials.

---

## 5. Non-Goals

This change request does not authorize:

- deleting existing DOC-06 decisions;
- reducing the PayPlus baseline scope;
- converting human source documents into AI build-execution documents;
- creating implementation tickets;
- changing payment, evidence, privacy, risk, notification, security, or admin behavior;
- treating open questions as answered;
- marking child documents as approved without founder confirmation;
- committing, pushing, or creating pull requests without explicit founder confirmation.

---

## 6. Proposed Document Set

### 6.1 Target Files

| File | Document ID | Proposed Title | Role |
| --- | --- | --- | --- |
| `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md` | DOC-06 | User Journey, UX Flow & Service Blueprint | Parent overview, source map, scope boundaries, prohibited UX controls, split index, dependencies, master decision summary. |
| `docs/01-product/doc-06a-core-user-journeys-service-blueprint.md` | DOC-06A | Core User Journeys & Service Blueprint | Core payer, payee, admin, system, evidence, review, authorization, status, visibility, notification, receipt, failure, exception, and service journey flows. |
| `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md` | DOC-06B | Navigation, IA & Route Taxonomy | Bottom navigation, Home dashboard, Pay+ action sheet, route taxonomy, route/screen/component/action standards, cross-area route registry. |
| `docs/01-product/doc-06c-bills-rent-tenancy-ux-module.md` | DOC-06C | Bills, Rent & Tenancy UX Module | Bills route, To Pay/To Receive, bill/rent cards, detail pages, activity, reminders, evidence UX, linking, role-aware actions. |
| `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md` | DOC-06D | UX Requirements, Acceptance Criteria & Test Matrix | Stable UX requirement IDs, acceptance criteria, route/action/state/event/test linkage, open-question/test readiness mapping. |

### 6.2 DOC-00 Governance Update Required

DOC-00 currently registers formal core documents using `DOC-XX` numbering.

Before or during the DOC-06 split, DOC-00 should be updated to recognize `DOC-06A` to `DOC-06D` as formal child documents under DOC-06, or to define an approved companion-document convention for split formal documents.

Recommended governance wording:

> Formal child documents may use a letter suffix, such as `DOC-06A`, when a core DOC-XX document becomes too large to manage as a single file. Child documents inherit the parent document's source-of-truth tier unless otherwise stated. Child document IDs must not be reused.

This governance update should be limited to document numbering and child-document handling. It should not change product scope.

---

## 7. Proposed Content Mapping

### 7.1 Parent DOC-06

DOC-06 should become a concise parent and navigation document for the DOC-06 family.

Recommended DOC-06 sections:

| New Section | Content |
| --- | --- |
| Purpose | Defines DOC-06 family purpose and confirms this is the UX/journey/service-blueprint source family. |
| Scope and Baseline | Summarizes baseline scope, gated enablement, and out-of-scope prohibited behavior. |
| Product Journey Summary | High-level payer-created and payee-created journey summary only. |
| User Roles | Payer, payee, admin/operations, system. |
| DOC-06 Family Map | Links DOC-06A to DOC-06D and describes ownership boundaries. |
| Cross-Document Ownership Boundaries | Clarifies what DOC-06 owns versus DOC-07, DOC-08, DOC-09, DOC-12, DOC-15, DOC-18, DOC-19, DOC-21, and DOC-22. |
| Prohibited Journey Controls | Keeps wallet, stored-value, cashout, self-cashout, unsupported P2P, remittance, lending, and automatic recurring-payment boundaries visible. |
| Master Decision Summary | Preserves existing DOC-06 decisions and links child decisions. |
| Dependencies | Lists family-level dependencies. |
| Open Questions | Keeps only cross-family DOC-06 questions; child-specific questions move to child docs. |
| Acceptance Criteria | Parent-level criteria: child docs exist, content is preserved, cross-links work, IDs are assigned progressively, no decisions changed. |
| Version History | Records the split. |

### 7.2 DOC-06A Core User Journeys & Service Blueprint

DOC-06A should own the user and service journeys that are not specific to one UI module.

Move or derive from current DOC-06:

| Current DOC-06 Section | DOC-06A Treatment |
| --- | --- |
| 5 Core MVP User Journeys | Move and rename to baseline core user journeys if desired. |
| 6 Common Account Journey | Move. |
| 8 Payee-Created Payment Request Flow | Move. |
| 9 Payer-Created Payment Flow | Move. |
| 10 Shared Bill, Tenancy, Invoice, or Obligation Journey | Move high-level journey; link Bills-specific UX to DOC-06C. |
| 11 Recipient Review Journey | Move. |
| 12 Evidence Upload and Review Journey | Move high-level journey; detailed verification remains DOC-12; Bills evidence UI links to DOC-06C. |
| 13 Clarification and Dispute Journey | Move. |
| 14 Payment Authorization Journey | Move; keep checkout UI ownership boundary to DOC-09. |
| 15 Payment and Payout Status Visibility | Move high-level visibility rules. |
| 16 Linked Records and Matching Journey | Move high-level linking/matching rules. |
| 17 Two-Sided Visibility and Permissions | Move high-level role visibility; detailed field rules remain DOC-15/DOC-18. |
| 18 Request Status UX | Move high-level user-facing request status rules. |
| 19 Admin and Operations Journey | Move touchpoints; detailed admin workflow remains DOC-22. |
| 20 Notification Touchpoints | Move touchpoints; detailed notification rules remain DOC-08. |
| 21 Receipt and History Touchpoints | Move touchpoints; detailed receipt and record rules remain DOC-08/DOC-11/DOC-15/DOC-18. |
| 22 Error, Failure, Cancellation, and Exception Journeys | Move. |

DOC-06A should include service-blueprint tables for important flows:

| Flow | Recommended Columns |
| --- | --- |
| Payer-created payment | User step, frontstage UI, backstage system, risk/compliance touchpoint, status/event, owning doc. |
| Payee-created request | User step, frontstage UI, backstage system, notification touchpoint, status/event, owning doc. |
| Evidence review | User step, OCR/autofill touchpoint, verification outcome, admin/risk path, owning doc. |
| Authorization | User step, required disclosures, auth/security touchpoint, payment handoff, owning doc. |
| Exception/dispute | User/admin step, status effect, notification, evidence/audit need, owning doc. |

### 7.3 DOC-06B Navigation, IA & Route Taxonomy

DOC-06B should own global app IA and route/screen/component definitions.

Move or derive from current DOC-06:

| Current DOC-06 Section | DOC-06B Treatment |
| --- | --- |
| 7.1 Design Intent | Move. |
| 7.2 Bottom Navigation | Move. |
| 7.3 Pay+ Action Sheet | Move. |
| 7.4 Home Dashboard Section Order | Move. |
| 7.5 Header Utilities | Move. |
| 7.6 Shortcut Grid | Move. |
| 7.7 Featured / What's New / Hot Offer Carousel | Move. |
| 7.8 Upcoming Bills / Rent | Move summary; Bills-specific destination rules link to DOC-06C. |
| 7.9 Recent Activity | Move global summary; bill/rent-specific activity rules link to DOC-06C. |
| 7.10 Route IA Workplan and Placeholder Titles | Move and convert into route-area workplan. |
| 24 UX Scope | Move global route/screen taxonomy items; Bills-specific UX scope moves to DOC-06C. |

DOC-06B should define the route taxonomy used by all DOC-06 family documents:

| Type | Definition |
| --- | --- |
| Area | Broad product area, such as Home, Bills, Offers, Me, Requests, Instructions, Receipts, Cards, Support. |
| Route | Navigable destination or deep-link target. |
| Screen | Full-page UI view rendered inside a route. |
| Tab / View | Role-aware, state-aware, or filtered view within a screen. |
| Sheet / Modal | Temporary focused interaction, such as Pay+ action sheet or confirmation modal. |
| Component | Reusable UI unit, such as a card, status badge, action row, or timeline entry. |
| Flow | Ordered multi-step journey that may span routes, screens, sheets, and system touchpoints. |
| Action | User-triggered behavior, such as Pay, Request, Remind Payer, Upload Evidence, Set Reminder. |
| System Touchpoint | Automated validation, notification, audit event, risk routing, status update, OCR/autofill step, or integration handoff. |

DOC-06B should require route registry tables to use this format:

| Column | Requirement |
| --- | --- |
| ID | Stable route, screen, component, or action ID. |
| Type | One of Area, Route, Screen, Tab/View, Sheet/Modal, Component, Flow, Action, or System Touchpoint. |
| Area | Parent product area. |
| Role | Payer, payee, admin, system, or mixed. |
| Opened By | Navigation element, action, notification, deep link, or system state. |
| User Purpose | Why the user is here. |
| Allowed Actions | Actions available from this object. |
| System Touchpoints | Major system actions triggered or displayed. |
| Owning Doc | Formal document owning detailed behavior. |
| Related IDs | Related requirements, states, events, notifications, or tests. |

### 7.4 DOC-06C Bills, Rent & Tenancy UX Module

DOC-06C should own the Bills route and related bill/rent/tenancy UX module.

Move from current DOC-06:

| Current DOC-06 Section | DOC-06C Treatment |
| --- | --- |
| 7.11 Bills Tab IA Working Baseline | Move entire section to DOC-06C. |
| 7.11.1 Route and Subsection IDs | Move and align with DOC-06B taxonomy. |
| 7.11.2 Top-Level Views | Move. |
| 7.11.3 Filters | Move. |
| 7.11.4 Bill / Fee Card | Move. |
| 7.11.5 Bill / Fee Detail Page | Move. |
| 7.11.6 Rent / Tenancy Card | Move. |
| 7.11.7 Rent / Tenancy Detail Page | Move. |
| 7.11.8 Bill / Rent Activity Sub-Route | Move. |
| 7.11.9 Add Bill / Rent Flow | Move. |
| 7.11.10 Evidence Sub-Route | Move. |
| 7.11.11 Reminder Route | Move. |
| 7.11.12 Evidence Structure and UX | Move. |
| 7.11.13 Payer-Created and Payee-Created Logic | Move. |
| 7.11.14 Action-Required UX | Move. |
| 7.11.15 Data and Intelligence Signals | Move; final event taxonomy remains DOC-18. |
| Bills-related open questions | Move from DOC-06 open questions into DOC-06C. |
| Bills-related decisions | Move or summarize in DOC-06C decision summary, with parent DOC-06 retaining master links. |

DOC-06C should preserve these decisions:

- `BILLS-PAY` is payer-oriented and must not expose payee-side request actions as payment actions.
- `BILLS-RECEIVE` is payee-oriented and must not show payer-side `Pay` actions.
- `Pay` from payer-side cards/details opens payment/checkout governed by DOC-09.
- DOC-06C owns the entry point and route handoff only for payment/checkout.
- `Request` and `Remind Payer` are payee-side request-management actions subject to DOC-08 and DOC-22.
- Evidence actions live inside bill/rent detail or evidence sub-flow and do not become generic instant-payment actions.
- QR/upload/manual input are input methods inside approved evidence-backed setup flows, not standalone open-loop payment actions.
- User-to-user linking must be initiated or accepted through an approved flow; automatic user-to-user matching is not allowed as a UX assumption.
- Tenancy evidence usually supports contract/relationship context; invoices/bills usually support obligation/payment-cycle context.
- Full evidence verification logic belongs to DOC-12.
- Final data objects, lineage, event taxonomy, and audit event definitions belong to DOC-18.
- Admin review and operational configuration belong to DOC-22.

### 7.5 DOC-06D UX Requirements, Acceptance Criteria & Test Matrix

DOC-06D should own stable UX requirement IDs and testability mapping for the DOC-06 family.

Move or derive from current DOC-06:

| Current DOC-06 Section | DOC-06D Treatment |
| --- | --- |
| 25 Non-Functional UX Requirements | Move and assign stable IDs. |
| 26 MVP Acceptance Criteria | Move, rename to baseline acceptance criteria if desired, and assign stable IDs/test IDs. |
| Route/screen/component/action buildability | Derive from DOC-06B and DOC-06C. |
| Open questions affecting testability | Link from DOC-06A/B/C and open-question register. |
| Traceability expectations | Align with DOC-00 and requirements traceability matrix. |

DOC-06D should define the mapping pattern:

```text
UXREQ -> ROUTE / SCREEN / COMPONENT -> ACTION -> STATE / EVENT -> TEST
```

Example:

```text
UXREQ-06C-014
Payer-side Bills cards must show Pay only when the record is eligible for payment.

Route: ROUTE-06C-BILLS-PAY
Component: COMP-06C-BILL-CARD
Action: ACT-06C-PAY-001
State dependency: STATE-06A-REQUEST-APPROVED-FOR-PAYMENT
Event dependency: EVT-06C-BILL-PAY-TAPPED
Owning docs: DOC-06C, DOC-09, DOC-12, DOC-14, DOC-15
Test: TC-06D-014
```

---

## 8. Stable ID Standard

### 8.1 ID Families

The DOC-06 family should use the following stable ID patterns:

| Artifact | Pattern | Example |
| --- | --- | --- |
| UX requirement | `UXREQ-06A-001`, `UXREQ-06B-001`, `UXREQ-06C-001`, `UXREQ-06D-001` | `UXREQ-06C-014` |
| Route | `ROUTE-06B-{AREA}` or `ROUTE-06C-{AREA-SUBROUTE}` | `ROUTE-06C-BILLS-PAY` |
| Screen | `SCREEN-06B-{NAME}` or `SCREEN-06C-{NAME}` | `SCREEN-06C-BILL-DETAIL` |
| Tab / View | `VIEW-06B-{NAME}` or `VIEW-06C-{NAME}` | `VIEW-06C-BILLS-RECEIVE` |
| Sheet / Modal | `SHEET-06B-{NAME}` or `SHEET-06C-{NAME}` | `SHEET-06B-PAYPLUS-ACTION` |
| Component | `COMP-06B-{NAME}` or `COMP-06C-{NAME}` | `COMP-06C-RENT-CARD` |
| User action | `ACT-06A-{NAME}-{NNN}`, `ACT-06B-{NAME}-{NNN}`, `ACT-06C-{NAME}-{NNN}` | `ACT-06C-PAY-001` |
| User-facing state | `STATE-06A-{NAME}` or module-specific state where appropriate | `STATE-06A-REQUEST-PENDING-PAYER-REVIEW` |
| Event signal | `EVT-06A-{NAME}`, `EVT-06B-{NAME}`, `EVT-06C-{NAME}` | `EVT-06C-BILL-VIEWED` |
| Open question | `OQ-06A-001`, `OQ-06B-001`, `OQ-06C-001`, `OQ-06D-001` | `OQ-06C-004` |
| Test case | `TC-06D-001` | `TC-06D-014` |

### 8.2 Existing Route ID Compatibility

Existing route IDs such as `BILLS-PAY`, `BILLS-RECEIVE`, `BILLS-ACTIVITY`, `BILLS-ACTIVITY-DETAIL`, `BILLS-EVIDENCE-DETAIL`, `BILLS-EVIDENCE-UPLOAD`, `BILLS-REMINDER-LIST`, and `BILLS-REMINDER-DETAIL` should be preserved as user-facing/product shorthand IDs.

When stable traceability requires a full ID, the shorthand should be mapped as follows:

| Existing ID | Stable ID |
| --- | --- |
| `BILLS-ROOT` | `ROUTE-06C-BILLS-ROOT` |
| `BILLS-PAY` | `ROUTE-06C-BILLS-PAY` |
| `BILLS-RECEIVE` | `ROUTE-06C-BILLS-RECEIVE` |
| `BILLS-ACTIVITY` | `ROUTE-06C-BILLS-ACTIVITY` |
| `BILLS-ACTIVITY-DETAIL` | `ROUTE-06C-BILLS-ACTIVITY-DETAIL` |
| `BILLS-ADD` | `ROUTE-06C-BILLS-ADD` |
| `BILLS-EVIDENCE-DETAIL` | `ROUTE-06C-BILLS-EVIDENCE-DETAIL` |
| `BILLS-EVIDENCE-UPLOAD` | `ROUTE-06C-BILLS-EVIDENCE-UPLOAD` |
| `BILLS-REMINDER-LIST` | `ROUTE-06C-BILLS-REMINDER-LIST` |
| `BILLS-REMINDER-DETAIL` | `ROUTE-06C-BILLS-REMINDER-DETAIL` |

DOC-06B should define whether shorthand IDs remain acceptable in diagrams, UX discussion, and product-facing documentation. DOC-06D should use stable full IDs for traceability.

### 8.3 ID Assignment Rules

| Rule | Requirement |
| --- | --- |
| Do not reuse IDs | Once assigned, an ID must not be reused for a different requirement, route, action, event, or test. |
| Do not silently delete IDs | Deprecated or removed IDs should be marked `Deprecated`, `Removed`, or `Superseded`. |
| Keep prose and IDs together | The ID should appear near the requirement or object it identifies. |
| Assign IDs before AI build conversion | AI build-execution files should cite stable source IDs, not line numbers alone. |
| Prefer source ownership | Requirements should be assigned in the owning child document. |
| Link downstream owners | Requirements should identify owning downstream docs where behavior depends on payment, notification, evidence, privacy, data, security, or admin operations. |
| Keep open questions distinct | Open questions must not become confirmed requirements until resolved in the owning source document. |

---

## 9. Cross-Linking Rules

### 9.1 Parent-to-Child Links

DOC-06 should include a family map:

| Source | Links To | Purpose |
| --- | --- | --- |
| DOC-06 | DOC-06A | Core journey and service blueprint detail. |
| DOC-06 | DOC-06B | Navigation, IA, and route taxonomy. |
| DOC-06 | DOC-06C | Bills, rent, tenancy, reminder, activity, and evidence UX module. |
| DOC-06 | DOC-06D | UX requirements, acceptance criteria, traceability, and test matrix. |

### 9.2 Child-to-Parent Links

Each child document should include:

- a statement that it is a child document under DOC-06;
- a link to DOC-06 parent;
- a local scope boundary;
- a related-documents list;
- a local open questions section;
- a local decision summary;
- a local version history.

### 9.3 Cross-Child Links

Cross-child links should be used where responsibilities meet:

| From | To | Link Reason |
| --- | --- | --- |
| DOC-06A | DOC-06B | Journey steps that enter or depend on navigation routes. |
| DOC-06A | DOC-06C | Journey steps that involve Bills, rent, tenancy, reminder, or evidence UX. |
| DOC-06B | DOC-06C | Global route taxonomy applied to Bills module routes and components. |
| DOC-06B | DOC-06D | Route, screen, component, and action IDs used in requirement/test mapping. |
| DOC-06C | DOC-06D | Bills UX requirements and test scenarios. |
| DOC-06D | DOC-06A/B/C | Source requirement, route, action, state, event, and test references. |

### 9.4 Downstream Owner Links

The DOC-06 family must avoid duplicating detailed behavior owned elsewhere:

| Topic | Owning Document |
| --- | --- |
| User-facing wording, disclosure, authorization copy | DOC-07 |
| Notifications, channels, receipts, delivery logging | DOC-08 |
| Checkout, payment quote, funding, payment instruction, payment states | DOC-09 |
| Payout and reconciliation | DOC-10 |
| Refund, cancellation, reversal, chargeback | DOC-11 |
| Evidence category, OCR, verification, duplicate detection, payee verification | DOC-12 |
| Promotions, coupons, vouchers, rewards, memberships | DOC-13 |
| AML, anti-cashout, fraud, dynamic auth, risk triggers | DOC-14 |
| Privacy, masking, retention, approved-purpose access | DOC-15 |
| Data model, lineage, audit events, event taxonomy, reporting | DOC-18 |
| Security, authentication, tokenization, access control | DOC-19 |
| Testing and go-live | DOC-20 |
| Monitoring, incidents, operations SOPs | DOC-21 |
| Admin dashboard, queues, overrides, configuration, operational workflows | DOC-22 |

---

## 10. Open Question Migration Plan

Current DOC-06 open questions should be redistributed by ownership.

| Current Question Area | Target |
| --- | --- |
| Exact distinction between request, obligation, bill record, payment transaction | DOC-06A and DOC-18 linkage |
| Payee adoption exceptions | DOC-06A |
| Payee-created request admin-review categories | DOC-06A / DOC-14 / DOC-22 |
| Accepted MVP evidence categories | DOC-06A reference; DOC-12 owns detail |
| Rent and tenancy launch controls | DOC-06C / DOC-12 / DOC-14 |
| KYC/KYB screens and handoff | DOC-06A / DOC-19 / DOC-22 |
| Payment methods | DOC-06A reference; DOC-09 owns detail |
| Payout rail setup | DOC-06A reference; DOC-10 owns detail |
| Fee disclosures | DOC-06A reference; DOC-07 / DOC-09 own detail |
| Dispute states and outcomes | DOC-06A / DOC-11 / DOC-22 |
| Refund/reversal journeys | DOC-06A / DOC-11 |
| Notification routing/preferences/channels | DOC-06A/B/C touchpoints; DOC-08 owns detail |
| Admin roles and permissions | DOC-06A touchpoints; DOC-19 / DOC-22 own detail |
| Masking and role display rules | DOC-06D traceability; DOC-15 / DOC-18 own detail |
| Duplicate detection signals | DOC-06A/C touchpoints; DOC-12 / DOC-14 / DOC-18 own detail |
| OCR/autofill UI by evidence category | DOC-06A/C; DOC-12 owns detail |
| Duplicate/reused evidence warning copy | DOC-06A/C; DOC-07 / DOC-12 / DOC-15 own detail |
| Dormant login threshold | DOC-06A; DOC-19 owns detail |
| Payment-instruction labels and partial-funded treatment | DOC-06A/B; DOC-09 owns detail |
| Pay+ visual layout/order/eligibility | DOC-06B |
| Route-level IA for Bills, Offers, Me, More, Requests, Instructions, Receipts, Reminders, Cards, Referral, Support | DOC-06B, with Bills in DOC-06C |
| Dashboard shortcut behavior | DOC-06B |
| Important Notice card rules | DOC-06B |
| Featured carousel rules | DOC-06B / DOC-13 / DOC-22 |
| User-initiated payee linking mechanism | DOC-06A/C / DOC-15 / DOC-18 |
| Bills tab visual layout and card density | DOC-06C |
| Evidence source selection UI | DOC-06C / DOC-12 |
| Request delivery and Remind Payer UX | DOC-06C / DOC-08 / DOC-22 |
| Checkout UI ownership | DOC-06A/B/C references; DOC-09 primary |

Cross-document blockers should remain or be linked in `docs/traceability/open-questions-register.md`.

---

## 11. Implementation Plan for the Documentation Split

This implementation plan is for documentation restructuring only. It is not software implementation.

### Phase 1 - Approve This Change Request

| Step | Action | Output |
| --- | --- | --- |
| 1.1 | Review this change request. | Founder feedback. |
| 1.2 | Confirm target document names and IDs. | Approved split architecture. |
| 1.3 | Confirm ID patterns. | Approved ID convention for DOC-06 family. |
| 1.4 | Confirm whether DOC-00 should be updated to support child document IDs. | Governance update decision. |

### Phase 2 - Prepare Governance and Skeletons

| Step | Action | Output |
| --- | --- | --- |
| 2.1 | Update DOC-00 to recognize letter-suffix child docs or formal companion docs. | DOC-00 minor version update. |
| 2.2 | Create skeleton files for DOC-06A to DOC-06D with YAML front matter. | Empty but governed child docs. |
| 2.3 | Update DOC-06 parent front matter related documents. | DOC-06 points to child docs. |
| 2.4 | Add child documents to each other's related document lists where relevant. | Cross-link baseline. |

### Phase 3 - Move Content Without Changing Decisions

| Step | Action | Output |
| --- | --- | --- |
| 3.1 | Move core journeys into DOC-06A. | DOC-06A populated. |
| 3.2 | Move navigation, dashboard, Pay+, and taxonomy into DOC-06B. | DOC-06B populated. |
| 3.3 | Move Bills/rent/tenancy UX module into DOC-06C. | DOC-06C populated. |
| 3.4 | Move non-functional UX requirements and acceptance criteria into DOC-06D. | DOC-06D populated. |
| 3.5 | Replace moved sections in DOC-06 with summaries and links. | Parent DOC-06 reduced and navigable. |
| 3.6 | Preserve all existing decisions in either parent DOC-06 or child decision summaries. | Decision preservation evidence. |

### Phase 4 - Assign Initial Stable IDs

| Step | Action | Output |
| --- | --- | --- |
| 4.1 | Assign IDs to high-priority DOC-06A journey requirements. | Initial `UXREQ-06A-*` list. |
| 4.2 | Assign IDs to DOC-06B route taxonomy and global navigation requirements. | Initial `UXREQ-06B-*`, `ROUTE-06B-*`, `SHEET-06B-*` list. |
| 4.3 | Assign IDs to DOC-06C Bills route, screen, component, action, and touchpoint requirements. | Initial `UXREQ-06C-*`, `ROUTE-06C-*`, `COMP-06C-*`, `ACT-06C-*` list. |
| 4.4 | Assign IDs to DOC-06D acceptance and test scenarios. | Initial `TC-06D-*` list. |
| 4.5 | Link open questions to relevant requirements where unresolved decisions affect testability. | Open-question traceability. |

### Phase 5 - Update Navigation and Traceability

| Step | Action | Output |
| --- | --- | --- |
| 5.1 | Update `docs/README.md` if it lists product docs. | Navigation updated. |
| 5.2 | Update root `README.md` only if it references DOC-06 directly. | Root navigation updated if needed. |
| 5.3 | Update requirements traceability matrix to reference DOC-06A to DOC-06D. | Traceability updated. |
| 5.4 | Update open-question register if cross-document open questions move or split. | Open-question traceability updated. |
| 5.5 | Update changelog if repository practice requires it for documentation restructuring. | Change evidence. |

### Phase 6 - Verification

| Step | Check | Expected Result |
| --- | --- | --- |
| 6.1 | Search for old section headings. | All moved headings are either in child docs or summarized in parent DOC-06. |
| 6.2 | Search for broken DOC-06 references. | References point to parent DOC-06 or correct child doc. |
| 6.3 | Search for duplicate conflicting decisions. | No parent/child contradiction. |
| 6.4 | Search for route ID consistency. | Existing shorthand IDs map to stable IDs where needed. |
| 6.5 | Review open questions. | No open question lost; each has an owner and status. |
| 6.6 | Review decision summaries. | Existing DOC-06 decisions preserved. |
| 6.7 | Review prohibited behavior controls. | Wallet, stored-value, cashout, self-cashout, unsupported P2P, remittance, lending, and automatic recurring-payment boundaries remain visible. |

---

## 12. Acceptance Criteria

This change request is acceptable when:

- it clearly states that DOC-06 splitting, modularization, and ID alignment are in scope;
- it identifies proposed target files and document IDs;
- it defines what remains in parent DOC-06;
- it maps existing DOC-06 sections to DOC-06A, DOC-06B, DOC-06C, or DOC-06D;
- it preserves existing DOC-06 decisions and does not introduce product-scope changes;
- it defines route, screen, component, action, flow, and system-touchpoint taxonomy;
- it defines stable ID patterns for UX requirements, routes, screens, components, actions, states, events, tests, and open questions;
- it preserves existing shorthand route IDs while introducing stable traceability IDs;
- it defines cross-linking rules between parent, child, and downstream owner documents;
- it defines open-question migration rules;
- it defines a phased documentation implementation plan;
- it defines verification checks for missing content, broken references, duplicated decisions, and lost open questions.

---

## 13. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-CR-DOC06-001 | Should DOC-00 be updated before creating DOC-06A to DOC-06D, or in the same documentation change set? | Product / Documentation Owner | High | Decided: same change set |
| OQ-CR-DOC06-002 | Should child documents use `Founder Working Baseline` immediately, matching current DOC-06, or start as `Draft` until reviewed? | Project Owner | High | Decided: Founder Working Baseline |
| OQ-CR-DOC06-003 | Should the current term `MVP` be preserved in child docs, or progressively replaced with `baseline`, `controlled initial release`, and `gated capability` language? | Product / Founder | Medium | Decided: preserve existing wording during first split |
| OQ-CR-DOC06-004 | Should DOC-06D include all test scenarios immediately, or start with requirement/test mapping placeholders that are expanded before AI build-execution conversion? | Product / QA / Engineering | Medium | Decided: start with skeleton/placeholders |
| OQ-CR-DOC06-005 | Should the first split preserve current section numbering as much as possible for auditability, or renumber child docs cleanly? | Documentation Owner | Medium | Decided: use new child-doc structure while preserving source-section labels where useful |

---

## 14. Decision Summary

| Decision | Status |
| --- | --- |
| DOC-06 should be split because the current single document is too large for efficient management and execution. | Implemented |
| The split should preserve existing product decisions and avoid changing previously concluded PayPlus scope or controls. | Implemented |
| The split should create DOC-06 as a parent and DOC-06A to DOC-06D as formal child documents. | Implemented |
| DOC-06A should own core user journeys and service blueprint flows. | Implemented |
| DOC-06B should own navigation, IA, and route/screen/component taxonomy. | Implemented |
| DOC-06C should own Bills, rent, tenancy, reminders, activity, and evidence UX module details. | Implemented |
| DOC-06D should own stable UX requirement IDs, acceptance criteria, and test matrix. | Implemented |
| Existing route shorthand IDs should be preserved but mapped to stable traceability IDs where needed. | Implemented |
| AI build-execution files should not be generated until the human DOC-06 family is split, reviewed, and stable enough. | Implemented |

---

## 15. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| 0.1.0 | 2026-06-25 | AI Documentation Assistant | Initial proposed change request for DOC-06 splitting, modularization, and ID alignment. |
| 0.1.1 | 2026-06-25 | AI Documentation Assistant | Added execution guardrails and non-goals for future AI handoff safety. |
| 0.2.0 | 2026-06-25 | AI Documentation Assistant | Marked change request implemented after creating DOC-06A to DOC-06D, updating DOC-00 governance, and aligning index/traceability references. |
