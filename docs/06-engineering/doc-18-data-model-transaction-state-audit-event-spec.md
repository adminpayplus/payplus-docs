---
document_id: DOC-18
title: Data Model, Transaction State, Audit Event & Reporting Specification
version: 2.0.0
status: Draft
owner: Engineering / Data
reviewers:
  - Product Lead
  - Engineering Lead
  - Data Lead
  - Privacy Lead
  - Security Lead
  - Risk Lead
  - Operations Lead
approvers:
  - Project Owner
  - Engineering Lead
  - Data Lead
last_updated: 2026-08-27
classification: Internal
related_documents:
  - DOC-00 Documentation Governance
  - DOC-01 Project Charter & Product Positioning
  - DOC-05 Master PRD & Feature Requirement Index
  - DOC-06B Navigation, IA & Route Taxonomy
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
  - DOC-17 API & Third-party Integration Specification
  - DOC-19 Security, Tokenization, Authentication & Admin Control Specification
  - DOC-20 Testing, UAT & Go-Live Checklist
  - DOC-21 Monitoring, Incident Response & Operational SOPs
  - DOC-22 Admin Management Dashboard & Operations Workflow
---

# DOC-18 - Data Model, Transaction State, Audit Event & Reporting Specification

| Document Control | Details |
| --- | --- |
| **Document ID** | `DOC-18` |
| **Title** | Data Model, Transaction State, Audit Event & Reporting Specification |
| **Version** | `2.0.0` |
| **Status** | Draft |
| **Owner** | Engineering / Data |
| **Reviewers** | Product Lead<br>Engineering Lead<br>Data Lead<br>Privacy Lead<br>Security Lead<br>Risk Lead<br>Operations Lead |
| **Approvers** | Project Owner<br>Engineering Lead<br>Data Lead |
| **Last Updated** | `2026-08-27` |
| **Classification** | Internal |
| **Related Documents** | DOC-00 Documentation Governance<br>DOC-01 Project Charter & Product Positioning<br>DOC-05 Master PRD & Feature Requirement Index<br>DOC-06B Navigation, IA & Route Taxonomy<br>DOC-06C Bills, Rent & Tenancy UX Module<br>DOC-07 Content, Disclosure & User Authorization Specification<br>DOC-08 Notification, Receipt & Communication Specification<br>DOC-09 Payment Domain Architecture<br>DOC-10 Payout & Reconciliation<br>DOC-11 Refund, Cancellation & Chargeback<br>DOC-12 Bill Category, Document AI/OCR & Payee Verification Specification<br>DOC-13 Promotion Engine, Coupon, Voucher, Referral & Membership Specification<br>DOC-14 AML, Anti-Cashout, Fraud, Dynamic Auth & Risk Control Specification<br>DOC-15 Privacy, Data Protection & Record Retention Specification<br>DOC-16 Technical Architecture Specification<br>DOC-17 API & Third-party Integration Specification<br>DOC-19 Security, Tokenization, Authentication & Admin Control Specification<br>DOC-20 Testing, UAT & Go-Live Checklist<br>DOC-21 Monitoring, Incident Response & Operational SOPs<br>DOC-22 Admin Management Dashboard & Operations Workflow |

> **Draft boundary.** This Draft defines business-recording, explainability, history, lineage, and owner-handoff requirements. It is not an Approved source of truth and does not approve a physical or logical schema, event or status taxonomy, timestamp or versioning convention, cardinality, identifier, API, payload, service, persistence product, queue, job, provider, security mechanism, backend design, implementation, acceptance result, enablement, production operation, or launch readiness.

## 1. Purpose, mission, authority, ownership, and non-decisions

DOC-18 is PayPlus's detailed business-recording rulebook. It defines what PayPlus must be able to remember, distinguish, relate, reconstruct, and explain about material business facts and actions, while the applicable product, domain, privacy, security, risk, operations, and acceptance owners retain authority over what those facts mean and what consequences they permit.

DOC-18 owns the business-level recording and explainability contract for:

- provenance and lineage between a supplied fact, processing result, owner assessment, effective business fact, and later consequence;
- relationships between material record families without making Bill or Rent a universal parent;
- distinct business-time meanings and the historical basis for an action or decision;
- current authoritative facts, material change, supersession, and non-rewriting history;
- representation of owner-defined state, outcome, projection, communication, access, retention, and audit meanings without merging them;
- governed reporting, analytics, model-use, and partner-reporting boundaries; and
- safe handoff of implementation-facing discoveries to the correct later owner and lifecycle stage.

DOC-18 does not own Bill, Rent, Declaration, Evidence, Payment, payer authorization, Payment Application, Payout, reconciliation, case, adjustment, promotion, risk, privacy, security, notification, route, Admin, acceptance, monitoring, or support policy. It consumes those meanings from their owners and records the minimum relationships needed to preserve them.

The following are explicit non-decisions:

- no technical representation or implementation choice is made;
- no new route, user-facing label, cross-domain status, product capability, domain entity, or owner is created;
- no external capability, operating effectiveness, compliance conclusion, or readiness claim is established;
- no exact Admin retrieval interface, search, permission, workflow, raw-access, export, queue, or maker-checker treatment is designed; and
- the working label `Engineering Specification` remains only a future documentation-architecture Explore input. DOC-18 does not assign its owner, document number, family, structure, or technical content.

## 2. Inherited owner contracts and controlled terminology

### 2.1 Owner contracts

| Concern | Primary owner | DOC-18 recording responsibility |
| --- | --- | --- |
| Product identity, Bill and Rent scope, controlled Category policy, materiality, Save and Archive meaning | DOC-05 and DOC-06C | Preserve the authoritative source identity, current fact, prior material history, provenance, projections, and owner references without redefining product or UX behavior. |
| Declaration, disclosure, Outcome, Resolution, Message and CTA meaning | DOC-07 and the applicable domain owner | Preserve the occurrence context, relied-upon facts, owner authority, and linkage without defining wording or presentation. |
| Notification, Receipt and communication meaning | DOC-08 | Keep communication identity, delivery, and presentation separate from the owning business fact and consequence. |
| Payment, Checkout, payer authorization, confirmed Payment and Payment Application | DOC-09 | Preserve distinct historical financial facts and the basis and relationships supplied by DOC-09 without creating Payment truth. |
| Destination, Settlement, Payout and reconciliation | DOC-10 | Preserve owner-defined Payout history, destination context, reconciliation evidence, and separation from Payment history. |
| Refund, cancellation, dispute, chargeback, reversal, adjustment and case handling | DOC-11 | Preserve owner-defined case and adjustment history without rewriting the financial facts to which it relates. |
| Evidence, extraction, correction, verification and Evidence-to-Payee meaning | DOC-12 | Preserve the required Evidence separations, provenance, material history, and owner assessment. |
| Promotion, offer, referral, membership, entitlement, reward and fulfilment meaning | DOC-13 | Preserve owner-defined relationships, history, and permitted reporting lineage without redefining commercial rules. |
| Risk, fraud, sanctions, anti-cashout, review and control outcomes | DOC-14 | Preserve the distinction between input, owner assessment, action, outcome, and later consequence without defining policy or thresholds. |
| Classification, purpose, masking, visibility, access, retention and lawful handling | DOC-15 | Consume owner-approved treatment and keep it separate from current effectiveness, actionability, and presentation. |
| Architecture boundaries, authoritative ownership, durable handoffs, recovery, reconciliation and observability | DOC-16 | Preserve the required business distinction between local owner truth and cross-boundary evidence without selecting technical design. |
| External interaction contract and observation provenance | DOC-17 | Preserve external information as non-authoritative until the applicable owner evaluates it. |
| Authentication, protected-value and access-enforcement controls | DOC-19 | Record only permitted references and safe business/audit facts; do not expose protected values or choose a control mechanism. |
| Testing, UAT and release evidence | DOC-20 | Provide traceable requirements for later acceptance evidence without asserting that evidence exists. |
| Monitoring, incident, support and operational escalation | DOC-21 | Preserve later evidence and historical reconstruction needs without defining operating procedures or claiming effectiveness. |
| Owner-permitted Admin execution | DOC-22 | Preserve the owner-authorized action and its business basis without granting generic Admin authority or defining execution design. |

### 2.2 Controlled terminology

The terms below are business-recording meanings, not technical structures:

