# PayPlus Simplified User Flows

These diagrams are presentation-style summaries of the PayPlus experience. They are intended for founder, product, design, and stakeholder discussion where the detailed route-entry map is too dense.

They do not define new routes, statuses, controls, or product behavior. The formal `DOC-XX` documents and the canonical route register remain authoritative. Current hierarchical route maps are indexed in [`docs/diagrams/README.md`](../README.md).

## Diagram Set

| Diagram | Purpose | Primary sources |
| --- | --- | --- |
| [`01-app-overview.png`](01-app-overview.png) | Simple product map from access to the five main navigation areas and key Home shortcuts. | DOC-06A, DOC-06B, DOC-06C |
| [`02-payer-journey.png`](02-payer-journey.png) | Core payer journey from choosing or adding an obligation through evidence/readiness checks, checkout, authorization, and receipt. | DOC-06A, DOC-06C, DOC-09, DOC-12 |
| [`03-payee-request-journey.png`](03-payee-request-journey.png) | Core payee-created request journey from request creation through payer acceptance, payer authorization, payout, and shared records. | DOC-06A, DOC-06B, DOC-09, DOC-10, DOC-12 |

Editable Mermaid sources are stored beside each rendered PNG and SVG as `.mmd` files.

## How to Read the Flows

- Solid arrows show the main user path.
- Dashed arrows show a shortcut, note, or recovery path.
- Blue nodes are main product areas or primary actions.
- Amber nodes are checks or user decisions.
- Green nodes are successful outcomes.
- Red nodes are blocked, rejected, or correction outcomes.

## Product Boundaries Preserved

- A payment request is not a payment.
- Payer acceptance of a payee-created request does not authorize payment.
- Payer authorization is required before payment processing.
- Evidence status and payment readiness remain separate concepts.
- Payer-created payments do not require payee acceptance by default, but evidence, payee/payout, risk, compliance, and authorization gates still apply.
- PayPlus is not shown as a wallet, cashout product, remittance product, or unrestricted peer-to-peer transfer app.
