---
document_id: DOC-15
title: Privacy, Data Protection & Record Retention Specification
version: 0.8.19
status: Founder Working Baseline
owner: Privacy / Compliance
reviewers:
  - Product Lead
  - Privacy Lead
  - Compliance Lead
  - Risk Lead
  - Security Lead
  - Engineering Lead
  - Data Lead
  - Operations Lead
  - Legal Lead
approvers:
  - Project Owner
  - Privacy Lead
  - Compliance Lead
  - Security Lead
last_updated: 2026-07-29
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Product Overview & Positioning
  - DOC-03 Regulatory, PSP & Acquirer Assessment
  - DOC-04 Compliance Certification Roadmap & Control Framework
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06 User Journey, UX Flow & Service Blueprint
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Rules
  - DOC-09 Payment Request, Multi-Funding Source & Settlement
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Risk Controls
  - DOC-17 API & Third-party Integration
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization & Authentication
  - DOC-21 Monitoring, Incident Response & Operations Runbook
  - DOC-22 Admin Management Dashboard Operations Workflow
  - DOC-99 ISMS Policy Library
---

# DOC-15 - Privacy, Data Protection & Record Retention Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-15` |
| **Title** | Privacy, Data Protection & Record Retention Specification |
| **Version** | `0.8.19` |
| **Status** | Founder Working Baseline |
| **Owner** | Privacy / Compliance |
| **Reviewers** | Product Lead<br>Privacy Lead<br>Compliance Lead<br>Risk Lead<br>Security Lead<br>Engineering Lead<br>Data Lead<br>Operations Lead<br>Legal Lead |
| **Approvers** | Project Owner<br>Privacy Lead<br>Compliance Lead<br>Security Lead |
| **Last Updated** | `2026-07-29` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Request, Multi-Funding Source & Settlement<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow<br>DOC-99 ISMS Policy Library |

---

## 1. Purpose

This document defines PayPlus privacy, data protection, data classification, visibility, masking, lawful-use, consent, vendor, and record-retention requirements.

PayPlus is a data-driven payment platform. It may collect, derive, retain, and use data from account activity, evidence verification, payment behavior, payout handling, risk review, support activity, and promotion activity to operate the service, verify obligations, reduce fraud, improve user experience, support analytics, manage commercial performance, and meet legal, audit, tax, compliance, partner, and operational requirements.

This document is not a final privacy policy, legal opinion, database schema, security architecture, authentication specification, or operations runbook.

---

## 2. Scope and Ownership

DOC-15 covers:

- data-use principles;
- data classification;
- account, identity, evidence, payment, payout, risk, promotion, support, and analytics data handling;
- user, payer, payee, admin, system, and vendor visibility boundaries;
- masking and access-control expectations at privacy-rule level;
- consent and communication privacy boundaries;
- retention, deletion, legal hold, and audit-record expectations;
- data subject access and correction support;
- vendor and cross-border processing expectations.

Detailed specifications belong to:

| Topic | Owning Document |
| --- | --- |
| Product scope and user journeys | DOC-05, DOC-06, DOC-06A, DOC-06B, DOC-06C |
| User-facing notices, disclosures, and authorization wording | DOC-07 |
| Notification channels, templates, consent, and delivery logging | DOC-08 |
| Payment profiles, tokenization boundary, and payment authorization data | DOC-09 |
| Payout, bank record, and reconciliation records | DOC-10 |
| Refund, dispute, chargeback, and evidence packages | DOC-11 |
| Evidence extraction, displayable fields, and document-derived data layers | DOC-12 |
| Promotion, referral, membership, reward, and partner offer data | DOC-13 |
| AML, anti-cashout, fraud, risk holds, and risk-review data | DOC-14 |
| API, provider, webhook, file, and third-party integration details | DOC-17 |
| Final data model, event schema, ledger, reporting, and warehouse design | DOC-18 |
| Authentication, encryption, RBAC, secrets, device security, and PCI controls | DOC-19 |
| Incident response, monitoring, and operational escalation | DOC-21 |
| Admin dashboard workflows, permissions, uploads, overrides, and review queues | DOC-22 |

---

## 3. Current Decision Baseline

| Area | Baseline |
| --- | --- |
| Launch market | Hong Kong. |
| Data strategy | PayPlus should support broad, lawful, purpose-linked data collection and analytics while preserving trust, consent, data minimization, access controls, and product-boundary restrictions. |
| Account creation and activation | A temporary registration attempt creates no account and reserves no identifier. Restricted account creation requires one unique verified primary email, accepted Terms and Privacy notices, and at least one usable login method. Verified phone, identity verification, and six-digit payment-passcode setup may be completed later but are mandatory through `ACCOUNT-ACTIVATION` before full registration and financially restricted actions. |
| Identity verification | Individual identity verification is expected through Jumio or equivalent provider. PayPlus may receive or store required identity attributes, provider references, verification outcomes, and approved evidence artifacts. |
| KYC attributes | Name, ID number, sex, ID document data, and other provider-returned attributes may be used where connected to KYC, risk, compliance, payee verification, audit, support, or legal purpose. |
| Login methods | One PayPlus account may use email/password and explicitly linked Google and Apple provider identities. Provider identities are linked by stable provider identifier, never by email match alone. |
| Primary email | One verified primary email may belong to only one PayPlus account. A provider-returned verified email may be selected; another entered email must be verified before use. |
| Password | A password is required only when email/password login is enabled. A social-authenticated account may set its first PayPlus password later through `ACCOUNT-SECURITY`. |
| Biometric unlock | User-enabled Fingerprint and Face ID may support device-local Fast Login. PayPlus should not store biometric templates or plaintext passwords. |
| New-device 2FA | Required on new device. SMS OTP is primary; email OTP or email deeplink may be fallback. |
| Fast Login | Eligibility uses a rolling one-month period renewed by each successful login and may be revoked earlier by risk, device, credential, account, or security changes. A separate dormant-account threshold remains open. |
| Payment confirmation | Payment passcode is required for proceeding with payment. Higher-risk activity may require additional step-up under DOC-14 and DOC-19. |
| Password reset | Email deeplink is supported, with single-use, short-lived, auditable reset flow. |
| Record retention | Payment, account, tax, audit, receipt, statement, proof-of-payment, dispute, chargeback, and compliance records are expected to use a 7-year baseline, subject to final legal and privacy review. |

Unconfirmed provider, retention exception, deletion, cross-border, sanctions, biometric, and security details should remain editable assumptions until confirmed.

---

## 4. Data Principles

