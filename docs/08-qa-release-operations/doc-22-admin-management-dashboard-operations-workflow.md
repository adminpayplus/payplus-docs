---
document_id: DOC-22
title: Admin Management Dashboard & Operations Workflow
version: 0.25.0
status: Founder Working Baseline
owner: Operations / Product
reviewers:
  - Product Lead
  - Operations Lead
  - Payments Lead
  - Risk Lead
  - Compliance Lead
  - Privacy Lead
  - Security Lead
  - Engineering Lead
  - Data Lead
approvers:
  - Project Owner
  - Product Lead
  - Operations Lead
  - Compliance Lead
last_updated: 2026-08-14
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Specification
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification
  - DOC-15 Privacy, Data Protection & Record Retention Specification
  - DOC-16 Technical Architecture Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization, Authentication & Admin Control Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operational SOPs
---

# DOC-22 — Admin Management Dashboard & Operations Workflow

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-22` |
| **Title** | Admin Management Dashboard & Operations Workflow |
| **Version** | `0.25.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Operations / Product |
| **Reviewers** | Product Lead<br>Operations Lead<br>Payments Lead<br>Risk Lead<br>Compliance Lead<br>Privacy Lead<br>Security Lead<br>Engineering Lead<br>Data Lead |
| **Approvers** | Project Owner<br>Product Lead<br>Operations Lead<br>Compliance Lead |
| **Last Updated** | `2026-08-14` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Specification<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-16 Technical Architecture Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization, Authentication & Admin Control Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operational SOPs |

## 1. Purpose

## 2. Scope

DOC-22 describes only operational execution, configuration, queue and audit work that a formal owner has specifically permitted. It does not own or decide product policy, source/Evidence truth, payment or Payout truth, risk outcome, privacy/retention, architecture or security proof, route access, notification eligibility/delivery, or financial correction/reissue outcome. Those matters remain with DOC-05 through DOC-16, DOC-19, DOC-21 and the applicable specialist owner.

Operational execution must preserve DOC-16 trust boundaries, local authoritative ownership, durable cross-boundary handoff meaning, provider-controlled card-data restrictions, least privilege, segregation of duties, auditability, and non-authoritative projection rules. DOC-22 does not choose a deployment, API, event, schema, provider, security mechanism, retry model, or reconciliation design.

The active product is Payer-only. An economic Payee need not be a User. Request, Linking, To Receive, Receiving Info, Payee-user, production legacy data, readers, adapters, fallbacks and deep links are retired. DOC-22 must not restore them through configuration, queues, workflows or permissions.

## 3. Out of Scope

## 4. Admin User Roles

## 5. Admin Permission Model Summary

## 6. Admin Dashboard Overview

## 7. Operations Queues

### 7.1 Account Review
### 7.2 Intended-Payee/Destination Review
### 7.3 Evidence Review

Where a formal owner specifically permits an operational workflow, DOC-22 may execute it and record operational evidence. DOC-22 does not assign or override Evidence, readiness, risk, Payment, Payout, privacy, retention or Archive truth, and does not define queue contents, statuses, permissions, dispositions, Archive/Restore or version presentation.

Detailed representation belongs in DOC-18; user routes in DOC-06; Evidence verification in DOC-12; risk escalation in DOC-14.

### 7.4 Retired Request Identifier

No active Request Review Queue exists. The retired stable identifiers are documentation provenance only and create no runtime queue, action, permission, disposition, notification or delivery requirement.

No active Request lifecycle, state, delivery, reminder, sharing, linking, Archive or permission configuration exists. DOC-22 must not convert any owner outcome into a retired Request state.

### 7.5 Risk Workflow Handoff
### 7.6 Duplicate-Detection Workflow Handoff
### 7.7 Dispute Workflow Handoff

DOC-11 owns adjustment/case meaning. DOC-22 may execute a specifically permitted workflow and must not redefine case lifecycle, approvals, holds or outcomes.
### 7.8 Clarification Workflow Handoff
### 7.9 Failed-Payment Workflow Handoff
### 7.10 Payout-Exception Workflow Handoff

DOC-10 and specialist owners determine destination/Payout exception meaning. DOC-22 does not create a Receiving Info profile, user-facing status or exception policy.
### 7.11 Refund/Reversal Workflow Handoff
### 7.12 Compliance-Escalation Workflow Handoff
### 7.13 Campaign and Promotion Workflow Handoff
### 7.14 Reward-Entitlement Workflow Handoff
### 7.15 Authentication and Account Activation Review

