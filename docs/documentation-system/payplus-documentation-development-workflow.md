# PayPlus Documentation Development Workflow

Last updated: 2026-07-29
Version: 2.0
Status: Production Ready

## 1. Purpose

This workflow governs the end-to-end development of PayPlus documentation, from task intake and source review through proposal, drafting, cross-document alignment, validation, founder approval, commit, and repository records. It also defines the normative Thinking Modes that separate Explore, Proposal, Draft, Review, Align, and Integrate behaviour.

It applies whether the work is performed by one agent, supported by parallel reviewers, produced through an approved worktree plan, or drafted directly by the founder. Parallel-agent and specialist procedures may supplement this workflow, but they do not replace its ownership, approval, integration, validation, or commit gates.

This workflow supplements [`DOC-00`](../00-foundation/doc-00-documentation-governance.md) and [`AGENTS.md`](../../AGENTS.md). It does not replace their governance, PayPlus product boundaries, documentation layering, product-thinking method, or founder authority.

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
11. apply the Thinking Mode assigned to the current lifecycle stage and do not carry permissions or decision behaviour from one mode into another.

Update the primary owning document first. Then identify and align only the governing, product, domain, reference, traceability, decision, acceptance, technical, operational, index, guidance, metadata, and visual files materially affected by that accepted change.

Checking a file does not mean it must be edited. Do not create mechanical reference churn, duplicate the owning requirement, or change unrelated content.

Workflow v2.0 is the Production Ready baseline. Further changes to its Thinking Modes, Stage Contracts, lifecycle philosophy, or mode boundaries require evidence from real PayPlus documentation work. Hypothetical preference or speculative improvement alone is insufficient: the change request must identify the observed task, failure or friction, affected stage, and supporting repository evidence.

## 3. Applicability, Work Modes, and Roles

Use this workflow for documentation review, drafting, rewriting, restructuring, integration, and commit preparation. It applies to new or revised requirements, routes, screens, flows, statuses, policies, data rules, admin controls, ownership boundaries, cross-document definitions, and repository-governance rules.

- The founder confirms product decisions and authorizes commits and pushes.
- The active lead agent acts as Documentation Lead and Change Integrator unless another owner is appointed.
- One document remains the primary source for each concept.
- Reference documents summarize or hand off; they must not redefine the primary rule.
- Parallel reviewers are optional and should be used when complexity or cross-document risk justifies them, except that material Stage 5 Proposal and material Stage 8 Draft use the fixed-seat contract in Section 3.1.

Classify the task into one of these work modes before acting:

| Work mode | Permitted result | Editing rule |
| --- | --- | --- |
| Explore | Founder clarifications, repository and industry findings, alternatives, conflicts, risks, open questions, and Proposal inputs. | Read-only. Do not recommend or select a solution. |
| Proposal | Decision-ready recommendation, alternatives, trade-offs, impacts, ownership, terminology, architecture, open questions, and proposed edit boundary. | Read-only. Stop at the Founder Decision gate. |
| Approved drafting | Convert an approved Proposal or equivalent explicit Founder instruction into primary-owner documentation. | Edit only the accepted scope and do not introduce new design decisions. |
| Review only | Correctness, completeness, ambiguity, inconsistency, quality, and implementation-fidelity findings. | Read-only. Do not redesign architecture. |
| Direct scoped edit | Implement an exact founder instruction that does not require a new material decision. | Record the scope and edit without an additional proposal gate. |
| Alignment | Synchronize terminology, ownership, references, duplicates, and materially affected documents. | Do not create requirements or redesign accepted work. |
| Integration and validation | Merge approved work into the complete documentation system, validate it, and prepare the pre-commit report. | Use the Change Impact Manifest; do not draft or alter the approved design. |
| Commit preparation | Produce the pre-commit report and verify the intended diff. | Do not commit until explicitly authorized. |
| Commit and records | Create the approved substantive commit and immediate records-only follow-up. | Do not push unless explicitly authorized. |

If the requested mode is unclear, choose the least expansive safe mode. Review and proposal requests do not authorize edits, and edit requests do not automatically authorize a commit.

### 3.1 Material Stage 5 and Stage 8 Fixed-Seat Contract

For material Stage 5 Proposal and material Stage 8 Draft, this contract is the canonical exception to general optional or adaptive parallel-role treatment in supporting procedures and routing references. Apply the existing materiality meaning and triggers in this workflow; this contract does not create a new materiality taxonomy, lifecycle stage, or gate. Non-material exact-scoped work retains proportionate and adaptive treatment.

#### Documentation Manager Coordination and Profile Selection

The Documentation Manager is coordination-only and does not count as a participating agent. For each material task, the Manager:

1. identifies the primary owning document, task subject, and material cross-owner handoffs;
2. selects or, where continuity applies, retains the three specialist profiles most relevant to the task and document;
3. assigns one distinct agent to each specialist seat;
4. records each selected profile's relevance, review scope, required sources and handoffs, expected output, authority boundary, and known capability limitations;
5. identifies every material capability gap;
6. issues the complete task contract;
7. receives the detailed Executor Result Pack; and
8. reports only a concise lifecycle, blocker, and status summary.

The Manager must not act as Lead, writer, specialist reviewer, Challenger, or Founder decision owner for this role model. Its summary cannot substitute for the Executor Result Pack.

Illustrative specialist profiles include:

- Product Strategy / Business Model / Product Boundary;
- UX / Journey / Route / Communication;
- Payment / Evidence / Payout / Accounting;
- API / Provider Integration / Data Contract;
- Backend / Distributed Architecture / Reliability;
- Security / Authentication / Access Control;
- Risk / Compliance / Privacy;
- Operations / Admin / Support / Monitoring; and
- QA / Acceptance / Traceability / Documentation Consistency.

This catalogue is illustrative, not a permanent role hierarchy. The Manager selects only the three profiles required for the current task. Each profile follows the applicable formal document owner and must not redefine meaning owned by another document.

These profiles are internal documentation-review lenses. They do not establish external professional accreditation, legal advice, regulatory approval, compliance certification, security assurance, provider acceptance, implementation readiness, or production readiness. A missing specialist capability is recorded as `Not performed` or `Unresolved`; it must not be invented.

#### Material Stage 5 Proposal

Material Stage 5 Proposal uses exactly four distinct participating agents:

1. **Seat 1 - Primary-owner Lead and Orchestrator.** Owns the canonical Proposal, identifies the primary owner and decision boundary, produces an independent Round 1 position, and performs Round 3 consolidation without replacing specialist review.
2. **Seats 2 to 4 - Three task-selected Specialist Reviewers.** Remain read-only during Proposal, review through their assigned profiles, preserve formal owner and handoff boundaries, and hold no Founder decision authority.

All four agents receive the same common evidence package and independently record their Round 1 positions before any position is shared.

Use this sequence:

```text
Round 1 - all four agents independently record positions before sharing
-> Round 2 - the same four conduct four-way cross-challenge
-> Round 3 - the Lead consolidates one decision-ready Proposal
-> Stage 6 Founder Decision
```

Round 2 challenges material conclusions, assumptions, omissions, owner boundaries, and risks across the four positions. Record material agreements, disagreements, accepted challenges, rejected challenges, and unresolved matters. Cross-challenge is shared among the same four agents; do not create a separate fifth Proposal Challenger.

Round 3 produces one coherent Proposal while preserving material disagreement and rejection reasons. Reviewer agreement is not Founder approval. A missing or combined seat, missing independent position, incomplete cross-challenge, or absent Lead consolidation blocks material Stage 5 exit. Material Proposal remains read-only and stops at Stage 6 Founder Decision.

#### Material Stage 8 Draft

When material Stage 8 follows material Stage 5, retain the same four participants. Seat 1 becomes the canonical writer; Seats 2 to 4 remain the same read-only Specialist Reviewers and must not create competing Draft edits. One canonical writer controls each formal document, and only that writer may modify it.

Where material Draft begins from an equivalent explicit Founder instruction without a preceding four-agent Stage 5 team, the Manager selects and records the four Stage 8 participants at the Stage 7 Definition of Ready gate using the same profile-selection rules. The four-seat record must be complete before drafting begins.

For every material Stage 8 Draft, the Manager separately appoints exactly one **Independent Internal Review Challenger / Draft Completeness Reviewer** and records that the Challenger:

- is separate from the four task participants;
- authored no Draft content and performed no Draft editing;
- remains read-only;
- cannot replace a missing Specialist Reviewer; and
- holds no Founder or Stage 9 approval authority.

The Challenger is the only mandatory additional Stage 8 participant. Material Stage 8 therefore uses exactly five participating agents total: one canonical writer, three task-selected read-only Specialist Reviewers, and one independent read-only Challenger.

Use exactly this sequence:

```text
canonical writer produces the Draft
-> three Specialist Reviewers inspect the complete Draft
-> independent Challenger performs completeness and fidelity review
-> writer applies only accepted-scope corrections
-> relevant Specialist Reviewers reinspect affected meaning
-> Challenger reinspects the actual final bytes
-> evidence-bearing Stage 8 handoff
```

The Challenger receives the approved decisions, Draft Plan, Decision Coverage Matrix, authoritative sources, specialist findings, complete Draft, and complete diff. It reviews completeness and fidelity, including omissions, contradictions, unsupported assumptions, owner-boundary breaches, and unimplemented accepted decisions. It remains Stage 8 support only and must not author or edit the Draft, approve a Founder decision, issue a Stage 9 result, or substitute for Stage 9 Primary Review.

Stage 8 exit is blocked when:

- any required Specialist Review is absent;
- the Challenger is absent;
- reviewer or Challenger independence is not evidenced;
- an evidence-backed accepted-scope objection remains unresolved;
- required specialist reinspection is absent;
- the Challenger has not inspected the actual final bytes; or
- a material substantive-completeness gap remains.

Any formal-document or controlling Decision Coverage Matrix change after reinspection invalidates the affected closure evidence. Relevant specialist reinspection and Challenger final-byte reinspection must then be repeated. Do not add a mandatory Stage 8 four-way cross-challenge round; four-way cross-challenge is a material Stage 5 Proposal control.

#### Stage 9 Boundary

Stage 9 remains unchanged as the existing formal independent Primary Review gate. The Stage 8 Challenger is not Stage 9, does not approve the Draft, and cannot substitute for Stage 9 Primary Review.

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
    -> Explore: Task Contract and Work Classification (Stages 1-2)
    -> Explore: Authority, Ownership Candidates, and Evidence (Stages 3-4)
    -> Proposal: Recommend One Direction or Confirm Exact Approved Scope (Stage 5)
    -> Founder Decision, when required
    -> Draft: Definition of Ready and Primary-Owner Documentation (Stages 7-8)
    -> Review: Validate the Primary-Owner Draft (Stage 9)
    -> Align: Manifest and Cross-Document Consistency (Stages 10-11)
    -> Integrate: Coordinated Validation and Pre-Commit Result (Stages 10-13)
    -> Founder Commit Approval
    -> Substantive Commit
    -> Changelog and Decision-Log Records Commit
    -> Push Approval and Push, when requested
    -> Complete
