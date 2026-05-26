---
document_id: DOC-02
title: Business Model & Unit Economics
version: 0.2.0
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
last_updated: 2026-05-26
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

It establishes how PayPlus may generate revenue, incur costs, evaluate transaction profitability, manage promotions, assess partner economics, and determine whether a bill category or payment flow is commercially viable.

`DOC-02` is a foundation document.

It is intended to guide downstream product, payment, promotion, finance, reconciliation, risk, and reporting documentation.

This document does not define final pricing, legal treatment, accounting treatment, tax treatment, promotion rules, payment processing rules, payout rules, reconciliation procedures, or contractual terms.

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
- Promotion and subsidy economics.
- Category-level commercial assessment.
- Multi-card or multi-source payment economics.
- Refund, chargeback, and failed payment economics.
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
- Final merchant or biller pricing.
- Legal fee classification.
- Tax advice.
- Accounting policy.
- PSP/acquirer contract terms.
- Card network rule interpretation.
- Payment state machine.
- Reconciliation process.
- Refund or chargeback operating procedure.
- Promotion campaign rule logic.
- Risk thresholds.
- AML controls.
- Product requirements.
- Technical architecture.
- Data schema.

These items must be defined in relevant downstream documents.

---

## 4. Commercial Objective

The commercial objective of PayPlus is to create a sustainable bill payment business where transaction revenue, partner funding, or other approved revenue sources exceed the full variable and allocated cost of processing, paying, supporting, and managing each transaction.

PayPlus should only scale categories, payment methods, promotions, or partner programs where unit economics are understood and acceptable.

At minimum, PayPlus should understand profitability at the following levels:

- Transaction level.
- User level.
- Bill category level.
- Campaign level.
- Partner level.
- Payment method level.
- Geography or jurisdiction level.
- Product line level.

---

## 5. Business Model Summary

PayPlus may use one or more business model components.

| Model Component | Description | Candidate Use |
| --- | --- | --- |
| User-paid service fee | User pays a fee for using card-funded bill payment. | Core candidate model. |
| Biller-paid fee | Biller or payee pays PayPlus to receive payments or users. | Possible where biller partnerships exist. |
| Partner-funded subsidy | A partner funds part of transaction cost or user incentive. | Possible for campaigns or acquisition. |
| Promotion-funded model | PayPlus or partner funds discounts, cashback, credits, or rewards. | Growth mechanism; must be controlled. |
| Advertisement or sponsored placement | Approved partners pay for placement or offers. | Future candidate; requires policy and disclosure. |
| Revenue share | PayPlus shares revenue with billers, PSPs, partners, or affiliates. | Possible if contractually allowed. |
| Subscription or membership | User pays recurring fee for preferred pricing or benefits. | Future candidate; requires consumer protection review. |
| Business account fees | Business users pay for invoice or bill payment tools. | Future candidate. |
| API or platform fees | Partners pay for API access or transaction processing. | Future candidate. |

No business model component should be launched until commercial, compliance, legal, accounting, tax, and operational impacts are assessed.

---

## 6. Revenue Streams

Candidate revenue streams include:

| Revenue Stream | Description | Notes |
| --- | --- | --- |
| Service fee | Fee charged to user per transaction. | Must be disclosed before payment confirmation. |
| Percentage fee | Fee calculated as percentage of bill amount or funded amount. | Must account for card processing cost and risk. |
| Fixed fee | Flat fee charged per transaction. | Useful for low-value transactions if user acceptable. |
| Minimum fee | Minimum fee floor to avoid negative economics on small transactions. | Important if fixed costs are material. |
| Partner subsidy | Third party funds part of user cost or PayPlus cost. | Must be contractually documented. |
| Campaign funding | Marketing or partner budget funds rewards or discounts. | Must be tracked at campaign level. |
| Advertisement revenue | Revenue from partner placement or sponsored biller offers. | Requires disclosure and content governance. |
| Revenue share | PayPlus receives or pays a share of fees with partners. | Must be reflected in contribution margin. |
| FX spread or fee | Revenue from currency conversion, if applicable. | Requires explicit approval and disclosure. |
| Late or exception fees | Fees related to failed payment, cancellation, or special handling. | High consumer risk; should require approval. |

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
| Fraud loss | Loss from unauthorized or abusive transactions. | Category, user risk, payee risk. |
| Promotion cost | Discounts, cashback, rewards, credits, partner offers, subsidies. | Campaign design and eligibility. |
| Manual review cost | Operations cost for bill, payee, risk, payout, or support review. | Review time and staffing cost. |
| Customer support cost | Cost of handling user or payee support. | Ticket volume, transaction complexity. |
| KYC/KYB cost | Identity or business verification cost. | Verification provider pricing. |
| Document AI/OCR cost | Bill document extraction or validation cost. | Pages, documents, API calls. |
| Fraud/risk tooling cost | Risk scoring, device intelligence, sanctions screening, monitoring tools. | API calls, users, transactions. |
| Notification cost | SMS, email, push, WhatsApp, or other communication cost. | Channel and message volume. |
| Infrastructure cost | Cloud, storage, database, compute, logging, monitoring. | Usage and retention volume. |
| Reconciliation cost | Finance and operations effort to reconcile transactions. | Transaction volume and exception rate. |
| Compliance cost | Compliance monitoring, audit, advisory, policy, reporting. | Jurisdiction and product complexity. |
| Reserve or holdback cost | Cost of funds or reduced liquidity due to partner reserves. | Reserve rate and release timing. |
| Tax cost | Transaction taxes, VAT/GST/sales tax, withholding, or other tax. | Jurisdiction and fee structure. |

Costs should be modeled conservatively until actual partner pricing and operational data are available.

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
- Notification Cost
- Variable Infrastructure Cost Allocation
- Tax Cost Allocation
= Transaction Contribution Margin
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

The final reporting definitions must be defined in `DOC-18` Data Model, Transaction Ledger & Reporting.

---

## 9. Key Economic Definitions

| Term | Definition |
| --- | --- |
| Gross Transaction Value, or GTV | Total bill payment amount submitted or processed before fees, depending on final reporting definition. |
| Funded Amount | Amount charged to the user funding source. |
| Bill Amount | Amount owed to the biller or payee. |
| Payout Amount | Amount sent to the biller, payee, or receiving account. |
| Gross Revenue | Total revenue earned from user fees, partner fees, campaign funding, or other approved revenue streams. |
| Net Revenue | Gross revenue after refunds, fee reversals, discounts, and revenue share, if defined this way in finance reporting. |
| Direct Cost | Cost directly attributable to a transaction, such as card processing or payout fees. |
| Allocated Cost | Cost assigned to a transaction using an approved allocation method. |
| Contribution Margin | Revenue minus direct and allocated variable costs. |
| Contribution Margin Rate | Contribution margin divided by GTV or another approved denominator. |
| Take Rate | Gross or net revenue divided by GTV, based on approved definition. |
| Promotion Burn | Total cost of discounts, cashback, rewards, credits, or subsidies. |
| Chargeback Loss | Principal, fees, and operational costs lost due to chargebacks. |
| Fraud Loss | Financial losses attributed to fraudulent or abusive activity. |
| Manual Review Cost | Labor cost allocated to bill, payee, risk, compliance, payout, or support review. |

All metrics should have one approved definition in `DOC-18`.

---

## 10. Fee Model Considerations

PayPlus may use one or more fee model structures.

