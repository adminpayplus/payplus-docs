---
document_id: DOC-05
title: Master PRD & Feature Requirement Index
version: 0.18.24
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-07-26
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-05 - PayPlus Master Product Requirements Document

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-05` |
| **Title** | Master PRD & Feature Requirement Index |
| **Version** | `0.18.24` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-07-26` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-02 Business Model & Unit Economics<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines the master product requirements for PayPlus.

PayPlus is an evidence-backed payment platform that allows payers and payees to create, view, link, authorize, and track bill, invoice, fee, rent, domestic service, and other approved obligation payment requests.

This document establishes the MVP product scope, core roles, required flows, controls, exclusions, and acceptance criteria.

---

## 2. Product Summary

PayPlus enables a user to make or request a payment when the payment is supported by a bill, invoice, fee, rent, tenancy document, agreement, employment/service record, statement, or other acceptable evidence.

The MVP supports both:

1. **Payer-created payment flow**
   - A payer creates a payment request and pushes a payment to a payee.

2. **Payee-created payment request flow**
   - A payee creates an evidence-backed payment request and sends it to a payer for review and payment.

Both flows are core MVP features.

Tenancy and rent payments are also MVP scope, subject to rent-specific evidence, payee verification, relationship, risk, limit, and review controls.

Domestic helper, driver, and personal service payments are MVP scope where supported by employment, service, invoice, fee, salary, or approved obligation evidence.

PayPlus is not a wallet, stored-value account, cashout product, open-loop money transfer product, or arbitrary peer-to-peer payment service.

PayPlus is also intended to be data-engine ready by design. MVP features should create structured, classified, auditable, and purpose-linked data that can support service operation, risk control, product analytics, commercial reporting, consented personalization, and future approved AI/model improvement. This does not make AI marketing automation, offsite advertising activation, user-level partner data sharing, credit scoring, or insurance underwriting part of MVP scope.

---

## 3. MVP Scope

### 3.1 In Scope

The MVP includes:

- payer account registration and login;
- payee account registration and login;
- payer-created payment requests;
- payee-created payment requests;
- evidence-backed bill, invoice, fee, tenancy, rent, domestic service, or document upload;
- AI/OCR-assisted evidence capture, autofill, user correction, verification, and review routing where enabled;
- payer and payee visibility into linked payment records where both sides are platform users and linking is approved;
- linking between bill/request/payment records, with duplicate detection and payee/payout validation;
- payer review and authorization before payment;
- admin review and operational controls;
- payment status tracking;
- request status tracking;
- audit history;
- receipt or confirmation records;
- basic notifications;
- sandbox or production-ready payment integration design;
- clear prohibition of wallet, stored balance, cashout, and unsupported P2P use cases.

### 3.1.1 MVP Gating and Configuration

Confirmed MVP scope does not mean every function must be enabled for every user, category, payee type, or launch phase.

The MVP must support independent enablement or disablement of major modules, including:

| Module or Capability | Gating Requirement |
|---|---|
| Payee-created requests | Enable by payee, category, risk tier, and control readiness. |
| Rent and tenancy payments | Enable only when rent evidence, landlord/payee verification, limits, monitoring, and manual review rules are ready. |
| Payment methods | Enable only when approved by PSP/acquirer and compliance review. |
| Payout methods | Enable only when payout provider, rail, timing, exception handling, and reconciliation are ready. |
| Fees and promotions | Enable only when DOC-13 promotion quote, entitlement, discount, coupon, voucher, reward, disclosure, accounting, tax, commercial, and reporting treatment is confirmed. |
| OCR or document AI | Enable by category, payee type, risk tier, document type, and provider readiness; manual or assisted review may be used until automation is approved. |
| Multi-card funding | MVP scope; support up to 6 credit cards per payment/profile, with related controls configurable where applicable. |
| Tokenized cards and saved payment profiles | MVP scope; DOC-06B defines the user route shell, DOC-09 defines checkout use, and DOC-19 defines tokenization/security mechanics. |
| User payment instruction | MVP scope for pending pay-later setup and incomplete payment continuation where DOC-06B route shell, DOC-09 funding rules, action-alert routing, partial funding, and payout controls are ready. |
| Data and AI readiness | Require structured events, field classification, lineage, auditability, consent/preference state, approved-purpose metadata, and model-use eligibility metadata where relevant; advanced model automation and external activation remain future-gated. |

Current launch assumptions:

- initial launch jurisdiction is Hong Kong;
- acquirer is undecided;
- card payments are expected to be treated as bill payment or ordinary online card purchase, subject to acquirer confirmation;
- PayPlus expects to seek an appropriate or special MCC from the selected acquirer;
- payouts are expected to be made from the PayPlus operating bank account after upstream settlement;
- Hong Kong payout rails include FPS, cheque, and EPS, with final operating-bank setup to be confirmed;
- payment gateway settlement is expected to be T+1 to T+3, with payout on the same day after upstream settlement;
- individual eKYC is expected through a service provider such as Jumio, with name verification, SMS phone verification, email capture, and ID copy submission;
- business KYB is expected to require a Business Registration document and owner ID;
- candidate notification channels are app notifications, push notifications, email, SMS, and WhatsApp;
- request delivery may use in-app message, app link, WhatsApp deeplink, QR code, or other approved channel;
- Pay+ `Request Payment` and the Requests `+ Create Request` action route to DOC-06B `REQUESTS-NEW`, which must link to an evidence-backed bill, fee, rent, tenancy, invoice, or approved obligation before sending;
- receipt, payment, account, tax, and audit record retention is expected to be 7 years, subject to final privacy and legal review;
- exact fee rates, fee allocation, promotion, coupon, voucher, reward, entitlement, refund, and reversal treatment remain to be confirmed and should be admin-configurable where applicable; multi-card card-count cap is 6 for MVP.

### 3.1.2 Requirement ID Approach

This founder working baseline may describe requirements in concise natural language.

Before AI build-execution conversion or implementation planning, core product requirements, business rules, controls, and testable acceptance criteria should receive stable IDs aligned with DOC-00.

---

### 3.2 Out of Scope for MVP

The MVP does not include:

- user wallet balances;
- stored-value accounts;
- cash withdrawal;
- cashout to self;
- unsupported peer-to-peer transfers;
- crypto payments;
- lending or credit issuance;
- automatic recurring payments unless separately approved;
- deferred or incomplete user payment instruction for single-card and split-card payment is in scope under DOC-06B/DOC-09 and is not an automatic recurring payment;
- marketplace escrow;
- investment, savings, or deposit accounts;
- open-loop funds transfer unrelated to a bill or evidence-backed obligation;
- fully automated compliance approval without admin or risk controls.

