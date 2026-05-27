---
document_id: DOC-04
title: Compliance Certification Roadmap & Control Framework
version: 0.5.0
status: Draft
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
last_updated: 2026-05-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Communication
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-13 Promotion Engine & Campaign Rules
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-16 Technical Architecture
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT, Release & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operations Runbook
---

# DOC-04 — Compliance Certification Roadmap & Control Framework

## 1. Purpose

This document defines the PayPlus compliance certification roadmap and control framework.

It converts legal, regulatory, PSP/acquirer, payout provider, card network, AML, sanctions, fraud, consumer protection, privacy, security, finance, reconciliation, and operational obligations into practical launch and operating controls.

`DOC-04` determines:

- what must be true before launch;
- which controls are launch blockers;
- what evidence is required;
- who owns each control;
- what must be tested;
- what must be monitored after launch;
- what must be reassessed before scaling or changing scope.

This document applies to PayPlus MVP and future expansion, including payee onboarding and payee-created bill, invoice, fee, and rent payment requests.

---

## 2. Core Principle

A payee-created bill, invoice, fee, or rent request must meet the same evidence, eligibility, verification, risk, disclosure, authorization, payment, payout, reconciliation, refund, chargeback, audit, privacy, and recordkeeping standards as a payer-created request.

Payee-created request functionality is therefore a gated capability.

If enabled, all relevant controls must be implemented, tested, evidenced, and approved before launch.

---

## 3. What Compliance Certification Means

For PayPlus, “compliance certification” means a documented internal and partner-supported readiness decision confirming that applicable controls have been:

- designed;
- implemented;
- tested;
- evidenced;
- approved for a defined launch scope.

Certification is scope-specific.

Approval for one jurisdiction, category, partner, payee type, request creator model, payment method, payout method, or funds flow does not imply approval for another.

| Certification Type | Meaning | Required Before |
| --- | --- | --- |
| Internal launch certification | Internal approval that launch controls are ready for approved scope. | MVP launch |
| Regulatory readiness | Legal/Compliance confirmation that role, licensing path, exemption, or partner coverage has been assessed. | MVP launch / jurisdiction expansion |
| PSP/acquirer readiness | Confirmation that PSP/acquirer supports use case, funds flow, categories, fees, payee types, and request creator model. | Production card processing |
| Payout readiness | Confirmation that payout provider, rails, reconciliation, exceptions, and settlement timing are ready. | Production payouts |
| Security and PCI readiness | Confirmation of PCI scope, card data model, access controls, and security review. | Production card processing |
| Privacy readiness | Confirmation that data map, privacy notice, consent, retention, deletion, and payer/payee visibility controls are ready. | MVP launch |
| AML/sanctions/fraud readiness | Confirmation that screening, limits, monitoring, escalation, anti-cashout, and recordkeeping controls are ready. | MVP launch |
| Consumer protection readiness | Confirmation that fee, timing, role, request origin, authorization, refund, cancellation, support, and dispute disclosures are ready. | MVP launch |
| Payee onboarding readiness | Confirmation that payee verification, sanctions, payout destination, capability, and offboarding controls are ready. | Before payee-created requests or payee payout |
| Payee-created request readiness | Confirmation that request creation, evidence, payer review, authorization, lifecycle, payout gating, abuse monitoring, privacy, and support controls are ready. | Before payee-created requests |
| Landlord/rent readiness | Confirmation that landlord onboarding, tenancy evidence, relationship checks, and rent-specific controls are ready. | Before landlord-created rent requests |
| Operational readiness | Confirmation that support, complaints, refunds, chargebacks, payout exceptions, disputes, incident response, and reconciliation operations are ready. | MVP launch |
| Expansion certification | Re-certification for new jurisdictions, categories, partners, payment methods, payee types, request creator models, or funds-flow changes. | Before expansion |

---

## 4. Scope

This document covers:

- compliance certification approach;
- MVP compliance posture;
- control tiers;
- non-waivable launch blockers;
- risk acceptance;
- control domains;
- MVP control baseline;
- payee onboarding controls;
- payee-created request controls;
- landlord/rent request controls;
- control matrix;
- evidence requirements;
- testing requirements;
- exception and remediation process;
- regulatory and partner change management;
- vendor and partner oversight;
- monitoring and reporting;
- governance forums;
- assumptions, constraints, dependencies, risks, and open questions.

---

## 5. Out of Scope

This document does not provide:

- final legal advice;
- final licensing opinion;
- final PSP/acquirer approval;
- final card network rule interpretation;
- final AML, sanctions, or fraud policy;
- final payee onboarding policy;
- final KYB/KYC standard;
- final landlord or invoice verification standard;
- complete PCI DSS implementation plan;
- complete SOC 2 audit plan;
- complete privacy program;
- product PRD;
- technical architecture;
- partner contract;
- support SOP;
- QA test suite;
- incident response runbook.

Those items belong in the appropriate downstream documents, policies, contracts, or operating procedures.

---

## 6. PayPlus Risk Themes

The control framework must address these core PayPlus risks.

| Theme ID | Risk Theme | Why It Matters |
| --- | --- | --- |
| `THEME-DOC04-001` | Bill payment may differ from ordinary card commerce. | Partners and regulators may view it as payment facilitation, money movement, quasi-cash, account funding, or money transmission. |
| `THEME-DOC04-002` | PayPlus may receive funds before paying third-party payees. | Creates licensing, safeguarding, settlement, reconciliation, and customer-funds risk. |
| `THEME-DOC04-003` | Payout may occur before final card settlement or before chargeback risk expires. | Creates liquidity, credit, fraud, and loss exposure. |
| `THEME-DOC04-004` | Chargebacks may occur after payout. | PayPlus may be unable to recover funds from payees. |
| `THEME-DOC04-005` | Multi-source funding increases complexity. | Creates refund allocation, chargeback, partial failure, AML, risk, and reconciliation complexity. |
| `THEME-DOC04-006` | Service fees may trigger legal, card network, and disclosure requirements. | Improper fee treatment can create regulatory, partner, and complaint risk. |
| `THEME-DOC04-007` | Some categories resemble cashout, debt repayment, money transfer, or restricted activity. | Rent, tax, loans, credit cards, crypto, gambling, investments, and self-payments may require enhanced review. |
| `THEME-DOC04-008` | MCC and classification affect user experience and cost. | Users may face declines, cash advance treatment, reward differences, or issuer fees. |
| `THEME-DOC04-009` | Payee verification is central to anti-cashout. | Weak verification may allow self-payment or collusive payees. |
| `THEME-DOC04-010` | Partner approvals are operating constraints. | PSP, acquirer, payout provider, and card network rules can override product assumptions. |
| `THEME-DOC04-011` | Reconciliation must connect charge, fee, payout, refund, chargeback, reserve, and ledger records. | Missing links create financial loss, reporting gaps, and audit failure. |
| `THEME-DOC04-012` | Product changes may alter regulatory classification. | Changes to funds flow, categories, fees, payout timing, custody, payee role, or request creator model can invalidate approvals. |
| `THEME-DOC04-013` | Payee-created requests may change PayPlus role. | May create PayFac, marketplace, sub-merchant, biller, agent, debt collection, or payment service implications. |
| `THEME-DOC04-014` | Payee-created requests may create fake obligation or collusion risk. | Payees and payers could create unsupported obligations without onboarding, evidence, relationship checks, and monitoring. |
| `THEME-DOC04-015` | Payer authorization is mandatory for payee-created requests. | Payee-created requests must not trigger funding, capture, or payout without payer review and authorization. |
| `THEME-DOC04-016` | Landlord-created rent requests are higher risk. | Rent may involve individual payees, high values, tenancy evidence, and disguised cashout risk. |
| `THEME-DOC04-017` | Payer/payee data visibility must be controlled. | Payees must not see sensitive payer funding, card, risk, or private profile information. |
| `THEME-DOC04-018` | Payee-created workflows increase operational load. | Onboarding, request review, disputes, evidence review, support, and monitoring require readiness. |

---

## 7. MVP Compliance Posture

For MVP, PayPlus should use a conservative launch posture.

MVP should be:

- limited by jurisdiction;
- limited by bill category;
- limited by payment method;
- limited by payout rail;
- limited by transaction amount and velocity;
- limited by payee type;
- limited by request creator type;
- limited by operational complexity;
- supported by PSP/acquirer and payout provider approval where possible;
- supported by manual review where automation is immature;
- supported by daily reconciliation;
- supported by enhanced launch monitoring.

MVP should avoid unless separately approved:

- ambiguous funds flows;
- unapproved jurisdictions;
- unapproved categories;
- user-to-self payments;
- unverified payees with immediate high-value payout;
- payee-created requests from unverified, restricted, or blocked payees;
- landlord-created rent requests without enhanced controls;
- payee-created invoice requests without evidence and payee verification;
- automatic payer charging based only on a payee-created request;
- payee modification of material terms after payer authorization without renewed authorization;
- crypto, gambling, gift card, stored value, investment, or cash-equivalent payments;
- cross-border payouts;
- FX;
- wallet or stored balance functionality;
- payout before funding certainty without approved controls;
- multi-card or multi-source funding unless specifically approved.

