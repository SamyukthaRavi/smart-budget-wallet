# Smart Budget Wallet

Digital envelope budgeting architecture for modern UPI payment applications.

A system design exploration showing how digital payment platforms can help users manage budgets using envelope-based financial planning.

## Problem Statement

Traditional budgeting works well when people use physical cash. 
Users often separate money into different envelopes or wallets for specific purposes such as food, rent, travel, and savings. This helps them control spending and build savings.

However, with the rise of digital payments through apps like Google Pay and Amazon Pay, all money exists in a single digital balance. This makes it harder for users to mentally allocate budgets and track category-based spending.

Many users struggle with:
- Overspending due to lack of budget visibility
- Difficulty allocating money for specific purposes
- Lack of automated saving mechanisms

## Proposed Solution

Smart Budget Wallet introduces a digital envelope budgeting system integrated within payment applications.

Users can create multiple budget envelopes such as:

- Rent
- Food
- Travel
- Shopping
- Entertainment
- Savings

Each envelope contains a user-defined monthly allocation.

When a payment transaction occurs, the system automatically categorizes the transaction and deducts the amount from the corresponding envelope.

Example:
Swiggy payment → deducted from Food budget  
Uber ride → deducted from Travel budget  
Amazon purchase → deducted from Shopping budget  

If the allocated amount is exhausted, the system alerts the user before proceeding.

## Key Features

- Digital Envelope Budgeting
- Automatic Transaction Categorization
- Real-time Budget Tracking
- Budget Exhaustion Alerts
- Monthly Budget Reset
- Automated Savings Transfer

## Example User Scenario

Monthly Salary: ₹60,000

User allocates:

Rent: ₹15,000  
Food: ₹8,000  
Travel: ₹3,000  
Shopping: ₹4,000  
Entertainment: ₹2,000  
Savings: ₹10,000  

When the user spends ₹500 on food delivery, the system deducts from the Food envelope and updates the remaining balance.

## System Architecture

The system follows an event-driven microservice architecture where payment events trigger budget tracking and categorization workflows.

Core components:

1. Transaction Service  
Receives payment events from the payment gateway.

2. Categorization Service  
Identifies merchant category using rule-based or machine learning methods.

3. Budget Service  
Maintains envelope allocations and tracks remaining balances.

4. Deduction Engine  
Handles deduction logic and updates user budgets.

5. Notification Service  
Alerts users when budgets approach limits.

## Technology Stack (Example)

Backend
- Java / Kotlin
- Spring Boot

Cloud Infrastructure
- AWS Lambda
- Amazon API Gateway
- Amazon DynamoDB

Event Processing
- Amazon Kinesis / Amazon EventBridge

Notifications
- Amazon SNS

Analytics
- Amazon Redshift


## High Level Flow

User makes a payment through a UPI app  
        ↓  
Transaction event is generated  
        ↓  
Transaction Categorization Service identifies merchant category  
        ↓  
Budget Service checks the relevant envelope  
        ↓  
Amount is deducted from the envelope balance  
        ↓  
User receives notification if the budget limit is nearing

## Architecture Diagram

                +----------------------+
                |   UPI Payment App    |
                | (Amazon Pay / GPay)  |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |  Transaction Service |
                +----------+-----------+
                           |
                           v
                +----------------------+
                | Categorization       |
                | Service              |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |   Budget Service     |
                | (Envelope Manager)   |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |  Deduction Engine    |
                +----------+-----------+
                           |
              +------------+------------+
              |                         |
              v                         v
    +------------------+      +------------------+
    | Budget Database  |      | Notification     |
    | (DynamoDB)       |      | Service (SNS)    |
    +------------------+      +------------------+

## Future Enhancements

- Machine learning based transaction categorization
- AI-powered spending insights
- Shared family budgets
- Automatic investment routing
- Integration with financial goal planning

## Purpose of this Project

This repository explores how digital payment platforms can incorporate behavioral budgeting principles to help users improve financial discipline and savings habits.

The goal is to demonstrate a scalable architecture that can be integrated into modern fintech payment systems.

## Project Structure
smart-budget-wallet:
docs/
   data-model.md
   design-tradeoffs.md
   edge-cases.md
   month-end-savings-transfer.md
   product-requirements.md
   product-roadmap.md
   system-architecture.md
   user-experience-flow.md

## Author

Samyuktha Ravichandran

## Disclaimer

This project is a conceptual system design created for learning and exploration purposes.

The architecture and ideas presented here are not based on any internal systems or proprietary information from any company.

Any references to payment platforms such as Google Pay or Amazon Pay are purely illustrative examples of where such a feature could potentially be integrated.
