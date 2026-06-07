---
document_id: DOC-09
title: Payment Request, Multi-Funding Source & Settlement
version: 0.8.0
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
last_updated: 2026-06-02
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
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
---

# DOC-09 - Payment Request, Multi-Funding Source & Settlement

## 1. Purpose

This document defines PayPlus MVP rules for payment requests, user payment instructions, card funding, multi-card funding, payer authorization, payment profiles, tokenization boundaries, payment status, and settlement readiness.

It explains how an evidence-backed request becomes eligible for card payment and how PayPlus tracks funding from authorization to completion, failure, or settlement readiness.

This document is not a PSP integration guide, PCI policy, data schema, payout manual, refund manual, or legal opinion.

---

## 2. Scope and Ownership

DOC-09 covers:

- payer-created and payee-created payment requests;
- eligibility gates before payment;
- evidence verification outcome consumption;
- promotion quote consumption;
- payment quotes;
- user payment instructions and deferred funding;
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
| Bill category, document AI/OCR, evidence verification, and duplicate evidence rules | DOC-12 |
| Promotion engine, campaign, offer, coupon, voucher, reward, entitlement, and promotion quote rules | DOC-13 |
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
| Bill and fee payments | MVP scope, subject to payment eligibility, evidence, payee, payout, and risk controls. |
| Tenancy and rent payments | MVP scope, subject to rent-specific controls. |
| Domestic helper, driver, and personal service payments | MVP scope where supported by acceptable evidence. |
| Multi-card payment | MVP scope, supporting up to a configurable number of credit cards per payment. Launch cap is to be confirmed. |
| User payment instruction | MVP scope. User may pay immediately or create a deferred payment instruction for single-card or split-card payment, subject to authorization, reminder, settlement, and payout rules. |
| Payout rails | FPS, cheque, and EPS are acceptable Hong Kong payout rails; payout execution belongs to DOC-10. |
| Upstream settlement | Payment gateway settlement expected T+1 to T+3. |
| Fee model | Percentage-based online payment processing service fee; exact rates and allocations remain admin-configurable and to be confirmed. |
| Step-up authentication | Extra authentication may be skipped below a configurable amount where partner, risk, compliance, and security rules allow. |
| Evidence verification | DOC-12 verification outcome must be resolved before payment quote and authorization where the category requires verification. |
| Promotion quote | DOC-13 promotion impact must be calculated before payer authorization where promotions, coupons, vouchers, rewards, membership benefits, or card-linked offers are enabled. |

Unconfirmed items should remain editable assumptions or gated requirements and should not block continued documentation drafting.

---

## 4. Payment Request Model

PayPlus supports evidence-backed payment requests funded by card.

Each payment request must link:

- payer;
- approved payee or payee record;
- bill, invoice, fee, rent, domestic service, or other approved obligation;
- evidence or approved evidence exception;
- evidence verification outcome and final evidence snapshot where applicable;
- promotion quote and reward entitlement references where applicable;
- amount;
- request origin;
- payment quote;
- user payment instruction where created;
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
| Evidence | Required evidence must exist, pass DOC-12 verification, or have an approved exception. |
| Payee | Payee must be eligible for request type and payout destination where required. |
| Payer | Payer must be eligible and not blocked, suspended, or restricted. |
| Request origin | Request origin must be allowed for category and payee type. |
| Risk | Risk, velocity, duplicate/reused evidence, same-party, and anti-cashout checks must pass or route to review. |
| Fee | Fee, promotion, discount, and total charge must be calculated before authorization. |
| Promotion | Promotion quote, entitlement, coupon/voucher selection, and card-linked eligibility must be resolved before authorization where applicable. |
| Disclosure | Required disclosures must be available before authorization. |
| Authorization | Payer must explicitly authorize before payment processing. |

Failed gates should create a clear status and, where appropriate, admin review or user action path.

---

## 6. Payment Domain Flow Summary

DOC-06 owns detailed user journeys, screen flow, and service blueprint steps.

DOC-09 owns the payment-domain lifecycle after a request exists or is ready for payment evaluation.

### 6.1 Common Payment Lifecycle

