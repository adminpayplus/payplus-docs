---
document_id: DOC-03
title: Regulatory Assessment
version: 1.0.0
status: Founder Working Baseline
owner: Compliance / Payments Owner
reviewers:
  - Legal Lead
  - Compliance Lead
  - Payments Lead
  - Risk Lead
  - Finance Lead
  - Product Lead
approvers:
  - Project Owner
  - Legal Lead
  - Compliance Lead
  - Payments Lead
last_updated: 2026-08-19
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-04 Compliance Certification Roadmap & Control Framework
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
---

# DOC-03 - Regulatory Assessment

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-03` |
| **Title** | Regulatory Assessment |
| **Version** | `1.0.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Compliance / Payments Owner |
| **Reviewers** | Legal Lead<br>Compliance Lead<br>Payments Lead<br>Risk Lead<br>Finance Lead<br>Product Lead |
| **Approvers** | Project Owner<br>Legal Lead<br>Compliance Lead<br>Payments Lead |
| **Last Updated** | `2026-08-19` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Project Charter & Product Positioning<br>DOC-02 Business Model & Unit Economics<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Communication<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-16 Technical Architecture<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT, Release & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operations Runbook |

---

## 1. Purpose

This document defines the regulatory assessment framework for PayPlus.

It explains the intended regulatory posture of the PayPlus MVP and identifies the key legal, compliance, PSP/acquirer, payment partner, and risk questions that must be resolved before launch.

PayPlus is intended to operate as a **payer-authorized payment platform for accepted controlled Bill Categories and the separate Rent journey**. Bills use the accepted tiered Evidence model, while Rent retains mandatory attached Evidence; professional assessment remains required.

PayPlus is **not intended** to operate as:

- a wallet;
- a stored-value account;
- an e-money product;
- a cashout product;
- an arbitrary peer-to-peer transfer service;
- a general money transmission product independent of an underlying accepted controlled Bill source or separate Rent source.

This document is not a final legal opinion. Final legal, regulatory, licensing, card network, PSP/acquirer, tax, accounting, and partner conclusions must be provided by qualified Legal, Compliance, Payments, Finance, Tax, Risk, Security, Privacy, and partner stakeholders.

---

## 2. Regulatory Position Summary

The PayPlus MVP is designed around the following regulatory position:

```text
PayPlus enables payments tied to a valid accepted controlled Bill source or separate Rent source.
PayPlus requires the applicable owner-governed source and Evidence outcome for the Bill/Rent Payment Obligation: Bills follow their accepted tier and Rent retains attached Evidence accepted before Payment.
PayPlus requires payer review and authorization before payment.
PayPlus does not provide user-controlled stored balances.
PayPlus does not allow arbitrary P2P transfers.
PayPlus does not allow cashout or self-payment.
PayPlus relies on approved PSP/acquirer, processor, payout, banking, or licensed partner arrangements where required.
```

The intended regulatory distinction is that PayPlus should support controlled Bill/Rent Payment Obligations subject to their applicable source, Evidence, authorization, risk and Payout controls, rather than function as an unrestricted value-transfer, stored-value, or cash-equivalent product.

This distinction depends on the actual product design, funds flow, contractual structure, partner model, and jurisdiction-specific legal analysis.

No flow should launch unless Legal, Compliance, Payments, Risk, Finance, and relevant partners approve the applicable assessment.

### 2.1 Current Regulatory Baseline

Payer-created controlled Bill payments and the separate Rent journey are the MVP product baseline. A Consumer User is a Payer. A Payee is the economic recipient of an applicable Payment Obligation arising from an accepted controlled Bill source or separate Rent source and may be an individual or an institution/company; the Payee need not be a PayPlus User. PayPlus has no active Request, Linking, To Receive, Consumer-Payee, Receiving Info, or production legacy-Request runtime.

The accepted launch inventory contains twelve controlled Bill Categories: 會計費用; 法律費用; 醫療費用; 電訊、流動電話及寬頻費; 物業管理費; 學費; 安老院、殘疾人士院舍及受規管照顧服務; 其他專業費用; 車輛維修費; 小型工程及樓宇維修費; 註冊幼兒中心及育嬰園費用; and 寵物醫療及寄養費. Rent is separate. Category-specific eligibility, evidence criteria, Directory contents, and partner approval remain owner-governed launch gates and are not implied by that inventory.

Regulatory, PSP/acquirer, payout, AML, privacy, card network, and partner approval remain gated requirements. If any required approval is unavailable, the affected module, category, payee type, or payment path must be disabled without blocking unrelated approved modules.

The initial launch jurisdiction is Hong Kong.

The current transaction classification assumption is that PayPlus card payments will be treated as bill payment or ordinary online card purchase transactions, subject to PSP/acquirer, card network, legal, and compliance confirmation. The acquirer remains undecided. PayPlus expects to seek an appropriate or special MCC from the selected acquirer and must avoid classification as quasi-cash, cash advance, account funding, unrestricted money transfer, or cash-equivalent activity unless separately assessed and approved.

