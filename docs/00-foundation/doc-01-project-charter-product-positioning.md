---
document_id: DOC-01
title: Project Charter & Product Positioning
version: 0.2.0
status: Draft
owner: Product Owner
reviewers:
  - Product Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Commercial Lead
approvers:
  - Product Lead
  - Project Owner
last_updated: 2026-05-26
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
---

# DOC-01 — Project Charter & Product Positioning

## 1. Purpose

This document defines the product charter, intended positioning, product boundaries, candidate MVP scope, assumptions, constraints, risks, dependencies, and open questions for PayPlus.

`DOC-01` is a foundation document.

It is intended to guide downstream product, payment, compliance, risk, security, engineering, and operational documentation.

This document does not define detailed requirements, technical specifications, legal conclusions, compliance determinations, security controls, payment processing rules, or operational procedures.

Those topics must be defined in downstream documents.

---

## 2. Product Summary

PayPlus is intended to be a card-funded bill payment platform.

The product is designed to let eligible users pay eligible real-world bills by card, while PayPlus or its payment partners route payment value to approved payees through supported settlement or payout methods.

The intended product model is:

1. A user submits a bill payment request.
2. The user provides or selects bill evidence.
3. PayPlus verifies bill eligibility and payee validity.
4. The user pays by supported card funding source.
5. PayPlus or its payment partner collects the card payment.
6. PayPlus or its payment partner settles, transfers, or pays the approved biller, payee, or receiving account.
7. PayPlus records the transaction, reconciliation status, audit trail, receipt, and any applicable service fee or promotion.

PayPlus should not be positioned as a general wallet, stored-value account, remittance service, cash withdrawal service, peer-to-peer transfer app, or payroll product unless separately assessed, approved, and documented.

---

## 3. Product Intent

The intended product intent is to help users pay valid bills using card funding sources in a controlled, compliant, and auditable way.

The core product goals are:

- Enable card-funded bill payments for eligible bill categories.
- Improve user convenience where billers or payees do not directly accept cards.
- Support multi-card or multi-funding-source payment behavior where commercially, technically, and compliance-feasible.
- Provide transparent pricing and disclosures.
- Maintain strong anti-cashout and fraud controls.
- Maintain bill verification and payee validation controls.
- Maintain transaction traceability from card funding through payout or settlement.
- Maintain auditable evidence for compliance, risk, reconciliation, user support, and partner review.

---

## 4. Product Positioning

PayPlus should be positioned as:

> A controlled card-funded bill payment service that enables users to pay eligible verified bills through approved payment rails.

PayPlus may use positioning language such as:

- Card-funded bill payment.
- Bill payment facilitation.
- Pay eligible bills by card.
- Split or combine eligible card payments for an approved bill, where supported.
- Pay approved billers, merchants, or payees through PayPlus-supported payout or settlement methods.
- Track bill payment status, receipt, and payment evidence.

PayPlus should avoid positioning language such as:

- Wallet.
- Stored value.
- Cash advance.
- Cash withdrawal.
- Cashout.
- Money transfer to anyone.
- Peer-to-peer transfer.
- Remittance.
- Payroll advance.
- Credit limit liquidation.
- Convert card limit to cash.
- Instant cash from credit card.
- Send money freely to any account.
- Bank account top-up.
- Prepaid balance or stored balance.

Final public language must be reviewed in `DOC-07 Content, Disclosure & User Communication`.

---

## 5. Product Problem Statement

Many users may want to pay bills using card funding sources for convenience, liquidity management, rewards, recordkeeping, or payment flexibility.

However, not all billers accept cards directly.

Some bill payments may require bank transfer, biller portal payment, account transfer, or other payout methods.

PayPlus aims to bridge this gap by allowing eligible users to fund a verified bill payment by card while ensuring that payment value is routed only toward approved bill obligations and not misused for cashout, unauthorized transfer, or unsupported use cases.

---

## 6. Target Users

Candidate target users may include:

- Individuals who need to pay eligible household bills.
- Individuals who want to use card funding for bill payments where direct card acceptance is unavailable or inconvenient.
- Users who want receipts, tracking, and consolidated payment history.
- Users who want to split a large eligible bill across more than one supported funding source, if supported.
- Users eligible for promotions, rewards, or partner-funded offers, if available.