| Term | Meaning |
| --- | --- |
| **Source Fact** | Information supplied by a user, an accepted document, an owner, or another permitted source, with its provenance and limitations preserved. |
| **Processing or Extraction Result** | A candidate interpretation or transformation of source information that has not become owner truth merely because processing occurred. |
| **Owner Assessment or Decision** | The applicable owner's evaluation under its accepted rules. |
| **Effective PayPlus Business Fact** | The fact the applicable owner recognizes as current or historically effective for its own purpose. |
| **External Observation** | Information received from outside the authoritative PayPlus owner boundary; it remains non-authoritative until owner evaluation. |
| **Downstream Consequence** | An action, decision, restriction, financial fact, case, presentation, or other result governed by its own owner. |
| **Current Effectiveness** | Whether an owner currently treats a fact as effective for a defined purpose. It is not generic readiness. |
| **Historical Action Basis** | The facts, owner decisions, and context that supported an action or consequence when it occurred. |
| **Material Change** | A change that an owner treats as capable of altering reliance, reconfirmation, evaluation, or consequence. |
| **Supersession** | Replacement of a fact's current effectiveness for a defined purpose while preserving the prior fact and its historical effects. |
| **Presentation Projection** | An owner-permitted view of current or historical meaning; it is not automatically the authoritative fact. |
| **Owner-permitted History Retrieval** | The business outcome that authorized people can retrieve the history needed for an owner-approved purpose, subject to access, masking, retention, and operational controls. |

## 3. Common business-recording and minimum-explainability contract

### 3.1 Required semantic separation

Where the meanings differ, PayPlus must preserve this separation:

```text
Source Fact
-> Processing or Extraction Result
-> Owner Assessment or Decision
-> Effective PayPlus Business Fact
-> Downstream Consequence
```

This is an explainability relationship, not a universal processing sequence. A family may omit a step that does not apply, but it must not collapse two distinct meanings merely for convenience. Processing does not create owner acceptance. Owner acceptance does not create a Payment, payer authorization, Payout, or other separately owned consequence. A consequence does not rewrite the source, assessment, or fact on which it was based.

### 3.2 Minimum Explainability Lens

For every applicable material record family, PayPlus must be able to answer the following business questions:

| Explainability question | Required answer |
| --- | --- |
| Subject and relationship | What is the record about, and how does it relate to its source, applicable business relationship, owner fact, and later action? |
| Source and provenance | Who or what supplied the information, what kind of source it was, and what limitations or uncertainty accompanied it? |
| Actor and authority | Who supplied, changed, processed, assessed, decided, or acted, and which owner determined current effectiveness? |
| Relevant business time | Which source-stated, received, processed, assessed, effective, submitted, confirmed, applied, consequence, expiry, or other business-time meaning matters? |
| Assessment and effectiveness | What was assessed, which owner rule applied, and what became effective for that owner's defined purpose? |
| Change and uncertainty | Was information corrected, supplemented, replaced, contradicted, withdrawn, reprocessed, or left uncertain? |
| Historical action basis | Which then-effective facts and decisions supported a prior action or consequence? |
| Supersession | What is current now, what ceased to be current, and what historical meaning remains preserved? |
| Owner-controlled use | Who may decide actionability, presentation, access, retention, reporting, or another consequence? |

No single record or label needs to answer every question by itself. The linked business history must answer them without inference from a generic status or from technical implementation behavior.

### 3.3 Recording-quality rules

1. Provenance follows a fact through correction, owner assessment, effectiveness, consequence, reporting, and permitted derived use.
2. A correction adds or supersedes meaning; it does not erase the original source or silently alter an established historical action basis.
3. Uncertainty, contradiction, late arrival, duplication, and absence remain visible until the applicable owner resolves their significance.
4. The same word must not be used to imply source presence, owner acceptance, actionability, authorization, financial confirmation, and completion when those meanings differ.
5. Current effectiveness, actionability, presentation, access, retention, and historical retrieval are separate owner-governed questions.
6. A historical record remains historical even when it is no longer effective, actionable, displayable, accessible, or retained for every purpose.
7. Recording an owner decision or action does not prove implementation or operating effectiveness.

## 4. Complete record-family coverage

### 4.1 Coverage method

Every material family below must satisfy the applicable Minimum Explainability Lens and identify its primary owner. The table defines recording coverage, not a technical object catalogue, new product scope, or permission to infer missing owner rules.

| Record family | Minimum business-recording coverage | Source-truth owner | Required handoffs |
| --- | --- | --- | --- |
| Account and product-account context | Account and actor context, owner-defined account meaning, material account-change history, and permitted consequence relationships | DOC-05 | DOC-06B/15/19/21/22 |
| Identity, authentication and account-control outcome context | Owner-defined identity or authentication outcome, protected-value boundary, current-versus-historical meaning, and permitted consequence relationships | DOC-06B for product and route-level outcome meaning | DOC-07/15/19/21/22 |
| Bill source | Same authoritative Bill identity, controlled Category, declared purpose and amount, economic Payee, Payee bank name, bank code, bank account number, applicable due or period facts, source provenance, Declaration context, material-change history, and Save/Archive/history-only projection relationships | DOC-05 | DOC-06C/07/09/10/12/14/15 |
| Rent source and tenancy context | Separate Rent identity and relationship context, Rent Amount and period, Payee/landlord, Payee bank name, bank code, bank account number, stated payout method, optional landlord contact where owner-permitted, tenant context where the Payer pays for another person, mandatory Evidence relationship, and material-change history | DOC-05 | DOC-06C/09/10/12/14/15 |
| Evidence | Supplied source, processing/extraction and user correction, owner assessment, accepted or unresolved Evidence meaning, provenance, replacement/supplement history, and separately owned consequences | DOC-12 | DOC-05/06C/09/10/14/15 |
| Payee acquisition and source context | Acquisition provenance, intended economic Payee, owner-defined relationship context, and separation from destination, risk, Payment and Payout meanings | DOC-05 | DOC-06C/09/10/12/14/15 |
| Effective destination and destination history | Owner-approved destination fact, applicable historical basis, and separation from source, economic-Payee, Payment and Payout meaning | DOC-10 | DOC-05/09/12/14/15/22 |
| Payment | Payable Basis and obligation context, payer authorization basis, confirmed Payment, Payment Application, later adjustment linkage, and immutable historical financial meaning | DOC-09 | DOC-07/10/11/14/17/20/21 |
| Deliberate Payment Instruction | Owner-defined instruction intent, applicable obligation and action context, and history that remains separate from ordinary reminders and an incomplete Checkout Workspace | DOC-09 | DOC-06B/07/08/18 |
| Ordinary Bill/Rent reminder | Owner-defined reminder purpose, source or obligation context, timing relevance, communication relationship, and history that remains separate from a Payment Instruction action alert | DOC-06C | DOC-08/15/18/21 |
| Payout and reconciliation | Owner-defined destination basis, Payout progression and outcome, hold or exception context, reconciliation result, and relationship to but separation from Payment history | DOC-10 | DOC-09/11/14/21 |
| Refund, cancellation, dispute, chargeback, reversal, adjustment and support case | Owner-defined case, decision, effective financial adjustment, historical basis, and linkage without mutating prior Payment or Payout facts | DOC-11 | DOC-09/10/21 |
| Risk, fraud, sanctions and review | Input provenance, owner assessment, applied action, review or override authority, outcome, and separately owned consequence | DOC-14 | DOC-15/19/21/22 |
| Promotion, offer, referral, membership, entitlement, reward and fulfilment | Owner-defined eligibility and relationship context, benefit or entitlement history, participant role where applicable, fulfilment or reversal meaning, and permitted audit/reporting lineage | DOC-13 | DOC-09/11/14/15/22 |
| Notification, Receipt and communication | Source business context, recipient and purpose as owner-permitted, approved communication identity, presentation and delivery history, and separation from owning-domain truth | DOC-08 | DOC-07 and the applicable domain owner |
| Privacy request and protected access | Owner-defined request or action history, approved purpose, authority, current handling, historical preservation, and permitted operational handoff | DOC-15 | DOC-19/21/22 |
| Account closure product context | Owner-defined closure request, blocker, cancellation or final outcome and its non-rewriting historical relationships | DOC-05 | DOC-06B/15/19/21/22 |
| Admin and operational action | Applicable owner permission, facts relied upon, actor authority, action, reason or qualification, result, and historical traceability without generic Admin policy | One applicable domain owner, named for the action | DOC-15/19/21/22 |
| Audit, lineage, reporting and analytics representation | Source lineage, purpose, ownership, sensitivity, permitted use, aggregation or disclosure boundary, qualification, and relationship to owner truth | DOC-18 | Applicable domain owner plus DOC-13/14/15/16/19/20/21 |
| AI/model-assisted use context | Owner-approved purpose, input and outcome relationships, human-review or explanation obligations, and qualified derived-use lineage | One applicable use-case domain owner, named before use | DOC-14/15/18/19/20/21 and professional owners |
| Partner-reporting context | Owner-approved commercial or domain purpose, permitted aggregation or disclosure, recipient qualification, and lineage to source truth | One applicable commercial or domain owner, named for the report | DOC-13/15/18/19 and applicable legal/risk owners |