---

## 4. Product Principles

| Principle | Requirement |
|---|---|
| Evidence-backed payments | Every payment must be linked to a bill, invoice, fee, rent, tenancy, agreement, employment/service record, statement, or acceptable proof of obligation. |
| Two-sided visibility | Both payer and payee should be able to view the linked bill/request/payment when both are platform users. |
| Authorization required | A payer must authorize payment before funds are charged or moved. |
| No wallet behavior | PayPlus must not create stored balances or user-controlled cash accounts. |
| No arbitrary P2P | PayPlus must not support unsupported person-to-person transfers without evidence. |
| Traceability | Each payment must be traceable to its request, evidence, payer, payee, and status history. |
| Compliance first | Product behavior must remain within approved regulatory and partner constraints. |
| Data-engine readiness | Material product actions should create structured events and classified data suitable for governed analytics, reporting, and future approved AI/model improvement. |
| Trust-preserving intelligence | Analytics, personalization, partner reporting, and AI use must preserve PayPlus product boundaries, privacy controls, consent rules, role-based visibility, and auditability. |

---

## 5. User Roles

| Role | Description | MVP Login? |
|---|---|---|
| Payer | User who reviews, authorizes, and makes payment. | Yes |
| Payee | User who receives payment or creates payment requests. | Yes |
| Admin / Operations | Internal user who reviews requests, evidence, risk, payee details, and exceptions. | Yes |
| System | Automated services handling status updates, notifications, duplicate detection, payee/payout validation, record linking, and audit events. | No |

---

## 6. Core MVP Flows

## 6.1 Payer-Created Payment Flow

The payer-created flow allows a payer to initiate a payment to a payee.

### Flow

1. Payer logs in.
2. Payer creates a new payment request.
3. Payer selects or enters payee details.
4. Payer adds payment amount, due date, category, and description.
5. Payer uploads or links evidence.
6. System processes evidence using OCR/document AI where enabled.
7. System autofills eligible fields and lets payer review or correct them.
8. System validates evidence, validates payee/payout details where required, checks duplicates, and routes red flags to review.
9. System creates a payment request record.
10. Payer may proceed to payment after eligibility gates and authorization; payee acceptance is not required by default for payer-created payment.
11. Payee may be represented by a valid non-user payee record or invited/linked through an approved user-initiated or user-accepted flow.
12. Admin/system reviews request and evidence according to configured controls.
13. Payer authorizes payment.
14. Payment is processed through approved payment partners.
15. Payee receives payment according to approved settlement/payout rules.
16. Both payer and payee can view the linked payment record when both are users and linking is approved.
17. System stores receipt, status history, and audit trail.

---

## 6.2 Payee-Created Payment Request Flow

The payee-created flow allows a payee to request payment from a payer.

### Flow

1. Payee logs in.
2. Payee creates a payment request.
3. Payee enters payer information or selects an existing payer.
4. Payee adds amount, due date, category, and description.
5. Payee uploads or links evidence, such as invoice, bill, fee notice, tenancy agreement, employment/service record, or statement.
6. System processes evidence using OCR/document AI where enabled.
7. System autofills eligible fields and lets payee review or correct them.
8. System validates evidence, validates payee/payout details where required, checks duplicates, and routes red flags to review.
9. System creates a payment request record.
10. Payer is notified or invited to view the request.
11. Payer logs in or registers.
12. Payer reviews the request, evidence summary, amount, payee details, and required disclosures.
13. Payer accepts or rejects the request, with rejection reason where required.
14. If accepted, payer authorizes payment.
15. Payment is processed through approved payment partners.
16. Payee receives payment according to approved settlement/payout rules.
17. Both payer and payee can view the linked bill/request/payment record.
18. System stores receipt, status history, and audit trail.

---

## 7. Evidence Requirements

Every payment request must be supported by acceptable evidence.

Detailed bill category, document AI/OCR, extracted field, autofill, user correction, duplicate detection, verification outcome, and payee/payout validation requirements belong in DOC-12.

### 7.1 Acceptable Evidence Types

MVP evidence may include:

- bill;
- invoice;
- tenancy agreement;
- rent demand;
- payment statement;
- service agreement;
- official notice;
- contract;
- uploaded PDF or image;
- manually entered bill details with supporting document;
- other admin-approved proof of payment obligation.

---

### 7.2 Evidence Rules

| Rule | Requirement |
|---|---|
| Evidence required | A payment or payment request cannot proceed without evidence supporting the obligation unless an approved exception applies. |
| Evidence linked | Evidence must link to the bill/rent/tenancy obligation. A request references the same evidence-backed context where a request is used. |
| OCR/autofill support | Where enabled, system should extract evidence fields and autofill request fields for user review. |
| User correction | Users must be able to review and correct autofilled fields before submission. |
| Verification outcome | Evidence must have a verification outcome or approved exception before payment eligibility. |
| Request delivery gate | Requests created through DOC-06B `REQUESTS-NEW` must not be sent or shown to the receiver before required evidence is verified or approved by exception. |
| Duplicate/reuse detection | System should detect duplicate or reused evidence and route configured red flags to review. |
| Payer review | Payer must be able to review evidence before authorizing payment. |
| Payee review | Payee must be able to view evidence attached to their own created requests or linked received payments. |
| Admin review | Admin must be able to view evidence for review, investigation, and support. |
| Sensitive display control | Extracted sensitive fields should be masked, hidden, or restricted unless needed for an approved task. |
| Auditability | Evidence actions must be logged. |

---

## 8. Linked Records, Participant Linking, and Duplicate Detection

PayPlus must support linked records between payer, payee or payee record, obligation, evidence, request, payment, payout, status, and audit objects.

When both payer and payee are platform users, two-sided visibility must require an approved link, invitation, acceptance, or other permitted user/operational action. The product must not assume automatic user-to-user matching.

### 8.1 Required Linked Objects

Each completed or active payment should be linkable to:

- payer user;
- payee user or payee record;
- payment request, only where the payment originated from a request;
- evidence record;
- payment transaction;
- payout or settlement record, if applicable;
- status history;
- audit events.

---

### 8.2 Linking and Duplicate Detection Requirements

