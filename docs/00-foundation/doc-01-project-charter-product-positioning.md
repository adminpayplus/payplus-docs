---
document_id: DOC-01
title: Project Charter & Product Positioning
version: 0.3.0
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
last_updated: 2026-05-27
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

Version `0.3.0` updates the charter to recognize that PayPlus may support both:

1. payer-created bill payment requests; and
2. payee-created bill, invoice, fee, or rent payment requests,

provided that payee-created requests are created only by onboarded or approved payees, are backed by required evidence, remain subject to category and risk controls, and require explicit payer review and authorization before payment.

---

## 2. Product Summary

PayPlus is intended to be a controlled card-funded bill payment platform.

The product is designed to let eligible users pay eligible real-world bills by card, while PayPlus or its payment partners route payment value to approved payees through supported settlement or payout methods.

PayPlus may support two controlled request creation models:

1. **Payer-created payment request**
   - A payer submits a bill payment request.
   - The payer provides bill evidence or structured bill details.
   - PayPlus verifies bill eligibility and payee validity.
   - The payer authorizes and funds the payment through a supported card funding source.
   - PayPlus or its payment partner settles, transfers, or pays the approved biller, payee, or receiving account.

2. **Payee-created payment request**
   - An onboarded or approved payee, such as a landlord, school, utility provider, biller, or service provider, creates a bill, invoice, fee, rent, or other approved payment obligation request.
   - The payee provides required evidence, such as an invoice, bill statement, tenancy contract, lease agreement, service agreement, or equivalent approved document.
   - The payee sends or pushes the request to the payer through an approved PayPlus flow.
   - The payer reviews the request, payee, amount, supporting evidence where applicable, service fee, total charge, timing, refund/cancellation terms, and PayPlus role.
   - The payer must explicitly accept required disclosures and authorize payment before PayPlus initiates funding or payout.
   - PayPlus verifies request eligibility, payee status, evidence, risk conditions, funding, payout readiness, reconciliation, and audit requirements.

The intended product model is:

1. A payer or approved payee creates a bill/payment request.
2. The request is tied to a valid bill, invoice, fee, rent obligation, or approved payment obligation.
3. Required evidence is provided by the request creator or otherwise captured through approved flows.
4. PayPlus verifies bill or obligation eligibility and payee validity.
5. The payer reviews the request and required disclosures.
6. The payer authorizes payment using a supported card funding source.
7. PayPlus or its payment partner collects the card payment.
8. PayPlus or its payment partner settles, transfers, or pays the approved biller, payee, or receiving account.
9. PayPlus records the transaction, reconciliation status, audit trail, receipt, and any applicable service fee or promotion.

PayPlus should not be positioned as a general wallet, stored-value account, remittance service, cash withdrawal service, peer-to-peer transfer app, open invoice marketplace, or payroll product unless separately assessed, approved, and documented.

---

## 3. Product Intent

The intended product intent is to help users pay valid bills or approved payment obligations using card funding sources in a controlled, compliant, and auditable way.

The core product goals are:

- Enable card-funded bill payments for eligible bill categories.
- Improve user convenience where billers or payees do not directly accept cards.
- Allow onboarded or approved payees to create valid bill, invoice, fee, or rent payment requests where approved.
- Ensure payee-created requests are backed by required evidence and do not bypass payer review or authorization.
- Support multi-card or multi-funding-source payment behavior where commercially, technically, and compliance-feasible.
- Provide transparent pricing and disclosures.
- Maintain strong anti-cashout and fraud controls.
- Maintain bill verification and payee validation controls.
- Maintain transaction traceability from request creation through card funding, payout, settlement, reconciliation, and receipt.
- Maintain auditable evidence for compliance, risk, reconciliation, user support, and partner review.

---

## 4. Product Positioning

PayPlus should be positioned as:

> A controlled card-funded bill payment service that enables eligible users to pay eligible verified bills or approved payment obligations through approved payment rails.

Where payee-created requests are approved, PayPlus may also be positioned as:

> A controlled payment request and bill payment service that allows approved payees to request payment for eligible verified bills or obligations, while the payer remains in control of payment authorization.

