---
document_id: DOC-06
title: User Journey, UX Flow & Service Blueprint
version: 0.5.0
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-05-30
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06 - PayPlus User Journey, Product Flow, and UX Scope

## 1. Purpose

This document defines the required MVP user journeys, product flows, and UX scope for PayPlus.

PayPlus is an evidence-backed payment platform that allows payers and payees to create, view, match, authorize, and track bill, invoice, fee, rent, domestic service, and other approved obligation payment requests.

This document translates the master product requirements in DOC-05 into user-facing and operational journeys.

The MVP must support both:

1. **Payee-created payment request flow**
   - A payee creates an evidence-backed payment request and pushes it to a payer for review and payment.

2. **Payer-created payment flow**
   - A payer creates an evidence-backed payment or obligation record, links or invites a payee, and pushes payment to the payee after required review and authorization.

Both flows are MVP scope.

Tenancy and rent journeys are MVP scope. They must be independently enableable and may remain disabled for specific users, payees, categories, or launch phases until required controls are ready.

Domestic helper, driver, and personal service payment journeys are MVP scope where supported by acceptable evidence and enabled controls.

---

## 2. Product Journey Summary

PayPlus supports two-sided payment journeys between a payer and a payee.

A payment may originate from either side:

- a **payee** may create a bill, invoice, fee, rent, tenancy, agreement, employment/service record, statement, or other evidence-backed payment request and send it to a payer; or
- a **payer** may create a bill, invoice, fee, rent, tenancy, employment/service, or payment obligation record, link or invite a payee, and push payment to that payee.

In all cases:

- the payment must be linked to acceptable evidence unless an approved exception applies;
- the payer must review the request or payment context before payment;
- the payer must explicitly authorize payment before funds are charged or moved;
- the payee may view linked request/payment context when they are a platform user;
- admin, operational, or risk controls may apply;
- the system must maintain linked records, status history, receipts, and audit events;
- PayPlus must not operate as a wallet, stored-value account, cashout product, or unsupported peer-to-peer transfer service.

---

## 3. MVP Scope

### 3.1 In Scope

The MVP user journey scope includes:

- payer registration and login;
- payee registration and login;
- payer dashboard;
- payee dashboard;
- payer-created payment requests;
- payee-created payment requests;
- payer-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup;
- payee-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup;
- payee adoption or acceptance of payer-created records;
- payer review of payee-created requests;
- evidence upload, OCR/autofill review, user correction, and evidence verification;
- request matching and linked records;
- recipient review flows;
- payer acceptance, rejection, dispute, and clarification actions;
- payee acceptance, adoption, rejection, dispute, and clarification actions where applicable;
- payer authorization before payment;
- payment status tracking;
- payout or settlement status visibility where applicable;
- receipt or confirmation records;
- request history;
- basic notifications;
- admin review and operations workflows;
- audit trail visibility for admin;
- error, failure, dispute, cancellation, and exception states;
- controls preventing wallet, cashout, stored balance, and unsupported P2P behavior.

### 3.1.1 UX Scope Boundaries

This document defines journeys, screens, user decisions, service touchpoints, and visibility boundaries.

It should not duplicate detailed payment processing, payout, refund, notification, data model, risk rule, security, or compliance specifications. Where those details are needed, this document should identify the user-facing touchpoint and defer the detailed rule to the owning downstream document.

---

### 3.2 Out of Scope for MVP

The MVP user journey scope does not include:

- user wallet balances;
- stored-value accounts;
- user-controlled cash accounts;
- cash withdrawal;
- payer self-cashout;
- unsupported arbitrary peer-to-peer transfers;
- crypto payments;
- lending or credit issuance;
- investment, savings, or deposit account journeys;
- marketplace escrow journeys;
- unsupported open-loop money transfer journeys;
- automatic recurring payments unless separately approved;
- fully automated compliance approval without admin or risk controls;
- advanced analytics dashboards;
- multi-entity enterprise treasury workflows;
- public API self-service configuration;
- complex role delegation or multi-admin hierarchy unless separately approved.

---

## 4. User Roles

| Role | Description | MVP Login? | Key Journey Responsibilities |
| --- | --- | ---: | --- |
| Payer | User who reviews, accepts, rejects, disputes, requests clarification, and authorizes payment. | Yes | Create payments, review requests, authorize payment, track status. |
| Payee | User who receives payments or creates payment requests. | Yes | Create requests, upload evidence, send requests to payers, adopt payer-created records, track status. |
| Admin / Operations | Internal user who reviews accounts, evidence, requests, risk, disputes, and exceptions. | Yes | Review, approve, reject, hold, investigate, and audit. |
| System | Automated services handling status changes, notifications, matching, audit events, and integrations. | No | Route, link, notify, validate, and record events. |

---

## 5. Core MVP User Journeys

The MVP must support the following essential journeys:

| # | Journey | Required for MVP |
| ---: | --- | ---: |
| 1 | Payer registration and login | Yes |
| 2 | Payee registration and login | Yes |
| 3 | Payer dashboard | Yes |
| 4 | Payee dashboard | Yes |
| 5 | Payee-created payment request flow | Yes |
| 6 | Payer-created payment flow | Yes |
| 7 | Payee-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup | Yes |
| 8 | Payer-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup | Yes |
| 9 | Payee adoption of payer-created record | Yes |
| 10 | Payer review of payee-created request | Yes |
| 11 | Evidence upload, OCR/autofill review, correction, and verification | Yes |
| 12 | Accept, reject, dispute, and clarification flows | Yes |
| 13 | Payer payment authorization | Yes |
| 14 | Payment and payout status visibility | Yes |
| 15 | Linked payer/payee visibility | Yes |
| 16 | Admin review and operations touchpoints | Yes |
| 17 | Notification touchpoints | Yes |
| 18 | Receipt and history touchpoints | Yes |
| 19 | Failure, cancellation, dispute, and exception touchpoints | Yes |

---

## 6. Common Account Journey

### 6.1 Payer Account Journey

#### Purpose

Allows a payer to access PayPlus, create payments, review requests, authorize payment, and track payment history.

#### Required Payer Capabilities

A payer must be able to:

