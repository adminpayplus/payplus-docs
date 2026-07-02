---
document_id: DOC-06A
title: Core User Journeys & Service Blueprint
version: 0.1.4
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
last_updated: 2026-07-02
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06A - Core User Journeys & Service Blueprint

## 1. Purpose

DOC-06A is the DOC-06 child document for core PayPlus user journeys and service blueprint touchpoints.

It governs payer, payee, admin, operations, system, evidence, review, authorization, status, visibility, notification, receipt, failure, cancellation, dispute, and exception journeys at the human-readable product level.

## 2. Scope Boundary

DOC-06A owns high-level journey and service behavior. It does not own detailed app navigation taxonomy, detailed Bills/rent/tenancy route UI, checkout processing rules, evidence verification algorithms, data schema, notification templates, or admin workflow design.

Detailed navigation and route taxonomy belong to DOC-06B. Detailed Bills/rent/tenancy route behavior belongs to DOC-06C. UX requirements and test mapping belong to DOC-06D.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Core account journeys | Working baseline | Needs later route and screen linkage. |
| Payee-created and payer-created journeys | Working baseline | Detailed request and payment state models remain linked to DOC-09 and DOC-18. |
| Evidence and review journeys | Working baseline | Detailed verification remains DOC-12. |
| Authorization and status visibility | Working baseline | Checkout behavior remains DOC-09. |
| Exception journeys | Working baseline | Refund/dispute/chargeback detail remains DOC-11 and DOC-22. |

## 4. Service Blueprint Ownership

When future edits add service-blueprint tables, use these columns:

| Column | Meaning |
| --- | --- |
| User Step | What the user is trying to do. |
| Frontstage UX | What the user sees or confirms. |
| Backstage System | Validation, routing, notification, risk, or integration behavior. |
| Risk / Compliance Touchpoint | Evidence, authorization, privacy, AML, fraud, or audit control. |
| State / Event | User-visible state or material event signal. |
| Owning Doc | Source document owning detailed behavior. |

---

## 5. Core User Journeys and Service Blueprint

### Core MVP User Journeys

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
| 9 | Optional payee adoption or linking of payer-created record | Yes |
| 10 | Payer review of payee-created request | Yes |
| 11 | Evidence upload, OCR/autofill review, correction, and verification | Yes |
| 12 | Accept, reject, and exception/support flows | Yes |
| 13 | Payer payment authorization | Yes |
| 14 | User payment instruction and deferred payment action | Yes |
| 15 | Payment and payout status visibility | Yes |
| 16 | Linked payer/payee visibility | Yes |
| 17 | Admin review and operations touchpoints | Yes |
| 18 | Notification touchpoints | Yes |
| 19 | Receipt and history touchpoints | Yes |
| 20 | Failure, cancellation, dispute, and exception touchpoints | Yes |

---

---

### Common Account Journey

#### Payer Account Journey

#### Purpose

Allows a payer to access PayPlus, create payments, review requests, authorize payment, and track payment history.

#### Required Payer Capabilities

A payer must be able to:

- register;
- verify phone by SMS OTP during registration;
- log in;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm material account, credential, payment profile, or contact changes using password, payment passcode, 2FA, or approved confirmation;
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
- escalate a query, dispute, or support issue through the approved exception flow where applicable;
- authorize payment;
- enter payment passcode before proceeding with payment authorization;
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

#### Payee Account Journey

#### Purpose

Allows a payee to access PayPlus, create requests, upload evidence, send requests to payers, adopt payer-created records, and track payment or payout status.

#### Required Payee Capabilities

A payee must be able to:

- register;
- verify phone by SMS OTP during registration;
- log in;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm material account, credential, payout destination, or contact changes using password, payment passcode, 2FA, or approved confirmation;
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
- escalate a query, dispute, or support issue through the approved exception flow where applicable;
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
- the payee returns to respond to a support, query, dispute, or exception case;
- the payee returns to view history.

---

---

### Payee-Created Payment Request Flow

#### Purpose

Allows a payee to create an evidence-backed payment request and push it to a payer for review and payment.

Within DOC-06A, a request is not a payment. A request asks another party to review, accept, link to, clarify, reject, or dispute a bill, tenancy, rent, invoice, fee, or approved obligation context. Acceptance links the parties to that accepted context and may support later payment readiness, but it does not authorize, process, or complete payment.

