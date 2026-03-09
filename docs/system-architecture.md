# System Architecture

This document describes the high-level architecture of the Smart Budget Wallet system.

The system is designed using an event-driven architecture where payment transactions trigger budget evaluation and deduction workflows.

---

## Architecture Overview

When a user makes a payment through a digital payment app, the transaction triggers a sequence of services responsible for categorizing the transaction and updating the user's budget envelopes.

High Level Flow:

User Payment  
↓  
Transaction Event Generated  
↓  
Transaction Service  
↓  
Transaction Categorization Service  
↓  
Budget Service  
↓  
Deduction Engine  
↓  
Notification Service

---

## Core Components

### 1. Transaction Service

Responsible for receiving transaction events from the payment system.

Responsibilities:
- Validate transaction
- Record transaction data
- Trigger categorization workflow

---

### 2. Categorization Service

Identifies the spending category based on merchant name.

Possible approaches:

Rule Based:
- Swiggy → Food
- Uber → Travel
- Amazon → Shopping

Future Enhancement:
Machine learning model for dynamic categorization.

---

### 3. Budget Service

Manages user budget envelopes.

Responsibilities:
- Store monthly allocations
- Track remaining balances
- Check budget limits before deduction

---

### 4. Deduction Engine

Handles the logic for deducting spending from envelopes.

Example:

Transaction: ₹500  
Category: Food  
Food Envelope Remaining: ₹800  

After transaction:

Food Envelope Remaining: ₹300

---

### 5. Notification Service

Notifies users when important events occur.

Examples:

- Budget nearing limit
- Budget exceeded
- Monthly summary

Notifications may be delivered via:

- Push notifications
- Email alerts
- In-app messages

---

### 6. Analytics Service (Optional)

Provides insights into user spending patterns.

Example features:

- Monthly spending reports
- Category-wise expense visualization
- Savings recommendations
