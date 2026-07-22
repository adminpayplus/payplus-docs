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
