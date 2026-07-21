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
| `DEC-2026-001` | `2026-07-20` | Post-Commit Documentation Records | Accepted | `DOC-00` | `36458da` |
| `DEC-2026-002` | `2026-07-20` | Offers Child-List Collection And Display Rules | Accepted | `DOC-13` | `36458da` |
| `DEC-2026-003` | `2026-07-20` | Card Offer Selection And Checkout Combination | Accepted | `DOC-13` | `36458da` |

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

## 5. Accepted Decisions

### `DEC-2026-001` - Post-Commit Documentation Records

| Field | Record |
| --- | --- |
| Date | `2026-07-20` |
| Status | Accepted |
| Primary owner | `DOC-00`, documentation governance |
| Affected documents | `AGENTS.md`, `DOC-00`, Documentation Change Integration and Commit Workflow, `docs/README.md`, changelog, decision log |
| Substantive commit | `36458da` |
| Founder approval | Approved in the founder review task on `2026-07-20` |

**Decision**

Every substantive documentation commit must be recorded in the changelog and decision log using its actual commit identifier. The registry changes are then committed in one immediate records-only follow-up commit before push or completion is reported.

**Rationale**

The substantive commit identifier does not exist before commit creation. A follow-up records-only commit preserves accurate traceability without leaving permanent uncommitted registry changes.

**Alternatives Considered**

- Recording a planned identifier before commit was rejected because it could be inaccurate.
- Requiring each records-only commit to record itself was rejected because it would create an infinite commit-recording loop.

**Consequences And Handoffs**

Agents must prepare record content before commit, create the substantive commit, add the actual commit identifier to both registries, validate the registry diff, and create the records-only follow-up commit. Records-only commits are exempt from self-recording unless they introduce another substantive decision.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

None.

### `DEC-2026-002` - Offers Child-List Collection And Display Rules

| Field | Record |
| --- | --- |
| Date | `2026-07-20` |
| Status | Accepted |
| Primary owner | `DOC-13`, promotion engine |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-13`, `DOC-18`, `DOC-22`, promotion-engine diagram, traceability matrix |
| Substantive commit | `36458da` |
| Founder approval | OCL-01 to OCL-09 accepted or clarified in the founder review task on `2026-07-20` |

**Decision**

Card Offers, PayPlus Offers, and Partner Offers use a shared child-list behavior contract with route-specific titles, content criteria, and filters. One offer may belong to multiple collections. The Offers root suppresses duplicate Offer IDs through one admin-selected primary placement with an audited override, while child lists use stable configured ordering rather than randomization or user sorting for MVP.

**Rationale**

The shared contract keeps route behavior predictable and compact while collection membership supports overlapping commercial classifications without duplicating the underlying offer.

**Alternatives Considered**

- Creating separate offer records for every collection placement was rejected because it would duplicate terms and campaign state.
- Random or user-controlled child-list ordering was rejected for MVP because it would weaken campaign control and testability.

**Consequences And Handoffs**

`DOC-06B` owns route-level rendering and navigation. `DOC-13` owns offer identity, collection membership, eligibility, and promotion rules. `DOC-18` must later define canonical data structures and events, and `DOC-22` must define admin placement, ordering, and override controls.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Equal-priority ordering fallback.
- PayPlus Offer and Partner Offer label taxonomy.
- Future personalization inclusion and ordering rules.

### `DEC-2026-003` - Card Offer Selection And Checkout Combination

| Field | Record |
| --- | --- |
| Date | `2026-07-20` |
| Status | Accepted |
| Primary owner | `DOC-13`, promotion engine |
| Affected documents | `DOC-05`, `DOC-06B`, `DOC-06D`, `DOC-09`, `DOC-13`, `DOC-18`, `DOC-22`, promotion-engine diagram, traceability matrix |
| Substantive commit | `36458da` |
| Founder approval | Approved in the founder review task on `2026-07-20` |

**Decision**

For each selected payment card or split-payment funding leg, PayPlus automatically applies only the eligible payment-method-sensitive Card Offer with the highest user value and displays the result. The user does not choose among competing Card Offers. A separate eligible checkout coupon, voucher, or discount may also be selected and applied before the payer confirms the final quote.

**Rationale**

Automatic best-value selection reduces checkout complexity and prevents conflicting card-sensitive benefits, while keeping coupons and vouchers separate preserves independently earned or issued value.

**Alternatives Considered**

- Allowing users to select among competing Card Offers was rejected because eligibility is payment-method-sensitive and the system can select the best quantified value consistently.
- Blocking all other promotions when a Card Offer applies was rejected because separate coupons, vouchers, and discounts may have independent entitlement and stacking rules.

**Consequences And Handoffs**

Checkout must evaluate the selected card or payment profile, display the applied Card Offer, allow any separately eligible coupon, voucher, or discount, recalculate the quote, and obtain payer confirmation before authorization. Split payments evaluate the rule per funding leg. `DOC-18` owns future selection and audit data; `DOC-22` owns deterministic priority and override controls.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Final valuation method for non-monetary, equal-value, or non-directly-comparable offers.
- Exact split-card checkout presentation.

### `DEC-2026-004` - Referral Attribution, Qualification, And Reward Claiming

| Field | Record |
| --- | --- |
| Date | `2026-07-21` |
| Status | Accepted |
| Primary owner | `DOC-06B` Referral routes and `DOC-13` referral/entitlement logic |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06D`, `DOC-08`, `DOC-13`, `DOC-15`, `DOC-18`, `DOC-22`, app route map, status matrix, open-questions register, traceability matrix |
| Substantive commit | `898d994` |
| Founder approval | REF-01 to REF-12 and subsequent registration-attribution decisions approved in the founder review task on `2026-07-21` |

