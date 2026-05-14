---
document_id: DOC-01
title: Project Charter & Product Positioning
version: 0.1.0
status: Draft
last_updated: 2026-05-14
classification: Internal
owner: TBD
reviewers:
  - Product Owner
  - Project Manager
  - Legal / Compliance
  - Finance
  - Engineering Lead
  - Operations Lead
  - Risk Lead
related_documents:
  - DOC-00 Documentation Governance
  - DOC-02 Business Model, Unit Economics & Commercial Model
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap
  - DOC-05 Master PRD & Feature Requirements
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification
  - DOC-13 Promotion Engine & Campaign Rules
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-19 Security, Tokenization & Access Control
---

# DOC-01 — Project Charter & Product Positioning

## 1. Purpose

This document defines the foundational product charter and positioning for PayPlus.

It establishes:

- What PayPlus is.
- What problem PayPlus intends to solve.
- Who PayPlus is intended to serve.
- What product boundaries must be preserved.
- What PayPlus must not become without further approval.
- What capabilities are expected at a high level.
- What assumptions, dependencies, constraints, and risks must be tracked before detailed product design begins.

This document should guide all later PayPlus documentation, including product requirements, payment domain design, bill verification, risk controls, regulatory assessment, technical architecture, security, testing, and operational SOPs.

---

## 2. Document Scope

This document covers:

- PayPlus product vision.
- Product rationale.
- Business and user problem.
- High-level product model.
- Target users.
- Target payees and bill categories.
- Market and launch assumptions.
- High-level capabilities.
- MVP positioning.
- Product boundaries.
- Non-goals.
- Success metrics.
- Assumptions.
- Constraints.
- Dependencies.
- Stakeholder responsibilities.
- Key risks and open questions.

This document does not define:

- Detailed functional requirements.
- Detailed payment state machines.
- Detailed OCR rules or confidence thresholds.
- Exact PSP or acquirer selection.
- Exact API endpoints.
- Database schema.
- Pricing tables.
- Promotion stacking rules.
- Fraud scoring thresholds.
- Legal conclusions.
- Full compliance control mappings.
- Operational SOPs.

Those items must be defined in later dedicated documents.

---

## 3. Background and Original Rationale

PayPlus is intended to address a practical payment problem:

Users often need to settle real bills or payment obligations, but the available payment options may be fragmented, inconvenient, costly, or limited by payment method acceptance.

Examples may include:

- Rent or tenancy-related payments.
- School or education invoices.
- Utility bills.
- Property management fees.
- Parking fees.
- Insurance invoices.
- Merchant or service invoices.
- Other eligible payment obligations approved by PayPlus.

The original rationale is that PayPlus should help users fund and settle legitimate payment obligations through a controlled platform that supports:

- Bill or invoice submission.
- Payment purpose verification.
- Payee validation.
- Supported funding methods.
- Multi-funding-source payment.
- Partial payment tracking.
- Settlement or payout to eligible recipients.
- Reconciliation.
- Receipt and communication.
- Refund, cancellation, and dispute handling.
- Risk, fraud, anti-cashout, and compliance controls.

PayPlus is therefore not merely a checkout feature.

It is a payment and bill settlement platform with product, financial, operational, regulatory, security, and compliance implications.

---

## 4. Product Vision

The product vision for PayPlus is:

```text
To provide a trusted, compliant, and user-friendly platform for settling eligible
bills and payment obligations using supported funding methods, while maintaining
clear verification, settlement, reconciliation, risk control, and communication.
```

PayPlus should make it easier for users to pay legitimate obligations while giving the business sufficient control over:

- What is being paid.
- Who receives the settlement.
- How payment is funded.
- Whether the transaction is eligible.
- Whether the transaction creates unacceptable regulatory, fraud, chargeback, or cashout risk.
- How each payment is tracked, reconciled, and supported.

---

## 5. Product Positioning

PayPlus should be positioned as a:

- Payment & Bill Settlement Platform.
- Bill and invoice payment facilitation platform.
- Eligible payment obligation settlement platform.
- Multi-funding-source payment platform.
- Verification-aware payment platform.
- Reconciliation-aware settlement platform.
- Compliance-conscious financial technology product.

PayPlus should help users initiate payment requests for eligible obligations and fund those requests using supported payment methods.

PayPlus should facilitate payment processing, verification, settlement, payout, reconciliation, and related communication according to approved business, regulatory, risk, and operational rules.

---

## 6. Product Positioning Statement

PayPlus is a **Payment & Bill Settlement Platform** that allows users to submit eligible bills or payment obligations, fund those payment requests using supported funding methods, and have PayPlus facilitate settlement to approved payees, billers, merchants, or recipients, subject to verification, risk control, compliance review, and operational rules.

---

## 7. What PayPlus Is

PayPlus is intended to be:

| Area | Positioning |
|---|---|
| Product type | Payment & Bill Settlement Platform |
| Core purpose | Help users settle eligible bills or payment obligations |
| Payment model | User funds a payment request using supported funding methods |
| Verification model | Bill, document, payee, and payment purpose should be verified according to risk-based rules |
| Settlement model | PayPlus facilitates settlement or payout to eligible recipients |
| Funding model | May support one or more funding sources per parent payment request |
| Tracking model | Payment progress, funding progress, settlement progress, and reconciliation should be tracked |
| Risk model | Transactions should be subject to AML, fraud, anti-cashout, document, payee, and payment method controls |
| Compliance model | Product design should consider PSP, acquirer, payment method, privacy, PCI, ISO 27001, SOC 2, and related expectations where applicable |

---

## 8. What PayPlus Is Not

Unless later approved through regulatory, legal, business, and technical review, PayPlus must not be positioned or designed as:

- A general-purpose wallet.
- A stored value facility.
- An unrestricted peer-to-peer transfer product.
- A remittance product.
- A cashout service.
- A general money transmission product.
- An anonymous payment tool.
- A crypto product.
- A bank account substitute.
- A lending product.
- A deposit-taking product.
- A marketplace escrow product.
- A payroll product.

PayPlus must not support transactions that have no legitimate bill, invoice, payee, merchant, biller, or approved payment obligation.

---

## 9. Core Product Boundary

The core product boundary is:

```text
PayPlus should only support payment requests that are linked to a real bill,
invoice, eligible payee, merchant, biller, or approved payment obligation.
```

This boundary is important because PayPlus should avoid becoming:

- A cashout tool.
- An unrestricted P2P transfer system.
- A stored-value balance product.
- A high-risk money movement product.
- A product that creates unapproved regulatory exposure.

This boundary must be reflected in:

- Product requirements.
- User journey.
- Content and disclosures.
- Bill verification.
- Payee verification.
- PSP and acquirer assessment.
- Risk controls.
- AML and anti-cashout rules.
- Refund and chargeback handling.
- Operations SOPs.

---

## 10. Problem Statement

Users may face difficulty paying eligible bills or payment obligations because:

- The biller or payee may not accept the user's preferred payment method.
- The user may wish to use multiple funding sources.
- The bill amount may need to be funded in parts.
- Payment status may be unclear.
- Proof of payment may be fragmented.
- Settlement timing may be uncertain.
- Refund or cancellation handling may be unclear.
- Available payment options may lack user-friendly tracking.
- Bill verification and payee validation may be manual or inconsistent.

PayPlus aims to solve these problems by providing a structured payment request, funding, verification, settlement, and tracking experience.

---

## 11. Target Users

Potential PayPlus users may include:

