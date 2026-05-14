---
title: PayPlus Project Continuation Context
version: 0.4.0
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
4. The recommended next step.

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
- A product that can support users, billers, merchants, schools, property managers, insurers, and other eligible payees, subject to approved scope.

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

PayPlus is expected to support eligible categories such as:

- Rent or tenancy-related payments.
- School fees or education invoices.
- Utility bills.
- Property management fees.
- Parking fees.
- Insurance invoices.
- Other approved bill or invoice categories.

The exact supported categories must be defined in the relevant formal documents.

Framework rationale:

```text
PayPlus must know what the user is paying, why the payment is legitimate,
who should receive the payment, and whether the bill category is supported.
```

### 5.2 Multi-Funding Source and Split Payment

PayPlus should support, or be designed to support, payments using multiple funding sources.

The earlier rationale includes:

- Parent payment request.
- Child payment transactions.
- Split amount allocation.
- Partial payment.
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

Avoid:

- `Wallet Balance`
- `Stored Balance`
- `User Balance`

Reason:

```text
The product should not look or behave like a stored-value wallet.
```

### 5.3 Payment Profiles and Tokenization

PayPlus may allow users to save payment methods through tokenized payment profiles, where supported by PSPs or payment providers.

The original rationale is:

- PayPlus should avoid storing PAN or CVV.
- Card or payment credentials should be handled through PSP-hosted fields, SDKs, or tokenization.
- PayPlus should store only token references where appropriate.
- Token lifecycle and user authorization must be documented.
- PCI scope strategy must be considered early.

### 5.4 AI/OCR-Assisted Bill Verification as MVP Capability

A major earlier framework decision is that OCR / AI-assisted bill verification should be treated as an MVP capability, not a later optimization.

Reason:

If users submit large volumes of rent agreements, invoices, utility bills, school bills, management fee statements, parking bills, insurance invoices, or similar documents, fully manual review creates risks:

- Review SLA bottlenecks.
- Month-end rent payment congestion.
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

Vendor examples such as Google Document AI, AWS Textract, Azure Form Recognizer, Veryfi, Rossum, or custom models may be useful for future evaluation, but the framework should not commit to a vendor.

### 5.5 Payee Verification

PayPlus must verify or validate payee information to reduce wrong-payee, fake-payee, cashout, and fraud risks.

Relevant concepts include:

- Payee name matching.
- Biller or merchant validation.
- Invoice or account reference capture.
- Payee whitelist or approved payee handling.
- Unsupported payee detection.
- Mismatch review.
- Manual override with audit trail.

Detailed rules belong in later formal documents.

### 5.6 Promotion Engine as a Core Architecture Area

The earlier framework emphasized that promotion logic must not be scattered across business model, PRD, UX, refund, and data model documents.

If PayPlus supports coupons, vouchers, referral rewards, membership benefits, bank promotions, fee waivers, cashback, or partner campaigns, promotion logic affects:

- Checkout.
- Fee calculation.
- Parent payment request.
- Partial payment.
- Refund.
- Chargeback.
- Fraud.
- Accounting.
- Campaign analytics.
- Customer support.
- API.
- Admin portal.

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

Detailed promotion rules, stacking rules, reward timing, and API endpoints should not be defined in this context file.

### 5.7 Refund, Cancellation, Chargeback, and Promotion Reversal

Because PayPlus may support partial payment and promotions, refund and cancellation logic must account for:

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

Reason:

```text
PayPlus must be able to explain how user funding became biller/payee settlement
and how every amount, fee, subsidy, refund, and dispute was reconciled.
```

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

Detailed thresholds belong in risk rulebooks or operations policies, not the framework.

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

### 5.11 Compliance Certification Planning

The earlier framework emphasized that PCI DSS, ISO 27001, SOC 2, and related evidence planning should be considered early.

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
    │   └── doc-00-documentation-governance.md
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
| `DOC-00` | Documentation Governance | `00-foundation/` | `Draft` |
| `DOC-01` | Project Charter & Product Positioning | `00-foundation/` | `Planned` |
| `DOC-02` | Business Model, Unit Economics & Commercial Model | `00-foundation/` | `Planned` |
| `DOC-03` | Regulatory, PSP & Acquirer Assessment | `00-foundation/` | `Planned` |
| `DOC-04` | Compliance Certification Roadmap | `00-foundation/` | `Planned` |
| `DOC-05` | Master PRD & Feature Requirements | `01-product/` | `Planned` |
| `DOC-06` | User Journey, UX Flow & Service Blueprint | `01-product/` | `Planned` |
| `DOC-07` | Content, Disclosure & User Communication | `01-product/` | `Planned` |
| `DOC-08` | Notification, Receipt & Communication Rules | `01-product/` | `Planned` |
| `DOC-09` | Payment Request, Multi-Funding Source & Settlement | `02-payment-domain/` | `Planned` |
| `DOC-10` | Payout & Reconciliation | `02-payment-domain/` | `Planned` |
| `DOC-11` | Refund, Cancellation & Chargeback | `02-payment-domain/` | `Planned` |
| `DOC-12` | Bill Category, Document AI/OCR & Payee Verification | `03-bill-verification/` | `Planned` |
| `DOC-13` | Promotion Engine & Campaign Rules | `04-growth-ecosystem/` | `Planned` |
| `DOC-14` | AML, Anti-Cashout, Fraud & Risk Controls | `05-risk-compliance-privacy/` | `Planned` |
| `DOC-15` | Privacy, Data Protection & Retention | `05-risk-compliance-privacy/` | `Planned` |
| `DOC-16` | Technical Architecture | `06-engineering/` | `Planned` |
| `DOC-17` | API & Third-party Integration | `06-engineering/` | `Planned` |
| `DOC-18` | Data Model, Transaction Ledger & Reporting | `06-engineering/` | `Planned` |
| `DOC-19` | Security, Tokenization & Access Control | `07-security-access-control/` | `Planned` |
| `DOC-20` | Testing, UAT, Release & Go-Live Checklist | `08-qa-release-operations/` | `Planned` |
| `DOC-21` | Monitoring, Incident Response & Operations Runbook | `08-qa-release-operations/` | `Planned` |

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