| Principle | Requirement |
| --- | --- |
| Lawful data utility | PayPlus may collect and use data where there is a defined product, payment, compliance, risk, operational, analytical, commercial, support, audit, tax, legal, or partner purpose. |
| Purpose-linked use | Each data class should have documented purposes and permitted use cases. |
| Data engine readiness | Data structures should support analytics, segmentation, risk intelligence, evidence quality, commercial reporting, and future model improvement where allowed. |
| Model-use governance | AI/model improvement, segmentation, personalization, partner reporting, and decision-support use should be governed by approved purpose, field classification, consent/preference state, prohibited-input rules, lineage, monitoring, and human-review requirements where applicable. |
| Transparency | Users should receive appropriate notices for account, identity, evidence, payment, communication, and marketing data handling. |
| Role-based visibility | Users, payees, admins, systems, vendors, and partners should see only the data needed for their approved role or task. |
| Mask by default for sensitive fields | Sensitive identity, evidence, payment, payout, and risk fields should be masked or restricted unless full access is needed for an approved purpose. |
| Auditability | Access, use, correction, export, deletion, override, review, and disclosure actions should be logged where material. |
| Retention discipline | Records should be retained for required business, legal, tax, audit, compliance, dispute, chargeback, risk, and partner purposes, then deleted, archived, or de-identified under approved rules. |

---

## 5. Data Classification

PayPlus data should be classified by source, sensitivity, and permitted purpose.

| Data Class | Examples | Core Uses |
| --- | --- | --- |
| Registration Attempt Data | Temporary attempt ID, proposed but unreserved identifiers, provider/OTP/referral/consent context, timestamps, inactivity expiry, completion/abandonment outcome, abuse-control and correlation references. | Registration continuity, duplicate prevention, abuse control, audit, and support without creating an account. |
| Account Identity Data | Unique primary email, phone, nickname/display name, account ID, user type, registration date, restricted-account and account-activation state, verification status. | Account operation, notices, fraud prevention, support, analytics. |
| Authentication and Security Data | Login-method type and state, stable external-provider subject/reference, provider-link status, password-set status and hash where applicable, payment passcode hash, OTP events, device ID, session logs, remembered masked-email reference, Fast Login eligibility, login history, failed attempts, new-device flags, biometric unlock status. | Authentication, account linking, step-up, security monitoring, incident investigation. |
| KYC / KYB Data | Provider reference, ID type, ID number, name, sex where returned, date of birth where required, nationality where required, Business Registration document, owner ID, verification outcome. | Onboarding, compliance, payee approval, risk control, dispute and chargeback evidence. |
| Evidence and Obligation Data | Bills, invoices, tenancy agreements, contracts, OCR text, extracted fields, corrected fields, final evidence snapshot, landlord/payee details, property address, due date, amount, reference number. | Payment validation, autofill, payer review, payee verification, duplicate detection, audit, analytics. |
| Payment and Funding Data | Request ID, amount, fees, quote, quote revalidation result, payment instruction, funding leg, deferred funding date, selected payee transfer date, authorization record, payment token reference, masked card summary, permitted masked cardholder name, card nickname, card brand, expiry, issuer/BIN metadata where available, default-card marker, saved split-card profile name, profile ratios, starred/frequent marker, profile action-required state, multi-card split, partial funding status, step-up result, PSP reference. | Payment processing, risk, reconciliation, chargeback defense, product analytics. |
| Payout and Payee Data | Payee profile, landlord/business payee data, Receiving Info profile ID, owner, nickname, method, version, readiness, proof reference, archive state, request/obligation/payment destination snapshot, source reference, bank/FPS/cheque/EPS details, payout status, payout batch, bank reference, reconciliation result. | Payout execution, payee validation, reconciliation, fraud prevention, support. |
| Participant Linking and Invitation Data | User-initiated search/input, invitation channel, deeplink/QR/app-link reference, pending participant record, linking acceptance/decline, linked participant role, and linkage audit trail. | Two-sided visibility, request delivery, support, fraud prevention, privacy-controlled communication. |
| Risk and Compliance Data | Risk score/band, rule triggers, AML/sanctions status, duplicate evidence signals, same-party indicators, fraud flags, payout holds, admin review outcome, escalation records. | Anti-cashout, fraud prevention, compliance control, monitoring, audit. |
| Refund, Dispute, Chargeback, and Support Data | Support tickets, user messages, dispute reason, refund case, chargeback reason code, evidence package, resolution, recovery/write-off status. | Support, dispute resolution, chargeback defense, operational learning, reporting. |
| Promotion, Referral, and Membership Data | Campaign eligibility, promotion quote reservation, coupon/voucher library, reward instrument type, earning source, program context, campaign/offer/entitlement source, fulfilment method, reward entitlement, opaque user-linked referral code/reference, registration attribution, masked referee phone, qualification progress/outcome, beneficiary role, entitlement-to-instrument link, membership tier, miles account reference, redemption status. | Growth, campaign operation, partner reporting, reward fulfilment, attribution, abuse detection. |
| Communication and Notification Data | Notification event ID, recipient-specific message ID, optional batch ID, category, source event/object, recipient role, template version, target route/object, read/archive state, status/action-at-send snapshot, channel preference, per-channel delivery attempt, provider reference, timestamps, reminder linkage, and WhatsApp/SMS/email/push logs. | Service communication, consent/preference operation, audit, support, communication performance. |
| UI Preference and Personalization Data | Approved shortcut-catalog/default version, account-level shortcut order and visibility, effective availability, restore-current-default action, dashboard placement exposure, carousel impression/action, Inbox read/archive interaction, Me destination use, notification preference, language, theme, and other user-selected display preferences. | Product operation, cross-device user preference, consented marketing/promotion display, analytics, and audit where required. |
| Behavioral and Product Analytics Data | Feature usage, funnel steps, payment patterns, category usage, correction behavior, conversion, drop-off, retry behavior, spend behavior, payer/payee relationship patterns, dashboard shortcut usage, reminder opened/ignored/actioned behavior, and placement performance. | Product improvement, risk intelligence, commercial analytics, segmentation. |
| Derived and Aggregated Data | Risk indicators, user segments, category economics, OCR quality metrics, fraud trends, campaign performance, anonymized or aggregated insights, model features where approved. | Analytics, approved model improvement, business intelligence, strategic decisions. |

Detailed fields, schemas, lineage, event names, feature/model metadata, and reporting tables belong in DOC-18.

---

## 6. Registration, Login, and Authentication Data

PayPlus should support the following account and authentication model:

| Function | Requirement |
| --- | --- |
| Registration attempt | Before account creation, use a temporary attempt record rather than a partial account. Proposed email, phone, provider identity, and other identifiers remain unreserved; app exit permits an immediate new attempt. An inactive attempt may remain for up to 30 minutes for cleanup/security, and final creation atomically rechecks uniqueness and required gates. |
| Restricted account creation | Require one unique verified primary email, accepted Terms and Privacy notices, and one usable login method. Google/Apple registration stores the verified provider identity by stable provider identifier; email registration requires verified email and password. |
| Account activation | `ACCOUNT-ACTIVATION` completes phone verification, identity verification, and six-digit payment-passcode setup after restricted account creation. Completion removes the registration-level restriction but does not bypass feature-specific evidence, risk, payment, provider, or role gates. |
| Login methods | One account may use email/password, Google, and Apple only where each method has been explicitly enabled or linked. Matching email addresses never create or merge a provider link automatically. |
| Primary email uniqueness | A verified primary email may belong to only one PayPlus account. An attempted social registration using an existing verified primary email must stop account creation and direct the authenticated user to log in to the existing account before linking the provider. |
| Phone and identity uniqueness | One verified phone and one verified individual identity may each belong to only one active individual account. A conflict found during Account Activation blocks activation and routes to Login, Recovery, or controlled Support handling without automatic merge. |
| Password | Email/password registration sets a password. A social-authenticated account may have no PayPlus password until the user selects `Set Password` in `ACCOUNT-SECURITY`; thereafter the action becomes `Change Password`. Password storage and hashing belong in DOC-19. |
| Provider linking | Linking or unlinking Google/Apple requires an authenticated session, fresh approved reauthentication, successful provider authentication, explicit confirmation, audit, and security notification. A provider identity may link to only one PayPlus account, and the final usable login method cannot be removed. |
| Fast Login and device-local biometric | Each successful login renews a one-month Fast Login period. User-enabled Fingerprint or Face ID may activate the approved device credential; biometric templates remain on device or approved platform service. PayPlus stores no plaintext password and masks the remembered email. |
| New-device 2FA | New-device login requires step-up. SMS OTP is primary; email OTP or email deeplink is fallback. |
| Dormant-login reauthentication | Login after a configured long inactivity period should require reauthentication, such as password plus SMS OTP, email OTP, or other approved factor. |
| Payment passcode | Payment passcode is required before proceeding with payment authorization. |
| Password reset | Email deeplink must be single-use, short-lived, and logged. User should receive security notification after reset. |
| Core account changes | Changes to an existing email, phone, password, payment passcode, immutable identifier, KYC/KYB record, or payout/Receiving Info profile require payment passcode or approved reauthentication before route-specific OTP, provider, review, or confirmation controls. First-time identity verification during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode. Payment-profile changes retain their separately approved optional-passcode rule. Review is required only where risk, compliance, payout, KYC/KYB, or fraud rules require it. |

DOC-15 defines data handling and privacy boundaries. DOC-19 owns security mechanics, authentication implementation, encryption, credential storage, device controls, and RBAC.

Account recovery must be capability-aware and disclosure-safe. PayPlus may evaluate whether approved email, linked-provider, authenticated-account, or controlled Support recovery remains available, but public responses must not reveal the existence of an account, password, provider link, phone, identity record, trusted device, or internal risk restriction. A remembered device, verified phone, verified identity, or provider email is not by itself a recovery method unless DOC-19 explicitly permits that capability. Recovery records and analytics must use opaque attempt, outcome, resolution, and correlation references rather than credentials, recovery secrets, or unrestricted identity/provider payloads.

### 6.1 Material Change Handling

Material changes should be grouped by sensitivity and handled with proportionate confirmation.

| Change Type | Examples | Recommended Treatment |
| --- | --- | --- |
| Contact rebinding | Change phone or email. Nickname/display name is not a login identifier. | Require payment passcode or approved reauthentication first. For phone change, send OTP to the registered email and then verify the new phone by SMS OTP. For email change, send SMS OTP to the registered phone and then verify the new email by OTP or deeplink. Notify old and new channels where available. Route users without a trusted old channel to support-assisted identity recovery. |
| Credential or login-method change | Set or change password, link or unlink Google/Apple, change payment passcode, recovery method, or 2FA setting. | Require fresh approved reauthentication and route-specific confirmation; require successful authentication by a provider being linked; prevent removal of the final usable login method; notify user after completion. |
| Device trust change | New device, trusted-device addition/removal, device reset. | Require step-up where applicable and log the device/session event. Removing another trusted device revokes its trust and active session; removing the current device logs the user out. |
| Payment profile change | Add, remove/archive, update, suspend, reactivate, star/unstar, or change default card/payment profile. | Require payer confirmation by default; payment passcode confirmation may be enabled by user setting; step-up may still apply where risk, PSP/acquirer, or security rules require; never expose raw card data. |
| Receiving Info profile change | Add, edit, version, reveal permitted full values, or archive a bank/FPS/cheque/EPS profile. | Require payment passcode or approved reauthentication before full-value reveal and add/edit. Archive requires confirmation. Stronger step-up may apply where risk, security, provider, or compliance rules require it. Third-party/company/ownership-mismatch profiles require proof and review. |
| Effective payout destination change | Change the destination selected for a request, obligation, payment, or payout. | Preserve a new immutable snapshot, apply the role and acceptance rules in DOC-06B/DOC-09/DOC-10, warn the payer where the selected destination differs from accepted request context, and require payer reauthorization after payment authorization. |
| Identity/KYC change | Correct a governed record or respond to an admin-required identity update. A user cannot voluntarily repeat verification after `Verified`. | Preserve the verified record and audit history. An authorized admin may set `Not Verified` or `Update Required`; new provider capture may require payment passcode or approved reauthentication. First-time verification follows the Account Activation exception. |
| Marketing or communication preference change | Opt-in/out, WhatsApp/SMS/email preference, direct-marketing consent. | Require logged preference update; step-up only if account takeover risk is present. |

Material changes should create audit events and user-facing security notifications where appropriate. Detailed status, event schema, and admin workflow belong in DOC-18, DOC-19, and DOC-22.

The user-facing Two-Step Verification toggle controls optional routine step-up only. It must not disable mandatory new-device, risk-triggered, contact-change, account-closure, or provider-required authentication. Payment Passcode settings may include a user-controlled preference requiring passcode confirmation for card or payment-profile changes; the default remains ordinary confirmation unless another mandatory rule applies.

### 6.2 `ME-ROOT` Account Display and Reveal

DOC-06B `ME-ROOT` is the permanent mixed-role account-control route. Privacy requirements are:

- `ACCOUNT-PROFILE` may show editable nickname/display name, copyable PayPlus User ID, masked phone, masked email, and identity-verification status only; nickname/display name is not a login identifier;
- `ACCOUNT-SECURITY` must present the account's usable login methods, use `Set Password` where no PayPlus password exists and `Change Password` after one is set, and support explicit Google/Apple link or unlink without email-based automatic merging;
- the only identity-verification labels shown there are `Not Verified`, `Processing`, `Verified`, `Failed`, and `Update Required`; actions follow DOC-06B and the status-display matrix;
- Back or Cancel from identity verification restores `ACCOUNT-PROFILE`; completion returns with refreshed status, `Processing` must not encourage duplicate submission, and `Verified` offers no voluntary re-verification;
- full identity attributes, identity documents, provider payloads, payment credentials, evidence content, full payout details, and internal risk reasons must not appear on the root;
- revealing approved masked sensitive values in a prominent account or Receiving Info surface uses the existing PayPlus payment passcode or approved reauthentication; no second reveal-only passcode should be introduced;
- changing existing sensitive identity, contact, security, credential, or Receiving Info data requires payment passcode or approved reauthentication before the applicable OTP, provider, review, or confirmation flow; first-time identity verification during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode;
- permitted evidence, invoice, receipt, statement, and payment-proof viewing/downloading within an authenticated approved-purpose context does not require an extra passcode or step-up solely because the document is opened or downloaded;
- additional step-up may apply where risk, security, legal, provider, or data-classification rules require it;
- reveal attempts and outcomes should be logged without copying sensitive values into analytics or ordinary notification content;
- `PRIVACY-DATA-CONTROLS` should separate optional direct-marketing, personalization, and approved partner-data-use choices from mandatory service, payment, security, risk, compliance, tax, audit, dispute, and retention processing;
- `PRIVACY-DATA-CONTROLS` should support approved access/export, correction, retention/deletion requests, request history, and a contextual handoff to account closure; direct account-field edits return through `ACCOUNT-PROFILE` and notification-channel choices remain in `NOTIFICATION-SETTINGS`;
- protected data export must use time-limited in-app access rather than an ordinary email attachment;
- account closure in `ACCOUNT-PROFILE` is a controlled request, not immediate deletion. It requires payment passcode plus 2FA, checks unresolved payment and operational blockers, remains cancellable until operational finalization, and must preserve records subject to retention, dispute, audit, tax, security, compliance, and legal-hold requirements;
- completed closure blocks new activity, terminates sessions, disables login, and sends an approved completion notice; the user should be prompted to obtain available records before closure, with later access handled through support or the approved privacy process;
- `RECEIVING-INFO` must keep the user's saved profile library private from payers. List, card, and ordinary detail views mask account/identifier data while leaving bank/provider name visible; payment-passcode or approved reauthentication is required before controlled Edit reveals permitted full current values. Archive hides the profile from ordinary selection but retains versions and audit history;
- a payer may see only the destination selected for the relevant request, obligation, payment, or payout context. That context snapshot remains valid independently of later source-profile edit or archive;
- `ARCHIVED-ROOT` separates archived obligations from archived/previous evidence. Archive is a per-user visibility projection and must not change the counterparty's visibility, party linkage, canonical obligation/evidence, completed history, or retained snapshots. `ARCHIVED-DOCS-LIST` may expose only permitted archived or previous evidence through controlled, role-appropriate access and must not bypass retention, masking, disposition, or audit rules.

Detailed passcode, session, device, reauthentication, and reveal implementation belongs in DOC-19. Final event and data structures belong in DOC-18.

---

## 7. Identity, KYC, and KYB Data Handling

PayPlus may collect and use identity data to support onboarding, verification, fraud prevention, compliance, audit, account recovery, payee validation, landlord verification, dispute handling, and partner requirements.

Rules:

- identity provider reference, verification outcome, verification timestamp, and reason codes should be stored;
- ID number and identity attributes may be stored where required for verification, risk, audit, legal, support, or partner purposes;
- full ID document images or provider artifacts may be stored only where approved by legal, compliance, security, provider contract, and retention rules;
- ID number, ID copy, sex, date of birth, nationality, address, and business-owner data should be masked or restricted by default;
- admin access to identity data must be permissioned and logged;
- KYC/KYB data should link to risk, payment, payout, refund, dispute, and chargeback records where needed for traceability.

Final provider API behavior belongs in DOC-17. Data schema belongs in DOC-18. Security controls belong in DOC-19.

---

## 8. Evidence and Obligation Data Handling

Evidence data is a major PayPlus data asset.

PayPlus may collect and process bills, invoices, tenancy agreements, contracts, statements, rent demands, service records, OCR text, extracted fields, user-corrected fields, verification signals, duplicate signals, review decisions, and final evidence snapshots.

Rules:

- raw evidence, OCR text, extracted fields, user corrections, verification signals, and final evidence snapshot should remain separately traceable;
- extractable data does not mean displayable data;
- sensitive evidence fields may be stored for approved purposes while hidden or masked in ordinary UI;
- payer and payee should only see role-appropriate evidence data;
- duplicate/reused evidence warnings must not disclose another user's private information;
- evidence data may support analytics, OCR quality improvement, risk intelligence, commercial reporting, and product improvement where permitted;
- evidence access, review, correction, download, export, replacement, and deletion actions should be logged where material.
- archive and retention are separate: archive changes user-facing visibility, while approved retention, legal hold, deletion, or disposition rules continue independently;
- user-facing archive and archived-detail actions must not offer ad hoc hard deletion; lawful scheduled deletion, de-identification, or other disposition may still occur under approved retention, legal-hold, privacy, tax, audit, dispute, security, and compliance rules;
- an archived-document preview or download must recheck the current session, ownership, role/linkage, approved purpose, privacy restrictions, retention restrictions, and legal restrictions;
- ordinary permitted archived-document view/download does not require an additional passcode solely for opening the document;
- search and filters in `ARCHIVED-DOCS-LIST` may use permitted displayed metadata but must not expose restricted OCR text, identity values, account data, or hidden extracted fields;
- legal hold or required retention may preserve evidence but must not expand user visibility;
- archive, restore, and previous-version history must preserve auditability without treating archived evidence as permanently retained beyond the approved schedule.

DOC-12 owns evidence field sets and verification flow. DOC-18 owns final evidence data model.

---

## 9. Payer, Payee, and Admin Visibility Boundaries

Visibility must reflect role, task, permission, and approved purpose.

