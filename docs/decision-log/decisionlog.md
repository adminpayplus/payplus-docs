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
| `DEC-2026-004` | `2026-07-21` | Referral Attribution, Qualification, And Reward Claiming | Accepted | `DOC-06B` / `DOC-13` | `898d994` |
| `DEC-2026-005` | `2026-07-21` | Referral Child-Screen And Entitlement Lifecycle | Accepted | `DOC-06B` / `DOC-13` | `9306498` |
| `DEC-2026-006` | `2026-07-21` | My Rewards Route And Canonical Reward Instrument Lifecycle | Accepted | `DOC-06B` / `DOC-13` | `298ab49` |
| `DEC-2026-007` | `2026-07-22` | Me Account-Control Route And Child-Destination Boundaries | Accepted | `DOC-06B` | `0586a37` |
| `DEC-2026-008` | `2026-07-22` | Canonical YAML With Human-Readable Document Control Mirror | Accepted | `DOC-00` | `53bfc19` |
| `DEC-2026-009` | `2026-07-22` | Me Account Information, Security, And Privacy Child Routes | Accepted | `DOC-06B` | `b5879e1` |
| `DEC-2026-010` | `2026-07-26` | Multiple Private Receiving Info Profiles And Destination Snapshots | Accepted | `DOC-06B` / `DOC-10` | `88c7c33` |
| `DEC-2026-011` | `2026-07-26` | Canonical Request Lifecycle And State-Domain Separation | Accepted | `DOC-06A` | `88c7c33` |
| `DEC-2026-012` | `2026-07-26` | Sensitive Reveal And Material-Change Authentication Boundary | Accepted | `DOC-15` | `88c7c33` |
| `DEC-2026-013` | `2026-07-26` | Change Impact And Prototype Lifecycle Governance | Accepted | `DOC-00` | `88c7c33` |
| `DEC-2026-014` | `2026-07-26` | Personal Archive Projection And Controlled Obligation Restore | Accepted | `DOC-06B` / `DOC-06C` | `9dc8015` |
| `DEC-2026-015` | `2026-07-26` | Hierarchical Route-Diagram Governance | Accepted | `DOC-00` | `9dc8015` |
| `DEC-2026-016` | `2026-07-27` | Pay+ Action Sheet And Request-Direction Boundary | Accepted | `DOC-06B` | `cd75183` |
| `DEC-2026-017` | `2026-07-27` | More Shortcut Management And Route Boundary | Accepted | `DOC-06B` | `4aa7d02` |

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

### `DEC-2026-005` - Referral Child-Screen And Entitlement Lifecycle

| Field | Record |
| --- | --- |
| Date | `2026-07-21` |
| Status | Accepted |
| Primary owner | `DOC-06B` Referral child screens and `DOC-13` referral entitlement logic |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-08`, `DOC-13`, `DOC-15`, `DOC-18`, `DOC-22`, app route map, status matrix, open-questions register, traceability matrix |
| Substantive commit | `9306498` |
| Founder approval | RCS-01 to RCS-13 and the exceptional administrator-held behavior approved on `2026-07-21` |

**Decision**

`REFERRAL-REWARDS-LIST` presents the current user's corresponding referrer and referee entitlements through route-local `Available to Claim` and `History` tabs. `REFERRAL-REWARD-CARD` is a list component and entry point to `REFERRAL-ENTITLEMENT-DETAIL`, not a route. Reward cards and child screens do not display referrer/referee identity; masked referee phone remains restricted to attributed-referee progress in `REFERRAL-ROOT`.

Manual claim remains detail-first through `REFERRAL-REWARD-CLAIM`. A successful claim offers `View Reward` to canonical `REWARD-DETAIL` or `Done` to the Referral Rewards History view. One entitlement creates at most one canonical reward instrument. Quota/value is reserved and applicable campaign, benefit, dates, and terms are snapshotted when the entitlement is created. Campaign end, claim deadline, and reward usage expiry remain separate.

Normal Referral reward presentation is `Available to Claim`, `Issued`, `Expired`, or `Reversed`. `Processing` remains transient/internal. `Under Review` appears only as an exceptional inactive History presentation where an authorized administrator holds an already-claimed entitlement or issued reward.

**Rationale**

The two-tab child-screen model separates immediately actionable rewards from claim history without creating extra routes. Role-sensitive beneficiary visibility supports both sides of a referral campaign while one canonical reward instrument prevents duplicate records. Entitlement-time reservation, snapshots, and idempotent issuance protect earned rewards from later campaign edits, quota races, or repeated submissions.

**Alternatives Considered**

- A referrer-only Referral Rewards list was rejected because referee offers may create corresponding entitlements for the referee.
- Separate tabs or routes for `Under Review` and `Processing` were rejected because they are exceptional or transient states, not primary user tasks.
- Claim directly from the list card was rejected because the user should review the full benefit and conditions before the material action.
- Tracking actual reward use in Referral History was rejected because issued-reward use belongs to `REWARDS-ROOT` and `REWARD-DETAIL`.

**Consequences And Handoffs**

DOC-06B owns list, card, detail, claim, and return behavior. DOC-13 owns entitlement creation, reservation, snapshot, claimability, issuance, expiry, reversal, and campaign lifecycle meaning. DOC-08 owns notifications; DOC-15 owns masking; DOC-18 must define canonical objects, states, events, idempotency, recovery, and audit linkage; DOC-22 must define authorized hold/release/reversal controls and operational reconciliation.

**Supersedes / Superseded By**

Supersedes only the referrer-only child-screen and claim wording in `DEC-2026-004`; the Referral Program, sharing, registration attribution, qualification, campaign, privacy, and canonical reward-engine decisions in that record remain effective.

**Remaining Open Items**

- Exact campaign rewards, qualification conditions, source events, payment/risk finality, values, quotas, and limits.
- Final deeplink/QR contract, attribution correction controls, notification copy, future multi-campaign visual behavior, and admin implementation.
- Final DOC-18 objects, canonical statuses/events, recovery contracts, and audit schema.

### `DEC-2026-006` - My Rewards Route And Canonical Reward Instrument Lifecycle

| Field | Record |
| --- | --- |
| Date | `2026-07-21` |
| Status | Accepted |
| Primary owner | `DOC-06B` Rewards routes and `DOC-13` reward-instrument logic |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-09`, `DOC-11`, `DOC-13`, `DOC-15`, `DOC-18`, `DOC-22`, app route map, status matrix, open-questions register, traceability matrix |
| Substantive commit | `298ab49` |
| Founder approval | RWD-01 to RWD-16 approved on `2026-07-21`; hold-versus-expiry treatment deferred |

