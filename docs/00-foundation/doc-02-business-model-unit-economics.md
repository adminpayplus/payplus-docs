---
document_id: DOC-02
title: Business Model & Unit Economics
version: 0.3.0
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
  - DOC-01 Project Charter & Product Positioning
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

## 1. Purpose

This document defines the commercial framework and unit economics model for PayPlus.

It establishes how PayPlus may generate revenue, incur costs, evaluate transaction profitability, manage promotions, assess partner economics, and determine whether a bill category, payment flow, request creator model, payee type, or payment obligation type is commercially viable.

`DOC-02` is a foundation document.

It is intended to guide downstream product, payment, promotion, finance, reconciliation, risk, operations, payee onboarding, and reporting documentation.

Version `0.3.0` updates the commercial framework to account for the `DOC-05 v0.2.0` product capability where approved payees may be onboarded to PayPlus and may create bill, invoice, fee, or rent payment requests for payer review, disclosure acceptance, authorization, and payment.

This document does not define final pricing, legal treatment, accounting treatment, tax treatment, promotion rules, payment processing rules, payout rules, payee onboarding fee policy, payee contract terms, reconciliation procedures, or contractual terms.

Those topics must be defined or confirmed in dedicated downstream documents, partner agreements, accounting policies, and legal/compliance reviews.

---

## 2. Scope

This document covers:

- Business model options.
- Revenue streams.
- Cost components.
- Transaction-level unit economics.
- Fee model considerations.
- Partner-funded and user-funded economics.
- Payee-funded or biller-funded economics.
- Payee onboarding, payee verification, and payee support economics.
- Payee-created bill, invoice, fee, or rent request economics.
- Payer-created versus payee-created request commercial comparison.
- Payer/payee incentive and fee allocation considerations.
- Promotion and subsidy economics.
- Category-level commercial assessment.
- Payee-type-level commercial assessment.
- Request-creator-type commercial assessment.
- Multi-card or multi-source payment economics.
- Refund, cancellation, payer rejection, payee withdrawal, dispute, chargeback, and failed payment economics.
- Working capital and settlement timing considerations.
- Reserve and holdback considerations.
- Tax, accounting, and reporting considerations at a framework level.
- Commercial viability gates.
- Metrics and reporting expectations.
- Assumptions, constraints, dependencies, risks, and open questions.

---

## 3. Out of Scope

This document does not define:

- Final user pricing.
- Final payer pricing.
- Final payee pricing.
- Final merchant, landlord, biller, school, service provider, or platform pricing.
- Final payee onboarding fees.
- Final payee subscription or platform fees.
- Final invoice, request, payout, or account maintenance fees.
- Legal fee classification.
- Tax advice.
- Accounting policy.
- PSP/acquirer contract terms.
- Payee contract or commercial terms.
- Card network rule interpretation.
- Payment state machine.
- Reconciliation process.
- Refund or chargeback operating procedure.
- Payee-created request rejection, query, dispute, or withdrawal procedure.
- Promotion campaign rule logic.
- Risk thresholds.
- AML controls.
- Product requirements.
- Technical architecture.
- Data schema.

These items must be defined in relevant downstream documents.

---

## 4. Commercial Objective

The commercial objective of PayPlus is to create a sustainable bill payment business where transaction revenue, payee-side revenue, partner funding, or other approved revenue sources exceed the full variable and allocated cost of processing, paying, supporting, verifying, and managing each transaction and payment request.

PayPlus should only scale categories, payment methods, request creator models, payee types, promotions, or partner programs where unit economics are understood and acceptable.

At minimum, PayPlus should understand profitability at the following levels:

- Transaction level.
- Payment request level.
- User or payer level.
- Payee level.
- Request creator type level.
- Payee type level.
- Bill category level.
- Campaign level.
- Partner level.
- Payment method level.
- Payout method level.
- Geography or jurisdiction level.
- Product line level.

For payee-created requests, PayPlus should separately assess:

- Cost to onboard and verify payees.
- Cost to support payees.
- Cost to create, deliver, review, and track requests.
- Payer acceptance and conversion rates.
- Payer rejection, query, dispute, and expiration rates.
- Fraud, fake invoice, fake rent, collusion, and cashout losses.
- Payee-side revenue, if any.
- Incremental volume or retention benefit from payee participation.
- Incremental operational load from payee-created requests.

---

## 5. Business Model Summary

PayPlus may use one or more business model components.

| Model Component | Description | Candidate Use |
| --- | --- | --- |
| User-paid service fee | User or payer pays a fee for using card-funded bill payment. | Core candidate model. |
| Payer-paid service fee | Payer pays a service fee when accepting and funding a payer-created or payee-created request. | Core candidate model. |
| Biller-paid fee | Biller or payee pays PayPlus to receive payments or users. | Possible where biller partnerships exist. |
| Payee onboarding fee | Payee pays a one-time fee to onboard, verify, or activate request creation capability. | Possible for approved payee programs; requires legal, tax, and commercial review. |
| Payee subscription or platform fee | Payee pays recurring fee for access to payee portal, payment request creation, reporting, or support features. | Future candidate; requires payee contract and billing model. |
| Payee request fee | Payee pays per bill, invoice, rent, fee, or payment request created, sent, accepted, or paid. | Possible for payee-created request model. |
| Payee payout fee | Payee pays for payout, expedited payout, payout retry, or special payout handling if approved. | Possible where legally and contractually allowed. |
| Split-fee model | Payer and payee each bear part of the service fee or platform fee. | Possible for partner or biller programs; requires clear disclosure. |
| Partner-funded subsidy | A partner funds part of transaction cost or user incentive. | Possible for campaigns or acquisition. |
| Promotion-funded model | PayPlus or partner funds discounts, cashback, credits, or rewards. | Growth mechanism; must be controlled. |
| Advertisement or sponsored placement | Approved partners pay for placement or offers. | Future candidate; requires policy and disclosure. |
| Revenue share | PayPlus shares revenue with billers, PSPs, payees, partners, or affiliates. | Possible if contractually allowed. |
| Subscription or membership | User pays recurring fee for preferred pricing or benefits. | Future candidate; requires consumer protection review. |
| Business account fees | Business users or payees pay for invoice or bill payment tools. | Future candidate. |
| API or platform fees | Partners or payees pay for API access or transaction processing. | Future candidate. |

No business model component should be launched until commercial, compliance, legal, accounting, tax, product, and operational impacts are assessed.

Payee-side fees must not obscure payer-facing fees or cause misleading disclosure of the total cost of payment.

