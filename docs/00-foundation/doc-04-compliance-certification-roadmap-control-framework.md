---
document_id: DOC-04
title: Compliance Control Framework
version: 0.13.4
status: Founder Working Baseline
owner: Compliance Lead
reviewers:
  - Legal Lead
  - Risk Lead
  - Security Lead
  - Privacy Lead
  - Payments Lead
  - Product Lead
  - Engineering Lead
  - Operations Lead
  - Finance Lead
approvers:
  - Project Owner
  - Legal Lead
  - Compliance Lead
  - Security Lead
  - Risk Lead
  - Payments Lead
  - Finance Lead
last_updated: 2026-08-13
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory Assessment
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Communication
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-16 Technical Architecture
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT, Release & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-04 - Compliance Control Framework

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-04` |
| **Title** | Compliance Control Framework |
| **Version** | `0.13.4` |
| **Status** | Founder Working Baseline |
| **Owner** | Compliance Lead |
| **Reviewers** | Legal Lead<br>Risk Lead<br>Security Lead<br>Privacy Lead<br>Payments Lead<br>Product Lead<br>Engineering Lead<br>Operations Lead<br>Finance Lead |
| **Approvers** | Project Owner<br>Legal Lead<br>Compliance Lead<br>Security Lead<br>Risk Lead<br>Payments Lead<br>Finance Lead |
| **Last Updated** | `2026-08-13` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Project Charter & Product Positioning<br>DOC-02 Business Model & Unit Economics<br>DOC-03 Regulatory Assessment<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Communication<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-16 Technical Architecture<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT, Release & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines the compliance control framework for PayPlus.

It translates PayPlus legal, regulatory, PSP/acquirer, payout, AML, sanctions, fraud, consumer protection, privacy, security, finance, reconciliation, and operational requirements into testable controls.

This document determines:

- what controls must exist before launch;
- which controls block launch if missing;
- what evidence must be retained;
- who owns each control;
- what must be tested;
- what must be monitored after launch.

This document applies to Payer-created controlled Bill sources and the separate Rent journey; authoritative source preservation and Evidence outcomes; payment authorization, Payout, adjustment and reconciliation controls; and owner-governed risk, privacy, security, operations and launch evidence. A Consumer User is a Payer. An economic Payee may be an individual or institution/company and need not be a User.

It does not authorize Request, Linking, To Receive, Receiving Info, Payee-user, reciprocal-visibility, production reader, adapter, fallback or legacy deep-link runtime. Any historical identifier remains documentation provenance only.

This document is not a legal opinion, final AML policy, PSP/acquirer approval, risk rulebook, product PRD, support SOP, or technical architecture.

---

## 2. Control Objectives

PayPlus controls must support the following objectives.

| Objective ID | Objective |
| --- | --- |
| `OBJ-DOC04-001` | Payments must be tied to an accepted controlled Bill source within the twelve accepted controlled Bill Categories or the separate Rent journey. |
| `OBJ-DOC04-002` | Payment contexts must reference authoritative Bill/Rent sources supported by applicable Evidence outcomes. |
| `OBJ-DOC04-003` | Payers must review and authorize payment before funding, capture, or payout. |
| `OBJ-DOC04-004` | No source, Evidence outcome, or Payment Instruction automatically triggers payment; Payer authorization remains required. |
| `OBJ-DOC04-005` | The intended economic Payee and effective destination must satisfy applicable verification and Payout conditions. |
| `OBJ-DOC04-006` | Prohibited and restricted categories must be blocked or routed to review. |
| `OBJ-DOC04-007` | Arbitrary P2P, self-payment, cashout, stored value, and wallet-like activity must be prevented. |
| `OBJ-DOC04-008` | Transaction limits, velocity rules, duplicate detection, and suspicious activity monitoring must be applied. |
| `OBJ-DOC04-009` | High-risk source, Evidence, transaction and Payout conditions must be routed to the applicable owner-governed review. |
| `OBJ-DOC04-010` | Source, payment, Evidence, authorization, Payout, adjustment and reconciliation facts must be traceable under their formal owners. |
| `OBJ-DOC04-011` | Payouts must be gated by payment status, payee status, risk status, and payout provider readiness. |
| `OBJ-DOC04-012` | Privacy, security, PCI, access, and data visibility controls must protect payer and payee information. |
| `OBJ-DOC04-013` | Compliance-critical controls must be tested before launch and monitored after launch. |

---

## 3. Control Categories

PayPlus controls are grouped into the following categories.

| Category ID | Category | Primary Owner | Related Documents |
| --- | --- | --- | --- |
| `CAT-DOC04-001` | User controls | Product / Compliance | DOC-06, DOC-15 |
| `CAT-DOC04-002` | Evidence controls | Product / Compliance / Risk | DOC-12, DOC-18 |
| `CAT-DOC04-003` | Payment authorization controls | Product / Payments / Engineering | DOC-07, DOC-09 |
| `CAT-DOC04-004` | Payee verification controls | Compliance / Risk / Operations | DOC-12, DOC-14 |
| `CAT-DOC04-005` | Transaction monitoring controls | Risk / Compliance | DOC-14, DOC-21 |
| `CAT-DOC04-006` | Admin review controls | Operations / Risk / Compliance | DOC-14, DOC-21, DOC-22 |
| `CAT-DOC04-007` | Audit and recordkeeping controls | Compliance / Finance / Engineering | DOC-15, DOC-18 |
| `CAT-DOC04-008` | Prohibited activity controls | Compliance / Risk / Product | DOC-03, DOC-14 |
| `CAT-DOC04-009` | Payout controls | Payments / Finance / Risk | DOC-10, DOC-18 |
| `CAT-DOC04-010` | Refund, dispute, and chargeback controls | Operations / Payments | DOC-11 |
| `CAT-DOC04-011` | Privacy and security controls | Privacy / Security / Engineering | DOC-15, DOC-19 |
| `CAT-DOC04-012` | Partner and launch readiness controls | Compliance / Payments / Legal | DOC-03, DOC-20 |

---

## 4. Control Tiers

Controls are classified by launch impact.

| Tier | Meaning | Launch Impact |
| --- | --- | --- |
| `T0` | Non-waivable launch blocker. | Cannot launch without completion. |
| `T1` | Critical launch control. | Blocks launch unless formally risk-accepted with mitigation. |
| `T2` | Important operating control. | May launch with approved remediation plan. |
| `T3` | Scale or maturity control. | Required before scale, expansion, or audit maturity. |

Controls marked `if enabled` apply only when the related feature is enabled.

Examples:

- `T1 if bill or fee category enabled`
- `T1 if rent enabled`
- `T1 if multi-source enabled`

The twelve accepted controlled Bill Categories and separate Rent journey are the only Wave 4 inventory boundary. Category-specific eligibility, Evidence criteria, labels, Directory contents, partner acceptance and commercial viability remain owner-governed. Conditional wording does not create a new Category, economic Payee capability, route or payment path.

---

## 5. User Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-USER-001` | `T0` | Capture required user identity, contact, eligibility, terms acceptance, and privacy acknowledgement before payment. | Product / Compliance | User profile, consent logs |
| `CTRL-DOC04-USER-002` | `T0` | Display required payment disclosures before payer authorization. | Product / Legal | UI screenshots, disclosure logs |
| `CTRL-DOC04-USER-003` | `T0` | Capture disclosure version, acceptance timestamp, Payer ID, authoritative source reference where applicable, Payment ID, amount, fees, and total charge. | Product / Engineering | Authorization and consent logs |
| `CTRL-DOC04-USER-004` | `T1` | Apply user eligibility rules, blocked-user rules, and restricted-user handling. | Product / Compliance / Risk | Eligibility config, blocked-user logs |
| `CTRL-DOC04-USER-005` | `T1` | Prevent users from paying themselves or related accounts unless explicitly approved. | Risk / Engineering | Rule config, alert logs |
| `CTRL-DOC04-USER-006` | `T1` | Provide Payer access to payment, adjustment, support and owner-approved source visibility information. | Product / Operations | UI evidence, support logs |
| `CTRL-DOC04-USER-007` | `T1` | Present current material facts and owner-approved safe handling before Payer payment authorization. | Product / Operations | Authorization and support evidence |
| `CTRL-DOC04-USER-008` | `T0` | Prevent funding, capture and Payout unless the Payer has explicitly authorized the applicable payment. | Product / Payments / Engineering | Authorization logs, payment state logs |