- register;
- log in;
- access a payer dashboard;
- create a payer-initiated payment;
- create or link a bill, invoice, tenancy, agreement, statement, or obligation record;
- enter or select payee details;
- upload or link evidence;
- review and correct autofilled evidence fields where applicable;
- receive payee-created payment requests;
- review evidence before payment;
- accept a request;
- reject a request;
- dispute a request;
- request clarification;
- authorize payment;
- view payment processing status;
- view failed payment status;
- view completed payment status;
- view receipts or confirmations;
- view request and payment history.

#### Payer Entry Points

The payer journey may begin when:

- the payer registers directly;
- the payer logs in to create a payment;
- the payer receives an invitation from a payee-created request;
- the payer receives a notification for a bill, invoice, tenancy, or payment request;
- the payer returns to view status or history.

---

### 6.2 Payee Account Journey

#### Purpose

Allows a payee to access PayPlus, create requests, upload evidence, send requests to payers, adopt payer-created records, and track payment or payout status.

#### Required Payee Capabilities

A payee must be able to:

- register;
- log in;
- access a payee dashboard;
- create a payment request;
- create or link a bill, invoice, tenancy, agreement, statement, or obligation record;
- enter or select payer details;
- upload or link evidence;
- review and correct autofilled evidence fields where applicable;
- send a request to a payer;
- receive payer-created bill/payment records;
- review payer-created records;
- accept or adopt payer-created records where applicable;
- reject payer-created records where applicable;
- dispute payer-created records where applicable;
- request clarification where applicable;
- respond to payer clarification requests;
- respond to disputes where applicable;
- view request status;
- view payment status;
- view payout or settlement status where applicable;
- view receipts or confirmations;
- view request and payment history.

#### Payee Entry Points

The payee journey may begin when:

- the payee registers directly;
- the payee logs in to create a request;
- the payee receives an invitation from a payer-created record;
- the payee receives notification of payment status;
- the payee returns to respond to a dispute or clarification request;
- the payee returns to view history.

---

## 7. Dashboard Journeys

### 7.1 Payer Dashboard

The payer dashboard should show:

- requests awaiting payer review;
- requests requiring payer clarification;
- draft payer-created payments;
- submitted payer-created payments;
- active payment requests;
- payment processing status;
- completed payments;
- failed payments;
- rejected, disputed, cancelled, or expired requests;
- receipts or confirmations;
- notifications;
- support or dispute entry points.

#### Payer Dashboard Actions

The payer should be able to:

- create a new payment;
- view received requests;
- review evidence;
- review or correct autofilled evidence fields;
- accept a request;
- reject a request;
- dispute a request;
- request clarification;
- authorize payment;
- view status;
- view receipt/history.

---

### 7.2 Payee Dashboard

The payee dashboard should show:

- draft payee-created requests;
- sent requests;
- payer-viewed requests;
- requests awaiting payer action;
- requests requiring payee clarification;
- payer-created records awaiting payee adoption;
- active linked payments;
- payment processing status;
- payout or settlement status where applicable;
- completed payments;
- failed payments;
- rejected, disputed, cancelled, or expired requests;
- receipts or confirmations;
- notifications;
- support or dispute entry points.

#### Payee Dashboard Actions

The payee should be able to:

- create a payment request;
- upload evidence;
- review or correct autofilled evidence fields;
- send a request to a payer;
- view request status;
- view payer action status;
- respond to clarification;
- respond to dispute;
- adopt or reject payer-created records where applicable;
- view linked payment status;
- view receipt/history.

---

## 8. Payee-Created Payment Request Flow

### 8.1 Purpose

Allows a payee to create an evidence-backed payment request and push it to a payer for review and payment.

This is a core MVP journey.

---

### 8.2 Primary Flow

1. Payee logs in.
2. Payee selects **Create Payment Request**.
3. Payee enters or selects payer information.
4. Payee enters request details:
   - amount;
   - due date;
   - category;
   - description;
   - reference number where applicable.
5. Payee creates or links an obligation record, such as:
   - bill;
   - invoice;
   - tenancy agreement;
   - rent demand;
   - payment statement;
   - service agreement;
   - official notice;
   - contract;
   - other acceptable proof of obligation.
6. Payee uploads or links evidence.
7. System processes evidence using OCR/document AI where enabled.
8. System autofills eligible fields and lets payee review or correct them.
9. System validates required fields, evidence verification outcome, duplicate/reused evidence indicators, and risk routing.
10. System creates a payment request record.
11. System links evidence and final evidence snapshot to the request.
12. System assigns request status.
13. Payee selects an available request delivery method, such as in-app message, app link, WhatsApp deeplink, QR code, or other approved channel.
14. System sends the request notification or invitation to the payer through the selected approved channel.
15. Payer logs in or registers.
16. Payer reviews:
    - payee identity/details;
    - amount;
    - due date;
    - category;
    - description;
    - evidence;
    - fees where applicable;
    - payment terms;
    - PayPlus disclosures where applicable.
17. Payer selects one of:
    - accept;
    - reject;
    - dispute;
    - request clarification.
18. If payer accepts, payer proceeds to payment authorization.
19. Payer explicitly authorizes payment.
20. System processes payment through approved payment partner or sandbox integration.
21. Payee receives payment according to approved payout or settlement rules.
22. Payer and payee can view the linked request/payment context.
23. System stores receipt, status history, and audit trail.

---

### 8.3 Payee-Created Request Status Path

A typical payee-created request may move through the following statuses:

```text
Draft
Submitted
Sent
Viewed
Accepted
Approved for Payment
Payment Authorized
Payment Processing
Paid
```

Alternative states may include:

```text
Clarification Requested
Rejected
Disputed
Failed
Cancelled
Expired
```

### 8.4 Required Controls

| Control | Requirement |
| --- | --- |
| Evidence required | Request cannot proceed to payment without required evidence unless an approved exception applies. |
| Evidence verification | OCR/autofill, user correction, duplicate detection, and verification outcomes follow DOC-12. |
| Payer review required | Payer must review the request context before payment authorization. |
| Payer authorization required | Payee-created request must not trigger payment without payer authorization. |
| Linked records required | Request, evidence, payer, payee, payment, status history, and audit events must be linked. |
| Admin/risk controls | Request may be subject to admin, operational, or risk review. |
| Unsupported P2P blocked | Request must be tied to a valid evidence-backed obligation. |

