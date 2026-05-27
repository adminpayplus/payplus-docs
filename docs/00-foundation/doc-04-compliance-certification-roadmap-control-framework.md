---
document_id: DOC-04
title: Compliance Certification Roadmap & Control Framework
version: 0.4.0
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

## 0. Revision Note — Version 0.4.0

This version updates `DOC-04` to align with the `DOC-05 v0.2.0` product capability where approved payees may be onboarded to PayPlus and may create bill, invoice, fee, or rent payment requests for eligible payers.

This amendment adds compliance certification and control requirements for:

- Payee onboarding.
- Payee-created bill, invoice, fee, and rent payment requests.
- Payer review, acceptance, rejection, query, dispute, and authorization before payment.
- Request creator type controls.
- Payee type and payee capability controls.
- Payee-created request evidence requirements.
- Landlord-created rent request evidence and relationship-validation controls.
- Payer-payee relationship risk and collusion prevention.
- Payee-created request abuse monitoring.
- Payer/payee privacy boundaries.
- Payee-side support, complaint, cancellation, and request-withdrawal controls.
- Payee-created request launch gates and evidence requirements.
- Expansion and recertification triggers for payee-created request flows.

Important principle:

```text
A payee-created bill/invoice/rent request must meet the same bill evidence, category eligibility, payee verification, risk, disclosure, authorization, payment, payout, reconciliation, refund, chargeback, audit, and recordkeeping standards as a payer-created request.
```

The control framework therefore treats payee-created request functionality as a gated capability.

If payee-created requests are included in MVP, pilot, or any production launch scope, all relevant `T0`, `T1`, and `P0 if enabled` controls must be implemented, tested, evidenced, and approved before enablement.

---

## 1. Purpose

This document defines the compliance certification roadmap and control framework for PayPlus.

Its purpose is to convert legal, regulatory, PSP/acquirer, payout provider, card network, AML, sanctions, fraud, consumer protection, privacy, security, finance, reconciliation, and operational obligations into a practical launch and operating control framework.

`DOC-04` determines:

- what must be true before PayPlus can launch;
- which controls are launch blockers;
- which risks may or may not be accepted;
- what evidence is required;
- who owns each control;
- where evidence must be stored;
- what must be tested;
- what must be monitored after launch;
- what must be revisited before scaling, adding categories, adding jurisdictions, changing funds flow, adding payment partners, adding payee types, or enabling payee-created payment requests.

This document is intended to be more than a generic compliance checklist. It is a PayPlus-specific control framework for a bill-payment product that may involve card-funded payments, service fees, third-party payees, payee onboarding, payee-created payment requests, multi-source funding, payout timing risk, chargebacks after payout, and PSP/acquirer dependency.

---

## 2. Definition of Compliance Certification

For PayPlus, “compliance certification” does not mean a single external regulatory certificate unless one is specifically required.

Instead, compliance certification means a documented internal and partner-supported readiness decision that confirms applicable controls have been designed, implemented, tested, evidenced, and approved for a defined launch scope.

Certification may include several components.

| Certification Type | Meaning | Required Before |
| --- | --- | --- |
| Internal launch certification | Internal approval that required launch controls are ready for the approved MVP scope. | MVP launch |
| Regulatory readiness certification | Legal and Compliance confirmation that regulatory role, licensing path, exemptions, or partner coverage have been assessed. | MVP launch / jurisdiction expansion |
| PSP/acquirer readiness certification | Written or contract-based confirmation that the PSP/acquirer supports the PayPlus use case, funds flow, categories, MCC/classification, fees, risk model, payee types, and request creator model. | Production card processing |
| Payout readiness certification | Confirmation that payout provider, rails, reconciliation, exception handling, payee payout eligibility, and settlement timing are ready. | Production payouts |
| Security and PCI readiness certification | Confirmation of PCI scope, card data handling model, access controls, vulnerability remediation, and security review. | Production card processing |
| Privacy readiness certification | Confirmation that data map, privacy notice, consent, payer/payee visibility, retention, deletion, and data processing requirements are ready. | MVP launch |
| AML/sanctions/fraud readiness certification | Confirmation that required screening, risk rules, monitoring, escalation, anti-cashout, payer-payee relationship, and recordkeeping controls are ready. | MVP launch |
| Consumer protection readiness certification | Confirmation that user fees, timing, role, request origin, payer authorization, refund, cancellation, support, and dispute disclosures are implemented and evidenced. | MVP launch |
| Payee onboarding readiness certification | Confirmation that payee onboarding, verification, sanctions, payout destination, payee capability, and offboarding controls are ready. | Before payee-created requests or payee payout |
| Payee-created request readiness certification | Confirmation that payee-created request creation, evidence, payer review, payer authorization, lifecycle, payout gating, abuse monitoring, privacy boundaries, and support controls are ready. | Before payee-created requests are enabled |
| Landlord/rent request readiness certification | Confirmation that landlord onboarding, tenancy or lease evidence, payer-landlord relationship checks, rent-specific risk controls, and rent request disclosures are ready. | Before landlord-created rent requests are enabled |
| Operational readiness certification | Confirmation that support, complaints, refunds, chargebacks, payout exceptions, payer/payee disputes, incident response, and reconciliation operations are ready. | MVP launch |
| Expansion certification | Re-certification for new jurisdictions, bill categories, payment methods, PSPs, payout providers, payee types, request creator models, payee-created request flows, or material funds-flow changes. | Before expansion |

Each certification must be tied to a defined scope. Approval for one jurisdiction, category, partner, payee type, request creator model, or funds flow does not imply approval for another.

---

## 3. Scope

This document covers:

- PayPlus-specific compliance certification approach.
- MVP compliance posture.
- Control tiers and launch-blocking controls.
- Non-waivable launch blockers.
- Risk acceptance authority.
- Control domains.
- Minimum MVP control baseline.
- Payee onboarding control baseline.
- Payee-created request control baseline.
- Landlord/rent request control baseline.
- Control matrix.
- Evidence requirements.
- Evidence systems of record.
- Control ownership.
- Testing requirements.
- Exception and remediation process.
- Regulatory and partner change management.
- Vendor and partner oversight.
- Monitoring and reporting.
- Governance forums.
- Roadmap from MVP to scale.
- Assumptions, constraints, dependencies, risks, open questions, and acceptance criteria.

---

## 4. Out of Scope

This document does not provide:

- Final legal advice.
- Final regulatory licensing opinion.
- Final PSP/acquirer approval.
- Final card network rule interpretation.
- Final AML policy.
- Final sanctions policy.
- Final fraud strategy.
- Final payee onboarding policy.
- Final KYB/KYC requirements for payees.
- Final landlord onboarding requirements.
- Final tenancy contract verification standard.
- Final invoice verification standard.
- Final payee-created request dispute procedure.
- Complete PCI DSS implementation plan.
- Complete SOC 2 audit plan.
- Complete privacy program.
- Product PRD.
- Technical architecture specification.
- Partner contract.
- Customer or payee support SOP.
- QA test suite.
- Incident response runbook.

Those items must be owned in the appropriate legal, compliance, risk, security, product, engineering, finance, operations, or partner documents.

---

## 5. PayPlus-Specific Risk Themes

The control framework must specifically address the following PayPlus risk themes.

| Theme ID | Risk Theme | Why It Matters |
| --- | --- | --- |
| `THEME-DOC04-001` | Bill payment may be treated differently from ordinary card commerce. | PSPs, acquirers, card networks, and regulators may view bill payment as payment facilitation, money movement, quasi-cash, account funding, or money transmission depending on flow. |
| `THEME-DOC04-002` | PayPlus may receive funds before paying a third-party payee. | This can create licensing, safeguarding, settlement, reconciliation, and customer-funds risk. |
| `THEME-DOC04-003` | PayPlus may pay a biller/payee before final card settlement or before chargeback risk expires. | This creates liquidity, credit, fraud, and loss exposure. |
| `THEME-DOC04-004` | Chargebacks may occur after payout. | PayPlus may be unable to recover funds from the payee and may absorb losses. |
| `THEME-DOC04-005` | Multi-card or multi-source funding increases complexity. | Split funding creates refund allocation, chargeback, partial failure, AML, risk, and reconciliation complexity. |
| `THEME-DOC04-006` | User-paid service fees may trigger legal, card network, and consumer disclosure requirements. | Improper fee treatment may cause regulatory, network, partner, and complaint risk. |
| `THEME-DOC04-007` | Certain bill categories may resemble cashout, debt repayment, money transfer, or restricted activity. | Rent, tax, loan repayment, credit card repayment, crypto-related, gambling-related, or self-payment use cases may require enhanced review. |
| `THEME-DOC04-008` | MCC and transaction classification may affect issuer behavior and user experience. | Users may face declines, cash advance treatment, rewards differences, or unexpected issuer fees. |
| `THEME-DOC04-009` | Payee verification is central to anti-cashout control. | Weak payee verification may allow users to route funds to themselves or collusive entities. |
| `THEME-DOC04-010` | Partner approvals are operating constraints. | PSP, acquirer, payout provider, and card network requirements can override product assumptions. |
| `THEME-DOC04-011` | Reconciliation must link user charge, PayPlus fee, payout, refund, chargeback, reserve, and ledger records. | Missing links can create financial loss, reporting gaps, and audit failure. |
| `THEME-DOC04-012` | Product changes may alter regulatory classification. | Changes to funds flow, categories, fees, payout timing, custody, payee role, or request creator model can invalidate prior approvals. |
| `THEME-DOC04-013` | Payee-created requests may change PayPlus regulatory and partner role analysis. | Onboarded payees creating payment requests may create PayFac, marketplace, sub-merchant, biller, agent, debt collection, or payment service implications. |
| `THEME-DOC04-014` | Payee-created requests may create fake obligation, inflated invoice, collusion, or cashout risk. | Payees and payers could collude to create unsupported payment obligations unless onboarding, evidence, relationship checks, and monitoring are effective. |
| `THEME-DOC04-015` | Payer authorization remains mandatory for payee-created requests. | Payee-created requests must not trigger funding, capture, or payout without explicit payer review, disclosure acceptance, and authorization. |
| `THEME-DOC04-016` | Landlord-created rent requests are higher risk. | Rent flows may involve individual payees, recurring high-value payments, tenancy evidence, relationship validation, and elevated self-payment or disguised cashout risk. |
| `THEME-DOC04-017` | Payer/payee data visibility must be controlled. | Payees must not see payer-sensitive funding, card, risk, or private profile information, and payers should not receive unnecessary payee-sensitive data. |
| `THEME-DOC04-018` | Payee-created request workflows may increase operational load. | Payee onboarding, request review, payer disputes, payee support, evidence review, and abuse monitoring require operational readiness before launch. |

