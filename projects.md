---
title: Projects
---

Selected work that demonstrates **scalable backend systems, full-stack development, and production-ready design**. Each project includes source code and documentation on GitHub.

---

## 1. Trade System — Order Matching Platform

**Repository:** [github.com/tallapallydheeraj/Ordermatching](https://github.com/tallapallydheeraj/Ordermatching)

A full-stack **trading application** where buy and sell orders are matched by **quantity and price**, and executed when criteria align. Built with a clear separation between frontend and backend for maintainability and scale.

### Tech Stack
**Backend:** Java, Spring Boot · **Frontend:** JavaScript, TypeScript, HTML, CSS

### What It Does
- Accepts and validates orders (quantity, cost, side)
- Matches orders based on quantity and stock price
- Executes and records trades with transactional consistency
- Exposes APIs for order management and trade history

### Why It Matters
- **Correctness:** Order-matching logic handles partial fills and edge cases
- **Architecture:** RESTful APIs, layered design, and relational persistence
- **Observability:** Structured for analytics and real-time dashboards

### Architecture
![Trade System architecture](/assets/images/trade-system-architecture.png)

---

## 2. Payment Project — UPI-Style Application

**Repository:** [github.com/tallapallydheeraj/Payment-Project](https://github.com/tallapallydheeraj/Payment-Project)

A **UPI-style payment application** with overdraft support and **SDN (Specially Designated Nationals) list checks** to block restricted users and comply with financial controls.

### Tech Stack
**Backend:** Java, Spring Boot · **Frontend:** TypeScript, HTML, CSS, JavaScript

### What It Does
- Processes payments in a UPI-like flow
- Supports **overdraft** within defined limits
- Integrates **SDN list** checks to block sanctioned entities
- Enforces validation, security, and auditability

### Why It Matters
- **Domain:** Real-world payments, compliance, and risk controls
- **Full-stack:** End-to-end flow from UI to backend and data layer
- **Security-conscious:** Access control and sanctioned-party blocking

---

## 3. BugHound — Bug Tracking System

**Repository:** [github.com/tallapallydheeraj/BugHound](https://github.com/tallapallydheeraj/BugHound)

A **bug tracking system** to log, triage, and resolve defects—and reduce recurrence through structured workflows and searchable history.

### Tech Stack
**Backend:** Java, Spring Boot · **Frontend:** JavaScript · **Data:** Relational database

### What It Does
- Tracks bugs across products, releases, and functional areas
- Role-based access for admins, developers, and testers
- Search, filter, and lifecycle workflows (e.g., New → In Progress → Resolved)
- Optional attachments (screenshots, logs) for context

### Why It Matters
- **Lifecycle management:** From report to resolution with clear state transitions
- **Scalable data model:** Supports filtering and reporting at scale
- **Security:** RBAC and validation for data quality and access control

### RBAC Model
![Bug Tracker RBAC](/assets/images/bug-tracker-rbac.png)

---

## 4. Cloud & Serverless Systems (Professional Work)

At **Cigna (Evernorth / Accredo)**, I build and operate a **cloud-native orchestration platform** for specialty pharmacy workflows.

### Tech Stack
AWS API Gateway, Lambda (Golang, Java, Node.js), Step Functions (JSONata), EKS, DynamoDB, MongoDB, DB2, Redis, S3, SSM Parameter Store, Secrets Manager, IAM/KMS, Terraform, CloudWatch, Dynatrace, Splunk

### What It Does
- Exposes **product APIs** behind an **API Gateway (HS Gateway)** for internal and partner consumers
- Implements a **Gateway Lambda (BFF)** behind the gateway:
  - If logic is simple, the Gateway Lambda **returns the response directly** to the UI
  - If logic is complex, it starts **Step Functions** workflows that orchestrate multiple downstream calls using **JSONata** transformations and branching
- Built a **common API Lambda layer** used by workflows and services: Parameter Store for API config, DynamoDB-driven custom error messages, exception handling, multi-host and optional per-API auth, all content types, S3 offload for responses >256 KB, and custom response-type handling
- Uses service Lambdas + data stores to support workflows like patient data & prescriptions, order scheduling, drug substitution, refills, onboarding
- Uses a dedicated Lambda for **MongoDB CRUD** (connects to MongoDB and performs create/read/update/delete operations)
- Runs containerized services on **Amazon EKS** for workloads that need Kubernetes orchestration
- Manages multi-environment infrastructure via Terraform
- Monitors and debugs with CloudWatch, Dynatrace, and Splunk
- Uses **AI-assisted development tools** (e.g., Copilot, Cursor) to speed up implementation and refactoring while keeping quality high
- Enabled **automatic GitHub Copilot review on every PR**, with custom instructions for consistent, faster code reviews

### Why It Matters
- **Production scale:** Critical healthcare operations with correctness and reliability
- **Modern stack:** Serverless, EKS, event-driven, infrastructure-as-code
- **End-to-end ownership:** Design, implementation, and operations
- **Velocity:** AI tools used thoughtfully to deliver faster without sacrificing standards

### Architecture Overview
![UI → API Gateway → Gateway Lambda (BFF) → Step Functions / Services](/assets/images/hs-architecture.svg)

**High-level layers**
1. **User Interaction Layer:** Users/Patients, Workspace/CRM Portal (login, scheduling, verification)
2. **Integration & Communication:** Outbound/Inbound communication (Genesys, PCAS), event handlers / screen pop
3. **Frontend Delivery:** CloudFront/S3 for static modules, user version/config management
4. **API Gateway Layer:** HS Gateway (API Gateway) routing to backend endpoints (Person, Prescription, Encounter, Order, etc.)
5. **Backend Services:** Gateway Lambda (BFF) and (as needed) Step Functions with JSONata; shared Common API Lambda; Parameter Store; DynamoDB
6. **Data Layer:** MongoDB/DB2 for transactional/config data, Redis cache for performance
7. **Analytics & Reporting:** Databricks/S3 data lake and Spark jobs
8. **Monitoring & Security:** IAM/KMS/Secrets Manager, CloudWatch/Dynatrace/Splunk
9. **External Integrations:** Okta for identity/access; legacy event systems

---

## What These Projects Show

| Area | Demonstrated In |
|------|------------------|
| **Backend & APIs** | Trade System, Payment Project, BugHound, Cigna platform |
| **Full-stack** | Trade System, Payment Project, BugHound |
| **Data & correctness** | Order matching, payments, bug lifecycle, workflow state |
| **Security & compliance** | SDN checks, RBAC, validation, auditability |
| **Cloud & scale** | AWS serverless, EKS, Terraform, observability |
| **AI-assisted dev** | Cigna platform (faster delivery, quality-focused) |

---

*For resume, experience details, and contact information, see the [Resume](resume.md) and [Home](index.md) pages.*