This is a core MVP journey.

---

#### Primary Flow

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
14. System sends the request notification or invitation to the payer through the selected approved channel only after required evidence is verified or approved by exception.
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
    - reject with reason where required.
18. If payer accepts, payer proceeds to payment authorization.
19. Payer explicitly authorizes payment.
20. System processes payment through approved payment partner or sandbox integration.
21. Payee receives payment according to approved payout or settlement rules.
22. Payer and payee can view the linked request/payment context.
23. System stores receipt, status history, and audit trail.

---

#### Payee-Created Request Status Path

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
Rejected
Additional Information Required
Linked Support / Dispute Case
Failed
Cancelled
Expired
```

#### Required Controls

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

---

### Payer-Created Payment Flow

#### Purpose

Allows a payer to create an evidence-backed payment or obligation record, link or invite a payee, and push payment to the payee after required review and authorization.

This is a core MVP journey.

#### Primary Flow

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
    - reject with reason where required.
17. Admin/system reviews request and evidence according to applicable risk controls.
18. Payer reviews final payment summary.
19. Payer explicitly authorizes payment.
20. System processes payment through approved payment partner or sandbox integration.
21. Payee receives payment according to approved payout or settlement rules.
22. Payer and payee can view the linked payment context.
23. System stores receipt, status history, and audit trail.

#### Payer-Created Payment Status Path

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
Rejected
Additional Information Required
Linked Support / Dispute Case
Failed
Cancelled
Expired
```

#### Required Controls

| Control | Requirement |
| --- | --- |
| Evidence required | Payment cannot proceed without required evidence unless an approved exception applies. |
| Evidence verification | OCR/autofill, user correction, duplicate detection, and verification outcomes follow DOC-12. |
| Payee record required | Payee must be linked, invited, or represented by a valid payee record and payout destination where required. |
| Optional payee adoption supported | Payee must be able to accept/adopt payer-created records for linking where applicable, but payer-created payment must not require payee acceptance by default. |
| Payer authorization required | Payment cannot be processed without explicit payer authorization. |
| Self-cashout blocked | Payer cannot use PayPlus to cash out to themselves. |
| Unsupported transfer blocked | Payment must be tied to a valid evidence-backed obligation. |
| No wallet behavior | System must not create user wallet balances or stored-value accounts. |

---

---

### Shared Bill, Tenancy, Invoice, or Obligation Journey

#### Purpose

Allows either a payer or payee to create an obligation record that can support a payment request or payment.

An obligation record may become shared only through an approved user action, such as payer acceptance of a payee-created request or optional payee linking/adoption of a payer-created record. PayPlus should not assume automatic user-to-user matching.

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

#### Payee-Created Obligation Path

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
13. Payer accepts or rejects the request, with rejection reason where required.
14. If accepted, payer may authorize payment.
15. System links payer, payee, request, evidence, and payment records.

#### Payer-Created Obligation Path

1. Payer logs in.
2. Payer creates a bill, invoice, tenancy, agreement, statement, or obligation record.
3. Payer enters payee information.
4. Payer uploads supporting evidence.
5. System processes evidence and autofills eligible obligation fields where enabled.
6. Payer reviews or corrects autofilled fields.
7. System validates evidence and creates obligation record.
8. System links evidence and final evidence snapshot to obligation record.
9. Payer may proceed to payment once required evidence, verification, risk, payout, and authorization gates pass.
10. Payee may be invited or linked where useful, but payee acceptance is not required before payer-created payment unless a category, risk rule, payout rule, or compliance gate explicitly requires it.
11. If the payee is a PayPlus user and linking is initiated, payee logs in or registers and reviews the obligation context.
12. Payee may accept/adopt or reject with reason for linkage purposes.
13. If adopted, payee becomes linked to the shared obligation context.
14. System links payer, payee, obligation, evidence, and payment records according to permissions.

#### Adoption Rules

| Rule | Requirement |
| --- | --- |
| Payer-created payment | Payer-created obligations may proceed without payee acceptance where evidence, verification, risk, payout, and authorization gates pass. |
| Optional payee adoption | Payee may accept/adopt payer-created obligation records for two-sided visibility, communication, and linked recordkeeping where applicable. |
| Payer acceptance | Payer may accept payee-created requests before authorizing payment. |
| No forced adoption | A recipient should not be forced to accept an inaccurate record. |
| Rejection support | Recipient may reject an inaccurate record with a reason where required. |
| Linked context | Once accepted/adopted, both sides should see the linked context subject to permissions. |
| Audit trail | Adoption and rejection actions must be logged. |

