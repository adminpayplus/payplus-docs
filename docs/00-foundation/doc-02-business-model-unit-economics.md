---
document_id: DOC-02
title: Business Model & Unit Economics
version: 0.11.0
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
last_updated: 2026-08-12
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
---

# DOC-02 - Business Model & Unit Economics

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-02` |
| **Title** | Business Model & Unit Economics |
| **Version** | `0.11.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Commercial / Finance Owner |
| **Reviewers** | Product Lead<br>Finance Lead<br>Commercial Lead<br>Payments Lead<br>Compliance Lead<br>Risk Lead |
| **Approvers** | Project Owner<br>Finance Lead<br>Commercial Lead |
| **Last Updated** | `2026-08-12` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification |

---


## 1. Purpose

This document defines the commercial framework and unit-economics model for PayPlus.

It explains how PayPlus may generate revenue, incur costs, evaluate profitability, govern pricing, manage promotions and assess whether a controlled Bill Category, Rent journey, economic-Payee type, Institutional Payee Programme, payment method, partner model or campaign is commercially viable.

DOC-02 consumes the product meanings owned by DOC-01 and DOC-05. It does not define product eligibility, Directory truth, final pricing, accounting policy, tax treatment, legal conclusions, partner terms, payment or payout rules, promotion logic, or Institutional Programme commercial approval.

---

## 2. Commercial Objective

PayPlus aims to create a sustainable Evidence-Backed Bill/Rent payment business in which approved revenue exceeds the full variable and allocated cost of processing, paying, verifying, supporting and governing each transaction and applicable programme activity.

Profitability should be evaluated by:

- transaction and Payer;
- economic-Payee class and, where appropriate, institution;
- supported controlled Bill Category or Rent;
- institutional programme, Category association and publication activity;
- campaign and partner;
- payment and payout method;
- geography and product line.

Retained Directory-selected or Self-provided provenance is available only for audit and troubleshooting under DOC-05. It must not become a pricing, promotion, profitability, margin-allocation, eligibility or general commercial-reporting dimension. Finance may model aggregate operating costs for the two product processes without using retained transaction provenance.

### 2.1 Current Commercial Baseline

The product baseline is Payer-only. Active Payee-created Request, Request delivery, acceptance/conversion funnel, Payee-user portal and Request/Linking economics are retired from current MVP treatment.

Commercial assessment must include:

- PSP/acquirer pricing and acceptance;
- payout cost, settlement timing, reserves and liquidity;
- transaction Evidence, Payee, destination, risk, support and reconciliation cost;
- institutional enrolment/KYB, Category association and Directory publication cost where applicable;
- aggregate verification and review cost for controlled Directory and Self-provided operating processes;
- scoped type-label review and permitted individual-notification cost where applicable;
- category-level contribution margin and approved fee recovery.

The current candidate fee baseline remains an online-payment service fee calculated as a percentage of transaction amount. Exact rates, allocation, subsidies, promotions, refunds and reversals remain unresolved.

DOC-22 may execute approved pricing configuration. Admin configurability does not make or replace a pricing, contract, legal, tax or commercial-approval decision.

---

## 3. Business Model Summary

| Model component | Candidate use |
|---|---|
| Payer-paid service fee | Core candidate transaction model; requires pre-authorization disclosure. |
| Percentage, fixed or minimum transaction fee | Candidate structures subject to approval. |
| Contracted institutional/biller fee | Possible onboarding, programme, platform, payout or transaction fee only where separately approved and contracted. |
| Split-fee or institutional subsidy | Possible with clear disclosure and approved accounting. |
| Partner-funded subsidy or campaign | Possible where funding, limits and reporting are controlled. |
| Promotion-funded model | Growth mechanism with approved budget and margin guardrails. |
| Revenue share | Possible where contractually permitted and included in margin. |
| Subscription or membership | Future candidate; no Payee-user portal or Request capability is implied. |
| API/platform fee | Future partner or institutional candidate; no runtime feature is authorized here. |
| Sponsored placement | Future gated candidate requiring product, legal and disclosure approval. |

No component launches without commercial, compliance, legal, accounting, tax, product, operational and partner review.

---

## 4. Revenue Streams

Candidate revenue may include Payer service fees, contracted institutional/biller/programme fees, payout or special-handling fees, partner subsidy, campaign funding, approved revenue share, and future separately approved platform or subscription revenue.

There is no active Request fee, Request-creation fee, Request-delivery fee or Payee-user portal revenue model.

All institutional or Payee-side revenue remains a candidate only. It requires agreement, disclosure, ledger support, legal/tax/accounting review and commercial approval. This Draft does not establish programme pricing, fee amount, structure, payer/payee allocation, margin or contract.

---

## 5. Fee Principles

