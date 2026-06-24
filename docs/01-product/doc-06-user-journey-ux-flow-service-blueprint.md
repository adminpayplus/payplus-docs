---
document_id: DOC-06
title: User Journey, UX Flow & Service Blueprint
version: 0.20.0
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
last_updated: 2026-06-24
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-02 Business Model & Unit Economics
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-07 Content, Disclosure & User Authorization Specification
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
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06 - PayPlus User Journey, Product Flow, and UX Scope

## 1. Purpose

This document defines the required MVP user journeys, product flows, and UX scope for PayPlus.

PayPlus is an evidence-backed payment platform that allows payers and payees to create, view, match, authorize, and track bill, invoice, fee, rent, domestic service, and other approved obligation payment requests.

This document translates the master product requirements in DOC-05 into user-facing and operational journeys.

The MVP must support both:

1. **Payee-created payment request flow**
   - A payee creates an evidence-backed payment request and pushes it to a payer for review and payment.

2. **Payer-created payment flow**
   - A payer creates an evidence-backed payment or obligation record, links or invites a payee, and pushes payment to the payee after required review and authorization.

Both flows are MVP scope.

Tenancy and rent journeys are MVP scope. They must be independently enableable and may remain disabled for specific users, payees, categories, or launch phases until required controls are ready.

Domestic helper, driver, and personal service payment journeys are MVP scope where supported by acceptable evidence and enabled controls.

---

## 2. Product Journey Summary

PayPlus supports two-sided payment journeys between a payer and a payee.

A payment may originate from either side:

- a **payee** may create a bill, invoice, fee, rent, tenancy, agreement, employment/service record, statement, or other evidence-backed payment request and send it to a payer; or
- a **payer** may create a bill, invoice, fee, rent, tenancy, employment/service, or payment obligation record, link or invite a payee, and push payment to that payee.

In all cases:

- the payment must be linked to acceptable evidence unless an approved exception applies;
- the payer must review the request or payment context before payment;
- the payer must explicitly authorize payment before funds are charged or moved;
- the payee may view linked request/payment context when they are a platform user;
- admin, operational, or risk controls may apply;
- the system must maintain linked records, status history, receipts, and audit events;
- PayPlus must not operate as a wallet, stored-value account, cashout product, or unsupported peer-to-peer transfer service.

---

## 3. MVP Scope

### 3.1 In Scope

The MVP user journey scope includes:

- payer registration and login;
- payee registration and login;
- payer dashboard;
- payee dashboard;
- payer-created payment requests;
- payee-created payment requests;
- payer-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup;
- payee-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup;
- optional payee adoption or linking of payer-created records;
- payer review of payee-created requests;
- evidence upload, OCR/autofill review, user correction, and evidence verification;
- request linking, duplicate detection, and linked records;
- recipient review flows;
- payer acceptance, rejection, dispute, and clarification actions;
- payee acceptance, adoption, rejection, dispute, and clarification actions where applicable;
- payer authorization before payment;
- payment status tracking;
- payout or settlement status visibility where applicable;
- receipt or confirmation records;
- request history;
- basic notifications;
- admin review and operations workflows;
- audit trail visibility for admin;
- error, failure, dispute, cancellation, and exception states;
- controls preventing wallet, cashout, stored balance, and unsupported P2P behavior.

### 3.1.1 UX Scope Boundaries

This document defines journeys, screens, user decisions, service touchpoints, and visibility boundaries.

It should not duplicate detailed payment processing, payout, refund, notification, data model, risk rule, security, or compliance specifications. Where those details are needed, this document should identify the user-facing touchpoint and defer the detailed rule to the owning downstream document.

---

### 3.2 Out of Scope for MVP

The MVP user journey scope does not include:

- user wallet balances;
- stored-value accounts;
- user-controlled cash accounts;
- cash withdrawal;
- payer self-cashout;
- unsupported arbitrary peer-to-peer transfers;
- crypto payments;
- lending or credit issuance;
- investment, savings, or deposit account journeys;
- marketplace escrow journeys;
- unsupported open-loop money transfer journeys;
- automatic recurring payments unless separately approved;
- deferred user payment instruction for single-card and split-card payment is in scope under DOC-09 and is not an automatic recurring payment;
- fully automated compliance approval without admin or risk controls;
- advanced analytics dashboards;
- multi-entity enterprise treasury workflows;
- public API self-service configuration;
- complex role delegation or multi-admin hierarchy unless separately approved.

---

## 4. User Roles

| Role | Description | MVP Login? | Key Journey Responsibilities |
| --- | --- | ---: | --- |
| Payer | User who reviews, accepts, rejects, disputes, requests clarification, and authorizes payment. | Yes | Create payments, review requests, authorize payment, track status. |
| Payee | User who receives payments or creates payment requests. | Yes | Create requests, upload evidence, send requests to payers, adopt payer-created records, track status. |
| Admin / Operations | Internal user who reviews accounts, evidence, requests, risk, disputes, and exceptions. | Yes | Review, approve, reject, hold, investigate, and audit. |
| System | Automated services handling status changes, notifications, matching, audit events, and integrations. | No | Route, link, notify, validate, and record events. |

---

## 5. Core MVP User Journeys

The MVP must support the following essential journeys:

| # | Journey | Required for MVP |
| ---: | --- | ---: |
| 1 | Payer registration and login | Yes |
| 2 | Payee registration and login | Yes |
| 3 | Payer dashboard | Yes |
| 4 | Payee dashboard | Yes |
| 5 | Payee-created payment request flow | Yes |
| 6 | Payer-created payment flow | Yes |
| 7 | Payee-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup | Yes |
| 8 | Payer-created bill, invoice, fee, tenancy, rent, domestic service, or obligation setup | Yes |
| 9 | Optional payee adoption or linking of payer-created record | Yes |
| 10 | Payer review of payee-created request | Yes |
| 11 | Evidence upload, OCR/autofill review, correction, and verification | Yes |
| 12 | Accept, reject, dispute, and clarification flows | Yes |
| 13 | Payer payment authorization | Yes |
| 14 | User payment instruction and deferred payment action | Yes |
| 15 | Payment and payout status visibility | Yes |
| 16 | Linked payer/payee visibility | Yes |
| 17 | Admin review and operations touchpoints | Yes |
| 18 | Notification touchpoints | Yes |
| 19 | Receipt and history touchpoints | Yes |
| 20 | Failure, cancellation, dispute, and exception touchpoints | Yes |

---

## 6. Common Account Journey

### 6.1 Payer Account Journey

#### Purpose

Allows a payer to access PayPlus, create payments, review requests, authorize payment, and track payment history.

#### Required Payer Capabilities

A payer must be able to:

- register;
- verify phone by SMS OTP during registration;
- log in;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm material account, credential, payment profile, or contact changes using password, payment passcode, 2FA, or approved confirmation;
- access a payer dashboard;
- create a payer-initiated payment;
- create or link a bill, invoice, tenancy, agreement, statement, or obligation record;
- enter or select payee details;
- upload or link evidence;
- review and correct autofilled evidence fields where applicable;
- receive payee-created payment requests;
- review evidence before payment;
- accept a request;
- reject a request;
- dispute a request;
- request clarification;
- authorize payment;
- enter payment passcode before proceeding with payment authorization;
- view payment processing status;
- view failed payment status;
- view completed payment status;
- view receipts or confirmations;
- view request and payment history.

#### Payer Entry Points

The payer journey may begin when:

- the payer registers directly;
- the payer logs in to create a payment;
- the payer receives an invitation from a payee-created request;
- the payer receives a notification for a bill, invoice, tenancy, or payment request;
- the payer returns to view status or history.

---

### 6.2 Payee Account Journey

#### Purpose

Allows a payee to access PayPlus, create requests, upload evidence, send requests to payers, adopt payer-created records, and track payment or payout status.

#### Required Payee Capabilities

A payee must be able to:

- register;
- verify phone by SMS OTP during registration;
- log in;
- complete new-device 2FA and dormant-login reauthentication where required;
- confirm material account, credential, payout destination, or contact changes using password, payment passcode, 2FA, or approved confirmation;
- access a payee dashboard;
- create a payment request;
- create or link a bill, invoice, tenancy, agreement, statement, or obligation record;
- enter or select payer details;
- upload or link evidence;
- review and correct autofilled evidence fields where applicable;
- send a request to a payer;
- receive payer-created bill/payment records;
- review payer-created records;
- accept or adopt payer-created records where applicable;
- reject payer-created records where applicable;
- dispute payer-created records where applicable;
- request clarification where applicable;
- respond to payer clarification requests;
- respond to disputes where applicable;
- view request status;
- view payment status;
- view payout or settlement status where applicable;
- view receipts or confirmations;
- view request and payment history.

#### Payee Entry Points

The payee journey may begin when:

- the payee registers directly;
- the payee logs in to create a request;
- the payee receives an invitation from a payer-created record;
- the payee receives notification of payment status;
- the payee returns to respond to a dispute or clarification request;
- the payee returns to view history.

---

## 7. Logged-in Home Dashboard and Navigation IA

### 7.1 Design Intent

The logged-in Home Dashboard is the default landing screen after login.

It must be task-first. It should prioritize urgent user actions, payment-related obligations, request status, payment instructions, and recent payment records before promotional discovery.

The dashboard is not a marketing page. Promotions, partner offers, hot offers, PayPlus events, and feature announcements may appear only through controlled placements and must not obscure payment tasks or status visibility.

This section defines the designated dashboard flow and layout baseline for MVP discussion. It is not the finalized UI design, visual design, component specification, or exact route-level screen specification. Exact UI details remain subject to later DOC-06 refinement and future design/specification work.

Visual reference: `docs/diagrams/payplus-home-dashboard-mvp-wireframe.svg` is a companion wireframe for this section. It supports human and AI understanding of layout hierarchy but does not override this document.

---

### 7.2 Bottom Navigation

MVP bottom navigation should use five primary destinations.

| Nav Item | Definition | Route Relationship | Current Status |
| --- | --- | --- | --- |
| Home | Default task-first dashboard. | Opens Home Dashboard. | Discussion baseline |
| Bills | Obligation and record management area. | Opens Bills area covering bills, rent/tenancies, requests, instructions, reminders, receipts, and related records. Exact sub-navigation remains to be finalized. | Discussion baseline |
| Pay+ | Central payment and request action. | Opens a slide-up action sheet for payment, setup, continuation, and request-payment actions. Exact visual UI and final ordering remain to be finalized. | Working baseline |
| Offers | Full promotion discovery area. | Opens Offers Hub covering hot offers, card partner offers, PayPlus campaigns, coupon/voucher library, referral, and What’s New. Exact route IA remains to be finalized. | Discussion baseline |
| Me | Account and user control area. | Opens profile, settings, security, notifications, privacy, support, cards/payment methods, and account controls. Exact route IA remains to be finalized. | Discussion baseline |