1. Request is created through an approved payer-created, payee-created, admin-created, or system-generated path.
2. Evidence is uploaded, processed, corrected, and verified where required by DOC-12.
3. System applies eligibility gates.
4. System obtains promotion quote where promotions or rewards are enabled.
5. System creates payment quote.
6. Payer selects eligible payment profile(s).
7. System recalculates promotion and payment quote if selected payment profile affects eligibility.
8. Payer chooses pay now or creates a payment instruction.
9. For pay-now flow, payer authorizes payment and system submits payment through approved PSP/acquirer flow.
10. For deferred instruction flow, system stores the instruction and sends the payer back to payment/checkout screen when action is required.
11. System records payment outcome for each submitted funding leg.
12. System records settlement readiness for each completed funding leg.
13. Payout readiness for settlement-ready funded portions passes to DOC-10.

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
- evidence verification summary and final evidence snapshot reference where applicable;
- payment amount;
- service fee;
- promotion quote ID, campaign/offer reference, discount, coupon, voucher, reward, entitlement, or subsidy where applicable;
- total charge;
- selected payment method summary;
- multi-card split summary where applicable;
- pay-now or deferred payment instruction choice;
- deferred funding date and selected payee transfer date where applicable;
- expected processing and settlement timing where relevant;
- disclosure version.
- quote validity or expiry timestamp where applicable.

If amount, fee, discount, promotion quote, reward entitlement, payment method, card split, payee, evidence, or other material terms change after review, payer reauthorization may be required.

If evidence is corrected, replaced, rejected, marked duplicate, or routed to review after quote creation, the quote must be recalculated or blocked until the required verification outcome is resolved.

If a selected payment profile changes card-linked promotion eligibility, or a promotion campaign, budget, entitlement, coupon/voucher, membership benefit, or reward status changes after quote creation, the quote must be recalculated or blocked until DOC-13 rules are resolved.

---

## 8. User Payment Instruction

User payment instruction is MVP scope.

A payment instruction means the user has entered the payment flow and selected payment amount, payment profile(s), split allocation where applicable, timing, and payee transfer preference, but one or more funding legs have not yet been submitted to the PSP/acquirer.

Payment instruction is not:

- a recurring payment mandate;
- an automatic recurring payment;
- a stored-value or wallet instruction;
- a normal bill/rent due-date reminder;
- a user manual reminder for a bill/rent record.

### 8.1 Instruction Types

| Type | Meaning | Gateway Submission |
| --- | --- | --- |
| Pay now | User submits selected funding leg(s) immediately. | Submit now. |
| Deferred payment instruction | User saves selected funding leg(s) for later action within the allowed window. | Do not submit until user returns and confirms. |
| Reminder only | User asks to be reminded about a bill/rent/obligation outside the payment flow. | No gateway submission and no payment instruction. |

Deferred payment instruction must support both single-card and split-card payments.

### 8.2 Timing Rules

| Rule | Requirement |
| --- | --- |
| Deferred instruction window | A deferred payment instruction may target a funding action date within 7 days. |
| Beyond 7 days | If user wants action more than 7 days later, PayPlus should create a reminder only; user must return and start or resume payment flow. |
| Gateway authorization validity | PayPlus must not assume PSP/acquirer 2FA, 3DS, authorization, or session validity will remain available until the deferred date. |
| User return required | Deferred instruction reminder should return the user to payment/checkout screen to confirm and submit payment. |
| Quote revalidation | Stored payment and promotion quotes must be revalidated when the user returns to submit a deferred funding leg. Material changes require recalculation and user confirmation. |
| Selected payee transfer date | User may select a payee transfer date only if it is no earlier than the applicable T+3 / settlement-ready date for the funded portion and subject to DOC-10 readiness rules. |
| No selected payee transfer date | Settlement-ready funded portions may pass to DOC-10 for normal payout timing. |

The exact 7-day window, T+3 basis, cutoff, business-day treatment, and PSP/acquirer constraints must remain configurable and subject to DOC-10, DOC-17, and DOC-18.

Creating a deferred payment instruction stores the user's selected payment context. It must not be represented as card authorization, capture, settlement, payout readiness, or completed payment until the relevant funding leg has actually been submitted and confirmed through the approved payment flow.

### 8.3 Split-Card Instruction Rules

Split-card payment instruction must track each funding leg separately.

Each card leg should include:

- funding leg ID;
- payment instruction ID;
- payment profile summary;
- allocated amount;
- target funding date where deferred;
- gateway submission status;
- authorization and step-up status;
- payment attempt status;
- settlement status;
- payout linkage where settlement-ready;
- reminder status;
- failure, expiry, or cancellation reason where applicable.

Rules:

- one or more card legs may be paid immediately while other legs remain pending;
- PayPlus cannot force the user to complete pending funding legs;
- the overall payment must not be marked completed until the intended full amount is funded;
- settlement-ready funded portions may proceed to DOC-10 payout evaluation even if the overall instruction remains partially funded;
- remaining unpaid legs must stay visible as pending, expired, failed, or cancelled according to status rules;
- user and payee screens must not describe partial funding as full payment completion.

### 8.4 Payment Instruction Status

| Status | Meaning |
| --- | --- |
| Instruction Created | Payment instruction exists but no funding leg has been submitted. |
| Pending User Action | User must return to confirm or submit one or more funding legs. |
| Partially Funded | At least one funding leg is completed, but the intended full amount is not funded. |
| Fully Funded | All intended funding legs are completed. |
| Expired | Instruction or remaining leg passed allowed action window. |
| Cancelled | User or admin cancelled the instruction where permitted. |

### 8.5 Funding Leg Status

| Status | Meaning |
| --- | --- |
| Pending | Leg selected but not submitted to gateway. |
| Reminder Sent | User reminder sent for pending leg. |
| Submitted | Leg submitted to PSP/acquirer. |
| Authorized | Gateway authorization succeeded where applicable. |
| Failed | Leg failed or was declined. |
| Settlement Pending | Leg completed but upstream settlement not ready. |
| Settlement Ready | Leg is settlement-ready for DOC-10 payout evaluation. |
| Paid Out | Funded portion linked to payout item or payout result. |
| Expired / Cancelled | Leg expired or was cancelled. |

### 8.6 Payment Completion and Partial Payout Rule

Payment completion and funded-portion payout are separate.

| Concept | Rule |
| --- | --- |
| Overall payment completion | Only when full intended amount is funded and all required payment checks pass. |
| Partial funding | Allowed where user submits only some split-card legs. Must not be called completed payment. |
| Partial payout | Settlement-ready funded portions may proceed to DOC-10 payout evaluation, subject to payee, risk, settlement, destination, dispute, and admin rules. |
| Remaining amount | Remains pending, failed, expired, cancelled, or otherwise unresolved until user action or expiry. |
| Receipt and proof | Receipt/proof wording must identify paid/funded portion versus remaining unpaid amount. |

DOC-10 owns payout execution, partial payout grouping, bank file/API handling, and reconciliation for settlement-ready funded portions.

### 8.7 Reminder Boundary

Payment instruction reminders are different from ordinary bill/rent reminders.

| Reminder Type | Source | User Action Destination |
| --- | --- | --- |
| Normal due-date reminder | System generated from bill/rent/obligation due date. | Bill/rent/obligation detail screen. |
| User manual reminder | User sets reminder date or offset for a bill/rent/obligation. | Bill/rent/obligation detail screen. |
| Deferred payment instruction reminder | User has entered payment flow and saved deferred payment context. | Payment/checkout screen for the same instruction. |

DOC-06 owns screen flow. DOC-08 owns notification IDs, channel rules, and message delivery.

---

## 9. Payment Profiles and Tokenization

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
| Privacy classification | Payment profile, token reference, masked card, card metadata, authorization, step-up, and payment behavior data must be classified as Payment and Funding Data or Authentication and Security Data under DOC-15 as applicable. |

Payment profile statuses should include `Active`, `Verification Required`, `Expired`, `Suspended`, and `Deleted`.

Detailed token vault, encryption, PCI, authentication, privacy classification, API, and schema requirements belong in DOC-15, DOC-17, DOC-18, and DOC-19.

---

## 10. Payment Method Selection

The payer must select one or more eligible payment profiles before authorization.

Rules:

- blocked, expired, suspended, deleted, or failed profiles must not be used without resolution;
- selected methods must cover the payment amount and applicable fees;
- payer must see masked method summary before authorization;
- payment method changes after authorization require reauthorization where material;
- admin users must not select payment methods for a payer unless a separately approved support process exists.

