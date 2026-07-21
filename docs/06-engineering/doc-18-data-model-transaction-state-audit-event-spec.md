---
document_id: DOC-18
title: Data Model, Transaction State, Audit Event & Reporting Specification
version: 0.4.6
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
last_updated: 2026-07-21
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-05 Master PRD & Feature Requirement Index
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
| Human review | Sensitive AI/model-assisted outcomes should support reason codes, reviewability, override controls, and audit trails. |

## 4. Core Object Families

DOC-18 should define logical structures for at least the following object families:

- user account;
- payer profile;
- payee profile;
- KYC/KYB verification reference;
- authentication, device, OTP, passcode, and material account-change event;
- payment request;
- request participant mapping;
- participant invitation or linking request;
- obligation record;
- contract or relationship record;
- evidence source record;
- evidence/document;
- evidence extraction layer;
- normalized evidence field;
- user correction;
- verification signal;
- final evidence snapshot;
- request status history;
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
- retention policy;
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
| Account events | registration, login, logout, new-device login, dormant reauthentication, contact change, credential change. |
| Evidence events | upload started, upload submitted, OCR processed, field extracted, user corrected, verification passed, mismatch found, duplicate detected, status changed, evidence snapshot finalized, evidence version created, evidence archived. |
| Request events | draft created, creation started, existing bill/rent selected, submitted for evidence verification, evidence verified and auto-sent, sent, shared, viewed, accepted, rejected with reason, expired, cancelled, archived, restored. |
| Participant-linking events | invitation created, app link generated, QR link generated, WhatsApp deeplink generated, invitation sent, viewed, accepted, declined, expired, linking completed, linking revoked. |
| Payment events | quote created, quote revalidated, instruction created, funding leg created, authorization attempted, authorized, failed, captured, payment completed. |
| Payment profile events | card add started, tokenization returned, card nickname edited, default card changed, card removed or archived, profile created, profile edited, profile starred/unstarred, profile marked action-required, profile selected for checkout/instruction, profile issue displayed. |
| Payout events | settlement received, payout ready, payout held, payout released, payout submitted, payout completed, reconciliation matched, exception opened. |
| Risk events | rule triggered, risk score assigned, step-up required, manual review opened, hold applied, block applied, override approved, escalation recorded. |
| Promotion events | offer displayed, offer viewed, collection filtered, eligibility evaluated, competing Card Offers compared, highest-user-value Card Offer auto-selected, coupon/voucher/discount selected, promotion quote created or recalculated, benefit reserved, entitlement earned, reward issued, reward redeemed, reward reversed. |
| Referral events | share action initiated, referral link copied, QR displayed, registration code validated, attribution created, qualification progressed or decided, referral entitlement created or held, claim attempted or completed, reward issued, reward reversed or clawed back. Share events must not imply delivery, recipient identity, or attribution. |
| Communication events | notification queued, sent, delivered, read, failed, opted in, opted out, template version applied. |
| Admin events | queue assigned, evidence viewed, action taken, export requested, sensitive field revealed, override reason captured. |
| Analytics/model events | aggregate created, model feature refreshed, model run executed, AI-assisted recommendation shown, human review outcome recorded where approved. |

Each event should capture event ID, event type, actor, role, timestamp, source object, affected object, previous state where applicable, new state where applicable, reason code where applicable, correlation ID, request ID or case ID where applicable, and audit classification.

## 7. Transaction State and Linkage

DOC-18 should maintain linkages between:

- request;
- obligation;
- contract or relationship record where applicable;
- evidence;
- evidence source;
- payer;
- payee;
- participant invitation or linking record where applicable;
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

Referral linkage must preserve the sequence `referrer -> user-linked code/reference -> campaign and role-specific offer -> referee registration attribution -> qualification -> beneficiary-specific entitlement -> issued reward instrument`. Referrer and referee entitlements may use the same campaign but must remain separate records with explicit beneficiary role. Referral sharing must not create a referee, relationship, or invitation lifecycle before valid registration attribution.

Future DOC-18 drafting must also specify entitlement-time quota/value reservation, campaign/offer/benefit/terms snapshot, separate campaign-end/claim-deadline/reward-usage-expiry fields, one-entitlement-to-at-most-one-instrument idempotency, duplicate/concurrent/uncertain claim recovery, and administrator hold/release/reversal audit linkage. User-facing Referral projections must remain distinct from canonical internal states, and masked referee phone must be projected only to the permitted `REFERRAL-ROOT` progress context.

