# DOC-05 — PayPlus Master Product Requirements Document

## Document Control

| Field | Value |
|---|---|
| Document ID | DOC-05 |
| Document Name | PayPlus Master Product Requirements Document |
| Product | PayPlus |
| Version | v0.2 |
| Status | Draft |
| Owner | Product / Founder |
| Last Updated | 2026-05-27 |
| Related Docs | DOC-00, DOC-01, DOC-02, DOC-03, DOC-04 |

---

## 1. Purpose

This document defines the master product requirements for PayPlus.

PayPlus is a bill-backed payment platform that allows payers and payees to create, view, match, authorize, and track evidence-backed payment requests.

This document establishes the MVP product scope, core roles, required flows, controls, exclusions, and acceptance criteria.

---

## 2. Product Summary

PayPlus enables a user to make or request a payment when the payment is supported by a bill, invoice, tenancy document, agreement, statement, or other acceptable evidence.

The MVP supports both:

1. **Payer-created payment flow**
   - A payer creates a payment request and pushes a payment to a payee.

2. **Payee-created payment request flow**
   - A payee creates a bill-backed payment request and sends it to a payer for review and payment.

Both flows are core MVP features.

PayPlus is not a wallet, stored-value account, cashout product, open-loop money transfer product, or arbitrary peer-to-peer payment service.

---

## 3. MVP Scope

### 3.1 In Scope

The MVP includes:

- payer account registration and login;
- payee account registration and login;
- payer-created payment requests;
- payee-created payment requests;
- evidence-backed bill, invoice, tenancy, or document upload;
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
- marketplace escrow;
- investment, savings, or deposit accounts;
- open-loop funds transfer unrelated to a bill or evidence-backed obligation;
- fully automated compliance approval without admin or risk controls.

---

## 4. Product Principles

| Principle | Requirement |
|---|---|
| Evidence-backed payments | Every payment must be linked to a bill, invoice, tenancy, agreement, statement, or acceptable proof of obligation. |
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
6. System creates a payment request record.
7. Payee may be invited, matched, or linked if already a PayPlus user.
8. Admin/system reviews request and evidence according to risk controls.
9. Payer authorizes payment.
10. Payment is processed through approved payment partners.
11. Payee receives payment according to approved settlement/payout rules.
12. Both payer and payee can view the linked payment record when both are users.
13. System stores receipt, status history, and audit trail.

---

## 6.2 Payee-Created Payment Request Flow

The payee-created flow allows a payee to request payment from a payer.

### Flow

1. Payee logs in.
2. Payee creates a payment request.
3. Payee enters payer information or selects an existing payer.
4. Payee adds amount, due date, category, and description.
5. Payee uploads or links evidence, such as invoice, bill, tenancy agreement, or statement.
6. System creates a payment request record.
7. Payer is notified or invited to view the request.
8. Payer logs in or registers.
9. Payer reviews the request, evidence, amount, and payee details.
10. Payer accepts, rejects, disputes, or requests clarification.
11. If accepted, payer authorizes payment.
12. Payment is processed through approved payment partners.
13. Payee receives payment according to approved settlement/payout rules.
14. Both payer and payee can view the linked bill/request/payment record.
15. System stores receipt, status history, and audit trail.

---

## 7. Evidence Requirements

Every payment request must be supported by acceptable evidence.

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
| Payer review | Payer must be able to review evidence before authorizing payment. |
| Payee review | Payee must be able to view evidence attached to their own created requests or linked received payments. |
| Admin review | Admin must be able to view evidence for review, investigation, and support. |
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
| Linked bill/payment | The bill, invoice, tenancy, or evidence record must link to the payment record. |
| Two-sided visibility | Payer and payee must be able to view the same linked transaction context, subject to permissions. |
| Duplicate detection | System should help detect duplicate requests or duplicate payments. |
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
| No unsupported transfer | Payment cannot be unrelated to a bill, invoice, tenancy, or proof of obligation. |
| No stored balance | PayPlus must not hold user wallet balances. |
| Failed payment handling | Failed payments must be visible and traceable. |
| Refunds/reversals | Refunds or reversals require controlled operational process. |

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

Notification channels may include email, in-app notification, or other approved channels.

---

## 14. Data Requirements

The MVP should support data structures for:

- users;
- payer profile;
- payee profile;
- payment request;
- evidence/document;
- request participant mapping;
- payment transaction;
- payout/settlement record;
- dispute or clarification thread;
- notification;
- audit event;
- admin review action.

Detailed data model requirements should be defined in a later technical/data document.

---

## 15. UX Requirements

The MVP should include user interfaces for:

### Payer

- register/login;
- dashboard;
- create payment;
- view received requests;
- review evidence;
- accept/reject/dispute request;
- authorize payment;
- view payment status;
- view receipts/history.

### Payee

- register/login;
- dashboard;
- create payment request;
- upload evidence;
- send request to payer;
- view request status;
- view linked payments;
- respond to clarification/dispute;
- view payout/payment status.

### Admin

- login;
- operational dashboard;
- request review queue;
- evidence review;
- user/payee review;
- payment status view;
- dispute/exception handling;
- audit log access.

---

## 16. MVP Business Requirements

The MVP should support:

- configurable service fee model;
- fee display before payer authorization;
- transaction-level revenue tracking;
- payment status reporting;
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
| Privacy | Restrict payer/payee visibility according to permissions. |
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
| OQ-05-002 | What onboarding/KYC/KYB level is required for payers and payees? | Compliance / Legal | Open |
| OQ-05-003 | Which evidence categories are accepted at launch? | Product / Compliance | Open |
| OQ-05-004 | Are rent and tenancy payments fully in MVP or controlled beta? | Product | Open |
| OQ-05-005 | What transaction limits apply by user type and category? | Risk / Product | Open |
| OQ-05-006 | What admin review rules are mandatory before payment or payout? | Operations / Risk | Open |
| OQ-05-007 | What fees are charged and to whom? | Business / Product | Open |
| OQ-05-008 | What payout methods are supported for payees? | Payments / Operations | Open |
| OQ-05-009 | What data retention rules apply to evidence documents? | Legal / Compliance | Open |
| OQ-05-010 | What dispute process applies after payment completion? | Operations / Legal | Open |

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
| Future Data Model Doc | Defines database objects and relationships |
| Future Payment Flow Doc | Defines payment authorization, processing, payout, refund, and failure states |
| Future Admin Ops Doc | Defines admin review, risk, dispute, and exception handling |
| Future Security Doc | Defines authentication, authorization, data protection, and privacy controls |

---

## 22. Decision Summary

| Decision | Status |
|---|---|
| Payer-created payment requests are MVP scope. | Confirmed |
| Payee-created payment requests are MVP scope. | Confirmed |
| Payers can log in. | Confirmed |
| Payees can log in. | Confirmed |
| Every payment should be evidence-backed. | Confirmed |
| Payer must authorize payment before funds movement. | Confirmed |
| Linked payer/payee views are required. | Confirmed |
| Wallet, cashout, and unsupported P2P are prohibited. | Confirmed |
| Future docs should use concise product-spec structure. | Confirmed |

---

## 23. Revision History

| Version | Date | Summary |
|---|---|---|
| v0.1 | Initial Draft | Initial master PRD structure. |
| v0.2 | 2026-05-27 | Updated MVP to include both payer-created and payee-created payment requests; added two-sided user visibility, evidence-backed matching, linked payer/payee records, and simplified structure. |
