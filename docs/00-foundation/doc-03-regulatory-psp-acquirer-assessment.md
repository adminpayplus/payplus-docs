---
document_id: DOC-03
title: Regulatory Assessment
version: 0.10.0
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
last_updated: 2026-06-02
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
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-16 Technical Architecture
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT, Release & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operations Runbook
---

# DOC-03 — Regulatory Assessment

## 1. Purpose

This document defines the regulatory assessment framework for PayPlus.

It explains the intended regulatory posture of the PayPlus MVP and identifies the key legal, compliance, PSP/acquirer, payment partner, and risk questions that must be resolved before launch.

PayPlus is intended to operate as an **evidence-backed, payer-authorized bill, invoice, fee, rent, and approved obligation payment request platform**.

PayPlus is **not intended** to operate as:

- a wallet;
- a stored-value account;
- an e-money product;
- a cashout product;
- an arbitrary peer-to-peer transfer service;
- a general money transmission product independent of an underlying bill, invoice, fee, rent, or approved obligation.

This document is not a final legal opinion. Final legal, regulatory, licensing, card network, PSP/acquirer, tax, accounting, and partner conclusions must be provided by qualified Legal, Compliance, Payments, Finance, Tax, Risk, Security, Privacy, and partner stakeholders.

---

## 2. Regulatory Position Summary

The PayPlus MVP is designed around the following regulatory position:

```text
PayPlus enables payments tied to a valid bill, invoice, fee, rent, or other approved obligation.
PayPlus requires supporting evidence for the obligation.
PayPlus requires payer review and authorization before payment.
PayPlus does not provide user-controlled stored balances.
PayPlus does not allow arbitrary P2P transfers.
PayPlus does not allow cashout or self-payment.
PayPlus relies on approved PSP/acquirer, processor, payout, banking, or licensed partner arrangements where required.
```

The intended regulatory distinction is that PayPlus should support payment of verified or evidence-backed obligations, rather than function as an unrestricted value-transfer, stored-value, or cash-equivalent product.

This distinction depends on the actual product design, funds flow, contractual structure, partner model, and jurisdiction-specific legal analysis.

No flow should launch unless Legal, Compliance, Payments, Risk, Finance, and relevant partners approve the applicable assessment.

### 2.1 Current Regulatory Baseline

Payee-created payment requests, bill payments, fee payments, tenancy/rent payments, domestic helper payments, driver payments, personal service payments, multi-card payments, and user payment instructions are included in the MVP product baseline where supported by acceptable evidence and enabled controls.

Regulatory, PSP/acquirer, payout, AML, privacy, card network, and partner approval remain gated requirements. If any required approval is unavailable, the affected module, category, payee type, or payment path must be disabled without blocking unrelated approved modules.

The initial launch jurisdiction is Hong Kong.

The current transaction classification assumption is that PayPlus card payments will be treated as bill payment or ordinary online card purchase transactions, subject to PSP/acquirer, card network, legal, and compliance confirmation. The acquirer remains undecided. PayPlus expects to seek an appropriate or special MCC from the selected acquirer and must avoid classification as quasi-cash, cash advance, account funding, unrestricted money transfer, or cash-equivalent activity unless separately assessed and approved.

The current payout baseline is direct payout from the PayPlus operating bank account after upstream settlement. Hong Kong payout rails include FPS, cheque, and EPS. Payment gateway settlement is expected to be T+1 to T+3, with payout expected on the same day after funds are settled by the upstream counterparty. Final operating-bank setup, rail configuration, liquidity treatment, reserves, exception handling, and reconciliation remain to be confirmed.

The current KYC/KYB baseline is highly confirmed. Individuals are expected to complete eKYC through a service provider such as Jumio, provide email, verify phone number by SMS, and submit ID copy through the eKYC provider. Businesses are expected to provide Business Registration documentation and owner ID. Final provider selection, check depth, sanctions screening, exception handling, and risk-tier rules remain to be confirmed.

