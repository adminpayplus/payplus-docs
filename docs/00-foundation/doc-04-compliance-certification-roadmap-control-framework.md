---
document_id: DOC-04
title: Compliance Control Framework
version: 0.12.1
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
last_updated: 2026-07-02
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
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
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

# DOC-04 — Compliance Control Framework

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

This document applies to:

- payer-created payment requests;
- payee-created payment requests;
- payee onboarding;
- bill, invoice, fee, and rent payment flows;
- domestic helper, driver, and personal service payment flows where evidence-backed and enabled;
- user payment instructions and deferred funding actions;
- payment authorization;
- payout controls;
- refund, dispute, chargeback, and reconciliation processes.

Payee-created requests are permitted only if they are:

```text
reviewable,
traceable,
evidence-backed,
risk-controlled,
and payer-authorized before payment.
```

This document is not a legal opinion, final AML policy, PSP/acquirer approval, risk rulebook, product PRD, support SOP, or technical architecture.

---

## 2. Control Objectives

PayPlus controls must support the following objectives.

| Objective ID | Objective |
| --- | --- |
| `OBJ-DOC04-001` | Payments must be tied to an approved bill, invoice, fee, rent, domestic helper, driver, personal service, or other approved obligation. |
| `OBJ-DOC04-002` | Payment requests must be supported by uploaded, linked, or captured evidence. |
| `OBJ-DOC04-003` | Payers must review and authorize payment before funding, capture, or payout. |
| `OBJ-DOC04-004` | Payee-created requests must not automatically trigger payment. |
| `OBJ-DOC04-005` | Payees must be verified before creating requests or receiving payouts, where required. |
| `OBJ-DOC04-006` | Prohibited and restricted categories must be blocked or routed to review. |
| `OBJ-DOC04-007` | Arbitrary P2P, self-payment, cashout, stored value, and wallet-like activity must be prevented. |
| `OBJ-DOC04-008` | Transaction limits, velocity rules, duplicate detection, and suspicious activity monitoring must be applied. |
| `OBJ-DOC04-009` | High-risk users, payees, requests, transactions, and payout events must be routed to admin review. |
| `OBJ-DOC04-010` | Payment, request, evidence, authorization, payout, refund, dispute, and reconciliation records must be traceable. |
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

- `T0 if payee-created enabled`
- `T1 if bill or fee category enabled`
- `T1 if rent enabled`
- `T1 if multi-source enabled`

Payee-created requests, bill payments, fee payments, rent/tenancy payments, domestic helper payments, driver payments, and personal service payments are MVP scope where supported by acceptable evidence and enabled controls. Invoice and other approved-obligation categories are MVP where evidence, payee, payment, payout, and risk controls are enabled. Conditional wording means the relevant module, category, payee type, or payment path must be independently configurable and may remain disabled until required controls are ready.

---

## 5. User Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-USER-001` | `T0` | Capture required user identity, contact, eligibility, terms acceptance, and privacy acknowledgement before payment. | Product / Compliance | User profile, consent logs |
| `CTRL-DOC04-USER-002` | `T0` | Display required payment disclosures before payer authorization. | Product / Legal | UI screenshots, disclosure logs |
| `CTRL-DOC04-USER-003` | `T0` | Capture disclosure version, acceptance timestamp, payer ID, request ID, transaction ID, amount, fees, and total charge. | Product / Engineering | Authorization and consent logs |
| `CTRL-DOC04-USER-004` | `T1` | Apply user eligibility rules, blocked-user rules, and restricted-user handling. | Product / Compliance / Risk | Eligibility config, blocked-user logs |
| `CTRL-DOC04-USER-005` | `T1` | Prevent users from paying themselves or related accounts unless explicitly approved. | Risk / Engineering | Rule config, alert logs |
| `CTRL-DOC04-USER-006` | `T1` | Provide payer access to request status, payment status, refund status, and support options. | Product / Operations | UI evidence, support logs |
| `CTRL-DOC04-USER-007` | `T1` | Allow payer to review, accept, reject, or ignore a payee-created request before payment, with query or dispute handled through approved support/exception paths where enabled. | Product / Operations | Request lifecycle and support/exception logs |
| `CTRL-DOC04-USER-008` | `T0` | Prevent funding, capture, and payout unless payer has explicitly authorized the payee-created request. | Product / Payments / Engineering | Authorization logs, payment state logs |