---

---

### Recipient Review Journey

#### Purpose

Allows the recipient of a request or obligation record to review the details and respond.

#### Recipient Review Matrix

| Creator | Recipient | Recipient Review Actions |
| --- | --- | --- |
| Payee creates payment request | Payer | Accept, reject with reason where required, authorize payment after acceptance. |
| Payer creates payment/obligation record | Payee | Optional accept/adopt or reject for linkage only; payer payment does not require payee acceptance unless a specific gate requires it. |

#### Required Review Information

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

#### Recipient Actions

| Action | Description |
| --- | --- |
| Accept | Recipient accepts the request or record as valid. |
| Adopt | Payee accepts a payer-created bill, tenancy, invoice, or payment context as linked to them. |
| Reject | Recipient rejects the request or record. |
| Authorize payment | Payer-only action that permits payment processing. |

#### Payment Authorization Boundary

Only the payer can authorize payment.

A payee may accept or adopt a payer-created record for linked visibility and communication, but a payee cannot authorize payment from the payer and payee adoption must not be treated as the payer's payment authorization.

---

---

### Evidence Upload and Review Journey

#### Purpose

Ensures each payment is linked to acceptable evidence before it can proceed to payment.

DOC-12 owns detailed bill category, OCR/document AI, extracted field, autofill, user correction, duplicate detection, verification outcome, and payee matching requirements. DOC-06A describes only the core user journey and UX touchpoints; DOC-06C owns Bills-specific evidence route behavior.

#### Accepted MVP Evidence Types

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

#### Evidence Upload and Verification Flow

1. User creates or updates a request, bill, rent, or obligation record.
2. User provides evidence through `BILLS-ADD` or `BILLS-EVIDENCE-UPLOAD` where evidence is required.
3. System validates file type and required metadata where applicable.
4. System processes OCR/document AI where enabled.
5. System extracts eligible fields and autofills the bill/rent/request setup fields.
6. User reviews and corrects the bill/rent/request details before submission.
7. System stores raw evidence, extraction result, user correction, and final evidence snapshot where applicable.
8. System links evidence to the request or obligation.
9. System applies duplicate/reused evidence, mismatch, completeness, same-party, and risk checks.
10. System assigns an evidence status.
11. Evidence status updates the bill/rent payment readiness status according to the Bills route mapping.
12. Low-risk accepted evidence becomes available for role-based review and payment eligibility checks.
13. Red-flag evidence routes to user clarification or admin review.

#### Evidence Review Access

| Role | Evidence Access |
| --- | --- |
| Payer | Can review evidence before authorizing payment. |
| Payee | Can view evidence attached to their own created requests or linked received payments. |
| Admin / Operations | Can view evidence for review, investigation, support, compliance, and audit. |
| System | Links evidence to request/payment records and logs actions. |

#### Evidence Rules

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
| Auditability | Evidence upload, view, update/replacement, archive, and status-change actions must be logged where applicable. |
| Access control | Evidence visibility must be restricted by role and permissions. |

---

---

### Query, Dispute, and Exception Support Journey

#### Purpose

Allows payer, payee, support, or admin to resolve incomplete, disputed, incorrect, or unclear request information through an exception/support path.

This journey is not the normal `REQUESTS-DETAIL` acceptance path. `REQUESTS-DETAIL` should keep material request actions focused on accept, reject, send, resend, remind, cancel, archive, and linked-detail handoff according to DOC-06B. Queries, disputes, and requests for more information may be available through support, admin review, or exception handling where enabled, and must remain linked to the original request.

#### Query / Additional Information Flow

1. Recipient reviews request or obligation record.
2. Recipient opens the approved support, query, or exception path where available.
3. Recipient enters the reason, question, or field requiring additional information.
4. Recipient may identify the disputed, missing, or unclear field.
5. System creates or updates a linked support/exception case.
6. System notifies the other party.
7. Other party responds with:
   - text explanation;
   - corrected field;
   - additional evidence;
   - cancellation;
   - dispute escalation.
8. System logs all support/exception activity.
9. Request returns to review, acceptance, rejection, cancellation, or admin-controlled status where allowed.