The final target user definition must be validated in the Master PRD and market research artifacts.

---

## 7. Candidate Bill Categories

Candidate bill categories may include:

| Category | Example Use Cases | Notes |
|---|---|---|
| Utilities | Electricity, water, gas, internet, mobile, telecom | Usually strong bill evidence and payee traceability. |
| Rent or property-related payments | Rent, property management fees, maintenance charges | Higher risk; may require stronger payee verification and anti-cashout controls. |
| Education | Tuition, school fees, course fees | May require institution validation. |
| Insurance | Health, auto, property, life insurance premiums | May require biller and policy validation. |
| Taxes and government fees | Taxes, fines, permit fees, public authority payments | Must be assessed for legal and partner feasibility. |
| Healthcare | Clinic, hospital, medical bills | Privacy and sensitive data handling considerations. |
| Loan or financing payments | Installments, financing obligations | May be restricted by partner, card network, or regulatory rules. |
| Business invoices | Supplier invoices, service invoices | May require business KYB, invoice validation, and category controls. |

Candidate categories are not automatically approved.

Each category must be assessed through:

- `DOC-03 Regulatory, PSP & Acquirer Assessment`.
- `DOC-12 Bill Category, Document AI/OCR & Payee Verification`.
- `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`.
- Applicable partner, card network, acquirer, and regulatory requirements.

---

## 8. Product Boundaries

### 8.1 In-Scope Product Capabilities

The following capabilities are candidates for PayPlus scope, subject to downstream approval:

- User registration and authentication.
- User profile and eligibility checks.
- Bill upload or bill detail entry.
- Bill document capture, OCR, or structured data extraction.
- Bill category classification.
- Payee validation.
- Bill eligibility checks.
- Payment quote and service fee calculation.
- Card payment authorization and capture.
- Multi-card or multi-source funding for one approved bill, where supported.
- Payment status tracking.
- Payout or settlement to approved payees.
- Transaction receipt generation.
- User notifications.
- Refund, cancellation, reversal, and exception handling.
- Promotion or campaign eligibility.
- Audit trail and reconciliation reporting.
- Risk review and manual review workflows.
- Compliance evidence retention.

### 8.2 Out-of-Scope Product Capabilities

Unless separately assessed and approved, PayPlus should not support:

- General-purpose stored balance.
- User wallet balance.
- Peer-to-peer transfers.
- Cash withdrawals.
- Cash advances.
- Card-to-bank-account cashout.
- Bank account top-up.
- Crypto purchases or transfers.
- Gambling or gaming top-ups.
- High-risk merchant categories not approved by compliance and partners.
- Payroll disbursement.
- Lending or credit underwriting by PayPlus.
- Consumer credit issuance by PayPlus.
- Unrestricted transfers to arbitrary recipients.
- Bill payments without sufficient bill evidence.
- Payout to unverified recipients.
- User-directed payout unrelated to a verified bill obligation.

---

## 9. Candidate MVP Scope

The candidate MVP should focus on a narrow, controlled launch.

Recommended MVP principles:

- Start with a limited number of low-risk bill categories.
- Start with a limited geography.
- Start with approved PSP, acquirer, bank, and payout partners.
- Start with a limited set of supported cards and payment methods.
- Require strong bill evidence before payment completion or payout.
- Require payee verification before payout.
- Use transaction limits and velocity controls.
- Use manual review for higher-risk transactions.
- Maintain clear user disclosures.
- Maintain full audit trail and reconciliation evidence.
- Avoid user wallet, stored value, cashout, and open money transfer behavior.

### 9.1 Candidate MVP Features

Candidate MVP features may include:

| Feature | Candidate MVP Treatment |
|---|---|
| User registration | In scope. |
| User authentication | In scope. |
| Basic user profile | In scope. |
| KYC/KYB | To be determined based on jurisdiction, partner model, bill category, and risk assessment. |
| Bill upload | In scope. |
| Manual bill data entry | In scope with validation. |
| OCR/document AI | Optional for MVP; may begin as assisted or back-office workflow. |
| Bill category eligibility | In scope. |
| Payee verification | In scope. |
| Card payment | In scope through approved PSP/acquirer. |
| Multi-card split payment | Candidate feature; may be deferred if complexity or partner risk is high. |
| Payment quote and fee disclosure | In scope. |
| Payout to payee | In scope through approved payout method. |
| User receipt | In scope. |
| Notifications | In scope for key lifecycle events. |
| Refund/cancellation | In scope at minimum viable process level. |
| Promotion engine | Optional; should not block MVP unless commercially required. |
| Partner advertisements | Out of initial MVP unless separately approved. |
| Admin review console | In scope for manual review and operations. |
| Reconciliation reporting | In scope. |
| Risk monitoring | In scope. |