```

This is one lifecycle, not a requirement to use every specialist procedure. Parallel-agent coordination is an optional execution method within appropriate stages except for the material Stage 5 and Stage 8 fixed-seat contract in Section 3.1. The Outcome framework, DOC-07 authoring guidance, and prototype guidance apply only when their subject matter is present.

### 4.3 Stage Ownership Matrix

The following matrix is the canonical lifecycle ownership reference. `Responsible` means the role that performs and reports the stage. `Approver / decision owner` means the role that supplies the required decision or authorization; `None` means no separate approval is required for that stage, although its output may be reviewed or may feed a later gate.

| Lifecycle stage | Responsible | Approver / decision owner |
| --- | --- | --- |
| 1. Explore - Task intake and task contract | Documentation Lead | Founder for requested scope; otherwise `None` for recording an already explicit instruction |
| 2. Explore - Work-mode and concept classification | Documentation Lead | `None`; unresolved classification or scope expansion returns to the Founder |
| 3. Explore - Authority, current ownership, ownership candidates, and dependency evidence | Documentation Lead | Founder when an existing authority conflict prevents exploration; otherwise `None` |
| 4. Explore - Source, repository-baseline, and applicable industry review | Documentation Lead | `None`; authoritative conflicts remain Explore findings and return to the Founder when they prevent Proposal |
| 5. Proposal - Decision recommendation or exact approved-scope confirmation | Documentation Lead, with the Section 3.1 fixed-seat contract for material Proposal or applicable reviewers otherwise | `None` for preparing the Proposal; the resulting material decision belongs to the Founder at Stage 6 |
| 6. Founder Decision and edit-scope gate | Documentation Lead presents the decision pack | Founder |
| 7. Draft - Definition of Ready | Documentation Lead | `None`; unmet readiness conditions block drafting |
| 8. Draft - Primary-owner documentation | Primary Document Owner or one canonical writer named in the applicable task contract; material Draft also uses the Section 3.1 specialist and Challenger controls | Founder for the accepted material decision and edit scope; formal document approver roles remain governed by `DOC-00` |
| 9. Review - Draft review gate | Documentation Lead, supported by applicable reviewers | Founder for any new material decision; otherwise `None` |
| 10. Align / Integrate - Change Impact Manifest | Change Integrator | `None`; scope expansion or unresolved conflicts return to the Founder |
| 11. Align / Integrate - Cross-document consistency | Change Integrator | Founder for any newly discovered material decision or scope expansion; otherwise `None` |
| 12. Integrate - Integrated Validation | Change Integrator, supported by applicable reviewers | `None`; failed validation blocks commit readiness |
| 13. Integrate - Integration completion, Definition of Done, and pre-commit report | Documentation Lead / Change Integrator | `None` for reporting; unresolved material matters return to the Founder |
| 14. Commit approval gate | Change Integrator presents the exact intended scope | Founder |
| 15. Substantive Commit | Change Integrator | Founder through the Stage 14 approval |
| 16. Changelog and decision-log update | Change Integrator | The accepted decision remains owned by the Founder; no new approval is required when records accurately describe the approved substantive commit |
| 17. Records-only Commit | Change Integrator | Founder through the Stage 14 approval, which covers the required immediate records follow-up |
| 18. Push approval gate | Change Integrator presents the commits to be pushed | Founder |
| 19. Push | Change Integrator | Founder through the Stage 18 approval |
| 20. Completion report | Documentation Lead / Change Integrator | `None`; completion requires evidence that all applicable prior gates passed |

The Founder may appoint named owners, reviewers, or approvers consistent with `DOC-00`. Such appointments do not transfer the Founder's reserved product-decision, commit-authorization, or push-authorization role unless the Founder explicitly states otherwise.

### 4.4 Normative Thinking Modes

Thinking Mode governs AI behaviour throughout the applicable lifecycle stage. It determines how the agent reasons, what it may produce, what it must not decide, and the evidence required before leaving the stage. A command selects a mode or lifecycle destination; it does not weaken this behavioural contract or authorize a later mode.

| Stage | Thinking Mode | Purpose | Decision Authority |
| --- | --- | --- | --- |
| Explore | Divergent | Expand understanding and generate Proposal inputs. | Cannot select a solution. |
| Proposal | Convergent | Evaluate alternatives and recommend one direction. | Recommendation only; Founder decides. |
| Draft | Execution | Convert approved decisions into documentation. | Cannot introduce new design decisions. |
| Review | Validation | Validate correctness, completeness, clarity, consistency, quality, and implementation fidelity. | Cannot redesign architecture. |
| Align | Consistency | Synchronize terminology, ownership, references, duplicates, and cross-document meaning. | Cannot create requirements. |
| Integrate | Integration | Merge approved work into the complete documentation system and prepare the coordinated result. | Cannot alter the approved design. |

The lifecycle mapping is:

```text
Stages 1-4   Explore
Stage 5      Proposal
Stage 6      Founder Decision
Stages 7-8   Draft
Stage 9      Review
Stages 10-11 Align
Stages 10-13 Integrate
```

Integrate is the orchestration mode across Stages 10 to 13. Within that sequence, Align supplies the Consistency behaviour for Stages 10 and 11, and Integrated Validation supplies validation evidence at Stage 12. Neither activity permits drafting or design changes.

The `Review` command may also route a source or baseline review to Stage 4 or support Integrated Validation at Stage 12. In those contexts, the Thinking Mode follows the lifecycle stage: Stage 4 remains divergent Explore, Stage 9 uses Review/Validation, and Stage 12 remains part of Integrate.

### 4.5 Canonical Stage Contracts

Each contract below is the canonical behavioural specification for AI operating in that Thinking Mode.

#### 4.5.1 Explore Stage Contract

##### Thinking Mode

Divergent.

##### Purpose

Expand understanding, investigate the current and external context, expose alternatives and conflicts, and prepare neutral inputs for a later Proposal. Explore exists to widen and clarify the decision space, not to converge on a solution.

##### Inputs

- Founder topic, goal, clarifications, constraints, and known concerns;
- current repository sources, ownership records, traceability, and working-tree evidence;
- applicable industry, professional, technical, regulatory, or operational evidence when available and appropriate;
- known assumptions, conflicts, dependencies, risks, and unanswered questions.

##### Outputs

Explore **SHALL** produce an **Explore Pack** containing:

1. Founder Clarifications;
2. Existing Repository Findings;
3. Industry Findings;
4. Alternative Comparison;
5. Conflict Analysis;
6. Risks;
7. Open Questions;
8. Proposal Inputs.

An item may be marked `Not applicable` or `No material finding` when supported by the exploration evidence; the heading must remain visible so omission is not mistaken for completed analysis.

##### Allowed Actions

- understand, investigate, compare, identify, classify, and expand possibilities;
- distinguish repository facts, external findings, assumptions, and unresolved questions;
- identify current owners and candidate future owners without selecting a new owner;
- describe candidate concepts, terminology, objects, lifecycle models, statuses, or architectures only as non-authoritative alternatives requiring comparison;
- identify conflicts, dependencies, risks, evidence gaps, and inputs needed for Proposal.

##### Forbidden Actions

Explore **MUST NOT**:

- recommend or select an architecture;
- define or recommend ownership;
- define or recommend terminology;
- define a lifecycle;
- define statuses;
- define an object model;
- recommend document edits;
- make or conceal a design decision;
- write documentation or let an Explore output gradually become Proposal or Draft content.

##### Exit Criteria

Explore may exit only when:

- sufficient evidence exists to understand the material problem and alternatives;
- repository findings and industry findings are distinguishable;
- candidate concepts remain explicitly non-authoritative;
- conflicts, risks, and open questions are visible;
- the Explore Pack is complete enough to support a separate Proposal;
- no recommendation or edit has been introduced.

Leaving Explore does not authorize Proposal. Proposal begins only under the hard boundary in Section 5.4.

#### 4.5.2 Proposal Stage Contract

##### Thinking Mode

Convergent.

##### Purpose

Evaluate the evidence and alternatives, recommend one proportionate direction, explain its consequences, and prepare the material decisions for the Founder.

##### Inputs

- a sufficient Explore Pack or equivalent current evidence;
- the problem and decision to be made;
- product, governance, documentation-layer, risk, security, privacy, compliance, operational, and delivery constraints;
- alternatives, conflicts, risks, and open questions;
- current owners and affected documents.

##### Outputs

Proposal **SHALL** produce:

1. recommended solution;
2. rationale;
3. alternatives considered;
4. rejected alternatives and rejection reasons;
5. trade-offs;
6. impacts;
7. ownership recommendation;
8. terminology recommendation;
9. architecture recommendation;
10. remaining Founder decisions;
11. proposed edit boundary and exclusions;
12. a bounded Proposal Challenge summary;
13. Decision Readiness evidence for every material decision;
14. one consolidated Founder Decision Pack wherever practical;
15. explicit Founder approval request.

Items that do not apply must be identified as such rather than silently omitted.

For a material Proposal, the task-context evidence must also identify the four participating agents and selected specialist profiles and retain the four Round 1 positions, Round 2 four-way cross-challenge record, and Round 3 Lead consolidation required by Section 3.1.

##### Allowed Actions

Proposal is the first stage permitted to:

- recommend architecture;
- recommend terminology;
- recommend ownership;
- recommend a lifecycle or status model;
- recommend an object model;
- recommend document changes and an edit boundary;
- select a preferred alternative and explain trade-offs;
- identify unresolved decisions that remain with the Founder.

##### Forbidden Actions

Proposal **MUST NOT**:

- edit documentation;
- present a recommendation as accepted;
- hide rejected alternatives or material trade-offs;
- bypass the Founder Decision gate;
- carry an unresolved recommendation into Draft as though it were approved.

##### Bounded Proposal Challenge

Before Proposal exit, challenge the initial recommendation through this sequence:

```text
Initial Recommendation
-> Adversarial Challenge
-> Scenario and Invariant Testing
-> Canonical Conflict Check
-> Cross-document Impact Check
-> Revised Recommendation
```

Run one challenge cycle by default and no more than two. A second cycle requires a recorded material recommendation change or newly exposed blocker. Use stable finding IDs, do not introduce a new alternative unless an existing option fails, and close with a concise challenge summary.

For a material Proposal, the Round 2 four-way cross-challenge required by Section 3.1 performs this bounded Proposal Challenge. It does not create a fifth Proposal Challenger or an additional lifecycle gate.

##### Decision Readiness and Founder Decision Pack

Mark every material decision `Pass`, `Fail`, or justified `N/A` for evidence completeness, a defined invariant, normal and exception scenarios, canonical-conflict resolution, current owner, downstream impact, and whether Founder approval is required. A material `Fail` cannot enter Draft; keep it in Proposal or return it to Explore when more evidence is required.

Wherever practical, consolidate material Founder decisions into one numbered pack. Each decision must state its Decision ID, problem and evidence, authority and current owner, viable options, agent recommendation, consequences and affected documents, exact Founder answer requested, decision class, and blocked and unaffected dependencies where applicable. Classify it as an agent-resolvable correction, an agent-analysis-required Founder-approved decision, or an affected-scope blocker. Escalate only material product, money, ownership, risk, compliance, privacy, security, architecture, scope, or governance decisions; an affected-scope blocker blocks only dependent scope.

##### Exit Criteria

Proposal exits only when:

- one direction is recommended clearly;
- alternatives, rejected alternatives, trade-offs, impacts, and remaining decisions are visible;
- proposed ownership, terminology, architecture, and document changes are explicit where applicable;
- the writable boundary and exclusions are reviewable;
- an explicit Founder approval request is presented.
- the bounded Proposal Challenge is complete;
- every material decision passes Decision Readiness or has been kept out of Draft;
- material Founder decisions are consolidated wherever practical and dependent-scope blocking is explicit.
- for a material Proposal, all four seats, independent positions, four-way cross-challenge, and Lead consolidation required by Section 3.1 are evidenced and complete.

Proposal remains read-only and ends at Stage 6, the existing Founder Decision and edit-scope gate.

#### 4.5.3 Draft Stage Contract

##### Thinking Mode

Execution.

##### Purpose

Convert approved Proposal decisions or an equivalent explicit Founder instruction into accurate primary-owner documentation.

##### Inputs

- an approved Proposal; or
- an explicit Founder instruction that supplies equivalent design authority and exact scope;
- primary owning document and writable-file allowlist;
- authoritative sources, approved terminology, ownership, architecture, requirements, and unresolved items;
- applicable specialist guidance.
- a Draft Plan and Decision Coverage Matrix for material work.
- for material work, the participant, profile-selection, authority-boundary, and capability-limitation records required by Section 3.1; Challenger independence must be evidenced before Challenger review.

##### Outputs

- primary-owner documentation implementing the approved meaning;
- traceability from the approved decisions or exact Founder instruction to the drafted content;
- visible assumptions, `TBD`, `Open`, or `To be confirmed` items that remain unresolved;
- a Draft Review handoff identifying the implemented scope, any blocked design discovery, the affected-scope semantic assessment, cross-document impact, residuals and dependencies, qualifications, and whether substantive completeness is self-proven for Stage 9;
- a coverage matrix mapping each approved decision or requirement to its normative section, required table, materially useful tree or Mermaid representation, Acceptance Criteria, primary owner, and downstream handoff; use justified `N/A` where a representation would not materially improve or govern meaning.
- for material work, three specialist review records, the Challenger completeness and fidelity findings, correction dispositions, relevant specialist reinspections, Challenger final-byte reinspection, and the exact identity of the final reviewed artifact.

The Draft Review handoff and coverage matrix are the existing Stage 8 coverage materials. They are execution evidence in the task context or existing execution record only and do not create a permanent Evidence Pack artifact.

##### Allowed Actions

- create or revise documentation within the approved writable scope;
- execute approved architecture, ownership, terminology, lifecycle, status, object, and requirement decisions;
- preserve repository consistency, stable IDs, documentation layering, and traceability;
- apply non-material editorial judgement needed to express the approved decision clearly.

##### Forbidden Actions

Draft **MUST NOT**:

- introduce new architecture;
- redefine ownership;
- redefine approved terminology;
- select among unapproved alternatives;
- redesign requirements;
- invent a decision to make the draft appear complete;
- expand the approved scope silently.

##### Exit Criteria

Draft exits only when:

- the approved decision is expressed in the primary owner;
- the implementation remains within the accepted boundary;
- approved terminology, ownership, architecture, and requirements are preserved;
- traceability to the approved Proposal or equivalent Founder instruction is visible;
- unresolved items remain explicit, including valid owner-backed `TBD`, `Open`, or deferred items;
- any new design discovery has been returned to Proposal rather than resolved in Draft;
- the Draft Review handoff and coverage matrix together self-prove substantive completeness within the accepted boundary before Stage 9, including decision coverage, affected-scope semantic assessment, cross-document impact, residuals and dependencies, and qualifications;
- no material uncovered, unknown, ownerless, or substantive-completeness gap remains; any such gap blocks Stage 8 exit;
- the mutation scope is separately identified from the broader read-only assessment, and assessed-but-unmutated references are not treated as writable authority;
- the coverage materials are complete and ready for independent Stage 9 Review.
- for material work, the Section 3.1 fixed-seat, specialist-review, Challenger, correction, reinspection, and final-byte requirements are evidenced and complete.

#### 4.5.4 Review Stage Contract

##### Thinking Mode

Validation.

##### Purpose

Validate the primary-owner draft against its approved decision, authoritative sources, quality expectations, and documentation boundaries.

##### Inputs

- the primary-owner draft or defined review target;
- approved Proposal or equivalent Founder instruction;
- authoritative sources and applicable specialist checks;
- requested review lens and acceptance expectations.
- the Draft Plan and Decision Coverage Matrix for material work.
- the Draft Review handoff, including its substantive-completeness claim, affected-scope assessment, cross-document impact, residuals, dependencies, and qualifications.

##### Outputs

- evidence-backed findings covering correctness, completeness, ambiguity, inconsistency, documentation quality, and implementation fidelity;
- severity and ownership for each material finding;
- accepted-scope corrections distinguished from design issues;
- design issues routed to Explore or Proposal;
- Draft Review PASS/FAIL conclusion and unresolved items.
- named findings and the review phase: Primary Review, Verification Review, or Final Verification.
- an independent confirmation or refutation of the Draft's substantive-completeness claim against the approved Proposal, authoritative sources, and approved coverage materials.

##### Allowed Actions

- identify defects, gaps, ambiguity, contradictions, duplication, unsupported assumptions, and incomplete implementation of the approved decision;
- recommend corrections that restore fidelity to the approved design;
- identify when a problem requires renewed exploration or a new Proposal;
- verify that the draft did not introduce undocumented architecture, terminology, ownership, objects, statuses, lifecycle, or requirements.

##### Forbidden Actions

Review **MUST NOT**:

- redesign architecture;
- select a new alternative;
- redefine ownership, terminology, lifecycle, statuses, objects, or requirements;
- convert a design finding into an unapproved corrective design;
- edit without a separately authorized correction scope.

##### Review Convergence

- **Primary Review** may identify any evidence-backed defect.
- **Verification Review** verifies named findings and accepted corrections. It may add a finding only for a regression, previously hidden contradiction, or material safety or implementation blocker.
- **Final Verification** is closure-led. New findings are limited to objective blockers, regressions, or bounded closure defects.
- Each Review `FAIL` containing accepted-scope findings creates one consolidated Draft correction scope for that Review phase and its permitted finding boundary. The correction scope includes only findings whose correction restores fidelity to the approved Proposal or accepted design within the authorized Draft boundary.
- Findings outside the accepted design or authorized Draft scope remain in the Review result and route to Proposal when a new design decision is required or to Explore when an evidence gap requires further understanding; they are not absorbed into the Draft correction scope.
- This convergence contract introduces no agent-count requirement. Existing applicable independent-review requirements remain unchanged.

After Proposal approval, an alternative preference is a non-blocking backlog observation unless the accepted design is contradictory, unsafe, impossible, or unimplementable. An alternative design that requires reconsideration returns to Explore or Proposal; it does not remain an open-ended review blocker.

##### Exit Criteria

Review exits only when:

- findings are evidence-backed and classified;
- corrections within the approved design are separated from new design questions;
- design issues are routed to Explore when more understanding is required or Proposal when a decision recommendation is required;
- the review states PASS or FAIL and identifies what blocks progression to Align.
- the applicable convergence phase has respected its new-finding boundary;
- when the result is `FAIL` with accepted-scope findings, one consolidated Draft correction scope is identified for that phase, while findings outside the accepted design or scope remain separately routed and unresolved.

#### 4.5.5 Align Stage Contract

##### Thinking Mode

Consistency.

##### Purpose

Synchronize the reviewed, approved primary change across materially affected documentation without creating new requirements or reopening the design.

##### Inputs

- reviewed primary-owner draft;
- approved Proposal or equivalent Founder instruction;
- Change Impact Manifest and affected-document set;
- existing terminology, ownership, references, registers, diagrams, traceability, and duplicate definitions.

##### Outputs

- terminology consistency;
- ownership consistency;
- reference consistency;
- removal or replacement of active duplicate and superseded definitions;
- cross-document consistency across materially affected artifacts;
- unresolved conflicts or scope expansion returned to Proposal.
- `ALIGN_EXECUTED - PENDING_VALIDATE`, together with unresolved matters; Align does not declare coordinated success.

##### Allowed Actions

- synchronize terminology, ownership statements, references, handoffs, registers, indexes, diagrams, traceability, and materially affected documents;
- remove or replace duplicate and superseded definitions;
- preserve one primary owner and make dependent documents reference it;
- report conflicts that cannot be resolved without a material decision.

##### Forbidden Actions

Align **MUST NOT**:

- create requirements;
- redesign architecture;
- redefine ownership or terminology beyond the approved decision;
- draft new primary-owner design;
- treat consistency work as authority to expand scope.
- report the coordinated result as passed before Validate.

##### Exit Criteria

Align exits only when:

- materially affected documents are consistent with the reviewed primary owner;
- terminology, ownership, references, and duplicated definitions are aligned;
- unrelated documents remain unchanged;
- every material conflict or scope expansion has returned to Proposal instead of being decided during Align.
- execution is reported as `ALIGN_EXECUTED - PENDING_VALIDATE` rather than as a coordinated PASS.

#### 4.5.6 Integrate Stage Contract

##### Thinking Mode

Integration.

##### Purpose

Merge approved and reviewed work into the complete documentation system, coordinate alignment and integrated validation, and produce the canonical pre-commit result.

##### Inputs

- approved Proposal or equivalent Founder instruction;
- reviewed primary-owner draft;
- repository and working-tree baseline;
- writable boundary and exclusions;
- Change Impact Manifest;
- aligned materially affected documents and governed artifacts;
- applicable validation and acceptance checks.

##### Outputs

- completed Change Impact Manifest;
- integrated, aligned documentation-system result;
- integrated validation evidence;
- integration-completion and Definition of Done conclusion;
- canonical pre-commit report, remaining blockers, and deferred items.
- an integration result of `INTEGRATE_FAIL - RETURN_TO_<STAGE>` or, only after coordinated validation passes, `INTEGRATE_PASS - READY_FOR_COMMIT_APPROVAL`.

##### Allowed Actions

- prepare and maintain the Change Impact Manifest;
- orchestrate Align across materially affected artifacts;
- perform repository impact checks and integrated validation;
- consolidate already approved work;
- prepare integration completion, Definition of Done, and pre-commit evidence.

##### Forbidden Actions

Integrate **MUST NOT**:

- draft or redraft primary-owner design;
- introduce or alter architecture;
- redefine ownership, terminology, lifecycle, statuses, objects, or requirements;
- select an unapproved alternative;
- use impact discovery as authority for a material change;
- alter the approved design.
- declare commit readiness before coordinated validation has passed.

##### Exit Criteria

Integrate exits only when:

- only approved and reviewed work has been merged;
- the Change Impact Manifest is complete;
- Alignment and Integrated Validation have been completed;
- no drafting or design decision occurred during Integration;
- material discoveries have returned to Proposal;
- the coordinated result satisfies Definition of Done or identifies explicit blockers;
- the pre-commit report is ready for the unchanged Stage 14 Founder Commit approval gate.
- coordinated validation has passed before `INTEGRATE_PASS - READY_FOR_COMMIT_APPROVAL` is reported.

## 5. Explore and Proposal

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

For material Stage 5 Proposal or material Stage 8 Draft, also record the Section 3.1 participant seats, selected specialist profiles, relevance and scope, required sources and handoffs, expected outputs, authority boundaries, capability limitations, and applicable independence controls.

Do not infer approval for a new route, status, requirement, policy, data object, control, disclosure rule, or product boundary from a general request to improve wording or structure.

### 5.2 Explore the Decision Space

During Stages 1 to 4, apply only the Explore/Divergent contract.

- classify the subject as a route, screen, view, component, action, status, outcome, event, data object, rule, setting, notification, report, or other governed concept;
- distinguish similar concepts using the separation rules in `AGENTS.md`;
- identify current authority and owners as repository findings;
- identify ownership, terminology, architecture, lifecycle, status, object, and document-treatment candidates only as alternatives;
- identify dependencies that may need to be decided later;
- check PayPlus product boundaries and documentation-layer boundaries;
- identify specialist frameworks or guides that may be conditionally required;
- investigate applicable repository and industry evidence;
- compare alternatives without choosing or recommending one.

If ownership is unclear or authoritative sources conflict, record the conflict in the Explore Pack. Do not resolve it through a hidden recommendation.

### 5.3 Produce the Explore Pack

The Explore Pack is the required Stage 4 handoff whenever the requested mode is Explore or the task needs material investigation before Proposal.

Use these headings:

1. Founder Clarifications;
2. Existing Repository Findings;
3. Industry Findings;
4. Alternative Comparison;
5. Conflict Analysis;
6. Risks;
7. Open Questions;
8. Proposal Inputs.

Repository facts, external findings, hypotheses, and candidate alternatives must remain distinguishable. The Explore Pack must not contain a preferred architecture, recommended ownership, selected terminology, lifecycle, status model, object model, or proposed document edit.

### 5.4 Hard Explore-to-Proposal Boundary

Explore **SHALL NOT** gradually evolve into Proposal. A sentence, table, diagram, object list, or candidate model created during Explore remains non-authoritative unless it is later evaluated and recommended explicitly in Proposal.

Proposal may begin only when:

- sufficient Explore evidence or equivalent current evidence exists;
- alternatives remain visibly non-authoritative;
- the Proposal mode is explicitly requested by the Founder or equivalent decision authority is present in an explicit Founder instruction;
- the intended decision, constraints, and stopping gate are clear.

An agent must not reinterpret a request to understand, investigate, compare, review, or explore as permission to recommend one solution.

### 5.5 Prepare the Proposal

For a material new feature, route, workflow, policy, status model, governance rule, or cross-document change, apply the Proposal/Convergent contract and produce a decision-ready recommendation containing:

1. recommended solution;
2. rationale;
3. alternatives considered;
4. rejected alternatives and rejection reasons;
5. trade-offs;
6. impacts;
7. ownership recommendation;
8. terminology recommendation;
9. architecture recommendation;
10. remaining Founder decisions;
11. proposed edit boundary and explicit exclusions;
12. explicit Founder approval request.

Proposal is the first stage permitted to recommend architecture, terminology, ownership, lifecycle, statuses, object model, or document changes. It remains read-only.

Run the bounded Proposal Challenge defined in Section 4.5.2 and include its concise summary. Complete Decision Readiness for every material decision. A material `Fail` stays in Proposal or returns to Explore and must not enter Draft.

For a material Proposal, use the Section 3.1 four-seat sequence: independent Round 1 positions, Round 2 four-way cross-challenge by the same four agents, and Round 3 Lead consolidation. This sequence satisfies the bounded Proposal Challenge; do not add a separate fifth Challenger.

Do not over-compress a multi-screen flow, material business rule, ownership choice, failure path, disclosure boundary, or cross-document consequence. Do not draft documentation while the task remains Proposal-only.

### 5.6 Founder Decision Gate

Founder confirmation is required before drafting when the proposal:

- introduces or changes product behavior, ownership, governance, status meaning, route structure, disclosure, risk, compliance, payment, privacy, security, operational, or admin rules;
- resolves a material open question or replaces an active definition;
- materially expands the requested file or concept scope.

Consolidate these material decisions into one numbered Founder Decision Pack wherever practical, using the content and classification defined in Section 4.5.2. Resolve agent-resolvable corrections without escalation. An affected-scope blocker blocks only its dependent scope; explicitly identify unaffected work that may proceed.

An additional Proposal gate is not required when the Founder has already approved the exact change or requests a direct scoped edit that supplies equivalent design authority and does not require a new material decision. That instruction becomes the bounded decision contract for Draft; it does not authorize Draft to redesign it. Record unresolved matters as `TBD`, `Open`, or `To be confirmed` with an owner rather than inventing an answer.

## 6. Drafting the Primary Owner

### 6.1 Definition of Ready

Drafting is ready when:

- an approved Proposal exists, or an explicit Founder instruction supplies equivalent design authority and exact scope;
- the task mode and edit boundary are clear;
- the primary owner is identified;
- authoritative inputs have been reviewed;
- required product decisions are accepted or explicitly left open without authorizing Draft to resolve them;
- affected concepts and dependencies are classified;
- unrelated files and working-tree changes are identified;
- specialist frameworks or guides have been selected only where applicable;
- the approved architecture, ownership, terminology, lifecycle, statuses, object model, requirements, and document treatment are identifiable where applicable.
- every material decision entering Draft has passed Decision Readiness;
- a Draft Plan and Decision Coverage Matrix maps approved decisions and requirements to the representations, Acceptance Criteria, ownership, and handoffs defined in Section 4.5.3.
- for material Draft following material Stage 5, the same four participants are retained and their Stage 8 roles are recorded as required by Section 3.1;
- for material Draft beginning from an equivalent explicit Founder instruction without a preceding four-agent Stage 5 team, the Manager has selected and recorded the four participants at this Stage 7 Definition of Ready gate using the Section 3.1 profile-selection rules;
- one canonical writer is identified for each formal document, the three Specialist Reviewers are read-only, and the separately appointed Challenger control is planned without treating it as Stage 9.

### 6.2 Owner-First Drafting

Draft the primary owning document before its dependants.

- Preserve useful content that remains valid.
- Replace superseded wording instead of layering a competing rule beside it.
- Keep the human source document readable and leave implementation detail to the correct technical or AI-execution layer.
- Use stable IDs, explicit ownership, measurable acceptance, and traceable handoffs where appropriate.
- Preserve traceability from each material drafted definition to the approved Proposal decision or equivalent explicit Founder instruction.
- Keep confirmed requirements separate from examples, assumptions, unselected options, and open questions.
- Do not redefine rules owned by another document.
- Do not silently expand the approved scope.
- Do not introduce architecture, redefine ownership or terminology, select alternatives, redesign requirements, or invent a decision to complete the draft.

If drafting reveals a material design decision not covered by the approval, stop that part of the edit, preserve completed in-scope work, and return the discovery to Proposal. If additional understanding is required before a recommendation can be prepared, return it to Explore first.

### 6.3 Draft Review Gate

Before handing the Draft to Stage 9 Review, confirm:

1. the primary owner contains the accepted meaning;
2. superseded wording in the owner has been replaced;
3. unresolved items remain visible;
4. ownership and documentation layering are preserved;
5. the draft has not introduced undocumented routes, statuses, signals, capabilities, controls, implementation assumptions, architecture, terminology, ownership, lifecycle, or object definitions;
6. each material definition remains traceable to the approved Proposal or equivalent Founder instruction;
7. the review covers correctness, completeness, ambiguity, inconsistency, documentation quality, and implementation fidelity.
8. the coverage matrix has been checked against prose, tables, trees and Mermaid diagrams, cardinality, formulas and monetary relationships, lifecycle and status terminology, Acceptance Criteria, and downstream handoffs, with justified `N/A` where applicable;
9. Primary, Verification, and Final Verification work follows the convergence limits in Section 4.5.4;
10. the Draft Review handoff and coverage matrix together self-prove substantive completeness within the accepted boundary, rather than merely asserting that the Draft is complete;
11. the affected scope has been semantically assessed, including assessed-but-unmutated references, cross-document impact, residuals, dependencies, and qualifications;
12. valid owner-backed `TBD`, `Open`, and deferred items remain visible, while material uncovered, unknown, ownerless, or substantive-completeness gaps block the Stage 8 handoff;
13. mutation scope and broader read-only assessment scope are explicitly separate, and read-only assessment has not expanded writable authority;
14. the Stage 8 handoff is execution evidence in the task context or existing execution record only; no permanent Evidence Pack artifact has been created.
15. for material Draft, all three required Specialist Reviews inspected the complete Draft;
16. the independently appointed Challenger inspected the complete Draft and required evidence for completeness and fidelity without authoring or editing;
17. every evidence-backed accepted-scope objection was corrected, while any unresolved objection remains an explicit blocker that prevents handoff;
18. relevant original Specialist Reviewers reinspected affected meaning after correction;
19. the Challenger reinspected the actual final bytes after all corrections, and any later formal-document or controlling Decision Coverage Matrix change repeated the affected specialist and Challenger closure; and
20. the participant, independence, findings, correction, reinspection, final-artifact, residual, and qualification evidence required by Section 3.1 is complete.

Review validates the Draft; it does not redesign it. Stage 9 independently confirms or refutes the Draft’s substantive-completeness claim against the approved Proposal, authoritative sources, and approved coverage materials. The Stage 8 self-validation and handoff are evidence for this Draft gate only; they are not a Stage 9 Review result or the later lifecycle Validate stage. The Stage 8 Challenger is not Stage 9, does not approve the Draft, and cannot substitute for Stage 9 Primary Review. Corrections that restore fidelity to the approved design may be recommended. A `FAIL` containing accepted-scope findings returns as one consolidated Draft correction scope for that Review phase and its permitted finding boundary. Findings outside the accepted design or scope remain in the Review result and route to Explore or Proposal as applicable; they are not absorbed into Draft correction scope. This does not introduce a numeric failure counter or expanded prompt machinery.

## 7. Align and Integrate Approved Work

Integrate spans Stages 10 to 13 and owns the Change Impact Manifest, coordination of Alignment, Integrated Validation, integration completion, and the pre-commit report. Align supplies only the Consistency behaviour needed to synchronize materially affected documents during Stages 10 and 11.

No Drafting occurs during Integrate. Alignment edits may synchronize approved meaning across dependent documents, but they must not create or alter architecture, ownership, terminology, lifecycle, statuses, object models, or requirements. Any material change returns to Proposal.

### 7.1 Confirm the Accepted Change

Before Alignment or Integration, record:

1. the accepted and reviewed definition, requirement, or behavior;
2. the primary owning document and affected section;
3. the permitted edit scope;
4. unresolved items that remain `TBD`, `Open`, or `To be confirmed`;
5. whether the change replaces an existing definition;
6. whether unrelated changes are prohibited.

If the Founder has not accepted the material product decision, return to Proposal rather than beginning Integration. If the primary-owner Draft has not passed Stage 9 Review, return to Draft or Review as applicable.

Create one task-level **Change Impact Manifest** before Alignment. It should identify:

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

### 7.2 Confirm the Reviewed Primary-Owner Draft

Confirm that the primary owning document:

- already contains the approved meaning from Draft;
- passed the Stage 9 Review gate;
- preserves useful content, documentation layering, established formatting, and stable IDs;
- replaces superseded requirements instead of adding a competing rule;
- keeps assumptions and open decisions visibly distinct from confirmed requirements.

Do not draft, redraft, or redesign the primary owner during Integration. If an accepted-scope correction is needed, return it to Draft and repeat Review before resuming Integration. If the discovery requires a material design change, return it to Proposal.

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

### 7.14 Perform Final Integrated Validation

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

Integrated Validation may identify a material design problem but must not solve it through Integration. Return an evidence gap to Explore and a decision-ready design issue to Proposal.

Use only these stage-result terms:

```text
REVIEW_EXECUTED - GATE_PASS
REVIEW_EXECUTED - GATE_FAIL
CORRECTION_REQUIRED - RETURN_TO_<STAGE>
ALIGN_EXECUTED - PENDING_VALIDATE
VALIDATE_FAIL - RETURN_TO_<STAGE>
REVALIDATE_PASS - READY_TO_INTEGRATE
INTEGRATE_FAIL - RETURN_TO_<STAGE>
INTEGRATE_PASS - READY_FOR_COMMIT_APPROVAL
```

`PASS WITH MAJOR CORRECTIONS` and equivalent mixed results are prohibited. Review may pass or fail only its own Draft Review gate. Align reports execution and unresolved matters, never coordinated success. Validate alone may pass or fail the coordinated Edit/Align result. Every failed result must name the correct return stage. Integrate may report readiness for Commit approval only after coordinated validation passes.

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

Parallel agents are not required for every change except material Stage 5 Proposal and material Stage 8 Draft under the Section 3.1 fixed-seat contract. Otherwise use them when the change is cross-document, conceptually difficult, replaces existing definitions, affects several owners, or has material payment, evidence, promotion, risk, privacy, status, data, route, or operations consequences.

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

Completion and pre-commit reporting must use the canonical stage-result vocabulary in Section 7.14 and must not use ambiguous or mixed PASS terminology.

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

### 11.1 Explore

```text
Explore [topic] under the PayPlus Documentation Development Workflow.
Use Divergent Thinking. Produce the complete Explore Pack: Founder
Clarifications, Existing Repository Findings, Industry Findings, Alternative
Comparison, Conflict Analysis, Risks, Open Questions, and Proposal Inputs.
Keep candidates non-authoritative. Do not recommend a solution, define
architecture, ownership, terminology, lifecycle, statuses, or objects, propose
document edits, edit files, commit, or push. Stop before Proposal.
```

### 11.2 Proposal

```text
Proposal [change] under the PayPlus Documentation Development Workflow.
Use Convergent Thinking. Evaluate sufficient Explore evidence, recommend one
direction, and report rationale, alternatives, rejected alternatives,
trade-offs, impacts, ownership, terminology, architecture, remaining Founder
decisions, and the exact proposed edit boundary. For material Proposal, apply
the Section 3.1 four-seat Round 1, Round 2, and Round 3 contract. Read-only.
Stop at the Founder Decision gate. Do not Draft, commit, or push.
```

### 11.3 Draft

```text
Draft [approved Proposal or equivalent explicit Founder instruction] in
[primary owner]. Use Execution Thinking. Implement only the approved decisions
and writable scope, preserve traceability and consistency, and return the Draft
Review handoff. For material Draft, apply the Section 3.1 four-seat plus
independent Challenger contract and final-byte reinspection. Do not introduce
architecture, redefine ownership or terminology, select alternatives, redesign
requirements, Align, Integrate, commit, or push. Return new design discoveries
to Proposal.
```

### 11.4 Review

```text
Review [draft or target] against [approved Proposal or authoritative source].
Use Validation Thinking. Report correctness, completeness, ambiguity,
inconsistency, documentation quality, and implementation-fidelity findings
with evidence, severity, and ownership. Do not redesign architecture or edit.
Return evidence gaps to Explore and decision-ready design issues to Proposal.
```

### 11.5 Align

```text
Align [reviewed and approved primary change] across only the materially
affected documents. Use Consistency Thinking. Synchronize terminology,
ownership, references, duplicate treatment, and cross-document meaning.
Do not create requirements, redesign the approved work, draft primary-owner
design, commit, or push. Return every material change to Proposal.
```

### 11.6 Integrate

```text
Integrate [approved and reviewed work] under the PayPlus Documentation
Development Workflow. Use Integration Thinking. Complete the Change Impact
Manifest, coordinate Alignment, perform Integrated Validation, determine
integration completion and Definition of Done, and return the pre-commit
report. Do not draft or redraft, alter the approved design, commit, or push.
Return material discoveries to Proposal.
```

### 11.7 Direct Scoped Edit

```text
Apply the PayPlus Documentation Development Workflow to this exact scoped edit:
[scope]. The product decision is already accepted. Confirm the owner and edit
boundary, treat the instruction as the bounded Draft decision contract,
implement only the named scope, perform proportionate Review, Alignment, and
Integration, and report the result. Do not introduce a new design decision,
commit, or push without my separate approval.
```