#### Dispute Flow

1. User reviews request, obligation, payment, or evidence.
2. User selects **Dispute**.
3. User enters dispute reason.
4. User may upload additional evidence.
5. System updates status to **Disputed**.
6. System notifies the other party.
7. Admin may review the dispute where required.
8. Other party may respond.
9. Admin or system may move the request to:
   - additional information required;
   - accepted;
   - rejected;
   - cancelled;
   - held;
   - resolved;
   - approved for payment where allowed.
10. System logs all dispute actions.

#### Required Query, Dispute, and Exception Controls

| Control | Requirement |
| --- | --- |
| Linked thread | Query, dispute, support, and exception activity must remain linked to the original request. |
| Audit trail | All query, dispute, support, and exception actions must be logged. |
| Notification | Relevant parties must be notified of material dispute, query, or exception events where enabled. |
| Admin visibility | Admin must be able to review query, dispute, support, and exception history. |
| Payment block | Disputed requests should not proceed to payment unless resolved under approved rules. |

---

---

### Payment Authorization Journey

#### Purpose

Ensures that the payer explicitly authorizes payment after reviewing the required context.

#### Required Payer Authorization Information

Before authorization, the payer should be shown:

- payee;
- amount;
- service fee where applicable;
- eligible promotion quote, discount, coupon, voucher, or reward impact where applicable;
- total charge;
- due date;
- category;
- description;
- evidence;
- payment method;
- pay-now or deferred payment instruction choice where enabled;
- funding leg and split-card summary where applicable;
- quote validity, expiry, or recalculation notice where applicable;
- selected payee transfer date where applicable;
- expected processing timing;
- expected payout or settlement timing where applicable;
- refund/reversal limitations where applicable;
- PayPlus role;
- relevant disclosures.

#### Authorization Flow

1. Payer reviews request or payer-created payment.
2. Payer confirms that evidence and payment details are acceptable.
3. System displays final payment summary.
4. System displays fee, promotion quote, discount, coupon/voucher impact, reward impact, and total charge where applicable.
5. Payer selects or confirms payment method.
6. Payer chooses pay now or creates a deferred payment instruction where enabled.
7. Payer accepts required terms or disclosures for the selected action.
8. Payer enters payment passcode or completes confirmation required for the selected action.
9. System applies any required step-up authentication, such as new-device, risk, amount, or partner challenge.
10. If paying now, payer confirms authorization and payment processing begins through approved payment partner or sandbox integration.
11. If creating a deferred payment instruction, system stores the payment context and returns the payer through payment-instruction reminder/action flow when payment submission is due.
12. On return, system revalidates payment quote, promotion quote, card eligibility, timing, and material terms before gateway submission.
13. If material terms changed, payer reviews the updated checkout summary and confirms before submission.
14. Payer completes required payment passcode, step-up, or partner challenge before actual funding submission where required.
15. System records authorization, payment instruction, payment attempt, and status events as applicable.

#### Authorization Rules

| Rule | Requirement |
| --- | --- |
| Explicit consent | Payer must explicitly authorize payment. |
| No automatic payment | Payee-created request cannot automatically trigger payment. |
| Evidence visibility | Payer must be able to review evidence before payment. |
| Fee visibility | Fees charged to payer must be displayed before authorization. |
| Promotion visibility | Eligible discounts, service-fee benefits, coupons, vouchers, and reward impact must be displayed before authorization where applicable. |
| Payment passcode | Payment passcode is required before payment authorization proceeds. |
| Step-up authentication | Additional authentication may be required by DOC-09, DOC-14, DOC-15, or DOC-19 risk/security rules. |
| Deferred instruction | Deferred payment instruction must return the payer to payment/checkout screen, not only to bill detail. |
| Quote revalidation | Deferred instruction return flow must show updated payment, promotion, card, fee, or timing changes before submission. |
| Partial funding | Split-card partial funding must not be shown as payment completed; remaining amount and funded portion should remain clear. |
| Audit logging | Authorization must be logged. |
| No hidden material terms | Material payment information must not be hidden from payer. |

---

---

### Payment and Payout Status Visibility

#### Purpose

Defines what users and admins need to see after payer authorization.

Detailed payment processing, payout, settlement, reconciliation, refund, reversal, chargeback, and exception rules belong in DOC-09, DOC-10, and DOC-11.

