# PayPlus Outcome, Resolution, Message and Notification Framework

Last updated: 2026-07-29

## 1. Purpose

This framework defines the repository-wide architecture for translating a PayPlus business rule into a system result, user-facing communication, follow-up action, external notification, audit evidence, acceptance coverage, and implementation.

It is the detailed canonical owner of the Outcome → Resolution Strategy → Message/CTA → Notification architecture and the supporting traceability chain for DOC-07 and every future PayPlus specification that defines or consumes user-visible outcomes. Platform Design Principles owns the durable separation doctrine. DOC-07 remains the formal product owner of user-facing outcome, message, disclosure, and CTA mappings. DOC-08 remains the formal owner of notification events, channels, delivery rules, preferences, and notification templates.

This framework supplements DOC-00 and `AGENTS.md`. It does not replace formal product, domain, privacy, security, data, testing, support, or admin requirements.

## 2. Canonical Architecture

Every material user-facing result that requires controlled handling must follow this chain:

```text
Business Intent and Source Rule
    -> Decision or Evaluation
    -> Outcome
    -> Resolution Strategy
    -> Message and CTA
    -> Notification, when required
    -> Audit Event
    -> Acceptance Test
    -> Code and Automated Test
```

The chain is a traceability sequence, not a rule that every result must create a notification. A message may be shown without an out-of-band notification. An event may be audited without being shown to the user. A notification may be triggered by a material domain event rather than directly by a screen message.

### 2.1 Separation of Concerns

| Artifact | Definition | Must not become |
| --- | --- | --- |
| Business Rule | Approved product, domain, security, privacy, risk, or operational requirement. | UI copy or an implementation shortcut. |
| Decision / Evaluation | Application of approved rules to the current actor, object, context, capability, and control state. | An undocumented override or a user-facing error message. |
| Outcome | Stable business result of one operation or evaluation. | A sentence, transport error, or persistent status by default. |
| Resolution Strategy | Safe next handling permitted for the outcome and current context, such as continue, restart, redirect, wait, support, or stop. | A persistent status, automatic authorization, or disclosure of unavailable capabilities. |
| Message | Approved user-facing interpretation of an outcome for a defined audience and surface. | Backend business logic or a notification delivery rule. |
| CTA | Approved next action, route, retry, dismissal, or support handoff presented with a message. | A substitute for route authorization or current-state validation. |
| Notification | Recipient-specific out-of-band or Inbox communication triggered by an eligible event. | The domain event, account status, or in-flow message itself. |
| Audit Event | Evidence that a material action, result, disclosure, or delivery attempt occurred. | Ordinary analytics containing secrets or full message content. |
| Acceptance Test | Verifiable proof that the rule and its mapped behavior are satisfied. | A vague completion statement. |

## 3. Outcome Architecture

An Outcome is the stable business result produced by a route action, service operation, policy evaluation, or system reconciliation.

Examples include:

- recovery request accepted;
- reset link expired;
- payment authorization declined;
- evidence review required;
- payout result unconfirmed;
- promotion eligibility failed.

An Outcome must:

- describe what the business operation concluded;
- remain stable when wording or localization changes;
- identify its owning domain and source requirement;
- state whether it is public, authenticated, restricted, or internal-only;
- state whether retry, alternative action, support handoff, notification, and audit are required;
- distinguish confirmed success, confirmed failure, and unconfirmed result;
- avoid embedding secrets, personal data, vendor text, or transport details in its identifier.

An Outcome must not:

- be created only to match one sentence of copy;
- duplicate an existing domain status;
- expose account existence, login method, risk reasoning, internal thresholds, or other restricted facts;
- convert a transient error into a persistent account, payment, evidence, or case status;
- use `UNKNOWN_ERROR` where a safe, actionable business classification is available.

### 3.1 Outcome Record

Each canonical outcome record must contain:

| Field | Requirement |
| --- | --- |
| Outcome ID | Stable traceability ID. |
| Outcome Code | Stable machine-readable business code. |
| Source Rule | Owning requirement or policy ID. |
| Owning Domain | Formal document that owns the underlying business behavior. |
| Trigger / Preconditions | Conditions that produce the outcome. |
| Classification | Success, accepted, failure, cancellation, expiry, conflict, restriction, unavailable, or unconfirmed. |
| Audience Eligibility | Anonymous, authenticated actor, counterparty, admin, support, or internal-only. |
| Disclosure Level | Maximum information that the mapped message may reveal. |
| Persistent Status Change | `None` or an explicit reference to the status owner and transition. |
| Retry / Idempotency | Whether and how the operation may be repeated safely. |
| Resolution Mapping | Approved next-handling strategy, eligible alternatives, selection rule, unavailable-path treatment, and owning route/domain rule. |
| Message Mapping | One or more DOC-07 Message IDs. |
| Notification Mapping | DOC-08 Notification ID or `None`. |
| Audit Mapping | DOC-18 event reference or explicit future-alignment marker. |
| Acceptance Mapping | DOC-20 or owning acceptance/test IDs. |

