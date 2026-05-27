---
document_id: DOC-03
title: Regulatory, PSP & Acquirer Assessment
version: 0.4.0
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

## 1. Purpose

This document defines the assessment framework for determining whether PayPlus can legally, operationally, commercially, and contractually support a proposed payment flow, bill category, payee type, request creator model, jurisdiction, payment partner, or payout model.

`DOC-03` is a foundation document.

It should be used before PayPlus:

- launches MVP;
- enters a new jurisdiction;
- adds a bill category;
- adds a payee type;
- enables payee-created payment requests;
- changes funds flow;
- changes payout flow;
- introduces multi-card or multi-source funding;
- changes fee model;
- contracts with a PSP, acquirer, processor, gateway, payout provider, or other payment partner.

This document does not provide legal advice, final regulatory conclusions, card network rule interpretations, accounting treatment, tax treatment, or final partner approval.

Those conclusions must be provided by qualified Legal, Compliance, Payments, Finance, Tax, Risk, Security, Privacy, and partner stakeholders.

---

## 2. Assessment Principle

Payee-created requests change who creates the request, but they must not weaken regulatory, PSP/acquirer, payout, evidence, authorization, risk, reconciliation, privacy, or recordkeeping controls.

No PayPlus flow should launch unless the relevant model has been assessed and approved by the required stakeholders.

At minimum, every assessed flow must answer:

- What is PayPlus’s regulatory and contractual role?
- Who is the payer paying?
- Who receives funds?
- Who controls funds?
- Who is merchant of record, if applicable?
- Is a license, registration, exemption, agency model, sponsorship, PayFac model, marketplace model, or partner coverage required?
- Does the PSP/acquirer support the use case?
- Does the payout provider support the payout flow?
- Are fees, disclosures, privacy boundaries, risk controls, and records sufficient?

---

## 3. Scope

This document covers:

- regulatory role assessment;
- licensing and exemption considerations;
- funds flow and settlement review;
- PSP, acquirer, processor, gateway, and payout provider assessment;
- card network and transaction classification considerations;
- MCC review;
- bill category, payee type, and request creator assessment;
- payee onboarding implications;
- payee-created request assessment;
- landlord-created rent request assessment;
- invoice and business-payee request assessment;
- consumer protection and disclosure assessment;
- AML, sanctions, fraud, anti-cashout, collusion, and request-abuse assessment;
- data protection, privacy, security, and PCI assessment;
- partner due diligence;
- contractual assessment;
- reserve, holdback, collateral, and liquidity review;
- multi-card and multi-source payment assessment;
- compliance readiness gates;
- assumptions, constraints, dependencies, risks, and open questions.

---

## 4. Out of Scope

This document does not define:

- final legal opinion;
- final licensing strategy;
- final compliance policy;
- final AML, sanctions, or fraud rules;
- final payee onboarding policy;
- final landlord or invoice verification standard;
- final PSP/acquirer/payout provider selection;
- final commercial pricing;
- final accounting or tax policy;
- product requirements;
- payment state machine;
- reconciliation procedures;
- user, payer, or payee disclosure copy;
- customer or payee support procedures.

These items must be defined in downstream documents, legal memoranda, partner contracts, policies, or operating procedures.

---

## 5. Assessment Triggers

A `DOC-03` assessment must be performed or refreshed when any material product, legal, partner, or funds-flow condition changes.

| Trigger ID | Trigger | Required Review |
| --- | --- | --- |
| `TRG-DOC03-001` | MVP launch. | Full regulatory, funds flow, partner, category, request creator, payee type, and payout assessment. |
| `TRG-DOC03-002` | New jurisdiction. | Legal, licensing, tax, data, and partner review. |
| `TRG-DOC03-003` | New bill category. | Category acceptability, MCC, evidence, payee, partner, and risk review. |
| `TRG-DOC03-004` | New payee type. | Payee due diligence, role, payout, AML, risk, privacy, and partner review. |
| `TRG-DOC03-005` | New payment method. | Partner, regulatory, fee, disclosure, and technical review. |
| `TRG-DOC03-006` | Multi-card or multi-source funding. | Funds flow, partner, authorization, refund, chargeback, risk, and reconciliation review. |
| `TRG-DOC03-007` | Funds flow change. | Legal, licensing, settlement, safeguarding, and partner review. |
| `TRG-DOC03-008` | Payout model change. | Payout provider, risk, settlement, liquidity, and reconciliation review. |
| `TRG-DOC03-009` | Pricing or fee model change. | Legal, consumer protection, card network, partner, accounting, and tax review. |
| `TRG-DOC03-010` | New PSP, acquirer, processor, gateway, or payout provider. | Vendor, compliance, security, commercial, and contract review. |
| `TRG-DOC03-011` | Reserve, holdback, collateral, or settlement change. | Finance, liquidity, legal, and risk review. |
| `TRG-DOC03-012` | Material increase in chargebacks, fraud, complaints, disputes, request abuse, or payout failures. | Risk, compliance, partner, and operational review. |
| `TRG-DOC03-013` | Regulatory, card network, partner, or legal rule change. | Impact assessment and required updates. |
| `TRG-DOC03-014` | Payee-created request enablement. | Role, PayFac/marketplace, partner, payee onboarding, payer authorization, risk, payout, privacy, fee, and contract review. |
| `TRG-DOC03-015` | Landlord-created rent requests. | Landlord onboarding, tenancy evidence, payer-landlord relationship, anti-collusion, payout, partner, and disclosure review. |
| `TRG-DOC03-016` | Payee-created invoice, fee, or business requests. | Business role, invoice evidence, KYB/KYC, invoice fraud, partner, chargeback, and dispute review. |
| `TRG-DOC03-017` | Payee capability permission change. | Regulatory role, partner approval, risk, privacy, and support review. |

---

## 6. Regulatory Role Assessment

PayPlus must determine its role for each jurisdiction, funds flow, category, payee type, and request creator model.

Potential roles include:

| Role | Assessment Question |
| --- | --- |
| Merchant of record | Is PayPlus treated as merchant for card acceptance? |
| Payment facilitator | Is PayPlus enabling payment acceptance for third-party payees or sub-merchants? |
| Sub-merchant platform | Are payees treated as sub-merchants under a PSP/acquirer or PayFac model? |
| Marketplace or platform | Does PayPlus connect payers and payees and facilitate payment? |
| Agent of the payee | Does PayPlus receive payment on behalf of payee, and when is payer obligation discharged? |
| Agent of the payer | Does PayPlus act for payer to transmit payment to payee? |
| Money transmitter or payment service provider | Does PayPlus receive funds for transmission to another party? |
| Stored value or e-money issuer | Does PayPlus hold user or payee value for later use? |
| Technical service provider | Does PayPlus provide technology without possession or control of funds? |
| Bill payment service provider | Does PayPlus provide regulated bill payment or payment initiation services? |
| Debt collection or collection agent | Could overdue invoices, rent, or fees create collection implications? |
| Request-to-pay provider | Does PayPlus facilitate requests for payment without being the underlying payee? |

For payee-created requests, assessment must specifically determine:

- whether the payee is a merchant, sub-merchant, biller, beneficiary, landlord, agent, platform participant, customer, or other role;
- whether PayPlus is facilitating payment acceptance for third-party payees;
- whether payee onboarding creates PayFac, marketplace, or platform obligations;
- whether PayPlus has possession or control of payer or payee funds;
- when the payer’s obligation to the payee is discharged;
- whether request messaging creates consumer protection, debt collection, or unfair-practice risk;
- whether rent, invoice, education, utility, or fee requests require category-specific legal treatment.

No product flow should launch without a documented role assessment.

---

## 7. Licensing and Exemption Assessment

Legal and Compliance must assess whether PayPlus requires or can rely on:

- money transmission license;
- payment services license or registration;
- bill payment service authorization;
- payment initiation or request-to-pay authorization;
- stored value, wallet, or e-money authorization;
- PayFac registration;
- sub-merchant onboarding arrangement;
- marketplace or platform payment model;
- agent-of-payee arrangement;
- agent-of-payer arrangement;
- commercial agent exemption;
- regulated partner sponsorship;
- licensed partner coverage;
- cross-border payment authorization;
- FX authorization;
- consumer lending or credit analysis, if payout timing creates credit exposure;
- debt collection analysis, if applicable;
- rent, invoice, education, utility, insurance, tax, government, loan, mortgage, or other category-specific review.

Each jurisdiction, category, payee type, request creator model, and flow should have a documented conclusion or unresolved risk rating before launch.

---

## 8. Funds Flow Assessment

A funds flow diagram and written description must be prepared for each payment model.

The assessment must identify:

- who creates the request;
- whether the request is payer-created, payee-created, admin-created, partner-created, or system-created;
- who the payer believes they are paying;
- who the payer legally pays;
- who is merchant of record, if applicable;
- who submits authorization and capture;
- who receives PSP/acquirer settlement;
- whether funds enter PayPlus-controlled accounts;
- whether funds are commingled, segregated, safeguarded, or held for another party;
- whether PayPlus has discretion over funds;
- who initiates payout;
- who receives payout;
- whether payout occurs before card settlement;
- whether PayPlus prefunds payout;
- whether reserves, holds, or collateral apply;
- whether refunds are possible after payout;
- whether chargeback liability remains after payout;
- when the payer obligation is satisfied;
- whether stored value, wallet value, credits, or balances are created;
- whether funds cross borders or involve FX;
- how failed, reversed, rejected, expired, cancelled, withdrawn, refunded, or charged-back transactions are handled.

For payee-created requests, the assessment must also document:

- whether the payee can create requests only after approval;
- whether the payer must accept and authorize before funding;
- whether the payee can change amount, destination, evidence, or terms after payer authorization;
- whether payee-side fees are deducted from payout or billed separately;
- whether payee withdrawal is supported before payer authorization;
- whether payer rejection, query, or dispute occurs before funds movement;
- whether request status, payout status, and reconciliation status remain accurate.

Funds flow design must align with legal conclusions, partner rules, accounting treatment, tax treatment, ledger design, and operating capabilities.

---

## 9. PSP, Acquirer, Card Network, and Classification Assessment

PayPlus must confirm whether proposed flows are acceptable to card networks, PSPs, acquirers, processors, gateways, and payout providers.

Assessment areas include:

| Area | Required Question |
| --- | --- |
| Product support | Does the partner support PayPlus bill payment use case? |
| Payee-created requests | Does the partner permit payees to create requests funded by payer card authorization? |
| PayFac / marketplace / platform | Does the flow require PayFac, marketplace, platform, or sub-merchant treatment? |
| Payee onboarding | What KYC/KYB, beneficial ownership, sanctions, underwriting, and monitoring obligations apply? |
| Category support | Are target categories approved, restricted, or prohibited? |
| MCC / transaction classification | What MCC or classification applies? |
| Cash-like treatment | Could transactions be quasi-cash, cash advance, account funding, money transfer, or cash equivalent? |
| Fees | Are payer service fees, convenience fees, surcharges, payee fees, platform fees, or payout fees permitted? |
| Multi-card | Are split payments, partial authorization, and multi-source funding supported? |
| Authorization and capture | Are timing, delayed capture, reversal, and expiry rules acceptable? |
| Refunds and reversals | Are refunds possible after payout or partial funding? |
| Chargebacks | Can PayPlus provide required evidence and meet deadlines? |
| Payouts | Are payout methods, timing, reversals, recalls, and destination controls supported? |
| Reserves | Are reserves, holdbacks, prefunding, collateral, or payee-specific holds required? |
| Reporting | Are transaction, fee, payout, dispute, balance, and payee-level reports available? |
| Geographic restrictions | Are jurisdictions, countries, states, territories, or currencies restricted? |
| Brand rules | Do card-brand-specific requirements apply? |

MCC and transaction classification may affect:

- processing cost;
- interchange and scheme fees;
- issuer authorization behavior;
- cash advance treatment;
- rewards eligibility;
- user complaints;
- chargebacks;
- partner underwriting;
- commercial viability.

