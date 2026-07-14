---
document_id: DOC-06B
title: Navigation, IA & Route Taxonomy
version: 0.1.16
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - Growth Lead
  - Privacy Lead
  - Operations Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-07-14
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06B - Navigation, IA & Route Taxonomy

## 1. Purpose

DOC-06B governs PayPlus global app navigation, information architecture, dashboard placement, route taxonomy, screen/component/action ID standards, and route completion tracking.

## 2. Scope Boundary

DOC-06B owns how app areas, routes, screens, views, sheets, components, actions, flows, and system touchpoints are named, grouped, opened, and routed at the product UX level.

DOC-06B does not own detailed Bills/rent/tenancy route behavior, which belongs to DOC-06C. It does not own checkout processing, payment instruction mechanics, evidence verification logic, data schema, notification delivery rules, privacy implementation, or admin workflow detail.

When drafting global non-Bills routes, DOC-06B should define the human-readable route-level UX baseline: route ID, entry points, destination relationships, user purpose, major sections, core visible fields and actions, view/filter structure, return behavior, and handoff rules. Exact visual styling and detailed lifecycle, status, payment, evidence, risk, notification, privacy, data, or admin logic remain in their owning documents and should be referenced rather than duplicated.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Bottom navigation | Partially defined | Home, Bills, Pay+, Offers, Me baseline exists. |
| Home dashboard | Partially defined | Section order exists; final card and visual details remain open. |
| Pay+ action sheet | Partially defined | Working action set exists; exact order and disabled states remain open. |
| Shortcut grid | Partially defined | Eight MVP shortcuts exist; detailed More/overflow UX remains open. |
| Route taxonomy and ID standard | Initial baseline | Stable IDs should be assigned progressively. |
| Non-Bills route registry | Partially defined | Requests, Instructions, Payment Profile, Activity, and Receipts & Statements have route-level working baselines; Offers, Me, Referral, and More need future drafting. |

---

## 4. Route Object Taxonomy

| Type | Definition |
| --- | --- |
| Area | Broad product area such as Home, Bills, Offers, Me, Requests, Instructions, Receipts, Cards, or Support. |
| Route | Navigable destination or deep-link target. |
| Screen | Full-page UI view rendered inside a route. |
| Tab / View | Role-aware, state-aware, or filtered view inside a screen. |
| Sheet / Modal | Temporary focused interaction, such as the Pay+ action sheet or confirmation modal. |
| Component | Reusable UI unit such as a card, badge, action row, timeline entry, or carousel card. |
| Flow | Ordered multi-step journey that may span routes, screens, sheets, and system touchpoints. |
| Action | User-triggered behavior such as Pay, Request, Remind Payer, Upload Evidence, Set Reminder, or Archive. |
| System Touchpoint | Automated validation, notification, audit event, risk routing, status update, OCR/autofill step, or integration handoff. |

### 4.1 Route Registry Table Standard

Route and screen registry tables should use this structure where practical.

| Column | Requirement |
| --- | --- |
| ID | Stable route, screen, component, or action ID. |
| Type | Area, Route, Screen, Tab/View, Sheet/Modal, Component, Flow, Action, or System Touchpoint. |
| Area | Parent product area. |
| Role | Payer, payee, admin, system, or mixed. |
| Opened By | Navigation element, action, notification, deep link, or system state. |
| User Purpose | Why the user is here. |
| Allowed Actions | Actions available from this object. |
| System Touchpoints | Major system actions triggered or displayed. |
| Owning Doc | Formal document owning detailed behavior. |
| Related IDs | Related requirements, states, events, notifications, or tests. |

### 4.2 Stable ID Standard

| Artifact | Pattern | Example |
| --- | --- | --- |
| UX requirement | UXREQ-06B-001 | UXREQ-06B-001 |
| Route | ROUTE-06B-{AREA} | ROUTE-06B-HOME |
| Screen | SCREEN-06B-{NAME} | SCREEN-06B-HOME-DASHBOARD |
| View | VIEW-06B-{NAME} | VIEW-06B-OFFERS-HUB |
| Sheet / Modal | SHEET-06B-{NAME} | SHEET-06B-PAYPLUS-ACTION |
| Component | COMP-06B-{NAME} | COMP-06B-SHORTCUT-GRID |
| User action | ACT-06B-{NAME}-{NNN} | ACT-06B-OPEN-PAYPLUS-001 |
| Event signal | EVT-06B-{NAME} | EVT-06B-SHORTCUT-TAPPED |
| Open question | OQ-06B-001 | OQ-06B-001 |

Stable IDs may be assigned progressively. Shorthand labels may remain in discussion and diagrams, but build-execution materials should use stable IDs when available.

### 4.3 Route Ownership Rule

Each route must have one primary owner. DOC-06B may list related documents, but related documents must not become duplicate owners of the same detailed route behavior.

| Route Work Item | DOC-06B Owns | Reference / Handoff Owner |
| --- | --- | --- |
| Route shell | Route ID, route purpose, entry points, destination relationship, major sections, empty state, and high-level allowed actions. | N/A |
| Request lifecycle | Route entry and where request lists open. | DOC-06A owns lifecycle, status meaning, acceptance, rejection, expiry, cancellation, and any later clarification/dispute extension if enabled. |
| Bills/rent request implementation | Global shortcut and route relationship. | DOC-06C owns `BILLS-PAY`, `BILLS-RECEIVE`, cards, details, request/remind-payer actions, and Bills-route handoff. |
| Payment/checkout route | Entry and return/handoff expectations only. | DOC-09 owns checkout screen behavior, payment instruction, funding, authorization, and payment states. |
| Payment Profile route | Route shell, entry points, major screens, card/profile management purpose, and route handoff. | DOC-09 owns checkout selection, allocation, authorization, funding, and payment states. DOC-19 owns tokenization and security mechanics. |
| Notification destination | Route target for a notification tap. | DOC-08 owns notification IDs, channels, templates, preferences, and delivery rules. |
| Data/intelligence signal | Signal existence at route level. | DOC-18 owns event taxonomy, schema, lineage, analytics, and reporting. |

---

## 5. Logged-in Home Dashboard and Navigation IA

### 5.1 Design Intent

The logged-in Home Dashboard is the default landing screen after login.

It must be task-first. It should prioritize urgent user actions, payment-related obligations, request status, payment instructions, and recent payment records before promotional discovery.

The dashboard is not a marketing page. Promotions, partner offers, hot offers, PayPlus events, and feature announcements may appear only through controlled placements and must not obscure payment tasks or status visibility.

This section defines the designated dashboard flow and layout baseline for MVP discussion. It is not the finalized UI design, visual design, component specification, or exact route-level screen specification. Exact UI details remain subject to later DOC-06B refinement and future design/specification work.

Visual references:

- `docs/diagrams/payplus-home-dashboard-mvp-wireframe.svg` is a companion wireframe for this section. It supports human and AI understanding of layout hierarchy but does not override this document.
- `docs/diagrams/payplus-app-route-entry-map.md` is a Mermaid route-entry map showing bottom navigation, Pay+ actions, the eight dashboard shortcuts, and major route handoffs. It is a discussion and alignment aid, not final UI design.

---

### 5.2 Bottom Navigation

MVP bottom navigation should use five primary destinations.

| Nav Item | Definition | Route Relationship | Current Status |
| --- | --- | --- | --- |
| Home | Default task-first dashboard. | Opens Home Dashboard. | Discussion baseline |
| Bills | Bill, fee, rent, tenancy, and obligation record management area. | Opens Bills area covering saved bill/rent/tenancy records and their DOC-06C sub-routes. Requests, instructions, receipts, cards, referral, and More remain separate management routes or shortcut destinations unless explicitly embedded as contextual handoffs. | Discussion baseline |
| Pay+ | Central payment and request action. | Opens a slide-up action sheet for payment, setup, continuation, and request-payment actions. Exact visual UI and final ordering remain to be finalized. | Working baseline |
| Offers | Full promotion discovery area. | Opens Offers Hub covering hot offers, card partner offers, PayPlus campaigns, coupon/voucher library, referral, and What's New. Exact route IA remains to be finalized. | Discussion baseline |
| Me | Account and user control area. | Opens profile, settings, security, notifications, privacy, support, cards/payment methods, and account controls. Exact route IA remains to be finalized. | Discussion baseline |

`Pay+` should be visually treated as the primary center action in the bottom navigation.

---

### 5.3 Pay+ Action Sheet

Tapping `Pay+` should open a slide-up action sheet instead of routing directly to one screen.

The Pay+ action sheet should contain user-friendly actions for starting or continuing the core PayPlus journey. It should not expose internal implementation terms such as capture layer, funding leg, or verification layer to users. User-facing labels such as `Payment Instructions` or `付款指示` may be used where the product means a pending or future payment action.

Working baseline Pay+ actions:

- Pay a Bill / Fee;
- Pay Rent;
- Add Bill / Rent;
- Continue Payment;
- Request Payment.

`Request Payment` should appear by default for all users, unless the request feature/module is disabled or the account is restricted. A user may be both payer and payee, such as a landlord who is also a renter elsewhere. `Request Payment` opens `REQUESTS-NEW` and must link to an evidence-backed bill, fee, rent, tenancy, invoice, or approved obligation before sending.

