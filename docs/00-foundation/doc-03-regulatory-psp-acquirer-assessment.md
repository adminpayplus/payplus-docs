---
document_id: DOC-03
title: Regulatory, PSP & Acquirer Assessment
version: 0.3.0
status: Draft
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
last_updated: 2026-05-27
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

# DOC-03 — Regulatory, PSP & Acquirer Assessment

## 0. Revision Note — Version 0.3.0

This version updates `DOC-03` to reflect the `DOC-05 v0.2.0` product capability where approved payees may be onboarded to PayPlus and may create bill, invoice, fee, or rent payment requests for eligible payers.

This amendment expands the assessment framework to cover:

- Payee onboarding regulatory and partner implications.
- Payee-created bill, invoice, fee, and rent payment requests.
- Payer review, acceptance, rejection, query, dispute, and authorization before payment.
- Request creator type as an assessment dimension.
- Payee type and payee capability permissions.
- Landlord-created rent request risks and evidence requirements.
- Invoice and business-payee request risks.
- Whether payees are merchants, sub-merchants, billers, agents, beneficiaries, customers, platform participants, or another classification.
- Payment facilitator, marketplace, commercial agent, and bill-payment-service implications.
- Payer-payee relationship risk, collusion risk, and fake obligation risk.
- Partner confirmation requirements for payee-created request models.
- Payee-side fee, onboarding, request, payout, subscription, or platform fee review where applicable.
- Payee-side data access, privacy, and security review.

Important principle:

```text
A payee-created request changes the creator of the payment request, but it must not weaken regulatory, PSP/acquirer, payout, evidence, authorization, risk, reconciliation, or recordkeeping controls.

No payee-created request flow should launch unless Legal, Compliance, Payments, Risk, Finance, Product, Security, Privacy, and relevant partners have assessed and approved the model.
```

---

## 1. Purpose

This document defines the assessment framework for determining whether PayPlus can legally, operationally, commercially, and contractually support a proposed bill payment product, payment flow, payee category, payee type, request creator model, jurisdiction, payment service provider, acquirer, processor, payout provider, or related payment partner.

`DOC-03` is a foundation document.

It should be used before PayPlus launches, expands into a new jurisdiction, adds a bill category, adds a payee type, enables payee-created payment requests, changes a payment flow, changes its role in the funds flow, introduces multi-card or multi-source payment, or contracts with a new payment partner.

This document does not provide legal advice, regulatory conclusions, card network rule interpretations, accounting treatment, tax treatment, or final partner approval.

All such conclusions must be provided by qualified internal or external legal, compliance, payments, tax, accounting, and partner stakeholders.

---

## 2. Scope

This document covers:

- Regulatory role assessment.
- Licensing and exemption considerations.
- Money transmission and payment services considerations.
- Bill payment service considerations.
- Payment facilitator and marketplace considerations.
- Payee onboarding regulatory and partner assessment.
- Payee-created payment request assessment.
- Request creator type assessment.
- Payee type and payee capability assessment.
- Landlord, rent, invoice, biller, school, utility, service provider, and business-payee role assessment.
- Card network and acquirer considerations.
- PSP, acquirer, processor, gateway, and payout provider assessment.
- Merchant category code and transaction classification considerations.
- Payee and bill category acceptability.
- Funds flow and settlement model review.
- Payout model review.
- Multi-card or multi-source payment assessment.
- Consumer protection and fee disclosure assessment.
- Payer authorization and payee-created request disclosure assessment.
- AML, sanctions, fraud, anti-cashout, collusion, and request-abuse considerations.
- Data protection and security due diligence.
- Payer/payee data visibility and privacy assessment.
- Partner onboarding and due diligence requirements.
- Reserve, holdback, collateral, and settlement terms.
- Contractual risk and required contract provisions.
- Launch readiness gates.
- Assumptions, constraints, dependencies, risks, and open questions.

---

## 3. Out of Scope

This document does not define:

- Final legal opinion.
- Regulatory licensing strategy.
- Final compliance policies.
- Final AML policy.
- Final sanctions policy.
- Final fraud rules.
- Final payee onboarding policy.
- Final landlord verification policy.
- Final tenancy contract verification standard.
- Final invoice verification standard.
- Final payer-payee dispute process.
- Final PSP or acquirer selection.
- Final commercial pricing.
- Final payee-side pricing.
- Final accounting policy.
- Final tax policy.
- Final technical architecture.
- Product requirements.
- Payment state machine.
- Reconciliation procedures.
- User, payer, or payee disclosures.
- Customer or payee support procedures.

These items must be defined in downstream documents, legal memoranda, compliance policies, partner contracts, or operating procedures.

---

## 4. Assessment Triggers

A `DOC-03` assessment should be performed or refreshed when any of the following occurs:

| Trigger ID | Trigger | Required Review |
| --- | --- | --- |
| `TRG-DOC03-001` | Launch of PayPlus MVP. | Full regulatory, PSP, acquirer, funds flow, category, request creator, payee type, and payout assessment. |
| `TRG-DOC03-002` | New jurisdiction. | Legal, licensing, tax, data, and partner review. |
| `TRG-DOC03-003` | New bill category. | Category acceptability, MCC, risk, evidence, payee, and partner review. |
| `TRG-DOC03-004` | New payee type. | Payee due diligence, payout, AML, risk, privacy, partner, and role classification review. |
| `TRG-DOC03-005` | New payment method. | Partner, regulatory, fee disclosure, and technical review. |
| `TRG-DOC03-006` | Multi-card or multi-source payment launch. | Funds flow, acquirer, card network, refund, chargeback, authorization, and reconciliation review. |
| `TRG-DOC03-007` | Change to funds flow. | Legal, licensing, settlement, safeguarding, and partner review. |
| `TRG-DOC03-008` | Change to payout model. | Payout provider, risk, settlement, and reconciliation review. |
| `TRG-DOC03-009` | Change to pricing, fee, surcharge, convenience fee, payee fee, or platform fee model. | Legal, consumer protection, card network, partner, accounting, and tax review. |
| `TRG-DOC03-010` | New PSP, acquirer, processor, gateway, or payout provider. | Vendor due diligence, compliance, security, commercial, and contract review. |
| `TRG-DOC03-011` | Partner reserve, holdback, or collateral requirement changes. | Finance, liquidity, legal, and risk review. |
| `TRG-DOC03-012` | Material increase in chargebacks, fraud, complaints, payer disputes, payee disputes, request abuse, or payout failures. | Risk, compliance, acquirer, partner, and operational review. |
| `TRG-DOC03-013` | Regulatory, card network, partner, or legal rule change. | Impact assessment and policy update. |
| `TRG-DOC03-014` | Enablement of payee-created payment requests. | Regulatory role, PayFac/marketplace, partner, payee onboarding, payer authorization, risk, payout, privacy, fee, and contract review. |
| `TRG-DOC03-015` | Enablement of landlord-created rent requests. | Rent category, landlord onboarding, tenancy evidence, payer-payee relationship, anti-collusion, payout, partner, and disclosure review. |
| `TRG-DOC03-016` | Enablement of payee-created invoice, fee, or business payment requests. | Business/payee role, invoice evidence, KYB/KYC, invoice fraud, partner, chargeback, and dispute review. |
| `TRG-DOC03-017` | Change to payee capability permissions. | Review whether newly permitted payee actions affect regulatory role, partner approval, risk, privacy, and support requirements. |

---

## 5. Regulatory Role Assessment

PayPlus must determine its regulatory role in each jurisdiction and payment flow.

Potential roles may include:

| Role | Description | Assessment Question |
| --- | --- | --- |
| Merchant of record | PayPlus is treated as merchant for card acceptance. | Is PayPlus selling a service, collecting funds, or facilitating bill payment as merchant? |
| Payment facilitator | PayPlus enables payment acceptance for third-party payees or sub-merchants. | Is PayPlus onboarding or processing for third-party payees? |
| Sub-merchant platform | Payees are treated as sub-merchants under a PSP/acquirer or PayFac model. | Are payees accepting card-funded payments through PayPlus? |
| Marketplace or platform | PayPlus connects payers and payees and facilitates payment. | Does payee-created request functionality create a marketplace or platform model? |
| Payment agent | PayPlus receives funds on behalf of biller, payee, or user. | Is PayPlus acting as agent for either party? |
| Commercial agent | PayPlus acts under a commercial agent arrangement for payees or billers. | Does an agency exemption or commercial agent model apply? |
| Agent of the payee | PayPlus receives payment on behalf of a payee such that payer obligation may be discharged when PayPlus receives funds. | Does the contractual structure support agent-of-payee treatment? |
| Agent of the user or payer | PayPlus acts on behalf of user or payer to transmit payment to payee. | Does this increase money transmission or payment service risk? |
| Money transmitter or payment service provider | PayPlus receives funds for transmission to another party. | Does the flow trigger licensing or registration obligations? |
| Stored value or e-money issuer | PayPlus holds user value for future use. | Are funds stored or redeemable later? |
| Technical service provider | PayPlus provides technology but does not control funds. | Is PayPlus isolated from possession/control of funds? |
| Bill payment service provider | PayPlus provides a bill payment or payment initiation service. | Are specific bill payment regulations applicable? |
| Debt collection or collection agent | PayPlus facilitates requests for payment of amounts owed to another party. | Could payee-created requests, overdue invoices, rent, or fees create debt collection implications? |
| Payment initiation or request-to-pay service provider | PayPlus initiates or facilitates requests for payment without itself being the underlying payee. | Does payee-created request functionality trigger payment initiation or request-to-pay regulation? |

The legal conclusion may vary by jurisdiction, payment method, payee type, request creator type, funds flow, contractual structure, and operational control.

For payee-created requests, assessment must specifically determine:

- Whether the payee is a merchant, sub-merchant, biller, beneficiary, agent, platform participant, customer, or other role.
- Whether PayPlus is facilitating payment acceptance for third-party payees.
- Whether payee onboarding creates payment facilitator or marketplace obligations.
- Whether the payer’s obligation is owed to the payee and when it is discharged.
- Whether PayPlus receives funds for transmission or only provides technology and payment coordination.
- Whether PayPlus has possession or control of payer or payee funds.
- Whether payer authorization and payee-created request messaging affect consumer protection or debt collection analysis.
- Whether rent, invoice, education, utility, or fee requests require category-specific legal treatment.

No product flow should launch without documented role assessment.

---

## 6. Licensing and Exemption Considerations

Legal and Compliance must assess whether PayPlus requires licenses, registrations, exemptions, agent arrangements, sponsorships, or partner coverage.

Assessment areas include:

- Money transmission.
- Payment services.
- Payment initiation services.
- Request-to-pay services.
- Bill payment services.
- Stored value or wallet services.
- E-money issuance.
- Prepaid access.
- Agent-of-the-payee models.
- Agent-of-the-user models.
- Commercial agent exemptions.
- Payment facilitator registration.
- Sub-merchant onboarding obligations.
- Marketplace payment facilitation.
- Platform payment services.
- Cross-border payment services.
- FX or currency conversion.
- Consumer lending or credit, if payment timing creates credit exposure.
- Debt collection implications, if relevant.
- Rent collection or landlord/tenant payment rules, if relevant.
- Invoice collection or accounts receivable facilitation, if relevant.
- Charitable solicitation, if bill categories include donations.
- Insurance premium payment rules, if applicable.
- Education, rent, tax, utility, government, loan, mortgage, invoice, or fee payment restrictions.
- State, federal, provincial, national, or regional requirements.
- Exemptions available through regulated partners.
- Contractual conditions required for an exemption.
- Payee onboarding, KYC/KYB, beneficial ownership, and sanctions requirements.

Each jurisdiction, flow, payee type, request creator type, and category should have a documented conclusion or unresolved risk rating before launch.

---

## 7. Funds Flow Assessment

A funds flow diagram and written description must be prepared for each payment model.

The assessment should identify:

- Who creates the payment request.
- Whether the request is payer-created, payee-created, admin-created, partner-created, or system-created.
- Who the payer pays.
- Who the user or payer believes they are paying.
- Who is merchant of record.
- Whether the payee is a merchant, sub-merchant, biller, beneficiary, agent, or platform participant.
- Who submits card authorization.
- Who captures the card payment.
- Who receives settlement from the acquirer or PSP.
- Whether funds enter PayPlus-controlled accounts.
- Whether funds are commingled or segregated.
- Whether funds are safeguarded or held for benefit of users, payers, or payees.
- Whether PayPlus has discretion over funds.
- Who initiates payout.
- Who is the payout recipient.
- Whether payout destination is controlled by PayPlus, partner, or payee.
- Whether payout occurs before card settlement.
- Whether PayPlus prefunds payout.
- Whether partner holds reserves.
- Whether payee-specific holds or reserves apply.
- Whether refunds are possible after payout.
- Whether chargeback liability remains after payout.
- Whether payer obligations are considered satisfied on PayPlus receipt, payee receipt, payout initiation, payout completion, or another event.
- Whether users receive stored balance, credits, or wallet value.
- Whether payees receive stored balance, wallet value, or account balance functionality.
- Whether funds cross borders.
- Whether FX occurs.
- How failed, reversed, rejected, expired, cancelled, withdrawn, refunded, or charged-back transactions are handled.

For payee-created requests, the funds flow assessment must also document:

- Whether the payee can create requests only after onboarding and approval.
- Whether the payer must accept and authorize before funding.
- Whether payee can alter amount, destination, evidence, or terms after payer authorization.
- Whether any payee-side fee is deducted from payout or billed separately.
- Whether payee request withdrawal is supported before payer authorization.
- Whether payer rejection, query, or dispute occurs before any funds movement.
- Whether payer or payee receives any stored-value-like credit, balance, or deferred settlement.

Funds flow design must be consistent with legal conclusions, PSP/acquirer rules, accounting treatment, tax treatment, and operational capabilities.

---

## 8. Card Network, PSP, and Acquirer Considerations

PayPlus must assess whether proposed flows are acceptable to card networks, PSPs, acquirers, and processors.

Assessment areas include:

| Area | Review Question |
| --- | --- |
| Merchant classification | What is the appropriate merchant category code or transaction classification? |
| Payee-created request model | Does the PSP/acquirer permit payees to create requests that result in card-funded payment after payer authorization? |
| PayFac or marketplace model | Does the flow require PayPlus to operate as payment facilitator, marketplace, platform, or sub-merchant manager? |
| Sub-merchant model | Are billers or payees treated as sub-merchants or merchant beneficiaries? |
| Payee onboarding requirements | What payee KYC/KYB, sanctions, beneficial ownership, and underwriting requirements apply? |
| Prohibited use cases | Is bill payment or the target bill category restricted or prohibited? |
| Cash-like transactions | Could the flow be considered cash disbursement, quasi-cash, money transfer, or cash equivalent? |
| Surcharging and convenience fees | Are payer-paid service fees permitted under applicable rules and law? |
| Payee-side fees | Are payee onboarding, subscription, request, payout, or platform fees permitted under partner rules and law? |
| Account funding transaction | Could the payment be treated as funding an account, wallet, or transfer? |
| Original credit transaction | Are payouts supported via card rails, if applicable? |
| Multi-card payment | Are split payments over multiple cards allowed? |
| Partial authorization | Is partial authorization supported or prohibited? |
| Delayed capture | Is capture timing allowed for the flow? |
| Request-to-pay timing | Are there rules affecting time between payee request creation, payer authorization, capture, and payout? |
| Refund after payout | Can refunds be processed if payout already occurred? |
| Payee request withdrawal | Does partner support or restrict withdrawal/cancellation before payer payment? |
| Chargeback evidence | Can PayPlus provide sufficient evidence of payer authorization, disclosure acceptance, request origin, payee identity, and service delivery? |
| Cardholder disclosure | Are fees, request origin, payee identity, and payment timing clearly disclosed? |
| Recurring payments | Are recurring or scheduled payee-created requests supported? |
| High-risk category | Does the category or payee type trigger enhanced underwriting or reserves? |
| Geographic restrictions | Are specific countries, states, or territories unsupported? |
| Brand rules | Are card brand-specific requirements applicable? |

