# Design Tradeoffs

This document explains important design decisions and tradeoffs considered while designing the Smart Budget Wallet system.

Understanding tradeoffs is important when building scalable fintech products.

---

## 1. Rule-Based Categorization vs Machine Learning

### Rule-Based Categorization

Example:

Swiggy → Food  
Uber → Travel  
Amazon → Shopping

Pros:
- Simple implementation
- Easy to debug
- Predictable behavior

Cons:
- Limited flexibility
- Requires manual updates for new merchants

---

### Machine Learning Categorization

A machine learning model predicts the category based on merchant name and historical transactions.

Pros:
- More adaptive
- Handles new merchants automatically
- Improves over time

Cons:
- Higher complexity
- Requires training data
- Less transparent decisions

Decision:

The initial system should start with rule-based categorization and gradually introduce ML models.

---

## 2. Relational Database vs NoSQL

### Relational Database (PostgreSQL)

Pros:
- Strong consistency
- Structured schema
- Powerful query capabilities

Cons:
- Scaling horizontally can be complex

---

### NoSQL Database (DynamoDB)

Pros:
- Highly scalable
- Suitable for high transaction workloads
- Managed infrastructure

Cons:
- Limited complex querying

Decision:

For large-scale fintech applications, DynamoDB is a suitable option due to scalability and low operational overhead.

---

## 3. Real-Time Processing vs Batch Processing

### Real-Time Processing

Transactions update budgets immediately.

Pros:
- Instant feedback to users
- Better user experience

Cons:
- Higher system complexity

---

### Batch Processing

Transactions processed periodically.

Pros:
- Simpler architecture
- Lower system load

Cons:
- Delayed updates for users

Decision:

Real-time processing is preferred to ensure accurate budget tracking.

---

## 4. Strict Budget Enforcement vs Soft Alerts

### Strict Enforcement

Transactions blocked when category budget is exceeded.

Pros:
- Strong financial discipline

Cons:
- Poor user experience

---

### Soft Alerts

Users receive warnings but transactions continue.

Pros:
- Flexible user experience
- Less friction

Cons:
- Users may ignore alerts

Decision:

Soft alerts should be the default behavior with optional strict enforcement settings.
