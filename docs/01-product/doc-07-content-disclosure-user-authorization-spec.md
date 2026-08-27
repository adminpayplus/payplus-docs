---
document_id: DOC-07
title: Content, Disclosure & User Authorization Specification
version: 1.1.1
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
last_updated: 2026-08-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-17 API & Third-party Integration Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-07 - Content, Disclosure & User Authorization Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-07` |
| **Title** | Content, Disclosure & User Authorization Specification |
| **Version** | `1.1.1` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Legal Lead<br>Risk Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-17 API & Third-party Integration Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines the governed user-facing communication, disclosure, consent, and authorization requirements for the PayPlus MVP.

PayPlus must explain controlled Bill/Rent payment meaning clearly enough that Payers understand:

- what authoritative source context is being considered;
- who the economic Payee is where disclosure is permitted;
- what attached Evidence is present or required under the applicable Bill tier or mandatory-Evidence Rent rule, noting that Tier 1 Bills may proceed without attached Evidence;
- how much will be charged;
- what fees apply;
- when payment and payout may occur;
- what actions the user is authorizing;
- what happens if an owner-governed payment, adjustment or support outcome requires attention.

This document is a product and content specification. It is not a final legal opinion, privacy policy, terms of service, payment processing specification, or operations manual.

---

## 2. Scope

### 2.1 In Scope

This document covers material user-facing communication that affects authorization, financial or processing meaning, user consequences or permitted action, mandatory disclosure, risk or privacy, recovery, or an unavailable resolution.

It covers:

- product terminology;
- allowed and prohibited user-facing language;
- Payer payment-review content;
- OCR/autofill, evidence correction, duplicate warning, and evidence verification disclosure touchpoints;
- payment authorization content;
- fee, promotion, and total charge disclosures;
- multi-card payment disclosures;
- payout and settlement timing disclosures;
- refund, cancellation, dispute, chargeback, and reversal disclosure touchpoints;
- privacy and data collection notices at product touchpoints;
- content audit records required for authorization evidence.

Ordinary navigation labels, general helper text, marketing expression, and presentation-only copy do not become DOC-07-owned merely because they contain text. They remain with their existing owners unless they express or alter a governed Semantic, Disclosure, CTA, or approved Copy contract.

### 2.2 Out of Scope

This document does not define:

- final legal terms;
- final privacy policy;
- final card scheme, PSP, acquirer, or MCC rules;
- payment state machine;
- payout execution rules;
- refund and chargeback operations manual;
- notification templates;
- notification identity, trigger, recipient, channel eligibility, delivery, retry, delivery evidence, or read/archive behavior;
- route, screen, component, placement, or return-behavior definitions;
- business-condition evaluation, payment calculations, eligibility, authorization rules, resolver logic, risk decisions, or security decisions;
- database schema;
- API contracts;
- runtime registry or version-key implementation;
- final Admin roles, permissions, publication workflow, activation mechanism, or rollback implementation.

Those details belong in downstream or adjacent documents.

---

## 3. Current Decision Baseline

DOC-07 consumes the Payer-only product baseline: a Consumer User is a Payer; an economic Payee may be an individual or institution/company and need not be a User. User-facing content must distinguish Bills governed by the Tier 1/2/3 model from the separate mandatory-Evidence Rent journey, while preserving Category-bound acquisition, owner-controlled Payment/Payout gates, and the prohibition on open transfer, Payee-account, Request, Linking, To Receive, Receiving Info, reciprocal-visibility or legacy runtime concepts.

Exact Message IDs, final Copy, CTA labels, localization and presentation remain DOC-07-owned and are only drafted when their source owner has supplied the required meaning. This Founder Working Baseline alignment removes obsolete two-sided content; it does not approve replacement Copy, outcomes, CTAs, routes, identifiers or notification delivery.

| Area | Baseline |
| --- | --- |
| Launch jurisdiction | Hong Kong. |
| Product model | Controlled Category-bound Bills use the approved Tier 1/2/3 model; Rent remains a separate mandatory-Evidence journey. Neither creates open P2P, remittance, cashout or marketplace scope. |
| Bill and Rent acquisition | Payer selects Directory discovery or provides a Payee within a supported Bill Category, or begins separate Rent. Bill acquisition may use optional or mandatory attached Evidence according to its tier; Rent always requires attached Evidence. Acquisition itself creates neither a Request, Payee account nor Payment. |
| Economic Payee | An individual or institution/company recipient, subject to owner-governed source, Evidence, destination, risk, Payout and privacy outcomes. |
| Multi-card payment | MVP scope, up to 6 credit cards per payment/profile. |
| Payout rails | FPS, cheque, and EPS are illustrative Hong Kong rail considerations; final rail and operating-bank setup remain subject to confirmation. |
| Settlement timing | Gateway settlement and same-day-after-settlement payout are working assumptions subject to PSP/acquirer, bank, risk, legal, partner and reconciliation confirmation. |
| Fee model | Online payment processing service fee as a percentage of transaction amount; exact rates, allocation, configuration mechanism, and operational authority remain to be confirmed by their formal owners. Applicable fees and total charge must still be disclosed before authorization. |
| Bill verification | OCR/document AI may extract and autofill evidence fields; users must be able to review and correct material fields before submission. |
| KYC/KYB | Individual eKYC and business KYB are working assumptions; provider and detailed checks remain subject to formal owner confirmation. |
| Notifications | Eligibility, recipient, channel, template, delivery and preferences are DOC-08-owned. DOC-07 may supply owner-approved content only. |
| Retention | Indefinite retention remains the accepted product/governance direction, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. No user-facing Copy, finite replacement duration or implementation mechanism is defined here. |
| Communication architecture | Governed material communication uses central authoritative contracts, bounded Domain Slices, layered composition, reference-only integration, and layer-level governance. Centrality is logical and does not require one matrix, file, physical registry, database, runtime service, enterprise registry, or new persistent object. |
| Checkout authorization | Every applicable Provider Submission requires current payer authorization. Earlier review, authorization, profile or card selection, Resume, notification content, or provider return does not authorize a later Provider Submission. |
| Instruction notification entry | Every instruction-related notification enters `NOTIFICATION-DETAIL`, which revalidates current state, payer, permission, target, and action availability before an owner-approved current CTA may invoke the DOC-09 Checkout Resolver. |

Unconfirmed items above remain owner-assigned assumptions, affected-path dependencies or open questions until finalized; they do not alter the accepted product meaning.

---

## 4. Content Principles

| Principle | Requirement |
| --- | --- |
| Plain language | User-facing content should be short, direct, and understandable without legal or payment-industry knowledge. |
| No false certainty | Do not imply payment, payout, refund, or settlement is complete before the relevant system of record confirms it. |
| Explicit authorization | Payment requires clear payer action and recorded authorization. |
| Role clarity | Content must distinguish the Payer from the economic Payee without implying a Payee account, participant relationship, recipient action or reciprocal runtime. |
| Source clarity | Content must distinguish temporary capture, authoritative source, Declaration, attached Evidence where present or required, Payable Basis, Payment Obligation, Checkout, confirmed Payment and projection without changing owner rules. |
| Evidence clarity | Content must explain whether attached Evidence is absent, optional, present, required, pending or accepted under the applicable Bill tier or mandatory-Evidence Rent rule, without overexposing sensitive data. |
| Evidence display control | User-facing screens should show task-relevant evidence fields; sensitive extracted fields may be stored for approved purposes without broad display. |
| Fee clarity | Payer-facing fees and total charge must be shown before authorization. |
| Controlled change | Mutability is governed by communication layer. A configurable expression must not alter source-owned meaning, eligibility, authorization, route, payment, risk, privacy, security, or resolver logic. |
| Auditability | Key content versions and authorization decisions must be logged. |

### 4.1 Governed Communication Architecture

DOC-07 uses this logical architecture for material communication:

```text
Central Authoritative Contracts
    + Bounded Domain Slices
    + Layered Composition
    + Reference-Only Integration
    + Layer-Level Governance
