# PayPlus Documentation Development Workflow

Last updated: 2026-07-29

## 1. Purpose

This workflow governs the end-to-end development of PayPlus documentation, from task intake and source review through proposal, drafting, cross-document alignment, validation, founder approval, commit, and repository records.

It applies whether the work is performed by one agent, supported by parallel reviewers, produced through an approved worktree plan, or drafted directly by the founder. Parallel-agent and specialist procedures may supplement this workflow, but they do not replace its ownership, approval, integration, validation, or commit gates.

This workflow supplements `DOC-00` and `AGENTS.md`. It does not replace their source-of-truth hierarchy, PayPlus product boundaries, documentation layering, product-thinking method, or founder authority.

## 2. Authority and Core Rules

The founder remains the product decision, scope-acceptance, document-approval, commit, and push authority.

Every documentation task must follow these rules:

1. classify the requested work before drafting;
2. identify one primary owning document for each material concept;
3. read the authoritative sources before proposing or editing;
4. separate confirmed requirements from assumptions, examples, and open questions;
5. obtain founder confirmation before introducing a material product, governance, ownership, or cross-document decision unless the exact change is already approved;
6. update the primary owner before aligning dependent documents;
7. align only files materially affected by the accepted change;
8. validate the integrated result once after the coordinated edit set;
9. obtain separate approval before committing or pushing unless the founder's instruction explicitly includes that action;
10. preserve unrelated user changes and keep the actual diff within the accepted scope.

Update the primary owning document first. Then identify and align only the governing, product, domain, reference, traceability, decision, acceptance, technical, operational, index, guidance, metadata, and visual files materially affected by that accepted change.

Checking a file does not mean it must be edited. Do not create mechanical reference churn, duplicate the owning requirement, or change unrelated content.

## 3. Applicability, Work Modes, and Roles

Use this workflow for documentation review, drafting, rewriting, restructuring, integration, and commit preparation. It applies to new or revised requirements, routes, screens, flows, statuses, policies, data rules, admin controls, ownership boundaries, cross-document definitions, and repository-governance rules.

- The founder confirms product decisions and authorizes commits and pushes.
- The active lead agent acts as Documentation Lead and Change Integrator unless another owner is appointed.
- One document remains the primary source for each concept.
- Reference documents summarize or hand off; they must not redefine the primary rule.
- Parallel reviewers are optional and should be used when complexity or cross-document risk justifies them.

Classify the task into one of these work modes before acting:

| Work mode | Permitted result | Editing rule |
| --- | --- | --- |
| Review only | Findings, inconsistencies, ownership map, recommendations, and open questions. | Do not edit. |
| Proposal | Decision-ready proposed structure, rules, alternatives, impacts, and open questions. | Do not edit unless the founder approves the exact change. |
| Approved drafting | Draft or revise the accepted content in the primary owner and approved alignment files. | Edit only the accepted scope. |
| Direct scoped edit | Implement an exact founder instruction that does not require a new material decision. | Record the scope and edit without an additional proposal gate. |
| Integration and validation | Align an accepted primary change across materially affected repository artifacts. | Use the Change Impact Manifest and owner-first sequence. |
| Commit preparation | Produce the pre-commit report and verify the intended diff. | Do not commit until explicitly authorized. |
| Commit and records | Create the approved substantive commit and immediate records-only follow-up. | Do not push unless explicitly authorized. |

If the requested mode is unclear, choose the least expansive safe mode. Review and proposal requests do not authorize edits, and edit requests do not automatically authorize a commit.

## 4. Canonical Documentation Lifecycle

### 4.1 Sole Canonical Ownership

This workflow is the sole canonical owner of the PayPlus Documentation Lifecycle and its lifecycle gates. It owns the repository-wide rules for:

- task intake and work-mode classification;
- Proposal and pre-edit review;
- Approval and Founder Decision gates;
- Drafting and primary-owner sequencing;
- Integration and cross-document Alignment;
- Validation and Definition of Done;
- Commit approval and the substantive Commit;
- Changelog and decision-log preparation;
- the Records Commit;
- Push approval and completion reporting.