**Decision**

`REWARDS-ROOT`, labelled `My Rewards`, manages canonical issued reward instruments through route-local Active and History views. Active contains non-terminal `Available`, `Action Required`, `In Progress`, and `Under Review` instruments. History contains terminal `Used`, `Credited`, `Expired`, and `Reversed` instruments. Search, instrument filters, ordering, cards, route states, and origin-preserving return behavior are defined without creating extra routes.

`REWARD-DETAIL` is the full reward-information and terms surface. Checkout rewards normally show availability and conditions without a direct-use action because DOC-09 checkout is the canonical selection point after payment-card/profile choice. External instruments may use configured QR, code, copy, or partner actions; miles show fulfilment progress. Viewing, revealing, copying, or opening a partner destination does not confirm use. One authoritative, idempotent redemption or fulfilment result governs lifecycle status and uncertain outcomes block unsafe repeated use.

MVP reward instruments are single-use by default and do not create a monetary partial-use balance. External vouchers and miles are launch-supported reward types, subject to partner-specific integration and operational readiness. Reward records separately preserve instrument type, earning source, participant role where applicable, program context, campaign/offer/entitlement source, and fulfilment method. Referral role is not an instrument type; issued referral rewards use the same canonical instrument and status model as other rewards.

**Rationale**

One canonical issued-reward route and lifecycle prevents duplicate schemas, conflicting statuses, checkout miscalculation, false redemption, and wallet-like presentation. Separating instrument, source, role, program, campaign, entitlement, and fulfilment dimensions preserves referral and partner context without overloading a generic reward type. Keeping checkout selection in DOC-09 maintains payer review and authorization as the payment control point.

**Alternatives Considered**

- Separate Active, Used, and Expired root views were replaced by Active and History because terminal outcomes belong together and status filters remain available.
- A default direct-use action from Reward Detail was rejected because checkout reward selection should follow obligation and payment-method selection.
- A separate referral reward schema/status family was rejected because referral describes earning source and participant role, not a different issued-instrument model.
- Monetary partial use was rejected for MVP because it would introduce balance-like behavior and substantially more accounting, reconciliation, and expiry complexity.
- Treating external vouchers and miles as future-only was rejected; capability is launch-supported while each partner method remains activation-gated.

**Consequences And Handoffs**

DOC-06B owns route presentation and navigation. DOC-09 owns checkout selection, recalculation, and authorization review. DOC-13 owns eligibility, lifecycle, dimensions, use, fulfilment, reversal, and restoration meaning. DOC-07/08 own disclosure and communication; DOC-11 owns refund/chargeback handoff; DOC-15 owns privacy and credential boundaries; DOC-18 must define final schema/events; DOC-22 must define operational controls. The status-display matrix is the user-facing alignment reference.

**Supersedes / Superseded By**

Supersedes the earlier three-view Rewards baseline, working-label wording, unresolved external-reward launch-scope wording, and any implication that viewing/revealing a reward confirms use or that Reward Detail independently owns checkout.

**Remaining Open Items**

- Whether a reward hold pauses, extends, permits, or reverses expiry.
- Final external-voucher and miles partners, credential contracts, fulfilment methods, reconciliation, and activation readiness.
- Final DOC-18 schema, idempotency keys, canonical event/reason model, credential references, and unknown-result recovery.
- Final My Rewards visual styling/icon and any future fixed-count usage extension.

### `DEC-2026-007` - Me Account-Control Route And Child-Destination Boundaries

