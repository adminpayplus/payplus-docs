# PayPlus Prototype Design and Validation Workflow

Last updated: 2026-07-26

## 1. Purpose

This procedure governs how PayPlus prototypes are proposed, built, reviewed, validated, aligned, and retired. It applies to route-flow, interaction, information-architecture, visual-design, responsive, and technical proof-of-concept prototypes.

It supplements `DOC-00`, `AGENTS.md`, `payplus-parallel-agent-drafting-workflow.md`, and `payplus-document-change-integration-workflow.md`. It does not replace product requirements, formal UX ownership, technical specifications, or founder approval.

## 2. Core Principles

1. Source documents define the product; prototypes visualize or test those definitions.
2. A prototype must not silently introduce a product requirement, route, status, role, payment behavior, or data rule.
3. Prototype discoveries that change product behavior return to the primary owning document before the prototype is treated as aligned.
4. Use the simplest technology that demonstrates the approved purpose reliably.
5. Use mock data only. Do not include real customer, payment, identity, credential, token, or partner data.
6. A prototype is not production code and must not be represented as implementation-ready unless separately assessed.

The normal lifecycle is:

```text
Source documents
-> prototype plan
-> founder scope confirmation
-> canonical prototype build
-> functional and visual validation
-> founder review
-> accepted discoveries return to source documents
-> prototype alignment and revalidation
-> documentation integration workflow
-> commit and lifecycle recording
```

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
| Founder | Confirms scope, reviews the prototype, decides product changes, and approves commits. | Decision authority |
| Prototype Orchestrator | Classifies the prototype, prepares context, assigns roles, controls scope, consolidates findings, and manages integration. | Controlled integration access |
| Prototype Designer / Builder | Creates the one canonical prototype from the confirmed plan. | Limited prototype write access |
| Product Consistency Reviewer | Checks PRD, route ownership, PayPlus boundaries, actors, labels, and accepted behavior. | Read-only |
| UX / Accessibility Reviewer | Checks hierarchy, usability, responsive behavior, accessibility, and user comprehension. | Read-only |
| Functional QA Reviewer | Tests controls, navigation, states, failure handling, and broken interactions. | Read-only |
| Documentation Integrator | Returns accepted product discoveries to the owning documents and applies the integration workflow. | Controlled document access |

Only one builder edits the canonical prototype at a time. Parallel agents may review independently, but must not create competing prototype implementations unless the founder explicitly requests design alternatives.

## 6. Prototype Review Pack

Before building, the Prototype Orchestrator must provide a compact but decision-complete review pack containing:

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
14. **Founder approval checklist:** numbered scope and behavior decisions with accept, amend, reject, or defer options.

Keep the review pack structured and easy to scan. Do not over-compress material behavior, states, interactions, source assumptions, or exclusions to the point that the founder cannot assess the plan confidently.

## 7. Required Source Package

The builder and reviewers must receive a task-specific package containing, as applicable:

- `AGENTS.md` and this workflow;
- relevant `DOC-00` and `DOC-05` sections;
- applicable `DOC-06A`, `DOC-06B`, `DOC-06C`, and `DOC-06D` sections;
- current route register, transition tables, and Mermaid route map;
- applicable domain owners such as `DOC-08`, `DOC-09`, `DOC-12`, `DOC-13`, `DOC-15`, `DOC-18`, or `DOC-22`;
- status-display reference matrix;
- accepted proposal or decision IDs;
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

## 10. Founder-Usable Delivery

Prototype delivery must not require the founder to understand terminal commands.

Provide:

- a working local URL when a server is required, or a directly openable file when static;
- a short scenario checklist describing what to tap and assess;
- clear identification of interactive controls;
- a concise statement of intentionally unimplemented behavior;
- fallback screenshots only where they help review or diagnose access problems.

If a development server is required, the builder starts it and provides the URL. Do not report completion while a required server or validation process is still running or unavailable.

## 11. Validation

Run prototype validation as one coordinated pass after the intended source-alignment and prototype edits are complete. Repeat only failed or materially affected checks rather than restarting the full workflow after every small change.

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

## 12. Founder Review Delivery

After validation, report:

1. prototype purpose, classification, status, and source baseline;
2. working URL or file link;
3. screens, interactions, scenarios, and states implemented;
4. validation performed and material findings;
5. differences from the current source documents;
6. product decisions discovered or still required;
7. known limitations and intentionally deferred behavior;
8. reviewer disagreements or unresolved risks;
9. founder scenario checklist;
10. accept, amend, reject, supersede, or retire decision points.

Keep the report compact but decision-complete. Do not substitute a screenshot gallery for the interaction and product findings.

## 13. Feedback Classification and Source Alignment

Classify founder and reviewer feedback before editing:

| Feedback type | Treatment |
| --- | --- |
| Prototype correction | Fix the prototype because it fails to represent accepted documentation. |
| Visual preference | Update the prototype if product behavior and ownership do not change. |
| Product requirement change | Update the primary owning document first through the approved drafting process. |
| New route, status, role, or behavior | Return to proposal and founder approval before implementation. |
| Technical limitation | Record for the technical owner; do not silently weaken product intent. |
| Deferred detail | Keep visible as open or exploratory. |

When feedback changes product behavior:

```text
Founder decision
-> update primary owning document
-> apply documentation change integration workflow
-> align route diagram where applicable
-> update prototype
-> repeat product, functional, visual, and accessibility validation
```

Do not update only the prototype and leave the source documents contradictory.

## 14. Validation and Lifecycle Gate

A prototype may become a `Validated Reference` only when:

- it matches the accepted source documents within its declared scope;
- required interactions and states work;
- functional, visual, responsive, product, and applicable accessibility checks pass;
- known limitations and open questions are documented;
- exploratory choices are not presented as final requirements;
- the founder confirms it is suitable as a reference.

When a prototype is replaced:

- mark it `Superseded` or `Retired`;
- identify its replacement where applicable;
- remove or revise current-index references;
- preserve it only when it has historical or diagnostic value;
- do not leave several artifacts appearing equally current.

## 15. Integration and Commit Gate

Before requesting commit approval:

1. list prototype source files changed;
2. list source documents changed or confirm that no product requirement changed;
3. classify existing and replacement prototypes;
4. apply `payplus-document-change-integration-workflow.md` when documentation or governed visual references changed;
5. update Mermaid route diagrams only when navigation changed;
6. verify the prototype `README.md`, source baseline, status, and limitations;
7. complete functional, visual, responsive, product, and accessibility checks;
8. identify files checked but unchanged;
9. exclude caches, dependency directories, temporary exports, and unrelated assets;
10. report commit readiness and obtain founder approval.

After a substantive commit, follow the repository changelog and decision-log follow-up commit requirements. A prototype-only visual correction with no substantive product or governance decision must still be recorded according to the integration workflow's `Not applicable` decision-log rule.

## 16. Parallel-Agent and Worktree Use

- Use one canonical builder for a normal prototype.
- Use parallel read-only Product, UX / Accessibility, and Functional QA reviewers when complexity justifies them.
- Use separate design alternatives only when the founder explicitly requests comparison.
- Use worktrees only for independent prototypes or disjoint components with defined ownership and integration order.
- Do not allow multiple agents to edit the same prototype concurrently.
- Apply `payplus-parallel-agent-drafting-workflow.md` when a prototype task uses parallel agents or worktrees.

## 17. Reusable Invocation Prompts

### Prototype Plan Only

```text
Apply the PayPlus Prototype Design and Validation Workflow to [prototype task].

First provide a compact but decision-complete Prototype Review Pack covering
purpose, classification, source documents, routes, screen and interaction
inventory, actors, states, scenarios, technology, responsive and accessibility
scope, exclusions, review roles, affected documents, and founder approval
checklist. Do not over-compress material behavior or assumptions.

Do not build, edit, commit, or push until I confirm the plan.
```

### Approval-Gated Build

```text
I approve the prototype plan items [IDs].

Build one canonical interactive prototype using mock data only. Perform product,
functional, visual, responsive, and accessibility validation. Start any required
local server and provide a working URL plus founder test scenarios.

Do not change product requirements silently. Return material product changes for
decision and apply the documentation integration workflow where required. Do not
commit or push without my approval.
```