`Add Bill / Rent` should include scan QR, upload bill/invoice/tenancy/evidence, and manual entry as input methods inside the setup flow. QR or upload should not be a standalone Pay+ payment action because PayPlus must remain evidence-backed and must not behave as generic QR instant payment.

`Continue Payment` should cover pending payment instructions, unfinished split-card payments, failed or retry payment legs, and interrupted checkout only where an eligible saved or incomplete payment instruction exists.

The Pay+ action sheet must avoid creating wallet, stored-value, cashout, unsupported P2P, or automatic recurring-payment behavior.

Pay+ actions may start or continue a user journey, but must not bypass evidence capture, bill/rent setup, payee validation, risk checks, authorization, fee calculation, or payment instruction rules.

Exact visual layout, button order, empty states, disabled states, eligibility copy, and final action limits remain open.

---

### 5.4 Home Dashboard Section Order

The Home Dashboard should use the following MVP section order.

| Order | Section | Definition | Display Rule | Route Relationship |
| ---: | --- | --- | --- | --- |
| 1 | Header | Greets the user and provides quick access to high-priority utilities. | Always shown. | Inbox and coupon/voucher library icons route to their respective screens. |
| 2 | Important Notice / Action Required | Combined swipeable section for urgent actions, account messages, system messages, announcements, late handling from payer/payee, expiring tenancies, and other important updates. | Disappears if empty. User may collapse with a close button. Eligible item types are initially defined here and may be expanded later. | Each card routes to the relevant task, detail, or message route. |
| 3 | Shortcut Grid | Operational shortcuts for common management tasks. Must not duplicate Pay+ direct payment-start actions. | MVP displays 8 shortcuts. Shortcut set, default order, visibility, and enablement must be configurable. | Each shortcut routes to its related management area. |
| 4 | Featured / What's New / Hot Offer | One combined carousel for approved PayPlus announcements, partner campaigns, feature updates, hot offers, and service events. | Must be admin-controllable. Use one combined carousel at this stage. | Routes to Offers Hub, offer detail, announcement detail, or feature route. |
| 5 | Upcoming Bills / Rent | Summary of upcoming bills, fees, rent, tenancy obligations, due reminders, and related next actions. | Show when active or saved obligations exist. Detailed card fields may be refined later. | Routes to Bills area or the specific bill/tenancy detail. |
| 6 | Recent Activity | Limited list of recent transactions and status records. | Show recent items only, capped by dashboard display rules. | Arrow or View More routes to Recent Activity detail page. |

Dashboard section order may be refined later only through explicit design review. This baseline intentionally places the Featured / What's New / Hot Offer carousel below shortcuts and above Upcoming Bills / Rent.

---

### 5.5 Header Utilities

| Element | Definition | Route Relationship |
| --- | --- | --- |
| Greeting | User recognition area. | No route required, or profile route if tapped. |
| Inbox icon | Notifications, messages, payment alerts, request updates, support replies, system notices, and announcements. | Notification / Inbox route. Request-related inbox items may route to `REQUESTS-ROOT`, `REQUESTS-DETAIL`, or the linked Bills/rent context depending on item type. |
| Coupon icon | Shortcut to user's available coupon/voucher library. | Coupon / Voucher Library route. |

---

### 5.6 Shortcut Grid

The shortcut grid provides quick access to common non-payment-start tasks.

Shortcut grid items are entry points, not independent feature owners. Each shortcut should open or deep-link to the relevant owning route, screen, sheet, or management area. The owning document for the destination continues to govern detailed behavior.

MVP shortcut grid:

| Shortcut | Definition | Route Relationship |
| --- | --- | --- |
| Requests | Requests that ask another party to accept, link to, review, or reject a bill, rent, tenancy, fee, invoice, or approved obligation context. A request is not a payment. | Opens `REQUESTS-ROOT`. |
| Instructions | Payment instructions / 付款指示 for pending pay-later setups, incomplete split-card payments, pending funding legs, expired instructions, and action-required instruction items. | Opens `INSTRUCTIONS-ROOT`. |
| Bills & Tenancies | Saved bills, fee records, rent records, tenancy records, evidence status, due dates, and obligation details. | Opens `BILLS-ROOT`. |
| Receipts | Payment receipts and statements. Proof of payment remains available from relevant Activity contexts for MVP. | Opens `RECEIPTS-ROOT`. |
| Reminders | User-set due reminders for bills, rent, tenancy obligations, and manual reminders. | Opens `BILLS-REMINDER-LIST`. |
| Cards | Payment Profile route for managing tokenized cards and saved split-card profiles. The shortcut is an entry point, not checkout. | Opens `PAYMENT-PROFILE-ROOT`. |
| Referral | Referral / MGM entry point and referral reward status where enabled. | Opens the future Referral route and may also link to Offers Hub referral content. |
| More | Opens remaining or secondary shortcuts and services. | Opens future More Shortcuts / Services route or sheet. |

Support should not be part of the initial eight dashboard shortcuts. Support remains accessible through `Me`, issue-specific status screens, and/or `More` if enabled.

Shortcut display must support:

- admin-managed default shortcut set;
- admin-managed default order;
- adding shortcuts;
- disabling shortcuts;
- hiding shortcuts by feature, module, category, user type, eligibility, or launch phase;
- user-managed shortcut display order;
- user-managed shortcut visibility where allowed;
- user setting overriding the system default;
- restore-to-default behavior.

Detailed admin configuration workflow belongs in DOC-22. User preference, visibility, and privacy/data handling belong in DOC-15 and DOC-18.

---

### 5.7 Featured / What's New / Hot Offer Carousel

The dashboard should use one combined promotional and announcement carousel.

The carousel may include:

- PayPlus feature updates;
- partner announcements;
- card partner offers;
- hot offers;
- service events;
- category launch announcements;
- approved campaigns;
- important non-urgent announcements.

The carousel must be admin-controllable, including placement, priority, start/end date, targeting, enable/disable, approval status, and audit log.

Detailed promotion eligibility, coupon/voucher logic, reward entitlement, campaign budget, and reversal logic belong in DOC-13. Detailed admin placement control belongs in DOC-22. Personalization and marketing data handling belong in DOC-15.

---

### 5.8 Upcoming Bills / Rent

The Upcoming Bills / Rent section should summarize the user's next relevant obligations.

Initial dashboard card information may include:

- biller, payee, landlord, or obligation name;
- category;
- amount;
- due date or rent period;
- payment status;
- evidence status where relevant;
- next action.

Exact card layout, maximum visible items, empty state, and filtering rules remain open and should be refined in later DOC-06B/DOC-06C route-level work.

---

### 5.9 Recent Activity

The Recent Activity section should display a capped list of recent transactions and status records.

Activity is the event or lifecycle view of what happened in the user account. Receipt is a transaction confirmation record for a completed transaction. Statement is a periodic or account-level summary record.

Dashboard recent activity items should show:

- date;
- item;
- action;
- amount;
- status.

The section should include a button or arrow to the Recent Activity detail page.

User-facing activity statuses must follow `docs/traceability/status-display-reference-matrix.md` so dashboard Recent Activity, global Activity, Bills activity, checkout result, receipts, statements, notifications, and future admin views do not invent conflicting labels for the same system/domain status.

Detailed receipt content, retention, and notification linkage belong in DOC-08, DOC-11, DOC-15, and DOC-18.

---

### 5.10 Route IA Workplan and Placeholder Titles

The DOC-06 family must next define what users see, what buttons exist, what each button does, and how route areas interact. The following titles are intentionally preserved as the working map so the route-level UI discussion does not lose scope.

| Area | Purpose of Future DOC-06 Family Detail | Current Status |
| --- | --- | --- |
| Bottom Navigation Route Map | Define how `Home`, `Bills`, `Pay+`, `Offers`, and `Me` relate to top-level routes and deep links. | Title preserved / not finalized |
| Pay+ Action Sheet Detail | Define final label order, empty states, disabled states, permission rules, and route destinations for the working baseline actions. | Working baseline / not finalized |
| Bills Tab IA | Define bill, fee, rent, tenancy, evidence, reminder, payment history, and setup sections under the Bills route. | Working baseline / not finalized |
| Offers Hub IA | Define offer discovery, hot offers, card partner offers, coupon/voucher library, referral, What's New, and campaign detail routes. | Title preserved / not finalized |
| Me Area IA | Define account, security, privacy, notification preferences, support, cards/payment methods, and user control routes. | Title preserved / not finalized |
| More Shortcuts IA | Define secondary shortcuts and services not shown in the first eight dashboard shortcuts. | Title preserved / not finalized |
| Requests Route | Define standalone Requests route shell, creation flow, entry points, list grouping, high-level actions, and handoff to request lifecycle or Bills/rent request detail. The route is for party-linking and request management, not payment processing. | Working baseline / not finalized |
| Instructions Route | Define payment instruction / 付款指示 route shell, pending versus incomplete instruction display, edit boundaries, cancellation/archive behavior, and checkout handoff. | Working baseline / not finalized |
| Bills & Tenancies Route | Define saved obligation list, tenancy detail, evidence status, payee/landlord detail, due dates, and linked payment actions. | Title preserved / not finalized |
| Activity Route | Define global account-level financial activity route shell, including role-aware `Paid` / `Received` views, single-entry transaction lifecycle behavior, and status-display matrix handoff. | Route shell defined / not final UI |
| Receipts & Statements Route | Define the searchable receipt/statement list, direct download, shared PDF preview, return behavior, and re-issue handoff. | Root and preview behavior defined / not final PDF design |
| Reminders Route | Define due reminders, user-set reminders, notification settings, and reminder destinations. | Title preserved / not finalized |
| Payment Profile Route | Define tokenized card management, saved split-card profile management, card status, default card, profile action-required behavior, and checkout/instruction handoff. | Route shell defined / not final UI |
| Referral Route | Define referral entry, invitation link, progress, reward status, and relationship with Offers Hub. | Title preserved / not finalized |
| Admin-Configurable UI Marker List | Mark app UI elements that require admin configuration later without drafting admin UI in DOC-06. | Title preserved / DOC-22 owns admin UI |