PayPlus may use positioning language such as:

- Card-funded bill payment.
- Bill payment facilitation.
- Pay eligible bills by card.
- Receive and pay eligible bill requests from approved payees.
- Approved payees can request payment for eligible bills, invoices, fees, or rent obligations.
- Pay rent or approved fees by card where supported and verified.
- Split or combine eligible card payments for an approved bill, where supported.
- Pay approved billers, merchants, landlords, service providers, or payees through PayPlus-supported payout or settlement methods.
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
- Create invoices to get cash from cards.
- Request money from anyone for any reason.
- Instant rent cashout.
- Pay yourself by card.
- Turn invoices into cash.
- Open invoice marketplace.
- Auto-charge tenants or payers without authorization.

Final public language must be reviewed in `DOC-07 Content, Disclosure & User Communication`.

---

## 5. Product Problem Statement

Many users may want to pay bills using card funding sources for convenience, liquidity management, rewards, recordkeeping, or payment flexibility.

However, not all billers accept cards directly.

Some bill payments may require bank transfer, biller portal payment, account transfer, or other payout methods.

Additionally, some legitimate payees, such as landlords, schools, service providers, property managers, utilities, or billers, may need a controlled way to request payment for valid bills, invoices, rent, or fees while still allowing the payer to review the request and choose whether to authorize card-funded payment.

PayPlus aims to bridge this gap by allowing eligible users to fund a verified bill payment by card while ensuring that payment value is routed only toward approved bill obligations and not misused for cashout, unauthorized transfer, unsupported invoicing, or unrestricted money movement.

---

## 6. Target Users

Candidate target users may include:

- Individuals who need to pay eligible household bills.
- Individuals who want to use card funding for bill payments where direct card acceptance is unavailable or inconvenient.
- Users who receive eligible payment requests from approved payees.
- Tenants or residents who receive approved rent or property-related payment requests from onboarded landlords or property managers, where rent is approved.
- Users who want receipts, tracking, and consolidated payment history.
- Users who want to split a large eligible bill across more than one supported funding source, if supported.
- Users eligible for promotions, rewards, or partner-funded offers, if available.
- Approved payees who receive payouts for eligible bills or payment obligations.
- Approved landlords, property managers, schools, billers, utilities, or service providers that may create payment requests where the feature is approved.

The final target user definition must be validated in the Master PRD and market research artifacts.

---

## 7. Candidate Bill Categories

Candidate bill categories may include:

| Category | Example Use Cases | Notes |
|---|---|---|
| Utilities | Electricity, water, gas, internet, mobile, telecom | Usually strong bill evidence and payee traceability. May support payer-created or approved biller-created requests if enabled. |
| Rent or property-related payments | Rent, property management fees, maintenance charges | Higher risk; may require landlord onboarding, tenancy contract or lease evidence, payer-landlord relationship validation, stronger payee verification, and anti-cashout controls. |
| Education | Tuition, school fees, course fees | May require institution validation. Approved schools may create fee requests if enabled. |
| Insurance | Health, auto, property, life insurance premiums | May require biller and policy validation. |
| Taxes and government fees | Taxes, fines, permit fees, public authority payments | Must be assessed for legal and partner feasibility. |
| Healthcare | Clinic, hospital, medical bills | Privacy and sensitive data handling considerations. |
| Loan or financing payments | Installments, financing obligations | May be restricted by partner, card network, or regulatory rules. |
| Business invoices | Supplier invoices, service invoices | May require business KYB, invoice validation, payer acceptance, dispute workflow, and category controls. |

Candidate categories are not automatically approved.

Each category must be assessed through:

- `DOC-03 Regulatory, PSP & Acquirer Assessment`.
- `DOC-12 Bill Category, Document AI/OCR & Payee Verification`.
- `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`.
- Applicable partner, card network, acquirer, and regulatory requirements.

Payee-created request support must be assessed separately from payer-created request support for each category.

---

## 8. Product Boundaries

### 8.1 In-Scope Product Capabilities

The following capabilities are candidates for PayPlus scope, subject to downstream approval:

- User registration and authentication.
- User profile and eligibility checks.
- Payee onboarding and payee profile creation.
- Payee type assignment and capability permissioning.
- Bill upload or bill detail entry.
- Bill, invoice, fee, or rent request creation by payer.
- Bill, invoice, fee, or rent request creation by approved payee, where enabled.
- Payee request push, invitation, or delivery to payer through approved channels.
- Payer review, acceptance, rejection, query, or dispute of payee-created requests.
- Bill document capture, OCR, or structured data extraction.
- Evidence capture for bills, invoices, tenancy contracts, lease agreements, service agreements, or equivalent approved documents.
- Bill category classification.
- Payee validation.
- Landlord, biller, school, service provider, or business payee verification where applicable.
- Bill eligibility checks.
- Payment quote and service fee calculation.
- Card payment authorization and capture.
- Multi-card or multi-source funding for one approved bill, where supported.
- Payment status tracking.
- Request status tracking for payer and payee.
- Payout or settlement to approved payees.
- Transaction receipt generation.
- User and payee notifications.
- Refund, cancellation, rejection, query, dispute, reversal, and exception handling.
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
- Payee-created requests by unverified, blocked, restricted, or ineligible payees.
- Automatic payer charging based on a payee-created request without explicit payer authorization.
- Open invoice or money-request marketplace.
- Payee-created requests for unsupported, fake, inflated, circular, self-dealing, or collusive obligations.
- Landlord-created rent requests without approved landlord onboarding and required tenancy or lease evidence where rent evidence is required.
- Payee modification of material request terms after payer authorization without renewed payer review and authorization.

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
- If payee-created requests are included, require approved payee onboarding, payer acceptance, payer authorization, evidence parity, relationship risk controls, and support workflows.

### 9.1 Candidate MVP Features

Candidate MVP features may include:

| Feature | Candidate MVP Treatment |
|---|---|
| User registration | In scope. |
| User authentication | In scope. |
| Basic user profile | In scope. |
| KYC/KYB | To be determined based on jurisdiction, partner model, bill category, payee type, and risk assessment. |
| Payee onboarding | Gated MVP scope; required if payee-created requests are enabled. |
| Payee capability permissioning | Gated MVP scope; required if payee-created requests are enabled. |
| Bill upload | In scope. |
| Manual bill data entry | In scope with validation. |
| Payee-created bill/invoice/fee/rent request creation | Gated MVP or pilot scope; disabled unless explicitly approved. |
| Payee request push/invitation to payer | Gated MVP or pilot scope; requires privacy and notification controls. |
| Payer review and acceptance of payee-created request | P0 if payee-created requests are enabled. |
| OCR/document AI | Optional for MVP; may begin as assisted or back-office workflow. |
| Bill category eligibility | In scope. |
| Payee verification | In scope. |
| Landlord verification | Required if rent requests are enabled. |
| Tenancy/lease evidence capture | Required if landlord-created rent requests are enabled. |
| Card payment | In scope through approved PSP/acquirer. |
| Multi-card split payment | Candidate feature; may be deferred if complexity or partner risk is high. |
| Payment quote and fee disclosure | In scope. |
| Payout to payee | In scope through approved payout method. |
| User receipt | In scope. |
| Notifications | In scope for key lifecycle events. |
| Refund/cancellation | In scope at minimum viable process level. |
| Payer rejection/query/dispute of payee-created request | Required if payee-created requests are enabled. |
| Promotion engine | Optional; should not block MVP unless commercially required. |
| Partner advertisements | Out of initial MVP unless separately approved. |
| Admin review console | In scope for manual review and operations. |
| Payee request/admin console | Required if payee-created requests are enabled. |
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
- Whether request creation is payer-created only or also payee-created.

Preferred MVP candidates may include:

- Utilities.
- Telecom or internet bills.
- Education fees.
- Insurance premiums.

Higher-risk categories such as rent, business invoices, loan repayment, or tax payments may require additional controls and may be deferred until later phases.