---

## 11. Multi-Card Funding

Multi-card funding is MVP scope.

PayPlus must support up to a configurable number of credit cards per payment. The exact launch card-count limit is to be confirmed.

| Rule | Requirement |
| --- | --- |
| Configurable cap | Maximum cards per payment must be configurable. |
| Allocation | Each selected card must have an allocated amount. |
| Total match | Allocations must equal the authorized total charge. |
| Masked summary | Payer must see masked card summary and amount per card before authorization. |
| Reauthorization | Changing selected cards or split amounts after authorization requires reauthorization. |
| Partial funding | Payment instruction may be partially funded, but overall payment must not be treated as fully completed until the intended full amount is funded. |
| Retry | Retry may be allowed subject to partner, risk, velocity, and authorization rules. |
| Audit | Each card attempt and result must be logged. |

If multi-card funding fails or remains incomplete, the user may be asked to complete remaining legs, replace a card, change the split, retry, cancel, or reauthorize according to configured rules.

---

## 12. Payer Authorization

Payer authorization is always required before payment processing. Payment passcode is the baseline PayPlus confirmation before payment authorization proceeds.

Authorization must record:

- payer ID;
- request ID;
- payment ID where available;
- payee reference;
- amount, fee, discount, and total charge;
- selected payment profile summary;
- payment instruction ID where applicable;
- multi-card split where applicable;
- pay-now or deferred instruction choice;
- selected payee transfer date where applicable;
- disclosure and terms version where applicable;
- payment passcode confirmation result;
- step-up authentication decision and result where applicable;
- timestamp;
- authorization result;
- channel or device context where available.

Material changes after authorization require invalidation or reauthorization.

Material changes include amount, fee, promotion quote, reward entitlement, total charge, selected card, card split, payee, evidence, evidence verification outcome, deferred funding date, selected payee transfer date, material timing, or disclosure terms.

---

## 13. Step-Up Authentication

Step-up authentication means an additional challenge beyond normal payer confirmation and payment passcode, such as 2FA, OTP, 3DS, biometric challenge, PSP/acquirer challenge, or PayPlus risk challenge.

| Rule | Requirement |
| --- | --- |
| Payer authorization always required | User confirmation is never skipped. |
| Payment passcode always required | Payment passcode is required before payment authorization proceeds, subject to final DOC-19 security design. |
| Step-up conditional | Extra authentication may be skipped below a configurable amount if allowed by partner, risk, compliance, and security rules. |
| Configurable threshold | Threshold must be configurable. |
| Risk override | Step-up may still be required below threshold when risk is elevated. |
| Policy variation | Thresholds may vary by user, card, category, payee type, request origin, amount, velocity, risk score, or partner rule. |
| Logging | Step-up required, skipped, passed, failed, and expired decisions must be logged. |
| Failure handling | Failed or expired step-up must not result in payment completion or payout readiness. |
| Deferred instruction | Saved deferred instruction must not rely on stale PSP/acquirer authorization or 2FA validity beyond allowed partner/security windows. |

Detailed security and authentication mechanics belong in DOC-19.

---

## 14. Payment Status Model

DOC-09 owns payment-domain status meaning at product-rule level. Canonical event schema belongs in DOC-18.

| Status Group | Example Statuses | Purpose |
| --- | --- | --- |
| Request setup | Draft, Submitted, Sent | Request exists but is not ready for payment. |
| Evidence verification | Evidence Processing, Pending User Correction, Pending Evidence Review, Evidence Rejected, Duplicate Suspected | Tracks DOC-12 evidence processing before payment readiness. |
| Review and response | Viewed, Accepted, Rejected, Disputed, Expired, Cancelled | Recipient action or lifecycle state before payment. |
| Payment readiness | Approved for Payment, Payment Quote Created | Request passed required gates and quote is available. |
| Payment instruction | Instruction Created, Pending User Action, Partially Funded, Fully Funded, Expired, Cancelled | Tracks saved payment context before and during deferred or split funding. |
| Authorization | Payment Authorized, Step-Up Required, Step-Up Passed, Step-Up Failed | Tracks payer authorization and extra authentication. |
| Funding leg | Pending, Reminder Sent, Submitted, Authorized, Failed, Settlement Pending, Settlement Ready, Paid Out, Expired, Cancelled | Tracks each card leg in single-card or split-card funding. |
| Processing | Payment Processing, Payment Completed, Payment Failed, Partially Funded | Tracks PSP/acquirer payment outcome without treating partial funding as complete. |
| Review or hold | Held for Review | Payment requires admin, risk, or partner review. |
| Settlement readiness | Settlement Pending, Settlement Confirmed | Tracks upstream settlement state before payout readiness. |

