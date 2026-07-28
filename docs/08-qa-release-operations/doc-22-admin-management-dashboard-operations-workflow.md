# DOC-22 - Admin Management Dashboard and Operations Workflow

## 1. Purpose

## 2. Scope

## 3. Out of Scope

## 4. Admin User Roles

## 5. Admin Permission Model Summary

## 6. Admin Dashboard Overview

## 7. Operations Queues

### 7.1 Account Review Queue
### 7.2 Payee Review Queue
### 7.3 Evidence Review Queue

Future full DOC-22 drafting must define admin queue behavior for DOC-06C Bills evidence routes.

Required items to be updated include:

- review evidence submitted from `BILLS-EVIDENCE-UPLOAD`;
- view the current active evidence set from `BILLS-EVIDENCE-DETAIL`;
- assign or override evidence-processing status, including `Pending Review`, `Accepted`, `Correction Needed`, `Update Needed`, `Rejected`, and `Duplicate Suspected`; archive visibility and previous-version history must remain separate;
- capture reason codes, reviewer identity, timestamp, and affected bill/rent readiness status;
- manage archive-not-delete behavior, per-user archive projections, parent-obligation archive/restore eligibility and blockers, non-restorable previous versions, expired non-restorable archives, retention disposition, and controlled access to prior evidence versions without mutating the counterparty projection or canonical obligation;
- route status changes to DOC-08 notifications or dashboard-only action items where applicable;
- audit all evidence view, status-change, archive, override, and sensitive-field reveal actions.

Detailed schema and event taxonomy belong in DOC-18. User-facing evidence routes belong in DOC-06. Evidence verification rules belong in DOC-12. Risk escalation rules belong in DOC-14.

### 7.4 Payment Request Review Queue

Future full DOC-22 drafting must present request review without one overloaded status field.

Required items to be updated include:

- filter and display the canonical request lifecycle: `Draft`, `Pending Evidence Verification`, `Pending Receiver Action`, `Accepted`, `Rejected`, `Expired`, and `Cancelled`;
- display sender/receiver role-facing projections separately from the underlying lifecycle state;
- preserve request events, timestamps, actors, reasons, delivery/share history, reminders, party linking, archive, and restore history;
- display evidence status, obligation readiness, linked support/dispute case, payment/payout status, and archive visibility as separate fields or linked records;
- prevent admin overrides from silently converting an event, evidence outcome, readiness result, case status, payment outcome, or archive action into a request lifecycle state;
- audit every permitted lifecycle correction, case/hold action, visibility change, and reason code.

Detailed request state and event structures belong in DOC-18. Product lifecycle meaning belongs in DOC-06A; route display belongs in DOC-06B; evidence, readiness, case, payment, payout, and notification meaning remain in their owning documents.

### 7.5 Risk Review Queue
### 7.6 Duplicate Detection Queue
### 7.7 Dispute Queue

Disputes and clarification work must use the linked case lifecycle `Open`, `Pending Information`, `Under Review`, `Resolved`, and `Closed`. Operational actions and outcomes such as approval, rejection, processing, completion, failure, escalation, or hold application must be recorded separately and must not overwrite request lifecycle state.
### 7.8 Clarification Queue
### 7.9 Failed Payment Queue
### 7.10 Payout Exception Queue

Future full DOC-22 drafting must distinguish destination-attributable exceptions that a user or reviewer can correct from transient bank, rail, provider, or system exceptions. Only the former should make a Receiving Info profile `Action Required`; both remain visible in the appropriate payout/operations queue.
### 7.11 Refund/Reversal Queue
### 7.12 Compliance Escalation Queue
### 7.13 Campaign and Promotion Review Queue
### 7.14 Reward Entitlement and Voucher Exception Queue
### 7.15 Authentication and Account Activation Review

Future full DOC-22 drafting must support controlled authentication and Account Activation operations without exposing credentials, OTPs, passcodes, raw provider payloads, or unnecessary identity data.

Required capabilities should include:

- locate permitted registration-attempt, authentication, session, and Account Activation events by user/account reference, attempt ID, occurrence/event ID, or correlation ID;
- show approved operational Outcome classifications, selected Resolution Strategies, and reason categories separately from persistent account status and user-facing message text;
- use the DOC-07 Authentication Outcome, Resolution, Message, and CTA Matrix for Message ID, disclosure, action, destination, and notification-treatment alignment;
- support authorized review of primary-email, phone, identity, provider-link, and account-creation uniqueness conflicts without automatically merging or linking accounts;
- inspect Fast Login eligibility renewal/revocation and current-device session revocation without storing or revealing plaintext passwords or protected device secrets;
- configure and monitor registration-attempt expiry, OTP invalidation, rate limits, abuse controls, and cleanup while ensuring temporary attempts do not reserve identifiers or grant account rights;
- apply the five user-facing identity projections `Not Verified`, `Processing`, `Verified`, `Failed`, and `Update Required` without presenting raw provider states as product statuses;
- prohibit administrators from directly setting identity status to `Verified`, bypassing Account Activation, reading OTPs/passcodes, selecting a replacement passcode, or marking phone verification complete without the approved verification result;
- permit an authorized administrator to set identity status to `Not Verified` or `Update Required`; changing `Verified` to `Not Verified` requires dual approval for MVP;
- record requester, approver, prior status, new status, reason, timestamp, and case/provider reference for every identity-status reset or required-update decision;
- configure the HK$3,000 additional external/risk step-up baseline without weakening mandatory payment-passcode, payer-authorization, PSP/acquirer, card-network, regulatory, or risk controls;
- preserve controlled support-assisted payment-passcode recovery for unavailable registered phones; exact proof and waiting-period rules remain TBC for the full DOC-19/DOC-22 drafting;
- preserve controlled account-recovery cases with case and correlation IDs, disclosure-safe available-capability summaries, proof and retained-evidence references, risk/reason category, reviewer and approver assignment, cooling-off treatment, permitted recovery authorization, notifications, and complete audit history;
- require dual approval where established recovery channels are unavailable, subject to final DOC-19/DOC-21/DOC-22 proof, role, and waiting-period decisions;
- prohibit administrators from choosing passwords or passcodes, reading recovery secrets, directly creating authenticated sessions, linking providers, bypassing phone/identity/activation controls, or promising recovery where ownership assurance cannot be established;
- preserve full audit history for permitted support, security, review, and override actions.

The exact authentication Outcome Type IDs, Resolution Strategy codes/mappings, Message IDs, user-facing messages, CTA mappings, and notification treatment remain open in DOC-07. Exact recovery proof, cooling-off, restricted-account treatment, reviewer/approver roles, and technical security controls remain open in DOC-19/DOC-21/DOC-22. DOC-22 must preserve the lookup and operational-control mechanism but must not invent or override those decisions.

## 8. Admin Review Workflows

## 9. User Management Workflows

## 10. Evidence and Bill Verification Workflows

## 11. Payment Operations Workflows

Admin dashboard must support DOC-09 user payment instruction review at operations level.

Required capabilities should include:

- view payment instruction status;
- view single-card or split-card funding leg progress;
- view deferred funding date, selected payee transfer date, payment instruction action-alert status, partial funding, remaining unpaid amount, and partial payout linkage;
- view payment quote, promotion quote, reservation status, revalidation result, changed-term acknowledgement, and expiry where applicable;
- distinguish partially funded instruction from completed payment;
- trigger permitted action alert, user action, hold, cancellation, expiry, or escalation workflow according to approved policy.

## 12. Payout and Reconciliation Workflows

## 13. Refund, Cancellation, and Chargeback Operations

## 14. Risk, Fraud, AML, and Anti-Cashout Operations

## 15. Dispute and Clarification Management

## 16. Internal Notes and Case Management

## 17. Admin Actions and Status Changes

## 18. Campaign, Promotion, Coupon, Voucher, Reward, and Referral Operations

