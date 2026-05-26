---
document_id: DOC-03
title: Regulatory, PSP & Acquirer Assessment
version: 0.2.0
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
last_updated: 2026-05-26
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User, Biller, Payee & Partner Onboarding
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-16 Security, Privacy & Data Protection
  - DOC-18 Data Model, Transaction Ledger & Reporting
---

# DOC-03 — Regulatory, PSP & Acquirer Assessment

## 1. Purpose

This document defines the assessment framework for determining whether PayPlus can legally, operationally, commercially, and contractually support a proposed bill payment product, payment flow, payee category, jurisdiction, payment service provider, acquirer, processor, payout provider, or related payment partner.

`DOC-03` is a foundation document.

It should be used before PayPlus launches, expands into a new jurisdiction, adds a bill category, changes a payment flow, changes its role in the funds flow, introduces multi-card or multi-source payment, or contracts with a new payment partner.

This document does not provide legal advice, regulatory conclusions, card network rule interpretations, accounting treatment, tax treatment, or final partner approval.

All such conclusions must be provided by qualified internal or external legal, compliance, payments, tax, accounting, and partner stakeholders.

---

## 2. Scope

This document covers:

- Regulatory role assessment.
- Licensing and exemption considerations.
- Money transmission and payment services considerations.
- Card network and acquirer considerations.
- PSP, acquirer, processor, gateway, and payout provider assessment.
- Merchant category code and transaction classification considerations.
- Payee and bill category acceptability.
- Funds flow and settlement model review.
- Payout model review.
- Multi-card or multi-source payment assessment.
- Consumer protection and fee disclosure assessment.
- AML, sanctions, fraud, anti-cashout, and risk considerations.
- Data protection and security due diligence.
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
- Final PSP or acquirer selection.
- Final commercial pricing.
- Final accounting policy.
- Final tax policy.
- Final technical architecture.
- Product requirements.
- Payment state machine.
- Reconciliation procedures.
- User disclosures.
- Customer support procedures.

These items must be defined in downstream documents, legal memoranda, compliance policies, partner contracts, or operating procedures.

---

## 4. Assessment Triggers

A `DOC-03` assessment should be performed or refreshed when any of the following occurs:

| Trigger ID | Trigger | Required Review |
| --- | --- | --- |
| `TRG-DOC03-001` | Launch of PayPlus MVP. | Full regulatory, PSP, acquirer, funds flow, and category assessment. |
| `TRG-DOC03-002` | New jurisdiction. | Legal, licensing, tax, data, and partner review. |
| `TRG-DOC03-003` | New bill category. | Category acceptability, MCC, risk, and partner review. |
| `TRG-DOC03-004` | New payee type. | Payee due diligence, payout, AML, and risk review. |
| `TRG-DOC03-005` | New payment method. | Partner, regulatory, fee disclosure, and technical review. |
| `TRG-DOC03-006` | Multi-card or multi-source payment launch. | Funds flow, acquirer, card network, refund, chargeback, and reconciliation review. |
| `TRG-DOC03-007` | Change to funds flow. | Legal, licensing, settlement, safeguarding, and partner review. |
| `TRG-DOC03-008` | Change to payout model. | Payout provider, risk, settlement, and reconciliation review. |
| `TRG-DOC03-009` | Change to pricing, fee, surcharge, or convenience fee model. | Legal, consumer protection, card network, and partner review. |
| `TRG-DOC03-010` | New PSP, acquirer, processor, gateway, or payout provider. | Vendor due diligence, compliance, security, commercial, and contract review. |
| `TRG-DOC03-011` | Partner reserve, holdback, or collateral requirement changes. | Finance, liquidity, legal, and risk review. |
| `TRG-DOC03-012` | Material increase in chargebacks, fraud, complaints, or payout failures. | Risk, compliance, acquirer, and operational review. |
| `TRG-DOC03-013` | Regulatory, card network, partner, or legal rule change. | Impact assessment and policy update. |

---

## 5. Regulatory Role Assessment

PayPlus must determine its regulatory role in each jurisdiction and payment flow.

Potential roles may include:

| Role | Description | Assessment Question |
| --- | --- | --- |
| Merchant of record | PayPlus is treated as merchant for card acceptance. | Is PayPlus selling a service, collecting funds, or facilitating bill payment as merchant? |
| Payment facilitator | PayPlus enables payment acceptance for third-party payees or sub-merchants. | Is PayPlus onboarding or processing for third-party payees? |
| Payment agent | PayPlus receives funds on behalf of biller or user. | Is PayPlus acting as agent for either party? |
| Money transmitter or payment service provider | PayPlus receives funds for transmission to another party. | Does the flow trigger licensing or registration obligations? |
| Stored value or e-money issuer | PayPlus holds user value for future use. | Are funds stored or redeemable later? |
| Marketplace or platform | PayPlus connects users and payees and facilitates payment. | Does the platform model trigger additional obligations? |
| Technical service provider | PayPlus provides technology but does not control funds. | Is PayPlus isolated from possession/control of funds? |
| Bill payment service provider | PayPlus provides a bill payment or payment initiation service. | Are specific bill payment regulations applicable? |

The legal conclusion may vary by jurisdiction, payment method, payee type, funds flow, contractual structure, and operational control.

No product flow should launch without documented role assessment.

---

## 6. Licensing and Exemption Considerations

Legal and Compliance must assess whether PayPlus requires licenses, registrations, exemptions, agent arrangements, sponsorships, or partner coverage.

Assessment areas include:

- Money transmission.
- Payment services.
- Payment initiation services.
- Bill payment services.
- Stored value or wallet services.
- E-money issuance.
- Prepaid access.
- Agent-of-the-payee models.
- Agent-of-the-user models.
- Payment facilitator registration.
- Marketplace payment facilitation.
- Cross-border payment services.
- FX or currency conversion.
- Consumer lending or credit, if payment timing creates credit exposure.
- Debt collection implications, if relevant.
- Charitable solicitation, if bill categories include donations.
- Insurance premium payment rules, if applicable.
- Education, rent, tax, utility, government, loan, or mortgage payment restrictions.
- State, federal, provincial, national, or regional requirements.
- Exemptions available through regulated partners.
- Contractual conditions required for an exemption.

Each jurisdiction and flow should have a documented conclusion or unresolved risk rating before launch.

---

## 7. Funds Flow Assessment

A funds flow diagram and written description must be prepared for each payment model.

The assessment should identify:

- Who the user pays.
- Who is merchant of record.
- Who submits card authorization.
- Who captures the card payment.
- Who receives settlement from the acquirer or PSP.
- Whether funds enter PayPlus-controlled accounts.
- Whether funds are commingled or segregated.
- Whether funds are safeguarded or held for benefit of users/payees.
- Whether PayPlus has discretion over funds.
- Who initiates payout.
- Who is the payout recipient.
- Whether payout occurs before card settlement.
- Whether PayPlus prefunds payout.
- Whether partner holds reserves.
- Whether refunds are possible after payout.
- Whether chargeback liability remains after payout.
- Whether users receive stored balance, credits, or wallet value.
- Whether funds cross borders.
- Whether FX occurs.
- How failed, reversed, cancelled, refunded, or charged-back transactions are handled.

Funds flow design must be consistent with legal conclusions, PSP/acquirer rules, accounting treatment, and operational capabilities.

---

## 8. Card Network, PSP, and Acquirer Considerations

PayPlus must assess whether proposed flows are acceptable to card networks, PSPs, acquirers, and processors.

Assessment areas include:

| Area | Review Question |
| --- | --- |
| Merchant classification | What is the appropriate merchant category code or transaction classification? |
| Prohibited use cases | Is bill payment or the target bill category restricted or prohibited? |
| Cash-like transactions | Could the flow be considered cash disbursement, quasi-cash, money transfer, or cash equivalent? |
| Surcharging and convenience fees | Are user-paid service fees permitted under applicable rules and law? |
| Payment facilitator model | Is PayPlus acting as a payment facilitator or marketplace? |
| Sub-merchant model | Are billers or payees treated as sub-merchants? |
| Account funding transaction | Could the payment be treated as funding an account, wallet, or transfer? |
| Original credit transaction | Are payouts supported via card rails, if applicable? |
| Multi-card payment | Are split payments over multiple cards allowed? |
| Partial authorization | Is partial authorization supported or prohibited? |
| Delayed capture | Is capture timing allowed for the flow? |
| Refund after payout | Can refunds be processed if payout already occurred? |
| Chargeback evidence | Can PayPlus provide sufficient evidence of user authorization and service delivery? |
| Cardholder disclosure | Are fees and payment timing clearly disclosed? |
| Recurring payments | Are recurring or scheduled payments supported? |
| High-risk category | Does the category trigger enhanced underwriting or reserves? |
| Geographic restrictions | Are specific countries, states, or territories unsupported? |
| Brand rules | Are card brand-specific requirements applicable? |

