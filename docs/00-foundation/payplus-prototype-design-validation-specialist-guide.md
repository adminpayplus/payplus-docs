# PayPlus Prototype Design and Validation Specialist Guide

Last updated: 2026-07-26

## 1. Purpose

This specialist guide defines how PayPlus prototypes are classified, scoped, built, reviewed, tested, represented, maintained, superseded, and retired. It applies to route-flow, interaction, information-architecture, visual-design, responsive, and technical proof-of-concept prototypes.

The PayPlus Documentation Development Workflow in `payplus-documentation-development-workflow.md` is the sole canonical owner of the Documentation Lifecycle, including Proposal, Founder Decision and Approval, Drafting, Integration and Alignment, general Validation gates, Commit, Records Commit, Push, and Completion. This guide extends that lifecycle with prototype-specific inputs, build methods, validation checks, review evidence, and artifact-status rules. It **MUST NOT** redefine, duplicate, weaken, bypass, or independently authorize a lifecycle stage, owner, or gate.

Prototype work must be invoked from a named canonical lifecycle stage and must return its plan, artifact, findings, or validation evidence to a named canonical lifecycle stage. It may also invoke the Parallel-Agent Documentation Procedure where the canonical lifecycle has authorized parallel execution. This guide does not replace product requirements, formal UX ownership, technical specifications, or founder authority.

## 2. Core Principles

1. Source documents define the product; prototypes visualize or test those definitions.
2. A prototype must not silently introduce a product requirement, route, status, role, payment behavior, or data rule.
3. Prototype discoveries that change product behavior return to the primary owning document before the prototype is treated as aligned.
4. Use the simplest technology that demonstrates the approved purpose reliably.
5. Use mock data only. Do not include real customer, payment, identity, credential, token, or partner data.
6. A prototype is not production code and must not be represented as implementation-ready unless separately assessed.

Use this specialist invocation map:

```text
Canonical Stage 5 -> prototype planning method -> return to canonical Stage 6
Canonical Stage 8 -> prototype build method -> return to canonical Stage 9
Canonical Stage 12 -> prototype-specific validation -> return evidence to canonical Stage 13
Prototype discovery requiring a product change -> return to canonical Stage 5 or 6
Accepted source change -> canonical Stages 8 to 11 -> re-invoke prototype build or validation as needed
```

The arrows describe specialist invocation and return, not a separate Documentation Lifecycle.

## 3. Prototype Classification

Before planning or building, classify the artifact:

| Type | Purpose |
| --- | --- |
| Route-flow prototype | Validate entry points, navigation, destinations, handoffs, and return behavior. |
| Interaction prototype | Validate controls, forms, sheets, filters, transitions, and state changes. |
| Information-architecture prototype | Validate screen hierarchy, grouping, labels, and content priority. |
| Visual-design prototype | Validate layout, components, typography, spacing, color, and visual hierarchy. |
| Responsive prototype | Validate supported viewport sizes, orientation, density, and adaptive behavior. |
| Technical proof of concept | Test the feasibility of a proposed interaction, rendering, or integration approach without becoming the product specification. |

A prototype may have more than one type, but the primary purpose and decision boundary must remain clear.

## 4. Prototype Authority and Status

Every prototype must identify:

- primary purpose and classification;
- supporting source documents;
- source Git commit or clearly stated working-tree baseline;
- routes, screens, actors, and scenarios covered;
- accepted decisions represented;
- assumptions and open questions;
- excluded or deferred behavior;
- whether visual treatment is exploratory or designated;
- prototype status and replacement, if any.

Use these statuses:

| Status | Meaning |
| --- | --- |
| Exploratory | Tests an unaccepted idea and must not be treated as a requirement. |
| Review Draft | Ready for founder and reviewer feedback but not yet validated. |
| Validated Reference | Accurately represents accepted behavior within its documented scope and limitations. |
| Superseded | Replaced by an identified newer prototype or accepted design. |
| Retired | No longer maintained or suitable as a current reference. |

Do not label a prototype `Approved`. Product and governance approval belongs to the owning documents and recorded decisions.

Maintain `docs/prototypes/README.md` as the prototype lifecycle register. At most one prototype may be designated as the current review artifact for the same product scope. A prototype cannot become a `Validated Reference` until its README identifies an immutable source commit and records completed validation.

When replacing a prototype:

1. designate the replacement in the registry;
2. move a historically useful predecessor to `docs/prototypes/archive/<prototype-name>-<version>-<YYYY-MM-DD>/`, or delete it when it has no continuing value;
3. mark any retained predecessor `Superseded` or `Retired` and identify its replacement;
4. ensure no archived or retired prototype is described as current in an index or README.

## 5. Roles

