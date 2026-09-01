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
| `DEC-2026-039` | `2026-08-06` | HOME-ROOT Logged-In Dashboard Presentation And Navigation Contracts | Accepted | `DOC-06B` | `c14fafe5ef70feedf64ee46c6451ed6e19fd402e` |
| `DEC-2026-040` | `2026-08-06` | Entrance Promotion Detail, Carousel, And Placement Management | Accepted | `DOC-06B` / `DOC-13` / `DOC-22` | `cebe5fce140e41cddfae131193d51d059e3fd424` |
| `DEC-2026-041` | `2026-08-11` | Workflow Draft Review Handoff And Review Convergence | Accepted | Documentation Development Workflow | `9072e00fffe3f3329dbf522c8965500e78d56b21` |
| `DEC-2026-042` | `2026-08-13` | Payer-Only Bill And Rent Architecture Alignment | Accepted | Multiple formal owners | `43e35bcd86f2fd5464606d6e9213aabda1a4b794` |
| `DEC-2026-043` | `2026-08-14` | DOC-16 Risk-Isolated Technical Architecture Baseline | Accepted | `DOC-16` | `77144f12d6675f6305c9a96e00bc75af97702f6e` |
| `DEC-2026-044` | `2026-08-18` | Material Workflow Fixed-Seat Review Controls | Accepted | Documentation Development Workflow | `651e739bd1d33e3068fc9e295879d5ddff4f1e79` |
| `DEC-2026-045` | `2026-08-20` | Material Proposal/Draft Convergence Workflow Correction | Accepted | Documentation Development Workflow / Parallel-Agent Documentation Procedure | `84656924860368e8055731175b9296fdf0912159` |
| `DEC-2026-046` | `2026-08-21` | DOC-19 Mechanism-Neutral Security Control Alignment | Accepted | `DOC-19` | `860fd78cbb7cc5a080e10334291b60ff8902a77d` |
| `DEC-2026-047` | `2026-08-20` | Bills Tiered Evidence, Declaration, Payment And Payout Model | Accepted | `DOC-05` / `DOC-06C` / `DOC-09` / `DOC-10` / `DOC-12` / `DOC-14` | `e84ce35dd0fa4687d2f98dd08191645fcffa69af` |
| `DEC-2026-048` | `2026-08-06` | ENTRANCE-PROMOTION-DETAIL Defined Baseline | Accepted | `DOC-06B` / `DOC-13` / `DOC-22` | `ec9b97bb4cf9b2e5b03992f4a23c546146de97e6` |
| `DEC-2026-049` | `2026-08-25` | DOC-17 Provider-Neutral External Interaction Contract | Accepted | `DOC-17` | `339bd8c8dfccf60ab102aa706f04135c9aab9e36` |
| `Not applicable` | `2026-08-23` | BTPR R2 Documentation Integration Record | Not applicable | Existing `FD-BTPR-01` owners | `7664d339e45c6e183cb8d6a2b0b107a405200749` |
| `Not applicable` | `2026-09-01` | DOC-10, DOC-12, And DOC-14 Technical Allocation Reconciliation | Not applicable | `DOC-10` / `DOC-12` / `DOC-14` | `f33e3cf88e57bb22c3269d50a9fdc34258b12049` |
| `Not applicable` | `2026-09-01` | DOC-09 Technical Allocation Reconciliation | Not applicable | `DOC-09` | `c11fa2e3a4807b1c601fc20d1052ff84bcf48263` |
| `Not applicable` | `2026-09-01` | DOC-13 Technical Allocation Reconciliation | Not applicable | `DOC-13` | `c8b6a8d55039e6bfe9a8773e7253db073753cf13` |

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

### `DEC-2026-039` - HOME-ROOT Logged-In Dashboard Presentation And Navigation Contracts

| Field | Record |
| --- | --- |
| Date | `2026-08-06` |
| Status | Accepted |
| Primary owner | `DOC-06B` HOME-ROOT route-level presentation and navigation |
| Affected documents | `DOC-05`, `DOC-06`, `DOC-06A`, `DOC-06B`, `DOC-06C`, `DOC-06D`, `DOC-07`, `DOC-08`, `DOC-09`, `DOC-10`, `DOC-11`, `DOC-13`, `DOC-15`, `DOC-22`, Requirements Traceability Matrix, Open Questions Register, Home Route Map, and Offers/Rewards/Referral Route Map |
| Substantive commit | `c14fafe5ef70feedf64ee46c6451ed6e19fd402e` |
| Founder approval | PDM-WI-005 accepted Founder decisions and conditional Integrate, Commit, and Push authorization on `2026-08-06`; mandatory records treatment applied under the Documentation Development Workflow |

**Decision**

`HOME-ROOT` remains the existing logged-in root and remains `Partially defined`. Its task-first section order is Header, Important Notice, Shortcut Grid, Home Hot Offer, Upcoming Bills / Rent, and Recent Activity. Greeting has no navigation and uses the accepted local-time bands, neutral timezone fallback, and Nickname then applicable `Mr./Miss + eKYC surname` then surname-only name precedence, with DOC-07 owning exact TC, SC, and EN expression.

Important Notice presents one eligible Inbox-backed notification, consumes source-owned canonical ordering values, uses canonical-session dismissal without changing notification or business state, opens `NOTIFICATION-DETAIL` from the body, and uses only a source-provided current action destination. Home Hot Offer is an Offer-only, Admin-selected surface that may present any canonical Offer status, shows no more than five cards, hides at zero candidates, opens `OFFER-DETAIL`, uses fixed or random Admin ordering and a five-second default rotation with the accepted stop/resume and reduced-motion treatment, and does not derive Offer eligibility or validate content completeness.

Upcoming Bills / Rent consumes active payer-role HKD candidates from DOC-06C, shows up to three, and orders them by due date, amount, type, creation timestamp, and stable source record ID. Recent Activity shows up to five completed source-owned Payment, Partial Payment, Payout, Refund, or Reversal outcomes ordered by canonical timestamp, with amount sign determined by canonical funds-flow direction. HOME-ROOT applies smallest-practical-surface resilience and no separate accessibility mode.

DOC-06B owns Home presentation, selection, ordering, capacity, interaction, navigation, dismissal, and return behavior without acquiring business truth. Source domains retain canonical notification, Bill/Rent, Offer, outcome, timestamp, funds-flow, privacy, technical, acceptance, and Admin meanings. Admin controls approved presentation but cannot alter or suppress canonical business truth.

**Rationale**

The accepted contracts make the existing logged-in Home route decision-ready for later visual, technical, prototype, and validation work while preserving task-first navigation, deterministic source-value consumption, safe disclosure, graceful degradation, and one primary owner per material concept. The owner-first composition model avoids making Home or Admin a duplicate business-content authority.

**Alternatives Considered**

- A combined Featured / What's New / Hot Offer Home carousel was not selected because the accepted HOME-ROOT surface is Offer-only and announcements and notification behavior retain their existing owners.
- Home-derived display eligibility, ordering normalization, status filtering, or fallback semantics were not selected because HOME-ROOT consumes canonical values and must not reinterpret source truth.
- Duplicating Home capacity, zero-state, routing, ranking, dismissal, or interaction rules in secondary owners was rejected in favor of bounded owner handoffs.
- A random final Upcoming Bills/Rent tie-break was replaced by canonical creation timestamp and stable source record ID for deterministic behavior.
- A route-specific mandatory visible Pause/Play control was not selected; the adopted platform accessibility standard may still require one during later implementation.

**Consequences And Handoffs**

DOC-06A retains journey touchpoints; DOC-06C retains Bill/Rent candidates and source facts; DOC-07 retains exact expression; DOC-08 retains notification identity, lifecycle, Inbox, Detail, and delivery; DOC-09, DOC-10, and DOC-11 retain outcome, timestamp, amount, and funds-flow truth; DOC-13 retains Offer identity, content, status, validity, eligibility, and available-action truth; DOC-15 retains privacy and approved-purpose rules; DOC-18 retains future technical data, status, event, audit, lineage, and reporting; DOC-20 retains detailed acceptance and UAT evidence; and DOC-22 retains Admin configuration, publication quality, audit, and operational controls.

The parent product and journey documents, acceptance mapping, traceability records, open questions, and current route diagrams now reference or project this owner split. The external `for-neng` derivative and Draft Research Memo remain expressly excluded non-authoritative supporting material for this change.

**Supersedes / Superseded By**