`Pay+` should be visually treated as the primary center action in the bottom navigation.

---

### 7.3 Pay+ Action Sheet

Tapping `Pay+` should open a slide-up action sheet instead of routing directly to one screen.

The Pay+ action sheet should contain user-friendly actions for starting or continuing the core PayPlus journey. It should not expose internal terms such as payment instruction, capture layer, or verification layer to users.

Working baseline Pay+ actions:

- Pay a Bill / Fee;
- Pay Rent;
- Add Bill / Rent;
- Continue Payment;
- Request Payment.

`Request Payment` should appear by default for all users, unless the request feature/module is disabled or the account is restricted. A user may be both payer and payee, such as a landlord who is also a renter elsewhere.

`Add Bill / Rent` should include scan QR, upload bill/invoice/tenancy/evidence, and manual entry as input methods inside the setup flow. QR or upload should not be a standalone Pay+ payment action because PayPlus must remain evidence-backed and must not behave as generic QR instant payment.

`Continue Payment` should cover deferred payment instructions, unfinished split-card payments, failed or retry payment legs, interrupted checkout, and other payment actions that require the user to resume.

The Pay+ action sheet must avoid creating wallet, stored-value, cashout, unsupported P2P, or automatic recurring-payment behavior.

Pay+ actions may start or continue a user journey, but must not bypass evidence capture, bill/rent setup, payee validation, risk checks, authorization, fee calculation, or payment instruction rules.

Exact visual layout, button order, empty states, disabled states, eligibility copy, and final action limits remain open.

---

### 7.4 Home Dashboard Section Order

The Home Dashboard should use the following MVP section order.

| Order | Section | Definition | Display Rule | Route Relationship |
| ---: | --- | --- | --- | --- |
| 1 | Header | Greets the user and provides quick access to high-priority utilities. | Always shown. | Inbox and coupon/voucher library icons route to their respective screens. |
| 2 | Important Notice / Action Required | Combined swipeable section for urgent actions, account messages, system messages, announcements, late handling from payer/payee, expiring tenancies, and other important updates. | Disappears if empty. User may collapse with a close button. Eligible item types are initially defined here and may be expanded later. | Each card routes to the relevant task, detail, or message route. |
| 3 | Shortcut Grid | Operational shortcuts for common management tasks. Must not duplicate Pay+ direct payment-start actions. | MVP displays 8 shortcuts. Shortcut set, default order, visibility, and enablement must be configurable. | Each shortcut routes to its related management area. |
| 4 | Featured / What’s New / Hot Offer | One combined carousel for approved PayPlus announcements, partner campaigns, feature updates, hot offers, and service events. | Must be admin-controllable. Use one combined carousel at this stage. | Routes to Offers Hub, offer detail, announcement detail, or feature route. |
| 5 | Upcoming Bills / Rent | Summary of upcoming bills, fees, rent, tenancy obligations, due reminders, and related next actions. | Show when active or saved obligations exist. Detailed card fields may be refined later. | Routes to Bills area or the specific bill/tenancy detail. |
| 6 | Recent Activity | Limited list of recent transactions and status records. | Show recent items only, capped by dashboard display rules. | Arrow or View More routes to Recent Activity detail page. |

Dashboard section order may be refined later only through explicit design review. This baseline intentionally places the Featured / What’s New / Hot Offer carousel below shortcuts and above Upcoming Bills / Rent.

---

### 7.5 Header Utilities

| Element | Definition | Route Relationship |
| --- | --- | --- |
| Greeting | User recognition area. | No route required, or profile route if tapped. |
| Inbox icon | Notifications, messages, payment alerts, request updates, support replies, system notices, and announcements. | Notification / Inbox route. |
| Coupon icon | Shortcut to user’s available coupon/voucher library. | Coupon / Voucher Library route. |

---

### 7.6 Shortcut Grid

The shortcut grid provides quick access to common non-payment-start tasks.

MVP shortcut grid:

| Shortcut | Definition | Route Relationship |
| --- | --- | --- |
| Requests | Payee-created or payer-linked requests requiring review, response, acceptance, rejection, query, dispute, or payment action. | Payment Requests route. |
| Instructions | Deferred payment instructions, split-card progress, pending funding legs, expired instructions, and action-required instructions. | Payment Instructions route. |
| Bills & Tenancies | Saved bills, fee records, rent records, tenancy records, evidence status, due dates, and obligation details. | Bills & Tenancies route. |
| Receipts | Payment receipts, proof of payment, statements, completed records, refund/reversal records, and related transaction evidence. | Receipts / Activity route. |
| Reminders | User-set due reminders for bills, rent, tenancy obligations, and manual reminders. | Opens `BILLS-REMINDER-LIST`. |
| Cards | Tokenized payment profiles, cards, payment methods, card status, and payment-method settings. | Cards / Payment Methods route. |
| Referral | Referral / MGM entry point and referral reward status where enabled. | Referral route and Offers Hub referral section. |
| More | Opens remaining or secondary shortcuts and services. | More Shortcuts / Services route or sheet. |

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

### 7.7 Featured / What’s New / Hot Offer Carousel

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

### 7.8 Upcoming Bills / Rent

The Upcoming Bills / Rent section should summarize the user’s next relevant obligations.

Initial dashboard card information may include:

- biller, payee, landlord, or obligation name;
- category;
- amount;
- due date or rent period;
- payment status;
- evidence status where relevant;
- next action.

Exact card layout, maximum visible items, empty state, and filtering rules remain open and should be refined in later DOC-06 route-level work.

---

### 7.9 Recent Activity

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

### 7.10 Route IA Workplan and Placeholder Titles

DOC-06 must next define what users see, what buttons exist, what each button does, and how route areas interact. The following titles are intentionally preserved as the working map so the route-level UI discussion does not lose scope.

| Area | Purpose of Future DOC-06 Detail | Current Status |
| --- | --- | --- |
| Bottom Navigation Route Map | Define how `Home`, `Bills`, `Pay+`, `Offers`, and `Me` relate to top-level routes and deep links. | Title preserved / not finalized |
| Pay+ Action Sheet Detail | Define final label order, empty states, disabled states, permission rules, and route destinations for the working baseline actions. | Working baseline / not finalized |
| Bills Tab IA | Define bill, fee, rent, tenancy, evidence, reminder, payment history, and setup sections under the Bills route. | Working baseline / not finalized |
| Offers Hub IA | Define offer discovery, hot offers, card partner offers, coupon/voucher library, referral, What's New, and campaign detail routes. | Title preserved / not finalized |
| Me Area IA | Define account, security, privacy, notification preferences, support, cards/payment methods, and user control routes. | Title preserved / not finalized |
| More Shortcuts IA | Define secondary shortcuts and services not shown in the first eight dashboard shortcuts. | Title preserved / not finalized |
| Requests Route | Define received requests, sent requests, request creation, response actions, status tracking, and request delivery records. | Title preserved / not finalized |
| Instructions Route | Define deferred payment instructions, split-card progress, retry/failed legs, pending actions, cancellation, expiry, and continuation paths. | Title preserved / not finalized |
| Bills & Tenancies Route | Define saved obligation list, tenancy detail, evidence status, payee/landlord detail, due dates, and linked payment actions. | Title preserved / not finalized |
| Receipts / Activity Route | Define receipts, proof of payment, statements, refund/reversal records, and transaction details. | Title preserved / not finalized |
| Reminders Route | Define due reminders, user-set reminders, notification settings, and reminder destinations. | Title preserved / not finalized |
| Cards / Payment Methods Route | Define tokenized card/payment profile management, card status, default card, and payment method issue handling. | Title preserved / not finalized |
| Referral Route | Define referral entry, invitation link, progress, reward status, and relationship with Offers Hub. | Title preserved / not finalized |
| Admin-Configurable UI Marker List | Mark app UI elements that require admin configuration later without drafting admin UI in DOC-06. | Title preserved / DOC-22 owns admin UI |

App UI elements that currently require admin configuration markers include Pay+ action visibility, shortcut visibility/order/defaults, Featured / What's New / Hot Offer carousel placement, Important Notice / Action Required item types, feature/module enablement, request-payment availability, and route-level gating by user type, category, launch phase, risk state, or compliance restriction.

---

### 7.11 Bills Tab IA Working Baseline

This section defines the working baseline for the `Bills` bottom-navigation route. It is a route-level UX and behavior specification, not a final visual UI design.

Route-level UI drafting rule: each route should define user-facing behavior and identify material events/data signals required for AI-ready data-engine support. Detailed schema, event taxonomy, lineage, model registry, and warehouse design remain owned by DOC-18.

#### 7.11.1 Route and Subsection IDs

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
| `BILLS-ACTIVITY` | Sub-route / screen or sheet | Bill/rent activity timeline | `View Activities` from bill/rent detail pages | User-facing payment activity plus limited request and evidence outcome milestones for one selected bill/rent record. This is not global history, evidence management, or an internal audit log. |
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
| Tap `Add Bill / Rent` | `BILLS-ROOT` or Pay+ action sheet | Opens `BILLS-ADD`. |
| Tap `Pay` on a payer-side card/detail | `BILLS-PAY`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Opens payment/checkout flow governed by DOC-09. DOC-06 owns the entry point and route handoff only. |
| Tap `Request` on a payee-side card/detail | `BILLS-RECEIVE`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Sends, resends, or opens request-delivery action for a verified payee-created request before payer acceptance. Exact request delivery method and notification behavior must follow DOC-08 and later DOC-22 controls. |
| Tap `Remind Payer` on a payee-side card/detail | `BILLS-RECEIVE`, `BILLS-CARD-BILL`, `BILLS-CARD-RENT`, `BILLS-DETAIL-BILL`, or `BILLS-DETAIL-RENT` | Opens or triggers an approved payer reminder action for the selected request. This is a payee-to-payer request reminder, not the user's own `BILLS-REMINDER-LIST` reminder record unless later explicitly linked. |
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

- DOC-06 owns the user-facing entry point, route handoff, back/return behavior expectation, and the fact that payer-side `Pay` opens checkout.
- DOC-09 owns the payment/checkout screen content and behavior, including payment quote, fee display, promotion quote, card or payment profile selection, split-card allocation, authorization, 2FA/passcode gates, deferred payment instruction, revalidation, error handling, and payment-state outcomes.
- DOC-07 owns required user-facing wording and disclosures; DOC-08 owns checkout-related notifications and receipts; DOC-13 owns promotion/coupon/voucher checkout treatment; DOC-15 owns masking and data visibility; DOC-19 owns authentication/security controls; DOC-18 owns route events and data signals.

