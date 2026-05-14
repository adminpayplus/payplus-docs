---
title: PayPlus Project Continuation Context
version: 0.5.0
status: Draft
last_updated: 2026-05-14
classification: Internal
---

# PayPlus Project Continuation Context

## 1. Purpose

This file provides continuation context for future AI-assisted documentation work on the PayPlus project.

It preserves:

1. The original rationale and intended functionality of PayPlus.
2. The rationale behind the documentation framework.
3. The current documentation project status.
4. The current formal document register.
5. Key decisions already incorporated into `DOC-01`.
6. The recommended next step.

This file is a memory and alignment aid only.

It is not a source of truth.

If this file conflicts with approved formal documentation, the approved formal documentation wins.

---

## 2. Important Context Rule

This file should help a future AI session or a new project contributor quickly understand why the documentation project is being built in its current form.

However, this file must not be treated as:

- A final PRD.
- A legal opinion.
- A regulatory conclusion.
- A technical design.
- An API specification.
- An operational SOP.
- A security policy.
- A risk rulebook.
- A replacement for approved `DOC-XX` documents.

Detailed product, regulatory, technical, security, risk, and operational rules must be defined in the relevant formal `DOC-XX` documents.

---

## 3. PayPlus Original Product Rationale

PayPlus is intended to be a **Payment & Bill Settlement Platform**.

The original concept is to help users pay eligible bills and real payment obligations through supported payment methods, while PayPlus coordinates verification, funding, settlement, payout, reconciliation, risk control, and communication.

The core rationale is:

```text
A user has a real bill, invoice, rent obligation, school fee, utility bill,
management fee, insurance invoice, parking fee, or other eligible payment obligation.

PayPlus helps verify the payment purpose and payee.

The user funds the payment through supported funding methods.

PayPlus facilitates settlement or payout to the eligible biller, payee, merchant,
or payment recipient.

PayPlus tracks payment status, receipts, reconciliation, exceptions, and risk.
```

PayPlus is designed to support legitimate payment obligations, not unrestricted movement of money.

---

## 4. Product Positioning to Preserve

PayPlus should be positioned as:

- A Payment & Bill Settlement Platform.
- A controlled payment facilitation layer.
- A bill/payment-obligation verification platform.
- A multi-funding-source payment platform.
- A reconciliation-aware settlement platform.
- A compliance-conscious financial technology product.
- A product that can support users, billers, merchants, schools, property managers, professional service providers, healthcare providers, telecom providers, and other eligible payees, subject to approved scope.

PayPlus should not be positioned as:

- A general wallet.
- A stored value facility, unless later explicitly approved by legal and regulatory assessment.
- An unrestricted peer-to-peer transfer product.
- A remittance product, unless later explicitly approved by legal and regulatory assessment.
- A cashout tool.
- An anonymous payment mechanism.
- A crypto product.
- A lending product, unless later explicitly approved in the business model and regulatory documents.
- A bank.
- A payroll product.
- A general e-commerce checkout product.

A key boundary is:

```text
PayPlus should not allow transactions without a real bill, invoice, eligible payee,
or approved payment obligation.
```

---

## 5. Original Functional Rationale

The earlier PayPlus framework emphasized that the platform is more complex than a simple checkout app because real-money bill settlement affects payment logic, verification, fraud control, promotion accounting, refunds, chargebacks, reconciliation, and compliance.

The following functional rationales should be preserved.

### 5.1 Eligible Bill and Payment Obligation Handling

PayPlus is expected to support eligible categories and payment obligations approved for MVP or future releases.

Earlier examples included:

- Rent or tenancy-related payments.
- School fees or education invoices.
- Utility bills.
- Property management fees.
- Parking fees.
- Insurance invoices.
- Other approved bill or invoice categories.

`DOC-01` version `0.2.0` has since refined the MVP bill scope for Hong Kong.

The current MVP bill types captured in `DOC-01` are:

| No. | MVP Bill Type | Notes |
|---:|---|---|
| 1 | Tuition fees | Education-related payment obligation |
| 2 | School fees | School or education-provider payment obligation |
| 3 | Management fees | Property/building management-related fees |
| 4 | Renovation fees | Requires invoice, quotation, milestone bill, signed work order, or approved payment evidence |
| 5 | Broadband internet fees | Telecom / internet service bills |
| 6 | Mobile phone fees | Telecom / mobile service bills |
| 7 | Domestic helper salary | Included with controls as an approved bill-like obligation; not general P2P, payroll, cashout, or remittance |
| 8 | Toll fees | Mobility/transport-related fees |
| 9 | Parking fees | Parking operator, property, or facility-related payment obligation |
| 10 | Tutorial centre fees | Education / tutorial service provider fees |
| 11 | Private doctor consultation fees | Healthcare service fee |
| 12 | Clubhouse / leisure fees | Clubhouse, membership, leisure, or facility-related payment obligation |
| 13 | Entertainment / subscription fees | Approved subscription or entertainment service bills; not general e-commerce purchases |
| 14 | Law / legal opinion fees | Legal/professional service fee supported by invoice, fee note, or engagement reference |

