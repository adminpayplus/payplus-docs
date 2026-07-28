---
document_id: DOC-07
title: Content, Disclosure & User Authorization Specification
version: 0.9.11
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
last_updated: 2026-07-28
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
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-07 - Content, Disclosure & User Authorization Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-07` |
| **Title** | Content, Disclosure & User Authorization Specification |
| **Version** | `0.9.11` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Legal Lead<br>Risk Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-07-28` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

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
- what happens if the request is rejected or cancelled, a linked dispute case is opened, or a linked payment is refunded, reversed, or charged back.

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
| Payer-created obligations and payments | MVP scope; no request or payee acceptance is required by default. |
| Payer-created linking requests | MVP scope where optional party linking is enabled. |
| Payee-created payment requests | MVP scope; payer acceptance is required before payment from the request. |
| Bill and fee payments | MVP scope, subject to evidence, payee, payment, payout, and risk controls. |
| Tenancy and rent payments | MVP scope, subject to rent-specific controls. |
| Domestic helper, driver, and personal service payments | MVP scope where supported by acceptable evidence. |
| Multi-card payment | MVP scope, up to 6 credit cards per payment/profile. |
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
| Request-origin clarity | Content must distinguish payee-created payment requests, optional payer-created linking requests, and direct payer-created obligations/payments. |
| Evidence clarity | Content must explain what evidence supports the obligation without overexposing sensitive data. |
| Evidence display control | User-facing screens should show task-relevant evidence fields; sensitive extracted fields may be stored for approved purposes without broad display. |
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
| Payer-created linking request | Linking request sent by you | The payer invited the payee to link to an evidence-backed obligation for shared visibility or communication. |
| Payee-created payment request | Sent by payee | An approved payee created and sent a payment request for payer review and acceptance. |
| Admin-created | Created by PayPlus support | PayPlus operations created the record under approved process. |
| System-generated | Generated by PayPlus | The system created an event, reminder, or status update. |

The exact label may vary by screen, but the user must not be confused about who initiated the request. A direct payer-created obligation/payment is not a request and should use obligation/payment wording instead of a request-origin label.

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
| Payment method | Show selected card or selected split-card payment profile with masked funding summary. |
| Multi-card split | If applicable, show split amounts, masked card summaries, and any action-required profile issue before authorization. |
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

Payment passcode entry is a separate payer confirmation step before payment authorization proceeds. Additional 2FA, 3DS, OTP, biometric, PSP/acquirer, or PayPlus risk challenge may apply under DOC-09, DOC-14, DOC-15, and DOC-19.

If the payer creates a deferred payment instruction, content must make clear that the payment has not yet been submitted to the PSP/acquirer and that the payer must return to the payment screen to complete the pending action.

If payment quote, promotion quote, card eligibility, fee, timing, or other material terms are revalidated when the payer returns, the updated terms must be shown before submission.

If a saved split-card profile is incomplete because one card is removed, expired, suspended, invalid, or otherwise unavailable, wording must explain that payment cannot proceed until the affected card is replaced, removed, or updated.

### 8.2 Authorization Statement

The final authorization screen should communicate:

```text
By confirming, you authorize PayPlus to charge the selected payment method(s)
for the total amount shown and to process payment for this approved request.
```

For a deferred payment instruction, the confirmation wording must not imply the card is charged immediately. It should state that the user is saving a payment instruction and must return to confirm submission when action is due.

Final wording must be reviewed by Legal, Compliance, Payments, and Product before launch.

### 8.3 Authorization Record

The system must record:

- payer ID;
- request ID where applicable;
- payment ID where available;
- payee ID or payee record;
- authorization timestamp;
- amount;
- service fee;
- total charge;
- selected payment method summary;
- payment instruction ID where applicable;
- multi-card split details where applicable;
- pay-now or deferred instruction choice where applicable;
- selected payee transfer date where applicable;
- payment quote or promotion quote version where applicable;
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
- reward, voucher, miles, or membership benefit impact where applicable;
- total charge;
- who pays the fee where relevant;
- whether a fee is refundable, non-refundable, reversed, or adjusted under applicable policy.

