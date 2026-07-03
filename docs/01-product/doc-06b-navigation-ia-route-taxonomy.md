---
document_id: DOC-06B
title: Navigation, IA & Route Taxonomy
version: 0.1.8
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
last_updated: 2026-07-03
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-06D UX Requirements, Acceptance Criteria & Test Matrix
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-15 Privacy, Data Protection & Record Retention
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06B - Navigation, IA & Route Taxonomy

## 1. Purpose

DOC-06B governs PayPlus global app navigation, information architecture, dashboard placement, route taxonomy, screen/component/action ID standards, and route completion tracking.

## 2. Scope Boundary

DOC-06B owns how app areas, routes, screens, views, sheets, components, actions, flows, and system touchpoints are named, grouped, opened, and routed at the product UX level.

DOC-06B does not own detailed Bills/rent/tenancy route behavior, which belongs to DOC-06C. It does not own checkout processing, payment instruction mechanics, evidence verification logic, data schema, notification delivery rules, privacy implementation, or admin workflow detail.

When drafting route IA, DOC-06B must define the route shell only: route ID, entry points, destination relationship, high-level user purpose, major sections, and handoff rules. If detailed lifecycle, status, payment, evidence, risk, notification, privacy, data, or admin logic is required, DOC-06B should reference the owning document instead of duplicating the rule.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Bottom navigation | Partially defined | Home, Bills, Pay+, Offers, Me baseline exists. |
| Home dashboard | Partially defined | Section order exists; final card and visual details remain open. |
| Pay+ action sheet | Partially defined | Working action set exists; exact order and disabled states remain open. |
| Shortcut grid | Partially defined | Eight MVP shortcuts exist; detailed More/overflow UX remains open. |
| Route taxonomy and ID standard | Initial baseline | Stable IDs should be assigned progressively. |
| Non-Bills route registry | Placeholder | Offers, Me, Requests, Instructions, Receipts, Cards, Referral, More need future drafting. |

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

The Pay+ action sheet should contain user-friendly actions for starting or continuing the core PayPlus journey. It should not expose internal terms such as payment instruction, capture layer, or verification layer to users.

Working baseline Pay+ actions:

- Pay a Bill / Fee;
- Pay Rent;
- Add Bill / Rent;
- Continue Payment;
- Request Payment.

`Request Payment` should appear by default for all users, unless the request feature/module is disabled or the account is restricted. A user may be both payer and payee, such as a landlord who is also a renter elsewhere. `Request Payment` opens `REQUESTS-NEW` and must link to an evidence-backed bill, fee, rent, tenancy, invoice, or approved obligation before sending.

`Add Bill / Rent` should include scan QR, upload bill/invoice/tenancy/evidence, and manual entry as input methods inside the setup flow. QR or upload should not be a standalone Pay+ payment action because PayPlus must remain evidence-backed and must not behave as generic QR instant payment.

`Continue Payment` should cover deferred payment instructions, unfinished split-card payments, failed or retry payment legs, interrupted checkout, and other payment actions that require the user to resume.

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
| Instructions | Deferred payment instructions, split-card progress, pending funding legs, expired instructions, and action-required instructions. | Opens the future Instructions route / DOC-09 continuation surface. |
| Bills & Tenancies | Saved bills, fee records, rent records, tenancy records, evidence status, due dates, and obligation details. | Opens `BILLS-ROOT`. |
| Receipts | Payment receipts, proof of payment, statements, completed records, refund/reversal records, and related transaction evidence. | Opens the future Receipts / Activity hub. |
| Reminders | User-set due reminders for bills, rent, tenancy obligations, and manual reminders. | Opens `BILLS-REMINDER-LIST`. |
| Cards | Tokenized payment profiles, cards, payment methods, card status, and payment-method settings. | Opens the future Cards / Payment Methods route. |
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

Dashboard recent activity items should show:

- date;
- item;
- action;
- amount;
- status.

The section should include a button or arrow to the Recent Activity detail page.

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
| Instructions Route | Define deferred payment instructions, split-card progress, retry/failed legs, pending actions, cancellation, expiry, and continuation paths. | Title preserved / not finalized |
| Bills & Tenancies Route | Define saved obligation list, tenancy detail, evidence status, payee/landlord detail, due dates, and linked payment actions. | Title preserved / not finalized |
| Receipts / Activity Route | Define receipts, proof of payment, statements, refund/reversal records, and transaction details. | Title preserved / not finalized |
| Reminders Route | Define due reminders, user-set reminders, notification settings, and reminder destinations. | Title preserved / not finalized |
| Cards / Payment Methods Route | Define tokenized card/payment profile management, card status, default card, and payment method issue handling. | Title preserved / not finalized |
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