Two existing boundaries are mandatory across these rows. An ordinary Bill/Rent reminder is not a Payment Instruction action alert. A deliberate Payment Instruction is not an incomplete Checkout Workspace. A Notification may communicate an owner-defined reminder, instruction action, or Checkout condition, but it does not create that fact, authorize Payment, or collapse their separate histories.

### 4.2 Positive Bill and Rent recording coverage

This table is the positive coverage record for the complete settled Bill/Rent fact, materiality, Declaration, change-history, and historical-action-basis universe applicable to this Draft. Each DOC-18 obligation states what PayPlus must remember and explain. Where a settled materiality classification exists, the obligation states it explicitly; optional or unclassified facts remain separately identified without inferred materiality. The table does not approve fields, schemas, cardinality, events, payloads, identifiers, persistence, or implementation.

| Business fact / rule | Source authority | DOC-18 obligation |
| --- | --- | --- |
| Authoritative Bill/Rent identity and projection boundary | DOC-01; DOC-05; DOC-06B; DOC-06C; DOC-09; DOC-15 | PayPlus must remember and explain the same authoritative Bill/Rent identity across Saved/current, Saved/Archived, history-only, established-but-unprojected, no-Save, and permitted post-Payment Save treatment without allowing a projection change to rewrite source, financial, case, or audit history. |
| Category-bound Bill acquisition and acquisition provenance | DOC-01; DOC-05; DOC-06C; DOC-12 | PayPlus must remember and explain whether the Bill Payee context was acquired through the Category-scoped Directory or `Provide Payee myself`, the selected controlled Category, and the acquisition provenance without treating either method as current eligibility, Evidence, destination, risk, Payment, Payout, or authorization truth. |
| Bill source, biller reference, and due/period context | DOC-05; DOC-06C; DOC-09; DOC-12 | PayPlus must remember and explain the applicable Bill source or biller reference, due or period context, provenance, relationship to the authoritative Bill, and the then-effective context relied upon for later owner assessment or action. |
| Bill Category | Direct Founder correction authority; DOC-05; DOC-06C; DOC-12 | PayPlus must remember and explain Category as a material and amendable Bill fact, the current controlled Category, its source and authority, and its relationship to the same authoritative Bill identity. |
| Bill date | Direct Founder correction authority; DOC-05; DOC-06C; DOC-12 | PayPlus must remember and explain Bill Date as a material Bill fact, its provenance, the applicable business-time meaning, and any later material change. |
| Bill declared purpose | DOC-05; DOC-06C; DOC-07; DOC-09; DOC-12 | PayPlus must remember and explain declared purpose as a material Bill fact, its provenance, the applicable Declaration or reconfirmation context, and the owner treatment applied when that purpose changes. |
| Bill economic Payee | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12 | PayPlus must remember and explain economic Payee as a material Bill fact and the context relied upon without inferring PayPlus membership, reciprocal relationship, destination truth, or authorization. |
| Bill amount | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12 | PayPlus must remember and explain Bill Amount as a material Bill fact and its applicable purpose or period, separately from any individual Payment Amount, applied amount, paid-out amount, or outstanding amount. |
| Bill date and amount non-reusability | DOC-05; DOC-06C; DOC-09 | PayPlus must remember and explain that a prior Bill date and Bill amount are not reusable as current facts for a later Bill context, while other owner-permitted stable context may only be prefilled and remains subject to current Declaration, Tier, destination, risk, and authorization rules. |
| Bill Payee bank name | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain Payee bank name as a material Bill fact and its provenance, subject to DOC-15 privacy/access/masking/retention treatment and DOC-10 destination/Payout authority. |
| Bill Payee bank code | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain Payee bank code as a material Bill fact and its provenance without treating that fact as economic-Payee, destination, Payment, or Payout truth by itself. |
| Bill Payee bank account number | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain Payee bank account number as a material Bill fact and its provenance, subject to DOC-15 privacy/access/masking/retention treatment and DOC-10 effective destination, Payout, and reconciliation authority. |
| Bill remark | Direct Founder correction authority; DOC-05/06C owner boundary | PayPlus must remember and explain a supplied remark and its provenance while treating it as normally non-material unless an applicable owner rule expressly makes it material for a defined purpose. |
| Bill materiality | Direct Founder correction authority; DOC-05; DOC-06C; DOC-07; DOC-09; DOC-10; DOC-12 | PayPlus must remember and explain that Category, Bill date, declared purpose, economic Payee, Bill amount, Payee bank name, bank code, and bank account number are material facts, while a remark is normally non-material, together with the owner treatment applied to any change. |
| C1/G1/G2 trigger reason and highest-tier evaluation | DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12; DOC-14 | PayPlus must remember and explain which owner-defined C1, G1, or G2 trigger reason applied, the applicable highest-tier result, the facts and owner authority used, and the historical evaluation basis without defining values or technical treatment. |
| Bill Tier 1/2/3 recording | DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12; DOC-14 | PayPlus must remember and explain the owner-defined Tier 1, Tier 2, or Tier 3 treatment, applicable Declaration, Evidence-presence, Evidence-acceptance, approval, Payment, and Payout relationships, and the then-effective basis without turning Tier into generic readiness. |
| Bill Evidence presence, acceptance, and financial consequence separation | DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12; DOC-14 | PayPlus must remember and explain Evidence presence separately from processing and owner acceptance, and each separately from Payment admission, payer authorization, confirmed Payment, Payout hold or release, reconciliation, and other owner consequences. |
| Payment, Payment Application, Payout, and reconciliation history | DOC-09; DOC-10; DOC-11; DOC-14 | PayPlus must remember and explain immutable confirmed Payment and Payment Application facts separately from Payout, reconciliation, refund, reversal, adjustment, case, Evidence, and risk history, including which owner governed each later consequence. |
| Category amendment | `FD-DOC18-03`; DOC-05/06C/09/10/12/14/15 owner boundaries | PayPlus must remember and explain Category amendment as a material amendment on the same Bill identity, the current authoritative Category, every prior Category retained in material history, and that PayPlus does not infer or distinguish why the user changed it. |
| Category historical and downstream boundary | `FD-DOC18-02/03`; DOC-09; DOC-10; DOC-11; DOC-12; DOC-14 | PayPlus must remember and explain that a Category amendment does not rewrite historical Payment, Payment Application, Payout, reconciliation, case, adjustment, Evidence, risk, or audit facts, and that every downstream consequence remains governed by its owner. |
| Rent is separate from Bill tiers and retains mandatory accepted Evidence | DOC-01; DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12; DOC-14 | PayPlus must remember and explain that Rent is not a Bill Category, does not use C1/G1/G2 or Tier 1/2/3, and requires attached Evidence and the owner-defined accepted outcome before Payment; a Declaration cannot replace, waive, reduce, or defer that requirement. |
| Rent address | Direct Founder correction authority; DOC-05; DOC-06C; DOC-12; DOC-15 | PayPlus must remember and explain address as a material Rent fact, its provenance, applicable relationship, and any later material change without defining display or access treatment. |
| Rent period | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12 | PayPlus must remember and explain period as a material Rent fact and its relationship to the Rent source, obligation context, Rent Amount, Due Day, and historical action basis. |
| Rent Amount | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12 | PayPlus must remember and explain Rent Amount as a material Rent fact for the applicable period, distinct from each individual Payment Amount and later financial consequence. |
| Rent Due Day | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12 | PayPlus must remember and explain Due Day as a material Rent fact, its business-time meaning, provenance, and any owner-governed change. |
| Rent landlord or economic Payee | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12 | PayPlus must remember and explain landlord or economic Payee as a material Rent fact and its provenance without creating PayPlus membership, reciprocal relationship, or Payout truth. |
| Rent Payee bank name | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain Payee bank name as a material Rent fact and its provenance, subject to DOC-15 privacy/access/masking/retention treatment and DOC-10 destination/Payout authority. |
| Rent Payee bank code | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain Payee bank code as a material Rent fact and its provenance without treating that fact as economic-Payee, destination, Payment, or Payout truth by itself. |
| Rent Payee bank account number | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain Payee bank account number as a material Rent fact and its provenance, subject to DOC-15 privacy/access/masking/retention treatment and DOC-10 effective destination, Payout, and reconciliation authority. |
| Rent stated payout method | Direct Founder correction authority; DOC-05; DOC-06C; DOC-10; DOC-12 | PayPlus must remember and explain stated payout method as a material Rent fact and its provenance while DOC-10 retains effective destination, Payout, and reconciliation authority. |
| Optional landlord contact | Direct Founder correction authority; DOC-05/06C/15 owner boundary | PayPlus must remember and explain optional landlord contact as a separate optional fact only where supplied and owner-permitted, including its provenance and approved purpose; PayPlus must not infer that it is material or non-material solely because it is present, absent, or changed. |
| Rent Payer-to-tenant relationship | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12; DOC-15 | PayPlus must remember and explain the Payer-to-tenant relationship as a material Rent fact where the Payer pays for another tenant, without creating account linkage or a reciprocal participant runtime. |
| Rent tenant name | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12; DOC-15 | PayPlus must remember and explain tenant name as required and material where the Payer-to-tenant relationship context applies, including its provenance and approved purpose. |
| Rent tenant mobile | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-12; DOC-15 | PayPlus must remember and explain tenant mobile as required and material where the Payer-to-tenant relationship context applies, including its provenance and approved purpose. |
| Rent Amount versus individual Payment Amount | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-10 | PayPlus must remember and explain both amounts and their relationship; a difference is not automatically an anomaly, mismatch, risk result, underpayment, overpayment, or owner consequence, and any reasonableness assessment remains with its applicable owner. |
| Applicable Rent materiality | Direct Founder correction authority; DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain that address, period, Rent Amount, Due Day, landlord/economic Payee, Payee bank name, bank code, bank account number, stated payout method, Payer-to-tenant relationship, tenant name, and tenant mobile are material Rent facts; optional landlord contact remains a separate optional fact with no inferred materiality; and each change retains its owner-defined Evidence or reconfirmation treatment. |
| Rent/tenancy and accepted-Evidence reuse boundary | DOC-05; DOC-06C; DOC-09; DOC-10; DOC-12; DOC-15 | PayPlus must remember and explain which accepted tenancy context and Rent Evidence remain applicable for reuse, and that reuse ends when expiry, replacement, or material change requires renewed owner-governed Evidence, materiality, or payment treatment. |
| Declaration and reconfirmation contexts | `FD-DOC18-02`; DOC-05; DOC-06C; DOC-07 | PayPlus must remember and explain the facts and confirmation context for Add Bill, a Pay progression that creates a new source, applicable source setup, and material change to a Saved source, while keeping Declaration separate from Save, Evidence, payer authorization, Payment, and Payout. |
| Ordinary Bill/Rent reminder versus Payment Instruction action alert | DOC-06C; DOC-08; DOC-09 | PayPlus must remember and explain whether a communication concerns an ordinary Bill/Rent reminder or an owner-defined Payment Instruction action alert, the applicable source or obligation context, and the separate history without converting one into the other. |
| Deliberate Payment Instruction versus incomplete Checkout Workspace | DOC-06B; DOC-08; DOC-09 | PayPlus must remember and explain a deliberate Payment Instruction and its owner-defined intent separately from an incomplete, partially funded, closed, expired, or otherwise non-continuable Checkout Workspace and its historical context. |
| Controlled late confirmation and immutable application history | DOC-06B; DOC-09; DOC-10; DOC-11; DOC-17 | PayPlus must remember and explain the exactly-one immutable confirmed Payment resulting from accepted late confirmation, any temporary absence of Payment Applications, the closed or expired historical Checkout, the controlled-resolution relationship, and separately owner-governed application, return, adjustment, Settlement, reconciliation, and Payout consequences. |
| Material-change history | `FD-DOC18-02/03`; DOC-05 through DOC-15 according to concern | PayPlus must remember and explain the prior fact, changed fact, provenance, actor/authority, owner materiality assessment, current authoritative fact, supersession, and separately governed consequence without historical rewrite. |
| Historical action basis and then-effective facts | `FD-DOC18-02`; DOC-09/10/11/12/14/15/18 owner boundaries | PayPlus must remember and explain which then-effective facts, owner decisions, qualifications, and relationships supported each historical action or consequence, even when a different fact is current now. |

