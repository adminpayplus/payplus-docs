# project-continuation-context.md

## Project

PayPlus — a bill-payment and payment-facilitation product that allows users to pay bills or approved payees using supported funding sources, potentially including card-funded payments and future multi-source payment flows.

The documentation set is being built as a structured product, compliance, payments, risk, operations, and engineering specification library.

The current goal is to create a complete document suite from `DOC-00` onward, with each document using consistent metadata, assumptions, constraints, dependencies, risks, open questions, acceptance criteria, and version history.

---

## Current Date

2026-05-26

---

## Working Style

The user is asking to proceed document by document.

Preferred response style:

- Produce the complete document in Markdown.
- Wrap the full document in a single Markdown code block.
- Use YAML-style front matter.
- Use stable document IDs.
- Include structured sections.
- Include tables where useful.
- Avoid overly casual commentary.
- Do not add legal disclaimers unless they belong in the document.
- Keep documents internally consistent with prior docs.
- Treat PayPlus as a serious fintech/payments product.
- Favor practical launch-readiness, compliance-readiness, partner-readiness, and operational-readiness framing.
- Use `TBD`, `Open`, or explicit placeholders when factual product decisions are not yet known.
- Maintain traceability to downstream documents.

---

## Product Context

PayPlus appears to involve:

- User bill payment.
- Approved billers, payees, or partners.
- Card or other funding sources.
- Potential multi-card or multi-source funding.
- PayPlus service fee.
- PSP/acquirer processing.
- Payouts to billers/payees.
- Settlement, reconciliation, refunds, cancellations, chargebacks, and disputes.
- Compliance-sensitive categories such as rent, taxes, loans, credit card repayment, utilities, tuition, insurance, medical bills, or other bill types.
- Potential regulatory issues around money transmission, payment services, agent models, PayFac/marketplace structures, card network rules, quasi-cash, cash-like transactions, and consumer disclosures.
- Need for AML, sanctions, fraud, anti-cashout, privacy, security, PCI, and operational controls.

No final product, legal, regulatory, jurisdictional, PSP/acquirer, MCC, fee, payout, or funds-flow conclusion has been provided yet.

---

## Document Suite Conventions

Each document should generally include:

1. YAML front matter:
   - `document_id`
   - `title`
   - `version`
   - `status`
   - `owner`
   - `reviewers`
   - `approvers`
   - `last_updated`
   - `classification`
   - `related_documents`

2. Main heading:
   - `# DOC-XX — Title`

3. Core sections appropriate to the document.

4. Structured tables for:
   - requirements,
   - gates,
   - controls,
   - assumptions,
   - constraints,
   - dependencies,
   - risks,
   - open questions,
   - acceptance criteria,
   - version history.

5. Version history with:
   - `0.1.0` dated `2026-05-14` where initial draft exists,
   - current expanded/reframed version dated `2026-05-26`.

6. Cross-document consistency:
   - Use references like `DOC-03`, `DOC-04`, etc.
   - Ensure downstream document impacts remain aligned.

---

## Documents Completed or Drafted

### `DOC-00 — Documentation Governance`

Status: Previously created.

Likely role:

- Governs document suite.
- Defines ownership, review, approvals, versioning, change control, and document taxonomy.

Use as the governance anchor for all subsequent docs.

---

### `DOC-01 — Project Charter & Product Positioning`

Status: Previously created.

Likely role:

- Defines PayPlus project purpose, scope, product thesis, stakeholders, objectives, and positioning.
- Sets strategic foundation.

---

### `DOC-02 — Business Model & Unit Economics`

Status: Completed/reframed.

Important framing:

- PayPlus monetizes through service fees and possibly other revenue streams.
- Unit economics depend on:
  - processing fees,
  - interchange/scheme/acquirer costs,
  - payout costs,
  - refund costs,
  - chargeback costs,
  - fraud losses,
  - reserves/holdbacks,
  - support costs,
  - promotion costs,
  - financing or prefunding costs,
  - settlement timing.
