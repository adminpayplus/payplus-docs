---
document_id: DOC-06B
title: Navigation, IA & Route Taxonomy
version: 1.1.0
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
last_updated: 2026-08-22
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
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
  - DOC-17 API & Third-party Integration Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-20 Testing, UAT & Release Readiness
  - DOC-21 Monitoring, Incident Response & Operational SOPs
  - DOC-22 Admin Management Dashboard Operations Workflow
---

# DOC-06B - Navigation, IA & Route Taxonomy

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06B` |
| **Title** | Navigation, IA & Route Taxonomy |
| **Version** | `1.1.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Growth Lead<br>Privacy Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-08-22` |
| **Classification** | Internal |
| **Related Documents** | DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-16 Technical Architecture Specification<br>DOC-17 API & Third-party Integration Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-20 Testing, UAT & Release Readiness<br>DOC-21 Monitoring, Incident Response & Operational SOPs<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## Current Wave 2 Payer-only Route and IA Baseline

This is the current normative DOC-06B Founder Working Baseline. Current active sections state Payer-only navigation, the four-action Pay+ sheet, BILLS-PAY, and owner handoffs directly. Prior Request, Linking, Receive, Consumer Receiving Info and pre-Checkout Save meaning may appear only in append-only version history or concise non-active documentation registers of retired stable IDs; it is not active or runtime behavior. Stable destination IDs and append-only history are preserved. No Route Register or route-status change is made in this route baseline.

### Global route and entry rules

- Consumer Users are Payers only. A Payee is an economic recipient who may be an individual or institution/company and need not be a PayPlus User. DOC-06B does not create Payee-user navigation, account invitation, reciprocal visibility, Request or Linking routes.
- A durable Bill/Rent ID is not established merely by opening a route. ID establishment consumes an owner-governed source/Evidence preservation eligibility outcome. DOC-06B defines route/journey timing and does not independently define the technical persistence threshold or exact minimum fields required for the authoritative identity. The outcome establishes the ID before Save/reuse materialization, Payable Basis or Payment Obligation materialization, or a payment-facing handoff requires stable source identity, including before immediate-pay Checkout; deliberate Setup consumes the same outcome before giving the same ID a Saved/current projection. Pending Evidence, mismatch or scoped Admin review does not automatically prevent ID establishment once the outcome permits it. ID establishment alone does not imply accepted Evidence, verified Payee, destination/Payout readiness, risk clearance, Payment Obligation or Checkout readiness, payer authorization, Payment success, Save or any Saved/current/Saved-Archived/history-only projection.
- Directory and Provide Payee myself are bounded Bill-flow views/actions after selection of one of the twelve Founder-confirmed launch controlled Bill Categories in DOC-05, not new roots. Category-specific eligibility, Evidence criteria, detailed labels and Directory contents remain owner-backed deferrals. Rent is not a Bill Category; it is a separate journey and bypasses Category and Directory mechanics.
- Immediate pay-now has no Save prompt before Checkout. After confirmed Payment with a separate Payment ID linked to the same source, Payment Result preserves an existing Saved/current projection without duplicate Save. For an otherwise unsaved source, it hands to the owner-controlled optional Save resolver before Activity, Payment History, Receipt or ordinary safe exit: selected Save makes the same ID Saved/current, while declined, skipped, dismissed, closed or otherwise abandoned Save resolution makes it history-only. Payment, Activity and Receipt exist independently of Save but do not bypass the projection resolution. Setup may give the same ID a Saved/current projection before Payment because Setup is deliberate reuse/collection intent; Saved/current is Payer reuse/visibility only.
- An established source may remain unprojected only when immediate pay ends or fails before confirmed Payment, or deliberate Setup ends before its Saved/current projection is completed. It receives no Saved/current, Saved/Archived or history-only Bills/Rent route, Activity Save action or new visible status solely because the ID exists. After a newly confirmed Payment for an otherwise unsaved source, closing or leaving Payment Result without selecting Save is skipped Save and produces history-only before downstream handoff; the source cannot remain unprojected. Archive is an existing projection for Saved/current sources; exact Restore, prior-version, Evidence-version and replacement-source presentation remain deferred. DOC-09 owns applicable payment-lifecycle continuation/recovery, DOC-15 owns retention governance and requirements, and DOC-18 owns only business recording and explainability; technical representation remains separately authorized.

### Current route outcomes

| Route/surface | Wave 2 outcome |
| --- | --- |
| HOME-ROOT | Retain/re-scope Payer-only; remove active Request shortcut/Request destination. Do not invent a replacement shortcut. |
| PAYPLUS-ACTION-SHEET | Retain; remove Request Payment; preserve the remaining four actions without reordering or materially renaming. |
| BILLS-ROOT / BILLS-PAY | Retain/re-scope as the Payer Bills area and stable Payer destination; remove mixed To Pay/To Receive presentation. |
| BILLS-RECEIVE | Retire active Consumer Payee view; stable ID remains non-active documentation lineage only. |
| BILLS-DETAIL-BILL / BILLS-DETAIL-RENT / BILLS-ADD | Retain/re-scope Payer-only; Category-first controlled Bill flow, separate Rent, source-ID timing and specialist handoffs. |
| BILLS-ACTIVITY / BILLS-ACTIVITY-DETAIL | Retain/re-scope; Activity behind a visible source projection; history-only Payment remains in global Activity/Receipt without a Bill/Rent route. |
| REQUESTS-ROOT / REQUESTS-DETAIL / REQUESTS-NEW | Retire active navigation and behavior; stable IDs remain non-active documentation lineage only. No runtime reader, adapter or fallback exists or is required. |
| BILLS-LINKING | Retire active flow; preserve stable ID as non-active documentation lineage and neutral future seams only. |
| RECEIVING-INFO family | Retire active Consumer Payee presentation; do not repurpose as a Payer destination library. |
| ARCHIVED-ROOT / ARCHIVED-BILLS-LIST | Retain/re-scope Payer-only for saved sources; ordinary Archive removes the same source from current Bills/Rent visibility and exposes its Archived projection through the active Archive route family without erasing history. |
| ARCHIVED-DOCS-LIST | Retain provisionally under the Founder-approved W2-FD-05 decision (Option A); this does not change route status. Exact evidence-version/prior-version/Restore presentation is deferred. |
| NOTIFICATION-ROOT family | Retain Payer-facing notification shell; optional Individual-Payee notification is a governed one-way capability, not a route or Request. |
| Unaffected auth, Instructions, Checkout, payment-profile, Offers/Rewards/Referral, Support/About/Terms and generic privacy/security routes | Retain; remove only local mixed-role wording where found. |

### Notification ownership rule

The optional one-way Payee notification is available only where the Payee is eligible under the governed Individual-Payee classification/determination policy. DOC-06B consumes that eligibility outcome and does not determine Payee type or make an Admin determination. Institution/company and unresolved/insufficient Individual determination leave notification unavailable. A governed Individual determination plus Payer choice may expose the informational one-way capability. Payer contact responsibility does not remove PayPlus obligations for lawful purpose, data minimization, wrong-recipient prevention, abuse/rate-limit controls, suppression/opt-out, security, delivery records, retention and support. It creates no Request, Linking, acceptance, consent proof, invitation, reciprocal visibility, payment authorization or payment-state change. DOC-05 owns only the eligibility boundary; DOC-07 owns approved Copy/disclosure/CTA; DOC-08 owns notification identity/channel/template/preference/delivery; DOC-14 owns risk/abuse; DOC-15 owns privacy/retention requirements; DOC-18 represents approved data/audit requirements; DOC-19 owns security; DOC-21 owns support/operations; and DOC-22 performs only permitted Admin execution. DOC-12 supplies any Evidence-derived classification input but does not own notification delivery. Contact provenance and lawful-basis or consent treatment remain with their applicable formal owners.

No new route ID, root, tab, replacement action, Directory root, self-provided root, legacy adapter, status or route-register entry is introduced.

---

## Active Normative Baseline

The route and IA sections below are active current requirements for Payer-only navigation and compatible route contracts. Retired Request, Linking, Receive and Consumer Receiving Info identifiers appear only in concise non-active documentation registers or append-only Version History; they do not define a runtime reader or current route behavior.

## 1. Purpose

DOC-06B governs PayPlus global app navigation, information architecture, dashboard placement, route taxonomy, screen/component/action ID standards, and route completion tracking.

## 2. Scope Boundary

DOC-06B owns how app areas, routes, screens, views, sheets, components, actions, flows, and system touchpoints are named, grouped, opened, and routed at the product UX level.

DOC-06B does not own detailed Bills/rent/tenancy route behavior, which belongs to DOC-06C. It does not own checkout processing, payment instruction mechanics, evidence verification logic, data schema, notification delivery rules, privacy implementation, or admin workflow detail.

When drafting global non-Bills routes, DOC-06B should define the human-readable route-level UX baseline: route ID, entry points, destination relationships, user purpose, major sections, core visible fields and actions, view/filter structure, return behavior, and handoff rules. Exact visual styling and detailed lifecycle, status, payment, evidence, risk, notification, privacy, data, or admin logic remain in their owning documents and should be referenced rather than duplicated.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Entrance and authentication | Defined baseline | `ENTRANCE-ROOT`, the Entrance Carousel, `ENTRANCE-PROMOTION-DETAIL`, the Login family, Registration, Recovery, and Account Activation handoffs have human-readable behavior that is decision-complete enough for continued alignment. Exact DOC-07 Copy/CTA, final visual and accessibility evidence, technical implementation, and security mechanics remain open with their formal owners; these downstream dependencies do not block the `ENTRANCE-PROMOTION-DETAIL` Defined baseline. |
| Bottom navigation | Working baseline | `HOME-ROOT`, Bills, `PAYPLUS-ACTION-SHEET`, Offers, and Me baseline exists; final visual design remains open. |
| Home dashboard | Partially defined | `HOME-ROOT` and section order exist; final card and visual details remain open. |
| Pay+ action sheet | Defined baseline | `PAYPLUS-ACTION-SHEET`, its four retained Payer-only actions, destination handoffs, availability behavior, and motion principles are defined; Request Payment is retired and exact visual specification remains open. |
| Shortcut grid and More | Defined baseline | Home supports a default and maximum of 8 shortcuts including protected `More`; `MORE-ROOT` manages account-level shortcut preferences and approved secondary-service entry. Final visual design remains open. |
| Route taxonomy and ID standard | Working baseline | Stable product destination rules are defined; the canonical destination inventory is maintained in `docs/traceability/route-register.md`. |
| Non-Bills route registry | Working baseline | Instructions, Payment Profile, Activity, Receipts & Statements, Offers, Rewards, Referral and Me core child routes have route-level baselines. `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST` retain active Payer-only route baselines; `ARCHIVED-DOCS-LIST` remains a provisional taxonomy identity with behavior deferred. Requests, BILLS-LINKING and Consumer Receiving Info remain retired stable IDs as non-active documentation evidence only; undefined destinations remain visible in the route register. |
| Notifications | Defined baseline | `NOTIFICATION-ROOT`, Inbox, Detail, and Settings behavior, entry/return rules, filters, archive visibility, and owning-domain handoffs are defined. Final visual styling remains open. |
| Payment Checkout | Defined baseline | `PAYMENT-CHECKOUT` is one persistent Checkout Workspace whose human-readable route behavior is decision-complete for continued alignment. Final visual and component design, exact Copy and identifiers, Locale Variants, Presentation Mappings, final Bill/Rent source-owner detail, technical contracts, prototype and accessibility/user-validation evidence, implementation/UAT, acceptance, monitoring, support, and operational evidence remain pending with their formal owners. |

---

## 4. Route Object Taxonomy

Stable IDs and taxonomy terms are retained for traceability. Only concise non-active documentation registers, append-only version-history rows and stable IDs explicitly marked retired may preserve prior Request, Linking, Receive, Consumer Receiving Info, replacement-action or pre-Checkout Save meaning. They create no runtime historical reader. Every other active section is a current Payer-only requirement and must be read on its own; no unlabelled active clause is silently superseded.

| Type | Definition |
| --- | --- |
| Area | Broad product area such as Home, Bills, Offers, Me, Instructions, Receipts, Cards, or Support. Retired Request identifiers may remain only in explicitly marked historical registers. |
| Route | Navigable destination or deep-link target. |
| Screen | Full-page UI view rendered inside a route. |
| Tab / View | Role-aware, state-aware, or filtered view inside a screen. |
| Sheet / Modal | Temporary focused interaction, such as the Pay+ action sheet or confirmation modal. |
| Component | Reusable UI unit such as a card, badge, action row, timeline entry, or carousel card. |
| Flow | Ordered multi-step journey that may span routes, screens, sheets, and system touchpoints. |
| Action | User-triggered behavior such as Pay, Upload Evidence, Set Reminder, or Archive. Former Request/Linking actions remain retired IDs in non-active documentation only. |
| System Touchpoint | Automated validation, notification, audit event, risk routing, status update, OCR/autofill step, or integration handoff. |

### 4.1 Route Registry Table Standard

Route and screen registry tables should use this structure where practical.

| Column | Requirement |
| --- | --- |
| ID | Stable route, screen, component, or action ID. |
| Type | Area, Route, Screen, Tab/View, Sheet/Modal, Component, Flow, Action, or System Touchpoint. |
| Area | Parent product area. |
| Role | Payer, Payee-as-recipient, admin, system, or non-active historical documentation context. |
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
| Product route / destination | Semantic product name | OFFERS-ROOT, OFFERS-CARD-LIST |
| Screen | SCREEN-06B-{NAME} | SCREEN-06B-HOME-DASHBOARD |
| View | VIEW-06B-{NAME} | VIEW-06B-OFFERS-HUB |
| Sheet / Modal | SHEET-06B-{NAME} | SHEET-06B-PAYPLUS-ACTION |
| Component | COMP-06B-{NAME} | COMP-06B-SHORTCUT-GRID |
| User action | ACT-06B-{NAME}-{NNN} | ACT-06B-OPEN-PAYPLUS-001 |
| Event signal | EVT-06B-{NAME} | EVT-06B-SHORTCUT-TAPPED |
| Open question | OQ-06B-001 | OQ-06B-001 |

Product destination IDs remain independent of DOC-06B and must survive future document restructuring. Reserve `*-ROOT` for an independent area's main screen and use clear child-screen suffixes such as `*-LIST` or `*-DETAIL`. Ordinary entry points are recorded through source/action/destination/return transitions rather than permanent IDs. Document-scoped requirement, screen, component, action, and test IDs may still be assigned progressively for traceability.

### 4.3 Route Ownership Rule

Each route must have one primary owner. DOC-06B may list related documents, but related documents must not become duplicate owners of the same detailed route behavior.

| Route Work Item | DOC-06B Owns | Reference / Handoff Owner |
| --- | --- | --- |
| Route shell | Route ID, route purpose, entry points, destination relationship, major sections, empty state, and high-level allowed actions. | N/A |
| Request lifecycle | No active route, runtime reader, legacy adapter or fallback. Retired IDs remain non-active documentation lineage only. | Documentation governance only; no dormant Request product. |
| Bills/rent acquisition and source projection | Global entry/return and route relationship. | DOC-06C owns Payer-only Bills/Rent views, Category-first acquisition, same-ID projections, Save/Archive visibility and specialist handoffs. |
| Payment/checkout route | Route ID, screen structure, entry/return behavior, interaction presentation, and handoffs. | DOC-09 owns Payment Domain architecture, monetary invariants, obligations, Checkout Workspace, funding execution, payer-authorization boundaries, Payments, and Payment Applications. DOC-07 owns Outcomes/Messages/CTAs; DOC-18 owns machine implementation. |
| Payment Profile route | Route shell, entry points, major screens, card/profile management purpose, and route handoff. | DOC-09 owns payment-time Funding Allocation and execution semantics; DOC-16 owns the provider-controlled card-data boundary; DOC-17 owns provider/tokenization mechanics; DOC-19 owns mechanism-neutral security controls. |
| Notification destination | Route target for a notification tap. | DOC-08 owns notification IDs, channels, templates, preferences, and delivery rules. |
| Data/intelligence signal | Signal existence at route level. | DOC-18 owns only business recording and explainability; technical representation remains separately authorized. |

### 4.4 Canonical Product Destination Register

`docs/traceability/route-register.md` is the canonical inventory of product destinations. It records each destination's parent, type, purpose, primary owning document, and definition status without duplicating route behavior.

When this document or another route owner defines, renames, replaces, or materially advances a destination, the same integration change must update the route register, the affected parent/family status, DOC-06D test readiness, and the Mermaid route map where navigation changes. Components, filters, tabs, and ordinary entry actions must not be added as routes.

---

## 5. Authentication Entry, Logged-in Home Dashboard and Navigation IA

### 5.0 Entrance and Authentication Route Family

`ENTRANCE-ROOT` is the only unauthenticated app root. Log In and Create Account are actions within `ENTRANCE-ROOT`, not a second route. `ENTRANCE-CAROUSEL` is a screen component, not a route; tapping one of its approved public items opens the separately navigable `ENTRANCE-PROMOTION-DETAIL`.

| Destination | Type | Purpose | Definition Status |
| --- | --- | --- | --- |
| `ENTRANCE-ROOT` | Unauthenticated root screen | Present public PayPlus entry content and the Log In / Create Account actions. | Defined baseline; final visual, technical, and validation evidence pending |
| `ENTRANCE-PROMOTION-DETAIL` | Public child screen | Display one approved public Promotion or Feature item, its inline Terms, and zero or one owner-approved action. | Defined baseline; human-readable UI/UX behavior is decision-complete enough for continued alignment, with exact Copy and downstream evidence pending |
| `AUTH-LOGIN` | Route family / entry resolver | Resolve an existing-user login into Fast or Full Login according to the current device and account context. | Resolver rules defined |
| `AUTH-LOGIN-FAST` | Child login screen | Reauthenticate a remembered eligible account through user-enabled device biometrics or password fallback. | Screen behavior defined; technical mechanics open |
| `AUTH-LOGIN-FULL` | Child login screen | Offer Google, Apple, or email/password login where Fast Login is unavailable or another account is selected. | Screen behavior defined; technical mechanics open |
| `AUTH-RECOVERY` | Reusable child flow | Recover an existing PayPlus login password or resolve account-access recovery through an approved controlled flow. | Product behavior and resolution baseline defined; detailed security, support, message, and notification mappings open |
| `AUTH-REGISTRATION` | Child registration flow | Complete Google, Apple, or email account creation and create a restricted account only after all account-creation gates pass. | Screen and account-creation baseline defined |
| `ACCOUNT-ACTIVATION` | Reusable orchestration flow | Coordinate the remaining phone, identity, and payment-passcode requirements for full registration. | Route, banner, and child handoffs defined |
| `PHONE-VERIFICATION` | Reusable `ACCOUNT-PROFILE` child flow | Verify or replace the account phone number through the approved method; Account Activation may invoke initial verification contextually. | Defined behavior baseline; exact security mechanisms remain open under `OQ-19-001` with Security/Engineering and any provider contract with DOC-17 |
| `IDENTITY-VERIFICATION` | Reusable `ACCOUNT-PROFILE` child flow | Complete first-time verification, resume processing, retry a failed attempt, or respond to an identity/security-owner-required update executed through a permitted Admin workflow; Account Activation may invoke it contextually. | Defined behavior baseline; provider mapping remains TBC |
| `PAYMENT-PASSCODE-SETTINGS` | Reusable `ACCOUNT-SECURITY` child flow | Set, change, or reset the six-digit payment passcode and manage the permitted card/profile confirmation preference; Account Activation may invoke Set contextually. | Defined behavior baseline; DOC-19 security controls are defined while exact mechanisms remain open under `OQ-19-001` |
| `HOME-ROOT` | Logged-in root screen | Provide the task-first dashboard after successful login or restricted-account creation. | Dashboard baseline defined; final UI pending |

#### Authentication Outcome and Resolution Rule

The Authentication route family applies the repository-wide decision chain:

```text
Business Rule and Current Context
    -> Decision or Evaluation
    -> Outcome
    -> Resolution Strategy
    -> DOC-07 Message and CTA
    -> DOC-08 Notification, when required
    -> DOC-18 Audit and Correlation
    -> DOC-06D / DOC-20 Acceptance Coverage
    -> Technical Implementation and Automated Test
