---
document_id: DOC-03
title: Regulatory, PSP & Acquirer Assessment
version: 0.2.0
status: Draft
last_updated: 2026-05-26
classification: Internal
owner: Legal / Compliance
reviewers:
  - Project Owner
  - Product Owner
  - Legal / Compliance
  - Payments Lead
  - Risk Lead
  - Finance
  - Operations Lead
  - Engineering Lead
approvers:
  - Project Owner
  - Legal / Compliance Lead
  - Payments Lead
  - Risk Lead
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration
  - DOC-19 Security, Tokenization & Authentication
---

# DOC-03 — Regulatory, PSP & Acquirer Assessment

## 1. Purpose

This document defines the regulatory, PSP, acquirer, payment partner, and banking feasibility assessment framework for PayPlus.

It is intended to answer:

- Whether the proposed PayPlus MVP model is feasible for Hong Kong launch.
- Which regulatory, PSP, acquirer, and banking approvals are required before launch.
- Which payment methods, payout methods, bill categories, and payee types require approval, limitation, or exclusion.
- Which product boundaries must be maintained to avoid wallet, stored value, remittance, cashout, or unrestricted money-transfer positioning.
- Which downstream documents must define detailed operational, technical, compliance, privacy, security, and risk controls.

This document is not a final legal opinion.

Final conclusions must be confirmed by qualified legal counsel, compliance reviewers, PSPs, acquirers, banking partners, payment partners, and relevant internal approvers.

---

## 2. Scope

This document covers:

- Regulatory positioning assessment.
- Hong Kong MVP regulatory considerations.
- PSP/acquirer and payment partner approval requirements.
- High-level payment method feasibility.
- High-level payout and settlement feasibility.
- Bill category and payee-type approval principles.
- Anti-wallet, anti-cashout, and non-remittance positioning requirements.
- Launch approval gates.
- Assumptions, risks, dependencies, and open questions.

This document does not define detailed requirements for:

| Area | Owned By |
|---|---|
| Payment request lifecycle, funding flow, and settlement states | `DOC-09` |
| Payout workflow, reconciliation, payout exceptions, and finance operations | `DOC-10` |
| Refunds, cancellations, disputes, and chargebacks | `DOC-11` |
| Bill category rules, OCR, document AI, and payee verification | `DOC-12` |
| AML, fraud, velocity limits, transaction monitoring, and anti-cashout rules | `DOC-14` |
| Privacy, data protection, document retention, and access control | `DOC-15` |
| API contracts, webhook behavior, and third-party integration details | `DOC-17` |
| PCI, tokenization, authentication, and security architecture | `DOC-19` |
| Engineering repository structure, codebase layout, or implementation design | Engineering architecture documentation |

---

## 3. Product Context

PayPlus is intended to be a **bill-backed payment and settlement platform**.

For MVP, PayPlus is expected to support Hong Kong users who submit eligible bills or approved payment obligations and fund those payment requests using supported payment methods.

Intended MVP funding methods:

- Credit card.
- AlipayHK.
- FPS.

Candidate payout methods:

- FPS.
- Online banking transfer.
- EPS, where feasible.
- Cheque.

PayPlus must preserve a bill-backed model and must not be positioned or implemented as:

- A general wallet.
- A stored value facility.
- A cash balance or top-up product.
- An unrestricted peer-to-peer transfer product.
- A remittance product.
- A cashout product.
- A payroll product.
- A lending product.
- A crypto or investment funding product.
- A general e-commerce checkout product.

---

## 4. Core Assessment Principles

| Principle | Requirement |
|---|---|
| Bill-backed model | Each payment request must be linked to an eligible bill, invoice, payee, biller, merchant, or approved payment obligation. |
| No stored value positioning | PayPlus must not present user funds as wallet balance, stored balance, cash balance, or top-up balance unless separately approved. |
| No unrestricted transfers | PayPlus must not allow general user-to-user, user-to-person, remittance, or cashout transfers. |
| PSP/acquirer alignment | The operating model must be accepted by selected PSPs, acquirers, wallet partners, payment partners, and banking partners. |
| Category approval | Bill categories must be approved, limited, deferred, or prohibited before production use. |
| Payee approval | Payee types must be assessed before payout is enabled, especially personal payees. |
| Evidence-based operation | PayPlus must retain sufficient evidence for authorization, bill validation, payee review, settlement, disputes, and audits. |
| Risk-based controls | Higher-risk categories, payees, funding methods, or transaction patterns must trigger enhanced review in downstream controls. |