### 3.2 Resolution Strategy

A Resolution Strategy states what PayPlus permits the user or system to do next after an Outcome is known and the current context and available capabilities have been checked.

Common strategies include:

- continue the current flow;
- restart the current flow;
- redirect to another approved route or login method;
- wait for review, reconciliation, service recovery, or a security condition;
- begin controlled Support handling; or
- stop where no approved continuation or recovery path remains.

One Outcome may support different resolutions in different assurance or capability contexts. For example, an inaccessible recovery email may permit an already-linked provider login for one user and require Support for another. The resolution selection must not expose unavailable login methods, internal risk rules, or protected account facts.

Resolution is a governed mapping, not a new persistent status or a requirement to build a standalone software service. The route or domain owner defines permitted resolution behavior. DOC-07 maps that behavior to approved messages and CTAs. DOC-19 and other specialist owners define the controls that determine whether a capability is usable.

## 4. Status vs Outcome

A Status is a durable fact about a governed object that other modules may rely on. An Outcome is the result of one operation.

| Question | Status | Outcome |
| --- | --- | --- |
| Does it remain true after the current request ends? | Usually yes. | Not necessarily. |
| Does it govern future permitted actions? | Often. | Only through mapped handling. |
| Does it require a defined lifecycle and transitions? | Yes. | No persistent lifecycle by default. |
| Example | `Identity Verification: Processing` | `RESET_LINK_EXPIRED` |

No agent may introduce a persistent status merely to preserve an outcome. If an operation changes a real domain status, the outcome must reference that separately owned transition.

## 5. Message Architecture

A Message is the approved user-facing interpretation of an outcome and permitted resolution in a specific context. DOC-07 is the canonical owner.

One outcome may map to different messages by:

- audience;
- authentication or verification level;
- surface;
- channel;
- locale;
- route context;
- legal or security disclosure boundary.

Multiple internal outcomes may map to one neutral public message when disclosure rules require it. For example, account-not-found, provider-only, and ineligible recovery processing may share one anonymous response even though internal audit results differ.

Each message definition must include:

- Message ID;
- mapped Outcome ID or IDs;
- route, screen, component, or surface;
- audience and required assurance context;
- title, body, supporting text, and approved variables;
- disclosure level and prohibited reveals;
- severity and presentation behavior;
- primary and secondary CTA mappings;
- retry and dismissal behavior;
- accessibility behavior;
- localization notes;
- DOC-08 notification relationship, if any;
- acceptance/test references.

Backend business logic must return a stable outcome and sufficient governed context for resolution and correlation, not hard-coded user-facing copy. Frontend or presentation services must resolve the approved message and CTA mapping without weakening current permission, disclosure, capability, or route checks.

## 6. CTA Architecture

A CTA is a user-facing action implementing a permitted Resolution Strategy and mapped to a message. It is not merely button copy.

Each CTA mapping must define:

- stable Action ID where traceability requires one;
- visible label;
- action type: retry, route, dismiss, cancel, request new link, contact support, or safe return;
- destination or command owner;
- authentication, permission, and current-state checks;
- return behavior;
- idempotency or duplicate-submission handling;
- unavailable-target fallback;
- whether the action is primary, secondary, or contextual.

A CTA must not authorize a payment, reveal protected data, revive an expired instruction, or bypass a security gate merely because it was presented in an earlier message. The target must be revalidated when the user acts.

## 7. Disclosure Framework

Disclosure determines what a message or notification may reveal, not what the system internally knows.

| Level | Name | Permitted baseline |
| --- | --- | --- |
| `D0` | Public Neutral | No confirmation of account existence, login method, protected object, risk rule, or recipient data. |
| `D1` | Authenticated General | General account or process information available to an authenticated actor without sensitive reveal. |
| `D2` | Verified Context | Context-specific information after required ownership, authorization, or verification checks. Masking still applies. |
| `D3` | Restricted Sensitive | Minimum necessary sensitive detail after explicit elevated assurance, role, purpose, and audit checks. |
| `DI` | Internal Only | Operational, security, risk, vendor, or diagnostic detail prohibited from user-facing output. |