The working payout assumption is direct payout from the PayPlus operating bank account after upstream settlement. FPS, cheque, and EPS are illustrative Hong Kong rail considerations, not a selected launch configuration. Payment gateway settlement and same-day-after-settlement payout timing remain working assumptions subject to PSP/acquirer, bank, liquidity, risk, legal, partner, and reconciliation confirmation. Final operating-bank setup, rail configuration, liquidity treatment, reserves, exception handling, and reconciliation remain open.

The working KYC/KYB assumption is that individuals may complete eKYC through a selected provider and businesses may provide Business Registration documentation and owner ID, subject to applicable owner, legal, PSP/acquirer, privacy, security, and risk confirmation. No provider is selected by this document. Final provider selection, check depth, sanctions screening, exception handling, and risk-tier rules remain open.

User payment instruction is a deferred user action model, not a recurring payment mandate. A saved instruction must not be treated as card authorization, capture, settlement, payout readiness, stored value, or completed payment until the user returns to submit and confirm the relevant funding leg through the approved payment flow.

---

## 3. Product Model Assessed

The MVP is assessed as a controlled, Payer-only Bill/Rent obligation-payment platform using the accepted tier-aware Bill Evidence model and separate mandatory-Evidence Rent model. A Payer selects a supported Bill Category through Directory discovery or provides a Payee within that selected Category, or enters the separate Rent journey. Those choices create temporary capture only until the applicable owner-governed preservation outcome establishes an authoritative Bill/Rent source ID.

The source is distinct from Evidence, Payable Basis, Payment Obligation, Checkout Workspace, Payment, and payment outcome. Evidence supports verification; it is not the source or a payment. DOC-09 owns the payment-domain path from payment-relevant source facts through Payable Basis, applicable Payment Obligations, Checkout Workspace, allocations/funding legs, immutable confirmed Payments, and Payment Applications. Controlled late confirmation may temporarily leave a confirmed Payment with zero Applications; it does not create a new product flow.

Each active flow must remain Category-bound or the separate Rent journey, use attached Evidence where the applicable Bill tier or Rent rule requires it, be payer-authorized before funding, remain subject to owner-governed risk, payment, payout and privacy gates, and be recorded under the appropriate domain owners. Directory discovery does not replace Evidence, intended-Payee, destination, Payout, risk, readiness, or authorization gates.

Economic Payees may include approved billers, service providers, institutions, businesses, landlords/property recipients, or individuals where their applicable owner-governed outcomes permit payment. This assessment does not grant PayPlus User accounts, payee-created capabilities, recipient libraries, reciprocal visibility, or Request creation.

---

## 4. Key Regulatory Boundaries

PayPlus must maintain the following boundaries.

| Boundary | Requirement | Reason |
| --- | --- | --- |
| Bill-backed | Every payment must relate to an accepted controlled Bill source or separate Rent source and its applicable Payment Obligation. | Supports distinction from arbitrary money transfer. |
| Controlled source and Evidence | Each payment context must rely on an authoritative Bill/Rent source and its applicable Bill-tier or Rent Evidence outcome. | Supports dispute handling, fraud controls, and regulatory posture. |
| Payer-authorized | Payer must explicitly authorize payment before funds move. | Prevents unauthorized payments and consumer harm. |
| No wallet | PayPlus must not provide user-controlled balances. | Reduces stored-value / e-money risk. |
| No stored value | PayPlus must not allow users to preload, hold, or reuse balances. | Avoids wallet-like functionality. |
| No cashout | PayPlus must not let users convert card funding into cash or cash-equivalent value. | Reduces cash advance, AML, and partner risk. |
| No arbitrary P2P | PayPlus must not allow unsupported person-to-person transfers. | Preserves obligation-backed payment model. |
| No self-payment | Payer and payee must not be the same person or collusive related parties unless explicitly approved. | Reduces cashout and fraud risk. |
| Approved categories only | Each bill category must be approved or restricted before launch. | Prevents unsupported legal or partner use cases. |
| Approved partners only | PSP/acquirer/payout partners must support the use case. | Prevents partner rule breach and settlement failure. |

These boundaries must be reflected in product requirements, compliance controls, risk rules, disclosures, data model, payment processing, and operations.

---

## 5. Money Movement Analysis

Each PayPlus payment flow must have a documented funds-flow assessment before launch.

The assessment must answer:

- which Payer-created Bill or separate Rent source is being assessed;
- who the payer believes they are paying;
- who the payer legally pays;
- who receives funds;
- who controls funds;
- who is merchant of record, if applicable;
- who submits authorization and capture;
- who receives PSP/acquirer settlement;
- whether funds enter PayPlus-controlled accounts;
- whether PayPlus has discretion over funds;
- who initiates payout;
- who receives payout;
- whether payout occurs before settlement;
- whether PayPlus prefunds payout;
- whether reserves, holds, or collateral apply;
- when the payer’s obligation is satisfied;
- how refunds, reversals, failed payments, cancellation, and chargebacks are handled.