### 9.2 Candidate MVP Bill Categories

Candidate MVP categories should be selected based on:

- Clear bill evidence.
- Verified payee identity.
- Lower cashout risk.
- Clear settlement or payout path.
- PSP/acquirer acceptance.
- Regulatory feasibility.
- Operational ability to review exceptions.
- User demand.
- Commercial viability.

Preferred MVP candidates may include:

- Utilities.
- Telecom or internet bills.
- Education fees.
- Insurance premiums.

Higher-risk categories such as rent, business invoices, loan repayment, or tax payments may require additional controls and may be deferred until later phases.

---

## 10. Non-MVP / Future Scope

Future scope may include:

- Additional bill categories.
- More countries or jurisdictions.
- More payment methods.
- Bank account funding.
- Wallet funding, only if legally and operationally approved.
- Advanced OCR/document AI automation.
- Advanced risk scoring.
- Partner-funded campaigns.
- Merchant or biller portal integrations.
- Biller directory.
- Automated payout routing.
- Enhanced reconciliation automation.
- Advanced reporting.
- Business user support.
- Multi-user or delegated account access.
- API access for partners.
- Partner advertisement modules.
- Loyalty or reward integrations.

Future scope must not be implemented until feasibility, compliance, risk, commercial, technical, and operational requirements are defined and approved.

---

## 11. Key Business Objectives

The key business objectives for PayPlus are:

- Build a compliant and trusted bill payment service.
- Enable card-funded bill payment in categories where users value payment flexibility.
- Create a sustainable service-fee or partner-funded revenue model.
- Maintain positive unit economics after card processing, payout, risk, refunds, operations, and support costs.
- Avoid unsupported wallet, cashout, remittance, and money-transfer positioning.
- Build scalable bill verification, risk review, and reconciliation processes.
- Support future growth into new categories, partners, and jurisdictions.

Detailed commercial assumptions belong in `DOC-02 Business Model & Unit Economics`.

---

## 12. Product Principles

PayPlus should follow these product principles:

| Principle | Meaning |
|---|---|
| Verified bill first | Payment should be tied to a valid bill or eligible payment obligation. |
| Approved payee only | Payout should go only to a verified and approved payee or biller. |
| No unrestricted cashout | The product should not enable card-funded cash withdrawal or unrestricted transfer. |
| Transparent pricing | Users should see service fees and total cost before payment confirmation. |
| Traceable lifecycle | Each transaction should be traceable from request through funding, payout, reconciliation, and receipt. |
| Risk-based controls | Higher-risk categories or behaviors should trigger stronger review and limits. |
| Compliance by design | Compliance, privacy, risk, and partner constraints should shape product behavior. |
| Operationally reviewable | Staff should be able to review exceptions, evidence, and transaction history. |
| Scalable automation | Manual controls may be used early, but should be designed for future automation. |
| Clear user communication | Users should receive clear, accurate, non-misleading status and receipt information. |

---

## 13. High-Level Transaction Lifecycle

The intended high-level lifecycle is:

1. User signs in.
2. User creates a bill payment request.
3. User provides bill details and/or uploads bill evidence.
4. PayPlus classifies the bill category.
5. PayPlus validates required bill fields.
6. PayPlus verifies or reviews the payee.
7. PayPlus calculates fees, limits, and eligibility.
8. User confirms payment quote and disclosures.
9. User pays by supported card funding source.
10. PSP/acquirer authorizes and captures the card payment.
11. PayPlus records funding status.
12. PayPlus performs final risk, compliance, and payout readiness checks.
13. PayPlus or partner initiates payout or settlement to approved payee.
14. PayPlus monitors payout status.
15. PayPlus reconciles funding, fees, payout, and exceptions.
16. User receives confirmation, receipt, and status updates.
17. Records are retained according to approved retention rules.

