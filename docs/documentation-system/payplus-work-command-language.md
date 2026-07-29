# PayPlus Work Command Language

## 1. Purpose and Classification

This document is the normative command-interface reference for PayPlus documentation work. It gives the Founder a small, stable vocabulary for stating work intent and tells an agent how to route that intent into the canonical [Documentation Development Workflow](payplus-documentation-development-workflow.md).

This reference owns command meaning, minimum command inputs, expected outputs, and routing. It is not a workflow and does not own or redefine lifecycle stages, gates, roles, validation authority, Git treatment, records treatment, Push, or Completion. Those rules remain exclusively owned by the Documentation Development Workflow. [`DOC-00`](../00-foundation/doc-00-documentation-governance.md) remains the documentation-governance authority, and [`AGENTS.md`](../../AGENTS.md) remains the repository operating contract and routing layer.

If this reference conflicts with the Documentation Development Workflow on a lifecycle matter, the workflow governs. A command selects an intended work mode or lifecycle destination; it never supplies an approval that the Founder did not explicitly give.

## 2. Command Contract

A useful command has this compact form:

```text
[Command] [target].
Goal: [desired outcome].
Scope: [included files or subject].
Boundary: [read-only, editable files, or explicit exclusions].
Stop at: [required report or approval gate].
Parallel agents: [not requested / may be recommended / authorized when useful].
Git: [no commit or push / specific authorization].
```

The Founder may omit fields that are already clear from current repository context. The Documentation Lead must confirm or safely infer the minimum task contract required by the canonical workflow: target and outcome, primary owner, authoritative sources, scope and exclusions, expected output, stopping condition, and Git authorization. If a missing field could materially expand scope or authority, stop at the applicable canonical gate.

Commands are case-insensitive in ordinary prompts. When several commands are chained, execute them in canonical lifecycle order and stop at the first unsatisfied gate.

## 3. Core Command Matrix

Stage numbers below are routing references only. Their definitions and all skip, entry, return, approval, and completion rules remain in the Documentation Development Workflow.

| Command | Purpose and allowed change | Minimum input | Expected output | Canonical lifecycle mapping | Stop / approval gate | Parallel agents |
| --- | --- | --- | --- | --- | --- | --- |
| **Explore** | Investigate the problem, current baseline, options, dependencies, and risks. Read-only; do not select or write an accepted solution. | Topic, goal, material constraints | Evidence summary, option space, ownership candidates, risks, open questions | Stages 1-4; may inform Stage 5 | Stop before Proposal or any edit unless separately requested | May be recommended or used when authorized for independent research or specialist coverage |
| **Proposal** | Produce a decision-ready recommendation. Read-only unless an exact edit scope was already authorized. | Problem or candidate change, intended decision, constraints | Recommended structure, primary owner, impact analysis, alternatives, open questions, proposed edit boundary | Stages 1-5 | Stop at Stage 6 Founder Decision | May be recommended or used when authorized for analysis and challenge |
| **Approve** | Record an explicit Founder decision or authorization for the named gate. It does not perform downstream work unless that work is also requested. | Exact decision or action, scope, applicable gate | Decision record in the task context and the next permitted action | Stage 6, 14, or 18 according to the named approval | Founder-only command; ambiguous approval must be clarified | Not applicable as delegated authority |
| **Draft** | Create or revise accepted content in the primary owner. Editing is limited to the approved scope. | Accepted decision or exact edit scope, primary owner, writable files | Primary-owner draft, assumptions and open items, draft-review handoff | Stages 7-9 | Stop for unresolved material decisions; otherwise at the Draft Review gate | May be used when authorized; one canonical writer controls each formal document |
| **Review** | Examine sources, a draft, or a diff and report findings. Read-only unless a separate Edit command or corrective scope is authorized. | Review target, review lens, authority sources | Findings with severity, evidence, ownership, recommendations, and unresolved items | Stage 4 or 9; may support Stage 12 when explicitly scoped as validation review | Stop before edits, approval, or Git action | May be recommended or used when authorized to improve independence or coverage |
| **Edit** | Apply an exact accepted correction without inventing a new material decision. | Exact change, target owner, writable-file allowlist | Scoped edits and proportionate impact report | Stages 5-12 as applicable to the accepted scope | Stop on scope expansion or a new material decision; no Commit authority | May be used when authorized; file ownership and independent review rules still apply |
| **Align** | Synchronize materially affected owners and references after the primary change. Do not create new requirements. | Accepted primary change, Change Impact Manifest or affected-document set | Owner-first cross-document updates and unresolved conflicts | Stages 10-11 | Stop on new material decisions, ownership conflict, or scope expansion | May be used when authorized for disjoint files or review; Integration Lead consolidates |
| **Validate** | Test the coordinated result against scope, ownership, consistency, links, format, and applicable acceptance criteria. Read-only except for separately authorized corrections. | Intended scope, changed files, applicable checks | PASS/FAIL evidence, unresolved items, and commit-readiness blockers | Stages 12-13 | Failed checks block commit readiness; does not authorize Commit | May be used when authorized for specialist checks; canonical validation conclusion remains with the workflow |
| **Integrate** | Complete impact analysis, Align affected artifacts, Validate the coordinated result, and prepare the pre-commit report. | Accepted primary change, writable scope, repository baseline | Integrated diff, validation evidence, open issues, and pre-commit report | Stages 10-13 | Stop at Stage 14 Commit approval unless Commit is separately authorized | May be used when authorized; the Integration Lead owns consolidation |
| **Commit** | Create the approved substantive commit for the exact validated scope. | Explicit Founder Commit approval and intended file set | Substantive commit identifier and included-file report | Stages 14-15 | Must not start without Stage 14 approval; does not by itself authorize Push | Parallel agents may review; one Change Integrator performs the controlled Git action |
| **Record** | Update the changelog and decision log and create the required records-only follow-up commit. | Approved substantive commit and accurate delivered scope | Updated records and records-only commit identifier | Stages 16-17 | Covered only by the applicable canonical Commit approval; no Push authority | Normally serial under the Change Integrator |
| **Push** | Push the approved substantive and records commits. | Explicit Founder Push approval and exact commits/remote | Push result and remote commit identifiers | Stages 18-19 | Must not start without Stage 18 approval | Normally serial under the Change Integrator |
| **Complete** | Report final state and evidence after every applicable prior gate passes. No editing or Git authority. | Lifecycle evidence and remaining issues | Completion report, including unresolved or deferred items | Stage 20 | Must not claim completion while an applicable gate or material issue remains open | Not normally required |

