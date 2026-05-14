---
document_id: DOC-01
title: Project Charter & Product Positioning
version: 0.2.0
status: Draft
last_updated: 2026-05-14
classification: Internal
owner: Product Owner
reviewers:
  - Project Owner
  - Product Owner
  - Project Manager
  - Legal / Compliance
  - Payments Lead
  - Finance
  - Engineering Lead
  - Operations Lead
  - Risk Lead
  - Marketing Lead
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
- What bill types are included in MVP scope.
- What payment methods are intended for MVP.
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
- MVP bill types.
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

- Tuition fees.
- School fees.
- Tutorial centre fees.
- Property management fees.
- Renovation fees.
- Broadband internet fees.
- Mobile phone fees.
- Domestic helper salary obligations.
- Toll fees.
- Parking fees.
- Private doctor consultation fees.
- Clubhouse or leisure fees.
- Entertainment or subscription fees.
- Law or legal opinion fees.
- Other eligible payment obligations approved by PayPlus in future.

The original rationale is that PayPlus should help users fund and settle legitimate payment obligations through a controlled platform that supports:

- Bill or invoice submission.
- Payment purpose verification.
- Payee validation.
- Supported funding methods.
- Multi-funding-source payment.
- Partial payment tracking.
- Combined payment handling.
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

For MVP, PayPlus is a **Hong Kong-first bill-backed payment facilitation product** for selected verified bills and approved bill-like payment obligations.

---

## 6. Product Positioning Statement

PayPlus is a **Payment & Bill Settlement Platform** that allows users to submit eligible bills or payment obligations, fund those payment requests using supported funding methods, and have PayPlus facilitate settlement to approved payees, billers, merchants, or recipients, subject to verification, risk control, compliance review, and operational rules.

For MVP, PayPlus supports a defined list of Hong Kong bill-backed and approved bill-like payment categories across education, property/building, renovation, telecom, domestic employment, mobility, healthcare, leisure/subscription, and professional service use cases.

---

## 7. What PayPlus Is

PayPlus is intended to be:

| Area | Positioning |
|---|---|
| Product type | Payment & Bill Settlement Platform |
| Core purpose | Help users settle eligible bills or payment obligations |
| Launch geography | Hong Kong for MVP |
| Payment model | User funds a payment request using supported funding methods |
| MVP funding methods | Credit card, AlipayHK, and FPS, subject to PSP/acquirer and banking feasibility |
| Verification model | Bill, document, payee, and payment purpose should be verified according to risk-based rules |
| Settlement model | PayPlus facilitates settlement or payout to eligible recipients |
| Funding model | Supports one or more funding sources per parent payment request |
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

Domestic helper salary is included in MVP only as an approved bill-like payment obligation category. It must not become an unrestricted peer-to-peer transfer, payroll, cash-out, stored-value, or remittance flow.

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

Every payment request must be backed by a valid bill, invoice, fee note, statement, employment/payment record, or other approved bill-like payment obligation. A user should not be able to initiate a payment unless the payment is linked to a valid payment obligation record, payee record, and verification workflow.

Domestic helper salary must be supported only where there is valid evidence of the payment obligation. It must not be treated as an open money transfer to an individual.

Entertainment and subscription fees must be supported only where they are structured as approved bill-backed or subscription payment obligations, not general e-commerce purchases.

Law and legal opinion fees must be supported only where there is a valid invoice, fee note, engagement reference, or approved professional service payment obligation.

---

## 10. Problem Statement

Users may face difficulty paying eligible bills or payment obligations because:

- The biller or payee may not accept the user's preferred payment method.
- The user may wish to use multiple funding sources.
- The user may wish to combine different funding methods or different cards for one payment obligation.
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
| Parents or students | Users paying school, tuition, tutorial centre, or education-related invoices |
| Property residents | Users paying management fees, parking fees, clubhouse fees, or property-related bills |
| Homeowners or tenants arranging renovation | Users paying renovation invoices or milestone payment requests |
| Telecom customers | Users paying broadband internet or mobile phone bills |
| Employers of domestic helpers | Users paying domestic helper salary obligations, subject to approved controls |
| Drivers or commuters | Users paying toll fees or parking fees |
| Patients or healthcare consumers | Users paying private doctor consultation fees |
| Leisure or subscription users | Users paying eligible clubhouse, leisure, entertainment, or subscription obligations |
| Legal or professional service clients | Users paying law firm, legal opinion, or professional service fee notes |
| Other approved users | Users with other supported payment obligations approved in future |

