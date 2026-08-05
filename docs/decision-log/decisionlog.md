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
| `DEC-2026-018` | `2026-07-27` | Notification Route Family And Signal Separation | Accepted | `DOC-06B` / `DOC-08` | `846c13d` |
| `DEC-2026-019` | `2026-07-27` | Authentication And Account-Access Model | Accepted | `DOC-15` / `DOC-06B` | `3d8d9ec` |
| `DEC-2026-020` | `2026-07-28` | Entrance, Authentication, Registration, And Account Activation | Accepted | `DOC-06B` / `DOC-07` | `6f2bd4b` |
| `DEC-2026-021` | `2026-07-28` | Authentication And Account-Control Route Hierarchy | Accepted | `DOC-06B` | `27583d7` |
| `DEC-2026-022` | `2026-07-28` | Identity Verification Passcode Boundary And Child-Route Readiness | Accepted | `DOC-06B` / `DOC-15` | `4f781c7` |
| `DEC-2026-023` | `2026-07-28` | Verification, Passcode, And Additional Step-Up Baseline | Accepted | `DOC-06B` | `b120c6e` |
| `DEC-2026-024` | `2026-07-28` | Optional Decision-Complete Behavior Pattern | Accepted | Parallel-agent drafting workflow | `d2a9bfd` |
| `DEC-2026-025` | `2026-07-29` | Capability-Aware Outcome And Resolution Framework | Accepted | Platform design principles / `DOC-07` workflow | `4255f63` |
| `DEC-2026-026` | `2026-07-29` | Authentication Recovery And Safe Return Model | Accepted | `DOC-06B` | `4255f63` |
| `DEC-2026-031` | `2026-08-01` | DOC-09 Payment Domain Architecture Baseline | Accepted | `DOC-09` | `0586c84d1038ba597470355d72414b70fbeff458` |
| `DEC-2026-032` | `2026-07-28` | Outcome Framework And DOC-07 Specialist Authoring Method | Accepted | Outcome Framework / `DOC-07` | `b3241adfd5b54a28039a365b354fe4715f36820b` |
| `DEC-2026-033` | `2026-08-02` | Immediate Workflow Stabilisation Controls | Accepted | Documentation Development Workflow | `a8b0c1963f71abb53cf4a7d6453f86b58555456c` |
| `DEC-2026-034` | `2026-08-02` | PayPlus Documentation Management Roadmap | Accepted | `DOC-00` | `b0f072c1d3fd60d84c51dbdc747537fe9341a1b1` |
| `DEC-2026-035` | `2026-08-03` | Adaptive Payment Checkout Workspace UI/UX | Accepted | `DOC-06B` | `afb4bb02b8de6e7ed63e973127a23b09435c2871` |
| `DEC-2026-036` | `2026-08-04` | Instruction Pay Now Resolver And Notification Detail Entry | Accepted | `DOC-09` / `DOC-08` / `DOC-06B` | `d0d35da995da1347844d11366387fbbf95774bd4` |
| `DEC-2026-037` | `2026-08-05` | DOC-07 Logical Communication Contracts And Bounded Domain Slices | Accepted | `DOC-07` | `eec4295bdde299d18d17bcaa6bab20a60786aa1f` |
| `DEC-2026-038` | `2026-08-05` | PAYMENT-CHECKOUT Defined Baseline | Accepted | `DOC-06B` | `d1e9f550e0f49e861132a96a5e48d8cdcc0882ed` |

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

### `DEC-2026-020` - Entrance, Authentication, Registration, And Account Activation

| Field | Record |
| --- | --- |
| Date | `2026-07-28` |
| Status | Accepted |
| Primary owners | `DOC-06B` route behavior and `DOC-07` authentication outcome/message presentation |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-13`, `DOC-15`, `DOC-18`, `DOC-22`, glossary, route register, requirements traceability matrix, open-questions register, route diagrams |
| Substantive commit | `6f2bd4b` |
| Founder approval | Authentication-route proposal, outcome-message mechanism, alignment scope, commit, and push approved on `2026-07-28` |

**Decision**

`ENTRANCE-ROOT` is the sole unauthenticated app root. It provides approved public non-personalized content, language and public Support/Terms access, and Log In / Create Account actions. `ENTRANCE-CAROUSEL` is a component; a selected item may open `ENTRANCE-PROMOTION-DETAIL`.

`AUTH-LOGIN` resolves an eligible remembered account to `AUTH-LOGIN-FAST` and otherwise opens `AUTH-LOGIN-FULL`. Every successful login renews Fast Login eligibility for one month, while approved risk, device, credential, account, or security changes may end it earlier. User-enabled OS biometric authentication may be presented automatically; password remains the fallback. Log In With Another Account requires confirmation, revokes the current-device session and protected local context, and opens Full Login without unlinking account methods.

Registration uses a temporary registration-attempt record before account creation. The attempt grants no account, login, dashboard, referral-attribution, or financial rights and does not reserve proposed identifiers. Final restricted-account creation atomically rechecks uniqueness, verified email, accepted Terms/Privacy, and attempt validity before claiming identifiers. Killing or leaving the app permits an immediate new attempt; an older attempt may remain for up to 30 minutes of inactivity for cleanup and security without blocking the new attempt.

A restricted account may enter `HOME-ROOT`, but full registration requires `ACCOUNT-ACTIVATION` to complete phone verification, identity verification, and six-digit payment-passcode setup. The route is entered from the post-account setup choice, persistent Home setup banner, or a blocked financial action and returns to the originating context after revalidation.

PayPlus must preserve one canonical Authentication Outcome and Message Matrix. It separates a stable internal Outcome Type ID, an approved user-facing Message ID, and one occurrence/event and correlation reference. Multiple internal outcomes may map to one public message. Exact IDs, approved messages, disclosure levels, CTA mappings, and technical mappings remain open and must not be invented.

**Rationale**

The model reduces account-entry friction without treating a temporary attempt as a customer account or weakening payment readiness. Separating Fast and Full Login keeps routine access simple while preserving controlled fallback and revocation. A canonical outcome/message mapping prevents route-specific wording drift, information leakage, and untraceable support failures.

**Alternatives Considered**

- Treating the public entrance as `AUTH-ENTRY` was rejected because the screen also owns public content, language, Support, and Terms access.
- Reserving email, phone, or provider identifiers during a partial attempt was rejected because an incomplete attempt must not block immediate restart or another valid registration.
- Treating every login as one screen was rejected because remembered-account Fast Login and full method selection have materially different behavior.
- Allowing each route to invent authentication errors was rejected because message disclosure, recovery actions, and operational correlation require one governed matrix.
- Completing all phone, identity, and passcode steps before any dashboard access was rejected in favor of restricted-account access plus persistent, enforceable Account Activation.

**Consequences And Handoffs**

`DOC-06B` owns routes, screen behavior, entry, return, and banner placement. `DOC-07` owns Message IDs, approved wording, disclosure, and CTA presentation. `DOC-15` owns account, identifier, privacy, and sensitive-data rules. `DOC-18` must define registration-attempt, account, session, outcome, message, event, and correlation structures. `DOC-19` must define provider, credential, biometric, retry, lockout, device, and session security. `DOC-20` must define test coverage, and `DOC-22` must define permitted support/admin lookup and controls.

**Supersedes / Superseded By**

Supersedes active use of `AUTH-ENTRY`, login-name-based access, financial-activation terminology, resumable identifier-reserving partial registration, and route-local authentication error definitions.

**Remaining Open Items**

Entrance carousel configuration; exact authentication outcome and message catalogue; provider-specific behavior; Recovery, Phone Verification, Identity Verification, and Payment Passcode Settings details; and final security, data, testing, and admin implementation remain open under their identified owners.

### `DEC-2026-021` - Authentication And Account-Control Route Hierarchy

| Field | Record |
| --- | --- |
| Date | `2026-07-28` |
| Status | Accepted |
| Primary owner | `DOC-06B` |
| Affected documents | `DOC-06B`, route register, diagram index, Authentication route map, Account Activation route map, Me route map |
| Substantive commit | `27583d7` |
| Founder approval | Authentication, Account Activation, and Me route-map hierarchy approved on `2026-07-28` |

**Decision**

`ACCOUNT-ACTIVATION` is an orchestration route that invokes only incomplete account-setup requirements. It is not the canonical parent of the reusable account-control routes.

`PHONE-VERIFICATION` and `IDENTITY-VERIFICATION` are canonically under `ACCOUNT-PROFILE`. `PAYMENT-PASSCODE-SETTINGS` is canonically under `ACCOUNT-SECURITY`. Account Activation may invoke those routes contextually; an activation-originated child returns to Account Activation with refreshed completion state, while a child opened from its canonical parent returns to that parent.

The Authentication map stops at the Account Activation handoff. A separate Account Activation map shows its contextual orchestration, and the Me map retains all existing Me branches while adding the three account-control child handoffs.

**Rationale**

One canonical parent per reusable route prevents duplicate ownership and makes later route drafting and AI implementation easier to trace. Separating the diagrams keeps the authentication overview readable without hiding the activation and account-management relationships.

**Alternatives Considered**

- Keeping Phone Verification, Identity Verification, and Payment Passcode Settings under Account Activation was rejected because the same controls must remain manageable later through Account Profile or Account Security.
- Showing the full activation child tree inside the Authentication map was rejected because it duplicated the child hierarchy and made the route map difficult to read.
- Replacing the Me map with an activation-focused map was rejected because the existing Me destinations remain valid and must be preserved.

**Consequences And Handoffs**

The route register records canonical parentage only. Contextual entry points and source-aware returns belong in DOC-06B transition rules and route-family diagrams. Detailed child-screen behavior remains subject to separate founder review.

**Supersedes / Superseded By**

Supersedes route-register and diagram wording that represented Account Activation as an additional parent of Phone Verification, Identity Verification, or Payment Passcode Settings.

**Remaining Open Items**

Detailed screen behavior, failure handling, provider mapping, retry/lockout, recovery, notification, security, data/event, admin, and acceptance requirements for the three reusable child routes remain open.

### `DEC-2026-022` - Identity Verification Passcode Boundary And Child-Route Readiness

| Field | Record |
| --- | --- |
| Date | `2026-07-28` |
| Status | Accepted |
| Primary owners | `DOC-06B` route behavior and `DOC-15` sensitive-change boundary |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-08`, `DOC-15`, `DOC-18`, glossary, status-display matrix, requirements traceability matrix, open-questions register |
| Substantive commit | `4f781c7` |
| Founder approval | First-time identity-verification exception, alignment corrections, and commit approved on `2026-07-28` |

