---
document_id: DOC-02
title: Business Model & Unit Economics
version: 0.7.0
status: Founder Working Baseline
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
last_updated: 2026-06-01
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
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-18 Data Model, Transaction Ledger & Reporting
---

# DOC-02 — Business Model & Unit Economics

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

### 2.1 Current Commercial Baseline

Payee-created requests and tenancy/rent payments are MVP scope from a product perspective.

From a commercial perspective, they remain gated by:

- PSP/acquirer pricing and acceptance;
- payout cost and settlement timing;
- payee onboarding and verification cost;
- payer acceptance and completion rate;
- support, dispute, refund, chargeback, fraud, and manual review cost;
- category-level contribution margin;
- approved fee disclosure and fee recovery model.

Each commercial module, fee model, category, payee type, promotion, and payout method should be independently configurable or disableable.

The current fee model baseline is an online payment processing service fee calculated as a percentage of transaction amount. Payer fees, payee fees, subsidies, coupons, promotion codes, discount codes, refunds, reversals, and exact rate logic remain to be confirmed.

Fee rates, fee allocation, subsidies, coupons, promotion codes, discount codes, refund handling, and reversal treatment should be configurable in the admin dashboard so pricing decisions can change without blocking documentation drafting.

The current payout timing baseline assumes payment gateway settlement of T+1 to T+3 and payout from the PayPlus operating bank account on the same day after upstream settlement, subject to final bank, PSP/acquirer, liquidity, reserve, and reconciliation approval.

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

PayPlus unit economics should include all direct, variable, and material allocated costs.

| Cost Driver | Description |
| --- | --- |
| Card processing cost | PSP, acquirer, interchange, scheme, processor, gateway, authorization, capture, and refund costs. |
| Payout cost | Bank transfer, payout provider, instant payout, retry, and payout exception costs. |
| Refund and reversal cost | Processing cost, revenue reversal, support cost, and failed payout recovery cost. |
| Chargeback cost | Chargeback fees, lost principal, dispute operations, and representment evidence cost. |
| Fraud loss | Loss from unauthorized, abusive, fake, inflated, collusive, or cashout activity. |
| Promotion cost | Discounts, cashback, credits, rewards, fee waivers, referral bonuses, and partner-funded offers. |
| Manual review cost | Operations review for bills, invoices, rent evidence, payees, risk alerts, payouts, disputes, and exceptions. |
| Support cost | Payer, user, payee, and partner support burden. |
| Payee onboarding cost | Payee activation, review, verification, contracting, and setup costs. |
| Payee verification cost | Landlord, biller, business, school, service provider, payout account, or other payee verification costs. |
| Evidence review cost | Bill, invoice, tenancy, lease, service agreement, fee notice, or supporting document review costs. |
| Request delivery cost | Email, SMS, push, WhatsApp, or other payer invitation and notification costs. |
| Payer query or dispute cost | Support and operations cost for pre-authorization rejection, query, clarification, or dispute. |
| KYC/KYB cost | Identity, business, sanctions, and watchlist verification costs. |
| OCR/document AI cost | Extraction or validation cost for bill, invoice, rent, or supporting evidence. |
| Risk tooling cost | Device intelligence, fraud scoring, sanctions screening, transaction monitoring, and abuse detection costs. |
| Infrastructure cost | Cloud, storage, database, logging, monitoring, and retention costs. |
| Reconciliation cost | Finance and operations effort to reconcile funding, fees, payouts, refunds, exceptions, and partner files. |
| Compliance and audit cost | Compliance monitoring, audit, advisory, reporting, policy, and evidence retention costs. |
| Reserve or holdback cost | Cost of funds or reduced liquidity from partner reserves, rolling reserves, collateral, or prefunding. |
| Tax cost | VAT, GST, sales tax, withholding, transaction tax, or other applicable tax cost. |

Costs should be modeled conservatively until actual partner pricing, operational effort, payee onboarding effort, request conversion, support burden, and loss data are available.

---

## 7. Unit Economics

### 7.1 Base Transaction Formula

PayPlus should calculate transaction contribution margin using a transparent formula.

```text
Gross Revenue
- Card Processing Cost
- Payout Cost
- Refund / Reversal Cost
- Chargeback Cost Allocation
- Fraud Loss Allocation
- Promotion Cost
- Partner Revenue Share
- Manual Review Cost Allocation
- Customer Support Cost Allocation
- KYC / KYB Cost Allocation
- OCR / Document AI Cost Allocation
- Risk Tooling Cost Allocation
- Notification Cost Allocation
- Variable Infrastructure Cost Allocation
- Tax Cost Allocation
= Transaction Contribution Margin
```

### 7.2 Payee-Created Request Formula

For payee-created requests, PayPlus should also include payee-side economics and request-funnel costs.

```text
Gross Revenue
+ Payee-Side Revenue
+ Partner / Campaign Funding
- Card Processing Cost
- Payout Cost
- Payee Onboarding Cost Allocation
- Payee Verification Cost Allocation
- Request Creation / Delivery Cost
- Bill / Invoice / Rent Evidence Review Cost
- Payer Query / Rejection / Dispute Handling Cost Allocation
- Payee Support Cost Allocation
- Refund / Reversal Cost
- Chargeback Cost Allocation
- Fraud Loss Allocation
- Promotion Cost
- Partner / Payee Revenue Share
- Manual Review Cost Allocation
- Customer Support Cost Allocation
- KYC / KYB Cost Allocation
- OCR / Document AI Cost Allocation
- Risk Tooling Cost Allocation
- Notification Cost Allocation
- Variable Infrastructure Cost Allocation
- Tax Cost Allocation
= Payee-Created Request Contribution Margin
```

