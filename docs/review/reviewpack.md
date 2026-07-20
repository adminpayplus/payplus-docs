# Founder Review Pack: Offers Child Lists

## 1. Review Status

The founder has accepted `OCL-01` through `OCL-09`, including the clarified multi-collection, duplicate-suppression, stable-ordering, and checkout-promotion rules recorded below.

This pack is a review and decision record. The authoritative behavior remains in `DOC-06B`, `DOC-09`, and `DOC-13`.

## 2. Mandatory Terminology

| Term | Definition |
| --- | --- |
| Offer | One promotion-engine benefit package identified by one unique Offer ID. |
| Offer card | A UI component displaying a simplified offer summary. It is unrelated to credit cards or tokenization. |
| Payment card | A tokenized or newly entered credit/debit card used as a funding instrument. |
| Payment method | A broader funding channel, such as payment card, Alipay, WeChat Pay, or another supported method. |
| Card Offer | An offer whose eligibility depends on permitted payment-card attributes. |
| Payment profile | A saved split-card allocation template containing multiple payment cards. |
| Discovery collection | A user-facing offer grouping, such as Card Offers, Pay+ Offers, or Partner Offers. It is not an eligibility rule or campaign. |
| Duplicate offer | The same Offer ID displayed repeatedly in the same screen context. Different Offer IDs are not duplicates. |

The documents should avoid using `card` alone where it could mean either an offer card or payment card.

## 3. Accepted Decisions

| ID | Accepted decision |
| --- | --- |
| `OCL-01` | `OFFERS-CARD-LIST`, `OFFERS-PAYPLUS-LIST`, and `OFFERS-PARTNER-LIST` remain child collection screens under `OFFERS-ROOT`. |
| `OCL-02` | The three screens share one collection-screen contract with route-specific differences. |
| `OCL-03` | Search, labels, filters, sorting, and result states are screen states, not routes. |
| `OCL-04` | Discovery offer cards open `OFFER-DETAIL`; material checkout, redemption, and external actions do not execute from the list card. |
| `OCL-05A` | One payment card may match multiple distinct offers, each evaluated under its own Offer ID. |
| `OCL-05B` | One Offer ID may belong to multiple relevant discovery collections. |
| `OCL-06` | The same Offer ID is suppressed from unintended repeated display on `OFFERS-ROOT` but remains available in every relevant child list. |
| `OCL-07` | Child lists use controlled, stable, collection-specific admin ordering without random reshuffling or MVP user sorting. |
| `OCL-08` | Payment-card/profile selection and applicable promotion handling occur in the same checkout screen or step before authorization. |
| `OCL-09` | MVP uses a single-column mobile list and single-select label filters where applicable. |

## 4. Collection And Duplicate Behavior

One Offer ID may be assigned to several discovery collections where its characteristics overlap. For example, one Cathay Mastercard offer may belong to Card Offers because card eligibility applies and Partner Offers because Cathay or Standard Chartered sponsors it.

Collection membership does not duplicate the underlying offer object or change eligibility rules.

Default display behavior:

1. Render each Offer ID once within each child list.
2. Allow the offer to appear in every relevant complete child list.
3. Render the same Offer ID once on a normal `OFFERS-ROOT` presentation.
4. Use the admin-configured primary root placement.
5. Permit an approved, audited override for intentional repeated root placement.

Two distinct offers eligible for the same payment card are not duplicates.

## 5. Stable Child-List Ordering

Display ordering controls discovery position only. It does not determine eligibility, stacking, benefit calculation, or which offer wins at checkout.

Required sequence:

1. Apply approval, enablement, display-period, market, privacy, consent, targeting, and compliance gates.
2. Apply collection-specific admin pinning and priority.
3. Apply approved personalization within the permitted priority band.
4. Resolve equal priority through a deterministic fallback, currently `TBC`.
5. Preserve the order while the user browses and returns from `OFFER-DETAIL`.

Root-carousel randomization remains separate from complete child-list ordering.

## 6. Payment-Method-Sensitive Offer Principle

If one payment card or split-payment funding leg is eligible for multiple payment-method-sensitive Card Offers:

1. Only one Card Offer applies to that payment card or funding leg.
2. PayPlus automatically selects the eligible Card Offer with the highest user value.
3. Checkout displays the applied offer and resulting benefit.
4. The payer does not manually choose between competing Card Offers.
5. Equal or non-directly-comparable values use a deterministic admin-configured priority until the final valuation method is specified.

This does not prevent a separate eligible checkout coupon, voucher, or discount code from applying. The automatically selected Card Offer and the user-selected coupon/voucher/discount are different benefit families and use separate application slots.

For split-card payment, the one-best-Card-Offer rule applies independently to each funding leg. A card-sensitive benefit normally applies only to that leg's funded amount unless approved offer rules explicitly use the whole payment.

## 7. Checkout Behavior

The same checkout screen or step must:

1. show the obligation and payment amount;
2. allow selection or confirmation of the payment card or payment profile;
3. evaluate payment-method-sensitive Card Offers;
4. auto-apply and display the highest-user-value eligible Card Offer per card/funding leg;
5. allow a separate eligible coupon/voucher/discount selection;
6. recalculate fees, discounts, benefits, and final total;
7. show the final quote before payer authorization.

Changing the payment card, profile, allocation, amount, or another material eligibility input invalidates the prior promotion result and triggers recalculation.

An offer opened through `OFFER-DETAIL` may be carried into checkout as a candidate, but checkout cannot treat it as selected or eligible until payment-card and transaction validation succeeds.

## 8. Ownership

| Document | Ownership |
| --- | --- |
| `DOC-06B` | Child-list UX, offer-card behavior, collection display, ordering, navigation, states, and checkout handoff. |
| `DOC-13` | Offer identity, collection membership, payment-card eligibility, highest-user-value selection, stacking, coupon/voucher rules, benefit calculation, and application. |
| `DOC-09` | Same-screen checkout sequence, payment-card/profile selection, promotion result display, quote recalculation, and payer authorization. |
| `DOC-06D` | Acceptance and test-readiness coverage. |
| `DOC-18` | Future data structures, selection records, funding-leg links, display snapshots, and audit events. |
| `DOC-22` | Future collection assignment, primary placement, priority, override, valuation, and audit controls. |

## 9. Remaining TBC Items

- Pay+ and Partner label taxonomy.
- Equal-priority child-list ordering fallback.
- Approved valuation method for non-monetary or non-directly-comparable Card Offers.
- Exact split-card offer-selection presentation.
- Whether personalization affects inclusion, ordering, or both.
- Final PSP/acquirer card metadata available for eligibility confirmation.
- Exact offer-card styling and responsive behavior.

## 10. Repository Alignment

The accepted decisions require alignment in:

- `DOC-05` and parent `DOC-06` for concise product/ownership references;
- `DOC-06B` for child-list UX;
- `DOC-06D` for acceptance coverage;
- `DOC-09` for checkout behavior;
- `DOC-13` for promotion rules;
- `DOC-18` and `DOC-22` for future technical/admin markers;
- the requirements traceability matrix.

No route-diagram topology change is required.
