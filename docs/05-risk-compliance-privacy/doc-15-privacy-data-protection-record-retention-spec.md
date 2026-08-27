---
document_id: DOC-15
title: Privacy, Data Protection & Record Retention Specification
version: 1.0.2
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
last_updated: 2026-08-27
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
  - DOC-09 Payment Domain Architecture
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
| **Version** | `1.0.2` |
| **Status** | Founder Working Baseline |
| **Owner** | Privacy / Compliance |
| **Reviewers** | Product Lead<br>Privacy Lead<br>Compliance Lead<br>Risk Lead<br>Security Lead<br>Engineering Lead<br>Data Lead<br>Operations Lead<br>Legal Lead |
| **Approvers** | Project Owner<br>Privacy Lead<br>Compliance Lead<br>Security Lead |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Product Overview & Positioning<br>DOC-03 Regulatory, PSP & Acquirer Assessment<br>DOC-04 Compliance Certification Roadmap & Control Framework<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06 User Journey, UX Flow & Service Blueprint<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Rules<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Risk Controls<br>DOC-17 API & Third-party Integration<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization & Authentication<br>DOC-21 Monitoring, Incident Response & Operations Runbook<br>DOC-22 Admin Management Dashboard Operations Workflow<br>DOC-99 ISMS Policy Library |

---

## 1. Purpose

This document defines PayPlus privacy, data protection, data classification, visibility, masking, lawful-use, consent, vendor, and record-retention requirements.

PayPlus is a data-driven payment platform. It may collect, derive, retain, and use data from account activity, Evidence verification, payment behavior, payout handling, risk review, support activity, and promotion activity to operate the service, verify applicable Bill/Rent Payment Obligations, reduce fraud, improve user experience, support analytics, manage commercial performance, and meet legal, audit, tax, compliance, partner, and operational requirements.

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
- retention, record-handling, legal-hold and audit-record expectations;
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
| Business recording, explainability, history, lineage, audit meaning, and reporting obligations | DOC-18; final data model, event schema, ledger representation, reporting implementation, and warehouse design remain separately authorized future work |
| Mechanism-neutral authentication, protected-value, access-enforcement, device/session, secure-boundary, and PCI-related security controls | DOC-19; final PCI applicability/scope requires professional confirmation |
| Incident response, monitoring, and operational escalation | DOC-21 |
| Admin dashboard workflows, permissions, uploads, overrides, and review queues | DOC-22 executes only expressly owner-permitted operations using approved policy and facts; underlying privacy/access/retention/security/product authority remains with the applicable owner. |

---

## 3. Current Decision Baseline

Privacy requirements apply to the Payer, authoritative Bill/Rent source, source-context economic-Payee facts, applicable Evidence, payment/Payout/adjustment records and owner-permitted operational access. An economic Payee need not be a User. The product has no active Request, Linking, To Receive, Receiving Info, Payee-user, participant-linking, reciprocal-reader, adapter, fallback, deep-link or production legacy runtime/data model.

DOC-15 owns privacy classification, masking, approved-purpose access, visibility and the lawful-scope assessment for the Founder-approved indefinite-retention direction, including required exceptions, restricted data classes and prohibited sensitive-data boundaries. The reviewed DOC-18 Draft owns business-recording, history, lineage, audit-meaning and reporting-explainability obligations; it does not approve schemas, machine states/events or implementation. Source Archive is a non-erasing visibility projection. This document does not define Archive/Restore, prior-version, Evidence-version, replacement-source or reader presentation.

| Area | Baseline |
| --- | --- |
| Launch market | Hong Kong. |
| Data strategy | PayPlus should support broad, lawful, purpose-linked data collection and analytics while preserving trust, consent, data minimization, access controls, and product-boundary restrictions. |
| Account creation and activation | A temporary registration attempt creates no account and reserves no identifier. Restricted account creation requires one unique verified primary email, accepted Terms and Privacy notices, and at least one usable login method. Verified phone, identity verification, and six-digit payment-passcode setup may be completed later but are mandatory through `ACCOUNT-ACTIVATION` before full registration and financially restricted actions. |
| Identity verification | Individual identity verification may use a provider selected and approved by the applicable formal owners. PayPlus may receive or store required identity attributes, provider references, verification outcomes, and approved evidence artifacts. |
| KYC attributes | Name, ID number, sex, ID document data, and other provider-returned attributes may be used where connected to KYC, risk, compliance, payee verification, audit, support, or legal purpose. |
| Login methods | One PayPlus account may use email/password and explicitly linked Google and Apple provider identities. Provider identities are linked by stable provider identifier, never by email match alone. |
| Primary email | One verified primary email may belong to only one PayPlus account. A provider-returned verified email may be selected; another entered email must be verified before use. |
| Password | A password is required only when email/password login is enabled. A social-authenticated account may set its first PayPlus password later through `ACCOUNT-SECURITY`. |
| Biometric unlock | User-enabled Fingerprint and Face ID may support device-local Fast Login. PayPlus should not store biometric templates or plaintext passwords. |
| New-device 2FA | Required on new device. Channel precedence and fallback remain subject to DOC-19 security and applicable owner confirmation. |
| Fast Login | Eligibility uses a rolling one-month period renewed by each successful login and may be revoked earlier by risk, device, credential, account, or security changes. A separate dormant-account threshold remains open. |
| Payment confirmation | Payment passcode is required for proceeding with payment. Higher-risk activity may require additional step-up under DOC-14 and DOC-19. |
| Password reset | Email deeplink is supported, with single-use, short-lived, auditable reset flow. |
| Record retention | Indefinite retention remains the accepted product/governance direction, subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries confirmed by DOC-15 and Legal/Privacy. Owners may define access, masking, legal-hold, correction and lawful handling controls; no finite replacement duration is selected here. |