Exact fee rates, fee allocation, coupons, vouchers, promotion codes, discount codes, rewards, miles, membership benefits, refunds, and reversals remain to be confirmed and should be admin-configurable. Promotion calculation and entitlement rules belong in DOC-13.

For an issued reward, `REWARD-DETAIL` must disclose the full benefit, eligibility, restrictions, usage method, limits, issue and usage dates, expiry, status explanation, and complete terms and conditions. Checkout-applied rewards must be shown as available candidates only after current eligibility is evaluated in DOC-09 checkout; viewing details must not imply selection, reservation, use, or guaranteed application.

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
- what happens if only part of the split-card payment is funded;
- that partial funding is not payment completion;
- that settlement-ready funded portions may be paid out while remaining amounts stay unpaid or pending under DOC-09 and DOC-10;
- whether the payer must re-authorize after changing card split amounts.

The MVP maximum is 6 cards per payment/profile. The displayed limit and any narrower partner-, risk-, or category-specific restriction should be configuration-driven where practical.

---

### 12.1 Payment Instruction and Reminder Disclosure

PayPlus must distinguish three user-facing concepts:

| Concept | User-Facing Meaning | Action Destination |
| --- | --- | --- |
| Normal due-date reminder | Reminder based on bill, rent, or obligation due date; payment flow has not started. | Bill/rent/obligation detail. |
| User manual reminder | Reminder date or offset set by user for a bill, rent, or obligation. | Bill/rent/obligation detail. |
| Deferred payment instruction reminder | Payment flow has started and payment context exists, but gateway submission is pending. | Payment/checkout screen. |

Bill/rent reminder cycles, custom reminder dates, reminder toggles, and reminder deletion/disabling must be described as reminder tools only. They must not imply automatic recurring payment, stored authorization, card authorization, gateway submission, payout readiness, or payment completion.

If a reminder is linked to a recurring bill/rent frequency, the user-facing wording should distinguish recurring reminder scheduling from recurring payment authorization. Reminder route behavior belongs in DOC-06. Notification channel and template wording belongs in DOC-08.

Deferred payment instruction wording must explain:

- selected funding date or action date;
- selected payee transfer date where applicable;
- card split and remaining pending amount where applicable;
- expiry or required action deadline;
- that payment quote, promotion quote, card eligibility, fee, or timing may need to be revalidated before submission;
- that PayPlus cannot force the user to complete pending funding legs;
- that partial funding may lead to partial payout of settlement-ready funded portions without making the overall payment completed.

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

Account, authentication, and material-change screens should explain the required action without exposing sensitive security detail. This includes phone SMS OTP verification, new-device 2FA, dormant-login reauthentication, password reset by email deeplink, payment passcode setup/change, and confirmation for material account, credential, payment profile, payout destination, or contact changes.

Where evidence, tenancy, KYC/KYB, payment profile, payout, or risk data is stored but not displayed, user-facing content should describe the purpose at a practical level and avoid implying that hidden fields are unused.

### 15.1 Account, Security, and Privacy Route Content

DOC-06B owns screen behavior. User-facing content must:

- use the verified primary email for email/password login and keep any nickname/display name separate from authentication;
- explain that one verified primary email belongs to one PayPlus account and that Google, Apple, and email/password are explicitly linked login methods rather than separate accounts;
- distinguish `Set Password` from `Change Password`, because a user who registered through Google or Apple may not yet have a PayPlus password;
- explain that matching email addresses do not automatically link, merge, or transfer accounts and that provider linking or unlinking requires an authenticated Account Security action;
- warn before unlinking a login method and prevent removal of the account's final usable login method;
- explain cross-channel verification before phone or email change without exposing OTP or recovery logic;
- present only `Not Verified`, `Processing`, `Verified`, `Failed`, or `Update Required` identity-verification labels with the context-aware actions defined in DOC-06B and the status-display matrix;
- distinguish incomplete capture from submitted provider processing, show no voluntary re-verification action after `Verified`, and prevent wording that encourages duplicate submission;
- explain that Two-Step Verification and Biometric Unlock toggles do not disable mandatory new-device, risk, contact-change, closure, or provider-required authentication;
- explain account-closure blockers, cancellation before finalization, login termination after completion, and continuing record retention without implying immediate deletion;
- distinguish directly editable account fields, governed correction requests, deletion of eligible data, and account closure;
- distinguish optional direct-marketing, personalization, and approved partner-data-use choices from required service, payment, security, risk, compliance, tax, audit, dispute, and retention processing;
- explain that data export uses protected in-app access and that privacy-request service timelines and legal outcomes remain subject to the approved privacy process.
- explain that Receiving Info is a private reusable profile library and not the sole payout source of truth;
- distinguish `Ready to Receive` as a PayPlus profile-readiness label from bank validation or guaranteed payout;
- explain when third-party/company account proof and review are required;
- explain that selecting one profile for a request discloses only that destination to the payer;
- explain that profile edit/archive does not change an accepted request or authorized payment destination;
- warn the payer before authorization when the effective destination differs from an accepted payee-created request.

