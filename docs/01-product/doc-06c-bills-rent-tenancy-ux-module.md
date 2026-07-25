---
document_id: DOC-06C
title: Bills, Rent & Tenancy UX Module
version: 0.1.14
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
last_updated: 2026-07-26
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06C - Bills, Rent & Tenancy UX Module

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06C` |
| **Title** | Bills, Rent & Tenancy UX Module |
| **Version** | `0.1.14` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-07-26` |
| **Classification** | Internal |
| **Related Documents** | DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

DOC-06C governs the PayPlus Bills, rent, tenancy, fee, obligation, reminder, activity, evidence, and role-aware Bills-route UX module.

It is the owning document for BILLS-PAY, BILLS-RECEIVE, BILLS-ACTIVITY, BILLS-ACTIVITY-DETAIL, BILLS-ADD, BILLS-EVIDENCE-DETAIL, BILLS-EVIDENCE-UPLOAD, BILLS-REMINDER-LIST, and BILLS-REMINDER-DETAIL at the human-readable UX level.

## 2. Scope Boundary

DOC-06C owns the user-facing Bills module route behavior, card/detail actions, role separation, evidence sub-flow, reminder management, activity timeline, and route handoffs.

DOC-06C does not own detailed checkout/payment processing, evidence verification algorithms, final data schema, final event taxonomy, privacy masking rules, notification templates, risk thresholds, or admin queue design. Those remain with DOC-08, DOC-09, DOC-12, DOC-14, DOC-15, DOC-18, DOC-19, and DOC-22 as applicable.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| BILLS-PAY payer-side route | Working baseline | Card/detail actions defined; final visual UI remains open. |
| BILLS-RECEIVE payee-side route | Working baseline | Request/remind-payer actions defined; resend limits and exact wording remain open. |
| Bill/rent cards and details | Working baseline | Field set defined; final density, masking, and visual hierarchy remain open. |
| Activity sub-route | Working baseline | Payment activity and limited milestones defined; global Activity and Receipts & Statements routes remain separate under DOC-06B. |
| Add Bill / Rent flow | Working baseline | Evidence capture methods and required fields defined; source selection UX remains open. |
| Evidence sub-route | Working baseline | Evidence detail/upload behavior and status mapping defined; data model remains DOC-18. |
| Reminder list/detail route | Working baseline | Linked reminders, defaults, custom override, toggle, and soft-delete defined; payment-instruction action alerts remain outside Bills reminder management. |
| User-to-user linking | Partially defined | Automatic matching is not allowed; invitation/linking mechanism remains open. |

## 4. Product Destination and Legacy Traceability Map

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

The product destination IDs in the first column are the stable route names for human documents, diagrams, and later AI build-execution conversion. The DOC-06C-prefixed aliases are retained only as legacy traceability references and must not replace the product destination names or be extended as a separate route taxonomy.

---

## 5. Bills, Rent & Tenancy UX Module Working Baseline

This section defines the working baseline for the `Bills` bottom-navigation route. It is a route-level UX and behavior specification, not a final visual UI design.

Route-level UI drafting rule: each route should define user-facing behavior and identify material events/data signals required for AI-ready data-engine support. Detailed schema, event taxonomy, lineage, model registry, and warehouse design remain owned by DOC-18.