| User Segment | Description |
|---|---|
| Individual bill payers | Users who need to pay eligible bills or invoices |
| Tenants | Users paying rent or tenancy-related obligations |
| Parents or students | Users paying school or education-related invoices |
| Property residents | Users paying management fees, parking fees, or property-related bills |
| Policyholders | Users paying insurance invoices or premiums, subject to approved scope |
| Small business users | Users paying eligible business invoices, if included in scope |
| Other approved users | Users with other supported payment obligations |

The exact MVP user segments must be confirmed in later documents.

---

## 12. Target Payees and Recipients

Potential payees or recipients may include:

- Landlords.
- Property management companies.
- Schools or education providers.
- Utility providers.
- Insurance providers.
- Parking operators.
- Merchants.
- Service providers.
- Other approved billers or payment recipients.

The exact supported payee types must be defined through:

- `DOC-03` Regulatory, PSP & Acquirer Assessment.
- `DOC-05` Master PRD & Feature Requirements.
- `DOC-12` Bill Category, Document AI/OCR & Payee Verification.
- `DOC-14` AML, Anti-Cashout, Fraud & Risk Controls.
- `DOC-21` Monitoring, Incident Response & Operations Runbook.

---

## 13. Target Bill Categories

Candidate bill categories may include:

| Category | Candidate Examples | MVP Status |
|---|---|---|
| Rent / tenancy | Rent, tenancy invoice, landlord payment request | TBD |
| Education | School fee, tuition invoice, course invoice | TBD |
| Utilities | Electricity, water, gas, telecom bills | TBD |
| Property management | Management fee, building fee, estate fee | TBD |
| Parking | Monthly parking fee, parking invoice | TBD |
| Insurance | Insurance premium invoice | TBD |
| Merchant / service invoice | Approved invoice from eligible merchant or service provider | TBD |
| Other approved categories | To be reviewed case by case | TBD |

The MVP supported categories must be confirmed before detailed PRD completion.

---

## 14. Target Market and Launch Geography

The launch geography is currently:

```text
TBD
```

The target market must be confirmed through:

- Product strategy.
- Legal and regulatory review.
- PSP and acquirer feasibility.
- Payment method availability.
- Supported currency.
- Supported bill categories.
- Payee settlement feasibility.
- Operational support capacity.

Until launch geography is confirmed, regulatory, payment method, and compliance assumptions must be treated as preliminary.

---

## 15. High-Level Product Model

At a high level, PayPlus may follow this product model:

```text
1. User creates a payment request.
2. User selects or enters the bill category.
3. User uploads or provides bill, invoice, or payment obligation evidence.
4. PayPlus performs document, bill, payee, and risk verification.
5. User selects one or more supported funding methods.
6. PayPlus calculates principal amount, fees, discounts, and payable amount.
7. User authorizes payment.
8. PayPlus processes one or more child payment transactions.
9. PayPlus tracks funding progress.
10. Once readiness conditions are satisfied, PayPlus initiates or records payout / settlement.
11. PayPlus reconciles funding, fees, promotions, payouts, refunds, and exceptions.
12. PayPlus provides status updates, receipts, and support handling.
```

This model is high-level only.

Detailed state models must be defined in later payment and data model documents.

---

## 16. Parent Payment Request and Child Transaction Concept

PayPlus should preserve the distinction between:

| Concept | Meaning |
|---|---|
| Parent Payment Request | The overall bill or payment obligation that the user wants to settle |
| Child Payment Transaction | One funding transaction used to fund part or all of the parent payment request |

This distinction is important because PayPlus may support:

- Multi-funding-source payment.
- Partial payment.
- Payment retry.
- Child-level payment failure.
- Child-level fees.
- Parent-level funding progress.
- Parent-level promotion redemption.
- Parent-level settlement readiness.
- Parent-level refund and dispute handling.

Detailed rules must be defined in `DOC-09`, `DOC-11`, `DOC-13`, and `DOC-18`.

---

## 17. Payment Language Principle

PayPlus should use language that accurately describes payment progress without implying stored value.

Preferred terms include:

- `Payment Progress`
- `Funding Progress`
- `Remaining Amount`
- `Amount Paid`
- `Amount Pending`
- `Settlement Status`
- `Payout Status`

Terms to avoid unless formally approved:

- `Wallet Balance`
- `Stored Balance`
- `User Balance`
- `Top-up Balance`
- `Cash Balance`

Reason:

```text
PayPlus should not appear to maintain stored value unless that model is later
formally approved through legal, regulatory, compliance, and technical review.
```

---

## 18. High-Level Capabilities

PayPlus is expected to include or consider the following high-level capabilities.

### 18.1 User and Account Capability

- User registration or onboarding.
- User profile management.
- Identity or risk information where required.
- User authentication.
- User consent records.
- User support history.

### 18.2 Payment Request Capability

- Create payment request.
- Select bill category.
- Enter payment amount.
- Enter or select payee.
- Upload supporting document.
- View payment request status.
- Cancel or amend where permitted.

### 18.3 Bill and Document Verification Capability

- Document upload.
- Document classification.
- OCR or document AI extraction.
- Field extraction.
- Bill category validation.
- Amount validation.
- Due date validation.
- Payee matching.
- Duplicate document detection.
- Confidence scoring.
- Human review routing.
- Reviewer override.
- Audit trail.

### 18.4 Payee Verification Capability

- Payee name capture.
- Payee account or reference capture.
- Payee type validation.
- Payee risk review.
- Approved payee handling.
- Mismatch escalation.

### 18.5 Multi-Funding Source Capability

- One or more funding sources.
- Child payment transactions.
- Split amount allocation.
- Partial payment tracking.
- Retry after payment failure.
- Per-child-transaction fee calculation.
- Funding completion detection.

### 18.6 Payment Method Capability

Candidate payment methods may include:

- Cards.
- Tokenized payment profiles.
- Alternative payment methods.
- Bank transfer or account-based payment methods.
- Other PSP-supported funding sources.

Exact payment methods must be approved in `DOC-03` and detailed in `DOC-09` and `DOC-17`.

### 18.7 Pricing and Fee Capability

- Principal amount.
- Fee amount.
- Payable amount.
- Payment-method-based fee.
- Bill-category-based fee.
- Promotion subsidy.
- Refund fee treatment.
- Chargeback cost treatment.

Detailed pricing belongs in `DOC-02`.

### 18.8 Promotion Capability

- Coupon.
- Voucher.
- Referral reward.
- Membership benefit.
- Partner campaign.
- Bank promotion.
- Fee waiver.
- Cashback or reward, if approved.

Promotion logic must be centralized in `DOC-13`.

### 18.9 Settlement and Payout Capability

- Payout readiness rules.
- Payout approval.
- Payout execution.
- One parent request to one or more child transactions.
- One payout linked to one or more funding records.
- Payout status tracking.
- Payout exception handling.

### 18.10 Reconciliation Capability

- PSP settlement reconciliation.
- Fee reconciliation.
- Promotion subsidy reconciliation.
- Refund reconciliation.
- Chargeback reconciliation.
- Bank statement matching.
- Finance reporting.
- Exception handling.

### 18.11 Refund, Cancellation, and Dispute Capability

- Cancellation before payment.
- Cancellation during partial payment.
- Cancellation after full funding before payout.
- Cancellation after payout.
- Child transaction refund.
- Parent payment request refund.
- Promotion reversal.
- Referral reward reversal.
- Chargeback evidence.
- Dispute handling.
- Loss allocation.

### 18.12 Risk and Fraud Capability

- AML risk indicators.
- Anti-cashout controls.
- Fake document detection.
- Duplicate document detection.
- Payee risk controls.
- User risk tiering.
- Payment method risk.
- Velocity checks.
- Promotion abuse controls.
- Risk review queue.
- Decision audit trail.

### 18.13 Authentication and Security Capability

