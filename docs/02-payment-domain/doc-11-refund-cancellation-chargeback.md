---
document_id: DOC-11
title: Refund, Cancellation & Chargeback
version: 0.6.1
status: Founder Working Baseline
owner: Payments / Operations
reviewers:
  - Product Lead
  - Payments Lead
  - Finance Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
  - Customer Support Lead
  - Engineering Lead
approvers:
  - Project Owner
  - Payments Lead
  - Operations Lead
  - Finance Lead
last_updated: 2026-07-02
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
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

# DOC-11 - Refund, Cancellation & Chargeback

## 1. Purpose

This document defines PayPlus MVP rules for cancellation, refund, reversal, dispute, chargeback, payee withdrawal, fee reversal, payout hold, recovery, and related case handling.

DOC-11 owns the payment-domain policy and system behavior required to handle exceptions after a request is created, authorized, paid, settled, or paid out.

This document is not a final legal policy, accounting memo, PSP/acquirer operating manual, customer support script, ledger schema, API specification, or admin dashboard design.

---

## 2. Scope and Ownership

DOC-11 covers:

- pre-authorization rejection, query, dispute, and payee withdrawal;
- cancellation before and after payment authorization;
- payment instruction cancellation, expiry, and incomplete split-card handling;
- refund eligibility and approval rules;
- technical reversals and operational adjustments;
- chargeback case handling;
- payout hold and recovery triggers;
- fee, promotion, and revenue reversal treatment;
- evidence, audit, support, and reporting requirements.
- DOC-12 evidence verification, duplicate/reused evidence, and extracted-field history used in case decisions.

Detailed specifications belong to:

| Topic | Owning Document |
| --- | --- |
| Product positioning and commercial assumptions | DOC-01, DOC-02 |
| Compliance controls and launch blockers | DOC-04 |
| Product requirements and user journeys | DOC-05, DOC-06 |
| User-facing wording and authorization disclosures | DOC-07 |
| Notifications, receipts, and status messages | DOC-08 |
| Payment authorization, payment status, settlement readiness, multi-card funding | DOC-09 |
| Payout execution, payout holds, payout recovery, reconciliation | DOC-10 |
| Bill category, OCR/autofill, evidence verification, duplicate/reused evidence, payee matching | DOC-12 |
| Promotion engine, coupon/voucher, reward entitlement, miles, referral, membership, and clawback rules | DOC-13 |
| Fraud, anti-cashout, fake invoice, fake rent, collusion, abuse monitoring | DOC-14 |
| Privacy, masking, retention, and sensitive evidence data handling | DOC-15 |
| PSP/acquirer, bank, webhook, file, and partner integration details | DOC-17 |
| Ledger, data model, reporting schema, audit event model | DOC-18 |
| Security, evidence access control, authentication | DOC-19 |
| Operational runbooks, escalation, incidents, monitoring | DOC-21 |
| Admin dashboard screens, workflows, permissions, uploads, overrides | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Launch market | Hong Kong. |
| Product model | Evidence-backed, payer-authorized bill, invoice, fee, rent, domestic service, and approved obligation payment platform. |
| Detailed policy | Final refund, cancellation, dispute, chargeback, and reversal policy details remain to be confirmed. |
| Operating approach | MVP should follow industry card-payment practice, subject to PSP/acquirer, legal, compliance, finance, and risk confirmation. |
| Admin support | Admin dashboard must support status handling, review, evidence capture, payout hold, recovery, and audit logging. |
| Payout impact | Refund, dispute, chargeback, and reversal cases may block payout, reverse payout readiness, or trigger recovery. |
| Multi-card impact | Refunds and reversals must support payment split across up to a configurable number of credit cards. |
| Payment instruction impact | A DOC-09 deferred payment instruction may be cancelled or expire before gateway submission. Refund rules apply only to funding legs actually submitted and completed. |
| Fee model | Fee refundability, fee reversals, promotions, coupons, and discounts remain configurable and to be confirmed. |

