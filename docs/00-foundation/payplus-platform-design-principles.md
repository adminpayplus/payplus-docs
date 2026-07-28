# PayPlus Platform Design Principles

Last updated: 2026-07-29

## 1. Purpose

This document defines reusable platform design principles for PayPlus. It provides a common decision baseline for product, journey, payment, risk, compliance, privacy, security, engineering, operations, and AI-assisted documentation work.

These principles guide design decisions across features and workflows. They do not replace the detailed requirements, controls, acceptance criteria, or implementation specifications owned by the applicable PayPlus documents.

## 2. Scope

These principles apply across PayPlus, including:

- authentication, account activation, recovery, and access control;
- navigation, interrupted journeys, and protected workflow continuation;
- bills, rent, payment, payout, refund, dispute, and reconciliation;
- evidence, verification, risk, compliance, privacy, and fraud controls;
- notifications, receipts, support, admin, and operational workflows;
- technical specifications and AI build-execution materials derived from approved source documents.

Where a principle requires feature-specific behavior, the applicable domain document must define that behavior and remain its primary source of truth.

## 3. Governance

- `DOC-00 Documentation Governance` governs document authority, status, ownership, change control, and source-of-truth precedence.
- This document is a repository-wide design reference. It does not override an approved formal requirement or specialist control.
- Each detailed rule must have one primary owning document. Other documents should reference that owner rather than duplicate or reinterpret the rule.
- Conflicts, exceptions, or material deviations must be identified and resolved through the applicable owner and approval process.
- New principles require founder approval and should be added only when they are reusable across multiple PayPlus domains.
- Downstream technical and AI execution documents must derive from approved human-readable sources and must not introduce new product or policy decisions.

## 4. Core Principles

### PP-DP-01 - Preserve Navigation Context, Never Security State

PayPlus may preserve only the minimum navigation or workflow context required to help a user return to an intended destination.

Preserved context must never bypass or carry forward authentication, authorization, activation, eligibility, payment validation, evidence, fraud, privacy, compliance, or other security decisions. Sensitive context must be minimized, protected, time-bounded, and discarded when no longer required.

### PP-DP-02 - Revalidate Before Protected Continuation

Before continuing any protected workflow, PayPlus must revalidate the user, current permissions, workflow state, destination, and applicable security and domain gates.

Previous success, cached state, a saved destination, or completion of a related step must not be treated as proof that the user or workflow remains eligible to continue.

### PP-DP-03 - Make Resume, Restart, Redirect, Wait, and Stop Explicit

An interrupted or blocked flow must have an explicit resolution.

PayPlus must distinguish between:

- **Resume**, where the prior workflow state remains valid and can safely continue;
- **Restart**, where the workflow must begin again because required state is missing, expired, invalid, consumed, or no longer trusted;
- **Redirect**, where the user must move to another valid workflow, authentication method, support path, or security review;
- **Wait**, where a temporary review, reconciliation, service, or security condition prevents immediate continuation; and
- **Stop**, where no approved continuation or recovery path remains.

The user-facing action and destination must reflect the current system decision. A flow must not silently continue from stale or partially trusted state.

### PP-DP-04 - Separate Outcome, Resolution, Message, and Notification

PayPlus must treat the following as separate concepts:

- **Outcome** - the authoritative result produced by a workflow or evaluation;
- **Resolution Strategy** - the safe next handling permitted after considering the outcome, current context, user capability, and governing controls;
- **Message** - the in-context explanation presented to the user; and
- **Notification** - an out-of-context communication delivered through an approved channel when required.

A resolution must not create a new persistent status by itself. A message or notification must represent the owning outcome and resolution accurately and must not create, change, or imply a system state that the owning workflow did not produce.

### PP-DP-05 - Resolve by Permitted Capability, Not Raw Error Alone

Where more than one valid continuation method may exist, PayPlus should evaluate the capabilities the user is permitted to use and select or present the safest usable path.

Capability-aware handling must not:

- reveal whether an account or login method exists before the required assurance;
- treat a remembered device, phone number, or identity record as sufficient proof unless the owning security specification permits it;
- bypass authentication, authorization, activation, risk, privacy, or compliance controls;
- force a silent redirect where the user must understand or choose the next action; or
- guarantee recovery when approved ownership evidence cannot be established.

The route or domain owner defines the permitted resolution strategies. DOC-07 defines their user-facing message and CTA mapping. DOC-19 and other specialist owners define the security and technical controls.

### PP-DP-06 - Maintain One Source of Truth and One Primary Owner

Each material rule, state, decision, route, workflow, control, or data definition must have one primary owning document or governed register.

Reference documents may summarize, link, or define handoffs, but must not maintain a competing definition. When ownership is unclear, ownership must be resolved before detailed requirements are drafted or changed.

### PP-DP-07 - Apply Security First with Proportionate Usability

PayPlus must protect authorization, funds, evidence, identity, personal data, and regulated workflows without creating avoidable user confusion or dead ends.

Usability may simplify explanation, navigation, and recovery, but must not weaken required security, risk, privacy, compliance, or payment controls. Security decisions should provide the safest clear next action that may be disclosed to the user.

### PP-DP-08 - Gate Features and Capabilities Modularly

Features and capabilities should be enabled, restricted, or withheld through explicit, independently governed gates where practical.

Eligibility, jurisdiction, partner readiness, account state, role, risk, compliance, operational readiness, and rollout status may affect availability. A feature being visible, configured, or technically deployed does not by itself make it authorized for use.

Gates must fail safely and must not create an unintended alternate path around an unavailable control.

### PP-DP-09 - Make Material Operations Idempotent Where Applicable

Operations that may be retried, repeated, resumed, or delivered more than once should be designed so that the same valid instruction does not create unintended duplicate effects.

This principle is particularly important for payment instructions, refunds, payouts, notifications, webhook processing, evidence submission, and administrative actions. The owning technical or domain specification must define the applicable identity, retry, deduplication, and conflict rules.

### PP-DP-10 - Design for Auditability

Material decisions and actions must be attributable and reconstructable to the degree required by their risk, regulatory, security, financial, privacy, and operational significance.

Audit design should identify the actor or system, action, time, relevant object, decision, outcome, resolution, and governing context without exposing unnecessary sensitive data. Audit records must not be treated as a substitute for the authoritative business state.

### PP-DP-11 - Preserve End-to-End Traceability

Material platform behavior must be traceable from the approved principle or requirement to its owning specification, outcome, resolution, controls, decisions, acceptance criteria, tests, operational evidence, and implementation reference where applicable.

Derived documents and implementation artifacts must link back to their authoritative sources. Traceability must expose unresolved decisions and deferred work rather than conceal them through assumptions.

## 5. Outcome Architecture Reference

PP-DP-04 establishes the durable principle that Outcome, Resolution Strategy, Message/CTA, and Notification are separate concepts. The detailed canonical chain, definitions, mappings, traceability fields, and acceptance model are owned by the [`PayPlus Outcome, Resolution, Message and Notification Framework`](payplus-outcome-message-notification-framework.md). This principles document must not maintain a competing copy of that detailed framework.

## 6. Application Rule

When designing or reviewing a feature or workflow:

1. identify the primary owner and authoritative source rule;
2. determine which principles apply;
3. identify the decision or evaluation and its possible outcomes;
4. distinguish persistent status changes from operation outcomes;
5. define the permitted resolution strategies, including resume, restart, redirect, wait, support, or stop where applicable;
6. identify required security, risk, privacy, compliance, payment, and operational gates;
7. align messages, CTAs, and notifications to the authoritative outcome and resolution;
8. define audit and traceability expectations proportionate to the decision;
9. record unresolved conflicts or exceptions for approval.

Principles should be referenced by ID where this improves clarity. They should not be copied into downstream documents as competing requirements.

## 7. Interpretation

These principles define design intent, not implementation architecture. The owning formal documents define the detailed requirement, control, status model, data rule, API behavior, test, or operational procedure.

Where two principles appear to conflict, PayPlus must preserve security, authorization, regulatory, privacy, and payment integrity first, then select the clearest usable path within those boundaries.