DOC-19, DOC-21 and applicable identity/security owners determine authentication, recovery, session, status, proof, access and audit requirements. DOC-22 may execute only their expressly permitted workflow and must not expose secrets, change security truth or define a recovery, outcome, message, queue, role, approval, technical or notification policy.

## 8. Admin Review Workflows

## 9. User Management Workflows

## 10. Evidence and Bill Verification Workflows

## 11. Payment Operations Workflows

DOC-09 owns Payment Instruction and Checkout semantics. DOC-22 may execute a specifically owner-permitted workflow using approved facts; it must not define partial funding, instruction status, quotes, alerts, holds, cancellation, expiry or escalation policy.

## 12. Payout and Reconciliation Workflows

## 13. Refund, Cancellation, and Chargeback Operations

## 14. Risk, Fraud, AML, and Anti-Cashout Operations

## 15. Dispute and Clarification Management

## 16. Internal Notes and Case Management

## 17. Admin Actions and Status Changes

## 18. Campaign, Promotion, Coupon, Voucher, Reward, and Referral Operations

DOC-13 owns promotion, offer, referral, qualification, entitlement and Reward truth. DOC-22 may execute an expressly owner-permitted operational workflow and record approved evidence only; it does not define campaign, eligibility, placement, entitlement, Reward, approval or presentation policy.

### 18.1 Dashboard Shortcut and Placement Configuration

DOC-06B owns Home routes, shortcuts, entry behaviour and presentation. DOC-13 owns Offer truth. Any operational configuration must be expressly permitted by those owners; DOC-22 cannot create a route, destination, availability rule, placement, priority, eligibility, CTA, status or presentation requirement.

#### 18.1.0 Public Entrance Content Configuration

DOC-13 and other formal owners determine any public-content truth. DOC-22 may execute an expressly owner-permitted operational workflow without creating publication, placement, targeting, accessibility, timing, approval, status, route, CTA, Copy or retention requirements.

#### 18.1.1 Pay+ Action Availability Configuration

DOC-06B owns Pay+ actions, availability and presentation. DOC-22 may not create, configure, rename, order or redirect an action; retired Request Payment remains unavailable.

### 18.2 Reminder Default Configuration

DOC-06C owns reminder behaviour and DOC-08 notification behaviour. DOC-22 may execute only an expressly owner-permitted workflow and does not define reminder timing, eligibility, channel or preference policy.

### 18.3 Retired Request Configuration

No active Request creation or delivery configuration exists. DOC-22 must not create a replacement action, delivery path, recipient model, queue or historical-runtime reader.

### 18.4 Payment Profile and Tokenized Card Configuration

DOC-06B owns route presentation, DOC-09 payment behaviour, DOC-16 the provider-controlled card-data architecture boundary and DOC-19 security controls. DOC-22 may execute an owner-permitted workflow using approved facts only; it does not define card limit, confirmation, step-up, status, lifecycle, access, audit or tokenization policy and must not expose raw PAN or card-verification values.

### 18.5 Offers Collection, Placement, and Application Configuration

DOC-13 owns Offers, eligibility, entitlement, placement truth and all promotion decisions; DOC-09 owns payment behaviour; DOC-06B owns route presentation. DOC-22 may execute only an expressly owner-permitted operational workflow using approved facts. It does not define eligibility, collection, placement, priority, targeting, application, benefit, audit, data or event requirements.

### 18.6 Referral Program, Campaign, and Qualification Configuration

DOC-13 owns Referral, qualification, entitlement and Reward truth; DOC-06B owns route presentation; DOC-15 owns privacy; and DOC-18 owns representation. DOC-22 may execute an expressly owner-permitted operational workflow only. It does not define campaign, qualification, entitlement, reward, timing, status, access, notification, audit, data or event policy.

### 18.7 Reward Instrument and Fulfilment Operations

DOC-13 owns Reward truth and any lifecycle outcome. DOC-22 may execute only an expressly owner-permitted operational workflow; it does not define actions, expiry, status, credential access, user notices or fulfilment policy. DOC-06B owns presentation, DOC-15 privacy, DOC-19 security and DOC-18 representation.

### 18.8 Me Route, Account-Control, and Receiving Info Configuration