| Actor | Visibility Rule |
| --- | --- |
| Payer | May view own account, payment request, payment summary, evidence summary, selected payment method summary, the destination selected for the relevant payment context, own masked card and payment profile summaries, status, receipts, and support history. A payer must not browse a payee's Receiving Info library. |
| Payee | May manage own Receiving Info profiles and view request/payout context needed to receive or request payment, but not payer card details, payer payment profiles, private funding data, unrelated KYC data, internal risk flags, or private payer profile data. |
| Admin / Operations | May access data required for assigned queue, review, support, payout, refund, dispute, risk, or compliance task. Access must be permissioned and logged. |
| Risk / Compliance | May access broader identity, evidence, relationship, payment, payout, refund, chargeback, promotion, and risk signals where needed for approved review. |
| Engineering | Should not access production personal data unless approved for incident, support, debugging, migration, or security task under controlled process. |
| Vendor / Partner | May receive only approved data needed for contracted service, integration, fulfilment, risk, payment, payout, or legal purpose. |

Detailed RBAC, access approval, admin workflows, and audit events belong in DOC-19, DOC-22, and DOC-18.

### 9.1 Participant Linking and Invitation Privacy

User-to-user linking must be controlled because payer/payee relationships can reveal sensitive financial, tenancy, household, employment, or business information.

Rules:

- PayPlus must not assume automatic user-to-user matching in the user experience;
- payer-created payment may use a valid non-user payee record or payout destination where allowed by DOC-06, DOC-09, DOC-10, DOC-12, and DOC-14;
- shared payer/payee visibility should require user-initiated search/input, invitation, acceptance, or approved operational action;
- phone number, user ID, QR code, app link, WhatsApp deeplink, or other invitation methods must avoid exposing unnecessary profile, KYC, evidence, payment, or relationship data before acceptance;
- counterparty lookup in DOC-06B `REQUESTS-NEW` may use PayPlus user ID or phone-number identifier, but the lookup result must avoid exposing unnecessary account, profile, evidence, payment, KYC/KYB, or relationship information before acceptance;
- WhatsApp deeplink, app-link, QR, or other request-sharing methods should route the receiver to authenticated/onboarded `REQUESTS-DETAIL` and must keep sensitive request and evidence details inside the authenticated app where practical;
- declined, expired, or ignored invitations must not reveal private information beyond the minimum status needed for the sender;
- participant search, invitation, acceptance, decline, and linking events should be logged and classified in DOC-18.

### 9.2 Referral Attribution Privacy

Referral attribution is separate from payer/payee participant linking and must not grant shared visibility, create a Request, or authorize payment.

Rules:

- opening a share sheet, copying a referral link, or displaying a QR must not create a known-recipient record or invitation status;
- referral URLs, QR payloads, and codes should use opaque references and must not expose account, KYC, evidence, bill/rent, payment, card/profile, payee, or internal risk data;
- a referral deeplink/QR may prefill a displayed non-editable code during registration; ordinary registration may provide an optional manually entered code;
- an invalid manual code may be corrected or cleared before registration completes;
- valid attribution should not be editable by the normal user after completed registration; controlled admin correction, if later approved, must require reason capture and audit;
- the referrer may see only the campaign, privacy-safe qualification progress, and a phone number with the middle half of digits masked, using `91****67` as the MVP format for an eight-digit Hong Kong number; the masked phone appears only in the attributed-referee progress area of `REFERRAL-ROOT`, not on referral reward cards or child reward screens;
- referral views and communications must not disclose the referee's bills, rent, evidence, payment amounts, payment cards/profiles, KYC data, payees, or internal risk reasons.

DOC-13 owns referral relationship, qualification, entitlement, and reward rules. DOC-18 owns final referral objects and events. DOC-22 owns future admin access and correction controls.

### 9.3 Reward Credential and Partner-Fulfilment Privacy

Issued reward metadata may be displayed according to DOC-06B, but usable credentials and partner handoffs require tighter controls:

- reward cards and notifications must not expose redeemable QR payloads, full partner/redemption codes, secrets, internal references, partner payloads, referral-party information, or internal risk reasons;
- QR/code payloads should be opaque and contain no unnecessary account, identity, evidence, payment, card/profile, payee, or risk data;
- credentials should remain concealed until deliberate reveal and current revalidation; app-switcher concealment should be used where supported, without promising generic screenshot prevention;
- copying a code is allowed only where the fulfilment method permits it and must not expose unrelated personal or partner data;
- cached reward metadata may be read-only with last-updated information, but credential reveal, checkout use, and partner handoff require authenticated access and current availability checks unless a separately approved fulfilment method permits otherwise;
- external partners receive only the fields required for the approved fulfilment, reconciliation, support, legal, or contractual purpose.

DOC-13 owns authoritative reward use and fulfilment. DOC-18 owns final credential-reference, access-event, reveal-event, partner-handoff, and lineage structures. DOC-19 owns technical protection and DOC-22 owns controlled operational access.

---

## 10. Consent, Notices, and Communication Privacy

PayPlus should separate service communication from optional marketing or promotional communication.

| Communication Type | Requirement |
| --- | --- |
| Service messages | Account, security, payment, evidence, payout, refund, dispute, receipt, and risk messages may be mandatory where needed to operate the service. |
| Optional messages | Promotion, referral, membership, partner offer, and marketing messages should follow consent, preference, and channel rules. |
| Sensitive content | SMS, WhatsApp, push, and ordinary email should avoid unnecessary identity, evidence, card, payout, or risk details. |
| Template governance | Privacy, legal, payment, risk, and commercial-sensitive templates should require approval before production use. |
| Consent records | Consent, preference, opt-in, opt-out, and template version records should be retained. |

Detailed notification IDs, templates, channel routing, preference controls, and delivery logging belong in DOC-08.

### 10.1 Data-Use Tiers

PayPlus should classify material data use by purpose and approval level.

| Tier | Use | Baseline Boundary |
| --- | --- | --- |
| Tier 0 | Service operation, payment processing, risk, reconciliation, audit, support, legal, tax, compliance, and security. | Required service use with appropriate notices, access controls, and audit logs. |
| Tier 1 | Internal product, risk, evidence, payment, support, operations, and commercial analytics. | Purpose-linked internal use with masking, role-based access, retention controls, and lineage. |
| Tier 2 | Internal derived or aggregated reporting and model-improvement preparation. | Use only approved fields and preserve lineage, sensitivity, and prohibited-input controls. |
| Tier 3 | Owned-channel personalization, promotion ranking, dashboard placement targeting, and partner-offer display inside PayPlus. | Follow consent, preference, campaign approval, role visibility, and sensitive-field exclusions. |
| Tier 4 | Partner-funded offers and campaign measurement inside PayPlus. | Use minimum necessary data, campaign approval, consent/preference controls, and aggregated or de-identified reporting where possible. |
| Tier 5 | External partner reporting, clean-room collaboration, or pseudonymized matching. | Future-gated; requires legal, privacy, security, compliance, contract, and output-control review before use. |
| Tier 6 | Offsite advertising activation or user-level external marketing data sharing. | Not approved by this document; requires separate founder approval, legal/privacy review, consent model, contracts, and formal source-document updates. |