```

DOC-06B owns route-level Outcomes and the permitted Resolution Strategies at the human-readable product level. A Resolution Strategy may continue, restart, redirect, wait, invoke controlled Support, or stop. It is not a route, persistent status, message, CTA, or notification, and it does not require a standalone software service.

Resolution must be capability-aware but disclosure-safe. PayPlus must use only authentication or recovery capabilities permitted by DOC-06B and the applicable account/route owner and must not reveal whether an account or login method exists before the required assurance. A remembered device, phone number, identity record, or provider email is not sufficient recovery proof; DOC-19 enforces security controls around owner-permitted capabilities without creating or permitting them.

The current AUTH-family resolution baseline is:

| Flow | Evaluation focus | Permitted resolution baseline |
| --- | --- | --- |
| `AUTH-LOGIN` | Current session, remembered-account eligibility, enabled login method, device and security context. | Resume an approved session, open Fast Login, open Full Login, or require Recovery. |
| `AUTH-LOGIN-FAST` | Biometric availability/result, remembered email, password fallback, and another-account choice. | Continue login, use password fallback, use Full Login, open Recovery, cancel, or wait/retry where permitted. |
| `AUTH-LOGIN-FULL` | Selected linked login method, credentials/provider result, account eligibility, and protected return. | Continue login, try another method, open Recovery, offer Registration where appropriate, cancel, or use Support where required. |
| `AUTH-REGISTRATION` | Attempt validity, provider/email verification, uniqueness, consent, and account-creation result. | Continue, restart, redirect to Login/Recovery, try another method, cancel, or stop account creation. |
| `ACCOUNT-ACTIVATION` | Missing phone, identity, and passcode requirements and each child result. | Invoke a missing child, wait for processing, permit retry/help, remain restricted, or complete and return after revalidation. |
| `PHONE-VERIFICATION` | Phone input, possession verification, replacement controls, expiry, restriction, and interruption. | Continue, resend, restart, wait, use Support, or stop where controls prohibit continuation. |
| `IDENTITY-VERIFICATION` | Current five-state identity status, provider processing, retry eligibility, and identity/security-owner-required update executed through a permitted Admin workflow. | Start/continue, wait and view status, retry/get help, perform an approved update, or remain blocked. |
| `PAYMENT-PASSCODE-SETTINGS` | Set/Change/Reset mode, matching entry, reauthentication, registered-phone access, restriction, and save result. | Continue, correct, retry, use controlled recovery, wait for reconciliation, cancel, or return safely. |

These mappings refine handling only. They do not change existing login, account-creation, activation, verification, passcode, security, or return decisions.

#### 5.0.1 `ENTRANCE-ROOT`

`ENTRANCE-ROOT` remains the Defined public unauthenticated root. Its fixed screen order is:

1. header with PayPlus logo, language action, and public Support and Terms actions;
2. full-width `ENTRANCE-CAROUSEL` image;
3. Carousel item-selection dots where more than one item is active;
4. horizontally arranged `Log In` and `Create Account` actions.

Language selection is a sheet or modal, not a route. Support and Terms handoffs must permit an anonymous-safe view. The Carousel and its detail route must not obscure, suppress, personalize, target, or change the defined Login and Registration actions. Public Entrance content is identical for all unauthenticated users.

##### Entrance Carousel Presentation and Interaction

`ENTRANCE-CAROUSEL` is a component, not a route. Promotion and Feature are its only permitted public content classes. Announcement is not an Entrance Carousel content class. A Promotion presentation may reference canonical Promotion or Offer source truth, but DOC-06B does not acquire that truth; each Feature must identify its formal product or business-truth owner.

The source image asset is `1080 x 1350`, equivalent to a `4:5` ratio. The current Carousel image uses the full available screen width. MVP Carousel presentation is image-only: it shows no promotion or feature name, no activity date, and no text overlay. The complete current image/Card is tappable and opens the existing `ENTRANCE-PROMOTION-DETAIL` child route.

When two or more items are active, interactive dots appear directly below the image and expose the selected item. A user may select an item by tapping its dot or by swiping horizontally. Automatic rotation occurs every five seconds and uses Crossfade. Manual dot selection or swipe pauses the current timer, gives the newly selected item one complete five-second interval, and then resumes automatic rotation. A movement threshold distinguishes swipe from tap; horizontal movement cancels detail activation so one gesture cannot both change the item and open detail.

The Login and Registration actions remain horizontally arranged immediately below the image and dots and must remain visible and unobscured. Exact responsive measurements, short-viewport treatment, focus mechanics, screen-reader expression, and adopted-platform implementation remain for later visual, accessibility, and technical evidence without changing this order.

##### Active Item Set and Sequence

The Entrance Carousel supports no more than five active items. At most one item may be designated as the priority item; when present, it appears first. All remaining items follow one deterministic manual order. Entrance does not use random ordering.

- With zero active items, omit the Carousel and dots while preserving the Header and horizontal Login / Registration actions.
- With one active item, show the static tappable image and omit automatic rotation, swipe, the first-use swipe cue, and an unnecessary dot control.
- With two to five active items, use the complete dots, swipe, Crossfade, timer, and first-use affordance behavior.

DOC-22 owns the corresponding placement-management controls, preview, publication, removal, and audit workflow without owning the source content.

##### First-Use Swipe Affordance

On the first applicable Entrance display after initial app use, and only where two or more items make horizontal navigation available, wait approximately `0.8` seconds, move the Carousel slightly left and right by approximately `8 px`, and return it to rest. The cue communicates that manual horizontal navigation is available. Any user interaction immediately cancels it, and the cue must not block tapping or swiping. Reduced-motion treatment removes or replaces positional movement. Exact persistence, animation, and platform implementation remain deferred to their later technical and validation owners.

##### `ENTRANCE-PROMOTION-DETAIL`

`ENTRANCE-PROMOTION-DETAIL` is the existing Defined baseline public child route. Its human-readable UI/UX behavior is decision-complete enough for continued alignment. It uses one image-first vertical composition:

1. header;
2. one visible Back control on the left and no separate Close control;
3. full-width `4:5` primary image using the `1080 x 1350` source ratio;
4. source-owned promotion/activity name;
5. source-owned activity date;
6. summary;
7. inline Terms;
8. zero or one owner-approved CTA where applicable.

Summary and Terms continue through one vertical scroll. Platform Back produces the same navigation result as the visible Back control. Back returns to `ENTRANCE-ROOT` and restores the same Carousel item and position.

The detail route may be informational and therefore show no CTA. Where a CTA exists, it must reference a current action and destination approved by the applicable source and route owners. Carousel placement and Admin configuration cannot invent or broaden an action, destination, eligibility, entitlement, or user-specific benefit. DOC-07 owns exact CTA Copy, hierarchy, disclosure, localization, and presentation.

##### Source Change and Owner Handoffs

An Entrance placement must be suspended when its Promotion or Feature source is withdrawn, is no longer authorized for public display, becomes prohibited by an applicable legal, privacy, permission, masking, or content restriction, or is materially changed after the placement's last approved preview/publication. A suspended placement is removed from the active Entrance presentation without deleting the source record or historical placement evidence. Return requires the updated presentation to be previewed and republished through the authorized DOC-22 workflow.

DOC-13 or the applicable Promotion/Offer owner retains Promotion and Offer validity, eligibility, entitlement, available-action, and business truth. The applicable formal Feature owner retains Feature business truth. DOC-22 owns only permitted Feature Management and central Entrance placement workflow/configuration execution. DOC-07 owns exact Copy; DOC-18 owns only business recording and explainability, while technical representation remains separately authorized; DOC-19 owns applicable access and security controls; DOC-20 owns acceptance evidence; DOC-21 owns monitoring and operations; and DOC-22 represents only the permitted Admin execution surface. Exact storage, timezone, source synchronization, scheduler and implementation mechanics remain with their applicable formal owners.

#### 5.0.2 Login Route Family

Tapping Log In invokes `AUTH-LOGIN`:

- resolve to `AUTH-LOGIN-FAST` when the device has a remembered account, the account has an eligible login method, and user-enabled biometric or password fast-login conditions remain valid;
- resolve to `AUTH-LOGIN-FULL` when Fast Login is unavailable, expired, revoked, or the user selects another account;
- bypass both child screens when an approved session can be resumed securely.

Fast-login eligibility lasts one month and is renewed by each successful login. Risk, device, credential, account, or security changes may revoke it earlier. PayPlus may remember the verified email identifier and approved device/session credential, but must never remember or store the plaintext password. The remembered email is masked on the pre-login screen.

On an eligible device, `AUTH-LOGIN-FAST` automatically presents the operating-system biometric prompt only where the user previously enabled biometric login. Cancellation, failure, or unavailability opens a slide-up sheet over a dimmed and blurred background containing:

1. masked remembered email;
2. password field with Forgot Password action;
3. device-appropriate `Use Fingerprint` or `Use Face ID` action;
4. `Log In`;
5. `Log In With Another Account`;
6. `Cancel`.

`Log In With Another Account` requires confirmation, revokes the current device session and refresh token, clears remembered account context, fast-login credential, and protected route history, then opens `AUTH-LOGIN-FULL`. It does not unlink account login methods. Cancel returns to `ENTRANCE-ROOT`.

`AUTH-LOGIN-FULL` shows Back, title, Continue with Google, Continue with Apple, and Continue with Email. Its Email view contains email, password, Forgot Password, Log In, and Cancel. The Email form is a view inside `AUTH-LOGIN-FULL`, not another route. Forgot Password opens `AUTH-RECOVERY`.

Provider identities use the stable provider-specific identifier. Matching email never creates, merges, transfers, or links an account. A linked provider may proceed through normal login and required step-up. An unlinked provider offers Create Account or Try Another Method without automatic email-based linking. Before the user proves control of an identifier, login and recovery errors must avoid confirming whether an account exists.

#### 5.0.3 `AUTH-RECOVERY`

`AUTH-RECOVERY` is one reusable flow for resetting an existing PayPlus login password or resolving account-access recovery through another approved method. It does not reset the Payment Passcode, recover Google or Apple credentials, create a provider-only user's first PayPlus password anonymously, change the primary email, merge accounts, or preserve authentication or payment authorization.

Invocation contexts are:

- Forgot Password from `AUTH-LOGIN-FAST` or the Email view in `AUTH-LOGIN-FULL`;
- a controlled Login or Registration conflict that permits Recovery without revealing account existence; and
- a protected destination that requires authentication before it can be reconsidered.

Recovery cases are internal modes or screen states inside `AUTH-RECOVERY`, not separate routes.

| Screen / state | Required product behavior |
| --- | --- |
| Recovery Start | Show Back, recovery title, a masked remembered email where permitted or editable email input, Continue, Try Another Login Method, Get Help, and Cancel. |
| Check Your Email | Show the submitted address subject to DOC-07 disclosure/masking rules and a neutral instruction to check email. Show `Cannot receive the email?`, a disabled `Resend` action with visible countdown, and clickable `Cannot Access This Email?`. Do not show `Open Email App` or an inline Change Email action; Back returns to Recovery Start for correction. |
| Link Validation | Validate the single-use deeplink silently. Show neutral loading only where needed and do not expose account, token, provider, restriction, or technical validation detail. |
| New Password | Show new-password and confirm-password fields, visibility controls, approved requirements, Confirm, and Cancel. Both entries must match before submission. |
| Recovery Resolution | Present only the safe next action permitted by the current Outcome, assurance, available capability, and control context. This is a conditional state, not a general error page or separate route. |
| Support-Authorized Setup | Permit restricted login-method setup only after approved Support recovery authorization. It does not create a normal authenticated session or bypass activation. |
| Recovery Complete | Confirm completion and session termination, then offer `Return to Log In` to `AUTH-LOGIN-FULL`. Successful reset does not log the user in. |

The Check Your Email presentation must behave equivalently where account, password, provider-link, restriction, or delivery eligibility cannot be disclosed. Exact wording, masking, Outcome IDs, Message IDs, CTA labels, and surface treatment belong to the DOC-07 Authentication slice.

##### Capability-Aware Recovery Resolution

Recovery evaluates the safest currently permitted path rather than presenting a raw-error catalogue.

| Situation / Outcome | Resolution Strategy | Product handling |
| --- | --- | --- |
| Recovery request accepted for neutral processing | Continue | Show Check Your Email without confirming account or password existence. |
| Reset link valid and an existing PayPlus password is eligible for reset | Continue | Open New Password in a restricted reset session. |
| Link invalid, expired, consumed, or reused | Restart | Permit Request New Link or Return to Login through the DOC-07 mapping. |
| Email inaccessible and an already-linked login method is safely usable | Redirect | Permit Try Another Login Method without exposing unverified linkage details. |
| Provider-only account has no PayPlus password | Redirect | Return to provider login or controlled Support; do not create a first password through anonymous Recovery. |
| Provider temporarily unavailable or cancelled | Redirect / Wait | Permit provider retry, another approved method, Provider Help, or Support as applicable. |
| No approved self-service method remains | Support | Begin controlled Support-assisted recovery. Phone OTP alone is insufficient. |
| Support cannot establish the required ownership assurance | Stop | Use a safe Recovery Not Permitted treatment without creating a security bypass or promising recovery. |
| Temporary security/service restriction or reset result is unconfirmed | Wait | Prevent unsafe duplicate submission, reconcile the result, and provide only an approved retry, return, or Support path. |
| Password reset completed | Redirect | Revoke affected sessions and authentication context, then return to `AUTH-LOGIN-FULL`. |

A trusted device, phone number, identity record, or provider-returned email may support risk or ownership assessment but is not an independent recovery capability unless DOC-06B and the applicable account/route owner permit it. DOC-19 enforces security controls around the permitted capability. Support is a controlled final recovery capability, not an ordinary convenience option.

##### Security, Support, and Return Rules

- A reset deeplink is single-use and expiring. Exact validity, resend cooldown, retry, throttling, and token mechanisms remain open under `OQ-19-001` with Security/Engineering and applicable DOC-17 provider contracts; DOC-14 retains abuse/risk trigger and outcome ownership.
- A valid link creates a restricted password-reset session only.
- Anonymous reset requests must not revoke sessions, lock the account, change credentials, or reveal account/login-method existence.
- Successful reset revokes active sessions, refresh tokens, Fast Login eligibility, remembered authentication context, biometric login binding, effective device trust, and sensitive pending authorization state. Device records remain where required for audit.
- Google and Apple credential recovery remains provider-owned. A usable linked provider may authenticate normally, after which first-password setup remains an authenticated `ACCOUNT-SECURITY` flow.
- If the primary email is unavailable and no linked login method works, Recovery hands off to controlled Support. DOC-06B owns the Recovery capability and route behavior; exact proof, cooling-off, restriction, and security mechanisms remain open with the applicable Product/Security/Operations owners and `OQ-19-001`/`OQ-19-005`; DOC-19 enforces approved security conditions, DOC-21 owns support and case handling, DOC-15 owns approved-purpose privacy/access requirements, and DOC-22 executes only the permitted Support/Admin workflow under those owner decisions.
- PayPlus may securely remember only an opaque intended destination during Recovery. After successful login, the destination and current permissions must be revalidated before return. Credentials, provider payloads, authorization results, and payment submission state must not be preserved.
- A payment return must revalidate the obligation, evidence, amount, fees, benefit selection, payment method, receiving destination, activation, payer authorization, and risk controls. Payment must never auto-submit after Recovery.

DOC-08 decides reset-link delivery and post-recovery security-notification treatment. DOC-18 owns recovery attempts, Outcomes, Resolution occurrences, correlations, session-revocation evidence, Support-case linkage, and audit lineage. DOC-20 owns detailed positive, neutral-equivalence, negative, expiry, replay, interruption, unconfirmed-result, accessibility, and return tests.

#### 5.0.4 Registration Attempt and Account Creation

`AUTH-REGISTRATION` offers Google, Apple, and Email paths:

- Google/Apple authenticates the provider, checks the stable provider identifier, uses a provider-confirmed verified email or verifies another entered email by OTP, checks primary-email uniqueness, captures referral context where applicable, records Terms/Privacy acceptance, and creates the restricted account;
- Email verifies the email by OTP, creates and confirms a password, captures referral context where applicable, records Terms/Privacy acceptance, and creates the restricted account.

A provider identity already linked to an account offers Continue to Log In. An unlinked provider whose proposed primary email already belongs to an account must stop account creation and direct the user to Login or Recovery; it must not link by email.

Before restricted-account creation, PayPlus records a temporary registration attempt, not an account:

- the attempt has its own attempt identifier and may retain temporary provider, email, phone, referral, consent, OTP, abuse-control, and audit context;
- it creates no account ID, dashboard, Inbox, user profile, referral attribution, login right, or financial permission;
- proposed email, phone, provider identity, and other login identifiers remain immediately available and are not reserved or occupied;
- killing or abandoning the app does not block an immediate new attempt using the same identifier;
- an old attempt may remain usable for up to 30 minutes of inactivity for security and continuation handling, without reserving an identifier; after that window it is expired/inactive for continuation and a new attempt may be required. The attempt record follows the accepted indefinite-retention direction subject to DOC-15 and Legal/Privacy lawful-scope, exception, restricted-class and prohibited-sensitive-data controls; it is not deleted, purged, erased, anonymised or disposed by this route baseline; a new attempt may invalidate an earlier OTP and remains subject to rate limits;
- final restricted-account creation atomically rechecks verified primary-email and provider-identity uniqueness, required verification, Terms/Privacy acceptance, and attempt validity;
- only the successful creation transaction claims the identifiers and creates referral attribution where applicable.

Referral deeplink or QR context remains prefilled and non-editable. Manual referral code entry remains optional and may be retried or cleared before account creation. DOC-13 owns attribution and qualification meaning.

After account creation, show `Complete Your PayPlus Setup` with `Complete Now` and `Do It Later`. Complete Now opens `ACCOUNT-ACTIVATION`; Do It Later opens `HOME-ROOT` with the applicable persistent Action Required banner.

#### 5.0.5 `ACCOUNT-ACTIVATION`

`ACCOUNT-ACTIVATION` completes full registration; it is not labelled payment setup. It may open after restricted-account creation, from the Home Action Required banner, or when a financially restricted action detects an incomplete requirement. It presents only the missing requirements and routes to `PHONE-VERIFICATION`, `IDENTITY-VERIFICATION`, or `PAYMENT-PASSCODE-SETTINGS`.

Account Activation orchestrates these handoffs but does not own or duplicate the reusable child routes. `PHONE-VERIFICATION` and `IDENTITY-VERIFICATION` are canonically under `ACCOUNT-PROFILE`; `PAYMENT-PASSCODE-SETTINGS` is canonically under `ACCOUNT-SECURITY`. When Account Activation invokes a child, completion or cancellation returns to `ACCOUNT-ACTIVATION` with refreshed completion state. A child opened from its canonical parent returns to that parent.

| Missing requirement | Banner | Action |
| --- | --- | --- |
| Two or more | `Complete your PayPlus setup` | `Complete Now` |
| Phone only | `Verify your phone number` | `Verify Now` |
| Identity only | `Verify your identity` | `Verify Now` |
| Passcode only | `Set up Passcode` | `Set Up Now` |
| Nothing missing | Banner hidden | None |

All banner actions enter `ACCOUNT-ACTIVATION`, which focuses the applicable incomplete step. Completion removes the registration-level restriction and returns to the originating permitted context: Home remains on Home; an interrupted payment or controlled action returns to that action after revalidation. Completion does not bypass evidence, role, payment, provider, risk, compliance, or other feature-specific gates.

One verified primary email, one verified phone number, and one verified individual identity may each belong to only one active individual account. A phone or identity conflict discovered after restricted-account creation blocks activation and routes to Login, Recovery, or controlled Support handling without automatic account merging.

The reusable child-flow behavior is defined in Sections 5.17.4.2 and 5.17.4.3. Account Activation must consume those flows without duplicating their screens or statuses. DOC-17 owns applicable provider-integration contracts and mappings; DOC-19 owns mechanism-neutral protected-value, retry/replay, session, and recovery security enforcement while exact mechanisms remain open under `OQ-19-001`; DOC-21 owns support handling; DOC-15 owns approved-purpose privacy/access requirements; and DOC-22 executes only owner-permitted workflow/configuration. Exact technical mechanics remain outside DOC-06B.

#### 5.0.6 Return, Failure, and Ownership Rules

Normal successful login opens `HOME-ROOT`. An approved protected deeplink resumes its intended destination only after authentication and current access revalidation; invalid, expired, consumed, or unauthorized destinations fall back to the safest owning root or Home without exposing protected content. Logout returns to `ENTRANCE-ROOT` and clears protected route history.

DOC-07 owns the Authentication Bounded Domain Slice and its linked Semantic, Disclosure, and CTA Contracts for governed user-facing communication. Exact Outcome, Message, and CTA IDs, approved Copy, Locale Variants, Presentation Mappings, Notification mappings, runtime/audit mappings, and acceptance mappings remain open with their applicable owners. DOC-06B owns route-level Outcome meaning, permitted Resolution Strategies, component and placement, action destination, entry and return behavior, and adaptive presentation referenced by those contracts. In-flow authentication messages are not Inbox notifications unless DOC-08 separately defines a notifiable event.

DOC-06A owns journey sequence, DOC-07 owns user-facing content and disclosure, DOC-13 owns referral attribution, DOC-15 owns account/privacy handling, DOC-18 owns only business recording and explainability; technical representation remains separately authorized; DOC-19 owns mechanism-neutral security controls, DOC-20 owns detailed test evidence, DOC-21 owns support handling, and DOC-22 owns permitted Admin execution and Entrance content configuration.

### 5.1 Design Intent

The logged-in Home Dashboard is the default landing screen after login.

It must be task-first. It should prioritize urgent Payer actions, payment-related obligations, owner-controlled outcome or action-required meaning, payment instructions, and recent payment records before promotional discovery.

The dashboard is not a marketing page. Promotions, partner offers, hot offers, PayPlus events, and feature announcements may appear only through controlled placements and must not obscure payment tasks or status visibility.

This section defines the designated dashboard flow and layout baseline for MVP discussion. It is not the finalized UI design, visual design, component specification, or exact route-level screen specification. Exact UI details remain subject to later DOC-06B refinement and future design/specification work.

Visual references:

- `docs/diagrams/payplus-home-dashboard-mvp-wireframe.svg` is a companion wireframe for this section. It supports human and AI understanding of layout hierarchy but does not override this document.
- `docs/diagrams/routes/payplus-app-route-map.md` is the Level 0 Mermaid navigation map. Detailed Home, Bills, Instructions, Payment Profile, Activity/Receipts, Offers/Rewards/Referral, Me, and Archive route families are maintained in separate maps listed in `docs/diagrams/README.md`; retired Request identifiers may remain only as historical alignment evidence. These diagrams are discussion and alignment aids, not final UI design.

---

### 5.2 Bottom Navigation

MVP bottom navigation should use five primary destinations.

| Nav Item | Definition | Route Relationship | Current Status |
| --- | --- | --- | --- |
| Home | Default task-first dashboard. | Opens `HOME-ROOT`. | Discussion baseline |
| Bills | Saved Bill/Rent source and tenancy-context management area, with contextual handoffs to owner-governed obligation and payment actions. | Opens Bills area covering saved Bill/Rent sources and their DOC-06C sub-routes. Instructions, receipts, cards, referral, and More remain separate management routes or shortcut destinations unless explicitly embedded as contextual handoffs; retired Request identifiers are non-active documentation lineage only. | Discussion baseline |
| Pay+ | Central Payer action-sheet entry. | Opens `PAYPLUS-ACTION-SHEET` for the four retained Payer-only actions defined in Section 5.3.2: `Pay a Bill`, `Pay Rent`, `Add Bill / Rent`, and `Continue Payment`, preserving their accepted order and material meaning. Request Payment is retired; no replacement Request or Linking action is introduced. | Defined behavior / final visual design open |
| Offers | Promotion and partner-offer discovery area. | Opens `OFFERS-ROOT`. Issued rewards and referral participation remain separate routes reached through contextual handoffs. | Working baseline |
| Me | Permanent account and user-control area. | Opens `ME-ROOT` for account information, security and privacy, Bills access, payments and records, rewards, Referral, preferences, support, About PayPlus, terms, and logout. | Core account child routes defined / other details pending |

`Pay+` should be visually treated as the primary center action in the bottom navigation.

---

### 5.3 Pay+ Action Sheet

Tapping `Pay+` should open `PAYPLUS-ACTION-SHEET`, a slide-up action sheet rather than an independent root route.

The sheet contains user-friendly entry actions only. It creates no request, obligation, instruction, payment, or payout by itself and must not expose internal implementation terms.

#### 5.3.1 Wave 2 Layout and Motion Principles

The designated baseline is:

1. the sheet animates upward over the current screen;
2. the background is dimmed and blurred to focus attention while preserving context;
3. four retained icon-and-label actions use the existing two-row grid:
   - first row: `Pay a Bill`, `Pay Rent`;
   - second row: `Add Bill / Rent`, `Continue Payment`;
4. action icons and labels enter with the sheet animation;
5. the center `Pay+` button toggles the sheet open and closed;
6. closing reverses the opening motion.

The design must support reduced-motion accessibility. No replacement action, fifth action, reorder or material rename is introduced by this route baseline. Exact iconography, measurements, spacing, blur strength, motion duration, easing, and final styling remain open.

#### 5.3.2 Action and Destination Rules

| Action | Destination | Required Behavior |
| --- | --- | --- |
| `Pay a Bill` | `BILLS-PAY` | Open a temporary Bill/Fee/non-rent selection scope without overwriting the user's saved Bills filters. After selection, hand the Bill source to the owner-controlled resolver for the applicable Payable Basis, current eligibility and Checkout condition under Section 5.20. A new Checkout may begin only when DOC-09 permits and no active continuable Checkout exists for the same basis; otherwise the journey resumes/resolves the existing Checkout or remains in the source-owner context. |
| `Pay Rent` | `BILLS-PAY` | Open a temporary Rent/Tenancy selection scope with the same saved-filter rule, then hand the Rent source to the same owner-controlled Checkout resolver while preserving Rent/tenancy context. |
| `Add Bill / Rent` | `BILLS-ADD` | Start controlled Bill or separate Rent setup. Bill Evidence is optional for Tier 1 and required where the applicable Bill tier requires it; Rent retains mandatory attached Evidence. QR scan, file/photo upload, and manual entry remain inside this flow and are not standalone Pay+ payment actions. |
| `Continue Payment` | `INSTRUCTIONS-DETAIL` or `INSTRUCTIONS-ROOT` | Count active pending Payment Instructions and continuable incomplete Checkout Workspaces, including items blocked by an applicable owner-controlled review. With none, show the action disabled; with one, open its detail; with more than one, open the list. An item blocked by an applicable owner-controlled review remains visible but cannot continue until that blocking condition is resolved. A label-only Company/Individual review does not qualify when every concrete owner-controlled gate passes. |
| Retired Request Payment | None | The former payee-to-payer Request action is retired from active MVP. No replacement action or route is created by this route baseline. |

The remaining four actions preserve their existing order and meaning. Bill entry remains Category-first; Rent remains a separate journey. Save is an action/projection, not a route. No fifth action, replacement Request flow, Directory root or self-provided root is introduced.

For an owner-recorded Tier 3 approval outcome, the Payer remains in, or returns to, the actual current Bill source context. The outcome does not navigate, authorize, Resume, submit or create an executable Checkout. A preserved Bill, `BILLS-PAY`, or prepared Workspace context must not be replaced by an artificial detail-page hop. The Payer deliberately selects the current Bill `Pay` action to invoke the same DOC-09 Checkout Resolver. It may Resume the prepared Workspace only after current revalidation confirms that Workspace is active, eligible and continuable; otherwise it stays in, or returns to, the current source-owner or historical resolution. No Tier 3 notification, route, direct notification-to-Checkout edge, or new recovery object is created.

#### 5.3.3 Completion, Availability, and Return Rules

- Standalone Pay+ `BILLS-ADD` completion may offer the existing `Pay Now` action only when the applicable specialist-owner outcomes permit payment continuation for the established Bill/Rent source; `Back to Home` remains available. Otherwise, present the applicable owner-governed verification or readiness outcome without enabling `Pay Now`. This route rule does not treat the Bill/Rent source as a Payment Obligation or define a new status.
- No historical Request reader or Request-origin `BILLS-ADD` return is defined.
- Completed or cancelled Payment Instructions, and closed or expired incomplete Checkout Workspaces, are excluded from `Continue Payment` eligibility.
- A globally unavailable or unlaunched action may be hidden. A user-specific, temporary, or applicable owner-controlled blocking restriction should leave the action visible but disabled with a safe explanation that does not expose internal risk logic. A label-only Company/Individual review does not create such a restriction when every concrete owner-controlled gate passes.
- Selecting an action closes the sheet and hands control to the owning route. Cancelling or closing the sheet returns to the unchanged originating screen and must not reopen the sheet.
- Opening the sheet must not silently discard unsaved work or interrupt external authorization. The app should block opening or require a leave confirmation where needed.
- The sheet and destination routes must prevent duplicate activation, and every destination must revalidate evidence, eligibility, risk, authorization, payment, and payout gates owned by the relevant documents.

The Pay+ action sheet must not create wallet, stored-value, cashout, unsupported P2P, generic QR payment, or automatic recurring-payment behavior.

#### 5.3.4 Configuration and Data Handoffs

DOC-22 may execute only product- and specialist-owner-approved enablement settings by module, category, market, launch phase, or approved user segment and must record configuration changes under the applicable audit requirements. Admin controls must not rename, reorder, or redirect the confirmed action semantics or bypass destination gates.

Material privacy-safe signals for later DOC-18 specification include sheet opened, sheet dismissed, action availability evaluated, action selected, blocked-reason category, and destination-handoff result. These signals must not contain sensitive evidence, identity, card, bank, request, or payment values.

---

### 5.4 Home Dashboard Section Order

The Home Dashboard should use the following MVP section order.

| Order | Section | Definition | Display Rule | Route Relationship |
| ---: | --- | --- | --- | --- |
| 1 | Header | Presents the contextual Greeting and quick access to high-priority utilities. | Always shown. | Greeting has no navigation action. Inbox and coupon/rewards icons route to their respective screens. |
| 2 | Important Notice | Presents one eligible Inbox-backed important notification without creating a duplicate Home notification record. | Zero eligible candidates hides the section. Dismiss is canonical-session-scoped and changes no notification or business state. | Body opens `NOTIFICATION-DETAIL`; Action Button opens the source-provided destination. |
| 3 | Shortcut Grid | Operational shortcuts for common management tasks. Must not duplicate Pay+ direct payment-start actions. | MVP default and maximum is 8 shortcuts including protected `More`. Users may keep fewer than 7 configurable shortcuts, but `More` remains present. | Each shortcut routes to its related management area. |
| 4 | Hot Offer | Offer-only carousel of canonical Offers selected by Admin for Home presentation. | Maximum five; zero candidates hides the section. | Every card and CTA opens canonical `OFFER-DETAIL`. |
| 5 | Upcoming Bills / Rent | Presents up to three active payer-role Bill and Rent candidates supplied by DOC-06C. | HKD-only MVP; deterministic canonical ordering. | `Pay Now` and `View Details` enter the source-owning route. |
| 6 | Recent Activity | Presents up to five completed payment-related outcomes supplied by DOC-09, DOC-10, and DOC-11. | Excludes technical events, intermediate states, failures, instructions, requests, and general Bill/Rent changes. | Item opens `ACTIVITY-DETAIL`; `View More` opens `ACTIVITY-ROOT`. |

Dashboard section order may be refined later only through explicit design review. This baseline intentionally places Hot Offer below shortcuts and above Upcoming Bills / Rent.

---

### 5.5 Header Utilities

| Element | Definition | Route Relationship |
| --- | --- | --- |
| Greeting | Contextual user-recognition text. | No navigation action. |
| Inbox icon | Payer-facing notifications, messages, payment alerts, support replies, system notices, and announcements. | Opens `NOTIFICATION-INBOX` only. No Request-era routing, runtime reader, adapter or fallback is defined. |
| Coupon / rewards icon | Shortcut to the user's issued coupons, vouchers, and other supported rewards. | Opens `REWARDS-ROOT`. |

Greeting uses the applicable local time:

- 05:00 - 11:59: Morning;
- 12:00 - 17:59: Afternoon;
- 18:00 - 04:59: Evening.

Server time may be used only with an applicable timezone; otherwise the approved neutral fallback is used. Display-name precedence is:

1. user-defined Nickname;
2. `Mr./Miss + eKYC surname` when applicable title data exists;
3. surname only when surname exists without applicable title data;
4. no displayed name otherwise.

DOC-07 owns TC, SC, and EN presentation. Greeting is normally one visual line, while assistive technology receives the complete rendered greeting. Technical time, timezone, and account-data mechanics remain with their formal owners.

#### Important Notice Contract

Important Notice presents one eligible Inbox-backed notification at a time and does not create a duplicate Home notification record. Promotions, Rewards, marketing, and ordinary feature announcements are ineligible by default.

Eligible candidates are ordered by:

1. Severity;
2. Category;
3. source-owned Business Priority Rank;
4. issued timestamp, newest first.

Category order is System, Payment, Account, then Other Important. Every ordering key is a canonical value supplied by its owning source domain. HOME-ROOT must not derive, normalize, reinterpret, or supply fallback ordering semantics. A missing or invalid ordering value is an upstream contract matter.

The Banner body opens canonical `NOTIFICATION-DETAIL`; the Action Button opens the source-provided destination. Dismiss is canonical-session-scoped and changes no read, resolved, expired, withdrawn, or business state. When Notification Details closes, enter Inbox if another eligible Important Notice exists; otherwise return Home. Zero eligible candidates hides the section.

Rent-reminder eligibility uses the source-provided canonical due timestamp: the effective due date is 23:59 in its canonical timezone; Home eligibility ends 24 hours later; and proposed due-date changes have no effect until applied to the canonical Bill/Rent record. DOC-07 owns severity and user-facing Message/CTA expression; DOC-08 owns notification lifecycle, eligibility, fields, Inbox, Details, and read state; source owners own business state, deadlines, resolution, destination, and Business Priority Rank; DOC-06B owns Home presentation, session-scoped dismiss behavior, and navigation. Technical session mechanics remain outside DOC-06B.

---

### 5.6 Shortcut Grid

The shortcut grid provides quick access to common non-payment-start tasks.

Shortcut grid items are entry points, not independent feature owners. Each shortcut should open or deep-link to the relevant owning route, screen, sheet, or management area. The owning document for the destination continues to govern detailed behavior.

MVP shortcut grid:

| Shortcut | Definition | Route Relationship |
| --- | --- | --- |
| Instructions | Payment instructions / 付款指示 for pending pay-later setups, incomplete split-card payments, pending funding legs, expired instructions, and action-required instruction items. | Opens `INSTRUCTIONS-ROOT`. |
| Bills & Tenancies | Saved Bill/Rent sources and tenancy contexts, Evidence-status handoffs, due-date presentation and contextual links to applicable owner-governed obligations. | Opens `BILLS-ROOT`. |
| Receipts | Payment receipts and statements. Proof of payment remains available from relevant Activity contexts for MVP. | Opens `RECEIPTS-ROOT`. |
| Reminders | User-set due reminders for Bill/Rent source contexts, explicitly owner-permitted obligation references, and manual reminders. | Opens `BILLS-REMINDER-LIST`. |
| Cards | Payment Profile route for managing tokenized cards and saved split-card profiles. The shortcut is an entry point, not checkout. | Opens `PAYMENT-PROFILE-ROOT`. |
| Referral | Referral entry point for sharing the user's reusable referral link, monitoring attributed-referee qualification, and managing corresponding referrer or referee rewards where enabled. | Opens `REFERRAL-ROOT`. Referral campaigns may be promoted in `OFFERS-ROOT`, but attribution, progress, and referral reward claiming remain owned by the Referral route. |
| More | Opens remaining or secondary shortcuts and services. | Opens `MORE-ROOT`. |

Support should not be part of the initial eight dashboard shortcuts. Support remains accessible through `Me`, issue-specific status screens, and/or `More` if enabled.

Shortcut display must support:

- an admin-managed approved catalog, default set, default order, and availability rules;
- a maximum of 7 user-configurable Home shortcuts plus protected `More`;
- fewer than 7 configurable shortcuts where the user prefers;
- account-level user order and visibility preferences overriding the eligible owner-approved default;
- `More` remaining present as the final shortcut and recovery entry;
- restore to the current eligible owner-approved default.

Detailed user behavior is defined in Section 5.18. DOC-22 may execute only DOC-06B-owner-approved shortcut configuration. User preference, visibility, and privacy/data handling belong in DOC-15 and DOC-18.

---

### 5.7 Hot Offer Carousel

Hot Offer is an Offer-only Home presentation surface. DOC-22 executes the product-owner-approved selection of which canonical Offers appear on Home; it does not decide Offer truth or eligibility. Home may present an Offer when `AdminHomePresentationEnabled` is true, except where an explicit canonical legal, privacy, permission, masking, or prohibited-content restriction forbids presentation. Offer status, validity, and redemption eligibility do not themselves block Home display.

Any canonical Offer status may be displayed, including not-started, active, expired, used-up, paused, and non-redeemable. HOME-ROOT must not automatically filter by Offer status, validity, redemption eligibility, or inferred display eligibility. `SourceHomeDisplayEligible` and the former multi-gate Home formula must not be created or restored. Admin presentation must not alter, suppress, reinterpret, or falsify canonical Offer truth. Every card and CTA opens canonical `OFFER-DETAIL`, which presents current canonical status and available actions.

The carousel displays a maximum of five cards and is hidden when no owner-approved, Admin-selected candidates are available for presentation. DOC-22 may execute the approved fixed or random ordering configuration; random ordering may reshuffle on each fresh Home entry. Auto-rotation defaults to five seconds and is Admin-configurable within the approved presentation policy.

Rotation stops while keyboard focus is inside the carousel, pointer hover is active, touch/swipe/drag/manual navigation is occurring, or assistive/accessibility interaction is active. Rotation may resume only after the interaction ends. After manual interaction, one complete five-second interval must elapse before rotation resumes. A separate visible Pause/Play control is not required unless the adopted platform accessibility standard requires one. Reduced motion removes transition animation but may continue rotation under the same non-disruption rules. Normal platform component practices govern accessible naming, position information, focus, and announcements.

DOC-06B does not validate Offer-content completeness. Empty fields render blank and are not a HOME-ROOT Error. DOC-13 owns canonical Offer content, status, validity, eligibility, and business truth. DOC-22 executes only owner-approved selection, publication workflow, ordering, interval and administrative quality controls. Retrieval, source, session, and bootstrap failures retain their owning-domain classification.

---

### 5.8 Upcoming Bills / Rent

Upcoming Bills / Rent consumes active payer-role candidates from DOC-06C, combines Bill and Rent candidates, supports HKD only for MVP, and displays up to three items. Fields follow the canonical Bill/Rent card baseline.

HOME-ROOT orders candidates by:

1. nearest due date;
2. higher amount;
3. Rent before Bill;
4. canonical creation timestamp, earliest first;
5. stable source-provided record ID when all preceding values are equal.

HOME-ROOT consumes these canonical values and does not derive their meaning. Only `Pay Now` and `View Details` are authorized. Both enter the source-owning route, which revalidates before any protected action. Missing amount or due date is an upstream invariant or retrieval failure, not a valid Home candidate. Overdue remains a Bill/Rent business state. HOME-ROOT introduces no additional masking beyond canonical privacy and payment-instrument rules.

---

### 5.9 Recent Activity

Recent Activity displays up to five completed payment-related outcomes:

- Payment Complete;
- Partial Payment;
- Payout Complete;
- Refund or Reversal.

Items are ordered by each owner's canonical ordering timestamp, newest first. Technical events, intermediate states, failures, instructions, requests, and general Bill/Rent changes are excluded. Multiple supporting technical events must not duplicate one outcome. Distinct Partial Payment outcomes remain separate. Refund and Reversal share the Home presentation while retaining distinct source meaning.

Amount sign follows the canonical funds-flow direction published by DOC-09, DOC-10, or DOC-11. HOME-ROOT must not infer, reverse, or reinterpret the sign from Consumer Payer or economic-Payee classification. User-facing expression follows DOC-07 and the status-display reference matrix without creating a new cross-domain outcome model.

`View More` opens `ACTIVITY-ROOT`. Selecting an item opens canonical `ACTIVITY-DETAIL`. Detail returns to Home when opened from Home and to `ACTIVITY-ROOT` when opened from Activity.

### Home Resilience Contract

HOME-ROOT uses smallest-practical-surface graceful degradation. Whole-Home handling applies only when the canonical session is invalid or unavailable, authentication or authorization cannot be established, the Home shell/bootstrap cannot be established, or identity/overall presentation authority cannot be safely determined.

Source and technical owners supply cache authorization, freshness, and failure classification. Retry is scoped to the failed section unless a bootstrap exception applies. Successfully loaded zero candidates is Empty; failed retrieval is Error. Blank Hot Offer fields are not Error. Authorized stale/offline data may be shown only with unsafe actions disabled or revalidated through the source route. Accessibility implementation is not part of the resilience contract.

### Home Accessibility Contract

HOME-ROOT does not create a separate accessibility mode or duplicate platform accessibility standards. DOC-06B owns only Home-specific interaction requirements, including complete rendered Greeting output, carousel stop/resume behavior during active interaction, keyboard and non-swipe controls, focus and return behavior, and section-state semantics. Normal platform component practices govern accessible naming, position information, focus, and announcements. DOC-06D maps the requirements; DOC-20 holds later detailed evidence; implementation mechanics remain with platform and technical owners.

### Home Presentation Governance

Admin controls approved presentation, not canonical business truth. Offer status is not itself a Home visibility gate. Existing explicit canonical legal, privacy, permission, masking, and prohibited-content restrictions continue to apply.

Admin must not alter due dates, amounts, permissions, payment status, notification lifecycle, severity, Business Priority Rank, or other business semantics. Admin must not suppress business-owned Upcoming Bills / Rent, Recent Activity, Important Notice truth, payment obligations, or other business-owned facts. Analytics, retention, event policy, configuration versioning, preference history, technical schema, and implementation remain with their formal owners.

---

### 5.10 Route IA Workplan and Placeholder Titles

The DOC-06 family must next define what users see, what buttons exist, what each button does, and how route areas interact. The following titles are intentionally preserved as the working map so the route-level UI discussion does not lose scope.

| Area | Purpose of Future DOC-06 Family Detail | Current Status |
| --- | --- | --- |
| Entrance and Authentication Routes | Maintain the defined `ENTRANCE-ROOT`, Entrance Carousel, `ENTRANCE-PROMOTION-DETAIL`, Login family, Registration, Recovery boundary, Account Activation, Phone Verification, Identity Verification, and Payment Passcode behavior; finalize exact Copy, provider mapping, technical/security implementation, prototype and accessibility evidence, and tests. | Defined baseline / `ENTRANCE-PROMOTION-DETAIL` human-readable behavior is decision-complete for continued alignment / downstream evidence pending and non-blocking |
| Bottom Navigation Route Map | Define how `HOME-ROOT`, Bills, `PAYPLUS-ACTION-SHEET`, Offers, and Me relate to top-level routes and deep links. | Working baseline; final visual design open |
| Pay+ Action Sheet Detail | Maintain the confirmed four-action Payer-only behavior after `Request Payment` retirement, destinations, availability, completion, return, and configuration boundaries; finalize only the remaining exact visual specification. | Defined behavior / final visual design open |
| Bills Tab IA | Define bill, fee, rent, tenancy, evidence, reminder, payment history, and setup sections under the Bills route. | Working baseline / not finalized |
| Offers and Rewards IA | Define `OFFERS-ROOT` discovery, category collection routes, `OFFER-DETAIL`, separate issued-reward management, referral handoff, and placement behavior. | Offers child-list baseline defined / not final visual design |
| Me Area IA | `ME-ROOT` is the permanent account-control route. Its section order, established-route handoffs, core account child-route behavior, masking, reveal, state, and return boundaries are defined in Section 5.17. | Core account child routes defined / other details pending |
| More Shortcuts IA | Maintain `MORE-ROOT` shortcut management, reorder/arrangement, restore-default behavior, approved secondary-service entry, and protected access to More. | Defined baseline / final visual design open |
| Requests Route | Preserve stable IDs as non-active documentation lineage only; no active route shell, runtime reader, deep-link adapter, creation flow, party-linking, request lifecycle or replacement action. | Retired active MVP / mandatory Wave 6 artifact alignment |
| Instructions Route | Define payment instruction / 付款指示 route shell, deliberate Payment Instruction versus incomplete Checkout Workspace display, Payment Instruction cancellation, Checkout continuation/Close/Expiry, and checkout handoff. | Working baseline / not finalized |
| Bills & Tenancies Route | Define saved Bill/Rent source projections, tenancy detail, Evidence-status handoff, Payee/landlord detail, due dates and linked payment actions without collapsing a source into one Payment Obligation. | Title preserved / not finalized |
| Activity Route | Define the global Payer account-level financial activity route shell, single-entry transaction lifecycle behavior, and status-display matrix handoff. | Route shell defined / not final UI |
| Receipts & Statements Route | Define the searchable receipt/statement list, direct download, shared PDF preview, return behavior, and re-issue handoff. | Root and preview behavior defined / not final PDF design |
| Reminders Route | Define due reminders, user-set reminders, notification settings, and reminder destinations. | Title preserved / not finalized |
| Payment Profile Route | Define tokenized card management, saved split-card profile management, card status, default card, profile action-required behavior, and checkout/instruction handoff. | Route shell defined / not final UI |
| Referral Route | Define `REFERRAL-ROOT`, referral attribution and progress presentation, role-sensitive entitlement list/detail/claim screens, registration handoff, and issued-reward handoff. Referral campaigns may be discovered through Offers, but Referral remains a separate route. | Child-screen behavior defined / not final visual design |
| Admin-Configurable UI Marker List | Mark app UI elements that require permitted Admin execution later without drafting Admin UI in DOC-06. | Title preserved / DOC-22 owns only the permitted execution UI under the applicable product and specialist owners |

App UI elements that currently require Admin execution markers include owner-approved Pay+ action availability, shortcut visibility/order/defaults, Hot Offer Home presentation, feature/module enablement and route-level application of owner-controlled user-type, Category, launch-phase, risk or compliance availability outcomes. Important Notice is source-driven: Admin may support approved inspection and audit but must not alter, suppress, or replace its canonical ordering, lifecycle, audience/permission, due-time or destination values.

---

---

### 5.11 Non-Active Documentation Register - Retired Requests and Linking IDs

The following concise register preserves retired stable IDs only as non-active documentation evidence. Founder confirmation establishes that no production Request/Payee-role runtime or legacy Request deep-link data exists. It is not a route, runtime reader, action, notification, Linking flow, adapter or fallback.

| Retained identifier or record | Preservation location | Current treatment |
| --- | --- | --- |
| REQUESTS-ROOT, REQUESTS-DETAIL, REQUESTS-NEW, BILLS-RECEIVE, BILLS-LINKING and associated actions | Stable IDs and prior actor-role/lineage meanings in append-only documentation history | Retired active MVP; no production data, route, runtime reader, action, notification, adapter, fallback, acceptance, Linking, reciprocal visibility or replacement behavior |
| Former Request/Linking status and response concepts | Append-only documentation history only | Retired terminology and lineage evidence; no production facts, authorized runtime reader, active lifecycle or participant state machine |



### 5.12 Payment Instructions Route

The user-facing route label may be `Payment Instructions` or `付款指示`.

The route manages two distinct item kinds: deliberate pay-later Payment Instructions and incomplete Checkout Workspaces that remain continuable. It is not the normal pay-now checkout route, not a bill/rent reminder route, not a request route, not full card management, and not payment history. Surfacing both item kinds in the same management route does not make an incomplete Checkout Workspace a Payment Instruction.

| Field | Requirement |
| --- | --- |
| Root product destination | `INSTRUCTIONS-ROOT` |
| Detail product destination | `INSTRUCTIONS-DETAIL` |
| Optional traceability screen reference | `SCREEN-06B-INSTRUCTIONS-DETAIL` |
| Primary owner | DOC-06B owns route shell, list/detail layout, entry points, high-level actions, and route handoff. |
| Payment owner | DOC-09 owns Payment Instruction and Checkout Workspace business meaning, funding and monetary invariants, payer-authorization boundaries, confirmed Payment creation, Payment Application, and continuation rules. DOC-06B owns route-level screen behavior and presentation. |
| Related owners | DOC-08 owns notification delivery; DOC-13 owns promotion quote impact; DOC-15 owns masking/privacy; DOC-18 owns only business recording and explainability; technical representation remains separately authorized; DOC-19 owns security/tokenization. DOC-22 may execute only DOC-09- and specialist-owner-permitted Admin configuration/workflows; it owns no Payment Instruction, funding, monetary, authorization or continuation policy. |

#### 5.12.1 Instruction Definition

A Payment Instruction is a deliberate user-created pay-later arrangement. It is not created merely because an immediate Checkout is interrupted, partly funded, failed, cancelled, or abandoned.

Payment instruction is created only where:

- the user intentionally creates a pay-later instruction within the allowed instruction window;
- the instruction requires user action before payment can proceed.

An immediate Checkout that has started execution but has not fully funded its Checkout Target remains an incomplete Checkout Workspace. It may appear in this route only for continuation or, when DOC-09 makes it non-continuable, historical Checkout presentation after Close or Expiry; it retains its own Checkout identity and lifecycle. Close or Expiry is not source Archive. If it contains a newly confirmed Payment linked to an otherwise unsaved source, the owner-controlled Payment Result/Save resolver must establish same-ID Saved/current or history-only before any ordinary return from that result to Instructions, Activity, Receipt or another safe exit; an already Saved/current source retains its projection. Normal completed payments belong to receipt/activity surfaces. A user who wants an alert without creating a pay-later arrangement should create a normal reminder.

#### 5.12.2 Instruction Types

| Managed Item | Meaning | User Edit Boundary |
| --- | --- | --- |
| Pending Payment Instruction | User intentionally set up a future/pay-later arrangement and no Provider Submission has been initiated for the related Checkout. | User may update the instruction's permitted setup before execution. When Checkout begins, DOC-09 target-lock and authorization rules apply. |
| Incomplete Checkout Workspace | Immediate payment execution started but the immutable Checkout Target was not fully funded. It is not a Payment Instruction. | User may continue or, where DOC-09 permits, Close Checkout; Expiry ends continuation. Neither outcome is source Archive. Confirmed Payments and Payment Applications remain immutable; the locked Checkout Target and Obligation Allocations cannot be reduced or redefined. |

`Pay Now` is not an instruction type and does not identify a predetermined Checkout. It is a Payment Instruction action that invokes the DOC-09 Checkout Resolver. Every attempt may have session, provider, or audit records, but only deliberate pay-later arrangements are Payment Instructions.

#### 5.12.3 Entry Points

| Entry Point | Route Behavior |
| --- | --- |
| Dashboard shortcut `Instructions` | Opens `INSTRUCTIONS-ROOT`. |
| Pay+ `Continue Payment` | Disabled when no active pending Payment Instruction or continuable incomplete Checkout Workspace exists; opens `INSTRUCTIONS-DETAIL` for exactly one or `INSTRUCTIONS-ROOT` for more than one. Items blocked by an applicable owner-controlled review remain visible but cannot continue; label-only Company/Individual review does not block when every concrete owner-controlled gate passes. |
| Important Notice / Action Required | Its body opens `NOTIFICATION-DETAIL`. After current-state and permission revalidation, the source-provided Action Button may open the relevant `INSTRUCTIONS-DETAIL` where a specific instruction exists. |
| Payment action notification | Opens `NOTIFICATION-DETAIL` first. After current-state and permission revalidation, an owner-approved instruction action may invoke the same DOC-09 Checkout Resolver. It must not bypass Notification Detail or identify a predetermined Checkout. |
| Checkout flow | Creates or updates a Payment Instruction only when the user deliberately chooses pay later. An interrupted or partly funded immediate Checkout returns as an incomplete Checkout Workspace without conversion into an instruction. |

#### 5.12.4 `INSTRUCTIONS-ROOT` List Screen

`INSTRUCTIONS-ROOT` displays existing instruction cards and provides the entry point for creating a new instruction. It should not process payment directly.

Recommended screen order:

1. Header: `Payment Instructions` or `付款指示`.
2. Top action: `+ Add Instruction`.
3. Filter row: `All`, `Pay Later`, `Incomplete`.
4. Managed-item card list.
5. Empty state.

Cards should be compact. They should not behave like a full payment summary or receipt, and must identify whether the item is a Payment Instruction or an incomplete Checkout Workspace.

MVP card fields:

- linked bill/rent/fee name;
- category;
- payee / recipient name;
- intended amount for a Payment Instruction, or immutable Checkout Target plus remaining target amount for an incomplete Checkout Workspace;
- item type and current user-facing condition;
- timing label:
  - pending instruction: `Pay on [date]`;
  - incomplete Checkout Workspace: `Expires in X days`, `Expires today`, or `Expired`.

Card action:

- `View Detail` opens `INSTRUCTIONS-DETAIL`.

The card should not show detailed quote, fee, promotion, or full payment profile status. Those belong in the instruction detail screen or DOC-09 checkout/review.

#### 5.12.5 `INSTRUCTIONS-DETAIL` Detail Screen

`INSTRUCTIONS-DETAIL` explains and controls one Payment Instruction or one incomplete Checkout Workspace. It is a context and management screen; actual payment submission remains in `PAYMENT-CHECKOUT` under DOC-09 domain rules.

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

- `Pay Now`, invoking the DOC-09 Checkout Resolver after current instruction and payer validation;
- `Update Instruction`;
- `Cancel Instruction`.

Instruction `Pay Now` does not unconditionally create, activate, or resume Checkout. The route consumes the resolver result owned by DOC-09:

| Resolver result | Route-level treatment |
| --- | --- |
| An active Checkout remains eligible and continuable for the instruction's current Payable Basis | Resume that existing Checkout after revalidation. Do not create another Checkout. |
| No active continuable Checkout exists and current instruction, obligation, evidence, eligibility, timing, and control conditions permit creation | Enter an eligible New Checkout with the instruction and source-aware return context. |
| The action is stale, withdrawn, expired, ineligible, unavailable, or otherwise cannot proceed | Remain in `INSTRUCTIONS-DETAIL` or return the applicable instruction/source-owner resolution. Do not create, resume, or reactivate Checkout. |

Before route handoff, the presentation must use current owner-supplied validity and action availability. The Checkout Workspace must revalidate applicable fees, benefits, funding, destination, risk, security, and authorization conditions. No stale authorization is carried forward, and tapping `Pay Now` creates no silent Funding Leg or Provider Submission.

For an incomplete Checkout Workspace, show:

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

Incomplete Checkout actions:

- `Continue Payment`, routing to DOC-09 checkout/review for remaining eligible action;
- `Close Checkout` only where DOC-09 permits it.

Incomplete Checkout must not allow reduction or redefinition of the locked Checkout Target, Obligation Allocations, confirmed Payments, or Payment Applications. Permitted changes to unexecuted funding arrangements must remain within the locked Checkout Target and follow DOC-09 allocation-version and renewed-authorization rules. Closing or expiry ends continuation only and does not rewrite confirmed financial facts. Where a newly confirmed Payment exists for an otherwise unsaved source, any user-facing close or ordinary safe return must first complete the owner-controlled same-ID Save/projection resolution; this route does not offer Save itself.

#### 5.12.6 Add Instruction Flow

`+ Add Instruction` starts an instruction setup flow, not a generic checkout shortcut.

The flow should:

1. require the Payer to select an existing eligible Bill/Rent source; DOC-09 determines any current Payable Basis and Payment Obligation required for instruction setup;
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
| Notification-backed Payment Instruction action alert | Enters `NOTIFICATION-DETAIL`; after current-state, authenticated-payer, permission, target, and action-availability revalidation, an owner-approved current CTA may invoke the DOC-09 Checkout Resolver. It does not enter `INSTRUCTIONS-DETAIL`, `PAYMENT-CHECKOUT`, or checkout/review directly. |

This avoids duplicate user functions:

- Reminders mean "remind me about a Bill/Rent source context or an explicitly owner-permitted obligation reference."
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
- for incomplete Checkout Workspaces, preserve confirmed Payment and Payment Application facts and route only to permitted continuation, closure, or correction actions; where a newly confirmed Payment belongs to an otherwise unsaved source, complete the owner-controlled same-ID Save/projection resolution before closure or an ordinary safe return.

Handoff behavior:

- actual checkout selection, split allocation for the current payment, quote recalculation, card-leg authorization, and payment submission are governed by DOC-09;
- reusable card and split-profile management belongs to `PAYMENT-PROFILE-ROOT`;
- the provider-controlled card-data boundary belongs to DOC-16, provider tokenization and return mechanics to DOC-17, security treatment to DOC-19, and final PCI applicability/scope to professional assessment.

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
- incomplete Checkout Workspace continued;
- incomplete Checkout Workspace closure or Expiry presented;
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
| Final visual layout, field density, and exact button labels distinguishing Payment Instruction cards from incomplete Checkout Workspace cards | Product / Design | Open |
| DOC-09-owned continuation-period countdown presentation, and distinction between instruction cancellation and Checkout Close/Expiry presentation | Product / Payments / Operations | Open |
| Exact visual copy, placement, and return-state UI for handoff among `INSTRUCTIONS-DETAIL`, `PAYMENT-PROFILE-ROOT`, and DOC-09 checkout. Route direction is clarified in `docs/diagrams/routes/payplus-instructions-route-map.md` and `docs/diagrams/routes/payplus-payment-profile-route-map.md`. | Product / Payments / Security | Open |
| Exact user-facing notification/message/CTA wording and semantics, plus timing, delivery, eligibility, and current action availability for Payment Instruction action alerts | DOC-07 for wording and CTA semantics; DOC-08 for timing, delivery, eligibility, and current action availability; Product / Payments as applicable | Open |

---

### 5.13 Payment Profile Route

The final user-facing route label is `Payment Profile`. The dashboard shortcut may remain `Cards`.

The route manages reusable payment setup objects. It is not checkout, not a wallet, not a stored-value account, and not a way to move money without an eligible controlled Bill/Rent obligation under the applicable owner Evidence treatment.

| Field | Requirement |
| --- | --- |
| Product destination | `PAYMENT-PROFILE-ROOT` |
| Primary owner | DOC-06B owns route shell, entry points, major screens, route handoff, and high-level user actions. |
| Payment owner | DOC-09 owns actual checkout selection, payment quote, split-card allocation for a payment, authorization, funding-leg submission, and payment states. |
| Security owner | DOC-16 owns the provider-controlled card-data architecture boundary; DOC-17 owns PSP/acquirer tokenization and provider mechanics; DOC-19 owns mechanism-neutral card-data, token/reference, authentication, and secure-boundary controls; final PCI applicability/scope requires professional confirmation. |
| Related owners | DOC-07 owns wording; DOC-08 owns notifications; DOC-13 owns card-linked benefit rules; DOC-15 owns masking/privacy; DOC-18 owns only business recording and explainability; technical representation remains separately authorized; DOC-19 owns token/security controls. DOC-22 may execute only owner-permitted Admin configuration/workflows and owns no payment, card/profile or security policy. |

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
| `ME-ROOT` / Payments & Records | Opens `PAYMENT-PROFILE-ROOT` or the relevant card/profile screen. |
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

When opened from the dashboard shortcut or `ME-ROOT`, the route behaves as a normal management area.

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

`PAYMENT-CARD-ADD` should route through the approved PSP/acquirer tokenization flow. PayPlus should store only the token/reference and permitted masked metadata. It must not store raw card number, CVV, magnetic-stripe data, or sensitive authentication data outside PayPlus storage and retention scope.

A default card may be set for single-card checkout. It may be pre-selected in checkout, but the user must be able to change it before authorization.

Removing or updating a card should show a confirmation prompt by default. Payment-passcode confirmation should be optional where the user enables it in user settings. Additional step-up may still apply where PSP/acquirer, risk, or security rules require it. Removal should use a non-destructive inactive/archive marker; no hard deletion is introduced.

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

When the Payment Profile capability is available and entered, present eligible profiles without silently preselecting or applying one. Starred or frequent profiles may appear first. Current-Checkout allocation remains a separate owner-confirmed capability. Direct entry where only one capability is available removes only the unnecessary capability-choice step; the payer must still complete the applicable selection or configuration within that capability.

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

1. present a neutral choice between a saved Payment Profile and a current-Checkout split only when the applicable owners make both capabilities available and the payer intentionally expands from single-card funding;
2. derive current-Checkout allocation from the selected profile ratios and current Checkout Target, or from the payer's current-Checkout allocation choices, without treating a profile as authorization;
3. allow eligible amount or ratio adjustment before authorization, subject to DOC-09 allocation and locking rules;
4. allow saving the adjusted split as a new or updated profile only where the applicable owner permits it;
5. authorize and submit each applicable Funding Leg sequentially under DOC-09;
6. describe the Checkout as fully funded only when confirmed obligation-funded value reaches the Checkout Target, while preserving every immutable Payment created by an earlier confirmed Funding Leg, including after partial funding.

DOC-06B does not define card or Payment Profile eligibility. Each applicable current-Checkout allocation change remains traceable through the authoritative Funding Allocation Version history or the owner-approved equivalent audit record. Section 5.20 defines the complete Checkout Workspace treatment and return behavior.

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
| Final PSP/acquirer tokenization return behavior and permitted card metadata | Payments / Security / DOC-17, with DOC-19 security treatment and DOC-18 representation | Open |

---

### 5.14 Activity Route

Activity is the event and lifecycle view of what happened in a user's PayPlus account. It is not the same as a receipt, statement, internal audit log, or bill/rent-specific activity timeline.

DOC-06B owns the global Activity route shell. DOC-06C owns `BILLS-ACTIVITY` for one selected Bill/Rent source. DOC-08 owns receipt and statement communication. DOC-09, DOC-10 and DOC-11 own payment, payout, refund, reversal and failure meaning. DOC-18 owns only business recording and explainability, including internal-review-history meaning; technical representation remains separately authorized. DOC-22 owns permitted Admin operations only.

| Field | Requirement |
| --- | --- |
| User-facing route label | `Activity` |
| Product destinations | `ACTIVITY-ROOT`, `ACTIVITY-DETAIL` |
| Purpose | Let a Payer review account-level financial activity for Bill/Rent Payments and related outcomes. |
| Boundary | Activity lists events and lifecycle status. It must not become the receipt/statement file library, the bill/rent-specific timeline, or an internal audit log. |

#### 5.14.1 Entry Points

| Entry Point | Destination |
| --- | --- |
| Dashboard Recent Activity arrow / View More | `ACTIVITY-ROOT` |
| `ME-ROOT` / Activity row | `ACTIVITY-ROOT` |
| Payment, payout, refund, return, or reversal notification | `ACTIVITY-DETAIL` where a specific transaction exists; otherwise `ACTIVITY-ROOT`. A notification cannot bypass any required unsaved-source projection resolution. |
| Checkout or Payment Result where activity review is needed | `ACTIVITY-DETAIL` for the submitted transaction where available, only after an existing Saved/current projection is retained or the owner-controlled Save resolver has made an otherwise unsaved source Saved/current or history-only. |

Bill/rent `View Activities` opens DOC-06C `BILLS-ACTIVITY`, not `ACTIVITY-ROOT`. `BILLS-ACTIVITY` stays contextual to one bill/rent record.

Activity never offers Save. For a newly confirmed Payment linked to an otherwise unsaved source, Payment Result must resolve selected Save to same-ID Saved/current or declined/skipped/dismissed Save to same-ID history-only before `ACTIVITY-ROOT` or `ACTIVITY-DETAIL` becomes the downstream destination. A source already Saved/current before Payment retains that projection without duplicate Save.

#### 5.14.2 Root Views

`ACTIVITY-ROOT` is a Payer-only account-level view. It does not provide a Payee role, receiving view, reciprocal visibility or participant navigation:

| View | Meaning |
| --- | --- |
| `All` | Payer account-level Bill/Rent Payment activity and related outcomes. |
| `Paid` | Payer-submitted or Payer-authorized Payment activity. |
| Retired identifier lineage | Request, Linking or receiving identifiers remain non-active documentation evidence only; no runtime or active view is created. |

Refunds, reversals, returns, failures, and rejected outcomes should appear in the relevant view with mapped status labels. They should not have a separate top-level MVP view unless later product usage justifies it.

#### 5.14.3 Activity Root Screen Behavior

`ACTIVITY-ROOT` should behave like a bank or accounting activity list. It is designed for scanning transaction-like entries first, then expanding one entry only when the user wants more actions.

Recommended screen order:

1. Header: `Activity`.
2. Payer activity view: `All` and `Paid` as applicable to the current product surface.
3. Optional search or filter row if enabled.
4. Activity list, newest first, grouped by date where useful.
5. Empty state where no activity exists.

Each collapsed activity entry should show:

| Field | Requirement |
| --- | --- |
| Date | Activity or transaction date. |
| Rent / bill / fee name | Authoritative Bill/Rent source name or, where the entry is owned at another layer, the linked Payment Obligation, Payment or activity name. |
| Payee name | Intended or matched Payee name, masked where required. |
| Amount | Display the Payer-side amount and applicable outcome direction. |
| Status | User-facing mapped status from `docs/traceability/status-display-reference-matrix.md`. |

Amount direction should follow the user's account perspective:

| Scenario | Display Direction |
| --- | --- |
| User paid as Payer | Payment amount and mapped outcome direction. |
| Refund returned to Payer | Refund amount and mapped outcome direction. |
| Return, reversal, or adjustment | Direction follows the Payer account impact and mapped status. |

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

Permitted receipt, proof, invoice, or evidence viewing/downloading in Activity does not require an extra passcode or step-up prompt solely for opening or downloading the document. The user must still be authenticated and authorized for the document; restricted actions remain hidden.

One transaction should normally appear as one activity entry. Payment, settlement, payout, receipt, refund, return, and reversal milestones should update the same activity lifecycle where they belong to the same transaction, instead of creating duplicate entries that describe the same payment.

#### 5.14.4 Activity Detail

`ACTIVITY-DETAIL` should show:

- transaction ID or reference ID;
- payment reference ID where available;
- payout or transfer reference ID where available;
- bill/rent/fee/payment name;
- counterparty;
- amount with positive/negative direction from the user's account perspective;
- payer action/outcome label, such as `Paid`, where applicable;
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

The Activity detail route displays the current Bill/Rent and Payment context. Retired Request or Linking identifiers remain non-active documentation lineage only and are not an Activity context, runtime reader or navigation surface.

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

DOC-06B owns the route, list, search, preview handoff, and entry points. DOC-08 owns receipt/statement content, notification, delivery, and re-issue communication. The applicable Payment, Payout, refund/dispute and Finance owners determine transaction-document truth and permitted correction or re-issue outcomes. DOC-15 owns masking, retention and approved-purpose access. DOC-18 owns only business recording and explainability; technical representation remains separately authorized. DOC-22 may execute only an explicitly owner-permitted correction or re-issue workflow and cannot rewrite immutable financial facts.

| Field | Requirement |
| --- | --- |
| Full route label | `Receipts & Statements` |
| Dashboard shortcut label | `Receipts` |
| Product destinations | `RECEIPTS-ROOT`, `RECEIPT-DETAIL`, `STATEMENT-DETAIL` |
| Purpose | Let users find, preview, and download transaction receipts and account statements. |
| Boundary | This route is a file/document hub. It should not replace Activity, checkout, bill/rent activity, or internal audit history. |

#### 5.15.1 Entry Points

| Entry Point | Destination |
| --- | --- |
| Dashboard shortcut `Receipts` | `RECEIPTS-ROOT` |
| `ME-ROOT` / Receipts & Statements row | `RECEIPTS-ROOT` |
| Receipt notification | `RECEIPT-DETAIL` |
| Statement notification | `STATEMENT-DETAIL` |
| `ACTIVITY-DETAIL` receipt action | Direct file download or `RECEIPT-DETAIL` where an in-app PDF preview is needed |
| `ACTIVITY-DETAIL` proof action | Direct file download for MVP |
| DOC-06C `BILLS-ACTIVITY-DETAIL` receipt/proof action | Direct file download by default |

Receipt and statement routes do not offer Save and cannot bypass Payment Result projection resolution. A receipt or statement entry associated with a newly confirmed Payment for an otherwise unsaved source is a downstream destination only after the owner-controlled resolver makes the source Saved/current or history-only; an already Saved/current source retains its projection.

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
- payer action/outcome indicator, such as `Paid`;
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

Permitted receipt and statement preview/download within an authenticated session does not require an extra passcode or step-up prompt solely because the file is viewed or downloaded. Protected data export under `PRIVACY-DATA-CONTROLS` remains a separate higher-assurance process.

#### 5.15.6 Re-Issue and Versioning

If a receipt or statement is wrong, replaced, or re-issued:

- the latest valid version should be shown by default;
- prior versions must be retained where required for audit, tax, support, and dispute handling;
- version number or issue timestamp should be stored;
- affected users should be notified where material;
- explicitly permitted Admin workflow and re-issue execution belongs in DOC-22; transaction-document truth and permitted correction/re-issue outcomes remain with the applicable Payment, Payout, refund/dispute and Finance owners;
- final document metadata, lineage and versioning representation belong in DOC-18, while DOC-15 owns retention governance and requirements and DOC-18 represents those approved requirements in the data model;
- notification and wording rules belong in DOC-08.

#### 5.15.7 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Final Activity visual styling, field density, search/filter behavior, grouping behavior, and empty-state copy | Product / Design | Open |
| Final receipt/statement PDF layout, visual design, export naming, and sharing controls | Product / Design / Finance / Legal | Open |
| Final receipt/statement correction/re-issue policy and permitted Admin workflow | Applicable Payment, Payout, refund/dispute and Finance owners for truth and permitted outcomes; DOC-21 for operations; DOC-22 for owner-permitted execution only | Open |

### 5.16 Offers and Rewards Routes

#### 5.16.1 Route Boundary and Register

Offers, issued rewards, and referral serve different user intentions and must not be treated as one route:

| Destination | Parent | Type | User-Facing Purpose | Owner | Definition Status |
| --- | --- | --- | --- | --- | --- |
| `OFFERS-ROOT` | Offers area | Root screen | Discover current Featured / Hot, card, Pay+, and partner offers. | DOC-06B | Defined baseline |
| `OFFERS-CARD-LIST` | `OFFERS-ROOT` | Child collection screen | View all Card Offers. | DOC-06B | Defined baseline |
| `OFFERS-PAYPLUS-LIST` | `OFFERS-ROOT` | Child collection screen | View and filter all Pay+ offers. | DOC-06B | Defined baseline |
| `OFFERS-PARTNER-LIST` | `OFFERS-ROOT` | Child collection screen | View and filter all partner offers. | DOC-06B | Defined baseline |
| `OFFER-DETAIL` | `OFFERS-ROOT` or an Offers child list | Route-addressable full-screen modal | Understand one offer and take its configured action. | DOC-06B; DOC-13 for offer logic | Defined baseline |
| `REWARDS-ROOT` | Rewards area | Root screen | Search, filter, and manage rewards already issued to the user, including launch-supported coupons, vouchers, external-partner instruments, and miles entitlements. | DOC-06B; DOC-13 for reward logic | Defined behavior |
| `REWARD-DETAIL` | `REWARDS-ROOT` | Route-addressable full-screen modal | View one issued reward's full details, terms, status, and permitted contextual action. Checkout, Referral, notification, and deeplink are alternative entry contexts, not route parents. | DOC-06B; DOC-13 for reward logic; DOC-09 for checkout | Defined behavior |
| `REFERRAL-ROOT` | Referral area | Root screen | Share the user's reusable referral link/code, select an active campaign where applicable, monitor attributed-referee qualification, and enter role-sensitive referral reward management. | DOC-06B; DOC-13 for referral logic | Defined baseline |
| `REFERRAL-REWARDS-LIST` | `REFERRAL-ROOT` | Child list screen | View the current user's corresponding referrer and referee reward entitlements through `Available to Claim` and `History` views. | DOC-06B; DOC-13 for entitlement logic | Defined behavior |
| `REFERRAL-ENTITLEMENT-DETAIL` | `REFERRAL-REWARDS-LIST` | Child detail screen | View one referral reward entitlement's campaign, benefit, conditions, claim deadline, usage expiry, and available action without displaying referral-party information. | DOC-06B; DOC-13 for entitlement logic | Defined behavior |
| `REFERRAL-REWARD-CLAIM` | `REFERRAL-ENTITLEMENT-DETAIL` | Confirmation flow | Confirm conversion of an approved referral entitlement into an issued reward instrument. | DOC-06B; DOC-13 for issuance logic | Defined behavior |

`OFFERS-ROOT` is a discovery route. `REWARDS-ROOT` is an issued-benefit management route. `REFERRAL-ROOT` is the PayPlus Referral Program management route for existing users participating as referrers and/or referral-reward beneficiaries. They may link to one another but must not redefine one another's behavior. Referral attribution does not create payer/payee linking, a Request, payment authority, or shared financial visibility.

What's New is not an Offers category by default. A dashboard What's New item should open its announcement or feature destination unless the item is also an approved offer governed by DOC-13.

Coupons, vouchers, external-partner benefits, and miles are reward-instrument classifications inside `REWARDS-ROOT`; they are not separate routes. A direct checkout discount, service-fee waiver, or special rate is not an issued reward and must not appear in `REWARDS-ROOT` unless DOC-13 creates a separate reward entitlement or instrument.

Navigation is defined by transition rather than by assigning an ID to every entry action:

| Source | User Action | Destination | Return Behavior |
| --- | --- | --- | --- |
| Bottom navigation | Tap `Offers` | `OFFERS-ROOT` | Normal bottom-navigation behavior. |
| Home Hot Offer | Tap an offer | `OFFER-DETAIL` | Return to Home and the prior carousel position. |
| `OFFERS-ROOT` | Tap any displayed offer | `OFFER-DETAIL` | Return to the same section and scroll position. |
| `OFFERS-ROOT` | Tap Card Offers `View More` | `OFFERS-CARD-LIST` | Return to the Card Offers section. |
| `OFFERS-ROOT` | Tap Pay+ Offers `View More` | `OFFERS-PAYPLUS-LIST` | Return to the Pay+ Offers section. |
| `OFFERS-ROOT` | Tap Partner Offers `View More` | `OFFERS-PARTNER-LIST` | Return to the Partner Offers section. |
| Any Offers child list | Tap an offer | `OFFER-DETAIL` | Return with search, filter, and scroll state preserved. |
| `OFFERS-ROOT` | Tap My Rewards banner | `REWARDS-ROOT` | Return to the prior Offers position. |
| Home rewards icon | Tap | `REWARDS-ROOT` | Return to Home. |
| `REWARDS-ROOT` | Tap a reward | `REWARD-DETAIL` | Return with the prior view and scroll state preserved. |
| DOC-09 checkout reward selector | Tap `View Details` for an eligible reward | `REWARD-DETAIL` | Close returns to the same checkout context without consuming, reserving, or selecting the reward. |
| Dashboard Referral shortcut or `Me` | Tap Referral | `REFERRAL-ROOT` | Return to the originating context. |
| `OFFER-DETAIL` | Take a referral-program action | `REFERRAL-ROOT` | Return to the originating offer where supported. |
| `REFERRAL-ROOT` | Tap `View Referral Rewards` | `REFERRAL-REWARDS-LIST` | Return to the selected campaign and prior Referral position. |
| `REFERRAL-REWARDS-LIST` | Tap a referral reward card or `View Details` | `REFERRAL-ENTITLEMENT-DETAIL` | Return with the selected tab and list position preserved. |
| `REFERRAL-ENTITLEMENT-DETAIL` | Tap `Claim Reward` | `REFERRAL-REWARD-CLAIM` | Cancel returns to entitlement detail. After issuance, `View Reward` opens `REWARD-DETAIL`; `Done` returns to `REFERRAL-REWARDS-LIST` with `History` selected and the issued item visible. |
| `REFERRAL-REWARDS-LIST` or `REFERRAL-ENTITLEMENT-DETAIL` | Tap `View Reward` for an issued instrument | `REWARD-DETAIL` | Return to the originating Referral context where supported. |
| Referral deeplink or QR | Open referral link as a prospective new user | Registration/onboarding with the referral code and campaign context prefilled | After successful registration attribution, continue the normal onboarding destination; this does not open a Referral child route. |
| Promotion or reward notification / approved deeplink | Open the referenced item | Relevant detail destination, or the corresponding root when no item is identified | Return to prior app context where available; otherwise use the corresponding root. |

#### 5.16.2 `OFFERS-ROOT` Screen

MVP screen order:

1. header with Back, title `Offers`, and Search icon;
2. My Rewards banner opening `REWARDS-ROOT`;
3. Featured / Hot Offers carousel, maximum 3 displayed offers;
4. Card Offers carousel, automatic slide, randomized order, maximum 4 displayed offers, and `View More`;
5. Pay+ Offers grid, maximum 6 displayed offers and `View More`;
6. Partner Offers grid, maximum 6 displayed offers and `View More`.

Randomized Card Offers must be selected only from active, approved, eligible-for-display offers after mandatory admin priority, targeting, consent, and compliance gates are applied. Exact refresh frequency and randomization method belong to later technical and admin specifications.

An offer may belong to more than one discovery collection where its characteristics genuinely overlap. Collection membership is display metadata and does not change DOC-13 eligibility or benefit rules. The same Offer ID should appear only once on a normal `OFFERS-ROOT` rendering, using its admin-configured primary placement, while remaining available in every relevant complete child collection. An audited admin override may intentionally repeat an offer on the root where approved.

The Search icon opens route-local search rather than a new route. Search should support offer title, partner or sponsor, offer category/label, eligible payment method, and relevant keywords without exposing internal rule fields. If no active offers match, show a no-offers state while keeping search reset and My Rewards available.

`View More` opens a dedicated collection route:

| Source Section | Destination | Required Screen Structure |
| --- | --- | --- |
| Card Offers | `OFFERS-CARD-LIST` | Back, title `Card Offers`, Search icon, and a single-column Card Offer list. No visible label filter is required for MVP. |
| Pay+ Offers | `OFFERS-PAYPLUS-LIST` | Back, title `Pay+ Offers`, Search icon, single-select label filters with `All` as default, and a single-column Pay+ offer list. |
| Partner Offers | `OFFERS-PARTNER-LIST` | Back, title `Partner Offers`, Search icon, single-select label filters with `All` as default, and a single-column partner-offer list. |

For this section, an **offer card** is only the UI component used to summarize an offer. A **payment card** is a credit/debit funding instrument, and a **Card Offer** is an offer whose eligibility depends on permitted payment-card attributes. These terms must not be used interchangeably.

All three child collection screens use this shared behavior:

1. Show Back, collection title, and Search in the header.
2. Open route-local Search without creating another route.
3. Show the applicable single-select label filters below Search where enabled.
4. Render each Offer ID once within the current child list.
5. Open `OFFER-DETAIL` when the user taps an offer card or `View Details`.
6. Preserve search, filter, loaded position, scroll position, and display order when returning from `OFFER-DETAIL`.
7. Show loading placeholders, a no-offers empty state, a no-match state with reset action, and a recoverable error with Retry where applicable.

Child-list ordering controls discovery position only. After mandatory approval, display-period, market, privacy, consent, targeting, compliance, and enablement gates, apply collection-specific admin pinning/priority, permitted personalization within that priority band, and then a deterministic fallback. Preserve the resulting order during the browsing session. Child lists do not randomize or provide user sorting for MVP; the limited root Card Offers carousel remains a separate placement behavior.

Offer label-filter values for Pay+ Offers and Partner Offers remain open. This concerns Offer filtering only and does not reopen the settled four-action `PAYPLUS-ACTION-SHEET` labels, order or destinations. Each relevant offer must carry one or more approved category/label references so filtering can be supported. DOC-13 owns the business metadata requirement, DOC-18 owns final schema, and DOC-22 owns label administration and placement controls.

Back from a collection route returns to `OFFERS-ROOT` at the originating section and prior scroll position. Back from `OFFERS-ROOT` returns to the prior app context where one exists; otherwise it returns to Home.

An offer card should show:

- partner or PayPlus identity;
- offer title;
- short benefit summary;
- applicable category or payment method where material;
- expiry or ending-soon information;
- concise availability or claim-method label;
- `View Details` action.

Material acceptance, claim, redemption, or payment actions should occur in `OFFER-DETAIL`, not directly on the discovery card.

Where a payment-method-sensitive offer hands off to checkout, `OFFER-DETAIL` may identify the offer as a candidate but must not finalize its selection. DOC-09 checkout evaluates the selected payment card/profile, DOC-13 automatically applies the single eligible Card Offer with the highest user value per payment card/funding leg, and checkout displays that result together with any separate eligible coupon/voucher/discount selection before authorization.

#### 5.16.3 `OFFER-DETAIL` Screen

`OFFER-DETAIL` opens as a full-screen modal that can also resolve as a notification or deeplink destination. Its screen structure is:

1. offer key visual;
2. Close icon;
3. offer title and sponsor;
4. offer details;
5. contextual action area.

Offer details should show:

1. offer title and sponsor;
2. benefit summary;
3. how the benefit is applied or delivered;
4. eligible bill, fee, rent, payment method, card, user, or partner conditions where applicable;
5. minimum amount, eligible amount cap, quota, frequency, or usage limit where user-relevant;
6. campaign period, claim period, and usage period as separate dates where they differ;
7. current eligibility, entitlement, claim, or availability outcome where known;
8. material terms, exclusions, and expandable full terms;
9. one contextual primary action and relevant secondary action.

The action target is configured by the offer and may open an approved campaign landing page, card-application flow, external link, in-app screen, referral route, or reward-redemption action. External targets must use approved destinations and must not expose sensitive PayPlus data in the URL or handoff.

The primary action depends on the DOC-13 benefit-delivery method:

| Benefit Context | User Action and Handoff |
| --- | --- |
| Direct checkout discount, fee waiver, or card-linked offer | `View Eligible Bills` or equivalent hands off to DOC-06C `BILLS-PAY`; `BILLS-PAY` remains outside the Offers route and DOC-09 owns checkout. |
| Redeemable coupon, voucher, or other reward | `Redeem` first checks current eligibility, campaign availability, quota, entitlement, and prior-redemption state under DOC-13. A successful redemption creates or confirms the reward entitlement/instrument. The primary button changes to non-actionable `Redeemed`, and `View My Reward` appears and opens `REWARDS-ROOT`. |
| Already redeemed reward | Show non-actionable `Redeemed` and `View My Reward`, which opens `REWARDS-ROOT`. |
| External partner benefit | Claim or eligibility confirmation precedes any approved QR, code, deeplink, or partner handoff. |
| Referral campaign | `View Referral` opens `REFERRAL-ROOT`; Offers does not manage invitations or progress. |

If redemption fails or the user is not eligible, no entitlement or reward instrument is created and the UI must show a clear, non-sensitive reason or next step. Closing an offer opened from an Offers route returns to the same search, filter, section, and list position. Closing an offer opened from Home, notification, or deeplink returns to the prior app context where available; otherwise it returns to `OFFERS-ROOT`.

#### 5.16.4 `REWARDS-ROOT` and `REWARD-DETAIL`

The user-facing label for `REWARDS-ROOT` is `My Rewards`. It manages issued reward instruments and is not a wallet, stored balance, transferable value, cashout right, campaign-discovery route, referral-progress route, or checkout owner.

`REWARDS-ROOT` has two route-local views:

- `Active`: non-terminal instruments shown with `Available`, `Action Required`, `In Progress`, or `Under Review` status as defined in the status-display reference matrix;
- `History`: terminal instruments shown with `Used`, `Credited`, `Expired`, or `Reversed` status.

Search is route-local and may match reward name, partner/program, source, and approved benefit wording. It must not search or expose redemption credentials or internal references. Instrument filters are `All`, `Coupons & Codes`, `Vouchers`, `Partner Benefits`, and `Miles`; these are classifications, not statuses. Any status filter must use the status-display reference matrix.

Active ordering is: Action Required; Available rewards within the configurable expiring-soon window by nearest expiry; other Available rewards by expiry with no-expiry items last; In Progress; Under Review. The default expiring-soon window is seven calendar days. History uses latest lifecycle event first. User sorting is not required for MVP.

A reward card is a component, not a route. It shows:

- reward name and benefit summary;
- source, program, or sponsor;
- instrument type;
- current user-facing status;
- relevant expiry, completion, or lifecycle date;
- `View Details`.

The card and `View Details` open `REWARD-DETAIL`. Cards must not reveal QR credentials, redemption codes, internal risk reasons, referral-party information, or partner payloads. Loading, no-rewards, no-active-rewards, no-history, no-match with reset, recoverable-error with Retry, and permitted cached read-only states must be supported. `Explore Offers` may appear only when no issued rewards exist; an empty Active view should preserve access to History.

`REWARD-DETAIL` opens as a full-screen modal and shows, in order:

1. Close control and reward key visual;
2. reward name and full benefit;
3. current status and safe explanation;
4. source, campaign, program, or sponsor;
5. instrument type, issue date, usage period, and expiry;
6. full eligibility, restrictions, limits, and usage method;
7. complete, expandable terms and conditions;
8. one contextual action only where meaningful.

Checkout coupons, vouchers, and discounts normally show `Available at checkout` and their conditions without a default direct-use action. Reward selection remains in the DOC-09 checkout after the payer selects a payment card or payment profile. If detail is opened from checkout, Close returns to the same checkout context without changing reward selection.

External instruments may expose only their configured action, such as `Show QR`, `Reveal Code`, permitted `Copy Code`, or `Open Partner`. Miles instruments show fulfilment progress and masked destination-account information where permitted, without a use action. `Action Required` may expose the action needed to resolve the issue. Held or terminal instruments show a safe explanation and no decorative use button.

Revealing or copying a credential, opening a partner destination, or viewing detail does not mark an instrument `Used`. Only an authoritative DOC-13 redemption or fulfilment result changes lifecycle status. On return from an external destination, PayPlus refreshes the same detail without assuming success. Unknown outcomes must prevent unsafe duplicate use until reconciled.

Closing detail restores its origin: Rewards preserves view, search, filter, list order, and scroll; Referral restores its prior context; checkout restores checkout; notification or deeplink returns to prior app context where available, otherwise to `REWARDS-ROOT`. Cached non-sensitive metadata may be read-only with last-updated information, but checkout use, credential reveal, and partner handoff require current revalidation unless a later approved fulfilment method explicitly permits otherwise.

#### 5.16.5 Referral Routes

PayPlus has one Referral Program. Every existing PayPlus user may act as a referrer without a separate program-enrolment action. The MVP supports one active referral campaign; later campaigns remain selectable as a route-local view rather than separate routes.

`REFERRAL-ROOT` screen order is:

1. header with Back, title `Referral`, and terms action;
2. campaign selector, hidden when only the MVP campaign is available;
3. selected campaign benefit, qualification, period, limit, and material-condition summary;
4. separate referrer and referee benefit explanation;
5. reusable personal referral code/link;
6. `Share`, `Copy Link`, and `Show QR` actions using approved external share channels;
7. attributed-referee qualification summary and list;
8. referral reward summary and `View Referral Rewards`;
9. no-active-campaign, no-attributed-referee, campaign-ended, and recoverable-error states.

Opening a system share sheet, copying a link, or displaying a QR does not identify a recipient and must not create an invitation card or user-facing `Awaiting acceptance`, `Accepted`, `Declined`, or `Expired` invitation status. A referee appears only after an eligible new user completes registration using a valid referral code/link.

The registration handoff must support:

- referral deeplink or QR context with the code shown, prefilled, and not editable;
- an optional manual referral-code field for ordinary registration;
- immediate validation before registration completion;
- invalid-code handling that lets the user re-enter the code or leave the field blank;
- immutable normal-user attribution after registration completes with a valid code;
- one MVP campaign without a campaign selector; where multiple campaigns are later enabled, manual entry requires campaign selection before code entry.

Exact registration, authentication, deeplink, QR-token, and technical return contracts remain owned by their applicable journey, privacy, security, and technical specifications.

Attributed-referee entries show the configured campaign, qualification progress, and a phone number with the middle half of digits masked; for an eight-digit Hong Kong number, use the MVP presentation `91****67`. They must not expose bills, rent, evidence, payment amounts, payment cards/profiles, KYC data, payee data, or internal risk reasons. Qualification display labels are `In Progress`, `Qualified`, `Not Qualified`, and `Under Review`, subject to the status-display reference matrix and future DOC-18 canonical mapping.

The masked referee phone belongs only to attributed-referee progress entries in `REFERRAL-ROOT`. It must not appear on a referral reward card, `REFERRAL-ENTITLEMENT-DETAIL`, `REFERRAL-REWARD-CLAIM`, or another reward screen.

##### `REFERRAL-REWARDS-LIST`

The list contains the current user's corresponding referrer and referee entitlements. It does not create a second issued-reward record or status family. The screen contains Back, title `Referral Rewards`, and two route-local tabs:

- `Available to Claim`: confirmed entitlements that the user may claim immediately;
- `History`: claimed or no-longer-claimable entitlements, including `Issued`, `Expired`, and `Reversed` presentations.

`Available to Claim` is ordered by earliest claim deadline; `History` is ordered by latest relevant lifecycle date. A tab with no items shows `No rewards available to claim` or `No reward history yet`; when neither tab has an item, show `No referral rewards yet` with a return action to `REFERRAL-ROOT`.

History records claim and issuance lifecycle only. Whether an issued coupon, voucher, or other reward has later been used remains owned by `REWARDS-ROOT` and `REWARD-DETAIL`.

A `REFERRAL-REWARD-CARD` is a screen component, not a route. It is an entry point to `REFERRAL-ENTITLEMENT-DETAIL` and displays reward name, benefit summary or amount, campaign name where useful, user-facing state, relevant claim/issuance/expiry/reversal date, and `View Details` or `View Reward` as applicable. It must not display referrer/referee identity, phone number, payment data, qualification transaction value, or internal review reason.

##### `REFERRAL-ENTITLEMENT-DETAIL`

The detail screen displays campaign name and identifier where useful, reward name, full reward description, benefit amount, current user-facing state, claim deadline where unclaimed, reward usage expiry as a separate date, user-facing eligibility and usage conditions, and the applicable `Claim Reward` or `View Reward` action. Internal terms-version identifiers remain hidden unless disclosure is required. No referrer/referee information appears on this screen.

##### `REFERRAL-REWARD-CLAIM`

The confirmation flow displays Close/Back, campaign name, reward name, full reward description, benefit amount, reward usage expiry, material usage conditions, `Claim Reward`, and Cancel. The claim deadline need not be repeated because entry is allowed only while the entitlement remains claimable.

Claim submission must prevent duplicate taps and present only transient progress, not a persistent user-facing `Processing` status. Success shows `Reward issued` with `View Reward`, which opens canonical `REWARD-DETAIL`, and `Done`, which returns to `REFERRAL-REWARDS-LIST` with `History` selected and the issued card visible. A repeated, concurrent, or uncertain claim must resolve to the existing result without issuing another reward.

##### Referral Reward Status Presentation

Normal user-facing labels are `Available to Claim`, `Issued`, `Expired`, and `Reversed`. `Under Review` is not a normal list tab or claim-processing state. If a DOC-13 or other applicable formal-owner outcome requires an already-claimed entitlement or issued reward to be held, the item remains in `History`, becomes visually inactive, and may display `Under Review` until resolved; DOC-22 may execute only the owner-permitted handling. Internal processing and review reasons must not be exposed.

#### 5.16.6 Placement, Control, and Data Boundaries

DOC-13 owns campaign, offer, qualification, entitlement, benefit, instrument, redemption, stacking, budget, quota, reversal, and fulfilment logic. DOC-06B owns only the route presentation and handoffs defined here.

DOC-22 should later define only the permitted execution controls for owner-approved Offer placement, priority, scheduling, targeting, enable/disable, Category/label filters and exception handling; DOC-13 and the applicable product/commercial owners retain Offer approval and business truth. Dashboard What's New administration remains a separate placement concern. DOC-15 owns consent, permitted personalization, masking, and partner-data boundaries. Sensitive evidence-derived data must not be used for offer targeting unless expressly approved under DOC-15.

Material route-level signals for later DOC-18 specification include offer impression, search/filter use, offer open, claim attempt/result, reward open, use action, checkout handoff, referral handoff, referral share action, registration attribution, qualification outcome, entitlement availability, referral claim/issuance result, external fulfilment handoff, and return outcome. A share action is not proof of delivery or recipient identity. DOC-18 owns final event IDs, schema, lineage, analytics, and model-use metadata.

#### 5.16.7 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Final My Rewards icon | Product / Design | Open; user-facing label confirmed |
| Final Offer label taxonomy and launch visibility for Pay+ Offers and Partner Offers; this does not change the settled Pay+ action composition | Product / Growth / Design | Open |
| Final offer/reward card styling, density, and empty-state copy | Product / Design | Open |
| Final personalized ranking and targeting scope | Product / Growth / Privacy | Open |
| Final membership-program route destination | Product / Growth | Open |
| Final launch partner activation, credential, fulfilment, and reconciliation method for each external reward | Product / Commercial / Operations / Engineering | Open; launch capability confirmed |
| Final referral campaign reward values, qualification conditions, payment/risk finality, technical deeplink/QR format, and multi-campaign visual design | Product / Growth / Risk / Design / Engineering | Open; owner-approved, Admin-executable configuration baseline defined |

### 5.17 Me Route

#### 5.17.1 Route Definition

`ME-ROOT` is the permanent Payer-only Consumer User account and control destination opened by the bottom-navigation `Me` button. It must remain present for MVP and must not be hidden, disabled, or replaced by `More`.

| Field | Definition |
| --- | --- |
| Route ID | `ME-ROOT` |
| Type | Top-level root route |
| Role | Payer-only Consumer User |
| Purpose | Let users view account information and reach account controls, records, settings, preferences, support, and established feature routes. |
| Primary owner | DOC-06B |
| Boundary | `ME-ROOT` is not a dashboard, inbox, payment/checkout route, wallet, balance screen, or owner of the feature behavior it links to. |

The route uses a vertically grouped settings-style list. It does not use payer/payee tabs, a role switch, a duplicate dashboard shortcut grid, or user-reorderable sections.

#### 5.17.2 Screen Order

The MVP screen order is:

1. **Header** - title `Me`; no Back button when opened through bottom navigation.
2. **Action Required** - compact banner for account, identity-verification, or security issues only; hidden when empty.
3. **Account Information** - masked account summary; opens `ACCOUNT-PROFILE`.
4. **Security & Privacy** - `Login & Security` opens `ACCOUNT-SECURITY`; `Privacy & Data` opens `PRIVACY-DATA-CONTROLS`.
5. **Bills & Tenancies** - opens `BILLS-ROOT` without moving Bills ownership into Me.
6. **Payments & Records** - Payment Profile, Activity, Receipts & Statements, and Archived Records. Archived Records opens the active Payer-only `ARCHIVED-ROOT`; `ARCHIVED-DOCS-LIST` is not an active user-facing row or entry. Retired Receiving Info identifiers remain non-active documentation lineage only.
7. **Rewards & Programs** - `My Rewards` opens `REWARDS-ROOT`; Membership remains hidden until its destination and launch behavior are defined and enabled.
8. **Referral Program** - opens `REFERRAL-ROOT` as a separate program area.
9. **Preferences & Settings** - Notification Settings, Language, and Theme.
10. **Help & Support** - opens `SUPPORT-ROOT`.
11. **About PayPlus** - About opens `ABOUT-ROOT`; Terms and Policies opens `TERMS-ROOT`.
12. **Log Out** - final button at the bottom of the screen.

Exact typography, spacing, icons, row density, banners, sheets, and visual design remain open.

#### 5.17.3 Destination Register and Transitions

The following register defines the new or newly confirmed Me destinations. Established destinations such as `BILLS-ROOT`, `PAYMENT-PROFILE-ROOT`, `ACTIVITY-ROOT`, `RECEIPTS-ROOT`, `REWARDS-ROOT`, and `REFERRAL-ROOT` retain their existing route ownership and definitions.

| Destination | Parent / Entry Context | Type | Purpose | Primary Route Owner | Definition Status |
| --- | --- | --- | --- | --- | --- |
| `ME-ROOT` | Bottom navigation | Root route | Permanent Payer account, records, settings, preferences, and support entry. | DOC-06B | Route shell defined; visual design pending |
| `ACCOUNT-PROFILE` | `ME-ROOT` Account Information | Child route | View permitted account/profile information, identity-verification status, controlled contact changes, and account closure. | DOC-06B | Route behavior defined; final visual design pending |
| `PHONE-VERIFICATION` | `ACCOUNT-PROFILE` | Reusable controlled flow | Verify or replace the account's primary phone number; Account Activation may invoke initial verification contextually. | DOC-06B | Defined behavior baseline; technical security constants pending |
| `IDENTITY-VERIFICATION` | `ACCOUNT-PROFILE` | Reusable controlled flow | Complete first-time verification, resume processing, retry after failure, or respond to an identity/security-owner-required update executed through a permitted Admin workflow; Account Activation may invoke the same flow contextually. | DOC-06B | Defined behavior baseline; provider mapping pending |
| `ACCOUNT-SECURITY` | `ME-ROOT` Security & Privacy | Child route | Manage enabled login methods, password setup/change, payment-passcode entry, permitted two-step verification, biometric unlock, trusted devices, and recovery/support entry. | DOC-06B | Route behavior defined; final visual design pending |
| `PAYMENT-PASSCODE-SETTINGS` | `ACCOUNT-SECURITY` Payment Passcode | Reusable child flow | Set, change, or reset the payment passcode and manage the optional passcode-confirmation preference for card/payment-profile changes; Account Activation may invoke Set contextually. | DOC-06B | Defined behavior baseline; technical security controls pending |
| `PRIVACY-DATA-CONTROLS` | `ME-ROOT` Security & Privacy | Child route | Manage approved privacy choices, access/export, correction, privacy requests, and request history without changing indefinite record retention. | DOC-06B | Route behavior defined; legal/provider detail pending |
| `RECEIVING-INFO` and child identifiers | Non-active documentation lineage | Retired stable identifiers only | Preserve prior actor-role meaning in append-only documentation history; no Consumer Payee profile library, runtime reader, add/edit flow or Request-context entry is defined. | DOC-06B | Retired active behavior |
| `ARCHIVED-ROOT` | `ME-ROOT` Payments & Records / Archived Records | Child root route | Active Payer-only Archive parent for Saved/Archived source projections; route access is retained while final visual design and detailed future Archive/Restore behavior remain deferred. | DOC-06B | Active Payer-only route baseline; final visual design open |
| `ARCHIVED-BILLS-LIST` | `ARCHIVED-ROOT` Archived Bills &amp; Rent | Child route | Active Payer-visible list of the Archived projection of previously Saved/current Bill/Rent sources; detailed Bills/Rent contents and UX remain with DOC-06C. | DOC-06C | Active route and accessibility retained; detailed UX owned by DOC-06C |
| `ARCHIVED-DOCS-LIST` | `ARCHIVED-ROOT` | Provisional child route identity | Stable route identity for a possible archived-document projection; exact contents, presentation and interaction remain deferred to DOC-06B/DOC-06C with DOC-10 payout/reconciliation blockers, DOC-11 refund/dispute/chargeback/case blockers and DOC-12/DOC-15/DOC-18 Evidence, privacy/retention and data/lineage handoffs. | DOC-06B | Provisional identity only; behavior deferred |
| `NOTIFICATION-SETTINGS` | `NOTIFICATION-ROOT`; direct entry from `ME-ROOT` Preferences & Settings | Child route | Manage permitted notification-channel and communication preferences. | DOC-06B / DOC-08 | Defined baseline; final visual design pending |
| `SUPPORT-ROOT` | `ME-ROOT` Help & Support | Root route | Enter the user support area. | DOC-06B | Purpose defined; detailed UI pending |
| `ABOUT-ROOT` | `ME-ROOT` About PayPlus | Root route | View PayPlus and app information. | DOC-06B | Purpose defined; content and detailed UI pending |
| `TERMS-ROOT` | `ME-ROOT` About PayPlus | Root route | View applicable terms, policies, and legal documents. | DOC-06B | Purpose defined; content and detailed UI pending |

Domain rules and content remain with the reference owners named in Sections 5.17.4 to 5.17.7; this register does not transfer those responsibilities to DOC-06B.

| Source | User action | Destination / behavior | Return behavior |
| --- | --- | --- | --- |
| Bottom navigation | Tap `Me` | `ME-ROOT` | Normal bottom-navigation behavior. |
| Account Information | Tap summary or row | `ACCOUNT-PROFILE` | Return with the masked summary refreshed and prior Me position preserved. |
| `ACCOUNT-PROFILE` | Tap phone-verification action | `PHONE-VERIFICATION` | Back or Cancel restores Account Information; completion returns with refreshed phone-verification status. |
| `ACCOUNT-PROFILE` | Tap the applicable identity action: Verify/Continue, View Status, Verify Again, Get Help, or Update Verification | `IDENTITY-VERIFICATION` or controlled Support where applicable | Back or Cancel restores Account Information; completion or provider result returns with refreshed verification status. |
| Security & Privacy | Tap `Login & Security` | `ACCOUNT-SECURITY` | Return to the same Me position. |
| `ACCOUNT-SECURITY` | Set or change password, or link or unlink Google/Apple | Complete the route-local credential/provider flow | Success returns with login-method state refreshed; Cancel preserves the prior configuration. |
| `ACCOUNT-SECURITY` | Tap `Payment Passcode` | `PAYMENT-PASSCODE-SETTINGS` | Return with the security summary and preference refreshed. |
| `ACCOUNT-SECURITY` | Change phone or email used by a security factor | `ACCOUNT-PROFILE` | Complete the controlled contact-change flow, then return to Login & Security. |
| Security & Privacy | Tap `Privacy & Data` | `PRIVACY-DATA-CONTROLS` | Return to the same Me position. |
| `PRIVACY-DATA-CONTROLS` | Correct a directly editable account field or open account closure | `ACCOUNT-PROFILE` | Return to the relevant Privacy & Data context after the account action. |
| `PRIVACY-DATA-CONTROLS` | Change notification channels | `NOTIFICATION-SETTINGS` | Return with the channel-preference summary refreshed. |
| Bills & Tenancies | Tap row | `BILLS-ROOT` | Return to the same Me position; Bills retains its own route state. |
| Payments & Records | Tap Payment Profile | `PAYMENT-PROFILE-ROOT` | Return with refreshed card/profile data and prior Me position preserved. |
| Payments & Records | Tap Activity | `ACTIVITY-ROOT` | Return with the prior Me position preserved. |
| Payments & Records | Tap Receipts & Statements | `RECEIPTS-ROOT` | Return with the prior Me position preserved. |
| Payments & Records | Tap Archived Records | `ARCHIVED-ROOT` | Back returns to the prior Payments & Records position in `ME-ROOT`. |
| `ARCHIVED-ROOT` | Tap Archived Bills &amp; Rent | `ARCHIVED-BILLS-LIST` | Back returns to the prior `ARCHIVED-ROOT` position. |
| `ARCHIVED-ROOT` | `ARCHIVED-DOCS-LIST` | Provisional child identity relationship only; exact archived-document contents, presentation and interaction remain deferred. | No user-facing action or return contract is defined here. |
| Rewards & Programs | Tap My Rewards | `REWARDS-ROOT` | Return with prior Rewards state and Me origin preserved. |
| Referral Program | Tap row | `REFERRAL-ROOT` | Return with prior Referral state and Me origin preserved. |
| Preferences & Settings | Tap Notification Settings | `NOTIFICATION-SETTINGS` | Return with updated preference summaries. |
| Preferences & Settings | Tap Language or Theme | Open route-local selection sheet/modal | Apply or cancel without creating another root route. |
| Help & Support | Tap row | `SUPPORT-ROOT` | Return to the same Me position. |
| About PayPlus | Tap About | `ABOUT-ROOT` | Return to the same Me position. |
| About PayPlus | Tap Terms and Policies | `TERMS-ROOT` | Return to the same Me position. |
| Log Out | Tap and confirm | End the current session and return to `ENTRANCE-ROOT` | Protected route history must not remain accessible after logout. |

Dashboard shortcuts and `ME-ROOT` may both link to an established route. The shortcut is a fast entry point; Me provides permanent account-level discoverability. The destination owner continues to govern its behavior.

#### 5.17.4 Account Information, Security, and Privacy

##### 5.17.4.1 Shared Child-Route Rules

- `ACCOUNT-PROFILE`, `ACCOUNT-SECURITY`, and `PRIVACY-DATA-CONTROLS` are Payer account routes; they do not use payer/payee tabs.
- Normal authenticated entry shows only permitted masked information and does not require payment-passcode entry merely to open a route.
- Revealing approved masked sensitive values in a permitted current account context requires the existing PayPlus payment passcode or approved reauthentication. DOC-14 owns risk triggers/actions, DOC-15 privacy conditions, and provider owners applicable partner conditions; DOC-19 enforces the resulting security assurance requirement without deciding the trigger or outcome.
- Changing existing sensitive identity, contact, security or credential information requires payment passcode or approved reauthentication before the route-specific OTP, provider, review, or confirmation steps. Payer-entered destination facts are changed only through the applicable Bill/Rent journey and owner controls. First-time identity verification invoked during `ACCOUNT-ACTIVATION` does not require a payment passcode that the user may not yet have created.
- Ordinary evidence, invoice, receipt, statement, and payment-proof viewing or downloading within an authenticated permitted context does not require an extra passcode or step-up solely because the document is opened or downloaded.
- Payment-passcode confirmation does not make every stored field revealable. Passwords, payment passcodes, identity documents, provider payloads, secrets, raw credentials, evidence content, unrestricted audit data, and internal risk reasons remain unavailable.
- Revealed information must re-mask on route exit, app backgrounding, session expiry, or the future configured reveal timeout.
- Offline or stale-session mode may show approved cached masked information but must block reveal, export, profile/security changes, recovery changes, privacy-request submission, and account closure.
- A dependent-service failure affects only the relevant section, preserves the last valid state, and provides Retry or clear unavailable behavior.
- Material reveal, change, recovery, device, preference, privacy-request, export, and closure outcomes require audit events without sensitive values in ordinary analytics.

##### 5.17.4.2 `ACCOUNT-PROFILE` - Account Information

The user-facing title is `Account Information`. The MVP screen order is:

1. Header with Back;
2. account Action Required banner, hidden when empty;
3. Profile Details;
4. Contact Details;
5. Identity Verification;
6. Account Management, with `Close Account` at the bottom.

Profile Details show the editable nickname/display name and copyable PayPlus User ID. The nickname/display name is not a login identifier. Contact Details show masked registered phone and email plus their verification states.

Contact changes follow these MVP flows:

- changing phone first requires payment passcode or approved reauthentication, then OTP confirmation through the registered email, followed by SMS OTP verification of the new phone;
- changing email first requires payment passcode or approved reauthentication, then SMS OTP confirmation through the registered phone, followed by OTP or approved deeplink verification of the new email;
- successful change notifies the old and new contact channels where available;
- when trusted channels are unavailable, the user must enter approved support-assisted identity recovery rather than bypass verification.

###### `PHONE-VERIFICATION`

The flow is reusable from Account Information and Account Activation. Its modes are initial verification, replacement of an existing verified phone, resumption of an unexpired OTP attempt, and retry after expiry, delivery failure, or interruption. Hong Kong `+852` phone numbers are the only launch-supported numbers.

| Screen | Required elements | Behavior |
| --- | --- | --- |
| Phone entry | Back, title, reason for collection, `+852`, phone input, Continue, Cancel | Validate the supported format and uniqueness without identifying another account holder. |
| OTP verification | Masked number, OTP input, Verify, Resend, countdown, Change Number | Resend invalidates the prior OTP but does not reset abuse counters. |
| Completion | Verified masked number, confirmation, Continue or Done | Return to the invoking parent with refreshed status. |
| Failure | Safe explanation and applicable Retry, Resend, Change Number, or Support action | Use the DOC-07 outcome/message mapping and preserve the last authoritative account state. |

Initial verification requires an authenticated restricted account and SMS OTP but no existing payment passcode. Device token, push token, device attestation, or biometric capability may support abuse detection but does not prove phone possession. One verified phone may belong to only one active individual account; conflict copy may say the number is already occupied but must not identify who uses it.

For phone replacement, the old phone remains authoritative until the full sequence succeeds: payment passcode or approved reauthentication, OTP through the registered email, then SMS OTP to the new phone. Cancelling leaves the old phone unchanged. `ACCOUNT-PROFILE` shows only `Verified` or `Not Verified`; `Code Sent`, `Expired`, `Incorrect Code`, and `Delivery Failed` are route outcomes, not persistent account statuses. OTP length, validity, resend interval, attempt limits, cooldown, and technical anti-automation mechanisms remain open under `OQ-19-001`; DOC-14 retains risk/abuse trigger and outcome ownership and DOC-17 any provider-delivery contract.

###### `IDENTITY-VERIFICATION`

The flow supports first-time verification, resuming incomplete provider capture, provider processing, retry after `Failed`, an identity/security-owner-required `Update Required` response executed through a permitted Admin workflow, and read-only status confirmation when `Verified`.

| Screen | Required elements | Behavior |
| --- | --- | --- |
| Status and introduction | Back, title, current approved status, purpose, provider disclosure, privacy link, preparation requirements | Present only approved user-facing status and safe guidance. |
| Review and consent | Information categories, provider handoff explanation, consent or acknowledgement | Record required consent/acknowledgement before external capture. |
| Provider handoff | The selected identity-verification provider's approved or equivalent capture flow, with provider selection subject to the applicable formal owner | Preserve origin, attempt, and correlation references without copying raw provider payload into route analytics. |
| Processing return | `Processing`, safe Close, View Status | Returning from the provider means submitted/processing, not successful verification; prevent duplicate submission. |
| Result | Approved status, safe explanation, applicable action | Use the mapping below and return to the invoking parent with refreshed state. |

| User-facing status | System meaning | User action |
| --- | --- | --- |
| `Not Verified` | Verification has not started, capture is incomplete, or an identity/security-owner-permitted Admin workflow executed the reset. | `Verify Now` or `Continue Verification`. |
| `Processing` | Submission was acquired and the authoritative provider result or PayPlus policy decision is pending. | `View Status`; no duplicate submission. |
| `Verified` | Authoritative provider result and PayPlus policy checks passed. | No verification action. |
| `Failed` | Provider verification or a PayPlus policy check failed, including duplicate identity. | `Verify Again` and `Get Help`, subject to retry controls. |
| `Update Required` | An applicable identity/security-owner outcome, executed through a permitted Admin review workflow, requires updated information. | `Update Verification`. |

First-time verification from Account Activation requires an authenticated restricted account but no pre-existing payment passcode. Returning from the provider does not prove success: an authoritative callback or retrieval plus PayPlus policy checks sets the final state. A duplicate identity fails PayPlus policy even if it is not a provider failure; safe copy may state that the identity is registered with another PayPlus account without exposing account details.

Once `Verified`, a user cannot voluntarily correct or repeat identity verification. Where the applicable identity/security owner permits it, an authorized administrator may execute a transition to `Not Verified` or `Update Required` through DOC-22 controls but cannot directly set `Verified`; `Verified` to `Not Verified` requires the existing dual-approval control for MVP. An owner-required update may require payment passcode or approved reauthentication before new provider capture.

While processing, Home shows a dismissible banner below the header with `View Status`. A successful result shows a dismissible completion banner. `Failed` or `Update Required` shows an Action Required banner. Dismissal changes presentation only, not the underlying state or activation gate. Exact provider-result-to-PayPlus mapping remains TBC until provider selection and belongs to DOC-17 integration, DOC-18 status/data representation and DOC-19 security ownership; DOC-22 executes only any permitted Admin handling. Account Information never shows legal name, ID reference, identity attributes, identity documents, provider payloads, or internal risk reasons.

Account closure remains a controlled Account Information flow, not a Privacy & Data action and not record destruction. It must:

1. explain the loss of future payment and account activity and continuing record-retention duties;
2. check unresolved instructions, payments, payouts, refunds, disputes, chargebacks, investigations, reviews, and legal/compliance holds;
3. require payment passcode plus 2FA;
4. create an account-closure submission and confirmation record;
5. allow cancellation until operational finalization begins;
6. on completion, block new activity, terminate active sessions, notify verified channels, disable login, and retain required records.

Detailed account-closure screen layout remains open. Before final closure, the user should be prompted to obtain available records; later access follows controlled Support or privacy-request handling.

##### 5.17.4.3 `ACCOUNT-SECURITY` - Login & Security

The user-facing title is `Login & Security`. The MVP screen order is:

1. Login Methods, containing PayPlus Password, Google, and Apple;
2. Payment Passcode;
3. Two-Step Verification toggle;
4. Biometric Unlock toggle;
5. Trusted Devices;
6. Recovery and Security Support.

Login Methods follows these rules:

- PayPlus Password shows `Set Password` when the account has no local password and `Change Password` after one is set;
- Google and Apple each show `Link` or `Unlink` according to the current account linkage;
- the account's verified primary email remains unique and is not itself permission to link a provider;
- provider linking requires fresh approved reauthentication, successful authentication by that provider, explicit confirmation, audit, and security notification;
- provider unlinking requires fresh approved reauthentication and confirmation, and must be blocked if it would remove the account's final usable login method;
- a provider identity already linked to another PayPlus account cannot be reassigned through this route;
- matching Google/Apple and PayPlus email addresses never cause silent account creation, merging, or linking.

No separate MVP root is created for login-method management. Set/Change Password and provider Link/Unlink are focused flows under `ACCOUNT-SECURITY`. Exact provider integration remains with DOC-17; DOC-06B retains account-recovery route behavior; exact security mechanisms and retry limits remain open under `OQ-19-001`; final screen design remains separate design work.

Tapping Payment Passcode opens `PAYMENT-PASSCODE-SETTINGS`. Account Activation opens Set mode. Account Security opens the settings overview and shows Set when absent or Change, Reset, and the permitted card/payment-profile confirmation preference when a passcode exists.

| Mode | Screen sequence and required behavior |
| --- | --- |
| Set | Introduction; enter a six-digit passcode; enter the same passcode again; enable Confirm only when both entries are complete and match; show success and return. |
| Change | Verify the current passcode or complete approved fresh reauthentication; enter the new six-digit passcode twice; confirm; show success and return. |
| Reset | Select Forgot Passcode; complete fresh login reauthentication through password, linked Google, or linked Apple; verify an OTP sent to the registered verified Hong Kong phone; enter the new six-digit passcode twice; confirm; invalidate sensitive pending authorization state; notify available verified channels; return. |

The passcode is a masked six-digit numeric secret. Entries clear when the app backgrounds, the session expires, or the route closes. A mismatch saves neither entry. Cancel Set leaves activation incomplete; Cancel Change or Reset preserves the current passcode. Existing passcodes are never displayed or recoverable. Unknown save results must be reconciled before another attempt.

Email OTP alone is insufficient to reset a payment-authorizing passcode. If the registered phone is unavailable, the user enters controlled support-assisted recovery. DOC-06B owns the recovery route/capability; exact proof, factors, waiting-period, and security mechanisms remain open with the applicable Product/Security/Operations owners and `OQ-19-001`/`OQ-19-005`; DOC-19 enforces approved security conditions, DOC-21 owns support/operations, DOC-15 owns approved-purpose privacy/access requirements, and DOC-22 executes only the permitted Support/Admin workflow under those owner decisions. An administrator cannot read, select, retrieve or reset a user's passcode.

The card/payment-profile passcode preference defaults to ordinary confirmation. Enabling it may use ordinary confirmation; disabling it requires the current passcode or approved reauthentication. Setting a passcode does not authorize payment. DOC-09 still requires a fresh payment passcode before payment authorization. Successful Change and Reset generate mandatory security notifications under DOC-08. Weak-code rules, retries, lockout, hashing, storage, recovery factors, and session-revocation mechanisms remain open under `OQ-19-001` with Security/Engineering and applicable provider contracts under DOC-17.

The Two-Step Verification toggle controls only permitted optional routine protection. It must not disable mandatory new-device 2FA, risk-triggered step-up, contact-change verification, account-closure verification, or provider-required authentication. SMS remains the MVP primary factor and email the fallback.

Biometric Unlock applies to the current device only, must be enabled by the user, and does not replace payment passcode or mandatory step-up. Where Fast Login is eligible, the operating-system biometric prompt may be presented automatically under Section 5.0.2. Each Trusted Devices entry provides `Remove`: removing another device revokes its trust and associated session; removing the current device requires confirmation and logs the user out. No separate Active Sessions list is required for MVP.

Recovery must not provide an unverified bypass. Forgotten password/passcode, unavailable trusted channels, or suspected compromise routes to the approved recovery or Support process. DOC-19 defines the mechanism-neutral enforcement contract; exact retry limits, lockout periods, recovery factors, session duration, and implementation mechanisms remain open under `OQ-19-001` with Security/Engineering.

##### 5.17.4.4 `PRIVACY-DATA-CONTROLS` - Privacy & Data

The user-facing title is `Privacy & Data`. The MVP screen order is:

1. Privacy Overview and notices;
2. Optional Data-Use Choices;
3. Request My Data;
4. Correct My Data;
5. Retention and Record Handling;
6. Privacy-Request History;
7. contextual link to account closure in `ACCOUNT-PROFILE`.

Only genuine optional choices may use toggles. Launch-capable categories are direct marketing, personalization, and approved partner-data use, subject to final legal/privacy wording and enablement. Required account, service, payment, security, risk, fraud, compliance, tax, audit, dispute, and retention processing is explained but is not disableable.

Notification-channel selection remains in `NOTIFICATION-SETTINGS`; Privacy & Data owns the underlying consent or approved-purpose choice. Directly editable profile fields hand off to `ACCOUNT-PROFILE`. Correction of KYC, verified, historical, payment, payout, or Evidence data creates a governed correction request and preserves the original audit record. A verified identity may reopen `IDENTITY-VERIFICATION` only after an applicable identity/security-owner outcome permits an authorized Admin to execute `Update Required` or `Not Verified`; the user cannot initiate voluntary re-verification.

Privacy-request history is a route-local section, not another route. User-facing request labels are `Submitted`, `In Progress`, `Action Required`, `Completed`, and `Unable to Complete`; internal states and service timelines remain TBC. Completed exports use authenticated, time-limited in-app download after reauthentication and must not be attached to ordinary email. Privacy requests and account closure remain separate processes, and neither destroys an underlying PayPlus record.

#### 5.17.5 Payments, Historical Receiving Info, and Archived Records

Consumer Receiving Info is retired from active MVP. Payer-entered destination facts remain inside the controlled Bill/Rent journey under DOC-10, DOC-12, DOC-14 and DOC-15. `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST` remain active Payer-only routes for Saved/Archived source projections; `ARCHIVED-DOCS-LIST` remains provisionally retained under the Founder-approved W2-FD-05 Option A decision with no active entry or interaction contract. Exact Restore, prior-version and Evidence-version contents and presentation remain deferred to DOC-06B/DOC-06C with DOC-10/DOC-11 blockers and DOC-12/DOC-15/DOC-18 handoffs.

`ACTIVITY-ROOT` remains the account-level Payer financial activity route. No separate receiving-activity route is active.

#### 5.17.6 Non-Active Documentation Register - Retired Receiving and Archive IDs

| Retained identifier or record | Preservation location | Current treatment |
| --- | --- | --- |
| RECEIVING-INFO identifiers and retired mixed-role archive/document identifiers | Append-only documentation history and retired stable IDs only | No active Consumer Payee or Payer destination-library route or runtime reader; ARCHIVED-DOCS-LIST remains provisional under W2-FD-05 Option A while detailed Restore/prior-version/Evidence-version presentation is deferred |
| Prior archive/document meanings | Append-only documentation history only | Does not define Restore, revalidation, version presentation, route, UI or replacement behavior |



#### 5.17.7 Visibility, State, and Return Rules

- `ME-ROOT` itself has no global empty state because core account controls always exist.
- The MVP section order is fixed and is not user-reorderable.
- Core Account Information, Security & Privacy, Help & Support, About PayPlus, Terms and Policies, and Log Out access must not be hidden by ordinary admin placement controls.
- Optional rows may follow module enablement, launch phase, account restriction, and retained-record requirements. The active `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST` route chain remains accessible from Payments & Records; the provisional `ARCHIVED-DOCS-LIST` identity alone does not authorize user-facing access behavior. Any permitted read-only treatment for other retained records remains subject to the applicable owner and deferred scope.
- The Action Required banner must not duplicate bill, payment, reward, or evidence-specific task lists. It is limited to account, identity-verification or security issues and must not expose internal risk reasons.
- A dependent-service failure should affect only the relevant row or child route and should provide retry or clear unavailable behavior; it must not blank `ME-ROOT`.
- Restricted accounts should retain access to security, privacy, permitted records, terms, and support where legally and operationally allowed.
- Offline behavior may show approved cached masked summaries but must block sensitive reveal, export, material changes, or other actions requiring current validation.
- Child routes opened from Me return to Me with position preserved. The same routes opened from checkout, Instructions, notification, deeplink, or another contextual flow return to that originating context instead.

`More` remains separate from Me. Me governs account information, records, settings, preferences, and support. More governs dashboard shortcut management, reorder/arrangement, restore-default behavior, approved secondary-service entry, and protected access to shortcut management. Detailed behavior is defined in Section 5.18.

#### 5.17.8 Notification, Data, and Admin Handoffs

`NOTIFICATION-SETTINGS` manages permitted channel and communication preferences under DOC-08 and is a child of `NOTIFICATION-ROOT`. `ME-ROOT` is a direct entry point to Settings; it does not change route ownership. Settings is not the Inbox and must not allow mandatory service, security, payment, receipt, risk, compliance, or legal messages to be universally disabled.

Material route-level signals for later DOC-18 specification include Me opened, destination selected, account-action item opened, sensitive reveal attempted/completed/failed, preference changed, proof submitted, profile status changed, destination selected for a Bill/Rent or Payment context, and logout completed. These signals must not copy sensitive values into analytics events. DOC-18 owns final event IDs, schema, lineage, audit classification, and model-use metadata; the provisional `ARCHIVED-DOCS-LIST` identity does not imply an access signal.

DOC-22 may execute only DOC-06B-owner-approved optional module visibility configuration and must not hide `ME-ROOT` or the core account, security, privacy, support, legal and logout controls. Exact permitted Admin execution workflow remains deferred to DOC-22; route availability policy remains with DOC-06B and applicable specialist owners.

#### 5.17.9 Open Items

| Item | Owner | Status |
| --- | --- | --- |
| Final visual design for Account Information, Login & Security, Privacy & Data, the active Archived Records and Archived Bills &amp; Rent routes, any later-authorized archived-document presentation, Support, About, and Terms | Product / Design / Privacy / Security / Operations | Open; active Archive root/list access is retained, while detailed Restore and version presentation and all `ARCHIVED-DOCS-LIST` behavior remain deferred to DOC-06B/DOC-06C with DOC-10/DOC-11 blockers and DOC-12/DOC-15/DOC-18 handoffs |
| External provider results and PayPlus policy outcomes mapped to `Not Verified`, `Processing`, `Verified`, `Failed`, and `Update Required` | Product / Compliance / Security / Data | Open pending provider selection; five user-facing labels confirmed |
| Final privacy-request internal states, service timelines, export format/expiry, and legal wording | Privacy / Legal / Operations / Security | Open; route labels and protected delivery confirmed |
| Final authentication retry, lockout, session, recovery-factor, and reveal-timeout mechanisms | Security / Engineering / Risk | Open under `OQ-19-001`; DOC-19 supplies the security-control contract without selecting values |
| Any future destination-profile requirements, external validation capability, identity-name normalization, third-party/company proof requirements, risk-based step-up rules, and review SLA | Payments / Operations / Privacy / Security | Open; no active Consumer Payee destination library is defined in Wave 2 |
| Final visual styling, density, and copy for active `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST`, and any later-authorized presentation for provisional `ARCHIVED-DOCS-LIST` | DOC-06B/DOC-06C; DOC-10/DOC-11 blockers; DOC-12/DOC-15/DOC-18 handoffs | Open; active root/list route behavior and ordinary parent return are retained, while detailed Archive/Restore, prior-version and Evidence-version behavior and all `ARCHIVED-DOCS-LIST` interaction remain deferred |
| Final language options, theme options, selection controls, and accessibility behavior | Product / Design / Engineering | Open |
| Final support, About PayPlus, terms, policies, and app-version content | Product / Support / Legal / Design | Open |
| Final Membership route and launch behavior | Product / Growth | Open; hidden until defined and enabled |
| Final visual styling, icons, density, action copy, and confirmation copy | Product / Design | Open |

### 5.18 More Route

#### 5.18.1 Route Definition and Boundary

| Item | Requirement |
| --- | --- |
| Route label | More |
| Product destination | `MORE-ROOT` |
| Purpose | Manage Home shortcuts and open approved secondary services or route entries that are not currently shown on Home. |
| Entry point | Protected `More` shortcut on `HOME-ROOT`. |
| Structure | One root route with Normal and Manage Shortcuts modes. Manage mode is not a separate route. |
| Boundary | More is an entry and preference-management surface. It does not own the destination features, replace `ME-ROOT`, or change route permissions, eligibility, or business rules. |

`Home Shortcuts` and `Other Shortcuts & Services` are dynamic sections within `MORE-ROOT`, not child routes or permanent destination categories. Entries may move between these sections as Home placement changes, while every opened destination remains owned by its governing route family.

The Home default and maximum capacity is 8 shortcuts: up to 7 configurable shortcuts plus protected `More`. A user may keep fewer than 7 configurable shortcuts. `More` must remain visible as the final Home shortcut and cannot be removed, displaced, disabled, or reordered by the user.

| Source | User action | Destination / result | Return behavior |
| --- | --- | --- | --- |
| `HOME-ROOT` | Tap protected `More` | Open `MORE-ROOT` in Normal mode. | Back returns to Home with prior context preserved. |
| `MORE-ROOT` Normal mode | Tap `Edit` | Enter Manage Shortcuts mode in the same route. | Save or discard returns to Normal mode. |
| `MORE-ROOT` Normal mode | Tap an approved entry | Open the entry's owning destination. | Back returns to More with prior scroll/search context where practical. |
| Manage Shortcuts mode | Tap `Save` | Apply the effective account-level shortcut preference and return to Normal mode. | A later Back returns to Home, where the refreshed shortcut grid is visible. |
| Manage Shortcuts mode | Tap `Restore Default` | Load the current eligible owner-approved default into the editable arrangement. | The restored arrangement is not applied until `Save`. |

#### 5.18.2 Normal Mode

The screen order is:

1. header with Back, title `More`, and Search;
2. `Home Shortcuts` section showing the user's current configurable Home shortcuts, with an `Edit` action;
3. `Other Shortcuts & Services` section listing approved route entries not currently shown on Home and approved secondary services.

Search should find approved entries by user-facing label or approved keyword without changing Home preferences. Tapping an entry opens its owning route. The default Other list excludes entries already on Home; if search returns one, it should be identified as `On Home` rather than presented as another addable object.

Initial approved secondary-service entries may include Activity, My Rewards, and Support where enabled. Their owning routes remain authoritative. Archive remains accessible through Me / Payments & Records and no Archive shortcut is added to More; `ARCHIVED-DOCS-LIST` is not an approved secondary-service entry. Retired Receiving Info identifiers remain non-active documentation lineage only.

#### 5.18.3 Manage Shortcuts Mode

Tapping `Edit` changes the screen to shortcut-management mode:

1. header with Back, title `Home Shortcuts`, and `Save`;
2. current configurable shortcuts with a corner remove control and drag-and-drop reordering;
3. other approved entries, with dashboard-eligible entries available to add;
4. `Restore Default` at the bottom.

Users may:

- remove a configurable shortcut from Home;
- reorder configurable shortcuts;
- add an eligible shortcut by dragging it into `Home Shortcuts`;
- use accessible `Add`, `Remove`, `Move Up`, and `Move Down` controls instead of drag-and-drop;
- save fewer than 7 configurable shortcuts;
- restore the current eligible owner-approved default.

If all 7 configurable positions are occupied and the user adds another shortcut, the last configurable shortcut returns to `Other Shortcuts & Services`. Protected `More` is never displaced. Exact replacement animation and an optional post-replacement Undo remain open visual/product decisions.

An entry that is visible in More but unavailable for Home must not appear actionable merely through reduced opacity. It should also show a clear unavailable or locked indicator and must not be draggable or addable.

#### 5.18.4 Save, Restore, and Return Behavior

- Changes take effect only after `Save`.
- Back with no unsaved changes returns to the prior context.
- Back with unsaved changes prompts `Save Changes`, `Discard Changes`, or `Continue Editing`.
- `Restore Default` loads the current owner-approved default after filtering for launched, enabled, account-eligible, and permitted entries. It does not load an obsolete historical default and remains pending until `Save`.
- Successful save returns to Normal mode, refreshes the Home shortcut grid, and keeps `More` as the final shortcut.
- Shortcut preferences are account-level and should follow the user across approved devices.
- Opening a destination from More and returning should restore the More scroll and search context where practical.
- A failed save or restore must preserve the unsaved arrangement and allow retry.

Routine shortcut preference changes require no payment passcode or notification. Authentication, feature access, risk, privacy, and route-specific controls still apply when the user opens the destination.

#### 5.18.5 Availability and Precedence

The effective shortcut set is resolved in this order:

1. protected PayPlus access and product-boundary rules;
2. launch, module, account, role, market, eligibility, risk, and compliance availability;
3. the owner-approved shortcut catalog;
4. the current eligible owner-approved default set and order;
5. the user's saved order and visibility preferences.

User preferences cannot expose a disabled, unlaunched, ineligible, or prohibited route. When a previously selected shortcut becomes unavailable, Home removes it from the effective set while preserving a privacy-safe preference reference where appropriate. More should explain unavailability without exposing internal risk or compliance logic.

#### 5.18.6 Data, Admin, and Acceptance Handoffs

Material privacy-safe signals for later DOC-18 specification include More opened, search used, manage mode entered, shortcut added/removed/reordered, save attempted/completed/failed, default restored, unavailable entry encountered, and destination opened. Events must not include sensitive destination data or internal risk reasons.

DOC-06B owns the approved shortcut catalog, current default and product availability rules for `More`. DOC-22 may execute only permitted configuration, versioning, rollback and audit under that policy; it does not set product policy. DOC-15 owns preference-data classification, approved-purpose use, and cross-device privacy. DOC-06D owns acceptance coverage. Exact layout measurements, iconography, animation, density, and styling remain open.

### 5.19 Notifications Route

#### 5.19.1 Route Structure and Boundary

| Destination / Element | Type | Purpose | Primary Owner |
| --- | --- | --- | --- |
| `NOTIFICATION-ROOT` | Parent route shell | Group Inbox, notification detail, and notification settings. A generic root entry opens Inbox by default. | DOC-06B / DOC-08 |
| `NOTIFICATION-INBOX` | Default child screen | Search, filter, read, and archive user-visible notification records. | DOC-06B / DOC-08 |
| `NOTIFICATION-DETAIL` | Child screen | Show one notification's permitted full content, mapped domain context, and current valid action. | DOC-06B / DOC-08 |
| `NOTIFICATION-SETTINGS` | Child screen | Manage permitted notification channels and communication preferences. | DOC-06B / DOC-08 |
| `NOTIFICATION-LIST` | Component | Render the ordered notification collection inside Inbox. | DOC-06B |
| `NOTIFICATION-CARD` | Component | Summarize one notification and open its detail. | DOC-06B |

Archived notifications are a filter/view within Inbox, not another route. A notification is a communication record, not a domain status, request, payment, reminder, dashboard task, or action-required state. Detailed event eligibility, IDs, channels, templates, consent, delivery, and retention belong to DOC-08.

#### 5.19.2 Entry, Handoff, and Return Rules

| Source | User Action | Destination | Return Behavior |
| --- | --- | --- | --- |
| `HOME-ROOT` header | Tap Inbox icon | `NOTIFICATION-INBOX` | Back returns to Home with prior context preserved. |
| `ME-ROOT` Preferences & Settings | Tap Notification Settings | `NOTIFICATION-SETTINGS` | Back returns to the prior Me position. |
| `NOTIFICATION-INBOX` | Tap Settings | `NOTIFICATION-SETTINGS` | Back returns to Inbox with search, filter, and scroll state preserved. |
| `NOTIFICATION-SETTINGS` | Tap Inbox | `NOTIFICATION-INBOX` | Back returns to Settings without creating repeated route-stack loops. |
| `NOTIFICATION-CARD` | Tap card | `NOTIFICATION-DETAIL` | Back returns to the originating Inbox state. |
| `NOTIFICATION-DETAIL` | Tap a current owner-approved contextual action | Owning product destination; an instruction `Pay Now` action invokes the DOC-09 Checkout Resolver | Back returns to Detail, then to the original Inbox or external entry context. |
| Push, email, SMS, WhatsApp, deeplink, or approved app context | Open a specific notification | `NOTIFICATION-DETAIL` after authentication and access checks | Back returns to the prior app context where available; otherwise Inbox. |

Opening a notification must revalidate the current owning-domain state, permissions, and target availability. A stale message may retain its historical content while its action is removed or replaced with a safe current-state explanation.

#### 5.19.3 `NOTIFICATION-INBOX` Screen

The MVP screen order is:

1. header with Back, title `Notifications`, Search, and Settings;
2. horizontally scrollable filters: `All`, `Unread`, `Action Required`, `System`, `Service`, `Transaction`, `Promotion`, and `Archived`;
3. newest-first `NOTIFICATION-LIST`;
4. the applicable empty, no-match, loading, offline, failure, or unavailable-target state.

`All` excludes archived records. The Home Inbox badge counts unread Inbox records only; it is not a count of unresolved tasks, unread external-channel deliveries, or domain objects.

Each `NOTIFICATION-CARD` shows:

- category label;
- title;
- concise preview;
- date and time;
- unread indicator;
- `Action Required` only where the owning domain currently requires user action.

Every card opens `NOTIFICATION-DETAIL`; material Accept, Reject, Pay, Verify, or other domain actions should not execute directly from the card. Marking a card read does not resolve an action or change the underlying domain status. The Inbox supports read/unread handling, `Mark All Read`, Archive, and Restore from Archived. It does not offer user hard deletion.

#### 5.19.4 `NOTIFICATION-DETAIL` Screen

The detail screen shows:

1. Back;
2. title and date/time;
3. category label;
4. full permitted message content;
5. mapped user-facing domain status where relevant;
6. permitted contextual reference;
7. one current contextual action where available;
8. Archive, or Restore when opened from Archived.

The UI must not display duplicate generic fields named `state`, `label`, and `status`. Category, Inbox presentation, domain status, and action requirement remain separate:

| Signal | Meaning | Source |
| --- | --- | --- |
| Category | `System`, `Service`, `Transaction`, or `Promotion` presentation grouping. | DOC-08 approved event definition |
| Presentation state | `Unread`, `Read`, or `Archived` for this recipient's Inbox record. | Notification Inbox record |
| Domain status | Current user-facing status mapped from the owning domain. | Owning domain and status-display reference matrix |
| Action Required | Current user task or resolution need. | Owning domain/task; never invented by Inbox |

The notification record may preserve status and action-at-send snapshots for audit, but current display and action availability must use the latest authorized domain state.

For an instruction-related notification, `NOTIFICATION-DETAIL` is mandatory before payment action. Detail revalidates the authenticated payer, current instruction state, permission, target availability, and action availability before presenting an owner-approved `Pay Now` action. Where still available, that action invokes the same DOC-09 Checkout Resolver described in Sections 5.12.5 and 5.20.3; there is no notification-to-Checkout bypass.

A stale, withdrawn, expired, ineligible, or unavailable notification target remains in Detail with the applicable current resolution or returns to an owner-approved source context. Notification content, delivery, read/archive state, and stored status/action/quote snapshots do not establish current Checkout eligibility, payer authorization, Provider Confirmation, Payment, or payment result.

#### 5.19.5 `NOTIFICATION-SETTINGS` Screen

The MVP screen order is:

1. header with Back, title `Notification Settings`, and Inbox;
2. channel availability and device push-permission state;
3. required communications, visibly labelled `Required` and not shown as disableable toggles;
4. optional reminders and service updates;
5. rewards, referral, offers, and product updates;
6. channel controls for launched, verified, consented, and permitted push, email, SMS, and WhatsApp;
7. handoff to `PRIVACY-DATA-CONTROLS` for underlying direct-marketing, personalization, or partner-data-use choices.

Preferences save immediately. A failed change restores the prior effective setting and offers Retry; there is no route-level Save button. Account-level preferences and Inbox read/archive state synchronize across approved devices. Device push permission remains device-specific. Language and Theme remain separate Me preferences.

Mandatory service Inbox records remain available even where optional channels are disabled. A channel toggle controls permitted delivery, not the underlying event, record retention, domain state, legal obligation, or privacy purpose.

#### 5.19.6 Data, Status, and Admin Handoffs

Material notification signals include root/inbox/detail/settings opened, search/filter used, message read/unread/archived/restored, Mark All Read, setting-change success/failure, contextual action opened, unavailable target encountered, and external entry resolved. These signals must reference the notification record and owning object without copying sensitive message content into ordinary analytics.

DOC-08 owns event IDs, category assignment, message eligibility, channels, templates, preference policy, message/batch/source identifiers, delivery attempts and notification retention requirements. The status-display reference matrix governs user-facing domain labels; the owning domain remains authoritative for status and action-required meaning. DOC-14 owns abuse/rate-limit and applicable risk controls; DOC-15 owns lawful-purpose, consent, masking, approved-purpose use and retention governance; DOC-18 must define the final object, event, lineage, correlation, recipient projection and delivery-attempt model; DOC-19 owns security; DOC-21 owns support and delivery operations; and DOC-22 owns only permitted Admin lookup, template/configuration execution, scheduling and audit handling under those owners.

#### 5.19.7 Open Items

- final visual styling, density, iconography, preview length, and filter-chip behavior;
- exact search matching, archive visibility/presentation/access controls, and offline cache policy; Archive is not a retention or disposition decision;
- final provider capabilities, quiet hours, retry/fallback thresholds, and admin workflow;
- final template content and legally validated mandatory-service classifications.

### 5.20 `PAYMENT-CHECKOUT` Checkout Workspace

`PAYMENT-CHECKOUT` is the existing, `Defined baseline` flow/screen group for one persistent Checkout Workspace. Its human-readable route behavior is decision-complete enough for continued alignment; final visual design, exact expression and mappings, technical specification, prototype and validation evidence, implementation, acceptance, and operational readiness remain pending with their formal owners. It is not a new route family, a sequence of child routes, a Payment, a Payment Instruction, a Settlement, or a Payout. Internal presentations are replaceable views of the same Workspace and must not redefine the unique domain truth owned by DOC-09.

DOC-06B owns the route-level UI/UX described in this section. The accepted payment-domain baseline is the current DOC-09 Founder Working Baseline at `docs/02-payment-domain/doc-09-payment-domain-architecture.md`. This section presents DOC-09 facts without redefining their object, lifecycle, status, event, audit, authorization, provider, or financial meaning.

The derived [Payment Checkout route map](../diagrams/routes/payplus-payment-checkout-route-map.md) is the current discussion-reference projection of this accepted route-level UI/UX. It does not override this section, DOC-09, or the route register and must not be read as a mandatory wizard, a set of child routes, or a domain state model.

#### 5.20.1 Ownership and Semantic Boundary

| Concern | DOC-06B treatment | Formal owner or handoff |
| --- | --- | --- |
| Checkout Workspace route UX | Entry and return behavior, adaptive presentation, visible payer task, funding interaction, review, progress, resolution, mobile, and accessibility. | DOC-06B |
| Bill/Rent source and handoff | Present source context received from the owning Bill/Rent or Tenancy surface; do not redefine source eligibility, amount, period, evidence, payee, or CTA rules. | DOC-06C |
| Payment Domain | Display one Checkout against exactly one Payable Basis, funding and confirmed-payment facts, locking, continuation, closure, expiry, and late-confirmation meaning. | DOC-09 |
| Outcome, disclosure, authorization wording, messages, and CTAs | Reserve content locations and distinguish facts and actions; do not invent final payer-facing wording. | DOC-07 |
| Notification identity, delivery, and notification action routing | Require instruction-related notifications to enter `NOTIFICATION-DETAIL`, revalidate current state and permission, and expose only a current owner-approved action to the DOC-09 Checkout Resolver. Notification content and delivery are non-authoritative. | DOC-08 plus the applicable domain owner |
| Promotions, fees, benefits, and payer charge | Display owner-supplied accepted, submitted-pending, or estimated facts with their applicable qualification. | DOC-02/DOC-07/DOC-09/DOC-13 and applicable commercial/accounting owners |
| Provider return and confirmation evidence | Treat return as non-authoritative and wait for or consume authoritative evidence. | DOC-17 and DOC-09 |
| Object schema, allocation-version implementation, machine states, events, lineage, audit, and reporting | Do not define them in this route document. | DOC-18 |
| Authentication, tokenization, session, and reauthentication | Preserve route context only after applicable security checks; do not preserve stale security state. | DOC-19 |
| Prototype, accessibility, implementation, UAT, operations, and support evidence | Record later evidence dependencies without claiming they have passed. | DOC-20, DOC-21, DOC-22, and applicable owners |

The Checkout presentation must preserve these DOC-09 boundaries:

- each Checkout is associated with exactly one Bill/Rent Payable Basis;
- at most one Checkout for that Payable Basis may be active and continuable at a time;
- a later eligible Checkout may be created after every earlier Checkout for that basis has become closed, expired, or otherwise non-continuable;
- every earlier Checkout remains an authoritative retained historical record in its recorded condition and is not erased, rewritten, invalidated as history, or reactivated merely because a later Checkout exists;
- each confirmed Funding Leg creates or returns exactly one immutable Payment, including where the Checkout remains partially funded;
- Checkout, Funding Allocation, Funding Leg, Payment Attempt, Provider Submission, Payment, Payment Application, Settlement, and Payout remain separate concepts;
- a Payment Profile is a reusable payer-owned ratio template, not a Checkout, Funding Allocation, Funding Leg, or payer authorization.

#### 5.20.2 Condition, Fact, Evidence, Presentation, and Technical-State Boundary

| Authority layer | Owned meaning | DOC-06B presentation boundary |
| --- | --- | --- |
| DOC-09 semantic business conditions | `Checkout editable`; `Checkout target locked`; `Checkout partially funded`; `Checkout fully funded`; `Checkout closed`; `Checkout expired`. | Present the applicable owner-supplied condition and valid action without converting it into a DOC-06B status taxonomy or a fixed sequence of screens. |
| DOC-09 authoritative payment facts | Confirmed Funding Leg; immutable Payment; confirmed obligation-funded value; Remaining Checkout Target. | Display confirmed and remaining obligation-funded value distinctly. Do not infer confirmation from provider return or from presentation progress. |
| DOC-17 evidence conditions | Provider submission or confirmation evidence awaiting authoritative evaluation. | `Pending evidence` is a presentation of unresolved authoritative evidence, not a success/failure conclusion or a new Checkout machine state. |
| DOC-06B presentation and task contexts | Checkout overview; Funding; Review and authorize; Funding Leg execution; Result and resolution; interrupted or protected-return task context; pending-evidence presentation. | These are adaptive internal Workspace presentations or task contexts. They may overlap, compose, or be skipped and are not routes, domain objects, lifecycle stages, or system-state enums. |
| DOC-18 technical implementation | Final machine-state enums; technical transitions; schemas; events; lineage; audit implementation. | DOC-06B must not name, infer, or freeze the technical representation. |
| DOC-07 payer-facing presentation | User-facing Outcome; status label; Message; disclosure; CTA; final presentation wording. | DOC-06B reserves the location and required meaning but does not create an Outcome ID, status label, Message ID, CTA mapping, or final copy. |

Terms such as `pending evidence`, `interrupted`, `unsuccessful presentation`, `result`, and `recovery` retain their actual layer: evidence-driven presentation, temporary task context, payer-visible result context, or a condition-dependent permitted action. They do not silently become machine-state enums, domain conditions, Outcomes, Messages, CTAs, or events.

#### 5.20.3 Checkout Resolver Entry and New Checkout Context

Bill/Rent Pay is a Checkout resolver, not unconditional Checkout creation. After the source owner has identified the current Bill/Rent source and DOC-09 has established the applicable Payable Basis, the transition must resolve current eligibility and the current Checkout condition:

| Resolver result | Route-level treatment |
| --- | --- |
| Eligible and no active continuable Checkout exists for the same Payable Basis | A new Checkout may begin. Carry the authoritative Bill/Rent source reference, the DOC-09-owned Payable Basis and its applicable Payment Obligation reference or references together with Payee or landlord context, Checkout Target, current eligibility/Evidence context, source-aware return context and available funding actions. |
| An active continuable Checkout exists for the same Payable Basis | Do not create another Checkout. Resolve or intentionally resume the existing Checkout after revalidation. |
| Not currently eligible | Remain in the Bill/Rent source-owner context with an explicit owner-supplied unavailable or resolution treatment. Do not create or resume Checkout merely to show an error. |

The source context remains visible without changing route identity:

| Context | Checkout presentation may carry forward | Source-owner facts that DOC-06B must not invent |
| --- | --- | --- |
| Bill | Bill identity, issuer/payee, category, due date, eligible amount, evidence/readiness summary, and return destination. | Bill CTA availability, current evidence, eligible amount, payee relationship, readiness, and contextual disclosures. |
| Rent/Tenancy | Rent identity, property/tenancy and landlord/payee context, payable period, due date, eligible amount, evidence/readiness summary, and return destination. | Tenancy standing, payable period, rent CTA availability, current evidence, eligible amount, landlord relationship, readiness, and contextual disclosures. |

Bill and Rent differences may change composed content, labels, disclosures, and return context. They do not by themselves create different Checkout routes or domain objects.

##### Instruction `Pay Now` and Notification Entry

Instruction `Pay Now` invokes the same DOC-09 Checkout Resolver rather than unconditionally creating, activating, or resuming a predetermined Checkout. Payment Instruction and Checkout remain separate objects throughout the handoff.

| Source action | Required route treatment |
| --- | --- |
| `INSTRUCTIONS-DETAIL` - current `Pay Now` | Verify the authenticated payer and consume current instruction validity and action availability before invoking the DOC-09 Checkout Resolver. |
| Instruction-related notification | Enter `NOTIFICATION-DETAIL`; revalidate current state, permission, target, and action availability; then expose an owner-approved `Pay Now` action to the same resolver only where still available. There is no direct notification-to-Checkout edge. |
| Resolver returns an active, eligible and continuable Checkout for the same Payable Basis | Intentionally Resume that existing Checkout after current revalidation. Do not create another Checkout. |
| Resolver permits a new Checkout because no active continuable Checkout exists and current eligibility passes | Establish an eligible New Checkout while preserving the Payment Instruction and source-aware return context as separate from Checkout identity. |
| Resolver cannot proceed | Remain in Instruction or Notification Detail, or return the applicable source-owner resolution. Do not create or reactivate Checkout. |

Every entry path must revalidate applicable obligation, evidence, eligibility, timing, fees, benefits, funding, destination, risk, security, and authorization conditions at the owner-controlled point where they apply. Neither a source CTA nor a notification snapshot carries forward stale authorization, silently creates a Funding Leg, or initiates a Provider Submission.

#### 5.20.4 Context Restoration and Adaptive Presentation

The Workspace composes its current presentation from the authoritative Checkout condition, the payer's current task, confirmed and remaining financial facts, current eligibility and revalidation results, and currently available actions.

| Entry or update | Required restoration behavior |
| --- | --- |
| New Checkout | Establish the new Workspace context described in Section 5.20.3 before presenting the applicable funding action. |
| Intentional Resume | Restore overall Workspace context only after revalidation confirms the Checkout remains active, eligible, and continuable. Foreground the original Checkout Target, confirmed value, Remaining Checkout Target, Funding Leg progress, continuation expiry, material changes, current eligibility, and next valid actions. |
| Protected re-entry | After card, Payment Profile, provider/3DS, reauthentication, or application return, restore the safest valid point in the interrupted task only after revalidation. This is task-context restoration, not a third standard first view. |
| Unsafe or materially changed protected return | Fall back to Resume overview only when the Checkout remains active, eligible, and continuable. Otherwise present historical or source-owner resolution. |
| Pending-evidence or confirmed-leg update | Evaluate the authoritative current condition and evidence before composing the next presentation. Do not use stale task context. |
| Inactive, ineligible, or non-continuable Checkout | Present historical or source-owner resolution. That resolution does not automatically re-enter Checkout composition. |

Neither Intentional Resume nor protected re-entry automatically proceeds to Funding. Revalidation must not preserve stale authorization, provider evidence, eligibility, fees, benefits, destination, risk, privacy, or security decisions.

The following five classifications describe adaptive presentation content, not fixed or exhaustive navigation:

| Presentation classification | Payer purpose and material content |
| --- | --- |
| Checkout overview | Understand source context, Checkout Target, confirmed and remaining facts, progress, expiry, material changes, continuability, and next valid actions. |
| Funding | Confirm or change an eligible card, provisionally express single-card intent when no eligible saved card is available, or intentionally expand to eligible multi-card allocation. |
| Review and authorize | Review the holistic Checkout and provide the applicable payer authorization for the next Provider Submission. |
| Funding Leg execution | Understand the current leg, authoritative evidence condition, confirmed progress, remaining target, and whether another valid action is available. |
| Result and resolution | Understand successful completion, partial funding, pending evidence, unsuccessful execution, closure, expiry, or source-owner/historical resolution. |

These classifications may be entered non-linearly, overlap, or be composed together. They may evolve, merge, split, or be renamed; a payer need not traverse all five. They are not routes, child destinations, machine states, domain objects, events, or technical contracts.

##### Checkout Entry, Revalidation and Presentation-Composition Decision Map

This decision map explains Bill/Rent Pay and Instruction `Pay Now` resolution; mandatory Notification Detail entry; eligibility and Checkout-condition evaluation; intentional Resume; protected return; authoritative evidence updates; presentation composition; historical or source-owner resolution; and late confirmation. It is not the complete payer-visible UI journey.

```mermaid
flowchart TD
    BP["Bill or Rent Pay"] --> ER["Resolve Payable Basis, eligibility, and current Checkout condition"]

    IP["INSTRUCTIONS-DETAIL<br/>Pay Now"] --> IV["Validate authenticated payer, current instruction, and action availability"]
    IN["Instruction-related notification"] --> ND["NOTIFICATION-DETAIL"]
    ND --> NV["Revalidate current state, permission, target, and action availability"]
    NV -->|"Owner-approved Pay Now remains available"| IV
    NV -->|"Stale, withdrawn, expired, ineligible, or unavailable"| NR["Notification/current resolution"]
    IV -->|"Invoke DOC-09 Checkout Resolver"| ER
    IV -->|"Cannot proceed"| SR

    ER -->|"Eligible; no active continuable Checkout"| NC["New Checkout"]
    ER -->|"Active continuable Checkout exists"| IR["Intentional Resume"]
    ER -->|"Not currently eligible"| SR["Source-owner resolution"]

    NC --> NO["Establish new Workspace context"]

    IR --> RV1["Revalidate Checkout, eligibility, continuability, and protected conditions"]
    RV1 -->|"Active, eligible, and continuable"| WR["Restore overall Workspace context"]
    RV1 -->|"Inactive, ineligible, or non-continuable"| HR["Historical or source-owner resolution"]

    PR["Card, Profile, provider, 3DS, reauthentication, or application return"] --> RV2["Revalidate user, Checkout, evidence, eligibility, fees, benefits, destination, risk, and security"]
    RV2 --> TC{"Interrupted task context remains safe?"}

    TC -->|"Yes"| TR["Restore safest valid interrupted task"]
    TC -->|"No, but Checkout remains active, eligible, and continuable"| FB["Resume overview"]
    TC -->|"No safe Checkout continuation"| HX["Historical or source-owner resolution"]

    PE["Pending-evidence update"] --> AE["Evaluate authoritative current condition and evidence"]
    CE["Confirmed-leg evidence update"] --> AE

    NO --> AE
    WR --> AE
    TR --> AE
    FB --> AE

    AE --> PC["Compose current presentation; not a route, state, event, or object"]

    PC -. "may include or combine" .-> O["Checkout overview"]
    PC -. "may include or combine" .-> F["Funding"]
    PC -. "may include or combine" .-> R["Review and authorize"]
    PC -. "may include or combine" .-> E["Funding Leg execution"]
    PC -. "may include or combine" .-> X["Result and resolution"]

    LC["Late accepted confirmation"] --> CR["Immutable Payment and independent controlled resolution outside ordinary continuation"]