If payee-created requests are enabled, they must be:

- approved through `DOC-03` and this document;
- gated by payee onboarding and capability permissions;
- limited to approved payee types and categories;
- subject to payer review and authorization;
- subject to evidence standards equal to payer-created requests;
- subject to request-abuse monitoring;
- subject to payer/payee privacy boundaries;
- subject to manual review for high-risk cases;
- certified specifically for the request creator model.

---

## 8. Control Tiers

| Tier | Name | Meaning | Launch Impact |
| --- | --- | --- | --- |
| `T0` | Non-waivable blocker | Mandatory for legal, partner, security, financial, or user-protection reasons. | Cannot launch without completion. |
| `T1` | Critical launch control | Required for launch unless formally risk-accepted by authorized approvers. | Blocks launch unless remediated or accepted. |
| `T2` | Important operating control | Required for stable operation; may be completed shortly after launch with mitigation. | May launch with approved remediation plan. |
| `T3` | Scale or maturity control | Required before scaling, audit maturity, or expansion. | Does not block MVP, but blocks scale or expansion. |

Controls marked `T0 if enabled` or `T1 if enabled` apply only when the related feature is enabled.

For example, payee-created request controls become launch-blocking when payee-created requests are in MVP, pilot, or production scope.

---

## 9. Non-Waivable Launch Blockers

PayPlus must not launch MVP if any `T0` blocker is unresolved.

| Blocker ID | Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-001` | Regulatory role and licensing path for MVP jurisdiction and funds flow are assessed and approved. | Legal / Compliance |
| `BLK-DOC04-002` | PSP/acquirer approval or equivalent written confirmation exists for use case, funds flow, categories, and fee model. | Payments |
| `BLK-DOC04-003` | Payout provider and payout flow are approved, tested, and operationally supported. | Payments / Finance |
| `BLK-DOC04-004` | MVP bill categories are approved; restricted and prohibited categories are blocked or controlled. | Compliance / Product |
| `BLK-DOC04-005` | Fee, total charge, payment timing, refund/cancellation, and PayPlus role disclosures are implemented before authorization. | Legal / Product |
| `BLK-DOC04-006` | PCI scope and card data handling model are approved before production card processing. | Security |
| `BLK-DOC04-007` | Sanctions screening and escalation requirements applicable to MVP are implemented. | Compliance |
| `BLK-DOC04-008` | Baseline fraud, velocity, and anti-cashout controls are implemented. | Risk |
| `BLK-DOC04-009` | Daily settlement, payout, fee, refund, chargeback, and ledger reconciliation process is defined and tested. | Finance / Payments |
| `BLK-DOC04-010` | Refund, cancellation, payout failure, and chargeback handling procedures are defined. | Operations / Payments |
| `BLK-DOC04-011` | Incident escalation path and severity classification are defined. | Security / Operations |
| `BLK-DOC04-012` | Privacy notice, terms acceptance, data collection, and consent controls are implemented. | Privacy / Legal |
| `BLK-DOC04-013` | Critical evidence is stored in an approved repository and linked to launch certification. | Compliance |
| `BLK-DOC04-014` | Required approvers sign launch certification for the defined MVP scope. | Project Owner / Compliance |

Additional blockers apply if payee-created requests are enabled.

| Blocker ID | Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-015` | Payee-created request model is assessed and approved through `DOC-03`. | Legal / Compliance / Payments |
| `BLK-DOC04-016` | Payee onboarding, verification, sanctions, payout destination, and capability controls are implemented. | Compliance / Risk / Operations |
| `BLK-DOC04-017` | Payee-created requests cannot trigger funding, capture, or payout before payer review, disclosure acceptance, and explicit authorization. | Product / Payments / Engineering |
| `BLK-DOC04-018` | Payee-created request evidence requirements are defined, implemented, and tested. | Product / Compliance / Risk |
| `BLK-DOC04-019` | Payout gating prevents payout until payer authorization, funding success, evidence checks, payee verification, risk checks, and payout readiness are complete. | Payments / Risk / Finance |
| `BLK-DOC04-020` | Payer/payee privacy boundaries and RBAC are implemented and tested. | Privacy / Security |
| `BLK-DOC04-021` | Request abuse, fake obligation, self-payment, relationship, and collusion controls are implemented. | Risk / Compliance |
| `BLK-DOC04-022` | Landlord-created rent requests are blocked unless landlord onboarding, tenancy evidence, rent-specific controls, and partner/legal approval are complete. | Legal / Compliance / Risk |
| `BLK-DOC04-023` | Support, complaint, rejection, query, dispute, and payee request withdrawal procedures are defined. | Operations / Legal / Product |

---

## 10. Risk Acceptance

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

The following cannot be accepted for launch:

- no regulatory role assessment;
- no PSP/acquirer approval for core payment flow;
- no PCI scope decision before card processing;
- no fee and total-charge disclosure before authorization;
- no sanctions screening where required;
- no baseline fraud and anti-cashout controls;
- no payout and reconciliation process;
- no incident escalation path;
- no terms/privacy acceptance;
- no launch approval record.

The following cannot be accepted for payee-created request launch:

- no regulatory, partner, and role assessment;
- no approved payee onboarding and verification model;
- no payer authorization before funding, capture, or payout;
- no payee-created request evidence standard;
- no payout gating;
- no controls preventing blocked or unverified payees from creating requests;
- no payer/payee privacy boundary;
- no request abuse monitoring;
- no landlord onboarding and tenancy evidence controls if landlord-created rent requests are enabled;
- no support and dispute process.

---

## 11. Control Domains

| Domain ID | Domain | Primary Owner | Related Documents |
| --- | --- | --- | --- |
| `CD-DOC04-001` | Governance, certification, approvals | Compliance | DOC-00, DOC-20 |
| `CD-DOC04-002` | Regulatory role, licensing, exemptions | Legal / Compliance | DOC-03 |
| `CD-DOC04-003` | PSP, acquirer, card network, payout provider readiness | Payments | DOC-03, DOC-09, DOC-10 |
| `CD-DOC04-004` | Category eligibility and payee acceptability | Compliance / Product | DOC-03, DOC-12 |
| `CD-DOC04-005` | User onboarding, consent, eligibility | Product / Compliance | DOC-06, DOC-15 |
| `CD-DOC04-006` | Payee onboarding, verification, capabilities | Compliance / Risk / Operations | DOC-12, DOC-14 |
| `CD-DOC04-007` | Payee-created request creation, evidence, authorization, lifecycle, payout gating | Product / Compliance / Payments | DOC-06, DOC-09, DOC-12, DOC-14 |
| `CD-DOC04-008` | Landlord/rent evidence and enhanced review | Legal / Compliance / Risk | DOC-06, DOC-12, DOC-14 |
| `CD-DOC04-009` | AML, sanctions, financial crime | Compliance | DOC-14 |
| `CD-DOC04-010` | Fraud, abuse, velocity, relationship risk | Risk | DOC-14 |
| `CD-DOC04-011` | Consumer protection, disclosures, consent, receipts | Legal / Product | DOC-07, DOC-08 |
| `CD-DOC04-012` | Fees, pricing, tax, economics | Finance / Product | DOC-02, DOC-07 |
| `CD-DOC04-013` | Authorization, capture, settlement, funding | Payments / Engineering | DOC-09 |
| `CD-DOC04-014` | Payout, reconciliation, reserves, ledger | Finance / Payments | DOC-10, DOC-18 |
| `CD-DOC04-015` | Refunds, cancellations, chargebacks, disputes, withdrawals | Operations / Payments | DOC-11 |
| `CD-DOC04-016` | Support, complaints, escalation | Operations | DOC-08, DOC-11, DOC-21 |
| `CD-DOC04-017` | Security, PCI, access, authentication | Security / Engineering | DOC-19, DOC-16 |
| `CD-DOC04-018` | Privacy, data protection, retention, visibility | Privacy / Legal | DOC-15 |
| `CD-DOC04-019` | Reporting, recordkeeping, evidence, auditability | Compliance / Finance | DOC-18 |
| `CD-DOC04-020` | Vendor and partner oversight | Compliance / Legal / Payments | DOC-03 |
| `CD-DOC04-021` | Incident response and resilience | Security / Operations | DOC-21 |
| `CD-DOC04-022` | Change management and release governance | Engineering / Compliance | DOC-20 |
| `CD-DOC04-023` | Training and access certification | Compliance / Security | DOC-19, DOC-21 |

---

## 12. Minimum MVP Control Baseline

### 12.1 Regulatory and Partner Baseline

PayPlus must have:

- MVP jurisdiction defined;
- MVP funds flow diagram completed;
- PayPlus role documented;
- licensing path, exemption, or partner coverage assessed;
- PSP/acquirer approval obtained or documented;
- payout provider approval obtained or documented;
- approved bill categories documented;
- prohibited and restricted categories documented;
- MCC or classification confirmed where possible;
- fee model reviewed;
- settlement timing reviewed;
- reserve, holdback, and liquidity impact reviewed;
- request creator types documented;
- payee types documented;
- payee-created request model assessed if enabled.

