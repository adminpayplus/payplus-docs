# Product Destination Register

Status: Working alignment reference
Owner: Product / Founder
Last updated: 2026-11-13
Classification: Internal

This register is the canonical inventory of PayPlus product destinations. Owning documents define behavior; this register tracks identity, parentage, type, ownership, and definition status without restating detailed requirements.

## Status Definitions

| Status | Meaning |
| --- | --- |
| Defined baseline | Human-readable route behavior is decision-complete enough for continued alignment; final visual design or technical specification may remain open. |
| Partially defined | Purpose and some behavior exist, but material route behavior remains open. |
| ID or route open | The product area exists, but its stable destination ID or route behavior is not yet defined. |
| Superseded | Former route identity retained for provenance only; it is not a current runtime destination or deep-link contract. |

## Destination Inventory

| Destination | Parent | Type | Purpose | Primary Owner | Status |
| --- | --- | --- | --- | --- | --- |
| `ENTRANCE-ROOT` | App launch / logout | Unauthenticated root screen | Present public non-personalized content and the Log In / Create Account entry actions. | DOC-06B | Defined baseline |
| `ENTRANCE-PROMOTION-DETAIL` | `ENTRANCE-ROOT` public carousel | Child public detail screen | Show one approved public Promotion or Feature item and an optional permitted action. A Promotion may reference an applicable Offer-owned source, but Offer is not a separate Entrance content class. | DOC-06B | Defined baseline |
| `AUTH-LOGIN` | `ENTRANCE-ROOT` / protected deeplink | Route family / entry resolver | Select Fast Login when eligible; otherwise open Full Login. | DOC-06B | Defined baseline |
| `AUTH-LOGIN-FAST` | `AUTH-LOGIN` | Child authentication screen / sheet | Authenticate an eligible remembered account through its distinct Login PIN or previously enabled biometric behavior, separately from Full Login OTP and Payment Passcode. | DOC-06B | Defined baseline |
| `AUTH-LOGIN-FULL` | `AUTH-LOGIN` / Log In With Another Account | Child authentication screen | Authenticate through Phone/Email destination-specific OTP views and explicitly enabled Google/Apple; neither OTP view requires an account password. | DOC-06B | Defined baseline |
| `AUTH-RECOVERY` | `AUTH-LOGIN-FAST` / `AUTH-LOGIN-FULL` | Reusable child flow | Recover account access through approved self-service, provider, or controlled Support resolution without creating an authenticated session. | DOC-06B | Defined baseline |
| `AUTH-REGISTRATION` | `ENTRANCE-ROOT` / referral or approved deeplink | Child registration/onboarding flow | Complete the shared verified-phone/user-data and required email-proof sequence, mandatory matching Login PIN and explicit Terms/Privacy, then confirmed restricted-account creation under DOC-06B Section 5.0.4. | DOC-06B | Defined baseline |
| `ACCOUNT-ACTIVATION` | Blocked financial action / other permitted activation caller | Orchestration route flow | Coordinate actual missing owner requirements and return after revalidation. New Done/Home identity callers invoke the shared child directly under DOC-06B Section 5.0.5; they do not require the old checklist hop. | DOC-06B | Defined baseline |
| `PHONE-VERIFICATION` | `ACCOUNT-PROFILE` | Reusable child flow | Verify or replace the required Hong Kong primary phone number; may be invoked contextually by `ACCOUNT-ACTIVATION`. | DOC-06B | Defined baseline |
| `HOME-ROOT` | Successful login / bottom navigation: Home | Root screen | Open the Payer task-first dashboard, including current new-user identity/no-source composition and source-derived calendar/label Upcoming views under DOC-06B Sections 5.5/5.8; views create no obligations. | DOC-06B | Partially defined |
| `PAYPLUS-ACTION-SHEET` | Bottom navigation: Pay+ | Sheet / modal | Start approved Bill/Rent payment selection, bill/rent setup, or payment continuation through the four defined actions. | DOC-06B | Defined baseline |
| `MORE-ROOT` | Dashboard shortcut: More | Root screen | Manage up to 7 configurable Home shortcuts plus protected More, restore the current eligible default, and access approved secondary services. | DOC-06B | Defined baseline |
| `NOTIFICATION-ROOT` | Home Inbox / standalone Me Notifications / approved notification context | Parent route shell | Group Inbox, notification detail, and notification settings; generic entry defaults to Inbox. | DOC-06B / DOC-08 | Defined baseline |
| `NOTIFICATION-INBOX` | `NOTIFICATION-ROOT` / Home header | Default child screen | Search/filter and read permitted notification records; individual Read follows successful necessary Detail content. No Inbox Archive/Restore action or Archived filter; current domain actions remain Detail-first and owner-revalidated. | DOC-06B / DOC-08 | Defined baseline |
| `NOTIFICATION-DETAIL` | `NOTIFICATION-INBOX` / approved external notification context | Child screen | Show one permitted message, revalidate current state and action availability, and route only an owner-approved current action to its owning destination. An instruction `Pay Now` action invokes the DOC-09 Checkout Resolver only after this Detail-first treatment. | DOC-06B / DOC-08 | Defined baseline |
| `NOTIFICATION-SETTINGS` | `NOTIFICATION-ROOT` / direct Me entry | Child screen | Manage permitted independent immediate delivery preferences, failed-value restoration and no late expired/superseded effect; preserve actual caller, reciprocal Inbox navigation and separate Privacy consent/device permission. | DOC-06B / DOC-08 | Defined baseline |
| `PAYMENT-CHECKOUT` | Bill/Rent Pay resolver, Instruction `Pay Now` Checkout Resolver, or another owner-approved resume or protected-return context | Flow / screen group | Provide one persistent adaptive Checkout Workspace for eligible New Checkout or valid Resume context, funding, holistic review and authorization, Funding Leg progress, condition-specific results and recovery, and safe return without imposing a fixed wizard or redefining DOC-09 domain meaning. Tier 3 may preserve a prepared but non-executable Workspace before approval. Instruction `Pay Now` follows the decided `OQ-XDOC-007` resolver contract; instruction-related notifications follow the decided `OQ-XDOC-015` `NOTIFICATION-DETAIL`-first contract. | DOC-06B; DOC-09 for domain architecture | Defined baseline |
| `BILLS-ROOT` | Bottom navigation: Bills | Root screen | Open the Bills area and its payer-visible obligation views. | DOC-06C | Defined baseline |
| `BILLS-PAY` | `BILLS-ROOT` | Tab / view | Manage Saved/current Bills and Rent obligations the user needs or expects to pay; Bill payment entry consumes the applicable Tier 1/2/3 and Declaration handoff, while Rent retains mandatory Evidence. | DOC-06C | Defined baseline |
| `BILLS-RECEIVE` | Former Bills Receive view | Retired route family | Retired; no Consumer-Payee or payee-user runtime is current. | DOC-06C | Superseded |
| `BILLS-DETAIL-BILL` | `BILLS-PAY` | Child screen | View the same Bill source and current permitted actions, including source-bound inline Next Payment Reminder shared with applicable results; no separate Bill reminder-management route. | DOC-06C | Defined baseline |
| `BILLS-DETAIL-RENT` | `BILLS-PAY` | Child screen | View one rent/tenancy obligation with permitted payer actions. | DOC-06C | Defined baseline |
| `BILLS-ADD` | Bills / Pay+ | Flow / screen group | Capture a controlled Category-scoped Bill source or the separate Rent/tenancy context; Bill B/D/upfront unselected interval and deliberate review/Save follow DOC-06C. Confirmed new-source Pay and Instruction support returns retain their exact source identity and owner gates. | DOC-06C | Defined baseline |
| `BILLS-ACTIVITY` | Bill/rent detail | Child screen | Show permitted payment-related activity scoped to one Bill/Rent source, distinct from global history/Statistics and Evidence lifecycle. | DOC-06C | Defined baseline |
| `BILLS-ACTIVITY-DETAIL` | `BILLS-ACTIVITY` | Child screen | Show one contextual payment-activity entry and permitted files. | DOC-06C | Defined baseline |
| `BILLS-EVIDENCE-DETAIL` | Bill/rent detail | Child screen / sheet | View and manage the active evidence set for one obligation. | DOC-06C | Defined baseline |
| `BILLS-EVIDENCE-UPLOAD` | `BILLS-EVIDENCE-DETAIL` / `BILLS-ADD` | Flow / screen group | Upload, capture, classify, review, and submit evidence. | DOC-06C | Defined baseline |
| `BILLS-REMINDER-LIST` | Existing permitted Rent reminder entry | Child screen | Retained Rent reminder management only under DOC-06C Section 5.12; Bill reminders are source-bound inline detail/result controls. The existing ID is not globally retired. | DOC-06C | Defined baseline |
| `BILLS-REMINDER-DETAIL` | Retained Rent reminder list / Rent context | Child screen / sheet | Create or edit one retained Rent reminder under its separate policy. Bill inline date/mode controls are not a new destination or this central/manual Bill flow. | DOC-06C | Defined baseline |
| `REQUESTS-*` | Former Requests route family | Retired route family | Retired; retained only in historical or superseded traceability material. | DOC-06A / DOC-06B | Superseded |
| `INSTRUCTIONS-ROOT` | Dashboard shortcut / Pay+ | Root screen | List deliberate pay-later Payment Instructions and incomplete Checkout Workspaces without treating them as the same domain object. | DOC-06B | Defined baseline |
| `INSTRUCTIONS-DETAIL` | `INSTRUCTIONS-ROOT` / Pay+ continuation / approved non-notification source context | Child screen | View and act on one Payment Instruction or one incomplete Checkout Workspace according to its distinct rules. A current Instruction `Pay Now` action invokes the DOC-09 Checkout Resolver without predetermining Checkout identity. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-ROOT` | Dashboard shortcut / Me Payment Methods / Checkout / Instruction support | Root route family | Manage tokenized cards and the shared saved-ratio profile editor; return to the actual caller without submitting or forcing a financial action on ordinary Me management. | DOC-06B | Defined baseline |
| `PAYMENT-CARD-LIST` | `PAYMENT-PROFILE-ROOT` Cards tab | Initial screen / tab content | List and manage tokenized cards. | DOC-06B | Defined baseline |
| `PAYMENT-CARD-ADD` | `PAYMENT-CARD-LIST` | Child flow | Add and tokenize a card through the selected PSP flow. | DOC-06B | Defined baseline |
| `PAYMENT-CARD-DETAIL` | `PAYMENT-CARD-LIST` | Child screen | View and manage one tokenized card's permitted metadata. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-LIST` | `PAYMENT-PROFILE-ROOT` Profiles tab | Initial screen / tab content | List saved split-card profiles. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-ADD` | `PAYMENT-PROFILE-LIST` | Child flow | Create a split-card profile of up to 6 cards. | DOC-06B | Defined baseline |
| `PAYMENT-PROFILE-DETAIL` | `PAYMENT-PROFILE-LIST` | Child screen | View or edit one saved split-card profile. | DOC-06B | Defined baseline |
| `ACTIVITY-ROOT` | Dashboard View More / Me Transaction History / safe owning fallback | Root screen | Show Payer account-level financial history and its global-only recent-spending summary/internal Statistics child view under DOC-06B Section 5.14.3. Statistics is not a new stable route, Statement or ledger. | DOC-06B | Defined baseline |
| `ACTIVITY-DETAIL` | `ACTIVITY-ROOT` / notification | Child screen | Show the shared permitted immutable financial detail with original global/source/Home/notification caller scope; cold entry safely falls back to Activity after revalidation. | DOC-06B | Defined baseline |
| `RECEIPTS-ROOT` | Dashboard shortcut / permitted document contexts | Root screen | Search, render and download actual private receipt/Statement PDFs; Single/Combined membership follows actual eligible confirmed Payments. No unadopted Me Receipts row or general entitlement from the result-artifact exception. | DOC-06B | Defined baseline |
| `RECEIPT-DETAIL` | `RECEIPTS-ROOT` / notification | Child PDF preview | Render the actual permitted private receipt PDF, including its Single/Combined presentation, with close/back to the actual caller and download of that file. | DOC-06B | Defined baseline |
| `STATEMENT-DETAIL` | `RECEIPTS-ROOT` / notification | Child PDF preview | Render the actual permitted period Statement PDF with close/back and file download; spending Statistics is separate. | DOC-06B | Defined baseline |
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
| `ME-ROOT` | Bottom navigation: Me | Root screen | Provide the current navbar-free grouped My Account root, one-open-group/search, standalone Notifications and owned child returns under DOC-06B Section 5.17.2; route existence alone grants no additional Me entry. | DOC-06B | Defined baseline |
| `ACCOUNT-PROFILE` | ME-ROOT / Account & Login | Child route | Manage account information, verification handoff, and closure entry. | DOC-06B | Defined baseline |
| `IDENTITY-VERIFICATION` | `ACCOUNT-PROFILE` | Reusable child flow | Use the existing shared identity flow for permitted first-time/status/retry/owner-required update. Done/Home direct callers and other activation/account callers retain their actual return; canonical parent remains ACCOUNT-PROFILE. | DOC-06B | Defined baseline |
| `ACCOUNT-SECURITY` | ME-ROOT / Account & Login | Child route | Manage separately applicable optional password/provider controls, shared Payment Passcode, permitted 2FA/biometric/device/recovery controls; do not replace Phone/Email OTP Full Login or conflate Login PIN and Payment Passcode. | DOC-06B | Defined baseline |
| `PAYMENT-PASSCODE-SETTINGS` | `ACCOUNT-SECURITY` | Reusable child flow | Set, change, or reset the six-digit payment passcode and manage the permitted confirmation preference; may be invoked in Set mode by `ACCOUNT-ACTIVATION`. | DOC-06B | Defined baseline |
| `PRIVACY-DATA-CONTROLS` | ME-ROOT / Settings & Support | Child route | Manage optional data-use choices and governed privacy requests. | DOC-06B | Defined baseline |
| `RECEIVING-INFO-*` | Former Receiving Info route family | Retired route family | Retired; destination snapshots and payout-owned detail remain with DOC-09/DOC-10 and are not a current runtime route. | DOC-06B / DOC-10 | Superseded |
| `ARCHIVED-ROOT` | ME-ROOT / Payments & Bills / Archived Data | Child root route | Enter the active Saved/Archived Bill/Rent source presentation; the archived-document identity is provisional, with exact Restore/document-version behavior deferred to the formal owners. | DOC-06B | Defined baseline |
| `ARCHIVED-BILLS-LIST` | `ARCHIVED-ROOT` | Child list screen | Search, filter, and review the user's archived bill/fee and rent obligations, then open archived read-only bill/rent detail. | DOC-06C | Defined baseline |
| `ARCHIVED-DOCS-LIST` | `ARCHIVED-ROOT` | Provisional child identity | Retained identity only; no active entry or archived-document/previous-version/Restore interaction contract is authorized by identity alone. | DOC-06B | ID or route open |
| `SUPPORT-ROOT` | ME-ROOT / Settings & Support / contextual failures | Root route | Access support and issue-specific assistance. | DOC-06B / DOC-21 | Partially defined |
| `ABOUT-ROOT` | `ME-ROOT` | Child route | Show PayPlus product and app information. | DOC-06B | Partially defined |
| `TERMS-ROOT` | `ME-ROOT` | Child route | Access applicable terms and policies. | DOC-06B / DOC-07 | Partially defined |

## Assigned Destinations Requiring Further Definition

All currently identified product areas have stable destination IDs. Entrance, Fast/Full Login, Registration, Account Activation, Recovery, Phone Verification, Identity Verification, Payment Passcode Settings, `ENTRANCE-PROMOTION-DETAIL`, and `PAYMENT-CHECKOUT` have defined human-readable behavior baselines. `HOME-ROOT` remains partially defined. For `ENTRANCE-PROMOTION-DETAIL`, final visual and component design, exact DOC-07 Copy/CTA, localization and accessibility expression, technical contracts, prototype and accessibility/user-validation evidence, implementation/UAT, acceptance, monitoring, support, and operational evidence remain open with their formal owners; these downstream dependencies do not block its Defined baseline. For `PAYMENT-CHECKOUT`, final visual and component design, exact Copy and identifiers, Locale Variants, Presentation Mappings, final Bill/Rent source-owner detail, technical contracts, prototype and accessibility/user-validation evidence, implementation/UAT, acceptance, monitoring, support, and operational evidence remain open with their formal owners. Recovery Outcome/Message IDs and copy, provider mapping, technical security controls, Support proof and approval details, detailed tests, and final visual design remain open where assigned to DOC-07, DOC-17, DOC-19, DOC-20, DOC-21, or DOC-22.

## Maintenance Rules

- Update the owning document first, then this register.
- The Parent column records the canonical route hierarchy. Contextual or alternative entry points belong in owning transition tables and route-family diagrams; they do not create a second parent.
- Do not add cards, filters, tabs, ordinary buttons, events, or status labels as routes.
- When a destination changes, check the DOC-06 parent status, DOC-06D, route Mermaid, requirements traceability, and affected notification/deeplink destinations.
- Unresolved items remain visible; do not invent an ID merely to make the register appear complete.