The funds flow must be reviewed for:

- licensing implications;
- money transmission / payment service implications;
- agent-of-payee or agent-of-payer treatment;
- PayFac, marketplace, or platform treatment;
- settlement and safeguarding requirements;
- partner acceptability;
- reconciliation and recordkeeping requirements.

The assessment must confirm that the Payer receives current material facts and separately authorizes funding; source facts, effective destination, Evidence outcomes, risk, payment, Payout, adjustment, and privacy owners determine their own gates. A Payee cannot change a payment-relevant fact after authorization without the owner-governed revalidation and fresh authorization required by DOC-09. Payout remains gated by the applicable confirmed-payment, application, destination, risk, reconciliation, adjustment and partner conditions.

---

## 6. Wallet / Stored Value Analysis

PayPlus is not intended to be a wallet, stored-value account, or e-money product.

The product must not allow users to:

- preload funds;
- maintain a reusable balance;
- store monetary value for later use;
- transfer stored value to another user;
- withdraw unused value;
- cash out card-funded value;
- send value unrelated to an accepted controlled Bill/Rent source and its applicable Payment Obligation.

Any credits, refunds, adjustments, promotional value, or failed-payment amounts must be reviewed to ensure they do not create stored value or wallet-like functionality.

If PayPlus ever introduces balances, credits, prefunding, overpayment handling, or reusable funds, Legal and Compliance must reassess whether PayPlus requires stored-value, e-money, money transmission, payment institution, or similar authorization.

---

## 7. P2P / Cashout Risk Analysis

PayPlus must not support arbitrary P2P transfers, self-payments, or cashout.

The product should prevent or restrict:

- payer and payee being the same person;
- circular payments;
- related-party abuse;
- fake invoices;
- fake rent obligations;
- inflated obligations;
- duplicate bills;
- unsupported person-to-person transfers;
- card-to-cash conversion;
- use of payment requests to generate cash-like value;
- collusive Payer/economic-Payee behaviour;
- payout to unverified or high-risk destinations.

Payer-created source facts can still create fake-obligation, self-payment, related-party, collusion, duplicate, and payout-destination risk. The applicable owners therefore determine verification, transaction monitoring, limits, duplicate detection, escalation, Payout controls, and evidence retention. Rent carries its own tenancy/source-context risk treatment; it is not a Bill Category and does not create a landlord-created Request model.

---

## 8. Payment Institution / MSB Considerations

Legal and Compliance must assess whether PayPlus requires, or can rely on, any of the following:

- money transmission license;
- payment services license or registration;
- bill payment service authorization;
- payment initiation authorization;
- stored value, wallet, or e-money authorization;
- PayFac registration;
- marketplace or platform payment model;
- sub-merchant onboarding arrangement;
- agent-of-payee arrangement;
- agent-of-payer arrangement;
- commercial agent exemption;
- regulated partner sponsorship;
- licensed partner coverage;
- cross-border payment authorization;
- FX authorization;
- consumer lending or credit analysis, if payout timing creates credit exposure;
- debt collection analysis, if overdue obligations are supported;
- category-specific legal review for the accepted Bill inventory, separate Rent, or other later approved scope.

The assessment must be performed by jurisdiction, controlled Bill Category or separate Rent, economic-Payee type, payment method, Payout model, and funds flow.

No MVP flow should launch without a documented conclusion or documented unresolved risk acceptance.

---

## 9. PSP, Acquirer, and Partner Assessment

PayPlus must confirm that PSPs, acquirers, processors, gateways, payout providers, and other material payment partners support the proposed flow.

Before launch, PayPlus should obtain written confirmation for:

- supported product use case;
- supported jurisdictions;
- supported funds flow;
- Payer-created controlled Bill and separate Rent payment support;
- merchant of record, PayFac, marketplace, platform, agent, or sub-merchant implications;
- approved bill categories;
- approved payee types;
- prohibited and restricted categories;
- payee onboarding requirements;
- KYC/KYB, beneficial ownership, sanctions, underwriting, and monitoring obligations;
- MCC or transaction classification;
- whether transactions may be treated as cash-like, quasi-cash, account funding, money transfer, or cash equivalent;
- fee restrictions;
- multi-card and split payment support;
- authorization and capture timing;
- payer authorization evidence requirements;
- refund and reversal support;
- chargeback process, liability, and evidence requirements;
- payout method and settlement timing;
- reserves, holdbacks, prefunding, collateral, or payee-specific holds;
- reporting and reconciliation data;
- payee-level reporting;
- data protection and security commitments;
- Payer and economic-Payee data visibility constraints;
- operational support and escalation;
- contractual change notice obligations.

If written confirmation cannot be obtained, the assumption must be logged as an open risk and approved before launch.

---

## 10. Required Controls

The following controls are required or must be explicitly risk-accepted before launch.