Final classification should be confirmed with the PSP/acquirer before launch.

---

## 10. Category, Payee Type, and Request Creator Assessment

Each bill category, payee type, and request creator model must be assessed for legal, partner, operational, commercial, and risk acceptability.

| Dimension | Assessment Question |
| --- | --- |
| Legal permissibility | Is the category and request model permitted in the launch jurisdiction? |
| Partner acceptability | Does the PSP/acquirer/payout provider allow it? |
| Classification | Is there an acceptable MCC or transaction classification? |
| Request creator type | Is the request payer-created, payee-created, admin-created, partner-created, or system-created? |
| Payee role | Is the payee a merchant, sub-merchant, biller, landlord, school, utility, service provider, beneficiary, agent, or other role? |
| Payee onboarding | Can the payee be verified before request creation or payout? |
| Capability permissions | Can product restrict payee actions by type, status, category, geography, and risk tier? |
| Risk level | Does the model increase fraud, cashout, collusion, fake invoice, fake rent, or chargeback risk? |
| Consumer protection | Are special disclosures, cancellation rights, dispute rights, or protections required? |
| Payer authorization | Does payment require payer review and explicit authorization? |
| Payer-payee relationship | Must the relationship be verified or risk-assessed? |
| Evidence quality | Can PayPlus prove obligation, request origin, payer authorization, disclosure, and payout? |
| Payout feasibility | Can PayPlus pay the payee reliably and reverse or recover where required? |
| Operational complexity | Does the category require manual review or custom routing? |
| Economics | Does the flow meet contribution margin thresholds? |
| Complaint risk | Is the category likely to create payer, payee, or partner complaints? |

PayPlus should maintain lists of:

- prohibited categories;
- restricted categories;
- enhanced review categories;
- approved MVP categories;
- approved payee-created request categories;
- approved payee types;
- partner-specific approved categories;
- jurisdiction-specific restrictions;
- request-creator-specific restrictions.

Enhanced review categories may include rent, mortgage, loan repayment, tax, government payments, utility payments, tuition, insurance, medical bills, legal fees, business invoices, service-provider invoices, donations, crypto-related payments, gambling-related payments, investment-related payments, money transfer, cash equivalents, gift cards, stored value, person-to-person payments, self-payments, related-party payments, and payments to newly onboarded individual payees.

---

## 11. Partner Due Diligence

Partner due diligence should cover PSPs, acquirers, processors, gateways, payout providers, identity providers, verification providers, fraud vendors, OCR/document providers, and other material payment partners.

| Area | Required Review |
| --- | --- |
| Regulatory status | Licenses, registrations, sponsorship model, jurisdiction coverage. |
| Product support | Bill payment, payee-created requests, multi-card, refunds, chargebacks, payouts, and reporting. |
| Role support | Merchant, PayFac, marketplace, platform, agent, or bill-payment provider model. |
| Payee onboarding | KYC/KYB, beneficial ownership, sanctions, underwriting, monitoring, and offboarding. |
| Category support | Approved and prohibited categories, including rent, invoice, education, utility, insurance, and other obligations. |
| Pricing | Processing, gateway, refund, chargeback, payout, FX, monthly, minimum, setup, onboarding, verification, and account fees. |
| Settlement | Settlement timing, reserves, holdbacks, minimum balances, prefunding, collateral, and payee-specific holds. |
| Risk controls | Fraud tools, monitoring, limits, payee monitoring, request abuse monitoring, and rule configuration. |
| Chargebacks | Evidence, representment, deadlines, fees, and liability. |
| Payouts | Bank transfer, instant payout, card payout, local rails, cross-border rails, and payout reporting. |
| Reconciliation | Reports, webhooks, transaction IDs, payout IDs, fee files, balance files, and payee-level reporting. |
| Security | PCI DSS, SOC reports, ISO certifications, penetration testing, encryption, and vulnerability management. |
| Privacy | DPA, sub-processors, data residency, retention, deletion, and payer/payee data boundaries. |
| Reliability | SLAs, uptime, incident response, escalation, account management, and status reporting. |
| Integration | APIs, SDKs, webhooks, idempotency, sandbox, and testing tools. |
| Contract | Liability, indemnity, termination, audit rights, data rights, change notice, prohibited use, and required payee terms. |

Due diligence records should be stored in vendor, compliance, and contract repositories.

---

## 12. Partner Comparison Scorecard

A partner scorecard should be used when comparing multiple PSPs, acquirers, processors, gateways, or payout providers.

| Criterion | Weight | Provider A | Provider B | Provider C | Notes |
| --- | --- | --- | --- | --- | --- |
| Regulatory coverage | TBD | TBD | TBD | TBD |  |
| Bill payment support | TBD | TBD | TBD | TBD |  |
| Payee-created request support | TBD | TBD | TBD | TBD |  |
| PayFac / marketplace / platform support | TBD | TBD | TBD | TBD |  |
| Payee onboarding support | TBD | TBD | TBD | TBD |  |
| Category support | TBD | TBD | TBD | TBD |  |
| Rent / invoice / utility / education support | TBD | TBD | TBD | TBD |  |
| Multi-card support | TBD | TBD | TBD | TBD |  |
| Payout capabilities | TBD | TBD | TBD | TBD |  |
| Refund and chargeback support | TBD | TBD | TBD | TBD |  |
| Reconciliation quality | TBD | TBD | TBD | TBD |  |
| Payee-level reporting | TBD | TBD | TBD | TBD |  |
| Pricing | TBD | TBD | TBD | TBD |  |
| Settlement timing | TBD | TBD | TBD | TBD |  |
| Reserve requirements | TBD | TBD | TBD | TBD |  |
| Fraud and request-abuse tools | TBD | TBD | TBD | TBD |  |
| Security and privacy | TBD | TBD | TBD | TBD |  |
| API quality | TBD | TBD | TBD | TBD |  |
| Operational support | TBD | TBD | TBD | TBD |  |
| Contract flexibility | TBD | TBD | TBD | TBD |  |
| Overall fit | TBD | TBD | TBD | TBD |  |