---

## 6. Evidence Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-EVD-001` | `T0` | Require each payment request to reference an approved obligation type, such as bill, invoice, fee, rent, domestic helper, driver, personal service, or other approved category. | Product / Compliance | Request record |
| `CTRL-DOC04-EVD-002` | `T0` | Require uploaded, linked, captured, or system-generated evidence for each payment request unless the category has an approved exception. | Product / Compliance | Evidence record |
| `CTRL-DOC04-EVD-003` | `T1` | Store evidence with request ID, payer ID, payee ID where applicable, category, timestamp, source, and review status. | Engineering / Compliance | Evidence metadata |
| `CTRL-DOC04-EVD-004` | `T1` | Prevent request submission if required evidence fields are missing. | Product / Engineering | Validation logs |
| `CTRL-DOC04-EVD-005` | `T1` | Detect duplicate evidence, duplicate invoices, duplicate rent requests, or repeated payment requests where feasible. | Risk / Engineering | Duplicate detection alerts |
| `CTRL-DOC04-EVD-006` | `T1` | Route unclear, incomplete, suspicious, or high-risk evidence to admin review. | Risk / Operations | Review case logs |
| `CTRL-DOC04-EVD-007` | `T1` | Require payee-created requests to include evidence equal to or stronger than payer-created request evidence for the same category. | Product / Compliance / Risk | Evidence requirements matrix |
| `CTRL-DOC04-EVD-008` | `T1` | Require rent evidence, such as lease, rent schedule, property reference, tenancy confirmation, or approved equivalent. | Product / Compliance / Risk | Rent evidence record |
| `CTRL-DOC04-EVD-009` | `T1 if invoice enabled` | Require invoice evidence, business-payee details, service description, amount, due date, and payee identity information. | Product / Compliance / Risk | Invoice evidence record |
| `CTRL-DOC04-EVD-010` | `T1 if domestic helper, driver, or personal service enabled` | Require acceptable employment, service, invoice, salary, contract, or obligation evidence before payment and payout. | Product / Compliance / Risk | Service-obligation evidence record |

---

## 7. Payment Authorization Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-AUTH-001` | `T0` | Payer must authorize payment before funding, capture, or payout. | Product / Payments / Engineering | Authorization logs |
| `CTRL-DOC04-AUTH-002` | `T0` | Authorization must capture payer ID, amount, fee, total charge, payee/biller identity, request ID, timestamp, payment method, and disclosure version. | Product / Engineering | Authorization record |
| `CTRL-DOC04-AUTH-003` | `T0` | Payment amount, fees, and total charge must not change after authorization unless payer re-authorizes. | Product / Payments / Engineering | Change logs, authorization logs |
| `CTRL-DOC04-AUTH-004` | `T1` | Authorization, capture, reversal, cancellation, refund, and chargeback events must be linked to the original request. | Payments / Engineering / Finance | Transaction ledger |
| `CTRL-DOC04-AUTH-005` | `T1` | Failed or expired authorizations must not result in payout. | Payments / Engineering | Payment state logs |
| `CTRL-DOC04-AUTH-006` | `T1` | Payer must receive confirmation or receipt after successful authorization or payment. | Product / Operations | Receipt logs |
| `CTRL-DOC04-AUTH-007` | `T1` | Payee-created requests must remain in a non-payment state such as pending evidence verification, sent/reviewing, viewed, accepted, rejected, expired, cancelled, withdrawn, or support/exception-linked until payer authorization occurs. | Product / Engineering | Request state and support/exception history |
| `CTRL-DOC04-AUTH-008` | `T0` | Payee-created request acceptance and payment authorization must be distinct, recorded events unless legally and product-approved as a single combined action. | Product / Legal / Engineering | Event logs |
| `CTRL-DOC04-AUTH-009` | `T1` | Payee cannot change amount, destination, due date, evidence, or material terms after payer authorization unless payer re-authorizes. | Product / Engineering | Change lock logs |
| `CTRL-DOC04-AUTH-010` | `T1 if payment instruction enabled` | A deferred user payment instruction must not be treated as card authorization, capture, settlement, payout readiness, or completed payment until the relevant funding leg is submitted and confirmed. | Product / Payments / Engineering | Payment instruction and funding-leg logs |
| `CTRL-DOC04-AUTH-011` | `T1 if payment instruction enabled` | Returning to a deferred payment instruction must revalidate material payment terms, including amount, fee, promotion quote, card eligibility, timing, and required disclosures before funding submission. | Product / Payments / Growth / Engineering | Quote revalidation and user confirmation logs |