| Field | Record |
| --- | --- |
| Date | `2026-07-22` |
| Status | Accepted |
| Primary owner | `DOC-06B`, Me route |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06C`, `DOC-06D`, `DOC-08`, `DOC-10`, `DOC-12`, `DOC-15`, `DOC-18`, `DOC-22`, app route map, open-questions register, traceability matrix |
| Substantive commit | `0586a37` |
| Founder approval | Approved on `2026-07-22` |

**Decision**

`ME-ROOT` is the permanent mixed-role account and user-control destination opened by the bottom-navigation Me button. It uses a fixed, vertically grouped list and does not use payer/payee tabs, a role switch, a duplicate dashboard shortcut grid, or user-reorderable sections. Its confirmed order covers Header, compact Action Required, Account Information, Security & Privacy, Bills & Tenancies, Payments & Records, Rewards & Programs, Referral Program, Preferences & Settings, Help & Support, About PayPlus, and bottom Log Out.

Account information is masked by default. Revealing sensitive information through a Me child route requires the existing PayPlus payment passcode for MVP, with additional step-up where required. `ACCOUNT-PROFILE`, `ACCOUNT-SECURITY`, and `PRIVACY-DATA-CONTROLS` remain separate destinations with distinct purposes.

`ACTIVITY-ROOT` remains the single account-level payer/payee financial activity route. `RECEIVING-DETAILS` manages the approved payout destination used when the user acts as payee and is not another activity route. `ARCHIVED-EVIDENCE-LIST`, labelled Archived Documents, contains archived or previous evidence only and is not a general archive. More remains separate and governs dashboard shortcut management, reorder, restore-default, overflow, and secondary services.

**Rationale**

A permanent mixed-role account route preserves discoverability for users who may act as payer, payee, or both without forcing a role switch. Reusing established feature routes avoids duplicate functionality and ownership. Separating Activity from receiving configuration, and archived evidence from general records, keeps each route understandable and implementable. Keeping More separate prevents shortcut customization from being confused with account controls.

**Alternatives Considered**

- Payer/payee tabs or a role switch in Me were rejected because one account may perform both roles and the account controls are shared.
- Hiding Me or core controls through ordinary admin placement was rejected because account, security, privacy, support, legal, and logout access must remain discoverable.
- A separate receiving-activity route was rejected because `ACTIVITY-ROOT` already covers payer and payee financial activity.
- A general Archived Records route was rejected because archived bills, requests, instructions, and activities remain with their owning routes.
- Combining More with Me was rejected because shortcut arrangement and overflow are distinct from account information, records, settings, and preferences.

**Consequences And Handoffs**

DOC-06B owns route presentation, destination relationships, entry and return behavior. DOC-06C/DOC-12 own evidence behavior; DOC-08 owns notification settings and delivery; DOC-10 owns payout-destination rules; DOC-15/DOC-19 own masking, passcode, step-up, and privacy/security controls; DOC-18 must define final objects and events; DOC-22 must define admin and operations controls. Established Bills, Payment Profile, Activity, Receipts, Rewards, and Referral destinations retain their existing owners.

**Supersedes / Superseded By**

Supersedes the prior undefined Me route baseline and shorthand Me/account entry labels. It does not supersede the established destination behavior owned by other documents.

**Remaining Open Items**

- Exact child-screen fields, layouts, and visual design.
- Final identity-verification display labels and technical status mapping.
- Final receiving-destination workflow and Archived Documents list/detail behavior.
- Final language/theme options, Support/About/Terms content, Membership destination, and More shortcut-management UI.

### `DEC-2026-008` - Canonical YAML With Human-Readable Document Control Mirror

| Field | Record |
| --- | --- |
| Date | `2026-07-22` |
| Status | Accepted |
| Primary owner | `DOC-00` documentation governance |
| Affected documents | `AGENTS.md`, documentation change-integration workflow, all 23 active YAML-backed documents, DOC-22 title, and DOC-00 repository tree |
| Substantive commit | `53bfc19` |
| Founder approval | Approved on `2026-07-22` |

**Decision**

YAML front matter remains the canonical metadata source for AI agents, validation, indexing, and later specification generation. Every active document that uses YAML must also present the same values in a human-readable `Document Control` table immediately below its H1 title. The YAML and table must be updated and verified together whenever metadata changes.

Empty placeholders are exempt until substantive drafting begins. Backup files are excluded from mechanical presentation updates. A document without established YAML metadata must not receive invented metadata solely to create a table.

**Rationale**

Canonical YAML preserves structured machine readability while the synchronized table gives founders, advisers, and reviewers a clean rendered presentation. Keeping one canonical source and one verified display mirror avoids choosing between AI usability and human readability. Placeholder and backup exclusions prevent speculative metadata and unnecessary historical-file churn.

**Alternatives Considered**

- Replacing YAML with tables was rejected because it would weaken structured metadata processing and later AI-execution generation.
- Keeping YAML only was rejected because raw metadata is visually poor in ordinary document review.
- Adding speculative metadata to every placeholder or partial document was rejected because unknown ownership, version, status, approval, and relationship values must not be invented.

**Consequences And Handoffs**

DOC-00, `AGENTS.md`, and the documentation change-integration workflow now require synchronized metadata presentation. Future edits must treat YAML as canonical and check the corresponding table for drift. Newly drafted formal documents and previously empty placeholders must adopt both representations when their metadata becomes known.

The physical repository structure was confirmed intact. DOC-00 now contains a repaired current ASCII structure illustration, and its lifecycle arrows and the DOC-22 title separator no longer contain corrupted presentation characters.

**Supersedes / Superseded By**

Supersedes the YAML-only presentation convention. It does not change document authority, product requirements, route ownership, or domain behavior.

**Remaining Open Items**

- Define DOC-22 metadata before adding its synchronized control table.
- Apply the standard to each currently empty formal or supporting placeholder when substantive drafting begins.

### `DEC-2026-009` - Me Account Information, Security, And Privacy Child Routes

| Field | Record |
| --- | --- |
| Date | `2026-07-22` |
| Status | Accepted |
| Primary owner | `DOC-06B`, Me account child routes |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-15`, `DOC-18`, `DOC-22`, route map, status matrix, open questions, traceability matrix |
| Substantive commit | `b5879e1` |
| Founder approval | Approved on `2026-07-22` |

**Decision**

`ACCOUNT-PROFILE`, labelled Account Information, displays permitted profile/contact information, the four user-facing identity-verification labels, controlled contact changes, and account closure. Login name is immutable after first setup; PayPlus User ID is copyable. `Pending`, `Failed`, and `Update Required` show `Verify Now`; `Verified` shows no action. `IDENTITY-VERIFICATION` is a reusable controlled flow that returns to its origin and must not create duplicate provider submissions.