Use only the roles justified by prototype complexity.

| Role | Responsibility | Default access |
| --- | --- | --- |
| Founder | Supplies scope or product decisions only through the applicable canonical lifecycle gate. | Decision authority defined by the canonical workflow |
| Prototype Orchestrator | Receives the invocation stage, classifies the prototype, prepares context, assigns roles, controls specialist scope, consolidates findings, and returns control to the canonical lifecycle. | Controlled specialist access |
| Prototype Designer / Builder | Creates the one canonical prototype within the write scope supplied by the canonical lifecycle. | Limited prototype write access |
| Product Consistency Reviewer | Checks PRD, route ownership, PayPlus boundaries, actors, labels, and accepted behavior. | Read-only |
| UX / Accessibility Reviewer | Checks hierarchy, usability, responsive behavior, accessibility, and user comprehension. | Read-only |
| Functional QA Reviewer | Tests controls, navigation, states, failure handling, and broken interactions. | Read-only |
| Documentation Integrator | Receives prototype discoveries through the canonical workflow and performs only the lifecycle work authorized there. | Controlled document access |

Only one builder edits the canonical prototype at a time. Parallel agents may review independently, but must not create competing prototype implementations unless the founder explicitly requests design alternatives.

## 6. Prototype Planning Input Pack

When canonical Stage 5 invokes prototype planning, the Prototype Orchestrator must return a compact but decision-complete specialist input pack containing:

1. **Objective and decision boundary:** what the prototype will test and what it will not decide.
2. **Prototype classification and proposed status:** primary and secondary artifact types.
3. **Source baseline:** required documents, route diagrams, statuses, decision IDs, and source commit or working-tree state.
4. **Actors and scenarios:** payer, payee, landlord, business payee, admin, system, or other permitted roles.
5. **Screen inventory:** each route, screen, sheet, modal, view, and material state to demonstrate.
6. **Interaction inventory:** controls, actions, destinations, return behavior, and expected results.
7. **Required states:** populated, empty, loading where useful, action-required, unavailable, validation, failure, and role-aware states.
8. **Proposed technology:** why static HTML, React, or another approach is proportionate.
9. **Viewport and accessibility scope:** target mobile sizes, desktop behavior if relevant, touch, keyboard, focus, and contrast expectations.
10. **Mock-data and integration boundaries:** simulated PSP, KYC, notification, partner, or backend behavior.
11. **Excluded and deferred details:** final styling, backend logic, external services, or unresolved product decisions.
12. **Review roles and validation plan:** product, UX, accessibility, functional, and responsive checks.
13. **Affected-document forecast:** documents that may need alignment if the prototype reveals a product change.
14. **Decision handoff checklist:** numbered scope and behavior matters, their decision owner, and the canonical stage that must resolve them.

Keep the pack structured and easy to scan. Do not over-compress material behavior, states, interactions, source assumptions, or exclusions. The pack supplies evidence to canonical Stage 6; it is not an independent Proposal or Approval stage.

## 7. Required Source Package

The builder and reviewers must receive a task-specific package containing, as applicable:

- `AGENTS.md` and this specialist guide;
- relevant `DOC-00` and `DOC-05` sections;
- applicable `DOC-06A`, `DOC-06B`, `DOC-06C`, and `DOC-06D` sections;
- current route register, transition tables, and Mermaid route map;
- applicable domain owners such as `DOC-08`, `DOC-09`, `DOC-12`, `DOC-13`, `DOC-15`, `DOC-18`, or `DOC-22`;
- status-display reference matrix;
- accepted canonical decision IDs;
- explicit open questions and visual-design limitations.

Do not build from a route name, screenshot, or chat summary alone when authoritative repository context exists.

## 8. Screen and Interaction Matrix

Before implementation, define the testable prototype contract:

| Destination or state | Actor | User sees | User action | Result or destination | Return behavior |
| --- | --- | --- | --- | --- | --- |
| Example | Payer | Required information and status | Selects a permitted action | Opens the documented destination | Returns to the originating context |

The matrix must identify, where applicable:

- default and populated behavior;
- empty state;
- loading state where useful for comprehension;
- action-required and disabled behavior;
- validation and failure behavior;
- payer/payee or role-aware differences;
- linked and unlinked counterparty behavior;
- non-member counterparty behavior;
- direct entry from notification or deeplink;
- back, close, cancel, and completion behavior.

## 9. Build Rules

### 9.1 Location and Prototype README

Place prototypes under:

```text
docs/prototypes/<prototype-name>/
```

Each maintained prototype must contain a `README.md` stating:

- purpose, classification, and status;
- source documents and source baseline;
- covered routes, actors, scenarios, and states;
- how to open or run it;
- test scenarios for the founder and reviewers;
- known limitations and deferred behavior;
- replacement or superseded artifact where applicable;
- last verification date.