### 15.2 Authentication Outcome and Message Matrix

PayPlus must maintain one canonical Authentication Outcome and Message Matrix for `ENTRANCE-ROOT`, `AUTH-LOGIN-FAST`, `AUTH-LOGIN-FULL`, `AUTH-RECOVERY`, `AUTH-REGISTRATION`, `ACCOUNT-ACTIVATION`, and their approved child flows.

The mechanism is a confirmed requirement. Exact Outcome IDs, Message IDs, approved user-facing messages, and final mappings remain open and must not be invented during implementation. Until those decisions are approved, route documents should reference this required matrix rather than create competing error copy.

The matrix must distinguish:

- an **Outcome Type ID**, identifying a reusable failure, cancellation, expiry, conflict, restriction, or unavailable condition;
- a **Message ID**, identifying the approved user-facing message and CTA treatment;
- an **Occurrence or Correlation ID**, identifying one actual attempt, incident, or support/audit record.

Multiple internal outcomes may map to one approved user-facing message where separate wording would expose whether an account, identifier, credential, provider link, or security restriction exists.

The matrix must contain:

| Field | Requirement |
| --- | --- |
| Outcome Type ID | Stable identifier for the reusable outcome class. |
| Outcome Classification | Failure, cancellation, expiry, conflict, restriction, or unavailable. |
| Originating Route | Route or child flow where the outcome may occur. |
| User Action / Step | Action or step that produced the outcome. |
| Internal Condition | Controlled description of the underlying condition; internal-only detail must not be copied into user text. |
| Disclosure Level | What may be disclosed before and after the user proves control of the identifier or login method. |
| Message ID | Stable identifier for the approved user-facing wording. |
| Approved Message | Exact message displayed to the user after content approval. |
| Primary and Secondary Actions | Permitted CTA labels, including Retry, Recovery, Login, Create Account, Try Another Method, Support, or Cancel where applicable. |
| Destination | Route or safe fallback opened by each action. |
| Return Behavior | Prior context, safe root, or protected destination restored after resolution. |
| Retry / Restriction Rule | Permitted retry, cooldown, expiry, or lockout treatment without exposing security-sensitive values. |
| Event / Audit Mapping | DOC-18 event and occurrence/correlation linkage required for the outcome. |
| Notification Requirement | Whether DOC-08 defines a separate external or Inbox notification; ordinary in-flow messages are not notifications. |
| Admin / Support Visibility | Permitted operational visibility, reason category, and correlation lookup under DOC-22. |

The matrix must cover, at minimum:

- registration attempt interruption, expiry, identifier conflict, and atomic account-creation failure;
- provider-login unavailable, unlinked, conflict, cancellation, and authentication failure;
- password-login failure, recovery-link expiry, and recovery failure;
- phone format, occupied-number, OTP delivery, resend, expiry, incorrect-code, attempt-limit, and replacement failure;
- identity capture interruption, processing, provider failure, PayPlus-policy failure including duplicate identity, and admin-required update;
- payment-passcode Set mismatch/failure, Change authentication/failure, Reset reauthentication/phone-OTP/recovery failure, and unknown save result;
- protected-return invalid, expired, consumed, unauthorized, or unavailable outcomes.

Exact Outcome Type IDs, Message IDs, and approved copy remain open. DOC-07 must assign them before AI implementation; route or domain documents must not invent competing message identifiers.