### 5.1 Route and Subsection IDs

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
| `BILLS-PAY` | Tab / view | To Pay view | `To Pay` tab inside `BILLS-ROOT`, Pay+ `Pay a Bill / Fee`, Pay+ `Pay Rent`, dashboard items, reminders, or action-required notifications | Payer-oriented selection and management route for bills, fees, rent, and requests the user needs or expects to pay. This replaces the earlier informal "To Pay view" description. It is not the checkout/payment route. |
| `BILLS-RECEIVE` | Tab / view | To Receive view | `To Receive` tab inside `BILLS-ROOT`, payee-side request status, dashboard items, or action-required notifications | Payee-oriented request and receive-management route for bills, fees, rent, and requests the user expects to receive. It must not show payer-side `Pay` actions. |
| `BILLS-CARD-BILL` | Card component | Bill / fee card | Rendered inside `BILLS-PAY` or `BILLS-RECEIVE` | Summary card for a bill, invoice, fee, or approved non-rent obligation. |
| `BILLS-CARD-RENT` | Card component | Rent / tenancy card | Rendered inside `BILLS-PAY` or `BILLS-RECEIVE` | Summary card for rent or tenancy-linked obligation. |
| `BILLS-DETAIL-BILL` | Screen | Bill / fee detail | `Details` on `BILLS-CARD-BILL` | Detail page for bill, invoice, fee, or approved obligation record. |
| `BILLS-DETAIL-RENT` | Screen | Rent / tenancy detail | `Details` on `BILLS-CARD-RENT` | Detail page for rent record and linked tenancy context. |
| `BILLS-ACTIVITY` | Sub-route / screen or sheet | Bill/rent activity timeline | `View Activities` from bill/rent detail pages | User-facing payment, payout/transfer, failure, return, refund, and reversal activity for one selected bill/rent record. This is not request history, evidence management, global history, or an internal audit log. |
| `BILLS-ACTIVITY-DETAIL` | Sub-route / screen or sheet | Activity entry detail | Tapping one entry in `BILLS-ACTIVITY` | Detail view for one selected payment/activity entry, with reference number, receipt/proof access, and optional link to the payment detail route where needed. |
| `BILLS-ADD` | Flow / screen group | Add Bill / Rent flow | `Add Bill / Rent` button or Pay+ action sheet | Setup flow for new bill, fee, rent, tenancy, or evidence-backed obligation. |
| `BILLS-EVIDENCE` | Sub-flow group / shorthand | Evidence sub-flow | Detail-page evidence area, `BILLS-ADD`, or evidence action-required state | Shorthand for bill/rent evidence actions. Evidence is a supporting attachment/status layer of a bill/rent record, not a standalone user object. |
| `BILLS-EVIDENCE-DETAIL` | Screen or sheet | Evidence detail | Evidence section inside `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT` | View and manage the current active evidence set for one bill/rent record. |
| `BILLS-EVIDENCE-UPLOAD` | Flow / screen group | Evidence upload/update | `Upload` or `Update` from evidence detail, or evidence step inside `BILLS-ADD` | Upload file, take photo, scan QR, or enter evidence manually; supports OCR/autofill and user correction through the bill/rent setup/detail flow. |
| `BILLS-REMINDER-LIST` | Screen | Reminder management | Dashboard shortcut `Reminders` | Alarm-style reminder management screen for reminders linked to bill, fee, rent, tenancy, or obligation records. |
| `BILLS-REMINDER-DETAIL` | Sheet or screen | Reminder setup/edit | `Set Reminder`, `Edit Reminder`, or `+ Add Reminder` | Create or edit one reminder linked to a specific bill, fee, rent, tenancy, or obligation. |
| `BILLS-LINKING` | Flow / sheet | Participant linking/invitation | Optional link/invite action where enabled | User-initiated or user-accepted payer/payee linking. Must not perform automatic user-to-user matching. |
| `BILLS-ARCHIVED` | Filtered view | Archived records | `Archived` filter | Archived bill/rent records only; archive is the normal user-facing removal action, not delete. |

Initial route ownership:

| User Action | Source | Destination / Behavior |
| --- | --- | --- |
| Tap `Bills` bottom nav | App bottom navigation | Opens `BILLS-ROOT`, defaulting to the last used or system-default `To Pay` / `To Receive` view. |
| Tap `To Pay` | `BILLS-ROOT` | Opens `BILLS-PAY`. |
| Tap `To Receive` | `BILLS-ROOT` | Opens `BILLS-RECEIVE`. |
| Tap `Add Bill / Rent` | `BILLS-ROOT`, Pay+ action sheet, or `REQUESTS-NEW` create-new path | Opens `BILLS-ADD`. If opened from `REQUESTS-NEW`, successful completion must return to `REQUESTS-NEW` with the created bill/rent context selected; cancellation returns to `REQUESTS-NEW` without changing the selected context. |
| Tap `Pay` on a payer-side card/detail | `BILLS-PAY`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Opens payment/checkout flow governed by DOC-09. DOC-06C owns the entry point and route handoff only. |
| Tap `Request` on a payee-side card/detail | `BILLS-RECEIVE`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Creates, sends, resends, or opens request-delivery action for a verified bill/rent/tenancy context before counterparty acceptance. The action creates or updates a request record that may appear in `REQUESTS-ROOT` and be managed in `REQUESTS-DETAIL`; it does not open `REQUESTS-ROOT` by default. Where the user must select receiver, delivery method, or share channel, route through DOC-06B `REQUESTS-NEW`. A request must not be delivered before required evidence is verified or approved by exception. Exact request delivery method and notification behavior must follow DOC-08 and later DOC-22 controls. |
| Tap `Remind Payer` on a payee-side card/detail | `BILLS-RECEIVE`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Opens or triggers an approved payer reminder action for the selected request. This is a payee-to-payer request reminder, not a payment action and not the user's own `BILLS-REMINDER-LIST` reminder record unless later explicitly linked. |
| Tap `Details` | Bill/rent card | Opens the relevant detail screen. |
| Tap `Set Reminder` / `Edit Reminder` | Bill/rent card or detail page | Opens `BILLS-REMINDER-DETAIL` for the selected linked record. |
| Tap `Reminders` shortcut | Dashboard shortcut grid | Opens `BILLS-REMINDER-LIST`. |
| Tap `+ Add Reminder` | `BILLS-REMINDER-LIST` | User selects an existing bill, fee, rent, tenancy, or obligation, then opens `BILLS-REMINDER-DETAIL`. |
| Tap `View Activities` | Detail page | Opens `BILLS-ACTIVITY`. |
| Tap one activity entry | `BILLS-ACTIVITY` | Opens `BILLS-ACTIVITY-DETAIL` or a later payment detail route if separately defined. |
| Tap contextual `View` evidence action | Evidence status area inside bill/rent detail page | Opens `BILLS-EVIDENCE-DETAIL` for the selected bill/rent record. |
| Tap `Upload` / `Update` evidence | `BILLS-EVIDENCE-DETAIL` or evidence step in `BILLS-ADD` | Opens `BILLS-EVIDENCE-UPLOAD`. |
| Tap evidence action-required prompt | Bill/rent detail page | Opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD` depending on whether evidence exists. |
| Tap `Archive` | Detail page | Archives the record and returns to the relevant Bills list/filter. |
| Tap optional `Invite / Link Payee` or `Invite / Link Payer` | Detail page or request context where enabled | Opens `BILLS-LINKING`; linking requires approved user or operational action. |

Payment/checkout ownership rule:

- DOC-06C owns the user-facing entry point, route handoff, back/return behavior expectation, and the fact that payer-side `Pay` opens checkout.
- DOC-09 owns the payment/checkout screen content and behavior, including payment quote, fee display, promotion quote, card or payment profile selection, split-card allocation, authorization, 2FA/passcode gates, deferred payment instruction, revalidation, error handling, and payment-state outcomes. DOC-06B `PAYMENT-PROFILE-ROOT` owns reusable card/profile management when checkout or instruction flows need a card/profile management handoff.
- DOC-07 owns required user-facing wording and disclosures; DOC-08 owns checkout-related notifications and receipts; DOC-13 owns promotion/coupon/voucher checkout treatment; DOC-15 owns masking and data visibility; DOC-19 owns authentication/security controls; DOC-18 owns route events and data signals.

### 5.2 Top-Level Views

`To Pay` and `To Receive` must always appear. If the user currently has no payee-side records, `To Receive` should show an empty state instead of disappearing.

| View | User Meaning | Includes | Does Not Include |
| --- | --- | --- | --- |
| `To Pay` | Things the user needs, expects, or has been requested to pay. | Payer-created bills/rent, payee-created requests awaiting payer action, due obligations, payment readiness, payment history, receipts. | Payee-side payout management. |
| `To Receive` | Things the user expects to receive as payee, landlord, biller, or service provider. | Payee-created bill/rent/request records, request status, payer response, payout-received status, payee evidence management. | Payer-side received requests that require the user to pay. |

A payer receiving a request from a payee belongs in `To Pay`, because the user is receiving a request to pay. It should not be shown under `To Receive`.

`BILLS-PAY` and `BILLS-RECEIVE` may render the same bill/rent card component types, but the action set must be role-aware:

| Context | Governed User Intent | Primary Actions |
| --- | --- | --- |
| `BILLS-PAY` | User is acting as payer. | Pay, review request where payer acceptance is required, view details, set reminder, update detail when action-required. |
| `BILLS-RECEIVE` | User is acting as payee, landlord, biller, or recipient. | Request before payer acceptance, view details, remind payer, edit detail where allowed, archive. |

The detail route may remain `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT`, but its visible actions must follow the context from which it was opened. A detail page opened from `BILLS-RECEIVE` must not show the payer-side `Pay` action.

### 5.3 Filters

| View | MVP Filters | Rule |
| --- | --- | --- |
| `To Pay` | All, Action Required, Due Soon, Paid, Archived | `All` excludes archived records. `Archived` shows only archived records. |
| `To Receive` | All, Action Required, Due Soon, Received, Archived | `All` excludes archived records. `Archived` shows only archived records. |

Action-required items should be visible through a filter and through status badges on the relevant card.

### 5.4 Bill / Fee Card

`BILLS-CARD-BILL` should show the minimum information needed for quick recognition and action:

- category: Bill, Fee, Invoice, or approved obligation;
- bill name, required;
- latest amount;
- next due date;
- last payment date;
- payment readiness or status badge.

Payer-side card actions when rendered in `BILLS-PAY`:

| Action | Route / Behavior |
| --- | --- |
| Pay | Opens payment/checkout flow for the selected obligation, subject to DOC-09 eligibility and authorization rules. |
| View Details | Opens `BILLS-DETAIL-BILL`. |
| Set Reminder | Opens `BILLS-REMINDER-DETAIL` for this obligation. |
| Update Detail | Replaces normal edit/detail prompt when the card is action-required due to rejected, missing, expired, or inconsistent information. |

Payee-side card actions when rendered in `BILLS-RECEIVE`:

| Action | Route / Behavior |
| --- | --- |
| Request | Available before payer acceptance; sends, resends, or opens request-delivery action for the selected verified request. Disappears after payer acceptance. |
| View Details | Opens `BILLS-DETAIL-BILL` in payee-side context. |
| Remind Payer | Opens or triggers approved payer reminder action for the selected request, subject to DOC-08 and DOC-22 controls. |

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
| View Activities | Opens `BILLS-ACTIVITY` for payment and related payout/refund/reversal activity for this obligation. |
| Set Reminder / Edit Reminder | Opens `BILLS-REMINDER-DETAIL` for this obligation. |
| Edit Details | Opens editable bill/payee/detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

Payee-side detail actions when opened from `BILLS-RECEIVE`:

| Action | Route / Behavior |
| --- | --- |
| Request | Available before payer acceptance; sends, resends, or opens request-delivery action. Disappears after payer acceptance. |
| View Activities | Opens `BILLS-ACTIVITY` for payment and related payout/refund/reversal activity for this obligation. |
| Set Reminder / Edit Reminder | Opens reminder behavior for the selected record where the reminder belongs to the current user; payer-facing request reminders are governed by DOC-08 and DOC-22. |
| Edit Details | Opens editable bill/payee/detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

The bill detail page should include a `Bill / Invoice` evidence status area. It should show current evidence status and extracted bill/invoice fields approved for display. Evidence management is not a default primary detail action. If evidence is missing, rejected, expired, or otherwise action-required, the status area should show a contextual action that opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD`. Extracted fields that belong to the bill/invoice record should be displayed in the bill detail area, not duplicated inside evidence detail.

