---
document_id: DOC-06D
title: UX Requirements, Acceptance Criteria & Test Matrix
version: 1.2.0
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
last_updated: 2026-11-13
classification: Internal
related_documents:
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-06A Core User Journeys & Service Blueprint
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operational SOPs
---

# DOC-06D - UX Requirements, Acceptance Criteria & Test Matrix

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-06D` |
| **Title** | UX Requirements, Acceptance Criteria & Test Matrix |
| **Version** | `1.2.0` |
| **Status** | Founder Working Baseline |
| **Owner** | Product / Founder |
| **Reviewers** | Product Lead<br>Design Lead<br>Engineering Lead<br>QA Lead<br>Compliance Lead |
| **Approvers** | Project Owner<br>Product Lead |
| **Last Updated** | `2026-11-13` |
| **Classification** | Internal |
| **Related Documents** | DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-06A Core User Journeys & Service Blueprint<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operational SOPs |

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

Map each adopted requirement to its actual formal owner, semantic route/view/component, action, condition and expected return. Keep accepted definition, bounded prototype observation and production verification separately identified. The PP-MVP-20261112-R1 M/K references below are local intake trace references, not new permanent requirement, route, status, event or test IDs. Existing stable IDs retain their meanings; assigning future technical/test identifiers remains separately owned.

Versioned Design nodes, static action evaluations, source tests, native export hashes and synthetic Make observations do not prove real OTP/OAuth/KYC/notification/payment/Payout/OS sharing or accessibility acceptance. Mark untested/unavailable branches explicitly. Visual-only tokens/type/spacing/radius/icons/header/motion specimens belong in Design/UI specification unless they change a named interaction contract.

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
| Entrance and authentication routes | DOC-06B / DOC-07 / DOC-15 / DOC-19 | Partial to strong | Phone/Email OTP/provider Full Login, distinct remembered PIN, verified-phone/provider registration with mandatory Login PIN, confirmed creation, direct Done/Home identity callers, identity-only prompt and retained financial-action activation, uniqueness/proof/unknown/cancel controls are human-testable; final carousel design, exact outcome/message mappings, child verification UI, and technical security mechanics remain open. |
| Home dashboard layout | DOC-06B / DOC-06C / DOC-07 / DOC-08 / DOC-09 / DOC-10 / DOC-11 / DOC-13 / DOC-15 / DOC-22 | Strong human-readable baseline / detailed evidence pending | Greeting, Important Notice, shortcuts, Hot Offer, Upcoming Bills / Rent, Recent Activity, resilience, accessibility, and presentation-governance behavior are testable at requirement level. Final visual styling, technical session/cache/schema mechanics, exact locale Copy, implementation evidence, accessibility evidence, and UAT remain with their formal owners and DOC-20. |
| Pay+ action sheet | DOC-06B / DOC-06C / DOC-09 | Partial to strong | The accepted four-action order (`Pay a Bill`, `Pay Rent`, `Add Bill / Rent`, `Continue Payment`), category-scoped Bills/Rent handoffs, availability, return, configuration limits, and no-side-effect boundary are testable; the retired Request Payment action is not an active path and exact visual specification remains open. |
| More and shortcut management | DOC-06B / DOC-15 / DOC-18 / DOC-22 | Partial to strong | `MORE-ROOT` Normal/Manage modes, 8-slot maximum, protected More entry, account-level preferences, accessible add/remove/reorder, current-default restore, availability precedence, unsaved-change handling, and secondary-service handoffs are testable; final visual styling and optional replacement Undo remain open. |
| Notifications route family | DOC-06B / DOC-08 / DOC-15 | Partial to strong | Shared Inbox/Detail/Settings, independent signals, successful-content read, no Archive/Restore UI, immediate independent preferences, failed restoration/expired-operation invariant and consent/device separation are human-testable; final styling, provider operations, and template wording remain open. |
| BILLS-PAY / retired receive surface | DOC-06C | Partial to strong | Payer-side BILLS-PAY and separate Rent acquisition are testable; the former BILLS-RECEIVE/Receive surface is a retired non-active identifier only, and visual detail remains open. |
| Bills evidence sub-flow | DOC-06C / DOC-12 | Partial | UX flow is testable; verification logic depends on DOC-12/DOC-18. |
| Bills activity sub-route | DOC-06C / DOC-09 / DOC-10 / DOC-11 | Partial to strong | Payment, payout/transfer, failure, return, refund, and reversal activity is testable; request and evidence lifecycle entries are explicitly excluded. |
| Bills reminder route | DOC-06C / DOC-08 / DOC-09 | Partial to strong | Bill source-bound B/D/I/original-day/period-isolated inline preferences and the narrow legacy exception are human-testable. Rent list/detail/defaults and Instruction alerts remain separate; actual period/delivery/persistence inputs and production evidence remain Open. |
| Retired Request/Linking/Receiving Info runtime | DOC-06A / DOC-06B / DOC-06C / DOC-08 / DOC-10 | Ready for negative acceptance | `REQUESTS-*`, `BILLS-LINKING`, `BILLS-RECEIVE`, Consumer-Payee and Receiving Info runtime, reader, adapter, fallback, and deep-link behavior must not be active; retired IDs may remain only in explicit non-active lineage/history. |
| Instructions route | DOC-06B / DOC-09 | Partial to strong | Deliberate Payment Instruction versus incomplete Checkout Workspace presentation, edit restrictions, actions, expiry, and checkout return are testable; final visual design remains open. |
| Payment checkout handoff | DOC-06A / DOC-06B / DOC-06C / DOC-09 | Strong human-readable adaptive UI baseline / detailed evidence pending | DOC-06B defines the reviewed adaptive `PAYMENT-CHECKOUT` Workspace UI/UX, including New versus Resume context, funding, review, authorization, progress, result-specific treatment, and protected return without imposing a fixed wizard. DOC-09 governs Payment Domain architecture and invariants. Stable acceptance IDs, technical tests, prototype evidence, accessibility testing, user validation, and implementation/UAT evidence remain pending under their formal owners. |
| Payment Profile route | DOC-06B / DOC-09 / DOC-15 / DOC-19 | Partial to strong | Two-tab `Cards` / `Profiles` baseline, card/profile management, max 6-card profile/payment cap, return context, masking, and non-checkout boundary are testable; final styling and tokenization behavior remain open. |
| Global Activity route | DOC-06B / DOC-09 / DOC-10 / DOC-11 | Partial to strong | Global/source history, immutable detail/caller, recent-30-day global summary and internal Statistics controls/Apply/Back are human-testable. Production paid/date/refund/fee/time/category/label metric definitions remain financial/data/privacy owner inputs, not fixture arithmetic. |
| Receipts & Statements route | DOC-06B / DOC-08 / DOC-15 | Partial to strong | Private Single/Combined Payment membership, individual access, actual PDF/file, distinct Statement/Statistics, separate public PNG eligibility/payload, truthful Save Image/download-start/WhatsApp feedback and caller returns are human-testable; reference/date/access/native capability and production evidence remain Open. |
| Offers and Rewards routes | DOC-06B / DOC-09 / DOC-13 / DOC-15 | Strong human-readable baseline | Section limits, child collection behavior, source/action/destination/return transitions, multi-collection membership, duplicate suppression, ordering, full-screen detail, checkout handoff, and issued-reward management are testable. External vouchers and miles are launch-supported; final visual design, label taxonomy, personalization, equal-priority tie-break, partner selection, fulfilment method, and operational readiness remain open. |
| Referral route | DOC-06B / DOC-13 / DOC-15 | Strong human-readable baseline | Sharing, attribution, progress, role-sensitive entitlement list/detail/claim, canonical reward handoff, and privacy boundaries are testable; final visual design and campaign operations remain open. |
| Me route | DOC-06B / DOC-06C / DOC-08 / DOC-10 / DOC-12 / DOC-15 / DOC-18 / DOC-19 / DOC-21 / DOC-22 | Strong route and child-flow behavior baseline | Current navbar-free grouped My Account, one-open-group/search, standalone Notifications, retained Archived Data, actual-caller returns, distinct PIN/passcode and bounded new-email sequence are testable alongside retained identity/privacy/closure/recovery controls. Provider mapping, technical security values, other Me children, and final visual design remain open. |
| Retired Receiving Info / Payee-user surface | DOC-06B / DOC-10 / DOC-12 / DOC-14 / DOC-15 | Ready for negative acceptance | Receiving Info, linked Payee-user profiles, destination-library readers and related setup/archive behavior are not active runtime; the former identifiers remain only as explicit non-active lineage/history. |
| Archived Records and Documents | DOC-06B / DOC-06C / DOC-12 / DOC-15 | Partial to strong | `ARCHIVED-ROOT` and `ARCHIVED-BILLS-LIST` source-visibility projections are testable as non-erasing views; `ARCHIVED-DOCS-LIST` remains provisional/unreachable and detailed document/version presentation is deferred. |

---

## 6. Non-Functional UX Requirements

| Area | Requirement |
| --- | --- |
| Clarity | Users must understand what they are paying, setting up, accepting, or authorizing. |
| Evidence visibility | Payer must be able to review attached Evidence before payment authorization where the applicable Bill tier or separate Rent rule requires or supplies it; Tier 1 Bills do not require attached Evidence. |
| Evidence correction | Users must be able to review and correct autofilled evidence fields before submission where OCR/autofill is enabled. |
| Sensitive field display control | UI must apply DOC-15 role-based display, masking, approved-purpose access, and controlled detail views; broader extractable data may be stored without broad display. |
| Status transparency | Users must see source/projection, evidence status, obligation readiness, linked case status, payment/payout status, and archive visibility as separate labelled concepts; no retired Request lifecycle is active. |
| Permissioning | Users must only see data appropriate to their role. |
| Auditability | Key actions must generate audit events. |
| Error handling | Failed, blocked, or incomplete actions must show clear next steps. |
| Accessibility | Apply the adopted platform accessibility standards without a separate accessibility mode. DOC-06B owns Home-specific interaction requirements, DOC-06D maps them, platform/technical owners retain implementation mechanics, and DOC-20 owns detailed evidence. |
| Mobile readiness | Core flows should be usable on common mobile screen sizes. Ordinary CTA groups follow content within its vertical scroll owner; only bottom navigation is fixed, while genuine overlays retain intrinsic placement. Preserve focus/reading order and actual-caller return without inferring tested device/AT coverage. |
| Security | Sensitive payment, identity, evidence, and payout details must be protected. |
| Compliance readiness | UX must support evidence, authorization, review, dispute, and traceability requirements. |

## 7. MVP Acceptance Criteria

The DOC-06 user journey scope is satisfied when:

- app launch without an approved session opens `ENTRANCE-ROOT`, where public non-personalized content does not obscure Log In or Create Account;
- `AUTH-LOGIN` resolves eligible remembered users to `AUTH-LOGIN-FAST` and other users to `AUTH-LOGIN-FULL`;
- each material authentication result keeps its business outcome, permitted resolution, persistent account status, user-facing Message/CTA, notification decision, audit occurrence, and acceptance evidence separate;
- authentication recovery selects only a capability permitted by DOC-06B and the applicable account/route owner, and does not treat a remembered device, phone number, verified identity, or provider email as a standalone recovery method; DOC-19 enforces applicable security controls without creating or permitting the recovery capability;
- each successful login renews Fast Login eligibility for one month, while approved risk, device, credential, account, or security changes may revoke it earlier;
- eligible remembered Fast Login uses distinct Login PIN and previously enabled device biometrics, with masked context, Full Login/approved recovery, another-account and cancel paths; no plaintext password is remembered and no payment effect follows;
- `Log In With Another Account` requires confirmation, revokes the current device session, clears remembered/protected local context, and opens `AUTH-LOGIN-FULL` without unlinking server-side login methods;
- normal successful login opens Home; confirmed creation shows Done with shared identity/Back-to-Done and Later-confirmation/Home or dismissal-to-Done. Protected/referral return revalidates its current destination;
- a temporary registration attempt creates no account, reserves no proposed identifier, permits an immediate new attempt after app exit, and performs atomic uniqueness recheck before account creation;
- creation requires verified supported phone, required name/email and current email proof where needed, mandatory matching six-digit Login PIN, explicit Terms/Privacy and final uniqueness/attempt checks; Phone/provider entries share this flow without password/gender/Skip;
- Full Login provides Phone/Email tabs with destination-specific OTP and Google/Apple, no password fields in those OTP views; provider-confirmed unchanged verified email avoids repeat OTP and changed/missing/unconfirmed email does not; no email match creates an account merge/link;
- social-authenticated users may set their first PayPlus password through `ACCOUNT-SECURITY`, after which the action changes from `Set Password` to `Change Password`;
- provider linking and unlinking require fresh approved reauthentication, explicit confirmation, audit, and security notification, and the final usable login method cannot be removed;
- phone is already verified at creation; identity and Payment Passcode remain financial gates. Done/Home directly invoke shared identity with actual caller; other financially blocked/activation contexts retain every actual missing requirement and current gate;
- new-user Home's completion prompt is identity-only and disappears on confirmed identity completion; missing Payment Passcode alone does not revive the old generic checklist prompt;
- one verified email, phone, and individual identity may each belong to only one active individual account; a post-account-creation phone or identity conflict blocks activation and never auto-merges accounts;
- authentication failure does not expose protected route history and keeps the user in the applicable authentication flow with a permitted retry or recovery path;
- `AUTH-RECOVERY` provides Recovery Start, Check Email, Link Validation, New Password, Recovery Resolution, Support-authorized Setup, and Recovery Complete as internal screens or states without creating extra route IDs;
- Check Email displays the destination address, a disabled resend action until its countdown ends, and `Cannot Access This Email`; it does not assume an email app or permit primary-email change within anonymous Recovery;
- a provider-only account cannot create its first PayPlus password through anonymous Recovery and is directed to provider login or controlled Support;
- successful password reset does not create a logged-in session, revokes active sessions and remembered authentication context, sends the required security communication, and returns to `AUTH-LOGIN-FULL`;
- recovery preserves only an opaque intended-destination reference, revalidates that destination after successful login, and never preserves or auto-submits payment authorization state;
- when self-service recovery cannot continue, PayPlus selects a safe redirect, waiting, Support, or Recovery Not Permitted resolution without disclosing protected account or capability information;
- authentication outcome and resolution presentation follows the mandatory DOC-07 matrix mechanism; exact Outcome IDs, Message IDs, approved copy, and final notification mappings remain open and must not be invented by implementation;
- the active consumer actor is the Payer; an economic Payee may be an individual or institution/company and does not require a PayPlus User account;
- phone verification, new-device 2FA, dormant-login reauthentication, and material-change confirmation touchpoints are represented;
- payers have `HOME-ROOT` as their logged-in dashboard;
- HOME-ROOT preserves the accepted section order and remains a presentation surface that consumes owner-published business content without becoming its business owner;
- the Greeting uses local-time `Morning` from `05:00–11:59`, `Afternoon` from `12:00–17:59`, and `Evening` from `18:00–04:59`; server time without an applicable timezone uses the approved neutral fallback;
- Greeting name precedence is Nickname, applicable `Mr.` or `Miss` plus eKYC surname, surname alone, then no displayed name; the visual is normally one line, assistive technology receives the complete rendered greeting, and the greeting has no navigation action;
- Important Notice displays at most one eligible Inbox-backed notification, creates no duplicate Home record, excludes promotions, Rewards, marketing, and ordinary feature announcements by default, and hides when no eligible candidate exists;
- Important Notice ordering uses source-supplied canonical Severity, Home category (`System`, `Payment`, `Account`, `Other Important`), Business Priority Rank, and issued timestamp newest first; Home supplies no derived, normalized, reinterpreted, or fallback ordering semantics;
- Important Notice body enters `NOTIFICATION-DETAIL`, its Action Button enters the source-provided destination, session dismissal changes no read/archive/lifecycle/business state, and closing Details enters Inbox when another eligible notice exists or otherwise returns Home;
- an eligible Rent reminder uses the source-provided due timestamp at `23:59` in its canonical timezone, ends Home eligibility 24 hours later, and ignores a proposed due-date change until it is applied to the canonical Bill/Rent record;
- Hot Offer may present a canonical Offer when `AdminHomePresentationEnabled` is true except where an explicit canonical legal, privacy, permission, masking, or prohibited-content restriction forbids presentation; status, validity, and redemption eligibility do not themselves block Home display;
- Hot Offer supports any canonical Offer status, no `SourceHomeDisplayEligible` or multi-gate formula, no automatic status/validity/redemption filter, no more than five cards, section hiding at zero, fixed or random Admin ordering, and optional reshuffle on fresh Home entry;
- every Hot Offer card and CTA enters `OFFER-DETAIL`, where current canonical truth and available actions are presented; Admin does not alter or suppress that truth, blank presentation fields render blank rather than Home Error, and source/retrieval/session/bootstrap failures retain their owning classification;
- Hot Offer rotation defaults to five seconds and stops during keyboard focus, pointer hover, touch/swipe/drag/manual navigation, or assistive interaction; it resumes only after interaction ends, waits one complete interval after manual interaction, and requires no separate Pause/Play unless the adopted platform standard requires one;
- reduced motion removes Hot Offer transition animation but may retain rotation under the same non-disruption rules, with platform-standard accessible naming, position, focus, announcement, keyboard, and non-swipe controls;
- Upcoming Bills / Rent consumes active payer-role Bill and Rent candidates from DOC-06C, supports HKD only for MVP, initially displays up to three matching cards with explicit Show All, and preserves ordering by nearest due date, higher amount, Rent before Bill, earliest canonical creation timestamp, then stable source record ID;
- Upcoming uses canonical Bill/Rent card fields and only `Pay Now` and `View Details`; both enter the source-owning route for revalidation, missing amount/due date is an upstream invariant or retrieval failure, overdue retains its Bill/Rent meaning, and Home adds no masking rule;
- Recent Activity displays up to five owner-published completed outcomes limited to Payment Complete, distinct Partial Payment, Payout Complete, Refund, and Reversal, ordered by canonical ordering timestamp newest first;
- Recent Activity excludes technical events, intermediate states, failures, instructions, retired Request identifiers, and general Bill/Rent changes; supporting events do not duplicate outcomes, and Refund/Reversal share presentation without losing distinct source meaning;
- Recent Activity amount sign consumes canonical funds-flow direction from DOC-09, DOC-10, or DOC-11 without payer/payee-role inference; `View More` enters `ACTIVITY-ROOT`, item selection enters `ACTIVITY-DETAIL`, and Detail returns to its Home or Activity origin;
- Home applies smallest-practical-surface graceful degradation; whole-Home handling is limited to invalid/unavailable session, failed authentication/authorization establishment, failed shell/bootstrap establishment, or unsafe identity/overall-presentation authority;
- loaded zero candidates is Empty, failed retrieval is Error, blank Offer fields are not Error, Retry is section-scoped except for a bootstrap exception, and authorized stale/offline data disables unsafe actions or revalidates through the source route;
- Home accessibility is not a separate mode or a resilience state; Home-specific complete Greeting output, carousel stop/resume, keyboard and non-swipe controls, focus/return behavior, section-state semantics, and platform naming/position/announcement practices are mapped here for later DOC-20 evidence;
- Admin controls approved presentation rather than canonical business truth and cannot alter or suppress due dates, amounts, permissions, payment status, notification lifecycle, severity, Business Priority Rank, Upcoming, Recent Activity, Important Notice, obligations, or other business-owned facts; analytics, retention, event policy, configuration versioning, preference history, schema, and implementation remain with their formal owners;
- Pay+ exposes the accepted four actions only; the retired `Request Payment` action and payer-to-payee linking are not active paths;
- Pay+ `Pay a Bill` and `Pay Rent` open temporary category-scoped `BILLS-PAY` selection without changing saved Bills filters and do not bypass readiness or checkout gates;
- Pay+ `Continue Payment` is disabled with no active pending Payment Instruction or continuable incomplete Checkout Workspace, opens one detail for exactly one managed item, and opens the Instructions list for more than one; review-blocked items remain visible but cannot continue;
- standalone Pay+ Bill/Rent setup offers `Pay Now` only when payment-ready and otherwise shows the current readiness state; there is no request-origin return path;
- Pay+ open/close, hidden-versus-disabled, unsaved-work protection, duplicate-activation prevention, and reduced-motion behavior follow DOC-06B;
- Payer Bill acquisition selects a controlled Bill Category before its Category-scoped Directory or `Provide Payee myself`, with a self-provided individual or institution/company remaining Category-bound. Rent uses its separate existing tenancy journey, not Bill Category/Directory/self-provided acquisition mechanics;
- the authoritative Bill/Rent source supplies source facts and identity; Evidence supports verification and readiness but is not the source, Payable Basis, Payment Obligation, Checkout, or Payment;
- payment-ready flows preserve the source -> Payable Basis -> applicable Payment Obligations -> one-basis Checkout Workspace -> allocations/funding -> immutable confirmed Payment -> Payment Applications separation;
- a confirmed Payment is valid and immutable even when the DOC-09 controlled late-confirmation exception temporarily has zero Payment Applications; no Application is fabricated and ordinary Payout readiness is not implied;
- confirmed deliberate Save gives same-ID Saved/current without Payment. After confirmed Payment, known Save success/decline/unknown remain distinct; Retry reconciles and Skip/exit cannot fabricate cancellation/history-only or negate success. Only independently permitted confirmed-result artifacts may precede optional Save, with no general list or Save-from-Activity entitlement;
- users can upload evidence;
- OCR/document AI can process evidence where enabled;
- users can review and correct autofilled evidence fields where applicable;
- evidence is associated with the authoritative Bill/Rent source and applicable verification context, not with a retired Request runtime;
- evidence verification outcomes can route to payment eligibility, user clarification, or admin review;
- payer can review attached Evidence before payment where the applicable Bill tier or separate Rent rule requires or supplies it;
- retired Request/Linking/Receive/Receiving Info/Consumer-Payee identifiers have no active lifecycle, reader, adapter, fallback, deep link, or production data semantics; any surviving identifier is documentation lineage only;
- users can raise or respond to supported query, dispute, support, or exception cases where enabled, with case truth owned by the applicable specialist owner;
- payer can explicitly authorize payment;
- payer must enter payment passcode before payment authorization proceeds;
- users can manage tokenized cards and saved split-card profiles through `PAYMENT-PROFILE-ROOT` without creating wallet, stored-value, cashout, or payment authorization behavior;
- the Payer can open permanent `ME-ROOT` from bottom navigation without a role switch; an economic Payee does not require a User account or a separate Payee runtime;
- navbar-free My Account uses the current grouped order, standalone Notifications, at most one open group, search and actual-caller/query/group return; Bill/payment/history/growth/privacy/support entries retain their owners and Archived Data is not deleted because Make omits it;
- Account Information shows editable nickname/display name that is not a login identifier, copyable PayPlus User ID, masked phone/email, and only `Not Verified`, `Processing`, `Verified`, `Failed`, or `Update Required` identity-verification status without exposing identity attributes, documents, provider payloads, payment credentials, evidence, or internal risk reasons;
- `Not Verified` offers Verify/Continue, `Processing` offers View Status without duplicate submission, `Verified` offers no verification action, `Failed` offers Verify Again/Get Help subject to retry controls, and `Update Required` offers Update Verification;
- first-time `IDENTITY-VERIFICATION` opened during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode; a `Verified` user cannot voluntarily re-verify, while an admin-required update may require passcode or approved reauthentication before new capture;
- `PHONE-VERIFICATION` accepts Hong Kong `+852` numbers for launch, verifies possession by SMS OTP, keeps the old phone authoritative until replacement completes, and uses registered-email OTP plus new-phone SMS OTP after passcode or approved reauthentication for replacement;
- phone change retains registered-email/new-phone verification; email change uses matching NEW email twice, payment passcode/approved reauthentication, NEW-email OTP and confirmed update without registered-phone SMS/old-email OTP. Cancel/failure/unknown preserves the authoritative value and successful changes retain required notices;
- revealing approved masked sensitive information in a prominent account or source-context surface requires payment passcode or approved reauthentication, with additional step-up where the owning security/risk rules require it, while prohibited fields remain unavailable;
- changing existing sensitive identity, contact, security, credential, or source-context data requires payment passcode or approved reauthentication before the route-specific OTP, provider, review, or confirmation flow;
- ordinary permitted evidence, invoice, receipt, statement, and payment-proof viewing/downloading does not require an extra passcode or step-up prompt solely because the document is opened or downloaded;
- `ACCOUNT-SECURITY` provides Login Methods with Set/Change Password and Google/Apple Link/Unlink state, Payment Passcode, permitted Two-Step Verification and Biometric Unlock toggles, Trusted Devices removal, and Recovery and Security Support without a separate MVP Active Sessions list;
- `PAYMENT-PASSCODE-SETTINGS` requires two matching six-digit entries for Set and Change; Reset requires fresh password/Google/Apple reauthentication plus OTP to the registered verified phone, invalidates sensitive pending authorization state, and sends mandatory security notifications; unavailable phone uses controlled support recovery;
- mandatory new-device, risk, contact-change, account-closure, and provider-required authentication cannot be disabled by the Two-Step Verification toggle;
- `PRIVACY-DATA-CONTROLS` separates optional direct-marketing, personalization, and approved partner-data-use choices from mandatory processing; provides governed access, correction, export, non-erasing privacy requests and request history; and uses `Submitted`, `In Progress`, `Action Required`, `Completed`, and `Unable to Complete` labels;
- completed data exports require authenticated, time-limited in-app access and are not attached to ordinary email;
- account closure requires payment passcode plus 2FA, checks unresolved cases, remains cancellable until operational finalization, disables login and terminates sessions after completion, and does not imply immediate deletion of retained records;
- retired Receiving Info and linked Payee-user profile behavior has no active list, setup, reveal, archive, destination-library, reader, or runtime meaning;
- payment authorization freezes the applicable source-governed destination facts, and any later change follows the owning payment, payout, risk, and privacy checks;
- `ARCHIVED-ROOT` separates the active `ARCHIVED-BILLS-LIST` source-visibility projection from the provisional/unreachable `ARCHIVED-DOCS-LIST`; detailed document/version presentation remains deferred;
- `Archived` and `Previous version` remain history/visibility descriptors rather than evidence-processing statuses; detailed Evidence-version presentation remains deferred;
- the current Evidence associated with an active obligation is not independently archived in this acceptance baseline; replacement and prior-version behavior remain owner-deferred;
- `ARCHIVED-BILLS-LIST` uses the accepted Bill/Fee and Rent/Tenancy source-visibility filters and reuses Bill/Rent detail in archived read-only mode; retired Receive/Receiving Info filters are not active;
- archived detail suppresses active actions and provides scoped Bill/Rent and activity handoffs; any Restore presentation and eligibility remain owner-deferred;
- source Archive is a non-erasing visibility projection of a Saved/current authoritative Bill/Rent source; it does not erase or dispose of source, Evidence, Payment, Payout, case, or retained history;
- personal Archive does not alter canonical source facts, completed history, or retained records; detailed Restore and prior/Evidence-version presentation remain owner-deferred;
- unresolved Evidence, Payment Instruction, incomplete Checkout, funding, Payment, Payout, refund, dispute, chargeback, restriction, or legal-hold dependencies block source Archive as defined by their owners, and incomplete Checkout Close/Expiry is not source Archive; any Restore behavior remains deferred;
- Archive disables the user's linked reminders; detailed Restore effects on reminders, instructions, scheduled actions, and prior authorizations remain owner-deferred;
- an expired obligation does not auto-Archive; any Restore eligibility or non-restorable treatment remains owner-deferred;
- core Me account, security, privacy, support, legal, and logout controls cannot be hidden by ordinary placement configuration, while optional rows follow module and retained-record rules;
- Me child-route return restores the prior Me position, while contextual entry from checkout, Instructions, notifications, or deeplinks returns to the originating context;
- Log Out is the final Me action, ends the current session, clears protected route history, and returns to `ENTRANCE-ROOT` without being treated as account closure;
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
- Inbox category/read/domain/action signals are independent; necessary permitted Detail content must load before individual Read, not card tap or failed load. No Archive/Restore UI appears and retained records remain unchanged; unread badge and owner-supplied Action Required are not domain outcomes;
- every notification card opens `NOTIFICATION-DETAIL`, which revalidates current status, permission, target, and action availability before any domain handoff;
- required communications stay locked; optional preferences take immediate independent effect without page Save, failed changes restore prior values, and expired/superseded operations cannot later apply. Account reading/preferences, device permission and Privacy-owned consent remain distinct; no timeout/query mechanism is inferred;
- payment entry routes use `PAYMENT-CHECKOUT`, whose route-level adaptive UI/UX is owned by DOC-06B and whose Payment Domain architecture and authoritative payment meaning are owned by DOC-09, without turning Bills, retired Request identifiers, Instructions, or Payment Profile into Checkout owners;
- saved split-card profiles and split-card checkout must observe the MVP maximum of 6 cards;
- single-card Checkout may preselect a default eligible card. When only one owner-confirmed funding capability is available, the Checkout Workspace proceeds directly to that capability without requiring a user selection. Selection is presented only when two or more owner-confirmed capabilities are simultaneously available. Multi-card treatment may use owner-confirmed current multi-card allocation, owner-confirmed Payment Profile capability, or both; a Payment Profile is not inherently required for multi-card Checkout;
- payment status can be tracked;
- payout or settlement status can be tracked where applicable;
- `BILLS-ACTIVITY` shows payment and related payout/transfer, failure, return, refund, and reversal activity for one obligation and excludes retired Request and Evidence lifecycle entries;
- payer-side Bills routes do not expose retired Request/Receive/Linking actions;
- the Payer reviews source, Evidence/readiness, Payment, Payout, and case projections through their owning routes; economic Payee facts remain source context and do not create a Payee-user runtime;
- Admin execution is limited to workflows expressly permitted by the relevant owner; DOC-06D does not grant generic Admin policy or queue authority;
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
- the applicable payment-card or Payment Profile facts, automatic Card Offer result, separate eligible coupon/voucher/discount selection, recalculated quote, and payer review are presented within the Checkout Workspace and reviewed before authorization. Adaptive presentations may combine or separate these facts according to the current payer task and authoritative conditions; one fixed screen or step is not required;
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

## 8. Wave 5 Acceptance and Test-Mapping Convergence

The following human-readable criteria retain the reviewed Wave 1–4 baseline and map the Founder-authorized R1 UX amendments to their defining owners. This is requirement-level coverage, not proof of execution. DOC-20 owns evidence and gate expectations; DOC-06D does not invent implementation schemas, event taxonomies, technical statuses, or automation design.

| Acceptance family | Required human-level criterion | Evidence / handoff |
| --- | --- | --- |
| Actor, category and acquisition | The active actor is the Payer; the economic Payee may be an individual or institution/company. Bill acquisition selects one of the twelve controlled Bill Categories before the Category-scoped Directory or `Provide Payee myself`, with self-provided Payee remaining Category-bound. Rent keeps its separate tenancy journey without Bill Category/Directory/self-provided acquisition mechanics. | DOC-05/DOC-06C; DOC-20 acceptance evidence; DOC-12 verification handoff |
| Evidence and readiness | Evidence supports source and intended-Payee verification; Evidence status is distinct from payment readiness and cannot itself become a Payable Basis, Obligation, Checkout, or Payment. | DOC-12/DOC-09; DOC-20 positive and blocked-flow evidence |
| Tiered Bill presentation and return | Tier 3 approval preserves the current Bill context and requires a deliberate current `Pay` action before the DOC-09 resolver may admit a valid Resume; it creates no route, notification, authorization, submission, or generic status. Tier 2 presents confirmed Payment, current Evidence, and Payout-held/release facts separately, and ordinary Evidence lifecycle is excluded from Activity. Add Bill confirms declared material facts before distinct Save admission; Rent remains outside Bill tiers and requires accepted attached Evidence before Payment. | DOC-05/DOC-06B/DOC-06C/DOC-07/DOC-09/DOC-10; DOC-08/DOC-11 boundaries; DOC-20 positive, negative, exception, and regression evidence |
| Source and projections | The authoritative Bill/Rent source, deliberate Setup, immediate pay-now, Payment Result, optional same-ID Save, Saved/current, Saved/Archived, history-only and established-but-unprojected projections, Activity/History/Receipt, and source Archive projections remain distinct and are presented without erasure. | DOC-05/DOC-06C/DOC-09; DOC-20 journey/regression evidence; DOC-21 operational handoff |
| Payment topology | UX acceptance preserves source -> Payable Basis -> applicable Payment Obligations -> one-basis Checkout Workspace -> allocations/Funding Legs -> immutable confirmed Payment -> Payment Applications. The controlled late-confirmation exception may temporarily have zero Applications without invalidating Payment or implying ordinary Payout readiness. | DOC-09; DOC-10/11 handoffs; DOC-20 exception/regression evidence |
| Checkout and Payment Instruction | Incomplete or partially funded Checkout follows DOC-09 Close/Expiry/continuation semantics and is not a Payment Instruction or source Archive. Deliberate Payment Instruction cancellation/expiry remains separate. | DOC-09/DOC-06B; DOC-20 negative/exception evidence; DOC-21 escalation routing |
| Archive and cases | Source Archive is a non-erasing visibility projection and cannot bypass Evidence, Payout/reconciliation, refund/dispute/chargeback/case, restriction, or legal-hold blockers. Detailed Restore/version presentation remains deferred. | DOC-10/DOC-11/DOC-12/DOC-15; DOC-20/21 handoff |
| Notification, risk and privacy | Notification requirements remain DOC-08-owned; risk/AML/anti-cashout/sanctions hand to DOC-14; privacy/access/masking and indefinite retention hand to DOC-15; DOC-22 performs only expressly owner-permitted execution. | DOC-08/DOC-14/DOC-15/DOC-22; DOC-20/21 evidence |
| Retired runtime and prohibited scope | No active Request, Linking, Receive, Receiving Info, Consumer-Payee, Payee-user runtime, reader, adapter, fallback, deep link, wallet, remittance, cashout, marketplace, or unrestricted P2P path is accepted. Retired IDs are lineage/history only. | DOC-06A/B/C; DOC-20 negative/regression evidence; DOC-21 incident routing |
| Accessibility and content | Accessibility, disclosure, and content acceptance are mapped at human requirement level; exact Copy, visual treatment, technical mechanics, and UAT evidence remain with DOC-07/DOC-20 and later owner work. | DOC-07/DOC-20; no new Copy or implementation mechanism |

### R1 accepted-decision coverage and owner handoffs

The complete R1 intake is covered below without minting permanent IDs. Each row requires positive, negative, interrupted/unknown and actual-caller return cases where applicable; DOC-20 owns detailed future tests and execution evidence. R01/R02 are disposed of by accepted/current owner rules; R03–R06 remain bounded owner-backed inputs, not missing UX votes.

| Local intake references | Defining representation / preserved meaning | Required acceptance and remaining owner input |
| --- | --- | --- |
| K00 / M01 | Task-scoped adoption only; DOC-00 hierarchy/status and fixed versus WIP/fixture distinctions remain. | No Design count/hash/native export is treated as canonical integration, exhaustive coverage or service assurance. |
| K01 / M02–05 | DOC-06B §§5.1–5.2/5.0.6: payer-only/five destinations, secondary navbar-free screens, ordinary scroll CTAs and actual caller/cold root. | Overlay exception; warm/cold/cancel/revalidation; no authentication/payment side effect. |
| K02 / M06–13 | DOC-06B §§5.0.2/5.0.4/5.0.6 and DOC-15 §§3/6: Full OTP/provider login, shared registration, mandatory Login PIN and proof/uniqueness boundaries. | Phone/email/provider branches, unchanged versus changed provider email, PIN repeat/no Skip, stale-purpose/tab/recipient/revision, unknown send/create and six-digit full-width OTP versus PIN slots; no invented security constant/mechanism. |
| K03 / M14–16 | DOC-06B §§5.0.4–5/5.5: Done/Home shared identity, Later confirmation, identity-only prompt and no-source composition. | Done/Home Back/Escape/confirmation, prompt disappears on identity completion, absent passcode does not revive it; real financial gates still block. |
| K04 / M16–24 | DOC-06B §5.8 and DOC-06C §5.7.3: 7-day/21-day/date-intersection scopes, All/manual labels, month/Today and source-value separation. | Retap dimensions, selected/past/empty day, rail/month mode/Today state preservation, max-three/Show All/independent disclosure/no-match; no predicted obligation or changed source readiness. |
| K05 / M25–30 | DOC-06C §5.9/5.10: category directory/manual/OCR, ordinary Save, exact-source new-Save Pay and retained gates. | Same-category Back versus category-cleared incompatible data; directory failure ≠ upload; extracted proposal review; new/edit/unknown result, C1 fallback, Rent Evidence and fresh Pay gates. |
| K06 / M31–43 | DOC-06C §5.12: B/D/I/upfront seven choices, original-day periods, custom C, Three/Once and shared inline preferences. | All seven/unselected upfront choices; short months; still-unpaid/explicit forward/old Single once; no backfill/auto-skip; late/custom/first-I/change-I; whole-paid/partial/pending; Off/On/date/reopen/result sharing; valid-D/missing-B preference-only positives and new/foreign/invalid-D/material-edit negatives. R05 actual financial/delivery/persistence inputs remain. |
| K07 / M44–45 | DOC-05 §10.1; DOC-06B §5.20 and DOC-06C source joins: actual same-ID Save and narrow result-artifact access. | Known success/decline/unknown, Retry before duplicate effect, Skip/dismiss/late success without cancellation/history-only claim, independently eligible artifact/return/unavailable, no general list or Save-from-Activity right. |
| K08 / M46–48 | Protected DOC-09 money/confirmation rules consumed by DOC-06B §5.20: target≠charge, first-submission lock and exact Continue. | Single/split/current capacity/authorization/pending/terminal negatives; exact mode/legs/identity restore; no sample fee, amount or metric policy. |
| K09 / M49–50 | DOC-06B §§5.12.6/5.13: one shared profile/editor/support and confirmed Instruction-source return. | Ratios100%, account/caller/draft/date/target/mode, new-source auto-selection only on confirmed same-account Save; cancel/unknown no success path; explicit Create/Pay. |
| K10 / M51–56 | DOC-06B §5.14.3–4: distinct global/source/detail, global summary and internal Statistics E1/D3. | All/Rent/Bill, period/custom, category single/label multi, uniform applied scope/donut % versus HKD legend/top4+Other/month bars, X/Reset/disabled Apply/Apply/Back filter isolation, paid/pending/failure/dedup; R03 metric/date/refund/fee/time/category/label inputs remain Open. |
| K11 / M57–58/M61 | DOC-06B §5.15 and DOC-08 §12.1: actual Payment Single/Combined, individual access, actual PDF/Statement and Save Image feedback. | Zero/one/multiple/partial leg, actual-file preview/download/cancel/caller, Statement≠Statistics, no App thumbnail; observed Saved versus download-start/failure/unavailable; R04 native capability remains. |
| K12 / M59–60/M62–63 | DOC-08 §12.2 and DOC-15 §§8–10: exact seven-field masked public PNG, full linked-Bill/current binding and user-confirmed WhatsApp. | Smaller target/partial/pending/foreign/stale/tampered negatives, missing date/reference/access unavailable rather than guessed, revalidate Save/Share, valid source phone versus recipient selection, same PNG/no auto-send/no false gallery claim; R04 inputs remain Open. |
| K13 / M64 | DOC-06B §5.19.1–4 / DOC-08 §7.2: separate signals, successful-content Read, detail-first/current action and no Archive UI. | Card tap/failed load not Read, successful permitted necessary content Read; cold/warm/expired action, badge/domain independence and retained records. |
| K14 / M65–66 | DOC-08 §15 / DOC-06B §5.19.5 / DOC-15 §10: immediate independent preferences and consent separation. | Success/failure/prior value/unknown/late expired or superseded result, locked groups/no page Save, delivery≠device permission≠Privacy choice and contextual Back; exact effect mechanism Open. |
| K15 / M67 | DOC-06B §§5.16.2–3: Offers discovery/shared child handoffs and adopted presentation. | My Rewards/search/Referral/full-width featured/child label-search order, list/detail return and zero/one/multiple carousel; placement creates no entitlement/ranking/pricing. |
| K16 / M68–70 | DOC-06B §5.16.4 with DOC-13/15: source/status/category independent, broad history source, qualification versus issued use. | Restricted/Soon condition filters, no Rewards featured/campaign-filter requirement, retained seven-day default R02, Browse unassigned versus named Use, expiry/date/current state/unknown-use/reveal-copy no-consumption. |
| K17 / M71 | DOC-06B §5.16.5 and DOC-13 attribution/DOC-15 masking: root/progress/shared rewards/scroll utilities. | Sharing creates no attribution; R01 manual correction/clear before creation versus locked incoming context/immutable completed attribution; masked progress only, same claim identity and cold current reward/root return. |
| K18 / M72 | DOC-06B §5.17.2–3/.7: current grouped My Account, standalone Notifications and retained Archive. | Navbar-free/single-open/search/query/group/child Back, no duplicated owners; Design Archive entry retained despite R06 Make omission. |
| K19 / M73/M75 | DOC-06B §5.17.4.2 / DOC-15 §6.1: double-new-email/passcode/new-email OTP/confirmed update. | Mismatch/stale/failed/cancelled/unknown preserve value; no old-email/SMS factor inserted; phone change and passcode Reset remain distinct; safe notices/uniqueness/recovery. |
| K20 / M74 | DOC-06B §5.17.4.3: one purpose-separated Payment Passcode owner. | Set/Verify/Change/Reset/current/new-repeat/mismatch/cancel/unknown, failure Retry to input not resubmit, approved stronger Reset factors and actual caller; factor entry alone never pays. |
| K21 / M75 | DOC-06B §§5.17.4–5/.7 and DOC-15: identity/privacy/closure/Support/Archive boundaries retained. | Verified nonactionable, approved update only, protected requests/export/closure/support, honest unsupported capability, non-erasing Archive/no invented Restore; R06 parity is not policy deletion. |
| K22 / M76 + affected M01–75 | DOC-06/DOC-06A summaries and this matrix reference defining owners rather than screen replicas. | Keep visual-only specimens separate, existing IDs/roles/statuses intact, derived-register/diagram work conditional after Review, and untested owner dependencies visible without production/approval/coding-ready claims. |

## 9. Local Open Questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-06D-001 | Which stable UXREQ IDs should be assigned before AI build-execution conversion? | Product / QA / Engineering | Open |
| OQ-06D-002 | Which route/action/state/event mappings are required before the first AI implementation prompt set? | Product / QA / Engineering | Open |
| OQ-06D-003 | Which incomplete routes should remain placeholder-only until detailed UI drafting is complete? | Product / Design | Open |
| OQ-06D-004 | Which acceptance criteria should remain at human-review level versus becoming implementation-level tests in DOC-20? | Product / QA | Open |

## 10. Version History
| Version | Date | Summary |
| --- | --- | --- |
| 1.2.0 | 2026-11-13 | Canonical Writer: Mapped all PP-MVP-20261112-R1 M01–76/K00–22 local intake meanings to owner clauses and positive/negative/unknown/return acceptance; replaced obsolete auth/reminder/file/Inbox/Me assumptions without inventing stable IDs or executed tests. Corrected Bill-only Directory acquisition versus the separate Rent journey through the consolidated Specialist batch. |
| 1.1.0 | 2026-08-22 | Added human-level acceptance coverage for the approved Tier 3 current-context resolver return, Tier 2 Payment/Evidence/Payout separation, Declaration/Save boundary, and separate Rent gate without defining routes, statuses, messages, mechanisms, or tests. |
| 1.0.1 | 2026-08-21 | Aligned Recovery acceptance ownership with DOC-06B and the reviewed DOC-19 security-control contract without changing approved recovery behavior or creating implementation tests. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. |
| 0.1.29 | 2026-08-12 | Converged Wave 5 acceptance mapping to the accepted Payer-only, fixed-Category/separate-Rent, source/projection, Payment topology, Checkout/Payment Instruction, Archive, notification, privacy, Admin-execution, and retired-runtime boundaries; added human-level coverage for DOC-20 evidence and DOC-21 operations without inventing implementation detail. |
| 0.1.28 | 2026-08-05 | Added requirement-level acceptance mapping for the approved HOME-ROOT Greeting, Important Notice, Hot Offer, Upcoming Bills / Rent, Recent Activity, resilience, accessibility, and presentation-governance contracts while reserving detailed implementation/UAT evidence for DOC-20. |
| 0.1.27 | 2026-08-03 | Aligned Checkout acceptance readiness with the reviewed adaptive DOC-06B UI baseline, preserved owner-confirmed current-allocation and Payment Profile capability choices, and removed fixed screen/step wording without adding test IDs or technical thresholds. |
| 0.1.26 | 2026-07-31 | Aligned UX acceptance coverage with the distinct Payment Instruction and incomplete Checkout Workspace model and DOC-09 domain-versus-route ownership. |
| 0.1.25 | 2026-07-29 | Added acceptance coverage for the capability-aware AUTH-RECOVERY baseline, explicit outcome-resolution separation, neutral recovery messaging, session revocation, safe return, and controlled Support or stop handling. |
| 0.1.24 | 2026-07-28 | Added acceptance coverage for HK-only Phone Verification, five-state Identity Verification and banners, no voluntary re-verification after Verified, and the defined six-digit Payment Passcode Set/Change/Reset flows. |
| 0.1.23 | 2026-07-28 | Corrected first-time identity-verification acceptance, added Phone Verification ownership coverage, and marked detailed verification/passcode screen and security behavior as pending DOC-19/DOC-20 work. |
| 0.1.22 | 2026-07-28 | Added acceptance coverage for Entrance, Fast/Full Login, Recovery, non-reserving registration attempts, Account Activation and banners, one-month Fast Login, uniqueness conflicts, display-name boundary, protected return, and the mandatory-but-open authentication outcome/message mechanism. |
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
