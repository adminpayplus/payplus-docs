---
title: Business Model & Unit Economics
document_id: DOC-02
version: 0.1.0
status: Draft
last_updated: 2026-05-14
classification: Internal
owner: TBD
approvers: TBD
---

# DOC-02 — Business Model & Unit Economics

## 1. Purpose

This document defines the business model and unit economics framework for PayPlus.

It explains how PayPlus may generate revenue, what major cost drivers affect each payment, and how commercial viability should be measured.

This document supports business planning, pricing decisions, PSP negotiation inputs, product prioritization, and financial review.

---

## 2. Scope

This document covers:

- Business model overview.
- Revenue streams.
- Fee model principles.
- Fee types.
- Key cost drivers.
- Unit economics framework.
- Promotion and subsidy economics at a commercial level.
- Partner advertisement revenue at a commercial level.
- Financial metrics.
- Commercial assumptions.
- Commercial risks.
- Open commercial questions.

This document does not define:

- Detailed payment flows.
- Detailed payout workflows.
- Reconciliation procedures.
- PSP or acquirer selection.
- Legal or regulatory conclusions.
- Full accounting policy.
- Detailed promotion campaign rules.
- Promotion reservation, consumption, or reversal logic.
- Refund and chargeback workflows.
- Fraud thresholds.
- Operational SOPs.
- API design.
- Database schema.
- Pricing approval authority matrix.

Those topics belong in dedicated documents.

---

## 3. Product Context

PayPlus is a **Payment & Bill Settlement Platform**.

PayPlus helps users pay approved bills and eligible payment obligations through supported funding methods.

PayPlus coordinates bill verification, funding, payout, reconciliation, promotion handling, communication, and risk control.

PayPlus is not intended to be:

- A general wallet.
- A stored value facility.
- An unrestricted peer-to-peer transfer product.
- A remittance product.
- A cashout tool.
- A payroll product.
- A general e-commerce checkout product.
- A bank.

The business model must support this positioning.

Commercial design must preserve a clear link between user funding and real bill or payee settlement.

---

## 4. Commercial Objectives

The business model should support the following objectives:

1. Generate sustainable revenue from eligible payment activity.
2. Cover payment processing, payout, risk, support, and operating costs.
3. Preserve clear bill-backed payment positioning.
4. Support controlled growth through promotions and partnerships.
5. Avoid incentives for unsupported cashout or quasi-cash activity.
6. Support flexible pricing across categories, funding methods, and payee types.
7. Support future expansion beyond the Hong Kong MVP market.

---

## 5. Business Model Overview

PayPlus may use one or more commercial models.

| Model | Description | MVP Relevance |
|---|---|---|
| User-paid service fee | User pays a service fee to use PayPlus for an eligible payment obligation | High |
| Payee-paid fee | Payee or biller pays PayPlus for collection or settlement support | Medium |
| Partner-funded promotion | Bank, card issuer, PSP, biller, or partner funds incentives | Medium |
| Platform-funded promotion | PayPlus funds discounts, fee waivers, cashback, or rewards | Medium |
| Partner advertisement revenue | Partner pays for approved exposure or campaign participation | Medium |
| Enterprise or institutional arrangement | PayPlus agrees commercial terms with schools, property managers, service providers, or other billers | Future / Optional |

The MVP business model should prioritize clarity, simplicity, and margin visibility.

---

## 6. Revenue Streams

Potential revenue streams include:

### 6.1 User Service Fees

PayPlus may charge users a service fee for processing an eligible payment obligation.

The fee may vary by:

- Bill category.
- Payment amount.
- Funding method.
- Payee type.
- Promotion eligibility.
- Risk or operational complexity.
- Payout method.

### 6.2 Payee or Biller Fees

PayPlus may charge payees, billers, or institutional partners for payment facilitation, reporting, reconciliation support, or collection support.

This may apply to:

- Schools.
- Property managers.
- Clubs or leisure facilities.
- Telecom or service providers.
- Professional service firms.
- Other approved payees.

### 6.3 Promotion and Campaign Funding

Promotion funding may come from:

- PayPlus.
- Card issuers.
- Banks.
- PSPs.
- Billers.
- Payees.
- Commercial partners.

For unit economics, promotion funding should be treated as either:

- A cost borne by PayPlus.
- A reimbursable partner subsidy.
- A shared commercial cost.
- A revenue-linked campaign arrangement.

Detailed promotion mechanics belong in `DOC-13`.

### 6.4 Partner Advertisement Revenue