### 7.3 Margin Formulas

```text
Transaction Contribution Margin / Gross Transaction Value
= Contribution Margin Rate
```

```text
Transaction Contribution Margin / Gross Revenue
= Revenue Margin Rate
```

```text
Gross Revenue / Gross Transaction Value
= Take Rate
```

For payee-created request programs:

```text
Completed Payee-Created Request Contribution Margin
- Cost of Rejected / Expired / Disputed Payee-Created Requests
= Net Payee-Created Request Program Margin
```

Final reporting definitions belong in `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 8. Key Economic Definitions

| Term | Definition |
| --- | --- |
| Gross Transaction Value, or GTV | Total bill payment amount submitted or processed, based on approved reporting definition. |
| Funded Amount | Amount charged to the payer funding source. |
| Bill Amount | Amount owed to the biller or payee. |
| Payout Amount | Amount sent to the biller, payee, or receiving account. |
| Gross Revenue | Total approved revenue from payer fees, payee fees, partner fees, campaign funding, or other sources. |
| Payee-Side Revenue | Revenue collected from payees, including onboarding, subscription, request, payout, platform, or biller-paid fees. |
| Net Revenue | Gross revenue after refunds, fee reversals, discounts, and revenue share, based on approved definition. |
| Direct Cost | Cost directly attributable to a transaction or request. |
| Allocated Cost | Cost assigned to a transaction, request, payer, payee, category, campaign, or partner through an approved method. |
| Contribution Margin | Revenue minus direct and allocated variable costs. |
| Contribution Margin Rate | Contribution margin divided by approved denominator. |
| Take Rate | Gross or net revenue divided by GTV, based on approved definition. |
| Promotion Burn | Total cost of discounts, cashback, rewards, credits, fee waivers, or subsidies. |
| Chargeback Loss | Principal, fee, and operational loss caused by chargebacks. |
| Fraud Loss | Financial loss from fraudulent or abusive activity. |
| Manual Review Cost | Labor cost allocated to bill, invoice, rent, payee, risk, payout, compliance, or support review. |
| Payee Acquisition Cost | Sales, onboarding, verification, activation, incentive, and support cost required to acquire an approved payee. |
| Payee Onboarding Cost | Cost to verify and activate a payee for payout or request creation capability. |
| Payee-Created Request | A bill, invoice, fee, rent, or approved obligation request created by an approved payee and sent to a payer for review and authorization. |
| Request Creator Type | Indicator of whether a request was created by payer, payee, admin, system, partner, or migration process. |
| Payee Type | Classification such as landlord, school, utility, biller, service provider, business, or property manager. |
| Request Acceptance Rate | Percentage of payee-created requests accepted and authorized by payers. |
| Request Completion Rate | Percentage of payee-created requests accepted, funded, and paid out. |
| Payee Profitability | Contribution margin attributable to a payee after revenue, verification, request, support, payout, risk, refund, and chargeback costs. |

All metrics should have one approved definition in `DOC-18`.

---

## 9. Category and Payee-Type Economics

Each bill category and payee type should be assessed separately.

Economics may vary by:

- average transaction value;
- processing and payout cost;
- bill or obligation evidence quality;
- payee verification effort;
- payee onboarding cost;
- request creator type;
- payer acceptance and completion rate;
- rejection, query, dispute, and expiration rates;
- manual review rate;
- fraud and chargeback risk;
- fake invoice, fake rent, collusion, or self-payment risk;
- refund rate;
- payer willingness to pay;
- payee willingness to pay;
- partner willingness to subsidize;
- operational complexity;
- regulatory or partner restrictions;
- support burden.

Recommended category and payee-type assessment:

| Assessment Area | Question |
| --- | --- |
| Demand | Is there meaningful payer and/or payee demand? |
| Willingness to pay | Will payers, payees, billers, or partners accept required fees? |
| Cost | Are direct and allocated costs acceptable? |
| Risk | Are fraud, chargeback, fake bill, fake invoice, fake rent, and cashout risks manageable? |
| Review effort | Can evidence and exceptions be reviewed efficiently? |
| Payee onboarding effort | Can payees be onboarded and verified efficiently? |
| Request conversion | For payee-created requests, are acceptance and completion rates commercially viable? |
| Partner feasibility | Do PSP/acquirer and payout partners support the category and request model? |
| Compliance feasibility | Is the category acceptable under legal and compliance review? |
| Margin | Does the category meet minimum contribution margin threshold? |
| Scalability | Can the category scale without excessive manual review, support, dispute, or reconciliation effort? |

---

## 10. Multi-Card or Multi-Source Payment Economics

Multi-card or multi-source payments may increase user value but also increase cost and complexity.

Commercial assessment must consider:

- multiple authorization and capture fees;
- higher PSP cost;
- higher decline or partial failure rates;
- complex refund allocation;
- complex chargeback handling;
- complex reconciliation;
- higher support cost;
- higher fraud and abuse risk;
- more complex fee disclosure;
- partner or card network restrictions;
- partial funding failure handling;
- parent-child payment event reporting.

For payee-created requests, PayPlus must also define:

- whether the payer authorizes the full request and each funding allocation;
- whether payee-side request or payout fees apply once or per funding source;
- how the payee sees partial, failed, pending, or completed funding status.

Multi-card functionality should not launch unless economic and operational impact is understood.

Detailed logic belongs in `DOC-09`, `DOC-11`, `DOC-13`, and `DOC-18`.

---

## 11. Promotion and Subsidy Economics

Promotions must be commercially controlled.

Promotion cost may include:

- discounts;
- cashback;
- credits;
- fee waivers;
- rewards;
- miles or points rewards;
- referral bonuses;
- partner-funded offers;
- external voucher or partner fulfilment costs;
- exceptional payee-funded payer discounts, if separately approved;
- payee onboarding incentives;
- payee request fee waivers;
- advertising credits;
- sponsored placement costs;
- campaign operations cost.

Each promotion must define:

- funding source;
- whether it applies to payer, payee, or both;
- whether eligibility differs for payer-created and payee-created requests;
- budget;
- eligibility;
- qualification and entitlement rules;
- usage limits and quotas;
- maximum benefit;
- benefit target and benefit method;
- promotion quote impact;
- redemption rules;
- expiration;
- reversal rules;
- refund treatment;
- chargeback treatment;
- payer rejection or payee withdrawal treatment;
- tax and accounting treatment;
- reporting requirements;
- approval owner.

Promotions must not create uncontrolled negative margin. Spending-threshold rewards should track qualification progress and benefit entitlement, not merely raw card or transaction usage.

Detailed promotion engine, coupon, voucher, referral, membership, Asia Miles, card-linked eligibility, and external partner offer rules belong in `DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification`.

---

## 12. Refund, Cancellation, Rejection, Dispute, and Chargeback Economics

Refunds, cancellations, payer rejections, payer queries, disputes, payee withdrawals, failed payouts, and chargebacks can materially affect unit economics.

Commercial rules must define:

- whether PayPlus refunds payer service fees;
- whether payee-side fees are refundable;
- whether PSP fees are returned or retained;
- whether payout has already occurred;
- whether payout can be reversed;
- who bears unrecoverable loss;
- whether partner agreements define recovery rights;
- whether a promotion must be reversed;
- whether chargeback fees apply;
- whether manual investigation is required;
- whether evidence can support representment;
- whether payer or payee restrictions are required after dispute;
- how revenue reversal is recorded;
- how rejected, expired, disputed, or withdrawn payee-created requests are treated before payer authorization.

Detailed rules belong in `DOC-10`, `DOC-11`, and `DOC-18`.

---

## 13. Working Capital, Settlement, and Reserves

PayPlus must understand timing differences between:

- request creation;
- payer invitation or delivery;
- payer review and authorization;
- card authorization and capture;
- PSP settlement;
- reserves or holdbacks;
- payout initiation;
- payout completion;
- payee-side billing or fee deduction;
- refund window;
- chargeback window;
- revenue recognition;
- partner or payee settlement.

Settlement timing may create working capital needs if PayPlus pays a biller or payee before card funds are settled and available.

Commercial assessment should include:

- settlement delay;
- payout delay;
- funding gap;
- reserve requirement;
- holdback requirement;
- prefunding requirement;
- collateral requirement;
- chargeback exposure period;
- refund exposure period;
- liquidity buffer requirement;
- bank cutoff, weekend, and holiday effects;
- payee payout expectations.

PayPlus should avoid payout timing models that create unacceptable credit, liquidity, fraud, or cash-flow exposure unless approved.

Payee-facing payout timing should not be promised unless supported by the approved settlement and liquidity model.

---

## 14. Partner Economics

Partner economics must be assessed before selection.

Partner cost and revenue factors may include:

- setup fees;
- monthly minimums;
- transaction fees;
- percentage fees;
- gateway fees;
- authorization and capture fees;
- refund fees;
- chargeback fees;
- payout fees;
- account verification fees;
- KYC/KYB fees;
- payee onboarding or sub-merchant onboarding fees;
- payee screening fees;
- landlord or business verification fees;
- payout account verification fees;
- request delivery or notification fees;
- risk screening fees;
- OCR/document AI fees;
- support fees;
- reserve requirements;
- payee-specific holdback requirements;
- revenue share requirements;
- contract minimums;
- early termination costs;
- SLA penalties;
- data export costs;
- migration costs.

For payee-created request models, partner assessment should also consider whether pricing changes based on:

- payee type;
- request creator type;
- merchant, sub-merchant, biller, agent, beneficiary, or payee classification;
- category such as rent, invoice, education, utilities, medical bills, or domestic service obligations;
- payout timing;
- chargeback risk;
- payee onboarding model;
- platform or marketplace treatment.

Detailed partner assessment belongs in `DOC-03 Regulatory, PSP & Acquirer Assessment`.

---

## 15. Pricing Governance

Pricing changes can affect user trust, payer trust, payee adoption, compliance, margins, partner obligations, tax treatment, and product behavior.

Material pricing changes should follow an approved change process and include:

- business rationale;
- affected categories;
- affected users, payers, payees, and payee types;
- affected geographies;
- affected request creator types;
- effective date;
- expected margin impact;
- expected conversion impact;
- expected payee adoption or churn impact;
- compliance review;
- legal or consumer protection review, where applicable;
- tax/accounting review, where applicable;
- communication plan;
- systems and QA impact;
- approval record.

Pricing changes should be reflected in:

- fee calculation logic;
- user, payer, and payee disclosures;
- receipts;
- payee statements or payout reports, if applicable;
- ledger and reporting;
- customer support scripts;
- payee support scripts;
- terms or policies, if applicable.

---

## 16. Commercial Viability Gates

Each category, payment method, request creator model, payee type, promotion, or partner program should pass commercial viability gates before launch.

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC02-001` | Revenue model defined | Revenue source and fee structure are documented. |
| `GATE-DOC02-002` | Cost model defined | Direct and material allocated costs are documented. |
| `GATE-DOC02-003` | Contribution margin modeled | Expected contribution margin is calculated using approved assumptions. |
| `GATE-DOC02-004` | Risk loss assumptions included | Fraud, chargeback, refund, fake invoice, fake rent, collusion, and operational losses are included where applicable. |
| `GATE-DOC02-005` | Partner pricing assessed | PSP, acquirer, payout, onboarding, verification, and other partner pricing is confirmed or conservatively estimated. |
| `GATE-DOC02-006` | Promotion economics approved | Budget, funding source, cost bearer, and margin impact are approved. |
| `GATE-DOC02-007` | Settlement timing assessed | Working capital, reserve, holdback, payout timing, and payee settlement impacts are assessed. |
| `GATE-DOC02-008` | Legal/tax/accounting review completed | Relevant treatment of fees, taxes, and revenue recognition is reviewed. |
| `GATE-DOC02-009` | Reporting requirements defined | Required metrics and reports are documented. |
| `GATE-DOC02-010` | Launch approval obtained | Commercial approver signs off before launch. |
| `GATE-DOC02-011` | Payee-created request economics approved | Onboarding, request delivery, evidence review, acceptance rate, support, payout, fraud, and dispute economics are modeled before enabling payee-created requests. |
| `GATE-DOC02-012` | Payee-side pricing approved | Payee onboarding, subscription, request, payout, platform, or other payee-side fees are documented, disclosed, legally reviewed, and reportable before launch. |
| `GATE-DOC02-013` | Rent or invoice economics approved | Rent or invoice economics include landlord/business verification, evidence review, enhanced fraud risk, support cost, dispute cost, and chargeback assumptions. |