The exact MVP user segmentation definitions are not finalized.

MVP must support segmentation capability for:

- Demographic segmentation.
- Behavioral segmentation.
- Geographic segmentation.

These segmentation capabilities should support future analytics, CRM, promotion targeting, risk review, and partner advertisement placement.

---

## 12. Target Payees and Recipients

Potential payees or recipients may include:

- Schools, universities, tutorial centres, and education providers.
- Property management companies.
- Owners' corporations.
- Car park operators.
- Clubhouse or leisure facility operators.
- Renovation companies, contractors, or approved home service providers.
- Broadband internet providers.
- Mobile network operators.
- Domestic helpers or approved domestic employment-related recipients, subject to controls.
- Toll operators.
- Private doctors, clinics, or medical service providers.
- Entertainment or subscription service providers.
- Law firms, lawyers, or legal service providers.
- Other approved billers or payment recipients.

The MVP supports both institutional and personal payees, subject to bill validation, payee verification, payout feasibility, and risk controls.

Personal payees may require stricter verification, fraud controls, payout controls, and compliance review than institutional payees.

The exact supported payee handling rules must be defined through:

- `DOC-03` Regulatory, PSP & Acquirer Assessment.
- `DOC-05` Master PRD & Feature Requirements.
- `DOC-12` Bill Category, Document AI/OCR & Payee Verification.
- `DOC-14` AML, Anti-Cashout, Fraud & Risk Controls.
- `DOC-21` Monitoring, Incident Response & Operations Runbook.

---

## 13. Target Bill Categories and MVP Bill Types

The MVP supports a defined list of approved bill-backed or approved bill-like payment categories for Hong Kong.

| No. | Bill Type | MVP Status | Notes / Boundary |
|---:|---|---|---|
| 1 | Tuition fees | Included | Education-related payment obligation |
| 2 | School fees | Included | School or education-provider payment obligation |
| 3 | Management fees | Included | Property/building management-related fees |
| 4 | Renovation fees | Included | Requires invoice, quotation, milestone bill, signed work order, or approved payment evidence |
| 5 | Broadband internet fees | Included | Telecom / internet service bills |
| 6 | Mobile phone fees | Included | Telecom / mobile service bills |
| 7 | Domestic helper salary | Included with controls | Must be supported by employment/payment record or approved bill-like obligation; not a general transfer, payroll, cashout, or remittance flow |
| 8 | Toll fees | Included | Mobility/transport-related fees |
| 9 | Parking fees | Included | Parking operator, property, or facility-related payment obligation |
| 10 | Tutorial centre fees | Included | Education / tutorial service provider fees |
| 11 | Private doctor consultation fees | Included | Healthcare service fee; may require invoice, receipt, clinic bill, or payment notice |
| 12 | Clubhouse / leisure fees | Included | Clubhouse, membership, leisure, or facility-related payment obligation |
| 13 | Entertainment / subscription fees | Included | Approved subscription or entertainment service bills; not general e-commerce purchases |
| 14 | Law / legal opinion fees | Included | Legal/professional service fee supported by invoice, fee note, or engagement reference |

Any bill type not listed above is excluded from MVP unless separately approved through change control.

The MVP should support category labels, bill-type configuration, verification rules, and payee rules so that additional bill types can be added in future without major architecture redesign.

### 13.1 MVP Bill Type Groups

For product, reporting, risk, and operations purposes, the MVP bill types may be grouped as follows:

| Group | Included Bill Types |
|---|---|
| Education | Tuition fees, school fees, tutorial centre fees |
| Property / Building | Management fees, parking fees, clubhouse/leisure fees |
| Renovation / Home Services | Renovation fees |
| Telecom | Broadband internet fees, mobile phone fees |
| Domestic Employment | Domestic helper salary |
| Mobility / Transport | Toll fees, parking fees |
| Healthcare | Private doctor consultation fees |
| Leisure / Subscription | Clubhouse/leisure fees, entertainment/subscription fees |
| Professional Services | Law/legal opinion fees |