---

## 5. Regulatory Positioning

### 5.1 Intended Positioning

The intended positioning for PayPlus is:

> PayPlus is a bill-backed payment facilitation and settlement coordination platform that helps users fund eligible payment obligations through supported payment methods and facilitates settlement to approved payees, subject to verification, partner rules, risk controls, and operational procedures.

This positioning must be validated by Legal / Compliance before launch.

### 5.2 Required Positioning Controls

| Control Area | Requirement |
|---|---|
| Payment purpose | Payment requests must be tied to eligible bills or approved payment obligations. |
| Payee linkage | Payout recipients must be linked to the underlying bill or obligation. |
| Funding source | Funding methods must be approved by PSP/acquirer/payment partners. |
| User authorization | Users must authorize payment amount, fees, payout destination, and applicable terms. |
| Product language | Product language must avoid wallet, stored value, top-up, cashout, remittance, and payroll positioning. |
| Refund discipline | Refunds must follow funding-method, PSP/acquirer, and operational rules. |
| Evidence retention | PayPlus must retain evidence of authorization, bill, payee, payment, payout, and reconciliation activity. |

### 5.3 Legal / Compliance Questions

The following require legal and compliance confirmation.

| Area | Question |
|---|---|
| Licensing | Does PayPlus require any license, registration, exemption, or partner operating structure for Hong Kong MVP? |
| Stored value | Could the funding or settlement model be considered stored value or wallet activity? |
| Money service / remittance | Could any flow be considered money service, money transmission, or remittance activity? |
| Personal payees | Are payouts to personal payees permitted, restricted, or prohibited under the intended model? |
| Domestic helper salary | Does this use case create payroll, employment-payment, remittance, or cashout concerns? |
| Card-funded bill payment | Could any card-funded category be treated as cash-equivalent, quasi-cash, restricted, or prohibited? |
| Promotions / rewards | Do discounts, cashback, vouchers, referrals, or partner-funded campaigns create additional regulatory or consumer-disclosure obligations? |

---

## 6. Hong Kong MVP Regulatory Considerations

For Hong Kong MVP, the following areas must be assessed before launch.

| Area | Required Assessment |
|---|---|
| Operating model | Confirm that PayPlus can operate under the proposed bill-backed model. |
| Stored value risk | Confirm that PayPlus does not unintentionally create a wallet or stored value facility. |
| Money service / remittance risk | Confirm that PayPlus does not create unrestricted money transfer or remittance activity. |
| AML / CTF | Confirm required level of customer, payee, transaction, and suspicious-activity controls. |
| Card scheme / acquirer rules | Confirm treatment of bill payment, personal payees, high-risk categories, refunds, disputes, and chargebacks. |
| Alternative payment methods | Confirm rules for AlipayHK, FPS, and any other supported payment method. |
| Consumer disclosures | Confirm requirements for fees, timing, rejected payments, refunds, and complaints. |
| Privacy and records | Confirm requirements for bill documents, personal data, retention, access control, and deletion. |
| Security / PCI | Confirm card data handling, tokenization, authentication, and integration obligations. |

Detailed control design belongs in the relevant downstream documents listed in Section 2.

---

## 7. PSP, Acquirer, Payment Partner, and Banking Assessment

### 7.1 Required Partner Capabilities

PayPlus may require partners to support:

- Card acceptance.
- Card tokenization.
- Authentication / 3DS.
- AlipayHK acceptance.
- FPS collection and/or payout.
- Settlement reporting.
- Refund processing.
- Chargeback and dispute handling.
- Webhooks and payment status updates.
- Payout or bank transfer support.
- Reconciliation reports.
- Merchant underwriting and category approval.
- Risk, reserve, or transaction-limit requirements.

### 7.2 Partner Assessment Criteria