App UI elements that currently require admin configuration markers include Pay+ action visibility, shortcut visibility/order/defaults, Featured / What's New / Hot Offer carousel placement, Important Notice / Action Required item types, feature/module enablement, request-payment availability, and route-level gating by user type, category, launch phase, risk state, or compliance restriction.

---

---

### 5.11 Requests Route Shell

DOC-06B owns the standalone Requests route shell. DOC-06A owns request lifecycle, status meaning, acceptance, rejection, expiry, and cancellation rules. DOC-06C owns Bills/rent/tenancy-specific implementation when the request is linked to a bill, fee, rent, tenancy, invoice, or obligation record. DOC-08 owns notification routing and delivery rules.

#### 5.11.1 Route Definition

| Item | Requirement |
| --- | --- |
| Route label | Requests |
| Working route ID | `REQUESTS-ROOT` |
| Stable route ID | `ROUTE-06B-REQUESTS` |
| Purpose | Let users create, view, manage, and respond to requests that connect parties to an evidence-backed bill, fee, rent, tenancy, invoice, or approved obligation context. |
| Boundary | A request is not a payment. The route must not authorize, process, capture, settle, or complete payment. |
| Default behavior | Open `Received` unless the user's last selected Requests view is available. Action-required received requests should be visually prioritized inside `Received`, not treated as a separate route. |

#### 5.11.2 Request Definition

A request is a payer-created or payee-created acceptance/linking request sent to the other party for an evidence-backed bill, fee, rent, tenancy, invoice, or approved obligation context.

Requests do not equal payment. A payer may pay a valid payee or payout destination without payee acceptance where evidence, verification, risk, payout, and authorization gates pass. If the payer-created record is not accepted or linked by a PayPlus payee user, the payee should not receive in-app visibility or in-app notifications for that record. A payee-created request requires payer acceptance before the payer can authorize payment from that request.

MVP request types include:

| Request Type | Sender | Recipient | Meaning |
| --- | --- | --- | --- |
| Payee-created acceptance request | Payee, landlord, biller, or recipient | Payer | Recipient is asked to accept or reject an evidence-backed bill/rent/fee request before payment can proceed from that request. |
| Payer-created linking request | Payer | Payee, landlord, biller, or recipient | Recipient is asked to accept linkage to a payer-created evidence-backed bill/rent/fee context for two-sided visibility and communication. |
| Request reminder | Sender or system | Pending recipient | Recipient is reminded to act on an existing request. A reminder must not create a new request. |

Accepted requests link the parties to the accepted context and may enable later payment readiness where all other gates pass. Acceptance must not be treated as payment authorization.

#### 5.11.3 Request Status and Display Labels

The system may use internal request states, but user-facing labels should be role-aware.

| Underlying State | Sender Sees | Receiver Sees | Visibility Rule |
| --- | --- | --- | --- |
| Draft | Draft | Not visible | Sender can continue, edit, or discard. |
| Pending evidence verification | Waiting for verification | Not visible | Request must not be delivered until evidence is verified. |
| Pending receiver action | Reviewing | Awaiting | Receiver can review and act. |
| Accepted | Accepted | Accepted | Parties are linked to the accepted context. |
| Rejected | Rejected | Rejected | Rejection reason should be retained where provided. |
| Expired | Expired | Expired | Sender may resend where allowed. |
| Cancelled | Cancelled | Cancelled where already visible | Sender cancelled the request. |

`Archived` is a visibility state, not a request status.

#### 5.11.4 Entry Points

| Entry Point | Route Behavior |
| --- | --- |
| Dashboard `Requests` shortcut | Opens `REQUESTS-ROOT`. |
| Header Inbox icon | Opens Inbox first; request-related inbox items may route to `REQUESTS-ROOT`, `REQUESTS-DETAIL`, or linked Bills/rent context depending on item type. |
| Request notification | Routes to `REQUESTS-DETAIL` by default when a specific request exists. It may route to `REQUESTS-ROOT`, `BILLS-PAY`, `BILLS-RECEIVE`, or linked bill/rent detail only where DOC-08 routing rules require it. |
| `+ Create Request` in `REQUESTS-ROOT` | Opens `REQUESTS-NEW`. |
| Pay+ `Request Payment` | Opens `REQUESTS-NEW`. It must not create an open money request or bypass evidence-backed context setup. |
| `Request` action on Bills/rent card or detail | Creates, sends, resends, or updates a request record for the selected verified context. It does not open `REQUESTS-ROOT` by default. |
| `Remind Payer` action on Bills/rent card or detail | Creates or sends a request reminder event against the existing request; it does not create a payment action or a new request. |
| App link, WhatsApp deeplink, QR code, or approved channel | Opens onboarding/login first where required, then routes to `REQUESTS-DETAIL` for the relevant request context. |

#### 5.11.5 `REQUESTS-ROOT` List Screen

`REQUESTS-ROOT` is the request inbox and management list. It should not show payment actions, evidence editing actions, or bill/rent edit actions directly.

Recommended screen order:

1. Header: `Requests`.
2. Top-right `+ Create Request` action.
3. Search and filter controls.
4. Segmented views: `Received`, `Sent`, `Archived`.
5. Request cards.
6. Empty state.

`Received`, `Sent`, and `Archived` are views or filters inside `REQUESTS-ROOT`, not separate routes. Exact visual design, filter density, and sort options remain open.

#### 5.11.6 Request Card

A request card should show enough information for the user to identify the request without exposing unnecessary sensitive details.

MVP card fields:

- received date or sent date;
- linked bill, fee, rent, or tenancy name;
- counterparty name;
- category: bill, fee, or rent;
- amount where applicable;
- payment due date where applicable;
- request expiry date where applicable;
- request status using role-aware display labels;
- primary action label: `Review` for received requests and `View` for sent requests.

Payment due date and request expiry date are separate fields. Payment due date relates to the underlying bill/rent/fee obligation. Request expiry date relates to the acceptance/linking request.

Sensitive fields must follow DOC-15 masking and role-based display rules. Detailed linked bill/rent fields remain in DOC-06C.

Card-level material actions such as accept, reject, cancel, resend, or remind should not appear directly on the card. Selecting a request card opens `REQUESTS-DETAIL`.

#### 5.11.7 Request Detail Screen

`REQUESTS-DETAIL` is its own DOC-06B screen. It must not be replaced by the linked DOC-06C bill/rent detail screen, because the request is a party-linking and request-management object, not the bill/rent record itself and not a payment.

| Item | Requirement |
| --- | --- |
| Working screen ID | `REQUESTS-DETAIL` |
| Stable screen ID | `SCREEN-06B-REQUESTS-DETAIL` |
| Purpose | Let the user understand, respond to, or manage one request before opening any linked bill/rent/tenancy context. |
| Boundary | The screen manages request status and request actions only. Payment authorization, checkout, evidence editing, and bill/rent record maintenance remain in the owning routes. |
| Linked-context handoff | If a linked bill/rent/tenancy exists, show a clear button such as `View Bill Detail`, `View Rent Detail`, or `View Tenancy`. That button opens the relevant DOC-06C detail route. |
| Return behavior | If the user opens DOC-06C bill/rent detail from `REQUESTS-DETAIL`, editing, saving, or backing out should return the user to `REQUESTS-DETAIL` and refresh the request summary. |
| Payment handoff | If the linked context is payment-ready, the screen may show a handoff to the relevant payment entry point, but payment flow remains governed by DOC-09 and the related DOC-06C route. |

Recommended detail screen order:

1. Status header: request status, direction, request expiry date, and payment due date where relevant.
2. Request summary: category, sender or recipient, linked bill/rent/tenancy name, amount, and message/note.
3. Linked context section: `View Bill Detail`, `View Rent Detail`, or `View Tenancy`.
4. Action area.
5. Request activity.
6. Secondary archive action where allowed.

Role-aware detail actions:

| User Context | Primary Actions |
| --- | --- |
| Recipient / received pending request | Accept, reject with reason, open linked bill/rent detail where available. |
| Sender / draft request | Send, edit, cancel. |
| Sender / waiting for verification | View, edit where allowed, cancel. |
| Sender / pending receiver action | View, remind, cancel, share where allowed. |
| Sender / rejected or expired request | Edit, resend, cancel or archive where allowed. |
| Accepted request | View details, archive where allowed. |
| Archived request | Restore where allowed, view retained request detail subject to DOC-15 visibility and retention rules. |

`Remind` must create a notification/event against the existing request, not a new request. Reminder limits, cooldowns, expiry, escalation wording, and channel eligibility belong to DOC-08 and DOC-22.

Request activity may show system-visible request events such as created, submitted for verification, verified and sent, viewed, reminded, accepted, rejected with reason, expired, cancelled, archived, or restored.

#### 5.11.8 `REQUESTS-NEW` Creation Flow

`REQUESTS-NEW` is the controlled request creation flow. It may be opened from the `+ Create Request` action in `REQUESTS-ROOT`, Pay+ `Request Payment`, or an approved Bills/rent request action.

The flow must not create an open money request. It must link to an evidence-backed bill, fee, rent, tenancy, invoice, or approved obligation before sending. It must not perform payment quote, checkout, authorization, funding, settlement, payout, or refund actions.

| Field | Requirement |
| --- | --- |
| Working route ID | `REQUESTS-NEW` |
| Stable screen ID | `SCREEN-06B-REQUESTS-NEW` |
| Route type | Controlled creation flow / screen group |
| Primary owner | DOC-06B |
| Linked owner | DOC-06C owns `BILLS-ADD` and Bills/rent detail handoff. DOC-08 owns notification and delivery-channel rules. DOC-12 owns evidence verification. DOC-15 owns privacy and counterparty lookup boundaries. |
| Primary user goal | Create a request that asks another party to accept or link to an eligible evidence-backed obligation context. |
| Boundary | A request is not a payment. This route prepares and sends the request only after the required evidence gate passes. |

The route should use the following section order:

| Order | Section | What User Sees / Does | Route Behavior |
| ---: | --- | --- | --- |
| 1 | Start Request | Header `Create Request`; short context that the request must link to a bill, fee, or rent item. | Preserve entry source for return behavior and analytics. |
| 2 | Category and Direction | Category selection: bill, fee, or rent. Direction should be inferred where possible from role and entry source. | Payee-to-payer requires payer acceptance before payment from that request. Payer-to-payee is for optional linking/adoption unless a gate requires payee action. |
| 3 | Linked Context | Select existing bill/rent/tenancy context, or create a new one. | Existing context stays in `REQUESTS-NEW`. New context opens `BILLS-ADD`; completion returns to `REQUESTS-NEW` with the created context selected. |
| 4 | Linked Detail Review | Compact summary: name, category, amount, due date, counterparty/payee/payer where applicable, evidence status, and readiness/status badge. | If evidence is missing, rejected, expired, or action-required, route to the relevant DOC-06C evidence/setup path before submission. |
| 5 | Counterparty and Delivery | Select counterparty by PayPlus user ID or phone-number identifier; add optional note; select allowed delivery method where available. | Lookup must be privacy-safe. Delivery options may include in-app, app link, WhatsApp deeplink, QR code, or approved channel. |
| 6 | Review and Submit | Final review of request summary, linked context, receiver, delivery method, expiry/due information where applicable, and notices. | Primary CTA should be `Submit and send after verification`. If evidence is already accepted, the system may send immediately. |

Counterparty lookup rules:

- lookup may use PayPlus user ID or phone-number identifier;
- lookup should confirm that a potential receiver exists only with minimal, privacy-safe display;
- lookup must not expose unnecessary account, KYC/KYB, evidence, payment, risk, or relationship data before acceptance;
- if no PayPlus user is found or the receiver is not onboarded, the sender may use an approved share/invitation method where enabled;
- final privacy, masking, and authentication controls belong to DOC-15 and DOC-19.

Evidence gate and send rules:

- the request must not be sent to the receiver before linked evidence is verified or approved by exception;
- the receiver must not be notified or shown the request while evidence verification is pending;
- if evidence is already accepted, the request may be sent immediately after user submission;
- if evidence becomes accepted after submission, the system should send the request automatically using the approved delivery method;
- if evidence is rejected or requires correction, the sender should see action required and the receiver should not receive the request;
- the request should remain linked to the evidence verification outcome for audit and support.

Share and delivery rules:

- in-app delivery is preferred where both parties are active PayPlus users;
- app link, WhatsApp deeplink, QR code, or other approved channel may be offered where enabled;
- external share content must avoid sensitive request, evidence, payment, identity, and account details;
- accepted share links should route through authentication or onboarding before opening `REQUESTS-DETAIL`;
- share-link expiry, resend limits, reminder cooldown, and channel eligibility belong to DOC-08 and DOC-22.

Return behavior:

- from `BILLS-ADD`, successful creation returns to `REQUESTS-NEW` with the created context selected;
- cancelling `BILLS-ADD` returns to `REQUESTS-NEW` without changing the selected context;
- opening linked bill/rent detail from request review should return to `REQUESTS-NEW` or `REQUESTS-DETAIL` according to the entry source;
- after request submission, the user should route to `REQUESTS-DETAIL` for the created request.

Primary state behavior:

| State | Sender View | Receiver View |
| --- | --- | --- |
| Draft | Editable draft. | Not visible. |
| Pending evidence verification | Waiting for verification; edit/cancel where allowed. | Not visible. |
| Action required | Evidence or linked detail correction required. | Not visible. |
| Sent / reviewing | Request detail shows sent status and allowed remind/share actions. | Request appears as awaiting review. |
| Accepted / rejected / expired / cancelled | Request detail shows final or current request state and available follow-up actions. | Same underlying state, role-appropriate actions only. |

#### 5.11.9 Empty, Action-Required, and Archive Behavior

| State | Behavior |
| --- | --- |
| Empty `Received` | Explain that requests sent to the user will appear here. |
| Empty `Sent` | Explain that requests the user sends will appear here. Creation must happen through `REQUESTS-NEW` or the relevant bill/rent/request flow, not as a free-floating open money request. |
| Empty `Archived` | Explain that archived requests will appear here. |
| Archived | Archived requests disappear from active views but remain retrievable subject to retention, audit, and role-based access rules. |
| Expiring soon | Show priority in `Received` or `Sent` and route to `REQUESTS-DETAIL`. |

#### 5.11.10 Data and Intelligence Signals

DOC-06B should identify route-level signals only. Final event taxonomy, schema, lineage, model eligibility, and analytics ownership remain DOC-18.

Material signals include:

- Requests route opened;
- request card viewed;
- request detail opened;
- request creation started;
- existing bill/rent selected for request;
- new bill/rent setup opened from `REQUESTS-NEW`;
- request submitted for evidence verification;
- request auto-sent after evidence verification;
- request accepted, rejected, cancelled, expired, archived, or restored where applicable;
- request reminder sent;
- request shared through approved channel;
- request notification opened;
- request led to linked bill/rent context opened;
- request led to payment-start handoff in `BILLS-PAY` where applicable.

These signals should support service quality, funnel analysis, risk review, support investigation, and future approved AI-driven payment intelligence without turning Requests into a payment or open P2P feature.

#### 5.11.11 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Final visual card density, tab style, sort/filter design, and empty-state wording | Product / Design | Open |
| Final `REQUESTS-DETAIL` visual layout, field density, copy, and button order | Product / Design | Open |
| Final `REQUESTS-NEW` visual styling, field-level validation copy, counterparty lookup display copy, and share-button placement | Product / Design / Privacy / Security | Open |
| Resend, reminder cooldown, expiry, and escalation rules | Product / Operations / DOC-08 / DOC-22 | Open |

---

### 5.12 Payment Instructions Route

The user-facing route label may be `Payment Instructions` or `付款指示`.

The route is for pending, future, or incomplete payment setups. It is not the normal pay-now checkout route, not a bill/rent reminder route, not a request route, not full card management, and not payment history.

| Field | Requirement |
| --- | --- |
| Working route ID | `INSTRUCTIONS-ROOT` |
| Stable route ID | `ROUTE-06B-INSTRUCTIONS-ROOT` |
| Detail screen ID | `INSTRUCTIONS-DETAIL` |
| Stable detail screen ID | `SCREEN-06B-INSTRUCTIONS-DETAIL` |
| Primary owner | DOC-06B owns route shell, list/detail layout, entry points, high-level actions, and route handoff. |
| Payment owner | DOC-09 owns payment instruction mechanics, checkout/payment screen behavior, payment quote, payment profile/card allocation, funding-leg state, authorization, revalidation, and payment status. |
| Related owners | DOC-08 owns notification delivery; DOC-13 owns promotion quote impact; DOC-15 owns masking/privacy; DOC-18 owns schema/events; DOC-19 owns security/tokenization; DOC-22 owns admin controls. |

#### 5.12.1 Instruction Definition

A payment instruction means the user has already entered, or intentionally started, a payment setup and the payment is not submitted or completed immediately.

Payment instruction is created only where:

- the user intentionally creates a pay-later instruction within the allowed instruction window;
- the user starts a split-card payment and one or more funding legs remain pending;
- a payment setup remains incomplete due to pending, failed, expired, or retry-required funding action;
- the instruction requires user action before payment can proceed.

