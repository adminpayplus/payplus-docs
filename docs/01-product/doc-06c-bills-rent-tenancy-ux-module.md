---
document_id: DOC-06C
title: Bills, Rent & Tenancy UX Module
version: 1.0.0
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
last_updated: 2026-08-18
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
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
  - DOC-21 Monitoring, Incident Response & Operational SOPs
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06C - Bills, Rent & Tenancy UX Module

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06C` |
| **Title** | Bills, Rent & Tenancy UX Module |
| **Version** | `1.0.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-18` |
| **Classification** | Internal |
| **Related Documents** | DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT & Release Readiness<br>DOC-21 Monitoring, Incident Response & Operational SOPs<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## Current Wave 2 Payer-only Bills/Rent UX Baseline

This is the current normative DOC-06C Founder Working Baseline. Active sections define Payer-only Bills/Rent UX, the Bills-only tiered Evidence/Declaration/Payment journey, Category-bound acquisition, the unchanged separate Rent model, same-ID Save/current/Archived projections, and specialist handoffs. Retired identifiers appear only in concise non-active documentation registers; no obsolete route, runtime reader, action or workflow is active. Stable IDs and append-only history remain preserved. No Route Register or route-status change is made here.

### Source identity and purpose timing

- Opening Pay a Bill/Rent or Setup a Bill/Rent creates temporary pre-validation capture/session state only; it does not establish a durable authoritative Bill/Rent ID.
- ID establishment consumes an owner-governed source-preservation eligibility outcome. DOC-06C defines the journey boundary and does not define the technical persistence threshold or minimum fields. The ID exists before Save/current projection, Payable Basis or Payment Obligation materialization, or a payment-facing handoff requires it. Pending Evidence, mismatch or scoped Admin review does not automatically prevent ID establishment once the outcome permits it. ID establishment alone does not imply accepted Evidence, verified Payee, destination/Payout readiness, risk clearance, Payment Obligation or Checkout readiness, Declaration, payer authorization, successful Payment, Save or current/Archived/history-only projection.
- Immediate pay-now never asks for Save before Checkout. After confirmed Payment with its separate Payment ID linked to the source, show Payment Result. A source already Saved/current before Payment keeps that projection without duplicate Save. For an otherwise unsaved source, selected Save makes the same ID Saved/current; declined, skipped, dismissed, closed or otherwise abandoned Save resolution makes it history-only before Activity, Payment History, Receipt or ordinary safe exit.
- Deliberate Save establishes persistence, visibility and reuse intent on the same source ID without Payment. Saved/current does not mean Evidence accepted, ready, approved or authorized. A later Payment is created only under current owner checks and separate DOC-09 payer authorization.
- Failure or abandonment after ID establishment may leave the source unprojected only when immediate pay ends before confirmed Payment or deliberate setup ends before Save/current projection. It creates no Bills/Rent entry or user-facing incomplete-source status. A newly confirmed Payment for an otherwise unsaved source must resolve to Saved/current or history-only before downstream handoff.

### Controlled Bill journeys

1. Select one of the twelve Founder-confirmed launch controlled Bill Categories in DOC-05 first. The inventory is accepted; Category-specific eligibility, Evidence criteria, detailed labels, Directory contents and Copy remain with their named owners and are not inferred here.
2. Use either the Category-scoped Directory (institutional Payee discovery/pre-trust only) or Provide Payee myself. Neither method is unrestricted and self-provided never bypasses Category or substantive owner controls.
3. Directory unpublication stops new discovery only; it does not hide, disable, rename or invalidate a saved Bill/Rent source or correct Payee/payment facts. Category disassociation, programme/risk suspension, invalid destination, fraud, sanctions, legal prohibition and security compromise remain separate substantive restrictions that apply across both acquisition methods.
4. Retain bounded acquisition provenance (Directory-selected or Self-provided, stable institution/Directory reference if one already exists, acquisition Category, timestamp and relevant lineage reference) for audit/troubleshooting only; it does not govern live eligibility, visibility or commercial authority.
5. For self-provided Bills, the Payer selects Company or Individual before Evidence. DOC-12 then recognizes Evidence and may derive an apparent type; only after that recognition may a mismatch prompt appear. Preserve the Payer choice, AI-apparent assessment, Payer accept/decline response and scoped Admin determination without overwriting provenance.
6. At Pay progression, consume current C1/G1/G2 and highest-tier outcome. Tier 1 requires Declaration but no attached Evidence; Tier 2 requires qualifying official Bill Evidence presence before Payment; Tier 3 requires Evidence and authorized approval before executable Payment. DOC-12/09/10/14 retain their respective Evidence, Payment, Payout and risk ownership.

### Separate Rent journey

Rent is independent of the controlled-Bill Directory and the Bill tiers. A Payer does not select a Bill Category or choose Directory versus Provide Payee myself for Rent. Rent always requires attached Evidence and the required Evidence acceptance before Payment. A Rent-specific Declaration cannot replace, waive, reduce or defer Evidence. Tenancy context and applicable accepted Evidence may be reused until expiry, replacement or material change requires renewed Evidence treatment. Destination, risk, readiness, period-specific obligation facts and fresh payer authorization remain Payment-specific.

### Save, visibility, Activity and Archive

- Save establishes persistence, visibility and reuse intent on the same authoritative source ID. A Saved/current Bill appears in the active/current list and may be Under Review, Action Required or Ready; those are handling/readiness conditions, not projections.
- A confirmed Payment for an otherwise unsaved source followed by declined, skipped, dismissed, closed or otherwise abandoned Save resolution makes that same ID history-only. It is neither Saved/current nor Saved/Archived and has no Bills/Rent UI entry. A source already Saved/current before Payment keeps its projection without duplicate Save. The Payment remains visible in global Activity, Payment History and Receipt.
- Post-payment Save gives the existing source the Saved/current projection; it creates no second source and moves/recreates no Payment lineage.
- Archive moves a Saved/current source into the Saved/Archived projection and governed Archived Bills presentation. Archived sources do not appear in the active/current list. Archive is not a readiness or financial status and never erases or rewrites Evidence, financial history, destination/payment snapshots, Payout, reconciliation or audit lineage.
- ARCHIVED-DOCS-LIST remains provisionally retained under the Founder-approved W2-FD-05 decision (Option A); this does not change route status. Exact Restore eligibility, revalidation, prior-version/Evidence-version/replacement-source presentation and detailed Archive/Restore UI remain deferred to DOC-06B/DOC-06C with DOC-10 payout/reconciliation blockers, DOC-11 refund/dispute/chargeback/case blockers and DOC-12/DOC-15/DOC-18 Evidence, privacy/retention and data/lineage handoffs.

### Active retirement and notification handoff

Active Request, BILLS-LINKING, BILLS-RECEIVE, Remind Payer, Payee-user and Consumer Receiving Info behavior is retired. Retired stable IDs and prior meanings remain non-active documentation evidence only. Founder confirmation establishes that no production Request/Payee-role runtime or legacy Request deep-link data exists; no runtime reader, adapter, fallback, dormant runtime or replacement Request product is created.

The optional one-way Payee notification is available only where the Payee is eligible under the governed Individual-Payee classification/determination policy. DOC-06C consumes this outcome and does not independently determine Payee type or make an Admin determination. Institution/company and unresolved/insufficient Individual determination leave notification unavailable. A governed Individual determination plus Payer choice may expose the informational one-way capability. Payer contact responsibility does not remove PayPlus obligations for lawful purpose, data minimization, wrong-recipient prevention, abuse/rate-limit controls, suppression/opt-out, security, delivery records, retention and support. The capability is not Request, Linking, acceptance, consent proof, invitation, reciprocal visibility, payment authorization or a payment-state change. DOC-05 owns only the eligibility boundary; DOC-07 owns approved Copy/disclosure/CTA; DOC-08 owns notification identity/channel/template/preference/delivery; DOC-14 owns risk/abuse; DOC-15 owns privacy/retention requirements; DOC-18 represents approved data/audit requirements; DOC-19 owns security; DOC-21 owns support/operations; and DOC-22 performs only permitted Admin execution. DOC-12 supplies any Evidence-derived classification input but does not own notification delivery. Contact provenance and lawful-basis or consent treatment remain with their applicable formal owners.

---

## Active Normative Baseline

The route and detail sections below are active current requirements for the Payer-only Bills/Rent UX. Retired BILLS-RECEIVE, Request, Linking, Receive and Payee-user identifiers appear only in concise non-active documentation registers or append-only Version History; they create no runtime reader or current product behavior.

## 1. Purpose

DOC-06C governs the PayPlus Payer-facing Bills, rent, tenancy, fee, obligation, reminder, activity and evidence UX module.

It is the owning document for the Payer-facing BILLS-ROOT/BILLS-PAY, BILLS-ACTIVITY, BILLS-ACTIVITY-DETAIL, BILLS-ADD, BILLS-EVIDENCE-DETAIL, BILLS-EVIDENCE-UPLOAD, BILLS-REMINDER-LIST, BILLS-REMINDER-DETAIL, and ARCHIVED-BILLS-LIST human-readable UX. BILLS-RECEIVE and BILLS-LINKING remain only as retired stable IDs in non-active documentation; they are not routes or runtime readers.

## 2. Scope Boundary

DOC-06C owns the user-facing Payer Bills module route behavior, card/detail actions, evidence sub-flow, reminder management, activity timeline, archived-source visibility boundary and route handoffs.

DOC-06C does not own detailed checkout/payment processing, evidence verification algorithms, final data schema, final event taxonomy, privacy masking rules, notification templates, risk thresholds, or admin queue design. Those remain with DOC-08, DOC-09, DOC-12, DOC-14, DOC-15, DOC-18, DOC-19, and DOC-22 as applicable.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| BILLS-PAY payer-side route | Working baseline | Card/detail actions defined; final visual UI remains open. |
| BILLS-RECEIVE retired ID | Retired active MVP | Stable ID remains non-active documentation lineage only; no Consumer Payee route, runtime reader or Request/Remind Payer behavior. |
| Bill/rent cards and details | Working baseline | Field set defined; final density, masking, and visual hierarchy remain open. |
| Activity sub-route | Working baseline | Payment activity and limited milestones defined; global Activity and Receipts & Statements routes remain separate under DOC-06B. |
| Add Bill / Rent flow | Working baseline | Add Bill C1-only Save admission, optional Bill Evidence assistance, separate mandatory-Evidence Rent, Declaration and Pay-time Tier handoff are defined; exact Copy and visual composition remain open. |
| Evidence sub-route | Working baseline | Evidence detail/upload behavior and status mapping defined; data model remains DOC-18. |
| Archived Bills & Rent | Working baseline / Payer-only re-scope | Saved-source visibility projection and non-erasure are current; exact Restore, evidence-version and prior-version behavior remains deferred. |
| Reminder list/detail route | Working baseline | Linked reminders, defaults, custom override, toggle, and non-destructive deactivation defined; payment-instruction action alerts remain outside Bills reminder management. |
| User-to-user Linking | Retired active MVP | Retired stable ID and neutral future seams only; no participant Linking flow or runtime reader. |

## 4. Product Destination and Retired-ID Traceability Map

| Product Destination ID | Legacy DOC-06C Traceability Alias |
| --- | --- |
| BILLS-ROOT | ROUTE-06C-BILLS-ROOT |
| BILLS-PAY | ROUTE-06C-BILLS-PAY |
| BILLS-RECEIVE | ROUTE-06C-BILLS-RECEIVE |
| BILLS-ACTIVITY | ROUTE-06C-BILLS-ACTIVITY |
| BILLS-ACTIVITY-DETAIL | ROUTE-06C-BILLS-ACTIVITY-DETAIL |
| BILLS-ADD | ROUTE-06C-BILLS-ADD |
| BILLS-EVIDENCE-DETAIL | ROUTE-06C-BILLS-EVIDENCE-DETAIL |
| BILLS-EVIDENCE-UPLOAD | ROUTE-06C-BILLS-EVIDENCE-UPLOAD |
| BILLS-REMINDER-LIST | ROUTE-06C-BILLS-REMINDER-LIST |
| BILLS-REMINDER-DETAIL | ROUTE-06C-BILLS-REMINDER-DETAIL |
| ARCHIVED-BILLS-LIST | N/A - stable destination added after modularization |

The product destination IDs in the first column are stable references for human documents, diagrams, and later AI build-execution conversion; current active treatment is governed by the normative route sections below. `BILLS-RECEIVE` is a retired stable ID in append-only documentation history only and is not made active by this map. The DOC-06C-prefixed aliases are retained only as traceability references and must not replace the product destination names or be extended as a separate route taxonomy.

---

## 5. Bills, Rent & Tenancy UX Module Working Baseline

This section defines the working baseline for the `Bills` bottom-navigation route. It is a route-level UX and behavior specification, not a final visual UI design.

Route-level UI specification rule: each route should define user-facing behavior and identify material events/data signals required for AI-ready data-engine support. Detailed schema, event taxonomy, lineage, model registry, and warehouse design remain owned by DOC-18.

### 5.1 Route and Subsection IDs

The active route table contains only current Payer routes, views and components. Retired BILLS-RECEIVE, Request, Remind Payer, Linking and Consumer Payee identifiers are preserved separately in the non-active documentation register in Section 5.14 and do not define routes, actions or runtime readers.

For DOC-06, a route ID may represent a full screen, tab/view, modal/sheet, section, or reusable card component. The type should be stated so later AI build documents do not duplicate screens or confuse components with navigation destinations.

Route ID naming standard:

- use uppercase, hyphen-separated IDs;
- use the pattern `[AREA]-[PRIMARY-ROUTE]-[SUBROUTE-OR-COMPONENT]` where a sub-route or component is needed;
- use a primary route ID for a broad product area or flow group, such as `BILLS-EVIDENCE`;
- add a sub-route ID only when the user task, screen/sheet, permission model, route destination, or implementation ownership is materially different;
- use the specific sub-route ID in AI build documents, notification destinations, analytics events, and implementation tasks where one exists;
- keep broad route IDs as shorthand discussion labels only when a more specific sub-route ID has been defined.

Examples include `BILLS-ROOT`, `BILLS-PAY`, `BILLS-DETAIL-BILL`, `BILLS-REMINDER-LIST`, and `BILLS-EVIDENCE-UPLOAD`.

| ID | Type | Route / Section | Opened By | Definition |
| --- | --- | --- | --- | --- |
| `BILLS-ROOT` | Screen | Bills route | Bottom nav `Bills` | Top-level Bills tab screen. |
| `BILLS-PAY` | Tab / view | Payer Bills view | `BILLS-ROOT`, Pay+ `Pay a Bill`, Pay+ `Pay Rent`, dashboard items, reminders, or action-required notifications | Payer-oriented selection and management route for Saved/current Bill/Rent sources. It may include Under Review, Action Required and Ready handling conditions but excludes Saved/Archived and history-only sources. Pay+ may open a temporary Bill or Rent selection scope without changing saved Bills filters. It is not Checkout. |
| `BILLS-CARD-BILL` | Card component | Bill / fee card | Rendered inside `BILLS-PAY` | Summary card for a controlled Bill, invoice or fee source. |
| `BILLS-CARD-RENT` | Card component | Rent / tenancy card | Rendered inside `BILLS-PAY` | Summary card for a Rent or tenancy-linked source. |
| `BILLS-DETAIL-BILL` | Screen | Bill / fee detail | `Details` on `BILLS-CARD-BILL` | Detail page for the selected controlled Bill, invoice or fee source. |
| `BILLS-DETAIL-RENT` | Screen | Rent / tenancy detail | `Details` on `BILLS-CARD-RENT` | Detail page for rent record and linked tenancy context. |
| `BILLS-ACTIVITY` | Sub-route / screen or sheet | Bill/rent activity timeline | `View Activities` from bill/rent detail pages | User-facing payment, payout/transfer, failure, return, refund, and reversal activity for one selected bill/rent record. This is not request history, evidence management, global history, or an internal audit log. |
| `BILLS-ACTIVITY-DETAIL` | Sub-route / screen or sheet | Activity entry detail | Tapping one entry in `BILLS-ACTIVITY` | Detail view for one selected payment/activity entry, with reference number, receipt/proof access, and optional link to the payment detail route where needed. |
| `BILLS-ADD` | Flow / screen group | Add Bill / Rent flow | `Add Bill / Rent` button or Pay+ action sheet | Setup flow for a new controlled Bill source or separate Rent/tenancy source. |
| `BILLS-EVIDENCE` | Sub-flow group / shorthand | Evidence sub-flow | Detail-page evidence area, `BILLS-ADD`, or evidence action-required state | Shorthand for bill/rent evidence actions. Evidence is a supporting attachment/status layer of a bill/rent record, not a standalone user object. |
| `BILLS-EVIDENCE-DETAIL` | Screen or sheet | Evidence detail | Evidence section inside `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT` | View and manage the current active evidence set for one bill/rent record. |
| `BILLS-EVIDENCE-UPLOAD` | Flow / screen group | Evidence upload/update | `Upload` or `Update` from evidence detail, or Evidence step inside `BILLS-ADD` | Upload file, take photo or scan QR; supports OCR/autofill and user correction. Manual Tier 1 Bill facts remain source input in `BILLS-ADD` and are not attached Evidence. |
| `BILLS-REMINDER-LIST` | Screen | Reminder management | Dashboard shortcut `Reminders` | Alarm-style reminder management screen for reminders linked to a Bill/Rent source or an applicable owner-governed obligation reference. |
| `BILLS-REMINDER-DETAIL` | Sheet or screen | Reminder setup/edit | `Set Reminder`, `Edit Reminder`, or `+ Add Reminder` | Create or edit one reminder linked to a specific Bill/Rent source or applicable owner-governed obligation reference without treating their identities as interchangeable. |

Initial route ownership:

| User Action | Source | Destination / Behavior |
| --- | --- | --- |
| Tap `Bills` bottom nav | App bottom navigation | Opens `BILLS-ROOT` with the Payer `BILLS-PAY` view. |
| Tap `To Pay` | `BILLS-ROOT` | Retained only as a compatible label/reference for `BILLS-PAY`; no mixed-role tab pair is active. |
| Tap `Pay a Bill` / `Pay Rent` | `PAYPLUS-ACTION-SHEET` | `Pay a Bill` opens a temporary controlled Bill selection/input scope and evaluates current C1/G1/G2 before the DOC-09 Checkout handoff. `Pay Rent` opens the separate Rent/tenancy scope and retains mandatory accepted Evidence before Payment. A permitted selection continues to the applicable Checkout or owner-approved resolution; no new route is created. |
| Tap `Add Bill / Rent` | `BILLS-ROOT` or Pay+ action sheet | Opens `BILLS-ADD`. Add a Bill applies C1 only before Save; Add Rent follows the separate mandatory-Evidence journey. G1/G2 do not apply or reserve capacity in Add. No active Request-origin return is created. |
| Tap `Pay` on a payer-side card/detail | `BILLS-PAY`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Opens payment/checkout flow governed by DOC-09. DOC-06C owns the entry point and route handoff only. |
| Tap `Details` | Bill/rent card | Opens the relevant detail screen. |
| Tap `Set Reminder` / `Edit Reminder` | Bill/rent card or detail page | Opens `BILLS-REMINDER-DETAIL` for the selected linked record. |
| Tap `Reminders` shortcut | Dashboard shortcut grid | Opens `BILLS-REMINDER-LIST`. |
| Tap `+ Add Reminder` | `BILLS-REMINDER-LIST` | Payer selects an existing Bill/Rent source context, then opens `BILLS-REMINDER-DETAIL`; any linked Payment Obligation reference remains distinct and owner-governed. |
| Tap `View Activities` | Detail page | Opens `BILLS-ACTIVITY`. |
| Tap one activity entry | `BILLS-ACTIVITY` | Opens `BILLS-ACTIVITY-DETAIL` or a later payment detail route if separately defined. |
| Tap contextual `View` evidence action | Evidence status area inside bill/rent detail page | Opens `BILLS-EVIDENCE-DETAIL` for the selected bill/rent record. |
| Tap `Upload` / `Update` evidence | `BILLS-EVIDENCE-DETAIL` or evidence step in `BILLS-ADD` | Opens `BILLS-EVIDENCE-UPLOAD`. |
| Tap evidence action-required prompt | Bill/rent detail page | Opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD` depending on whether evidence exists. |
| Tap `Archive` | Detail page for a Saved/current source | Applies ordinary Archive to the same authoritative Bill/Rent source, removes its current-list projection, and returns to the current Bills/Rent list. The same source remains Payer-accessible through `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST`; Archive does not erase or rewrite Evidence, Payment, destination, Payout, reconciliation or audit lineage. Exact eligibility, Restore and version behavior remains deferred. |