---

## 8. Payee Verification Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-PAYEE-001` | `T1` | Verify payee identity, business identity, payout destination, and eligibility before payout where required. | Compliance / Risk / Operations | Payee verification record |
| `CTRL-DOC04-PAYEE-002` | `T0` | Verify payee eligibility before granting payee-created request capability. | Compliance / Risk / Product | Capability approval log |
| `CTRL-DOC04-PAYEE-003` | `T1` | Screen payees against applicable sanctions or blocked-party lists where required. | Compliance | Screening logs |
| `CTRL-DOC04-PAYEE-004` | `T1` | Assign payee status, risk tier, category permissions, payout permissions, and request creation permissions. | Product / Risk / Compliance | Payee capability config |
| `CTRL-DOC04-PAYEE-005` | `T1` | Block restricted, rejected, suspended, or unverified payees from payout. | Product / Payments / Engineering | Payout block logs |
| `CTRL-DOC04-PAYEE-006` | `T1 if payee-created enabled` | Block restricted, rejected, suspended, or unverified payees from creating or sending payment requests. | Product / Engineering | Request permission logs |
| `CTRL-DOC04-PAYEE-007` | `T1` | Review payout destination changes before allowing payout to the new destination where risk requires. | Operations / Risk / Payments | Change review logs |
| `CTRL-DOC04-PAYEE-008` | `T1` | Verify landlord or property manager identity, property relationship, payout destination, and rent-request eligibility. | Compliance / Risk / Operations | Landlord verification record |
| `CTRL-DOC04-PAYEE-009` | `T1 if invoice enabled` | Verify business-payee identity, business status, invoice legitimacy indicators, and payout destination where required. | Compliance / Risk / Operations | Business payee verification record |
| `CTRL-DOC04-PAYEE-010` | `T1` | Offboard or suspend payees with confirmed fraud, sanctions issues, excessive disputes, unsupported categories, or partner violations. | Compliance / Risk / Operations | Offboarding logs |

---

## 9. Transaction Monitoring Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-MON-001` | `T0` | Apply baseline transaction limits before launch. | Risk / Product | Limit config |
| `CTRL-DOC04-MON-002` | `T0` | Apply velocity limits for users, cards, payees, requests, failed authorizations, and payouts where applicable. | Risk / Engineering | Rule config |
| `CTRL-DOC04-MON-003` | `T1` | Monitor failed authorizations, repeated attempts, suspicious refunds, chargebacks, payout failures, and account changes. | Risk / Operations | Monitoring reports |
| `CTRL-DOC04-MON-004` | `T1` | Monitor duplicate bills, duplicate invoices, duplicate rent requests, and repeated obligation evidence. | Risk / Engineering | Duplicate alerts |
| `CTRL-DOC04-MON-005` | `T1` | Monitor payer-payee concentration, unusual payer-payee relationships, circular activity, and related-party patterns. | Risk / Compliance | Relationship alerts |
| `CTRL-DOC04-MON-006` | `T1` | Monitor restricted categories, high-risk MCC/classification issues, suspicious payees, and unsupported activity. | Risk / Compliance | Monitoring reports |
| `CTRL-DOC04-MON-007` | `T1 if payee-created enabled` | Monitor payee-created request volume, rejection rate, dispute rate, expiry rate, complaint rate, and conversion to paid status. | Risk / Operations | Request monitoring dashboard |
| `CTRL-DOC04-MON-008` | `T1 if payee-created enabled` | Monitor fake obligation, inflated amount, request spam, duplicate request, collusion, and self-payment indicators. | Risk / Compliance | Alerts, case logs |
| `CTRL-DOC04-MON-009` | `T1 if rent enabled` | Monitor rent amount reasonableness, duplicate rent, recurring rent patterns, property reuse, and suspicious landlord/payer relationships. | Risk / Compliance | Rent monitoring report |
| `CTRL-DOC04-MON-010` | `T1` | Escalate suspicious activity to Compliance, Risk, Legal, or partner contacts according to severity. | Risk / Compliance / Operations | Escalation logs |