| Fee Model | Description | Benefits | Risks |
| --- | --- | --- | --- |
| Percentage fee | User pays a percentage of bill amount. | Aligns revenue with transaction value. | May be expensive for high-value bills. |
| Fixed fee | User pays a fixed amount. | Simple and predictable. | May be uneconomic for low-value transactions if too low. |
| Percentage plus fixed fee | User pays percentage and fixed component. | Covers both value-based and fixed costs. | More complex disclosure. |
| Tiered fee | Fee varies by bill amount, category, card type, or user segment. | Can optimize margin. | Harder to explain and govern. |
| Category-based fee | Fee varies by bill category. | Reflects risk and cost differences. | May create fairness or disclosure concerns. |
| Payment-method-based fee | Fee varies by card type or funding source. | Reflects different processing costs. | May be restricted by law, card network, or partner rules. |
| Partner-subsidized fee | User fee reduced by partner funding. | Supports growth and acquisition. | Requires careful campaign accounting. |
| Promotional fee | Temporary discounted fee. | Drives adoption. | Can create negative margins if uncontrolled. |

Fee models must be transparent before user confirmation.

Any fee model that distinguishes by card type, issuer, funding source, jurisdiction, category, or user segment must be reviewed for legal, card network, and partner constraints.

---

## 11. Fee Disclosure Requirements

At a minimum, users should be shown before payment confirmation:

- Bill amount.
- Payee or biller, where applicable.
- Service fee.
- Taxes, if applicable.
- Promotion or discount, if applicable.
- Total amount charged.
- Expected payout amount.
- Expected payment timing or processing window.
- Refund or cancellation limitations.
- Statement that payment completion may depend on verification, partner processing, or payee acceptance, where applicable.

Final disclosure language belongs in:

- `DOC-07` Content, Disclosure & User Communication.
- `DOC-08` Notification, Receipt & Communication Rules.

---

## 12. Category-Level Economics

Each bill category should be assessed separately.

Category economics may vary due to:

- Average transaction value.
- Card processing cost.
- Payout method.
- Bill evidence quality.
- Payee verification effort.
- Manual review rate.
- Fraud risk.
- Chargeback risk.
- Refund rate.
- User willingness to pay.
- Partner willingness to subsidize.
- Operational complexity.
- Regulatory or partner restrictions.
- Customer support burden.

Recommended category commercial assessment:

| Assessment Area | Question |
| --- | --- |
| Demand | Is there meaningful user demand for this category? |
| Willingness to pay | Will users accept required service fee? |
| Cost | Are direct and allocated costs acceptable? |
| Risk | Are fraud, chargeback, and cashout risks manageable? |
| Review effort | Can the category be reviewed efficiently? |
| Partner feasibility | Do PSP/acquirer and payout partners support this category? |
| Compliance feasibility | Is the category acceptable under legal and compliance review? |
| Margin | Does the category meet minimum contribution margin threshold? |
| Scalability | Can the category scale without excessive manual effort? |

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

Multi-card functionality should not be launched unless the economic and operational impact is understood.

At minimum, downstream documents should define:

- Whether PayPlus charges one service fee or multiple service fees.
- How fees are allocated across funding sources.
- What happens if one card authorization succeeds and another fails.
- What happens if payout cannot proceed after partial funding.
- How refunds are allocated.
- How chargebacks are handled when only one funding source disputes.
- How reconciliation records parent and child payment events.
- Whether promotions apply per transaction, per card, per user, or per bill.

Detailed logic belongs in:

- `DOC-09` Payment Request, Multi-Funding Source & Settlement.
- `DOC-11` Refund, Cancellation & Chargeback.
- `DOC-13` Promotion Engine & Campaign Rules.
- `DOC-18` Data Model, Transaction Ledger & Reporting.

---

## 14. Promotion and Subsidy Economics

Promotions should be commercially controlled.

Promotion cost may include:

- Cashback.
- Discounts.
- Credits.
- Fee waivers.
- Partner-funded offers.
- Reward points.
- Referral bonuses.
- Advertising credits.
- Sponsored placement costs.
- Campaign operations cost.

Each promotion should define:

- Funding source.
- Budget.
- Eligibility.
- Maximum benefit.
- Redemption rules.
- Expiration.
- Reversal rules.
- Refund treatment.
- Chargeback treatment.
- Tax and accounting treatment.
- Reporting requirements.
- Approval owner.

Promotions should not be allowed to create uncontrolled negative margin.

Detailed promotion rules belong in `DOC-13` Promotion Engine & Campaign Rules.

