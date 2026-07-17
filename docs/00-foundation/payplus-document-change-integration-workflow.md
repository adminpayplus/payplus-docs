# PayPlus Documentation Change Integration and Commit Workflow

## 1. Purpose

This procedure governs how an accepted PayPlus documentation change becomes repository-consistent and commit-ready. It applies whether the change is produced by one agent, a Level 1 parallel-agent task, a Level 2 worktree drafting wave, or a founder edit.

This procedure supplements `DOC-00` and `AGENTS.md`. It does not replace their source-of-truth hierarchy, product-drafting method, approval rules, or Git controls.

## 2. Core Rule

Update the primary owning document first. Then identify and align only the governing, product, domain, reference, traceability, decision, acceptance, technical, operational, index, guidance, metadata, and visual files materially affected by that accepted change.

Checking a file does not mean it must be edited. Do not create mechanical reference churn, duplicate the owning requirement, or change unrelated content.

## 3. Applicability and Roles

Use this workflow for any material documentation change, including a new or revised requirement, route, screen, flow, status, policy, data rule, admin control, ownership boundary, or cross-document definition.

- The founder confirms product decisions and authorizes commits and pushes.
- The active lead agent acts as Change Integrator unless another owner is appointed.
- One document remains the primary source for each concept.
- Reference documents summarize or hand off; they must not redefine the primary rule.
- Parallel reviewers are optional and should be used when complexity or cross-document risk justifies them.

## 4. Integration Sequence

### 4.1 Confirm the Accepted Change

Before editing, record:

1. the accepted definition, requirement, or behavior;
2. the primary owning document and affected section;
3. the permitted edit scope;
4. unresolved items that remain `TBD`, `Open`, or `To be confirmed`;
5. whether the change replaces an existing definition;
6. whether unrelated changes are prohibited.

If the founder has not accepted the material product decision, return to proposal and review rather than beginning integration.

### 4.2 Update the Primary Owner

Edit the document that owns the behavior first.

- Preserve useful existing content that remains valid.
- Replace superseded requirements instead of adding a second competing rule.
- Keep assumptions and open decisions visibly distinct from confirmed requirements.
- Keep implementation detail in its proper documentation layer.
- Preserve established formatting and stable IDs unless the approved change requires otherwise.

### 4.3 Perform Repository Impact Search

Search the repository for:

- the previous definition and material terminology;
- route, destination, requirement, status, control, and decision IDs;
- relevant actors, roles, actions, and user flows;
- references to the primary owner;
- duplicated or contradictory definitions;
- diagrams and indexes presenting the affected concept.

Classify each relevant result as:

| Classification | Required treatment |
| --- | --- |
| Must update | The accepted change would otherwise leave the file inaccurate, contradictory, or incomplete. |
| Reference only | The file should point to the owner without restating detailed behavior. |
| Checked and unaffected | No edit is required; preserve the file. |
| Superseded | Replace or remove the obsolete definition so it no longer appears valid. |
| Confirmation required | Stop and return the conflict or ownership question to the founder. |

### 4.4 Check Governing and Domain Documents

Check the documents relevant to the change, which may include:

- `DOC-00` for governance, ownership, status, and structure;
- `DOC-01` for charter and product-positioning effects;
- `DOC-05` for product requirement, MVP, module, and role effects;
- parent `DOC-06` and applicable `DOC-06A` to `DOC-06D` for journey, route, Bills UX, and acceptance effects;
- the governing domain documents from `DOC-07` to `DOC-15`;
- `DOC-16` to `DOC-22` where drafted and materially affected;
- privacy, status-display, open-question, or other specialist owners required by `AGENTS.md`.

Do not update every listed document automatically. Edit only when the accepted change alters that document's governed content, handoff, acceptance coverage, or reference accuracy.

### 4.5 Check Shared Alignment Files

Check, where applicable:

- route register and transition tables;
- root and documentation indexes;
- root `README.md` and `docs/README.md`;
- `AGENTS.md`;
- glossary and naming references.

Apply these rules:

- Update `AGENTS.md` only when reusable agent behavior, drafting rules, workflow, or governance changes.
- Update README or index files only when structure, reading order, ownership, baseline status, or an important repository reference changes.
- Update route registers and transition tables when a destination, relationship, entry, handoff, or return behavior changes.
- Update glossary or naming references when an accepted term, route ID, actor name, or system/user-facing distinction changes.

### 4.6 Check Traceability, Decisions, and Open Questions

Check, where applicable:

- requirements traceability matrix;
- open-questions register;
- status-display reference matrix;
- decision log and changelog;
- relevant change request;
- requirement, control, decision, risk, and test links.

Apply these rules:

- Update traceability when requirement ownership, status, dependencies, controls, tests, decisions, or document references change.
- Update the open-questions register when an item is added, resolved, replaced, reopened, or materially reframed.
- Update status-display references when user-facing terminology or its system-state mapping changes.
- Update a decision record or change request when the accepted change implements, replaces, narrows, or closes it.
- Do not mark a question, decision, change request, control, or test complete without supporting source-document evidence.

### 4.7 Check Acceptance and Test Effects

Check applicable acceptance and test owners, including `DOC-06D`, future `DOC-20`, and requirements-to-test traceability when the change affects:

- user-visible behavior or route handoffs;
- roles, permissions, visibility, masking, or access;
- validation, eligibility, limits, or configurable rules;
- status transitions or action-required behavior;
- failure, retry, return, cancellation, exception, or recovery handling;
- notification, evidence, authorization, payout, or reconciliation outcomes.

Update acceptance coverage only after the governing requirement is accepted. Do not invent implementation-level test detail in an early human source document.

### 4.8 Check Downstream Technical, Operational, and Admin Owners

Check relevant drafted downstream owners when the accepted human requirement has a material effect, including:

- `DOC-16` for architecture and component boundaries;
- `DOC-17` for APIs and partner integrations;
- `DOC-18` for data objects, statuses, events, lineage, reporting, and AI-ready signals;
- `DOC-19` for security and access controls;
- `DOC-20` for testing and UAT;
- `DOC-21` for monitoring, incidents, and service operations;
- `DOC-22` for admin configuration, queues, review actions, thresholds, exceptions, and operational controls.

Where a downstream document is still a placeholder, do not infer or draft missing technical detail. Record a precise future-alignment requirement only where needed to prevent the accepted requirement from being lost.

Check `DOC-08` when the change creates or alters a notifiable event, deeplink destination, channel rule, user preference, or admin communication control. Check risk, privacy, compliance, and security owners when the change affects evidence, authorization, participant linking, personal data, masking, approved-purpose access, fraud, AML, tokenization, auditability, or retention.

### 4.9 Check Formal Document Metadata

For every materially edited formal document, check:

- related-document references;
- version and last-updated date;
- version history;
- document status;
- owner, reviewer, and approver fields;
- requirement and section IDs.

Update metadata according to `DOC-00`. Do not mark a document `Approved`, assign an approver, or close an approval gate without founder authorization and the required evidence.

### 4.10 Check Visual and UX Artifacts

Check designated current visual artifacts when the accepted change affects what they represent, including:

- Mermaid route diagrams;
- interactive prototypes;
- dashboard or route wireframes;
- screen-flow images;
- generated diagram exports.

Update only artifacts that are current, governed, and materially affected. Regenerate derived exports from their governing source where practical. Do not treat a prototype, screenshot, JPG, or exported diagram as an independent source of truth.

### 4.11 Check Derived AI and External Handoff Documents

Check derived AI execution materials only when that documentation layer is active and the founder has approved source-to-execution conversion. Human source changes must not trigger premature drafting of reserved or placeholder AI execution files.

Classify external or temporary handoff documents, including files under `for-neng/`, as one of:

- actively maintained derivative;
- temporary experiment;
- historical snapshot;
- external handoff pending regeneration.

Do not align these files automatically. Update or regenerate them only when the accepted scope explicitly includes the derivative deliverable.