**Decision**

First-time `IDENTITY-VERIFICATION` invoked during `ACCOUNT-ACTIVATION` does not require a pre-existing payment passcode. The user remains in an authenticated restricted-account context and must complete provider-required verification controls.

Later correction, update, or re-verification of an existing identity record requires payment passcode or approved reauthentication before provider submission. The material-sensitive-change rule applies to changes to existing records, not first-time activation.

Identity Verification uses only `Pending`, `Verified`, `Failed`, and `Update Required` as user-facing labels. Internal provider, risk, compliance, or operational suspension must map to `Failed` or `Update Required` according to domain meaning and must not create a fifth label.

`PHONE-VERIFICATION`, `IDENTITY-VERIFICATION`, and `PAYMENT-PASSCODE-SETTINGS` have confirmed route ownership, modes, and return handoffs. Their detailed screen behavior remains pending. Payment Passcode Settings must not be described as fully screen-defined until Set, Change, Reset, validation, failure, and security behavior is approved.

**Rationale**

A user completing first-time identity verification may not yet have created a payment passcode. Requiring that passcode would create a circular activation dependency. Later changes affect an established sensitive identity record and therefore require stronger confirmation. A four-label projection prevents provider and internal states from leaking into inconsistent user-facing terminology.

**Alternatives Considered**

- Requiring payment passcode before every identity-provider submission was rejected because it blocks valid first-time activation before passcode setup.
- Allowing identity correction or re-verification without passcode or approved reauthentication was rejected because it weakens protection for an established sensitive identity record.
- Adding `Suspended` as a user-facing identity label was rejected because the approved four labels already express failed verification or required user correction without exposing internal operational state.
- Treating Payment Passcode Settings as screen-complete was rejected because its detailed UI and security mechanics have not yet been drafted.

**Consequences And Handoffs**

DOC-19 must define OTP, provider, credential, retry, lockout, reset, session, storage, and reauthentication controls without adding a passcode prerequisite to first-time identity verification. DOC-20 must derive positive, negative, interruption, recovery, accessibility, and security acceptance tests. DOC-18 must preserve first-time-versus-later verification context, provider-processing deduplication, the four-label projection, and passcode Set/Change/Reset events without storing secrets in analytics.

**Supersedes / Superseded By**

Narrows `DEC-2026-012` only where its general material identity-change wording could be read to include first-time identity verification. Its rules for prominent sensitive reveal and changes to existing sensitive records remain accepted.

**Remaining Open Items**

Detailed Phone Verification, Identity Verification, and Payment Passcode Settings screen order, fields, actions, provider mapping, retry/lockout behavior, recovery, exact messages, technical security controls, admin operations, and acceptance tests remain open.

### `DEC-2026-023` - Verification, Passcode, And Additional Step-Up Baseline