DOC-18 must include data structures for DOC-09 user payment instruction, payment instruction funding leg, deferred funding date, selected payee transfer date, payment instruction action alert/task, partial funding status, partial payout linkage, remaining unpaid amount, payment quote revalidation, promotion quote reservation, and changed-term acknowledgement.

DOC-18 must include data structures for DOC-06B/DOC-09 tokenized card and payment profile behavior, including card token/reference, permitted masked metadata, card nickname, card status, default-card marker, saved split-card profile name, card slots, stored ratios, setup/reference amount, starred/frequent marker, action-required state, soft-delete/archive metadata, checkout/instruction return context, and related audit events.

DOC-18 must include data structures linking each applied payment-method-sensitive Card Offer to the selected payment card or funding leg, the competing eligible Offer IDs, approved user-value comparison result, automatic-selection reason, affected funded amount, separate coupon/voucher/discount application, promotion quote version, and revalidation event. The same Offer ID may have multiple discovery-collection memberships but should remain one underlying offer object.

DOC-18 must also include data structures for DOC-06C ordinary bill/rent reminders, including reminder ID, linked obligation ID, reminder source type, cycle, offset or custom date/time, active/inactive/expired/deleted status, custom override marker, soft-delete/audit metadata, notification linkage, and events for reminder creation, edit, disable, deletion, firing, opening, dismissal, and payment-start attribution.

DOC-18 must also distinguish:

- obligation records, such as bill, invoice, fee, rent, domestic service, or approved payment obligation;
- contract or relationship records, such as tenancy, employment, service agreement, or other ongoing relationship evidence;
- evidence source records, such as invoice, bill, tenancy agreement, stamp duty document, CR109, rent demand, HKHA tenancy card, carpark invoice, property management notice, upload, QR-derived record, or manual entry;
- participant linking records, which connect platform users to an obligation only after approved user or operational action.

Automatic user-to-user matching must not be modeled as a default UX state. Evidence-to-payee validation, duplicate detection, payout validation, and risk analysis may run as system checks, but shared payer/payee visibility requires an approved participant-linking state.

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
- retention and deletion expectations for model inputs and outputs;
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
| OQ-18-001 | What final logical and physical schema should be used for core request, evidence, payment, payout, promotion, risk, audit, and analytics objects? | Engineering / Data | High | Open |
| OQ-18-002 | What event taxonomy, reason-code library, and correlation ID model should be used before AI build-execution conversion? | Engineering / Data / Operations | High | Open |
| OQ-18-003 | What warehouse, data mart, and reporting architecture should PayPlus use for MVP and post-MVP analytics? | Engineering / Data | High | Open |
| OQ-18-004 | What metadata format should represent data class, sensitivity, displayability, masking, retention, owner, approved purpose, access role, lineage, partner-sharing status, and model-use eligibility? | Data / Privacy / Security | High | Open |
| OQ-18-005 | What aggregation thresholds and output controls are required before partner reporting or clean-room collaboration? | Data / Privacy / Legal | High | Open |
| OQ-18-006 | What model registry, feature registry, monitoring, and audit-event structure should be required before AI/model-assisted decisioning? | Data / Engineering / Risk | High | Open |
| OQ-18-007 | Which model features or derived signals are prohibited from marketing, partner reporting, insurance-related targeting, credit scoring, or external activation? | Privacy / Legal / Risk | High | Open |
| OQ-18-008 | What final data objects, fields, events, lineage, and audit records should support DOC-06C evidence detail/upload routes, one active evidence set, evidence versioning, archive-not-delete behavior, and evidence-status-to-readiness changes? | Engineering / Data / Product / Risk | High | Open |
| OQ-18-009 | What final data objects, states, events, reason codes, correlation IDs, and audit records should support DOC-06B `REQUESTS-NEW`, evidence-gated auto-send, counterparty lookup, request sharing, reminder events, and return handoffs with DOC-06C Bills routes? | Engineering / Data / Product / Privacy / Operations | High | Open |
| OQ-18-010 | What final referral identifiers, deeplink/QR token contract, attribution idempotency, qualification event mapping, entitlement/claim linkage, masking projection, correction controls, and audit records should implement the DOC-06B/DOC-13 Referral baseline? | Engineering / Data / Product / Privacy / Growth / Risk | High | Open |

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
