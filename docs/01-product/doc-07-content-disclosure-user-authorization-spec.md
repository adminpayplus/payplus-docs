---
document_id: DOC-07
title: Content, Disclosure & User Authorization Specification
version: 0.3.0
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - Compliance Lead
  - Legal Lead
  - Risk Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-05-30
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction Ledger & Reporting
  - DOC-19 Security, Tokenization & Authentication
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-07 - Content, Disclosure & User Authorization Specification

## 1. Purpose

This document defines the user-facing content, disclosure, consent, and authorization requirements for the PayPlus MVP.

PayPlus must explain payment requests clearly enough that payers and payees understand:

- what the request is for;
- who created it;
- who will receive payment;
- what evidence supports it;
- how much will be charged;
- what fees apply;
- when payment and payout may occur;
- what actions the user is authorizing;
- what happens if the request is rejected, cancelled, disputed, refunded, reversed, or charged back.

This document is a product and content specification. It is not a final legal opinion, privacy policy, terms of service, payment processing specification, or operations manual.

---

## 2. Scope

### 2.1 In Scope

This document covers:

- product terminology;
- allowed and prohibited user-facing language;
- request-origin labels;
- payer review content;
- payee request creation content;
- OCR/autofill, evidence correction, duplicate warning, and evidence verification disclosure touchpoints;
- payment authorization content;
- fee, promotion, and total charge disclosures;
- multi-card payment disclosures;
- payout and settlement timing disclosures;
- refund, cancellation, dispute, chargeback, and reversal disclosure touchpoints;
- privacy and data collection notices at product touchpoints;
- content audit records required for authorization evidence.

### 2.2 Out of Scope

This document does not define:

- final legal terms;
- final privacy policy;
- final card scheme, PSP, acquirer, or MCC rules;
- payment state machine;
- payout execution rules;
- refund and chargeback operations manual;
- notification templates;
- database schema;
- API contracts.

Those details belong in downstream or adjacent documents.

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Launch jurisdiction | Hong Kong. |
| Product model | Controlled payer-authorized card-funded bill, invoice, fee, rent, domestic service, and approved obligation payment platform. |
| Payer-created requests | MVP scope. |
| Payee-created requests | MVP scope. |
| Tenancy and rent payments | MVP scope, subject to rent-specific controls. |
| Domestic helper, driver, and personal service payments | MVP scope where supported by acceptable evidence. |
| Multi-card payment | MVP scope, up to a configurable number of credit cards per payment. The launch cap is to be confirmed. |
| Payout rails | FPS, cheque, and EPS are acceptable Hong Kong payout rails; final operating-bank setup remains to be confirmed. |
| Settlement timing | Payment gateway settlement expected T+1 to T+3; payout expected same day after upstream settlement. |
| Fee model | Online payment processing service fee as a percentage of transaction amount; exact rates and allocation remain to be confirmed and admin-configurable. |
| Bill verification | OCR/document AI may extract and autofill evidence fields; users must be able to review and correct material fields before submission. |
| KYC/KYB | Individual eKYC and business KYB baseline is highly confirmed; final provider and detailed checks remain to be confirmed. |
| Notifications | App, push, email, SMS, and WhatsApp are candidate channels. |
| Retention | Receipt, payment, account, tax, and audit records expected to be retained for 7 years, subject to final privacy and legal review. |

Unconfirmed items above should not block documentation drafting. They should remain editable assumptions, gated requirements, or open questions until finalized.

---

## 4. Content Principles

| Principle | Requirement |
| --- | --- |
| Plain language | User-facing content should be short, direct, and understandable without legal or payment-industry knowledge. |
| No false certainty | Do not imply payment, payout, refund, or settlement is complete before the relevant system of record confirms it. |
| Explicit authorization | Payment requires clear payer action and recorded authorization. |
| Role clarity | Users must understand whether they are acting as payer, payee, landlord, business payee, or admin. |
| Request-origin clarity | Content must show whether a request is payer-created, payee-created, admin-created, or system-generated. |
| Evidence clarity | Content must explain what evidence supports the obligation without overexposing sensitive data. |
| Evidence data minimization | User-facing screens should show only task-relevant evidence fields; sensitive extracted fields may be stored under controls without broad display. |
| Fee clarity | Payer-facing fees and total charge must be shown before authorization. |
| Configurability | Fee text, card-count limits, category text, and policy-driven messages should be configurable where practical. |
| Auditability | Key content versions and authorization decisions must be logged. |

---

## 5. Product Language Rules

### 5.1 Allowed Language

PayPlus may use language such as:

- bill payment;
- payment request;
- card-funded payment;
- pay eligible bills by card;
- pay eligible invoices, fees, rent, and approved obligations by card;
- pay approved domestic helper, driver, or personal service obligations by card where supported;
- pay rent by card where supported;
- payment to approved payee;
- evidence-backed payment request;
- payer authorization;
- payment processing;
- payout or settlement to payee;
- receipt or confirmation record.

### 5.2 Prohibited Language

PayPlus must not use language that positions the product as:

- wallet;
- stored value;
- cash advance;
- cash withdrawal;
- cashout;
- convert card limit to cash;
- send money freely;
- peer-to-peer transfer;
- remittance;
- bank account top-up;
- pay yourself;
- open marketplace for any invoice;
- automatic tenant charge;
- guaranteed instant payout.

### 5.3 Legal Review Required

Public website copy, app-store copy, onboarding terms, checkout disclosures, privacy notices, and payment authorization language must be reviewed before launch.

---

## 6. Request-Origin Labels

Every user-facing request should identify its origin.

| Origin | User-Facing Label | Meaning |
| --- | --- | --- |
| Payer-created | Created by you | The payer started the payment record. |
| Payee-created | Sent by payee | An approved payee created and sent the request. |
| Admin-created | Created by PayPlus support | PayPlus operations created the record under approved process. |
| System-generated | Generated by PayPlus | The system created an event, reminder, or status update. |

The exact label may vary by screen, but the user must not be confused about who initiated the request.

---

## 7. Payer Review Disclosure

Before payment authorization, the payer must be shown a clear payment summary.

Required fields:

| Field | Requirement |
| --- | --- |
| Payee | Show approved payee name or display name. |
| Request origin | Show whether the request was created by payer, payee, admin, or system. |
| Category | Show bill, invoice, rent, fee, or other approved obligation category. |
| Amount | Show payment amount. |
| Service fee | Show payer fee where applicable. |
| Total charge | Show final amount charged to the payer. |
| Payment method | Show selected card or masked funding source summary. |
| Multi-card split | If applicable, show split amounts and masked card summaries. |
| Evidence | Show evidence summary or accessible evidence view, subject to privacy rules. |
| Verification status | Show role-appropriate evidence status where action is needed, such as pending correction, pending review, duplicate warning, or rejected evidence. |
| Timing | Show expected processing, settlement, and payout timing where relevant. |
| Refund/cancellation note | Show applicable high-level limitations or policy link. |
| PayPlus role | Explain that PayPlus facilitates payment of an eligible obligation to an approved payee. |

The payer must be able to cancel or go back before authorization.

---

## 8. Payer Authorization

### 8.1 Authorization Action

Payment authorization must require an explicit payer action, such as selecting a final confirmation button after reviewing the payment summary.

The authorization action should not be preselected, hidden, implied by viewing a request, or bundled with unrelated consent.

### 8.2 Authorization Statement

The final authorization screen should communicate:

```text
By confirming, you authorize PayPlus to charge the selected payment method(s)
for the total amount shown and to process payment for this approved request.
```

Final wording must be reviewed by Legal, Compliance, Payments, and Product before launch.

### 8.3 Authorization Record

The system must record:

- payer ID;
- request ID;
- payment ID where available;
- payee ID or payee record;
- authorization timestamp;
- amount;
- service fee;
- total charge;
- selected payment method summary;
- multi-card split details where applicable;
- disclosure version;
- terms or policy version where applicable;
- authorization result;
- source channel or device context where available.

Detailed data fields belong in DOC-18.

---

## 9. Payee-Created Request Content

When a payee creates a request, PayPlus should guide the payee to provide accurate and evidence-backed information.

Required content areas:

| Area | Requirement |
| --- | --- |
| Payee identity | Explain that only approved or eligible payees may create requests. |
| Obligation type | Require selection of bill, invoice, rent, fee, or approved obligation category. |
| Evidence | Explain what evidence is required for the selected category. |
| OCR/autofill review | Explain that extracted fields may be auto-filled and must be reviewed before submission where enabled. |
| Correction responsibility | Explain that user corrections should be accurate and may be reviewed. |
| Payer information | Explain how payer contact details will be used to deliver the request. |
| No automatic charge | Make clear that the payer must review and authorize before payment. |
| Accuracy statement | Payee should confirm that request details and evidence are accurate. |
| Prohibited use | Warn against fake invoices, fake rent, self-payment, collusive requests, unsupported P2P, and cashout. |

Payee-created request content must not imply that sending a request guarantees payment.

---

## 10. Rent and Tenancy Content

Rent and tenancy payments are MVP scope but require enhanced content controls.

Rent-related screens should explain:

- tenancy or rent evidence may be required;
- extracted tenancy data may include sensitive fields that are not all displayed in the UI;
- landlord, property manager, or payee verification may be required;
- payer-landlord or payer-property relationship checks may apply;
- limits, manual review, duplicate detection, and risk review may apply;
- duplicate or reused tenancy evidence may trigger warning, hold, or review;
- payout may be delayed or blocked if checks fail;
- recurring rent requests, if supported, still require payer authorization unless a separately approved recurring authorization model exists.

Final rent wording must be reviewed before launch.

---

## 11. Fee, Promotion, and Total Charge Disclosure

Before payer authorization, PayPlus must show:

- payment amount;
- service fee;
- discount, coupon, promotion code, or subsidy where applicable;
- total charge;
- who pays the fee where relevant;
- whether a fee is refundable, non-refundable, reversed, or adjusted under applicable policy.

Exact fee rates, fee allocation, coupons, promotion codes, discount codes, refunds, and reversals remain to be confirmed and should be admin-configurable.

PayPlus must not hide payer-facing fees inside vague or misleading wording.

---

## 12. Multi-Card Disclosure

Multi-card payment is MVP scope.

The payer must be shown:

- maximum number of cards allowed for the payment;
- amount charged to each card;
- masked card summary for each card;
- total charge across all cards;
- fee treatment for split payments;
- what happens if one card authorization fails;
- whether the payer must re-authorize after changing card split amounts.

The exact card-count limit is to be confirmed and should be configurable.

---

## 13. Payment, Settlement, and Payout Timing Disclosure

PayPlus should distinguish:

| Term | User-Facing Meaning |
| --- | --- |
| Payment authorized | Payer approved the payment. |
| Payment processing | PayPlus or its payment partner is processing the card payment. |
| Payment completed | Card payment has completed according to the relevant payment system record. |
| Settlement pending | Funds have not yet settled from the upstream payment partner. |
| Payout pending | Payout to payee has not yet completed. |
| Payout completed | Payout has completed through the approved payout method. |

PayPlus should disclose that payment gateway settlement is expected to be T+1 to T+3 and that payout is expected on the same day after upstream settlement, subject to review, risk checks, bank processing, partner rules, and exceptions.

Do not promise guaranteed same-day payout unless the underlying payment, bank, risk, and operational conditions support it.

---

## 14. Refund, Cancellation, Dispute, Chargeback, and Reversal Disclosure

The product must support status options and case handling for:

- payer rejection before authorization;
- payer query or clarification before authorization;
- payer dispute before authorization;
- cancellation;
- refund;
- reversal;
- chargeback;
- payout exception;
- operational hold.

Detailed policy and handling steps belong in DOC-11, DOC-21, and DOC-22.

DOC-07 owns the user-facing disclosure points:

| Stage | Disclosure Requirement |
| --- | --- |
| Before authorization | Show high-level refund, cancellation, and dispute limitations where material. |
| After failed payment | Explain that payment failed and no successful payment was completed, unless partial multi-card behavior applies. |
| After cancellation | Explain whether payment was not processed, reversed, or pending operational review. |
| Refund requested | Explain request status and expected review path. |
| Dispute opened | Explain that the case is under review and may require evidence. |
| Chargeback received | Show role-appropriate status and support path where applicable. |

Do not expose internal risk reasons or sensitive admin notes to users unless approved.

---

## 15. Privacy and Data Collection Notices

PayPlus collects personal, payment, payee, business, identity, evidence, and transaction data to support onboarding, payment processing, fraud prevention, compliance, support, reporting, tax, audit, and record retention.

Product touchpoints should include privacy notices where users:

- register;
- submit eKYC/KYB information;
- upload identity documents;
- upload bill, invoice, rent, tenancy, or other evidence;
- use OCR/autofill or correct extracted evidence fields;
- receive duplicate/reused evidence warnings;
- enter payer or payee contact details;
- authorize payment;
- open a dispute or support case;
- opt into notification channels.

Privacy notice content must be reviewed against Hong Kong privacy requirements, including collection purpose, use, transfer, retention, access, correction, direct marketing where applicable, and consent requirements.

---

## 16. Notification and Communication Content Boundary

DOC-07 defines what must be disclosed and authorized.

DOC-08 owns notification:

- templates;
- channel-specific wording;
- delivery rules;
- retry rules;
- receipt wording;
- statement wording;
- WhatsApp, SMS, email, push, and app notification behavior.

DOC-07 requirements must be reflected in DOC-08 templates.

---

## 17. Admin-Configurable Content

The admin dashboard or configuration layer should support controlled updates to:

- service fee rates;
- payer/payee fee allocation text;
- promotion, coupon, discount, or subsidy labels;
- multi-card maximum card count;
- category-specific evidence guidance;
- OCR/autofill review guidance;
- duplicate/reused evidence warning text;
- rent-specific evidence guidance;
- payout timing notes;
- refund/cancellation/dispute policy links;
- maintenance or exception banners;
- notification channel availability messages.

Content changes that affect legal, payment, privacy, or financial meaning must follow approval workflow before publication.

---

## 18. Audit and Evidence Requirements

PayPlus must be able to prove what the user saw and accepted at key moments.

Required audit evidence includes:

| Event | Evidence |
| --- | --- |
| Account registration | Terms/privacy version where applicable. |
| eKYC/KYB submission | Consent, provider handoff, submission event, and status. |
| Request creation | Request creator, content version, category, evidence, and confirmation statement. |
| Evidence verification | OCR/autofill notice, extracted-field review, user correction, duplicate warning, verification outcome, and review status where applicable. |
| Payer review | Request details and disclosure version shown to payer. |
| Payment authorization | Final amount, fee, payment method summary, authorization text/version, timestamp, and result. |
| Multi-card authorization | Card split, total charge, per-card amount, and reauthorization event where applicable. |
| Refund/dispute/chargeback case | User-facing status, case messages, evidence submitted, and admin actions. |

Detailed event schema belongs in DOC-18.

---

## 19. External Review References

Legal, Compliance, Privacy, and Payments should validate final content against current official sources and partner rules.

Current reference points include:

- Hong Kong Monetary Authority guidance on Stored Value Facilities and Retail Payment Systems.
- Hong Kong Monetary Authority guidance on Faster Payment System.
- Office of the Privacy Commissioner for Personal Data guidance on the Personal Data (Privacy) Ordinance.
- PSP/acquirer, card network, bank, KYC/KYB provider, and notification-provider contractual requirements.

This document does not interpret those sources as final legal advice.

---

## 20. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-07-001 | What final legal wording is required for payer authorization? | Legal / Product | Open |
| OQ-07-002 | What final privacy notice wording is required at registration, evidence upload, eKYC/KYB, payment authorization, and support touchpoints? | Legal / Privacy | Open |
| OQ-07-003 | What exact fee, promotion, coupon, discount, refund, and reversal wording should be configurable in admin? | Product / Commercial | Open |
| OQ-07-004 | What configurable maximum number of credit cards per payment should be shown at launch? | Product / Payments | Open |
| OQ-07-005 | What wording should explain T+1 to T+3 upstream settlement and same-day-after-settlement payout without overpromising? | Payments / Legal / Product | Open |
| OQ-07-006 | What category-specific disclosure is required for rent and tenancy payments? | Legal / Risk / Product | Open |
| OQ-07-007 | What refund, cancellation, dispute, chargeback, and reversal policy links or short summaries must be shown before authorization? | Operations / Legal / Product | Open |
| OQ-07-008 | What content approval workflow is required for legal, payment, privacy, commercial, or risk-sensitive copy changes? | Project Owner / Compliance | Open |
| OQ-07-009 | What wording should explain OCR/autofill, user correction responsibility, duplicate/reused evidence warning, and sensitive extracted-field handling? | Product / Legal / Privacy | Open |

---

## 21. Acceptance Criteria

DOC-07 is acceptable when:

- user-facing product language is aligned with PayPlus positioning;
- prohibited wallet, cashout, P2P, remittance, and stored-value language is excluded;
- payer authorization requirements are explicit;
- payer review disclosure fields are defined;
- payee-created request content requirements are defined;
- rent and tenancy disclosure requirements are defined;
- OCR/autofill, evidence correction, duplicate warning, and evidence verification disclosure touchpoints are defined;
- fee, promotion, total charge, and multi-card disclosure requirements are defined;
- payment, settlement, and payout timing wording is cautious and accurate;
- refund, cancellation, dispute, chargeback, and reversal disclosure touchpoints are defined;
- privacy and data collection notice touchpoints are identified;
- content audit evidence is defined;
- open questions are clear and do not block continued drafting.

---

## 22. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.3.0 | 2026-05-30 | Aligned disclosure requirements with DOC-12 OCR/autofill, evidence correction, duplicate/reused evidence warning, verification status, and sensitive extracted-field minimization. |
| 0.2.0 | 2026-05-30 | Aligned disclosure scope with updated DOC-01 positioning for invoices, fees, rent, domestic service obligations, approved obligations, and payer-authorized push payment language. |
| 0.1.0 | 2026-05-29 | Initial founder working baseline for content, disclosure, and payer authorization requirements. |
