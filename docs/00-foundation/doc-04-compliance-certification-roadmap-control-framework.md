---
document_id: DOC-04
title: Compliance Certification Roadmap & Control Framework
version: 0.3.0
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
last_updated: 2026-05-26
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User, Biller, Payee & Partner Onboarding
  - DOC-07 Content, Disclosure & User Communication
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-13 Admin, Risk & Operations Console
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Customer Support, Complaints & Disputes
  - DOC-16 Security, Privacy & Data Protection
  - DOC-17 Infrastructure, Reliability & Observability
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-20 Launch Readiness, QA & Go-Live Checklist
  - DOC-21 Operating Runbooks & Incident Response
---

# DOC-04 — Compliance Certification Roadmap & Control Framework

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
- what must be revisited before scaling, adding categories, adding jurisdictions, changing funds flow, or adding payment partners.

This document is intended to be more than a generic compliance checklist. It is a PayPlus-specific control framework for a bill-payment product that may involve card-funded payments, service fees, third-party payees, multi-source funding, payout timing risk, chargebacks after payout, and PSP/acquirer dependency.

---

## 2. Definition of Compliance Certification

For PayPlus, “compliance certification” does not mean a single external regulatory certificate unless one is specifically required.

Instead, compliance certification means a documented internal and partner-supported readiness decision that confirms applicable controls have been designed, implemented, tested, evidenced, and approved for a defined launch scope.

Certification may include several components.

| Certification Type | Meaning | Required Before |
|---|---|---|
| Internal launch certification | Internal approval that required launch controls are ready for the approved MVP scope. | MVP launch |
| Regulatory readiness certification | Legal and Compliance confirmation that regulatory role, licensing path, exemptions, or partner coverage have been assessed. | MVP launch / jurisdiction expansion |
| PSP/acquirer readiness certification | Written or contract-based confirmation that the PSP/acquirer supports the PayPlus use case, funds flow, categories, MCC/classification, fees, and risk model. | Production card processing |
| Payout readiness certification | Confirmation that payout provider, rails, reconciliation, exception handling, and settlement timing are ready. | Production payouts |
| Security and PCI readiness certification | Confirmation of PCI scope, card data handling model, access controls, vulnerability remediation, and security review. | Production card processing |
| Privacy readiness certification | Confirmation that data map, privacy notice, consent, retention, deletion, and data processing requirements are ready. | MVP launch |
| AML/sanctions/fraud readiness certification | Confirmation that required screening, risk rules, monitoring, escalation, and recordkeeping controls are ready. | MVP launch |
| Consumer protection readiness certification | Confirmation that user fees, timing, role, refund, cancellation, support, and dispute disclosures are implemented and evidenced. | MVP launch |
| Operational readiness certification | Confirmation that support, complaints, refunds, chargebacks, payout exceptions, incident response, and reconciliation operations are ready. | MVP launch |
| Expansion certification | Re-certification for new jurisdictions, bill categories, payment methods, PSPs, payout providers, or material funds-flow changes. | Before expansion |

Each certification must be tied to a defined scope. Approval for one jurisdiction, category, partner, or funds flow does not imply approval for another.

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
- Complete PCI DSS implementation plan.
- Complete SOC 2 audit plan.
- Complete privacy program.
- Product PRD.
- Technical architecture specification.
- Partner contract.
- Customer support SOP.
- QA test suite.
- Incident response runbook.

Those items must be owned in the appropriate legal, compliance, risk, security, product, engineering, finance, operations, or partner documents.

---

## 5. PayPlus-Specific Risk Themes

The control framework must specifically address the following PayPlus risk themes.

| Theme ID | Risk Theme | Why It Matters |
|---|---|---|
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
| `THEME-DOC04-012` | Product changes may alter regulatory classification. | Changes to funds flow, categories, fees, payout timing, or custody can invalidate prior approvals. |

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
- crypto, gambling, gift card, stored value, investment, or cash-equivalent payments;
- cross-border payouts;
- FX;
- wallet or stored balance functionality;
- payout before funding certainty without approved credit and liquidity controls;
- multi-card funding unless specifically approved by PSP/acquirer, Legal, Compliance, Risk, Payments, and Finance.

---

## 7. Control Tiering

Controls are tiered according to launch criticality and risk.

| Tier | Name | Meaning | Launch Impact |
|---|---|---|---|
| `T0` | Non-waivable blocker | Mandatory control required for legal, partner, security, financial, or user-protection reasons. | Cannot launch without completion. |
| `T1` | Critical launch control | Required for MVP launch unless formally accepted by authorized approvers. | Blocks launch unless remediated or formally accepted. |
| `T2` | Important operating control | Required for stable operation, but may be completed shortly after launch with approved mitigation. | May launch with approved remediation plan. |
| `T3` | Scale or maturity control | Required before scaling, certification maturity, audit maturity, or expansion. | Does not block MVP, but blocks scale or expansion. |