Payment instruction must not be created merely because a user pays immediately and completes payment. Normal completed payments belong to receipt/activity surfaces. A user who wants to pay beyond the allowed instruction window should create a normal reminder or future payment prompt, not a payment instruction.

#### 5.12.2 Instruction Types

| Type | Meaning | User Edit Boundary |
| --- | --- | --- |
| Pending Instruction | User intentionally set up a future/pay-later payment and no funding leg has been submitted. | User may change target bill/rent, amount, payment profile/card allocation, and payment schedule before submitting. |
| Incomplete Instruction | User already started payment and at least one payment step, funding leg, or failure/retry state exists. | User may continue payment or archive the instruction, but should not materially change target bill/rent, original amount, or completed funding legs. |

`Pay now` is not an instruction type. It is the normal checkout/payment path governed by DOC-09. Every payment may have backend session, quote, attempt, or audit records, but only pending/future/incomplete setups appear as user-facing payment instructions.

#### 5.12.3 Entry Points

| Entry Point | Route Behavior |
| --- | --- |
| Dashboard shortcut `Instructions` | Opens `INSTRUCTIONS-ROOT`. |
| Pay+ `Continue Payment` | Opens `INSTRUCTIONS-ROOT`, or may deep-link to `INSTRUCTIONS-DETAIL` where there is one urgent instruction. |
| Important Notice / Action Required card | Opens the relevant `INSTRUCTIONS-DETAIL` where a specific instruction exists. |
| Payment instruction notification | Opens `INSTRUCTIONS-DETAIL` by default for context; its primary action may continue to DOC-09 checkout/review where payment submission is required. |
| Checkout/payment flow | May create or update a payment instruction where user chooses pay later, split-card remains incomplete, or payment remains pending action. |

#### 5.12.4 `INSTRUCTIONS-ROOT` List Screen

`INSTRUCTIONS-ROOT` displays existing instruction cards and provides the entry point for creating a new instruction. It should not process payment directly.

Recommended screen order:

1. Header: `Payment Instructions` or `付款指示`.
2. Top action: `+ Add Instruction`.
3. Filter row: `All`, `Pending`, `Incomplete`, `Archived`.
4. Instruction card list.
5. Empty state.

Instruction cards should be compact. They should not behave like a full payment summary or receipt.

MVP card fields:

- linked bill/rent/fee name;
- category;
- payee / recipient name;
- intended amount or remaining amount, depending instruction type;
- instruction status;
- timing label:
  - pending instruction: `Pay on [date]`;
  - incomplete instruction: `Expires in X days`, `Expires today`, or `Expired`.

Card action:

- `View Detail` opens `INSTRUCTIONS-DETAIL`.

The card should not show detailed quote, fee, promotion, or full payment profile status. Those belong in the instruction detail screen or DOC-09 checkout/review.

#### 5.12.5 `INSTRUCTIONS-DETAIL` Detail Screen

`INSTRUCTIONS-DETAIL` explains and controls one instruction. It is a context and management screen; actual payment submission remains in DOC-09 checkout/payment.

For a pending instruction, show:

- linked bill/rent/fee;
- category;
- payee / recipient;
- payment amount;
- selected payment profile or card allocation summary;
- payment schedule;
- expiry countdown;
- instruction status.

Pending instruction allowed edits:

- change target bill/rent, with payment details recalculated through DOC-09;
- edit payment amount;
- change payment profile/card allocation;
- change payment schedule.

Pending instruction actions:

- `Pay Now`, routing to DOC-09 checkout/review;
- `Update Instruction`;
- `Cancel Instruction`.

For an incomplete instruction, show:

- linked bill/rent/fee;
- category;
- payee / recipient;
- total intended amount;
- funded amount where applicable;
- remaining amount;
- payment method or split-leg progress summary;
- failed, pending, or retry-required leg summary where applicable;
- expiry countdown;
- instruction status.

Incomplete instruction actions:

- `Continue Payment`, routing to DOC-09 checkout/review for remaining eligible action;
- `Archive`.

Incomplete instruction must not allow material changes to the target bill/rent, original intended amount, or completed funding legs. If the user wants a different target, different amount, or different payment setup after payment has partly started, the user should create a new payment or instruction instead of mutating the incomplete one.

#### 5.12.6 Add Instruction Flow

`+ Add Instruction` starts an instruction setup flow, not a generic checkout shortcut.

The flow should:

1. require the user to select an existing eligible bill, fee, rent, or approved obligation;
2. route to `BILLS-ADD` if the user needs to add a new bill/rent first;
3. route into DOC-09 payment setup rules for amount, payment profile/card allocation, timing, quote, eligibility, and authorization boundary;
4. create a pending instruction only when the user confirms a pay-later setup within the allowed instruction window.

If the selected target bill/rent changes during a pending instruction edit, the payee, amount, payment readiness, fee, promotion eligibility, schedule, and available payment profile/allocation must be recalculated through DOC-09 before the instruction can be updated or paid.

#### 5.12.7 Reminder and Notification Boundary

A payment instruction may generate app notifications, action-required alerts, and system tasks, but it should not create a normal user-visible `BILLS-REMINDER-LIST` reminder record.

| Concept | Route / Owner |
| --- | --- |
| Bill/rent due-date reminder | DOC-06C `BILLS-REMINDER-LIST` / `BILLS-REMINDER-DETAIL`. |
| User manual bill/rent reminder | DOC-06C `BILLS-REMINDER-LIST` / `BILLS-REMINDER-DETAIL`. |
| Payment instruction action alert | `INSTRUCTIONS-DETAIL` and DOC-09 checkout/review, with delivery governed by DOC-08. |

This avoids duplicate user functions:

- Reminders mean "remind me about an obligation."
- Payment Instructions mean "finish or manage a pending payment setup."
- Checkout means "submit payment."

#### 5.12.8 Payment Profile / Card Allocation Boundary

Payment instruction may display selected payment profile, masked card, or split allocation summary because that information is needed to understand the pending payment setup.

Payment instruction must not become the full Payment Profile management route.

Allowed route behavior:

- show whether the instruction uses a single-card payment or split-card payment;
- show masked card or payment-profile allocation summary;
- show if a selected card or profile is unavailable, expired, failed, or requires action;
- for pending single-card instructions, provide `Choose Card` or `Update Card`;
- for pending split-card instructions, provide `Choose Profile` or `Edit Profile`;
- for incomplete instructions, preserve completed funding-leg facts and route only to permitted continuation or correction actions.

Handoff behavior:

- actual checkout selection, split allocation for the current payment, quote recalculation, card-leg authorization, and payment submission are governed by DOC-09;
- reusable card and split-profile management belongs to `PAYMENT-PROFILE-ROOT`;
- tokenization, card-data security, PSP return handling, and PCI mechanics belong to DOC-19.

`Choose Card`, `Update Card`, `Choose Profile`, and `Edit Profile` should open `PAYMENT-PROFILE-ROOT` in instruction-context mode and return to `INSTRUCTIONS-DETAIL` with refreshed card/profile data after the permitted selection, setup, or edit action.

#### 5.12.9 Data and Intelligence Signals

DOC-06B should identify route-level signals only. Final event taxonomy, schema, lineage, model eligibility, and analytics ownership remain DOC-18.

Material signals include:

- Instructions route opened;
- instruction card viewed;
- instruction detail opened;
- add instruction started;
- target bill/rent selected;
- pending instruction created;
- pending instruction updated;
- pending instruction cancelled;
- incomplete instruction continued;
- incomplete instruction archived;
- instruction expired;
- payment profile/card issue displayed;
- user routed from instruction to Payment Profile;
- user returned from Payment Profile to instruction with refreshed card/profile data;
- user routed from instruction to checkout/review;
- user returned from checkout/review to instruction where applicable;
- instruction led to successful funding, partial funding, failure, expiry, cancellation, or payout-ready funded portion.

These signals support funnel analysis, payment-friction analysis, support investigation, risk monitoring, operations, and future approved AI-driven payment intelligence.

#### 5.12.10 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Final visual layout, field density, and exact button labels for pending versus incomplete instruction cards | Product / Design | Open |
| Final expiry window, expiry countdown wording, cancellation/archive rules, and restore rules | Product / Payments / Operations | Open |
| Exact visual copy, placement, and return-state UI for handoff among `INSTRUCTIONS-DETAIL`, `PAYMENT-PROFILE-ROOT`, and DOC-09 checkout. Route direction is clarified in `docs/diagrams/payplus-app-route-entry-map.md`. | Product / Payments / Security | Open |
| Exact notification wording and timing for payment instruction action alerts | Product / Payments / DOC-08 | Open |

---

### 5.13 Payment Profile Route

The final user-facing route label is `Payment Profile`. The dashboard shortcut may remain `Cards`.

The route manages reusable payment setup objects. It is not checkout, not a wallet, not a stored-value account, and not a way to move money without an eligible evidence-backed obligation.