Payments, Legal, and Compliance must obtain written partner confirmation for material assumptions where possible.

---

## 9. Merchant Category Code and Transaction Classification

MCC and transaction classification may affect:

- Interchange and scheme fees.
- User card rewards eligibility.
- Cash advance treatment.
- Issuer authorization behavior.
- Risk scoring.
- Card network compliance.
- PSP/acquirer underwriting.
- User complaints.
- Dispute handling.
- Commercial viability.

PayPlus should document:

- Proposed MCC or classification.
- Rationale.
- PSP/acquirer confirmation.
- Card network restrictions, if any.
- Whether transactions may be treated as quasi-cash or money transfer.
- Whether issuer cash advance fees may apply.
- Whether user-facing disclosure is required.
- Whether classification varies by category or payee type.
- Impact on pricing and unit economics.

Final classification should be confirmed with the PSP/acquirer before launch.

---

## 10. Payee and Bill Category Assessment

Each bill category and payee type should be assessed for regulatory, partner, operational, and risk acceptability.

Candidate assessment dimensions:

| Dimension | Questions |
| --- | --- |
| Legal permissibility | Is the category legally permitted in the launch jurisdiction? |
| Partner acceptability | Does the PSP/acquirer/payout provider allow this category? |
| MCC fit | Is there an acceptable transaction classification? |
| Risk level | Does the category increase fraud, cashout, or chargeback risk? |
| Consumer protection | Are special disclosures or cancellation rights required? |
| Payee verification | Can the payee be verified sufficiently? |
| Payout feasibility | Can PayPlus pay the biller or payee reliably? |
| Refund feasibility | Can payments be reversed or refunded if needed? |
| Evidence quality | Can PayPlus prove service delivery and user authorization? |
| Operational complexity | Does the category require manual review or custom routing? |
| Economics | Does the category meet contribution margin thresholds? |
| Complaint risk | Is the category likely to create user complaints? |

High-risk or restricted categories should require explicit approval before launch.

---

## 11. Prohibited, Restricted, and Enhanced Review Categories

PayPlus should maintain category lists for:

- Prohibited categories.
- Restricted categories.
- Enhanced review categories.
- Approved MVP categories.
- Approved partner-specific categories.
- Jurisdiction-specific restricted categories.

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
- Donations.
- Crypto-related payments.
- Gambling-related payments.
- Investment-related payments.
- Money transfer.
- Cash equivalent purchases.
- Gift cards or stored value.
- Person-to-person payments.
- Self-payments or payments to user-controlled entities.

Final prohibited and restricted category lists must be approved by Legal, Compliance, Payments, Risk, and relevant partners.

---

## 12. PSP, Acquirer, Processor, Gateway, and Payout Provider Due Diligence

Partner due diligence should cover:

| Area | Required Review |
| --- | --- |
| Regulatory status | Licenses, registrations, sponsorship model, jurisdiction coverage. |
| Product support | Support for bill payment, multi-card, refunds, chargebacks, payouts, and reporting. |
| Category support | Approved and prohibited categories. |
| Card network coverage | Supported card brands, regions, issuer routing, scheme capabilities. |
| Pricing | Authorization, capture, processing, gateway, refund, chargeback, payout, FX, monthly, minimum, and setup fees. |
| Settlement | Settlement timing, reserves, holdbacks, minimum balances, prefunding, collateral. |
| Risk controls | Fraud tools, transaction monitoring, velocity limits, rule configuration. |
| Chargebacks | Dispute process, evidence submission, representment support, deadlines, fees. |
| Payout capabilities | Bank transfer, instant payout, card payout, local rails, cross-border rails, settlement reports. |
| Reconciliation | Reporting files, webhooks, transaction IDs, payout IDs, fee reports, balance reports. |
| Security | PCI DSS status, SOC reports, ISO certifications, penetration testing, encryption. |
| Privacy | Data processing agreement, sub-processors, data residency, retention, deletion. |
| Reliability | SLAs, uptime history, incident process, status page, support model. |
| Integration | APIs, SDKs, webhooks, idempotency, sandbox, testing tools. |
| Contract | Liability, indemnity, termination, audit rights, data rights, change notice, prohibited use. |
| Operational support | Escalation process, account management, implementation support. |