#### Required Visibility

| User | Required Visibility |
| --- | --- |
| Payer | Authorization result, payment status, failure state, cancellation/refund state where applicable, and receipt/history. |
| Payee | Request status, payer response, payment completion status, funded portion, payout/settlement visibility where permitted, and exceptions requiring payee action. |
| Admin | Full request, payment instruction, funding leg, payout, failure, refund, dispute, exception, and audit context. |

#### UX Rules

| Rule | Requirement |
| --- | --- |
| Status clarity | User-facing labels must distinguish request status, payment status, and payout/settlement status. |
| No false certainty | The UX must not imply payment or payout is complete before the relevant system of record confirms it. |
| Role-appropriate visibility | Payees must not see sensitive payer payment method, risk, or private account data. |
| Exception visibility | Failures, holds, cancellations, refunds, and disputes must have clear user-facing states and admin review paths. |

---

---

### Linked Records and Matching Journey

#### Purpose

Ensures that payer, payee, request, evidence, payment, payout, status, dispute, and audit records remain linked.

#### Required Linked Objects

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

#### Linking Flow

1. Request or payment record is created.
2. System checks payee records, payout destination, and evidence consistency required for the payment flow.
3. System may support user-initiated or user-accepted linking using approved identifiers, app links, deeplinks, QR codes, or invitation records.
4. If no platform user exists, system may create a non-user payee record, invitation record, or pending participant record.
5. Recipient registers, logs in, or accepts an invitation where linking is requested.
6. System links recipient to request or obligation only after the required user action or approved operational action.
7. System displays shared context to both sides subject to permissions.
8. System checks for duplicate, suspicious, or conflicting records where applicable.
9. System logs search, invitation, acceptance, rejection, and linking events.

Automatic user-to-user matching must not be assumed for the user experience. Duplicate detection, payee verification, payout validation, and risk checks may run in the background, but shared user visibility requires an approved linking or acceptance event.

#### Matching Requirements

| Requirement | Description |
| --- | --- |
| Shared request ID | Both payer and payee should reference the same payment request when both are users. |
| Linked evidence | Evidence record must link to request and payment context. |
| Two-sided visibility | Payer and payee must see the same underlying transaction context, subject to permissions. |
| User-accepted linking | User-to-user linking must be initiated, invited, accepted, or otherwise approved; automatic UX linking is not allowed. |
| Duplicate detection | System should help detect duplicate bills, requests, or payments. |
| Status consistency | Payer and payee views must reflect the same underlying status. |
| Exception linkage | Queries, disputes, support cases, and exception records must remain linked to the original request. |

---

---

### Two-Sided Visibility and Permissions

#### Purpose

Allows both payer and payee to view linked request/payment context while protecting sensitive information.

#### Shared Visibility

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

#### Role-Based Visibility Boundaries

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

#### Privacy and Permission Rules

| Rule | Requirement |
| --- | --- |
| Least privilege | Users should only see information needed for their role in the transaction. |
| Sensitive data masking | Payment and payout instrument details must be masked or restricted. |
| Admin access controls | Admin access must be permissioned and logged. |
| Evidence privacy | Evidence visibility must be limited to authorized users. |
| Consistent status | Status should remain consistent across payer and payee views. |

---

---

### Request Status UX

#### Core Request Statuses

The MVP UX should expose clear user-facing request states. Canonical state-machine definitions belong in DOC-09 and DOC-18.

Request states must be distinct from payment states. A request may lead to payment readiness, but payment authorization, processing, completion, failure, payout, refund, reversal, and chargeback states belong to the payment, payout, refund, and data-state owner documents.

| Status | Meaning |
| --- | --- |
| Draft | Request created but not submitted. |
| Submitted | Request submitted for review or routing. |
| Evidence Processing | Evidence OCR, extraction, autofill, or verification is in progress. |
| Pending User Correction | User must review or correct extracted evidence fields. |
| Pending Evidence Review | Evidence requires admin or risk review before payment eligibility. |
| Sent | Request sent to payer or payee. |
| Viewed | Recipient viewed the request. |
| Accepted | Payer accepted the request or recipient accepted the record. |
| Rejected | Recipient rejected the request or record. |
| Approved for Payment | Required request, evidence, verification, risk, and acceptance checks passed so the linked payment flow may become available where applicable. |
| Cancelled | Request cancelled. |
| Expired | Request expired. |