---

## 6. Evidence Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-EVD-001` | `T0` | Require each payment context to reference an authoritative controlled Bill source or separate Rent source and applicable Evidence outcome. | Product / Compliance | Source and payment-context record |
| `CTRL-DOC04-EVD-002` | `T0` | Require uploaded, linked, captured, or system-generated Evidence for each applicable Payment Obligation arising from an accepted controlled Bill source or separate Rent source, unless an owner-governed exception applies. | Product / Compliance | Evidence record |
| `CTRL-DOC04-EVD-003` | `T1` | Store Evidence under the applicable source, Payer, economic-Payee context, Category or separate Rent, timestamp, source and review outcome. | Engineering / Compliance | Evidence metadata |
| `CTRL-DOC04-EVD-004` | `T1` | Prevent an owner-governed payment path from proceeding when its required Evidence outcome is unavailable. | Product / Engineering | Validation logs |
| `CTRL-DOC04-EVD-005` | `T1` | Detect duplicate Evidence, duplicate invoices, duplicate Rent sources or repeated source indicators where feasible. | Risk / Engineering | Duplicate detection alerts |
| `CTRL-DOC04-EVD-006` | `T1` | Route unclear, incomplete, suspicious, or high-risk evidence to admin review. | Risk / Operations | Review case logs |
| `CTRL-DOC04-EVD-007` | `T1` | Apply owner-governed Evidence criteria to the authoritative source; this framework does not define Category-specific criteria. | Product / Compliance / Risk | Evidence requirements matrix |
| `CTRL-DOC04-EVD-008` | `T1` | Require rent evidence, such as lease, rent schedule, property reference, tenancy confirmation, or approved equivalent. | Product / Compliance / Risk | Rent evidence record |
| `CTRL-DOC04-EVD-009` | `T1 if invoice enabled` | Require invoice evidence, business-payee details, service description, amount, due date, and payee identity information. | Product / Compliance / Risk | Invoice evidence record |

---

## 7. Payment Authorization Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-AUTH-001` | `T0` | Payer must authorize payment before funding, capture, or payout. | Product / Payments / Engineering | Authorization logs |
| `CTRL-DOC04-AUTH-002` | `T0` | Authorization must capture the Payer, amount, fee, total charge, economic-Payee/source context, timestamp, payment method, and applicable disclosure version. | Product / Engineering | Authorization record |
| `CTRL-DOC04-AUTH-003` | `T0` | Payment amount, fees, and total charge must not change after authorization unless payer re-authorizes. | Product / Payments / Engineering | Change logs, authorization logs |
| `CTRL-DOC04-AUTH-004` | `T1` | Authorization, capture, reversal, cancellation, refund and chargeback facts must retain applicable source, Payment and owner-governed lineage. | Payments / Engineering / Finance | Transaction ledger |
| `CTRL-DOC04-AUTH-005` | `T1` | Failed or expired authorizations must not result in payout. | Payments / Engineering | Payment state logs |
| `CTRL-DOC04-AUTH-006` | `T1` | Payer must receive an authorization confirmation after successful authorization and a receipt after completed payment. | Product / Operations | Authorization confirmation and receipt logs |
| `CTRL-DOC04-AUTH-007` | `T1` | Source establishment, Evidence verification and Payment authorization remain distinct owner-governed outcomes; retired Request states have no active control meaning. | Product / Engineering | Applicable owner records |
| `CTRL-DOC04-AUTH-008` | `T0` | Payment authorization is the Payer's separate funding authorization and is not replaced by source establishment or Evidence review. | Product / Legal / Engineering | Authorization record |
| `CTRL-DOC04-AUTH-009` | `T1` | A material payment-relevant source or destination fact must be revalidated and freshly authorized as required by the applicable owners. | Product / Engineering | Owner-governed revalidation evidence |
| `CTRL-DOC04-AUTH-010` | `T1 if payment instruction enabled` | A deferred user payment instruction must not be treated as card authorization, capture, settlement, payout readiness, or completed payment until the relevant funding leg is submitted and confirmed. | Product / Payments / Engineering | Payment instruction and funding-leg logs |
| `CTRL-DOC04-AUTH-011` | `T1 if payment instruction enabled` | Returning to a deferred payment instruction must revalidate material payment terms, including amount, fee, promotion quote, card eligibility, timing, and required disclosures before funding submission. | Product / Payments / Growth / Engineering | Quote revalidation and user confirmation logs |

---