---

## 15. Refund, Cancellation, and Chargeback Economics

Refunds, cancellations, disputes, and chargebacks can materially affect unit economics.

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
- Whether user account restrictions are required after dispute.
- Whether evidence can support representment.

Downstream documents must define:

- Fee refund rules.
- Partial refund rules.
- Failed payout refund rules.
- Chargeback liability.
- Dispute evidence.
- Loss allocation.
- Revenue reversal.
- Promotion reversal.
- Accounting entries.
- Ledger treatment.

Detailed rules belong in:

- `DOC-10` Payout & Reconciliation.
- `DOC-11` Refund, Cancellation & Chargeback.
- `DOC-18` Data Model, Transaction Ledger & Reporting.

---

## 16. Working Capital and Settlement Timing

PayPlus must understand timing differences between:

- User card authorization.
- Card capture.
- PSP settlement to PayPlus or partner account.
- Holdbacks or reserves.
- Payout initiation.
- Payout completion.
- Refund eligibility.
- Chargeback window.
- Revenue recognition.
- Fee settlement.
- Partner invoice or revenue share settlement.

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
- Bank cutoff times.
- Weekend and holiday effects.

PayPlus should avoid payout timing models that create unacceptable credit, liquidity, or fraud exposure unless approved.

---

## 17. Reserve, Holdback, and Collateral Considerations

PSPs, acquirers, banks, or payment partners may require reserves, rolling reserves, holdbacks, collateral, prefunding, or delayed settlement.

These arrangements can affect:

- Cash flow.
- Working capital.
- Contribution margin.
- Growth capacity.
- Risk appetite.
- Launch feasibility.
- Partner selection.
- Financial reporting.

Commercial assessment should model:

- Reserve percentage.
- Reserve release timing.
- Holdback amount.
- Prefunding requirement.
- Minimum balance requirement.
- Collateral requirement.
- Impact on cash runway.
- Impact on category expansion.

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
- Risk screening fees.
- OCR/document AI fees.
- Support fees.
- Reserve requirements.
- Revenue share requirements.
- Contract minimums.
- Early termination costs.
- SLA penalties.
- Data export costs.
- Migration costs.

Partner comparison should include both direct pricing and operational implications.

Detailed partner assessment belongs in `DOC-03` Regulatory, PSP & Acquirer Assessment.

---

## 19. Pricing Governance

Pricing changes can affect user trust, compliance, margins, partner obligations, tax treatment, and product behavior.

Pricing changes should be governed through an approved change process.

At minimum, material pricing changes should include:

- Business rationale.
- Affected categories.
- Affected users.
- Affected geographies.
- Effective date.
- Expected margin impact.
- Expected conversion impact.
- Compliance review.
- Legal or consumer protection review, where applicable.
- Tax/accounting review, where applicable.
- User communication plan.
- Systems and QA impact.
- Approval record.

Pricing changes should be reflected in:

- Product requirements.
- Fee calculation logic.
- User disclosures.
- Receipts.
- Ledger and reporting.
- Customer support scripts.
- Terms or policies, if applicable.

---

## 20. Commercial Viability Gates

Each category, payment method, promotion, or partner program should pass commercial viability gates before launch.

Recommended gates:

| Gate ID | Gate | Acceptance Condition |
| --- | --- | --- |
| `GATE-DOC02-001` | Revenue model defined | Revenue source and fee structure are documented. |
| `GATE-DOC02-002` | Cost model defined | Direct and material allocated costs are documented. |
| `GATE-DOC02-003` | Contribution margin modeled | Expected contribution margin is calculated using approved assumptions. |
| `GATE-DOC02-004` | Risk loss assumptions included | Fraud, chargeback, refund, and operational losses are included. |
| `GATE-DOC02-005` | Partner pricing confirmed | PSP, acquirer, payout, and other partner pricing is confirmed or conservatively estimated. |
| `GATE-DOC02-006` | Promotion economics approved | Campaign budget, funding source, and margin impact are approved. |
| `GATE-DOC02-007` | Settlement timing assessed | Working capital, reserve, holdback, and payout timing impacts are assessed. |
| `GATE-DOC02-008` | Legal/tax/accounting review completed | Relevant treatment of fees, taxes, and revenue recognition is reviewed. |
| `GATE-DOC02-009` | Reporting requirements defined | Required metrics and reports are documented. |
| `GATE-DOC02-010` | Launch approval obtained | Commercial approver signs off before launch. |

