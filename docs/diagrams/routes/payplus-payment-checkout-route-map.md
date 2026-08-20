# PayPlus Payment Checkout Route Map

Status: Current discussion reference
Owner: DOC-06B for route-level UI/UX; DOC-09 for Payment Domain architecture
Last updated: 2026-08-19

This derived diagram projects the reviewed payer-visible `PAYMENT-CHECKOUT` journey from DOC-06B Section 5.20. DOC-06B remains the primary source for adaptive presentation behavior, DOC-09 remains authoritative for payment-domain facts and invariants, and the route register remains authoritative for destination identity and definition status.

The projection is not a mandatory fixed wizard, a route hierarchy, a machine-state model, or a source of new payment requirements. The numbered nodes are replaceable Workspace presentations that may overlap, combine, or be skipped according to the authoritative Checkout condition and the payer's current permitted task.

```mermaid
flowchart TD
    SRC["Bill/Rent source route<br/>DOC-06C"] -->|"Select item(s) and Pay"| R{"Checkout resolution<br/>DOC-09 condition"}
    INS["INSTRUCTIONS-DETAIL<br/>current Pay Now"] -->|"Validate payer, Instruction, and action"| R
    NOTIF["Instruction-related notification"] --> NDETAIL["NOTIFICATION-DETAIL"]
    NDETAIL -->|"Current-state, payer, permission,<br/>target, and action revalidation;<br/>owner-approved Pay Now"| R
    NDETAIL -->|"Action unavailable"| H

    R -->|"Eligible new Checkout"| N["1. New Checkout overview"]
    R -->|"Valid Resume"| O["1. Resume overview"]
    R -->|"Unavailable"| H["Source or historical resolution"]

    subgraph WORKSPACE["PAYMENT-CHECKOUT - one persistent Workspace"]
        N -->|"Funding is the next permitted task"| F["2. Choose or change funding"]
        O -->|"Funding is the next permitted task"| F

        F -->|"Default eligible path"| SC["Single card"]
        F -->|"Use multiple cards"| MC["Multi-card or Payment Profile"]

        SC --> V["3. Review amount, fees and benefits"]
        MC --> V

        V --> A["4. Authorize next Provider Submission"]
        A --> E["5. Funding Leg progress"]
        E --> C{"Authoritative result"}

        C -->|"Fully funded"| D["6. Fully funded completion"]
        C -->|"Partially funded"| P["6. Partial result"]
        C -->|"Evidence pending"| W["6. Pending result"]
        C -->|"Unsuccessful"| U["6. Unsuccessful result"]

        P -->|"Continue or adjust if permitted"| F
        P -->|"Wait where evidence remains pending"| W
        W -. "Authoritative evidence update" .-> C
        U -->|"Owner-confirmed recovery"| F
    end

    D --> X["Safe completion exit"]
    P -->|"Close if permitted"| H
    P -->|"Safe return; continuation preserved"| X2["Safe return or approved later continuation"]
    W -->|"Safe return"| X2
    U -->|"Close if permitted"| H
    U -->|"Safe return"| X2

    classDef source fill:#f3f4f6,stroke:#4b5563,color:#111827,stroke-width:1.5px;
    classDef presentation fill:#e8f2ff,stroke:#2563eb,color:#102a43,stroke-width:1.5px;
    classDef condition fill:#fff4cc,stroke:#b7791f,color:#4a2c00,stroke-width:1.5px;
    classDef completion fill:#e5f7ed,stroke:#238636,color:#0f3d1f,stroke-width:1.5px;
    classDef resolution fill:#f5f0ff,stroke:#7c3aed,color:#2e1065,stroke-width:1.5px;

    class SRC,INS,NOTIF,NDETAIL source;
    class N,O,F,SC,MC,V,A,E,P,W,U presentation;
    class R,C condition;
    class D,X completion;
    class H,X2 resolution;
    style WORKSPACE fill:#ffffff,stroke:#2563eb,stroke-width:2px
```

## Interpretation

- `PAYMENT-CHECKOUT` is the only registered route/flow group in the blue Workspace boundary. Its numbered nodes and funding/result nodes are adaptive internal presentations, not child routes, domain objects, machine states, or a required universal screen order.
- Bill admission consumes the accepted C1/G1/G2 and highest-tier handoff. Tier 2 requires qualifying official Bill Evidence presence before Payment; acceptance may remain pending while Payout is held. Tier 3 may preserve this Workspace as prepared context but remains non-executable before Evidence and approval, with no executable authorization or Provider Submission.
- G1 is the product-semantic receiving-account/authoritative-payout-destination progression handoff and G2 consumes proposed pre-check versus actual confirmed value; neither is a technical Payment-record or route-state definition.
- Rent follows its separate mandatory attached-Evidence and acceptance-before-Payment rule and does not use Bill Tier 1/2/3 semantics.
- Amber diamonds are owner-controlled domain or evidence conditions used to select a valid presentation; they are not payer-visible screens or new status definitions. Grey and purple nodes are source, historical-resolution, or safe-exit handoffs outside ordinary Checkout composition and do not create a destination that is absent from the route register.
- Intentional Resume proceeds to Funding only when Funding is the next permitted task. Otherwise DOC-06B's decision map and Minimum Adaptive UI Contract restore the applicable Review, progress, pending, result, or safe-return presentation after required revalidation.
- Approved Card, Payment Profile, provider, 3DS, reauthentication, and application handoffs return to the safest valid presentation only after the checks owned by the applicable domain, provider, and security documents; the diagram intentionally leaves that detailed resolution in DOC-06B.
- Fully funded completion is terminal and exposes no Funding, Continue, adjust, retry, wait, or Close Checkout action. Pending evidence exposes no retry or alternate-funding submission while evidence remains unresolved. Partial and unsuccessful results expose only owner- and condition-permitted actions.
- Late confirmation remains outside ordinary Checkout continuation and follows DOC-09's independent controlled-resolution treatment.
- Instruction `Pay Now` invokes the DOC-09 Checkout Resolver rather than predetermining new-versus-Resume identity. An existing Checkout resumes only when it remains active, eligible, and continuable; a later eligible Checkout may begin only when no active continuable Checkout exists; otherwise the payer receives the applicable source or historical resolution.
- Every instruction-related notification enters `NOTIFICATION-DETAIL` first. Notification content and delivery do not establish current eligibility or result; only after current-state, payer, permission, target, and action-availability revalidation may an owner-approved current CTA invoke the same resolver. There is no notification-to-Checkout bypass edge.
- Payment Instruction and Checkout remain separate. Earlier Checkouts remain authoritative in their recorded non-continuable condition and are not reactivated or rewritten. Resolver entry carries no stale authorization and silently creates no Funding Allocation, Funding Leg, Payment Attempt, or Provider Submission.

## References

- [DOC-06B Section 5.20](../../01-product/doc-06b-navigation-ia-route-taxonomy.md)
- [DOC-09 Payment Domain Architecture](../../02-payment-domain/doc-09-payment-domain-architecture.md)
- [Product Destination Register](../../traceability/route-register.md)
- [Open Questions Register](../../traceability/open-questions-register.md)
