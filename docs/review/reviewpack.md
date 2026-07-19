# Founder Review Pack: Offers Child Lists

## 1. Task And Boundary

Apply the PayPlus Level 1 parallel-agent review to:

- `OFFERS-CARD-LIST`
- `OFFERS-PAYPLUS-LIST`
- `OFFERS-PARTNER-LIST`

In scope: screen structure, cards, search and filter behavior, ordering, states, navigation, collection membership, ownership, and future document changes.

Out of scope: exact visual styling, campaign calculation, reward issuance, referral logic, checkout, redemption fulfilment, technical schemas, and admin-dashboard UI.

This is a proposal for founder review. It does not make the proposed decisions authoritative until approved and recorded in the owning documents.

## 2. Current Repository Position

- The three child screens already exist as minimal shells in `DOC-06B`.
- The Mermaid route topology is correct.
- `DOC-13` defines discovery groups and offer metadata but not multi-collection membership or duplicate-placement rules.
- `DOC-06D` incorrectly refers to `entry-point IDs`.

## 3. Proposed Decisions

| ID | Recommended decision | Rationale |
| --- | --- | --- |
| `OCL-01` | Treat all three as child collection screens under `OFFERS-ROOT`. | They browse collections; they do not own promotion logic. |
| `OCL-02` | Define one shared collection-screen contract with route-specific differences. | Prevents duplication while preserving clear behavior. |
| `OCL-03` | Search, labels, filters, sorting, and result states remain screen states, not routes. | No materially different destination exists. |
| `OCL-04` | Cards open `OFFER-DETAIL`; material actions do not execute from list cards. | Keeps discovery separate from redemption, checkout, and external handoff. |
| `OCL-05` | Permit one offer to belong to multiple collections. | Card applicability, PayPlus management, and partner sponsorship are different classification dimensions. |
| `OCL-06` | Suppress duplicate offers on `OFFERS-ROOT`, while permitting them in every applicable child list. | Keeps the root concise without weakening complete collections. |
| `OCL-07` | Use stable admin-priority ordering; no randomization or user sorting in child lists for MVP. | Supports predictable browsing and return-state preservation. |
| `OCL-08` | Display may precede final transaction eligibility confirmation. | Users may discover offers before selecting a card or payment context. |
| `OCL-09` | Use a single-column mobile list and single-select labels for MVP. | Offer cards contain material conditions that need readable space. |

## 4. Shared Screen Structure

1. Header: Back, collection title, and Search.
2. Search field when activated.
3. Label-filter row where applicable.
4. Scrollable offer collection.
5. Loading-more indicator where needed.
6. Empty, no-results, or recoverable-error state where applicable.

Back closes active Search first. Otherwise, it returns to the originating `OFFERS-ROOT` section and restores its position.

## 5. Shared Offer Card

Show:

- approved key visual or identity mark;
- PayPlus, issuer, sponsor, or partner identity;
- offer title;
- concise benefit;
- material category, card, or payment-method condition;
- expiry or `Ending Soon`;
- concise availability or use-method description;
- `View Details`.

The entire card may be tappable. Redemption, card application, checkout, QR presentation, external links, and partner handoff remain in `OFFER-DETAIL`.

## 6. Route Differences

| Route | Collection and controls |
| --- | --- |
| `OFFERS-CARD-LIST` | Card or payment-method offers. Search offer, issuer, card product, scheme, partner, and benefit. No visible label filter for MVP. Never claim final eligibility solely from saved-card or BIN detection. |
| `OFFERS-PAYPLUS-LIST` | PayPlus-branded or PayPlus-managed offers. Search plus `All` and single-select label filters. Show applicable bill, fee, rent, payment, or service-fee context. |
| `OFFERS-PARTNER-LIST` | External-partner offers. Search plus `All` and single-select label filters. Clearly identify the partner and whether use is in-app or external. |

## 7. Business And System Rules

- `All offers` means active, approved, scheduled, and currently displayable offers assigned to that collection after visibility, consent, targeting, and compliance gates.
- Display does not confirm final payment eligibility. `DOC-13` and `DOC-09` revalidate card, quota, budget, payment, and checkout conditions.
- `Featured/Hot` is a placement flag, not an offer type.
- Child-list ordering applies mandatory display gates, admin priority, approved personalization, and then a deterministic fallback.
- Ordering remains stable during the navigation session.
- Returning from `OFFER-DETAIL` restores route, search, label, loaded results, and scroll position.
- Cards must not expose BINs, internal targeting reasons, risk signals, or sensitive evidence-derived information.
- Future `DOC-18` events should cover impressions, position, searches, filters, no-results, offer opens, and returns.
- `DOC-22` should govern labels, placement, priority, targeting, enablement, scheduling, and audit history.