- Must model gross margin, contribution margin, break-even, and sensitivity by category/payment method.
- Connects heavily to `DOC-03`, `DOC-04`, `DOC-09`, `DOC-10`, `DOC-11`, `DOC-14`, and `DOC-18`.

---

### `DOC-03 — Regulatory, PSP & Acquirer Assessment`

Status: Completed as version `0.2.0`.

Important framing:

- Foundation assessment framework.
- Does **not** provide legal advice or final regulatory conclusions.
- Used before launch, new jurisdiction, new bill category, new payee type, new payment method, multi-card launch, funds-flow change, payout change, pricing/fee change, new PSP/acquirer/provider, material risk changes, or regulatory/card network changes.
- Covers:
  - regulatory role assessment,
  - licensing/exemption considerations,
  - money transmission/payment services,
  - PayFac/marketplace/agent models,
  - funds flow,
  - PSP/acquirer/card network acceptability,
  - MCC and transaction classification,
  - bill category/payee assessment,
  - prohibited/restricted/enhanced review categories,
  - partner due diligence,
  - partner scorecard,
  - required partner confirmations,
  - consumer disclosures,
  - AML/sanctions/fraud/anti-cashout assessment,
  - privacy/security,
  - contracts,
  - reserves/settlement/liquidity,
  - multi-card/multi-source review,
  - compliance readiness gates,
  - assessment template.

Important `DOC-03` concepts to carry forward:

- No product flow should launch without documented regulatory role assessment.
- No unsupported category should launch without partner/legal/compliance approval.
- Funds-flow changes trigger reassessment.
- PSP/acquirer written confirmation is preferred.
- MCC/classification may affect cost, issuer behavior, user complaints, and legal/partner obligations.
- Multi-card/multi-source payment requires special review.
- Partner contracts must support refunds, chargebacks, reconciliation, settlement, reserves, reporting, and data/security obligations.

---

### `DOC-04 — Compliance Certification Roadmap & Control Framework`

Status: Reframed and completed as version `0.3.0`.

Important framing:

- PayPlus-specific compliance certification framework.
- Converts `DOC-03` outputs and other obligations into controls, gates, evidence, testing, and launch certification.
- “Compliance certification” is defined broadly as documented internal and partner-supported readiness, not necessarily a single external certificate.
- Strongly MVP-focused and launch-readiness oriented.

Major additions in `0.3.0`:

1. **Definition of compliance certification**
   - Internal launch certification.
   - Regulatory readiness certification.
   - PSP/acquirer readiness certification.
   - Payout readiness certification.
   - Security/PCI readiness certification.
   - Privacy readiness certification.
   - AML/sanctions/fraud readiness certification.
   - Consumer protection readiness certification.
   - Operational readiness certification.
   - Expansion certification.

2. **PayPlus-specific risk themes**
   - Bill payment may not be ordinary card commerce.
   - PayPlus may receive funds before paying third-party payee.
   - Payout may happen before final settlement/chargeback window ends.
   - Chargebacks may occur after payout.
   - Multi-card/multi-source increases complexity.
   - User-paid service fees create legal/network/disclosure risk.
   - Certain categories resemble cashout, debt repayment, money transfer, or restricted activity.
   - MCC/classification affects issuer behavior/user experience.
   - Payee verification is central to anti-cashout.
   - Partner approvals are operating constraints.
   - Reconciliation must link charges, fees, payouts, refunds, chargebacks, reserves, and ledger.
   - Product changes may alter regulatory classification.

3. **MVP compliance posture**
   - Conservative, limited jurisdiction/category/payment/payout scope.
   - Avoid unsupported funds flows, unapproved categories, self-payments, risky categories, cross-border, FX, wallet/stored value, payout before funding certainty, and multi-card unless separately approved.

4. **Control tiering**
   - `T0` — non-waivable blocker.
   - `T1` — critical launch control.
   - `T2` — important operating control.
   - `T3` — scale/maturity control.

