---
document_id: DOC-09
title: Payment Request, Multi-Funding Source & Settlement
version: 0.2.0
status: Founder Working Baseline
owner: Payments / Product
reviewers:
  - Product Lead
  - Engineering Lead
  - Payments Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
  - Security Lead
approvers:
  - Project Owner
  - Product Lead
  - Payments Lead
last_updated: 2026-05-30
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-19 Security, Tokenization & Authentication
---

# DOC-09 - Payment Request, Multi-Funding Source & Settlement

## 1. Purpose

This document defines PayPlus MVP rules for payment requests, card funding, multi-card funding, payer authorization, payment profiles, tokenization boundaries, payment status, and settlement readiness.

It explains how an evidence-backed request becomes eligible for card payment and how PayPlus tracks funding from authorization to completion, failure, or settlement readiness.

This document is not a PSP integration guide, PCI policy, data schema, payout manual, refund manual, or legal opinion.

---

## 2. Scope and Ownership

DOC-09 covers:

- payer-created and payee-created payment requests;
- eligibility gates before payment;
- payment quotes;
- payment method and payment profile selection;
- tokenization product rules;
- multi-card funding;
- payer authorization;
- step-up authentication;
- payment status and failure handling;
- settlement readiness;
- payment-domain admin controls.

DOC-09 does not define:

| Topic | Owning Document |
| --- | --- |
| User disclosure and authorization wording | DOC-07 |
| Notification and receipt delivery | DOC-08 |
| Payout execution and reconciliation | DOC-10 |
| Refund, cancellation, dispute, chargeback, and reversal operations | DOC-11 |
| Risk scoring and anti-cashout rules | DOC-14 |
| PSP/acquirer and tokenization APIs | DOC-17 |
| Data model, ledger, and audit event schema | DOC-18 |
| PCI, token vault, authentication, and security mechanics | DOC-19 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Launch jurisdiction | Hong Kong. |
| Transaction classification | Expected bill payment or ordinary online card purchase; final PSP/acquirer, MCC, and classification remain to be confirmed. |
| Payer-created requests | MVP scope. |
| Payee-created requests | MVP scope. |
| Tenancy and rent payments | MVP scope, subject to rent-specific controls. |
| Domestic helper, driver, and personal service payments | MVP scope where supported by acceptable evidence. |
| Multi-card payment | MVP scope, supporting up to a configurable number of credit cards per payment. Launch cap is to be confirmed. |
| Payout rails | FPS, cheque, and EPS are acceptable Hong Kong payout rails; payout execution belongs to DOC-10. |
| Upstream settlement | Payment gateway settlement expected T+1 to T+3. |
| Fee model | Percentage-based online payment processing service fee; exact rates and allocations remain admin-configurable and to be confirmed. |
| Step-up authentication | Extra authentication may be skipped below a configurable amount where partner, risk, compliance, and security rules allow. |

Unconfirmed items should remain editable assumptions or gated requirements and should not block continued documentation drafting.

---

## 4. Payment Request Model

PayPlus supports evidence-backed payment requests funded by card.

Each payment request must link:

- payer;
- approved payee or payee record;
- bill, invoice, fee, rent, domestic service, or other approved obligation;
- evidence or approved evidence exception;
- amount;
- request origin;
- payment quote;
- payer authorization record;
- payment status history;
- audit trail.

Request origins:

| Origin | Rule |
| --- | --- |
| Payer-created | Payer creates the request and may proceed after gates and authorization. |
| Payee-created | Approved payee creates the request; payer must review and authorize before funding. |
| Admin-created | Internal user creates or corrects a record under approved process; payment still requires payer authorization. |
| System-generated | System creates status, reminder, or derived event; cannot authorize payment. |

PayPlus must not support wallet balance, stored value, arbitrary P2P transfer, self-cashout, card-to-bank cashout, or payment unrelated to an approved evidence-backed obligation.

---

## 5. Eligibility Gates

A request must pass required gates before payment processing.