---

## 9. Payer-Created Payment Flow

### 9.1 Purpose

Allows a payer to create an evidence-backed payment or obligation record, link or invite a payee, and push payment to the payee after required review and authorization.

This is a core MVP journey.

### 9.2 Primary Flow

1. Payer logs in.
2. Payer selects **Create Payment**.
3. Payer enters or selects payee information.
4. Payer enters payment details:
   - amount;
   - due date;
   - category;
   - description;
   - reference number where applicable.
5. Payer creates or links an obligation record, such as:
   - bill;
   - invoice;
   - tenancy agreement;
   - rent demand;
   - payment statement;
   - service agreement;
   - official notice;
   - contract;
   - other acceptable proof of obligation.
6. Payer uploads or links evidence.
7. System processes evidence using OCR/document AI where enabled.
8. System autofills eligible fields and lets payer review or correct them.
9. System validates required fields, evidence verification outcome, duplicate/reused evidence indicators, and risk routing.
10. System creates a payment request or payment intent record.
11. System links evidence and final evidence snapshot to the record.
12. System matches payee if already a PayPlus user or creates an invite/link record.
13. System sends notification or invitation to payee where applicable.
14. Payee logs in or registers.
15. Payee reviews the payer-created record.
16. Payee selects one of:
    - accept/adopt;
    - reject;
    - dispute;
    - request clarification.
17. Admin/system reviews request and evidence according to applicable risk controls.
18. Payer reviews final payment summary.
19. Payer explicitly authorizes payment.
20. System processes payment through approved payment partner or sandbox integration.
21. Payee receives payment according to approved payout or settlement rules.
22. Payer and payee can view the linked payment context.
23. System stores receipt, status history, and audit trail.

### 9.3 Payer-Created Payment Status Path

A typical payer-created payment may move through the following statuses:

```text
Draft
Submitted
Sent
Viewed
Accepted
Approved for Payment
Payment Authorized
Payment Processing
Paid
```

Alternative states may include:

```text
Clarification Requested
Rejected
Disputed
Failed
Cancelled
Expired
```

### 9.4 Required Controls

| Control | Requirement |
| --- | --- |
| Evidence required | Payment cannot proceed without required evidence unless an approved exception applies. |
| Evidence verification | OCR/autofill, user correction, duplicate detection, and verification outcomes follow DOC-12. |
| Payee link required | Payee must be linked, invited, or represented by a valid payee record. |
| Payee adoption supported | Payee must be able to accept/adopt payer-created records where applicable. |
| Payer authorization required | Payment cannot be processed without explicit payer authorization. |
| Self-cashout blocked | Payer cannot use PayPlus to cash out to themselves. |
| Unsupported transfer blocked | Payment must be tied to a valid evidence-backed obligation. |
| No wallet behavior | System must not create user wallet balances or stored-value accounts. |

---

## 10. Shared Bill, Tenancy, Invoice, or Obligation Journey

### 10.1 Purpose

Allows either a payer or payee to create a shared obligation record that can support a payment request or payment.

An obligation record may represent:

- bill;
- invoice;
- tenancy agreement;
- rent demand;
- payment statement;
- service agreement;
- official notice;
- contract;
- other acceptable proof of payment obligation.

### 10.2 Payee-Created Obligation Path

1. Payee logs in.
2. Payee creates a bill, invoice, tenancy, agreement, statement, or obligation record.
3. Payee enters payer information.
4. Payee uploads supporting evidence.
5. System processes evidence and autofills eligible obligation fields where enabled.
6. Payee reviews or corrects autofilled fields.
7. System validates evidence and creates obligation record.
8. System links evidence and final evidence snapshot to obligation record.
9. Payee creates or sends payment request.
10. Payee selects an available request delivery method, such as in-app message, app link, WhatsApp deeplink, QR code, or other approved channel.
11. Payer is notified or invited through the selected approved channel.
12. Payer reviews the obligation, evidence summary, and request.
13. Payer accepts, rejects, disputes, or requests clarification.
14. If accepted, payer may authorize payment.
15. System links payer, payee, request, evidence, and payment records.

### 10.3 Payer-Created Obligation Path

1. Payer logs in.
2. Payer creates a bill, invoice, tenancy, agreement, statement, or obligation record.
3. Payer enters payee information.
4. Payer uploads supporting evidence.
5. System processes evidence and autofills eligible obligation fields where enabled.
6. Payer reviews or corrects autofilled fields.
7. System validates evidence and creates obligation record.
8. System links evidence and final evidence snapshot to obligation record.
9. Payee is notified or invited.
10. Payee logs in or registers.
11. Payee reviews the obligation and evidence summary.
12. Payee accepts/adopts, rejects, disputes, or requests clarification.
13. If adopted, payee becomes linked to the shared obligation context.
14. Payer may authorize payment.
15. System links payer, payee, obligation, evidence, and payment records.

### 10.4 Adoption Rules

| Rule | Requirement |
| --- | --- |
| Payee adoption | Payee may accept/adopt payer-created obligation records. |
| Payer acceptance | Payer may accept payee-created requests before authorizing payment. |
| No forced adoption | A recipient should not be forced to accept an inaccurate record. |
| Dispute support | Recipient may dispute or request clarification. |
| Linked context | Once accepted/adopted, both sides should see the linked context subject to permissions. |
| Audit trail | Adoption, rejection, clarification, and dispute actions must be logged. |

---

## 11. Recipient Review Journey

### 11.1 Purpose

Allows the recipient of a request or obligation record to review the details and respond.

### 11.2 Recipient Review Matrix

| Creator | Recipient | Recipient Review Actions |
| --- | --- | --- |
| Payee creates payment request | Payer | Accept, reject, dispute, request clarification, authorize payment after acceptance. |
| Payer creates payment/obligation record | Payee | Accept/adopt, reject, dispute, request clarification. |

### 11.3 Required Review Information

The recipient should be able to view:

- creator identity or profile details;
- payer details;
- payee details;
- amount;
- due date;
- category;
- description;
- evidence;
- obligation type;
- request status;
- payment status where applicable;
- fees where applicable;
- relevant disclosures;
- clarification or dispute history where applicable.