If payment status is displayed near a request, it should be labelled as linked payment status, not request status.

#### Status Rules

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

---

### Admin and Operations Journey

#### Purpose

Allows internal users to review accounts, requests, evidence, risk, disputes, payouts, settlement, failures, and exceptions.

#### Admin Capabilities

Admins must be able to:

- log in;
- access an operational dashboard;
- access sensitive data only through role-based permission, masking, reason capture, and audit logging;
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
- raise a support, query, or dispute case where enabled;
- investigate duplicates;
- review disputes;
- review payment status;
- review payout or settlement status where applicable;
- manage failed payment exceptions;
- manage payout exceptions where applicable;
- manage refund or reversal workflows where applicable;
- access audit logs.

#### Admin Review Flow

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
   - raise a support, query, or dispute case where enabled;
   - escalate;
   - mark duplicate;
   - cancel;
   - resolve.
5. System updates status where applicable.
6. System notifies relevant users where applicable.
7. System logs admin action.

#### Admin Control Rules

| Rule | Requirement |
| --- | --- |
| Permissioned access | Admin access must be role-based and controlled. |
| Sensitive data access | Sensitive identity, evidence, payment, payout, risk, and promotion data must follow DOC-15 classification, masking, reason capture, and audit rules. |
| Logged actions | Admin actions must be audit logged. |
| Evidence access | Admin must be able to review evidence. |
| OCR review support | Admin must be able to review extracted fields, user corrections, verification outcomes, and duplicate indicators where applicable. |
| Exception handling | Admin must be able to manage operational exceptions. |
| No silent overrides | Admin overrides must be traceable. |
| Risk review support | MVP must support manual review where risk rules require it. |

---

---

### Notification Touchpoints

#### Purpose

Identifies where notifications are needed in the user journey. Notification content, templates, channels, preferences, retry behavior, and audit rules belong in DOC-08.

#### User Notifications

The MVP should support basic notifications for:

- account registration;
- payment request created;
- payment request received;
- request viewed;
- request accepted;
- request rejected;
- payer-created record available for optional payee adoption/linking;
- payee adopted payer-created record;
- payment authorized;
- payment instruction pending user action;
- payment instruction partially funded;
- remaining split-card payment action due;
- payment processing;
- payment completed;
- payment failed;
- payout completed where applicable;
- partial payout completed where applicable;
- request cancelled;
- request expired.

#### Admin Notifications or Queues

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

#### Notification Channels

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

---

### Receipt and History Touchpoints

#### Purpose

Identifies where users and admins need access to prior actions, statuses, confirmations, and payment outcomes. Receipt content and records policy belong in DOC-08, DOC-15, DOC-18, and payment-domain docs.

#### User History

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

#### Receipt or Confirmation Contents

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

#### History Rules

| Rule | Requirement |
| --- | --- |
| Traceability | User-visible history must link to the underlying request/payment context. |
| Role permissions | History must show role-appropriate information. |
| Audit separation | User history is not the same as full admin audit logs. |
| Failed states | Failed, rejected, disputed, cancelled, and expired states must remain visible. |
| Receipt storage | Completed payments should have receipt or confirmation records. |
| Retention baseline | Receipt, payment, account, tax, and audit records are expected to be retained for 7 years, subject to final privacy and legal review. |

---

---

### Error, Failure, Cancellation, and Exception Journeys

#### Failed Payment

1. Payment processing fails.
2. System updates status to **Failed**.
3. System records failure reason where available.
4. Payer is notified.
5. Payee is notified where applicable.
6. Admin can review failure.
7. User may retry only if allowed by approved rules.

#### Cancelled Request

1. Eligible user or admin cancels request.
2. System checks whether cancellation is allowed.
3. System updates status to **Cancelled**.
4. System notifies relevant parties.
5. System logs cancellation event.
6. Cancelled request cannot be paid unless recreated or reopened under approved rules.

#### Expired Request

1. Request passes expiry date or expiry condition.
2. System updates status to **Expired**.
3. System notifies relevant parties.
4. Expired request cannot be paid unless renewed, recreated, or reopened under approved rules.

#### Duplicate Request

1. System or admin detects possible duplicate request, duplicate evidence, or reused evidence.
2. User may be warned that the evidence appears to have been used before, subject to DOC-12 privacy and anti-tipping-off rules.
3. Request is flagged for review where configured.
4. Admin reviews duplicate indicators.
5. Admin may hold, reject, clarify, or allow request.
6. System logs duplicate review outcome.