| Gate | Requirement |
| --- | --- |
| Category | Category must be approved and enabled. |
| Evidence | Required evidence must exist or have an approved exception. |
| Payee | Payee must be eligible for request type and payout destination where required. |
| Payer | Payer must be eligible and not blocked, suspended, or restricted. |
| Request origin | Request origin must be allowed for category and payee type. |
| Risk | Risk, velocity, duplicate, and anti-cashout checks must pass or route to review. |
| Fee | Fee, promotion, discount, and total charge must be calculated before authorization. |
| Disclosure | Required disclosures must be available before authorization. |
| Authorization | Payer must explicitly authorize before payment processing. |

Failed gates should create a clear status and, where appropriate, admin review or user action path.

---

## 6. Payment Domain Flow Summary

DOC-06 owns detailed user journeys, screen flow, and service blueprint steps.

DOC-09 owns the payment-domain lifecycle after a request exists or is ready for payment evaluation.

### 6.1 Common Payment Lifecycle

1. Request is created through an approved payer-created, payee-created, admin-created, or system-generated path.
2. System applies eligibility gates.
3. System creates payment quote.
4. Payer selects eligible payment profile(s).
5. Payer authorizes payment.
6. System applies required step-up authentication rules.
7. System submits payment through approved PSP/acquirer flow.
8. System records payment outcome.
9. System records settlement readiness.
10. Payout readiness passes to DOC-10.

### 6.2 Origin-Specific Rules

| Origin | Payment-Domain Rule |
| --- | --- |
| Payer-created | Payer may proceed to quote and authorization after eligibility gates pass. |
| Payee-created | Payer must accept or otherwise choose to proceed before payment method selection and authorization. |
| Admin-created | Admin-created records must remain auditable and cannot bypass payer authorization for payment. |
| System-generated | System-generated events cannot authorize or process payment by themselves. |

A payee-created request must not trigger funding, capture, payout, or settlement action before payer authorization.

---

## 7. Payment Quote

Before authorization, PayPlus must generate a payment quote containing:

- request ID;
- payee;
- request origin;
- category and obligation reference;
- payment amount;
- service fee;
- discount, coupon, promotion, or subsidy where applicable;
- total charge;
- selected payment method summary;
- multi-card split summary where applicable;
- expected processing and settlement timing where relevant;
- disclosure version.

If amount, fee, discount, payment method, card split, payee, evidence, or other material terms change after review, payer reauthorization may be required.

---

## 8. Payment Profiles and Tokenization

A payment profile represents a payer's saved or selected payment instrument reference.

Payment profiles may include:

- PSP/acquirer token or payment method reference;
- masked card summary;
- card brand and expiry where permitted;
- payer owner reference;
- status;
- risk or verification status where applicable.

Core rules:

| Rule | Requirement |
| --- | --- |
| Tokenized processing | Card funding should use PSP/acquirer tokenization where available. |
| No raw card storage | PayPlus must not store raw card number, CVV, magnetic stripe data, or sensitive authentication data unless separately approved under PCI scope. |
| Limited metadata | PayPlus should store only token/reference and permitted masked metadata. |
| Payer ownership | Payment profile must be linked to the payer account or approved user context. |
| Authorization link | Each token/profile use must be linked to payer authorization. |
| Reuse | Saved profile reuse requires payer authorization for each payment unless a separately approved recurring authorization model exists. |

Payment profile statuses should include `Active`, `Verification Required`, `Expired`, `Suspended`, and `Deleted`.

Detailed token vault, encryption, PCI, authentication, API, and schema requirements belong in DOC-17, DOC-18, and DOC-19.

---

## 9. Payment Method Selection

The payer must select one or more eligible payment profiles before authorization.

Rules:

- blocked, expired, suspended, deleted, or failed profiles must not be used without resolution;
- selected methods must cover the payment amount and applicable fees;
- payer must see masked method summary before authorization;
- payment method changes after authorization require reauthorization where material;
- admin users must not select payment methods for a payer unless a separately approved support process exists.

---

## 10. Multi-Card Funding

Multi-card funding is MVP scope.

PayPlus must support up to a configurable number of credit cards per payment. The exact launch card-count limit is to be confirmed.

