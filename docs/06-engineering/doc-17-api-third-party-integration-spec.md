---
document_id: DOC-17
title: API & Third-party Integration Specification
version: 0.1.0
status: Draft
owner: Engineering / Integration
reviewers:
  - TBD
approvers:
  - TBD
last_updated: 2026-08-25
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06C Bills, Rent & Tenancy UX Module
  - DOC-07 Content, Disclosure & User Authorization Specification
  - DOC-08 Notification, Receipt & Communication Specification
  - DOC-09 Payment Domain Architecture
  - DOC-10 Payout & Reconciliation
  - DOC-11 Refund, Cancellation & Chargeback
  - DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification
  - DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification
  - DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification
  - DOC-15 Privacy, Data Protection & Record Retention Specification
  - DOC-16 Technical Architecture Specification
  - DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification
  - DOC-19 Security, Tokenization, Authentication & Admin Control Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operational SOPs
  - DOC-22 Admin Management Dashboard & Operations Workflow
---

# DOC-17 - API & Third-party Integration Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-17` |
| **Title** | API & Third-party Integration Specification |
| **Version** | `0.1.0` |
| **Status** | Draft |
| **Owner** | Engineering / Integration |
| **Reviewers** | TBD |
| **Approvers** | TBD |
| **Last Updated** | `2026-08-25` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Specification<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-16 Technical Architecture Specification<br>DOC-18 Data Model, Transaction State, Audit Event & Reporting Specification<br>DOC-19 Security, Tokenization, Authentication & Admin Control Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operational SOPs<br>DOC-22 Admin Management Dashboard & Operations Workflow |

> **Draft boundary.** This Draft expresses a provider-neutral External Interaction Contract. It is not an Approved source of truth and does not select a provider, establish a provider capability or approval, define an API, schema, event, status, credential, security mechanism, implementation, test result, operating effectiveness, enablement, or launch readiness.

## 1. Purpose, scope, and ownership

DOC-17 translates accepted PayPlus product, domain, architecture, security, privacy, risk, operations, and acceptance requirements into a reviewable provider-neutral external interaction contract. It defines the required interaction evidence, separation of authority, and owner handoffs that a later selected external provider or integration pattern must faithfully realise.

DOC-17 is the primary owner for the provider-neutral interaction contract, its Functional-Surface Coverage, and its evidence and handoff obligations. It does not become the primary owner of the facts or consequences that an interaction may concern.

| Concern | Primary owner | DOC-17 role |
| --- | --- | --- |
| Payment, payer authorization, Provider Confirmation, Payment, and Payment Application | DOC-09 | Define interaction and confirmation-evidence obligations without determining payment or authorization truth. |
| Payout, settlement, bank evidence, and reconciliation | DOC-10 / Finance where applicable | Define bank/file/feed/manual-observation obligations without accepting a payout or reconciliation result. |
| Refund, reversal, dispute, chargeback, and case consequence | DOC-11 | Define case-related interaction evidence without deciding case or financial treatment. |
| Bill/Rent evidence, document verification, OCR, and payee verification | DOC-12 where applicable | Define an applicable external Evidence or document-verification boundary without accepting Evidence or transferring identity authority. |
| Risk, anti-cashout, fraud, and dynamic authorization | DOC-14 | Define owner-required interaction evidence without determining a risk outcome or control action. |
| Privacy, purpose, masking, retention, vendor, and cross-border treatment | DOC-15 | Consume applicable data-handling constraints and require their later evidence; do not decide privacy or legal treatment. |
| Architecture, trust boundary, reliability, recovery, and local authority | DOC-16 | Consume architecture constraints and hand off technical realisation; do not choose an architecture or mechanism. |
| Representation, correlation, event, audit, and lineage | DOC-18 | Hand off facts that must be represented; do not define fields, schemas, events, states, or persistence. |
| Security, protected values, access enforcement, and verification | DOC-19 | Consume the mechanism-neutral security-control contract; do not choose a security mechanism or assert assurance. |
| Acceptance, operations, and owner-permitted execution | DOC-20 / DOC-21 / DOC-22 | Hand off evidence needs; do not claim acceptance, operating readiness, or authorize an operation. |

## 2. Contract orientation and non-ownership rule

The required reasoning order is:

```text
Accepted PayPlus owner rules
-> DOC-17 provider-neutral External Interaction Contract
-> candidate-specific factual evidence and feasibility assessment
-> future provider selection and professional confirmation
-> provider-specific realisation mapping
-> implementation and acceptance evidence
```

Candidate-provider documentation, delivery records, callbacks, returns, queries, files, reports, redirects, token or reference values, and manual uploads are supporting observations or evidence only. They cannot narrow, replace, or reopen an accepted PayPlus requirement, and they do not by themselves become Payment, Payout, Evidence acceptance, risk, identity, authorization, notification decision, case, privacy, or other PayPlus truth.

DOC-17 must not be used to introduce a wallet, stored-value account, unrestricted peer-to-peer transfer, cashout, remittance, lending, cash advance, or open money-request marketplace model.

## 3. Terms and authority layers

| Term | Meaning and boundary |
| --- | --- |
| **External Interaction** | A provider-neutral exchange, delivery, inbound observation, outbound consumer relationship, or operational interaction that may require contract evidence. It does not imply a selected provider or an implemented interface. |
| **External Observation** | A received or attempted external signal, including a return, callback, query result, file, report, delivery record, redirect, or manual upload. It is not authoritative PayPlus truth by itself. |
| **Interaction Reference** | A provider-neutral reference used for correlation or later investigation. It is not an authorization, financial result, or protected value. |
| **Integrity / Provenance Evidence** | Evidence concerning source, completeness, correlation, timing, delivery, or limitation. It does not decide domain acceptance. |
| **Representation / Lineage** | The later record of observation, source, correlation, and relationship. DOC-18 owns its representation. |
| **Owner Evaluation** | The applicable formal owner evaluates whether an observation is sufficient under its approved rule. DOC-17 cannot perform or pre-decide that evaluation. |
| **Domain Acceptance** | An owner-defined decision affecting a domain fact. It remains separate from transport, provenance, and financial or case consequence. |
| **Financial / Case Consequence** | A Payment, Payout, refund, reversal, dispute, chargeback, reconciliation, adjustment, hold, or case effect owned by the applicable domain owner. |
| **Uncertainty** | A known absence, ambiguity, conflict, duplication, replay, delay, staleness, malformation, unknown origin, or unavailable observation. It must remain visible and must not be converted into an assumed result. |
| **Replacement / Exit Evidence** | Evidence needed to retain owner accountability and recoverability when a provider or pattern changes or ends. It does not guarantee portability, support, or a migration mechanism. |

Every material interaction must preserve the following separate layers:

1. delivery or transport observation;
2. technical integrity or provenance;
3. representation or lineage;
4. domain acceptance; and
5. financial reconciliation or case consequence.

## 4. Provider-neutral interaction requirements

### 4.1 Core requirements

| ID | Requirement |
| --- | --- |
| `PNIC-01` | Start from accepted PayPlus owner rules. A provider observation or capability statement must not redefine product, financial, security, privacy, Evidence, risk, status, or lifecycle meaning. |
| `PNIC-02` | Classify each external signal as an External Observation, not as authoritative PayPlus truth. |
| `PNIC-03` | Do not automatically convert an External Observation into a Payment, Payout, Evidence acceptance, risk outcome, authorization, notification decision, case outcome, or privileged effect. |
| `PNIC-04` | Name the applicable owner evaluation and downstream owner handoff wherever an observation may be relevant to an authoritative outcome. |
| `PNIC-05` | Preserve uncertainty and the evidence limitation for duplicate, replayed, late, missing, stale, malformed, contradictory, unknown-origin, or unavailable observations. |
| `PNIC-06` | Require a provider-neutral interaction reference and correlation obligation sufficient for later owner investigation, recovery, reconciliation, and audit without defining a field, schema, event, or identifier format. |
| `PNIC-07` | Require provenance, integrity, completeness, and timing evidence appropriate to the interaction class without selecting transport, validation, signing, or security mechanisms. |
| `PNIC-08` | Duplicate or replayed external evidence must not create a second PayPlus notification decision, financial consequence, domain consequence or privileged effect. Provider delivery retry and delivery semantics remain owned by DOC-08. |
| `PNIC-09` | Preserve already-authoritative facts when uncertainty arises. An uncertain observation must not automatically resubmit work, reopen Checkout, or create a new Payment or Payment Application. |
| `PNIC-10` | Do not release Payout, apply a financial correction, resolve a case, or invoke a privileged action from an observation alone; the applicable owner rule and evaluation remain required. |
| `PNIC-11` | Treat normal, duplicate, replayed, late, missing, stale, malformed, contradictory, unknown, and unavailable observations as separately assessable conditions. Do not impose an unsupported hierarchy between callback, query, report, file, portal, return, delivery record, or alert. |
| `PNIC-12` | Require a durable, retryable, idempotent-at-the-receiving-owner-boundary, correlated, auditable, recoverable, reconcilable, and owner-routed handoff posture without selecting a retry model, idempotency-key model, timeout, persistence, or distributed-transaction mechanism. |