Detailed promotion-engine rules belong in DOC-13. Admin workflows should support campaign setup, offer setup, eligibility rule configuration, qualification and entitlement review, coupon/voucher issuance, miles fulfilment status, external voucher exception handling, reward reversal, and approval/audit workflow where promotions are enabled.

### 18.1 Dashboard Shortcut and Placement Configuration

Admin dashboard must support configuration hooks for the DOC-06B designated Home Dashboard flow where enabled.

Required capabilities should include:

- maintain an approved shortcut and secondary-service catalog without creating, renaming, or redirecting product destinations;
- configure the current default Home set and order up to the 8-slot maximum, including protected `More`;
- keep `More` enabled, present, and final so users retain access to shortcut management;
- enable, disable, hide, or gate catalog entries by feature, module, category, market, account/role eligibility, risk/compliance restriction, or launch phase;
- preserve account-level user order and visibility preferences where still eligible;
- resolve the effective Home set in DOC-06B precedence order: protected rules, eligibility/availability, approved catalog, current default, then user preference;
- support restore to the current eligible default rather than an obsolete historical default;
- version default/catalog changes and preserve privacy-safe handling when a previously selected entry becomes unavailable;
- prevent admin configuration from bypassing destination permissions, feature gates, or PayPlus product boundaries;
- configure Important Notice / Action Required items, including priority, expiry, collapse behavior, route target, audience, approval status, and audit log;
- configure Featured / What's New / Hot Offer carousel placements, including priority, start/end date, targeting, offer or announcement linkage, route target, approval status, enable/disable, and audit log;
- distinguish dashboard placement from notification delivery, inbox entry, campaign eligibility, and promotion entitlement;
- record admin changes to shortcut defaults, dashboard placements, carousel configuration, and notice/action items.

Detailed final admin screens, permission matrix, approval workflow, and implementation fields will be drafted in full DOC-22 and DOC-18.

#### 18.1.0 Public Entrance Content Configuration

Future full DOC-22 drafting must support controlled public content for `ENTRANCE-ROOT` and `ENTRANCE-PROMOTION-DETAIL`.

Required capabilities should include:

- configure public, non-personalized carousel content, publication status, start/end dates, priority, language, image, approved action, and route or external target;
- prevent pre-login targeting from using protected account, payment, identity, evidence, card, receiving, risk, or behavioral data;
- require approval, version history, rollback, and audit records for public Entrance content and target changes;
- keep Log In, Create Account, language, Support, and Terms access outside campaign suppression or commercial targeting controls.

Exact carousel capacity, rotation, targeting, and supported action types remain open in DOC-06B and must be configurable only after the product decision is finalized.

#### 18.1.1 Pay+ Action Availability Configuration

Future full DOC-22 drafting must support controlled availability for the five DOC-06B `PAYPLUS-ACTION-SHEET` actions:

- enable or disable an action by module, category, market, launch phase, or approved user segment;
- distinguish globally unavailable/unlaunched actions, which may be hidden, from user-specific, temporary, or review restrictions, which should remain visible but disabled with safe user-facing explanation;
- preserve the confirmed meanings, order, and destinations for `Pay a Bill`, `Pay Rent`, `Add Bill / Rent`, `Continue Payment`, and payee-to-payer `Request Payment`;
- prevent admin users from renaming, reordering, or redirecting those action semantics or bypassing destination evidence, eligibility, risk, authorization, payment, or payout gates;
- record configuration version, actor, reason, effective scope, timestamp, and rollback/audit information.

Exact admin screen, permission, approval, and implementation-field design remains for full DOC-22 drafting.

### 18.2 Reminder Default Configuration

Admin dashboard must support configuration hooks for DOC-06C bill/rent reminder defaults where enabled.

Required capabilities should include:

- configure default reminder timing for rent, monthly bills, and one-off invoices;
- configure allowed reminder cycles, offsets, and custom-date availability by category or module;
- enable, disable, or gate reminder features by feature, category, user type, eligibility, risk state, launch phase, or compliance restriction;
- configure whether system/default reminders may be disabled, reset, or replaced by user custom override;
- configure reminder notification channel availability in coordination with DOC-08;
- audit changes to reminder defaults, eligibility, channel linkage, and feature gating.

Detailed reminder data structures belong in DOC-18. User-facing reminder route behavior belongs in DOC-06.

### 18.3 Request Creation and Delivery Configuration

Admin dashboard must support future configuration hooks for DOC-06B `REQUESTS-NEW`, `REQUESTS-DETAIL`, and request-delivery controls where enabled.

Required capabilities should include:

- configure request feature/module availability by user type, category, risk state, launch phase, or compliance restriction;
- configure request expiry, resend eligibility, reminder cooldown, maximum reminders per period, and cancellation rules;
- configure whether specific categories require admin review or approved exception before evidence-gated request delivery;
- configure approved request delivery and sharing channels, including in-app, app link, WhatsApp deeplink, QR code, or other approved channels;
- distinguish request reminders from new request creation;
- audit request creation, evidence-gated send, resend, reminder, cancellation, share-link generation, and channel-configuration changes.

### 18.4 Payment Profile and Tokenized Card Configuration

Admin dashboard must support future configuration and operations hooks for DOC-06B `PAYMENT-PROFILE-ROOT`, DOC-09 payment profile use, and DOC-19 tokenization controls where enabled.

Required items to be updated include:

- configure controls for the MVP maximum of 6 cards per payment profile and checkout split;
- configure default confirmation behavior, optional user-enabled payment-passcode confirmation, and risk/PSP/security step-up rules for card removal/update;
- view masked tokenized card and payment profile status without exposing raw card data, CVV, sensitive authentication data, or full token secrets;
- view profile action-required reasons such as removed, expired, suspended, invalid, or unavailable card;
- support permitted suspend/reactivate/flag workflows for risk, support, or partner requirements;
- audit card add, tokenization return, card removal/archive, default-card change, profile create/edit/remove, profile star/unstar, and profile action-required resolution.

Detailed Payment Profile route behavior belongs in DOC-06B. Checkout use belongs in DOC-09. Tokenization and card-security controls belong in DOC-19. Notification routing belongs in DOC-08. Data, state, and audit-event taxonomy belongs in DOC-18.

### 18.5 Offers Collection, Placement, and Application Configuration

Future full DOC-22 drafting must support the confirmed DOC-06B, DOC-09, and DOC-13 Offers behavior without redefining promotion logic.

Required capabilities include:

- assign one Offer ID to one or more discovery collections;
- configure Featured / Hot placement separately from collection membership;
- configure the primary `OFFERS-ROOT` placement and suppress unintended repeated root display of the same Offer ID by default;
- allow an approved, audited override for intentional repeated root placement;
- configure pinning and display priority separately for each collection;
- configure offer enablement, display dates, targeting, labels, and publication approval;
- configure whether an offer is payment-method-sensitive and automatically applied or belongs to the separate user-selected coupon/voucher/discount family;
- configure the approved user-value amount/method and deterministic equal-value or non-comparable tie-break used to auto-select the best eligible Card Offer;
- audit collection assignment, placement, priority, override, value-comparison, and application-mode changes.

Detailed eligibility, stacking, value comparison, and benefit calculation belong in DOC-13. Same-screen checkout behavior belongs in DOC-09. Final data objects and events belong in DOC-18.

### 18.6 Referral Program, Campaign, and Qualification Configuration

Future full DOC-22 drafting must support the confirmed DOC-06B and DOC-13 Referral baseline without redefining referral or reward logic.

Required capabilities include:

- enable or disable the PayPlus Referral Program and individual campaigns;
- support one MVP campaign and preserve support for multiple future campaigns;
- configure separate referrer and referee offers and beneficiary-role entitlements;
- configure qualifying conditions, source events, payment/risk finality, qualification periods, campaign end, claim deadlines, reward usage expiry, quotas, and per-user limits as separate controls;
- reserve quota/value when each role-sensitive entitlement is created and preserve the applicable campaign, offer, benefit, and terms snapshot;
- keep reusable user-linked referral codes non-expiring by default while preserving optional future validity controls;
- configure campaign availability, terms, share channels, and campaign-specific registration context;
- review privacy-safe attribution and qualification records without exposing unnecessary bills, evidence, payments, cards, KYC data, payees, or internal risk reasons;
- hold, release, reject, reverse, or claw back referral entitlements or issued rewards according to approved permissions, reason codes, and audit rules; an authorized hold on a claimed item must support the inactive `Under Review` History presentation defined by DOC-06B without exposing internal reasons;
- reconcile duplicate, concurrent, retried, or uncertain claim submissions against the existing entitlement-to-instrument issuance result without creating another reward;
- support controlled attribution correction only if later approved, with reason capture, authorization, and full audit history;
- audit campaign changes, rule changes, qualification decisions, manual overrides, entitlement actions, claim outcomes, and reward issuance linkages.

Detailed Referral route behavior belongs in DOC-06B. Referral, qualification, entitlement, and reward rules belong in DOC-13. Privacy and masking belong in DOC-15. Final objects, identifiers, statuses, events, and lineage belong in DOC-18.

### 18.7 Reward Instrument and Fulfilment Operations

Future full DOC-22 drafting must support the confirmed canonical reward lifecycle without redefining DOC-13 business rules.

Required capabilities include:

- manage activation and operational readiness for launch-supported external-voucher and miles fulfilment methods;
- view instrument type, earning source, participant role where applicable, program, campaign/offer/entitlement source, fulfilment method, and canonical status as separate dimensions;
- review Action Required, In Progress, Under Review, unknown-result, partner-failure, duplicate-use, and reconciliation exceptions;
- perform permitted hold, release, reverse, void, restore, reissue, or fulfilment-retry actions with permission, reason, user-notice, and audit controls;
- prevent duplicate issuance or use by reconciling repeated, concurrent, retried, and uncertain operations against the authoritative result;
- configure the seven-calendar-day expiring-soon default and later approved fixed-count usage where enabled;
- define hold-versus-expiry behavior after the open DOC-13 policy decision is resolved;
- restrict credential reveal, export, partner payload, and internal reason access according to DOC-15 and DOC-19.

Detailed reward logic and status meaning belong in DOC-13 and the status-display reference matrix. User-facing screens belong in DOC-06B, checkout selection in DOC-09, privacy in DOC-15, and final objects/events in DOC-18.

### 18.8 Me Route, Account-Control, and Receiving Info Configuration

Future full DOC-22 drafting must support the confirmed DOC-06B `ME-ROOT` baseline without turning the admin dashboard into the owner of user-facing route behavior.

Required controls include:

- preserve `ME-ROOT` as a permanent MVP bottom-navigation destination;
- prevent ordinary configuration from hiding core Account Information, Security & Privacy, Help & Support, About PayPlus, Terms and Policies, or Log Out controls;
- enable or disable optional module rows, including Membership, while preserving the MVP `RECEIVING-INFO` capability and permitted access to retained user records;
- manage account and identity-verification action-required cases, provider exceptions, retries, and the five-state mapping without exposing provider payloads or internal reasons in user-facing routes or creating duplicate verification submissions;
- support controlled recovery where a user cannot access the registered phone or email, with identity checks, reason capture, approval, notification, and audit evidence;
- support contact-change exception handling and audit for the confirmed cross-channel phone/email verification flows;
- resolve duplicate-primary-email and external-provider-link conflicts through controlled support or security workflows without automatically merging accounts by email;
- support audited Google/Apple login-method link and unlink exceptions, first-password setup state, and the safeguard that prevents removal of an account's final usable login method;
- expose restricted-account and Account Activation gate outcomes for authorized support and operations roles without allowing admin configuration to bypass phone, identity, passcode, payer-verification, or authorization requirements;
- manage privacy requests through controlled queues using `Submitted`, `In Progress`, `Action Required`, `Completed`, and `Unable to Complete` user-facing projections, with internal reasons, service timelines, assignee, and evidence retained separately;
- issue, revoke, expire, and audit protected in-app data exports without sending the export as an ordinary email attachment;
- manage account-closure blockers, cancellation before finalization, operational finalization, session termination, login disablement, retained-record access, and completion notice without treating closure as immediate deletion;
- support trusted-device removal and session revocation audit, including current-device logout behavior;
- preserve optional direct-marketing, personalization, and approved partner-data-use choices while preventing users or administrators from disabling mandatory service, payment, security, risk, compliance, tax, audit, dispute, and retention processing;
- configure enabled receiving methods and method-specific fields without inventing unsupported provider validation;
- support multiple user-linked Receiving Info profiles, optional nicknames, version/archive history, and masked operational views;
- configure identity-name normalization and evidence requirements used to propose `Ready to Receive`, without presenting that result as external bank validation;
- route third-party, company, ownership-mismatch, and proof-deficient profiles to controlled review with permitted approval or `Action Required` outcomes;
- keep the private Receiving Info library separate from request, obligation, payment, and payout destination snapshots;
- ensure source-profile edit or archive does not rewrite accepted or payer-authorized snapshots;
- distinguish destination-attributable payout failures from transient bank, rail, provider, or system failures;
- support linked-payee destination-change notifications and optional controlled save-to-Receiving-Info without adding payee approval or payout delay;
- audit profile add, edit, version, archive, proof submission, review, status change, destination selection, snapshot creation, destination difference acknowledgement, linked-party notification, and payer reauthorization;
- support `ARCHIVED-ROOT`, `ARCHIVED-BILLS-LIST`, and `ARCHIVED-DOCS-LIST` operational handoffs without merging obligation archive, evidence processing, payment readiness, or retention disposition;
- prevent standalone archive of the sole current evidence linked to an active obligation;
- preserve accepted replacement lineage, mark prior versions non-restorable, project current evidence into Archived Documents whenever its parent obligation is archived, and recheck evidence validity when an eligible archived obligation is restored;
- distinguish obligations archived while eligible for later restore from already-expired obligations that are manually archived and non-restorable;
- keep archive/restore user-scoped, prevent it from cancelling or releasing active request/payment/payout/refund/dispute/risk/legal processes, and audit the blocker or override reason;
- define admin restore-on-behalf permission, reason, approval, user-notice, and audit rules in the full DOC-22 before enabling that capability; the product route baseline does not grant it implicitly;
- support controlled archived/previous evidence access, denial, legal hold, retention, and disposition audit under DOC-06C, DOC-12, DOC-15, and DOC-18;
- audit sensitive reveal, account/profile changes, privacy requests, receiving-destination changes, optional-row configuration, and account restriction or closure operations;
- preserve the separate More boundary for dashboard shortcut management, reorder/arrangement, restore-default, overflow, and secondary services.

Detailed `ME-ROOT` and `RECEIVING-INFO` route behavior belongs in DOC-06B. Notification preferences belong in DOC-08, payout-destination rules in DOC-10, evidence in DOC-06C/DOC-12, risk in DOC-14, privacy in DOC-15, and final objects/events in DOC-18.

### 18.9 Notification Configuration and Operations

Future full DOC-22 drafting must support the DOC-06B/DOC-08 Notifications baseline without making the admin dashboard the owner of domain status or user-route behavior.

Required capabilities include:

- maintain stable notification event definitions and approved `System`, `Service`, `Transaction`, or `Promotion` category assignment;
- map each recipient-specific message to its event type, source event/object, recipient and role, template version, registered route target, correlation/causation/deduplication references, and optional batch/campaign/manual/support/scheduled-job reference;
- search by notification message ID, event ID, batch ID, source reference, recipient, template, route target, channel attempt, provider reference, and permitted time range;
- distinguish recipient Inbox `Unread` / `Read` / `Archived` presentation from delivery status, owning-domain status, and owning-domain Action Required;
- prevent manual/admin actions from inventing or clearing a domain status or Action Required condition;
- configure event enablement, channel availability, working service classification, fallback/retry, quiet hours, scheduling, rate limits, duplicate suppression, and retention subject to DOC-08/DOC-15;
- label mandatory service communications as required and prevent preference/admin configuration from disabling them contrary to approved policy;
- keep direct-marketing, personalization, and approved partner-data-use consent in `PRIVACY-DATA-CONTROLS`, while notification settings govern permitted delivery;
- support approved templates, versioning, preview, legal/compliance approval, rollback, and audit;
- log each channel attempt and outcome separately from the Inbox message record;
- support safe unavailable-target handling and current-state revalidation before a user-facing action remains available;
- preserve read/archive history, message snapshots, provider outcomes, and admin actions according to approved retention and access rules.

DOC-08 owns event eligibility, user communication rules, channels, templates, and preferences. DOC-06B owns user-facing routes and return behavior. Domain owners and the status-display reference matrix govern displayed status meaning. DOC-18 owns final schema, lineage, and event taxonomy. Final provider selection, permission matrix, scheduling UI, operational SLA, and retention/disposition workflow remain open for full DOC-22 drafting.

## 19. Audit Logging Requirements

## 20. Notifications and Escalations

## 21. Dashboard Screen Inventory

## 22. Reporting and Export Requirements

## 23. Security and Access Control Requirements

Admin access must be role-based and aligned with DOC-15 and DOC-19. Sensitive identity, evidence, payment, payout, risk, promotion, support, and authentication/security data should use masking, controlled reveal, reason capture, and audit logging.

Admin users should not access raw card data, CVV, sensitive authentication data, full token secrets, or unrestricted identity/evidence files unless explicitly approved under the final security and privacy model.

## 24. Privacy and Data Handling Requirements

Admin screens must respect DOC-15 data classification and DOC-18 field metadata.

Required admin data-handling controls should include:

- field-level visibility by role, queue, and approved purpose;
- masking and reveal rules for sensitive fields;
- access reason capture for sensitive data views, exports, downloads, overrides, and corrections;
- audit logging for access, change, export, review, hold, release, override, and deletion actions;
- audit logging for dashboard shortcut configuration, dashboard placement configuration, notice/action configuration, carousel configuration, restore-default configuration, and reminder default configuration;
- privacy-safe duplicate/reused evidence warnings that do not reveal another user's private data;
- export controls for reports, bank files, payout batches, evidence packages, dispute files, and promotion/partner reports.

Detailed workflow, screen design, and permission matrix will be drafted in full DOC-22.

## 25. Monitoring and Incident Response Linkage

## 26. MVP Acceptance Criteria

## 27. Open Questions

## 28. Revision History

