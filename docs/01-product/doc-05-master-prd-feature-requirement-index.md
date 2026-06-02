---
document_id: DOC-05
title: Master PRD & Feature Requirement Index
version: 0.10.0
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
last_updated: 2026-06-02
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-06 User Journey, UX Flow & Service Blueprint
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
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-05 - PayPlus Master Product Requirements Document

## 1. Purpose

This document defines the master product requirements for PayPlus.

PayPlus is an evidence-backed payment platform that allows payers and payees to create, view, match, authorize, and track bill, invoice, fee, rent, domestic service, and other approved obligation payment requests.

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
- payer and payee visibility into linked payment records;
- matching between bill/request/payment records;
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
| Multi-card funding | MVP scope; support up to a configurable number of credit cards per payment, with the launch cap and related controls to be confirmed. |
| User payment instruction | MVP scope; enable for single-card and split-card payments where DOC-09 deferred funding, reminder, partial funding, and payout controls are ready. |

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
- receipt, payment, account, tax, and audit record retention is expected to be 7 years, subject to final privacy and legal review;
- exact fee rates, fee allocation, promotion, coupon, voucher, reward, entitlement, refund, reversal, and multi-card card-count limit remain to be confirmed and should be admin-configurable where applicable.

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
- deferred user payment instruction for single-card and split-card payment is in scope under DOC-09 and is not an automatic recurring payment;
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

---

## 5. User Roles

| Role | Description | MVP Login? |
|---|---|---|
| Payer | User who reviews, authorizes, and makes payment. | Yes |
| Payee | User who receives payment or creates payment requests. | Yes |
| Admin / Operations | Internal user who reviews requests, evidence, risk, payee details, and exceptions. | Yes |
| System | Automated services handling status updates, notifications, matching, and audit events. | No |

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
8. System validates evidence, matches payee, checks duplicates, and routes red flags to review.
9. System creates a payment request record.
10. Payee may be invited, matched, or linked if already a PayPlus user.
11. Admin/system reviews request and evidence according to configured controls.
12. Payer authorizes payment.
13. Payment is processed through approved payment partners.
14. Payee receives payment according to approved settlement/payout rules.
15. Both payer and payee can view the linked payment record when both are users.
16. System stores receipt, status history, and audit trail.

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
8. System validates evidence, matches payee, checks duplicates, and routes red flags to review.
9. System creates a payment request record.
10. Payer is notified or invited to view the request.
11. Payer logs in or registers.
12. Payer reviews the request, evidence summary, amount, payee details, and required disclosures.
13. Payer accepts, rejects, disputes, or requests clarification.
14. If accepted, payer authorizes payment.
15. Payment is processed through approved payment partners.
16. Payee receives payment according to approved settlement/payout rules.
17. Both payer and payee can view the linked bill/request/payment record.
18. System stores receipt, status history, and audit trail.

---

## 7. Evidence Requirements

Every payment request must be supported by acceptable evidence.

Detailed bill category, document AI/OCR, extracted field, autofill, user correction, duplicate detection, verification outcome, and payee matching requirements belong in DOC-12.

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
| Evidence required | A payment request cannot proceed to payment without evidence unless explicitly approved by admin policy. |
| Evidence linked | Evidence must be linked to the payment request. |
| OCR/autofill support | Where enabled, system should extract evidence fields and autofill request fields for user review. |
| User correction | Users must be able to review and correct autofilled fields before submission. |
| Verification outcome | Evidence must have a verification outcome or approved exception before payment eligibility. |
| Duplicate/reuse detection | System should detect duplicate or reused evidence and route configured red flags to review. |
| Payer review | Payer must be able to review evidence before authorizing payment. |
| Payee review | Payee must be able to view evidence attached to their own created requests or linked received payments. |
| Admin review | Admin must be able to view evidence for review, investigation, and support. |
| Sensitive display control | Extracted sensitive fields should be masked, hidden, or restricted unless needed for an approved task. |
| Auditability | Evidence actions must be logged. |

---

## 8. Matching and Linked Records

Because both payer and payee are MVP users, PayPlus must support linked records between both sides.

### 8.1 Required Linked Objects

Each completed or active payment should be linkable to:

- payer user;
- payee user or payee record;
- payment request;
- evidence record;
- payment transaction;
- payout or settlement record, if applicable;
- status history;
- audit events.

---

### 8.2 Matching Requirements