PayPlus may support partner advertisement or sponsored campaign revenue if approved for MVP or later phases.

Potential commercial models include:

- Fixed placement fee.
- Campaign fee.
- Cost-per-click.
- Cost-per-action.
- Revenue share.
- Bundled partner campaign package.

Advertisement content, placement, approval workflow, user data use, and campaign operations belong in `DOC-07`, `DOC-13`, and `DOC-15`.

---

## 7. Fee Model Principles

PayPlus pricing should follow these principles:

1. Fees should be transparent before user confirmation.
2. Fees should be explainable.
3. Fees should be traceable in reporting.
4. Fees should reflect cost, risk, and commercial value.
5. Fees should not encourage unsupported cashout or quasi-cash behavior.
6. Fees should preserve bill-backed payment positioning.
7. Fees should support refund and cancellation handling.
8. Fee logic should support parent payment requests and child payment transactions.
9. Fee rules should be configurable, not hardcoded.
10. Fee changes should be auditable.

---

## 8. Fee Types

PayPlus may support the following fee types.

| Fee Type | Description | Notes |
|---|---|---|
| Percentage fee | Fee calculated as a percentage of payment amount | Common for card-funded payments |
| Fixed fee | Flat fee per payment request or transaction | Useful for low-value payments |
| Hybrid fee | Percentage fee plus fixed fee | May better reflect PSP cost structures |
| Category-based fee | Fee varies by bill category | Useful when cost or risk differs by category |
| Method-based fee | Fee varies by funding method | Reflects card, FPS, wallet, or bank cost differences |
| Payee-based fee | Fee varies by payee type or agreement | Useful for institutional arrangements |
| Promotional fee | Reduced, waived, or subsidized fee | Requires campaign rules |
| Minimum fee | Minimum fee charged | Helps protect low-value economics |
| Maximum fee cap | Maximum fee charged | May improve user acceptance |

Exact fee levels are not defined in this document.

Fee levels should be approved separately after cost, risk, and market positioning assumptions are reviewed.

---

## 9. Key Cost Drivers

PayPlus unit economics are affected by the following cost categories.

| Cost Driver | Description |
|---|---|
| Payment processing cost | PSP, acquirer, card scheme, wallet, or bank processing cost |
| Payout cost | Cost of FPS, bank transfer, cheque, or other settlement method |
| Refund cost | Cost incurred when reversing or refunding payments |
| Chargeback and dispute cost | Dispute fees, operational effort, and possible financial loss |
| Promotion cost | Discounts, fee waivers, cashback, rewards, or subsidy gaps |
| Bill verification cost | AI/OCR cost, manual review cost, and exception handling |
| Payee verification cost | Payee onboarding, validation, review, and maintenance |
| Fraud and risk cost | Fraud losses, abuse control, risk tooling, and investigation |
| Customer support cost | User and payee support workload |
| Compliance cost | Legal, compliance, audit, monitoring, and reporting cost |
| Technology cost | Infrastructure, vendor services, monitoring, and development |
| Operations cost | Finance operations, reconciliation, and exception handling |

For unit economics, the priority is to separate variable transaction-level costs from fixed or semi-fixed operating costs.

---

## 10. Unit Economics Framework

Unit economics should be measured at the payment request level and, where needed, at the child transaction level.

### 10.1 Parent Payment Request View

The parent payment request view measures the economics of one full user payment obligation.

Example framework:

```text
Gross Payment Amount
+ User Service Fee
+ Payee Fee
+ Partner Revenue
- Payment Processing Cost
- Payout Cost
- Promotion Cost
- Bill Verification Cost
- Payee Verification Cost
- Refund / Chargeback / Dispute Cost
- Support and Operations Cost
= Contribution Margin
```

### 10.2 Child Transaction View

The child transaction view measures funding method-level economics.

This is important when one parent payment request is funded through multiple child transactions.

Example framework:

```text
Child Transaction Amount
+ Child-Level Fee, if applicable
- Funding Method Processing Cost
- Refund or Failure Cost
- Method-Specific Risk Cost
= Child Transaction Contribution
```

### 10.3 Recommended Core Formula

The recommended high-level formula is:

```text
Contribution Margin =
Total Revenue
- Variable Payment Cost
- Variable Payout Cost
- Variable Verification Cost
- Variable Promotion Cost
- Variable Risk / Dispute Cost
- Variable Support / Operations Cost
```

This formula should be refined when actual processing cost, payout cost, review cost, promotion cost, and risk loss data become available.