### 12.2 Product and Disclosure Baseline

Before authorization, the product must show:

- bill amount;
- PayPlus service fee;
- taxes, if applicable;
- total amount charged;
- payee or biller identity;
- request origin, where applicable;
- expected processing or delivery timing;
- PayPlus role;
- cancellation and refund rules;
- payer responsibility for late fees or payee consequences where applicable;
- terms acceptance;
- privacy notice access.

The system must retain:

- disclosure version;
- acceptance timestamp;
- user or payer ID;
- transaction ID;
- request creator type;
- amount and fee shown;
- payment authorization record.

### 12.3 User and Payee Baseline

PayPlus must define:

- minimum user information;
- user eligibility rules;
- blocked user criteria;
- payee information required;
- payee verification method;
- payee onboarding method where payees can create requests;
- payee capability permissions;
- relationship or ownership checks where applicable;
- self-payment controls;
- high-risk payee escalation;
- prohibited payee categories;
- blocked, restricted, rejected, and unverified payee behavior.

### 12.4 Payee-Created Request Baseline

If enabled, PayPlus must implement:

- eligible payee types;
- approved request categories by payee type;
- request creator type tracking;
- payer identification or invitation controls;
- required request fields;
- required evidence by category;
- request-origin disclosure;
- payer review and authorization flow;
- payer rejection, query, dispute, expiry, and cancellation states;
- payee withdrawal rules before payer authorization;
- material term locks after payer authorization;
- renewed authorization for material changes;
- audit events;
- manual review triggers;
- payout gating;
- payer/payee privacy boundaries;
- support and escalation procedures.

### 12.5 Landlord/Rent Baseline

If rent requests are enabled, PayPlus must implement:

- landlord onboarding requirements;
- landlord identity or business verification;
- payout destination verification;
- property or rental reference capture;
- tenancy contract, lease agreement, rent schedule, or approved equivalent evidence;
- payer-landlord relationship validation where required;
- rent amount reasonableness checks where feasible;
- duplicate rent request detection;
- recurring or repeated rent controls;
- payout destination change review;
- self-payment, related-party, and collusion checks;
- manual review for first payment, high-value payment, changed payout destination, changed landlord details, or unusual pattern.

### 12.6 AML, Sanctions, Fraud, and Anti-Cashout Baseline

MVP must include:

- sanctions screening where required;
- adverse match review;
- blocked party escalation;
- transaction limits;
- daily and rolling user limits;
- new-user limits;
- card velocity limits;
- failed authorization velocity limits;
- payee velocity limits;
- payee concentration monitoring;
- self-payment detection;
- circular payment detection where feasible;
- payer-payee relationship checks where payee-created requests are enabled;
- request abuse monitoring where enabled;
- fake invoice or fake rent detection where applicable;
- suspicious refund monitoring;
- manual review queue;
- risk decision audit logs.

### 12.7 Payment, Payout, and Reconciliation Baseline

MVP must include:

- unique transaction IDs;
- parent-child linkage for multi-source funding, if enabled;
- request creator type linkage;
- authorization and capture logs;
- settlement status tracking;
- payout status tracking;
- payout readiness controls;
- payee-created request payout gating where enabled;
- fee ledger entries;
- refund ledger entries;
- chargeback ledger entries;
- daily reconciliation;
- unresolved exception log;
- payout failure process;
- refund failure process;
- chargeback evidence process.

### 12.8 Security, Privacy, and Access Baseline

MVP must include:

- PCI scope decision;
- tokenized card handling where applicable;
- no unnecessary storage of sensitive card data;
- encryption in transit;
- encryption at rest for sensitive data;
- role-based admin access;
- role-based payee access where enabled;
- payer/payee visibility boundaries where enabled;
- audit logs for sensitive actions;
- vulnerability review before launch;
- privacy notice;
- data map;
- retention approach;
- incident escalation path.

### 12.9 Operations Baseline

MVP must include:

- refund procedure;
- cancellation procedure;
- payout failure procedure;
- chargeback procedure;
- payer rejection, query, and dispute procedure where payee-created requests are enabled;
- payee request withdrawal procedure where enabled;
- complaint intake and escalation;
- payer and payee support macros where applicable;
- support macros for timing, fees, refunds, failures, request origin, and authorization;
- internal escalation contacts;
- incident severity levels;
- daily launch monitoring during initial production period.

---

## 13. Control Matrix

| Control ID | Tier | Domain | Control Objective | Type | Frequency | Owner | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `CTRL-DOC04-001` | `T0` | Governance | Maintain launch certification scope, approvers, and evidence package. | Directive | Per launch | Compliance | Launch package, approval log |
| `CTRL-DOC04-002` | `T0` | Regulatory | Confirm regulatory role and licensing path for jurisdiction, funds flow, payee type, and request creator model. | Preventive | Per launch / change | Legal / Compliance | DOC-03 assessment, legal memo |
| `CTRL-DOC04-003` | `T0` | Partner readiness | Confirm PSP/acquirer support for use case, categories, fees, funds flow, payee types, and request creator model. | Preventive | Per partner / change | Payments | Partner approval, contract |
| `CTRL-DOC04-004` | `T0` | Payout readiness | Confirm payout provider, rails, settlement timing, eligibility, and exception handling. | Preventive | Per launch / change | Payments / Finance | Payout approval, test evidence |
| `CTRL-DOC04-005` | `T0` | Category eligibility | Maintain and enforce approved, restricted, and prohibited categories. | Preventive | Per launch / monthly | Compliance / Product | Category register, config |
| `CTRL-DOC04-006` | `T1` | Payee controls | Verify payee eligibility before payout. | Preventive | Per payee | Compliance / Operations | Verification record |
| `CTRL-DOC04-007` | `T1` | User controls | Capture required user information and terms/privacy consent. | Preventive | Per user | Product / Compliance | User profile, consent logs |
| `CTRL-DOC04-008` | `T0` | Sanctions | Screen required parties and escalate potential matches. | Preventive / Detective | Onboarding / ongoing | Compliance | Screening logs |
| `CTRL-DOC04-009` | `T0` | Fraud / Anti-cashout | Apply transaction limits, velocity rules, and self-payment controls. | Preventive / Detective | Real-time / daily | Risk | Rule config, alerts |
| `CTRL-DOC04-010` | `T1` | Manual review | Route high-risk transactions, users, payees, categories, or requests to manual review. | Preventive | Per trigger | Risk / Operations | Case logs |
| `CTRL-DOC04-011` | `T0` | Disclosures | Display amount, fee, total, timing, role, request origin where applicable, and refund/cancellation terms before authorization. | Preventive | Per transaction | Product / Legal | Screenshots, logs |
| `CTRL-DOC04-012` | `T0` | Authorization | Capture payer authorization and immutable transaction details. | Preventive | Per transaction | Product / Engineering | Authorization logs |
| `CTRL-DOC04-013` | `T1` | Fee controls | Ensure fee calculation matches approved pricing, including payee-side fees where applicable. | Preventive / Detective | Per transaction / daily | Finance / Product | Pricing config, reports |
| `CTRL-DOC04-014` | `T0` | Reconciliation | Reconcile PSP settlement, fees, payouts, refunds, chargebacks, reserves, ledger, and bank records. | Detective | Daily | Finance / Payments | Reconciliation report |
| `CTRL-DOC04-015` | `T0` | Payout exceptions | Detect and resolve failed, delayed, returned, or misdirected payouts. | Corrective | Daily / exception | Payments / Operations | Exception log |
| `CTRL-DOC04-016` | `T0` | Refunds | Process refunds according to approved rules and ledger treatment. | Preventive / Corrective | Per refund | Operations / Payments | Refund record |
| `CTRL-DOC04-017` | `T1` | Chargebacks | Track, evidence, and respond to chargebacks within deadlines. | Corrective | Per dispute | Operations / Payments | Dispute case |
| `CTRL-DOC04-018` | `T1` | Complaints | Log, classify, investigate, and resolve payer and payee complaints. | Corrective | Per complaint | Operations | Complaint register |
| `CTRL-DOC04-019` | `T0` | PCI | Approve PCI scope and card data handling model before card processing. | Preventive | Launch / annual / change | Security | PCI scope document |
| `CTRL-DOC04-020` | `T1` | Access control | Restrict admin and sensitive data access by role. | Preventive | Continuous / quarterly | Security / Engineering | Role matrix, review logs |
| `CTRL-DOC04-021` | `T1` | Audit logging | Log sensitive admin, payment, payout, refund, risk, support, payee onboarding, and request actions. | Detective | Continuous | Engineering / Security | Audit logs |
| `CTRL-DOC04-022` | `T0` | Privacy | Provide privacy notice and capture required consent. | Preventive | Per user / change | Privacy / Product | Consent logs |
| `CTRL-DOC04-023` | `T1` | Retention | Retain and delete records according to approved schedule. | Preventive / Corrective | Continuous / periodic | Privacy / Engineering | Retention policy |
| `CTRL-DOC04-024` | `T1` | Vendor diligence | Review material vendors and payment partners before production use. | Preventive | Per vendor / annual | Compliance / Security / Legal | Due diligence file |
| `CTRL-DOC04-025` | `T0` | Incident escalation | Maintain incident severity levels, escalation contacts, and notification process. | Corrective | Per incident / launch | Security / Operations | Incident runbook |
| `CTRL-DOC04-026` | `T1` | Change management | Review product, risk, compliance, and technical changes before release. | Preventive | Per release | Engineering / Compliance | Change tickets |
| `CTRL-DOC04-027` | `T1` | Regulatory/partner monitoring | Monitor regulatory, card network, PSP, acquirer, payout provider, and contractual changes. | Detective | Monthly / event | Legal / Compliance / Payments | Monitoring log |
| `CTRL-DOC04-028` | `T2` | Training | Provide role-based compliance, security, fraud, onboarding, and support training. | Directive | On hire / annual | Compliance / Security | Training records |
| `CTRL-DOC04-029` | `T2` | Control testing | Test design and operating effectiveness of key controls. | Detective | Quarterly / annual | Compliance / QA | Test results |
| `CTRL-DOC04-030` | `T3` | SOC 2 readiness | Prepare for formal security/compliance audit maturity if commercially required. | Directive | Pre-scale / annual | Security | Readiness plan |
| `CTRL-DOC04-031` | `T1 if enabled` | Payee onboarding | Onboard and verify payees before granting request creation or payout capabilities. | Preventive | Per payee | Compliance / Risk / Operations | Onboarding case |
| `CTRL-DOC04-032` | `T1 if enabled` | Payee capabilities | Assign payee capabilities by type, verification status, risk, category permissions, and launch scope. | Preventive | Per payee / change | Product / Risk / Compliance | Capability config |
| `CTRL-DOC04-033` | `T1 if enabled` | Request eligibility | Prevent blocked, restricted, rejected, or unverified payees from creating or sending requests. | Preventive | Per request | Product / Engineering / Compliance | Permission logs |
| `CTRL-DOC04-034` | `T1 if enabled` | Request evidence | Require sufficient evidence for payee-created bill, invoice, fee, or rent requests. | Preventive | Per request | Product / Compliance / Operations | Evidence record |
| `CTRL-DOC04-035` | `T0 if enabled` | Payer authorization | Prevent funding, capture, or payout until payer review, disclosure acceptance, and authorization are complete. | Preventive | Per request | Product / Payments / Engineering | Authorization logs |
| `CTRL-DOC04-036` | `T1 if enabled` | Request lifecycle | Maintain lifecycle states for pending, viewed, accepted, rejected, queried, disputed, expired, cancelled, paid, and withdrawn. | Preventive / Detective | Per request | Product / Engineering | Status history |
| `CTRL-DOC04-037` | `T1 if enabled` | Material change lock | Lock material request terms after authorization or require renewed payer authorization. | Preventive | Per change | Product / Engineering | Change logs |
| `CTRL-DOC04-038` | `T1 if enabled` | Relationship risk | Monitor suspicious, circular, self-payment, collusive, related-party, or unusual payer-payee relationships. | Preventive / Detective | Per request / daily | Risk | Alerts, cases |
| `CTRL-DOC04-039` | `T1 if enabled` | Request abuse monitoring | Monitor excessive requests, repeated rejection, fake invoices, duplicate rent, complaints, and unusual patterns. | Detective | Daily / weekly | Risk / Operations | Monitoring report |
| `CTRL-DOC04-040` | `T1 if rent enabled` | Landlord/rent controls | Apply landlord verification, tenancy evidence, duplicate rent, amount reasonableness, payout change, and recurring pattern controls. | Preventive / Detective | Per request / ongoing | Risk / Compliance / Operations | Rent review record |
| `CTRL-DOC04-041` | `T1 if enabled` | Privacy boundary | Enforce payer/payee visibility rules and prevent unauthorized access to sensitive data. | Preventive | Continuous | Privacy / Security / Engineering | RBAC test, logs |
| `CTRL-DOC04-042` | `T1 if enabled` | Payer response | Support payer rejection, query, dispute, or clarification before authorization without funds movement. | Preventive / Corrective | Per request | Operations / Product | Case log |
| `CTRL-DOC04-043` | `T1 if enabled` | Payee withdrawal | Support payee withdrawal before payer authorization where permitted. | Corrective | Per withdrawal | Product / Operations | Withdrawal log |
| `CTRL-DOC04-044` | `T1 if enabled` | Evidence package | Link request evidence, authorization, disclosure, communication, payment, payout, refund, dispute, and reconciliation records. | Detective | Per transaction | Compliance / Engineering / Operations | Evidence package |
| `CTRL-DOC04-045` | `T1 if enabled` | Support visibility | Ensure support tooling distinguishes payer-side and payee-side visibility and permissions. | Preventive | Continuous / case | Operations / Security | Role matrix, cases |