`ME-ROOT` route behaviour belongs in DOC-06B. Consumer Receiving Info is retired. Account, privacy, security, notification, destination, Evidence, risk, Payout, Archive and representation requirements remain with DOC-08, DOC-10, DOC-12, DOC-14, DOC-15, DOC-18, DOC-19 and the applicable formal owner. DOC-22 may execute only a specifically owner-permitted operational workflow and cannot establish a route, status, Archive/Restore rule, profile, access rule, notification or override policy.

### 18.9 Notification Configuration and Operations

DOC-08 owns notification identity, eligibility, recipients, channels, templates, preferences and delivery. DOC-06B owns routes; domain owners own status; DOC-15 owns approved-purpose retention/access; DOC-18 owns representation. DOC-22 may execute an expressly owner-permitted workflow and record operational evidence without defining an event, category, route, status, channel, template, schedule, provider, retention or notification mechanism.

## 19. Audit Logging Requirements

## 20. Notifications and Escalations

## 21. Dashboard Screen Inventory

## 22. Reporting and Export Requirements

## 23. Security and Access Control Requirements

DOC-16 owns architecture and trust-boundary requirements, DOC-19 owns security and access policy, and DOC-15 owns approved-purpose privacy and retention requirements. DOC-22 may execute an expressly owner-permitted operational workflow only; it cannot define access, masking, reveal, credential, evidence, payment, Payout, risk, promotion, support or audit policy.

## 24. Privacy and Data Handling Requirements

DOC-15 owns data classification, approved-purpose access, masking and retention requirements; DOC-18 owns approved representation. DOC-22 may execute only a specifically owner-permitted workflow using approved facts and must not establish fields, visibility, queue, reveal, export, audit, evidence, deletion or permission requirements.

## 25. Monitoring and Incident Response Linkage

DOC-21 owns monitoring, incident, support, escalation and closure evidence. DOC-22 may perform only an expressly owner-permitted operational action and record its approved result. It must preserve the local authoritative fact, must not treat a handoff or projection as domain truth, and must route retry, recovery, reconciliation or security concerns to the applicable DOC-16/DOC-17/DOC-18/DOC-19 and domain owners.

## 26. MVP Acceptance Criteria

Detailed acceptance and UAT evidence belong to DOC-20. This document supplies only the owner-permitted execution boundary: an Admin workflow may execute an approved owner outcome, but cannot create source truth, acceptance criteria, route, presentation, publication, notification, data, permission, audit or security requirements.

## 27. Open Questions

Exact Admin workflow, queue, permission, approval, technical, monitoring and implementation detail remains with the applicable formal owners. These open matters do not authorize DOC-22 to establish product, security, privacy, route, notification, source, payment, Payout, risk or representation policy.

## 28. Revision History