- User authentication.
- Login 2FA, where required.
- Transaction step-up authentication.
- Card 3DS / SCA integration, where applicable.
- Alternative payment method authentication.
- Admin authentication.
- Admin RBAC.
- Maker-checker controls.
- Tokenization.
- Encryption.
- Secure logging.
- Audit events.

### 18.14 Notification, Receipt, and Communication Capability

- Payment request confirmation.
- Document review result.
- Payment success notice.
- Child transaction failure notice.
- Partial payment reminder.
- Payout processing notice.
- Payout completed notice.
- Refund notice.
- Promotion notice.
- Chargeback or dispute notice.
- Receipt.
- Support messages.

### 18.15 Admin and Operations Capability

- Admin review queue.
- Document verification review.
- Risk review.
- Payout approval.
- Refund approval.
- Promotion campaign management.
- Support case handling.
- Audit log review.
- Reporting dashboard.

---

## 19. MVP Scope Principles

The MVP should focus on proving the controlled bill settlement model.

The MVP should include enough functionality to support real payment requests safely, not merely a front-end prototype.

The MVP scope should prioritize:

- Clear product boundary.
- Approved bill categories.
- Payment request creation.
- Document upload.
- AI/OCR-assisted bill verification.
- Payee verification.
- Supported funding method processing.
- Multi-funding-source architecture, if required for launch.
- Partial payment tracking, if required for launch.
- Fee calculation.
- User authorization.
- Receipt and notification.
- Payout or settlement process.
- Reconciliation baseline.
- Refund and cancellation baseline.
- Fraud and anti-cashout controls.
- Admin review.
- Audit trail.
- Security and tokenization controls.
- Go-live monitoring and support SOPs.

The MVP must not depend solely on manual review if expected document volume would make manual review operationally unsustainable.

---

## 20. MVP Candidate Scope

The following is a candidate MVP scope and must be confirmed later.

| Capability | Candidate MVP Treatment | Status |
|---|---|---|
| User account | Basic user account and authentication | TBD |
| Payment request | Create eligible bill/payment request | TBD |
| Bill category | Limited approved categories | TBD |
| Document upload | Required for selected categories | TBD |
| OCR / AI extraction | MVP capability with human review routing | TBD |
| Payee verification | Required for settlement readiness | TBD |
| Funding method | Limited supported payment methods | TBD |
| Multi-funding source | Architecture should support; launch behavior TBD | TBD |
| Partial payment | Architecture should support; launch behavior TBD | TBD |
| Fee calculation | Required | TBD |
| Promotion engine | Required if launch promotions exist | TBD |
| Payout / settlement | Required | TBD |
| Reconciliation | Baseline required | TBD |
| Refund / cancellation | Baseline required | TBD |
| Chargeback handling | Required if card payments are supported | TBD |
| Risk controls | Required | TBD |
| Notification / receipt | Required | TBD |
| Admin portal | Required for review and operations | TBD |
| Compliance evidence | Minimum evidence collection from launch | TBD |

---

## 21. Out of Scope for Initial MVP Unless Approved

The following should be out of scope unless explicitly approved:

- General wallet balance.
- Stored value account.
- Unrestricted P2P transfer.
- Cash withdrawal or cashout.
- Remittance.
- Crypto payment.
- Lending or installment credit.
- Payroll.
- Marketplace escrow.
- Unsupported bill categories.
- Unsupported high-risk merchants or payees.
- Full automated approval without human review fallback.
- Multi-level referral schemes.
- Complex loyalty marketplace.
- Full ISO 27001 or SOC 2 certification completion before MVP, unless separately required.

---

## 22. Business Objectives

Potential business objectives include:

- Validate demand for bill settlement through supported funding methods.
- Increase successful eligible bill payment volume.
- Create a trusted payment flow for users and payees.
- Generate sustainable fee revenue.
- Manage PSP and payment method costs.
- Reduce manual review burden through AI/OCR-assisted verification.
- Reduce payment errors and wrong-payee risk.
- Reduce fraud, chargeback, and cashout abuse.
- Support promotion-driven acquisition where financially controlled.
- Build a compliance-ready foundation for future partnerships.