The lowest applicable level wins. A higher-assurance surface must not reveal information prohibited by privacy, legal, risk, PSP/acquirer, or domain requirements.

Every mapping must identify:

- assurance prerequisites;
- permitted facts;
- prohibited facts;
- masking rules;
- safe fallback wording;
- whether localization may alter meaning;
- whether the same content is permitted in push, email, SMS, Inbox, support, and admin surfaces.

## 8. Event vs Notification

A Domain or Audit Event records that something happened. A Notification is a communication decision and delivery record.

```text
Domain operation
    -> Outcome
    -> Domain/Audit Event
        -> Notification eligibility decision
            -> Recipient message
                -> Channel delivery attempts
```

Not every event creates a notification. Not every recipient receives every eligible notification. Notification delivery failure must not rewrite the underlying outcome unless the owning domain explicitly defines that dependency.

DOC-08 must define:

- Notification ID and eligible trigger event;
- required and optional recipients;
- mandatory, optional, preference-controlled, or prohibited delivery;
- required and optional channels;
- content/template ownership;
- routing/deeplink behavior;
- retry, failure, escalation, and suppression rules;
- retention and delivery evidence.

DOC-18 must distinguish the domain event, audit event, notification event type, recipient-specific message, batch/job, and channel delivery attempt.

## 9. Naming Conventions

Identifiers are stable interfaces. Renaming requires an explicit migration and traceability review.

| Artifact | Pattern | Example |
| --- | --- | --- |
| Product/domain rule | `RULE-[DOMAIN]-[NNN]` or owning document requirement pattern | `RULE-AUTH-REC-001` |
| Outcome traceability ID | `OUT-[DOMAIN]-[NNN]` | `OUT-AUTH-REC-004` |
| Outcome code | `[DOMAIN]_[CONTEXT]_[RESULT]` | `AUTH_RECOVERY_LINK_EXPIRED` |
| Message ID | `MSG-[DOMAIN]-[NNN]` | `MSG-AUTH-REC-004` |
| Notification ID | `NOTIF-[DOMAIN]-[NNN]` | `NOTIF-SEC-004` |
| Audit/domain event | Owning DOC-18 event convention | `EVT-AUTH-RECOVERY-COMPLETED` |
| Acceptance criterion | `AC-[DOMAIN]-[NNN]` or owning test pattern | `AC-AUTH-REC-009` |

Rules:

- use uppercase ASCII and hyphens for document IDs;
- use uppercase ASCII and underscores for machine-readable outcome/event codes;
- identify the domain and result, not the UI wording or document filename;
- do not encode mutable copy, locale, HTTP status, vendor name, or numeric threshold in a stable ID;
- do not reuse a retired ID for a different meaning;
- aliases and migrations must point to one current canonical ID.

## 10. Ownership Rules

| Concern | Primary Owner |
| --- | --- |
| Route, screen sequence, entry, destination, return | DOC-06B or applicable DOC-06 family/domain route owner |
| Outcome meaning and permitted Resolution Strategy | Applicable route or domain owner |
| User-facing outcome, message, disclosure, and CTA mapping | DOC-07 |
| Notification event, recipient, channel, template, delivery, and preference | DOC-08 |
| Domain lifecycle and payment behavior | Applicable domain document, including DOC-09 to DOC-14 |
| Privacy, masking, retention, approved-purpose access | DOC-15 |
| Data model, status/event taxonomy, audit, lineage, reporting | DOC-18 |
| Authentication, token, session, access, and security control | DOC-19 |
| Acceptance, UAT, release evidence | DOC-20 |
| Monitoring, incident, retry, and operational escalation | DOC-21 |
| Support procedure and user handoff | DOC-21 unless a later approved support owner supersedes it |
| Admin configuration, review, override, and evidence | DOC-22 |

Reference documents must link to the owner instead of copying the canonical rule. A conflict must be returned to the owning documents; an agent must not resolve it by silently choosing one version.

## 11. Traceability Rules

Every material user-facing result must be traceable across:

| Source Rule | Outcome | Resolution | Message / CTA | Notification | Event/Audit | Acceptance/Test | Code/Test |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Stable requirement ID | Outcome ID/code | Permitted next handling | Message ID and action/destination | Notification ID or `None` | Event ID | AC/test ID | Implementation reference |