### 4.2 Candidate evidence, replacement, and handoff requirements

| ID | Requirement |
| --- | --- |
| `PNIC-13` | Keep external-action providers, external-observation providers, inbound data sources, outbound data consumers, bidirectional systems, and operational providers as pattern lenses, not provider selections, feature commitments, or architecture choices. |
| `PNIC-14` | Limit interaction information to the approved-purpose minimum required by the applicable owner. Protected values, raw PAN, card-verification values, secrets, credentials, OTPs, and unnecessary provider payloads must not be introduced into this contract. |
| `PNIC-15` | Record candidate-specific evidence, where used, with its source identity, version or date where available, locator, stated limitation, and affected-owner dependency. Missing or unclear evidence is an Evidence Gap. |
| `PNIC-16` | Preserve replacement and exit evidence for in-flight work, late observations, open cases, historical references, reconciliation, data access or portability consideration, credential withdrawal, coexistence or rollback questions, and post-termination support. |
| `PNIC-17` | Hand off required acceptance, monitoring, incident, support, change, maintenance, deprecation, and operational evidence to DOC-20 and DOC-21; DOC-22 may execute only an owner-permitted workflow. |
| `PNIC-18` | Where an external interaction concerns evidence, document verification, eKYC, or KYB, involve DOC-12 only for the applicable Evidence or document-verification concern. This does not transfer identity, risk, privacy, security, Payment, or authorization authority to DOC-12. |
| `PNIC-19` | For Bill/Rent-related interactions, DOC-17 must consume and must not weaken the applicable formal owner rules for Tier 2, Tier 3, Rent Evidence gating and G1 treatment. The product, payment, Evidence, risk and Payout owners retain their detailed definitions. |
| `PNIC-20` | Maintain Functional-Surface Coverage for the identified PayPlus functional families and apply the Extension Rule before treating a new or newly externalised capability as covered. Coverage does not approve a capability, provider, permission, route, status, schema, or implementation. |
| `PNIC-21` | Provider-neutrality makes replacement across provider, language and framework achievable only when later architecture, representation, security and implementation owners faithfully realise the accepted contract. DOC-17 neither selects nor defines those mechanisms. |
| `PNIC-22` | Treat an external authorized AI agent as a future Founder decision only. No AI actor, authority, data-sharing arrangement, or execution capability is created by this Draft. |

## 5. Interaction-pattern profiles

The profiles below organise the interaction contract. They do not require a provider, an interface, an API, or external connectivity.

| Profile | Contract focus | Required separation and handoff |
| --- | --- | --- |
| External Action Provider | A provider-neutral action request, response, query, failure, uncertainty, evidence, and exit obligation. | DOC-09, DOC-10, DOC-11, DOC-14, DOC-16, DOC-18, DOC-19, and DOC-20/21 as applicable. |
| External Observation Provider | Provenance, limitation, correlation, owner evaluation, and safe uncertainty for an observation. | The applicable domain owner; DOC-12 only where Evidence/document verification applies. |
| Inbound Data Source | Completeness, source authority, correlation, late delivery, replay, and exit evidence. | The receiving owner, DOC-18 representation, DOC-15 handling, and DOC-21 operations. |
| Outbound Data Consumer | Approved purpose, minimum data, consent or other owner-defined permission, delivery evidence, revocation, and exit evidence. | DOC-15 and the relevant functional owner; DOC-18 representation and DOC-21 operations. |
| Bidirectional System | Source-of-truth boundary, conflict visibility, version or compatibility evidence, reconciliation, and exit evidence. | Applicable owner, DOC-16/18/19, DOC-20/21, and professional owners as applicable. |
| Operational Provider | Observation, support, incident, change, maintenance, deprecation, migration, and exit evidence. | DOC-21; DOC-20 for acceptance evidence; DOC-22 only for owner-permitted execution. |