Prohibited or highly restricted uses include raw personal data sale, raw evidence export for marketing, risk-flag sale, unrestricted profiling, credit scoring, insurance underwriting, or offsite audience activation unless separately assessed, approved, and documented.

---

## 11. Analytics, Data Product, and Derived Data

PayPlus may use collected and derived data to support:

- product analytics;
- payment funnel analysis;
- category economics;
- OCR/document AI quality improvement;
- risk monitoring and fraud trend detection;
- payer/payee relationship insights;
- support and operational performance;
- promotion, referral, membership, and campaign performance;
- dashboard shortcut usage, user preference patterns, placement exposure, and carousel performance;
- commercial reporting;
- data marts, dashboards, and future model improvement where approved.

Derived or aggregated data should retain lineage to source data class, permitted purpose, and access controls. Sensitive personal data should not be exposed in dashboards unless required for approved review or operations.

Dashboard shortcut ordering is an account-level product-operation preference and does not by itself require marketing consent. Placement targeting and Featured / What's New / Hot Offer exposure remain subject to applicable consent, preference, approved-purpose, and role-appropriate visibility rules. User-selected shortcut settings may override the current eligible admin default as defined in DOC-06B, but remain subject to protected access, launch/module availability, account eligibility, risk restrictions, compliance controls, and disabled-module rules. Preference analytics must not expose sensitive route content or internal restriction reasons.

Model features, segments, scores, and AI-generated outputs should retain lineage to source data, approved purpose, sensitivity level, permitted use, retention expectation, access roles, and monitoring requirements. Sensitive identity, raw evidence, medical details, child/family-sensitive education details, precise tenancy/property details, domestic helper employment details, raw support narratives, sanctions/AML results, internal risk notes, and vulnerability or hardship indicators should not be used for marketing models or partner reporting unless separately assessed and approved by legal, privacy, compliance, risk, and the Project Owner.

Marketing, personalization, and partner-offer models should distinguish:

- service and risk use;
- product analytics use;
- consented personalization use;
- aggregated commercial reporting;
- partner campaign measurement;
- external activation, which remains future-gated and not approved by this document.

Detailed warehouse, analytics, lineage, event taxonomy, feature/model registry, aggregation thresholds, and reporting design belongs in DOC-18.

---

## 12. Retention, Deletion, and Legal Hold

PayPlus should maintain retention rules by data class and purpose.

Baseline:

- payment, account, tax, audit, receipt, statement, proof-of-payment, dispute, chargeback, compliance, and reconciliation records are expected to follow a 7-year retention baseline;
- KYC/KYB, evidence, payout, refund, dispute, chargeback, risk review, support, and promotion records may require aligned or longer retention where legal, partner, audit, risk, dispute, or operational purpose exists;
- optional marketing preference and consent records should be retained while relevant and for an approved post-change period;
- deleted, anonymized, archived, or de-identified records should preserve required audit, tax, legal, dispute, chargeback, security, and compliance evidence where needed.

Legal hold may override normal deletion where litigation, investigation, dispute, chargeback, regulatory review, audit, incident, fraud, or recovery action is active.

Final retention schedule requires legal, privacy, finance, compliance, tax, security, and partner review.

---

## 13. Data Subject Access, Correction, and Support

PayPlus should support user requests to access, correct, or query personal data according to approved legal and operational process.

Requirements:

- verify requester identity before disclosing sensitive data;
- distinguish user-visible history from full internal audit records;
- distinguish direct editing of permitted account fields from a formal correction request; a verified identity record is not directly editable and only an admin-required `Update Required` decision may reopen provider capture, while other governed corrections use `Correct My Data`;
- present privacy-request status as `Submitted`, `In Progress`, `Action Required`, `Completed`, or `Unable to Complete`; underlying case and provider states remain internal;
- provide completed exports through protected, time-limited in-app access and do not send ordinary email attachments containing the export;
- preserve audit history where correction affects payment, evidence, KYC/KYB, risk, payout, refund, dispute, chargeback, or compliance records;
- avoid disclosing another user's or payee's private data through access responses;
- distinguish deletion of eligible data from account closure and explain that mandatory retention, legal hold, disputes, investigations, security, tax, audit, and compliance duties may limit either outcome;
- route complex or sensitive requests to privacy, compliance, legal, support, or risk review.

Detailed support workflow belongs in DOC-21 and DOC-22.

---

## 14. Vendor, Partner, and Cross-Border Data Handling

PayPlus may share or process data with approved vendors and partners where needed for service operation.

Candidate vendors and partners include:

- KYC/KYB provider;
- OCR/document AI provider;
- PSP/acquirer/payment gateway;
- bank or payout provider;
- SMS, email, push, and WhatsApp providers;
- cloud, storage, analytics, logging, monitoring, and support tools;
- promotion, voucher, miles, referral, or commercial partners.

Requirements:

- vendor purpose, data scope, retention, security, location, subprocessor, incident, and deletion terms should be reviewed;
- cross-border processing should be documented where vendor systems or support teams process data outside Hong Kong;
- partner sharing should be limited to approved purpose and documented in user notices or agreements where required;
- partner reporting should prefer aggregated, de-identified, or campaign-level outputs over user-level data;
- clean-room, pseudonymized matching, external activation, or user-level partner marketing use requires separate approval, contractual controls, output controls, and consent/preference review;
- vendor access and transfer records should be available for audit where practical.

Detailed provider integration belongs in DOC-17. Vendor risk and security policy alignment belong in DOC-04 and ISMS policies.

---

## 15. Security and Incident Boundary

DOC-15 defines privacy requirements. DOC-19 owns technical security implementation.

Privacy-sensitive security expectations include:

- encryption in transit and at rest for sensitive data;
- credential, token, passcode, and OTP data protection;
- role-based access control;
- production data access logging;
- restricted evidence and identity document access;
- secrets and token protection;
- masked card and payout display;
- controlled export and download;
- incident and breach investigation records.

Security incidents, data incidents, provider incidents, unauthorized access, mistaken disclosure, and evidence leakage should route to DOC-21 incident workflow and DOC-22 admin operations where applicable.

---

## 16. Security Standards Alignment

PayPlus security and privacy controls should be designed to support ISO/IEC 27001-aligned information security management and PCI DSS requirements where payment data, cardholder data, payment pages, tokenization, PSP integrations, or cardholder data environment scope applies.

Requirements:

- information security governance, risk assessment, asset ownership, access control, supplier control, logging, incident response, change management, secure development, vulnerability management, and business continuity should align with the PayPlus ISMS policy set and ISO/IEC 27001 expectations;
- card data handling, payment profile tokenization, payment-page security, authentication, access control, logging, vulnerability management, and provider responsibilities should align with PCI DSS requirements where in scope;
- PayPlus should prefer PSP/acquirer tokenization and avoid storing raw card number, CVV, magnetic stripe data, or sensitive authentication data;
- PCI scope, SAQ/ROC path, responsibility matrix, and QSA/acquirer expectations must be confirmed before production launch;
- ISO and PCI evidence should be traceable to policies, controls, logs, approvals, tests, incidents, vendor reviews, and change records.

Detailed ISO/ISMS policies belong in DOC-99 policy library. PCI and authentication implementation details belong in DOC-19. Provider responsibility and integration scope belong in DOC-17.

---

## 17. Affected and Related Documents

| Document | Required Cross-Check |
| --- | --- |
| DOC-05 | Product data requirements, evidence requirements, role visibility, and admin requirements. |
| DOC-06 / DOC-06A / DOC-06B / DOC-06C | Parent UX source map, core journeys, navigation placement, Bills UX display boundaries, and privacy-driven screen variations. |
| DOC-07 | User-facing privacy, evidence, authorization, and policy wording. |
| DOC-08 | Consent, preferences, notification channel privacy, and sensitive message restrictions. |
| DOC-09 | Payment profile metadata, tokenization boundary, authorization records, and masked card display. |
| DOC-10 | Payout destination, bank record, reconciliation, and payout history retention. |
| DOC-11 | Refund, dispute, chargeback, evidence package, recovery, and write-off records. |
| DOC-12 | Evidence data layers, extractable versus displayable fields, duplicate warning, and OCR analytics. |
| DOC-13 | Promotion, referral, membership, miles account, partner voucher, and marketing consent data. |
| DOC-14 | Risk data, AML/sanctions, fraud signals, risk holds, and review records. |
| DOC-17 | Provider API, data transfer, webhook, file, and integration records. |
| DOC-18 | Data model, data classification metadata, lineage, audit events, warehouse, ledger, reporting, and data marts. |
| DOC-19 | Authentication, encryption, RBAC, device controls, PCI, ISO-aligned security controls, and security mechanics. |
| DOC-21 | Incident response, support escalation, data incident workflow, and operations runbooks. |
| DOC-22 | Admin permissions, queues, review workflows, overrides, exports, and access logs. |
| DOC-99 | ISMS policies, access control, cryptography, supplier security, incident management, logging, secure development, and related ISO-aligned policies. |

---

## 18. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-15-001 | What final privacy notice, personal information collection statement, and terms wording are required for Hong Kong launch? | Legal / Privacy | High | Open |
| OQ-15-002 | Which KYC/KYB provider data fields, artifacts, ID copies, and verification results will PayPlus store versus reference through provider? | Compliance / Security / Engineering | High | Open |
| OQ-15-003 | What exact retention schedule applies by data class beyond the 7-year baseline? | Legal / Privacy / Finance | High | Open |
| OQ-15-004 | What data may be used for analytics, model improvement, segmentation, and commercial reporting? | Privacy / Data / Product | High | Open |
| OQ-15-005 | What cross-border processing locations and subprocessors apply for KYC, OCR, PSP, cloud, SMS, email, WhatsApp, analytics, and support providers? | Privacy / Security / Vendor Management | High | Open |
| OQ-15-006 | What user consent, preference, and opt-out rules apply to promotion, referral, partner offer, WhatsApp, SMS, and email communication? | Product / Legal / Privacy | Medium | Open |
| OQ-15-007 | Which sensitive evidence fields are displayable, masked, or restricted by role and category? | Product / Privacy / Security | High | Open |
| OQ-15-008 | What data subject access, correction, deletion, and legal-hold workflow applies? | Privacy / Operations / Legal | Medium | Open |
| OQ-15-009 | What inactivity period triggers dormant-login reauthentication, and which factor should be required? | Security / Product / Risk | Medium | Open |
| OQ-15-010 | What exact PCI DSS scope, SAQ/ROC path, QSA/acquirer expectations, and responsibility matrix apply before production launch? | Security / Payments / Compliance | High | Open |
| OQ-15-011 | What ISO/IEC 27001 control evidence should DOC-15 privacy and data handling controls produce for the ISMS? | Security / Compliance / Privacy | Medium | Open |
| OQ-15-012 | What final retention and analytics rules apply to account-level shortcut preferences, and what consent, preference, retention, and analytics rules apply to placement exposure, carousel impressions, and personalized offer targeting? Functional shortcut management does not itself require marketing consent. | Product / Privacy / Growth | Medium | Partially open |
| OQ-15-013 | Which data classes, fields, derived features, segments, scores, and AI outputs may be used for model improvement, personalization, partner reporting, and campaign measurement? | Privacy / Data / Product | High | Open |
| OQ-15-014 | Which data classes, fields, and derived signals are prohibited from marketing models, partner reporting, clean-room collaboration, or offsite activation? | Privacy / Legal / Risk | High | Open |
| OQ-15-015 | What consent, opt-out, notice, partner-contract, and output-control rules are required before clean-room collaboration, pseudonymized matching, or external activation? | Legal / Privacy / Security | High | Open |
| OQ-15-016 | Which Receiving Info fields may be revealed during controlled edit, and what final masking, proof access, step-up, and retention rules apply by receiving method and actor? | Privacy / Security / Payments | High | Open |

---

## 19. Acceptance Criteria

DOC-15 is acceptable when it clearly defines:

- PayPlus's lawful data utility principle;
- data classification for account, authentication, KYC/KYB, evidence, payment, payout, risk, support, promotion, communication, analytics, and derived data;
- registration, login, new-device 2FA, dormant-login reauthentication, biometric unlock, payment passcode, password reset, and material-change handling baseline;
- identity and KYC/KYB data boundaries;
- evidence and obligation data handling;
- payer, payee, admin, system, vendor, and partner visibility rules;
- referral attribution privacy, masking, no-recipient-on-share, and separation from payer/payee participant linking;
- consent, notice, and communication privacy boundaries;
- data-use tiers, partner-sharing boundaries, model-use governance, and sensitive-data red lines;
- dashboard shortcut preference, placement exposure, personalization, and user preference boundaries;
- analytics and data product expectations;
- retention, deletion, and legal-hold expectations;
- vendor, partner, and cross-border data handling requirements;
- ISO/IEC 27001 and PCI DSS alignment boundaries;
- clear ownership boundaries with DOC-07, DOC-08, DOC-12, DOC-14, DOC-17, DOC-18, DOC-19, DOC-21, and DOC-22.

This document should remain a compact privacy, data protection, and retention specification.

It should not become:

- final privacy policy;
- final legal opinion;
- final data schema;
- final authentication/security architecture;
- vendor contract;
- incident response runbook;
- admin dashboard design;
- customer support script.

---

## 20. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.8.19` | `2026-07-29` | Product Documentation Team | Added the disclosure-safe, capability-aware account-recovery privacy boundary and required opaque Outcome, Resolution, and correlation references without changing approved authentication methods. |
| `0.8.18` | `2026-07-28` | Product Documentation Team | Aligned privacy and account-control rules with HK Phone Verification, the five-state Identity Verification projection, no voluntary re-verification after Verified, admin-required update boundaries, and defined Payment Passcode recovery controls. |
| `0.8.17` | `2026-07-28` | Product Documentation Team | Distinguished first-time identity verification from later sensitive identity changes: Account Activation does not require a pre-existing passcode, while correction, update, and re-verification require passcode or approved reauthentication. |
| `0.8.16` | `2026-07-28` | Product Documentation Team | Added non-account registration attempts with unreserved identifiers, Account Activation, one-month Fast Login, biometric/password boundaries, unique phone/identity conflict handling, nickname/display-name separation, and authentication outcome/correlation data requirements. |
| `0.8.15` | `2026-07-27` | Product Documentation Team | Defined one-account/multiple-login-method handling, unique verified primary email, explicit Google/Apple linking, social-account password setup in Account Security, deferred phone/identity/passcode completion, and financial-activation gates. |
| `0.8.14` | `2026-07-27` | Product Documentation Team | Aligned notification data classification with recipient messages, batches, source lineage, category, read/archive presentation, status/action snapshots, route targets, per-channel attempts, and cross-device Inbox preference handling. |
| `0.8.13` | `2026-07-27` | Product Documentation Team | Aligned account-level `MORE-ROOT` shortcut preferences, current-default restore, protected availability precedence, cross-device use, and privacy-safe analytics while separating functional shortcut settings from marketing consent. |
| `0.8.12` | `2026-07-26` | Product Documentation Team | Defined archive as a per-user visibility projection, preserved counterparty/canonical records and snapshots, and distinguished prohibited ad hoc hard deletion from lawful retention disposition. |
| `0.8.11` | `2026-07-26` | Product Documentation Team | Aligned privacy, search, access recheck, retention/disposition, and audit rules with `ARCHIVED-ROOT` and `ARCHIVED-DOCS-LIST`. |
| `0.8.10` | `2026-07-26` | Product Documentation Team | Required passcode or approved reauthentication for prominent sensitive reveal and material identity/contact/Receiving Info changes, while confirming that ordinary permitted evidence, receipt, statement, invoice, and proof viewing/download does not need an extra prompt. |
| `0.8.9` | `2026-07-23` | Product Documentation Team | Added Receiving Info data classification, private-library visibility, masking, controlled-edit confirmation, version/archive retention, and context-snapshot separation from effective payout-destination changes. |
| `0.8.8` | `2026-07-22` | Product Documentation Team | Aligned Account Information, Identity Verification, Login & Security, Payment Passcode Settings, Privacy & Data, contact-change, trusted-device, account-closure, privacy-request, and protected-export privacy requirements with DOC-06B. |
| `0.8.7` | `2026-07-22` | Product Documentation Team | Aligned privacy requirements with DOC-06B `ME-ROOT`, including masked account summary, payment-passcode-gated sensitive reveal, Privacy & Data controls, account-closure retention boundary, Receiving Details masking, Archived Documents access, and Me preference data. |
| `0.8.6` | `2026-07-21` | Product Documentation Team | Added explicit classification of confirmed reward dimensions and issued-reward credential/partner-fulfilment privacy controls for safe display, opaque payloads, deliberate reveal, cached read-only metadata, partner minimization, and controlled access events. |
| `0.8.5` | `2026-07-21` | Product Documentation Team | Restricted masked referee-phone display to attributed-referee progress in `REFERRAL-ROOT` and excluded referral reward cards, entitlement detail, claim, and issued-reward screens. |
| `0.8.4` | `2026-07-21` | Product Documentation Team | Added referral attribution data classification and privacy rules for opaque reusable codes, no-recipient sharing, immutable normal-user attribution, masked referee phone display, restricted referral visibility, and separation from payer/payee linking. |
| `0.1.0` | `2026-06-02` | Product Documentation Team | Initial founder working baseline for privacy, lawful data utility, data classification, registration/authentication data handling, visibility, masking, retention, vendor handling, ISO/PCI alignment, and cross-document ownership. |
| `0.2.0` | `2026-06-02` | Product Documentation Team | Aligned data classification with DOC-09 user payment instruction by adding payment instruction, funding leg, deferred funding date, selected transfer date, partial funding, and payment-instruction reminder data. |
| `0.3.0` | `2026-06-02` | Product Documentation Team | Added deferred instruction quote revalidation result and DOC-13 promotion quote reservation data to the classification baseline. |
| `0.4.0` | `2026-06-02` | Product Documentation Team | Standardized coupon/voucher library and reward instrument wording to avoid stored-value confusion. |
| `0.5.0` | `2026-06-04` | Product Documentation Team | Aligned privacy/data classification with DOC-06 dashboard baseline by adding shortcut preferences, dashboard placement exposure, carousel interaction, personalization, and targeting boundaries. |
| `0.6.0` | `2026-06-08` | Product Documentation Team | Added data-use tiers, model-use governance, partner-sharing boundaries, sensitive-data red lines, clean-room/external activation gates, and related open questions for AI/data-engine readiness. |
| `0.7.0` | `2026-06-12` | Product Documentation Team | Aligned privacy boundaries with DOC-06 Bills tab baseline by adding participant linking and invitation data, no automatic user-to-user matching, and minimum-disclosure invitation rules. |
| `0.8.0` | `2026-06-17` | Product Documentation Team | Aligned data classification with DOC-06 Bills reminder routes by adding linked reminder records, reminder timing, custom override, soft-delete state, and reminder interaction behavior. |
| `0.8.1` | `2026-07-02` | Product Documentation Team | Aligned participant-linking privacy with DOC-06B `REQUESTS-NEW`, counterparty lookup, and request-sharing deeplink boundaries. |
| `0.8.2` | `2026-07-03` | Product Documentation Team | Aligned notification data classification with DOC-06B Instructions route by distinguishing payment instruction action-alert status from ordinary bill/rent reminder records. |
| `0.8.3` | `2026-07-06` | Product Documentation Team | Aligned payment and funding data classification with DOC-06B Payment Profile route by adding tokenized card metadata, saved split-card profile metadata, payer-only visibility, action-required profile handling, and default confirmation behavior. |