Payments, Legal, and Compliance must obtain written partner confirmation for material assumptions where possible.

---

## 9. Merchant Category Code and Transaction Classification

MCC and transaction classification may affect:

- Interchange and scheme fees.
- User or payer card rewards eligibility.
- Cash advance treatment.
- Issuer authorization behavior.
- Risk scoring.
- Card network compliance.
- PSP/acquirer underwriting.
- User or payer complaints.
- Payee complaints.
- Dispute handling.
- Commercial viability.

PayPlus should document:

- Proposed MCC or classification.
- Rationale.
- PSP/acquirer confirmation.
- Card network restrictions, if any.
- Whether transactions may be treated as quasi-cash or money transfer.
- Whether issuer cash advance fees may apply.
- Whether user-facing or payer-facing disclosure is required.
- Whether classification varies by category.
- Whether classification varies by payee type.
- Whether classification varies by request creator type.
- Whether payee-created rent, invoice, fee, or bill requests require separate classification.
- Impact on pricing and unit economics.

Final classification should be confirmed with the PSP/acquirer before launch.

---

## 10. Payee, Request Creator, and Bill Category Assessment

Each bill category, payee type, and request creator model should be assessed for regulatory, partner, operational, and risk acceptability.

Candidate assessment dimensions:

| Dimension | Questions |
| --- | --- |
| Legal permissibility | Is the category and request creator model legally permitted in the launch jurisdiction? |
| Partner acceptability | Does the PSP/acquirer/payout provider allow this category, payee type, and request model? |
| MCC fit | Is there an acceptable transaction classification? |
| Request creator type | Is the request payer-created, payee-created, admin-created, partner-created, or system-created? |
| Payee role | Is the payee a merchant, sub-merchant, biller, landlord, school, utility, service provider, beneficiary, agent, or other role? |
| Payee onboarding | Can the payee be onboarded and verified sufficiently before request creation or payout? |
| Payee capability permissions | Can product controls restrict payee actions by type, status, category, geography, and risk tier? |
| Risk level | Does the category or request model increase fraud, cashout, collusion, fake invoice, fake rent, or chargeback risk? |
| Consumer protection | Are special disclosures, cancellation rights, dispute rights, or payer protections required? |
| Payer authorization | Does the flow ensure payment cannot occur until payer review and authorization? |
| Payer-payee relationship | Can the relationship between payer and payee be verified or risk-assessed where required? |
| Payout feasibility | Can PayPlus pay the biller or payee reliably and reversibly where required? |
| Refund feasibility | Can payments be reversed or refunded if needed? |
| Evidence quality | Can PayPlus prove payment obligation, request origin, payer authorization, service delivery, and payout? |
| Operational complexity | Does the category require manual review or custom routing? |
| Economics | Does the category and request model meet contribution margin thresholds? |
| Complaint risk | Is the category or request model likely to create user, payer, or payee complaints? |

High-risk or restricted categories, payee types, and request creator models should require explicit approval before launch.

---

## 11. Prohibited, Restricted, and Enhanced Review Categories

PayPlus should maintain category lists for:

- Prohibited categories.
- Restricted categories.
- Enhanced review categories.
- Approved MVP categories.
- Approved payee-created request categories.
- Approved payee types.
- Approved partner-specific categories.
- Jurisdiction-specific restricted categories.
- Request-creator-specific restricted categories.

Examples of categories that may require enhanced review include:

- Rent.
- Mortgage.
- Loan repayment.
- Credit card repayment.
- Tax payments.
- Government payments.
- Utility payments.
- Tuition and education payments.
- Insurance premiums.
- Medical bills.
- Legal fees.
- Business invoices.
- Service provider invoices.
- School fees.
- Landlord-created rent requests.
- Payee-created invoice requests.
- Donations.
- Crypto-related payments.
- Gambling-related payments.
- Investment-related payments.
- Money transfer.
- Cash equivalent purchases.
- Gift cards or stored value.
- Person-to-person payments.
- Self-payments or payments to user-controlled entities.
- Payments to newly onboarded individual payees.
- Payments where payer and payee appear related or collusive.
- Requests created by payees with high rejection, dispute, complaint, or chargeback rates.

Final prohibited and restricted category lists must be approved by Legal, Compliance, Payments, Risk, and relevant partners.

---

## 12. PSP, Acquirer, Processor, Gateway, and Payout Provider Due Diligence

Partner due diligence should cover:

| Area | Required Review |
| --- | --- |
| Regulatory status | Licenses, registrations, sponsorship model, jurisdiction coverage. |
| Product support | Support for bill payment, payee-created requests, multi-card, refunds, chargebacks, payouts, and reporting. |
| PayFac/platform support | Whether partner supports PayPlus as merchant, PayFac, marketplace, platform, agent, or bill-payment provider. |
| Payee onboarding | Partner requirements for payee KYC/KYB, beneficial ownership, sanctions, underwriting, and monitoring. |
| Category support | Approved and prohibited categories, including rent, invoice, education, utility, insurance, and other payment obligations. |
| Card network coverage | Supported card brands, regions, issuer routing, scheme capabilities. |
| Pricing | Authorization, capture, processing, gateway, refund, chargeback, payout, FX, monthly, minimum, setup, payee onboarding, verification, and payee account fees. |
| Settlement | Settlement timing, reserves, holdbacks, minimum balances, prefunding, collateral, payee-specific holds. |
| Risk controls | Fraud tools, transaction monitoring, velocity limits, payee monitoring, request abuse monitoring, rule configuration. |
| Chargebacks | Dispute process, evidence submission, representment support, deadlines, fees. |
| Payout capabilities | Bank transfer, instant payout, card payout, local rails, cross-border rails, settlement reports. |
| Reconciliation | Reporting files, webhooks, transaction IDs, payout IDs, fee reports, balance reports, payee-level reporting. |
| Security | PCI DSS status, SOC reports, ISO certifications, penetration testing, encryption. |
| Privacy | Data processing agreement, sub-processors, data residency, retention, deletion, payer/payee data boundaries. |
| Reliability | SLAs, uptime history, incident process, status page, support model. |
| Integration | APIs, SDKs, webhooks, idempotency, sandbox, testing tools. |
| Contract | Liability, indemnity, termination, audit rights, data rights, change notice, prohibited use, payee terms, sub-merchant terms. |
| Operational support | Escalation process, account management, implementation support, dispute escalation, payee onboarding support. |

Due diligence results should be stored in the vendor and compliance records.

---

## 13. Partner Comparison Scorecard

A partner comparison scorecard should be used where multiple PSPs/acquirers/payout providers are considered.

| Criterion | Weight | Provider A | Provider B | Provider C | Notes |
| --- | --- | --- | --- | --- | --- |
| Regulatory coverage | TBD | TBD | TBD | TBD |  |
| Bill payment acceptability | TBD | TBD | TBD | TBD |  |
| Payee-created request support | TBD | TBD | TBD | TBD |  |
| PayFac / marketplace / platform support | TBD | TBD | TBD | TBD |  |
| Payee onboarding and underwriting support | TBD | TBD | TBD | TBD |  |
| Category support | TBD | TBD | TBD | TBD |  |
| Rent / invoice / education / utility support | TBD | TBD | TBD | TBD |  |
| Multi-card support | TBD | TBD | TBD | TBD |  |
| Payout capabilities | TBD | TBD | TBD | TBD |  |
| Refund and chargeback support | TBD | TBD | TBD | TBD |  |
| Reconciliation quality | TBD | TBD | TBD | TBD |  |
| Payee-level reporting | TBD | TBD | TBD | TBD |  |
| Pricing | TBD | TBD | TBD | TBD |  |
| Settlement timing | TBD | TBD | TBD | TBD |  |
| Reserve requirements | TBD | TBD | TBD | TBD |  |
| Payee-specific reserve or hold support | TBD | TBD | TBD | TBD |  |
| Fraud tools | TBD | TBD | TBD | TBD |  |
| Payee/request abuse monitoring | TBD | TBD | TBD | TBD |  |
| Security and compliance | TBD | TBD | TBD | TBD |  |
| API quality | TBD | TBD | TBD | TBD |  |
| Operational support | TBD | TBD | TBD | TBD |  |
| Contract flexibility | TBD | TBD | TBD | TBD |  |
| Overall fit | TBD | TBD | TBD | TBD |  |