---

## 17. Reporting and Metrics

PayPlus should report commercial performance at transaction, request, category, user, payer, payee, partner, request-origin, and campaign level.

Candidate metrics include:

| Metric | Description |
| --- | --- |
| GTV | Total processed or submitted transaction value, based on approved definition. |
| Funded volume | Total value successfully charged to funding sources. |
| Paid-out volume | Total value successfully paid to payees or billers. |
| Gross revenue | Total service fees, payer fees, payee fees, partner fees, campaign funding, and other revenue. |
| Payee-side revenue | Revenue from payee onboarding, subscription, request, payout, platform, biller, or partner-payee fees. |
| Net revenue | Gross revenue after discounts, reversals, fee refunds, and revenue share, based on approved definition. |
| Card processing cost | Total and per-transaction card processing costs. |
| Payout cost | Total and per-transaction payout costs. |
| Payee onboarding cost | Total and per-approved-payee onboarding and verification costs. |
| Payee acquisition cost | Sales, onboarding, verification, support, and incentive cost per activated payee. |
| Request delivery cost | Cost to send or notify payers of payee-created requests. |
| Evidence review cost | Cost to review bill, invoice, rent, tenancy, or other supporting evidence. |
| Promotion burn | Total campaign or offer cost. |
| Fraud loss | Losses from fraud or abuse. |
| Chargeback loss | Principal and fee losses from chargebacks. |
| Manual review cost | Allocated cost of manual review. |
| Support cost | Allocated payer and payee support cost. |
| Contribution margin | Revenue less variable and allocated costs. |
| Contribution margin rate | Contribution margin as a percentage of approved denominator. |
| Take rate | Revenue as a percentage of GTV. |
| Average transaction value | Average bill or payment amount. |
| Approval rate | Percentage of payment requests approved. |
| Decline rate | Percentage of card payment attempts declined. |
| Payout failure rate | Percentage of payouts that fail. |
| Category profitability | Margin by bill category. |
| Payee profitability | Margin by payee or payee type. |
| Request-origin profitability | Margin by payer-created versus payee-created request. |
| Partner profitability | Margin by partner or payment route. |
| Campaign profitability | Margin after campaign cost. |
| Payee-created request volume | Number and value of requests created by approved payees. |
| Request acceptance rate | Percentage of payee-created requests accepted and authorized by payers. |
| Request rejection/query/dispute rate | Percentage of payee-created requests rejected, queried, or disputed before authorization. |
| Request expiration rate | Percentage of payee-created requests expiring without authorization. |
| Request completion rate | Percentage of payee-created requests accepted, funded, and paid out. |
| Payee activation rate | Percentage of onboarded payees that create at least one valid request. |
| Payee retention rate | Percentage of payees that continue creating valid requests over time. |