---

## 6. Revenue Streams

Candidate revenue streams include:

| Revenue Stream | Description | Notes |
| --- | --- | --- |
| Service fee | Fee charged to user or payer per transaction. | Must be disclosed before payment confirmation. |
| Payer service fee | Fee charged to payer when authorizing a payment request. | Applies to payer-created or payee-created requests where approved. |
| Percentage fee | Fee calculated as percentage of bill amount or funded amount. | Must account for card processing cost and risk. |
| Fixed fee | Flat fee charged per transaction. | Useful for low-value transactions if user acceptable. |
| Minimum fee | Minimum fee floor to avoid negative economics on small transactions. | Important if fixed costs are material. |
| Payee onboarding fee | Fee charged to payee for onboarding, verification, or activation where approved. | Must account for KYC/KYB, review, support, and legal/tax treatment. |
| Payee subscription fee | Recurring fee charged to payee for access to PayPlus request or reporting tools. | Requires billing, cancellation, renewal, and contract rules. |
| Payee request fee | Fee charged to payee per request created, sent, accepted, funded, paid, or completed. | Trigger point must be defined to avoid disputes. |
| Payee payout fee | Fee charged to payee for standard or enhanced payout services where approved. | Must be reflected in payout, receipt, and reporting records. |
| Biller-paid fee | Fee paid by biller or payee to receive PayPlus-supported payments. | Must be contractually documented. |
| Partner subsidy | Third party funds part of user cost or PayPlus cost. | Must be contractually documented. |
| Campaign funding | Marketing or partner budget funds rewards or discounts. | Must be tracked at campaign level. |
| Advertisement revenue | Revenue from partner placement or sponsored biller offers. | Requires disclosure and content governance. |
| Revenue share | PayPlus receives or pays a share of fees with partners, billers, payees, or affiliates. | Must be reflected in contribution margin. |
| FX spread or fee | Revenue from currency conversion, if applicable. | Requires explicit approval and disclosure. |
| Late or exception fees | Fees related to failed payment, cancellation, special handling, or exceptional support. | High consumer and payee-relations risk; should require approval. |

Revenue recognition, tax treatment, and accounting classification must be reviewed by Finance and Legal/Tax before implementation.

---

## 7. Cost Components

PayPlus unit economics should include all variable and allocated costs.

| Cost Component | Description | Example Drivers |
| --- | --- | --- |
| Card processing cost | PSP, acquirer, interchange, scheme, processor, and gateway cost. | Card type, card country, transaction amount, MCC, region. |
| Payout cost | Cost to transfer funds to biller or payee. | Bank transfer, instant payout, payout provider fee. |
| FX cost | Currency conversion cost, if applicable. | Currency pair, spread, provider fee. |
| Refund cost | Processing cost or lost fee from refund. | Refund method, timing, partner fee policy. |
| Chargeback cost | Chargeback fee, lost principal, dispute operations, evidence preparation. | Fraud, service dispute, user complaint. |
| Fraud loss | Loss from unauthorized or abusive transactions. | Category, user risk, payee risk, request creator type. |
| Promotion cost | Discounts, cashback, rewards, credits, partner offers, subsidies. | Campaign design and eligibility. |
| Manual review cost | Operations cost for bill, payee, risk, payout, payee-created request, or support review. | Review time and staffing cost. |
| Customer support cost | Cost of handling user, payer, or payee support. | Ticket volume, transaction complexity, payer/payee disputes. |
| Payee onboarding cost | Cost to onboard and approve payees. | Payee type, verification depth, manual review time. |
| Payee verification cost | Cost of verifying landlord, biller, business, school, service provider, payout account, or other payee data. | KYC/KYB provider pricing, document review, sanctions checks. |
| Landlord or rent verification cost | Cost to review landlord identity, property reference, tenancy evidence, rent schedule, and relationship evidence. | Rent category, evidence complexity, manual review rate. |
| Invoice or request evidence review cost | Cost to review invoices, fee notices, service agreements, or other payee-created request evidence. | Request volume, category, document complexity. |
| Payer invitation or request delivery cost | Cost to notify or invite payer to review a payee-created request. | Email, SMS, push, WhatsApp, delivery retries. |
| Payer query or dispute handling cost | Cost to handle pre-authorization payer rejection, query, dispute, or clarification. | Query rate, dispute rate, support staffing. |
| Payee support cost | Cost to support payee onboarding, request creation, payout questions, and disputes. | Payee volume, request volume, support channels. |
| KYC/KYB cost | Identity or business verification cost. | Verification provider pricing. |
| Document AI/OCR cost | Bill, invoice, rent, or supporting document extraction or validation cost. | Pages, documents, API calls. |
| Fraud/risk tooling cost | Risk scoring, device intelligence, sanctions screening, monitoring tools. | API calls, users, payees, transactions. |
| Notification cost | SMS, email, push, WhatsApp, or other communication cost. | Channel and message volume. |
| Infrastructure cost | Cloud, storage, database, compute, logging, monitoring. | Usage and retention volume. |
| Reconciliation cost | Finance and operations effort to reconcile transactions, requests, payouts, and fees. | Transaction volume and exception rate. |
| Compliance cost | Compliance monitoring, audit, advisory, policy, reporting. | Jurisdiction and product complexity. |
| Reserve or holdback cost | Cost of funds or reduced liquidity due to partner reserves. | Reserve rate and release timing. |
| Tax cost | Transaction taxes, VAT/GST/sales tax, withholding, or other tax. | Jurisdiction and fee structure. |

Costs should be modeled conservatively until actual partner pricing, operational effort, payee onboarding effort, request conversion, and support data are available.

---

## 8. Unit Economics Formula

At transaction level, PayPlus should calculate contribution margin using a transparent formula.

Recommended base formula:

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

For payee-created requests, the formula should also consider:

```text
Gross Revenue
+ Payee-Side Revenue
+ Partner / Campaign Funding
- Card Processing Cost
- Payout Cost
- Payee Onboarding Cost Allocation
- Payee Verification Cost Allocation
- Payee Request Creation / Delivery Cost
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

Recommended margin rate formula:

```text
Transaction Contribution Margin / Gross Transaction Value
= Contribution Margin Rate
```

Recommended revenue margin formula:

```text
Transaction Contribution Margin / Gross Revenue
= Revenue Margin Rate
```

Where useful, PayPlus should also calculate:

```text
Gross Transaction Value
- Payout Amount
- Direct Transaction Costs
= Net Economic Spread
```

For payee-created requests, PayPlus should also calculate request-funnel economics:

```text
Payee-Created Request Revenue
- Payee-Created Request Variable Costs
= Request-Level Contribution Margin
```

And:

```text
Completed Payee-Created Request Contribution Margin
- Cost of Rejected / Expired / Disputed Payee-Created Requests
= Net Payee-Created Request Program Margin
```

The final reporting definitions must be defined in `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 9. Key Economic Definitions

