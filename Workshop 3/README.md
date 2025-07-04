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

A distributed database was chosen instead of a parallel database because:

- Nequi mainly performs OLTP operations (transfers, payments, balance checks) requiring real-time processing and high availability.
- Parallel databases are better suited for OLAP workloads with massive batch queries, which is not Kine’s primary use case.
- A distributed architecture allows:
  - Geographic replication for regional availability.
  - Separation of hot data (recent transactions) from cold data (historical archives) for regulatory compliance.
  - Horizontal scaling to handle millions of users without a single point of failure.

Thus, a distributed model meets Kine’s needs for real-time operations, scalability, and compliance more efficiently than a purely parallel system.

---

##  Performance Strategies

- Regional replication for lower latency.
- Offloading old data to cloud to reduce DB load.
- Horizontal scaling using sharding.

---

##  Workshop 2 Improvements

- Added attributes to Pocket entity for savings goals.
- Enhanced architecture for concurrency and distributed systems.
