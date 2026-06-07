---
document_id: DOC-12
title: Bill Category, Document AI/OCR & Payee Verification Specification
version: 0.5.0
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
last_updated: 2026-06-08
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
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
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

## 1. Purpose

This document defines PayPlus MVP rules for bill category verification, document AI/OCR extraction, autofill, evidence validation, duplicate detection, payee matching, and human-review routing.

Bill verification is a core PayPlus capability. It improves the user experience by reading bills, invoices, tenancy agreements, contracts, and other evidence, then auto-filling request fields while preserving evidence, traceability, compliance controls, and risk review.

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
| Product evidence requirements and MVP request rules | DOC-05 |
| User journey, UX screens, review/correction flow | DOC-06 |
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
| Admin review queues, override workflow, configuration, permissions | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Product model | PayPlus is an evidence-backed, payer-authorized bill, invoice, fee, rent, domestic service, and approved obligation payment platform. |
| Bill verification | Important MVP capability for better UX, autofill, evidence quality, and risk control. |
| Evidence types | Bill, invoice, tenancy, rent demand, contract, service agreement, payment statement, and other approved evidence. |
| AI/OCR role | System should read evidence, capture fields, classify documents, and autofill request fields where confidence is acceptable. |
| User correction | Users must be able to review and correct autofilled fields before submission. |
| Human review | Most evidence should be system-processed; unclear, inconsistent, duplicate, reused, sensitive, or risky cases route to human review. |
| Data asset | Extracted evidence data is an important PayPlus data asset, but it is only one component of the broader PayPlus data profile and must remain classified, purpose-linked, and governed under DOC-15 and DOC-18. |
| Configuration | Category fields, confidence thresholds, duplicate strictness, red flags, and review routing should be configurable in admin. |

Unconfirmed items should remain editable assumptions or gated requirements and should not block continued documentation drafting.

---

## 4. Core Principles

| Principle | Requirement |
| --- | --- |
| Evidence-backed payments | Payment requests must link to acceptable evidence unless an approved exception applies. |
| UX assist, not blind automation | AI/OCR may autofill fields, but users must review and correct material fields before submission. |
| Extractable does not mean displayable | Sensitive fields may be extracted and stored under controls without being shown broadly in the UI. |
| Data layer separation | Evidence document data must be labeled as document-derived data, not as the entire user profile. |
| Configurable controls | Required fields, thresholds, duplicate handling, and review rules must be configurable by category and risk level. |
| Human review for risk | Material mismatch, low confidence, duplicate/reused evidence, same-party indicators, or suspicious documents must route to review. |
| Auditability | Raw evidence, extraction, user correction, verification result, review decision, and final evidence snapshot must be traceable. |
| Privacy by design | Evidence may contain sensitive personal, business, property, tenancy, payment, and identity information; access and display must be limited. |

---

## 5. Evidence Category Model

MVP and candidate evidence categories include:

| Evidence Category | Typical Use | Notes |
| --- | --- | --- |
| Bill | Utility, telecom, internet, school, medical, service, or other approved bill. | Usually strong reference, amount, due date, and payee data. |
| Invoice | Business or service invoice. | Requires payee/business validation where applicable. |
| Tenancy agreement | Rent and property-related payment. | Sensitive category; requires enhanced extraction, duplicate checks, and review rules. |
| Rent demand or rent statement | Rent payment evidence. | May supplement or replace full tenancy agreement where approved. |
| Contract or service agreement | Domestic helper, driver, personal service, or other contractual obligation. | Field requirements depend on category. |
| Payment statement | Statement showing amount due or payment schedule. | Must be linked to approved obligation and payee. |
| Official notice | Formal fee, levy, or demand notice where category is approved. | May require institution or issuer validation. |
| Other approved obligation evidence | Admin-approved document or record. | Requires documented exception and review rule. |

Unsupported or prohibited categories must follow DOC-01, DOC-03, DOC-04, DOC-05, and DOC-14.

---

## 6. Document AI/OCR Processing Flow