If rent is included, especially landlord-created rent requests, additional controls should be expected, including landlord onboarding, tenancy or lease evidence, payer-landlord relationship validation, anti-collusion controls, duplicate rent request detection, and manual review for higher-risk cases.

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
- Payee request portal.
- Landlord rent request portal.
- Open payee onboarding for approved categories.
- Automated payout routing.
- Enhanced reconciliation automation.
- Advanced reporting.
- Business user support.
- Multi-user or delegated account access.
- API access for partners.
- Payee-created request APIs.
- Recurring payee-created rent or invoice requests, only with approved authorization, cancellation, evidence, and risk controls.
- Partner advertisement modules.
- Loyalty or reward integrations.

Future scope must not be implemented until feasibility, compliance, risk, commercial, technical, and operational requirements are defined and approved.

---

## 11. Key Business Objectives

The key business objectives for PayPlus are:

- Build a compliant and trusted bill payment service.
- Enable card-funded bill payment in categories where users value payment flexibility.
- Support controlled payment request creation by approved payees where it improves bill payment completion and user convenience.
- Create a sustainable service-fee, payee-funded, biller-funded, or partner-funded revenue model.
- Maintain positive unit economics after card processing, payout, risk, refunds, operations, onboarding, verification, and support costs.
- Avoid unsupported wallet, cashout, remittance, and money-transfer positioning.
- Build scalable bill verification, payee onboarding, risk review, and reconciliation processes.
- Support future growth into new categories, partners, payee types, and jurisdictions.

Detailed commercial assumptions belong in `DOC-02 Business Model & Unit Economics`.

---

## 12. Product Principles

PayPlus should follow these product principles:

| Principle | Meaning |
|---|---|
| Verified bill first | Payment should be tied to a valid bill or eligible payment obligation. |
| Approved payee only | Payout should go only to a verified and approved payee or biller. |
| Payer authorization required | No payee-created request should result in funding or payout without explicit payer authorization. |
| Evidence parity | Payee-created requests should meet the same evidence standard as payer-created requests. |
| Request-origin clarity | Product should clearly identify whether a request was payer-created, payee-created, admin-created, or system-created. |
| Permissioned payee capability | Payees should only create request types and categories they are approved to create. |
| No unrestricted cashout | The product should not enable card-funded cash withdrawal or unrestricted transfer. |
| Transparent pricing | Users should see service fees and total cost before payment confirmation. |
| Traceable lifecycle | Each transaction should be traceable from request through funding, payout, reconciliation, and receipt. |
| Risk-based controls | Higher-risk categories or behaviors should trigger stronger review and limits. |
| Compliance by design | Compliance, privacy, risk, and partner constraints should shape product behavior. |
| Operationally reviewable | Staff should be able to review exceptions, evidence, and transaction history. |
| Scalable automation | Manual controls may be used early, but should be designed for future automation. |
| Clear user communication | Users should receive clear, accurate, non-misleading status and receipt information. |
| Privacy-bound visibility | Payers and payees should only see information appropriate to their role and authorization level. |

---

## 13. High-Level Transaction Lifecycle

PayPlus may support two high-level transaction lifecycle models.

### 13.1 Payer-Created Request Lifecycle

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

### 13.2 Payee-Created Request Lifecycle

1. Payee signs in or is onboarded through an approved process.
2. Payee completes required onboarding, verification, payout, and eligibility checks.
3. Approved payee creates a bill, invoice, fee, rent, or approved payment obligation request.
4. Payee provides required details and evidence.
5. PayPlus validates payee permissions, category eligibility, evidence sufficiency, amount limits, payer identification, and risk rules.
6. Request is sent to payer, routed to manual review, rejected, or returned to payee for more information.
7. Payer receives a notification or invitation to review the request.
8. Payer reviews request origin, payee identity, amount, evidence information where applicable, service fee, total charge, timing, refund/cancellation rules, and PayPlus role.
9. Payer accepts and authorizes payment, rejects the request, raises a query, disputes the request, or lets the request expire.
10. If payer authorizes payment, payer pays by supported card funding source.
11. PSP/acquirer authorizes and captures the card payment.
12. PayPlus records funding status.
13. PayPlus performs final risk, compliance, and payout readiness checks.
14. PayPlus or partner initiates payout or settlement to approved payee.
15. PayPlus monitors payout status.
16. PayPlus reconciles funding, fees, payout, and exceptions.
17. Payer and payee receive appropriate confirmation, receipt, status, or payout updates.
18. Records are retained according to approved retention rules.