Detailed state machines and payment lifecycle rules belong in:

- `DOC-09 Payment Request, Multi-Funding Source & Settlement`.
- `DOC-10 Payout & Reconciliation`.
- `DOC-11 Refund, Cancellation & Chargeback`.

---

## 14. Commercial Model Summary

The candidate commercial model may include:

- User-paid service fees.
- Biller-paid or partner-paid fees.
- Campaign-funded subsidies.
- Partner-funded promotions.
- Advertisement or sponsored placement revenue, if later approved.
- Revenue share with billers, PSPs, or partners, if commercially and legally feasible.

The commercial model must consider:

- Card processing fees.
- Scheme fees.
- Acquirer fees.
- PSP fees.
- Payout fees.
- Bank transfer fees.
- FX costs, where applicable.
- Refund and chargeback losses.
- Fraud losses.
- Promotion costs.
- Manual review costs.
- Customer support costs.
- Reconciliation and operations costs.
- Compliance and audit costs.
- Tax treatment.

Detailed unit economics belong in `DOC-02 Business Model & Unit Economics`.

---

## 15. Compliance and Regulatory Positioning Summary

PayPlus must be assessed before launch against applicable legal, regulatory, card network, PSP, acquirer, banking, privacy, AML, consumer protection, and advertising requirements.

Important positioning assumptions include:

- PayPlus is intended as a bill payment facilitation service.
- PayPlus should avoid stored-value or wallet behavior unless separately approved.
- PayPlus should avoid unrestricted money transmission behavior unless licensed, exempt, sponsored, or otherwise approved.
- PayPlus should not enable cashout from card funding sources.
- PayPlus should maintain evidence that funded payments correspond to valid bills or obligations.
- PayPlus should maintain evidence that payout recipients are approved payees.
- PayPlus should use approved payment partners and settlement models.
- PayPlus should maintain appropriate disclosures and user consent.

Final regulatory and compliance assessment belongs in:

- `DOC-03 Regulatory, PSP & Acquirer Assessment`.
- `DOC-04 Compliance Certification Roadmap & Control Framework`.
- `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`.
- `DOC-15 Privacy, Data Protection & Record Retention`.

---

## 16. Risk Positioning Summary

Key risk themes include:

- Cashout risk.
- Fraud risk.
- Synthetic or fake bill risk.
- Fake or collusive payee risk.
- Chargeback risk.
- Dispute and refund risk.
- AML or suspicious activity risk.
- User deception or misleading communication risk.
- Data privacy risk.
- Sensitive document handling risk.
- Partner rule violation risk.
- Card network rule violation risk.
- Reconciliation failure risk.
- Operational processing error risk.
- Unsupported category expansion risk.
- Poor unit economics risk.

Detailed controls belong in `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`.

Privacy controls belong in `DOC-15 Privacy, Data Protection & Record Retention`.

---

## 17. Partner and Payment Model Summary

PayPlus may require one or more partner types:

- PSP.
- Acquirer.
- Card processor.
- Payment facilitator or sponsored merchant model provider.
- Bank or payout provider.
- Bill payment aggregator.
- OCR/document AI provider.
- KYC/KYB provider.
- Fraud/risk provider.
- Notification provider.
- Cloud infrastructure provider.
- Reconciliation or ledger provider.
- Customer support tooling provider.

Partner selection must consider:

- Supported geographies.
- Supported merchant categories.
- Card network rules.
- Bill payment category support.
- MCC treatment.
- Settlement flows.
- Payout methods.
- Refund and chargeback handling.
- Compliance obligations.
- Data sharing and privacy obligations.
- Security standards.
- SLAs and operational support.
- Fees and reserve requirements.
- Reporting and reconciliation files.
- Contract restrictions.
- Exit and migration risk.

Detailed partner assessment belongs in `DOC-03 Regulatory, PSP & Acquirer Assessment`.

---