---

## 6. MVP Compliance Posture

For MVP, PayPlus should adopt a conservative compliance posture.

The MVP posture should be:

- limited in jurisdiction scope;
- limited in bill category scope;
- limited in payment methods;
- limited in payout rails;
- limited in maximum transaction amounts;
- limited in transaction velocity;
- limited in payee types;
- limited in request creator types;
- limited in operational complexity;
- dependent on written PSP/acquirer and payout provider approval where possible;
- supported by manual review where automation is immature;
- supported by daily reconciliation;
- supported by enhanced monitoring during launch.

MVP should avoid, unless separately approved:

- unsupported or ambiguous funds flows;
- unapproved jurisdictions;
- unapproved bill categories;
- user-to-self payments;
- user-created unverified payees with immediate high-value payout;
- payee-created requests from unverified, restricted, blocked, or ineligible payees;
- landlord-created rent requests without enhanced onboarding and tenancy evidence;
- payee-created invoice requests without invoice evidence and payee verification;
- automatic payer charging based only on a payee-created request;
- payee modification of material request terms after payer authorization without renewed payer authorization;
- crypto, gambling, gift card, stored value, investment, or cash-equivalent payments;
- cross-border payouts;
- FX;
- wallet or stored balance functionality;
- payout before funding certainty without approved credit and liquidity controls;
- multi-card funding unless specifically approved by PSP/acquirer, Legal, Compliance, Risk, Payments, and Finance.

If payee-created requests are included in MVP or pilot scope, the posture should be:

- explicitly approved through `DOC-03` and this document;
- gated by payee onboarding and capability permissions;
- limited to approved payee types and categories;
- subject to payer review and authorization;
- subject to evidence requirements equal to payer-created requests;
- subject to payee-created request abuse monitoring;
- subject to payer/payee privacy boundaries;
- subject to manual review for high-risk payees, categories, evidence, or relationship patterns;
- subject to launch certification specific to the request creator model.

---

## 7. Control Tiering

Controls are tiered according to launch criticality and risk.

| Tier | Name | Meaning | Launch Impact |
| --- | --- | --- | --- |
| `T0` | Non-waivable blocker | Mandatory control required for legal, partner, security, financial, or user-protection reasons. | Cannot launch without completion. |
| `T1` | Critical launch control | Required for MVP launch unless formally accepted by authorized approvers. | Blocks launch unless remediated or formally accepted. |
| `T2` | Important operating control | Required for stable operation, but may be completed shortly after launch with approved mitigation. | May launch with approved remediation plan. |
| `T3` | Scale or maturity control | Required before scaling, certification maturity, audit maturity, or expansion. | Does not block MVP, but blocks scale or expansion. |

Each control in the control matrix must be assigned a tier.

If payee-created request functionality is enabled, controls marked as applicable to payee onboarding, payer authorization, payee-created request evidence, payout gating, privacy boundaries, and request-abuse monitoring must be treated as launch-blocking for that feature.

---

## 8. Non-Waivable Launch Blockers

The following items are non-waivable for MVP launch.

PayPlus must not launch if any `T0` blocker is unresolved.