| Term | Definition |
| --- | --- |
| Gross Transaction Value, or GTV | Total bill payment amount submitted or processed before fees, depending on final reporting definition. |
| Funded Amount | Amount charged to the user or payer funding source. |
| Bill Amount | Amount owed to the biller or payee. |
| Payout Amount | Amount sent to the biller, payee, or receiving account. |
| Gross Revenue | Total revenue earned from user fees, payer fees, payee fees, partner fees, campaign funding, or other approved revenue streams. |
| Payee-Side Revenue | Revenue collected from payees, including onboarding fees, request fees, subscription fees, payout fees, platform fees, or biller-paid fees. |
| Net Revenue | Gross revenue after refunds, fee reversals, discounts, and revenue share, if defined this way in finance reporting. |
| Direct Cost | Cost directly attributable to a transaction or request, such as card processing, payout fees, request delivery, or verification fees. |
| Allocated Cost | Cost assigned to a transaction, request, user, payee, category, or campaign using an approved allocation method. |
| Contribution Margin | Revenue minus direct and allocated variable costs. |
| Contribution Margin Rate | Contribution margin divided by GTV or another approved denominator. |
| Take Rate | Gross or net revenue divided by GTV, based on approved definition. |
| Promotion Burn | Total cost of discounts, cashback, rewards, credits, or subsidies. |
| Chargeback Loss | Principal, fees, and operational costs lost due to chargebacks. |
| Fraud Loss | Financial losses attributed to fraudulent or abusive activity. |
| Manual Review Cost | Labor cost allocated to bill, invoice, rent, payee, risk, compliance, payout, or support review. |
| Payee Acquisition Cost | Sales, onboarding, verification, activation, incentive, and support cost required to acquire an approved payee. |
| Payee Onboarding Cost | Cost to verify and activate a payee for payout or request creation capability. |
| Payee-Created Request | A bill, invoice, fee, rent, or approved payment obligation request created by an approved payee and sent to a payer for review and authorization. |
| Request Creator Type | Indicator of whether a request was created by payer, payee, admin, system, partner, or migration process. |
| Payee Type | Classification of payee, such as landlord, school, utility, biller, service provider, business, property manager, or other approved type. |
| Request Acceptance Rate | Percentage of payee-created requests accepted and authorized by payers. |
| Request Rejection Rate | Percentage of payee-created requests rejected by payers before authorization. |
| Request Expiration Rate | Percentage of payee-created requests that expire without payer authorization. |
| Request Query or Dispute Rate | Percentage of payee-created requests that generate payer query, clarification, or dispute before authorization. |
| Request Completion Rate | Percentage of payee-created requests that are accepted, funded, and successfully paid out. |
| Payee Profitability | Contribution margin attributable to a payee after revenue, verification, request, support, payout, risk, refund, and chargeback costs. |

All metrics should have one approved definition in `DOC-18`.

---

## 10. Fee Model Considerations

PayPlus may use one or more fee model structures.

| Fee Model | Description | Benefits | Risks |
| --- | --- | --- | --- |
| Percentage fee | User or payer pays a percentage of bill amount. | Aligns revenue with transaction value. | May be expensive for high-value bills. |
| Fixed fee | User or payer pays a fixed amount. | Simple and predictable. | May be uneconomic for low-value transactions if too low. |
| Percentage plus fixed fee | User or payer pays percentage and fixed component. | Covers both value-based and fixed costs. | More complex disclosure. |
| Tiered fee | Fee varies by bill amount, category, card type, user segment, payee type, or request creator type. | Can optimize margin. | Harder to explain and govern. |
| Category-based fee | Fee varies by bill category. | Reflects risk and cost differences. | May create fairness or disclosure concerns. |
| Payment-method-based fee | Fee varies by card type or funding source. | Reflects different processing costs. | May be restricted by law, card network, or partner rules. |
| Request-origin-based fee | Fee varies depending on whether request is payer-created or payee-created. | Reflects different cost and conversion dynamics. | May confuse users or create inconsistent incentives. |
| Payee-paid request fee | Payee pays per request created, sent, accepted, funded, or completed. | Monetizes payee-side demand. | Can create spam incentives if charged only on completion or payee dissatisfaction if charged before acceptance. |
| Payee onboarding fee | Payee pays to onboard or activate. | Offsets verification and setup cost. | May reduce payee adoption and may be hard to refund. |
| Payee subscription fee | Payee pays recurring fee for portal, reporting, or request tools. | Predictable revenue. | Requires subscription governance, cancellation rules, and support. |
| Split payer/payee fee | Fee is shared between payer and payee. | Can reduce payer friction. | Requires clear allocation, disclosure, accounting, and dispute treatment. |
| Payee-subsidized payer fee | Payee funds part or all of payer fee. | Improves payer conversion. | Requires contract, reporting, and campaign controls. |
| Partner-subsidized fee | User fee reduced by partner funding. | Supports growth and acquisition. | Requires careful campaign accounting. |
| Promotional fee | Temporary discounted fee. | Drives adoption. | Can create negative margins if uncontrolled. |

Fee models must be transparent before payer confirmation.

Any fee model that distinguishes by card type, issuer, funding source, jurisdiction, category, request creator type, payee type, payer segment, or user segment must be reviewed for legal, card network, partner, consumer protection, tax, and accounting constraints.

---

## 11. Fee Disclosure Requirements

At a minimum, payers should be shown before payment confirmation:

- Bill amount.
- Payee or biller, where applicable.
- Request creator or request origin, where applicable.
- Service fee charged to payer.
- Taxes, if applicable.
- Promotion or discount, if applicable.
- Total amount charged to payer.
- Expected payout amount.
- Expected payment timing or processing window.
- Refund or cancellation limitations.
- Statement that payment completion may depend on verification, partner processing, payout processing, or payee acceptance where applicable.
- For payee-created requests, statement that the request was created by the payee and will not be paid unless the payer authorizes payment.

Where payees are charged fees, payee-facing disclosures should include, as applicable:

- Payee onboarding fee.
- Payee subscription or platform fee.
- Request creation, delivery, acceptance, completion, payout, or exception fees.
- Trigger point for each fee.
- Refundability or non-refundability of payee fees.
- Payout amount net of payee-side fees, if applicable.
- Timing of payee billing or deduction.
- Payee cancellation or withdrawal implications.
- Dispute, chargeback, refund, and reversal implications.
- Tax treatment or tax-inclusive/tax-exclusive presentation, where applicable.

Final disclosure language belongs in:

- `DOC-07 Content, Disclosure & User Communication`.
- `DOC-08 Notification, Receipt & Communication Rules`.

---

## 12. Category-Level Economics

Each bill category should be assessed separately.

Category economics may vary due to:

- Average transaction value.
- Card processing cost.
- Payout method.
- Bill evidence quality.
- Payee verification effort.
- Payee onboarding cost.
- Payee type and payee concentration.
- Request creator type.
- Payer acceptance rate for payee-created requests.
- Request rejection, query, dispute, and expiration rates.
- Manual review rate.
- Fraud risk.
- Fake invoice or fake rent risk.
- Payer-payee collusion or self-payment risk.
- Chargeback risk.
- Refund rate.
- User or payer willingness to pay.
- Payee willingness to pay.
- Partner willingness to subsidize.
- Operational complexity.
- Regulatory or partner restrictions.
- Customer and payee support burden.

Recommended category commercial assessment:

| Assessment Area | Question |
| --- | --- |
| Demand | Is there meaningful payer and/or payee demand for this category? |
| Willingness to pay | Will payers, payees, billers, or partners accept required fees? |
| Cost | Are direct and allocated costs acceptable? |
| Risk | Are fraud, chargeback, fake bill, fake invoice, fake rent, and cashout risks manageable? |
| Review effort | Can the category and evidence be reviewed efficiently? |
| Payee onboarding effort | Can payees in this category be onboarded and verified efficiently? |
| Request conversion | For payee-created requests, are payer acceptance and completion rates commercially viable? |
| Partner feasibility | Do PSP/acquirer and payout partners support this category and request model? |
| Compliance feasibility | Is the category acceptable under legal and compliance review? |
| Margin | Does the category meet minimum contribution margin threshold? |
| Scalability | Can the category scale without excessive manual, payee support, dispute, or reconciliation effort? |

---

## 13. Multi-Card or Multi-Source Payment Economics

Multi-card or multi-source payments may increase user value but also increase cost and operational complexity.

Economic considerations include:

- Multiple authorization fees.
- Multiple capture fees.
- Higher PSP costs.
- Higher decline or partial failure rates.
- More complex refund allocation.
- More complex chargeback handling.
- More complex reconciliation.
- Higher support cost.
- Higher fraud and abuse risk.
- More complex fee disclosure.
- Possible partner or card network restrictions.
- Need to reserve or release partial funding if full bill payment fails.
- For payee-created requests, need to ensure the payer authorizes the full request and each funding allocation before any funding attempt.
- For payee-created requests, need to define whether payee-side request or payout fees apply once, per funding source, or only after completion.

Multi-card functionality should not be launched unless the economic and operational impact is understood.

At minimum, downstream documents should define:

- Whether PayPlus charges one service fee or multiple service fees.
- How fees are allocated across funding sources.
- What happens if one card authorization succeeds and another fails.
- What happens if payout cannot proceed after partial funding.
- How refunds are allocated.
- How chargebacks are handled when only one funding source disputes.
- How reconciliation records parent and child payment events.
- Whether promotions apply per transaction, per card, per user, per payee, per request, or per bill.
- How payee-created request status and payee visibility are handled during partial or failed funding.

Detailed logic belongs in:

- `DOC-09 Payment Request, Multi-Funding Source & Settlement`.
- `DOC-11 Refund, Cancellation & Chargeback`.
- `DOC-13 Promotion Engine & Campaign Rules`.
- `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 14. Promotion and Subsidy Economics

Promotions should be commercially controlled.

Promotion cost may include:

- Cashback.
- Discounts.
- Credits.
- Fee waivers.
- Partner-funded offers.
- Payee-funded payer discounts.
- Payee onboarding incentives.
- Payee request fee waivers.
- Reward points.
- Referral bonuses.
- Advertising credits.
- Sponsored placement costs.
- Campaign operations cost.

Each promotion should define:

- Funding source.
- Whether the promotion applies to payer, payee, or both.
- Whether promotion eligibility differs for payer-created versus payee-created requests.
- Budget.
- Eligibility.
- Maximum benefit.
- Redemption rules.
- Expiration.
- Reversal rules.
- Refund treatment.
- Chargeback treatment.
- Payee withdrawal or payer rejection treatment.
- Tax and accounting treatment.
- Reporting requirements.
- Approval owner.

Promotions should not be allowed to create uncontrolled negative margin.

For payee-created requests, promotion economics must define whether the payer, payee, PayPlus, partner, or campaign sponsor bears the cost of any discount, fee waiver, reward, or incentive.

Detailed promotion rules belong in `DOC-13 Promotion Engine & Campaign Rules`.

---

## 15. Refund, Cancellation, Rejection, Dispute, and Chargeback Economics

Refunds, cancellations, payer rejections, payer queries, disputes, payee withdrawals, and chargebacks can materially affect unit economics.

Economic considerations include:

- Whether PayPlus refunds the service fee.
- Whether PSP fees are returned or retained.
- Whether payout has already occurred.
- Whether payout can be reversed.
- Whether PayPlus bears the loss.
- Whether the payee bears the loss.
- Whether partner agreements define recovery rights.
- Whether the transaction was promotional.
- Whether a chargeback fee applies.
- Whether manual investigation is required.
- Whether user, payer, or payee account restrictions are required after dispute.
- Whether evidence can support representment.
- Whether a payee-created request was rejected or disputed before payment authorization.
- Whether a payee-created request was withdrawn before payer authorization.
- Whether payee-side fees are refundable if a request is rejected, expired, cancelled, disputed, or withdrawn.
- Whether payee-side fees are reversed after payer chargeback or refund.
- Whether payer query or dispute handling creates support costs before any revenue is earned.

Downstream documents must define:

- Fee refund rules.
- Payee-side fee refund rules.
- Partial refund rules.
- Failed payout refund rules.
- Pre-authorization payer rejection and query handling.
- Payee request withdrawal rules.
- Chargeback liability.
- Dispute evidence.
- Loss allocation.
- Revenue reversal.
- Promotion reversal.
- Accounting entries.
- Ledger treatment.

Detailed rules belong in:

- `DOC-10 Payout & Reconciliation`.
- `DOC-11 Refund, Cancellation & Chargeback`.
- `DOC-18 Data Model, Transaction Ledger & Reporting`.

---

## 16. Working Capital and Settlement Timing

PayPlus must understand timing differences between:

- Payee-created request creation.
- Payer invitation or request delivery.
- Payer review and acceptance.
- User card authorization.
- Card capture.
- PSP settlement to PayPlus or partner account.
- Holdbacks or reserves.
- Payout initiation.
- Payout completion.
- Payee payout availability or payee receipt timing.
- Payee-side billing or fee deduction timing.
- Refund eligibility.
- Chargeback window.
- Revenue recognition.
- Fee settlement.
- Partner, biller, or payee invoice or revenue share settlement.

Settlement timing may create working capital needs if PayPlus pays the biller or payee before card funds are fully settled and available.

Commercial assessment should include:

- Expected settlement delay.
- Payout delay.
- Funding gap.
- Reserve requirement.
- Chargeback exposure period.
- Refund exposure period.
- Liquidity buffer requirement.
- Float or prefunding needs.
- Partner settlement schedule.
- Payee settlement expectations.
- Payee payout timing representations.
- Bank cutoff times.
- Weekend and holiday effects.

PayPlus should avoid payout timing models that create unacceptable credit, liquidity, or fraud exposure unless approved.

Payee-facing payout timing should not be commercially promised unless supported by the approved settlement and liquidity model.

---

## 17. Reserve, Holdback, and Collateral Considerations

PSPs, acquirers, banks, payout providers, or payment partners may require reserves, rolling reserves, holdbacks, collateral, prefunding, delayed settlement, or payee-specific reserves.

These arrangements can affect:

- Cash flow.
- Working capital.
- Contribution margin.
- Growth capacity.
- Risk appetite.
- Launch feasibility.
- Partner selection.
- Financial reporting.
- Payee payout timing.
- Payee economics.
- Category expansion.

Commercial assessment should model:

- Reserve percentage.
- Reserve release timing.
- Holdback amount.
- Prefunding requirement.
- Minimum balance requirement.
- Collateral requirement.
- Payee-specific reserve or payout hold policy, if applicable.
- Impact on cash runway.
- Impact on category expansion.
- Impact on payee onboarding and retention.

---

## 18. Partner Economics

Partner economics should be assessed before selection.

Partner cost and revenue factors may include:

- Setup fees.
- Monthly minimum fees.
- Transaction fees.
- Percentage fees.
- Gateway fees.
- Authorization fees.
- Capture fees.
- Refund fees.
- Chargeback fees.
- Payout fees.
- Account verification fees.
- KYC/KYB fees.
- Payee onboarding or sub-merchant onboarding fees.
- Payee screening fees.
- Landlord or business verification fees.
- Payout account verification fees.
- Request delivery or notification fees.
- Risk screening fees.
- OCR/document AI fees.
- Support fees.
- Reserve requirements.
- Payee-specific holdback requirements.
- Revenue share requirements.
- Contract minimums.
- Early termination costs.
- SLA penalties.
- Data export costs.
- Migration costs.

Partner comparison should include both direct pricing and operational implications.

For payee-created request models, partner assessment should include whether partner pricing changes based on:

- Payee type.
- Request creator type.
- Merchant, sub-merchant, biller, agent, beneficiary, or payee classification.
- Category such as rent, invoice, education, utilities, or insurance.
- Payout timing.
- Chargeback risk.
- Payee onboarding model.
- Platform or marketplace treatment.

Detailed partner assessment belongs in `DOC-03 Regulatory, PSP & Acquirer Assessment`.

---

## 19. Pricing Governance

Pricing changes can affect user trust, payer trust, payee adoption, compliance, margins, partner obligations, tax treatment, and product behavior.

Pricing changes should be governed through an approved change process.

At minimum, material pricing changes should include:

- Business rationale.
- Affected categories.
- Affected users or payers.
- Affected payees or payee types.
- Affected geographies.
- Affected request creator types.
- Effective date.
- Expected margin impact.
- Expected conversion impact.
- Expected payee adoption or churn impact.
- Compliance review.
- Legal or consumer protection review, where applicable.
- Tax/accounting review, where applicable.
- User, payer, or payee communication plan.
- Systems and QA impact.
- Approval record.

Pricing changes should be reflected in:

- Product requirements.
- Fee calculation logic.
- User, payer, and payee disclosures.
- Receipts.
- Payee statements or payout reports, if applicable.
- Ledger and reporting.
- Customer support scripts.
- Payee support scripts.
- Terms or policies, if applicable.

---

## 20. Commercial Viability Gates

Each category, payment method, request creator model, payee type, promotion, or partner program should pass commercial viability gates before launch.

Recommended gates:

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC02-001` | Revenue model defined | Revenue source and fee structure are documented. |
| `GATE-DOC02-002` | Cost model defined | Direct and material allocated costs are documented. |
| `GATE-DOC02-003` | Contribution margin modeled | Expected contribution margin is calculated using approved assumptions. |
| `GATE-DOC02-004` | Risk loss assumptions included | Fraud, chargeback, refund, fake invoice, fake rent, collusion, and operational losses are included where applicable. |
| `GATE-DOC02-005` | Partner pricing confirmed | PSP, acquirer, payout, payee onboarding, verification, and other partner pricing is confirmed or conservatively estimated. |
| `GATE-DOC02-006` | Promotion economics approved | Campaign budget, funding source, cost bearer, and margin impact are approved. |
| `GATE-DOC02-007` | Settlement timing assessed | Working capital, reserve, holdback, payout timing, and payee settlement impacts are assessed. |
| `GATE-DOC02-008` | Legal/tax/accounting review completed | Relevant treatment of fees, payee-side fees, taxes, and revenue recognition is reviewed. |
| `GATE-DOC02-009` | Reporting requirements defined | Required metrics and reports are documented. |
| `GATE-DOC02-010` | Launch approval obtained | Commercial approver signs off before launch. |
| `GATE-DOC02-011` | Payee-created request economics approved | Payee onboarding, request creation, request delivery, evidence review, acceptance rate, support, payout, fraud, and dispute economics are modeled and approved before enabling payee-created requests. |
| `GATE-DOC02-012` | Payee-side pricing approved | Any payee onboarding, subscription, request, payout, platform, or other payee-side fee is documented, disclosed, legally reviewed, and reportable before launch. |
| `GATE-DOC02-013` | Rent or invoice economics approved | Rent or invoice request economics include landlord/business verification, evidence review, enhanced fraud risk, support cost, dispute cost, and chargeback assumptions before launch. |