```

Instruction `Pay Now` reaches the DOC-09 Checkout Resolver only after current instruction and payer validation; it does not preselect new-versus-Resume identity. An instruction-related notification reaches that same resolver only through `NOTIFICATION-DETAIL` and current action revalidation, with no notification-to-Checkout bypass edge. Resolver and revalidation nodes are operations, not payer-visible presentations, routes, states, events, or objects. Historical, notification, or source-owner resolution has no arrow back to presentation composition. Late accepted confirmation remains outside ordinary Checkout continuation.

##### Condition-Aware Illustrative Checkout Workspace Payer Experience Flow

This diagram is an illustrative payer-visible journey from Bill/Rent Pay or a current Instruction `Pay Now` action through Checkout resolution, funding, review, authorization, progress, result, and safe completion or recovery. It is not a mandatory fixed wizard, screen sequence, route hierarchy, machine-state diagram, object lifecycle, or implementation contract. The preceding decision map and the Minimum Adaptive UI Contract retain the detailed resolution, revalidation, evidence, and action-availability rules.

```mermaid
flowchart TD
    B["Bill/Rent: select items and Pay"] --> R{"Checkout resolution"}
    I["INSTRUCTIONS-DETAIL: current Pay Now"] --> R
    N0["Instruction-related notification"] --> ND["NOTIFICATION-DETAIL"]
    ND -->|"Revalidate; current owner-approved Pay Now"| R

    R -->|"Eligible new Checkout"| N["1. New Checkout overview"]
    R -->|"Valid Resume"| O["1. Resume overview"]
    R -->|"Unavailable"| H["Source or historical resolution"]

    N -->|"Funding is the next permitted task"| F["2. Choose or change funding"]
    O -->|"Funding is the next permitted task"| F

    F -->|"Default eligible path"| SC["Single card"]
    F -->|"Use multiple cards"| MC["Multi-card or Payment Profile"]

    SC --> V["3. Review amount, fees and benefits"]
    MC --> V

    V --> A["4. Authorize next submission"]
    A --> E["5. Funding Leg progress"]
    E --> C{"Authoritative result"}

    C -->|"Fully funded"| D["6. Payment Result / fully funded completion"]
    C -->|"Partially funded"| P["6. Partial result"]
    C -->|"Evidence pending"| W["6. Pending result"]
    C -->|"Unsuccessful"| U["6. Unsuccessful result"]

    P -->|"Continue or adjust if permitted"| F
    P -->|"Wait where evidence remains pending"| W
    P -->|"Close if permitted"| G
    P -->|"Safe return; continuation preserved"| G

    W -. "Authoritative evidence update" .-> C
    W -->|"Safe return"| G

    U -->|"Owner-confirmed recovery"| F
    U -->|"Close if permitted"| G
    U -->|"Safe return"| G

    D --> G{"Newly confirmed Payment on otherwise unsaved source?"}
    G -->|"No; source already projected or no Payment confirmed"| X["Safe return or approved later continuation"]
    G -->|"Yes"| S["Owner-controlled optional Save resolver"]
    S -->|"Save selected"| SA["Same ID Saved/current"]
    S -->|"Declined, skipped, dismissed, or leave Result"| SH["Same ID history-only"]
    SA --> X
    SH --> X

    classDef journey fill:#eaf3ff,stroke:#285b8f,stroke-width:2px,color:#172b3a;
    classDef decision fill:#fff4ce,stroke:#8a6d1d,stroke-width:2px,color:#222;
    classDef completion fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#153d18;
    classDef resolution fill:#f3f4f6,stroke:#5f6368,stroke-width:2px,color:#202124;
    class B,I,N0,ND,N,O,F,SC,MC,V,A,E,P,W,U,S journey;
    class R,C,G decision;
    class D,SA,SH completion;
    class H,X resolution;
