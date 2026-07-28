# PayPlus DOC-07 Design Specification Workflow

Last updated: 2026-07-28

## 1. Purpose

This workflow governs how DOC-07 is authored, reviewed, validated, approved, and maintained as PayPlus's canonical specification for user-facing outcomes, messages, disclosures, and CTAs.

It must be used with:

- `AGENTS.md`;
- DOC-00;
- `payplus-outcome-message-notification-framework.md`;
- `payplus-document-change-integration-workflow.md`.

This workflow does not approve any copy, identifier, disclosure, legal position, security value, or implementation by itself.

## 2. DOC-07 Mandate

DOC-07 owns:

- the canonical Outcome and Message Matrix for user-facing results;
- Message IDs and approved user-facing copy;
- audience, surface, disclosure, masking, and variable rules;
- CTA label, priority, action, destination, retry, dismissal, and safe-return mapping;
- many-to-one neutral-message mappings;
- accessibility and localization notes;
- references to notification, audit, acceptance, support, and admin owners.

DOC-07 does not own:

- route structure or return behavior defined by DOC-06B;
- notification eligibility, recipients, channels, delivery, preferences, or retry rules defined by DOC-08;
- data schemas, canonical statuses, event taxonomy, or audit implementation defined by DOC-18;
- token, session, authentication, rate-limit, and access controls defined by DOC-19;
- test execution and release evidence defined by DOC-20;
- monitoring, incidents, service operations, and support execution defined by DOC-21;
- admin configuration, review, override, and operational evidence defined by DOC-22.

## 3. Roles and Ownership

| Role | Responsibility |
| --- | --- |
| Product / Founder | Confirms product meaning, priority, and user outcome. |
| DOC-07 Owner | Maintains the canonical matrix, wording, disclosure, CTA, and traceability. |
| Route/Domain Owner | Supplies the approved rule, trigger, route context, status relationship, and safe next steps. |
| Content/Design Reviewer | Reviews clarity, hierarchy, surface behavior, CTA, accessibility, and localization readiness. |
| Privacy/Security/Risk Reviewer | Reviews disclosure, masking, enumeration, sensitive variables, and abuse cases. |
| Legal/Compliance Reviewer | Reviews regulated, contractual, consent, and authorization wording where applicable. |
| Engineering/Data Reviewer | Confirms stable machine mapping, event/audit feasibility, and no copy/business-logic coupling. |
| QA Reviewer | Confirms measurable acceptance and negative-path coverage. |
| Support/Operations Reviewer | Confirms support handoff, correlation, failure handling, and operational usability. |
| Change Integrator | Performs owner-first alignment, validation, staged-diff review, and approved commit workflow. |

No reviewer may redefine another document's owned business rule inside DOC-07.

## 4. Inputs Required Before Drafting

For each route family or domain slice, collect:

1. approved source requirements and stable IDs;
2. route, screen, action, destination, and return behavior;
3. domain statuses and transitions, if any;
4. operation outcomes, including success, failure, cancellation, expiry, conflict, restriction, unavailable, and unconfirmed cases;
5. actor, audience, authentication, authorization, and assurance context;
6. prohibited disclosure and masking requirements;
7. notification eligibility and delivery owner;
8. event, audit, correlation, and retention requirements;
9. acceptance criteria and known test cases;
10. support and admin handoffs;
11. unresolved decisions and configurable values.

Chat, prototypes, diagrams, and AI execution files may help locate questions but must not override formal source documents.

## 5. Required DOC-07 Sections

DOC-07 must contain or link to:

1. Purpose and scope;
2. ownership and source-of-truth boundary;
3. terminology and prohibited language;
4. disclosure-level model;
5. global content and variable rules;
6. canonical Outcome Registry;
7. canonical Outcome and Message Matrix;
8. CTA and safe-return rules;
9. surface and presentation rules;
10. localization and accessibility rules;
11. notification handoff to DOC-08;
12. audit/data handoff to DOC-18;
13. security/privacy/control handoff;
14. support and admin handoff;
15. traceability matrix;
16. acceptance criteria;
17. open questions;
18. version history.

### 5.1 Mandatory Matrix Fields

Each matrix row must include:

| Field | Requirement |
| --- | --- |
| Source Rule ID | Approved rule producing the result. |
| Outcome ID / Code | Stable result identifier and machine-readable code. |
| Classification | Success, accepted, failure, cancellation, expiry, conflict, restriction, unavailable, or unconfirmed. |
| Origin Context | Route, screen, action, domain object, or system process. |
| Audience / Assurance | Actor and authentication/verification context. |
| Disclosure Level | `D0`, `D1`, `D2`, `D3`, or `DI`. |
| Message ID | Stable DOC-07 ID. |
| Surface | Inline, field, banner, sheet, modal, full page, toast, Inbox detail, or other approved surface. |
| Title / Body | Approved source copy or explicit `TBC`. |
| Variables | Allowed variables, format, source, masking, and fallback. |
| Primary / Secondary CTA | Label, action, destination, revalidation, and return behavior. |
| Retry / Dismissal | Allowed behavior, cooldown, idempotency, and fallback owner. |
| Notification | DOC-08 ID or `None` with reason. |
| Event / Audit | DOC-18 ID or future-alignment marker. |
| Security / Privacy | DOC-15/DOC-19 references and prohibited reveals. |
| Support / Admin | DOC-21/DOC-22 handoff or `None`. |
| Acceptance / Test | DOC-20 or owning acceptance IDs. |
| Status | Draft, In Review, Founder Working Baseline, Approved, Superseded, or TBC. |

## 6. Authoring Workflow

### Phase 1: Select and Bound the Slice

Author DOC-07 by coherent route family or domain slice, not as an uncontrolled repository-wide copy exercise.

For the slice:

- identify the primary route/domain owner;
- list included source requirement IDs;
- list excluded adjacent behavior;
- identify required reviewers;
- record open conflicts before drafting.

### Phase 2: Build the Outcome Inventory

For every material operation:

1. identify confirmed success or accepted result;
2. identify validation and policy failure;
3. identify cancellation, expiry, conflict, restriction, and unavailable results;
4. identify interrupted and unconfirmed results;
5. identify internal-only outcomes that must map to a neutral public message;
6. confirm whether any real persistent status changes;
7. remove duplicates and outcome-as-copy variants.

Do not create Message IDs until the Outcome inventory is coherent.

### Phase 3: Classify Disclosure

For each outcome:

- identify what the system knows;
- identify what this audience is allowed to know;
- assign the maximum disclosure level;
- list prohibited reveals;
- define the safe neutral fallback;
- review push/email/SMS exposure separately from authenticated surfaces.

Anonymous authentication and recovery outcomes require explicit account-enumeration review.

### Phase 4: Draft Message and CTA Mappings

Draft:

- message purpose;
- title and body;
- permitted variables;
- presentation surface and severity;
- primary and secondary CTA;
- retry, dismissal, support, and safe-return behavior;
- accessibility announcement and focus;
- localization notes.

Copy must be clear, accurate, non-accusatory, and actionable without overstating an unconfirmed result.

### Phase 5: Map Cross-Document Handoffs

For every row, determine:

- whether DOC-08 defines a separate notification;
- which DOC-18 event/audit evidence is required;
- which DOC-19 control constrains the result or reveal;
- which DOC-20 acceptance/test proves the behavior;
- whether DOC-21 support/operations must handle the result;
- whether DOC-22 exposes configuration, review, or override.

Use `TBC` with an owner when a downstream document is not ready. Do not invent missing technical detail.

### Phase 6: Review by Risk

Apply review depth proportionate to the row:

| Risk | Required Review |
| --- | --- |
| Public neutral or authentication result | Product, Content/Design, Security, Privacy, QA |
| Payment authorization or money movement | Product, Payments, Risk, Compliance, Legal as applicable, Engineering, QA |
| Sensitive data reveal or change | Product, Privacy, Security, Legal as applicable, Engineering, QA |
| Mandatory security notification | Product, Security, DOC-08 owner, Operations, QA |
| Support-assisted recovery or admin action | Product, Security, Support/Operations, DOC-22 owner, QA |
| Low-risk informational message | Product, Content/Design, owning domain, QA |

### Phase 7: Validate and Integrate

Run the validation in Section 10, apply the repository integration workflow, update only materially affected sources and registers, and prepare the pre-commit report.