Final metric definitions belong in `DOC-18`.

---

## 18. Data and Ledger Expectations

Commercial reporting requires accurate transaction, request, payee, campaign, partner, and ledger records.

At minimum, PayPlus should track:

- bill amount;
- funded amount;
- payout amount;
- service fee;
- payer fee;
- payee fee;
- payee onboarding fee;
- payee subscription fee;
- payee request fee;
- payee payout fee;
- platform fee;
- discount amount;
- promotion amount;
- partner funding amount;
- tax amount, if applicable;
- card processing cost;
- payout cost;
- payee onboarding cost allocation;
- payee verification cost allocation;
- request delivery cost allocation;
- evidence review cost allocation;
- payer query or dispute cost allocation;
- payee support cost allocation;
- refund amount;
- chargeback amount;
- chargeback fee;
- fraud loss amount;
- revenue share amount;
- net revenue amount;
- contribution margin estimate;
- funding source type;
- payment route;
- payout route;
- bill category;
- user or payer segment;
- payee ID;
- payee type;
- payee onboarding status;
- request creator type;
- payee-created request status;
- payer response status;
- partner ID;
- campaign ID;
- transaction status;
- payout status;
- reconciliation status.

Detailed data model and ledger design belong in `DOC-18`.

---

## 19. Accounting, Tax, and Revenue Recognition Considerations