| Field | Record |
| --- | --- |
| Date | `2026-07-28` |
| Status | Accepted |
| Primary owner | `DOC-06B` |
| Affected documents | `AGENTS.md`, parallel drafting workflow, `DOC-05`, `DOC-06`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-09`, `DOC-14`, `DOC-15`, `DOC-18`, `DOC-22`, route maps, glossary, and traceability registers |
| Substantive commit | `b120c6e` |
| Founder approval | Consolidated authentication-child proposal and cross-document alignment approved on `2026-07-28` |

**Decision**

`PHONE-VERIFICATION` is a reusable `ACCOUNT-PROFILE` child flow and may be invoked contextually by `ACCOUNT-ACTIVATION`. Hong Kong `+852` numbers are the only launch-supported numbers. Initial verification uses SMS OTP without requiring an existing payment passcode. Replacement requires payment passcode or approved reauthentication, registered-email OTP, and new-phone SMS OTP; the old phone remains authoritative until completion.

Identity Verification uses five user-facing states: `Not Verified`, `Processing`, `Verified`, `Failed`, and `Update Required`. Provider return means `Processing`, not successful verification. An authoritative provider result plus PayPlus policy checks determines final status. Duplicate identity is a PayPlus policy failure. A verified user cannot voluntarily re-verify.

An authorized administrator may set identity status to `Not Verified` or `Update Required` but cannot directly set `Verified`. Changing `Verified` to `Not Verified` requires dual approval and full audit evidence.

`PAYMENT-PASSCODE-SETTINGS` is a reusable `ACCOUNT-SECURITY` child flow. Set and Change require two matching six-digit entries. Reset requires fresh login reauthentication through password or a linked provider, OTP to the registered verified phone, two matching new entries, invalidation of sensitive pending authorization state, and mandatory security notification. Email OTP alone is insufficient.

Payment passcode and payer authorization remain mandatory for payment. Additional external or risk step-up uses an admin-configurable HK$3,000-or-above baseline. Risk, PSP/acquirer, card-network, regulatory, or other mandatory controls may require step-up below that amount and cannot be weakened by the threshold.

**Rationale**

The model separates user-facing identity state from provider and admin workflow state, prevents duplicate submissions and unsafe voluntary identity changes, and gives passcode recovery stronger protection than a single email factor. A configurable step-up threshold provides a clear MVP baseline without overriding mandatory partner or risk controls.

**Alternatives Considered**

- Retaining `Pending` for both incomplete capture and provider processing was rejected because it obscures whether submission occurred.
- Allowing voluntary re-verification after `Verified` was rejected because changes to an established verified identity require governed admin handling.
- Allowing email OTP alone for payment-passcode reset was rejected as insufficient for a payment-authorizing secret.
- Treating HK$3,000 as a universal exemption was rejected because partner, network, regulatory, and risk controls may still require step-up.

**Consequences And Handoffs**

DOC-17 must define the selected provider contract and callbacks. DOC-18 must define provider-state, policy-decision, event, correlation, and audit structures. DOC-19 must define OTP values, retry, lockout, passcode storage, recovery, and session controls. DOC-20 must derive implementation tests. DOC-22 must implement the prohibited admin actions, dual approval, threshold configuration, and support-assisted recovery controls. DOC-07 must assign exact authentication Outcome and Message IDs before AI implementation.

**Supersedes / Superseded By**

Supersedes the four-label identity projection, user-initiated later correction/re-verification behavior, and pending child-flow readiness in `DEC-2026-022`. The first-time identity-verification passcode exception and other non-conflicting protections from that decision remain accepted.

**Remaining Open Items**

- OTP length, validity, resend interval, attempts, cooldown, and velocity limits.
- Final identity-provider result and failure-reason mapping.
- Support-assisted passcode-recovery proof and waiting period.
- Exact authentication Outcome IDs, Message IDs, approved copy, actions, and destinations.
- Implementation-level positive, negative, interruption, recovery, security, and accessibility tests.

### `DEC-2026-024` - Optional Decision-Complete Behavior Pattern

| Field | Record |
| --- | --- |
| Date | `2026-07-28` |
| Status | Accepted |
| Primary owner | `docs/00-foundation/payplus-parallel-agent-drafting-workflow.md` |
| Affected documents | Parallel-agent drafting workflow |
| Substantive commit | `d2a9bfd` |
| Founder approval | Optional decision-complete drafting pattern approved on `2026-07-28` |

**Decision**

The parallel-agent workflow includes an optional decision-complete behavior pattern for material routes, screens, states, exceptions, and failure behavior that would become ambiguous if reduced to topic-only bullets.

When useful, the pattern records meaning, user-visible behavior, available actions, destinations, material system effects, preserved boundaries, interruption/failure/return behavior, and document ownership. The Orchestrator decides whether the pattern improves the task.

The pattern is not a mandatory format. Simple policy decisions, narrow wording changes, metadata updates, reference corrections, and other work that remains clear without the structure should use the shortest suitable presentation.

**Rationale**

Human-readable source documents must remain compact while preserving enough behavior for professional and AI review without relying on chat history. Making the pattern optional prevents the workflow from expanding simple changes or mechanically duplicating behavior across documents.

**Alternatives Considered**

- Keeping only topic-level bullets was rejected where material behavior could become ambiguous or incomplete.
- Requiring the full pattern for every task was rejected because many changes do not need screen, action, destination, failure, and return analysis.

**Consequences And Handoffs**

The pattern may be used in Founder Review Packs and canonical drafts where applicable. Existing source-ownership and documentation-layering rules continue to determine where exact technical values, schemas, message copy, security constants, and admin procedures belong.

**Supersedes / Superseded By**

Adds optional detail guidance without superseding the existing compact-but-decision-complete Founder Review Pack requirement.

**Remaining Open Items**

None.

### `DEC-2026-025` - Capability-Aware Outcome And Resolution Framework

| Field | Record |
| --- | --- |
| Date | `2026-07-29` |
| Status | Accepted |
| Primary owner | `docs/00-foundation/payplus-platform-design-principles.md` and `docs/00-foundation/payplus-outcome-message-notification-framework.md` |
| Affected documents | `AGENTS.md`, documentation integration workflow, `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-15`, `DOC-18`, `DOC-22`, documentation index, glossary, route register, requirements matrix, and open-question register |
| Substantive commit | `4255f63` |
| Founder approval | Capability-aware resolution concept and AUTH-family refinement approved on `2026-07-29` |

**Decision**

Material PayPlus flows may use the canonical chain:

`Business Intent And Source Rule -> Decision/Evaluation -> Outcome -> Resolution Strategy -> Message/CTA -> Notification -> Audit Event -> Acceptance Test -> Code And Automated Test`.

The decision layer determines what is true. The resolution layer selects the permitted next handling path. `DOC-07` owns user-facing Outcome, Message, and CTA definitions; `DOC-08` owns notification behavior. Domain owners retain business logic, and future technical documents retain schemas, engines, security constants, and implementation contracts.

Capability-aware resolution must guide a user toward the safest available valid path rather than multiplying error-specific routes. A resolution, mode, state, or message is not automatically a route.

**Rationale**

Separating decisions, resolutions, outcomes, messages, notifications, and audit events prevents UX copy from becoming business logic, reduces duplicate route definitions, and creates a stable bridge from human requirements to later technical and AI-execution specifications.

**Alternatives Considered**

- Treating every failure as a dedicated error page was rejected because it produces fragmented routes and maintenance-heavy behavior.
- Letting each domain define its own message and notification semantics was rejected because it creates inconsistent user communication and weak traceability.
- Applying the framework mechanically to every simple interaction was rejected because it would over-complicate human-readable documents.

**Consequences And Handoffs**

Owning documents must define business intent, decisions, available capabilities, and permitted resolutions. `DOC-07` must assign canonical Outcome and Message records; `DOC-08` must map notifications only where justified; `DOC-18` must map correlation and audit events; `DOC-20` must test decision and resolution paths. Route diagrams remain navigation views and must not represent outcomes or resolutions as destinations unless an independently navigable screen exists.

**Supersedes / Superseded By**

Refines earlier outcome/message guidance without changing accepted domain decisions.

**Remaining Open Items**

- Exact canonical Outcome IDs, Message IDs, approved copy, disclosure levels, actions, and destinations.
- Detailed technical decision-engine and resolution-registry design in the future engineering layer.

### `DEC-2026-026` - Authentication Recovery And Safe Return Model

| Field | Record |
| --- | --- |
| Date | `2026-07-29` |
| Status | Accepted |
| Primary owner | `DOC-06B`, `AUTH-RECOVERY` |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-15`, `DOC-18`, `DOC-22`, Authentication and Account Activation route maps, glossary, route register, requirements matrix, and open-question register |
| Substantive commit | `4255f63` |
| Founder approval | Consolidated AUTH recovery proposal and alignment approved on `2026-07-29` |

**Decision**

`AUTH-RECOVERY` is one reusable route with internal modes and screens for recovery start, email delivery confirmation, reset-link validation, new-password entry, capability-aware resolution, Support-authorized setup, and completion. Password reset uses a single-use expiring deeplink sent to the verified primary email and applies only when a PayPlus password already exists.

A provider-only account must authenticate through its linked provider and may set its first PayPlus password only from authenticated Account Security. Provider recovery remains provider-owned. If ordinary recovery capabilities are unavailable, PayPlus evaluates permitted alternatives and may continue, restart, redirect, wait, escalate to controlled Support recovery, or stop when ownership cannot be established.

Successful password reset terminates active authentication sessions and remembered access context, does not log the user in, and returns to `AUTH-LOGIN-FULL`. PayPlus may preserve only an opaque intended destination; after login, it must revalidate the destination, permissions, and all payment controls. It must never preserve credentials, OTPs, passcodes, authorization results, or a payment-submission state.

**Rationale**

The model supports practical self-service recovery without creating an authentication bypass. Capability-aware resolution gives users the safest remaining path while allowing recovery to stop where identity or account ownership cannot be established.

**Alternatives Considered**

- Email OTP or login password alone for payment-passcode reset was rejected as insufficient for a payment-authorizing secret.
- Creating separate routes for every recovery failure was rejected because they are outcomes and resolution states within one route.
- Automatically logging in or resuming payment after reset was rejected because authentication, payment context, and authorization must be revalidated.

**Consequences And Handoffs**

`DOC-07` must define disclosure-safe recovery outcomes, messages, and CTAs. `DOC-08` distinguishes reset-link delivery from mandatory reset-completion security notification. `DOC-18` must retain attempt, link, correlation, callback, outcome, resolution, and audit records without logging secrets. `DOC-22` must provide a controlled Support recovery case interface and prohibit administrators from viewing secrets, choosing credentials, directly creating sessions, linking providers, or bypassing activation and verification controls.

**Supersedes / Superseded By**

Completes the previously pending `AUTH-RECOVERY` baseline while preserving `DEC-2026-019` through `DEC-2026-023`.

**Remaining Open Items**

- Exact reset-link validity, resend cooldown, retry limits, and security constants in `DOC-19`.
- Exact Support-assisted proof, cooling period, restricted-account treatment, and approval roles in `DOC-19` and `DOC-22`.
- Exact recovery Outcome IDs, Message IDs, approved copy, CTA records, and disclosure rules in `DOC-07`.
- Final provider-specific recovery and failure mapping after provider selection.