Payout statuses belong in DOC-10.

Refund, reversal, chargeback, cancellation, and dispute operation statuses belong in DOC-11, though DOC-09 must link those events to the original payment.

---

## 15. Failure Handling

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
- deferred instruction expiry;
- incomplete split-card funding.

Rules:

- failed payment must be visible and traceable;
- failed or expired authorization must not result in payout readiness;
- retries may be allowed where configured;
- pending or incomplete funding legs may generate reminders and user action tasks;
- retry limits must be configurable;
- repeated failures may trigger risk review or payment profile suspension;
- failure events should feed DOC-08 notification decisions and DOC-18 audit records.

---

## 16. Settlement Readiness

Payment completion and payout readiness are not the same.

| Concept | Meaning |
| --- | --- |
| Payment authorized | Payer approved charge. |
| Payment completed | Card payment completed according to approved payment system record. |
| Partially funded | One or more intended funding legs completed, but intended full amount is not completed. |
| Settlement pending | Funds not yet settled by upstream counterparty. |
| Settlement confirmed | Settlement file, report, webhook, or approved record indicates settlement is complete or settlement-ready. |
| Payout-ready | Payment, payee, risk, payout destination, and settlement checks permit payout evaluation. |

Current baseline assumes upstream payment gateway settlement of T+1 to T+3.

Payout is expected on the same day after upstream settlement, subject to DOC-10 payout readiness, selected payee transfer date, bank processing, partner rules, risk holds, reserves, exceptions, and reconciliation.

For partially funded split-card instructions, each settlement-ready funded portion may pass to DOC-10 for payout evaluation. This does not make the overall payment completed.

DOC-09 emits settlement readiness status or evidence for DOC-10; DOC-10 owns payout execution.

---

## 17. Admin Controls

Admin or operations users should be able to:

- view payment request and payment attempt status;
- view payment instruction status;
- view masked payment profile summary;
- view multi-card allocation and attempt status;
- view pending, incomplete, expired, settlement-ready, and paid-out funding legs;
- view step-up status where available;
- place or release payment hold where permitted;
- trigger permitted retry or user reauthorization path;
- suspend or flag payment profile where required by risk/support policy;
- view settlement readiness;
- view audit log.

Admin users must not see raw card data, CVV, sensitive authentication data, or full token secrets.

Admin actions must be permissioned and logged.

---

## 18. Risk and Anti-Cashout Boundary

Payment processing must support controls against self-payment, unsupported P2P transfer, fake invoice, fake rent, duplicate obligation, collusive activity, card testing, suspicious refunds, unsupported categories, and payment profile abuse.

Evidence-derived mismatch, duplicate/reused evidence, same-party, and verification signals come from DOC-12 and feed payment eligibility and risk routing. Detailed risk scoring, rules, thresholds, monitoring, and investigation procedures belong in DOC-14 and DOC-21.

Risk routing should be proportionate. Not every red flag blocks payment; DOC-14 defines whether a signal should allow, warn, require clarification, require step-up, route to manual review, hold payment or payout, block, suspend, or escalate.

Deferred payment instruction and partial funding create additional timing and loss risks. Risk controls may consider pending duration, repeated incomplete split payments, unusual card split patterns, selected payee transfer date, settlement-ready partial payout, and user/payee complaint or dispute history.

---

## 19. Events, Notifications, and Audit

DOC-09 emits payment-domain statuses and events.

DOC-08 determines whether and how users or admins are notified.

DOC-18 defines detailed data model, ledger, reporting, and event schema.

DOC-09 requires traceability for:

- request origin;
- payer;
- payee;
- obligation and evidence;
- evidence verification outcome and final evidence snapshot where applicable;
- quote;
- promotion quote, benefit application, reward entitlement, and instrument reference where applicable;
- payment profile and token reference;
- payment instruction ID and status where applicable;
- authorization and step-up decision;
- payment attempt and status;
- multi-card allocation and funding leg status;
- failure reason where available;
- settlement readiness;
- partial payout linkage where applicable;
- admin action.