| Requirement | Description |
|---|---|
| Shared request ID | Both payer and payee should reference the same payment request when both are users. |
| Linked obligation/payment | The bill, invoice, fee, tenancy, rent, domestic service, or evidence record must link to the payment record. |
| Two-sided visibility | Payer and payee must be able to view the same linked transaction context, subject to permissions. |
| Duplicate detection | System should help detect duplicate requests or duplicate payments. |
| Evidence verification linkage | OCR extraction, user corrections, verification outcomes, duplicate indicators, and review decisions must remain linked to the request. |
| Status consistency | Request status shown to payer and payee must be consistent. |
| Dispute tracking | Disputes or clarifications must remain linked to the original request. |

---

## 9. Request Status Model

### 9.1 Core Statuses

The MVP should support the following request statuses:

| Status | Meaning |
|---|---|
| Draft | Request created but not submitted. |
| Submitted | Request submitted for review or routing. |
| Sent | Request sent to payer or payee. |
| Viewed | Recipient viewed the request. |
| Clarification Requested | Recipient or admin requested more information. |
| Accepted | Payer accepted the request. |
| Rejected | Payer rejected the request. |
| Disputed | Payer or payee disputed the request. |
| Approved for Payment | Required checks passed before payment. |
| Payment Authorized | Payer authorized payment. |
| Payment Processing | Payment is being processed. |
| Paid | Payment completed. |
| Failed | Payment failed. |
| Cancelled | Request cancelled. |
| Expired | Request expired. |

---

### 9.2 Status Rules

| Rule | Requirement |
|---|---|
| Payer authorization | No payment may be processed without payer authorization. |
| Evidence gate | Request cannot move to Approved for Payment without required evidence or approved exception. |
| Evidence verification gate | Request cannot move to Approved for Payment when DOC-12 verification outcome requires user clarification, admin review, rejection, or fraud/risk escalation. |
| Admin/risk gate | Requests may require admin or risk approval before payment. |
| Rejection finality | Rejected requests cannot be paid unless recreated or reopened under approved rules. |
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
| Deferred instruction quote validity | A deferred payment instruction must revalidate payment quote, promotion quote, card eligibility, and material terms before funding submission where required by DOC-09 and DOC-13. |
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
- approve, reject, hold, or request clarification;
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
- payment request received;
- request viewed;
- clarification requested;
- request accepted;
- request rejected;
- request disputed;
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
- each material data object should support classification metadata, including data class, sensitivity, displayability, masking rule, retention policy, owner, approved purpose, access role, audit requirement, and source lineage where applicable;
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
- payout/settlement record;
- campaign, offer, promotion quote, promotion quote reservation, benefit entitlement, reward instrument, and redemption/fulfilment records where promotions are enabled;
- dispute or clarification thread;
- notification;
- reminder or user action task;
- audit event;
- admin review action.

Detailed data model requirements should be defined in a later technical/data document.

---

## 15. UX Requirements

The MVP should include the following UX surfaces. Detailed screen flows, service blueprint steps, and interaction rules belong in DOC-06.

### Payer

- register/login;
- verify phone by SMS OTP during registration;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm core account, payment profile, or credential changes using password, payment passcode, 2FA, or approved confirmation method;
- dashboard;
- create payment;
- view received requests;
- review evidence;
- review and correct autofilled evidence fields where applicable;
- accept/reject/dispute request;
- authorize payment;
- enter payment passcode before proceeding with payment authorization;
- choose pay now or create a deferred payment instruction where enabled;
- view and act on payment instruction reminders;
- review updated quote, promotion, fee, card eligibility, or timing changes when returning to a deferred payment instruction;
- view partial funding, remaining amount, and partial payout status where applicable;
- review eligible discounts, coupon/voucher selection, reward status, or promotion quote where promotions are enabled;
- view payment status;
- view coupon/voucher library where enabled;
- view receipts/history.

### Payee

- register/login;
- verify phone by SMS OTP during registration;
- complete new-device 2FA and dormant-login reauthentication where required;
- dashboard;
- create payment request;
- upload evidence;
- review and correct autofilled evidence fields where applicable;
- send request to payer;
- view request status;
- view linked payments;
- respond to clarification/dispute;
- view payout/payment status.

### Admin