Supersedes active HOME-ROOT combined Featured / What's New / Hot Offer terminology and the corresponding decided portions of OQ-05-017, OQ-06-024, OQ-06-025, and OQ-XDOC-011. Historical, archived, and excluded supporting occurrences remain non-operative. No earlier decision record is superseded.

**Remaining Open Items**

- Final HOME-ROOT visual design, prototype, and user-validation evidence.
- Exact DOC-07 Copy, identifiers, CTA labels, Locale Variants, and presentation mappings.
- Technical session, cache, freshness, schema, status/event/audit, analytics, retention, cross-device, authentication, security, monitoring, and operational mechanics.
- Adopted-platform accessibility implementation and detailed DOC-20 acceptance, UAT, implementation, localization, and release evidence.
- Detailed DOC-22 Admin screens, permissions, approval workflow, implementation fields, and operational evidence.

### `DEC-2026-040` - Entrance Promotion Detail, Carousel, And Placement Management

| Field | Record |
| --- | --- |
| Date | `2026-08-06` |
| Status | Accepted |
| Primary owner | `DOC-06B` Entrance Carousel and ENTRANCE-PROMOTION-DETAIL route-level behavior; `DOC-13` Promotion/Offer source truth and placement-timing boundary; `DOC-22` Feature Management and central Entrance placement workflow |
| Affected documents | `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`, `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md`, `docs/08-qa-release-operations/doc-22-admin-management-dashboard-operations-workflow.md`, `docs/traceability/route-register.md`, `docs/traceability/open-questions-register.md` |
| Substantive commit | `cebe5fce140e41cddfae131193d51d059e3fd424` |
| Founder approval | PDM-WI-006 accepted Founder decisions, Stage 9 review, Stages 10–12 alignment and validation, Stage 13 integration, and conditional Commit, Record, and Push authorization on `2026-08-06`; mandatory records treatment applied under the Documentation Development Workflow |

**Decision**

Entrance supports only the `Promotion` and `Feature` content classes. `Offer` is not a separate Entrance class; a Promotion may reference an applicable Offer-owned source while remaining a Promotion for Entrance placement and presentation. `Announcement` is excluded from active Entrance scope. `ENTRANCE-ROOT` remains the Defined public unauthenticated root, `ENTRANCE-CAROUSEL` remains a component, and `ENTRANCE-PROMOTION-DETAIL` remains the existing Partially defined child route.

The public contract is Header, a full-width 4:5 image-only Carousel, interactive dots, and horizontally arranged Login / Registration buttons. The Carousel uses the accepted five-second Crossfade, dot selection, horizontal swipe with a swipe-versus-tap threshold, full timer interval after manual interaction, fixed first-use swipe affordance with reduced-motion treatment, and zero, one, and multiple-item behavior. Placement allows at most five active items and one optional priority item first, with deterministic manual ordering for the remainder and no random ordering.

Detail uses one visible Back control, no separate Close control, platform Back with the same result, an image-first 4:5 presentation, name, activity date, Summary, inline Terms, one continuous vertical scroll, and same-item-and-position restoration. Detail supports zero or one source- and route-owner-approved CTA; no CTA produces informational detail and Admin placement cannot invent an action or destination.

Central Entrance Carousel Management owns placement selection, Display on Entrance, timing choice, priority, manual order, preview, publication, and removal. For a Promotion, `Use Promotion Period` checked follows the canonical Promotion period while manual placement dates are read-only; unchecked uses separately managed placement dates. Feature placement always uses manually managed dates. Feature content has an independent Feature Management source area with an identifiable reference, formal product/business-truth owner, public name, 1080 × 1350 image, accessibility description, activity/feature date value, summary, Terms content or approved reference, optional source-approved action intent and destination, locale variants, and content-readiness evidence. Placement fields are not duplicated into Feature source management.

Placement is suspended when its Promotion or Feature source is withdrawn, prohibited from public display, no longer authorized, or materially changed after approved preview/publication. Suspension removes the item from active Entrance presentation while preserving the source record and historical placement evidence; restoration requires updated preview and republication.

**Rationale**

The accepted contract preserves a simple public unauthenticated entry experience while keeping route presentation, Promotion/Offer truth, Feature truth, and Admin placement responsibilities separate. Central placement management gives one controlled location for common Entrance sequencing and publication without making DOC-06B or DOC-22 a source-truth owner.

**Alternatives Considered**

No new product alternatives were selected at the records stage. The Founder-approved Carousel, detail, timing, sequence, navigation, action, Terms, Feature Management, source-safety, and ownership decisions are recorded as the accepted direction; the substantive commit contains the bounded comparison and recommendation evidence from Proposal.

**Consequences And Handoffs**

DOC-06B owns route-level presentation, interaction, navigation, and return behavior; DOC-13 retains Promotion/Offer identity, content, validity, eligibility, entitlement, and available-action truth; and DOC-22 owns Admin workflow and configuration without becoming business-truth owner. DOC-07 retains exact Copy and CTA expression/presentation. DOC-18–DOC-21 and later DOC-22 work retain technical data, status/event/audit, security, testing, acceptance, monitoring, support, and operational mechanisms. Design, platform accessibility, validation, and implementation evidence remain deferred. No prototype, route-status advancement, technical implementation, or roadmap update is included.

**Supersedes / Superseded By**

Supersedes active traceability wording that treated Offer as a separate Entrance class and the decided portions of the broad Entrance open question that are now resolved. Historical append-only decision, changelog, and other historical records remain unchanged. No earlier decision record is renumbered or rewritten.

**Remaining Open Items**

- Exact DOC-07 Copy, CTA labels, accessibility expression, and presentation details.
- Responsive and reduced-motion implementation, gesture thresholds, cue persistence, and visual validation.
- Exact date storage, timezone, synchronization, validation, scheduler, source-change detection, permissions, audit/events, monitoring, UAT, acceptance, and release mechanisms under their later formal owners.
- Later DOC-22 operational and technical workflow detail, plus Design, platform, accessibility, validation, and implementation evidence.
- `ENTRANCE-PROMOTION-DETAIL` remains `Partially defined`; no route or document status advancement is recorded.

### `DEC-2026-041` - Workflow Draft Review Handoff And Review Convergence

| Field | Record |
| --- | --- |
| Date | `2026-08-11` |
| Status | Accepted |
| Primary owner | `docs/documentation-system/payplus-documentation-development-workflow.md` §§4.5.3, 4.5.4, and 6.3 |
| Affected documents | `docs/documentation-system/payplus-documentation-development-workflow.md` |
| Substantive commit | `9072e00fffe3f3329dbf522c8965500e78d56b21` |
| Founder approval | Founder-approved minimal Workflow-only Proposal with automatic progression through Align, Validate, Integrate, and Commit when canonical gates pass on `2026-08-11`; Push not authorized |

**Decision**

The existing Stage 8 Draft exit and handoff condition is strengthened so the Draft Review handoff and coverage materials must self-prove substantive completeness within the accepted boundary before Stage 9 Review. Stage 9 independently confirms or refutes that claim against the approved Proposal, authoritative sources, and approved coverage materials.

Each Review `FAIL` containing accepted-scope findings creates one consolidated Draft correction scope for that Review phase and its permitted finding boundary. Only corrections restoring fidelity to the approved Proposal or accepted design within the authorized Draft boundary are included. New design decisions return to Proposal, evidence gaps return to Explore, and findings outside the accepted design or scope remain in the Review result rather than being absorbed into Draft correction.

Valid owner-backed `TBD`, `Open`, and deferred items remain visible. Material uncovered, unknown, ownerless, or substantive-completeness gaps block Stage 8 exit. Mutation scope remains distinct from broader read-only assessment scope. The change creates no new lifecycle stage, gate, Evidence Pack system, numeric failure counter, expanded prompt machinery, or agent-count requirement.

**Rationale**

The accepted change closes the existing Draft-to-Review handoff ambiguity while preserving the canonical Workflow as the sole lifecycle authority. It makes completeness evidence explicit, keeps independent Review meaningful, and preserves routing for design and evidence uncertainty without expanding the approved Workflow-only boundary.

**Alternatives Considered**

- A new lifecycle stage or gate was not selected because the accepted direction strengthens the existing Stage 8 exit and Stage 9 Review contracts.
- A permanent Evidence Pack, numeric failure counter, expanded prompt system, or new agent-count rule was not selected because execution evidence and existing independent-review requirements remain sufficient.
- Supporting-document mutations were not selected because read-only impact assessment found no contradictory or materially incomplete governed reference requiring alignment.

