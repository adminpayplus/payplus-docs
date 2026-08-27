---
document_id: DOC-11
title: Refund, Cancellation & Chargeback
version: 1.1.1
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
last_updated: 2026-08-27
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
  - DOC-09 Payment Domain Architecture
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

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-11` |
| **Title** | Refund, Cancellation & Chargeback |
| **Version** | `1.1.1` |
| **Status** | Founder Working Baseline |
| **Owner** | Payments / Operations |
| **Reviewers** | Product Lead<br>Payments Lead<br>Finance Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead<br>Customer Support Lead<br>Engineering Lead |
| **Approvers** | Project Owner<br>Payments Lead<br>Operations Lead<br>Finance Lead |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-02 Business Model & Unit Economics<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines PayPlus MVP rules for cancellation, refund, reversal, dispute, chargeback, source or payout-recipient exceptions, fee reversal, payout hold, recovery, and related case handling.

DOC-11 owns adjustment and case policy for cancellation, refund, reversal, chargeback, dispute, return, recovery, and related exceptions. It does not rewrite DOC-09 Payment or Payment Application facts.

This document is not a final legal policy, accounting memo, PSP/acquirer operating manual, customer support script, ledger schema, API specification, or admin dashboard design.

---

## 2. Scope and Ownership

DOC-11 covers:

- pre-authorization source exceptions, query, and dispute;
- cancellation before and after payment authorization;
- deliberate Payment Instruction cancellation policy and separate adjustment handling for confirmed Payments produced by an incomplete Checkout;
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
| Payment Obligation, Checkout Workspace, funding execution, payer-authorization boundary, immutable Payment and Payment Application, and Effective Coverage response to an effective adjustment | DOC-09 |
| Payout execution, payout holds, payout recovery, reconciliation | DOC-10 |
| Bill category, OCR/autofill, evidence verification, duplicate/reused evidence, payee matching | DOC-12 |
| Promotion engine, coupon/voucher, reward entitlement, miles, referral, membership, and clawback rules | DOC-13 |
| Fraud, anti-cashout, fake invoice, fake rent, collusion, abuse monitoring | DOC-14 |
| Privacy, masking, retention, and sensitive evidence data handling | DOC-15 |
| PSP/acquirer, bank, webhook, file, and partner integration details | DOC-17 |
| Business recording, historical action basis, lineage, audit meaning, and reporting explainability | DOC-18; Finance and the applicable domain owners retain accounting/ledger policy; exact technical representation remains separately gated |
| Security, evidence access control, authentication | DOC-19 |
| Operational runbooks, escalation, incidents, monitoring | DOC-21 |
| Owner-permitted Admin workflow execution, configuration, queues, permissions, and controlled overrides | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Launch market | Hong Kong. |
| Product model | Payer-authorized controlled Bill Category and separate Rent payment platform for approved obligations. Bills follow their accepted tiered Evidence treatment; Rent retains mandatory attached Evidence. |
| Detailed policy | Final refund, cancellation, dispute, chargeback, and reversal policy details remain to be confirmed. |
| Operating approach | MVP should follow industry card-payment practice, subject to PSP/acquirer, legal, compliance, finance, and risk confirmation. |
| Admin support | DOC-11 defines case and adjustment policy. DOC-22 may execute only owner-permitted workflow, configuration, queue, review, hold, recovery, and audit steps; it does not independently determine case, Payment, Payout, risk, privacy, or retention policy. |
| Payout impact | Refund, dispute, chargeback, and reversal cases may block payout, reverse payout readiness, or trigger recovery. |
| Multi-card impact | Refunds and reversals must support payment split across up to a configurable number of credit cards. |
| Payment instruction and Checkout impact | A deliberate DOC-09 Payment Instruction may be cancelled or expire before Provider Submission. An incomplete Checkout remains DOC-09-owned; DOC-11 rules apply only when a confirmed Payment, return, refund, reversal, chargeback, or dispute adjustment exists. |
| Fee model | Fee refundability, fee reversals, promotions, coupons, and discounts remain configurable and to be confirmed. |

Unconfirmed items should remain editable owner-assigned assumptions or gated requirements and block only their affected configuration, enablement, implementation or acceptance work.

When DOC-11 determines that an obligation-attributed financial adjustment has become effective, it must preserve the original Payment and any existing Payment Applications, and provide the effective adjustment amount and attribution to DOC-09. A controlled late-confirmed Payment may have zero or insufficient Applications under DOC-09 and must not acquire one merely because an adjustment exists. DOC-09 uses only the portion legally attributable to existing valid Payment Application coverage in obligation-coverage arithmetic; any remaining adjustment value remains an authoritative adjustment fact outside that arithmetic under the existing owner-controlled settlement, reconciliation, or adjustment boundary. DOC-09 then recalculates the Payment Obligation's Effective Coverage, Outstanding Amount, and future payable capacity without allowing negative coverage or fictional obligation value. The historical Checkout Workspace is not reopened.

---

## 4. Core Principles

PayPlus refund, cancellation, dispute, and chargeback handling must follow these principles:

| Principle | Requirement |
| --- | --- |
| Original transaction linkage | Every case must link to the authoritative Bill/Rent source where applicable, Evidence, Payer authorization, Payment Obligation, Payment, any existing applicable Payment Application, Payout, fee, and ledger records. |
| Payer authorization remains central | An economic Payee is not a PayPlus User or a request originator. Payment, cancellation liability, refund liability, and chargeback exposure require the applicable Payer authorization and confirmed Payment facts. |
| No wallet or cashout behavior | Refunds, reversals, recoveries, and payout adjustments must not create stored value, user wallet balance, arbitrary transfer, self-cashout, or cash-equivalent behavior. |
| Evidence-based decisioning | Decisions must consider obligation evidence, payer authorization, payee verification, payment status, payout status, support record, and risk flags. |
| Evidence verification traceability | Case review should preserve DOC-12 extraction, correction, duplicate/reuse, verification outcome, and human-review history where applicable. |
| No false certainty | User-facing status must not state that a refund, payout, reversal, settlement, or chargeback outcome is complete before the relevant system of record confirms it. |
| Auditability | Owner-permitted case actions must preserve the applicable permission, reason, Evidence, time, historical action basis, and immutable audit meaning under DOC-18's reviewed business-recording contract. Exact technical representation remains separately gated. |
| Reconciliation first | Refunds, reversals, chargebacks, payouts, fees, recoveries, reserves, and write-offs must be reconcilable. |

---

## 5. Definitions

| Term | Meaning |
| --- | --- |
| Pre-authorization discontinuance | A Payer may discontinue temporary capture or a pre-authorization path. No Payment, refund, or Payout result follows merely from that discontinuance. Detailed incomplete-source and Checkout treatment remains with the applicable owners. |
| Query or clarification | A Payer or applicable owner may seek information about a source, Evidence, Payment, Payout, service, or case. It does not create a Request or reciprocal product relationship. |
| Dispute | A Payer, economic Payee through an applicable owner-controlled channel, or owner may raise a case about source facts, Payment, Payout, service, or Evidence. A dispute is not automatically a card chargeback. |
| Source or payout-recipient exception | An owner-governed issue with source facts, intended Payee, destination, or Payout may require the applicable case treatment. It does not create a Payee-user action, Request, or Linking runtime. |
| Payment instruction cancellation | Owner-governed cancellation of a deliberate saved DOC-09 Payment Instruction before it starts Checkout execution. Closing or expiring an incomplete Checkout Workspace remains a separate DOC-09 action. |
| Cancellation | Stopping an applicable Payment-domain path before it becomes final under payment, settlement, or Payout rules. |
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
| Pre-authorization source exception | Before authorization | Product / Support |
| Payer query or clarification | Before or after authorization | Support / Operations |
| Source or payout-recipient exception | Before authorization or owner-governed post-authorization treatment | Operations / Payments |
| Cancellation before authorization | Before payer authorizes payment | Product / Operations |
| Payment instruction cancellation or expiry | After a deliberate Payment Instruction is saved but before it starts Checkout execution | Product / Payments / Operations |
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

Refund, cancellation, dispute, chargeback, and reversal work must separate the case lifecycle from the operational action or outcome.

| Case Lifecycle State | Meaning |
| --- | --- |
| Open | Case created and awaiting initial review. |
| Pending Information | Additional user, payee, partner, bank, or internal evidence is required. |
| Under Review | Operations, Payments, Risk, Compliance, Finance, or Legal review is active. |
| Resolved | A decision or required operational outcome has been reached and recorded. |
| Closed | Case resolved with final outcome and evidence retained. |

Operational action or outcome states such as `Approved`, `Rejected`, `Processing`, `Completed`, `Failed`, or `Escalated` may be recorded against the relevant refund, reversal, chargeback, recovery, hold, or partner action. They must not be used as substitute case-lifecycle states. DOC-11 and the applicable domain owner define the meaning of each action, outcome, and reason. DOC-18 requires the business history and action basis to remain explainable but does not define fields or reason-code design; DOC-22 may execute only owner-permitted workflow/configuration and does not define the values or policy.

---

## 8. Pre-Authorization Handling

Before Payer authorization, a Payer may discontinue temporary capture or an owner may handle a source, Evidence, intended-Payee, or support exception under its own rules. Neither creates a Request, Linking relationship, reciprocal visibility, or Payee-user action. No card Payment should be processed, no Payout should be generated, and no refund should be required because funds have not moved.

Pre-authorization discontinuance, expiry, cancellation, and source/query/dispute/support-case handling are not Payment refund events. A case does not change the authoritative Bill/Rent source or its projection unless the applicable owner expressly governs that result.

User-facing presentation belongs in DOC-06 and DOC-07; notification identity, channel, and delivery belong in DOC-08. DOC-11 does not define a new exception route or user-facing case action.

For deliberate DOC-09 Payment Instructions and incomplete Checkout Workspaces:

- cancellation or expiry of a deliberate Payment Instruction before Checkout execution should not create a refund because no funds moved;
- closing or expiring the unconfirmed remainder of an incomplete Checkout Workspace must not reverse confirmed Payments automatically;
- confirmed Payments should follow refund, settlement, payout hold, and recovery rules based on their actual payment and payout status;
- user-facing presentation must distinguish Payment Instruction cancellation or expiry, Checkout closure or expiry, and refund or reversal outcomes.

---

## 9. Cancellation Rules

Cancellation treatment depends on payment and payout status.

| Stage | Rule |
| --- | --- |
| Before Payer authorization | Temporary capture may be discontinued or an owner-governed source/query/dispute exception may be handled without funds movement. A case may apply an applicable hold without creating a Request lifecycle. |
| Deliberate Payment Instruction before Checkout execution | The instruction may be cancelled or expire without refund, subject to audit and any owner-governed communication treatment. |
| Incomplete Checkout before Provider Submission for a remaining Funding Leg | The Checkout may be closed or expire under DOC-09 without refund for its unconfirmed remainder; confirmed Payments remain unchanged. |
| After authorization but before capture/completion | Cancellation may attempt void, reversal, or cancellation through PSP/acquirer where supported. |
| After payment completion but before upstream settlement | Cancellation normally becomes refund or reversal handling, subject to PSP/acquirer capability. |
| After settlement but before payout | Cancellation may require refund approval and payout hold. |
| After payout | Cancellation normally becomes refund, recovery, dispute, chargeback, or write-off handling; payout reversal is not assumed. |

Cancellation must not bypass risk review, partner rules, fee rules, disclosure requirements, or reconciliation.

For a partially funded DOC-09 Checkout Workspace, ending the remaining continuation follows DOC-09 closure or expiry rules and does not cancel confirmed Payments. Confirmed Payments remain subject to refund, reversal, payout hold, or recovery rules in this document.

---

## 10. Refund Rules

Refunds may be full or partial where supported by PSP/acquirer, card network, operational policy, and ledger capability.

A refund decision should consider:

- payment status;
- payment instruction and funding-leg status where applicable;
- settlement status;
- payout status;
- payout recovery ability;
- controlled Bill Category or separate Rent context;
- authoritative Bill/Rent source and applicable Evidence;
- DOC-12 evidence verification outcome and duplicate/reused evidence indicators where applicable;
- payer authorization evidence;
- Payer and economic-Payee context where applicable; no PayPlus Payee account is required;
- dispute or fraud indicators;
- chargeback status;
- fee and promotion treatment;
- partner rules and legal requirements.

Refunds must:

- link to the authoritative Bill/Rent source, applicable Payment Obligation, Payment, and any existing applicable Payment Application;
- link to payment instruction and funding leg where applicable;
- preserve payment method and funding source traceability;
- use permitted PSP/acquirer or approved operational process;
- update ledger, revenue, fee, promotion, payout, and reconciliation records;
- publish owner-governed outcome facts for DOC-07/DOC-08 receipt and communication treatment where required.

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

DOC-18 supplies the reviewed business-recording, lineage and explainability contract. Detailed technical data representation remains separately gated. PSP/acquirer API behavior belongs in DOC-17 only under an accepted provider-specific contract.

Refund, reversal, dispute, chargeback, support, evidence-package, funding-source-allocation, and recovery history must preserve DOC-15 classification, approved-purpose access, masking, retention and visibility treatment, together with DOC-18 business lineage and explainability. This requirement does not approve fields, access roles, schema, storage, or implementation.

---

## 12. Fee, Promotion, and Revenue Treatment

Refund, cancellation, reversal, dispute, and chargeback cases may affect:

- payer service fees;
- economic-Payee-side fees where applicable;
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

When an effective DOC-11 adjustment, refund, reversal, dispute, or chargeback outcome affects a reward entitlement, DOC-11 supplies the financial/effective adjustment fact to DOC-13. DOC-13 determines canonical entitlement and issued-instrument truth; DOC-06B and DOC-07 consume that truth for route/presentation and user-facing expression. Uncertain or duplicate refund/chargeback callbacks must not independently alter entitlement or issued-instrument truth.

DOC-02 owns business model and unit economics. Finance and the applicable payment owners own accounting and ledger policy. DOC-13 owns promotion, entitlement, instrument, and fulfilment rules. DOC-18 owns business-recording and reporting-explainability obligations only. DOC-07 and DOC-08 own user-facing disclosure and receipt wording.

---

## 13. Chargeback Rules

Chargebacks must be handled as formal card-payment disputes through the applicable issuer, card network, acquirer, PSP, or payment gateway process.

Each chargeback case must track, at minimum:

- authoritative Bill/Rent source ID and applicable Payment Obligation ID;
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
- economic-Payee restriction or suspension where applicable;
- payer restriction or review;
- refund block or adjustment;
- recovery from payee;
- reserve or holdback adjustment;
- financial loss recognition;
- risk rule update.

DOC-17 and the applicable payments, legal, and partner owners govern chargeback deadlines, reason-code meaning, representment, and partner handling. DOC-21 owns operational escalation; DOC-22 may execute only the owner-permitted workflow/configuration. DOC-11 does not define those mechanisms.

---

## 14. Payout Hold, Recovery, and Write-Off

Refund, dispute, chargeback, fraud, risk, or operational cases may require payout hold before funds are released.

Where an active refund, dispute, chargeback, recovery, or linked case materially depends on the authoritative Bill/Rent source or an applicable Payment Obligation, ordinary Archive visibility must be blocked until the case resolves or the applicable owner outcome permits it. Archive visibility never closes the case, removes its Evidence, releases a hold, or alters completed Payment/Payout history. Detailed Restore, prior-version, Evidence-version, and replacement-source presentation remains deferred to the applicable owners.

Payout hold is required or recommended where:

- payment is not settled or settlement-ready;
- Checkout Workspace is partially funded and payout, refund, dispute, or risk treatment for a confirmed Payment is unresolved;
- a material refund case is open;
- chargeback has been opened or is reasonably expected;
- obligation evidence is disputed;
- evidence verification is pending, rejected, duplicate-suspected, or fraud/risk escalated;
- intended-Payee verification is incomplete, suspended, or owner-held;
- Payer/economic-Payee relationship appears suspicious;
- payout destination changed recently;
- duplicate payment or processing error is suspected;
- risk, compliance, legal, or finance review requires hold.

For a Tier 2 Bill, an Evidence-acceptance Payout hold does not itself initiate, approve, or imply cancellation, Refund, reversal, chargeback, recovery, or case outcome. A confirmed Payment remains a DOC-09 immutable financial fact while DOC-10 retains the Payout-held or release decision. DOC-11 determines a refund or case only when its applicable owner-governed policy and evidence require one; it does not derive that result from pending Evidence acceptance.

After payout, PayPlus may need recovery handling. Recovery methods may include:

- offset against future payout;
- payee repayment;
- reserve or holdback use;
- manual bank recovery where available;
- legal or collections process;
- finance-approved write-off.

DOC-10 owns payout execution and reconciliation. Finance and the applicable financial owners own accounting and ledger policy; DOC-18 requires resulting business facts and history to remain explainable without defining technical ledger representation. DOC-21 owns operational escalation.

---

## 15. Accounting, Data, and Audit Requirements

Each case must be traceable for accounting, reconciliation, compliance, support, analytics, and chargeback defense.

At minimum, the system must link the case to:

- authoritative Bill/Rent source, applicable Payment Obligation, Evidence verification outcome, Payer authorization, Payment, any existing applicable Payment Application, Funding Leg, Payout where applicable, ledger entries, Payer/economic-Payee context, owner-permitted actions, partner references, and support ticket where applicable;
- financial impact, including principal, PayPlus fees, Payer/economic-Payee fees where applicable, PSP/acquirer fees, promotions, Payout impact, recovery, write-off, and net exposure where applicable;
- immutable status history, action reason, approver, timestamp, evidence, communication, partner response, and final outcome.

Finance and the applicable financial owners retain journal treatment, chart of accounts, tax treatment and ledger policy. DOC-18 owns the reviewed business-recording, historical-basis, lineage, audit-meaning and reporting-obligation contract. Ledger schema, reporting tables and audit-event implementation remain separately authorized technical work.

DOC-15 owns the Founder-settled indefinite-retention requirement and applicable approved-purpose access and privacy controls. DOC-11 consumes that owner-governed outcome, preserves authoritative case and financial history, and does not define a disposition mechanism.

---

## 16. Owner-Permitted Administration, Support, and Communication

DOC-11 owns case and adjustment policy. DOC-22 may execute only the owner-permitted workflow, configuration, queue, review, hold, recovery, correction, or audit step. DOC-22 does not independently determine an Evidence outcome, payment/financial truth, Payout disposition, risk outcome, privacy/retention rule, legal conclusion, or final case policy.

Customer support must be able to identify case type, explain current status without overpromising outcome, request missing evidence, record communication, and escalate payment, payout, risk, compliance, legal, or finance issues.

User-facing Copy must follow DOC-07. Notification identity, channel routing, delivery, and receipt communication records belong in DOC-08. DOC-15 owns privacy/retention requirements; DOC-18 owns business-recording, history, audit-meaning, lineage and explainability requirements, not machine status/event representation. Detailed support scripts, SLA targets, escalation playbooks, and incident handling belong in DOC-21. Detailed Admin screens, permissions, review queues, uploads, overrides, and operational action design belong in DOC-22 only where an applicable owner permits them.

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

Risk triggers may require the applicable owner-controlled review, Payout hold, Payer or economic-Payee restriction, partner escalation, or case escalation. DOC-22 executes only owner-permitted workflow.

Detailed risk scoring, thresholds, velocity rules, and monitoring logic belong in DOC-14 and DOC-21.

---

## 18. Reporting and Analytics

PayPlus should track cancellation, refund, partial refund, dispute, chargeback, recovery, write-off, net loss, case aging, support SLA, Category concentration, economic-Payee concentration, and multi-card refund failure metrics.

DOC-18 defines the business-reporting and explainability obligations. Detailed dashboard, warehouse, ledger and reporting representation remain separately gated; DOC-22 may execute only a specifically owner-permitted operational presentation.

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
| Case audit | Every owner-permitted action must receive the required audit treatment. |
| Reconciliation | Case outcomes must reconcile against payment, payout, bank, PSP, and ledger records. |
| User disclosure | Material refund, cancellation, chargeback, and dispute limitations must be disclosed before authorization where required. |

### 19.1 HOME-ROOT Recent Activity Refund and Reversal Projection

DOC-11 publishes each canonical completed Refund or Reversal outcome for consumption by the DOC-06B HOME-ROOT Recent Activity contract. Refund and Reversal retain distinct source meaning and outcome identity.

Each outcome supplies its canonical ordering timestamp, canonical amount, and canonical funds-flow direction. These values retain their DOC-11 meaning at the handoff boundary.

Cases, instructions, failures, intermediate actions, technical callbacks, allocation events, recovery work, and supporting events are not completed Refund or Reversal outcomes merely because they support one. Uncertain or repeated callbacks remain subject to this document's idempotency and canonical-outcome rules.

DOC-11 does not create a cross-domain activity model. DOC-06B is the sole normative owner of Home eligibility, cap, ordering, shared Refund/Reversal presentation, cross-domain consumption, deduplication, navigation, entry, and return behavior. DOC-07 owns user-facing expression; DOC-18 supplies the reviewed business-recording and lineage contract. Physical fields, machine event/status taxonomy and audit implementation remain future separately authorized Engineering/Data work.

---

## 20. Assumptions, Constraints, and Dependencies

### 20.1 Assumptions

| ID | Assumption | Owner | Status |
| --- | --- | --- | --- |
| ASM-11-001 | MVP will follow industry card-payment refund and chargeback practice unless final PSP/acquirer rules require a different approach. | Payments / Legal | Open |
| ASM-11-002 | Refund and chargeback handling can be executed through owner-permitted internal workflows. | Product / Operations | Open |
| ASM-11-003 | Multi-card refund allocation can be supported by selected PSP/acquirer or through approved operational handling. | Payments / Engineering | Open |
| ASM-11-004 | Payout holds can be triggered before payout where refund, dispute, chargeback, fraud, or recovery risk exists. | Payments / Operations | Open |

### 20.2 Constraints

| ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| CON-11-001 | PSP/acquirer rules may limit refund timing, refund amount, partial refund support, and chargeback workflow. | May change product rules and owner-permitted workflow. | Payments |
| CON-11-002 | Final legal, compliance, and customer disclosure wording is not yet approved. | User-facing policy must remain draft until reviewed. | Legal / Compliance |
| CON-11-003 | Refunds after payout may create recovery and loss exposure. | Requires payout hold, reserve, recovery, and write-off controls. | Finance / Operations |
| CON-11-004 | Detailed accounting and ledger treatment is not finalized. | Requires Finance and applicable owner decisions plus separately authorized technical representation before affected implementation or launch. DOC-18 supplies business-recording inputs only. | Finance |

### 20.3 Dependencies

| ID | Dependency | Needed For | Status |
| --- | --- | --- | --- |
| DEP-11-001 | PSP/acquirer refund and chargeback rules. | Final refund/chargeback workflow. | Open |
| DEP-11-002 | Final fee and promotion policy. | Fee reversal and revenue treatment. | Open |
| DEP-11-002A | DOC-13 promotion entitlement, reward instrument, miles, voucher, and clawback rules. | Promotion reversal, coupon restoration, miles reversal, and reward clawback. | Open |
| DEP-11-003 | Final payout hold and recovery rules. | Payout risk control. | Open |
| DEP-11-004 | Ledger and data model. | Reconciliation and audit. | Open |
| DEP-11-005 | Owner-permitted DOC-22 workflow. | Operations handling. | Open |
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
| OQ-11-004 | How will chargeback liability be allocated between PayPlus, Payer, economic Payee, PSP/acquirer, and partners? | Legal / Finance / Risk | High | Open |
| OQ-11-005 | What reserve, holdback, or recovery model is required for paid-out transactions? | Finance / Payments / Risk | High | Open |
| OQ-11-006 | What partial refund allocation method is supported for multi-card payments? | Payments / Engineering | High | Open |
| OQ-11-007 | What chargeback evidence package format and deadline rules apply under the selected PSP/acquirer? | Payments / Operations | High | Open |
| OQ-11-008 | What customer support SLA applies to refund, cancellation, dispute, and chargeback cases? | Operations / Support | Medium | Open |
| OQ-11-009 | What owner-approved status values, reason codes, and DOC-22 workflow configuration are required for case execution? | Product / Operations / Engineering | Medium | Open |
| OQ-11-010 | What legal wording is required before authorization and in receipts for refund, cancellation, dispute, and chargeback limitations? | Legal / Product | High | Open |
| OQ-11-011 | Which DOC-12 verification outcomes should automatically block refund, payout release, representment, or recovery actions pending review? | Operations / Risk / Payments | High | Open |
| OQ-11-012 | What final cancellation, expiry, refund, and user-facing wording should apply to deliberate DOC-09 Payment Instructions and incomplete Checkout Workspaces? | Product / Payments / Operations | Medium | Open |

---

## 22. Acceptance Criteria

DOC-11 is acceptable when it clearly defines:

- refund, cancellation, reversal, dispute, chargeback, and source/payout-recipient exception boundaries;
- pre-authorization versus post-authorization handling;
- deliberate Payment Instruction cancellation or expiry and incomplete Checkout exception handling;
- pre-payout versus post-payout handling;
- multi-card refund allocation requirements;
- fee, promotion, and revenue reversal ownership;
- DOC-13 reward entitlement, coupon/voucher, miles, membership, and external voucher reversal boundaries;
- payout hold, recovery, and write-off triggers;
- chargeback evidence and case tracking requirements;
- DOC-12 evidence verification history linkage for refund, dispute, chargeback, payout hold, and recovery decisions;
- Adjustment arithmetic preserves immutable Payment and Payment Application facts, applies only the legally attributable portion to valid Application coverage, never fabricates an Application or negative coverage, and leaves any excess adjustment fact outside coverage arithmetic for the existing DOC-09/DOC-10 controlled boundary;
- owner-permitted Admin execution boundary;
- customer support expectations;
- accounting, ledger, data, audit, reporting, and reconciliation requirements;
- risk and anti-cashout controls;
- owning documents for detailed implementation;
- open questions with their owner and affected-path dependency visible;
- DOC-11 publishes distinct canonical Refund and Reversal outcomes with their ordering timestamp, amount, and funds-flow direction for the DOC-06B HOME-ROOT handoff; supporting events remain separate non-outcomes, and DOC-06B owns Home eligibility, shared presentation, ordering, deduplication, sign presentation, navigation, and return behavior.

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
| 1.1.1 | 2026-08-27 | Product Documentation Team | Removed overbroad DOC-18 accounting, ledger, field, reason-code and technical-representation ownership while preserving distinct immutable case and financial histories. |
| 1.1.0 | 2026-08-22 | Product Documentation Team | Aligned Tier 2 Evidence-acceptance Payout holds with the existing case boundary: the hold alone is not cancellation, Refund, reversal, recovery, or a case outcome, and confirmed Payment remains immutable. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. | Stage 11 alignment evidence |
| `0.7.3` | `2026-08-13` | Product Documentation Team | Bounded adjustment impact to valid Payment Application coverage for zero- or insufficient-Application cases while preserving immutable Payment and adjustment facts and existing owner-controlled settlement boundaries. |
| `0.7.2` | `2026-08-12` | Product Documentation Team | Applied the Founder-settled indefinite-retention handoff to adjustment, refund, dispute and case records without changing their financial or operational mechanisms. |
| `0.7.1` | `2026-08-12` | Product Documentation Team | Qualified adjustment and case lineage for DOC-09's controlled late-confirmation zero-Application exception and returned Rewards presentation to DOC-13, DOC-06B, and DOC-07 ownership. |
| `0.7.0` | `2026-08-12` | Product Documentation Team | Replaced active Request and Payee-user case semantics with authoritative Bill/Rent-source, Payment Obligation, economic-Payee, Payer-only, owner-permitted execution, and Archive-blocker boundaries while preserving DOC-09 Payment/Application and DOC-10 Payout handoffs. |
| `0.6.6` | `2026-08-05` | Product Documentation Team | Added the bounded HOME-ROOT Recent Activity Refund/Reversal handoff by publishing distinct canonical outcome identity, ordering timestamp, amount, funds-flow direction, and source truth while retaining Home eligibility, shared presentation, ordering, deduplication, navigation, and return behavior in DOC-06B. |
| `0.6.5` | `2026-07-31` | Product Documentation Team | Aligned adjustment ownership with immutable DOC-09 Payment and Payment Application facts, the Effective Coverage/Outstanding Amount recalculation boundary, and incomplete Checkout closure treatment. |
| `0.6.4` | `2026-07-26` | Product Documentation Team | Aligned obligation archive/restore blockers with active refund, dispute, chargeback, recovery, and linked-case handling without changing case lifecycle or completed history. |
| `0.6.3` | `2026-07-26` | Product Documentation Team | Established the canonical five-state case lifecycle, separated operational action/outcome states, and clarified that disputes and queries are linked cases rather than request lifecycle states. |
| `0.6.2` | `2026-07-21` | Product Documentation Team | Linked authoritative reward restoration/reversal outcomes to canonical My Rewards Active/History status, including restored usable rewards returning to Active, and prohibited duplicate outcome application from uncertain or repeated callbacks. |
| `0.3.0` | `2026-05-30` | Product Documentation Team | Aligned case handling with DOC-12 by adding evidence verification history, OCR/extracted field and user correction records, duplicate/reused evidence indicators, and verification-outcome linkage for refunds, disputes, chargebacks, payout holds, and recovery decisions. |
| `0.4.0` | `2026-06-01` | Product Documentation Team | Aligned refund and chargeback treatment with DOC-13 by adding reward entitlement, coupon/voucher restoration, miles, membership benefit, external voucher, and promotion clawback references. |
| `0.5.0` | `2026-06-02` | Product Documentation Team | Aligned case records, evidence packages, funding-source allocation, recovery, and support data with DOC-15 classification metadata and DOC-18 lineage requirements. |
| `0.6.0` | `2026-06-02` | Product Documentation Team | Aligned exception handling with DOC-09 user payment instruction by adding pending instruction cancellation, expiry, partially funded split-card, funding-leg refund linkage, and partial payout hold boundaries. |
| `0.6.1` | `2026-07-02` | Product Documentation Team | Aligned pre-authorization query and dispute wording with DOC-06B request-route boundaries by treating them as approved exception/support paths rather than normal request actions. |
| `0.2.0` | `2026-05-30` | Product Documentation Team | Simplified draft by consolidating detailed ledger, admin, support, communication, and analytics requirements into compact owner sections with references to DOC-08, DOC-18, DOC-21, and DOC-22. |
| `0.1.0` | `2026-05-30` | Product Documentation Team | Initial founder working baseline for refund, cancellation, reversal, dispute, chargeback, payout hold, recovery, fee reversal, audit, support, and reporting rules. |