Unconfirmed provider, cross-border, sanctions, biometric, security and implementation-control details should remain editable assumptions until confirmed; no owner may create a finite retention period or time-triggered destruction rule.

---

## 4. Data Principles

| Principle | Requirement |
| --- | --- |
| Lawful data utility | PayPlus may collect and use data where there is a defined product, payment, compliance, risk, operational, analytical, commercial, support, audit, tax, legal, or partner purpose. |
| Purpose-linked use | Each data class should have documented purposes and permitted use cases. |
| Data engine readiness | Data structures should support analytics, segmentation, risk intelligence, evidence quality, commercial reporting, and future model improvement where allowed. |
| Model-use governance | AI/model improvement, segmentation, personalization, partner reporting, and decision-support use should be governed by approved purpose, field classification, consent/preference state, prohibited-input rules, lineage, monitoring, and human-review requirements where applicable. |
| Transparency | Users should receive appropriate notices for account, identity, evidence, payment, communication, and marketing data handling. |
| Role-based visibility | Payers, authorised owner roles, systems, vendors and partners should see only data needed for their approved purpose or task; an economic Payee is not a PayPlus User role. |
| Mask by default for sensitive fields | Sensitive identity, evidence, payment, payout, and risk fields should be masked or restricted unless full access is needed for an approved purpose. |
| Auditability | Access, use, correction, export, privacy-request, override, review, and disclosure actions should be logged where material. |
| Retention discipline | Indefinite retention remains the accepted product/governance direction for applicable records, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. Archive changes visibility only and is not deletion, purge, erasure or de-identification. |

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
| Payment and Funding Data | Bill/Rent Payable Basis reference, Projection inputs/outputs where retained, Payment Obligation, Due Amount, Effective Coverage, Outstanding Amount, Checkout Workspace, Checkout Target, Obligation Allocation, payable-capacity reservation, Funding Allocation Version, Funding Leg, Payment Attempt, Provider Submission, Provider Confirmation reference, Payment, Payment Application, Effective Payout Destination Snapshot, deliberate Payment Instruction, deferred funding date, authorization record, payment token reference, masked card summary, permitted masked cardholder name, card nickname, card brand, expiry, issuer/BIN metadata where available, default-card marker, saved split-card profile name, profile ratios, starred/frequent marker, profile action-required state, step-up result, provider reference. | Payment processing, risk, reconciliation, chargeback defense, product analytics. |
| Payout and economic-Payee Data | Source-context economic-Payee and owner-approved destination facts, authorization-time destination snapshot, Payout status, batch, bank reference and reconciliation result. | Payout execution, intended-Payee/destination verification, reconciliation, fraud prevention and support. |
| Retired Participant-Linking Data | No active collection, runtime or reader; append-only documentation history only. | Documentation provenance only. |
| Risk and Compliance Data | Risk score/band, rule triggers, AML/sanctions status, duplicate evidence signals, same-party indicators, fraud flags, payout holds, admin review outcome, escalation records. | Anti-cashout, fraud prevention, compliance control, monitoring, audit. |
| Refund, Dispute, Chargeback, and Support Data | Support tickets, user messages, dispute reason, refund case, chargeback reason code, evidence package, resolution, recovery/write-off status. | Support, dispute resolution, chargeback defense, operational learning, reporting. |
| Promotion, Referral, and Membership Data | Campaign eligibility, promotion quote reservation, coupon/voucher library, reward instrument type, earning source, program context, campaign/offer/entitlement source, fulfilment method, reward entitlement, opaque user-linked referral code/reference, registration attribution, masked referee phone, qualification progress/outcome, beneficiary role, entitlement-to-instrument link, membership tier, miles account reference, redemption status. | Growth, campaign operation, partner reporting, reward fulfilment, attribution, abuse detection. |
| Communication and Notification Data | Notification event ID, recipient-specific message ID, optional batch ID, category, source event/object, recipient role, template version, target route/object, read/archive state, status/action-at-send snapshot, channel preference, per-channel delivery attempt, provider reference, timestamps, reminder linkage, and WhatsApp/SMS/email/push logs. | Service communication, consent/preference operation, audit, support, communication performance. |
| UI Preference and Personalization Data | Approved shortcut-catalog/default version, account-level shortcut order and visibility, effective availability, restore-current-default action, dashboard placement exposure, carousel impression/action, Inbox read/archive interaction, Me destination use, notification preference, language, theme, and other user-selected display preferences. | Product operation, cross-device user preference, consented marketing/promotion display, analytics, and audit where required. |
| Behavioral and Product Analytics Data | Feature usage, funnel steps, payment patterns, Category usage, correction behaviour, conversion, drop-off, retry behaviour, spend behaviour, dashboard shortcut usage and placement performance. | Product improvement, risk intelligence, commercial analytics and segmentation. |
| Derived and Aggregated Data | Risk indicators, user segments, category economics, OCR quality metrics, fraud trends, campaign performance, anonymized or aggregated insights, model features where approved. | Analytics, approved model improvement, business intelligence, strategic decisions. |