- login;
- operational dashboard;
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
- transaction-level revenue tracking;
- payment status reporting;
- payment instruction status reporting, including deferred, pending, partial funding, fully funded, expired, and cancelled states;
- partial payout status reporting for settlement-ready funded portions;
- user-level activity history;
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
| Reliability | Payment status and request status must remain consistent. |
| Auditability | Key user, admin, payment, and evidence actions must be logged. |
| Scalability | Architecture should support future automation and additional payment categories. |
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
- allow payee-created requests to trigger payment without payer acceptance;
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
- payer can accept, reject, dispute, or request clarification;
- payer can authorize payment;
- payment status can be tracked;
- payer and payee can view the same linked request/payment context;
- admin can review users, requests, evidence, and exceptions;
- no wallet balance or cashout behavior exists;
- all key actions are audit logged;
- prohibited flows are blocked;
- failed, rejected, disputed, and cancelled requests are handled clearly.

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
| OQ-05-012 | What configurable maximum number of credit cards per payment should be allowed at launch? | Product / Payments | Open |
| OQ-05-013 | Which OCR/document AI provider, confidence thresholds, and launch categories should be enabled first? | Product / Engineering / Risk | Open |
| OQ-05-014 | Which extracted fields are displayable, masked, or restricted by role and evidence category? | Product / Privacy / Security | Open |

---

## 21. Dependencies

| Dependency | Purpose |
|---|---|
| DOC-00 | Documentation governance and source-of-truth rules |
| DOC-01 | Product overview and positioning |
| DOC-02 | Business model and monetization |
| DOC-03 | Regulatory assessment |
| DOC-04 | Compliance control framework |
| DOC-06 | User journey, product flow, and UX scope |
| DOC-07 | User-facing disclosure, authorization, evidence, privacy, and policy wording |
| DOC-08 | Notifications, receipts, communication triggers, and delivery logging |
| DOC-09 | Payment request, funding, authorization, and settlement readiness |
| DOC-10 | Payout, payout readiness, payout destination, batching, and reconciliation |
| DOC-11 | Refund, cancellation, reversal, dispute, and chargeback handling |
| DOC-12 | Bill category, document AI/OCR, evidence verification, duplicate detection, and payee matching |
| DOC-14 | AML, anti-cashout, fake evidence, duplicate evidence, collusion, and risk controls |
| DOC-15 | Privacy, data protection, masking, retention, and lawful data use |
| DOC-17 | Third-party APIs including OCR/document AI, PSP, bank, and provider integrations |
| DOC-18 | Data model, evidence data layers, transaction state, audit events, ledger, and reporting |
| DOC-19 | Authentication, authorization, evidence access, security, and tokenization |
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

---

## 23. Revision History

| Version | Date | Summary |
|---|---|---|
| v0.1 | Initial Draft | Initial master PRD structure. |
| v0.2 | 2026-05-27 | Updated MVP to include both payer-created and payee-created payment requests; added two-sided user visibility, evidence-backed matching, linked payer/payee records, and simplified structure. |
| v0.3 | 2026-05-29 | Confirmed payee-created requests and tenancy/rent as MVP scope, added MVP gating and configuration rules, clarified that detailed data and UX design belong in downstream docs, and updated open questions. |
| v0.4 | 2026-05-30 | Aligned product requirements with updated DOC-01 scope for invoices, fees, rent, domestic service obligations, request delivery methods, and evidence-backed positioning. |
| v0.5 | 2026-05-30 | Aligned master PRD with DOC-12 by adding OCR/autofill, user correction, evidence verification outcomes, duplicate/reused evidence routing, sensitive field display controls, and explicit downstream document references. |
| v0.6 | 2026-06-01 | Aligned master PRD with DOC-13 by adding promotion quote, entitlement, coupon/voucher library, reward instrument, campaign data, and admin promotion-control references. |
| v0.7 | 2026-06-02 | Aligned master PRD with DOC-15 by adding privacy data classes, field-level classification metadata, authentication UX requirements, material-change confirmation, payment passcode, and admin sensitive-data access controls. |
| v0.8 | 2026-06-02 | Added DOC-09 user payment instruction as MVP scope for deferred single-card and split-card payment, payment-instruction reminders, partial funding, and partial payout visibility. |
| v0.9 | 2026-06-02 | Aligned PRD with DOC-09 and DOC-13 deferred payment instruction quote revalidation, promotion reservation, and return-to-checkout update review. |
| v0.10 | 2026-06-02 | Standardized coupon/voucher library wording to avoid stored-value confusion. |