| Field | Requirement |
| --- | --- |
| Working route ID | `PAYMENT-PROFILE-ROOT` |
| Stable route ID | `ROUTE-06B-PAYMENT-PROFILE-ROOT` |
| Primary owner | DOC-06B owns route shell, entry points, major screens, route handoff, and high-level user actions. |
| Payment owner | DOC-09 owns actual checkout selection, payment quote, split-card allocation for a payment, authorization, funding-leg submission, and payment states. |
| Security owner | DOC-19 owns PSP/acquirer tokenization, card-data security, PCI boundary, authentication, and token handling. |
| Related owners | DOC-07 owns wording; DOC-08 owns notifications; DOC-13 owns card-linked benefit rules; DOC-15 owns masking/privacy; DOC-18 owns schema/events; DOC-22 owns admin controls. |

#### 5.13.1 Route Structure

`PAYMENT-PROFILE-ROOT` should use a two-tab structure:

| Tab | Purpose | Working IDs |
| --- | --- | --- |
| Cards | Manage individual tokenized credit cards for the payer account. | `PAYMENT-CARD-LIST`, `PAYMENT-CARD-ADD`, `PAYMENT-CARD-DETAIL` |
| Profiles | Manage saved split-card allocation templates created from tokenized cards. | `PAYMENT-PROFILE-LIST`, `PAYMENT-PROFILE-ADD`, `PAYMENT-PROFILE-DETAIL` |

Payment profiles belong to the payer user account. Payees must not see payer cards, payer payment profiles, token references, or private funding data.

#### 5.13.2 Entry Points and Return Behavior

| Entry Point | Route Behavior |
| --- | --- |
| Dashboard shortcut `Cards` | Opens `PAYMENT-PROFILE-ROOT`. |
| Me / account payment settings | Opens `PAYMENT-PROFILE-ROOT` or the relevant card/profile screen. |
| Checkout add/change card | Opens card add or selection flow and returns to DOC-09 checkout. |
| Checkout choose/edit split profile | Opens profile selection or edit flow and returns to DOC-09 checkout. |
| `INSTRUCTIONS-DETAIL` payment profile action | Opens the relevant card/profile screen and returns to the instruction or checkout context according to the entry source. |

The route must preserve return context when opened from checkout, instruction detail, or profile editing.

#### 5.13.3 Root Visual Behavior

`PAYMENT-PROFILE-ROOT` should show:

- page title: `Payment Profile`;
- two tabs: `Cards` and `Profiles`;
- contextual return state where opened from checkout or instruction detail;
- clear empty states for no saved cards and no saved profiles;
- no balance, wallet, cashout, transfer, or payment authorization content.

When opened from dashboard shortcut or Me/account settings, the route behaves as a normal management area.

When opened from checkout or `INSTRUCTIONS-DETAIL`, the route behaves as a temporary management or selection support flow. After add/edit/select actions, the user should return to the originating checkout or instruction context with refreshed card/profile data.

#### 5.13.4 Cards Tab

Card list items should show:

- card nickname entered by the user;
- masked cardholder name only where returned or permitted by the PSP/acquirer;
- masked card number;
- expiry date;
- card brand where available;
- card status;
- default-card marker where applicable;
- remove action.

`PAYMENT-CARD-ADD` should route through the approved PSP/acquirer tokenization flow. PayPlus should store only the token/reference and permitted masked metadata. It must not store raw card number, CVV, magnetic-stripe data, or sensitive authentication data unless separately approved under final PCI scope.

A default card may be set for single-card checkout. It may be pre-selected in checkout, but the user must be able to change it before authorization.

Removing or updating a card should show a confirmation prompt by default. Payment-passcode confirmation should be optional where the user enables it in user settings. Additional step-up may still apply where PSP/acquirer, risk, or security rules require it. Removal should be implemented as archive/soft delete, not hard deletion.

#### 5.13.5 Profiles Tab

A payment profile means a saved split-card allocation template. It is not a stored balance and does not authorize future payment by itself.

Profile list items should show:

- profile name;
- number of cards;
- starred/frequent marker where set by the user;
- profile status;
- edit and remove actions.

Add/edit profile should support:

- profile name;
- base total payment amount for setup calculation;
- card slots, default 1 and maximum 6 for MVP;
- selected saved card per slot;
- payment amount per card;
- auto-calculated ratio per card;
- amount-to-ratio and ratio-to-amount recalculation while editing;
- save and cancel actions.

The saved reusable profile should store ratios as the reusable allocation basis. The base total amount is a setup/reference value and should not lock future checkout amount.

Validation rules:

- total allocation must equal the entered total amount for MVP;
- total allocation must not exceed the entered total amount;
- each card allocation must be positive;
- duplicate use of the same card in one profile should be blocked unless later explicitly approved;
- maximum card count is 6 for MVP unless a later approved change reduces or expands it.

Split-card checkout should not pre-select a payment profile by default. Users should choose a profile during checkout. Starred/frequent profiles should be displayed first.

#### 5.13.6 Invalid Card and Action-Required Behavior

If a card is removed, expired, suspended, invalid, or otherwise unavailable:

- the affected card remains visible where retention and masking rules allow;
- affected payment profiles remain visible but show `Action Required`;
- the user may select the profile in checkout, but checkout must warn that the profile is incomplete and cannot proceed until the affected card is replaced, removed, or updated;
- pending instructions using the affected card/profile should show action required;
- historical payments and receipts must not be changed.

Recommended warning meaning: the profile is incomplete because one card is unavailable, and the user must replace, remove, or update that card before payment.

#### 5.13.7 Checkout and Split-Card Boundary

`PAYMENT-PROFILE-ROOT` manages reusable setup only. DOC-09 checkout owns payment-time behavior.

For split-card payment, checkout should:

1. require the payer to choose a profile or define a current-payment split;
2. calculate each card leg from the selected profile ratios and current payment amount;
3. allow amount and ratio adjustment before authorization, subject to total-amount rules;
4. allow saving the adjusted split as a new or updated profile where permitted;
5. authorize and submit each card leg one by one;
6. treat the payment as completed only when all required legs complete.

Estimated card-linked benefits may be shown during checkout, but final eligibility must be recalculated per card leg before authorization under DOC-13 and DOC-09.

#### 5.13.8 Data and Intelligence Signals

DOC-06B should identify route-level signals only. Final event taxonomy, schema, lineage, model eligibility, and analytics ownership remain DOC-18.

Material signals include:

- Payment Profile route opened;
- card add started and tokenization returned;
- card nickname edited;
- card default set or changed;
- card removed, expired, suspended, or restored;
- profile created, edited, starred, unstarred, removed, or marked action-required;
- profile selected from checkout or instruction context;
- profile issue displayed;
- user returned to checkout or instruction after card/profile action.

These signals support checkout-friction analysis, card/profile usability, support investigation, risk monitoring, and future approved AI-driven payment intelligence.

#### 5.13.9 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Two-tab `Cards` / `Profiles` structure | Product / Design | Confirmed |
| Exact final card styling, field density, empty-state copy, and list visual design | Product / Design | Open |
| Final PSP/acquirer tokenization return behavior and permitted card metadata | Payments / Security / DOC-19 | Open |

---

### 5.14 Activity Route

Activity is the event and lifecycle view of what happened in a user's PayPlus account. It is not the same as a receipt, statement, internal audit log, or bill/rent-specific activity timeline.

DOC-06B owns the global Activity route shell. DOC-06C owns `BILLS-ACTIVITY` for one selected bill/rent record. DOC-08 owns receipt and statement communication. DOC-09, DOC-10, and DOC-11 own payment, payout, refund, reversal, and failure status meaning. DOC-18 owns final event taxonomy, IDs, schema, lineage, and analytics. DOC-22 owns admin operations and internal review history.

| Field | Requirement |
| --- | --- |
| User-facing route label | `Activity` |
| Working route IDs | `ACTIVITY-ROOT`, `ACTIVITY-DETAIL` |
| Stable route IDs | `ROUTE-06B-ACTIVITY-ROOT`, `ROUTE-06B-ACTIVITY-DETAIL` |
| Purpose | Let a user review account-level financial activity across payer and payee roles. |
| Boundary | Activity lists events and lifecycle status. It must not become the receipt/statement file library, the bill/rent-specific timeline, or an internal audit log. |

#### 5.14.1 Entry Points

| Entry Point | Destination |
| --- | --- |
| Dashboard Recent Activity arrow / View More | `ACTIVITY-ROOT` |
| Me / account activity entry | `ACTIVITY-ROOT` |
| Payment, payout, refund, return, or reversal notification | `ACTIVITY-DETAIL` where a specific transaction exists; otherwise `ACTIVITY-ROOT` |
| Checkout or payment result where activity review is needed | `ACTIVITY-DETAIL` for the submitted transaction where available |

Bill/rent `View Activities` opens DOC-06C `BILLS-ACTIVITY`, not `ACTIVITY-ROOT`. `BILLS-ACTIVITY` stays contextual to one bill/rent record.

#### 5.14.2 Root Views

`ACTIVITY-ROOT` should use role-aware views:

| View | Meaning |
| --- | --- |
| `All` | Mixed payer and payee account-level financial activity. |
| `Paid` | User acted as payer or funded a payment. |
| `Received` | User acted as payee/recipient and received or expects transfer/payout visibility. |