User payment instruction is a deferred user action model, not a recurring payment mandate. A saved instruction must not be treated as card authorization, capture, settlement, payout readiness, stored value, or completed payment until the user returns to submit and confirm the relevant funding leg through the approved payment flow.

---

## 3. Product Model Assessed

The MVP is assessed as a two-sided payment request platform.

PayPlus supports both:

| Flow | Description |
| --- | --- |
| Payer-created payment | A payer creates a payment request to pay a bill, invoice, rent obligation, fee, or other approved obligation. |
| Payee-created request | An approved payee creates a request for payment and sends it to a payer for review and authorization. |

Both flows must remain:

- evidence-backed;
- linked to an approved bill category or obligation type;
- subject to payer authorization before payment;
- subject to risk and compliance controls;
- processed through approved PSP/acquirer and payout arrangements;
- recorded for audit, reconciliation, dispute, and compliance purposes.

For payee-created requests:

```text
A payee-created request does not itself move money.
The payer must review, accept, and authorize the payment before any funding or payout occurs.
```

Approved payees may include, subject to legal and partner approval:

- landlords;
- schools;
- utilities;
- billers;
- service providers;
- businesses;
- other approved payees.

Payee eligibility, onboarding, verification, capability permissions, payout eligibility, and monitoring must be defined before launch.

---

## 4. Key Regulatory Boundaries

PayPlus must maintain the following boundaries.

| Boundary | Requirement | Reason |
| --- | --- | --- |
| Bill-backed | Every payment must relate to an approved bill, invoice, rent, fee, or obligation. | Supports distinction from arbitrary money transfer. |
| Evidence-backed | Each request must include or link to supporting evidence. | Supports dispute handling, fraud controls, and regulatory posture. |
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

- who creates the request;
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
- how refunds, reversals, failed payments, rejected requests, cancelled requests, and chargebacks are handled.

The funds flow must be reviewed for:

- licensing implications;
- money transmission / payment service implications;
- agent-of-payee or agent-of-payer treatment;
- PayFac, marketplace, or platform treatment;
- settlement and safeguarding requirements;
- partner acceptability;
- reconciliation and recordkeeping requirements.

For payee-created requests, the assessment must also confirm:

- the payee can create requests only if eligible and approved;
- the payer must accept and authorize before funding;
- the payee cannot change amount, destination, evidence, or payment terms after payer authorization unless the payer re-authorizes;
- payout is gated by payment status, payee status, risk status, and partner rules;
- payer rejection, query, or dispute can occur before funds movement;
- request, payment, payout, refund, and chargeback statuses remain traceable.

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
- send value unrelated to an approved bill or obligation.

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
- collusive payer/payee behavior;
- payout to unverified or high-risk destinations.

Payee-created requests create additional cashout and collusion risk because the payee initiates the request.

Therefore, payee-created requests require:

- payee onboarding;
- payee verification;
- request evidence;
- payer authorization;
- relationship or obligation checks where required;
- request monitoring;
- transaction limits;
- duplicate detection;
- suspicious activity escalation;
- payout controls;
- chargeback evidence retention.

Landlord-created rent requests require enhanced review because rent can be misused for fake obligation, self-payment, related-party, or collusive cashout schemes.

Landlord-created rent requests are MVP scope where required evidence, verification, risk, payment, payout, privacy, and operational controls are enabled. Category controls, limits, review routing, and partner confirmations remain launch gates.

---

## 8. Payment Institution / MSB Considerations

Legal and Compliance must assess whether PayPlus requires, or can rely on, any of the following:

- money transmission license;
- payment services license or registration;
- bill payment service authorization;
- payment initiation or request-to-pay authorization;
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
- category-specific legal review for rent, education, utility, medical, domestic service, loan, mortgage, or other regulated categories.

The assessment must be performed by jurisdiction, bill category, payee type, request creator model, payment method, payout model, and funds flow.

No MVP flow should launch without a documented conclusion or documented unresolved risk acceptance.

---