DOC-18 defines the business facts, provenance, history, lineage and explainability that later work must preserve. Detailed fields, schemas, event names, feature/model metadata and reporting tables remain separately authorized future Engineering/Data work.

---

## 6. Registration, Login, and Authentication Data

PayPlus should support the following account and authentication model:

| Function | Requirement |
| --- | --- |
| Registration attempt | Before account creation, use a temporary attempt record rather than a partial account. Proposed email, phone, provider identity, and other identifiers remain unreserved; app exit permits an immediate new attempt. An attempt may remain usable for up to 30 minutes of inactivity for security and continuation handling; after that window it is expired/inactive for continuation and a new attempt may be required. The attempt record follows the accepted indefinite-retention direction subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries; it is not deleted, purged, erased, anonymised or disposed by this document. Final creation atomically rechecks uniqueness and required gates. |
| Restricted account creation | Require one unique verified primary email, accepted Terms and Privacy notices, and one usable login method. Google/Apple registration stores the verified provider identity by stable provider identifier; email registration requires verified email and password. |
| Account activation | `ACCOUNT-ACTIVATION` completes phone verification, identity verification, and six-digit payment-passcode setup after restricted account creation. Completion removes the registration-level restriction but does not bypass feature-specific evidence, risk, payment, provider, or role gates. |
| Login methods | One account may use email/password, Google, and Apple only where each method has been explicitly enabled or linked. Matching email addresses never create or merge a provider link automatically. |
| Primary email uniqueness | A verified primary email may belong to only one PayPlus account. An attempted social registration using an existing verified primary email must stop account creation and direct the authenticated user to log in to the existing account before linking the provider. |
| Phone and identity uniqueness | One verified phone and one verified individual identity may each belong to only one active individual account. A conflict found during Account Activation blocks activation and routes to Login, Recovery, or controlled Support handling without automatic merge. |
| Password | Email/password registration sets a password. A social-authenticated account may have no PayPlus password until the user selects `Set Password` in `ACCOUNT-SECURITY`; thereafter the action becomes `Change Password`. Password storage and hashing belong in DOC-19. |
| Provider linking | Linking or unlinking Google/Apple requires an authenticated session, fresh approved reauthentication, successful provider authentication, explicit confirmation, audit, and security notification. A provider identity may link to only one PayPlus account, and the final usable login method cannot be removed. |
| Fast Login and device-local biometric | Each successful login renews a one-month Fast Login period. User-enabled Fingerprint or Face ID may activate the approved device credential; biometric templates remain on device or approved platform service. PayPlus stores no plaintext password and masks the remembered email. |
| New-device 2FA | New-device login requires step-up. Channel precedence and fallback remain subject to DOC-19 security and applicable owner confirmation. |
| Dormant-login reauthentication | Login after a configured long inactivity period should require reauthentication, such as password plus SMS OTP, email OTP, or other approved factor. |
| Payment passcode | Payment passcode is required before proceeding with payment authorization. |
| Password reset | Email deeplink must be single-use, short-lived, and logged. User should receive security notification after reset. |
| Core account changes | Changes to an existing email, phone, password, payment passcode, immutable identifier or KYC/KYB record require payment passcode or approved reauthentication before route-specific owner controls. First-time identity verification during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode. Payment-profile changes retain their separately approved optional-passcode rule. |

DOC-15 defines data handling and privacy boundaries. DOC-19 owns mechanism-neutral security invariants, enforcement requirements, prohibited exposure, and verification handoffs for authentication, protected values, device/session assurance, and access enforcement. Exact mechanisms remain open technical decisions and provider contracts remain with DOC-17.

Account recovery must be capability-aware and disclosure-safe. PayPlus may evaluate whether approved email, linked-provider, authenticated-account, or controlled Support recovery remains available, but public responses must not reveal the existence of an account, password, provider link, phone, identity record, trusted device, or internal risk restriction. A remembered device, verified phone, verified identity, or provider email is not by itself a recovery method unless the applicable route/account owner permits that capability and DOC-19 security enforcement is satisfied. Recovery records and analytics must use opaque attempt, outcome, resolution, and correlation references rather than credentials, recovery secrets, or unrestricted identity/provider payloads.

