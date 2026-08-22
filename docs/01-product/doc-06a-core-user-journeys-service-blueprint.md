---
document_id: DOC-06A
title: Core User Journeys & Service Blueprint
version: 1.1.0
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-08-22
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT & Release Readiness
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06A - Core User Journeys & Service Blueprint

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06A` |
| **Title** | Core User Journeys & Service Blueprint |
| **Version** | `1.1.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-22` |
| **Classification** | Internal |
| **Related Documents** | DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT & Release Readiness<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## Current Wave 2 Payer-only Journey Baseline

This is the current normative DOC-06A Founder Working Baseline. Its active Payer-only journey rules stand independently and retire mixed-role, payee-user, Request, Linking, and pre-Checkout Save behavior. Explicitly labelled non-active registers and append-only decisions or revision history preserve documentation lineage only; they do not define, supplement, or override current runtime behavior.

### Actor and journey boundary

- A Consumer User is a Payer only. The Payee is an economic recipient who may be an individual or institution/company and need not be a PayPlus User. DOC-06A does not create a Consumer Payee login, dashboard, Request or reciprocal-visibility journey.
- MVP covers a Payer-created controlled Bill payment using the accepted Tier 1/2/3 Evidence model or the separate Rent/tenancy journey with mandatory attached Evidence accepted before Payment. Category-specific eligibility, Evidence criteria, detailed labels and Directory contents remain with their named owners. Unrestricted P2P, arbitrary company payment, remittance, cashout and open Payee marketplace behavior are prohibited.
- Bill journeys select the supported Category before the Category-scoped Directory or Provide Payee myself. Rent is independent of the Bill Directory and does not use Bill Category selection or either Bill acquisition method.

### Bill identity and purpose timing

Opening Pay a Bill/Rent or Setup a Bill/Rent creates temporary pre-validation capture/session state only. ID establishment consumes an owner-governed source/Evidence preservation eligibility outcome. DOC-06A defines the journey boundary and does not independently define the technical persistence threshold or exact minimum fields required to establish the authoritative Bill/Rent identity. The outcome establishes the ID before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or a payment-facing handoff requires stable source identity, including before immediate-pay Checkout or before deliberate Setup becomes Saved/current. Pending Evidence, mismatch or scoped Admin review does not automatically prevent ID establishment once the outcome permits it. ID establishment alone does not imply accepted Evidence, verified Payee, destination or Payout readiness, risk clearance, Payment Obligation or Checkout readiness, payer authorization, successful Payment, Saved/current, Saved/Archived or history-only projection.

Immediate pay-now journey:

1. select supported Bill Category or enter separate Rent;
2. for a self-provided Bill, capture the Payer's Company/Individual selection before any attached Evidence input where applicable without treating it as Payee truth; for Directory-selected Bills and Rent, continue with the applicable Payee/tenancy context;
3. resolve/provide Payee and apply the applicable Bill Tier 1/2/3 or separate Rent Evidence treatment; only where attached Evidence is present or required may an AI-apparent type assessment and mismatch prompt appear, after which preserve the Payer's accept/decline response and any scoped Admin determination without overwriting provenance;
4. consume the owner-governed source/Evidence preservation eligibility outcome and establish the authoritative Bill/Rent ID before Payable Basis or Payment Obligation materialization and before payment-facing Checkout requires stable source identity;
5. complete DOC-10 destination/Payout, DOC-14 risk/sanctions/fraud/anti-cashout, DOC-09 obligation/Checkout/authorization and other applicable owner gates;
6. complete Payment, whose separate Payment ID links to the Bill/Rent ID;
7. show Payment Result with the separate Payment ID already linked to the same Bill/Rent ID;
8. if the source was already Saved/current before Payment, retain that projection without duplicate Save; for an otherwise unsaved source, resolve the optional Save decision before downstream handoff: selected Save makes the same ID Saved/current, while declined, skipped, dismissed, closed or otherwise abandoned Save resolution makes the same ID history-only;
9. only after that existing-projection or Save-resolution outcome, continue to Activity, Payment History, Receipt or ordinary safe exit. Payment, Activity and Receipt existence does not depend on Save, but those destinations do not bypass the projection resolution.

For a Tier 3 Bill, a prepared Workspace may preserve current context but remains non-executable before qualifying Evidence and authorized approval. An owner-recorded approval keeps the Payer in, or returns the Payer to, the current Bill context; it does not navigate, notify, authorize, submit, or create Checkout. The Payer deliberately selects the current Bill `Pay` action to invoke the DOC-09 Checkout Resolver, which may Resume only after current revalidation confirms the Workspace is active, eligible, and continuable. For Tier 2, confirmed Payment, the current Evidence condition, and DOC-10 Payout hold or release remain separate; ordinary Evidence lifecycle is not Bills Activity. At Add Bill, deliberate confirmation of declared material facts precedes the separate Save-admission outcome, and Rent remains outside Bill tiers with accepted attached Evidence before Payment.

Failure or abandonment after Bill/Rent ID establishment may leave the source unprojected only when immediate pay ends before confirmed Payment, or deliberate Setup ends before its Saved/current projection is completed. Such an outcome does not by itself expose a Bills/Rent route or list entry or create a user-facing incomplete-source status. DOC-09 owns applicable payment-lifecycle continuation/recovery, DOC-15 owns retention governance and requirements, and DOC-18 represents approved data/status/event/audit lineage and technical lifecycle facts. After a newly confirmed Payment for an otherwise unsaved source, closing or leaving Payment Result without selecting Save is skipped Save and produces same-ID history-only before Activity, Payment History, Receipt or ordinary safe exit; it cannot remain unprojected.

Deliberate Setup Bill/Rent journey:

1. enter setup purpose and provide source/Evidence input;
2. consume the owner-governed source/Evidence preservation eligibility outcome and establish the authoritative Bill/Rent ID before Setup gives the source a Saved/current projection and before any Payable Basis or Payment Obligation materialization requires stable source identity;
3. make that same ID Saved/current because Setup is deliberate reuse/collection intent, without a Payment or Payment ID; Saved/current expresses Payer Save/reuse intent and visibility only and does not imply Evidence acceptance, Payee verification, destination readiness, Payment eligibility or authorization;
4. create a later Payment only through DOC-09 under fresh payment-specific gates.

### Journey handoffs and notification

DOC-06A defines journey order, visible choices, continuation, Back/Close/return and owner-approved unavailable treatment only. DOC-12 owns Category, Evidence, OCR/extraction, verification and Evidence-to-Payee matching; DOC-09 owns Payment Obligation, Checkout, payer authorization and Payment invariants; DOC-10 owns destination readiness, Payout and reconciliation; DOC-14 owns risk/sanctions/fraud/anti-cashout; DOC-15 owns privacy/masking/retention; DOC-18 represents approved data/status/event/audit/lineage/reporting requirements; DOC-22 owns only permitted Admin execution under the applicable owner outcomes.

The optional one-way Payee notification is available only where the Payee is eligible under the governed Individual-Payee classification/determination policy. DOC-06 consumes that eligibility outcome and does not determine Payee type, convert Payer-selected type into truth or make an Admin determination. Institution/company Payees are not notified; unresolved or insufficient Individual determination leaves notification unavailable. Where governed Individual determination exists, the Payer may choose the optional one-way informational notification. It is not Request, Linking, acceptance, consent proof, account invitation, reciprocal visibility, payment authorization or a payment-state change. DOC-06A does not define channel, provider, template, contact provenance, lawful basis, consent, suppression/opt-out, delivery evidence, retention, security or support mechanics.

### Accepted journey set

| Journey | Current Wave 2 treatment |
| --- | --- |
| Category-first controlled Bill / Directory-selected Payee | Active Payer journey; Directory is bounded discovery/pre-trust only. |
| Category-first controlled Bill / Provide Payee myself | Active Payer journey; remains Category-bound and consumes the applicable Bill Tier 1/2/3 or separate Rent Evidence treatment. |
| Separate Rent/tenancy | Active Payer journey; no Bill Directory or Category selection. |
| Company/Individual provenance and scoped Admin review | Active handoff; label-only disagreement may be asynchronous/non-user-facing; concrete defects remain owner-controlled. |
| Immediate pay-now Save | No Save before Checkout. After confirmed Payment, an already Saved/current source retains its projection; an otherwise unsaved source resolves selected Save to same-ID Saved/current or declined/skipped/dismissed Save to same-ID history-only before downstream handoff. |
| Deliberate Setup Bill/Rent | Owner-governed source/Evidence preservation eligibility establishes the same ID; Setup gives it Saved/current projection before Payment without implying acceptance or readiness. |
| No-Save/history-only | A confirmed Payment followed by skipped, declined, dismissed, closed or otherwise abandoned Save resolution produces same-ID history-only; an established but unprojected source is limited to pre-confirmed immediate-pay or incomplete-Setup abandonment. Payment remains visible in Activity/History/Receipt after projection resolution. |
| Archive | Ordinary Archive only for saved sources; non-erasure; detailed Restore/prior-version behavior deferred. |
| Request/BILLS-LINKING | Active behavior retired; append-only documentation history and retired stable IDs only; no runtime reader, adapter, fallback or dormant runtime. |

---

## Active Normative Baseline

The sections below are active current requirements for Payer-only journeys and compatible authentication, Checkout, Instructions, Activity, Receipts, failure and return contracts. Retired Request, Linking and Payee-user identifiers appear only in non-active documentation registers or append-only Version History. They define no runtime reader. Append-only Version History remains historical evidence and is not current product behavior.

## 1. Purpose

DOC-06A is the DOC-06 child document for core PayPlus user journeys and service blueprint touchpoints.

It governs Payer journeys, Payee-as-recipient handoffs, Admin/operations/system touchpoints, Evidence/review/authorization boundaries, visibility, notification, receipt, failure and exception journeys at the human-readable product level. It does not create an active Consumer Payee journey.

## 2. Scope Boundary

DOC-06A owns high-level journey and service behavior. It does not own detailed app navigation taxonomy, detailed Bills/rent/tenancy route UI, checkout processing rules, evidence verification algorithms, data schema, notification templates, or admin workflow design.

Detailed navigation and route taxonomy belong to DOC-06B. Detailed Bills/rent/tenancy route behavior belongs to DOC-06C. UX requirements and test mapping belong to DOC-06D.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Core account journeys | Working baseline | Needs later route and screen linkage. |
| Payer-created Bill/Rent journeys | Current Wave 2 baseline | Category-first Bill and separate Rent journeys consume owner-governed source identity outcomes and hand off to specialist domains. |
| Former Payee-created Request journeys | Retired active MVP / documentation history only | Stable IDs remain non-active documentation lineage; no Request runtime, runtime reader, adapter, fallback, replacement route, Linking or Payee-user journey. |
| Evidence and review journeys | Working baseline | Detailed verification remains DOC-12. |
| Authorization and status visibility | Working baseline | Checkout behavior remains DOC-09. |
| Exception journeys | Working baseline | DOC-11 owns refund/dispute/chargeback meaning; DOC-21 owns support/operations and DOC-22 owns only permitted Admin execution. |

## 4. Service Blueprint Ownership

When future edits add service-blueprint tables, use these columns:

| Column | Meaning |
| --- | --- |
| User Step | What the user is trying to do. |
| Frontstage UX | What the user sees or confirms. |
| Backstage System | Validation, routing, notification, risk, or integration behavior. |
| Risk / Compliance Touchpoint | Evidence, authorization, privacy, AML, fraud, or audit control. |
| State / Event | User-visible state or material event signal. |
| Owning Doc | Source document owning detailed behavior. |

---

## 5. Core User Journeys and Service Blueprint

### Core MVP User Journeys

The MVP must support the following essential journeys:

| # | Journey | Required for MVP |
| ---: | --- | ---: |
| 1 | Payer registration and login | Yes |
| 2 | Payer dashboard and account journey | Yes |
| 3 | Category-first controlled Bill payment with Directory/self-provided acquisition | Yes |
| 4 | Separate Rent/tenancy setup and payment | Yes |
| 5 | Evidence recognition, OCR/autofill review, correction and verification handoff | Yes |
| 6 | Company/Individual provenance and scoped Admin review handoff | Yes |
| 7 | Payer payment authorization and Checkout handoff | Yes |
| 8 | Confirmed Payment, Payment Result, Activity, Payment History and Receipt | Yes |
| 9 | Deliberate Setup Bill/Rent and same-ID Saved/current projection | Yes |
| 10 | Immediate pay-now optional post-payment Save and same-ID activation | Yes |
| 11 | No-Save internal history-only source treatment | Yes |
| 12 | Archive projection and non-erasure boundary | Yes |
| 13 | Governed informational Individual-Payee notification handoff | Yes |
| 14 | Admin, risk, privacy, payout and support handoffs | Yes |
| 15 | Retired Request/BILLS-LINKING ID and documentation-lineage treatment | Yes |
| 16 | Failure, cancellation, dispute and exception touchpoints | Yes |
| 21 | Referral registration attribution and qualification tracking | Yes, where Referral campaign is enabled |

---

### Progressive Account Creation and Financial Activation

Payer registration uses the current account model:

1. enter through `ENTRANCE-ROOT`, then use email, Google, or Apple through the defined DOC-06B Login or Registration routes;
2. establish one unique verified primary email and at least one usable login method;
3. accept the required Terms and Privacy notices;
4. create a restricted PayPlus account and enter `HOME-ROOT`;
5. complete full registration through `ACCOUNT-ACTIVATION`, covering phone verification, identity verification, and six-digit payment-passcode setup;
6. preserve the originating permitted context so successful completion can return the user to the interrupted action where applicable.

Google/Apple identities are linked by stable provider identifier only through explicit account creation or authenticated `ACCOUNT-SECURITY` linking. Email equality never creates an automatic account merge or provider link. Social-authenticated users may set a PayPlus password later through `ACCOUNT-SECURITY`.

Before account creation, a temporary registration attempt may preserve verified in-flow context and security records but creates no account and reserves no email, phone, provider identity, or other proposed identifier. Account creation atomically rechecks uniqueness. Referral attribution begins only when restricted-account creation succeeds.

The `AUTH-LOGIN` family resolves remembered eligible users to `AUTH-LOGIN-FAST` and other users to `AUTH-LOGIN-FULL`. Each successful login renews the one-month Fast Login period; approved risk, device, credential, account, or security changes may revoke it earlier. `AUTH-RECOVERY` owns password recovery. DOC-06B owns detailed route and return behavior.

Authentication journeys use capability-aware resolution without changing their approved route sequence. After an operation Outcome is known, PayPlus may continue, restart, redirect, wait, invoke controlled Support, or stop according to the current permitted capability and control context. The Resolution Strategy is separate from persistent status, user-facing message, CTA, notification, and audit event. DOC-06B owns route-level resolution behavior; DOC-07 owns presentation; DOC-08 owns notification; and DOC-18/DOC-19/DOC-20/DOC-21/DOC-22 own their respective data, security, testing, Support, and admin specifications.

---

### Common Account Journey

#### Payer Account Journey

##### Purpose

Allows a Payer to access PayPlus, create controlled Bill/Rent contexts, authorize eligible Payment and track Payment history.

##### Required Payer Capabilities

A payer must be able to:

- register;
- create a restricted account with a unique verified primary email and complete `ACCOUNT-ACTIVATION` before full registration;
- log in;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm material account, credential, payment profile, or contact changes using password, payment passcode, 2FA, or approved confirmation;
- access a payer dashboard;
- create a payer-initiated payment;
- create a controlled Bill or separate Rent/tenancy source context;
- select a supported Bill Category and then Directory or Provide Payee myself for a Bill;
- enter or resolve Payee details within the applicable tier-aware Bill or separate Rent flow;
- upload or link evidence;
- review and correct autofilled evidence fields where applicable;
- review Evidence and owner-controlled outcomes before payment;
- escalate a query, dispute, or support issue through the approved exception flow where applicable;
- authorize payment;
- enter payment passcode before proceeding with payment authorization;
- view payment processing status;
- view failed payment status;
- view completed payment status;
- view receipts or confirmations;
- view Payment, Activity, Receipt and history-only source lineage without a Bills/Rent UI entry when unsaved.

##### Payer Entry Points

The Payer journey may begin when:

- the payer registers directly;
- the payer logs in to create a payment;
- the payer opens Pay a Bill/Rent or Setup a Bill/Rent;
- the payer receives an owner-approved informational notification without creating a Request or Linking relationship;
- the payer returns to view status or history.

---

#### Payee Recipient Boundary

##### Purpose

The Payee is an economic recipient. A Payee may be an individual or institution/company and need not be a PayPlus User. DOC-06A does not define a Consumer Payee account, dashboard, Request, Linking, Receiving Info or reciprocal-visibility journey.

##### Required Payee Capabilities

Payee facts, destination, payout, risk, privacy and notification treatment are consumed from DOC-05 and specialist owners. No active Request or Linking behavior is defined here.

##### Payee Entry Points

No Consumer Payee entry route or runtime historical reader is part of the Wave 2 journey set. Prior actor-role meanings remain only in append-only documentation history and retired stable IDs.

---

#### Referral Registration Attribution Journey

An existing user may share a reusable referral link, code, or QR without identifying a recipient. Sharing does not create an invitation relationship or invitation status.

1. A prospective new user opens a referral deeplink/QR or enters an optional referral code during ordinary registration.
2. Deeplink/QR registration shows the code prefilled and not editable. Ordinary registration allows the user to correct an invalid code or continue without one.
3. The system validates the code and campaign before registration completes. The MVP uses one campaign; future manual entry may require campaign selection first.
4. Successful registration creates immutable normal-user referral attribution between the referrer, referee, campaign, and role-sensitive offers.
5. The system tracks configured qualification conditions and exposes privacy-safe progress to the referrer through the DOC-06B Referral route.
6. Qualification may create separate referrer and referee entitlements under DOC-13. Issued instruments use the canonical Rewards route and status model.

Referral attribution is not payer/payee participant linking, a Request, payment authorization, or permission to view another user's bills, evidence, payment amounts, cards, KYC data, payees, or internal risk reasons.

---

---

### Non-Active Documentation Register - Retired Request and Two-Sided IDs

This concise register preserves retired stable IDs and prior actor-role meanings only as non-active documentation evidence. PayPlus has no production Request/Payee-role runtime or legacy Request deep-link data. This register is not a route, runtime reader, notification, Linking or Payee-user journey.

| Retained record | Preservation location | Current treatment |
| --- | --- | --- |
| Request, Payee and participant stable IDs; prior actor-role and lineage meanings | Append-only documentation history only | Retired active MVP; no route, runtime reader, action, notification, adapter, fallback, acceptance or reciprocal visibility |
| Prior response, consent or invitation concepts | Append-only documentation history only | No production data or active lifecycle/participant state machine |



### Evidence Upload and Review Journey

#### Purpose

Ensures each payment is linked to the authoritative Bill/Rent source and uses attached Evidence where the applicable Bill tier or Rent rule requires it before payment; Tier 1 Bills do not require attached Evidence.

DOC-12 owns detailed bill category, OCR/document AI, extracted field, autofill, user correction, duplicate detection, verification outcome, and payee matching requirements. DOC-06A describes only the core user journey and UX touchpoints; DOC-06C owns Bills-specific evidence route behavior.

#### Accepted MVP Evidence Types

MVP evidence may include:

- bill;
- invoice;
- tenancy agreement;
- rent demand;
- payment statement;
- service agreement;
- official notice;
- contract;
- uploaded PDF;
- uploaded image;
- manually entered bill details with supporting document;
- other proof of payment obligation permitted by the applicable DOC-12-owned Evidence policy.

#### Evidence Upload and Verification Flow

1. Payer creates or updates a controlled Bill or separate Rent source context.
2. User provides evidence through `BILLS-ADD` or `BILLS-EVIDENCE-UPLOAD` where evidence is required.
3. System validates file type and required metadata where applicable.
4. System processes OCR/document AI where enabled.
5. System extracts eligible fields and autofills permitted Bill/Rent setup fields.
6. Payer reviews and corrects the Bill/Rent details before submission.
7. System stores raw evidence, extraction result, user correction, and final evidence snapshot where applicable.
8. System links Evidence to the Bill/Rent source context under DOC-12 ownership.
9. System applies duplicate/reused evidence, mismatch, completeness, same-party, and risk checks.
10. System assigns an evidence status.
11. DOC-12-owned Evidence status becomes one input to the combined owner-controlled readiness evaluation; it does not itself establish Payable Basis, Payment Obligation, destination/Payout readiness, risk clearance, Checkout eligibility or payer authorization.
12. Accepted Evidence may satisfy the Evidence dimension for role-based review and combined eligibility evaluation. DOC-09 owns Payment Obligation, Checkout and authorization readiness; DOC-10 owns destination/Payout readiness and reconciliation; DOC-14 owns sanctions, fraud and anti-cashout risk. User-facing readiness consumes the combined owner-controlled outcome without collapsing those dimensions.
13. An owner-controlled red-flag outcome may produce an approved Payer clarification step or a bounded specialist/Admin review handoff.

#### Evidence Review Access

| Role | Evidence Access |
| --- | --- |
| Payer | Can review attached Evidence before authorizing payment where the applicable Bill tier or separate Rent rule requires or supplies it. |
| Payee | No active Consumer Payee evidence surface; any permitted recipient view is specialist-owned and controlled. |
| Admin / Operations | May receive only the Evidence context defined by DOC-12 and fields permitted by DOC-15 for the applicable approved purpose. DOC-22 executes only that permitted Admin access; DOC-06A does not grant access. |
| System | Links Evidence to Bill/Rent and Payment lineage and logs actions under specialist ownership. |

#### Evidence Rules

| Rule | Requirement |
| --- | --- |
| Evidence boundary | Evidence supports a controlled Bill Category or separate Rent journey. Evidence truth, acceptance and matching remain with DOC-12; Evidence alone never creates eligibility outside the approved product boundary. |
| Evidence linked | Evidence links to the Bill/Rent source and downstream Payment Domain lineage; Checkout executes only through DOC-09 Payment Obligation controls. |
| OCR/autofill | Where enabled, extracted fields assist Bill/Rent capture but must not remove Payer review. |
| User correction | Users must be able to correct autofilled fields before submission. |
| Extractable vs displayable | Sensitive extracted fields may be stored under controls without being shown broadly in UI. |
| Duplicate warning | Duplicate or reused Evidence may produce a DOC-12/DOC-14-owner-approved Payer warning or bounded Admin-review handoff, subject to DOC-15 privacy controls. |
| Verification outcome | Concrete Evidence, intended-Payee, destination, beneficiary/agent, Category, sanctions, fraud, anti-cashout, payout, readiness or authorization defects may block their applicable stage. A label-only Company/Individual disagreement may create asynchronous/non-user-facing Admin review and must not by itself force a payment-review state or block otherwise eligible payment. |
| Payer review | Payer must be able to review attached Evidence before authorizing payment where the applicable Bill tier or separate Rent rule requires or supplies it. |
| Admin review handoff | Where an applicable owner requires Admin review, DOC-06A hands off the relevant Evidence context without defining access, queue, action or disposition. DOC-12 owns Evidence requirements, DOC-15 owns approved-purpose access and privacy controls, and DOC-22 executes only the permitted Admin workflow under those and other applicable specialist-owner rules. |
| Auditability | DOC-12 owns the required Evidence meaning, while DOC-18 represents approved Evidence upload, view, update/replacement and review lineage in later data, status/event and audit models. DOC-22 may execute permitted audit-handling steps but does not define the audit requirement or status meaning. |
| Access control | Evidence visibility follows DOC-15-owned approved-purpose access and masking requirements together with DOC-12 Evidence rules. DOC-22 may execute only the resulting permitted Admin access; DOC-06A and DOC-22 do not independently define permissions. |

---

---

### Payer Support, Dispute, and Exception Handoff

This is a bounded Payer-side support and exception handoff for a controlled Bill/Rent source, Payment, or applicable Evidence issue. Bills use their accepted tiered Evidence treatment and Rent retains mandatory attached Evidence. It does not define a Request route, acceptance flow, participant relationship, or reciprocal-visibility journey. Detailed case, dispute, notification, payment-hold, Admin and audit treatment remains with DOC-09, DOC-11, DOC-14, DOC-18, DOC-21 and DOC-22 as applicable.

| Boundary | Payer-only treatment |
| --- | --- |
| Entry | A Payer may enter an owner-approved support or exception path from the relevant Bill/Rent, Evidence, Checkout, Payment or Activity context where available. |
| Context | The matter remains linked to applicable Bill/Rent, Evidence and/or Payment lineage; no Request or participant object is created. |
| Response | The Payer may provide an explanation or additional information where the owning process permits it. |
| Review | The applicable specialist owner supplies the controlling policy and outcome; permitted Admin or operations staff may execute only the bounded review through DOC-22 and owner-approved processes. DOC-06A does not define case statuses, queues, permissions, dispositions, notifications or payment blocks. |
| History | Support, dispute and exception history remains auditable through controlled owner readers without creating reciprocal visibility or an active two-sided journey. |

---

---

### Payment Authorization Journey

#### Purpose

Ensures that the payer explicitly authorizes payment after reviewing the required context.

#### Required Payer Authorization Information

Before authorization, the payer should be shown:

- payee;
- amount;
- service fee where applicable;
- eligible promotion quote, discount, coupon, voucher, or reward impact where applicable;
- total charge;
- due date;
- category;
- description;
- evidence;
- payment method;
- pay-now or deferred payment instruction choice where enabled;
- funding leg and split-card summary where applicable;
- quote validity, expiry, or recalculation notice where applicable;
- selected payee transfer date where applicable;
- expected processing timing;
- expected payout or settlement timing where applicable;
- refund/reversal limitations where applicable;
- PayPlus role;
- relevant disclosures.

#### Authorization Flow

1. Payer reviews the controlled Bill/Rent source and applicable payment details.
2. Payer confirms that owner-controlled Evidence and payment details are acceptable.
3. System displays the final payment summary and effective destination; no Request or Payee acceptance flow is required for the Payer-created journey.
4. System displays fee, promotion quote, discount, coupon/voucher impact, reward impact, and total charge where applicable.
5. Payer selects or confirms the applicable funding method. Single-card funding may use an eligible default card. Multi-card funding may use an owner-confirmed current-Checkout allocation or Payment Profile capability. Where exactly one capability is available, the Workspace proceeds directly to that capability without a capability-selection step; direct entry does not silently select a specific profile, confirm an allocation, or authorize funding. Where two or more capabilities are simultaneously available, the payer selects the capability. The payer then completes the applicable funding configuration, review, and authorization.
6. Payer chooses pay now or creates a deferred payment instruction where enabled.
7. Payer accepts required terms or disclosures for the selected action.
8. Payer enters payment passcode or completes confirmation required for the selected action.
9. System applies any required step-up authentication, such as new-device, risk, amount, or partner challenge.
10. If paying now, payer confirms authorization and payment processing begins through approved payment partner or sandbox integration.
11. If creating a deferred payment instruction, system stores the payment context and returns the payer through payment-instruction reminder/action flow when payment submission is due.
12. On return, system revalidates payment quote, promotion quote, card eligibility, timing, and material terms before gateway submission.
13. If material terms changed, payer reviews the updated checkout summary and confirms before submission.
14. Payer completes required payment passcode, step-up, or partner challenge before actual funding submission where required.
15. System records authorization, payment instruction, payment attempt, and status events as applicable.

#### Authorization Rules

| Rule | Requirement |
| --- | --- |
| Explicit consent | Payer must explicitly authorize payment. |
| No automatic payment | Payment requires explicit Payer authorization; no Request or Payee acceptance flow is part of the Payer-created journey. |
| Evidence visibility | Payer must be able to review attached Evidence before payment where the applicable Bill tier or separate Rent rule requires or supplies it. |
| Fee visibility | Fees charged to payer must be displayed before authorization. |
| Promotion visibility | Eligible discounts, service-fee benefits, coupons, vouchers, and reward impact must be displayed before authorization where applicable. |
| Payment passcode | Payment passcode is required before payment authorization proceeds. |
| Step-up authentication | DOC-09 owns payment-admission conditions, DOC-14 owns risk triggers/actions, DOC-15 owns privacy conditions, and provider owners supply applicable partner conditions; DOC-19 enforces the resulting security assurance requirement without deciding the trigger or outcome. |
| Deferred instruction | A deliberate Payment Instruction must return the payer to checkout when submission is due; an interrupted immediate payment remains an incomplete Checkout Workspace and must resume through its preserved checkout context. |
| Quote revalidation | Deferred instruction return flow must show updated payment, promotion, card, fee, or timing changes before submission. |
| Partial execution | Confirmed Payments must remain visible even when the Checkout Target is not fully funded. The remaining Checkout Target and the obligation Outstanding Amount must remain distinct and clear. |
| Audit logging | Authorization must be logged. |
| No hidden material terms | Material payment information must not be hidden from payer. |

---

---

### Payment and Payout Status Visibility

#### Purpose

Identifies Payer-visible outcomes after authorization and the bounded handoff of owner-authorized context to Admin/operations where an applicable owner requires it.

Detailed payment processing, payout, settlement, reconciliation, refund, reversal, chargeback, and exception rules belong in DOC-09, DOC-10, and DOC-11.

#### Required Visibility

| User | Required Visibility |
| --- | --- |
| Payer | Authorization result, payment status, failure state, cancellation/refund state where applicable, and receipt/history. |
| Admin / operations | Receives only the review context defined by the applicable specialist owner and permitted by DOC-15; DOC-22 executes only the resulting Admin workflow. This journey does not grant object access or define a generic Admin view. |

#### UX Rules

| Rule | Requirement |
| --- | --- |
| Status clarity | User-facing labels must distinguish Payment, payout/settlement and other owner-controlled outcome meaning; no Request status is active. |
| No false certainty | The UX must not imply payment or payout is complete before the relevant system of record confirms it. |
| Permissioned visibility | Payer and Admin/support views expose only the fields permitted by the owning privacy and domain controls. |
| Exception visibility | Failures, holds, cancellations, refunds, and disputes must have clear owner-approved user-facing treatment and, only where an applicable owner requires review, a bounded Admin/operations handoff. |

---

---


### Non-Active Documentation Register - Retired Linking and Request Status IDs

| Retained record | Preservation location | Current treatment |
| --- | --- | --- |
| Linking identifiers and prior actor-role/status meanings | Append-only documentation history only | Retired active MVP; no runtime reader, invitation, reciprocal visibility or participant permissions |
| Prior Request outcome labels and response concepts | Append-only documentation history only | No production data, active Request status model or replacement journey |



### Admin and Operations Handoff Journey

#### Purpose

Represents the journey-level handoff when an applicable formal owner requires controlled Admin or operations review of a Payer account, Bill/Rent source, Evidence, risk matter, dispute, Payment, payout, settlement, failure or exception. DOC-22 and the applicable specialist owner govern execution. This handoff does not create a Consumer Payee account view or active Request workflow.

#### Journey-Level Handoff

| Journey boundary | Active treatment |
| --- | --- |
| Trigger | The applicable Evidence, payment, payout, refund/reversal, risk, privacy, support or operations owner determines whether controlled review is required. DOC-06A does not create a generic review trigger or queue. |
| Context handoff | The journey may retain a reference to the affected Payer, Bill/Rent source, Evidence, Payment or other owner-controlled object. The applicable owner and DOC-15 determine which facts may be shown, masked or withheld. |
| Routing | Review is handed to a DOC-22 workflow or specialist-owned process only where that owner has defined and enabled it. DOC-06A does not select the queue, permission, action, disposition, status or resolution. |
| Scoped Company/Individual determination | Payer selection, AI-apparent assessment, Payer response and the scoped determination remain separate provenance. `Reviewed` and `Resolved` remain separate. Label-only review may be asynchronous and non-user-facing and does not block otherwise eligible payment when every concrete owner-controlled gate passes. |
| Owner outcome | The journey consumes the applicable owner-approved outcome without converting it into global Payee truth or independently changing Evidence, risk, Payment, payout, refund/reversal, dispute or account state. |
| Communication | Any Payer communication remains with the applicable outcome, Copy and notification owners. Payee-facing notification remains unavailable for institution/company or unresolved/insufficient Individual determination and requires governed Individual eligibility plus affirmative Payer choice. |
| Audit and operations | The applicable domain owner defines the required outcome and audit meaning; DOC-18 represents approved data/event/audit lineage, DOC-21 owns support and escalation, and DOC-22 executes only the permitted Admin queue and handling. DOC-06A defines none of their technical or permission mechanics. |

---

---

### Notification Touchpoints  - Governed Individual-Payee Handoff

DOC-06A consumes the governed Individual-Payee eligibility/determination outcome; it does not determine Payee type or make an Admin determination. Institution/company and unresolved/insufficient Individual determination leave notification unavailable. A governed Individual determination plus Payer choice may expose an optional one-way informational capability only. It is not Request, Linking, acceptance, consent proof, invitation, reciprocal visibility, payment authorization or a payment-state change. DOC-05 owns only the eligibility boundary; DOC-07 owns approved Copy/disclosure/CTA; DOC-08 owns notification identity/channel/template/preference/delivery; DOC-14 owns risk/abuse; DOC-15 owns privacy/retention requirements; DOC-18 represents approved data/audit requirements; DOC-19 owns security; DOC-21 owns support/operations; and DOC-22 performs only permitted Admin execution. DOC-12 supplies any Evidence-derived classification input but does not own notification delivery. Contact provenance and lawful-basis or consent treatment remain with their applicable formal owners. No Request notification behavior is active.

#### Purpose

Identifies where notifications are needed in the user journey. Notification content, templates, channels, preferences, retry behavior, and audit rules belong in DOC-08.

#### User Notifications

The Payer-only MVP should support basic notifications for:

- account registration;
- payment authorized;
- payment instruction pending user action;
- payment instruction partially funded;
- remaining split-card payment action due;
- payment processing;
- payment completed;
- payment failed;
- payout completed where applicable;
- partial payout completed where applicable;
- optional one-way informational notification to an eligible Individual Payee after governed eligibility and Payer choice; institution/company or unresolved/insufficient Individual determination remains unavailable.

#### Admin Notification and Queue Handoff

Admin queue and notification eligibility remain owner-controlled. DOC-06A identifies only the broad handoff for Evidence, duplicate, risk, dispute, Payment, payout, refund/reversal and operational exceptions. DOC-09, DOC-10, DOC-11, DOC-12 and DOC-14 retain their respective domain policy and outcomes; DOC-15 governs access and retention; DOC-18 represents approved event and audit requirements; DOC-21 owns support/operations; and DOC-22 owns permitted Admin execution. DOC-06A defines none of their queues, actions, permissions, dispositions, channels, providers, templates, delivery, retry, preference, consent or retention mechanics.

---

---

### Receipt and History Touchpoints  - Current Payer Boundary

Confirmed Payment has a separate Payment ID linked to the authoritative Bill/Rent ID. A source already Saved/current before Payment retains that projection without duplicate Save. For an otherwise unsaved source, Payment Result must resolve selected Save to same-ID Saved/current or declined/skipped/dismissed/closed Save to same-ID history-only before Activity, Payment History, Receipt or ordinary safe exit. Those records exist independently of Save, but they do not provide a bypass; no Save-from-Activity or Unsave action exists. DOC-09 owns Payment lifecycle and record meaning, DOC-15 owns retention governance and requirements, and DOC-18 represents approved data/status/event/audit lineage. Retired Request/Linking IDs remain non-active documentation evidence only.

#### Purpose

Identifies where users and admins need access to prior actions, statuses, confirmations, and payment outcomes. Receipt content and records policy belong in DOC-08, DOC-15, DOC-18, and payment-domain docs.

#### User History

Payers should be able to view:

- the authoritative Bill/Rent source and its permitted projections;
- Evidence records subject to owner-controlled access;
- payment status;
- payout status where applicable;
- dispute history;
- completed payment records;
- failed payment records;
- receipts or confirmations. Retired Request/Linking IDs are not an active user or runtime-reader surface.

#### Receipt or Confirmation Contents

A receipt or confirmation should include:

- Bill/Rent source reference;
- payment ID where applicable;
- payer;
- payee;
- amount;
- fees where applicable;
- total charged where applicable;
- payment status;
- payment date/time;
- evidence or obligation reference;
- payment method summary where appropriate;
- payout or settlement status where appropriate;
- confirmation reference where applicable.

#### History Rules

| Rule | Requirement |
| --- | --- |
| Traceability | User-visible history must link to the authoritative Bill/Rent and Payment context; retired Request IDs remain non-active documentation lineage only. |
| Role permissions | Payer history and controlled support/Admin readers show only owner-approved information. |
| Audit separation | User history is not the same as full admin audit logs. |
| Failed and exception visibility | Failed Payment outcomes and linked dispute/support cases remain visible in their owning surfaces; retired Request states are not runtime-reader content. |
| Receipt storage | Completed payments should have receipt or confirmation records. |
| Retention baseline | DOC-15 owns the accepted indefinite-retention direction, subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries, plus privacy classification, access and masking controls; this journey document defines no storage or disposition mechanism. |

---

---

### Error, Failure, Cancellation, and Exception Journeys

#### Failed Payment

1. A payment attempt is authoritatively unsuccessful without a confirmed Payment for that attempt.
2. DOC-09 and the applicable data/status owner record and expose the owner-approved unsuccessful outcome for the affected attempt or Checkout context; DOC-06A does not define a new `Failed` status or assign it to an unspecified object.
3. An owner-approved failure reason may be presented where available and permitted.
4. Payer notification follows the applicable owner-defined behavior.
5. Any Payee-facing notification remains subject to governed Individual eligibility plus affirmative Payer choice; it is not automatic and is unavailable for institution/company or unresolved/insufficient Individual determination.
6. Where an owner-controlled support or Admin review is required, the journey hands off to the applicable DOC-09/DOC-21/DOC-22 process without defining its queue, permission, action or disposition.
7. User may retry only if allowed by approved rules.
8. If no Payment is confirmed, no post-Payment Save outcome is created. Any separate newly confirmed Payment in the same Checkout follows the required existing-projection or Save-resolution boundary before Activity, Receipt or ordinary safe exit.

#### Retired Request Concepts

Request cancellation, expiry and response meanings remain append-only documentation history only. DOC-06A defines no active Request route, runtime reader, notification, state transition, adapter, fallback, reopening or replacement behavior.

#### Duplicate or Reused Evidence and Source Review

1. Applicable DOC-12 Evidence controls and DOC-14 risk controls may identify duplicate/reused Evidence or source indicators.
2. The Payer may receive an owner-approved safe clarification where permitted, subject to privacy and anti-tipping-off controls.
3. Payment progression follows the applicable owner-controlled Evidence, risk and payment gates; DOC-06A does not create a Request object, Request state, queue, lifecycle, acceptance, reopening or replacement runtime, and it does not define Admin dispositions or permissions.
4. DOC-12 and DOC-14 retain Evidence/risk outcome authority, DOC-18 represents approved audit lineage, and DOC-22 executes only the permitted Admin review under those owner rules.

#### Refund or Reversal

1. Refund or reversal need is identified.
2. Where DOC-11 requires controlled review, the applicable owner process receives only the authorized case, Payment, Evidence, source and historical-lineage context; DOC-22 executes only the permitted Admin handling.
3. The journey consumes the owner-controlled review outcome without defining Admin actions, permissions or dispositions.
4. The applicable DOC-11/DOC-18 owner records and exposes the approved refund or reversal outcome.
5. Payer notification follows the applicable owner-defined behavior. Any Payee-facing notification remains subject to governed Individual eligibility plus affirmative Payer choice and is never automatic.
6. DOC-11 defines the required case/outcome lineage, DOC-18 represents the approved audit lineage, and DOC-22 records only its permitted execution under those requirements.

Refund and reversal rules belong in DOC-11. Payment, payout, reconciliation, and admin workflow details belong in DOC-09, DOC-10, DOC-18, DOC-21, and DOC-22.

---

---

## 6. Local Open Questions

Core journey open questions should remain here when they affect Payer journeys, recipient-policy handoffs, Admin/operations handoffs, or system journeys generally. Cross-document blockers should also be linked in docs/traceability/open-questions-register.md.

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06-001 | Retired under the Payer-only target: no Request-facing UX or runtime record exists. The current Founder Working Baseline distinguishes the authoritative Bill/Rent source, Payable Basis, Payment Obligation, Checkout Workspace and confirmed Payment under their owners. | Product / Design / Payments | Answered/retired; later technical representation remains owner work |
| OQ-06-002 | Retired under the Payer-only target: no Payee adoption requirement or active Payee-created category is defined by DOC-06A. Any future participant capability requires a separately governed Proposal. | Product / Operations / Risk | Retired |
| OQ-06-003 | Retired under the Payer-only target: no Payee-created Request category, active Request Admin flow or runtime historical reader is defined by DOC-06A. | Risk / Operations | Retired |
| OQ-06-004 | What DOC-12-owned Evidence forms and criteria apply to each accepted launch Bill Category and to the separate Rent journey? | DOC-12 / Product / Compliance | Open; the twelve-category inventory itself is settled |
| OQ-06-005 | Which rent and tenancy journey controls must be ready before initial launch enablement? | Product / Legal / Risk | Open |
| OQ-06-006 | What final KYC/KYB screens, provider handoff, failure states, exception states, and risk-tier steps are required for the baseline onboarding model? | Compliance / Legal | Open |
| OQ-06-007 | What payment methods are available to payers at MVP launch? | Payments / Product | Open |
| OQ-06-008 | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Operations | Open |
| OQ-06-009 | What fee disclosures must be shown before payment authorization? | Business / Legal | Open |
| OQ-06-010 | What detailed dispute case types, action outcomes, service levels, and payment/payout hold rules are required beyond the accepted `Open`, `Pending Information`, `Under Review`, `Resolved`, and `Closed` case lifecycle? | Operations / Legal | Open |
| OQ-06-011 | What refund or reversal journeys are supported in MVP? | Payments / Operations | Open |
| OQ-06-012 | What routing, preferences, templates, consent rules, and fallback behavior apply across app, push, email, SMS, and WhatsApp notifications? | Product / Engineering | Open |
| OQ-06-013 | What permitted Admin execution roles and permission levels must DOC-22 define under the applicable security and DOC-15 privacy/access requirements? | Operations / Security / Privacy | Deferred owner handoff; DOC-06A defines no role or permission |
| OQ-06-014 | What information should be hidden or masked between payer and payee? | Product / Security / Legal | Open |
| OQ-06-015 | What duplicate detection signals are required for MVP? | Risk / Engineering | Open |
| OQ-06-016 | What OCR/autofill review UI is required for each evidence category? | Product / Design | Open |
| OQ-06-017 | What duplicate/reused evidence warning can be shown without over-disclosing sensitive information? | Product / Legal / Privacy | Open |
| OQ-06-018 | What separate dormant-account reauthentication threshold, if any, should apply beyond the confirmed rolling one-month Fast Login eligibility period? | Product / Security | Partially open; Fast Login period defined |
| OQ-06-019 | What exact masking, reveal, and role-based display rules should apply to each sensitive field by screen and category? | Product / Privacy / Security | Open |
| OQ-06-020 | What exact payment-instruction screen labels, call-to-action wording, and partial-funded visual treatment should be used? | Product / Design / Legal | Open |
| OQ-06-021 | What exact Pay+ iconography, measurements, spacing, blur strength, motion timing/easing, responsive treatment and accessibility implementation should be used within the confirmed four-action Payer-only order and behavior? | Product / Design / Payments | Partially open; composition, order, material meaning and Request Payment retirement are settled in DOC-06B |
| OQ-06-022 | What route-level IA remains to be defined in DOC-06B for Support and other incomplete secondary routes? Me, More, Offers, Rewards, and Referral route boundaries are defined. | Product / Design | Open |
| OQ-06-023 | What final styling and optional post-replacement Undo should apply to the defined `MORE-ROOT` behavior? The shortcut maximum, protected More entry, reorder/remove/add behavior, account-level preference, current-default restore, owner-approved default and permitted Admin-configuration mechanism are decided. | Product / Design / Operations | Partially open |
| OQ-06-024 | What final visual design, exact DOC-07 Copy and identifiers, technical session mechanics, adopted-platform accessibility implementation, and DOC-20 evidence should apply to the decided HOME-ROOT Important Notice baseline? Its Home consumption of source-provided ordering, session dismissal, Detail and source-action routing, return, and zero-state behavior are defined in DOC-06B; DOC-08 and source owners retain notification and business meaning. | Product / Operations / Compliance | Partially open; Home behavior decided, residual owner dependencies pending |
| OQ-06-025 | What final visual design, exact DOC-07 Copy and identifiers, technical carousel mechanics, adopted-platform accessibility implementation, and DOC-20 evidence should apply to the decided Home Hot Offer baseline? Its Home cap, Admin selection and ordering, rotation and interaction, canonical restrictions, and `OFFER-DETAIL` handoff are defined through DOC-06B and its formal source-owner handoffs. | Product / Growth / Operations | Partially open; Home behavior decided, residual owner dependencies pending |
| OQ-06-026 | If a future participant Linking or invitation capability is proposed after MVP, what separately governed domain and privacy/security review should define it? | Product / Privacy / Engineering | Deferred; no active Linking or invitation behavior |
| OQ-06-027 | What exact Bills tab visual layout, card density, status badge style, action-required treatment, and field masking rules should be used? | Product / Design / Privacy | Open |
| OQ-06-028 | What evidence source selection UI should be used when bill, invoice, tenancy, rent demand, contract, and supporting evidence types are not obvious from upload/OCR? | Product / Design / Risk | Open |
| OQ-06-029 | Retired: Founder confirmed there is no production Request/BILLS-RECEIVE runtime or legacy deep-link data requiring a reader, adapter or fallback. | Product / Design / Operations | Answered/retired |
| OQ-06-030 | The reviewed DOC-06B Section 5.20 adaptive UI contract and decided Bill/Rent, Instruction `Pay Now`, and `NOTIFICATION-DETAIL`-first entry contracts establish route-level `PAYMENT-CHECKOUT` behavior as a Defined baseline without imposing one fixed screen order. DEC-2026-037 establishes the accepted DOC-07 logical Semantic, Disclosure, CTA, Reference, Registry, non-executable Composition, and Bounded Domain Slice architecture. Which remaining exact Copy, IDs, CTA labels, Locale Variants, Presentation Mappings, final Bill/Rent source-owner detail, technical contracts, prototype and accessibility/user-validation evidence, implementation/UAT, and acceptance evidence must the applicable owners complete? | Product / Design / Payments | Partially open; route-level UI/UX, entry contracts, and logical communication architecture are decided, while exact expression and mappings plus named source-owner, technical, prototype, validation, implementation/UAT, and acceptance dependencies remain pending. |

## 7. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 1.1.0 | 2026-08-22 | Aligned the Bill journey to approved Tier 3 current-context and deliberate-resolver return, Tier 2 separate Payment/Evidence/Payout treatment, and Add-Bill Declaration/Save boundary while preserving Rent, owner, and no-invention constraints. |
| 1.0.1 | 2026-08-21 | Separated payment, risk, privacy and provider step-up conditions from DOC-19 mechanism-neutral security enforcement without changing journey behavior. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 0.1.23 | 2026-08-12 | Applied the Founder-settled indefinite-retention boundary to the journey handoff without introducing storage or disposition mechanics. |
| 0.1.22 | 2026-08-12 | Clarified that the active Payer-only journey baseline stands independently of non-active documentation lineage; no journey, route, or interaction behavior changed. |
| 0.1.21 | 2026-08-12 | Stage 8 Wave 2 Draft: aligned Payer-only Bill/Rent journeys to the accepted Category inventory, removed nonexistent Request-runtime/readers/deep-link obligations, preserved source/Save/readiness and notification boundaries, and kept Admin treatment at bounded specialist-owner handoffs. |
| 0.1.20 | 2026-08-06 | Narrowed OQ-06-024 and OQ-06-025 to final visual, Copy/identifier, technical, adopted-platform accessibility-implementation, and DOC-20 evidence dependencies after the HOME-ROOT Important Notice and Home Hot Offer route-level baselines were decided in DOC-06B. |
| 0.1.19 | 2026-08-05 | Recognized `PAYMENT-CHECKOUT` as a Defined baseline and DEC-2026-037 as the accepted logical communication architecture while retaining exact Copy, identifiers, CTA labels, Locale Variants, Presentation Mappings, Bill/Rent source detail, technical, prototype, validation, implementation/UAT, and acceptance dependencies in OQ-06-030. |
| 0.1.18 | 2026-08-04 | Recorded the decided Instruction `Pay Now` Checkout Resolver and mandatory `NOTIFICATION-DETAIL` entry contracts while retaining Bill/Rent handoff, DOC-07 communication, technical, prototype, validation, and implementation/UAT dependencies. |
| 0.1.17 | 2026-08-03 | Aligned the Checkout authorization journey with owner-confirmed current-allocation and Payment Profile capabilities, including direct entry when only one capability is available without silently selecting, confirming, or authorizing funding. |
| 0.1.16 | 2026-08-03 | Aligned OQ-06-030 with the reviewed DOC-06B adaptive Checkout UI contract while retaining cross-owner entry, copy, technical, prototype, validation, and acceptance dependencies. |
| 0.1.15 | 2026-07-31 | Aligned journeys with Request-as-linkage, Payment Obligation/Checkout boundaries, and the distinct deliberate Payment Instruction versus incomplete Checkout Workspace model. |
| 0.1.14 | 2026-07-29 | Aligned the AUTH journeys with capability-aware Outcome-to-Resolution handling while preserving the existing Login, Registration, Recovery, Account Activation, and protected-return decisions. |
| 0.1.13 | 2026-07-28 | Defined the journey handoff for `ENTRANCE-ROOT`, Fast/Full Login, Recovery, non-reserving registration attempts, restricted-account creation, Account Activation, rolling one-month Fast Login eligibility, and protected contextual return. |
| 0.1.12 | 2026-07-27 | Added the progressive restricted-account and financial-activation journey, unique primary email, explicit email/password and provider login methods, deferred phone/identity/passcode completion, and Account Security linking handoff. |
| 0.1.11 | 2026-07-27 | Closed the material More/shortcut IA questions after DOC-06B defined capacity, protected access, preference, reorder, restore, availability, and secondary-service behavior; retained final styling and optional Undo as open. |
| 0.1.10 | 2026-07-27 | Narrowed the Pay+ open question to exact visual and motion specification after DOC-06B defined the five-action order, route handoffs, role direction, and availability behavior. |
| 0.1.9 | 2026-07-26 | Established the canonical request lifecycle and role-facing labels, separated request events, evidence, readiness, payment, dispute-case, and archive domains, and corrected payer-created payment flow so optional linking is not an acceptance prerequisite. |
| 0.1.8 | 2026-07-23 | Added Receiving Info selection, private-profile boundary, request destination snapshots, pre/post-acceptance change rules, payer-selected replacement handling, linked-payee notification, and authorization-time destination freeze. |
| 0.1.7 | 2026-07-21 | Added the referral registration-attribution journey, separating external sharing from attribution, qualification, payer/payee linking, requests, payment authority, and canonical reward issuance. |
| 0.1.6 | 2026-07-14 | Clarified that receipt request ID applies only where the completed payment originated from a request. |
| 0.1.5 | 2026-07-06 | Added lightweight journey alignment for default single-card selection and user-selected split-card payment profile handoff without moving checkout behavior out of DOC-09. |
| 0.1.4 | 2026-07-02 | Reclassified query, dispute, and information-request handling as exception/support flows instead of normal `REQUESTS-DETAIL` actions. |
| 0.1.3 | 2026-07-02 | Aligned request lifecycle with DOC-06B `REQUESTS-NEW`, evidence-before-send delivery gate, and simplified accept/reject request actions. |
| 0.1.2 | 2026-06-25 | Clarified that requests are party-linking and acceptance records, not payments; separated request states from linked payment states. |
| 0.1.1 | 2026-06-25 | Removed temporary source-section heading wording and finalized official DOC-06A heading style. |
| 0.1.0 | 2026-06-25 | Created as DOC-06A child document for core user journeys and service-blueprint content without changing product decisions. |
