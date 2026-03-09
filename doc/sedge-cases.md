# Edge Cases and Failure Handling

This document describes potential edge cases that the Smart Budget Wallet system must handle.

---

## 1. Budget Exhausted

If a user attempts a transaction after the budget for a category has been exhausted.

Example:

Food Budget Remaining: ₹0  
User attempts Swiggy payment: ₹500

Possible Solutions:

- Prompt the user to continue using general wallet balance
- Allow overdraft with warning notification
- Block transaction depending on user preference

---

## 2. Unknown Merchant

The system may fail to categorize a merchant if it does not exist in the category mapping table.

Example:

Merchant: Local restaurant

Handling Strategy:

- Assign default category "Others"
- Ask user to manually categorize
- Update mapping table for future transactions

---

## 3. Refund Handling

If a transaction is refunded, the system should restore the amount back to the correct envelope.

Example:

Original transaction:

Uber → ₹300 → Travel envelope

Refund:

₹300 returned to Travel envelope.

---

## 4. Multiple Transactions at the Same Time

Users may perform transactions simultaneously from multiple devices.

Possible Issue:

Race conditions when updating envelope balances.

Solution:

- Use atomic database operations
- Implement locking or transactional updates

---

## 5. Month Reset

At the beginning of a new month:

- Budgets reset to allocated values
- Remaining balances move to savings (optional feature)

Example:

Food Budget: ₹800 remaining

Possible handling:

- Carry forward to savings envelope
- Reset to new monthly budget
