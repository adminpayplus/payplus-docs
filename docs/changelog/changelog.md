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