DOC-07 owns Message IDs, approved user-facing wording, disclosure level, and CTA wording. DOC-06B owns route placement, destination, and return behavior. DOC-18 owns occurrence/correlation records and event mapping. DOC-19 owns technical authentication outcome codes, retry, lockout, session, provider, biometric, and security handling. DOC-20 owns test coverage, and DOC-22 owns permitted admin/support handling.

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
- reward, voucher, miles, membership, eligibility, expiry, and benefit-entitlement wording;
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
| Authentication outcome | Outcome Type ID, Message ID, originating route/action, occurrence/correlation ID, disclosure level, CTA/destination, timestamp, and permitted technical reason category without secrets. |
| eKYC/KYB submission | Consent, provider handoff, submission event, and status. |
| Request creation | Request creator, content version, category, evidence, and confirmation statement. |
| Evidence verification | OCR/autofill notice, extracted-field review, user correction, duplicate warning, verification outcome, and review status where applicable. |
| Payer review | Request details and disclosure version shown to payer. |
| Payment authorization | Final amount, fee, payment method summary, authorization text/version, timestamp, and result. |
| Promotion authorization | Promotion quote, applied discount, service-fee benefit, coupon/voucher selection, reward entitlement, and related wording shown before authorization where applicable. |
| Multi-card authorization | Card split, total charge, per-card amount, and reauthorization event where applicable. |
| Receiving Info add/edit/archive | Profile ID/version, permitted masked summary, ownership declaration, proof requirement/status, confirmation method, outcome, and notification evidence. |
| Destination selection/change | Destination source and version shown, request or obligation linkage, payer/payee actor, linked-payee notification where applicable, difference warning, and authorization or reauthorization evidence. |
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
| OQ-07-004 | What maximum number of credit cards per payment/profile should be shown at launch? | Product / Payments | Answered: 6 |
| OQ-07-005 | What wording should explain T+1 to T+3 upstream settlement and same-day-after-settlement payout without overpromising? | Payments / Legal / Product | Open |
| OQ-07-006 | What category-specific disclosure is required for rent and tenancy payments? | Legal / Risk / Product | Open |
| OQ-07-007 | What refund, cancellation, dispute, chargeback, and reversal policy links or short summaries must be shown before authorization? | Operations / Legal / Product | Open |
| OQ-07-008 | What content approval workflow is required for legal, payment, privacy, commercial, or risk-sensitive copy changes? | Project Owner / Compliance | Open |
| OQ-07-009 | What wording should explain OCR/autofill, user correction responsibility, duplicate/reused evidence warning, and sensitive extracted-field handling? | Product / Legal / Privacy | Open |
| OQ-07-010 | What wording should explain promotion quotes, coupon/voucher eligibility, miles rewards, membership benefits, expiry, and entitlement limits before authorization? | Product / Commercial / Legal | Open |
| OQ-07-011 | What wording should explain SMS OTP, new-device 2FA, dormant-login reauthentication, payment passcode, material-change confirmation, and security notifications? | Product / Security / Legal | Open |
| OQ-07-012 | What exact wording should explain deferred payment instruction, pending funding legs, partial funding, partial payout, remaining unpaid amount, and payment completion boundary? | Product / Legal / Payments | Open |
| OQ-07-013 | What wording should explain quote expiry, promotion reservation, recalculation, and changed checkout terms when a payer returns to a deferred payment instruction? | Product / Legal / Growth | Open |
| OQ-07-014 | What exact Outcome Type IDs, Message IDs, approved messages, disclosure levels, CTA labels, destinations, and technical/event mappings should populate the mandatory Authentication Outcome and Message Matrix? | Product / Content / Design / Security / Privacy / Support | Open; mechanism and required fields confirmed |

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
- deferred payment instruction, reminder destination, partial funding, partial payout, and remaining unpaid amount disclosure boundaries are defined;
- deferred instruction quote revalidation and changed-term disclosure boundaries are defined;
- coupon, voucher, reward, miles, membership, entitlement, and expiry disclosure boundaries are defined where applicable;
- payment, settlement, and payout timing wording is cautious and accurate;
- refund, cancellation, dispute, chargeback, and reversal disclosure touchpoints are defined;
- privacy and data collection notice touchpoints are identified;
- the mandatory Authentication Outcome and Message Matrix mechanism, fields, ownership, and open exact-copy/ID boundary are defined;
- content audit evidence is defined;
- open questions are clear and do not block continued drafting.

