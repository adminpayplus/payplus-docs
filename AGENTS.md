# AGENTS.md

## Purpose

This file gives AI assistants working in this repository a shared operating guide.

PayPlus documentation must be developed in two stages:

1. Human-readable source-of-truth documentation.
2. AI-coding-friendly execution documentation derived from the human docs.

Do not reverse this order unless the founder explicitly approves it.

## Repository Context

PayPlus is a controlled bill, fee, rent, and approved-payee payment application.

The product is intended to support eligible real-world bills or approved payment obligations, with evidence, payer authorization, payee verification, risk controls, auditability, reconciliation, and operational oversight.

PayPlus must not be casually described or designed as:

- a wallet;
- a stored-value account;
- an unrestricted peer-to-peer transfer app;
- a cashout product;
- a remittance product;
- a lending product;
- a cash advance product;
- an open money-request marketplace.

If any future feature appears to move PayPlus toward one of those models, flag it as a risk or open question instead of treating it as approved scope.

## Source of Truth

Use `docs/00-foundation/doc-00-documentation-governance.md` as the primary documentation governance guide.

When sources conflict, follow the source-of-truth hierarchy in `DOC-00`.

In general:

1. Approved formal `DOC-XX` documents win.
2. Draft formal documents guide discussion but are not final authority.
3. AI build-execution files support implementation but must not override human source documents.
4. Backup files are not authoritative.
5. Chat history is useful context but must not override repository documents.

## Current Documentation Strategy

The intended documentation flow is:

```text
Human source docs -> AI execution docs -> implementation tasks -> tests/evidence -> traceability updates
```

Use these repository areas as follows:

- `docs/00-foundation/`: governance, product positioning, business model, regulatory and compliance foundation.
- `docs/01-product/`: product requirements, user journeys, disclosures, notifications, and user-facing behavior.
- `docs/02-payment-domain/`: payment, funding, payout, reconciliation, refund, cancellation, and chargeback behavior.
- `docs/03-bill-verification/`: bill categories, evidence, document AI/OCR, and payee verification.
- `docs/04-growth-ecosystem/`: promotions, coupons, referrals, memberships, and growth features.
- `docs/05-risk-compliance-privacy/`: AML, anti-cashout, fraud, privacy, and retention.
- `docs/06-engineering/`: architecture, APIs, data model, transaction states, and audit events.
- `docs/07-security-access-control/`: security, tokenization, authentication, access control, and admin controls.
- `docs/08-qa-release-operations/`: testing, UAT, go-live, monitoring, incidents, and operations.
- `docs/09-ai-build-execution/`: AI build-execution materials derived from human docs.
- `docs/99-isms-policies/`: ISMS and security policy library.
- `docs/traceability/`: requirements, controls, tests, decisions, and open-question linkage.

## Agent Workflow Rules

Before making broad documentation changes:

1. Check the current workspace path.
2. Check `git status --short --branch`.
3. Review the relevant source documents before editing.
4. Identify whether the requested work is review-only, drafting, rewriting, or AI-execution conversion.
5. Preserve existing useful content.
6. Flag contradictions, missing decisions, and open questions.
7. Ask for founder confirmation before committing changes.

Do not commit, push, create pull requests, or mark documents as approved unless the founder explicitly asks for that action.

## Writing Standards

Write PayPlus documents in clear, professional, human-readable Markdown.

Prefer:

- precise fintech, payments, compliance, risk, security, and operations language;
- concise paragraphs;
- tables where they improve scanability;
- stable IDs for requirements, risks, controls, decisions, tests, and open questions;
- explicit `TBD`, `Open`, or `To be confirmed` markers where facts are unknown;
- practical launch-readiness and implementation-readiness language.

Avoid:

- unsupported regulatory conclusions;
- invented partner capabilities;
- invented legal advice;
- vague claims such as "fully compliant" or "bank-grade" unless supported by formal review;
- moving unapproved assumptions into requirements;
- treating AI build files as source-of-truth documents.

## Formal Document Expectations

Formal `DOC-XX` files should generally follow `DOC-00` governance and include:

- YAML front matter where the document already uses it or where a new formal document is being created;
- document ID;
- title;
- version;
- status;
- owner;
- reviewers;
- approvers;
- last updated date;
- classification;
- related documents;
- purpose;
- scope;
- requirements, rules, controls, or flows as appropriate;
- open questions;
- acceptance criteria;
- version history.

When editing an existing document, preserve its established format unless the task is specifically to standardize format.

## Compliance and Risk Caution

PayPlus is a payments-adjacent product with regulatory, card network, PSP/acquirer, AML, privacy, security, fraud, chargeback, and consumer-protection implications.

Agents must:

- distinguish product intent from legal conclusion;
- use "requires assessment", "subject to approval", or "to be confirmed" where decisions are unresolved;
- flag jurisdiction, PSP/acquirer, card network, payout, KYC/KYB, AML, privacy, PCI, and retention questions;
- avoid giving final legal, regulatory, tax, or compliance advice;
- keep evidence, authorization, payee verification, anti-cashout, audit, and reconciliation controls visible in relevant docs.

## Human Docs Before AI Coding Docs

Do not start converting documents into AI-coding-friendly implementation prompts until the founder confirms that the human-readable documentation set is complete enough.

When conversion is approved, AI execution docs must:

- cite or link back to their human source documents;
- preserve product boundaries and prohibited behaviors;
- keep open questions visible;
- separate confirmed requirements from assumptions;
- include test and traceability expectations.

## Recommended Review Output

When asked to review documentation, provide:

1. High-priority issues.
2. Cross-document inconsistencies.
3. Missing documents or empty placeholders.
4. Recommended drafting order.
5. Suggested edits or rewrite scope.
6. Open questions for the founder.

Do not make large rewrites unless the founder asks for direct file edits.

## Git and Change Safety

This repository may contain user edits.

Agents must not discard or revert user changes unless explicitly asked.

Before finishing any edit session, report:

- files changed;
- checks performed;
- material recommendations;
- whether changes were committed.

Commits require explicit founder confirmation.