---

## 21. Reporting and Metrics

PayPlus should be able to report commercial performance at transaction, category, user, partner, and campaign level.

Candidate metrics include:

| Metric | Description |
| --- | --- |
| GTV | Total processed or submitted transaction value, based on approved definition. |
| Funded volume | Total value successfully charged to funding sources. |
| Paid-out volume | Total value successfully paid to payees or billers. |
| Gross revenue | Total service fees, partner fees, campaign funding, and other revenue. |
| Net revenue | Gross revenue after discounts, reversals, fee refunds, and revenue share, based on approved definition. |
| Card processing cost | Total and per-transaction card processing costs. |
| Payout cost | Total and per-transaction payout costs. |
| Promotion burn | Total campaign or offer cost. |
| Fraud loss | Losses from fraud or abuse. |
| Chargeback loss | Principal and fee losses from chargebacks. |
| Refund rate | Refunds as count or value percentage. |
| Chargeback rate | Chargebacks as count or value percentage. |
| Manual review cost | Allocated cost of manual review. |
| Support cost | Allocated support cost. |
| Contribution margin | Revenue less variable and allocated costs. |
| Contribution margin rate | Contribution margin as a percentage of approved denominator. |
| Take rate | Revenue as a percentage of GTV. |
| Average transaction value | Average bill or payment amount. |
| Approval rate | Percentage of payment requests approved. |
| Decline rate | Percentage of card payment attempts declined. |
| Payout failure rate | Percentage of payouts that fail. |
| Category profitability | Margin by bill category. |
| Partner profitability | Margin by partner or payment route. |
| Campaign profitability | Margin after campaign cost. |

Final metric definitions belong in `DOC-18`.

---

## 22. Data and Ledger Expectations

Commercial reporting requires accurate transaction and ledger records.

At minimum, PayPlus should track:

- Bill amount.
- Funded amount.
- Payout amount.
- Service fee.
- Discount amount.
- Promotion amount.
- Partner funding amount.
- Tax amount, if applicable.
- Card processing cost.
- Payout cost.
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
- User segment.
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
- Whether user service fees are recognized gross or net.
- When revenue is recognized.
- How refunds affect revenue.
- How chargebacks affect revenue and losses.
- How promotion costs are classified.
- How partner-funded incentives are treated.
- Whether taxes apply to service fees.
- Whether withholding, VAT, GST, sales tax, or other transaction taxes apply.
- Whether payout amounts are treated as pass-through funds.
- How reserves and holdbacks are recorded.
- How unpaid, pending, failed, reversed, or disputed transactions are reported.

This document provides a framework only and does not establish accounting or tax policy.

---

## 24. Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
| --- | --- | --- | --- |
| `ASM-DOC02-001` | Users will accept a service fee high enough to cover card processing and payout cost in at least one MVP category. | Commercial / Product | Open |
| `ASM-DOC02-002` | PSP/acquirer pricing will allow positive contribution margin for target categories. | Commercial / Payments | Open |
| `ASM-DOC02-003` | Payout cost can be kept low enough for target transaction sizes. | Finance / Payments | Open |
| `ASM-DOC02-004` | Fraud and chargeback losses can be controlled through verification and risk rules. | Risk / Finance | Open |
| `ASM-DOC02-005` | Manual review cost is acceptable during MVP volume levels. | Operations / Finance | Open |
| `ASM-DOC02-006` | Promotions can be capped and tracked to avoid uncontrolled losses. | Growth / Finance | Open |
| `ASM-DOC02-007` | Partner-funded campaigns can be reconciled and invoiced accurately. | Commercial / Finance | Open |
| `ASM-DOC02-008` | Transaction data will support category, partner, campaign, and margin reporting. | Finance / Engineering | Open |
| `ASM-DOC02-009` | Reserve and settlement timing will not create unacceptable working capital needs. | Finance / Payments | Open |
| `ASM-DOC02-010` | Tax and accounting treatment will not materially undermine the selected fee model. | Finance / Legal / Tax | Open |