---

## 20. Open Questions

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
| OQ-09-011 | Which DOC-12 evidence verification outcomes block payment quote, authorization, retry, or settlement readiness? | Product / Payments / Risk | Open |
| OQ-09-012 | Which DOC-13 promotion quote, reward entitlement, card-linked eligibility, and coupon/voucher states block or require recalculation before payer authorization? | Product / Payments / Growth | Open |
| OQ-09-013 | What exact deferred payment instruction validity window should apply if PSP/acquirer, 3DS, or security rules differ from the 7-day product baseline? | Payments / Security / Product | Open |
| OQ-09-014 | What selected payee transfer date rules apply when split-card funding legs complete on different dates? | Payments / Finance / Product | Open |
| OQ-09-015 | What expiry, cancellation, and reminder schedule should apply to incomplete payment instructions and funding legs? | Product / Operations / Payments | Open |
| OQ-09-016 | What payer/payee wording should describe partial funding, partial payout, remaining unpaid amount, and incomplete payment? | Product / Legal / Operations | Open |
| OQ-09-017 | What quote reservation, expiry, revalidation, and campaign-budget handling should apply to deferred payment instructions? | Product / Growth / Payments | Open |

---

## 21. Acceptance Criteria

DOC-09 is acceptable when:

- payer-created and payee-created payment request flows are defined;
- payment eligibility gates are clear;
- DOC-12 evidence verification outcomes are consumed before payment quote and authorization where required;
- payment quote requirements are defined;
- user payment instruction and deferred funding rules are defined for single-card and split-card payments;
- deferred payment instruction quote revalidation and material-term confirmation rules are defined;
- DOC-13 promotion quote requirements are consumed before authorization where applicable;
- payment profiles and tokenization boundaries are included without duplicating DOC-17, DOC-18, or DOC-19;
- multi-card funding is defined as MVP scope with configurable card-count limit;
- partial funding is distinguished from payment completion;
- settlement-ready funded portions can be routed to DOC-10 without falsely completing the overall payment;
- payer authorization is mandatory and auditable;
- payment passcode is recorded as a baseline confirmation before authorization proceeds;
- step-up authentication can be conditionally skipped below configurable threshold where allowed;
- payment status and failure handling are defined at product-rule level;
- settlement readiness is distinguished from payout execution;
- admin controls are defined without exposing raw card data;
- DOC-10, DOC-11, DOC-14, DOC-15, DOC-17, DOC-18, and DOC-19 ownership boundaries remain clear.

---

## 22. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.0 | 2026-05-29 | Initial founder working baseline for payment request, card funding, multi-card funding, payment profiles, tokenization boundary, payer authorization, step-up authentication, payment status, failure handling, and settlement readiness. |
| 0.3.0 | 2026-05-30 | Aligned payment eligibility and quote rules with DOC-12 evidence verification outcomes, final evidence snapshots, duplicate/reused evidence routing, and evidence-related payment blocks. |
| 0.2.0 | 2026-05-30 | Aligned payment request scope with updated DOC-01 positioning for invoices, fees, rent, domestic service obligations, and evidence-backed payment boundaries. |
| 0.4.0 | 2026-06-01 | Aligned payment quote and authorization rules with DOC-13 promotion quote, reward entitlement, coupon/voucher, card-linked eligibility, and recalculation requirements. |
| 0.5.0 | 2026-06-02 | Clarified bill and fee MVP baseline and added DOC-14 proportionate risk-routing boundary. |
| 0.6.0 | 2026-06-02 | Aligned payment authorization and payment-profile handling with DOC-15 by adding payment passcode, authentication/security data references, and DOC-15 privacy classification boundaries. |
| 0.7.0 | 2026-06-02 | Added MVP user payment instruction model covering deferred single-card and split-card funding, reminder boundaries, partial funding, funding-leg status, selected transfer date, and partial payout routing to DOC-10. |
| 0.8.0 | 2026-06-02 | Added deferred payment instruction quote revalidation, promotion quote expiry/reservation open question, and changed-term confirmation before funding submission. |