| Rule | Requirement |
| --- | --- |
| Configurable cap | Maximum cards per payment must be configurable. |
| Allocation | Each selected card must have an allocated amount. |
| Total match | Allocations must equal the authorized total charge. |
| Masked summary | Payer must see masked card summary and amount per card before authorization. |
| Reauthorization | Changing selected cards or split amounts after authorization requires reauthorization. |
| Partial failure | If one card fails, payment must not be treated as fully completed unless a separately approved partial-payment model exists. |
| Retry | Retry may be allowed subject to partner, risk, velocity, and authorization rules. |
| Audit | Each card attempt and result must be logged. |

If multi-card funding fails partially, the user may be asked to replace a card, change the split, retry, or reauthorize according to configured rules.

---

## 11. Payer Authorization

Payer authorization is always required before payment processing.

Authorization must record:

- payer ID;
- request ID;
- payment ID where available;
- payee reference;
- amount, fee, discount, and total charge;
- selected payment profile summary;
- multi-card split where applicable;
- disclosure and terms version where applicable;
- timestamp;
- authorization result;
- channel or device context where available.

Material changes after authorization require invalidation or reauthorization.

Material changes include amount, fee, total charge, selected card, card split, payee, evidence, material timing, or disclosure terms.

---

## 12. Step-Up Authentication

Step-up authentication means an additional challenge beyond normal payer confirmation, such as 2FA, OTP, 3DS, biometric challenge, PSP/acquirer challenge, or PayPlus risk challenge.

| Rule | Requirement |
| --- | --- |
| Payer authorization always required | User confirmation is never skipped. |
| Step-up conditional | Extra authentication may be skipped below a configurable amount if allowed by partner, risk, compliance, and security rules. |
| Configurable threshold | Threshold must be configurable. |
| Risk override | Step-up may still be required below threshold when risk is elevated. |
| Policy variation | Thresholds may vary by user, card, category, payee type, request origin, amount, velocity, risk score, or partner rule. |
| Logging | Step-up required, skipped, passed, failed, and expired decisions must be logged. |
| Failure handling | Failed or expired step-up must not result in payment completion or payout readiness. |

Detailed security and authentication mechanics belong in DOC-19.

---

## 13. Payment Status Model

DOC-09 owns payment-domain status meaning at product-rule level. Canonical event schema belongs in DOC-18.

| Status Group | Example Statuses | Purpose |
| --- | --- | --- |
| Request setup | Draft, Submitted, Sent | Request exists but is not ready for payment. |
| Review and response | Viewed, Accepted, Rejected, Disputed, Expired, Cancelled | Recipient action or lifecycle state before payment. |
| Payment readiness | Approved for Payment, Payment Quote Created | Request passed required gates and quote is available. |
| Authorization | Payment Authorized, Step-Up Required, Step-Up Passed, Step-Up Failed | Tracks payer authorization and extra authentication. |
| Processing | Payment Processing, Payment Completed, Payment Failed, Partial Failure | Tracks PSP/acquirer payment outcome. |
| Review or hold | Held for Review | Payment requires admin, risk, or partner review. |
| Settlement readiness | Settlement Pending, Settlement Confirmed | Tracks upstream settlement state before payout readiness. |

Payout statuses belong in DOC-10.

Refund, reversal, chargeback, cancellation, and dispute operation statuses belong in DOC-11, though DOC-09 must link those events to the original payment.

---

## 14. Failure Handling

Payment failure may result from:

- card decline;
- expired or invalid token;
- issuer rejection;
- failed step-up authentication;
- PSP/acquirer error;
- duplicate or velocity rule;
- risk hold;
- user cancellation;
- timeout;
- partial multi-card failure.

Rules:

- failed payment must be visible and traceable;
- failed or expired authorization must not result in payout readiness;
- retries may be allowed where configured;
- retry limits must be configurable;
- repeated failures may trigger risk review or payment profile suspension;
- failure events should feed DOC-08 notification decisions and DOC-18 audit records.

---

## 15. Settlement Readiness

Payment completion and payout readiness are not the same.

| Concept | Meaning |
| --- | --- |
| Payment authorized | Payer approved charge. |
| Payment completed | Card payment completed according to approved payment system record. |
| Settlement pending | Funds not yet settled by upstream counterparty. |
| Settlement confirmed | Settlement file, report, webhook, or approved record indicates settlement is complete or settlement-ready. |
| Payout-ready | Payment, payee, risk, payout destination, and settlement checks permit payout evaluation. |

