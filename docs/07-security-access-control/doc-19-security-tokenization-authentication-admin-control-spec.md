---
document_id: DOC-19
title: Security, Tokenization, Authentication & Admin Control Specification
version: 0.1.2
status: Draft
owner: Security Architecture Owner
reviewers:
  - Security Architecture
  - Risk/Privacy
  - Operations/Acceptance
approvers:
  - Founder
last_updated: 2026-08-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06B Navigation, IA & Route Taxonomy
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Specification
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-14 AML, Anti-Cashout, Fraud & Dynamic Auth Risk Control Specification
  - DOC-15 Privacy, Data Protection & Record Retention Specification
  - DOC-16 Technical Architecture Specification
  - DOC-17 API & Third-party Integration Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operational SOPs
  - DOC-22 Admin Management Dashboard & Operations Workflow
  - DOC-99 ISMS Policy Library
---

# DOC-19 - Security, Tokenization, Authentication & Admin Control Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | DOC-19 |
| **Title** | Security, Tokenization, Authentication & Admin Control Specification |
| **Version** | 0.1.2 |
| **Status** | Draft |
| **Owner** | Security Architecture Owner |
| **Reviewers** | Security Architecture<br>Risk/Privacy<br>Operations/Acceptance |
| **Approvers** | Founder |
| **Last Updated** | 2026-08-27 |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Specification<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-14 AML, Anti-Cashout, Fraud & Dynamic Auth Risk Control Specification<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-16 Technical Architecture Specification<br>DOC-17 API & Third-party Integration Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operational SOPs<br>DOC-22 Admin Management Dashboard & Operations Workflow<br>DOC-99 ISMS Policy Library |

> This Draft is not an Approved source of truth and does not establish implementation, operating effectiveness, ISO/IEC 27001 certification, PCI DSS compliance or scope, provider approval, regulatory approval, production readiness, or launch readiness.

## 1. Purpose, scope, and ownership

DOC-19 is PayPlus's cross-domain technical security-control contract. It translates accepted owner rules and the DOC-16 trust-boundary posture into security invariants, technical enforcement requirements, prohibited exposure, and verification handoffs.

It owns security-control requirements for identity and authentication, sessions/devices, recovery, credentials/secrets, token and cryptographic-material treatment, access enforcement, privileged operations, provider/card-data treatment, secure boundary handling, logging/redaction, technical anti-automation, security telemetry, and verification handoffs.

DOC-19 is mechanism-neutral. It does not select a provider, API, schema, event, protocol, algorithm, key, session value, factor, timeout, rate limit, status, route, product behaviour, deployment product, or implementation mechanism.

| DOC-19 owns | Primary owner elsewhere |
| --- | --- |
| Security invariants, enforcement requirements, prohibited exposure, and security evidence obligations | Product/account/route behaviour: DOC-05 and DOC-06B |
| Security enforcement around a controlled Bill/Rent/Evidence/Payment/Payout context | Bills/Rent source and route meaning: DOC-06C; Evidence/verification meaning: DOC-12; Payment/payer authorization: DOC-09; Settlement/Payout/reconciliation: DOC-10 |
| Technical enforcement of an owner-required security assurance condition | Payer authorization, Payment, and admission: DOC-09; risk trigger, threshold, action, and outcome: DOC-14 |
| Security treatment of provider-controlled card capture and handoffs | Architecture/trust posture: DOC-16; provider/API/callback/credential contract: DOC-17; business-recording and explainability handoff: DOC-18; exact technical representation remains separately gated |
| Least privilege, reauthentication, audit, and segregation support for permitted privileged action | Action meaning, maker/checker policy, exceptions, queues, configurations, and Admin workflow: affected owner and DOC-22 |
| Security-control verification handoffs | Acceptance: DOC-20; operations: DOC-21; privacy and retention: DOC-15; ISMS policy/certification: DOC-99 |

For current or historical information, the applicable domain owner defines the purpose and relevant history; DOC-15 owns approved-purpose access, masking, visibility and retention. DOC-19 only enforces access that those owners have already permitted. It creates no access, presentation or retrieval authority. DOC-22 may execute only a specifically owner-permitted presentation or retrieval operation, and DOC-21 may consume already permitted operational evidence only.