5. **Non-waivable launch blockers**
   - Regulatory role/licensing path approved.
   - PSP/acquirer approval.
   - Payout readiness.
   - Approved categories.
   - Fee/timing/refund/role disclosures before authorization.
   - PCI scope.
   - Sanctions requirements.
   - Baseline fraud/velocity/anti-cashout.
   - Daily reconciliation.
   - Refund/cancellation/payout failure/chargeback procedures.
   - Incident escalation.
   - Privacy/terms/consent.
   - Evidence repository.
   - Launch approval signatures.

6. **Risk acceptance authority**
   - Critical risks require Project Owner, Legal Lead, Compliance Lead, and relevant functional lead.
   - T0 blockers cannot be accepted/waived.
   - High/medium/low risks have defined authority.

7. **Minimum MVP control baseline**
   - Regulatory/partner baseline.
   - Product/disclosure baseline.
   - User/payee baseline.
   - AML/sanctions/fraud/anti-cashout baseline.
   - Payment/payout/reconciliation baseline.
   - Security/privacy/access baseline.
   - Operations baseline.

8. **Control matrix with tiers**
   - Includes T0/T1/T2/T3 controls.
   - Important controls include regulatory assessment, PSP/acquirer support, payout readiness, category controls, sanctions, fraud, disclosures, authorization logging, settlement reconciliation, payout exceptions, refunds, PCI, privacy, incident escalation, change management, training, control testing, SOC 2 readiness.

9. **Evidence system-of-record mapping**
   - Legal assessment, PSP approval, payout approval, fee approval, UI evidence, consent, screening, fraud decisions, settlement reports, payout reports, ledger entries, reconciliation exceptions, refunds, disputes, complaints, PCI, access review, audit logs, incidents, vendor diligence, change approval, training.

10. **Certification roadmap**
    - Discovery.
    - MVP control design.
    - MVP control build.
    - MVP control test.
    - MVP certification.
    - Controlled launch.
    - Stabilization.
    - Scale readiness.
    - Expansion certification.

11. **Launch gates**
    - T0/T1 gates tied to launch scope, regulatory role, PSP/acquirer, payout, categories, user/payee, sanctions, fraud, disclosures, authorization, reconciliation, security/PCI, privacy, support, incident escalation, evidence, exceptions, approval.

12. **Relationship to `DOC-03`**
    - `DOC-03` identifies risks and obligations.
    - `DOC-04` operationalizes controls and certification.
    - If `DOC-03` identifies critical unresolved issues, `DOC-04` blocks, narrows scope, remediates, or requires acceptable risk acceptance.

13. **Relationship to `DOC-20`**
    - `DOC-20` should convert `DOC-04` controls into executable go/no-go checklist.

---

## Current Next Document

The likely next document is:

### `DOC-05 — Master PRD & Feature Requirement Index`

Expected role:

- Product-wide master requirements document.
- Should consolidate product features and reference downstream feature-specific docs.
- Should translate project/compliance/business constraints into product requirements.
- Should not over-specify implementation details that belong in technical docs.
- Should include a requirement taxonomy and feature index.
- Should align strongly with `DOC-03` and `DOC-04`.

Recommended framing for `DOC-05`:

- It is the master product requirements and feature traceability document.
- It should define:
  - MVP scope,
  - non-MVP scope,
  - feature domains,
  - requirement priority,
  - launch-critical requirements,
  - compliance-critical requirements,
  - payment-critical requirements,
  - risk-critical requirements,
  - user journeys,
  - role/persona overview,
  - requirement ID scheme,
  - acceptance criteria format,
  - traceability to controls/gates,
  - dependency mapping to downstream docs.

Important `DOC-05` should inherit from `DOC-04`:

- T0/T1 controls must become product requirements where product-facing.
- Fee and total-charge disclosure before authorization is a T0 requirement.
- Consent/version/timestamp logging is required.
- Approved/restricted/prohibited category enforcement is required.
- User/payee eligibility and verification are required.
- Sanctions/fraud/manual-review hooks are required.
- Transaction logs must link user, amount, fee, payee, payment method, authorization, payout, refund, chargeback, and ledger state.
- Multi-card/multi-source should be explicitly marked as MVP-included only if separately approved; otherwise deferred or gated.
- Admin/risk/reconciliation support should be treated as product requirements, not just ops afterthoughts.
- Launch scope must be explicit and scope-specific.