## 8. Payee Verification Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-PAYEE-001` | `T1` | Verify payee identity, business identity, payout destination, and eligibility before payout where required. | Compliance / Risk / Operations | Payee verification record |
| `CTRL-DOC04-PAYEE-002` | `T0` | Verify intended-Payee and effective-destination eligibility before Payout where required. | Compliance / Risk / Product | Applicable owner evidence |
| `CTRL-DOC04-PAYEE-003` | `T1` | Screen payees against applicable sanctions or blocked-party lists where required. | Compliance | Screening logs |
| `CTRL-DOC04-PAYEE-004` | `T1` | Apply owner-governed intended-Payee, Category, destination and Payout outcomes without granting a Payee-user capability. | Product / Risk / Compliance | Applicable owner evidence |
| `CTRL-DOC04-PAYEE-005` | `T1` | Block restricted, rejected, suspended, or unverified payees from payout. | Product / Payments / Engineering | Payout block logs |
| `CTRL-DOC04-PAYEE-006` | `T1` | Retired payee-created Request capability must not be available in the active MVP. | Product / Engineering | Product-scope evidence |
| `CTRL-DOC04-PAYEE-007` | `T1` | Review payout destination changes before allowing payout to the new destination where risk requires. | Operations / Risk / Payments | Change review logs |
| `CTRL-DOC04-PAYEE-008` | `T1` | For separate Rent, verify applicable property/tenancy source context and effective destination where required. | Compliance / Risk / Operations | Owner-governed verification record |
| `CTRL-DOC04-PAYEE-009` | `T1 if invoice enabled` | Verify business-payee identity, business status, invoice legitimacy indicators, and payout destination where required. | Compliance / Risk / Operations | Business payee verification record |
| `CTRL-DOC04-PAYEE-010` | `T1` | Offboard or suspend payees with confirmed fraud, sanctions issues, excessive disputes, unsupported categories, or partner violations. | Compliance / Risk / Operations | Offboarding logs |

---

## 9. Transaction Monitoring Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-MON-001` | `T0` | Apply baseline transaction limits before launch. | Risk / Product | Limit config |
| `CTRL-DOC04-MON-002` | `T0` | Apply velocity limits for Payers, cards, intended-Payee/destination context, failed authorizations and Payouts where applicable. | Risk / Engineering | Rule config |
| `CTRL-DOC04-MON-003` | `T1` | Monitor failed authorizations, repeated attempts, suspicious refunds, chargebacks, payout failures, and account changes. | Risk / Operations | Monitoring reports |
| `CTRL-DOC04-MON-004` | `T1` | Monitor duplicate Bills, invoices, Rent source indicators and repeated Evidence. | Risk / Engineering | Duplicate alerts |
| `CTRL-DOC04-MON-005` | `T1` | Monitor source-context concentration, circular activity and related-party indicators without creating a Payer-Payee relationship runtime. | Risk / Compliance | Risk indicators |
| `CTRL-DOC04-MON-006` | `T1` | Monitor restricted categories, high-risk MCC/classification issues, suspicious payees, and unsupported activity. | Risk / Compliance | Monitoring reports |
| `CTRL-DOC04-MON-007` | `T1` | Retired Request metrics and lifecycle monitoring have no active control meaning. | Risk / Operations | Scope evidence |
| `CTRL-DOC04-MON-008` | `T1` | Monitor fake obligation, inflated amount, duplicate-source, collusion and self-payment indicators. | Risk / Compliance | Alerts, case logs |
| `CTRL-DOC04-MON-009` | `T1 if Rent enabled` | Monitor Rent source reasonableness, duplicates, property reuse and risk indicators where required. | Risk / Compliance | Rent monitoring report |
| `CTRL-DOC04-MON-010` | `T1` | Escalate suspicious activity to Compliance, Risk, Legal, or partner contacts according to severity. | Risk / Compliance / Operations | Escalation logs |

---

## 10. Admin Review Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-ADM-001` | `T1` | The applicable owner defines any review requirement; DOC-22 may execute only a specifically owner-permitted workflow. | Operations / Risk | Owner-governed review evidence |
| `CTRL-DOC04-ADM-002` | `T1` | Risk, Compliance and specialist owners define any applicable review triggers. | Risk / Compliance | Owner-governed control evidence |
| `CTRL-DOC04-ADM-003` | `T1` | Review truth, outcomes and audit requirements remain with their formal owners; DOC-18 will represent approved requirements. | Operations / Risk | Applicable owner records |
| `CTRL-DOC04-ADM-004` | `T1` | This framework grants no generic Admin disposition authority. | Operations / Product | Owner-permitted workflow evidence |
| `CTRL-DOC04-ADM-005` | `T1` | Security owns access-control policy; owner-permitted execution follows least-privilege requirements. | Security / Engineering | Applicable security evidence |
| `CTRL-DOC04-ADM-006` | `T1` | Applicable owners determine audit facts; DOC-22 must not rewrite them. | Engineering / Security | Applicable audit evidence |
| `CTRL-DOC04-ADM-007` | `T1` | Retired payee-created Requests have no active review path. | Risk / Operations | Scope evidence |
| `CTRL-DOC04-ADM-008` | `T1 if Rent enabled` | Risk and specialist owners determine whether a Rent source/destination review is required. | Risk / Operations | Owner-governed review evidence |

---

## 11. Audit and Recordkeeping Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-AUD-001` | `T0` | Maintain a launch certification evidence package before MVP launch. | Compliance | Launch package |
| `CTRL-DOC04-AUD-002` | `T0` | Retain source, Evidence, disclosure, authorization, Payment, Payout, adjustment, dispute, chargeback and reconciliation records under their formal owners. | Compliance / Engineering / Finance | Records inventory |
| `CTRL-DOC04-AUD-003` | `T1` | Maintain immutable or tamper-evident audit logs for compliance-critical actions. | Engineering / Security | Audit logs |
| `CTRL-DOC04-AUD-004` | `T1` | Preserve applicable source, Evidence, Payer authorization, Payment, Payout, adjustment, dispute, chargeback and ledger lineage. | Engineering / Finance | Ledger linkage |
| `CTRL-DOC04-AUD-005` | `T1` | Represent approved source context, economic-Payee type, Category or Rent, and owner-governed outcomes only when DOC-18 is authorized. | Engineering / Product | Future representation requirements |
| `CTRL-DOC04-AUD-006` | `T1` | Maintain controls for indefinite retention and approved-purpose access, masking, legal hold and correction handling for compliance, privacy, tax, finance, partner, and dispute records; no time- or purpose-triggered destruction is implied. | Privacy / Compliance / Legal | Retention and access controls |
| `CTRL-DOC04-AUD-007` | `T1` | Store dispute and chargeback evidence in a retrievable evidence package. | Operations / Payments | Dispute evidence package |
| `CTRL-DOC04-AUD-008` | `T1` | Maintain daily reconciliation evidence for settlement, fees, payouts, refunds, chargebacks, reserves, bank records, and ledger entries. | Finance / Payments | Reconciliation reports |
| `CTRL-DOC04-AUD-009` | `T1` | Retired Request origin has no active audit requirement; append-only documentation history remains provenance only. | Compliance / Engineering / Operations | Documentation history |
| `CTRL-DOC04-AUD-010` | `T1` | Retain risk review, manual review, sanctions review, and suspicious activity escalation records. | Risk / Compliance | Case records |