| Control Area | Required Control |
| --- | --- |
| Regulatory role | Document PayPlus role for each Payer-created flow, jurisdiction, controlled Category or separate Rent, and economic-Payee type. |
| Licensing path | Document required licenses, exemptions, partner sponsorships, agency models, or unresolved risk. |
| Funds flow | Maintain approved funds-flow diagram and description. |
| PSP/acquirer approval | Confirm partner support for use case, Category or separate Rent, MCC/classification, and Payout model. |
| Category restrictions | Maintain approved, restricted, prohibited, and enhanced-review categories. |
| Economic-Payee verification | Verify the intended Payee and effective destination before Payout where required by the applicable owners. |
| Payer authorization | Require explicit payer authorization before funding or payout. |
| Evidence | Require each payment context to reference an authoritative Bill/Rent source and applicable supporting Evidence outcomes. |
| Anti-cashout | Prevent self-payment, fake obligation, circular payment, related-party abuse, and unsupported P2P. |
| Transaction monitoring | Monitor fraud, velocity, duplicate source indicators, complaints, chargebacks, and Payout anomalies. |
| Disclosure | Disclose PayPlus role, relevant Payee identity, fees, timing, authorization, refunds, disputes, and failed-payment behavior as owned by DOC-07. |
| Privacy | Define Payer/economic-Payee data visibility and approved-purpose access boundaries. |
| Security / PCI | Review PCI scope, tokenization, authentication, encryption, RBAC, audit logs, and partner security. |
| Recordkeeping | Retain source, Evidence, authorization, disclosure, communication, Payout, adjustment, and reconciliation records under their formal owners. |
| Settlement / liquidity | Review settlement timing, reserves, holdbacks, prefunding, payout timing, and liquidity impact. |
| Contractual support | Ensure partner contracts support required flow, reporting, chargebacks, payouts, data protection, and change notice. |

Detailed control implementation belongs in:

- `DOC-04 Compliance Certification Roadmap & Control Framework`;
- `DOC-09 Payment Domain Architecture`;
- `DOC-10 Payout & Reconciliation`;
- `DOC-11 Refund, Cancellation & Chargeback`;
- `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`;
- `DOC-15 Privacy, Data Protection & Record Retention`;
- `DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification`;
- `DOC-19 Security, Tokenization & Authentication`.

---

## 11. Compliance Readiness Gates

PayPlus should not launch a jurisdiction, controlled Category or separate Rent path, payment method, partner, economic-Payee type, or funds flow until applicable gates are satisfied.

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC03-001` | Regulatory role assessed | Legal/Compliance documents PayPlus role for the Payer-created flow, economic-Payee type, and jurisdiction. |
| `GATE-DOC03-002` | Licensing path confirmed | Required licenses, exemptions, sponsorships, agency arrangements, PayFac arrangements, or partner coverage are documented. |
| `GATE-DOC03-003` | Funds flow approved | Funds flow diagram and description are approved by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-004` | PSP/acquirer acceptability confirmed | Partner confirms use case, controlled Category or separate Rent, economic-Payee type, MCC/classification, and flow support. |
| `GATE-DOC03-005` | Payout model approved | Payout method, provider, timing, failures, reversals, destination controls, and reconciliation are assessed. |
| `GATE-DOC03-006` | Category restrictions defined | Approved, restricted, prohibited, and enhanced-review categories are documented. |
| `GATE-DOC03-007` | Fee model reviewed | Payer, payee, service, convenience, surcharge, platform, or payout fee model is reviewed. |
| `GATE-DOC03-008` | AML/risk assessment completed | AML, sanctions, fraud, anti-cashout, collusion, fake obligation, and abuse risks are assessed. |
| `GATE-DOC03-009` | Security/privacy review completed | PCI, privacy, security, Payer/economic-Payee visibility, and data protection reviews are completed. |
| `GATE-DOC03-010` | Partner due diligence completed | Vendor, regulatory, commercial, security, payee onboarding, and contract reviews are completed. |
| `GATE-DOC03-011` | Contract approved | Legal approves partner contract and required provisions. |
| `GATE-DOC03-012` | Settlement/reserve impact approved | Finance approves settlement timing, reserves, holdbacks, payout timing, and liquidity impact. |
| `GATE-DOC03-013` | Disclosure requirements identified | Required user, payer, and payee disclosures are identified for implementation. |
| `GATE-DOC03-014` | Reporting and recordkeeping defined | Required source, payment, economic-Payee, compliance, dispute, and reconciliation records are identified. |
| `GATE-DOC03-015` | Intended-Payee and destination assessment approved | Verification, destination, monitoring, and Payout conditions are assessed where applicable. |
| `GATE-DOC03-016` | Source model assessed | The Payer-created Category-bound Bill and separate Rent model is assessed without a Request, Payee-user, or linking capability. |
| `GATE-DOC03-017` | Rent source model assessed, if applicable | Tenancy/source evidence, economic-Payee verification, rent risk, partner approval, and enhanced controls are assessed. |
| `GATE-DOC03-018` | Launch approval obtained | Required approvers sign off before launch. |