Finance and Legal/Tax must determine:

- whether PayPlus acts as principal or agent in each flow;
- whether treatment differs for payer-created and payee-created requests;
- how onboarded payees are classified for accounting and tax purposes;
- whether fees are recognized gross or net;
- when payer-side revenue is recognized;
- when payee-side revenue is recognized;
- how rejected, expired, withdrawn, cancelled, disputed, refunded, or charged-back requests affect revenue recognition;
- how promotion costs are classified;
- how partner-funded or payee-funded incentives are treated;
- whether taxes apply to payer fees, payee fees, platform fees, subscription fees, request fees, payout fees, or partner fees;
- whether withholding, VAT, GST, sales tax, or other transaction taxes apply;
- whether payout amounts are pass-through funds;
- how reserves, holdbacks, unpaid amounts, pending transactions, failed transactions, reversals, and chargebacks are recorded.

This document provides a framework only and does not establish accounting or tax policy.

---

## 20. Key Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC02-001` | Users or payers will accept a service fee high enough to cover card processing and payout cost in at least one MVP category. | Commercial / Product | Open |
| `ASM-DOC02-002` | PSP/acquirer pricing will allow positive contribution margin for target categories. | Commercial / Payments | Open |
| `ASM-DOC02-003` | Payout cost can be kept low enough for target transaction sizes. | Finance / Payments | Open |
| `ASM-DOC02-004` | Fraud and chargeback losses can be controlled through verification and risk rules. | Risk / Finance | Open |
| `ASM-DOC02-005` | Manual review cost is acceptable during MVP volume levels. | Operations / Finance | Open |
| `ASM-DOC02-006` | Promotions can be capped and tracked to avoid uncontrolled losses. | Growth / Finance | Open |
| `ASM-DOC02-007` | Transaction data will support category, partner, campaign, payee, request-origin, and margin reporting. | Finance / Engineering | Open |
| `ASM-DOC02-008` | Reserve and settlement timing will not create unacceptable working capital needs. | Finance / Payments | Open |
| `ASM-DOC02-009` | Tax and accounting treatment will not materially undermine the selected fee model. | Finance / Legal / Tax | Open |
| `ASM-DOC02-010` | Payee-created requests can produce incremental completed payment volume that justifies onboarding, verification, request delivery, support, and review costs. | Commercial / Product / Finance | Open |
| `ASM-DOC02-011` | Approved payees will accept payee-side fees, reduced payout amounts, or other commercial terms if selected. | Commercial / Product | Open |
| `ASM-DOC02-012` | Payers will accept payee-created requests at a rate sufficient to make the payee-created model commercially viable. | Product / Commercial | Open |
| `ASM-DOC02-013` | Payee onboarding and verification costs can be recovered through transaction margin, payee-side revenue, partner funding, or strategic value. | Commercial / Finance / Risk | Open |
| `ASM-DOC02-014` | Payee-created rent or invoice requests can be controlled without fraud, dispute, support, or chargeback costs exceeding margin. | Risk / Finance / Operations | Open |
| `ASM-DOC02-015` | Ledger and reporting data will support request creator type, payee type, payer response, payee-side fee, and request-funnel reporting. | Finance / Engineering | Open |

---

## 21. Key Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC02-001` | Fees must be disclosed before user or payer payment confirmation. | Requires transparent quote and checkout design. | Product / Legal |
| `CON-DOC02-002` | Pricing must comply with applicable law, card network rules, and partner restrictions. | May limit fee structures. | Legal / Compliance / Payments |
| `CON-DOC02-003` | Promotions must have approved budgets and controls. | Prevents uncontrolled negative margin. | Growth / Finance |
| `CON-DOC02-004` | Settlement timing may limit payout speed. | May require delayed payout or liquidity buffer. | Finance / Payments |
| `CON-DOC02-005` | Partner reserves or holdbacks may constrain growth. | Affects cash flow and capital planning. | Finance / Commercial |
| `CON-DOC02-006` | Accounting and tax treatment must be confirmed before launch. | May affect pricing, reporting, and contracts. | Finance / Legal / Tax |
| `CON-DOC02-007` | Negative-margin transactions must be approved or blocked unless strategically justified. | Requires margin monitoring and approval process. | Finance / Commercial |
| `CON-DOC02-008` | Commercial reporting depends on reliable ledger and reconciliation data. | Requires engineering and finance alignment. | Finance / Engineering |
| `CON-DOC02-009` | Multi-card payments may increase processing and support costs. | May require higher fees or deferral from MVP. | Product / Payments |
| `CON-DOC02-010` | Category expansion must pass commercial viability gates. | Controls rollout sequence. | Product / Commercial |
| `CON-DOC02-011` | Payee-created request enablement must pass commercial viability gates before launch. | Requires modeling onboarding, request delivery, acceptance, support, risk, payout, and dispute costs. | Commercial / Product / Finance |
| `CON-DOC02-012` | Payee-side fees must be disclosed, contractually supported, and reportable before implementation. | Requires pricing, billing, ledger, tax, and communication readiness. | Commercial / Legal / Finance |
| `CON-DOC02-013` | Payer must not be charged for a payee-created request before explicit payer authorization. | Prevents revenue capture before authorization. | Product / Payments / Legal |
| `CON-DOC02-014` | Payee-created rent or invoice requests may require higher fees, limits, or deferral if review, fraud, or support costs are too high. | May constrain category rollout or payee-side pricing. | Commercial / Risk / Product |