## 2. Accepted security-control inputs and non-reopening rule

The following inputs are consumed without redefinition: risk-isolated modular architecture; provider-controlled capture/tokenization with no PayPlus raw PAN or card-verification values; local atomic authority; durable/idempotent/auditable handoffs; the established Bills/Evidence/Payment/Payout baseline; existing owner separation; and Security & Compliance by Design.

Applicable ISO/IEC 27001 and PCI DSS requirements are design and evidence direction for the affected security controls. Their applicability, scope, shared responsibility, assessment path, and compliance outcome require appropriate professional confirmation. This Draft does not claim implementation, operating effectiveness, certification, compliance, provider approval, production readiness, or launch.

DOC-19 does not reopen accepted payment, risk, privacy, architecture, or ownership meaning. Cross-document effects require governing change control and relevant owner authorization.

## 3. Required terminology and separation

| Term | DOC-19 meaning | Must remain distinct from |
| --- | --- | --- |
| Authentication/session assurance | Technical establishment, continuation, revocation, or renewal of an authenticated context. | Payer authorization, provider/cardholder authentication, Provider Confirmation, Payment, and Payout release. |
| Security assurance condition | Technical enforcement of assurance required by an owner. | DOC-14 risk decision/threshold/action and DOC-09 payment admission. |
| Payment passcode | A payer-confirmation control used where owners require it. | An account credential, payer authorization itself, provider result, or confirmed Payment. |
| Provider token/reference | A permitted integration reference or masked metadata. | Raw PAN, card-verification value, session token, credential, secret, or PCI-scope conclusion. |
| Credential, secret, OTP, passcode, cryptographic material | Protected value families with different purposes. | Each other; no token/reference is automatically a secret. |
| Security fact/audit occurrence | A permitted record of a security-relevant attempt, decision, result, revocation, or recovery. | Domain status, Outcome, Notification, Payment fact, or control-effectiveness proof. |
| Privileged action | A domain-owner-permitted operation with security enforcement. | A generic Admin disposition, role catalogue, queue, override, or policy. |
| Operational expiry/revocation | A capability becomes unusable. | Deletion of a permitted record or audit fact. |

## 4. Control-card model and control consequences

Every material control has a stable Control Card: source owner/rule; invariant; prohibited behaviour; product/business risk; reasonable non-sensitive verification evidence; applicable DOC-18, DOC-20, DOC-21, DOC-15, DOC-17, and DOC-22 handoffs; and a reason for each N/A.

Each card lists one or more applicable consequence classifications below. A classification with no matching prohibited behaviour is omitted, or shown as N/A with its reason. The vocabulary does not create a mechanical five-class matrix, a new control path, or a business/risk outcome.

| Classification | Meaning |
| --- | --- |
| **Absolute prohibition** | The operation or exposure must not occur. |
| **Revalidation required before proceeding** | Current authority, assurance, owner facts, or state must be checked again. |
| **Permitted only under owner-defined conditions** | Enforcement may occur only where the named owner supplies the condition. |
| **Monitor/record only and must not automatically block** | Preserve a permitted fact or signal without making a business/risk block. |
| **Escalate to the designated owner** | Preserve safe facts and route the concern; do not decide the domain outcome. |

## 5. Material Control Cards