---

## 25. Constraints

| Constraint ID | Constraint | Impact | Owner |
| --- | --- | --- | --- |
| `CON-DOC02-001` | Fees must be disclosed before user payment confirmation. | Requires transparent quote and checkout design. | Product / Legal |
| `CON-DOC02-002` | Pricing must comply with applicable law, card network rules, and partner restrictions. | May limit surcharging or card-type-based fees. | Legal / Compliance / Payments |
| `CON-DOC02-003` | Promotions must have approved budgets and controls. | Prevents uncontrolled negative margin. | Growth / Finance |
| `CON-DOC02-004` | Settlement timing may limit payout speed. | May require delayed payout or liquidity buffer. | Finance / Payments |
| `CON-DOC02-005` | Partner reserves or holdbacks may constrain growth. | Affects cash flow and capital planning. | Finance / Commercial |
| `CON-DOC02-006` | Accounting and tax treatment must be confirmed before launch. | May affect pricing, reporting, and contracts. | Finance / Legal / Tax |
| `CON-DOC02-007` | Negative-margin transactions must be approved or blocked unless strategically justified. | Requires margin monitoring and approval process. | Finance / Commercial |
| `CON-DOC02-008` | Commercial reporting depends on reliable ledger and reconciliation data. | Requires engineering and finance alignment. | Finance / Engineering |
| `CON-DOC02-009` | Multi-card payments may increase processing and support costs. | May require higher fees or deferral from MVP. | Product / Payments |
| `CON-DOC02-010` | Category expansion must pass commercial viability gates. | Controls rollout sequence. | Product / Commercial |

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

---

## 27. Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `RISK-DOC02-001` | Card processing costs exceed user willingness to pay. | Negative margin or low conversion. | Test pricing, model category margins, and consider partner subsidies. | Commercial / Product | Open |
| `RISK-DOC02-002` | PSP/acquirer pricing or reserves make model uneconomic. | Launch delay or margin failure. | Compare multiple providers and model reserve impact. | Commercial / Payments | Open |
| `RISK-DOC02-003` | Promotions create uncontrolled losses. | Cash burn and distorted unit economics. | Use campaign budgets, caps, eligibility, and margin reporting. | Growth / Finance | Open |
| `RISK-DOC02-004` | Chargebacks or fraud losses exceed assumptions. | Margin loss and partner risk. | Strong risk controls, limits, monitoring, and evidence retention. | Risk / Finance | Open |
| `RISK-DOC02-005` | Manual review costs are underestimated. | Lower contribution margin and operational bottlenecks. | Track review time and automate high-volume checks. | Operations / Finance | Open |
| `RISK-DOC02-006` | Fee disclosures are unclear or non-compliant. | Complaints, chargebacks, regulatory risk. | Legal and compliance review of checkout and receipt language. | Product / Legal | Open |
| `RISK-DOC02-007` | Settlement timing creates liquidity pressure. | Working capital gap and delayed payouts. | Model settlement schedules, reserves, and liquidity buffers. | Finance / Payments | Open |
| `RISK-DOC02-008` | Reporting data cannot support margin analysis. | Poor commercial decisions and audit gaps. | Define data model and ledger fields before launch. | Finance / Engineering | Open |
| `RISK-DOC02-009` | Accounting or tax treatment changes economics. | Pricing, reporting, or contract redesign. | Obtain Finance and Tax review before pricing approval. | Finance / Legal / Tax | Open |
| `RISK-DOC02-010` | Category expansion occurs without commercial review. | Scaling negative-margin categories. | Enforce commercial viability gates. | Product / Commercial | Open |