The repository-level prototype registry must also identify:

- the single current review artifact, if any;
- current status;
- immutable source commit for a Validated Reference, or explicit working-tree baseline for a Review Draft;
- replacement/archival relationship;
- archive naming convention.

### 9.2 Technology Selection

- Prefer standalone HTML, CSS, and JavaScript when they can demonstrate the required behavior reliably.
- Use React or another framework when reusable stateful components, complex interaction, routing, or responsive behavior materially benefits from it.
- Reuse an established prototype stack in the repository where suitable.
- Do not add a backend, database, authentication service, or external integration unless the proof-of-concept purpose explicitly requires it.
- Simulate PSP, KYC, notification, AI/OCR, partner, and admin services unless live connectivity is separately approved.

### 9.3 Product and UI Boundaries

- Preserve route, screen, view, sheet, component, and action classifications from `AGENTS.md`.
- Do not promote a tab, filter, card, shortcut, or contextual action into an independent route without an accepted source requirement.
- Preserve PayPlus product boundaries, payer authorization, evidence requirements, role behavior, privacy, risk, and status terminology.
- Clearly mark exploratory visual treatment when final UI design is not defined.
- Use familiar controls and concise user-facing labels rather than internal technical terminology.

### 9.4 Data and Repository Hygiene

Use fictional, obviously non-production data. Do not include real:

- names, phone numbers, email addresses, identity records, tenancy documents, invoices, bank accounts, cards, tokens, credentials, API keys, or transaction references;
- production URLs or partner secrets;
- customer-derived analytics or support records.

Do not commit dependency directories, caches, temporary screenshots, development-server output, local configuration, or secrets. Commit dependency manifests and lockfiles only when the selected prototype technology requires them.

## 10. Founder-Usable Prototype Delivery

Prototype delivery must not require the founder to understand terminal commands.

Provide:

- a working local URL when a server is required, or a directly openable file when static;
- a short scenario checklist describing what to tap and assess;
- clear identification of interactive controls;
- a concise statement of intentionally unimplemented behavior;
- fallback screenshots only where they help review or diagnose access problems.

If a development server is required, the builder starts it and provides the URL. The specialist delivery is not ready for handoff while a required server or prototype-specific check is still running or unavailable.

## 11. Specialist Prototype Validation

When canonical Stage 12 invokes prototype validation, run the following specialist checks as one coordinated pass after the intended source-alignment and prototype edits are ready. Repeat only failed or materially affected checks rather than restarting all specialist checks after every small change.

These checks produce prototype validation evidence for the canonical workflow. They do not independently declare general Validation passed, establish lifecycle Definition of Done, authorize a commit, or mark the documentation task complete.

### 11.1 Functional Validation

Verify:

- every visible interactive control works or is clearly disabled;
- forward navigation, back, close, cancel, and return behavior match the matrix;
- forms, tabs, filters, toggles, sheets, and modals behave consistently;
- route IDs and destinations match the source documents;
- empty, action-required, failure, and role-aware states are reachable where required;
- no dead control appears actionable;
- dynamic content does not cause incoherent layout shifts.

### 11.2 Visual and Responsive Validation

Use browser inspection and screenshots at the agreed viewports. Verify:

- no text, controls, cards, overlays, navigation, or dynamic content overlap;
- text fits and remains readable;
- stable controls do not resize unexpectedly;
- bottom navigation, fixed actions, sheets, and dialogs do not obscure content;
- mobile and relevant desktop layouts remain correctly framed;
- assets, icons, and generated content render as intended;
- empty, error, and action-required states remain visually coherent.

### 11.3 Product and Consistency Validation

Verify:

- the prototype does not invent routes, statuses, actors, permissions, or product behavior;
- request is not represented as payment;
- bill/rent records remain separate from evidence;
- evidence status remains separate from payment readiness;
- shortcuts remain entry points rather than feature owners;
- payer and payee behavior matches the owning documents;
- user-facing labels follow the status-display reference;
- unresolved decisions remain exploratory or visibly open;
- the route diagram and written behavior remain consistent.

### 11.4 Accessibility Validation

At minimum, check:

- readable contrast;
- practical touch targets;
- keyboard operation for web controls where applicable;
- visible focus states;
- semantic controls and understandable labels;
- no essential meaning conveyed only by color;
- reduced-motion behavior where material motion is used.

## 12. Specialist Review Handoff

Return the following prototype evidence to canonical Stage 13:

1. prototype purpose, classification, status, and source baseline;
2. working URL or file link;
3. screens, interactions, scenarios, and states implemented;
4. validation performed and material findings;
5. differences from the current source documents;
6. product decisions discovered or still required;
7. known limitations and intentionally deferred behavior;
8. reviewer disagreements or unresolved risks;
9. founder scenario checklist;
10. any accept, amend, reject, supersede, or retire decision points that must be routed to the applicable canonical decision stage.

Keep the report compact but decision-complete. Do not substitute a screenshot gallery for the interaction and product findings.

## 13. Feedback Classification and Source Alignment

Classify founder and reviewer feedback before editing:

| Feedback type | Treatment |
| --- | --- |
| Prototype correction | Fix the prototype because it fails to represent accepted documentation. |
| Visual preference | Update the prototype if product behavior and ownership do not change. |
| Product requirement change | Return to canonical Stage 5 or 6; the canonical workflow updates the primary owner first. |
| New route, status, role, or behavior | Return to canonical Stage 5 or 6 before implementation. |
| Technical limitation | Record for the technical owner; do not silently weaken product intent. |
| Deferred detail | Keep visible as open or exploratory. |

When feedback changes product behavior, use this invocation and return path:

```text
Prototype specialist finding
-> return to canonical Stage 5 or 6
-> canonical workflow updates the primary owner and performs Alignment
-> canonical workflow re-invokes prototype build support at Stage 8 when needed
-> canonical workflow re-invokes prototype-specific validation at Stage 12
-> return specialist evidence to canonical Stage 13
```

Do not update only the prototype and leave the source documents contradictory.

## 14. Validated Reference Criteria

A prototype may become a `Validated Reference` only when:

- it matches the accepted source documents within its declared scope;
- required interactions and states work;
- functional, visual, responsive, product, and applicable accessibility checks pass;
- known limitations and open questions are documented;
- exploratory choices are not presented as final requirements;
- the applicable canonical decision owner confirms it is suitable as a reference.

These are prototype-status criteria, not a general Validation gate or lifecycle Completion rule. The Prototype Orchestrator returns the evidence and requested status change to the canonical workflow; this guide does not approve the documentation change or Git action.

When a prototype is replaced:

- mark it `Superseded` or `Retired`;
- identify its replacement where applicable;
- remove or revise current-index references;
- preserve it only when it has historical or diagnostic value;
- do not leave several artifacts appearing equally current.

## 15. Canonical Lifecycle Handoff

When returning prototype work to canonical Stage 13, provide this specialist evidence:

1. list prototype source files changed;
2. list source documents changed or confirm that no product requirement changed;
3. classify existing and replacement prototypes;
4. identify any documentation or governed visual-reference impact for canonical Alignment;
5. update Mermaid route diagrams only when navigation changed;
6. verify the prototype `README.md`, source baseline, status, and limitations;
7. complete functional, visual, responsive, product, and accessibility checks;
8. identify files checked but unchanged;
9. exclude caches, dependency directories, temporary exports, and unrelated assets;
10. identify unresolved specialist findings and the canonical stage that must receive them.

The canonical Documentation Development Workflow exclusively determines Alignment, general Validation, Definition of Done, commit readiness, Commit, changelog and decision-log treatment, Records Commit, Push, and Completion.

## 16. Parallel-Agent and Worktree Use

- Use one canonical builder for a normal prototype.
- Use parallel read-only Product, UX / Accessibility, and Functional QA reviewers when complexity justifies them.
- Use separate design alternatives only when the founder explicitly requests comparison.
- Use worktrees only for independent prototypes or disjoint components with defined ownership and integration order.
- Do not allow multiple agents to edit the same prototype concurrently.
- Apply the Parallel-Agent Documentation Procedure in `payplus-parallel-agent-documentation-procedure.md` when the canonical lifecycle authorizes parallel agents or worktrees for a prototype task.

## 17. Reusable Specialist Invocation Prompts

### Prototype Planning Support

```text
Within canonical Documentation Development Workflow Stage 5, invoke the PayPlus
Prototype Design and Validation Specialist Guide for [prototype task]. Return a
compact, decision-complete Prototype Planning Input Pack covering purpose,
classification, sources, routes, screens, interactions, actors, states,
technology, responsive and accessibility scope, exclusions, reviewers, affected
documents, and decision handoffs to canonical Stage 6.
```

### Prototype Build and Specialist Validation

```text
Within canonical Documentation Development Workflow Stage 8, invoke the PayPlus
Prototype Design and Validation Specialist Guide for the accepted prototype
scope [IDs]. Build one canonical prototype using mock data, then return the
artifact to canonical Stage 9. When canonical Stage 12 is reached, re-invoke the
specialist functional, visual, responsive, product, and accessibility checks and
return the evidence to canonical Stage 13. Route material product discoveries
back to canonical Stage 5 or 6.
```