### CTRL-19-001 - Identity, authentication, recovery, session, and device assurance

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | DOC-06B owns AUTH-family route behaviour, Recovery, protected returns, and device/login context; DOC-07 owns disclosure and message/CTA; DOC-15 owns disclosure-safe authentication-data treatment; DOC-18 owns business-recording and explainability obligations, while exact technical representation remains separately gated. Matching email addresses do not automatically link, merge, or transfer accounts. |
| **Security invariant** | Authentication and recovery establish only the approved account/login-method context. Session, remembered-device, redirect, notification, callback, or other continuation may be used only while current authority and required assurance remain valid. |
| **Prohibited behaviour and consequence** | Automatic account merge or provider link by email - **Absolute prohibition**. Public recovery disclosure of account, credential, provider link, phone, identity, device, or restriction existence - **Absolute prohibition**. Treat phone, identity, device, or provider email as a recovery method without an applicable owner-defined recovery rule and required DOC-19 security enforcement - **Permitted only under owner-defined conditions**. Reuse stale, revoked, expired, consumed, or unauthorized continuation - **Revalidation required before proceeding**. No safe recovery or contradictory context - **Escalate to the designated owner**. |
| **Product/business risk** | Account takeover, enumeration, identity confusion, unsafe recovery, stale access, and unintended protected continuation. |
| **Reasonable non-sensitive verification evidence** | Protected tests for valid, invalid, expired, repeated, conflicted, revoked, and protected-return cases; neutral-response evidence; correlation/audit evidence that excludes credentials, OTPs, passcodes, and recovery secrets. |
| **Handoffs** | DOC-18: opaque attempt/outcome/resolution business history and explainability; technical correlation representation remains separately gated. DOC-20: positive, neutral-equivalence, negative, expiry, replay, interruption, and revalidation evidence. DOC-21: consume-only security/support escalation evidence. DOC-15: classification, masking, purpose, and retention constraints. DOC-17: provider identity/recovery detail where a provider contract applies. DOC-22: N/A for ordinary self-service flows; it may execute only expressly owner-permitted Support/Admin action. |

### CTRL-19-002 - Security-assurance enforcement around payment and risk gates

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | DOC-09 owns payer authorization and Payment admission. DOC-14 owns risk triggers, thresholds, actions, and outcomes. DOC-16 requires re-evaluation at material trust boundaries. |
| **Security invariant** | Where an owner requires an assurance condition, DOC-19 enforces the required security control and permitted evidence without defining the trigger, factor, threshold, Payment semantics, or business consequence. |
| **Prohibited behaviour and consequence** | Treat authentication, passcode entry, provider/cardholder challenge, provider observation, or security fact as payer authorization, Provider Confirmation, Payment, Payment Application, or Payout release - **Absolute prohibition**. Submit/resume with stale authorization or without owner-required checks - **Revalidation required before proceeding**. Enforce assurance only where DOC-09, DOC-14, provider, or another owner has supplied the condition - **Permitted only under owner-defined conditions**. Unenforceable or conflicting assurance requirement - **Escalate to the designated owner**. |
| **Product/business risk** | Unauthorized Provider Submission, risk bypass, false Payment certainty, fraud, chargeback, and payout loss. |
| **Reasonable non-sensitive verification evidence** | Traceable scenarios separating risk trigger, assurance enforcement, payer authorization, provider evidence, Payment result, and Payout; negative evidence that no automatic submission or Payment claim occurs. |
| **Handoffs** | DOC-18: permitted assurance-reference business history and audit meaning; technical representation remains separately gated. DOC-20: separation and negative-path acceptance evidence. DOC-21: consume-only exception/escalation evidence. DOC-15: approved-purpose privacy treatment. DOC-17: provider/cardholder challenge detail where relevant. DOC-10: Payout/reconciliation meaning; security does not determine release. DOC-22: N/A unless an owner permits an operation; no action matrix is created. |