Due diligence results should be stored in the vendor and compliance records.

---

## 13. Partner Comparison Scorecard

A partner comparison scorecard should be used where multiple PSPs/acquirers/payout providers are considered.

| Criterion | Weight | Provider A | Provider B | Provider C | Notes |
| --- | ---: | ---: | ---: | ---: | --- |
| Regulatory coverage | TBD | TBD | TBD | TBD |  |
| Bill payment acceptability | TBD | TBD | TBD | TBD |  |
| Category support | TBD | TBD | TBD | TBD |  |
| Multi-card support | TBD | TBD | TBD | TBD |  |
| Payout capabilities | TBD | TBD | TBD | TBD |  |
| Refund and chargeback support | TBD | TBD | TBD | TBD |  |
| Reconciliation quality | TBD | TBD | TBD | TBD |  |
| Pricing | TBD | TBD | TBD | TBD |  |
| Settlement timing | TBD | TBD | TBD | TBD |  |
| Reserve requirements | TBD | TBD | TBD | TBD |  |
| Fraud tools | TBD | TBD | TBD | TBD |  |
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
- Approved jurisdictions.
- Approved bill categories.
- Prohibited categories.
- Merchant of record structure.
- PayFac or marketplace implications.
- MCC or transaction classification.
- Whether the transaction may be treated as cash-like, quasi-cash, account funding, or money transfer.
- User fee, convenience fee, or surcharge restrictions.
- Multi-card or split payment support.
- Authorization and capture timing.
- Refund and reversal support.
- Chargeback process and liability.
- Payout method and settlement timing.
- Reserve, holdback, prefunding, or collateral requirements.
- Reporting and reconciliation data availability.
- Data protection and security commitments.
- Operational support and escalation process.
- Contractual change notice obligations.

Where written confirmation cannot be obtained, the assumption should be logged as an open risk.

---

## 15. Consumer Protection and Disclosure Assessment

Legal, Compliance, and Product should assess whether user disclosures adequately cover:

- PayPlus role.
- Bill amount.
- Service fee.
- Taxes, if applicable.
- Total amount charged.
- Payee or biller details.
- Estimated processing time.
- Whether payment is guaranteed or conditional.
- Refund and cancellation rules.
- Failed payment behavior.
- Chargeback and dispute rights.
- Promotion terms.
- Card statement descriptor.
- Potential card issuer fees, if applicable and known.
- User responsibility for late fees from billers.
- Data use and privacy.
- Customer support contact.
- Terms acceptance.

Detailed content requirements belong in:

- `DOC-07 Content, Disclosure & User Communication`.
- `DOC-08 Notification, Receipt & Communication Rules`.

---

## 16. AML, Sanctions, Anti-Cashout, and Fraud Assessment

PayPlus must assess whether the product flow creates AML, sanctions, fraud, cashout, or abuse risk.

Assessment areas include:

- User identity verification requirements.
- Payee verification requirements.
- Beneficial ownership review, where applicable.
- Sanctions screening.
- PEP screening, if applicable.
- Adverse media review, if applicable.
- Transaction monitoring.
- Velocity limits.
- Category limits.
- Payee limits.
- User limits.
- Self-payment detection.
- Circular payment detection.
- Card testing detection.
- Stolen card fraud detection.
- Account takeover detection.
- First-party misuse.
- Synthetic identity risk.
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
- User consent.
- Privacy notice coverage.
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

Detailed requirements belong in `DOC-16 Security, Privacy & Data Protection`.

---

## 18. Contractual Assessment

Partner contracts should be reviewed for:

| Contract Area | Review Focus |
| --- | --- |
| Scope of services | Does the contract clearly allow PayPlus use case and categories? |
| Role definitions | Are merchant, platform, agent, processor, and data roles clear? |
| Regulatory responsibility | Who is responsible for licenses, KYC, AML, sanctions, reporting, and complaints? |
| Card network compliance | Who is responsible for network rule compliance and fines? |
| Pricing | Are all fees, minimums, and pass-through charges documented? |
| Reserves | Are reserves, holdbacks, collateral, and prefunding terms clear? |
| Settlement | Are settlement timing and funding obligations clear? |
| Chargebacks | Are liability, fees, deadlines, evidence, and representment rights clear? |
| Refunds | Are refund rights, timing, and fees clear? |
| Payouts | Are payout responsibilities, failures, reversals, and recalls clear? |
| Data protection | Are controller/processor roles, DPA, sub-processors, and breach notices clear? |
| Security | Are PCI, audits, penetration testing, and security controls addressed? |
| SLAs | Are uptime, support, incident response, and escalation commitments defined? |
| Reporting | Are transaction, fee, dispute, payout, balance, and reconciliation reports required? |
| Audit rights | Can PayPlus audit relevant compliance, security, and financial records? |
| Change notice | Must partner notify PayPlus of pricing, rule, reserve, or capability changes? |
| Termination | Are suspension, termination, migration, and wind-down rights acceptable? |
| Indemnity and liability | Are liability caps, exclusions, and indemnities acceptable? |
| Assignment and subcontracting | Can partner change processors or subcontractors without approval? |
| Governing law | Is governing law acceptable for the launch model? |

Legal approval is required before signing any material payment partner agreement.

---

## 19. Settlement, Reserve, Holdback, and Liquidity Review

Finance and Payments must assess:

- Settlement timing.
- Funding availability.
- Payout timing.
- Whether payout occurs before card settlement.
- Reserve percentage.
- Rolling reserve period.
- Holdback amount.
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

This review should be aligned with `DOC-02 Business Model & Unit Economics`.

---

## 20. Multi-Card and Multi-Source Payment Assessment

If PayPlus supports multi-card or multi-source payments, the assessment must include:

- Whether PSP/acquirer supports split funding.
- Whether multiple authorizations may fund one bill.
- Whether partial authorization is supported.
- Whether PayPlus may hold partial funds while completing other authorizations.
- Whether failed partial funding requires reversal or cancellation.
- How service fees are calculated.
- How fees are allocated across funding sources.
- How refunds are allocated across funding sources.
- How chargebacks are handled when only one funding source disputes.
- Whether the biller receives one payout or multiple payouts.
- How reconciliation links parent bill payment to child funding events.
- How promotion eligibility is calculated.
- Whether multi-card increases AML or cashout risk.
- Whether multi-card changes licensing or funds control analysis.
- Whether additional disclosures are required.

Detailed requirements belong in:

- `DOC-09 Payment Request, Multi-Funding Source & Settlement`.
- `DOC-11 Refund, Cancellation & Chargeback`.
- `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 21. Compliance Readiness Gates

PayPlus should not launch a jurisdiction, category, payment method, payment partner, or funds flow until applicable compliance readiness gates are satisfied.

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC03-001` | Regulatory role assessed | Legal/Compliance documents PayPlus role for the flow and jurisdiction. |
| `GATE-DOC03-002` | Licensing path confirmed | Required licenses, exemptions, sponsorships, or partner coverage are documented. |
| `GATE-DOC03-003` | Funds flow approved | Funds flow diagram and description are approved by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-004` | PSP/acquirer acceptability confirmed | Partner confirms use case, category, MCC/classification, and flow support. |
| `GATE-DOC03-005` | Payout model approved | Payout method, provider, timing, failures, and reversals are assessed. |
| `GATE-DOC03-006` | Category restrictions defined | Approved, restricted, and prohibited categories are documented. |
| `GATE-DOC03-007` | Fee model reviewed | User fee, surcharge, convenience fee, or pricing model is reviewed by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-008` | AML/risk assessment completed | AML, sanctions, fraud, anti-cashout, and abuse risks are assessed. |
| `GATE-DOC03-009` | Security/privacy review completed | PCI, privacy, security, and data protection reviews are completed. |
| `GATE-DOC03-010` | Partner due diligence completed | Vendor, regulatory, commercial, security, and contract reviews are completed. |
| `GATE-DOC03-011` | Contract approved | Legal approves partner contract and required provisions. |
| `GATE-DOC03-012` | Settlement/reserve impact approved | Finance approves settlement timing, reserves, holdbacks, and liquidity impact. |
| `GATE-DOC03-013` | Disclosure requirements identified | Required user disclosures are identified for product implementation. |
| `GATE-DOC03-014` | Reporting and recordkeeping defined | Required transaction, compliance, dispute, and reconciliation records are identified. |
| `GATE-DOC03-015` | Launch approval obtained | Required approvers sign off before launch. |