## 18. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
|---|---|---|---|
| `ASM-DOC01-001` | Users have demand for card-funded bill payment in at least one launch category. | Product / Commercial | Open |
| `ASM-DOC01-002` | At least one PSP/acquirer model can support the intended card-funded bill payment flow. | Product / Compliance / Payments | Open |
| `ASM-DOC01-003` | Eligible bill categories can be verified with acceptable evidence and operational effort. | Product / Operations / Risk | Open |
| `ASM-DOC01-004` | Payee verification can sufficiently reduce cashout and fraud risk. | Risk / Compliance / Operations | Open |
| `ASM-DOC01-005` | Unit economics can remain positive after card costs, payout costs, support, risk losses, and promotions. | Commercial / Finance | Open |
| `ASM-DOC01-006` | Manual review can support early MVP operations before full automation. | Operations | Open |
| `ASM-DOC01-007` | Users will accept service fees in exchange for card-funded bill payment convenience. | Product / Commercial | Open |
| `ASM-DOC01-008` | Required disclosures can make product behavior clear without increasing regulatory or partner risk. | Legal / Compliance / Product | Open |
| `ASM-DOC01-009` | Bill payment status can be communicated accurately despite partner processing delays. | Product / Operations / Engineering | Open |
| `ASM-DOC01-010` | Partner and payment data can support reliable reconciliation and audit requirements. | Finance / Engineering / Operations | Open |

---

## 19. Constraints

| Constraint ID | Constraint | Impact | Owner |
|---|---|---|---|
| `CON-DOC01-001` | PayPlus must not operate as a wallet or stored-value product unless separately approved. | Limits product architecture and UX. | Product / Compliance |
| `CON-DOC01-002` | PayPlus must not enable unrestricted card-funded cashout. | Requires bill and payee verification. | Risk / Compliance |
| `CON-DOC01-003` | Supported categories must be approved by compliance and payment partners. | Limits category rollout. | Product / Compliance |
| `CON-DOC01-004` | Payout recipients must be verified or approved before payout. | Requires payee verification workflow. | Risk / Operations |
| `CON-DOC01-005` | PSP/acquirer capabilities may limit multi-card payments, payout timing, refunds, and chargebacks. | May constrain MVP scope. | Payments / Engineering |
| `CON-DOC01-006` | Card network, partner, and regulatory requirements may restrict certain categories. | Requires category-by-category assessment. | Compliance |
| `CON-DOC01-007` | Sensitive documents and personal data must be handled under approved privacy controls. | Requires data handling and retention controls. | Privacy / Security |
| `CON-DOC01-008` | Transaction records must support audit and reconciliation. | Requires ledger and reporting design. | Finance / Engineering |
| `CON-DOC01-009` | User-facing claims must not misrepresent product capabilities, timing, guarantees, or legal status. | Requires content review. | Product / Legal / Compliance |
| `CON-DOC01-010` | MVP scope must remain operationally reviewable with available staffing. | Limits launch volume and category breadth. | Operations |

---

## 20. Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
|---|---|---|---|---|
| `DEP-DOC01-001` | PSP/acquirer feasibility assessment. | Card payment acceptance. | Payments / Compliance | Open |
| `DEP-DOC01-002` | Payout provider or settlement partner selection. | Payee payment execution. | Payments / Operations | Open |
| `DEP-DOC01-003` | Regulatory assessment by launch jurisdiction. | Product launch approval. | Legal / Compliance | Open |
| `DEP-DOC01-004` | Bill category approval framework. | Category rollout. | Product / Risk / Compliance | Open |
| `DEP-DOC01-005` | Payee verification process. | Anti-cashout control. | Risk / Operations | Open |
| `DEP-DOC01-006` | Privacy and data retention model. | Bill document handling. | Privacy / Security | Open |
| `DEP-DOC01-007` | Risk rules and manual review workflow. | MVP launch controls. | Risk / Operations | Open |
| `DEP-DOC01-008` | Reconciliation and transaction ledger model. | Finance and audit readiness. | Finance / Engineering | Open |
| `DEP-DOC01-009` | Content and disclosure approval. | User-facing launch. | Product / Legal / Compliance | Open |
| `DEP-DOC01-010` | Customer support and incident workflow. | Operational readiness. | Operations / Support | Open |

---

