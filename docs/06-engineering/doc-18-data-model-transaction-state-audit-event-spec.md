---
document_id: DOC-18
title: Data Model, Transaction State, Audit Event & Reporting Specification
version: 0.4.24
status: Founder Working Baseline
owner: Engineering / Data
reviewers:
  - Product Lead
  - Engineering Lead
  - Data Lead
  - Privacy Lead
  - Security Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Engineering Lead
  - Data Lead
last_updated: 2026-08-13
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Domain Architecture
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention Specification
  - DOC-16 Technical Architecture Specification
  - DOC-17 API & Third-party Integration Specification
  - DOC-19 Security, Tokenization, Authentication & Admin Control Specification
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-18 - Data Model, Transaction State, Audit Event & Reporting Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-18` |
| **Title** | Data Model, Transaction State, Audit Event & Reporting Specification |
| **Version** | `0.4.24` |
| **Status** | Founder Working Baseline |
| **Owner** | Engineering / Data |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Data Lead<br>Privacy Lead<br>Security Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Engineering Lead<br>Data Lead |
| **Last Updated** | `2026-08-13` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-09 Payment Domain Architecture<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-16 Technical Architecture Specification<br>DOC-17 API & Third-party Integration Specification<br>DOC-19 Security, Tokenization, Authentication & Admin Control Specification<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

DOC-18 defines PayPlus data-model, transaction-state, audit-event, reporting, warehouse, lineage, analytics, and AI/model-readiness requirements at specification level.

This document is not a final physical database schema, migration plan, data warehouse build plan, model design, vendor selection, privacy policy, or implementation ticket set.

DOC-18 should make PayPlus ready for AI-assisted coding later by ensuring every material product object, event, and field can be traced to its business purpose, privacy classification, source, owner, access rule, retention rule, audit requirement, and permitted downstream use.

## 2. Scope and Ownership

DOC-18 owns:

- logical data object families;
- field metadata requirements;
- transaction state and status linkage requirements;
- audit-event taxonomy requirements;
- reporting, warehouse, and analytics data-mart requirements;
- data lineage and derived-data requirements;
- future feature/model metadata requirements;
- aggregation and partner-reporting data boundaries at technical-data level.

Detailed requirements belong to:

| Topic | Owning Document |
| --- | --- |
| Product scope and positioning | DOC-01, DOC-05 |
| Evidence field sets and document AI/OCR behavior | DOC-12 |
| Promotion, coupon, referral, membership, and partner-offer logic | DOC-13 |
| Risk signal meaning, review routing, and model-assisted risk boundaries | DOC-14 |
| Privacy, consent, retention, approved-purpose use, and data-use tiers | DOC-15 |
| System architecture and services | DOC-16 |
| Provider APIs, webhooks, files, and partner integrations | DOC-17 |
| Authentication, encryption, tokenization, RBAC, and pseudonymization | DOC-19 |
| Admin workflows, queues, exports, and operational actions | DOC-22 |

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Data-engine readiness | Material product features should create structured, classified, auditable, purpose-linked data. |
| Privacy inheritance | DOC-15 data classes, approved-purpose rules, masking, retention, consent, and data-use tiers apply to DOC-18 objects and fields. |
| MVP model posture | MVP may use rules, OCR/document AI, and assisted review where enabled; advanced AI decisioning, offsite activation, or user-level partner data sharing is not approved by DOC-18. |
| Event-first design | Material user, system, admin, payment, evidence, promotion, notification, support, and risk actions should create traceable events where practical. |
| Lineage | Raw, extracted, corrected, verified, derived, aggregated, reported, and model-feature data should preserve lineage. |
| Bills evidence future update | Final DOC-18 must define the logical objects, status fields, active-version rules, lineage, events, and audit records for DOC-06C `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`. |
| Payment profile future update | Final DOC-18 must define tokenized card, saved split-card payment profile, allocation-ratio, card-slot, default-card, starred/frequent profile, action-required profile, return-context, and audit-event structures for DOC-06B `PAYMENT-PROFILE-ROOT`. |
| Offers and promotion future update | Final DOC-18 must distinguish offer UI presentation from payment-card funding data and define Offer ID, multi-collection membership, primary root placement, per-collection display priority, display snapshot, payment-card/funding-leg eligibility result, highest-user-value comparison, automatic Card Offer application, separate coupon/voucher/discount application, promotion quote, and audit-event structures required by DOC-06B, DOC-09, and DOC-13. |
| Referral future update | Final DOC-18 must define the reusable user-linked referral code/reference, registration attribution, campaign and beneficiary-role linkage, qualification progression/outcome, entitlement, claim, issued reward reference, privacy-safe display projection, hold/reversal, and audit-event structures required by DOC-06B, DOC-13, DOC-15, and DOC-22. Sharing must remain distinct from recipient identity and attribution. |
| Reward instrument future update | Final DOC-18 must define canonical issued-reward objects, lifecycle projections, authoritative fulfilment and idempotency, unknown-result recovery, credential references, reveal/access events, checkout selection linkage, and separate instrument-type, earning-source, participant-role, program, campaign/offer/entitlement, and fulfilment-method dimensions required by DOC-06B, DOC-09, DOC-13, DOC-15, and DOC-22. |
| Authentication and account-control future update | Final DOC-18 must define temporary registration attempts, atomic account creation and identifier claiming, unique verified primary-email/phone/identity constraints, stable PayPlus User ID and optional nickname, explicit login methods, stable external-provider identity links, password-set state, restricted-account and Account Activation gates, Fast Login eligibility, device/session revocation, masked-contact fields, HK Phone Verification challenge/attempt records, separate provider and PayPlus Identity Verification decisions, the five-label identity projection (`Not Verified`, `Processing`, `Verified`, `Failed`, `Update Required`), capability-aware Recovery attempts, separate Outcome and Resolution Strategy records, origin/return context, provider-callback correlation, no-duplicate-submission handling, contact-change events, six-digit Payment Passcode Set/Change/Reset attempts and preference state, security notifications, privacy-request lifecycle, protected-export access, and account-closure lifecycle required by DOC-06B, DOC-07, and DOC-15. Provider payloads, credentials, OTPs, passcodes, and sensitive values must not be copied into route analytics. |
| Destination-fact future update | Final DOC-18 may represent only owner-approved, context-specific destination facts and immutable snapshots required by DOC-10 and related owners. DOC-10 owns effective destination and payout meaning; DOC-22 may execute only owner-permitted operations. No destination profile library or retired Receiving Info runtime is defined here. |
| More and shortcut future update | Final DOC-18 must distinguish the approved shortcut catalog, versioned current eligible admin default, account-level user preference, effective resolved Home set, protected `More` rule, availability reason category, save/restore attempt, and destination-handoff event required by DOC-06B, DOC-15, and DOC-22. It must not copy sensitive destination data or internal risk/compliance reasons into analytics. |
| Notification future update | Final DOC-18 must define stable notification event types, recipient-specific Inbox/message records, optional batches, source event/object lineage, recipient role projection, category, read/archive presentation, status/action-at-send snapshots, current-domain resolution, templates, route targets, correlation/causation/deduplication, per-channel delivery attempts, preferences, and audit events required by DOC-06B, DOC-08, DOC-15, and DOC-22. |
| Human review | Sensitive AI/model-assisted outcomes should support reason codes, reviewability, override controls, and audit trails. |

## 4. Core Object Families

DOC-18 should define logical structures for at least the following object families:

- user account;
- temporary registration attempt;
- primary account email and uniqueness record;
- primary phone and individual-identity uniqueness record;
- account login method;
- external login-provider identity link;
- password-set state;
- Fast Login eligibility and remembered-device/session reference;
- restricted-account and Account Activation gate;
- authentication outcome-to-message mapping;
- payer profile;
- payee profile;
- KYC/KYB verification reference;
- authentication, device, OTP, passcode, and material account-change event;
- obligation record;
- contract or relationship record;
- evidence source record;
- evidence/document;
- evidence extraction layer;
- normalized evidence field;
- user correction;
- verification signal;
- final evidence snapshot;
- obligation payment-readiness history;
- linked support/dispute case;
- payment quote;
- tokenized card;
- saved payment profile;
- payment instruction;
- payment instruction funding leg;
- payment attempt;
- payment authorization;
- settlement record;
- payout item;
- payout batch;
- payout reconciliation result;
- refund, cancellation, dispute, reversal, chargeback, and support case;
- campaign;
- offer;
- offer discovery collection membership;
- offer rule;
- promotion quote;
- promotion quote reservation;
- benefit application and selection-basis record;
- qualification accumulator;
- benefit entitlement;
- reward instrument;
- redemption or fulfilment record;
- referral code/reference;
- referral relationship;
- referral registration attribution;
- referral qualification record;
- referral beneficiary-role linkage;
- membership account;
- account/profile preference record;
- identity-verification reference and user-facing status projection;
- privacy request and protected-export access record;
- account-closure request, blocker, cancellation, and finalization record;
- owner-approved context-specific destination facts and immutable destination snapshots with source reference;
- canonical obligation and evidence records separate from non-erasing source-visibility projections; detailed archive, restore, prior-version, and evidence-version representation remains deferred to the applicable formal owners;
- dashboard shortcut configuration;
- user shortcut preference;
- dashboard placement exposure;
- carousel impression/action;
- communication and notification event;
- admin review case;
- risk signal;
- risk decision;
- audit event;
- analytics aggregate;
- model feature definition where approved;
- model run or AI-assisted decision event where approved.

## 5. Field Metadata Requirements

Each material object and field should support metadata for:

- DOC-15 data class;
- sensitivity level;
- displayability by role and screen;
- masking or reveal rule;
- Founder-settled indefinite retention requirement and approved access/masking controls;
- data owner;
- approved purpose;
- access roles;
- audit requirement;
- source system or evidence layer;
- source object and source event;
- lineage to derived, analytics, reporting, risk, or model-feature data;
- consent or preference dependency where applicable;
- partner-sharing status;
- aggregation/de-identification status;
- model-use eligibility;
- prohibited-use flag where applicable.

This metadata is required so AI-build execution materials can later generate code, schemas, access rules, tests, and audit events without guessing privacy or product intent.

## 6. Event Taxonomy Requirements

PayPlus should define event families before implementation.

| Event Family | Examples |
| --- | --- |
| Account and authentication events | registration attempt created/progressed/abandoned/expired/invalidated, identifier uniqueness rechecked, restricted account created, Account Activation evaluated/completed, login resolver invoked, Fast Login eligibility renewed/revoked, Full Login selected, login succeeded/failed, logout, Log In With Another Account confirmed, current-device session revoked, login method linked/unlinked/blocked, first password set, password changed, provider authentication returned, account-link conflict detected, new-device login, dormant reauthentication, material-change reauthentication attempted/completed/failed, authentication outcome recorded, approved message selected, contact change initiated/verified/completed/failed, credential or identity change, Me opened, account/security/privacy destination selected, phone-verification opened/challenge-created/delivered/resent/verified/expired/failed/replaced, identity-verification opened/capture-resumed/submitted/processing/provider-result-received/policy-checked/verified/failed/update-required/admin-reset/returned, identity admin reset requested/approved/rejected, payment-passcode set/change/reset attempted/completed/failed, passcode recovery escalated, sensitive pending authorization invalidated, security notification issued, sensitive reveal attempted/completed/failed, action-required item opened, payment-passcode preference changed, trusted-device removed, session revoked, language/theme changed, privacy request submitted/status changed/completed/failed, protected export issued/opened/expired, account closure requested/blocked/cancelled/finalized. |
| Evidence and archive events | upload started, upload submitted, OCR processed, field extracted, user corrected, verification passed, mismatch found, duplicate detected, status changed, evidence snapshot finalized, replacement submitted/accepted/rejected, archive eligibility checked, source-visibility projection created, current evidence projected into that visibility, current evidence revalidated, archived-root/list opened/searched/filtered where approved, archived detail opened where approved, access denied or unavailable. Detailed restore, prior-version, and evidence-version behavior remains deferred. |
| Route/navigation events | Pay+ action sheet opened/dismissed and action handoff; More opened/searched; shortcut manage mode entered; shortcut added, removed, reordered, saved, restored to current default, or save/restore failed; unavailable entry encountered; destination opened/handoff succeeded or failed. Route events may record only safe availability/reason categories and must not carry sensitive evidence, identity, card, bank, payment, destination-content, or internal risk/compliance values. |
| Payment events | quote created, quote revalidated, instruction created, funding leg created, authorization attempted, authorized, failed, captured, payment completed. |
| Payment profile events | card add started, tokenization returned, card nickname edited, default card changed, card removed or archived, profile created, profile edited, profile starred/unstarred, profile marked action-required, profile selected for checkout/instruction, profile issue displayed. |
| Payout and destination events | Owner-approved destination facts reviewed, destination snapshot created, destination difference acknowledged, linked payee notified where permitted, payout destination held/approved, settlement received, payout ready, payout held, payout released, payout submitted, payout completed, reconciliation matched, destination-attributable exception opened, transient exception opened. DOC-10 owns payout and destination meaning; this taxonomy does not create a destination profile or runtime. |
| Risk events | rule triggered, risk score assigned, step-up required, manual review opened, hold applied, block applied, override approved, escalation recorded. |
| Promotion events | offer displayed, offer viewed, collection filtered, eligibility evaluated, competing Card Offers compared, highest-user-value Card Offer auto-selected, coupon/voucher/discount selected, promotion quote created or recalculated, benefit reserved, entitlement earned, reward issued, reward detail viewed, credential revealed/copied where permitted, partner handoff opened/returned, reward use attempted/confirmed/unknown, reward credited, reward expired, reward held/released/reversed. |
| Referral events | share action initiated, referral link copied, QR displayed, registration code validated, attribution created, qualification progressed or decided, referral entitlement created or held, claim attempted or completed, reward issued, reward reversed or clawed back. Share events must not imply delivery, recipient identity, or attribution. |
| Communication events | notification event qualified/suppressed, recipient message created, batch linked, queued, scheduled, sent, delivered, failed, retried, read, marked unread, archived, restored, Mark All Read applied, contextual target opened/unavailable, preference changed/failed, and template version applied. |
| Admin events | queue assigned, evidence viewed, action taken, export requested, sensitive field revealed, override reason captured. |
| Analytics/model events | aggregate created, model feature refreshed, model run executed, AI-assisted recommendation shown, human review outcome recorded where approved. |

Each event should capture event ID, event type, actor, role, timestamp, source object, affected object, previous state where applicable, new state where applicable, reason code where applicable, correlation ID, applicable case ID, and audit classification.

Authentication events must distinguish:

- the stable internal outcome type;
- the permitted Resolution Strategy selected after that outcome;
- the approved user-facing Message ID selected under DOC-07;
- the unique occurrence/event ID and correlation ID used for one attempt or related flow;
- the originating route, user action, disclosure level, permitted destination, return context, retry/restriction result, and admin/support visibility.

Multiple internal outcomes may map to one approved public message, and multiple outcomes may use the same permitted Resolution Strategy. Outcome, Resolution Strategy, persistent domain status, Message/CTA, notification record, and audit occurrence must remain separately identifiable. Exact outcome identifiers, resolution codes, Message IDs, message copy, and mappings remain open under DOC-07 and must not be inferred by DOC-18.

## 7. Transaction State and Linkage

DOC-18 should maintain linkages between:

- obligation;
- contract or relationship record where applicable;
- evidence;
- evidence source;
- payer;
- payee;
- payment quote;
- promotion quote;
- payment instruction;
- funding leg;
- payment attempt;
- settlement record;
- payout item;
- payout batch;
- notification;
- bill/rent reminder;
- support/dispute case;
- admin review case;
- audit event.

Evidence proves or supports an obligation but is not itself an obligation or financial activity. A payer-created obligation may link directly to evidence. Payment and payout activity link to the obligation and its transaction records, not to evidence as the activity owner. Any historical Request or participant-linking identifier is traceability-only and must not define current runtime behavior.

User-facing `BILLS-ACTIVITY` projections must contain only payment and related payout/transfer, failure, return, refund, and reversal events for the selected obligation. Evidence verification and other owner-domain histories remain separately queryable and auditable in their owning domains.

The final data model must not use one overloaded status field for unrelated domain handling. It must preserve separate fields or linked records for:

- evidence verification outcome and user-facing evidence status;
- obligation payment readiness: `Ready to Pay`, `Action Required`, or `Under Review`;
- linked support/dispute case lifecycle: `Open`, `Pending Information`, `Under Review`, `Resolved`, or `Closed`;
- payment and payout lifecycle records linked through the obligation.

Evidence or source verification does not itself establish payment authorization or readiness. A payer-created evidence-backed obligation may proceed only where all applicable owner gates pass.

Referral linkage must preserve the sequence `referrer -> user-linked code/reference -> campaign and role-specific offer -> referee registration attribution -> qualification -> beneficiary-specific entitlement -> issued reward instrument`. Referrer and referee entitlements may use the same campaign but must remain separate records with explicit beneficiary role. Referral sharing must not create a referee, relationship, or invitation lifecycle before valid registration attribution.

Reward-instrument linkage must preserve independent instrument type, earning source, participant role where applicable, program context, campaign and offer source, originating entitlement, fulfilment method, current canonical state, lifecycle projection, authoritative redemption/fulfilment result, and related checkout/payment or partner-reconciliation reference. Referral role must not be stored as an instrument type, and issued reward status must remain distinct from Referral claim-history presentation.

Future DOC-18 drafting must also specify entitlement-time quota/value reservation, campaign/offer/benefit/terms snapshot, separate campaign-end/claim-deadline/reward-usage-expiry fields, one-entitlement-to-at-most-one-instrument idempotency, duplicate/concurrent/uncertain claim recovery, and administrator hold/release/reversal audit linkage. User-facing Referral projections must remain distinct from canonical internal states, and masked referee phone must be projected only to the permitted `REFERRAL-ROOT` progress context.

DOC-18 must implement the DOC-09 Payment Domain architecture without redefining it. The logical model must preserve distinct Bill/Rent Payable Basis, Projection, Materialization, Payment Obligation, Checkout Workspace, Obligation Allocation, payable-capacity reservation, Funding Allocation Version, Funding Leg, Payment Attempt, Provider Submission, Provider Confirmation Event, Payment, Payment Application, Effective Financial Adjustment reference, Effective Coverage, Outstanding Amount, and Effective Payout Destination Snapshot concepts.

The model must also keep a deliberate Payment Instruction separate from an incomplete Checkout Workspace. It must preserve stable identities, correlation and causation, target-lock timing, allocation versions, payer authorization, provider evidence references, late-confirmation exception handling, immutable Payment and Payment Application facts, adjustment attribution, coverage recalculation inputs, and downstream Settlement/Payout handoffs. Machine states, transitions, persistence, event IDs, schemas, and reporting projections remain DOC-18 work and must trace to DOC-09 semantic conditions and invariants.

DOC-18 must include data structures for DOC-06B/DOC-09 tokenized card and payment profile behavior, including card token/reference, permitted masked metadata, card nickname, card status, default-card marker, saved split-card profile name, card slots, stored ratios, setup/reference amount, starred/frequent marker, action-required state, soft-delete/archive metadata, checkout/instruction return context, and related audit events.

DOC-18 may represent an owner-approved, context-specific destination fact and immutable destination snapshot separately from source truth. DOC-10 owns effective destination, payout, authorization, and reconciliation meaning; detailed profile, version, proof, readiness, archive, or replacement-source behavior is not defined here.

DOC-18 must include data structures linking each applied payment-method-sensitive Card Offer to the selected payment card or funding leg, the competing eligible Offer IDs, approved user-value comparison result, automatic-selection reason, affected funded amount, separate coupon/voucher/discount application, promotion quote version, and revalidation event. The same Offer ID may have multiple discovery-collection memberships but should remain one underlying offer object.

DOC-18 must also define the notification model as linked but distinct records: a stable event definition; one recipient-specific Inbox/message record; an optional batch/manual/campaign/support/scheduled-job grouping; source event and source object references; recipient and role projection; approved category; `Unread` / `Read` / `Archived` presentation; status/action-at-send snapshots; current-domain resolution reference; template version; registered route target; correlation, causation, and deduplication references; and separate channel-delivery attempts. Category, presentation state, domain status, and Action Required must not be collapsed into one status field. Message read/archive changes must not mutate the owning domain object.

DOC-18 must also represent DOC-06C ordinary bill/rent reminders only to the extent approved by that owner, including source and obligation lineage, operational active/inactive/expired/disabled treatment, notification linkage, and auditability. Operational disablement or expiry must not delete, purge, or destroy the retained record.

DOC-18 must also define the temporary registration-attempt object required by DOC-06B and DOC-15. It should use a stable attempt ID and may hold proposed provider, email, phone, referral, consent, OTP-state, security, rate-limit, correlation, created, last-active, and expiry references. It must not create an account ID, reserve a proposed identifier, create referral attribution, grant login or financial rights, or expose account-only routes. Final restricted-account creation must atomically recheck uniqueness, verified-email state, Terms/Privacy acceptance, and attempt validity before claiming identifiers and creating account-linked records.

DOC-18 must also distinguish:

- obligation records for accepted controlled Bill sources and the separate Rent journey, as defined by DOC-05 and DOC-09;
- owner-approved tenancy or other relationship context where it precedes an applicable obligation;
- evidence source records, such as invoice, bill, tenancy agreement, stamp duty document, CR109, rent demand, HKHA tenancy card, carpark invoice, property management notice, upload, QR-derived record, or manual entry;
- source-context associations remain factual lineage and do not create a participant-linking runtime.

Payer/economic-Payee association remains factual source context. Evidence-to-payee validation, duplicate detection, payout validation, and risk analysis may run as owner-governed checks; DOC-18 does not define a participant object, reciprocal runtime, or automatic user-to-user matching state.

## 8. Analytics, Warehouse, and Data Marts

PayPlus should support governed analytics without exposing unnecessary sensitive data.

Candidate data marts include:

- product funnel mart;
- evidence/OCR quality mart;
- payment success and failure mart;
- payout and reconciliation mart;
- risk and manual-review mart;
- promotion and campaign performance mart;
- dashboard placement and personalization mart;
- reminder effectiveness and due-date behavior mart;
- support, dispute, refund, and chargeback mart;
- category economics mart;
- aggregate partner reporting mart where approved.

Analytics outputs should preserve source lineage, aggregation level, sensitivity, permitted purpose, retention rule, owner, access role, and partner-sharing status.

## 9. AI and Model-Readiness Requirements

DOC-18 should support future approved AI/model use without approving every model.

Required metadata for approved model features or AI-assisted decisions should include:

- model or feature ID;
- model purpose;
- source data classes;
- permitted inputs;
- prohibited inputs;
- consent/preference dependency;
- aggregation or pseudonymization method where applicable;
- training, validation, and monitoring owner;
- explainability or reason-code requirement;
- human-review requirement;
- adverse-impact, fairness, privacy, or sensitive-use review requirement where applicable;
- Founder-settled indefinite retention and approved access/masking expectations for model inputs and outputs; operational expiry or purpose completion must not delete the record;
- audit-event linkage.

Candidate future model areas include:

- bill/category classification;
- evidence extraction and evidence quality scoring;
- duplicate or reused evidence detection;
- risk and fraud decision support;
- payer-payee relationship graph analysis;
- promotion abuse detection;
- lifecycle segmentation;
- consented offer ranking;
- campaign lift measurement;
- internal analyst copilots.

Marketing, partner reporting, external activation, insurance-related targeting, credit scoring, or user-level partner data sharing may not use AI/model outputs unless the use is separately approved in DOC-13, DOC-15, legal/privacy review, and the relevant partner contracts.

## 10. Partner Reporting and Aggregation Controls

Partner reporting should prefer aggregated, de-identified, campaign-level, or cohort-level outputs.

DOC-18 should define:

- aggregation thresholds;
- small-cell suppression rules;
- de-identification or pseudonymization method;
- output approval workflow;
- report recipient and purpose;
- partner-sharing status;
- data retention for reports;
- audit event for report generation and delivery.

Clean-room collaboration, pseudonymized matching, or offsite activation is future-gated and requires separate approval under DOC-15 and the affected commercial, legal, security, and partner documents.

## 11. Open Questions

Sections 4 through 10 define the current baseline for PayPlus data objects, lifecycle states, metadata, lineage, AI/model-use eligibility, reporting events, and audit records. The open questions below are remaining implementation and approval decisions, not a signal that the baseline requirement is absent.

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-18-001 | What final logical and physical schema should be used for core source, evidence, payment, payout, promotion, risk, audit, and analytics objects? | Engineering / Data | High | Open |
| OQ-18-002 | What event taxonomy, reason-code library, and correlation ID model should be used before AI build-execution conversion? | Engineering / Data / Operations | High | Open |
| OQ-18-003 | What warehouse, data mart, and reporting architecture should PayPlus use for MVP and post-MVP analytics? | Engineering / Data | High | Open |
| OQ-18-004 | What metadata format should represent data class, sensitivity, displayability, masking, Founder-settled indefinite retention, owner, approved purpose, access role, lineage, partner-sharing status, and model-use eligibility? | Data / Privacy / Security | High | Open |
| OQ-18-005 | What aggregation thresholds and output controls are required before partner reporting or clean-room collaboration? | Data / Privacy / Legal | High | Open |
| OQ-18-006 | What model registry, feature registry, monitoring, and audit-event structure should be required before AI/model-assisted decisioning? | Data / Engineering / Risk | High | Open |
| OQ-18-007 | Which model features or derived signals are prohibited from marketing, partner reporting, insurance-related targeting, credit scoring, or external activation? | Privacy / Legal / Risk | High | Open |
| OQ-18-008 | What owner-approved representation should capture current evidence, source-Archive visibility, access/masking, and evidence-to-readiness lineage without mutating the canonical source, obligation, or economic-Payee projection? | Engineering / Data / Product / Risk / Privacy | High | Open |
| OQ-18-009 | What final physical fields, projections, reason codes, correlation IDs, idempotency rules, and audit records should implement the confirmed separation of role-facing labels, evidence status, obligation readiness, linked case lifecycle, source-Archive visibility, and payment/payout records for DOC-06A/DOC-06B/DOC-06C owner flows? | Engineering / Data / Product / Privacy / Operations | High | Open |
| OQ-18-010 | What final referral identifiers, deeplink/QR token contract, attribution idempotency, qualification event mapping, entitlement/claim linkage, masking projection, correction controls, and audit records should implement the DOC-06B/DOC-13 Referral baseline? | Engineering / Data / Product / Privacy / Growth / Risk | High | Open |
| OQ-18-011 | What final reward-instrument schema, state mapping, credential-reference model, checkout/partner linkage, idempotency keys, unknown-result recovery, and field-level representation should implement the separate reward dimensions and lifecycle defined in DOC-13? | Engineering / Data / Product / Growth / Privacy / Operations | High | Open |
| OQ-18-012 | What final registration-attempt, identifier-claim, uniqueness, login-method, provider-identity, Fast Login, restricted-account, Account Activation, authentication Outcome/Resolution/Message/correlation, capability-aware Recovery attempt, HK phone challenge, five-label identity projection, provider-result/PayPlus-policy separation, duplicate-identity, admin reset/dual-approval, Payment Passcode Set/Change/Reset/recovery, preference, contact-change, privacy-request, protected-export, account-closure, route-event, reveal-audit, and retention-safe structures implement the accepted model without reserving identifiers before account creation, copying sensitive values into analytics, or auto-linking accounts by email? | Engineering / Data / Product / Privacy / Security / Operations | High | Open |
| OQ-18-013 | What final context-specific destination facts, immutable destination snapshots, source references, authorization boundaries, visibility projection, failure mapping, and audit structures implement the accepted product model without treating a saved profile or directory entry as payout truth? | Engineering / Data / Payments / Product / Privacy / Risk / Operations | High | Open |
| OQ-18-014 | What final catalog/default/preference/effective-set structures, configuration version links, availability categories, cross-device synchronization, protected-entry constraints, and privacy-safe events implement the DOC-06B `MORE-ROOT` baseline? | Engineering / Data / Product / Privacy / Operations | Medium | Open |
| OQ-18-015 | What final notification event/message/batch/source/template/route/correlation/delivery-attempt schema, state projection, deduplication, retention, and owner-permitted operational lookup model implements the DOC-06B/DOC-08 Notifications baseline without granting DOC-22 policy authority? | Engineering / Data / Product / Privacy / Operations | High | Open |

## 12. Acceptance Criteria

DOC-18 is acceptable when it defines:

- logical object families;
- material field metadata requirements;
- event taxonomy requirements;
- transaction state linkage expectations;
- audit-event requirements;
- analytics, warehouse, and data-mart boundaries;
- data lineage and derived-data handling;
- AI/model-readiness metadata;
- partner reporting and aggregation controls;
- clear ownership boundaries with DOC-12, DOC-13, DOC-14, DOC-15, DOC-16, DOC-17, DOC-19, and DOC-22.

This document should not become:

- a final database migration;
- a vendor-specific data warehouse design;
- a final model architecture;
- an AI coding prompt pack;
- a privacy policy;
- a security architecture;
- an admin dashboard specification.

## 13. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| 0.4.24 | 2026-08-13 | Product Documentation Team | Retired active Request/Linking/Receiving Info assumptions, aligned representation to owner-approved source, destination, payment, notification, and indefinite-retention boundaries, and preserved DOC-09/DOC-10/DOC-13 handoffs without adding schemas or mechanisms. |
| 0.4.23 | 2026-07-31 | Product Documentation Team | Added the precise future implementation marker for canonical Request identity and DOC-09 Payment Domain objects, invariants, semantic conditions, correlation, late confirmation, adjustments, and distinct Instruction/Checkout identities. |
| 0.4.22 | 2026-07-29 | Product Documentation Team | Added future data and audit requirements for capability-aware Recovery and explicit separation of authentication Outcome, Resolution Strategy, persistent status, Message/CTA, notification, and occurrence records. |
| 0.4.21 | 2026-07-28 | Product Documentation Team | Replaced the superseded four-label identity projection with five states; added HK phone challenge, provider-result/PayPlus-policy separation, passcode reset, admin reset/dual-approval, security notification, and correlation requirements. |
| 0.4.20 | 2026-07-28 | Product Documentation Team | Added durable future data/event requirements for separate Phone and Identity Verification, first-time versus later identity-change context, four-label projection, provider-pending deduplication, and Payment Passcode Set/Change/Reset modes. |
| 0.4.19 | 2026-07-28 | Product Documentation Team | Aligned future authentication data and event requirements with Entrance, Fast/Full Login, temporary non-reserving registration attempts, atomic restricted-account creation, Account Activation, session revocation, and the mandatory DOC-07 authentication outcome/message/correlation mapping mechanism. |
| 0.4.18 | 2026-07-27 | Product Documentation Team | Added future structures and events for unique primary email, explicit email/Google/Apple login methods, stable provider identity links, first-password setup, restricted-account creation, and financial-activation gates. |
| 0.4.17 | 2026-07-27 | Product Documentation Team | Added future notification event/message/batch/source lineage, category/presentation/domain/action separation, route targeting, delivery-attempt, preference, correlation, and audit requirements for the defined Notifications route family. |
| 0.4.16 | 2026-07-27 | Product Documentation Team | Added future object and privacy-safe event requirements for `MORE-ROOT`, approved shortcut catalog, current eligible default, account-level preferences, protected More, effective resolution, save/restore, availability, and destination handoffs. |
| 0.4.15 | 2026-07-27 | Product Documentation Team | Added future privacy-safe Pay+ action-sheet availability, selection, blocked-reason, and destination-handoff event requirements without defining technical payloads. |
| 0.4.14 | 2026-07-26 | Product Documentation Team | Added canonical-obligation versus per-user archive-projection separation, archived-list/detail/eligibility events, blocker reasons, current-evidence projection, and counterparty-safe restore requirements. |
| 0.4.13 | 2026-07-26 | Product Documentation Team | Added future archive-family, evidence-version lineage, archive-origin/restore-eligibility, parent archive/restore, access recheck, and archived-document audit requirements. |
| 0.4.12 | 2026-07-26 | Product Documentation Team | Added future canonical data separation for request lifecycle, role projections, request events, evidence status, obligation readiness, linked cases, archive visibility, and payment/payout linkage without one overloaded status field. |
| 0.4.11 | 2026-07-26 | Product Documentation Team | Added material-change and Receiving Info reveal/authentication event markers, clarified evidence/request/obligation/payment linkage, and limited the user-facing Bills Activity projection to payment-related transaction events. |
| 0.4.10 | 2026-07-23 | Product Documentation Team | Added future Receiving Info profile/version/proof/readiness, destination-snapshot, source-reference, visibility, linked-notification, authorization-freeze, failure, and audit requirements. |
| 0.4.9 | 2026-07-22 | Product Documentation Team | Added future object and event requirements for Account Information, reusable Identity Verification, contact changes, Payment Passcode Settings, trusted-device/session revocation, privacy requests, protected exports, and account closure. |
| 0.4.8 | 2026-07-22 | Product Documentation Team | Added future data/event markers for DOC-06B `ME-ROOT`, account/security/privacy navigation, payment-passcode-gated reveal auditability, preferences, Receiving Details, archived-evidence access, and logout. |
| 0.4.7 | 2026-07-21 | Product Documentation Team | Added future canonical reward-instrument markers for separate data dimensions, lifecycle projections, checkout/partner linkage, credential events, authoritative fulfilment, idempotency, unknown-result recovery, and operational auditability. |
| 0.4.6 | 2026-07-21 | Product Documentation Team | Added future Referral markers for entitlement-time quota reservation and terms snapshot, separate lifecycle dates, idempotent issuance and recovery, admin hold auditability, status projection, and route-scoped masked-phone visibility. |
| 0.4.5 | 2026-07-21 | Product Documentation Team | Added future Referral object, linkage, event, privacy-projection, qualification, claim, reward-issuance, and audit markers while separating sharing from recipient identity and registration attribution. |
| 0.4.4 | 2026-07-20 | Product Documentation Team | Added future data/event markers for multi-collection Offers, root placement, per-collection priority, payment-card/funding-leg offer evaluation, highest-user-value automatic Card Offer selection, separate coupon/voucher/discount application, quote recalculation, and audit linkage. |
| 0.1.0 | 2026-06-08 | Product Documentation Team | Replaced interim note with founder working baseline for data model ownership, field metadata, event taxonomy, lineage, analytics marts, AI/model-readiness metadata, partner reporting controls, and open questions. |
| 0.2.0 | 2026-06-12 | Product Documentation Team | Aligned data-model baseline with DOC-06 Bills tab requirements by adding obligation, contract/relationship, evidence source, participant linking, invitation, action, and no-auto-matching state/event expectations. |
| 0.3.0 | 2026-06-17 | Product Documentation Team | Aligned data-model baseline with DOC-06 Bills reminder list/detail routes by adding linked reminder objects, lifecycle states, soft-delete metadata, notification linkage, and reminder effectiveness events. |
| 0.4.0 | 2026-06-18 | Product Documentation Team | Added future DOC-18 update markers for DOC-06 Bills evidence detail/upload routes, active evidence versioning, archive-not-delete behavior, evidence status changes, and readiness-change audit events. |
| 0.4.1 | 2026-07-02 | Product Documentation Team | Added future data/event markers for DOC-06B `REQUESTS-NEW`, evidence-gated auto-send, counterparty lookup, sharing, and route handoff auditability. |
| 0.4.2 | 2026-07-03 | Product Documentation Team | Aligned future data-model marker with DOC-06B Instructions route by distinguishing payment instruction action alerts/tasks from ordinary bill/rent reminders. |
| 0.4.3 | 2026-07-06 | Product Documentation Team | Added future data/event markers for DOC-06B Payment Profile route, including tokenized cards, saved split-card profiles, allocation ratios, action-required profile state, and checkout/instruction return context. |