---

## 28. Downstream Document Impact

DOC-02 should guide downstream documents as follows:

| Downstream Document | Impact |
| --- | --- |
| `DOC-03` | Include PSP/acquirer pricing, reserve, category support, payout model, and commercial restrictions in partner assessment. |
| `DOC-04` | Include commercial viability gates in launch readiness and change governance. |
| `DOC-05` | Convert fee quote, pricing display, promotion handling, and commercial eligibility into product requirements. |
| `DOC-07` | Define user-facing pricing, fee, promotion, and timing disclosures. |
| `DOC-08` | Define receipts, fee breakdowns, refund messages, and promotion notifications. |
| `DOC-09` | Define funding, fee calculation, multi-card fee allocation, and failed authorization behavior. |
| `DOC-10` | Define payout cost, settlement timing, reconciliation, and financial exception handling. |
| `DOC-11` | Define refund, cancellation, chargeback, loss allocation, and fee reversal rules. |
| `DOC-13` | Define campaign budgets, promotion cost, partner funding, eligibility, reversal, and reporting. |
| `DOC-14` | Include fraud and chargeback losses in risk appetite and controls. |
| `DOC-18` | Define ledger fields, metric definitions, revenue, cost, margin, campaign, and partner reporting. |
| `DOC-20` | Include commercial readiness and pricing test cases in launch checklist. |
| `DOC-21` | Include operational monitoring for margin-impacting exceptions, payout failures, refunds, and chargebacks. |

---

## 29. Open Questions

| Question ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| `OQ-DOC02-001` | What service fee model will be used for MVP? | Commercial / Product | Critical | Open |
| `OQ-DOC02-002` | What is the target minimum contribution margin per transaction and by category? | Finance / Commercial | Critical | Open |
| `OQ-DOC02-003` | What PSP/acquirer pricing assumptions should be used before contracts are signed? | Payments / Commercial | Critical | Open |
| `OQ-DOC02-004` | What payout provider pricing assumptions should be used? | Payments / Commercial | High | Open |
| `OQ-DOC02-005` | Will PayPlus charge different fees by category, amount, or funding source? | Commercial / Legal / Product | High | Open |
| `OQ-DOC02-006` | Are card surcharges, convenience fees, or payment-method-based fees permitted in the launch jurisdiction and partner model? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC02-007` | What refund and fee reversal rules will apply? | Finance / Payments / Product | High | Open |
| `OQ-DOC02-008` | How will chargeback liability be allocated between PayPlus, users, payees, and partners? | Legal / Finance / Risk | High | Open |
| `OQ-DOC02-009` | What promotion budget and campaign controls are approved for MVP? | Growth / Finance | Medium | Open |
| `OQ-DOC02-010` | What reserve, holdback, or prefunding requirements will partners impose? | Commercial / Payments | High | Open |
| `OQ-DOC02-011` | What accounting treatment applies to service fees, payout amounts, refunds, and promotions? | Finance | Critical | Open |
| `OQ-DOC02-012` | What tax treatment applies to user fees, partner fees, and promotions? | Legal / Tax / Finance | Critical | Open |
| `OQ-DOC02-013` | What data fields are required to calculate transaction margin accurately? | Finance / Engineering | High | Open |
| `OQ-DOC02-014` | What commercial approval process is required before category or pricing changes? | Project Owner / Finance | Medium | Open |

---

## 30. Acceptance Criteria

DOC-02 is acceptable when it clearly defines:

- Commercial objective.
- Candidate business model components.
- Revenue streams.
- Cost components.
- Transaction-level unit economics formula.
- Key economic definitions.
- Fee model considerations.
- Fee disclosure expectations.
- Category-level economics.
- Multi-card or multi-source payment economics.
- Promotion and subsidy economics.
- Refund, cancellation, and chargeback economics.
- Working capital and settlement timing considerations.
- Reserve, holdback, and collateral considerations.
- Partner economics.
- Pricing governance.
- Commercial viability gates.
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