### 6.1 Material Change Handling

Material changes should be grouped by sensitivity and handled with proportionate confirmation.

| Change Type | Examples | Recommended Treatment |
| --- | --- | --- |
| Contact rebinding | Change phone or email. Nickname/display name is not a login identifier. | Require payment passcode or approved reauthentication first. For phone change, send OTP to the registered email and then verify the new phone by SMS OTP. For email change, send SMS OTP to the registered phone and then verify the new email by OTP or deeplink. Notify old and new channels where available. Route users without a trusted old channel to support-assisted identity recovery. |
| Credential or login-method change | Set or change password, link or unlink Google/Apple, change payment passcode, recovery method, or 2FA setting. | Require fresh approved reauthentication and route-specific confirmation; require successful authentication by a provider being linked; prevent removal of the final usable login method; notify user after completion. |
| Device trust change | New device, trusted-device addition/removal, device reset. | Require step-up where applicable and log the device/session event. Removing another trusted device revokes its trust and active session; removing the current device logs the user out. |
| Payment profile change | Add, remove/archive, update, suspend, reactivate, star/unstar, or change default card/payment profile. | Require payer confirmation by default; payment passcode confirmation may be enabled by user setting; step-up may still apply where risk, PSP/acquirer, or security rules require; never expose raw card data. |
| Retired Receiving Info | No active Consumer Receiving Info profile, library, version, reveal or archive interaction exists. | Documentation provenance only. |
| Effective payout destination change | Owner-governed source-context destination facts and an applicable authorization-time snapshot. | DOC-09/DOC-10 control those facts; DOC-15 supplies approved-purpose privacy requirements only. |
| Identity/KYC change | Correct a governed record or respond to an owner-required identity update. A user cannot voluntarily repeat verification after `Verified`. | The applicable identity/security owner determines any outcome; DOC-22 may execute only an expressly permitted workflow. First-time verification follows the Account Activation exception. |
| Marketing or communication preference change | Opt-in/out, WhatsApp/SMS/email preference, direct-marketing consent. | Require logged preference update; step-up only if account takeover risk is present. |

Material changes require business audit meaning and user-facing security notifications where appropriate. DOC-18 owns the historical action-basis and explainability obligation; detailed machine status/event representation remains separately gated; applicable security enforcement belongs in DOC-19, notification policy in DOC-08, and specifically owner-permitted Admin execution in DOC-22.

The user-facing Two-Step Verification toggle controls optional routine step-up only. It must not disable mandatory new-device, risk-triggered, contact-change, account-closure, or provider-required authentication. Payment Passcode settings may include a user-controlled preference requiring passcode confirmation for card or payment-profile changes; the default remains ordinary confirmation unless another mandatory rule applies.

### 6.2 `ME-ROOT` Account Display and Reveal

DOC-06B `ME-ROOT` is the Payer-only account-control route. DOC-15 supplies privacy requirements only; route, return and user-facing status behaviour remain with their formal owners.

- account surfaces must mask sensitive identity, contact and credential information unless approved-purpose access permits it;
- authentication, security, route, return and displayed-status requirements remain with DOC-06B, DOC-07 and DOC-19;
- full identity attributes, identity documents, provider payloads, payment credentials, evidence content, full payout details, and internal risk reasons must not appear on the root;
- revealing approved masked sensitive account values uses the existing PayPlus payment passcode or approved reauthentication; no second reveal-only passcode should be introduced;
- changing existing sensitive identity, contact, security or credential data requires payment passcode or approved reauthentication before applicable owner controls; first-time identity verification during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode;
- permitted evidence, invoice, receipt, statement, and payment-proof viewing/downloading within an authenticated approved-purpose context does not require an extra passcode or step-up solely because the document is opened or downloaded;
- additional step-up may apply where risk, security, legal, provider, or data-classification rules require it;
- reveal attempts and outcomes should be logged without copying sensitive values into analytics or ordinary notification content;
- `PRIVACY-DATA-CONTROLS` should separate optional direct-marketing, personalization, and approved partner-data-use choices from mandatory service, payment, security, risk, compliance, tax, audit, dispute, and retention processing;
- `PRIVACY-DATA-CONTROLS` should support approved access/export, correction, privacy-request handling, request history, and a contextual handoff to account closure; direct account-field edits return through `ACCOUNT-PROFILE` and notification-channel choices remain in `NOTIFICATION-SETTINGS`; none of these requests erases the underlying record;
- protected data export must use time-limited in-app access rather than an ordinary email attachment;
- account closure in `ACCOUNT-PROFILE` is a controlled request, not record destruction. It requires payment passcode plus 2FA, checks unresolved payment and operational blockers, remains cancellable until operational finalization, and preserves underlying records under the accepted indefinite-retention direction subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries;
- completed closure blocks new activity, terminates sessions, disables login, and sends an approved completion notice; the user should be prompted to obtain available records before closure, with later access handled through support or the approved privacy process;
- Consumer Receiving Info has no active product surface. Payer-entered destination facts remain within the controlled Bill/Rent journey under the applicable owner boundaries;
- a Payer may see only owner-approved source-context destination facts for the relevant payment context, subject to DOC-15 approved-purpose access requirements;
- Archive is a Payer visibility projection that must not erase or rewrite authoritative source, Evidence, Payment, destination, Payout, reconciliation or audit history. `ARCHIVED-ROOT`/`ARCHIVED-BILLS-LIST` presentation belongs to DOC-06B/DOC-06C. `ARCHIVED-DOCS-LIST` is provisional and unreachable through active UI; it has no DOC-15-defined content or interaction. If a later owner authorizes presentation, DOC-15 supplies approved-purpose access and retention requirements only.