| Requirement | Description |
|---|---|
| Shared request ID | Both payer and payee should reference the same payment request when both are users. |
| Linked obligation/payment | The bill, invoice, fee, tenancy, rent, domestic service, or evidence record must link to the payment record. |
| Two-sided visibility | Payer and payee must be able to view the same linked transaction context, subject to permissions. |
| User-accepted linking | User-to-user linking must be initiated, invited, accepted, or otherwise approved; automatic UX matching is not allowed. |
| Payer-created payment | Payer-created payments do not require payee acceptance by default if evidence, payee/payout, risk, and authorization gates pass. |
| Payee-created request | Payee-created requests require payer acceptance before payment authorization. |
| Duplicate detection | System should help detect duplicate requests or duplicate payments. |
| Evidence verification linkage | OCR extraction, user corrections, verification outcomes, duplicate indicators, and review decisions must remain linked to the evidence and obligation, and to the request where a request is used. |
| Status consistency | Request status shown to payer and payee must be consistent. |
| Exception/support tracking | Queries, disputes, requests for more information, or support cases must remain linked to the original request without becoming normal request-route actions. |

---

## 9. Request Status Model

### 9.1 Canonical Request Lifecycle

A request is not a payment. Its lifecycle must remain separate from evidence processing, obligation readiness, payment/payout status, linked case handling, and archive visibility.

| Underlying State | Sender Label | Receiver Label | Meaning |
|---|---|---|---|
| `Draft` | Draft | Not visible | Sender started the request but has not submitted it. |
| `Pending Evidence Verification` | Waiting for Verification | Not visible | Delivery is blocked until evidence passes or an approved exception applies. |
| `Pending Receiver Action` | Reviewing | Awaiting | Request was delivered and awaits acceptance or rejection. |
| `Accepted` | Accepted | Accepted | Receiver accepted the evidence-backed context; this may link the parties but is not payment authorization. |
| `Rejected` | Rejected | Rejected | Receiver rejected the request; retain the reason where provided. |
| `Expired` | Expired | Expired | Request validity ended before acceptance. |
| `Cancelled` | Cancelled | Cancelled where previously visible | Sender cancelled the request where permitted. |

Submission, sending, sharing, viewing, reminding, archiving, and restoration are events or visibility transitions, not request states.

---

### 9.2 Status Rules

| Rule | Requirement |
|---|---|
| Payer authorization | No payment may be processed without payer authorization. |
| Evidence gate | Request cannot move to `Pending Receiver Action` without accepted evidence or an approved exception. |
| Evidence verification gate | Request remains `Pending Evidence Verification` while DOC-12 requires clarification, review, duplicate handling, rejection handling, or fraud/risk escalation. |
| Admin/risk gate | Requests may require admin or risk approval before payment. |
| Rejection finality | Rejected requests cannot be paid unless recreated or reopened under approved rules. |
| Readiness separation | `Ready to Pay`, `Action Required`, and `Under Review` describe the linked obligation, not the request lifecycle. |
| Case separation | Query, dispute, support, and exception handling use linked case records and do not create request lifecycle states. |
| Archive separation | Archive changes list visibility without replacing the request lifecycle state. |
| Audit trail | Every status change must be logged. |
| Two-sided consistency | Payer and payee views must reflect the same underlying status. |

---

## 10. Payment Rules

| Rule | Requirement |
|---|---|
| Payment purpose | Payment must be tied to an evidence-backed obligation. |
| Payer consent | Payer must explicitly authorize payment. |
| Payee payout | Payee may receive payment only through approved payout channels. |
| No self-cashout | Payer cannot use PayPlus to cash out to themselves. |
| No unsupported transfer | Payment cannot be unrelated to a bill, invoice, fee, rent, tenancy, domestic service, or proof of obligation. |
| No stored balance | PayPlus must not hold user wallet balances. |
| Failed payment handling | Failed payments must be visible and traceable. |
| Payment instruction quote validity | A pending or incomplete payment instruction must revalidate payment quote, promotion quote, card eligibility, and material terms before funding submission where required by DOC-09 and DOC-13. |
| Refunds/reversals | Refunds or reversals require admin-dashboard status handling and must follow approved operational policy. |

---

## 11. Admin and Operations Requirements

Admins must be able to:

- view payer accounts;
- view payee accounts;
- view payment requests;
- view evidence;
- review new payees;
- review high-risk requests;
- approve, reject, hold, or request additional information;
- investigate duplicates;
- review disputes;
- view payment and payout status;
- manage operational exceptions;
- access audit logs.

Admin actions must be permissioned and logged.

---

## 12. Compliance and Risk Controls

### 12.1 Required MVP Controls

| Control | Requirement |
|---|---|
| Identity/account controls | Payer and payee accounts must have appropriate onboarding and access controls. |
| Evidence requirement | Payments must be supported by evidence. |
| Evidence verification | OCR/autofill, user correction, duplicate/reuse detection, mismatch checks, verification outcomes, and red-flag routing follow DOC-12. |
| Payer authorization | Payer approval is required before payment. |
| Payee verification | Payee details must be verified according to approved operational policy. |
| Risk review | Requests may be subject to risk review before payment. |
| Duplicate detection | System should help identify duplicate bills or requests. |
| Transaction limits | MVP should support configurable limits. |
| Audit logging | Key actions must be logged. |
| Dispute handling | Payer and payee disputes must be traceable. |
| Restricted use prevention | Wallet, cashout, and unsupported P2P behavior must be blocked. |

---

## 13. Notifications

The MVP should support basic notifications for:

- account registration;
- payment request created;
- request submitted for evidence verification;
- request evidence verified and sent;
- payment request received;
- request viewed;
- request accepted;
- request rejected;
- request expired;
- request cancelled;
- request reminder sent;
- payment authorized;
- payment processing;
- payment completed;
- payment failed;
- payout completed, if applicable.

Candidate notification channels include app notifications, push notifications, email, SMS, and WhatsApp. Final channel routing, user preferences, templates, retry behavior, consent rules, and audit requirements belong in DOC-08.

---

## 14. Data Requirements

The MVP should support data structures for the following object families. Detailed fields, relationships, indexes, event schemas, and ledger behavior belong in DOC-18.

