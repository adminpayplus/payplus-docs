---
document_id: DOC-06
title: User Journey, UX Flow & Service Blueprint
version: 0.21.16
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
last_updated: 2026-07-22
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

# DOC-06 - PayPlus User Journey, UX Flow, and Service Blueprint Family

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06` |
| **Title** | User Journey, UX Flow & Service Blueprint |
| **Version** | `0.21.16` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>Compliance Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-07-22` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-06D UX Requirements, Acceptance Criteria & Test Matrix<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-15 Privacy, Data Protection & Record Retention<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow |

---

## 1. Purpose

This parent document governs the DOC-06 family for PayPlus user journeys, UX flow, navigation, route taxonomy, service blueprint touchpoints, and UX acceptance mapping.

PayPlus is an evidence-backed payment platform that allows payers and payees to create, view, link, authorize, request, receive, and track eligible bill, invoice, fee, rent, tenancy, domestic service, and other approved obligation payments.

DOC-06 is now a family index and governance map. Detailed content is split into DOC-06A to DOC-06D so unfinished route specifications can be tracked clearly without overloading one document.

This modularization does not change PayPlus product scope, payment behavior, risk controls, privacy rules, or operational decisions. It only separates ownership and navigation.

---

## 2. Scope and Baseline

The DOC-06 family defines:

- payer, payee, admin, operations, and system journeys;
- logged-in navigation and route taxonomy;
- Bills, rent, tenancy, evidence, reminder, activity, and request/receive UX module behavior;
- user-facing state visibility and handoff points to payment, evidence, notification, privacy, risk, data, and admin owner documents;
- UX requirements, acceptance criteria, and test-readiness mapping.

The DOC-06 family does not own detailed payment processing, payout, refund, notification templates, evidence verification algorithms, data schema, security architecture, or admin workflow details. Those details remain with their owning documents.

Tenancy, rent, bill, fee, payee-created request, payer-created payment, domestic helper, driver, personal service, and approved-obligation journeys remain baseline scope where supported by acceptable evidence and enabled controls.

### 2.1 MVP Scope Summary

The DOC-06 family keeps the following MVP user-journey scope as the official baseline:

- payer and payee registration, login, verification, dashboard, and role-appropriate account journeys;
- payer-created and payee-created bill, invoice, fee, tenancy, rent, domestic service, personal service, and approved-obligation setup;
- payee-created request creation, evidence-gated delivery, payer review, payer acceptance or rejection, exception/support handoff where needed, and payment authorization;
- payer-created obligation setup, evidence-backed payment, optional payee invitation/linking, and status visibility;
- evidence capture, OCR/autofill review, user correction, evidence verification outcome visibility, duplicate/reused evidence handling, and admin review touchpoints;
- Bills, rent, tenancy, reminder, activity, request/receive, dashboard, Pay+, shortcut, notification, receipt, failure, exception, and support handoff journeys;
- controls preventing wallet, stored-value, cashout, unsupported peer-to-peer, lending, and automatic recurring-payment journeys.

### 2.2 User Role Summary

| Role | Description | MVP Login? | Key Journey Responsibility |
| --- | --- | ---: | --- |
| Payer | User who reviews, accepts, rejects, raises approved support/exception cases where needed, and authorizes payment. | Yes | Create obligations, review requests, authorize payment, track status. |
| Payee | User who receives payments or creates payment requests. | Yes | Create requests, upload evidence, send requests, optionally adopt/link payer-created records, track status. |
| Admin / Operations | Internal user who reviews accounts, evidence, requests, risk, disputes, and exceptions. | Yes | Review, approve, reject, hold, investigate, configure, and audit. |
| System | Automated services handling status changes, notifications, linking, validation, audit events, and integrations. | No | Route, link, notify, validate, and record events. |

### 2.3 UX Surface Summary

The DOC-06 family covers payer, payee, admin, and system UX/service surfaces at the human-readable product level:

| Surface | Covered Examples | Main DOC-06 Family References |
| --- | --- | --- |
| Payer UX | registration, login, dashboard, Bills/To Pay, request review, evidence review, payment handoff, deferred instruction handoff, split-payment status, receipts, notifications, account basics. | DOC-06A / DOC-06B / DOC-06C |
| Payee UX | registration, login, dashboard, Bills/To Receive, request creation, request delivery, payer response visibility, evidence management, payout/settlement visibility, receipts, notifications, account basics. | DOC-06A / DOC-06B / DOC-06C |
| Admin UX touchpoints | admin login, review queues, evidence/OCR review, risk review, dispute/exception handling, dashboard placement controls, audit visibility. | DOC-06A handoff; DOC-22 owns detail |
| System service touchpoints | record creation, participant linking, invitation routing, evidence linking, OCR/autofill, verification routing, duplicate detection, status updates, notification events, audit events, admin queue routing. | DOC-06A handoff; DOC-18/DOC-22 own detail |

---

## 3. DOC-06 Family Governance Map

| Document | Governs | Does Not Govern | Current Completion Status |
| --- | --- | --- | --- |
| DOC-06 | Parent UX/service-blueprint overview, family map, scope boundaries, prohibited journey controls, family decision summary, dependencies, and split governance. | Detailed route specs, detailed component behavior, full acceptance matrix. | Active parent baseline. |
| DOC-06A | Core payer, payee, admin, system, evidence, review, authorization, status, visibility, notification, receipt, failure, and exception service journeys. | Global app navigation taxonomy or detailed Bills route UI. | Working baseline; service-blueprint refinement still needed. |
| DOC-06B | Navigation IA, dashboard structure, bottom navigation, Pay+ action sheet, route/screen/component/action standards, route registry, and route completion status. | Deep Bills/rent/tenancy behavior or payment checkout logic. | Partially defined; non-Bills routes remain incomplete and must be drafted later. |
| DOC-06C | Bills, fees, rent, tenancy, To Pay, To Receive, cards, detail pages, activity, reminders, evidence UX, linking, role-aware actions, and Bills-route handoffs. | Checkout processing, full evidence verification logic, final data model, or admin queue design. | Partially defined; Bills module has strong baseline but not final UI. |
| DOC-06D | UX requirement IDs, acceptance criteria, route/action/state/event/test mapping, and UX test-readiness tracking. | Business policy decisions or implementation tickets. | Skeleton/initial baseline; full test matrix must be expanded before AI build-execution conversion. |

Formal child documents use DOC-06A to DOC-06D. They inherit DOC-06 source-of-truth tier unless a child document explicitly states otherwise.

### 3.1 Single-Owner Rule for Future Drafting

Each route, function, status, screen, or flow should have one primary owning document. Other DOC-06 family documents may reference it, define entry or handoff behavior, or list dependencies, but must not duplicate the same detailed requirements.

Use this rule before adding new content:

| If the change is mainly about... | Primary owner | Other docs may only... |
| --- | --- | --- |
| User journey, service step, lifecycle, status meaning, exception path, or role responsibility | DOC-06A | Link to the journey or status and define navigation handoff only. |
| Navigation, route ID, dashboard placement, shortcut, bottom navigation, global non-Bills route shell, route-level UX behavior, or IA | DOC-06B | Reference domain rules and defer detailed lifecycle, payment, evidence, privacy, data, and operations behavior to the owning document. |
| Bills, rent, tenancy, evidence UI, reminder UI, activity UI, role-aware Bills actions, or Bills-route handoff | DOC-06C | Reference global navigation or lifecycle rules without restating them. |
| UX requirement ID, acceptance criterion, route/action/state/event/test mapping, or test readiness | DOC-06D | Reference source requirements and avoid adding new product behavior. |

If a topic appears to belong to more than one child document, update the parent route matrix first to identify the primary owner and reference-only documents before drafting detailed content.

---

## 4. Route Completion Status Matrix

This matrix prevents the split from creating a false impression that all routes are complete.