DOC-19 defines the mechanism-neutral passcode, session, device, reauthentication, and reveal security-control contract; exact mechanisms remain open with Security/Engineering and provider detail with DOC-17. DOC-18 owns the business-recording and explainability handoff; final event and data structures remain separately gated.

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

Final provider API behavior belongs in DOC-17 under an accepted provider-specific contract. DOC-18 supplies the business-recording and explainability contract; a technical data schema remains separately gated. Security controls belong in DOC-19.

---

## 8. Evidence and Obligation Data Handling

Evidence data is a major PayPlus data asset.

PayPlus may collect and process bills, invoices, tenancy agreements, contracts, statements, rent demands, service records, OCR text, extracted fields, user-corrected fields, verification signals, duplicate signals, review decisions, and final evidence snapshots.

Rules:

- raw evidence, OCR text, extracted fields, user corrections, verification signals, and final evidence snapshot should remain separately traceable;
- extractable data does not mean displayable data;
- sensitive evidence fields may be stored for approved purposes while hidden or masked in ordinary UI;
- the Payer and authorised owner roles should see only approved-purpose Evidence data;
- duplicate/reused evidence warnings must not disclose another user's private information;
- evidence data may support analytics, OCR quality improvement, risk intelligence, commercial reporting, and product improvement where permitted;
- evidence access, review, correction, download, export, replacement and privacy-request actions should be logged where material.
- archive and retention are separate: archive changes user-facing visibility, while the accepted indefinite-retention direction continues subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries;
- user-facing archive and archived-detail actions must not offer hard deletion, purge, erasure, de-identification or other destruction; owner-governed access, masking, correction and legal-hold controls do not change the underlying retained record;
- legal hold or required retention may preserve evidence but must not expand user visibility;
- Archive visibility must not erase or rewrite Evidence, Payment, destination, Payout, reconciliation or audit history; exact Archive, Restore, prior-version, Evidence-version and `ARCHIVED-DOCS-LIST` presentation remains deferred.

DOC-12 owns Evidence fact meaning, permitted input sets and verification flow. DOC-18 owns the business-recording and explainability handoff; a final technical Evidence data model remains separately gated.

---

## 9. Payer, Payee, and Admin Visibility Boundaries

Visibility must reflect role, task, permission, and approved purpose.

| Actor | Visibility Rule |
| --- | --- |
| Payer | May view own account, applicable payment summary, owner-approved Evidence summary, selected payment-method summary, source-context destination facts, own masked card/payment-profile summaries, receipts and support history subject to approved-purpose rules. |
| Economic Payee | Is not a PayPlus User role or active reciprocal reader. Source-context intended-Payee and destination privacy remain with the applicable formal owners. |
| Admin / Operations | May access data required for assigned queue, review, support, payout, refund, dispute, risk, or compliance task. Access must be permissioned and logged. |
| Risk / Compliance | May access broader identity, evidence, relationship, payment, payout, refund, chargeback, promotion, and risk signals where needed for approved review. |
| Engineering | Should not access production personal data unless approved for incident, support, debugging, migration, or security task under controlled process. |
| Vendor / Partner | May receive only approved data needed for contracted service, integration, fulfilment, risk, payment, payout, or legal purpose. |

Affected domain owners define the purpose, relevant current and historical facts, and whether presentation or retrieval is permitted. DOC-15 owns approved-purpose access, masking, visibility and retention. DOC-19 enforces access only after an owner and DOC-15 permit it and creates no access or retrieval authority. DOC-22 may execute only the specifically owner-permitted presentation or retrieval operation and creates no generic Admin access or mechanics. DOC-21 may consume already permitted operational evidence but has no access, presentation or retrieval authority. DOC-18 requires the business history, action basis, lineage and audit meaning to remain explainable; exact audit-event representation remains separately gated.

### 9.1 Retired Participant-Linking Privacy

Participant Linking, invitations, Request delivery and reciprocal visibility are retired from active MVP. No production data, reader, adapter, fallback or deep-link obligation exists. Their prior names may appear only in append-only documentation history. This section imposes no current collection, sharing, visibility, retention or runtime requirement for them.

