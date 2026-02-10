# Projects

This page highlights projects that demonstrate my experience designing
**scalable backend systems, distributed workflows, and full-stack applications**.

---

## Trade System — Stock Order Management Platform

**Tech Stack:** Spring Boot, Angular, MariaDB

### Overview
A full-stack trading platform designed to execute stock orders accurately
based on real-time price and quantity constraints. The system emphasizes
**transactional correctness, scalability, and performance**.

### Architecture & Design
- Spring Boot backend exposing RESTful APIs for order placement and execution
- Relational data model ensuring consistency across orders and transactions
- Angular frontend providing real-time analytical dashboards
- Clear separation of concerns between API, business logic, and persistence layers

### Engineering Highlights
- Implemented precise execution logic to handle edge cases such as partial fills
- Optimized SQL queries to reduce latency under concurrent access
- Designed APIs with idempotency and validation to ensure correctness

---

## Bug Tracking System — Secure Issue Management Platform

**Tech Stack:** Spring Boot, React, MySQL, Tailwind CSS

### Overview
A secure, web-based bug tracking system designed to manage the full lifecycle
of software defects across products and teams.

### Architecture & Design
- Role-Based Access Control (RBAC) for Admins, Developers, and Testers
- Relational schema modeling bugs, products, releases, and functional areas
- Dynamic workflows enforcing validation and data consistency
- Secure authentication and authorization mechanisms

### Engineering Highlights
- Designed scalable schemas supporting advanced search and filtering
- Implemented dynamic forms and validations to enforce data quality
- Supported file attachments such as screenshots and logs

---

## Cloud & Serverless Systems (Professional Work)

At Cigna, I work on a **cloud-native orchestration platform** powering specialty
pharmacy workflows.

### Highlights
- AWS Step Functions coordinating distributed, asynchronous workflows
- Golang and Java Lambda functions handling business logic
- JSONata-based payload transformation inside workflows
- DynamoDB and MongoDB for low-latency data access
- Terraform-managed infrastructure for multi-environment deployments
- CloudWatch and Splunk for monitoring and troubleshooting

---

## What These Projects Demonstrate

- Distributed system design
- Workflow orchestration
- Backend correctness and scalability
- Security-conscious architecture
- Production-readiness