| Route / Area | Primary Owning Doc | Reference / Handoff Docs | Status | Notes |
| --- | --- | --- | --- | --- |
| Home Dashboard | DOC-06B | DOC-06A for journey touchpoints; DOC-13/DOC-15/DOC-22 where relevant | Partially Defined | Section order, shortcut baseline, Featured carousel, Important Notice, and Recent Activity summary are defined; exact UI and card rules remain open. |
| Bottom Navigation | DOC-06B | Child route owners for destination behavior | Partially Defined | Home, Bills, Pay+, Offers, Me baseline is defined; sub-route detail remains open. |
| Pay+ Action Sheet | DOC-06B | DOC-06A for journey entry; DOC-06C/DOC-09 for Bills/payment handoff | Partially Defined | Working action set is defined but final visual order, disabled states, and eligibility copy remain open. |
| Bills / Rent / Tenancy | DOC-06C | DOC-06B for route entry; DOC-06A for lifecycle; DOC-09/DOC-12 for payment/evidence detail | Partially Defined | BILLS-PAY, BILLS-RECEIVE, BILLS-ACTIVITY, BILLS-EVIDENCE, and BILLS-REMINDER have working baseline rules. |
| Payment / Checkout | DOC-09 | DOC-06A/DOC-06C for entry, return, and high-level handoff only | Partially Defined | DOC-09 owns checkout behavior; DOC-06 family should not duplicate checkout screen detail. |
| Requests | DOC-06B | DOC-06A for request lifecycle; DOC-06C for Bills/rent request implementation; DOC-08 for notification routing | Route Shell Defined / Not Final UI | Requests connect parties to bill/rent/tenancy/obligation contexts and are not payments. DOC-06B now defines the standalone route shell; detail layout, resend/reminder limits, and linked Bills/rent routing remain open. |
| Instructions | DOC-06B for route shell; DOC-09 for payment-instruction behavior | DOC-06A/DOC-06C for entry or return touchpoints | Partially Defined | Dashboard/shortcut route is identified; detailed route UX remains incomplete. |
| Activity and Receipts & Statements | DOC-06B for global route shells | DOC-06A for receipt/history touchpoints; DOC-06C for bill/rent-specific activity; DOC-08 for receipts/statements; DOC-09/DOC-10/DOC-11 for payment/payout/refund facts | Working Baseline / Not Final Visual Design | Global Activity and Receipts & Statements remain separate. `RECEIPTS-ROOT` owns search and the document list; `RECEIPT-DETAIL` / `STATEMENT-DETAIL` open the shared in-app PDF preview, while list-level `Download` acts directly. |
| Reminders | DOC-06C for bill/rent reminders | DOC-06B for shortcut/route shell; DOC-08 for notifications; DOC-09 for payment-instruction reminders | Partially Defined | Bill/rent reminder list/detail route is defined; relationship to payment-instruction reminders remains open. |
| Offers and Rewards | DOC-06B for route shells and placement | DOC-13 for promotion, entitlement, instrument, lifecycle, and fulfilment logic; DOC-09 for checkout | Offers Child Lists and Rewards Defined / Not Final Visual Design | `OFFERS-ROOT` governs sectioned discovery; its child lists use multi-collection membership, root duplicate suppression, and stable ordering. `REWARDS-ROOT` governs issued rewards through Active and History views; `REWARD-DETAIL` shows full details and terms but does not create a second checkout path. `BILLS-PAY` remains an external DOC-06C handoff and DOC-09 owns same-screen payment-card/profile, eligible-reward selection, quote recalculation, and authorization review. |
| Me / Account | DOC-06B for route UX | DOC-06C/DOC-08/DOC-10/DOC-12/DOC-15/DOC-18/DOC-19/DOC-21/DOC-22 for domain handoffs | Core Account Child Routes Defined / Other Details Pending | `ME-ROOT`, Account Information, reusable Identity Verification, Login & Security, Payment Passcode Settings, and Privacy & Data behavior are defined. Receiving Details, Archived Documents, Support/About/Terms, and final visual design remain pending. |
| Payment Profile / Cards | DOC-06B for route shell | DOC-09/DOC-15/DOC-19 for checkout, privacy, and security detail | Route Shell Defined / Not Final UI | Shortcut opens `PAYMENT-PROFILE-ROOT`; route manages tokenized cards and saved split-card profiles, while checkout remains DOC-09. |
| Referral | DOC-06B for route UX and registration handoff | DOC-13 for referral, qualification, entitlement, and reward logic | Child-Screen Behavior Defined / Not Final Visual Design | `REFERRAL-ROOT`, role-sensitive referrer/referee entitlement list/detail/claim screens, reusable sharing, registration attribution handoff, qualification display, and issued-reward handoff are defined. |
| More | DOC-06B | Destination owners for launched routes | Boundary Defined / Route Detail Pending | More manages dashboard shortcut arrangement, reorder, restore-default behavior, overflow, and secondary services; it does not replace Me. |