---

## 12. Prohibited Activity Controls

PayPlus must prevent or restrict activity that could undermine the product's evidence-backed, payer-authorized accepted controlled Bill/Rent Payment Obligation model.

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-PROH-001` | `T0` | Block wallet, stored balance, preload, user-controlled stored value, and cashout functionality unless separately approved. | Product / Legal / Compliance | Product configuration |
| `CTRL-DOC04-PROH-002` | `T0` | Block arbitrary P2P transfers unrelated to an accepted controlled Bill or separate Rent source. | Product / Compliance | Category/source validation |
| `CTRL-DOC04-PROH-003` | `T0` | Block prohibited Categories before applicable payment authorization. | Product / Compliance | Category config |
| `CTRL-DOC04-PROH-004` | `T1` | Route restricted categories to enhanced review or block them according to approved rules. | Product / Risk / Compliance | Review logs |
| `CTRL-DOC04-PROH-005` | `T1` | Block or escalate self-payment, circular payment, related-party abuse, and collusive payment patterns. | Risk / Compliance | Alerts, case logs |
| `CTRL-DOC04-PROH-006` | `T1` | Block cash-equivalent, gift card, crypto, gambling, investment, and other restricted use cases unless explicitly approved. | Product / Compliance | Category rules |
| `CTRL-DOC04-PROH-007` | `T1` | Prevent unsupported, unverifiable or misleading source facts from creating an applicable payment path. | Product / Risk / Compliance | Applicable owner evidence |
| `CTRL-DOC04-PROH-008` | `T1` | Retired payee-created Requests must not imply payment, validation or automatic charge. | Product / Legal | Scope evidence |
| `CTRL-DOC04-PROH-009` | `T1 if Rent enabled` | Block unsupported Rent source/destination payment paths unless applicable verification and risk controls are enabled. | Product / Compliance / Risk | Owner-governed control evidence |
| `CTRL-DOC04-PROH-010` | `T1` | Suspend users or payees associated with confirmed prohibited activity. | Compliance / Risk / Operations | Suspension logs |

---

## 13. Payout Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-POUT-001` | `T0` | Operating-bank payout setup, approved payout rails, settlement timing, liquidity treatment, and payout exception handling must be approved before production payout. | Payments / Finance | Payout approval record |
| `CTRL-DOC04-POUT-002` | `T0` | Payout must be blocked unless payment status, payee status, risk status, and payout destination status are eligible. | Payments / Risk / Engineering | Payout gating logs |
| `CTRL-DOC04-POUT-003` | `T1` | Payout readiness must check authorization success, capture status, settlement status where required, refund status, dispute status, risk hold status, and reserve requirements. | Payments / Finance / Risk | Payout readiness record |
| `CTRL-DOC04-POUT-004` | `T1` | Failed, returned, delayed, rejected, or misdirected payouts must create an exception case. | Payments / Operations | Payout exception log |
| `CTRL-DOC04-POUT-005` | `T1` | Payout destination changes must be logged and reviewed according to risk level. | Operations / Risk / Payments | Destination change logs |
| `CTRL-DOC04-POUT-006` | `T1` | Reserves, holdbacks, prefunding, collateral, and liquidity impacts must be reviewed where applicable. | Finance / Payments | Reserve review |
| `CTRL-DOC04-POUT-007` | `T0` | Payout must be blocked unless the applicable Payment is confirmed and has valid applicable Payment Application lineage sufficient for the payout value being treated, or an explicit authoritative owner-controlled resolution covers a zero- or insufficient-Application case. A confirmed Payment with zero or insufficient valid Applications is not ordinary Payout-ready; unapplied or excess adjustment value must not create payout readiness, fictional coverage, or a bypass of the applicable DOC-09/DOC-10/DOC-11 reconciliation or exception boundary. | Payments / Risk / Engineering | Payout gate evidence |
| `CTRL-DOC04-POUT-008` | `T1 if rent enabled` | Rent payouts must be subject to landlord verification, tenancy evidence, duplicate detection, payout destination controls, and risk review where required. | Payments / Risk / Operations | Rent payout review |

---

## 14. Refund, Dispute, and Chargeback Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-RDC-001` | `T1` | Maintain refund rules covering eligibility, timing, amount, fees, payout status, and ledger treatment. | Operations / Payments / Finance | Refund policy, refund logs |
| `CTRL-DOC04-RDC-002` | `T1` | Link refunds to applicable source, authorization, Payment, fee, Payout and ledger entries. | Payments / Engineering / Finance | Refund ledger |
| `CTRL-DOC04-RDC-003` | `T1` | Maintain cancellation rules before payment, after authorization, before payout, and after payout. | Operations / Product / Payments | Cancellation logs |
| `CTRL-DOC04-RDC-004` | `T1` | Track payer disputes, payee disputes, payer queries, complaints, and support escalations. | Operations | Case logs |
| `CTRL-DOC04-RDC-005` | `T1` | Track chargebacks, reason codes, deadlines, evidence, representment status, liability, and outcome. | Operations / Payments | Chargeback case |
| `CTRL-DOC04-RDC-006` | `T1` | Maintain chargeback Evidence under the applicable source, authorization, disclosure, communication, Payment and Payout owners. | Operations / Payments / Compliance | Chargeback evidence package |
| `CTRL-DOC04-RDC-007` | `T1` | Adjustment/case handling is owned by DOC-11 and does not reinstate retired Request lifecycle behavior. | Product / Operations | DOC-11 handoff |
| `CTRL-DOC04-RDC-008` | `T1` | A confirmed Payment is governed by applicable cancellation, refund or reversal rules; no Payee-user withdrawal action is defined. | Product / Payments / Operations | Applicable owner records |

---