### Phase 8: Approve, Commit, and Record

Only after founder authorization:

- stage intended files only;
- inspect the staged diff and file list;
- create the substantive commit;
- record it in changelog and decision log as required by the integration workflow;
- create the records-only follow-up commit;
- push only when explicitly authorized.

## 7. Interaction With Owning Documents

### 7.1 DOC-06B

DOC-06B supplies:

- route and screen context;
- user action and origin;
- destination and return behavior;
- current-state revalidation expectation;
- route-level failure and interruption points.

DOC-07 returns Outcome/Message/CTA IDs. It must not redefine route topology.

### 7.2 DOC-08

DOC-07 identifies whether an outcome may require a notification and supplies approved content/disclosure intent. DOC-08 decides:

- notification event ID;
- trigger eligibility;
- recipient;
- mandatory or preference-controlled delivery;
- channel;
- template and channel-safe content;
- retry, suppression, escalation, and delivery evidence.

An in-flow message is not a notification unless DOC-08 defines it as one.

### 7.3 DOC-18

DOC-18 maps:

- outcome occurrence/correlation;
- domain and audit events;
- canonical status transitions;
- notification message/batch/delivery records;
- lineage, timestamps, retention, and reporting.

DOC-07 must not define database schema or treat a message as an event.

### 7.4 DOC-19

DOC-19 owns:

- authentication and assurance;
- reset/token/session behavior;
- rate limiting, lockout, replay, and abuse controls;
- access and authorization;
- security logging and secret handling.

DOC-07 expresses these controls safely to the user without revealing control internals.

### 7.5 DOC-20

DOC-20 must cover:

- every canonical outcome and message mapping;
- disclosure and neutral-response equivalence;
- CTA and destination behavior;
- expiry, cancellation, retry, duplicate, interruption, and unconfirmed results;
- notification queueing where required;
- audit/correlation evidence;
- accessibility and localization-critical behavior.

No row is Done without mapped acceptance coverage.

### 7.6 DOC-21

DOC-21 owns:

- monitoring and operational alerts;
- retry and failure operations;
- incident response;
- support procedures and escalation;
- correlation-reference use.

DOC-07 defines what the user is told and how a support handoff begins.

### 7.7 DOC-22

DOC-22 owns:

- admin configuration;
- manual review and case actions;
- dual control or approval;
- permitted override and prohibited bypass;
- admin evidence and audit.

DOC-07 defines admin-visible or user-visible result messaging only; it must not grant an override.

## 8. Definition of Ready

A DOC-07 slice is ready for authoring when:

- the route/domain owner is confirmed;
- scope and exclusions are explicit;
- source requirements are stable enough to reference;
- operation boundaries and actors are known;
- known outcomes include negative and uncertain paths;
- status ownership is clear;
- disclosure and privacy inputs are available;
- route actions and destinations are defined or explicitly TBC;
- required reviewers are identified;
- conflicts and unresolved values are visible.

A slice is not ready if drafting would require the author to invent a business rule, security control, legal position, route, status, or notification trigger.

## 9. Definition of Done

A DOC-07 slice is Done when:

- every included source rule maps to an outcome or an explicit non-user-visible disposition;
- every user-visible outcome maps to an approved Message ID;
- every CTA has action, destination, revalidation, and safe-return behavior;
- disclosure levels and prohibited reveals are reviewed;
- persistent status changes reference their true owner;
- notifications reference DOC-08 or explicitly state `None`;
- event/audit mappings reference DOC-18 or an owned TBC;
- DOC-19 controls are referenced where applicable;
- DOC-20 acceptance/test IDs cover success, negative, interruption, and unconfirmed paths;
- DOC-21 and DOC-22 handoffs are defined where applicable;
- accessibility and localization notes are complete enough for implementation;
- no conflicting active ID or duplicate canonical copy remains;
- open questions have owners and do not masquerade as requirements;
- metadata, version history, indexes, traceability, changelog, and decision records are aligned as required;
- the founder-approved commit sequence is complete.

## 10. Validation

### 10.1 Structural Validation

Check:

- all mandatory fields exist;
- IDs follow the framework;
- references and Markdown links resolve;
- no duplicate active Outcome, Message, or Notification ID exists;
- `TBC`, `Open`, and `Superseded` rows are distinguishable;
- document metadata mirrors DOC-00 requirements.