## 6. Functional-Surface Coverage and Extension Rule

### 6.1 Coverage rule

This matrix is a complete coverage classification for currently identified PayPlus functional families. It does not map every screen, control, or hypothetical feature to an external interface. Each row has exactly one current result:

- **No external interaction** — no external interaction is currently required by the accepted owner rule;
- **Conditional** — an external interaction may be relevant only when an owner-approved condition or later provider decision requires it;
- **Future Decision** — an interaction cannot be defined until a separate Founder decision; or
- **Required Coverage** — the functional family requires a provider-neutral interaction contract and evidence coverage, without asserting a provider or implementation exists.

| Functional surface | Owning source | Functional purpose | External interaction classification | Applicable pattern lens | Authoritative owner | Required external observation or action evidence | Current result |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `FSC-01` Payment and payer authorization | DOC-09 | Payment-facing obligation, Checkout, funding execution, Provider Confirmation, Payment, and Payment Application. | External action and confirmation observation | External Action Provider | DOC-09 | Interaction reference, provenance, uncertainty, and owner-evaluation handoff. | Required Coverage |
| `FSC-02` Settlement, Payout, and reconciliation | DOC-10 | Settlement evidence, Payout readiness, bank result ingestion, reconciliation, and exception handling. | Inbound bank or settlement observation | Inbound Data Source | DOC-10 / Finance where applicable | Source, period or batch context, completeness, correlation, replay, uncertainty, and reconciliation handoff. | Required Coverage |
| `FSC-03` Refund, reversal, dispute, and chargeback | DOC-11 | Case and financial-treatment lifecycle. | External case or financial observation | External Action Provider | DOC-11 | Case reference, provenance, uncertainty, and owner consequence handoff. | Required Coverage |
| `FSC-04` Bill/Rent and approved-payee source | DOC-05 / DOC-06C | Bill, rent, payee, and obligation source facts. | Inbound source observation | Inbound Data Source | Applicable product owner | Source provenance, limitation, correlation, and owner acceptance boundary. | Conditional |
| `FSC-05` Evidence, OCR, and document verification | DOC-12 | Applicable Evidence acquisition, extraction, verification, and Evidence-to-Payee work. | External observation provider | External Observation Provider | DOC-12 where applicable | Evidence provenance, limitation, correlation, and DOC-12 evaluation handoff. | Conditional |
| `FSC-06` eKYC, KYB, and identity-related verification | Applicable identity owner / DOC-12 where applicable | An owner-required identity or document-verification concern. | External observation provider | External Observation Provider | Applicable identity owner; DOC-12 only for applicable Evidence or document verification | Source limitation, approved-purpose boundary, and owner evaluation; no identity-proof or account-linking rule. | Conditional |
| `FSC-07` Risk and dynamic authorization | DOC-14 | Owner-controlled fraud, anti-cashout, AML, and dynamic-authorization input. | External observation or action | External Observation Provider | DOC-14 | Provenance, limitation, uncertainty, and risk-owner evaluation handoff. | Conditional |
| `FSC-08` Notification, receipt, and communication delivery | DOC-08 | Notification and receipt delivery under an owner-defined notification decision. | External action provider | External Action Provider | DOC-08 | Delivery attempt or result evidence distinct from the notification decision; `PNIC-08` applies. | Conditional |
| `FSC-09` Promotion, reward, referral, and partner fulfilment | DOC-13 | Owner-defined promotion, reward, referral, or partner-funded consequence. | Outbound consumer or bidirectional system | Outbound Data Consumer | DOC-13 | Approved-purpose, provenance, limitation, and owner consequence handoff. | Conditional |
| `FSC-10` Payee or partner data exchange | DOC-05 / DOC-12 / DOC-15 | Potential source, partner, or payee data exchange. | Inbound source or bidirectional system | Bidirectional System | Applicable product owner and DOC-15 | Source authority, purpose, limitation, conflict, and owner acceptance boundary. | Conditional |
| `FSC-11` Accounting, ERP, tax, and finance exchange | DOC-10 / Finance | Potential accounting, reporting, or finance information exchange. | Inbound source, outbound consumer, or bidirectional system | Bidirectional System | DOC-10 / Finance | Purpose, source, period, correlation, reconciliation, and exit evidence. | Conditional |
| `FSC-12` Regulatory or reporting export | Compliance / Finance / DOC-15 | Potential owner-approved reporting or export. | Outbound data consumer | Outbound Data Consumer | Applicable professional owner and DOC-15 | Approved purpose, permitted data, delivery evidence, retention, and revocation or exit handoff. | Conditional |
| `FSC-13` Operations, support, and incident observation | DOC-21 | Monitoring, support, incident, escalation, and closure evidence. | Operational provider | Operational Provider | DOC-21 | Observation, correlation, limitation, escalation, change, and support evidence. | Conditional |
| `FSC-14` Owner-permitted Admin execution | DOC-22 | Execution of an already owner-permitted workflow. | No independent external interaction | Operational Provider | DOC-22 under the applicable owner | Owner authorization and audit handoff only; no policy or external capability is supplied by this row. | No external interaction |
| `FSC-15` Privacy, data-subject, vendor, and termination treatment | DOC-15 | Approved-purpose handling, vendor treatment, data access, retention, and termination concern. | Outbound data consumer or operational provider | Outbound Data Consumer | DOC-15 | Minimum-necessary transfer, approved-purpose, masking, retention, vendor, and exit evidence. | Conditional |
| `FSC-16` Security and protected-value boundary | DOC-19 | Mechanism-neutral protection and verification requirements. | No independent external interaction | External Action Provider | DOC-19 | Security-owner handoff and prohibited-value boundary; no mechanism, secret, credential, or protocol. | No external interaction |
| `FSC-17` Provider replacement and exit | DOC-15 / DOC-16 / DOC-21 | Continuity of evidence and owner routing across provider change or termination. | Operational provider or bidirectional system | Operational Provider | Applicable owner with DOC-15, DOC-16, and DOC-21 | `PNIC-16` exit evidence for in-flight, historical, reconciliation, access, and support concerns. | Required Coverage |
| `FSC-18` External authorized AI-agent interaction | Founder decision | Potential future authorized-agent capability. | Future provider-neutral interaction | External Action Provider | Founder and future owners | A future decision package defining actor, authority, data access, consent, revocation, risk, and stop/review authority. | Future Decision |
| `FSC-19` Engineering tooling, SDK, and build support | Engineering | Later evaluation of maintainability, compatibility, lifecycle, testability, and deployment criteria. | No product external interaction | Operational Provider | Engineering | Evaluation criteria and owner evidence only; no language, framework, SDK, provider, or implementation selection. | No external interaction |