---

## 22. Key Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
| --- | --- | --- | --- | --- |
| `DEP-DOC02-001` | PSP/acquirer pricing and fee schedule. | Card processing cost model. | Commercial / Payments | Open |
| `DEP-DOC02-002` | Payout provider pricing. | Payout cost model. | Commercial / Payments | Open |
| `DEP-DOC02-003` | Launch category decision. | Category-level economics. | Product / Compliance | Open |
| `DEP-DOC02-004` | Transaction limits and risk rules. | Fraud and chargeback loss assumptions. | Risk / Compliance | Open |
| `DEP-DOC02-005` | Refund and chargeback rules. | Loss and revenue reversal model. | Payments / Risk / Finance | Open |
| `DEP-DOC02-006` | Promotion engine design. | Campaign economics and budget controls. | Growth / Product | Open |
| `DEP-DOC02-007` | Ledger and reporting model. | Margin reporting. | Finance / Engineering | Open |
| `DEP-DOC02-008` | Accounting policy decision. | Revenue recognition and financial reporting. | Finance | Open |
| `DEP-DOC02-009` | Tax review. | Fee and tax disclosure. | Legal / Tax / Finance | Open |
| `DEP-DOC02-010` | Partner contracts. | Revenue share, reserves, fees, and settlement timing. | Commercial / Legal | Open |
| `DEP-DOC02-011` | Payee onboarding cost model. | Payee-created request economics and payee-side pricing. | Commercial / Risk / Operations | Open |
| `DEP-DOC02-012` | Payee type taxonomy and capability model. | Pricing, cost allocation, and payee profitability reporting. | Product / Commercial / Risk | Open |
| `DEP-DOC02-013` | Payee-side fee policy. | Payee onboarding, request, payout, subscription, or platform pricing. | Commercial / Finance / Legal | Open |
| `DEP-DOC02-014` | Payer identification and invitation mechanism. | Request delivery cost and conversion modeling. | Product / Engineering / Commercial | Open |
| `DEP-DOC02-015` | Payer response and pre-authorization dispute process. | Rejection, query, dispute, support, and operational cost modeling. | Product / Operations / Legal | Open |
| `DEP-DOC02-016` | Landlord/rent verification standard. | Rent request economics and landlord onboarding cost model. | Product / Risk / Operations | Open |
| `DEP-DOC02-017` | Invoice verification standard. | Invoice request economics and business payee cost model. | Product / Risk / Operations | Open |
| `DEP-DOC02-018` | Payee support operating model. | Payee support cost allocation and payee profitability reporting. | Operations / Commercial | Open |

---

## 23. Key Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC02-001` | Card processing costs exceed payer willingness to pay. | Negative margin or low conversion. | Test pricing, model category margins, and consider partner subsidies. | Commercial / Product | Open |
| `RISK-DOC02-002` | PSP/acquirer pricing or reserves make model uneconomic. | Launch delay or margin failure. | Compare providers and model reserve impact. | Commercial / Payments | Open |
| `RISK-DOC02-003` | Promotions create uncontrolled losses. | Cash burn and distorted unit economics. | Use budgets, caps, eligibility, and margin reporting. | Growth / Finance | Open |
| `RISK-DOC02-004` | Chargebacks or fraud losses exceed assumptions. | Margin loss and partner risk. | Use risk controls, limits, monitoring, and evidence retention. | Risk / Finance | Open |
| `RISK-DOC02-005` | Manual review costs are underestimated. | Lower contribution margin and operational bottlenecks. | Track review time and automate high-volume checks. | Operations / Finance | Open |
| `RISK-DOC02-006` | Fee disclosures are unclear or non-compliant. | Complaints, chargebacks, regulatory risk. | Legal and compliance review of checkout and receipt language. | Product / Legal | Open |
| `RISK-DOC02-007` | Settlement timing creates liquidity pressure. | Working capital gap and delayed payouts. | Model settlement schedules, reserves, and liquidity buffers. | Finance / Payments | Open |
| `RISK-DOC02-008` | Reporting data cannot support margin analysis. | Poor commercial decisions and audit gaps. | Define data model and ledger fields before launch. | Finance / Engineering | Open |
| `RISK-DOC02-009` | Accounting or tax treatment changes economics. | Pricing, reporting, or contract redesign. | Obtain Finance and Tax review before pricing approval. | Finance / Legal / Tax | Open |
| `RISK-DOC02-010` | Category expansion occurs without commercial review. | Scaling negative-margin categories. | Enforce commercial viability gates. | Product / Commercial | Open |
| `RISK-DOC02-011` | Payee-created requests have low payer acceptance or completion rates. | Request delivery, onboarding, support, and review costs may not convert into revenue. | Model funnel economics, pilot with limits, and monitor acceptance rate. | Commercial / Product | Open |
| `RISK-DOC02-012` | Payee onboarding and verification costs are underestimated. | Payee-created request model may be uneconomic. | Track cost per approved payee and require payee-type-level reporting. | Commercial / Operations | Open |
| `RISK-DOC02-013` | Payee-side fees reduce payee adoption. | Lower request volume and weaker network growth. | Test pricing, segment by payee type, and consider subsidies. | Commercial / Product | Open |
| `RISK-DOC02-014` | Payee-created requests increase support and dispute costs. | Margin erosion and operational backlog. | Track payer queries, disputes, payee tickets, and review cost. | Operations / Finance | Open |
| `RISK-DOC02-015` | Fake invoice, fake rent, or collusive request losses exceed assumptions. | Fraud losses, chargebacks, partner risk, and negative margin. | Include enhanced risk loss assumptions and require controls before scaling. | Risk / Finance | Open |
| `RISK-DOC02-016` | Payee-created rent requests have high evidence review cost. | Rent category may be commercially unattractive. | Pilot rent separately and model landlord verification and tenancy review cost. | Commercial / Risk | Open |
| `RISK-DOC02-017` | Payee-side billing, refunds, or fee reversals are not ledgered correctly. | Revenue leakage, disputes, accounting errors, audit gaps. | Define payee fee ledger fields and reconciliation requirements in DOC-18. | Finance / Engineering | Open |
| `RISK-DOC02-018` | Payer-facing and payee-facing fee allocation is confusing. | Complaints, disputes, regulatory risk, and lower conversion. | Require clear disclosures and pricing QA before launch. | Product / Legal | Open |
| `RISK-DOC02-019` | Payee payout timing expectations create commercial or liquidity pressure. | Support burden, trust loss, or unsafe early payout. | Align payout communications with settlement and risk model. | Finance / Operations | Open |
| `RISK-DOC02-020` | Payee-created request spam creates notification, support, and review costs without revenue. | Negative request-level economics and user dissatisfaction. | Apply request limits, payee controls, abuse monitoring, and commercial gating. | Commercial / Risk | Open |