Each control in the control matrix must be assigned a tier.

---

## 8. Non-Waivable Launch Blockers

The following items are non-waivable for MVP launch.

PayPlus must not launch if any `T0` blocker is unresolved.

| Blocker ID | Non-Waivable Requirement | Owner |
|---|---|---|
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

---

## 9. Risk Acceptance Authority

Some risks may be accepted. Others may not.

Risk acceptance must be explicit, documented, time-bound, and tied to compensating controls.

| Risk Severity | Who May Accept | Conditions |
|---|---|---|
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

---

## 10. Control Domains

PayPlus controls are grouped into the following domains.

| Domain ID | Domain | Primary Owner | Related Documents |
|---|---|---|---|
| `CD-DOC04-001` | Governance, accountability, certification, and approvals | Compliance | DOC-00, DOC-20 |
| `CD-DOC04-002` | Regulatory role, licensing, exemptions, and legal obligations | Legal / Compliance | DOC-03 |
| `CD-DOC04-003` | PSP, acquirer, card network, payout provider, and partner readiness | Payments | DOC-03, DOC-09, DOC-10 |
| `CD-DOC04-004` | Category eligibility, restricted categories, and payee acceptability | Compliance / Product | DOC-03, DOC-06 |
| `CD-DOC04-005` | User onboarding, identity, consent, and eligibility | Product / Compliance | DOC-06 |
| `CD-DOC04-006` | Payee onboarding, verification, and anti-cashout | Compliance / Risk / Operations | DOC-06, DOC-14 |
| `CD-DOC04-007` | AML, sanctions, and financial crime controls | Compliance | DOC-14 |
| `CD-DOC04-008` | Fraud, abuse, velocity, and transaction risk | Risk | DOC-14 |
| `CD-DOC04-009` | Consumer protection, disclosures, consent, and receipts | Legal / Product | DOC-07, DOC-08 |
| `CD-DOC04-010` | Fees, pricing, tax, economics, and margin controls | Finance / Product | DOC-02, DOC-07 |
| `CD-DOC04-011` | Authorization, capture, settlement, and funding controls | Payments / Engineering | DOC-09 |
| `CD-DOC04-012` | Payout, reconciliation, reserves, and ledger controls | Finance / Payments | DOC-10, DOC-18 |
| `CD-DOC04-013` | Refunds, cancellations, chargebacks, and disputes | Operations / Payments | DOC-11, DOC-15 |
| `CD-DOC04-014` | Customer support, complaints, and escalation | Operations | DOC-15 |
| `CD-DOC04-015` | Security, PCI, access, and infrastructure controls | Security / Engineering | DOC-16, DOC-17 |
| `CD-DOC04-016` | Privacy, data protection, retention, and deletion | Privacy / Legal | DOC-16 |
| `CD-DOC04-017` | Reporting, recordkeeping, evidence, and auditability | Compliance / Finance | DOC-18 |
| `CD-DOC04-018` | Vendor and partner oversight | Compliance / Legal / Payments | DOC-03 |
| `CD-DOC04-019` | Incident response, business continuity, and resilience | Security / Operations | DOC-17, DOC-21 |
| `CD-DOC04-020` | Change management and release governance | Engineering / Compliance | DOC-20 |
| `CD-DOC04-021` | Training, awareness, and access certification | Compliance / Security | DOC-16, DOC-21 |

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

### 11.2 Product and Disclosure Baseline

The product must show, before authorization:

- bill amount;
- PayPlus service fee;
- taxes, if applicable;
- total amount charged;
- payee or biller identity;
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
- amount and fee shown;
- payment authorization record.

### 11.3 User and Payee Baseline

PayPlus must define:

- minimum user information required;
- user eligibility rules;
- blocked user criteria;
- payee information required;
- payee verification method;
- payee ownership or relationship checks where applicable;
- self-payment controls;
- high-risk payee escalation process;
- prohibited payee categories.

### 11.4 AML, Sanctions, Fraud, and Anti-Cashout Baseline

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
- suspicious refund monitoring;
- manual review queue;
- risk decision audit logs.

### 11.5 Payment, Payout, and Reconciliation Baseline

MVP must include:

- unique transaction IDs;
- parent-child linkage for funding events, if multi-source funding exists;
- authorization and capture logs;
- settlement status tracking;
- payout status tracking;
- fee ledger entries;
- refund ledger entries;
- chargeback ledger entries;
- daily reconciliation process;
- unresolved exception log;
- payout failure process;
- refund failure process;
- chargeback evidence process.

### 11.6 Security, Privacy, and Access Baseline

MVP must include:

- PCI scope decision;
- tokenized card handling where applicable;
- no unnecessary storage of sensitive card data;
- encryption in transit;
- encryption at rest for sensitive data;
- role-based access for admin tools;
- audit logs for sensitive actions;
- vulnerability review before launch;
- privacy notice;
- data map;
- data retention approach;
- incident escalation path.