- account identity, authentication, security, KYC/KYB, evidence, payment, payout, risk, support, promotion, communication, analytics, and derived data must be classifiable under DOC-15;
- each material data object should support classification metadata, including data class, sensitivity, displayability, masking rule, retention policy, owner, approved purpose, access role, audit requirement, source lineage, partner-sharing status, and model-use eligibility where applicable;
- material user, system, admin, payment, evidence, promotion, risk, communication, and support actions should create traceable events with event type, actor, timestamp, source object, status transition, reason code where applicable, and audit linkage;
- consent and preference state should be represented in data structures where promotion, personalization, partner offers, marketing communication, analytics, or model-improvement use may depend on user choice or legal/privacy approval;
- analytics and derived data should preserve lineage to source data classes, permitted purposes, sensitivity, aggregation/de-identification status, and access controls;
- future AI/model use should be supported by metadata that identifies approved model purpose, permitted feature inputs, prohibited inputs, human-review requirement, and monitoring/audit expectation where applicable;
- users;
- payer profile;
- payee profile;
- authentication, device, OTP, payment passcode, and material account-change events;
- payment request;
- evidence/document;
- evidence extraction, normalized fields, user corrections, verification signals, review outcome, and final evidence snapshot;
- request participant mapping;
- payment transaction;
- payment instruction;
- payment instruction funding leg;
- tokenized card and payment profile record, including masked metadata, card status, default-card marker, saved split-card profile ratios, starred/frequent marker, action-required state, and soft-delete/archive metadata where applicable;
- bill/rent reminder record, including linked obligation ID, timing, status, custom override, and deletion/disable state where enabled;
- payout/settlement record;
- campaign, offer, promotion quote, promotion quote reservation, benefit entitlement, reward instrument, and redemption/fulfilment records where promotions are enabled; issued rewards must separately preserve instrument type, earning source, participant role where applicable, program context, campaign/offer/entitlement source, and fulfilment method;
- dashboard shortcut configuration, user shortcut preference, restore-default action, dashboard placement exposure, and carousel impression/action records where applicable;
- dispute or clarification thread;
- notification;
- reminder or user action task;
- audit event;
- admin review action.

Detailed data model, event taxonomy, warehouse, analytics marts, feature/model metadata, aggregation thresholds, lineage, and reporting requirements should be defined in DOC-18.

---

## 15. UX Requirements

The MVP should include the following UX surfaces. Detailed route flows, service blueprint steps, and non-payment interaction rules belong in the DOC-06 family. Payment/checkout screen content and payment-domain UI behavior belong primarily in DOC-09, with DOC-06A/DOC-06C owning route entry and handoff.

DOC-06 is the parent UX family map. DOC-06A owns core service journeys, DOC-06B owns navigation, route taxonomy, and human-readable route-level UX for global non-Bills routes, DOC-06C owns Bills/rent/tenancy UX, and DOC-06D owns UX requirement/test mapping. Product requirements in DOC-05 should reference stable product destination IDs where useful, use specific child destinations where defined, and avoid duplicating screen-level routing rules.

For split UX topics, use one primary owner. DOC-06B owns standalone route shells and human-readable route-level UX for Requests, Instructions, Payment Profile, Offers, Me, Referral, More, and global Receipts/Activity routes. DOC-06A owns the underlying journey lifecycle. DOC-06C owns Bills/rent/tenancy-specific implementation. DOC-06D owns testability mapping. If a requirement seems to affect multiple DOC-06 child documents, define the primary owner first, then update only references or handoffs in the other documents.

Stable global destination IDs are mandatory for traceability even where detailed UI remains incomplete. `AUTH-ENTRY` is the pre-login choice screen; `AUTH-LOGIN` and `AUTH-REGISTRATION` are the required authentication destinations; normal successful entry proceeds to `HOME-ROOT`, subject to approved contextual deeplink return. `PAYPLUS-ACTION-SHEET`, `MORE-ROOT`, and `NOTIFICATION-INBOX` identify the Pay+, More, and Inbox destinations. DOC-09 `PAYMENT-CHECKOUT` identifies the payment checkout flow/screen group without transferring checkout ownership to DOC-06.

For growth UX, `OFFERS-ROOT` owns promotion discovery; its child screens `OFFERS-CARD-LIST`, `OFFERS-PAYPLUS-LIST`, and `OFFERS-PARTNER-LIST` own the respective View More collections; `REWARDS-ROOT` owns issued-reward management through Active and History views; and the `REFERRAL-ROOT`, `REFERRAL-REWARDS-LIST`, `REFERRAL-ENTITLEMENT-DETAIL`, and `REFERRAL-REWARD-CLAIM` route family owns referral sharing, attributed-referee qualification progress, and role-sensitive referrer/referee reward claiming. `REWARD-DETAIL` owns full reward information and terms but is not a second checkout route; checkout reward selection remains in DOC-09 after card/profile selection. The Referral Rewards list uses `Available to Claim` and `History` route-local tabs; claimed reward use remains in canonical Rewards. One offer may belong to multiple discovery collections, while unintended repeated display of the same Offer ID is suppressed on `OFFERS-ROOT`. Direct checkout discounts are not issued rewards. Referral campaigns may appear in Offers, but referral actions remain in the Referral route; an issued referral reward uses the canonical `REWARD-DETAIL`. Detailed commercial, qualification, entitlement, lifecycle, fulfilment, and calculation logic remains owned by DOC-13.

For Requests, use the DOC-06 family boundary: a request is not a payment. It is a record asking another party to review, accept, link to, or reject a bill, rent, tenancy, fee, invoice, or approved obligation context. Accepted requests link the parties to the accepted context and may support later payment readiness, but payment authorization and processing remain separate payment-domain behavior.

The standalone Requests route shell is defined in DOC-06B. It provides route entry, views, card-level summary fields, `REQUESTS-DETAIL`, `REQUESTS-NEW`, high-level actions, empty states, and handoff rules. `REQUESTS-DETAIL` is the request-management screen; it may link into DOC-06C bill/rent/tenancy detail where a linked context exists, but it must not be replaced by the bill/rent detail screen. `REQUESTS-NEW` is the controlled creation flow and must not create an open money request. Detailed request lifecycle remains DOC-06A, Bills/rent implementation remains DOC-06C, notification routing remains DOC-08, and final data/event specification remains DOC-18.

Bills-route requirements must remain role-aware:

- `BILLS-PAY` is the payer-side route for bills, fees, rent, and payee-created requests the user needs or expects to pay;
- `BILLS-RECEIVE` is the payee-side route for bill, fee, rent, and request records the user expects to receive;
- payee-side records must not show payer-side `Pay` actions;
- payer-side received requests belong in `BILLS-PAY`, not `BILLS-RECEIVE`.

For account-control UX, `ME-ROOT` is a permanent MVP bottom-navigation route for users acting as payer, payee, or both. It provides masked Account Information, account/security/privacy child-route entry, Bills access, Payment Profile, Receiving Info, Activity, Receipts & Statements, Archived Records, My Rewards, Referral, preferences, support, About/Terms, and logout. These rows are route handoffs and do not transfer ownership from DOC-06C, DOC-08, DOC-10, DOC-12, DOC-13, DOC-15, DOC-18, DOC-19, DOC-21, or DOC-22.

DOC-06B defines `ACCOUNT-PROFILE`, reusable `IDENTITY-VERIFICATION`, `ACCOUNT-SECURITY`, child screen `PAYMENT-PASSCODE-SETTINGS`, and `PRIVACY-DATA-CONTROLS`. The MVP includes immutable login name after setup, copyable PayPlus User ID, cross-channel phone/email change verification, four identity-verification display labels, immediate `Verify Now` handoff for non-verified states, account closure as a controlled request, password/passcode and permitted 2FA/biometric controls, trusted-device removal, optional privacy choices, governed correction/access/export/deletion requests, and protected in-app export.