### 11.4 Recipient Actions

| Action | Description |
| --- | --- |
| Accept | Recipient accepts the request or record as valid. |
| Adopt | Payee accepts a payer-created bill, tenancy, invoice, or payment context as linked to them. |
| Reject | Recipient rejects the request or record. |
| Dispute | Recipient disputes the request, evidence, amount, payee, payer, or obligation context. |
| Request clarification | Recipient asks the creator for more information or correction. |
| Authorize payment | Payer-only action that permits payment processing. |

### 11.5 Payment Authorization Boundary

Only the payer can authorize payment.

A payee may accept or adopt a payer-created record, but a payee cannot authorize payment from the payer.

---

## 12. Evidence Upload and Review Journey

### 12.1 Purpose

Ensures each payment is linked to acceptable evidence before it can proceed to payment.

DOC-12 owns detailed bill category, OCR/document AI, extracted field, autofill, user correction, duplicate detection, verification outcome, and payee matching requirements. DOC-06 describes only the user journey and UX touchpoints.

### 12.2 Accepted MVP Evidence Types

MVP evidence may include:

- bill;
- invoice;
- tenancy agreement;
- rent demand;
- payment statement;
- service agreement;
- official notice;
- contract;
- uploaded PDF;
- uploaded image;
- manually entered bill details with supporting document;
- other admin-approved proof of payment obligation.

### 12.3 Evidence Upload and Verification Flow

1. User creates a request or obligation record.
2. User uploads or links evidence.
3. System validates file type and required metadata where applicable.
4. System processes OCR/document AI where enabled.
5. System extracts and autofills eligible fields.
6. User reviews and corrects autofilled fields before submission.
7. System stores raw evidence, extraction result, user correction, and final evidence snapshot where applicable.
8. System links evidence to the request or obligation.
9. System applies duplicate/reused evidence, mismatch, completeness, same-party, and risk checks.
10. System assigns an evidence verification outcome.
11. Low-risk evidence becomes available for role-based review and payment eligibility checks.
12. Red-flag evidence routes to user clarification or admin review.

### 12.4 Evidence Review Access

| Role | Evidence Access |
| --- | --- |
| Payer | Can review evidence before authorizing payment. |
| Payee | Can view evidence attached to their own created requests or linked received payments. |
| Admin / Operations | Can view evidence for review, investigation, support, compliance, and audit. |
| System | Links evidence to request/payment records and logs actions. |

### 12.5 Evidence Rules

| Rule | Requirement |
| --- | --- |
| Evidence required | Payment request cannot proceed to payment without required evidence unless an approved exception applies. |
| Evidence linked | Evidence must be linked to a payment request, obligation, or payment record. |
| OCR/autofill | Where enabled, extracted fields should assist request creation but must not remove user review. |
| User correction | Users must be able to correct autofilled fields before submission. |
| Extractable vs displayable | Sensitive extracted fields may be stored under controls without being shown broadly in UI. |
| Duplicate warning | Duplicate or reused evidence may trigger user warning and admin review, subject to DOC-12 and privacy rules. |
| Verification outcome | Pending user clarification, pending admin review, rejected, duplicate suspected, or fraud/risk escalated outcomes must block payment eligibility until resolved. |
| Payer review | Payer must be able to review evidence before authorizing payment. |
| Admin review | Admin must be able to view evidence for review and investigation. |
| Auditability | Evidence upload, view, replacement, and deletion actions must be logged where applicable. |
| Access control | Evidence visibility must be restricted by role and permissions. |

---

## 13. Clarification and Dispute Journey

### 13.1 Purpose

Allows payer, payee, or admin to resolve incomplete, disputed, incorrect, or unclear request information.

### 13.2 Clarification Flow

1. Recipient reviews request or obligation record.
2. Recipient selects **Request Clarification**.
3. Recipient enters clarification reason or question.
4. Recipient may identify the disputed or unclear field.
5. System updates status to **Clarification Requested**.
6. System notifies the other party.
7. Other party responds with:
   - text explanation;
   - corrected field;
   - additional evidence;
   - cancellation;
   - dispute escalation.
8. System logs all clarification activity.
9. Request returns to review, acceptance, rejection, dispute, or cancellation state.

### 13.3 Dispute Flow

1. User reviews request, obligation, payment, or evidence.
2. User selects **Dispute**.
3. User enters dispute reason.
4. User may upload additional evidence.
5. System updates status to **Disputed**.
6. System notifies the other party.
7. Admin may review the dispute where required.
8. Other party may respond.
9. Admin or system may move the request to:
   - clarification requested;
   - accepted;
   - rejected;
   - cancelled;
   - held;
   - resolved;
   - approved for payment where allowed.
10. System logs all dispute actions.

### 13.4 Required Dispute and Clarification Controls

| Control | Requirement |
| --- | --- |
| Linked thread | Clarification and dispute activity must remain linked to the original request. |
| Audit trail | All clarification and dispute actions must be logged. |
| Notification | Relevant parties must be notified of dispute or clarification events. |
| Admin visibility | Admin must be able to review dispute and clarification history. |
| Payment block | Disputed requests should not proceed to payment unless resolved under approved rules. |

---

## 14. Payment Authorization Journey

### 14.1 Purpose

Ensures that the payer explicitly authorizes payment after reviewing the required context.

### 14.2 Required Payer Authorization Information

Before authorization, the payer should be shown:

- payee;
- amount;
- service fee where applicable;
- total charge;
- due date;
- category;
- description;
- evidence;
- payment method;
- expected processing timing;
- expected payout or settlement timing where applicable;
- refund/reversal limitations where applicable;
- PayPlus role;
- relevant disclosures.

### 14.3 Authorization Flow

1. Payer reviews request or payer-created payment.
2. Payer confirms that evidence and payment details are acceptable.
3. System displays final payment summary.
4. System displays fee and total charge where applicable.
5. Payer selects or confirms payment method.
6. Payer accepts required terms or disclosures where applicable.
7. Payer confirms authorization.
8. System records authorization timestamp and authorization event.
9. Request status changes to **Payment Authorized**.
10. Payment processing begins through approved payment partner or sandbox integration.