### 11.7 Operations Baseline

MVP must include:

- refund procedure;
- cancellation procedure;
- payout failure procedure;
- chargeback procedure;
- complaint intake and escalation;
- support macros for payment timing, fees, refunds, and failed payments;
- internal escalation contacts;
- incident severity levels;
- daily launch monitoring during initial production period.

---

## 12. Control Matrix

The following matrix defines the initial PayPlus control set.

| Control ID | Tier | Domain | Control Objective | Type | Frequency | Owner | Evidence |
|---|---|---|---|---|---|---|---|
| `CTRL-DOC04-001` | `T0` | Governance | Maintain launch certification scope, approvers, and evidence package. | Directive | Per launch | Compliance | Launch certification package, approval log. |
| `CTRL-DOC04-002` | `T0` | Regulatory | Confirm regulatory role and licensing path for MVP jurisdiction and funds flow. | Preventive | Per launch / Material change | Legal / Compliance | DOC-03 assessment, legal memo, approval record. |
| `CTRL-DOC04-003` | `T0` | Partner readiness | Confirm PSP/acquirer support for PayPlus use case, categories, fees, and funds flow. | Preventive | Per partner / Material change | Payments | Partner approval, contract, underwriting record. |
| `CTRL-DOC04-004` | `T0` | Payout readiness | Confirm payout provider, payout rails, settlement timing, and exception handling. | Preventive | Per launch / Material change | Payments / Finance | Payout approval, test payout evidence, SOP. |
| `CTRL-DOC04-005` | `T0` | Category eligibility | Maintain and enforce MVP approved, restricted, and prohibited categories. | Preventive | Per launch / Monthly | Compliance / Product | Category register, configuration, approval log. |
| `CTRL-DOC04-006` | `T1` | Payee controls | Verify payee eligibility before payout. | Preventive | Per payee | Compliance / Operations | Payee verification record, review notes. |
| `CTRL-DOC04-007` | `T1` | User controls | Capture required user information and terms/privacy consent. | Preventive | Per user | Product / Compliance | User profile, consent logs. |
| `CTRL-DOC04-008` | `T0` | Sanctions | Screen required parties and escalate potential matches. | Preventive / Detective | Onboarding / Ongoing | Compliance | Screening logs, match disposition records. |
| `CTRL-DOC04-009` | `T0` | Fraud / Anti-cashout | Apply baseline transaction limits, velocity rules, and self-payment controls. | Preventive / Detective | Real-time / Daily | Risk | Rule configuration, decision logs, alerts. |
| `CTRL-DOC04-010` | `T1` | Manual review | Route high-risk transactions, users, or payees to manual review. | Preventive | Per trigger | Risk / Operations | Case queue, disposition logs. |
| `CTRL-DOC04-011` | `T0` | Disclosures | Display bill amount, service fee, total charge, timing, role, and refund/cancellation terms before authorization. | Preventive | Per transaction | Product / Legal | UI screenshots, disclosure version, consent logs. |
| `CTRL-DOC04-012` | `T0` | Payment authorization | Capture user authorization and immutable transaction details. | Preventive | Per transaction | Product / Engineering | Authorization logs, transaction record. |
| `CTRL-DOC04-013` | `T1` | Fee controls | Ensure fee calculation matches approved pricing and margin rules. | Preventive / Detective | Per transaction / Daily | Finance / Product | Pricing configuration, fee reports. |
| `CTRL-DOC04-014` | `T0` | Settlement reconciliation | Reconcile PSP settlement, fees, payouts, refunds, chargebacks, reserves, ledger, and bank records. | Detective | Daily | Finance / Payments | Reconciliation report, exception log. |
| `CTRL-DOC04-015` | `T0` | Payout exceptions | Detect and resolve failed, delayed, returned, or misdirected payouts. | Corrective | Daily / Per exception | Payments / Operations | Payout exception log, resolution record. |
| `CTRL-DOC04-016` | `T0` | Refunds | Process refunds according to approved rules and ledger treatment. | Preventive / Corrective | Per refund | Operations / Payments | Refund record, approval log, ledger entry. |
| `CTRL-DOC04-017` | `T1` | Chargebacks | Track, evidence, and respond to chargebacks within deadlines. | Corrective | Per dispute | Operations / Payments | Dispute case, evidence package, outcome. |
| `CTRL-DOC04-018` | `T1` | Complaints | Log, classify, investigate, and resolve complaints. | Corrective | Per complaint | Operations | Complaint register, response record. |
| `CTRL-DOC04-019` | `T0` | PCI | Approve PCI scope and card data handling model before card processing. | Preventive | Per launch / Annual / Material change | Security | PCI scope document, architecture diagram, SAQ/AOC if applicable. |
| `CTRL-DOC04-020` | `T1` | Access control | Restrict admin and sensitive data access based on role. | Preventive | Continuous / Quarterly | Security / Engineering | Role matrix, access review, audit logs. |
| `CTRL-DOC04-021` | `T1` | Audit logging | Log sensitive admin, payment, payout, refund, risk, and support actions. | Detective | Continuous | Engineering / Security | Audit logs, log retention evidence. |
| `CTRL-DOC04-022` | `T0` | Privacy | Provide privacy notice and capture required consent. | Preventive | Per user / Material change | Privacy / Product | Privacy version, consent logs. |
| `CTRL-DOC04-023` | `T1` | Data retention | Retain and delete records according to approved schedule. | Preventive / Corrective | Continuous / Periodic | Privacy / Engineering | Retention policy, deletion logs. |
| `CTRL-DOC04-024` | `T1` | Vendor diligence | Review material vendors and payment partners before production use. | Preventive | Per vendor / Annual | Compliance / Security / Legal | Due diligence checklist, SOC report, contract review. |
| `CTRL-DOC04-025` | `T0` | Incident escalation | Maintain incident severity levels, escalation contacts, and notification process. | Corrective | Per incident / Per launch | Security / Operations | Incident runbook, escalation matrix. |
| `CTRL-DOC04-026` | `T1` | Change management | Review product, risk, compliance, and technical changes before release. | Preventive | Per release | Engineering / Compliance | Change tickets, approvals, release notes. |
| `CTRL-DOC04-027` | `T1` | Regulatory/partner change monitoring | Monitor regulatory, card network, PSP, acquirer, payout provider, and contractual changes. | Detective | Monthly / Event-driven | Legal / Compliance / Payments | Monitoring log, impact assessment. |
| `CTRL-DOC04-028` | `T2` | Training | Provide role-based compliance, security, fraud, and support training. | Directive | On hire / Annual | Compliance / Security | Training completion records. |
| `CTRL-DOC04-029` | `T2` | Control testing | Test design and operating effectiveness of key controls. | Detective | Quarterly / Annual | Compliance / QA / Internal Audit | Test plan, samples, results, remediation log. |
| `CTRL-DOC04-030` | `T3` | SOC 2 readiness | Prepare for formal security/compliance audit maturity if commercially required. | Directive | Pre-scale / Annual | Security | SOC 2 readiness plan, gap assessment. |

