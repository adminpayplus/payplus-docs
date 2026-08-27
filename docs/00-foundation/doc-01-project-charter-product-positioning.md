---
document_id: DOC-01
title: Product Overview & Positioning
version: 1.0.1
status: Founder Working Baseline
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
last_updated: 2026-08-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-09 Payment Domain Architecture
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification
  - DOC-15 Privacy, Data Protection & Record Retention Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
---

# DOC-01 - Product Overview & Positioning

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-01` |
| **Title** | Product Overview & Positioning |
| **Version** | `1.0.1` |
| **Status** | Founder Working Baseline |
| **Owner** | Product Owner |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Commercial Lead |
| **Approvers** | Product Lead<br>Project Owner |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-02 Business Model & Unit Economics<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-09 Payment Domain Architecture<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification |

---

## 1. Purpose

This document defines the PayPlus product overview, positioning, MVP scope, product boundaries, key assumptions, risks, dependencies, success criteria, and open questions.

`DOC-01` is a foundation document.

It guides downstream product, payment, compliance, risk, security, engineering, commercial, and operational documentation.

This document does not define detailed product requirements, technical architecture, payment rules, legal conclusions, compliance controls, risk policies, security controls, or operating procedures. Those belong in downstream documents.

---


## 2. Product Summary

PayPlus is a controlled Bill and Rent Payment App. Bills use the accepted tiered Evidence, Declaration, Payment and Payout model; Tier 1 does not require attached Evidence, while Tier 2 and Tier 3 use the applicable official Bill Evidence gates. Rent remains a separate mandatory attached-Evidence journey. Consumer Users act as Payers and use cards subject to specialist-owned controls and fresh Payer authorization.

A Payee is the economic recipient. The Payee may be an individual or an institution/company and does not need to be a PayPlus User.

MVP scope is limited to:

- Rent through a separate tenancy/relationship journey; and
- specified supported controlled Bill Categories.

For Bills, the Payer either uses a Category-scoped Payee Directory or selects `Provide Payee myself`. Both methods remain governed by the already selected supported Bill Category. Neither method creates an open Payee marketplace or authorizes arbitrary payment.

PayPlus must not be positioned as a wallet, stored-value account, cashout service, peer-to-peer transfer app, remittance service, lending product, open invoice marketplace or arbitrary company-payment service.

PayPlus should remain data-disciplined. Material account, Evidence, Bill/Rent, acquisition, payment, payout, risk, promotion, support, communication and Admin actions should create structured, classified, auditable and purpose-linked data where appropriate. This does not approve advertising-network, data-broker, offsite activation, credit-scoring, insurance-underwriting or unrestricted profiling behavior.

### 2.1 Current MVP Decision Baseline

| Decision | Baseline |
|---|---|
| Consumer actor | Consumer Users are Payers only. |
| Economic Payee | An individual or institution/company recipient; PayPlus membership is not required. |
| Product families | Rent and specified supported controlled Bill Categories only. |
| Bill acquisition | Category-scoped Directory or `Provide Payee myself`; both remain controlled by the selected Category. |
| Rent | Separate tenancy/relationship journey; no controlled-Bill Directory use in MVP. |
| Institutional Programme and Directory | Bounded product policy belongs to DOC-05. Enrolment, Category association and Directory publication remain separate from transaction controls. |
| Bill/Rent identity, Category amendment, and Save | One authoritative source identity may become Saved/current through deliberate Setup or post-Payment Save, may become history-only only after confirmed Payment without Save, or may become Saved/Archived after ordinary Archive of a Saved/current source. Save records reuse intent on the same identity. Category is an amendable material Bill fact: changing it preserves the same Bill identity, updates the current Category, retains every prior Category in material-change history, and does not imply a reason for the change. |
| Request/BILLS-LINKING | Active behavior is retired. Only append-only documentation history and retired stable IDs remain as non-active evidence; no production runtime, historical reader, adapter or fallback exists. |
| Bill and Rent payments | MVP scope, subject to Evidence, Payee, destination, Payment, Payout, risk and authorization controls. |
| First launch jurisdiction | Hong Kong. |
| Initial card transaction classification assumption | Expected bill payment or ordinary online card purchase treatment, subject to acquirer confirmation. |
| Acquirer / MCC | Acquirer undecided; appropriate or special MCC treatment remains subject to acquirer confirmation. |
| Payout model | Expected operating-bank payout after upstream settlement; Hong Kong candidate rails include FPS, cheque and EPS, subject to final setup. |
| Multi-card support | MVP maximum of 6 cards per payment/profile, with narrower owner-controlled restrictions where applicable. |
| User Payment Instruction | MVP scope under DOC-09; not recurring payment. |
| Settlement timing | Expected T+1 to T+3 upstream settlement and same-day downstream payout after settlement, subject to approval. |
| KYC/KYB | Provider and final depth remain open; institutional programme enrolment is not transaction eligibility. |
| Notification | Institutional/company Payees are not notified. A governed individual may receive an optional Payer-initiated one-way notification under specialist controls. |
| Record retention | Indefinite retention remains the Founder-approved product and governance direction, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. That assessment must not silently rewrite immutable financial, audit, Save/Archive or case lineage. |
| Independent feature controls | Major functions must remain independently configurable or disableable under their owners. |
| Data and AI readiness | Business-recording, explainability, history, lineage, auditability and approved-purpose obligations remain required where relevant; exact structured events and technical representation remain separately gated. |
| Unresolved launch details | Remain assumptions, dependencies, open questions or gated requirements until confirmed. |

This baseline does not remove legal, compliance, PSP/acquirer, payout, risk, privacy, security, commercial or operational approval before production launch.

---

## 3. Market Problem

Many Payers want to pay eligible Bills or Rent by card for convenience, liquidity management, rewards, recordkeeping or payment flexibility, while many economic Payees do not directly accept cards.

PayPlus addresses this gap by allowing eligible card-funded payment to be routed to the intended individual or institutional recipient while preserving Evidence, Payer authorization, Payee and destination checks, risk controls, reconciliation and auditability.

The product does not depend on a Payee becoming a Consumer User, creating a Request or accepting a participant link.

---

## 4. Product Positioning

PayPlus should be positioned as:

> A controlled Bill and Rent Payment App that lets Payers use cards for eligible Rent and supported Bill Categories while Bills apply their accepted tiered Evidence model and PayPlus applies verification, risk, payout, reconciliation and audit controls.

Allowed language may include:

- Card-funded Bill and Rent payment.
- Pay eligible supported Bills by card.
- Pay eligible Rent by card where tenancy and relationship controls pass.
- Select an eligible institutional Payee from a Category-scoped Directory.
- Provide an individual or institutional Payee within the already selected supported Bill Category.
- Track payment status, receipts and applicable Evidence lineage in payment history.
- Privacy-safe payment intelligence for approved product, risk and operations purposes.

Prohibited positioning includes wallet, stored value, cash advance, cash withdrawal, cashout, unrestricted P2P, remittance, free transfer to any account, bank-account top-up, self-payment, open marketplace, arbitrary company payment, open money request, automatic payer charging, sale of financial data, financial surveillance, and unapproved credit or insurance decisioning.

Final public language belongs to DOC-07.

---

## 5. Target Users and Actors

| Actor | High-level meaning |
|---|---|
| Payer | The sole Consumer User for MVP; pays eligible controlled Bills or Rent obligations by card under the applicable Evidence treatment. |
| Economic Payee | Individual or institution/company recipient. A PayPlus User account is not required. |
| Admin and Operations | Internal actors applying owner-approved reviews, configuration and exception handling. |
| Partners | PSPs, acquirers, payout providers, banks, OCR, KYC/KYB, risk, notification and approved commercial service providers. |

DOC-05 owns detailed product-policy roles. An institution may enrol in the bounded Institutional Payee Programme without becoming a Consumer User.

---

## 6. Core Use Cases

| Use Case | Description |
|---|---|
| Directory-selected Bill payment | Payer selects a supported controlled Bill Category, chooses a published institutional Payee for that Category, provides Evidence and authorizes an eligible payment after all applicable controls pass. |
| Self-provided Bill payment | Payer selects a supported controlled Bill Category, provides an institutional or individual Payee within that Category, supplies Evidence and authorizes an eligible payment after all applicable controls pass. |
| Rent payment | Payer uses the separate tenancy/relationship journey and Rent-specific Evidence and controls. |
| Bill/Rent verification | PayPlus evaluates applicable Category, Evidence and Payee facts without treating Directory state as transaction truth. |
| Save or no-Save | Deliberate Setup makes the same authoritative Bill/Rent identity Saved/current without Payment. In immediate pay-now, an otherwise-unsaved source becomes Saved/current or history-only only after confirmed Payment, Payment Result and the optional Save resolution. Save never creates payment authorization. |
| Card-funded payment | Payer funds an eligible Payment through a supported card source. |
| Multi-card payment | Payer may use up to 6 cards per payment/profile subject to narrower owner controls. |
| User Payment Instruction | Payer may pay immediately or create a deliberate deferred instruction under DOC-09. |
| Payout and reconciliation | PayPlus applies approved settlement, payout and reconciliation controls for the intended economic Payee. |
| Receipt, Activity and audit | Payment remains visible through Activity/Payment History/Receipt even when its Bill/Rent source is history-only. |
| Optional individual notification | Payer may initiate a separately permitted one-way notification to a governed individual Payee; it is not Request, Linking, acceptance or authorization. |
| Manual review and monitoring | Higher-risk or mismatched facts follow their specialist-owned review and blocking rules. |

Detailed requirements belong to DOC-05 and the applicable domain owners.

---

## 7. MVP and Accepted Launch Bill Categories

MVP consists of two product families:

| Family | Boundary |
|---|---|
| Supported controlled Bill Categories | The Founder-confirmed launch inventory is the twelve Categories listed below and normatively owned by DOC-05 Section 3.1.1. Every Bill acquisition method remains within its selected supported Category. |
| Rent | Separate tenancy/relationship journey requiring Rent-specific Evidence, relationship, Payee, destination, risk and authorization controls. It does not use the Bill Directory. |

| Order | Accepted launch Category name |
|---|---|
| 1 | 會計費用 |
| 2 | 法律費用 |
| 3 | 醫療費用 |
| 4 | 電訊、流動電話及寬頻費 |
| 5 | 物業管理費 |
| 6 | 學費 |
| 7 | 安老院、殘疾人士院舍及受規管照顧服務 |
| 8 | 其他專業費用 |
| 9 | 車輛維修費 |
| 10 | 小型工程及樓宇維修費 |
| 11 | 註冊幼兒中心及育嬰園費用 |
| 12 | 寵物醫療及寄養費 |

The inventory names establish controlled Bill scope only. Category-specific eligibility, Evidence criteria, Directory contents and detailed labels remain with DOC-05 and DOC-12; Bills UX consumes their outcomes under DOC-06C, and approved Copy remains with DOC-07. Rent is not a Bill Category.

Each Category remains subject to DOC-03, DOC-12 and DOC-14 assessment and applicable payment, payout, privacy, operations and acceptance owners.

---

## 8. MVP Definition

The narrow controlled MVP includes:

| Area | MVP treatment |
|---|---|
| Payer registration and authentication | In scope. |
| Supported controlled Bill and separate Rent payment | In scope for the accepted twelve-category inventory and the separate Rent journey; Category-specific readiness remains owner-gated. |
| Category-scoped Directory and `Provide Payee myself` | In scope for Bills; Category remains governing in both methods. |
| Institutional Payee Programme | Bounded enrolment, Category association and publication policy in DOC-05; detailed execution and commercial terms remain owner-gated. |
| Evidence capture and verification | In scope under DOC-12. |
| Authoritative Bill/Rent source and projections | In scope; Save, history-only and Archive meanings follow DOC-05. |
| Card payment, quote and fee disclosure | In scope through approved partners and DOC-09. |
| Payout and reconciliation | In scope under DOC-10. |
| Receipt and lifecycle notifications | Payer notifications in scope; individual-Payee notification only within the approved one-way boundary. |
| Refund, cancellation and dispute | Minimum viable process under DOC-11. |
| Admin review | In scope as controlled execution, not product-policy authority. |
| OCR/document AI | Optional assisted capability under DOC-12. |
| Multi-card payment | Up to 6 cards per payment/profile, subject to owner controls. |
| Promotion engine | Optional and not an MVP blocker unless commercially required. |
| Active Request and BILLS-LINKING | Retired from target MVP; no dormant product stack. |
| Partner advertisements | Out of initial MVP unless separately approved. |

### 8.1 Gated MVP Requirements

| Area | Gating requirement |
|---|---|
| Launch jurisdiction | Hong Kong legal, regulatory, payment, privacy, tax, audit and operational assessment. |
| PSP/acquirer model | Support for intended transaction treatment, fees, authorization, MCC/classification and settlement. |
| Payout model | Approved operating-bank setup, rails, timing, exceptions and reconciliation. |
| KYC/KYB and Payee verification | Approved provider depth, sanctions, exceptions, Category and risk-tier rules. |
| Controlled Categories | Each enabled Category requires owner-confirmed Evidence, Payee, destination, risk, payment, payout, privacy and operational readiness. |
| Institutional Programme and Directory | Enrolment, Category association and publication remain separately governed and do not replace transaction checks. |
| Self-provided acquisition | Must remain Category-bound and subject to the same specialist controls. |
| Rent | Must meet tenancy, relationship, verification, limit and review controls. |
| Fees and disclosures | Must be approved before Payer authorization. |
| Multi-card | Maximum 6; partner, risk and reconciliation restrictions remain owner-controlled. |
| Refund, dispute and chargeback | Controlled handling under approved policy. |

---

## 9. Product Boundaries

### 9.1 In Scope

- Payer registration, authentication, profile and eligibility;
- supported controlled Bill Categories;
- separate Rent journey;
- Category-scoped institutional Directory;
- Category-bound self-provided individual or institutional Payee acquisition;
- bounded Institutional Payee Programme;
- Evidence capture and verification;
- authoritative Bill/Rent source identity and Save/history-only/Archive projections;
- payment quote, card authorization, multi-card payment and Payment Instructions;
- payout, settlement, receipts, reconciliation and audit;
- optional individual-only one-way notification under specialist controls;
- refunds, cancellations, disputes, chargebacks and exceptions;
- risk, privacy and manual-review controls;
- append-only documentation history and retired Request/Linking stable IDs as non-active governance evidence, with no runtime reader, adapter or fallback.

### 9.2 Out of Scope Unless Separately Approved

- wallet, stored value, cash withdrawal or cash advance;
- self-cashout, remittance or unrestricted transfer;
- arbitrary recipient or arbitrary company payment;
- open Payee, invoice or money-request marketplace;
- active Payee-user navigation, Request or BILLS-LINKING behavior;
- reciprocal visibility or Payee-user notifications;
- dormant Request/Linking queues, APIs, jobs, flags or tests;
- Directory state as Evidence truth or transaction authorization;
- cross-Category or unrestricted `Provide Payee myself`;
- automatic charging without fresh Payer authorization;
- payout unrelated to a supported controlled Bill/Rent obligation under the applicable Evidence treatment.

---

## 10. Product Principles

| Principle | Meaning |
|---|---|
| Controlled Bill/Rent obligation | Each Payment traces to an eligible controlled Bill/Rent source under the applicable Bill tier or Rent Evidence rule. |
| Payer-only Consumer model | Consumer product behavior belongs to the Payer; Payee is an economic role. |
| Controlled acquisition | Category precedes and governs both Bill acquisition methods. |
| Separation of meaning | Programme enrolment, Category association, publication, acquisition provenance and transaction controls remain distinct. |
| Fresh Payer authorization | No Directory, notification, Save or Admin action authorizes Payment. |
| No unrestricted cashout | Wallet, cashout, remittance and arbitrary transfer behavior remain prohibited. |
| One authoritative source | A Bill/Rent source receives stable identity only after the owner-governed preservation outcome establishes it for durable reference, before Save/reuse materialization or payment-facing handoff requires that identity. Identity establishment alone creates no Evidence acceptance, readiness, Payment or visibility projection. |
| Projection separation | Save, no-Save and Archive change visibility/reuse intent without rewriting immutable history. |
| Traceable lifecycle | Bill/Rent, Payable Basis, obligation, Checkout, Payment, Payment Application and Payout remain linked but distinct. |
| Risk-based controls | Concrete Evidence, Payee, destination, sanctions, fraud and anti-cashout issues retain specialist blocking effect. |
| Privacy-bound access | Display, notification, payment-history and support access remain approved-purpose and controlled. |
| Data-engine readiness | Material actions should produce governed, classified and auditable data. |

---

## 11. High-Level Payer Lifecycle

1. Payer signs in.
2. Payer selects Rent or a supported controlled Bill Category.
3. For a Bill, Payer uses the Category-scoped Directory or `Provide Payee myself`; Rent remains separate.
4. Payer provides permitted source and Evidence inputs; the applicable owners evaluate their facts.
5. The owner-governed source/Evidence preservation outcome may establish one authoritative Bill/Rent source ID for durable identification and reference before Save/reuse materialization or payment-facing handoff requires it. ID establishment alone creates no Evidence acceptance, Payee verification, destination or Payout readiness, risk clearance, Payment Obligation or Checkout readiness, Payment, Saved/current, Saved/Archived or history-only projection.

The high-level lifecycle then follows the Payer's chosen purpose:

- **Deliberate Setup:** the same source ID becomes Saved/current because the Payer deliberately chose setup/reuse. No Payment or Payment ID exists. Any later Payment receives fresh applicable Evidence, Payee, destination, Payout, risk, readiness, Checkout and Payer-authorization checks.
- **Immediate pay-now:** no Save decision occurs before Checkout. The Payer reviews current quote, fee, disclosures, timing and material facts, supplies fresh authorization, and proceeds through DOC-09/DOC-10 Payment and Payout controls. A confirmed Payment has its own Payment ID linked to the source. Payment Result then precedes the optional Save resolution for an otherwise-unsaved source: selected Save makes the same source Saved/current; declined, skipped, dismissed or closed Save makes it history-only. That projection resolution occurs before ordinary continuation to Activity, Payment History, Receipt or safe exit. Payment history remains visible regardless of Save.
- **Pre-confirmed failure or abandonment:** an established source may remain unprojected. It is not Saved/current, Saved/Archived or history-only and receives no invented visible status or route. DOC-09 owns applicable payment-lifecycle continuation or recovery, DOC-15 owns retention requirements, and the reviewed DOC-18 Draft requires the business history and action basis to remain explainable. Exact technical representation and lifecycle implementation remain separately authorized future work.

Detailed state, settlement, Payout, refund and chargeback rules belong to DOC-09, DOC-10 and DOC-11. Archive and source-list visibility never erase financial history.

---

## 12. Commercial Model Summary

Potential revenue sources remain subject to DOC-02 and separate approval:

- Payer-paid service fees;
- contractually supported institutional, biller or partner fees;
- programme enrolment, platform or payout fees only if separately approved;
- campaign-funded subsidies or partner-funded promotions;
- approved partner revenue share.

Potential fee allocations may involve the Payer, an institution/biller or a partner. This charter does not decide pricing, fee level, allocation, margin, contract, Institutional Programme pricing or commercial approval.

The model must account for processing, payout, refunds, chargebacks, fraud, promotions, institutional enrolment and verification where applicable, Evidence review, support, reconciliation, compliance, security and audit costs.

---

## 13. Compliance and Risk Positioning

PayPlus requires applicable legal, regulatory, network, partner, privacy, AML, consumer-protection and advertising assessment before launch.

Key boundaries:

- PayPlus is intended as controlled Bill/Rent payment facilitation.
- Directory publication and acquisition provenance do not establish transaction eligibility.
- Self-provided acquisition cannot bypass Category, Evidence, Payee, destination, sanctions, fraud, anti-cashout, payout or authorization controls.
- PayPlus must not enable wallet, stored value, unrestricted transmission or card-funded cashout.
- Each Payment requires applicable Evidence, intended-Payee/destination checks and fresh Payer authorization.
- Company/Individual label disagreement remains distinct from concrete defects.
- Optional individual notification remains one-way and subject to privacy, abuse, wrong-recipient, suppression, security, delivery-record and support controls.
- Appropriate disclosures, records, reconciliation and audit remain required.

Key risks include category bypass, Directory over-trust, fake Evidence, collusion, label/risk conflation, wrong-recipient notification, chargeback, AML, sensitive-document handling, partner-rule breach, reconciliation failure and negative unit economics.

---

## 14. Partner and Payment Model Summary

Potential partners include PSP, acquirer, processor, payout provider, bank, bill-payment aggregator, OCR, KYC/KYB, institutional enrolment, fraud/risk, notification, cloud, reconciliation and support providers.

Assessment must consider geography, controlled Categories, network rules, transaction treatment, MCC, economic-Payee classification, institutional programme requirements, payout, refunds, compliance, privacy, security, costs, reserves, reporting, reconciliation, operations, contracts and exit risk.

No partner capability or commercial term is approved by this charter.

---

## 15. Key Assumptions

| Assumption ID | Assumption | Validation Owner | Status |
|---|---|---|---|
| `ASM-DOC01-001` | Payers have demand for card-funded Bill/Rent payment in at least one launch Category. | Product / Commercial | Open |
| `ASM-DOC01-002` | At least one PSP/acquirer model supports the intended flow. | Product / Compliance / Payments | Open |
| `ASM-DOC01-003` | Eligible Categories can be verified with acceptable Evidence and operational effort. | Product / Operations / Risk | Open |
| `ASM-DOC01-004` | Payee and destination controls can sufficiently reduce cashout and fraud risk. | Risk / Compliance / Operations | Open |
| `ASM-DOC01-005` | Unit economics can remain positive after full costs. | Commercial / Finance | Open |
| `ASM-DOC01-006` | Manual review can support early MVP operations. | Operations | Open |
| `ASM-DOC01-007` | Original active Payee-created Request assumption. | Product / Legal / Compliance | Retired under Payer-only target |
| `ASM-DOC01-008` | Original Payee-created Request Evidence assumption. | Product / Risk / Operations | Retired under Payer-only target |
| `ASM-DOC01-009` | Original Payer acceptance of Payee-created Requests assumption. | Product / Design / Legal | Retired under Payer-only target |
| `ASM-DOC01-010` | Partner and payment data can support reliable reconciliation and audit. | Finance / Engineering / Operations | Open |
| `ASM-DOC01-011` | Governed structured data can support approved analytics and future model improvement. | Product / Data / Privacy | Open |
| `ASM-DOC01-012` | A bounded Institutional Programme and Category-controlled acquisition model can operate without becoming an open marketplace. | Product / Compliance / Risk | Open |

---

## 16. Key Constraints

| Constraint ID | Constraint | Impact | Owner |
|---|---|---|---|
| `CON-DOC01-001` | No wallet or stored-value product without separate approval. | Limits product architecture and UX. | Product / Compliance |
| `CON-DOC01-002` | No unrestricted card-funded cashout. | Requires Evidence, Payee and destination controls. | Risk / Compliance |
| `CON-DOC01-003` | Supported Categories require owner and partner approval. | Limits rollout. | Product / Compliance |
| `CON-DOC01-004` | Payout recipients and destinations require applicable checks. | Requires specialist workflow. | Risk / Operations |
| `CON-DOC01-005` | Partner capabilities may constrain multi-card, timing, refunds and chargebacks. | May constrain MVP. | Payments / Engineering |
| `CON-DOC01-006` | Sensitive data requires approved privacy controls. | Requires governed handling and retention. | Privacy / Security |
| `CON-DOC01-007` | Records must support audit and reconciliation. | Requires data and ledger design. | Finance / Engineering |
| `CON-DOC01-008` | Original Payee-created Request enablement constraint. | Superseded by formal retirement. | Product / Compliance / Risk |
| `CON-DOC01-009` | Original Payee-created Request authorization constraint. | Superseded by formal retirement. | Product / Legal / Payments |
| `CON-DOC01-010` | Original landlord-created Request constraint. | Superseded; Rent remains separately controlled. | Product / Risk / Operations |
| `CON-DOC01-011` | Data and AI use must remain purpose-linked, permissioned and traceable. | Requires governance and approval. | Product / Privacy / Data |
| `CON-DOC01-012` | Both Bill acquisition methods remain within the selected supported Category. | Prevents arbitrary payment escape. | Product / Risk |
| `CON-DOC01-013` | Directory publication cannot replace transaction controls. | Prevents false trust and bypass. | Product / Compliance / Risk |

---

## 17. Key Dependencies

| Dependency ID | Dependency | Required For | Owner | Status |
|---|---|---|---|---|
| `DEP-DOC01-001` | PSP/acquirer feasibility assessment. | Card acceptance. | Payments / Compliance | Open |
| `DEP-DOC01-002` | Payout provider or settlement model. | Payout execution. | Payments / Operations | Open |
| `DEP-DOC01-003` | Jurisdictional regulatory assessment. | Launch approval. | Legal / Compliance | Open |
| `DEP-DOC01-004` | Bill Category approval framework. | Category rollout. | Product / Risk / Compliance | Open |
| `DEP-DOC01-005` | Payee and destination verification process. | Anti-cashout control. | Risk / Operations | Open |
| `DEP-DOC01-006` | Privacy access, masking and lawful-handling controls under the accepted indefinite-retention direction, subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. | Evidence and contact handling. | Privacy / Security | Open |
| `DEP-DOC01-007` | Risk and manual-review rules. | Launch controls. | Risk / Operations | Open |
| `DEP-DOC01-008` | Reconciliation and ledger model. | Finance and audit. | Finance / Engineering | Open |
| `DEP-DOC01-009` | Content and disclosure approval. | User-facing launch. | Product / Legal / Compliance | Open |
| `DEP-DOC01-010` | Institutional enrolment, Category association and Directory publication operating model. | Programme/Directory execution. | Product / Compliance / Operations | Open |
| `DEP-DOC01-011` | Original Payer invitation mechanism for Requests. | Retired active behavior. | Product / Engineering / Privacy | Retired |
| `DEP-DOC01-012` | Original Payer response workflow for Requests. | Retired active behavior. | Product / Operations / Legal | Retired |
| `DEP-DOC01-013` | Data and AI governance model. | Analytics and future approved AI. | Data / Privacy / Engineering | Open |
| `DEP-DOC01-014` | Data and operations design must make the Founder-approved history-only source auditable without creating a new user route. | Implementation and acceptance evidence for the accepted architecture. | Data / Operations | Open downstream evidence |

---

## 18. Key Risks

| Risk ID | Risk | Impact | Initial Mitigation | Owner | Status |
|---|---|---|---|---|---|
| `RISK-DOC01-001` | Product is perceived or used as card-to-cash. | Regulatory, partner, fraud and loss risk. | Evidence, Payee, destination, limits and monitoring. | Risk / Compliance | Open |
| `RISK-DOC01-002` | Unsupported legal or transmission classification. | Delay, rejection or licensing consequence. | Assessment before launch. | Legal / Compliance | Open |
| `RISK-DOC01-003` | PSP/acquirer rejects model or Category. | Payment model unavailable. | Early due diligence. | Payments / Commercial | Open |
| `RISK-DOC01-004` | Fake Evidence or collusive Payees enable abuse. | Fraud and cashout risk. | Verification, limits and review. | Risk / Operations | Open |
| `RISK-DOC01-005` | Chargeback/refund creates loss. | Revenue leakage and burden. | Owner-defined handling. | Payments / Risk / Operations | Open |
| `RISK-DOC01-006` | Multi-card funding increases complexity. | Reconciliation or partner risk. | Owner controls within confirmed cap. | Product / Engineering / Payments | Open |
| `RISK-DOC01-007` | Disclosures are unclear. | Complaints and regulatory risk. | DOC-07 and legal review. | Product / Legal | Open |
| `RISK-DOC01-008` | Full-cost economics are negative. | Unsustainable model. | DOC-02 viability gates. | Commercial / Finance | Open |
| `RISK-DOC01-009` | Manual review does not scale. | Delay and error. | Controlled volume and automation. | Operations / Product | Open |
| `RISK-DOC01-010` | Sensitive Evidence is mishandled. | Privacy/security harm. | DOC-15/DOC-19 controls. | Privacy / Security | Open |
| `RISK-DOC01-011` | Original Payee-created Request confusion risk. | Superseded active product risk. | Active behavior retired. | Product / Legal | Retired |
| `RISK-DOC01-012` | Original reciprocal Payer/Payee visibility risk. | Superseded active product risk. | Active Payee-user visibility retired. | Privacy / Security | Retired |
| `RISK-DOC01-013` | Data or AI use appears exploitative. | Trust and regulatory risk. | Purpose limitation and governance. | Product / Privacy / Data | Open |
| `RISK-DOC01-014` | External activation exceeds approved scope. | Product and privacy breach. | Separate approval gate. | Commercial / Legal / Privacy | Open |
| `RISK-DOC01-015` | Self-provided acquisition bypasses Category policy. | Open-transfer and control failure. | Category selected before acquisition and continuously enforced. | Product / Risk | Open |
| `RISK-DOC01-016` | Directory is treated as verification or payment eligibility. | False trust and control bypass. | Explicit discovery-only meaning and specialist revalidation. | Product / Compliance / Risk | Open |
| `RISK-DOC01-017` | Individual notification reaches the wrong person or creates hidden Request semantics. | Privacy, abuse and support harm. | Governed Individual determination and one-way boundary. | Privacy / Risk / Product | Open |
| `RISK-DOC01-018` | Save/projection confusion hides or rewrites financial history. | Audit and user-trust harm. | One source identity and immutable lineage. | Product / Data / Operations | Open |

---

## 19. Launch Readiness Themes

PayPlus should not launch until:

- scope and positioning are approved, and each Category in the accepted twelve-category inventory meets its applicable owner-controlled launch gates;
- PSP/acquirer, payout and jurisdictional models are approved;
- Category, Evidence, Payee, destination, risk and anti-cashout controls are defined;
- Institutional Programme enrolment, Category association and Directory publication operations are defined if enabled;
- Rent Evidence and relationship controls are defined;
- Bill/Rent source identity and projection behavior is specified downstream;
- privacy, notification, data, security and approved-purpose record-access controls are defined;
- payment, Payout, refund, reconciliation, support and incident workflows are defined;
- disclosures and Acceptance Criteria are approved;
- operational owners and evidence are assigned.

Detailed launch gates belong to DOC-04 and DOC-20.

---

## 20. Success Criteria

| Metric | Description |
|---|---|
| Activated Payers | Consumer Users eligible to submit payment. |
| Controlled Bill/Rent sources | Eligible Bill/Rent contexts preserved for verification, Save or payment under the applicable Evidence treatment. |
| Controlled Bill/Rent completion | Eligible Payer-created Bill and Rent contexts that progress through applicable owner-controlled gates. |
| Enrolled institutions | Institutional programme participation reported separately from Category association and publication. |
| Completed Payments | Number and value successfully funded and applied. |
| Payment and Payout success | Owner-defined successful processing measures. |
| Saved/current versus history-only sources | Projection distribution without loss of financial traceability. |
| Repeat use | Payers completing more than one eligible Payment. |
| Manual review | Owner-defined Evidence, type, Payee, destination and risk review burden. |
| Notification safety | Permitted individual notifications, delivery/suppression and wrong-recipient/support outcomes under DOC-08/DOC-15. |
| Refund, cancellation and chargeback | Transaction-level outcome rates. |
| Fraud loss | Loss as a percentage of processed volume. |
| Contribution margin | Revenue after full attributable costs. |
| Data quality and analytics readiness | Governed lineage, classification, ownership and auditability. |

Applicable business facts, provenance, historical action basis, and reporting explainability must follow DOC-18. Exact metric formulae remain with their business owners, and technical metric representation remains separately gated.

---

## 21. Downstream Document Impact

| Document | Impact |
|---|---|
| `DOC-02` | Align commercial assumptions to Payer-created payment, controlled acquisition and bounded institutional programme costs without active Request economics. |
| `DOC-03` / `DOC-04` | Assess regulatory boundaries, external approvals and launch controls. |
| `DOC-05` | Own detailed Payer-only product policy, Institutional Programme, Directory, acquisition, Save and retirement meanings. |
| `DOC-06A` | Define Payer-only Bill/Rent journeys. |
| `DOC-06B` | Align navigation, Activity/History/Receipt and active Request/Linking route retirement. |
| `DOC-06C` | Define Bills/Rent acquisition, visibility, Save, Archive and Rent presentation. |
| `DOC-06D` | Map end-to-end UX Acceptance Criteria after preceding journey alignment. |
| `DOC-07` / `DOC-08` | Define user-facing language and notification delivery within the approved boundary. |
| `DOC-09` / `DOC-10` / `DOC-11` | Preserve Payment invariants; define payout, reconciliation, refund and dispute behavior. |
| `DOC-12` | Define Categories, Evidence/OCR, Payee match and verification outcomes. |
| `DOC-13` | Define promotion and reward behavior without using Directory provenance as eligibility truth. |
| `DOC-14` / `DOC-15` | Define risk, anti-cashout, privacy, contact and approved-purpose record-access controls. |
| `DOC-18` | Define the reviewed business-recording, explainability, history, lineage, audit-meaning, reporting-obligation, and owner-handoff contract; it does not create a Request-runtime reader or approve IDs, schemas, fields, events, persistence, or implementation. |
| `DOC-20` / `DOC-21` | Define acceptance, monitoring, support and incident evidence. |
| `DOC-22` | Execute approved Admin policy through governed queues, permissions and configuration; no product-policy ownership. |

---

## 22. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC01-001` | What Hong Kong legal, regulatory, payment, privacy, tax, audit and operational requirements apply before launch? | Project Owner / Legal | Critical | Open |
| `OQ-DOC01-002` | Original question asking which controlled Bill Categories form the initial launch inventory. | Product / Compliance / Risk | Critical | Answered by the Founder-confirmed twelve-category inventory in DOC-05 Section 3.1.1; retained for lineage |
| `OQ-DOC01-003` | Which PSP/acquirer supports the intended treatment and MCC/classification? | Payments / Commercial | Critical | Open |
| `OQ-DOC01-004` | Which operating-bank setup supports approved payout rails? | Payments / Operations | Critical | Open |
| `OQ-DOC01-005` | Which partner, risk and reconciliation controls apply within the six-card cap? | Product / Payments / Engineering | High | Partially open |
| `OQ-DOC01-006` | What KYC/KYB provider, depth, sanctions, exceptions and risk tiers apply? | Legal / Compliance / Risk | High | Open |
| `OQ-DOC01-007` | What transaction limits apply? | Risk / Compliance / Product | High | Open |
| `OQ-DOC01-008` | What pricing, fee allocation, subsidy, promotion, refund and reversal treatment applies? | Commercial / Finance | High | Open |
| `OQ-DOC01-009` | What disclosures are required before payment confirmation? | Product / Legal / Compliance | High | Open |
| `OQ-DOC01-010` | Which Evidence and record classes must be captured and what approved-purpose access, masking and audit controls apply to each transaction under the accepted indefinite-retention direction and its lawful-scope qualification? | Compliance / Privacy / Operations | High | Open |
| `OQ-DOC01-011` | Original active Payee-created Request module question. | Project Owner / Product / Compliance | Critical | Retired under Payer-only target |
| `OQ-DOC01-012` | Original Payee Request-creator eligibility question. | Product / Risk / Compliance | Critical | Retired under Payer-only target |
| `OQ-DOC01-013` | Original landlord-created Rent Request control question. | Product / Legal / Risk | Critical | Retired; Rent remains separately governed |
| `OQ-DOC01-014` | Original landlord-created Rent Request Evidence question. | Product / Legal / Risk / Operations | Critical | Retired; Rent Evidence remains owner-controlled |
| `OQ-DOC01-015` | Original Payee-to-Payer invitation question. | Product / Engineering / Privacy | High | Retired |
| `OQ-DOC01-016` | Original Payer response options for Payee-created Requests. | Product / Operations / Legal | High | Retired |
| `OQ-DOC01-017` | Original reciprocal Request visibility question. | Product / Privacy / Security | High | Retired |
| `OQ-DOC01-018` | Original active Request-abuse monitoring question. | Risk / Compliance / Operations | Critical | Retired; fake Evidence and collusion remain governed |
| `OQ-DOC01-019` | Original recurring Payee-created Request question. | Product / Legal / Payments | High | Retired |
| `OQ-DOC01-020` | Which data classes may support approved analytics, model improvement and personalization? | Product / Privacy / Data | High | Open |
| `OQ-DOC01-021` | Which data classes and fields are prohibited from external or model use? | Privacy / Legal / Risk | High | Open |
| `OQ-DOC01-022` | What governance applies before external data collaboration or activation? | Founder / Legal / Privacy / Compliance | High | Open |