---

## 14. Evidence and Systems of Record

Evidence must be stored in approved systems of record.

| Evidence Type | System of Record | Owner |
| --- | --- | --- |
| Legal assessment | Legal repository / compliance folder | Legal |
| Regulatory role approval | Compliance evidence repository | Compliance |
| PSP/acquirer approval | Contract repository / partner folder | Payments / Legal |
| Payout provider approval | Contract repository / partner folder | Payments / Legal |
| Category approval | Compliance register / product configuration | Compliance / Product |
| Fee approval | Finance model / pricing configuration / approval ticket | Finance / Product |
| UI disclosure evidence | QA repository / screenshot archive | Product / Legal |
| Terms and privacy acceptance | Application database / audit log | Product / Engineering |
| User onboarding record | Application database | Product |
| Payee onboarding and verification | Compliance case system / operations queue / application database | Compliance / Operations |
| Payee capability record | Application database / admin console | Product / Risk |
| Payee-created request record | Application database / transaction system | Product / Engineering |
| Request, invoice, rent, or bill evidence | Evidence repository / document storage / application database | Product / Compliance / Risk |
| Payer response and authorization | Application database / audit log / payment platform | Product / Payments / Engineering |
| Payer/payee communication | Notification system / support system | Operations / Product |
| Dispute, query, or complaint | Support system / case management tool | Operations |
| Sanctions screening | Screening tool / compliance case system | Compliance |
| Fraud and relationship risk decision | Risk engine / case management tool | Risk / Operations |
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

## 15. Certification Roadmap

| Phase | Name | Objective | Required Before Exit |
| --- | --- | --- | --- |
| `PH-DOC04-001` | Discovery | Identify scope, jurisdiction, funds flow, categories, partners, payee types, request creator types, and obligations. | Draft `DOC-03`, product scope, obligation inventory. |
| `PH-DOC04-002` | MVP Control Design | Define T0/T1 controls, owners, evidence, blockers, and evidence plan. | Approved control matrix and evidence plan. |
| `PH-DOC04-003` | MVP Control Build | Implement required product, partner, risk, payment, security, privacy, payee, request lifecycle, and operational controls. | T0 controls implemented; T1 controls implemented or risk-accepted. |
| `PH-DOC04-004` | MVP Control Test | Test critical controls and document exceptions. | T0 controls tested; critical exceptions closed. |
| `PH-DOC04-005` | MVP Certification | Assemble launch package and obtain approvals. | Launch certification signed. |
| `PH-DOC04-006` | Controlled Launch | Launch with limited scope and enhanced monitoring. | Daily monitoring, issue tracking, reconciliation, request-abuse monitoring, and support review active. |
| `PH-DOC04-007` | Stabilization | Validate operating effectiveness and remediate findings. | Initial post-launch control review completed. |
| `PH-DOC04-008` | Scale Readiness | Add T2/T3 maturity controls for higher volume or enterprise readiness. | Control testing, vendor reassessment, SOC 2/PCI maturity as needed. |
| `PH-DOC04-009` | Expansion Certification | Re-certify for new jurisdictions, categories, partners, payment methods, payee types, request creator models, or funds-flow changes. | Expansion certification approved. |

---

## 16. Launch Certification Package

The launch certification package must include:

- launch scope;
- jurisdiction scope;
- category scope;
- user and payee scope;
- payee type scope;
- request creator type scope;
- payment and payout method scope;
- funds flow diagram;
- regulatory role assessment;
- licensing, exemption, or partner coverage analysis;
- PSP/acquirer approval evidence;
- payout provider approval evidence;
- MCC or classification evidence;
- category approval evidence;
- restricted and prohibited category list;
- fee model approval;
- consumer disclosure evidence;
- request-origin disclosure evidence where applicable;
- payer authorization evidence design where applicable;
- terms and privacy evidence;
- sanctions control evidence;
- fraud and anti-cashout control evidence;
- relationship risk control evidence where applicable;
- request abuse monitoring evidence where applicable;
- user and payee onboarding evidence;
- payee capability control evidence where applicable;
- payee-created request evidence standard where applicable;
- landlord/rent evidence standard where applicable;
- PCI scope and security evidence;
- payer/payee privacy boundary evidence where applicable;
- partner due diligence evidence;
- contract approval evidence;
- settlement, reserve, and liquidity evidence;
- payout gating test evidence;
- reconciliation test evidence;
- refund and chargeback readiness evidence;
- payer rejection, query, dispute, and payee withdrawal procedure evidence where applicable;
- support and complaint readiness evidence;
- incident escalation evidence;
- QA evidence for compliance-critical flows;
- control matrix with statuses;
- open exceptions and remediation plan;
- accepted risks;
- approver signatures.