Weights should reflect launch priorities and risk appetite.

---

## 14. Required Partner Confirmations

Before launch, PayPlus should seek written confirmation from relevant partners on:

- Whether the PayPlus product and funds flow are supported.
- Whether payer-created and payee-created request models are supported.
- Whether payee onboarding or payee-created request functionality changes the partner’s view of PayPlus role.
- Approved jurisdictions.
- Approved bill categories.
- Approved payee types.
- Approved request creator types.
- Prohibited categories.
- Merchant of record structure.
- PayFac, marketplace, platform, agent, or sub-merchant implications.
- Payee onboarding, KYC/KYB, beneficial ownership, and sanctions obligations.
- MCC or transaction classification.
- Whether classification varies by category, payee type, or request creator type.
- Whether the transaction may be treated as cash-like, quasi-cash, account funding, or money transfer.
- User, payer, payee, convenience fee, surcharge, platform fee, or service fee restrictions.
- Multi-card or split payment support.
- Authorization and capture timing.
- Payer acceptance and authorization evidence requirements.
- Refund and reversal support.
- Payee request withdrawal or cancellation support.
- Chargeback process and liability.
- Required chargeback evidence for payee-created requests.
- Payout method and settlement timing.
- Reserve, holdback, prefunding, collateral, or payee-specific reserve requirements.
- Reporting and reconciliation data availability.
- Payee-level reporting availability.
- Data protection and security commitments.
- Payer/payee data visibility constraints.
- Operational support and escalation process.
- Contractual change notice obligations.

Where written confirmation cannot be obtained, the assumption should be logged as an open risk.

---

## 15. Consumer Protection and Disclosure Assessment

Legal, Compliance, and Product should assess whether user, payer, and payee disclosures adequately cover:

- PayPlus role.
- Request creator or request origin.
- Whether request is payer-created or payee-created.
- Payee or biller details.
- Bill amount or payment obligation amount.
- Service fee.
- Payee-side fees, if applicable and visible to payee.
- Taxes, if applicable.
- Total amount charged to payer.
- Payout amount or net payout amount, if shown to payee.
- Estimated processing time.
- Whether payment is guaranteed or conditional.
- Payer authorization requirement.
- Statement that payee-created requests are not paid unless payer authorizes payment.
- Payer rejection, query, dispute, or expiration behavior.
- Payee withdrawal or cancellation behavior before payer authorization.
- Refund and cancellation rules.
- Failed payment behavior.
- Chargeback and dispute rights.
- Promotion terms.
- Card statement descriptor.
- Potential card issuer fees, if applicable and known.
- User or payer responsibility for late fees from billers or payees.
- Payee responsibility for accurate request information and evidence.
- Data use and privacy.
- Customer and payee support contact.
- Terms acceptance.

For payee-created requests, disclosure assessment should confirm that the payer is not misled into believing:

- the request is mandatory merely because the payee sent it,
- the payment has already been completed,
- PayPlus has validated the legal enforceability of the obligation unless expressly approved,
- PayPlus guarantees the payee’s performance or the underlying service,
- payout timing is guaranteed before actual confirmation.

Detailed content requirements belong in:

- `DOC-07 Content, Disclosure & User Communication`.
- `DOC-08 Notification, Receipt & Communication Rules`.

---

## 16. AML, Sanctions, Anti-Cashout, and Fraud Assessment

PayPlus must assess whether the product flow creates AML, sanctions, fraud, cashout, collusion, or abuse risk.

Assessment areas include:

- User or payer identity verification requirements.
- Payee verification requirements.
- Payee onboarding requirements.
- Payee type risk rating.
- Beneficial ownership review, where applicable.
- Sanctions screening.
- PEP screening, if applicable.
- Adverse media review, if applicable.
- Transaction monitoring.
- Request monitoring.
- Velocity limits.
- Category limits.
- Payee limits.
- User or payer limits.
- Request creation limits.
- Payee-created request spam detection.
- Self-payment detection.
- Circular payment detection.
- Related-party or collusive payer-payee detection.
- Fake invoice detection.
- Fake rent request detection.
- Duplicate tenancy, lease, invoice, or bill detection.
- Landlord verification and tenancy evidence review, where rent is enabled.
- Card testing detection.
- Stolen card fraud detection.
- Account takeover detection.
- First-party misuse.
- Refund abuse.
- Chargeback abuse.
- Promotion abuse.
- Suspicious activity escalation.
- Law enforcement or regulatory request process.
- Recordkeeping requirements.

Detailed controls belong in `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`.

---

## 17. Data Protection, Privacy, and Security Assessment

PayPlus must assess data protection and security requirements for each partner and flow.

Review areas include:

- PCI DSS scope.
- Card data handling.
- Tokenization.
- Data minimization.
- User, payer, and payee consent.
- Privacy notice coverage.
- Payer/payee data visibility boundaries.
- Payee access to request and payout information.
- Payer access to payee-created request evidence.
- Treatment of tenancy contracts, invoices, service agreements, and other sensitive documents.
- Role-based access controls for payer, payee, support, operations, compliance, risk, finance, and admin users.
- Data processing agreements.
- Cross-border data transfers.
- Data residency.
- Sub-processor lists.
- Retention and deletion.
- Encryption in transit.
- Encryption at rest.
- Access controls.
- Audit logs.
- Incident notification.
- Breach response.
- Vulnerability management.
- SOC 2 or equivalent reports.
- Penetration testing.
- Business continuity and disaster recovery.
- Partner API security.
- Webhook security.
- Secrets management.

Detailed requirements belong in:

- `DOC-15 Privacy, Data Protection & Record Retention`.
- `DOC-19 Security, Tokenization & Authentication`.

---

## 18. Contractual Assessment

Partner contracts should be reviewed for:

| Contract Area | Review Focus |
| --- | --- |
| Scope of services | Does the contract clearly allow PayPlus use case, categories, payee types, and payee-created request model? |
| Role definitions | Are merchant, platform, PayFac, sub-merchant, agent, processor, payer, payee, and data roles clear? |
| Payee onboarding | Are KYC/KYB, sanctions, beneficial ownership, underwriting, monitoring, and approval responsibilities clear? |
| Payee terms | Are required payee terms, sub-merchant terms, biller terms, landlord terms, or platform terms defined where applicable? |
| Regulatory responsibility | Who is responsible for licenses, KYC, AML, sanctions, reporting, complaints, and payee monitoring? |
| Card network compliance | Who is responsible for network rule compliance and fines? |
| Pricing | Are all fees, minimums, payee-side charges, platform fees, and pass-through charges documented? |
| Reserves | Are reserves, holdbacks, collateral, prefunding, and payee-specific hold terms clear? |
| Settlement | Are settlement timing, payee payout timing, and funding obligations clear? |
| Chargebacks | Are liability, fees, deadlines, evidence, and representment rights clear for payer-created and payee-created requests? |
| Refunds | Are refund rights, timing, and fees clear? |
| Payouts | Are payout responsibilities, failures, reversals, recalls, payee account changes, and exception handling clear? |
| Request withdrawal | Are payee request withdrawal or cancellation obligations supported where applicable? |
| Payer disputes | Are payer query, rejection, and dispute obligations supported where applicable? |
| Data protection | Are controller/processor roles, DPA, sub-processors, and breach notices clear for payer and payee data? |
| Security | Are PCI, audits, penetration testing, and security controls addressed? |
| SLAs | Are uptime, support, incident response, and escalation commitments defined? |
| Reporting | Are transaction, request, fee, dispute, payout, balance, payee-level, and reconciliation reports required? |
| Audit rights | Can PayPlus audit relevant compliance, security, payee onboarding, and financial records? |
| Change notice | Must partner notify PayPlus of pricing, rule, reserve, capability, category, or payee onboarding changes? |
| Termination | Are suspension, termination, migration, payee offboarding, and wind-down rights acceptable? |
| Indemnity and liability | Are liability caps, exclusions, chargeback liability, fraud liability, and indemnities acceptable? |
| Assignment and subcontracting | Can partner change processors or subcontractors without approval? |
| Governing law | Is governing law acceptable for the launch model? |