| Category | Assessment Criteria |
|---|---|
| Model fit | Partner accepts PayPlus bill-backed payment and settlement model. |
| Hong Kong support | Partner supports Hong Kong merchant setup, currency, settlement, and local methods. |
| Payment methods | Partner supports required funding methods for MVP. |
| Payout support | Partner supports required payout or settlement model, if applicable. |
| Category acceptance | Partner confirms approved, restricted, and prohibited bill categories. |
| Personal payees | Partner confirms whether personal payees are allowed, limited, or prohibited. |
| Card treatment | Partner confirms MCC, descriptor, quasi-cash/cash-equivalent treatment, and chargeback implications. |
| Refunds / disputes | Partner supports required refund, cancellation, and chargeback processes. |
| Reporting | Partner provides reports sufficient for reconciliation, audit, and dispute evidence. |
| Risk controls | Partner confirms applicable transaction limits, reserves, holds, monitoring, or underwriting conditions. |
| Technical readiness | Partner provides required APIs, webhooks, sandbox, idempotency, and production support. |
| Commercial terms | Partner provides pricing, settlement cycle, reserves, chargeback fees, payout fees, and other costs. |

### 7.3 Minimum Due Diligence Questions

Before selecting or launching with a partner, PayPlus should obtain answers to the following.

| Question ID | Question |
|---|---|
| `DDQ-DOC03-001` | Does the partner approve the PayPlus bill-backed model? |
| `DDQ-DOC03-002` | Which MVP bill categories are approved, restricted, or prohibited? |
| `DDQ-DOC03-003` | Are personal payees supported, limited, or prohibited? |
| `DDQ-DOC03-004` | Is domestic helper salary supported, restricted, or prohibited? |
| `DDQ-DOC03-005` | Are card-funded bill payments treated as purchase, bill payment, quasi-cash, cash-equivalent, or another category? |
| `DDQ-DOC03-006` | What MCC and transaction descriptor will apply? |
| `DDQ-DOC03-007` | What transaction limits, reserves, holds, or risk conditions apply? |
| `DDQ-DOC03-008` | What refund, dispute, chargeback, and evidence rules apply? |
| `DDQ-DOC03-009` | What settlement, payout, and reconciliation reports are available? |
| `DDQ-DOC03-010` | What onboarding, underwriting, compliance review, and production approval steps are required? |

---

## 8. Payment Method Feasibility

DOC-03 only determines whether a payment method is feasible and approved at a high level.

Detailed funding flows, transaction states, retry behavior, webhook handling, and reconciliation requirements belong in `DOC-09`, `DOC-10`, `DOC-11`, `DOC-17`, and `DOC-19`.

### 8.1 MVP Funding Methods

| Method | MVP Direction | Required Confirmation |
|---|---:|---|
| Credit card | Intended | PSP/acquirer approval, MCC/category treatment, tokenization, authentication, refund, dispute, chargeback, settlement, reserve, and limit rules. |
| AlipayHK | Intended | Partner approval, supported categories, authorization flow, refund rules, settlement reporting, limits, and dispute handling. |
| FPS | Intended | Collection model, banking/PSP support, reference matching, confirmation timing, refund/reversal feasibility, reporting, and limits. |

### 8.2 Future Payment Methods

No future payment method should be added without review of:

- Regulatory impact.
- PSP/acquirer/payment partner support.
- Category and payee restrictions.
- Refund and dispute handling.
- Settlement and reconciliation impact.
- Risk, AML, fraud, and anti-cashout impact.
- Privacy and data impact.
- Unit economics impact.

---

## 9. Payout and Settlement Feasibility

DOC-03 only assesses whether payout and settlement methods are feasible and approvable.

Detailed payout workflows, cutoff times, maker-checker controls, settlement states, bank file processing, reconciliation, and exception handling belong in `DOC-10`.

### 9.1 Candidate Payout Methods

| Method | Direction | Required Confirmation |
|---|---:|---|
| FPS | Candidate | Banking/partner support, payee eligibility, account validation, limits, timing, failure handling, and reporting. |
| Online banking transfer | Candidate | Bank support, approval workflow, settlement timing, fees, references, and reconciliation data. |
| EPS | Candidate where feasible | Availability, payee support, settlement process, reporting, and operational constraints. |
| Cheque | Candidate / fallback | Operational feasibility, approval controls, mailing/collection process, stale cheque handling, and audit evidence. |

### 9.2 Payout Boundary

PayPlus must not allow unrestricted payout to arbitrary recipients.

Payouts must remain linked to:

- An eligible bill.
- An approved payment obligation.
- An approved payee.
- An approved payout method.
- A completed risk and operational review where required.

---

## 10. Bill Category and Payee Approval