Sensitive information remains masked by default. Prominent reveal of approved masked sensitive values, and material changes to identity, contact, security, credential, or Receiving Info data, require payment passcode or approved reauthentication under DOC-15 and future DOC-19 controls. Ordinary permitted evidence, invoice, receipt, statement, and payment-proof viewing/downloading does not require an extra prompt solely for opening or downloading the document. `ACTIVITY-ROOT` remains the single account-level payer/payee financial activity route. `RECEIVING-INFO` manages private reusable receiving profiles. `ARCHIVED-ROOT` separates archived obligations in `ARCHIVED-BILLS-LIST` from archived/previous evidence in `ARCHIVED-DOCS-LIST`.

An active bill/rent must retain one current evidence set. That sole evidence cannot be archived independently. Accepted replacement moves the prior version to `ARCHIVED-DOCS-LIST` as `Previous version`. Archiving a bill/rent moves its current linked evidence, where one exists, into the same user's archived-document projection. Restore is offered only to eligible obligations, revalidates the restored current evidence, and never restores a previous version. Expired obligations do not auto-archive; an already-expired obligation manually archived by the user is non-restorable.

Archive is a per-user visibility action. It must not change the counterparty's active view, party linkage, the canonical obligation, completed financial history, or retained destination/payment snapshots. `ARCHIVED-BILLS-LIST` uses one mixed-role list with Bill/Fee, Rent/Tenancy, Pay, Receive, and Restore available filters. Archived detail reuses the normal bill/rent detail route in read-only mode and exposes Restore only after current eligibility checks.

### Payer

- enter through `AUTH-ENTRY` and use `AUTH-LOGIN` or `AUTH-REGISTRATION`;
- verify phone by SMS OTP during registration;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm core account, payment profile, or credential changes using password, payment passcode, 2FA, or approved confirmation method;
- dashboard through `HOME-ROOT`;
- logged-in `HOME-ROOT` baseline with `Home`, `Bills`, `Pay+`, `Offers`, and `Me` navigation where enabled by DOC-06B;
- Pay+ center action entry point opening `PAYPLUS-ACTION-SHEET` where enabled by DOC-06B;
- dashboard shortcut grid for Requests, Instructions, Bills & Tenancies, Receipts, Reminders, Cards, Referral, and More where enabled by DOC-06B; shortcuts are entry points into owning routes or management areas, not independent feature owners;
- `Cards` shortcut opens DOC-06B `PAYMENT-PROFILE-ROOT` for tokenized card management and saved split-card profile management; it is not checkout and does not authorize payment;
- user shortcut display order, visibility preference, and restore-default behavior;
- permanent `ME-ROOT` access with fixed account-control sections, masked Account Information, security/privacy entry, established-route handoffs, preferences, support, About/Terms, and a bottom Log Out button;
- Important Notice / Action Required, Featured / What's New / Hot Offer carousel, Upcoming Bills / Rent, and Recent Activity dashboard sections where enabled by DOC-06B;
- bill/rent reminder management through DOC-06C `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`, including linked reminders, reminder defaults, custom overrides, disable/delete behavior, and notification ownership boundaries;
- create payment;
- view payee-created requests that require payer action through DOC-06C `BILLS-PAY`;
- review evidence;
- review and correct autofilled evidence fields where applicable;
- accept or reject request;
- authorize payment;
- enter payment passcode before proceeding with payment authorization;
- choose pay now or create a pending payment instruction where enabled;
- view and act on payment instruction action alerts through DOC-06B `INSTRUCTIONS-ROOT` / `INSTRUCTIONS-DETAIL`;
- review updated quote, promotion, fee, card eligibility, or timing changes when returning to a pending or incomplete payment instruction;
- view partial funding, remaining amount, and partial payout status where applicable;
- review the automatically selected highest-user-value payment-method-sensitive Card Offer, separately select an eligible checkout coupon/voucher/discount, and review the recalculated promotion/payment quote in the same checkout screen or step before authorization;
- discover approved promotions through DOC-06B `OFFERS-ROOT` and review conditions through `OFFER-DETAIL`;
- manage issued coupons, vouchers, external-partner instruments, miles entitlements, or other supported rewards through `REWARDS-ROOT` and `REWARD-DETAIL`; external vouchers and miles are launch-supported reward types, while each actual provider method remains subject to operational and integration readiness;
- share a reusable referral link/code, view attributed-referee qualification progress, and claim the user's corresponding referrer or referee rewards through the Referral route family where enabled; referral sharing alone does not identify a recipient or create an invitation status;
- manage tokenized cards, set a default card for single-card checkout, and manage saved split-card payment profiles where enabled;
- view payment status;
- view receipts/history.

### Payee

- enter through `AUTH-ENTRY` and use `AUTH-LOGIN` or `AUTH-REGISTRATION`;
- verify phone by SMS OTP during registration;
- complete new-device 2FA and dormant-login reauthentication where required;
- dashboard through `HOME-ROOT`;
- create payment request;
- upload evidence;
- review and correct autofilled evidence fields where applicable;
- send request to payer;
- view request and receive-management status through DOC-06C `BILLS-RECEIVE`;
- remind payer where enabled and controlled by DOC-06C, DOC-08, and DOC-22;
- view linked payments;
- respond to clarification/dispute;
- view payout/payment status;
- manage multiple private reusable receiving profiles through `RECEIVING-INFO`, including optional nickname, readiness, masked display, add/edit/version/archive, and proof where required;
- select one destination for a payee-created request without exposing other saved profiles to the payer;
- preserve separate request/obligation/payment destination snapshots so profile edits or archive do not alter accepted requests or authorized payouts;
- access account-level Activity, Receipts & Statements, Archived Records, and controlled archived/previous evidence through the applicable `ME-ROOT` handoffs.

### Admin

- login;
- operational dashboard;
- dashboard shortcut, notice/action, carousel placement, and feature enablement configuration where enabled;
- role-based sensitive data access with masking, reason capture, and audit logging;
- request review queue;
- evidence review;
- OCR/verification review;
- duplicate/reused evidence review;
- user/payee review;
- payment status view;
- dispute/exception handling;
- audit log access.
- campaign, offer, coupon/voucher, reward entitlement, and promotion exception view where promotions are enabled.

---

## 16. MVP Business Requirements

The MVP should support:

- configurable service fee model;
- configurable promotion engine rules where enabled;
- fee display before payer authorization;
- promotion quote, discount, coupon, voucher, reward, and final total display before payer authorization where applicable;
- admin-configurable dashboard shortcut defaults, dashboard placements, and carousel display rules where enabled;
- admin-configurable bill/rent reminder defaults, reminder eligibility, and reminder feature gating where enabled;
- user-managed shortcut ordering and restore-default behavior where enabled;
- transaction-level revenue tracking;
- payment status reporting;
- governed product, risk, evidence, payment, promotion, support, and operations analytics where enabled;
- payment instruction status reporting, including deferred, pending, partial funding, fully funded, expired, and cancelled states;
- partial payout status reporting for settlement-ready funded portions;
- user-level activity history, with bill/rent-specific activity governed by DOC-06C and full audit/event history governed by DOC-18 and DOC-22;
- operational review workflows;
- support and dispute handling;
- partner/payment processor compatibility.

Final pricing, fee model, and partner economics should be governed by DOC-02 and later commercial decisions.

---

## 17. Non-Functional Requirements

| Area | Requirement |
|---|---|
| Security | Protect user, payment, and evidence data. |
| Privacy | Apply DOC-15 data classification, role-based display controls, masking, retention, and approved-purpose access. |
| Data governance | Material data should support classification, lineage, auditability, consent/preference state, approved purpose, partner-sharing status, and future model-use eligibility metadata where applicable. |
| Reliability | Payment status and request status must remain consistent. |
| Auditability | Key user, admin, payment, and evidence actions must be logged. |
| Scalability | Architecture should support future automation and additional payment categories. |
| AI readiness | Architecture should support future approved AI/model improvement through governed data capture, model input controls, explainability, monitoring, and human-review boundaries. |
| Availability | MVP should be available enough for controlled beta operations. |
| Maintainability | Product should use clear object models and status transitions. |
| Compliance readiness | System should support review, evidence, audit, and reporting needs. |

---

## 18. Prohibited Product Behavior

PayPlus must not:

- operate as a wallet;
- provide user stored balances;
- allow cash withdrawal;
- allow payer self-cashout;
- allow unsupported arbitrary P2P transfers;
- process payments without payer authorization;
- process payments without evidence or approved exception;
- allow payee-created requests to trigger payment without required payer acceptance and explicit payer authorization;
- hide material payment information from payer before authorization;
- create untraceable payment records;
- bypass admin/risk controls where required;
- represent funds as deposits or bank account balances.

---

## 19. MVP Acceptance Criteria

The MVP is acceptable when:

- payers can register and log in;
- payees can register and log in;
- payer-created payment requests can be created;
- payee-created payment requests can be created;
- evidence can be attached to requests;
- OCR/document AI can extract and autofill evidence fields where enabled;
- users can review and correct autofilled evidence fields before submission;
- duplicate/reused evidence and material mismatch cases can route to review;
- payer can review evidence before payment;
- payer can accept or reject a request, with rejection reason where required;
- payer can authorize payment;
- payment status can be tracked;
- payer and payee can view the same linked request/payment context;
- admin can review users, requests, evidence, and exceptions;
- no wallet balance or cashout behavior exists;
- all key actions are audit logged;
- prohibited flows are blocked;
- failed, rejected, expired, and cancelled requests are handled clearly.

---

## 20. Open Questions

| ID | Question | Owner | Status |
|---|---|---|---|
| OQ-05-001 | What specific payment processor or PSP will be used? | Product / Payments | Open |
| OQ-05-002 | What final KYC/KYB provider, check depth, sanctions screening, exception process, and risk-tier rules apply to the baseline onboarding model? | Compliance / Legal | Open |
| OQ-05-003 | Which evidence categories are accepted at launch? | Product / Compliance | Open |
| OQ-05-004 | Which rent and tenancy controls are required before initial launch enablement? | Product / Risk | Open |
| OQ-05-005 | What transaction limits apply by user type and category? | Risk / Product | Open |
| OQ-05-006 | What admin review rules are mandatory before payment or payout? | Operations / Risk | Open |
| OQ-05-007 | What exact percentage service fee, payer/payee fee allocation, subsidy, coupon, promotion, discount, refund, and reversal treatment will be used? | Business / Product | Open |
| OQ-05-008 | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Operations | Open |
| OQ-05-009 | What privacy, deletion, masking, and legal exception rules apply beyond the 7-year tax and audit retention baseline? | Legal / Compliance | Open |
| OQ-05-010 | What dispute process applies after payment completion? | Operations / Legal | Open |
| OQ-05-011 | What appropriate or special MCC and transaction classification will the selected acquirer confirm for PayPlus? | Payments / Legal | Open |
| OQ-05-012 | What maximum number of credit cards per payment/profile should be allowed at launch? | Product / Payments | Answered: 6 |
| OQ-05-013 | Which OCR/document AI provider, confidence thresholds, and launch categories should be enabled first? | Product / Engineering / Risk | Open |
| OQ-05-014 | Which extracted fields are displayable, masked, or restricted by role and evidence category? | Product / Privacy / Security | Open |
| OQ-05-015 | What exact dashboard shortcut cap, default ordering, user reorder UI, restore-default behavior, and More shortcut behavior should apply? | Product / Design / Operations | Open |
| OQ-05-016 | What exact Pay+ action sheet actions, labels, ordering, and eligibility rules should apply? | Product / Design / Payments | Open |
| OQ-05-017 | What admin controls are required for Important Notice / Action Required, Featured / What's New / Hot Offer carousel, and dashboard placement targeting? | Product / Growth / Operations | Open |
| OQ-05-018 | Which MVP events and data objects must be captured for product analytics, risk analytics, commercial reporting, and future approved AI/model improvement? | Product / Data / Engineering | Open |
| OQ-05-019 | What user consent and preference categories are required for personalization, partner offers, marketing communication, and model improvement? | Product / Privacy / Legal | Open |
| OQ-05-020 | Which data classes, fields, and derived features are prohibited from marketing models, partner reports, or external activation? | Product / Privacy / Risk | Open |
| OQ-05-021 | What final Payment Profile card metadata display and tokenization return UX should apply at launch? Route label is `Payment Profile`; payment/profile card-count cap is 6. | Product / Payments / Security | Partially open |

---

## 21. Dependencies

