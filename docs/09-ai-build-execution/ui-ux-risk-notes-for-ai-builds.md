# PayPlus UI/UX Directional Notes for Future AI Builds

Status: Directional reference only

Source of truth: Formal `DOC-XX` documents, approved decision records, traceability registers, and approved technical specifications remain authoritative.

This note does not activate AI build execution. It must not override formal PayPlus product, payment, risk, compliance, privacy, engineering, security, QA, release, or operations documents.

---

## Purpose

This note captures UI/UX risks observed from reviewing AI-assisted product builds.

It is intended as a future reference for PayPlus AI build-execution materials, especially UI prototype PRDs, prompt packs, coding rules, and definitions of done.

It is not a final UI specification, brand guide, design system, or implementation instruction.

---

## Core Warning

AI builders can produce broad functional coverage while still defaulting to generic responsive web application patterns.

Common defaults include:

- sidebars;
- dashboard cards;
- boxed sections;
- basic tab groups;
- generic tables;
- status badges;
- modal forms;
- repeated card layouts;
- simple responsive stacking.

These patterns can make an app look complete while still lacking strong workflow design, information hierarchy, operational density, product-specific judgment, and payment-control clarity.

For PayPlus, functional breadth is not enough. The interface must support controlled bill, fee, rent, and approved-payee payment workflows with evidence, payer authorization, payee verification, risk controls, auditability, reconciliation, and operational oversight.

---

## Avoid

Future AI build materials should caution AI agents against:

- treating dashboard cards as a substitute for workflow clarity;
- using generic SaaS layouts for payment-control, risk-review, or audit workflows;
- overusing cards, boxes, tabs, and decorative panels;
- making every feature equally visible without prioritizing the next required action;
- designing admin, review, compliance, or operations screens like marketing pages;
- hiding evidence, authorization, payee verification, risk status, audit history, or reconciliation context behind too many clicks;
- allowing UI labels to imply unsupported legal, regulatory, compliance, payment, or risk conclusions;
- using vague status labels where controlled payment, verification, or exception states are required;
- presenting payment movement as casual wallet, cashout, peer-to-peer transfer, remittance, lending, or cash-advance behavior;
- letting AI invent visual hierarchy without product-specific UX direction;
- relying on responsive layout alone as proof of usability;
- accepting screens that look polished but do not expose the controls, evidence, exceptions, and audit context needed for safe operations.

---

## Prefer

Future AI build materials should encourage:

- workflow-first screens;
- clear payment-request and obligation status;
- visible evidence and authorization context;
- visible payee verification and approved-purpose context;
- prominent risk, exception, hold, review, refund, chargeback, and reconciliation states;
- dense but readable admin and operations layouts;
- calm, controlled, audit-ready visual tone;
- payer-facing simplicity without removing required disclosures, authorization, or confirmation context;
- operations-facing detail for review, approval, investigation, reconciliation, and incident handling;
- clear separation between user-facing actions and internal review controls;
- field-level visibility and masking aligned with privacy and approved-purpose access rules;
- UI decisions traceable to product, payment-domain, risk, privacy, security, and operations documents.

---

## Future Use

When the founder confirms that PayPlus human-readable and technical documentation is mature enough for AI build execution, this note should be reviewed and converted into concrete UI/UX execution requirements where appropriate.

Potential downstream uses include:

- UI prototype PRD guardrails;
- AI prompt-pack instructions;
- agent coding rules;
- definition-of-done criteria;
- review checklists for generated screens;
- QA checks for workflow clarity, evidence visibility, role visibility, and audit context.

Until then, this note remains directional reference only.