The table proves positive coverage only when every applicable settled fact or rule has a source-authority row and an explicit obligation describing what PayPlus must remember and explain. A generic family row, requirement ID, topic reference, umbrella phrase, or negative exclusion does not substitute for this fact-level coverage. In particular, `bank account context` cannot substitute for an explicit bank account number, and combined `bank and payout-method context` cannot substitute for separate Payee bank name, bank code, bank account number, and stated payout method facts.

### 4.3 Bill minimum business facts and materiality

Bill recording must preserve, where applicable under the owner rules:

- the same authoritative Bill identity across creation, Save/no-Save treatment, payment-facing use, later Save, Archive, and history-only treatment;
- the current controlled Bill Category and prior Category history;
- declared purpose, Bill amount, applicable period or due facts, and source or biller reference context;
- economic-Payee and receiving details, including the owner-permitted Payee bank name, bank code, and bank account number where relevant;
- a remark where supplied, with the default business understanding that a remark is normally non-material unless an owner rule makes its content material for a defined purpose;
- source provenance, acquisition context, applicable Evidence relationship, Declaration context, and material-change history; and
- owner-defined consequences without using Bill history as Payment, Payout, Evidence, risk, or readiness truth.

These are minimum business questions the recording must answer. They are not approved fields, mandatory display content, a persistence threshold, or authority to retain or expose sensitive details.

### 4.4 Rent minimum business facts and materiality

Rent is a separate tenancy or relationship journey and is not a Bill Category. Rent recording must preserve, where applicable under owner rules:

- the authoritative Rent source and applicable tenancy or relationship context;
- landlord or other economic-Payee context, Payee bank name, bank code, bank account number, and stated payout method;
- optional landlord contact only where supplied and owner-permitted;
- the Rent Amount, applicable rent period and due context;
- when a Payer pays for another tenant, the owner-permitted tenant name, mobile and relationship context needed to explain the payment purpose;
- mandatory attached Evidence and the owner-defined Evidence acceptance relationship;
- source provenance, Declaration or reconfirmation context where applicable, and material-change history; and
- separate Payment amounts, because an individual Payment Amount may differ from the Rent Amount without being anomalous merely for that reason.

The recording must not infer a reciprocal participant relationship, PayPlus account linkage, or user-to-user runtime from factual Payer, tenant, landlord, or economic-Payee context.

Address, period, Rent Amount, Due Day, landlord/economic Payee, Payee bank name, bank code, bank account number, stated payout method, and—where another-tenant context applies—the Payer-to-tenant relationship, tenant name, and tenant mobile are material Rent facts. Optional landlord contact remains a separate optional fact; its presence, absence, or change does not by itself establish materiality.

### 4.5 Declaration coverage

PayPlus must preserve the applicable Declaration or proportionate reconfirmation context for:

1. Add Bill;
2. a Pay progression that establishes a new Bill or Rent source;
3. an applicable owner-defined source setup; and
4. a material change to a Saved source.

The recording must distinguish the facts presented, the Payer's factual or intent confirmation, the applicable owner policy, and any later owner-governed consequence. Unchanged declared facts do not require a new Declaration merely because a limit or gate is re-evaluated. A material change is subject to owner-defined materiality and proportionate reconfirmation; DOC-18 does not decide whether the treatment is field-specific, summary-level, or a full Declaration.

Declaration remains separate from Save intent, Evidence presence or acceptance, Payment readiness, payer authorization, external submission, confirmed Payment, Payout release, and Receipt.

### 4.6 Evidence four-way separation

Evidence recording must keep four meanings independently explainable:

1. **Supplied Evidence:** what was provided, by whom or from what source class, with original provenance and limitations.
2. **Processing and correction:** what was extracted, normalized, inferred, corrected, supplemented, or left uncertain, without overwriting the supplied source.
3. **Owner assessment:** what the Evidence owner assessed about provenance, integrity, declared-fact fit, temporal relevance, duplication, mismatch, acceptance, correction, or review.
4. **Owner-governed consequence:** what another owner permitted, held, rejected, re-evaluated, or left unresolved because of the assessment.

Evidence presence is not Evidence acceptance. Processing confidence is not Evidence acceptance. Evidence acceptance is not payer authorization, confirmed Payment, Payout release, or generic readiness. Bill Tier treatment and the separate Rent Evidence policy remain with their owners. Communication-originated material cannot become mandatory Bill Evidence merely because it is recordable.

### 4.7 Bill-tier recording handoff

For Bills, PayPlus must preserve the applicable owner-defined Tier evaluation and its historical basis without turning the Tier into a generic state. The recording must keep distinguishable:

- the current owner-defined C1 Category single-Payment evaluation, G1 receiving-destination frequency evaluation, and G2 monthly confirmed Bill-value evaluation, including which trigger reason applied;
- the resulting Tier 1, Tier 2, or Tier 3 treatment and the owner-defined precedence where more than one trigger applies;
- Declaration, Evidence presence, Evidence processing, Evidence acceptance, Tier 3 approval, Payment admission, payer authorization, confirmed Payment, Payout release, and reconciliation as separate meanings;
- Tier 1 treatment without an attached-Evidence gate, subject to every other applicable owner gate;
- Tier 2 treatment in which qualifying Evidence presence may permit Payment progression while Evidence acceptance remains a separate Payout gate;
- Tier 3 treatment in which qualifying Evidence and owner-authorized approval are required before Checkout becomes executable or Payment progression may occur;
- the source's Saved/current, Archived, history-only, or unprojected treatment without treating any projection as Evidence, Payment, Payout, or readiness truth; and
- owner-permitted history presentation and retrieval only for the applicable domain owner's approved purpose, with DOC-15 owning privacy, approved-purpose access, masking, visibility and retention; DOC-19 enforcing access already permitted by an owner without creating access authority; DOC-22 executing only an expressly owner-permitted operation; and DOC-21 consuming already-permitted history only for approved monitoring, support, incident or operational evidence without becoming an access or retrieval authority.

Rent remains outside Bill C1/G1/G2 and Tier 1/2/3 treatment. Its mandatory attached Evidence and owner-defined acceptance before Payment remain separate and cannot be replaced or deferred by a Declaration. DOC-18 records these owner-supplied distinctions and their historical relationships; it does not define values, detailed workflows, technical representation, presentation, or downstream owner decisions.

### 4.8 Separate Payment and Payout histories

Payment and Payout histories must remain distinct:

- a confirmed Payment and its Payment Applications remain historical financial facts;
- a later Evidence, risk, case, refund, reversal, adjustment, Payout, or reconciliation outcome relates to those facts but does not rewrite them;
- Payment amount, applied amount, outstanding obligation amount, paid-out amount, returned amount, and adjusted amount retain their owner-defined meanings;
- Payout history preserves its own owner-defined basis, holds, exceptions, outcome, return or reconciliation treatment; and
- neither Evidence progress nor Payment confirmation alone implies Payout completion or recipient receipt.

Under DOC-09's controlled late-confirmation rule, a valid confirmed Payment may temporarily have zero Payment Applications. The recording must preserve that Payment as an immutable confirmed financial fact, identify it as not yet applied, retain the controlled-resolution relationship, and keep the historical Checkout closed or expired. It must not fabricate a Payment Application, reactivate a released historical basis, reduce an obligation without an owner-authorized application, or treat the Payment as ordinarily Payout-ready. Settlement, reconciliation, application, return, refund, adjustment, and later Payout consequences remain separately owner-controlled by DOC-09, DOC-10, DOC-11, and the applicable operational owners; external-interaction mechanics remain with DOC-17.

## 5. Relationships, business time, current effectiveness, material change, supersession, and non-rewrite

### 5.1 Relationship rule

DOC-18 must preserve the relationships needed to explain material business history while avoiding a universal parent model. A Bill or Rent source may relate to Evidence, tenancy context, economic-Payee context, a Payable Basis, a Payment Obligation, Payment, Payment Application, Payout, reconciliation, case, adjustment, communication, and audit history. Each relationship retains the meaning and authority assigned by its owner.

Evidence can support a source or obligation but is not itself the obligation or financial activity. Payment and Payout relate to the applicable obligation and financial history, not to Evidence as the owner of financial activity. Factual source-context association does not create a participant-linking runtime.

### 5.2 Business-time rule

When business-time meanings differ, the recording must preserve enough context to distinguish them. Relevant meanings may include:

- the time stated by a source;
- receipt or capture;
- processing or extraction;
- user correction or confirmation;
- owner assessment or decision;
- the start or end of current effectiveness;
- payer authorization;
- financial confirmation and application;
- Payout or reconciliation consequence;
- material change, replacement, withdrawal, contradiction, expiry, or closure; and
- reporting or derived-use context.

DOC-18 does not select a timestamp model or ordering mechanism. It requires only that later reviewers and systems can tell which business-time meaning supported the then-effective action or consequence.

### 5.3 Material change and historical non-rewrite

For every material change, PayPlus must preserve:

1. the prior fact and its provenance;
2. the change or new information and its provenance;
3. the applicable owner and materiality assessment;
4. the fact recognized as current after the assessment;
5. any owner-governed prospective consequence; and
6. the historical facts, decisions, actions, and consequences that remain unchanged.

A new current fact must not rewrite what was supplied, assessed, declared, authorized, confirmed, applied, paid out, reconciled, communicated, or decided in the past. Correction of an error must remain distinguishable from an ordinary amendment, supplement, replacement, withdrawal, contradiction, or reprocessing result.

### 5.4 Category amendment rule

Category is an amendable material Bill fact. PayPlus does not distinguish or infer why the user changes Category.

A Category amendment:

- retains the same authoritative Bill identity;
- updates the current authoritative Category after the applicable owner treatment;
- preserves the prior Category in material-change history;
- preserves the source, Declaration or reconfirmation, assessment, and supersession context needed for explainability; and
- routes any re-declaration, re-evaluation, Evidence, risk, Payment, Payout, or other downstream consequence to its owner.

The changed Category governs only the purposes for which the applicable owner recognizes it as current. It does not silently rewrite a prior Payable Basis, materialized Payment Obligation, locked Checkout context, payer authorization, confirmed Payment, Payment Application, destination basis, Payout, reconciliation, case, adjustment, communication, or audit history.

### 5.5 Current effectiveness and supersession

Supersession changes which fact an owner treats as current for a defined purpose. It does not convert the superseded fact into false history, delete it, or make every dependent consequence automatically current again.

For a superseded fact, PayPlus must remain able to explain:

- what was previously current and for which purpose;
- which owner recognized that effectiveness;
- which historical actions relied on it;
- what later fact superseded it and for which purpose; and
- which consequences required separate owner review rather than automatic change.

## 6. State, outcome, projection, and communication separation

### 6.1 No overloaded cross-domain meaning

DOC-18 prohibits a single generic readiness or handling meaning from standing in for distinct owner facts. The following remain separate where applicable:

```text
Bill or Rent source treatment
!= Evidence presence
!= Evidence processing result
!= Evidence owner assessment
!= Payment admission or Payment condition
!= payer authorization
!= confirmed Payment
!= Payment Application
!= Payout condition or reconciliation
!= risk or compliance outcome
!= case or adjustment lifecycle
!= operation Outcome
!= Resolution Strategy
!= Message or CTA
!= Notification or Receipt
!= presentation label
!= access or retention treatment
```

`Ready`, `Under Review`, `Action Required`, `complete`, `accepted`, or similar language has meaning only within the scope of the owner that defines it. DOC-18 must not create an overall PayPlus readiness state or imply production, enablement, or launch readiness.

### 6.2 Owner state and business outcome

Where an owner defines a persistent state, assessment result, operation Outcome, or case condition, DOC-18 records the distinction and relationship without redefining the allowed values. An occurrence of a decision or action remains separate from the current state it may affect.

### 6.3 Presentation, Message, Notification and Receipt

A presentation projection is not automatically the authoritative fact. Message and CTA meaning remains with DOC-07; Notification, Receipt and delivery meaning remains with DOC-08. Read, archive, delivery, retry, suppression, display, or navigation treatment must not change the underlying Bill, Evidence, Payment, Payout, risk, case, privacy, or other owner fact.

Historical presentation may accurately show a then-effective fact or action even when a different fact is current now. It must not present a superseded fact as current or silently apply current meaning to a historical consequence.

## 7. External Observations and cross-boundary handoff representation

### 7.1 External Observation non-authority

Information received from outside an authoritative PayPlus owner boundary is an External Observation until the applicable owner evaluates it under accepted rules. Receipt, repetition, apparent success, or technical validity does not by itself establish:

- Evidence acceptance;
- Payee, destination, Payment, payer authorization, Payout, reconciliation, refund, case, risk, privacy, security, notification, or Admin truth;
- a financial or privileged consequence; or
- implementation, acceptance, operating effectiveness, enablement, or readiness.

### 7.2 Minimum observation explainability

For each material External Observation, the recording must make it possible to explain:

- its source class and applicable provenance;
- the business subject or interaction to which it was believed to relate;
- known uncertainty, limitation, duplication, lateness, absence, staleness, contradiction, or replacement;
- the owner responsible for evaluation;
- the assessment or non-assessment that followed; and
- any separately owned consequence.

These are business questions only. DOC-18 does not define external contracts, transport, payloads, identifiers, security controls, or implementation mechanics.

### 7.3 Handoff and historical integrity

A cross-boundary handoff must not imply that two owners share one atomic truth. The sending fact, information in transit, receiving observation, receiving-owner assessment, and receiving-owner consequence remain distinguishable.

Repeated, late, stale, missing, malformed, or contradictory information must not silently create a duplicate consequence or rewrite a prior owner decision. Recovery, reconciliation, and exception treatment remain with the applicable owners; DOC-18 preserves the business history needed to support them.

## 8. Continuity, actionability, presentation, access, retention, and operational/Admin retrievability

### 8.1 Six separate questions