## 9. PSP, Acquirer, and Partner Assessment

PayPlus must confirm that PSPs, acquirers, processors, gateways, payout providers, and other material payment partners support the proposed flow.

Before launch, PayPlus should obtain written confirmation for:

- supported product use case;
- supported jurisdictions;
- supported funds flow;
- payer-created and payee-created request support;
- merchant of record, PayFac, marketplace, platform, agent, or sub-merchant implications;
- approved bill categories;
- approved payee types;
- approved request creator types;
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
- payer/payee data visibility constraints;
- operational support and escalation;
- contractual change notice obligations.

If written confirmation cannot be obtained, the assumption must be logged as an open risk and approved before launch.

---

## 10. Required Controls

The following controls are required or must be explicitly risk-accepted before launch.

| Control Area | Required Control |
| --- | --- |
| Regulatory role | Document PayPlus role for each flow, jurisdiction, category, payee type, and request creator type. |
| Licensing path | Document required licenses, exemptions, partner sponsorships, agency models, or unresolved risk. |
| Funds flow | Maintain approved funds-flow diagram and description. |
| PSP/acquirer approval | Confirm partner support for use case, category, MCC/classification, request model, and payout model. |
| Category restrictions | Maintain approved, restricted, prohibited, and enhanced-review categories. |
| Payee onboarding | Verify payees before request creation or payout, as required by risk and partner rules. |
| Payer authorization | Require explicit payer authorization before funding or payout. |
| Evidence | Link each payment request to supporting evidence of the bill or obligation. |
| Anti-cashout | Prevent self-payment, fake obligation, circular payment, related-party abuse, and unsupported P2P. |
| Transaction monitoring | Monitor fraud, velocity, duplicate requests, complaints, chargebacks, and payout anomalies. |
| Disclosure | Disclose PayPlus role, request origin, payee identity, fees, timing, authorization, refunds, disputes, and failed-payment behavior. |
| Privacy | Define payer/payee data visibility and access boundaries. |
| Security / PCI | Review PCI scope, tokenization, authentication, encryption, RBAC, audit logs, and partner security. |
| Recordkeeping | Retain request, evidence, authorization, disclosure, communication, payout, refund, chargeback, and reconciliation records. |
| Settlement / liquidity | Review settlement timing, reserves, holdbacks, prefunding, payout timing, and liquidity impact. |
| Contractual support | Ensure partner contracts support required flow, reporting, chargebacks, payouts, data protection, and change notice. |

Detailed control implementation belongs in:

- `DOC-04 Compliance Certification Roadmap & Control Framework`;
- `DOC-09 Payment Request, Multi-Funding Source & Settlement`;
- `DOC-10 Payout & Reconciliation`;
- `DOC-11 Refund, Cancellation & Chargeback`;
- `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`;
- `DOC-15 Privacy, Data Protection & Record Retention`;
- `DOC-18 Data Model, Transaction Ledger & Reporting`;
- `DOC-19 Security, Tokenization & Authentication`.

---

## 11. Compliance Readiness Gates