DOC-12 defines the following verification flow:

1. User creates or edits a request or obligation record.
2. User uploads or links evidence.
3. System validates file type, file size, malware/safety checks, and required metadata where applicable.
4. System runs OCR/text extraction.
5. System classifies document type and evidence category.
6. System extracts candidate fields.
7. System assigns field-level and document-level confidence.
8. System normalizes extracted values.
9. System autofills eligible request fields.
10. User reviews and corrects autofilled fields.
11. System compares extracted values, user-corrected values, selected payee, payer, request amount, category, and history.
12. System applies duplicate, mismatch, same-party, and risk rules.
13. System assigns verification outcome.
14. Low-risk cases proceed to payment eligibility gates in DOC-09.
15. Red-flag cases route to admin/human review under DOC-22.

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
| Human Review Layer | Admin review decision, reason, notes, evidence, and outcome. |
| Final Evidence Snapshot | The version of evidence and fields used for payer review and payment authorization. |
| Analytics Layer | Aggregated or permitted data used for product quality, OCR performance, risk analytics, and category insights. |

Other PayPlus data layers, such as payment behavior, spending patterns, user relationships, referral/member-get-member activity, refunds, chargebacks, support behavior, and payout history, belong in DOC-18 and later analytics specifications.

Each evidence layer and material field should carry DOC-15 classification metadata in DOC-18, including data class, sensitivity, displayability, masking rule, retention policy, owner, approved purpose, access role, audit requirement, source, and lineage. Evidence-derived data is normally Evidence and Obligation Data, but some extracted fields may also support KYC/KYB, payout/payee, risk/compliance, payment, analytics, or derived-data classifications depending on use.

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
| Biller or supplier name | Payee matching and payer review. |
| Customer or payer name | Relationship and evidence validation where applicable. |
| Bill, invoice, or reference number | Duplicate detection and reconciliation. |
| Issue date | Freshness and audit. |
| Due date | User reminder, eligibility, and payout timing context. |
| Amount due | Request amount autofill and mismatch check. |
| Currency | Payment and settlement validation. |
| Description or service details | Category and obligation support. |
| Billing or service period | Recurring and duplicate checks. |
| Payment destination details | Payee verification and payout destination support where applicable. |
| Business or issuer identifier where shown | Business/institution validation where applicable. |

Display in UI should be limited to fields needed for request creation, payer review, and user confirmation. Sensitive or unnecessary extracted fields should be masked, hidden, or restricted according to DOC-15 and DOC-19.

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

Detailed UX display rules belong in DOC-06 and DOC-07. Privacy, masking, retention, and access-control rules belong in DOC-15 and DOC-19.

---

## 11. Contract and Service Evidence Field Set

For contracts, service agreements, domestic helper/driver evidence, personal service evidence, and similar obligations, PayPlus should extract:

| Field | Use |
| --- | --- |
| Service provider or payee name | Payee matching and request validation. |
| Customer, employer, or payer name | Relationship validation where applicable. |
| Contract or service description | Category and obligation support. |
| Contract/reference number where shown | Duplicate detection and audit. |
| Service period | Recurrence, amount, and duplicate checks. |
| Amount payable | Request amount autofill and mismatch check. |
| Due date or payment schedule | Reminder and payment timing context. |
| Payment destination details | Payee verification and payout support where applicable. |
| Supporting identity/contact fields where shown | Review-only validation where required. |

Domestic helper, driver, and personal service payment categories are MVP scope where supported by acceptable evidence and enabled controls. Exact evidence standards, review thresholds, privacy visibility, and category configuration remain subject to legal, compliance, risk, product, and operations confirmation.

---

## 12. Autofill and User Correction Rules

AI/OCR-extracted fields may autofill request fields when confidence and category rules permit.

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
| Amount match | Compare extracted amount with user-entered/request amount. |
| Payee match | Compare extracted payee/biller/landlord/supplier name with selected payee or payout destination. |
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
- admin should be able to disable, soften, or strengthen duplicate rules by category or configuration, with audit trail.

