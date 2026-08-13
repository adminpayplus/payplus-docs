---
document_id: DOC-12
title: Bill Category, Document AI/OCR & Payee Verification Specification
version: 0.8.2
status: Founder Working Baseline
owner: Product / Risk
reviewers:
  - Product Lead
  - Engineering Lead
  - Data Lead
  - Risk Lead
  - Compliance Lead
  - Privacy Lead
  - Operations Lead
  - Payments Lead
approvers:
  - Project Owner
  - Product Lead
  - Risk Lead
  - Compliance Lead
last_updated: 2026-08-12
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-12 - Bill Category, Document AI/OCR & Payee Verification Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-12` |
| **Title** | Bill Category, Document AI/OCR & Payee Verification Specification |
| **Version** | `0.8.2` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Risk |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Data Lead<br>Risk Lead<br>Compliance Lead<br>Privacy Lead<br>Operations Lead<br>Payments Lead |
| **Approvers** | Project Owner<br>Product Lead<br>Risk Lead<br>Compliance Lead |
| **Last Updated** | `2026-08-12` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines PayPlus MVP rules for controlled Bill Category support, document AI/OCR extraction, autofill, Evidence verification, duplicate detection, Evidence-to-Payee matching, and owner-governed human-review routing.

Bill verification is a core PayPlus capability. It improves the Payer journey by reading bills, invoices, tenancy agreements, contracts, and other Evidence, then autofilling permitted Bill/Rent source facts while preserving Evidence, traceability, compliance controls, and risk review.

This document is not a final database schema, AI model design, OCR provider API specification, fraud rulebook, admin dashboard design, or legal/privacy policy.

---

## 2. Scope and Ownership

DOC-12 covers:

- accepted evidence categories;
- document AI/OCR processing flow;
- extracted, normalized, user-corrected, and verified evidence data;
- autofill and user correction rules;
- general and category-specific field sets;
- extractable versus displayable field boundaries;
- confidence scoring and mismatch handling;
- duplicate and reused evidence detection;
- red-flag and human-review routing;
- payee verification linkage;
- evidence data labels and analytics signals.

Detailed specifications belong to:

| Topic | Owning Document |
| --- | --- |
| Product Evidence requirements and MVP source rules | DOC-05 |
| User journey, UX screens, review/correction flow | DOC-06A, DOC-06C |
| User-facing evidence, privacy, and authorization wording | DOC-07 |
| Notifications and review alerts | DOC-08 |
| Payment eligibility gates and authorization | DOC-09 |
| Payout destination and payee payout readiness | DOC-10 |
| Refund, dispute, chargeback evidence packages | DOC-11 |
| Fraud, anti-cashout, duplicate evidence, collusion, and risk-routing framework | DOC-14 |
| Privacy, masking, retention, and lawful data use | DOC-15 |
| OCR/document AI provider API and integration design | DOC-17 |
| Evidence data model, document store, audit events, reporting schema | DOC-18 |
| Access control, encryption, authentication, and evidence security | DOC-19 |
| Monitoring, support, escalation, and operations runbooks | DOC-21 |
| Owner-permitted Admin workflow execution, configuration and permissions | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Product model | PayPlus is an evidence-backed, payer-authorized controlled Bill Category and separate Rent payment platform for approved obligations. |
| Bill verification | Important MVP capability for better UX, autofill, evidence quality, and risk control. |
| Evidence types | Bill, invoice, tenancy, rent demand, contract, service agreement, payment statement, and other approved evidence. |
| AI/OCR role | System should read Evidence, capture fields, classify documents, and autofill permitted Bill/Rent source facts where confidence is acceptable. |
| User correction | Users must be able to review and correct autofilled fields before submission. |
| Human review | Most evidence should be system-processed; unclear, inconsistent, duplicate, reused, sensitive, or risky cases route to human review. |
| Data asset | Extracted evidence data is an important PayPlus data asset, but it is only one component of the broader PayPlus data profile and must remain classified, purpose-linked, and governed under DOC-15 and DOC-18. |
| Configuration | Category fields, confidence thresholds, duplicate strictness, red flags, and review-routing policy remain owner-governed; DOC-22 may execute only permitted configuration/workflow. |

Unconfirmed items should remain editable assumptions or gated requirements and should not block continued documentation drafting.

---

## 4. Core Principles

| Principle | Requirement |
| --- | --- |
| Evidence-backed payment context | Evidence supports owner-governed verification of authoritative Bill/Rent source facts and intended-Payee facts. It is not the authoritative source and does not create or become a Payable Basis, Payment Obligation, Checkout, or Payment. A Payment Application, not Evidence, applies confirmed obligation value from a Payment to a Payment Obligation. The authoritative Bill/Rent source supplies payment-relevant facts through the DOC-09 Payable Basis; Checkout never executes directly against Evidence or the Bill/Rent source. |
| UX assist, not blind automation | AI/OCR may autofill fields, but users must review and correct material fields before submission. |
| Extractable does not mean displayable | Sensitive fields may be extracted and stored under controls without being shown broadly in the UI. |
| Data layer separation | Evidence document data must be labeled as document-derived data, not as the entire user profile. |
| Configurable controls | Required fields, thresholds, duplicate handling, and review rules must be configurable by category and risk level. |
| Human review for risk | Material mismatch, low confidence, duplicate/reused evidence, same-party indicators, or suspicious documents must route to review. |
| Auditability | Raw evidence, extraction, user correction, verification result, review decision, and final evidence snapshot must be traceable. |
| Privacy by design | Evidence may contain sensitive personal, business, property, tenancy, payment, and identity information; access and display must be limited. |

---

## 5. Controlled Bill Category and Evidence Model

### 5.1 Accepted Launch Bill Category Inventory

DOC-05 is the normative product owner of the accepted controlled Bill Category inventory. DOC-12 consumes that inventory for Evidence and verification planning:

| # | Accepted Bill Category |
| --- | --- |
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

Rent is a separate journey and is not a Bill Category. The list does not decide Category-specific eligibility, Evidence criteria, field sets, thresholds, detailed labels, or Directory contents. Those remain explicit owner-backed work for DOC-05, DOC-12, DOC-06C, DOC-07, DOC-14, and the applicable later owners.

### 5.2 Evidence Types

Potential Evidence types are examples only. They may support verification within an already accepted controlled Bill Category or the separate Rent journey; they do not decide eligibility, establish a Category mapping, determine Directory membership, or define Category-specific Evidence criteria.

Potential Evidence types include:

| Evidence Category | Typical Use | Notes |
| --- | --- | --- |
| Bill | Utility, telecom, internet, school, medical, service, or other approved bill. | Usually strong reference, amount, due date, and payee data. |
| Invoice | Business or service invoice. | Requires payee/business validation where applicable. |
| Tenancy agreement | Rent and property-related payment. | Contract/relationship evidence; sensitive category requiring enhanced extraction, duplicate checks, and review rules. |
| Stamp duty document or CR109 | Rent and tenancy support evidence. | May support tenancy relationship, property details, parties, or rent period where approved. |
| Rent demand or rent statement | Rent payment evidence. | May support a rent obligation or supplement full tenancy evidence where approved. |
| HKHA tenancy card, carpark invoice, or property management notice | Rent or property-related support evidence. | May be recognised as Evidence only when it supports the separate Rent journey or an already accepted controlled Bill Category. It does not establish a Carpark Category, Category mapping, eligibility, or Evidence criteria. |
| Contract or service agreement | Contractual evidence within an accepted controlled Bill Category or the separate Rent journey. | Field requirements remain owner-governed and depend on the applicable scope. |
| Payment statement | Statement showing amount due or payment schedule. | Must be linked to approved obligation and payee/payout destination where applicable. |
| Official notice | Formal fee, levy, or demand notice where category is approved. | May require institution or issuer validation. |
| Other source evidence | Supplementary document for an already accepted controlled Bill Category or separate Rent journey. | Evidence recognition does not establish eligibility; any exception requires owner-governed policy within the accepted scope. |

Unsupported or prohibited categories must follow DOC-01, DOC-03, DOC-04, DOC-05, and DOC-14.

---

## 6. Document AI/OCR Processing Flow

DOC-12 defines the following verification flow:

1. Payer creates or edits temporary Bill/Rent source capture or an established Bill/Rent source.
2. User uploads or links evidence.
3. System validates file type, file size, malware/safety checks, and required metadata where applicable.
4. System runs OCR/text extraction.
5. System classifies document type and evidence category.
6. System extracts candidate fields.
7. System assigns field-level and document-level confidence.
8. System normalizes extracted values.
9. System autofills eligible Bill/Rent source fields.
10. Payer reviews and corrects autofilled fields.
11. System compares extracted values, user-corrected values, intended Payee, Payer, source amount, Category, and relevant prior Evidence signals.
12. System applies duplicate, mismatch, same-party, and risk rules.
13. System assigns verification outcome.
14. Low-risk cases proceed to payment eligibility gates in DOC-09.
15. Red-flag cases route to the applicable owner-governed human review; DOC-22 may execute only the permitted workflow.

The UX flow belongs in DOC-06. Provider API details belong in DOC-17. Data objects and audit events belong in DOC-18.

---

## 7. Evidence Data Layer Model

Evidence verification data must be stored and labeled carefully because it is one part of the broader PayPlus data ecosystem.

DOC-12 owns the document-derived evidence data layers:

| Layer | Description |
| --- | --- |
| Raw Evidence File | Uploaded or linked original file, image, PDF, scan, or approved source. |
| OCR Text Layer | Text produced by OCR or document AI. |
| Extracted Evidence Fields | Candidate values captured from document text or layout. |
| Normalized Evidence Fields | Standardized values, such as date format, amount format, category, payee name, and address normalization. |
| User-Corrected Evidence Fields | Values changed or confirmed by user before submission. |
| Verification Signals | Match/mismatch results, confidence scores, completeness checks, and duplicate indicators. |
| Evidence Risk Flags | Document-derived risk signals that may require review. |
| Human Review Layer | Applicable owner-governed review decision, permitted workflow reason/notes, Evidence, and outcome. |
| Final Evidence Snapshot | The version of evidence and fields used for payer review and payment authorization. |
| Analytics Layer | Aggregated or permitted data used for product quality, OCR performance, risk analytics, and category insights. |

Other PayPlus data layers, such as payment behavior, spending patterns, owner-governed source and economic-Payee context, risk-derived association facts, referral/member-get-member activity, refunds, chargebacks, support behavior, and payout history, belong in DOC-18 and later analytics specifications.

Each evidence layer and material field should carry DOC-15 classification metadata in DOC-18, including data class, sensitivity, displayability, masking rule, retention policy, owner, approved purpose, access role, audit requirement, source, and lineage. Evidence-derived data is normally Evidence and Obligation Data, but some extracted fields may also support KYC/KYB, payout/payee, risk/compliance, payment, analytics, or derived-data classifications depending on use.

### 7.1 Evidence Source and Payment Handoff Boundary

Evidence handling distinguishes the authoritative Bill/Rent source, Evidence, and any applicable tenancy or relationship context. This is a conceptual verification boundary, not a parent-child model, lifecycle, schema, event sequence, or technical materialization rule.

```text
Payer -> authoritative Bill/Rent source
Evidence and any applicable tenancy/relationship context -> support owner-governed verification of source and intended-Payee facts
authoritative Bill/Rent source -> payment-relevant facts through the DOC-09 Payable Basis
DOC-09 -> owns later materialization, Payment Obligation, Checkout, Funding, Payment, and Payment Application behavior
```

Bills, invoices, fee notices, and rent demands may support owner-governed verification of source facts for a specific payment context. Tenancy agreements and similar documents may support verification of tenancy context without replacing the authoritative Bill/Rent source. Applicable tenancy or relationship context may precede individual Payment Obligations; DOC-09 owns any later Payable Basis, Payment Obligation, Checkout, and Payment lifecycle behavior.

Detailed logical and physical schema belongs in DOC-18. DOC-06C owns the user-facing evidence source selection and Bills route behavior.

---

## 8. General Extracted Field Set

Where available, document AI/OCR should attempt to extract:

| Field Group | Candidate Fields |
| --- | --- |
| Document identity | Document type, category, issue date, document/reference number, language, page count. |
| Parties | Payee/biller/landlord/service provider name, payer/customer/tenant name, agent/intermediary name where applicable. |
| Amounts | Amount due, subtotal, fees, taxes where shown, deposit where applicable, currency, outstanding balance. |
| Dates | Due date, issue date, service period, billing period, rent period, contract period. |
| Obligation details | Description, service address, property address, account number, customer number, contract number. |
| Payment details | Bank name, account name, account number, FPS identifier, payment reference, cheque instruction, other destination details where shown. |
| Contact details | Phone, email, address, agent contact, business contact where shown. |
| Verification data | Confidence score, extraction method, matched category, mismatch reason, duplicate indicator, review outcome. |

Field requirements must be configurable by category, document type, payee type, risk tier, and launch phase.

---

## 9. Bill and Invoice Field Set

For bills and invoices, PayPlus should extract and validate:

| Field | Use |
| --- | --- |
| Biller or supplier name | Payee/payout validation and payer review. |
| Customer or payer name | Source-context and Evidence validation where applicable. |
| Bill, invoice, or reference number | Duplicate detection and reconciliation. |
| Issue date | Freshness and audit. |
| Due date | User reminder, eligibility, and payout timing context. |
| Amount due | Bill/Rent source amount autofill and mismatch check. |
| Currency | Payment and settlement validation. |
| Description or service details | Category and obligation support. |
| Billing or service period | Recurring and duplicate checks. |
| Payment destination details | Payee verification and payout destination support where applicable. |
| Business or issuer identifier where shown | Business/institution validation where applicable. |

Display in UI should be limited to fields needed for Bill/Rent source capture, Payer review, and user confirmation. Sensitive or unnecessary extracted fields should be masked, hidden, or restricted according to DOC-15 and DOC-19.

---

## 10. Tenancy and Rent Field Set

Tenancy and rent evidence is sensitive and must be handled with stronger privacy, duplicate, and review controls.

Extractable tenancy/rent fields may include:

| Field Group | Extractable Fields |
| --- | --- |
| Property | Property address, unit, lease property reference where shown. |
| Landlord/payee | Landlord name, landlord ID number, landlord phone, landlord address, payout/payment details where shown. |
| Tenant/payer | Tenant name, tenant ID number, tenant phone, tenant address where shown. |
| Agent | Agent name, contact, company, license number where shown. |
| Rent terms | Rent amount, rent period, lease start date, lease end date, payment frequency, payment due day, deposit, management fee where shown. |
| Payment details | Bank name, account name, account number, FPS identifier, payment reference, cheque instruction where shown. |
| Agreement indicators | Signature/execution indicators, document date, stamp/registration indicator where shown. |

Typical UI display should be narrower than extraction. User-facing screens should usually show only:

- property address;
- rent period;
- rent amount;
- payment due day for each period;
- landlord name;
- landlord phone where appropriate;
- payment details needed for verification or user confirmation, with masking where appropriate.

Landlord ID number, tenant ID number, full landlord address, full tenant address, agent license number, and other sensitive data should not be broadly displayed unless required for an approved review, compliance, support, legal, or verification purpose.

Detailed UX display rules belong in DOC-06A, DOC-06C, and DOC-07. Privacy, masking, retention, and access-control rules belong in DOC-15 and DOC-19.

---

## 11. Contract and Service Evidence Field Set

For contracts, service agreements, and similar obligation Evidence, PayPlus should extract:

| Field | Use |
| --- | --- |
| Service provider or payee name | Evidence-to-Payee and payout-destination review where applicable. |
| Customer, employer, or payer name | Source-context validation where applicable. |
| Contract or service description | Category and obligation support. |
| Contract/reference number where shown | Duplicate detection and audit. |
| Service period | Recurrence, amount, and duplicate checks. |
| Amount payable | Bill/Rent source amount autofill and mismatch check. |
| Due date or payment schedule | Reminder and payment timing context. |
| Payment destination details | Payee verification and payout support where applicable. |
| Supporting identity/contact fields where shown | Review-only validation where required. |

This Evidence type does not itself enable a Bill Category. Exact Category-specific Evidence standards, review thresholds, privacy visibility, and configuration remain subject to the accepted DOC-05 inventory and the applicable legal, compliance, risk, product, and operations owner work.

---

## 12. Autofill and User Correction Rules

AI/OCR-extracted fields may autofill Bill/Rent source fields when owner-governed confidence and Category rules permit.

Rules:

- user must be able to review and correct autofilled fields before submission;
- system must retain original extracted value, normalized value, user-corrected value, correction timestamp, and correction source;
- material user correction should trigger revalidation;
- large variance between extracted and user-entered values should trigger warning or review;
- user corrections must not overwrite raw evidence or OCR text;
- final payer authorization should use a final evidence snapshot and final displayed payment details.

User correction is expected and should improve UX. Repeated, material, or suspicious correction patterns should become risk and analytics signals.

---

## 13. Validation and Matching Rules

The system should compare extracted, user-entered, selected, and historical data.

| Validation Area | Rule |
| --- | --- |
| Amount match | Compare extracted amount with user-entered Bill/Rent source amount. |
| Evidence-to-payee validation | Compare extracted payee/biller/landlord/supplier name with selected payee or payout destination. |
| Payer match | Compare extracted payer/customer/tenant name with payer where applicable. |
| Category match | Compare extracted document type with selected category. |
| Date validity | Check due date, issue date, service period, lease period, or contract period where applicable. |
| Payment destination | Compare extracted payment details with payee payout destination where applicable. |
| Duplicate reference | Check repeated bill/invoice/reference number. |
| Duplicate evidence | Check exact or highly similar files, text, references, amounts, parties, property address, or payment details. |
| Same-party risk | Detect payer/payee, tenant/landlord, or related-party indicators. |
| Completeness | Check mandatory fields for the category. |

Risk meaning, routing, and threshold framework belong in DOC-14. Final matching algorithms, score data, and event schema belong in DOC-18, with production thresholds controlled through approved configuration.

---

## 14. Duplicate and Reused Evidence Rules

Duplicate or reused evidence detection is required, especially for tenancy and rent.

Rules:

- exact duplicate evidence should create a duplicate alert;
- highly similar evidence should create a possible reuse alert;
- tenancy/rent duplicates should normally route to manual review;
- users should be alerted in the UI when the evidence appears to have been used before, subject to privacy and anti-tipping-off review;
- duplicate strictness must be configurable by category, document type, payee type, amount, risk tier, and launch phase;
- lower-risk business bills or business-entity fee payments may use softer handling where compliance and risk approve;
- owner-governed duplicate policy may be executed through permitted DOC-22 configuration/workflow, with audit trail.

Duplicate detection must not disclose another user's sensitive details. Risk-routing framework belongs in DOC-14. DOC-22 executes only owner-permitted configuration and review workflow; DOC-18 owns the approved representation.

---

## 15. Red Flags and Human Review Routing

The system should route evidence to human review when one or more red flags occur.

| Red Flag | Example |
| --- | --- |
| Low extraction confidence | OCR cannot reliably identify amount, payee, document type, or due date. |
| Material mismatch | User-entered amount or payee differs materially from extracted data. |
| Missing mandatory field | Required category field is absent. |
| Duplicate or reused evidence | Same or highly similar bill, invoice, tenancy, property, reference, or payment details found. |
| Same-party risk | Payer and payee, tenant and landlord, or bank account holder appear the same or related. |
| Payee mismatch | Extracted payee does not match selected payee or payout destination. |
| Sensitive category | Tenancy/rent, high-value obligation, or category requiring enhanced controls. |
| Suspicious document | Altered, inconsistent, cropped, low-quality, or conflicting evidence. |
| High amount | Amount exceeds configured threshold. |
| Repeated correction | User repeatedly changes extracted values materially. |
| New or unverified payee | Payee lacks sufficient verification for category. |
| Destination mismatch | Extracted payment destination conflicts with registered payout destination. |

Review routing must produce an owner-governed outcome, permitted workflow handoff, Evidence package, and audit trail. DOC-22 does not independently determine Evidence policy, outcome, or status truth.

---

## 16. Evidence Verification Outcomes

Evidence verification should produce one of the following outcomes:

| Outcome | Meaning |
| --- | --- |
| Auto-Verified | Required checks pass within configured thresholds. |
| Auto-Verified with Warning | Checks pass but minor warning or low-severity issue is recorded. |
| Pending User Clarification | User must provide missing information, correction, or additional evidence. |
| Pending Owner Review | Owner-governed human review is required before an applicable downstream gate may proceed. |
| Accepted after Owner Review | The applicable owner accepts Evidence after review. |
| Rejected after Owner Review | The applicable owner determines Evidence is invalid, unsupported, insufficient, or prohibited. |
| Duplicate Suspected | Evidence appears duplicate or reused and requires review or approved exception. |
| Fraud/Risk Escalated | Evidence or source-context pattern is escalated to risk/compliance review. |

Payment eligibility gates in DOC-09 must consume the final verification outcome.

### 16.1 DOC-06C Evidence Status and Payment Readiness Mapping

DOC-12 verification outcomes must map cleanly to the DOC-06C user-facing evidence status and bill/rent payment-readiness model. DOC-12 outcomes describe verification decisions; DOC-06C statuses describe what the user sees and how the bill/rent record becomes payable.

| DOC-12 Outcome | DOC-06C Evidence Status / Handling |
| --- | --- |
| Auto-Verified | `Accepted`. |
| Auto-Verified with Warning | `Accepted` if warning is low severity; otherwise `Pending Review` or `Correction Needed` according to risk/category rule. |
| Pending User Clarification | `Correction Needed` or `Update Needed`. |
| Pending Owner Review | DOC-06C consumes the owner outcome as `Pending Review` where the applicable owner-controlled review affects readiness. |
| Accepted after Owner Review | DOC-06C consumes the owner outcome as `Accepted`. |
| Rejected after Owner Review | DOC-06C consumes the owner outcome as `Rejected`. |
| Duplicate Suspected | `Duplicate Suspected`. |
| Fraud/Risk Escalated | `Pending Review` or risk hold according to DOC-14. |

DOC-12 publishes Evidence and Evidence-to-Payee outcomes. DOC-06C owns the user-facing payment-readiness mapping and consumes only the applicable owner outcomes. DOC-09 consumes payment-facing Bill/Rent facts and applicable readiness outcomes when deriving Projection, materializing Payment Obligations, and evaluating Checkout eligibility. Settlement and Payout remain downstream under DOC-10.

Evidence replacement, expiry, Archive, Restore, prior-version, Evidence-version, replacement-source, retention, and presentation behaviour are not defined here. High-level source/non-erasure policy belongs in DOC-05; route and Bills/Rent presentation belongs in DOC-06B/DOC-06C; Evidence criteria belong in DOC-12; retention/access belongs in DOC-15; and approved representation/lineage belongs in DOC-18.

Extracted fields approved for display should populate the bill/rent detail record in DOC-06C. Evidence detail screens should avoid duplicating those fields except where needed for evidence review, correction, or status explanation.

---

## 17. Payee Verification Linkage

Document extraction should support payee and payout validation but does not replace KYC/KYB, sanctions, payout destination, or risk controls.

Rules:

- extracted payee/biller/landlord/supplier data should be matched against the selected payee record where applicable;
- extracted payment destination data should support payout destination review where shown;
- landlord, property manager, business payee, institution, and higher-risk payees may require enhanced review;
- mismatch between extracted payee and selected payee should route to review unless approved category rules allow it;
- Evidence-to-Payee validation, duplicate detection, and risk checks must not be treated as automatic user-to-user matching, account creation, Payee acceptance, reciprocal visibility, or Payment authorization;
- Payee type and any governed Individual-Payee eligibility outcome are supplied by their applicable owners. DOC-12 does not make an independent legal, operational, or Admin determination of Payee type.

### 17.1 Destination-Fact Handoff

Evidence extraction may support owner-governed matching of intended-Payee and destination facts for one controlled Bill/Rent source. It does not establish bank-account validity, payout readiness, a reusable destination library, a Payee account, or a payment authorization.

The applicable owner must resolve Evidence-to-Payee and destination mismatches under the relevant Evidence, payout, risk, privacy, and security policies. DOC-10 owns payout destination readiness and the immutable authorization-time destination snapshot; DOC-14 and DOC-19 own applicable risk/security controls; DOC-15 owns approved-purpose access and retention; DOC-18 owns representation and lineage; and DOC-22 executes only owner-permitted workflow.

---

## 18. Owner-Permitted Configuration and Execution Handoff

DOC-12 defines the Evidence-domain policy needs that may require approved configuration, such as controlled Category support, Evidence fields, extraction scope, matching, duplicate handling, and review routing. It does not define generic Admin capability, queue, permission, override, threshold, or disposition design.

The applicable product, Evidence, risk, privacy, security, payment, and payout owners retain their policy and decision authority. DOC-22 may execute only the workflow/configuration specifically permitted by those owners, while DOC-18 owns the approved representation and audit/lineage requirements.

---

## 19. Analytics and Data Asset Rules

Evidence data should support product quality, operational efficiency, risk monitoring, category economics, and future analytics.

DOC-12 analytics signals may include:

- document category;
- extracted field completeness;
- OCR confidence;
- user correction rate;
- mismatch type;
- duplicate/reuse rate;
- review outcome;
- owner-governed review outcome reason;
- evidence age;
- category conversion rate;
- fraud or risk escalation rate;
- field-level extraction quality;
- payment success after verification;
- refund, dispute, or chargeback linkage where applicable.

Evidence-derived data must be labeled separately from broader PayPlus user lifecycle data such as Payment behavior, Payer spending behavior, authoritative source and economic-Payee context, owner-governed risk-derived association facts, referral/member-get-member data, support history, refund behavior, and payout history.

Evidence-derived model features, analytics signals, or AI training inputs must preserve lineage to raw, extracted, corrected, verified, and final evidence layers. Raw evidence text, tenancy/property details, medical details, identity document data, domestic helper employment details, and other sensitive fields should not be used for marketing models, partner reporting, external activation, credit scoring, or insurance underwriting unless separately assessed, approved, and documented under DOC-15 and the relevant source documents.

Detailed reporting, warehouse, data marts, lineage, feature/model metadata, and privacy controls belong in DOC-18 and DOC-15.

---

## 20. Security, Privacy, and Access Controls

Evidence may contain sensitive personal, business, tenancy, identity, address, phone, payment, and banking information.

Requirements:

- role-based access control is required;
- sensitive extracted fields should be masked or hidden by default where not needed;
- raw Evidence access should be limited to authorized Payers, owner-permitted personnel/workflows, systems, or partners with an approved purpose;
- UI display must show only the fields needed for the relevant user task;
- evidence access, extraction, correction, review, download, privacy-request and override actions must be logged where applicable;
- every Evidence record is retained indefinitely under the Founder decision; DOC-15 supplies approved-purpose access, masking and lawful handling controls without a destruction schedule.

Detailed privacy and retention rules belong in DOC-15. Security and access controls belong in DOC-19.

---

## 21. UX and Document Alignment Impact

DOC-06C defines the user-facing Bills Evidence sub-route model. DOC-12 must remain aligned with DOC-06C for:

- AI/OCR evidence capture;
- autofill from extracted fields;
- user review and correction before submission;
- extractable versus displayable field distinction;
- duplicate/reused evidence warning;
- pending user clarification;
- pending owner review;
- payer review of final evidence summary before authorization;
- Evidence-to-Payee outcome consumption, while leaving Archive, Restore, prior-version, Evidence-version, replacement-source, retention, and presentation behaviour to their respective owners.

DOC-06 remains the parent UX source map; DOC-06C should remain a user-facing Bills UX document. It should not copy all DOC-12 field tables or data-layer rules.

---

## 22. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-12-001 | Which OCR/document AI provider will be used for MVP? | Product / Engineering | High | Open |
| OQ-12-002 | Retired: the accepted DOC-05 twelve-category Bill inventory is fixed and Rent is separate. Category-specific eligibility, Evidence criteria, field sets, thresholds, detailed labels, and Directory contents remain with their named owners. | DOC-05 / DOC-12 / DOC-06C / DOC-07 / DOC-14 | High | Decided inventory; detailed owner work remains Open |
| OQ-12-003 | What exact mandatory fields apply by category? | Product / Operations / Compliance | High | Open |
| OQ-12-004 | What confidence thresholds trigger user warning or owner-governed review? | Risk / Product / Engineering | High | Open |
| OQ-12-005 | What duplicate strictness applies to tenancy, invoice, business fee, and low-risk categories? | Risk / Compliance / Product | High | Open |
| OQ-12-006 | What sensitive tenancy fields may be extracted, stored, masked or displayed under approved-purpose access while the underlying Evidence record remains retained indefinitely? | Privacy / Legal / Compliance | High | Open |
| OQ-12-007 | What user warning wording is allowed for duplicate/reused evidence without disclosing another user's information? | Legal / Product / Risk | Medium | Open |
| OQ-12-008 | Can evidence-derived data be used for model improvement, analytics, and risk training? | Privacy / Legal / Data | High | Open |
| OQ-12-009 | Retired as a current launch-Category question: no domestic-helper, driver, or personal-service Category is inferred outside the accepted DOC-05 inventory. Any future Category proposal requires its own Founder-approved scope and owner evidence rules. | Product / Compliance / Risk | Medium | Not current scope |
| OQ-12-010 | What owner-permitted DOC-22 workflow/configuration and reason capture are required for Evidence review? | Operations / Risk / Product | Medium | Open |
| OQ-12-011 | Which evidence-derived fields and model features are prohibited from marketing, partner reporting, external activation, credit scoring, or insurance-related targeting? | Privacy / Legal / Risk | High | Open |
| OQ-12-012 | What final mapping, reason codes, and exception rules should connect DOC-12 verification outcomes to DOC-06C evidence status and bill/rent payment readiness? | Product / Risk / Operations / Engineering | High | Open |

---

## 23. Acceptance Criteria

DOC-12 is acceptable when it clearly defines:

- evidence category model;
- document AI/OCR processing flow;
- extractable, normalized, corrected, verified, and final evidence data layers;
- general bill, invoice, tenancy, rent, contract, and service evidence field sets;
- extractable versus displayable field boundaries;
- autofill and user correction rules;
- validation and matching rules;
- duplicate/reused evidence rules;
- red flags and human-review routing;
- verification outcomes;
- payee verification linkage;
- owner-permitted configuration and execution handoff;
- analytics and data asset rules;
- evidence-derived model-use and prohibited-use boundaries;
- privacy, security, and access-control expectations;
- related documents for detailed UX, API, data model, risk, privacy, owner-permitted workflow, and operations specifications.

This document must remain a compact bill verification and evidence-domain specification.

It should not become:

- final AI/OCR provider specification;
- final database schema;
- final fraud rulebook;
- final privacy policy;
- final Admin dashboard workflow;
- final UX screen design;
- final legal opinion.

---

## 24. Revision History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.8.2` | `2026-08-12` | Product Documentation Team | Applied the Founder-settled indefinite-retention rule to Evidence records and reframed the sensitive-tenancy open question around approved-purpose access and masking without changing Evidence ownership. |
| `0.8.1` | `2026-08-12` | Product Documentation Team | Clarified Evidence as verification support rather than source or Payment lifecycle, constrained Evidence examples from creating Category eligibility, and retained economic-Payee association as source context only. |
| `0.8.0` | `2026-08-12` | Product Documentation Team | Consumed the accepted DOC-05 twelve-category Bill inventory and separate Rent boundary; replaced active Request and Receiving Info runtime, generic Admin authority, and defined Archive/version presentation with Payer-only source, Evidence-to-Payee, owner-permitted execution, and explicit owner-handoff boundaries. |
| `0.7.8` | `2026-07-31` | Product Documentation Team | Aligned Evidence, Request, Bill/Rent, Payment Obligation, Checkout eligibility, and downstream Settlement/Payout boundaries with DOC-09. |
| `0.7.7` | `2026-07-27` | Product Documentation Team | Aligned evidence-parity wording by distinguishing payee-created payment requests from direct payer-created obligations/payments. |
| `0.7.6` | `2026-07-26` | Product Documentation Team | Clarified that parent archive projects current evidence into Archived Documents for both restorable and non-restorable obligations, while restore remains obligation-level and previous versions remain non-restorable. |
| `0.7.5` | `2026-07-26` | Product Documentation Team | Defined sole-current-evidence protection, accepted replacement and previous-version behavior, parent-obligation archive/restore, expiry handling, and `ARCHIVED-DOCS-LIST` access. |
| `0.7.4` | `2026-07-26` | Product Documentation Team | Limited bill/rent payment readiness to `Ready to Pay`, `Action Required`, and `Under Review`, kept payment outcomes/archive visibility separate, and clarified that evidence links to the obligation while payer-created payment does not require a request. |
| `0.7.3` | `2026-07-23` | Product Documentation Team | Added Receiving Info proof, identity-name matching, third-party/company review, destination-snapshot, payout-failure, and evidence-reuse lineage boundaries. |
| `0.7.2` | `2026-07-22` | Product Documentation Team | Aligned controlled archived/previous evidence retrieval with DOC-06B `ME-ROOT` and `ARCHIVED-EVIDENCE-LIST` without changing evidence lifecycle, active-version, or archive-not-delete rules. |
| `0.1.0` | `2026-05-30` | Product Documentation Team | Initial founder working baseline for bill category verification, document AI/OCR extraction, autofill, evidence data layers, duplicate detection, payee verification linkage, red-flag routing, and DOC-06 alignment impact. |
| `0.2.0` | `2026-06-02` | Product Documentation Team | Clarified that DOC-14 owns risk meaning and routing framework while final thresholds, algorithms, configuration, and schemas remain with DOC-18 and DOC-22. |
| `0.3.0` | `2026-06-02` | Product Documentation Team | Aligned evidence data layers with DOC-15 by adding field-level classification metadata, displayability, masking, retention, approved-purpose, and lineage requirements for DOC-18. |
| `0.4.0` | `2026-06-02` | Product Documentation Team | Aligned domestic helper, driver, and personal service categories with confirmed evidence-backed MVP scope while keeping exact evidence standards and review thresholds open. |
| `0.5.0` | `2026-06-08` | Product Documentation Team | Added evidence-derived model-use, sensitive-field, prohibited marketing/partner-reporting, and DOC-15/DOC-18 lineage boundaries for AI/data-engine readiness. |
| `0.6.0` | `2026-06-12` | Product Documentation Team | Aligned evidence structure with DOC-06 Bills tab baseline by separating obligation, contract/relationship, and evidence source records; added rent-supporting evidence examples; clarified payee/payout validation versus participant linking. |
| `0.7.0` | `2026-06-18` | Product Documentation Team | Aligned DOC-12 verification outcomes with DOC-06 evidence status, bill/rent payment readiness, active evidence versioning, archive-not-delete behavior, and extracted-field display ownership. |
| `0.7.1` | `2026-07-02` | Product Documentation Team | Aligned evidence verification with DOC-06B `REQUESTS-NEW` by adding evidence-before-request-delivery gate. |