## 4. Subject Qualifiers, Not Competing Lifecycle Commands

`Prototype` and `Specify` identify the artifact or specialist method; they do not create separate lifecycle paths.

- **Prototype** routes the task to the [Prototype Design and Validation Specialist Guide](payplus-prototype-design-validation-specialist-guide.md). Pair it with a core command, such as `Explore Prototype`, `Draft Prototype`, or `Review Prototype`.
- **Specify** routes DOC-07 work to the [DOC-07 Design Specification Specialist Guide](payplus-doc-07-design-specification-specialist-guide.md) and, when applicable, the [Outcome Framework](../00-foundation/payplus-outcome-message-notification-framework.md). Pair it with a core command, such as `Proposal Specify`, `Draft Specify`, or `Validate Specify`.

If the Founder uses `Prototype` or `Specify` alone, the Documentation Lead must infer the least expansive safe core command from the requested outcome. When intent is unclear, default to Explore or Review rather than editing.

## 5. Command Interpretation Rules

1. Start with `AGENTS.md`, the primary owner, and the Documentation Development Workflow.
2. Treat the named command as the requested mode or destination, not permission for later stages.
3. Preserve the distinction between read-only commands and editing commands.
4. Apply the narrowest scope consistent with the request; do not turn `Edit` into redesign or `Align` into new requirements.
5. A chained prompt such as `Draft, Align, Validate` authorizes those actions only within the accepted writable scope. It still does not authorize Commit or Push.
6. `Commit`, `Record`, and `Push` retain their canonical sequencing and approval gates. A general request to finish local edits is not Git authorization.
7. Use the [Parallel-Agent Documentation Procedure](payplus-parallel-agent-documentation-procedure.md) only when parallel execution is explicitly requested or authorized. The Lead may recommend it when independent review, specialist coverage, or delivery quality would materially improve.
8. If role coverage is insufficient, apply the Parallel Procedure's Adaptive Role Coverage rules; do not invent expertise or claim an unperformed review passed.
9. Route any new material decision, ownership change, scope expansion, or authority conflict to the applicable Founder gate.
10. Report the command interpreted, lifecycle stage reached, files changed, validation performed, unresolved matters, and Commit/Push status.

## 6. Founder Prompt Templates

### Explore

```text
Explore [topic]. Map the current baseline, owners, dependencies, options, and
risks. Read-only. Do not recommend one final solution or edit files. Stop with
open questions and the next sensible command.
```

### Proposal

```text
Proposal [change]. Identify the canonical owner and affected documents, compare
material alternatives, and return a decision-ready recommendation with an exact
edit boundary. Read-only. Stop for my Founder Decision.
```

### Draft, Align, and Validate

```text
Draft [accepted change] in [primary owner], then Align only the materially
affected references and Validate the coordinated result. Preserve unrelated
changes. Stop with the pre-commit report. Do not Commit or Push.
```

### Review

```text
Review [target] for [product/domain/consistency/acceptance] concerns. Read-only.
Return evidence-backed findings, ownership, impact, and recommended corrections.
Do not Edit, Commit, or Push.
```

### Exact Edit

```text
Edit [target] to apply this accepted correction: [exact change]. Writable scope:
[files]. Do not add new requirements. Validate the result and stop before Commit.
```

### Integrate

```text
Integrate [accepted change]. Confirm the Change Impact Manifest, Align affected
owners and references, Validate the coordinated result, and prepare the canonical
pre-commit report. Do not Commit or Push.
```

### Commit, Record, and Push

```text
Commit the exact validated scope in [files]. This is explicit Founder Commit
approval. Then Record the substantive commit through the required changelog and
decision-log follow-up. Do not Push.
```

```text
Push substantive commit [id] and records commit [id] to [remote/branch]. This is
explicit Founder Push approval. Report the remote result, then Complete.
```

### Authorized Parallel Support

```text
[Command] [target]. You may use parallel agents where this materially improves
independent review, specialist coverage, or delivery quality. Apply Adaptive Role
Coverage, keep one canonical writer per formal document, and return control to
the mapped Documentation Development Workflow stage.
```