---

## 24. Downstream Document Impact

`DOC-02` should guide downstream documents as follows:

| Document | Impact |
| --- | --- |
| `DOC-03` | Include PSP/acquirer pricing, reserve, category support, payout model, commercial restrictions, payee onboarding economics, payee classification, and payee-created request support in partner assessment. |
| `DOC-04` | Include commercial viability gates for payee-created requests, payee-side pricing, rent/invoice economics, and launch/change governance. |
| `DOC-05` | Convert fee quote, pricing display, promotion handling, commercial eligibility, payee-side pricing, request-origin reporting, and payee profitability requirements into product requirements. |
| `DOC-07` | Define payer-facing and payee-facing pricing, fee, promotion, timing, request-origin, and authorization disclosures. |
| `DOC-08` | Define receipts, fee breakdowns, payee statements, refund messages, promotion notifications, request invitations, and payer/payee status messages. |
| `DOC-09` | Define funding, fee calculation, payer authorization, payee-created request fee treatment, multi-card fee allocation, and failed authorization behavior. |
| `DOC-10` | Define payout cost, payee-side fee deduction if applicable, settlement timing, reconciliation, and financial exception handling. |
| `DOC-11` | Define refund, cancellation, payer rejection, payee withdrawal, chargeback, loss allocation, payee fee reversal, and fee reversal rules. |
| `DOC-13` | Define campaign budgets, promotion cost, funding source, eligibility, qualification, entitlement, usage, promotion quote, reversal, abuse controls, reward fulfilment, and reporting. |
| `DOC-14` | Include fraud, fake invoice, fake rent, request abuse, chargeback, and payee-created request losses in risk appetite and controls. |
| `DOC-18` | Define ledger fields, request creator type, payee type, payer response status, payee-side fees, metric definitions, revenue, cost, margin, campaign, request-origin, and partner reporting. |
| `DOC-20` | Include commercial readiness, pricing, payee-side fee, request-origin, and payee-created request economics test cases in launch checklist. |
| `DOC-21` | Include monitoring for margin-impacting exceptions, onboarding costs, request spam, payout failures, refunds, chargebacks, payer disputes, and payee support burden. |

---