Unconfirmed items should remain editable assumptions or gated requirements and should not block continued documentation drafting.

---

## 4. Core Principles

PayPlus refund, cancellation, dispute, and chargeback handling must follow these principles:

| Principle | Requirement |
| --- | --- |
| Original transaction linkage | Every case must link to the original request, evidence, payer authorization, payment, payout, fee, and ledger records. |
| Payer authorization remains central | A payee-created request cannot trigger payment, cancellation liability, refund liability, or chargeback exposure until the payer authorizes payment. |
| No wallet or cashout behavior | Refunds, reversals, recoveries, and payout adjustments must not create stored value, user wallet balance, arbitrary transfer, self-cashout, or cash-equivalent behavior. |
| Evidence-based decisioning | Decisions must consider obligation evidence, payer authorization, payee verification, payment status, payout status, support record, and risk flags. |
| Evidence verification traceability | Case review should preserve DOC-12 extraction, correction, duplicate/reuse, verification outcome, and human-review history where applicable. |
| No false certainty | User-facing status must not state that a refund, payout, reversal, settlement, or chargeback outcome is complete before the relevant system of record confirms it. |
| Auditability | Admin decisions must have permission, reason, timestamp, evidence, and immutable event history. |
| Reconciliation first | Refunds, reversals, chargebacks, payouts, fees, recoveries, reserves, and write-offs must be reconcilable. |

---

## 5. Definitions

| Term | Meaning |
| --- | --- |
| Rejection | Payer declines a payee-created request before payment authorization. No payment should be processed. |
| Query or clarification | Payer or payee requests more information before or after authorization. |
| Dispute | A user, payee, or admin-raised case about request validity, payment, payout, service issue, or evidence. A dispute is not automatically a card chargeback. |
| Payee withdrawal | Payee withdraws a request before payer authorization, or requests withdrawal under approved rules after authorization. |
| Payment instruction cancellation | User or admin cancellation of a saved DOC-09 payment instruction or remaining pending funding leg before gateway submission. |
| Cancellation | Stopping a request or payment flow before it becomes final under payment, settlement, or payout rules. |
| Refund | Returning all or part of a completed payment to the payer through the permitted payment rail or PSP/acquirer process. |
| Reversal | Technical, partner, or operational reversal of a payment, fee, promotion, ledger, or payout-related event. |
| Chargeback | Formal cardholder dispute raised through issuer, card network, acquirer, PSP, or payment gateway process. |
| Recovery | Attempt to recover funds from a payee, reserve, future payout, bank transfer, legal process, or other approved method after PayPlus incurs or expects a loss. |
| Write-off | Approved accounting recognition that an amount is unlikely to be recovered. |

---

## 6. Case Types

DOC-11 uses the following case types:

| Case Type | Typical Timing | Primary Owner |
| --- | --- | --- |
| Payer rejection | Before authorization | Product / Support |
| Payer query or clarification | Before or after authorization | Support / Operations |
| Payee withdrawal | Before authorization or approved post-authorization window | Operations |
| Cancellation before authorization | Before payer authorizes payment | Product / Operations |
| Payment instruction cancellation or expiry | After payment context is saved but before one or more funding legs are submitted | Product / Payments / Operations |
| Cancellation after authorization | After authorization but before final completion, settlement, or payout | Payments / Operations |
| Refund request | After payment completion | Operations / Payments |
| Partial refund | After payment completion where allowed | Operations / Payments / Finance |
| Technical reversal | Payment, fee, promotion, settlement, or ledger exception | Payments / Engineering / Finance |
| Duplicate payment correction | Duplicate or erroneous payment identified | Payments / Operations / Finance |
| Chargeback | Issuer/card-network/acquirer process | Payments / Operations / Risk |
| Fraud or abuse case | Suspicious behavior, fake evidence, collusion, cashout risk | Risk / Compliance |
| Recovery or write-off case | After PayPlus loss or expected loss | Finance / Operations / Legal |