---

## 17. Launch Readiness Gates

| Gate ID | Tier | Gate | Acceptance Condition | Owner |
| --- | --- | --- | --- | --- |
| `GATE-DOC04-001` | `T0` | Launch scope locked | MVP jurisdiction, categories, payment methods, payout methods, partners, payee types, and request creator types are defined. | Project Owner |
| `GATE-DOC04-002` | `T0` | Regulatory role approved | Regulatory role and licensing path are approved for the MVP flow, payee type, and request creator model. | Legal / Compliance |
| `GATE-DOC04-003` | `T0` | PSP/acquirer approval obtained | PSP/acquirer confirms support for use case, categories, fee model, funds flow, payee types, and request creator model. | Payments |
| `GATE-DOC04-004` | `T0` | Payout readiness approved | Payout provider, rails, settlement timing, payee payout eligibility, and exceptions are approved and tested. | Payments / Finance |
| `GATE-DOC04-005` | `T0` | Category controls implemented | Approved, restricted, and prohibited category controls are implemented. | Compliance / Product |
| `GATE-DOC04-006` | `T1` | User and payee controls ready | Onboarding, consent, verification, screening, eligibility, and payee capability controls are implemented. | Product / Compliance |
| `GATE-DOC04-007` | `T0` | Sanctions controls ready | Required screening, escalation, and recordkeeping controls are implemented. | Compliance |
| `GATE-DOC04-008` | `T0` | Fraud and anti-cashout controls ready | Baseline limits, velocity, self-payment, payee, relationship risk, and manual review controls are implemented. | Risk |
| `GATE-DOC04-009` | `T0` | Fee and disclosure controls ready | Fee, total charge, timing, role, request origin, refund, and cancellation disclosures are approved and tested. | Legal / Product |
| `GATE-DOC04-010` | `T0` | Authorization controls ready | Authorization, capture, consent, payer acceptance where applicable, and transaction logging are tested. | Payments / Engineering |
| `GATE-DOC04-011` | `T0` | Reconciliation controls ready | Settlement, payout, fee, refund, chargeback, reserve, ledger, request creator type, and bank reconciliation are tested. | Finance / Payments |
| `GATE-DOC04-012` | `T0` | Security and PCI ready | PCI scope, card data model, access controls, and security review are complete. | Security |
| `GATE-DOC04-013` | `T0` | Privacy controls ready | Privacy notice, data map, consent, retention, and payer/payee visibility controls are ready. | Privacy / Legal |
| `GATE-DOC04-014` | `T1` | Support and complaint controls ready | Support, complaints, disputes, refunds, chargebacks, payer queries, and payee withdrawal procedures are ready. | Operations |
| `GATE-DOC04-015` | `T0` | Incident escalation ready | Incident severity model and escalation paths are documented. | Security / Operations |
| `GATE-DOC04-016` | `T0` | Evidence repository complete | Required T0 evidence is stored and linked to launch certification. | Compliance |
| `GATE-DOC04-017` | `T0` | Critical exceptions closed | T0 exceptions are closed; T1 exceptions are closed or accepted. | Compliance |
| `GATE-DOC04-018` | `T0` | Launch certification approved | Required approvers sign the certification package. | Project Owner / Compliance |
| `GATE-DOC04-019` | `T0 if enabled` | Payee-created request model approved | Flow, role, partner approval, regulatory assessment, payer authorization, evidence, risk, privacy, payout, and reconciliation controls are approved. | Legal / Compliance / Payments |
| `GATE-DOC04-020` | `T0 if enabled` | Payee onboarding controls ready | Payee onboarding, verification, sanctions, payout destination, status, capabilities, and offboarding controls are implemented and tested. | Compliance / Risk / Operations |
| `GATE-DOC04-021` | `T0 if enabled` | Payer authorization ready | Payee-created requests cannot fund, capture, or pay out until payer review, disclosure acceptance, and authorization are complete. | Product / Payments / Engineering |
| `GATE-DOC04-022` | `T1 if enabled` | Request evidence controls ready | Required evidence by category is implemented, reviewable, retained, and linked to lifecycle records. | Product / Compliance / Risk |
| `GATE-DOC04-023` | `T1 if enabled` | Request abuse controls ready | Fake obligation, duplicate request, relationship, collusion, spam, complaint, and rejection-rate monitoring are implemented. | Risk / Compliance |
| `GATE-DOC04-024` | `T1 if enabled` | Privacy and support controls ready | Payer/payee visibility, support permissions, communications, disputes, and withdrawal procedures are tested. | Privacy / Security / Operations |
| `GATE-DOC04-025` | `T0 if rent enabled` | Landlord/rent controls ready | Landlord verification, tenancy evidence, rent risk controls, relationship checks, and partner/legal approval are complete. | Legal / Compliance / Risk |

---

## 18. Control Testing

Critical controls must be tested before launch.

Required testing includes:

- fee and total amount display before authorization;
- consent logging with version and timestamp;
- prohibited category blocking;
- payee verification before payout;
- payee capability gating;
- eligible payee-created request creation;
- payee-created request evidence capture;
- payer review and authorization before funding, capture, or payout;
- payer rejection, query, dispute, or expiry without funds movement;
- payee withdrawal before payer authorization where permitted;
- material change lock or renewed authorization;
- landlord/rent evidence where enabled;
- payer-payee relationship risk controls;
- request abuse monitoring;
- payer/payee privacy boundary;
- support visibility permissions;
- sanctions escalation and blocking;
- fraud and velocity rules;
- self-payment detection;
- authorization logging;
- payout success and failure paths;
- payout gating;
- reconciliation of settlement, payout, fee, refund, request creator type, and ledger records;
- refund flow;
- chargeback evidence package;
- access controls;
- audit logs;
- incident escalation.

---

## 19. Exception and Remediation Management

Control exceptions must be logged.

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

`T0` exceptions cannot be accepted for MVP launch.

`T0 if enabled` exceptions cannot be accepted for launch of the applicable enabled feature.

---

## 20. Regulatory and Partner Change Management

Material changes require reassessment.

Triggers include:

- new jurisdiction;
- new bill category;
- new payee type;
- new request creator type;
- payee-created request enablement;
- landlord-created rent request enablement;
- payee-created invoice or fee request enablement;
- change to payee onboarding;
- change to payee capability permissions;
- change to payer identification or invitation mechanism;
- change to payer acceptance, rejection, query, or dispute process;
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
- AML or sanctions requirement change;
- card network, PSP, acquirer, payout provider, bank, or legal requirement change;
- material fraud, chargeback, complaint, payout failure, request abuse, onboarding failure, or reconciliation issue.

Compliance must determine whether recertification is required before release.

---

## 21. Vendor and Partner Oversight

Material vendors and partners must be reviewed before production use.

Payment partner review should cover:

- regulatory coverage;
- PSP/acquirer approval;
- card network compliance;
- payee-created request support;
- payee onboarding or sub-merchant support;
- payout capability;
- settlement timing;
- reserves and holdbacks;
- chargebacks and disputes;
- refunds;
- reporting and reconciliation;
- privacy and security;
- business continuity;
- incident and SLA process;
- pricing and reserve terms;
- annual or risk-based reassessment.

---

## 22. Training and Awareness

Before launch, relevant personnel should receive role-based training on:

- PayPlus product and funds flow;
- approved, restricted, and prohibited categories;
- request creator type and request origin;
- fee and disclosure rules;
- user and payee eligibility;
- payee onboarding and capability permissions;
- payer authorization for payee-created requests;
- sanctions escalation;
- fraud and anti-cashout red flags;
- payer-payee relationship and collusion red flags;
- fake invoice and fake rent red flags where applicable;
- manual review procedures;
- refund and cancellation handling;
- payer rejection, query, dispute, and payee withdrawal where applicable;
- chargeback evidence handling;
- complaint escalation;
- payer/payee privacy and data handling;
- security and access obligations;
- incident escalation.

Training records must be retained.

---

## 23. Monitoring and Reporting

MVP launch should include enhanced monitoring.

| Area | Metrics |
| --- | --- |
| Payments | Authorization rate, capture failures, payment failures, processor errors. |
| Payouts | Payout success rate, payout failures, delayed payouts, returned payouts. |
| Payee onboarding | Applications, approvals, rejections, pending reviews, verification failures, payout destination failures. |
| Payee-created requests | Sent, viewed, accepted, rejected, queried, disputed, expired, withdrawn, and paid requests. |
| Rent requests | Landlord approvals, tenancy evidence failures, duplicate rent signals, relationship alerts, rent amount exceptions. |
| Reconciliation | Unmatched transactions, settlement breaks, payout breaks, fee breaks, request creator type mismatches. |
| Fraud | Rule triggers, manual review queue, blocked transactions, suspicious payees, suspicious requests. |
| Anti-cashout | Self-payment alerts, relationship alerts, payee concentration, suspicious refunds, collusion indicators. |
| Sanctions | Screening hits, pending reviews, blocked parties. |
| Refunds | Refund volume, failure rate, reasons. |
| Chargebacks | New disputes, reason codes, exposure amount, evidence availability. |
| Complaints | Complaint volume, payer complaints, payee complaints, request-origin complaints, SLA, escalations. |
| Security | Incidents, access anomalies, critical vulnerabilities. |
| Privacy | Consent errors, visibility issues, data request issues, deletion exceptions. |
| Finance | Gross volume, fees, reserves, losses, margin variance. |