`ACCOUNT-SECURITY`, labelled Login & Security, owns login password, Payment Passcode entry, permitted Two-Step Verification and Biometric Unlock toggles, Trusted Devices, and recovery/support entry. `PAYMENT-PASSCODE-SETTINGS` owns passcode change/reset and the optional user preference requiring passcode confirmation for card or payment-profile changes. Optional toggles cannot disable mandatory new-device, risk, contact-change, closure, or provider-required authentication.

`PRIVACY-DATA-CONTROLS`, labelled Privacy & Data, separates optional direct-marketing, personalization, and approved partner-data-use choices from mandatory processing. It owns data access/export, governed correction, retention/deletion requests, and request history using `Submitted`, `In Progress`, `Action Required`, `Completed`, and `Unable to Complete`. Completed exports use protected, time-limited in-app access. Account closure remains an Account Information flow and is not immediate deletion.

**Rationale**

Three distinct routes match user expectations while preserving clean ownership between account information, authentication/security, and privacy rights. Reusable verification and passcode screens avoid duplicate flows. Shared status mappings and protected handoffs keep provider, security, privacy, and operational complexity out of the root UI without losing implementation requirements.

**Alternatives Considered**

- Combining security and privacy into one detail route was rejected because authentication controls and privacy requests have materially different purposes and data handling.
- Placing verification updates only under Privacy & Data was rejected because users expect verification status and immediate action in Account Information.
- Creating separate root routes for identity verification or payment-passcode settings was rejected because both are controlled child flows.
- Showing legal name, ID reference, provider payloads, or internal reasons in Account Information was rejected in favor of status-only presentation.
- Treating account closure as deletion was rejected because operational blockers, cancellation, finalization, and retention duties remain distinct.

**Consequences And Handoffs**

DOC-06B owns route behavior and return context. DOC-08 owns notifiable events and destinations; DOC-15 owns privacy, masking, retention, and protected-change boundaries; the status matrix owns user-facing alignment. DOC-18 must define final objects/events and provider-state projections, DOC-19 must define security implementation, and DOC-22 must define operations and admin controls. No wallet, open P2P, cashout, or payment-authorization behavior is introduced.

**Supersedes / Superseded By**

Supersedes the prior Me baseline in which the three child routes were named but their detailed behavior, identity labels, contact changes, security controls, privacy requests, and closure flow remained pending. It does not supersede established KYC/KYB, payment, payout, evidence, risk, notification, or retention ownership.

**Remaining Open Items**

- Final external-provider/backend mapping into the four identity-verification labels.
- Final DOC-19 recovery factors, retry/lockout rules, session duration, and step-up implementation.
- Detailed account-closure screen design and final operational sequencing.
- Privacy-request service timelines, export format, and final legal/provider wording.
- Remaining Me child routes and final visual design.

### `DEC-2026-010` - Multiple Private Receiving Info Profiles And Destination Snapshots

| Field | Record |
| --- | --- |
| Date | `2026-07-26` |
| Status | Accepted |
| Primary owner | `DOC-06B`, Receiving Info route; `DOC-10`, payout destination |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06C`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-09`, `DOC-10`, `DOC-12`, `DOC-14`, `DOC-15`, `DOC-18`, `DOC-22`, route map, glossary, status matrix, traceability |
| Substantive commit | `88c7c33` |
| Founder approval | Receiving Info proposal, alignment, and final commit scope approved on `2026-07-26` |

**Decision**

`RECEIVING-INFO` is a private payee-side library of multiple reusable, user-linked, versioned receiving profiles. It is optional and is not the sole payout source of truth. Each request, obligation, payment, and payout uses a separate destination snapshot that is not mutated by later source-profile edits or archive.

Profiles support masked list/detail display, optional nickname, add/edit, proof where required, readiness, retained versions, and archive instead of hard deletion. Payers cannot browse a payee's profile library. Payee-created requests require a selected destination before sending. Destination changes after payer acceptance follow the replacement rules in the owning documents; payer-selected changes notify a linked payee without creating a payee approval or payout-delay gate.

**Rationale**

Reusable profiles improve payee efficiency while immutable context snapshots preserve payer authorization, auditability, non-user-payee support, privacy, and payout integrity.

**Alternatives Considered**

- A single approved payout account was rejected because payees may manage multiple destinations.
- Treating the current saved profile as payout truth was rejected because edits or archive could silently redirect an accepted or authorized payment.
- Exposing a payee's library to payers was rejected for privacy and purpose-limitation reasons.

**Consequences And Handoffs**

DOC-06B owns route behavior; DOC-10 owns destination and payout rules; DOC-12/DOC-14 own proof and review; DOC-15 owns masking and access; DOC-18/DOC-22 must define final objects, events, review, configuration, and audit.

**Supersedes / Superseded By**

Supersedes singular `RECEIVING-DETAILS` as the active product model. Historical version and decision records remain unchanged.

**Remaining Open Items**

Final methods, fields, external validation capability, name matching, proof types, review SLA, failure mapping, conditional step-up, and technical/admin design.

### `DEC-2026-011` - Canonical Request Lifecycle And State-Domain Separation

| Field | Record |
| --- | --- |
| Date | `2026-07-26` |
| Status | Accepted |
| Primary owner | `DOC-06A`, request lifecycle |
| Affected documents | `DOC-01` to `DOC-12` where affected, `DOC-18`, `DOC-22`, glossary, open questions, status matrix, route register, traceability |
| Substantive commit | `88c7c33` |
| Founder approval | Canonical request-state model and repository alignment approved on `2026-07-26` |