---

## 12. Legal Review Items

Legal and Compliance must review and document conclusions for the following items before launch or risk acceptance.

| Review Item | Required Question | Priority |
| --- | --- | --- |
| Launch jurisdiction | What Hong Kong-specific regulatory and partner requirements apply before launch? | Critical |
| Regulatory role | What role does PayPlus take in each MVP funds flow? | Critical |
| Licensing | Does the MVP require money transmission, payment service, bill payment, e-money, or similar licensing? | Critical |
| Partner reliance | Can PayPlus rely on a regulated partner, exemption, sponsorship, or agent model? | Critical |
| PSP/acquirer support | Which PSP/acquirer supports the Hong Kong bill payment use case? | Critical |
| Transaction classification | What MCC or transaction classification applies, and can it support bill payment or ordinary online card purchase treatment? | Critical |
| Cash-like treatment | Could transactions be treated as quasi-cash, cash advance, account funding, money transfer, or cash equivalent? | Critical |
| Fee model | Are payer-paid, payee-paid, service, convenience, surcharge, platform, or payout fees permitted? | Critical |
| Approved categories | Which bill categories are approved, restricted, prohibited, or enhanced-review for MVP? | Critical |
| Intended-Payee verification | What verification is required for the intended economic Payee and effective destination before Payout where applicable? | Critical |
| Payer-created source model | What legal, partner, Category and control gates apply to the Payer-created controlled Bill and separate Rent model? | Critical |
| Payee role | Are payees merchants, sub-merchants, billers, beneficiaries, agents, customers, platform participants, or another role? | Critical |
| PayFac / marketplace | Does the accepted Payer-created payment model create PayFac, marketplace, platform or sub-merchant implications? | Critical |
| Payer authorization | How must payer authorization be captured and retained? | Critical |
| Separate Rent | What tenancy/source, recipient, risk and partner controls apply to the separate Rent journey? | Critical |
| Debt collection | Could overdue invoices, rent, fees, or payment reminders create debt collection implications? | High |
| Privacy boundaries | What payee information may be shown to payer, and what payer information may be shown to payee? | High |
| Repeated payment | What owner-governed revalidation and fresh Payer authorization are required for a later payment? | High |
| Multi-card | What PSP/acquirer, legal, risk, and reconciliation controls apply to MVP multi-card payments with configurable card-count limits? | High |
| Settlement/reserves | What settlement timing, reserves, holdbacks, collateral, or prefunding apply? | High |
| Disclosures | What disclosures are required at source capture, Checkout, receipt and owner-governed notification surfaces? | High |
| Partner contracts | What contractual provisions are mandatory for PSP/acquirer/payout agreements? | High |

---

## 13. Key Risks

| Risk ID | Risk | Initial Mitigation | Owner |
| --- | --- | --- | --- |
| `RISK-DOC03-001` | PayPlus launches with incorrect regulatory role classification. | Obtain legal assessment per jurisdiction and flow. | Legal / Compliance |
| `RISK-DOC03-002` | Flow is treated as money transmission or regulated payment service requiring licensing. | Evaluate licenses, exemptions, partner sponsorship, or licensed provider model. | Legal / Compliance |
| `RISK-DOC03-003` | PSP/acquirer rejects PayPlus use case or category. | Obtain written partner confirmation early. | Payments / Commercial |
| `RISK-DOC03-004` | Transaction is classified as quasi-cash, cash advance, account funding, or money transfer. | Confirm MCC/classification and add disclosures if required. | Payments / Legal |
| `RISK-DOC03-005` | Fee model violates law, network rules, or partner restrictions. | Complete legal, card network, and partner fee review before launch. | Legal / Payments |
| `RISK-DOC03-006` | An accepted Payer-created payment model is characterized as PayFac, marketplace, agent, or regulated payment service without assessment. | Complete role assessment and partner confirmation. | Legal / Compliance / Payments |
| `RISK-DOC03-007` | A source is used for fake invoices, fake Rent, self-payment, or collusive cashout. | Apply applicable Evidence, risk, destination, monitoring and Payout controls. | Risk / Compliance |
| `RISK-DOC03-008` | Separate Rent creates tenancy, rent collection, debt collection, or heightened consumer-protection issues. | Conduct rent-specific legal and risk assessment. | Legal / Compliance / Product |
| `RISK-DOC03-009` | Payer believes source establishment, Evidence, or an instruction is mandatory, validated, or already paid. | Use owner-approved disclosure and explicit Payer authorization. | Product / Legal |
| `RISK-DOC03-010` | Inadequate payee verification enables fraud or cashout. | Implement payee verification and anti-cashout controls. | Risk / Compliance |
| `RISK-DOC03-011` | Partner reserves or holdbacks create liquidity strain. | Model reserve impact and obtain Finance approval. | Finance / Payments |
| `RISK-DOC03-012` | Partner contract lacks reporting, chargeback, payout, or change-notice support. | Use contractual checklist and Legal review. | Legal / Payments |
| `RISK-DOC03-013` | Privacy, PCI, or security obligations are underestimated. | Complete privacy, security, and PCI review. | Security / Privacy |
| `RISK-DOC03-014` | Required disclosures are incomplete or unclear. | Legal review of source, Checkout, receipt, notification and terms content. | Product / Legal |
| `RISK-DOC03-015` | Payee sees payer-sensitive payment, card, risk, or private profile information. | Enforce data visibility boundaries and RBAC. | Privacy / Security |
| `RISK-DOC03-016` | Regulatory, network, or partner rule changes affect approved flows. | Maintain periodic review and partner change-notice monitoring. | Compliance / Payments |

