---
document_id: DOC-06D
title: UX Requirements, Acceptance Criteria & Test Matrix
version: 0.1.21
status: Founder Working Baseline
owner: Product / Founder
reviewers:
  - Product Lead
  - Design Lead
  - Engineering Lead
  - QA Lead
  - Compliance Lead
approvers:
  - Project Owner
  - Product Lead
last_updated: 2026-07-27
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
---

# DOC-06D - UX Requirements, Acceptance Criteria & Test Matrix

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06D` |
| **Title** | UX Requirements, Acceptance Criteria & Test Matrix |
| **Version** | `0.1.21` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>QA Lead<br>Compliance Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-07-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-20 Testing, UAT & Go-Live Checklist |

---

## 1. Purpose

DOC-06D governs UX requirement IDs, acceptance criteria, route/action/state/event/test mapping, and test-readiness tracking for the DOC-06 family.

## 2. Scope Boundary

DOC-06D owns the mapping between human-readable UX requirements and testable acceptance criteria. It does not create product scope, technical implementation tasks, database schemas, endpoint contracts, or detailed automated tests.

DOC-06D should expand progressively as DOC-06A, DOC-06B, and DOC-06C become more stable.

## 3. Completion Markers

| Area | Status | Notes |
| --- | --- | --- |
| Non-functional UX baseline | Working baseline | Stable UXREQ IDs should be assigned progressively. |
| MVP/baseline acceptance criteria | Working baseline | Needs route/action/state/test mapping. |
| Route/action/state/event/test matrix | Skeleton | Start with settled Bills-route requirements, then expand to other routes. |
| Open-question/test-readiness mapping | Skeleton | Incomplete routes must remain visible as not test-ready. |

## 4. Mapping Standard

DOC-06D should use this relationship when expanding detailed testability:

```text
UXREQ -> ROUTE / SCREEN / COMPONENT -> ACTION -> STATE / EVENT -> TEST
```

Example pattern:

| Field | Example |
| --- | --- |
| UX Requirement | UXREQ-06C-014 |
| Requirement Text | Payer-side Bills cards must show Pay only when the record is eligible for payment. |
| Route | ROUTE-06C-BILLS-PAY |
| Component | COMP-06C-BILL-CARD |
| Action | ACT-06C-PAY-001 |
| State Dependency | STATE-06C-OBLIGATION-READY-TO-PAY |
| Event Dependency | EVT-06C-BILL-PAY-TAPPED |
| Owning Docs | DOC-06C, DOC-09, DOC-12, DOC-14, DOC-15 |
| Test | TC-06D-014 |

## 5. Initial Test-Readiness Matrix

| Area | Source Doc | Test Readiness | Notes |
| --- | --- | --- | --- |
| Prohibited wallet/stored-value/cashout journeys | DOC-06 / DOC-06A | Ready for high-level blocked-flow criteria | Detailed tests later in DOC-20. |
| Authentication entry routes | DOC-06B / DOC-15 / DOC-19 | Partial | Route IDs, normal/contextual success handoffs, unique primary email, explicit email/password and Google/Apple login methods, no email-based automatic linking, restricted account creation, deferred financial activation, and Account Security Set/Change Password and link/unlink rules are testable; detailed screens, recovery, protected-deeplink, validation, and security mechanics remain open. |
| Home dashboard layout | DOC-06B | Partial | `HOME-ROOT` is assigned; exact card behavior and UI detail remain open. |
| Pay+ action sheet | DOC-06B / DOC-06C / DOC-09 | Partial to strong | Five-action order, payee-to-payer request direction, category-scoped Bills handoffs, Add/Continue behavior, availability, return, configuration limits, and no-side-effect boundary are testable; exact visual specification remains open. |
| More and shortcut management | DOC-06B / DOC-15 / DOC-18 / DOC-22 | Partial to strong | `MORE-ROOT` Normal/Manage modes, 8-slot maximum, protected More entry, account-level preferences, accessible add/remove/reorder, current-default restore, availability precedence, unsaved-change handling, and secondary-service handoffs are testable; final visual styling and optional replacement Undo remain open. |
| Notifications route family | DOC-06B / DOC-08 / DOC-15 | Partial to strong | Root/Inbox/Detail/Settings hierarchy, Home/Me entry, reciprocal navigation, filters, read/archive behavior, badge semantics, current-state contextual handoff, preference failure recovery, and signal separation are testable; final styling, provider operations, and template wording remain open. |
| BILLS-PAY / BILLS-RECEIVE role separation | DOC-06C | Partial to strong | Core role distinction is testable; visual detail remains open. |
| Bills evidence sub-flow | DOC-06C / DOC-12 | Partial | UX flow is testable; verification logic depends on DOC-12/DOC-18. |
| Bills activity sub-route | DOC-06C / DOC-09 / DOC-10 / DOC-11 | Partial to strong | Payment, payout/transfer, failure, return, refund, and reversal activity is testable; request and evidence lifecycle entries are explicitly excluded. |
| Bills reminder route | DOC-06C / DOC-08 / DOC-09 | Partial to strong | Reminder list/detail behavior and separation from payment-instruction action alerts are testable; final visual design remains open. |
| Requests route | DOC-06B / DOC-06A / DOC-06C / DOC-08 | Partial to strong | `REQUESTS-ROOT`, `REQUESTS-DETAIL`, and `REQUESTS-NEW`, canonical lifecycle states, role labels, event separation, evidence gate, linked-case boundary, and archive visibility are testable; final visual design and detailed operational limits remain open. |
| Instructions route | DOC-06B / DOC-09 | Partial to strong | Pending versus incomplete cards/details, edit restrictions, actions, expiry, and checkout return are testable; final visual design remains open. |
| Payment checkout handoff | DOC-06A / DOC-06C / DOC-09 | Partial | `PAYMENT-CHECKOUT` is assigned; DOC-06 can test route handoff and DOC-09 owns checkout tests. |
| Payment Profile route | DOC-06B / DOC-09 / DOC-15 / DOC-19 | Partial to strong | Two-tab `Cards` / `Profiles` baseline, card/profile management, max 6-card profile/payment cap, return context, masking, and non-checkout boundary are testable; final styling and tokenization behavior remain open. |
| Global Activity route | DOC-06B / DOC-09 / DOC-10 / DOC-11 | Partial to strong | Accounting-style entries, role-aware direction/status, expansion, detail, document actions, and return behavior are testable; final visual density/search/grouping remain open. |
| Receipts & Statements route | DOC-06B / DOC-08 / DOC-15 | Partial to strong | `RECEIPTS-ROOT` views, search, list, `Paid` / `Received` role indicator, empty-state behavior, direct download, shared PDF preview, notification entry, and return behavior are testable; final PDF design and re-issue operations remain open. |
| Offers and Rewards routes | DOC-06B / DOC-09 / DOC-13 / DOC-15 | Strong human-readable baseline | Section limits, child collection behavior, source/action/destination/return transitions, multi-collection membership, duplicate suppression, ordering, full-screen detail, checkout handoff, and issued-reward management are testable. External vouchers and miles are launch-supported; final visual design, label taxonomy, personalization, equal-priority tie-break, partner selection, fulfilment method, and operational readiness remain open. |
| Referral route | DOC-06B / DOC-13 / DOC-15 | Strong human-readable baseline | Sharing, attribution, progress, role-sensitive entitlement list/detail/claim, canonical reward handoff, and privacy boundaries are testable; final visual design and campaign operations remain open. |
| Me route | DOC-06B / DOC-06C / DOC-08 / DOC-10 / DOC-12 / DOC-15 / DOC-18 / DOC-19 / DOC-21 / DOC-22 | Strong for core account routes | Permanent `ME-ROOT`, Account Information, reusable Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, masking/reveal, contact changes, verification labels/actions, closure, trusted-device removal, privacy requests, protected export, return behavior, and failures are testable; provider/system mapping, technical security values, other Me children, and final visual design remain open. |
| Receiving Info route | DOC-06B / DOC-10 / DOC-12 / DOC-14 / DOC-15 | Partial to strong | Multiple profiles, masked list/detail, passcode/reauthenticated full-value reveal and add/edit, proof/readiness, version/archive, destination snapshots, and origin return are testable; provider validation and final visual design remain open. |
| Archived Records and Documents | DOC-06B / DOC-06C / DOC-12 / DOC-15 | Strong human-readable baseline | `ARCHIVED-ROOT`, `ARCHIVED-BILLS-LIST`, archived read-only bill/rent detail mode, and `ARCHIVED-DOCS-LIST` route behavior are testable; final visual design and technical schema remain open. |

---

## 6. Non-Functional UX Requirements

| Area | Requirement |
| --- | --- |
| Clarity | Users must understand what they are requesting, paying, accepting, or authorizing. |
| Evidence visibility | Payer must be able to review evidence before payment authorization. |
| Evidence correction | Users must be able to review and correct autofilled evidence fields before submission where OCR/autofill is enabled. |
| Sensitive field display control | UI must apply DOC-15 role-based display, masking, approved-purpose access, and controlled detail views; broader extractable data may be stored without broad display. |
| Status transparency | Users must see request lifecycle, evidence status, obligation readiness, linked case status, payment/payout status, and archive visibility as separate labelled concepts. |
| Permissioning | Users must only see data appropriate to their role. |
| Auditability | Key actions must generate audit events. |
| Error handling | Failed, blocked, or incomplete actions must show clear next steps. |
| Accessibility | MVP UX should follow basic accessibility principles. |
| Mobile readiness | Core flows should be usable on common mobile screen sizes. |
| Security | Sensitive payment, identity, evidence, and payout details must be protected. |
| Compliance readiness | UX must support evidence, authorization, review, dispute, and traceability requirements. |

## 7. MVP Acceptance Criteria

The DOC-06 user journey scope is satisfied when:

- app launch without an approved session opens `AUTH-ENTRY`, where the user can choose `AUTH-LOGIN` or `AUTH-REGISTRATION`;
- normal successful login or completed registration opens `HOME-ROOT`, while an approved protected or referral deeplink may resume its intended destination after authentication;
- restricted account creation requires one unique verified primary email, accepted Terms and Privacy notices, and one usable login method;
- email/password, Google, and Apple may access the same account only after explicit setup or linking, with stable provider identity and no automatic link or merge based only on matching email;
- social-authenticated users may set their first PayPlus password through `ACCOUNT-SECURITY`, after which the action changes from `Set Password` to `Change Password`;
- provider linking and unlinking require fresh approved reauthentication, explicit confirmation, audit, and security notification, and the final usable login method cannot be removed;
- a restricted account may enter `HOME-ROOT` before phone, identity, and payment-passcode completion, but payment and other financially restricted actions remain blocked until the applicable gates complete;
- authentication failure does not expose protected route history and keeps the user in the applicable authentication flow with a permitted retry or recovery path;
- payers can register and log in;
- payees can register and log in;
- phone verification, new-device 2FA, dormant-login reauthentication, and material-change confirmation touchpoints are represented;
- payers have `HOME-ROOT` as their logged-in dashboard;
- payees have `HOME-ROOT` as their logged-in dashboard;
- payees can create evidence-backed payment requests;
- payees can send payment requests to payers;
- Pay+ `Request Payment` opens `REQUESTS-NEW` as a payee-to-payer request entry, while payer-to-payee linking begins only from an approved contextual bill/rent/linking action;
- Pay+ `Pay a Bill` and `Pay Rent` open temporary category-scoped `BILLS-PAY` selection without changing saved Bills filters and do not bypass readiness or checkout gates;
- Pay+ `Continue Payment` is disabled with no active pending/incomplete instruction, opens one instruction detail for exactly one, and opens the instruction list for more than one; review-blocked instructions remain visible but cannot continue;
- standalone Pay+ bill/rent setup offers `Pay Now` only when payment-ready and otherwise shows the current readiness state; request-origin setup returns to `REQUESTS-NEW`;
- Pay+ open/close, hidden-versus-disabled, unsaved-work protection, duplicate-activation prevention, and reduced-motion behavior follow DOC-06B;
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
- payer can accept or reject a request, with rejection reason where required;
- request lifecycle is limited to `Draft`, `Pending Evidence Verification`, `Pending Receiver Action`, `Accepted`, `Rejected`, `Expired`, and `Cancelled`;
- sender and receiver see the role-aware labels defined by DOC-06A and DOC-06B, while drafts and evidence-gated requests remain hidden from receivers;
- submitted, sent/shared, viewed, reminded, archived, and restored are treated as events or visibility transitions rather than request states;
- evidence outcomes, obligation readiness, payment/payout status, and linked case status do not overwrite the request lifecycle;
- users can raise or respond to linked query, dispute, support, or exception cases where enabled;
- payer can explicitly authorize payment;
- payer must enter payment passcode before payment authorization proceeds;
- users can manage tokenized cards and saved split-card profiles through `PAYMENT-PROFILE-ROOT` without creating wallet, stored-value, cashout, or payment authorization behavior;
- payer, payee, and mixed-role users can open permanent `ME-ROOT` from bottom navigation without a role switch;
- `ME-ROOT` presents the confirmed fixed section order and treats Bills, Payment Profile, Activity, Receipts & Statements, My Rewards, and Referral as handoffs to their owning routes;
- Account Information shows display name, immutable login name after setup, copyable PayPlus User ID, masked phone/email, and only `Pending`, `Verified`, `Failed`, or `Update Required` identity-verification status without exposing identity attributes, documents, provider payloads, payment credentials, evidence, or internal risk reasons;
- `Verified` shows no verification action, while the other three labels show `Verify Now` and open reusable `IDENTITY-VERIFICATION` without duplicate submission;
- changing phone verifies the registered email and new phone; changing email verifies the registered phone and new email; successful changes notify old and new channels where available;
- revealing approved masked sensitive information in a prominent account or Receiving Info surface requires payment passcode or approved reauthentication, with additional step-up where the owning security/risk rules require it, while prohibited fields remain unavailable;
- changing sensitive identity, contact, security, credential, or Receiving Info data requires payment passcode or approved reauthentication before the route-specific OTP, provider, review, or confirmation flow;
- ordinary permitted evidence, invoice, receipt, statement, and payment-proof viewing/downloading does not require an extra passcode or step-up prompt solely because the document is opened or downloaded;
- `ACCOUNT-SECURITY` provides Login Methods with Set/Change Password and Google/Apple Link/Unlink state, Payment Passcode, permitted Two-Step Verification and Biometric Unlock toggles, Trusted Devices removal, and Recovery and Security Support without a separate MVP Active Sessions list;
- `PAYMENT-PASSCODE-SETTINGS` supports passcode change/reset and the optional passcode-confirmation preference for card/payment-profile changes without ever displaying the existing passcode;
- mandatory new-device, risk, contact-change, account-closure, and provider-required authentication cannot be disabled by the Two-Step Verification toggle;
- `PRIVACY-DATA-CONTROLS` separates optional direct-marketing, personalization, and approved partner-data-use choices from mandatory processing; provides governed access, correction, export, retention/deletion requests and request history; and uses `Submitted`, `In Progress`, `Action Required`, `Completed`, and `Unable to Complete` labels;
- completed data exports require authenticated, time-limited in-app access and are not attached to ordinary email;
- account closure requires payment passcode plus 2FA, checks unresolved cases, remains cancellable until operational finalization, disables login and terminates sessions after completion, and does not imply immediate deletion of retained records;
- `RECEIVING-INFO` opens its list immediately, supports multiple user-linked profiles, optional nickname, masked cards, trailing swipe `Edit` / `Archive`, detail and setup routes, retained versions, and no hard deletion;
- other saved profiles remain private when one destination is selected for a request, bill, or rent;
- self-identity matching may result in `Ready to Receive`, while third-party/company profiles require proof and `Under Review`; destination-attributable failures may show `Action Required`, but transient payout failures do not change profile readiness;
- profile edit/archive does not alter existing request, obligation, payment, or payout snapshots;
- payee destination change after request acceptance creates a new request and bill/rent record, while payer destination change does not require payee approval and notifies a linked payee;
- payment authorization freezes the effective destination and a later change requires renewed payer authorization;
- `RECEIVING-INFO` remains configuration and does not create another Activity route, wallet, balance, cashout feature, or payer-visible payee-profile directory;
- `ARCHIVED-ROOT` separates `ARCHIVED-BILLS-LIST` from `ARCHIVED-DOCS-LIST`, and the Archived Documents screen supports the defined search, filters, newest-first list, read-only preview, permitted download/link handoff, state preservation, and access/failure states;
- `Archived` and `Previous version` remain history/visibility descriptors rather than evidence-processing statuses;
- the sole current evidence linked to an active obligation cannot be archived independently; accepted replacement creates a non-restorable previous version;
- `ARCHIVED-BILLS-LIST` uses one mixed-role newest-first list with Bill/Fee, Rent/Tenancy, Pay, Receive, and Restore available filters, and reuses bill/rent detail in archived read-only mode;
- archived detail suppresses active actions, offers Restore only after current eligibility checks, and provides scoped archived-document and activity handoffs;
- archiving a bill/rent archives its current linked evidence for the same user, while restoring an eligible obligation restores and revalidates that current evidence without restoring previous versions;
- personal archive/restore does not alter the counterparty's view, linkage, canonical obligation, completed history, or retained snapshots;
- unresolved reviews and active request/payment-instruction/funding/payment/payout/refund/dispute/chargeback/restriction/legal-hold dependencies block archive or restore as defined by their owners;
- archive disables the user's linked reminders, while restore does not reactivate reminders, instructions, scheduled actions, or prior authorizations;
- an expired obligation does not auto-archive, and an already-expired obligation manually archived by the user is non-restorable;
- core Me account, security, privacy, support, legal, and logout controls cannot be hidden by ordinary placement configuration, while optional rows follow module and retained-record rules;
- Me child-route return restores the prior Me position, while contextual entry from checkout, Instructions, notifications, or deeplinks returns to the originating context;
- Log Out is the final Me action, ends the current session, clears protected route history, and returns to `AUTH-ENTRY` without being treated as account closure;
- `MORE-ROOT` remains separate from Me and uses one root with Normal and Manage Shortcuts modes;
- Home supports a default and maximum of 8 shortcuts, comprising up to 7 configurable entries plus protected `More`, while users may keep fewer configurable shortcuts;
- protected `More` remains the final Home shortcut and cannot be removed, disabled, displaced, or user-reordered;
- users can search More entries, add/remove/reorder eligible shortcuts, use non-drag accessibility controls, save account-level preferences, and restore the current eligible admin default;
- adding an eighth configurable candidate when 7 configurable positions are full returns the last configurable shortcut to Other Shortcuts & Services without displacing `More`;
- entries unavailable for Home show an explicit unavailable/locked indicator and cannot be added, while destination-specific access controls remain enforced by the owning route;
- Back with unsaved shortcut changes offers Save Changes, Discard Changes, or Continue Editing; failed save/restore preserves the pending arrangement for retry;
- shortcut resolution follows protected product boundaries, eligibility/availability, approved catalog, current admin default, then user preference; user preference cannot expose an unavailable or prohibited route;
- More may open approved secondary services but does not own them, replace `ME-ROOT`, or bypass their controls;
- the Home Inbox icon opens `NOTIFICATION-INBOX`, while its items route to their owning destinations and notification preferences remain in `NOTIFICATION-SETTINGS`;
- `NOTIFICATION-ROOT` defaults to Inbox; Home enters Inbox, Me enters Settings, Inbox and Settings cross-link without route-stack loops, and external notification entry preserves or safely resolves return context;
- Inbox `All` excludes Archived, the badge counts unread Inbox records only, read/archive actions do not alter owning-domain state, and `Action Required` comes from the owning domain;
- every notification card opens `NOTIFICATION-DETAIL`, which revalidates current status, permission, target, and action availability before any domain handoff;
- required communications are not shown as disableable toggles, optional preference changes save immediately, failed changes restore the prior effective value, account preferences/read/archive state synchronize across approved devices, and device push permission remains device-specific;
- payment entry routes use `PAYMENT-CHECKOUT` for DOC-09 checkout behavior without turning Bills, Requests, Instructions, or Payment Profile into checkout owners;
- saved split-card profiles and split-card checkout must observe the MVP maximum of 6 cards;
- single-card checkout may preselect a default card while split-card checkout requires user selection of a payment profile;
- payment status can be tracked;
- payout or settlement status can be tracked where applicable;
- `BILLS-ACTIVITY` shows payment and related payout/transfer, failure, return, refund, and reversal activity for one obligation and excludes request and evidence lifecycle entries;
- payer-side Bills routes do not show payee-side request actions as payment actions;
- payee-side Bills routes do not show payer-side `Pay` actions;
- payer and payee can view the same linked request/payment context subject to permissions;
- admin can review users, requests, evidence, disputes, and exceptions;
- key status changes are audit logged;
- receipts or confirmations are available for completed payments;
- users can search, view, and directly download available receipts and statements through `RECEIPTS-ROOT`, with `RECEIPT-DETAIL` and `STATEMENT-DETAIL` providing a minimal in-app PDF preview;
- users can discover promotions through `OFFERS-ROOT`, review material conditions in `OFFER-DETAIL`, and manage issued rewards separately through `REWARDS-ROOT` and `REWARD-DETAIL`;
- `REWARDS-ROOT` uses route-local Active and History views, route-local search, instrument filters that are not statuses, defined ordering, and loading, empty, no-match, error, and permitted cached read-only states;
- reward cards expose approved summary fields and open `REWARD-DETAIL` without revealing redemption credentials, internal references, internal risk reasons, referral-party information, or partner payloads;
- `REWARD-DETAIL` shows the full benefit, eligibility, restrictions, usage method, expiry, and complete terms and conditions, and exposes only a meaningful contextual action;
- checkout-applied rewards are selected in DOC-09 checkout after card/profile selection; viewing reward detail returns to the same checkout without selection, reservation, or consumption;
- credential reveal, copy, or external-partner open does not mark a reward Used; authoritative outcomes, duplicate retries, unknown results, and terminal display follow DOC-13 and the status-display reference matrix;
- issued reward records preserve instrument type, earning source, participant role where applicable, program, campaign/offer/entitlement source, and fulfilment method without presenting My Rewards as a wallet or stored balance;
- users can open complete Card, Pay+, and Partner offer collections through `OFFERS-CARD-LIST`, `OFFERS-PAYPLUS-LIST`, and `OFFERS-PARTNER-LIST` without treating category labels as routes;
- one Offer ID may belong to multiple discovery collections, appears once within each child list, and is suppressed from unintended repeated display on `OFFERS-ROOT` while remaining available in every relevant child list;
- Offers child lists apply mandatory display gates and stable collection-specific admin priority without random reshuffling or MVP user sorting;
- one payment card may qualify for multiple distinct offers without those offers being treated as duplicates;
- checkout automatically applies the single eligible payment-method-sensitive Card Offer with the highest user value per selected payment card or split-payment funding leg and displays the applied result;
- payment-card/profile selection, automatic Card Offer result, separate eligible coupon/voucher/discount selection, recalculated quote, and payer review occur in the same checkout screen or step before authorization;
- changing a payment card, profile, funding allocation, amount, or other material eligibility input re-evaluates the promotion result and blocks authorization until the revised quote is reviewed;
- navigation tests cover source, user action, destination, and return behavior without requiring a permanent ID for every entry action;
- successful redemption changes the offer action to `Redeemed` and exposes `View My Reward`, while failed or ineligible redemption creates no reward instrument;
- referral participation remains separate from Offers through `REFERRAL-ROOT`, `REFERRAL-REWARDS-LIST`, `REFERRAL-ENTITLEMENT-DETAIL`, and `REFERRAL-REWARD-CLAIM`, and `BILLS-PAY` remains an external handoff rather than an Offers sub-route;
- opening a referral share sheet, copying a link, or showing a QR creates no known recipient, invitation card, or invitation status;
- referral deeplink/QR registration displays a valid code prefilled and not editable, while ordinary registration permits optional manual entry, retry, or clearing an invalid code;
- completed valid registration creates normal-user-immutable referral attribution without creating payer/payee linking, a Request, payment authority, or shared financial visibility;
- referral qualification displays `In Progress`, `Qualified`, `Not Qualified`, or `Under Review` without exposing private financial, evidence, KYC, card, payee, or internal risk data;
- corresponding referrer and referee entitlements appear in `REFERRAL-REWARDS-LIST`, preserve beneficiary role, and use `Available to Claim` and `History` route-local tabs without creating additional routes;
- referral reward cards expose only approved reward/campaign/status/date fields, open `REFERRAL-ENTITLEMENT-DETAIL`, and do not expose referral-party identity or private qualification data;
- claim is initiated from entitlement detail, prevents duplicate submission, and creates at most one canonical issued reward; success offers `View Reward` to `REWARD-DETAIL` and `Done` to the Referral Rewards `History` tab with the issued card visible;
- campaign end, claim deadline, and reward usage expiry remain separate; valid earned entitlements survive campaign end according to DOC-13;
- normal Referral reward presentation uses `Available to Claim`, `Issued`, `Expired`, and `Reversed`; an administrator-held claimed item remains inactive in `History` with exceptional `Under Review` presentation until resolved;
- direct checkout discounts do not appear as issued rewards unless DOC-13 creates a separate entitlement or instrument;
- failed, rejected, cancelled, expired, and exception/support cases are handled clearly;
- wallet, stored balance, cashout, self-cashout, and unsupported P2P journeys are blocked.

## 8. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06D-001 | Which stable UXREQ IDs should be assigned before AI build-execution conversion? | Product / QA / Engineering | Open |
| OQ-06D-002 | Which route/action/state/event mappings are required before the first AI implementation prompt set? | Product / QA / Engineering | Open |
| OQ-06D-003 | Which incomplete routes should remain placeholder-only until detailed UI drafting is complete? | Product / Design | Open |
| OQ-06D-004 | Which acceptance criteria should remain at human-review level versus becoming implementation-level tests in DOC-20? | Product / QA | Open |

## 9. Version History

| Version | Date | Summary |
| --- | --- | --- |
| 0.1.21 | 2026-07-27 | Added acceptance coverage for unique primary email, explicit multiple login methods, no automatic email-based linking, social-account password setup, restricted account creation, deferred financial activation, and Account Security link/unlink safeguards. |
| 0.1.20 | 2026-07-27 | Added test-readiness and acceptance coverage for the Notifications route family, entry/return behavior, filters, unread badge, read/archive separation, detail revalidation, Settings behavior, cross-device state, and owning-domain signal boundaries. |
| 0.1.19 | 2026-07-27 | Added test-readiness and acceptance coverage for `MORE-ROOT` modes, shortcut capacity, protected More access, account-level preferences, accessible management, current-default restore, availability precedence, replacement behavior, unsaved changes, failures, and destination boundaries. |
| 0.1.18 | 2026-07-27 | Added test-readiness and acceptance coverage for the Pay+ five-action order, request direction, Bills scopes, Add/Continue decisions, visibility rules, return behavior, duplicate prevention, and reduced-motion baseline. |
| 0.1.17 | 2026-07-26 | Added acceptance coverage for Archive hub/list behavior, archived read-only detail reuse, search/filters, blockers, personal visibility, restore revalidation, reminder effects, and obligation/evidence separation. |
| 0.1.16 | 2026-07-26 | Added archive-family route, Archived Documents UI/access, evidence replacement/archive/restore, expiry, history-label, and non-restorable acceptance coverage. |
| 0.1.15 | 2026-07-26 | Added test-readiness and acceptance coverage for `AUTH-ENTRY`, `AUTH-LOGIN`, `AUTH-REGISTRATION`, `HOME-ROOT`, `PAYPLUS-ACTION-SHEET`, `MORE-ROOT`, `NOTIFICATION-INBOX`, and `PAYMENT-CHECKOUT`. |
| 0.1.14 | 2026-07-26 | Added acceptance coverage for the canonical request lifecycle, role labels, event/evidence/readiness/case/archive separation, and replaced the obsolete approved-for-payment request-state dependency. |
| 0.1.13 | 2026-07-26 | Expanded route-family test readiness, added Bills Activity scope tests, aligned prominent sensitive reveal and material-change authentication, and confirmed ordinary permitted document viewing/download without an extra prompt. |
| 0.1.12 | 2026-07-23 | Added acceptance coverage for multiple Receiving Info profiles, list/card/detail/setup behavior, masking and edit reveal, readiness/proof states, archive/versioning, destination snapshots, request replacement, linked-payee notification, and authorization freeze. |
| 0.1.11 | 2026-07-22 | Added acceptance coverage for Account Information, Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, contact changes, status/action mapping, trusted-device removal, protected export, and account closure. |
| 0.1.10 | 2026-07-22 | Added `ME-ROOT` acceptance coverage for permanent mixed-role entry, fixed section order, masking and passcode-gated reveal, established-route handoffs, Receiving Details, Archived Documents, core visibility, return behavior, logout, and the separate More boundary. |
| 0.1.9 | 2026-07-21 | Added Rewards acceptance coverage for Active/History views, search/filter/order and route states, safe reward cards, complete detail/T&C, checkout selection and return, credential-versus-use behavior, canonical statuses, and separate reward-data dimensions. |
| 0.1.8 | 2026-07-21 | Added Referral child-screen acceptance coverage for role-sensitive rewards, two tabs, card/privacy boundaries, detail-first claim, idempotent issuance, lifecycle-date separation, and exceptional admin-held History presentation. |
| 0.1.7 | 2026-07-21 | Added Referral route, sharing, registration-attribution, qualification-display, privacy-boundary, role-sensitive entitlement, claim, and canonical reward-handoff acceptance coverage. |
| 0.1.6 | 2026-07-20 | Added Offers child-list, multi-collection, duplicate-suppression, stable-ordering, distinct-offer, same-screen checkout, highest-user-value Card Offer, separate coupon/voucher, and promotion-recalculation acceptance coverage; removed stale entry-point-ID wording. |
| 0.1.5 | 2026-07-17 | Added Offers and Rewards test-readiness for stable product destinations, source/action/destination/return transitions, section limits, child collection screens, full-screen detail behavior, redemption state, issued-reward management, partial Referral routing, and external Bills/checkout handoffs. |
| 0.1.4 | 2026-07-14 | Added test-readiness and MVP acceptance coverage for `RECEIPTS-ROOT` search, role-aware list behavior, direct document download, and shared PDF preview behavior through `RECEIPT-DETAIL` and `STATEMENT-DETAIL`. |
| 0.1.3 | 2026-07-06 | Added Payment Profile route test-readiness and MVP acceptance coverage for two-tab card/profile management, max 6-card cap, default single-card behavior, split-profile selection, default confirmation behavior, return context, and non-checkout boundary. |
| 0.1.2 | 2026-07-02 | Aligned UX acceptance criteria with DOC-06B request-route model by separating accept/reject request actions from support, query, dispute, and exception cases. |
| 0.1.1 | 2026-06-25 | Removed temporary source-section heading wording and corrected the UX mapping code fence for official DOC-06D baseline use. |
| 0.1.0 | 2026-06-25 | Created as DOC-06D child document for non-functional UX requirements, acceptance criteria, and initial test-readiness mapping. |