Payment/checkout ownership rule:

- DOC-06C owns the user-facing entry point, route handoff, back/return behavior expectation, and the fact that payer-side `Pay` opens checkout.
- DOC-06B owns the reviewed global `PAYMENT-CHECKOUT` route-level adaptive Workspace UI/UX, including presentation, entry, return, and handoff behavior. DOC-09 owns the underlying Payment Domain architecture and business invariants, including Payment Obligations, Checkout Workspace, monetary and funding allocations, Provider Submission, confirmed Payments, Payment Applications, deliberate Payment Instructions, and incomplete Checkout continuation. DOC-06B `PAYMENT-PROFILE-ROOT` owns reusable card/profile management when Checkout or instruction flows need a card/profile management handoff. DOC-06C continues to own Bill/Rent selection, payer-side `Pay` entry, source facts, consumption of the combined owner-controlled readiness presentation, contextual treatment, and source-aware return behavior; it does not own Checkout composition or payment-domain meaning.
- DOC-07 owns required user-facing wording and disclosures; DOC-08 owns checkout-related notifications and receipts; DOC-13 owns promotion/coupon/voucher checkout treatment; DOC-15 owns masking and data visibility; DOC-19 owns authentication/security controls; DOC-18 owns route events and data signals.

Standalone `BILLS-ADD` started from Pay+ hands to the applicable Payer success or payment context under DOC-09. It does not create a Request-origin return; exact incomplete-source treatment remains with DOC-09/DOC-15/DOC-18.