### 4.12 Replace Superseded Definitions

When the accepted change replaces an existing rule:

1. update the primary owner;
2. revise or remove contradictory descriptions elsewhere;
3. preserve historical records only where governance requires them;
4. ensure references point to the current owner;
5. verify that the old and new definitions do not both appear operationally valid.

An alignment note is insufficient when the previous definition has been superseded.

### 4.13 Update Route Visualization Where Applicable

Update the governing Mermaid route diagram when the accepted change affects:

- route or destination existence;
- route parent/child relationship;
- navigation destination or route handoff;
- entry point;
- return behavior;
- material cross-route connection.

Do not update the route diagram for wording, backend logic, notification content, data handling, or other changes that do not affect navigation.

The Mermaid diagram is a visual consistency check and proof of the documented route concept. It is not an independent source of truth and must not introduce behavior absent from the owning documents.

### 4.14 Perform Final Integrated Review

Before reporting commit readiness, verify:

1. the primary owner is clear;
2. no contradictory or superseded definition remains active;
3. no unnecessary duplication was introduced;
4. route IDs, terminology, statuses, actors, and handoffs are consistent;
5. references and links identify the correct owner;
6. traceability and open-question records are accurate;
7. acceptance criteria and test mappings reflect the accepted requirement where applicable;
8. technical, operational, admin, notification, risk, privacy, and security impacts were handled or clearly deferred;
9. document metadata and version history are accurate;
10. diagrams and current visual artifacts match written behavior where applicable;
11. derived AI and external handoff documents were correctly included, deferred, or excluded;
12. PayPlus boundaries and documentation layering remain intact;
13. unrelated content and user changes were preserved;
14. the actual diff matches the approved scope.

Use `git diff --check` and appropriate repository searches. Add other validation when the affected artifact requires it.

## 5. Optional Parallel Review

Parallel agents are not required for every change. Use them when the change is cross-document, conceptually difficult, replaces existing definitions, affects several owners, or has material payment, evidence, promotion, risk, privacy, status, data, route, or operations consequences.

Recommended post-edit review roles:

| Role | Integration check |
| --- | --- |
| Product Reviewer | Charter, PRD, MVP, actor, and PayPlus boundary alignment. |
| Domain Reviewer | Governing domain logic and specialist handoffs. |
| Consistency Reviewer | Contradictions, duplication, ownership, IDs, terminology, references, and affected files. |
| Acceptance Reviewer | Testability, acceptance coverage, and traceability readiness. |
| Orchestrator / Change Integrator | Final scope, shared files, route visualization, consolidated resolution, and commit readiness. |

Reviewers remain read-only unless the Orchestrator gives one canonical writer an approved corrective scope.

## 6. Pre-Commit Report

Before requesting commit approval, report:

1. primary document changed;
2. alignment documents changed;
3. obsolete definitions replaced;
4. material documents checked but unchanged;
5. consistency and validation checks performed;
6. acceptance, test, technical, operational, admin, and metadata effects;
7. diagram or visual-artifact changes, or why none were required;
8. derived AI or external handoff treatment;
9. remaining open questions;
10. unrelated existing changes preserved;
11. whether anything still needs cross-document alignment;
12. commit readiness.

## 7. Commit and Push Gate

After explicit founder approval:

1. stage only the intended files;
2. inspect the staged diff and file list;
3. confirm unrelated changes are not staged;
4. create a concise, scoped commit;
5. report the commit identifier and included files;
6. push only when explicitly requested or clearly included in the founder's approval.

If the staged diff differs materially from the approved scope, stop and obtain renewed confirmation.

## 8. Reusable Invocation Prompt

```text
Apply the PayPlus Documentation Change Integration and Commit Workflow to
[accepted change]. Update the primary owner first, search for affected and
superseded definitions, and complete the full impact review. Align only
materially affected governing, product, domain, traceability, acceptance,
technical, operational, index, guidance, metadata, and visual artifacts.
Report checked-but-unchanged files and the full pre-commit checklist. Do not
commit or push without my approval.
```