| Principle | Requirement |
|---|---|
| Transparent | Payer-facing fees appear before payment authorization. |
| Accurate | Quote, receipt, ledger and report values reconcile. |
| Authorized | No Payer charge before explicit payment authorization. |
| Contracted | Institutional or other non-Payer fees require an approved agreement. |
| Compliant | Applicable legal, network, partner, tax and consumer requirements apply. |
| Economically justified | Fees consider processing, payout, risk, review, support and margin. |
| Non-misleading | Subsidies do not obscure total cost or PayPlus role. |
| Reversible where required | Refund, cancellation, dispute and chargeback treatment is defined. |
| Reportable | Fees are attributable by transaction, Payer, Payee class, Category, programme, campaign and partner where applicable. |

Directory acquisition provenance must not determine pricing, promotion eligibility, profitability, margin allocation or future transaction eligibility.

---

## 6. Cost Drivers

| Cost driver | Description |
|---|---|
| Card processing | PSP, acquirer, interchange, scheme, gateway, authorization, capture and refund. |
| Payout | Transfer, provider, retry and exception cost. |
| Refund/reversal/chargeback | Processing, lost principal, representment and operations. |
| Fraud and risk loss | Unauthorized, fake, inflated, collusive, cashout or other abuse. |
| Promotion | Discounts, rewards, subsidies, referral and fulfilment. |
| Evidence/OCR | Extraction, validation and document review. |
| Manual review | Evidence, type, Payee, destination, risk, payout, disputes and exceptions. |
| Support | Payer, economic-Payee, institution and partner support. |
| Institutional programme | Enrolment, KYB, contracting, Category association, publication maintenance and offboarding operations where applicable. |
| Payee/destination verification | Individual, institution, beneficiary/agent and payout-account checks. |
| Controlled Bill-acquisition operations | Aggregate Directory and Self-provided process cost, measured without repurposing transaction provenance beyond audit/troubleshooting. |
| Notification | Payer service communication and separately permitted individual-Payee notification. |
| Infrastructure and retention | Cloud, storage, logging, monitoring and records. |
| Reconciliation/compliance/audit | Finance, control, reporting and evidence retention. |
| Reserve/holdback/liquidity | Cost of funds, collateral, prefunding or reduced liquidity. |
| Tax | Applicable transaction or service tax cost. |

Model costs conservatively until partner pricing and measured operational data exist.

---

## 7. Unit Economics

