# PayPlus Prototype Registry

This folder contains review aids derived from approved PayPlus source documents. Prototypes do not create product requirements and must not override the owning documents.

## Current Prototype

No current prototype is registered.

A prototype may be listed here only after its scope, source baseline, status, and required specialist validation have been recorded under the [`PayPlus Prototype Design and Validation Specialist Guide`](../documentation-system/payplus-prototype-design-validation-specialist-guide.md) and processed through the canonical [`Documentation Development Workflow`](../documentation-system/payplus-documentation-development-workflow.md).

## Lifecycle Rules

- Keep at most one current prototype for the same product scope.
- A prototype must identify its status, source baseline, owning documents, last validation date, and known limitations.
- When a current prototype is superseded, either delete it if it has no continuing comparison value or move it to `archive/<prototype-name>-<version>-<YYYY-MM-DD>/`.
- Archived prototypes must remain clearly labelled non-current.
- Product discoveries from a prototype must return to the owning source document before implementation.
- Only a prototype validated against an immutable source commit may be labelled `Validated Reference`.

No archived prototype is retained at this baseline. The earlier `doc06-route-prototype` was removed because it duplicated the same scope using superseded route and document assumptions.