### `DEC-2026-027` - Documentation Operating Architecture And Canonical Lifecycle

| Field | Record |
| --- | --- |
| Date | `2026-07-29` |
| Status | Accepted |
| Primary owner | DOC-00 for governance; `AGENTS.md` for operating contract and routing; Documentation Development Workflow for lifecycle |
| Affected documents | `AGENTS.md`, DOC-00, foundation architecture documents, documentation index, DOC-07 live specialist reference, and prototype registry references |
| Substantive commit | `eb6526726f87ba2e38d99f67d69aaa602f806793` |
| Founder approval | Bounded Final Integration authorized on `2026-07-29` |

**Decision**

PayPlus documentation uses one operating architecture:

- DOC-00 is the sole documentation-governance authority and sole owner of the ranked source-of-truth hierarchy.
- `AGENTS.md` is the repository Operating Contract and Routing Layer and does not define a competing hierarchy or Documentation Lifecycle.
- `payplus-documentation-development-workflow.md` is the sole canonical owner of the Documentation Lifecycle and all lifecycle stages, roles, gates, validation authority, Git and records treatment, and completion rules.
- `payplus-parallel-agent-documentation-procedure.md` supplies optional parallel-execution mechanics only.
- `payplus-prototype-design-validation-specialist-guide.md` and `payplus-doc-07-design-specification-specialist-guide.md` supply specialist methods and checks only.
- Platform Design Principles owns durable platform and product design doctrine.
- The Outcome Framework is the detailed owner of the Outcome → Resolution Strategy → Message/CTA → Notification architecture.

The following filename migration is accepted:

- `payplus-document-change-integration-workflow.md` → `payplus-documentation-development-workflow.md`;
- `payplus-parallel-agent-drafting-workflow.md` → `payplus-parallel-agent-documentation-procedure.md`;
- `payplus-prototype-design-validation-workflow.md` → `payplus-prototype-design-validation-specialist-guide.md`;
- `payplus-doc-07-design-specification-workflow.md` → `payplus-doc-07-design-specification-specialist-guide.md`.

**Rationale**

One concept must have one owner and one authoritative definition. Separating governance, routing, lifecycle execution, specialist methods, platform doctrine, and outcome architecture reduces duplicated rules and prevents agents from selecting a competing workflow or authority.

**Alternatives Considered**

- Retaining multiple complete workflows was rejected because lifecycle gates and responsibilities could drift.
- Keeping old filenames after changing document roles was rejected because the names continued to imply competing workflows.
- Repeating DOC-00's ranked hierarchy in `AGENTS.md` was rejected because two ranked copies could diverge.
- Keeping the detailed outcome chain in both Platform Principles and the Outcome Framework was rejected because the framework is the appropriate detailed owner.

**Consequences And Handoffs**

All documentation tasks route through the canonical Documentation Development Workflow. Specialist procedures and guides are loaded only when their triggers apply and must return their outputs to a named lifecycle stage. Current repository navigation and live references use the new filenames. Historical changelog, decision-log, DOC-00 version-history, backup, and superseded wording remains unchanged as time-accurate evidence.

**Supersedes / Superseded By**

Supersedes the former architectural interpretation that Parallel, Prototype, DOC-07, or documentation-change integration could operate as separate lifecycle workflows. It does not rewrite or invalidate historical records created under their former names.

**Remaining Open Items**

None for the approved Final Integration scope.

### `DEC-2026-028` - Documentation System Directory And Architecture Map

| Field | Record |
| --- | --- |
| Date | `2026-07-29` |
| Status | Accepted |
| Primary owner | DOC-00 for governance; Documentation Architecture Map for navigation; Documentation Development Workflow for lifecycle |
| Affected documents | `AGENTS.md`, DOC-00, documentation index, Documentation System artifacts, DOC-07 live specialist reference, Outcome Framework maintenance reference, and prototype registry references |
| Substantive commit | `c7b3f23f35b6f0c32886ae37e45daa86821a4db6` |
| Founder approval | Bounded Documentation System Directory Migration authorized on `2026-07-29` |

**Decision**

Create `docs/documentation-system/` as the repository location for the operating architecture used to create, review, integrate, and maintain PayPlus documentation.

The directory contains:

- a concise directory README;
- `documentation-architecture-map.md` as the canonical navigation artifact for authority, ownership, routing, dependencies, directory rules, and operating-document classification;
- the sole canonical Documentation Development Workflow;
- the optional Parallel-Agent Documentation Procedure;
- the DOC-07 Design Specification Specialist Guide;
- the Prototype Design and Validation Specialist Guide.

The following path migrations are accepted:

- `docs/00-foundation/payplus-documentation-development-workflow.md` → `docs/documentation-system/payplus-documentation-development-workflow.md`;
- `docs/00-foundation/payplus-parallel-agent-documentation-procedure.md` → `docs/documentation-system/payplus-parallel-agent-documentation-procedure.md`;
- `docs/00-foundation/payplus-doc-07-design-specification-specialist-guide.md` → `docs/documentation-system/payplus-doc-07-design-specification-specialist-guide.md`;
- `docs/00-foundation/payplus-prototype-design-validation-specialist-guide.md` → `docs/documentation-system/payplus-prototype-design-validation-specialist-guide.md`.

DOC-00, DOC-01 through DOC-04, Platform Design Principles, and the Outcome Framework remain in `docs/00-foundation/`.

**Rationale**

Operational workflows, execution procedures, and specialist documentation guides are part of the documentation operating system rather than the product, regulatory, commercial, compliance, or subject-framework foundation. Separating them makes repository routing and future extension clearer without changing authority.

The Architecture Map provides one concise navigation owner so `AGENTS.md`, directory indexes, workflows, procedures, and specialist guides can reference the approved structure without reproducing it.

**Authority Confirmation**

- DOC-00 remains the sole documentation-governance authority and ranked source-of-truth owner.
- `AGENTS.md` remains the Operating Contract and Routing Layer only.
- The Documentation Development Workflow remains the sole owner of the complete Documentation Lifecycle and lifecycle gates.
- Platform Design Principles and the Outcome Framework retain their existing subject ownership.
- Parallel remains an optional Procedure; DOC-07 and Prototype remain Specialist Guides.
- The directory migration and Architecture Map do not create or transfer approval, lifecycle, product, or domain authority.

**Consequences And Handoffs**

Current normative references use `docs/documentation-system/`. Future documentation operating workflows, procedures, architecture maps, and specialist documentation guides belong in that directory. New artifacts require explicit concept ownership, classification, non-duplication boundaries, invocation and return rules, and governed updates to the Architecture Map and routing indexes.

Historical changelog, decision-log, DOC-00 version-history, backups, archives, and superseded snapshots retain their time-accurate former paths.

**Supersedes / Superseded By**

Refines the directory placement established by `DEC-2026-027` without changing its authority or lifecycle decisions.

**Remaining Open Items**

None for the approved directory-migration scope.

### `DEC-2026-029` - Work Command Interface And Adaptive Parallel Role Coverage

| Field | Record |
| --- | --- |
| Date | `2026-07-29` |
| Status | Accepted |
| Primary owner | PayPlus Work Command Language for command meaning and routing; Parallel-Agent Documentation Procedure for adaptive parallel-role coverage |
| Affected documents | `AGENTS.md`, documentation indexes, Documentation Architecture Map, Parallel-Agent Documentation Procedure, and PayPlus Work Command Language |
| Substantive commit | `9b5706016e69a062ab1c61962732d5cb0a1c607a` |
| Founder approval | Local documentation change and Commit/Record authorized on `2026-07-29`; Push not authorized |

**Decision**

Create `payplus-work-command-language.md` as a normative command-interface reference so the Founder can use a stable vocabulary to route work into the canonical Documentation Development Workflow.

The core commands are Explore, Proposal, Approve, Draft, Review, Edit, Align, Validate, Integrate, Commit, Record, Push, and Complete. Prototype and Specify are subject qualifiers that must be paired with, or safely interpreted as, a core command. The command reference owns command meaning, minimum inputs, expected outputs, and lifecycle routing only.

Extend the Parallel-Agent Documentation Procedure so the Orchestrator assesses domain expertise, independent review, document ownership, and integration coverage before parallel work. Compatible responsibilities may be combined with disclosed conflict controls. Temporary specialist roles may be assigned for the current task when their scope, inputs, outputs, authority boundary, handoff, and completion condition are defined.