## 21. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
|---|---|---|---|---|---|
| `RISK-DOC01-001` | Product is perceived or used as card-to-cash cashout. | Regulatory, partner, fraud, and financial loss risk. | Strong bill verification, payee verification, limits, monitoring, and communication controls. | Risk / Compliance | Open |
| `RISK-DOC01-002` | Unsupported legal or money transmission classification. | Launch delay, enforcement, partner rejection, or licensing requirement. | Jurisdiction and partner assessment before launch. | Legal / Compliance | Open |
| `RISK-DOC01-003` | PSP/acquirer rejects business model or category. | Product cannot process payments as designed. | Early partner due diligence and category review. | Payments / Commercial | Open |
| `RISK-DOC01-004` | Fake bills or collusive payees are used for abuse. | Fraud losses and cashout risk. | Bill evidence validation, payee verification, velocity limits, and manual review. | Risk / Operations | Open |
| `RISK-DOC01-005` | Chargeback or refund process creates financial loss. | Revenue leakage, disputes, and operational burden. | Define refund, chargeback, and evidence handling rules. | Payments / Risk / Operations | Open |
| `RISK-DOC01-006` | Multi-card funding increases complexity or partner risk. | Delayed MVP or higher reconciliation risk. | Consider deferring multi-card to post-MVP unless clearly supported. | Product / Engineering / Payments | Open |
| `RISK-DOC01-007` | User disclosures are unclear or misleading. | User complaints, regulatory risk, and chargebacks. | Content and legal review before launch. | Product / Legal | Open |
| `RISK-DOC01-008` | Unit economics are negative after full cost allocation. | Unsustainable business model. | Model costs and minimum fee thresholds in `DOC-02`. | Commercial / Finance | Open |
| `RISK-DOC01-009` | Manual review operations do not scale. | Delays, errors, user dissatisfaction. | Limit MVP volume and automate high-confidence checks over time. | Operations / Product | Open |
| `RISK-DOC01-010` | Sensitive bill documents are mishandled. | Privacy, security, and reputation risk. | Apply privacy, security, access, retention, and deletion controls. | Privacy / Security | Open |

---

## 22. Launch Readiness Themes

PayPlus should not launch until the following themes are sufficiently addressed:

- Product scope is approved.
- Launch categories are approved.
- Product positioning is approved.
- PSP/acquirer model is approved.
- Payout or settlement model is approved.
- Compliance assessment is completed for launch jurisdiction.
- Risk and anti-cashout controls are defined.
- Bill and payee verification process is defined.
- Privacy and data retention controls are defined.
- Security model is defined.
- Payment, payout, refund, and reconciliation workflows are defined.
- User disclosures are approved.
- Customer support and incident workflows are defined.
- MVP test cases and UAT results are acceptable.
- Operational owners are assigned.
- Evidence retention and audit trail requirements are defined.

Detailed launch gates belong in `DOC-04 Compliance Certification Roadmap & Control Framework` and `DOC-20 Testing, UAT, Release & Go-Live Checklist`.

---

## 23. Success Metrics

Candidate success metrics may include:

| Metric | Description |
|---|---|
| Activated users | Users who complete registration and become eligible to submit bill payments. |
| Submitted bill payment requests | Number of bill payment requests created. |
| Approved bill payment requests | Number and percentage of requests approved after verification. |
| Completed payments | Number and value of successfully funded and paid bills. |
| Payment success rate | Percentage of card payments successfully authorized and captured. |
| Payout success rate | Percentage of payouts successfully completed to approved payees. |
| Average processing time | Time from request submission to payout completion. |
| Manual review rate | Percentage of transactions requiring manual review. |
| Rejection rate | Percentage of requests rejected due to invalid bill, unsupported category, payee issue, or risk issue. |
| Refund and cancellation rate | Percentage of transactions refunded or cancelled. |
| Chargeback rate | Percentage of funded transactions disputed or charged back. |
| Fraud loss rate | Fraud losses as a percentage of processed volume. |
| Contribution margin | Revenue after variable payment, payout, promotion, risk, support, and operations costs. |
| User complaint rate | Complaints per transaction or user. |
| Repeat usage rate | Percentage of users who submit more than one approved bill payment. |

