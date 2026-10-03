# CriticalPay - Architecture Vision

## 1. Purpose

CriticalPay is a high-reliability payment gateway designed to process payment operations safely, consistently, and observably.

The project is intended to explore software architecture and engineering practices for critical systems, including domain modeling, concurrency, resilience, distributed systems, event-driven communication, observability, SQL/NoSQL persistence, and cloud-native infrastructure.

## 2. Core Domain

The core domain is payment processing.

The initial domain concepts are:

- Payment
- PaymentId
- PaymentStatus
- Money
- Merchant
- PaymentTransaction
- PaymentProvider
- Ledger

## 3. Main Business Concerns

The system must address problems such as:

- duplicate payment requests
- idempotency
- payment state transitions
- concurrency
- partial failures
- external provider failures
- auditability
- consistency
- resilience
- observability

## 4. Initial Architectural Approach

CriticalPay will start as a modular monolith.

The initial architecture will be inspired by:

- Domain-Driven Design
- Clean Architecture
- Hexagonal Architecture
- SOLID principles

The system will evolve toward distributed components only when there is a concrete architectural reason to do so.

## 5. Initial Technical Direction

Current planned technologies:

- Java 21
- Spring Boot
- PostgreSQL
- Flyway
- Docker
- JUnit

Planned evolution:

- Kafka
- MongoDB
- Kubernetes
- Prometheus
- Grafana
- OpenTelemetry
- CI/CD

## 6. Architectural Principles

- Business rules should not depend directly on frameworks or infrastructure.
- Infrastructure should remain replaceable where practical.
- Domain concepts should be explicit in the code.
- High-value business rules should be protected by domain objects.
- Technical complexity should only be introduced when justified.
- Tests should validate business behavior, not only implementation details.
- Architectural decisions should be documented as they are made.

## 7. Open Questions

The following decisions are intentionally left open for now:

- Whether Payment will also be a JPA entity or will be separated from persistence entities
- Exact aggregate boundaries
- Whether PaymentTransaction belongs inside the Payment aggregate
- Which use case will justify MongoDB
- When the system should evolve from modular monolith to distributed services
- When Kafka should be introduced