### 10.2 Semantic Validation

Check:

- Outcome is not confused with Status;
- Message is not confused with Notification;
- Event is not confused with recipient delivery;
- the same internal result does not leak more information on a lower-assurance surface;
- many-to-one neutral mappings remain equivalent;
- unconfirmed results do not claim success or failure;
- CTA behavior cannot bypass route, security, authorization, payment, privacy, or risk controls;
- current state is revalidated on action;
- mandatory notification failure behavior is owned;
- support and admin handling cannot silently override product/security rules.

### 10.3 Traceability Validation

For every row, verify:

```text
Source Rule
  -> Outcome
  -> Message
  -> CTA
  -> Notification or None
  -> Event/Audit
  -> Acceptance/Test
  -> implementation mapping when coding begins
```

Missing links must be reported, not inferred.

### 10.4 Repository Validation

Run:

- targeted searches for old wording and IDs;
- duplicate-ID searches;
- link/reference checks where tooling exists;
- `git diff --check`;
- staged file-list and staged-diff review before commit.

Also confirm that unrelated existing changes remain unstaged.

## 11. Review Checklist

### Product and Domain

- Does each row reflect an approved rule?
- Is the actor, operation, and result unambiguous?
- Are all material negative and uncertain paths present?
- Is a real status transition referenced rather than invented?

### Content and Design

- Is the message accurate, concise, actionable, and consistent?
- Is the surface appropriate?
- Are CTA priority, label, destination, and return clear?
- Are loading, interruption, retry, dismissal, and unavailable-target states covered?

### Disclosure, Privacy, and Security

- Could the message reveal account existence, login method, counterparty, protected object, risk rule, or sensitive data?
- Are masking and assurance prerequisites explicit?
- Are variables restricted and safely sourced?
- Do public and out-of-band channels use safer content where required?

### Notification and Operations

- Is notification eligibility owned by DOC-08?
- Are mandatory notification recipients and failure behavior defined?
- Can support identify the occurrence through a safe correlation reference?
- Are monitoring, retry, escalation, and admin handoffs owned?

### Engineering and Data

- Can backend code return Outcome without copy?
- Are outcome occurrence, event, status transition, message, and delivery records distinct?
- Are idempotency and unconfirmed-result handling defined?
- Are prohibited raw errors and secrets excluded?

### QA and Traceability

- Does every rule map to an acceptance criterion?
- Are equivalence, negative, expiry, duplicate, interrupted, unconfirmed, stale-target, and accessibility cases covered?
- Can each requirement be traced to future code and automated tests?

## 12. Maintenance Workflow

When a source rule changes:

1. identify affected Outcome and Message rows;
2. determine whether meaning changed or only copy changed;
3. preserve stable IDs for non-semantic copy edits;
4. supersede rather than reuse IDs when business meaning changes;
5. check route, notification, event/status, security, test, support, and admin impacts;
6. update traceability and open questions;
7. invalidate or update derived AI execution material;
8. apply the integration and commit workflow.

At each material release or scheduled documentation review:

- find orphaned outcomes and messages;
- find implementation-only IDs absent from DOC-07;
- find notification templates without current source mappings;
- review `TBC` and open rows;
- verify localization and variable changes;
- review disclosure classifications after security/privacy changes;
- reconcile test and implementation traceability.

## 13. AI Authoring Prompt Contract

An AI agent drafting DOC-07 must be instructed to:

1. read all authoritative inputs first and not edit yet;
2. return the slice boundary, owners, applicable IDs, conflicts, and missing decisions;
3. draft only approved rows;
4. preserve exact source IDs and route names;
5. use `TBC` with an owner instead of invention;
6. produce a complete traceability matrix and review report;
7. stop before commit unless founder approval already covers the exact scope.

## 14. Workflow Acceptance Criteria

This workflow is effective when:

- DOC-07 can be authored incrementally without becoming a duplicate route, security, data, notification, or operations specification;
- reviewers can evaluate each mapping by stable ID and owned source;
- missing decisions remain visible;
- AI coding receives precise outcomes, messages, CTAs, disclosure rules, and tests;
- repository changes preserve source ownership and traceability.