## 15. Privacy and Security Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-SEC-001` | `T0` | PCI scope and card data handling model must be approved before production card processing. | Security | PCI scope document |
| `CTRL-DOC04-SEC-002` | `T0` | Sensitive card data must not be stored unless explicitly approved under PCI scope. | Security / Engineering | Architecture review |
| `CTRL-DOC04-SEC-003` | `T1` | Use tokenized card handling where applicable. | Security / Payments / Engineering | Tokenization evidence |
| `CTRL-DOC04-SEC-004` | `T1` | Encrypt sensitive data in transit and at rest. | Security / Engineering | Security review |
| `CTRL-DOC04-SEC-005` | `T1` | Restrict Admin, support, risk and engineering access by role; an economic Payee is not a PayPlus User role. | Security / Engineering | RBAC matrix |
| `CTRL-DOC04-SEC-006` | `T1` | Log approved-purpose access to sensitive Payer, source-context economic-Payee, Payment, Evidence, Payout and risk data. | Security / Engineering | Access logs |
| `CTRL-DOC04-SEC-007` | `T1` | Maintain privacy notice, consent records, data map, indefinite-retention requirements, approved-purpose access and correction/request handling; no time-triggered deletion process is implied. | Privacy / Legal / Product | Privacy records |
| `CTRL-DOC04-SEC-008` | `T1` | Enforce Payer and source-context economic-Payee approved-purpose visibility without reciprocal runtime. | Privacy / Security / Engineering | Visibility test evidence |
| `CTRL-DOC04-SEC-009` | `T1` | Limit Payer access to Evidence according to owner-approved disclosure and privacy rules. | Privacy / Product / Legal | Visibility rules |
| `CTRL-DOC04-SEC-010` | `T1` | Maintain incident severity levels, escalation contacts, and incident response procedure. | Security / Operations | Incident runbook |
| `CTRL-DOC04-SEC-011` | `T1` | Maintain DOC-15 data classification, approved-purpose, masking, retention, and access-control mapping for material objects and fields. | Privacy / Security / Engineering / Data | Data classification register |

---

## 16. Partner and Launch Readiness Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-LAUNCH-001` | `T0` | Launch scope must define Hong Kong requirements, the accepted controlled Categories and separate Rent, payment methods, Payout methods, partners and economic-Payee types. | Project Owner / Compliance | Launch scope record |
| `CTRL-DOC04-LAUNCH-002` | `T0` | Regulatory role and licensing path must be assessed before launch. | Legal / Compliance | DOC-03 assessment |
| `CTRL-DOC04-LAUNCH-003` | `T0` | PSP/acquirer support must be confirmed for use case, funds flow, accepted Category/separate Rent paths, fees and intended MCC/classification. | Payments / Legal | Partner confirmation |
| `CTRL-DOC04-LAUNCH-004` | `T0` | PayPlus operating bank setup and approved Hong Kong payout rails must be confirmed before production payout. | Payments / Legal | Partner confirmation |
| `CTRL-DOC04-LAUNCH-005` | `T0` | Fee model, total charge display, and required disclosures must be approved before launch. | Legal / Product / Finance | Approval record |
| `CTRL-DOC04-LAUNCH-006` | `T0` | Required T0 controls must be implemented, tested, and evidenced before launch. | Compliance / QA | Test evidence |
| `CTRL-DOC04-LAUNCH-007` | `T1` | T1 exceptions must be remediated or formally risk-accepted with mitigation and target date. | Compliance / Functional Owner | Exception log |
| `CTRL-DOC04-LAUNCH-008` | `T0` | Required approvers must sign launch certification for the defined scope. | Project Owner / Compliance | Approval log |
| `CTRL-DOC04-LAUNCH-009` | `T0` | Retired payee-created Request capability is not part of launch certification. | Legal / Compliance / Payments | Scope evidence |
| `CTRL-DOC04-LAUNCH-010` | `T0 if Rent enabled` | Separate Rent requires applicable owner-governed legal, verification and risk readiness. | Legal / Compliance / Risk | Rent readiness evidence |

---

## 17. Launch Blockers

PayPlus must not launch if any of the following are unresolved.

| Blocker ID | Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-001` | Regulatory role and licensing path are not assessed. | Legal / Compliance |
| `BLK-DOC04-002` | PSP/acquirer approval or equivalent confirmation is missing for the core payment flow. | Payments |
| `BLK-DOC04-003` | Payout provider and payout flow are not approved or tested. | Payments / Finance |
| `BLK-DOC04-004` | Approved, restricted, and prohibited categories are not defined or enforced. | Compliance / Product |
| `BLK-DOC04-005` | Fee, total charge, timing, refund/cancellation, and PayPlus role disclosures are not shown before authorization. | Legal / Product |
| `BLK-DOC04-006` | Payer authorization is not captured before funding, capture, or payout. | Product / Payments |
| `BLK-DOC04-007` | PCI scope and card data handling model are not approved before card processing. | Security |
| `BLK-DOC04-008` | Sanctions screening and escalation requirements are not implemented where required. | Compliance |
| `BLK-DOC04-009` | Baseline fraud, velocity, and anti-cashout controls are missing. | Risk |
| `BLK-DOC04-010` | Daily reconciliation process is not defined and tested. | Finance / Payments |
| `BLK-DOC04-011` | Refund, cancellation, payout failure, dispute, and chargeback handling are not defined. | Operations / Payments |
| `BLK-DOC04-012` | Privacy notice, terms acceptance, and consent controls are not implemented. | Privacy / Legal |
| `BLK-DOC04-013` | Critical evidence is not stored in an approved repository. | Compliance |
| `BLK-DOC04-014` | Required approvers have not signed launch certification. | Project Owner / Compliance |

The following retained blocker IDs describe the accepted Payer-only baseline; they do not create retired Request runtime.

| Blocker ID | Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-015` | The accepted Payer-created source model is not assessed through DOC-03. | Legal / Compliance / Payments |
| `BLK-DOC04-016` | Required intended-Payee/destination verification, sanctions or Payout controls are not enabled. | Compliance / Risk / Operations |
| `BLK-DOC04-017` | Funding or Payout can occur without applicable Payer authorization. | Product / Payments / Engineering |
| `BLK-DOC04-018` | Required source/Evidence outcomes are not available. | Product / Compliance / Risk |
| `BLK-DOC04-019` | Payout gating is not implemented for applicable Payments. | Payments / Risk / Finance |
| `BLK-DOC04-020` | Approved-purpose privacy boundaries and access controls are not implemented. | Privacy / Security |
| `BLK-DOC04-021` | Fake-source, self-payment, related-party or collusion controls are not implemented. | Risk / Compliance |
| `BLK-DOC04-022` | Separate Rent is enabled without required tenancy/source, destination, risk or legal readiness. | Legal / Compliance / Risk |
| `BLK-DOC04-023` | Support, complaint, adjustment and dispute procedures are not defined. | Operations / Legal / Product |