## 8. Screen States

- Loading: skeleton cards without fabricated content.
- Empty: no currently available offers; no create action.
- No results: `Clear Search` or `Reset Filters`.
- Error: non-sensitive message and `Retry`, preserving state.
- Expired or withdrawn: `OFFER-DETAIL` shows unavailable and disables material actions.
- Personalization unavailable: show the approved generic collection.
- No collection-level `Action Required` state.

## 9. Ownership And Handoffs

| Document | Ownership or handoff |
| --- | --- |
| `DOC-06B` | Route UX and navigation owner. |
| `DOC-13` | Campaign, offer, eligibility, redemption, benefit, and collection-membership owner. |
| `DOC-09` | Checkout and payment validation. |
| `DOC-15` | Privacy, targeting, and approved-purpose data use. |
| `DOC-18` | Future data objects, events, lineage, and analytics. |
| `DOC-22` | Future admin configuration and placement operations. |
| `DOC-06D` | Acceptance coverage. |

## 10. Exact Future Document Changes

- `DOC-06B`: add the shared contract, route differences, states, ordering, and return behavior.
- `DOC-06D`: replace `entry-point IDs` with source/action/destination/return transitions and add acceptance tests.
- `DOC-13`: add approved multi-collection membership, root duplicate suppression, and PayPlus classification rules.
- Parent `DOC-06` and the traceability matrix: update completion and test references.
- Route Mermaid: no topology change; add definition-status annotation only if useful.
- `DOC-18` and `DOC-22`: add future ownership markers only where missing.
- Check but otherwise leave unchanged: `DOC-00`, `DOC-05`, `DOC-08`, `DOC-09`, `DOC-15`, `AGENTS.md`, `docs/README.md`, and the Product Charter.

## 11. Replacement And Consistency Effects

- Replace the stale `entry-point IDs` wording in `DOC-06D`; do not create entry IDs for search, filters, or collection entry actions.
- Keep route ownership separate from promotion-engine ownership.
- Keep offer discovery separate from checkout, reward management, referral, and payment authorization.
- Keep display eligibility separate from final transaction eligibility.
- Do not redefine notification, privacy, checkout, or benefit-calculation rules in `DOC-06B`.

## 12. Reviewer Findings

All Level 1 reviewers agreed on the shared contract, route boundaries, stable child-list ordering, detail handoff, and absence of direct material actions.

The principal unresolved question was whether currently ineligible offers should be hidden. The recommendation is to hide offers failing mandatory display, privacy, or compliance gates, but allow publicly discoverable offers whose final card or transaction eligibility is not yet known.

The consistency review also found that Card, PayPlus, and Partner collections use different classification dimensions. Treating them as mutually exclusive would create unnecessary promotion-engine constraints.

## 13. Meaningful Alternatives

| Alternative | Decision and reason |
| --- | --- |
| Mutually exclusive collections | Not recommended because card applicability and sponsorship can overlap. |
| Random child-list ordering | Not recommended because it disrupts browsing and return context. |
| Direct material actions on cards | Not recommended because conditions must be reviewed in `OFFER-DETAIL`. |
| Two-column grid | Defer as a responsive design option; single-column is recommended for MVP. |
| Multi-select filters | Defer; single-select is simpler and sufficient initially. |
| Hide every currently ineligible offer | Not recommended when the offer is publicly discoverable and final eligibility requires later context. |

## 14. Open Questions And Deferred Details

Required now:

1. Confirm `OCL-05` and `OCL-06`: multi-collection membership and root-level duplicate suppression.
2. Confirm whether `Pay+ Offers` means PayPlus-branded or PayPlus-managed regardless of funding source.
3. Confirm the treatment of discoverable offers whose final eligibility is not yet known.

May remain `TBC`:

- PayPlus and Partner label taxonomy.
- Equal-priority fallback ordering.
- Card issuer or network filters after MVP.
- Whether personalization affects inclusion, ordering, or both.
- Exact card design and responsive breakpoint.
- Whether list state survives only the navigation session or later visits.

## 15. Founder Approval Checklist

Mark each proposal as `Accept`, `Amend`, `Reject`, or `Defer`:

| Proposal | Decision |
| --- | --- |
| `OCL-01` Route classification | |
| `OCL-02` Shared collection contract | |
| `OCL-03` Search, filter, and state classification | |
| `OCL-04` Detail-only material actions | |
| `OCL-05` Multi-collection membership | |
| `OCL-06` Root duplicate suppression | |
| `OCL-07` Stable ordering without MVP user sorting | |
| `OCL-08` Display versus final eligibility | |
| `OCL-09` MVP list and filter layout | |