---

## 13. Control-to-Evidence-to-System Mapping

Evidence must be mapped to a system of record.

| Evidence Type | System of Record | Owner |
|---|---|---|
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
| Payee verification record | Compliance case system / operations queue | Compliance / Operations |
| Sanctions screening result | Screening tool / compliance case system | Compliance |
| Fraud decision | Risk engine / risk decision logs | Risk / Engineering |
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
|---|---|---|---|
| `PH-DOC04-001` | Discovery | Identify product scope, jurisdiction, funds flow, categories, partners, and obligations. | Draft DOC-03, product scope, initial obligation inventory. |
| `PH-DOC04-002` | MVP Control Design | Define T0/T1 controls, owners, evidence, and launch blockers. | Approved control matrix and evidence plan. |
| `PH-DOC04-003` | MVP Control Build | Implement required product, partner, risk, payment, security, privacy, and operational controls. | T0 controls implemented; T1 controls implemented or risk-accepted. |
| `PH-DOC04-004` | MVP Control Test | Test critical controls and document exceptions. | T0 controls tested; critical exceptions closed. |
| `PH-DOC04-005` | MVP Certification | Assemble launch package and obtain approvals. | Launch certification signed. |
| `PH-DOC04-006` | Controlled Launch | Launch with enhanced monitoring and limited scope. | Daily monitoring, issue tracking, reconciliation, and support review active. |
| `PH-DOC04-007` | Stabilization | Validate operating effectiveness and remediate launch findings. | Initial post-launch control review completed. |
| `PH-DOC04-008` | Scale Readiness | Add T2/T3 maturity controls required for higher volume or enterprise readiness. | Control testing, vendor reassessment, SOC 2/PCI maturity as needed. |
| `PH-DOC04-009` | Expansion Certification | Re-certify for new jurisdictions, categories, partners, payment methods, or funds-flow changes. | Expansion certification approved before change. |

---

## 15. Launch Certification Package

The launch certification package must be assembled before MVP launch.

It must include:

- launch scope;
- jurisdiction scope;
- bill category scope;
- user scope;
- payee scope;
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
- terms and privacy evidence;
- sanctions control evidence;
- fraud and anti-cashout control evidence;
- user and payee onboarding evidence;
- PCI scope and security evidence;
- privacy and data protection evidence;
- partner due diligence evidence;
- contract approval evidence;
- settlement, reserve, and liquidity evidence;
- reconciliation test evidence;
- refund and chargeback readiness evidence;
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
|---|---|---|---|---|
| `GATE-DOC04-001` | `T0` | Launch scope locked | MVP jurisdiction, categories, payment methods, payout methods, and partners are defined. | Project Owner |
| `GATE-DOC04-002` | `T0` | Regulatory role approved | Regulatory role and licensing path are approved for the MVP flow. | Legal / Compliance |
| `GATE-DOC04-003` | `T0` | PSP/acquirer approval obtained | PSP/acquirer confirms support for use case, categories, fee model, and funds flow. | Payments |
| `GATE-DOC04-004` | `T0` | Payout readiness approved | Payout provider, rails, settlement timing, and exceptions are approved and tested. | Payments / Finance |
| `GATE-DOC04-005` | `T0` | Category controls implemented | Approved, restricted, and prohibited category controls are implemented. | Compliance / Product |
| `GATE-DOC04-006` | `T1` | User and payee controls ready | Onboarding, consent, verification, screening, and eligibility controls are implemented. | Product / Compliance |
| `GATE-DOC04-007` | `T0` | Sanctions controls ready | Required screening, escalation, and recordkeeping controls are implemented. | Compliance |
| `GATE-DOC04-008` | `T0` | Fraud and anti-cashout controls ready | Baseline limits, velocity, self-payment, payee, and manual review controls are implemented. | Risk |
| `GATE-DOC04-009` | `T0` | Fee and disclosure controls ready | Fee, total charge, timing, role, refund, and cancellation disclosures are approved and tested. | Legal / Product |
| `GATE-DOC04-010` | `T0` | Payment authorization controls ready | Authorization, capture, consent, and transaction logging are tested. | Payments / Engineering |
| `GATE-DOC04-011` | `T0` | Reconciliation controls ready | Settlement, payout, fee, refund, chargeback, reserve, ledger, and bank reconciliation is tested. | Finance / Payments |
| `GATE-DOC04-012` | `T0` | Security and PCI controls ready | PCI scope, card data model, access controls, and launch security review are complete. | Security |
| `GATE-DOC04-013` | `T0` | Privacy controls ready | Privacy notice, data map, consent, and retention approach are ready. | Privacy / Legal |
| `GATE-DOC04-014` | `T1` | Support and complaint controls ready | Support, complaint, dispute, refund, and chargeback procedures are ready. | Operations |
| `GATE-DOC04-015` | `T0` | Incident escalation ready | Incident severity model and escalation paths are documented. | Security / Operations |
| `GATE-DOC04-016` | `T0` | Evidence repository complete | Required T0 evidence is stored and linked to launch certification. | Compliance |
| `GATE-DOC04-017` | `T0` | Critical exceptions closed | T0 exceptions are closed; T1 exceptions are closed or accepted. | Compliance |
| `GATE-DOC04-018` | `T0` | Launch certification approved | Required approvers sign the certification package. | Project Owner / Compliance |

---

## 17. Control Testing

Critical controls must be tested before launch.

Testing should include:

| Test Area | Required Test |
|---|---|
| Fee disclosure | Confirm fee and total amount appear before authorization. |
| Consent logging | Confirm terms/privacy/disclosure consent is recorded with version and timestamp. |
| Category blocking | Confirm prohibited categories cannot be submitted or paid. |
| Payee verification | Confirm unverified or restricted payees cannot receive payout. |
| Sanctions handling | Confirm potential match creates escalation and blocks payout until disposition. |
| Fraud rules | Confirm limits, velocity rules, and high-risk triggers operate. |
| Self-payment detection | Confirm obvious user-to-self patterns are blocked or reviewed. |
| Authorization logging | Confirm transaction record links user, amount, fee, payee, payment method, and consent. |
| Payout flow | Confirm successful payout and failed payout paths. |
| Reconciliation | Confirm PSP settlement, payout, fee, refund, and ledger records can be matched. |
| Refund flow | Confirm refund allocation, ledger entries, and user communication. |
| Chargeback flow | Confirm evidence package can be assembled. |
| Access controls | Confirm admin roles restrict sensitive actions. |
| Audit logs | Confirm sensitive actions are logged. |
| Incident escalation | Confirm escalation contacts and severity model are usable. |

---

## 18. Exception and Remediation Management

Control exceptions must be logged.

| Field | Description |
|---|---|
| Exception ID | Unique exception identifier. |
| Control ID | Related control. |
| Tier | T0, T1, T2, or T3. |
| Severity | Critical, high, medium, low. |
| Description | Exception details. |
| Detection Date | When the issue was found. |
| Owner | Responsible remediation owner. |
| Root Cause | Cause of exception. |
| Impact | Compliance, financial, operational, user, security, privacy, or partner impact. |
| Temporary Mitigation | Interim control or workaround. |
| Remediation Plan | Corrective action. |
| Target Date | Due date. |
| Status | Open, in progress, remediated, accepted risk, closed. |
| Approver | Required approver for closure or acceptance. |
| Evidence | Proof of remediation. |