These groupings are for product management, analytics, operations, and risk handling. The controlling MVP scope remains the approved bill type list above.

Parking may appear under both Property / Building and Mobility / Transport depending on use case and payee type.

---

## 14. Target Market and Launch Geography

The MVP launch geography is:

```text
Hong Kong only
```

Future expansion candidates include:

- Taiwan.
- Japan.
- Thailand.
- Mainland China.
- Malaysia.

These future markets are not included in MVP scope.

The target market must be validated through:

- Product strategy.
- Legal and regulatory review.
- PSP and acquirer feasibility.
- Payment method availability.
- Supported currency.
- Supported bill categories.
- Payee settlement feasibility.
- Operational support capacity.

For MVP, regulatory, payment method, payout, and compliance assumptions should be assessed for Hong Kong first.

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

This distinction is important because PayPlus must support:

- Multi-funding-source payment.
- Combined payment.
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
- User segmentation labels or attributes, where required for analytics, risk, promotion, or partner advertisement targeting.

### 18.2 Payment Request Capability

- Create payment request.
- Select bill category.
- Enter payment amount.
- Enter or select payee.
- Upload supporting document.
- View payment request status.
- Cancel or amend where permitted.

### 18.3 Bill and Document Verification Capability

Bill verification workflow is an MVP requirement.

The MVP must include a workflow to validate that a payment request is backed by a valid bill, invoice, statement, fee note, receipt, employment/payment record, or approved bill-like payment obligation.

AI-assisted bill review is also an MVP requirement. The specific AI provider or AI service has not yet been selected. The architecture must preserve an integration boundary/API for AI bill review.

The bill verification workflow should support category-specific validation because different bill types may require different evidence.

| Bill Type | Possible Verification Evidence |
|---|---|
| Tuition / school / tutorial centre fees | School bill, tuition invoice, payment notice, student account statement |
| Management / parking / clubhouse fees | Property management notice, car park invoice, membership/facility bill |
| Renovation fees | Contractor invoice, quotation, milestone payment request, signed work order |
| Broadband / mobile phone fees | Telecom bill, service statement, account notice |
| Domestic helper salary | Employment contract reference, salary payment record, approved payroll/payment evidence |
| Toll fees | Toll statement, account bill, operator notice |
| Private doctor consultation fees | Clinic invoice, consultation bill, receipt, or payment notice |
| Entertainment / subscription fees | Subscription invoice, service statement, renewal notice |
| Law / legal opinion fees | Legal fee note, invoice, engagement letter reference |

The bill verification workflow should support:

- Bill upload or bill data submission.
- Document upload.
- Document classification.
- OCR or document AI extraction.
- Field extraction.
- Bill category validation.
- Bill type classification.
- Amount validation.
- Due date validation.
- Payee matching.
- Duplicate document detection.
- Confidence scoring.
- AI-assisted review.
- Human review routing.
- Reviewer override.
- Audit trail.
- Rejection or resubmission handling.
- Verification status tracking.

Exact operational rules, SLA, approval thresholds, fraud signals, acceptable evidence, and manual review policies should be defined in later operations/risk documentation.

### 18.4 Payee Verification Capability

- Payee name capture.
- Payee account or reference capture.
- Payee type validation.
- Payee category labels.
- Payee supported bill type labels.
- Payee risk review.
- Approved payee handling.
- Institutional/person indicator.
- Payout method eligibility.
- Mismatch escalation.

Payees should support labels or attributes similar to user segmentation.

Recommended payee labels include:

- Payee type.
- Payee category.
- Bill types supported.
- Geography.
- Supported payout methods.
- Verification status.
- Risk status.
- Compliance status.
- Institution/person indicator.
- Settlement preference.
- Operational handling status.

### 18.5 Multi-Funding Source Capability

- One or more funding sources.
- Multiple cards or payment methods for one parent payment request.
- Child payment transactions.
- Split amount allocation.
- Combined payment.
- Partial payment tracking.
- Retry after payment failure.
- Per-child-transaction fee calculation.
- Funding completion detection.

### 18.6 Payment Method Capability