---

## 22. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.9.11 | 2026-07-28 | Aligned identity wording with the five approved labels and context-aware actions, prohibited voluntary re-verification after Verified, and defined the mandatory authentication outcome categories while keeping exact IDs and copy open. |
| 0.9.10 | 2026-07-28 | Defined the mandatory Authentication Outcome and Message Matrix fields, ownership, disclosure and many-to-one mapping rules while leaving exact IDs and approved messages open; removed login-name content requirements. |
| 0.9.9 | 2026-07-27 | Added user-facing content boundaries for one unique primary email, explicit email/Google/Apple login methods, Set versus Change Password, no automatic email-based account linking, and final-login-method protection. |
| 0.9.8 | 2026-07-27 | Distinguished direct payer-created obligations/payments from payer-created linking requests and payee-created payment requests, and aligned user-facing origin labels without changing authorization rules. |
| 0.9.7 | 2026-07-26 | Separated request lifecycle outcomes from linked dispute cases and linked payment refund, reversal, and chargeback outcomes. |
| 0.9.6 | 2026-07-26 | Replaced the stale card-count TBC wording with the confirmed MVP maximum of 6 cards per payment/profile while preserving narrower configurable restrictions. |
| 0.9.5 | 2026-07-23 | Added Receiving Info library, readiness, proof, privacy, selected-destination, profile-version, linked-payee notification, changed-destination warning, and authorization-evidence content requirements. |
| 0.9.4 | 2026-07-22 | Added account, identity-verification, security-toggle, contact-change, account-closure, privacy-choice, correction/deletion, and protected-export content boundaries for the defined Me child routes. |
| 0.5.0 | 2026-06-02 | Clarified bill and fee MVP disclosure baseline and aligned risk/disclosure assumptions with DOC-14. |
| 0.6.0 | 2026-06-02 | Aligned disclosure requirements with DOC-15 by adding payment passcode, account/authentication content, material-change confirmation wording, and stored-but-not-displayed data notice boundaries. |
| 0.7.0 | 2026-06-02 | Aligned disclosure requirements with DOC-09 user payment instruction by adding deferred payment, reminder destination, partial funding, partial payout, and remaining unpaid amount wording boundaries. |
| 0.8.0 | 2026-06-02 | Added deferred payment instruction quote revalidation disclosure for payment quote, promotion quote, card eligibility, fee, timing, and changed checkout terms. |
| 0.9.0 | 2026-06-17 | Aligned reminder disclosure boundaries with DOC-06 reminder list/detail routes by distinguishing recurring reminders from automatic recurring payment or stored authorization. |
| 0.9.1 | 2026-07-06 | Aligned disclosure requirements with DOC-06B Payment Profile route and DOC-09 split-card profile rules, including masked card/profile summaries, 6-card cap, and incomplete-profile warnings before authorization. |
| 0.9.3 | 2026-07-21 | Added issued-reward detail disclosure requirements for full benefit, eligibility, restrictions, usage, limits, dates, status, and complete terms, while separating detail viewing from checkout selection and consumption. |
| 0.9.2 | 2026-07-14 | Clarified that authorization records require a request ID only where the payment originated from a request. |
| 0.4.0 | 2026-06-01 | Aligned disclosure requirements with DOC-13 by adding promotion quote, coupon/voucher, reward, miles, membership, entitlement, expiry, and authorization-audit wording boundaries. |
| 0.3.0 | 2026-05-30 | Aligned disclosure requirements with DOC-12 OCR/autofill, evidence correction, duplicate/reused evidence warning, verification status, and sensitive extracted-field display controls. |
| 0.2.0 | 2026-05-30 | Aligned disclosure scope with updated DOC-01 positioning for invoices, fees, rent, domestic service obligations, approved obligations, and payer-authorized push payment language. |
| 0.1.0 | 2026-05-29 | Initial founder working baseline for content, disclosure, and payer authorization requirements. |