Detailed state machines and payment lifecycle rules belong in:

- `DOC-09 Payment Request, Multi-Funding Source & Settlement`.
- `DOC-10 Payout & Reconciliation`.
- `DOC-11 Refund, Cancellation & Chargeback`.

---

## 14. Commercial Model Summary

The candidate commercial model may include:

- User-paid service fees.
- Payee-paid request, onboarding, platform, subscription, or payout fees, if approved.
- Biller-paid or partner-paid fees.
- Campaign-funded subsidies.
- Partner-funded promotions.
- Advertisement or sponsored placement revenue, if later approved.
- Revenue share with billers, PSPs, payees, or partners, if commercially and legally feasible.

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
- Payee onboarding and verification costs.
- Payee support costs.
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
- PayPlus may support payer-created and approved payee-created payment requests only where the model is assessed and approved.
- PayPlus should avoid stored-value or wallet behavior unless separately approved.
- PayPlus should avoid unrestricted money transmission behavior unless licensed, exempt, sponsored, or otherwise approved.
- PayPlus should not enable cashout from card funding sources.
- PayPlus should maintain evidence that funded payments correspond to valid bills or obligations.
- PayPlus should maintain evidence that payee-created requests correspond to valid bills, invoices, rent, fees, or approved obligations.
- PayPlus should maintain evidence that payout recipients are approved payees.
- PayPlus should require payer authorization before payment on payee-created requests.
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
- Fake invoice or fake rent request risk.
- Fake or collusive payee risk.
- Landlord-tenant collusion risk.
- Self-payment or related-party abuse risk.
- Payee-created request spam or harassment risk.
- Payee modification of material terms after payer authorization.
- Chargeback risk.
- Dispute and refund risk.
- AML or suspicious activity risk.
- User deception or misleading communication risk.
- Payer confusion regarding payee-created requests.
- Payee access to sensitive payer information.
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
- Payee onboarding provider.
- Landlord, property manager, biller, school, utility, or service provider verification source.
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
- Payee-created request support.
- Landlord, invoice, or biller request model support.
- Whether onboarded payees are treated as merchants, sub-merchants, billers, agents, beneficiaries, or other role classifications.
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
| `ASM-DOC01-011` | Payee-created payment requests can be supported without converting PayPlus into an unrestricted money request, cashout, wallet, or remittance product. | Product / Legal / Compliance | Open |
| `ASM-DOC01-012` | Approved payees can provide sufficient evidence for created requests, including tenancy or lease evidence for rent where required. | Product / Risk / Operations | Open |
| `ASM-DOC01-013` | Payers will understand and accept payee-created requests only after clear review, disclosure, and authorization flow. | Product / Design / Legal | Open |
| `ASM-DOC01-014` | Payee onboarding and verification can be operationally supported within MVP or pilot staffing if the feature is enabled. | Operations / Risk | Open |

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
| `CON-DOC01-011` | Payee-created request capability must be disabled unless approved payee onboarding, evidence, risk, payout, privacy, support, and reconciliation controls are in place. | Requires feature gating and launch control. | Product / Compliance / Risk |
| `CON-DOC01-012` | Payee-created requests must not charge or bind the payer without explicit payer authorization. | Requires payer acceptance and authorization controls. | Product / Legal / Payments |
| `CON-DOC01-013` | Payees must not be able to create unsupported, fake, inflated, circular, self-dealing, or collusive requests. | Requires payee permissioning, evidence controls, risk monitoring, and manual review. | Risk / Compliance |
| `CON-DOC01-014` | Landlord-created rent requests require approved landlord onboarding and tenancy or lease evidence where rent is enabled. | Requires rent-specific onboarding, evidence, and risk controls. | Product / Risk / Operations |

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
| `DEP-DOC01-011` | Payee onboarding and capability model. | Payee-created requests and payee payout. | Product / Compliance / Risk | Open |
| `DEP-DOC01-012` | Payee type taxonomy. | Determine which payees can create which request types. | Product / Risk / Operations | Open |
| `DEP-DOC01-013` | Landlord/rent verification standard. | Landlord-created rent requests. | Product / Legal / Risk | Open |
| `DEP-DOC01-014` | Payer identification and invitation mechanism. | Payee-created request delivery to payer. | Product / Engineering / Privacy | Open |
| `DEP-DOC01-015` | Payer response and pre-authorization dispute workflow. | Payee-created request acceptance, rejection, query, and dispute. | Product / Operations / Legal | Open |

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
| `RISK-DOC01-011` | Payee-created requests are used to generate fake, inflated, circular, or collusive payment obligations. | Fraud, cashout, regulatory risk, chargebacks, and financial loss. | Payee onboarding, evidence requirements, payer authorization, relationship checks, and manual review. | Risk / Compliance | Open |
| `RISK-DOC01-012` | Landlord-created rent requests are used for self-payment or disguised cashout. | High cashout, fraud, and partner risk. | Landlord verification, tenancy evidence, payer-payee relationship checks, limits, and manual review. | Risk / Operations | Open |
| `RISK-DOC01-013` | Payer misunderstands payee-created request as mandatory, already paid, or automatically charged. | Complaints, disputes, trust loss, and potential consumer protection risk. | Clear request-origin messaging, explicit payer acceptance, and no auto-charge behavior. | Product / Legal | Open |
| `RISK-DOC01-014` | Payee sees sensitive payer payment, card, or risk information. | Privacy, security, and trust risk. | Role-based access, data minimization, and payee-safe status messaging. | Privacy / Security | Open |
| `RISK-DOC01-015` | Payee-created request workflow increases operational review load beyond MVP capacity. | Delays, review errors, and launch readiness risk. | Feature gating, controlled payee onboarding, volume limits, and operational queue design. | Operations / Product | Open |

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
- Payee onboarding and capability controls are defined if payee-created requests are enabled.
- Payer acceptance and authorization flow is defined if payee-created requests are enabled.
- Rent evidence and landlord verification controls are defined if landlord-created rent requests are enabled.
- Privacy and data retention controls are defined.
- Payer/payee data visibility boundaries are defined if payee-created requests are enabled.
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
| Activated users | Users who complete registration and become eligible to submit or pay bill payments. |
| Onboarded payees | Payees that complete onboarding and are approved to receive payouts or create requests where enabled. |
| Submitted bill payment requests | Number of bill payment requests created. |
| Payer-created requests | Number of payment requests created by payers. |
| Payee-created requests | Number of payment requests created by approved payees. |
| Payee request delivery rate | Percentage of payee-created requests successfully delivered to intended payer. |
| Payee request acceptance rate | Percentage of payee-created requests accepted by payers. |
| Payee request rejection/query/dispute rate | Percentage of payee-created requests rejected, queried, or disputed before authorization. |
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
| Payee-created request abuse rate | Rate of requests flagged for fake invoice, fake rent, duplicate, collusive, or spam behavior. |
| Contribution margin | Revenue after variable payment, payout, promotion, risk, support, onboarding, verification, and operations costs. |
| User complaint rate | Complaints per transaction or user. |
| Payee complaint rate | Complaints per onboarded payee or payee-created request. |
| Repeat usage rate | Percentage of users who submit or pay more than one approved bill payment. |