#### Refund or Reversal

1. Refund or reversal need is identified.
2. Admin reviews request, payment, evidence, and status history.
3. Admin follows approved operational process.
4. System records refund or reversal status.
5. Payer and payee are notified where applicable.
6. System logs all actions.

Refund and reversal rules belong in DOC-11. Payment, payout, reconciliation, and admin workflow details belong in DOC-09, DOC-10, DOC-18, DOC-21, and DOC-22.

---

---

## 6. Local Open Questions

Core journey open questions should remain here when they affect payer/payee/admin/system journeys generally. Cross-document blockers should also be linked in docs/traceability/open-questions-register.md.

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06-001 | What exact UX distinction should exist between a payment request, obligation record, bill record, and payment transaction? | Product / Design | Open |
| OQ-06-002 | Which exceptional payer-created categories, if any, require payee adoption before payment can proceed despite the default rule that payer-created payments do not require payee acceptance? | Product / Operations / Risk | Open |
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
| OQ-06-018 | What dormant-login inactivity threshold and user-facing reauthentication path should be used? | Product / Security | Open |
| OQ-06-019 | What exact masking, reveal, and role-based display rules should apply to each sensitive field by screen and category? | Product / Privacy / Security | Open |
| OQ-06-020 | What exact payment-instruction screen labels, call-to-action wording, and partial-funded visual treatment should be used? | Product / Design / Legal | Open |
| OQ-06-021 | What exact Pay+ action sheet visual layout, button order, empty states, disabled states, eligibility copy, and final action limits should be used? | Product / Design / Payments | Partially answered |
| OQ-06-022 | What exact route-level IA should apply to Bills, Offers, Me, More, Requests, Instructions, Receipts, Reminders, Cards, Referral, and Support entry points? | Product / Design | Open / placeholders added |
| OQ-06-023 | What dashboard shortcut display cap, user reorder UI, restore-default behavior, and admin default mechanism should be used? | Product / Design / Operations | Open |
| OQ-06-024 | What priority, collapse, expiry, and routing rules should apply to Important Notice / Action Required cards? | Product / Operations / Compliance | Open |
| OQ-06-025 | What carousel card limit, auto-rotation behavior, ranking, targeting, and admin approval workflow should apply to Featured / What's New / Hot Offer placements? | Product / Growth / Operations | Open |
| OQ-06-026 | What final user-initiated payee linking or invitation mechanism should be used: user ID, phone search, app link, WhatsApp deeplink, QR code, or another approved flow? | Product / Privacy / Engineering | Open |
| OQ-06-027 | What exact Bills tab visual layout, card density, status badge style, action-required treatment, and field masking rules should be used? | Product / Design / Privacy | Open |
| OQ-06-028 | What evidence source selection UI should be used when bill, invoice, tenancy, rent demand, contract, and supporting evidence types are not obvious from upload/OCR? | Product / Design / Risk | Open |
| OQ-06-029 | What exact request-delivery and `Remind Payer` UX should apply inside `BILLS-RECEIVE`, including resend limits, payer acceptance states, wording, and notification-channel rules? | Product / Design / Operations | Open |
| OQ-06-030 | Should detailed payment/checkout UI be documented inside DOC-09 only, or should DOC-06 keep a lightweight route shell for checkout entry, return, and navigation behavior? | Product / Design / Payments | Proposed: DOC-09 owns checkout UI; DOC-06 owns handoff. |

---

---

## 7. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.4 | 2026-07-02 | Reclassified query, dispute, and information-request handling as exception/support flows instead of normal `REQUESTS-DETAIL` actions. |
| 0.1.3 | 2026-07-02 | Aligned request lifecycle with DOC-06B `REQUESTS-NEW`, evidence-before-send delivery gate, and simplified accept/reject request actions. |
| 0.1.2 | 2026-06-25 | Clarified that requests are party-linking and acceptance records, not payments; separated request states from linked payment states. |
| 0.1.1 | 2026-06-25 | Removed temporary source-section heading wording and finalized official DOC-06A heading style. |
| 0.1.0 | 2026-06-25 | Created as DOC-06A child document for core user journeys and service-blueprint content without changing product decisions. |
