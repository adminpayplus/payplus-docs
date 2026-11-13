# PayPlus Offers, Rewards, and Referral Route Map

Status: Current discussion reference
Owner: DOC-06B / DOC-13
Last updated: 2026-11-13

```mermaid
flowchart TD
  NAV["Bottom navigation Offers"] --> OFFERS["OFFERS-ROOT"]
  HOME["Home Hot Offer"] --> OFFERDETAIL["OFFER-DETAIL"]
  OFFERS --> OFFERDETAIL
  OFFERS --> CARDLIST["OFFERS-CARD-LIST"]
  OFFERS --> PAYPLUSLIST["OFFERS-PAYPLUS-LIST"]
  OFFERS --> PARTNERLIST["OFFERS-PARTNER-LIST"]
  CARDLIST --> OFFERDETAIL
  PAYPLUSLIST --> OFFERDETAIL
  PARTNERLIST --> OFFERDETAIL

  OFFERS -->|"Header My Rewards"| REWARDS["REWARDS-ROOT"]
  REWARDS --> REWARDDETAIL["REWARD-DETAIL"]
  CHECKOUT["PAYMENT-CHECKOUT"] -->|"View reward details"| REWARDDETAIL
  REWARDDETAIL -. "Return without changing checkout selection" .-> CHECKOUT

  SHORTCUT["Dashboard Referral shortcut"] --> REFERRAL["REFERRAL-ROOT"]
  ME["ME-ROOT"] --> REFERRAL
  OFFERDETAIL -. "Referral-program action" .-> REFERRAL
  REFERRAL --> REFLIST["REFERRAL-REWARDS-LIST"]
  REFLIST --> REFDETAIL["REFERRAL-ENTITLEMENT-DETAIL"]
  REFDETAIL --> CLAIM["REFERRAL-REWARD-CLAIM"]
  CLAIM --> REWARDDETAIL

  REFLINK["Referral deeplink / QR"] --> REGISTER["AUTH-REGISTRATION"]
  REGISTER -. "Post-create Done/identity/Later flow: see Authentication map" .-> AUTHFLOW["Owned authentication handoff"]
  REGISTER -. "Confirmed eligible account creation with valid code only" .-> ATTRIBUTION["Referral attribution record"]
  ATTRIBUTION -. "Progress later visible" .-> REFERRAL
```

Offers remains discovery, Rewards manages issued instruments and Referral preserves qualification/entitlement/claim identities. Current root/child composition and header/filter/search/carousel behavior follow DOC-06B Section 5.16; source/category/status remain independent. Restricted/Soon are conditions, no Rewards featured module or mandatory detailed campaign filters are added, and the seven-day default remains owner-controlled. Browse unassigned qualification differs from named issued Use/usage expiry; view/reveal/copy/external return does not prove consumption.

Manual optional referral code may be corrected/cleared before confirmed creation; incoming deeplink/QR stays non-editable and completed attribution immutable. Sharing alone creates no recipient/attribution. Masked friend progress is its owned child presentation, not another stable destination. `HOME-ROOT` is reached through the owned post-create/return contract, not a direct unconfirmed registration edge. Current state and original caller/claim identity are preserved; partner/native/growth parity remains an implementation limit, not new policy.