---

## 14. Assessment Template

Each assessed Payer-created flow, partner, controlled Category or separate Rent path, economic-Payee type, or jurisdiction should use the following template.

```text
Assessment Name:
Assessment Type:
Jurisdiction:
Bill Category:
Payee Type:
Payment Method:
Payout Method:
Partner(s):
Date:
Owner:
Reviewers:

1. Summary Recommendation
- Approved / Approved with conditions / Not approved / Deferred

2. Product and Funds Flow Description
- Payer journey:
- Economic-Payee context, where applicable:
- Funding flow:
- Payout flow:
- Refund flow:
- Chargeback flow:
- Safe support/adjustment handling, if applicable:

3. Regulatory Role Assessment
- PayPlus role:
- Partner role:
- Payee role:
- Payer role:
- Merchant / PayFac / marketplace / agent implications:
- Open legal questions:

4. Licensing / Exemption Analysis
- Required license or registration:
- Exemption or sponsorship:
- Agent or partner coverage:
- Conditions:
- Gaps:

5. Partner Acceptability
- PSP/acquirer confirmation:
- Payout provider confirmation:
- Intended-Payee/destination assessment:
- MCC/classification:
- Restricted categories:
- Conditions:

6. Fee and Disclosure Review
- Payer fee:
- Payee fee:
- Partner fee:
- Platform fee:
- Tax:
- Required payer disclosures:
- Required payee disclosures:
- Restrictions:

7. Risk and Compliance Review
- AML risk:
- Sanctions risk:
- Fraud risk:
- Cashout risk:
- Collusion risk:
- Fake obligation risk:
- Chargeback risk:
- Controls required:

8. Data, Privacy, and Security Review
- PCI impact:
- Personal data:
- Sensitive data:
- Payer/economic-Payee visibility:
- Data transfers:
- Security requirements:
- Partner obligations:

9. Commercial and Settlement Review
- Processing cost:
- Payout cost:
- Payee onboarding cost:
- Reserve:
- Holdback:
- Settlement timing:
- Payee payout timing:
- Liquidity impact:

10. Operational Review
- Payee onboarding operations:
- Manual review required:
- Support impact:
- Payer query/dispute handling:
- Payout exceptions:
- Reconciliation needs:
- Monitoring requirements:

11. Required Conditions Before Launch
- Condition 1:
- Condition 2:
- Condition 3:

12. Risks and Open Issues
- Risk 1:
- Risk 2:
- Risk 3:

13. Approval
- Legal:
- Compliance:
- Payments:
- Finance:
- Risk:
- Product:
- Security/Privacy, where applicable:
```

---