Metric definitions should be finalized in `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 24. Downstream Document Impact

`DOC-01` should guide downstream documents as follows:

| Downstream Document | Impact |
|---|---|
| `DOC-02` | Validate service fee, payee fee, partner fee, promotion, onboarding, verification, support, and unit economics assumptions. |
| `DOC-03` | Assess regulatory, PSP, acquirer, category, payment rail, payee feasibility, payee-created request model, landlord/biller role, and request creator implications. |
| `DOC-04` | Define launch gates, compliance controls, payee onboarding controls, payer authorization controls, evidence, and approval workflow. |
| `DOC-05` | Convert candidate capabilities into prioritized PRD requirements, including payer-created and payee-created request models. |
| `DOC-06` | Define end-to-end payer, payee, admin, and service blueprint flows. |
| `DOC-07` | Define allowed and prohibited product language, request-origin language, payee-created request disclosures, and payer authorization disclosures. |
| `DOC-08` | Define lifecycle notifications, request invitation messages, payer/payee status messaging, and receipt language. |
| `DOC-09` | Define payment request, request creator type, payer acceptance, card funding, multi-source, settlement readiness, and payment state behavior. |
| `DOC-10` | Define payout execution, payee payout status, and reconciliation rules. |
| `DOC-11` | Define cancellation, request withdrawal, payer rejection, query, refund, dispute, chargeback, and reversal rules. |
| `DOC-12` | Define bill category eligibility, document AI/OCR, evidence validation, rent evidence, invoice evidence, payee onboarding, landlord verification, and payee verification. |
| `DOC-13` | Define promotion eligibility, reward handling, campaign rules, funded offers, and payer/payee promotion cost allocation if applicable. |
| `DOC-14` | Define AML, anti-cashout, fraud, velocity, payee-created request abuse, payer-payee relationship risk, manual review, and risk controls. |
| `DOC-15` | Define privacy, payer/payee data visibility, sensitive document handling, retention, deletion, and data rights. |
| `DOC-16` | Define technical architecture aligned to product boundaries and controls, including payee request capability if enabled. |
| `DOC-17` | Define API and third-party integration requirements, including payee request APIs if enabled. |
| `DOC-18` | Define data model, request creator type, payee-created request object, ledger, reporting, audit trail, and metric definitions. |
| `DOC-19` | Define security, tokenization, authentication, encryption, access control, and payer/payee RBAC requirements. |
| `DOC-20` | Define test coverage, UAT, launch checklist, and release readiness for payer-created and payee-created flows if enabled. |
| `DOC-21` | Define monitoring, support, payee onboarding operations, incident response, and operational runbook. |

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
| `OQ-DOC01-013` | Are payee-created payment requests included in MVP, pilot, or post-MVP scope? | Project Owner / Product / Compliance | Critical | Open |
| `OQ-DOC01-014` | Which payee types can be onboarded to create payment requests? | Product / Risk / Compliance | Critical | Open |
| `OQ-DOC01-015` | Is landlord-created rent request creation included in MVP or deferred? | Product / Legal / Risk | Critical | Open |
| `OQ-DOC01-016` | What evidence is required for landlord-created rent requests? | Product / Legal / Risk / Operations | Critical | Open |
| `OQ-DOC01-017` | What payee onboarding checks are required for individuals, landlords, businesses, schools, utilities, or service providers? | Compliance / Risk / Operations | Critical | Open |
| `OQ-DOC01-018` | How will a payee identify or invite a payer? | Product / Engineering / Privacy | High | Open |
| `OQ-DOC01-019` | What payer response options are supported for payee-created requests? | Product / Operations / Legal | High | Open |
| `OQ-DOC01-020` | What information from a payee-created request can be shown to the payer, and what information can be shown to the payee? | Product / Privacy / Security | High | Open |
| `OQ-DOC01-021` | What dispute or query process applies before payer authorization? | Product / Operations / Legal | High | Open |
| `OQ-DOC01-022` | What monitoring is required to detect fake invoices, fake rent requests, related-party abuse, and payee-created request spam? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC01-023` | Are payees charged any onboarding, subscription, invoice, payout, platform, or transaction fees? | Commercial / Finance / Product | Medium | Open |
| `OQ-DOC01-024` | Are recurring payee-created rent or invoice requests allowed, or must each request be individually created and authorized? | Product / Legal / Payments | High | Open |

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
- Payer-created request model.
- Payee-created request model, if enabled.
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
| `0.3.0` | `2026-05-27` | Product Documentation Team | Updated charter to include controlled payee-created bill, invoice, fee, and rent payment request capability. Added payee onboarding, payer acceptance and authorization, evidence parity, landlord/rent evidence controls, request-origin positioning, additional risks, dependencies, success metrics, launch readiness themes, and downstream document impacts aligned to `DOC-05 v0.2.0`. |