For every material current or historical fact, PayPlus must keep these questions separate:

| Question | Owner-governed meaning |
| --- | --- |
| Continuity | Does the authoritative identity and historical lineage remain preserved? |
| Current effectiveness | Does the applicable owner currently recognize the fact for a defined purpose? |
| Actionability | Does an owner permit an action based on the fact now? |
| Presentation | May an owner-approved projection show the fact, to whom, and as current or historical? |
| Access | May a person or process retrieve the fact for an approved purpose, with applicable masking or restriction? |
| Retention | Must or may the record remain, and under what lawful scope, exception, restriction, hold, or prohibited-data rule? |

A record can remain historically preserved without being current, actionable, presented, or generally accessible. Operational expiry, closure, Archive, replacement, correction, or purpose completion does not by itself authorize historical rewrite or deletion. DOC-15 remains authoritative for retention and lawful handling.

### 8.2 Owner-permitted history retrieval and normal Admin/operational presentation outcome

PayPlus must support owner-permitted normal Admin/operational presentation and retrieval of material history where needed for an approved operational, support, dispute, reconciliation, privacy, risk, audit, or other owner purpose. The permitted presentation or retrieval must be sufficient to explain the source, changes, then-effective facts, decisions, actions, consequences, supersession, and qualifications relevant to that purpose.

This is a required business outcome, not a grant of generic Admin or operational access:

| Owner | Exact boundary |
| --- | --- |
| Applicable domain owner | Defines the approved purpose, business meaning, relevant history, and whether an owner-permitted operational use exists. |
| DOC-15 | Owns privacy classification, approved-purpose access, masking, visibility, retention, lawful-scope qualification, and applicable restrictions. |
| DOC-19 | Owns security enforcement for access that another owner has already permitted; it does not create access or retrieval authority. |
| DOC-22 | Executes only specifically owner-permitted Admin/operational presentation or retrieval using approved facts and controls; it does not create policy, purpose, or truth. |
| DOC-21 | May consume already permitted history only for approved monitoring, support, incident, escalation, closure, or other operational evidence; it is not an access, presentation, or retrieval authority. |
| DOC-18 | Requires that the permitted history can be remembered, related, reconstructed, and explained; it does not define access or presentation mechanics. |

DOC-18 does not define an Admin UI, search, role, permission, workflow, queue, raw-data view or raw access, export, override, or maker-checker process. It defines only the owner-permitted presentation/retrieval outcome and explainability obligation.

### 8.3 Protected and sensitive information

Business-recording completeness does not authorize unnecessary collection, exposure, copying, or retention. Raw PAN, card-verification values, credentials, secrets, one-time codes, passcodes, recovery secrets, cryptographic private material, and other prohibited protected values must not appear in PayPlus business, audit, analytics, support, or reporting representations. Owner-permitted references and masked context are not by themselves Payment, Payout, identity, or authorization truth.

## 9. Audit, lineage, reporting, analytics, AI/model, and partner-reporting boundaries

### 9.1 Audit and lineage purpose

Material recording must support reconstruction of who or what supplied information, who acted, which owner assessed or decided, which facts were effective, what changed, which consequence occurred, and what historical basis applied. Audit and lineage evidence must preserve owner truth and qualifications rather than create a competing domain history.

The business questions include:

- which requirement, source, owner rule, assessment, and fact supported a material action;
- how corrections, supplements, replacements, uncertainty, supersession, and later consequences relate;
- whether a report or derived use relied on current or historical meaning; and
- whether a later owner can obtain the evidence needed for acceptance, operations, support, investigation, or reconciliation.

DOC-18 does not select an audit taxonomy, reason-code library, correlation model, technical format, or storage treatment in this Draft.

### 9.2 Reporting and analytics

Reporting and analytics must remain traceable to owner-defined facts and preserve, as applicable:

- purpose and responsible owner;
- source and transformation lineage;
- current versus historical meaning;
- aggregation or de-identification boundary;
- sensitivity, permitted audience, access and retention treatment;
- qualification, uncertainty and excluded interpretation; and
- whether the output is internal, partner-facing, or otherwise restricted.

An aggregate, dashboard, report, metric, or analytic inference is not automatically an authoritative domain fact and must not silently drive an owner consequence.

### 9.3 AI and model-use boundaries

DOC-18 may state the business evidence and explainability obligations for a separately approved AI-assisted or model-supported use. It does not approve any model, feature, input, output, training use, automated decision, external activation, marketing use, credit use, insurance use, partner sharing, or production deployment.

Before an approved use can rely on PayPlus records, the applicable owners must determine purpose, permitted and prohibited inputs, privacy and security treatment, human review, explanation or reason requirements, monitoring, acceptance, and adverse-impact considerations. A model output remains an input or assessment aid until the applicable owner recognizes a business fact or consequence.

### 9.4 Partner reporting

Partner reporting should prefer the least sensitive owner-approved level of aggregation. Recipient, purpose, permitted detail, aggregation or suppression, retention, disclosure control, and delivery evidence remain subject to the applicable commercial, privacy, legal, security, risk, and domain owners.

DOC-18 does not approve user-level sharing, offsite activation, pseudonymized matching, clean-room activity, a recipient, or an external reporting capability.

## 10. Owner handoffs, safe extension, and deferred technical realisation

### 10.1 Owner-handoff rule

When DOC-18 records a fact or relationship owned elsewhere, it must:

1. name the primary owner;
2. state the minimum recording or explainability obligation;
3. avoid copying the owner's detailed rule;
4. preserve uncertainty or open treatment visibly;
5. identify the owner of any later consequence; and
6. avoid turning absence of implementation detail into permission to invent it.

### 10.2 Safe extension and coding discovery

If later coding, design, acceptance, or operational work discovers missing business meaning, the discovery must be classified before technical work continues:

| Discovery | Required route |
| --- | --- |
| Missing or unclear product/domain rule | Return to the primary owner through Explore or Proposal as required. |
| Missing recording or explainability obligation within accepted DOC-18 ownership | Return to DOC-18 through the Documentation Development Workflow. |
| Missing privacy, security, risk, Admin, acceptance, operations, or professional determination | Return to the named owner; do not infer it in code or supporting material. |
| Implementation-facing representation question with accepted business meaning | Hold for separately authorized technical work and its applicable owner evidence. |
| External capability or contract question | Return to DOC-17 and the applicable domain and professional owners. |

No coding agent, prototype, test, provider material, external observation, or derived document may create business truth that the formal owner has not accepted.

### 10.3 Two-horizon boundary

This Draft establishes the business-recording horizon: semantic separation, minimum explainability, complete record-family coverage, relationships, business time, current effectiveness, material history, supersession, non-rewrite, owner handoffs, and the business questions later technical work must answer.

Exact technical representation remains a later horizon requiring separate evidence, Proposal, authorization, technical drafting, review, acceptance, and implementation. Deferral does not transfer DOC-18's assigned future representation responsibilities to another document, and it does not approve any technical choice now.

### 10.4 Engineering Specification governance gap

`Engineering Specification` is retained only as a working label for a possible future documentation-architecture Explore concerning implementation-facing application capabilities and technical handoffs. That Explore has not begun and has no approved owner, document number, family, structure, artifact, or technical decision. It does not block this business-recording rulebook.

## 11. Decision coverage, Acceptance Criteria, traceability, and open dependencies

### 11.1 Decision and requirement coverage

| Founder decision | Draft representation | Stable requirement coverage | Primary owner dependencies |
| --- | --- | --- | --- |
| `FD-DOC18-01` | Approved eleven-section hybrid active body | `REQ-18-BR-001` through `REQ-18-BR-012` | DOC-00 and the owner map in Section 2 |
| `FD-DOC18-02` | Business recording, explainability, time, relationships, history, supersession, non-rewrite, External Observation, no generic readiness, and retrieval rules | `REQ-18-BR-002` through `REQ-18-BR-011` | DOC-05 through DOC-22 according to concern |
| `FD-DOC18-03` | DOC-18-only business-rulebook boundary, settled Category treatment, Admin retrieval boundary, two horizons, and Engineering gap | `REQ-18-BR-001`, `REQ-18-BR-004`, `REQ-18-BR-006`, `REQ-18-BR-009`, `REQ-18-BR-011`, `REQ-18-BR-012` | DOC-00/05/06C/15/16/17/19/22 |
| Direct Founder bounded correction authority dated 2026-08-27 | Positive Bill/Rent fact and rule coverage, owner-permitted history presentation/retrieval boundary, DOC-00 metadata-label normalization, and positive-coverage verification control | `REQ-18-BR-004`, `REQ-18-BR-006`, `REQ-18-BR-010`, `REQ-18-BR-013`; `AC-18-004`, `AC-18-006`, `AC-18-010`, `AC-18-013` | Product and financial sources: DOC-05/06C/07/09/10/11/12/14; metadata: DOC-00; retrieval: applicable domain owner for purpose, DOC-15 for privacy/access/retention, DOC-19 for enforcement only, DOC-22 for owner-permitted execution, and DOC-21 for consume-only operational evidence |