**Authority Confirmation**

- The Documentation Development Workflow remains the sole owner of the Documentation Lifecycle and every lifecycle stage and gate.
- A work command does not independently authorize editing, approval, validation, Commit, Records Commit, Push, or Completion.
- Temporary specialist roles cannot approve Founder decisions, expand approved scope, override canonical owners, or become permanent governance roles.
- Missing specialist capability must be marked `Not performed` or `Unresolved`; full review or validation cannot be claimed.
- A permanent role-model change requires a separate proposal through the canonical workflow and Founder approval.

**Rationale**

A stable command interface reduces repeated prompting while preserving canonical lifecycle ownership. Adaptive role coverage allows the Orchestrator to match specialist capability to task risk without creating a large permanent role catalogue or allowing agents to invent expertise and authority.

**Alternatives Considered**

- Adding the commands directly to the lifecycle workflow was rejected because the vocabulary is an interface and routing concern, not a second lifecycle definition.
- Treating Prototype and Specify as standalone workflows was rejected because their specialist guides operate within the canonical lifecycle.
- Creating permanent specialist roles for every domain was rejected because most specialist needs are task-specific.
- Allowing self-review when no independent reviewer is available was rejected for material work; the review must instead remain explicitly incomplete.

**Consequences And Handoffs**

`AGENTS.md` and the Documentation Architecture Map route named work commands to the Work Command Language and then to the canonical workflow. The Documentation System README and documentation index expose the reference. Parallel work packets must record role coverage and unresolved capability gaps. Existing core roles remain available; no permanent specialist role is created by this decision.

**Supersedes / Superseded By**

Extends `DEC-2026-027` and `DEC-2026-028` without changing their governance, lifecycle, directory, or specialist-document ownership decisions.

**Remaining Open Items**

None for the approved Work Command Language and adaptive-role scope.

### `DEC-2026-030` - Documentation Workflow v2.0 Thinking Mode Separation

| Field | Record |
| --- | --- |
| Date | `2026-07-29` |
| Status | Accepted |
| Primary owner | Documentation Development Workflow |
| Affected documents | `docs/documentation-system/payplus-documentation-development-workflow.md` |
| Substantive commit | `0d5864f142844c557be2309fa00477023f0792ec` |
| Founder approval | Workflow v2.0 accepted as Production Ready and Commit authorized on `2026-07-29`; Push not authorized |

**Decision**

Adopt Documentation Workflow v2.0 as the Production Ready baseline and explicitly separate the reasoning behaviour used across documentation work:

- Explore uses Divergent Thinking to investigate, compare, expose conflicts and risks, and produce a neutral Explore Pack without selecting a solution.
- Proposal uses Convergent Thinking and is the first mode permitted to recommend architecture, terminology, ownership, lifecycle, status, object-model, or documentation changes.
- Draft uses Execution Thinking to convert an approved Proposal or equivalent explicit Founder instruction into documentation without introducing new design decisions.
- Review uses Validation Thinking to identify correctness, quality, completeness, ambiguity, inconsistency, and implementation-fidelity issues without redesigning architecture.
- Align uses Consistency Thinking to synchronize approved terminology, ownership, references, and meaning without creating requirements.
- Integrate uses Integration Thinking to merge and validate approved work across the documentation system without drafting or altering the approved design.

Each Thinking Mode has one canonical Stage Contract defining purpose, inputs, outputs, allowed actions, forbidden actions, and exit criteria. The existing 20 lifecycle stages, Founder Decision, Commit, and Push gates remain authoritative and unchanged in ownership.

Further changes to Workflow v2.0 Thinking Modes, Stage Contracts, lifecycle philosophy, or mode boundaries require evidence from real PayPlus documentation work. A hypothetical preference or speculative improvement alone is not sufficient; the change request must identify an observed task, failure or friction, affected stage, and supporting repository evidence.

**Authority Confirmation**

- The Documentation Development Workflow remains the sole owner of the Documentation Lifecycle and every lifecycle stage and gate.
- Explore cannot make recommendations, Draft cannot introduce new design decisions, and Review, Align, and Integrate cannot redesign approved architecture.
- Proposal recommendations remain subject to the existing Stage 6 Founder Decision gate.
- Commit, Records Commit, Push, and Completion authority remain governed by the existing lifecycle stages and Founder gates.
- The Work Command Language continues to interpret commands and route them into these canonical modes; it does not own or redefine the modes or lifecycle.

**Rationale**

PAYMENT-CHECKOUT exploration demonstrated that exploration output could gradually converge into hidden recommendations or draft content. Separating divergent investigation, convergent decision preparation, and documentation execution makes decision ownership visible, prevents premature architecture, and gives agents a testable behavioural boundary at every stage.

**Alternatives Considered**

- Allowing Explore to recommend a preferred architecture was rejected because it collapses investigation and decision-making into one mode.
- Allowing Proposal content to evolve directly into documentation was rejected because approved decisions must exist before execution begins.
- Creating a second workflow for Thinking Modes was rejected because the Documentation Development Workflow is already the sole lifecycle owner.
- Redesigning existing approval, Commit, Records Commit, Push, or Completion stages was rejected because the evidence concerned reasoning boundaries rather than lifecycle authority.

**Consequences And Handoffs**

Future documentation tasks must apply the Thinking Mode assigned to the current lifecycle stage. Explore produces inputs for a separate Proposal; Proposal stops for explicit Founder approval; Draft implements only the approved meaning; Review, Align, and Integrate return newly discovered material design questions to Proposal. Work Command Language compatibility and specialist invocation remain intact.

Workflow changes after this Production Ready baseline must cite real repository documentation evidence. Routine use should now focus on applying the workflow and collecting observed evidence rather than continuing speculative workflow redesign.

**Supersedes / Superseded By**

Extends `DEC-2026-027`, `DEC-2026-028`, and `DEC-2026-029` without changing their governance, lifecycle ownership, directory, command-interface, or specialist-document decisions.

**Remaining Open Items**

None for the approved Documentation Workflow v2.0 scope.

### `DEC-2026-031` - DOC-09 Payment Domain Architecture Baseline

| Field | Record |
| --- | --- |
| Date | `2026-08-01` |
| Status | Accepted |
| Primary owner | `DOC-09` Payment Domain Architecture |
| Affected documents | `DOC-00`, `DOC-01` to `DOC-15` where directly aligned, `DOC-18`, `DOC-22`, `AGENTS.md`, documentation index, route diagrams, glossary, and traceability registers |
| Mechanical rename commit | `200bc0e26e508723ae5c1fc392385e0c41460ab6` |
| Substantive commit | `0586c84d1038ba597470355d72414b70fbeff458` |
| Founder approval | Candidate Final, rename, alignment, validation, integration, and Commit grouping approved through the DOC-09 workflow ending `2026-08-01` |

**Decision**

Accept `DOC-09 - Payment Domain Architecture` version `1.1.0` as a Founder Working Baseline and canonical replacement for the superseded DOC-09 payment-request, multi-funding-source, and settlement baseline. Rename the canonical file to `doc-09-payment-domain-architecture.md` while preserving Git history and align only direct repository references and owned handoffs.

**Rationale**

The accepted document now owns the Payment Domain architecture and its boundaries more accurately than the former feature-oriented title and baseline. The validated split commits preserve rename traceability and separate the mechanical path change from the accepted substantive content.

**Alternatives Considered**

- Retaining the former filename and title was rejected because they no longer represented the accepted domain ownership.
- Combining rename, substantive content, and records into one commit was rejected in favor of the Founder-approved history-safe split grouping.

**Consequences And Handoffs**

Live documentation references use the new DOC-09 title and path. The accepted architecture replaces the superseded baseline. Direct repository alignment and validation passed, and no new architecture decision was introduced during Align or bounded correction. Downstream Settlement, adjustment, provider integration, machine-state, outcome/message, security, testing, operations, and admin details remain with their named owners.

**Supersedes / Superseded By**

Supersedes the former active DOC-09 baseline titled `Payment Request, Multi-Funding Source & Settlement` without rewriting its historical records.

**Remaining Open Items**

Downstream technical and operational TBCs remain with the owners identified by `DOC-09`; none blocks the Founder Working Baseline.