---

## 18. Control Testing

Compliance-critical controls must be tested before launch.

Required launch tests include:

- user eligibility and consent capture;
- fee and total amount display before authorization;
- disclosure version logging;
- prohibited category blocking;
- restricted category review routing;
- source/Evidence capture and applicable verification;
- missing evidence blocking;
- duplicate bill, invoice, or rent detection where applicable;
- payer authorization before funding, capture, or payout;
- deferred user payment instruction is not treated as authorization, capture, settlement, payout readiness, or completed payment before funding submission;
- returning to a deferred payment instruction revalidates payment quote, promotion quote, card eligibility, fee, timing, and required disclosures;
- material term lock after authorization;
- intended-Payee/destination verification before Payout where required;
- sanctions screening and escalation where required;
- transaction limits and velocity rules;
- self-payment detection;
- suspicious activity escalation;
- owner-governed review evidence and permitted-execution logging;
- payout eligibility and payout gating;
- payout failure handling;
- refund flow;
- dispute and chargeback tracking;
- chargeback evidence package retrieval;
- daily reconciliation;
- audit log generation;
- record retention mapping;
- PCI/card data handling controls;
- Payer/economic-Payee approved-purpose privacy controls;
- incident escalation.

For separate Rent, applicable tests include:

- landlord verification;
- tenancy evidence capture;
- rent amount reasonableness check where required;
- duplicate rent detection;
- source-context/risk assessment where required;
- payout destination change review;
- owner-governed Rent review evidence where required.

---

## 19. Evidence and Systems of Record

| Evidence Type | System of Record | Owner |
| --- | --- | --- |
| Launch certification | Compliance evidence repository | Compliance |
| Regulatory role assessment | Legal repository / compliance repository | Legal / Compliance |
| PSP/acquirer approval | Contract repository / partner folder | Payments / Legal |
| Payout provider approval | Contract repository / partner folder | Payments / Legal |
| Category approval | Compliance register / product configuration | Compliance / Product |
| Fee approval | Finance model / pricing configuration / approval ticket | Finance / Product |
| UI disclosure evidence | QA repository / screenshot archive | Product / Legal |
| Terms and privacy acceptance | Application database / audit log | Product / Engineering |
| User record | Application database | Product |
| Intended-Payee and destination verification | Applicable owner system of record | Compliance / Operations |
| Retired Payee-user capability | No active system of record; documentation provenance only | Product / Risk |
| Authoritative Bill/Rent source | Application database / applicable owner system | Product / Engineering |
| Bill/Rent Evidence | Evidence repository / document storage / application database | Product / Compliance / Risk |
| Payer response and authorization | Application database / audit log / payment platform | Product / Payments / Engineering |
| Payer-facing owner-governed communication | Notification system / support system | Operations / Product |
| Dispute, query, or complaint | Support system / case management tool | Operations |
| Sanctions screening | Screening tool / compliance case system | Compliance |
| Fraud and risk decision | Risk engine / case management tool | Risk / Operations |
| Manual review case | Admin console / case management tool | Risk / Operations |
| Settlement and payout reports | PSP/payout portal / reconciliation system | Finance / Payments |
| Ledger entry | Transaction ledger | Finance / Engineering |
| Refund record | Application ledger / PSP portal / operations case | Operations / Payments |
| Chargeback case | PSP portal / dispute case system | Operations / Payments |
| PCI evidence | Security repository | Security |
| Access review | IAM / admin console / access review tracker | Security |
| Audit logs | Logging platform / application audit tables | Engineering / Security |
| Incident record | Incident management system | Security / Operations |
| Vendor diligence | Vendor risk repository | Compliance / Security |
| Change approval | Ticketing / release management system | Engineering |
| Training record | LMS / training tracker | Compliance |

---

## 20. Monitoring and Reporting

After launch, PayPlus must monitor the following.

| Area | Required Monitoring |
| --- | --- |
| Payments | Authorization rate, capture failures, payment failures, processor errors. |
| Payment instructions | Pending instructions, expired instructions, incomplete split-card funding, reminder effectiveness, quote revalidation changes, and partial funding/payout exceptions. |
| Payouts | Payout success rate, payout failures, delayed payouts, returned payouts. |
| Intended-Payee/destination verification | Applicable outcomes, verification failures and Payout destination failures. |
| Retired Request capability | No active lifecycle metrics; documentation history only. |
| Separate Rent | Tenancy/source evidence failures, duplicate Rent indicators and risk outcomes. |
| Reconciliation | Unmatched transactions, settlement breaks, Payout breaks and fee breaks. |
| Fraud | Rule triggers, owner-governed review outcomes, blocked transactions and suspicious source/destination indicators. |
| Anti-cashout | Self-payment alerts, source-context risk indicators, suspicious refunds and collusion indicators. |
| Sanctions | Screening hits, pending reviews, blocked parties. |
| Refunds | Refund volume, failure rate, reasons. |
| Disputes and chargebacks | New disputes, reason codes, exposure amount, evidence availability, representment status. |
| Complaints | Complaint volume, Payer complaints, source-context concerns, SLA and escalations. |
| Security | Incidents, access anomalies, critical vulnerabilities. |
| Privacy | Consent errors, visibility issues, data request issues, and privacy-request exceptions. |
| Finance | Gross volume, fees, reserves, losses, margin variance. |

Monitoring cadence:

| Period | Cadence |
| --- | --- |
| First 2 weeks after launch | Daily review |
| Weeks 3–8 | At least weekly review |
| After stabilization | Monthly governance review unless risk indicators require more frequent review |

---

## 21. Change Management

Material changes require reassessment and may require recertification.

Examples include:

- new jurisdiction;
- new bill category;
- new payee type;
- change to accepted source or economic-Payee assessment;
- change to separate Rent enablement;
- change to intended-Payee/destination verification;
- change to payer authorization flow;
- change to Payer/economic-Payee approved-purpose visibility;
- new payment method;
- new payout method;
- new PSP/acquirer;
- new payout provider;
- funds flow change;
- merchant of record change;
- PayFac, marketplace, sub-merchant, biller, or agent model change;
- fee model change;
- MCC or classification change;
- settlement timing change;
- reserve or holdback change;
- refund or chargeback process change;
- data handling change;
- AML, sanctions, fraud, or monitoring requirement change;
- material increase in fraud, chargebacks, complaints, Payout failures, source abuse, verification failures or reconciliation breaks.