---

## 22. Assessment Template

Each assessed flow, partner, category, or jurisdiction should include the following template.

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
- User journey:
- Card/funding flow:
- Payout flow:
- Refund flow:
- Chargeback flow:

3. Regulatory Role Assessment
- PayPlus role:
- Partner role:
- Payee role:
- User role:
- Open legal questions:

4. Licensing / Exemption Analysis
- Required license or registration:
- Exemption or sponsorship:
- Conditions:
- Gaps:

5. Partner Acceptability
- PSP/acquirer confirmation:
- Payout provider confirmation:
- MCC/classification:
- Restricted categories:
- Conditions:

6. Fee and Disclosure Review
- User fee:
- Partner fee:
- Tax:
- Required disclosures:
- Restrictions:

7. Risk and Compliance Review
- AML risk:
- Sanctions risk:
- Fraud risk:
- Cashout risk:
- Chargeback risk:
- Controls required:

8. Data, Privacy, and Security Review
- PCI impact:
- Personal data:
- Sensitive data:
- Data transfers:
- Security requirements:
- Partner obligations:

9. Commercial and Settlement Review
- Processing cost:
- Payout cost:
- Reserve:
- Holdback:
- Settlement timing:
- Liquidity impact:

10. Operational Review
- Manual review required:
- Support impact:
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
```

---

## 23. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC03-001` | PayPlus will require a documented legal role assessment before launch. | Legal / Compliance | Open |
| `ASM-DOC03-002` | PSP/acquirer approval will be required for the PayPlus bill payment use case. | Payments | Open |
| `ASM-DOC03-003` | MCC or transaction classification will materially affect cost, risk, and cardholder experience. | Payments / Finance | Open |
| `ASM-DOC03-004` | Some bill categories may be prohibited or restricted by partners. | Compliance / Payments | Open |
| `ASM-DOC03-005` | Multi-card or split funding may require additional partner approval. | Payments / Product | Open |
| `ASM-DOC03-006` | User fee or convenience fee rules may vary by jurisdiction and partner. | Legal / Compliance | Open |
| `ASM-DOC03-007` | Settlement timing and reserves may materially affect launch feasibility. | Finance / Payments | Open |
| `ASM-DOC03-008` | Payee verification requirements may vary by category and payout model. | Compliance / Risk | Open |
| `ASM-DOC03-009` | Partner contracts will define key operating constraints. | Legal / Commercial | Open |
| `ASM-DOC03-010` | Regulatory conclusions may change if funds flow changes. | Legal / Compliance | Open |

---

## 24. Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC03-001` | No launch without documented regulatory role assessment. | Prevents unassessed legal exposure. | Legal / Compliance |
| `CON-DOC03-002` | No launch without PSP/acquirer approval or acceptable documented assumption. | Prevents partner rule breach. | Payments |
| `CON-DOC03-003` | No restricted category launch without explicit approval. | Prevents unsupported or high-risk use cases. | Compliance / Risk |
| `CON-DOC03-004` | Fee model must be reviewed before implementation. | Prevents unlawful or prohibited fees. | Legal / Compliance |
| `CON-DOC03-005` | Funds flow cannot change without reassessment. | Prevents licensing and partner mismatch. | Legal / Payments |
| `CON-DOC03-006` | Partner contracts must support operational requirements. | Prevents gaps in refunds, chargebacks, reporting, and settlement. | Legal / Payments |
| `CON-DOC03-007` | AML, sanctions, fraud, and anti-cashout controls must be appropriate to flow risk. | Prevents financial crime and partner risk. | Compliance / Risk |
| `CON-DOC03-008` | Security and privacy review is required for payment partners. | Prevents data protection and PCI gaps. | Security / Privacy |
| `CON-DOC03-009` | Settlement and reserve terms must be approved by Finance. | Prevents liquidity surprises. | Finance |
| `CON-DOC03-010` | Required disclosures must be implemented before launch. | Prevents consumer protection and complaint risk. | Product / Legal |