Weights should reflect launch priorities and risk appetite.

---

## 13. Required Partner Confirmations

Before launch, PayPlus should seek written partner confirmation for material assumptions, including:

- supported product use case;
- supported jurisdictions;
- supported funds flow;
- payer-created and payee-created request support;
- merchant of record, PayFac, marketplace, platform, agent, or sub-merchant implications;
- approved bill categories;
- approved payee types;
- approved request creator types;
- prohibited and restricted categories;
- payee onboarding, KYC/KYB, beneficial ownership, sanctions, and monitoring obligations;
- MCC or transaction classification;
- whether transactions may be treated as cash-like, quasi-cash, account funding, or money transfer;
- fee restrictions;
- multi-card and split payment support;
- authorization and capture timing;
- payer authorization evidence requirements;
- refund and reversal support;
- payee request withdrawal support;
- chargeback process, liability, and evidence requirements;
- payout method and settlement timing;
- reserves, holdbacks, prefunding, collateral, or payee-specific holds;
- reporting and reconciliation data;
- payee-level reporting;
- data protection and security commitments;
- payer/payee data visibility constraints;
- operational support and escalation;
- contractual change notice obligations.

If written confirmation cannot be obtained, the assumption must be logged as an open risk.

---

## 14. Consumer Protection and Disclosure Assessment

Legal, Compliance, and Product should assess whether user, payer, and payee disclosures cover:

- PayPlus role;
- request creator or request origin;
- payee or biller identity;
- bill or obligation amount;
- payer service fee;
- payee-side fees, if applicable;
- taxes, if applicable;
- total amount charged to payer;
- payout amount or net payout amount, if shown to payee;
- estimated processing time;
- whether payment is guaranteed or conditional;
- payer authorization requirement;
- statement that payee-created requests are not paid unless payer authorizes payment;
- payer rejection, query, dispute, or expiration behavior;
- payee withdrawal or cancellation behavior;
- refund and cancellation rules;
- failed payment behavior;
- chargeback and dispute rights;
- promotion terms;
- card statement descriptor;
- potential issuer fees, if applicable and known;
- payer responsibility for late fees;
- payee responsibility for accurate request information and evidence;
- data use and privacy;
- support contact;
- terms acceptance.

For payee-created requests, disclosures must avoid implying that:

- the request is mandatory merely because the payee sent it;
- payment has already been completed;
- PayPlus validates legal enforceability unless explicitly approved;
- PayPlus guarantees the payee’s performance or underlying service;
- payout timing is guaranteed before confirmation.

Detailed content belongs in `DOC-07` and `DOC-08`.

---

## 15. AML, Sanctions, Anti-Cashout, and Fraud Assessment

PayPlus must assess whether each flow creates AML, sanctions, fraud, cashout, collusion, or abuse risk.

Assessment areas include:

- payer identity verification;
- payee verification;
- beneficial ownership review;
- sanctions screening;
- PEP or adverse media screening, if applicable;
- transaction monitoring;
- request monitoring;
- velocity limits;
- category limits;
- payee limits;
- payer limits;
- request creation limits;
- request spam detection;
- self-payment detection;
- circular payment detection;
- related-party or collusive payer-payee detection;
- fake invoice detection;
- fake rent detection;
- duplicate tenancy, lease, invoice, or bill detection;
- landlord verification and tenancy evidence review;
- card testing;
- stolen card fraud;
- account takeover;
- first-party misuse;
- refund abuse;
- chargeback abuse;
- promotion abuse;
- suspicious activity escalation;
- law enforcement or regulatory request handling;
- recordkeeping.

Detailed controls belong in `DOC-14 AML, Anti-Cashout, Fraud & Risk Controls`.

---

## 16. Data Protection, Privacy, Security, and PCI Assessment

PayPlus must assess data protection and security requirements for each partner and flow.

Review areas include:

- PCI DSS scope;
- card data handling;
- tokenization;
- data minimization;
- user, payer, and payee consent;
- privacy notice coverage;
- payer/payee data visibility boundaries;
- payee access to request and payout information;
- payer access to payee-created request evidence;
- sensitive document handling;
- role-based access controls;
- data processing agreements;
- cross-border data transfers;
- data residency;
- sub-processors;
- retention and deletion;
- encryption in transit and at rest;
- audit logs;
- incident notification;
- breach response;
- vulnerability management;
- SOC 2 or equivalent reports;
- penetration testing;
- business continuity and disaster recovery;
- partner API and webhook security;
- secrets management.

Detailed requirements belong in `DOC-15` and `DOC-19`.

---

## 17. Contractual Assessment

Partner contracts should be reviewed for:

| Contract Area | Review Focus |
| --- | --- |
| Scope of services | Does the contract allow PayPlus use case, categories, payee types, and payee-created request model? |
| Role definitions | Are merchant, PayFac, platform, sub-merchant, agent, processor, payer, payee, and data roles clear? |
| Payee onboarding | Are KYC/KYB, sanctions, beneficial ownership, underwriting, monitoring, and approval responsibilities clear? |
| Payee terms | Are required payee, sub-merchant, biller, landlord, or platform terms defined? |
| Regulatory responsibility | Who is responsible for licenses, AML, sanctions, complaints, reporting, and payee monitoring? |
| Card network compliance | Who is responsible for network rule compliance and fines? |
| Pricing | Are all fees, minimums, pass-through charges, payee-side charges, and platform fees documented? |
| Reserves and settlement | Are reserves, holdbacks, collateral, prefunding, settlement timing, and payout timing clear? |
| Chargebacks and refunds | Are liability, fees, deadlines, evidence, representment, and refund rights clear? |
| Payouts | Are payout failures, reversals, recalls, destination changes, and exception handling addressed? |
| Request withdrawal and payer disputes | Are payee withdrawal, payer rejection, payer query, and payer dispute processes supported? |
| Data protection and security | Are DPA, sub-processors, breach notice, PCI, audits, and security controls addressed? |
| SLAs and support | Are uptime, incident response, escalation, and support commitments defined? |
| Reporting | Are transaction, request, fee, dispute, payout, balance, payee-level, and reconciliation reports required? |
| Audit rights | Can PayPlus audit relevant compliance, security, payee onboarding, and financial records? |
| Change notice | Must partner notify PayPlus of pricing, rule, reserve, capability, category, or onboarding changes? |
| Termination | Are suspension, termination, migration, payee offboarding, and wind-down rights acceptable? |
| Liability and indemnity | Are liability caps, exclusions, chargeback liability, fraud liability, and indemnities acceptable? |