Compliance must determine whether the change requires:

- no action;
- control update;
- additional testing;
- risk acceptance;
- DOC-03 reassessment;
- DOC-20 go-live checklist update;
- full recertification.

---

## 22. Risk Acceptance and Exceptions

Risk acceptance must be:

- explicit;
- documented;
- time-bound;
- tied to compensating controls;
- approved by the correct authority.

| Risk Severity | Acceptance Authority | Conditions |
| --- | --- | --- |
| Critical | Project Owner, Legal Lead, Compliance Lead, and relevant functional lead jointly | Only if not `T0` and compensating controls exist. |
| High | Compliance Lead and relevant functional lead | Remediation date, mitigation, and monitoring required. |
| Medium | Functional owner and Compliance reviewer | Remediation plan required. |
| Low | Functional owner | Tracked or accepted as residual risk. |

`T0` exceptions cannot be accepted for MVP launch.

`T0 if enabled` exceptions cannot be accepted for launch of the applicable enabled feature.

Exception log fields:

| Field | Description |
| --- | --- |
| Exception ID | Unique exception identifier. |
| Control ID | Related control. |
| Tier | `T0`, `T1`, `T2`, or `T3`. |
| Severity | Critical, high, medium, low. |
| Description | Exception details. |
| Detection Date | When issue was found. |
| Owner | Responsible remediation owner. |
| Root Cause | Cause of exception. |
| Impact | Compliance, financial, operational, payer, payee, security, privacy, or partner impact. |
| Temporary Mitigation | Interim control or workaround. |
| Remediation Plan | Corrective action. |
| Target Date | Due date. |
| Status | Open, in progress, remediated, accepted risk, closed. |
| Approver | Required approver for closure or acceptance. |
| Evidence | Proof of remediation. |

---

