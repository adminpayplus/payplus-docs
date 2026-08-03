
# Diagrams

This folder stores visual reference artifacts for PayPlus documentation.

Diagrams help human reviewers and AI coding agents understand structure, flow, hierarchy, and relationships. They do not override formal `DOC-XX` source documents.

## Current Diagrams

| File | Purpose | Source / Owner |
| --- | --- | --- |
| `payplus-home-dashboard-mvp-wireframe.svg` | Visual reference for the DOC-06B designated Home Dashboard flow and layout baseline. It is not finalized UI design, visual design, component specification, or exact route-level screen specification. | DOC-06B |
| `routes/payplus-app-route-map.md` | Level 0 app navigation map. It stops at direct global destinations and route-family handoffs. | DOC-06B |
| `routes/payplus-authentication-route-map.md` | Entrance, Fast/Full Login, Registration, Recovery, protected-context return, and the Account Activation handoff. | DOC-06B / DOC-07 / DOC-15 |
| `routes/payplus-account-activation-route-map.md` | Account Activation entry contexts, contextual verification/passcode handoffs, and origin-aware return. | DOC-06B / DOC-15 / DOC-19 |
| `routes/payplus-home-route-map.md` | Home, dashboard shortcuts, and direct dashboard-section handoffs. | DOC-06B |
| `routes/payplus-action-sheet-route-map.md` | Pay+ action-sheet actions, availability decisions, and destination handoffs. It does not define final visual design. | DOC-06B |
| `routes/payplus-bills-route-map.md` | Bills, rent, evidence, activity, reminder, linking, checkout, and Archive-family handoffs. | DOC-06C |
| `routes/payplus-requests-route-map.md` | Requests list/detail/new and Bills/Receiving Info handoffs. | DOC-06B |
| `routes/payplus-instructions-route-map.md` | Payment Instructions, checkout, and Payment Profile handoffs. | DOC-06B / DOC-09 |
| `routes/payplus-payment-profile-route-map.md` | Cards/Profile tabs, child screens, tokenization, and contextual return. | DOC-06B / DOC-09 |
| `routes/payplus-payment-checkout-route-map.md` | Current discussion-reference projection of the accepted payer-visible adaptive Checkout Workspace journey, result-specific treatment, and safe exits. It is not a fixed wizard or domain-state map. | DOC-06B / DOC-09 |
| `routes/payplus-activity-receipts-route-map.md` | Account Activity, Receipts & Statements, and contextual Bills Activity handoffs. | DOC-06B / DOC-06C |
| `routes/payplus-offers-rewards-referral-route-map.md` | Offers discovery, Rewards, Referral, registration attribution, and checkout handoffs. | DOC-06B / DOC-13 |
| `routes/payplus-me-route-map.md` | `ME-ROOT` direct child destinations plus Account Profile and Account Security handoffs to phone, identity, and payment-passcode controls. | DOC-06B |
| `routes/payplus-more-route-map.md` | Compact `MORE-ROOT` route boundary, Normal/Manage modes, and generic handoff to independently owned destinations. Detailed shortcut behavior remains in DOC-06B. | DOC-06B |
| `routes/payplus-archive-route-map.md` | `ARCHIVED-ROOT`, Archived Bills & Rent, Archived Documents, archived detail, and restore handoffs. | DOC-06B / DOC-06C |
| `routes/payplus-notification-route-map.md` | Notifications parent, Inbox, Detail, Settings, Home/Me entries, and owning-destination handoff. | DOC-06B / DOC-08 |
| `payplus-promotion-engine-structure.md` | Mermaid business-structure reference for the unified promotion engine, program contexts, campaigns, offers, rule evaluation, and benefit-delivery paths. DOC-13 remains authoritative. | DOC-13 |

## Superseded Snapshots

| File | Status | Replacement |
| --- | --- | --- |
| `routes/archive/payplus-app-route-entry-map-2026-07-26-v1.md` | Superseded, non-authoritative snapshot of the former all-in-one route map. | Active hierarchical maps under `routes/`. |

## Rules

- Keep diagrams aligned with the owning source document.
- Use an app-level map for direct global destinations and route-family maps for detailed trees; do not duplicate a child family's full tree in its parent map.
- Treat `docs/traceability/route-register.md` as the canonical destination inventory and definition-status source.
- Mark whether a diagram is a final approved design, discussion reference, or implementation aid.
- Do not treat diagrams as source of truth when they conflict with formal documentation.
- Preserve replaced governed diagrams as dated, clearly superseded snapshots and keep them out of the Current Diagrams table.
- Do not place real customer, identity, card, bank, payment, or evidence data in diagrams.
