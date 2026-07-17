# PayPlus Promotion-Engine Structure

Status: Business-structure reference

Owner: DOC-13

Last updated: 2026-07-17

This diagram duplicates the promotion-engine structure defined in DOC-13 for convenient visual reference. DOC-13 remains the authoritative source. If this file conflicts with DOC-13, DOC-13 prevails.

```mermaid
flowchart TD
    ENGINE["Unified Growth and Promotion Engine"]

    GENERAL["General Promotion"]
    REFERRAL["Referral Program"]
    MEMBERSHIP["Membership / Loyalty Program"]

    CAMPAIGNS["Each context contains Campaigns"]
    OFFERS["Each campaign contains Offers"]
    RULES["Rule Sets<br/>Eligibility, qualification, entitlement and limits"]
    DECISION{"Benefit Decision"}

    CHECKOUT["Apply at Checkout<br/>Discount, fee waiver or special rate"]
    REWARD["Issue Reward<br/>Coupon, voucher or miles"]
    PARTNER["Partner Fulfilment<br/>QR, code, deeplink or API"]

    ENGINE --> GENERAL
    ENGINE --> REFERRAL
    ENGINE --> MEMBERSHIP

    GENERAL --> CAMPAIGNS
    REFERRAL --> CAMPAIGNS
    MEMBERSHIP --> CAMPAIGNS

    CAMPAIGNS --> OFFERS
    OFFERS --> RULES
    RULES --> DECISION

    DECISION --> CHECKOUT
    DECISION --> REWARD
    DECISION --> PARTNER
```

Each general-promotion, referral, or membership context may contain multiple campaigns. Each campaign may contain multiple offers. An offer may combine multiple rule groups and conditions.

This is a business-structure diagram, not an app navigation map. DOC-06B and `payplus-app-route-entry-map.md` separately govern how users discover offers, manage issued rewards, and enter referral functions.