---

## 7. Status Model

Refund, cancellation, dispute, chargeback, and reversal cases should use clear status values.

| Status | Meaning |
| --- | --- |
| Open | Case created and awaiting initial review. |
| Pending Information | Additional user, payee, partner, bank, or internal evidence is required. |
| Under Review | Operations, Payments, Risk, Compliance, Finance, or Legal review is active. |
| Approved | Case approved for cancellation, refund, reversal, payout hold, recovery, or other action. |
| Rejected | Case rejected with reason and audit trail. |
| Processing | Approved action submitted to PSP, bank, ledger, payout, or internal process. |
| Completed | Confirmed by relevant system of record. |
| Failed | Action failed and requires review or retry. |
| Escalated | Routed to Risk, Compliance, Legal, Finance, partner, or senior operations. |
| Closed | Case resolved with final outcome and evidence retained. |

Status names may be refined in DOC-18 and DOC-22, but status meaning must remain traceable and auditable.

---

## 8. Pre-Authorization Handling

Before payer authorization:

- payer may reject a payee-created request;
- payer may raise a query, dispute, or support case through the approved exception path where enabled;
- payee may withdraw a request;
- admin may cancel, suspend, or hold a request;
- no card payment should be processed;
- no payout should be generated;
- no refund should be required because funds have not moved.

Pre-authorization rejection, query, dispute, support case, expiry, and withdrawal are product and support events, not payment refund events.

The request lifecycle belongs in DOC-05 and DOC-06. User-facing messages belong in DOC-07 and DOC-08.

For DOC-09 deferred payment instructions:

- cancellation or expiry before gateway submission should not create a refund because no funds moved for that pending leg;
- cancellation or expiry of remaining split-card legs must not reverse already completed funding legs automatically;
- funded legs should follow refund, settlement, payout hold, and recovery rules based on their actual payment and payout status;
- user-facing status must distinguish cancelled or expired pending legs from refunded or reversed funded legs.

---

## 9. Cancellation Rules

Cancellation treatment depends on payment and payout status.

| Stage | Rule |
| --- | --- |
| Before payer authorization | Request may be rejected, withdrawn, expired, disputed, or cancelled without funds movement. |
| Deferred instruction before gateway submission | Pending instruction or pending funding leg may be cancelled or expire without refund, subject to audit and user notification. |
| After authorization but before capture/completion | Cancellation may attempt void, reversal, or cancellation through PSP/acquirer where supported. |
| After payment completion but before upstream settlement | Cancellation normally becomes refund or reversal handling, subject to PSP/acquirer capability. |
| After settlement but before payout | Cancellation may require refund approval and payout hold. |
| After payout | Cancellation normally becomes refund, recovery, dispute, chargeback, or write-off handling; payout reversal is not assumed. |

Cancellation must not bypass risk review, partner rules, fee rules, disclosure requirements, or reconciliation.

For partially funded DOC-09 payment instructions, cancellation may apply to the remaining unpaid instruction balance while completed funding legs remain subject to refund, reversal, payout hold, or recovery rules.

---

## 10. Refund Rules

Refunds may be full or partial where supported by PSP/acquirer, card network, operational policy, and ledger capability.

A refund decision should consider:

- payment status;
- payment instruction and funding-leg status where applicable;
- settlement status;
- payout status;
- payout recovery ability;
- request category;
- original obligation evidence;
- DOC-12 evidence verification outcome and duplicate/reused evidence indicators where applicable;
- payer authorization evidence;
- user and payee account status;
- dispute or fraud indicators;
- chargeback status;
- fee and promotion treatment;
- partner rules and legal requirements.

Refunds must:

- link to the original payment and request;
- link to payment instruction and funding leg where applicable;
- preserve payment method and funding source traceability;
- use permitted PSP/acquirer or approved operational process;
- update ledger, revenue, fee, promotion, payout, and reconciliation records;
- generate appropriate user/admin notifications and receipts where required.

Refunds must not:

- be paid to an unrelated bank account;
- create wallet credit unless a separately approved stored-value model exists;
- be used to cash out card-funded payments;
- be processed without authorization, approval, or audit trail.

---

## 11. Multi-Card Refund Allocation

Where a payment is funded by multiple credit cards, refunds and reversals must support allocation across funding sources.

Default allocation should be proportional to the amount funded by each card unless PSP/acquirer capability, card-network rules, risk decision, or approved policy requires another method.

The system must track:

- payment instruction ID and funding leg ID where applicable;
- original funding split;
- amount refunded per funding source;
- refund status per funding source;
- failed refund attempts per funding source;
- remaining refundable amount;
- fee and promotion allocation impact.

Detailed data model belongs in DOC-18. PSP/acquirer API behavior belongs in DOC-17.

Refund, reversal, dispute, chargeback, support, evidence package, funding-source allocation, and recovery records must carry DOC-15 classification metadata in DOC-18, including sensitivity, displayability, masking, retention, approved purpose, access roles, audit requirements, and lineage to source payment, evidence, payout, and promotion records.

---

## 12. Fee, Promotion, and Revenue Treatment

Refund, cancellation, reversal, dispute, and chargeback cases may affect:

- payer service fees;
- payee-side fees;
- processing fees;
- partner fees;
- coupons;
- promotion codes;
- discount codes;
- subsidies;
- vouchers;
- reward entitlements;
- miles rewards;
- membership benefits;
- revenue share;
- tax and accounting treatment.

Exact fee refundability, fee reversal, coupon restoration, voucher reversal, reward entitlement clawback, miles reversal, promotion clawback, and allocation logic remain to be confirmed and should be configurable where appropriate.

DOC-02 owns business model and unit economics. DOC-13 owns promotion, entitlement, instrument, and fulfilment rules. DOC-18 owns ledger and reporting treatment. DOC-07 and DOC-08 own user-facing disclosure and receipt wording.

---

## 13. Chargeback Rules

Chargebacks must be handled as formal card-payment disputes through the applicable issuer, card network, acquirer, PSP, or payment gateway process.

Each chargeback case must track, at minimum:

- original request ID;
- payment ID;
- funding source or card transaction reference;
- PSP/acquirer reference;
- reason code;
- chargeback amount;
- chargeback fee;
- deadline;
- evidence package status;
- representment status;
- outcome;
- loss, recovery, or write-off status.

Evidence packages should include enough material to defend the transaction, including obligation evidence, OCR/extracted fields where relevant, user corrections, evidence verification outcome, duplicate/reused evidence indicators, payee verification, payer authorization, user disclosures, payment logs, communication history, payout proof where applicable, support notes, and risk review records.

Chargeback outcomes may trigger:

- payout hold;
- payee restriction or suspension;
- payer restriction or review;
- refund block or adjustment;
- recovery from payee;
- reserve or holdback adjustment;
- financial loss recognition;
- risk rule update.

Detailed chargeback deadlines, reason-code mapping, representment workflow, and partner portal handling belong in DOC-17, DOC-21, and DOC-22.

---

## 14. Payout Hold, Recovery, and Write-Off

Refund, dispute, chargeback, fraud, risk, or operational cases may require payout hold before funds are released.

Payout hold is required or recommended where:

- payment is not settled or settlement-ready;
- payment instruction is partially funded and payout, refund, dispute, or risk treatment is unresolved;
- refund request is open and material;
- chargeback has been opened or is reasonably expected;
- obligation evidence is disputed;
- evidence verification is pending, rejected, duplicate-suspected, or fraud/risk escalated;
- payee verification is incomplete or suspended;
- payer/payee relationship appears suspicious;
- payout destination changed recently;
- duplicate payment or processing error is suspected;
- risk, compliance, legal, or finance review requires hold.