DOC-03 defines the approval framework only.

Detailed bill evidence rules, OCR extraction, document validation, payee verification, category-specific requirements, and operational review workflows belong in `DOC-12` and `DOC-14`.

### 10.1 Category Decision Types

Each bill category must receive one of the following decisions before production use.

| Decision | Meaning |
|---|---|
| Approved | Category may be supported subject to standard controls. |
| Approved with limits | Category may be supported only with specific limits, disclosures, reviews, or payout restrictions. |
| Pilot only | Category may be tested with limited users, lower limits, and manual review. |
| Deferred | Category is not supported for MVP but may be reviewed later. |
| Prohibited | Category must not be supported under the current model. |
| Legal / partner approval required | Category cannot proceed until legal and/or partner approval is obtained. |

### 10.2 Initial Category Direction

| Category | Initial Direction | Primary Reason |
|---|---:|---|
| Utilities | Candidate for approval | Standard bill payment use case; requires payee/reference validation. |
| Telecom / Internet | Candidate for approval | Standard bill payment use case; requires account/reference validation. |
| Government / public fees | Review required | Acceptance, reference, and settlement rules may vary. |
| Education fees | Review required | Institutional payee and privacy considerations. |
| Insurance premiums | Review required | Regulatory, refund, and card acceptance considerations. |
| Property management fees | Review required | Payee validation and reconciliation considerations. |
| Rent to institutional landlord | Review required | High-value payment and evidence requirements. |
| Rent to individual landlord | Higher-risk / limited review | Personal payee and cashout risk. |
| Medical bills | Review required | Sensitive data and refund considerations. |
| Domestic helper salary | Not approved unless separately approved | Payroll, remittance, personal payee, employment-payment, and cashout concerns. |
| Personal IOU / personal transfer | Prohibited for MVP | Unrestricted transfer and cashout risk. |
| Crypto / investment funding | Prohibited | Regulatory and high-risk activity. |
| Gambling / betting | Prohibited | Restricted or prohibited activity. |
| Cash withdrawal / cash advance | Prohibited | Cashout and quasi-cash risk. |
| General wallet top-up | Prohibited | Stored value / wallet risk. |

### 10.3 Payee-Type Direction

| Payee Type | Initial Direction | Primary Requirement |
|---|---:|---|
| Verified institutional biller | Preferred | Validate biller identity and payout destination. |
| Government or public body | Candidate | Confirm accepted payment route and reference rules. |
| Utility / telecom provider | Candidate | Validate account reference and reconciliation approach. |
| School / education institution | Review required | Validate institution and privacy handling. |
| Insurance company | Review required | Confirm regulatory, refund, and card acceptance implications. |
| Corporate landlord / property manager | Review required | Validate lease/invoice and payout account. |
| Individual landlord | Higher-risk / limited | Requires enhanced review and anti-cashout controls. |
| Domestic helper | Not approved unless separately approved | Requires dedicated legal, PSP/acquirer, AML, and operational approval. |
| Individual service provider | Higher-risk / limited | Requires evidence, identity, account, and collusion-risk review. |
| Arbitrary individual | Prohibited for MVP | No unrestricted payout. |

---

## 11. Non-Wallet, Non-Remittance, and Anti-Cashout Boundaries

This section defines product boundaries only.

Detailed monitoring rules, velocity limits, risk scoring, manual review triggers, and fraud controls belong in `DOC-14`.

### 11.1 Prohibited Behaviors

PayPlus MVP must not support:

- User wallet balance.
- Stored value balance.
- User top-up account.
- Withdrawable cash balance.
- Unrestricted P2P transfer.
- User-to-self payout.
- Card-funded cash withdrawal.
- Card-funded wallet top-up.
- Card-funded gambling, investment, or crypto funding.
- Generic “send money” flow.
- Generic “cash advance” flow.
- Overpayment payout to user.
- Payout to arbitrary recipient without bill evidence.

### 11.2 Product Language Rules

Use terms such as:

- Payment request.
- Bill payment.
- Eligible bill.
- Approved payee.
- Payment obligation.
- Funding method.
- Settlement.
- Service fee.
- Payment status.

Avoid terms such as:

- Wallet.
- Stored balance.
- Cash balance.
- Top up.
- Withdraw.
- Cash out.
- Send money.
- Remit.
- Payroll service.
- Salary service.
- Loan.
- Advance.