---

## 10. Admin Review Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-ADM-001` | `T1` | Maintain an admin review queue for high-risk users, payees, requests, evidence, transactions, refunds, payouts, and disputes. | Operations / Risk | Review queue logs |
| `CTRL-DOC04-ADM-002` | `T1` | Define manual review triggers before launch. | Risk / Compliance | Trigger matrix |
| `CTRL-DOC04-ADM-003` | `T1` | Require reviewer decision, timestamp, rationale, and outcome for each manual review case. | Operations / Risk | Case decision logs |
| `CTRL-DOC04-ADM-004` | `T1` | Support approve, reject, hold, request more information, escalate, suspend, or close actions. | Operations / Product | Case action logs |
| `CTRL-DOC04-ADM-005` | `T1` | Restrict admin access by role and least privilege. | Security / Engineering | RBAC matrix |
| `CTRL-DOC04-ADM-006` | `T1` | Log all admin actions affecting requests, evidence, user status, payee status, risk decisions, payment status, payout status, refund status, or dispute status. | Engineering / Security | Admin audit logs |
| `CTRL-DOC04-ADM-007` | `T1 if payee-created enabled` | Route suspicious payee-created requests to admin review before payer authorization or payout, depending on risk severity. | Risk / Operations | Review case logs |
| `CTRL-DOC04-ADM-008` | `T1 if rent enabled` | Route high-value, first-time, duplicate, unusual, or changed-destination rent requests to admin review. | Risk / Operations | Rent review logs |

---

## 11. Audit and Recordkeeping Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-AUD-001` | `T0` | Maintain a launch certification evidence package before MVP launch. | Compliance | Launch package |
| `CTRL-DOC04-AUD-002` | `T0` | Retain request, evidence, disclosure, authorization, payment, payout, refund, dispute, chargeback, and reconciliation records. | Compliance / Engineering / Finance | Records inventory |
| `CTRL-DOC04-AUD-003` | `T1` | Maintain immutable or tamper-evident audit logs for compliance-critical actions. | Engineering / Security | Audit logs |
| `CTRL-DOC04-AUD-004` | `T1` | Link request records to evidence, payer authorization, payment transaction, payout, refund, dispute, chargeback, and ledger entries. | Engineering / Finance | Ledger linkage |
| `CTRL-DOC04-AUD-005` | `T1` | Record request creator type, payee type, category, evidence status, authorization status, payment status, payout status, and risk status. | Engineering / Product | Data records |
| `CTRL-DOC04-AUD-006` | `T1` | Maintain retention and deletion rules for compliance, privacy, tax, finance, partner, and dispute records. | Privacy / Compliance / Legal | Retention schedule |
| `CTRL-DOC04-AUD-007` | `T1` | Store dispute and chargeback evidence in a retrievable evidence package. | Operations / Payments | Dispute evidence package |
| `CTRL-DOC04-AUD-008` | `T1` | Maintain daily reconciliation evidence for settlement, fees, payouts, refunds, chargebacks, reserves, bank records, and ledger entries. | Finance / Payments | Reconciliation reports |
| `CTRL-DOC04-AUD-009` | `T1 if payee-created enabled` | Link payee-created request origin, evidence, payer response, authorization, communication, payment, payout, refund, and dispute records. | Compliance / Engineering / Operations | Request evidence package |
| `CTRL-DOC04-AUD-010` | `T1` | Retain risk review, manual review, sanctions review, and suspicious activity escalation records. | Risk / Compliance | Case records |

---

## 12. Prohibited Activity Controls