Refunds, reversals, returns, failures, and rejected outcomes should appear in the relevant view with mapped status labels. They should not have a separate top-level MVP view unless later product usage justifies it.

#### 5.14.3 Activity Root Screen Behavior

`ACTIVITY-ROOT` should behave like a bank or accounting activity list. It is designed for scanning transaction-like entries first, then expanding one entry only when the user wants more actions.

Recommended screen order:

1. Header: `Activity`.
2. Segmented views: `All`, `Paid`, `Received`.
3. Optional search or filter row if enabled.
4. Activity list, newest first, grouped by date where useful.
5. Empty state where no activity exists.

Each collapsed activity entry should show:

| Field | Requirement |
| --- | --- |
| Date | Activity or transaction date. |
| Rent / bill / fee name | Linked obligation, payment, or activity name. |
| Payee / payer name | Counterparty name, role-aware and masked where required. |
| Amount | Display as positive or negative to show debit/credit direction. |
| Status | User-facing mapped status from `docs/traceability/status-display-reference-matrix.md`. |

Amount direction should follow the user's account perspective:

| Scenario | Display Direction |
| --- | --- |
| User paid as payer | Negative amount, such as `-HK$8,000`. |
| User received as payee | Positive amount, such as `+HK$8,000`. |
| Refund returned to payer | Positive amount. |
| Return, reversal, or adjustment | Direction should follow the actual user account impact and mapped status. |

Interaction behavior:

| User Action | Behavior |
| --- | --- |
| Tap collapsed entry | Expand the entry into an activity card. |
| Tap expanded entry or `Close` | Collapse the activity card. |
| Tap `View Details` | Open `ACTIVITY-DETAIL`. |
| Tap receipt/proof download button | Directly download the available receipt/proof. |
| Tap invoice button, if shown | Directly download the permitted linked invoice. Evidence access remains governed by DOC-06C, DOC-12, and DOC-15. |

Expanded activity card should show the same core entry information plus available actions:

- `View Details`;
- `Download Receipt`, where available;
- `Download Proof`, where available;
- `View / Download Invoice`, only where linked invoice/evidence access is permitted;
- `Close`.

Button availability rules:

| Situation | Requirement |
| --- | --- |
| Receipt/proof unavailable | Hide the button by default. Show a disabled button only where useful with a clear, non-sensitive reason. |
| Invoice/evidence access not permitted | Hide restricted document buttons. Do not show sensitive denial details. |
| Invoice/evidence file permitted and relevant | Show direct download action. |

One transaction should normally appear as one activity entry. Payment, settlement, payout, receipt, refund, return, and reversal milestones should update the same activity lifecycle where they belong to the same transaction, instead of creating duplicate entries that describe the same payment.

#### 5.14.4 Activity Detail

`ACTIVITY-DETAIL` should show:

- transaction ID or reference ID;
- payment reference ID where available;
- payout or transfer reference ID where available;
- bill/rent/fee/payment name;
- counterparty;
- amount with positive/negative direction from the user's account perspective;
- role/action label: `Paid` or `Received`;
- user-facing status from the status display reference matrix;
- linked bill/rent detail where applicable;
- masked payment method summary where allowed;
- receipt/proof download button where available;
- invoice or evidence access only where permitted;
- lifecycle timeline using mapped user-facing labels.

Recommended detail screen order:

1. Header with back button.
2. Status summary.
3. Main transaction summary.
4. Counterparty and linked bill/rent section.
5. Reference IDs section.
6. Lifecycle timeline.
7. Download receipt/proof section with available file actions and a `Close` or back action.

Route exit and return behavior:

| Action / Entry Context | Behavior |
| --- | --- |
| Open linked bill/rent detail | Route to `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT`; back returns to `ACTIVITY-DETAIL`. |
| `Close` / back after opening from `ACTIVITY-ROOT` | Return to `ACTIVITY-ROOT` with the originating entry still available; preserving the expanded state is preferred where practical. |
| `Close` / back after opening from notification | Return to the prior app context. |
| Download receipt/proof | Direct download where available and permitted. |
| Receipt/proof unavailable | Hide the button by default, or show disabled only where useful with a clear, non-sensitive reason. |
| Invoice/evidence access not permitted | Hide restricted document buttons and avoid exposing sensitive denial details. |

The detail screen may show lifecycle milestones, but it must not expose raw backend status names as user-facing labels. Timeline wording should follow the status display reference matrix and the owning domain documents.

The Activity detail route should not display a linked request as the main context after a request has become an accepted bill/rent/payment context. If a request is relevant for support or audit, that relationship belongs in system records and controlled detail views, not the default activity list.

#### 5.14.5 Data and Intelligence Signals

DOC-06B identifies route-level signals only. Final event taxonomy, ID strategy, audit events, warehouse fields, model eligibility, and analytics rules belong in DOC-18.

Material route signals include:

- Activity route opened;
- Activity view selected;
- activity item opened;
- activity entry expanded or collapsed;
- receipt/proof downloaded from activity root or detail;
- invoice/evidence access opened from activity root or detail where permitted;
- linked bill/rent detail opened from activity detail;
- user viewed or acted after a failed, returned, refunded, reversed, or under-review activity status.

### 5.15 Receipts & Statements Route

`Receipts & Statements` is the route for transaction confirmation records and periodic/account summary files. The dashboard shortcut may remain `Receipts`.

Receipt is a transaction confirmation record for a completed transaction. Statement is a periodic or account-level summary record. Activity is the event/lifecycle view and remains separate.

DOC-06B owns the route, list, search, preview handoff, and entry points. DOC-08 owns receipt/statement content, notification, delivery, and re-issue communication. DOC-15 owns masking, retention, and privacy access. DOC-18 owns final document IDs, file metadata, versioning schema, lineage, and audit events. DOC-22 owns admin re-issue and correction operations.

| Field | Requirement |
| --- | --- |
| Full route label | `Receipts & Statements` |
| Dashboard shortcut label | `Receipts` |
| Working route IDs | `RECEIPTS-ROOT`, `RECEIPT-DETAIL`, `STATEMENT-DETAIL` |
| Stable route IDs | `ROUTE-06B-RECEIPTS-ROOT`, `ROUTE-06B-RECEIPT-DETAIL`, `ROUTE-06B-STATEMENT-DETAIL` |
| Purpose | Let users find, preview, and download transaction receipts and account statements. |
| Boundary | This route is a file/document hub. It should not replace Activity, checkout, bill/rent activity, or internal audit history. |

#### 5.15.1 Entry Points

| Entry Point | Destination |
| --- | --- |
| Dashboard shortcut `Receipts` | `RECEIPTS-ROOT` |
| Me / account records entry | `RECEIPTS-ROOT` |
| Receipt notification | `RECEIPT-DETAIL` |
| Statement notification | `STATEMENT-DETAIL` |
| `ACTIVITY-DETAIL` receipt action | Direct file download or `RECEIPT-DETAIL` where an in-app PDF preview is needed |
| `ACTIVITY-DETAIL` proof action | Direct file download for MVP |
| DOC-06C `BILLS-ACTIVITY-DETAIL` receipt/proof action | Direct file download by default |

#### 5.15.2 Root Screen and Views

`RECEIPTS-ROOT` is the only substantive list-management screen in this route family. It should show, in order:

1. route header `Receipts & Statements`;
2. search control;
3. `All`, `Receipts`, and `Statements` views;
4. receipt and statement list items;
5. empty state where applicable.

`RECEIPTS-ROOT` should use:

| View | Meaning |
| --- | --- |
| `All` | Receipts and statements together. |
| `Receipts` | Transaction receipt records. |
| `Statements` | Periodic/account summary records. |

Search should cover available receipt and statement metadata, including but not limited to bill/fee/rent name, date, payer name, payee name, counterparty name, document name, receipt ID, and transaction reference. Search refines the current view and does not create another route.

If no receipt or statement is available in the selected view, show `No receipts or statements yet.` There is no user-facing create action because receipts and statements are system-generated records.

There should be no separate `Corrections` MVP view. If a receipt or statement must be replaced, PayPlus should re-issue a new version and retain the prior version under controlled recordkeeping.

#### 5.15.3 Receipt List Item

Receipt items should show:

- date of payment;
- bill/fee/rent name;
- counterparty;
- amount;
- role indicator `Paid` or `Received`;
- `View` button;
- `Download` button.

#### 5.15.4 Statement List Item

Statement items should show:

- date of issuance;
- statement name, such as `Pay+ Statement - June 2026`;
- `View` button;
- `Download` button.

#### 5.15.5 Receipt and Statement Detail

`RECEIPT-DETAIL` and `STATEMENT-DETAIL` are deep-linkable PDF-preview destinations, not separate information-heavy detail pages. Both should use the same in-app PDF-view behavior:

- `RECEIPT-DETAIL` opens the selected receipt PDF;
- `STATEMENT-DETAIL` opens the selected statement PDF;
- the preview shows only the PDF, `Close` or `Back`, and `Download`;
- required receipt and statement content follows DOC-08; exact PDF layout and visual design are defined later.