### 14.4 Authorization Rules

| Rule | Requirement |
| --- | --- |
| Explicit consent | Payer must explicitly authorize payment. |
| No automatic payment | Payee-created request cannot automatically trigger payment. |
| Evidence visibility | Payer must be able to review evidence before payment. |
| Fee visibility | Fees charged to payer must be displayed before authorization. |
| Audit logging | Authorization must be logged. |
| No hidden material terms | Material payment information must not be hidden from payer. |

---

## 15. Payment and Payout Status Visibility

### 15.1 Purpose

Defines what users and admins need to see after payer authorization.

Detailed payment processing, payout, settlement, reconciliation, refund, reversal, chargeback, and exception rules belong in DOC-09, DOC-10, and DOC-11.

### 15.2 Required Visibility

| User | Required Visibility |
| --- | --- |
| Payer | Authorization result, payment status, failure state, cancellation/refund state where applicable, and receipt/history. |
| Payee | Request status, payer response, payment completion status, payout/settlement visibility where permitted, and exceptions requiring payee action. |
| Admin | Full request, payment, payout, failure, refund, dispute, exception, and audit context. |

### 15.3 UX Rules

| Rule | Requirement |
| --- | --- |
| Status clarity | User-facing labels must distinguish request status, payment status, and payout/settlement status. |
| No false certainty | The UX must not imply payment or payout is complete before the relevant system of record confirms it. |
| Role-appropriate visibility | Payees must not see sensitive payer payment method, risk, or private account data. |
| Exception visibility | Failures, holds, cancellations, refunds, and disputes must have clear user-facing states and admin review paths. |

---

## 16. Linked Records and Matching Journey

### 16.1 Purpose

Ensures that payer, payee, request, evidence, payment, payout, status, dispute, and audit records remain linked.

### 16.2 Required Linked Objects

Each active or completed payment should be linkable to:

- payer user;
- payee user or payee record;
- payment request;
- obligation record where applicable;
- evidence record;
- payment transaction;
- payout or settlement record where applicable;
- dispute or clarification thread where applicable;
- notification records;
- status history;
- audit events;
- admin review actions where applicable.

### 16.3 Matching Flow

1. Request or payment record is created.
2. System checks payer and payee identifiers.
3. System attempts to match existing users or records.
4. If no user exists, system creates an invitation or pending participant record.
5. Recipient registers or logs in.
6. System links recipient to request or obligation.
7. System displays shared context to both sides subject to permissions.
8. System checks for duplicate or suspicious records where applicable.
9. System logs matching and linking events.

### 16.4 Matching Requirements

| Requirement | Description |
| --- | --- |
| Shared request ID | Both payer and payee should reference the same payment request when both are users. |
| Linked evidence | Evidence record must link to request and payment context. |
| Two-sided visibility | Payer and payee must see the same underlying transaction context, subject to permissions. |
| Duplicate detection | System should help detect duplicate bills, requests, or payments. |
| Status consistency | Payer and payee views must reflect the same underlying status. |
| Dispute linkage | Disputes and clarifications must remain linked to the original request. |

---

## 17. Two-Sided Visibility and Permissions

### 17.1 Purpose

Allows both payer and payee to view linked request/payment context while protecting sensitive information.

### 17.2 Shared Visibility

Both payer and payee should be able to view:

- request ID;
- obligation type;
- amount;
- due date;
- category;
- description;
- evidence, subject to permissions;
- current request status;
- current payment status;
- clarification status;
- dispute status;
- completed payment confirmation;
- relevant history;
- relevant notifications.

### 17.3 Role-Based Visibility Boundaries

| Data | Payer View | Payee View | Admin View |
| --- | --- | --- | --- |
| Request details | Yes | Yes | Yes |
| Evidence | Yes, if linked to request/payment | Yes, if creator or linked participant | Yes |
| Payer identity | Yes | Yes, limited as appropriate | Yes |
| Payee identity | Yes | Yes | Yes |
| Payment method details | Yes, masked/limited | No | Limited/controlled |
| Payout account details | No or masked | Yes, masked/limited | Limited/controlled |
| Fees charged to payer | Yes | Limited or as applicable | Yes |
| Payout status | Limited or as applicable | Yes | Yes |
| Audit events | Limited user-facing history | Limited user-facing history | Yes |
| Risk flags | No | No | Yes |

### 17.4 Privacy and Permission Rules

| Rule | Requirement |
| --- | --- |
| Least privilege | Users should only see information needed for their role in the transaction. |
| Sensitive data masking | Payment and payout instrument details must be masked or restricted. |
| Admin access controls | Admin access must be permissioned and logged. |
| Evidence privacy | Evidence visibility must be limited to authorized users. |
| Consistent status | Status should remain consistent across payer and payee views. |

---

## 18. Request Status UX

### 18.1 Core Request Statuses

The MVP UX should expose clear user-facing request states. Canonical state-machine definitions belong in DOC-09 and DOC-18.

| Status | Meaning |
| --- | --- |
| Draft | Request created but not submitted. |
| Submitted | Request submitted for review or routing. |
| Evidence Processing | Evidence OCR, extraction, autofill, or verification is in progress. |
| Pending User Correction | User must review or correct extracted evidence fields. |
| Pending Evidence Review | Evidence requires admin or risk review before payment eligibility. |
| Sent | Request sent to payer or payee. |
| Viewed | Recipient viewed the request. |
| Clarification Requested | Recipient or admin requested more information. |
| Accepted | Payer accepted the request or recipient accepted the record. |
| Rejected | Recipient rejected the request or record. |
| Disputed | Payer or payee disputed the request or record. |
| Approved for Payment | Required checks passed before payment. |
| Payment Authorized | Payer authorized payment. |
| Payment Processing | Payment is being processed. |
| Paid | Payment completed. |
| Failed | Payment failed. |
| Cancelled | Request cancelled. |
| Expired | Request expired. |

### 18.2 Status Rules