### 7.1 Base Transaction Formula

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
- Evidence / OCR Cost Allocation
- Risk Tooling Cost Allocation
- Notification Cost Allocation
- Variable Infrastructure Cost Allocation
- Tax Cost Allocation
= Transaction Contribution Margin
```

### 7.2 Institutional Programme Cost Considerations

The ordinary cost model should include institutional enrolment/KYB, Category-association, publication-maintenance, contract, support and offboarding costs where applicable. Any institutional or partner revenue remains separately approved and belongs in the base transaction or approved programme reporting model determined by Finance.

No new programme contribution formula is accepted by this Draft. Aggregate operating-cost comparison between Directory and Self-provided processes may support capacity planning, but retained acquisition provenance remains audit/troubleshooting-only and cannot drive pricing, profitability attribution or transaction eligibility.

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

Final allocation and reporting definitions belong to DOC-18 and Finance approval.

---

## 8. Key Economic Definitions

| Term | Definition |
|---|---|
| GTV | Total submitted or processed Bill/Rent payment value under an approved definition. |
| Funded Amount | Value charged to Payer funding sources. |
| Bill/Rent Amount | Amount supported by the applicable source and obligation context. |
| Payout Amount | Value sent to the intended economic Payee or approved payout destination. |
| Gross Revenue | Approved Payer, institutional, partner or campaign revenue. |
| Net Revenue | Gross revenue after approved reversals, discounts and revenue share. |
| Direct / Allocated Cost | Cost attributed directly or through an approved allocation method. |
| Contribution Margin | Revenue less direct and allocated variable costs. |
| Take Rate | Approved revenue measure divided by GTV. |
| Promotion Burn | Approved discount, reward, subsidy or fulfilment cost. |
| Manual Review Cost | Attributable Evidence, type, Payee, destination, risk, payout or support review labor. |
| Institutional Enrolment Cost | Cost of a real enrolment process; separate from transaction Payee/destination verification. |
| Directory Maintenance Cost | Cost of Category association and publication operations; not a transaction-eligibility cost. |
| Acquisition provenance | Directory-selected or Self-provided lineage retained only for audit and troubleshooting under DOC-05; not a commercial segmentation or pricing field. |
| Payee Type | Individual or institution/company for product-policy purposes; detailed commercial segmentation remains owner-controlled. |
| Payee Profitability | Approved contribution view for an economic Payee or institution after attributable revenue and costs. |

No composite `Approved Payee` economic state may collapse enrolment, publication or transaction readiness.

---

## 9. Category and Payee-Type Economics

Assessment may vary by average value, processing/payout cost, Evidence quality, individual/institutional type, programme enrolment cost, Category association, verification and review effort, fraud/chargeback risk, refund rate, willingness to pay, partner subsidy, operational complexity, regulation, support and margin.

| Assessment | Question |
|---|---|
| Demand | Is there meaningful Payer demand? |
| Willingness to pay | Will the approved cost bearer accept the proposed fee? |
| Cost | Are full transaction and programme costs understood? |
| Risk | Are fraud, collusion, fake Evidence and cashout risks manageable? |
| Review | Can owner-controlled checks operate efficiently? |
| Programme | Are institutional enrolment and publication costs justified where applicable? |
| Operating process | Are aggregate Directory and Self-provided operating costs understood without converting retained transaction provenance into a commercial dimension? |
| Partner/compliance | Do partners and owners support the Category and model? |
| Margin | Does the Category meet an approved threshold? |
| Scalability | Can volume grow without excessive review, support or reconciliation burden? |

The twelve-category launch inventory is fixed by DOC-05 Section 3.1.1. This commercial framework does not make any Category commercially ready or approve Category-specific pricing, fees, partner terms, programme economics or viability; those assessments remain open under DOC-02 and the applicable owners. Rent is assessed as a separate journey and economic line, not as a Bill Category.

---

## 10. Multi-Card or Multi-Source Payment Economics

Multi-card may increase value and cost through multiple authorizations, higher decline/partial-failure risk, refund allocation, chargeback handling, reconciliation, support, fraud, disclosure and partner restrictions.

The Payer authorizes the applicable Provider Submissions under DOC-09. Any fee or cost allocation by funding source remains open. Multi-card must not launch without commercial and operational understanding within the confirmed six-card cap.

---

## 11. Promotion and Subsidy Economics

Each promotion requires an approved funding source, budget, eligibility, qualification, limits, benefit, quote effect, expiry, reversal, refund, chargeback, tax/accounting, reporting and owner.

Directory provenance must not by itself determine promotion eligibility. Institutional subsidy is possible only if separately approved and must not convert publication into transaction eligibility.

Detailed promotion logic belongs to DOC-13.

---

## 12. Refund, Cancellation, Dispute and Chargeback Economics

Commercial treatment must address service-fee refund, institutional fee treatment where contracted, retained partner costs, Payout state, reversibility, loss bearer, recovery rights, promotion reversal, chargeback fees, investigation cost, representment Evidence, restrictions and revenue reversal.

Request rejection, expiry and withdrawal are not current-product economic states. Because no production Request/Payee-role runtime existed, this model defines no legacy Request reporting, funnel or transaction dataset.

Detailed rules belong to DOC-10, DOC-11 and DOC-18.

---

## 13. Working Capital, Settlement and Reserves

Assess timing between Checkout/Provider Submission, card authorization/capture, upstream settlement, reserves/holdbacks, Payout initiation/completion, any contracted institutional billing, refunds, chargebacks and revenue recognition.

Assessment includes settlement delay, funding gap, reserve, prefunding, collateral, exposure periods, liquidity buffer, cutoff/weekend effects and Payout expectations.

No Payout timing promise is created here.

---

## 14. Partner Economics

Assess setup and minimum fees; transaction, authorization, refund, chargeback and Payout fees; KYC/KYB, institutional enrolment, Category association/publication maintenance, Payee/destination verification, Evidence/OCR, notification, risk, support, reserve, revenue-share, contract, SLA, export and migration costs.

Partner assessment may vary by Category, economic-Payee type, programme enrolment, payout timing, risk and partner classification. It must not assume a marketplace, Request creator, Payee-user portal or Request-delivery product.

Detailed assessment belongs to DOC-03.

---

## 15. Pricing Governance

Material pricing changes require rationale, affected Categories and cost bearers, geography, effective date, expected margin and adoption impact, applicable legal/compliance/tax/accounting review, communication, systems/QA impact and approval record.

Changes must align quote logic, disclosures, receipts, contracted institutional statements if applicable, ledger, reports, support and terms.

DOC-22 implements only approved configuration. It does not decide pricing or commercial policy.

---

## 16. Commercial Viability Gates

| Gate ID | Gate | Acceptance condition |
|---|---|---|
| `GATE-DOC02-001` | Revenue model | Approved candidate revenue and fee structure documented. |
| `GATE-DOC02-002` | Cost model | Direct and material allocated costs documented. |
| `GATE-DOC02-003` | Contribution margin | Expected margin modeled under approved assumptions. |
| `GATE-DOC02-004` | Risk losses | Fraud, chargeback, refund, collusion and operational loss included. |
| `GATE-DOC02-005` | Partner pricing | PSP, acquirer, payout, verification and other pricing confirmed or conservatively estimated. |
| `GATE-DOC02-006` | Promotion | Budget, funding and margin impact approved. |
| `GATE-DOC02-007` | Settlement | Working capital, reserve, holdback and Payout timing assessed. |
| `GATE-DOC02-008` | Legal/tax/accounting | Applicable treatment reviewed. |
| `GATE-DOC02-009` | Reporting | Required metrics and lineage defined. |
| `GATE-DOC02-010` | Launch approval | Commercial approver signs off. |
| `GATE-DOC02-011` | Original Payee-created Request economics gate | Retired under the Payer-only target; ordinary cost and partner-pricing gates still apply to programme operations. |
| `GATE-DOC02-012` | Original Payee-side pricing gate | Retired with the active Request/Payee-user model; any future institutional terms require separately accepted commercial scope and the ordinary approval gates. |
| `GATE-DOC02-013` | Rent or controlled Bill economics | Applicable Evidence, verification, risk, support, dispute and chargeback costs are included. |

These gates do not make Directory state a transaction-time commercial eligibility truth.

---

## 17. Reporting and Metrics

Report commercial performance at transaction, Category, Payer, economic-Payee class, institution where justified, programme, partner, payment/Payout method and campaign level.

Candidate metrics include GTV, funded and paid-out volume, gross/net revenue, approved institutional revenue, processing and Payout cost, enrolment/KYB cost, Category-association/publication cost, aggregate controlled-acquisition operating cost, Evidence review, Payee/destination verification, optional-notification cost, promotion burn, fraud/chargeback loss, manual review, support, contribution margin/rate, take rate, average value, authorization/decline/Payout-failure rate, Category/institution/partner/campaign profitability and programme operating cost.

Request volume, acceptance, rejection, expiry, completion, Request-origin profitability and Payee Request activation/retention are retired MVP metrics. No historical Request measure or production reporting obligation exists.

Final definitions belong to DOC-18.

---

## 18. Data and Ledger Expectations

Commercial reporting requires, where applicable:

- Bill/Rent amount, funded amount and Payout amount;
- service fee and approved Payer/institutional/partner fee components;
- discounts, promotion funding, tax, processing and Payout cost;
- enrolment/KYB, Category association, publication and Directory maintenance cost;
- Evidence, Payee/destination, type-label and risk review cost;
- permitted individual-notification cost;
- refunds, chargebacks, fraud loss, revenue share, net revenue and margin;
- funding, payment and Payout route;
- Payer, economic-Payee class, institution and partner attribution where lawful and approved;
- transaction, Payout and reconciliation status under their owners.

Exact fields, IDs, schemas and ledger design belong to DOC-18. Institutional enrolment, Category association and Directory publication must remain separate. Acquisition provenance remains outside commercial ledger/reporting use except controlled audit/troubleshooting access. Retired Request stable IDs and append-only documentation history do not create commercial fields, records or reporting requirements.

---

## 19. Accounting, Tax and Revenue Recognition Considerations

Finance and Legal/Tax must determine principal/agent treatment; economic-Payee and institution classification; gross/net recognition; timing of Payer, institutional and partner revenue; refund/chargeback treatment; promotion classification; taxes on each approved fee; withholding or transaction taxes; pass-through treatment; and reserves, holdbacks, pending items, failures and reversals.

Request/Linking lifecycle is not an accounting dimension for the target MVP. No production Request/Payee-role transactions existed, so retired IDs and append-only documentation history create no accounting or historical-reporting treatment.

This document establishes no accounting or tax policy.

---

## 20. Key Assumptions

| Assumption ID | Assumption | Owner | Status |
|---|---|---|---|
| `ASM-DOC02-001` | Payers accept an approved fee sufficient for at least one Category. | Commercial / Product | Open |
| `ASM-DOC02-002` | PSP/acquirer pricing permits positive margin. | Commercial / Payments | Open |
| `ASM-DOC02-003` | Payout cost is viable for target values. | Finance / Payments | Open |
| `ASM-DOC02-004` | Fraud and chargeback losses remain controllable. | Risk / Finance | Open |
| `ASM-DOC02-005` | Manual review is affordable at MVP volume. | Operations / Finance | Open |
| `ASM-DOC02-006` | Promotions can be capped and tracked. | Growth / Finance | Open |
| `ASM-DOC02-007` | Data supports Category, partner, programme and margin reporting while acquisition provenance remains audit/troubleshooting-only. | Finance / Engineering | Open |
| `ASM-DOC02-008` | Settlement and reserves do not create unacceptable liquidity needs. | Finance / Payments | Open |
| `ASM-DOC02-009` | Tax/accounting treatment does not undermine the selected model. | Finance / Legal / Tax | Open |
| `ASM-DOC02-010` | Original Payee-created Request incremental-volume assumption. | Commercial / Product / Finance | Retired under Payer-only target |
| `ASM-DOC02-011` | Institutions may accept separately approved commercial terms if selected. | Commercial / Product | Open; no term approved |
| `ASM-DOC02-012` | Original Payee Request acceptance-rate assumption. | Product / Commercial | Retired |
| `ASM-DOC02-013` | Institutional enrolment/verification cost may be recoverable through approved transaction margin, institutional revenue, partner funding or strategic value. | Commercial / Finance / Risk | Open |
| `ASM-DOC02-014` | Original Payee-created Rent/invoice Request assumption. | Risk / Finance / Operations | Retired |
| `ASM-DOC02-015` | Original Request-creator and funnel-reporting assumption. | Finance / Engineering | Retired |

---

## 21. Key Constraints

| Constraint ID | Constraint | Impact | Owner |
|---|---|---|---|
| `CON-DOC02-001` | Fees disclosed before Payer authorization. | Requires transparent quote. | Product / Legal |
| `CON-DOC02-002` | Pricing complies with law, network and partner rules. | May limit structures. | Legal / Compliance / Payments |
| `CON-DOC02-003` | Promotions require approved budgets. | Prevents uncontrolled loss. | Growth / Finance |
| `CON-DOC02-004` | Settlement may constrain Payout speed. | May require buffer/delay. | Finance / Payments |
| `CON-DOC02-005` | Reserves/holdbacks may constrain growth. | Affects capital. | Finance / Commercial |
| `CON-DOC02-006` | Accounting/tax treatment precedes launch. | May affect pricing and contracts. | Finance / Legal / Tax |
| `CON-DOC02-007` | Negative-margin transactions require approval or blocking. | Requires monitoring. | Finance / Commercial |
| `CON-DOC02-008` | Reporting depends on reliable ledger/reconciliation. | Requires alignment. | Finance / Engineering |
| `CON-DOC02-009` | Multi-card may increase cost. | Requires owner treatment. | Product / Payments |
| `CON-DOC02-010` | Category expansion passes viability gates. | Controls rollout. | Product / Commercial |
| `CON-DOC02-011` | Original Payee-created Request commercial-gate constraint. | Superseded by formal active-Request retirement. | Commercial / Product / Finance |
| `CON-DOC02-012` | Institutional fees require agreement, disclosure, approval and reporting. | No fee inferred. | Commercial / Legal / Finance |
| `CON-DOC02-013` | Original Payee-created Request charging constraint. | Superseded; Payer authorization remains under DOC-09. | Product / Payments / Legal |
| `CON-DOC02-014` | Original Payee-created Rent/invoice pricing constraint. | Retired; Category economics remain gated. | Commercial / Risk / Product |
| `CON-DOC02-015` | Payment Instructions may change timing, quote, support and Payout cost. | Requires downstream reporting. | Commercial / Product / Finance |

---

## 22. Key Dependencies

| Dependency ID | Dependency | Required for | Owner | Status |
|---|---|---|---|---|
| `DEP-DOC02-001` | PSP/acquirer pricing. | Processing cost. | Commercial / Payments | Open |
| `DEP-DOC02-002` | Payout provider pricing. | Payout cost. | Commercial / Payments | Open |
| `DEP-DOC02-003` | Original launch Category inventory decision. | The twelve-category inventory is fixed in DOC-05; Category-specific commercial readiness remains governed elsewhere in this document. | Product / Compliance | Resolved; retained for lineage |
| `DEP-DOC02-004` | Limits and risk rules. | Loss assumptions. | Risk / Compliance | Open |
| `DEP-DOC02-005` | Refund/chargeback rules. | Reversal model. | Payments / Risk / Finance | Open |
| `DEP-DOC02-006` | Promotion design. | Campaign economics. | Growth / Product | Open |
| `DEP-DOC02-007` | Ledger/reporting model. | Margin reporting. | Finance / Engineering | Open |
| `DEP-DOC02-008` | Accounting policy. | Recognition/reporting. | Finance | Open |
| `DEP-DOC02-009` | Tax review. | Fee/tax disclosure. | Legal / Tax / Finance | Open |
| `DEP-DOC02-010` | Partner contracts. | Revenue share, reserves and settlement. | Commercial / Legal | Open |
| `DEP-DOC02-011` | Institutional enrolment/KYB cost model. | Programme economics. | Commercial / Risk / Operations | Open |
| `DEP-DOC02-012` | Economic-Payee and institution classification. | Cost allocation and profitability. | Product / Commercial / Risk | Open |
| `DEP-DOC02-013` | Institutional commercial policy. | Any onboarding, programme, Payout or platform fee. | Commercial / Finance / Legal | Open |
| `DEP-DOC02-014` | Original Payer invitation mechanism. | Retired Request economics. | Product / Engineering / Commercial | Retired |
| `DEP-DOC02-015` | Original Payer Request response process. | Retired Request economics. | Product / Operations / Legal | Retired |
| `DEP-DOC02-016` | Rent verification standard. | Rent economics. | Product / Risk / Operations | Open |
| `DEP-DOC02-017` | Controlled Bill verification standard. | Category economics. | Product / Risk / Operations | Open |
| `DEP-DOC02-018` | Institutional and economic-Payee support model. | Support allocation. | Operations / Commercial | Open |
| `DEP-DOC02-019` | Payment Instruction reporting. | Deferred funding economics. | Finance / Product / Engineering | Open |

---

## 23. Key Risks

| Risk ID | Risk | Impact | Mitigation | Owner | Status |
|---|---|---|---|---|---|
| `RISK-DOC02-001` | Processing cost exceeds willingness to pay. | Negative margin. | Model/test approved pricing. | Commercial / Product | Open |
| `RISK-DOC02-002` | Partner pricing/reserves are uneconomic. | Delay or failure. | Compare providers. | Commercial / Payments | Open |
| `RISK-DOC02-003` | Promotions create uncontrolled loss. | Cash burn. | Budgets and caps. | Growth / Finance | Open |
| `RISK-DOC02-004` | Chargeback/fraud exceeds assumptions. | Margin/partner harm. | Risk controls and Evidence. | Risk / Finance | Open |
| `RISK-DOC02-005` | Review cost underestimated. | Lower margin/backlog. | Measure and automate. | Operations / Finance | Open |
| `RISK-DOC02-006` | Fee disclosure unclear. | Complaints/regulatory harm. | Legal/compliance review. | Product / Legal | Open |
| `RISK-DOC02-007` | Settlement creates liquidity pressure. | Delayed Payout. | Model reserves/buffers. | Finance / Payments | Open |
| `RISK-DOC02-008` | Data cannot support margin. | Poor decisions/audit gap. | DOC-18 definition. | Finance / Engineering | Open |
| `RISK-DOC02-009` | Accounting/tax changes economics. | Redesign. | Pre-approval review. | Finance / Legal / Tax | Open |
| `RISK-DOC02-010` | Category expands without review. | Negative-margin scale. | Enforce gates. | Product / Commercial | Open |
| `RISK-DOC02-011` | Original low Request acceptance/completion risk. | Superseded active product risk. | Active Requests retired. | Commercial / Product | Retired |
| `RISK-DOC02-012` | Institutional enrolment/verification cost underestimated. | Programme may be uneconomic. | Cost attribution by institution/type. | Commercial / Operations | Open |
| `RISK-DOC02-013` | Institutional fees reduce participation. | Lower programme value. | Separate pricing approval and testing. | Commercial / Product | Open |
| `RISK-DOC02-014` | Original Request support/dispute cost risk. | Superseded active product risk. | Active Requests retired. | Operations / Finance | Retired |
| `RISK-DOC02-015` | Fake Evidence or collusion loss exceeds assumptions. | Fraud/chargeback loss. | Owner controls and conservative loss model. | Risk / Finance | Open |
| `RISK-DOC02-016` | Rent Evidence/verification cost is high. | The separate Rent journey and economic line may be commercially unattractive. | Model Rent separately from controlled Bill Categories. | Commercial / Risk | Open |
| `RISK-DOC02-017` | Institutional billing/reversals are ledgered incorrectly. | Revenue/audit error. | DOC-18/Finance design. | Finance / Engineering | Open |
| `RISK-DOC02-018` | Fee allocation confuses Payers or institutions. | Complaints/disputes. | Clear approved disclosure. | Product / Legal | Open |
| `RISK-DOC02-019` | Payout timing expectations create pressure. | Support or unsafe early Payout. | Align communication to model. | Finance / Operations | Open |
| `RISK-DOC02-020` | Original Request spam cost risk. | Superseded active product risk. | Active Requests retired; individual notification abuse remains specialist-owned. | Commercial / Risk | Retired |
| `RISK-DOC02-021` | Deferred Instructions or partial funding create cost complexity. | Revenue/reconciliation harm. | Revalidate and report under owners. | Finance / Product / Operations | Open |
| `RISK-DOC02-022` | Directory operations are assumed to remove independently required transaction checks. | Underestimated operating cost and control failure. | Include owner-required transaction controls in aggregate costs. | Commercial / Risk | Open |
| `RISK-DOC02-023` | Self-provided-process verification burden is underestimated. | Negative Category margin. | Measure aggregate process and review cost without repurposing transaction provenance. | Commercial / Operations | Open |
| `RISK-DOC02-024` | Unpublication is confused with commercial offboarding or suspension. | Incorrect records or bypass. | Model each action separately under its owner. | Commercial / Product | Open |

---

## 24. Downstream Document Impact

| Document | Impact |
|---|---|
| `DOC-03` / `DOC-04` | Assess partner pricing, reserves, programme/commercial controls and launch gates. |
| `DOC-05` | Retains product-policy authority; commercial modeling cannot redefine Directory, acquisition, Save or retirement meanings. |
| `DOC-06` family | Later Payer-only journeys and presentation must disclose approved fees without inheriting Request economics. |
| `DOC-07` / `DOC-08` | Approved fee language and permitted notification cost/delivery. |
| `DOC-09` / `DOC-10` / `DOC-11` | Funding, authorization, payout, reconciliation, refund and chargeback economics. |
| `DOC-12` | Evidence, Category and Payee-verification cost inputs. |
| `DOC-13` | Promotion budgets, funding, reversals and reporting. |
| `DOC-14` / `DOC-15` | Risk-loss, privacy and wrong-recipient cost inputs. |
| `DOC-18` | Represent approved ledger, programme dimensions, costs, margin and reporting requirements; acquisition provenance remains audit/troubleshooting-only, and no Request-runtime reporting is created. |
| `DOC-20` / `DOC-21` | Commercial readiness, monitoring, support and incident evidence. |
| `DOC-22` | Audited execution of approved pricing/configuration only; no commercial-policy authority. |

---

## 25. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC02-001` | What pricing, fee allocation, subsidy, promotion, refund and reversal treatment applies? | Commercial / Product | Critical | Open |
| `OQ-DOC02-002` | What minimum contribution margin applies by transaction/Category? | Finance / Commercial | Critical | Open |
| `OQ-DOC02-003` | What PSP/acquirer assumptions apply before contracts? | Payments / Commercial | Critical | Open |
| `OQ-DOC02-004` | What payout pricing assumptions apply? | Payments / Commercial | High | Open |
| `OQ-DOC02-005` | May approved fees differ by Category, amount, funding source or Payee class, and on what independently approved basis? | Commercial / Legal / Product | High | Open |
| `OQ-DOC02-006` | Are payment-method-based fees permitted? | Legal / Compliance / Payments | Critical | Open |
| `OQ-DOC02-007` | What refund and reversal rules apply? | Finance / Payments / Product | High | Open |
| `OQ-DOC02-008` | How is chargeback liability allocated? | Legal / Finance / Risk | High | Open |
| `OQ-DOC02-009` | What promotion budget and controls apply? | Growth / Finance | Medium | Open |
| `OQ-DOC02-010` | What reserves/holdbacks/prefunding apply? | Commercial / Payments | High | Open |
| `OQ-DOC02-011` | What accounting treatment applies? | Finance | Critical | Open |
| `OQ-DOC02-012` | What tax treatment applies to each approved fee? | Legal / Tax / Finance | Critical | Open |
| `OQ-DOC02-013` | Original transaction, Request, Payee and Request-origin margin-data question. | Finance / Engineering | High | Retired; replacement programme-data question uses a new ID |
| `OQ-DOC02-014` | What commercial approval process applies to Category, institutional programme or pricing changes? | Project Owner / Finance | Medium | Open |
| `OQ-DOC02-015` | Original active Payee-created Request commercial-gate question. | Project Owner / Commercial / Product | Critical | Retired |
| `OQ-DOC02-016` | Original Request-creator Payee-type question. | Commercial / Product / Risk | Critical | Retired |
| `OQ-DOC02-017` | Original Payee onboarding, subscription, invoice, Request, Payout, platform or transaction-fee question. | Commercial / Finance / Product | Critical | Retired with active Request/Payee-user economics |
| `OQ-DOC02-018` | Original Payee-side fee-trigger question. | Commercial / Finance / Product | High | Retired with active Request/Payee-user economics |
| `OQ-DOC02-019` | Original Request-state treatment for Payee-side fees. | Finance / Legal / Product | High | Retired with active Request economics |
| `OQ-DOC02-020` | Original Request acceptance-rate question. | Commercial / Product | High | Retired |
| `OQ-DOC02-021` | What institutional enrolment and sales-acquisition cost is acceptable by institutional class and Category? | Commercial / Finance | High | Open |
| `OQ-DOC02-022` | Original landlord-created Rent Request model question. | Commercial / Legal / Risk | Critical | Retired; Rent economics remain separately open |
| `OQ-DOC02-023` | Original invoice Request model question. | Commercial / Legal / Risk | High | Retired; controlled Bill economics remain separately open |
| `OQ-DOC02-024` | May an institution subsidize Payer fees, and under what approved treatment? | Commercial / Finance / Legal | High | Open |
| `OQ-DOC02-025` | Original Request spam-limit question. | Commercial / Risk / Operations | High | Retired |
| `OQ-DOC02-026` | Original Request-flow margin-threshold question. | Finance / Commercial | High | Retired |
| `OQ-DOC02-027` | What institution/economic-Payee reporting is required for Payout, fees, disputes, refunds and tax/accounting? | Finance / Product / Engineering | Medium | Open |
| `OQ-DOC02-028` | What margin treatment applies to Payment Instructions and partial funding/Payout? | Finance / Product / Engineering | Medium | Open |
| `OQ-DOC02-029` | What programme data is required to report institutional enrolment, Category-association, publication, operating cost and approved revenue without using Bill-acquisition provenance? | Finance / Engineering | High | Open |
| `OQ-DOC02-030` | What, if any, separately approved institutional enrolment, programme, platform, Payout, subsidy or transaction terms should apply? | Commercial / Finance / Legal | Critical | Open; no term approved |

