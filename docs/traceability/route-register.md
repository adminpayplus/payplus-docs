# Product Destination Register

Status: Working alignment reference
Owner: Product / Founder
Last updated: 2026-07-26
Classification: Internal

This register is the canonical inventory of PayPlus product destinations. Owning documents define behavior; this register tracks identity, parentage, type, ownership, and definition status without restating detailed requirements.

## Status Definitions

| Status | Meaning |
| --- | --- |
| Defined baseline | Human-readable route behavior is decision-complete enough for continued alignment; final visual design or technical specification may remain open. |
| Partially defined | Purpose and some behavior exist, but material route behavior remains open. |
| ID or route open | The product area exists, but its stable destination ID or route behavior is not yet defined. |

## Destination Inventory

| Destination | Parent | Type | Purpose | Primary Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `AUTH-ENTRY` | App launch / logout | Unauthenticated root screen | Provide the pre-login choice to Log In or Register. | DOC-06B | Partially defined |
| `AUTH-LOGIN` | `AUTH-ENTRY` / protected deeplink | Child authentication flow | Authenticate an existing user and establish an approved session. | DOC-06B / DOC-19 | Partially defined |
| `AUTH-REGISTRATION` | `AUTH-ENTRY` / referral or approved deeplink | Child registration/onboarding flow | Create an account and complete required registration gates. | DOC-06B / DOC-15 | Partially defined |
| `HOME-ROOT` | Successful authentication / bottom navigation: Home | Root screen | Open the task-first logged-in dashboard. | DOC-06B | Partially defined |
| `PAYPLUS-ACTION-SHEET` | Bottom navigation: Pay+ | Sheet / modal | Start or continue approved PayPlus payment, setup, instruction, or request journeys. | DOC-06B | Partially defined |
| `MORE-ROOT` | Dashboard shortcut: More | Root screen | Manage dashboard shortcuts and access approved secondary services. | DOC-06B | Partially defined |
| `NOTIFICATION-INBOX` | Home header / approved notification context | Utility route | List notification-backed messages, announcements, support replies, and action items. | DOC-06B / DOC-08 | Partially defined |
| `PAYMENT-CHECKOUT` | Bills, Instructions, Requests, or approved payment entry | Flow / screen group | Review payment method, eligible benefits, quote, authorization, and submission. | DOC-09 | Partially defined |
| `BILLS-ROOT` | Bottom navigation: Bills | Root screen | Open the Bills area and its payer/payee views. | DOC-06C | Defined baseline |
| `BILLS-PAY` | `BILLS-ROOT` | Tab / view | Manage obligations the user needs or expects to pay. | DOC-06C | Defined baseline |
| `BILLS-RECEIVE` | `BILLS-ROOT` | Tab / view | Manage payee-created obligations and requests the user expects to receive. | DOC-06C | Defined baseline |
| `BILLS-DETAIL-BILL` | `BILLS-PAY` / `BILLS-RECEIVE` | Child screen | View one bill/fee obligation with role-aware actions. | DOC-06C | Defined baseline |
| `BILLS-DETAIL-RENT` | `BILLS-PAY` / `BILLS-RECEIVE` | Child screen | View one rent/tenancy obligation with role-aware actions. | DOC-06C | Defined baseline |
| `BILLS-ADD` | Bills / Pay+ / Requests | Flow / screen group | Create an evidence-backed bill, fee, rent, or tenancy obligation. | DOC-06C | Defined baseline |
| `BILLS-ACTIVITY` | Bill/rent detail | Child screen | Show payment-related transaction activity for one obligation. | DOC-06C | Defined baseline |
| `BILLS-ACTIVITY-DETAIL` | `BILLS-ACTIVITY` | Child screen | Show one contextual payment-activity entry and permitted files. | DOC-06C | Defined baseline |
| `BILLS-EVIDENCE-DETAIL` | Bill/rent detail | Child screen / sheet | View and manage the active evidence set for one obligation. | DOC-06C | Defined baseline |
| `BILLS-EVIDENCE-UPLOAD` | `BILLS-EVIDENCE-DETAIL` / `BILLS-ADD` | Flow / screen group | Upload, capture, classify, review, and submit evidence. | DOC-06C | Defined baseline |
| `BILLS-REMINDER-LIST` | Dashboard shortcut / Bills | Child screen | Manage reminders linked to obligations. | DOC-06C | Defined baseline |
| `BILLS-REMINDER-DETAIL` | Reminder list / bill/rent context | Child screen / sheet | Create or edit one linked reminder. | DOC-06C | Defined baseline |
| `BILLS-LINKING` | Bill/rent/request context | Flow / sheet | Support user-initiated participant linking without auto-matching. | DOC-06C | Partially defined |
| `REQUESTS-ROOT` | Dashboard shortcut / Me | Root screen | List and manage received, sent, and archived requests. | DOC-06B | Defined baseline |
| `REQUESTS-DETAIL` | `REQUESTS-ROOT` / notification / deeplink | Child screen | Review and act on one request while preserving linked-context handoffs. | DOC-06B | Defined baseline |
| `REQUESTS-NEW` | Requests / Pay+ / bill/rent context | Child flow | Create and send one controlled evidence-backed request. | DOC-06B | Defined baseline |
| `INSTRUCTIONS-ROOT` | Dashboard shortcut / Pay+ | Root screen | List pending pay-later and incomplete payment instructions. | DOC-06B | Defined baseline |
| `INSTRUCTIONS-DETAIL` | `INSTRUCTIONS-ROOT` / alert | Child screen | View and act on one pending or incomplete instruction. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-ROOT` | Dashboard shortcut / Me / checkout / instruction | Root route family | Manage tokenized cards and saved split-card profiles. | DOC-06B | Defined baseline |
| `PAYMENT-CARD-LIST` | `PAYMENT-PROFILE-ROOT` Cards tab | Initial screen / tab content | List and manage tokenized cards. | DOC-06B | Defined baseline |
| `PAYMENT-CARD-ADD` | `PAYMENT-CARD-LIST` | Child flow | Add and tokenize a card through the selected PSP flow. | DOC-06B | Defined baseline |
| `PAYMENT-CARD-DETAIL` | `PAYMENT-CARD-LIST` | Child screen | View and manage one tokenized card's permitted metadata. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-LIST` | `PAYMENT-PROFILE-ROOT` Profiles tab | Initial screen / tab content | List saved split-card profiles. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-ADD` | `PAYMENT-PROFILE-LIST` | Child flow | Create a split-card profile of up to 6 cards. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-DETAIL` | `PAYMENT-PROFILE-LIST` | Child screen | View or edit one saved split-card profile. | DOC-06B | Defined baseline |
| `ACTIVITY-ROOT` | Dashboard Recent Activity / Me | Root screen | Show mixed-role account financial activity. | DOC-06B | Defined baseline |
| `ACTIVITY-DETAIL` | `ACTIVITY-ROOT` / notification | Child screen | Show one account-level transaction lifecycle and permitted handoffs/files. | DOC-06B | Defined baseline |
| `RECEIPTS-ROOT` | Dashboard shortcut / Me | Root screen | Search, preview, and download receipts and statements. | DOC-06B | Defined baseline |
| `RECEIPT-DETAIL` | `RECEIPTS-ROOT` / notification | Child PDF preview | Preview one receipt with close/back and download. | DOC-06B | Defined baseline |
| `STATEMENT-DETAIL` | `RECEIPTS-ROOT` / notification | Child PDF preview | Preview one statement with close/back and download. | DOC-06B | Defined baseline |
| `OFFERS-ROOT` | Bottom navigation: Offers / dashboard | Root screen | Discover Featured, Card, Pay+, and Partner offers. | DOC-06B | Defined baseline |
| `OFFERS-CARD-LIST` | `OFFERS-ROOT` | Child collection screen | View all Card Offers. | DOC-06B | Defined baseline |
| `OFFERS-PAYPLUS-LIST` | `OFFERS-ROOT` | Child collection screen | View all Pay+ Offers. | DOC-06B | Defined baseline |
| `OFFERS-PARTNER-LIST` | `OFFERS-ROOT` | Child collection screen | View all Partner Offers. | DOC-06B | Defined baseline |
| `OFFER-DETAIL` | Offers surfaces / deeplink | Full-screen detail | Show one offer's full conditions and permitted action. | DOC-06B | Defined baseline |
| `REWARDS-ROOT` | Offers / dashboard utility / Me / Referral | Root screen | Manage issued rewards through Active and History views. | DOC-06B | Defined baseline |
| `REWARD-DETAIL` | `REWARDS-ROOT` / checkout context | Full-screen detail | Show full reward details, terms, status, and permitted action. | DOC-06B | Defined baseline |
| `REFERRAL-ROOT` | Dashboard shortcut / Offers / Me | Root screen | Share referral entry and show attributed qualification progress. | DOC-06B | Defined baseline |
| `REFERRAL-REWARDS-LIST` | `REFERRAL-ROOT` | Child screen | List role-sensitive referral reward entitlements. | DOC-06B | Defined baseline |
| `REFERRAL-ENTITLEMENT-DETAIL` | Referral reward list | Child screen | Show one referral entitlement and claim eligibility. | DOC-06B | Defined baseline |
| `REFERRAL-REWARD-CLAIM` | Referral entitlement detail | Child confirmation screen | Confirm claim and hand issued reward to My Rewards. | DOC-06B | Defined baseline |
| `ME-ROOT` | Bottom navigation: Me | Root screen | Provide permanent account, security, privacy, records, program, and support access. | DOC-06B | Defined baseline |
| `ACCOUNT-PROFILE` | `ME-ROOT` | Child route | Manage account information, verification handoff, and closure entry. | DOC-06B | Defined baseline |
| `IDENTITY-VERIFICATION` | `ACCOUNT-PROFILE` / approved contexts | Reusable child flow | Submit, continue, retry, or update identity verification. | DOC-06B | Defined baseline |
| `ACCOUNT-SECURITY` | `ME-ROOT` | Child route | Manage password, passcode, 2FA, biometric, devices, and recovery. | DOC-06B | Defined baseline |
| `PAYMENT-PASSCODE-SETTINGS` | `ACCOUNT-SECURITY` | Child screen | Change/reset passcode and manage permitted confirmation preference. | DOC-06B | Defined baseline |
| `PRIVACY-DATA-CONTROLS` | `ME-ROOT` | Child route | Manage optional data-use choices and governed privacy requests. | DOC-06B | Defined baseline |
| `RECEIVING-INFO` | `ME-ROOT` / approved context | Root route family | Manage private reusable receiving-information profiles. | DOC-06B | Defined baseline |
| `RECEIVING-INFO-LIST` | `RECEIVING-INFO` | Initial screen | List saved receiving-information profiles. | DOC-06B | Defined baseline |
| `RECEIVING-INFO-DETAILS` | `RECEIVING-INFO-LIST` | Child screen | View one masked profile and its readiness/actions. | DOC-06B | Defined baseline |
| `RECEIVING-INFO-SETUP` | Receiving Info / request context | Child flow | Add or edit one receiving-information profile. | DOC-06B | Defined baseline |
| `ARCHIVED-ROOT` | `ME-ROOT` | Child root route | Enter Archived Bills & Rent or Archived Documents. | DOC-06B | Defined baseline |
| `ARCHIVED-BILLS-LIST` | `ARCHIVED-ROOT` | Child list screen | Search, filter, and review the user's archived bill/fee and rent obligations, then open archived read-only bill/rent detail. | DOC-06C | Defined baseline |
| `ARCHIVED-DOCS-LIST` | `ARCHIVED-ROOT` | Child list screen | Search, filter, preview, and download permitted archived or previous evidence documents. | DOC-06B | Defined baseline |
| `NOTIFICATION-SETTINGS` | `ME-ROOT` | Child route | Manage permitted communication preferences. | DOC-08 | Partially defined |
| `SUPPORT-ROOT` | `ME-ROOT` / contextual failures | Root route | Access support and issue-specific assistance. | DOC-06B / DOC-21 | Partially defined |
| `ABOUT-ROOT` | `ME-ROOT` | Child route | Show PayPlus product and app information. | DOC-06B | Partially defined |
| `TERMS-ROOT` | `ME-ROOT` | Child route | Access applicable terms and policies. | DOC-06B / DOC-07 | Partially defined |

## Assigned Destinations Requiring Further Definition

All currently identified product areas now have stable destination IDs. `AUTH-ENTRY`, `AUTH-LOGIN`, `AUTH-REGISTRATION`, `HOME-ROOT`, `PAYPLUS-ACTION-SHEET`, `MORE-ROOT`, `NOTIFICATION-INBOX`, and `PAYMENT-CHECKOUT` remain partially defined and must receive detailed route or screen behavior before their applicable acceptance scope is complete. The Archive route family has a defined human-readable behavior baseline; final visual design and technical implementation remain open.

## Maintenance Rules

- Update the owning document first, then this register.
- Do not add cards, filters, tabs, ordinary buttons, events, or status labels as routes.
- When a destination changes, check the DOC-06 parent status, DOC-06D, route Mermaid, requirements traceability, and affected notification/deeplink destinations.
- Unresolved items remain visible; do not invent an ID merely to make the register appear complete.