---

## 5. Product Journey Summary

PayPlus supports two-sided payment journeys between a payer and a payee.

A payment may originate from either side:

- a payee may create a bill, invoice, fee, rent, tenancy, agreement, employment/service record, statement, or other evidence-backed payment request and send it to a payer; or
- a payer may create a bill, invoice, fee, rent, tenancy, employment/service, or payment obligation record, link or invite a payee, and push payment to that payee.

In all cases:

- the payment must be linked to acceptable evidence unless an approved exception applies;
- the payer must review the request or payment context before payment;
- the payer must explicitly authorize payment before funds are charged or moved;
- the payee may view linked request/payment context when they are a platform user;
- admin, operational, or risk controls may apply;
- the system must maintain linked records, status history, receipts, and audit events;
- PayPlus must not operate as a wallet, stored-value account, cashout product, or unsupported peer-to-peer transfer service.

Detailed journeys are in DOC-06A. Bills/rent/tenancy route behavior is in DOC-06C.

---

## 6. Cross-Document Ownership Boundaries

| Topic | UX Family Role | Owning Detail Document |
| --- | --- | --- |
| Content, wording, disclosures, authorization language | DOC-06 identifies touchpoints. | DOC-07 |
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
| Admin dashboard, queues, overrides, configuration | DOC-06 identifies admin/operations touchpoints. | DOC-22 |

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
| Core journey, request lifecycle, review, exception, status, visibility, and service blueprint questions | DOC-06A |
| Dashboard, bottom navigation, Pay+ action sheet, route taxonomy, global shortcut and placement questions | DOC-06B |
| Bills/rent/tenancy cards, details, activity, reminders, evidence, linking, and role-aware action questions | DOC-06C |
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

---

## 10. Master Decision Summary