---

## 21. Reporting and Metrics

PayPlus should be able to report commercial performance at transaction, request, category, user, payer, payee, partner, request-origin, and campaign level.

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
| Fake invoice or fake rent loss | Losses or prevented losses tied to fraudulent payee-created requests. |
| Chargeback loss | Principal and fee losses from chargebacks. |
| Refund rate | Refunds as count or value percentage. |
| Chargeback rate | Chargebacks as count or value percentage. |
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
| Request rejection rate | Percentage of payee-created requests rejected by payers. |
| Request query or dispute rate | Percentage of payee-created requests queried or disputed before authorization. |
| Request expiration rate | Percentage of payee-created requests expiring without authorization. |
| Request completion rate | Percentage of payee-created requests accepted, funded, and paid out. |
| Payee activation rate | Percentage of onboarded payees that create at least one valid request. |
| Payee retention rate | Percentage of payees that continue creating valid requests over time. |

Final metric definitions belong in `DOC-18`.

---

## 22. Data and Ledger Expectations

Commercial reporting requires accurate transaction, request, payee, and ledger records.

At minimum, PayPlus should track:

- Bill amount.
- Funded amount.
- Payout amount.
- Service fee.
- Payer fee.
- Payee fee.
- Payee onboarding fee.
- Payee subscription fee.
- Payee request fee.
- Payee payout fee.
- Platform fee.
- Discount amount.
- Promotion amount.
- Partner funding amount.
- Tax amount, if applicable.
- Card processing cost.
- Payout cost.
- Payee onboarding cost allocation.
- Payee verification cost allocation.
- Request delivery cost allocation.
- Evidence review cost allocation.
- Payer query or dispute cost allocation.
- Payee support cost allocation.
- Refund amount.
- Chargeback amount.
- Chargeback fee.
- Fraud loss amount.
- Revenue share amount.
- Net revenue amount.
- Contribution margin estimate.
- Funding source type.
- Card type or category, if permitted.
- Payment route.
- Payout route.
- Bill category.
- User or payer segment.
- Payee ID.
- Payee type.
- Payee onboarding status.
- Request creator type.
- Payee-created request status.
- Payer response status.
- Partner ID.
- Campaign ID.
- Transaction status.
- Payout status.
- Reconciliation status.

Detailed data model and ledger design belong in `DOC-18`.

---

## 23. Accounting, Tax, and Revenue Recognition Considerations

Finance and Legal/Tax must determine:

- Whether PayPlus acts as principal or agent in relevant transaction flows.
- Whether treatment differs for payer-created and payee-created requests.
- Whether onboarded payees are treated as billers, merchants, sub-merchants, agents, beneficiaries, customers, suppliers, or another classification for accounting and tax purposes.
- Whether user, payer, payee, biller, platform, subscription, request, onboarding, payout, and partner fees are recognized gross or net.
- When revenue is recognized for payer fees.
- When revenue is recognized for payee-side fees.
- How rejected, expired, withdrawn, cancelled, or disputed payee-created requests affect revenue recognition.
- How refunds affect revenue.
- How chargebacks affect revenue and losses.
- How promotion costs are classified.
- How partner-funded or payee-funded incentives are treated.
- Whether taxes apply to payer fees, payee fees, platform fees, subscription fees, request fees, or payout fees.
- Whether withholding, VAT, GST, sales tax, or other transaction taxes apply.
- Whether payout amounts are treated as pass-through funds.
- How reserves and holdbacks are recorded.
- How unpaid, pending, failed, reversed, withdrawn, expired, rejected, or disputed transactions and requests are reported.

This document provides a framework only and does not establish accounting or tax policy.

---

## 24. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC02-001` | Users or payers will accept a service fee high enough to cover card processing and payout cost in at least one MVP category. | Commercial / Product | Open |
| `ASM-DOC02-002` | PSP/acquirer pricing will allow positive contribution margin for target categories. | Commercial / Payments | Open |
| `ASM-DOC02-003` | Payout cost can be kept low enough for target transaction sizes. | Finance / Payments | Open |
| `ASM-DOC02-004` | Fraud and chargeback losses can be controlled through verification and risk rules. | Risk / Finance | Open |
| `ASM-DOC02-005` | Manual review cost is acceptable during MVP volume levels. | Operations / Finance | Open |
| `ASM-DOC02-006` | Promotions can be capped and tracked to avoid uncontrolled losses. | Growth / Finance | Open |
| `ASM-DOC02-007` | Partner-funded campaigns can be reconciled and invoiced accurately. | Commercial / Finance | Open |
| `ASM-DOC02-008` | Transaction data will support category, partner, campaign, payee, request-origin, and margin reporting. | Finance / Engineering | Open |
| `ASM-DOC02-009` | Reserve and settlement timing will not create unacceptable working capital needs. | Finance / Payments | Open |
| `ASM-DOC02-010` | Tax and accounting treatment will not materially undermine the selected fee model. | Finance / Legal / Tax | Open |
| `ASM-DOC02-011` | Payee-created requests can produce incremental completed payment volume that justifies onboarding, verification, request delivery, support, and review costs. | Commercial / Product / Finance | Open |
| `ASM-DOC02-012` | Approved payees will accept payee-side fees, reduced payout amounts, or other commercial terms if such models are selected. | Commercial / Product | Open |
| `ASM-DOC02-013` | Payers will accept payee-created requests at a rate sufficient to make the payee-created request model commercially viable. | Product / Commercial | Open |
| `ASM-DOC02-014` | Payee onboarding and verification costs can be recovered through transaction margin, payee-side revenue, partner funding, or strategic value. | Commercial / Finance / Risk | Open |
| `ASM-DOC02-015` | Payee-created rent or invoice requests can be controlled without fraud, dispute, support, or chargeback costs exceeding margin. | Risk / Finance / Operations | Open |
| `ASM-DOC02-016` | Ledger and reporting data will support request creator type, payee type, payer response, payee-side fee, and request-funnel reporting. | Finance / Engineering | Open |

---