### 6.2 Extension Rule

A future or newly externalised capability must enter this matrix through one new row before it is treated as covered by DOC-17. The row must identify the owning source, purpose, interaction classification, applicable pattern lens, authoritative owner, evidence obligation, and exactly one current result. The addition itself does not approve a capability, provider, integration, permission, route, status, architecture, schema, or implementation.

If the new row requires a material product, ownership, risk, privacy, security, commercial, or architecture decision, it must return through the applicable owner and the Documentation Development Workflow before DOC-17 is changed.

## 7. External observations, uncertainty, and owner evaluation

External observations may be received through a callback, query, report, file, portal, browser return, delivery record, alert, or manual upload. No channel is presumed more authoritative than another. The applicable owner evaluates the observation under its existing rule; DOC-17 records only the contract expectation that the observation, its provenance, its limitation, and its correlation be available for that evaluation.

| Condition | DOC-17 contract obligation | Prohibited automatic effect |
| --- | --- | --- |
| Duplicate or replayed evidence | Preserve the observation and correlation evidence; prevent a second PayPlus decision or consequence. | A second notification decision, financial consequence, domain consequence, privileged effect, Payment, Payout, or case effect. |
| Late, stale, missing, unknown, or unavailable evidence | Preserve uncertainty and make an owner-routed recovery, reconciliation, support, or escalation handoff possible. | Assumed success or failure, automatic resubmission, reopening of Checkout, or automatic Payment/Application creation. |
| Malformed, contradictory, or unknown-origin evidence | Preserve the limitation and route for owner/security evaluation under applicable rules. | Treating the observation as trusted truth, releasing Payout, changing a case, or invoking a privileged action. |
| Incomplete bank or settlement report | Preserve source, period, count, correlation, and completeness limitation for reconciliation. | Declaring Settlement, Payout, or reconciliation accepted. |

