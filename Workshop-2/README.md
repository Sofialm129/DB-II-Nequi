# Workshop 2 — Data System Architecture and Information Retrieval

## Introduction

This repository contains the deliverables for **Workshop No. 2** of the Databases II course. The main objective of this workshop is to design the first version of the data system architecture for the Nequi-inspired application and to define the types of information the system must retrieve, as well as how it will retrieve them using SQL (PostgreSQL) and NoSQL (MongoDB) queries.

This work builds on the foundations of Workshop 1 and integrates improvements in data modeling, query design, and support for semi-structured data needs.

---

## Structure of This Delivery

### 1. **System Architecture**
- High-level overview of the system components.
- Technologies selected: PostgreSQL (relational) and MongoDB (NoSQL).
- Explanation of data flow from user interaction to data analytics (via ETL and BI).

### 2. **Information Requirements**
- Description of critical business needs and user stories.
- Identification of what data must be retrieved to support those needs.
- Includes support, credit management, account activity, user authentication, and more.

### 3. **Query Proposals**
- SQL queries (PostgreSQL) for retrieving structured data (accounts, movements, authentication, credit).
- NoSQL queries (MongoDB) for handling support requests and communication tracking.
- Each query includes an explanation of its purpose and the business insight it provides.

### 4. **Workshop 1 Improvements**
- Revised entity-relationship model (ERD).
- Refined user stories and business logic.
- Additions to the Money Management module (pocket, cushion, card).
- Enhancements to the Device and Movement entities.

---

## Technologies Used

| Component                      | Technology            | Purpose                                       |
|-------------------------------|------------------------|-----------------------------------------------|
| API & Microservices           | Java Spring Boot       | Service orchestration and business logic      |
| Relational Database           | PostgreSQL             | Structured data (users, accounts, movements)  |
| NoSQL Database                | MongoDB                | Semi-structured support data                  |
| ETL Pipeline                  | Python + Pandas        | Data extraction and transformation            |
| Data Warehouse                | Google BigQuery        | Historical data storage and querying          |
| BI Tool                       | Google Data Studio     | Dashboards and report visualization           |