## 15. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC03-001` | What Hong Kong-specific regulatory, payment, privacy, tax, audit, and operational requirements apply before launch? | Project Owner / Legal | Critical | Open |
| `OQ-DOC03-002` | What legal role will PayPlus take in the MVP funds flow? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-003` | Does the MVP funds flow require money transmission, payment service, bill payment, e-money, or similar licensing? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-004` | Can PayPlus rely on a regulated partner, exemption, sponsorship, or agent model? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-005` | Which PSP/acquirer will support the PayPlus Hong Kong bill payment use case? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-006` | What appropriate or special MCC will the selected acquirer assign? | Payments | Critical | Open |
| `OQ-DOC03-007` | Can transactions be confirmed as bill payment or ordinary online card purchase rather than quasi-cash, cash advance, account funding, money transfer, or cash equivalent? | Payments / Legal | Critical | Open |
| `OQ-DOC03-008` | Are payer-paid, payee-paid, service, convenience, platform, surcharge, or payout fees permitted? | Legal / Payments | Critical | Open |
| `OQ-DOC03-008A` | What legal, PSP/acquirer, Payout and partner gates apply to Payer-created controlled Bills and separate Rent? | Legal / Payments / Compliance | Critical | Open |
| `OQ-DOC03-009` | Which bill categories are approved, restricted, prohibited, or enhanced-review for MVP? | Compliance / Risk / Product | Critical | Open |
| `OQ-DOC03-010` | What final KYC/KYB provider, check depth, sanctions screening, exception handling and risk-tier rules apply before applicable Payout? | Risk / Compliance | Critical | Open |
| `OQ-DOC03-011` | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Commercial | High | Open |
| `OQ-DOC03-012` | What reserves, holdbacks, collateral, prefunding, liquidity, settlement timing, payout timing, and exception rules apply, subject to Finance / Payments confirmation? | Finance / Payments | High | Open |
| `OQ-DOC03-013` | What PSP/acquirer, legal, risk, and reconciliation controls apply to MVP multi-card payments with configurable card-count limits? | Product / Payments / Legal | High | Open |
| `OQ-DOC03-014` | What AML, sanctions, fraud, anti-cashout, collusion and source-abuse controls are required before MVP? | Compliance / Risk | Critical | Open |
| `OQ-DOC03-015` | What PCI, privacy, security, and data protection requirements apply? | Security / Privacy | High | Open |
| `OQ-DOC03-016` | What partner reporting files or APIs are required for reconciliation and compliance records? | Finance / Engineering | High | Open |
| `OQ-DOC03-017` | What disclosures are required at source capture, Checkout, receipt and notification surfaces? | Legal / Product | High | Open |
| `OQ-DOC03-018` | What contract provisions are mandatory for PSP/acquirer/payout provider agreements? | Legal / Payments | High | Open |
| `OQ-DOC03-019` | What remaining legal, partner, Category and control gates apply to the accepted Payer-created source model? | Project Owner / Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-020` | What legal role does an economic Payee have in the accepted Payer-created flow? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-021` | Are intended Payees merchants, sub-merchants, billers, beneficiaries, agents, or another legally assessed role? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-022` | Does the accepted Payer-created flow require PayFac, marketplace, platform or sub-merchant treatment? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-023` | Do PSP/acquirer and Payout partners approve the accepted controlled Bill and separate Rent flows? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-024` | What controls and restrictions apply to the separate Rent journey? | Product / Legal / Risk / Payments | Critical | Open |
| `OQ-DOC03-025` | What intended-Payee, property, destination, sanctions and tenancy evidence checks apply to Rent where required? | Legal / Compliance / Risk | Critical | Open |
| `OQ-DOC03-026` | Could the separate Rent journey create landlord/tenant, rent collection or debt-collection implications? | Legal / Compliance | High | Open |
| `OQ-DOC03-027` | What Evidence and KYB/KYC requirements apply to controlled Category paths where required? | Compliance / Risk / Legal | High | Open |
| `OQ-DOC03-028` | How must Payer authorization be captured for an applicable payment? | Legal / Payments / Product | Critical | Open |
| `OQ-DOC03-029` | What source-context information may be shown to the Payer, and what Payer information may be disclosed under approved-purpose rules? | Privacy / Security / Legal | High | Open |
| `OQ-DOC03-030` | What owner-governed support, adjustment or dispute handling applies before or after authorization? | Product / Legal / Operations | High | Open |
| `OQ-DOC03-031` | What revalidation and separate Payer authorization is required for a later payment? | Legal / Payments / Product | High | Open |
| `OQ-DOC03-032` | What monitoring is required for fake invoices, fake Rent, related-party abuse, complaints and chargebacks? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC03-033` | Are applicable Payout, platform or other fees permitted? | Legal / Finance / Commercial | High | Open |
| `OQ-DOC03-034` | What partner contract terms are required for intended-Payee verification, monitoring and Payout? | Legal / Payments / Commercial | High | Open |

---

## 16. Downstream Document Impact

`DOC-03` informs downstream documents as follows:

| Document | Impact |
| --- | --- |
| `DOC-04` | Compliance gates, controls, Evidence, intended-Payee/destination assessment, and controlled Bill/separate Rent launch controls. |
| `DOC-05` | Product requirements for payment methods, accepted Categories, separate Rent, partner constraints, disclosures, economic-Payee context, and flow limits. |
| `DOC-06` | Payer journeys, economic-Payee source context, Bills/Rent presentation, and compatible partner handoffs. |
| `DOC-07` | Owner-approved role, fee, timing, refund, risk, authorization and issuer-fee disclosure architecture. |
| `DOC-08` | Payer-facing receipts and owner-governed notification for payment, authorization, status and failure outcomes. |
| `DOC-09` | Payment Domain aggregates, payable-capacity controls, checkout and funding execution, payer authorization boundaries, confirmed Payment creation, and multi-card limits. Provider mechanics remain with `DOC-17`; Settlement and Payout remain with `DOC-10`. |
| `DOC-10` | Payout, reconciliation, payout eligibility, reserves, settlement timing, and reporting. |
| `DOC-11` | Refund, cancellation, chargeback, dispute, adjustment/case and loss-allocation boundaries. |
| `DOC-12` | Accepted Category inventory consumption, OCR, Evidence, intended-Payee verification and separate Rent evidence. |
| `DOC-14` | AML, sanctions, fraud, cashout, collusion, fake-source and economic-Payee risk controls. |
| `DOC-15` | Privacy, retention, data classification, role-based visibility, masking, approved-purpose access, and sensitive document handling. |
| `DOC-18` | Future representation of approved regulatory records, source/Payee facts, Payer authorization, disputes, reconciliation and audit/lineage requirements. |
| `DOC-19` | Future authentication, tokenization, PCI, RBAC, Payer/economic-Payee data boundaries, access, encryption and audit controls. |
| `DOC-20` | Launch checklist including DOC-03 gates and approvals. |
| `DOC-21` | Monitoring for partner restrictions, verification issues, source abuse, settlement issues, chargebacks, Category violations, Payout failures and compliance incidents. |
| `DOC-22` | Owner-permitted configuration and execution workflows; it does not own policy, truth, queues or override criteria. |