**Consequences And Handoffs**

The canonical Workflow remains the sole owner of lifecycle stages, gates, validation authority, records treatment, and Git completion rules. Supporting references remain unchanged and continue to route to the Workflow. The substantive commit is followed by this immediate records-only commit. Push requires separate explicit authorization.

**Supersedes / Superseded By**

Supersedes the prior Stage 8 handoff wording that ended at a pre-Primary Review representation check. No product, domain, technical, route, status, ownership, or source-of-truth definition is superseded.

**Remaining Open Items**

- Push remains unauthorized and is outside this Commit executor task.
- No new unresolved product or governance decision remains from this accepted Workflow-only change.

### `DEC-2026-042` - Payer-Only Bill And Rent Architecture Alignment

| Field | Record |
| --- | --- |
| Date | `2026-08-13` |
| Status | Accepted |
| Primary owner | Existing formal owners for product, route, payment, evidence, risk, privacy, promotion, acceptance, operations, Admin, and the aligned reference artifacts |
| Affected documents | Exactly the 37 paths in substantive commit `43e35bcd86f2fd5464606d6e9213aabda1a4b794`: the 23 reviewed formal documents plus the 14 aligned artifacts listed in the corresponding changelog entry |
| Substantive commit | `43e35bcd86f2fd5464606d6e9213aabda1a4b794` |
| Founder approval | PDM-WI-008 accepted the existing Wave 1-6 architecture and explicitly authorized conditional Stage 13 Integration, Stage 15 Commit, and immediate Stage 16/17 records treatment on `2026-08-13`; Push is not authorized |

**Decision**

The existing Founder-approved PayPlus architecture is recorded as delivered and aligned. Consumer Users are Payers only; economic Payees may be individuals or institutions and need not be Users. Launch scope is exactly the twelve controlled Bill Categories plus separate Rent, acquired through Category-bound Directory or self-provided context. Request, Linking, Receive, Receiving Info, Consumer-Payee, and Payee-user runtime is rejected/superseded and remains only as explicit non-active provenance where present. The formal owner chain remains authoritative for source, Payable Basis, applicable Obligations, one-basis Checkout, allocations/Funding Legs, immutable confirmed Payment, Payment Applications, controlled zero/insufficient-Application exceptions, Payout/reconciliation, Evidence, notification, risk, privacy, promotion, acceptance, operations, Admin execution, and future representation.

Every PayPlus record remains retained indefinitely; operational expiry, access/masking restrictions, source Archive visibility, account closure, and terminal or case outcomes do not erase records. The 14 derived/reference artifacts were synchronized to this accepted meaning and formal owner boundaries. This records no new product, governance, legal, commercial, security, provider, retention, route, status, event, permission, schema, category, or implementation decision.

**Rationale**

Stage 10 impact assessment, Stage 11 alignment, Stage 12 integrated validation, and Stage 13 integration confirmed that the accepted formal baseline and its derived/reference projections agree. The alignment removes stale Request/Payee-user and broad-inventory implications while preserving owner truth, historical provenance, deferred detail, and the no-redesign boundary.

**Alternatives Considered**

- Retaining active Request, Linking, Receive, Receiving Info, or Payee-user terminology was rejected because those product paths are retired and cannot remain active in derived references.
- Treating Rent as a Bill Category or permitting broad obligations was rejected because the accepted launch inventory is fixed and Rent is a separate journey.
- Making derived artifacts new source owners or adding routes, statuses, actions, schemas, events, permissions, retention exceptions, providers, or implementation mechanisms was rejected because alignment cannot create requirements.

**Consequences And Handoffs**

The formal document owners remain the source of truth. Derived route maps, glossary, route register, status matrix, RTM, OQ register, and README indexes are aligned projections only. DOC-18/19 representation and security detail, future implementation and AI-build material, prototype work, UAT/release evidence, and operational mechanisms remain deferred to their formal owners and later lifecycle stages. No push or remote mutation occurred.

**Supersedes / Superseded By**

Supersedes active derived-reference wording that implied open Requests, Payee-user participation, broad obligations, Rent-as-Category, stale Receive/Linking/Receiving Info routes, or conflated Payment Instruction/Checkout with source Archive. Historical append-only records, revision rows, backups, and non-authoritative provenance remain unchanged. No formal owner definition is superseded.

**Remaining Open Items**

- Later owner work for technical representation/security, implementation, prototypes, AI-build conversion, UAT/release evidence, monitoring and operations remains open and is not included in this alignment record.
- Push requires separate explicit authorization.

### `DEC-2026-043` - DOC-16 Risk-Isolated Technical Architecture Baseline

| Field | Record |
| --- | --- |
| Date | `2026-08-14` |
| Status | Accepted |
| Primary owner | `DOC-16`, technical architecture |
| Affected documents | `AGENTS.md`, `docs/README.md`, `docs/glossary/glossary.md`, `DOC-16`, `DOC-18`, `DOC-20`, `DOC-21`, `DOC-22`, requirements traceability matrix, open-questions register, documentation-management roadmap |
| Substantive commit | `77144f12d6675f6305c9a96e00bc75af97702f6e` |
| Founder approval | Founder approved `DOC16-FD-01` through `DOC16-FD-05`, the bounded DOC-16 Draft and Review chain, Stage 10 impact manifest, conditional Alignment/Validation/Integration/Commit, and separate Push authorization on `2026-08-14` |

**Decision**

PayPlus adopts a risk-isolated modular architecture without pre-committing to full microservices. Each authoritative owner preserves local atomic state and invariants; cross-boundary and provider handoffs are durable, retryable, idempotent, correlated, auditable, recoverable, and reconcilable, and never replace or silently rewrite authoritative domain truth.

Provider-controlled capture and tokenization is the default payment-data boundary. PayPlus does not receive, process, transmit, or retain raw PAN or card-verification values unless a separately authorized architecture and security Proposal changes that boundary. Provider token/reference values and approved masked metadata remain distinct from raw card data.

Security & Compliance by Design applies across technical work from the outset, including applicable ISO/IEC 27001, PCI DSS, privacy, payment, regulatory, least-privilege, segregation-of-duties, auditability, reliability, recovery, reconciliation, observability, testability, and evidence considerations. Documentation alone does not establish certification or compliance. Operational expiry or invalidation does not erase the indefinitely retained record.

`DOC-16` owns architecture posture and boundaries. `DOC-17` owns future provider/API integration detail, `DOC-18` owns approved representation/status/event/audit/lineage detail, `DOC-19` owns future authentication/token/access/security implementation detail, and `DOC-20`, `DOC-21`, and `DOC-22` own acceptance evidence, operational evidence, and owner-permitted Admin execution respectively. Technical owners must consume accepted product/domain requirements and return genuine conflicts through the canonical workflow rather than reopening them implicitly.

**Rationale**

This baseline preserves professional technical ownership, limits sensitive-payment and PCI scope, supports strong transaction and recovery invariants, and avoids both premature distributed-system commitments and under-specified security, compliance, financial, and operational controls. The owner split keeps architecture normative while deferring implementation mechanisms to their formal owners.

**Alternatives Considered**

- Pre-committing PayPlus to full microservices was rejected because the accepted risk-isolated modular posture permits technical isolation only where evidence and risk justify it.
- Direct PayPlus handling or storage of raw PAN/card-verification values was rejected as the default because provider-controlled capture/tokenization reduces sensitive-data and PCI scope.
- Treating a cross-boundary handoff as one distributed atomic transaction was rejected because each owner retains local atomic authority and durable handoffs preserve recoverability and reconciliation.
- Treating operational expiry as record deletion was rejected because usability/security lifetime and indefinite record retention are separate concerns.
- Inventing provider mechanics, APIs, schemas, events, databases, security constants, routes, statuses, or implementation completion in DOC-16 was rejected in favor of explicit owner handoffs.

**Consequences And Handoffs**

DOC-18 and DOC-20 through DOC-22 now consume the architecture boundaries without redefining them. `AGENTS.md`, the documentation index, glossary, RTM, OQ register, and roadmap identify the current DOC-16 baseline and its downstream owners. DOC-17 and DOC-19 remain protected placeholders and require separate owner-first work before provider integration and security implementation can be considered fully defined. Later implementation, testing, operational evidence, and certification assessment must demonstrate the controls; this decision does not claim production or certification completion.

**Supersedes / Superseded By**

Supersedes any active implication that PayPlus is already committed to full microservices, may treat cross-boundary work as one transaction, may handle raw card data by default, or may treat operational expiry as record destruction. Historical provenance remains unchanged.