Detailed financial modelling belongs in `DOC-02`.

---

## 23. Success Metrics

Candidate success metrics include:

| Metric Area | Candidate Metric |
|---|---|
| Adoption | Number of registered users |
| Activation | Number of users creating first payment request |
| Payment volume | Total approved payment request volume |
| Completion | Percentage of payment requests successfully settled |
| Funding | Child transaction success rate |
| Verification | Percentage of documents processed within SLA |
| Automation | Percentage of documents auto-extracted successfully |
| Review | Manual review backlog and turnaround time |
| Risk | Fraud rate, chargeback rate, suspicious transaction rate |
| Finance | Gross margin per payment category |
| Reconciliation | Percentage of transactions reconciled without exception |
| Support | Support tickets per payment request |
| Notification | Delivery success rate for critical notifications |
| Retention | Repeat payment request rate |
| Promotion | Promotion redemption and abuse rates |

Exact KPI definitions and targets must be confirmed later.

---

## 24. Key Assumptions

The following assumptions are currently preliminary:

| Assumption ID | Assumption | Status |
|---|---|---|
| `ASM-DOC01-001` | PayPlus will be designed as a Payment & Bill Settlement Platform, not a wallet. | Open |
| `ASM-DOC01-002` | PayPlus will support only eligible bills or payment obligations. | Open |
| `ASM-DOC01-003` | PayPlus will require bill, invoice, payee, or payment purpose evidence for relevant categories. | Open |
| `ASM-DOC01-004` | PayPlus will avoid storing PAN or CVV. | Open |
| `ASM-DOC01-005` | PayPlus will rely on PSP tokenization, hosted fields, SDKs, or equivalent mechanisms where cards are supported. | Open |
| `ASM-DOC01-006` | PayPlus will need AI/OCR-assisted bill verification for MVP scalability. | Open |
| `ASM-DOC01-007` | PayPlus will need human-in-the-loop review for lower-confidence or higher-risk cases. | Open |
| `ASM-DOC01-008` | PayPlus may support multi-funding-source payment. | Open |
| `ASM-DOC01-009` | PayPlus may support partial payment. | Open |
| `ASM-DOC01-010` | PayPlus may support promotions, coupons, vouchers, referrals, or membership benefits. | Open |
| `ASM-DOC01-011` | PayPlus will require payout and reconciliation workflows. | Open |
| `ASM-DOC01-012` | PayPlus will require baseline fraud, AML, anti-cashout, and chargeback controls. | Open |
| `ASM-DOC01-013` | PayPlus will require compliance planning for PCI DSS and may require ISO 27001 or SOC 2 planning. | Open |
| `ASM-DOC01-014` | Launch geography is not yet confirmed. | Open |
| `ASM-DOC01-015` | Supported MVP bill categories are not yet confirmed. | Open |

---

## 25. Constraints

Potential constraints include:

| Constraint ID | Constraint |
|---|---|
| `CON-DOC01-001` | Product design must avoid creating an unapproved stored-value model. |
| `CON-DOC01-002` | Product design must avoid unrestricted P2P transfer behavior. |
| `CON-DOC01-003` | Payment methods depend on PSP, acquirer, card scheme, and local regulatory approval. |
| `CON-DOC01-004` | Supported bill categories may be limited by acquirer underwriting and risk appetite. |
| `CON-DOC01-005` | Settlement timing may depend on PSP, banking, and operational processes. |
| `CON-DOC01-006` | Refund and chargeback behavior may be constrained by PSP and payment method rules. |
| `CON-DOC01-007` | AI/OCR accuracy may vary by document type, language, format, and scan quality. |
| `CON-DOC01-008` | Manual review capacity may limit transaction throughput. |
| `CON-DOC01-009` | Compliance certification maturity may take longer than MVP delivery. |
| `CON-DOC01-010` | Promotion features must not create uncontrolled financial liability. |