---
## 6. Route Completion Status

| Route / Area | Status | Next Required Work |
| --- | --- | --- |
| Home Dashboard | Partially Defined | Confirm card-level UI, notice priority, carousel behavior, dashboard activity cap, and empty states. |
| Bills | Partially Defined in DOC-06C | Continue detailed Bills route work in DOC-06C. |
| Pay+ | Partially Defined | Confirm visual order, disabled states, eligibility copy, and final action limits. |
| Offers | Not Fully Defined | Define Offers Hub, offer detail, coupon/voucher library routing, and placement interactions with DOC-13. |
| Me | Not Fully Defined | Define profile, settings, privacy, notification, security, payment-method, and support routes. |
| Requests | Route Shell Defined / Not Final UI | Confirm final visual styling, card density, sort/filter behavior, field-level copy, resend/reminder limits, and detailed channel controls. `REQUESTS-NEW` section order, route boundary, evidence gate, counterparty lookup boundary, share routing, and DOC-06C handoff are defined. |
| Instructions | Partially Defined by DOC-09 | Define route shell, shortcut behavior, dashboard action-required placement, and return-to-checkout behavior. |
| Receipts / Activity | Partially Defined | Define global receipt/activity hub and relationship to bill/rent-specific activity in DOC-06C. |
| Reminders | Partially Defined in DOC-06C | Confirm relationship between ordinary bill/rent reminders and payment-instruction reminders. |
| Cards | Not Fully Defined | Define payment profile route UX with DOC-09 and DOC-19. |
| Referral | Not Fully Defined | Define route UX with DOC-13. |
| More | Not Fully Defined | Define overflow, management, and admin/user shortcut configuration behavior. |

## 7. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06B-001 | What final Pay+ visual layout, button order, disabled states, eligibility copy, and final action limits should be used? | Product / Design / Payments | Open |
| OQ-06B-002 | What route-level IA should apply to Offers, Me, More, Instructions, Receipts, Cards, Referral, and Support? | Product / Design | Open |
| OQ-06B-003 | What dashboard shortcut display cap, user reorder UI, restore-default behavior, and admin default mechanism should be used? | Product / Design / Operations | Open |
| OQ-06B-004 | What priority, collapse, expiry, and routing rules should apply to Important Notice / Action Required cards? | Product / Operations / Compliance | Open |
| OQ-06B-005 | What carousel card limit, auto-rotation behavior, ranking, targeting, and admin approval workflow should apply to Featured / What's New / Hot Offer placements? | Product / Growth / Operations | Open |
| OQ-06B-006 | What exact visual styling, card density, field-level copy, resend/reminder limit, share-button placement, and filter/sort design should apply to the Requests route? | Product / Design / Operations | Open |

## 8. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.8 | 2026-07-03 | Finalized `REQUESTS-NEW` route shell with section order, route boundary, linked-context selection, evidence gate, counterparty lookup, share/delivery rules, state behavior, and DOC-06C return behavior. |
| 0.1.7 | 2026-07-02 | Added `REQUESTS-NEW`, clarified request status labels, evidence-before-send gate, counterparty identifier, WhatsApp deeplink sharing, and return behavior between Requests and Bills routes. |
| 0.1.6 | 2026-07-02 | Clarified shortcut grid items as entry points rather than feature owners, narrowed Bills bottom-nav ownership, and added the app route-entry Mermaid diagram reference. |
| 0.1.5 | 2026-06-29 | Defined `REQUESTS-DETAIL` as its own DOC-06B screen and clarified linked DOC-06C bill/rent detail handoff. |
| 0.1.4 | 2026-06-25 | Drafted Requests route shell, including route definition, entry points, views, card fields, actions, empty states, and data-signal boundaries. |
| 0.1.3 | 2026-06-25 | Clarified Requests route definition, top-right inbox relationship, and request-not-payment boundary. |
| 0.1.2 | 2026-06-25 | Added route ownership rule to keep DOC-06B focused on route shells and handoffs while lifecycle and module behavior remain in owning documents. |
| 0.1.1 | 2026-06-25 | Cleaned publication wording and corrected dashboard copy formatting for official DOC-06B baseline use. |
| 0.1.0 | 2026-06-25 | Created as DOC-06B child document for dashboard, navigation, Pay+, shortcut, route taxonomy, and route workplan content. |