**Remaining Open Items**

- Owner-first drafting and independent review of DOC-17 provider/API integration and DOC-19 security implementation detail.
- Final approved schemas, events, persistence, security mechanisms, operational controls, implementation, tests, evidence, and any external certification remain later-owner work.

### `DEC-2026-044` - Material Workflow Fixed-Seat Review Controls

| Field | Record |
| --- | --- |
| Date | `2026-08-18` |
| Status | Accepted |
| Primary owner | `docs/documentation-system/payplus-documentation-development-workflow.md` Section 3.1 and its material Stage 5, Stage 7, and Stage 8 enforcement references |
| Affected documents | `docs/documentation-system/payplus-documentation-development-workflow.md` |
| Substantive commit | `651e739bd1d33e3068fc9e295879d5ddff4f1e79` |
| Founder approval | Founder-approved final Stage 5 Proposal and direct clarifications, followed by the authorized and gated Draft, Review, Align, Validate, Integrate, and substantive Commit chain on `2026-08-18` |

**Decision**

Material Stage 5 Proposal uses exactly four distinct participating agent seats: one Primary-owner Lead and three Manager-selected specialist reviewers whose professional profiles are selected for the actual task and document. All four independently produce Round 1 positions from a common evidence package, the same four perform Round 2 cross-challenge, and the Lead performs Round 3 consolidation. There is no separate Stage 5 Challenger. Missing or combined seats, a missing independent position, incomplete cross-challenge, or absent consolidation blocks material Stage 5 exit.

Ordinary material Stage 8 retains the same four participants. Where material Draft begins from equivalent explicit Founder authority without a preceding four-agent Stage 5 team, the Manager selects and records the four participants at Stage 7 using the same profile-selection rules. One canonical writer controls each formal document and the three specialist reviewers remain read-only.

The Manager separately appoints one additional independent, read-only, non-authoring Challenger, producing exactly five Stage 8 participants. The required sequence is canonical writer Draft, three specialist reviews, Challenger completeness and fidelity review, accepted-scope writer correction, relevant specialist reinspection, Challenger actual-final-byte reinspection, and evidence-bearing Stage 8 handoff. Missing review, independence, correction closure, specialist reinspection, final-byte reinspection, or substantive completeness blocks exit. Any later formal-document or controlling Decision Coverage Matrix change invalidates affected closure evidence and repeats the applicable reviews.

The fixed-seat contract is the canonical exception for material Stage 5 and Stage 8. Non-material exact-scoped work retains proportionate adaptive treatment. Stage 9 remains unchanged, and the Stage 8 Challenger does not approve or substitute for Stage 9 Primary Review.

**Rationale**

The fixed-seat model provides predictable professional coverage for material documentation decisions and Drafts while allowing the three specialist profiles to match the actual document, owner, and cross-owner handoffs. It preserves one accountable Lead/writer, independent specialist depth, horizontal completeness challenge, and a separate formal Stage 9 gate without creating a large permanent specialist hierarchy.

**Alternatives Considered**

- Permanently fixing the same three specialist profile names for every document was rejected because Product, UX, Payment, API, backend, security, and operations documents require different expertise.
- Retaining a fully adaptive participant count for material work was rejected because it does not guarantee the required four-seat coverage or the separate Stage 8 Challenger.

**Consequences And Handoffs**

Material work requires additional coordination and agent capacity. The Documentation Manager selects or retains task-relevant profiles, records capability and authority boundaries, issues the task contract, receives the detailed Executor Result Pack, and reports only a concise status summary without filling a counted seat or substituting for the Executor. Supporting procedures and routing references remain unchanged and subordinate to the Workflow's material-stage exception. No product, domain, technical, route, status, implementation, legal, compliance, security, privacy, provider, certification, or production-readiness decision is introduced.

**Supersedes / Superseded By**

Establishes the later material Stage 5 and Stage 8 exception to the general adaptive-role treatment recorded by `DEC-2026-029` and to the then-current no-agent-count treatment recorded by `DEC-2026-041`. Both earlier records remain unchanged and time-accurate for their substantive commits; their other command-interface, lifecycle-ownership, completeness, correction-routing, and evidence-boundary decisions remain effective.

**Remaining Open Items**

- Future operation of the fixed-seat control remains to be evidenced through later material tasks.
- Internal specialist titles do not establish external accreditation, professional approval, implementation readiness, or production readiness.
- The `3adb` Stage 8 replacement-reviewer exception remains task-local and is not a canonical replacement rule.
- Push is authorized separately but had not occurred when this record was prepared.

### `DEC-2026-045` - Material Proposal/Draft Convergence Workflow Correction

| Field | Record |
| --- | --- |
| Date | `2026-08-20` |
| Status | Accepted |
| Primary owner | `docs/documentation-system/payplus-documentation-development-workflow.md` and `docs/documentation-system/payplus-parallel-agent-documentation-procedure.md` |
| Affected documents | The two primary operating documents above |
| Substantive commit | `84656924860368e8055731175b9296fdf0912159` |
| Founder approval | Founder-approved governance direction and conditional Stage 12-20 sequence after independent Stage 9 Review and Stage 10 Align evidence |

**Decision**

Material Stage 5 uses one Lead plus three distinct task-selected Specialists by default. The Documentation Manager may add one distinct fourth Specialist only for a documented genuine material coverage gap involving an uncovered decision, interface, owner, or required capability that cannot safely be reassigned. The exception records its scope, limitation, and cost and returns to the Founder only where it requires new material scope, ownership, product or governance authority.

The same selected team normally continues into material Stage 8, with evidence-backed replacement onboarding where continuity is unavailable. One canonical Writer controls one Draft; selected Specialists inspect the complete Draft and complete diff through assigned lenses while deep source review remains proportionate. Every material cross-domain interface receives two recorded Specialist lenses. One additional independent, read-only Whole-Draft Completeness Reviewer cannot replace a Specialist or Stage 9 Primary Reviewer.

Decision Coverage remains mandatory. One logically separable task-context Draft Control Record may provide the Draft Plan, coverage, findings and dispositions, correction and closure, Acceptance Criteria and traceability, residuals, and final identity without becoming a permanent Evidence Pack, new documentation layer, or required file format. The Workflow owns lifecycle obligations and consequences; the Procedure owns task-packet, convergence, correction, and return-control mechanics.

Material Proposal preserves independent concise Decision Positions, exception-driven cross-challenge over the complete decision universe, and Lead-only consolidation. Material Draft preserves complete review universes, frozen consolidated findings, batch correction, semantic closure, supported non-semantic treatment, bounded delta closure, authoritative affected-scope routing, accepted-scope completeness, prospective transition, and a fresh independent Stage 9 gate.

**Rationale**

The correction keeps the minimum professional coverage and independent review safeguards while allowing a recorded fourth lens when a genuine material interface, owner, decision, or capability gap would otherwise remain uncovered. It removes repeated full-source reading and overlapping task-context artifacts without reducing complete-Draft inspection, Decision Coverage, correction closure, or Stage 9 independence.

**Alternatives Considered**

- Retaining the exact Lead-plus-three model was rejected because it cannot cover a demonstrated fourth material lens.
- Fully adaptive or uncapped staffing was rejected because cost, independence, continuity, and completion evidence would become unpredictable.
- A separate Stage 5 Challenger, competing Draft writers, visibility-only review, duplicate deep reading of every source, immediate piecemeal correction, a permanent Evidence Pack, and migration-only reopening of completed Stage 9 work were rejected because they weaken control, increase duplication, or expand governance unnecessarily.

**Consequences And Handoffs**

The Workflow remains the sole lifecycle authority. The Procedure implements the selected-team packet, Draft Control Record, complete-review/frozen-finding, correction, closure, supplement, and return mechanics without issuing lifecycle results or Git authority. Existing protected Work Command Language, Architecture Map, AGENTS.md, and historical records remain valid where they are subordinate or time-accurate; later alignment is required only for a verified operative contradiction. No product, domain, technical, privacy, security, provider, implementation, certification, or production decision is introduced.

**Supersedes / Superseded By**

Supersedes the active material exact-seat, same-four, separate-Draft-Plan/Decision-Coverage, and earlier Stage 8 review-expression controls established by `DEC-2026-044` where they conflict with this accepted current Workflow. `DEC-2026-044` remains unchanged as append-only historical provenance for commit `651e739bd1d33e3068fc9e295879d5ddff4f1e79`. The unaffected lifecycle-ownership, source-boundary, and historical-record principles of `DEC-2026-041` and `DEC-2026-044` remain effective.