| Rule | Requirement |
| --- | --- |
| Payer authorization | No payment may be processed without payer authorization. |
| Evidence gate | Request cannot move to Approved for Payment without required evidence or approved exception. |
| Verification gate | Request cannot move to Approved for Payment while DOC-12 evidence verification requires correction, admin review, rejection handling, duplicate review, or fraud/risk escalation. |
| Admin/risk gate | Requests may require admin or risk approval before payment. |
| Rejection handling | Rejected requests cannot be paid unless recreated or reopened under approved rules. |
| Dispute handling | Disputed requests should not proceed to payment unless resolved under approved rules. |
| Audit trail | Every status change must be logged. |
| Two-sided consistency | Payer and payee views must reflect the same underlying status. |

---

## 19. Admin and Operations Journey

### 19.1 Purpose

Allows internal users to review accounts, requests, evidence, risk, disputes, payouts, settlement, failures, and exceptions.

### 19.2 Admin Capabilities

Admins must be able to:

- log in;
- access an operational dashboard;
- view payer accounts;
- view payee accounts;
- view payment requests;
- view obligation records;
- view evidence;
- review new payees;
- review high-risk requests;
- approve requests where applicable;
- reject requests where applicable;
- hold requests where applicable;
- request clarification;
- investigate duplicates;
- review disputes;
- review payment status;
- review payout or settlement status where applicable;
- manage failed payment exceptions;
- manage payout exceptions where applicable;
- manage refund or reversal workflows where applicable;
- access audit logs.

### 19.3 Admin Review Flow

1. Request, user, evidence, dispute, or payment is flagged for review.
2. Admin opens review queue.
3. Admin reviews relevant context:
   - payer;
   - payee;
   - request;
   - amount;
   - evidence;
   - extracted fields and user corrections where applicable;
   - evidence verification outcome;
   - status history;
   - duplicate indicators;
   - risk indicators;
   - dispute or clarification history.
4. Admin selects an action:
   - approve;
   - reject;
   - hold;
   - request clarification;
   - escalate;
   - mark duplicate;
   - cancel;
   - resolve.
5. System updates status where applicable.
6. System notifies relevant users where applicable.
7. System logs admin action.

### 19.4 Admin Control Rules

| Rule | Requirement |
| --- | --- |
| Permissioned access | Admin access must be role-based and controlled. |
| Logged actions | Admin actions must be audit logged. |
| Evidence access | Admin must be able to review evidence. |
| OCR review support | Admin must be able to review extracted fields, user corrections, verification outcomes, and duplicate indicators where applicable. |
| Exception handling | Admin must be able to manage operational exceptions. |
| No silent overrides | Admin overrides must be traceable. |
| Risk review support | MVP must support manual review where risk rules require it. |

---

## 20. Notification Touchpoints

### 20.1 Purpose

Identifies where notifications are needed in the user journey. Notification content, templates, channels, preferences, retry behavior, and audit rules belong in DOC-08.

### 20.2 User Notifications

The MVP should support basic notifications for:

- account registration;
- payment request created;
- payment request received;
- request viewed;
- clarification requested;
- clarification response received;
- request accepted;
- request rejected;
- request disputed;
- payer-created record awaiting payee adoption;
- payee adopted payer-created record;
- payment authorized;
- payment processing;
- payment completed;
- payment failed;
- payout completed where applicable;
- request cancelled;
- request expired.

### 20.3 Admin Notifications or Queues

The MVP should support admin queues or notifications for:

- request requiring review;
- high-risk request;
- missing or invalid evidence;
- evidence verification review required;
- duplicate or reused evidence warning;
- new payee review;
- duplicate suspected;
- dispute opened;
- clarification unresolved;
- payment failed;
- payout failed where applicable;
- refund or reversal review where applicable;
- operational exception.

### 20.4 Notification Channels

Notification channels may include:

- app notifications;
- push notifications;
- email;
- SMS;
- WhatsApp;
- dashboard task;
- other approved channels.

Final channel routing, user preferences, templates, retry behavior, consent rules, and audit requirements should be defined in DOC-08 and implementation planning.

---

## 21. Receipt and History Touchpoints

### 21.1 Purpose

Identifies where users and admins need access to prior actions, statuses, confirmations, and payment outcomes. Receipt content and records policy belong in DOC-08, DOC-15, DOC-18, and payment-domain docs.

### 21.2 User History

Payers and payees should be able to view:

- created requests;
- received requests;
- linked obligation records;
- evidence records subject to permissions;
- request status;
- payment status;
- payout status where applicable;
- clarification history;
- dispute history;
- completed payment records;
- failed payment records;
- rejected requests;
- cancelled requests;
- expired requests;
- receipts or confirmations.

### 21.3 Receipt or Confirmation Contents

A receipt or confirmation should include:

- request ID;
- payment ID where applicable;
- payer;
- payee;
- amount;
- fees where applicable;
- total charged where applicable;
- payment status;
- payment date/time;
- evidence or obligation reference;
- payment method summary where appropriate;
- payout or settlement status where appropriate;
- confirmation reference where applicable.

### 21.4 History Rules

| Rule | Requirement |
| --- | --- |
| Traceability | User-visible history must link to the underlying request/payment context. |
| Role permissions | History must show role-appropriate information. |
| Audit separation | User history is not the same as full admin audit logs. |
| Failed states | Failed, rejected, disputed, cancelled, and expired states must remain visible. |
| Receipt storage | Completed payments should have receipt or confirmation records. |
| Retention baseline | Receipt, payment, account, tax, and audit records are expected to be retained for 7 years, subject to final privacy and legal review. |

---

## 22. Error, Failure, Cancellation, and Exception Journeys

### 22.1 Failed Payment

1. Payment processing fails.
2. System updates status to **Failed**.
3. System records failure reason where available.
4. Payer is notified.
5. Payee is notified where applicable.
6. Admin can review failure.
7. User may retry only if allowed by approved rules.

### 22.2 Cancelled Request

1. Eligible user or admin cancels request.
2. System checks whether cancellation is allowed.
3. System updates status to **Cancelled**.
4. System notifies relevant parties.
5. System logs cancellation event.
6. Cancelled request cannot be paid unless recreated or reopened under approved rules.

### 22.3 Expired Request

1. Request passes expiry date or expiry condition.
2. System updates status to **Expired**.
3. System notifies relevant parties.
4. Expired request cannot be paid unless renewed, recreated, or reopened under approved rules.

### 22.4 Duplicate Request