No user-to-user linking privacy model is active. Retired identifiers create no collection, sharing, visibility, retention, event or runtime requirement.

### 9.2 Referral Attribution Privacy

Referral attribution is separate from source-context economic-Payee facts and must not grant shared visibility, create a Request or authorize payment.

Rules:

- opening a share sheet, copying a referral link, or displaying a QR must not create a known-recipient record or invitation status;
- referral URLs, QR payloads, and codes should use opaque references and must not expose account, KYC, evidence, bill/rent, payment, card/profile, payee, or internal risk data;
- a referral deeplink/QR may prefill a displayed non-editable code during registration; ordinary registration may provide an optional manually entered code;
- an invalid manual code may be corrected or cleared before registration completes;
- valid attribution should not be editable by the normal user after completed registration; controlled admin correction, if later approved, must require reason capture and audit;
- the referrer may see only the campaign, privacy-safe qualification progress, and a phone number with the middle half of digits masked, using `91****67` as the MVP format for an eight-digit Hong Kong number; the masked phone appears only in the attributed-referee progress area of `REFERRAL-ROOT`, not on referral reward cards or child reward screens;
- referral views and communications must not disclose the referee's bills, rent, evidence, payment amounts, payment cards/profiles, KYC data, payees, or internal risk reasons.

DOC-13 owns referral relationship, qualification, entitlement, and reward rules. DOC-18 owns the business-recording and explainability handoff; final referral objects and events remain separately authorized technical work. DOC-22 may execute only expressly owner-permitted access and correction workflows using approved policy and facts.

### 9.3 Reward Credential and Partner-Fulfilment Privacy

Issued reward metadata may be displayed according to DOC-06B, but usable credentials and partner handoffs require tighter controls:

- reward cards and notifications must not expose redeemable QR payloads, full partner/redemption codes, secrets, internal references, partner payloads, referral-party information, or internal risk reasons;
- QR/code payloads should be opaque and contain no unnecessary account, identity, evidence, payment, card/profile, payee, or risk data;
- credentials should remain concealed until deliberate reveal and current revalidation; app-switcher concealment should be used where supported, without promising generic screenshot prevention;
- copying a code is allowed only where the fulfilment method permits it and must not expose unrelated personal or partner data;
- cached reward metadata may be read-only with last-updated information, but credential reveal, checkout use, and partner handoff require authenticated access and current availability checks unless a separately approved fulfilment method permits otherwise;
- external partners receive only the fields required for the approved fulfilment, reconciliation, support, legal, or contractual purpose.

DOC-13 owns authoritative reward use and fulfilment. DOC-18 owns the business-recording, history, lineage and explainability obligations for credential reference, permitted access/reveal occurrence, and partner handoff. Final technical structures and events remain separately gated. DOC-19 owns technical protection and DOC-22 may execute only expressly owner-permitted controlled operational access workflows.

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
- source-context and risk-derived indicators only where separately owner-approved;
- support and operational performance;
- promotion, referral, membership, and campaign performance;
- dashboard shortcut usage, user preference patterns, placement exposure, and carousel performance;
- commercial reporting;
- data marts, dashboards, and future model improvement where approved.

Derived or aggregated data should retain lineage to source data class, permitted purpose, and access controls. Sensitive personal data should not be exposed in dashboards unless required for approved review or operations.

Dashboard shortcut ordering is an account-level product-operation preference and does not by itself require marketing consent. Placement targeting and Home Hot Offer exposure remain subject to applicable consent, preference, approved-purpose, and role-appropriate visibility rules. User-selected shortcut settings may override the current eligible admin default as defined in DOC-06B, but remain subject to protected access, launch/module availability, account eligibility, risk restrictions, compliance controls, and disabled-module rules. Preference analytics must not expose sensitive route content or internal restriction reasons.

Model features, segments, scores, and AI-generated outputs should retain lineage to source data, approved purpose, sensitivity level, permitted use, lawful-scope-qualified indefinite-retention treatment, access roles, and monitoring requirements. Sensitive identity, raw evidence, medical details, child/family-sensitive education details, precise tenancy/property details, hypothetical future Founder-approved employment-category details, raw support narratives, sanctions/AML results, internal risk notes, and vulnerability or hardship indicators should not be used for marketing models or partner reporting unless separately assessed and approved by legal, privacy, compliance, risk, and the Project Owner.

Marketing, personalization, and partner-offer models should distinguish:

- service and risk use;
- product analytics use;
- consented personalization use;
- aggregated commercial reporting;
- partner campaign measurement;
- external activation, which remains future-gated and not approved by this document.

DOC-18 owns business lineage, audit meaning, reporting obligations and explainability. Detailed warehouse, analytics implementation, machine event taxonomy, feature/model registry, aggregation thresholds and reporting design remain separately authorized future work.

---

## 12. Retention, Record Handling, and Legal Hold