## 25. Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC02-001` | Fees must be disclosed before user or payer payment confirmation. | Requires transparent quote and checkout design. | Product / Legal |
| `CON-DOC02-002` | Pricing must comply with applicable law, card network rules, and partner restrictions. | May limit surcharging, card-type-based fees, payee-side fees, or request-origin-based fees. | Legal / Compliance / Payments |
| `CON-DOC02-003` | Promotions must have approved budgets and controls. | Prevents uncontrolled negative margin. | Growth / Finance |
| `CON-DOC02-004` | Settlement timing may limit payout speed. | May require delayed payout or liquidity buffer. | Finance / Payments |
| `CON-DOC02-005` | Partner reserves or holdbacks may constrain growth. | Affects cash flow and capital planning. | Finance / Commercial |
| `CON-DOC02-006` | Accounting and tax treatment must be confirmed before launch. | May affect pricing, reporting, and contracts. | Finance / Legal / Tax |
| `CON-DOC02-007` | Negative-margin transactions must be approved or blocked unless strategically justified. | Requires margin monitoring and approval process. | Finance / Commercial |
| `CON-DOC02-008` | Commercial reporting depends on reliable ledger and reconciliation data. | Requires engineering and finance alignment. | Finance / Engineering |
| `CON-DOC02-009` | Multi-card payments may increase processing and support costs. | May require higher fees or deferral from MVP. | Product / Payments |
| `CON-DOC02-010` | Category expansion must pass commercial viability gates. | Controls rollout sequence. | Product / Commercial |
| `CON-DOC02-011` | Payee-created request enablement must pass commercial viability gates before launch. | Requires modeling onboarding, request delivery, acceptance, support, risk, payout, and dispute costs. | Commercial / Product / Finance |
| `CON-DOC02-012` | Payee-side fees must be disclosed, contractually supported, and reportable before implementation. | Requires payee pricing, billing, ledger, tax, and communication readiness. | Commercial / Legal / Finance |
| `CON-DOC02-013` | Payer must not be charged for a payee-created request before explicit payer authorization. | Prevents revenue capture before authorization and affects request-funnel economics. | Product / Payments / Legal |
| `CON-DOC02-014` | Payee-created rent or invoice requests may require higher fees, limits, or deferral if review, fraud, or support costs are too high. | May constrain category rollout or payee-side pricing. | Commercial / Risk / Product |

---

## 26. Dependencies

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

## 27. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC02-001` | Card processing costs exceed user or payer willingness to pay. | Negative margin or low conversion. | Test pricing, model category margins, and consider partner subsidies. | Commercial / Product | Open |
| `RISK-DOC02-002` | PSP/acquirer pricing or reserves make model uneconomic. | Launch delay or margin failure. | Compare multiple providers and model reserve impact. | Commercial / Payments | Open |
| `RISK-DOC02-003` | Promotions create uncontrolled losses. | Cash burn and distorted unit economics. | Use campaign budgets, caps, eligibility, and margin reporting. | Growth / Finance | Open |
| `RISK-DOC02-004` | Chargebacks or fraud losses exceed assumptions. | Margin loss and partner risk. | Strong risk controls, limits, monitoring, and evidence retention. | Risk / Finance | Open |
| `RISK-DOC02-005` | Manual review costs are underestimated. | Lower contribution margin and operational bottlenecks. | Track review time and automate high-volume checks. | Operations / Finance | Open |
| `RISK-DOC02-006` | Fee disclosures are unclear or non-compliant. | Complaints, chargebacks, regulatory risk. | Legal and compliance review of checkout and receipt language. | Product / Legal | Open |
| `RISK-DOC02-007` | Settlement timing creates liquidity pressure. | Working capital gap and delayed payouts. | Model settlement schedules, reserves, and liquidity buffers. | Finance / Payments | Open |
| `RISK-DOC02-008` | Reporting data cannot support margin analysis. | Poor commercial decisions and audit gaps. | Define data model and ledger fields before launch. | Finance / Engineering | Open |
| `RISK-DOC02-009` | Accounting or tax treatment changes economics. | Pricing, reporting, or contract redesign. | Obtain Finance and Tax review before pricing approval. | Finance / Legal / Tax | Open |
| `RISK-DOC02-010` | Category expansion occurs without commercial review. | Scaling negative-margin categories. | Enforce commercial viability gates. | Product / Commercial | Open |
| `RISK-DOC02-011` | Payee-created requests have low payer acceptance or completion rates. | Request delivery, onboarding, support, and review costs may not convert into revenue. | Model funnel economics, pilot with limits, and monitor acceptance rate. | Commercial / Product | Open |
| `RISK-DOC02-012` | Payee onboarding and verification costs are underestimated. | Payee-created request model may be uneconomic. | Track cost per approved payee and require payee-type-level margin reporting. | Commercial / Operations | Open |
| `RISK-DOC02-013` | Payee-side fees reduce payee adoption. | Lower request volume and weaker network growth. | Test pricing, segment by payee type, and consider partner subsidies. | Commercial / Product | Open |
| `RISK-DOC02-014` | Payee-created requests increase support and dispute costs. | Margin erosion and operational backlog. | Track payer queries, disputes, payee tickets, and review cost. | Operations / Finance | Open |
| `RISK-DOC02-015` | Fake invoice, fake rent, or collusive request losses exceed assumptions. | Fraud losses, chargebacks, partner risk, and negative margin. | Include enhanced risk loss assumptions and require controls before scaling. | Risk / Finance | Open |
| `RISK-DOC02-016` | Payee-created rent requests have high evidence review cost. | Rent category may be commercially unattractive. | Pilot rent separately and model landlord verification and tenancy review cost. | Commercial / Risk | Open |
| `RISK-DOC02-017` | Payee-side billing, refunds, or fee reversals are not ledgered correctly. | Revenue leakage, disputes, accounting errors, audit gaps. | Define payee fee ledger fields and reconciliation requirements in DOC-18. | Finance / Engineering | Open |
| `RISK-DOC02-018` | Payer-facing and payee-facing fee allocation is confusing. | Complaints, disputes, regulatory risk, and lower conversion. | Require clear disclosures and pricing QA before launch. | Product / Legal | Open |
| `RISK-DOC02-019` | Payee payout timing expectations create commercial or liquidity pressure. | Support burden, trust loss, or unsafe early payout. | Align payout communications with settlement and risk model. | Finance / Operations | Open |
| `RISK-DOC02-020` | Payee-created request spam creates notification, support, and review costs without revenue. | Negative request-level economics and user dissatisfaction. | Apply request limits, payee controls, abuse monitoring, and commercial gating. | Commercial / Risk | Open |

---

## 28. Downstream Document Impact

`DOC-02` should guide downstream documents as follows:

| Downstream Document | Impact |
| --- | --- |
| `DOC-03` | Include PSP/acquirer pricing, reserve, category support, payout model, commercial restrictions, payee onboarding economics, payee classification, and payee-created request support in partner assessment. |
| `DOC-04` | Include commercial viability gates for payee-created requests, payee-side pricing, rent/invoice economics, and launch/change governance. |
| `DOC-05` | Convert fee quote, pricing display, promotion handling, commercial eligibility, payee-side pricing, request-origin reporting, and payee profitability requirements into product requirements. |
| `DOC-07` | Define user-facing, payer-facing, and payee-facing pricing, fee, promotion, timing, request-origin, and authorization disclosures. |
| `DOC-08` | Define receipts, fee breakdowns, payee statements, refund messages, promotion notifications, request invitations, and payer/payee status messages. |
| `DOC-09` | Define funding, fee calculation, payer authorization, payee-created request fee treatment, multi-card fee allocation, and failed authorization behavior. |
| `DOC-10` | Define payout cost, payee-side fee deduction if applicable, settlement timing, reconciliation, and financial exception handling. |
| `DOC-11` | Define refund, cancellation, payer rejection, payee withdrawal, chargeback, loss allocation, payee fee reversal, and fee reversal rules. |
| `DOC-13` | Define campaign budgets, promotion cost, partner/payee funding, eligibility, reversal, abuse controls, payer/payee cost allocation, and reporting. |
| `DOC-14` | Include fraud, fake invoice, fake rent, request abuse, chargeback, and payee-created request losses in risk appetite and controls. |
| `DOC-18` | Define ledger fields, request creator type, payee type, payer response status, payee-side fees, metric definitions, revenue, cost, margin, campaign, request-origin, and partner reporting. |
| `DOC-20` | Include commercial readiness, pricing, payee-side fee, request-origin, and payee-created request economics test cases in launch checklist. |
| `DOC-21` | Include operational monitoring for margin-impacting exceptions, payee onboarding costs, request spam, payout failures, refunds, chargebacks, payer disputes, and payee support burden. |

---

## 29. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC02-001` | What service fee model will be used for MVP? | Commercial / Product | Critical | Open |
| `OQ-DOC02-002` | What is the target minimum contribution margin per transaction and by category? | Finance / Commercial | Critical | Open |
| `OQ-DOC02-003` | What PSP/acquirer pricing assumptions should be used before contracts are signed? | Payments / Commercial | Critical | Open |
| `OQ-DOC02-004` | What payout provider pricing assumptions should be used? | Payments / Commercial | High | Open |
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
| `OQ-DOC02-015` | Are payee-created payment requests included in MVP, pilot, or post-MVP scope from a commercial perspective? | Project Owner / Commercial / Product | Critical | Open |
| `OQ-DOC02-016` | Which payee types can be commercially supported for request creation? | Commercial / Product / Risk | Critical | Open |
| `OQ-DOC02-017` | Are payees charged onboarding, subscription, invoice, request, payout, platform, or transaction fees? | Commercial / Finance / Product | Critical | Open |
| `OQ-DOC02-018` | If payee-side fees are charged, when are they charged: onboarding, request creation, request delivery, payer acceptance, funding, payout, monthly, or another trigger? | Commercial / Finance / Product | High | Open |
| `OQ-DOC02-019` | Are payee-side fees refundable if a request is rejected, expired, disputed, cancelled, withdrawn, refunded, or charged back? | Finance / Legal / Product | High | Open |
| `OQ-DOC02-020` | What payer acceptance rate is required for payee-created requests to be commercially viable? | Commercial / Product | High | Open |
| `OQ-DOC02-021` | What payee onboarding cost and payee acquisition cost are acceptable by payee type? | Commercial / Finance | High | Open |
| `OQ-DOC02-022` | What support cost assumptions apply to payee onboarding, payer queries, payer disputes, and payee payout questions? | Operations / Finance | High | Open |
| `OQ-DOC02-023` | What commercial model applies to landlord-created rent requests if rent is enabled? | Commercial / Legal / Risk | Critical | Open |
| `OQ-DOC02-024` | What commercial model applies to invoice requests if business or service-provider payees are enabled? | Commercial / Legal / Risk | High | Open |
| `OQ-DOC02-025` | Can payees subsidize payer service fees, and how should those subsidies be disclosed, recorded, and reversed? | Commercial / Finance / Legal | High | Open |
| `OQ-DOC02-026` | What request, notification, or review limits are required to prevent payee-created request spam from creating negative economics? | Commercial / Risk / Operations | High | Open |
| `OQ-DOC02-027` | What margin threshold must payee-created request flows meet before scale-up? | Finance / Commercial | High | Open |
| `OQ-DOC02-028` | What payee-level reporting is required for payout, fees, request volume, disputes, refunds, and tax/accounting purposes? | Finance / Product / Engineering | Medium | Open |

---

## 30. Acceptance Criteria

`DOC-02` is acceptable when it clearly defines:

- Commercial objective.
- Candidate business model components.
- Revenue streams.
- Cost components.
- Transaction-level unit economics formula.
- Payee-created request unit economics formula.
- Key economic definitions.
- Fee model considerations.
- Fee disclosure expectations.
- Category-level economics.
- Payee-type-level economics.
- Request-creator-type economics.
- Multi-card or multi-source payment economics.
- Promotion and subsidy economics.
- Refund, cancellation, payer rejection, payee withdrawal, dispute, and chargeback economics.
- Working capital and settlement timing considerations.
- Reserve, holdback, and collateral considerations.
- Partner economics.
- Pricing governance.
- Commercial viability gates.
- Payee-created request commercial viability gates.
- Reporting and metric expectations.
- Data and ledger expectations.
- Accounting, tax, and revenue recognition considerations.
- Assumptions.
- Constraints.
- Dependencies.
- Risks.
- Downstream document impact.
- Open questions.

This document should remain a commercial framework and should not become a final pricing sheet, accounting policy, tax memo, partner contract, product PRD, or payment processing specification.

---

## 31. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-02 Business Model & Unit Economics. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation commercial framework, added unit economics model, revenue and cost taxonomy, commercial viability gates, pricing governance, promotion economics, settlement and reserve considerations, reporting expectations, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
| `0.3.0` | 2026-05-27 | Product Documentation Team | Updated commercial framework to account for payee onboarding and payee-created bill, invoice, fee, and rent payment request capability introduced in DOC-05 v0.2.0. Added payee-side revenue streams, payee onboarding and verification costs, request-origin economics, payer/payee fee allocation, payee-created request funnel metrics, rent/invoice economics, payee-side pricing governance, new commercial viability gates, expanded reporting and ledger expectations, additional assumptions, constraints, dependencies, risks, and open questions. |