| Requirement ID | Requirement | Acceptance coverage |
| --- | --- | --- |
| `REQ-18-BR-001` | DOC-18 remains a detailed business-recording rulebook with explicit authority and non-decisions. | `AC-18-001`, `AC-18-012` |
| `REQ-18-BR-002` | Source, processing/extraction, owner assessment, effective fact, and consequence remain separate where meanings differ. | `AC-18-002` |
| `REQ-18-BR-003` | Every material family satisfies the applicable Minimum Explainability Lens and owner handoff. | `AC-18-003` |
| `REQ-18-BR-004` | Bill/Rent minimum facts, materiality, Declaration coverage, Category amendment, and same-source identity are preserved without technical design. | `AC-18-004` |
| `REQ-18-BR-005` | Evidence preserves the four-way separation and separately owned consequences. | `AC-18-005` |
| `REQ-18-BR-006` | Material change, business time, current effectiveness, supersession, and historical non-rewrite remain explainable. | `AC-18-006` |
| `REQ-18-BR-007` | Payment, Payment Application, Payout, reconciliation, case, and adjustment histories retain separate owner meanings. | `AC-18-007` |
| `REQ-18-BR-008` | No generic readiness or overloaded cross-domain meaning is introduced. | `AC-18-008` |
| `REQ-18-BR-009` | External Observation remains non-authoritative and owner evaluation remains visible. | `AC-18-009` |
| `REQ-18-BR-010` | Continuity, actionability, presentation, access, retention, and owner-permitted history presentation/retrieval remain separate; the applicable domain owner defines purpose, DOC-15 owns privacy/access/retention, DOC-19 enforces already-permitted access only, DOC-22 executes owner-permitted operations, and DOC-21 consumes permitted operational evidence without access or retrieval authority. | `AC-18-010` |
| `REQ-18-BR-011` | Coding discoveries and deferred implementation questions route to their owners without invented business or technical truth. | `AC-18-011` |
| `REQ-18-BR-012` | Audit, lineage, reporting, analytics, AI/model, partner reporting, acceptance, and operations remain qualified and owner-governed. | `AC-18-012` |
| `REQ-18-BR-013` | Every settled Founder business fact is individually named in positive, source-identified DOC-18 coverage stating what PayPlus must remember and explain; every settled material fact is explicitly classified as material in its own clause, and optional or unclassified facts remain separate without inferred materiality; generic matrices, topic labels, umbrella phrases, owner lists, or requirement IDs cannot substitute, and policy/access authority, enforcement, owner-permitted execution, and evidence consumption remain distinguished wherever those roles differ. | `AC-18-013` |

### 11.2 Positive coverage verification control

Positive coverage verification is mandatory for every settled Founder business fact, materiality rule, history or non-rewrite rule, and exact owner boundary applicable to DOC-18.

Coverage evidence must make separately inspectable:

1. the exact business fact or rule;
2. its current source authority;
3. an explicit DOC-18 obligation stating what PayPlus must remember and explain;
4. the applicable requirement and Acceptance Criterion;
5. the source owner and every separately governed consequence; and
6. any qualified open or deferred treatment.

A generic family matrix, requirement or Acceptance Criterion ID, topic heading, umbrella phrase, owner list, negative exclusion, or assertion that coverage is complete is not evidence of complete positive coverage. Each settled Founder fact must be named explicitly, each settled material fact must be explicitly classified as material in its own clause, and optional or unclassified facts must remain separate without inferred materiality. If any applicable settled fact, materiality classification, or exact owner boundary lacks positive expression, DOC-18 coverage completeness is not demonstrated.

Section 4.2 is the current positive verification record for the settled Bill/Rent fact, materiality, Category, Declaration, history, and historical-action-basis universe. Later accepted facts must receive the same positive treatment through the Documentation Development Workflow rather than being inferred from this table.

### 11.3 Acceptance Criteria

DOC-18 is acceptable for this Draft scope when:

| AC ID | Criterion |
| --- | --- |
| `AC-18-001` | The eleven-section active body is coherent, owner-first, readable, and does not rely on superseded append-only sections for active meaning. |
| `AC-18-002` | Each applicable source, processing/extraction, assessment, effective-fact, and consequence relationship can be distinguished without assuming a technical pipeline. |
| `AC-18-003` | The complete record-family table covers current material families and every family routes domain truth to one primary owner. |
| `AC-18-004` | Bill and Rent minimum facts, four Declaration contexts, amendable Category on the same Bill identity, prior Category history, and owner-governed consequences are explicit. |
| `AC-18-005` | Supplied Evidence, processing/correction, owner assessment, and owner-governed consequence are distinct; presence and acceptance are not collapsed. |
| `AC-18-006` | Material change preserves provenance, owner treatment, current effectiveness, historical action basis, supersession, and non-rewrite. |
| `AC-18-007` | Confirmed Payment and Payment Application history remains distinct from Payout, reconciliation, Evidence, case, refund, reversal, adjustment, and risk history. |
| `AC-18-008` | The Draft contains no overall readiness state and does not treat source, Evidence, Payment, Payout, risk, case, communication, access, or retention meanings as interchangeable. |
| `AC-18-009` | External Observation is visibly non-authoritative, uncertainty remains visible, and only an applicable owner can establish a consequence. |
| `AC-18-010` | Owner-permitted history presentation/retrieval is a required business outcome with the applicable domain owner defining purpose, DOC-15 owning privacy/access/retention, DOC-19 enforcing already-permitted access only, DOC-22 executing owner-permitted operations, and DOC-21 consuming permitted operational evidence without access or retrieval authority; UI, search, roles, permissions, workflow, raw access, export, queue, override, and maker-checker design remain excluded. |
| `AC-18-011` | Safe-extension and coding-discovery routing prevents code, prototypes, tests, external material, and supporting documents from inventing owner truth or technical design. |
| `AC-18-012` | Privacy, security, provider, acceptance, operations, analytics, AI/model, partner reporting, Engineering Specification, and technical-realisation boundaries are explicit and make no effectiveness or readiness claim. |
| `AC-18-013` | Each settled Founder business fact is individually named with a positive source-authority mapping and an explicit statement of what PayPlus must remember and explain; every settled material fact is explicitly classified as material in its own clause; optional or unclassified facts remain separate without inferred materiality; policy/access authority, enforcement, owner-permitted execution, and evidence consumption are not collectively assigned; and generic matrices, topic labels, umbrella phrases, owner lists, or requirement IDs do not count as complete coverage. |

### 11.4 Traceability and downstream evidence

Later work must be able to trace each accepted requirement to:

- its Founder decision and primary-owner source;
- the material families and relationships it affects;
- the applicable Acceptance Criteria;
- any owner-backed open or deferred dependency;
- later DOC-20 acceptance evidence and DOC-21 operational evidence where applicable; and
- any separately authorized technical or implementation work.

This traceability requirement does not authorize edits to a register, create an implementation ticket, or claim that downstream evidence exists.

### 11.5 Open and deferred dependencies

| Dependency | Owner | Treatment and blocking effect |
| --- | --- | --- |
| Exact field-specific, summary, or full Declaration and proportionate reconfirmation treatment | DOC-05/07 and applicable Product/Legal/Compliance/Privacy/Payments owners | Open later owner treatment; does not block this business-recording rule. |
| Category-by-Category Evidence criteria, C1 values, and affected operating rules | DOC-05/12/14 and applicable owners | Open owner inputs; block only affected configuration, acceptance, and enablement. |
| Field-level privacy classification, approved-purpose access, masking, visibility, correction, legal hold, retention exception, and prohibited-sensitive-data treatment | DOC-15 and applicable professional owners | Open later privacy/access/retention treatment; blocks only affected handling or professional assurance. |
| Security enforcement for already-permitted history access | DOC-19 | Open later enforcement treatment; DOC-19 does not create an access purpose, presentation decision, or retrieval authority. |
| Owner-permitted Admin/operational presentation or retrieval execution mechanics | Applicable domain owner for purpose and permission; DOC-22 for execution only | Explicitly outside this Draft; blocks only the affected Admin or operational execution capability and does not grant DOC-22 policy authority. |
| Monitoring, support, incident, escalation, closure, or operational-evidence consumption of already-permitted history | DOC-21 | Open later evidence-consumption treatment; DOC-21 is not an access, presentation, or retrieval authority. |
| Exact technical representation and implementation | Engineering / Data and applicable owners under separate authority | Deferred; no technical choice or implementation readiness is established. |
| External capability and provider-specific facts | DOC-17 and applicable domain/professional owners | Deferred; blocks only affected feasibility, implementation, acceptance, or enablement. |
| Testing, UAT, monitoring, support, incident, operational and launch evidence | DOC-20/21 and applicable owners | Not performed by this Draft; blocks the corresponding acceptance, operations, or readiness claim. |
| Engineering Specification ownership and documentation architecture | Future separately authorized documentation-architecture Explore | Not a DOC-18 decision and not a blocker to this rulebook. |