#### 7.11.2 Top-Level Views

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

#### 7.11.3 Filters

| View | MVP Filters | Rule |
| --- | --- | --- |
| `To Pay` | All, Action Required, Due Soon, Paid, Archived | `All` excludes archived records. `Archived` shows only archived records. |
| `To Receive` | All, Action Required, Due Soon, Received, Archived | `All` excludes archived records. `Archived` shows only archived records. |

Action-required items should be visible through a filter and through status badges on the relevant card.

#### 7.11.4 Bill / Fee Card

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

#### 7.11.5 Bill / Fee Detail Page

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
| View Activities | Opens `BILLS-ACTIVITY` for payment activity and limited evidence milestones for this obligation. |
| Set Reminder / Edit Reminder | Opens `BILLS-REMINDER-DETAIL` for this obligation. |
| Edit Details | Opens editable bill/payee/detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

Payee-side detail actions when opened from `BILLS-RECEIVE`:

| Action | Route / Behavior |
| --- | --- |
| Request | Available before payer acceptance; sends, resends, or opens request-delivery action. Disappears after payer acceptance. |
| View Activities | Opens `BILLS-ACTIVITY` for payment activity, request milestones, and limited evidence milestones for this obligation. |
| Set Reminder / Edit Reminder | Opens reminder behavior for the selected record where the reminder belongs to the current user; payer-facing request reminders are governed by DOC-08 and DOC-22. |
| Edit Details | Opens editable bill/payee/detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