PayPlus should not launch a jurisdiction, category, payment method, partner, payee type, request creator model, or funds flow until applicable gates are satisfied.

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC03-001` | Regulatory role assessed | Legal/Compliance documents PayPlus role for the flow, request creator type, payee type, and jurisdiction. |
| `GATE-DOC03-002` | Licensing path confirmed | Required licenses, exemptions, sponsorships, agency arrangements, PayFac arrangements, or partner coverage are documented. |
| `GATE-DOC03-003` | Funds flow approved | Funds flow diagram and description are approved by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-004` | PSP/acquirer acceptability confirmed | Partner confirms use case, category, payee type, request model, MCC/classification, and flow support. |
| `GATE-DOC03-005` | Payout model approved | Payout method, provider, timing, failures, reversals, destination controls, and reconciliation are assessed. |
| `GATE-DOC03-006` | Category restrictions defined | Approved, restricted, prohibited, and enhanced-review categories are documented. |
| `GATE-DOC03-007` | Fee model reviewed | Payer, payee, service, convenience, surcharge, platform, or payout fee model is reviewed. |
| `GATE-DOC03-008` | AML/risk assessment completed | AML, sanctions, fraud, anti-cashout, collusion, fake obligation, and abuse risks are assessed. |
| `GATE-DOC03-009` | Security/privacy review completed | PCI, privacy, security, payer/payee visibility, and data protection reviews are completed. |
| `GATE-DOC03-010` | Partner due diligence completed | Vendor, regulatory, commercial, security, payee onboarding, and contract reviews are completed. |
| `GATE-DOC03-011` | Contract approved | Legal approves partner contract and required provisions. |
| `GATE-DOC03-012` | Settlement/reserve impact approved | Finance approves settlement timing, reserves, holdbacks, payout timing, and liquidity impact. |
| `GATE-DOC03-013` | Disclosure requirements identified | Required user, payer, and payee disclosures are identified for implementation. |
| `GATE-DOC03-014` | Reporting and recordkeeping defined | Required transaction, request, payee, compliance, dispute, and reconciliation records are identified. |
| `GATE-DOC03-015` | Payee onboarding model approved | Payee onboarding, verification, permissions, monitoring, and offboarding requirements are assessed. |
| `GATE-DOC03-016` | Payee-created request model approved | Role, evidence, payer authorization, partner acceptability, risk, privacy, payout, and recordkeeping are assessed. |
| `GATE-DOC03-017` | Landlord/rent request model approved, if applicable | Landlord verification, tenancy evidence, payer-landlord relationship, rent risk, partner approval, and enhanced controls are assessed. |
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
| Payee verification | What verification is required before request creation and payout? | Critical |
| Payee-created requests | What legal, partner, category, and control gates must be satisfied before payee-created requests are enabled for launch? | Critical |
| Payee role | Are payees merchants, sub-merchants, billers, beneficiaries, agents, customers, platform participants, or another role? | Critical |
| PayFac / marketplace | Does payee-created request functionality require PayFac, marketplace, platform, or sub-merchant treatment? | Critical |
| Payer authorization | How must payer authorization be captured and retained? | Critical |
| Landlord-created rent | What controls and restrictions are required before landlord-created rent requests are enabled for production use? | Critical |
| Debt collection | Could overdue invoices, rent, fees, or payment reminders create debt collection implications? | High |
| Privacy boundaries | What payee information may be shown to payer, and what payer information may be shown to payee? | High |
| Recurring requests | Are recurring payee-created requests permitted, or must each request require separate payer authorization? | High |
| Multi-card | What PSP/acquirer, legal, risk, and reconciliation controls apply to MVP multi-card payments with configurable card-count limits? | High |
| Settlement/reserves | What settlement timing, reserves, holdbacks, collateral, or prefunding apply? | High |
| Disclosures | What disclosures are required at request review, checkout, receipt, notification, and payee communications? | High |
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
| `RISK-DOC03-006` | Payee-created requests change PayPlus into PayFac, marketplace, agent, or regulated payment service model. | Complete dedicated role assessment and partner confirmation. | Legal / Compliance / Payments |
| `RISK-DOC03-007` | Payee-created requests are used for fake invoices, fake rent, self-payment, or collusive cashout. | Require onboarding, evidence, relationship checks, limits, monitoring, and payout controls. | Risk / Compliance |
| `RISK-DOC03-008` | Landlord-created rent requests create landlord/tenant, rent collection, debt collection, or heightened consumer protection issues. | Conduct rent-specific legal and risk assessment. | Legal / Compliance / Product |
| `RISK-DOC03-009` | Payer believes a payee-created request is mandatory, validated, or already paid. | Require request-origin disclosure and explicit payer authorization. | Product / Legal |
| `RISK-DOC03-010` | Inadequate payee verification enables fraud or cashout. | Implement payee verification and anti-cashout controls. | Risk / Compliance |
| `RISK-DOC03-011` | Partner reserves or holdbacks create liquidity strain. | Model reserve impact and obtain Finance approval. | Finance / Payments |
| `RISK-DOC03-012` | Partner contract lacks reporting, chargeback, payout, or change-notice support. | Use contractual checklist and Legal review. | Legal / Payments |
| `RISK-DOC03-013` | Privacy, PCI, or security obligations are underestimated. | Complete privacy, security, and PCI review. | Security / Privacy |
| `RISK-DOC03-014` | Required disclosures are incomplete or unclear. | Legal review of request, checkout, receipt, notification, and terms content. | Product / Legal |
| `RISK-DOC03-015` | Payee sees payer-sensitive payment, card, risk, or private profile information. | Enforce data visibility boundaries and RBAC. | Privacy / Security |
| `RISK-DOC03-016` | Regulatory, network, or partner rule changes affect approved flows. | Maintain periodic review and partner change-notice monitoring. | Compliance / Payments |

