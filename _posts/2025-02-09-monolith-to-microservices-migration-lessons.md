---
layout: post
title: "Monolith to Microservices — Migration Lessons"
date: 2025-02-09 10:00:00 -0600
categories: engineering architecture migration
---

These lessons come from modernizing legacy pharmacy workflows into a Step Functions + Lambda–based orchestration platform at Cigna. Migrating from a monolith to microservices is less about “rewrite everything” and more about **bounded steps, clear boundaries, and keeping the system running**. Here’s what translated well.

## 1. Strangler fig, not big bang

- Don’t plan to replace the monolith in one release.
- **Identify a slice:** one capability (e.g., “order scheduling for prescriptions,” “drug substitution evaluation”) that has a clear API and limited dependencies.
- Build a new service (or Lambda + API) that implements that slice. Route new callers (or one workflow) to it; keep the rest on the monolith.
- Gradually move more traffic and, when safe, retire that path in the monolith.

Repeating this for multiple slices over time is the “strangler fig” pattern: the new system grows around the old one until the old one can be turned off.

## 2. Define boundaries by capability and data

- **Capability:** “This service owns order scheduling,” “This one owns drug-substitution logic.”
- **Data:** Prefer one service to own a given dataset (or aggregate). Share via APIs or events, not shared DB writes from many places.
- Avoid “microservices” that are just the monolith split by layer (e.g., “user service” that only does CRUD and every feature still talks to it for everything). Each service should deliver a clear business capability.

## 3. APIs and contracts first

- Before moving logic, define the **contract** (request/response, idempotency, errors).
- Version the API if you need to evolve it (e.g., `v1/order-scheduling`, `v2/drug-substitution`).
- Document and test the contract; then implement behind it. This keeps the monolith and new service interchangeable from the caller’s perspective during the cutover.

## 4. Operate and observe from day one

- **Logging:** Structured logs with request/correlation IDs so you can trace a flow across services.
- **Metrics:** Latency, error rate, throughput per operation.
- **Alerts:** On error rate, latency SLOs, and dependency failures.

When something breaks (and it will), you need to know whether it’s the monolith, the new service, or the integration.

## 5. Accept temporary duplication and integration complexity

- During migration, you often have **two implementations** of the same capability (monolith + new service). That’s okay for a while.
- You may need **adapters** or **orchestration** (e.g., Step Functions) to route and coordinate. The goal is to remove them once the monolith path is gone.
- Avoid “perfect” shared libraries that couple all services; prefer small, well-defined client SDKs or open API specs.

## 6. Team and ownership

- Align ownership with service boundaries: one team (or clear owner) per service or slice.
- Migration work should include **runbooks**, **on-call**, and **documentation** so the new service is maintainable.

---

**Summary:** Migrate in small, contract-first slices; own capabilities and data clearly; invest in observability and accept some short-term complexity. That keeps the migration low-risk and reversible while you gradually retire the monolith.