```

- The numbered presentations are adaptive Workspace views, not child routes, domain conditions, machine states, or a mandatory fixed wizard. Presentations may combine or be skipped when the current payer task does not require them.
- Instruction `Pay Now` invokes Checkout resolution and does not choose New-versus-Resume identity. An instruction-related notification reaches resolution only after `NOTIFICATION-DETAIL` revalidates current state, permission, target, and action availability; there is no bypass edge.
- A Resume proceeds to Funding only when Funding is the next permitted task. Otherwise, the preceding decision map and the Minimum Adaptive UI Contract restore the applicable Review, progress, pending, result, or safe-return presentation.
- Protected return revalidates and restores the safest valid presentation; its detailed resolution remains in the preceding decision map.
- Late confirmation remains outside ordinary Checkout continuation and is intentionally not a normal-flow branch here.
- Fully funded completion exposes no Funding, Continue, adjust, retry, wait, or `Close Checkout` action. Before Activity, Receipt, source return or ordinary safe exit, an otherwise unsaved source with a newly confirmed Payment must pass through the owner-controlled Save resolver; an already Saved/current source keeps its existing projection, and Activity never offers Save.
- Pending exposes no retry or alternate-funding submission while authoritative evidence remains unresolved.
- Partial and unsuccessful results expose only owner- and condition-permitted actions.
- `OQ-XDOC-007` and `OQ-XDOC-015` retain their permanent traceability IDs; their decided dispositions are aligned across the Open Questions Register and derived route diagrams. `PDM-PROP-X01` and `PDM-PROP-X02` remain historical Proposal-evidence aliases only.

##### Minimum Adaptive UI Contract

This contract defines the minimum route-level meaning that every permitted composition must preserve. It does not select final tabs, sheets, cards, steppers, animation, styling, measurements, or pixel layout.

| Conformance term | Meaning in this section |
| --- | --- |
| Required | Every applicable composition must preserve the stated information, action boundary, or return behavior. |
| Recommended | Normal presentation treatment unless current condition, accessibility, security, or available capability requires a safer composition. |
| Optional | May be included only when an applicable owner supplies the capability and it does not obscure required facts or actions. |

Workspace-wide requirements:

| UI concern | Minimum adaptive contract |
| --- | --- |
| Persistent Workspace identity | Required: keep the Bill/Rent identity, payee or landlord context, and Checkout Target visible or available through an immediately accessible Workspace summary without leaving `PAYMENT-CHECKOUT`. Bill/Rent details may be condensed after initial confirmation but must not be replaced by generic payment wording. |
| Persistent financial position | Required wherever execution has begun or confirmed/pending value exists: keep confirmed value, unconfirmed value, Remaining Checkout Target, applicable payer-charge category, and current Funding Leg progress visible or available through the same Workspace presentation. Estimated, submitted-pending, and confirmed charges remain separate. |
| Current condition and consequence | Required: state the current payer-relevant Checkout/evidence meaning, whether ordinary continuation is available, material changes since the prior action, and the consequence of the currently offered primary action. Exact Outcome, Message, disclosure, and CTA wording remains DOC-07. |
| Action hierarchy | Required: expose only currently permitted actions. Where one action advances the current valid task, present it as the primary action. Present change, Back, safe return, wait, or `Close Checkout` as secondary/escape actions according to condition. A disabled or unavailable action must never appear equivalent to an enabled primary action. |
| Unavailable and disabled actions | Required: never enable an action that current authoritative conditions prohibit. A temporarily unavailable action may remain visible only with an owner-approved explanation and resolution. An unlaunched or unsupported capability may be omitted. Internal risk, security, or provider reasons must not be exposed without owner approval. |
| Back and cancel | Required: Back or cancel never authorizes, submits, retries, closes, or rewrites Checkout. Before Provider Submission, preserve valid entered intent or obtain explicit confirmation before discarding unsaved changes. After submission, Back may leave the presentation safely but must not cancel or classify the Provider Submission. |
| Supporting handoff | Required: Card/Profile/provider/3DS/reauthentication handoff preserves a protected return reference, then revalidates before restoring the safest valid task presentation, Resume first view, or historical/source-owner resolution. Cancellation or failure returns with retained valid context and an explicit recovery action where available. |
| Responsive composition | Required: on mobile, place the current financial position and primary action before lower-priority detail; a condensed summary may expand in place. Content must reflow for large text, zoom, orientation, and safe areas without hiding condition, consequence, or escape action. |
| Accessible updates | Required: use semantic headings/landmarks, programmatic labels, logical reading/focus order, non-color-only distinctions, and announcements for authoritative evidence, progress, Remaining Checkout Target, errors, and action-availability changes. Focus returns to the restored task heading or current resolution after a protected handoff. |

The information hierarchy below describes semantic priority, not fixed vertical order. Presentations may overlap or combine when all required information and action boundaries remain clear.

| Adaptive presentation | Entry or activation condition | Minimum information hierarchy and persistent context | Primary action | Secondary, Back, handoff, and unavailable treatment | Owners and intentionally open visual detail |
| --- | --- | --- | --- | --- | --- |
| New Checkout first view | Required when Bill/Rent Pay resolves an eligible Payable Basis with no active continuable Checkout. | Required: (1) Bill/Rent identity and payee/landlord; (2) payable period/due context where applicable; (3) Checkout Target and current eligibility/evidence summary; (4) estimated fee/benefit/payer-charge facts where supplied; (5) return context; (6) available funding readiness. The payer must be able to confirm what is being paid before authorization. | Required: advance to the currently available funding task, using the eligible default single-card presentation where applicable. This may be composed with the first view but must not obscure Target confirmation. | Recommended: owner-permitted Target adjustment before lock, change source only through the owning Bill/Rent context, or safe return. Back before submission preserves valid intent or explicitly confirms discard. Ineligible/unavailable resolution remains with DOC-06C and must not create Checkout. | DOC-06B composition; DOC-06C source facts; DOC-09 eligibility/Target; DOC-07 wording. Final card, summary, and section styling remain open. |
| Intentional Resume first view | Required only after revalidation confirms an existing Checkout is active, eligible, and continuable. | Required: (1) original Bill/Rent and Checkout Target; (2) confirmed value; (3) unconfirmed value; (4) Remaining Checkout Target; (5) Funding Leg progress; (6) continuation expiry; (7) material fee, benefit, card, destination, eligibility, evidence, risk, or security changes; (8) next valid actions. Foreground changed or action-required facts before routine detail. | Required: the condition-specific next valid action, which may be review, continue eligible unexecuted funding, wait, resolve a material change, or safe return. Resume does not default to Funding. | Recommended: view full leg/progress detail; `Close Checkout` only when permitted and with consequences; safe return to the approved source. If revalidation fails, replace Resume actions with historical/source-owner resolution. | DOC-06B presentation; DOC-09 continuability; DOC-07 consequence wording; DOC-19 reauthentication. Final overview arrangement remains open. |
| Funding | Required when current conditions permit selection or change of unexecuted funding. | Required: (1) persistent Checkout Target and current confirmed/unconfirmed/remaining position; (2) current eligible saved-card/default or provisional no-card presentation; (3) single-card choice with clear progressive expansion to owner-confirmed multi-card capability; (4) per-card obligation-funded allocation and separate estimated payer charge/benefit where supplied; (5) allocation validation/error summary. | Required: continue to holistic review only after the current funding choice is owner-confirmed eligible and the authoritative allocation requirements pass. | Recommended: change card, expand/contract eligible multi-card presentation, or open Card/Profile support; Back returns to New/Resume context without submission. Cancel/failure of support restores retained valid intent and recovery. Unsupported capabilities are omitted or owner-approved unavailable, never selectable. | DOC-09 allocation/locking; DOC-18 audit implementation; DOC-19 card/security; DOC-13 benefits. Final editor control, tabs/sheets, and visual allocation treatment remain open. |
| Review and authorize | Required before every Provider Submission, including revised execution after a material change. | Required: (1) persistent source and Checkout Target; (2) current Funding Leg obligation-funded amount; (3) masked funding method; (4) accepted/confirmed, submitted-pending, or estimated payer charge as applicable; (5) fee/benefit facts; (6) confirmed/unconfirmed/remaining position; (7) destination/timing/evidence and material-change disclosures; (8) authorization consequence. | Required: provide the applicable payer authorization for the next Provider Submission. Authorization applies only to that submission and must not be inferred from prior review, profile selection, Resume, or provider return. | Recommended before submission: return to eligible unexecuted funding changes or safe return. Back/cancel does not submit. Once submission begins, route to Funding Leg progress and do not offer cancellation through generic Back. Disabled authorization requires an owner-approved explanation/resolution. | DOC-07 final wording/CTA; DOC-09 authorization and lock; DOC-19 security. Final review layout and authentication component remain open. |
| Funding Leg progress | Required after authorization while the current Provider Submission or authoritative confirmation evaluation is unresolved or while sequential legs remain. | Required: (1) current leg identity/position within the funding arrangement; (2) submitted obligation-funded value and payer charge category; (3) confirmed value; (4) unconfirmed value; (5) Remaining Checkout Target; (6) prior leg results; (7) current authoritative evidence meaning; (8) next available action, if any. | Required: no generic primary action while authoritative evidence is unresolved. When the current condition permits another action, present only that condition-specific action after evaluation. | Provider/3DS return revalidates before restoring progress, pending, or result. Back/safe return does not cancel the submission. Prevent duplicate activation and unsafe retry. Announce leg/evidence/remaining-value changes accessibly. | DOC-09 execution semantics; DOC-17 provider evidence; DOC-18 technical states/events; DOC-07 payer wording. Final progress visualization remains open. |

Every Back, close, source-return or safe-return treatment in this adaptive table is subject to the source-projection guard. Before any confirmed Payment exists, no post-Payment Save outcome is created and legitimate pre-confirmation unprojected treatment may continue. If the current Workspace contains a newly confirmed Payment linked to an otherwise unsaved source, an ordinary return or exit first hands to the owner-controlled Save resolver for same-ID Saved/current or history-only. An already Saved/current source retains its existing projection. Activity and Receipt never supply the missing Save action.

Result and resolution presentations must not share one generic action set:

| Result or resolution presentation | Activation condition | Minimum information hierarchy and persistent context | Primary action | Secondary, closing, return, and unavailable treatment | Owners and intentionally open visual detail |
| --- | --- | --- | --- | --- | --- |
| Fully funded completion | Required when authoritative confirmed obligation-funded value equals Checkout Target. | Required: (1) fully funded Checkout meaning; (2) Checkout Target and confirmed value; (3) applicable confirmed payer-charge facts; (4) confirmed Funding Leg/Payment summary without implying Settlement or Payout completion; (5) Bill/Rent/source context; (6) source-projection handoff before any receipt/activity or source-return handoff. | Required: retain an existing Saved/current projection, or for an otherwise unsaved source resolve selected Save to same-ID Saved/current or declined/skipped/dismissed Save to same-ID history-only before approved safe exit or source return. | Optional detail, receipt, or Activity handoff is available only after that projection outcome. Do not expose Funding, Continue, adjust, retry, wait, `Close Checkout`, or Save from Activity. Back must not reopen setup. | DOC-09 confirmation/full-funding meaning; DOC-05/DOC-06C Save policy; DOC-07 completion wording; DOC-10 payout separation. Final celebration, illustration, and layout remain open. |
| Partially funded result and recovery | Required when confirmed value is above zero and below Checkout Target. | Required: original Checkout Target, confirmed value and immutable Payment facts, unconfirmed value, Remaining Checkout Target, complete Funding Leg progress, continuation expiry, locked versus eligible unexecuted funding, and consequence of wait, continue/change, safe return, or closing. | Required: one current condition-permitted action: continue eligible unexecuted funding, wait for authoritative evidence, or another owner-confirmed recovery. Pending evidence takes precedence where duplicate submission risk exists. | Where the result contains a newly confirmed Payment for an otherwise unsaved source, any Close Checkout, source return, Activity, Receipt or ordinary safe exit first hands to the owner-controlled Save resolver; selected Save produces Saved/current and declined/skipped/dismissed Save produces history-only. Recommended recovery actions remain owner-permitted. | DOC-09 partial funding/closure; DOC-05/DOC-06C projection policy; DOC-07 consequence wording; DOC-17 provider evidence; DOC-14 risk; DOC-19 security enforcement. Final recovery component layout remains open. |
| Pending-evidence result | Required whenever authoritative submission/confirmation evidence is unresolved, including after provider/3DS return or later evidence update. | Required: (1) known submitted leg/value; (2) no-success/no-definitive-failure meaning; (3) confirmed value from other legs; (4) unconfirmed value; (5) Remaining Checkout Target; (6) what is being awaited; (7) whether any safe action is currently available. | Required: wait or another owner-confirmed non-submission action. There is no retry, alternate-funding submission, or success action while duplicate-submission risk remains unresolved. | If no Payment is confirmed, no post-Payment Save outcome exists. If another leg created a newly confirmed Payment for an otherwise unsaved source, any safe return, Activity or Receipt handoff first resolves same-ID Saved/current or history-only through the owner-controlled Save resolver. Back does not cancel or reclassify. | DOC-17 evidence; DOC-09 confirmation; DOC-05/DOC-06C projection policy; DOC-07 wording; DOC-21 support. Final pending illustration, timing text, and refresh mechanism remain owner-controlled/open. |
| Unsuccessful result and permitted recovery | Required only after authoritative evidence supports an unsuccessful attempt or Funding Leg result. | Required: (1) affected leg and unsuccessful meaning; (2) no Payment for that unsuccessful attempt; (3) any confirmed value from other legs; (4) unconfirmed value, if any separate evidence remains pending; (5) Remaining Checkout Target; (6) locked/unexecuted funding facts; (7) owner-supplied recovery availability. | Required: only a currently permitted recovery after revalidation, such as using eligible unexecuted funding. Do not expose a generic retry. | If no Payment is confirmed, no post-Payment Save outcome exists. If another leg created a newly confirmed Payment for an otherwise unsaved source, any Close Checkout, safe return, Activity or Receipt handoff first resolves same-ID Saved/current or history-only through the owner-controlled Save resolver. | DOC-09 attempt/leg meaning; DOC-05/DOC-06C projection policy; DOC-17 provider evidence; DOC-14 risk; DOC-19 security enforcement; DOC-07 wording. Final error illustration and component styling remain open. |
| Historical or source-owner resolution | Required when Checkout is inactive, ineligible, non-continuable, closed/expired with no ordinary continuation, or Bill/Rent resolution must remain with its owner. | Required: (1) recorded Checkout condition; (2) original Checkout Target; (3) preserved confirmed Payment facts where applicable; (4) no-continuation meaning; (5) source Bill/Rent context; (6) owner-confirmed resolution or support handoff. Historical facts must remain authoritative and unchanged. | Required: the applicable source-owner, historical-detail, support, or safe-exit action. | If this resolution contains a newly confirmed Payment for an otherwise unsaved source, the owner-controlled Save resolver must first produce same-ID Saved/current or history-only. Otherwise preserve the existing projection or legitimate pre-confirmed/incomplete-Setup unprojected treatment. Do not expose ordinary Checkout composition or invent Archived-source behavior. | DOC-06C source/projection resolution; DOC-09 history/continuability; DOC-07 wording; DOC-21 support. Final historical-detail composition remains open. |

Where adaptive presentations are combined, the more restrictive current condition controls action availability. A composed surface must not hide required context or make two mutually incompatible actions appear concurrently primary. Final visual hierarchy may vary by viewport and task only within these constraints.

#### 5.20.5 Funding Selection, Allocation, and Protected Support Return

When at least one owner-confirmed eligible saved card is available, a new Checkout defaults to a clear single-card funding presentation. The payer may change the selected eligible card or intentionally expand the same Workspace into multi-card funding. Single-card and multi-card are UI configurations derived from authoritative Funding Allocation facts, not permanent Checkout states.

When no eligible saved card is available, use a provisional single-card funding presentation that explains the need to add or select a card and preserves the Checkout context during that supporting action. This presentation expresses payer intent only. It does not determine when an authoritative Funding Allocation Version or Funding Leg is created. Exact record creation, versioning, audit, card eligibility, and technical behavior remain with DOC-09, DOC-18, DOC-19, and the applicable owners.

When the payer intentionally expands to multi-card funding, the Checkout Workspace resolves the currently available owner-confirmed funding capabilities. Where exactly one capability is available, the Workspace proceeds directly to that capability without requiring a capability-selection step. Direct entry does not silently apply a Payment Profile, confirm an allocation, or authorize funding; the payer must still complete the applicable selection, review, and authorization actions.

Selection between capabilities is presented only where two or more owner-confirmed capabilities are simultaneously available. An unavailable capability must not appear selectable. It may be omitted or presented as unavailable only where the applicable owner has supplied or approved the explanation and presentation treatment.

Do not treat a Payment Profile as authorization, preselect it silently, or invent what makes a card or profile eligible or usable. Current-Checkout allocation must support one to six eligible cards only where that owner-confirmed capability is available. Amount/ratio editing, total reconciliation, rounding, and profile-save behavior must consume owner-supplied rules rather than define new payment or technical logic here.

| Temporary supporting action | Protected return behavior |
| --- | --- |
| Card add/change/select succeeds | Revalidate and return to the relevant single-card or allocation context with refreshed eligible card facts. |
| Card add/change/select is cancelled or fails | Return safely to the relevant funding context with retained valid intent, a clear owner-approved explanation, and an explicit recovery action; do not create or imply a Funding Leg. |
| Payment Profile select/edit succeeds | Revalidate and return to the related split-funding context with refreshed ratios and card eligibility. |
| Payment Profile select/edit is cancelled or fails | Return safely to the related split-funding context with the last valid current-Checkout allocation intent and an explicit recovery action. |

Each applicable current-Checkout allocation change remains traceable through the authoritative Funding Allocation Version history or the owner-approved equivalent audit record. Before the first Provider Submission, editable allocation facts remain subject to owner-supplied validation and revalidation rules; editing does not itself authorize payment. After the first Provider Submission, the Checkout Target and applicable obligation allocations remain locked under DOC-09: submitted or confirmed Funding Legs are not rewritten; changes are limited to eligible unexecuted funding; prior versions remain auditable; and revised execution requires revalidation and renewed payer authorization.

#### 5.20.6 Holistic Review, Payer Charge, and Authorization

Before a Provider Submission, the Workspace presents one holistic Checkout review containing the applicable Bill/Rent context, payee or landlord, Checkout Target, funding allocation, masked cards, fees, benefits, payer charge, destination/timing disclosures, evidence/readiness facts, material changes, and consequences supplied by their formal owners. Exact wording, disclosure order, and CTA labels remain with DOC-07.

Every Provider Submission requires the applicable payer authorization. A prior Checkout review, Payment Profile selection, card selection, earlier Funding Leg authorization, provider return, or Resume action does not authorize another submission. Revalidation or a material change may require renewed review and authorization before execution continues.

Payer charge presentation must separate:

| Charge category | Presentation rule |
| --- | --- |
| Accepted or confirmed payer-charge fact | Label it as accepted/confirmed only when the authoritative owner provides that fact. Associate it with the applicable confirmed financial result without treating it as obligation-funded value. |
| Submitted charge awaiting authoritative evidence | Show it as submitted and awaiting evidence. Do not present it as confirmed, failed, or available for unsafe retry. |
| Estimated charge for unexecuted funding | Mark it as an estimate subject to recalculation, eligibility, benefit, risk, and authorization rules before submission. |

Confirmed, pending, estimated, and remaining values are not automatically additive. The UI must not sum them into a misleading total or subtract payer charge from the Checkout Target.

#### 5.20.7 Financial Position and Funding Leg Progress

The payer-facing financial position must keep these concepts distinct:

| Concept | Required route-level meaning |
| --- | --- |
| Checkout Target | The obligation-funded amount pursued by the Checkout; it becomes immutable when the first Provider Submission is initiated and excludes payer charge. |
| Funding Leg obligation-funded amount | The portion of Checkout Target assigned to an authoritative Funding Leg; it is not the payer charge. |
| Confirmed value | Obligation-funded value represented by immutable Payments from confirmed Funding Legs. |
| Unconfirmed value | Submitted obligation-funded value awaiting authoritative evidence; it is not yet confirmed value and must not support a success claim. |
| Remaining Checkout Target | The authoritative outstanding obligation-funded value after confirmed Payments; it is not a payer charge and must remain distinguishable from unconfirmed submitted value. |
| Payer charge | A separate accepted/confirmed, submitted-pending, or estimated charge fact displayed under Section 5.20.6. |

Sequential execution must keep visible the current Funding Leg, completed confirmed progress, any submitted value awaiting evidence, unsuccessful or unexecuted funding, Remaining Checkout Target, applicable payer charge, current Checkout condition, and valid next actions. The presentation may emphasize the current leg while retaining access to the complete leg list and holistic financial position.

A provider or 3DS return is non-authoritative. On return, the Workspace revalidates and presents pending, execution, or result context only after evaluating authoritative current evidence. A confirmed Funding Leg advances progress using its immutable Payment and updated remaining target. Completed single-card funding presents the applicable Payment Result; if the source was otherwise unsaved, the owner-controlled Save resolver must establish same-ID Saved/current or history-only before Activity, Receipt, source return or ordinary safe exit. It must not reopen funding setup.

#### 5.20.8 Partial Funding, Pending Evidence, Recovery, Closure, and Expiry

Recovery is a condition-dependent permitted action, not a mandatory stage. It depends on authoritative Checkout and Funding Leg conditions, provider evidence, eligibility, continuability, risk/security controls, and locked versus unexecuted funding.

For a partially funded Checkout, the UI may expose only currently permitted actions:

- continue with eligible unexecuted funding;
- modify eligible unexecuted funding, followed by revalidation and renewed authorization;
- wait for authoritative evidence;
- `Close Checkout` for remaining continuation;
- return safely and use an approved later continuation entry.

Because a partially funded Checkout contains at least one confirmed Payment, `Close Checkout`, safe return, source return, Activity, Receipt, or later-continuation handoff must first preserve the source projection. A source already Saved/current retains that projection without duplicate Save. For an otherwise unsaved source, present the applicable owner-controlled Payment Result and resolve the optional Save decision before the exit or handoff: selected Save makes the same ID Saved/current, while declined, skipped, dismissed, closed or otherwise abandoned Save resolution makes it history-only. Activity and Receipt never provide the missing Save action.

`Close Checkout` ends remaining continuation under DOC-09. It does not mean or cause a refund, reversal, cancellation of the authoritative Bill/Rent source or an applicable DOC-09 Payment Obligation, Payment Instruction cancellation, invalidation of confirmed Payments, rewrite of the original Checkout Target, rewrite of Payment Applications, or rewrite/erasure/reactivation of Checkout history.

Pending-evidence presentation must:

- make no success claim;
- make no definitive failure claim without authoritative evidence;
- prevent unsafe retry or duplicate submission;
- preserve the safest valid task context where possible;
- explain the known facts and any currently available action using owner-approved wording.

Interruption never authorizes Resume automatically. After revalidation, an active, eligible, and continuable Checkout may restore overall Workspace context or the safest valid task context. An inactive, ineligible, or non-continuable Checkout presents historical or source-owner resolution. Continuation expiry and closure must preserve confirmed Payments and historical Checkout facts while preventing unavailable continuation actions.

#### 5.20.9 Late Confirmation

A delayed or late accepted provider confirmation follows an independent controlled-resolution path. It creates or returns exactly one immutable Payment for the confirmed Funding Leg while the historical Checkout remains closed, expired, or otherwise non-continuable. The confirmed Payment may remain unapplied pending controlled resolution. This route does not decide when that resolution becomes a user-facing Payment Result; when an owner-controlled result is presented for a newly confirmed Payment linked to an otherwise unsaved source, the same Save/projection resolution applies before Activity, Receipt or ordinary safe exit. No Archived-source behavior is inferred.

Late confirmation must not reopen Checkout, recreate reservations, rewrite the historical Checkout Target, authorize another submission, or expose ordinary Checkout actions such as Continue Payment, change unexecuted funding, retry, close, or restart. Activity, notification, payer disclosure, support, application, and operations treatment remains with the applicable formal owners.

#### 5.20.10 Mobile and Accessibility Requirements

The Checkout Workspace must support:

- a mobile-first single-column composition that preserves the primary financial position and next valid action;
- large text and dynamic type without clipping, overlap, or loss of action access;
- zoom and reflow without requiring two-dimensional scrolling for ordinary content;
- portrait and landscape operation with safe-area treatment;
- owner-approved minimum touch-target sizing and adequate spacing;
- sufficient contrast and non-color-only communication of progress, warnings, confirmation, pending evidence, and errors;
- reduced-motion behavior that preserves sequence and progress meaning;
- keyboard and screen-reader operation for all interactive content;
- meaningful announcements when Funding Leg progress, authoritative evidence, Remaining Checkout Target, or an error changes;
- deliberate focus restoration after card, Payment Profile, provider, 3DS, or reauthentication return;
- usable one-to-six-card allocation on mobile where multi-card capability is available, without requiring precision dragging as the sole interaction.

Accessibility presentation must preserve the semantic distinctions among Checkout Target, confirmed value, unconfirmed value, Remaining Checkout Target, and payer charge. Reading order and announcements must not imply that pending value is confirmed or that partial funding completed the Checkout.

#### 5.20.11 Decided Entry Contracts and Downstream Dependencies

The material entry questions recorded under `OQ-XDOC-007` and `OQ-XDOC-015` are decided for the current baseline:

- Instruction `Pay Now` invokes the DOC-09 Checkout Resolver and does not unconditionally create, activate, or resume a predetermined Checkout.
- An instruction-related notification enters `NOTIFICATION-DETAIL`, revalidates current state and permission, and only then exposes an owner-approved current action to that same resolver. It does not bypass Notification Detail.

The permanent Open Questions Register and derived route diagrams already record these decided dispositions. `PDM-PROP-X01` and `PDM-PROP-X02` remain historical Proposal-evidence aliases only.

These decisions do not close their remaining exact-expression, implementation, or validation dependencies. DEC-2026-037 records the accepted DOC-07 logical Semantic, Disclosure, CTA, Reference, Registry, non-executable Composition, and Bounded Domain Slice architecture. Exact Copy, IDs, CTA labels, Locale Variants, Presentation Mappings, prototype-dependent treatment, technical mappings, acceptance, implementation, monitoring, support, and operational evidence remain pending with their formal owners. No DOC-07 document, specialist guide, framework, runtime registry, schema, or admin-content model is changed here.

Other downstream dependencies remain explicit:

- DOC-06C: final Bill/Rent source CTA, eligibility, evidence, contextual disclosure, and return contract;
- DOC-07: accepted logical communication contracts apply; exact Copy, IDs, CTA labels, Locale Variants, Presentation Mappings, and prototype-dependent treatment remain pending;
- DOC-08: notification identities, recipients, channels, templates, and approved continuation treatment;
- DOC-09: payment-domain invariants, authorization boundaries, confirmation, continuation, closure, expiry, and application meaning;
- DOC-10/DOC-11: payout/reconciliation and any refund, reversal, cancellation, dispute, or chargeback treatment;
- DOC-13/DOC-14/DOC-15: benefit, risk, anti-cashout, privacy, masking, and approved-purpose rules;
- DOC-17: provider evidence and tokenization/integration mechanics; DOC-18: exact schema/version/event/audit representation; DOC-19: mechanism-neutral authentication and security controls;
- DOC-20/DOC-21/DOC-22: UAT, monitoring, support, incident, and controlled operations evidence.

#### 5.20.12 Future Validation and Acceptance Evidence

This specification does not claim that prototype, accessibility, user-validation, implementation, UAT, or acceptance evidence has passed.

Later acceptance evidence must demonstrate:

- New Checkout and Intentional Resume present their distinct required first-view context without forcing Resume into Funding;
- the persistent Workspace and financial position remain available across Funding, Review, execution, and result compositions;
- fully funded, partial, pending-evidence, unsuccessful, and historical/source-owner presentations expose only their condition-permitted actions;
- every user-facing result containing a newly confirmed Payment retains an existing Saved/current projection or resolves an otherwise unsaved source to same-ID Saved/current or history-only before Activity, Receipt, source return or ordinary safe exit, with no Save action in Activity;
- no dead-end in the primary payer journey;
- no loss of valid Checkout context through cancel, back, card/Profile support, provider/3DS, or reauthentication return;
- no duplicate or unsafe Provider Submission;
- correct payer understanding of confirmed, unconfirmed, remaining, and payer-charge values;
- clear recovery after partial funding, pending evidence, and unsuccessful execution;
- no continuation action for an inactive, ineligible, or non-continuable Checkout;
- usable keyboard, screen-reader, large-text, reflow, orientation, and mobile operation.

No numerical accessibility, performance, or usability threshold is established here. Stable acceptance and test IDs remain a later DOC-06D/DOC-20 responsibility.

| Evidence layer | Required later evidence | Current specification position |
| --- | --- | --- |
| Prototype | Demonstrate adaptive composition, New versus Resume understanding, protected return, pending evidence, sequential progress, partial funding, closure, and one-to-six-card mobile allocation. | Required later; no prototype created. |
| Accessibility validation | Test large text/dynamic type, zoom/reflow, orientation, safe areas, touch targets, contrast, reduced motion, keyboard/screen reader use, announcements, and focus restoration across supporting returns. | Required later; not yet validated. |
| User validation | Test comprehension of New Checkout versus Resume, confirmed versus unconfirmed versus remaining value, payer charge categories, partial funding, pending evidence, and `Close Checkout` consequences. | Required later; not yet validated. |
| Implementation/UAT | Verify resolver outcomes, no duplicate active continuable Checkout, revalidation gates, protected return, sequential authorization/submission, allocation traceability, locking, pending safeguards, closure/expiry, and late-confirmation separation. | DOC-20 dependency; no implementation or UAT evidence claimed. |
| Owner acceptance | Verify DOC-06C handoff facts, DOC-07 wording/disclosures, DOC-08 notification treatment, DOC-09 invariants, and DOC-17/DOC-18/DOC-19 technical mappings without changing this route boundary. | Required through later owning-document alignment, validation, and acceptance evidence. |

## 6. Route Completion Status

| Route / Area | Status | Next Required Work |
| --- | --- | --- |
| Entrance and Authentication | Defined baseline / final design, technical, and validation evidence pending | `ENTRANCE-ROOT`, the Entrance Carousel, and `ENTRANCE-PROMOTION-DETAIL` human-readable UI/UX behavior are decision-complete enough for continued alignment, alongside Login, Recovery boundary, Registration, Account Activation, Phone Verification, Identity Verification, Payment Passcode Settings, banners, protected return, and route ownership. Confirm exact DOC-07 Copy/CTA, final visual and accessibility evidence, provider mapping, and DOC-19/DOC-20 technical and test controls; these downstream dependencies do not block the `ENTRANCE-PROMOTION-DETAIL` Defined baseline. |
| Home Dashboard | `HOME-ROOT` Assigned / Partially Defined | Bounded Greeting, Important Notice, Hot Offer, Upcoming Bills / Rent, Recent Activity, resilience, accessibility, and presentation-governance behavior is defined. Confirm final visual design and later DOC-20 evidence. |
| Bills | Partially Defined in DOC-06C | Continue detailed Bills route work in DOC-06C. |
| Payment Checkout | `PAYMENT-CHECKOUT` Defined baseline | Preserve the decision-complete human-readable Workspace, resolver, funding, authorization, execution, recovery, and accessibility boundaries in Section 5.20 while exact Copy, IDs, Locale Variants, Presentation Mappings, final Bill/Rent source-owner detail, technical mappings, prototype and accessibility/user-validation evidence, implementation/UAT, acceptance, monitoring, support, and operational evidence remain pending. |
| Pay+ | `PAYPLUS-ACTION-SHEET` Payer-only re-scope / Not Final Visual Design | Four retained actions remain in their existing order and material meaning; Request Payment is retired and no replacement action is introduced. Confirm only exact iconography, measurements, spacing, blur, motion timing/easing, responsive treatment and accessibility implementation in later authorized work. |
| Offers and Rewards | Defined Behavior / Not Final Visual Design | Offers discovery and child-list behavior are defined. `REWARDS-ROOT` Active/History views, search, filters, ordering, cards, route states, `REWARD-DETAIL`, checkout return, and contextual fulfilment actions are defined. Confirm final styling, Offers label taxonomy, personalization, equal-priority fallback, and partner-specific activation methods. |
| Me | Core Account Defined / Active Archive root and Bills/Rent list / Archived-document identity provisional / Receiving Info retired from active Consumer Payee presentation | `ME-ROOT` and account/security/privacy routes remain defined. `ARCHIVED-ROOT` and DOC-06C-owned `ARCHIVED-BILLS-LIST` retain active Payer-only route access for Saved/Archived source projections; `ARCHIVED-DOCS-LIST` remains a provisional identity with no active entry or interaction. Detailed Archive/Restore and version presentation remain deferred. `RECEIVING-INFO` is retained only as a retired stable ID in non-active documentation. Support/About/Terms detail and final visual design remain open. |
| Instructions | Route Shell Defined / Not Final UI | Confirm final visual styling, card density, exact button labels, expiry/closure presentation, and payment-profile handoff behavior. |
| Activity | Route Shell Defined / Not Final UI | Screen order, accounting-style list behavior, expandable activity cards, amount direction, core detail sections, and download actions are defined. Confirm final visual styling, field density, search/filter behavior, grouping behavior, and empty-state copy. |
| Receipts & Statements | Root and Preview Behavior Defined / Not Final PDF Design | `RECEIPTS-ROOT` search, list, Payer-facing transaction-direction indicator, empty state, direct download, shared PDF preview, and return behavior are defined. Confirm PDF layout/design, export naming, sharing controls, statement schedule, and re-issue workflow. |
| Reminders | Partially Defined in DOC-06C | Ordinary bill/rent reminders remain separate from payment instruction action alerts. |
| Payment Profile / Cards | Two-Tab Route Baseline Defined / Not Final Visual Design | Confirm final card styling, field density, empty-state copy, PSP tokenization return behavior, and permitted card metadata. |
| Referral | Child-Screen Behavior Defined / Not Final Visual Design | `REFERRAL-ROOT`, role-sensitive entitlement list/detail/claim screens, registration attribution handoff, reusable sharing, qualification display, privacy boundary, two-tab reward list, exceptional admin hold presentation, and canonical issued-reward handoff are defined. Confirm final styling and open campaign parameters. |
| Notifications | Defined Baseline / Not Final Visual Design | `NOTIFICATION-ROOT`, Inbox, Detail, Settings, entry/return behavior, filters, cards, read/archive behavior, signal separation, and domain handoffs are defined. Confirm final styling, search matching, archive visibility/access presentation, provider operations, and templates; notification records follow the accepted indefinite-retention direction subject to DOC-15 and Legal/Privacy lawful-scope, exception, restricted-class and prohibited-sensitive-data controls. |
| More | Defined Baseline / Not Final Visual Design | `MORE-ROOT` Normal and Manage modes, 8-slot maximum, protected More entry, account-level preferences, current-default restore, availability precedence, secondary-service handoffs, accessibility, and save/return behavior are defined. Confirm final styling and optional replacement Undo. |

## 7. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06B-001 | What exact Pay+ iconography, measurements, spacing, blur strength, motion timing/easing, responsive treatment and accessibility implementation should be used within the confirmed four-action Payer-only baseline? | Product / Design / Payments | Partially open; composition, order, material meaning and Request Payment retirement are settled |
| OQ-06B-002 | What final visual design and remaining child-route UI should apply to Me, the active `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST` route chain, any later-authorized `ARCHIVED-DOCS-LIST` presentation, More shortcut management, and Support, while preserving the retired Consumer Receiving Info boundary? More behavior, Account Information, Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, and active Archive root/list access are defined; detailed Archive/Restore and version presentation remain deferred and Receiving Info remains non-active documentation lineage only. | Product / Design / Privacy / Security / Operations | Partially open |
| OQ-06B-003 | What final styling and optional post-replacement Undo behavior should apply to the defined `MORE-ROOT` shortcut-management experience? | Product / Design / Operations | Partially open; capacity, protected More, reorder, save, restore, owner-approved default and permitted Admin-configuration behavior defined |
| OQ-06B-004 | What priority, collapse, expiry, and routing rules should apply to Important Notice / Action Required cards? | Product / Operations / Compliance | Resolved for Home: one Inbox-backed item, source-provided ordering, session-scoped dismiss, canonical Detail/action routing, and zero-state behavior defined; final visual design and DOC-20 evidence pending |
| OQ-06B-005 | What final visual styling, implementation treatment, and DOC-20 evidence should apply to the defined Home Hot Offer placement? | Product / Design / Growth / Operations | Partially open; Offer-only scope, maximum five, Admin-selected fixed/random order, five-second configurable rotation, interaction stops, canonical restrictions, and `OFFER-DETAIL` handoff are defined |
| OQ-06B-006 | Retired: Founder confirmed there is no production Request runtime or legacy Request deep-link data requiring a reader, adapter or fallback. | Product / Design / Operations | Answered/retired |
| OQ-06B-007 | What exact visual styling, field density, expiry/closure wording, and card/payment-profile handoff should distinguish deliberate Payment Instructions from incomplete Checkout Workspaces in the shared Instructions route? | Product / Design / Payments / Security | Open |
| OQ-06B-008 | What exact Payment Profile card styling, field density, empty-state copy, tokenization return UX, and permitted PSP card metadata should be used? Two-tab `Cards` / `Profiles` structure is confirmed. | Product / Design / Payments / Security | Partially open |
| OQ-06B-009 | What exact Activity visual styling, field density, search/filter behavior, grouping behavior, empty-state copy, lifecycle timeline wording, and transaction-detail display should be used? Screen order, expandable entry behavior, amount direction, and core actions are defined. | Product / Design / Payments / Operations | Partially open |
| OQ-06B-010 | What final receipt/statement PDF layout and visual design, export naming, sharing control, statement schedule, and re-issue workflow should be used? Required content follows DOC-08; root search, direct download, and shared in-app preview behavior are defined. | Product / Finance / Legal / Operations | Partially open |
| OQ-06B-011 | What final My Rewards icon, reward/offer card styling, Offer label taxonomy for Pay+ Offers and Partner Offers, personalized ranking scope, membership destination, partner-specific reward activation, and Card Offers randomization cadence should apply? The `My Rewards` label and Rewards behavior are confirmed, and this question does not reopen the settled Pay+ action composition. | Product / Design / Growth / Privacy / Commercial | Partially open |
| OQ-06B-012 | What final responsive measurements, short-viewport treatment, first-use-cue persistence and animation implementation, exact Copy/CTA presentation, screen-reader behavior, technical scheduling/synchronization, and DOC-20 evidence should implement the defined Entrance Carousel and `ENTRANCE-PROMOTION-DETAIL` behavior? | Product / Design / Content / Growth / Security / Privacy / Engineering / QA / Operations | Partially open and non-blocking to the Defined baseline; capacity, sequence, timing, interaction, Promotion/Feature scope, image-first detail, Back, inline Terms, optional CTA, source-change suspension, and same-item return are defined |
| OQ-06B-013 | What final OTP constants, provider-result mapping, weak-code/retry/lockout rules, support-assisted passcode-recovery proof and waiting period, credential storage, session-revocation mechanisms, and final visual design apply to the defined `PHONE-VERIFICATION`, `IDENTITY-VERIFICATION`, and `PAYMENT-PASSCODE-SETTINGS` flows? DOC-17 owns applicable provider-integration mappings; `OQ-19-001` retains exact security mechanisms with Security/Engineering; DOC-06B retains recovery route behavior; DOC-15 owns approved-purpose privacy/access requirements; DOC-21 owns support operations; DOC-22 owns only owner-permitted queue/workflow/configuration execution; and DOC-20 must derive implementation tests. | Security / Engineering / Compliance / Privacy / QA / Operations | Partially open; product behavior, five identity labels, HK-only phone baseline, six-digit passcode flows, and return behavior confirmed |
| OQ-06B-014 | What exact Authentication Outcome IDs, Resolution mappings, Message IDs, approved user-facing messages, CTA mappings, disclosure levels, notification treatment, and technical outcome/event mappings should populate the mandatory DOC-07 Authentication slice? | Product / Content / Design / Security / Privacy / Support | Open; route-level Outcomes and Resolution Strategies defined, exact DOC-07/DOC-08/DOC-18 mappings pending |

## 8. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 1.1.0 | 2026-08-22 | Drafted the approved Tier 3 Bill current-context and deliberate-resolver return expression without adding a route, notification, automatic transition, stale Resume, authorization, or Provider Submission; preserved the integrated `ENTRANCE-PROMOTION-DETAIL` Defined baseline unchanged. |
| 1.0.2 | 2026-08-21 | Integrated the Founder-authorized `ENTRANCE-PROMOTION-DETAIL` Defined baseline status transition, preserving the current route, owner, Bills, security, and open-mechanism baseline while retaining the downstream deferrals as non-blocking. |
| 1.0.1 | 2026-08-21 | Aligned Recovery, provider/tokenization, PCI, risk and security handoffs with the reviewed DOC-19 contract and existing owner boundaries without changing routes, statuses, product behavior or open mechanism decisions. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 0.1.57 | 2026-08-13 | Clarified registration-attempt expiry versus indefinite record retention and made identity-provider handoff wording provider-neutral without selecting a provider. |
| 0.1.55 | 2026-08-12 | Stage 8 correction: removed Archive treatment from incomplete Checkouts and Payment Instructions, including the Archived filter/action; retained DOC-09 continuation, Close and Expiry semantics; and replaced the stale DOC-09 v1.1.1 pin with the current Founder Working Baseline reference. |
| 0.1.56 | 2026-08-12 | Applied the Founder-settled indefinite-retention boundary to Privacy & Data route wording without adding a deletion or disposition mechanism. |
| 0.1.54 | 2026-08-12 | Stage 8 correction: removed retired Requests references from active shortcut and completion-status tables, restored the pre-existing `payment instructions / 付款指示` Copy provenance, and retained pay-later as a Payment Instruction concept rather than a newly selected route/header label. |
| 0.1.53 | 2026-08-12 | Stage 8 ownership correction: removed residual generic or joint DOC-22 policy authority from Payment Instruction, Payment Profile, receipts/statements, identity and passcode-recovery handoffs; retained formal-owner policy and truth while limiting DOC-22 to owner-permitted execution. |
| 0.1.52 | 2026-08-12 | Stage 8 Wave 2 Draft: preserved the settled four-action Pay+, Category-first Bill and separate Rent routes; removed nonexistent Request runtime/readers/deep-link handling; corrected active/historical structure; and retained the same-ID Save/Activity and Archive three-way boundaries without adding a route, action, status or ID. |
| 0.1.51 | 2026-08-06 | Defined the public Entrance Carousel and `ENTRANCE-PROMOTION-DETAIL` human-level UI/UX: full-width `4:5` image-only presentation, dots, five-second Crossfade, swipe/tap separation, first-use cue, five-item priority/manual sequence, Promotion/Feature-only scope, Back-only image-first detail, inline Terms, optional CTA, same-item return, source-change suspension, and bounded owner handoffs while preserving route statuses and authentication behavior. |
| 0.1.50 | 2026-08-05 | Defined the approved HOME-ROOT Greeting, Inbox-backed Important Notice, Admin-selected Hot Offer, payer-only Upcoming Bills / Rent, completed-outcome Recent Activity, section-level resilience, accessibility, and presentation-governance contracts while preserving source ownership, Partially Defined Home status, and Defined PAYMENT-CHECKOUT. |
| 0.1.49 | 2026-08-05 | Updated active `PAYMENT-CHECKOUT` references to Defined baseline, recognized completed PDM-WI-003 register/diagram alignment and the DEC-2026-037 logical communication architecture, and retained exact-expression, source-owner, technical, prototype, validation, implementation/UAT, acceptance, monitoring, support, and operational dependencies. |
| 0.1.48 | 2026-08-05 | Replaced the superseded mandatory Authentication Matrix reference with the DOC-07 Authentication Bounded Domain Slice and linked Semantic, Disclosure, and CTA Contracts while preserving route, placement, destination, entry/return, adaptive-presentation ownership and open downstream mappings. |
| 0.1.47 | 2026-08-04 | Defined Instruction `Pay Now` and instruction-notification entry through the owner-approved Checkout Resolver, required `NOTIFICATION-DETAIL` and current revalidation before any notification payment CTA, removed the X01/X02 route-level authority gaps, and preserved separate Payment Instruction/Checkout identity, retained history, no stale authorization, and no silent funding/submission behavior. |
| 0.1.46 | 2026-08-03 | Removed superseded mandatory Payment Profile wording and aligned profile presentation with owner-confirmed current-Checkout allocation, capability-aware direct entry, and required within-capability selection or configuration. |
| 0.1.45 | 2026-08-03 | Added mechanical cross-references from the reviewed Checkout Workspace contract to the derived route map and permanent Open Question IDs while preserving the accepted UI/UX and DOC-09 meaning. |
| 0.1.44 | 2026-08-03 | Replaced the second Checkout illustration with a concise payer-visible Bill/Rent Pay-to-funding, review, authorization, Funding Leg progress, result, and safe-resolution journey while preserving the separate decision map, adaptive UI contract, domain invariants, exclusions, and owner boundaries. |
| 0.1.43 | 2026-08-03 | Corrected the illustrative Checkout payer-experience flow so resolver, Resume, protected-return, evidence, result, and recovery paths preserve condition-aware actions; added the minimum adaptive UI contract for New, Resume, funding, review, execution, completion, recovery, pending, unsuccessful, and historical/source-owner presentations without creating fixed steps, routes, states, or technical contracts. |
| 0.1.42 | 2026-08-03 | Replaced the oversized illustrative Checkout payer-experience diagram with a concise top-to-bottom Bill/Rent Pay-to-result-and-recovery journey while preserving the existing Checkout, funding, protected-return, late-confirmation, and unresolved-entry-contract meaning. |
| 0.1.41 | 2026-08-03 | Clarified the DOC-09/DOC-17/DOC-06B/DOC-18/DOC-07 condition, evidence, presentation, and technical-state boundary; added the illustrative adaptive payer-experience flow; consolidated single- versus multi-capability funding fallback; distinguished the entry/revalidation decision map; and strengthened acceptance intent without changing the accepted `PAYMENT-CHECKOUT` product meaning. |
| 0.1.40 | 2026-08-03 | Defined the approved PDM-WI-003 `PAYMENT-CHECKOUT` persistent Workspace route UX, including Bill/Rent resolver entry, New/Resume/protected re-entry, adaptive presentation, funding and allocation treatment, holistic review and authorization, Funding Leg progress, financial-position separation, recovery/closure/expiry, independent late confirmation, accessibility, owner handoffs, exclusions, and future validation dependencies; route status remained `Partially defined`. |
| 0.1.39 | 2026-07-31 | Aligned checkout ownership and Instructions-route presentation with DOC-09 Payment Domain Architecture, keeping deliberate Payment Instructions distinct from incomplete Checkout Workspaces. |
| 0.1.38 | 2026-07-29 | Adopted the capability-aware Outcome-to-Resolution framework across the AUTH family; defined the full `AUTH-RECOVERY` product flow, screen states, resolution matrix, security/support boundaries, and protected return without changing existing authentication decisions. |
| 0.1.37 | 2026-07-28 | Defined Phone Verification, five-state Identity Verification, processing/dashboard banners, six-digit Payment Passcode Set/Change/Reset, phone-based reset recovery, return behavior, admin reset boundaries, and technical-owner TBCs; removed superseded four-label and voluntary re-verification wording. |
| 0.1.36 | 2026-07-28 | Corrected the first-time identity-verification passcode rule, synchronized all three Account Activation child-route references, and marked Payment Passcode Settings screen/security details plus DOC-19/DOC-20 handoffs as pending. |
| 0.1.35 | 2026-07-28 | Clarified Account Activation as an orchestration route, established Account Profile and Account Security as the canonical parents of reusable verification/passcode routes, aligned origin-aware return behavior, and simplified the hierarchical Authentication, Account Activation, and Me route-map handoffs. |
| 0.1.34 | 2026-07-28 | Replaced `AUTH-ENTRY` with `ENTRANCE-ROOT`; defined public Entrance content, Fast/Full Login, Recovery, registration attempts, restricted-account creation, Account Activation, persistent banner mapping, protected return, login-name removal, and the mandatory-but-open authentication outcome/message handoff. |
| 0.1.33 | 2026-07-27 | Preserved the accepted unique-primary-email and multiple-login-method model, restricted-account handoff, deferred financial activation, and Account Security Set/Change Password and Google/Apple link/unlink behavior while keeping full authentication-route UI pending. |
| 0.1.32 | 2026-07-27 | Defined the `NOTIFICATION-ROOT` family, Inbox/Detail/Settings behavior, Home and Me entries, source-aware returns, filters, card/detail rules, read/archive handling, badge semantics, settings, signal separation, and data/admin handoffs. |
| 0.1.31 | 2026-07-27 | Defined `MORE-ROOT` Normal and Manage Shortcuts modes, the 8-slot maximum with protected More, account-level user preference override, accessible reorder/add/remove controls, current-default restore, availability precedence, secondary-service handoffs, save/return/failure behavior, and data/admin boundaries. |
| 0.1.30 | 2026-07-27 | Defined the Pay+ action-sheet five-action layout principle, animation and accessibility baseline, category-scoped Bills handoffs, Add/Continue completion logic, payee-to-payer Request Payment meaning, contextual payer-to-payee linking boundary, availability rules, return behavior, configuration limits, and data-signal handoff. |
| 0.1.29 | 2026-07-26 | Defined `ARCHIVED-ROOT`, aligned the `Archived Bills & Rent` label, clarified obligation-versus-evidence placement, personal archive visibility, document-to-obligation handoff, DOC-06C ownership, and hierarchical route-map references. |
| 0.1.28 | 2026-07-26 | Replaced `ARCHIVED-EVIDENCE-LIST` with the `ARCHIVED-ROOT` family, defined `ARCHIVED-DOCS-LIST` screen behavior and access boundary, and registered `ARCHIVED-BILLS-LIST` for later drafting. |
| 0.1.27 | 2026-07-26 | Assigned stable destination IDs for authentication entry, Home, Pay+, More, Notification Inbox, and checkout handoff; defined the pre-login Login/Register baseline and normal/contextual post-authentication routing while leaving detailed UI pending. |
| 0.1.26 | 2026-07-26 | Confirmed the canonical request lifecycle and role-facing labels, and separated request events, route views, evidence status, obligation readiness, linked cases, payment/payout status, and archive visibility. |
| 0.1.25 | 2026-07-26 | Added the canonical route-register handoff, synchronized route completion language, required passcode/reauthentication for prominent sensitive reveal and material sensitive changes, retained ordinary authenticated document viewing/download without an extra prompt, and strengthened Receiving Info reveal/edit controls. |
| 0.1.24 | 2026-07-23 | Replaced singular Receiving Details with the `RECEIVING-INFO` route family, multiple private reusable profiles, list/card/detail/setup behavior, trailing swipe actions, archive/version rules, readiness labels, proof and masking boundaries, destination snapshots, request-change rules, linked-payee notification handoff, and authorization freeze. |
| 0.1.23 | 2026-07-22 | Defined `ACCOUNT-PROFILE`, reusable `IDENTITY-VERIFICATION`, `ACCOUNT-SECURITY`, `PAYMENT-PASSCODE-SETTINGS`, and `PRIVACY-DATA-CONTROLS`, including status/CTA behavior, immutable login name, cross-channel contact changes, passcode/2FA/recovery boundaries, trusted-device removal, privacy requests, protected export, and account closure flow. |
| 0.1.22 | 2026-07-22 | Defined permanent `ME-ROOT` route behavior, fixed section order, masked Account Information and passcode-gated reveal, Security & Privacy child routes, Bills and existing-route handoffs, Receiving Details, Archived Documents, Preferences, Support, About/Terms, logout, state/return rules, and the separate More shortcut-management boundary. |
| 0.1.21 | 2026-07-21 | Defined `My Rewards` Active/History views, search and instrument filters, ordering, reward-card fields, full `REWARD-DETAIL` content and terms, contextual fulfilment actions, checkout-detail return, credential/use boundary, route states, and secure return behavior. |
| 0.1.20 | 2026-07-21 | Defined Referral child-screen behavior for role-sensitive referrer/referee entitlements, two list tabs, reward-card fields and privacy boundary, detail and claim UI, idempotent success handling, canonical reward handoff, and exceptional admin-held `Under Review` presentation. |
| 0.1.19 | 2026-07-21 | Defined the Referral route family, reusable share behavior, registration attribution handoff, qualification display, referrer entitlement list/detail/claim flow, role-sensitive reward handoff, privacy boundary, and distinction between referral entitlements and canonical issued reward instruments. |
| 0.1.18 | 2026-07-20 | Defined the three Offers child-list baselines, clarified offer card versus payment card versus Card Offer terminology, added multi-collection membership, root duplicate suppression, stable collection-specific ordering, list states, return preservation, and DOC-09/DOC-13 checkout handoff. |
| 0.1.17 | 2026-07-17 | Defined Offers, child collection, Rewards, and partial Referral route boundaries; added a product-level route register and source/action/destination/return transitions, section limits/layout, View More list screens, full-screen offer/reward detail behavior, redemption-state changes, cross-route handoffs, and promotion-engine ownership separation. |
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