**Decision**

The request lifecycle is `Draft`, `Pending Evidence Verification`, `Pending Receiver Action`, `Accepted`, `Rejected`, `Expired`, or `Cancelled`. While receiver action is pending, the sender sees `Reviewing` and the receiver sees `Awaiting`.

Submission, delivery, sharing, viewing, reminding, acceptance, rejection, expiry, cancellation, linking, archive, and restoration are events or visibility transitions. Evidence status, obligation readiness, payment/payout status, linked case lifecycle, and archive visibility remain separate state domains. A payer-created evidence-backed obligation may proceed without a request or payee acceptance; a payee-created request requires payer acceptance before separate payment authorization.

**Rationale**

One canonical lifecycle avoids overloaded status fields, contradictory user labels, invalid data models, and accidental treatment of request acceptance as payment authorization.

**Alternatives Considered**

- One combined request/payment status family was rejected because request, evidence, obligation, payment, payout, dispute, and archive records have different lifecycles.
- Treating sent, viewed, reminded, or archived as request states was rejected because they are events or visibility.
- Requiring every payer-created payment to use a request was rejected because payer-created evidence-backed obligations may proceed directly.

**Consequences And Handoffs**

DOC-06A owns lifecycle meaning; DOC-06B owns route display; DOC-12 owns evidence; DOC-06C owns readiness; DOC-09 to DOC-11 own payment, payout, and linked cases; DOC-18/DOC-22 must implement separate objects, projections, events, reason codes, and audit records.

**Supersedes / Superseded By**

Supersedes mixed request states such as `Viewed`, `Approved for Payment`, payment outcomes, dispute status, or archive status appearing in the request lifecycle.

**Remaining Open Items**

Final physical schema, reason codes, event payloads, idempotency, detailed case actions, and operational limits.

### `DEC-2026-012` - Sensitive Reveal And Material-Change Authentication Boundary

| Field | Record |
| --- | --- |
| Date | `2026-07-26` |
| Status | Accepted |
| Primary owner | `DOC-15`, privacy and protected-data handling |
| Affected documents | `DOC-05`, `DOC-06B`, `DOC-06C`, `DOC-06D`, `DOC-07`, `DOC-10`, `DOC-15`, `DOC-18` |
| Substantive commit | `88c7c33` |
| Founder approval | Sensitive reveal and change-authentication rules approved on `2026-07-26` |

**Decision**

Prominent reveal of approved masked sensitive values and material changes to identity, contact, security, credential, or Receiving Info data require payment passcode or approved reauthentication before route-specific OTP, provider, review, or confirmation controls. Ordinary permitted viewing or downloading of evidence, invoices, receipts, statements, and payment proof does not require an additional prompt solely because the document is opened or downloaded.

**Rationale**

Prominent full-value display and material data changes create account-takeover and shoulder-surfing risk. Ordinary controlled document access has different user intent and usability consequences and remains governed by session, role, purpose, masking, and authorization controls.

**Alternatives Considered**

- Requiring passcode for every permitted document view/download was rejected as disproportionate.
- Allowing sensitive material changes with confirmation only was rejected because an unattended or compromised device could alter identity or recovery-critical information.

**Consequences And Handoffs**

DOC-15 owns the human-readable privacy baseline. DOC-19 must define final factors, session, step-up, retry, recovery, and lockout mechanics. DOC-18 must retain audit signals without exposing sensitive values in analytics.

**Supersedes / Superseded By**

Clarifies `DEC-2026-009` by separating prominent sensitive reveal and material changes from ordinary permitted document access.

**Remaining Open Items**

Final DOC-19 implementation, risk-triggered step-up, provider requirements, session freshness, and recovery mechanics.

### `DEC-2026-013` - Change Impact And Prototype Lifecycle Governance

| Field | Record |
| --- | --- |
| Date | `2026-07-26` |
| Status | Accepted |
| Primary owner | `DOC-00`, documentation governance |
| Affected documents | `AGENTS.md`, `DOC-00`, documentation integration workflow, prototype workflow, documentation and diagram indexes, prototype registry, route register |
| Substantive commit | `88c7c33` |
| Founder approval | Workflow improvements and final audited commit scope approved on `2026-07-26` |

**Decision**

Material documentation changes begin with one task-level Change Impact Manifest, proceed owner-first through only materially affected files, synchronize parent/family/register/acceptance references, and end with one integrated validation pass. Prototypes are governed review aids, not sources of truth. Each must declare purpose, source baseline, status, scope, limitations, and validation; only one may be current for the same scope, and superseded artifacts are deleted or clearly archived.

No current prototype is registered at this baseline. Stale JPG exports, simplified user-flow diagrams, and the unvalidated mobile prototype were excluded from the substantive commit.

**Rationale**

The workflow prevents missed alignment without repeatedly scanning the full repository after every small edit. Prototype lifecycle controls prevent obsolete or exploratory artifacts from being mistaken for current product requirements.

**Alternatives Considered**

- Repeated repository-wide checks after each file were rejected as inefficient.
- Committing all visual artifacts because they exist locally was rejected because several predated the accepted source baseline.
- Treating prototypes as implementation authority was rejected because formal source documents own product behavior.

**Consequences And Handoffs**

Future agents must use the impact manifest and integrated review. Route changes update the route register and applicable diagram. Prototype work follows the dedicated workflow and returns material discoveries to the owning documents before becoming aligned.

**Supersedes / Superseded By**

Supersedes ad hoc impact checking and unregistered coexisting prototypes.

**Remaining Open Items**