From `RECEIPTS-ROOT`, `View` opens the relevant in-app PDF preview. `Download` downloads the latest valid PDF directly without opening the preview. Closing a preview opened from `RECEIPTS-ROOT` returns to the same view and list position. Closing a preview opened from a notification returns to the prior app context; if no prior context exists, it returns to `RECEIPTS-ROOT`.

The MVP keeps separate detail route IDs for notification/deeplink routing and future flexibility, while using one shared preview behavior.

#### 5.15.6 Re-Issue and Versioning

If a receipt or statement is wrong, replaced, or re-issued:

- the latest valid version should be shown by default;
- prior versions must be retained where required for audit, tax, support, and dispute handling;
- version number or issue timestamp should be stored;
- affected users should be notified where material;
- admin workflow and re-issue controls belong in DOC-22;
- final document metadata, lineage, versioning, and retention schema belong in DOC-18;
- notification and wording rules belong in DOC-08.

#### 5.15.7 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Final Activity visual styling, field density, search/filter behavior, grouping behavior, and empty-state copy | Product / Design | Open |
| Final receipt/statement PDF layout, visual design, export naming, and sharing controls | Product / Design / Finance / Legal | Open |
| Final receipt/statement re-issue policy and admin workflow | Product / Finance / Operations / DOC-22 | Open |

## 6. Route Completion Status

| Route / Area | Status | Next Required Work |
| --- | --- | --- |
| Home Dashboard | Partially Defined | Confirm card-level UI, notice priority, carousel behavior, dashboard activity cap, and empty states. |
| Bills | Partially Defined in DOC-06C | Continue detailed Bills route work in DOC-06C. |
| Pay+ | Partially Defined | Confirm visual order, disabled states, eligibility copy, and final action limits. |
| Offers | Not Fully Defined | Define Offers Hub, offer detail, coupon/voucher library routing, and placement interactions with DOC-13. |
| Me | Not Fully Defined | Define profile, settings, privacy, notification, security, payment-method, and support routes. |
| Requests | Route Shell Defined / Not Final UI | Confirm final visual styling, card density, sort/filter behavior, field-level copy, resend/reminder limits, and detailed channel controls. `REQUESTS-NEW` section order, route boundary, evidence gate, counterparty lookup boundary, share routing, and DOC-06C handoff are defined. |
| Instructions | Route Shell Defined / Not Final UI | Confirm final visual styling, card density, exact button labels, expiry/archive rules, and payment-profile handoff behavior. |
| Activity | Route Shell Defined / Not Final UI | Screen order, accounting-style list behavior, expandable activity cards, amount direction, core detail sections, and download actions are defined. Confirm final visual styling, field density, search/filter behavior, grouping behavior, and empty-state copy. |
| Receipts & Statements | Root and Preview Behavior Defined / Not Final PDF Design | `RECEIPTS-ROOT` search, list, role indicator, empty state, direct download, shared PDF preview, and return behavior are defined. Confirm PDF layout/design, export naming, sharing controls, statement schedule, and re-issue workflow. |
| Reminders | Partially Defined in DOC-06C | Ordinary bill/rent reminders remain separate from payment instruction action alerts. |
| Payment Profile / Cards | Two-Tab Route Baseline Defined / Not Final Visual Design | Confirm final card styling, field density, empty-state copy, PSP tokenization return behavior, and permitted card metadata. |
| Referral | Not Fully Defined | Define route UX with DOC-13. |
| More | Not Fully Defined | Define overflow, management, and admin/user shortcut configuration behavior. |

## 7. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06B-001 | What final Pay+ visual layout, button order, disabled states, eligibility copy, and final action limits should be used? | Product / Design / Payments | Open |
| OQ-06B-002 | What route-level IA should apply to Offers, Me, More, Referral, and Support? | Product / Design | Open |
| OQ-06B-003 | What dashboard shortcut display cap, user reorder UI, restore-default behavior, and admin default mechanism should be used? | Product / Design / Operations | Open |
| OQ-06B-004 | What priority, collapse, expiry, and routing rules should apply to Important Notice / Action Required cards? | Product / Operations / Compliance | Open |
| OQ-06B-005 | What carousel card limit, auto-rotation behavior, ranking, targeting, and admin approval workflow should apply to Featured / What's New / Hot Offer placements? | Product / Growth / Operations | Open |
| OQ-06B-006 | What exact visual styling, card density, field-level copy, resend/reminder limit, share-button placement, and filter/sort design should apply to the Requests route? | Product / Design / Operations | Open |
| OQ-06B-007 | What exact visual styling, field density, expiry/archive wording, and card/payment-profile handoff should apply to pending and incomplete payment instruction routes? | Product / Design / Payments / Security | Open |
| OQ-06B-008 | What exact Payment Profile card styling, field density, empty-state copy, tokenization return UX, and permitted PSP card metadata should be used? Two-tab `Cards` / `Profiles` structure is confirmed. | Product / Design / Payments / Security | Partially open |
| OQ-06B-009 | What exact Activity visual styling, field density, search/filter behavior, grouping behavior, empty-state copy, lifecycle timeline wording, and transaction-detail display should be used? Screen order, expandable entry behavior, amount direction, and core actions are defined. | Product / Design / Payments / Operations | Partially open |
| OQ-06B-010 | What final receipt/statement PDF layout and visual design, export naming, sharing control, statement schedule, and re-issue workflow should be used? Required content follows DOC-08; root search, direct download, and shared in-app preview behavior are defined. | Product / Finance / Legal / Operations | Partially open |

## 8. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.16 | 2026-07-14 | Defined `RECEIPTS-ROOT` search, views, role-aware list and empty-state behavior; defined direct download and shared in-app PDF preview behavior for `RECEIPT-DETAIL` and `STATEMENT-DETAIL`; kept proof as an Activity-context direct download and final PDF design open. |
| 0.1.15 | 2026-07-13 | Refined `ACTIVITY-ROOT` and `ACTIVITY-DETAIL` UI behavior with accounting-style activity entries, positive/negative amount direction, expandable activity cards, permitted receipt/proof/invoice actions, and detail screen order without support/help. |
| 0.1.14 | 2026-07-08 | Defined global `ACTIVITY-ROOT` / `ACTIVITY-DETAIL` and `RECEIPTS-ROOT` / `RECEIPT-DETAIL` / `STATEMENT-DETAIL` route shells, separated Activity from receipt/statement files, and clarified contextual Bills activity boundaries. |
| 0.1.13 | 2026-07-06 | Added Activity, Receipt, and Statement definitions and required user-facing activity status labels to follow the status display reference matrix. |
| 0.1.12 | 2026-07-06 | Clarified instruction-context handoff to `PAYMENT-PROFILE-ROOT`, return to `INSTRUCTIONS-DETAIL`, related data signals, and remaining visual handoff open item. |
| 0.1.11 | 2026-07-06 | Confirmed Payment Profile two-tab `Cards` / `Profiles` structure and added root visual behavior, empty-state, return-context, and non-wallet/non-checkout UI boundaries. |
| 0.1.10 | 2026-07-06 | Defined `PAYMENT-PROFILE-ROOT` route shell for tokenized card management and saved split-card profile management, including final `Payment Profile` label, max 6-card profile/payment cap, default confirmation behavior, card/profile entry points, instruction and checkout handoffs, invalid-card behavior, split-profile boundaries, and DOC-09/DOC-19 ownership separation. |
| 0.1.9 | 2026-07-03 | Defined `INSTRUCTIONS-ROOT` and `INSTRUCTIONS-DETAIL` route shell for payment instructions / 付款指示, including pending versus incomplete instruction behavior, compact card fields, detail actions, reminder boundary, checkout handoff, and payment-profile/card allocation boundary. |
| 0.1.8 | 2026-07-03 | Finalized `REQUESTS-NEW` route shell with section order, route boundary, linked-context selection, evidence gate, counterparty lookup, share/delivery rules, state behavior, and DOC-06C return behavior. |
| 0.1.7 | 2026-07-02 | Added `REQUESTS-NEW`, clarified request status labels, evidence-before-send gate, counterparty identifier, WhatsApp deeplink sharing, and return behavior between Requests and Bills routes. |
| 0.1.6 | 2026-07-02 | Clarified shortcut grid items as entry points rather than feature owners, narrowed Bills bottom-nav ownership, and added the app route-entry Mermaid diagram reference. |
| 0.1.5 | 2026-06-29 | Defined `REQUESTS-DETAIL` as its own DOC-06B screen and clarified linked DOC-06C bill/rent detail handoff. |
| 0.1.4 | 2026-06-25 | Drafted Requests route shell, including route definition, entry points, views, card fields, actions, empty states, and data-signal boundaries. |
| 0.1.3 | 2026-06-25 | Clarified Requests route definition, top-right inbox relationship, and request-not-payment boundary. |
| 0.1.2 | 2026-06-25 | Added route ownership rule to keep DOC-06B focused on route shells and handoffs while lifecycle and module behavior remain in owning documents. |
| 0.1.1 | 2026-06-25 | Cleaned publication wording and corrected dashboard copy formatting for official DOC-06B baseline use. |
| 0.1.0 | 2026-06-25 | Created as DOC-06B child document for dashboard, navigation, Pay+, shortcut, route taxonomy, and route workplan content. |