### 5.2 Top-Level Payer Views

The current Payer Bills area uses the stable `BILLS-PAY` destination. The former `To Pay` / `To Receive` role-tab pair is not active Wave 2 presentation. No replacement tab or route is invented. A no-Save source is not shown in the active Bills list, and a Saved/Archived source appears only in the governed Archived Bills presentation.

| View | User Meaning | Includes | Does Not Include |
| --- | --- | --- | --- |
| `BILLS-PAY` | Payer-visible Saved/current Bill/Rent sources. | Saved/current controlled Bills/Rent, including Under Review, Action Required and Ready handling conditions, source details, Evidence handoff, Payment entry, reminders, Activity and Archive handoffs. | Saved/Archived, history-only, Consumer Payee, Request, Linking or payout-management routes. |

Request and Payee-user concepts are not active Bills views. Retired IDs and prior meanings remain append-only documentation history only; no production runtime records or readers exist.

`BILLS-PAY` renders Payer-only bill/rent card types. `BILLS-RECEIVE` is retired from active MVP and is not a second role tab.

| Context | Governed User Intent | Primary Actions |
| --- | --- | --- |
| `BILLS-PAY` | User is acting as Payer. | Select supported Category, Directory/self-provided acquisition, view details, deliberately Setup for reuse where offered, Pay, Activity, Set Reminder, Archive. Immediate pay has no pre-Checkout Save; optional Save for an otherwise unsaved source is resolved only after Payment Result, and Activity never offers Save. |

The detail route may remain `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT`, with visible actions determined by the active Payer source context. `BILLS-RECEIVE` has no active entry or action and is preserved only as a retired stable ID in Section 5.14.

### 5.3 Filters

| View | MVP Filters | Rule |
| --- | --- | --- |
| `BILLS-PAY` | All, Action Required, Due Soon, Paid | Archived records are excluded and belong to `ARCHIVED-BILLS-LIST`; no mixed-role filter is active. |

Action-required items should be visible through a filter and through status badges on the relevant card.

### 5.4 Bill / Fee Card

`BILLS-CARD-BILL` should show the minimum information needed for quick recognition and action:

- controlled Bill Category and source type, such as Bill, Fee or Invoice;
- bill name, required;
- latest amount;
- next due date;
- last payment date;
- payment readiness or status badge.

Payer-side card actions when rendered in `BILLS-PAY`:

| Action | Route / Behavior |
| --- | --- |
| Pay | Opens payment/Checkout handoff for the selected Bill source; DOC-09 owns any applicable Payable Basis, Payment Obligation, eligibility and authorization rules. |
| View Details | Opens `BILLS-DETAIL-BILL`. |
| Set Reminder | Opens `BILLS-REMINDER-DETAIL` for this Bill source or an applicable owner-governed obligation reference without treating their identities as interchangeable. |
| Update Detail | Replaces normal edit/detail prompt when the card is action-required due to required Evidence or other owner-governed information being rejected, missing, expired or inconsistent. Tier 1 Evidence absence alone is not Action Required. |

Former Payee-side card actions remain append-only documentation history only; no BILLS-RECEIVE action or runtime reader is available.


### Non-Active Documentation Register - Retired Payee-Side Card Action IDs

| Retired documentation evidence | Preservation location | Current treatment |
| --- | --- | --- |
| Former BILLS-RECEIVE card/action IDs and prior actor-role meanings | Append-only documentation history | Retired Consumer Payee, Request and Remind Payer behavior; no runtime reader or replacement action |



### 5.5 Bill / Fee Detail Page

`BILLS-DETAIL-BILL` should show:

- category;
- bill name, required;
- payee information and payout/account information, masked where required;
- latest amount;
- next due date;
- last payment date;
- bill/invoice extracted fields that are approved for display, where applicable;
- evidence status area for the latest bill/invoice support;
- payment readiness or status badge.

Payer-side detail actions when opened from `BILLS-PAY`:

| Action | Route / Behavior |
| --- | --- |
| Pay | Opens payment/checkout flow. |
| View Activities | Opens `BILLS-ACTIVITY` for payment and related payout/refund/reversal activity linked to this Bill source. |
| Set Reminder / Edit Reminder | Opens `BILLS-REMINDER-DETAIL` for this Bill source or an applicable linked obligation without changing their identity. |
| Edit Details | Opens editable bill/payee/detail fields subject to verification and audit rules. |
| Archive | Moves this Saved/current Bill source to the Saved/Archived projection and removes it from the current list without deleting the source or history. Exact eligibility and Restore behavior remain deferred to the applicable owners. |

Former Payee-side detail actions remain append-only documentation history only; no BILLS-RECEIVE action or runtime reader is available.


### Non-Active Documentation Register - Retired Payee-Side Bill Detail IDs

| Retired documentation evidence | Preservation location | Current treatment |
| --- | --- | --- |
| Former BILLS-RECEIVE bill-detail action IDs and prior meanings | Append-only documentation history | Retired behavior; no runtime reader, replacement action or workflow |



The bill detail page should include a `Bill / Invoice` Evidence area where attached Evidence exists or is required; the existing label does not limit DOC-12's qualifying official Bill Evidence types. For Tier 1, absent Evidence must not be presented as Action Required by itself. For Tier 2/3, missing, rejected, expired or otherwise action-required Evidence should expose the applicable contextual action to `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD`. Extracted fields approved for display belong in bill detail rather than being duplicated.

### 5.6 Rent / Tenancy Card

`BILLS-CARD-RENT` should show:

- journey/source type: Rent; no Bill Category applies;
- bill/rent name, required;
- rent amount;
- rent period;
- next due date;
- last payment date;
- payment readiness or status badge.

Payer-side card actions when rendered in `BILLS-PAY`:

| Action | Route / Behavior |
| --- | --- |
| Pay | Opens payment/Checkout handoff for the selected Rent source; DOC-09 owns any applicable Payable Basis, Payment Obligation, eligibility and authorization rules. |
| View Details | Opens `BILLS-DETAIL-RENT`. |
| Set Reminder | Opens `BILLS-REMINDER-DETAIL` for this rent record. |
| Update Detail | Replaces normal edit/detail prompt when the card is action-required. |

Former Payee-side rent-card actions remain append-only documentation history only; no BILLS-RECEIVE action or runtime reader is available.


### Non-Active Documentation Register - Retired Payee-Side Rent Card IDs

| Retired documentation evidence | Preservation location | Current treatment |
| --- | --- | --- |
| Former BILLS-RECEIVE rent-card action IDs and prior actor-role meanings | Append-only documentation history | Retired behavior; no runtime reader, replacement action or workflow |



### 5.7 Rent / Tenancy Detail Page

`BILLS-DETAIL-RENT` should show:

- journey/source type: Rent; no Bill Category applies;
- bill/rent name, required;
- property address, masked or limited where required;
- rent amount;
- rent period;
- last payment amount;
- last payment date;
- next due date;
- landlord/payee information and payout/account information, masked where required;
- rental document extracted fields that are approved for display, where applicable;
- evidence status area for rental documents;
- payment readiness or status badge.

Payer-side detail actions when opened from `BILLS-PAY`:

| Action | Route / Behavior |
| --- | --- |
| Pay | Opens payment/checkout flow. |
| View Activities | Opens `BILLS-ACTIVITY` for payment and related payout/refund/reversal activity linked to this Rent source. |
| Set Reminder / Edit Reminder | Opens `BILLS-REMINDER-DETAIL` for this rent record. |
| Edit Details | Opens editable rent/landlord/payment detail fields subject to verification and audit rules. |
| Archive | Moves this Saved/current Rent source to the Saved/Archived projection and removes it from the current list without deleting the source or history. It does not change Rent Evidence/readiness. Exact eligibility and Restore behavior remain deferred. |

Former Payee-side rent-detail actions remain append-only documentation history only; no BILLS-RECEIVE action or runtime reader is available.


#### 5.7.1 Rent Evidence Presentation