---

## 17. Acceptance Criteria

`DOC-03` is acceptable when it clearly defines:

- PayPlus’s intended regulatory posture;
- the Payer-only controlled Bill and separate Rent MVP model;
- how the product uses tier-aware Bill Evidence and the separate mandatory-Evidence Rent journey for applicable Payment Obligations arising from accepted controlled sources;
- why payer authorization is mandatory;
- why PayPlus is not intended to be a wallet or stored-value product;
- why arbitrary P2P and cashout are prohibited;
- money movement assessment requirements;
- licensing, MSB, payment institution, PayFac, marketplace, agency, and partner reliance questions;
- PSP/acquirer and payout partner confirmation requirements;
- required controls;
- compliance readiness gates;
- legal review items;
- key risks;
- open questions;
- downstream document impact.

This document must remain an assessment framework and must not become:

- final legal advice;
- final licensing decision;
- final compliance policy;
- partner contract;
- pricing sheet;
- PRD;
- technical integration specification;
- risk rulebook;
- operations SOP.

---

## 18. Revision History
| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. | Stage 11 alignment evidence |
| `0.11.1` | 2026-08-12 | Product Documentation Team | Consolidated provider/rail/timing qualification and active source, Evidence, Payment Obligation and inventory-boundary corrections without selecting a provider or rail. |
| `0.11.0` | 2026-08-12 | Product Documentation Team | Reframed the active regulatory assessment around Payer-created controlled Bill sources and separate Rent; retired Request/Linking runtime assumptions; and preserved owner-governed payment, Evidence, Payout, risk and privacy boundaries. |
| `0.10.3` | 2026-07-31 | Product Documentation Team | Aligned DOC-09 title, Request-as-linkage terminology, Payment Domain aggregates, provider-integration boundaries, and separate Settlement/Payout ownership. |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-03 Regulatory, PSP & Acquirer Assessment. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation assessment framework, added triggers, role and licensing assessment, funds flow review, partner due diligence, scorecard, category restrictions, required confirmations, contractual assessment, compliance gates, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
| `0.3.0` | 2026-05-27 | Product Documentation Team | Updated assessment framework for payee onboarding and payee-created bill, invoice, fee, and rent payment request capability introduced in DOC-05 v0.2.0. |
| `0.4.0` | 2026-05-27 | Product Documentation Team | Simplified structure and language while preserving essential regulatory, PSP/acquirer, funds flow, partner, category, payee-created request, rent request, disclosure, privacy, security, contractual, settlement, readiness gate, risk, and open-question content. |
| `0.5.0` | 2026-05-27 | Product Documentation Team | Reorganized into simplified regulatory assessment format focused on regulatory posture, two-sided MVP model, key boundaries, money movement, wallet/stored value, P2P/cashout risk, MSB/payment institution considerations, required controls, legal review items, risks, and open questions. |
| `0.6.0` | 2026-05-29 | Product Documentation Team | Confirmed payee-created requests and tenancy/rent as MVP product scope while preserving regulatory, partner, payout, and category gating before production enablement. |
| `0.7.0` | 2026-05-30 | Product Documentation Team | Aligned regulatory framing with updated DOC-01 scope for invoices, fees, rent, medical bills, domestic service obligations, and payer-authorized push payment positioning. |
| `0.8.0` | 2026-06-01 | Product Documentation Team | Updated DOC-13 related-document title for promotion engine, coupon, voucher, referral, membership, and reward alignment. |
| `0.9.0` | 2026-06-02 | Product Documentation Team | Aligned regulatory privacy references with DOC-15 data classification, role-based visibility, masking, and approved-purpose access wording. |
| `0.10.0` | 2026-06-02 | Product Documentation Team | Aligned regulatory baseline with confirmed evidence-backed MVP categories, clarified user payment instruction is not recurring payment or stored value, softened rent enablement wording to category-gated launch controls, and added DOC-22 downstream reference. |
| `0.10.1` | 2026-07-26 | Product Documentation Team | Distinguished payer-created payment from optional linking and separated payee-created request acceptance from payment authorization. |
| `0.10.2` | 2026-07-27 | Product Documentation Team | Clarified partner assessment for direct payer-created payments, optional payer-to-payee linking requests, and payee-created payment requests as separate supported-flow questions. |