| Blocker ID | Non-Waivable Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-001` | Regulatory role and licensing path for MVP jurisdiction and funds flow are assessed and approved. | Legal / Compliance |
| `BLK-DOC04-002` | PSP/acquirer approval or equivalent written partner confirmation exists for the PayPlus use case, funds flow, categories, and fee model. | Payments |
| `BLK-DOC04-003` | Payout provider and payout flow are approved, tested, and operationally supported. | Payments / Finance |
| `BLK-DOC04-004` | MVP bill categories are approved; restricted and prohibited categories are configured or procedurally blocked. | Compliance / Product |
| `BLK-DOC04-005` | User fee, total charge, payment timing, refund/cancellation, and PayPlus role disclosures are implemented before authorization. | Legal / Product |
| `BLK-DOC04-006` | PCI scope and card data handling model are approved before production card processing. | Security |
| `BLK-DOC04-007` | Sanctions screening and escalation requirements applicable to MVP are implemented. | Compliance |
| `BLK-DOC04-008` | Baseline fraud, velocity, and anti-cashout controls are implemented. | Risk |
| `BLK-DOC04-009` | Daily settlement, payout, fee, refund, chargeback, and ledger reconciliation process is defined and tested. | Finance / Payments |
| `BLK-DOC04-010` | Refund, cancellation, payout failure, and chargeback handling procedures are defined. | Operations / Payments |
| `BLK-DOC04-011` | Incident escalation path and severity classification are defined. | Security / Operations |
| `BLK-DOC04-012` | Privacy notice, terms acceptance, data collection, and consent controls are implemented. | Privacy / Legal |
| `BLK-DOC04-013` | Critical evidence is stored in an approved repository and linked to launch certification. | Compliance |
| `BLK-DOC04-014` | Required approvers sign launch certification for the defined MVP scope. | Project Owner / Compliance |

The following additional blockers apply if payee-created payment requests are enabled in MVP, pilot, or production scope.

| Blocker ID | Non-Waivable Requirement | Owner |
| --- | --- | --- |
| `BLK-DOC04-015` | Payee-created request model is assessed and approved through `DOC-03`, including payee role, request creator type, partner acceptability, and regulatory implications. | Legal / Compliance / Payments |
| `BLK-DOC04-016` | Payee onboarding, verification, sanctions, payout destination, and capability controls are implemented for payees allowed to create requests. | Compliance / Risk / Operations |
| `BLK-DOC04-017` | Payee-created requests cannot trigger funding, capture, or payout before payer review, disclosure acceptance, and explicit authorization. | Product / Payments / Engineering |
| `BLK-DOC04-018` | Payee-created request evidence requirements are defined, implemented, and tested. | Product / Compliance / Risk |
| `BLK-DOC04-019` | Payee-created request payout gating prevents payout until payer authorization, funding success, evidence checks, payee verification, risk checks, and payout readiness are complete. | Payments / Risk / Finance |
| `BLK-DOC04-020` | Payer/payee privacy boundaries and role-based access controls are implemented and tested. | Privacy / Security |
| `BLK-DOC04-021` | Payee-created request abuse, fake obligation, payer-payee relationship, self-payment, and collusion controls are implemented. | Risk / Compliance |
| `BLK-DOC04-022` | Landlord-created rent requests are blocked unless landlord onboarding, tenancy evidence, rent-specific risk controls, and partner/legal approval are complete. | Legal / Compliance / Risk |
| `BLK-DOC04-023` | Support, complaint, rejection, query, dispute, and payee request withdrawal procedures are defined for payee-created requests. | Operations / Legal / Product |

---

## 9. Risk Acceptance Authority

Some risks may be accepted. Others may not.

Risk acceptance must be explicit, documented, time-bound, and tied to compensating controls.

| Risk Severity | Who May Accept | Conditions |
| --- | --- | --- |
| Critical | Project Owner, Legal Lead, Compliance Lead, and relevant functional lead jointly | Only if not a `T0` blocker and if compensating controls exist. |
| High | Compliance Lead and relevant functional lead | Remediation date, temporary mitigation, and monitoring required. |
| Medium | Functional owner and Compliance reviewer | Remediation plan required. |
| Low | Functional owner | Tracked to closure or accepted as residual risk. |

The following risks may not be accepted for launch:

- no regulatory role assessment;
- no PSP/acquirer approval for the core payment flow;
- no PCI scope decision before card processing;
- no fee and total-charge disclosure before authorization;
- no sanctions screening where required;
- no baseline fraud and anti-cashout controls;
- no payout and reconciliation process;
- no incident escalation path;
- no terms/privacy acceptance;
- no launch approval record.

The following risks may not be accepted for payee-created request launch:

- no regulatory, partner, and role assessment for payee-created request flow;
- no approved payee onboarding and verification model;
- no payer authorization before funding, capture, or payout;
- no payee-created request evidence standard;
- no payout gating for payee-created requests;
- no controls preventing blocked, restricted, rejected, or unverified payees from creating payment requests;
- no payer/payee privacy boundary;
- no payee-created request abuse monitoring;
- no landlord onboarding and tenancy evidence controls if landlord-created rent requests are enabled;
- no support and dispute handling process for payer rejection, query, dispute, or payee withdrawal.

---

## 10. Control Domains

PayPlus controls are grouped into the following domains.

| Domain ID | Domain | Primary Owner | Related Documents |
| --- | --- | --- | --- |
| `CD-DOC04-001` | Governance, accountability, certification, and approvals | Compliance | DOC-00, DOC-20 |
| `CD-DOC04-002` | Regulatory role, licensing, exemptions, and legal obligations | Legal / Compliance | DOC-03 |
| `CD-DOC04-003` | PSP, acquirer, card network, payout provider, and partner readiness | Payments | DOC-03, DOC-09, DOC-10 |
| `CD-DOC04-004` | Category eligibility, restricted categories, and payee acceptability | Compliance / Product | DOC-03, DOC-12 |
| `CD-DOC04-005` | User onboarding, identity, consent, and eligibility | Product / Compliance | DOC-06, DOC-15 |
| `CD-DOC04-006` | Payee onboarding, verification, capability permissions, and anti-cashout | Compliance / Risk / Operations | DOC-12, DOC-14 |
| `CD-DOC04-007` | Payee-created request creation, evidence, payer authorization, lifecycle, and payout gating | Product / Compliance / Payments | DOC-06, DOC-09, DOC-12, DOC-14 |
| `CD-DOC04-008` | Landlord/rent request evidence, relationship validation, and enhanced review | Legal / Compliance / Risk | DOC-06, DOC-12, DOC-14 |
| `CD-DOC04-009` | AML, sanctions, and financial crime controls | Compliance | DOC-14 |
| `CD-DOC04-010` | Fraud, abuse, velocity, payer-payee relationship risk, and transaction risk | Risk | DOC-14 |
| `CD-DOC04-011` | Consumer protection, disclosures, consent, request-origin clarity, and receipts | Legal / Product | DOC-07, DOC-08 |
| `CD-DOC04-012` | Fees, pricing, tax, economics, payee-side fees, and margin controls | Finance / Product | DOC-02, DOC-07 |
| `CD-DOC04-013` | Authorization, capture, settlement, and funding controls | Payments / Engineering | DOC-09 |
| `CD-DOC04-014` | Payout, reconciliation, reserves, and ledger controls | Finance / Payments | DOC-10, DOC-18 |
| `CD-DOC04-015` | Refunds, cancellations, chargebacks, payer disputes, and payee request withdrawal | Operations / Payments | DOC-11 |
| `CD-DOC04-016` | Customer, payer, payee support, complaints, and escalation | Operations | DOC-08, DOC-11, DOC-21 |
| `CD-DOC04-017` | Security, PCI, access, authentication, and infrastructure controls | Security / Engineering | DOC-19, DOC-16 |
| `CD-DOC04-018` | Privacy, data protection, retention, deletion, and payer/payee data visibility | Privacy / Legal | DOC-15 |
| `CD-DOC04-019` | Reporting, recordkeeping, evidence, and auditability | Compliance / Finance | DOC-18 |
| `CD-DOC04-020` | Vendor and partner oversight | Compliance / Legal / Payments | DOC-03 |
| `CD-DOC04-021` | Incident response, business continuity, and resilience | Security / Operations | DOC-21 |
| `CD-DOC04-022` | Change management and release governance | Engineering / Compliance | DOC-20 |
| `CD-DOC04-023` | Training, awareness, and access certification | Compliance / Security | DOC-19, DOC-21 |

---

## 11. Minimum MVP Control Baseline

The following minimum controls are required for MVP.

### 11.1 Regulatory and Partner Baseline

PayPlus must have:

- MVP jurisdiction defined.
- MVP funds flow diagram completed.
- PayPlus role documented.
- Licensing path, exemption, or partner coverage assessed.
- PSP/acquirer approval obtained or documented.
- Payout provider approval obtained or documented.
- Approved bill categories documented.
- Prohibited and restricted categories documented.
- MCC or transaction classification confirmed where possible.
- Fee model reviewed.
- Settlement timing reviewed.
- Reserve, holdback, and liquidity impact reviewed.
- Request creator types documented.
- Payee types documented.
- Payee-created request model assessed if enabled.

### 11.2 Product and Disclosure Baseline

The product must show, before authorization:

- bill amount;
- PayPlus service fee;
- taxes, if applicable;
- total amount charged;
- payee or biller identity;
- request origin where applicable;
- expected processing or delivery timing;
- PayPlus role;
- cancellation and refund rules;
- user responsibility for late fees or biller consequences where applicable;
- terms acceptance;
- privacy notice access.

The system must retain:

- disclosure version;
- timestamp of acceptance;
- user ID;
- transaction ID;
- request creator type;
- amount and fee shown;
- payment authorization record.

### 11.3 User and Payee Baseline

PayPlus must define:

- minimum user information required;
- user eligibility rules;
- blocked user criteria;
- payee information required;
- payee verification method;
- payee onboarding method where payees can create requests;
- payee capability permissions;
- payee ownership or relationship checks where applicable;
- self-payment controls;
- high-risk payee escalation process;
- prohibited payee categories;
- blocked, restricted, rejected, and unverified payee behavior.

### 11.4 Payee-Created Request Baseline

If payee-created requests are enabled, PayPlus must define and implement:

- approved payee types eligible to create requests;
- approved request categories per payee type;
- request creator type tracking;
- payer identification or invitation controls;
- required request fields;
- required evidence by category;
- request-origin disclosure;
- payer review and authorization flow;
- payer rejection, query, dispute, expiration, and cancellation states;
- payee request withdrawal rules before payer authorization;
- locks on material request terms after payer authorization;
- renewed payer authorization for material changes;
- payee-created request audit events;
- payee-created request manual review triggers;
- payout gating for payee-created requests;
- payer/payee communication and privacy boundaries;
- support and escalation procedures.

### 11.5 Landlord/Rent Request Baseline

If rent requests or landlord-created rent requests are enabled, PayPlus must define and implement:

- landlord onboarding requirements;
- landlord identity or business verification;
- payout destination verification;
- property or rental reference capture;
- tenancy contract, lease agreement, rent schedule, or approved equivalent evidence;
- payer-landlord relationship validation where required;
- rent amount reasonableness checks where feasible;
- duplicate rent request detection;
- recurring or repeated rent request controls;
- payout destination change review;
- self-payment, related-party, and collusion checks;
- manual review for first payment, high-value payment, changed payout destination, changed landlord details, or unusual pattern.

### 11.6 AML, Sanctions, Fraud, and Anti-Cashout Baseline

MVP must include:

- sanctions screening where required;
- adverse match review process;
- blocked party escalation;
- transaction amount limits;
- daily and rolling user limits;
- new-user limits;
- card velocity limits;
- failed authorization velocity limits;
- payee velocity limits;
- payee concentration monitoring;
- self-payment detection;
- circular payment detection where feasible;
- payer-payee relationship risk checks where payee-created requests are enabled;
- payee-created request abuse monitoring where enabled;
- fake invoice or fake rent detection where applicable;
- suspicious refund monitoring;
- manual review queue;
- risk decision audit logs.

### 11.7 Payment, Payout, and Reconciliation Baseline

MVP must include:

- unique transaction IDs;
- parent-child linkage for funding events, if multi-source funding exists;
- request creator type linkage;
- authorization and capture logs;
- settlement status tracking;
- payout status tracking;
- payout readiness controls;
- payee-created request payout gating where enabled;
- fee ledger entries;
- refund ledger entries;
- chargeback ledger entries;
- daily reconciliation process;
- unresolved exception log;
- payout failure process;
- refund failure process;
- chargeback evidence process.

### 11.8 Security, Privacy, and Access Baseline

MVP must include:

- PCI scope decision;
- tokenized card handling where applicable;
- no unnecessary storage of sensitive card data;
- encryption in transit;
- encryption at rest for sensitive data;
- role-based access for admin tools;
- role-based access for payee functionality where enabled;
- payer/payee data visibility boundaries where enabled;
- audit logs for sensitive actions;
- vulnerability review before launch;
- privacy notice;
- data map;
- data retention approach;
- incident escalation path.

### 11.9 Operations Baseline

MVP must include:

- refund procedure;
- cancellation procedure;
- payout failure procedure;
- chargeback procedure;
- payer rejection, query, and dispute procedure for payee-created requests where enabled;
- payee request withdrawal procedure where enabled;
- complaint intake and escalation;
- payer and payee support macros where applicable;
- support macros for payment timing, fees, refunds, failed payments, request origin, and payer authorization;
- internal escalation contacts;
- incident severity levels;
- daily launch monitoring during initial production period.

---

## 12. Control Matrix

The following matrix defines the initial PayPlus control set.

| Control ID | Tier | Domain | Control Objective | Type | Frequency | Owner | Evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `CTRL-DOC04-001` | `T0` | Governance | Maintain launch certification scope, approvers, and evidence package. | Directive | Per launch | Compliance | Launch certification package, approval log. |
| `CTRL-DOC04-002` | `T0` | Regulatory | Confirm regulatory role and licensing path for MVP jurisdiction, funds flow, payee type, and request creator model. | Preventive | Per launch / Material change | Legal / Compliance | DOC-03 assessment, legal memo, approval record. |
| `CTRL-DOC04-003` | `T0` | Partner readiness | Confirm PSP/acquirer support for PayPlus use case, categories, fees, funds flow, payee types, and request creator model. | Preventive | Per partner / Material change | Payments | Partner approval, contract, underwriting record. |
| `CTRL-DOC04-004` | `T0` | Payout readiness | Confirm payout provider, payout rails, settlement timing, payee payout eligibility, and exception handling. | Preventive | Per launch / Material change | Payments / Finance | Payout approval, test payout evidence, SOP. |
| `CTRL-DOC04-005` | `T0` | Category eligibility | Maintain and enforce MVP approved, restricted, and prohibited categories, including request-creator-specific restrictions. | Preventive | Per launch / Monthly | Compliance / Product | Category register, configuration, approval log. |
| `CTRL-DOC04-006` | `T1` | Payee controls | Verify payee eligibility before payout. | Preventive | Per payee | Compliance / Operations | Payee verification record, review notes. |
| `CTRL-DOC04-007` | `T1` | User controls | Capture required user information and terms/privacy consent. | Preventive | Per user | Product / Compliance | User profile, consent logs. |
| `CTRL-DOC04-008` | `T0` | Sanctions | Screen required parties and escalate potential matches. | Preventive / Detective | Onboarding / Ongoing | Compliance | Screening logs, match disposition records. |
| `CTRL-DOC04-009` | `T0` | Fraud / Anti-cashout | Apply baseline transaction limits, velocity rules, and self-payment controls. | Preventive / Detective | Real-time / Daily | Risk | Rule configuration, decision logs, alerts. |
| `CTRL-DOC04-010` | `T1` | Manual review | Route high-risk transactions, users, payees, categories, or requests to manual review. | Preventive | Per trigger | Risk / Operations | Case queue, disposition logs. |
| `CTRL-DOC04-011` | `T0` | Disclosures | Display bill amount, service fee, total charge, timing, role, request origin where applicable, and refund/cancellation terms before authorization. | Preventive | Per transaction | Product / Legal | UI screenshots, disclosure version, consent logs. |
| `CTRL-DOC04-012` | `T0` | Payment authorization | Capture user or payer authorization and immutable transaction details. | Preventive | Per transaction | Product / Engineering | Authorization logs, transaction record. |
| `CTRL-DOC04-013` | `T1` | Fee controls | Ensure fee calculation matches approved pricing and margin rules, including payee-side fees where applicable. | Preventive / Detective | Per transaction / Daily | Finance / Product | Pricing configuration, fee reports. |
| `CTRL-DOC04-014` | `T0` | Settlement reconciliation | Reconcile PSP settlement, fees, payouts, refunds, chargebacks, reserves, ledger, and bank records. | Detective | Daily | Finance / Payments | Reconciliation report, exception log. |
| `CTRL-DOC04-015` | `T0` | Payout exceptions | Detect and resolve failed, delayed, returned, or misdirected payouts. | Corrective | Daily / Per exception | Payments / Operations | Payout exception log, resolution record. |
| `CTRL-DOC04-016` | `T0` | Refunds | Process refunds according to approved rules and ledger treatment. | Preventive / Corrective | Per refund | Operations / Payments | Refund record, approval log, ledger entry. |
| `CTRL-DOC04-017` | `T1` | Chargebacks | Track, evidence, and respond to chargebacks within deadlines. | Corrective | Per dispute | Operations / Payments | Dispute case, evidence package, outcome. |
| `CTRL-DOC04-018` | `T1` | Complaints | Log, classify, investigate, and resolve payer and payee complaints. | Corrective | Per complaint | Operations | Complaint register, response record. |
| `CTRL-DOC04-019` | `T0` | PCI | Approve PCI scope and card data handling model before card processing. | Preventive | Per launch / Annual / Material change | Security | PCI scope document, architecture diagram, SAQ/AOC if applicable. |
| `CTRL-DOC04-020` | `T1` | Access control | Restrict admin and sensitive data access based on role. | Preventive | Continuous / Quarterly | Security / Engineering | Role matrix, access review, audit logs. |
| `CTRL-DOC04-021` | `T1` | Audit logging | Log sensitive admin, payment, payout, refund, risk, support, payee onboarding, and payee-created request actions. | Detective | Continuous | Engineering / Security | Audit logs, log retention evidence. |
| `CTRL-DOC04-022` | `T0` | Privacy | Provide privacy notice and capture required consent. | Preventive | Per user / Material change | Privacy / Product | Privacy version, consent logs. |
| `CTRL-DOC04-023` | `T1` | Data retention | Retain and delete records according to approved schedule. | Preventive / Corrective | Continuous / Periodic | Privacy / Engineering | Retention policy, deletion logs. |
| `CTRL-DOC04-024` | `T1` | Vendor diligence | Review material vendors and payment partners before production use. | Preventive | Per vendor / Annual | Compliance / Security / Legal | Due diligence checklist, SOC report, contract review. |
| `CTRL-DOC04-025` | `T0` | Incident escalation | Maintain incident severity levels, escalation contacts, and notification process. | Corrective | Per incident / Per launch | Security / Operations | Incident runbook, escalation matrix. |
| `CTRL-DOC04-026` | `T1` | Change management | Review product, risk, compliance, and technical changes before release. | Preventive | Per release | Engineering / Compliance | Change tickets, approvals, release notes. |
| `CTRL-DOC04-027` | `T1` | Regulatory/partner change monitoring | Monitor regulatory, card network, PSP, acquirer, payout provider, and contractual changes. | Detective | Monthly / Event-driven | Legal / Compliance / Payments | Monitoring log, impact assessment. |
| `CTRL-DOC04-028` | `T2` | Training | Provide role-based compliance, security, fraud, payee onboarding, and support training. | Directive | On hire / Annual | Compliance / Security | Training completion records. |
| `CTRL-DOC04-029` | `T2` | Control testing | Test design and operating effectiveness of key controls. | Detective | Quarterly / Annual | Compliance / QA / Internal Audit | Test plan, samples, results, remediation log. |
| `CTRL-DOC04-030` | `T3` | SOC 2 readiness | Prepare for formal security/compliance audit maturity if commercially required. | Directive | Pre-scale / Annual | Security | SOC 2 readiness plan, gap assessment. |
| `CTRL-DOC04-031` | `T1` | Payee onboarding | Onboard and verify payees before granting request creation or payout capabilities. | Preventive | Per payee | Compliance / Risk / Operations | Payee onboarding case, verification evidence, approval record. |
| `CTRL-DOC04-032` | `T1` | Payee capabilities | Assign payee capabilities by payee type, verification status, risk status, category permissions, and launch scope. | Preventive | Per payee / Material change | Product / Risk / Compliance | Capability configuration, payee status record, approval log. |
| `CTRL-DOC04-033` | `T1` | Payee-created request eligibility | Prevent blocked, restricted, rejected, or unverified payees from creating or sending payment requests unless approved exception applies. | Preventive | Per request | Product / Engineering / Compliance | Permission checks, blocked request logs, exception approval. |
| `CTRL-DOC04-034` | `T1` | Payee-created request evidence | Require sufficient evidence for payee-created bill, invoice, fee, or rent requests before configured processing stages. | Preventive | Per request | Product / Compliance / Operations | Uploaded evidence, validation record, review decision. |
| `CTRL-DOC04-035` | `T0` | Payer authorization for payee-created requests | Prevent funding, capture, or payout for payee-created requests until payer review, disclosure acceptance, and authorization are complete. | Preventive | Per request | Product / Payments / Engineering | Payer authorization logs, state transition evidence. |
| `CTRL-DOC04-036` | `T1` | Payee-created request lifecycle | Maintain lifecycle states for pending, viewed, accepted, rejected, queried, disputed, expired, cancelled, paid, and withdrawn where applicable. | Preventive / Detective | Per request | Product / Engineering | Request status history, audit logs. |
| `CTRL-DOC04-037` | `T1` | Material change lock | Lock material payee-created request terms after payer authorization or require renewed payer authorization. | Preventive | Per change | Product / Engineering | Change logs, reauthorization records. |
| `CTRL-DOC04-038` | `T1` | Payer-payee relationship risk | Monitor suspicious, circular, self-payment, collusive, related-party, or unusual payer-payee relationships. | Preventive / Detective | Per request / Daily | Risk | Relationship risk signals, alerts, case dispositions. |
| `CTRL-DOC04-039` | `T1` | Payee-created request abuse monitoring | Monitor excessive request creation, repeated rejection, fake invoices, duplicate rent, payer complaints, and unusual acceptance/funding patterns. | Detective | Daily / Weekly | Risk / Operations | Monitoring report, alerts, review cases. |
| `CTRL-DOC04-040` | `T1` | Landlord/rent controls | Apply landlord verification, tenancy evidence, duplicate rent, amount reasonableness, payout destination change, and recurring pattern controls where rent is enabled. | Preventive / Detective | Per rent request / Ongoing | Risk / Compliance / Operations | Landlord review, tenancy evidence, rent review decision. |
| `CTRL-DOC04-041` | `T1` | Payer/payee privacy boundary | Enforce payer/payee visibility rules and prevent unauthorized access to sensitive payer funding, card, risk, or private profile data. | Preventive | Continuous | Privacy / Security / Engineering | RBAC test, access logs, privacy review. |
| `CTRL-DOC04-042` | `T1` | Payer rejection, query, and dispute | Support payer rejection, query, dispute, or clarification flows before authorization without funding movement. | Preventive / Corrective | Per request | Operations / Product | Case log, request status, communication record. |
| `CTRL-DOC04-043` | `T1` | Payee withdrawal | Support payee withdrawal or cancellation of a payee-created request before payer authorization, subject to audit logging and notification. | Corrective | Per withdrawal | Product / Operations | Withdrawal log, notification record, audit event. |
| `CTRL-DOC04-044` | `T1` | Payee-created request evidence package | Link request evidence, payer authorization, disclosure, communication, payment, payout, refund, dispute, and reconciliation records. | Detective | Per transaction | Compliance / Engineering / Operations | Evidence package, data links, retrieval test. |
| `CTRL-DOC04-045` | `T1` | Payee-side support visibility | Ensure support tooling distinguishes payer-side and payee-side visibility and permissions. | Preventive | Continuous / Per case | Operations / Security | Support role matrix, access test, case records. |

---

## 13. Control-to-Evidence-to-System Mapping

Evidence must be mapped to a system of record.

| Evidence Type | System of Record | Owner |
| --- | --- | --- |
| Legal assessment | Legal repository / compliance evidence folder | Legal |
| Regulatory role approval | Compliance evidence repository | Compliance |
| PSP/acquirer approval | Contract repository / partner folder | Payments / Legal |
| Payout provider approval | Contract repository / partner folder | Payments / Legal |
| Category approval | Compliance register / product configuration | Compliance / Product |
| Fee approval | Finance model / pricing configuration / approval ticket | Finance / Product |
| UI disclosure evidence | Product QA repository / screenshot archive | Product / Legal |
| Terms acceptance | Application database / audit log | Product / Engineering |
| Privacy consent | Application database / consent log | Privacy / Engineering |
| User onboarding record | Application database | Product |
| Payee onboarding record | Compliance case system / operations queue / application database | Compliance / Operations |
| Payee verification record | Compliance case system / operations queue | Compliance / Operations |
| Payee capability permission record | Application database / product configuration / admin console | Product / Risk |
| Payee-created request record | Application database / transaction system | Product / Engineering |
| Payee-created request evidence | Evidence repository / document storage / application database | Product / Compliance |
| Rent evidence | Evidence repository / document storage / application database | Product / Compliance / Risk |
| Payer response record | Application database / audit log | Product / Engineering |
| Payer authorization for payee-created request | Payment platform / application ledger / audit log | Payments / Engineering |
| Payer/payee communication record | Notification system / support system / communication log | Operations / Product |
| Payer/payee dispute or query record | Support system / case management tool | Operations |
| Payee request withdrawal record | Application database / audit log | Product / Operations |
| Payer/payee visibility rules | Privacy repository / access-control matrix | Privacy / Security |
| Sanctions screening result | Screening tool / compliance case system | Compliance |
| Fraud decision | Risk engine / risk decision logs | Risk / Engineering |
| Payer-payee relationship risk decision | Risk engine / case management tool | Risk / Operations |
| Payee-created request abuse monitoring | Risk monitoring system / operations dashboard | Risk / Operations |
| Manual review case | Admin console / case management tool | Risk / Operations |
| Authorization record | Payment platform / application ledger | Payments / Engineering |
| Settlement report | PSP portal / reconciliation system | Finance / Payments |
| Payout report | Payout provider portal / reconciliation system | Finance / Payments |
| Ledger entry | Transaction ledger | Finance / Engineering |
| Reconciliation exception | Reconciliation tracker / finance system | Finance |
| Refund record | Application ledger / PSP portal / operations case | Operations / Payments |
| Chargeback case | PSP portal / dispute case system | Operations / Payments |
| Complaint record | Support system / complaint register | Operations |
| PCI scope evidence | Security repository | Security |
| Access review | IAM / admin console / access review tracker | Security |
| Audit logs | Logging platform / application audit tables | Engineering / Security |
| Incident record | Incident management system | Security / Operations |
| Vendor due diligence | Vendor risk repository | Compliance / Security |
| Change approval | Ticketing system / release management tool | Engineering |
| Training completion | LMS / training tracker | Compliance |

---

## 14. Certification Roadmap

The roadmap separates MVP, early operation, scale, and expansion.

| Phase | Name | Objective | Required Before Exit |
| --- | --- | --- | --- |
| `PH-DOC04-001` | Discovery | Identify product scope, jurisdiction, funds flow, categories, partners, payee types, request creator types, and obligations. | Draft DOC-03, product scope, initial obligation inventory. |
| `PH-DOC04-002` | MVP Control Design | Define T0/T1 controls, owners, evidence, launch blockers, payee-created request controls where applicable, and evidence plan. | Approved control matrix and evidence plan. |
| `PH-DOC04-003` | MVP Control Build | Implement required product, partner, risk, payment, security, privacy, payee onboarding, request lifecycle, and operational controls. | T0 controls implemented; T1 controls implemented or risk-accepted. |
| `PH-DOC04-004` | MVP Control Test | Test critical controls and document exceptions. | T0 controls tested; critical exceptions closed. |
| `PH-DOC04-005` | MVP Certification | Assemble launch package and obtain approvals. | Launch certification signed. |
| `PH-DOC04-006` | Controlled Launch | Launch with enhanced monitoring and limited scope. | Daily monitoring, issue tracking, reconciliation, request-abuse monitoring, and support review active. |
| `PH-DOC04-007` | Stabilization | Validate operating effectiveness and remediate launch findings. | Initial post-launch control review completed. |
| `PH-DOC04-008` | Scale Readiness | Add T2/T3 maturity controls required for higher volume or enterprise readiness. | Control testing, vendor reassessment, SOC 2/PCI maturity as needed. |
| `PH-DOC04-009` | Expansion Certification | Re-certify for new jurisdictions, categories, partners, payment methods, payee types, request creator models, payee-created requests, or funds-flow changes. | Expansion certification approved before change. |

---

## 15. Launch Certification Package

The launch certification package must be assembled before MVP launch.

It must include:

- launch scope;
- jurisdiction scope;
- bill category scope;
- user scope;
- payee scope;
- payee type scope;
- request creator type scope;
- payment method scope;
- payout method scope;
- funds flow diagram;
- PayPlus regulatory role assessment;
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
- payer-payee relationship risk control evidence where applicable;
- payee-created request abuse monitoring evidence where applicable;
- user and payee onboarding evidence;
- payee capability control evidence where applicable;
- payee-created request evidence standard where applicable;
- landlord/rent evidence standard where applicable;
- PCI scope and security evidence;
- payer/payee access and privacy boundary evidence where applicable;
- privacy and data protection evidence;
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
- launch approver signatures.

---

## 16. Launch Readiness Gates

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
| `GATE-DOC04-009` | `T0` | Fee and disclosure controls ready | Fee, total charge, timing, role, request origin where applicable, refund, and cancellation disclosures are approved and tested. | Legal / Product |
| `GATE-DOC04-010` | `T0` | Payment authorization controls ready | Authorization, capture, consent, payer acceptance where applicable, and transaction logging are tested. | Payments / Engineering |
| `GATE-DOC04-011` | `T0` | Reconciliation controls ready | Settlement, payout, fee, refund, chargeback, reserve, ledger, request creator type, and bank reconciliation are tested. | Finance / Payments |
| `GATE-DOC04-012` | `T0` | Security and PCI controls ready | PCI scope, card data model, access controls, and launch security review are complete. | Security |
| `GATE-DOC04-013` | `T0` | Privacy controls ready | Privacy notice, data map, consent, retention approach, and payer/payee data visibility controls are ready. | Privacy / Legal |
| `GATE-DOC04-014` | `T1` | Support and complaint controls ready | Support, complaint, dispute, refund, chargeback, payer query, and payee request withdrawal procedures are ready. | Operations |
| `GATE-DOC04-015` | `T0` | Incident escalation ready | Incident severity model and escalation paths are documented. | Security / Operations |
| `GATE-DOC04-016` | `T0` | Evidence repository complete | Required T0 evidence is stored and linked to launch certification. | Compliance |
| `GATE-DOC04-017` | `T0` | Critical exceptions closed | T0 exceptions are closed; T1 exceptions are closed or accepted. | Compliance |
| `GATE-DOC04-018` | `T0` | Launch certification approved | Required approvers sign the certification package. | Project Owner / Compliance |
| `GATE-DOC04-019` | `T0 if enabled` | Payee-created request model approved | Payee-created request flow, payee role, partner approval, regulatory assessment, payer authorization, evidence, risk, privacy, payout, and reconciliation controls are approved. | Legal / Compliance / Payments |
| `GATE-DOC04-020` | `T0 if enabled` | Payee onboarding controls ready | Payee onboarding, verification, sanctions, payout destination, payee status, capability permissions, and offboarding controls are implemented and tested. | Compliance / Risk / Operations |
| `GATE-DOC04-021` | `T0 if enabled` | Payer authorization for payee-created requests ready | Payee-created requests cannot fund, capture, or pay out until payer review, disclosure acceptance, and authorization are complete. | Product / Payments / Engineering |
| `GATE-DOC04-022` | `T1 if enabled` | Payee-created request evidence controls ready | Required evidence by category is implemented, reviewable, retained, and linked to request lifecycle records. | Product / Compliance / Risk |
| `GATE-DOC04-023` | `T1 if enabled` | Payee-created request abuse controls ready | Fake obligation, duplicate request, payer-payee relationship, collusion, spam, complaint, and rejection-rate monitoring are implemented. | Risk / Compliance |
| `GATE-DOC04-024` | `T1 if enabled` | Payer/payee privacy and support controls ready | Payer/payee data visibility, support permissions, communications, disputes, and request withdrawal procedures are tested. | Privacy / Security / Operations |
| `GATE-DOC04-025` | `T0 if rent enabled` | Landlord/rent request controls ready | Landlord verification, tenancy evidence, rent-specific risk controls, relationship checks, and partner/legal approval are complete. | Legal / Compliance / Risk |

---

## 17. Control Testing

Critical controls must be tested before launch.

Testing should include:

| Test Area | Required Test |
| --- | --- |
| Fee disclosure | Confirm fee and total amount appear before authorization. |
| Consent logging | Confirm terms/privacy/disclosure consent is recorded with version and timestamp. |
| Category blocking | Confirm prohibited categories cannot be submitted or paid. |
| Payee verification | Confirm unverified or restricted payees cannot receive payout. |
| Payee capability gating | Confirm payees can create only permitted request types based on status, type, category, and launch scope. |
| Payee-created request creation | Confirm only eligible payees can create payee-created requests. |
| Payee-created request evidence | Confirm required evidence is captured before configured processing stages. |
| Payer review and authorization | Confirm payee-created requests cannot trigger funding, capture, or payout before payer authorization. |
| Payer rejection/query/dispute | Confirm payer can reject, query, dispute, or allow expiry without funding movement before authorization. |
| Payee withdrawal | Confirm payee can withdraw or cancel a request before payer authorization where permitted. |
| Material change lock | Confirm material request terms are locked after payer authorization or require renewed authorization. |
| Landlord/rent evidence | Confirm rent requests require approved tenancy, lease, rent schedule, or equivalent evidence where enabled. |
| Payer-payee relationship risk | Confirm suspicious, circular, self-payment, or related-party patterns are blocked or routed to review. |
| Payee-created request abuse monitoring | Confirm repeated rejections, duplicate rent requests, fake invoice signals, and request spam can be detected or reviewed. |
| Payer/payee privacy boundary | Confirm payees cannot view sensitive payer funding, card, private profile, or internal risk information. |
| Support visibility | Confirm support tooling distinguishes payer-side and payee-side permissions. |
| Sanctions handling | Confirm potential match creates escalation and blocks payout until disposition. |
| Fraud rules | Confirm limits, velocity rules, and high-risk triggers operate. |
| Self-payment detection | Confirm obvious user-to-self patterns are blocked or reviewed. |
| Authorization logging | Confirm transaction record links user, amount, fee, payee, payment method, request origin, and consent. |
| Payout flow | Confirm successful payout and failed payout paths. |
| Payee-created payout gating | Confirm payout remains blocked until payer authorization, funding success, evidence checks, payee verification, risk checks, and payout readiness pass. |
| Reconciliation | Confirm PSP settlement, payout, fee, refund, request creator type, and ledger records can be matched. |
| Refund flow | Confirm refund allocation, ledger entries, and user communication. |
| Chargeback flow | Confirm evidence package can be assembled, including request origin, evidence, payer authorization, disclosures, communication, and payout proof. |
| Access controls | Confirm admin roles restrict sensitive actions. |
| Audit logs | Confirm sensitive actions are logged. |
| Incident escalation | Confirm escalation contacts and severity model are usable. |

---

## 18. Exception and Remediation Management

Control exceptions must be logged.

| Field | Description |
| --- | --- |
| Exception ID | Unique exception identifier. |
| Control ID | Related control. |
| Tier | `T0`, `T1`, `T2`, or `T3`. |
| Severity | Critical, high, medium, low. |
| Description | Exception details. |
| Detection Date | When the issue was found. |
| Owner | Responsible remediation owner. |
| Root Cause | Cause of exception. |
| Impact | Compliance, financial, operational, user, payer, payee, security, privacy, or partner impact. |
| Temporary Mitigation | Interim control or workaround. |
| Remediation Plan | Corrective action. |
| Target Date | Due date. |
| Status | Open, in progress, remediated, accepted risk, closed. |
| Approver | Required approver for closure or acceptance. |
| Evidence | Proof of remediation. |

`T0` exceptions cannot be accepted for MVP launch.

`T0 if enabled` exceptions cannot be accepted for launch of the applicable enabled feature, including payee-created requests or landlord-created rent requests.

---

## 19. Regulatory and Partner Change Management

Material changes require reassessment.

Triggers include:

- new jurisdiction;
- new bill category;
- new payee type;
- new request creator type;
- enablement of payee-created requests;
- enablement of landlord-created rent requests;
- enablement of payee-created invoice or fee requests;
- change to payee onboarding requirements;
- change to payee capability permissions;
- change to payer identification or invitation mechanism;
- change to payer acceptance, rejection, query, or dispute process;
- change to payer/payee data visibility;
- new payment method;
- new payout method;
- new PSP or acquirer;
- new payout provider;
- changed funds flow;
- changed merchant of record structure;
- changed PayFac, marketplace, sub-merchant, biller, or agent model;
- changed fee model;
- changed MCC or transaction classification;
- changed settlement timing;
- changed reserve or holdback;
- changed refund or chargeback process;
- changed data handling;
- changed sanctions or AML requirement;
- changed card network, PSP, acquirer, payout provider, bank, or legal requirement;
- material fraud, chargeback, complaint, payout failure, request abuse, payee onboarding failure, or reconciliation issue.

A material change must not be released until Compliance determines whether recertification is required.

---

## 20. Vendor and Partner Oversight

Material vendors and partners must be reviewed before production use.

Payment partners require enhanced review because they may affect:

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
- reporting;
- reconciliation;
- privacy and security;
- operational continuity.

Vendor and partner oversight should include:

- due diligence;
- contract review;
- data protection review;
- security review;
- regulatory status review;
- business continuity review;
- pricing and reserve review;
- payee onboarding support review where applicable;
- payee-level reporting capability review where applicable;
- reporting capability review;
- incident and SLA review;
- annual or risk-based reassessment.

---

## 21. Training and Awareness

Before launch, relevant personnel should receive role-based training.

Required MVP training topics include:

- PayPlus product and funds flow;
- approved, restricted, and prohibited categories;
- request creator type and request-origin concepts;
- fee and disclosure rules;
- user and payee eligibility;
- payee onboarding and capability permissions;
- payer authorization requirements for payee-created requests;
- sanctions escalation;
- fraud and anti-cashout red flags;
- payer-payee relationship and collusion red flags;
- fake invoice and fake rent red flags where applicable;
- manual review procedures;
- refund and cancellation handling;
- payer rejection, query, dispute, and payee withdrawal handling where applicable;
- chargeback evidence handling;
- complaint escalation;
- payer/payee privacy and data handling;
- security and access obligations;
- incident escalation.

Training records should be retained.

---

## 22. Monitoring and Reporting

MVP launch should include enhanced monitoring.

Candidate daily launch metrics:

| Area | Metrics |
| --- | --- |
| Payments | Authorization rate, capture failures, payment failures, processor errors. |
| Payouts | Payout success rate, payout failures, delayed payouts, returned payouts. |
| Payee onboarding | Payee applications, approval rate, rejection rate, pending reviews, verification failures, payout destination failures. |
| Payee-created requests | Request volume, sent requests, viewed requests, accepted requests, rejected requests, queried requests, disputed requests, expired requests, withdrawn requests. |
| Rent requests | Rent request volume, landlord approvals, tenancy evidence failures, duplicate rent signals, relationship risk alerts, rent amount exceptions. |
| Reconciliation | Unmatched transactions, settlement breaks, payout breaks, fee breaks, request creator type mismatches. |
| Fraud | Rule triggers, manual review queue, blocked transactions, suspicious payees, suspicious payee-created requests. |
| Anti-cashout | Self-payment alerts, payer-payee relationship alerts, payee concentration, suspicious refund behavior, collusion indicators. |
| Sanctions | Screening hits, pending reviews, blocked parties. |
| Refunds | Refund volume, refund failure rate, refund reasons. |
| Chargebacks | New disputes, reason codes, exposure amount, evidence availability. |
| Complaints | Complaint volume, payer complaints, payee complaints, request-origin complaints, response SLA, escalations. |
| Security | Incidents, access anomalies, critical vulnerabilities. |
| Privacy | Consent errors, payer/payee visibility issues, data request issues, deletion exceptions. |
| Finance | Gross volume, fees, reserves, losses, margin variance. |

Monitoring cadence:

| Period | Cadence |
| --- | --- |
| First 2 weeks after launch | Daily review |
| Weeks 3–8 | At least weekly review |
| After stabilization | Monthly governance review, unless risk indicators require more frequent review |

If payee-created requests are enabled, request abuse, payer rejection/dispute, payee complaint, payee onboarding exception, and payer/payee privacy metrics should be included in launch monitoring.

---

## 23. Governance Forums

| Forum | Frequency | Purpose | Participants |
| --- | --- | --- | --- |
| MVP Launch Readiness Review | Weekly pre-launch | Track gates, blockers, evidence, and risk acceptance. | Product, Compliance, Legal, Payments, Risk, Security, Finance, Operations, Engineering. |
| Payee-Created Request Readiness Review | Weekly pre-launch if enabled / event-driven | Track payee onboarding, payer authorization, request evidence, rent controls, abuse monitoring, privacy, support, and partner approval readiness. | Product, Compliance, Legal, Payments, Risk, Security, Privacy, Finance, Operations, Engineering. |
| Daily Launch Monitoring | Daily during initial launch | Review live metrics, incidents, settlement, payout, fraud, complaints, payee onboarding, payee-created requests, and exceptions. | Compliance, Risk, Payments, Finance, Operations, Engineering. |
| Risk and Compliance Review | Monthly | Review compliance metrics, control exceptions, remediation, incidents, request abuse, payee risk, and regulatory changes. | Compliance, Legal, Risk, Security, Operations. |
| Payments and Reconciliation Review | Weekly / Monthly | Review settlement, payout, chargebacks, reserves, reconciliation, request creator type issues, and partner issues. | Payments, Finance, Operations, Engineering. |
| Security and Privacy Review | Monthly / Quarterly | Review security posture, access, incidents, privacy issues, payer/payee visibility, and vendor security. | Security, Privacy, Engineering, Legal. |
| Vendor and Partner Review | Quarterly / Annual | Review material vendor and partner performance, attestations, incidents, payee-created request support, and renewals. | Compliance, Legal, Security, Payments, Finance. |
| Expansion Certification Review | Event-driven | Approve new jurisdictions, categories, partners, payment methods, payee types, request creator models, or funds-flow changes. | Project Owner, Legal, Compliance, Payments, Risk, Security, Privacy, Finance. |

---

## 24. Relationship to DOC-03

`DOC-03` determines what regulatory, PSP/acquirer, partner, category, payee type, request creator model, and funds-flow risks exist.

`DOC-04` determines how PayPlus operationalizes and certifies controls against those risks.

`DOC-04` should not override `DOC-03`.

If `DOC-03` identifies an unresolved critical issue, `DOC-04` must either:

- block launch;
- require remediation;
- require formal risk acceptance, if acceptable; or
- narrow the launch scope.

Examples:

| DOC-03 Output | DOC-04 Response |
| --- | --- |
| PSP does not approve a category. | Category is prohibited or blocked. |
| Legal role uncertain for a flow. | Flow cannot launch until assessed or redesigned. |
| Fee model requires disclosure. | Disclosure control becomes T0. |
| Payout before settlement creates liquidity risk. | Finance reserve and reconciliation controls become T0/T1. |
| Multi-card support uncertain. | Multi-card is excluded from MVP or requires expansion certification. |
| Payee verification is required. | Payee verification control becomes T1 or T0 depending on risk. |
| Payee-created request model changes PayPlus role analysis. | Payee-created request gate becomes T0 for that feature until assessed and approved. |
| PSP/acquirer does not approve payee-created requests. | Payee-created request functionality is disabled or redesigned. |
| Landlord-created rent requests require enhanced controls. | Landlord/rent gate becomes T0 if rent is enabled. |
| Partner requires payee onboarding or sub-merchant checks. | Payee onboarding and capability controls become launch blockers for enabled payee-created request flows. |
| Payer authorization evidence is required for disputes. | Payer authorization logging and evidence package controls become T0/T1. |
| Payer/payee privacy boundaries are required. | Access control, privacy, support visibility, and communication controls become T1 or T0 depending on risk. |

---

## 25. Relationship to Launch Readiness

`DOC-20 Testing, UAT, Release & Go-Live Checklist` should convert `DOC-04` controls into an executable checklist.

`DOC-20` should include:

- each applicable `T0` and `T1` control;
- each applicable `T0 if enabled` and `T1 if enabled` control for payee-created request features;
- test case references;
- evidence links;
- owners;
- status;
- launch decision;
- open exceptions;
- accepted risks;
- approver signatures.

No launch should proceed if `DOC-20` shows unresolved `T0` gaps.

No payee-created request feature should launch if `DOC-20` shows unresolved `T0 if enabled` gaps for that feature.

---

## 26. Assumptions

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
| `ASM-DOC04-011` | Payee-created request capability may be included in MVP only if payee onboarding, evidence, payer acceptance, risk, payout, reconciliation, privacy, and support controls are approved. | Product / Compliance / Risk | Open |
| `ASM-DOC04-012` | Payer authorization remains mandatory for all payee-created requests. | Product / Legal / Payments | Open |
| `ASM-DOC04-013` | Landlord-created rent requests require enhanced onboarding, tenancy evidence, and relationship-risk controls if enabled. | Legal / Compliance / Risk | Open |
| `ASM-DOC04-014` | Payee-created requests will not create wallet, stored-value, cashout, or unrestricted transfer functionality. | Product / Legal / Compliance | Open |
| `ASM-DOC04-015` | Payee-created request controls may require additional PSP/acquirer, payout provider, and partner confirmations. | Payments / Compliance | Open |
| `ASM-DOC04-016` | Payer/payee privacy boundaries must be defined before payee-created requests are enabled. | Privacy / Security | Open |

---

## 27. Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC04-001` | T0 blockers cannot be waived for MVP launch. | Prevents launch with unacceptable legal, partner, payment, security, or user-protection gaps. | Project Owner / Compliance |
| `CON-DOC04-002` | No production card processing without approved PSP/acquirer and PCI scope. | Blocks card launch until partner and security readiness are complete. | Payments / Security |
| `CON-DOC04-003` | No production payout without payout provider readiness and reconciliation controls. | Blocks payout launch until operational and finance controls are ready. | Payments / Finance |
| `CON-DOC04-004` | No restricted category launch without explicit approval. | Prevents high-risk or unsupported use cases. | Compliance / Product |
| `CON-DOC04-005` | Fee model cannot launch without legal/product disclosure approval. | Prevents consumer protection and partner rule violations. | Legal / Product |
| `CON-DOC04-006` | Material changes require reassessment before release. | Prevents stale approvals and control gaps. | Compliance / Engineering |
| `CON-DOC04-007` | Control evidence must be retained and retrievable. | Enables certification, audit, and partner review. | Compliance |
| `CON-DOC04-008` | Launch approval is scope-specific. | Prevents approval reuse for unassessed flows or categories. | Compliance |
| `CON-DOC04-009` | T1 exceptions require formal risk acceptance and remediation plan. | Prevents unmanaged launch risk. | Compliance |
| `CON-DOC04-010` | Daily monitoring is required during controlled launch. | Enables early detection of payment, fraud, payout, request-abuse, and support issues. | Operations / Compliance |
| `CON-DOC04-011` | Payee-created request capability cannot launch without approved payee onboarding and verification controls. | Prevents unapproved payee-created requests, cashout, and fake obligation risk. | Product / Compliance / Risk |
| `CON-DOC04-012` | Payee-created requests cannot trigger payer funding, capture, or payout without payer authorization. | Prevents unauthorized payment and consumer harm. | Product / Payments / Legal |
| `CON-DOC04-013` | Payee-created requests must meet evidence and risk controls equivalent to payer-created requests. | Prevents weakened controls based on request origin. | Compliance / Risk |
| `CON-DOC04-014` | Landlord-created rent requests cannot launch without approved landlord onboarding, tenancy evidence, and rent-specific risk controls. | Prevents rent-based cashout, fake rent, and collusion risk. | Legal / Compliance / Risk |
| `CON-DOC04-015` | Payer/payee data visibility controls must be implemented before payee-created request launch. | Prevents privacy, security, and trust failures. | Privacy / Security |
| `CON-DOC04-016` | Payee-created request functionality must be feature-gated by scope, payee type, category, risk status, and partner approval. | Prevents unsupported feature exposure. | Product / Engineering / Compliance |