The next prototype must be corrected, validated, assigned a source commit, and explicitly registered before it becomes a current reference.

### `DEC-2026-014` - Personal Archive Projection And Controlled Obligation Restore

| Field | Record |
| --- | --- |
| Date | `2026-07-26` |
| Status | Accepted |
| Primary owner | `DOC-06B`, archive navigation; `DOC-06C`, Bills/rent archive and restore behavior |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06C`, `DOC-06D`, `DOC-08` to `DOC-12`, `DOC-14`, `DOC-15`, `DOC-18`, `DOC-22`, glossary, traceability registers, route maps |
| Substantive commit | `9dc8015` |
| Founder approval | Archive hierarchy, eligibility, evidence treatment, restoration, and status rules approved on `2026-07-26` |

**Decision**

PayPlus uses `ARCHIVED-ROOT` as the archive hub, with `ARCHIVED-BILLS-LIST` for archived bill, fee, rent, and tenancy obligations and `ARCHIVED-DOCS-LIST` for evidence archived with its parent and superseded evidence versions. Archive is a per-user visibility projection; it does not change the canonical obligation, counterparty visibility, party linkage, completed transaction history, or retained snapshots.

The sole current evidence of an active obligation cannot be archived independently. Replacing accepted evidence preserves the prior version as non-restorable. Archiving an obligation also archives its current evidence in that user's projection. An obligation may be restored only when its archive-time class is restore-eligible and current operational blockers permit restoration. Restore revalidates current evidence, recipient, compliance, and risk conditions and does not reactivate reminders, instructions, schedules, or prior payment authorization.

**Rationale**

Separating archived obligations from archived evidence preserves the distinction between an evidence-backed obligation and the documents that support it. Per-user projection avoids one party's housekeeping action changing another party's records or operational payment truth. Controlled restore prevents archived records from bypassing current evidence, identity, recipient, compliance, risk, payment, payout, refund, or dispute controls.

**Alternatives Considered**

- One combined archive list was rejected because obligations and evidence have different meaning, ownership, and restore behavior.
- Allowing the sole current evidence to be archived alone was rejected because an active obligation would become intentionally evidence-free.
- Treating `Cannot be restored` as a lifecycle status was rejected; restore eligibility is a contextual capability and explanation.
- Automatically archiving expired obligations was rejected; expiry changes status but does not change user visibility.

**Consequences And Handoffs**

`DOC-18` must define the canonical data model, projection records, audit events, version lineage, and blocker evaluation. `DOC-22` must define future admin review and restore-on-behalf controls. Prototype work must represent this route family only after alignment with the approved source documents.

**Supersedes / Superseded By**

Supersedes the singular `ARCHIVED-EVIDENCE-LIST` destination and any implication that archive changes counterparty or canonical operational state.

**Remaining Open Items**

Final visual design, technical schema and event contracts, admin workflow detail, and implementation acceptance tests remain to be completed in their owning layers.

### `DEC-2026-015` - Hierarchical Route-Diagram Governance

| Field | Record |
| --- | --- |
| Date | `2026-07-26` |
| Status | Accepted |
| Primary owner | `DOC-00`, documentation governance |
| Affected documents | `AGENTS.md`, Documentation Change Integration Workflow, diagram index, route register, DOC-06 family, route-family diagrams |
| Substantive commit | `9dc8015` |
| Founder approval | Hierarchical Mermaid approach and preservation of the prior map approved on `2026-07-26` |

**Decision**

PayPlus route diagrams use a hierarchy. The app-level map stops at direct global destinations. Each material route family owns a detailed map. Parent maps stop at child-route or documented handoff boundaries and must not duplicate another family's internal flow. The route register remains the canonical route inventory; Mermaid diagrams are visual navigation aids.

The former all-in-one route map is retained as a dated, superseded, non-authoritative snapshot. Trivial leaf screens do not require separate diagrams unless their behavior becomes materially complex.

**Rationale**

Hierarchical maps keep navigation understandable as the product grows, expose missing child destinations without creating a single unreadable graph, and preserve one canonical route inventory.

**Alternatives Considered**

- Continuing one all-in-one route map was rejected because overlapping route families and repeated handoffs obscured ownership.
- Deleting the prior map was rejected because a dated snapshot is useful for comparison and audit history.
- Creating a separate map for every leaf screen was rejected as unnecessary documentation overhead.

**Consequences And Handoffs**

Future route changes must update the route register and only the affected diagram level. New route-family maps must identify status, owner, scope, handoffs, and source documents. Superseded maps must remain clearly non-authoritative.

**Supersedes / Superseded By**

Supersedes the single-map route documentation model.

**Remaining Open Items**

Future route families may receive detailed maps as their behavior becomes materially defined. Mermaid render automation remains optional until the repository adopts a supported validation toolchain.

### `DEC-2026-016` - Pay+ Action Sheet And Request-Direction Boundary

| Field | Record |
| --- | --- |
| Date | `2026-07-27` |
| Status | Accepted |
| Primary owner | `DOC-06B`, Pay+ action-sheet behavior and route handoffs |
| Affected documents | `DOC-01` to `DOC-09` where materially affected, `DOC-12`, `DOC-18`, `DOC-22`, route diagrams, route register, traceability matrix, open-questions register |
| Substantive commit | `cd75183` |
| Founder approval | Pay+ principles, request directions, alignment scope, and commit approved on `2026-07-27` |

**Decision**

`PAYPLUS-ACTION-SHEET` is a slide-up sheet, not an independent root route. Its five MVP icon-and-label actions use two rows: `Pay a Bill` and `Pay Rent` on the first row; `Add Bill / Rent`, `Continue Payment`, and `Request Payment` on the second.

Pay+ `Request Payment` starts a payee-to-payer payment request through `REQUESTS-NEW`. A payer-to-payee request is a separate optional linking request initiated from an approved bill/rent detail or linking context. Acceptance may create shared visibility or communication but is not payment authorization and is not required for a direct payer-created obligation/payment.

The sheet creates no business object by itself. Each action hands off to its owning route, which revalidates evidence, eligibility, risk, authorization, payment, and payout gates. Exact visual design remains open.

**Rationale**

The five-action arrangement reflects PayPlus's evidence-backed payment purpose while keeping common payment, setup, continuation, and payee-request actions accessible. Separating request directions prevents payer-created direct payments from being incorrectly gated by payee acceptance and prevents the Pay+ payment-request action from being mistaken for optional party linking.

**Alternatives Considered**

- Treating every payer-created payment as a request was rejected because a payer may create and pay an evidence-backed obligation without a linked PayPlus payee.
- Combining payee-to-payer payment requests and payer-to-payee linking requests under one Pay+ action was rejected because their purpose and acceptance consequences differ.
- Finalizing exact visual measurements and motion values now was deferred; only the accepted layout and interaction principles are fixed.

**Consequences And Handoffs**

`DOC-06C` owns Bills/rent selection and setup, `DOC-09` owns checkout and payment instructions, and `DOC-06B` owns request-route and Pay+ handoffs. `DOC-18` must define privacy-safe action-sheet events, while `DOC-22` must define controlled availability and audit behavior without changing action semantics or bypassing destination gates.

**Supersedes / Superseded By**

Supersedes active wording that treats a direct payer-created obligation/payment as a payer-created payment request. Historical revision records remain unchanged.

**Remaining Open Items**

Exact iconography, dimensions, spacing, blur strength, animation duration/easing, final styling, future added-button layout, technical event payloads, and final admin UI/permission design remain open.

### `DEC-2026-017` - More Shortcut Management And Route Boundary

| Field | Record |
| --- | --- |
| Date | `2026-07-27` |
| Status | Accepted |
| Primary owner | `DOC-06B`, More route behavior and shortcut-management UX |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06D`, `DOC-15`, `DOC-18`, `DOC-22`, route diagrams, route register, traceability matrix, open-questions register |
| Substantive commit | `4aa7d02` |
| Founder approval | More behavior, shortcut rules, route boundary, compact diagram, alignment scope, and commit approved on `2026-07-27` |