## 25. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC02-001` | What exact percentage service fee, payer/payee fee allocation, subsidy, coupon, promotion, discount, refund, and reversal treatment will be used for MVP? | Commercial / Product | Critical | Open |
| `OQ-DOC02-002` | What is the target minimum contribution margin per transaction and by category? | Finance / Commercial | Critical | Open |
| `OQ-DOC02-003` | What PSP/acquirer pricing assumptions should be used before contracts are signed? | Payments / Commercial | Critical | Open |
| `OQ-DOC02-004` | What operating-bank, FPS, cheque, and EPS pricing assumptions should be used for payout modeling? | Payments / Commercial | High | Open |
| `OQ-DOC02-005` | Will PayPlus charge different fees by category, amount, funding source, request creator type, or payee type? | Commercial / Legal / Product | High | Open |
| `OQ-DOC02-006` | Are card surcharges, convenience fees, or payment-method-based fees permitted in the launch jurisdiction and partner model? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC02-007` | What refund and fee reversal rules will apply? | Finance / Payments / Product | High | Open |
| `OQ-DOC02-008` | How will chargeback liability be allocated between PayPlus, users, payers, payees, and partners? | Legal / Finance / Risk | High | Open |
| `OQ-DOC02-009` | What promotion budget and campaign controls are approved for MVP? | Growth / Finance | Medium | Open |
| `OQ-DOC02-010` | What reserve, holdback, or prefunding requirements will partners impose? | Commercial / Payments | High | Open |
| `OQ-DOC02-011` | What accounting treatment applies to service fees, payout amounts, refunds, and promotions? | Finance | Critical | Open |
| `OQ-DOC02-012` | What tax treatment applies to user fees, payer fees, payee fees, partner fees, and promotions? | Legal / Tax / Finance | Critical | Open |
| `OQ-DOC02-013` | What data fields are required to calculate transaction, request, payee, and request-origin margin accurately? | Finance / Engineering | High | Open |
| `OQ-DOC02-014` | What commercial approval process is required before category, payee type, request-origin, or pricing changes? | Project Owner / Finance | Medium | Open |
| `OQ-DOC02-015` | What commercial gates must payee-created payment requests pass before launch enablement and scale-up? | Project Owner / Commercial / Product | Critical | Open |
| `OQ-DOC02-016` | Which payee types can be commercially supported for request creation? | Commercial / Product / Risk | Critical | Open |
| `OQ-DOC02-017` | Are payees charged onboarding, subscription, invoice, request, payout, platform, or transaction fees? | Commercial / Finance / Product | Critical | Open |
| `OQ-DOC02-018` | If payee-side fees are charged, when are they charged: onboarding, request creation, request delivery, payer acceptance, funding, payout, monthly, or another trigger? | Commercial / Finance / Product | High | Open |
| `OQ-DOC02-019` | Are payee-side fees refundable if a request is rejected, expired, disputed, cancelled, withdrawn, refunded, or charged back? | Finance / Legal / Product | High | Open |
| `OQ-DOC02-020` | What payer acceptance rate is required for payee-created requests to be commercially viable? | Commercial / Product | High | Open |
| `OQ-DOC02-021` | What payee onboarding cost and payee acquisition cost are acceptable by payee type? | Commercial / Finance | High | Open |
| `OQ-DOC02-022` | What commercial model applies to landlord-created rent requests if rent is enabled? | Commercial / Legal / Risk | Critical | Open |
| `OQ-DOC02-023` | What commercial model applies to invoice requests if business or service-provider payees are enabled? | Commercial / Legal / Risk | High | Open |
| `OQ-DOC02-024` | Can payees subsidize payer service fees, and how should those subsidies be disclosed, recorded, and reversed? | Commercial / Finance / Legal | High | Open |
| `OQ-DOC02-025` | What request, notification, or review limits are required to prevent payee-created request spam from creating negative economics? | Commercial / Risk / Operations | High | Open |
| `OQ-DOC02-026` | What margin threshold must payee-created request flows meet before scale-up? | Finance / Commercial | High | Open |
| `OQ-DOC02-027` | What payee-level reporting is required for payout, fees, request volume, disputes, refunds, and tax/accounting purposes? | Finance / Product / Engineering | Medium | Open |

---

## 26. Acceptance Criteria

`DOC-02` is acceptable when it clearly defines:

- commercial objective;
- business model components;
- revenue streams;
- fee principles;
- cost drivers;
- transaction-level unit economics;
- payee-created request economics;
- key economic definitions;
- category and payee-type economics;
- multi-card economics;
- promotion and subsidy economics;
- refund, cancellation, rejection, dispute, and chargeback economics;
- working capital, settlement, and reserve considerations;
- partner economics;
- pricing governance;
- commercial viability gates;
- reporting and metric expectations;
- data and ledger expectations;
- accounting, tax, and revenue recognition considerations;
- assumptions;
- constraints;
- dependencies;
- risks;
- downstream document impact;
- open questions.

This document should remain a commercial framework and should not become a final pricing sheet, accounting policy, tax memo, partner contract, product PRD, or payment processing specification.

---

## 27. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-02 Business Model & Unit Economics. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation commercial framework, added unit economics model, revenue and cost taxonomy, commercial viability gates, pricing governance, promotion economics, settlement and reserve considerations, reporting expectations, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
| `0.3.0` | 2026-05-27 | Product Documentation Team | Updated commercial framework to account for payee onboarding and payee-created bill, invoice, fee, and rent payment request capability introduced in DOC-05 v0.2.0. Added payee-side revenue streams, payee onboarding and verification costs, request-origin economics, payer/payee fee allocation, payee-created request funnel metrics, rent/invoice economics, payee-side pricing governance, commercial viability gates, reporting and ledger expectations, assumptions, constraints, dependencies, risks, and open questions. |
| `0.4.0` | 2026-05-27 | Product Documentation Team | Simplified structure and language while preserving essential commercial model, revenue streams, fee principles, cost drivers, unit economics formulas, payee-created request economics, commercial viability gates, reporting expectations, assumptions, constraints, dependencies, risks, and open questions. |
| `0.5.0` | 2026-05-29 | Product Documentation Team | Confirmed payee-created requests and tenancy/rent as product MVP scope while keeping commercial launch enablement gated by pricing, partner, payout, verification, support, risk, and margin assumptions. |
| `0.6.0` | 2026-05-30 | Product Documentation Team | Aligned category examples with updated DOC-01 positioning for rent, invoices, medical bills, and domestic service obligations. |
| `0.7.0` | 2026-06-01 | Product Documentation Team | Aligned promotion economics with DOC-13 by adding qualification, entitlement, promotion quote, miles, external voucher, and partner fulfilment cost concepts while de-emphasizing payee-funded discounts as exceptional. |