All other PayPlus workflows, procedures, playbooks, templates, prompts, and `AGENTS.md` routing instructions **MUST** reference this lifecycle when they require one of these stages or gates. They **MUST NOT** redefine, duplicate, weaken, bypass, or create a competing version of a Documentation Lifecycle stage, stage owner, approval rule, validation gate, commit rule, or records requirement.

Specialist materials may define subject-specific inputs, outputs, roles, checks, and execution steps within a lifecycle stage. The parallel-agent procedure may define how work is distributed and consolidated. Neither may replace or restate the lifecycle itself. If a secondary document conflicts with this workflow on a lifecycle matter, this workflow governs subject to `DOC-00` and explicit founder direction.

### 4.2 Lifecycle Sequence

Use this lifecycle for every task, skipping a stage only when the task mode makes it inapplicable or the founder has already supplied the required decision or approval:

```text
Task Request
    -> Classify Work and Concept
    -> Identify Authority and Primary Owner
    -> Review Sources and Current Baseline
    -> Prepare Proposal or Confirm Exact Edit Scope
    -> Founder Decision, when required
    -> Draft the Primary Owner
    -> Integrate Materially Affected Documents
    -> Validate the Coordinated Result
    -> Founder Commit Approval
    -> Substantive Commit
    -> Changelog and Decision-Log Records Commit
    -> Push Approval and Push, when requested
    -> Complete
```

This is one lifecycle, not a requirement to use every specialist procedure. Parallel-agent coordination is an optional execution method within appropriate stages. The Outcome framework, DOC-07 authoring guidance, and prototype guidance apply only when their subject matter is present.

### 4.3 Stage Ownership Matrix

The following matrix is the canonical lifecycle ownership reference. `Responsible` means the role that performs and reports the stage. `Approver / decision owner` means the role that supplies the required decision or authorization; `None` means no separate approval is required for that stage, although its output may be reviewed or may feed a later gate.

| Lifecycle stage | Responsible | Approver / decision owner |
| --- | --- | --- |
| 1. Task intake and task contract | Documentation Lead | Founder for requested scope; otherwise `None` for recording an already explicit instruction |
| 2. Work-mode and concept classification | Documentation Lead | `None`; unresolved classification or scope expansion returns to the Founder |
| 3. Authority, primary-owner, and dependency identification | Documentation Lead | Founder when ownership is unclear, disputed, or materially changed; otherwise `None` |
| 4. Source and repository-baseline review | Documentation Lead | `None`; authoritative conflicts return to the Founder |
| 5. Proposal or exact edit-scope preparation | Documentation Lead, with applicable reviewers | `None` for preparing the proposal; the resulting material decision belongs to the Founder at Stage 6 |
| 6. Founder Decision and edit-scope gate | Documentation Lead presents the decision pack | Founder |
| 7. Definition of Ready | Documentation Lead | `None`; unmet readiness conditions block drafting |
| 8. Primary-owner drafting | Primary Document Owner or one canonical writer appointed by the Documentation Lead | Founder for the accepted material decision and edit scope; formal document approver roles remain governed by `DOC-00` |
| 9. Draft review gate | Documentation Lead, supported by applicable reviewers | Founder for any new material decision; otherwise `None` |
| 10. Change Impact Manifest | Change Integrator | `None`; scope expansion or unresolved conflicts return to the Founder |
| 11. Integration and cross-document Alignment | Change Integrator | Founder for any newly discovered material decision or scope expansion; otherwise `None` |
| 12. Integrated Validation | Change Integrator, supported by applicable reviewers | `None`; failed validation blocks commit readiness |
| 13. Definition of Done and pre-commit report | Documentation Lead / Change Integrator | `None` for reporting; unresolved material matters return to the Founder |
| 14. Commit approval gate | Change Integrator presents the exact intended scope | Founder |
| 15. Substantive Commit | Change Integrator | Founder through the Stage 14 approval |
| 16. Changelog and decision-log update | Change Integrator | The accepted decision remains owned by the Founder; no new approval is required when records accurately describe the approved substantive commit |
| 17. Records-only Commit | Change Integrator | Founder through the Stage 14 approval, which covers the required immediate records follow-up |
| 18. Push approval gate | Change Integrator presents the commits to be pushed | Founder |
| 19. Push | Change Integrator | Founder through the Stage 18 approval |
| 20. Completion report | Documentation Lead / Change Integrator | `None`; completion requires evidence that all applicable prior gates passed |

