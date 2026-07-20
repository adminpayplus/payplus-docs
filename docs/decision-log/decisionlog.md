# PayPlus Decision Log

## 1. Purpose

This append-only register records accepted PayPlus product, documentation, governance, ownership, workflow, technical, operational, risk, privacy, and implementation-boundary decisions after the substantive commit implementing them exists.

Formal source documents remain authoritative. This log records why and where a decision was implemented; it does not replace the owning document.

## 2. Recording Standard

- Use one stable ID per material decision: `DEC-YYYY-NNN`.
- Record only founder-approved decisions or an explicit `Not applicable` result for commits without a substantive decision.
- Identify the primary owning document and all materially affected documents.
- Include the substantive commit identifier, not the records-only follow-up commit identifier.
- Keep confirmed decisions separate from assumptions and remaining `TBC` items.
- Record meaningful alternatives and reasons for rejection where they affected the decision.
- Preserve history. Use `Superseded` or a dated correction rather than deleting an earlier decision.
- Apply the PayPlus Product Drafting Method, source-ownership rules, writing standards, and PayPlus boundary checks from `AGENTS.md`.

## 3. Decision Index

| Decision ID | Date | Title | Status | Primary Owner | Substantive Commit |
| --- | --- | --- | --- | --- | --- |

## 4. Decision Record Template

### `DEC-YYYY-NNN` - Decision Title

| Field | Record |
| --- | --- |
| Date | `YYYY-MM-DD` |
| Status | Accepted / Superseded / Not applicable |
| Primary owner | `DOC-XX`, section |
| Affected documents | List only materially affected files or document IDs |
| Substantive commit | Commit identifier |
| Founder approval | Approval source or date |

**Decision**

State the accepted rule compactly and decisively.

**Rationale**

Explain why the decision was selected.

**Alternatives Considered**

List only meaningful alternatives and why they were not selected.

**Consequences And Handoffs**

Record material UX, payment, promotion, risk, privacy, data, admin, acceptance, operational, or implementation consequences and their owners.

**Supersedes / Superseded By**

Reference earlier or later decision IDs where applicable. Otherwise state `None`.

**Remaining Open Items**

List any surviving `TBC`, open question, or professional-assessment item. Otherwise state `None`.
