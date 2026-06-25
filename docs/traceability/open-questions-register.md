
# Open Questions Register

This register summarizes cross-document open-question groups. Document-specific open questions remain in the owning `DOC-XX` files and should be linked here when they become launch blockers, architecture blockers, legal blockers, or implementation blockers.

Status values: `Open`, `In Review`, `Decided`, `Deferred`, `Superseded`.

## Cross-Document Open Questions

| ID | Topic | Summary | Primary Owner | Source Docs | Status |
| --- | --- | --- | --- | --- | --- |
| OQ-XDOC-001 | Hong Kong launch requirements | Confirm final legal, regulatory, privacy, tax, accounting, partner, and operational requirements for the first market. | Legal / Compliance / Finance | DOC-01, DOC-03, DOC-04, DOC-15 | Open |
| OQ-XDOC-002 | PSP/acquirer and transaction classification | Confirm PSP/acquirer, MCC or special classification, card network treatment, and whether PayPlus transactions are accepted as bill payment or ordinary online card purchase. | Payments / Legal / Compliance | DOC-01, DOC-03, DOC-04, DOC-09 | Open |
| OQ-XDOC-003 | Payout rails and settlement operations | Confirm operating bank setup, FPS, cheque, EPS applicability, payout files/API, settlement timing, cutoff rules, holiday handling, and exception process. | Payments / Finance / Operations | DOC-01, DOC-03, DOC-04, DOC-10, DOC-17, DOC-22 | Open |
| OQ-XDOC-004 | MVP category launch gates | Confirm which MVP categories are enabled at initial launch and the evidence, limit, review, payout, and privacy gates for each category. | Product / Compliance / Risk | DOC-01, DOC-04, DOC-05, DOC-12, DOC-14 | Open |
| OQ-XDOC-005 | KYC/KYB and screening depth | Confirm final provider, check depth, sanctions screening, risk-tier exceptions, payee capability rules, and change-review rules. | Compliance / Risk / Operations | DOC-03, DOC-04, DOC-12, DOC-14, DOC-15, DOC-19 | Open |
| OQ-XDOC-006 | Fee and promotion treatment | Confirm fee rates, payer/payee allocation, subsidies, coupons, vouchers, promo codes, campaign budgets, reversals, and refund fee treatment. | Commercial / Finance / Product | DOC-02, DOC-05, DOC-09, DOC-11, DOC-13 | Open |
| OQ-XDOC-007 | User payment instruction details | Confirm validity windows, reminder schedule, expiry, quote reservation, quote revalidation, changed-term confirmation, partial funding, and partial payout operations. | Product / Payments / Operations | DOC-05, DOC-06, DOC-06A, DOC-06B, DOC-06C, DOC-07, DOC-08, DOC-09, DOC-10, DOC-11, DOC-13, DOC-14, DOC-18, DOC-22 | Open |
| OQ-XDOC-008 | Refund, dispute, cancellation, reversal, chargeback policy | Define operating policy details, reason-code handling, evidence packages, liability, payout hold/recovery, and user-facing wording. | Operations / Payments / Legal | DOC-07, DOC-08, DOC-10, DOC-11, DOC-14, DOC-21, DOC-22 | Open |
| OQ-XDOC-009 | Privacy and data classification implementation | Confirm field-level data classification, masking, approved-purpose access, retention/deletion exceptions, analytics use, partner sharing, and admin visibility. | Privacy / Security / Engineering | DOC-06, DOC-06A, DOC-06B, DOC-06C, DOC-06D, DOC-12, DOC-13, DOC-14, DOC-15, DOC-18, DOC-19, DOC-22 | Open |
| OQ-XDOC-010 | Technical specification readiness | Draft DOC-16 to DOC-22 and align architecture, integrations, data model, security, testing, monitoring, and admin operations with human source docs. | Engineering / Product / Operations | DOC-16, DOC-17, DOC-18, DOC-19, DOC-20, DOC-21, DOC-22 | Open |
| OQ-XDOC-011 | Home dashboard, navigation, shortcuts, and placements | Confirm Pay+ action sheet actions, route-level IA, shortcut cap/reorder/default behavior, Important Notice rules, Featured carousel rules, placement targeting, and privacy/consent treatment. | Product / Design / Growth / Privacy / Operations | DOC-05, DOC-06, DOC-06B, DOC-08, DOC-13, DOC-15, DOC-22 | Open |
| OQ-XDOC-012 | AI-ready data engine and model governance | Partial baseline is defined in DOC-18 and supporting research context. Confirm final event taxonomy, data lineage format, feature/model metadata, approved model purposes, prohibited inputs, consent/preference dependencies, partner-reporting boundaries, aggregation thresholds, and external activation gates. | Product / Data / Privacy / Risk / Engineering | DOC-01, DOC-05, DOC-12, DOC-13, DOC-14, DOC-15, DOC-18, DOC-19; supporting research memo | Open |
| OQ-XDOC-013 | Bills tab, activity, evidence source selection, and participant linking | Confirm final Bills tab visual layout, role-aware `BILLS-PAY` / `BILLS-RECEIVE` card and detail actions, payee-side request/remind-payer behavior, bill/rent-specific activity timeline and activity-detail behavior, evidence-source selection UI, DOC-06C evidence detail/upload route behavior, evidence status/payment-readiness mapping, archived evidence retrieval route, user-initiated payee linking/invitation mechanism, no-auto-matching privacy controls, and technical object/event model. | Product / Design / Privacy / Engineering | DOC-05, DOC-06, DOC-06C, DOC-06D, DOC-08, DOC-12, DOC-15, DOC-18, DOC-19, DOC-22 | Open |
| OQ-XDOC-015 | Checkout UI ownership and route handoff | Confirm whether detailed payment/checkout UI specification remains in DOC-09, with DOC-06 limited to route entry and handoff, or whether a future lightweight DOC-06 checkout shell is needed for navigation consistency. | Product / Design / Payments / Engineering | DOC-06, DOC-06A, DOC-06B, DOC-06C, DOC-07, DOC-08, DOC-09, DOC-13, DOC-15, DOC-18, DOC-19 | Open |
| OQ-XDOC-014 | Reminder management and payment instruction reminder placement | Confirm whether deferred payment instruction reminders should appear in DOC-06C reminder management, or remain only under Instructions, dashboard action-required surfaces, and the DOC-09 checkout/payment instruction flow. | Product / Design / Payments / Operations | DOC-05, DOC-06, DOC-06B, DOC-06C, DOC-08, DOC-09, DOC-18, DOC-22 | Open |

## Maintenance Rules

- Keep detailed questions in the owning document.
- Add a cross-document entry here when a question affects more than one document or blocks launch/architecture.
- Close or supersede entries only when the owning source documents have been updated.
- Do not use old chat history or AI context files as final decision evidence unless the decision is reflected in formal docs.