### CTRL-19-003 - Protected values, secrets, tokens, and cryptographic material

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | DOC-15 owns classification, approved purpose, masking, retention, and lawful-scope assessment. DOC-16 requires minimisation and prohibits raw PAN/card-verification values in logs, analytics, handoffs, test data, and support tools. |
| **Security invariant** | Credentials, secrets, one-time values, passcodes, OTPs, security tokens, and cryptographic material are minimised, purpose-separated, protected, and never confused with provider token/reference values or raw card data. Any later non-human or integration credential is purpose-separated and least privileged under an owner-approved DOC-17 contract; it cannot confer generic domain, Payment, or privileged-action authority. |
| **Prohibited behaviour and consequence** | Store, process, transmit, retain, reconstruct, display, infer, log, or hand off raw PAN or card-verification values in PayPlus systems under the accepted boundary - **Absolute prohibition**. Expose raw/plaintext passwords, passcodes, OTPs, recovery secrets, or cryptographic private material, if later used, in logs, traces, analytics, support exports, screenshots, test fixtures, examples, or handoffs - **Absolute prohibition**. Reuse expired, revoked, consumed, or purpose-mismatched protected value - **Revalidation required before proceeding**. Use or retain permitted hashes, references, security-lifecycle facts, or necessary protected material only under later security-owner technical treatment, owner-defined purpose, and DOC-15 classification/lawful handling - **Permitted only under owner-defined conditions**. Suspected protected-value exposure - **Escalate to the designated owner**. |
| **Product/business risk** | Credential theft, payment-data exposure, account takeover, PCI exposure, privacy harm, fraud, and incident impact. |
| **Reasonable non-sensitive verification evidence** | Redaction/minimisation inspection; protected negative tests; non-sensitive inventory/configuration evidence separating value families; suspected-exposure escalation evidence. |
| **Handoffs** | DOC-18: only permitted references/classifications/audit facts. DOC-20: prohibited-value and expiry/revocation evidence. DOC-21: incident/support evidence. DOC-15: classification, purpose, masking, retention, and lawful-scope constraints. DOC-17: provider token/reference and credential detail where applicable. DOC-22: N/A unless an owner permits an operational action. |

### CTRL-19-004 - Access enforcement and privileged-operation protection

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | Affected domain owners decide whether action exists and its truth. DOC-15 owns approved-purpose access/masking. DOC-16 requires least privilege, segregation, current-state revalidation, and audit. DOC-22 is owner-permitted execution only. |
| **Security invariant** | Privileged action requires current-authority revalidation, proportionate reauthentication, least-privilege enforcement, auditability, segregation support, and support for owner-defined maker/checker controls where applicable. |
| **Prohibited behaviour and consequence** | Perform, approve, expose, or override without current authority, approved purpose, required assurance, or auditability - **Absolute prohibition**. Continue after relevant authority/state/assurance changes - **Revalidation required before proceeding**. Apply maker/checker only where owner defines it - **Permitted only under owner-defined conditions**. Unsafe, conflicting, or unavailable privileged treatment - **Escalate to the designated owner**. |
| **Product/business risk** | Unauthorized data access, Payment/Payout/risk override, operational abuse, privacy breach, and audit failure. |
| **Reasonable non-sensitive verification evidence** | Current-authority and reauthentication scenarios; permitted audit evidence; proof that no generic Admin queue, role catalogue, override policy, or action matrix was created. |
| **Handoffs** | DOC-18: business history, action-basis, lineage and audit-meaning obligations only. DOC-20: privileged-access and negative-path evidence. DOC-21: consume-only security/operations escalation evidence, with no access/presentation/retrieval authority. DOC-15: purpose, masking, visibility and retention constraints. DOC-17: N/A unless later provider privileged access applies. DOC-10: Payout/reconciliation meaning where a privileged action affects that domain; security does not decide it. DOC-22: only a specifically owner-permitted action; no generic access or policy authority. |