The rent detail page should include a `Rental Doc` evidence status area. `Rental Doc` covers tenancy agreements and other approved rent-supporting evidence, such as rent demand, stamp duty document, CR109, HKHA tenancy card, carpark invoice, or property management notice. It should show current evidence status and extracted rental fields approved for display. Evidence management is not a default primary detail action. If evidence is missing, rejected, expired, or otherwise action-required, the status area should show a contextual action that opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD`. Extracted fields that belong to the rent/tenancy record should be displayed in the rent detail area, not duplicated inside evidence detail.

Rent normally should not require a new invoice for each payment cycle unless tenancy evidence expires, changes, is replaced, is rejected, or is flagged by risk/review rules.

#### 5.7.2 Non-Active Documentation Register - Retired Payee-Side Rent Detail IDs

| Retired documentation evidence | Preservation location | Current treatment |
| --- | --- | --- |
| Former BILLS-RECEIVE rent-detail action IDs and prior actor-role meanings | Append-only documentation history | Retired behavior; no runtime reader, replacement action or workflow |

#### 5.7.3 HOME-ROOT Upcoming Bills / Rent Source Projection

DOC-06C publishes the active payer-role Bill and Rent candidates consumed by the DOC-06B HOME-ROOT `Upcoming Bills / Rent` section. This is a projection of canonical Bill/Rent records, not a Home-owned obligation or status.

Each candidate must supply canonical:

- Bill or Rent type;
- active payer-role eligibility;
- HKD amount for MVP;
- due date and applicable canonical timezone;
- creation timestamp; and
- stable source record ID.

DOC-06C also publishes the canonical card fields and masking treatment, source-route action availability, and the values required for current-state, permission, readiness, and action-availability revalidation before a protected source-route action.

A missing amount or due date is an upstream invariant or retrieval failure. Overdue remains a Bill/Rent business state.

For a Rent reminder, DOC-06C supplies the canonical due timestamp: the effective due date at `23:59` in its canonical timezone. A proposed due-date change does not change this value until applied to the canonical Bill/Rent record.

DOC-06B is the sole normative owner of the HOME-ROOT cap, deterministic ranking and ordering, card presentation, selected Home actions, Home route and return behavior, additional Home masking prohibition, and Important Notice Rent-reminder eligibility window. DOC-06C publishes the canonical source values and revalidation truth above without restating the Home algorithm.

### 5.8 Bill / Rent Activity Sub-Route

`BILLS-ACTIVITY` is a user-facing sub-route for one selected Saved/current Bill/Rent record. It should be opened from `View Activities` inside the applicable detail screen. It never offers Save and cannot bypass Payment Result projection resolution; a newly confirmed Payment for an otherwise unsaved source reaches global Activity/Payment History/Receipt only after same-ID Saved/current or history-only resolution.

Primary owner: DOC-06C.

Related ownership:

| Area | Owning Document |
| --- | --- |
| Notification and receipt/proof messaging | DOC-08 |
| Global Activity and Receipts & Statements route shells | DOC-06B |
| Payment status and payment-detail linkage | DOC-09 |
| Transfer, payout, and rejected payout status | DOC-10 |
| Returned, refunded, reversed, or chargeback-related transaction outcomes; linked dispute cases remain outside Bills Activity unless they produce a transaction outcome | DOC-11 |
| Evidence approval/rejection meaning | DOC-12 |
| Masking and role-based visibility | DOC-15 |
| Full event, audit, data model, and lineage | DOC-18 |
| Evidence-review history and internal audit representation | DOC-12 for Evidence meaning; DOC-15 for approved-purpose access; DOC-18 for data/audit/lineage representation; DOC-22 for permitted Admin execution |

`BILLS-ACTIVITY` should include:

- payment activity entries;
- transfer or payout outcome where user-relevant;
- failed, returned, refunded, or reversed outcomes where applicable;
- receipt or payment proof access;
- user-facing status mapped from the canonical status-display reference.

`BILLS-ACTIVITY` should not include:

- ordinary bill/rent detail edit history;
- OCR/upload processing logs;
- every evidence status change;
- request workflow or acceptance history;
- internal approval workflow history;
- admin audit trail;
- global transaction history;
- global receipt or statement library;
- Evidence view, update or upload actions, which belong to `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`; exact Evidence archive/version presentation remains deferred to its formal owners;
- payment processing logic, which belongs to DOC-09;
- payout and reconciliation logic, which belongs to DOC-10.

Activity list entries should show:

| Field | Rule |
| --- | --- |
| Payment date | Show clearly and compactly. |
| Recipient / payee name | Normal text prominence. |
| Bill / rent name | Smaller supporting text. |
| Amount | Clear and easy to scan. |
| Status | User-facing status mapped from `docs/traceability/status-display-reference-matrix.md`. |

Bill/rent activity status must not create a separate status vocabulary. User-facing labels should follow the status display reference matrix, with DOC-09, DOC-10, and DOC-11 remaining owners of the underlying payment, payout, refund, reversal, and failure statuses.

Initial payment-lifecycle display mapping:

| Role | Example User-Facing Labels | Owning Detail |
| --- | --- | --- |
| Payer | `Paid`, `Transferred`, `Failed`, `Returned`, `Refunded`, `Reversed`, `Under Review` | DOC-09 / DOC-10 / DOC-11 / DOC-14 own the applicable outcome; DOC-22 executes only owner-permitted Admin handling and does not make `Under Review` apply where a label-only disagreement is nonblocking. DOC-18 owns later status representation. |

Tapping one activity entry should open `BILLS-ACTIVITY-DETAIL` or a later payment detail route if separately defined.

`BILLS-ACTIVITY-DETAIL` should show:

- payment date;
- bill/rent name;
- recipient/payee name;
- amount;
- payment status;
- transfer/payout status where applicable;
- payment reference number, if any;
- receipt/proof direct download where available;
- link to payment detail where needed and separately governed.

`BILLS-ACTIVITY-DETAIL` should not route to global `RECEIPT-DETAIL` by default. The default user action should be direct receipt/proof download because the user is already in the contextual activity detail for one bill/rent. Global receipt and statement browsing belongs to DOC-06B `RECEIPTS-ROOT`.

Activity detail may show system lifecycle milestones, but user-facing labels must follow the status display reference matrix. Do not expose raw backend milestones such as payment authorization, settlement readiness, payout processing, reversal handling, or review queue status as independent user-facing status labels unless mapped and approved.

Former Request lifecycle text is historical only; no active Request lifecycle belongs in `BILLS-ACTIVITY`. `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD` are route surfaces for Payer Evidence presentation and owner-approved action handoff. DOC-12 owns Evidence, extraction, verification and Evidence-to-Payee meaning; DOC-15 owns approved-purpose access and retention governance; DOC-18 represents approved data, status, event, audit and lineage requirements; and DOC-22 performs only specifically owner-permitted Admin execution. Neither Evidence-policy meaning nor Admin execution belongs in `BILLS-ACTIVITY`.

### 5.9 Add Bill / Rent Flow

`BILLS-ADD` is the existing Payer-only setup flow. It supports distinct Bill and Rent branches without creating a new route or combining their Evidence rules.

Add a Bill:

1. Select one of the twelve accepted launch controlled Categories first.
2. Choose the Category-scoped Directory or Provide Payee myself; neither bypasses Category, risk, Payee or destination controls.
3. Capture the Bill source facts and the owner-required Declaration concerning Category, purpose, amount and Payee/receiving details. Declaration is not Save intent or Payment authorization.
4. At initial Bill capture, attached Evidence is optional and may be supplied through `BILLS-EVIDENCE-UPLOAD` for AI/OCR-assisted prefill. Manual source-fact input remains available for Tier 1.
5. Apply C1 only before Save. If the proposed amount exceeds C1, Save is not permitted. G1/G2 do not apply and no monthly capacity is reserved.
6. Consume the owner-governed source-preservation outcome and establish one authoritative Bill ID where permitted. Deliberate Save gives that ID the Saved/current projection without Payment.
7. Save does not establish Evidence acceptance, readiness, approval, Payment authorization or future Tier.

Pay a Bill:

1. Use current Category, purpose, amount, economic-Payee and receiving details; re-evaluate current C1/G1/G2 and retain every trigger reason.
2. No trigger uses Tier 1: Declaration is required, attached Evidence is not, and other owner gates remain.
3. C1 or G1 without G2 uses Tier 2: require qualifying owner-approved official Bill Evidence presence before Payment. Payment may proceed while acceptance remains pending; Payout remains held.
4. G2 uses Tier 3: require qualifying official Bill Evidence and mandatory authorized approval before any executable Payment action.
5. A prepared Tier 3 `PAYMENT-CHECKOUT` Workspace may preserve context, but before approval it exposes no executable Payment authorization, Provider Submission or confirmed Payment. No new route or recovery object is created.
6. After confirmed Payment, retain an existing Saved/current projection without duplicate Save; otherwise resolve optional Save on the same ID to Saved/current or history-only before downstream Activity/Payment History/Receipt or ordinary safe exit.

Declaration continuity:

- unchanged declared facts require no new Declaration;
- C1/G1/G2 re-evaluation alone is not a Declaration trigger; and
- user changes follow owner-defined materiality and proportionate reconfirmation, which may be field-specific, summary-based or full. Every amount edit does not automatically require a full Declaration.

Rent:

- enter the separate tenancy journey without Bill Category, Directory, C1/G1/G2 or Bill tiers;
- require attached Evidence and the required Evidence acceptance before Payment; and
- do not let a Rent-specific Declaration replace, waive, reduce or defer Evidence.

Where a Bill Category permits prepayment, present only the owner-approved period choices and evaluate the selected-period aggregate against C1/G2. One independent user-initiated prepayment progression counts once under G1 despite multiple periods, cards or Funding Legs. Prepayment does not create an Evidence-coverage classifier or bypass any gate.

Illustrative capture areas (not a technical persistence threshold or exact minimum-field rule):

| Field Area | Bill / Fee | Rent |
| --- | --- | --- |
| Name | Bill name, required. | Rent/tenancy name, required. |
| Amount | Bill amount / invoice amount. | Rent amount. |
| Date / Period | Invoice date and due date. | Rent period and rent due date. |
| Frequency | One-off, monthly, bi-monthly, quarterly, yearly, or custom if enabled. | Usually monthly for rent; custom frequency if enabled. |
| Payee / Landlord | Name required where available; ID and phone optional unless category rules require them. | Landlord/payee name required where available; ID and phone optional unless category rules require them. |
| Account / Payout Details | Payer-entered or context-selected recipient name, receiving method, bank/provider, and destination identifier where applicable. | Payer-entered or context-selected landlord/payee name, receiving method, bank/provider, and destination identifier where applicable. |

QR scanning belongs inside `BILLS-ADD` and `BILLS-EVIDENCE-UPLOAD` as a setup and Evidence-capture aid. It must not bypass the applicable Bill Tier or Rent Evidence, verification, risk, destination and Payer-authorization gates.

Destination and Payout facts are specialist-owned. A Payer may provide source/Payee facts for a non-user recipient inside the Category-bound controlled Bill flow or the separate Rent/tenancy flow. DOC-10 owns destination readiness, Payout and reconciliation, and DOC-15 owns privacy/masking/retention. No Consumer Payee Receiving Info route or Request copy behavior is active. The capture-area table does not establish ID persistence, Evidence acceptance or Payment readiness.

Frequency supports due-date display, reminder defaults, bill/rent management, analytics, and payment-readiness UX. It must not be represented as automatic recurring payment, recurring card authorization, or recurring gateway submission unless a separate approved recurring payment model is later defined.

### 5.10 Evidence Sub-Route - DOC-12 Handoff

Evidence is proof supporting a bill/rent/tenancy obligation. It is not itself an obligation, activity, or standalone user-facing card.

An active Request is not required or available for this relationship: a Payer-created Bill/Rent source may link directly to Evidence and proceed to Payment where all applicable owner gates pass.

DOC-12 owns Evidence truth, OCR/extraction, verification, Category and Evidence-to-Payee matching. DOC-06C defines only capture/view handoffs and must not decide Evidence-version presentation, Restore, expiry, revalidation, retention or technical lifecycle mechanics.

Founder-update traceability: Tier 2/3 may use owner-approved formal bills, fee notices, school payment notices, statements, invoices and formal historical receipts only where DOC-12's Category framework accepts them. Examples do not create acceptance. Communication-originated material cannot satisfy, substitute for or contribute to mandatory Evidence. Category operating lists remain later owner/enablement inputs. Rent keeps its separate mandatory attached-Evidence and acceptance-before-Payment model.

Core model:

| Item | Rule |
| --- | --- |
| Main object | Authoritative Bill/Rent source record. |
| Supporting object | One active evidence set for the bill/rent record under normal operation. |
| Versioning | DOC-12 owns Evidence replacement and current-version meaning; DOC-18 represents approved version and lineage requirements when drafted. DOC-06C defines no version rule or presentation. |
| Previous evidence | Detailed presentation and controlled access remain deferred to DOC-12/DOC-15/DOC-18; no new route or prior-version rule is introduced here. |
| Extracted data | Extracted fields should populate bill/rent detail fields where displayable; evidence detail should not duplicate those fields. |

User-facing evidence labels:

| Record Type | Evidence Label |
| --- | --- |
| Bill / fee / invoice | `Bill / Invoice` |
| Rent / tenancy / rent support document | `Rental Doc` |

Evidence actions must be available inside bill/rent detail, not on the bill/rent card. The bill/rent card should show payment readiness and normal card actions such as `Pay`, `View Details`, and `Set Reminder`.

`BILLS-EVIDENCE-DETAIL` should show:

1. Linked bill/rent summary.
2. Evidence label: `Bill / Invoice` or `Rental Doc`.
3. Evidence status.
4. Current active evidence preview or document metadata.
5. Upload or review timestamp.
6. Verified/review timestamp where applicable.
7. Issue note where action is required.
8. Buttons based on evidence existence.

Evidence buttons:

| Evidence State | Buttons |
| --- | --- |
| Evidence exists | `View`, `Update`. |
| Evidence does not exist | `Upload`. |

`BILLS-EVIDENCE-UPLOAD` should support:

- upload file;
- take photo;
- scan QR.

Manual Bill source-fact input remains available in `BILLS-ADD` for Tier 1. Manually entered facts are not attached Evidence and must not be represented as satisfying Tier 2/3 or Rent Evidence.

Upload/update flow:

1. User starts upload or update from `BILLS-EVIDENCE-DETAIL` or evidence step inside `BILLS-ADD`.
2. System captures evidence.
3. AI/OCR reads and classifies evidence where enabled.
4. System autofills extracted fields into the bill/rent record.
5. User reviews and corrects bill/rent details.
6. User submits the Evidence and any permitted corrections.
7. System records the DOC-12-owned Evidence outcome or pending review treatment.
8. Evidence presence and acceptance feed the applicable Bill Tier or Rent gate without themselves establishing Payment Obligation, destination/Payout, risk, Checkout or authorization readiness.

Permitted evidence viewing and downloading within an authenticated session does not require an extra payment-passcode or step-up prompt solely because the document is opened or downloaded. Role, approved-purpose, masking, stale-session, and access-control rules still apply under DOC-15 and DOC-19.

Evidence replacement, Archive and Restore behavior is not defined in detail here. DOC-06B owns later route presentation, DOC-12 owns Evidence eligibility/revalidation/version meaning, DOC-15 owns retention and approved-purpose access requirements, and DOC-18 represents approved data, version, event, audit and lineage requirements. DOC-06C preserves only the high-level source/projection and non-erasure boundary.


#### 5.10.1 Non-Active Documentation Register - Retired Evidence and Version IDs

| Retired documentation evidence | Preservation location | Current treatment |
| --- | --- | --- |
| Former evidence-version, replacement and Restore IDs and prior meanings | Append-only documentation history | Retired detail; no runtime reader, and detailed Restore, revalidation and version presentation are not defined here |



#### 5.10.2 Active Evidence and Readiness Presentation Handoffs

The following Evidence labels are existing illustrative display handoffs only. They are not Bill Tier, Payment readiness, projection or technical taxonomy. DOC-12 owns Evidence outcomes; DOC-09 Payment admission; DOC-10 Payout readiness; DOC-14 risk; DOC-07 exact Copy; and DOC-18 later representation.

Evidence statuses:

| Evidence Status | Meaning |
| --- | --- |
| `Not Provided` | No active evidence exists. |
| `Pending Review` | Evidence uploaded, review not complete. |
| `Accepted` | Evidence accepted for current bill/rent purpose. |
| `Correction Needed` | User must correct extracted or entered fields. |
| `Update Needed` | Current evidence is expired, outdated, insufficient, or requires replacement. |
| `Rejected` | Evidence cannot support the bill/rent. |
| `Duplicate Suspected` | Evidence may be reused/duplicate and needs review. |

#### 5.10.3 Bill/Rent Payment Readiness

Saved/current, Saved/Archived and history-only are source projections/treatments. Under Review, Action Required and Ready are owner-governed handling/readiness conditions that do not create, remove or change a Save/Archive projection.

| Scope | Evidence/readiness handoff |
|---|---|
| Bill Tier 1 | `Not Provided` does not by itself create Action Required or block Payment. Declaration and every other applicable gate remain. Voluntary Evidence remains attributable and owner-governed. |
| Bill Tier 2 | Missing qualifying official Bill Evidence requires user action and blocks Payment. Qualifying presence may permit Payment while acceptance remains pending; Payout remains held. The presentation must not imply that Under Review prevents Payment when only the Tier 2 Evidence-acceptance/Payout gate is pending. |
| Bill Tier 3 | Missing qualifying Evidence or pending mandatory approval blocks executable Payment. A prepared Checkout Workspace may be visible only as non-executable context; no new route/object is created. |
| Rent | Missing, pending, rejected or otherwise unaccepted required Rent Evidence blocks Payment. A Declaration cannot replace or defer it. |

Evidence corrections, updates, rejection and duplicate/risk outcomes expose only owner-approved next actions. A pending Company/Individual label review does not by itself block otherwise eligible Payment when every concrete gate passes.

`Paid` is a Payment activity outcome. `Archived` is a projection descriptor and Archived sources are excluded from the current list. `Due Soon` is a date-derived filter/label. None is an Evidence-processing status or a Bill Tier.

Exact readiness labels, reason presentation and data/event representation remain with DOC-07/DOC-18 and affected source owners. DOC-22 executes only owner-permitted review/configuration and cannot create readiness, Evidence, Tier or approval truth.

### 5.11 Archived Bills & Rent - Current Projection Boundary

Archive moves an already Saved/current authoritative Bill/Rent source into the Saved/Archived visibility projection. Archived sources appear only in the governed Archived Bills presentation and are excluded from the current/active list. Archive is not Under Review, Action Required, Ready, an Evidence outcome or a financial status. It never creates a new source or erases or rewrites Evidence, Payment, destination, Payout, reconciliation or audit history. Detailed Restore, eligibility, revalidation and version behavior remains deferred; DOC-10/DOC-11 blockers remain effective.

`ARCHIVED-BILLS-LIST` is the Payer visibility projection for authoritative Bill/Rent sources that were Saved/current before Archive and now have the Saved/Archived projection. Archived sources do not appear in `BILLS-PAY`. The list is not a readiness condition, mixed-role list, Evidence archive, Payment history or Request archive. Exact Restore eligibility, revalidation, prior-version, Evidence-version, replacement-source presentation and detailed Archive/Restore UI remain deferred to the applicable owners.


#### 5.11.1 Non-Active Documentation Register - Retired Archive IDs

| Retired documentation evidence | Preservation location | Current treatment |
| --- | --- | --- |
| Former mixed-role Archive/Restore IDs and prior meanings | Append-only documentation history | Retired detail; no runtime reader, and detailed Restore, revalidation and version presentation are not defined here |



### 5.12 Reminder Route

Reminder routes must use specific route IDs:

- `BILLS-REMINDER-LIST` for the reminder management screen.
- `BILLS-REMINDER-DETAIL` for creating or editing one reminder.

`BILLS-REMINDER` may be used only as a shorthand discussion label. AI build documents should use the specific list/detail route ID so screens, sheets, and actions are not confused.

Reminder source type should be stored internally without overexposing technical labels to users. MVP source types should include system due-date reminder, user manual reminder, and user custom override reminder. Payment instruction action alerts are not ordinary Bills reminder records and should not appear in `BILLS-REMINDER-LIST`.

Every Bills reminder must have a `reminderID` and link to exactly one existing Bill/Rent source ID or, where the applicable owner permits, one linked obligation reference. The reminder must not treat those identities as interchangeable. A reminder created from a Bill/Rent card or detail page should inherit its governing source context. A reminder created from `BILLS-REMINDER-LIST` through `+ Add Reminder` must first require the Payer to select an existing Bill/Rent source context. Free-floating reminders are not MVP scope.

`BILLS-REMINDER-LIST` should use the following rough screen order:

1. Page title: `Reminders`.
2. Top action: `+ Add Reminder`.
3. Filter row: All, Bill, Rent, Due Soon, Inactive.
4. Optional sort control: Due Date or Amount.
5. Reminder card list, ranked by due date by default.
6. Empty state when no reminders exist.
7. Selection-mode bottom action bar only when long-press selection is active.

Reminder cards should show, in compact order:

- reminder summary;
- linked Bill/Rent name, the controlled Bill Category where applicable or Rent journey/source type, and the current owner-governed readiness/status presentation;
- amount and due date;
- reminder timing and next reminder date;
- on/off toggle on the right side.

Tapping the non-toggle area of a reminder card opens `BILLS-REMINDER-DETAIL`.

`BILLS-REMINDER-DETAIL` should use the following rough screen order:

1. Linked bill/rent/fee summary.
2. Active/inactive toggle.
3. Reminder type: due-date based or custom date/time.
4. Cycle: one-off, monthly, bi-monthly, quarterly, yearly, or custom if enabled.
5. Reminder offset or custom date/time.
6. Notification note: app notification and push notification are MVP where permission is granted; email, SMS, and WhatsApp routing are governed by DOC-08.
7. Save and cancel actions.
8. Disable or deactivate action where applicable; indefinite retention remains the Founder-approved product and governance direction for underlying reminder records, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries.

DOC-06C owns the approved reminder-default product policy. DOC-22 may expose and execute only permitted Admin configuration of those approved defaults; it does not set the product policy:

| Record Type | Default Reminder |
| --- | --- |
| Rent | Monthly, 3 days before due date. |
| Monthly bill | Monthly, 3 days before due date. |
| One-off invoice | Once, 3 days before due date. |

If a user custom reminder exists for the same bill/rent reminder period, it overrides the system/default reminder for that instance.

Reminder status and lifecycle:

| Condition | Reminder Behavior |
| --- | --- |
| Linked bill/rent is archived | Reminder becomes inactive. |
| One-off invoice is fully paid | Reminder becomes inactive. |
| Reminder date has passed and reminder is not recurring | Reminder becomes expired or inactive. |
| Evidence is expired, invalid, rejected, or requires review | Reminder remains valid. For Tier 1 Bills, absence alone does not create Action Required; Tier 2/3 and Rent consume the applicable owner-controlled Evidence gate. The linked presentation must preserve its Tier/Rent meaning. |

Reminder deactivation should be supported from `BILLS-REMINDER-LIST`:

1. User long-presses a reminder card.
2. Screen enters selection mode and automatically selects the tapped card.
3. Checkboxes appear on reminder cards.
4. A bottom action bar slides up and stays fixed at the bottom area.
5. User may select multiple reminders.
6. Deactivation requires confirmation.
7. User-facing deactivation must preserve the reminder record for audit, support, analytics and abuse investigation; no hard deletion is introduced.

User-created or custom reminder records may be disabled or deactivated. System/default due-date reminders should normally be disabled. Payment instruction action alerts are excluded from this reminder-management flow; no reminder record is destroyed.

Due soon, overdue, evidence rejected, and payment-readiness action states belong primarily to the linked bill/rent card and detail page. Reminder cards should focus on reminder state such as next reminder date, reminder off, reminder expired, or custom reminder set.

DOC-08 owns notification IDs, channel matrix, templates, user preferences, retry behavior, and delivery logging. DOC-06B owns `INSTRUCTIONS-ROOT` and `INSTRUCTIONS-DETAIL` route shells and return presentation. DOC-09 owns the domain distinction between deliberate Payment Instructions and incomplete Checkout Workspaces. DOC-15 owns sensitive-data display and masking. DOC-18 owns final schema, event taxonomy, lineage, and analytics definitions.

### 5.13 Evidence Structure and UX

Evidence handling must distinguish the obligation, the relationship/contract, and the source evidence.

Working conceptual relationship — DOC-09 remains authoritative:

```text
Authoritative Bill/Rent source
-> Contract / relationship context and owner-governed Evidence facts where applicable
-> one or more DOC-09 Payable Bases where materialized
-> one or more DOC-09 Payment Obligations where materialized