The Founder may appoint named owners, reviewers, or approvers consistent with `DOC-00`. Such appointments do not transfer the Founder's reserved product-decision, commit-authorization, or push-authorization role unless the Founder explicitly states otherwise.

## 5. Intake, Classification, and Proposal

### 5.1 Confirm the Task Contract

At intake, identify:

1. the requested outcome and work mode;
2. the concept type under `AGENTS.md`;
3. the primary owning document and affected section, if known;
4. authoritative sources and reference-only materials;
5. repository and Git baseline;
6. writable-file scope and explicit exclusions;
7. confirmed decisions, assumptions, examples, and open questions;
8. expected deliverable and validation;
9. stopping, approval, commit, and push conditions.

Do not infer approval for a new route, status, requirement, policy, data object, control, disclosure rule, or product boundary from a general request to improve wording or structure.

### 5.2 Classify Ownership and Dependencies

Before proposing structure or edits:

- classify the subject as a route, screen, view, component, action, status, outcome, event, data object, rule, setting, notification, report, or other governed concept;
- distinguish similar concepts using the separation rules in `AGENTS.md`;
- identify the primary owner and reference or handoff owners;
- identify dependencies that must be decided first;
- check PayPlus product boundaries and documentation-layer boundaries;
- identify specialist frameworks or playbooks that are conditionally required.

If ownership is unclear or authoritative sources conflict, stop at proposal and return the conflict for founder decision.

### 5.3 Prepare the Pre-Edit Proposal

For a material new feature, route, workflow, policy, status model, governance rule, or cross-document change, provide a decision-ready proposal containing:

1. concept classification;
2. recommended structure and why it is proportionate;
3. primary owner and reference documents;
4. user-facing or operational flow where applicable;
5. affected documents and expected treatment;
6. superseded definitions;
7. alternatives or reviewer disagreements that materially affect the decision;
8. open questions and named future owners;
9. proposed edit boundary and explicit exclusions.

Do not over-compress a multi-screen flow, material business rule, ownership choice, failure path, disclosure boundary, or cross-document consequence. Do not edit while the task remains review-only or proposal-only.

### 5.4 Founder Decision Gate

Founder confirmation is required before drafting when the proposal:

- introduces or changes product behavior, ownership, governance, status meaning, route structure, disclosure, risk, compliance, payment, privacy, security, operational, or admin rules;
- resolves a material open question or replaces an active definition;
- materially expands the requested file or concept scope.

An additional proposal gate is not required when the founder has already approved the exact change or requests a direct scoped edit that does not require a new material decision. Record unresolved matters as `TBD`, `Open`, or `To be confirmed` with an owner rather than inventing an answer.

## 6. Drafting the Primary Owner

### 6.1 Definition of Ready

Drafting is ready when:

- the task mode and edit boundary are clear;
- the primary owner is identified;
- authoritative inputs have been reviewed;
- required product decisions are accepted or explicitly left open;
- affected concepts and dependencies are classified;
- unrelated files and working-tree changes are identified;
- specialist frameworks or playbooks have been selected only where applicable.

### 6.2 Owner-First Drafting

Draft the primary owning document before its dependants.