MVP intended payment methods are:

- Credit card.
- AlipayHK.
- FPS.

Credit card tokenization is an MVP requirement, subject to selected PSP/acquirer support.

Candidate future payment methods may include:

- Additional cards.
- Additional tokenized payment profiles.
- Additional alternative payment methods.
- Additional bank transfer or account-based payment methods.
- Other PSP-supported funding sources.

Exact payment method implementation must be approved in `DOC-03` and detailed in `DOC-09` and `DOC-17`.

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

Promotions and partner advertisement placements are MVP capabilities.

Promotion capability may include:

- Coupon.
- Voucher.
- Referral reward.
- Membership benefit.
- Partner campaign.
- Bank promotion.
- Fee waiver.
- Cashback or reward, if approved.
- Partner advertisement placement.
- Campaign creation.
- Campaign editing.
- Campaign removal or disabling.
- Placement management.

Promotion logic must be centralized in `DOC-13`.

Promotion and advertisement tools must include controls to avoid uncontrolled financial liability, misleading claims, or unapproved targeting.

### 18.9 Settlement and Payout Capability

- Payout readiness rules.
- Payout approval.
- Payout execution.
- One parent request to one or more child transactions.
- One payout linked to one or more funding records.
- Payout status tracking.
- Payout exception handling.

Candidate payout methods include:

- FPS.
- Online banking transfer.
- EPS, where feasible.
- Cheques.

Final payout feasibility depends on banking, PSP, payee type, compliance, and operational process.

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
- Category-specific risk rules.
- Domestic helper salary controls.
- Personal payee controls.
- High-value renovation payment controls.

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
- Credit card tokenization.
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
- Partner advertisement placement management.
- Support case handling.
- Audit log review.
- Reporting dashboard.
- Bill-type configuration.
- Payee-category configuration.
- Verification evidence configuration.
- Manual review policy configuration.

---

## 19. MVP Scope Principles

The MVP should focus on proving the controlled bill settlement model in Hong Kong.

The MVP should include enough functionality to support real payment requests safely, not merely a front-end prototype.

The MVP scope should prioritize:

- Clear product boundary.
- Approved MVP bill types.
- Hong Kong launch support.
- Credit card, AlipayHK, and FPS payment methods.
- Credit card tokenization.
- Payment request creation.
- Document upload.
- AI/OCR-assisted bill verification.
- Bill-type-specific verification rules.
- Payee verification.
- Supported funding method processing.
- Multi-funding-source support.
- Partial payment tracking.
- Combined payment handling.
- Fee calculation.
- User authorization.
- Receipt and notification.
- Payout or settlement process.
- Reconciliation baseline.
- Refund and cancellation baseline.
- Fraud and anti-cashout controls.
- Admin review.
- Audit trail.
- Promotion and partner advertisement placement support.
- Security and tokenization controls.
- Go-live monitoring and support SOPs.

The MVP must not depend solely on manual review if expected document volume would make manual review operationally unsustainable.

---

## 20. MVP Scope

The following is the MVP scope baseline.

