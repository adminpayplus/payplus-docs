# DOC-18 - Data Model, Transaction State, Audit Event & Reporting Specification

## 1. Interim Alignment Note

DOC-18 is reserved for the final data model, transaction state, audit event, ledger, reporting, warehouse, and data lineage specification.

Until DOC-18 is drafted in full, future data-model work must preserve the DOC-15 classification model and the domain data structures defined in DOC-05, DOC-09, DOC-10, DOC-11, DOC-12, DOC-13, DOC-14, and DOC-22.

DOC-18 must include data structures for DOC-09 user payment instruction, payment instruction funding leg, deferred funding date, selected payee transfer date, reminder/action task, partial funding status, partial payout linkage, remaining unpaid amount, payment quote revalidation, promotion quote reservation, and changed-term acknowledgement.

Each material object and field should support metadata for:

- DOC-15 data class;
- sensitivity level;
- displayability by role and screen;
- masking or reveal rule;
- retention policy;
- data owner;
- approved purpose;
- access roles;
- audit requirement;
- source system or evidence layer;
- lineage to derived, analytics, reporting, or risk data;
- linkage between request, payment instruction, funding leg, payment attempt, payment quote, promotion quote, settlement record, partial payout item, payout batch, notification, and audit event.

This note is an alignment guardrail only. It is not the final DOC-18 schema.