Legal approval is required before signing material payment partner agreements.

---

## 18. Settlement, Reserve, Holdback, and Liquidity Review

Finance and Payments must assess:

- settlement timing;
- funding availability;
- payout timing;
- payee payout timing;
- whether payout occurs before card settlement;
- reserve percentage;
- rolling reserve period;
- holdback amount;
- payee-specific holds;
- payee-specific reserve requirements;
- collateral or guarantee requirements;
- prefunding requirement;
- minimum balance requirement;
- chargeback reserve requirement;
- refund reserve requirement;
- currency and FX settlement;
- weekend and holiday delays;
- bank cutoff times;
- liquidity buffer needed;
- impact on cash runway;
- impact on category scaling;
- impact on payee-created request scaling;
- risk of promising payout timing before funds are available.

This review should align with `DOC-02 Business Model & Unit Economics`.

---

## 19. Multi-Card and Multi-Source Assessment

If PayPlus supports multi-card or multi-source payments, the assessment must include:

- whether PSP/acquirer supports split funding;
- whether multiple authorizations may fund one bill or request;
- whether partial authorization is supported;
- whether PayPlus may hold partial funds while completing other authorizations;
- whether failed partial funding requires reversal or cancellation;
- how payer authorization covers each funding source;
- how payer service fees are calculated and allocated;
- how payee-side fees interact with split funding;
- how refunds are allocated;
- how chargebacks are handled when only one funding source disputes;
- whether payee receives one payout or multiple payouts;
- how reconciliation links parent request to child funding events;
- how promotion eligibility is calculated;
- whether multi-card increases AML, cashout, collusion, or request-abuse risk;
- whether multi-card changes licensing or funds-control analysis;
- whether additional disclosures are required;
- whether payee-created request status remains accurate during partial authorization or failure.

Detailed requirements belong in `DOC-09`, `DOC-11`, and `DOC-18`.

---

## 20. Payee-Created Request Assessment

Payee-created payment requests require dedicated assessment before launch.

This applies when an approved payee, such as a landlord, school, utility, biller, service provider, business, or other approved payee, creates a bill, invoice, fee, rent, or payment obligation request and sends it to a payer.

| Assessment Area | Required Question |
| --- | --- |
| Payee eligibility | Which payee types may create requests? |
| Payee onboarding | What KYC/KYB, sanctions, beneficial ownership, payout verification, and risk checks are required? |
| Payee role | Is the payee a merchant, sub-merchant, biller, beneficiary, landlord, agent, customer, or platform participant? |
| PayPlus role | Does PayPlus act as merchant, PayFac, marketplace, agent, payment service provider, bill payment provider, or technical service provider? |
| Request evidence | What evidence is required to support the obligation? |
| Payer authorization | How does payer review, accept, authorize, reject, query, or dispute the request? |
| Legal enforceability | How does PayPlus avoid implying that it validates enforceability unless approved? |
| Consumer protection | What payer disclosures and protections are required? |
| Debt collection risk | Could overdue obligations create collection implications? |
| Abuse risk | How are fake, inflated, duplicate, spam, collusive, or self-dealing requests prevented? |
| Payer-payee relationship | Is relationship verification required? |
| Partner approval | Does PSP/acquirer/payout provider approve the model? |
| Classification | Does MCC or classification differ from payer-created requests? |
| Fee model | Are payer fees, payee fees, platform fees, or split fees permitted and disclosed? |
| Payout | When may payout occur and to whom? |
| Refund/chargeback | How are refunds, reversals, disputes, and chargebacks handled? |
| Privacy | What information can be shown to payer and payee? |
| Recordkeeping | What evidence must be retained? |
| Monitoring | What fraud, abuse, complaint, rejection, dispute, and chargeback monitoring is required? |

Payee-created requests must not launch unless:

- payee onboarding is approved;
- payer authorization is mandatory;
- evidence requirements are defined;
- payout gating is implemented;
- partner approval is obtained or risk-accepted;
- required disclosures are identified;
- privacy boundaries are defined;
- request abuse controls are defined;
- reconciliation and recordkeeping requirements are defined.

---

## 21. Landlord-Created Rent Request Assessment

Landlord-created rent requests require enhanced review because they may create higher cashout, collusion, fraud, dispute, and regulatory risk.

The assessment should include:

| Assessment Area | Required Question |
| --- | --- |
| Landlord eligibility | Which landlords or property managers may onboard? |
| Landlord verification | What identity, business, property, payout, sanctions, and risk checks are required? |
| Tenant relationship | How is the payer-landlord relationship validated? |
| Tenancy evidence | What lease, rent schedule, property reference, or equivalent evidence is required? |
| Rent amount reasonableness | Can rent amount be checked against evidence or historical pattern? |
| Duplicate rent prevention | How are duplicate rent requests detected? |
| Recurring rent | Are recurring rent requests permitted, or must each request be separately authorized? |
| Self-payment and collusion | How are related-party, circular, or collusive patterns detected? |
| Payout destination changes | What review is required when landlord payout details change? |
| Chargeback evidence | Can PayPlus produce authorization, tenancy evidence, landlord verification, payout proof, and communication evidence? |
| Consumer protection | What disclosures are required? |
| Debt collection | Could overdue rent create landlord/tenant or debt collection implications? |
| Partner approval | Do PSP/acquirer and payout providers approve rent and landlord-created requests? |
| Limits and monitoring | What value, frequency, payer, payee, and category limits apply? |