Monitoring cadence:

| Period | Cadence |
| --- | --- |
| First 2 weeks after launch | Daily review |
| Weeks 3–8 | At least weekly review |
| After stabilization | Monthly governance review, unless risk indicators require more frequent review |

If payee-created requests are enabled, request abuse, payer rejection/dispute, payee complaint, onboarding exception, and payer/payee privacy metrics must be monitored.

---

## 24. Governance Forums

| Forum | Frequency | Purpose | Participants |
| --- | --- | --- | --- |
| MVP Launch Readiness Review | Weekly pre-launch | Track gates, blockers, evidence, and risk acceptance. | Product, Compliance, Legal, Payments, Risk, Security, Finance, Operations, Engineering |
| Payee-Created Request Readiness Review | Weekly pre-launch if enabled / event-driven | Track payee onboarding, payer authorization, evidence, rent controls, abuse monitoring, privacy, support, and partner approval. | Product, Compliance, Legal, Payments, Risk, Security, Privacy, Finance, Operations, Engineering |
| Daily Launch Monitoring | Daily during initial launch | Review live metrics, incidents, settlement, payout, fraud, complaints, onboarding, requests, and exceptions. | Compliance, Risk, Payments, Finance, Operations, Engineering |
| Risk and Compliance Review | Monthly | Review metrics, exceptions, remediation, incidents, request abuse, payee risk, and regulatory changes. | Compliance, Legal, Risk, Security, Operations |
| Payments and Reconciliation Review | Weekly / Monthly | Review settlement, payout, chargebacks, reserves, reconciliation, request creator issues, and partner issues. | Payments, Finance, Operations, Engineering |
| Security and Privacy Review | Monthly / Quarterly | Review security, access, incidents, privacy, payer/payee visibility, and vendor security. | Security, Privacy, Engineering, Legal |
| Vendor and Partner Review | Quarterly / Annual | Review vendor and partner performance, attestations, incidents, payee-created request support, and renewals. | Compliance, Legal, Security, Payments, Finance |
| Expansion Certification Review | Event-driven | Approve new jurisdictions, categories, partners, payment methods, payee types, request creator models, or funds-flow changes. | Project Owner, Legal, Compliance, Payments, Risk, Security, Privacy, Finance |

---

## 25. Relationship to DOC-03 and DOC-20

`DOC-03` identifies regulatory, PSP/acquirer, partner, category, payee type, request creator model, and funds-flow risks.

`DOC-04` defines how PayPlus controls and certifies readiness against those risks.

`DOC-04` must not override `DOC-03`.

If `DOC-03` identifies an unresolved critical issue, `DOC-04` must:

- block launch;
- require remediation;
- require formal risk acceptance, if permitted; or
- narrow launch scope.

`DOC-20 Testing, UAT, Release & Go-Live Checklist` must convert `DOC-04` controls into executable go/no-go criteria, including:

- applicable `T0` and `T1` controls;
- applicable `T0 if enabled` and `T1 if enabled` controls;
- test case references;
- evidence links;
- owners;
- status;
- open exceptions;
- accepted risks;
- approver signatures.

No launch should proceed if `DOC-20` shows unresolved `T0` gaps.

No payee-created request feature should launch if `DOC-20` shows unresolved `T0 if enabled` gaps for that feature.

---

## 26. Key Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC04-001` | PayPlus will launch with limited MVP scope. | Project Owner | Open |
| `ASM-DOC04-002` | PayPlus will require documented regulatory and partner approval before production launch. | Legal / Payments | Open |
| `ASM-DOC04-003` | PSP/acquirer requirements will materially affect allowable flows, categories, fees, MCC/classification, payee types, and request creator models. | Payments | Open |
| `ASM-DOC04-004` | MVP will not include wallet, stored value, FX, cross-border payout, or unrestricted user-generated payees unless separately approved. | Product / Legal | Open |
| `ASM-DOC04-005` | Multi-card or multi-source funding requires separate approval and may be excluded from MVP. | Product / Payments | Open |
| `ASM-DOC04-006` | PCI scope will depend on final card data handling architecture. | Security | Open |
| `ASM-DOC04-007` | Fraud and anti-cashout controls are required even if formal AML obligations are limited. | Risk / Compliance | Open |
| `ASM-DOC04-008` | Daily reconciliation is required for MVP. | Finance / Payments | Open |
| `ASM-DOC04-009` | Evidence will be retained in approved systems of record. | Compliance | Open |
| `ASM-DOC04-010` | New jurisdictions, categories, partners, payee types, request creator models, or funds-flow changes require recertification. | Compliance | Open |
| `ASM-DOC04-011` | Payee-created request capability may be included only if onboarding, evidence, authorization, risk, payout, reconciliation, privacy, and support controls are approved. | Product / Compliance / Risk | Open |
| `ASM-DOC04-012` | Payer authorization remains mandatory for all payee-created requests. | Product / Legal / Payments | Open |
| `ASM-DOC04-013` | Landlord-created rent requests require enhanced onboarding, tenancy evidence, and relationship-risk controls if enabled. | Legal / Compliance / Risk | Open |
| `ASM-DOC04-014` | Payee-created requests will not create wallet, stored-value, cashout, or unrestricted transfer functionality. | Product / Legal / Compliance | Open |
| `ASM-DOC04-015` | Payee-created request controls may require additional PSP/acquirer, payout provider, and partner confirmations. | Payments / Compliance | Open |
| `ASM-DOC04-016` | Payer/payee privacy boundaries must be defined before payee-created requests are enabled. | Privacy / Security | Open |

---

## 27. Key Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC04-001` | T0 blockers cannot be waived for MVP launch. | Prevents unacceptable legal, partner, payment, security, or user-protection gaps. | Project Owner / Compliance |
| `CON-DOC04-002` | No production card processing without approved PSP/acquirer and PCI scope. | Blocks card launch until partner and security readiness are complete. | Payments / Security |
| `CON-DOC04-003` | No production payout without payout readiness and reconciliation controls. | Blocks payout launch until operations and finance controls are ready. | Payments / Finance |
| `CON-DOC04-004` | No restricted category launch without explicit approval. | Prevents unsupported or high-risk use cases. | Compliance / Product |
| `CON-DOC04-005` | Fee model cannot launch without legal/product disclosure approval. | Prevents consumer protection and partner rule violations. | Legal / Product |
| `CON-DOC04-006` | Material changes require reassessment before release. | Prevents stale approvals and control gaps. | Compliance / Engineering |
| `CON-DOC04-007` | Control evidence must be retained and retrievable. | Enables certification, audit, and partner review. | Compliance |
| `CON-DOC04-008` | Launch approval is scope-specific. | Prevents approval reuse for unassessed flows or categories. | Compliance |
| `CON-DOC04-009` | T1 exceptions require formal risk acceptance and remediation plan. | Prevents unmanaged launch risk. | Compliance |
| `CON-DOC04-010` | Daily monitoring is required during controlled launch. | Enables early detection of payment, fraud, payout, request-abuse, and support issues. | Operations / Compliance |
| `CON-DOC04-011` | Payee-created requests cannot launch without approved payee onboarding and verification controls. | Prevents cashout and fake obligation risk. | Product / Compliance / Risk |
| `CON-DOC04-012` | Payee-created requests cannot trigger funding, capture, or payout without payer authorization. | Prevents unauthorized payment and consumer harm. | Product / Payments / Legal |
| `CON-DOC04-013` | Payee-created requests must meet evidence and risk controls equivalent to payer-created requests. | Prevents weakened controls based on request origin. | Compliance / Risk |
| `CON-DOC04-014` | Landlord-created rent requests cannot launch without landlord onboarding, tenancy evidence, and rent-specific controls. | Prevents rent-based cashout and collusion risk. | Legal / Compliance / Risk |
| `CON-DOC04-015` | Payer/payee data visibility controls must be implemented before payee-created request launch. | Prevents privacy, security, and trust failures. | Privacy / Security |
| `CON-DOC04-016` | Payee-created request functionality must be feature-gated by scope, payee type, category, risk status, and partner approval. | Prevents unsupported feature exposure. | Product / Engineering / Compliance |

---