PayPlus must prevent or restrict activity that could undermine the product's evidence-backed, payer-authorized approved-obligation model.

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-PROH-001` | `T0` | Block wallet, stored balance, preload, user-controlled stored value, and cashout functionality unless separately approved. | Product / Legal / Compliance | Product configuration |
| `CTRL-DOC04-PROH-002` | `T0` | Block arbitrary P2P transfers unrelated to an approved bill, invoice, fee, rent, or obligation. | Product / Compliance | Category and request validation |
| `CTRL-DOC04-PROH-003` | `T0` | Block prohibited categories before request submission or payment authorization. | Product / Compliance | Category config |
| `CTRL-DOC04-PROH-004` | `T1` | Route restricted categories to enhanced review or block them according to approved rules. | Product / Risk / Compliance | Review logs |
| `CTRL-DOC04-PROH-005` | `T1` | Block or escalate self-payment, circular payment, related-party abuse, and collusive payment patterns. | Risk / Compliance | Alerts, case logs |
| `CTRL-DOC04-PROH-006` | `T1` | Block cash-equivalent, gift card, crypto, gambling, investment, and other restricted use cases unless explicitly approved. | Product / Compliance | Category rules |
| `CTRL-DOC04-PROH-007` | `T1` | Prevent payees from requesting payment for unsupported, unverifiable, or misleading obligations. | Product / Risk / Compliance | Request validation logs |
| `CTRL-DOC04-PROH-008` | `T1 if payee-created enabled` | Prevent payee-created requests from implying that payment is mandatory, already completed, legally validated by PayPlus, or automatically charged. | Product / Legal | Disclosure review |
| `CTRL-DOC04-PROH-009` | `T1 if rent enabled` | Block landlord-created rent requests unless landlord verification, tenancy evidence, relationship checks, and rent controls are implemented. | Product / Compliance / Risk | Feature gate config |
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
| `CTRL-DOC04-POUT-007` | `T0 if payee-created enabled` | Payee-created request payout must be blocked until payer authorization, payment success, required evidence, payee verification, risk checks, and payout readiness are complete. | Payments / Risk / Engineering | Payout gate evidence |
| `CTRL-DOC04-POUT-008` | `T1 if rent enabled` | Rent payouts must be subject to landlord verification, tenancy evidence, duplicate detection, payout destination controls, and risk review where required. | Payments / Risk / Operations | Rent payout review |

---

## 14. Refund, Dispute, and Chargeback Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-RDC-001` | `T1` | Maintain refund rules covering eligibility, timing, amount, fees, payout status, and ledger treatment. | Operations / Payments / Finance | Refund policy, refund logs |
| `CTRL-DOC04-RDC-002` | `T1` | Link refunds to original request, authorization, payment, fee, payout, and ledger entries. | Payments / Engineering / Finance | Refund ledger |
| `CTRL-DOC04-RDC-003` | `T1` | Maintain cancellation rules before payment, after authorization, before payout, and after payout. | Operations / Product / Payments | Cancellation logs |
| `CTRL-DOC04-RDC-004` | `T1` | Track payer disputes, payee disputes, payer queries, complaints, and support escalations. | Operations | Case logs |
| `CTRL-DOC04-RDC-005` | `T1` | Track chargebacks, reason codes, deadlines, evidence, representment status, liability, and outcome. | Operations / Payments | Chargeback case |
| `CTRL-DOC04-RDC-006` | `T1` | Maintain chargeback evidence package including request evidence, payer authorization, disclosures, communication, payment logs, and payout proof. | Operations / Payments / Compliance | Chargeback evidence package |
| `CTRL-DOC04-RDC-007` | `T1 if payee-created enabled` | Track payer rejection, expiry, cancellation, payee withdrawal, and any linked query/dispute/support case before authorization. | Product / Operations | Request lifecycle and support/exception logs |
| `CTRL-DOC04-RDC-008` | `T1 if payee-created enabled` | Payee withdrawal must not reverse an already authorized payment unless cancellation, refund, or reversal rules allow it. | Product / Payments / Operations | Withdrawal and refund logs |

---