Framework rationale:

```text
PayPlus must know what the user is paying, why the payment is legitimate,
who should receive the payment, and whether the bill category is supported.
```

The exact verification requirements for each bill type must be defined in `DOC-12` and related risk/operations documents.

---

### 5.2 Multi-Funding Source, Partial Payment, and Combined Payment

PayPlus should support payments using multiple funding sources.

`DOC-01` version `0.2.0` confirms that the following are MVP capabilities:

- Multiple funding sources.
- Partial payment.
- Combined payment.
- Multiple child payment transactions under one parent payment request.
- Use of the same or different payment methods/cards for one payment obligation, where supported.

The earlier rationale includes:

- Parent payment request.
- Child payment transactions.
- Split amount allocation.
- Partial payment.
- Combined payment handling.
- Funding progress.
- Remaining amount.
- Retry after failed child transaction.
- Per-child-transaction fee calculation.
- Mixed payment methods where supported.
- Settlement only when payment readiness conditions are met.

Important wording principle:

Use:

- `Payment Progress`
- `Funding Progress`
- `Remaining Amount`
- `Amount Paid`
- `Amount Pending`
- `Settlement Status`
- `Payout Status`

Avoid:

- `Wallet Balance`
- `Stored Balance`
- `User Balance`
- `Top-up Balance`
- `Cash Balance`

Reason:

```text
The product should not look or behave like a stored-value wallet.
```

---

### 5.3 Payment Profiles and Tokenization

PayPlus may allow users to save payment methods through tokenized payment profiles, where supported by PSPs or payment providers.

`DOC-01` version `0.2.0` confirms that credit card tokenization is an MVP requirement, subject to selected PSP/acquirer support.

The original rationale is:

- PayPlus should avoid storing PAN or CVV.
- Card or payment credentials should be handled through PSP-hosted fields, SDKs, or tokenization.
- PayPlus should store only token references where appropriate.
- Token lifecycle and user authorization must be documented.
- PCI scope strategy must be considered early.

Detailed card data flow, token lifecycle, PCI scope approach, and security controls belong in:

- `DOC-03` Regulatory, PSP & Acquirer Assessment.
- `DOC-04` Compliance Certification Roadmap.
- `DOC-09` Payment Request, Multi-Funding Source & Settlement.
- `DOC-17` API & Third-party Integration.
- `DOC-19` Security, Tokenization & Access Control.

---

### 5.4 AI/OCR-Assisted Bill Verification as MVP Capability

A major earlier framework decision is that OCR / AI-assisted bill verification should be treated as an MVP capability, not a later optimization.

`DOC-01` version `0.2.0` confirms that:

- Bill verification workflow is an MVP requirement.
- AI-assisted bill review is an MVP requirement.
- The specific AI service/provider has not been selected.
- The architecture must preserve an integration boundary/API for AI bill review.
- Human review fallback must exist.

Reason:

If users submit large volumes of invoices, tuition bills, school bills, management fee statements, telecom bills, renovation invoices, medical bills, legal fee notes, salary-related evidence, or similar documents, fully manual review creates risks:

- Review SLA bottlenecks.
- Month-end payment congestion.
- Excessive manual operation cost.
- Long user waiting time.
- Inconsistent reviewer decisions.
- Increased fake-document risk.
- Weak scalability.

The intended MVP approach is not necessarily full automation.

The preferred approach is:

```text
OCR or document AI extraction
+ rule-based and/or AI-assisted validation
+ confidence scoring
+ configurable review routing
+ human-in-the-loop review
+ reviewer override
+ audit trail
+ feedback for future improvement
```

Framework principle:

```text
The system must support confidence-based routing and configurable review thresholds.
Specific thresholds must not be hardcoded in the framework.
```

Vendor examples such as Google Document AI, AWS Textract, Azure AI Document Intelligence, Veryfi, Rossum, or custom models may be useful for future evaluation, but the framework should not commit to a vendor.

---

### 5.5 Payee Verification

PayPlus must verify or validate payee information to reduce wrong-payee, fake-payee, cashout, and fraud risks.

`DOC-01` version `0.2.0` confirms that MVP may support both institutional and personal payees, subject to controls.

Relevant concepts include:

- Payee name matching.
- Biller or merchant validation.
- Invoice or account reference capture.
- Payee whitelist or approved payee handling.
- Unsupported payee detection.
- Institutional/person indicator.
- Payee type labels.
- Payee category labels.
- Bill types supported.
- Geography.
- Supported payout methods.
- Verification status.
- Risk status.
- Compliance status.
- Mismatch review.
- Manual override with audit trail.

Personal payees may require stricter verification, fraud controls, payout controls, and compliance review than institutional payees.

