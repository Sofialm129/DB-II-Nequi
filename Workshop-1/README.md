# Nequi Data Management System — Workshop 1

This repository contains the deliverables for Workshop No. 1 of the Databases II course (2025-I), under the guidance of Eng. Carlos Andrés Sierra at Universidad Distrital Francisco José de Caldas.

---

## Methodology and Deliverables

### 1. Business Model Canvas

We present the Business Model Canvas for Nequi as a digital financial services platform. It includes:

- **Key Partners**: Banking institutions, payment processors, app stores.
- **Key Activities**: Mobile transactions, digital wallet services, user account management, security.
- **Value Propositions**: Instant transactions, accessible financial tools, no-cost services.
- **Customer Relationships**: User-centered support, secure authentication.
- **Customer Segments**: Mobile users in Colombia, banked and unbanked individuals.
- **Channels**: Mobile app, website.
- **Key Resources**: Cloud infrastructure, customer data, software platform.
- **Cost Structure**: Infrastructure, development, operations, support.
- **Revenue Streams**: Commissions on services, interest from loans, partnerships.

### 2. Requirements Documentation

#### Functional Requirements

- User registration and authentication
- Balance inquiry and transaction history
- Transfers, bill payments, and mobile top-ups
- Credit application and approval process
- Support ticket management

#### Non-Functional Requirements

- High availability and reliability
- Scalability to handle millions of users
- Low-latency query execution
- Data security and privacy
- Real-time data ingestion
- Distributed architecture for multi-location access

### 3. User Stories

Includes 8 detailed user stories from multiple roles (end-user, support agent, admin), each with acceptance criteria and formatted as:

> As a [role], I want to [action] so that [benefit].

Example:

> As a user, I want to check my account balance so that I can keep track of my finances.

### 4. Initial Database Architecture

- A high-level Entity-Relationship (ER) model was designed considering scalability and modularity.
- Main entities include: User, Account, Transaction, Device, Authentication, Loan, Support.
- Relationships between entities have been defined based on real-world financial operations.
- Data flow diagram and a relational schema are included to illustrate system dynamics.