**Decision**

`MORE-ROOT` is one route with Normal and Manage Shortcuts modes; the modes and their screen sections are not child routes. Home supports a default and maximum of 8 shortcuts: up to 7 user-configurable entries plus protected `More`, which remains visible as the final shortcut. Users may keep fewer configurable entries, reorder or remove eligible shortcuts, add approved entries, save account-level preferences, and restore the current eligible admin default.

Normal mode contains dynamic `Home Shortcuts` and `Other Shortcuts & Services` sections. Entries may move between those sections as Home placement changes. Tapping an entry hands off to its independently owned destination; More does not own destination behavior, replace `ME-ROOT`, or change route permissions or business rules.

**Rationale**

One route with two internal modes keeps shortcut discovery and management understandable without creating artificial child routes. Protected More access ensures users can recover and manage shortcuts even when they keep fewer than 7 configurable entries. Dynamic sections avoid treating Home placement as a permanent product category.

**Alternatives Considered**

- Treating Normal mode, Manage mode, shortcut sections, save, restore, and prompts as separate route nodes was rejected because those items are internal UI states or actions.
- Allowing `More` to be removed or displaced was rejected because it would remove the user's recovery and shortcut-management entry.
- Treating secondary destinations as features owned by More was rejected because each destination retains its established owner and controls.

**Consequences And Handoffs**

`DOC-15` owns shortcut-preference privacy treatment, `DOC-18` owns future data objects and privacy-safe events, and `DOC-22` owns the approved catalog, current default, availability rules, configuration versioning, and admin audit controls. The compact Mermaid presents only the route boundary, two internal modes, and generic destination handoff; detailed UI behavior remains in DOC-06B.

**Supersedes / Superseded By**

Supersedes active wording that described More detail as pending and any diagram treatment that elevated internal More actions or sections into routes.

**Remaining Open Items**

Final visual styling, exact motion and interaction design, and optional post-replacement Undo behavior remain open. Final DOC-18 implementation structures and DOC-22 admin UI and permission details remain deferred to their owning technical layers.

### `DEC-2026-018` - Notification Route Family And Signal Separation