Landlord-created rent requests should remain restricted or deferred unless explicitly approved by Legal, Compliance, Payments, Risk, Product, Finance, Operations, Security, Privacy, and relevant partners.

---

## 22. Compliance Readiness Gates

PayPlus should not launch a jurisdiction, category, payment method, partner, payee type, request creator model, or funds flow until applicable gates are satisfied.

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC03-001` | Regulatory role assessed | Legal/Compliance documents PayPlus role for the flow, request creator type, payee type, and jurisdiction. |
| `GATE-DOC03-002` | Licensing path confirmed | Required licenses, exemptions, sponsorships, agent arrangements, PayFac arrangements, or partner coverage are documented. |
| `GATE-DOC03-003` | Funds flow approved | Funds flow diagram and description are approved by Legal, Compliance, Payments, and Finance. |
| `GATE-DOC03-004` | PSP/acquirer acceptability confirmed | Partner confirms use case, category, payee type, request model, MCC/classification, and flow support. |
| `GATE-DOC03-005` | Payout model approved | Payout method, provider, timing, failures, reversals, destination controls, and reconciliation are assessed. |
| `GATE-DOC03-006` | Category restrictions defined | Approved, restricted, and prohibited categories are documented. |
| `GATE-DOC03-007` | Fee model reviewed | User, payer, payee, surcharge, convenience fee, platform fee, or pricing model is reviewed. |
| `GATE-DOC03-008` | AML/risk assessment completed | AML, sanctions, fraud, anti-cashout, collusion, fake obligation, and abuse risks are assessed. |
| `GATE-DOC03-009` | Security/privacy review completed | PCI, privacy, security, payer/payee data visibility, and data protection reviews are completed. |
| `GATE-DOC03-010` | Partner due diligence completed | Vendor, regulatory, commercial, security, payee onboarding, and contract reviews are completed. |
| `GATE-DOC03-011` | Contract approved | Legal approves partner contract and required provisions. |
| `GATE-DOC03-012` | Settlement/reserve impact approved | Finance approves settlement timing, reserves, holdbacks, payout timing, and liquidity impact. |
| `GATE-DOC03-013` | Disclosure requirements identified | Required user, payer, and payee disclosures are identified for product implementation. |
| `GATE-DOC03-014` | Reporting and recordkeeping defined | Required transaction, request, payee, compliance, dispute, and reconciliation records are identified. |
| `GATE-DOC03-015` | Launch approval obtained | Required approvers sign off before launch. |
| `GATE-DOC03-016` | Payee onboarding model approved | Payee onboarding, verification, permissions, monitoring, and offboarding requirements are assessed. |
| `GATE-DOC03-017` | Payee-created request model approved | Role, evidence, payer authorization, partner acceptability, risk, privacy, payout, and recordkeeping are assessed. |
| `GATE-DOC03-018` | Landlord/rent request model approved | Landlord verification, tenancy evidence, payer-landlord relationship, rent risk, partner approval, and enhanced controls are assessed. |

---

## 23. Assessment Template

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

## 24. Key Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC03-001` | PayPlus will require a documented legal role assessment before launch. | Legal / Compliance | Open |
| `ASM-DOC03-002` | PSP/acquirer approval will be required for the PayPlus bill payment use case. | Payments | Open |
| `ASM-DOC03-003` | MCC or transaction classification will materially affect cost, risk, and payer experience. | Payments / Finance | Open |
| `ASM-DOC03-004` | Some bill categories may be prohibited or restricted by partners. | Compliance / Payments | Open |
| `ASM-DOC03-005` | Multi-card or split funding may require additional partner approval. | Payments / Product | Open |
| `ASM-DOC03-006` | Payer, payee, convenience fee, surcharge, or platform fee rules may vary by jurisdiction and partner. | Legal / Compliance | Open |
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

## 25. Key Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC03-001` | No launch without documented regulatory role assessment. | Prevents unassessed legal exposure. | Legal / Compliance |
| `CON-DOC03-002` | No launch without PSP/acquirer approval or acceptable documented assumption. | Prevents partner rule breach. | Payments |
| `CON-DOC03-003` | No restricted category launch without explicit approval. | Prevents unsupported or high-risk use cases. | Compliance / Risk |
| `CON-DOC03-004` | Fee model must be reviewed before implementation. | Prevents unlawful or prohibited fees. | Legal / Compliance |
| `CON-DOC03-005` | Funds flow cannot change without reassessment. | Prevents licensing and partner mismatch. | Legal / Payments |
| `CON-DOC03-006` | Partner contracts must support operational requirements. | Prevents gaps in refunds, chargebacks, reporting, and settlement. | Legal / Payments |
| `CON-DOC03-007` | AML, sanctions, fraud, anti-cashout, collusion, and request-abuse controls must match flow risk. | Prevents financial crime and partner risk. | Compliance / Risk |
| `CON-DOC03-008` | Security and privacy review is required for payment partners and payee-created request flows. | Prevents data protection, PCI, and visibility gaps. | Security / Privacy |
| `CON-DOC03-009` | Settlement and reserve terms must be approved by Finance. | Prevents liquidity surprises. | Finance |
| `CON-DOC03-010` | Required disclosures must be implemented before launch. | Prevents consumer protection and complaint risk. | Product / Legal |
| `CON-DOC03-011` | Payee-created requests cannot launch without payee onboarding, payer authorization, partner acceptability, and risk review. | Prevents unapproved PayFac/marketplace, cashout, fake obligation, and consumer protection risks. | Product / Legal / Compliance / Payments |
| `CON-DOC03-012` | Payee-created rent requests cannot launch without landlord verification, tenancy evidence, and enhanced controls. | Prevents rent-based cashout and collusion risk. | Legal / Risk / Compliance |
| `CON-DOC03-013` | Payee-created request flows cannot charge or fund payer without explicit payer authorization. | Prevents unauthorized payment and consumer harm. | Product / Payments / Legal |
| `CON-DOC03-014` | Payee access to payer information must be limited to approved visibility. | Prevents privacy and security violations. | Privacy / Security |
| `CON-DOC03-015` | Payer access to payee evidence must be limited to approved visibility. | Prevents over-disclosure of payee-sensitive data. | Privacy / Product / Legal |