After payout, PayPlus may need recovery handling. Recovery methods may include:

- offset against future payout;
- payee repayment;
- reserve or holdback use;
- manual bank recovery where available;
- legal or collections process;
- finance-approved write-off.

DOC-10 owns payout execution and reconciliation. DOC-18 owns accounting and ledger recording. DOC-21 owns operational escalation.

---

## 15. Accounting, Data, and Audit Requirements

Each case must be traceable for accounting, reconciliation, compliance, support, analytics, and chargeback defense.

At minimum, the system must link the case to:

- original request, obligation evidence, evidence verification outcome, payer authorization, payment, funding source, payout where applicable, ledger entries, user/payee records, admin actions, partner references, and support ticket where applicable;
- financial impact, including principal, PayPlus fees, payer/payee fees, PSP/acquirer fees, promotions, payout impact, recovery, write-off, and net exposure where applicable;
- immutable status history, action reason, approver, timestamp, evidence, communication, partner response, and final outcome.

Detailed ledger schema, journal treatment, chart of accounts, tax treatment, reporting tables, and audit event model belong in DOC-18 and Finance policy.

Retention should follow the 7-year tax and audit baseline, subject to final legal, privacy, and compliance review.

---

## 16. Admin, Support, and Communication Requirements

The admin and support workflow must allow PayPlus to classify cases, review evidence, review DOC-12 verification history where relevant, update status, approve or reject actions, apply payout holds, assemble chargeback evidence, track partner references, record recovery/write-off decisions, and maintain role-based audit logs.

Customer support must be able to identify case type, explain current status without overpromising outcome, request missing evidence, record communication, and escalate payment, payout, risk, compliance, legal, or finance issues.

User-facing copy must follow DOC-07. Notification channel routing, notification IDs, receipt records, and retention requirements belong in DOC-08. Detailed support scripts, SLA targets, escalation playbooks, and incident handling belong in DOC-21. Detailed admin screens, permissions, review queues, uploads, overrides, and operational action design belong in DOC-22.

---

## 17. Risk and Abuse Controls

Refund, cancellation, dispute, and chargeback handling must support risk controls for:

- fake bill, fake invoice, fake rent, or fake obligation evidence;
- duplicate or reused evidence;
- material mismatch between extracted evidence and user-corrected fields;
- collusion between payer and payee;
- self-cashout or circular payment behavior;
- repeated refund requests;
- repeated chargebacks;
- payee dispute concentration;
- high-risk category patterns;
- multiple cards used to create refund complexity;
- payout destination changes before refund or dispute;
- excessive support complaints.

Risk triggers should support admin review, payout hold, account restriction, payee suspension, partner escalation, and case escalation.

Detailed risk scoring, thresholds, velocity rules, and monitoring logic belong in DOC-14 and DOC-21.

---

## 18. Reporting and Analytics

PayPlus should track cancellation, refund, partial refund, dispute, chargeback, recovery, write-off, net loss, case aging, support SLA, category concentration, payee concentration, and multi-card refund failure metrics.

Detailed dashboard, warehouse, ledger, and reporting schema belong in DOC-18 and DOC-22.

---

## 19. Controls

| Control | Requirement |
| --- | --- |
| Refund approval | Refunds require approved policy, permission, reason, and audit trail. |
| Payout hold | Open refund, dispute, chargeback, fraud, or recovery cases must be able to block payout where required. |
| Chargeback evidence | Chargeback cases must support retrievable evidence packages. |
| Evidence verification linkage | Refund, dispute, and chargeback cases must preserve DOC-12 verification history where relevant. |
| Fee reversal | Fee, promotion, and revenue reversal logic must be traceable. |
| Multi-card traceability | Refunds must preserve funding-source allocation. |
| No cashout | Refunds and reversals must not pay unrelated recipients or create wallet balance. |
| Case audit | Every admin action must be logged. |
| Reconciliation | Case outcomes must reconcile against payment, payout, bank, PSP, and ledger records. |
| User disclosure | Material refund, cancellation, chargeback, and dispute limitations must be disclosed before authorization where required. |