- Preserve useful content that remains valid.
- Replace superseded wording instead of layering a competing rule beside it.
- Keep the human source document readable and leave implementation detail to the correct technical or AI-execution layer.
- Use stable IDs, explicit ownership, measurable acceptance, and traceable handoffs where appropriate.
- Keep confirmed requirements separate from examples, assumptions, options, and open questions.
- Do not redefine rules owned by another document.
- Do not silently expand the approved scope.

If drafting reveals a material decision not covered by the approval, stop that part of the edit, preserve completed in-scope work, and return the new decision for confirmation.

### 6.3 Draft Review Gate

Before integration, confirm:

1. the primary owner contains the accepted meaning;
2. superseded wording in the owner has been replaced;
3. unresolved items remain visible;
4. ownership and documentation layering are preserved;
5. the draft has not introduced undocumented routes, statuses, signals, capabilities, controls, or implementation assumptions.

## 7. Integration Sequence

### 7.1 Confirm the Accepted Change

Before editing, record:

1. the accepted definition, requirement, or behavior;
2. the primary owning document and affected section;
3. the permitted edit scope;
4. unresolved items that remain `TBD`, `Open`, or `To be confirmed`;
5. whether the change replaces an existing definition;
6. whether unrelated changes are prohibited.

If the founder has not accepted the material product decision, return to proposal and review rather than beginning integration.

Create one task-level **Change Impact Manifest** before editing. It should identify:

- the primary owner and exact accepted decision;
- superseded terms, rules, values, routes, statuses, and open questions;
- likely affected governing, parent, product, domain, technical, acceptance, traceability, glossary, index, diagram, prototype, and derived-document files;
- files that are explicitly excluded;
- unresolved conflicts that require founder confirmation.

Use the manifest to batch repository searches and classify impacts once at the start. Re-run broad searches only if the scope changes, validation reveals an unexpected conflict, or a new decision is introduced.

Use this generic trigger guide:

| Change Type | Mandatory Impact Targets |
| --- | --- |
| Route, screen, entry, or handoff | Primary UX owner, parent/family overview, route register, Mermaid map, acceptance/test mapping, affected notification or deeplink owner. |
| Status or user-facing label | Domain owner, status-display matrix, affected UX/notification surfaces, DOC-18 marker, acceptance/test mapping. |
| Decision closure or numeric limit | Primary owner, every matching open/TBC/assumption statement, parent summary, open-question register, acceptance/test mapping. |
| Sensitive reveal or material data change | Product/UX owner, DOC-15, future DOC-19 marker, DOC-18 audit marker, acceptance/test mapping. |
| New or materially changed term | Primary owner and glossary; references should link to the owner rather than redefine the term. |
| Prototype-represented behavior | Current prototype registry, prototype README/source baseline, represented interaction, and prototype validation record. |

### 7.2 Confirm or Update the Primary Owner

Edit the document that owns the behavior first.

- Preserve useful existing content that remains valid.
- Replace superseded requirements instead of adding a second competing rule.
- Keep assumptions and open decisions visibly distinct from confirmed requirements.
- Keep implementation detail in its proper documentation layer.
- Preserve established formatting and stable IDs unless the approved change requires otherwise.

### 7.3 Perform Repository Impact Search

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

### 7.3A Synchronize Parent, Family, and Registers

When an accepted change is made in a child, module, or specialist document, check and update the affected:

- parent overview or family governance map;
- completion/progress status;
- route, requirement, control, or decision register;
- acceptance/test-readiness mapping;
- glossary and index entries;
- current route or architecture diagram.

This is a generic rule for all modular document families. A parent must not continue to describe a child as incomplete, pending, or governed differently after the child has established a newer accepted baseline.

### 7.4 Check Governing and Domain Documents

Check the documents relevant to the change, which may include:

- `DOC-00` for governance, ownership, status, and structure;
- `DOC-01` for charter and product-positioning effects;
- `DOC-05` for product requirement, MVP, module, and role effects;
- parent `DOC-06` and applicable `DOC-06A` to `DOC-06D` for journey, route, Bills UX, and acceptance effects;
- the governing domain documents from `DOC-07` to `DOC-15`;
- `DOC-16` to `DOC-22` where drafted and materially affected;
- privacy, status-display, open-question, or other specialist owners required by `AGENTS.md`.