Detailed payee verification rules belong in `DOC-12`, `DOC-14`, and `DOC-21`.

---

### 5.6 Promotion Engine and Partner Advertisement as Core Architecture Areas

The earlier framework emphasized that promotion logic must not be scattered across business model, PRD, UX, refund, and data model documents.

`DOC-01` version `0.2.0` confirms that promotions and partner advertisement placements are MVP capabilities.

If PayPlus supports coupons, vouchers, referral rewards, membership benefits, bank promotions, fee waivers, cashback, partner campaigns, or partner advertisement placements, the logic affects:

- Checkout.
- Fee calculation.
- Parent payment request.
- Partial payment.
- Combined payment.
- Refund.
- Chargeback.
- Fraud.
- Accounting.
- Campaign analytics.
- Customer support.
- API.
- Admin portal.
- Placement governance.
- Marketing compliance.

Therefore, PayPlus should maintain a distinct Promotion Engine document.

Important earlier decision:

```text
Coupon or promotion redemption should generally attach to the Parent Payment Request,
not only to an individual Child Transaction.
```

Reason:

```text
PayPlus supports partial payment and multiple child payment transactions.

If promotion redemption is attached only to a child transaction, cancellation,
payment failure, refund, or chargeback can make coupon state difficult to manage.
```

Detailed promotion rules, stacking rules, reward timing, advertisement approval workflows, placement inventory, and API endpoints should not be defined in this context file.

They should be defined in `DOC-13`.

---

### 5.7 Refund, Cancellation, Chargeback, and Promotion Reversal

Because PayPlus may support partial payment, combined payment, multiple child transactions, and promotions, refund and cancellation logic must account for:

- Cancellation before funding.
- Cancellation during partial payment.
- Cancellation after full funding but before payout.
- Cancellation after payout.
- Child transaction refund.
- Parent payment request refund.
- Promotion reservation release.
- Promotion consumption reversal.
- Referral reward reversal.
- Chargeback and dispute evidence.
- Financial loss allocation.
- User communication.

The documentation must preserve this complexity and not reduce refund handling to a simple single-transaction refund model.

Detailed rules belong in `DOC-11`, with dependencies on `DOC-09`, `DOC-10`, `DOC-13`, and `DOC-14`.

---

### 5.8 Payout and Reconciliation

PayPlus must be designed around traceable real-money settlement.

Important concepts:

- Parent payment request.
- Child payment transactions.
- Payout readiness.
- Payout execution.
- PSP settlement reports.
- Bank statement matching.
- Fee reconciliation.
- Promotion subsidy reconciliation.
- Refund reconciliation.
- Chargeback reconciliation.
- Exception handling.
- Finance reporting.

`DOC-01` version `0.2.0` captures candidate payout methods as:

- FPS.
- Online banking transfer.
- EPS, where feasible.
- Cheques.

These payout methods are provisional and require feasibility validation.

Reason:

```text
PayPlus must be able to explain how user funding became biller/payee settlement
and how every amount, fee, subsidy, refund, and dispute was reconciled.
```

Detailed payout and reconciliation rules belong in `DOC-10`.

---

### 5.9 Risk, AML, Anti-Cashout, Fraud, and Dynamic Authentication

PayPlus must protect against:

- Fake bills.
- Duplicate documents.
- Fake payees.
- Collusive payees.
- Stolen payment methods.
- Chargeback abuse.
- Promotion abuse.
- Velocity abuse.
- Cashout behavior.
- Unsupported quasi-cash flows.
- Suspicious payment patterns.
- Misuse of domestic helper salary payment flow.
- General e-commerce use hidden under entertainment/subscription category.
- High-value renovation fraud.
- Personal payee payout abuse.

Relevant control areas include:

- AML risk indicators.
- Anti-cashout controls.
- Fraud scoring.
- Velocity checks.
- Document fraud signals.
- Payee risk.
- User risk tiering.
- Device, IP, and payment profile risk.
- Promotion abuse controls.
- Login 2FA.
- Transaction step-up authentication.
- Card 3DS / SCA where applicable.
- Admin 2FA.
- Admin review queues.
- Risk decision audit trail.
- Category-specific risk rules.
- Domestic helper salary controls.
- Personal payee controls.
- High-value renovation payment controls.

Detailed thresholds belong in risk rulebooks or operations policies, not the framework.

Detailed risk rules belong in `DOC-14` and `DOC-21`.

---

### 5.10 Notification, Receipt, and Communication

The earlier framework separated notification and receipt logic into a dedicated document because PayPlus communications directly affect trust, auditability, and support workload.

Communication must cover events such as:

- Payment request created.
- Document submitted.
- Document approved.
- Document rejected.
- Funding succeeded.
- Child transaction failed.
- Payment partially funded.
- Payment fully funded.
- Payout processing.
- Payout completed.
- Refund initiated.
- Refund completed.
- Promotion reserved.
- Promotion released.
- Promotion consumed.
- Chargeback or dispute notice.
- Receipt issued.
- Action required.