## 28. Key Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
| --- | --- | --- | --- | --- |
| `DEP-DOC04-001` | Completed or substantially completed `DOC-03` assessment. | Regulatory, partner, category, payee type, request creator model, and funds-flow control design. | Legal / Compliance / Payments | Open |
| `DEP-DOC04-002` | MVP product scope. | Launch certification scope. | Product | Open |
| `DEP-DOC04-003` | MVP jurisdiction. | Legal, privacy, AML, disclosure, and recordkeeping controls. | Legal / Project Owner | Open |
| `DEP-DOC04-004` | MVP bill categories. | Category approval, risk controls, and partner approval. | Product / Compliance | Open |
| `DEP-DOC04-005` | MVP funds flow diagram. | Regulatory, partner, payout, and reconciliation controls. | Product / Payments | Open |
| `DEP-DOC04-006` | PSP/acquirer selection and approval. | Card processing readiness. | Payments | Open |
| `DEP-DOC04-007` | Payout provider selection and approval. | Payout readiness. | Payments | Open |
| `DEP-DOC04-008` | Fee model. | Fee disclosure, pricing, margin, and partner review. | Product / Finance | Open |
| `DEP-DOC04-009` | Card data architecture. | PCI scope and security readiness. | Security / Engineering | Open |
| `DEP-DOC04-010` | User and payee onboarding model. | Verification, consent, screening, and anti-cashout controls. | Product / Compliance | Open |
| `DEP-DOC04-011` | Risk rules and review tools. | Fraud, velocity, relationship risk, request abuse, and manual review controls. | Risk / Engineering | Open |
| `DEP-DOC04-012` | Terms, privacy notice, and disclosure drafts. | Consumer protection and privacy readiness. | Legal / Product | Open |
| `DEP-DOC04-013` | Ledger and reporting design. | Reconciliation, evidence, and monitoring. | Finance / Engineering | Open |
| `DEP-DOC04-014` | Operations SOPs. | Refunds, cancellations, chargebacks, complaints, payout exceptions, payer queries, and payee withdrawal. | Operations | Open |
| `DEP-DOC04-015` | Evidence repository. | Certification package and auditability. | Compliance / Security | Open |
| `DEP-DOC04-016` | QA/UAT test evidence. | Launch certification. | Product / Engineering / QA | Open |
| `DEP-DOC04-017` | Partner contracts and vendor due diligence. | Partner readiness and vendor oversight. | Legal / Payments / Compliance | Open |
| `DEP-DOC04-018` | Payee onboarding requirements. | Payee-created request controls, payout readiness, sanctions, verification, and capability gating. | Product / Compliance / Risk | Open |
| `DEP-DOC04-019` | Payee type taxonomy and capability model. | Determine which payees can create which requests under which controls. | Product / Risk / Compliance | Open |
| `DEP-DOC04-020` | Request creator type model. | Scope gating, regulatory assessment, disclosure, reporting, and reconciliation. | Product / Payments / Legal | Open |
| `DEP-DOC04-021` | Landlord/rent verification standard. | Landlord-created rent request controls. | Product / Legal / Risk | Open |
| `DEP-DOC04-022` | Invoice evidence and payee-created request evidence standard. | Payee-created invoice, fee, bill, and rent request controls. | Product / Compliance / Risk | Open |
| `DEP-DOC04-023` | Payer identification and invitation mechanism. | Payee-created request delivery, privacy, consent, and security controls. | Product / Engineering / Privacy | Open |
| `DEP-DOC04-024` | Payer acceptance, rejection, query, and dispute process. | Payer authorization, support, dispute, and operations controls. | Product / Operations / Legal | Open |
| `DEP-DOC04-025` | Payer/payee data visibility rules. | Privacy, RBAC, support tooling, and communication controls. | Privacy / Security / Product | Open |
| `DEP-DOC04-026` | Payee-created request monitoring and reporting requirements. | Request abuse, fake obligation, collusion, complaint, rejection, and chargeback monitoring. | Risk / Compliance / Operations | Open |

---

## 29. Key Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC04-001` | PayPlus launches without clear regulatory role or licensing path. | Regulatory breach, suspension, partner termination. | T0 regulatory role and licensing gate. | Legal / Compliance | Open |
| `RISK-DOC04-002` | PSP/acquirer does not support actual PayPlus flow. | Processing disruption, fines, reserves, termination. | Written partner approval and contract review. | Payments / Legal | Open |
| `RISK-DOC04-003` | Category is misclassified or unsupported. | Partner rejection, chargebacks, compliance risk. | Approved/restricted/prohibited category controls. | Compliance / Product | Open |
| `RISK-DOC04-004` | Transaction is treated as quasi-cash, money transfer, account funding, or cash advance unexpectedly. | Higher costs, complaints, issuer declines. | MCC/classification review and disclosures. | Payments / Legal | Open |
| `RISK-DOC04-005` | Fee disclosure is incomplete or misleading. | Complaints, regulatory risk, refund exposure. | T0 disclosure testing and evidence. | Legal / Product | Open |
| `RISK-DOC04-006` | User routes funds to self or collusive payee. | Cashout, fraud, loss. | Payee verification, self-payment detection, limits. | Risk / Compliance | Open |
| `RISK-DOC04-007` | Payout occurs before funding certainty and later chargeback creates loss. | Financial loss and liquidity stress. | Settlement review, reserves, limits, risk rules. | Finance / Risk | Open |
| `RISK-DOC04-008` | Multi-source funding causes refund, chargeback, and reconciliation failures. | Operational breaks and user harm. | Exclude from MVP or require separate certification. | Product / Payments | Open |
| `RISK-DOC04-009` | Reconciliation fails to detect settlement or payout breaks. | Financial loss and inaccurate reporting. | Daily reconciliation and exception management. | Finance / Payments | Open |
| `RISK-DOC04-010` | PCI scope is underestimated. | Security breach, compliance failure, remediation cost. | PCI scope review and tokenized architecture. | Security | Open |
| `RISK-DOC04-011` | Evidence is incomplete or not retrievable. | Failed certification, audit, or partner review. | Evidence repository and system mapping. | Compliance | Open |
| `RISK-DOC04-012` | Critical launch risk is accepted informally. | Unmanaged legal, partner, user, or financial exposure. | Risk acceptance authority matrix. | Compliance / Project Owner | Open |
| `RISK-DOC04-013` | Operations cannot handle refunds, payout failures, chargebacks, or complaints. | User harm, losses, reputation damage. | SOPs, training, support readiness gates. | Operations | Open |
| `RISK-DOC04-014` | Material product change invalidates approvals. | Regulatory or partner breach. | Change management and recertification triggers. | Compliance / Engineering | Open |
| `RISK-DOC04-015` | Vendor or partner control failure affects PayPlus. | Payment disruption, security, privacy, or settlement failure. | Vendor oversight and partner monitoring. | Compliance / Payments / Security | Open |
| `RISK-DOC04-016` | Payee-created request model launches without regulatory or partner approval. | Licensing risk, partner termination, fines, suspension. | Readiness gate and DOC-03 assessment. | Legal / Compliance / Payments | Open |
| `RISK-DOC04-017` | Payee onboarding is too weak for request creation or payout. | Fraud, cashout, fake invoices, partner risk. | Onboarding, verification, sanctions, capability gating. | Compliance / Risk | Open |
| `RISK-DOC04-018` | Payee-created requests trigger funding or payout without payer authorization. | Unauthorized payment, complaints, disputes, regulatory risk. | T0 authorization control and state gating. | Product / Payments / Engineering | Open |
| `RISK-DOC04-019` | Payee-created requests are used for fake, inflated, duplicate, or collusive obligations. | Fraud, chargebacks, partner escalation. | Evidence, relationship checks, monitoring, manual review. | Risk / Compliance | Open |
| `RISK-DOC04-020` | Landlord-created rent requests are used for self-payment or disguised cashout. | High fraud and cashout risk. | Landlord verification, tenancy evidence, rent controls, limits. | Risk / Operations | Open |
| `RISK-DOC04-021` | Payer believes a payee-created request is mandatory, validated, or already paid. | Complaints, disputes, unfair experience risk. | Request-origin disclosure, explicit payer acceptance, no auto-charge. | Product / Legal | Open |
| `RISK-DOC04-022` | Payee sees payer-sensitive payment, card, risk, or private profile information. | Privacy, security, trust risk. | Payer/payee data boundary, RBAC, support visibility. | Privacy / Security | Open |
| `RISK-DOC04-023` | Payer receives excessive payee-sensitive data or evidence. | Privacy, contractual, or trust risk. | Evidence minimization and privacy review. | Privacy / Legal | Open |
| `RISK-DOC04-024` | Payee changes material request details after payer authorization. | Unauthorized terms, disputes, chargebacks. | Material change lock and renewed authorization. | Product / Engineering | Open |
| `RISK-DOC04-025` | Payee-created request workflow exceeds operational capacity. | Support delays, review backlogs, launch risk. | Controlled scope, review queues, limits, monitoring. | Operations / Product | Open |
| `RISK-DOC04-026` | Chargeback evidence for payee-created requests is insufficient. | Losses and failed representment. | Evidence package linking origin, evidence, authorization, disclosure, communication, and payout proof. | Payments / Operations | Open |

---

## 30. Downstream Document Impact