**Remaining Open Items**

- Future material tasks must provide operational evidence that the revised responsibility and convergence controls work as intended.
- No historical Stage 9 work is reopened solely for migration; later evidence-backed findings follow the normal lifecycle.
- Push and completion depend on the separately verified records-only commit and current remote equality; neither is asserted by this decision record.

### `DEC-2026-047` - Bills Tiered Evidence, Declaration, Payment And Payout Model

| Field | Record |
| --- | --- |
| Date | `2026-08-20` |
| Status | Accepted |
| Primary owner | `DOC-05` product policy; `DOC-06C` Bills/Rent UX; `DOC-09` Payment; `DOC-10` Payout; `DOC-12` Evidence; `DOC-14` risk/control |
| Affected documents | DOC-01–05; DOC-06, DOC-06A, DOC-06B, DOC-06C, DOC-06D, DOC-07, DOC-08; DOC-09–12; DOC-14–16, DOC-18, DOC-20–22; and the aligned documentation index, glossary, traceability and governed Bills/Checkout/Archive diagrams |
| Substantive commit | `e84ce35dd0fa4687d2f98dd08191645fcffa69af` |
| Founder approval | Founder-approved consolidated Bill-only tiered Evidence, Declaration, Payment and Payout package, with explicit Stage 14–16 commit and push authorization on `2026-08-20` |

**Decision-Record Correction / Provenance**

At correction time, the locked live `main` registry already owned `DEC-2026-044` for Material Workflow Fixed-Seat Review Controls. The previously unmerged Bills branch-local use of `DEC-2026-044` therefore collided with that canonical record. `DEC-2026-047` is the canonical replacement ID for this Bills decision; the former branch-local label remains preserved only through Git history and this correction provenance. The Bills substantive commit and accepted decision text remain `e84ce35dd0fa4687d2f98dd08191645fcffa69af`; this record-only correction does not alter Bills product content.

The Phase 2 main merge-result record must cite `DEC-2026-047` for the Bills alignment while retaining distinct references to main `DEC-2026-044`, main `DEC-2026-045`, and DOC-19 `DEC-2026-046`.

**Decision**

Bills use the approved three-tier C1/G1/G2 model and highest-tier precedence. Tier 1 requires Declaration but no mandatory attached Evidence; Tier 2 requires owner-approved official Bill Evidence presence before Payment and acceptance before Payout; Tier 3 requires qualifying Evidence and authorized approval before executable Payment progression, while a prepared Checkout Workspace remains non-executable. Rent remains separate with mandatory attached Evidence accepted before Payment.

G1 is a product-semantic limit of five independent user-initiated Bill payment progressions per Hong Kong calendar month by the same receiving account/authoritative payout destination, not economic-Payee identity or a technical Payment record. G2 pre-checks confirmed monthly Bill usage plus proposed obligation-funded value and finalizes from actual confirmed value; payer fees are excluded, Refund/reversal does not restore capacity, and only confirmed duplicate/error correction does. C1 policy authority is layered: the designated product/risk owner governs policy, DOC-12 binds Category configuration, DOC-09 consumes it, and DOC-22 executes approved configuration only.

Save expresses persistence, visibility and reuse intent. Saved/current, Saved/Archived, history-only and unprojected treatment remain distinct from readiness, Checkout, Payment, Payout, Refund, case and reconciliation truth. Indefinite retention remains the accepted product/governance direction subject to lawful scope, required exceptions, restricted data classes and prohibited sensitive-data boundaries.

**Rationale**

The accepted model gives a predictable Bill-only control boundary while preserving the existing Rent gate, immutable financial facts, owner separation, and later professional/implementation decisions.

**Alternatives Considered**

- Universal Bill Evidence was rejected because Tier 1 must permit a Declaration-only Bill path when all other gates pass.
- Economic-Payee identity as the G1 key was rejected in favour of the deliberate receiving-destination simplification.
- Treating Archive as readiness, or allowing Save to imply verification, authorization or Payout readiness, was rejected.
- Invoice-only mandatory Evidence and communication-originated material as mandatory Evidence were rejected.

**Consequences And Handoffs**

DOC-12 governs official Bill Evidence qualification and examples without automatic acceptance; DOC-09/10 preserve Payment/Payout and reconciliation truth; DOC-11 retains Refund/case ownership; DOC-15 governs lawful retention and privacy; DOC-18 represents approved lineage without redefining domain truth; DOC-20–22 retain acceptance, operations and execution-only Admin responsibilities. Derived artifacts remain projections of formal owners.

**Supersedes / Superseded By**

Supersedes active universal-Evidence, stale Active-projection, invoice-only and unqualified-retention implications in the aligned scope. Historical provenance remains non-operative. No accepted formal owner rule is silently replaced outside the approved package.

**Remaining Open Items**

- C1 values, configuration representation and operating change details.
- Category-specific official Bill Evidence lists and acceptance criteria.
- Tier 3 operating roles, workflow and segregation controls.
- Declaration materiality, Tier 2 hold/Refund operation, G1 normalization/concurrency and lawful-scope confirmation.
- Later DOC-17/DOC-19, implementation, professional assessment, UAT, operational and production-readiness evidence.

### `DEC-2026-046` - DOC-19 Mechanism-Neutral Security Control Alignment

| Field | Record |
| --- | --- |
| Date | `2026-08-21` |
| Status | Accepted |
| Primary owner | `DOC-19`, Security Architecture Owner |
| Affected documents | Exactly the 29 paths in substantive commit `860fd78cbb7cc5a080e10334291b60ff8902a77d`: DOC-19 plus the 28 governing, product, domain, technical, acceptance, operations, specialist, diagram, glossary, index and traceability paths listed in the corresponding changelog entry |
| Substantive commit | `860fd78cbb7cc5a080e10334291b60ff8902a77d` |
| Founder approval | Founder authorized DOC-19 Stage 12 Validation, conditional Stage 13 Integration, substantive Commit, required append-only records treatment and exact-branch Push on `2026-08-21` |

**Decision**

PayPlus adopts the reviewed DOC-19 Draft as its mechanism-neutral cross-domain technical security-control contract. DOC-19 owns security invariants, enforcement requirements, prohibited exposure, protected-value and token/reference treatment, session/device assurance, privileged-operation protection, safe telemetry, non-sensitive evidence obligations and verification handoffs. It does not select providers, APIs, schemas, events, protocols, algorithms, keys, credentials, factors, timeouts, rate limits, statuses, routes, permissions, implementation products or final PCI scope.

Owner separation remains mandatory. DOC-06B owns route and recovery behavior; DOC-09 payer authorization and Payment; DOC-10 Payout and reconciliation; DOC-12 Evidence; DOC-14 risk triggers, thresholds, actions and outcomes; DOC-15 privacy, masking, purpose and retention; DOC-16 architecture and the provider-controlled card-data boundary; DOC-17 provider/API/tokenization mechanics; DOC-18 representation; DOC-20 acceptance evidence; DOC-21 operations; DOC-22 owner-permitted execution only; and DOC-99 ISMS policy and assurance evidence.

The 28 aligned consumers now identify DOC-19 as a Stage 9-passed Draft rather than a placeholder, preserve its seven Control Cards, ten acceptance criteria, eight enablement dependencies and seven open questions, and remove active ownership inversions without changing product behavior, routes, statuses, requirements or implementation detail.

**Rationale**

The mechanism-neutral contract makes security enforcement and evidence obligations explicit while preventing security documentation from silently deciding another owner's product, payment, risk, privacy, provider, data, operational, Admin or policy meaning. Provider-controlled card handling, least privilege, non-exposure and owner-first handoffs reduce ambiguity without claiming implementation, operating effectiveness, compliance, certification, provider approval, production readiness or launch readiness.

**Alternatives Considered**

- Leaving DOC-19 as a placeholder was rejected because the reviewed control contract now exists and active consumers must not continue to describe it as absent.
- Assigning provider mechanics, recovery behavior, payer authorization, risk decisions, privacy policy, status/event representation or Admin permissions to DOC-19 was rejected because those concerns retain their established owners.
- Selecting exact security mechanisms or values during Alignment was rejected because DOC-19 is mechanism-neutral and `OQ-19-001` through `OQ-19-007` remain open.
- Treating the Draft or validation evidence as proof of implementation, PCI scope, compliance, certification or readiness was rejected because those outcomes require later implementation, professional assessment and operating evidence.