Metric definitions should be finalized in `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 24. Downstream Document Impact

`DOC-01` should guide downstream documents as follows:

| Downstream Document | Impact |
|---|---|
| `DOC-02` | Validate service fee, partner fee, promotion, and unit economics assumptions. |
| `DOC-03` | Assess regulatory, PSP, acquirer, category, payment rail, and payee feasibility. |
| `DOC-04` | Define launch gates, compliance controls, evidence, and approval workflow. |
| `DOC-05` | Convert candidate capabilities into prioritized PRD requirements. |
| `DOC-06` | Define end-to-end user, admin, and service blueprint flows. |
| `DOC-07` | Define allowed and prohibited product language and disclosures. |
| `DOC-08` | Define lifecycle notifications and receipt language. |
| `DOC-09` | Define payment request, card funding, multi-source, settlement readiness, and payment state behavior. |
| `DOC-10` | Define payout execution and reconciliation rules. |
| `DOC-11` | Define cancellation, refund, dispute, chargeback, and reversal rules. |
| `DOC-12` | Define bill category eligibility, document AI/OCR, evidence validation, and payee verification. |
| `DOC-13` | Define promotion eligibility, reward handling, campaign rules, and funded offers. |
| `DOC-14` | Define AML, anti-cashout, fraud, velocity, manual review, and risk controls. |
| `DOC-15` | Define privacy, sensitive document handling, retention, deletion, and data rights. |
| `DOC-16` | Define technical architecture aligned to product boundaries and controls. |
| `DOC-17` | Define API and third-party integration requirements. |
| `DOC-18` | Define data model, ledger, reporting, audit trail, and metric definitions. |
| `DOC-19` | Define security, tokenization, authentication, encryption, and access control requirements. |
| `DOC-20` | Define test coverage, UAT, launch checklist, and release readiness. |
| `DOC-21` | Define monitoring, support, incident response, and operational runbook. |

---

## 25. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC01-001` | What is the initial launch country or jurisdiction? | Project Owner | Critical | Open |
| `OQ-DOC01-002` | Which bill categories are approved for MVP? | Product / Compliance / Risk | Critical | Open |
| `OQ-DOC01-003` | Which PSP/acquirer model will be used? | Payments / Commercial | Critical | Open |
| `OQ-DOC01-004` | Which payout or settlement partner will be used? | Payments / Operations | Critical | Open |
| `OQ-DOC01-005` | Will MVP support multi-card split payments, or defer them? | Product / Payments / Engineering | High | Open |
| `OQ-DOC01-006` | What KYC/KYB level is required for users, payees, and business users? | Legal / Compliance / Risk | High | Open |
| `OQ-DOC01-007` | What transaction limits should apply at MVP? | Risk / Compliance / Product | High | Open |
| `OQ-DOC01-008` | What service fee model will be used? | Commercial / Finance | High | Open |
| `OQ-DOC01-009` | What user disclosures are required before payment confirmation? | Product / Legal / Compliance | High | Open |
| `OQ-DOC01-010` | What evidence must be retained for each transaction? | Compliance / Privacy / Operations | High | Open |
| `OQ-DOC01-011` | Which product claims are prohibited in marketing and user communication? | Product / Legal / Compliance | Medium | Open |
| `OQ-DOC01-012` | What operational SLA should apply to bill review and payout execution? | Operations / Product | Medium | Open |

---

## 26. Acceptance Criteria

`DOC-01` is acceptable when it clearly defines:

- PayPlus product summary.
- Product intent.
- Product positioning.
- Product problem statement.
- Target users.
- Candidate bill categories.
- Product boundaries.
- In-scope and out-of-scope capabilities.
- Candidate MVP scope.
- Candidate MVP categories.
- Non-MVP or future scope.
- Key business objectives.
- Product principles.
- High-level transaction lifecycle.
- Commercial model summary.
- Compliance and regulatory positioning summary.
- Risk positioning summary.
- Partner and payment model summary.
- Assumptions.
- Constraints.
- Dependencies.
- Risks.
- Launch readiness themes.
- Candidate success metrics.
- Downstream document impact.
- Open questions.

This document should remain a foundation charter and should not become a detailed PRD, legal memo, payment specification, risk policy, or technical architecture.

---

## 27. Version History

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-01` Project Charter & Product Positioning. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Reframed as foundation charter, clarified product positioning, added product boundaries, candidate MVP scope, assumptions, constraints, dependencies, risks, launch readiness themes, downstream document impact, and standardized metadata and version history. |