---

## 20. Assumptions, Constraints, and Dependencies

### 20.1 Assumptions

| ID | Assumption | Owner | Status |
| --- | --- | --- | --- |
| ASM-11-001 | MVP will follow industry card-payment refund and chargeback practice unless final PSP/acquirer rules require a different approach. | Payments / Legal | Open |
| ASM-11-002 | Refund and chargeback handling can be administered through internal dashboard workflows. | Product / Operations | Open |
| ASM-11-003 | Multi-card refund allocation can be supported by selected PSP/acquirer or through approved operational handling. | Payments / Engineering | Open |
| ASM-11-004 | Payout holds can be triggered before payout where refund, dispute, chargeback, fraud, or recovery risk exists. | Payments / Operations | Open |

### 20.2 Constraints

| ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| CON-11-001 | PSP/acquirer rules may limit refund timing, refund amount, partial refund support, and chargeback workflow. | May change product rules and admin workflow. | Payments |
| CON-11-002 | Final legal, compliance, and customer disclosure wording is not yet approved. | User-facing policy must remain draft until reviewed. | Legal / Compliance |
| CON-11-003 | Refunds after payout may create recovery and loss exposure. | Requires payout hold, reserve, recovery, and write-off controls. | Finance / Operations |
| CON-11-004 | Detailed accounting and ledger treatment is not finalized. | Requires DOC-18 follow-up before production launch. | Finance |

### 20.3 Dependencies

| ID | Dependency | Needed For | Status |
| --- | --- | --- | --- |
| DEP-11-001 | PSP/acquirer refund and chargeback rules. | Final refund/chargeback workflow. | Open |
| DEP-11-002 | Final fee and promotion policy. | Fee reversal and revenue treatment. | Open |
| DEP-11-002A | DOC-13 promotion entitlement, reward instrument, miles, voucher, and clawback rules. | Promotion reversal, coupon restoration, miles reversal, and reward clawback. | Open |
| DEP-11-003 | Final payout hold and recovery rules. | Payout risk control. | Open |
| DEP-11-004 | Ledger and data model. | Reconciliation and audit. | Open |
| DEP-11-005 | Admin dashboard workflow. | Operations handling. | Open |
| DEP-11-006 | Customer support SLA and scripts. | User support readiness. | Open |
| DEP-11-007 | Evidence verification records and duplicate/reuse indicators from DOC-12. | Refund, dispute, chargeback, payout hold, and recovery decisions. | Open |

---

## 21. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-11-001 | What final refund window applies by payment status, category, and payout status? | Payments / Legal / Operations | High | Open |
| OQ-11-002 | Which fees are refundable, non-refundable, partially refundable, or reversible? | Finance / Product / Legal | High | Open |
| OQ-11-003 | How should promotions, coupons, discount codes, and subsidies be reversed or clawed back? | Commercial / Finance | Medium | Open |
| OQ-11-003A | How should DOC-13 reward entitlement, coupon/voucher restoration, external voucher reversal, membership benefit reversal, and miles clawback work after refund or chargeback? | Commercial / Finance / Growth | Medium | Open |
| OQ-11-004 | How will chargeback liability be allocated between PayPlus, payer, payee, PSP/acquirer, and partners? | Legal / Finance / Risk | High | Open |
| OQ-11-005 | What reserve, holdback, or recovery model is required for paid-out transactions? | Finance / Payments / Risk | High | Open |
| OQ-11-006 | What partial refund allocation method is supported for multi-card payments? | Payments / Engineering | High | Open |
| OQ-11-007 | What chargeback evidence package format and deadline rules apply under the selected PSP/acquirer? | Payments / Operations | High | Open |
| OQ-11-008 | What customer support SLA applies to refund, cancellation, dispute, and chargeback cases? | Operations / Support | Medium | Open |
| OQ-11-009 | What status values and reason codes should be implemented in the admin dashboard? | Product / Operations / Engineering | Medium | Open |
| OQ-11-010 | What legal wording is required before authorization and in receipts for refund, cancellation, dispute, and chargeback limitations? | Legal / Product | High | Open |
| OQ-11-011 | Which DOC-12 verification outcomes should automatically block refund, payout release, representment, or recovery actions pending review? | Operations / Risk / Payments | High | Open |
| OQ-11-012 | What cancellation, expiry, refund, and user-facing wording should apply to pending or partially funded DOC-09 payment instructions? | Product / Payments / Operations | Medium | Open |

