## Nequi System — Workshop 3

**Databases II — 2025-I**  
Universidad Distrital Francisco José de Caldas  
Instructor: Ing. Carlos Andrés Sierra  

---

##  Project Summary

This project addresses Workshop 3, focused on Nequi, a digital financial platform. It includes:

- Analysis of concurrency risks.
- Design of a distributed database architecture.
- Performance improvement strategies.
- Updates from Workshop 2.

---

##  Concurrency Analysis

| Scenario | Problem | Solution |
|----------|---------|----------|
| Simultaneous transfers & payments | Risk of negative balance due to simultaneous operations reading the same initial balance. | Pessimistic locking (`SELECT ... FOR UPDATE`) |
| Balance check during top-up | User might see outdated balance. | Use `READ COMMITTED` or `REPEATABLE READ` isolation levels |
| Simultaneous Pocket operations | Conflicting updates causing inconsistencies. | Optimistic concurrency control with versioning |
| Duplicate transfer attempts | Same transaction executed twice due to retries. | UUIDs + idempotency to avoid duplicate processing |

---

##  Distributed Database Design

###  Proposed Distributed Architecture

A **distributed architecture** is proposed for Nequi, based on:

- **Polyglot Persistence:**
  - **PostgreSQL** → For critical relational data: accounts, transactions, credits.
  - **MongoDB** → For semi-structured data: support, PQR, logs.

- **Geographical replication:**
  - Nodes distributed in Bogotá, Medellín, and abroad.
  - High availability in case of regional failures.

- **Horizontal partitioning (Sharding):**
  - PostgreSQL partitioned by `account_id` or region.
  - MongoDB sharded by `user_id`.

- **ETL and historical storage:**
  - Historical data migrated to **cloud cold storage** (e.g., Google Cloud).
  - Maintains regulatory compliance for minimum two months of online data retention.

- **Parallel processing:**
  - OLAP queries executed in engines like BigQuery.
  - ETL processes for BI without impacting the transactional database.

---

##  Performance Strategies

- Regional replication for lower latency.
- Offloading old data to cloud to reduce DB load.
- Horizontal scaling using sharding.

---

##  Workshop 2 Improvements

- Added attributes to Pocket entity for savings goals.
- Enhanced architecture for concurrency and distributed systems.