### `DEC-2026-032` - Outcome Framework And DOC-07 Specialist Authoring Method

| Field | Record |
| --- | --- |
| Date | `2026-07-28` |
| Status | Accepted; retrospectively recorded on `2026-08-01` |
| Primary owner | Outcome Framework for cross-domain result architecture; `DOC-07` for approved user-facing mappings |
| Affected documents | `docs/00-foundation/payplus-outcome-message-notification-framework.md`; original `docs/00-foundation/payplus-doc-07-design-specification-workflow.md`, now governed through the DOC-07 specialist guide under `docs/documentation-system/` |
| Substantive commit | `b3241adfd5b54a28039a365b354fe4715f36820b` |
| Founder approval | Original substantive change delivered on `2026-07-28`; retrospective records closure authorized on `2026-08-01` |

**Decision**

Establish a repository-wide architecture that keeps a business rule, operation Outcome, user-facing Message, CTA, Notification, audit evidence, acceptance coverage, and implementation mapping distinct and traceable. Establish a specialist DOC-07 authoring method for outcome, disclosure, message, and CTA records without transferring ownership from the applicable route, domain, notification, data, security, testing, support, or admin document.

**Rationale**

Stable outcome semantics and explicit ownership boundaries prevent backend logic, persistent statuses, user-facing copy, notifications, and audit evidence from collapsing into one ambiguous implementation concept. A specialist DOC-07 method makes the required mappings reviewable without creating a competing documentation lifecycle.

**Alternatives Considered**

- Embedding user-facing copy directly in backend business logic was rejected because wording and localization must not redefine business outcomes.
- Treating notifications or persistent statuses as operation outcomes was rejected because each has a different owner and lifecycle.
- Allowing the DOC-07 guide to approve product rules or operate as an independent lifecycle was rejected; later documentation-system decisions made this boundary explicit.

**Consequences And Handoffs**

Domain owners supply approved rules and decisions. `DOC-07` owns approved user-facing Outcome, Message, disclosure, and CTA mappings; `DOC-08` owns notification behavior; technical, testing, support, and admin owners retain their respective implementation and evidence responsibilities. `DEC-2026-025` later added the capability-aware Resolution layer. `DEC-2026-027` and `DEC-2026-028` later confirmed the canonical lifecycle and reclassified the DOC-07 material as a specialist guide under the Documentation System.

**Supersedes / Superseded By**

Refined by `DEC-2026-025`, `DEC-2026-027`, and `DEC-2026-028`; this retrospective record does not supersede those later decisions.

**Remaining Open Items**

None for this retrospective records closure.

### `DEC-2026-033` - Immediate Workflow Stabilisation Controls

| Field | Record |
| --- | --- |
| Date | `2026-08-02` |
| Status | Accepted |
| Primary owner | Documentation Development Workflow |
| Affected documents | `docs/documentation-system/payplus-documentation-development-workflow.md`; `docs/documentation-system/payplus-work-command-language.md` |
| Substantive commit | `a8b0c1963f71abb53cf4a7d6453f86b58555456c` |
| Founder approval | Revised Immediate Workflow Stabilisation Proposal, exact implementation scope, branch attachment, and substantive Commit authorized through the execution workflow ending `2026-08-02` |

**Decision**

Adopt six generic Immediate Workflow Stabilisation controls within the existing Documentation Development Workflow and its command interface:

- a bounded Proposal Challenge with one default cycle and a hard maximum of two;
- Proposal Decision Readiness for each material decision;
- one consolidated Founder Decision Pack wherever practical;
- a Draft Plan and Decision Coverage Matrix for material work;
- bounded Primary, Verification, and Final Verification Review convergence;
- canonical result vocabulary that separates Align execution, coordinated Validate passage, and Integrate readiness.

The controls remain internal contracts and structured outputs of existing stages. They do not create a lifecycle stage, Thinking Mode, product-specific workflow, standalone guide, template, knowledge base, automation, or migration process. The existing 20-stage lifecycle remains the canonical baseline.

**Rationale**

The DOC-09 retrospective showed that material decisions, scenario and invariant coverage, cross-document representation, review convergence, and the distinction between Align execution and coordinated validation required stronger controls at their existing lifecycle gates. Integrating bounded generic controls into the canonical workflow addresses those observed failure modes without creating a competing workflow or coupling workflow governance to a product document.

**Alternatives Considered**

- A DOC-06 `PAYMENT-CHECKOUT` Pilot Pack and document-specific workflow guidance were rejected because they would couple the generic workflow to one product family and risk becoming shadow authority.
- A new lifecycle stage or Thinking Mode was rejected because the required controls fit the existing Proposal, Draft, Review, Align, Validate, and Integrate contracts.
- Standalone templates, scripts, automation, observation files, and legacy migration rules were excluded because the immediate scope was limited to evidence-backed generic stabilisation.
- Preserving the earlier controls unchanged was rejected because observed DOC-09 execution and validation findings demonstrated material decision-timing, representation, convergence, and stage-result ambiguity.

**Consequences And Handoffs**

Future material Proposals must include the bounded challenge, Decision Readiness evidence, and consolidated material Founder escalation wherever practical. Material Draft work must use decision coverage before Primary Review. Verification and Final Verification cannot reopen accepted design through unbounded alternative preferences. Align reports `ALIGN_EXECUTED - PENDING_VALIDATE`; Validate owns coordinated passage; Integrate reports commit readiness only after validation passes.

The first evidence-producing use is the separately governed restart and completion of the DOC-06 `PAYMENT-CHECKOUT` route. Observations from that route may inform a later retrospective and Workflow Improvement Round 2 but cannot independently change this accepted workflow.

**Supersedes / Superseded By**

Extends `DEC-2026-030` without changing the existing 20 lifecycle stages, six Thinking Modes, Founder gates, lifecycle ownership, records treatment, or Push authority.

**Remaining Open Items**

The six controls require evidence-based evaluation after the complete `PAYMENT-CHECKOUT` route. Keep, Modify, Remove, Automate, or Still Unproven treatment belongs to the later Workflow Improvement Round 2; Workflow vNext remains separately governed.

### `DEC-2026-034` - PayPlus Documentation Management Roadmap

| Field | Record |
| --- | --- |
| Date | `2026-08-02` |
| Status | Accepted |
| Primary owner | `DOC-00` documentation governance |
| Affected documents | `docs/traceability/payplus-documentation-management-roadmap.md`; `docs/00-foundation/doc-00-documentation-governance.md` |
| Substantive commit | `b0f072c1d3fd60d84c51dbdc747537fe9341a1b1` |
| Founder approval | Roadmap role, boundaries, bounded corrections, DOC-00 alignment, Validate, Integrate, and conditional Commit approved through the management-roadmap workflow ending `2026-08-02` |

**Decision**

Establish the PayPlus Documentation Management Roadmap as a derived programme-level coordination and progress tracker. It may register bounded work, task assignments, canonical lifecycle position, dependencies, returned evidence, queues, and next permitted actions. It must preserve returned canonical results without reinterpretation and must not own product truth, lifecycle stages or gates, approvals, validation authority, Git actions, records treatment, or completion.

The PayPlus Documentation Development Workflow remains the sole lifecycle authority. Manager assignments embed or reference its task contract, and execution tasks return its required outputs unchanged.

**Rationale**

A persistent coordination surface makes multi-task documentation progress, dependencies, evidence, and Founder gates visible without turning task management into a competing workflow or duplicating formal requirements.

**Alternatives Considered**

- Using conversation history alone was rejected because it does not provide a stable repository-level progress and dependency record.
- Creating a separate management lifecycle or manager-owned result vocabulary was rejected because it would compete with the canonical Documentation Development Workflow.

**Consequences And Handoffs**

DOC-00 registers the roadmap as a derived traceability artifact. The roadmap references canonical owners, uses coordination-only work-item IDs and statuses, and cannot independently approve, validate, integrate, commit, push, or establish completion. Product and domain requirements remain in their formal owners.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

None for the accepted roadmap and DOC-00 registration scope.

### `DEC-2026-035` - Adaptive Payment Checkout Workspace UI/UX