---

## 14. Assessment Template

Each assessed flow, partner, category, payee type, request creator model, or jurisdiction should use the following template.

```text
Assessment Name:
Assessment Type:
Jurisdiction:
Bill Category:
Payee Type:
Request Creator Type:
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
- Payee journey, if applicable:
- Request creation model:
- Funding flow:
- Payout flow:
- Refund flow:
- Chargeback flow:
- Rejection/query/dispute flow before authorization, if applicable:

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
- Payee-created request support:
- Payee onboarding requirements:
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
- Payer/payee visibility:
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
| `OQ-DOC03-008A` | What legal, PSP/acquirer, payout, and partner gates must payee-created requests and rent payments satisfy before launch enablement? | Legal / Payments / Compliance | Critical | Open |
| `OQ-DOC03-009` | Which bill categories are approved, restricted, prohibited, or enhanced-review for MVP? | Compliance / Risk / Product | Critical | Open |
| `OQ-DOC03-010` | What final KYC/KYB provider, check depth, sanctions screening, exception handling, and risk-tier rules are required before request creation and payout? | Risk / Compliance | Critical | Open |
| `OQ-DOC03-011` | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Commercial | High | Open |
| `OQ-DOC03-012` | What reserves, holdbacks, collateral, prefunding, liquidity, and exception rules apply to the T+1 to T+3 upstream settlement and same-day-after-settlement payout baseline? | Finance / Payments | High | Open |
| `OQ-DOC03-013` | What PSP/acquirer, legal, risk, and reconciliation controls apply to MVP multi-card payments with configurable card-count limits? | Product / Payments / Legal | High | Open |
| `OQ-DOC03-014` | What AML, sanctions, fraud, anti-cashout, collusion, and request-abuse controls are required before MVP? | Compliance / Risk | Critical | Open |
| `OQ-DOC03-015` | What PCI, privacy, security, and data protection requirements apply? | Security / Privacy | High | Open |
| `OQ-DOC03-016` | What partner reporting files or APIs are required for reconciliation and compliance records? | Finance / Engineering | High | Open |
| `OQ-DOC03-017` | What disclosures are required at request review, checkout, receipt, notification, and payee communications? | Legal / Product | High | Open |
| `OQ-DOC03-018` | What contract provisions are mandatory for PSP/acquirer/payout provider agreements? | Legal / Payments | High | Open |
| `OQ-DOC03-019` | What legal, partner, category, and control gates must be satisfied before payee-created requests are enabled for launch? | Project Owner / Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-020` | Which payee types can create payment requests? | Product / Legal / Compliance / Risk | Critical | Open |
| `OQ-DOC03-021` | Are onboarded payees treated as merchants, sub-merchants, billers, beneficiaries, agents, customers, platform participants, or another role? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-022` | Does enabling payee-created requests require PayFac, marketplace, platform, or sub-merchant treatment? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-023` | Do PSP/acquirer and payout partners approve payee-created bill, invoice, fee, or rent request flows? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-024` | What controls and restrictions are required before landlord-created rent requests are enabled for production use? | Product / Legal / Risk / Payments | Critical | Open |
| `OQ-DOC03-025` | What landlord onboarding, identity, property, payout, sanctions, and tenancy evidence checks are required? | Legal / Compliance / Risk | Critical | Open |
| `OQ-DOC03-026` | Could landlord-created rent requests create landlord/tenant, rent collection, or debt collection implications? | Legal / Compliance | High | Open |
| `OQ-DOC03-027` | What invoice evidence and KYB/KYC requirements apply to payee-created invoice or fee requests? | Compliance / Risk / Legal | High | Open |
| `OQ-DOC03-028` | How must payer authorization be captured for payee-created requests? | Legal / Payments / Product | Critical | Open |
| `OQ-DOC03-029` | What information from a payee-created request may be shown to payer, and what payer information may be shown to payee? | Privacy / Security / Legal | High | Open |
| `OQ-DOC03-030` | What pre-authorization rejection, query, or dispute process is required? | Product / Legal / Operations | High | Open |
| `OQ-DOC03-031` | Are recurring payee-created requests permitted, or must each request require separate payer authorization? | Legal / Payments / Product | High | Open |
| `OQ-DOC03-032` | What payee-created request monitoring is required for fake invoices, fake rent, related-party abuse, spam, complaints, and chargebacks? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC03-033` | Are payee onboarding, request, payout, subscription, platform, or other payee-side fees permitted? | Legal / Finance / Commercial | High | Open |
| `OQ-DOC03-034` | What partner contract terms are required for payee onboarding, payee-created requests, payee monitoring, and payee offboarding? | Legal / Payments / Commercial | High | Open |