The following document has been created:

```text
docs/00-foundation/doc-00-documentation-governance.md
```

Document details:

| Field | Value |
|---|---|
| Document ID | `DOC-00` |
| Title | Documentation Governance |
| Version | `0.1.0` |
| Status | `Draft` |
| Classification | `Internal` |
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

### 10.2 DOC-00 Refinements Already Made

`DOC-00` has been reviewed and refined.

Important refinements made:

- Section 6 now contains both:
  - `Document IDs must not be reused.`
  - `If a document is deprecated or retired, its document ID remains reserved.`
- Section 5 includes repository-structure change control guidance.
- Section 20 is named `Changelog Rules`.
- Section 23 is named `Document Changelog`.
- Formatting has been cleaned up.
- Governance content has been kept separate from PayPlus product behavior.

### 10.3 Current AI Context Update

This file has now been updated to preserve:

- The original PayPlus product rationale.
- The earlier v3.1 framework reasoning.
- The distinction between framework-level decisions and detailed implementation decisions.
- The current documentation structure.
- The current document register.
- The next recommended step.

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

---

## 12. Important Principles for Future AI Work

Future AI assistance should preserve the following principles:

1. PayPlus is a Payment & Bill Settlement Platform.
2. PayPlus is not a general wallet.
3. PayPlus is not a stored value facility unless explicitly approved later.
4. PayPlus is not an unrestricted P2P transfer product.
5. PayPlus should not support transactions without real bills, invoices, eligible payees, or approved payment obligations.
6. Multi-funding-source and partial payment logic are core PayPlus concepts.
7. Parent payment request and child payment transaction modeling should be preserved.
8. Use `Payment Progress`, `Funding Progress`, and `Remaining Amount`; avoid wallet-like terms.
9. AI/OCR-assisted bill verification is an MVP capability.
10. AI/OCR should support extraction, confidence scoring, configurable routing, human review, reviewer override, and audit trail.
11. Promotion engine logic should be centralized, not scattered.
12. Promotion redemption should generally attach to the parent payment request.
13. Refund, chargeback, and cancellation rules must account for partial payment and promotion reversal.
14. Payout and reconciliation are core to PayPlus, not back-office afterthoughts.
15. Risk, AML, anti-cashout, fraud, and dynamic authentication controls are central to product safety.
16. Notification, receipt, and communication rules deserve a dedicated document.
17. PCI DSS, ISO 27001, SOC 2, and ISMS readiness should be planned early.
18. Framework documents should avoid hardcoding thresholds, vendor choices, API endpoints, database schemas, or full policy text.
19. Detailed rules should live in detailed specs, rulebooks, ADRs, appendices, vendor evaluations, and SOPs.
20. No secrets, credentials, tokens, or real customer data should be stored in documentation.

---

## 13. Known Open Questions