---

## 26. Key Dependencies

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
| `DEP-DOC03-012` | Disclosure drafts. | Consumer protection assessment. | Product / Legal | Open |
| `DEP-DOC03-013` | Payee onboarding requirements. | Payee-created request, payout, role, AML, sanctions, partner, and risk assessment. | Product / Compliance / Risk | Open |
| `DEP-DOC03-014` | Payee type taxonomy and capability model. | Payee capability and control assessment. | Product / Risk / Compliance | Open |
| `DEP-DOC03-015` | Request creator type model. | Role, funds flow, partner, disclosure, and reporting assessment. | Product / Payments / Legal | Open |
| `DEP-DOC03-016` | Landlord/rent evidence standard. | Landlord-created rent request assessment. | Product / Legal / Risk | Open |
| `DEP-DOC03-017` | Invoice evidence and business-payee verification standard. | Payee-created invoice and fee request assessment. | Product / Risk / Compliance | Open |
| `DEP-DOC03-018` | Payer identification and invitation mechanism. | Consumer protection, privacy, security, and request delivery assessment. | Product / Engineering / Privacy | Open |
| `DEP-DOC03-019` | Payer acceptance, rejection, query, and dispute process. | Payee-created request legal, operational, and disclosure assessment. | Product / Operations / Legal | Open |
| `DEP-DOC03-020` | Payer/payee data visibility rules. | Privacy, security, support, and disclosure assessment. | Privacy / Security / Product | Open |
| `DEP-DOC03-021` | Partner confirmation of payee-created request support. | Launch approval for payee-created request model. | Payments / Commercial | Open |

---

## 27. Key Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC03-001` | PayPlus launches with incorrect regulatory role classification. | Licensing breach, enforcement, partner termination. | Obtain legal assessment per jurisdiction and flow. | Legal / Compliance | Open |
| `RISK-DOC03-002` | Flow is treated as money transmission or payment service requiring licensing. | Launch delay, regulatory risk, operating restrictions. | Evaluate exemptions, partner sponsorship, or licensed provider model. | Legal / Compliance | Open |
| `RISK-DOC03-003` | PSP/acquirer rejects bill payment or target category after integration. | Launch delay and rework. | Obtain written partner confirmation early. | Payments / Commercial | Open |
| `RISK-DOC03-004` | Transactions are classified as quasi-cash, cash advance, account funding, or money transfer. | Higher costs, issuer declines, complaints. | Confirm MCC/classification and add disclosures if required. | Payments / Legal | Open |
| `RISK-DOC03-005` | Fee model violates law, network rules, or partner restrictions. | Fines, refunds, product redesign. | Legal, card network, and partner fee review before launch. | Legal / Payments | Open |
| `RISK-DOC03-006` | Multi-card funding creates unsupported funds flow or refund complexity. | Compliance, operational, and reconciliation failures. | Require dedicated assessment and partner approval. | Product / Payments | Open |
| `RISK-DOC03-007` | Partner reserves or holdbacks create liquidity strain. | Working capital pressure and growth limits. | Model reserve impact and obtain Finance approval. | Finance / Payments | Open |
| `RISK-DOC03-008` | Inadequate payee verification enables fraud or cashout. | Financial loss and regulatory risk. | Implement payee verification and anti-cashout controls. | Risk / Compliance | Open |
| `RISK-DOC03-009` | Partner contract lacks required reporting or chargeback support. | Reconciliation gaps and loss exposure. | Use contractual checklist and Legal review. | Legal / Payments | Open |
| `RISK-DOC03-010` | Privacy, PCI, or security obligations are underestimated. | Breach, compliance failure, remediation cost. | Complete security, privacy, and PCI scope review. | Security / Privacy | Open |
| `RISK-DOC03-011` | Required disclosures are incomplete or unclear. | Complaints, disputes, regulatory risk. | Legal review of checkout, receipt, request, and terms content. | Product / Legal | Open |
| `RISK-DOC03-012` | Regulatory or network rule changes affect approved flows. | Product restrictions or operational changes. | Maintain periodic review and partner change notice monitoring. | Compliance / Payments | Open |
| `RISK-DOC03-013` | Payee-created request model changes PayPlus into a PayFac, marketplace, agent, or regulated payment service model unexpectedly. | Licensing, partner, contract, and operational impact. | Dedicated role assessment and partner confirmation. | Legal / Compliance / Payments | Open |
| `RISK-DOC03-014` | Payees are incorrectly classified. | Regulatory, tax, contract, dispute, and partner compliance risk. | Define payee role by flow, category, and contract. | Legal / Compliance / Payments | Open |
| `RISK-DOC03-015` | Payee-created requests are used for fake invoices, fake rent, self-payment, or collusive cashout. | Fraud, chargebacks, partner termination, regulatory risk. | Require onboarding, evidence, relationship checks, limits, and monitoring. | Risk / Compliance | Open |
| `RISK-DOC03-016` | Landlord-created rent requests trigger landlord/tenant, rent collection, debt collection, or heightened consumer protection issues. | Legal risk, complaints, launch delay. | Conduct rent-specific legal and risk assessment. | Legal / Compliance / Product | Open |
| `RISK-DOC03-017` | Payer believes a payee-created request is mandatory, validated, or already paid. | Complaints, disputes, unfair experience risk. | Require request-origin disclosure and explicit payer authorization. | Product / Legal | Open |
| `RISK-DOC03-018` | Payee sees payer-sensitive payment, card, risk, or private profile information. | Privacy, security, and trust risk. | Enforce data visibility boundaries and RBAC. | Privacy / Security | Open |
| `RISK-DOC03-019` | PSP/acquirer does not support payee-created requests, sub-merchant treatment, or payee onboarding model. | Launch blocker or redesign. | Obtain written confirmation before build or launch. | Payments / Commercial | Open |
| `RISK-DOC03-020` | Payee-created requests increase chargeback evidence burden. | Higher losses and representment failures. | Capture request origin, evidence, authorization, disclosure, communication, and payout proof. | Payments / Operations | Open |
| `RISK-DOC03-021` | Payee-side fee model is prohibited or creates unexpected disclosure, tax, or contract obligations. | Product redesign and financial risk. | Review payee-side pricing with Legal, Finance, Tax, and partners. | Legal / Finance / Commercial | Open |