---

## 12. Launch Approval Gates

PayPlus should not launch MVP payment functionality until the required gates are complete.

| Gate ID | Gate | Required Evidence |
|---|---|---|
| `GATE-DOC03-001` | Legal / compliance model review | Written legal/compliance approval or risk acceptance. |
| `GATE-DOC03-002` | PSP/acquirer approval | Written confirmation that the PayPlus model and MVP categories are acceptable. |
| `GATE-DOC03-003` | Credit card approval | Confirmation of card acceptance, MCC/category treatment, tokenization, refunds, disputes, chargebacks, settlement, and limits. |
| `GATE-DOC03-004` | AlipayHK approval | Confirmation of acceptance, category support, refund, settlement, and operating rules. |
| `GATE-DOC03-005` | FPS/banking approval | Confirmation of FPS/banking collection and/or payout model. |
| `GATE-DOC03-006` | Category approval | Approved MVP category list with restrictions and prohibited categories. |
| `GATE-DOC03-007` | Payee-type approval | Explicit decision on institutional payees, personal payees, domestic helpers, and arbitrary individuals. |
| `GATE-DOC03-008` | Non-wallet / anti-cashout boundary approval | Risk approval that product boundaries and required controls are sufficient for MVP. |
| `GATE-DOC03-009` | Downstream control readiness | Confirmation that required controls are defined in `DOC-09`, `DOC-10`, `DOC-11`, `DOC-12`, `DOC-14`, `DOC-15`, `DOC-17`, and `DOC-19`. |
| `GATE-DOC03-010` | Launch decision | Project Owner approval after required legal, partner, risk, product, payment, and operations sign-offs. |

---

## 13. Assumptions

| Assumption ID | Assumption | Owner | Status |
|---|---|---|---|
| `ASM-DOC03-001` | MVP launch geography is Hong Kong only. | Project Owner | Assumed |
| `ASM-DOC03-002` | PayPlus will operate as a bill-backed payment and settlement platform. | Legal / Compliance | Requires validation |
| `ASM-DOC03-003` | PayPlus will not provide wallet balance, top-up balance, or withdrawable funds. | Product / Legal | Requires validation |
| `ASM-DOC03-004` | Credit card, AlipayHK, and FPS are intended MVP funding methods. | Product / Payments | Assumed |
| `ASM-DOC03-005` | FPS, online banking transfer, EPS, and cheque are candidate payout methods. | Payments / Operations | Assumed |
| `ASM-DOC03-006` | PSP/acquirer partners will approve the model and supported MVP categories. | Payments Lead | Requires validation |
| `ASM-DOC03-007` | Personal payees will be restricted or excluded unless separately approved. | Legal / Risk | Requires decision |
| `ASM-DOC03-008` | Domestic helper salary will not be enabled unless separately approved. | Legal / Compliance | Requires decision |
| `ASM-DOC03-009` | Detailed operational and technical controls will be defined in downstream documents. | Project Owner | Assumed |

---

## 14. Key Risks

| Risk ID | Risk | Impact | Primary Mitigation |
|---|---|---:|---|
| `RISK-DOC03-001` | PayPlus requires license, registration, exemption, or model change. | High | Obtain legal review before launch. |
| `RISK-DOC03-002` | PSP/acquirer rejects the model or key categories. | High | Validate early and limit MVP scope. |
| `RISK-DOC03-003` | Card-funded bill payments are treated as quasi-cash or restricted. | High | Confirm MCC, category treatment, and scheme/acquirer rules. |
| `RISK-DOC03-004` | Product is perceived as wallet, remittance, or cashout. | High | Enforce positioning, product language, category limits, and payout boundaries. |
| `RISK-DOC03-005` | Personal payees enable cashout or collusion. | High | Exclude or apply enhanced approval and controls. |
| `RISK-DOC03-006` | Domestic helper salary creates payroll, remittance, or employment-payment risk. | High | Exclude unless separately approved. |
| `RISK-DOC03-007` | Chargeback occurs after payout and funds cannot be recovered. | High | Define controls in `DOC-11` and payout rules in `DOC-10`. |
| `RISK-DOC03-008` | Sensitive bill documents create privacy or retention risk. | Medium | Define controls in `DOC-15`. |
| `RISK-DOC03-009` | Reconciliation gaps create payment or payout errors. | Medium | Define controls in `DOC-10`. |
| `RISK-DOC03-010` | Categories expand without approval. | Medium | Require category governance and change approval. |

