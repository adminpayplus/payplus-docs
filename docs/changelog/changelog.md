# PayPlus Documentation Changelog

## 1. Purpose

This append-only register records the documentation delivered by each substantive commit. It complements the decision log and does not replace formal document version histories.

## 2. Recording Standard

- Add one entry after every substantive documentation commit.
- Record the substantive commit identifier and actual delivered files.
- Summarize material changes, replaced definitions, validation performed, and remaining open items.
- Link each change to its primary owning document and decision-log entry where applicable.
- Apply the PayPlus writing, ownership, source-of-truth, scope, and review standards from `AGENTS.md`.
- Preserve history; correct errors through a dated correction instead of silently deleting prior entries.

## 3. Changelog Entry Template

### `YYYY-MM-DD` - Change Title

| Field | Record |
| --- | --- |
| Substantive commit | Commit identifier |
| Primary owner | `DOC-XX`, section |
| Decision record | `DEC-YYYY-NNN` or `Not applicable` with reason |
| Founder approval | Approval source or date |

**Files Changed**

- List the files included in the substantive commit.

**Material Changes**

- Summarize delivered requirements, replacements, ownership changes, alignment, and metadata updates.

**Checks Performed**

- Record integration, consistency, formatting, diagram, acceptance, and traceability checks performed.

**Remaining Open Items**

- List surviving `TBC` or open questions. Otherwise state `None`.

## 4. Change Records

### `2026-07-20` - Offers Child Lists, Checkout Selection, And Commit Records

| Field | Record |
| --- | --- |
| Substantive commit | `36458da` |
| Primary owner | `DOC-00` documentation governance and `DOC-13` promotion engine |
| Decision record | `DEC-2026-001`, `DEC-2026-002`, `DEC-2026-003` |
| Founder approval | Approved in the founder review task on `2026-07-20` |

**Files Changed**

- `AGENTS.md`
- `docs/00-foundation/doc-00-documentation-governance.md`
- `docs/00-foundation/payplus-document-change-integration-workflow.md`
- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md`
- `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`
- `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
- `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`
- `docs/README.md`
- `docs/changelog/changelog.md`
- `docs/decision-log/decisionlog.md`
- `docs/diagrams/payplus-promotion-engine-structure.md`
- `docs/review/reviewpack.md`
- `docs/traceability/requirements-traceability-matrix.md`

**Material Changes**

- Added the mandatory substantive-commit, changelog, decision-log, and records-only follow-up workflow.
- Defined a shared child-list contract for Card Offers, PayPlus Offers, and Partner Offers, including collection membership, duplicate suppression, stable ordering, search, filters, and route handoffs.
- Defined automatic selection of the highest-value eligible payment-method-sensitive Card Offer per payment card or split-payment funding leg.
- Preserved separate application of an eligible checkout coupon, voucher, or discount and aligned UX, checkout, data, admin, acceptance, diagram, and traceability references.

**Checks Performed**

- Verified the staged file scope and excluded unrelated workspace changes.
- Ran `git diff --cached --check` before the substantive commit.
- Checked route ownership, promotion ownership, checkout handoff, data and admin handoffs, acceptance criteria, traceability, and promotion-diagram alignment.
- Confirmed `DOC-08`, `DOC-15`, and the app route-topology diagram did not require changes.

**Remaining Open Items**

- Final valuation method for non-monetary or equal-value offers.
- Equal-priority child-list ordering fallback.
- PayPlus Offer and Partner Offer label taxonomy.
- Exact split-card checkout presentation and future personalization rules.
- Final PSP-returned card metadata.

### `2026-07-21` - Referral Attribution, Qualification, And Reward Claiming

| Field | Record |
| --- | --- |
| Substantive commit | `898d994` |
| Primary owner | `DOC-06B` Referral routes and `DOC-13` referral/entitlement logic |
| Decision record | `DEC-2026-004` |
| Founder approval | Approved in the founder review task on `2026-07-21` |

**Files Changed**

- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06a-core-user-journeys-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/01-product/doc-08-notification-receipt-communication-spec.md`
- `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`
- `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md`
- `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
- `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`
- `docs/diagrams/payplus-app-route-entry-map.md`
- `docs/traceability/open-questions-register.md`
- `docs/traceability/requirements-traceability-matrix.md`
- `docs/traceability/status-display-reference-matrix.md`

**Material Changes**