**Consequences And Handoffs**

DOC-20 and DOC-21 can now trace later acceptance and operational evidence to existing DOC-19 controls without inventing tests, signals or runbooks. DOC-22 remains execution-only. The RTM, OQ register, status matrix, glossary, roadmap, documentation index, specialist guide and Payment Profile diagram are aligned projections, not new source owners. DOC-17, DOC-18, DOC-20, DOC-21, DOC-22 and DOC-99 retain their unresolved owner-first or evidence work.

**Supersedes / Superseded By**

Supersedes active placeholder/future-owner and ownership-inversion wording within the approved 28-path alignment scope. Historical decision records, changelog entries, backups, archived diagrams and task-specific provenance remain unchanged. No accepted product, route, status, payment, risk, privacy, provider, data, operations, Admin or policy definition is superseded.

**Remaining Open Items**

- `OQ-19-001` through `OQ-19-007` and `DEP-19-001` through `DEP-19-008` remain open.
- DOC-17 provider/API contracts, final DOC-18 representation, DOC-20 test/UAT/release evidence, DOC-21 monitoring/runbooks, owner-permitted DOC-22 actions and DOC-99 policy/supplier evidence remain separately gated.
- PCI applicability, scope, shared responsibility and assessment require professional confirmation.
- Implementation, operating-effectiveness, compliance, certification, provider-approval, production-readiness and launch-readiness evidence remain future work.
### `DEC-2026-048` - ENTRANCE-PROMOTION-DETAIL Defined Baseline

| Field | Record |
| --- | --- |
| Date | `2026-08-06` |
| Status | Accepted |
| Primary owner | `DOC-06B` route-level status and UX; `DOC-13` Promotion/Offer source truth; `DOC-22` Feature Management and central Entrance placement workflow |
| Affected documents | `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`, `docs/traceability/route-register.md`, `docs/traceability/payplus-documentation-management-roadmap.md` |
| Substantive commit | `ec9b97bb4cf9b2e5b03992f4a23c546146de97e6` |
| Founder approval | PDM-WI-006 Founder-authorized status-only transition after Stage 9 Review, corrected Align, Stage 12 validation, and Stage 13 Integration on `2026-08-06`; Commit, Record, and Push authorized |

**Decision-Record Correction / Provenance**

At main-integration time, the locked live `main` registry already owned `DEC-2026-041` for Workflow Draft Review Handoff And Review Convergence. The previously unmerged Entrance branch-local use of `DEC-2026-041` therefore collided with that canonical record. `DEC-2026-048` is the canonical replacement ID for this Entrance decision; the former branch-local label remains preserved only through Git history and this correction provenance. The Entrance substantive commit and accepted route-status decision remain `ec9b97bb4cf9b2e5b03992f4a23c546146de97e6`; this record-only correction does not alter Entrance route behavior.

The source branch's 74/69/5 inventory remains historical evidence for that original three-file change. The current main roadmap follows the canonical Route Register's 68 physical records: 61 Defined baseline, 4 Partially defined, and 3 Superseded route-family records. This integration alignment changes no route state other than the accepted `ENTRANCE-PROMOTION-DETAIL` transition.

**Decision**

The Founder-authorized status transition upgrades `ENTRANCE-PROMOTION-DETAIL` from `Partially defined` to `Defined baseline`. Its human-readable route behavior is decision-complete enough for continued alignment; final visual design and technical specification remain open and non-blocking under their formal owners.

The accepted meaning carried by this status baseline remains unchanged: Entrance supports `Promotion` and `Feature` only; `Announcement` is excluded; an Offer-owned source may be referenced beneath Promotion without creating an Offer Entrance class; and `ENTRANCE-ROOT` remains Defined while `ENTRANCE-CAROUSEL` remains a component. The accepted Carousel and detail contracts remain the image-first 4:5 presentation, five-second Crossfade, dots, swipe/tap separation, first-use cue, deterministic priority/manual sequence, Back-only navigation, same-item return, optional source-approved action, and inline Terms. Central placement retains timing, sequence, Feature Management, source-change suspension, preview, publication, and removal responsibility without taking source truth. Promotion placement uses `Use Promotion Period` when checked and read-only manual dates, or separate manual placement dates when unchecked; Feature placement always uses manual dates. Placement allows up to five active items, at most one priority item first, deterministic manual ordering for the remainder, and no random ordering. Feature Management remains an independent source area with a formal product/business-truth owner, while central Entrance placement owns common placement configuration. Withdrawn, prohibited, unauthorized, or materially changed source content is suspended from active presentation while its source and historical evidence are preserved, and restoration requires updated preview and republication.

The synchronized route inventory is 74 registered destinations, 69 Defined baseline destinations, and 5 Partially defined destinations: `HOME-ROOT`, `BILLS-LINKING`, `SUPPORT-ROOT`, `ABOUT-ROOT`, and `TERMS-ROOT`. No other route or document status changed.

**Rationale**

The reviewed route contract satisfies the Product Destination Register criterion for Defined baseline while clearly preserving downstream work. The status-only alignment keeps route presentation, Promotion/Offer truth, Feature truth, and Admin placement responsibilities separate and does not add product behavior, technical implementation, or ownership meaning.

**Consequences And Handoffs**

`OQ-06B-012` remains open and explicitly non-blocking. `OQ-XDOC-011` remains open and unchanged. DOC-07 retains exact Copy, CTA, disclosure, localization, accessibility expression, and presentation; Design and platform owners retain responsive, motion, and visual validation work; technical owners retain scheduling, synchronization, source-change detection, permissions, schemas, events, audit, monitoring, security, and implementation; DOC-20 retains testing, UAT, acceptance, and release evidence; and later DOC-22 work retains operational and technical detail. The separate pre-existing PDM-WI-002 roadmap-maintenance debt remains untouched.

**Supersedes / Superseded By**

Supersedes the active status references that treated `ENTRANCE-PROMOTION-DETAIL` as `Partially defined`. DEC-2026-040, changelog history, decision-log history, and historical DOC-06B revision rows remain preserved; no append-only historical record was rewritten.

**Remaining Open Items**

- Exact DOC-07 Copy, CTA labels, disclosure, localization, accessibility expression, and presentation.
- Responsive measurements, short-viewport treatment, reduced-motion implementation, gesture thresholds, first-use-cue persistence, animation, and visual validation.
- Technical date/time storage, scheduling, synchronization, source-change detection, permissions, schemas, events, audit, monitoring, security, and platform implementation.
- DOC-20 testing, UAT, acceptance, and release evidence, plus later DOC-22 operational and technical workflow detail.

### `Not applicable` - BTPR R2 Documentation Integration Record

| Field | Record |
| --- | --- |
| Date | `2026-08-23` |
| Status | Not applicable — post-commit provenance only; no new product or governance decision |
| Primary owner | Existing `FD-BTPR-01` owners: `DOC-05`, `DOC-06B`, `DOC-06C`, `DOC-07`, `DOC-09`, and `DOC-10` |
| Affected documents | The exact 15 paths in substantive commit `7664d339e45c6e183cb8d6a2b0b107a405200749` |
| Substantive commit | `7664d339e45c6e183cb8d6a2b0b107a405200749` |
| Founder approval | Existing `FD-BTPR-01` acceptance and Founder-authorized BTPR R2 Stage 14–19 sequence on `2026-08-23` |

**Record**

This record binds the already accepted `FD-BTPR-01` documentation contract to its substantive commit. It does not add, modify, or approve a product or governance decision. Formal source documents remain authoritative for the integrated current-context presentation, return, Payment, Evidence, Payout, Declaration, Rent, notification, and owner-boundary treatment.

**Rationale**

The required records-only follow-up provides accurate post-commit provenance using the actual substantive hash while preserving the Founder-approved source boundary.

**Alternatives Considered**

- Minting a new product or governance decision for this records-only entry was rejected because no such decision was authorized.
- Omitting the decision-log record was rejected because the workflow requires an explicit `Not applicable` result when a substantive commit implements already accepted material without a new decision record.

**Consequences And Handoffs**

All existing source owners and deferred dependencies remain unchanged. `ALIGN-BTPR-001` remains pre-existing DOC-11 historical-table debt and is not a BTPR semantic defect.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Existing deferred owner dependencies remain unchanged; no implementation, compliance, certification, provider approval, production-readiness, or launch-readiness claim is created by this record.

### `DEC-2026-049` - DOC-17 Provider-Neutral External Interaction Contract