Indefinite retention remains the accepted product/governance direction, subject to DOC-15 and Legal/Privacy confirmation of lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries. DOC-15 owns the privacy, access, masking, legal-hold and record-handling requirements that apply to each data class and purpose; no finite replacement duration is selected here.

Baseline:

- payment, account, tax, audit, receipt, statement, proof-of-payment, dispute, chargeback, compliance, reconciliation, KYC/KYB, Evidence, payout, refund, risk review, support and promotion records follow the Founder-approved indefinite-retention direction, subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries;
- optional marketing preference and consent records follow the accepted indefinite-retention direction subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries, with access and use governed by approved purpose and preference controls;
- Archive, account closure, Save outcomes, Payment/Instruction/Checkout terminal treatment, case closure and notification delivery do not erase the underlying record.

Legal hold, investigation, dispute, chargeback, regulatory review, audit, incident, fraud or recovery handling may impose additional access, preservation or review controls. A professional conclusion that makes the direction impermissible for a material class must be handled under the canonical workflow rather than silently selecting a different treatment.

Indefinite retention remains the accepted product/governance direction. Legal, privacy, finance, compliance, tax, security and partner owners confirm lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries; a material-class conflict is handled under the canonical workflow rather than silently replaced, and no finite duration is selected here.

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
- distinguish privacy/access/correction requests from account closure and explain that neither changes the accepted indefinite-retention direction, subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries, or erases the underlying record;
- route complex or sensitive requests to privacy, compliance, legal, support, or risk review.

DOC-21 may consume permitted operational evidence for support and incident handling but creates no access, presentation or retrieval authority. DOC-22 may execute only a specifically owner-permitted workflow. Detailed mechanics remain open and do not grant either document generic access.

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

- vendor purpose, data scope, retention, security, location, subprocessor, incident, access and termination terms should be reviewed; no vendor operation may destroy a PayPlus record;
- cross-border processing should be documented where vendor systems or support teams process data outside Hong Kong;
- partner sharing should be limited to approved purpose and documented in user notices or agreements where required;
- partner reporting should prefer aggregated, de-identified, or campaign-level outputs over user-level data;
- clean-room, pseudonymized matching, external activation, or user-level partner marketing use requires separate approval, contractual controls, output controls, and consent/preference review;
- vendor access and transfer records should be available for audit where practical.

Detailed provider integration belongs in DOC-17. Vendor risk and security policy alignment belong in DOC-04 and ISMS policies.

---

## 15. Security and Incident Boundary

DOC-15 defines privacy requirements. DOC-19 owns the mechanism-neutral technical security-control contract; implementation mechanisms and operating evidence remain separately unresolved.

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

Detailed ISO/ISMS policies belong in the DOC-99 policy library. DOC-19 defines PCI-related and authentication security-control requirements without determining final PCI scope or implementation mechanisms. Provider responsibility and integration scope belong in DOC-17; PCI applicability and assessment require professional confirmation.

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
| DOC-18 | Reviewed business recording, explainability, material-fact history, historical action basis, lineage, audit meaning, reporting obligations, and owner handoffs; exact technical data model, metadata fields, events, warehouse, ledger representation, reporting implementation, and marts remain separately gated. |
| DOC-19 | Mechanism-neutral authentication, protected-value, access-enforcement, device/session, secure-boundary, and verification-handoff controls; no final PCI scope, provider mechanism, implementation, or certification claim. |
| DOC-21 | Incident response, support escalation, data incident workflow, and operations runbooks. |
| DOC-22 | Execution and operation of expressly owner-permitted permissions, queues, review workflows, overrides, exports, and access logging using approved policy and facts; DOC-22 does not define the underlying privacy, access, retention, security, or product decision. |
| DOC-99 | ISMS policies, access control, cryptography, supplier security, incident management, logging, secure development, and related ISO-aligned policies. |

---

## 18. Open Questions

