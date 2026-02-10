# Projects

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
AWS Step Functions, Lambda (Golang, Java, Node.js), EKS, DynamoDB, MongoDB, S3, Terraform, CloudWatch, Splunk

### What It Does
- Develops **product APIs** that expose specialty pharmacy capabilities to internal and partner systems
- Built a **common API Lambda layer** used by many workflows: Parameter Store for API config, DynamoDB for custom error messages, exception handling, multi-host and optional per-API auth, all content types, S3 for responses >256 KB, and custom response-type handling
- Orchestrates distributed, asynchronous workflows (e.g., patient data & prescriptions, order scheduling, drug substitution, refills, onboarding)
- Runs containerized services on **Amazon EKS** for workloads that need Kubernetes orchestration
- Transforms payloads with JSONata inside workflows
- Manages multi-environment infrastructure via Terraform
- Monitors and debugs with CloudWatch and Splunk
- Uses **AI-assisted development tools** (e.g., Copilot, Cursor) to speed up implementation and refactoring while keeping quality high
- Enabled **automatic GitHub Copilot review on every PR**, with custom instructions for consistent, faster code reviews

### Why It Matters
- **Production scale:** Critical healthcare operations with correctness and reliability
- **Modern stack:** Serverless, EKS, event-driven, infrastructure-as-code
- **End-to-end ownership:** Design, implementation, and operations
- **Velocity:** AI tools used thoughtfully to deliver faster without sacrificing standards

### Workflow Overview
![AWS Step Functions flow](/assets/images/aws-step-functions-flow.png)

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