---

## 11. Finance and Accounting Dependencies

This document does not define accounting policy.

Finance owners should later confirm how revenue, costs, refunds, chargebacks, subsidies, and advertisement income are treated for accounting and reporting purposes.

Until confirmed, this document should use commercial unit economics assumptions only.

---

## 12. Promotion and Subsidy Economics

Promotions may materially affect contribution margin.

For unit economics, each promotion should identify:

- Funding owner.
- Estimated cost per payment.
- Maximum campaign budget.
- Expected revenue impact.
- Expected margin impact.
- Whether partner reimbursement is guaranteed or conditional.

Detailed promotion eligibility, reservation, consumption, reversal, expiry, and campaign rules belong in `DOC-13`.

Refund and chargeback handling belongs in `DOC-11`.

---

## 13. Partner Advertisement Commercial Model

Partner advertisement may be a revenue stream if approved for MVP or later phases.

Possible commercial models include:

- Fixed placement fee.
- Campaign fee.
- Cost-per-click.
- Cost-per-action.
- Revenue share.
- Bundled partner campaign package.

For unit economics, advertisement revenue should be included only when there is a confirmed or reasonably supportable commercial basis.

This document only covers advertisement revenue treatment at a commercial level.

Content standards, placement rules, approval workflow, user data use, and campaign operations belong in `DOC-07`, `DOC-13`, and `DOC-15`.

---

## 14. Bill Category Economics

Different bill categories may have different economics.

Key factors include:

- Average payment amount.
- Payment frequency.
- User willingness to pay.
- Verification complexity.
- Fraud risk.
- Chargeback risk.
- Payee verification effort.
- Payout method.
- Support workload.
- Partner or biller commercial potential.

MVP bill categories should be reviewed for commercial viability before launch.

The review should consider whether each category can support:

- Processing cost.
- Verification cost.
- Payout cost.
- Risk cost.
- Support cost.
- Promotion cost, if any.
- Target contribution margin.

---

## 15. Payment Method Economics

Funding methods may have different cost and risk profiles.

For unit economics, each method should have assumptions for:

- Processing cost.
- Refund cost.
- Dispute or chargeback exposure.
- Settlement timing impact.
- Expected user adoption.
- Operational complexity.

MVP payment methods currently expected for evaluation are:

- Credit card.
- AlipayHK.
- FPS.

Detailed PSP, regulatory, and integration assessment belongs in `DOC-03` and `DOC-17`.

---

## 16. Payout Method Economics

Payout methods affect cost, timing, and operational workload.

For unit economics, each payout method should have assumptions for:

- Direct payout cost.
- Failure cost.
- Manual handling effort.
- Reconciliation complexity.
- Scalability.

Candidate payout methods include:

- FPS.
- Online banking transfer.
- EPS, where feasible.
- Cheque.

Detailed payout design belongs in `DOC-10`.

---

## 17. Financial Metrics

PayPlus should track financial metrics at product, category, payment method, and campaign levels.

| Metric | Purpose |
|---|---|
| Gross payment volume | Measures total payment obligation volume processed |
| Net revenue | Measures revenue after discounts or fee waivers |
| Transaction count | Measures payment activity |
| Average payment amount | Measures transaction size |
| Average service fee | Measures fee yield |
| Payment processing cost rate | Measures funding cost |
| Payout cost per payment | Measures settlement cost |
| Verification cost per payment | Measures review cost |
| Promotion cost per payment | Measures campaign cost |
| Refund rate | Measures reversal frequency |
| Chargeback rate | Measures dispute exposure |
| Fraud loss rate | Measures risk loss |
| Support cost per payment | Measures operational burden |
| Contribution margin | Measures unit profitability |
| Contribution margin rate | Measures profitability as a percentage of volume or revenue |
| Customer acquisition cost | Measures growth efficiency |
| Payback period | Measures recovery time for acquisition or promotion spend |

Metric definitions should be standardized before automated reporting is implemented.

---

## 18. Pricing Control Principles

Pricing rules should be configurable, auditable, and approved by the responsible business owner.

Fee changes should consider:

- User disclosure.
- Margin impact.
- Category impact.
- Payment method cost impact.
- Promotion impact.
- Existing active payment requests.

Detailed approval workflow and authority matrix should be defined in a governance or operating model document.

---

## 19. Commercial Assumptions

The following assumptions are used for this draft.

