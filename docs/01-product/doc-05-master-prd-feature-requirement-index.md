---
document_id: DOC-05
title: Master PRD & Feature Requirement Index
version: 1.1.1
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Engineering Lead
  - Compliance Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-08-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-16 Technical Architecture Specification
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT & Release Readiness
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-05 - PayPlus Master Product Requirements Document

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-05` |
| **Title** | Master PRD & Feature Requirement Index |
| **Version** | `1.1.1` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-02 Business Model & Unit Economics<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-16 Technical Architecture Specification<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT & Release Readiness<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This document defines the master product requirements for PayPlus, a controlled Bill and Rent Payment App in which Consumer Users act as Payers. Bills use the approved tiered Evidence, Declaration, Payment and Payout policy; Rent retains its existing mandatory attached-Evidence and Evidence-acceptance-before-Payment model.

DOC-05 is the primary human product-policy owner for the bounded Institutional Payee Programme, Category-scoped Payee Directory, Bill Payee-acquisition model, Bill/Rent Save meaning, individual-notification capability boundary, and target retirement of active Request and BILLS-LINKING behavior. It establishes product meaning, limits, ownership and Acceptance Criteria without taking over specialist rules.

DOC-01 retains high-level product identity and positioning. Evidence truth belongs to DOC-12; Payment Domain invariants to DOC-09; payout and destination execution to DOC-10; risk to DOC-14; privacy to DOC-15; notification delivery to DOC-08; reviewed business recording, explainability, history and owner handoffs to DOC-18; and Admin execution to DOC-22. Exact technical representation remains separately gated. Detailed journeys, routes and UI remain with the DOC-06 family.

---

## 2. Product Summary

PayPlus enables a Payer to pay an eligible real-world Bill or Rent obligation by card when every applicable Category, Declaration, Evidence, Payee, destination, payment, payout, risk, privacy, compliance and authorization gate passes. Attached Evidence treatment is tiered for Bills only; Rent always requires attached Evidence and its owner-governed acceptance before Payment.

| Concept | MVP meaning |
|---|---|
| Consumer User | A PayPlus User acting as Payer. The MVP does not require a Payee-user role. |
| Payee | The economic recipient. A Payee may be an individual or an institution/company and does not need to be a PayPlus User. |
| Bill scope | Only specified supported controlled Bill Categories. Each Bill journey remains governed by its selected Category. |
| Rent scope | A separate tenancy/relationship journey governed by Rent-specific Evidence and controls. Rent does not use the controlled-Bill Directory in MVP. |
| Payment model | Payer-created and explicitly Payer-authorized. A Bill may proceed under Tier 1 without attached Evidence only when the approved Bill-tier rules and every other applicable gate pass. Tier 2/3 Bills and all Rent Payments require attached Evidence as defined by their owners. A Payment is not created or authorized by a Request, Directory selection, notification, Save action, Declaration or Admin determination. |

The model must not become unrestricted P2P transfer, an open Payee marketplace, remittance, cashout, arbitrary company payment or an open money-request product.

PayPlus is not a wallet, stored-value account, cashout product, open-loop money transfer product, or arbitrary peer-to-peer payment service.

PayPlus is also intended to be data-engine ready by design. MVP features should create structured, classified, auditable, and purpose-linked data that can support service operation, risk control, product analytics, commercial reporting, consented personalization, and future approved AI/model improvement. This does not make AI marketing automation, offsite advertising activation, user-level partner data sharing, credit scoring, or insurance underwriting part of MVP scope.

---

## 3. MVP Scope

### 3.1 In Scope

The MVP includes:

- Payer account registration and login;
- Payer-created controlled Bill sources and Evidence-backed Rent sources and payments;
- specified supported controlled Bill Categories and the separate Rent journey;
- Category-scoped Payee Directory and `Provide Payee myself` as the two Bill Payee-acquisition methods;
- institutional and individual economic Payees who need not be PayPlus Users;
- optional attached-Evidence capture for an initial Bill flow, mandatory owner-approved official Bill Evidence for Tier 2/3, and mandatory attached Evidence for Rent; potential document examples are Evidence only where DOC-12 approves the applicable Category or Rent rule;
- AI/OCR-assisted evidence capture, autofill, user correction, verification, and review routing where enabled;
- preservation of user-selected Company/Individual type, AI-apparent type, Payer response and scoped Admin determination;
- one authoritative Bill/Rent source record with Saved/current, Saved/Archived, history-only and established-but-unprojected treatment as applicable;
- optional Save, no-Save, post-payment Save on the same Bill/Rent ID, and ordinary Archive after Save;
- bounded historical Directory acquisition provenance where applicable;
- Payer review and explicit authorization before each applicable Provider Submission;
- Admin review and operational controls owned by the applicable specialist sources;
- Payment status and Activity/Receipt history;
- audit history;
- receipt or confirmation records;
- basic Payer notifications and an optional Payer-initiated one-way notification to a governed individual Payee where separately permitted;
- sandbox or production-ready payment integration design;
- clear prohibition of wallet, stored balance, cashout, and unsupported P2P use cases.

#### 3.1.1 Accepted Launch Bill Category Inventory

The following twelve supported controlled Bill Categories are Founder-confirmed for the launch inventory. Each name identifies a controlled Bill scope; it does not by itself decide Category-specific eligibility, Evidence criteria, Directory membership, detailed UI labels or approved Copy.

| Order | Accepted launch Category name |
|---|---|
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

Rent is not a Bill Category in this inventory. It remains the separate tenancy/relationship journey.

### 3.1.2 MVP Gating and Configuration

Confirmed MVP scope does not mean every function must be enabled for every user, category, payee type, or launch phase.

The MVP must support independent enablement or disablement of major modules, including:

| Module or Capability | Gating Requirement |
|---|---|
| Controlled Bill Categories | Enable only after Category, Evidence, Payee, destination, payment, payout, risk, privacy, compliance and operational owners confirm applicable readiness. |
| Institutional Payee Programme and Directory | Enrolment, Category association and Directory publication are independently controlled and must not replace transaction-specific checks. |
| Rent and tenancy payments | Enable only when rent evidence, landlord/payee verification, limits, monitoring, and manual review rules are ready. |
| Payment methods | Enable only when approved by PSP/acquirer and compliance review. |
| Payout methods | Enable only when payout provider, rail, timing, exception handling, and reconciliation are ready. |
| Fees and promotions | Enable only when DOC-13 promotion quote, entitlement, discount, coupon, voucher, reward, disclosure, accounting, tax, commercial, and reporting treatment is confirmed. |
| OCR or document AI | Enable by category, payee type, risk tier, document type, and provider readiness; manual or assisted review may be used until automation is approved. |
| Multi-card funding | MVP scope; support up to 6 credit cards per payment/profile, with related controls configurable where applicable. |
| Tokenized cards and saved payment profiles | MVP scope; DOC-06B defines the user route shell, DOC-09 defines checkout use, DOC-16 defines the provider-controlled card-data boundary, DOC-17 owns provider/tokenization mechanics, and DOC-19 defines mechanism-neutral security controls. |
| Payment Instructions and incomplete Checkout continuation | MVP scope. A Payment Instruction is a deliberate pay-later arrangement. An interrupted immediate payment remains an incomplete Checkout Workspace, although both may be surfaced through DOC-06B Instructions routes for user management. DOC-09 owns their Payment Domain distinction and funding rules; DOC-10 owns Payout. |
| Pay+ and Bills entry | The accepted Wave 2 route/action baseline is implemented by DOC-06B: Pay+ retains `Pay a Bill`, `Pay Rent`, `Add Bill / Rent`, and `Continue Payment` in that order and material meaning. `Request Payment` is retired, no replacement action is introduced, and no active Request or BILLS-LINKING capability is part of the target MVP. Exact visual, responsive, accessibility, Copy and implementation evidence remains with its applicable owners. |
| Data and AI readiness | Require business-recording, classification, lineage, auditability, consent/preference, approved-purpose and model-use eligibility obligations where relevant; structured events, fields, persistence, advanced model automation and external activation remain future-gated. |

Current launch assumptions:

- initial launch jurisdiction is Hong Kong;
- acquirer is undecided;
- card payments are expected to be treated as bill payment or ordinary online card purchase, subject to acquirer confirmation;
- PayPlus expects to seek an appropriate or special MCC from the selected acquirer;
- payouts are expected to be made from the PayPlus operating bank account after upstream settlement;
- Hong Kong payout rails include FPS, cheque, and EPS, with final operating-bank setup to be confirmed;
- payment gateway settlement is expected to be T+1 to T+3, with payout on the same day after upstream settlement;
- individual eKYC is expected through an identity-verification provider selected and approved by the applicable formal owners, with identity attributes, provider outcome, and approved ID-document handling; primary-phone possession is verified separately through `PHONE-VERIFICATION`;
- business KYB is expected to require a Business Registration document and owner ID;
- candidate Payer notification channels are app notifications, push notifications, email, SMS, and WhatsApp;
- exact Copy remains with DOC-07; channel and delivery with DOC-08; risk/abuse with DOC-14; privacy, lawful purpose and retention with DOC-15 and applicable professional review; security with DOC-19; support with DOC-21; and permitted Admin execution with DOC-22;
- indefinite retention remains the Founder-approved product and governance direction, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries; that assessment must not silently erase or rewrite immutable financial truth, auditability, Save/Archive history or case lineage;
- exact fee rates, fee allocation, promotion, coupon, voucher, reward, entitlement, refund, and reversal treatment remain to be confirmed by their formal owners and may be made Admin-configurable only after owner approval; multi-card card-count cap is 6 for MVP.

### 3.1.3 Requirement ID Approach

This founder working baseline may describe requirements in concise natural language.

Before AI build-execution conversion or implementation planning, core product requirements, business rules, controls, and testable acceptance criteria should receive stable IDs aligned with DOC-00.

---

### 3.2 Out of Scope for MVP

The MVP does not include:

- user wallet balances;
- stored-value accounts;
- cash withdrawal;
- cashout to self;
- unsupported peer-to-peer transfers;
- crypto payments;
- lending or credit issuance;
- automatic recurring payments unless separately approved;
- deliberate Payment Instructions and incomplete Checkout continuation for single-card and split-card payment are in scope under DOC-06B/DOC-09 and are not automatic recurring payments or the same domain object;
- marketplace escrow;
- investment, savings, or deposit accounts;
- open-loop funds transfer unrelated to an eligible controlled Bill or Rent obligation;
- fully automated compliance approval without admin or risk controls.
- Consumer Payee accounts or active Payee-user navigation as a requirement of receiving payment;
- active Request creation, delivery, reminder, acceptance or reciprocal visibility;
- active BILLS-LINKING or participant-link permission/consent behavior;
- Payee-user notifications or account invitations arising from payment;
- dormant end-to-end Request/Linking queues, APIs, jobs, feature flags or product tests;
- an unrestricted or cross-Category `Provide Payee myself` path;
- a live Directory dependency for Saved Bill/Rent identity or future eligibility.

---

## 4. Product Principles

| Principle | Requirement |
|---|---|
| Controlled Bill/Rent payments | Every Payment must remain linked to a Bill within a specified supported controlled Bill Category or to the separate Rent journey. Bill Tier 1 may omit attached Evidence only under the approved tier policy; Tier 2/3 Bills require owner-approved official Bill Evidence, and Rent always requires owner-approved attached Evidence accepted before Payment. Evidence examples never establish automatic eligibility. |
| Payer-only Consumer User | Consumer product behavior is designed for the Payer. A Payee is the economic recipient and need not be a PayPlus User. |
| Controlled acquisition | The selected supported Bill Category governs Directory selection and self-provided acquisition continuously. Neither method bypasses specialist gates. |
| Authorization required | A payer must authorize payment before funds are charged or moved. |
| No wallet behavior | PayPlus must not create stored balances or user-controlled cash accounts. |
| No arbitrary P2P | PayPlus permits payment only for an eligible Rent journey or specified supported controlled Bill Category under the applicable Declaration, Evidence and specialist gates. Declaration or Evidence alone never creates eligibility outside that boundary; unrestricted person-to-person payment remains prohibited. |
| Authoritative source | A Payment is never source-less. Each Checkout targets one Bill/Rent Payable Basis and executes through DOC-09 Obligation Allocations against one or more applicable Payment Obligations. Each Payment remains traceable to those applicable obligations, that Payable Basis, one authoritative Bill/Rent source, Payer, Payee, destination, status/event history and Evidence lineage where Evidence exists or is required; normally this includes one or more Payment Applications. Under DOC-09's controlled late-confirmation exception, a confirmed Payment may temporarily have zero Payment Applications without becoming invalid or source-less. |
| Projection separation | Save, no-Save and Archive affect Payer reuse and visibility projections without creating, cloning or erasing the authoritative Bill/Rent or immutable financial history. |
| Compliance first | Product behavior must remain within approved regulatory and partner constraints. |
| Data-engine readiness | Material product actions should create structured events and classified data suitable for governed analytics, reporting, and future approved AI/model improvement. |
| Trust-preserving intelligence | Analytics, personalization, partner reporting, and AI use must preserve PayPlus product boundaries, privacy controls, consent rules, role-based visibility, and auditability. |

---

## 5. User Roles

| Actor | Description | MVP login? |
|---|---|---|
| Payer | Consumer User who creates or selects the controlled Bill or Evidence-backed Rent context, makes any required Declaration, chooses whether to Save, and separately authorizes payment. | Yes |
| Payee | Economic recipient, either an individual or institution/company. A Payee may be represented without a PayPlus User account. | Not required |
| Admin / Operations | Internal user executing only owner-required and owner-permitted review or handling for Evidence, type disagreements, risk, Payee/destination facts and exceptions. Admin execution does not create global Payee truth, specialist outcomes or product policy. | Yes |
| System | Automated services supporting Evidence processing, preservation of provenance, payment/payout processing, controlled notifications and audit events. | No |

---

## 6. Core MVP Payer Flow

The core MVP flow allows a Payer to establish or pay a controlled Bill, or pay an Evidence-backed Rent obligation, to an economic Payee under the applicable owner gates.

### Deliberate Setup Bill/Rent

1. Payer logs in and deliberately enters Setup Bill or Setup Rent for reuse.
2. For a Bill, Payer selects a supported controlled Bill Category, then uses the Category-scoped Directory or `Provide Payee myself`; Rent remains a separate tenancy/relationship journey.
3. In the self-provided Bill journey, Payer selects Paying a company or Paying an individual before optional attached-Evidence input. Detailed receiving and payment facts remain owner-governed and must preserve provenance.
4. Payer provides required source facts and may provide attached Evidence for AI/OCR assistance. Tier 2/3 later require qualifying attached Evidence; Tier 1 does not. AI/OCR may derive an apparent Company/Individual type only after Evidence recognition, and a mismatch prompt preserves the Payer response and prior provenance.
5. ID establishment consumes an owner-governed source-preservation eligibility outcome, using Evidence inputs only where applicable. Product and journey documents do not independently define the technical persistence threshold, exact minimum fields, physical identifier generation, Evidence-acceptance criteria, indefinite-retention controls or non-destructive handling mechanics.
6. For Add a Bill, the current proposed amount is assessed against C1 before Save; G1/G2 do not apply or reserve capacity. Rent remains on its existing setup and mandatory-Evidence model.
7. One authoritative Bill/Rent ID is established where the owner-governed preservation outcome permits it. Deliberate Save gives the same ID a current Saved projection without Payment.
8. Saved/current means Payer persistence, visibility and reuse intent only. It does not mean Evidence accepted, Payee verified, destination ready, Payment eligible, standing authorization or future payment approval.
9. Any later Bill Payment re-evaluates C1/G1/G2 and every applicable specialist gate. Any later Rent Payment retains mandatory attached Evidence and Evidence acceptance before Payment.

### Immediate Pay-Now Bill/Rent

1. Payer enters a controlled Bill journey or the separate Rent journey.
2. The journey consumes the applicable owner-governed source-preservation outcome. One authoritative Bill/Rent ID exists before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or downstream payment-facing actions require stable source identity.
3. For Bills, current C1/G1/G2 determines Tier 1, 2 or 3 and the applicable Declaration/Evidence/admission gates in Section 7. For Rent, mandatory attached Evidence and owner-governed acceptance remain Payment gates. Intended-Payee, destination, Payout, sanctions, fraud, anti-cashout, risk, readiness, Checkout and authorization gates remain with their owners.
4. DOC-09 confirms Payment with a separate Payment identity linked to the authoritative Bill/Rent source.
5. Payment Result is shown. If the source was already Saved/current before this Payment, its existing projection remains intact and no duplicate Save is created.
6. For an otherwise unsaved source, the optional Save decision must be resolved before Activity, Payment History, Receipt or ordinary safe exit. Selecting Save makes the same Bill/Rent ID Saved/current. Declining, skipping, dismissing, closing or otherwise leaving the Save decision without selection makes the same ID history-only.
7. Only after that existing-projection or Save-resolution outcome may the route continue to Activity, Payment History, Receipt or ordinary safe exit. Payment, Activity, Payment History and Receipt exist independently of Save, but they do not bypass the required projection resolution.

### Established but abandoned pre-Payment source

Where an authoritative Bill/Rent ID is established but an immediate-pay journey ends or fails before confirmed Payment, ID establishment alone does not make it Saved/current, Saved/Archived or history-only, expose a Bills/Rent route or list entry, or create a user-facing status. The same unprojected boundary applies where deliberate setup ends before Save/current projection is completed. It never applies after a newly confirmed Payment for an otherwise unsaved source: closing or leaving Payment Result without selecting Save is skipped Save and resolves the same ID to history-only before downstream handoff. DOC-09 owns applicable payment-lifecycle continuation/recovery, DOC-15 owns retention governance and requirements, and DOC-18 requires the source facts, projection distinction, historical action basis and owner handoffs to remain explainable. Exact technical lifecycle representation remains separately authorized future work.

DOC-09 derives payment-facing facts and evaluates Payment Obligation and Checkout eligibility. No Request, Payee acceptance, Directory state, Save action, notification or type label authorizes payment. Payment and Payout proceed through DOC-09 and DOC-10 controls. A Payment remains visible through Activity/Payment History/Receipt after either post-Payment Save branch.

---

## 7. Bill-only Tiered Evidence, Declaration, Payment and Payout Policy

This section owns the high-level product policy approved for Bills. It does not redefine DOC-09 Payment Domain objects, DOC-10 Payout, DOC-11 Refund/case treatment, DOC-12 Evidence truth, DOC-14 risk outcomes, DOC-18 business-recording and explainability obligations, or DOC-22 execution.

### 7.1 Terms and scope

| Term | Product meaning |
|---|---|
| Evidence | Attached Evidence. |
| Declaration | The Payer's factual and intent declaration concerning Category, purpose, amount and Payee/receiving details under the owner-approved Declaration policy. |
| Payment | The Payer pays on PayPlus; DOC-09 owns the immutable confirmed financial meaning. |
| Payout | PayPlus pays the designated economic Payee; DOC-10 owns release and reconciliation. |

Evidence, Declaration, Checkout, Payment, Payment Application, Payout, Refund, case, adjustment and reconciliation remain distinct.

The tiered policy applies only to Bills. Rent remains under its existing mandatory attached-Evidence model: attached Rent Evidence and the required Evidence acceptance remain Payment gates. A Rent-specific Declaration, if defined by its owner, cannot replace, waive, reduce or defer those Evidence requirements. Bill C1/G1/G2, Tier 1/2/3 and official Bill Evidence rules do not apply to Rent.

### 7.2 Bill limits

| Limit | Product invariant | Ownership boundary |
|---|---|---|
| C1 - Category single-Payment threshold | Each controlled Bill Category has an approved single-Payment threshold. For prepayment, use the selected-period aggregate. | C1 policy authority belongs to the designated product/risk owner. DOC-12 binds the applicable Category configuration, DOC-09 consumes it, and DOC-22 only executes approved configuration. Exact Category values, permitted adjustments, configuration representation and operating change details are later owner-defined configuration/enablement inputs; they do not reopen the settled layering. |
| G1 - receiving-destination frequency | Maximum five independent user-initiated Bill payment progressions to the same receiving account/authoritative payout destination per Hong Kong calendar month. One progression/Checkout counts once despite split-card Funding Legs, Payment Attempts, confirmed Payments, retries, recovery or continuation. A genuinely new independent progression counts again. | G1 is product-semantic and is not bound here to authorization, Provider Submission, Payment confirmation, a status, an event or a schema. DOC-18 requires the accepted fact, action basis and history to remain explainable; exact technical representation requires separate Engineering/Data authority. The receiving account/authoritative payout destination is the counting key, not economic-Payee identity. |
| G2 - monthly confirmed Bill value | Maximum HKD1,000,000 per verified Payer account per Hong Kong calendar month. Pre-check confirmed monthly Bill usage plus the proposed obligation-funded amount; final usage records actual successfully confirmed obligation-funded value. | DOC-09 consumes the Payment facts; DOC-14 supplies risk/control treatment; DOC-18 requires the accepted rule and historical basis to remain explainable. Exact technical representation remains separately gated. Payer fees are excluded. |

G2 permanent-capacity treatment:

- failed, declined, cancelled-before-confirmation and proven duplicate attempts do not permanently consume capacity;
- confirmed Payments remain in the original Hong Kong month after Refund or reversal;
- only a confirmed duplicate/error correction restores capacity; and
- a projected Tier 3 decision is not retroactively downgraded when actual confirmed value later remains below HKD1,000,000.

### 7.3 Highest-tier precedence

When multiple limits trigger, retain every trigger reason but execute only the highest Tier workflow:

```text
G2 triggered
-> Tier 3