### 5.6 Rent / Tenancy Card

`BILLS-CARD-RENT` should show:

- category: Rent;
- bill/rent name, required;
- rent amount;
- rent period;
- next due date;
- last payment date;
- payment readiness or status badge.

Payer-side card actions when rendered in `BILLS-PAY`:

| Action | Route / Behavior |
| --- | --- |
| Pay | Opens payment/checkout flow for the rent obligation, subject to DOC-09 eligibility and authorization rules. |
| View Details | Opens `BILLS-DETAIL-RENT`. |
| Set Reminder | Opens `BILLS-REMINDER-DETAIL` for this rent record. |
| Update Detail | Replaces normal edit/detail prompt when the card is action-required. |

Payee-side card actions when rendered in `BILLS-RECEIVE`:

| Action | Route / Behavior |
| --- | --- |
| Request | Available before payer acceptance; sends, resends, or opens request-delivery action for the selected verified rent request. Disappears after payer acceptance. |
| View Details | Opens `BILLS-DETAIL-RENT` in payee-side context. |
| Remind Payer | Opens or triggers approved payer reminder action for the selected rent request, subject to DOC-08 and DOC-22 controls. |

### 5.7 Rent / Tenancy Detail Page

`BILLS-DETAIL-RENT` should show:

- category: Rent;
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
| View Activities | Opens `BILLS-ACTIVITY` for payment and related payout/refund/reversal activity for this rent record. |
| Set Reminder / Edit Reminder | Opens `BILLS-REMINDER-DETAIL` for this rent record. |
| Edit Details | Opens editable rent/landlord/payment detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

Payee-side detail actions when opened from `BILLS-RECEIVE`:

| Action | Route / Behavior |
| --- | --- |
| Request | Available before payer acceptance; sends, resends, or opens request-delivery action. Disappears after payer acceptance. |
| View Activities | Opens `BILLS-ACTIVITY` for payment and related payout/refund/reversal activity for this rent record. |
| Set Reminder / Edit Reminder | Opens reminder behavior for the selected record where the reminder belongs to the current user; payer-facing request reminders are governed by DOC-08 and DOC-22. |
| Edit Details | Opens editable rent/landlord/payment detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