Duplicate detection must not disclose another user's sensitive details. Risk-routing framework belongs in DOC-14. Final threshold configuration and admin review workflow belong in DOC-22, with supporting data model in DOC-18.

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

Review routing must produce clear status, admin queue entry, reason code, evidence package, and audit trail.

---

## 16. Evidence Verification Outcomes

Evidence verification should produce one of the following outcomes:

| Outcome | Meaning |
| --- | --- |
| Auto-Verified | Required checks pass within configured thresholds. |
| Auto-Verified with Warning | Checks pass but minor warning or low-severity issue is recorded. |
| Pending User Clarification | User must provide missing information, correction, or additional evidence. |
| Pending Admin Review | Human review required before payment eligibility. |
| Approved by Admin | Admin approves evidence after review. |
| Rejected by Admin | Evidence is invalid, unsupported, insufficient, or prohibited. |
| Duplicate Suspected | Evidence appears duplicate or reused and requires review or approved exception. |
| Fraud/Risk Escalated | Evidence or relationship pattern is escalated to risk/compliance review. |
| Evidence Replaced | User replaces prior evidence; replacement history is retained. |
| Evidence Expired | Evidence is too old or no longer valid under category rules. |

Payment eligibility gates in DOC-09 must consume the final verification outcome.

---

## 17. Payee Verification Linkage

Document extraction should support payee verification but does not replace KYC/KYB, sanctions, payout destination, or risk controls.

Rules:

- extracted payee/biller/landlord/supplier data should be matched against the selected payee record where applicable;
- extracted payment destination data should support payout destination review where shown;
- landlord, property manager, business payee, institution, and higher-risk payees may require enhanced review;
- mismatch between extracted payee and selected payee should route to review unless approved category rules allow it;
- payee-created requests should require evidence equal to or stronger than payer-created requests for the same category.

KYC/KYB, sanctions, and fraud rules belong in DOC-14 and DOC-19. Payout destination controls belong in DOC-10. Data schema belongs in DOC-18.

---

## 18. Admin Configuration Requirements

Admin configuration should support:

- enabled evidence categories;
- mandatory and optional fields by category;
- extractable fields by category;
- UI-displayable fields by role;
- confidence thresholds;
- amount mismatch thresholds;
- payee/payer/name matching thresholds;
- duplicate strictness;
- red-flag routing rules;
- review queue assignment;
- category enablement or disablement;
- OCR/autofill enablement or disablement;
- user warning behavior;
- manual override permissions and reason codes.

Detailed admin screens, permissions, workflow, and audit controls belong in DOC-22.

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
- admin rejection reason;
- evidence age;
- category conversion rate;
- fraud or risk escalation rate;
- field-level extraction quality;
- payment success after verification;
- refund, dispute, or chargeback linkage where applicable.

Evidence-derived data must be labeled separately from broader PayPlus user lifecycle data such as payment behavior, user spending behavior, payer/payee relationships, referral/member-get-member data, support history, refund behavior, and payout history.

Evidence-derived model features, analytics signals, or AI training inputs must preserve lineage to raw, extracted, corrected, verified, and final evidence layers. Raw evidence text, tenancy/property details, medical details, identity document data, domestic helper employment details, and other sensitive fields should not be used for marketing models, partner reporting, external activation, credit scoring, or insurance underwriting unless separately assessed, approved, and documented under DOC-15 and the relevant source documents.

Detailed reporting, warehouse, data marts, lineage, feature/model metadata, and privacy controls belong in DOC-18 and DOC-15.

---

## 20. Security, Privacy, and Access Controls

Evidence may contain sensitive personal, business, tenancy, identity, address, phone, payment, and banking information.

Requirements:

- role-based access control is required;
- sensitive extracted fields should be masked or hidden by default where not needed;
- raw evidence access should be limited to users, payees, admins, systems, or partners with approved purpose;
- UI display must show only the fields needed for the relevant user task;
- evidence access, extraction, correction, review, download, deletion, and override actions must be logged where applicable;
- data retention and deletion must follow legal, privacy, audit, tax, finance, and dispute requirements.