---

## 26. Key Dependencies

| Dependency ID | Dependency | Related Documents |
|---|---|---|
| `DEP-DOC01-001` | Legal and regulatory assessment | `DOC-03` |
| `DEP-DOC01-002` | PSP and acquirer feasibility | `DOC-03` / `DOC-17` |
| `DEP-DOC01-003` | Supported payment method confirmation | `DOC-03` / `DOC-09` / `DOC-17` |
| `DEP-DOC01-004` | Supported bill category confirmation | `DOC-03` / `DOC-05` / `DOC-12` |
| `DEP-DOC01-005` | Payee type and payout feasibility | `DOC-03` / `DOC-10` / `DOC-12` |
| `DEP-DOC01-006` | Pricing and fee model | `DOC-02` |
| `DEP-DOC01-007` | OCR / document AI approach | `DOC-12` / `DOC-16` / `DOC-17` |
| `DEP-DOC01-008` | Risk and anti-cashout design | `DOC-14` |
| `DEP-DOC01-009` | Privacy and retention approach | `DOC-15` |
| `DEP-DOC01-010` | Security and tokenization design | `DOC-19` |
| `DEP-DOC01-011` | Operational review process | `DOC-21` |
| `DEP-DOC01-012` | Compliance certification roadmap | `DOC-04` |

---

## 27. Stakeholders and RACI

The following RACI is preliminary.

| Area | Responsible | Accountable | Consulted | Informed |
|---|---|---|---|---|
| Product positioning | Product Owner | Project Sponsor | Legal, Compliance, Risk, Engineering | All teams |
| Business model | Finance / Product | Project Sponsor | PSP, Legal, Compliance | Product, Engineering, Ops |
| Regulatory assessment | Legal / Compliance | Project Sponsor | Product, PSP, Risk | All teams |
| PSP / acquirer assessment | Payments Lead | Project Sponsor | Engineering, Legal, Finance | Product, Ops |
| Product requirements | Product Manager | Product Owner | Engineering, Design, Ops, Risk | All teams |
| Bill verification | Product / Operations | Product Owner | Risk, Engineering, Compliance | Support |
| OCR / AI approach | Engineering / Product | Product Owner | Ops, Risk, Compliance | Support |
| Payment architecture | Engineering Lead | CTO / Tech Lead | Product, PSP, Security | Ops |
| Risk controls | Risk Lead | Compliance / Risk Owner | Product, Engineering, Ops | Support |
| Security | Security Lead | CTO / Security Owner | Engineering, Compliance | All teams |
| Operations SOP | Operations Lead | COO / Operations Owner | Product, Risk, Support, Finance | All teams |
| Compliance roadmap | Compliance Lead | Project Sponsor | Security, Legal, Engineering | All teams |

Final owners and approvers must be confirmed.

---

## 28. Key Risks

