# PayPlus Simplified User Flows

These diagrams are presentation-style summaries of the PayPlus experience. They are intended for founder, product, design, and stakeholder discussion where the detailed route-entry map is too dense.

They do not define new routes, statuses, controls, or product behavior. The formal `DOC-XX` documents and the canonical route register remain authoritative. Current hierarchical route maps are indexed in [`docs/diagrams/README.md`](../README.md).

## Diagram Set

| Diagram | Purpose | Primary sources |
| --- | --- | --- |
| Former app-overview journey | Superseded and unavailable; no current image is registered. | Historical provenance only |
| Former payer journey | Superseded and unavailable; no current image is registered. | Historical provenance only |
| Former payee-request journey | Superseded and unavailable; no current image is registered for the retired Request runtime. | Historical provenance only |

Editable Mermaid sources, when present, are stored beside their rendered PNG or SVG as `.mmd` files.

## How to Read the Flows

- Solid arrows show the main user path.
- Dashed arrows show a shortcut, note, or recovery path.
- Blue nodes are main product areas or primary actions.
- Amber nodes are checks or user decisions.
- Green nodes are successful outcomes.
- Red nodes are blocked, rejected, or correction outcomes.

## Product Boundaries Preserved

- Payer authorization is required before payment processing.
- Evidence status and payment readiness remain separate concepts.
- Category-bound source and Evidence gates remain separate from payment readiness.
- PayPlus is not shown as a wallet, cashout product, remittance product, or unrestricted peer-to-peer transfer app.