| Capability | MVP Treatment | Status |
|---|---|---|
| Launch geography | Hong Kong only | Confirmed |
| Future expansion geography | Taiwan, Japan, Thailand, Mainland China, and Malaysia are future candidates, not MVP | Confirmed |
| User account | Basic user account and authentication | Included |
| User segmentation | Must support demographic, behavioral, and geographic segmentation capability; exact segment definitions TBD | Included / To Define |
| Payment request | Create eligible bill/payment request | Included |
| Bill category | Limited to approved MVP bill types listed in this document | Included |
| Document upload | Required for relevant categories | Included |
| OCR / AI extraction | MVP capability with human review routing | Included |
| AI bill review provider | Provider not selected; architecture/API boundary required | Open |
| Bill-type-specific verification rules | Required, but detailed rules still to be defined | Included / To Define |
| Payee verification | Required for settlement readiness | Included |
| Payee types | Institutional and personal payees, subject to controls | Included / To Define |
| Payee labels | Payee attributes/labels should be supported | Included |
| Funding method | Credit card, AlipayHK, and FPS, subject to PSP/acquirer feasibility | Included / Provisional |
| Credit card tokenization | Required, subject to selected PSP/acquirer support | Included |
| Multi-funding source | Multiple funding sources are MVP | Included |
| Partial payment | Partial payment is MVP | Included |
| Combined payment | Combined payment using same or different payment methods/cards is MVP | Included |
| Fee calculation | Required | Included |
| Promotion engine | Required for launch promotions | Included |
| Partner advertisement placement | Required for MVP | Included |
| Payout / settlement | Required | Included |
| Candidate payout methods | FPS, online banking transfer, EPS where feasible, and cheques | Provisional |
| Reconciliation | Baseline required | Included |
| Refund / cancellation | Baseline required | Included |
| Chargeback handling | Required if card payments are supported | Included |
| Risk controls | Required | Included |
| Notification / receipt | Required | Included |
| Admin portal | Required for review and operations | Included |
| Compliance evidence | Minimum evidence collection from launch | Included |
| Formal compliance certification before pre-launch | Not required for early pre-launch activities | Not Required |
| ISO / PCI planning | Should be considered for production operation | Required for Planning |

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
- General e-commerce purchases.
- General-purpose money transfer.
- Domestic helper payment without approved bill-like employment/payment evidence.
- Entertainment or subscription payment without approved bill/subscription evidence.
- Full automated approval without human review fallback.
- Multi-level referral schemes.
- Complex loyalty marketplace.
- Full ISO 27001 or SOC 2 certification completion before MVP, unless separately required.
- Non-Hong Kong launch.

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
- Support partner advertisement revenue or partnership value where approved.
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
| Category adoption | Payment volume and count by MVP bill type |
| Completion | Percentage of payment requests successfully settled |
| Funding | Child transaction success rate |
| Combined payment | Percentage of payment requests using multiple funding sources or multiple child transactions |
| Verification | Percentage of documents processed within SLA |
| Automation | Percentage of documents auto-extracted successfully |
| Review | Manual review backlog and turnaround time |
| Risk | Fraud rate, chargeback rate, suspicious transaction rate |
| Anti-cashout | Number and percentage of transactions blocked or escalated for cashout risk |
| Finance | Gross margin per payment category |
| Reconciliation | Percentage of transactions reconciled without exception |
| Support | Support tickets per payment request |
| Notification | Delivery success rate for critical notifications |
| Retention | Repeat payment request rate |
| Promotion | Promotion redemption and abuse rates |
| Partner ads | Advertisement placement impressions, clicks, conversion, or partner-defined metrics where applicable |

Exact KPI definitions and targets must be confirmed later.

---

## 24. Key Assumptions

The following assumptions are currently tracked:

| Assumption ID | Assumption | Status |
|---|---|---|
| `ASM-DOC01-001` | PayPlus will be designed as a Payment & Bill Settlement Platform, not a wallet. | Confirmed |
| `ASM-DOC01-002` | PayPlus will support only eligible bills or approved payment obligations. | Confirmed |
| `ASM-DOC01-003` | PayPlus will require bill, invoice, payee, or payment purpose evidence for relevant categories. | Confirmed |
| `ASM-DOC01-004` | PayPlus will avoid storing PAN or CVV. | Confirmed |
| `ASM-DOC01-005` | PayPlus will rely on PSP tokenization, hosted fields, SDKs, or equivalent mechanisms where cards are supported. | Confirmed |
| `ASM-DOC01-006` | PayPlus will need AI/OCR-assisted bill verification for MVP scalability. | Confirmed |
| `ASM-DOC01-007` | PayPlus will need human-in-the-loop review for lower-confidence or higher-risk cases. | Confirmed |
| `ASM-DOC01-008` | PayPlus will support multi-funding-source payment in MVP. | Confirmed |
| `ASM-DOC01-009` | PayPlus will support partial payment in MVP. | Confirmed |
| `ASM-DOC01-010` | PayPlus will support promotions and partner advertisement placements in MVP. | Confirmed |
| `ASM-DOC01-011` | PayPlus will require payout and reconciliation workflows. | Confirmed |
| `ASM-DOC01-012` | PayPlus will require baseline fraud, AML, anti-cashout, and chargeback controls. | Confirmed |
| `ASM-DOC01-013` | PayPlus will require compliance planning for PCI DSS and may require ISO 27001 or SOC 2 planning. | Confirmed for Planning |
| `ASM-DOC01-014` | Launch geography is Hong Kong only for MVP. | Confirmed |
| `ASM-DOC01-015` | Supported MVP bill types are limited to the approved MVP bill type list in this document. | Confirmed |
| `ASM-DOC01-016` | MVP payment methods are intended to include credit card, AlipayHK, and FPS, subject to PSP/acquirer and banking feasibility. | Provisional |
| `ASM-DOC01-017` | Domestic helper salary must be treated as an approved bill-like obligation, not as unrestricted payroll, P2P, cashout, or remittance. | Confirmed |
| `ASM-DOC01-018` | No formal compliance certification is required for early pre-launch activities, but ISO and PCI should be considered for production operation. | Provisional / Requires Validation |

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
| `CON-DOC01-011` | Partner advertisement placement must not create misleading, non-compliant, or unapproved marketing exposure. |
| `CON-DOC01-012` | Domestic helper salary handling must not create remittance, cashout, unrestricted P2P, or payroll product behavior. |
| `CON-DOC01-013` | Personal payees may require stricter verification and payout controls than institutional payees. |
| `CON-DOC01-014` | High-value renovation payments may require additional risk review, amount limits, or staged payment controls. |
| `CON-DOC01-015` | MVP is limited to Hong Kong; future markets require separate regulatory, PSP, payout, and operational review. |