Legal approval is required before signing any material payment partner agreement.

---

## 19. Settlement, Reserve, Holdback, and Liquidity Review

Finance and Payments must assess:

- Settlement timing.
- Funding availability.
- Payout timing.
- Payee payout timing.
- Whether payout occurs before card settlement.
- Reserve percentage.
- Rolling reserve period.
- Holdback amount.
- Payee-specific holds.
- Payee-specific reserve requirements.
- Collateral or guarantee requirements.
- Prefunding requirement.
- Minimum balance requirement.
- Chargeback reserve requirement.
- Refund reserve requirement.
- Currency settlement.
- FX settlement.
- Weekend and holiday delays.
- Bank cutoff times.
- Liquidity buffer needed.
- Impact on cash runway.
- Impact on category scaling.
- Impact on payee-created request scaling.
- Impact on payee onboarding and payee retention.
- Risk of promising payout timing to payees before funds are available.

This review should be aligned with `DOC-02 Business Model & Unit Economics`.

---

## 20. Multi-Card and Multi-Source Payment Assessment

If PayPlus supports multi-card or multi-source payments, the assessment must include:

- Whether PSP/acquirer supports split funding.
- Whether multiple authorizations may fund one bill.
- Whether multiple authorizations may fund one payee-created request.
- Whether partial authorization is supported.
- Whether PayPlus may hold partial funds while completing other authorizations.
- Whether failed partial funding requires reversal or cancellation.
- How payer authorization covers each funding source.
- How service fees are calculated.
- How fees are allocated across funding sources.
- How payee-side fees, if any, interact with split funding.
- How refunds are allocated across funding sources.
- How chargebacks are handled when only one funding source disputes.
- Whether the biller or payee receives one payout or multiple payouts.
- How reconciliation links parent bill payment to child funding events.
- How promotion eligibility is calculated.
- Whether multi-card increases AML, cashout, collusion, or request-abuse risk.
- Whether multi-card changes licensing or funds control analysis.
- Whether additional disclosures are required.
- Whether payee-created request status remains accurate during partial authorization or partial failure.

Detailed requirements belong in:

- `DOC-09 Payment Request, Multi-Funding Source & Settlement`.
- `DOC-11 Refund, Cancellation & Chargeback`.
- `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 21. Payee-Created Request Assessment

Payee-created payment requests require a dedicated assessment before launch.

This assessment applies when an approved payee, such as a landlord, school, utility provider, biller, service provider, business, or other approved payee, creates a bill, invoice, fee, rent, or payment obligation request and sends it to a payer.

The assessment must determine:

| Assessment Area | Required Question |
| --- | --- |
| Payee eligibility | Which payee types may create requests? |
| Payee onboarding | What onboarding, KYC/KYB, sanctions, beneficial ownership, payout verification, and risk checks are required? |
| Payee role | Is the payee a merchant, sub-merchant, biller, beneficiary, landlord, agent, customer, or platform participant? |
| PayPlus role | Does PayPlus act as merchant, PayFac, marketplace, agent, payment service provider, bill payment provider, or technical service provider? |
| Payer role | Is the payer a consumer, business, tenant, student, customer, or other payer type? |
| Request evidence | What evidence is required to prove the bill, invoice, fee, rent, or obligation? |
| Payer authorization | How does the payer review, accept, authorize, reject, query, or dispute the request? |
| Legal enforceability | Does PayPlus need to avoid representing that it validates the legal enforceability of the underlying obligation? |
| Consumer protection | What payer disclosures and protections are required? |
| Debt collection risk | Could payee-created requests be viewed as collection activity, especially for overdue obligations? |
| Payee abuse risk | How are fake, inflated, duplicate, spam, collusive, or self-dealing requests prevented? |
| Payer-payee relationship | Is relationship verification required for rent, landlord, invoice, or other categories? |
| Partner approval | Does PSP/acquirer/payout provider approve this model? |
| Classification | Does MCC or transaction classification differ from payer-created requests? |
| Fee model | Are payer fees, payee fees, platform fees, or split fees permitted and disclosed? |
| Payout | When may payout occur and to whom? |
| Refund/chargeback | How are refunds, chargebacks, reversals, and disputes handled? |
| Privacy | What information can be shown to payer and payee? |
| Recordkeeping | What evidence must be retained for audit, disputes, regulatory review, and partner review? |
| Monitoring | What request abuse, fraud, complaint, rejection, dispute, and chargeback monitoring is required? |

Payee-created requests must not be enabled unless:

- payee onboarding is approved,
- payer authorization is mandatory,
- evidence requirements are defined,
- payout gating is implemented,
- partner approval is obtained or risk-accepted,
- required disclosures are identified,
- privacy boundaries are defined,
- request abuse controls are defined,
- reconciliation and recordkeeping requirements are defined.

---

## 22. Landlord-Created Rent Request Assessment

Landlord-created rent requests require enhanced review before launch because they may create higher cashout, collusion, fraud, dispute, and regulatory risk.

The assessment should include:

| Assessment Area | Required Question |
| --- | --- |
| Landlord eligibility | Which landlords or property managers may onboard? |
| Landlord verification | What identity, business, property, payout, sanctions, and risk checks are required? |
| Tenant/payer relationship | How is the relationship between payer and landlord validated? |
| Tenancy evidence | What tenancy contract, lease agreement, rent schedule, property reference, or equivalent evidence is required? |
| Rent amount reasonableness | Can rent amount be checked against tenancy evidence or historical pattern? |
| Duplicate rent prevention | How are duplicate rent requests detected? |
| Recurring rent | Are recurring rent requests permitted, or must each request be individually authorized? |
| Self-payment and collusion | How are related-party, self-payment, circular, or collusive patterns detected? |
| Payout destination changes | What review is required when landlord payout details change? |
| Chargeback evidence | Can PayPlus produce payer authorization, tenancy evidence, landlord verification, payout proof, and communication evidence? |
| Consumer protection | What disclosures are required so payer understands PayPlus role and payment timing? |
| Debt collection | Could overdue rent requests create debt collection or landlord/tenant regulatory implications? |
| Partner approval | Do PSP/acquirer and payout providers approve rent and landlord-created requests? |
| Limits and monitoring | What value, frequency, payee, payer, and category limits apply? |

Landlord-created rent requests should remain restricted or deferred unless explicitly approved by Legal, Compliance, Payments, Risk, Product, Finance, Operations, Security, Privacy, and relevant partners.

---

## 23. Compliance Readiness Gates

PayPlus should not launch a jurisdiction, category, payment method, payment partner, payee type, request creator model, or funds flow until applicable compliance readiness gates are satisfied.

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC03-001` | Regulatory role assessed | Legal/Compliance documents PayPlus role for the flow, request creator type, payee type, and jurisdiction. |
| `GATE-DOC03-002` | Licensing path confirmed | Required licenses, exemptions, sponsorships, agent arrangements, PayFac arrangements, or partner coverage are documented. |
| `GATE-DOC03-003` | Funds flow approved | Funds flow diagram and description are approved by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-004` | PSP/acquirer acceptability confirmed | Partner confirms use case, category, payee type, request model, MCC/classification, and flow support. |
| `GATE-DOC03-005` | Payout model approved | Payout method, provider, timing, failures, reversals, payee destination controls, and reconciliation are assessed. |
| `GATE-DOC03-006` | Category restrictions defined | Approved, restricted, and prohibited categories are documented. |
| `GATE-DOC03-007` | Fee model reviewed | User, payer, payee, surcharge, convenience fee, platform fee, or pricing model is reviewed by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-008` | AML/risk assessment completed | AML, sanctions, fraud, anti-cashout, collusion, fake obligation, and abuse risks are assessed. |
| `GATE-DOC03-009` | Security/privacy review completed | PCI, privacy, security, payer/payee data visibility, and data protection reviews are completed. |
| `GATE-DOC03-010` | Partner due diligence completed | Vendor, regulatory, commercial, security, payee onboarding, and contract reviews are completed. |
| `GATE-DOC03-011` | Contract approved | Legal approves partner contract and required provisions. |
| `GATE-DOC03-012` | Settlement/reserve impact approved | Finance approves settlement timing, reserves, holdbacks, payee payout timing, and liquidity impact. |
| `GATE-DOC03-013` | Disclosure requirements identified | Required user, payer, and payee disclosures are identified for product implementation. |
| `GATE-DOC03-014` | Reporting and recordkeeping defined | Required transaction, request, payee, compliance, dispute, and reconciliation records are identified. |
| `GATE-DOC03-015` | Launch approval obtained | Required approvers sign off before launch. |
| `GATE-DOC03-016` | Payee onboarding model approved | Payee onboarding, verification, status, capability permissions, monitoring, and offboarding requirements are assessed and approved. |
| `GATE-DOC03-017` | Payee-created request model approved | Payee-created request role, evidence, payer authorization, partner acceptability, risk, privacy, payout, and recordkeeping requirements are assessed and approved. |
| `GATE-DOC03-018` | Landlord/rent request model approved | Landlord verification, tenancy evidence, payer-landlord relationship, rent risk, partner approval, and enhanced controls are assessed and approved before rent request launch. |