Do not update every listed document automatically. Edit only when the accepted change alters that document's governed content, handoff, acceptance coverage, or reference accuracy.

### 7.5 Check Shared Alignment Files

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

### 7.6 Check Traceability, Decisions, and Open Questions

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

### 7.7 Check Acceptance and Test Effects

Check applicable acceptance and test owners, including `DOC-06D`, future `DOC-20`, and requirements-to-test traceability when the change affects:

- user-visible behavior or route handoffs;
- roles, permissions, visibility, masking, or access;
- validation, eligibility, limits, or configurable rules;
- status transitions or action-required behavior;
- failure, retry, return, cancellation, exception, or recovery handling;
- notification, evidence, authorization, payout, or reconciliation outcomes.

Update acceptance coverage only after the governing requirement is accepted. Do not invent implementation-level test detail in an early human source document.

### 7.8 Check Downstream Technical, Operational, and Admin Owners

Check relevant drafted downstream owners when the accepted human requirement has a material effect, including:

- `DOC-16` for architecture and component boundaries;
- `DOC-17` for APIs and partner integrations;
- `DOC-18` for data objects, statuses, events, lineage, reporting, and AI-ready signals;
- `DOC-19` for security and access controls;
- `DOC-20` for testing and UAT;
- `DOC-21` for monitoring, incidents, and service operations;
- `DOC-22` for admin configuration, queues, review actions, thresholds, exceptions, and operational controls.

When a change introduces or revises a material result path, check the full chain:

```text
Business Intent and Source Rule
-> Decision or Evaluation
-> Outcome
-> Resolution Strategy
-> Message and CTA
-> Notification when required
-> Audit Event
-> Acceptance Test
-> Code and Automated Test
```

Update only the owners affected by that chain. The route or domain owner defines the business Outcome and permitted Resolution Strategy; DOC-07 governs Message/CTA presentation; DOC-08 governs notifications; DOC-18 governs occurrence and correlation data; DOC-19 governs security eligibility; DOC-20 governs tests; and DOC-21/DOC-22 govern controlled operational handling where applicable. Do not collapse these concepts into one status or duplicate their definitions.

Where a downstream document is still a placeholder, do not infer or draft missing technical detail. Record a precise future-alignment requirement only where needed to prevent the accepted requirement from being lost.

Check `DOC-08` when the change creates or alters a notifiable event, deeplink destination, channel rule, user preference, or admin communication control. Check risk, privacy, compliance, and security owners when the change affects evidence, authorization, participant linking, personal data, masking, approved-purpose access, fraud, AML, tokenization, auditability, or retention.

### 7.9 Check Formal Document Metadata

For every materially edited formal document, check:

- canonical YAML front matter is present where required by DOC-00;
- a human-readable `Document Control` table appears immediately below the H1 title and exactly mirrors the YAML metadata;
- related-document references;
- version and last-updated date;
- version history;
- document status;
- owner, reviewer, and approver fields;
- requirement and section IDs.

Treat YAML as the metadata source of truth. Update the YAML and its Document Control mirror together, and verify that scalar values, list values, dates, status, version, owner, reviewers, approvers, classification, and related-document references do not drift. Empty placeholders are exempt until drafting begins, and backup files are excluded from mechanical presentation updates.

Update metadata according to `DOC-00`. Do not mark a document `Approved`, assign an approver, or close an approval gate without founder authorization and the required evidence.

### 7.10 Check Visual and UX Artifacts

When a prototype is created, materially changed, validated, superseded, or retired, also apply `payplus-prototype-design-validation-specialist-guide.md`.

Check designated current visual artifacts when the accepted change affects what they represent, including:

- Mermaid route diagrams;
- interactive prototypes;
- dashboard or route wireframes;
- screen-flow images;
- generated diagram exports.