T0 exceptions cannot be accepted for MVP launch.

---

## 19. Regulatory and Partner Change Management

Material changes require reassessment.

Triggers include:

- new jurisdiction;
- new bill category;
- new payee type;
- new payment method;
- new payout method;
- new PSP or acquirer;
- new payout provider;
- changed funds flow;
- changed merchant of record structure;
- changed PayFac, marketplace, or agent model;
- changed fee model;
- changed MCC or transaction classification;
- changed settlement timing;
- changed reserve or holdback;
- changed refund or chargeback process;
- changed data handling;
- changed sanctions or AML requirement;
- changed card network, PSP, acquirer, payout provider, bank, or legal requirement;
- material fraud, chargeback, complaint, payout failure, or reconciliation issue.

A material change must not be released until Compliance determines whether recertification is required.

---

## 20. Vendor and Partner Oversight

Material vendors and partners must be reviewed before production use.

Payment partners require enhanced review because they may affect:

- regulatory coverage;
- PSP/acquirer approval;
- card network compliance;
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
- reporting capability review;
- incident and SLA review;
- annual or risk-based reassessment.

---

## 21. Training and Awareness

Before launch, relevant personnel should receive role-based training.

Required MVP training topics include:

- PayPlus product and funds flow;
- approved, restricted, and prohibited categories;
- fee and disclosure rules;
- user and payee eligibility;
- sanctions escalation;
- fraud and anti-cashout red flags;
- manual review procedures;
- refund and cancellation handling;
- chargeback evidence handling;
- complaint escalation;
- privacy and data handling;
- security and access obligations;
- incident escalation.

Training records should be retained.

---

## 22. Monitoring and Reporting

MVP launch should include enhanced monitoring.

Candidate daily launch metrics:

| Area | Metrics |
|---|---|
| Payments | Authorization rate, capture failures, payment failures, processor errors. |
| Payouts | Payout success rate, payout failures, delayed payouts, returned payouts. |
| Reconciliation | Unmatched transactions, settlement breaks, payout breaks, fee breaks. |
| Fraud | Rule triggers, manual review queue, blocked transactions, suspicious payees. |
| Anti-cashout | Self-payment alerts, payee concentration, suspicious refund behavior. |
| Sanctions | Screening hits, pending reviews, blocked parties. |
| Refunds | Refund volume, refund failure rate, refund reasons. |
| Chargebacks | New disputes, reason codes, exposure amount. |
| Complaints | Complaint volume, categories, response SLA, escalations. |
| Security | incidents, access anomalies, critical vulnerabilities. |
| Privacy | consent errors, data request issues, deletion exceptions. |
| Finance | gross volume, fees, reserves, losses, margin variance. |

Monitoring cadence:

| Period | Cadence |
|---|---|
| First 2 weeks after launch | Daily review |
| Weeks 3–8 | At least weekly review |
| After stabilization | Monthly governance review, unless risk indicators require more frequent review |

---

## 23. Governance Forums

| Forum | Frequency | Purpose | Participants |
|---|---|---|---|
| MVP Launch Readiness Review | Weekly pre-launch | Track gates, blockers, evidence, and risk acceptance. | Product, Compliance, Legal, Payments, Risk, Security, Finance, Operations, Engineering. |
| Daily Launch Monitoring | Daily during initial launch | Review live metrics, incidents, settlement, payout, fraud, complaints, and exceptions. | Compliance, Risk, Payments, Finance, Operations, Engineering. |
| Risk and Compliance Review | Monthly | Review compliance metrics, control exceptions, remediation, incidents, and regulatory changes. | Compliance, Legal, Risk, Security, Operations. |
| Payments and Reconciliation Review | Weekly / Monthly | Review settlement, payout, chargebacks, reserves, reconciliation, and partner issues. | Payments, Finance, Operations, Engineering. |
| Security and Privacy Review | Monthly / Quarterly | Review security posture, access, incidents, privacy issues, and vendor security. | Security, Privacy, Engineering, Legal. |
| Vendor and Partner Review | Quarterly / Annual | Review material vendor and partner performance, attestations, incidents, and renewals. | Compliance, Legal, Security, Payments, Finance. |
| Expansion Certification Review | Event-driven | Approve new jurisdictions, categories, partners, payment methods, or funds-flow changes. | Project Owner, Legal, Compliance, Payments, Risk, Security, Finance. |

---

## 24. Relationship to DOC-03

`DOC-03` determines what regulatory, PSP/acquirer, partner, category, and funds-flow risks exist.

`DOC-04` determines how PayPlus operationalizes and certifies controls against those risks.

`DOC-04` should not override `DOC-03`.

If `DOC-03` identifies an unresolved critical issue, `DOC-04` must either:

- block launch;
- require remediation;
- require formal risk acceptance, if acceptable; or
- narrow the launch scope.

Examples:

| DOC-03 Output | DOC-04 Response |
|---|---|
| PSP does not approve a category. | Category is prohibited or blocked. |
| Legal role uncertain for a flow. | Flow cannot launch until assessed or redesigned. |
| Fee model requires disclosure. | Disclosure control becomes T0. |
| Payout before settlement creates liquidity risk. | Finance reserve and reconciliation controls become T0/T1. |
| Multi-card support uncertain. | Multi-card is excluded from MVP or requires expansion certification. |
| Payee verification is required. | Payee verification control becomes T1 or T0 depending on risk. |

---

## 25. Relationship to Launch Readiness

`DOC-20 Launch Readiness, QA & Go-Live Checklist` should convert `DOC-04` controls into an executable checklist.

`DOC-20` should include:

- each applicable `T0` and `T1` control;
- test case references;
- evidence links;
- owners;
- status;
- launch decision;
- open exceptions;
- accepted risks;
- approver signatures.

No launch should proceed if `DOC-20` shows unresolved `T0` gaps.

---

## 26. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
|---|---|---|---|
| `ASM-DOC04-001` | PayPlus will launch with limited MVP scope. | Project Owner | Open |
| `ASM-DOC04-002` | PayPlus will require documented regulatory and partner approval before production launch. | Legal / Payments | Open |
| `ASM-DOC04-003` | PSP/acquirer requirements will materially affect allowable flows, categories, fees, and MCC/classification. | Payments | Open |
| `ASM-DOC04-004` | MVP will not include wallet, stored value, FX, cross-border payout, or unrestricted user-generated payees unless separately approved. | Product / Legal | Open |
| `ASM-DOC04-005` | Multi-card or multi-source funding requires separate approval and may be excluded from MVP. | Product / Payments | Open |
| `ASM-DOC04-006` | PCI scope will depend on final card data handling architecture. | Security | Open |
| `ASM-DOC04-007` | Fraud and anti-cashout controls are required even if formal AML obligations are limited. | Risk / Compliance | Open |
| `ASM-DOC04-008` | Daily reconciliation is required for MVP. | Finance / Payments | Open |
| `ASM-DOC04-009` | Evidence will be retained in approved systems of record. | Compliance | Open |
| `ASM-DOC04-010` | New jurisdictions, categories, partners, or funds-flow changes require recertification. | Compliance | Open |

---

## 27. Constraints

| Constraint ID | Constraint | Impact | Owner |
|---|---|---|---|
| `CON-DOC04-001` | T0 blockers cannot be waived for MVP launch. | Prevents launch with unacceptable legal, partner, payment, security, or user-protection gaps. | Project Owner / Compliance |
| `CON-DOC04-002` | No production card processing without approved PSP/acquirer and PCI scope. | Blocks card launch until partner and security readiness are complete. | Payments / Security |
| `CON-DOC04-003` | No production payout without payout provider readiness and reconciliation controls. | Blocks payout launch until operational and finance controls are ready. | Payments / Finance |
| `CON-DOC04-004` | No restricted category launch without explicit approval. | Prevents high-risk or unsupported use cases. | Compliance / Product |
| `CON-DOC04-005` | Fee model cannot launch without legal/product disclosure approval. | Prevents consumer protection and partner rule violations. | Legal / Product |
| `CON-DOC04-006` | Material changes require reassessment before release. | Prevents stale approvals and control gaps. | Compliance / Engineering |
| `CON-DOC04-007` | Control evidence must be retained and retrievable. | Enables certification, audit, and partner review. | Compliance |
| `CON-DOC04-008` | Launch approval is scope-specific. | Prevents approval reuse for unassessed flows or categories. | Compliance |
| `CON-DOC04-009` | T1 exceptions require formal risk acceptance and remediation plan. | Prevents unmanaged launch risk. | Compliance |
| `CON-DOC04-010` | Daily monitoring is required during controlled launch. | Enables early detection of payment, fraud, payout, and support issues. | Operations / Compliance |

---