---

## 26. Acceptance Criteria

DOC-02 is acceptable when it:

1. retains the transaction-level revenue, cost, margin, promotion, settlement, partner and accounting framework;
2. contains no active Payee-created Request, Request-fee, Payee-user portal or Request-funnel commercial model;
3. treats Consumer product demand and payment economics as Payer-led;
4. includes institutional enrolment, Category association, publication and aggregate controlled-acquisition operating costs where applicable without creating a new contribution formula or commercial gate;
5. keeps acquisition provenance limited to audit/troubleshooting and out of pricing, promotion, profitability, margin allocation and general commercial reporting;
6. preserves relevant Evidence, Payee/destination, risk, Payout, support and reconciliation costs;
7. keeps unpublication separate from commercial offboarding and substantive suspension;
8. preserves only append-only documentation history and retired Request stable IDs as non-active evidence, without creating runtime records, measures, fields, transactions or reporting obligations;
9. recognises the Founder-confirmed twelve-category launch inventory and separate Rent economic line while leaving Category-specific pricing, fee structures, viability, margins, contracts, institutional programme terms, accounting, tax and partner conclusions unresolved;
10. keeps DOC-05 product-policy authority and DOC-22 execution-only boundaries explicit.

This document remains a commercial framework, not a pricing sheet, accounting policy, tax memo, partner contract, product PRD or payment specification.

