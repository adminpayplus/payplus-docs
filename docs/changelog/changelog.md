# PayPlus Documentation Changelog

## 1. Purpose

This append-only register records the documentation delivered by each substantive commit. It complements the decision log and does not replace formal document version histories.

## 2. Recording Standard

- Add one entry after every substantive documentation commit.
- Record the substantive commit identifier and actual delivered files.
- Summarize material changes, replaced definitions, validation performed, and remaining open items.
- Link each change to its primary owning document and decision-log entry where applicable.
- Apply the PayPlus writing, ownership, source-of-truth, scope, and review standards from `AGENTS.md`.
- Preserve history; correct errors through a dated correction instead of silently deleting prior entries.

## 3. Changelog Entry Template

### `YYYY-MM-DD` - Change Title

| Field | Record |
| --- | --- |
| Substantive commit | Commit identifier |
| Primary owner | `DOC-XX`, section |
| Decision record | `DEC-YYYY-NNN` or `Not applicable` with reason |
| Founder approval | Approval source or date |

**Files Changed**

- List the files included in the substantive commit.

**Material Changes**

- Summarize delivered requirements, replacements, ownership changes, alignment, and metadata updates.

**Checks Performed**

- Record integration, consistency, formatting, diagram, acceptance, and traceability checks performed.

**Remaining Open Items**

- List surviving `TBC` or open questions. Otherwise state `None`.