DOC-09 Checkout Workspace against one Payable Basis
-> Checkout-owned Obligation Allocations referencing applicable Payment Obligations
-> Funding Legs
-> each successfully confirmed Funding Leg produces one immutable Payment
-> Payment Applications apply confirmed obligation value to applicable Payment Obligations

Activity / Payment History / Receipt are projections of the applicable authoritative source and confirmed Payment facts.
A controlled late-confirmed Payment may temporarily have zero Payment Applications.
```

For bills, invoices, and fees, the evidence usually supports a specific obligation or payment cycle.

For rent, tenancy evidence usually supports a contract or relationship. Rent obligations may then be generated from that tenancy context. Tenancy-related evidence may include tenancy agreement, stamp duty document, CR109, rent demand, property management notice, HKHA tenancy card, carpark invoice, or other approved rent-supporting evidence. Exact evidence categories, fields, review thresholds, and schemas belong in DOC-12 and DOC-18.

The Bills route should therefore support evidence source detection or selection inside `BILLS-EVIDENCE-UPLOAD` when the category or document type is not obvious, instead of assuming every rent flow equals tenancy agreement and every bill flow equals invoice.

### 5.14 Non-Active Documentation Register - Retired Two-Sided IDs

The records below preserve retired stable IDs and prior meanings only as non-active documentation evidence. Founder confirmation establishes that no production Request/Payee-role runtime or legacy Request deep-link data exists. They define no runtime reader, screen, action, notification, Linking, acceptance, destination change, Restore, adapter, fallback or event behavior.

| Retired identifier or concept | Preservation location | Current treatment |
| --- | --- | --- |
| Former BILLS-RECEIVE, Request, Linking and Payee-side Bill/Rent IDs | Append-only documentation history | Retired active MVP; no production data, route, runtime reader, action, reciprocal visibility or replacement behavior |
| Prior destination, archive and Evidence-version meanings | Append-only documentation history | Archive remains the same-source Payer visibility projection under W2-FD-05 Option A; detailed Restore, revalidation, prior-version and Evidence-version presentation remains deferred to DOC-06/DOC-10/DOC-11/DOC-12/DOC-15/DOC-18 |


### 5.15 Action-Required UX

Action-required states must be visible before the user attempts payment where possible.

Examples where the applicable Bill Tier, Rent rule or another owner gate requires action:

- evidence needs Payer correction or additional input;
- required Evidence not provided; Tier 1 absence alone is excluded;
- evidence rejected;
- evidence expired;
- missing required field;
- material mismatch between user-entered and extracted evidence data;
- duplicate or reused evidence warning;
- payee/payout detail requires Payer correction or another owner-approved action;
- payment instruction requires user action;
- reminder/action deadline is approaching.

The card should show the payment readiness badge and a clear next action. Evidence-specific actions should appear inside the bill/rent detail evidence section, not as multiple evidence buttons on the card. The detail page should show the affected section, the rejected or missing field where appropriate, an `Upload`, `Update`, or `Fix` evidence action, and cautious helper text below the affected field. Exact user-facing wording belongs in DOC-07 and DOC-08.

### 5.16 Data and Intelligence Signals

Bills route interactions should produce structured events or signals for later DOC-18 specification, including:

- route opened and view selected;
- filter selected;
- Bill/Rent card viewed;
- detail opened;
- evidence source selected;
- input method selected: upload, photo, QR scan, or manual entry;
- extracted field confirmed or corrected;
- evidence upload or update started;
- evidence submitted;
- evidence status changed;
- evidence verification outcome displayed;
- combined bill/rent readiness presentation changed after an owner-controlled Evidence input changed;
- action-required state displayed;
- action-required state resolved;
- payer-created record created;
- payment started from card or detail page;
- reminder created, edited, disabled, deactivated, fired, opened, ignored/dismissed, or followed by payment start;
- record archived;
- bill/rent activity timeline opened;
- activity entry detail opened;
- receipt or payment proof downloaded;
- payment, payout/transfer, failure, return, refund, or reversal status displayed in activity.

These events should support product analytics, operational monitoring, risk review, support investigation, and future approved AI/payment-intelligence use under DOC-15 and DOC-18. They must not create automatic user-to-user matching or overexpose sensitive evidence data.

## 6. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06C-001 | Which owner-approved C1 values/operating details, Category official Bill Evidence lists and Tier 3 role/workflow controls implement the settled frameworks? | Product / Operations / Risk / Compliance | Open later configuration/enablement input; blocks affected-path enablement/acceptance until supplied |
| OQ-06C-002 | Which rent and tenancy journey controls must be ready before initial launch enablement? | Product / Legal / Risk | Open |
| OQ-06C-003 | What, if any, future participant Linking or invitation capability should be proposed as a separately governed domain after MVP? | Product / Privacy / Engineering | Deferred; no active Linking or invitation behavior is authorized |
| OQ-06C-004 | What exact Bills tab visual layout, card density, status badge style, action-required treatment, and field masking rules should be used? | Product / Design / Privacy | Open |
| OQ-06C-005 | What evidence source selection UI should be used when bill, invoice, tenancy, rent demand, contract, and supporting evidence types are not obvious from upload/OCR? | Product / Design / Risk | Open |
| OQ-06C-006 | Retired: Founder confirmed there is no production BILLS-RECEIVE/Request runtime or legacy deep-link data requiring a reader, adapter or fallback. | Product / Design / Operations | Answered/retired |
| OQ-06C-007 | What exact DOC-07 Copy and presentation distinguish Saved/current projection from Under Review, Action Required and Ready conditions, and exclude Archived sources from the current list? | Product / Design / Content | Open; Copy/visual detail does not change the accepted semantic boundary |
| OQ-06C-008 | What operating tests and presentation implement the accepted Declaration materiality and proportionate reconfirmation framework without treating limit re-evaluation or every amount edit as a full new Declaration? | Product / Content / Legal / Compliance / Payments | Open later product/content/acceptance input; any future answer must preserve or be reconciled through the accepted rule |

Legal, Compliance, PSP/acquirer, card-network, Finance, Privacy, Security and Operations confirmations remain explicit affected-path dependencies. They must be resolved before the affected path's enablement, implementation, acceptance, production readiness or launch. A professional conflict that changes product meaning must be handled under the canonical PayPlus Documentation Development Workflow.

## 7. Acceptance Criteria

DOC-06C defines the following user-journey boundaries:

1. Add a Bill applies C1 only before Save and does not apply or reserve G1/G2.
2. Pay a Bill re-evaluates current C1/G1/G2 and consumes only the highest Tier while retaining all trigger reasons.
3. Tier 1 supports manual Bill facts and optional Evidence assistance without making attached Evidence mandatory.
4. Tier 2 blocks Payment until qualifying official Bill Evidence is present, permits Payment while acceptance remains pending where other gates pass, and communicates that Payout remains held.
5. Tier 3 permits prepared but non-executable Checkout context and exposes no executable authorization, Provider Submission or confirmed Payment before approval.
6. No new Tier route, recovery object, exact Copy, technical event, status, schema or permission is introduced.
7. Declaration, Save intent and Payment authorization remain distinct; unchanged facts require no new Declaration; user changes use owner-defined proportionate reconfirmation.
8. Saved/current Bills may remain visible while Under Review, Action Required or Ready; those conditions do not create or remove the projection.
9. Archive moves a Saved/current source to Saved/Archived presentation, excludes it from `BILLS-PAY`, and does not erase source or history.
10. History-only treatment remains limited to the established confirmed-Payment/no-Save rule.
11. Category prepayment uses the aggregate C1/G2 amount and one G1 progression without creating Evidence-coverage classification.
12. Rent remains outside Bill C1/G1/G2 and tiers, requires attached Evidence accepted before Payment, and cannot use Declaration to bypass that gate.
13. C1 values/operating details, official Bill Evidence Category lists, Tier 3 operating controls, Declaration presentation and professional confirmations remain visible later dependencies at their actual enablement/implementation/acceptance/launch blocking level rather than being hidden in DOC-22 workflow language.

## 8. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 1.0.0 | 2026-08-18 | Implemented the material Bills-only UX baseline and fixed-seat compliance supplement; traced the Founder-updated official Bill Evidence framework, preserved C1/Tier 3/Declaration semantics, neutralized active lifecycle-language ambiguity, qualified reminder retention by lawful scope, and retained exact Copy/representation ownership. |
| 0.1.23 | 2026-08-12 | Applied the Founder-settled indefinite-retention boundary to reminder controls without introducing a deletion mechanism. |
| 0.1.22 | 2026-08-12 | Stage 8 correction: made the conceptual Payment Domain relationship DOC-09-faithful and restored the bounded DOC-12/DOC-15/DOC-18/DOC-22 Evidence ownership handoff without introducing technical design. |
| 0.1.21 | 2026-08-12 | Stage 8 Wave 2 Draft: aligned to the accepted Category inventory and separate Rent journey, removed nonexistent Request-runtime/readers/deep-link obligations, structurally separated active readiness from non-active history, preserved source-to-Payment separation, and retained DOC-10/DOC-11 Archive owner blockers. |
| 0.1.20 | 2026-08-05 | Added the bounded HOME-ROOT Upcoming Bills / Rent source handoff by publishing active payer-role candidate facts, deterministic source values, canonical card/masking fields, source-route revalidation truth, upstream invariant treatment, and the canonical Rent due timestamp while retaining Home presentation and ordering in DOC-06B. |
| 0.1.19 | 2026-08-03 | Removed the stale future-draft qualification and aligned Bill/Rent handoff ownership with the reviewed DOC-06B Checkout route-level UI/UX contract and DOC-09 Payment Domain authority. |
| 0.1.18 | 2026-07-31 | Aligned Bills-to-checkout handoff and Instructions references with DOC-09 Payment Domain Architecture while preserving DOC-06B route-level UX ownership. |
| 0.1.17 | 2026-07-27 | Aligned `BILLS-PAY` with temporary Pay+ Bill/Fee and Rent/Tenancy selection scopes and defined standalone Pay+ `BILLS-ADD` success/readiness behavior without changing Bills ownership or checkout logic. |
| 0.1.16 | 2026-07-26 | Defined `ARCHIVED-BILLS-LIST`, archived read-only bill/rent detail mode, mixed-role search/filters, archive eligibility and blockers, personal archive projection, restore behavior, evidence cascade, reminder effects, and non-restorable handling. |
| 0.1.15 | 2026-07-26 | Moved archived obligations out of Bills filters into the `ARCHIVED-ROOT` family, removed standalone current-evidence archive, and defined replacement, parent archive, restore, expiry, and previous-version rules. |
| 0.1.14 | 2026-07-26 | Limited obligation readiness to `Ready to Pay`, `Action Required`, and `Under Review`; separated payment outcomes, archive visibility, due-state labels, request lifecycle, and linked dispute cases from Bills Activity. |
| 0.1.13 | 2026-07-26 | Limited `BILLS-ACTIVITY` to payment and related payout/failure/return/refund/reversal activity, removed request/evidence milestones, clarified evidence-request-obligation relationships and payer-created direct linkage, and aligned document viewing/download authentication behavior. |
| 0.1.12 | 2026-07-23 | Aligned bill/rent setup and linked-context behavior with private multiple Receiving Info profiles, destination snapshots, payee-request replacement rules, payer destination changes, linked-payee notifications, and authorization freeze. |
| 0.1.11 | 2026-07-22 | Aligned archived/previous evidence retrieval with DOC-06B `ME-ROOT` and the dedicated `ARCHIVED-EVIDENCE-LIST` destination while preserving Bills-specific archive ownership and archive-not-delete behavior. |
| 0.1.10 | 2026-07-17 | Reclassified existing `BILLS-*` names as stable product destinations and retained `ROUTE-06C-*` values only as legacy traceability aliases, without changing Bills behavior. |
| 0.1.9 | 2026-07-08 | Clarified `BILLS-ACTIVITY` as DOC-06C contextual activity, separated it from DOC-06B global Activity and Receipts & Statements routes, and made receipt/proof access a direct download by default from `BILLS-ACTIVITY-DETAIL`. |
| 0.1.8 | 2026-07-06 | Aligned `BILLS-ACTIVITY` user-facing status labels and activity-detail timeline wording with the status display reference matrix. |
| 0.1.7 | 2026-07-06 | Clarified Bills-route checkout handoff with DOC-06B `PAYMENT-PROFILE-ROOT` while preserving DOC-09 ownership of checkout and split-card payment behavior. |
| 0.1.6 | 2026-07-03 | Aligned reminder route boundary with DOC-06B Instructions route: payment instruction action alerts stay outside `BILLS-REMINDER-LIST` and route through Instructions / DOC-09 instead. |
| 0.1.5 | 2026-07-03 | Aligned Bills add/request handoffs with the finalized DOC-06B `REQUESTS-NEW` route shell, including create-new return behavior, cancellation behavior, and request-delivery handoff. |
| 0.1.4 | 2026-07-02 | Aligned Bills add/detail handoffs with DOC-06B `REQUESTS-NEW` and `REQUESTS-DETAIL`, including evidence-before-request-delivery boundary. |
| 0.1.3 | 2026-06-29 | Aligned Bills/rent request actions with DOC-06B `REQUESTS-DETAIL` ownership. |
| 0.1.2 | 2026-06-25 | Clarified that Bills/rent `Request` actions create or update request records and do not directly open the Requests route by default. |
| 0.1.1 | 2026-06-25 | Cleaned publication wording for official DOC-06C baseline use without changing Bills/rent/tenancy decisions. |
| 0.1.0 | 2026-06-25 | Created as DOC-06C child document for Bills, rent, tenancy, activity, evidence, reminder, payer/payee role, and data-signal UX content. |