---

## 27. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.11.0` | 2026-08-12 | Product Documentation Team | Aligned the commercial framework to the Founder-confirmed twelve-category inventory and separate Rent economic line, and removed nonexistent production Request records, measures, fields, transactions and historical-reporting obligations while preserving retired IDs and append-only documentation history. |
| `0.10.0` | 2026-08-10 | Product Documentation Team | Drafted the narrow Wave 1 commercial alignment: retired active Request/Payee-user economics, retained transaction economics, and identified institutional programme operating costs and legacy reporting without approving pricing, terms, new formulas or acquisition-provenance use. |
| `0.9.3` | 2026-07-31 | Product Documentation Team | Aligned DOC-09 title references and commercial request-origin language with Request-as-linkage and Payment Obligation boundaries. |
| `0.1.0` | 2026-05-14 | Initial Author | Initial draft of DOC-02 Business Model & Unit Economics. |
| `0.2.0` | 2026-05-26 | Product Documentation Team | Reframed as foundation commercial framework, added unit economics model, revenue and cost taxonomy, commercial viability gates, pricing governance, promotion economics, settlement and reserve considerations, reporting expectations, assumptions, constraints, dependencies, risks, downstream impact, and standardized metadata and version history. |
| `0.3.0` | 2026-05-27 | Product Documentation Team | Updated commercial framework to account for payee onboarding and payee-created bill, invoice, fee, and rent payment request capability introduced in DOC-05 v0.2.0. Added payee-side revenue streams, payee onboarding and verification costs, request-origin economics, payer/payee fee allocation, payee-created request funnel metrics, rent/invoice economics, payee-side pricing governance, commercial viability gates, reporting and ledger expectations, assumptions, constraints, dependencies, risks, and open questions. |
| `0.4.0` | 2026-05-27 | Product Documentation Team | Simplified structure and language while preserving essential commercial model, revenue streams, fee principles, cost drivers, unit economics formulas, payee-created request economics, commercial viability gates, reporting expectations, assumptions, constraints, dependencies, risks, and open questions. |
| `0.5.0` | 2026-05-29 | Product Documentation Team | Confirmed payee-created requests and tenancy/rent as product MVP scope while keeping commercial launch enablement gated by pricing, partner, payout, verification, support, risk, and margin assumptions. |
| `0.6.0` | 2026-05-30 | Product Documentation Team | Aligned category examples with updated DOC-01 positioning for rent, invoices, medical bills, and domestic service obligations. |
| `0.7.0` | 2026-06-01 | Product Documentation Team | Aligned promotion economics with DOC-13 by adding qualification, entitlement, promotion quote, miles, external voucher, and partner fulfilment cost concepts while de-emphasizing payee-funded discounts as exceptional. |
| `0.8.0` | 2026-06-02 | Product Documentation Team | Clarified MVP commercial baseline for bill, fee, rent/tenancy, invoice, and approved-obligation categories in line with DOC-14 risk-control scope. |
| `0.9.0` | 2026-06-02 | Product Documentation Team | Added commercial impact references for DOC-09 deferred payment instruction, partial funding, quote revalidation, partial payout, and DOC-22 admin operations reporting. |
| `0.9.1` | 2026-07-26 | Product Documentation Team | Separated request acceptance from payment authorization, and separated request lifecycle outcomes from linked query/dispute cases and linked payment refund/chargeback outcomes in commercial metrics and open questions. |
| `0.9.2` | 2026-07-27 | Product Documentation Team | Distinguished direct payer-created payments, optional payer-to-payee linking requests, and payee-created payment requests across fee, promotion, profitability, and accounting treatment. |