| Field | Record |
| --- | --- |
| Date | `2026-08-03` |
| Status | Accepted |
| Primary owner | `DOC-06B` route-level UI/UX; `DOC-09` remains authoritative for Payment Domain architecture and meaning |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06C`, `DOC-06D`, `DOC-13`, diagram index, Pay+ and Instructions route maps, PAYMENT-CHECKOUT route map, Open Questions Register, and Product Destination Register |
| Substantive commit | `afb4bb02b8de6e7ed63e973127a23b09435c2871` |
| Founder approval | PDM-WI-003 Explore and Proposal dispositions, Draft authorization and corrections, Stage 9 Review passage, Align and Validate authorizations, and conditional Stage 14 Commit approval activated on `2026-08-03` |

**Decision**

Define `PAYMENT-CHECKOUT` as the existing `Partially defined` flow/screen group containing one persistent adaptive Checkout Workspace. Bill/Rent Pay resolves the current Payable Basis, eligibility, and Checkout condition rather than unconditionally creating a Checkout. Eligible New Checkout, intentional Resume, protected return, funding, holistic review, applicable authorization for each Provider Submission, Funding Leg progress, condition-specific results, recovery, and safe exit are composed as replaceable presentations rather than a mandatory fixed wizard, child routes, domain states, events, or new payment objects.

Default single-card funding may progressively expand to owner-confirmed multi-card capabilities. Current-Checkout allocation and Payment Profile are distinct capabilities; Payment Profile remains a reusable ratio template rather than authorization. When exactly one capability is available, the Workspace may enter it directly without silently selecting a profile, confirming an allocation, or authorizing funding. When multiple capabilities are available, the payer selects among them and completes the applicable configuration, review, and authorization.

`DOC-06B` owns route-level Workspace UI/UX, adaptive presentation, entry, return, and handoff behavior. `DOC-09` retains ownership of Payment Domain architecture, objects, invariants, cardinality, locking, immutable confirmed Payments, Payment Application, Settlement, authoritative evidence, and historical-record meaning.

**Rationale**

The adaptive Workspace preserves payer context while keeping authoritative payment truth independent from replaceable presentation. It gives prototype and implementation work a reviewable route-level contract for first views, information hierarchy, actions, protected return, results, mobile use, and accessibility without allowing UI structure to redefine payment identity, authorization, or financial semantics.

**Alternatives Considered**

- A mandatory fixed Checkout wizard was rejected because valid New, Resume, protected-return, progress, pending-evidence, result, and recovery contexts do not share one universal screen order.
- Treating every Bill/Rent Pay action as unconditional new-Checkout creation was rejected because the resolver must respect current eligibility and any active continuable Checkout for the same Payable Basis.
- Requiring Payment Profile for multi-card funding was rejected because owner-confirmed current-Checkout allocation is a separate capability and capability availability must not silently select or authorize funding.
- Using a system decision map as the primary payer journey was rejected because route-level review also requires a concise payer-visible projection while preserving the separate decision map and normative contract.

**Consequences And Handoffs**

DOC-05, the DOC-06 family, DOC-13, route diagrams, and traceability registers now use the accepted owner split, adaptive composition, funding-capability treatment, and unresolved-entry boundaries. `PAYMENT-CHECKOUT` remains `Partially defined`; this decision does not approve final visual design, implementation, technical contracts, copy, accessibility results, or operational readiness.

`DOC-07` owns final authorization, disclosure, and payer-facing wording. `DOC-08` owns notification behavior. Payment, provider, data/audit, security, testing, support, and operations owners retain their technical and validation responsibilities. Prototype, accessibility, user-validation, implementation/UAT, and operational evidence remain pending.

**Supersedes / Superseded By**

None. This decision applies the accepted `DOC-09` v1.1.0 architecture baseline without reinterpreting it.

**Remaining Open Items**

- `OQ-XDOC-007`: whether Instruction `Pay Now` creates, activates, or resumes Checkout remains unresolved.
- `OQ-XDOC-015`: whether an instruction-related notification may bypass `NOTIFICATION-DETAIL` remains unresolved.
- Final prototype, visual design, copy, technical contract, accessibility, user-validation, implementation/UAT, acceptance, monitoring, support, and operational evidence remains with the applicable formal owners.

### `DEC-2026-036` - Instruction Pay Now Resolver And Notification Detail Entry

| Field | Record |
| --- | --- |
| Date | `2026-08-04` |
| Status | Accepted |
| Primary owner | `DOC-09` for Checkout identity and resolver meaning; `DOC-08` for notification entry and current action availability; `DOC-06B` for route-level UI/UX |
| Affected documents | `DOC-05`, `DOC-06A`, `DOC-06B`, `DOC-08`, `DOC-09`, Pay+ route map, Instructions route map, PAYMENT-CHECKOUT route map, Open Questions Register, and Product Destination Register |
| Substantive commit | `d0d35da995da1347844d11366387fbbf95774bd4` |
| Founder approval | PDM-WI-003 Instruction Pay Now and Notification Entry Contracts decisions and conditional Commit, Record, and Push authorization activated on `2026-08-04` |

**Decision**

Instruction `Pay Now` invokes the DOC-09 Checkout Resolver rather than unconditionally creating, activating, or resuming a predetermined Checkout. The resolver validates the authenticated payer, Payment Instruction, current Payable Basis, source/return context, obligation, evidence, eligibility, timing, and applicable controls. An existing Checkout takes precedence only when it remains active, eligible, and continuable; an active continuable Checkout that is currently ineligible is resolved without duplicate creation; a later eligible Checkout may be created only when no active continuable Checkout exists and current eligibility permits; otherwise the payer receives explicit Instruction or source-owner resolution. Payment Instruction and Checkout remain separate, historical Checkouts remain authoritative in their recorded condition, and resolver entry carries no stale authorization or quote and creates no silent Funding Allocation, Funding Leg, Payment Attempt, or Provider Submission.

Every instruction-related notification enters `NOTIFICATION-DETAIL`. Notification Detail revalidates current state, authenticated payer, permission, target, and action availability before an owner-approved current CTA may invoke the same Checkout Resolver. Notification content, delivery, read/archive state, and stored snapshots are non-authoritative and cannot establish Checkout eligibility, payer authorization, Provider Confirmation, Payment, or payment result. Stale, withdrawn, expired, ineligible, or unavailable targets remain in Notification Detail or use the applicable current resolution.

**Rationale**

The resolver preserves Payment Instruction and Checkout identity, respects active-Checkout precedence and retained history, and prevents duplicate or stale execution. Mandatory Notification Detail entry prevents communication convenience or historical notification evidence from bypassing current authority and eligibility checks.

**Alternatives Considered**

- Unconditionally creating a Checkout or predetermining Resume from Instruction `Pay Now` was rejected because current Payable Basis, eligibility, continuability, and retained Checkout history must be resolved first.
- Allowing an instruction-related notification to bypass `NOTIFICATION-DETAIL` was rejected because notification delivery and stored content are not authoritative evidence of current eligibility, authorization, or payment result.

**Consequences And Handoffs**

`OQ-XDOC-007` and `OQ-XDOC-015` are `Decided`, while `PAYMENT-CHECKOUT` remains `Partially defined`. DOC-09 owns Checkout identity and resolver meaning, DOC-08 owns notification entry and current action availability, and DOC-06B owns route-level UI/UX. A separate Manager-owned DOC-07 work item must define communication semantics and final user-facing message and CTA treatment. Technical contracts, prototype and visual evidence, accessibility and user validation, implementation/UAT, acceptance, monitoring, support, and operational evidence remain pending with their formal owners.

**Supersedes / Superseded By**

Completes the two entry-contract decisions left open by `DEC-2026-035` without superseding its accepted adaptive Checkout Workspace direction.

**Remaining Open Items**

- Complete the separate Manager-owned DOC-07 communication-semantic work item without changing the accepted resolver or Detail-first entry contracts.
- Complete the applicable technical, prototype, visual, accessibility, user-validation, implementation/UAT, acceptance, monitoring, support, and operational evidence under their formal owners.

### `DEC-2026-037` - DOC-07 Logical Communication Contracts And Bounded Domain Slices

| Field | Record |
| --- | --- |
| Date | `2026-08-05` |
| Status | Accepted |
| Primary owner | `DOC-07` |
| Affected documents | `AGENTS.md`, `DOC-01`, `DOC-06B`, `DOC-07`, `DOC-22`, DOC-07 Specialist Guide, and Requirements Traceability Matrix |
| Substantive commit | `eec4295bdde299d18d17bcaa6bab20a60786aa1f` |
| Founder approval | PDM-WI-004 `FDP-004-01` through `FDP-004-05`, Stage 6 Founder Decision, and Stage 14 substantive and records commit authorization on `2026-08-05` |

**Decision**

DOC-07 governs material user-facing communication through logically central Semantic, Disclosure, and CTA Contracts supported by logical Reference and Registry Contracts, non-executable Composition, and reference-only Bounded Domain Slices. Source owners retain business conditions, Outcomes, permitted Resolution Strategies, eligibility, routes, notification delivery, runtime and audit, acceptance, support, and operational authority. Reference validity does not establish current eligibility, and CTA Contracts reference action intent, capability, route, or resolver without embedding executable eligibility or business logic.

Copy, Locale Variants, and Presentation Mappings must preserve accepted meaning. AI may propose bounded expression but cannot redefine intent, approve its own output, or receive activation authority. Propose, Approve, and Activate are logical responsibility distinctions only; formal documentation approval and release remain governed by DOC-00 and the canonical Documentation Development Workflow, and no operational activation authority is granted.

Every applicable Provider Submission requires current payer authorization. The confirmed six-card MVP maximum, adaptive Checkout, Instruction `Pay Now` Checkout Resolver, and mandatory instruction-related `NOTIFICATION-DETAIL`-first entry remain preserved.

**Rationale**

This architecture enables semantic-first authoring, cross-document traceability, controlled change, localization readiness, and later technical handoff without coupling independent ownership and maturity into one wide record, duplicating domain authority, turning configuration into business logic, or prematurely selecting a runtime schema or persistent registry.

**Alternatives Considered**

- A single wide Matrix was rejected because it couples independent concerns and owner maturity and becomes difficult to maintain and audit.
- A purely layered architecture was rejected because it weakens bounded domain navigation and increases cross-layer join and runtime pressure.
- Pure federated ownership and pure Slice ownership were rejected because they increase semantic drift, duplication, and fragmented audit coverage.
- The accepted hybrid preserves logical central authority, source-owner retention, bounded navigation, non-executable composition, and reference-only integration.

**Consequences And Handoffs**

DOC-06B retains route, component, placement, destination, entry/return, and adaptive-presentation ownership. DOC-08 retains Notification identity, trigger, recipient, channel, template, delivery, retry, evidence, read/archive, and Detail-first ownership. DOC-09 retains payment, Checkout Resolver, Funding Leg, Provider Submission, and authorization-rule ownership. DOC-15 and DOC-19 retain privacy and security controls. DOC-18 retains runtime, event, audit, and persistent representation. DOC-20 retains acceptance and release evidence. DOC-21 and DOC-22 retain support and Admin operations without inferred permissions or activation authority.

Exact IDs, approved Copy, Locale Variants, Presentation Mappings, notification relationships, runtime mappings, acceptance evidence, Admin mechanisms, and prototype-dependent treatment remain Open, `TBD`, or deferred with their formal owners. TA-21 remains Open. `PAYMENT-CHECKOUT` remains `Partially defined`.

**Supersedes / Superseded By**

Supersedes only the mandatory one-wide Authentication Matrix method recorded historically in `DEC-2026-020` and refines the DOC-07 specialist method recorded in `DEC-2026-032`. It does not supersede `DEC-2026-020` authentication product meaning or the adaptive Checkout and entry contracts in `DEC-2026-035` and `DEC-2026-036`.

**Remaining Open Items**

- TA-21: boundary among DOC-07 Semantic/base Copy, DOC-08 channel-template expression, Locale/platform variants, version relationships, and approval relationships.
- Exact Outcome, Message, CTA, and Notification IDs and mappings; approved Copy and Locale Variants; and prototype-dependent Presentation Mappings.
- DOC-18 runtime, event, audit, schema, version, and persistent representation.
- DOC-20 acceptance, UAT, implementation, accessibility, localization, and release evidence.
- DOC-22 operational roles, permissions, activation, publication, enforcement, audit, and rollback.
- Narrower partner, risk, category, and reconciliation card restrictions and their configuration and enforcement.
- Monitoring, support, implementation, and operational evidence under their formal owners.

### `DEC-2026-038` - PAYMENT-CHECKOUT Defined Baseline

| Field | Record |
| --- | --- |
| Date | `2026-08-05` |
| Status | Accepted |
| Primary owner | `DOC-06B` route-level adaptive UI/UX; `DOC-09` retains authoritative Payment Domain ownership and meaning |
| Affected documents | `DOC-06`, `DOC-06A`, `DOC-06B`, Open Questions Register, and Product Destination Register |
| Substantive commit | `d1e9f550e0f49e861132a96a5e48d8cdcc0882ed` |
| Founder approval | PAYMENT-CHECKOUT Definition Closure Assessment, Definition-Status Draft, Stage 9 Review, Align, Validate, Integrate, and conditional Commit, Record, and Push authorization accepted on `2026-08-05` |

**Decision**

`PAYMENT-CHECKOUT` satisfies the unchanged `Defined baseline` route criterion: its human-readable route behavior is decision-complete enough for continued alignment, while final visual design and technical specification may remain open. It remains one existing `Flow / screen group` containing one persistent adaptive Checkout Workspace. No route, child destination, domain object, state, event, or technical contract is created by this status transition.

`DOC-06B` retains adaptive route-level UI/UX ownership. `DOC-09` retains authoritative Payment Domain architecture and meaning. `DOC-07` retains Semantic, Disclosure, CTA, and Copy ownership, and `DOC-08` retains notification identity, eligibility, delivery, and Detail-first ownership. `OQ-XDOC-007` and `OQ-XDOC-015` remain `Decided`.

**Rationale**

The accepted Checkout Workspace, resolver entry, notification entry, adaptive presentation, funding, authorization, progress, result, recovery, safe-return, mobile, and accessibility behavior now gives continued alignment a decision-complete human-readable route baseline. The status therefore no longer needs to remain `Partially defined`, while owner-controlled expression, technical, validation, implementation, and operational work remains explicitly incomplete.

**Alternatives Considered**

- Keeping `PAYMENT-CHECKOUT` `Partially defined` was rejected because the Definition Closure Assessment found no remaining Category A material route-definition blocker under the existing criterion.
- Treating `Defined baseline` as final visual, technical, implementation, validation, release, operational, or Approved-status completion was rejected because those concerns remain with their formal owners and later lifecycle evidence.

**Consequences And Handoffs**

The Product Destination Register, DOC-06 parent projection, DOC-06A dependency wording, DOC-06B route-owner status, and Open Questions Register now use the active `Defined baseline` treatment. Route identity, adaptive Checkout behavior, resolver and `NOTIFICATION-DETAIL`-first entry contracts, and the DOC-06B/DOC-07/DOC-08/DOC-09 owner split remain unchanged.

Final Bill/Rent source-owner facts, eligibility, CTA, disclosure, and return detail remain pending. Exact Copy, IDs, CTA labels, Locale Variants, and Presentation Mappings remain pending. Provider, schema, event, audit, authentication, and security mappings remain pending. Prototype, accessibility, and user-validation evidence; implementation, UAT, localization, acceptance, and release evidence; monitoring, support, Admin, and operational mechanisms; and final commercial, promotion, risk, and partner values or restrictions remain pending with their formal owners.

This decision does not claim final visual, implementation, validation, operational, release, or Approved-status completion.

**Supersedes / Superseded By**

None. `DEC-2026-038` records a later route-definition status transition and does not rewrite or invalidate `DEC-2026-035`, `DEC-2026-036`, `DEC-2026-037`, their changelog history, or the historical DOC-06B v0.1.40 revision row.

**Remaining Open Items**

- Final Bill/Rent source-owner facts, eligibility, CTA, disclosure, and return detail.
- Exact Copy, IDs, CTA labels, Locale Variants, and Presentation Mappings.
- Provider, schema, event, audit, authentication, and security mappings.
- Prototype, accessibility, user-validation, implementation, UAT, localization, acceptance, and release evidence.
- Monitoring, support, Admin, and operational mechanisms.
- Final commercial, promotion, risk, and partner values or restrictions.
