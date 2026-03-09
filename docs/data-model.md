# Data Model Design

This document defines the core data structures required to support the Smart Budget Wallet system.

The system stores information about user budgets, transactions, and merchant category mappings.

---

## 1. User Budget Table

This table stores the envelope budgets created by users for a given month.

Each category has an allocated budget and a remaining balance that gets updated after each transaction.

Fields:

user_id  
month  
category  
allocated_amount  
remaining_amount  
created_at  
updated_at  

Example:

| user_id | month | category | allocated_amount | remaining_amount |
|-------|-------|---------|------------------|------------------|
| 123 | 2026-03 | Food | 8000 | 6500 |
| 123 | 2026-03 | Travel | 3000 | 2400 |
| 123 | 2026-03 | Shopping | 4000 | 3900 |

---

## 2. Transactions Table

This table stores all payment transactions performed by the user.

Fields:

transaction_id  
user_id  
merchant_name  
category  
amount  
timestamp  
payment_method  

Example:

| transaction_id | user_id | merchant_name | category | amount |
|---------------|--------|---------------|---------|-------|
| tx001 | 123 | Swiggy | Food | 500 |
| tx002 | 123 | Uber | Travel | 300 |

---

## 3. Category Mapping Table

This table maps merchants to spending categories.

The categorization service uses this table to automatically classify transactions.

Fields:

merchant_name  
category  
confidence_score  

Example:

| merchant_name | category | confidence_score |
|---------------|---------|------------------|
| Swiggy | Food | 0.95 |
| Uber | Travel | 0.98 |
| Amazon | Shopping | 0.92 |

---

## 4. Savings Rules Table (Future Feature)

This table defines automated saving rules for users.

For example, round-up savings or percentage-based micro savings.

Fields:

rule_id  
user_id  
rule_type  
rule_value  
created_at  

Example:

| rule_id | user_id | rule_type | rule_value |
|--------|--------|-----------|-----------|
| r1 | 123 | round_up | nearest_10 |
| r2 | 123 | percentage_save | 5% |

---

## Data Storage Considerations

Possible storage options include:

- Amazon DynamoDB for scalable key-value storage
- PostgreSQL for relational data modeling

The choice depends on scalability, query patterns, and system requirements.