| ID | Question | Owner | Priority | Status |
| --- | --- | --- | --- | --- |
| OQ-15-001 | What final privacy notice, personal information collection statement, and terms wording are required for Hong Kong launch? | Legal / Privacy | High | Open |
| OQ-15-002 | Which KYC/KYB provider data fields, artifacts, ID copies, and verification results will PayPlus store versus reference through provider? | Compliance / Security / Engineering | High | Open |
| OQ-15-003 | Which approved-purpose access, masking, legal-hold, correction and privacy-request controls apply by data class and purpose under the accepted indefinite-retention direction and its lawful-scope qualification? | Legal / Privacy / Finance | High | Answered: direction is indefinite; controls remain owner-governed |
| OQ-15-004 | What data may be used for analytics, model improvement, segmentation, and commercial reporting? | Privacy / Data / Product | High | Open |
| OQ-15-005 | What cross-border processing locations and subprocessors apply for KYC, OCR, PSP, cloud, SMS, email, WhatsApp, analytics, and support providers? | Privacy / Security / Vendor Management | High | Open |
| OQ-15-006 | What user consent, preference, and opt-out rules apply to promotion, referral, partner offer, WhatsApp, SMS, and email communication? | Product / Legal / Privacy | Medium | Open |
| OQ-15-007 | Which sensitive evidence fields are displayable, masked, or restricted by role and category? | Product / Privacy / Security | High | Open |
| OQ-15-008 | What data-subject access, correction, privacy-request and legal-hold workflow applies without changing the accepted indefinite-retention direction, subject to lawful scope and required exceptions, or erasing the underlying record? | Privacy / Operations / Legal | Medium | Open |
| OQ-15-009 | What inactivity period triggers dormant-login reauthentication, and which factor should be required? | Security / Product / Risk | Medium | Open |
| OQ-15-010 | What exact PCI DSS scope, SAQ/ROC path, QSA/acquirer expectations, and responsibility matrix apply before production launch? | Security / Payments / Compliance | High | Open |
| OQ-15-011 | What ISO/IEC 27001 control evidence should DOC-15 privacy and data handling controls produce for the ISMS? | Security / Compliance / Privacy | Medium | Open |
| OQ-15-012 | What consent, preference, approved-purpose access and analytics rules apply to account-level shortcut preferences, placement exposure, carousel impressions and personalized offer targeting? Functional shortcut management does not itself require marketing consent; record retention follows the accepted indefinite-retention direction subject to lawful scope and required exceptions. | Product / Privacy / Growth | Medium | Partially open |
| OQ-15-013 | Which data classes, fields, derived features, segments, scores, and AI outputs may be used for model improvement, personalization, partner reporting, and campaign measurement? | Privacy / Data / Product | High | Open |
| OQ-15-014 | Which data classes, fields, and derived signals are prohibited from marketing models, partner reporting, clean-room collaboration, or offsite activation? | Privacy / Legal / Risk | High | Open |
| OQ-15-015 | What consent, opt-out, notice, partner-contract, and output-control rules are required before clean-room collaboration, pseudonymized matching, or external activation? | Legal / Privacy / Security | High | Open |
| OQ-15-016 | What approved-purpose privacy, masking, proof-access and retention requirements apply to owner-governed source-context destination facts? | Privacy / Security / Payments | High | Open |

---

## 19. Acceptance Criteria

DOC-15 is acceptable when it clearly defines:

- PayPlus's lawful data utility principle;
- data classification for account, authentication, KYC/KYB, evidence, payment, payout, risk, support, promotion, communication, analytics, and derived data;
- registration, login, new-device 2FA, dormant-login reauthentication, biometric unlock, payment passcode, password reset, and material-change handling baseline;
- identity and KYC/KYB data boundaries;
- evidence and obligation data handling;
- payer, payee, admin, system, vendor, and partner visibility rules;
- referral attribution privacy, masking, no-recipient-on-share, and separation from retired participant linking;
- consent, notice, and communication privacy boundaries;
- data-use tiers, partner-sharing boundaries, model-use governance, and sensitive-data red lines;
- dashboard shortcut preference, placement exposure, personalization, and user preference boundaries;
- analytics and data product expectations;
- retention, record-handling and legal-hold expectations;
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
| 1.0.2 | 2026-08-27 | Product Documentation Team | Aligned approved-purpose history access, masking, visibility and retention with DOC-18 business recording, DOC-19 enforcement-only, DOC-21 consume-only and DOC-22 specifically permitted execution boundaries. |
| 1.0.1 | 2026-08-21 | Product Documentation Team | Aligned privacy, recovery, representation, Admin, and PCI handoffs with the reviewed mechanism-neutral DOC-19 contract while retaining DOC-15 privacy ownership and unresolved professional/implementation dependencies. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. | Stage 11 alignment evidence |
| `0.9.3` | `2026-08-13` | Product Documentation Team | Distinguished the 30-minute registration-attempt usability window from indefinite record retention without adding a deletion or disposal mechanism. |
| `0.9.2` | `2026-08-12` | Product Documentation Team | Recorded the Founder-settled indefinite-retention decision, removed finite/open-duration language, and reframed privacy, access, legal-hold and correction handling without creating a disposition mechanism. |
| `0.9.1` | `2026-08-12` | Product Documentation Team | Consolidated provider/authentication/retention, hypothetical-scope, DOC-22 execution-only and source/Payment Obligation privacy-boundary corrections. |
| `0.9.0` | `2026-08-12` | Product Documentation Team | Aligned privacy scope with the Payer-only/economic-Payee source model; retired Request/Linking/Receiving Info runtime data; and clarified DOC-15 requirements versus DOC-18 representation. |
| `0.8.21` | `2026-08-06` | Product Documentation Team | Replaced the superseded combined Home placement terminology with Home Hot Offer while preserving the existing consent, preference, approved-purpose, role-appropriate visibility, protected-access, eligibility, risk, compliance, and privacy-safe analytics rule. |
| `0.8.20` | `2026-07-31` | Product Documentation Team | Aligned Request visibility, payment/funding data classification, and DOC-09 title references with the accepted Payment Domain aggregate and derived-value model. |
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