---

## 26. Key Dependencies

| Dependency ID | Dependency | Related Documents | Status / Notes |
|---|---|---|---|
| `DEP-DOC01-001` | Legal and regulatory assessment | `DOC-03` | Required; must validate product boundary |
| `DEP-DOC01-002` | PSP and acquirer feasibility | `DOC-03` / `DOC-17` | Open; critical MVP dependency |
| `DEP-DOC01-003` | Supported payment method confirmation | `DOC-03` / `DOC-09` / `DOC-17` | Credit card, AlipayHK, and FPS intended; final feasibility pending |
| `DEP-DOC01-004` | Supported bill category confirmation | `DOC-03` / `DOC-05` / `DOC-12` | Approved MVP bill types listed in this document |
| `DEP-DOC01-005` | Payee type and payout feasibility | `DOC-03` / `DOC-10` / `DOC-12` | Institutional and personal payees, subject to controls |
| `DEP-DOC01-006` | Pricing and fee model | `DOC-02` | Required |
| `DEP-DOC01-007` | OCR / document AI approach | `DOC-12` / `DOC-16` / `DOC-17` | Provider not selected; integration boundary required |
| `DEP-DOC01-008` | Risk and anti-cashout design | `DOC-14` | Required |
| `DEP-DOC01-009` | Privacy and retention approach | `DOC-15` | Required |
| `DEP-DOC01-010` | Security and tokenization design | `DOC-19` | Required; credit card tokenization is MVP |
| `DEP-DOC01-011` | Operational review process | `DOC-21` | Required |
| `DEP-DOC01-012` | Compliance certification roadmap | `DOC-04` | No formal certification required for early pre-launch; ISO/PCI planning required for production |
| `DEP-DOC01-013` | Bill-type verification rules | `DOC-12` / `DOC-14` / `DOC-21` | To be defined for each MVP bill type |
| `DEP-DOC01-014` | Domestic helper salary compliance handling | `DOC-03` / `DOC-12` / `DOC-14` | Requires validation and controls |
| `DEP-DOC01-015` | Promotion and partner advertisement governance | `DOC-13` | Required for MVP |
| `DEP-DOC01-016` | Segmentation model | `DOC-05` / `DOC-13` / `DOC-14` | Exact definitions to be defined |

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
| Bill-type verification rules | Product / Operations / Risk | Product Owner | Compliance, Engineering, Legal | Support |
| OCR / AI approach | Engineering / Product | Product Owner | Ops, Risk, Compliance | Support |
| Payment architecture | Engineering Lead | CTO / Tech Lead | Product, PSP, Security | Ops |
| Risk controls | Risk Lead | Compliance / Risk Owner | Product, Engineering, Ops | Support |
| Domestic helper salary controls | Product / Compliance / Risk | Compliance / Risk Owner | Legal, Operations, Engineering | Support |
| Promotion and partner ads | Marketing / Product | Product Owner | Legal, Compliance, Finance, Risk | Engineering, Ops |
| Security | Security Lead | CTO / Security Owner | Engineering, Compliance | All teams |
| Operations SOP | Operations Lead | COO / Operations Owner | Product, Risk, Support, Finance | All teams |
| Compliance roadmap | Compliance Lead | Project Sponsor | Security, Legal, Engineering | All teams |