```

`Central` means that each governed communicated meaning has one authoritative contract location and accountable owner. Central contracts may remain domain-specific. Cross-domain reuse is permitted only where meaning, owner, disclosure, prohibited implications, and CTA constraints genuinely align. This architecture does not require one large matrix, one physical registry, one database, one runtime service, one enterprise registry, or one new persistent object.

#### 4.1.1 Communication Layers

| Layer | Governs | Must not govern |
| --- | --- | --- |
| Semantic Contract | User-relevant meaning, required understanding, must-communicate facts, must-not-imply facts, audience, and authoritative source references. | Source-condition evaluation, payment logic, route choice, security/risk decisions, or runtime schema. |
| Outcome and Resolution Relationship | The communicated relationship to a source-owned Outcome and owner-permitted Resolution Strategy. | Redefining an Outcome, inventing a Resolution Strategy, creating a persistent status, or making an unavailable capability available. |
| Composition Rule | Permitted structure and relationships among already-supplied Semantic, Disclosure, CTA, and expression elements. | Determining whether a condition is true; executable if/else branching; eligibility evaluation; payment calculation; route selection; authorization; or resolver, risk, privacy, or security decisions. |
| Disclosure Contract | Mandatory communicated meaning, prohibited omission, disclosure boundary, and reference to the owner of the underlying obligation. | Inventing legal, payment, privacy, risk, or compliance requirements. |
| CTA Contract | User-facing action intent, referenced capability, route, or resolver, revalidation requirement, prohibited implication, and unavailable-action treatment. | Current eligibility, authorization, executable action logic, route decisions, or security decisions. |
| Copy | Approved user-facing expression of the applicable Semantic, Disclosure, and CTA Contracts. | Changing facts, consequences, eligibility, disclosure, or action meaning. |
| Locale Variant | Meaning-preserving localized expression of approved Copy. | Locale-specific business logic, weaker disclosure, or broader action authority. |
| Presentation Mapping | Mapping of approved expression to an owner-defined route, component, surface, slot, or channel. | Inventing routes, screens, components, notification triggers, or domain statuses. |

Semantic is authoritative. Composition defines communication structure. Disclosure defines mandatory communicated meaning. Copy and Locale express accepted meaning. Presentation Mapping determines where and how that expression appears. A later layer must not contradict or silently broaden an earlier authoritative layer.

#### 4.1.2 Core Invariants

1. Every governed communication definition or mapping must reference authoritative business contracts instead of embedding executable business semantics.
2. Referencing a contract does not transfer ownership of that contract.
3. Reference validity proves traceability only; it does not prove current eligibility.
4. Current eligibility and permitted action must be revalidated by the authoritative source owner.
5. Composition does not execute business branching.
6. Disclosure does not invent the underlying obligation.
7. A CTA Contract references action intent, capability, route, or resolver without embedding eligibility.
8. Copy and Locale must preserve accepted required and prohibited meaning.
9. Presentation Mapping must use owner-defined product structure.
10. AI may propose an expression but must not redefine intent, approve its own output, or gain activation authority.
11. The PayPlus Documentation Development Workflow remains the sole canonical Documentation Workflow.
12. No new persistent object may be introduced unless an authorized technical decision demonstrates that it removes more complexity than it adds.
13. Checkout is a representative Semantic Validation subject, not the centre of the architecture.

#### 4.1.3 Reference Contract

A Reference Contract is a logical governance requirement. It must identify:

| Property | Requirement |
| --- | --- |
| Authoritative target | Identify the referenced formal rule, condition, Outcome, Resolution Strategy, disclosure constraint, capability, route, resolver, notification authority, audit owner, or acceptance owner. |
| Target owner and authority | Identify who owns the target and the authority under which it applies. |
| Reference purpose | Explain why the communication depends on the target. |
| Dependency or supersession identification | Make the applicable dependency and any replacement or supersession discoverable without prescribing technical keys. |
| Authority retention | State that the source owner retains authority. |
| Referential validity | Permit missing, replaced, or superseded references to be identified during review and alignment. |
| Revalidation | Identify the source owner responsible for current condition or action-availability revalidation. |
| Permitted projection | State what DOC-07 may communicate or summarize. |
| Prohibited embedded content | Exclude eligibility expressions, calculations, authorization logic, route decisions, resolver implementation, risk/security decisions, and executable amount, threshold, funding, or configuration rules. |

Reference validity does not establish current authorization, route availability, payment or evidence state, risk/security permission, resolver result, or validity of stored Copy, Locale, Presentation, or Notification data. Technical reference syntax, JSON, schema, runtime keys, database structures, error codes, and fallback algorithms remain outside DOC-07.

#### 4.1.4 Registry Contract

`Registry Contract` is an authority declaration and discoverability rule, not a physical registry or application.

| Property | DOC-07 requirement |
| --- | --- |
| Owner | Identify the accountable owner of the governed communicated meaning or mapping. |
| Authority | State the material communication authority being declared. |
| Reference Purpose | Connect the communication to source-owned conditions, capabilities, presentation, notification, runtime, and acceptance owners. |
| May Reference | List the permitted authoritative target types. |
| May Be Referenced By | Identify permitted consuming documents or later authorized implementation material. |
| Must Not Define | Exclude source business logic, routes, notification triggers/delivery, technical schemas, Admin roles, and lifecycle status. |
| Authority Retention | Preserve every referenced source owner's authority. |
| Version Policy | Require governed replacement or supersession when meaning changes; final version syntax remains deferred. |
| Change Policy | Require the canonical Workflow, owner review, impact analysis, and later authorized alignment. |

#### 4.1.5 Bounded Domain Slices

A Bounded Domain Slice is a navigation, composition, coverage, transition, or validation view over authoritative contracts. It may assemble references and show domain coverage, but it must not duplicate, redefine, or independently own referenced Semantic, Disclosure, CTA, or source rules.

A genuinely domain-specific Semantic may remain domain-specific, but it must have one authoritative contract owner before the Slice references it. Checkout may be used as a representative validation subject without producing a complete Checkout message inventory or expanding unrelated Refund, Settlement, Payout, Admin Approval, or Account Linking inventories.

#### 4.1.6 Prototype Boundary

Semantic, mandatory Disclosure, prohibited meaning, CTA intent/type, Reference/Registry governance, Domain Slice boundaries, and logical traceability are prototype-independent and may be governed before final UI evidence exists.

Exact Copy, final CTA labels and hierarchy, surface, component, slot, responsive treatment, visual prominence, final focus/announcement behavior, and final Presentation Mapping remain prototype-dependent where current evidence is insufficient. `Defer for Prototype` must not conceal an unresolved Semantic, Disclosure, prohibited meaning, or CTA intent.

---

## 5. Product Language Rules

### 5.1 Allowed Language

PayPlus may use language such as:

- bill payment;
- card-funded payment;
- pay eligible bills by card;
- pay eligible invoices and fees within an accepted controlled Bill Category, or pay through the separate Rent journey, by card;
- pay a Payment Obligation arising from an accepted controlled Bill Category or the separate Rent journey;
- pay rent by card where supported;
- payment to approved payee;
- authoritative Bill source with the Declaration and attached Evidence required by its tier, or an authoritative Rent source with mandatory attached Evidence;
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

## 6. Retired Request-Origin Labels

Request-origin labels, payee-created request content and recipient-side review language are retired from active MVP. They do not define an outcome, message, CTA, route, notification, reader, adapter or fallback. Append-only revision history remains provenance only.

---

## 7. Payer Review Disclosure

Before payment authorization, the payer must be shown a clear payment summary.

Required fields:

| Field | Requirement |
| --- | --- |
| Payee | Show approved payee name or display name. |
| Source context | Show owner-approved source and economic-Payee facts without implying a participant relationship or Payee action. |
| Category | Show the selected accepted controlled Bill Category or separate Rent context; no additional Category is implied. |
| Amount | Show payment amount. |
| Service fee | Show payer fee where applicable. |
| Total charge | Show final amount charged to the payer. |
| Payment method | Show selected card or selected split-card payment profile with masked funding summary. |
| Multi-card split | If applicable, show split amounts, masked card summaries, and any action-required profile issue before authorization. |
| Evidence | Where attached Evidence is present or required, show the owner-approved summary or accessible view subject to privacy rules; Tier 1 Bills must not imply that attached Evidence exists. |
| Verification status | Show role-appropriate evidence status where action is needed, such as pending correction, pending review, duplicate warning, or rejected evidence. |
| Timing | Show expected processing, settlement, and payout timing where relevant. |
| Refund/cancellation note | Show applicable high-level limitations or policy link. |
| PayPlus role | Explain that PayPlus facilitates payment of an eligible Bill/Rent Payment Obligation to an approved economic Payee. |

The payer must be able to cancel or go back before authorization.

---

## 8. Payer Authorization

### 8.1 Authorization Action

Every applicable Provider Submission requires current payer authorization after the payer has reviewed the applicable current facts and consequences. Authorization applies only to that Provider Submission.

A prior Checkout review, Payment Profile selection, card selection, earlier Funding Leg authorization, provider return, Resume action, notification, or saved instruction must not silently authorize a later Provider Submission. Revalidation or a material change may require renewed review and authorization before execution continues.

The authorization action must be explicit. Adaptive Checkout presentation may combine, separate, or omit presentation steps according to the current valid task; it must not be converted into one mandatory fixed final screen.

The authorization action should not be preselected, hidden, implied by source or Evidence viewing, or bundled with unrelated consent.

Payment passcode entry is a separate payer confirmation step before payment authorization proceeds; it is not payer authorization itself. DOC-09 owns payment admission and payer authorization, DOC-14 risk triggers/actions, DOC-15 privacy conditions, DOC-17 provider/cardholder challenge contracts, and DOC-19 mechanism-neutral security enforcement.

If the payer creates a deferred Payment Instruction, content must make clear that payment has not yet been submitted to the PSP/acquirer and that a later `Pay Now` action invokes the DOC-09 Checkout Resolver. The instruction does not identify a predetermined Checkout or carry forward payer authorization.

If payment quote, promotion quote, card eligibility, fee, timing, or other material terms are revalidated when the payer returns, the updated terms must be shown before submission.

If a saved split-card profile is incomplete because one card is removed, expired, suspended, invalid, or otherwise unavailable, wording must explain that payment cannot proceed until the affected card is replaced, removed, or updated.

### 8.2 Authorization Statement

The authorization Semantic and Disclosure Contracts must communicate, for the applicable next Provider Submission:

- the payer's deliberate authorization intent;
- the applicable authoritative source context, without implying that source establishment or Evidence itself authorizes payment;
- the current Funding Leg obligation-funded amount and the applicable payer charge supplied by their owners;
- the selected masked funding method or methods;
- material fee, benefit, destination, timing, evidence, and changed-term consequences supplied by their owners;
- that authorization is distinct from submission, provider evidence, confirmed Payment, full Checkout funding, Settlement, and Payout;
- that another Provider Submission requires its own applicable authorization; and
- that an unavailable or disabled authorization action must use an owner-approved explanation or resolution without exposing protected internal reasons.

For a deferred Payment Instruction, the governed meaning must state that the instruction is being saved and that no immediate card charge or Provider Submission is implied.

The exact authorization statement, CTA label, surface, hierarchy, and presentation remain `TBD` pending prototype evidence and Legal / Compliance / Payments / Product review. This deferral does not postpone or weaken the presentation-independent authorization semantics above.

### 8.3 Authorization Record

PayPlus must preserve evidence of what the payer was shown and accepted for each applicable authorization. The evidence must remain logically traceable to:

- the Payer and applicable authoritative source context;
- the applicable Checkout, Funding Leg, and Provider Submission references supplied by DOC-09;
- the Semantic, Disclosure, and CTA Contracts;
- the approved Copy and Locale Variant;
- the Presentation Mapping used;
- applicable amount, fee, benefit, masked funding, destination, timing, evidence, quote, policy, and material-change references supplied by their owners;
- the authorization occurrence, timestamp, and result; and
- any applicable Notification template or channel variant without treating notification state as authorization evidence.

DOC-07 defines this user-facing evidence intent. DOC-09 retains payment and authorization-rule ownership. DOC-18 owns the reviewed business occurrence, historical-basis, lineage, audit-meaning and explainability handoff; final fields, schema, machine events, correlation design, storage, and implementation remain separately gated.

---

## 9. Payer-Authorization Content Boundary

DOC-07 may describe the Payer's owner-approved Payment Instruction, Checkout, payment authorization, confirmed result and owner-supplied safe next handling. It must not create an economic-Payee action, acceptance, reminder, Request delivery, recipient library or reciprocal communication. Payer authorization is governed by DOC-09 and product context; DOC-07 provides only the approved user-facing communication mapping.

DOC-07 may communicate owner-approved source capture, Declaration, tier-dependent attached Evidence, verification, Checkout, Payer authorization, Payment Result, optional post-Payment Save, Activity/Receipt and source Archive meaning. Tier 1 content must not imply mandatory attached Evidence; Tier 2/3 content must distinguish Evidence presence from acceptance; Rent content must preserve mandatory attached Evidence and acceptance-before-Payment. DOC-07 must not create Category-specific rules, a Payee action, recipient library, link, delivery, acceptance, reminder or reciprocal communication. Exact expression remains deferred to the applicable DOC-07 slice and source-owner input.

For Bills, the communication contract keeps Declaration separate from Evidence, Save, Payer authorization, Payment and Payout. Add Bill communicates reviewed declared facts and deliberate confirmation before the distinct Save-admission outcome. An owner-confirmed non-material edit may communicate ordinary Save; a material edit communicates only the owner-defined proportionate reconfirmation. A Pay action with unchanged declared facts communicates current Payment terms and the separate applicable authorization, not a repeated full Declaration. The recording handoff distinguishes four occurrence contexts: Add Bill; a Pay progression that establishes a new Bill/Rent source; an applicable owner-defined Bill/Rent source setup; and a material change to a Saved Bill/Rent source. Exact wording, legal sufficiency and reconfirmation treatment remain with their owners. DOC-19 may enforce the relevant security boundary but does not change these product meanings or select Copy.

---

## 10. Rent and Tenancy Content

Rent and tenancy payments are MVP scope but require enhanced content controls.

Rent-related screens should explain:

- attached Rent Evidence is always required and its owner-controlled acceptance remains a Payment gate;
- extracted tenancy data may include sensitive fields that are not all displayed in the UI;
- landlord, property manager, or payee verification may be required;
- payer-landlord or payer-property relationship checks may apply;
- limits, manual review, duplicate detection, and risk review may apply;
- duplicate or reused tenancy evidence may trigger warning, hold, or review;
- payout may be delayed or blocked if checks fail;
- each applicable Payment requires the owner-governed current authorization; this document does not define a recurring authorization model.

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

Exact fee rates and allocation remain `To be confirmed` by Product / Commercial and the applicable payment owners. Promotion calculation and entitlement rules belong in DOC-13; current payment, quote, and action eligibility belongs in DOC-09; refund and reversal rules belong in DOC-11. DOC-07 retains the required user-facing disclosure of applicable fees, benefits, total charge, allocation meaning, refundability, and user consequences, but it must reference rather than define those source rules or their configuration mechanisms.

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
- that an incomplete Checkout may already contain one or more confirmed Payments while its Checkout Target remains partly unfunded;
- that Checkout completion, Payment confirmation, Payment Obligation Effective Coverage, and downstream Payout are separate concepts owned by DOC-09 and DOC-10 as applicable;
- whether the payer must re-authorize after changing card split amounts.

The confirmed MVP maximum is 6 cards per payment/profile. `OQ-07-004` remains `Answered: 6` and must not return to `Open` or `TBD`.

Any narrower partner-, risk-, or category-specific restriction, its configuration mechanism, operational authority, and technical enforcement remain `To be confirmed` by Payments / Risk / Product / Operations and their formal owners. DOC-07 owns user-facing disclosure of the applicable maximum and any current narrower restriction; it does not own eligibility, restriction logic, configuration, Admin authority, or enforcement.

---

### 12.1 Payment Instruction and Reminder Disclosure

PayPlus must distinguish four user-facing concepts:

| Concept | User-Facing Meaning | Action Destination |
| --- | --- | --- |
| Normal due-date reminder | Reminder based on bill, rent, or obligation due date; payment flow has not started. | Bill/rent/obligation detail. |
| User manual reminder | Reminder date or offset set by user for a bill, rent, or obligation. | Bill/rent/obligation detail. |
| Payment Instruction action alert | The user deliberately created a pay-later arrangement and action is now due. | An instruction-related notification enters `NOTIFICATION-DETAIL`; after current revalidation, an owner-approved CTA may invoke the DOC-09 Checkout Resolver. |
| Incomplete Checkout continuation alert | Immediate payment execution started but the Checkout Target remains partly unfunded. This is not a Payment Instruction. | The preserved Checkout context. |

Bill/rent reminder cycles, custom reminder dates, reminder toggles, and reminder deactivation must be described as reminder tools only. They must not imply automatic recurring payment, stored authorization, card authorization, gateway submission, payout readiness, or payment completion.

If a reminder is linked to a recurring bill/rent frequency, the user-facing wording should distinguish recurring reminder scheduling from recurring payment authorization. Reminder route behavior belongs in DOC-06. Notification channel and template wording belongs in DOC-08.

Payment Instruction wording must explain:

- selected funding date or action date;
- intended amount and funding arrangement where applicable;
- expiry or required action deadline;
- that amount, promotion, card eligibility, fee, destination, or timing may need to be revalidated before Provider Submission;
- that `Pay Now` invokes the DOC-09 Checkout Resolver without predetermining New or Resume Checkout identity, creating silent funding/submission, or carrying forward payer authorization;
- that every applicable Provider Submission still requires current payer authorization.

Incomplete Checkout wording must explain:

- the immutable Checkout Target;
- confirmed Payments and the remaining target amount;
- expiry of the continuation capability;
- that closing or expiry does not cancel or rewrite confirmed Payments or Payment Applications;
- that downstream Settlement and Payout treatment belongs to DOC-10 and does not determine whether the original Checkout is complete.

---

## 13. Authorization, Payment, Settlement, and Payout Meaning

PayPlus must distinguish the following source-owned semantic conditions. They are not final user-facing labels, persistent-status definitions, or implementation enums.

| Semantic condition | Required communicated meaning |
| --- | --- |
| Payer authorization supplied | The payer authorized only the applicable Provider Submission. Authorization is not submission, provider evidence, confirmed Payment, full funding, Settlement, or Payout. |
| Provider Submission initiated | A provider-bound attempt was initiated. Its result is not established merely because the user left or returned from a provider surface. |
| Provider evidence unresolved | No definitive success or failure may be communicated until authoritative evidence is evaluated. Unsafe retry or alternate submission must not be implied. |
| Funding Leg successfully confirmed | The applicable confirmed Funding Leg produces one immutable Payment under DOC-09. Other legs and Remaining Checkout Target remain separate. |
| Checkout partially funded | Confirmed value is above zero and below Checkout Target. Confirmed Payments remain authoritative; unconfirmed value and Remaining Checkout Target remain distinct. |
| Checkout fully funded | Confirmed obligation-funded value equals Checkout Target. This does not imply Settlement or Payout completion. |
| Settlement pending or completed | Use only the current Settlement meaning supplied by DOC-10; do not infer it from authorization, provider return, Payment, or Checkout funding. |
| Payout pending or completed | Use only the current Payout meaning supplied by DOC-10 and the applicable payout owner. |

For a Tier 2 Bill, a confirmed Payment, the current Evidence condition, and a Payout hold or release remain distinct communicated truths. Receipt or proof communicates confirmed Payment and must not communicate Payout completion unless the Payout owner has confirmed it. Bill detail may explain a current Payout hold using owner-supplied safe context; ordinary Evidence lifecycle is not recast as payment-lifecycle Activity. `Transfer pending` is not a default expression for an Evidence-acceptance Payout hold because it could imply that Payout execution has begun. Exact safe wording, including any Payer action or no-action presentation, remains subject to DOC-07, DOC-08, DOC-10, privacy, risk and applicable owner input; this section creates no notification or new user-facing status.

PayPlus may disclose working settlement and payout assumptions only when the applicable PSP/acquirer, bank, payout, risk, legal, partner and reconciliation owners have confirmed them.

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

| Condition | Disclosure Requirement |
| --- | --- |
| Before authorization | Show high-level refund, cancellation, and dispute limitations where material. |
| Provider evidence unresolved | Explain the known pending facts without claiming success or definitive failure, and do not imply a safe retry or alternate submission unless the owner currently permits it. |
| Authoritatively unsuccessful attempt | Explain the affected attempt or Funding Leg, that it produced no Payment, any confirmed value from other legs, any separate unconfirmed value, Remaining Checkout Target, and only an owner-permitted recovery after revalidation. |
| Partial funding | Preserve confirmed Payment facts and distinguish confirmed value, unconfirmed value, Remaining Checkout Target, continuation availability, and closing consequences. |
| After cancellation | Explain whether payment was not processed, reversed, or pending operational review. |
| Refund requested | Explain request status and expected review path. |
| Dispute opened | Explain that the case is under review and may require evidence. |
| Chargeback received | Show role-appropriate status and support path where applicable. |

Do not expose internal risk reasons or sensitive admin notes to users unless approved.

---

## 15. Privacy and Data Collection Notices

PayPlus collects approved personal, Payment, Payee, business, identity, attached-Evidence where present or required, and transaction data to support onboarding, payment processing, fraud prevention, compliance, support, reporting, tax, audit, and record retention. Raw PAN, CVV/CVC, track data and prohibited sensitive-authentication values remain outside PayPlus collection and retention.

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
- explain account-closure blockers, cancellation before finalization, login termination after completion, and the accepted indefinite-retention direction without implying deletion, while preserving DOC-15 and Legal/Privacy lawful-scope, required-exception and restricted-data qualifications;
- distinguish directly editable account fields, governed privacy/access/correction requests, and account closure without implying destruction of an underlying PayPlus record;
- distinguish optional direct-marketing, personalization, and approved partner-data-use choices from required service, payment, security, risk, compliance, tax, audit, dispute, and retention processing;
- explain that data export uses protected in-app access and that privacy-request service timelines and legal outcomes remain subject to the approved privacy process.
- explain only source-owner-approved economic-Payee and destination disclosures; DOC-07 must not create a destination library, readiness label, source-version, request or change-warning contract.

### 15.2 Authentication Bounded Domain Slice

PayPlus must maintain an Authentication Bounded Domain Slice for `ENTRANCE-ROOT`, `AUTH-LOGIN-FAST`, `AUTH-LOGIN-FULL`, `AUTH-RECOVERY`, `AUTH-REGISTRATION`, `ACCOUNT-ACTIVATION`, and their approved child flows.

The Slice is a reference-only navigation, coverage, transition, and validation view over authoritative contracts. It must not become a second Semantic owner, redefine route behavior, copy source-owned business/security logic, or require one wide record that couples Semantic, exact Copy, Surface, CTA, technical mapping, audit, and acceptance maturity.

The capability-aware Outcome and Resolution relationship remains confirmed. The Slice must keep these concepts distinct:

- an owner-defined **Outcome**, representing the operation or evaluation result;
- an owner-permitted **Resolution Strategy**, representing the current continue, restart, redirect, wait, Support, or stop handling;
- a DOC-07 **Semantic Contract**, **Disclosure Contract**, and **CTA Contract** governing communicated meaning;
- **Copy**, **Locale Variant**, and **Presentation Mapping** expressing accepted meaning when approved;
- a DOC-08 Notification relationship or `None` with reason;
- a DOC-18 business-occurrence, historical-basis, lineage and audit-meaning handoff, with technical correlation separately gated; and
- a DOC-20 acceptance handoff.

Multiple internal Outcomes may map to one neutral user-facing Semantic and Copy expression where separate wording would expose whether an account, identifier, credential, provider link, or security restriction exists.

The Slice must provide or reference the following layered coverage. Separate tables or views may be used when they remain linked to one authority; not every presentation-dependent or technical field must be final before the Semantic is governed.

| Layered coverage | Requirement | Current owner or handoff |
| --- | --- | --- |
| Source and context | Source requirement, owning route/domain, Outcome, actor/assurance context, and originating action. | Applicable route/domain owner. |
| Outcome and Resolution | Outcome classification, owner-permitted Resolution Strategy, eligible alternatives, and no-safe-path treatment. | Applicable route/domain/security owner. |
| Semantic and Disclosure | Required meaning, prohibited implication/reveal, disclosure level, and masking constraints. | DOC-07 with DOC-15/DOC-19 constraints. |
| CTA Contract | Action intent, owner-defined destination/capability, revalidation, safe return, and unavailable-action treatment. | DOC-07 mapping; capability/route owner retains availability and behavior. |
| Copy and Locale | Approved expression or explicit `TBD`; meaning-preservation and variable constraints. | DOC-07; final Copy/Locale review remains open. |
| Presentation Mapping | Owner-defined surface/component/slot reference, hierarchy, accessibility, and responsive evidence or explicit `TBD`. | DOC-06B surface owner with DOC-07 mapping. |
| Notification | DOC-08 relationship or `None`; an in-flow message is not automatically a Notification. | DOC-08. |
| Runtime and audit | Business occurrence, historical action basis, lineage and audit-meaning handoff, plus separately gated technical representation or explicit `TBD`. | DOC-18 for the reviewed business contract; future Engineering/Data authority for technical representation; DOC-19 only for applicable security-control constraints. |
| Support and operations | Controlled Support/Admin visibility and handoff without granting an override. | DOC-21/DOC-22. |
| Acceptance | Semantic, negative-path, accessibility, localization, revalidation, and implementation evidence or explicit `TBD`. | DOC-20 and applicable acceptance owners. |

The Slice must cover, at minimum:

- registration attempt interruption, expiry, identifier conflict, and atomic account-creation failure;
- provider-login unavailable, unlinked, conflict, cancellation, and authentication failure;
- password-login failure, recovery-link expiry, and recovery failure;
- phone format, occupied-number, OTP delivery, resend, expiry, incorrect-code, attempt-limit, and replacement failure;
- identity capture interruption, processing, provider failure, PayPlus-policy failure including duplicate identity, and admin-required update;
- payment-passcode Set mismatch/failure, Change authentication/failure, Reset reauthentication/phone-OTP/recovery failure, and unknown save result;
- protected-return invalid, expired, consumed, unauthorized, or unavailable outcomes.

Exact Outcome Type IDs, Message IDs, Action IDs, approved Copy, Locale Variants, CTA labels/hierarchy, Presentation Mappings, notification mappings, and technical mappings remain open. They must not be invented during implementation. Route or domain documents must not create competing message identifiers or copy.

DOC-06B and applicable route/domain owners retain Outcome meaning, permitted Resolution Strategies, route placement, destination, and return behavior. DOC-07 owns the governed user-facing Semantic, Disclosure, CTA, approved Copy, Locale constraints, and Presentation references. DOC-08 owns Notification identity, trigger, recipient, channel eligibility, templates, delivery, retry, delivery evidence, and read/archive behavior. DOC-18 owns the business occurrence, historical basis, lineage, audit-meaning and explainability handoff; exact correlation records and machine event mapping remain separately gated. DOC-17 owns provider contracts; DOC-19 owns mechanism-neutral authentication, protected-value, retry/replay, session/device and access-enforcement controls while exact mechanisms remain open. DOC-20 owns detailed acceptance, DOC-21 owns Support procedure, and DOC-22 may execute only expressly owner-permitted future Admin operations.

#### 15.2.1 Authentication Slice Order

DOC-07 should be authored by coherent slice after the owning route behavior is stable:

1. `AUTH-RECOVERY`;
2. `AUTH-LOGIN-FAST` and `AUTH-LOGIN-FULL`;
3. `AUTH-REGISTRATION`;
4. `ACCOUNT-ACTIVATION`;
5. `PHONE-VERIFICATION`, `IDENTITY-VERIFICATION`, and `PAYMENT-PASSCODE-SETTINGS`;
6. authenticated Set Password and Primary Email Change after their detailed route-local flows are defined.

This order does not change route ownership or implementation priority. It limits duplication and allows the anonymous Recovery disclosure model to be reviewed before reuse across the AUTH family.

#### 15.2.2 `AUTH-RECOVERY` Preliminary Outcome and Resolution Inventory

The following inventory preserves the approved DOC-06B product behavior without assigning final IDs or copy:

| Situation / Outcome Class | Owner-Approved Resolution | Presentation Intent | Notification Handoff |
| --- | --- | --- | --- |
| Recovery request accepted for neutral processing | Continue | Check Your Email presentation that does not confirm account, password, provider-link, restriction, or delivery eligibility. | Reset-link delivery treatment TBC in DOC-08. |
| Reset link valid and password reset permitted | Continue | Silent validation followed by New Password. | None by default. |
| Link invalid, expired, consumed, or reused | Restart | Safe resolution treatment permitting Request New Link or Return to Login. | None by default. |
| Provider-only account has no PayPlus password | Redirect | Return to provider login or controlled Support without anonymous first-password creation. | None by default. |
| Email unavailable and another linked method is safely usable | Redirect | Offer Try Another Login Method without disclosing unverified linkage details. | None by default. |
| No approved self-service method remains | Support | Begin controlled Support recovery. | Case acknowledgement/action-required treatment TBC in DOC-08. |
| Support cannot establish required ownership assurance | Stop | Safe Recovery Not Permitted treatment without promising account recovery. | TBC only if DOC-08 defines a material security communication. |
| Temporary restriction, provider unavailability, or reset result unconfirmed | Wait / Redirect | Safe wait, retry, alternative-method, return, or Support treatment according to current capability. | None unless DOC-08 approves a separate event. |
| Password reset completed | Redirect | Recovery Complete followed by Return to `AUTH-LOGIN-FULL`; do not auto-login. | Mandatory credential-change security communication; exact DOC-08 mapping TBC. |

Multiple internal Outcomes may map to the same public-neutral message. The exact copy, masking, CTA hierarchy, Outcome/Message/Action IDs, and notification mappings require the [`DOC-07 Design Specification Specialist Guide`](../documentation-system/payplus-doc-07-design-specification-specialist-guide.md) and applicable security, privacy, notification, data, testing, Support, and admin reviews.

---

## 16. Notification and Communication Content Boundary

DOC-07 owns governed Semantic, Disclosure, CTA, and approved Copy requirements within its accepted scope. Subject to TA-21, the exact canonical/base-Copy relationship with DOC-08-owned channel-template expression remains `Open`. DOC-08 owns Notification:

- identity and event definition;
- trigger and eligibility;
- recipient;
- channel eligibility and preference treatment;
- channel-template expression;
- delivery and retry;
- delivery evidence;
- read/archive behavior;
- receipt and statement communication rules; and
- mandatory `NOTIFICATION-DETAIL`-first entry for instruction-related notifications.

Every instruction-related notification must enter `NOTIFICATION-DETAIL`. Notification Detail revalidates current state, authenticated payer, permission, target, and action availability before an owner-approved current CTA may invoke the DOC-09 Checkout Resolver. Notification content, delivery, read/archive state, and stored snapshots do not establish current Checkout eligibility, payer authorization, Provider Confirmation, Payment, or payment result.

Any future mapping between DOC-07-owned requirements and DOC-08-owned channel-template expression remains subject to TA-21 and must not transfer Notification ownership to DOC-07.

**Open decision — canonical/base Copy and channel-template relationship:** The boundary among DOC-07 canonical Semantic and base-Copy authority, DOC-08 channel-template expression, Locale and platform variants, version relationships, and approval relationships remains `Open`. Owners: Product / Content / DOC-08 Owner / Design / Legal / Compliance as applicable. This open item does not reopen DOC-08 ownership listed above or the mandatory Detail-first entry contract.

### 16.1 HOME-ROOT Content and Disclosure Contract

DOC-07 owns the Traditional Chinese, Simplified Chinese, and English presentation of the following HOME-ROOT semantics. This section defines content meaning and disclosure boundaries; DOC-06B owns placement, interaction, navigation, and route-level state.

#### Greeting

- The presentation must express `Morning` for local time `05:00–11:59`, `Afternoon` for `12:00–17:59`, and `Evening` for `18:00–04:59`.
- Server time may be used only with an applicable timezone. When no applicable timezone is available, the presentation must use an approved neutral greeting and must not infer a local-time band.
- The displayed-name precedence is user-defined Nickname; `Mr.` or `Miss` plus eKYC surname where applicable title data exists; surname alone where the surname exists without an applicable title; and no displayed name otherwise.
- The visual presentation is normally one line. Assistive technology receives the complete rendered greeting even where visual adaptation is required.
- The greeting must not imply a navigation action.
- Exact approved Traditional Chinese, Simplified Chinese, and English expressions remain governed Copy and Locale Variants under this document; technical time, timezone, and account-data mechanics remain with their formal owners.

#### Important Notice and Recent Activity expression

- Important Notice content must preserve the owning source's current severity, category, required action, and safe-disclosure meaning. A Home dismissal must not be worded or presented as `Read`, `Resolved`, `Expired`, `Withdrawn`, or as a change to the owning business state.
- The notice body opens canonical `NOTIFICATION-DETAIL`; an Action Button names and opens only the current source-provided destination. DOC-08 retains notification identity, lifecycle, Inbox-record, and delivery ownership.
- Promotions, Rewards, marketing, and ordinary feature announcements are not Important Notice content by default.
- Recent Activity presentation maps only the owner-published completed outcome. Refund and Reversal may share one Home presentation treatment but must not be described as the same source outcome.
- Amount presentation preserves the canonical funds-flow direction published by DOC-09, DOC-10 or DOC-11. Copy or visual treatment must not infer or reverse the sign from Payer/economic-Payee context.
- Exact message, CTA, status-label, masking, and Locale Variant work remains bounded by the applicable source owner, DOC-07 approval, and DOC-15 safe-disclosure rules; HOME-ROOT does not create new source outcomes or notification meanings.

---

## 17. Communication Control and Change Authority

The Authority Gradient permits greater expression flexibility in later layers but never permits a later layer to contradict an earlier authoritative layer. `Propose`, `Approve`, and `Activate` are separate authorities:

- **Propose** means generating or suggesting an expression or mapping.
- **Approve** means confirming that it preserves the authoritative contracts and applicable review requirements.
- **Activate** means making an already-approved variant effective through a separately authorized future mechanism.

AI may propose bounded expression but must not redefine intent, approve its own output, or activate content.

| Layer | Owner | Authority | Mutability | Risk | Generatability |
| --- | --- | --- | --- | --- | --- |
| Source condition, Outcome, or Resolution | Applicable route/domain owner | Product/domain truth and permitted handling | Low | Critical | AI may summarize only. |
| Semantic Contract | DOC-07, constrained by source owners | User-relevant communicated meaning | Low | Critical | AI may propose expression, not meaning. |
| Composition Rule | DOC-07 | Non-executable assembly structure | Controlled | High | AI may propose within approved contracts. |
| Disclosure Contract | DOC-07, constrained by the obligation owner | Mandatory communicated meaning | Low | Critical | AI may propose expression only. |
| CTA Contract | DOC-07, constrained by the capability/route owner | User-facing action intent and reference | Low | Critical | AI may propose label or mapping only. |
| Copy | DOC-07 within its accepted scope; notification-channel expression remains subject to TA-21 | Approved expression | Controlled | Variable | Human or AI may propose. |
| Locale Variant | DOC-07 within its accepted scope, with applicable locale/privacy review; notification-channel expression remains subject to TA-21 | Meaning-preserving localized expression | Controlled | Variable; high for material content | Qualified human or AI may propose. |
| Presentation Mapping | DOC-07 mapping; surface owner defines the surface | Placement of approved expression | Higher | Medium to high | Design, Content, or AI may propose. |

This matrix defines logical responsibility boundaries only. Formal documentation ownership, review, approval, and release remain governed by DOC-00 and the canonical PayPlus Documentation Development Workflow. No operational activation authority is granted by DOC-07. Final operational actors, mechanisms, permissions, publication controls, and enforcement remain `TBD` under DOC-22 and applicable technical owners.

| Layer | Propose | Approve | Activate | Approval class | Audit unit | Rollback unit |
| --- | --- | --- | --- | --- | --- | --- |
| Source condition, Outcome, or Resolution | Source owner or bounded analysis | Source owner and Founder where material | Effective only through the owning source under DOC-00 and the canonical Workflow. | Material source decision | Source requirement or decision | Accepted prior source version |
| Semantic Contract | DOC-07 owner or bounded analysis | DOC-07 owner, source owner, required reviewers, and Founder where material | Effective only through DOC-00 and the canonical Workflow. | Material communication meaning | Contract provision | Superseded prior contract |
| Composition Rule | Content/Design or bounded AI | DOC-07 owner and affected reviewers | Effective only through DOC-00 and the canonical Workflow. | Governance/content rule | Rule provision | Prior approved rule |
| Disclosure Contract | DOC-07 and applicable specialist inputs | Applicable owners/reviewers and Founder where material | Effective only through DOC-00 and the canonical Workflow. | Financial/legal/privacy/risk-sensitive | Disclosure provision | Prior approved disclosure |
| CTA Contract | DOC-07, Content, or Design | DOC-07 plus capability/route/domain owner | Effective only through DOC-00 and the canonical Workflow; current action still requires source-owner revalidation. | Protected-action mapping | CTA provision | Prior approved mapping |
| Copy | Human or AI | DOC-07 owner and risk-proportionate reviewers | No operational activation authority granted; future mechanism and role TBD. | Copy/content approval | Copy variant | Prior approved variant |
| Locale Variant | Qualified human or AI | DOC-07 and applicable locale/risk reviewers | No operational activation authority granted; future mechanism and role TBD. | Localization/content approval | Locale variant | Prior approved Locale Variant |
| Presentation Mapping | Route/Design/Content owner or AI | Surface owner plus DOC-07 where meaning may change | No operational activation authority granted; future mechanism and role TBD. | UX/content approval | Mapping provision | Prior approved mapping |

Service-fee rates and allocation, promotion/entitlement calculations, the confirmed six-card maximum, narrower card restrictions, eligibility, and policy rules are source facts, not editable communication semantics. Communication changes may express only current owner-supplied values and constraints.

Final Admin roles, permissions, technical enforcement, publication workflow, approval screens, activation mechanism, technical representation, and implemented rollback remain `TBD` under the applicable owner, Security, Operations and separately authorized Engineering/Data work. DOC-22 may execute only a specifically owner-permitted operation; DOC-18 supplies business-recording inputs only. This section grants no Admin or implementation authority.

---

## 18. Audit and Evidence Requirements

PayPlus must be able to prove what the user saw and accepted at key moments.

The logical architecture must preserve traceability across:

```text
Authoritative Source Contract
    -> Semantic Contract
    -> Disclosure Contract
    -> CTA Contract
    -> approved Copy
    -> Locale Variant
    -> Presentation Mapping
    -> applicable Notification template or channel variant
    -> user-facing authorization or acceptance evidence