The following boundary remains exact: duplicate or replayed external evidence must not create a second PayPlus notification decision, financial consequence, domain consequence or privileged effect. Provider delivery retry and delivery semantics remain owned by DOC-08.

## 8. Bill/Rent, Evidence, Payment, and Payout consumption boundary

For Bill/Rent-related interactions, DOC-17 must consume and must not weaken the applicable formal owner rules for Tier 2, Tier 3, Rent Evidence gating and G1 treatment. The product, payment, Evidence, risk and Payout owners retain their detailed definitions.

Accordingly, this contract does not restate or alter the following owner-defined boundaries:

- Tier 2 qualifying Evidence presence may permit Payment while Evidence acceptance remains a DOC-10 Payout gate;
- Tier 3 requires qualifying Evidence and authorized approval before first Provider Submission;
- Rent requires accepted attached Evidence before Payment; and
- G1 is a product-semantic Bill progression tied to the receiving account or authoritative payout destination, not a provider event, status, schema, or signal.

DOC-17 may require correlation, provenance, uncertainty, and an owner handoff for an applicable Bill/Rent interaction. It cannot make a candidate provider or its observation a substitute for evidence, payer authorization, Payment, Payment Application, Payout readiness, risk outcome, or payee truth.

## 9. Candidate evidence and generic-contract boundary

Candidate-specific documented facts, limitations, and Evidence Gaps may inform a later candidate feasibility assessment. They must be kept separate from the generic contract.

Candidate-specific gaps do not block generic DOC-17 drafting or review while this document remains provider-neutral and makes no unsupported provider-specific assertion. They continue to block candidate-specific feasibility, recommendation, selection, mapping, implementation, testing, acceptance, enablement, assurance, and launch conclusions.

No candidate identity, capability, entitlement, account, environment, callback reliability, commercial term, PCI position, privacy position, support commitment, or provider readiness is asserted by this Draft.

## 10. Replacement, exit, and technical-realisation handoffs

### 10.1 Replacement and exit evidence

Where a provider or interaction pattern may change or end, the later evidence universe must address, as applicable:

- in-flight work and late observations;
- open cases and historical references;
- reconciliation and finance-owner continuity;
- approved-purpose data access, portability consideration, retention, and termination treatment;
- credential withdrawal and protected-value separation;
- coexistence, rollback, or recovery questions; and
- post-termination monitoring, support, incident, and escalation evidence.

This is an evidence obligation, not a promise that a provider supports portability, termination, coexistence, rollback, or support in any particular way.

### 10.2 Technical-realisation boundary

| Concern | Owner and future handoff |
| --- | --- |
| Provider-neutral contract, evidence obligation, and owner handoff | DOC-17 |
| Architecture, trust boundary, reliability, durable handoff, recovery, and reconciliation posture | DOC-16 |
| Data, correlation, event, audit, and lineage representation | DOC-18 |
| Protected values, access enforcement, secure boundary, and security verification | DOC-19 |
| Positive, negative, exception, and regression acceptance evidence | DOC-20 |
| Monitoring, incident, support, change, and escalation evidence | DOC-21 |
| Owner-permitted execution workflow | DOC-22 |
| Later mapping to a selected provider and internal Engineering realisation | Future Engineering work under separately accepted owner decisions |

Provider-neutrality makes replacement across provider, language and framework achievable only when later architecture, representation, security and implementation owners faithfully realise the accepted contract. DOC-17 neither selects nor defines those mechanisms.

## 11. Open, deferred, and professional-owner gates

The following are intentionally open or deferred. They do not block faithful expression of this generic contract, but they block the relevant later provider-specific, professional, implementation, acceptance, enablement, or launch work.