| Document | Impact |
| --- | --- |
| `DOC-05` | Product requirements must include T0/T1 controls and launch blockers. |
| `DOC-06` | Journeys must support eligibility, onboarding, authorization, consent, screening, and anti-cashout controls. |
| `DOC-07` | Disclosures must cover fees, timing, role, refunds, cancellation, request origin, authorization, and responsibilities. |
| `DOC-08` | Notifications and receipts must support status, evidence, payer/payee communication, and audit controls. |
| `DOC-09` | Payment and settlement must reflect approved funds flow, request creator model, authorization, and transaction logs. |
| `DOC-10` | Payout and reconciliation must implement daily reconciliation, payout eligibility, exceptions, reports, and ledger mapping. |
| `DOC-11` | Refund, cancellation, chargeback, rejection, query, dispute, withdrawal, and evidence controls must be supported. |
| `DOC-12` | Category, OCR, evidence, payee verification, landlord verification, invoice evidence, and rent evidence must satisfy controls. |
| `DOC-13` | Promotion controls must account for disclosures, abuse monitoring, reversals, cost allocation, and request origin. |
| `DOC-14` | AML, sanctions, fraud, velocity, anti-cashout, relationship, fake invoice, fake rent, request abuse, and payee risk controls must implement this baseline. |
| `DOC-15` | Privacy, retention, minimization, consent, visibility, data rights, and sensitive document handling must satisfy T0/T1 controls. |
| `DOC-16` | Architecture must support integrations, auditability, request services, reliability, and safe degradation. |
| `DOC-17` | APIs must support PSP/acquirer, payout, OCR, notification, webhook, payee request, idempotency, and reporting needs. |
| `DOC-18` | Data model and ledger must support creator type, request records, transaction linkage, fees, payouts, refunds, chargebacks, reconciliation, and reporting. |
| `DOC-19` | Security, authentication, PCI, tokenization, RBAC, payee access, payer/payee boundary, encryption, and audit logging must satisfy controls. |
| `DOC-20` | Launch checklist must convert DOC-04 gates into executable go/no-go criteria. |
| `DOC-21` | Runbooks must operationalize incidents, payout failures, reconciliation breaks, refunds, chargebacks, complaints, partner outages, onboarding exceptions, request disputes, and control exceptions. |

---

## 31. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC04-001` | What exact MVP jurisdiction is in scope? | Project Owner / Legal | Critical | Open |
| `OQ-DOC04-002` | What exact bill categories are in MVP? | Product / Compliance | Critical | Open |
| `OQ-DOC04-003` | What is the final MVP funds flow? | Product / Payments / Legal | Critical | Open |
| `OQ-DOC04-004` | What is PayPlus’s legal and partner role? | Legal / Compliance | Critical | Open |
| `OQ-DOC04-005` | What licensing, exemption, or partner coverage applies? | Legal / Compliance | Critical | Open |
| `OQ-DOC04-006` | Which PSP/acquirer will support MVP? | Payments | Critical | Open |
| `OQ-DOC04-007` | What written PSP/acquirer confirmations are available? | Payments / Legal | Critical | Open |
| `OQ-DOC04-008` | What MCC or transaction classification applies? | Payments | Critical | Open |
| `OQ-DOC04-009` | Will transactions be treated as purchase, quasi-cash, account funding, money transfer, or cash advance? | Payments / Legal | Critical | Open |
| `OQ-DOC04-010` | What payout provider and payout rail will be used? | Payments | Critical | Open |
| `OQ-DOC04-011` | Does payout occur before settlement or before funding certainty? | Payments / Finance | Critical | Open |
| `OQ-DOC04-012` | What transaction, user, card, and payee limits apply at MVP? | Risk / Product | High | Open |
| `OQ-DOC04-013` | What payee verification is required? | Compliance / Risk | High | Open |
| `OQ-DOC04-014` | What sanctions screening is legally or contractually required? | Compliance / Legal | Critical | Open |
| `OQ-DOC04-015` | What fraud and anti-cashout rules are required at launch? | Risk | Critical | Open |
| `OQ-DOC04-016` | Is multi-card or multi-source funding included in MVP or deferred? | Product / Payments / Legal | Critical | Open |
| `OQ-DOC04-017` | What PCI scope applies? | Security | Critical | Open |
| `OQ-DOC04-018` | What disclosures must be shown before authorization? | Legal / Product | Critical | Open |
| `OQ-DOC04-019` | What records must be retained? | Legal / Compliance / Finance | High | Open |
| `OQ-DOC04-020` | What systems of record will store consent, authorization, risk, payout, refund, dispute, and reconciliation evidence? | Engineering / Compliance | High | Open |
| `OQ-DOC04-021` | Who has final authority to approve MVP launch? | Project Owner / Compliance | Critical | Open |
| `OQ-DOC04-022` | What post-launch monitoring cadence is acceptable after stabilization? | Compliance / Operations | Medium | Open |
| `OQ-DOC04-023` | Are payee-created payment requests included in MVP, pilot, or post-MVP scope? | Project Owner / Product / Compliance | Critical | Open |
| `OQ-DOC04-024` | Which payee types can create payment requests? | Product / Risk / Compliance | Critical | Open |
| `OQ-DOC04-025` | What payee onboarding, verification, sanctions, payout destination, and capability checks are required? | Compliance / Risk / Operations | Critical | Open |
| `OQ-DOC04-026` | Does the payee-created request model require additional partner confirmation? | Payments / Legal / Compliance | Critical | Open |
| `OQ-DOC04-027` | How must payer authorization be captured for payee-created requests? | Product / Legal / Payments | Critical | Open |
| `OQ-DOC04-028` | What evidence is required for payee-created bill, invoice, fee, or rent requests? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC04-029` | Is landlord-created rent request creation included in MVP or deferred? | Product / Legal / Risk | Critical | Open |
| `OQ-DOC04-030` | What landlord onboarding, tenancy evidence, property reference, and relationship checks are required? | Product / Legal / Risk / Operations | Critical | Open |
| `OQ-DOC04-031` | What payer response options are supported for payee-created requests? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-032` | What payer rejection, query, dispute, or clarification process applies before authorization? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-033` | What payee-created request information can be shown to payer, and what payer information can be shown to payee? | Product / Privacy / Security | High | Open |
| `OQ-DOC04-034` | What monitoring is required to detect fake invoices, fake rent, related-party abuse, and request spam? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC04-035` | Are recurring payee-created rent or invoice requests allowed, or must each request be individually authorized? | Product / Legal / Payments | High | Open |
| `OQ-DOC04-036` | Are payees charged onboarding, subscription, invoice, payout, platform, or transaction fees? | Commercial / Finance / Product | Medium | Open |
| `OQ-DOC04-037` | What payee-side support, complaint, cancellation, and withdrawal procedures are required? | Operations / Product / Legal | High | Open |

---

## 32. Acceptance Criteria

`DOC-04` is acceptable when it clearly defines:

- what compliance certification means for PayPlus;
- PayPlus-specific risk themes;
- MVP compliance posture;
- control tiering;
- non-waivable launch blockers;
- payee-created request launch blockers where applicable;
- risk acceptance authority;
- control domains;
- minimum MVP control baseline;
- payee onboarding control baseline;
- payee-created request control baseline;
- landlord/rent request control baseline;
- control matrix with tiers;
- evidence requirements and systems of record;
- launch certification package;
- launch readiness gates;
- control testing expectations;
- exception and remediation process;
- regulatory and partner change management triggers;
- vendor and partner oversight expectations;
- training and awareness requirements;
- monitoring and reporting requirements;
- governance forums;
- relationship to `DOC-03`;
- relationship to `DOC-20`;
- assumptions;
- constraints;
- dependencies;
- risks;
- downstream document impact;
- open questions.

This document should remain the governing compliance readiness framework for PayPlus MVP and future expansion.

It should be updated whenever launch scope, funds flow, partner model, jurisdiction, bill category, payment method, payout method, fee model, risk model, regulatory interpretation, payee type, payee onboarding model, request creator model, or payee-created request flow changes.

---

## 33. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-04 Compliance Certification Roadmap & Control Framework`. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Expanded into broad compliance roadmap and control framework with control domains, starter matrix, launch gates, evidence requirements, testing, remediation, governance, assumptions, constraints, dependencies, risks, downstream impact, and acceptance criteria. |
| `0.3.0` | `2026-05-26` | Product Documentation Team | Reframed as PayPlus-specific compliance certification framework with certification definition, MVP compliance posture, control tiering, non-waivable launch blockers, risk acceptance authority, MVP minimum control baseline, evidence system mapping, scope-specific launch gates, and stronger DOC-03/DOC-20 linkage. |
| `0.4.0` | `2026-05-27` | Product Documentation Team | Updated control framework to align with `DOC-05 v0.2.0` payee onboarding and payee-created bill, invoice, fee, and rent payment request capability. Added payee-created request certification, payee onboarding controls, payer authorization blockers, request evidence controls, landlord/rent controls, payer-payee relationship risk, payee-created request abuse monitoring, payer/payee privacy boundaries, support/dispute controls, expanded gates, dependencies, risks, open questions, and downstream document impacts. |
| `0.5.0` | `2026-05-27` | Product Documentation Team | Simplified structure and wording while preserving essential compliance certification, launch blocker, control matrix, payee-created request, landlord/rent, evidence, testing, monitoring, governance, risk, and readiness content. |
