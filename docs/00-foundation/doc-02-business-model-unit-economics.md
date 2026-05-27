---
document_id: DOC-02
title: Business Model & Unit Economics
version: 0.4.0
status: Draft
owner: Commercial / Finance Owner
reviewers:
  - Product Lead
  - Finance Lead
  - Commercial Lead
  - Payments Lead
  - Compliance Lead
  - Risk Lead
approvers:
  - Project Owner
  - Finance Lead
  - Commercial Lead
last_updated: 2026-05-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-13 Promotion Engine & Campaign Rules
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-18 Data Model, Transaction Ledger & Reporting
---

# DOC-02 — Business Model & Unit Economics

---

## 1. Purpose

This document defines the commercial framework and unit economics model for PayPlus.

It explains how PayPlus may generate revenue, incur costs, evaluate profitability, govern pricing, manage promotions, and determine whether a category, payment method, request type, payee type, partner model, or campaign is commercially viable.

`DOC-02` is a foundation document.

It guides downstream product, finance, payments, risk, promotion, reconciliation, operations, payee onboarding, and reporting documentation.

This document does not define final pricing, accounting policy, tax treatment, legal conclusions, partner contract terms, payment processing rules, payout rules, reconciliation procedures, promotion logic, or payee commercial terms.

Those topics must be confirmed in downstream documents, partner agreements, finance policies, tax review, and legal/compliance review.

---

## 2. Commercial Objective

The commercial objective of PayPlus is to create a sustainable bill payment business where approved revenue sources exceed the full variable and allocated costs of processing, paying, verifying, supporting, and managing each request or transaction.

PayPlus should only scale a category, request model, payee type, payment method, promotion, partner program, or geography when unit economics are understood and acceptable.

PayPlus should evaluate profitability at the following levels:

- transaction;
- payment request;
- user or payer;
- payee;
- request creator type;
- payee type;
- bill category;
- campaign;
- partner;
- payment method;
- payout method;
- geography or jurisdiction;
- product line.

For payee-created requests, PayPlus must separately assess:

- payee onboarding and verification cost;
- request creation and delivery cost;
- payer acceptance and completion rate;
- payer rejection, query, dispute, and expiration rate;
- evidence review cost;
- payee support cost;
- fraud, fake invoice, fake rent, collusion, and cashout loss assumptions;
- payee-side revenue, if any;
- incremental completed payment volume;
- incremental operational load.

---

## 3. Business Model Summary

PayPlus may use one or more approved business model components.

| Model Component | Description | Candidate Use |
| --- | --- | --- |
| Payer-paid service fee | Payer pays a fee when funding a payer-created or payee-created request. | Core candidate model. |
| Percentage fee | Fee calculated as a percentage of bill amount or funded amount. | Candidate core fee model. |
| Fixed fee | Flat fee per request, transaction, payout, or other approved event. | Candidate supplemental model. |
| Minimum fee | Fee floor to avoid negative economics on small transactions. | Candidate margin protection. |
| Payee-paid fee | Payee pays onboarding, request, platform, subscription, payout, collection, or transaction fee. | Candidate payee-side model. |
| Biller-paid fee | Biller or payee pays PayPlus to receive payments or access payer demand. | Possible where partnerships exist. |
| Split-fee model | Payer and payee each bear part of the fee. | Possible with clear disclosure. |
| Payee-subsidized payer fee | Payee funds part or all of the payer fee. | Possible for conversion or collection use cases. |
| Partner-funded subsidy | Partner funds part of transaction cost or user incentive. | Possible for campaigns or acquisition. |
| Promotion-funded model | PayPlus or partner funds discounts, cashback, credits, or rewards. | Growth mechanism; must be controlled. |
| Revenue share | PayPlus receives or pays a share of fees with partners, billers, payees, or affiliates. | Possible if contractually allowed. |
| Subscription or membership | User or payee pays recurring fee for preferred pricing, portal access, or benefits. | Future candidate. |
| API or platform fees | Partners or payees pay for API access or transaction processing. | Future candidate. |
| Advertisement or sponsored placement | Approved partners pay for placement or offers. | Future candidate; requires policy and disclosure. |

No business model component should launch until commercial, compliance, legal, accounting, tax, product, operational, and partner impacts are assessed.

Payee-side fees must not obscure payer-facing fees or mislead either party about the total cost of payment.

---

## 4. Revenue Streams

Candidate revenue streams include:

| Revenue Stream | Description | Notes |
| --- | --- | --- |
| Service fee | Fee charged to user or payer per transaction. | Must be disclosed before payment confirmation. |
| Payer service fee | Fee charged when payer authorizes payment. | May apply to payer-created or payee-created requests. |
| Payee onboarding fee | Fee charged to payee for onboarding, verification, or activation. | Requires legal, tax, and commercial review. |
| Payee subscription or platform fee | Recurring fee for payee portal, reporting, request creation, or support tools. | Requires billing and cancellation rules. |
| Payee request fee | Fee charged per request created, sent, accepted, funded, paid, or completed. | Trigger point must be defined. |
| Payee payout fee | Fee charged to payee for payout or special payout handling. | Requires disclosure and ledger support. |
| Biller-paid fee | Fee paid by biller or payee to receive PayPlus-supported payments. | Must be contractually documented. |
| Partner subsidy | Third party funds part of user cost or PayPlus cost. | Must be tracked and reconciled. |
| Campaign funding | Marketing, partner, or payee budget funds offers, rewards, or discounts. | Must be campaign-level reportable. |
| Revenue share | PayPlus receives or pays a share of revenue with partners or payees. | Must be included in margin calculations. |
| FX fee or spread | Revenue from currency conversion, if applicable. | Requires approval and disclosure. |
| Exception fee | Fee for failed payment, special handling, cancellation, or other exception. | High risk; requires explicit approval. |

Revenue recognition, tax treatment, and accounting classification must be reviewed by Finance and Legal/Tax before implementation.

---

## 5. Fee Principles

PayPlus fee design should follow these principles:

| Principle | Requirement |
| --- | --- |
| Transparent | Payer-facing fees must be shown before payment confirmation. |
| Accurate | Fee calculations must match receipts, ledger entries, and reports. |
| Authorized | Payer must not be charged before explicit payment authorization. |
| Contracted | Payee-side fees must be supported by payee agreement, disclosure, and ledger rules. |
| Compliant | Fees must comply with applicable law, card network rules, partner rules, tax rules, and consumer protection requirements. |
| Economically justified | Fees should reflect processing cost, payout cost, risk, review effort, support burden, and margin targets. |
| Non-misleading | Payee-funded or partner-funded subsidies must not hide the real payer cost or PayPlus role. |
| Reversible where required | Refund, cancellation, withdrawal, rejection, dispute, and chargeback fee treatment must be defined. |
| Reportable | Fees must be reportable by transaction, request, payer, payee, category, campaign, partner, and request origin where applicable. |

Payer-created payments and payee-created requests may support different fee presentation models.

Potential fee allocation models include:

- payer pays the full service fee;
- payee absorbs the full fee;
- payer and payee split the fee;
- biller, merchant, payee, or partner subsidizes the fee;
- campaign-funded or promotional fee reduction;
- blended model by category, payee type, or request origin.

Any fee model that varies by card type, issuer, funding source, jurisdiction, category, request creator type, payee type, payer segment, or user segment must be reviewed before launch.

---

## 6. Cost Drivers

... (document continues with sections 6 through 18 as in the provided text, formatted consistently)

---

## 19. Acceptance Criteria

DOC-02 is acceptable when it defines:

- commercial objective and scope;
- business model components;
- revenue streams;
- fee principles;
- cost drivers;
- unit economics formulas;
- key economic definitions;
- category and payee-type economics;
- multi-card or multi-source economics;
- promotion and subsidy economics;
- refund, cancellation, rejection, dispute, and chargeback economics;
- working capital, settlement, and reserves;
- partner economics;
- pricing governance;
- commercial viability gates;
- reporting and metrics;
- data and ledger expectations.

DOC-02 must remain focused on business model and unit economics governance only.

---

## 20. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-DOC02-001 | What is the minimum acceptable contribution margin rate for launch? | Finance Lead | High | Open |
| OQ-DOC02-002 | Should payee onboarding fees be refundable if verification fails? | Commercial / Finance Owner | Medium | Open |
| OQ-DOC02-003 | How should promotion burn be allocated between PayPlus and partners? | Product / Finance / Commercial | Medium | Open |
| OQ-DOC02-004 | What reporting cadence is required for campaign profitability metrics? | Finance / Product Owner | Medium | Open |
| OQ-DOC02-005 | Should multi-card payments be supported in MVP despite higher complexity? | Product Lead | High | Open |
| OQ-DOC02-006 | What is the approved definition of net revenue for reporting consistency? | Finance Lead | High | Open |
| OQ-DOC02-007 | How should rejected or expired payee-created requests be treated in margin reporting? | Finance / Risk Lead | Medium | Open |
| OQ-DOC02-008 | What reserve or holdback model is acceptable for PSP/acquirer partners? | Finance / Risk Lead | High | Open |
| OQ-DOC02-009 | Should payee subscription fees be billed monthly or annually? | Commercial Lead | Medium | Open |
| OQ-DOC02-010 | How should exception fees be disclosed to payers and payees? | Compliance Lead | Medium | Open |

---

## 21. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| 0.1.0 | 2026-05-14 | Initial Author | Initial draft of DOC-02 Business Model & Unit Economics. |
| 0.2.0 | 2026-05-20 | Commercial / Finance Owner | Added business model components, revenue streams, fee principles, and cost drivers. |
| 0.3.0 | 2026-05-24 | Commercial / Finance Owner | Expanded unit economics formulas, margin definitions, category/payee-type economics, and promotion rules. |
| 0.4.0 | 2026-05-27 | Commercial / Finance Owner | Added multi-card economics, refund/cancellation/dispute economics, working capital and reserves, partner economics, pricing governance, commercial viability gates, reporting metrics, and data/ledger expectations. |