Recommended `DOC-01` owner:

```text
Product Owner
```

Recommended `DOC-01` approvers:

- Project Owner.
- Product Owner.
- Engineering Lead.
- Compliance Lead.
- Payments Lead.
- Finance Lead.
- Operations / Risk Lead.
- Marketing Lead.

Final named owners and approvers must be confirmed.

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
| `RISK-DOC01-016` | Domestic helper salary flow is perceived as payroll, P2P, remittance, or cashout | Regulatory, AML, and product boundary risk | Require approved bill-like evidence, payee controls, and compliance validation |
| `RISK-DOC01-017` | Entertainment/subscription category is used for general e-commerce purchases | Product boundary and acquirer risk | Restrict to approved subscription or entertainment service bills |
| `RISK-DOC01-018` | Renovation payments involve high-value or risky payees | Fraud, dispute, chargeback, and payout risk | Invoice validation, payee verification, amount limits, staged payments, and risk review |
| `RISK-DOC01-019` | Personal payee payout creates elevated fraud or compliance risk | Loss, complaints, regulatory exposure | Enhanced personal payee verification and payout controls |
| `RISK-DOC01-020` | Partner advertisements are misleading or non-compliant | Legal, reputational, or partner risk | Approval workflow, placement governance, and marketing compliance review |

---

## 29. Acceptance Criteria

`DOC-01` can be considered acceptable when:

- PayPlus product positioning is clearly defined.
- PayPlus product boundaries are explicitly stated.
- PayPlus is clearly distinguished from wallet, stored value, P2P, remittance, cashout, and payroll products.
- The original bill settlement rationale is preserved.
- Hong Kong MVP launch geography is stated.
- Future expansion markets are listed as non-MVP candidates.
- Target users and candidate payees are described.
- MVP bill types are listed and marked as included.
- Unsupported bill types are excluded unless separately approved.
- Domestic helper salary is described as an approved bill-like payment obligation with controls.
- High-level capabilities are described without over-defining implementation.
- Parent payment request and child transaction concepts are introduced.
- Multi-funding-source, partial payment, and combined payment are included as MVP capabilities.
- Credit card, AlipayHK, and FPS are identified as intended MVP payment methods, subject to PSP/acquirer feasibility.
- Credit card tokenization is identified as an MVP requirement, subject to selected PSP/acquirer support.
- AI/OCR-assisted bill verification is recognized as an MVP requirement.
- Promotion and partner advertisement placement are acknowledged as MVP capabilities.
- Refund, payout, reconciliation, and risk implications are acknowledged.
- Dependencies on regulatory, PSP, compliance, security, and technical work are identified.
- Assumptions and open questions are clearly listed.
- Detailed thresholds, vendor choices, API endpoints, schemas, and SOPs are not prematurely fixed.

---

## 30. Open Questions