Detailed privacy and retention rules belong in DOC-15. Security and access controls belong in DOC-19.

---

## 21. UX and Document Alignment Impact

DOC-12 introduces more specific evidence verification flow than DOC-06 currently describes.

After DOC-12 is approved, DOC-06 should be reviewed and updated for:

- AI/OCR evidence capture;
- autofill from extracted fields;
- user review and correction before submission;
- extractable versus displayable field distinction;
- duplicate/reused evidence warning;
- pending user clarification;
- pending admin review;
- payer review of final evidence summary before authorization.

DOC-06 should remain a user journey and UX scope document. It should not copy all DOC-12 field tables or data-layer rules.

---

## 22. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-12-001 | Which OCR/document AI provider will be used for MVP? | Product / Engineering | High | Open |
| OQ-12-002 | Which evidence categories are enabled at MVP launch? | Product / Compliance / Risk | High | Open |
| OQ-12-003 | What exact mandatory fields apply by category? | Product / Operations / Compliance | High | Open |
| OQ-12-004 | What confidence thresholds trigger user warning or admin review? | Risk / Product / Engineering | High | Open |
| OQ-12-005 | What duplicate strictness applies to tenancy, invoice, business fee, and low-risk categories? | Risk / Compliance / Product | High | Open |
| OQ-12-006 | What sensitive tenancy fields may be extracted, stored, masked, displayed, or deleted? | Privacy / Legal / Compliance | High | Open |
| OQ-12-007 | What user warning wording is allowed for duplicate/reused evidence without disclosing another user's information? | Legal / Product / Risk | Medium | Open |
| OQ-12-008 | Can evidence-derived data be used for model improvement, analytics, and risk training? | Privacy / Legal / Data | High | Open |
| OQ-12-009 | What exact evidence standards, field requirements, and review thresholds apply to domestic helper, driver, and personal service obligations? | Legal / Compliance / Risk / Product | Medium | Open |
| OQ-12-010 | What admin override permissions and reason codes are required for evidence approval? | Operations / Risk / Product | Medium | Open |
| OQ-12-011 | Which evidence-derived fields and model features are prohibited from marketing, partner reporting, external activation, credit scoring, or insurance-related targeting? | Privacy / Legal / Risk | High | Open |

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
- admin configuration requirements;
- analytics and data asset rules;
- evidence-derived model-use and prohibited-use boundaries;
- privacy, security, and access-control expectations;
- related documents for detailed UX, API, data model, risk, privacy, admin, and operations specifications.

This document must remain a compact bill verification and evidence-domain specification.

It should not become:

- final AI/OCR provider specification;
- final database schema;
- final fraud rulebook;
- final privacy policy;
- final admin dashboard workflow;
- final UX screen design;
- final legal opinion.

---

## 24. Revision History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | `2026-05-30` | Product Documentation Team | Initial founder working baseline for bill category verification, document AI/OCR extraction, autofill, evidence data layers, duplicate detection, payee verification linkage, red-flag routing, and DOC-06 alignment impact. |
| `0.2.0` | `2026-06-02` | Product Documentation Team | Clarified that DOC-14 owns risk meaning and routing framework while final thresholds, algorithms, configuration, and schemas remain with DOC-18 and DOC-22. |
| `0.3.0` | `2026-06-02` | Product Documentation Team | Aligned evidence data layers with DOC-15 by adding field-level classification metadata, displayability, masking, retention, approved-purpose, and lineage requirements for DOC-18. |
| `0.4.0` | `2026-06-02` | Product Documentation Team | Aligned domestic helper, driver, and personal service categories with confirmed evidence-backed MVP scope while keeping exact evidence standards and review thresholds open. |
| `0.5.0` | `2026-06-08` | Product Documentation Team | Added evidence-derived model-use, sensitive-field, prohibited marketing/partner-reporting, and DOC-15/DOC-18 lineage boundaries for AI/data-engine readiness. |