1. System or admin detects possible duplicate request, duplicate evidence, or reused evidence.
2. User may be warned that the evidence appears to have been used before, subject to DOC-12 privacy and anti-tipping-off rules.
3. Request is flagged for review where configured.
4. Admin reviews duplicate indicators.
5. Admin may hold, reject, clarify, or allow request.
6. System logs duplicate review outcome.

### 22.5 Refund or Reversal

1. Refund or reversal need is identified.
2. Admin reviews request, payment, evidence, and status history.
3. Admin follows approved operational process.
4. System records refund or reversal status.
5. Payer and payee are notified where applicable.
6. System logs all actions.

Refund and reversal rules belong in DOC-11. Payment, payout, reconciliation, and admin workflow details belong in DOC-09, DOC-10, DOC-18, DOC-21, and DOC-22.

---

## 23. Prohibited Journey Controls

PayPlus must prevent the following journeys:

| Prohibited Journey | Required Control |
| --- | --- |
| Wallet balance creation | Do not show or maintain user wallet balances. |
| Stored-value account use | Do not allow users to store funds for later discretionary use. |
| Cash withdrawal | Do not provide withdrawal functionality. |
| Payer self-cashout | Block payer from paying themselves or equivalent self-cashout patterns. |
| Unsupported P2P transfer | Require evidence-backed obligation and approved category. |
| Payment without payer authorization | Require explicit payer authorization before payment. |
| Payment without evidence | Require evidence or approved exception before payment. |
| Payee-triggered automatic payment | Payee request must be reviewed and authorized by payer. |
| Hidden material payment terms | Show material amount, fee, payee, evidence, and payment context before authorization. |
| Untraceable payment | Link request, evidence, payer, payee, transaction, status, and audit history. |
| Bypassed risk controls | Apply admin/risk gates where required. |
| Deposit representation | Do not represent funds as deposits or bank account balances. |

---

## 24. UX Scope

### 24.1 Payer UX Screens

The MVP should include payer-facing screens for:

- registration;
- login;
- payer dashboard;
- create payment;
- create or link bill/invoice/tenancy/obligation;
- enter payee details;
- upload evidence;
- review or correct autofilled evidence fields;
- view duplicate/reused evidence warning where applicable;
- received request list;
- request detail;
- evidence review;
- accept/reject/dispute/request clarification;
- payment authorization;
- payment processing status;
- payment completed status;
- failed payment status;
- receipt/history;
- notifications;
- account/profile basics.

### 24.2 Payee UX Screens

The MVP should include payee-facing screens for:

- registration;
- login;
- payee dashboard;
- create payment request;
- create or link bill/invoice/tenancy/obligation;
- enter payer details;
- select request delivery method;
- upload evidence;
- review or correct autofilled evidence fields;
- view duplicate/reused evidence warning where applicable;
- send request;
- sent request list;
- received payer-created record list;
- payer-created record detail;
- accept/adopt/reject/dispute/request clarification;
- clarification response;
- dispute response;
- payment status;
- payout or settlement status where applicable;
- receipt/history;
- notifications;
- account/profile basics.

### 24.3 Admin UX Screens

The MVP should include admin-facing screens for:

- admin login;
- operations dashboard;
- request review queue;
- evidence review;
- OCR/extracted field review;
- duplicate or reused evidence review;
- payer account view;
- payee account view;
- payee review queue;
- risk review queue;
- duplicate review;
- dispute review;
- clarification review;
- payment status view;
- payout or settlement status view where applicable;
- failed payment exception view;
- refund/reversal review where applicable;
- audit log view.

### 24.4 System UX and Service Touchpoints

The MVP should include system-level handling for:

- record creation;
- participant matching;
- invitation routing;
- status updates;
- evidence linking;
- OCR/autofill processing where enabled;
- evidence verification outcome routing;
- duplicate detection support;
- notification events;
- payment partner status updates;
- payout or settlement updates where applicable;
- audit event creation;
- error handling;
- admin queue routing.

---

## 25. Non-Functional UX Requirements

| Area | Requirement |
| --- | --- |
| Clarity | Users must understand what they are requesting, paying, accepting, or authorizing. |
| Evidence visibility | Payer must be able to review evidence before payment authorization. |
| Evidence correction | Users must be able to review and correct autofilled evidence fields before submission where OCR/autofill is enabled. |
| Sensitive field minimization | UI must display only fields needed for the user task; broader extractable evidence data belongs behind controlled access. |
| Status transparency | Users must see clear status for pending, processing, completed, failed, disputed, rejected, cancelled, and expired requests. |
| Permissioning | Users must only see data appropriate to their role. |
| Auditability | Key actions must generate audit events. |
| Error handling | Failed, blocked, or incomplete actions must show clear next steps. |
| Accessibility | MVP UX should follow basic accessibility principles. |
| Mobile readiness | Core flows should be usable on common mobile screen sizes. |
| Security | Sensitive payment, identity, evidence, and payout details must be protected. |
| Compliance readiness | UX must support evidence, authorization, review, dispute, and traceability requirements. |

---

## 26. MVP Acceptance Criteria

The DOC-06 user journey scope is satisfied when:

- payers can register and log in;
- payees can register and log in;
- payers have a dashboard;
- payees have a dashboard;
- payees can create evidence-backed payment requests;
- payees can send payment requests to payers;
- payers can receive and review payee-created requests;
- payers can create evidence-backed payments or obligation records;
- payers can link or invite payees;
- payees can review payer-created records;
- payees can accept/adopt payer-created records where applicable;
- users can upload evidence;
- OCR/document AI can process evidence where enabled;
- users can review and correct autofilled evidence fields where applicable;
- evidence is linked to the request or obligation;
- evidence verification outcomes can route to payment eligibility, user clarification, or admin review;
- payer can review evidence before payment;
- payer can accept, reject, dispute, or request clarification;
- payee can respond to clarification or dispute where applicable;
- payer can explicitly authorize payment;
- payment status can be tracked;
- payout or settlement status can be tracked where applicable;
- payer and payee can view the same linked request/payment context subject to permissions;
- admin can review users, requests, evidence, disputes, and exceptions;
- key status changes are audit logged;
- receipts or confirmations are available for completed payments;
- failed, rejected, disputed, cancelled, and expired requests are handled clearly;
- wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are blocked.

