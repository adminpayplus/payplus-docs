# PayPlus Current Mobile Prototype

| Field | Value |
| --- | --- |
| Purpose | Rebuild the PayPlus mobile prototype from the current repository route definitions rather than the legacy prototype. |
| Classification | Route-flow, interaction, information-architecture, responsive, and exploratory visual-design prototype. |
| Status | Review Draft / Archive-family alignment required |
| Source baseline | Current working tree reviewed on 2026-07-26, including the DOC-06 family, route register, status-display matrix, and route map. An immutable source commit must be recorded before this prototype can become a Validated Reference. |
| Visual direction | Adapted from the founder-approved AUREX reference: premium light fintech hierarchy without banking-balance, wallet, deposit, or open-transfer behavior. |
| Last verified | 2026-07-26 |

## Primary Sources

- `AGENTS.md`
- `docs/documentation-system/payplus-prototype-design-validation-specialist-guide.md`
- `docs/01-product/doc-05-master-prd-feature-requirement-index.md`
- `docs/01-product/doc-06-user-journey-ux-flow-service-blueprint.md`
- `docs/01-product/doc-06a-core-user-journeys-service-blueprint.md`
- `docs/01-product/doc-06b-navigation-ia-route-taxonomy.md`
- `docs/01-product/doc-06c-bills-rent-tenancy-ux-module.md`
- `docs/01-product/doc-06d-ux-requirements-acceptance-test-matrix.md`
- `docs/diagrams/README.md`
- `docs/diagrams/routes/payplus-app-route-map.md`
- applicable route-family maps under `docs/diagrams/routes/`
- `docs/traceability/route-register.md`
- `docs/traceability/status-display-reference-matrix.md`

## Represented Route Families

- Home, five-item bottom navigation, eight shortcuts, notices, Featured, Upcoming Bills/Rent, and Recent Activity.
- Pay+ action sheet.
- Bills To Pay/To Receive, bill/rent detail, scoped activity, evidence detail/update, reminder detail, and Add Bill/Rent.
- Requests root/detail/new.
- Payment Instructions root/detail.
- Payment Profile Cards/Profiles with add and detail screens.
- Reminders, account Activity, and receipt/statement preview destinations.
- Offers with three child lists and offer detail, My Rewards and reward detail, plus Referral reward-list, entitlement, and claim destinations.
- `ME-ROOT`, `ACCOUNT-PROFILE`, `IDENTITY-VERIFICATION`, `ACCOUNT-SECURITY`, `PAYMENT-PASSCODE-SETTINGS`, `PRIVACY-DATA-CONTROLS`, `RECEIVING-INFO`, `RECEIVING-INFO-LIST`, `RECEIVING-INFO-DETAILS`, `RECEIVING-INFO-SETUP`, `NOTIFICATION-SETTINGS`, `SUPPORT-ROOT`, `ABOUT-ROOT`, and `TERMS-ROOT`.
- The current `ARCHIVED-ROOT`, `ARCHIVED-BILLS-LIST`, and `ARCHIVED-DOCS-LIST` behavior is not yet represented and must be aligned before this prototype can be treated as current.
- More/shortcut-management review screen.

## Review Scenarios

1. Start on Home and test all five bottom destinations and all eight shortcuts.
2. Open Pay+ and verify that its five actions enter controlled evidence-backed flows.
3. Switch Bills between To Pay and To Receive and compare role-aware actions.
4. Review Bill/Rent detail and its scoped Activity, Rental Doc, and Reminder destinations.
5. Review Requests, Instructions, Payment Profile, Activity, and Receipts.
6. Review Offers, My Rewards, and Referral as separate route owners.
7. Open Referral from the dashboard shortcut, Offers, and Me.
8. Open Receiving Info from Me, review the masked list/detail, and open the setup flow.
9. Open Me and review every defined account, security, privacy, records, rewards, preference, support, and legal destination.
10. Test Back, modal Close, bottom navigation, toggles, and mock download actions.

## Boundaries

- All data is fictional.
- External PSP, KYC/KYB, OCR, risk, notification, payout, promotion, PDF, and backend behavior is simulated.
- Final visual design, copy, detailed pending child routes, and production checkout remain open where the source documents say they are open.
- The prototype does not create a wallet, stored value, cashout, remittance, lending, unrestricted P2P, or an open request marketplace.
- Product discoveries must return to the owning document before being treated as accepted requirements.
- This Review Draft has not completed commit-based source validation and must not be treated as a Validated Reference.