Possible `DOC-05` sections:

1. Purpose
2. Scope
3. Out of Scope
4. Product Principles
5. Source-of-Truth Relationship
6. MVP Product Scope
7. Deferred / Non-MVP Scope
8. User Roles and Personas
9. Core User Journeys
10. Requirement Taxonomy
11. Requirement Priority and Criticality
12. Feature Domain Index
13. Master Requirement Index
14. Compliance-Critical Product Requirements
15. Payment-Critical Product Requirements
16. Risk-Critical Product Requirements
17. Operations-Critical Product Requirements
18. Data and Evidence Requirements
19. UX and Content Requirements
20. Admin and Internal Tooling Requirements
21. Reporting and Reconciliation Requirements
22. Non-Functional Requirements
23. Traceability Matrix
24. Release and Change Control
25. Assumptions
26. Constraints
27. Dependencies
28. Risks
29. Downstream Document Impact
30. Open Questions
31. Acceptance Criteria
32. Version History

---

## Cross-Document Themes to Preserve

Across all future docs, preserve these themes:

### Launch is scope-specific

Approval for one jurisdiction, category, partner, payment method, payout method, or funds flow does not approve others.

### Compliance controls are product requirements

Do not treat compliance as separate from product design. Disclosures, consent capture, category blocking, verification, risk routing, evidence retention, and audit logs are product requirements.

### PSP/acquirer approval matters

Product assumptions must be subordinate to PSP/acquirer, payout provider, card network, and legal constraints.

### Funds flow drives everything

Regulatory role, licensing, settlement, reconciliation, refund, chargeback, risk, and accounting treatment all depend on funds flow.

### Multi-source funding is high complexity

Multi-card or multi-source funding must be deferred, restricted, or separately certified unless the user explicitly decides it is MVP.

### Payee verification is central

Payee verification and self-payment/collusion controls are core to anti-cashout and fraud prevention.

### Fee disclosure is launch-critical

Service fee, bill amount, total charge, payment timing, PayPlus role, refund/cancellation rules, and user responsibility must be clear before authorization.

### Reconciliation is not optional

Daily reconciliation across user charge, fees, PSP settlement, payout, refunds, chargebacks, reserves, and ledger is a launch blocker.

### Evidence matters

Every critical control should produce durable evidence in a known system of record.

### Change management is mandatory

New category, jurisdiction, funds flow, fee model, payment method, payout method, provider, or material product change triggers reassessment.

---

## Known Open Strategic Questions

These remain unresolved and should continue appearing as open questions where relevant:

- What jurisdiction will PayPlus launch in first?
- What exact MVP bill categories are in scope?
- What exact MVP funds flow will be used?
- What is PayPlus’s legal/regulatory role?
- Is PayPlus merchant of record, agent, PayFac, marketplace, money transmitter, technical provider, or another role?
- What licensing, exemption, or partner coverage applies?
- Which PSP/acquirer will support MVP?
- What MCC or transaction classification applies?
- Will transactions be treated as purchase, quasi-cash, account funding, money transfer, or cash advance?
- What payout provider and payout rail will be used?
- Does payout occur before settlement or before funding certainty?
- What settlement timing, reserves, holdbacks, or prefunding apply?
- What transaction, user, card, and payee limits apply?
- What payee verification is required?
- What sanctions screening is required?
- What fraud and anti-cashout rules are required at launch?
- Is multi-card or multi-source funding included in MVP or deferred?
- What PCI scope applies?
- What disclosures must be shown before authorization?
- What records must be retained?
- What systems of record will store consent, authorization, risk decisions, payouts, refunds, disputes, and reconciliation evidence?
- Who has final authority to approve MVP launch?

---

## Current State Summary

Completed through:

- `DOC-03` as `0.2.0`
- `DOC-04` as `0.3.0`

Next recommended action:

- Draft `DOC-05 — Master PRD & Feature Requirement Index`
- Ensure it converts `DOC-04` T0/T1 controls into product requirements and traceability items.