- Defined `REFERRAL-ROOT`, `REFERRAL-REWARDS-LIST`, `REFERRAL-ENTITLEMENT-DETAIL`, and `REFERRAL-REWARD-CLAIM` with registration and canonical Rewards handoffs.
- Defined one PayPlus Referral Program, one MVP campaign, reusable non-expiring user-linked codes, no-recipient-on-share behavior, registration attribution, qualification progress, and role-sensitive referrer/referee entitlements.
- Confirmed that referral entitlements and issued instruments reuse the canonical promotion/reward engine and status model.
- Aligned notification, privacy, future data/event, admin, acceptance, route-map, and traceability requirements without changing Requests, payment authorization, or payer/payee linking boundaries.

**Checks Performed**

- Verified the staged scope contained only the 14 approved files.
- Ran `git diff --cached --check` before the substantive commit.
- Searched for stale Referral invitation-lifecycle and partially-defined route wording.
- Checked route ownership, registration attribution, masking, status reuse, canonical reward issuance, PayPlus boundaries, metadata, acceptance, diagrams, and traceability.
- Confirmed external handoff files, prototypes, generated assets, and unrelated workspace changes were excluded.

**Remaining Open Items**

- Exact campaign rewards, qualification conditions, source events, payment/risk finality, quotas, and limits.
- Final deeplink/QR token contract, attribution idempotency/correction controls, notification copy, and admin implementation.
- Final multi-campaign visual design and technical data/status/event schemas.

### `2026-07-21` - Referral Child-Screen And Entitlement Lifecycle

| Field | Record |
| --- | --- |
| Substantive commit | `9306498` |
| Primary owner | `DOC-06B` Referral child screens and `DOC-13` referral entitlement logic |
| Decision record | `DEC-2026-005` |
| Founder approval | RCS-01 to RCS-13 and the exceptional administrator-held behavior approved on `2026-07-21` |

**Files Changed**

- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/01-product/doc-08-notification-receipt-communication-spec.md`
- `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`
- `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md`
- `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
- `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`
- `docs/diagrams/payplus-app-route-entry-map.md`
- `docs/traceability/open-questions-register.md`
- `docs/traceability/requirements-traceability-matrix.md`
- `docs/traceability/status-display-reference-matrix.md`

**Material Changes**

- Defined `Available to Claim` and `History` route-local tabs, `REFERRAL-REWARD-CARD` as a non-route component, and detailed list/detail/claim behavior.
- Made corresponding referrer and referee entitlements visible to each beneficiary while restricting masked referee phone to `REFERRAL-ROOT` progress.
- Defined detail-first manual claiming, deterministic success return, idempotent one-entitlement-to-at-most-one-instrument issuance, and canonical `REWARD-DETAIL` handoff.
- Defined entitlement-time quota reservation and terms snapshot, separate campaign-end/claim-deadline/usage-expiry dates, and exceptional inactive `Under Review` History presentation for an administrator-held claimed reward.
- Aligned product, notification, privacy, acceptance, future data/admin markers, route diagram, status display, open questions, and traceability without creating new routes or reward status families.

**Checks Performed**

- Verified the staged scope contained only the 13 approved files and preserved unrelated workspace changes.
- Ran `git diff --cached --check` before the substantive commit.
- Searched for active referrer-only claiming definitions and checked route, component, status, privacy, notification, canonical reward, acceptance, and lifecycle-date alignment.
- Reviewed the Mermaid source manually; Mermaid CLI was unavailable for rendered validation.

**Remaining Open Items**

- Exact campaign rewards, qualification conditions, source events, payment/risk finality, values, quotas, and limits.
- Final deeplink/QR contract, attribution correction controls, notification copy, future multi-campaign visual behavior, and full admin implementation.
- Final DOC-18 objects, canonical statuses/events, recovery contracts, and audit schema.

### `2026-07-21` - My Rewards Route And Canonical Reward Instrument Lifecycle

| Field | Record |
| --- | --- |
| Substantive commit | `298ab49` |
| Primary owner | `DOC-06B` Rewards routes and `DOC-13` reward-instrument logic |
| Decision record | `DEC-2026-006` |
| Founder approval | RWD-01 to RWD-16 approved on `2026-07-21`; hold-versus-expiry treatment remains open |

**Files Changed**

- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/01-product/doc-07-content-disclosure-user-authorization-spec.md`
- `docs/01-product/doc-08-notification-receipt-communication-spec.md`
- `docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md`
- `docs/02-payment-domain/doc-11-refund-cancellation-chargeback.md`
- `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`
- `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md`
- `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
- `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`
- `docs/diagrams/payplus-app-route-entry-map.md`
- `docs/traceability/open-questions-register.md`
- `docs/traceability/requirements-traceability-matrix.md`
- `docs/traceability/status-display-reference-matrix.md`