---

## 23. Acceptance Criteria

DOC-01 is acceptable when it:

1. defines PayPlus as an controlled Bill/Rent Payment App;
2. states that Consumer Users are Payers only;
3. defines Payee as an individual or institution/company economic recipient that need not be a PayPlus User;
4. limits MVP to Rent and specified supported controlled Bill Categories;
5. states both Bill acquisition methods and the continuing Category restriction;
6. keeps Rent separate from the Bill Directory;
7. states the bounded Institutional Programme/Directory and specialist-owner boundary;
8. distinguishes deliberate Setup from immediate pay-now, prohibits pre-Checkout Save in immediate pay-now, and places Payment Result before optional same-ID Save/history-only resolution and downstream Activity/Payment History/Receipt;
9. keeps pre-confirmed established-but-abandoned sources unprojected and leaves their lifecycle, retention and representation to DOC-09, DOC-15 and DOC-18;
10. preserves high-level same-ID Save and Archive meaning without treating identity establishment as Evidence, readiness, Payment or projection truth;
11. states the optional individual-notification boundary without Request/Linking semantics;
12. formally retires active Request/BILLS-LINKING product behavior while preserving only append-only documentation history and retired stable IDs as non-active evidence;
13. preserves wallet, cashout, remittance, arbitrary payment and marketplace prohibitions;
14. records the accepted twelve-category inventory while keeping Category-specific eligibility, Evidence criteria, Directory contents, detailed labels, UI, routes, Copy, schemas, technical mechanisms, commercial terms and legal conclusions with their owners.