## 15. Privacy and Security Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-SEC-001` | `T0` | PCI scope and card data handling model must be approved before production card processing. | Security | PCI scope document |
| `CTRL-DOC04-SEC-002` | `T0` | Sensitive card data must not be stored unless explicitly approved under PCI scope. | Security / Engineering | Architecture review |
| `CTRL-DOC04-SEC-003` | `T1` | Use tokenized card handling where applicable. | Security / Payments / Engineering | Tokenization evidence |
| `CTRL-DOC04-SEC-004` | `T1` | Encrypt sensitive data in transit and at rest. | Security / Engineering | Security review |
| `CTRL-DOC04-SEC-005` | `T1` | Restrict admin, support, risk, payee, and engineering access by role. | Security / Engineering | RBAC matrix |
| `CTRL-DOC04-SEC-006` | `T1` | Log access to sensitive payer, payee, payment, evidence, payout, and risk data. | Security / Engineering | Access logs |
| `CTRL-DOC04-SEC-007` | `T1` | Maintain privacy notice, consent records, data map, retention rules, and deletion process. | Privacy / Legal / Product | Privacy records |
| `CTRL-DOC04-SEC-008` | `T1 if payee-created enabled` | Enforce payer/payee visibility boundaries so payees cannot see sensitive payer funding, card, risk, or private profile information. | Privacy / Security / Engineering | Visibility test evidence |
| `CTRL-DOC04-SEC-009` | `T1 if payee-created enabled` | Limit payer access to payee evidence based on approved disclosure and privacy rules. | Privacy / Product / Legal | Visibility rules |
| `CTRL-DOC04-SEC-010` | `T1` | Maintain incident severity levels, escalation contacts, and incident response procedure. | Security / Operations | Incident runbook |
| `CTRL-DOC04-SEC-011` | `T1` | Maintain DOC-15 data classification, approved-purpose, masking, retention, and access-control mapping for material objects and fields. | Privacy / Security / Engineering / Data | Data classification register |

---

## 16. Partner and Launch Readiness Controls

| Control ID | Tier | Requirement | Owner | Evidence |
| --- | --- | --- | --- | --- |
| `CTRL-DOC04-LAUNCH-001` | `T0` | Launch scope must define Hong Kong launch requirements, categories, payment methods, payout methods, partners, payee types, and request creator types. | Project Owner / Compliance | Launch scope record |
| `CTRL-DOC04-LAUNCH-002` | `T0` | Regulatory role and licensing path must be assessed before launch. | Legal / Compliance | DOC-03 assessment |
| `CTRL-DOC04-LAUNCH-003` | `T0` | PSP/acquirer support must be confirmed for use case, funds flow, categories, fees, request creator model, and intended MCC/classification. | Payments / Legal | Partner confirmation |
| `CTRL-DOC04-LAUNCH-004` | `T0` | PayPlus operating bank setup and approved Hong Kong payout rails must be confirmed before production payout. | Payments / Legal | Partner confirmation |
| `CTRL-DOC04-LAUNCH-005` | `T0` | Fee model, total charge display, and required disclosures must be approved before launch. | Legal / Product / Finance | Approval record |
| `CTRL-DOC04-LAUNCH-006` | `T0` | Required T0 controls must be implemented, tested, and evidenced before launch. | Compliance / QA | Test evidence |
| `CTRL-DOC04-LAUNCH-007` | `T1` | T1 exceptions must be remediated or formally risk-accepted with mitigation and target date. | Compliance / Functional Owner | Exception log |
| `CTRL-DOC04-LAUNCH-008` | `T0` | Required approvers must sign launch certification for the defined scope. | Project Owner / Compliance | Approval log |
| `CTRL-DOC04-LAUNCH-009` | `T0 if payee-created enabled` | Payee-created request model must be approved through DOC-03 and certified through this framework before launch. | Legal / Compliance / Payments | Approval record |
| `CTRL-DOC04-LAUNCH-010` | `T0 if rent enabled` | Landlord-created rent requests must be separately approved and certified before launch. | Legal / Compliance / Risk | Rent approval record |

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

Additional blockers apply if payee-created requests are enabled.