| Assumption ID | Assumption |
|---|---|
| `ASM-DOC02-001` | Hong Kong is the MVP launch geography. |
| `ASM-DOC02-002` | MVP payment methods may include credit card, AlipayHK, and FPS. |
| `ASM-DOC02-003` | PayPlus may charge user service fees. |
| `ASM-DOC02-004` | PayPlus may pursue payee, biller, partner, or advertiser commercial arrangements. |
| `ASM-DOC02-005` | Promotions may be funded by PayPlus or external partners. |
| `ASM-DOC02-006` | Actual PSP, acquirer, payout, and banking costs are not yet confirmed. |
| `ASM-DOC02-007` | Exact pricing levels are not yet approved. |
| `ASM-DOC02-008` | Accounting treatment will be confirmed by finance/accounting owners. |

---

## 20. Dependencies

This document depends on or informs the following documents.

| Document | Relationship |
|---|---|
| `DOC-01` | Provides product positioning and MVP scope |
| `DOC-03` | Provides PSP, acquirer, payment method, and regulatory assessment |
| `DOC-05` | Defines product requirements affected by fees and commercial rules |
| `DOC-09` | Defines payment request and funding logic |
| `DOC-10` | Defines payout and reconciliation rules |
| `DOC-11` | Defines refund, cancellation, and chargeback handling |
| `DOC-13` | Defines detailed promotion and campaign rules |
| `DOC-14` | Defines fraud, abuse, and risk controls |
| `DOC-15` | Defines data usage and privacy controls |
| `DOC-18` | Defines reporting, ledger, and data model requirements |

---

## 21. Key Risks

| Risk ID | Risk | Mitigation Direction |
|---|---|---|
| `RISK-DOC02-001` | Payment processing cost may exceed user fee revenue | Validate payment cost assumptions before pricing approval |
| `RISK-DOC02-002` | Promotions may create negative unit economics | Require funding owner, budget, and margin review |
| `RISK-DOC02-003` | High manual review cost may reduce profitability | Use risk-based review and automation where appropriate |
| `RISK-DOC02-004` | Chargebacks or fraud losses may exceed assumptions | Coordinate with risk controls in `DOC-14` |
| `RISK-DOC02-005` | Certain bill categories may be commercially unattractive | Review category-level economics before launch |
| `RISK-DOC02-006` | Payout methods may create high cost or operational load | Validate payout assumptions in `DOC-10` |
| `RISK-DOC02-007` | Partner advertisement may affect user trust | Apply content, disclosure, and compliance controls in related docs |
| `RISK-DOC02-008` | Fee model may appear similar to cashout or quasi-cash service | Preserve bill-backed payment positioning and risk controls |

---

## 22. Acceptance Criteria

This document is acceptable when:

- Business model options are clearly described.
- Revenue streams are identified.
- Fee model principles are defined.
- Key fee types are listed.
- Major cost drivers are documented.
- Unit economics formulas are defined.
- Promotion and subsidy economics are addressed at a commercial level.
- Partner advertisement revenue is addressed at a commercial level.
- Financial metrics are defined.
- Commercial assumptions and risks are captured.
- Content belonging to other documents is excluded or referenced only at a high level.
- Open commercial questions are clearly listed.

---

## 23. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC02-001` | What MVP user fee structure should PayPlus adopt: percentage fee, fixed fee, hybrid fee, category-based fee, or method-based fee? | Business Owner | High | Open |
| `OQ-DOC02-002` | Will PayPlus include payee-paid or biller-paid fees in the MVP revenue model, or defer them to a later phase? | Business Owner | Medium | Open |
| `OQ-DOC02-003` | Which MVP bill categories meet the minimum contribution margin threshold under expected cost and pricing assumptions? | Business / Finance | High | Open |
| `OQ-DOC02-004` | What minimum contribution margin or contribution margin rate should each MVP category target? | Business / Finance | High | Open |
| `OQ-DOC02-005` | What confirmed payment processing cost assumptions should be used in the DOC-02 unit economics model? | Business / Finance / Partnership | High | Open |
| `OQ-DOC02-006` | What confirmed payout cost assumptions should be used in the DOC-02 unit economics model? | Finance / Operations | High | Open |
| `OQ-DOC02-007` | What promotion cost assumptions and funding sources should be included in the MVP unit economics model? | Growth / Business / Finance | Medium | Open |
| `OQ-DOC02-008` | Will partner advertisement be included as an MVP revenue stream or treated as a post-MVP opportunity? | Business / Growth | Low | Open |

---

## 24. Document Changelog

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Product Documentation Team | Initial draft of business model and unit economics framework |
