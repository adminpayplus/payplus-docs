# DOC-22 — Admin Management Dashboard and Operations Workflow

## 1. Purpose

## 2. Scope

## 3. Out of Scope

## 4. Admin User Roles

## 5. Admin Permission Model Summary

## 6. Admin Dashboard Overview

## 7. Operations Queues

### 7.1 Account Review Queue
### 7.2 Payee Review Queue
### 7.3 Evidence Review Queue
### 7.4 Payment Request Review Queue
### 7.5 Risk Review Queue
### 7.6 Duplicate Detection Queue
### 7.7 Dispute Queue
### 7.8 Clarification Queue
### 7.9 Failed Payment Queue
### 7.10 Payout Exception Queue
### 7.11 Refund/Reversal Queue
### 7.12 Compliance Escalation Queue
### 7.13 Campaign and Promotion Review Queue
### 7.14 Reward Entitlement and Voucher Exception Queue

## 8. Admin Review Workflows

## 9. User Management Workflows

## 10. Evidence and Bill Verification Workflows

## 11. Payment Operations Workflows

Admin dashboard must support DOC-09 user payment instruction review at operations level.

Required capabilities should include:

- view payment instruction status;
- view single-card or split-card funding leg progress;
- view deferred funding date, selected payee transfer date, reminder status, partial funding, remaining unpaid amount, and partial payout linkage;
- view payment quote, promotion quote, reservation status, revalidation result, changed-term acknowledgement, and expiry where applicable;
- distinguish partially funded instruction from completed payment;
- trigger permitted reminder, user action, hold, cancellation, expiry, or escalation workflow according to approved policy.

## 12. Payout and Reconciliation Workflows

## 13. Refund, Cancellation, and Chargeback Operations

## 14. Risk, Fraud, AML, and Anti-Cashout Operations

## 15. Dispute and Clarification Management

## 16. Internal Notes and Case Management

## 17. Admin Actions and Status Changes

## 18. Campaign, Promotion, Coupon, Voucher, and Reward Operations

Detailed promotion-engine rules belong in DOC-13. Admin workflows should support campaign setup, offer setup, eligibility rule configuration, qualification and entitlement review, coupon/voucher issuance, miles fulfilment status, external voucher exception handling, reward reversal, and approval/audit workflow where promotions are enabled.

### 18.1 Dashboard Shortcut and Placement Configuration

Admin dashboard must support configuration hooks for the DOC-06 designated Home Dashboard flow where enabled.

Required capabilities should include:

- configure default dashboard shortcut set;
- configure default dashboard shortcut order;
- add, disable, hide, or restore shortcuts by feature, module, category, user type, eligibility, or launch phase;
- preserve user-managed shortcut order and visibility preferences where allowed;
- allow user restore-to-default behavior;
- configure Important Notice / Action Required items, including priority, expiry, collapse behavior, route target, audience, approval status, and audit log;
- configure Featured / What's New / Hot Offer carousel placements, including priority, start/end date, targeting, offer or announcement linkage, route target, approval status, enable/disable, and audit log;
- distinguish dashboard placement from notification delivery, inbox entry, campaign eligibility, and promotion entitlement;
- record admin changes to shortcut defaults, dashboard placements, carousel configuration, and notice/action items.

Detailed final admin screens, permission matrix, approval workflow, and implementation fields will be drafted in full DOC-22 and DOC-18.

## 19. Audit Logging Requirements

## 20. Notifications and Escalations

## 21. Dashboard Screen Inventory

## 22. Reporting and Export Requirements

## 23. Security and Access Control Requirements

Admin access must be role-based and aligned with DOC-15 and DOC-19. Sensitive identity, evidence, payment, payout, risk, promotion, support, and authentication/security data should use masking, controlled reveal, reason capture, and audit logging.

Admin users should not access raw card data, CVV, sensitive authentication data, full token secrets, or unrestricted identity/evidence files unless explicitly approved under the final security and privacy model.

## 24. Privacy and Data Handling Requirements

Admin screens must respect DOC-15 data classification and DOC-18 field metadata.

Required admin data-handling controls should include:

- field-level visibility by role, queue, and approved purpose;
- masking and reveal rules for sensitive fields;
- access reason capture for sensitive data views, exports, downloads, overrides, and corrections;
- audit logging for access, change, export, review, hold, release, override, and deletion actions;
- audit logging for dashboard shortcut configuration, dashboard placement configuration, notice/action configuration, carousel configuration, and restore-default configuration;
- privacy-safe duplicate/reused evidence warnings that do not reveal another user's private data;
- export controls for reports, bank files, payout batches, evidence packages, dispute files, and promotion/partner reports.

Detailed workflow, screen design, and permission matrix will be drafted in full DOC-22.

## 25. Monitoring and Incident Response Linkage

## 26. MVP Acceptance Criteria

## 27. Open Questions

## 28. Revision History