```

The traceability requirement is logical and applies even where final Copy, Locale, Presentation, runtime, or acceptance evidence remains pending. DOC-18 supplies the reviewed business-recording and explainability contract. Physical schema, runtime/database representation, storage mechanics, technical version keys and audit-event implementation require separate future Engineering/Data authority; operational rollback remains an owner-permitted DOC-22 handoff.

Required audit evidence includes:

| Event | Evidence |
| --- | --- |
| Account registration | Terms/privacy version where applicable. |
| Authentication outcome | Outcome Type ID, selected Resolution Strategy, Message ID, originating route/action, occurrence/correlation ID, disclosure level, CTA/destination, timestamp, and permitted technical reason category without secrets. |
| eKYC/KYB submission | Consent, provider handoff, submission event, and status. |
| Source capture | Authoritative-source reference, Bill Category or separate Rent context, Declaration/confirmation reference, and attached-Evidence notice only where Evidence is present or required. |
| Evidence verification | Where attached Evidence is present or required, OCR/autofill notice, extracted-field review, user correction, duplicate warning, verification outcome and owner-supplied handling condition; Tier 1 Bills do not require an Evidence-verification record. |
| Payer review | Current source/payment disclosure version shown to Payer. |
| Payment authorization | Applicable Provider Submission; Semantic, Disclosure, and CTA Contract references; approved Copy/Locale/Presentation references; current amount, fee, benefit, masked funding, destination, timing, evidence and material-change references; timestamp; and result. |
| Promotion authorization | Promotion quote, applied discount, service-fee benefit, coupon/voucher selection, reward entitlement, and related wording shown before authorization where applicable. |
| Multi-card authorization | Card split, total charge, per-card amount, and reauthorization event where applicable. |
| Economic-Payee and destination | Owner-supplied disclosure reference, masking boundary and authorization evidence where applicable; no library, recipient notification or source-version contract is created. |
| Refund/dispute/chargeback case | User-facing status, case messages, evidence submitted, and admin actions. |

DOC-18 owns the business-recording, historical-basis, lineage, audit-meaning and explainability obligations for this evidence. Detailed event schema, physical version keys, storage, runtime linkage and audit-event implementation remain future separately authorized Engineering/Data work. Operational activation, rollback, and administrative audit workflow belong in DOC-22 only where a source owner specifically permits them. These handoffs do not transfer user-facing Semantic authority.

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
| OQ-07-003 | What exact fee, promotion, coupon, discount, refund, and reversal wording is required, and what separately authorized operational configuration should later be supported? | Product / Commercial | Open |
| OQ-07-004 | What maximum number of credit cards per payment/profile should be shown at launch? | Product / Payments | Answered: 6 |
| OQ-07-005 | What wording should explain owner-confirmed upstream settlement and payout timing without overpromising? | Payments / Legal / Product | Open |
| OQ-07-006 | What category-specific disclosure is required for rent and tenancy payments? | Legal / Risk / Product | Open |
| OQ-07-007 | What refund, cancellation, dispute, chargeback, and reversal policy links or short summaries must be shown before authorization? | Operations / Legal / Product | Open |
| OQ-07-008 | What content approval workflow is required for legal, payment, privacy, commercial, or risk-sensitive copy changes? | Project Owner / Compliance | Open |
| OQ-07-009 | What wording should explain OCR/autofill, user correction responsibility, duplicate/reused evidence warning, and sensitive extracted-field handling? | Product / Legal / Privacy | Open |
| OQ-07-010 | What wording should explain promotion quotes, coupon/voucher eligibility, miles rewards, membership benefits, expiry, and entitlement limits before authorization? | Product / Commercial / Legal | Open |
| OQ-07-011 | What wording should explain SMS OTP, new-device 2FA, dormant-login reauthentication, payment passcode, material-change confirmation, and security notifications? | Product / Security / Legal | Open |
| OQ-07-012 | What exact wording should explain deferred payment instruction, pending funding legs, partial funding, partial payout, remaining unpaid amount, and payment completion boundary? | Product / Legal / Payments | Open |
| OQ-07-013 | What wording should explain quote expiry, promotion reservation, recalculation, and changed checkout terms when a payer returns to a deferred payment instruction? | Product / Legal / Growth | Open |
| OQ-07-014 | What exact Outcome Type IDs, Resolution Strategy codes/mappings, Message IDs, approved messages, disclosure levels, CTA labels, destinations, notification treatment, and technical/event mappings should populate the Authentication Bounded Domain Slice and its linked contracts? | Product / Content / Design / Security / Privacy / Support | Open; layered mechanism and coverage confirmed |

### 20.1 Communication Architecture Open Items

| Open item | Owner | Status |
| --- | --- | --- |
| TA-21 boundary among DOC-07 canonical Semantic/base Copy, DOC-08 channel-template expression, Locale/platform variants, version relationships, and approval relationships. This does not reopen any DOC-08-owned notification behavior. | Product / Content / DOC-08 Owner / Design / Legal / Compliance | Open |
| Final authorization statement, CTA label, hierarchy, surface, and presentation. | Legal / Compliance / Payments / Product / Design | TBD pending prototype evidence |
| Exact approved Copy and Locale Variants for governed contracts. | Product / Content / Design / Legal / Privacy as applicable | Open |
| Final Presentation Mappings, responsive treatment, focus, announcement, and visual prominence. | DOC-06B Owner / Design / Content / Accessibility | TBD pending prototype evidence |
| Exact fee and allocation authority where not established by current sources. | Product / Commercial / Payments | Open |
| Narrower partner-, risk-, or category-specific card restrictions and their configuration mechanism. | Payments / Risk / Product / Operations | Open |
| Final Admin roles, permissions, approval/activation workflow, publication controls, and operational rollback. | DOC-22 Owner / Operations / Security / Compliance | Open |
| Physical Registry/Reference representation, schema, runtime keys, version linkage, storage, audit events, and implemented rollback. | Future separately authorized Engineering / Data work using DOC-18's reviewed business contract; applicable owner plus DOC-22 for specifically permitted rollback execution | Open; DOC-18 does not currently approve the mechanism |
| Detailed acceptance, UAT, accessibility, localization, implementation, and release evidence. | DOC-20 Owner / QA / Product / Design | Open |
| Exact later impacts, if any, to the DOC-07 Specialist Guide and Outcome/Message/Notification Framework after change-impact and duplicate-definition analysis. | Documentation Lead / Product / Founder | Open; separate authorization required |

---

## 21. Acceptance Criteria

DOC-07 is acceptable when:

- user-facing product language is aligned with PayPlus positioning;
- prohibited wallet, cashout, P2P, remittance, and stored-value language is excluded;
- payer authorization requirements are explicit;
- every applicable Provider Submission requires current payer authorization without relying on a fixed final screen or prior authorization;
- payer review disclosure fields are defined;
- retired Request/Payee-user/Receiving Info runtime has no active communication requirement;
- rent and tenancy disclosure requirements are defined;
- OCR/autofill, evidence correction, duplicate warning, and evidence verification disclosure touchpoints are defined;
- fee, promotion, total charge, and multi-card disclosure requirements are defined;
- deferred payment instruction, reminder destination, partial funding, partial payout, and remaining unpaid amount disclosure boundaries are defined;
- deferred instruction quote revalidation and changed-term disclosure boundaries are defined;
- coupon, voucher, reward, miles, membership, entitlement, and expiry disclosure boundaries are defined where applicable;
- payment, settlement, and payout timing wording is cautious and accurate;
- refund, cancellation, dispute, chargeback, and reversal disclosure touchpoints are defined;
- privacy and data collection notice touchpoints are identified;
- governed material communication, ordinary-copy exclusions, and the central-contract / Domain-Slice / composition / reference / governance architecture are defined;
- Semantic, Outcome/Resolution, Composition, Disclosure, CTA, Copy, Locale, Presentation, Reference, Registry, and Authority Gradient boundaries are defined without executable business logic;
- the Authentication Bounded Domain Slice mechanism, layered coverage, ownership, and open exact-copy/ID boundary are defined;
- DOC-08 ownership and mandatory instruction-related `NOTIFICATION-DETAIL`-first entry remain explicit;
- the confirmed six-card MVP maximum remains `Answered: 6` while narrower restrictions and configuration remain open;
- HOME-ROOT Greeting, Important Notice, and Recent Activity expression boundaries preserve complete locale output, source meaning, notification separation, and canonical funds-flow direction without transferring route or business ownership to DOC-07;
- logical traceability from source authority through user-facing authorization or acceptance evidence is defined, with physical implementation deferred;
- content audit evidence is defined;
- open questions are clear and do not block continued drafting.

---

## 22. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 1.1.1 | 2026-08-27 | Aligned the four Declaration occurrence handoffs and narrowed DOC-18 to its reviewed business-recording/explainability contract without approving Copy, technical representation, mechanisms, or implementation. |
| 1.1.0 | 2026-08-22 | Drafted bounded Tier 2 Payment/Evidence/Payout communication separation and proportionate Declaration expression while preserving DOC-08 notification ownership, DOC-10 Payout truth, DOC-19 mechanism-neutral enforcement, and open Copy. |
| 1.0.1 | 2026-08-21 | Aligned payer-authorization, provider, runtime/audit and security-control handoffs with DOC-09, DOC-17, DOC-18 and the reviewed mechanism-neutral DOC-19 contract without approving Copy or mechanisms. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 0.11.1 | 2026-08-12 | Consolidated fixed-inventory, Payment Obligation, provider/rail/timing/retention and DOC-22 execution-boundary corrections without approving new Copy or CTA. |
| 0.11.2 | 2026-08-12 | Applied the Founder-settled indefinite-retention rule to disclosure meaning and account-closure/privacy-request wording without inventing Copy or a disposition mechanism. |
| 0.11.0 | 2026-08-12 | Retired active Request/Payee-user/Receiving Info communication requirements and aligned the content boundary with Payer-only, economic-Payee and owner-governed notification meaning without approving new Copy or CTA. |
| 0.10.1 | 2026-08-05 | Added the approved HOME-ROOT Greeting, Important Notice, and Recent Activity content/disclosure contract, including locale ownership, neutral greeting fallback, displayed-name precedence, notification-state separation, and canonical funds-flow-direction presentation. |
| 0.10.0 | 2026-08-04 | Drafted the accepted communication semantic architecture in DOC-07, including logical central contracts, bounded Domain Slices, layered composition, Reference/Registry governance, layer-level control, per-Provider-Submission authorization semantics, Detail-first notification entry, logical traceability, preserved six-card baseline, and explicit prototype/technical/Admin/acceptance deferrals. |
| 0.9.13 | 2026-07-31 | Aligned Request, Payment Instruction, incomplete Checkout, confirmed Payment, obligation coverage, and downstream Payout disclosure boundaries with DOC-09. |
| 0.9.12 | 2026-07-29 | Added owner-approved Resolution Strategy between Outcome and user presentation, established capability-aware AUTH slice sequencing, and added the preliminary `AUTH-RECOVERY` outcome/resolution inventory while leaving exact IDs, copy, CTA hierarchy, and notification mappings open. |
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
