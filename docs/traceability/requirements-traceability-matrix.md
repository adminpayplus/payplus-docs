
# Requirements Traceability Matrix

This starter matrix links major PayPlus requirement areas to source documents, future technical specifications, and expected verification evidence.

Detailed requirement IDs should be expanded when DOC-16 to DOC-22 are drafted and when implementation tickets, tests, controls, and release evidence are created.

## Traceability Matrix

| Requirement Area | Human Source Docs | Technical / Operational Owner Docs | Expected Verification Evidence |
| --- | --- | --- | --- |
| Documentation governance and source of truth | DOC-00 | AGENTS.md, docs/README.md | Document register, version history, review notes, approved changes. |
| Product positioning and prohibited models | DOC-01, DOC-03, DOC-04 | DOC-05, DOC-06, DOC-07, DOC-14, DOC-19 | UX review, disclosure review, blocked-flow tests, risk-control tests. |
| Home dashboard, navigation, shortcuts, and placements | DOC-05, DOC-06, DOC-08, DOC-13, DOC-15 | DOC-18, DOC-20, DOC-22 | UX review, wireframe review, shortcut configuration tests, user preference tests, placement approval tests, dashboard task tests. |
| Bills tab, obligation management, evidence source selection, and participant linking | DOC-05, DOC-06, DOC-08, DOC-12, DOC-15 | DOC-18, DOC-19, DOC-20, DOC-22 | Bills route UX review, card/detail/action-required tests, evidence-source tests, participant-linking privacy tests, no-auto-matching tests, audit-event evidence. |
| MVP category support and gating | DOC-01, DOC-04, DOC-05, DOC-12, DOC-14 | DOC-18, DOC-20, DOC-22 | Category config, evidence matrix, review queue tests, launch gate evidence. |
| Payee-created requests | DOC-01, DOC-03, DOC-04, DOC-05, DOC-06, DOC-07 | DOC-09, DOC-10, DOC-11, DOC-18, DOC-20, DOC-22 | Request lifecycle tests, authorization logs, visibility tests, admin review evidence. |
| User payment instruction and deferred funding | DOC-05, DOC-06, DOC-07, DOC-08, DOC-09 | DOC-10, DOC-11, DOC-13, DOC-14, DOC-18, DOC-20, DOC-22 | Payment-instruction state tests, reminder tests, quote revalidation tests, partial funding and payout evidence. |
| Multi-card / split-card payment | DOC-01, DOC-05, DOC-09 | DOC-10, DOC-13, DOC-14, DOC-18, DOC-20, DOC-22 | Funding-leg tests, settlement grouping tests, reconciliation evidence, risk-monitoring evidence. |
| Payout and reconciliation | DOC-02, DOC-03, DOC-04, DOC-10 | DOC-17, DOC-18, DOC-20, DOC-21, DOC-22 | Batch/API evidence, bank-feed/upload reconciliation, exception reports, payout audit logs. |
| Refund, cancellation, dispute, reversal, chargeback | DOC-07, DOC-08, DOC-10, DOC-11, DOC-14 | DOC-18, DOC-20, DOC-21, DOC-22 | Refund tests, chargeback case evidence, user notification logs, ledger entries. |
| Bill verification, OCR, evidence, and payee verification | DOC-05, DOC-06, DOC-12, DOC-14, DOC-15 | DOC-17, DOC-18, DOC-20, DOC-22 | OCR extraction tests, field-metadata tests, duplicate evidence tests, manual review evidence. |
| Promotion engine, coupon/voucher library, referral, membership | DOC-02, DOC-05, DOC-06, DOC-09, DOC-13, DOC-15 | DOC-18, DOC-20, DOC-22 | Promotion quote tests, eligibility tests, quota/budget tests, reward instrument records, reversal tests. |
| Risk, AML, anti-cashout, fraud, and dynamic auth | DOC-03, DOC-04, DOC-09, DOC-12, DOC-13, DOC-14 | DOC-18, DOC-19, DOC-20, DOC-21, DOC-22 | Risk-rule tests, step-up tests, payout hold evidence, alert/review case logs. |
| Privacy, data classification, masking, retention | DOC-06, DOC-12, DOC-13, DOC-14, DOC-15 | DOC-18, DOC-19, DOC-20, DOC-21, DOC-22 | Data inventory, RBAC tests, masking tests, retention schedule, access logs. |
| AI-ready data engine, analytics, model governance, and partner intelligence | DOC-01, DOC-05, DOC-12, DOC-13, DOC-14, DOC-15 | DOC-16, DOC-17, DOC-18, DOC-19, DOC-20, DOC-21, DOC-22 | Event taxonomy, field metadata tests, lineage tests, consent/preference tests, model-input registry, prohibited-input tests, aggregation/output-control evidence, partner-reporting approvals. |
| Authentication, tokenization, PCI, and admin access | DOC-09, DOC-15 | DOC-18, DOC-19, DOC-20, DOC-22 | Auth tests, tokenization evidence, PCI scope review, admin access review, audit logs. |
| Testing, release, monitoring, and operations | DOC-04, DOC-05, DOC-10, DOC-11, DOC-14, DOC-15 | DOC-20, DOC-21, DOC-22 | UAT pack, go-live checklist, monitoring dashboard, incident runbook, operational SOP evidence. |

## Expansion Rules

- Add stable requirement IDs before AI build-execution conversion.
- Link each requirement to one source document and all affected downstream specs.
- Link each implementation ticket, test case, migration, and release item back to a source requirement.
- Keep open questions visible; do not convert an open question into a confirmed requirement without updating the owning source document.