### CTRL-19-005 - Provider-controlled card-data and secure external boundaries

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | DOC-16 owns provider-controlled capture/tokenization and no raw PAN/card-verification values. DOC-09 owns payment meaning. DOC-17 owns provider/API/callback/credential/environment detail. DOC-18 owns business-recording and explainability obligations; technical representation remains separately gated. |
| **Security invariant** | PayPlus controls preserve the provider-card boundary across normal, failure, retry, support, reconciliation, audit, and test paths. Public input, callback, redirect, notification context, handoff, projection, and operational signal must not become authority for another owner's fact. |
| **Prohibited behaviour and consequence** | Receive, process, transmit, retain, reconstruct, display, infer, log, or hand off raw PAN/card-verification values under the accepted boundary - **Absolute prohibition**. Treat provider return/callback/redirect/token/reference as payer authorization, Payment, or Payout truth - **Absolute prohibition**. Continue a provider or boundary operation without current validity/security/state checks - **Revalidation required before proceeding**. Process external/handoff data only under owner-defined contract, classification, and purpose - **Permitted only under owner-defined conditions**. Preserve duplicate, late, missing, unknown, or contradictory observation without rewriting owner truth - **Monitor/record only and must not automatically block**. Suspected exposure, contract contradiction, or unsafe boundary - **Escalate to the designated owner**. |
| **Product/business risk** | Card-data exposure, replay/tampering, duplicate financial effects, incorrect Payment confirmation, PCI/shared-responsibility risk, and loss of authoritative truth. |
| **Reasonable non-sensitive verification evidence** | Boundary and prohibited-value checks; duplicate/late/replay/stale scenario evidence; non-sensitive separation of provider observation from Payment creation; provider responsibility evidence when later available. |
| **Handoffs** | DOC-18: permitted token/reference business history, lineage and audit meaning; technical correlation/audit representation remains separately gated. DOC-20: boundary and prohibited-value evidence. DOC-21: consume-only incident, recovery, reconciliation, and escalation evidence. DOC-15: masking, purpose, retention, lawful-scope constraints. DOC-17: required for provider-specific contract detail. DOC-10: Payout/reconciliation meaning; provider/security observation cannot establish release. DOC-22: N/A unless an owner permits an operational response; it cannot configure card-data policy. |

### CTRL-19-006 - Logging, technical anti-automation, and safe telemetry

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | DOC-16 owns architecture-level observability/evidence obligations. DOC-15 owns privacy controls. DOC-14 owns fraud/risk meaning and financial outcomes. DOC-18 owns business-recording and explainability obligations; exact representation remains separately gated; DOC-20 owns acceptance; DOC-21 owns operations without access/retrieval authority. |
| **Security invariant** | Security facts needed for assurance, recovery, privileged action, boundary handling, anti-automation, and suspected exposure are safely observable without copying prohibited/unnecessary sensitive values. Authentication, recovery, session, protected-access, and privileged-operation surfaces require proportionate technical anti-automation protection where security analysis indicates it. |
| **Prohibited behaviour and consequence** | Include raw PAN/card-verification values, credentials, secrets, OTPs, passcodes, recovery material, unnecessary provider payloads, or unnecessary restricted identity/evidence values in logs, traces, analytics, support exports, screenshots, test fixtures, or handoffs - **Absolute prohibition**. Treat telemetry/anti-automation signal as Payment, Payout, fraud, or risk decision - **Absolute prohibition**. Continue a protected attempt where control state requires current verification - **Revalidation required before proceeding**. Expose/use telemetry or apply protection only under owner-defined access/purpose/policy conditions - **Permitted only under owner-defined conditions**. Record permitted control signal without automatic business block - **Monitor/record only and must not automatically block**. Suspected leakage, tampering, repeated unsafe condition, or material evidence gap - **Escalate to the designated owner**. |
| **Product/business risk** | Sensitive-data exposure, credential stuffing/enumeration, false assurance, improper operational action, and inability to investigate safely. |
| **Reasonable non-sensitive verification evidence** | Redaction/minimisation inspection; repeated/expired/replayed attempt tests; evidence that financial/risk meaning stays with DOC-14; control-to-source traceability and safe operational routing. |
| **Handoffs** | DOC-18: business occurrence, audit meaning, history and lineage obligations; machine event/audit representation remains separately gated. DOC-20: redaction, negative, regression, and verification evidence. DOC-21: consume-only monitoring, incident, support, escalation, and closure evidence. DOC-15: classification, masking, purpose, retention, lawful-scope controls. DOC-17: N/A except later provider logging/throttling contract. DOC-10: Payout/reconciliation meaning where telemetry concerns that domain; telemetry cannot decide release. DOC-22: may execute only owner-permitted operational action. |

### CTRL-19-007 - Security verification, change exposure, and supplier-security handoff