---

## 28. Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
| --- | --- | --- | --- | --- |
| `DEP-DOC04-001` | Completed or substantially completed DOC-03 assessment. | Regulatory, partner, category, payee type, request creator model, and funds-flow control design. | Legal / Compliance / Payments | Open |
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

## 29. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC04-001` | PayPlus launches without clear regulatory role or licensing path. | Regulatory breach, forced suspension, partner termination. | T0 regulatory role and licensing gate. | Legal / Compliance | Open |
| `RISK-DOC04-002` | PSP/acquirer does not support actual PayPlus flow. | Processing disruption, fines, reserves, termination. | Written partner approval and contract review. | Payments / Legal | Open |
| `RISK-DOC04-003` | Category is misclassified or unsupported. | Partner rejection, chargebacks, compliance risk. | Approved/restricted/prohibited category controls. | Compliance / Product | Open |
| `RISK-DOC04-004` | Transaction is treated as quasi-cash, money transfer, or cash advance unexpectedly. | Higher costs, user complaints, issuer declines. | MCC/classification review and user disclosures. | Payments / Legal | Open |
| `RISK-DOC04-005` | Fee disclosure is incomplete or misleading. | Consumer complaints, regulatory risk, refund exposure. | T0 disclosure testing and evidence. | Legal / Product | Open |
| `RISK-DOC04-006` | User routes funds to self or collusive payee. | Cashout, fraud, financial loss. | Payee verification, self-payment detection, velocity limits. | Risk / Compliance | Open |
| `RISK-DOC04-007` | Payout occurs before funding certainty and later chargeback creates loss. | Financial loss and liquidity stress. | Settlement timing review, reserves, limits, risk rules. | Finance / Risk | Open |
| `RISK-DOC04-008` | Multi-source funding causes refund, chargeback, and reconciliation failures. | Operational breaks and user harm. | Exclude from MVP or require separate certification. | Product / Payments | Open |
| `RISK-DOC04-009` | Reconciliation fails to detect settlement or payout breaks. | Financial loss and inaccurate reporting. | Daily reconciliation and exception management. | Finance / Payments | Open |
| `RISK-DOC04-010` | PCI scope is underestimated. | Security breach, compliance failure, remediation cost. | PCI scope review and tokenized architecture. | Security | Open |
| `RISK-DOC04-011` | Evidence is incomplete or not retrievable. | Failed certification, audit, or partner review. | Evidence repository and system-of-record mapping. | Compliance | Open |
| `RISK-DOC04-012` | Critical launch risk is accepted informally. | Unmanaged legal, partner, user, or financial exposure. | Risk acceptance authority matrix. | Compliance / Project Owner | Open |
| `RISK-DOC04-013` | Operational teams cannot handle refunds, payout failures, chargebacks, or complaints. | User harm, losses, reputation damage. | SOPs, training, support readiness gates. | Operations | Open |
| `RISK-DOC04-014` | Material product change invalidates prior approvals. | Regulatory or partner breach. | Change management and recertification triggers. | Compliance / Engineering | Open |
| `RISK-DOC04-015` | Vendor or partner control failure affects PayPlus operations. | Payment disruption, security, privacy, or settlement failure. | Vendor oversight and partner monitoring. | Compliance / Payments / Security | Open |
| `RISK-DOC04-016` | Payee-created request model is launched without regulatory or partner approval. | Licensing, partner termination, fines, or forced suspension. | Payee-created request readiness gate and DOC-03 assessment. | Legal / Compliance / Payments | Open |
| `RISK-DOC04-017` | Payee onboarding is too weak for request creation or payout. | Fraud, cashout, fake invoices, partner risk. | Payee onboarding controls, verification, sanctions, and capability gating. | Compliance / Risk | Open |
| `RISK-DOC04-018` | Payee-created requests trigger funding or payout without payer authorization. | Unauthorized payment, complaints, disputes, regulatory risk. | T0 payer authorization control and state gating. | Product / Payments / Engineering | Open |
| `RISK-DOC04-019` | Payee-created requests are used for fake, inflated, duplicate, or collusive obligations. | Fraud, chargebacks, regulatory risk, partner escalation. | Evidence requirements, payer-payee relationship checks, abuse monitoring, manual review. | Risk / Compliance | Open |
| `RISK-DOC04-020` | Landlord-created rent requests are used for self-payment or disguised cashout. | High fraud and cashout risk. | Landlord verification, tenancy evidence, rent controls, limits, manual review. | Risk / Operations | Open |
| `RISK-DOC04-021` | Payer believes a payee-created request is mandatory, already validated, or already paid. | Complaints, disputes, unfair experience risk. | Request-origin disclosure, explicit payer acceptance, no auto-charge. | Product / Legal | Open |
| `RISK-DOC04-022` | Payee sees payer-sensitive payment, card, risk, or private profile information. | Privacy, security, and trust risk. | Payer/payee data boundary, RBAC, support visibility controls. | Privacy / Security | Open |
| `RISK-DOC04-023` | Payer receives excessive payee-sensitive data or evidence. | Privacy, contractual, or trust risk. | Evidence minimization, approved evidence summaries, privacy review. | Privacy / Legal | Open |
| `RISK-DOC04-024` | Payee changes material request details after payer authorization. | Unauthorized payment terms, disputes, chargebacks. | Material change lock and renewed authorization requirement. | Product / Engineering | Open |
| `RISK-DOC04-025` | Payee-created request workflow increases operational review load beyond MVP capacity. | Support delays, review backlogs, launch readiness risk. | Controlled scope, review queues, limits, monitoring, phased rollout. | Operations / Product | Open |
| `RISK-DOC04-026` | Chargeback evidence for payee-created requests is insufficient. | Losses and failed representment. | Evidence package linking request origin, payee evidence, payer authorization, disclosure, communication, and payout proof. | Payments / Operations | Open |