---

## 25. Dependencies

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

---

## 26. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC03-001` | PayPlus launches with incorrect regulatory role classification. | Licensing breach, enforcement, partner termination. | Obtain legal assessment per jurisdiction and flow. | Legal / Compliance | Open |
| `RISK-DOC03-002` | Product flow is treated as money transmission or payment service requiring licensing. | Launch delay, regulatory risk, operating restrictions. | Evaluate exemptions, partner sponsorship, or licensed provider model. | Legal / Compliance | Open |
| `RISK-DOC03-003` | PSP/acquirer rejects bill payment or target category after integration. | Launch delay and rework. | Obtain written partner confirmation early. | Payments / Commercial | Open |
| `RISK-DOC03-004` | Transactions are classified as quasi-cash, cash advance, or money transfer. | Higher costs, issuer declines, user complaints. | Confirm MCC/classification and add disclosures if required. | Payments / Legal | Open |
| `RISK-DOC03-005` | User fee model violates law, network rules, or partner restrictions. | Fines, refunds, product redesign. | Legal, card network, and partner fee review before launch. | Legal / Payments | Open |
| `RISK-DOC03-006` | Multi-card funding creates unsupported funds flow or refund complexity. | Compliance, operational, and reconciliation failures. | Require dedicated multi-card assessment and partner approval. | Product / Payments | Open |
| `RISK-DOC03-007` | Partner reserves or holdbacks create liquidity strain. | Working capital pressure and growth limits. | Model reserve impact and obtain Finance approval. | Finance / Payments | Open |
| `RISK-DOC03-008` | Inadequate payee verification enables fraud or cashout. | Financial loss and regulatory risk. | Implement payee verification and anti-cashout controls. | Risk / Compliance | Open |
| `RISK-DOC03-009` | Partner contract lacks required reporting or chargeback support. | Reconciliation gaps and loss exposure. | Contractual checklist and Legal review. | Legal / Payments | Open |
| `RISK-DOC03-010` | Privacy, PCI, or security obligations are underestimated. | Breach, compliance failure, remediation cost. | Security/privacy due diligence and PCI scope review. | Security / Privacy | Open |
| `RISK-DOC03-011` | Required user disclosures are incomplete or unclear. | Complaints, disputes, regulatory risk. | Legal review of checkout, receipt, and terms content. | Product / Legal | Open |
| `RISK-DOC03-012` | Regulatory or network rule changes affect approved flows. | Product restrictions or operational changes. | Maintain periodic review and partner change notice monitoring. | Compliance / Payments | Open |

---

## 27. Downstream Document Impact

DOC-03 should guide downstream documents as follows:

| Downstream Document | Impact |
| --- | --- |
| `DOC-04` | Compliance readiness gates, certifications, controls, evidence, and launch approvals should reflect regulatory and partner assessment outputs. |
| `DOC-05` | Product requirements must incorporate approved payment methods, categories, partner constraints, disclosures, and flow limitations. |
| `DOC-06` | User, biller, payee, and partner onboarding requirements should reflect verification, eligibility, and restricted category decisions. |
| `DOC-07` | User-facing fee, timing, role, refund, risk, and issuer-fee disclosures must reflect legal and partner findings. |
| `DOC-08` | Receipts and notifications must include required transaction, fee, timing, and failure information. |
| `DOC-09` | Payment request and settlement design must comply with approved funds flow, partner constraints, and multi-card limitations. |
| `DOC-10` | Payout and reconciliation must reflect approved payout provider, settlement timing, reserves, and reporting files. |
| `DOC-11` | Refund, cancellation, chargeback, and dispute logic must reflect partner capabilities and liability allocation. |
| `DOC-14` | AML, sanctions, fraud, cashout, and abuse controls must reflect risks identified in this assessment. |
| `DOC-16` | Security, privacy, PCI, and partner data protection requirements must reflect provider due diligence and flow design. |
| `DOC-18` | Ledger and reporting must capture fields needed for regulatory records, partner reporting, disputes, reconciliation, and margin analysis. |
| `DOC-20` | Launch checklist must include completion of relevant `DOC-03` gates and approvals. |
| `DOC-21` | Runbooks must include monitoring for partner restrictions, settlement issues, chargebacks, category violations, and compliance incidents. |

