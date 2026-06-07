
# Agent Context Index

This index identifies AI context files and whether they are current.

Status: `Reserved / not active for build execution`.

## Context Files

| File | Status | Use |
| --- | --- | --- |
| `context/project-continuation-context.md` | Legacy / non-authoritative | Do not use as source of truth unless refreshed from current formal docs and approved. |

## Current Source Documents

For context, read current formal documents instead:

- `DOC-00` to `DOC-04` for foundation, business, regulatory, and compliance control baseline.
- `DOC-05` to `DOC-08` for product, UX, disclosure, notification, and communication behavior.
- `DOC-09` to `DOC-11` for payment, payout, reconciliation, refund, cancellation, dispute, and chargeback behavior.
- `DOC-12` to `DOC-15` for evidence verification, promotion engine, risk controls, privacy, data classification, and retention.
- `DOC-16` to `DOC-22` when drafted for technical architecture, integrations, data model, security, testing, monitoring, and admin operations.
- `DOC-18` for the current technical baseline on data model, transaction state, audit events, reporting, and AI-ready data-engine requirements.
- `docs/04-growth-ecosystem/payplus-data-strategy-ai-marketing-research.md` only as supporting research context for AI/data-engine strategy; it does not override formal DOC-XX requirements.

## Regeneration Rule

When AI build-execution conversion starts, regenerate context from the current formal documents and traceability registers. Carry forward the AI/data-engine boundary that PayPlus must not be implemented as an ad network, data broker, credit scoring product, insurance underwriting product, or offsite audience activation platform unless a future approved source document changes that scope. Do not carry forward old context blindly.