Update only artifacts that are current, governed, and materially affected. Regenerate derived exports from their governing source where practical. Do not treat a prototype, screenshot, JPG, or exported diagram as an independent source of truth.

### 7.11 Check Derived AI and External Handoff Documents

Check derived AI execution materials only when that documentation layer is active and the founder has approved source-to-execution conversion. Human source changes must not trigger premature drafting of reserved or placeholder AI execution files.

Classify external or temporary handoff documents, including files under `for-neng/`, as one of:

- actively maintained derivative;
- temporary experiment;
- historical snapshot;
- external handoff pending regeneration.

Do not align these files automatically. Update or regenerate them only when the accepted scope explicitly includes the derivative deliverable.

### 7.12 Replace Superseded Definitions

When the accepted change replaces an existing rule:

1. update the primary owner;
2. revise or remove contradictory descriptions elsewhere;
3. preserve historical records only where governance requires them;
4. ensure references point to the current owner;
5. verify that the old and new definitions do not both appear operationally valid.

An alignment note is insufficient when the previous definition has been superseded.

### 7.13 Update Route Visualization Where Applicable

Update the governing Mermaid route diagram when the accepted change affects:

- route or destination existence;
- route parent/child relationship;
- navigation destination or route handoff;
- entry point;
- return behavior;
- material cross-route connection.

Do not update the route diagram for wording, backend logic, notification content, data handling, or other changes that do not affect navigation.

The Mermaid diagram is a visual consistency check and proof of the documented route concept. It is not an independent source of truth and must not introduce behavior absent from the owning documents.

Use hierarchical route diagrams:

1. Keep the app-level diagram limited to primary navigation destinations and direct global entry points.
2. Give each material route family its own detailed diagram for parent/child destinations, material cross-route handoffs, and return behavior.
3. Stop parent diagrams at the direct child or handoff. Do not repeat the child's full route tree in the parent.
4. Do not create a separate diagram for every trivial leaf screen; create one where navigation ownership, return behavior, or cross-route interaction is material.
5. Treat `docs/traceability/route-register.md` as the canonical destination inventory and definition-status source. Diagrams are visual projections of that register and the owning documents.
6. When a governed diagram is replaced, preserve the prior version under a dated archive/snapshot path, mark it superseded and non-authoritative, identify its replacement diagrams, and update the diagram index.
7. Regenerate governed exports from the active Mermaid source where applicable. Old exports must be marked superseded or kept outside the current-reference index.

### 7.14 Perform Final Integrated Review

Before reporting commit readiness, verify:

1. the primary owner is clear;
2. no contradictory or superseded definition remains active;
3. no unnecessary duplication was introduced;
4. route IDs, terminology, statuses, actors, and handoffs are consistent;
5. material outcomes, permitted resolutions, persistent statuses, Message/CTA presentation, notifications, audit occurrences, and acceptance evidence remain distinct and correctly owned;
6. references and links identify the correct owner;
7. traceability and open-question records are accurate;
8. acceptance criteria and test mappings reflect the accepted requirement where applicable;
9. technical, operational, admin, notification, risk, privacy, and security impacts were handled or clearly deferred;
10. document metadata and version history are accurate;
11. diagrams and current visual artifacts match written behavior where applicable;
12. derived AI and external handoff documents were correctly included, deferred, or excluded;
13. PayPlus boundaries and documentation layering remain intact;
14. unrelated content and user changes were preserved;
15. the actual diff matches the approved scope.

Use `git diff --check` and appropriate repository searches. Add other validation when the affected artifact requires it.

Perform this as one batched validation pass after the coordinated edit set. Do not repeat every repository-wide check after each file unless a failed check or changed scope justifies another pass. The pre-commit report should identify the search terms, affected files checked, validation results, and any consciously deferred alignment.

### 7.15 Prepare Changelog and Decision-Log Recording

Every substantive documentation commit must be recorded in both:

- `docs/changelog/changelog.md`; and
- `docs/decision-log/decisionlog.md`.