---

## 28. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC03-001` | What jurisdictions will PayPlus launch in first? | Project Owner / Legal | Critical | Open |
| `OQ-DOC03-002` | What legal role will PayPlus take in the MVP funds flow? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-003` | Does the MVP funds flow require money transmission, payment service, or similar licensing? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-004` | Can PayPlus rely on a regulated partner, exemption, or agent model? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-005` | Which PSP/acquirer will support the bill payment use case? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-006` | What MCC or transaction classification will apply? | Payments | Critical | Open |
| `OQ-DOC03-007` | Will transactions be treated as purchase, quasi-cash, money transfer, or account funding? | Payments / Legal | Critical | Open |
| `OQ-DOC03-008` | Are user-paid service fees, convenience fees, or surcharges permitted? | Legal / Payments | Critical | Open |
| `OQ-DOC03-009` | Which bill categories are approved, restricted, or prohibited for MVP? | Compliance / Risk / Product | Critical | Open |
| `OQ-DOC03-010` | What payee verification is required before payout? | Risk / Compliance | High | Open |
| `OQ-DOC03-011` | What payout provider and payout rail will be used? | Payments / Commercial | High | Open |
| `OQ-DOC03-012` | What settlement timing, reserves, holdbacks, or prefunding will apply? | Finance / Payments | High | Open |
| `OQ-DOC03-013` | Are multi-card or multi-source payments supported by the PSP/acquirer and legally acceptable? | Product / Payments / Legal | High | Open |
| `OQ-DOC03-014` | What AML, sanctions, fraud, and anti-cashout controls are required before MVP? | Compliance / Risk | Critical | Open |
| `OQ-DOC03-015` | What PCI, privacy, security, and data protection requirements apply? | Security / Privacy | High | Open |
| `OQ-DOC03-016` | What partner reporting files or APIs are required for reconciliation and compliance records? | Finance / Engineering | High | Open |
| `OQ-DOC03-017` | What disclosures are legally and contractually required at checkout and receipt? | Legal / Product | High | Open |
| `OQ-DOC03-018` | What contract provisions are non-negotiable for PSP/acquirer/payout provider agreements? | Legal / Payments | Medium | Open |

---

## 29. Acceptance Criteria

DOC-03 is acceptable when it clearly defines:

- Purpose and scope of regulatory, PSP, and acquirer assessment.
- Assessment triggers.
- Regulatory role assessment framework.
- Licensing and exemption considerations.
- Funds flow assessment requirements.
- Card network, PSP, and acquirer considerations.
- MCC and transaction classification considerations.
- Payee and bill category assessment.
- Prohibited, restricted, and enhanced review category framework.
- PSP/acquirer/processor/gateway/payout provider due diligence requirements.
- Partner comparison scorecard.
- Required partner confirmations.
- Consumer protection and disclosure assessment.
- AML, sanctions, anti-cashout, and fraud assessment.
- Data protection, privacy, and security assessment.
- Contractual assessment.
- Settlement, reserve, holdback, and liquidity review.
- Multi-card and multi-source payment assessment.
- Compliance readiness gates.
- Assessment template.
- Assumptions.
- Constraints.
- Dependencies.
- Risks.
- Downstream document impact.
- Open questions.

This document should remain an assessment framework and should not become a final legal opinion, compliance policy, partner contract, pricing sheet, product PRD, or technical integration specification.

---

## 30. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-03 Regulatory, PSP & Acquirer Assessment. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation assessment framework, added triggers, role and licensing assessment, funds flow review, partner due diligence, scorecard, category restrictions, required confirmations, contractual assessment, compliance gates, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
