---
document_id: DOC-18
title: Data Model, Transaction State, Audit Event & Reporting Specification
version: 0.1.0
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
last_updated: 2026-06-08
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
- evidence/document;
- evidence extraction layer;
- normalized evidence field;
- user correction;
- verification signal;
- final evidence snapshot;
- request status history;
- payment quote;
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
- offer rule;
- promotion quote;
- promotion quote reservation;
- qualification accumulator;
- benefit entitlement;
- reward instrument;
- redemption or fulfilment record;
- referral relationship;
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
| Evidence events | upload, OCR processed, field extracted, user corrected, verification passed, mismatch found, duplicate detected, evidence snapshot finalized. |
| Request events | draft created, submitted, sent, viewed, accepted, rejected, disputed, clarification requested, expired, cancelled. |
| Payment events | quote created, quote revalidated, instruction created, funding leg created, authorization attempted, authorized, failed, captured, payment completed. |
| Payout events | settlement received, payout ready, payout held, payout released, payout submitted, payout completed, reconciliation matched, exception opened. |
| Risk events | rule triggered, risk score assigned, step-up required, manual review opened, hold applied, block applied, override approved, escalation recorded. |
| Promotion events | offer viewed, eligibility evaluated, promotion quote created, benefit reserved, entitlement earned, reward issued, reward redeemed, reward reversed. |
| Communication events | notification queued, sent, delivered, read, failed, opted in, opted out, template version applied. |
| Admin events | queue assigned, evidence viewed, action taken, export requested, sensitive field revealed, override reason captured. |
| Analytics/model events | aggregate created, model feature refreshed, model run executed, AI-assisted recommendation shown, human review outcome recorded where approved. |

Each event should capture event ID, event type, actor, role, timestamp, source object, affected object, previous state where applicable, new state where applicable, reason code where applicable, correlation ID, request ID or case ID where applicable, and audit classification.

## 7. Transaction State and Linkage

DOC-18 should maintain linkages between:

- request;
- evidence;
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
- support/dispute case;
- admin review case;
- audit event.

DOC-18 must include data structures for DOC-09 user payment instruction, payment instruction funding leg, deferred funding date, selected payee transfer date, reminder/action task, partial funding status, partial payout linkage, remaining unpaid amount, payment quote revalidation, promotion quote reservation, and changed-term acknowledgement.

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
| 0.1.0 | 2026-06-08 | Product Documentation Team | Replaced interim note with founder working baseline for data model ownership, field metadata, event taxonomy, lineage, analytics marts, AI/model-readiness metadata, partner reporting controls, and open questions. |