## 23. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC04-001` | What Hong Kong-specific launch requirements must be satisfied? | Project Owner / Legal | Critical | Open |
| `OQ-DOC04-002` | Which confirmed MVP categories are enabled at initial launch, and what gates, limits, evidence standards, and review controls apply by category? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC04-003` | What is the final MVP funds flow? | Product / Payments / Legal | Critical | Open |
| `OQ-DOC04-004` | What is PayPlus’s legal and partner role? | Legal / Compliance | Critical | Open |
| `OQ-DOC04-005` | What licensing, exemption, or partner coverage applies? | Legal / Compliance | Critical | Open |
| `OQ-DOC04-006` | Which PSP/acquirer will support MVP in Hong Kong? | Payments | Critical | Open |
| `OQ-DOC04-007` | What written PSP/acquirer confirmations are available? | Payments / Legal | Critical | Open |
| `OQ-DOC04-008` | What appropriate or special MCC will the selected acquirer assign? | Payments | Critical | Open |
| `OQ-DOC04-009` | Can transactions be confirmed as bill payment or ordinary online card purchase rather than quasi-cash, account funding, money transfer, cash advance, or cash-equivalent activity? | Payments / Legal | Critical | Open |
| `OQ-DOC04-010` | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments | Critical | Open |
| `OQ-DOC04-011` | What controls confirm payout occurs only after owner-confirmed upstream settlement and funding certainty, including the applicable settlement and payout timing? | Payments / Finance | Critical | Open |
| `OQ-DOC04-012` | What transaction, user, card, and payee limits apply at MVP? | Risk / Product | High | Open |
| `OQ-DOC04-013` | What final payee verification, payout destination verification, and exception checks are required by payee type and risk tier? | Compliance / Risk | High | Open |
| `OQ-DOC04-014` | What sanctions screening is legally or contractually required? | Compliance / Legal | Critical | Open |
| `OQ-DOC04-015` | What fraud and anti-cashout rules are required at launch? | Risk | Critical | Open |
| `OQ-DOC04-016` | What partner, risk, and reconciliation controls apply to the confirmed MVP maximum of 6 cards per payment/profile? | Product / Payments / Legal | Critical | Partially open |
| `OQ-DOC04-017` | What PCI scope applies? | Security | Critical | Open |
| `OQ-DOC04-018` | What disclosures must be shown before authorization? | Legal / Product | Critical | Open |
| `OQ-DOC04-019` | Which privacy, masking, approved-purpose access, legal-hold and correction/request controls apply by record class while every PayPlus record remains retained indefinitely under the Founder decision? | Legal / Compliance / Finance | High | Open |
| `OQ-DOC04-020` | What systems of record will store consent, authorization, risk, payout, refund, dispute, and reconciliation evidence? | Engineering / Compliance | High | Open |
| `OQ-DOC04-021` | Who has final authority to approve MVP launch? | Project Owner / Compliance | Critical | Open |
| `OQ-DOC04-022` | What post-launch monitoring cadence is acceptable after stabilization? | Compliance / Operations | Medium | Open |
| `OQ-DOC04-023` | Which accepted controlled Category or separate Rent paths are enabled at launch when their applicable controls are ready? | Project Owner / Product / Compliance | Critical | Open |
| `OQ-DOC04-024` | Which economic-Payee types are eligible for an owner-governed payment path? | Product / Risk / Compliance | Critical | Open |
| `OQ-DOC04-025` | What final KYC/KYB provider, check depth, sanctions screening, payout destination verification, and capability checks apply to the baseline onboarding model? | Compliance / Risk / Operations | Critical | Open |
| `OQ-DOC04-026` | What partner confirmation applies to the accepted Payer-created source model? | Payments / Legal / Compliance | Critical | Open |
| `OQ-DOC04-027` | How must Payer authorization be captured for an applicable payment? | Product / Legal / Payments | Critical | Open |
| `OQ-DOC04-028` | What Evidence is required for controlled Bill or separate Rent paths where applicable? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC04-029` | What controls and restrictions apply before the separate Rent journey is enabled? | Product / Legal / Risk | Critical | Open |
| `OQ-DOC04-030` | What tenancy/source, property reference and destination checks are required for Rent? | Product / Legal / Risk / Operations | Critical | Open |
| `OQ-DOC04-031` | What owner-governed support, adjustment or dispute handling applies? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-032` | What complaint, dispute or clarification process applies under the applicable owner? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-033` | What source-context information may be shown to the Payer under approved-purpose rules? | Product / Privacy / Security | High | Open |
| `OQ-DOC04-034` | What monitoring is required to detect fake invoices, fake Rent, related-party abuse and source abuse? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC04-035` | What revalidation and separate Payer authorization is required for a later payment? | Product / Legal / Payments | High | Open |
| `OQ-DOC04-036` | What applicable Payout or transaction fees are permitted? | Commercial / Finance / Product | Medium | Open |
| `OQ-DOC04-037` | What support, complaint, cancellation and adjustment procedures are required? | Operations / Product / Legal | High | Open |

---

## 24. Acceptance Criteria

`DOC-04` is acceptable when it clearly defines:

- PayPlus control objectives;
- control categories;
- control tiers;
- user controls;
- evidence controls;
- payment authorization controls;
- payee verification controls;
- transaction monitoring controls;
- admin review controls;
- audit and recordkeeping controls;
- prohibited activity controls;
- payout controls;
- refund, dispute, and chargeback controls;
- privacy and security controls;
- partner and launch readiness controls;
- launch blockers;
- control testing requirements;
- evidence and systems of record;
- monitoring and reporting requirements;
- change management triggers;
- risk acceptance and exception process;
- open questions.

This document must remain a testable compliance control framework.

It should not become:

- final legal advice;
- final licensing opinion;
- final PSP/acquirer approval;
- final AML policy;
- final sanctions policy;
- final fraud rulebook;
- product PRD;
- technical architecture;
- partner contract;
- support SOP;
- QA test suite;
- incident response runbook.

---

## 25. Revision History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.13.4` | `2026-08-13` | Product Documentation Team | Qualified Payout control evidence for confirmed Payment with valid sufficient Application lineage or an owner-controlled zero- or insufficient-Application resolution, without creating a Payout bypass or new mechanism. |
| `0.13.1` | `2026-08-12` | Product Documentation Team | Consolidated fixed-inventory, source/Payment Obligation, timing, retention and active/history corrections; removed the retired non-inventory control row from the active table. |
| `0.13.2` | `2026-08-12` | Product Documentation Team | Applied indefinite retention to active compliance controls and reframed the privacy/deletion open question as access, masking, legal-hold and correction handling without a destruction schedule. |
| `0.13.0` | `2026-08-12` | Product Documentation Team | Reframed the current compliance baseline for Payer-only controlled Bill and separate Rent flows; retired Request/Payee-user control assumptions; and preserved owner-first payment, Evidence, risk, privacy, Payout and Admin boundaries. |
| `0.12.6` | `2026-07-31` | Product Documentation Team | Aligned DOC-09 title references and evidence controls with Request-as-linkage rather than payment. |
| `0.12.5` | `2026-07-27` | Product Documentation Team | Distinguished direct payer-created obligations/payments from optional payer-created linking requests and aligned evidence-parity terminology without changing compliance controls. |
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-04 Compliance Certification Roadmap & Control Framework`. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Expanded into broad compliance roadmap and control framework with control domains, starter matrix, launch gates, evidence requirements, testing, remediation, governance, assumptions, constraints, dependencies, risks, downstream impact, and acceptance criteria. |
| `0.3.0` | `2026-05-26` | Product Documentation Team | Reframed as PayPlus-specific compliance certification framework with certification definition, MVP compliance posture, control tiering, non-waivable launch blockers, risk acceptance authority, MVP minimum control baseline, evidence system mapping, scope-specific launch gates, and stronger DOC-03/DOC-20 linkage. |
| `0.4.0` | `2026-05-27` | Product Documentation Team | Updated control framework to align with `DOC-05 v0.2.0` payee onboarding and payee-created bill, invoice, fee, and rent payment request capability. Added payee-created request certification, payee onboarding controls, payer authorization blockers, request evidence controls, landlord/rent controls, payer-payee relationship risk, payee-created request abuse monitoring, payer/payee privacy boundaries, support/dispute controls, expanded gates, dependencies, risks, open questions, and downstream document impacts. |
| `0.5.0` | `2026-05-27` | Product Documentation Team | Simplified structure and wording while preserving essential compliance certification, launch blocker, control matrix, payee-created request, landlord/rent, evidence, testing, monitoring, governance, risk, and readiness content. |
| `0.6.0` | `2026-05-27` | Product Documentation Team | Simplified into a testable compliance control framework with clear control categories for users, evidence, authorization, payee verification, monitoring, admin review, audit, prohibited activity, payout, disputes, privacy/security, and launch readiness. Preserved two-sided controls requiring payee-created requests to be evidence-backed, traceable, reviewed, and payer-authorized before payment. |
| `0.7.0` | `2026-05-29` | Product Documentation Team | Confirmed payee-created requests and tenancy/rent as MVP scope, clarified conditional controls as independent enablement gates, and promoted core payee-created and rent controls into the MVP control baseline. |
| `0.8.0` | `2026-05-30` | Product Documentation Team | Aligned prohibited activity controls with updated DOC-01 evidence-backed approved-obligation positioning. |
| `0.9.0` | `2026-06-01` | Product Documentation Team | Updated DOC-13 related-document title for promotion engine, coupon, voucher, referral, membership, and reward alignment. |
| `0.10.0` | `2026-06-02` | Product Documentation Team | Clarified that bill, fee, and rent/tenancy payments are MVP scope and that category-specific controls remain independently gated, aligned with DOC-14. |
| `0.11.0` | `2026-06-02` | Product Documentation Team | Added DOC-15 data classification register control covering approved-purpose use, masking, retention, and access-control mapping for material data objects and fields. |
| `0.12.0` | `2026-06-02` | Product Documentation Team | Aligned control framework with confirmed evidence-backed domestic helper, driver, and personal service MVP categories, DOC-09 user payment instruction controls, DOC-22 admin operations references, and updated category-gating open question wording. |
| `0.12.1` | `2026-07-02` | Product Documentation Team | Aligned payee-created request controls with DOC-06B `REQUESTS-NEW` and `REQUESTS-DETAIL` by treating query/dispute handling as linked support or exception paths rather than normal request-route statuses. |
| `0.12.2` | `2026-07-14` | Product Documentation Team | Distinguished authorization confirmation from the receipt issued after completed payment. |
| `0.12.3` | `2026-07-26` | Product Documentation Team | Confirmed the MVP maximum of 6 cards per payment/profile and retained partner, risk, and reconciliation controls as the remaining open compliance question. |
| `0.12.4` | `2026-07-26` | Product Documentation Team | Aligned monitoring with the canonical request lifecycle and separated request events, evidence outcomes, linked cases, payment outcomes, and archive visibility. |
```
```