No open dependency authorizes DOC-18 to infer missing owner truth or technical detail.

## Version History

| Version | Date | Author | Change Summary |
| --- | --- | --- | --- |
| 2.0.0 | 2026-08-27 | Product Documentation Team | Reorganized DOC-18 into the Founder-approved eleven-section business-recording rulebook; added positive Bill/Rent fact and materiality coverage, minimum explainability, amendable Category history, non-rewrite, External Observation, no-generic-readiness, bounded owner-permitted history presentation/retrieval, safe-extension, and decision/acceptance traceability while deferring all technical representation and implementation choices. |
| 1.0.1 | 2026-08-21 | Product Documentation Team | Aligned DOC-18 ownership with DOC-19 security-control facts while retaining DOC-15 privacy/pseudonymization policy and DOC-18 schema, event, audit, correlation, and lineage representation. |
| 1.0.0 | 2026-08-19 | Stage 11 Alignment: synchronized accepted Bills-tier, Rent, owner-handoff, projection, retention and non-invention meaning without adding implementation detail. | Stage 11 alignment evidence |
| 0.5.0 | 2026-08-14 | Product Documentation Team | Aligned data, event, audit, lineage, reporting, and analytics representation with the Stage 9-passed DOC-16 architecture: local atomic authority, durable non-authoritative handoffs, provider-controlled card-data boundaries, and factual economic-Payee context; added acceptance and evidence-owner handoffs without selecting schemas, events, providers, databases, or security mechanisms. |
| 0.4.24 | 2026-08-13 | Product Documentation Team | Retired active Request/Linking/Receiving Info assumptions, aligned representation to owner-approved source, destination, payment, notification, and indefinite-retention boundaries, and preserved DOC-09/DOC-10/DOC-13 handoffs without adding schemas or mechanisms. |
| 0.4.23 | 2026-07-31 | Product Documentation Team | Added the precise future implementation marker for canonical Request identity and DOC-09 Payment Domain objects, invariants, semantic conditions, correlation, late confirmation, adjustments, and distinct Instruction/Checkout identities. |
| 0.4.22 | 2026-07-29 | Product Documentation Team | Added future data and audit requirements for capability-aware Recovery and explicit separation of authentication Outcome, Resolution Strategy, persistent status, Message/CTA, notification, and occurrence records. |
| 0.4.21 | 2026-07-28 | Product Documentation Team | Replaced the superseded four-label identity projection with five states; added HK phone challenge, provider-result/PayPlus-policy separation, passcode reset, admin reset/dual-approval, security notification, and correlation requirements. |
| 0.4.20 | 2026-07-28 | Product Documentation Team | Added durable future data/event requirements for separate Phone and Identity Verification, first-time versus later identity-change context, four-label projection, provider-pending deduplication, and Payment Passcode Set/Change/Reset modes. |
| 0.4.19 | 2026-07-28 | Product Documentation Team | Aligned future authentication data and event requirements with Entrance, Fast/Full Login, temporary non-reserving registration attempts, atomic restricted-account creation, Account Activation, session revocation, and the mandatory DOC-07 authentication outcome/message/correlation mapping mechanism. |
| 0.4.18 | 2026-07-27 | Product Documentation Team | Added future structures and events for unique primary email, explicit email/Google/Apple login methods, stable provider identity links, first-password setup, restricted-account creation, and financial-activation gates. |
| 0.4.17 | 2026-07-27 | Product Documentation Team | Added future notification event/message/batch/source lineage, category/presentation/domain/action separation, route targeting, delivery-attempt, preference, correlation, and audit requirements for the defined Notifications route family. |
| 0.4.16 | 2026-07-27 | Product Documentation Team | Added future object and privacy-safe event requirements for `MORE-ROOT`, approved shortcut catalog, current eligible default, account-level preferences, protected More, effective resolution, save/restore, availability, and destination handoffs. |
| 0.4.15 | 2026-07-27 | Product Documentation Team | Added future privacy-safe Pay+ action-sheet availability, selection, blocked-reason, and destination-handoff event requirements without defining technical payloads. |
| 0.4.14 | 2026-07-26 | Product Documentation Team | Added canonical-obligation versus per-user archive-projection separation, archived-list/detail/eligibility events, blocker reasons, current-evidence projection, and counterparty-safe restore requirements. |
| 0.4.13 | 2026-07-26 | Product Documentation Team | Added future archive-family, evidence-version lineage, archive-origin/restore-eligibility, parent archive/restore, access recheck, and archived-document audit requirements. |
| 0.4.12 | 2026-07-26 | Product Documentation Team | Added future canonical data separation for request lifecycle, role projections, request events, evidence status, obligation readiness, linked cases, archive visibility, and payment/payout linkage without one overloaded status field. |
| 0.4.11 | 2026-07-26 | Product Documentation Team | Added material-change and Receiving Info reveal/authentication event markers, clarified evidence/request/obligation/payment linkage, and limited the user-facing Bills Activity projection to payment-related transaction events. |
| 0.4.10 | 2026-07-23 | Product Documentation Team | Added future Receiving Info profile/version/proof/readiness, destination-snapshot, source-reference, visibility, linked-notification, authorization-freeze, failure, and audit requirements. |
| 0.4.9 | 2026-07-22 | Product Documentation Team | Added future object and event requirements for Account Information, reusable Identity Verification, contact changes, Payment Passcode Settings, trusted-device/session revocation, privacy requests, protected exports, and account closure. |
| 0.4.8 | 2026-07-22 | Product Documentation Team | Added future data/event markers for DOC-06B `ME-ROOT`, account/security/privacy navigation, payment-passcode-gated reveal auditability, preferences, Receiving Details, archived-evidence access, and logout. |
| 0.4.7 | 2026-07-21 | Product Documentation Team | Added future canonical reward-instrument markers for separate data dimensions, lifecycle projections, checkout/partner linkage, credential events, authoritative fulfilment, idempotency, unknown-result recovery, and operational auditability. |
| 0.4.6 | 2026-07-21 | Product Documentation Team | Added future Referral markers for entitlement-time quota reservation and terms snapshot, separate lifecycle dates, idempotent issuance and recovery, admin hold auditability, status projection, and route-scoped masked-phone visibility. |
| 0.4.5 | 2026-07-21 | Product Documentation Team | Added future Referral object, linkage, event, privacy-projection, qualification, claim, reward-issuance, and audit markers while separating sharing from recipient identity and registration attribution. |
| 0.4.4 | 2026-07-20 | Product Documentation Team | Added future data/event markers for multi-collection Offers, root placement, per-collection priority, payment-card/funding-leg offer evaluation, highest-user-value automatic Card Offer selection, separate coupon/voucher/discount application, quote recalculation, and audit linkage. |
| 0.1.0 | 2026-06-08 | Product Documentation Team | Replaced interim note with founder working baseline for data model ownership, field metadata, event taxonomy, lineage, analytics marts, AI/model-readiness metadata, partner reporting controls, and open questions. |
| 0.2.0 | 2026-06-12 | Product Documentation Team | Aligned data-model baseline with DOC-06 Bills tab requirements by adding obligation, contract/relationship, evidence source, participant linking, invitation, action, and no-auto-matching state/event expectations. |
| 0.3.0 | 2026-06-17 | Product Documentation Team | Aligned data-model baseline with DOC-06 Bills reminder list/detail routes by adding linked reminder objects, lifecycle states, soft-delete metadata, notification linkage, and reminder effectiveness events. |
| 0.4.0 | 2026-06-18 | Product Documentation Team | Added future DOC-18 update markers for DOC-06 Bills evidence detail/upload routes, active evidence versioning, archive-not-delete behavior, evidence status changes, and readiness-change audit events. |
| 0.4.1 | 2026-07-02 | Product Documentation Team | Added future data/event markers for DOC-06B `REQUESTS-NEW`, evidence-gated auto-send, counterparty lookup, sharing, and route handoff auditability. |
| 0.4.2 | 2026-07-03 | Product Documentation Team | Aligned future data-model marker with DOC-06B Instructions route by distinguishing payment instruction action alerts/tasks from ordinary bill/rent reminders. |
| 0.4.3 | 2026-07-06 | Product Documentation Team | Added future data/event markers for DOC-06B Payment Profile route, including tokenized cards, saved split-card profiles, allocation ratios, action-required profile state, and checkout/instruction return context. |