The rent detail page should include a `Rental Doc` evidence status area. `Rental Doc` covers tenancy agreements and other approved rent-supporting evidence, such as rent demand, stamp duty document, CR109, HKHA tenancy card, carpark invoice, or property management notice. It should show current evidence status and extracted rental fields approved for display. Evidence management is not a default primary detail action. If evidence is missing, rejected, expired, or otherwise action-required, the status area should show a contextual action that opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD`. Extracted fields that belong to the rent/tenancy record should be displayed in the rent detail area, not duplicated inside evidence detail.

Rent normally should not require a new invoice for each payment cycle unless tenancy evidence expires, changes, is replaced, is rejected, or is flagged by risk/review rules.

### 5.8 Bill / Rent Activity Sub-Route

`BILLS-ACTIVITY` is a user-facing sub-route for one selected bill/rent record. It should be opened from `View Activities` inside `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT`.

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
| Admin/internal audit and evidence review history | DOC-22 |

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
- evidence view, update, upload, or archive actions, which belong to `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`;
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
| Payer | `Paid`, `Transferred`, `Failed`, `Returned`, `Refunded`, `Reversed`, `Under Review` | DOC-09 / DOC-10 / DOC-11 / DOC-14 / DOC-22 |
| Payee | `Processing`, `Received`, `Rejected`, `Returned`, `Reversed`, `Under Review` | DOC-09 / DOC-10 / DOC-11 / DOC-14 / DOC-22 |

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

Request lifecycle belongs to DOC-06A/DOC-06B. Evidence lifecycle and management belong to `BILLS-EVIDENCE-DETAIL`, `BILLS-EVIDENCE-UPLOAD`, DOC-12, DOC-18, and DOC-22. Neither belongs in `BILLS-ACTIVITY`.

### 5.9 Add Bill / Rent Flow

`BILLS-ADD` should support:

1. Select category: Bill / Fee or Rent.
2. Capture evidence where category rules require it, or enter details manually where permitted.
3. Use `BILLS-EVIDENCE-UPLOAD` for upload file, take photo, scan QR code, or manual evidence input.
4. Process AI/OCR classification and extraction where enabled.
5. Autofill extracted fields into the bill/rent setup fields.
6. Let user review and correct bill/rent details before submission.
7. Submit the bill/rent setup and linked evidence for system verification, user clarification, or admin review according to DOC-12 and DOC-14.
8. Create the initial evidence status and bill/rent payment readiness status.

Minimum setup fields:

| Field Area | Bill / Fee | Rent |
| --- | --- | --- |
| Name | Bill name, required. | Rent/tenancy name, required. |
| Amount | Bill amount / invoice amount. | Rent amount. |
| Date / Period | Invoice date and due date. | Rent period and rent due date. |
| Frequency | One-off, monthly, bi-monthly, quarterly, yearly, or custom if enabled. | Usually monthly for rent; custom frequency if enabled. |
| Payee / Landlord | Name required where available; ID and phone optional unless category rules require them. | Landlord/payee name required where available; ID and phone optional unless category rules require them. |
| Account / Payout Details | Payer-entered or context-selected recipient name, receiving method, bank/provider, and destination identifier where applicable. | Payer-entered or context-selected landlord/payee name, receiving method, bank/provider, and destination identifier where applicable. |

QR scanning belongs inside `BILLS-ADD` and `BILLS-EVIDENCE-UPLOAD` as a setup and evidence-capture aid. It must not allow unsupported instant payment without evidence, verification, and payer authorization.

Account / Payout Details belong to the bill/rent context. A payer may enter a valid destination for a non-user payee. A payee creating a request may select one private profile from DOC-06B `RECEIVING-INFO`; the selected version is copied into the bill/rent/request context, and the payer must not browse the payee's other profiles. Editing or archiving the source profile must not change an existing bill/rent, accepted request, authorized payment, or payout snapshot.

Frequency supports due-date display, reminder defaults, bill/rent management, analytics, and payment-readiness UX. It must not be represented as automatic recurring payment, recurring card authorization, or recurring gateway submission unless a separate approved recurring payment model is later defined.

### 5.10 Evidence Sub-Route

Evidence is proof supporting a bill/rent/tenancy obligation. It is not itself an obligation, activity, or standalone user-facing card.

An accepted request may connect the parties and its evidence-backed context to the resulting obligation. A request is not required for this relationship: a payer-created bill/rent/tenancy obligation may link directly to evidence and proceed to payment and payout without payee acceptance where all applicable evidence, verification, risk, payout, compliance, and payer-authorization gates pass.

Core model:

| Item | Rule |
| --- | --- |
| Main object | Bill/rent record. |
| Supporting object | One active evidence set for the bill/rent record under normal operation. |
| Versioning | Evidence updates create new versions; the newest accepted version becomes active. |
| Previous evidence | Previous or archived evidence is hidden from normal bill/rent UI and retained under controlled records access. |
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
| Evidence exists | `View`, `Update`, `Archive`. |
| Evidence does not exist | `Upload`. |

`BILLS-EVIDENCE-UPLOAD` should support:

- upload file;
- take photo;
- scan QR;
- enter manually where permitted.

Upload/update flow:

1. User starts upload or update from `BILLS-EVIDENCE-DETAIL` or evidence step inside `BILLS-ADD`.
2. System captures evidence.
3. AI/OCR reads and classifies evidence where enabled.
4. System autofills extracted fields into the bill/rent record.
5. User reviews and corrects bill/rent details.
6. User submits.
7. System sets evidence status.
8. Bill/rent payment readiness updates based on evidence status and other gates.

Permitted evidence viewing and downloading within an authenticated session does not require an extra payment-passcode or step-up prompt solely because the document is opened or downloaded. Role, approved-purpose, masking, stale-session, and access-control rules still apply under DOC-15 and DOC-19.

Evidence archive behavior:

- archive hides evidence from normal bill/rent UI;
- archive must not hard-delete evidence from the database;
- archived evidence remains retained under DOC-15 and DOC-18;
- archived/previous evidence is retrievable from DOC-06B `ME-ROOT` through `ARCHIVED-EVIDENCE-LIST`, labelled `Archived Documents`; this route contains archived/previous evidence only and must not become a general archive for Bills, requests, instructions, or activities.

Evidence statuses:

| Evidence Status | Meaning |
| --- | --- |
| `Not Provided` | No active evidence exists. |
| `Pending Review` | Evidence uploaded, review not complete. |
| `Accepted` | Evidence accepted for current bill/rent purpose. |
| `Correction Needed` | User must correct extracted or entered fields. |
| `Update Needed` | Evidence expired, outdated, replaced, or insufficient. |
| `Rejected` | Evidence cannot support the bill/rent. |
| `Duplicate Suspected` | Evidence may be reused/duplicate and needs review. |
| `Archived` | Hidden from normal UI, retained in records/history. |

Bill/rent payment readiness statuses:

| Payment Readiness | Meaning |
| --- | --- |
| `Ready to Pay` | Evidence and required gates pass. |
| `Action Required` | User must fix evidence, details, payment setup, or another required item. |
| `Under Review` | System, admin, or risk review is pending. |

`Paid` / `Received` are payment-activity outcomes, not readiness states. `Archived` is obligation visibility, and `Due Soon` is a date-derived filter or label. None of these changes the request lifecycle.

Evidence-to-readiness mapping:

| Evidence Status | Bill/Rent Payment Readiness |
| --- | --- |
| `Not Provided` | `Action Required`. |
| `Pending Review` | `Under Review`. |
| `Accepted` | `Ready to Pay`, if other gates pass. |
| `Correction Needed` | `Action Required`. |
| `Update Needed` | `Action Required`. |
| `Rejected` | `Action Required`. |
| `Duplicate Suspected` | `Under Review` or `Action Required`, depending review rule. |
| `Archived` | `Action Required`, unless another active accepted evidence version exists. |

Evidence status and bill/rent readiness must be managed through system automation, AI/OCR classification, rules engine checks, admin/manual review, user correction, and lifecycle events. DOC-12 owns extraction, verification, duplicate/reused evidence, and evidence review logic. DOC-14 owns risk triggers. DOC-15 owns privacy, masking, retention, and access boundaries. DOC-18 owns final data objects, status taxonomy, audit events, and analytics. DOC-22 owns admin review and configuration workflow.

### 5.11 Reminder Route

Reminder routes must use specific route IDs:

- `BILLS-REMINDER-LIST` for the reminder management screen.
- `BILLS-REMINDER-DETAIL` for creating or editing one reminder.

`BILLS-REMINDER` may be used only as a shorthand discussion label. AI build documents should use the specific list/detail route ID so screens, sheets, and actions are not confused.

Reminder source type should be stored internally without overexposing technical labels to users. MVP source types should include system due-date reminder, user manual reminder, and user custom override reminder. Payment instruction action alerts are not ordinary Bills reminder records and should not appear in `BILLS-REMINDER-LIST`.

Every Bills reminder must have a `reminderID` and link to exactly one existing bill, fee, rent, tenancy, or obligation record ID. A reminder created from a bill/rent card or detail page should automatically inherit the linked record ID. A reminder created from `BILLS-REMINDER-LIST` through `+ Add Reminder` must first require the user to select an existing bill, fee, rent, tenancy, or obligation record. Free-floating reminders are not MVP scope.

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
- linked bill/rent name, category, and current readiness/status badge;
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
8. Delete or disable action where applicable.

Smart default values should be configurable in the admin dashboard under DOC-22:

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
| Evidence is expired, invalid, rejected, or requires review | Reminder remains valid; the linked bill/rent readiness changes to action-required. |

Reminder deletion should be supported from `BILLS-REMINDER-LIST`:

1. User long-presses a reminder card.
2. Screen enters selection mode and automatically selects the tapped card.
3. Checkboxes appear on reminder cards.
4. A bottom action bar slides up and stays fixed at the bottom area.
5. User may select multiple reminders.
6. Delete requires confirmation.
7. User-facing delete should be implemented as soft delete for audit, support, analytics, and abuse investigation.

User-created or custom reminder records may be deleted. System/default due-date reminders should normally be disabled rather than hard-deleted. Payment instruction action alerts are excluded from this deletion flow.

Due soon, overdue, evidence rejected, and payment-readiness action states belong primarily to the linked bill/rent card and detail page. Reminder cards should focus on reminder state such as next reminder date, reminder off, reminder expired, or custom reminder set.

DOC-08 owns notification IDs, channel matrix, templates, user preferences, retry behavior, and delivery logging. DOC-06B owns `INSTRUCTIONS-ROOT` and `INSTRUCTIONS-DETAIL` route shells. DOC-09 owns payment instruction mechanics and return-to-checkout behavior. DOC-15 owns sensitive-data display and masking. DOC-18 owns final schema, event taxonomy, lineage, and analytics definitions.

### 5.12 Evidence Structure and UX

Evidence handling must distinguish the obligation, the relationship/contract, and the source evidence.

Working conceptual structure:

```text
Customer profile
-> Obligation record
-> Contract / relationship record where applicable
-> Evidence source record
-> Extracted, corrected, verified, and final evidence fields
-> Payment activity
-> Receipt / proof
```

For bills, invoices, and fees, the evidence usually supports a specific obligation or payment cycle.

For rent, tenancy evidence usually supports a contract or relationship. Rent obligations may then be generated from that tenancy context. Tenancy-related evidence may include tenancy agreement, stamp duty document, CR109, rent demand, property management notice, HKHA tenancy card, carpark invoice, or other approved rent-supporting evidence. Exact evidence categories, fields, review thresholds, and schemas belong in DOC-12 and DOC-18.

The Bills route should therefore support evidence source detection or selection inside `BILLS-EVIDENCE-UPLOAD` when the category or document type is not obvious, instead of assuming every rent flow equals tenancy agreement and every bill flow equals invoice.

### 5.13 Payer-Created and Payee-Created Logic

| Scenario | UX Rule | Linking Rule |
| --- | --- | --- |
| Payer creates bill/rent for own payment | Payee acceptance is not required before the payer may proceed, provided required evidence, verification, risk, payout, and authorization gates pass. | If the payee is also a PayPlus user, optional linking may be initiated or accepted through an approved user action. |
| Payee creates bill/rent/request for payer | Payer acceptance is required after verification and before payment authorization. | The payer is linked only after in-app acceptance or approved invitation/deeplink flow. |
| Both parties are PayPlus users | Both sides may view the same linked bill, tenancy, request, or payment context after accepted linking, subject to role-based permissions. | Linking must be user-initiated or user-accepted; automatic user-to-user matching is not allowed as a UX assumption. |
| Payee is not a PayPlus user | Payer may still pay an approved evidence-backed obligation to a valid payee record or payout destination. | The payee may remain a non-user payee record unless invited and onboarded later. |

Phone number, user ID, app link, WhatsApp deeplink, QR code, or other approved invitation mechanisms remain to be defined. Search, invitation, and acceptance design must follow DOC-15 privacy and DOC-19 security controls.

Destination rules:

- a payee-created request must select a destination before sending;
- before payer acceptance, the payee may change the destination and send the latest request version;
- after payer acceptance, a payee destination change requires a new request and new bill/rent record, which may link to the same evidence; the prior record is not auto-archived;
- a payer-created bill/rent with no linked PayPlus payee may change destination without a request or payee handling, subject to normal recipient, evidence, risk, payout, compliance, and authorization checks;
- where the bill/rent is linked to a PayPlus payee, a payer destination change notifies that payee but does not require payee approval;
- a payer-selected destination different from an accepted payee-created request must remain a separate bill/payment-context snapshot and must not rewrite the accepted request;
- the bill/rent detail should make the effective destination and its source clear to the payer before payment;
- any destination change after payment authorization requires renewed payer authorization under DOC-09;
- a linked payee may be offered a controlled option to review and save a payer-selected destination into `RECEIVING-INFO`, but this does not delay payout and does not auto-approve that profile.

When a user opens `BILLS-ADD` from DOC-06B `REQUESTS-NEW`, `BILLS-ADD` owns the bill/rent/evidence setup steps and must preserve the request-creation context. Successful setup returns the created context to `REQUESTS-NEW`; cancellation returns without creating or selecting a new context. If a user opens `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT` from `REQUESTS-DETAIL`, save/back behavior should return to `REQUESTS-DETAIL` and refresh the linked request summary. If a user opens linked bill/rent detail from `REQUESTS-NEW` review, save/back behavior should return to `REQUESTS-NEW`.

### 5.14 Action-Required UX

Action-required states must be visible before the user attempts payment where possible.

Examples:

- evidence pending verification;
- evidence not provided;
- evidence rejected;
- evidence expired;
- missing required field;
- material mismatch between user-entered and extracted evidence data;
- duplicate or reused evidence warning;
- payee/payout detail requires review;
- payment instruction requires user action;
- reminder/action deadline is approaching.

The card should show the payment readiness badge and a clear next action. Evidence-specific actions should appear inside the bill/rent detail evidence section, not as multiple evidence buttons on the card. The detail page should show the affected section, the rejected or missing field where appropriate, an `Upload`, `Update`, or `Fix` evidence action, and cautious helper text below the affected field. Exact user-facing wording belongs in DOC-07 and DOC-08.

### 5.15 Data and Intelligence Signals

Bills route interactions should produce structured events or signals for later DOC-18 specification, including:

- route opened and view selected;
- filter selected;
- obligation card viewed;
- detail opened;
- evidence source selected;
- input method selected: upload, photo, QR scan, or manual entry;
- extracted field confirmed or corrected;
- evidence upload or update started;
- evidence submitted;
- evidence status changed;
- evidence archived;
- evidence verification outcome displayed;
- bill/rent readiness changed due to evidence;
- action-required state displayed;
- action-required state resolved;
- payer-created record created;
- payee-created request received and accepted/rejected;
- user-initiated participant invitation sent;
- participant invitation accepted or declined;
- payment started from card or detail page;
- reminder created, edited, disabled, deleted, fired, opened, ignored/dismissed, or followed by payment start;
- record archived;
- bill/rent activity timeline opened;
- activity entry detail opened;
- receipt or payment proof downloaded;
- payment, payout/transfer, failure, return, refund, or reversal status displayed in activity.

These events should support product analytics, operational monitoring, risk review, support investigation, and future approved AI/payment-intelligence use under DOC-15 and DOC-18. They must not create automatic user-to-user matching or overexpose sensitive evidence data.

---

---

## 6. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06C-001 | Which exceptional payer-created categories, if any, require payee adoption before payment can proceed despite the default rule that payer-created payments do not require payee acceptance? | Product / Operations / Risk | Open |
| OQ-06C-002 | Which rent and tenancy journey controls must be ready before initial launch enablement? | Product / Legal / Risk | Open |
| OQ-06C-003 | What final user-initiated payee linking or invitation mechanism should be used: user ID, phone search, app link, WhatsApp deeplink, QR code, or another approved flow? | Product / Privacy / Engineering | Open |
| OQ-06C-004 | What exact Bills tab visual layout, card density, status badge style, action-required treatment, and field masking rules should be used? | Product / Design / Privacy | Open |
| OQ-06C-005 | What evidence source selection UI should be used when bill, invoice, tenancy, rent demand, contract, and supporting evidence types are not obvious from upload/OCR? | Product / Design / Risk | Open |
| OQ-06C-006 | What exact request-delivery and Remind Payer UX should apply inside BILLS-RECEIVE, including resend limits, payer acceptance states, wording, and notification-channel rules? | Product / Design / Operations | Open |

## 7. Version History

| Version | Date | Summary |
| --- | --- | --- |
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