The bill detail page should include a `Bill / Invoice` evidence status area. It should show current evidence status and extracted bill/invoice fields approved for display. Evidence management is not a default primary detail action. If evidence is missing, rejected, expired, or otherwise action-required, the status area should show a contextual action that opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD`. Extracted fields that belong to the bill/invoice record should be displayed in the bill detail area, not duplicated inside evidence detail.

#### 7.11.6 Rent / Tenancy Card

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

#### 7.11.7 Rent / Tenancy Detail Page

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
| View Activities | Opens `BILLS-ACTIVITY` for payment activity and limited evidence milestones for this rent record. |
| Set Reminder / Edit Reminder | Opens `BILLS-REMINDER-DETAIL` for this rent record. |
| Edit Details | Opens editable rent/landlord/payment detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

Payee-side detail actions when opened from `BILLS-RECEIVE`:

| Action | Route / Behavior |
| --- | --- |
| Request | Available before payer acceptance; sends, resends, or opens request-delivery action. Disappears after payer acceptance. |
| View Activities | Opens `BILLS-ACTIVITY` for payment activity, request milestones, and limited evidence milestones for this rent record. |
| Set Reminder / Edit Reminder | Opens reminder behavior for the selected record where the reminder belongs to the current user; payer-facing request reminders are governed by DOC-08 and DOC-22. |
| Edit Details | Opens editable rent/landlord/payment detail fields subject to verification and audit rules. |
| Archive | Archives the record; user-facing delete should not be the default MVP action. |

The rent detail page should include a `Rental Doc` evidence status area. `Rental Doc` covers tenancy agreements and other approved rent-supporting evidence, such as rent demand, stamp duty document, CR109, HKHA tenancy card, carpark invoice, or property management notice. It should show current evidence status and extracted rental fields approved for display. Evidence management is not a default primary detail action. If evidence is missing, rejected, expired, or otherwise action-required, the status area should show a contextual action that opens `BILLS-EVIDENCE-DETAIL` or `BILLS-EVIDENCE-UPLOAD`. Extracted fields that belong to the rent/tenancy record should be displayed in the rent detail area, not duplicated inside evidence detail.

Rent normally should not require a new invoice for each payment cycle unless tenancy evidence expires, changes, is replaced, is rejected, or is flagged by risk/review rules.

#### 7.11.8 Bill / Rent Activity Sub-Route

`BILLS-ACTIVITY` is a user-facing sub-route for one selected bill/rent record. It should be opened from `View Activities` inside `BILLS-DETAIL-BILL` or `BILLS-DETAIL-RENT`.

Primary owner: DOC-06.

Related ownership:

| Area | Owning Document |
| --- | --- |
| Notification and receipt/proof messaging | DOC-08 |
| Payment status and payment-detail linkage | DOC-09 |
| Transfer, payout, and rejected payout status | DOC-10 |
| Returned, refunded, reversed, disputed, or chargeback-related outcomes | DOC-11 |
| Evidence approval/rejection meaning | DOC-12 |
| Masking and role-based visibility | DOC-15 |
| Full event, audit, data model, and lineage | DOC-18 |
| Admin/internal audit and evidence review history | DOC-22 |

`BILLS-ACTIVITY` should include:

- payment activity entries;
- limited request lifecycle milestones where relevant to the selected bill/rent, such as request sent, accepted, rejected, expired, or cancelled;
- transfer or payout outcome where user-relevant;
- returned, rejected, failed, or under-review payment outcomes;
- receipt or payment proof access;
- limited evidence milestones, only where user-relevant.

`BILLS-ACTIVITY` should not include:

- ordinary bill/rent detail edit history;
- OCR/upload processing logs;
- every evidence status change;
- full request workflow logs;
- internal approval workflow history;
- admin audit trail;
- global transaction history;
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
| Status | User-facing status such as `Paid`, `Transferred`, `Processing`, `Under Review`, `Returned`, `Rejected`, or `Failed`. |

Status meaning should remain high-level:

| Status | User Meaning | Owning Detail |
| --- | --- | --- |
| `Paid` | Payer funding/payment completed. | DOC-09 |
| `Transferred` | PayPlus transfer/payout to payee completed. | DOC-10 |
| `Processing` | Payment, settlement, or transfer is still in progress. | DOC-09 / DOC-10 |
| `Under Review` | Payment or payout requires review before completion. | DOC-14 / DOC-22 |
| `Returned` | Funds were returned, refunded, reversed, or recovered. | DOC-11 |
| `Rejected` | Payment or payout could not proceed or was rejected. | DOC-09 / DOC-10 / DOC-11 |
| `Failed` | Payment attempt or transfer failed. | DOC-09 / DOC-10 |

Tapping one activity entry should open `BILLS-ACTIVITY-DETAIL` or a later payment detail route if separately defined.

`BILLS-ACTIVITY-DETAIL` should show:

- payment date;
- bill/rent name;
- recipient/payee name;
- amount;
- payment status;
- transfer/payout status where applicable;
- payment reference number, if any;
- receipt/proof download where available;
- link to payment detail where needed and separately governed.

Request and evidence milestones in `BILLS-ACTIVITY` should remain minimal. MVP user-facing evidence milestones should be limited to:

- evidence approved;
- evidence rejected;
- evidence update required, only where it blocks payment readiness.

Detailed evidence management belongs to `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`. Full evidence audit history belongs to DOC-18 and DOC-22.

#### 7.11.9 Add Bill / Rent Flow

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
| Account / Payout Details | Account name, bank name, and bank account required where bank transfer applies. | Account name, bank name, and bank account required where bank transfer applies. |

QR scanning belongs inside `BILLS-ADD` and `BILLS-EVIDENCE-UPLOAD` as a setup and evidence-capture aid. It must not allow unsupported instant payment without evidence, verification, and payer authorization.

Frequency supports due-date display, reminder defaults, bill/rent management, analytics, and payment-readiness UX. It must not be represented as automatic recurring payment, recurring card authorization, or recurring gateway submission unless a separate approved recurring payment model is later defined.

#### 7.11.10 Evidence Sub-Route

Evidence is a supporting attachment/status layer linked to a bill/rent record. It is not a standalone user-facing card or independent management object.

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

Evidence archive behavior:

- archive hides evidence from normal bill/rent UI;
- archive must not hard-delete evidence from the database;
- archived evidence remains retained under DOC-15 and DOC-18;
- archived/previous evidence should be retrievable through a controlled account records/archive area, likely under `Me`; exact route remains open.

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
| `Paid` / `Received` | Completed payment state, depending payer/payee view. |
| `Archived` | Bill/rent hidden from normal list. |

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

#### 7.11.11 Reminder Route

Reminder routes must use specific route IDs:

- `BILLS-REMINDER-LIST` for the reminder management screen.
- `BILLS-REMINDER-DETAIL` for creating or editing one reminder.

`BILLS-REMINDER` may be used only as a shorthand discussion label. AI build documents should use the specific list/detail route ID so screens, sheets, and actions are not confused.

Reminder source type should be stored internally without overexposing technical labels to users. MVP source types should include system due-date reminder, user manual reminder, and user custom override reminder. Deferred payment instruction reminders are governed by DOC-09 and remain an open placement question for the Bills reminder management UI.

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

User-created or custom reminder records may be deleted. System/default due-date reminders should normally be disabled rather than hard-deleted. Deferred payment instruction reminders are excluded from this deletion flow unless a later decision explicitly brings them into reminder management.

Due soon, overdue, evidence rejected, and payment-readiness action states belong primarily to the linked bill/rent card and detail page. Reminder cards should focus on reminder state such as next reminder date, reminder off, reminder expired, or custom reminder set.

DOC-08 owns notification IDs, channel matrix, templates, user preferences, retry behavior, and delivery logging. DOC-09 owns deferred payment instruction reminders and return-to-checkout behavior. DOC-15 owns sensitive-data display and masking. DOC-18 owns final schema, event taxonomy, lineage, and analytics definitions.

Open question: Should deferred payment instruction reminders also appear in `BILLS-REMINDER-LIST`, or remain only under Instructions, dashboard action-required surfaces, and the DOC-09 checkout/payment instruction flow?

#### 7.11.12 Evidence Structure and UX

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

#### 7.11.13 Payer-Created and Payee-Created Logic

| Scenario | UX Rule | Linking Rule |
| --- | --- | --- |
| Payer creates bill/rent for own payment | Payee acceptance is not required before the payer may proceed, provided required evidence, verification, risk, payout, and authorization gates pass. | If the payee is also a PayPlus user, optional linking may be initiated or accepted through an approved user action. |
| Payee creates bill/rent/request for payer | Payer acceptance is required after verification and before payment authorization. | The payer is linked only after in-app acceptance or approved invitation/deeplink flow. |
| Both parties are PayPlus users | Both sides may view the same linked bill, tenancy, request, or payment context after accepted linking, subject to role-based permissions. | Linking must be user-initiated or user-accepted; automatic user-to-user matching is not allowed as a UX assumption. |
| Payee is not a PayPlus user | Payer may still pay an approved evidence-backed obligation to a valid payee record or payout destination. | The payee may remain a non-user payee record unless invited and onboarded later. |

Phone number, user ID, app link, WhatsApp deeplink, QR code, or other approved invitation mechanisms remain to be defined. Search, invitation, and acceptance design must follow DOC-15 privacy and DOC-19 security controls.

#### 7.11.14 Action-Required UX

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

#### 7.11.15 Data and Intelligence Signals

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
- payee-created request received and accepted/rejected/disputed;
- user-initiated participant invitation sent;
- participant invitation accepted or declined;
- payment started from card or detail page;
- reminder created, edited, disabled, deleted, fired, opened, ignored/dismissed, or followed by payment start;
- record archived;
- bill/rent activity timeline opened;
- activity entry detail opened;
- receipt or payment proof downloaded;
- evidence milestone shown in activity timeline.

These events should support product analytics, operational monitoring, risk review, support investigation, and future approved AI/payment-intelligence use under DOC-15 and DOC-18. They must not create automatic user-to-user matching or overexpose sensitive evidence data.

---

## 8. Payee-Created Payment Request Flow

### 8.1 Purpose

Allows a payee to create an evidence-backed payment request and push it to a payer for review and payment.

This is a core MVP journey.

---

### 8.2 Primary Flow

1. Payee logs in.
2. Payee selects **Create Payment Request**.
3. Payee enters or selects payer information.
4. Payee enters request details:
   - amount;
   - due date;
   - category;
   - description;
   - reference number where applicable.
5. Payee creates or links an obligation record, such as:
   - bill;
   - invoice;
   - tenancy agreement;
   - rent demand;
   - payment statement;
   - service agreement;
   - official notice;
   - contract;
   - other acceptable proof of obligation.
6. Payee uploads or links evidence.
7. System processes evidence using OCR/document AI where enabled.
8. System autofills eligible fields and lets payee review or correct them.
9. System validates required fields, evidence verification outcome, duplicate/reused evidence indicators, and risk routing.
10. System creates a payment request record.
11. System links evidence and final evidence snapshot to the request.
12. System assigns request status.
13. Payee selects an available request delivery method, such as in-app message, app link, WhatsApp deeplink, QR code, or other approved channel.
14. System sends the request notification or invitation to the payer through the selected approved channel.
15. Payer logs in or registers.
16. Payer reviews:
    - payee identity/details;
    - amount;
    - due date;
    - category;
    - description;
    - evidence;
    - fees where applicable;
    - payment terms;
    - PayPlus disclosures where applicable.
17. Payer selects one of:
    - accept;
    - reject;
    - dispute;
    - request clarification.
18. If payer accepts, payer proceeds to payment authorization.
19. Payer explicitly authorizes payment.
20. System processes payment through approved payment partner or sandbox integration.
21. Payee receives payment according to approved payout or settlement rules.
22. Payer and payee can view the linked request/payment context.
23. System stores receipt, status history, and audit trail.

---

### 8.3 Payee-Created Request Status Path

A typical payee-created request may move through the following statuses:

```text
Draft
Submitted
Sent
Viewed
Accepted
Approved for Payment
Payment Authorized
Payment Processing
Paid
```

Alternative states may include:

```text
Clarification Requested
Rejected
Disputed
Failed
Cancelled
Expired
```

### 8.4 Required Controls

| Control | Requirement |
| --- | --- |
| Evidence required | Request cannot proceed to payment without required evidence unless an approved exception applies. |
| Evidence verification | OCR/autofill, user correction, duplicate detection, and verification outcomes follow DOC-12. |
| Payer review required | Payer must review the request context before payment authorization. |
| Payer authorization required | Payee-created request must not trigger payment without payer authorization. |
| Linked records required | Request, evidence, payer, payee, payment, status history, and audit events must be linked. |
| Admin/risk controls | Request may be subject to admin, operational, or risk review. |
| Unsupported P2P blocked | Request must be tied to a valid evidence-backed obligation. |

---

## 9. Payer-Created Payment Flow

### 9.1 Purpose

Allows a payer to create an evidence-backed payment or obligation record, link or invite a payee, and push payment to the payee after required review and authorization.

This is a core MVP journey.

### 9.2 Primary Flow

1. Payer logs in.
2. Payer selects **Create Payment**.
3. Payer enters or selects payee information.
4. Payer enters payment details:
   - amount;
   - due date;
   - category;
   - description;
   - reference number where applicable.
5. Payer creates or links an obligation record, such as:
   - bill;
   - invoice;
   - tenancy agreement;
   - rent demand;
   - payment statement;
   - service agreement;
   - official notice;
   - contract;
   - other acceptable proof of obligation.
6. Payer uploads or links evidence.
7. System processes evidence using OCR/document AI where enabled.
8. System autofills eligible fields and lets payer review or correct them.
9. System validates required fields, evidence verification outcome, duplicate/reused evidence indicators, and risk routing.
10. System creates a payment request or payment intent record.
11. System links evidence and final evidence snapshot to the record.
12. System matches payee if already a PayPlus user or creates an invite/link record.
13. System sends notification or invitation to payee where applicable.
14. Payee logs in or registers.
15. Payee reviews the payer-created record.
16. Payee selects one of:
    - accept/adopt;
    - reject;
    - dispute;
    - request clarification.
17. Admin/system reviews request and evidence according to applicable risk controls.
18. Payer reviews final payment summary.
19. Payer explicitly authorizes payment.
20. System processes payment through approved payment partner or sandbox integration.
21. Payee receives payment according to approved payout or settlement rules.
22. Payer and payee can view the linked payment context.
23. System stores receipt, status history, and audit trail.

### 9.3 Payer-Created Payment Status Path

A typical payer-created payment may move through the following statuses:

```text
Draft
Submitted
Sent
Viewed
Accepted
Approved for Payment
Payment Authorized
Payment Processing
Paid
```

Alternative states may include:

```text
Clarification Requested
Rejected
Disputed
Failed
Cancelled
Expired
```

### 9.4 Required Controls

| Control | Requirement |
| --- | --- |
| Evidence required | Payment cannot proceed without required evidence unless an approved exception applies. |
| Evidence verification | OCR/autofill, user correction, duplicate detection, and verification outcomes follow DOC-12. |
| Payee record required | Payee must be linked, invited, or represented by a valid payee record and payout destination where required. |
| Optional payee adoption supported | Payee must be able to accept/adopt payer-created records for linking where applicable, but payer-created payment must not require payee acceptance by default. |
| Payer authorization required | Payment cannot be processed without explicit payer authorization. |
| Self-cashout blocked | Payer cannot use PayPlus to cash out to themselves. |
| Unsupported transfer blocked | Payment must be tied to a valid evidence-backed obligation. |
| No wallet behavior | System must not create user wallet balances or stored-value accounts. |

---

## 10. Shared Bill, Tenancy, Invoice, or Obligation Journey

### 10.1 Purpose

Allows either a payer or payee to create an obligation record that can support a payment request or payment.

An obligation record may become shared only through an approved user action, such as payer acceptance of a payee-created request or optional payee linking/adoption of a payer-created record. PayPlus should not assume automatic user-to-user matching.

An obligation record may represent:

- bill;
- invoice;
- tenancy agreement;
- rent demand;
- payment statement;
- service agreement;
- official notice;
- contract;
- other acceptable proof of payment obligation.

### 10.2 Payee-Created Obligation Path

1. Payee logs in.
2. Payee creates a bill, invoice, tenancy, agreement, statement, or obligation record.
3. Payee enters payer information.
4. Payee uploads supporting evidence.
5. System processes evidence and autofills eligible obligation fields where enabled.
6. Payee reviews or corrects autofilled fields.
7. System validates evidence and creates obligation record.
8. System links evidence and final evidence snapshot to obligation record.
9. Payee creates or sends payment request.
10. Payee selects an available request delivery method, such as in-app message, app link, WhatsApp deeplink, QR code, or other approved channel.
11. Payer is notified or invited through the selected approved channel.
12. Payer reviews the obligation, evidence summary, and request.
13. Payer accepts, rejects, disputes, or requests clarification.
14. If accepted, payer may authorize payment.
15. System links payer, payee, request, evidence, and payment records.

### 10.3 Payer-Created Obligation Path

1. Payer logs in.
2. Payer creates a bill, invoice, tenancy, agreement, statement, or obligation record.
3. Payer enters payee information.
4. Payer uploads supporting evidence.
5. System processes evidence and autofills eligible obligation fields where enabled.
6. Payer reviews or corrects autofilled fields.
7. System validates evidence and creates obligation record.
8. System links evidence and final evidence snapshot to obligation record.
9. Payer may proceed to payment once required evidence, verification, risk, payout, and authorization gates pass.
10. Payee may be invited or linked where useful, but payee acceptance is not required before payer-created payment unless a category, risk rule, payout rule, or compliance gate explicitly requires it.
11. If the payee is a PayPlus user and linking is initiated, payee logs in or registers and reviews the obligation context.
12. Payee may accept/adopt, reject, dispute, or request clarification for linkage purposes.
13. If adopted, payee becomes linked to the shared obligation context.
14. System links payer, payee, obligation, evidence, and payment records according to permissions.

### 10.4 Adoption Rules

| Rule | Requirement |
| --- | --- |
| Payer-created payment | Payer-created obligations may proceed without payee acceptance where evidence, verification, risk, payout, and authorization gates pass. |
| Optional payee adoption | Payee may accept/adopt payer-created obligation records for two-sided visibility, communication, and linked recordkeeping where applicable. |
| Payer acceptance | Payer may accept payee-created requests before authorizing payment. |
| No forced adoption | A recipient should not be forced to accept an inaccurate record. |
| Dispute support | Recipient may dispute or request clarification. |
| Linked context | Once accepted/adopted, both sides should see the linked context subject to permissions. |
| Audit trail | Adoption, rejection, clarification, and dispute actions must be logged. |

---

## 11. Recipient Review Journey

### 11.1 Purpose

Allows the recipient of a request or obligation record to review the details and respond.

### 11.2 Recipient Review Matrix

| Creator | Recipient | Recipient Review Actions |
| --- | --- | --- |
| Payee creates payment request | Payer | Accept, reject, dispute, request clarification, authorize payment after acceptance. |
| Payer creates payment/obligation record | Payee | Optional accept/adopt, reject, dispute, or request clarification for linkage only; payer payment does not require payee acceptance unless a specific gate requires it. |

### 11.3 Required Review Information

The recipient should be able to view:

- creator identity or profile details;
- payer details;
- payee details;
- amount;
- due date;
- category;
- description;
- evidence;
- obligation type;
- request status;
- payment status where applicable;
- fees where applicable;
- relevant disclosures;
- clarification or dispute history where applicable.

### 11.4 Recipient Actions

| Action | Description |
| --- | --- |
| Accept | Recipient accepts the request or record as valid. |
| Adopt | Payee accepts a payer-created bill, tenancy, invoice, or payment context as linked to them. |
| Reject | Recipient rejects the request or record. |
| Dispute | Recipient disputes the request, evidence, amount, payee, payer, or obligation context. |
| Request clarification | Recipient asks the creator for more information or correction. |
| Authorize payment | Payer-only action that permits payment processing. |

### 11.5 Payment Authorization Boundary

Only the payer can authorize payment.

A payee may accept or adopt a payer-created record for linked visibility and communication, but a payee cannot authorize payment from the payer and payee adoption must not be treated as the payer's payment authorization.

---

## 12. Evidence Upload and Review Journey

### 12.1 Purpose

Ensures each payment is linked to acceptable evidence before it can proceed to payment.

DOC-12 owns detailed bill category, OCR/document AI, extracted field, autofill, user correction, duplicate detection, verification outcome, and payee matching requirements. DOC-06 describes only the user journey and UX touchpoints.

### 12.2 Accepted MVP Evidence Types

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
- other admin-approved proof of payment obligation.

### 12.3 Evidence Upload and Verification Flow

1. User creates or updates a request, bill, rent, or obligation record.
2. User provides evidence through `BILLS-ADD` or `BILLS-EVIDENCE-UPLOAD` where evidence is required.
3. System validates file type and required metadata where applicable.
4. System processes OCR/document AI where enabled.
5. System extracts eligible fields and autofills the bill/rent/request setup fields.
6. User reviews and corrects the bill/rent/request details before submission.
7. System stores raw evidence, extraction result, user correction, and final evidence snapshot where applicable.
8. System links evidence to the request or obligation.
9. System applies duplicate/reused evidence, mismatch, completeness, same-party, and risk checks.
10. System assigns an evidence status.
11. Evidence status updates the bill/rent payment readiness status according to the Bills route mapping.
12. Low-risk accepted evidence becomes available for role-based review and payment eligibility checks.
13. Red-flag evidence routes to user clarification or admin review.

### 12.4 Evidence Review Access

| Role | Evidence Access |
| --- | --- |
| Payer | Can review evidence before authorizing payment. |
| Payee | Can view evidence attached to their own created requests or linked received payments. |
| Admin / Operations | Can view evidence for review, investigation, support, compliance, and audit. |
| System | Links evidence to request/payment records and logs actions. |

### 12.5 Evidence Rules

| Rule | Requirement |
| --- | --- |
| Evidence required | Payment request cannot proceed to payment without required evidence unless an approved exception applies. |
| Evidence linked | Evidence must be linked to a payment request, obligation, or payment record. |
| OCR/autofill | Where enabled, extracted fields should assist request creation but must not remove user review. |
| User correction | Users must be able to correct autofilled fields before submission. |
| Extractable vs displayable | Sensitive extracted fields may be stored under controls without being shown broadly in UI. |
| Duplicate warning | Duplicate or reused evidence may trigger user warning and admin review, subject to DOC-12 and privacy rules. |
| Verification outcome | Pending user clarification, pending admin review, rejected, duplicate suspected, or fraud/risk escalated outcomes must block payment eligibility until resolved. |
| Payer review | Payer must be able to review evidence before authorizing payment. |
| Admin review | Admin must be able to view evidence for review and investigation. |
| Auditability | Evidence upload, view, update/replacement, archive, and status-change actions must be logged where applicable. |
| Access control | Evidence visibility must be restricted by role and permissions. |

---

## 13. Clarification and Dispute Journey

### 13.1 Purpose

Allows payer, payee, or admin to resolve incomplete, disputed, incorrect, or unclear request information.

### 13.2 Clarification Flow

1. Recipient reviews request or obligation record.
2. Recipient selects **Request Clarification**.
3. Recipient enters clarification reason or question.
4. Recipient may identify the disputed or unclear field.
5. System updates status to **Clarification Requested**.
6. System notifies the other party.
7. Other party responds with:
   - text explanation;
   - corrected field;
   - additional evidence;
   - cancellation;
   - dispute escalation.
8. System logs all clarification activity.
9. Request returns to review, acceptance, rejection, dispute, or cancellation state.

### 13.3 Dispute Flow

1. User reviews request, obligation, payment, or evidence.
2. User selects **Dispute**.
3. User enters dispute reason.
4. User may upload additional evidence.
5. System updates status to **Disputed**.
6. System notifies the other party.
7. Admin may review the dispute where required.
8. Other party may respond.
9. Admin or system may move the request to:
   - clarification requested;
   - accepted;
   - rejected;
   - cancelled;
   - held;
   - resolved;
   - approved for payment where allowed.
10. System logs all dispute actions.

### 13.4 Required Dispute and Clarification Controls

| Control | Requirement |
| --- | --- |
| Linked thread | Clarification and dispute activity must remain linked to the original request. |
| Audit trail | All clarification and dispute actions must be logged. |
| Notification | Relevant parties must be notified of dispute or clarification events. |
| Admin visibility | Admin must be able to review dispute and clarification history. |
| Payment block | Disputed requests should not proceed to payment unless resolved under approved rules. |

---

## 14. Payment Authorization Journey

### 14.1 Purpose

Ensures that the payer explicitly authorizes payment after reviewing the required context.

### 14.2 Required Payer Authorization Information

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

### 14.3 Authorization Flow

1. Payer reviews request or payer-created payment.
2. Payer confirms that evidence and payment details are acceptable.
3. System displays final payment summary.
4. System displays fee, promotion quote, discount, coupon/voucher impact, reward impact, and total charge where applicable.
5. Payer selects or confirms payment method.
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

### 14.4 Authorization Rules

| Rule | Requirement |
| --- | --- |
| Explicit consent | Payer must explicitly authorize payment. |
| No automatic payment | Payee-created request cannot automatically trigger payment. |
| Evidence visibility | Payer must be able to review evidence before payment. |
| Fee visibility | Fees charged to payer must be displayed before authorization. |
| Promotion visibility | Eligible discounts, service-fee benefits, coupons, vouchers, and reward impact must be displayed before authorization where applicable. |
| Payment passcode | Payment passcode is required before payment authorization proceeds. |
| Step-up authentication | Additional authentication may be required by DOC-09, DOC-14, DOC-15, or DOC-19 risk/security rules. |
| Deferred instruction | Deferred payment instruction must return the payer to payment/checkout screen, not only to bill detail. |
| Quote revalidation | Deferred instruction return flow must show updated payment, promotion, card, fee, or timing changes before submission. |
| Partial funding | Split-card partial funding must not be shown as payment completed; remaining amount and funded portion should remain clear. |
| Audit logging | Authorization must be logged. |
| No hidden material terms | Material payment information must not be hidden from payer. |

---

## 15. Payment and Payout Status Visibility

### 15.1 Purpose

Defines what users and admins need to see after payer authorization.

Detailed payment processing, payout, settlement, reconciliation, refund, reversal, chargeback, and exception rules belong in DOC-09, DOC-10, and DOC-11.

### 15.2 Required Visibility

| User | Required Visibility |
| --- | --- |
| Payer | Authorization result, payment status, failure state, cancellation/refund state where applicable, and receipt/history. |
| Payee | Request status, payer response, payment completion status, funded portion, payout/settlement visibility where permitted, and exceptions requiring payee action. |
| Admin | Full request, payment instruction, funding leg, payout, failure, refund, dispute, exception, and audit context. |

### 15.3 UX Rules

| Rule | Requirement |
| --- | --- |
| Status clarity | User-facing labels must distinguish request status, payment status, and payout/settlement status. |
| No false certainty | The UX must not imply payment or payout is complete before the relevant system of record confirms it. |
| Role-appropriate visibility | Payees must not see sensitive payer payment method, risk, or private account data. |
| Exception visibility | Failures, holds, cancellations, refunds, and disputes must have clear user-facing states and admin review paths. |

---

## 16. Linked Records and Matching Journey

### 16.1 Purpose

Ensures that payer, payee, request, evidence, payment, payout, status, dispute, and audit records remain linked.

### 16.2 Required Linked Objects

Each active or completed payment should be linkable to:

- payer user;
- payee user or payee record;
- payment request;
- obligation record where applicable;
- evidence record;
- payment transaction;
- payout or settlement record where applicable;
- dispute or clarification thread where applicable;
- notification records;
- status history;
- audit events;
- admin review actions where applicable.

### 16.3 Linking Flow

1. Request or payment record is created.
2. System checks payee records, payout destination, and evidence consistency required for the payment flow.
3. System may support user-initiated or user-accepted linking using approved identifiers, app links, deeplinks, QR codes, or invitation records.
4. If no platform user exists, system may create a non-user payee record, invitation record, or pending participant record.
5. Recipient registers, logs in, or accepts an invitation where linking is requested.
6. System links recipient to request or obligation only after the required user action or approved operational action.
7. System displays shared context to both sides subject to permissions.
8. System checks for duplicate, suspicious, or conflicting records where applicable.
9. System logs search, invitation, acceptance, rejection, and linking events.

Automatic user-to-user matching must not be assumed for the user experience. Duplicate detection, payee verification, payout validation, and risk checks may run in the background, but shared user visibility requires an approved linking or acceptance event.

### 16.4 Matching Requirements

| Requirement | Description |
| --- | --- |
| Shared request ID | Both payer and payee should reference the same payment request when both are users. |
| Linked evidence | Evidence record must link to request and payment context. |
| Two-sided visibility | Payer and payee must see the same underlying transaction context, subject to permissions. |
| User-accepted linking | User-to-user linking must be initiated, invited, accepted, or otherwise approved; automatic UX linking is not allowed. |
| Duplicate detection | System should help detect duplicate bills, requests, or payments. |
| Status consistency | Payer and payee views must reflect the same underlying status. |
| Dispute linkage | Disputes and clarifications must remain linked to the original request. |

---

## 17. Two-Sided Visibility and Permissions

### 17.1 Purpose

Allows both payer and payee to view linked request/payment context while protecting sensitive information.

### 17.2 Shared Visibility

Both payer and payee should be able to view:

- request ID;
- obligation type;
- amount;
- due date;
- category;
- description;
- evidence, subject to permissions;
- current request status;
- current payment status;
- clarification status;
- dispute status;
- completed payment confirmation;
- relevant history;
- relevant notifications.

### 17.3 Role-Based Visibility Boundaries

| Data | Payer View | Payee View | Admin View |
| --- | --- | --- | --- |
| Request details | Yes | Yes | Yes |
| Evidence | Yes, if linked to request/payment | Yes, if creator or linked participant | Yes |
| Payer identity | Yes | Yes, limited as appropriate | Yes |
| Payee identity | Yes | Yes | Yes |
| Payment method details | Yes, masked/limited | No | Limited/controlled |
| Payout account details | No or masked | Yes, masked/limited | Limited/controlled |
| Fees charged to payer | Yes | Limited or as applicable | Yes |
| Payout status | Limited or as applicable | Yes | Yes |
| Audit events | Limited user-facing history | Limited user-facing history | Yes |
| Risk flags | No | No | Yes |

### 17.4 Privacy and Permission Rules

| Rule | Requirement |
| --- | --- |
| Least privilege | Users should only see information needed for their role in the transaction. |
| Sensitive data masking | Payment and payout instrument details must be masked or restricted. |
| Admin access controls | Admin access must be permissioned and logged. |
| Evidence privacy | Evidence visibility must be limited to authorized users. |
| Consistent status | Status should remain consistent across payer and payee views. |

---

## 18. Request Status UX

### 18.1 Core Request Statuses

The MVP UX should expose clear user-facing request states. Canonical state-machine definitions belong in DOC-09 and DOC-18.

| Status | Meaning |
| --- | --- |
| Draft | Request created but not submitted. |
| Submitted | Request submitted for review or routing. |
| Evidence Processing | Evidence OCR, extraction, autofill, or verification is in progress. |
| Pending User Correction | User must review or correct extracted evidence fields. |
| Pending Evidence Review | Evidence requires admin or risk review before payment eligibility. |
| Sent | Request sent to payer or payee. |
| Viewed | Recipient viewed the request. |
| Clarification Requested | Recipient or admin requested more information. |
| Accepted | Payer accepted the request or recipient accepted the record. |
| Rejected | Recipient rejected the request or record. |
| Disputed | Payer or payee disputed the request or record. |
| Approved for Payment | Required checks passed before payment. |
| Payment Authorized | Payer authorized payment. |
| Payment Processing | Payment is being processed. |
| Paid | Payment completed. |
| Failed | Payment failed. |
| Cancelled | Request cancelled. |
| Expired | Request expired. |

### 18.2 Status Rules

| Rule | Requirement |
| --- | --- |
| Payer authorization | No payment may be processed without payer authorization. |
| Evidence gate | Request cannot move to Approved for Payment without required evidence or approved exception. |
| Verification gate | Request cannot move to Approved for Payment while DOC-12 evidence verification requires correction, admin review, rejection handling, duplicate review, or fraud/risk escalation. |
| Admin/risk gate | Requests may require admin or risk approval before payment. |
| Rejection handling | Rejected requests cannot be paid unless recreated or reopened under approved rules. |
| Dispute handling | Disputed requests should not proceed to payment unless resolved under approved rules. |
| Audit trail | Every status change must be logged. |
| Two-sided consistency | Payer and payee views must reflect the same underlying status. |

---

## 19. Admin and Operations Journey

### 19.1 Purpose

Allows internal users to review accounts, requests, evidence, risk, disputes, payouts, settlement, failures, and exceptions.

### 19.2 Admin Capabilities

Admins must be able to:

- log in;
- access an operational dashboard;
- access sensitive data only through role-based permission, masking, reason capture, and audit logging;
- view payer accounts;
- view payee accounts;
- view payment requests;
- view obligation records;
- view evidence;
- review new payees;
- review high-risk requests;
- approve requests where applicable;
- reject requests where applicable;
- hold requests where applicable;
- request clarification;
- investigate duplicates;
- review disputes;
- review payment status;
- review payout or settlement status where applicable;
- manage failed payment exceptions;
- manage payout exceptions where applicable;
- manage refund or reversal workflows where applicable;
- access audit logs.

### 19.3 Admin Review Flow

1. Request, user, evidence, dispute, or payment is flagged for review.
2. Admin opens review queue.
3. Admin reviews relevant context:
   - payer;
   - payee;
   - request;
   - amount;
   - evidence;
   - extracted fields and user corrections where applicable;
   - evidence verification outcome;
   - status history;
   - duplicate indicators;
   - risk indicators;
   - dispute or clarification history.
4. Admin selects an action:
   - approve;
   - reject;
   - hold;
   - request clarification;
   - escalate;
   - mark duplicate;
   - cancel;
   - resolve.
5. System updates status where applicable.
6. System notifies relevant users where applicable.
7. System logs admin action.

### 19.4 Admin Control Rules

| Rule | Requirement |
| --- | --- |
| Permissioned access | Admin access must be role-based and controlled. |
| Sensitive data access | Sensitive identity, evidence, payment, payout, risk, and promotion data must follow DOC-15 classification, masking, reason capture, and audit rules. |
| Logged actions | Admin actions must be audit logged. |
| Evidence access | Admin must be able to review evidence. |
| OCR review support | Admin must be able to review extracted fields, user corrections, verification outcomes, and duplicate indicators where applicable. |
| Exception handling | Admin must be able to manage operational exceptions. |
| No silent overrides | Admin overrides must be traceable. |
| Risk review support | MVP must support manual review where risk rules require it. |

---

## 20. Notification Touchpoints

### 20.1 Purpose

Identifies where notifications are needed in the user journey. Notification content, templates, channels, preferences, retry behavior, and audit rules belong in DOC-08.

### 20.2 User Notifications

The MVP should support basic notifications for:

- account registration;
- payment request created;
- payment request received;
- request viewed;
- clarification requested;
- clarification response received;
- request accepted;
- request rejected;
- request disputed;
- payer-created record available for optional payee adoption/linking;
- payee adopted payer-created record;
- payment authorized;
- payment instruction pending user action;
- payment instruction partially funded;
- remaining split-card payment action due;
- payment processing;
- payment completed;
- payment failed;
- payout completed where applicable;
- partial payout completed where applicable;
- request cancelled;
- request expired.

### 20.3 Admin Notifications or Queues

The MVP should support admin queues or notifications for:

- request requiring review;
- high-risk request;
- missing or invalid evidence;
- evidence verification review required;
- duplicate or reused evidence warning;
- new payee review;
- duplicate suspected;
- dispute opened;
- clarification unresolved;
- payment failed;
- payout failed where applicable;
- refund or reversal review where applicable;
- operational exception.

### 20.4 Notification Channels

Notification channels may include:

- app notifications;
- push notifications;
- email;
- SMS;
- WhatsApp;
- dashboard task;
- other approved channels.

Final channel routing, user preferences, templates, retry behavior, consent rules, and audit requirements should be defined in DOC-08 and implementation planning.

---

## 21. Receipt and History Touchpoints

### 21.1 Purpose

Identifies where users and admins need access to prior actions, statuses, confirmations, and payment outcomes. Receipt content and records policy belong in DOC-08, DOC-15, DOC-18, and payment-domain docs.

### 21.2 User History

Payers and payees should be able to view:

- created requests;
- received requests;
- linked obligation records;
- evidence records subject to permissions;
- request status;
- payment status;
- payout status where applicable;
- clarification history;
- dispute history;
- completed payment records;
- failed payment records;
- rejected requests;
- cancelled requests;
- expired requests;
- receipts or confirmations.

### 21.3 Receipt or Confirmation Contents

A receipt or confirmation should include:

- request ID;
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

### 21.4 History Rules

| Rule | Requirement |
| --- | --- |
| Traceability | User-visible history must link to the underlying request/payment context. |
| Role permissions | History must show role-appropriate information. |
| Audit separation | User history is not the same as full admin audit logs. |
| Failed states | Failed, rejected, disputed, cancelled, and expired states must remain visible. |
| Receipt storage | Completed payments should have receipt or confirmation records. |
| Retention baseline | Receipt, payment, account, tax, and audit records are expected to be retained for 7 years, subject to final privacy and legal review. |

---

## 22. Error, Failure, Cancellation, and Exception Journeys

### 22.1 Failed Payment

1. Payment processing fails.
2. System updates status to **Failed**.
3. System records failure reason where available.
4. Payer is notified.
5. Payee is notified where applicable.
6. Admin can review failure.
7. User may retry only if allowed by approved rules.

### 22.2 Cancelled Request

1. Eligible user or admin cancels request.
2. System checks whether cancellation is allowed.
3. System updates status to **Cancelled**.
4. System notifies relevant parties.
5. System logs cancellation event.
6. Cancelled request cannot be paid unless recreated or reopened under approved rules.

### 22.3 Expired Request

1. Request passes expiry date or expiry condition.
2. System updates status to **Expired**.
3. System notifies relevant parties.
4. Expired request cannot be paid unless renewed, recreated, or reopened under approved rules.

### 22.4 Duplicate Request

1. System or admin detects possible duplicate request, duplicate evidence, or reused evidence.
2. User may be warned that the evidence appears to have been used before, subject to DOC-12 privacy and anti-tipping-off rules.
3. Request is flagged for review where configured.
4. Admin reviews duplicate indicators.
5. Admin may hold, reject, clarify, or allow request.
6. System logs duplicate review outcome.

### 22.5 Refund or Reversal

1. Refund or reversal need is identified.
2. Admin reviews request, payment, evidence, and status history.
3. Admin follows approved operational process.
4. System records refund or reversal status.
5. Payer and payee are notified where applicable.
6. System logs all actions.

Refund and reversal rules belong in DOC-11. Payment, payout, reconciliation, and admin workflow details belong in DOC-09, DOC-10, DOC-18, DOC-21, and DOC-22.

---

## 23. Prohibited Journey Controls

PayPlus must prevent the following journeys:

| Prohibited Journey | Required Control |
| --- | --- |
| Wallet balance creation | Do not show or maintain user wallet balances. |
| Stored-value account use | Do not allow users to store funds for later discretionary use. |
| Cash withdrawal | Do not provide withdrawal functionality. |
| Payer self-cashout | Block payer from paying themselves or equivalent self-cashout patterns. |
| Unsupported P2P transfer | Require evidence-backed obligation and approved category. |
| Payment without payer authorization | Require explicit payer authorization before payment. |
| Payment without evidence | Require evidence or approved exception before payment. |
| Payee-triggered automatic payment | Payee request must be reviewed and authorized by payer. |
| Hidden material payment terms | Show material amount, fee, payee, evidence, and payment context before authorization. |
| Untraceable payment | Link request, evidence, payer, payee, transaction, status, and audit history. |
| Bypassed risk controls | Apply admin/risk gates where required. |
| Deposit representation | Do not represent funds as deposits or bank account balances. |

---

## 24. UX Scope

### 24.1 Payer UX Screens

The MVP should include payer-facing screens for:

- registration;
- login;
- SMS OTP phone verification;
- new-device 2FA and dormant-login reauthentication;
- payer dashboard;
- logged-in Home Dashboard with bottom navigation, Pay+ action sheet entry, shortcut grid, notices/actions, upcoming obligations, featured carousel, and recent activity;
- user shortcut ordering, visibility, and restore-default settings;
- create payment;
- create or link bill/invoice/tenancy/obligation;
- enter payee details;
- upload evidence;
- review or correct autofilled evidence fields;
- view duplicate/reused evidence warning where applicable;
- received request list;
- request detail;
- evidence review;
- accept/reject/dispute/request clarification;
- payment authorization;
- pay-now or deferred payment instruction selection;
- payment instruction action/reminder screen;
- split-card funding leg progress;
- payment passcode confirmation;
- promotion/coupon/voucher selection where enabled;
- coupon/voucher library where enabled;
- referral or reward status where enabled;
- membership/tier status where enabled;
- Offers Hub entry and coupon/voucher library entry where enabled;
- payment processing status;
- payment completed status;
- partially funded status and remaining amount;
- partial payout status where applicable;
- failed payment status;
- receipt/history;
- notifications;
- account/profile basics.
- material account-change confirmation and security notifications.

### 24.2 Payee UX Screens

The MVP should include payee-facing screens for:

- registration;
- login;
- SMS OTP phone verification;
- new-device 2FA and dormant-login reauthentication;
- payee dashboard;
- logged-in Home Dashboard surfaces relevant payee request, response, payout, instruction, notice, activity, shortcut, and offer entry points subject to permissions;
- create payment request;
- create or link bill/invoice/tenancy/obligation;
- enter payer details;
- select request delivery method;
- upload evidence;
- review or correct autofilled evidence fields;
- view duplicate/reused evidence warning where applicable;
- send request;
- sent request list;
- received payer-created record list;
- payer-created record detail;
- accept/adopt/reject/dispute/request clarification;
- clarification response;
- dispute response;
- payment status;
- coupon/voucher or partner reward status where enabled;
- referral or membership status where enabled;
- payout or settlement status where applicable;
- receipt/history;
- notifications;
- account/profile basics.

### 24.3 Admin UX Screens

The MVP should include admin-facing screens for:

- admin login;
- operations dashboard;
- request review queue;
- evidence review;
- OCR/extracted field review;
- duplicate or reused evidence review;
- payer account view;
- payee account view;
- payee review queue;
- risk review queue;
- duplicate review;
- dispute review;
- clarification review;
- payment status view;
- payout or settlement status view where applicable;
- failed payment exception view;
- refund/reversal review where applicable;
- campaign, offer, coupon/voucher, reward entitlement, and promotion exception view where promotions are enabled;
- shortcut configuration, dashboard placement, announcement, carousel, and feature enablement controls where enabled;
- audit log view.

### 24.4 System UX and Service Touchpoints

The MVP should include system-level handling for:

- record creation;
- participant linking;
- invitation routing;
- status updates;
- evidence linking;
- OCR/autofill processing where enabled;
- evidence verification outcome routing;
- duplicate detection support;
- promotion quote and reward entitlement support where enabled;
- coupon/voucher library and external reward fulfilment support where enabled;
- shortcut configuration and user preference handling;
- dashboard placement configuration for notices, carousel content, and shortcut visibility;
- notification events;
- payment partner status updates;
- payout or settlement updates where applicable;
- audit event creation;
- error handling;
- admin queue routing.

---

## 25. Non-Functional UX Requirements

| Area | Requirement |
| --- | --- |
| Clarity | Users must understand what they are requesting, paying, accepting, or authorizing. |
| Evidence visibility | Payer must be able to review evidence before payment authorization. |
| Evidence correction | Users must be able to review and correct autofilled evidence fields before submission where OCR/autofill is enabled. |
| Sensitive field display control | UI must apply DOC-15 role-based display, masking, approved-purpose access, and controlled detail views; broader extractable data may be stored without broad display. |
| Status transparency | Users must see clear status for pending, processing, completed, failed, disputed, rejected, cancelled, and expired requests. |
| Permissioning | Users must only see data appropriate to their role. |
| Auditability | Key actions must generate audit events. |
| Error handling | Failed, blocked, or incomplete actions must show clear next steps. |
| Accessibility | MVP UX should follow basic accessibility principles. |
| Mobile readiness | Core flows should be usable on common mobile screen sizes. |
| Security | Sensitive payment, identity, evidence, and payout details must be protected. |
| Compliance readiness | UX must support evidence, authorization, review, dispute, and traceability requirements. |

---

## 26. MVP Acceptance Criteria

The DOC-06 user journey scope is satisfied when:

- payers can register and log in;
- payees can register and log in;
- phone verification, new-device 2FA, dormant-login reauthentication, and material-change confirmation touchpoints are represented;
- payers have a dashboard;
- payees have a dashboard;
- payees can create evidence-backed payment requests;
- payees can send payment requests to payers;
- payers can receive and review payee-created requests;
- payers can create evidence-backed payments or obligation records;
- payers can link or invite payees;
- payees can review payer-created records;
- payees can optionally accept/adopt payer-created records for linking where applicable;
- users can upload evidence;
- OCR/document AI can process evidence where enabled;
- users can review and correct autofilled evidence fields where applicable;
- evidence is linked to the request or obligation;
- evidence verification outcomes can route to payment eligibility, user clarification, or admin review;
- payer can review evidence before payment;
- payer can accept, reject, dispute, or request clarification;
- payee can respond to clarification or dispute where applicable;
- payer can explicitly authorize payment;
- payer must enter payment passcode before payment authorization proceeds;
- payment status can be tracked;
- payout or settlement status can be tracked where applicable;
- payer-side Bills routes do not show payee-side request actions as payment actions;
- payee-side Bills routes do not show payer-side `Pay` actions;
- payer and payee can view the same linked request/payment context subject to permissions;
- admin can review users, requests, evidence, disputes, and exceptions;
- key status changes are audit logged;
- receipts or confirmations are available for completed payments;
- failed, rejected, disputed, cancelled, and expired requests are handled clearly;
- wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are blocked.

---

## 27. Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06-001 | What exact UX distinction should exist between a payment request, obligation record, bill record, and payment transaction? | Product / Design | Open |
| OQ-06-002 | Which exceptional payer-created categories, if any, require payee adoption before payment can proceed despite the default rule that payer-created payments do not require payee acceptance? | Product / Operations / Risk | Open |
| OQ-06-003 | Which payee-created request categories require admin review before payer authorization? | Risk / Operations | Open |
| OQ-06-004 | Which evidence categories are accepted at MVP launch? | Product / Compliance | Open |
| OQ-06-005 | Which rent and tenancy journey controls must be ready before initial launch enablement? | Product / Legal / Risk | Open |
| OQ-06-006 | What final KYC/KYB screens, provider handoff, failure states, exception states, and risk-tier steps are required for the baseline onboarding model? | Compliance / Legal | Open |
| OQ-06-007 | What payment methods are available to payers at MVP launch? | Payments / Product | Open |
| OQ-06-008 | Which operating bank setup will be used for FPS, cheque, and EPS payouts? | Payments / Operations | Open |
| OQ-06-009 | What fee disclosures must be shown before payment authorization? | Business / Legal | Open |
| OQ-06-010 | What dispute states and resolution outcomes are required for MVP? | Operations / Legal | Open |
| OQ-06-011 | What refund or reversal journeys are supported in MVP? | Payments / Operations | Open |
| OQ-06-012 | What routing, preferences, templates, consent rules, and fallback behavior apply across app, push, email, SMS, and WhatsApp notifications? | Product / Engineering | Open |
| OQ-06-013 | What admin roles and permission levels are required? | Operations / Security | Open |
| OQ-06-014 | What information should be hidden or masked between payer and payee? | Product / Security / Legal | Open |
| OQ-06-015 | What duplicate detection signals are required for MVP? | Risk / Engineering | Open |
| OQ-06-016 | What OCR/autofill review UI is required for each evidence category? | Product / Design | Open |
| OQ-06-017 | What duplicate/reused evidence warning can be shown without over-disclosing sensitive information? | Product / Legal / Privacy | Open |
| OQ-06-018 | What dormant-login inactivity threshold and user-facing reauthentication path should be used? | Product / Security | Open |
| OQ-06-019 | What exact masking, reveal, and role-based display rules should apply to each sensitive field by screen and category? | Product / Privacy / Security | Open |
| OQ-06-020 | What exact payment-instruction screen labels, call-to-action wording, and partial-funded visual treatment should be used? | Product / Design / Legal | Open |
| OQ-06-021 | What exact Pay+ action sheet visual layout, button order, empty states, disabled states, eligibility copy, and final action limits should be used? | Product / Design / Payments | Partially answered |
| OQ-06-022 | What exact route-level IA should apply to Bills, Offers, Me, More, Requests, Instructions, Receipts, Reminders, Cards, Referral, and Support entry points? | Product / Design | Open / placeholders added |
| OQ-06-023 | What dashboard shortcut display cap, user reorder UI, restore-default behavior, and admin default mechanism should be used? | Product / Design / Operations | Open |
| OQ-06-024 | What priority, collapse, expiry, and routing rules should apply to Important Notice / Action Required cards? | Product / Operations / Compliance | Open |
| OQ-06-025 | What carousel card limit, auto-rotation behavior, ranking, targeting, and admin approval workflow should apply to Featured / What’s New / Hot Offer placements? | Product / Growth / Operations | Open |
| OQ-06-026 | What final user-initiated payee linking or invitation mechanism should be used: user ID, phone search, app link, WhatsApp deeplink, QR code, or another approved flow? | Product / Privacy / Engineering | Open |
| OQ-06-027 | What exact Bills tab visual layout, card density, status badge style, action-required treatment, and field masking rules should be used? | Product / Design / Privacy | Open |
| OQ-06-028 | What evidence source selection UI should be used when bill, invoice, tenancy, rent demand, contract, and supporting evidence types are not obvious from upload/OCR? | Product / Design / Risk | Open |
| OQ-06-029 | What exact request-delivery and `Remind Payer` UX should apply inside `BILLS-RECEIVE`, including resend limits, payer acceptance states, wording, and notification-channel rules? | Product / Design / Operations | Open |
| OQ-06-030 | Should detailed payment/checkout UI be documented inside DOC-09 only, or should DOC-06 keep a lightweight route shell for checkout entry, return, and navigation behavior? | Product / Design / Payments | Proposed: DOC-09 owns checkout UI; DOC-06 owns handoff. |

---

## 28. Dependencies

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
| DOC-09 | Payment request, funding, authorization, and settlement readiness. |
| DOC-10 | Payout, payout readiness, payout destination, batching, and reconciliation. |
| DOC-11 | Refund, cancellation, reversal, dispute, and chargeback handling. |
| DOC-12 | Bill category, document AI/OCR, evidence verification, duplicate detection, and payee matching. |
| DOC-14 | AML, anti-cashout, fake evidence, duplicate evidence, collusion, and risk controls. |
| DOC-15 | Privacy, data protection, masking, retention, and lawful data use. |
| DOC-18 | Request, obligation, evidence, payment, payout, audit, ledger, reporting, and participant data objects. |
| DOC-19 | Authentication, authorization, evidence access, data protection, and privacy controls. |
| DOC-21 | Monitoring, support escalation, incident handling, and operations runbooks. |
| DOC-22 | Admin review, risk, dispute, exception, support, configuration, and override workflows. |
| Future UX Wireframes | Defines screen-level UX and interaction design. |

---

## 29. Decision Summary

| Decision | Status |
| --- | --- |
| Payer registration and login are MVP scope. | Confirmed |
| Payee registration and login are MVP scope. | Confirmed |
| Payer dashboard is MVP scope. | Confirmed |
| Payee dashboard is MVP scope. | Confirmed |
| Payee-created payment requests are MVP scope. | Confirmed |
| Payer-created payments are MVP scope. | Confirmed |
| Tenancy and rent journeys are MVP scope. | Confirmed |
| Payee-created bill, invoice, tenancy, or obligation setup is MVP scope. | Confirmed |
| Payer-created bill, invoice, tenancy, or obligation setup is MVP scope. | Confirmed |
| Payer-created payments do not require payee acceptance by default, provided evidence, verification, risk, payout, and authorization gates pass. | Confirmed |
| Payee adoption of payer-created records is optional where applicable for two-sided visibility, communication, and linked recordkeeping. | Confirmed |
| Payer review and authorization are required before payment. | Confirmed |
| Evidence-backed payments are required unless approved exception applies. | Confirmed |
| OCR/document AI-assisted evidence capture, autofill, user correction, duplicate warning, and evidence verification routing are required UX touchpoints where enabled. | Confirmed |
| Linked payer/payee visibility is required subject to permissions. | Confirmed |
| Admin/risk review support is required. | Confirmed |
| Wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are prohibited. | Confirmed |
| Final payment processor, operating-bank setup, detailed KYC/KYB steps, fees, multi-card card-count limit, and dispute policy details remain open or to be confirmed. | Open |
| Major functions and modules must be independently disableable. | Confirmed |
| Promotion, coupon/voucher, reward, MGM, and membership UX surfaces are framework scope but launch-gated by DOC-13. | Confirmed |
| Home Dashboard is task-first and uses bottom navigation `Home`, `Bills`, `Pay+`, `Offers`, and `Me`. | Designated Layout Baseline |
| `Pay+` is the preferred center bottom-nav action label. Working baseline actions are Pay a Bill / Fee, Pay Rent, Add Bill / Rent, Continue Payment, and Request Payment. | Working Baseline / Not Final |
| `Add Bill / Rent` includes scan QR, upload evidence, and manual entry inside the setup flow; QR/upload is not a standalone instant-payment action. | Working Baseline |
| `Request Payment` should appear by default for all users unless the feature/module is disabled or the account is restricted. | Working Baseline |
| MVP dashboard shortcuts are Requests, Instructions, Bills & Tenancies, Receipts, Reminders, Cards, Referral, and More. | Designated Layout Baseline |
| Dashboard shortcuts must be admin-configurable and user-reorderable, with user settings overriding system default and restore-default support. | Confirmed |
| Important Notice / Action Required is a combined swipeable section, collapsible by user, hidden when empty. | Confirmed |
| Featured / What’s New / Hot Offer is one combined admin-controllable carousel at this stage. | Confirmed |
| Recent Activity dashboard section displays limited recent transactions with date, item, action, amount, and status. | Confirmed |
| The dashboard flow and layout are designated for MVP discussion, but final UI design, exact component specification, and exact route-level screen specification are not finalized. | Confirmed |
| Bills tab working baseline uses `To Pay` and `To Receive` views, route/subsection IDs, bill/rent cards, detail pages, bill/rent-specific activity sub-routes, evidence status, archive behavior, and Add Bill / Rent setup flow. | Working Baseline / Not Final |
| `BILLS-PAY` is the formal payer-side route replacing the earlier informal `To Pay` view description; `BILLS-RECEIVE` is the formal payee-side request/receive route and must not show payer-side `Pay` actions. | Working Baseline / Not Final |
| Payment/checkout UI behavior is primarily governed by DOC-09; DOC-06 governs Bills-route entry points, route handoff, and high-level navigation behavior. | Working Baseline / Not Final |
| Bills activity route uses `BILLS-ACTIVITY` and `BILLS-ACTIVITY-DETAIL` for bill/rent-specific payment activity, limited request/evidence milestones, receipt/proof access, and status visibility; ordinary record edit history, full request workflow logs, and internal audit logs are excluded. | Working Baseline / Not Final |
| Bills reminder route uses `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`, linked reminder IDs, bill/rent setup frequency, reminder defaults, custom override, soft-delete behavior, and DOC-08/DOC-09/DOC-18 ownership boundaries. | Working Baseline / Not Final |
| Bills evidence route treats evidence as a bill/rent detail sub-flow, using `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`; evidence actions live inside bill/rent detail, extracted fields populate bill/rent details, and evidence status drives payment readiness. | Working Baseline / Not Final |
| User-to-user payee linking must be initiated or accepted through an approved flow; automatic user-to-user matching is not allowed as a UX assumption. | Working Baseline |
| Tenancy evidence is treated as contract/relationship evidence, while invoices/bills usually support obligation/payment-cycle evidence; detailed data structure remains owned by DOC-12 and DOC-18. | Working Baseline |

---

## 30. Revision History

| Version | Date | Summary |
| --- | --- | --- |
| v0.1 | 2026-05-27 | Initial DOC-06 draft aligned to DOC-05 v0.2; includes payer-created and payee-created MVP journeys, payee onboarding/login, bill/tenancy setup, adoption flow, evidence review, two-sided visibility, admin operations, and prohibited journey controls. |
| v0.2 | 2026-05-29 | Confirmed tenancy/rent journeys as MVP scope, added UX scope boundaries, clarified independent module disablement, and reduced overlap with payment, notification, receipt, and data specifications. |
| v0.3 | 2026-05-30 | Aligned user journeys with updated DOC-01 scope for invoices, fees, rent, domestic service obligations, and evidence-backed positioning. |
| v0.4 | 2026-05-30 | Added explicit payee-created request delivery method selection for in-app message, app link, WhatsApp deeplink, QR code, or other approved channel. |
| v0.5 | 2026-05-30 | Aligned UX flows with DOC-12 by adding OCR/autofill review, user correction, evidence verification outcomes, duplicate/reused evidence warning, sensitive field display boundaries, and explicit downstream document references. |
| v0.6 | 2026-06-01 | Aligned UX scope with DOC-13 by adding promotion quote, coupon/voucher library, reward entitlement, referral/MGM, membership, and promotion admin touchpoints where enabled. |
| v0.7 | 2026-06-02 | Aligned UX scope with DOC-15 by adding SMS OTP registration, new-device 2FA, dormant-login reauthentication, payment passcode, material-change confirmation, and sensitive-field display controls. |
| v0.8 | 2026-06-02 | Aligned UX scope with DOC-09 user payment instruction by adding deferred payment action, reminder destinations, split-card funding-leg progress, partial funding, and partial payout visibility. |
| v0.9 | 2026-06-02 | Added return-to-checkout quote revalidation for deferred payment instructions, including payment quote, promotion quote, card eligibility, fee, and timing changes before submission. |
| v0.10 | 2026-06-02 | Standardized coupon/voucher library wording to avoid stored-value confusion. |
| v0.11 | 2026-06-04 | Added Home Dashboard and navigation IA discussion baseline covering bottom navigation, Pay+ center action, shortcut grid, notice/action section, upcoming obligations, featured carousel, recent activity, shortcut configurability, user shortcut preferences, and open route-level UI decisions. |
| v0.12 | 2026-06-04 | Updated designated dashboard flow to place Featured / What's New / Hot Offer directly under shortcuts, clarified the dashboard as a designated layout baseline rather than finalized UI design or exact component specification. |
| v0.13 | 2026-06-07 | Added Pay+ action sheet working baseline, clarified QR/upload as part of Add Bill / Rent, confirmed Request Payment default visibility subject to gating, and added route IA placeholder titles for continued app UI specification work. |
| v0.14 | 2026-06-12 | Added Bills tab IA working baseline with To Pay/To Receive views, route/subsection IDs, bill/rent cards, detail pages, activity panels, Add Bill / Rent flow, evidence source structure, payer-created/payee-created acceptance rules, user-accepted linking, action-required UX, and AI-ready event signals. |
| v0.15 | 2026-06-15 | Clarified Bills tab route IDs as screens, tabs/views, sheets, sections, flows, or card components, and added initial button-to-route ownership for Bills tab UI drafting. |
| v0.16 | 2026-06-16 | Added Bills reminder list/detail route specification, linked reminder behavior, reminder setup frequency, smart defaults, custom override, soft-delete interaction, notification ownership boundaries, and reminder AI/data signals. |
| v0.17 | 2026-06-17 | Added DOC-06 route ID naming standard for primary route IDs, sub-route IDs, shorthand labels, and downstream AI build, notification, analytics, and implementation references. |
| v0.18 | 2026-06-18 | Updated Bills evidence sub-route model, Add Bill / Rent evidence flow, bill/rent detail evidence sections, evidence status mapping, archive/version behavior, and evidence-related data signals. |
| v0.19 | 2026-06-23 | Defined `BILLS-ACTIVITY` and `BILLS-ACTIVITY-DETAIL` as bill/rent-specific payment activity sub-routes, limited evidence milestones, receipt/proof access, and ownership boundaries with DOC-08 through DOC-12, DOC-15, DOC-18, and DOC-22. |
| v0.20 | 2026-06-24 | Clarified `BILLS-PAY` and `BILLS-RECEIVE` as role-aware Bills routes, separated payer-side and payee-side card/detail actions, bounded `BILLS-ACTIVITY` request milestones, removed evidence management from default primary detail actions, and added checkout UI ownership boundary with DOC-09. |