| Field | Record |
| --- | --- |
| Date | `2026-08-25` |
| Status | Accepted |
| Primary owner | `DOC-17`, Engineering / Integration |
| Affected documents | The exact 11 paths in substantive commit `339bd8c8dfccf60ab102aa706f04135c9aab9e36` |
| Substantive commit | `339bd8c8dfccf60ab102aa706f04135c9aab9e36` |
| Founder approval | Founder approved `DOC17-FD-01` through `DOC17-FD-08` as one coherent provider-neutral direction and authorized the chained Stage 12–19 sequence on `2026-08-25` |

**Decision**

PayPlus adopts the reviewed DOC-17 Draft as its provider-neutral External Interaction Contract. DOC-17 owns the contract, Functional-Surface Coverage, interaction-evidence obligations, candidate-evidence method, uncertainty treatment, replacement/exit evidence, and owner handoffs. An External Observation is not authoritative PayPlus truth by itself and cannot independently establish Payment, Payout, Evidence acceptance, risk outcome, payer authorization, notification decision, case consequence, privacy treatment, or privileged effect.

The contract must consume and must not weaken applicable Bill/Rent, Payment, Payout, Evidence, risk, privacy, notification, architecture, representation, security, acceptance, operations, and Admin-owner rules. Duplicate, replayed, late, missing, stale, malformed, contradictory, unknown-origin, and unavailable observations remain visible without creating a second domain, financial, notification, or privileged consequence. Candidate-specific gaps do not block the generic provider-neutral contract but continue to block candidate-specific feasibility, recommendation, selection, mapping, implementation, testing, acceptance, enablement, assurance, and launch conclusions.

Provider selection and provider-specific realisation remain separately gated. DOC-16 retains architecture, reliability, recovery, and reconciliation posture; DOC-18 retains data/event/correlation/audit/lineage representation; DOC-19 retains mechanism-neutral security treatment; DOC-20 and DOC-21 retain acceptance and operational evidence; DOC-22 remains owner-permitted execution only; and future Engineering work may map an accepted contract only after the applicable decisions. DOC-17 selects no provider, API, backend, adapter, schema, event, status, credential, language, framework, security mechanism, implementation, assurance, enablement, or launch model.

**Rationale**

A single provider-neutral contract makes the complete external-interaction universe reviewable while preventing candidate facts or transport observations from becoming product/domain truth. Functional-Surface Coverage and the Extension Rule prevent omissions and silent externalisation, while explicit owner handoffs preserve current PayPlus authority and future technical optionality.

**Alternatives Considered**

- A candidate-first contract was rejected because incomplete or provider-specific evidence cannot define generic PayPlus requirements or establish capability/readiness.
- A principles-only placeholder was rejected because it would not provide reviewable requirements, complete functional coverage, uncertainty treatment, acceptance traceability, or replacement/exit obligations.
- Multiple competing provider or profile documents were rejected in favour of one DOC-17 contract with internal provider-neutral interaction profiles and one primary owner.
- Defining provider APIs, backend/adapters, schemas/events/statuses, security mechanisms, or implementation during this decision was rejected because those matters remain with later separately authorized owners and gates.

**Consequences And Handoffs**

DOC-09 retains Payment, payer authorization, Provider Confirmation acceptance, Payment, and Payment Application meaning. DOC-10 retains Settlement, Payout, and reconciliation; DOC-11 case and financial-adjustment consequences; DOC-12 applicable Evidence/document verification; DOC-14 risk; DOC-15 privacy/vendor/retention; DOC-16 architecture; DOC-18 representation; DOC-19 security; DOC-20 acceptance; DOC-21 operations; and DOC-22 owner-permitted execution. AGENTS, the documentation index, glossary, OQ register, roadmap, RTM, and the bounded DOC-09/20/21/22 handoffs are aligned projections, not new source owners.

**Supersedes / Superseded By**

Supersedes active DOC-17 placeholder, future-owner, missing-acceptance, and representation-ownership wording within the exact aligned scope. Historical changelog/decision entries, backups, AI contexts, task snapshots, and prior protected-scope statements remain append-only or non-authoritative provenance and are not rewritten as current authority.

**Remaining Open Items**

- Formal DOC-17 reviewer and approver assignments remain `TBD`.
- Provider selection, commercial terms, provider capability/environment evidence, exact API/file/callback/report/portal/payload contracts, backend/adapters, representation, security mechanisms, professional determinations, implementation, testing, monitoring, acceptance, enablement, assurance, and launch remain separately gated.
- Candidate-specific feasibility and evidence gaps remain unresolved at their applicable gates.
- External authorized AI remains a future Founder decision. Future Backend Capability or Engineering Handoff material remains future Explore input only.

### Not applicable - DOC-18 Business-Recording Boundary Alignment

| Field | Record |
| --- | --- |
| Date | 2026-08-27 |
| Status | Not applicable — post-commit provenance only; no new product or governance decision |
| Primary owner | DOC-18, Engineering / Data; all existing formal domain owners retain their authority |
| Affected documents | The exact 27 paths in substantive commit 4464a82dbccc96116762f3877eae72990d790501 |
| Substantive commit | 4464a82dbccc96116762f3877eae72990d790501 |
| Founder approval | Founder-authorized DOC-18 Stage 14–19 Commit, Record, Push, and canonical-main integration sequence on 2026-08-27 |

**Record**

This record binds the already accepted DOC-18 business-recording and explainability boundary to substantive commit 4464a82dbccc96116762f3877eae72990d790501. It does not add, modify, or approve a product, governance, owner, technical, provider, security, implementation, assurance, enablement, or launch decision.

**Rationale**

The required records-only follow-up preserves accurate post-commit provenance and the exact delivered scope without inventing a new decision. DOC-18 remains limited to business recording and explainability; technical representation remains separately authorized.

**Alternatives Considered**

- Minting a new decision identifier was rejected because the substantive commit implements already accepted DOC-18 alignment and no new product or governance decision was authorized.
- Omitting this record was rejected because the Workflow requires an explicit Not applicable result when a substantive commit delivers accepted work without a new decision record.

**Consequences And Handoffs**

Existing owners retain their scopes: Payment and payer authorization; Payout and reconciliation; Evidence; Risk; Privacy; Security; provider interaction; acceptance; operations; and owner-permitted Admin execution. The 30 future Engineering Specification Explore inputs, 8 compatible items, and 1 provenance-only item remain unchanged and do not authorize technical design.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Engineering Specification ownership and technical representation remain future separately authorized Explore work.
- Provider-specific capability and contracts, privacy/access/retention treatment, security mechanisms, Declaration and Category-specific Evidence treatment, Admin mechanics, testing, UAT, operations, implementation, professional assessment, enablement, and launch evidence remain separately gated.

### Not applicable - Engineering Specification Family Integration Record

| Field | Record |
| --- | --- |
| Date | 2026-08-30 |
| Status | Not applicable — post-commit provenance only; no new product or governance decision |
| Primary owner | `DOC-23` Engineering Core; `DOC-24` and `DOC-25` are bounded Engineering Specifications that consume accepted owner inputs |
| Affected documents | The exact nine paths in substantive commit `10dd64508a3c3161eaa1d4494c22c98704f43d90` |
| Substantive commit | `10dd64508a3c3161eaa1d4494c22c98704f43d90` |
| Founder authorization | User-authorized Stage 13, substantive commit, records-only follow-up, and canonical-main push chain on 2026-08-30 |

**Record**

This record binds the already accepted Engineering Specification Family documentation to substantive commit `10dd64508a3c3161eaa1d4494c22c98704f43d90`. It does not add, modify, or approve a product, governance, owner, provider, technical-representation, security-mechanism, implementation, acceptance, enablement, or launch decision.

**Rationale**

The required records-only follow-up preserves the actual substantive commit identity and delivered nine-path scope. `DOC-23` remains the Engineering Core; `DOC-24` and `DOC-25` remain bounded Engineering Specifications, and accepted source owners retain their authority.

**Alternatives Considered**

- Minting a new decision identifier was rejected because the substantive commit implements already accepted Engineering Specification Family work and no new product or governance decision was authorized.
- Omitting this record was rejected because the Documentation Development Workflow requires the immediate decision-log provenance treatment for every substantive documentation commit.

**Consequences And Handoffs**