This document remains a concise charter and must not become a detailed PRD, legal memo, payment specification, risk policy or technical architecture.

---

## 24. Version History
| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| 1.0.1 | 2026-08-27 | Product Documentation Team | Aligned same-Bill Category amendment and prior-history meaning with the reviewed DOC-18 business-recording Draft, and removed current technical-representation implications. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. | Stage 11 alignment evidence |
| `0.12.1` | `2026-08-12` | Product Documentation Team | Corrected the high-level Payer lifecycle to distinguish deliberate Setup, immediate pay-now and pre-confirmed unprojected abandonment; placed optional same-ID Save/history-only resolution after confirmed Payment Result; and aligned Acceptance Criteria without adding technical lifecycle detail. |
| `0.12.2` | `2026-08-12` | Product Documentation Team | Applied the Founder-settled indefinite-retention rule to the charter and reframed the retained-record open question around capture, access, masking and audit controls without adding a disposition mechanism. |
| `0.12.0` | `2026-08-12` | Product Documentation Team | Recorded the Founder-confirmed twelve-category launch inventory and separate Rent boundary, answered `OQ-DOC01-002`, and removed nonexistent Request/Linking runtime-reader assumptions while preserving retired IDs and append-only documentation history. |
| `0.11.0` | `2026-08-10` | Product Documentation Team | Drafted the Founder-approved Payer-only charter alignment for controlled Bill/Rent scope, economic Payee meaning, Category-bound acquisition, institutional programme, same-ID Save, individual notification and active Request/BILLS-LINKING retirement. |
| `0.10.5` | `2026-08-05` | Product Documentation Team | Aligned three stale configurable/TBC card-cap statements with the confirmed MVP maximum of 6 cards per payment/profile while preserving narrower partner, risk, category, reconciliation, configuration, and enforcement controls as source-owned or open. |
| `0.10.4` | `2026-07-31` | Product Documentation Team | Aligned charter terminology and downstream ownership with DOC-09 Payment Domain Architecture, clarified Request as upstream linkage rather than payment, and preserved DOC-10 Settlement/Payout ownership. |
| `0.10.3` | `2026-07-27` | Product Documentation Team | Replaced obsolete payer-created payment-request wording with direct payer-created obligation/payment terminology, preserved optional payer-to-payee linking requests as a separate concept, and aligned evidence, lifecycle, traceability, and metric language. |
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of `DOC-01` Project Charter & Product Positioning. |
| `0.2.0` | `2026-05-26` | Product Documentation Team | Reframed as foundation charter, clarified product positioning, added product boundaries, candidate MVP scope, assumptions, constraints, dependencies, risks, launch readiness themes, downstream document impact, and standardized metadata and version history. |
| `0.3.0` | `2026-05-27` | Product Documentation Team | Updated charter to include controlled payee-created bill, invoice, fee, and rent payment request capability. Added payee onboarding, payer acceptance and authorization, evidence parity, landlord/rent evidence controls, request-origin positioning, additional risks, dependencies, success metrics, launch readiness themes, and downstream document impacts aligned to `DOC-05 v0.2.0`. |
| `0.4.0` | `2026-05-27` | Product Documentation Team | Simplified structure and language while preserving essential product positioning, MVP scope, payer-created and payee-created request models, boundaries, controls, risks, dependencies, open questions, and downstream impacts. |
| `0.5.0` | `2026-05-29` | Product Documentation Team | Confirmed payee-created requests and tenancy/rent as MVP scope, added gated MVP requirements, and clarified independent feature/module disablement. |
| `0.6.0` | `2026-05-30` | Product Documentation Team | Incorporated professional review feedback by broadening payer-created scope, adding payer-authorized push payment positioning, adding request delivery methods, updating MVP categories, and clarifying settlement, fee, and payout wording. |
| `0.7.0` | `2026-06-02` | Product Documentation Team | Clarified that bill and fee payments are MVP scope alongside rent/tenancy, aligned with DOC-14 risk-control baseline. |
| `0.8.0` | `2026-06-02` | Product Documentation Team | Aligned privacy wording with DOC-15 approved-purpose visibility, masking, and role-based access controls. |
| `0.9.0` | `2026-06-02` | Product Documentation Team | Added DOC-09 user payment instruction as MVP scope and added DOC-22 admin dashboard downstream ownership. |
| `0.10.0` | `2026-06-08` | Product Documentation Team | Added data-engine and AI-readiness positioning, trust-preserving intelligence boundaries, related assumptions, constraints, dependencies, risks, success metrics, downstream impacts, and open questions. |
| `0.10.1` | `2026-07-26` | Product Documentation Team | Confirmed the MVP maximum of 6 cards per payment/profile and narrowed the remaining open question to partner, risk, and reconciliation controls. |
| `0.10.2` | `2026-07-26` | Product Documentation Team | Aligned charter language with the canonical request lifecycle, distinguished payer-created payment from optional linking, separated request acceptance from payment authorization, separated evidence outcomes from request state, and treated query/dispute handling as a linked case. |