| Version | Date | Summary |
| --- | --- | --- |
| 0.25.0 | 2026-08-14 | Aligned owner-permitted Admin execution with the Stage 9-passed DOC-16 architecture, provider-controlled card-data, authoritative-owner, durable-handoff, monitoring and evidence boundaries without adding Admin policy, mechanisms, queues, statuses, permissions, schemas or providers. |
| 0.24.0 | 2026-08-12 | Reframed DOC-22 as owner-permitted operational execution only; retired Request configuration/queue meaning; and aligned Admin scope with the Payer-only baseline. |
| 0.23.0 | 2026-08-06 | Defined independent Feature Management and central Entrance Carousel Management for Promotion/Feature-only public content, including minimum Feature fields, source-reference ownership, `Use Promotion Period` and manual placement dates, one-priority-plus-manual ordering, five-item capacity, preview/publication/removal, optional-action boundaries, non-personalization, and source-change suspension/republication without inventing technical schema, events, permissions, or scheduler mechanics. |
| 0.22.0 | 2026-08-05 | Added approved Admin selection, ordering, rotation, publication-quality, and audit controls for source-owned Important Notice signals and Admin-selected Hot Offers; preserved canonical Offer truth and restriction boundaries; and established bounded DOC-06B handoffs for Home capacity, zero-state presentation, and navigation. |
| 0.21.0 | 2026-07-29 | Aligned future authentication administration with capability-aware Recovery, the Outcome/Resolution/Message/CTA separation, controlled Support recovery cases, dual approval, and explicit administrator prohibitions while leaving security and operational details TBC. |
| 0.20.0 | 2026-07-28 | Added future admin controls for the five-state identity model, prohibited direct verification/passcode bypass, required dual approval for Verified-to-Not-Verified reset, recorded reset audit fields, preserved support-assisted passcode-recovery TBCs, and added the configurable HK$3,000 step-up baseline. |
| 0.19.0 | 2026-07-28 | Added future operational controls for temporary registration attempts, authentication outcome/message/correlation lookup, account-activation conflicts, Fast Login/session handling, and approved public Entrance content while preserving DOC-07 ownership of exact IDs and messages. |
| 0.18.0 | 2026-07-27 | Added future admin and support markers for unique-primary-email conflicts, explicit provider login-method links, first-password state, final-login-method protection, and restricted-account financial-activation gates. |
| 0.17.0 | 2026-07-27 | Added future admin requirements for notification event/message/batch/source traceability, category and signal separation, lookup, templates, channels, preferences, delivery attempts, current-state actions, retention, and audit. |
| 0.16.0 | 2026-07-27 | Aligned future admin controls with defined `MORE-ROOT` catalog/default management, 8-slot maximum, protected More access, eligibility precedence, account-level preferences, current-default restore, configuration versioning, and destination-boundary protection. |
| 0.15.0 | 2026-07-27 | Added future Pay+ action availability configuration, hidden-versus-disabled rules, fixed semantic boundaries, destination-gate protection, and audit requirements. |
| 0.14.0 | 2026-07-26 | Added future per-user archive-projection, archived-obligation blocker/eligibility, current-evidence cascade, canonical-record protection, and operational audit requirements; admin restore-on-behalf remains to be defined in the full DOC-22. |
| 0.13.0 | 2026-07-26 | Added future archive-family controls, separate archive/history descriptors, sole-current-evidence protection, parent archive/restore, non-restorable expiry/history, access, retention, and audit requirements. |
| 0.12.0 | 2026-07-26 | Added future admin requirements separating canonical request lifecycle, role projections, events, evidence, readiness, linked cases, payment/payout status, and archive visibility, plus the canonical linked-case lifecycle. |
| 0.11.0 | 2026-07-23 | Added future Receiving Info method configuration, profile/proof review, readiness, version/archive, snapshot separation, payout-failure classification, linked notification, save invitation, and audit requirements. |
| 0.10.0 | 2026-07-22 | Added future operations markers for identity-provider exceptions, support-assisted recovery, cross-channel contact changes, privacy-request queues, protected exports, account-closure blockers/finality, trusted-device revocation, and optional-versus-mandatory privacy controls. |
| 0.9.0 | 2026-07-22 | Added future admin and operations markers for permanent `ME-ROOT`, protected core controls, optional-row enablement, account action-required handling, Receiving Details, archived-evidence access, reveal/privacy auditability, and the separate More shortcut-management boundary. |
| 0.8.0 | 2026-07-21 | Added future Reward operations markers for launch-supported partner/miles readiness, separate data dimensions, lifecycle and exception queues, authoritative/idempotent fulfilment, expiry configuration, hold-versus-expiry follow-up, and credential access controls. |
| 0.7.0 | 2026-07-21 | Added future Referral admin markers for entitlement-time quota reservation and terms snapshot, separate campaign/claim/use dates, idempotent claim oversight, and authorized hold/release handling for exceptional `Under Review` presentation. |
| 0.6.0 | 2026-07-21 | Added future Referral Program, campaign, role-sensitive offer, qualification, finality, quota, validity, privacy-safe review, entitlement hold/release/reversal, attribution-correction, and audit configuration markers. |
| 0.5.0 | 2026-07-20 | Added future admin markers for multi-collection Offers, primary root placement, duplicate suppression and override, per-collection priority, payment-method-sensitive application mode, highest-user-value comparison, and audit controls. |
| 0.1.0 | 2026-06-17 | Added DOC-06 reminder default configuration hooks for bill/rent reminder timing, category gating, channel linkage, and audit logging. |
| 0.2.0 | 2026-06-18 | Added future DOC-22 update markers for admin handling of DOC-06 Bills evidence detail/upload routes, evidence statuses, readiness impact, archive-not-delete behavior, prior evidence access, notifications, and audit logging. |
| 0.3.0 | 2026-07-02 | Added future DOC-22 configuration markers for DOC-06B request creation, evidence-gated request delivery, resend/reminder limits, sharing channels, and audit logging. |
| 0.4.0 | 2026-07-06 | Added future admin configuration and operations markers for DOC-06B Payment Profile route, tokenized card status, payment profile action-required handling, max 6-card payment/profile limit, default confirmation behavior, optional user-enabled payment-passcode confirmation, and audit logging. |