`DOC-00` currently tracks the following open questions:

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC00-001` | Who is the official Documentation Owner? | Project Owner | `High` | `Open` |
| `OQ-DOC00-002` | Who are the required approvers for each document category? | Project Owner | `High` | `Open` |
| `OQ-DOC00-003` | Should approvals be handled through pull requests, signed records, tickets, or another method? | Project Owner | `Medium` | `Open` |

Additional PayPlus product open questions to carry forward into `DOC-01` and related documents:

| Question ID | Question | Suggested Target Document | Priority | Status |
|---|---|---|---|---|
| `OQ-CTX-001` | What is the initial launch geography? | `DOC-01` / `DOC-03` | `High` | `Open` |
| `OQ-CTX-002` | What bill categories are included in MVP? | `DOC-01` / `DOC-05` / `DOC-12` | `High` | `Open` |
| `OQ-CTX-003` | Which funding methods are intended for MVP? | `DOC-01` / `DOC-03` / `DOC-09` | `High` | `Open` |
| `OQ-CTX-004` | Which payee types are supported at launch? | `DOC-01` / `DOC-03` / `DOC-12` | `High` | `Open` |
| `OQ-CTX-005` | What PSP, acquirer, or payment partners are being considered? | `DOC-03` / `DOC-17` | `High` | `Open` |
| `OQ-CTX-006` | What promotions are required for MVP, if any? | `DOC-02` / `DOC-13` | `Medium` | `Open` |
| `OQ-CTX-007` | What regulatory assumptions are currently available? | `DOC-03` / `DOC-04` | `High` | `Open` |
| `OQ-CTX-008` | What compliance certification goals are required before launch versus after launch? | `DOC-04` | `Medium` | `Open` |
| `OQ-CTX-009` | What operational review model is expected for bill verification? | `DOC-12` / `DOC-21` | `High` | `Open` |

---

## 14. Recommended Next Step

The recommended next document remains:

```text
docs/00-foundation/doc-01-project-charter-product-positioning.md
```

Document ID:

```text
DOC-01
```

Title:

```text
Project Charter & Product Positioning
```

Recommended status:

```text
Draft
```

Reason:

`DOC-01` should establish the business and product foundation before detailed requirements are written.

It should capture the product identity and boundaries clearly, especially:

- PayPlus as a Payment & Bill Settlement Platform.
- The problem being solved.
- The target users and payee ecosystem.
- Supported launch geography assumptions.
- MVP bill categories.
- MVP funding method assumptions.
- High-level payment flow.
- Multi-funding-source and partial payment positioning.
- Product boundaries.
- What PayPlus is not.
- Core success metrics.
- Core risks and assumptions.
- Major dependencies.
- Stakeholder responsibilities.

`DOC-01` should not define detailed payment state machines, OCR thresholds, PSP API endpoints, promotion stacking logic, fraud thresholds, database schemas, or operational SOPs.

---

## 15. Suggested DOC-01 Structure

Suggested structure for `DOC-01`:

1. Purpose
2. Background and Original Rationale
3. Product Vision
4. Product Positioning
5. Problem Statement
6. Target Users
7. Target Payees and Bill Categories
8. Target Market and Launch Geography
9. Value Proposition
10. Product Boundaries
11. What PayPlus Is Not
12. High-Level Product Capabilities
13. MVP Scope
14. Out of Scope
15. Business Objectives
16. Success Metrics
17. Key Assumptions
18. Constraints
19. Stakeholders and RACI
20. Key Dependencies
21. Risks and Considerations
22. Acceptance Criteria
23. Open Questions
24. Document Changelog

`DOC-01` should be the formal place to preserve PayPlus product positioning.

This context file should support `DOC-01` creation but should not replace it.

---

## 16. Instructions for Future AI Sessions

When continuing this project, future AI should:

1. Read this context file first.
2. Read `DOC-00` before creating or revising formal documents.
3. Treat approved `DOC-XX` files as source of truth.
4. Use the current document register unless governance is formally revised.
5. Preserve the original PayPlus rationale from this context.
6. Keep explanations outside copy/paste document boxes.
7. Put actual document content inside a single Markdown copy/paste box.
8. Avoid mixing rationale with document content unless the document section calls for rationale.
9. Maintain the document numbering system from `DOC-00`.
10. Maintain requirement, rule, and test case ID conventions from `DOC-00`.
11. Ask clarifying questions only when needed.
12. Prefer structured Markdown.
13. Keep each document focused on its assigned scope.
14. Avoid adding product behavior to governance documents.
15. Avoid adding implementation detail to framework-level or positioning documents.
16. Flag assumptions clearly.
17. Do not include secrets, credentials, tokens, or real customer data.
18. Preserve the Payment & Bill Settlement Platform positioning unless changed by approved documentation.
19. Avoid wallet/stored-value/P2P language unless discussing boundaries.
20. Place thresholds, vendor choices, API endpoints, and database schemas in later detailed documents, not in `DOC-01`.

---

## 17. Current State Summary

Current state:

```text
DOC-00 is created and refined as Draft.
Project continuation context is updated to version 0.4.0.
The context now preserves original PayPlus product rationale and framework reasoning.
Next recommended document is DOC-01.
```

Recommended next action:

```text
Create DOC-01 — Project Charter & Product Positioning.
```

---

## 18. Context Changelog

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial AI continuation context created |
| `0.2.0` | `2026-05-14` | Initial Author | Updated after `DOC-00` creation and refinement |
| `0.3.0` | `2026-05-14` | Initial Author | Added PayPlus product rationale, intended characteristics, core functions, and strategic boundaries |
| `0.4.0` | `2026-05-14` | Initial Author | Incorporated earlier PayPlus v3.1 framework rationale, preserved original functionality reasoning, mapped earlier structure to current document register, and clarified next step |

---

## Next Step

Create:

```text
docs/00-foundation/doc-01-project-charter-product-positioning.md
```