---

## 22. Acceptance Criteria

DOC-11 is acceptable when it clearly defines:

- refund, cancellation, reversal, dispute, chargeback, and payee withdrawal boundaries;
- pre-authorization versus post-authorization handling;
- payment instruction cancellation, expiry, and partially funded exception handling;
- pre-payout versus post-payout handling;
- multi-card refund allocation requirements;
- fee, promotion, and revenue reversal ownership;
- DOC-13 reward entitlement, coupon/voucher, miles, membership, and external voucher reversal boundaries;
- payout hold, recovery, and write-off triggers;
- chargeback evidence and case tracking requirements;
- DOC-12 evidence verification history linkage for refund, dispute, chargeback, payout hold, and recovery decisions;
- admin dashboard capability expectations;
- customer support expectations;
- accounting, ledger, data, audit, reporting, and reconciliation requirements;
- risk and anti-cashout controls;
- owning documents for detailed implementation;
- open questions that do not block continued documentation drafting.

This document must remain a compact payment-domain policy and control document.

It should not become:

- final legal terms;
- customer-facing policy wording;
- PSP/acquirer operating procedure;
- accounting policy memo;
- ledger schema;
- API specification;
- admin dashboard screen design;
- customer support script;
- incident response runbook.

---

## 23. Revision History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.3.0` | `2026-05-30` | Product Documentation Team | Aligned case handling with DOC-12 by adding evidence verification history, OCR/extracted field and user correction records, duplicate/reused evidence indicators, and verification-outcome linkage for refunds, disputes, chargebacks, payout holds, and recovery decisions. |
| `0.4.0` | `2026-06-01` | Product Documentation Team | Aligned refund and chargeback treatment with DOC-13 by adding reward entitlement, coupon/voucher restoration, miles, membership benefit, external voucher, and promotion clawback references. |
| `0.5.0` | `2026-06-02` | Product Documentation Team | Aligned case records, evidence packages, funding-source allocation, recovery, and support data with DOC-15 classification metadata and DOC-18 lineage requirements. |
| `0.6.0` | `2026-06-02` | Product Documentation Team | Aligned exception handling with DOC-09 user payment instruction by adding pending instruction cancellation, expiry, partially funded split-card, funding-leg refund linkage, and partial payout hold boundaries. |
| `0.6.1` | `2026-07-02` | Product Documentation Team | Aligned pre-authorization query and dispute wording with DOC-06B request-route boundaries by treating them as approved exception/support paths rather than normal request actions. |
| `0.2.0` | `2026-05-30` | Product Documentation Team | Simplified draft by consolidating detailed ledger, admin, support, communication, and analytics requirements into compact owner sections with references to DOC-08, DOC-18, DOC-21, and DOC-22. |
| `0.1.0` | `2026-05-30` | Product Documentation Team | Initial founder working baseline for refund, cancellation, reversal, dispute, chargeback, payout hold, recovery, fee reversal, audit, support, and reporting rules. |