| Risk ID | Risk | Potential Impact | Mitigation Direction |
|---|---|---|---|
| `RISK-DOC01-001` | Product is perceived as wallet or stored value | Regulatory exposure | Maintain strict product boundary and wording |
| `RISK-DOC01-002` | Product enables cashout behavior | Fraud, AML, acquirer risk | Bill/payee verification and anti-cashout controls |
| `RISK-DOC01-003` | Unsupported bill categories are accepted | Compliance and financial risk | Category whitelist and review process |
| `RISK-DOC01-004` | Fake or altered documents are submitted | Fraud and loss | OCR, fraud signals, human review, audit trail |
| `RISK-DOC01-005` | Payee mismatch or wrong payout | Financial loss and customer harm | Payee verification and payout controls |
| `RISK-DOC01-006` | Manual review backlog grows too large | SLA failure and poor UX | AI/OCR-assisted extraction and review routing |
| `RISK-DOC01-007` | Payment succeeds but internal status fails to update | User trust and reconciliation issues | Idempotency, webhook handling, reconciliation |
| `RISK-DOC01-008` | Partial payment creates unclear status | User confusion and support load | Parent-child state model and clear communication |
| `RISK-DOC01-009` | Promotion abuse creates financial loss | Margin loss and fraud | Promotion engine controls and reversal logic |
| `RISK-DOC01-010` | Refund and chargeback rules are incomplete | Financial and support risk | Dedicated refund and chargeback specification |
| `RISK-DOC01-011` | PSP or acquirer does not support model | Launch blocker | Early PSP/acquirer assessment |
| `RISK-DOC01-012` | PCI scope expands unintentionally | Compliance burden | Tokenization and no PAN/CVV policy |
| `RISK-DOC01-013` | Privacy and document retention are mishandled | Legal and reputational risk | Privacy and retention specification |
| `RISK-DOC01-014` | Operations lacks evidence for audits | Partnership and compliance risk | Evidence ownership and compliance roadmap |
| `RISK-DOC01-015` | Notifications are incomplete or misleading | Disputes and support tickets | Dedicated notification and receipt rules |

---

## 29. Acceptance Criteria

`DOC-01` can be considered acceptable when:

- PayPlus product positioning is clearly defined.
- PayPlus product boundaries are explicitly stated.
- PayPlus is clearly distinguished from wallet, stored value, P2P, remittance, and cashout products.
- The original bill settlement rationale is preserved.
- Target users and candidate payees are described.
- Candidate bill categories are listed with MVP status marked as `TBD` where not confirmed.
- High-level capabilities are described without over-defining implementation.
- Parent payment request and child transaction concepts are introduced.
- AI/OCR-assisted bill verification is recognized as an MVP design consideration.
- Promotion, refund, payout, reconciliation, and risk implications are acknowledged.
- Dependencies on regulatory, PSP, compliance, security, and technical work are identified.
- Assumptions and open questions are clearly listed.
- Detailed thresholds, vendor choices, API endpoints, schemas, and SOPs are not prematurely fixed.

---

## 30. Open Questions

| Question ID | Question | Owner | Priority | Status |
|---|---|---|---|---|
| `OQ-DOC01-001` | What is the official launch geography? | Project Owner | High | Open |
| `OQ-DOC01-002` | What are the MVP bill categories? | Product Owner | High | Open |
| `OQ-DOC01-003` | What user segments are included in MVP? | Product Owner | High | Open |
| `OQ-DOC01-004` | What payee types are supported at launch? | Product / Compliance | High | Open |
| `OQ-DOC01-005` | What payment methods are intended for MVP? | Product / Payments Lead | High | Open |
| `OQ-DOC01-006` | Will MVP support multiple funding sources at launch, or only preserve architecture for it? | Product / Engineering | High | Open |
| `OQ-DOC01-007` | Will MVP support partial payment at launch, or only preserve architecture for it? | Product / Engineering | High | Open |
| `OQ-DOC01-008` | What PSPs, acquirers, or payment partners are being considered? | Payments Lead | High | Open |
| `OQ-DOC01-009` | What payout methods are feasible for supported payees? | Payments Lead / Finance | High | Open |
| `OQ-DOC01-010` | Are launch promotions required for MVP? | Product / Marketing | Medium | Open |
| `OQ-DOC01-011` | What minimum bill verification workflow is required for MVP? | Product / Operations / Risk | High | Open |
| `OQ-DOC01-012` | What compliance certification goals are required pre-launch versus post-launch? | Compliance Lead | Medium | Open |
| `OQ-DOC01-013` | Who is the official owner of DOC-01? | Project Owner | High | Open |
| `OQ-DOC01-014` | Who are the required approvers for DOC-01? | Project Owner | High | Open |

---

## 31. Document Changelog

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of DOC-01 Project Charter & Product Positioning |