Reason:

```text
PayPlus communication is not just marketing notification.
It is part of payment clarity, audit trail, user authorization, and support reduction.
```

Detailed notification and receipt rules belong in `DOC-08`.

---

### 5.11 Compliance Certification Planning

The earlier framework emphasized that PCI DSS, ISO 27001, SOC 2, and related evidence planning should be considered early.

`DOC-01` version `0.2.0` states:

- No formal compliance certification is required for early pre-launch activities.
- ISO and PCI should be considered for production operation.
- Exact timing and scope require legal, compliance, and security confirmation.

This does not mean all controls must be completed at framework stage.

It means PayPlus documentation should plan for:

- PCI DSS scope strategy.
- Target SAQ type, if applicable.
- Card data flow boundaries.
- Tokenization control approach.
- ISO 27001 roadmap.
- SOC 2 roadmap, if needed.
- Control mapping methodology.
- Evidence ownership.
- Audit readiness timeline.
- ISMS policy set.
- Access review evidence.
- Incident response evidence.
- Vendor risk management evidence.

Important principle:

```text
The framework should define certification goals, scope strategy, control mapping
approach, evidence ownership, and document dependencies.

It should not contain the full PCI control matrix, ISO control implementation,
or complete ISMS policy text.
```

---

## 6. Framework Rationale to Preserve

The PayPlus documentation framework exists because PayPlus has many interdependent domains.

A simple PRD is not sufficient.

The documentation set must separate responsibilities across:

- Business positioning.
- Commercial model.
- Regulatory and PSP assessment.
- Compliance certification planning.
- Product requirements.
- User journey.
- Authorization and disclosure.
- Notification and receipt.
- Payment request and settlement.
- Bill verification.
- Payout and reconciliation.
- Refund and dispute handling.
- Promotion engine.
- AML, fraud, and anti-cashout controls.
- Privacy and retention.
- Technical architecture.
- API and integration.
- Data model, state, and audit events.
- Security and access control.
- Testing and go-live.
- Monitoring, incident response, and operational SOPs.
- ISMS and compliance policies.

The framework should define:

```text
which documents are needed,
what each document owns,
what each document must cover,
what decisions must be recorded,
and where detailed rules should live.
```

The framework should not prematurely lock:

- OCR confidence thresholds.
- Fuzzy match thresholds.
- Transaction review amount thresholds.
- Exact PSP or OCR vendors.
- Full API endpoint lists.
- Exact database schema.
- Full PCI DSS control implementation.
- Full ISO 27001 control implementation.
- Complete ISMS policies.
- Detailed promotion stacking rules.
- Detailed fraud scoring weights.
- Exact payout bank operational processes.
- Exact campaign placement rules.

Those details should be handled in detailed specs, rulebooks, ADRs, appendices, vendor evaluations, SOPs, or configuration-controlled policies.

---

## 7. Current Documentation Structure

The current documentation structure has already been adjusted and should be followed unless `DOC-00` is later revised.

Current intended structure:

```text
payplus-docs/
├── README.md
└── docs/
    ├── 00-foundation/
    │   ├── doc-00-documentation-governance.md
    │   ├── doc-01-project-charter-product-positioning.md
    │   ├── doc-02-business-model-unit-economics-commercial-model.md
    │   ├── doc-03-regulatory-psp-acquirer-assessment.md
    │   └── doc-04-compliance-certification-roadmap.md
    ├── 01-product/
    ├── 02-payment-domain/
    ├── 03-bill-verification/
    ├── 04-growth-ecosystem/
    ├── 05-risk-compliance-privacy/
    ├── 06-engineering/
    ├── 07-security-access-control/
    ├── 08-qa-release-operations/
    ├── 99-isms-policies/
    ├── ai-context/
    │   └── project-continuation-context.md
    ├── changelog/
    ├── decision-log/
    ├── glossary/
    ├── templates/
    └── traceability/
```

The current structure differs slightly from the earlier v3.1 framework folder numbering, but preserves the same conceptual domains.

Future work should stick with the current structure unless a formal documentation governance change is made.

---

## 8. Current Document Register

The current planned document register is:

| Document ID | Document Name | Folder | Status |
|---|---|---|---|
| `DOC-00` | Documentation Governance | `00-foundation/` | Draft |
| `DOC-01` | Project Charter & Product Positioning | `00-foundation/` | Draft |
| `DOC-02` | Business Model, Unit Economics & Commercial Model | `00-foundation/` | Planned |
| `DOC-03` | Regulatory, PSP & Acquirer Assessment | `00-foundation/` | Planned |
| `DOC-04` | Compliance Certification Roadmap | `00-foundation/` | Planned |
| `DOC-05` | Master PRD & Feature Requirements | `01-product/` | Planned |
| `DOC-06` | User Journey, UX Flow & Service Blueprint | `01-product/` | Planned |
| `DOC-07` | Content, Disclosure & User Communication | `01-product/` | Planned |
| `DOC-08` | Notification, Receipt & Communication Rules | `01-product/` | Planned |
| `DOC-09` | Payment Request, Multi-Funding Source & Settlement | `02-payment-domain/` | Planned |
| `DOC-10` | Payout & Reconciliation | `02-payment-domain/` | Planned |
| `DOC-11` | Refund, Cancellation & Chargeback | `02-payment-domain/` | Planned |
| `DOC-12` | Bill Category, Document AI/OCR & Payee Verification | `03-bill-verification/` | Planned |
| `DOC-13` | Promotion Engine & Campaign Rules | `04-growth-ecosystem/` | Planned |
| `DOC-14` | AML, Anti-Cashout, Fraud & Risk Controls | `05-risk-compliance-privacy/` | Planned |
| `DOC-15` | Privacy, Data Protection & Retention | `05-risk-compliance-privacy/` | Planned |
| `DOC-16` | Technical Architecture | `06-engineering/` | Planned |
| `DOC-17` | API & Third-party Integration | `06-engineering/` | Planned |
| `DOC-18` | Data Model, Transaction Ledger & Reporting | `06-engineering/` | Planned |
| `DOC-19` | Security, Tokenization & Access Control | `07-security-access-control/` | Planned |
| `DOC-20` | Testing, UAT, Release & Go-Live Checklist | `08-qa-release-operations/` | Planned |
| `DOC-21` | Monitoring, Incident Response & Operations Runbook | `08-qa-release-operations/` | Planned |

---

## 9. Mapping from Earlier v3.1 Framework to Current Structure

The earlier v3.1 framework remains important as rationale, but the current repository structure should be followed.

Conceptual mapping:

| Earlier v3.1 Concept | Current Document |
|---|---|
| Project Charter & Product Positioning | `DOC-01` |
| Business Model, Pricing, Fee & Promotion Policy | `DOC-02`, with promotion mechanics in `DOC-13` |
| Regulatory, PSP, Acquirer & Payment Method Assessment | `DOC-03` |
| Compliance Certification Roadmap & Control Framework | `DOC-04` |
| Master PRD & Feature Requirement Index | `DOC-05` |
| User Journey, UX Flow & Service Blueprint | `DOC-06` |
| Content, Disclosure & User Authorization Spec | `DOC-07` |
| Notification, Receipt & Communication Spec | `DOC-08` |
| Payment Request, Multi-Funding Source & Settlement Spec | `DOC-09` |
| Bill Category, Document AI/OCR & Payee Verification Spec | `DOC-12` |
| Payout, Reconciliation & Finance Operations Spec | `DOC-10` |
| Refund, Cancellation, Chargeback & Dispute Spec | `DOC-11` |
| Promotion Engine — Coupon, Voucher, Referral & Membership Spec | `DOC-13` |
| AML, Anti-cash-out, Fraud & Dynamic Authentication Risk Control Spec | `DOC-14` |
| Privacy, Data Protection & Record Retention Spec | `DOC-15` |
| Technical Architecture Spec | `DOC-16` |
| API & Third-party Integration Spec | `DOC-17` |
| Data Model, Transaction State & Audit Event Spec | `DOC-18` |
| Security, Tokenization, Authentication & Admin Control Spec | `DOC-19` |
| Testing Strategy, UAT & Go-live Checklist | `DOC-20` |
| Monitoring, Incident Response & Operational SOPs | `DOC-21` |
| ISMS Policies & Compliance Annex | `99-isms-policies/` |

---

## 10. Documentation Project Current Status

### 10.1 Completed

The formal documentation repository structure has been defined.

The following document has been created and refined:

```text
docs/00-foundation/doc-00-documentation-governance.md
```

Document details:

| Field | Value |
|---|---|
| Document ID | `DOC-00` |
| Title | Documentation Governance |
| Version | `0.1.0` |
| Status | Draft |
| Classification | Internal |
| Last Updated | `2026-05-14` |

`DOC-00` defines:

- Documentation purpose.
- Documentation scope.
- Source-of-truth hierarchy.
- Repository structure.
- Document numbering.
- Document status rules.
- Versioning rules.
- Ownership and approval rules.
- Change control expectations.
- Requirement ID convention.
- Business rule ID convention.
- Test case ID convention.
- ADR governance.
- Template governance.
- Traceability expectations.
- AI context governance.
- Sensitive information rules.
- Review cadence.
- Changelog rules.
- Acceptance criteria.
- Open questions.
- Document changelog.

The following document has also been created and updated:

```text
docs/00-foundation/doc-01-project-charter-product-positioning.md
```

Document details:

| Field | Value |
|---|---|
| Document ID | `DOC-01` |
| Title | Project Charter & Product Positioning |
| Version | `0.2.0` |
| Status | Draft |
| Classification | Internal |
| Last Updated | `2026-05-14` |