| Field | Requirement |
| --- | --- |
| **Source owner/rule** | DOC-00 governs documentation control; DOC-16 requires security review for changed trust/payment-data/authentication/authorization/secret/privileged boundaries; DOC-19 defines security-verification handoffs; DOC-20 owns acceptance/UAT/release evidence; DOC-21 owns monitoring, incident, support, escalation, and closure evidence; DOC-99 owns ISMS policy content. |
| **Security invariant** | Each material security control has traceable design, implementation-verification, and operational-evidence handoffs. A changed DOC-19 boundary is assessed against source owner, invariant, exposure restriction, verification handoff, and enablement dependency before the affected scope is represented as enabled or ready. |
| **Prohibited behaviour and consequence** | Claim implementation, operating effectiveness, certification, compliance, provider approval, PCI scope, production readiness, or launch from this Draft, a supplier assertion, or a security fact alone - **Absolute prohibition**. Treat changed trust/authentication/privileged/secret/payment-data boundary as unchanged - **Revalidation required before proceeding**. Use supplier/security evidence only under owner-defined provider, privacy, risk, and operational conditions - **Permitted only under owner-defined conditions**. Material boundary exception, unresolved shared responsibility, evidence failure, or unresolvable conflict - **Escalate to the designated owner**. |
| **Product/business risk** | False assurance, undetected boundary expansion, supplier exposure, weak shared responsibility, unreviewed regression, and unsafe enablement. |
| **Reasonable non-sensitive verification evidence** | Control-to-source mapping; impact/review records; non-sensitive design, test, and operational evidence distinguished from operating-effectiveness proof; explicit unresolved enablement gates. |
| **Handoffs** | DOC-18: N/A unless later representation changes are accepted; this card creates no data model. DOC-20: acceptance evidence for an accepted scope. DOC-21: operational/incident evidence. DOC-15: privacy/vendor treatment where data is involved. DOC-17: provider/supplier contract. DOC-22: N/A unless an owner permits execution; it never certifies control operation. |

## 6. Operational expiry, retention, and non-erasure

Expiry, revocation, closure, invalidation, or restart may make a session, credential, OTP, passcode, token, one-time value, or temporary capability unusable. It does not itself delete, purge, destroy, anonymise, de-identify, or erase a permitted record or audit fact.

The accepted indefinite-retention direction for applicable records does not require indefinite retention of ephemeral secrets, credentials, one-time values, prohibited card data, or unnecessary sensitive material. DOC-15 owns lawful scope, exceptions, restricted classes, purpose, masking, visibility, retention, legal hold, and professional confirmation. DOC-19 enforces minimisation/non-exposure without selecting a duration or disposition mechanism.

## 7. Open Dependencies / Enablement Gates

These do not block documentation expression. They block the affected scope from being enabled, accepted, launched, or represented as assured until resolved.

| ID | Dependency / enablement gate | Owner | Affected scope |
| --- | --- | --- | --- |
| DEP-19-001 | PCI DSS applicability, scope, shared responsibility, assessment path, and acquirer/QSA expectations. | Security / Payments / Compliance / professional assessment | Provider/card-data and payment-related enablement. |
| DEP-19-002 | Provider/API/callback/credential/environment contract and supplier-security evidence. | DOC-17 / provider owners | Provider-dependent control implementation and assurance. |
| DEP-19-003 | Lawful scope, exceptions, restricted data, retention, masking, and approved-purpose treatment. | DOC-15 / Legal / Privacy | Data-bearing controls and operational access. |
| DEP-19-004 | Final security data/event/audit/correlation representation that preserves DOC-18's reviewed business meaning. | Future separately authorized Engineering / Data work; DOC-18 supplies business inputs | Implementation and traceability representation. |
| DEP-19-005 | Detailed security acceptance/UAT/release evidence. | DOC-20 | Acceptance/readiness claims. |
| DEP-19-006 | Monitoring, incident, support, escalation, and runbook detail. | DOC-21 | Operational enablement/evidence. |
| DEP-19-007 | Owner-permitted Admin action, maker/checker rule, queue, exception, and configuration detail. | Affected owner / DOC-22 | Privileged operational action. |
| DEP-19-008 | ISMS policy and supplier-security evidence. | DOC-99 / Security / Compliance | Policy/assurance treatment. |

## 8. Acceptance criteria and verification handoff