---

## 24. Assessment Template

Each assessed flow, partner, category, payee type, request creator model, or jurisdiction should include the following template.

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
- User / payer journey:
- Payee journey, if applicable:
- Request creation model:
- Card/funding flow:
- Payout flow:
- Refund flow:
- Chargeback flow:
- Rejection/query/dispute flow before authorization, if applicable:

3. Regulatory Role Assessment
- PayPlus role:
- Partner role:
- Payee role:
- Payer/user role:
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
- User/payer fee:
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

## 25. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC03-001` | PayPlus will require a documented legal role assessment before launch. | Legal / Compliance | Open |
| `ASM-DOC03-002` | PSP/acquirer approval will be required for the PayPlus bill payment use case. | Payments | Open |
| `ASM-DOC03-003` | MCC or transaction classification will materially affect cost, risk, and cardholder experience. | Payments / Finance | Open |
| `ASM-DOC03-004` | Some bill categories may be prohibited or restricted by partners. | Compliance / Payments | Open |
| `ASM-DOC03-005` | Multi-card or split funding may require additional partner approval. | Payments / Product | Open |
| `ASM-DOC03-006` | User, payer, convenience fee, surcharge, payee fee, or platform fee rules may vary by jurisdiction and partner. | Legal / Compliance | Open |
| `ASM-DOC03-007` | Settlement timing and reserves may materially affect launch feasibility. | Finance / Payments | Open |
| `ASM-DOC03-008` | Payee verification requirements may vary by category, payee type, request creator model, and payout model. | Compliance / Risk | Open |
| `ASM-DOC03-009` | Partner contracts will define key operating constraints. | Legal / Commercial | Open |
| `ASM-DOC03-010` | Regulatory conclusions may change if funds flow changes. | Legal / Compliance | Open |
| `ASM-DOC03-011` | Payee-created requests may change PayPlus role analysis, including PayFac, marketplace, agent, bill payment provider, or money transmission treatment. | Legal / Compliance / Payments | Open |
| `ASM-DOC03-012` | Payee onboarding and payee capability permissions may be required before payee-created requests can be approved by partners. | Payments / Compliance / Risk | Open |
| `ASM-DOC03-013` | Landlord-created rent requests may require enhanced legal, partner, evidence, and risk review. | Legal / Compliance / Risk | Open |
| `ASM-DOC03-014` | Payee-created invoice or fee requests may require KYB/KYC, invoice evidence, and business-payee underwriting. | Compliance / Risk / Payments | Open |
| `ASM-DOC03-015` | Payer authorization and request-origin disclosure will be required before any payee-created request can be funded. | Legal / Product / Payments | Open |
| `ASM-DOC03-016` | Payer/payee privacy boundaries may require separate data visibility and access-control assessment. | Privacy / Security | Open |

---

## 26. Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC03-001` | No launch without documented regulatory role assessment. | Prevents unassessed legal exposure. | Legal / Compliance |
| `CON-DOC03-002` | No launch without PSP/acquirer approval or acceptable documented assumption. | Prevents partner rule breach. | Payments |
| `CON-DOC03-003` | No restricted category launch without explicit approval. | Prevents unsupported or high-risk use cases. | Compliance / Risk |
| `CON-DOC03-004` | Fee model must be reviewed before implementation. | Prevents unlawful or prohibited fees. | Legal / Compliance |
| `CON-DOC03-005` | Funds flow cannot change without reassessment. | Prevents licensing and partner mismatch. | Legal / Payments |
| `CON-DOC03-006` | Partner contracts must support operational requirements. | Prevents gaps in refunds, chargebacks, reporting, and settlement. | Legal / Payments |
| `CON-DOC03-007` | AML, sanctions, fraud, anti-cashout, collusion, and request-abuse controls must be appropriate to flow risk. | Prevents financial crime and partner risk. | Compliance / Risk |
| `CON-DOC03-008` | Security and privacy review is required for payment partners and payee-created request flows. | Prevents data protection, PCI, and payer/payee visibility gaps. | Security / Privacy |
| `CON-DOC03-009` | Settlement and reserve terms must be approved by Finance. | Prevents liquidity surprises. | Finance |
| `CON-DOC03-010` | Required disclosures must be implemented before launch. | Prevents consumer protection and complaint risk. | Product / Legal |
| `CON-DOC03-011` | Payee-created request capability cannot launch without payee onboarding, payer authorization, partner acceptability, and risk review. | Prevents unapproved PayFac/marketplace, cashout, fake obligation, and consumer protection risks. | Product / Legal / Compliance / Payments |
| `CON-DOC03-012` | Payee-created rent requests cannot launch without landlord verification, tenancy evidence, and enhanced risk controls. | Prevents rent-based cashout and collusion risk. | Legal / Risk / Compliance |
| `CON-DOC03-013` | Payee-created request flows cannot charge or fund payer without explicit payer authorization. | Prevents unauthorized payment and consumer harm. | Product / Payments / Legal |
| `CON-DOC03-014` | Payee access to payer information must be limited to approved visibility. | Prevents privacy and security violations. | Privacy / Security |
| `CON-DOC03-015` | Payer access to payee evidence must be limited to approved visibility. | Prevents over-disclosure of payee-sensitive data. | Privacy / Product / Legal |

---