**Material Changes**

- Defined `My Rewards` through `REWARDS-ROOT` Active/History views, search, instrument filters, ordering, route states, reward cards, and origin-preserving return behavior.
- Defined `REWARD-DETAIL` as the complete reward/T&C surface with contextual external, credential, miles, action-required, and checkout-detail behavior without creating another checkout route.
- Kept reward selection in DOC-09 checkout after payment-card/profile choice and required status, expiry, eligibility, stacking, limits, and quote revalidation before authorization.
- Defined canonical reward display labels, single-use default, authoritative/idempotent fulfilment, credential-reveal-versus-use boundary, unknown-result protection, and restored-reward return to Active.
- Required independent reward instrument type, earning source, participant role, program, campaign/offer/entitlement source, and fulfilment-method dimensions across product, data, privacy, acceptance, and admin handoffs.
- Confirmed external vouchers and miles as launch-supported reward types while leaving each partner method and operational readiness gated.

**Checks Performed**

- Ran product/reward-domain, consistency/privacy/data, and acceptance/integration reviews and resolved all material findings.
- Verified the staged scope contained only the 16 approved files and preserved unrelated workspace changes.
- Ran `git diff --cached --check` before the substantive commit.
- Searched for superseded three-view Rewards wording, unresolved My Rewards naming, stale external-reward scope, conflicting status labels, route-parent errors, and restoration-to-History errors.
- Reviewed Mermaid source manually; Mermaid CLI was unavailable for rendered validation.

**Remaining Open Items**

- Whether a reward hold pauses, extends, permits, or reverses expiry.
- Final external-voucher and miles partners, credentials, fulfilment methods, reconciliation, and activation readiness.
- Final DOC-18 schema, idempotency keys, credential model, and unknown-result recovery.
- Final My Rewards visual styling/icon and any later approved fixed-count usage rules.

### `2026-07-22` - Me Account-Control Route And Child-Destination Boundaries

| Field | Record |
| --- | --- |
| Substantive commit | `0586a37` |
| Primary owner | `DOC-06B`, Me route |
| Decision record | `DEC-2026-007` |
| Founder approval | Approved in the founder review task on `2026-07-22` |

**Files Changed**

- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06c-bills-rent-tenancy-ux-module.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/01-product/doc-08-notification-receipt-communication-spec.md`
- `docs/02-payment-domain/doc-10-payout-reconciliation.md`
- `docs/03-bill-verification/doc-12-bill-category-document-ai-ocr-payee-verification-spec.md`
- `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md`
- `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
- `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`
- `docs/diagrams/payplus-app-route-entry-map.md`
- `docs/traceability/open-questions-register.md`
- `docs/traceability/requirements-traceability-matrix.md`

**Material Changes**

- Defined `ME-ROOT` as the permanent mixed-role bottom-navigation account-control route with fixed section order and no payer/payee role switch.
- Defined the Account Profile, Account Security, Privacy & Data, Receiving Details, Archived Documents, Notification Settings, Support, About, and Terms destination purposes and handoffs while leaving detailed child-screen UI open.
- Required masking by default and the existing PayPlus payment passcode for sensitive reveal, with additional step-up where the owning rules require it.
- Kept `ACTIVITY-ROOT` as the single mixed-role financial activity route, limited `RECEIVING-DETAILS` to payout-destination management, and limited `ARCHIVED-EVIDENCE-LIST` to archived or previous evidence.
- Kept More separate as the dashboard shortcut-management, reorder, restore-default, overflow, and secondary-services area.
- Aligned product requirements, acceptance coverage, notifications, payout, evidence, privacy, future data/admin requirements, traceability, open questions, and the app route map.

**Checks Performed**

- Verified DOC-06B remained the sole route-level UX owner and reference documents did not duplicate its behavior.
- Searched for stale Me shorthand, undefined route wording, unapproved Membership route IDs, and conflicting Receiving Details, Activity, Archived Documents, masking, and Action Required definitions.
- Checked metadata, version histories, route-register structure, Markdown fence balance, and Mermaid source structure.
- Ran `git diff --cached --check` and verified the substantive commit contained only the 14 approved files.

**Remaining Open Items**