Before the substantive commit, prepare the information required for both records, including the change title, affected documents, owning document, accepted decision or requirement, founder approval status, remaining open items, and intended commit scope. Do not invent a commit identifier before the commit exists.

After the substantive commit succeeds:

1. add the substantive commit identifier to both records;
2. update the changelog with the actual files and material changes delivered;
3. update the decision log with the accepted decision, rationale, alternatives considered, ownership, consequences, superseded rules, and remaining `TBC` items;
4. apply the same PayPlus writing, ownership, source-of-truth, scope, and review standards used for formal documentation;
5. validate the registry diff and create one immediate records-only follow-up commit;
6. do not push or report the documentation change as complete until both the substantive commit and records-only commit exist.

The records-only follow-up commit does not require another self-referential changelog or decision-log entry unless it introduces a new substantive product, governance, ownership, or workflow decision. This exemption prevents an infinite commit-recording loop.

Registry rules:

- use stable decision IDs in the format defined by `decisionlog.md`;
- keep entries concise but decision-complete;
- link to the primary owning document and affected alignment documents;
- preserve append-only history; correct an earlier record through a dated correction or superseding decision rather than silently rewriting history;
- do not paste raw chat or agent output into either registry;
- do not record an unapproved proposal as an accepted decision;
- use `Not applicable` with a short reason when a commit contains no product or governance decision, rather than omitting the decision-log record.

## 8. Optional Parallel Review

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

## 9. Definition of Done and Pre-Commit Report

The documentation work is content-complete when:

- the accepted requirement or decision is correctly stated in its primary owner;
- materially affected documents and governed artifacts are aligned;
- superseded definitions no longer appear active;
- ownership, terminology, IDs, routes, statuses, outcomes, messages, notifications, and handoffs remain consistent where applicable;
- unresolved items are visible with an owner and have not been invented away;
- acceptance, traceability, technical, operational, admin, security, privacy, risk, diagram, prototype, and derived-document impacts are addressed or explicitly deferred;
- validation passes and the diff contains only the accepted scope;
- the founder has received a decision-complete result and any remaining approval request.

Content completion does not mean Git completion. A task is commit-complete only after the approved substantive commit and its required changelog and decision-log records commit exist. It is push-complete only after an explicitly authorized push succeeds.

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
12. prepared changelog and decision-log record content;
13. commit readiness.

## 10. Commit and Push Gate

After explicit founder approval:

1. stage only the intended files;
2. inspect the staged diff and file list;
3. confirm unrelated changes are not staged;
4. create a concise, scoped commit;
5. update `docs/changelog/changelog.md` and `docs/decision-log/decisionlog.md` with the substantive commit identifier and actual delivered scope;
6. inspect and create the immediate records-only follow-up commit;
7. report both commit identifiers and included files;
8. push both commits only when explicitly requested or clearly included in the founder's approval.

If the staged diff differs materially from the approved scope, stop and obtain renewed confirmation.

## 11. Reusable Invocation Prompts

### 11.1 Review or Proposal Only

```text
Apply the PayPlus Documentation Development Workflow to [task].
Classify the work and concept, identify the primary owner and authoritative
sources, and return a decision-ready proposal with affected documents,
superseded definitions, alternatives, and open questions. Review and proposal
only. Do not edit, commit, or push.
```

### 11.2 Approved Drafting and Integration

```text
Apply the PayPlus Documentation Development Workflow to [accepted change].
Draft the primary owner first, then align only materially affected documents
and governed artifacts. Preserve unrelated changes, replace superseded
definitions, perform one integrated validation pass, and return the full
pre-commit report. Do not commit or push without my separate approval.
```

### 11.3 Direct Scoped Edit

```text
Apply the PayPlus Documentation Development Workflow to this exact scoped edit:
[scope]. The product decision is already accepted. Confirm the owner and edit
boundary, implement only the named scope, perform proportionate impact review
and validation, and report the result. Do not commit or push without my
separate approval.
```
