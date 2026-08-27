---
document_id: DOC-06
title: User Journey, UX Flow & Service Blueprint
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
  - DOC-00 Documentation Governance
  - DOC-05 Master PRD & Feature Requirement Index
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
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT & Release Readiness
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06 - PayPlus User Journey, UX Flow, and Service Blueprint Family

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06` |
| **Title** | User Journey, UX Flow & Service Blueprint |
| **Version** | `1.1.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-22` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT & Release Readiness<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## Current Payer-only Founder Working Baseline

This is the current normative Payer-only Founder Working Baseline for the DOC-06 family. Active requirements in this parent are Payer-only. Retired Request, Linking, Receive and Payee-user identifiers appear only in explicit retirement provisions or append-only documentation history; they create no runtime reader. Append-only decision and revision history remains unchanged.

### Family-level product and journey boundary

- A Consumer User acts as a Payer only. A Payee is an economic recipient who may be an individual or institution/company and need not be a PayPlus User.
- MVP supports the twelve Founder-confirmed launch controlled Bill Categories owned by DOC-05 plus the separate Rent journey. Rent is not a Bill Category and never uses the controlled-Bill Directory. Category-specific eligibility, Evidence criteria, detailed labels and Directory contents remain with their named owners.
- A controlled Bill journey selects its supported Category before showing either the Category-scoped Directory or Provide Payee myself. Neither method is unrestricted recipient discovery; Provide Payee myself never bypasses the selected Category.
- Directory selection is discovery convenience/pre-trust only. Evidence truth, Payee/Evidence matching, destination readiness, Payout, risk, sanctions/fraud/anti-cashout and payer authorization remain with DOC-12, DOC-10, DOC-14 and DOC-09.
- Directory unpublication or loss of a live Directory relationship stops new discovery only. It does not hide, disable, rename or invalidate an already saved Bill/Rent source or correct Payee/payment facts. Category disassociation, programme/risk suspension, invalid destination, fraud, sanctions, legal prohibition or security compromise remain separate substantive owner-controlled restrictions and apply across both acquisition methods.
- When applicable, retain bounded acquisition provenance (Directory-selected or Self-provided, stable institution/Directory reference if one already exists, acquisition Category, timestamp and relevant lineage reference) for audit/troubleshooting only; it never governs live eligibility, visibility, pricing, promotion, profitability, margin allocation, commercial reporting or ledger authority.
- Active Request, BILLS-LINKING, Consumer Payee navigation, BILLS-RECEIVE and Consumer Receiving Info behavior are retired from MVP. Append-only documentation history and retired stable IDs remain non-active evidence. No runtime historical reader, legacy Request adapter, fallback route, dormant product stack or replacement Request route is required because no production Request/Payee-role runtime existed.

### Family-level source identity and Save boundary

- Opening Pay a Bill/Rent or Setup a Bill/Rent creates only temporary pre-validation capture/session state. It does not by itself establish a durable authoritative Bill/Rent ID.
- ID establishment consumes an owner-governed source/Evidence preservation eligibility outcome. DOC-06 defines the journey boundary and does not independently define the technical persistence threshold or exact minimum fields required to establish the authoritative Bill/Rent identity. The authoritative ID must exist before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or a payment-facing handoff requires stable source identity. Pending Evidence, mismatch or scoped Admin review does not automatically prevent the ID from existing once that owner-governed outcome permits it. ID establishment alone does not imply accepted Evidence, verified Payee, destination or Payout readiness, risk clearance, Payment Obligation or Checkout readiness, payer authorization, successful Payment, Saved/current, Saved/Archived or history-only projection.
- Immediate pay-now does not ask for Save before Checkout. After confirmed Payment with a separate Payment ID linked to the Bill/Rent ID, show Payment Result. A source already Saved/current before Payment retains its existing projection without duplicate Save. For an otherwise unsaved source, resolve the optional Save decision before Activity, Payment History, Receipt or ordinary safe exit: selected Save makes the same ID Saved/current; declined, skipped, dismissed, closed or otherwise abandoned Save resolution makes it history-only. Payment, Activity and Receipt existence does not depend on Save, but those destinations do not bypass the projection resolution; no Save-from-Activity or separate Unsave action exists.
- Deliberate Setup Bill/Rent consumes the same owner-governed source/Evidence preservation eligibility outcome, establishes the authoritative ID, and because Setup is deliberate reuse/collection intent gives that same ID a Saved/current projection without a Payment or Payment ID. Saved/current means Payer Save/reuse intent and visibility only; it does not imply Evidence acceptance, Payee verification, destination readiness, Payment eligibility or standing authorization. A later Payment is created only through DOC-09 under fresh owner-controlled checks and payer authorization.
- ID establishment alone does not create a Saved/current, Saved/Archived or history-only projection. Saved/current, history-only and Saved/Archived are later projections of one source. An established source may remain unprojected only when immediate pay ends or fails before confirmed Payment, or deliberate Setup ends before its Saved/current projection is completed. DOC-09 owns applicable payment-lifecycle continuation/recovery, DOC-15 owns retention governance and requirements, and DOC-18 owns only business recording and explainability; technical representation remains separately authorized. Save never creates a second ID, clones a source, or moves/recreates Payment lineage.
- Failure or abandonment before confirmed Payment, or incomplete deliberate Setup before Saved/current projection, does not by itself make the source Saved/current, Saved/Archived or history-only, expose a Bills/Rent route or list entry, or create a user-facing incomplete-source status. After a newly confirmed Payment for an otherwise unsaved source, closing or leaving Payment Result without selecting Save is skipped Save and produces history-only before Activity, Payment History, Receipt or ordinary safe exit; the source cannot remain unprojected. Detailed continuation, cleanup, expiry and recovery follow DOC-09 where payment lifecycle is involved; DOC-15 owns retention requirements, and DOC-18 owns only business recording and explainability; technical representation remains separately authorized.

### Family-level notification and specialist handoffs

The optional one-way Payee notification is available only where the Payee is eligible under the governed Individual-Payee classification/determination policy. Institution/company or unresolved/insufficient Individual determination leaves notification unavailable; governed Individual determination plus Payer choice may expose the optional capability. DOC-06 consumes that eligibility outcome and does not independently determine Payee type. Payer contact responsibility does not remove PayPlus obligations for lawful purpose, data minimization, wrong-recipient prevention, abuse/rate-limit controls, suppression/opt-out, security, delivery records, retention and support. The notification is informational only and does not create a Request, Linking relationship, Payee acceptance requirement, reciprocal visibility, account invitation, payment authorization, or any change to payment state. DOC-06 defines none of its mechanics: DOC-05 owns only the eligibility boundary; DOC-07 owns approved Copy/disclosure/CTA; DOC-08 owns notification identity, channel, template, preference and delivery; DOC-14 owns risk/abuse; DOC-15 owns privacy/retention requirements; DOC-18 represents approved data/audit requirements; DOC-19 owns security; DOC-21 owns support/operations; and DOC-22 performs only permitted Admin execution. DOC-12 supplies any Evidence-derived classification input but does not own notification delivery. Contact provenance and lawful-basis or consent treatment remain with their applicable formal owners.

DOC-06A owns family journeys; DOC-06B owns global roots, routes and IA; DOC-06C owns Bills/Rent presentation and source projections. DOC-09 owns Payment Obligation, Checkout, payer authorization and Payment invariants; DOC-10 owns destination readiness, Payout and reconciliation; DOC-12 owns Category, Evidence, OCR/extraction, verification and Evidence-to-Payee matching; DOC-14 owns risk/sanctions/fraud/anti-cashout; DOC-15 owns privacy, masking and retention requirements; DOC-18 owns only business recording and explainability, while technical representation remains separately authorized; DOC-22 executes only permitted Admin review under the applicable owner outcomes. DOC-06 references these owners without redefining them.

### Tiered Bill presentation and return boundary

An owner-recorded Tier 3 Bill approval outcome keeps the Payer in, or returns the Payer to, the current Bill context. It is not navigation authority, a notification, Payer authorization, Provider Submission, or a direction to open executable Checkout. The Payer deliberately selects the current Bill `Pay` action, and DOC-09 then resolves current eligibility and any valid Resume after revalidation; otherwise the applicable source-owner or historical resolution remains. No new route, generic status, recovery object, or Payee/retired runtime is created.

For Tier 2, confirmed Payment, the current Evidence condition, and a DOC-10 Payout hold or release remain separate truths; ordinary Evidence lifecycle does not become Bills Activity. At Add Bill, the Payer confirms declared material facts before the distinct Save-admission outcome; material edits receive owner-defined proportionate reconfirmation, while unchanged facts do not repeat Declaration solely because current Tier evaluation occurs. Rent remains outside Bill tiers and keeps its accepted-attached-Evidence-before-Payment rule.

### Wave 2 route-family outcomes

- Retain/re-scope HOME-ROOT, PAYPLUS-ACTION-SHEET, BILLS-ROOT, BILLS-PAY, Bill/Rent detail, BILLS-ADD, Activity, Receipts, Archive, Notifications, Me and unaffected account/service roots as Payer-only surfaces.
- Remove Request Payment from Pay+ while preserving the remaining four actions without reordering or materially renaming them. Remove Requests shortcuts without inventing replacements.
- Retire active REQUESTS-ROOT, REQUESTS-DETAIL, REQUESTS-NEW, BILLS-RECEIVE, BILLS-LINKING and Consumer RECEIVING-INFO presentation. Preserve their stable identifiers only as non-active documentation lineage.
- Retain ARCHIVED-DOCS-LIST provisionally under the Founder-approved W2-FD-05 decision (Option A). This is provisional retention only and does not change route status or authorize detailed Restore. Archive remains a visibility projection of the same source and does not erase or rewrite Evidence, Payment, destination, Payout, reconciliation or audit history. Exact Restore, prior-version, Evidence-version and replacement-source presentation remains deferred to DOC-06B/DOC-06C with DOC-10 payout/reconciliation blockers, DOC-11 refund/dispute/chargeback/case blockers, and DOC-12/DOC-15/DOC-18 Evidence, privacy/retention and data/lineage handoffs.

No route status, Route Register, diagram, traceability, status matrix, open-question register, records, Management Roadmap or later-wave document is changed by this parent baseline.

---

## Active Normative Baseline

The sections below are active current requirements for the Payer-only family and compatible authentication, Checkout, Instructions, Activity/Receipt, failure and return contracts. Retired Request, Linking, Receive and Payee-user identifiers appear only in provisions explicitly marked as retirement or append-only documentation history. They define no runtime reader. Append-only Version History remains historical evidence and is not current product behavior.

## 1. Purpose

This parent document governs the DOC-06 family for PayPlus user journeys, UX flow, navigation, route taxonomy, service blueprint touchpoints, and UX acceptance mapping.

PayPlus is a controlled Bill and Rent Payment App in which Consumer Users act as Payers. Bills use the accepted Tier 1/2/3 Evidence model, while Rent retains mandatory attached Evidence accepted before Payment. A Payee is an economic recipient who may be an individual or institution/company and need not be a PayPlus User. The family therefore defines Payer-only Bill/Rent journeys, bounded acquisition, payment handoffs and history visibility; it does not define an active Consumer Payee product.

DOC-06 is now a family index and governance map. Detailed content is split into DOC-06A to DOC-06D so unfinished route specifications can be tracked clearly without overloading one document.

This modularization does not change PayPlus product scope, payment behavior, risk controls, privacy rules, or operational decisions. It only separates ownership and navigation.

---

## 2. Scope and Baseline

The current DOC-06 family defines:

- Payer, Payee-as-recipient, Admin, operations, and system handoffs;
- logged-in navigation and route taxonomy;
- controlled Bill, separate Rent, Evidence, reminder, Activity and receipt UX handoffs;
- user-facing state visibility and handoff points to payment, evidence, notification, privacy, risk, data, and admin owner documents;
- UX requirements, acceptance criteria, and test-readiness mapping.

The DOC-06 family does not own detailed payment processing, payout, refund, notification templates, evidence verification algorithms, data schema, security architecture, or admin workflow details. Those details remain with their owning documents.

Rent and the twelve specified supported controlled Bill Categories remain baseline scope where supported by acceptable Evidence and enabled controls. Active Request/BILLS-LINKING, Consumer Payee, arbitrary P2P, open marketplace and uncontrolled recipient journeys are retired or prohibited. Retired stable IDs and prior meanings remain append-only documentation history only; no Request/Payee-role runtime records or readers exist.

### 2.1 MVP Scope Summary

The DOC-06 family keeps the following current Wave 2 MVP journey scope:

- Payer registration, login, verification, dashboard and account journeys;
- Payer-created controlled Bill and separate Rent setup/payment journeys;
- Category-first Bill acquisition through Directory-selected or Provide Payee myself methods;
- tier-aware type/provenance handoff, specialist gates, payer authorization and payment result/history;
- deliberate setup Save and immediate-pay post-payment Save using the same authoritative Bill/Rent ID;
- bounded optional one-way Individual-Payee notification after governed eligibility determination;
- evidence capture, OCR/autofill review, user correction, evidence verification outcome visibility, duplicate/reused evidence handling, and bounded specialist/Admin review handoffs;
- Bills, rent, tenancy, reminder, activity, dashboard, Pay+, shortcut, notification, receipt, failure, exception, and support handoff journeys;
- controls preventing wallet, stored-value, cashout, unsupported peer-to-peer, lending, and automatic recurring-payment journeys.

### 2.2 User Role Summary

| Role | Description | MVP Login? | Key Journey Responsibility |
| --- | --- | ---: | --- |
| Payer | Consumer User who provides source/Evidence facts, reviews owner-controlled outcomes, and authorizes eligible payment. | Yes | Create controlled Bill/Rent contexts, select acquisition method, Save or continue, authorize payment, track history. |
| Payee | Economic recipient; may be an individual or institution/company and need not be a PayPlus User. | No | Recipient-side policy and specialist handoffs only; no active Consumer Payee route, Request or Linking product. |
| Admin / Operations | Internal user executing only owner-approved review, configuration, support or exception work through governed access. | Yes | Consume specialist-owner outcomes and perform bounded DOC-22 execution without creating product, Evidence, Payment, payout, refund, risk, privacy or data authority. |
| System | Automated services handling status changes, notifications, validation, audit events, and integrations. | No | Route, notify, validate, and record events under specialist ownership. |

### 2.3 UX Surface Summary

The DOC-06 family covers Payer UX, Payee-as-recipient handoffs, Admin touchpoints and system service handoffs at the human-readable product level:

| Surface | Covered Examples | Main DOC-06 Family References |
| --- | --- | --- |
| Payer UX | registration, login, dashboard, controlled Bills, separate Rent, Evidence handoff, payment/Checkout, Save/no-Save, Activity, Receipts, optional Individual notification, account basics. | DOC-06A / DOC-06B / DOC-06C |
| Payee-recipient boundary | Recipient facts, governed Individual determination and specialist destination/notification handoffs only; no Consumer Payee login, dashboard, Request, Linking or reciprocal visibility. | DOC-05 plus DOC-06A/C handoffs |
| Admin UX touchpoints | Owner-required Evidence, type, Payment, payout, refund/dispute, risk, privacy, support and configuration handoffs. The applicable specialist owns policy and outcome; DOC-22 owns permitted execution only. | DOC-06A handoff; specialist owners plus DOC-22 |
| System service touchpoints | Source identity handoff, OCR/autofill, verification routing, duplicate detection, owner-controlled status/result inputs, notification events, audit events and permitted Admin-queue handoff. | DOC-06A handoff; applicable domain owner, DOC-18 and DOC-22 |

---

## 3. DOC-06 Family Governance Map

| Document | Governs | Does Not Govern | Current Completion Status |
| --- | --- | --- | --- |
| DOC-06 | Parent UX/service-blueprint overview, family map, scope boundaries, prohibited journey controls, family decision summary, dependencies, and split governance. | Detailed route specs, detailed component behavior, full acceptance matrix. | Active parent baseline. |
| DOC-06A | Core Payer, economic-Payee handoff, Admin/system, Evidence, review, authorization, visibility, notification, receipt, failure and exception service journeys. | Global app navigation taxonomy, detailed Bills route UI, specialist policy or Admin execution design. | Working baseline; service-blueprint refinement still needed. |
| DOC-06B | Navigation IA, dashboard structure, bottom navigation, Pay+ action sheet, route/screen/component/action standards, route registry, and route completion status. | Deep Bills/rent/tenancy behavior or payment checkout logic. | Working baseline; Instructions, Payment Profile, Activity, Receipts & Statements, Offers, Rewards, Referral, Me core child routes, active `ARCHIVED-ROOT` and active `ARCHIVED-BILLS-LIST`, More and Notifications are defined at human-readable route level. `ARCHIVED-DOCS-LIST` is provisional and unreachable through active UI. Requests, BILLS-LINKING and Consumer Receiving Info remain retired stable IDs in append-only documentation history only. Several secondary routes remain incomplete. |
| DOC-06C | Bills, fees, rent, tenancy, cards, detail pages, activity, reminders, evidence UX, Payer actions, and Bills-route handoffs. | Checkout processing, full evidence verification logic, final data model, or admin queue design. | Partially defined; Bills module has strong baseline but not final UI. |
| DOC-06D | UX requirement IDs, acceptance criteria, route/action/state/event/test mapping, and UX test-readiness tracking. | Business policy decisions or implementation tickets. | Working acceptance and test-readiness baseline; route-family coverage exists, while detailed executable test cases remain for DOC-20 and the AI execution layer. |

Formal child documents use DOC-06A to DOC-06D. They inherit DOC-06 source-of-truth tier unless a child document explicitly states otherwise.

### 3.1 Single-Owner Rule for Future Drafting

Each route, function, status, screen, or flow should have one primary owning document. Other DOC-06 family documents may reference it, define entry or handoff behavior, or list dependencies, but must not duplicate the same detailed requirements.

Use this rule before adding new content:

| If the change is mainly about... | Primary owner | Other docs may only... |
| --- | --- | --- |
| User journey, service step, lifecycle, status meaning, exception path, or role responsibility | DOC-06A | Link to the journey or status and define navigation handoff only. |
| Navigation, route ID, dashboard placement, shortcut, bottom navigation, global non-Bills route shell, route-level UX behavior, or IA | DOC-06B | Reference domain rules and defer detailed lifecycle, payment, evidence, privacy, data, and operations behavior to the owning document. |
| Bills, rent, tenancy, evidence UI, reminder UI, activity UI, Payer Bills actions, or Bills-route handoff | DOC-06C | Reference global navigation or lifecycle rules without restating them. |
| UX requirement ID, acceptance criterion, route/action/state/event/test mapping, or test readiness | DOC-06D | Reference source requirements and avoid adding new product behavior. |

If a topic appears to belong to more than one child document, update the parent route matrix first to identify the primary owner and reference-only documents before drafting detailed content.

---

## 4. Route Completion Status Matrix

This matrix prevents the split from creating a false impression that all routes are complete.

| Route / Area | Primary Owning Doc | Reference / Handoff Docs | Status | Notes |
| --- | --- | --- | --- | --- |
| Entrance and Authentication | DOC-06B | DOC-06A for journey; DOC-07/DOC-15/DOC-19 for presentation, privacy, and security; DOC-20 for derived acceptance tests | Defined Behavior Baseline / Security-Control Contract Defined / Final Design, Mechanisms and Evidence Pending | `ENTRANCE-ROOT` is the public root; `AUTH-LOGIN` resolves to Fast/Full Login; Recovery, Registration, Account Activation, `PHONE-VERIFICATION`, `IDENTITY-VERIFICATION`, and `PAYMENT-PASSCODE-SETTINGS` are assigned. The family uses capability-aware Outcome-to-Resolution handling without changing route or status decisions. `AUTH-RECOVERY` now has a defined product flow and safe continue/restart/redirect/wait/Support/stop baseline. Normal success enters `HOME-ROOT`; approved deeplinks may resume only after revalidation. |
| Home Dashboard | DOC-06B | DOC-06A for journey touchpoints; DOC-06C, DOC-07, DOC-08, DOC-09, DOC-10, DOC-11, DOC-13, DOC-15, DOC-20, and DOC-22 for owned handoffs | `HOME-ROOT` Assigned / Partially Defined | The reviewed route-level baseline covers Greeting, Important Notice, Home Hot Offer, Upcoming Bills / Rent, Recent Activity, section-level resilience, Home-specific accessibility, and presentation governance. DOC-06B owns Home presentation and navigation; final visual design, exact DOC-07 Copy and identifiers, technical mechanics, and later DOC-20 evidence remain pending with their formal owners. |
| Bottom Navigation | DOC-06B | Child route owners for destination behavior | Working Baseline | `HOME-ROOT`, Bills, `PAYPLUS-ACTION-SHEET`, Offers, and Me baseline is defined; final visuals and remaining child-route detail remain open. |
| Pay+ Action Sheet | DOC-06B | DOC-06A for journey entry; DOC-06C/DOC-09 for Bills/payment handoff | Defined Behavior / Not Final Visual Design | Four retained actions keep their existing order and meaning after Request Payment retirement; destination handoffs, availability, completion, return, configuration limits, and motion principles are defined. |
| Bills / Rent / Tenancy | DOC-06C | DOC-06B for route entry/archive family; DOC-06A for lifecycle; DOC-09/DOC-12 for payment/evidence detail | Partially Defined | BILLS-PAY, BILLS-ACTIVITY, BILLS-EVIDENCE, BILLS-REMINDER, and `ARCHIVED-BILLS-LIST` have Payer-only working baseline rules; BILLS-RECEIVE is a retired stable ID with no active or runtime-reader behavior. |
| Payment / Checkout | DOC-06B for route-level UI/UX; DOC-09 for Payment Domain architecture | DOC-06A/DOC-06C for source journey, entry, return, and handoff; applicable content, notification, technical, and acceptance owners | `PAYMENT-CHECKOUT` Defined Baseline | DOC-06B owns the adaptive Checkout Workspace presentation, entry, return, and handoff behavior. DOC-09 owns payment objects, invariants, and authoritative payment meaning. Detailed UI remains in DOC-06B rather than being duplicated here; exact content, visual, technical, prototype, validation, implementation, acceptance, and operational evidence remain pending with the applicable owners. |
| Requests | DOC-06B | Documentation governance for append-only history | Retired active MVP / documentation evidence only | `REQUESTS-ROOT`, `REQUESTS-DETAIL`, and `REQUESTS-NEW` have no active behavior, runtime reader, replacement route, adapter, fallback or dormant runtime. Stable IDs remain non-active documentation lineage only. |
| Instructions | DOC-06B for route UX; DOC-09 for payment-instruction behavior | DOC-06A/DOC-06C for entry or return touchpoints | Core Route Behavior Defined / Not Final Visual Design | `INSTRUCTIONS-ROOT` and `INSTRUCTIONS-DETAIL` distinguish pending pay-later instructions from incomplete funding, define permitted actions, and hand off to DOC-09 checkout/payment behavior. |
| Activity and Receipts & Statements | DOC-06B for global route shells | DOC-06A for receipt/history touchpoints; DOC-06C for bill/rent-specific activity; DOC-08 for receipts/statements; DOC-09/DOC-10/DOC-11 for payment/payout/refund facts | Working Baseline / Not Final Visual Design | Global Activity and Receipts & Statements remain separate. `RECEIPTS-ROOT` owns search and the document list; `RECEIPT-DETAIL` / `STATEMENT-DETAIL` open the shared in-app PDF preview, while list-level `Download` acts directly. |
| Reminders | DOC-06C for bill/rent reminders | DOC-06B for shortcut/route shell; DOC-08 for notifications; DOC-09 for payment-instruction alerts | Working Baseline / Not Final Visual Design | Bill/rent reminder list/detail behavior is defined. Payment-instruction alerts remain owned by the instruction/payment flow and do not become reminder records. |
| Offers and Rewards | DOC-06B for route shells and placement | DOC-13 for promotion, entitlement, instrument, lifecycle, and fulfilment logic; DOC-09 for authoritative payment meaning | Offers Child Lists and Rewards Defined / Not Final Visual Design | `OFFERS-ROOT` governs sectioned discovery; its child lists use multi-collection membership, root duplicate suppression, and stable ordering. `REWARDS-ROOT` governs issued rewards through Active and History views; `REWARD-DETAIL` shows full details and terms but does not create a second checkout path. `BILLS-PAY` remains an external DOC-06C handoff; DOC-06B owns adaptive Checkout presentation, DOC-13 owns benefit rules, and DOC-09 owns the underlying Payment Domain architecture and authoritative payment meaning. |
| Me / Account | DOC-06B for route UX | DOC-06C/DOC-08/DOC-10/DOC-12/DOC-15/DOC-18/DOC-19/DOC-21/DOC-22 for domain handoffs | Core Account and active Archive root/list defined; archived-document identity provisional / Other Details Pending | `ME-ROOT`, account/security/privacy routes, Phone Verification, Identity Verification, Payment Passcode Set/Change/Reset, explicit login-method and Set/Change Password controls, active `ARCHIVED-ROOT` and active `ARCHIVED-BILLS-LIST` remain defined. `ARCHIVED-DOCS-LIST` is provisional and unreachable through active UI. Consumer Receiving Info is retired; its stable ID remains append-only documentation history only. |
| Payment Profile / Cards | DOC-06B for route UX | DOC-09/DOC-15/DOC-19 for payment-domain, privacy, and security detail | Core Route Behavior Defined / Not Final Visual Design | `PAYMENT-PROFILE-ROOT` and its Cards/Profiles child screens manage tokenized cards and saved split-card profiles with a confirmed maximum of 6 cards; DOC-06B owns Checkout route-level UI/UX and DOC-09 owns authoritative payment meaning. |
| Referral | DOC-06B for route UX and registration handoff | DOC-13 for referral, qualification, entitlement, and reward logic | Child-Screen Behavior Defined / Not Final Visual Design | `REFERRAL-ROOT`, role-sensitive referrer/referee entitlement list/detail/claim screens, reusable sharing, registration attribution handoff, qualification display, and issued-reward handoff are defined. |
| Notifications | DOC-06B / DOC-08 | Notification and domain destination owners | Defined Behavior / Not Final Visual Design | `NOTIFICATION-ROOT` groups Inbox, Detail, and Settings. Home opens Inbox, Me opens Settings, and notification actions hand off to the owning domain after current-state checks. |
| More | DOC-06B | DOC-15 for preference/privacy; DOC-18 for data/events; DOC-22 for permitted configuration execution; destination owners for launched-route outcomes | Defined Baseline / Not Final Visual Design | `MORE-ROOT` uses Normal and Manage modes, supports up to 7 configurable shortcuts plus protected More, account-level preference override, current-default restore, accessible management controls, and approved secondary-service handoffs without replacing Me or owning destination behavior. DOC-06B owns shortcut/default/availability product policy. |

---

## 5. Product Journey Summary

PayPlus supports Payer-created controlled Bill journeys with their accepted tiered Evidence model and the separate mandatory-Evidence Rent journey. Consumer Users are Payers only; a Payee is an economic recipient and need not be a PayPlus User.

- A Bill journey is Category-first and then uses the selected Category's Directory or `Provide Payee myself`. Rent uses a separate tenancy journey and does not use the Bill Directory.
- Deliberate Setup and immediate pay-now both consume an owner-governed source/Evidence preservation outcome and establish one authoritative Bill/Rent ID before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or a downstream payment handoff requires stable source reference. DOC-06 consumes that outcome and does not define technical persistence thresholds, exact fields, Evidence acceptance, indefinite-retention controls or non-destructive handling mechanics.
- Deliberate Setup gives the same authoritative Bill/Rent ID a Saved/current projection because Setup expresses reuse intent. Immediate pay-now completes owner-controlled gates and DOC-09 Payment, shows Payment Result, offers optional Save, and then gives the same ID Saved/current or history-only treatment before Activity/History/Receipt navigation.
- An established but abandoned pre-Payment source does not receive a user-facing projection, status or route solely because an ID exists. Payment, Activity and Receipt records do not depend on Save.
- Admin, risk, Evidence, destination, Payout, privacy, notification and operations controls remain with their formal owners. Active Request/BILLS-LINKING, Consumer Payee and reciprocal-visibility behavior are retired; retired stable IDs and prior meanings remain append-only documentation history only.

Detailed journeys are in DOC-06A. Bills/rent/tenancy route behavior is in DOC-06C.

---

## 6. Cross-Document Ownership Boundaries

| Topic | UX Family Role | Owning Detail Document |
| --- | --- | --- |
| Outcomes, user-facing resolution presentation, wording, disclosures, and authorization language | DOC-06 identifies route/domain Outcomes and permitted Resolution Strategies. | DOC-07 |
| Notifications, receipts, communication channels, delivery logging | DOC-06 identifies trigger points and route destinations. | DOC-08 |
| Checkout, payment quote, funding, payment instruction, payment states | DOC-06 identifies entry, handoff, return, and status visibility. | DOC-09 |
| Payout and reconciliation | DOC-06 identifies user-facing payout or settlement visibility. | DOC-10 |
| Refund, cancellation, reversal, dispute, chargeback | DOC-06 identifies user journey states and handoffs. | DOC-11 |
| Evidence categories, OCR, verification, duplicate detection, payee verification | DOC-06 identifies UX capture/review points. | DOC-12 |
| Promotions, offers, coupons, rewards, referral, membership | DOC-06 identifies placement and route surfaces. | DOC-13 |
| AML, anti-cashout, fraud, risk triggers, dynamic auth | DOC-06 identifies user-facing risk/review states. | DOC-14 |
| Privacy, masking, retention, approved-purpose access | DOC-06 identifies display and permission boundaries. | DOC-15 |
| Data objects, lineage, audit events, event taxonomy, reporting | DOC-06 identifies required signals and events at a high level. | DOC-18 |
| Authentication, tokenization, access control | DOC-06 identifies user journey touchpoints. | DOC-19 |
| Testing and go-live | DOC-06D maps UX acceptance and test readiness. | DOC-20 |
| Monitoring, support, incident, operational SOPs | DOC-06 identifies exception journeys and support handoffs. | DOC-21 |
| Admin dashboard, queues, permissions, controlled overrides and configuration | DOC-06 identifies only an owner-required Admin/operations handoff. The applicable specialist retains policy and outcome authority. | DOC-22 for permitted execution; applicable specialist owner for meaning |

---

## 7. Prohibited Journey Controls

PayPlus must not provide UX paths that create or imply:

- wallet balances;
- stored-value accounts;
- unrestricted peer-to-peer transfer;
- user-controlled cash accounts;
- cash withdrawal;
- payer self-cashout;
- unsupported open-loop money transfer;
- crypto payment;
- lending, credit issuance, investment, deposit, or savings journeys;
- marketplace escrow journeys;
- automatic recurring payment unless separately approved.

Deferred user payment instruction for single-card and split-card payment remains in scope under DOC-09 and is not automatic recurring payment.

---

## 8. Open Questions

DOC-06 family open questions are now distributed as follows:

| Area | Primary Owner |
| --- | --- |
| Core Payer journey, review, exception, status, visibility, and service blueprint questions | DOC-06A; retired Request/Linking IDs remain append-only documentation history only |
| Dashboard, bottom navigation, Pay+ action sheet, route taxonomy, global shortcut and placement questions | DOC-06B |
| Bills/rent/tenancy cards, details, Activity, reminders, Evidence, and Payer action questions | DOC-06C; retired Linking IDs remain append-only documentation history only |
| UX requirement IDs, acceptance criteria, route/action/state/event/test mapping, and test-readiness questions | DOC-06D |

Cross-document blockers remain tracked in docs/traceability/open-questions-register.md.

---

## 9. Dependencies

| Dependency | Purpose |
| --- | --- |
| DOC-00 | Documentation governance and source-of-truth rules. |
| DOC-01 | Product overview and positioning. |
| DOC-02 | Business model, pricing, fee logic, and monetization. |
| DOC-03 | Regulatory assessment. |
| DOC-04 | Compliance control framework. |
| DOC-05 | Master product requirements and MVP scope. |
| DOC-07 | User-facing disclosure, authorization, evidence, privacy, and policy wording. |
| DOC-08 | Notification templates, channels, triggers, user preferences, and delivery logging. |
| DOC-09 | Payment Domain architecture and business invariants from payment-facing Bill/Rent facts through Payable Basis, Payment Obligation, Checkout, funding execution, confirmed Payments, and Payment Applications. Retired Request meanings remain append-only documentation history only; Settlement and Payout remain with DOC-10. |
| DOC-10 | Payout, payout readiness, payout destination, batching, and reconciliation. |
| DOC-11 | Refund, cancellation, reversal, dispute, and chargeback handling. |
| DOC-12 | Bill category, document AI/OCR, evidence verification, duplicate detection, and payee matching. |
| DOC-14 | AML, anti-cashout, fake evidence, duplicate evidence, collusion, and risk controls. |
| DOC-15 | Privacy, data protection, masking, retention, and lawful data use. |
| DOC-18 | Canonical data, status/event, audit, lineage and reporting representation for current Bill/Rent, Evidence, Payment and payout. DOC-18 does not create Request/participant runtime objects or decide retention policy. |
| DOC-19 | Mechanism-neutral authentication, protected-value, access-enforcement and security-control requirements; payer authorization remains with DOC-09, privacy with DOC-15, and representation with DOC-18. |
| DOC-21 | Monitoring, support escalation, incident handling, and operations runbooks. |
| DOC-22 | Permitted Admin execution, queues, permissions, configuration and controlled overrides under the applicable product, Evidence, payment, payout, refund/dispute, risk, privacy and operations owners. |
| Future UX Wireframes | Defines screen-level UX and interaction design. |

---

---

## 10. Master Decision Summary

This parent summary preserves the DOC-06 family decisions. Detailed decisions also appear in the child document that owns the relevant area.

| Decision | Status |
| --- | --- |
| Material AUTH handling follows `Decision/Evaluation -> Outcome -> Resolution Strategy -> Message/CTA`, with notification, audit, security, testing, Support, and admin behavior retained by their specialist owners. Resolution is not a route or persistent status and does not change approved AUTH decisions. | Confirmed |
| `ENTRANCE-ROOT` is the unauthenticated entry screen; the `AUTH-LOGIN` family and `AUTH-REGISTRATION` own Login and Create Account. Normal successful authentication enters `HOME-ROOT`; approved contextual deeplinks may resume their intended destination. | Working Baseline / Behavior Defined |
| Restricted account creation requires one unique verified primary email and one explicitly enabled login method. Registration attempts reserve no identifiers. Email/password, Google, and Apple may access the same account only through explicit linking; social accounts may set a password later; phone, identity, and six-digit payment-passcode completion remain mandatory through `ACCOUNT-ACTIVATION` before full registration. | Confirmed |
| Payer registration and login are MVP scope. | Confirmed |
| Payee registration and login are not MVP scope; Payee remains an economic recipient. | Re-scoped Payer-only baseline |
| Payer dashboard is MVP scope. | Confirmed |
| Payee dashboard is not MVP scope; no Consumer Payee runtime or reader is defined. | Re-scoped Payer-only baseline |
| Payee-created Requests are retired from active MVP; retired stable IDs and prior meanings remain append-only documentation history only. | Retired active behavior |
| Payer-created payments are MVP scope. | Confirmed |
| Tenancy and rent journeys are MVP scope. | Confirmed |
| Payee-created bill, invoice, tenancy, or obligation setup is retired from active MVP; Payer-created controlled Bill/Rent journeys remain. | Retired active behavior |
| Payer-created bill, invoice, tenancy, or obligation setup is MVP scope. | Confirmed |
| Payer-created payments use owner-controlled Evidence, Payee, destination, risk, Payout, readiness and payer-authorization gates; no Payee acceptance or account is required by the Payer-only model. | Confirmed |
| Payee adoption, reciprocal visibility and participant Linking are retired active behavior; retired stable IDs remain documentation history and neutral future seams require separate governance. | Retired active behavior |
| Payer review and authorization are required before payment. | Confirmed |
| Every Payment must remain tied to an acceptable controlled Bill or Rent context. Bills consume the accepted Tier 1/2/3 Evidence treatment and Rent retains mandatory attached Evidence accepted before Payment; DOC-12 and the applicable product, payment and risk owners govern detailed qualification. | Confirmed |
| OCR/document AI-assisted evidence capture, autofill, user correction, duplicate warning, and evidence verification routing are required UX touchpoints where enabled. | Confirmed |
| Payer-visible source, Payment, Activity and Receipt records follow their owning domains; reciprocal payer/payee visibility is not an active MVP requirement. | Re-scoped Payer-only baseline |
| Owner-controlled risk review and bounded Admin execution handoffs are required where applicable; DOC-06 grants neither generic review nor cross-domain override authority. | Confirmed |
| Company/Individual source values remain non-overwriting provenance; `Reviewed` and `Resolved` are separate, and label-only review may remain asynchronous, non-user-facing and nonblocking when every concrete owner-controlled gate passes. | Founder-approved |
| Institution/company and unresolved/insufficient Individual determination leave the optional Payee notification unavailable; a governed Individual determination plus Payer choice enables only an informational one-way capability without Request, Linking, reciprocal visibility, authorization or payment-state meaning. | Founder-approved |
| Wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are prohibited. | Confirmed |
| Final payment processor, operating-bank setup, detailed KYC/KYB steps, fees, partner/risk/reconciliation controls for multi-card payment, and dispute policy details remain open or to be confirmed. The MVP maximum is 6 cards per payment/profile. | Partially Open |
| Major functions and modules must be independently disableable. | Confirmed |
| Promotion discovery, issued-reward management, and referral participation use separate DOC-06B routes. Referral sharing, registration attribution, qualification progress, role-sensitive entitlement claiming, two-tab Referral Rewards behavior, and canonical issued-reward handoff are defined; commercial availability and campaign conditions remain governed by DOC-13. | Working Baseline / Not Final Visual Design |
| `HOME-ROOT` is task-first and uses bottom navigation `Home`, `Bills`, `Pay+`, `Offers`, and `Me`. | Designated Layout Baseline |
| `Pay+` is the preferred center bottom-nav action label and opens `PAYPLUS-ACTION-SHEET`. Wave 2 retains the four existing actions in their existing order after retiring Request Payment; exact visual specification remains open. | Defined Behavior / Not Final Visual Design |
| `Add Bill / Rent` includes scan QR, upload evidence, and manual entry inside the setup flow; QR/upload is not a standalone instant-payment action. | Working Baseline |
| Pay+ `Request Payment` is retired from active MVP. No replacement Request or Linking action is created. | Retired active behavior |
| Pay+ `Continue Payment` is disabled with no active pending Payment Instruction or continuable incomplete Checkout Workspace, opens one `INSTRUCTIONS-DETAIL` when exactly one managed item exists, and opens `INSTRUCTIONS-ROOT` when more than one exists; review-blocked items remain visible but cannot continue. | Confirmed |
| Requests shortcut is retired without a replacement; remaining Home shortcuts and More retain their existing owner-controlled configuration boundaries. | Re-scoped Wave 2 baseline |
| Dashboard shortcuts use a DOC-06B owner-approved catalog/default and may be configured through permitted DOC-22 execution; users may reorder eligible entries, override the default and restore the current owner-approved default. | Confirmed |
| Important Notice presents one eligible Inbox-backed notification at a time. DOC-06B owns its Home session dismissal and body, source-action, Detail-close, and zero-state route behavior; DOC-08 and source owners retain notification and business meaning. | Defined Behavior / Not Final Visual Design |
| Home Hot Offer is the Offer-only Home placement selected through DOC-22 Admin controls. DOC-06B owns Home layout, interaction, and `OFFER-DETAIL` handoff; DOC-13 retains canonical Offer truth, while final visual and technical treatment remain pending. | Defined Behavior / Not Final Visual Design |
| Upcoming Bills / Rent presents a bounded payer-role projection of DOC-06C candidates and hands protected actions back to the source-owning route; DOC-06B owns only Home selection, ordering, cap, presentation, and navigation. | Defined Behavior / Not Final Visual Design |
| Recent Activity presents a bounded projection of completed outcomes from DOC-09, DOC-10, and DOC-11, with source-published ordering and funds-flow direction and DOC-06B-owned Home navigation. | Defined Behavior / Not Final Visual Design |
| HOME-ROOT uses section-level graceful degradation and Home-specific accessible interaction under DOC-06B, while source and technical owners retain cache, freshness, session, implementation, and failure classification. Admin presentation cannot alter canonical business truth. | Defined Behavior / Technical and DOC-20 Evidence Pending |
| Global Activity is an account-level event/lifecycle route, while Receipts & Statements is a file/document route for receipt and statement files. Proof of payment remains a direct document action from the relevant Activity context for MVP. They must not be merged into one generic history hub. | Working Baseline / Not Final UI |
| Activity root uses accounting-style entries with date, obligation/payment name, counterparty, positive/negative amount direction, and mapped status. Tapping an entry expands available actions before routing to `ACTIVITY-DETAIL`. | Working Baseline / Not Final UI |
| Receipts & Statements uses `RECEIPTS-ROOT` as the searchable list. `View` opens a shared in-app PDF preview through `RECEIPT-DETAIL` or `STATEMENT-DETAIL`; `Download` downloads directly. Exact PDF design remains open. | Working Baseline / Not Final PDF Design |
| The dashboard flow and layout are designated for MVP discussion, but final UI design, exact component specification, and exact route-level screen specification are not finalized. | Confirmed |
| Bills tab working baseline is Payer-only `BILLS-PAY` with bill/rent cards, detail pages, bill/rent-specific activity sub-routes, Evidence handoff, Archive handoff, and Add Bill / Rent setup. Archived saved-source projections are excluded from active Bills filters and remain Payer-accessible through `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST`. | Re-scoped Wave 2 baseline |
| `BILLS-RECEIVE` is retired active Consumer Payee behavior; its stable ID remains only as non-active documentation lineage. | Retired active behavior |
| `PAYMENT-CHECKOUT` identifies the `Defined baseline` checkout flow/screen group. DOC-06B owns its route-level adaptive Workspace UI/UX, entry, return, and handoff behavior; DOC-09 owns Payment Domain architecture, objects, invariants, and authoritative payment meaning. | Defined Baseline / Final Visual, Technical, and Validation Evidence Pending |
| Bills activity route uses `BILLS-ACTIVITY` and `BILLS-ACTIVITY-DETAIL` only for payment, payout/transfer, failure, return, refund, and reversal activity linked to one Bill/Rent source context. Request, Evidence, ordinary edit and internal audit histories remain in their owning domains. | Working Baseline / Not Final |
| Bills reminder route uses `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`, linked reminder IDs, bill/rent setup frequency, reminder defaults, custom override, soft-delete behavior, and DOC-08/DOC-09/DOC-18 ownership boundaries. | Working Baseline / Not Final |
| Bills evidence route treats Evidence as a bill/rent detail sub-flow, using `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`; Evidence actions live inside bill/rent detail and extracted fields populate bill/rent details. DOC-12-owned Evidence status is one input to combined readiness, not readiness itself: it does not establish Payable Basis, Payment Obligation, destination/Payout readiness, risk clearance, Checkout eligibility or payer authorization. DOC-09, DOC-10 and DOC-14 own those separate dimensions, and the user-facing readiness presentation consumes their combined owner-controlled outcome. | Working Baseline / Not Final |
| Evidence proves or supports an obligation but is not itself an obligation. A Request is not required for a Payer-created controlled Bill/Rent source, Payment or Payout; Bills use their accepted tiered Evidence treatment and Rent retains mandatory attached Evidence. | Confirmed |
| Former Request lifecycle states remain append-only historical records only; no active Request state machine or dormant runtime is defined by Wave 2. | Retired active behavior |
| Payment Profile route uses `PAYMENT-PROFILE-ROOT` for tokenized card management and saved split-card profile management; it does not authorize payment or replace DOC-09 checkout. | Working Baseline / Not Final |
| Approved prominent sensitive-value reveal and material changes to existing identity or contact data require payment passcode or approved reauthentication. Payer-entered destination facts are changed only through the applicable Bill/Rent journey and owner controls. First-time identity verification during Account Activation does not require a pre-existing payment passcode. Ordinary authenticated evidence, receipt, statement, invoice, and proof viewing/download does not require an extra prompt solely because the document is viewed or downloaded. | Confirmed |
| `ME-ROOT` is the permanent bottom-navigation account-control route for the Payer-only Consumer User. DOC-06B defines Account Information, Phone Verification, Identity Verification, Login & Security, Payment Passcode Set/Change/Reset, and Privacy & Data behavior while preserving handoffs to established feature owners. Provider-specific mapping, exact technical security mechanisms, implementation evidence, and final visual design remain pending; the mechanism-neutral DOC-19 security-control contract is defined. | Working Baseline / Core Account Routes Defined |
| `ACTIVITY-ROOT` is the Payer-only account-level financial activity route. `RECEIVING-INFO` has no active Consumer Payee profile-library or runtime-reader behavior; its stable identifier remains only as non-active documentation lineage. Destination snapshots remain owned by the applicable current domains. | Re-scoped Payer-only baseline |
| `ARCHIVED-ROOT` exposes the Saved/Archived Payer visibility projection for previously Saved/current Bill/Rent sources, with `ARCHIVED-DOCS-LIST` provisionally retained under W2-FD-05 Option A. Archived sources are excluded from the active/current Bills list. Exact Restore, prior-version and Evidence-version behavior remains deferred to DOC-06B/DOC-06C with DOC-10/DOC-11 blockers and DOC-12/DOC-15/DOC-18 handoffs. | Re-scoped / Founder-approved provisional route retention |
| `ARCHIVED-DOCS-LIST` is provisionally retained under W2-FD-05 Option A; exact Restore eligibility, revalidation, prior-version, Evidence-version and replacement-source presentation remain deferred to DOC-06B/DOC-06C with DOC-10 payout/reconciliation blockers, DOC-11 case blockers and DOC-12/DOC-15/DOC-18 Evidence, privacy/retention and data/lineage handoffs. | Deferred / Founder-approved provisional route retention |
| Archive is a same-source Payer visibility projection that does not erase or rewrite Evidence, completed financial history, destination/payment snapshots, Payout, reconciliation or audit lineage. | Confirmed |
| Participant Linking and automatic user-to-user matching are retired active behavior; no Linking acceptance or reciprocal-visibility flow is defined by Wave 2. | Retired active behavior |
| Tenancy evidence is treated as contract/relationship evidence, while invoices/bills usually support obligation/payment-cycle evidence; detailed data structure remains owned by DOC-12 and DOC-18. | Working Baseline |

## 11. Parent Acceptance Criteria

The DOC-06 parent is acceptable when:

- DOC-06A to DOC-06D exist and are linked from this parent;
- each child document clearly states what it governs and what it does not govern;
- incomplete routes and deferred details are visibly marked;
- stable IDs are introduced progressively without forcing unfinished route detail;
- authentication acceptance includes `ENTRANCE-ROOT`, the `AUTH-LOGIN` family, capability-aware `AUTH-RECOVERY`, `AUTH-REGISTRATION`, `ACCOUNT-ACTIVATION`, `PHONE-VERIFICATION`, `IDENTITY-VERIFICATION`, and `PAYMENT-PASSCODE-SETTINGS`, with Outcome-to-Resolution handling, defined child-flow behavior, normal successful entry to `HOME-ROOT`, and approved contextual return;
- all currently identified global product areas have stable destination IDs, including `PAYPLUS-ACTION-SHEET`, `MORE-ROOT`, the `NOTIFICATION-ROOT` family, and DOC-06B/DOC-09 `PAYMENT-CHECKOUT` under their route-UX/domain ownership split;
- `PAYPLUS-ACTION-SHEET` acceptance covers the retained four-action order after retiring Request Payment, Category-first Bills handoff, separate Rent handoff, instruction-count routing, completion/return behavior, availability treatment, and no-side-effect boundary while final visual design remains open;
- `MORE-ROOT` acceptance covers one root with Normal and Manage modes, a default and maximum of 8 Home shortcuts including protected More, account-level preference override, accessible add/remove/reorder behavior, current-default restore, unsaved-change handling, availability precedence, and secondary-service handoffs;
- the Notifications family identifies `NOTIFICATION-ROOT`, `NOTIFICATION-INBOX`, `NOTIFICATION-DETAIL`, and `NOTIFICATION-SETTINGS`, with Home/Me entry, source-aware return, Inbox read/archive behavior, owning-domain status/action separation, and preference handoffs;
- the archive family keeps `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST` active and Payer-accessible with ordinary parent-route return, while provisionally retained `ARCHIVED-DOCS-LIST` has no active entry, action or return contract and retired mixed-role Archive/Restore identifiers remain non-active documentation lineage only; Archive is a same-source visibility projection, DOC-10 payout/reconciliation blockers and DOC-11 refund/dispute/chargeback/case blockers remain effective, and detailed Restore/prior-version/Evidence-version behavior remains deferred to DOC-06B/DOC-06C with DOC-12/DOC-15/DOC-18 handoffs;
- immediate pay-now consumes the owner-governed source/Evidence preservation eligibility outcome before Checkout; after newly confirmed Payment, an already Saved/current source keeps its projection, while an otherwise unsaved source resolves selected Save to same-ID Saved/current or declined/skipped/dismissed Save to same-ID history-only before Activity/Payment History/Receipt or ordinary safe exit; Payment, Activity and Receipt exist independently of Save but cannot bypass that resolution;
- deliberate Setup consumes the owner-governed source/Evidence preservation eligibility outcome, establishes the same ID and gives it a Saved/current projection before Payment because Setup expresses reuse intent; Saved/current does not imply Evidence acceptance, Payee verification, destination readiness, Payment eligibility or authorization;
- ID establishment alone does not create Saved/current, Saved/Archived or history-only; established-but-unprojected treatment is limited to immediate-pay failure/abandonment before confirmed Payment or deliberate Setup ending before Saved/current projection, with applicable payment-lifecycle continuation/recovery owned by DOC-09, retention requirements owned by DOC-15 and approved data/technical lifecycle representation owned by DOC-18;
- every Payment remains tied to an acceptable controlled Bill or Rent context; Bills consume the accepted Tier 1/2/3 Evidence treatment, Rent retains mandatory attached Evidence accepted before Payment, and Evidence status remains only one DOC-12-owned input to the combined DOC-09/DOC-10/DOC-14 readiness outcome;
- pending, correction, mismatch and scoped Admin-review Evidence provenance can be retained under the same source ID without claiming accepted Evidence, destination readiness, risk clearance, payer authorization or Payment;
- a label-only Company/Individual disagreement may create asynchronous/non-user-facing Admin review and does not block otherwise eligible payment when all applicable concrete owner-controlled gates pass; concrete Evidence, intended-Payee, destination, beneficiary/agent, Category, sanctions, fraud, anti-cashout, payout, readiness or authorization defects may block their applicable stage;
- Payer selection, AI-apparent assessment, Payer response and scoped Admin determination remain non-overwriting provenance, and `Reviewed` and `Resolved` remain separate dimensions;
- no DOC-06 family provision grants generic Admin access, queue, action, disposition or override authority; each handoff consumes applicable specialist-owner policy/outcomes and leaves DOC-22 only permitted execution;
- institution/company and unresolved or insufficient Individual determination make notification unavailable; governed Individual determination plus Payer choice may expose only the optional one-way informational capability, and delivery failure, suppression or opt-out does not change Payment state or outcome;
- notification does not create Request, Linking, acceptance, consent proof, invitation, reciprocal visibility, payment authorization or a payment-review route/status;
- no Save-from-Activity or Unsave action exists, and active Requests, `BILLS-LINKING`, `BILLS-RECEIVE` and Consumer Payee routes are retired with no runtime historical reader, adapter or fallback;
- the twelve accepted launch Bill Categories are consumed from DOC-05, Rent remains separate, and Category-specific eligibility, Evidence criteria, detailed labels and Directory contents remain explicitly owner-backed deferrals;
- detailed DOC-20 testing/UAT and DOC-21 operations/support evidence is mandatory Wave 5 work, while Route Register, status-display, requirements-traceability, open-question and governed-diagram alignment is mandatory Wave 6 work; neither is claimed or mutated here;
- existing product decisions are preserved in parent or child docs;
- prohibited PayPlus journey boundaries remain visible;
- cross-document owners remain clear;
- traceability/index references point to the DOC-06 family rather than only the parent DOC-06 file.

---

## 12. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 1.1.0 | 2026-08-22 | Aligned the family summary to the approved Tier 3 current-context and deliberate-resolver return, Tier 2 Payment/Evidence/Payout separation, proportionate Declaration, and unchanged Rent negative control without creating routes, statuses, notifications, mechanisms, or enablement. |
| 1.0.1 | 2026-08-21 | Aligned family status and handoffs with the reviewed DOC-19 security-control contract while preserving route, authorization, privacy, provider and representation ownership and open implementation mechanisms. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 0.22.1 | 2026-08-12 | Applied the Founder-settled indefinite-retention boundary to reminder wording without introducing a deletion or disposition mechanism. |
| 0.22.0 | 2026-08-12 | Stage 8 Wave 2 Draft: aligned the family to the accepted twelve-category Payer-only model, removed nonexistent Request-runtime/deep-link obligations, preserved source/Save/Archive and specialist-owner boundaries, and recorded mandatory Wave 5 acceptance/operations and Wave 6 derived-artifact handoffs. |
| v0.21.34 | 2026-08-06 | Aligned the DOC-06 parent with the reviewed `HOME-ROOT` Greeting, Important Notice, Home Hot Offer, Upcoming Bills / Rent, Recent Activity, resilience, accessibility, and presentation-governance baseline while preserving DOC-06B route ownership, source-owner meaning, Partially Defined status, and pending visual, Copy, technical, and DOC-20 evidence. |
| v0.21.33 | 2026-08-05 | Updated the active `PAYMENT-CHECKOUT` family status to Defined baseline under the route-register criterion while preserving DOC-06B/DOC-09 ownership and all pending exact-content, visual, technical, prototype, validation, implementation, acceptance, and operational evidence. |
| v0.21.32 | 2026-08-03 | Aligned the DOC-06 parent with DOC-06B ownership of `PAYMENT-CHECKOUT` route-level adaptive UI/UX and DOC-09 ownership of Payment Domain architecture and authoritative payment meaning, without duplicating the detailed Checkout contract. |
| v0.21.31 | 2026-07-31 | Aligned the DOC-06 family map and Request terminology with DOC-09 Payment Domain Architecture and separated Payment Instruction from incomplete Checkout continuation without redefining route UX. |
| v0.21.30 | 2026-07-29 | Synchronized the DOC-06 family with the capability-aware Outcome-to-Resolution framework and the decision-complete `AUTH-RECOVERY` product baseline without changing existing authentication routes or statuses. |
| v0.21.29 | 2026-07-28 | Synchronized the DOC-06 parent with the completed human-readable Phone Verification, five-state Identity Verification, and Payment Passcode Set/Change/Reset baselines while retaining provider/security/test detail with DOC-17/DOC-19/DOC-20/DOC-22. |
| v0.21.28 | 2026-07-28 | Synchronized the parent with all three Account Activation child routes, the first-time identity-verification passcode exception, and the still-pending detailed verification/passcode screens and DOC-19/DOC-20 handoffs. |
| v0.21.27 | 2026-07-28 | Synchronized the DOC-06 family with the defined Entrance, Fast/Full Login, Recovery, registration-attempt, restricted-account, Account Activation, and authentication outcome/message handoffs. |
| v0.21.26 | 2026-07-27 | Synchronized the parent with the unique-primary-email and explicit multiple-login-method model, restricted account creation, deferred financial activation, and Account Security Set/Change Password and provider-linking behavior. |
| v0.21.25 | 2026-07-27 | Synchronized the parent with the defined Notifications route family, Home/Me entries, Inbox/Detail/Settings behavior, signal separation, contextual handoffs, and remaining visual/provider scope. |
| v0.21.24 | 2026-07-27 | Synchronized the parent with defined `MORE-ROOT` modes, shortcut capacity, protected More access, account-level preference override, current-default restore, availability precedence, accessibility, and secondary-service handoffs. |
| v0.21.23 | 2026-07-27 | Synchronized the parent with the defined Pay+ five-action behavior, payee-to-payer Request Payment direction, contextual payer-linking boundary, category-scoped Bills handoff, instruction-count routing, and remaining visual-design scope. |
| v0.21.22 | 2026-07-26 | Synchronized the parent with defined Archive-family behavior, personal archive projection, archived-detail reuse, eligibility/blocker and restore rules, and obligation/evidence separation. |
| v0.21.21 | 2026-07-26 | Synchronized the parent with the `ARCHIVED-ROOT` family, defined Archived Documents behavior, archived-obligation handoff, and accepted evidence replacement/archive/restore rules. |
| v0.21.20 | 2026-07-26 | Synchronized the parent with assigned authentication, Home, Pay+, More, Notification Inbox, and Payment Checkout destination IDs and the pre-login Login/Register handoff baseline. |
| v0.21.19 | 2026-07-26 | Synchronized the parent with the accepted canonical request lifecycle and the separation of role labels, request events, evidence, obligation readiness, linked cases, payment, and archive visibility. |
| v0.21.18 | 2026-07-26 | Synchronized the parent with current child-route progress, confirmed the 6-card MVP maximum, removed request/evidence events from Bills Activity, clarified evidence-request-obligation relationships, aligned sensitive reveal/change controls, and recorded the request-lifecycle alignment decision as open. |
| v0.21.17 | 2026-07-23 | Aligned the parent UX map with the `RECEIVING-INFO` route family, multiple private profiles, list/detail/setup behavior, destination snapshots, linked-payee notification, and authorization freeze. |
| v0.21.16 | 2026-07-22 | Aligned the parent UX map with defined Account Information, reusable Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, contact-change, verification-status, closure, trusted-device, privacy-request, and export behavior. |
| v0.21.15 | 2026-07-22 | Aligned the parent UX map with permanent `ME-ROOT`, fixed account-control sections, passcode-gated sensitive reveal, Receiving Details, Archived Documents, established-route handoffs, logout, and the separate More shortcut-management boundary. |
| v0.21.14 | 2026-07-21 | Aligned the parent UX map with defined My Rewards Active/History behavior, full reward detail/T&C, and DOC-09 checkout-owned reward selection after payment-card/profile choice. |
| v0.21.13 | 2026-07-21 | Aligned the parent UX map with role-sensitive Referral Rewards child-screen behavior, two list tabs, detail-first claiming, and canonical issued-reward handoff. |
| v0.21.12 | 2026-07-21 | Aligned the parent UX map with the defined Referral route family, registration-attribution handoff, reusable sharing, qualification display, referrer entitlement claiming, and canonical issued-reward handoff. |
| v0.21.11 | 2026-07-20 | Aligned the parent UX map with the defined Offers child-list baseline, multi-collection membership, root duplicate suppression, stable ordering, and DOC-09 same-screen payment-card/profile and promotion-selection ownership. |
| v0.21.10 | 2026-07-17 | Aligned the parent route matrix with stable Offers destination names, child-list screens, full-screen offer/reward detail destinations, separate `REWARDS-ROOT`, partial `REFERRAL-ROOT`, and external `BILLS-PAY` handoff. |
| v0.21.9 | 2026-07-14 | Aligned DOC-06B route-level UX ownership and the parent route status with `RECEIPTS-ROOT` search/list behavior, minimal PDF preview/direct-download behavior, and direct Activity-context proof download. |
| v0.21.8 | 2026-07-13 | Aligned parent DOC-06 with DOC-06B Activity root/detail behavior, including accounting-style entries, expandable activity cards, and separate Activity versus Receipts & Statements ownership. |
| v0.21.7 | 2026-07-08 | Aligned parent DOC-06 route status with DOC-06B Activity and Receipts & Statements route shells and clarified separation from contextual DOC-06C Bills activity. |
| v0.21.6 | 2026-07-06 | Updated parent DOC-06 route matrix and decision summary to recognize DOC-06B `PAYMENT-PROFILE-ROOT` as the payment profile route shell while keeping checkout and tokenization detail in DOC-09/DOC-19. |
| v0.21.5 | 2026-07-02 | Aligned parent DOC-06 scope and role wording with DOC-06B `REQUESTS-NEW` and the simplified request accept/reject route model. |
| v0.21.4 | 2026-06-25 | Updated Requests status to reflect DOC-06B route shell baseline while leaving lifecycle, Bills/rent implementation, and notification behavior in owning documents. |
| v0.21.3 | 2026-06-25 | Clarified that Requests connect parties to accepted obligation contexts and do not equal payment processing. |
| v0.21.2 | 2026-06-25 | Added single-owner drafting rule and clarified route matrix primary owners versus reference or handoff documents. |
| v0.21.1 | 2026-06-25 | Cleaned DOC-06 family publication wording and added compact MVP scope, role, and UX surface summaries so the parent remains understandable after modularization. |
| v0.21 | 2026-06-25 | Split DOC-06 into parent DOC-06 plus DOC-06A to DOC-06D child documents, added family governance map, route completion matrix, ownership boundaries, and preserved prior decisions through child documents. |