| ID | Acceptance criterion |
| --- | --- |
| SEC19-AC-001 | DOC-19 has one security-control owner and explicit non-ownership of payment, risk, privacy, provider/API, data/event, operations, acceptance, Admin-domain truth, and DOC-99 policy/certification. |
| SEC19-AC-002 | Every material control has an ID, source owner/rule, invariant, prohibited behaviour, business risk, non-sensitive verification evidence, applicable handoffs, and justified N/A. |
| SEC19-AC-003 | Every Control Card uses one or more applicable consequence classifications, omits or gives a reasoned N/A for inapplicable classifications, and avoids blanket blocking, unsafe permissiveness, or manufactured control paths. |
| SEC19-AC-004 | Bills/Rent source and Evidence meaning, authentication/session, payer authorization, risk decision, provider challenge/observation, Provider Confirmation, Payment, Payment Application, Settlement/Payout/reconciliation, and Payout release remain separate and with their named owners. |
| SEC19-AC-005 | Privileged-operation controls require authority revalidation, proportionate reauthentication, auditability, segregation support, and owner-defined maker/checker support without creating Admin policy. |
| SEC19-AC-006 | Provider-controlled capture/tokenization and no raw PAN/card-verification values are preserved across normal, failure, retry, support, reconciliation, audit, telemetry, analytics, test, and handoff paths. |
| SEC19-AC-007 | Protected values are minimised/redacted while permitted non-sensitive evidence remains available. |
| SEC19-AC-008 | Operational expiry/revocation remains distinct from record retention and DOC-15 ownership. |
| SEC19-AC-009 | PCI, provider, privacy, data, acceptance, operations, Admin, and ISMS dependencies remain enablement gates without assurance claims. |
| SEC19-AC-010 | Provider mechanics, schemas/events, parameters, thresholds, protocols, algorithms/keys, session values, factors, timeouts, and rate limits remain deferred to the proper owner. |

## 9. Open questions

| ID | Question | Owner | Status |
| --- | --- | --- | --- |
| OQ-19-001 | Which mechanisms, protocols, factors, session/device values, recovery proofs, retry/lockout controls, and rate limits implement these requirements? | Security / Engineering | Open; delegated technical decision. |
| OQ-19-002 | Which provider security, callback, credential, payment-page, and shared-responsibility contract applies to each enabled path? | DOC-17 / Security / Payments | Open; provider enablement gate. |
| OQ-19-003 | Which fields, events, correlations, and audit representations implement the control cards while preserving DOC-18's reviewed business meaning? | Engineering / Data / Security under separate future authority | Open; DOC-18 does not currently approve the mechanism. |
| OQ-19-004 | Which detailed tests, UAT evidence, release gates, monitoring signals, and runbooks demonstrate enabled controls? | DOC-20 / DOC-21 / Security | Open. |
| OQ-19-005 | Which privileged actions, maker/checker rules, roles, queues, exceptions, and configurations are owner-permitted? | Affected owner / DOC-22 | Open; not owned by DOC-19. |
| OQ-19-006 | Which lawful-scope, exception, restricted-data, purpose, masking, retention, and supplier-security treatments apply? | DOC-15 / Legal / Privacy / Compliance | Open. |
| OQ-19-007 | What PCI scope, assessment path, shared responsibility, acquirer/QSA expectations, and evidence apply before launch? | Security / Payments / Compliance | Open; professional confirmation required. |

## Version History

| Version | Date | Owner | Change Summary |
| --- | --- | --- | --- |
| 0.1.2 | 2026-08-27 | Security Architecture Owner | Made the history-access handoff explicitly enforcement-only after owner and DOC-15 permission, with no access, presentation, retrieval, or technical-representation authority. |
| 0.1.1 | 2026-08-21 | Security Architecture Owner | Refined the source-document boundary and corrected dependency-table structure without changing security-control meaning. |
| 0.1.0 | 2026-08-21 | Security Architecture Owner | Initial Draft: mechanism-neutral cross-domain security controls, Control Cards, owner handoffs, verification treatment, and enablement gates without selected mechanisms or assurance claims. |