| Dependency | Purpose |
|---|---|
| DOC-00 | Documentation governance and source-of-truth rules |
| DOC-01 | Product overview and positioning |
| DOC-02 | Business model and monetization |
| DOC-03 | Regulatory assessment |
| DOC-04 | Compliance control framework |
| DOC-06 | Parent user journey, UX flow, and service blueprint family map |
| DOC-06A | Core user journeys and service blueprint |
| DOC-06B | Navigation, IA, route taxonomy, dashboard, Pay+, global non-Bills route-level UX, and route completion status |
| DOC-06C | Bills, rent, tenancy, activity, reminder, evidence, and role-aware Bills-route UX |
| DOC-06D | UX requirements, acceptance criteria, and test-readiness mapping |
| DOC-07 | User-facing disclosure, authorization, evidence, privacy, and policy wording |
| DOC-08 | Notifications, receipts, communication triggers, and delivery logging |
| DOC-09 | Payment request, funding, authorization, and settlement readiness |
| DOC-10 | Payout, payout readiness, payout destination, batching, and reconciliation |
| DOC-11 | Refund, cancellation, reversal, dispute, and chargeback handling |
| DOC-12 | Bill category, document AI/OCR, evidence verification, duplicate detection, and payee/payout validation |
| DOC-14 | AML, anti-cashout, fake evidence, duplicate evidence, collusion, and risk controls |
| DOC-15 | Privacy, data protection, masking, retention, lawful data use, consent, personalization, model-improvement, and partner-sharing boundaries |
| DOC-17 | Third-party APIs including OCR/document AI, PSP, bank, provider, analytics, campaign, and partner-reporting integrations where approved |
| DOC-18 | Data model, evidence data layers, transaction state, audit events, ledger, event taxonomy, lineage, analytics marts, feature/model metadata, and reporting |
| DOC-19 | Authentication, authorization, evidence access, security, tokenization, analytics access controls, pseudonymization, and partner-sharing controls |
| DOC-21 | Monitoring, incidents, support escalation, and operations runbooks |
| DOC-22 | Admin dashboard workflows, review queues, overrides, permissions, and configuration |

---

## 22. Decision Summary

| Decision | Status |
|---|---|
| Payer-created payment requests are MVP scope. | Confirmed |
| Payee-created payment requests are MVP scope. | Confirmed |
| Tenancy and rent payments are MVP scope. | Confirmed |
| Payers can log in. | Confirmed |
| Payees can log in. | Confirmed |
| Every payment should be evidence-backed. | Confirmed |
| OCR/document AI-assisted evidence capture, autofill, user correction, duplicate detection, and verification routing are required capabilities where enabled. | Confirmed |
| Payer must authorize payment before funds movement. | Confirmed |
| Linked payer/payee views are required. | Confirmed |
| Wallet, cashout, and unsupported P2P are prohibited. | Confirmed |
| Major functions and modules must be independently disableable. | Confirmed |
| Future docs should use concise product-spec structure. | Confirmed |
| Promotion engine capabilities are framework scope but launch-gated by DOC-13 rules and admin configuration. | Confirmed |
| `AUTH-ENTRY`, `AUTH-LOGIN`, and `AUTH-REGISTRATION` are required acceptance-scope destinations. Normal successful authentication enters `HOME-ROOT`; approved contextual deeplinks may resume their intended destination. | Working Baseline / Detailed UI Pending |
| `PAYPLUS-ACTION-SHEET`, `MORE-ROOT`, `NOTIFICATION-INBOX`, and DOC-09 `PAYMENT-CHECKOUT` are the stable destination IDs for their respective product areas. | Working Baseline / Detailed UI Pending |
| DOC-06B designated Home Dashboard flow and layout baseline is accepted for MVP discussion, but final UI design and exact component specification remain open. | Confirmed |
| Dashboard shortcut grid, user shortcut preferences, Pay+ entry point, and admin-controlled dashboard placements must be supported where enabled. | Confirmed |
| DOC-06C `BILLS-PAY` and `BILLS-RECEIVE` route split is accepted as the current role-aware Bills-route baseline; checkout/payment screen behavior remains primarily governed by DOC-09. | Working Baseline / Not Final |
| DOC-06B `PAYMENT-PROFILE-ROOT` is accepted as the current route shell for tokenized card and saved split-card profile management; checkout authorization and funding remain governed by DOC-09. | Working Baseline / Not Final |
| DOC-06B `ME-ROOT`, Account Information, Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, `RECEIVING-INFO`, and the `ARCHIVED-ROOT` family are accepted; Support/About/Terms and final visual design remain pending. | Working Baseline / Core Account, Receiving Info, and Archive Family Defined |
| The canonical product destination inventory is maintained in `docs/traceability/route-register.md`; route owners and the DOC-06 parent must remain synchronized with it. | Confirmed |
| PayPlus MVP should be data-engine ready by design, with structured events, field classification, source lineage, auditability, consent/preference state, approved-purpose metadata, and future model-use eligibility metadata where relevant. | Confirmed |
| Advanced AI decisioning, external partner activation, offsite advertising, user-level data sharing, credit scoring, and insurance underwriting are not MVP scope unless separately assessed, approved, and documented. | Confirmed |

---

## 23. Revision History