The mapping must:

- use `None` with a reason where a notification or CTA is intentionally absent;
- identify open technical mappings as `TBC` without inventing them;
- preserve many-to-one neutral-message mappings;
- record superseded IDs and their replacement;
- identify untested, unimplemented, or deferred rows explicitly;
- be updated when a rule, owner, disclosure boundary, route, or notification trigger changes.

No item is implementation-ready if the source rule, outcome, message behavior, and acceptance coverage cannot be identified.

## 12. AI Coding Rules

An AI coding agent must:

1. read the owning source documents and this framework before implementation;
2. enumerate applicable stable IDs and unresolved conflicts before coding;
3. use documented Outcome codes unchanged;
4. implement only documented Resolution Strategies and re-evaluate current capability before action;
5. keep user copy outside backend business logic;
6. keep notification dispatch driven by eligible events and policy, not UI rendering;
7. preserve neutral public responses and disclosure limits;
8. represent unconfirmed results explicitly and avoid unsafe automatic retry;
9. preserve idempotency, correlation, audit, and current-state revalidation;
10. create automated tests for every mapped acceptance criterion;
11. return a requirement-to-code-and-test traceability report.

An AI coding agent must not:

- invent an Outcome, Message ID, Notification ID, status, disclosure exception, or admin override;
- expose raw provider, database, stack, HTTP, risk, or security errors to users;
- treat notification success as proof of domain success;
- roll back a completed security or payment operation solely because a notification failed unless the owner requires it;
- hard-code localized copy into business services;
- mark implementation complete while a required mapping or test is missing.

## 13. AI Review Rules

An AI reviewer must review by stable ID and report:

- missing or duplicate owners;
- Outcome/Status confusion;
- Outcome/Resolution confusion or an undocumented resolution path;
- Event/Notification confusion;
- missing neutral-response or disclosure handling;
- messages without outcomes or outcomes without mapped presentation behavior;
- CTAs without permission, current-state, safe-return, or unavailable-target handling;
- mandatory notifications without delivery-failure behavior;
- missing audit/correlation evidence;
- undocumented IDs, copy, status, or assumptions introduced in code;
- missing negative, interruption, expiry, duplicate, and unconfirmed-result tests;
- traceability rows without code or tests.

The reviewer must not approve on screen appearance alone.

## 14. Canonical Example

```yaml
source_rule: RULE-AUTH-REC-004
outcome_id: OUT-AUTH-REC-004
outcome_code: AUTH_RECOVERY_LINK_EXPIRED
classification: expiry
owner: DOC-06B
disclosure_level: D0
persistent_status_change: none
resolution_strategy: restart_recovery
message_id: MSG-AUTH-REC-004
primary_cta:
  label: Request New Link
  action: AUTH_RECOVERY_REQUEST_NEW_LINK
secondary_cta:
  label: Return to Log In
  destination: AUTH-LOGIN-FULL
notification_id: none
audit_event: EVT-AUTH-RECOVERY-LINK-REJECTED
acceptance_test: AC-AUTH-REC-004
```

This example defines structure only. DOC-07, DOC-18, DOC-20, and the owning route/security documents must approve the exact IDs and behavior before implementation.

## 15. Change and Maintenance Rules

Changes to this framework are governance-sensitive. Apply the [`PayPlus Documentation Development Workflow`](../documentation-system/payplus-documentation-development-workflow.md).

When a canonical mapping changes:

1. update the primary owner;
2. update DOC-07 and DOC-08 only where their owned behavior changes;
3. check DOC-18, DOC-19, DOC-20, DOC-21, and DOC-22 impacts;
4. update traceability and open questions;
5. preserve or explicitly supersede stable IDs;
6. regenerate derived AI execution material only after source documents are accepted;
7. validate that old and new definitions do not both appear active.

## 16. Framework Acceptance Criteria

This framework is satisfied when:

- Decision, Outcome, Resolution Strategy, Message, CTA, Notification, Disclosure, Status, and Event are kept distinct;
- DOC-07 is the sole canonical owner of user-facing outcome/message/CTA mappings;
- DOC-08 is the sole canonical owner of notification delivery behavior;
- each material result has a stable, reviewable traceability chain;
- disclosure rules govern content independently of internal knowledge;
- AI coding and review can identify missing definitions without inventing them;
- implementation completion requires mapped automated tests.