---

## 30. Downstream Document Impact

`DOC-04` should guide downstream documents as follows:

| Downstream Document | Impact |
| --- | --- |
| `DOC-05` | Product requirements must include T0/T1 compliance-critical controls and launch blockers, including payee-created request controls where enabled. |
| `DOC-06` | User, payer, payee, landlord, biller, and partner journeys must support user eligibility, payee onboarding, payer authorization, request-origin clarity, consent, screening, and anti-cashout controls. |
| `DOC-07` | Content and disclosure requirements must satisfy fee, timing, role, refund, cancellation, request-origin, payer authorization, and responsibility disclosures. |
| `DOC-08` | Notifications and receipts must support authorization evidence, payment status, payee-created request status, refund status, failure handling, payer/payee communication, and audit controls. |
| `DOC-09` | Payment and settlement requirements must reflect approved funds flow, request creator model, payer acceptance, authorization, capture, multi-source constraints, consent, and transaction logs. |
| `DOC-10` | Payout and reconciliation requirements must implement daily reconciliation, payee payout eligibility, payout exceptions, settlement reports, and ledger mapping. |
| `DOC-11` | Refund, cancellation, chargeback, payer rejection, payer query, payer dispute, payee withdrawal, and dispute requirements must support evidence, allocation, timing, and liability controls. |
| `DOC-12` | Bill category, document AI/OCR, evidence, payee verification, landlord verification, invoice evidence, rent evidence, and manual review requirements must satisfy control requirements. |
| `DOC-13` | Promotion controls must account for fee disclosure, abuse monitoring, reversal, payer/payee cost allocation, and request-origin treatment where applicable. |
| `DOC-14` | AML, sanctions, fraud, velocity, anti-cashout, payer-payee relationship, fake invoice, fake rent, request abuse, and payee risk controls must implement the baseline MVP control requirements. |
| `DOC-15` | Privacy, retention, data minimization, consent, payer/payee visibility, data subject rights, and sensitive document handling must satisfy T0/T1 controls. |
| `DOC-16` | Technical architecture must support service boundaries, integrations, idempotency, auditability, payee request services, reliability, and safe degradation controls. |
| `DOC-17` | APIs and third-party integrations must support PSP/acquirer, payout, OCR, notification, webhook, payee request, idempotency, and partner reporting requirements. |
| `DOC-18` | Data model and ledger must support evidence, creator type, payee-created request records, parent-child transaction linkage, fee records, payout records, refunds, chargebacks, reconciliation, and reporting. |
| `DOC-19` | Security, authentication, PCI, tokenization, RBAC, payee access, payer/payee data boundary, admin access, encryption, and audit logging requirements must satisfy T0/T1 controls. |
| `DOC-20` | Launch checklist must convert DOC-04 gates, including payee-created request gates if enabled, into executable go/no-go criteria. |
| `DOC-21` | Runbooks must operationalize incidents, payout failures, reconciliation breaks, refunds, chargebacks, complaints, partner outages, payee onboarding exceptions, payee-created request disputes, and control exceptions. |