**Decision**

PayPlus has one Referral Program. Every existing user may share a reusable user-linked referral code, link, or QR. Sharing does not identify a recipient or create invitation statuses. Referral attribution begins only when an eligible new user completes registration with a valid code. The MVP uses one campaign; future campaigns remain campaign selections inside the Referral route rather than separate route families.

The Referral route family comprises `REFERRAL-ROOT`, `REFERRAL-REWARDS-LIST`, `REFERRAL-ENTITLEMENT-DETAIL`, and `REFERRAL-REWARD-CLAIM`. Campaigns may create separate role-sensitive referrer and referee entitlements. Claim converts an eligible referrer entitlement into one canonical issued reward instrument, which is then managed through `REWARDS-ROOT` and `REWARD-DETAIL`.

**Rationale**

Separating anonymous sharing, registration attribution, qualification, entitlement, claim, and reward use avoids false invitation records and duplicate reward models. It keeps referral progress understandable while preserving one promotion/reward engine and clear privacy, payment, Request, and payer/payee-linking boundaries.

**Alternatives Considered**

- Invitation statuses such as awaiting, accepted, declined, or expired were rejected because PayPlus usually does not know the recipient when a link is externally shared.
- A separate referral reward schema and status family was rejected because referral benefits use the same entitlement and reward-instrument engine as other rewards.
- Separate route families for each campaign were rejected because campaign selection is a view within the one PayPlus Referral Program.

**Consequences And Handoffs**

DOC-06B owns route presentation and registration handoffs. DOC-13 owns campaigns, qualification, entitlements, claims, and reward logic. DOC-08 owns notifications; DOC-15 owns masking and privacy; DOC-18 must define final objects, events, linkage, and auditability; DOC-22 must define admin campaign, qualification, review, and correction controls. Referral attribution does not create a Request, authorize payment, link payer/payee financial records, or grant shared financial visibility.

**Supersedes / Superseded By**

Supersedes earlier partial Referral route wording and any implied referral invitation lifecycle before registration attribution.

**Remaining Open Items**

- Exact MVP campaign rewards, qualification conditions, source events, payment/risk finality, quotas, and limits.
- Final deeplink/QR token contract, attribution idempotency and correction controls, notification copy, and admin implementation.
- Final multi-campaign visual design and technical data/status/event schemas.