The registry, routing, index, traceability, and `DOC-18` handoff projections are aligned to the reviewed family. Product, domain, provider, representation, security, acceptance, operations, Admin, and AI build-execution owners remain unchanged; the record selects no provider, API, schema, event taxonomy, security mechanism, implementation, acceptance, enablement, or launch outcome.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Provider/API and bank detail, technical representation/schema/event taxonomy, security mechanisms, implementation, testing/acceptance, operations, enablement, launch, and AI build-execution conversion remain separately gated with their applicable owners.

### Not applicable - DOC-10, DOC-12, And DOC-14 Technical Allocation Reconciliation

| Field | Record |
| --- | --- |
| Date | `2026-09-01` |
| Status | Not applicable - post-commit provenance only; no new product, governance, owner, or technical decision |
| Primary owner | `DOC-10` Payments / Finance; `DOC-12` Product / Risk; `DOC-14` Risk / Compliance |
| Affected documents | The exact three paths in substantive commit `f33e3cf88e57bb22c3269d50a9fdc34258b12049` |
| Substantive commit | `f33e3cf88e57bb22c3269d50a9fdc34258b12049` |
| Founder authorization | User-authorized Stage 12, Stage 13, substantive commit, records-only follow-up, branch push, and canonical-main integration chain on `2026-09-01` |

**Record**

This record binds the already accepted `DOC-10`, `DOC-12`, and `DOC-14` technical-allocation corrections to substantive commit `f33e3cf88e57bb22c3269d50a9fdc34258b12049`. It does not add, modify, or approve a product, governance, owner, technical-representation, provider, security-mechanism, implementation, acceptance, enablement, or launch decision.

**Rationale**

The records-only follow-up preserves the exact delivered source identities and commit provenance while retaining each formal source owner's meaning. `DOC-18` remains limited to its reviewed business-recording and explainability contract; exact technical representation remains separately authorized without a selected owner.

**Alternatives Considered**

- Minting a new decision identifier was rejected because the substantive commit publishes already accepted source-owner boundary corrections and introduces no new product, governance, owner, or technical decision.
- Omitting the record was rejected because the Documentation Development Workflow requires explicit decision-log treatment for every substantive documentation commit.

**Consequences And Handoffs**

`DOC-10` retains Settlement, Payout, Finance, and reconciliation ownership; `DOC-12` retains Evidence, OCR, validation, matching, and duplicate policy; and `DOC-14` retains AML, anti-cashout, fraud, risk, and control meaning. Existing `DOC-09` and `DOC-13` technical-allocation clauses remain protected future Explore inputs. No technical owner, `DOC-26`, shared Engineering Specification, schema, data model, event taxonomy, reason-code model, API, provider, algorithm, persistence, security mechanism, implementation, acceptance, enablement, or launch outcome is selected.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Existing `DOC-09` and `DOC-13` technical-allocation clauses require their own future owner-led Explore before any Proposal or edit.
- Exact technical representation and all provider, mechanism, implementation, acceptance, enablement, and launch detail remain separately gated with their applicable owners.

### Not applicable - DOC-09 Technical Allocation Reconciliation

| Field | Record |
| --- | --- |
| Date | `2026-09-01` |
| Status | Not applicable - post-commit provenance only; no new product, governance, owner, or technical decision |
| Primary owner | `DOC-09` Payments / Product |
| Affected documents | `docs/02-payment-domain/doc-09-payment-domain-architecture.md` |
| Substantive commit | `c11fa2e3a4807b1c601fc20d1052ff84bcf48263` |
| Founder authorization | User-authorized Stage 9 review, Stage 10 Manifest, conditional Stage 11 Alignment, Stage 12 validation, Stage 13 integration, substantive commit, records-only follow-up, branch push, and canonical-main integration chain on `2026-09-01` |

**Record**

This record binds the already accepted `DOC-09` technical-allocation correction to substantive commit `c11fa2e3a4807b1c601fc20d1052ff84bcf48263`. It does not add, modify, or approve a product, governance, owner, technical-representation, provider, security-mechanism, implementation, acceptance, enablement, or launch decision.

**Rationale**

The records-only follow-up preserves the exact delivered DOC-09 identity and commit provenance while retaining Payment, replay, Payment Application, G1, Evidence/Rent, Payout, external-observation, risk, privacy, security, and formal owner boundaries. Exact technical representation remains separately authorized without a selected recipient.

**Alternatives Considered**

- Minting a new decision identifier was rejected because the substantive commit publishes an already accepted source-owner boundary correction and introduces no new product, governance, owner, or technical decision.
- Omitting the record was rejected because the Documentation Development Workflow requires explicit decision-log treatment for every substantive documentation commit.

**Consequences And Handoffs**

`DOC-09` retains payer authorization, Funding Leg, immutable Payment, replay, Payment Application, G1 consumption, and financial non-rewrite meaning. Existing downstream owner contracts remain unchanged. The Stage 10 Manifest required no alignment edit; protected `DOC-13` and broader pre-existing technical-representation allocations remain future owner-specific Explore inputs rather than being silently treated as aligned.

**Supersedes / Superseded By**

None.

**Remaining Open Items**

- Protected `DOC-13` and broader pre-existing technical-representation allocations require their own owner-led Explore and Proposal authority before any correction.
- Exact schema, event/state model, persistence, correlation/idempotency mechanism, API, provider, algorithm, implementation, acceptance, operations, enablement, and launch detail remain separately gated without a selected technical owner.

### Not applicable - DOC-13 Technical Allocation Reconciliation

| Field | Record |
| --- | --- |
| Date | `2026-09-01` |
| Status | Not applicable - post-commit provenance only; no new product, governance, owner, or technical decision |
| Primary owner | `DOC-13` Growth / Product |
| Affected documents | `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`; `docs/01-product/doc-08-notification-receipt-communication-spec.md`; `docs/04-growth-ecosystem/doc-13-promotion-engine-coupon-voucher-referral-membership-spec.md` |
| Substantive commit | `c8b6a8d55039e6bfe9a8773e7253db073753cf13` |
| Founder authorization | User-authorized Stage 10 Manifest, conditional Stage 11 Alignment, Stage 12 validation, Stage 13 integration, substantive commit, records-only follow-up, non-force branch push, and fast-forward canonical-main integration chain on `2026-09-01` |

**Record**

This record binds the already accepted DOC-13 technical-allocation correction and its two exact downstream owner-boundary alignments to substantive commit `c8b6a8d55039e6bfe9a8773e7253db073753cf13`. It does not add, modify, or approve a product, governance, owner, technical-representation, provider, security-mechanism, implementation, acceptance, enablement, or launch decision.

**Rationale**

The records-only follow-up preserves the exact delivered DOC-13, DOC-06B, and DOC-08 identities and commit provenance while retaining DOC-13 promotion/commercial truth, DOC-06B route presentation, DOC-08 notification policy, DOC-22 owner-permitted execution, and DOC-18's reviewed business-recording boundary. Exact technical representation remains separately authorized without a selected recipient.

**Alternatives Considered**

- Minting a new decision identifier was rejected because the substantive commit publishes an already accepted source-owner boundary correction and introduces no new product, governance, owner, or technical decision.
- Omitting the two downstream alignment clauses was rejected because their active schema/event allocations would have contradicted the reviewed DOC-13/DOC-18 owner boundary.
- Omitting this record was rejected because the Documentation Development Workflow requires explicit decision-log treatment for every substantive documentation commit.

**Consequences And Handoffs**

DOC-13 retains campaign, Offer, eligibility, qualification, entitlement, benefit, quote, reservation, budget, quota, stacking, funding, reversal, fulfilment, referral, membership, reward, and promotion-commercial meaning. DOC-06B retains route and presentation ownership; DOC-08 retains notification identity, eligibility, recipient, channel, template, preference, delivery, and retry ownership; DOC-18 retains business-recording, explainability, history, lineage, audit-meaning, reporting-obligation, and owner-handoff obligations only. No technical owner, shared specification, schema, event taxonomy, API, provider, persistence, model representation, security mechanism, implementation, acceptance, enablement, or launch outcome is selected.

**Supersedes / Superseded By**

No decision record is superseded. The substantive commit replaces only the active legacy technical-allocation wording in the three affected documents; append-only historical records remain provenance.

**Remaining Open Items**

- Provider/API/file/webhook capability, exact technical representation, schema, event/state taxonomy, identifiers, persistence, analytics/model representation, security mechanisms, implementation, acceptance, operations, enablement, and launch remain separately gated with their applicable owners.
- Broader pre-existing technical-allocation wording outside the DOC-13 promotion, notification, and route-handoff boundary remains future owner-specific Explore input and was not widened into this change.
