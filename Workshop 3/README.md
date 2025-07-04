## Project: Nequi System (Workshop 3)

**Databases II — 2025-I**  
**Universidad Distrital Francisco José de Caldas**  
Instructor: Ing. Carlos Andrés Sierra  

---

## ✅ Overview

This project corresponds to the development of Workshop No. 3 for the Databases II course, focused on the digital financial platform **Nequi**. In this deliverable, we:

- Analyze concurrency risks and scenarios involving simultaneous access to critical data.
- Design a distributed database architecture ensuring availability, performance, and regulatory compliance.
- Propose specific performance improvement strategies.
- Incorporate enhancements based on feedback from Workshop 2.

The solution is inspired by real architectures of financial platforms like Nequi, designed to support high volumes of users and real-time transactions.

---

## 🔹 1. Concurrency Analysis

The following critical concurrency scenarios were identified in the Nequi system:

| Concurrency Scenario | Problem Description | Proposed Solution | Technical Explanation |
|----------------------|---------------------|-------------------|-----------------------|
| Simultaneous transfers and payments from the same account | Two operations (a transfer and a payment) may execute almost simultaneously, leading to the risk of a negative balance if both read the same initial balance. | Pessimistic locking (`SELECT ... FOR UPDATE`) on the account record. | Locks the account row during the operation, ensuring only one transaction can modify the balance at a time. The second waits until the first completes. |
| Balance inquiry during a top-up | While the user performs a top-up, they simultaneously check their balance, potentially showing an outdated balance. | Use of `READ COMMITTED` or `REPEATABLE READ` isolation levels. | Ensures reads only access committed data, avoiding dirty reads. |
| Simultaneous use of a Pocket (Savings Pocket) | The user has an automatic daily saving transfer and simultaneously performs a manual withdrawal from the same Pocket. This may cause inconsistencies or duplicate records. | Optimistic concurrency control (versioning). | A version or timestamp field is used. Before saving, the system checks if another process modified the record. If so, it rejects the operation and requires a retry with updated data. |
| Duplicate transfer due to retries | A user sends a transfer and, after a network error, presses “Send” again. Both requests might be processed without control. | Use of UUIDs and idempotency. | A unique `transaction_id` (UUID) is generated and saved in the database. If the same transaction arrives again, it’s detected and not executed twice. |

---

## 🔹 2. Design of Parallel and Distributed Databases

### 🌐 Proposed Distributed Architecture

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

## 🔹 3. Performance Improvement Strategies

### ✅ Distributed Replication

- Regional replicas for faster reads.
- Lower latency based on user geographic location.
- High availability in case a node fails.

### ✅ Offloading Historical Data

- Transactions older than two months migrated to cloud storage.
- Reduces load on active databases.
- Complies with Colombian data retention regulations.

### ✅ Horizontal Scaling

- Sharding used in PostgreSQL and MongoDB.
- Supports traffic spikes without relying on massive servers.
- Dynamic adjustment of nodes based on demand.

---

## 🔹 4. Improvements over Workshop 2

- Attributes were added to the **Pocket** entity to support automated savings goals.
- Queries and architecture adjusted to consider concurrency and distributed systems.
- Better integration between OLTP (transactional) and OLAP (analytical) components.

---

## 📦 Repository Structure