| Version | Date | Summary |
| --- | --- | --- |
| 0.21.0 | 2026-07-29 | Aligned future authentication administration with capability-aware Recovery, the Outcome/Resolution/Message/CTA separation, controlled Support recovery cases, dual approval, and explicit administrator prohibitions while leaving security and operational details TBC. |
| 0.20.0 | 2026-07-28 | Added future admin controls for the five-state identity model, prohibited direct verification/passcode bypass, required dual approval for Verified-to-Not-Verified reset, recorded reset audit fields, preserved support-assisted passcode-recovery TBCs, and added the configurable HK$3,000 step-up baseline. |
| 0.19.0 | 2026-07-28 | Added future operational controls for temporary registration attempts, authentication outcome/message/correlation lookup, account-activation conflicts, Fast Login/session handling, and approved public Entrance content while preserving DOC-07 ownership of exact IDs and messages. |
| 0.18.0 | 2026-07-27 | Added future admin and support markers for unique-primary-email conflicts, explicit provider login-method links, first-password state, final-login-method protection, and restricted-account financial-activation gates. |
| 0.17.0 | 2026-07-27 | Added future admin requirements for notification event/message/batch/source traceability, category and signal separation, lookup, templates, channels, preferences, delivery attempts, current-state actions, retention, and audit. |
| 0.16.0 | 2026-07-27 | Aligned future admin controls with defined `MORE-ROOT` catalog/default management, 8-slot maximum, protected More access, eligibility precedence, account-level preferences, current-default restore, configuration versioning, and destination-boundary protection. |
| 0.15.0 | 2026-07-27 | Added future Pay+ action availability configuration, hidden-versus-disabled rules, fixed semantic boundaries, destination-gate protection, and audit requirements. |
| 0.14.0 | 2026-07-26 | Added future per-user archive-projection, archived-obligation blocker/eligibility, current-evidence cascade, canonical-record protection, and operational audit requirements; admin restore-on-behalf remains to be defined in the full DOC-22. |
| 0.13.0 | 2026-07-26 | Added future archive-family controls, separate archive/history descriptors, sole-current-evidence protection, parent archive/restore, non-restorable expiry/history, access, retention, and audit requirements. |
| 0.12.0 | 2026-07-26 | Added future admin requirements separating canonical request lifecycle, role projections, events, evidence, readiness, linked cases, payment/payout status, and archive visibility, plus the canonical linked-case lifecycle. |
| 0.11.0 | 2026-07-23 | Added future Receiving Info method configuration, profile/proof review, readiness, version/archive, snapshot separation, payout-failure classification, linked notification, save invitation, and audit requirements. |
| 0.10.0 | 2026-07-22 | Added future operations markers for identity-provider exceptions, support-assisted recovery, cross-channel contact changes, privacy-request queues, protected exports, account-closure blockers/finality, trusted-device revocation, and optional-versus-mandatory privacy controls. |
| 0.9.0 | 2026-07-22 | Added future admin and operations markers for permanent `ME-ROOT`, protected core controls, optional-row enablement, account action-required handling, Receiving Details, archived-evidence access, reveal/privacy auditability, and the separate More shortcut-management boundary. |
| 0.8.0 | 2026-07-21 | Added future Reward operations markers for launch-supported partner/miles readiness, separate data dimensions, lifecycle and exception queues, authoritative/idempotent fulfilment, expiry configuration, hold-versus-expiry follow-up, and credential access controls. |
| 0.7.0 | 2026-07-21 | Added future Referral admin markers for entitlement-time quota reservation and terms snapshot, separate campaign/claim/use dates, idempotent claim oversight, and authorized hold/release handling for exceptional `Under Review` presentation. |
| 0.6.0 | 2026-07-21 | Added future Referral Program, campaign, role-sensitive offer, qualification, finality, quota, validity, privacy-safe review, entitlement hold/release/reversal, attribution-correction, and audit configuration markers. |
| 0.5.0 | 2026-07-20 | Added future admin markers for multi-collection Offers, primary root placement, duplicate suppression and override, per-collection priority, payment-method-sensitive application mode, highest-user-value comparison, and audit controls. |
| 0.1.0 | 2026-06-17 | Added DOC-06 reminder default configuration hooks for bill/rent reminder timing, category gating, channel linkage, and audit logging. |
| 0.2.0 | 2026-06-18 | Added future DOC-22 update markers for admin handling of DOC-06 Bills evidence detail/upload routes, evidence statuses, readiness impact, archive-not-delete behavior, prior evidence access, notifications, and audit logging. |
| 0.3.0 | 2026-07-02 | Added future DOC-22 configuration markers for DOC-06B request creation, evidence-gated request delivery, resend/reminder limits, sharing channels, and audit logging. |
| 0.4.0 | 2026-07-06 | Added future admin configuration and operations markers for DOC-06B Payment Profile route, tokenized card status, payment profile action-required handling, max 6-card payment/profile limit, default confirmation behavior, optional user-enabled payment-passcode confirmation, and audit logging. |