## 27. Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
| --- | --- | --- | --- | --- |
| `DEP-DOC03-001` | Product flow and funds flow diagram. | Regulatory and partner assessment. | Product / Payments | Open |
| `DEP-DOC03-002` | Target jurisdictions. | Licensing and legal assessment. | Project Owner / Legal | Open |
| `DEP-DOC03-003` | Target bill categories. | Category and partner acceptability assessment. | Product / Compliance | Open |
| `DEP-DOC03-004` | Proposed PSP/acquirer list. | Partner due diligence and confirmation. | Payments / Commercial | Open |
| `DEP-DOC03-005` | Proposed payout provider list. | Payout and settlement assessment. | Payments / Commercial | Open |
| `DEP-DOC03-006` | Proposed fee model. | Fee, disclosure, and card network review. | Commercial / Product | Open |
| `DEP-DOC03-007` | Risk control framework. | AML, sanctions, fraud, and anti-cashout review. | Risk / Compliance | Open |
| `DEP-DOC03-008` | Security and privacy requirements. | Partner data protection review. | Security / Privacy | Open |
| `DEP-DOC03-009` | Partner pricing and reserve terms. | Commercial and liquidity assessment. | Commercial / Finance | Open |
| `DEP-DOC03-010` | Draft partner contracts. | Contractual assessment. | Legal / Commercial | Open |
| `DEP-DOC03-011` | Ledger and reporting requirements. | Reconciliation, recordkeeping, and compliance reporting. | Finance / Engineering | Open |
| `DEP-DOC03-012` | Customer disclosure drafts. | Consumer protection assessment. | Product / Legal | Open |
| `DEP-DOC03-013` | Payee onboarding requirements. | Payee-created request, payout, role, AML, sanctions, partner, and risk assessment. | Product / Compliance / Risk | Open |
| `DEP-DOC03-014` | Payee type taxonomy and capability model. | Determine which payees can create which request types and under which controls. | Product / Risk / Compliance | Open |
| `DEP-DOC03-015` | Request creator type model. | Role, funds flow, partner, disclosure, and reporting assessment. | Product / Payments / Legal | Open |
| `DEP-DOC03-016` | Landlord/rent evidence standard. | Landlord-created rent request assessment. | Product / Legal / Risk | Open |
| `DEP-DOC03-017` | Invoice evidence and business-payee verification standard. | Payee-created invoice and fee request assessment. | Product / Risk / Compliance | Open |
| `DEP-DOC03-018` | Payer identification and invitation mechanism. | Consumer protection, privacy, security, and request delivery assessment. | Product / Engineering / Privacy | Open |
| `DEP-DOC03-019` | Payer acceptance, rejection, query, and dispute process. | Payee-created request legal, operational, and disclosure assessment. | Product / Operations / Legal | Open |
| `DEP-DOC03-020` | Payer/payee data visibility rules. | Privacy, security, support, and disclosure assessment. | Privacy / Security / Product | Open |
| `DEP-DOC03-021` | Partner confirmation of payee-created request support. | Launch approval for payee-created request model. | Payments / Commercial | Open |

---

## 28. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC03-001` | PayPlus launches with incorrect regulatory role classification. | Licensing breach, enforcement, partner termination. | Obtain legal assessment per jurisdiction and flow. | Legal / Compliance | Open |
| `RISK-DOC03-002` | Product flow is treated as money transmission or payment service requiring licensing. | Launch delay, regulatory risk, operating restrictions. | Evaluate exemptions, partner sponsorship, or licensed provider model. | Legal / Compliance | Open |
| `RISK-DOC03-003` | PSP/acquirer rejects bill payment or target category after integration. | Launch delay and rework. | Obtain written partner confirmation early. | Payments / Commercial | Open |
| `RISK-DOC03-004` | Transactions are classified as quasi-cash, cash advance, or money transfer. | Higher costs, issuer declines, user complaints. | Confirm MCC/classification and add disclosures if required. | Payments / Legal | Open |
| `RISK-DOC03-005` | User, payer, payee, platform, convenience fee, or surcharge model violates law, network rules, or partner restrictions. | Fines, refunds, product redesign. | Legal, card network, and partner fee review before launch. | Legal / Payments | Open |
| `RISK-DOC03-006` | Multi-card funding creates unsupported funds flow or refund complexity. | Compliance, operational, and reconciliation failures. | Require dedicated multi-card assessment and partner approval. | Product / Payments | Open |
| `RISK-DOC03-007` | Partner reserves or holdbacks create liquidity strain. | Working capital pressure and growth limits. | Model reserve impact and obtain Finance approval. | Finance / Payments | Open |
| `RISK-DOC03-008` | Inadequate payee verification enables fraud or cashout. | Financial loss and regulatory risk. | Implement payee verification and anti-cashout controls. | Risk / Compliance | Open |
| `RISK-DOC03-009` | Partner contract lacks required reporting or chargeback support. | Reconciliation gaps and loss exposure. | Contractual checklist and Legal review. | Legal / Payments | Open |
| `RISK-DOC03-010` | Privacy, PCI, or security obligations are underestimated. | Breach, compliance failure, remediation cost. | Security/privacy due diligence and PCI scope review. | Security / Privacy | Open |
| `RISK-DOC03-011` | Required user, payer, or payee disclosures are incomplete or unclear. | Complaints, disputes, regulatory risk. | Legal review of checkout, receipt, request, and terms content. | Product / Legal | Open |
| `RISK-DOC03-012` | Regulatory or network rule changes affect approved flows. | Product restrictions or operational changes. | Maintain periodic review and partner change notice monitoring. | Compliance / Payments | Open |
| `RISK-DOC03-013` | Payee-created request model changes PayPlus into a PayFac, marketplace, agent, or regulated payment service model unexpectedly. | Licensing, partner, contractual, and operational impact. | Dedicated payee-created request role assessment and partner confirmation. | Legal / Compliance / Payments | Open |
| `RISK-DOC03-014` | Payees are incorrectly classified as billers, beneficiaries, merchants, sub-merchants, or agents. | Regulatory, tax, contract, dispute, and partner compliance risk. | Define payee role classification by flow, category, and contract. | Legal / Compliance / Payments | Open |
| `RISK-DOC03-015` | Payee-created requests are used for fake invoices, fake rent, self-payment, or collusive cashout. | Fraud, chargebacks, partner termination, regulatory risk. | Require payee onboarding, evidence, relationship checks, limits, and monitoring. | Risk / Compliance | Open |
| `RISK-DOC03-016` | Landlord-created rent requests trigger landlord/tenant, rent collection, debt collection, or heightened consumer protection issues. | Legal risk, complaints, launch delay. | Conduct rent-specific legal and risk assessment before enablement. | Legal / Compliance / Product | Open |
| `RISK-DOC03-017` | Payer believes a payee-created request is mandatory, already validated, or already paid. | Complaints, disputes, unfair experience risk. | Require request-origin disclosure and explicit payer authorization. | Product / Legal | Open |
| `RISK-DOC03-018` | Payee sees payer-sensitive payment, card, risk, or private profile information. | Privacy, security, and trust risk. | Enforce payer/payee data visibility boundaries and RBAC. | Privacy / Security | Open |
| `RISK-DOC03-019` | PSP/acquirer does not support payee-created requests, sub-merchant treatment, or payee onboarding model. | Launch blocker or redesign. | Obtain explicit written confirmation before build or launch. | Payments / Commercial | Open |
| `RISK-DOC03-020` | Payee-created requests increase chargeback evidence burden. | Higher losses and representment failures. | Capture request origin, evidence, payer authorization, disclosure, communication, and payout proof. | Payments / Operations | Open |
| `RISK-DOC03-021` | Payee-side fee model is prohibited or creates unexpected disclosure, tax, or contract obligations. | Product redesign and financial risk. | Review payee-side pricing with Legal, Finance, Tax, and partners. | Legal / Finance / Commercial | Open |

---

## 29. Downstream Document Impact

`DOC-03` should guide downstream documents as follows:

| Downstream Document | Impact |
| --- | --- |
| `DOC-04` | Compliance readiness gates, certifications, controls, evidence, and launch approvals should reflect regulatory and partner assessment outputs, including payee onboarding, payee-created request, and rent/invoice request controls. |
| `DOC-05` | Product requirements must incorporate approved payment methods, categories, partner constraints, disclosures, payee types, request creator types, and flow limitations. |
| `DOC-06` | Payer, payee, landlord, biller, and partner journeys should reflect verification, eligibility, restricted category, payer authorization, and request-origin decisions. |
| `DOC-07` | User-facing, payer-facing, and payee-facing fee, timing, role, request-origin, refund, risk, authorization, issuer-fee, and payee-created request disclosures must reflect legal and partner findings. |
| `DOC-08` | Receipts and notifications must include required transaction, request-origin, payer authorization, fee, timing, request status, and failure information. |
| `DOC-09` | Payment request and settlement design must comply with approved funds flow, request creator model, payer authorization requirements, partner constraints, and multi-card limitations. |
| `DOC-10` | Payout and reconciliation must reflect approved payout provider, payee onboarding status, payee payout eligibility, settlement timing, reserves, and reporting files. |
| `DOC-11` | Refund, cancellation, chargeback, dispute, payer rejection, payee withdrawal, and loss allocation logic must reflect partner capabilities and liability allocation. |
| `DOC-12` | Bill category, document AI/OCR, payee verification, invoice evidence, rent evidence, landlord verification, and evidence standards must reflect approved assessment outputs. |
| `DOC-13` | Promotion rules must reflect any partner, fee, payer/payee, request-origin, and abuse restrictions identified in this assessment. |
| `DOC-14` | AML, sanctions, fraud, cashout, collusion, fake invoice, fake rent, request abuse, and payee risk controls must reflect risks identified in this assessment. |
| `DOC-15` | Privacy, retention, data visibility, data minimization, and sensitive document handling must reflect payer/payee data implications. |
| `DOC-16` | Technical architecture must support approved flow, payee portal/request services, integrations, controls, and partner constraints. |
| `DOC-17` | APIs, PSP/acquirer integrations, payout integrations, notification integrations, webhook handling, payee request APIs, and idempotency must reflect approved partner capabilities. |
| `DOC-18` | Ledger and reporting must capture fields needed for regulatory records, request creator type, payee type, payer authorization, partner reporting, disputes, reconciliation, and margin analysis. |
| `DOC-19` | Authentication, tokenization, PCI, RBAC, payer/payee data boundary, admin access, encryption, and audit controls must reflect approved assessment outputs. |
| `DOC-20` | Launch checklist must include completion of relevant DOC-03 gates and approvals, including payee-created request and rent-specific gates if enabled. |
| `DOC-21` | Runbooks must include monitoring for partner restrictions, payee onboarding issues, request abuse, settlement issues, chargebacks, category violations, payout failures, and compliance incidents. |