| Matter | Owner or required return | Status |
| --- | --- | --- |
| Formal named reviewers and approvers for DOC-17 | Founder / Documentation Owner | TBD |
| Provider, PSP, acquirer, bank, accounting, partner, or commercial selection | Founder and relevant professional owners | Deferred |
| Provider capabilities, entitlement, account, region, channel, currency, scheme, and environment evidence | Candidate-specific feasibility owner | Evidence Gap / later gate |
| API, file, callback, report, portal, payload, schema, event, status, correlation, credential, and environment detail | DOC-17, DOC-18, DOC-19, and Engineering after required decisions | Deferred |
| Security mechanism, PCI scope, shared responsibility, legal, privacy, DPA, cross-border, and vendor determination | Security, Compliance, Privacy, Legal, and professional owners | Deferred professional gate |
| Accounting, reserve, settlement, matching, and reconciliation policy | Finance and DOC-10 | Deferred |
| Acceptance, UAT, monitoring, incident, support, operations, and Admin permissions | DOC-20, DOC-21, DOC-22, and applicable owners | Deferred evidence gate |
| External authorized AI-agent capability | Founder and future owners | Future Decision |

## 12. Decision coverage and acceptance criteria

| Approved decision or correction | Draft representation | Acceptance coverage |
| --- | --- | --- |
| `DOC17-FD-01` | Sections 1-6 establish one provider-neutral contract, pattern lenses, evidence method, and Functional-Surface Coverage. | `D17-AC-01` |
| `DOC17-FD-02` and `CORR-02` | Sections 2-4, 7, and 8 preserve External Observation separation and the exact Bill/Rent consume-and-must-not-weaken boundary. | `D17-AC-02` |
| `DOC17-FD-03` and `CORR-04` | Section 6 provides the eight-column, 19-row Functional-Surface matrix, four exclusive results, and Extension Rule. | `D17-AC-03` |
| `DOC17-FD-04` and `CORR-03` | Sections 1, 4, 6, and 9 preserve candidate separation and qualified DOC-12 participation. | `D17-AC-04` |
| `DOC17-FD-05` and `CORR-01` | Sections 4 and 7 preserve uncertainty, duplicate-effect prevention, and the exact DOC-08 delivery-retry boundary. | `D17-AC-05` |
| `DOC17-FD-06` and `CORR-05` | Section 10 requires replacement and exit evidence and separates DOC-17 from DOC-16, DOC-18, DOC-19, and later Engineering realisation. | `D17-AC-06` |
| `DOC17-FD-07` | Metadata and Sections 1-2 preserve Engineering / Integration ownership and the primary-owner boundary. | `D17-AC-07` |
| `DOC17-FD-08` and `CORR-06` | Sections 4, 6, 10, 11, and 12 preserve AI deferral, technical non-decisions, and decision traceability without recreating a Founder choice. | `D17-AC-08` |

| Acceptance ID | Criterion |
| --- | --- |
| `D17-AC-01` | One coherent DOC-17 Draft defines the approved provider-neutral contract, its evidence method, interaction profiles, Functional-Surface Coverage, and exclusions without competing contract artifacts. |
| `D17-AC-02` | External observations cannot become domain or financial truth without the applicable owner evaluation; Bill/Rent definitions remain with their formal owners. |
| `D17-AC-03` | Every Functional-Surface row has all eight required fields and exactly one permitted current result; the Extension Rule prevents silent enablement or architecture creation. |
| `D17-AC-04` | Candidate gaps do not block generic Drafting, no unsupported provider fact is asserted, and DOC-12 participation remains limited to applicable Evidence or document-verification work. |
| `D17-AC-05` | Duplicate, replayed, late, missing, stale, malformed, contradictory, unknown, and unavailable observations preserve facts and do not authorize unsafe continuation; DOC-08 retains provider delivery retry and delivery semantics. |
| `D17-AC-06` | Replacement and exit coverage includes open work, historical, reconciliation, data-treatment, protected-value, and support evidence while technical owners remain distinct and no mechanism is selected. |
| `D17-AC-07` | Metadata and Document Control are exact mirrors, Engineering / Integration remains the primary owner for this contract, and owner handoffs do not duplicate or redefine protected source rules. |
| `D17-AC-08` | AI, provider, mechanism, implementation, assurance, enablement, and launch non-decisions remain visible; no readiness claim is introduced, and `DOC17-FD-01` through `DOC17-FD-08` plus `CORR-01` through `CORR-06` are accurately mapped to Draft representation and acceptance coverage. |

## 13. Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| `0.1.0` | `2026-08-25` | Engineering / Integration | Initial Draft of the approved provider-neutral External Interaction Contract, including settled correction and traceability coverage; no provider selection or implementation detail. |