---

## 28. Downstream Document Impact

`DOC-03` should guide downstream documents as follows:

| Document | Impact |
| --- | --- |
| `DOC-04` | Compliance gates, controls, evidence, certifications, payee onboarding, payee-created request, and rent/invoice controls. |
| `DOC-05` | Product requirements for payment methods, categories, partner constraints, disclosures, payee types, request creator types, and flow limits. |
| `DOC-06` | Payer, payee, landlord, biller, and partner journeys reflecting eligibility, verification, restrictions, authorization, and request-origin decisions. |
| `DOC-07` | Payer-facing and payee-facing role, fee, timing, request-origin, refund, risk, authorization, issuer-fee, and payee-created request disclosures. |
| `DOC-08` | Receipts and notifications for transaction, request-origin, payer authorization, fee, timing, status, and failure information. |
| `DOC-09` | Payment request and settlement design aligned to approved funds flow, request creator model, authorization, partner constraints, and multi-card limits. |
| `DOC-10` | Payout and reconciliation aligned to approved payout provider, payee status, payout eligibility, settlement timing, reserves, and reporting files. |
| `DOC-11` | Refund, cancellation, chargeback, dispute, payer rejection, payee withdrawal, and loss allocation logic. |
| `DOC-12` | Bill category, document AI/OCR, payee verification, invoice evidence, rent evidence, landlord verification, and evidence standards. |
| `DOC-13` | Promotion rules aligned to partner, fee, payer/payee, request-origin, and abuse restrictions. |
| `DOC-14` | AML, sanctions, fraud, cashout, collusion, fake invoice, fake rent, request abuse, and payee risk controls. |
| `DOC-15` | Privacy, retention, data visibility, minimization, and sensitive document handling. |
| `DOC-16` | Architecture support for approved flows, payee portal/request services, integrations, controls, and partner constraints. |
| `DOC-17` | PSP/acquirer, payout, notification, webhook, payee request APIs, and idempotency integration requirements. |
| `DOC-18` | Ledger and reporting fields for regulatory records, request creator type, payee type, payer authorization, disputes, reconciliation, and margin analysis. |
| `DOC-19` | Authentication, tokenization, PCI, RBAC, payer/payee data boundaries, admin access, encryption, and audit controls. |
| `DOC-20` | Launch checklist including DOC-03 gates and approvals. |
| `DOC-21` | Monitoring for partner restrictions, onboarding issues, request abuse, settlement issues, chargebacks, category violations, payout failures, and compliance incidents. |

---

## 29. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC03-001` | What jurisdictions will PayPlus launch in first? | Project Owner / Legal | Critical | Open |
| `OQ-DOC03-002` | What legal role will PayPlus take in the MVP funds flow? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-003` | Does the MVP funds flow require money transmission, payment service, or similar licensing? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-004` | Can PayPlus rely on a regulated partner, exemption, or agent model? | Legal / Compliance | Critical | Open |
| `OQ-DOC03-005` | Which PSP/acquirer will support the bill payment use case? | Payments / Commercial | Critical | Open |
| `OQ-DOC03-006` | What MCC or transaction classification will apply? | Payments | Critical | Open |
| `OQ-DOC03-007` | Will transactions be treated as purchase, quasi-cash, money transfer, or account funding? | Payments / Legal | Critical | Open |
| `OQ-DOC03-008` | Are payer-paid, payee-paid, service, convenience, platform, or surcharge fees permitted? | Legal / Payments | Critical | Open |
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

## 30. Acceptance Criteria

`DOC-03` is acceptable when it clearly defines:

- purpose and scope;
- assessment principles;
- assessment triggers;
- regulatory role assessment framework;
- licensing and exemption considerations;
- funds flow assessment;
- PSP, acquirer, card network, and transaction classification assessment;
- category, payee type, and request creator assessment;
- partner due diligence and scorecard;
- required partner confirmations;
- consumer protection and disclosure assessment;
- AML, sanctions, anti-cashout, collusion, and fraud assessment;
- data protection, privacy, security, and PCI assessment;
- contractual assessment;
- settlement, reserve, holdback, and liquidity review;
- multi-card and multi-source assessment;
- payee-created request assessment;
- landlord-created rent request assessment;
- compliance readiness gates;
- assessment template;
- assumptions;
- constraints;
- dependencies;
- risks;
- downstream document impact;
- open questions.

This document should remain an assessment framework and should not become a final legal opinion, compliance policy, partner contract, pricing sheet, product PRD, technical integration specification, risk rulebook, or operations SOP.

---

## 31. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-03 Regulatory, PSP & Acquirer Assessment. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation assessment framework, added triggers, role and licensing assessment, funds flow review, partner due diligence, scorecard, category restrictions, required confirmations, contractual assessment, compliance gates, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
| `0.3.0` | 2026-05-27 | Product Documentation Team | Updated assessment framework to account for payee onboarding and payee-created bill, invoice, fee, and rent payment request capability introduced in DOC-05 v0.2.0. Added request creator type assessment, payee role classification, PayFac/marketplace/platform implications, payer authorization assessment, payee-created request partner confirmations, landlord/rent assessment, payer/payee privacy boundaries, expanded risk, disclosure, contract, settlement, assumptions, constraints, dependencies, open questions, and readiness gates. |
| `0.4.0` | 2026-05-27 | Product Documentation Team | Simplified structure and language while preserving essential regulatory, PSP/acquirer, funds flow, partner, category, payee-created request, rent request, disclosure, privacy, security, contractual, settlement, readiness gate, risk, and open-question content. |