| Blocker ID | Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-015` | Payee-created request model is not assessed and approved through DOC-03. | Legal / Compliance / Payments |
| `BLK-DOC04-016` | Payee onboarding, verification, sanctions, payout destination, and capability controls are not implemented. | Compliance / Risk / Operations |
| `BLK-DOC04-017` | Payee-created requests can trigger funding, capture, or payout before payer authorization. | Product / Payments / Engineering |
| `BLK-DOC04-018` | Payee-created request evidence requirements are not implemented. | Product / Compliance / Risk |
| `BLK-DOC04-019` | Payout gating is not implemented for payee-created requests. | Payments / Risk / Finance |
| `BLK-DOC04-020` | Payer/payee privacy boundaries and RBAC are not implemented. | Privacy / Security |
| `BLK-DOC04-021` | Request abuse, fake obligation, self-payment, relationship, and collusion controls are not implemented. | Risk / Compliance |
| `BLK-DOC04-022` | Landlord-created rent requests are enabled without landlord verification, tenancy evidence, rent controls, and partner/legal approval. | Legal / Compliance / Risk |
| `BLK-DOC04-023` | Support, complaint, rejection, query, dispute, and payee withdrawal procedures are not defined. | Operations / Legal / Product |

---

## 18. Control Testing

Compliance-critical controls must be tested before launch.

Required launch tests include:

- user eligibility and consent capture;
- fee and total amount display before authorization;
- disclosure version logging;
- prohibited category blocking;
- restricted category review routing;
- evidence upload or linking;
- missing evidence blocking;
- duplicate bill, invoice, or rent detection where applicable;
- payer authorization before funding, capture, or payout;
- deferred user payment instruction is not treated as authorization, capture, settlement, payout readiness, or completed payment before funding submission;
- returning to a deferred payment instruction revalidates payment quote, promotion quote, card eligibility, fee, timing, and required disclosures;
- material term lock after authorization;
- payee verification before payout;
- payee capability gating before payee-created requests;
- sanctions screening and escalation where required;
- transaction limits and velocity rules;
- self-payment detection;
- suspicious activity escalation;
- admin review queue and decision logging;
- payout eligibility and payout gating;
- payout failure handling;
- refund flow;
- dispute and chargeback tracking;
- chargeback evidence package retrieval;
- daily reconciliation;
- audit log generation;
- record retention mapping;
- PCI/card data handling controls;
- payer/payee privacy boundary controls;
- incident escalation.

If payee-created requests are enabled, additional tests must include:

- payee-created request creation by eligible payee only;
- blocked payee cannot create request;
- required evidence for payee-created request;
- payer can review request before payment;
- payer can reject or ignore request without funds movement, and can raise a query/dispute/support case through the approved exception path where enabled;
- payee-created request cannot fund, capture, or pay out before payer authorization;
- payee cannot change material terms after payer authorization without renewed authorization;
- payee withdrawal before authorization where supported;
- request abuse monitoring;
- request origin disclosure;
- payer/payee visibility rules;
- payout gating for payee-created request.

If landlord-created rent requests are enabled, additional tests must include:

- landlord verification;
- tenancy evidence capture;
- rent amount reasonableness check where required;
- duplicate rent detection;
- payer-landlord relationship check where required;
- payout destination change review;
- rent request manual review triggers.

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
| Payee onboarding and verification | Compliance case system / operations queue / application database | Compliance / Operations |
| Payee capability record | Application database / admin console | Product / Risk |
| Payment request record | Application database / transaction system | Product / Engineering |
| Request, invoice, rent, or bill evidence | Evidence repository / document storage / application database | Product / Compliance / Risk |
| Payer response and authorization | Application database / audit log / payment platform | Product / Payments / Engineering |
| Payer/payee communication | Notification system / support system | Operations / Product |
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
| Payee onboarding | Applications, approvals, rejections, pending reviews, verification failures, payout destination failures. |
| Payee-created requests | Sent, viewed, accepted, rejected, expired, withdrawn, paid, and linked query/dispute/support case records. |
| Rent requests | Landlord approvals, tenancy evidence failures, duplicate rent signals, relationship alerts, rent amount exceptions. |
| Reconciliation | Unmatched transactions, settlement breaks, payout breaks, fee breaks, request creator type mismatches. |
| Fraud | Rule triggers, manual review queue, blocked transactions, suspicious payees, suspicious requests. |
| Anti-cashout | Self-payment alerts, relationship alerts, payee concentration, suspicious refunds, collusion indicators. |
| Sanctions | Screening hits, pending reviews, blocked parties. |
| Refunds | Refund volume, failure rate, reasons. |
| Disputes and chargebacks | New disputes, reason codes, exposure amount, evidence availability, representment status. |
| Complaints | Complaint volume, payer complaints, payee complaints, request-origin complaints, SLA, escalations. |
| Security | Incidents, access anomalies, critical vulnerabilities. |
| Privacy | Consent errors, visibility issues, data request issues, deletion exceptions. |
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
- new request creator type;
- payee-created request enablement;
- landlord-created rent request enablement;
- payee-created invoice or fee request enablement;
- change to payee onboarding;
- change to payer authorization flow;
- change to payer/payee data visibility;
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
- material increase in fraud, chargebacks, complaints, payout failures, request abuse, onboarding failures, or reconciliation breaks.

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
| `OQ-DOC04-011` | What controls confirm payout occurs only after upstream settlement and funding certainty under the expected T+1 to T+3 settlement model? | Payments / Finance | Critical | Open |
| `OQ-DOC04-012` | What transaction, user, card, and payee limits apply at MVP? | Risk / Product | High | Open |
| `OQ-DOC04-013` | What final payee verification, payout destination verification, and exception checks are required by payee type and risk tier? | Compliance / Risk | High | Open |
| `OQ-DOC04-014` | What sanctions screening is legally or contractually required? | Compliance / Legal | Critical | Open |
| `OQ-DOC04-015` | What fraud and anti-cashout rules are required at launch? | Risk | Critical | Open |
| `OQ-DOC04-016` | What configurable maximum number of credit cards per payment should be allowed at launch, and what partner, risk, and reconciliation controls apply? | Product / Payments / Legal | Critical | Open |
| `OQ-DOC04-017` | What PCI scope applies? | Security | Critical | Open |
| `OQ-DOC04-018` | What disclosures must be shown before authorization? | Legal / Product | Critical | Open |
| `OQ-DOC04-019` | What privacy, deletion, masking, and legal exception rules apply beyond the 7-year tax and audit retention baseline? | Legal / Compliance / Finance | High | Open |
| `OQ-DOC04-020` | What systems of record will store consent, authorization, risk, payout, refund, dispute, and reconciliation evidence? | Engineering / Compliance | High | Open |
| `OQ-DOC04-021` | Who has final authority to approve MVP launch? | Project Owner / Compliance | Critical | Open |
| `OQ-DOC04-022` | What post-launch monitoring cadence is acceptable after stabilization? | Compliance / Operations | Medium | Open |
| `OQ-DOC04-023` | Which payee-created request modules, categories, and payee types are enabled at initial launch versus disabled until controls are ready? | Project Owner / Product / Compliance | Critical | Open |
| `OQ-DOC04-024` | Which payee types can create payment requests? | Product / Risk / Compliance | Critical | Open |
| `OQ-DOC04-025` | What final KYC/KYB provider, check depth, sanctions screening, payout destination verification, and capability checks apply to the baseline onboarding model? | Compliance / Risk / Operations | Critical | Open |
| `OQ-DOC04-026` | Does the payee-created request model require additional partner confirmation? | Payments / Legal / Compliance | Critical | Open |
| `OQ-DOC04-027` | How must payer authorization be captured for payee-created requests? | Product / Legal / Payments | Critical | Open |
| `OQ-DOC04-028` | What evidence is required for payee-created bill, invoice, fee, or rent requests? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC04-029` | What controls and restrictions are required before landlord-created rent request creation is enabled for production use? | Product / Legal / Risk | Critical | Open |
| `OQ-DOC04-030` | What landlord onboarding, tenancy evidence, property reference, and relationship checks are required? | Product / Legal / Risk / Operations | Critical | Open |
| `OQ-DOC04-031` | What payer response options are supported for payee-created requests? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-032` | What payer rejection, query, dispute, or clarification process applies before authorization? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-033` | What payee-created request information can be shown to payer, and what payer information can be shown to payee? | Product / Privacy / Security | High | Open |
| `OQ-DOC04-034` | What monitoring is required to detect fake invoices, fake rent, related-party abuse, and request spam? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC04-035` | Are recurring payee-created rent or invoice requests allowed, or must each request be individually authorized? | Product / Legal / Payments | High | Open |
| `OQ-DOC04-036` | Are payees charged onboarding, subscription, invoice, payout, platform, or transaction fees? | Commercial / Finance / Product | Medium | Open |
| `OQ-DOC04-037` | What payee-side support, complaint, cancellation, and withdrawal procedures are required? | Operations / Product / Legal | High | Open |

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
```
```