---

## 16. Downstream Document Impact

`DOC-03` informs downstream documents as follows:

| Document | Impact |
| --- | --- |
| `DOC-04` | Compliance gates, controls, evidence, payee onboarding, payee-created request, rent/invoice controls. |
| `DOC-05` | Product requirements for payment methods, categories, partner constraints, disclosures, payee types, request creator types, and flow limits. |
| `DOC-06` | Payer, payee, landlord, biller, and partner journeys. |
| `DOC-07` | Role, fee, timing, request-origin, refund, risk, authorization, issuer-fee, and payee-created request disclosures. |
| `DOC-08` | Receipts and notifications for request, payment, authorization, status, and failure events. |
| `DOC-09` | Payment request, funds flow, settlement, authorization, partner constraints, and multi-card limits. |
| `DOC-10` | Payout, reconciliation, payout eligibility, reserves, settlement timing, and reporting. |
| `DOC-11` | Refund, cancellation, chargeback, dispute, payer rejection, payee withdrawal, and loss allocation. |
| `DOC-12` | Bill category, OCR, payee verification, invoice evidence, rent evidence, and landlord verification. |
| `DOC-14` | AML, sanctions, fraud, cashout, collusion, fake invoice, fake rent, request abuse, and payee risk controls. |
| `DOC-15` | Privacy, retention, data classification, role-based visibility, masking, approved-purpose access, and sensitive document handling. |
| `DOC-18` | Ledger and reporting fields for regulatory records, request creator type, payee type, payer authorization, disputes, reconciliation, and margin analysis. |
| `DOC-19` | Authentication, tokenization, PCI, RBAC, payer/payee data boundaries, admin access, encryption, and audit controls. |
| `DOC-20` | Launch checklist including DOC-03 gates and approvals. |
| `DOC-21` | Monitoring for partner restrictions, onboarding issues, request abuse, settlement issues, chargebacks, category violations, payout failures, and compliance incidents. |
| `DOC-22` | Admin configuration, review queues, overrides, payment-instruction handling, evidence review, payout exception handling, and operational audit evidence. |

---

## 17. Acceptance Criteria

`DOC-03` is acceptable when it clearly defines:

- PayPlus’s intended regulatory posture;
- the two-sided MVP model;
- why the product is evidence-backed and tied to approved obligations;
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