---

## 30. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC03-001` | What jurisdictions will PayPlus launch in first? | Project Owner / Legal | Critical | Open |
| `OQ-DOC03-002` | What legal role will PayPlus take in the MVP funds flow? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-003` | Does the MVP funds flow require money transmission, payment service, or similar licensing? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-004` | Can PayPlus rely on a regulated partner, exemption, or agent model? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-005` | Which PSP/acquirer will support the bill payment use case? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-006` | What MCC or transaction classification will apply? | Payments | Critical | Open |
| `OQ-DOC03-007` | Will transactions be treated as purchase, quasi-cash, money transfer, or account funding? | Payments / Legal | Critical | Open |
| `OQ-DOC03-008` | Are user-paid, payer-paid, payee-paid, service, convenience, platform, or surcharge fees permitted? | Legal / Payments | Critical | Open |
| `OQ-DOC03-009` | Which bill categories are approved, restricted, or prohibited for MVP? | Compliance / Risk / Product | Critical | Open |
| `OQ-DOC03-010` | What payee verification is required before payout? | Risk / Compliance | High | Open |
| `OQ-DOC03-011` | What payout provider and payout rail will be used? | Payments / Commercial | High | Open |
| `OQ-DOC03-012` | What settlement timing, reserves, holdbacks, or prefunding will apply? | Finance / Payments | High | Open |
| `OQ-DOC03-013` | Are multi-card or multi-source payments supported by the PSP/acquirer and legally acceptable? | Product / Payments / Legal | High | Open |
| `OQ-DOC03-014` | What AML, sanctions, fraud, anti-cashout, collusion, and request-abuse controls are required before MVP? | Compliance / Risk | Critical | Open |
| `OQ-DOC03-015` | What PCI, privacy, security, and data protection requirements apply? | Security / Privacy | High | Open |
| `OQ-DOC03-016` | What partner reporting files or APIs are required for reconciliation and compliance records? | Finance / Engineering | High | Open |
| `OQ-DOC03-017` | What disclosures are legally and contractually required at checkout, request review, receipt, and payee communications? | Legal / Product | High | Open |
| `OQ-DOC03-018` | What contract provisions are non-negotiable for PSP/acquirer/payout provider agreements? | Legal / Payments | Medium | Open |
| `OQ-DOC03-019` | Are payee-created payment requests included in MVP, pilot, or post-MVP scope from a regulatory and partner perspective? | Project Owner / Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-020` | Which payee types can be onboarded to create payment requests? | Product / Legal / Compliance / Risk | Critical | Open |
| `OQ-DOC03-021` | Are onboarded payees treated as merchants, sub-merchants, billers, beneficiaries, agents, customers, platform participants, or another role? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-022` | Does enabling payee-created requests require PayFac, marketplace, platform, agent, or additional payment service treatment? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC03-023` | Do PSP/acquirer and payout partners approve payee-created bill, invoice, fee, or rent request flows? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-024` | Is landlord-created rent request creation approved or deferred? | Product / Legal / Risk / Payments | Critical | Open |
| `OQ-DOC03-025` | What landlord onboarding, identity, property, payout, sanctions, and tenancy evidence checks are required? | Legal / Compliance / Risk | Critical | Open |
| `OQ-DOC03-026` | Could landlord-created rent requests create landlord/tenant, rent collection, or debt collection implications? | Legal / Compliance | High | Open |
| `OQ-DOC03-027` | What invoice evidence and KYB/KYC requirements apply to payee-created invoice or fee requests? | Compliance / Risk / Legal | High | Open |
| `OQ-DOC03-028` | How must payer authorization be captured for payee-created requests to satisfy legal, partner, dispute, and chargeback requirements? | Legal / Payments / Product | Critical | Open |
| `OQ-DOC03-029` | What information from a payee-created request may be shown to payer, and what payer information may be shown to payee? | Privacy / Security / Legal | High | Open |
| `OQ-DOC03-030` | What pre-authorization rejection, query, or dispute process is legally and operationally required? | Product / Legal / Operations | High | Open |
| `OQ-DOC03-031` | Are recurring payee-created requests permitted, or must each request require separate payer authorization? | Legal / Payments / Product | High | Open |
| `OQ-DOC03-032` | What payee-created request monitoring is required for fake invoices, fake rent, related-party abuse, spam, complaints, and chargebacks? | Risk / Compliance / Operations | Critical | Open |
| `OQ-DOC03-033` | Are payee onboarding, request, payout, subscription, platform, or other payee-side fees legally and contractually permitted? | Legal / Finance / Commercial | High | Open |
| `OQ-DOC03-034` | What partner contract terms are required for payee onboarding, payee-created requests, payee monitoring, and payee offboarding? | Legal / Payments / Commercial | High | Open |

---

## 31. Acceptance Criteria

`DOC-03` is acceptable when it clearly defines:

- Purpose and scope of regulatory, PSP, and acquirer assessment.
- Assessment triggers.
- Regulatory role assessment framework.
- Licensing and exemption considerations.
- Funds flow assessment requirements.
- Card network, PSP, and acquirer considerations.
- MCC and transaction classification considerations.
- Payee, request creator, and bill category assessment.
- Prohibited, restricted, and enhanced review category framework.
- PSP/acquirer/processor/gateway/payout provider due diligence requirements.
- Partner comparison scorecard.
- Required partner confirmations.
- Consumer protection and disclosure assessment.
- AML, sanctions, anti-cashout, collusion, and fraud assessment.
- Data protection, privacy, and security assessment.
- Contractual assessment.
- Settlement, reserve, holdback, and liquidity review.
- Multi-card and multi-source payment assessment.
- Payee-created request assessment.
- Landlord-created rent request assessment.
- Compliance readiness gates.
- Assessment template.
- Assumptions.
- Constraints.
- Dependencies.
- Risks.
- Downstream document impact.
- Open questions.

This document should remain an assessment framework and should not become a final legal opinion, compliance policy, partner contract, pricing sheet, product PRD, technical integration specification, risk rulebook, or operations SOP.

---

## 32. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-03 Regulatory, PSP & Acquirer Assessment. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation assessment framework, added triggers, role and licensing assessment, funds flow review, partner due diligence, scorecard, category restrictions, required confirmations, contractual assessment, compliance gates, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
| `0.3.0` | 2026-05-27 | Product Documentation Team | Updated assessment framework to account for payee onboarding and payee-created bill, invoice, fee, and rent payment request capability introduced in DOC-05 v0.2.0. Added request creator type assessment, payee role classification, PayFac/marketplace/platform implications, payer authorization assessment, payee-created request partner confirmations, landlord/rent assessment, payer/payee privacy boundaries, expanded risk, disclosure, contract, settlement, assumptions, constraints, dependencies, open questions, and readiness gates. |