| Version | Date | Summary |
|---|---|---|
| v0.18.24 | 2026-07-26 | Defined the archived-obligation product baseline, mixed-role filters, read-only detail reuse, eligibility/blocker and restore rules, personal archive projection, and obligation/evidence separation. |
| v0.18.23 | 2026-07-26 | Added the `ARCHIVED-ROOT` family and confirmed evidence replacement, parent archive, restoration, expiry, non-restorable history, and Archived Documents behavior. |
| v0.18.22 | 2026-07-26 | Added stable authentication, Home, Pay+, More, Notification Inbox, and Payment Checkout destination IDs and the pre-login Login/Register handoff baseline. |
| v0.18.21 | 2026-07-26 | Adopted the canonical request lifecycle, role-facing labels, event/evidence/readiness/case/archive separation, and removed mixed request-status definitions. |
| v0.18.20 | 2026-07-26 | Clarified evidence-to-obligation linkage and optional request involvement, aligned prominent sensitive reveal and material-change authentication, retained ordinary permitted document viewing/download without extra prompt, and referenced the canonical route register. |
| v0.18.19 | 2026-07-23 | Replaced singular Receiving Details with multiple private reusable Receiving Info profiles and aligned request selection, destination snapshots, masking/edit behavior, archive/versioning, and authorization-freeze requirements. |
| v0.18.18 | 2026-07-22 | Aligned the PRD with defined Account Information, Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, contact-change, verification-status, account-closure, trusted-device, privacy-request, and protected-export behavior. |
| v0.18.17 | 2026-07-22 | Aligned the PRD with permanent `ME-ROOT`, masked account display and passcode-gated reveal, account/security/privacy handoffs, Receiving Details, archived-evidence access, established feature-route entry, preferences, support, About/Terms, logout, and the separate More boundary. |
| v0.18.16 | 2026-07-21 | Aligned the PRD with defined My Rewards Active/History management, complete reward detail/T&C, checkout-owned reward selection, launch-supported external vouchers and miles, and separate reward instrument/source/role/program/campaign/entitlement/fulfilment data dimensions. |
| v0.18.15 | 2026-07-21 | Aligned the PRD with role-sensitive Referral Rewards child screens, two list tabs, detail-first claiming, canonical issued-reward usage, and the restricted masked-phone display boundary. |
| v0.18.14 | 2026-07-21 | Aligned the PRD with the defined Referral route family, reusable sharing, registration attribution, qualification progress, referrer entitlement claiming, and canonical issued-reward handoff. |
| v0.18.13 | 2026-07-20 | Aligned the PRD with multi-collection Offers, root duplicate suppression, stable child-list ordering, automatic highest-user-value Card Offer selection per payment card/funding leg, separate coupon/voucher/discount selection, and same-screen checkout review. |
| v0.1 | Initial Draft | Initial master PRD structure. |
| v0.2 | 2026-05-27 | Updated MVP to include both payer-created and payee-created payment requests; added two-sided user visibility, evidence-backed linking, linked payer/payee records, and simplified structure. |
| v0.3 | 2026-05-29 | Confirmed payee-created requests and tenancy/rent as MVP scope, added MVP gating and configuration rules, clarified that detailed data and UX design belong in downstream docs, and updated open questions. |
| v0.4 | 2026-05-30 | Aligned product requirements with updated DOC-01 scope for invoices, fees, rent, domestic service obligations, request delivery methods, and evidence-backed positioning. |
| v0.5 | 2026-05-30 | Aligned master PRD with DOC-12 by adding OCR/autofill, user correction, evidence verification outcomes, duplicate/reused evidence routing, sensitive field display controls, and explicit downstream document references. |
| v0.6 | 2026-06-01 | Aligned master PRD with DOC-13 by adding promotion quote, entitlement, coupon/voucher library, reward instrument, campaign data, and admin promotion-control references. |
| v0.7 | 2026-06-02 | Aligned master PRD with DOC-15 by adding privacy data classes, field-level classification metadata, authentication UX requirements, material-change confirmation, payment passcode, and admin sensitive-data access controls. |
| v0.8 | 2026-06-02 | Added DOC-09 user payment instruction as MVP scope for deferred single-card and split-card payment, payment-instruction reminders, partial funding, and partial payout visibility. |
| v0.9 | 2026-06-02 | Aligned PRD with DOC-09 and DOC-13 deferred payment instruction quote revalidation, promotion reservation, and return-to-checkout update review. |
| v0.10 | 2026-06-02 | Standardized coupon/voucher library wording to avoid stored-value confusion. |
| v0.11 | 2026-06-04 | Aligned PRD with DOC-06 Home Dashboard baseline by adding Pay+ navigation, shortcut grid, user shortcut preferences, dashboard placements, Featured carousel, and related admin configuration expectations. |
| v0.12 | 2026-06-08 | Added data-engine and AI-readiness requirements for structured events, field metadata, consent/preference state, approved-purpose data use, future model eligibility, analytics readiness, and prohibited MVP AI/partner activation boundaries. |
| v0.13 | 2026-06-12 | Aligned PRD with DOC-06 Bills tab baseline by clarifying payer-created payment without default payee acceptance, user-accepted participant linking, payee/payout validation, and no automatic user-to-user matching. |
| v0.14 | 2026-06-15 | Clarified that DOC-06 owns user-facing route IDs, route types, and button-to-route ownership for Bills tab and related UI surfaces. |
| v0.15 | 2026-06-17 | Aligned PRD with DOC-06 Bills reminder route split, linked reminder records, reminder defaults, custom override, and admin reminder configuration boundaries. |
| v0.16 | 2026-06-17 | Added PRD alignment note that DOC-06 owns route ID naming standards and specific sub-route IDs where available. |
| v0.17 | 2026-06-25 | Aligned PRD with DOC-06 role-aware `BILLS-PAY` / `BILLS-RECEIVE` route split, payee-side request/remind-payer behavior, checkout ownership boundary with DOC-09, and activity-history ownership boundaries. |
| v0.18 | 2026-06-25 | Aligned PRD references with the DOC-06 family split by pointing navigation/dashboard content to DOC-06B, Bills/rent/tenancy UX to DOC-06C, core journeys to DOC-06A, and UX acceptance/test mapping to DOC-06D. |
| v0.18.1 | 2026-06-25 | Confirmed DOC-06 family publication cleanup and parent scope, role, and UX-surface summaries without changing master product requirements. |
| v0.18.2 | 2026-06-25 | Added single-primary-owner drafting rule for DOC-06 family topics and clarified route shell versus lifecycle versus Bills/rent implementation ownership. |
| v0.18.3 | 2026-06-25 | Clarified request-not-payment boundary and request acceptance as party-linking to an accepted obligation context. |
| v0.18.4 | 2026-06-25 | Reflected DOC-06B Requests route shell baseline and preserved lifecycle, Bills/rent implementation, notification, and data ownership boundaries. |
| v0.18.5 | 2026-06-29 | Added PRD alignment that `REQUESTS-DETAIL` is the request-management screen and links to, but is not replaced by, DOC-06C bill/rent detail. |
| v0.18.6 | 2026-07-02 | Clarified dashboard shortcuts as entry points into owning routes or management areas, aligned with DOC-06B route-entry map. |
| v0.18.7 | 2026-07-02 | Aligned PRD with DOC-06B `REQUESTS-NEW`, evidence-before-send request delivery gate, and request-not-payment route boundary. |
| v0.18.8 | 2026-07-02 | Removed stale request-route clarification/dispute actions and aligned exception/support wording with DOC-06B `REQUESTS-NEW` and `REQUESTS-DETAIL`. |
| v0.18.9 | 2026-07-03 | Aligned PRD wording with DOC-06B Instructions route and DOC-09 payment instruction boundary: pending/incomplete instructions remain separate from ordinary reminders and completed pay-now payments. |
| v0.18.10 | 2026-07-06 | Aligned PRD with DOC-06B Payment Profile route shell for tokenized cards and saved split-card profiles, including final `Payment Profile` label, max 6-card cap, checkout/instruction handoff, default confirmation behavior, and non-wallet boundary. |
| v0.18.11 | 2026-07-14 | Clarified DOC-06B ownership of human-readable route-level UX for global non-Bills routes while preserving domain-logic ownership boundaries. |
| v0.18.12 | 2026-07-17 | Aligned the PRD with stable product destination naming, separate Offers child-list screens, issued-reward management, and partial referral routes while preserving DOC-13 business-logic and DOC-09 checkout ownership. |