---

## 31. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC04-001` | What exact MVP jurisdiction is in scope? | Project Owner / Legal | Critical | Open |
| `OQ-DOC04-002` | What exact bill categories are in MVP? | Product / Compliance | Critical | Open |
| `OQ-DOC04-003` | What is the final MVP funds flow? | Product / Payments / Legal | Critical | Open |
| `OQ-DOC04-004` | Is PayPlus merchant of record, agent, PayFac, marketplace, money transmitter, technical provider, or another role? | Legal / Compliance | Critical | Open |
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
| `OQ-DOC04-019` | What records must be retained for regulatory, partner, dispute, tax, finance, and audit purposes? | Legal / Compliance / Finance | High | Open |
| `OQ-DOC04-020` | What systems of record will store consent, authorization, risk decisions, payouts, refunds, disputes, and reconciliation evidence? | Engineering / Compliance | High | Open |
| `OQ-DOC04-021` | Who has final authority to approve MVP launch? | Project Owner / Compliance | Critical | Open |
| `OQ-DOC04-022` | What post-launch monitoring cadence is acceptable after stabilization? | Compliance / Operations | Medium | Open |
| `OQ-DOC04-023` | Are payee-created payment requests included in MVP, pilot, or post-MVP scope? | Project Owner / Product / Compliance | Critical | Open |
| `OQ-DOC04-024` | Which payee types can be onboarded to create payment requests? | Product / Risk / Compliance | Critical | Open |
| `OQ-DOC04-025` | What payee onboarding, verification, sanctions, payout destination, and capability checks are required? | Compliance / Risk / Operations | Critical | Open |
| `OQ-DOC04-026` | Does the payee-created request model require additional PSP/acquirer, payout provider, or partner confirmation? | Payments / Legal / Compliance | Critical | Open |
| `OQ-DOC04-027` | How must payer authorization be captured for payee-created requests? | Product / Legal / Payments | Critical | Open |
| `OQ-DOC04-028` | What evidence is required for payee-created bill, invoice, fee, or rent requests? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC04-029` | Is landlord-created rent request creation included in MVP or deferred? | Product / Legal / Risk | Critical | Open |
| `OQ-DOC04-030` | What landlord onboarding, tenancy evidence, property reference, and payer-landlord relationship checks are required? | Product / Legal / Risk / Operations | Critical | Open |
| `OQ-DOC04-031` | What payer response options are supported for payee-created requests? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-032` | What payer rejection, query, dispute, or request-for-clarification procedure applies before authorization? | Product / Operations / Legal | High | Open |
| `OQ-DOC04-033` | What information from a payee-created request can be shown to the payer, and what payer information can be shown to the payee? | Product / Privacy / Security | High | Open |
| `OQ-DOC04-034` | What monitoring is required to detect fake invoices, fake rent requests, related-party abuse, and payee-created request spam? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC04-035` | Are recurring payee-created rent or invoice requests allowed, or must each request be individually created and authorized? | Product / Legal / Payments | High | Open |
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
- evidence requirements;
- evidence systems of record;
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

This document should be treated as the governing compliance readiness framework for PayPlus MVP and future expansion. It should be updated whenever the launch scope, funds flow, partner model, jurisdiction, bill category, payment method, payout method, fee model, risk model, regulatory interpretation, payee type, payee onboarding model, request creator model, or payee-created request flow changes.

If payee-created requests are included in MVP or pilot scope, all payee onboarding, evidence, payer authorization, request lifecycle, risk, payout, privacy, support, reconciliation, and monitoring requirements marked `T0 if enabled` or `T1 if enabled` must be mapped to test cases, evidence records, and launch readiness gates in `DOC-20`.

---

## 33. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-04` Compliance Certification Roadmap & Control Framework. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Expanded into broad compliance roadmap and control framework with control domains, starter matrix, launch gates, evidence requirements, testing, remediation, governance, assumptions, constraints, dependencies, risks, downstream impact, and acceptance criteria. |
| `0.3.0` | `2026-05-26` | Product Documentation Team | Reframed as PayPlus-specific compliance certification framework with certification definition, MVP compliance posture, control tiering, non-waivable launch blockers, risk acceptance authority, MVP minimum control baseline, evidence system mapping, scope-specific launch gates, and stronger DOC-03/DOC-20 linkage. |
| `0.4.0` | `2026-05-27` | Product Documentation Team | Updated control framework to align with `DOC-05 v0.2.0` payee onboarding and payee-created bill, invoice, fee, and rent payment request capability. Added payee-created request certification, payee onboarding controls, payer authorization blockers, request evidence controls, landlord/rent controls, payer-payee relationship risk, payee-created request abuse monitoring, payer/payee privacy boundaries, support/dispute controls, expanded gates, dependencies, risks, open questions, and downstream document impacts. |