| Question ID | Question | Owner | Priority | Status | Answer / Decision |
|---|---|---|---|---|---|
| `OQ-DOC01-001` | What is the official launch geography? | Project Owner | High | Closed | MVP launch geography is Hong Kong only. Taiwan, Japan, Thailand, Mainland China, and Malaysia are future expansion candidates but are not part of MVP. |
| `OQ-DOC01-002` | What are the MVP bill categories? | Product Owner | High | Closed | MVP bill types are tuition fees, school fees, management fees, renovation fees, broadband internet fees, mobile phone fees, domestic helper salary, toll fees, parking fees, tutorial centre fees, private doctor consultation fees, clubhouse/leisure fees, entertainment/subscription fees, and law/legal opinion fees. |
| `OQ-DOC01-003` | What user segments are included in MVP? | Product Owner | High | Answered / To Define | Exact segment definitions are not finalized. MVP must support demographic, behavioral, and geographic segmentation capability. |
| `OQ-DOC01-004` | What payee types are supported at launch? | Product / Compliance | High | Answered / To Define | MVP supports institutional and personal payees, subject to verification and risk controls. Payee labels/attributes should be supported. |
| `OQ-DOC01-005` | What payment methods are intended for MVP? | Product / Payments Lead | High | Answered / Provisional | Hong Kong MVP intended payment methods are credit card, AlipayHK, and FPS, subject to PSP/acquirer and banking feasibility. |
| `OQ-DOC01-006` | Will MVP support multiple funding sources at launch, or only preserve architecture for it? | Product / Engineering | High | Closed | Yes. Multiple funding sources are MVP. Credit card tokenization is also MVP, subject to selected PSP/acquirer support. Architecture must support this. |
| `OQ-DOC01-007` | Will MVP support partial payment at launch, or only preserve architecture for it? | Product / Engineering | High | Closed | Yes. Partial payment and combined payment are MVP. A bill may be settled through several payments using the same or different payment methods or different cards. |
| `OQ-DOC01-008` | What PSPs, acquirers, or payment partners are being considered? | Payments Lead | High | Open | No answer yet. This remains a business decision. PSP/acquirer selection is a critical MVP dependency. |
| `OQ-DOC01-009` | What payout methods are feasible for supported payees? | Payments Lead / Finance | High | Answered / Provisional | Candidate payout methods include FPS, online banking transfer, EPS where feasible, and cheques. Final feasibility depends on banking/PSP/payee type. |
| `OQ-DOC01-010` | Are launch promotions required for MVP? | Product / Marketing | Medium | Closed | Yes. Promotions and partner ads are MVP. UI must support placements, and backend/admin must support create, edit, remove/disable, and placement management. |
| `OQ-DOC01-011` | What minimum bill verification workflow is required for MVP? | Product / Operations / Risk | High | Answered / To Define | Bill verification workflow is MVP. AI-assisted bill review is required, but the specific AI service/provider is not selected. Architecture/API boundary must be preserved. Bill-type-specific verification rules still need to be defined. |
| `OQ-DOC01-012` | What compliance certification goals are required pre-launch versus post-launch? | Compliance Lead | Medium | Answered / Requires Validation | No formal certification is required for early pre-launch activities. ISO and PCI should be considered for production operation; exact timing and scope require legal/compliance/security confirmation. |
| `OQ-DOC01-013` | Who is the official owner of DOC-01? | Project Owner | High | Provisional | Recommended owner: Product Owner, with Project Owner as accountable sponsor until a named owner is appointed. |
| `OQ-DOC01-014` | Who are the required approvers for DOC-01? | Project Owner | High | Provisional | Recommended approvers: Project Owner, Product Owner, Engineering Lead, Compliance Lead, Payments Lead, Finance Lead, Operations/Risk Lead, and Marketing Lead. |
| `OQ-DOC01-015` | What verification evidence and review rules are required for each MVP bill type? | Product / Operations / Risk / Compliance | High | Open | Each approved MVP bill type needs acceptable evidence, validation rules, risk rules, and manual review rules. |
| `OQ-DOC01-016` | Which AI bill review provider or service will be selected? | Product / Engineering | Medium | Open | Provider has not been selected. Architecture should preserve an integration boundary. |
| `OQ-DOC01-017` | What exact PSP/acquirer will support credit card, AlipayHK, FPS, and tokenization? | Payments Lead | High | Open | PSP/acquirer selection remains open and is a critical dependency. |

---

## 31. Document Changelog

| Version | Date | Author | Change Summary |
|---|---|---|---|
| `0.1.0` | `2026-05-14` | Initial Author | Initial draft of DOC-01 Project Charter & Product Positioning |
| `0.2.0` | `2026-05-14` | Product Documentation Team | Incorporated stakeholder answers and corrected MVP bill type scope to include the full approved multi-category MVP bill type list; confirmed Hong Kong MVP scope, payment methods, partial/combined payment, multiple funding sources, credit card tokenization, promotions, partner ads, bill verification, AI review requirement, payout candidates, and regulatory product boundary |