`DOC-01` now captures the core product charter and product positioning for PayPlus.

---

### 10.2 DOC-00 Refinements Already Made

`DOC-00` has been reviewed and refined.

Important refinements made:

- Section 6 now contains both:
  - Document IDs must not be reused.
  - If a document is deprecated or retired, its document ID remains reserved.
- Section 5 includes repository-structure change control guidance.
- Section 20 is named `Changelog Rules`.
- Section 23 is named `Document Changelog`.
- Formatting has been cleaned up.
- Governance content has been kept separate from PayPlus product behavior.

---

### 10.3 DOC-01 Creation and Refinements Already Made

`DOC-01` has been created and updated to version `0.2.0`.

Important decisions and refinements captured in `DOC-01` include:

- PayPlus is positioned as a **Payment & Bill Settlement Platform**.
- PayPlus must not be positioned as a wallet, stored value facility, unrestricted P2P transfer product, remittance product, cashout service, crypto product, bank substitute, lending product, payroll product, or general e-commerce checkout product.
- MVP launch geography is **Hong Kong only**.
- Future expansion candidates are:
  - Taiwan.
  - Japan.
  - Thailand.
  - Mainland China.
  - Malaysia.
- MVP bill types are explicitly listed.
- MVP payment methods are intended to include:
  - Credit card.
  - AlipayHK.
  - FPS.
- Credit card tokenization is an MVP requirement, subject to PSP/acquirer support.
- Multi-funding-source payment is an MVP capability.
- Partial payment is an MVP capability.
- Combined payment is an MVP capability.
- Bill verification workflow is an MVP requirement.
- AI-assisted bill review is an MVP requirement.
- Specific AI provider/service has not been selected.
- Promotions are an MVP capability.
- Partner advertisement placement is an MVP capability.
- Candidate payout methods include:
  - FPS.
  - Online banking transfer.
  - EPS, where feasible.
  - Cheques.
- User segmentation capability is required for:
  - Demographic segmentation.
  - Behavioral segmentation.
  - Geographic segmentation.
- Payee labels/attributes should be supported.
- Domestic helper salary is included only as an approved bill-like payment obligation with controls, not as unrestricted P2P, payroll, remittance, or cashout.
- No formal compliance certification is required for early pre-launch activities, but ISO and PCI should be considered for production operation.
- Several `DOC-01` open questions were closed, answered, or carried forward as formal dependencies.

---

### 10.4 Current AI Context Update

This file has now been updated to version `0.5.0` to preserve:

- The original PayPlus product rationale.
- The earlier v3.1 framework reasoning.
- The distinction between framework-level decisions and detailed implementation decisions.
- The current documentation structure.
- The current document register.
- The current `DOC-01` decisions.
- The next recommended step after `DOC-01`.

---

## 11. Source-of-Truth Hierarchy

Approved formal documentation is the source of truth.

Current source-of-truth hierarchy from `DOC-00`:

1. Approved core `DOC-XX` documents.
2. Approved ADRs.
3. Approved rulebooks.
4. Approved API, data model, and test specifications.
5. Approved ISMS policies, where relevant.
6. Approved traceability registers.
7. AI context summaries.
8. Informal notes or chat history.

This AI context file is supporting guidance only.

It does not override approved formal documents.

Current practical note:

`DOC-00` and `DOC-01` are currently in `Draft` status.

Until formally approved, they are stronger working references than chat history, but not final approved source-of-truth documents.

---

## 12. Important Principles for Future AI Work

Future AI assistance should preserve the following principles:

- PayPlus is a Payment & Bill Settlement Platform.
- PayPlus is not a general wallet.
- PayPlus is not a stored value facility unless explicitly approved later.
- PayPlus is not an unrestricted P2P transfer product.
- PayPlus is not a remittance product unless explicitly approved later.
- PayPlus is not a cashout tool.
- PayPlus is not a payroll product.
- PayPlus is not a general e-commerce checkout product.
- PayPlus should not support transactions without real bills, invoices, eligible payees, or approved payment obligations.
- Hong Kong is the MVP launch geography.
- Taiwan, Japan, Thailand, Mainland China, and Malaysia are future expansion candidates, not MVP scope.
- MVP bill types are limited to the list captured in `DOC-01`.
- Domestic helper salary is included only as an approved bill-like payment obligation with controls.
- Entertainment/subscription fees must remain bill-backed or subscription-obligation-backed, not general e-commerce purchases.
- Multi-funding-source and partial payment logic are core PayPlus concepts.
- Combined payment is an MVP concept.
- Parent payment request and child payment transaction modeling should be preserved.
- Use `Payment Progress`, `Funding Progress`, and `Remaining Amount`; avoid wallet-like terms.
- Credit card, AlipayHK, and FPS are intended MVP payment methods, subject to PSP/acquirer and banking feasibility.
- Credit card tokenization is an MVP requirement, subject to selected PSP/acquirer support.
- AI/OCR-assisted bill verification is an MVP capability.
- AI/OCR should support extraction, confidence scoring, configurable routing, human review, reviewer override, and audit trail.
- The AI bill review provider is not selected and should not be prematurely locked.
- Payee verification is required for settlement readiness.
- Personal payees may require stricter controls than institutional payees.
- Promotion engine logic should be centralized, not scattered.
- Promotion redemption should generally attach to the parent payment request.
- Partner advertisement placement is an MVP capability but requires governance and compliance controls.
- Refund, chargeback, and cancellation rules must account for partial payment, combined payment, multiple child transactions, and promotion reversal.
- Payout and reconciliation are core to PayPlus, not back-office afterthoughts.
- Candidate payout methods are FPS, online banking transfer, EPS where feasible, and cheques; final feasibility remains pending.
- Risk, AML, anti-cashout, fraud, and dynamic authentication controls are central to product safety.
- Notification, receipt, and communication rules deserve a dedicated document.
- PCI DSS, ISO 27001, SOC 2, and ISMS readiness should be planned early.
- No formal compliance certification is required for early pre-launch activities unless later changed.
- Framework documents should avoid hardcoding thresholds, vendor choices, API endpoints, database schemas, or full policy text.
- Detailed rules should live in detailed specs, rulebooks, ADRs, appendices, vendor evaluations, and SOPs.
- No secrets, credentials, tokens, or real customer data should be stored in documentation.

---

## 13. Known Open Questions