## 28. Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
|---|---|---|---|---|
| `DEP-DOC04-001` | Completed or substantially completed DOC-03 assessment. | Regulatory, partner, category, and funds-flow control design. | Legal / Compliance / Payments | Open |
| `DEP-DOC04-002` | MVP product scope. | Launch certification scope. | Product | Open |
| `DEP-DOC04-003` | MVP jurisdiction. | Legal, privacy, AML, disclosure, and recordkeeping controls. | Legal / Project Owner | Open |
| `DEP-DOC04-004` | MVP bill categories. | Category approval, risk controls, and partner approval. | Product / Compliance | Open |
| `DEP-DOC04-005` | MVP funds flow diagram. | Regulatory, partner, payout, and reconciliation controls. | Product / Payments | Open |
| `DEP-DOC04-006` | PSP/acquirer selection and approval. | Card processing readiness. | Payments | Open |
| `DEP-DOC04-007` | Payout provider selection and approval. | Payout readiness. | Payments | Open |
| `DEP-DOC04-008` | Fee model. | Fee disclosure, pricing, margin, and partner review. | Product / Finance | Open |
| `DEP-DOC04-009` | Card data architecture. | PCI scope and security readiness. | Security / Engineering | Open |
| `DEP-DOC04-010` | User and payee onboarding model. | Verification, consent, screening, and anti-cashout controls. | Product / Compliance | Open |
| `DEP-DOC04-011` | Risk rules and review tools. | Fraud, velocity, and manual review controls. | Risk / Engineering | Open |
| `DEP-DOC04-012` | Terms, privacy notice, and disclosure drafts. | Consumer protection and privacy readiness. | Legal / Product | Open |
| `DEP-DOC04-013` | Ledger and reporting design. | Reconciliation, evidence, and monitoring. | Finance / Engineering | Open |
| `DEP-DOC04-014` | Operations SOPs. | Refunds, cancellations, chargebacks, complaints, payout exceptions. | Operations | Open |
| `DEP-DOC04-015` | Evidence repository. | Certification package and auditability. | Compliance / Security | Open |
| `DEP-DOC04-016` | QA/UAT test evidence. | Launch certification. | Product / Engineering / QA | Open |
| `DEP-DOC04-017` | Partner contracts and vendor due diligence. | Partner readiness and vendor oversight. | Legal / Payments / Compliance | Open |

---

## 29. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
|---|---|---|---|---|---|
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

---

## 30. Downstream Document Impact

`DOC-04` should guide downstream documents as follows:

| Downstream Document | Impact |
|---|---|
| `DOC-05` | Product requirements must include T0/T1 compliance-critical controls and launch blockers. |
| `DOC-06` | Onboarding requirements must support user eligibility, payee verification, consent, screening, and anti-cashout controls. |
| `DOC-07` | Content and disclosure requirements must satisfy fee, timing, role, refund, cancellation, and responsibility disclosures. |
| `DOC-08` | Notifications and receipts must support authorization evidence, payment status, refund status, failure handling, and user communication controls. |
| `DOC-09` | Payment and settlement requirements must reflect approved funds flow, authorization, capture, multi-source constraints, consent, and transaction logs. |
| `DOC-10` | Payout and reconciliation requirements must implement daily reconciliation, payout exceptions, settlement reports, and ledger mapping. |
| `DOC-11` | Refund, cancellation, chargeback, and dispute requirements must support evidence, allocation, timing, and liability controls. |
| `DOC-13` | Admin and risk console must support manual review, case management, audit logs, access control, and escalation. |
| `DOC-14` | AML, sanctions, fraud, velocity, and anti-cashout controls must implement the baseline MVP control requirements. |
| `DOC-15` | Support and complaints SOPs must support complaint logging, user communication, refund requests, dispute handling, and escalation. |
| `DOC-16` | Security, privacy, PCI, data retention, access, and audit logging requirements must satisfy T0/T1 controls. |
| `DOC-17` | Infrastructure and observability must support monitoring, incident detection, audit logs, and reliability controls. |
| `DOC-18` | Data model and ledger must support evidence, parent-child transaction linkage, fee records, payout records, refunds, chargebacks, reconciliation, and reporting. |
| `DOC-20` | Launch checklist must convert DOC-04 gates into executable go/no-go criteria. |
| `DOC-21` | Runbooks must operationalize incidents, payout failures, reconciliation breaks, refunds, chargebacks, complaints, partner outages, and control exceptions. |

---

## 31. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
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

---

## 32. Acceptance Criteria

`DOC-04` is acceptable when it clearly defines:

- what compliance certification means for PayPlus;
- PayPlus-specific risk themes;
- MVP compliance posture;
- control tiering;
- non-waivable launch blockers;
- risk acceptance authority;
- control domains;
- minimum MVP control baseline;
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

This document should be treated as the governing compliance readiness framework for PayPlus MVP and future expansion. It should be updated whenever the launch scope, funds flow, partner model, jurisdiction, bill category, payment method, payout method, fee model, risk model, or regulatory interpretation changes.

---

## 33. Version History

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-04` Compliance Certification Roadmap & Control Framework. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Expanded into broad compliance roadmap and control framework with control domains, starter matrix, launch gates, evidence requirements, testing, remediation, governance, assumptions, constraints, dependencies, risks, downstream impact, and acceptance criteria. |
| `0.3.0` | `2026-05-26` | Product Documentation Team | Reframed as PayPlus-specific compliance certification framework with certification definition, MVP compliance posture, control tiering, non-waivable launch blockers, risk acceptance authority, MVP minimum control baseline, evidence system mapping, scope-specific launch gates, and stronger DOC-03/DOC-20 linkage. |
