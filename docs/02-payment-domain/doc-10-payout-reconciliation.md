---
document_id: DOC-10
title: Payout & Reconciliation
version: 0.8.2
status: Founder Working Baseline
owner: Payments / Finance
reviewers:
  - Product Lead
  - Engineering Lead
  - Payments Lead
  - Finance Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Payments Lead
  - Finance Lead
last_updated: 2026-08-13
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
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

# DOC-10 - Payout & Reconciliation

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-10` |
| **Title** | Payout & Reconciliation |
| **Version** | `0.8.2` |
| **Status** | Founder Working Baseline |
| **Owner** | Payments / Finance |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Payments Lead<br>Finance Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Payments Lead<br>Finance Lead |
| **Last Updated** | `2026-08-13` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines PayPlus MVP rules for payout readiness, payout execution, payout batching, payout rails, settlement calendar handling, reconciliation, payout exceptions, and payout reporting.

DOC-10 starts from the confirmed Payment and destination facts handed off by DOC-09. It owns Settlement, Payout, reconciliation, timing, readiness, and the movement of eligible funds from PayPlus's operating bank account to approved payees. Checkout completion is not a prerequisite for accepting a confirmed Payment handoff.

This document is not a bank API specification, ledger schema, accounting policy, refund manual, or admin dashboard UI specification.

---

## 2. Scope and Ownership

DOC-10 covers:

- payout readiness checks;
- payout destination controls;
- payout rail rules;
- payout timing and cutoff rules;
- payout grouping and batching;
- bank file/API payout options;
- bank record ingestion;
- reconciliation matching rules;
- payout exception handling;
- payout metrics and reporting expectations.

Detailed specifications belong to:

| Topic | Owning Document |
| --- | --- |
| Payment Obligation, Checkout Workspace, payer-authorization boundary, Provider Confirmation acceptance, confirmed Payment, Payment Application, and destination snapshot handoff | DOC-09 |
| Refund, cancellation, chargeback, dispute, and reversal operations | DOC-11 |
| Risk scoring, anti-cashout, fake invoice, fake rent, and monitoring rules | DOC-14 |
| Privacy, masking, retention, and approved-purpose access for payout and bank records | DOC-15 |
| Bank API, bank file, SFTP, webhook, and integration details | DOC-17 |
| Payout, batch, bank-feed, ledger, and reconciliation data model | DOC-18 |
| Operational monitoring, incident handling, and escalation | DOC-21 |
| Owner-permitted workflow execution for upload, review, override, and resolution | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Payout provider | PayPlus expects to payout directly from its operating bank account. |
| Payout rails | FPS, cheque, and EPS are acceptable Hong Kong payout rails. |
| Upstream settlement | Payment gateway settlement expected T+1 to T+3. |
| Payout timing | Payout expected on the same day after upstream settlement, subject to readiness checks, bank processing, holidays, holds, reserves, and exceptions. |
| Gateway cutoff | Default cutoff assumption is 23:00 Hong Kong time. Payments from 23:00 to 23:59 are treated as next business day for settlement timing. |
| Business days | Hong Kong holidays and non-business days postpone settlement and payout. Foreign/offshore payment methods may follow platform, issuer, acquirer, or foreign-market calendars. |
| Split payment grouping | Same payer, payee, and obligation payments before cutoff on the same business day should normally group into one payout where permitted. |
| Confirmed Payment handoff | Each eligible confirmed Payment handed off by DOC-09 may proceed to Settlement and Payout evaluation independently of whether its originating Checkout Workspace later completes, closes, or expires. |
| Selected transfer date | An owner-governed selected transfer date may delay payout but must not be earlier than applicable T+3 / settlement-ready timing and payout readiness checks. |
| Batch processing | Normal non-red-flag payouts should support batch generation for bank processing. Direct bank API payout should remain a supported future option. |

Unconfirmed bank setup, file formats, API options, exact cutoff mechanics, and reconciliation feeds should remain editable assumptions until confirmed.

---

## 4. Payout Model

PayPlus routes approved payouts from its operating bank account after upstream payment settlement is confirmed or settlement-ready according to approved evidence.

Payout must not operate as:

- user wallet withdrawal;
- arbitrary bank transfer;
- cashout;
- unsupported P2P transfer;
- payout to an unverified or unsupported recipient;
- payout unrelated to an approved bill, invoice, rent, fee, or obligation.

Payout is linked to the approved obligation, not to the number of cards the payer used.

---

## 5. Payout Readiness

A payout may proceed only when all required checks pass.

| Check | Requirement |
| --- | --- |
| Payment status | Full payment or funded portion must be completed according to DOC-09. An overall partially funded Checkout Workspace must not be treated as fully completed; a deliberate Payment Instruction is a distinct DOC-09 object. |
| Payment Application lineage | A confirmed Payment normally reaches Payout with one or more applicable Payment Applications. Under DOC-09's controlled late-confirmation exception, a confirmed Payment may temporarily have zero Applications: it remains a valid Payment but is not ordinarily Payout-ready until the applicable owner-controlled Settlement, reconciliation, or adjustment treatment permits it. |
| Settlement | Upstream settlement must be confirmed or settlement-ready for the specific funded portion under approved rules. |
| Payee / recipient status | The economic Payee, whether an individual or institution/company, must be eligible for the applicable payout. A PayPlus User account is not required. |
| Payout destination | The immutable authorization-time destination snapshot attached to the confirmed Payment must pass the applicable intended-Payee, Evidence, risk, compliance, and payout checks. Subsequent source changes must not alter the snapshot. |
| Authoritative source and Evidence boundary | The Payer-controlled Bill/Rent source, applicable Evidence-to-Payee outcome, and payment-facing facts must support the payout context. No Request lifecycle, Payee acceptance, Linking relationship, or Consumer Receiving Info profile is a payout gate. |
| Case or hold | An open material dispute, support case, operational, risk, refund, or chargeback hold may block payout under DOC-11 and DOC-14 without changing the authoritative Bill/Rent source or its visibility projection. |
| Risk status | The applicable owner-controlled risk outcome must permit payout. |
| Refund/dispute/chargeback hold | Payout must be blocked where policy requires hold. |
| Amount | Payout amount must match approved obligation, funded portion, fee, adjustment, partial payout, and ledger rules. |
| Selected transfer date | Payout must respect the owner-governed selected transfer date where set and valid. |
| Duplicate prevention | Payout item must not have been paid already. |

A Payer Archive visibility change must not proceed where an active payout, payout hold, reconciliation exception, or unresolved payout-dependent operation materially relies on the authoritative Bill/Rent source. Archive visibility must not cancel, redirect, duplicate, or rewrite payout and destination snapshots, and it must not change completed payout or reconciliation history. Detailed Archive, Restore, and version presentation remains with the applicable DOC-06, DOC-12, DOC-15, and DOC-18 owner work.

Failed checks should route to pending, held, or exception status with an audit trail.

---

## 6. Payout Destination Controls

A payout destination is the bank account, FPS identifier, cheque recipient, EPS, or other approved rail-specific destination represented by owner-governed facts in one controlled Bill/Rent source and the effective authorization-time destination snapshot. It may be supported by Payer-supplied source facts, Evidence extraction followed by Payer review, or an owner-permitted correction. It is not a reusable Consumer Receiving Info library, a Payee User profile, a Request, or a Linking relationship.

### 6.1 Destination Snapshot Boundary

The destination used for Payout is the immutable context-specific snapshot frozen no later than final Payer authorization. A later source, intended-Payee, or payout-configuration change must not silently redirect a confirmed Payment or Payout. A material destination change after authorization requires the applicable owner-controlled treatment and, where applicable, renewed Payer authorization.

If the authorized snapshot becomes unusable, Payout must be held, failed, or otherwise resolved under the applicable payout, risk, support, and partner rules. It must not be silently switched to another destination. DOC-10 does not define a replacement route, notification, source-library, or user-facing recovery behaviour.

### 6.2 Validation, Review, and Audit

Destination processing must:

- apply intended-Payee, Evidence, controlled Bill Category, Payout, risk, anti-cashout, sanctions, privacy, and compliance checks appropriate to the source and context;
- preserve the source and authorization-time snapshot reference, Payer authorization, Payout result, and owner-governed review/audit evidence without redefining the detailed data representation;
- keep internal provider, risk, match-score, and review reasons out of ordinary user display; and
- use DOC-22 only for owner-permitted workflow execution. DOC-22 does not determine destination, payment, payout, risk, privacy, or security policy.

DOC-12 owns Evidence and Evidence-to-Payee matching. DOC-14 owns risk meaning and routing. DOC-15 owns approved-purpose access and retention. DOC-18 owns approved representation, status/event, audit, and lineage requirements. DOC-19 owns security/recovery controls. DOC-21 owns support and operations. DOC-08 owns notification identity, channel, and delivery. Exact user-facing presentation remains with DOC-06/DOC-07.

---

## 7. Payout Rails

PayPlus MVP payout rails may include:

| Rail | Use | Notes |
| --- | --- | --- |
| FPS | Primary electronic payout rail where supported. | Suitable for Hong Kong bank transfers where payee destination supports it. |
| Cheque | Manual or fallback payout rail. | Requires cheque issue, dispatch, clearance, and reconciliation handling. |
| EPS | Acceptable Hong Kong payout rail where operationally available. | Final operating setup and processing details remain to be confirmed. |
| Bank API | Future or optional direct payout path. | Preserve architecture opportunity; details belong in DOC-17. |
| Bank batch upload | Practical MVP payout path for bulk processing. | File format belongs in DOC-17; owner-permitted upload workflow belongs in DOC-22. |

Rail availability should be configurable by payee type, category, amount, risk status, destination, business day, and operations readiness.

---

## 8. Settlement Calendar and Cutoff Rules

Settlement and payout should be calculated by business day, not simple calendar day.

### 8.1 Gateway Cutoff

Default assumption:

- payment gateway cutoff is 23:00 Hong Kong time;
- payments from 00:00 to 22:59 are treated as same business day for settlement grouping;
- payments from 23:00 to 23:59 are treated as next business day for settlement timing;
- settlement delay rolls forward accordingly.

Exact gateway cutoff, timezone, and holiday behavior must be confirmed with the PSP/acquirer and documented in DOC-17.

### 8.2 Hong Kong Business Days

Hong Kong public holidays and non-business days postpone settlement and payout.

If settlement or payout would fall on a non-business day, it should roll to the next applicable business day unless the rail or partner supports otherwise.

### 8.3 Foreign and Offshore Calendars

Foreign-issued cards and offshore platforms may follow issuer, acquirer, platform, or foreign-market settlement calendars.

Examples include:

- UnionPay China;
- WeChat Pay China;
- foreign-issued credit cards;
- other offshore payment methods introduced later.

China holidays, including longer May and October holiday periods, may affect settlement timing. Calendar rules must be configurable by PSP/acquirer, payment method, issuer/platform, currency, rail, and jurisdiction where applicable.

Detailed calendar data structures belong in DOC-18.

---

## 9. Split Payment and Payout Aggregation

Multi-card funding may create multiple payment attempts or settlement records for one invoice, fee, rent, or obligation.

Backend and data handling must preserve the full split-payment structure while allowing payee payout to be grouped.

Core rule:

```text
PayPlus may aggregate payout to the payee, but must not collapse or overwrite the underlying split-payment funding records.
```

### 9.1 Same-Business-Day Grouping

Any split payment or multiple payments from the same payer for the same invoice, fee, rent, or obligation within the same business day before the 23:00 cutoff should normally be grouped into one payout to the payee where operationally permitted.

Rules:

- grouping applies to payout items, not to underlying payment records;
- individual card allocations and payment attempts must remain traceable;
- payments after cutoff belong to next business day grouping;
- grouping must respect risk holds, dispute holds, payout destination status, and settlement status;
- grouped payout must still reconcile to each source payment.

### 9.2 Required Traceability

The system must preserve links between:

- authoritative Bill/Rent source and applicable Payment Obligation;
- payer;
- payee;
- each card funding allocation;
- each payment attempt;
- each settlement record;
- aggregated payout item;
- payout batch;
- bank result record;
- reconciliation match.

Detailed data model belongs in DOC-18.

### 9.3 Payout from an Incomplete Checkout

If an incomplete DOC-09 Checkout Workspace has already produced one or more confirmed Payments, each eligible confirmed Payment may be evaluated for Settlement and Payout without marking the Checkout Target as fully funded.

Rules:

- payout applies only to confirmed Payments that satisfy DOC-10 Settlement and Payout rules; where a controlled DOC-09 late-confirmed Payment temporarily has zero Applications, it must not be treated as ordinarily Payout-ready and remains subject to the applicable owner-controlled Settlement, reconciliation, or adjustment treatment;
- unconfirmed or unexecuted Funding Legs remain outside the payout amount;
- payout item and payout batch must show that the payout is partial where applicable;
- payee-facing wording must not imply the Payment Obligation is Fully Paid when Effective Coverage remains below Due Amount;
- payer-facing receipt/history must distinguish confirmed Payment amount, paid-out amount, and obligation Outstanding Amount;
- reconciliation must link each payout to its confirmed Payment, originating Funding Leg and Checkout Workspace, any existing applicable Payment Applications, settlement record, Payer, economic Payee, and destination snapshot without requiring a retired Request object or a Payment Instruction.

---

## 10. Payout Batch Processing

Normal non-red-flag payouts should support batch processing.

### 10.1 Batch Creation

A payout batch may contain one or more payout items that are ready for payout.

Batch rules:

- include only payout-ready items;
- exclude held, red-flag, incomplete, returned, manually blocked, or applicable linked-dispute-case/hold items;
- group eligible same-business-day payments for the same payer/payee/obligation where permitted;
- assign stable batch ID and payout item IDs;
- prevent duplicate inclusion of the same payout item;
- record creator, creation time, cutoff basis, rail, amount, and status.

### 10.2 Bank File and API Options

PayPlus should support:

- generating a batch file for bank upload;
- manual upload to bank portal where API is unavailable;
- future direct bank API submission where supported;
- preserving bank reference or API response for each item.

Detailed file formats, API endpoints, authentication, SFTP, bank portal process, and provider behavior belong in DOC-17.

Owner-permitted upload, review, and workflow execution belongs in DOC-22.

### 10.3 Partial Batch Success

Batch status and item status must be separate.

Some items in a batch may succeed while others fail, return, or remain pending.

Each payout item must have its own status, bank reference where available, reconciliation state, and exception state.

---

## 11. Payout Status Model

DOC-10 owns payout status meaning at product-rule level. Canonical schema belongs in DOC-18.

| Status | Meaning |
| --- | --- |
| Payout Pending | Payout exists but is not yet ready or submitted. |
| Payout Ready | Readiness checks passed. |
| Payout Held | Payout blocked by risk, compliance, destination, refund, dispute, settlement, or manual hold. |
| Payout Batched | Payout item included in a batch. |
| Payout Submitted | Payout sent to bank, uploaded, or submitted through API. |
| Payout Processing | Bank or rail is processing payout. |
| Payout Completed | Successful payout confirmed by bank/feed/uploaded record. |
| Payout Failed | Payout failed before completion. |
| Payout Returned | Bank or recipient returned payout after submission. |
| Payout Cancelled | Payout cancelled before successful completion. |
| Payout Exception | Payout requires manual review or reconciliation resolution. |

User-facing labels and notifications belong in DOC-07 and DOC-08.

---

## 12. Bank Record Ingestion

Reconciliation may use one or more bank or partner evidence sources.

Supported patterns should include:

- bank feed API;
- bank statement import;
- bank payout result file;
- manual upload of batch payout result;
- manual upload of bank record;
- PSP/acquirer settlement report;
- bank portal export.

Where API or automated feed is unavailable, owner-permitted manual upload and review workflow may be executed under DOC-22. DOC-10 does not define its screens, queues, permissions, or dispositions.

Integration formats, API behavior, file validation, and provider-specific rules belong in DOC-17.

Data model and matching records belong in DOC-18.

---

## 13. Reconciliation Matching Rules

PayPlus must recognize successful individual payouts from bank feeds or uploaded records.

Matching may use:

- payout batch ID;
- payout item ID;
- bank reference;
- amount;
- payee name or payee identifier;
- payout destination;
- payout rail;
- value date;
- processing date;
- bank status;
- authoritative source, Payment Obligation, and Payment reference where available.

### 13.1 Matching Outcomes

| Outcome | Rule |
| --- | --- |
| Auto-matched | Matching confidence is high and required fields align. |
| Manually matched | An owner-permitted workflow records the match with required reason and Evidence. |
| Unmatched | No reliable payout item or bank record match exists. |
| Ambiguous | Multiple possible matches or incomplete evidence. |
| Mismatched | Amount, payee, destination, date, rail, or reference conflicts. |
| Duplicate | Same bank record or payout item appears more than once. |

Auto-match thresholds and matching keys must be configurable. Detailed matching data model belongs in DOC-18.

---

## 14. Reconciliation Process

Daily reconciliation is required for MVP operations.

DOC-10 reconciliation should match:

- PSP/acquirer settlement evidence;
- payment records;
- fee and adjustment records;
- payout items;
- payout batches;
- bank/API/uploaded payout result records;
- internal ledger/reporting records.

Reconciliation should identify:

- settled but not payout-ready items;
- payout-ready but not submitted items;
- submitted but not confirmed items;
- completed but not reconciled items;
- failed or returned payouts;
- duplicated bank records;
- amount mismatches;
- payee or destination mismatches;
- stale pending items.

Ledger schema belongs in DOC-18. Accounting treatment and revenue recognition policy are not defined in DOC-10.

---

## 15. Exception Handling

Payout exceptions include:

- failed payout;
- returned payout;
- delayed payout;
- missing bank result;
- duplicate bank record;
- amount mismatch;
- payee mismatch;
- payout destination mismatch;
- partial batch success;
- stale pending payout;
- manual hold;
- payout submitted after cutoff unexpectedly;
- holiday/calendar mismatch.

Each exception must have:

- owner or queue;
- reason;
- status;
- evidence;
- resolution action;
- audit log;
- link to authoritative Bill/Rent source, Payment Obligation, Payment, payout item, batch, and bank record where available.

Operational escalation belongs in DOC-21; owner-permitted workflow execution belongs in DOC-22.

---

## 16. Idempotency and Duplicate Prevention

The payout system must prevent duplicate payout.

Rules:

- each payout item must have a stable unique ID;
- each payout batch must have a stable unique ID;
- bank file/API submission should include unique payout references where supported;
- retries must reuse or link to original payout item and idempotency key;
- a payout item must not be included in multiple active batches unless the prior attempt is cancelled, failed, returned, or explicitly superseded;
- manual override must require permission, reason, evidence, and audit log.

Detailed idempotency keys, constraints, and schema belong in DOC-18. API/file behavior belongs in DOC-17.

---

## 17. Owner-Permitted Operational Execution

DOC-10 defines the Payout and reconciliation policy boundaries. Where an owner authorizes a manual, exception, hold, release, retry, cancellation, matching, or correction workflow, DOC-22 may execute that specific workflow with the owner-required reason, Evidence, permission, and audit treatment. DOC-22 does not independently decide payout policy, financial truth, destination validity, risk disposition, or retention.

Access to Payout destination, bank account, FPS, cheque, EPS, Payout batch, bank-feed, reconciliation, and economic-Payee-sensitive records must follow DOC-15 classification, masking, approved-purpose access, retention, export-control, and audit requirements. Detailed screens, queues, permissions, workflow, and audit representation remain with DOC-22 and DOC-18.

---

## 18. Accounting and Finance Boundary

DOC-10 requires reconciliation evidence but does not define final accounting treatment.

Finance and accounting review must determine:

- revenue recognition;
- fee recognition;
- refund and chargeback accounting;
- payout payable treatment;
- reserves and holdbacks;
- suspense or clearing account treatment;
- tax reporting implications.
- promotion, reward, voucher, miles, partner reimbursement, or campaign-funded benefit accounting where applicable.

DOC-18 should define ledger and reporting fields. Finance policy should define accounting conclusions.

---

## 19. Metrics and Reporting

DOC-10 should support reporting for:

- payout volume;
- payout value;
- payout success rate;
- payout failure rate;
- payout return rate;
- payout delay rate;
- average settlement-to-payout time;
- payout aging;
- unreconciled settlement amount;
- reconciliation break count;
- partial batch success count;
- manual override count.
- promotion-funded payout adjustment or partner reimbursement exception count where applicable.

Useful dimensions include:

- payout rail;
- payee type;
- category;
- controlled Bill/Rent source acquisition context;
- PSP/acquirer;
- bank account;
- business day;
- risk status;
- payout status;
- reconciliation status.
- campaign, offer, or reward identifier where promotion settlement or partner reimbursement is involved.

Detailed reporting schema belongs in DOC-18.

---

## 20. Event and Notification Boundary

DOC-10 emits payout and reconciliation events.

DOC-08 determines whether and how users or admins are notified.

Examples:

| Event | Notification Handling |
| --- | --- |
| Payout Ready | Internal owner context; DOC-10 does not define a user-facing notification. |
| Payout Completed | DOC-08 determines whether a permitted communication is created; this does not create a Payee User or notification entitlement. |
| Payout Failed | Owner workflow may be required; DOC-08 determines any permitted communication. |
| Payout Held | Owner workflow may be required; DOC-08 determines any permitted communication. |
| Reconciliation Break | Internal owner context. |

### 20.1 HOME-ROOT Recent Activity Payout Projection

DOC-10 publishes each canonical completed `Payout Complete` outcome for consumption by the DOC-06B HOME-ROOT Recent Activity contract. Each outcome supplies its canonical outcome identity, canonical ordering timestamp, canonical amount, and canonical funds-flow direction.

Settlement, batch, bank-ingestion, reconciliation, retry, intermediate, failure, and supporting events are not completed Payout outcomes merely because they support one.

DOC-10 does not create a cross-domain activity model. DOC-06B is the sole normative owner of Home eligibility, cap, ordering, cross-domain consumption, deduplication, presentation, navigation, entry, and return behavior. DOC-07 owns user-facing expression; DOC-18 remains the future owner of physical fields, event/status taxonomy, lineage, and audit representation.

---

## 21. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-10-001 | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Finance | Open |
| OQ-10-002 | What exact bank cutoff, PSP/acquirer cutoff, and timezone rules apply? | Payments / Engineering | Open |
| OQ-10-003 | What Hong Kong and foreign/offshore settlement calendars must be configured at launch? | Payments / Finance | Open |
| OQ-10-004 | What bank file format or API integration will be used for payout batch submission? | Engineering / Payments | Open |
| OQ-10-005 | What bank feed, result file, or manual upload format will confirm individual payout success? | Engineering / Finance | Open |
| OQ-10-006 | What auto-match confidence threshold and matching keys are approved? | Finance / Engineering | Open |
| OQ-10-007 | What payout hold rules apply for refund, dispute, chargeback, risk, destination change, and payee verification? | Risk / Operations / Payments | Open |
| OQ-10-008 | What cutoff rules apply to same-business-day grouping for split payments across foreign/offshore payment methods? | Payments / Engineering | Open |
| OQ-10-009 | What owner-permitted DOC-22 workflow, permissions, and audit requirements are required for exceptional Payout and reconciliation handling? | Operations / Security / Payments | Open |
| OQ-10-010 | What finance/accounting policy applies to payout payable, settlement clearing, reserves, and reconciliation breaks? | Finance | Open |
| OQ-10-011 | Which partner-funded promotions, external vouchers, miles rewards, or campaign reimbursements require reconciliation against payout, settlement, or partner records? | Finance / Growth / Payments | Open |
| OQ-10-012 | What payout, accounting, and payee-facing wording should apply when an incomplete DOC-09 Checkout Workspace has produced confirmed Payments but the Checkout Target remains partly unfunded? | Payments / Finance / Product | Open |
| OQ-10-013 | What owner-governed intended-Payee/destination matching, external validation capability, proof, review, and failure-treatment requirements apply at launch? This is not a Consumer Receiving Info library or Payee-user runtime question. | Payments / Risk / Compliance / Operations / Security | Open |

---

## 22. Acceptance Criteria

DOC-10 is acceptable when:

- payout readiness rules are clear;
- payout destination controls are defined;
- FPS, cheque, EPS, batch upload, and future bank API paths are acknowledged;
- cutoff, business day, Hong Kong holiday, and foreign/offshore calendar rules are defined at business-rule level;
- same-business-day split-payment grouping is defined without losing item-level traceability;
- payout from confirmed Payments is defined without treating the originating Checkout Workspace as fully funded;
- a confirmed Payment with zero or insufficient Payment Applications is not ordinary Payout-ready; payout amount and readiness do not derive from unapplied or excess adjustment value, and any owner-controlled downstream resolution preserves the no-fabricated-coverage boundary;
- payout batching and partial batch success rules are defined;
- bank record ingestion and manual upload requirements are defined;
- successful individual payout matching rules are defined;
- reconciliation process and exceptions are clear;
- idempotency and duplicate prevention are required;
- owner-permitted operational-execution boundary is explicit;
- detailed integration, privacy, data model, and workflow ownership is clearly assigned to DOC-15, DOC-17, DOC-18, and DOC-22.
- promotion-related reimbursement or reward settlement exceptions are routed to DOC-13, DOC-18, and DOC-22 where applicable.
- DOC-10 publishes canonical Payout Complete outcomes with their ordering timestamp, amount, and funds-flow direction for the DOC-06B HOME-ROOT handoff; supporting events remain separate non-outcomes, and DOC-06B owns Home eligibility, ordering, deduplication, sign presentation, navigation, and return behavior.

---

## 23. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.8.2 | 2026-08-13 | Regularized the zero- or insufficient-Payment-Application Payout criterion and its owner-controlled reconciliation/exception boundary; preserved the confirmed Payment, no-fabricated-coverage and no-bypass rules. |
| 0.8.1 | 2026-08-12 | Corrected Payout readiness and incomplete-Checkout wording for the DOC-09 controlled late-confirmation zero-Application exception while preserving Payment validity and owner-controlled Settlement, reconciliation, and adjustment boundaries. |
| 0.8.0 | 2026-08-12 | Replaced active Request, linked-user, and Consumer Receiving Info payout semantics with the Payer-only economic-Payee, controlled source, Evidence-to-Payee, immutable authorization-time destination snapshot, owner-permitted execution, and non-erasure boundaries. |
| 0.7.5 | 2026-08-05 | Added the bounded HOME-ROOT Recent Activity Payout handoff by publishing canonical Payout Complete outcome identity, ordering timestamp, amount, and funds-flow direction while retaining Home eligibility, ordering, deduplication, presentation, navigation, and return behavior in DOC-06B. |
| 0.7.4 | 2026-07-31 | Aligned the DOC-09 handoff to confirmed Payments and destination facts, removed Checkout-completion and Payment-Instruction payout coupling, and preserved DOC-10 Settlement/Payout ownership. |
| 0.7.3 | 2026-07-26 | Confirmed payout and reconciliation blockers for obligation archive/restore and preserved payout, destination, and completed-history snapshots across personal archive visibility changes. |
| 0.7.2 | 2026-07-26 | Replaced ambiguous request-status payout gating with the canonical payee-created request lifecycle and separate linked-case/hold controls, while preserving payer-created no-request payment. |
| 0.7.1 | 2026-07-26 | Required passcode or approved reauthentication for full Receiving Info reveal and add/edit while retaining confirmation for archive and stronger risk/provider step-up where applicable. |
| 0.7.0 | 2026-07-23 | Replaced the singular payout-destination model with multiple optional Receiving Info profiles, readiness and proof rules, versioned context snapshots, payee-request and payer-change behavior, linked-payee notifications, destination-attributable failure treatment, and authorization-time destination freeze. |
| 0.6.0 | 2026-07-22 | Added the DOC-06B `ME-ROOT` handoff to `RECEIVING-DETAILS`, clarified its payout-configuration purpose and mixed-role availability, and kept payer/payee transaction history in `ACTIVITY-ROOT`. |
| 0.1.0 | 2026-05-30 | Initial founder working baseline for payout readiness, payout rails, settlement calendars, split-payment grouping, payout batching, bank record ingestion, reconciliation matching, exceptions, idempotency, admin controls, and reporting. |
| 0.2.0 | 2026-05-30 | Aligned payout wording with updated DOC-01 settlement, fee, and approved payout positioning. |
| 0.3.0 | 2026-06-01 | Aligned payout and reconciliation boundaries with DOC-13 by adding promotion-funded adjustment, partner reimbursement, external voucher, and miles reward reconciliation references where applicable. |
| 0.4.0 | 2026-06-02 | Aligned payout, bank-record, reconciliation, export, and admin access handling with DOC-15 privacy classification and masking requirements. |
| 0.5.0 | 2026-06-02 | Aligned payout and reconciliation with DOC-09 user payment instruction by adding selected transfer date, partial funded portion payout, partial payout traceability, and remaining unpaid amount boundaries. |