This parent summary preserves the DOC-06 family decisions. Detailed decisions also appear in the child document that owns the relevant area.

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
| Promotion discovery, issued-reward management, and referral participation use separate DOC-06B routes. Referral sharing, registration attribution, qualification progress, role-sensitive entitlement claiming, two-tab Referral Rewards behavior, and canonical issued-reward handoff are defined; commercial availability and campaign conditions remain governed by DOC-13. | Working Baseline / Not Final Visual Design |
| Home Dashboard is task-first and uses bottom navigation `Home`, `Bills`, `Pay+`, `Offers`, and `Me`. | Designated Layout Baseline |
| `Pay+` is the preferred center bottom-nav action label. Working baseline actions are Pay a Bill / Fee, Pay Rent, Add Bill / Rent, Continue Payment, and Request Payment. | Working Baseline / Not Final |
| `Add Bill / Rent` includes scan QR, upload evidence, and manual entry inside the setup flow; QR/upload is not a standalone instant-payment action. | Working Baseline |
| `Request Payment` should appear by default for all users unless the feature/module is disabled or the account is restricted. | Working Baseline |
| MVP dashboard shortcuts are Requests, Instructions, Bills & Tenancies, Receipts, Reminders, Cards, Referral, and More. | Designated Layout Baseline |
| Dashboard shortcuts must be admin-configurable and user-reorderable, with user settings overriding system default and restore-default support. | Confirmed |
| Important Notice / Action Required is a combined swipeable section, collapsible by user, hidden when empty. | Confirmed |
| Featured / What's New / Hot Offer is one combined admin-controllable carousel at this stage. | Confirmed |
| Recent Activity dashboard section displays limited recent transactions with date, item, action, amount, and status. | Confirmed |
| Global Activity is an account-level event/lifecycle route, while Receipts & Statements is a file/document route for receipt and statement files. Proof of payment remains a direct document action from the relevant Activity context for MVP. They must not be merged into one generic history hub. | Working Baseline / Not Final UI |
| Activity root uses accounting-style entries with date, obligation/payment name, counterparty, positive/negative amount direction, and mapped status. Tapping an entry expands available actions before routing to `ACTIVITY-DETAIL`. | Working Baseline / Not Final UI |
| Receipts & Statements uses `RECEIPTS-ROOT` as the searchable list. `View` opens a shared in-app PDF preview through `RECEIPT-DETAIL` or `STATEMENT-DETAIL`; `Download` downloads directly. Exact PDF design remains open. | Working Baseline / Not Final PDF Design |
| The dashboard flow and layout are designated for MVP discussion, but final UI design, exact component specification, and exact route-level screen specification are not finalized. | Confirmed |
| Bills tab working baseline uses `To Pay` and `To Receive` views, route/subsection IDs, bill/rent cards, detail pages, bill/rent-specific activity sub-routes, evidence status, archive behavior, and Add Bill / Rent setup flow. | Working Baseline / Not Final |
| `BILLS-PAY` is the formal payer-side route replacing the earlier informal `To Pay` view description; `BILLS-RECEIVE` is the formal payee-side request/receive route and must not show payer-side `Pay` actions. | Working Baseline / Not Final |
| Payment/checkout UI behavior is primarily governed by DOC-09; DOC-06 governs Bills-route entry points, route handoff, and high-level navigation behavior. | Working Baseline / Not Final |
| Bills activity route uses `BILLS-ACTIVITY` and `BILLS-ACTIVITY-DETAIL` for bill/rent-specific payment activity, limited request/evidence milestones, receipt/proof access, and status visibility; ordinary record edit history, full request workflow logs, and internal audit logs are excluded. | Working Baseline / Not Final |
| Bills reminder route uses `BILLS-REMINDER-LIST` and `BILLS-REMINDER-DETAIL`, linked reminder IDs, bill/rent setup frequency, reminder defaults, custom override, soft-delete behavior, and DOC-08/DOC-09/DOC-18 ownership boundaries. | Working Baseline / Not Final |
| Bills evidence route treats evidence as a bill/rent detail sub-flow, using `BILLS-EVIDENCE-DETAIL` and `BILLS-EVIDENCE-UPLOAD`; evidence actions live inside bill/rent detail, extracted fields populate bill/rent details, and evidence status drives payment readiness. | Working Baseline / Not Final |
| Payment Profile route uses `PAYMENT-PROFILE-ROOT` for tokenized card management and saved split-card profile management; it does not authorize payment or replace DOC-09 checkout. | Working Baseline / Not Final |
| `ME-ROOT` is the permanent bottom-navigation account-control route for mixed-role users. DOC-06B defines its Account Information, reusable Identity Verification, Login & Security, Payment Passcode Settings, and Privacy & Data behavior while preserving handoffs to established feature owners. | Working Baseline / Core Account Child Routes Defined |
| `ACTIVITY-ROOT` remains the single account-level payer/payee financial activity route. `RECEIVING-DETAILS` manages the user's approved payee payout destination and is not another activity route. | Working Baseline / Child Details Pending |
| `ARCHIVED-EVIDENCE-LIST`, labelled `Archived Documents`, provides controlled access to archived or previous evidence only; archived bills/rent, requests, instructions, and activities remain in their owning routes. | Working Baseline / Child Details Pending |
| User-to-user payee linking must be initiated or accepted through an approved flow; automatic user-to-user matching is not allowed as a UX assumption. | Working Baseline |
| Tenancy evidence is treated as contract/relationship evidence, while invoices/bills usually support obligation/payment-cycle evidence; detailed data structure remains owned by DOC-12 and DOC-18. | Working Baseline |

---

---

## 11. Parent Acceptance Criteria

The DOC-06 parent is acceptable when:

- DOC-06A to DOC-06D exist and are linked from this parent;
- each child document clearly states what it governs and what it does not govern;
- incomplete routes and deferred details are visibly marked;
- stable IDs are introduced progressively without forcing unfinished route detail;
- existing product decisions are preserved in parent or child docs;
- prohibited PayPlus journey boundaries remain visible;
- cross-document owners remain clear;
- traceability/index references point to the DOC-06 family rather than only the parent DOC-06 file.

---

## 12. Version History

| Version | Date | Summary |
| --- | --- | --- |
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