Current baseline assumes upstream payment gateway settlement of T+1 to T+3.

Payout is expected on the same day after upstream settlement, subject to DOC-10 payout readiness, bank processing, partner rules, risk holds, reserves, exceptions, and reconciliation.

DOC-09 emits settlement readiness status or evidence for DOC-10; DOC-10 owns payout execution.

---

## 16. Admin Controls

Admin or operations users should be able to:

- view payment request and payment attempt status;
- view masked payment profile summary;
- view multi-card allocation and attempt status;
- view step-up status where available;
- place or release payment hold where permitted;
- trigger permitted retry or user reauthorization path;
- suspend or flag payment profile where required by risk/support policy;
- view settlement readiness;
- view audit log.

Admin users must not see raw card data, CVV, sensitive authentication data, or full token secrets.

Admin actions must be permissioned and logged.

---

## 17. Risk and Anti-Cashout Boundary

Payment processing must support controls against self-payment, unsupported P2P transfer, fake invoice, fake rent, duplicate obligation, collusive activity, card testing, suspicious refunds, unsupported categories, and payment profile abuse.

Detailed risk scoring, rules, thresholds, monitoring, and investigation procedures belong in DOC-14 and DOC-21.

---

## 18. Events, Notifications, and Audit

DOC-09 emits payment-domain statuses and events.

DOC-08 determines whether and how users or admins are notified.

DOC-18 defines detailed data model, ledger, reporting, and event schema.

DOC-09 requires traceability for:

- request origin;
- payer;
- payee;
- obligation and evidence;
- quote;
- payment profile and token reference;
- authorization and step-up decision;
- payment attempt and status;
- multi-card allocation;
- failure reason where available;
- settlement readiness;
- admin action.

---

## 19. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-09-001 | Which PSP/acquirer will support the intended bill payment or ordinary online card purchase treatment? | Payments / Commercial | Open |
| OQ-09-002 | What MCC/classification will the selected acquirer assign? | Payments / Legal | Open |
| OQ-09-003 | What configurable maximum number of credit cards per payment should be allowed at launch? | Product / Payments | Open |
| OQ-09-004 | What configurable amount threshold allows step-up authentication to be skipped? | Risk / Security / Payments | Open |
| OQ-09-005 | Which risk factors force step-up authentication even below the amount threshold? | Risk / Security | Open |
| OQ-09-006 | What retry limits apply by user, card, request, payee, category, and time window? | Risk / Payments | Open |
| OQ-09-007 | What authorization expiry period applies before payer reauthorization is required? | Payments / Product | Open |
| OQ-09-008 | What payment profile metadata may be stored under final PSP/acquirer, PCI, privacy, and security design? | Security / Payments / Engineering | Open |
| OQ-09-009 | What settlement file, report, webhook, or reconciliation signal confirms settlement readiness? | Payments / Finance / Engineering | Open |
| OQ-09-010 | What partial multi-card failure status naming should be exposed to payer and admin? | Product / Design / Operations | Open |

---

## 20. Acceptance Criteria

DOC-09 is acceptable when:

- payer-created and payee-created payment request flows are defined;
- payment eligibility gates are clear;
- payment quote requirements are defined;
- payment profiles and tokenization boundaries are included without duplicating DOC-17, DOC-18, or DOC-19;
- multi-card funding is defined as MVP scope with configurable card-count limit;
- payer authorization is mandatory and auditable;
- step-up authentication can be conditionally skipped below configurable threshold where allowed;
- payment status and failure handling are defined at product-rule level;
- settlement readiness is distinguished from payout execution;
- admin controls are defined without exposing raw card data;
- DOC-10, DOC-11, DOC-14, DOC-17, DOC-18, and DOC-19 ownership boundaries remain clear.

---

## 21. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.0 | 2026-05-29 | Initial founder working baseline for payment request, card funding, multi-card funding, payment profiles, tokenization boundary, payer authorization, step-up authentication, payment status, failure handling, and settlement readiness. |
| 0.2.0 | 2026-05-30 | Aligned payment request scope with updated DOC-01 positioning for invoices, fees, rent, domestic service obligations, and evidence-backed payment boundaries. |