---

## 27. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06-001 | What exact UX distinction should exist between a payment request, obligation record, bill record, and payment transaction? | Product / Design | Open |
| OQ-06-002 | Which payer-created records require payee adoption before payment can proceed? | Product / Operations | Open |
| OQ-06-003 | Which payee-created request categories require admin review before payer authorization? | Risk / Operations | Open |
| OQ-06-004 | Which evidence categories are accepted at MVP launch? | Product / Compliance | Open |
| OQ-06-005 | Which rent and tenancy journey controls must be ready before initial launch enablement? | Product / Legal / Risk | Open |
| OQ-06-006 | What final KYC/KYB screens, provider handoff, failure states, exception states, and risk-tier steps are required for the baseline onboarding model? | Compliance / Legal | Open |
| OQ-06-007 | What payment methods are available to payers at MVP launch? | Payments / Product | Open |
| OQ-06-008 | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Operations | Open |
| OQ-06-009 | What fee disclosures must be shown before payment authorization? | Business / Legal | Open |
| OQ-06-010 | What dispute states and resolution outcomes are required for MVP? | Operations / Legal | Open |
| OQ-06-011 | What refund or reversal journeys are supported in MVP? | Payments / Operations | Open |
| OQ-06-012 | What routing, preferences, templates, consent rules, and fallback behavior apply across app, push, email, SMS, and WhatsApp notifications? | Product / Engineering | Open |
| OQ-06-013 | What admin roles and permission levels are required? | Operations / Security | Open |
| OQ-06-014 | What information should be hidden or masked between payer and payee? | Product / Security / Legal | Open |
| OQ-06-015 | What duplicate detection signals are required for MVP? | Risk / Engineering | Open |
| OQ-06-016 | What OCR/autofill review UI is required for each evidence category? | Product / Design | Open |
| OQ-06-017 | What duplicate/reused evidence warning can be shown without over-disclosing sensitive information? | Product / Legal / Privacy | Open |

---

## 28. Dependencies

| Dependency | Purpose |
| --- | --- |
| DOC-00 | Documentation governance and source-of-truth rules. |
| DOC-01 | Product overview and positioning. |
| DOC-02 | Business model, pricing, fee logic, and monetization. |
| DOC-03 | Regulatory assessment. |
| DOC-04 | Compliance control framework. |
| DOC-05 | Master product requirements and MVP scope. |
| DOC-07 | User-facing disclosure, authorization, evidence, privacy, and policy wording. |
| DOC-08 | Notification templates, channels, triggers, user preferences, and delivery logging. |
| DOC-09 | Payment request, funding, authorization, and settlement readiness. |
| DOC-10 | Payout, payout readiness, payout destination, batching, and reconciliation. |
| DOC-11 | Refund, cancellation, reversal, dispute, and chargeback handling. |
| DOC-12 | Bill category, document AI/OCR, evidence verification, duplicate detection, and payee matching. |
| DOC-14 | AML, anti-cashout, fake evidence, duplicate evidence, collusion, and risk controls. |
| DOC-15 | Privacy, data protection, masking, retention, and lawful data use. |
| DOC-18 | Request, obligation, evidence, payment, payout, audit, ledger, reporting, and participant data objects. |
| DOC-19 | Authentication, authorization, evidence access, data protection, and privacy controls. |
| DOC-21 | Monitoring, support escalation, incident handling, and operations runbooks. |
| DOC-22 | Admin review, risk, dispute, exception, support, configuration, and override workflows. |
| Future UX Wireframes | Defines screen-level UX and interaction design. |

---

## 29. Decision Summary

| Decision | Status |
| --- | --- |
| Payer registration and login are MVP scope. | Confirmed |
| Payee registration and login are MVP scope. | Confirmed |
| Payer dashboard is MVP scope. | Confirmed |
| Payee dashboard is MVP scope. | Confirmed |
| Payee-created payment requests are MVP scope. | Confirmed |
| Payer-created payments are MVP scope. | Confirmed |
| Tenancy and rent journeys are MVP scope. | Confirmed |
| Payee-created bill, invoice, tenancy, or obligation setup is MVP scope. | Confirmed |
| Payer-created bill, invoice, tenancy, or obligation setup is MVP scope. | Confirmed |
| Payee adoption of payer-created records is supported where applicable. | Confirmed |
| Payer review and authorization are required before payment. | Confirmed |
| Evidence-backed payments are required unless approved exception applies. | Confirmed |
| OCR/document AI-assisted evidence capture, autofill, user correction, duplicate warning, and evidence verification routing are required UX touchpoints where enabled. | Confirmed |
| Linked payer/payee visibility is required subject to permissions. | Confirmed |
| Admin/risk review support is required. | Confirmed |
| Wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are prohibited. | Confirmed |
| Final payment processor, operating-bank setup, detailed KYC/KYB steps, fees, multi-card card-count limit, and dispute policy details remain open or to be confirmed. | Open |
| Major functions and modules must be independently disableable. | Confirmed |

---

## 30. Revision History

| Version | Date | Summary |
| --- | --- | --- |
| v0.1 | 2026-05-27 | Initial DOC-06 draft aligned to DOC-05 v0.2; includes payer-created and payee-created MVP journeys, payee onboarding/login, bill/tenancy setup, adoption flow, evidence review, two-sided visibility, admin operations, and prohibited journey controls. |
| v0.2 | 2026-05-29 | Confirmed tenancy/rent journeys as MVP scope, added UX scope boundaries, clarified independent module disablement, and reduced overlap with payment, notification, receipt, and data specifications. |
| v0.3 | 2026-05-30 | Aligned user journeys with updated DOC-01 scope for invoices, fees, rent, domestic service obligations, and evidence-backed positioning. |
| v0.4 | 2026-05-30 | Added explicit payee-created request delivery method selection for in-app message, app link, WhatsApp deeplink, QR code, or other approved channel. |
| v0.5 | 2026-05-30 | Aligned UX flows with DOC-12 by adding OCR/autofill review, user correction, evidence verification outcomes, duplicate/reused evidence warning, sensitive field display boundaries, and explicit downstream document references. |