- Final child-screen fields and visual design.
- Final identity-verification display labels and system mapping.
- Final receiving-destination workflow and Archived Documents list/detail behavior.
- Final language/theme options, Support/About/Terms content, Membership destination, and More UI.

### `2026-07-22` - Document Control Presentation And Repository-Tree Repair

| Field | Record |
| --- | --- |
| Substantive commit | `53bfc19` |
| Primary owner | `DOC-00` documentation governance |
| Decision record | `DEC-2026-008` |
| Founder approval | Approved in the documentation-formatting task on `2026-07-22` |

**Files Changed**

- `AGENTS.md`
- `docs/00-foundation/doc-00-documentation-governance.md`
- `docs/00-foundation/doc-01-project-charter-product-positioning.md`
- `docs/00-foundation/doc-02-business-model-unit-economics.md`
- `docs/00-foundation/doc-03-regulatory-psp-acquirer-assessment.md`
- `docs/00-foundation/doc-04-compliance-certification-roadmap-control-framework.md`
- `docs/00-foundation/payplus-document-change-integration-workflow.md`
- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06a-core-user-journeys-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06c-bills-rent-tenancy-ux-module.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/01-product/doc-07-content-disclosure-user-authorization-spec.md`
- `docs/01-product/doc-08-notification-receipt-communication-spec.md`
- `docs/02-payment-domain/doc-09-payment-request-multi-funding-source-settlement.md`
- `docs/02-payment-domain/doc-10-payout-reconciliation.md`
- `docs/02-payment-domain/doc-11-refund-cancellation-chargeback.md`
- `docs/03-bill-verification/doc-12-bill-category-document-ai-ocr-payee-verification-spec.md`
- `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`
- `docs/04-growth-ecosystem/payplus-data-strategy-ai-marketing-research.md`
- `docs/05-risk-compliance-privacy/doc-14-aml-anti-cashout-fraud-dynamic-auth-risk-control-spec.md`
- `docs/05-risk-compliance-privacy/doc-15-privacy-data-protection-record-retention-spec.md`
- `docs/06-engineering/doc-18-data-model-transaction-state-audit-event-spec.md`
- `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`
- `docs/change-requests/cr-doc-06-modularization-and-id-alignment.md`

**Material Changes**

- Kept YAML front matter as canonical machine-readable metadata and added a synchronized human-readable `Document Control` table below the H1 title.
- Applied the presentation to all 23 active YAML-backed documents without changing their substantive product requirements.
- Added synchronization and validation requirements to `AGENTS.md`, DOC-00, and the documentation change-integration workflow.
- Exempted empty placeholders until drafting begins and excluded backup files from mechanical presentation updates.
- Replaced the corrupted and stale DOC-00 repository-tree illustration with an ASCII representation aligned to the current repository, repaired lifecycle arrows, and corrected the DOC-22 title separator.

**Checks Performed**

- Verified all 23 active YAML-backed documents contain a `Document Control` table.
- Compared every YAML field against its table presentation and found zero mismatches.
- Verified all documented top-level repository areas exist.
- Ran `git diff --cached --check` before the substantive commit.
- Staged only the 26 approved files and preserved unrelated working-tree changes.

**Remaining Open Items**

- DOC-22 remains without YAML metadata or a control table because its formal metadata has not yet been defined.
- Empty DOC-16, DOC-17, DOC-19, DOC-20, DOC-21, AI-execution, policy, and template placeholders should receive YAML and a synchronized table when substantive drafting begins.

### `2026-07-22` - Account Information, Login Security, And Privacy Data Routes

| Field | Record |
| --- | --- |
| Substantive commit | `b5879e1` |
| Primary owner | `DOC-06B`, Me account child routes |
| Decision record | `DEC-2026-009` |
| Founder approval | Approved on `2026-07-22` |

**Files Changed**

- `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-15`, `DOC-18`, and `DOC-22`;
- app route-entry map;
- status-display reference matrix;
- open-questions register;
- requirements traceability matrix.

**Material Changes**

- Defined `ACCOUNT-PROFILE`, `ACCOUNT-SECURITY`, and `PRIVACY-DATA-CONTROLS` as distinct Me child routes.
- Defined reusable `IDENTITY-VERIFICATION` and child screen `PAYMENT-PASSCODE-SETTINGS` without creating additional root routes.
- Confirmed identity-verification display labels, `Verify Now` behavior, immutable login name, copyable PayPlus User ID, cross-channel contact changes, trusted-device removal, security-toggle boundaries, account closure, privacy choices, privacy-request labels, and protected in-app export.
- Aligned notifications, disclosures, privacy rules, acceptance coverage, future data/admin requirements, traceability, open questions, status mapping, and navigation visualization.
- Removed the unrelated Dashboard shortcut/More box from the Me route handoff diagram.

**Checks Performed**

- Verified DOC-06B remains the sole route-level UX owner and reference documents do not redefine its screen behavior.
- Verified YAML and Document Control metadata synchronization for all edited formal documents.
- Checked the route register, return behavior, status-display mappings, Mermaid fence balance, stale wording, and duplicate route/status risks.
- Ran `git diff --cached --check` and staged only the 13 approved files.

**Remaining Open Items**

- Final identity-provider/backend state mapping and provider-returned metadata.
- Final DOC-19 authentication, recovery, retry, lockout, and session mechanics.
- Detailed account-closure visual design and operational finalization.
- Privacy-request service timelines and export format.
- Remaining Me child-route and final visual-design work.

### `2026-07-26` - Receiving Info, Canonical Request States, And Documentation Integration Controls

| Field | Record |
| --- | --- |
| Substantive commit | `88c7c33` |
| Primary owner | `DOC-06A`, request lifecycle; `DOC-06B`, Receiving Info and route UX; `DOC-10`, payout destination; `DOC-00`, documentation governance |
| Decision record | `DEC-2026-010`, `DEC-2026-011`, `DEC-2026-012`, `DEC-2026-013` |
| Founder approval | Decisions and final commit scope approved on `2026-07-26` |

**Files Changed**

- `AGENTS.md`;
- `DOC-00` to `DOC-12` where materially affected, plus `DOC-14`, `DOC-15`, `DOC-18`, and `DOC-22`;
- Documentation Change Integration and Prototype Design and Validation workflows;
- documentation and diagram indexes, route-entry Mermaid map, glossary, and prototype lifecycle registry;
- open-questions register, requirements traceability matrix, route register, and status-display reference matrix.

**Material Changes**

- Replaced mixed request-status definitions with the canonical request lifecycle and role-facing labels.
- Separated request events, evidence status, obligation readiness, payment/payout status, linked-case lifecycle, and archive visibility.
- Confirmed the direct payer-created evidence-to-obligation path and that payee-created request acceptance remains separate from payment authorization.
- Replaced singular Receiving Details with multiple private, reusable Receiving Info profiles and immutable destination snapshots.
- Defined Receiving Info readiness, masking, proof, versioning, archive, change, notification, and payer-authorization-freeze rules.
- Clarified authentication for prominent sensitive-data reveal and material sensitive changes while retaining ordinary permitted document view/download without an extra prompt.
- Added the canonical route register, expanded glossary and traceability, synchronized DOC-06 family completion status, and aligned the route map.
- Added task-level impact-manifest, parent/family synchronization, batched validation, and prototype lifecycle controls.
- Registered no current prototype and excluded stale or unvalidated visual artifacts from the substantive commit.

**Checks Performed**

- Audited all tracked and untracked workspace changes and staged only the 33 approved files.
- Verified active request, evidence, readiness, case, payment, payout, archive, Receiving Info, and sensitive-data terminology.
- Checked route ownership, DOC-06 parent/child status, route register, status matrix, glossary, traceability, open questions, and Mermaid handoffs.
- Verified local Markdown links and ran `git diff --cached --check`.
- Excluded the external `for-neng` derivative, remote attachments, stale JPG exports, stale simplified user-flow diagrams, and unvalidated prototype.

**Remaining Open Items**

- Final Receiving Info method fields, external validation, matching, proof, review, failure mapping, and technical/admin design.
- Final request-state physical schema, reason codes, event payloads, and operational limits.
- Final DOC-19 authentication, step-up, session, recovery, and security implementation.
- `ARCHIVED-EVIDENCE-LIST`, Support/About/Terms, Home/More/Notification Inbox IDs, checkout destination IDs, and final visual design.
- No prototype is a current validated reference; future prototype work must use the new workflow.

### `2026-07-26` - Archive Route Family And Hierarchical Route Maps

| Field | Record |
| --- | --- |
| Substantive commit | `9dc8015` |
| Primary owner | `DOC-06B`, archive navigation; `DOC-06C`, Bills/rent archive behavior; `DOC-00`, diagram governance |
| Decision record | `DEC-2026-014`, `DEC-2026-015` |
| Founder approval | Archive model, restore rules, and hierarchical diagram approach approved on `2026-07-26` |

**Files Changed**

- `AGENTS.md`, `DOC-00`, and the Documentation Change Integration Workflow;
- `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06C`, `DOC-06D`, and `DOC-08`;
- `DOC-09`, `DOC-10`, `DOC-11`, `DOC-12`, `DOC-14`, `DOC-15`, `DOC-18`, and `DOC-22`;
- diagram and supporting README files, ten current route-family maps, and one archived prior route map;
- glossary, open-questions register, requirements traceability matrix, route register, and status-display reference matrix.

**Material Changes**

- Defined `ARCHIVED-ROOT`, `ARCHIVED-BILLS-LIST`, and their relationship with `ARCHIVED-DOCS-LIST`.
- Defined archive list behavior, search, filters, cards, archived read-only detail, archive eligibility, restore eligibility, blockers, reminder effects, and evidence restoration.
- Established archive as a per-user projection that does not alter canonical obligations, counterparty records, party linkage, completed history, or operational snapshots.
- Prevented independent archive of the sole current evidence and retained replaced evidence as non-restorable previous versions.
- Aligned notification, payment, payout, refund, dispute, risk, evidence, privacy, data, and admin boundaries.
- Replaced the all-in-one route map with an app-level map and route-family maps while preserving the former map as a dated superseded snapshot.
- Added hierarchical route-diagram rules to repository guidance and integration workflow.
- Updated the route register, status-display reference, requirements traceability, glossary, and open-question disposition.

**Checks Performed**

- Staged only the 37 approved files and preserved unrelated workspace changes.
- Verified YAML and Document Control version parity for edited formal documents.
- Verified archive route IDs against the route register and DOC-06 owning documents.
- Checked active route-map Mermaid fences and stale active-route references.
- Ran `git diff --cached --check`.
- Confirmed the prototype remains a non-authoritative review draft requiring archive-family alignment.

**Remaining Open Items**

- Final archive visual design and a source-aligned interactive prototype.
- Final `DOC-18` schema, projection, event, lineage, and blocker-evaluation design.
- Final `DOC-22` admin workflow, including restore-on-behalf controls and formal metadata.
- Full Mermaid rendering was not run because Mermaid CLI is not installed locally; structural checks passed.

### `2026-07-27` - Pay+ Action Sheet And Request-Direction Alignment

| Field | Record |
| --- | --- |
| Substantive commit | `cd75183` |
| Primary owner | `DOC-06B`, Pay+ action-sheet behavior and route handoffs |
| Decision record | `DEC-2026-016` |
| Founder approval | Pay+ principles, request directions, alignment scope, and commit approved on `2026-07-27` |

**Files Changed**

- `DOC-01` to `DOC-09` where materially affected, plus `DOC-12`, `DOC-18`, and `DOC-22`;
- DOC-06 parent, route, Bills, and UX-acceptance family documents;
- diagram index, app/Home/Instructions/Requests maps, and the new Pay+ action-sheet map;
- open-questions register, requirements traceability matrix, and route register.

**Material Changes**

- Defined `PAYPLUS-ACTION-SHEET` as a slide-up sheet with five MVP actions arranged in two rows: `Pay a Bill`, `Pay Rent`, `Add Bill / Rent`, `Continue Payment`, and `Request Payment`.
- Defined category-scoped Bills handoffs, readiness-aware setup completion, zero/one/many instruction routing, visible review-blocked instructions, return behavior, availability rules, duplicate prevention, reduced motion, and future admin controls.
- Confirmed Pay+ `Request Payment` as a payee-to-payer payment-request entry.
- Separated optional contextual payer-to-payee linking requests from payee-created payment requests and from direct payer-created obligations/payments.
- Replaced active wording that incorrectly treated payer-created payment as a payer-created payment request.
- Added the dedicated hierarchical Pay+ route map and aligned parent and route-family diagrams.

**Checks Performed**

- Staged only the 25 approved files and preserved unrelated workspace changes.
- Verified active request-direction and payer-created-payment terminology.
- Verified YAML and Document Control metadata parity for materially edited formal documents.
- Checked route-register, traceability, open-question, notification, acceptance, data, and admin handoffs.
- Ran `git diff --cached --check`; Mermaid structure passed, while full rendering remained unavailable because Mermaid CLI is not installed locally.

**Remaining Open Items**

- Exact Pay+ iconography, dimensions, spacing, blur strength, animation timing/easing, final styling, and future added-button layout.
- Final DOC-18 event payloads and DOC-22 admin screen, permission, and implementation-field design.