---

## 15. Dependencies

| Dependency ID | Dependency | Owner | Related Document |
|---|---|---|---|
| `DEP-DOC03-001` | Legal review of PayPlus operating model. | Legal / Compliance | `DOC-03`, `DOC-04` |
| `DEP-DOC03-002` | PSP/acquirer approval. | Payments Lead | `DOC-03`, `DOC-17` |
| `DEP-DOC03-003` | Payment method feasibility and integration design. | Payments / Engineering | `DOC-09`, `DOC-17`, `DOC-19` |
| `DEP-DOC03-004` | Payout method feasibility and reconciliation design. | Payments / Operations / Finance | `DOC-10` |
| `DEP-DOC03-005` | Bill category and payee verification requirements. | Product / Risk | `DOC-12` |
| `DEP-DOC03-006` | AML, fraud, and anti-cashout control design. | Risk / Compliance | `DOC-14` |
| `DEP-DOC03-007` | Privacy and document retention requirements. | Legal / Privacy | `DOC-15` |
| `DEP-DOC03-008` | Refund, cancellation, and chargeback requirements. | Payments / Operations | `DOC-11` |

---

## 16. Open Questions

| Question ID | Question | Owner | Status |
|---|---|---|---|
| `OQ-DOC03-001` | Does PayPlus require any license, registration, exemption, or specific partner structure for Hong Kong MVP? | Legal / Compliance | Open |
| `OQ-DOC03-002` | Which PSP/acquirer can support the bill-backed model? | Payments Lead | Open |
| `OQ-DOC03-003` | What MCC, transaction descriptor, and category classification will apply to card payments? | Payments Lead | Open |
| `OQ-DOC03-004` | Which MVP bill categories are approved, limited, deferred, or prohibited? | Product / Risk | Open |
| `OQ-DOC03-005` | Are personal payees allowed at MVP? If yes, under what limits? | Legal / Risk | Open |
| `OQ-DOC03-006` | Is domestic helper salary excluded, deferred, or approved with enhanced controls? | Legal / Compliance | Open |
| `OQ-DOC03-007` | Can AlipayHK support the intended MVP categories? | Payments Lead | Open |
| `OQ-DOC03-008` | Can FPS support collection, payout, or both? | Payments / Banking | Open |
| `OQ-DOC03-009` | What payout methods are operationally feasible at launch? | Operations / Payments | Open |
| `OQ-DOC03-010` | What refund and chargeback liability model applies after payout? | Payments / Operations | Open |
| `OQ-DOC03-011` | What transaction limits should apply by category, user, payee, and funding method? | Risk | Open |
| `OQ-DOC03-012` | What launch restrictions are required if partner approval is conditional? | Project Owner | Open |

---

## 17. MVP Readiness Checklist

| Checklist Item | Owner | Status |
|---|---|---|
| Legal / compliance model assessment completed. | Legal / Compliance | Not started |
| Stored value / wallet risk assessment completed. | Legal / Compliance | Not started |
| Money service / remittance risk assessment completed. | Legal / Compliance | Not started |
| PSP/acquirer approval obtained. | Payments Lead | Not started |
| Credit card acceptance and category treatment confirmed. | Payments Lead | Not started |
| AlipayHK acceptance confirmed. | Payments Lead | Not started |
| FPS/banking feasibility confirmed. | Payments / Banking | Not started |
| MVP category list approved. | Product / Risk | Not started |
| Payee-type policy approved. | Legal / Risk | Not started |
| Domestic helper salary decision recorded. | Legal / Compliance | Not started |
| Non-wallet and anti-cashout boundaries approved. | Risk / Compliance | Not started |
| Required downstream documents reviewed for launch readiness. | Project Owner | Not started |
| Final launch approval completed. | Project Owner | Not started |

---

## 18. Version History

| Version | Date | Author | Notes |
|---|---|---|---|
| 0.1.0 | 2026-05-26 | Product / Compliance Draft | Initial extended draft. |
| 0.2.0 | 2026-05-26 | Product / Compliance Draft | Simplified to assessment-level scope; removed implementation/codebase content and reduced overlap with downstream documents. |