| Field | Record |
| --- | --- |
| Date | `2026-07-27` |
| Status | Accepted |
| Primary owners | `DOC-06B` route behavior and `DOC-08` notification content, delivery, and preference rules |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-08`, `DOC-15`, `DOC-18`, `DOC-22`, glossary, route diagrams, route register, status-display matrix, requirements traceability matrix, open-questions register |
| Substantive commit | `846c13d` |
| Founder approval | Notification route hierarchy, screen behavior, signal boundaries, identifier model, alignment scope, and commit approved on `2026-07-27` |

**Decision**

`NOTIFICATION-ROOT` is the parent route for `NOTIFICATION-INBOX`, `NOTIFICATION-DETAIL`, and `NOTIFICATION-SETTINGS`. Generic entry defaults to Inbox; the Home Inbox icon opens Inbox and Me Notification Settings opens Settings. Inbox and Settings cross-link without repeated route-stack loops and preserve a safe source-aware return. `NOTIFICATION-LIST` and `NOTIFICATION-CARD` are screen components, while Archived is an Inbox filter rather than a route.

Every notification card opens Detail before a material action. Detail displays permitted content and mapped context, then revalidates current domain state, user permission, route target, and action availability before handing off to the owning product destination. Read, unread, archive, restore, and Mark All Read change only the recipient-specific Inbox presentation and must not resolve Action Required or mutate the source domain.

Notification category (`System`, `Service`, `Transaction`, or `Promotion`), recipient presentation (`Unread`, `Read`, or `Archived`), owning-domain status, owning-domain Action Required, and per-channel delivery status are separate concepts. Each recipient message requires a unique message identifier and must remain traceable to its event, optional batch, source event/object, recipient and role, template version, registered route target, correlation/causation/deduplication references, timestamps, and channel-delivery attempts.

**Rationale**

A parent route with three child screens gives Inbox and Settings reciprocal access without placing notification ownership under Home or Me. Separating presentation, domain, and delivery states prevents reading or archiving a message from changing payment, request, evidence, payout, reward, privacy, support, or other business state. Recipient-level identifiers and source lineage support auditability, operations, delivery troubleshooting, and later implementation without exposing internal technical states to users.

**Alternatives Considered**

- Treating Archived as a separate route was rejected because it renders the same Inbox records under different selection criteria.
- Treating notification list and card as routes was rejected because they are components of Inbox.
- Executing material domain actions directly from a card was rejected because current state and permission must be revalidated in Detail.
- Storing category, read/archive, Action Required, domain status, and delivery outcome in one status field was rejected because they have different owners and lifecycles.
- Making Me the owner of Notification Settings was rejected; Me is a direct entry point while the screen remains a child of `NOTIFICATION-ROOT`.

**Consequences And Handoffs**

`DOC-06B` owns route-level behavior, entry, return, filters, and screen interaction. `DOC-08` owns event/message eligibility, category, channel, template, preference, retention, and delivery rules. `DOC-15` governs personal-data treatment and the underlying marketing, personalization, and partner-data-use choices. `DOC-18` must define the physical notification/event/message/batch/delivery-attempt model and mappings. `DOC-22` must define controlled templates, manual or campaign sends, provider operations, lookup, permissions, configuration, and audit controls.

**Supersedes / Superseded By**

Supersedes active wording that described Notification Inbox or detailed notification IA as pending, placed Notification Settings under Me ownership, or did not separate Inbox presentation from owning-domain status and delivery state.

**Remaining Open Items**

Final visual styling, search matching, archive retention and disposition, provider capabilities, templates, legally validated service classifications, quiet hours, retry/fallback thresholds, physical schema, and detailed admin workflow remain open under their identified owners.

### `DEC-2026-019` - Authentication And Account-Access Model

| Field | Record |
| --- | --- |
| Date | `2026-07-27` |
| Status | Accepted |
| Primary owners | `DOC-15` account/privacy rules and `DOC-06B` route behavior |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-15`, `DOC-18`, `DOC-22`, glossary, route register, requirements traceability matrix, open-questions register |
| Substantive commit | `3d8d9ec` |
| Founder approval | Authentication/account-access model, alignment scope, and commit approved on `2026-07-27` |

**Decision**

One PayPlus account has one unique verified primary email and may use explicitly enabled email/password, Google, and Apple login methods. External provider identities are linked by stable provider identifier; matching email alone never creates, links, merges, or transfers an account. A provider identity belongs to one PayPlus account.

Google/Apple registration may create a restricted account without an initial PayPlus password. The user may later select `Set Password` in `ACCOUNT-SECURITY`; after setup, the action becomes `Change Password`. Linking or unlinking Google/Apple requires an authenticated session, fresh approved reauthentication, successful provider authentication where applicable, explicit confirmation, audit, and security notification. The final usable login method cannot be removed.

A restricted account requires a unique verified primary email, at least one usable login method, and acceptance of Terms and Privacy notices. It may enter `HOME-ROOT` before phone verification, identity verification, and payment-passcode setup. Those controls remain mandatory before payment or another financially restricted action.

**Rationale**

This model reduces initial registration friction while preserving one-account identity, explicit ownership of external login methods, and strong payment activation controls. It avoids unsafe email-based account merging and allows users to add convenient login methods later without creating duplicate PayPlus accounts.

**Alternatives Considered**

- Requiring password, phone, identity verification, and payment passcode before any dashboard access was rejected because it creates unnecessary registration abandonment before a financial action.
- Treating matching provider and PayPlus emails as permission to auto-link accounts was rejected because email equality is not proof of intended account linkage.
- Requiring every social-authenticated user to set a password during registration was rejected because the provider login is already a usable authentication method.
- Allowing removal of the final login method was rejected because it could leave the account inaccessible.

**Consequences And Handoffs**

`DOC-06B` owns the route-level account-access and Account Security behavior. `DOC-15` owns unique-email, account-linking, data classification, privacy, and material-change requirements. `DOC-07` owns user-facing explanation, `DOC-08` owns security notifications, `DOC-18` must define the future objects and events, `DOC-19` must define security implementation, and `DOC-22` must define authorized support/admin handling.

**Supersedes / Superseded By**

Supersedes active wording that required a PayPlus password and SMS phone verification during initial registration for every account, treated phone/login name as general login methods, or left provider linking to email equality.

**Remaining Open Items**

Detailed `AUTH-ENTRY`, `AUTH-LOGIN`, and `AUTH-REGISTRATION` UI and failure behavior; provider-specific conflicts; recovery; retry and lockout; session/device and 2FA mechanics; protected-deeplink and post-authentication return behavior; and final technical/admin implementation remain open under their identified owners.