`DOC-00` currently tracks the following open questions:

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC00-001` | Who is the official Documentation Owner? | Project Owner | High | Open |
| `OQ-DOC00-002` | Who are the required approvers for each document category? | Project Owner | High | Open |
| `OQ-DOC00-003` | Should approvals be handled through pull requests, signed records, tickets, or another method? | Project Owner | Medium | Open |

`DOC-01` version `0.2.0` closed or answered several earlier product-positioning questions, but the following important questions remain open or require further definition in later documents:

| Question ID | Question | Suggested Target Document | Priority | Status |
|---|---|---|---|---|
| `OQ-CTX-001` | What PSPs, acquirers, or payment partners are being considered for credit card, AlipayHK, FPS, and tokenization? | `DOC-03` / `DOC-17` | High | Open |
| `OQ-CTX-002` | What payout methods are actually feasible for supported institutional and personal payees? | `DOC-03` / `DOC-10` / `DOC-17` | High | Open / Provisional |
| `OQ-CTX-003` | What verification evidence and review rules are required for each MVP bill type? | `DOC-12` / `DOC-14` / `DOC-21` | High | Open |
| `OQ-CTX-004` | Which AI bill review provider or service will be selected? | `DOC-12` / `DOC-16` / `DOC-17` | Medium | Open |
| `OQ-CTX-005` | What exact user segmentation model will be used for demographic, behavioral, and geographic segmentation? | `DOC-05` / `DOC-13` / `DOC-14` | Medium | Open |
| `OQ-CTX-006` | What exact payee label model will be used? | `DOC-05` / `DOC-10` / `DOC-12` / `DOC-14` | Medium | Open |
| `OQ-CTX-007` | What promotion types, limits, funding responsibilities, and reversal rules are required for MVP? | `DOC-02` / `DOC-13` / `DOC-11` | High | Open |
| `OQ-CTX-008` | What partner advertisement placement rules, approval flows, and reporting requirements are required? | `DOC-13` / `DOC-07` / `DOC-15` | Medium | Open |
| `OQ-CTX-009` | What regulatory assumptions are currently available for Hong Kong MVP? | `DOC-03` / `DOC-04` | High | Open |
| `OQ-CTX-010` | What compliance certification goals are required before production launch versus after launch? | `DOC-04` / `DOC-19` | Medium | Open / Requires Validation |
| `OQ-CTX-011` | What operational review model is expected for bill verification and payee verification? | `DOC-12` / `DOC-21` | High | Open |
| `OQ-CTX-012` | What risk controls are required for domestic helper salary, personal payees, high-value renovation, and entertainment/subscription categories? | `DOC-12` / `DOC-14` / `DOC-21` | High | Open |
| `OQ-CTX-013` | What business model, pricing, fee, and unit economics assumptions are required for MVP? | `DOC-02` | High | Open |
| `OQ-CTX-014` | Who is the official owner of `DOC-01`, and who are its required approvers? | `DOC-01` / `DOC-00` | High | Provisional |

---

## 14. Recommended Next Step

The recommended next document is:

```text
docs/00-foundation/doc-02-business-model-unit-economics-commercial-model.md
```

Document ID:

```text
DOC-02
```

Title:

```text
Business Model, Unit Economics & Commercial Model
```

Recommended status:

```text
Draft
```

Reason:

`DOC-01` has established the product identity, product boundaries, MVP launch geography, MVP bill types, and high-level capability scope.

The next logical foundation document is `DOC-02`, which should define the commercial foundation before detailed PRD, PSP assessment, settlement design, promotion mechanics, and risk controls are finalized.

`DOC-02` should capture:

- Business model assumptions.
- Revenue model.
- Fee model.
- Cost model.
- Unit economics.
- Margin considerations.
- Payment-method cost assumptions.
- Bill-category economics.
- Payout and banking cost assumptions.
- Promotion subsidy ownership.
- Partner advertisement revenue or partnership-value assumptions.
- Refund, chargeback, and dispute cost treatment.
- Commercial constraints.
- Financial KPIs.
- Sensitivity areas.
- Dependencies on PSP/acquirer pricing and settlement terms.

`DOC-02` should not define:

- Detailed promotion campaign rules.
- Detailed promotion stacking logic.
- Exact PSP integration design.
- Detailed payment state machines.
- Database schemas.
- API endpoints.
- Legal conclusions.
- Final accounting policy.
- Fraud thresholds.
- Operational SOPs.

Those items belong in later dedicated documents.

---

## 15. Suggested DOC-02 Structure

Suggested structure for `DOC-02`:

1. Purpose
2. Document Scope
3. Business Model Overview
4. Commercial Positioning
5. Revenue Streams
6. Fee Model Principles
7. Payment Method Cost Model
8. Bill Category Commercial Model
9. Payout and Settlement Cost Considerations
10. Promotion Subsidy and Campaign Economics
11. Partner Advertisement and Partnership Commercial Model
12. Refund, Cancellation, Chargeback, and Dispute Cost Treatment
13. Unit Economics Framework
14. Margin and Profitability Considerations
15. Financial KPI Framework
16. Pricing Governance and Change Control
17. Commercial Assumptions
18. Constraints
19. Dependencies
20. Stakeholders and RACI
21. Key Risks
22. Acceptance Criteria
23. Open Questions
24. Document Changelog

`DOC-02` should be the formal place to preserve PayPlus business model and unit economics assumptions.

This context file should support `DOC-02` creation but should not replace it.

---

## 16. Instructions for Future AI Sessions

When continuing this project, future AI should:

- Read this context file first.
- Read `DOC-00` before creating or revising formal documents.
- Read `DOC-01` before creating `DOC-02` or later formal documents.
- Treat approved `DOC-XX` files as source of truth.
- Treat draft `DOC-XX` files as stronger working references than chat history, while recognizing they are not final approved source-of-truth documents.
- Use the current document register unless governance is formally revised.
- Preserve the original PayPlus rationale from this context.
- Keep explanations outside copy/paste document boxes.
- Put actual document content inside a single Markdown copy/paste box.
- Avoid mixing rationale with document content unless the document section calls for rationale.
- Maintain the document numbering system from `DOC-00`.
- Maintain requirement, rule, and test case ID conventions from `DOC-00`.
- Ask clarifying questions only when needed.
- Prefer structured Markdown.
- Keep each document focused on its assigned scope.
- Avoid adding product behavior to governance documents.
- Avoid adding implementation detail to framework-level or positioning documents.
- Flag assumptions clearly.
- Do not include secrets, credentials, tokens, or real customer data.
- Preserve the Payment & Bill Settlement Platform positioning unless changed by approved documentation.
- Avoid wallet/stored-value/P2P language unless discussing boundaries.
- Place thresholds, vendor choices, API endpoints, and database schemas in later detailed documents, not in foundation documents.
- Do not use web research unless explicitly requested or needed for current factual/legal/regulatory/vendor information.
- When producing a formal document, output the whole Markdown file again.

---

## 17. Current State Summary

Current state:

```text
DOC-00 is created and refined as Draft.
DOC-01 is created and updated to version 0.2.0 as Draft.
Project continuation context is updated to version 0.5.0.
The context now preserves original PayPlus product rationale, framework reasoning,
DOC-01 decisions, and the next recommended step.
```

Recommended next action:

```text
Create DOC-02 — Business Model, Unit Economics & Commercial Model.
```

---

## 18. Context Changelog

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial AI continuation context created |
| `0.2.0` | `2026-05-14` | Initial Author | Updated after `DOC-00` creation and refinement |
| `0.3.0` | `2026-05-14` | Initial Author | Added PayPlus product rationale, intended characteristics, core functions, and strategic boundaries |
| `0.4.0` | `2026-05-14` | Initial Author | Incorporated earlier PayPlus v3.1 framework rationale, preserved original functionality reasoning, mapped earlier structure to current document register, and clarified next step |
| `0.5.0` | `2026-05-14` | Product Documentation Team | Updated after `DOC-01` creation and refinement; captured Hong Kong MVP scope, MVP bill types, payment methods, tokenization, AI bill review, multi-funding, partial/combined payment, promotions, partner ads, payout candidates, open questions, and next recommended step `DOC-02` |