No G2, but C1 or G1 triggered
-> Tier 2

No C1/G1/G2 trigger
-> Tier 1
```

G1 exceedance does not prohibit Payment; it elevates the Bill progression to Tier 2. Exact equality to an approved maximum remains within that maximum.

### 7.4 Tier gates

| Gate | Tier 1 | Tier 2 | Tier 3 |
|---|---|---|---|
| Declaration | Required | Required | Required |
| Attached Evidence | Not required | Owner-approved official current/historical Bill Evidence required | Owner-approved official current/historical Bill Evidence required |
| Evidence presence | No Evidence-specific Payment gate | Payment gate | Payment and Payout gate |
| Evidence acceptance | Not a Tier 1 attached-Evidence gate | Payout gate; Payment may confirm while verification remains pending | Required with authorized approval before Payment and Payout progression |
| Human review | Only where another owner gate requires it | Exception-only owner-approved review for unresolved cases | Mandatory authorized approval |
| Checkout | Executable only when all other applicable gates pass | Executable after Evidence presence and other applicable Payment gates pass | A prepared Checkout Workspace may exist, but it remains non-executable before approval |
| Provider Submission and confirmed Payment | Ordinary DOC-09 rules | Ordinary DOC-09 rules after Evidence presence | Prohibited before approval |
| Payout | All applicable non-Evidence release gates | Held until Evidence acceptance and every other release gate passes | Held until Evidence, approval and every other release gate passes |

Tier 3 approval is an admission gate before the First Provider Submission. Before approval there is no executable Payment authorization, Provider Submission or confirmed Payment. Material changes to the approved Category, purpose, amount, Payee or receiving details require Tier and approval re-evaluation. No separate Tier 3 recovery object is created.

An owner-recorded Tier 3 approval outcome keeps the Payer in, or returns the Payer to, the current Bill context. It is not navigation authority, Payer authorization, Provider Submission, or a direction to open an executable Checkout. A deliberate current `Pay` action invokes the DOC-09 Checkout Resolver. The resolver may Resume a prepared Workspace only when current revalidation confirms it remains active, eligible and continuable; every later Provider Submission still requires fresh Payer authorization. Otherwise the resolver returns the applicable source-owner or historical resolution. This policy creates no Tier-specific route, notification or automatic continuation.

### 7.5 Owner-approved official Bill Evidence

Tier 2/3 mandatory Evidence means owner-approved official current/historical Bill Evidence. Potential formal document examples include an official bill, invoice, fee notice, payment statement, school payment notice or formal receipt used as historical Evidence. These examples are not automatically accepted types.

DOC-12 defines the acceptance framework, issuer attribution, provenance, integrity, Category fit, relationship to declared facts, temporal relevance, duplicate/reuse treatment and acceptance. Category-by-Category operating lists remain later owner inputs and block affected-path enablement and acceptance until supplied. WhatsApp or other communication-originated material cannot satisfy, substitute for or contribute to the mandatory Tier 2/3 requirement. Any future supplementary investigation use remains outside the core Bill Payment eligibility model.

Evidence presence, extraction, automated result, owner acceptance, Tier 3 approval, Payment and Payout remain separate.

### 7.6 Declaration policy

- Unchanged declared facts require no new Declaration.
- C1/G1/G2 re-evaluation by itself is not a Declaration trigger.
- User changes to Category, purpose, amount or Payee/receiving details are subject to owner-defined materiality and proportionate reconfirmation.
- The Declaration owner may require field-specific confirmation, a refreshed summary or a full Declaration according to the accepted policy; every amount edit does not automatically require a full Declaration.
- Declaration, Save/persistence intent and Payment authorization remain separate and auditable.
- Declaration does not replace Evidence where required, payer authorization, account security, sanctions, prohibited-purpose, intended-Payee, destination, risk, provider or Payout gates.

DOC-05 owns the product-policy framework. DOC-07 owns final user-facing expression; DOC-09 consumes current facts and preserves separate Provider Submission authorization; DOC-15 owns privacy and retention controls. Exact operating materiality tests and reconfirmation presentation remain later owner-defined product/content/acceptance inputs unless a future answer contradicts the approved proportionate rule.

At Add a Bill, the Payer reviews the declared material facts and deliberately confirms them before the separate Save-admission decision. An unchanged or owner-confirmed non-material edit uses ordinary Save. A material change receives the owner-defined proportionate reconfirmation before the changed facts are relied upon. Paying a Bill with unchanged declared facts does not repeat Declaration solely because C1/G1/G2 is re-evaluated; every applicable Provider Submission remains separately authorized.

The DOC-18 business-recording handoff preserves four distinct Declaration occurrence contexts without deciding wording, legal sufficiency, UI, or reconfirmation mechanics: Add Bill; a Pay progression that establishes a new Bill/Rent source; an applicable owner-defined Bill/Rent source setup; and a material change to a Saved Bill/Rent source.

For owner-summary consistency, the settled material Bill facts are Category, Bill Date, declared purpose, economic Payee, Bill Amount, Payee bank name, bank code, and bank account number. The settled material Rent facts are address, period, Rent Amount, Due Day, landlord/economic Payee, Payee bank name, bank code, bank account number, stated payout method, Payer-to-tenant relationship, tenant name, and tenant mobile where applicable. Bill remark remains normally non-material; optional landlord contact remains optional with no inferred materiality. Rent Amount and each Payment Amount remain distinct, and a difference does not by itself imply an anomaly. Category is an amendable material Bill fact on the same Bill identity: the current Category changes, every prior Category remains material history, and no reason is inferred. These are business-recording and explainability facts, not a schema or field catalogue.

### 7.7 Add, Pay and prepayment boundaries

| Path | Required treatment |
|---|---|
| Add a Bill | Apply C1 only as the Save-admission assessment. If the amount exceeds C1, Save is not permitted. G1/G2 do not apply and no monthly capacity is reserved. Save does not mean verified, ready or approved. |
| Pay a Bill | Re-evaluate current C1/G1/G2 using current facts and current approved configuration. A prior Save assessment neither reserves capacity nor guarantees the Payment-time Tier. |
| Prepayment | Preserve existing Category eligibility. Test the selected-period aggregate against C1/G2. One independent user-initiated progression counts once under G1 despite multiple periods, cards or Funding Legs. Prepayment does not override any gate. |

Prepayment is Category-controlled and must not be represented as automated current/specified-period/continuing Evidence coverage.

### 7.8 Evidence reuse and later-payment boundary

| Context | Product-policy boundary |
|---|---|
| Bill | Bill date and amount are not reusable. Other owner-permitted stable context may be prefilled only and remains subject to current Declaration, Tier, destination, risk and authorization rules. |
| Rent | Tenancy context and applicable accepted Evidence may support later Rent periods until expiry, replacement or material change requires renewed Evidence treatment. The mandatory Rent Evidence gate remains. |
| Every later Payment | Destination, risk, sanctions, readiness, period-specific obligation facts and Payer authorization remain current-owner decisions. |
| Save and duplicate controls | Repeated Save of the same authoritative identity is idempotent. Duplicate Payment, duplicate Evidence and risk controls remain separate. |

---

## 8. Institutional Payee Programme and Bill Payee Acquisition

### 8.1 Ownership and Scope

DOC-05 owns the bounded human product policy for the Institutional Payee Programme and Category-scoped Payee Directory. DOC-22 executes permitted Admin work and configuration but does not own programme, Category or Directory policy.

| Bill acquisition method | Product meaning |
|---|---|
| Category-scoped Payee Directory | Payer-facing selection convenience and bounded higher pre-trust for enrolled, Category-associated and published institutional Payees. It is not Evidence truth, Payee or destination verification, transaction eligibility, risk clearance, Payment Obligation readiness or Payer authorization. |
| `Provide Payee myself` | Category-governed alternative for a non-enrolled institution, an institution not displayed in the Directory, an individual Payee, or a Payer who does not use the Directory. It is never free-form or an escape from Category policy. |

### 8.2 Institutional Lifecycle and Separate Dimensions

Institutional programme enrolment uses only these concise concepts:

- `Not enrolled`;
- `Enrolment in progress`, only after a real enrolment process begins;
- `Enrolled`;
- `Not applicable for individuals`.

| Dimension | Required separation |
|---|---|
| Programme enrolment | Institutional participation in the bounded programme. It does not establish payment eligibility. |
| Category association | Categories for which the institution may be considered for Directory publication or other programme treatment. |
| Directory publication | Whether the institution is displayed for new Category-scoped discovery. |
| Acquisition source | Whether a Payer acquired the Payee through Directory selection or self-provision. |
| Evidence/Payee match | Transaction-specific Evidence assessment owned by DOC-12. |
| Destination readiness and Payout | Context-specific destination and Payout controls owned by DOC-10 and related specialist owners. |
| Risk disposition | Sanctions, fraud, anti-cashout and related treatment owned by DOC-14 and applicable control owners. |
| Payment Obligation readiness and authorization | Payment meaning and Payer authorization owned by DOC-09. |

No composite `Approved Payee` status may collapse these dimensions.

### 8.3 Directory Change and Provenance

Directory unpublication stops only new Directory display and discovery. By itself it does not delete, hide, rename, disable or invalidate a saved Bill/Rent, correct Payee/payment facts, or an in-progress or future payment.

Unpublication remains separate from Category disassociation, commercial offboarding, programme or risk suspension, invalid destination, fraud, sanctions, legal prohibition and security compromise. Those owner-controlled restrictions remain effective and must be evaluated independently of Directory publication; they cannot be bypassed through `Provide Payee myself`.

Where applicable, retain only this bounded historical acquisition provenance:

- `Directory-selected` or `Self-provided`;
- acquisition-time stable institution/Directory reference, if one already exists;
- acquisition Category, timestamp and relevant lineage reference.

The provenance supports audit and troubleshooting only. It does not govern Saved Bill/Rent identity, visibility, usability or future eligibility and must not require a live Directory lookup.

### 8.4 Future Dedicated-Owner Threshold

A future dedicated Institutional Programme owner requires handling under the canonical PayPlus Documentation Development Workflow and is warranted only when the programme becomes an independently governed domain, such as through multiple programmes, markets or publication channels; material contractual/commercial onboarding and offboarding; reusable cross-product institutional entitlements; complex Category-association or termination policy; independent SLAs, disputes, reporting or integrations; or policy volume that DOC-05 can no longer express compactly.

---

## 9. Payee Type, Notification Boundary, and Request/Linking Retirement

### 9.1 Company/Individual Provenance

| Fact | Requirement |
|---|---|
| User-selected type | Preserve the Payer's pre-Evidence choice of Paying a company or Paying an individual. |
| AI-apparent type | Preserve each material post-recognition Company/Individual assessment and its provenance. It does not overwrite the Payer selection. |
| Payer response | Preserve whether the Payer accepted or declined a mismatch prompt. A decline does not make the Payer selection system truth. |
| Admin determination | Preserve the scoped reviewed determination without overwriting earlier facts. It does not create global Payee truth, programme enrolment, permanent eligibility or destination approval. |
| Review and resolution | `Reviewed` and `Resolved` remain separate dimensions. |

A declined type mismatch creates an Admin review obligation. If the disagreement is exclusively the Company/Individual label and the intended Payee, Evidence, beneficiary/agent relationship, Category, destination, sanctions, fraud, anti-cashout, payout readiness and Payer authorization independently pass, payment may proceed. This review may be asynchronous and need not create a user-facing payment-review status. Concrete defects remain capable of blocking their applicable owner-controlled product, Payment, Payout, risk or readiness outcome.

### 9.2 Individual-Payee Notification Boundary

An institution/company Payee is not notified in MVP. A governed Individual determination is required before an individual Payee may receive an optional Payer-initiated one-way notification through a separately permitted PayPlus method. The Payer's pre-Evidence selection, AI-apparent type or Payer response alone is insufficient.

The notification must not create or require a Request ID, account lookup, PayPlus account invitation, participant link, acceptance/decline state, consent proof, reciprocal visibility, Payee authorization or payment/Payout gate. Delivery failure or suppression does not change payment outcome, and Payer-entered contact does not establish recipient identity or Individual truth.

When Company/Individual type remains unresolved, payment may proceed if otherwise eligible but the individual-only notification remains unavailable. Payer responsibility for contact input does not remove PayPlus lawful-purpose, minimization, wrong-recipient, abuse/rate-limit, suppression/opt-out, security, delivery-record, retention and support obligations.

DOC-05 owns only the eligibility and product-meaning boundary. DOC-07 owns Copy/disclosure/CTA; DOC-08 owns notification identity, channel, template, preference and delivery; DOC-14 owns abuse/risk controls; DOC-15 owns privacy and retention requirements; DOC-18 owns business-recording, audit-meaning and lineage obligations; DOC-19 owns security; DOC-21 owns support/operations; and DOC-22 executes only permitted Admin handling. Exact technical representation and mechanics remain separately gated.

### 9.3 Request and BILLS-LINKING Retirement

The Payer-only target formally retires active Request and BILLS-LINKING behavior rather than retaining a disabled dormant product.

| Preserve narrowly | Retire from active product |
|---|---|
| Retired stable IDs, actor/role-at-time meanings and prior invitation/acceptance/decline/consent concepts in append-only documentation history. | Payee-user navigation and reciprocal visibility. |
| Governance-required append-only documentation history; there is no production Request/Payee-role data to expose. | Request creation, delivery, reminder and acceptance. |
| Obligation, Payee, destination, Payment, Payout and notification lineage. | Participant-link permissions and consent state machines. |
| Append-only documentation history and retired stable IDs as non-active documentation evidence. | Payee-user notifications or runtime historical-reader UI. |
| No production legacy Request records or deep-link behavior exist; no adapter or fallback is required. | Dormant end-to-end queues, APIs, jobs, feature flags, product tests, deep-link adapters or fallback routes. |
| Neutral future-compatible Party, Payee and Obligation seams. | Prebuilt future participant Linking or institutional landlord/property-manager discovery. |

Prior Request meanings remain only in append-only documentation history and retired stable IDs. PayPlus has no production Request/Payee-role runtime or legacy Request deep-link data to expose through a reader, adapter or fallback. Future participant Linking requires a separately governed domain and approval.

---

## 10. Bill/Rent Identity, Save, and Payment Rules

### 10.1 Authoritative Source and Projections

Use one authoritative Bill/Rent source record with multiple user-facing projections. ID establishment consumes an owner-governed source-preservation eligibility outcome, which may include Evidence inputs where applicable but does not impose attached Evidence on Tier 1. DOC-05 defines the product-policy boundary and does not independently define the technical persistence threshold, exact minimum fields, physical identifier generation, Evidence-acceptance criteria, indefinite-retention controls or non-destructive handling mechanics. The authoritative ID exists before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or a payment-facing handoff requires stable source identity.

| Projection | Meaning |
|---|---|
| Authoritative source identity | A stable source reference established only after the applicable owner-governed preservation-eligibility outcome. It is distinct from Evidence acceptance, Payee verification, Payment readiness, Payment identity and every user-facing projection. |
| Saved/current | The Payer deliberately chose Save during setup or selected post-Payment Save, so the same authoritative identity is persisted and visible in the current/active Bill or Rent presentation for reuse. It may have an Under Review, Action Required or Ready handling/readiness condition without changing the projection. It does not establish Evidence acceptance, Payee verification, destination readiness, Payment eligibility or standing authorization. |
| History-only | A confirmed Payment for an otherwise unsaved source followed by declined, skipped, dismissed, closed or otherwise abandoned post-Payment Save resolution produces this treatment. The same authoritative source remains internal and linked to financial history, is neither Saved/current nor Saved/Archived, and is not visible through Bills/Rent UI. Related Payment, Activity/Payment History and Receipt remain visible after that resolution. |
| Established but unprojected | An authoritative ID exists after an immediate-pay journey ends or fails before confirmed Payment, or after deliberate setup ends before Saved/current projection is completed. No Saved/current, Saved/Archived or history-only treatment, user-facing status, Bills/Rent route or list entry is implied. This treatment cannot apply after a newly confirmed Payment for an otherwise unsaved source; that source must resolve to Saved/current or history-only before downstream handoff. DOC-09 owns applicable payment-lifecycle continuation/recovery, DOC-15 owns retention governance and requirements, and DOC-18 requires the business facts, distinction, history and action basis to remain explainable. Exact data/status/event and technical lifecycle representation remains separately gated. |
| Saved/Archived | A previously Saved/current Bill/Rent is moved from the current presentation to the governed Archived presentation. Archived sources do not appear in the active/current list. Archive is not a readiness or financial status and does not erase the authoritative source, Evidence, Payment, destination, Payout, reconciliation or audit history. Exact Restore, prior-version and Evidence-version behavior remains deferred. |

One Bill/Rent may support multiple Payment Obligations, Checkouts and Payments. Payment Result and Bill/Rent are not parent/child. A Payment has a separate DOC-09-owned Payment identity linked to the source. Save does not first create or clone the source, create Payment, copy Payment history, establish a new identity or merge similar records. A source already Saved/current before Payment retains that projection without duplicate Save. For an otherwise unsaved source, post-payment Save resolution operates on the same ID: selected Save enables Saved/current, while declined, skipped, dismissed or abandoned Save resolution produces history-only before Activity, Payment History, Receipt or ordinary safe exit.

No later Save-from-Activity route or behavior is accepted. No separate Unsave action is required; once saved, ordinary Archive applies.

### 10.2 Payment Rules

| Rule | Requirement |
|---|---|
| Payment purpose | Payment must remain tied to an eligible controlled obligation. Bill Tier 1 may omit attached Evidence only under Section 7; Tier 2/3 Bills and all Rent use their required Evidence gates. |
| Payer consent | Payer must explicitly authorize payment. |
| Payee payout | Payee may receive payment only through approved payout channels. |
| No self-cashout | Payer cannot use PayPlus to cash out to themselves. |
| No unsupported transfer | Payment must remain tied to a Bill within its specified supported controlled Bill Category or to the separate Rent journey. Evidence form alone does not create another payment scope. |
| No stored balance | PayPlus must not hold user wallet balances. |
| Failed payment handling | Failed payments must be visible and traceable. |
| Payment continuation revalidation | A pending Payment Instruction or incomplete Checkout Workspace must revalidate applicable amount, fee, benefit, funding-method, destination, eligibility, and risk facts before Provider Submission where required by DOC-09 and DOC-13. |
| Refunds/reversals | DOC-11 owns refund, cancellation, reversal, dispute and chargeback meaning. DOC-22 may execute only the Admin treatment permitted by DOC-11 and the applicable payment, data, privacy and operations owners; DOC-05 grants no generic status or disposition authority. |
| Source lineage | Every Payment remains linked to the applicable Payment Obligations, their Payable Basis and the authoritative Bill/Rent source; normally this lineage includes one or more Payment Applications. DOC-09's controlled late-confirmation exception may temporarily have zero Payment Applications, without making Payment ID alone sufficient source context or deciding Payout, reconciliation, or adjustment treatment. |
| Save separation | Save, no-Save, post-payment Save and Archive do not authorize payment or mutate immutable Payment/Application facts. |

---

## 11. Admin and Specialist-Owner Handoffs

DOC-05 defines when product policy requires a bounded Admin or operations handoff; it does not grant generic access, queue, action, disposition or override authority. DOC-22 executes only the specifically owner-permitted operation and does not independently own workflow, permission, queue or configuration policy. DOC-15 governs approved-purpose access and masking, and DOC-18 owns business audit-meaning, history and lineage obligations.

| Concern | Product-policy boundary | Primary owner and Admin handoff |
|---|---|---|
| Institutional Payee Programme | Permitted enrolment, Category association and Directory publication work implements DOC-05 policy without creating transaction eligibility or global Payee truth. | DOC-05 policy; DOC-22 execution; DOC-02/DOC-03/DOC-04 and other specialists where their concerns apply. |
| Company/Individual disagreement | Preserve Payer selection, AI-apparent assessment, Payer response and the scoped reviewed determination. `Reviewed` and `Resolved` remain separate, and label-only review may be asynchronous and nonblocking. | DOC-05 product meaning; DOC-12/DOC-14/DOC-15 outcomes where applicable; DOC-22 execution. |
| Evidence and Evidence-to-Payee | Admin receives only the context and fields permitted for an owner-required review. DOC-05 does not decide Evidence acceptance, duplicate treatment or a review disposition. | DOC-12 policy/outcome; DOC-14 risk where applicable; DOC-15 access; DOC-22 execution. |
| Payment and payer authorization | Admin handling cannot create a Payment Obligation, make Checkout ready, authorize Payment or rewrite immutable Payment facts. | DOC-09 policy/outcome; DOC-15 access; DOC-18 business history/explainability; DOC-21 consume-only operations; DOC-22 specifically permitted execution. |
| Destination, Payout and reconciliation | Admin handling cannot approve a destination globally or replace destination-readiness, Payout or reconciliation outcomes. | DOC-10 policy/outcome; DOC-14 risk where applicable; DOC-15 access; DOC-22 execution. |
| Refund, cancellation, reversal, dispute and chargeback | Admin handling consumes the applicable owner-controlled case and outcome; DOC-05 defines no generic approve, reject, hold, cancel or resolve action. | DOC-11 policy/outcome; DOC-15 access; DOC-18 business history/explainability; DOC-21 consume-only operations; DOC-22 specifically permitted execution. |
| Risk, sanctions, fraud and anti-cashout | Admin execution cannot waive, reinterpret or replace the applicable risk outcome. | DOC-14 policy/outcome; DOC-15 access; DOC-18 business history/explainability; DOC-21 consume-only operations; DOC-22 specifically permitted execution. |
| Privacy, support and audit | Access is approved-purpose, masked and auditable. Support and operational handling cannot create product, Evidence, Payment, payout, refund or risk truth. | DOC-15 privacy/access/retention; DOC-18 business audit meaning/history; DOC-21 consume-only support/operations; DOC-22 specifically permitted execution. |

Every permitted Admin action must be permissioned and auditable under its formal owners. A scoped Admin determination or action does not create global Payee truth, programme enrolment, permanent eligibility, destination approval, Evidence acceptance, Payment readiness, payer authorization or a new cross-domain override.

---

## 12. Compliance and Risk Controls

### 12.1 Required MVP Controls

| Control | Requirement |
|---|---|
| Identity/account controls | Payer accounts must have appropriate onboarding and access controls. Institutional programme/KYB and economic-Payee controls remain separate from Consumer User login. |
| Evidence requirement | Bill Tier 1 does not require attached Evidence; Tier 2/3 Bills require owner-approved official Bill Evidence; Rent always requires attached Evidence accepted before Payment. |
| Evidence verification | OCR/autofill, user correction, duplicate/reuse detection, mismatch checks, verification outcomes, official Bill Evidence acceptance and Rent acceptance follow DOC-12. Tier 2 presence and acceptance remain separate gates. |
| Payer authorization | Payer approval is required before payment. |
| Payee verification | Payee details must be verified according to approved operational policy. |
| Risk review | Payments, Evidence, Payees, beneficiaries/agents and destinations may be subject to owner-controlled review or blocking treatment. Label-only disagreement is not a substitute for those checks. |
| Duplicate detection | System should help identify duplicate Bills, Evidence or Payments without treating idempotent Save as a duplicate-record problem. |
| Transaction limits | Apply approved C1/G1/G2 Bill limits and highest-tier precedence under Section 7. Exact C1 authority/values remain owner-readiness items; DOC-22 executes only approved configuration. |
| Audit logging | Key actions must be logged. |
| Dispute handling | Payer and payee disputes must be traceable. |
| Restricted use prevention | Wallet, cashout, and unsupported P2P behavior must be blocked. |

---

## 13. Notifications

The MVP should support these basic Payer-facing notifications:

- account registration;
- Evidence received or requiring Payer action;
- payment authorized;
- payment processing;
- payment completed;
- payment failed;
- payout completed, if applicable.
- as the only Payee-facing exception, an optional Payer-initiated one-way notification after a governed Individual determination, where DOC-08 and all applicable owners permit it.

No notification channel is selected by DOC-05. DOC-05 owns only the eligibility boundary; DOC-07 owns approved Copy/disclosure/CTA, DOC-08 owns notification identity/channel/template/preference/delivery, DOC-14 owns risk and abuse controls, DOC-15 owns privacy and retention requirements, DOC-18 owns business-recording and audit-meaning requirements, DOC-19 owns security requirements, DOC-21 owns support/operations, and DOC-22 performs only permitted Admin execution. Contact provenance and lawful-basis or consent treatment remain with their applicable formal owners. DOC-12 supplies any Evidence-derived classification input but does not own notification delivery.

The MVP Notifications route family separates Inbox category, recipient read/archive state, owning-domain status, and owning-domain `Action Required`. Current Payer route behavior remains owned by DOC-06B and DOC-08. Read/archive actions must not change the underlying payment, payout, Evidence, reward, support, privacy or other domain state. Active Request/Linking notification and route behavior is retired from MVP. Retired IDs and prior meanings remain append-only documentation history only; no runtime reader exists or may be inferred.

---

## 14. Data Requirements

The MVP must preserve product-level identity, lineage and provenance for the following record families. DOC-18 owns that business-recording and explainability obligation. Detailed fields, physical IDs, relationships, schemas, machine events, indexes, data-model representation and ledger behavior remain separately authorized future Engineering/Data work; DOC-15 owns privacy classification, masking, approved-purpose access, retention governance and retention requirements.

- Payer account, identity, authentication, security and KYC context;
- authoritative Bill/Rent source identity, Save intent, current or Archived projection, history-only treatment and separate readiness/handling condition;
- Evidence/document lineage, extraction, permitted Payer correction, verification and review outcome;
- institutional programme enrolment, Category association and Directory publication as separate dimensions;
- Bill Payee acquisition method, acquisition Category, acquisition timestamp, relevant lineage reference and acquisition-time stable institution/Directory reference where one already exists;
- Payer-selected Company/Individual type, each material AI-apparent assessment, Payer response and scoped Admin determination without overwriting prior provenance;
- Payable Basis, Payment Obligation, Checkout, Funding Leg, Payment, Payment Application, Payment Instruction, payout, settlement and reconciliation lineage under their specialist owners;
- destination snapshots and other owner-governed transaction facts;
- optional individual-notification eligibility and delivery lineage without a Request or participant link;
- retired Request/Linking IDs and prior actor/role-at-time, invitation, acceptance, decline and consent meanings in append-only documentation history only; Founder confirmation establishes that no production Request/Payee-role records or runtime lineage exist;
- tokenized card and payment-profile records;
- Bill/Rent reminders where enabled;
- campaign, offer, promotion, entitlement, reward and fulfilment records where enabled;
- dashboard and shortcut configuration and Payer preference records where enabled;
- dispute, clarification, support, notification, audit and Admin-review records.

Each material object remains subject to DOC-15 classification, masking, approved-purpose access and retention governance. Material user, system and Admin actions require auditable source lineage. Acquisition provenance and projection state must not become substitute payment eligibility, destination truth, risk clearance or authorization.

Detailed data model, event taxonomy, warehouse, analytics, feature/model metadata, aggregation, lineage and reporting requirements for current product objects remain for DOC-18 and later authorized Waves. No Request/Payee-role runtime reader or production lineage is implied.

---

## 15. UX Requirements

The MVP should include the following UX surfaces. Detailed route flows, service blueprint steps, and non-payment interaction rules belong in the DOC-06 family. DOC-06B owns `PAYMENT-CHECKOUT` route-level UI/UX, adaptive Workspace presentation, entry, return, and handoff behavior. DOC-09 owns Payment Domain architecture, objects, invariants, and authoritative payment meaning. DOC-05 remains the product requirement and feature index and does not duplicate detailed Checkout UI.

DOC-06 is the parent UX family map. DOC-06A owns core service journeys, DOC-06B owns navigation, route taxonomy, and human-readable route-level UX for global non-Bills routes, DOC-06C owns Bills/rent/tenancy UX, and DOC-06D owns UX requirement/test mapping. Product requirements in DOC-05 should reference stable product destination IDs where useful, use specific child destinations where defined, and avoid duplicating screen-level routing rules.

For split UX topics, use one primary owner. DOC-06A owns core Payer journeys, DOC-06B owns global navigation, Activity/Payment History/Receipt separation and active Request/Linking route retirement, DOC-06C owns Bills/Rent acquisition, visibility, Save and Archive presentation, and DOC-06D owns testability mapping. The current Wave 2 DOC-06 baseline addresses the accepted route retirement and Save/Archive meaning; related owner work remains with the applicable formal owners, and no downstream document may override the product policy in this document.

Stable global destination IDs are mandatory for traceability even where detailed UI remains incomplete. `ENTRANCE-ROOT` is the unauthenticated app root; `AUTH-LOGIN` resolves to `AUTH-LOGIN-FAST` or `AUTH-LOGIN-FULL`; `AUTH-RECOVERY` owns password recovery; and `AUTH-REGISTRATION` owns restricted-account creation. `ACCOUNT-ACTIVATION` completes phone, identity, and payment-passcode requirements through their reusable child flows. Normal successful login proceeds to `HOME-ROOT`, subject to approved contextual deeplink return. `PAYPLUS-ACTION-SHEET` and `MORE-ROOT` identify the Pay+ and More destinations. `NOTIFICATION-ROOT` groups Inbox, Detail, and Settings, with `NOTIFICATION-INBOX` as its default child. `PAYMENT-CHECKOUT` identifies the existing payment checkout flow/screen group; DOC-06B owns its route-level UI/UX, adaptive Workspace presentation, entry, return, and handoff behavior, while DOC-09 owns its Payment Domain architecture and authoritative payment meaning.

Material AUTH handling must separate the operation Outcome from its permitted Resolution Strategy, user-facing Message/CTA, Notification, and persistent status. Capability-aware resolution may continue, restart, redirect, wait, invoke controlled Support, or stop according to the current permitted authentication and recovery context. It must not reveal unproven login methods, create a security bypass, silently authorize a protected action, or imply that every account can be recovered. DOC-06B owns route-level Outcomes and Resolution Strategies; DOC-07 owns presentation; DOC-08 owns notifications; and DOC-18 to DOC-22 own their respective technical, security, testing, operational, and admin details.

PayPlus uses one account with one unique verified primary email and one or more explicitly enabled login methods. Email/password, Google, and Apple may access the same account only after the provider identity is explicitly linked; matching email addresses never merge or link accounts automatically. Social-authenticated users may set a PayPlus password later through `ACCOUNT-SECURITY`. Before account creation, a temporary registration attempt creates no account and reserves no proposed identifier. Restricted account creation may reach `HOME-ROOT` before phone verification, identity verification, and six-digit payment-passcode setup; `ACCOUNT-ACTIVATION` must complete those gates before the registration-level restriction is removed or a financially restricted action proceeds.

The current Wave 2 DOC-06 baseline retires active Request and Payee-user actions in the `PAYPLUS-ACTION-SHEET` and Bills-route surfaces. `PAYPLUS-ACTION-SHEET` retains, in the accepted order and material meaning, `Pay a Bill`, `Pay Rent`, `Add Bill / Rent`, and `Continue Payment`; Request Payment is retired and no replacement action or route is created. That composition, order, material labels and destinations are not open. Exact visual treatment, responsive and accessibility behavior, Copy detail, technical implementation and acceptance evidence remain with their applicable formal owners.

`MORE-ROOT` is one route with Normal and Manage Shortcuts modes. Home has a default and maximum of 8 shortcuts: up to 7 user-configurable entries plus protected `More`, which remains visible as the final shortcut. Users may keep fewer configurable shortcuts, reorder or remove eligible entries, add approved entries, save account-level preferences, and restore the current eligible owner-approved default. More may also open approved secondary services but does not own them or replace `ME-ROOT`.

For growth UX, `OFFERS-ROOT` owns promotion discovery; its child screens `OFFERS-CARD-LIST`, `OFFERS-PAYPLUS-LIST`, and `OFFERS-PARTNER-LIST` own the respective View More collections; `REWARDS-ROOT` owns issued-reward management through Active and History views; and the `REFERRAL-ROOT`, `REFERRAL-REWARDS-LIST`, `REFERRAL-ENTITLEMENT-DETAIL`, and `REFERRAL-REWARD-CLAIM` route family owns referral sharing, attributed-referee qualification progress, and role-sensitive referrer/referee reward claiming. `REWARD-DETAIL` owns full reward information and terms but is not a second checkout route; checkout reward selection remains in DOC-09 after card/profile selection. The Referral Rewards list uses `Available to Claim` and `History` route-local tabs; claimed reward use remains in canonical Rewards. One offer may belong to multiple discovery collections, while unintended repeated display of the same Offer ID is suppressed on `OFFERS-ROOT`. Direct checkout discounts are not issued rewards. Referral campaigns may appear in Offers, but referral actions remain in the Referral route; an issued referral reward uses the canonical `REWARD-DETAIL`. Detailed commercial, qualification, entitlement, lifecycle, fulfilment, and calculation logic remains owned by DOC-13.

Active Request and BILLS-LINKING routes, creation, delivery, reminders, acceptance, reciprocal visibility and Payee-user behavior are retired from MVP by the current DOC-06 Founder Working Baseline. Only append-only documentation history and retired stable IDs remain as non-active evidence. No runtime historical reader, adapter, fallback or replacement route is required because no production legacy Request/Payee-role runtime existed.

For Bills/Rent UX, the current Wave 2 DOC-06 baseline preserves the Category-before-acquisition sequence for Bills, the separate Rent journey, the same authoritative identity across Save/no-Save/post-payment Save, the absence of a Bills/Rent UI entry for history-only sources, ordinary Archive after Save, and the prohibition on a later Save-from-Activity route. Exact screens, route IDs, Copy and interaction mechanics remain with the applicable DOC-06, DOC-07 and other formal owners.

For account-control UX, `ME-ROOT` is a permanent MVP bottom-navigation route for Payers. It provides masked Account Information, account/security/privacy child-route entry and owner-governed feature handoffs. Existing Payee-user and Receiving Info product treatment is retired in the current DOC-06 Founder Working Baseline; destination and payout data remain specialist-owned and do not create a Consumer Payee role.

DOC-06B defines `ACCOUNT-PROFILE`, reusable `PHONE-VERIFICATION` and `IDENTITY-VERIFICATION`, `ACCOUNT-SECURITY`, reusable `PAYMENT-PASSCODE-SETTINGS`, and `PRIVACY-DATA-CONTROLS`. The MVP includes editable nickname/display name that is not a login identifier, copyable PayPlus User ID, cross-channel phone/email change verification, the five identity-verification labels `Not Verified`, `Processing`, `Verified`, `Failed`, and `Update Required`, account closure as a controlled request, login-method and Set/Change Password controls, payment-passcode Set/Change/Reset and permitted 2FA/biometric controls, trusted-device removal, optional privacy choices, governed correction/access/export/privacy requests, and protected in-app export. First-time identity verification during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode. Once verified, users cannot voluntarily re-verify; retries follow `Failed`, and an authorized Admin may execute an applicable identity/security-owner requirement to update without directly setting `Verified`.

Sensitive information remains masked by default. Prominent reveal of approved masked sensitive values, and material changes to existing identity, contact, security or credential data, require payment passcode or approved reauthentication under DOC-15 and the reviewed DOC-19 security controls. This material-change rule does not create a passcode prerequisite for first-time identity verification during Account Activation. Ordinary permitted evidence, invoice, receipt, statement, and payment-proof viewing/downloading does not require an extra prompt solely for opening or downloading the document. `ACTIVITY-ROOT` remains the Payer's account-level financial activity route. Bills/Rent source projections and Payment Activity/History/Receipt remain distinct. The current DOC-06 Founder Working Baseline retires Consumer Receiving Info and mixed-role Archive treatment; `ARCHIVED-ROOT` and Bills/Rent Archive presentation remain owned by the DOC-06 family.

Save records Payer persistence, visibility and reuse intent for one authoritative Bill/Rent source. A Saved/current source may remain in the current list while Under Review, Action Required or Ready; those are handling/readiness conditions, not projections. Archive moves a previously Saved/current source into the governed Archived projection, and Archived sources do not appear in the active/current list. Save and Archive must not erase or rewrite the source, Evidence, completed financial history, destination/payment snapshots, payout, reconciliation or audit lineage. No separate Unsave action or later Save-from-Activity route is introduced. Exact labels, Restore, replaced-Evidence/prior-version presentation, eligibility, revalidation, route and UI behavior remain downstream DOC-06 family and DOC-18 work.

### Payer

- enter through `ENTRANCE-ROOT` and use the `AUTH-LOGIN` family or `AUTH-REGISTRATION`;
- create a restricted account with a unique verified primary email, then complete `ACCOUNT-ACTIVATION` before full registration;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm core account, payment profile, or credential changes using password, payment passcode, 2FA, or approved confirmation method;
- dashboard through `HOME-ROOT`;
- logged-in `HOME-ROOT` baseline with `Home`, `Bills`, `Pay+`, `Offers`, and `Me` navigation where enabled by DOC-06B;
- Pay+ center action entry point opening `PAYPLUS-ACTION-SHEET` where enabled by DOC-06B;
- dashboard shortcut grid aligned by DOC-06B to the Payer-only target; the Requests entry is retired, and retained shortcuts remain entry points into owning routes or management areas rather than independent feature owners;
- `Cards` shortcut opens DOC-06B `PAYMENT-PROFILE-ROOT` for tokenized card management and saved split-card profile management; it is not checkout and does not authorize payment;
- user shortcut display order, visibility preference, and restore-default behavior;
- permanent `ME-ROOT` access with fixed account-control sections, masked Account Information, security/privacy entry, established-route handoffs, preferences, support, About/Terms, and a bottom Log Out button;
- Greeting, Important Notice, Home Hot Offer, Upcoming Bills / Rent, Recent Activity, section-level resilience, accessibility, and presentation-governance dashboard baselines where enabled by DOC-06B; source-owned notification, obligation, outcome, Offer, privacy, and Admin meanings remain with their applicable formal owners;
- bill/rent reminder management through DOC-06C `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`, including linked reminders, reminder defaults, custom overrides, non-destructive disable/deactivation behavior, and notification ownership boundaries;
- create payment;
- review evidence;
- review and correct autofilled evidence fields where applicable;
- authorize payment;
- enter payment passcode before proceeding with payment authorization;
- choose pay now or create a pending payment instruction where enabled;
- view and act on Payment Instruction actions through DOC-06B `INSTRUCTIONS-ROOT` / `INSTRUCTIONS-DETAIL`; when entry is notification-backed, first open `NOTIFICATION-DETAIL` and complete DOC-08 current-state, authenticated-payer, permission, target, and action-availability revalidation before an owner-approved current CTA may invoke the DOC-09 Checkout Resolver;
- review updated amount, promotion, fee, card eligibility, destination, or timing changes when returning to a pending Payment Instruction or incomplete Checkout Workspace;
- view confirmed funded value and the remaining Checkout Target or obligation Outstanding Amount where applicable, without treating them as the same value;
- review the automatically selected highest-user-value payment-method-sensitive Card Offer and separately select an eligible checkout coupon/voucher/discount; the applicable payment, promotion, fee, benefit, quote, and review facts must be presented within the Checkout Workspace and reviewed before the applicable authorization. Their presentation may be adaptively combined or separated and is not required to use one fixed screen or step;
- discover approved promotions through DOC-06B `OFFERS-ROOT` and review conditions through `OFFER-DETAIL`;
- manage issued coupons, vouchers, external-partner instruments, miles entitlements, or other supported rewards through `REWARDS-ROOT` and `REWARD-DETAIL`; external vouchers and miles are launch-supported reward types, while each actual provider method remains subject to operational and integration readiness;
- share a reusable referral link/code, view attributed-referee qualification progress, and claim the user's corresponding referrer or referee rewards through the Referral route family where enabled; referral sharing alone does not identify a recipient or create an invitation status;
- manage tokenized cards, set a default card for single-card checkout, and manage saved split-card payment profiles where enabled;
- view payment status;
- view receipts/history.

### Economic Payee

The Payee is the economic recipient and has no MVP Consumer login, dashboard, route, Request, linking, receipt-history or reciprocal-visibility entitlement. An institution may participate in the bounded Institutional Payee Programme without becoming a Consumer User. Payout destination, masking, verification, notification and support behavior remains with its specialist owner.

### Admin / Operations Handoff

The UX may expose only owner-permitted Admin execution surfaces. DOC-22 may execute only specifically owner-permitted operations and controlled overrides; it does not independently create route, queue, permission or configuration mechanics. Each applicable specialist owner supplies the governing policy, outcome and permitted actions. DOC-15 governs approved-purpose access and masking, DOC-18 owns business audit-meaning/lineage obligations, and DOC-21 owns support and operational escalation without retrieval authority. This section does not grant generic account, Evidence, Payment, payout, refund, dispute, risk, source, data or audit access and does not define an Admin disposition.

Institutional programme execution, scoped Company/Individual review, Home/feature configuration, Evidence/payment/payout/risk/refund/support handoffs and promotion operations may appear only where their formal owners have authorized the capability and context. Detailed Admin UI, exact actions, queues, permissions and implementation remain outside DOC-05.

---

## 16. MVP Business Requirements

The MVP should support:

- configurable service fee model;
- configurable promotion engine rules where enabled;
- fee display before payer authorization;
- promotion quote, discount, coupon, voucher, reward, and final total display before payer authorization where applicable;
- owner-approved dashboard shortcut defaults, dashboard placements and carousel display rules where enabled, with DOC-22 limited to permitted configuration execution;
- DOC-06C/DOC-08 and applicable owner-approved bill/rent reminder defaults, reminder eligibility and feature gating where enabled, with DOC-22 limited to permitted configuration execution;
- user-managed shortcut ordering and restore-default behavior where enabled;
- transaction-level revenue tracking;
- payment status reporting;
- governed product, risk, evidence, payment, promotion, support, and operations analytics where enabled;
- deliberate Payment Instruction reporting, including pending, cancellation and expiry conditions;
- incomplete Checkout Workspace, Funding Leg, confirmed Payment, Payment Application, Effective Coverage, Outstanding Amount, and downstream payout reporting without collapsing them into one status family;
- user-level activity history, with Bill/Rent-specific activity governed by DOC-06C, data/event/audit representation governed by DOC-18, and DOC-22 limited to permitted Admin execution and access;
- operational review workflows;
- support and dispute handling;
- partner/payment processor compatibility.

Final pricing, fee model, and partner economics should be governed by DOC-02 and later commercial decisions.

---

## 17. Non-Functional Requirements

| Area | Requirement |
|---|---|
| Security | Protect user, payment, and evidence data. |
| Privacy | Apply DOC-15 data classification, role-based display controls, masking, retention, and approved-purpose access. |
| Data governance | Material data should support classification, lineage, auditability, consent/preference state, approved purpose, partner-sharing status, and future model-use eligibility metadata where applicable. |
| Reliability | Payment, source-projection and owner-governed readiness facts must remain consistent without collapsing them into one status. |
| Auditability | Key user, admin, payment, and evidence actions must be logged. |
| Scalability | Architecture should support future automation and additional payment categories. |
| AI readiness | Architecture should support future approved AI/model improvement through governed data capture, model input controls, explainability, monitoring, and human-review boundaries. |
| Availability | MVP should be available enough for controlled beta operations. |
| Maintainability | Product should use clear object models and status transitions. |
| Compliance readiness | System should support review, evidence, audit, and reporting needs. |

---

## 18. Prohibited Product Behavior

PayPlus must not:

- operate as a wallet;
- provide user stored balances;
- allow cash withdrawal;
- allow payer self-cashout;
- allow unsupported arbitrary P2P transfers;
- allow arbitrary company payment or an open Payee marketplace;
- allow `Provide Payee myself` to bypass the selected supported controlled Bill Category;
- treat Directory enrolment, association, publication or selection as Evidence truth, destination authorization, eligibility, risk clearance, readiness or Payer authorization;
- collapse institutional enrolment, Category association, Directory publication, acquisition source or transaction controls into an `Approved Payee` state;
- process payments without payer authorization;
- process a Tier 2/3 Bill without required owner-approved official Bill Evidence, or process Rent without required accepted attached Evidence;
- treat a Company/Individual label, Payer response or scoped Admin determination as global Payee truth;
- turn individual notification into Request, Linking, acceptance, invitation, consent proof or authorization;
- treat Directory unpublication alone as saved-record invalidation or substantive suspension;
- make Save create or clone a source, copy Payment history, establish readiness or standing authorization;
- expose a history-only Bill/Rent through Bills/Rent UI or create a later Save-from-Activity route;
- erase financial, Evidence, Payout, reconciliation or audit history through Save, no-Save or Archive;
- preserve active Request/BILLS-LINKING as a disabled dormant runtime product;
- hide material payment information from payer before authorization;
- create untraceable payment records;
- bypass applicable owner-controlled review, sanctions, fraud, anti-cashout or other risk controls;
- represent funds as deposits or bank account balances.

---

## 19. MVP Acceptance Criteria

The Wave 1 product-policy baseline is acceptable when:

1. Consumer Users are Payers only, while a Payee is an individual or institution/company economic recipient that need not be a PayPlus User.
2. MVP is limited to the twelve accepted launch controlled Bill Categories in Section 3.1.1 and the separate Rent journey; Category-specific eligibility, Evidence criteria, Directory contents, detailed labels and Copy remain owner-backed later work.
3. Category-scoped Directory and `Provide Payee myself` are the only Bill Payee-acquisition methods and both remain governed by the already selected supported Category.
4. Rent remains a separate tenancy/relationship journey and does not use the controlled-Bill Directory.
5. DOC-05 owns bounded Institutional Payee Programme and Directory policy; DOC-12 owns Category, Evidence, OCR/extraction, Evidence verification and Evidence-to-Payee matching; DOC-09 owns Payment Obligation, Checkout, payer authorization and Payment invariants; DOC-10 owns destination readiness, Payout and reconciliation; DOC-14 owns applicable sanctions, fraud and anti-cashout controls; DOC-15 owns privacy and retention governance; and DOC-22 owns only the permitted Admin execution under those owners.
6. Institutional enrolment, Category association, Directory publication, acquisition source, Evidence/Payee match, destination readiness, risk disposition, Payment Obligation readiness and authorization remain separate.
7. Directory meaning is limited to Category-scoped discovery and bounded higher pre-trust; no composite `Approved Payee` truth exists.
8. Self-provided Company/Individual choice precedes Evidence; AI-apparent type, Payer response and scoped Admin determination remain non-overwriting provenance; Reviewed and Resolved remain separate, and the scoped determination does not create global Payee truth, enrolment, permanent eligibility or destination approval.
9. Label-only disagreement is separated from concrete Evidence, intended-Payee, destination, beneficiary/agent, Category, sanctions, fraud, anti-cashout, payout, readiness and authorization defects; label-only review may be asynchronous and need not create a user-facing payment-review status, and payment may proceed only when every applicable concrete owner-controlled gate passes.
10. Company/institutional Payees receive no MVP notification; only a governed Individual determination enables the optional Payer-initiated one-way individual notification, and Payer selection or AI-apparent type alone is insufficient. Lawful-purpose, data-minimization, wrong-recipient, abuse/rate-limit, suppression/opt-out, security, delivery-record, retention and support obligations remain with their formal owners.
11. Directory unpublication changes only new discovery, while substantive owner-controlled restrictions remain independently effective across both acquisition methods.
12. ID establishment consumes an owner-governed source-preservation eligibility outcome, using Evidence inputs only where applicable; one authoritative Bill/Rent source identity exists before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or a Payment-facing handoff requires stable identity, without defining technical thresholds or minimum fields here.
13. Deliberate Save gives the same ID Saved/current Payer persistence, visibility and reuse intent without Payment; immediate pay-now confirms a separate DOC-09 Payment identity, shows Payment Result, and for an otherwise unsaved source resolves optional Save on the same ID before Activity, Payment History, Receipt or ordinary safe exit. A source already Saved/current retains its projection without duplicate Save.
14. Declined, skipped, dismissed, closed or otherwise abandoned Save resolution after confirmed Payment produces same-ID history-only; it is neither Saved/current nor Saved/Archived, has no Bills/Rent UI entry, and its Payment remains visible through Activity/Payment History/Receipt. An immediate-pay source may remain established but unprojected only when the journey ends before confirmed Payment; deliberate setup may do so only before Save/current projection is completed.
15. One Bill/Rent may support multiple obligations, Checkouts and Payments, and no Payment is source-less or supported by Payment ID alone.
16. Directory acquisition provenance remains bounded historical lineage for audit/troubleshooting only; it is not used as live eligibility, pricing, promotion, profitability, margin allocation, general commercial reporting or commercial-ledger authority and is never a live dependency for source identity, visibility, usability or future eligibility.
17. Bill date and amount are not reusable; Rent/tenancy reuse ends on expiry, replacement or material change; each payment retains fresh owner-controlled checks and Payer authorization.
18. Active Request and BILLS-LINKING behavior is retired without a dormant runtime. Append-only documentation history and retired stable IDs remain non-active evidence; no production historical Request/Payee-role data, runtime reader, adapter or fallback exists or is required.
19. No exact route, UI, Copy, schema, API, event, permission, SLA, legal conclusion, commercial term, prototype or implementation mechanism is defined by Wave 1; indefinite retention remains the Founder-approved product and governance direction, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. That qualification does not authorize erasure or rewriting of immutable Payment, Payment Application, Payout, Refund, case, reconciliation, audit, Save or Archive lineage.
20. Wallet, open marketplace, arbitrary recipient payment, P2P, remittance and cashout behavior remain prohibited.
21. DOC-05 grants no generic Admin access, queue, action, disposition or override authority. Every Admin handoff consumes applicable specialist-owner policy and outcomes; DOC-22 owns only permitted execution, with approved-purpose access, masking, audit and support retained by DOC-15, DOC-18 and DOC-21 as applicable.
22. Bill C1/G1/G2, highest-tier precedence and Tier 1/2/3 gates conform to Section 7 without redefining DOC-09 Payment records or tying G1 to a technical event.
23. G1 uses the same receiving account/authoritative payout destination as its deliberate policy key and does not redefine economic-Payee identity.
24. G2 uses the verified Payer's Hong Kong calendar-month confirmed obligation-funded Bill value, excludes payer fees, preserves original-month usage after Refund/reversal and permits only confirmed duplicate/error correction to restore capacity.
25. Tier 2 requires owner-approved official Bill Evidence presence before Payment and acceptance before Payout; Tier 3 requires Evidence and authorized approval before executable Payment progression.
26. Potential official Bill Evidence examples are not automatically accepted, and communication-originated material cannot satisfy, substitute for or contribute to Tier 2/3 mandatory Evidence.
27. Add a Bill applies C1 only; Pay a Bill re-evaluates current C1/G1/G2; prepayment uses the selected-period aggregate and one G1 progression.
28. Unchanged declared facts require no new Declaration; limit re-evaluation alone is not a trigger; user changes use owner-defined materiality and proportionate reconfirmation.
29. Saved/current and Saved/Archived are distinct projections; Under Review, Action Required and Ready are handling/readiness conditions; Archived sources are excluded from the current list.
30. Rent remains outside C1/G1/G2 and the Bill tiers, always requires attached Evidence accepted before Payment, and cannot use a Declaration to replace or defer that requirement.

---

## 20. Open Questions

| ID | Question | Owner | Status |
|---|---|---|---|
| OQ-05-001 | What specific payment processor or PSP will be used? | Product / Payments | Open |
| OQ-05-002 | What final KYC/KYB provider, check depth, sanctions screening, exception process, and risk-tier rules apply to the baseline onboarding model? | Compliance / Legal | Open |
| OQ-05-003 | Which Category-by-Category official current/historical Bill Evidence types and operating criteria instantiate the approved DOC-12 acceptance framework, and which separate attached-Evidence criteria govern Rent? Communication-originated material remains excluded. | DOC-12 / Product / Compliance / Risk | Open later owner/configuration input; blocks affected-path enablement/acceptance until supplied |
| OQ-05-004 | Which rent and tenancy controls are required before initial launch enablement? | Product / Risk | Open |
| OQ-05-005 | What owner-approved C1 Category values, permitted adjustments, configuration representation and operating change details apply under the settled designated product/risk authority? G1/G2 values and product meanings are settled; DOC-12 binds C1, DOC-09 consumes it and DOC-22 only executes approved configuration. | Product / Risk / Compliance | Open later configuration/enablement input; blocks affected configuration, acceptance and enablement until supplied |
| OQ-05-006 | Which authorized operating role, approval workflow and segregation controls implement mandatory Tier 3 approval, and what bounded DOC-22 execution is permitted? | Product / Risk / Compliance / Security / Payments / Operations | Open later operating/security input; the normative approval gate remains unchanged, and Tier 3 enablement/implementation is blocked until supplied |
| OQ-05-007 | What exact percentage service fee, payer/payee fee allocation, subsidy, coupon, promotion, discount, refund, and reversal treatment will be used? | Business / Product | Open |
| OQ-05-008 | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Operations | Open |
| OQ-05-009 | Which lawful-scope assessment, required exceptions, restricted data classes, prohibited sensitive-data boundaries, approved-purpose access, masking, legal-hold and correction/request controls apply while indefinite retention remains the Founder-approved product and governance direction? | Legal / Privacy / Compliance | Open |
| OQ-05-010 | What dispute process applies after payment completion? | Operations / Legal | Open |
| OQ-05-011 | What appropriate or special MCC and transaction classification will the selected acquirer confirm for PayPlus? | Payments / Legal | Open |
| OQ-05-012 | What maximum number of credit cards per payment/profile should be allowed at launch? | Product / Payments | Answered: 6 |
| OQ-05-013 | Which OCR/document AI provider, confidence thresholds and Category-specific OCR capabilities should apply to the accepted launch inventory and separate Rent journey? | DOC-12 / Engineering / Risk | Open; the twelve-category inventory itself is settled |
| OQ-05-014 | Which extracted fields are displayable, masked, or restricted by role and evidence category? | Product / Privacy / Security | Open |
| OQ-05-015 | What final styling and optional post-replacement Undo behavior should apply to `MORE-ROOT`? The 8-slot maximum, protected More entry, user reorder/remove/add behavior, account-level preference, current-default restore, availability precedence, and secondary-service boundary are defined. | Product / Design / Operations | Partially open |
| OQ-05-016 | Retired under the Payer-only target: the former five-action visual/composition question no longer governs. Residual exact visual, responsive and accessibility treatment for the confirmed four-action baseline is tracked by DOC-06B without reopening composition, order, material meaning or destinations. | Product / Design / Payments | Retired/superseded; any replacement-composition question requires handling under the canonical PayPlus Documentation Development Workflow and a DOC-06-owned ID |
| OQ-05-017 | What remaining implementation detail and evidence are required for the decided Admin controls supporting Home Hot Offer publication and other approved Home configuration? DOC-06B owns Home presentation; source owners retain canonical business truth; DOC-22 owns Admin publication and configuration controls; technical mechanics and later detailed evidence remain with their formal owners. | Product / Growth / Operations | Partially open; presentation-governance and ownership boundaries decided |
| OQ-05-018 | Which MVP events and data objects must be captured for product analytics, risk analytics, commercial reporting, and future approved AI/model improvement? | Product / Data / Engineering | Open |
| OQ-05-019 | What user consent and preference categories are required for personalization, partner offers, marketing communication, and model improvement? | Product / Privacy / Legal | Open |
| OQ-05-020 | Which data classes, fields, and derived features are prohibited from marketing models, partner reports, or external activation? | Product / Privacy / Risk | Open |
| OQ-05-021 | What final Payment Profile card metadata display and tokenization return UX should apply at launch? Route label is `Payment Profile`; payment/profile card-count cap is 6. | Product / Payments / Security | Partially open |
| OQ-05-022 | What owner-approved operating tests and presentation implement the accepted Declaration materiality and proportionate reconfirmation framework when a user changes Category, purpose, amount or Payee/receiving details? Limit re-evaluation alone is not a trigger. | Product / Legal / Compliance / Privacy / Payments | Open later product/content/acceptance input; any future answer must preserve or be reconciled through the approved framework |

Legal, Compliance, PSP/acquirer, card-network, Finance, Privacy, Security and Operations confirmations remain explicit affected-path dependencies. They must be resolved before the affected path's enablement, implementation, acceptance, production readiness or launch. A professional conflict that changes product meaning or makes the model impossible must be handled under the canonical PayPlus Documentation Development Workflow.

The accepted launch Category inventory is not an Open Question. Category-specific eligibility, Evidence criteria, Directory contents, detailed labels and Copy remain assigned to DOC-05, DOC-12, DOC-06C and DOC-07 respectively.

---

## 21. Dependencies

| Dependency | Purpose |
|---|---|
| DOC-00 | Documentation governance and source-of-truth rules |
| DOC-01 | Product overview and positioning |
| DOC-02 | Business model and monetization |
| DOC-03 | Regulatory assessment |
| DOC-04 | Compliance control framework |
| DOC-06 | Parent user journey, UX flow, and service blueprint family map |
| DOC-06A | Core user journeys and service blueprint |
| DOC-06B | Navigation, IA, route taxonomy, dashboard, Pay+, global non-Bills route-level UX, and route completion status |
| DOC-06C | Bills, Rent, tenancy, controlled acquisition, source visibility, Save, Archive, reminder and Evidence-entry UX |
| DOC-06D | UX requirements, acceptance criteria, and test-readiness mapping |
| DOC-07 | User-facing disclosure, authorization, evidence, privacy, and policy wording |
| DOC-08 | Notifications, receipts, communication triggers, and delivery logging |
| DOC-09 | Payment Domain architecture, including payable basis, projection, obligations, checkout, funding execution, payer authorization boundaries, confirmed Payments, Payment Applications, and deliberate Payment Instructions |
| DOC-10 | Payout, payout readiness, payout destination, batching, and reconciliation |
| DOC-11 | Refund, cancellation, reversal, dispute, and chargeback handling |
| DOC-12 | Bill category, document AI/OCR, evidence verification, duplicate detection, and Evidence-to-Payee matching |
| DOC-14 | AML, anti-cashout, fake evidence, duplicate evidence, collusion, and risk controls |
| DOC-15 | Privacy, data protection, masking, retention, lawful data use, consent, personalization, model-improvement, and partner-sharing boundaries |
| DOC-17 | Third-party APIs including OCR/document AI, PSP, bank, provider, analytics, campaign, and partner-reporting integrations where approved |
| DOC-18 | Reviewed business recording, explainability, material-fact history, historical action basis, lineage, audit meaning, reporting obligations, and owner handoffs; exact data model, fields, machine states, events, ledger representation, persistence, marts, and implementation remain future separately authorized work |
| DOC-19 | Mechanism-neutral authentication, protected-value, access-enforcement, secure-boundary, telemetry and verification-handoff controls; payer authorization remains with DOC-09, privacy/pseudonymization with DOC-15, provider mechanics with DOC-17, DOC-18 supplies business-recording inputs, and exact technical representation remains separately gated |
| DOC-20 | Mandatory Wave 5 detailed testing, UAT and release-readiness evidence; this document defines human Acceptance Criteria only |
| DOC-21 | Monitoring, incidents, support escalation, and operations runbooks |
| DOC-22 | Permitted Admin dashboard execution, queues, permissions, controlled overrides and configuration under the applicable product and specialist owners |

### 21.1 Owner-backed Deferrals and Mandatory Later-Wave Handoffs

| Deferred matter | Primary owner | Affected handoffs | Owner dependency | Effect when missing |
|---|---|---|---|---|
| C1 Category values, permitted adjustments and operating configuration | Designated product/risk owner, with DOC-12/DOC-09/DOC-22 handoffs | DOC-05/12/14/09/06C | Owner-defined configuration and enablement | Blocks affected configuration, acceptance and enablement until supplied |
| Official Bill Evidence Category lists and operating criteria | DOC-12, within DOC-05 product boundary | DOC-06C UX; DOC-07 Copy; DOC-09/10 gates | Owner-defined configuration and enablement | Exact lists block affected-path enablement and acceptance until supplied |
| Tier 3 operating role, workflow and segregation controls | Designated Product/Risk/Compliance/Security owners | DOC-14/09/10/22 | Owner-defined operating/security detail | The normative approval gate remains unchanged; blocks Tier 3 enablement and implementation until supplied |
| Category-specific eligibility, other Evidence criteria and Directory contents | DOC-12, within DOC-05 Programme boundary | DOC-06C UX after owner rules; DOC-07 Copy | Category owner definition | Explicit material owner gaps block the affected handoff |
| Exact visual, Copy, motion, accessibility and responsive treatment | DOC-06B/DOC-06C presentation | DOC-07 approved Copy; DOC-20 acceptance evidence | Presentation and acceptance owner detail | Blocks the affected presentation and acceptance work until supplied |
| ID persistence threshold, schema, events and technical lifecycle | DOC-12 source/Evidence outcome; DOC-09 payment lifecycle; DOC-15 retention governance; future separately authorized Engineering/Data representation using DOC-18's reviewed business inputs | DOC-06 consumes outcomes only | Technical-owner detail under a separate authority | Blocks affected technical representation and implementation until supplied |
| Notification channel, provider, legal/contact, suppression, delivery and support mechanics | DOC-08 delivery, with DOC-05 eligibility boundary | DOC-07/14/15/18/19/21/22 | Notification and professional owner detail | Blocks affected notification delivery and support operation until supplied |
| Exact Archive eligibility, Restore, prior-version, Evidence-version and replacement-source presentation | DOC-06B/DOC-06C presentation under DOC-05 same-source policy | DOC-10/11/12/15/18 owner blockers and representation | Presentation and owner-rule detail | Blocks the affected presentation or owner-controlled operation until supplied |
| Route Register, status-display matrix, requirements traceability, open-question register and governed diagrams | Each artifact owner | All affected formal owners | Artifact-owner maintenance | Requires later authorized artifact-owner work |
| Detailed testing, UAT, operations and support evidence | DOC-20 and DOC-21 | Owning human and specialist requirements | Testing and operational owner detail | Blocks affected acceptance, operational readiness and support evidence until supplied |

---

## 22. Decision Summary

| Decision | Status |
|---|---|
| PayPlus MVP is a controlled Bill and Evidence-backed Rent Payment App; Consumer Users are Payers only. Bills use the approved tier policy, while Rent retains mandatory accepted attached Evidence before Payment. | Founder-approved |
| A Payee is an individual or institution/company economic recipient and need not be a PayPlus User. | Founder-approved |
| MVP supports the twelve accepted launch controlled Bill Categories in Section 3.1.1 plus the separate Rent journey; Category-specific detailed policy remains owner-backed later work. | Founder-approved inventory and boundary |
| Category-scoped Directory and `Provide Payee myself` are the two Bill acquisition methods; both remain governed by the already selected Category. | Founder-approved |
| Rent remains a separate tenancy/relationship journey and does not use the controlled-Bill Directory. | Founder-approved |
| DOC-05 is the bounded primary human product-policy owner for the Institutional Payee Programme, Directory and related Payer-only meanings, with specialist handoffs and the stated future-owner threshold. | Founder-approved |
| Programme enrolment, Category association, Directory publication, acquisition source and transaction-control dimensions remain separate; no composite `Approved Payee` state exists. | Founder-approved |
| Company/Individual selection, AI-apparent assessment, Payer response and scoped Admin determination preserve non-overwriting provenance; `Reviewed` and `Resolved` remain separate; label-only review may be asynchronous, non-user-facing and nonblocking when every concrete owner-controlled gate passes. | Founder-approved |
| DOC-05 defines bounded product-policy handoffs but no generic Admin access, queue, action, disposition or override; specialist owners retain policy/outcome authority and DOC-22 owns permitted execution only. | Founder-approved ownership boundary |
| Company/institutional Payees receive no MVP notification; a governed individual may receive an optional Payer-initiated one-way notification without Request/Linking semantics. | Founder-approved |
| Directory unpublication changes discovery only and remains separate from substantive owner-controlled restrictions. | Founder-approved |
| One authoritative Bill/Rent source preserves Save intent and distinct Saved/current, Saved/Archived, history-only and established-but-unprojected treatment. Under Review, Action Required and Ready are conditions within current presentation; Archived sources are excluded from the current list. | Founder-approved |
| No later Save-from-Activity route or separate Unsave action is accepted; ordinary Archive applies after Save. | Founder-approved |
| Directory acquisition provenance is bounded historical lineage and is not a live identity or eligibility dependency. | Founder-approved |
| Bill date and amount are not reusable; Rent/tenancy context reuse ends on expiry, replacement or material change; later payments retain fresh checks and authorization. | Founder-approved |
| Active Request and BILLS-LINKING behavior is retired; only append-only documentation history and retired stable IDs remain non-active evidence because no production legacy runtime or deep-link data exists. | Founder-approved clarification |
| Every Payment remains tied to an eligible controlled Bill or Rent context. Bill Tier 1 may omit attached Evidence only under the approved tier policy; Tier 2/3 Bills and all Rent retain their required Evidence gates. | Founder-approved |
| Bill C1/G1/G2, highest-tier precedence, Tier gates, Declaration, Add/Pay, prepayment and immutable financial boundaries follow Section 7. | Founder-approved |
| G1 is a product-semantic receiving-account/authoritative-payout-destination progression limit and is not economic-Payee identity or a selected technical event. | Founder-approved |
| The Founder-updated Tier 2/3 Evidence direction permits owner-approved formal bills, fee notices, school payment notices, statements, invoices and formal historical receipts within the DOC-12 framework; examples do not create acceptance, communication material is excluded, and Rent remains separate. | Founder-approved correction input / DOC-12 owner framework |
| C1 Category values/operating details, official Bill Evidence Category lists, Tier 3 operating controls and Declaration implementation detail remain visible later owner dependencies and cannot be delegated to DOC-22. | Founder-approved completeness classification / Open later inputs |
| OCR/document AI-assisted evidence capture, autofill, user correction, duplicate detection, and verification routing are required capabilities where enabled. | Confirmed |
| Payer must authorize payment before funds movement. | Confirmed |
| Every Payment is source-linked and freshly Payer-authorized under DOC-09; payout and destination remain under DOC-10. | Confirmed / specialist-owned |
| Wallet, cashout, and unsupported P2P are prohibited. | Confirmed |
| Major functions and modules must be independently disableable. | Confirmed |
| Future docs should use concise product-spec structure. | Confirmed |
| Promotion engine capabilities are framework scope but launch-gated by DOC-13 rules and admin configuration. | Confirmed |
| AUTH routes use capability-aware Outcome-to-Resolution handling without changing approved login, registration, activation, verification, passcode, or return decisions. | Confirmed |
| `ENTRANCE-ROOT`, the `AUTH-LOGIN` family, `AUTH-RECOVERY`, `AUTH-REGISTRATION`, and `ACCOUNT-ACTIVATION` are required product destinations. Normal successful authentication enters `HOME-ROOT`; approved contextual deeplinks may resume their intended destination. | Working Baseline / Behavior Defined |
| One account uses one unique verified primary email and may explicitly enable email/password, Google, and Apple login methods. Social accounts may set a password later; matching emails never auto-link accounts; a registration attempt reserves no identifier; phone, identity, and six-digit payment-passcode completion remove the registration-level restriction through `ACCOUNT-ACTIVATION`. | Confirmed |
| The current DOC-06 baseline implements the Founder-approved `PAYPLUS-ACTION-SHEET` composition: the retained four actions remain in their accepted order and material meaning, Request Payment is retired, and related owner work remains with the applicable formal owners. | Founder-approved composition |
| DOC-06B defines the reviewed `HOME-ROOT` route-level baseline for Greeting, Important Notice, Home Hot Offer, Upcoming Bills / Rent, Recent Activity, section-level resilience, accessibility, and presentation governance. `HOME-ROOT` remains Partially defined while final visual design, exact DOC-07 Copy and identifiers, technical mechanics, and later DOC-20 evidence remain pending with their formal owners. | Working Baseline / Route Behavior Defined |
| Dashboard shortcut grid, account-level user shortcut preferences, protected `More`, current-default restore, Pay+ entry point, and admin-controlled dashboard placements must be supported where enabled. | Confirmed |
| Request, mixed-role Bills, Payee-user and related route behavior is retired from the current Payer-only product baseline. Retired stable IDs and prior meanings remain append-only non-active documentation evidence only; they create no active route, runtime, reader, adapter, or fallback. Related owner work remains with the applicable formal owners. | Founder-approved target |
| DOC-06B `PAYMENT-PROFILE-ROOT` is accepted as the current route shell for tokenized card and saved split-card profile management; checkout authorization and funding remain governed by DOC-09. | Working Baseline / Not Final |
| Existing unaffected authentication, payment profile, Instructions, promotion, reward, referral, data-governance and Home baselines remain in force subject to their formal owners; Payee-user Receiving Info and mixed-role Archive treatment are re-scoped by the current DOC-06 baseline, with related owner work retained by the applicable formal owners. | Retained |
| The canonical product destination inventory is maintained in `docs/traceability/route-register.md`; route owners and the DOC-06 parent must remain synchronized with it. | Confirmed |
| PayPlus MVP should be data-engine ready by design, with structured events, field classification, source lineage, auditability, consent/preference state, approved-purpose metadata, and future model-use eligibility metadata where relevant. | Confirmed |
| Advanced AI decisioning, external partner activation, offsite advertising, user-level data sharing, credit scoring, and insurance underwriting are not MVP scope unless separately assessed, approved, and documented. | Confirmed |

---

## 23. Revision History

| Version | Date | Summary |
|---|---|---|
| v1.1.1 | 2026-08-27 | Aligned complete Bill/Rent material-fact, same-Bill Category-amendment, prior-history, four-context Declaration, and current-versus-future DOC-18 ownership handoffs without adding schema, UI, implementation, or enablement detail. |
| v1.1.0 | 2026-08-22 | Drafted the approved Bills Tiered Payer Presentation and Return Contract: deliberate Tier 3 Pay/resolver re-entry, proportionate Declaration, and distinct Save-admission versus current Payment progression, without selecting configuration, routes, notifications, security mechanisms, or enablement. |
| v1.0.1 | 2026-08-21 | Aligned product handoffs with the reviewed DOC-19 security-control contract while preserving payer authorization, privacy, provider, representation and open-mechanism ownership. |
| v1.0.0 | 2026-08-18 | Implemented the material Bills-only tier model and fixed-seat compliance supplement; preserved C1 layering and Founder-updated Evidence traceability, retained owner-level dependencies, neutralized the complete active lifecycle-language family, and qualified indefinite retention by lawful scope, required exceptions and restricted data classes. |
| v0.19.5 | 2026-08-13 | Replaced the named identity-verification provider example with provider-neutral, owner-qualified wording without selecting a provider or changing verification requirements. |
| v0.19.3 | 2026-08-12 | Removed the unsupported archived Payment Instruction reporting condition; retained the accepted deliberate Instruction pending, cancellation and expiry boundary and the separate incomplete Checkout Close/Expiry and source-Archive meanings. |
| v0.19.4 | 2026-08-12 | Applied the Founder-settled indefinite-retention rule to the product baseline and Acceptance Criteria/Open Question wording without changing Payment, Save, Archive or implementation ownership. |
| v0.19.2 | 2026-08-12 | Corrected Payment/Application lineage for DOC-09's controlled late-confirmation exception and made the Payer-only active baseline independent of retired documentation lineage. |
| v0.19.1 | 2026-08-12 | Added the Founder-confirmed twelve-category launch inventory; removed nonexistent Request-runtime/deep-link obligations; made later owner and Wave handoffs explicit; and preserved the settled Pay+, source identity, Admin, notification and Archive boundaries for Wave 2 Draft. |
| v0.19.0 | 2026-08-11 | Stage 8 accepted-scope correction following Primary Review: preserved the source/projection, post-Payment Save and four-action Pay+ decisions; confirmed that alternative Evidence remains Evidence; and replaced generic cross-domain Admin authority with bounded specialist-owner handoffs and DOC-22 execution. |
| v0.18.36 | 2026-08-06 | Aligned the Master PRD with the reviewed `HOME-ROOT` route-level baseline, replaced the superseded combined Home placement terminology with Home Hot Offer, and narrowed OQ-05-017 to residual Admin implementation and evidence dependencies without duplicating DOC-06B or source-owner contracts. |
| v0.18.35 | 2026-08-04 | Aligned notification-backed Payment Instruction actions with mandatory `NOTIFICATION-DETAIL` entry, current DOC-08 revalidation, and an owner-approved CTA to the DOC-09 Checkout Resolver without creating a direct notification-to-Instructions or Checkout path. |
| v0.18.34 | 2026-08-03 | Aligned the PAYMENT-CHECKOUT owner split to DOC-06B route-level UI/UX and DOC-09 authoritative Payment Domain meaning, and replaced fixed-screen review wording with the accepted adaptive Workspace composition. |
| v0.18.33 | 2026-07-31 | Aligned product requirements with DOC-09 Payment Domain Architecture, separated deliberate Payment Instructions from incomplete Checkout Workspaces, and clarified Request, Payment Obligation, Checkout, Payment, Payment Application, coverage, and downstream Payout boundaries. |
| v0.18.32 | 2026-07-29 | Added the platform-wide Outcome-to-Resolution product requirement and aligned the AUTH baseline with capability-aware recovery without changing existing account, login, activation, or security decisions. |
| v0.18.31 | 2026-07-28 | Aligned the PRD with the defined Phone Verification, five-state Identity Verification, no voluntary re-verification after Verified, and six-digit Payment Passcode Set/Change/Reset behavior. |
| v0.18.30 | 2026-07-28 | Aligned the PRD with separate Phone and Identity Verification routes, the first-time identity-verification passcode exception, and the pending detailed Payment Passcode Settings definition. |
| v0.18.29 | 2026-07-28 | Aligned the PRD with `ENTRANCE-ROOT`, Fast/Full Login, Recovery, non-reserving registration attempts, Account Activation, six-digit passcode requirement, uniqueness conflicts, display-name boundary, and authentication outcome/message ownership. |
| v0.18.28 | 2026-07-27 | Added the accepted unique-primary-email, explicit multiple-login-method, social-account password-setup, restricted-account, and deferred-financial-activation product baseline. |
| v0.18.27 | 2026-07-27 | Aligned the PRD with the defined `NOTIFICATION-ROOT` family, Home/Me entries, Inbox/Detail/Settings separation, domain-status and Action Required boundaries, and current-state contextual routing. |
| v0.18.26 | 2026-07-27 | Aligned the PRD with defined `MORE-ROOT` Normal/Manage behavior, 8-slot maximum, protected More entry, account-level shortcut preferences, current-default restore, availability precedence, and secondary-service boundary. |
| v0.18.25 | 2026-07-27 | Distinguished direct payer-created obligations/payments from optional payer-created linking requests, defined Pay+ Request Payment as payee-to-payer, and aligned the confirmed five-action Pay+ behavior while leaving exact visual design open. |
| v0.18.24 | 2026-07-26 | Defined the archived-obligation product baseline, mixed-role filters, read-only detail reuse, eligibility/blocker and restore rules, personal archive projection, and obligation/evidence separation. |
| v0.18.23 | 2026-07-26 | Added the `ARCHIVED-ROOT` family and confirmed evidence replacement, parent archive, restoration, expiry, non-restorable history, and Archived Documents behavior. |
| v0.18.22 | 2026-07-26 | Added stable authentication, Home, Pay+, More, Notification Inbox, and Payment Checkout destination IDs and the pre-login Login/Register handoff baseline. |
| v0.18.21 | 2026-07-26 | Adopted the canonical request lifecycle, role-facing labels, event/evidence/readiness/case/archive separation, and removed mixed request-status definitions. |
| v0.18.20 | 2026-07-26 | Clarified evidence-to-obligation linkage and optional request involvement, aligned prominent sensitive reveal and material-change authentication, retained ordinary permitted document viewing/download without extra prompt, and referenced the canonical route register. |
| v0.18.19 | 2026-07-23 | Replaced singular Receiving Details with multiple private reusable Receiving Info profiles and aligned request selection, destination snapshots, masking/edit behavior, archive/versioning, and authorization-freeze requirements. |
| v0.18.18 | 2026-07-22 | Aligned the PRD with defined Account Information, Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, contact-change, verification-status, account-closure, trusted-device, privacy-request, and protected-export behavior. |
| v0.18.17 | 2026-07-22 | Aligned the PRD with permanent `ME-ROOT`, masked account display and passcode-gated reveal, account/security/privacy handoffs, Receiving Details, archived-evidence access, established feature-route entry, preferences, support, About/Terms, logout, and the separate More boundary. |
| v0.18.16 | 2026-07-21 | Aligned the PRD with defined My Rewards Active/History management, complete reward detail/T&C, checkout-owned reward selection, launch-supported external vouchers and miles, and separate reward instrument/source/role/program/campaign/entitlement/fulfilment data dimensions. |
| v0.18.15 | 2026-07-21 | Aligned the PRD with role-sensitive Referral Rewards child screens, two list tabs, detail-first claiming, canonical issued-reward usage, and the restricted masked-phone display boundary. |
| v0.18.14 | 2026-07-21 | Aligned the PRD with the defined Referral route family, reusable sharing, registration attribution, qualification progress, referrer entitlement claiming, and canonical issued-reward handoff. |
| v0.18.13 | 2026-07-20 | Aligned the PRD with multi-collection Offers, root duplicate suppression, stable child-list ordering, automatic highest-user-value Card Offer selection per payment card/funding leg, separate coupon/voucher/discount selection, and same-screen checkout review. |
| v0.1 | Initial Draft | Initial master PRD structure. |
| v0.2 | 2026-05-27 | Updated MVP to include both payer-created and payee-created payment requests; added two-sided user visibility, evidence-backed linking, linked payer/payee records, and simplified structure. |
| v0.3 | 2026-05-29 | Confirmed payee-created requests and tenancy/rent as MVP scope, added MVP gating and configuration rules, clarified that detailed data and UX design belong in downstream docs, and updated open questions. |
| v0.4 | 2026-05-30 | Aligned product requirements with updated DOC-01 scope for invoices, fees, rent, domestic service obligations, request delivery methods, and evidence-backed positioning. |
| v0.5 | 2026-05-30 | Aligned master PRD with DOC-12 by adding OCR/autofill, user correction, evidence verification outcomes, duplicate/reused evidence routing, sensitive field display controls, and explicit downstream document references. |
| v0.6 | 2026-06-01 | Aligned master PRD with DOC-13 by adding promotion quote, entitlement, coupon/voucher library, reward instrument, campaign data, and admin promotion-control references. |
| v0.7 | 2026-06-02 | Aligned master PRD with DOC-15 by adding privacy data classes, field-level classification metadata, authentication UX requirements, material-change confirmation, payment passcode, and admin sensitive-data access controls. |
| v0.8 | 2026-06-02 | Added DOC-09 user payment instruction as MVP scope for deferred single-card and split-card payment, payment-instruction reminders, partial funding, and partial payout visibility. |
| v0.9 | 2026-06-02 | Aligned PRD with DOC-09 and DOC-13 deferred payment instruction quote revalidation, promotion reservation, and return-to-checkout update review. |
| v0.10 | 2026-06-02 | Standardized coupon/voucher library wording to avoid stored-value confusion. |
| v0.11 | 2026-06-04 | Aligned PRD with DOC-06 Home Dashboard baseline by adding Pay+ navigation, shortcut grid, user shortcut preferences, dashboard placements, Featured carousel, and related admin configuration expectations. |
| v0.12 | 2026-06-08 | Added data-engine and AI-readiness requirements for structured events, field metadata, consent/preference state, approved-purpose data use, future model eligibility, analytics readiness, and prohibited MVP AI/partner activation boundaries. |
| v0.13 | 2026-06-12 | Aligned PRD with DOC-06 Bills tab baseline by clarifying payer-created payment without default payee acceptance, user-accepted participant linking, payee/payout validation, and no automatic user-to-user matching. |
| v0.14 | 2026-06-15 | Clarified that DOC-06 owns user-facing route IDs, route types, and button-to-route ownership for Bills tab and related UI surfaces. |
| v0.15 | 2026-06-17 | Aligned PRD with DOC-06 Bills reminder route split, linked reminder records, reminder defaults, custom override, and admin reminder configuration boundaries. |
| v0.16 | 2026-06-17 | Added PRD alignment note that DOC-06 owns route ID naming standards and specific sub-route IDs where available. |
| v0.17 | 2026-06-25 | Aligned PRD with DOC-06 role-aware `BILLS-PAY` / `BILLS-RECEIVE` route split, payee-side request/remind-payer behavior, checkout ownership boundary with DOC-09, and activity-history ownership boundaries. |
| v0.18 | 2026-06-25 | Aligned PRD references with the DOC-06 family split by pointing navigation/dashboard content to DOC-06B, Bills/rent/tenancy UX to DOC-06C, core journeys to DOC-06A, and UX acceptance/test mapping to DOC-06D. |
| v0.18.1 | 2026-06-25 | Confirmed DOC-06 family publication cleanup and parent scope, role, and UX-surface summaries without changing master product requirements. |
| v0.18.2 | 2026-06-25 | Added single-primary-owner drafting rule for DOC-06 family topics and clarified route shell versus lifecycle versus Bills/rent implementation ownership. |
| v0.18.3 | 2026-06-25 | Clarified request-not-payment boundary and request acceptance as party-linking to an accepted obligation context. |
| v0.18.4 | 2026-06-25 | Reflected DOC-06B Requests route shell baseline and preserved lifecycle, Bills/rent implementation, notification, and data ownership boundaries. |
| v0.18.5 | 2026-06-29 | Added PRD alignment that `REQUESTS-DETAIL` is the request-management screen and links to, but is not replaced by, DOC-06C bill/rent detail. |
| v0.18.6 | 2026-07-02 | Clarified dashboard shortcuts as entry points into owning routes or management areas, aligned with DOC-06B route-entry map. |
| v0.18.7 | 2026-07-02 | Aligned PRD with DOC-06B `REQUESTS-NEW`, evidence-before-send request delivery gate, and request-not-payment route boundary. |
| v0.18.8 | 2026-07-02 | Removed stale request-route clarification/dispute actions and aligned exception/support wording with DOC-06B `REQUESTS-NEW` and `REQUESTS-DETAIL`. |
| v0.18.9 | 2026-07-03 | Aligned PRD wording with DOC-06B Instructions route and DOC-09 payment instruction boundary: pending/incomplete instructions remain separate from ordinary reminders and completed pay-now payments. |
| v0.18.10 | 2026-07-06 | Aligned PRD with DOC-06B Payment Profile route shell for tokenized cards and saved split-card profiles, including final `Payment Profile` label, max 6-card cap, checkout/instruction handoff, default confirmation behavior, and non-wallet boundary. |
| v0.18.11 | 2026-07-14 | Clarified DOC-06B ownership of human-readable route-level UX for global non-Bills routes while preserving domain-logic ownership boundaries. |
| v0.18.12 | 2026-07-17 | Aligned the PRD with stable product destination naming, separate Offers child-list screens, issued-reward management, and partial referral routes while preserving DOC-13 business-logic and DOC-09 checkout ownership. |
