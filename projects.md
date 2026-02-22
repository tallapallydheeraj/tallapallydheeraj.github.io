---
title: Projects
---

<div class="projects-intro">
  <p>Selected work that demonstrates <strong>scalable backend systems, full-stack development, production-ready design, and AI/ML (RAG, LLMs, NLP)</strong>. Each project includes source code and documentation on GitHub; where applicable, live demos and architecture notes are linked.</p>
</div>

---

## 1. Clinical Adverse Event Detection — AI for Healthcare

**Repository:** [github.com/tallapallydheeraj/ai-clinical-ae-detection](https://github.com/tallapallydheeraj/ai-clinical-ae-detection) · **Live app:** [Clinical AE Assessment](https://clinical-ae-agent-bmj4hszpwa-uc.a.run.app/)

A system that helps healthcare teams **identify and understand adverse events** in clinical data. It combines analytics with clear explanations to improve patient safety and support compliance. Built with a modular backend: ingestion pipelines, RAG (retrieval-augmented generation), and LLM-based detection with explainable outputs.

### Tech Stack
**Backend:** Python 3.8+, FastAPI, uvicorn · **Data:** MongoDB (vector store, RAG) · **AI/ML:** RAG, LLMs (Azure OpenAI, HuggingFace, Ollama), embeddings · **Ops:** Docker (optional), LangSmith tracing

### What It Does
- Detects potential adverse events in clinical data (e.g., FHIR QuestionnaireResponse, contract/knowledge-base data)
- Produces **explainable** outputs: criteria, reasoning, next steps, and confidence
- Ingests structured and unstructured healthcare data with chunking and vector embeddings
- Supports **PHI redaction** and multiple LLM/embedding providers
- Serves results via REST API for integration with external systems

### Why It Matters
- **Healthcare domain:** Patient safety, compliance, and transparent AI for clinical decision support
- **Explainability:** Every detection comes with clear reasoning for audits and trust
- **Modular design:** Separate ingestion and agent services; production-oriented (env, Docker, security)

### Architecture

<div class="architecture-diagram" style="max-width: 100%; overflow-x: auto;">
<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="720" viewBox="0 0 1200 720" role="img" aria-label="Clinical Adverse Event Detection Architecture" style="max-width: 100%; height: auto;">
  <defs>
    <style>.ae-title{font:700 24px system-ui,sans-serif;fill:#2c3e50}.ae-subtitle{font:500 14px system-ui,sans-serif;fill:#5d6d7e}.ae-label{font:600 13px system-ui,sans-serif;fill:#2c3e50}.ae-text{font:500 12px system-ui,sans-serif;fill:#34495e}.ae-small{font:500 11px system-ui,sans-serif;fill:#7f8c8d}</style>
    <marker id="ae-arrowHead" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="8" markerHeight="8" orient="auto"><path d="M 0 0 L 10 5 L 0 10 z" fill="#16a085"/></marker>
    <linearGradient id="ae-headerGrad" x1="0%" y1="0%" x2="100%" y2="0%"><stop offset="0%" style="stop-color:#16a085;stop-opacity:0.08"/><stop offset="100%" style="stop-color:#2c3e50;stop-opacity:0.08"/></linearGradient>
  </defs>
  <rect width="1200" height="720" fill="#ffffff"/>
  <rect x="0" y="0" width="1200" height="80" fill="url(#ae-headerGrad)"/>
  <text x="600" y="35" class="ae-title" text-anchor="middle">Clinical Adverse Event Detection — AI for Healthcare</text>
  <text x="600" y="60" class="ae-subtitle" text-anchor="middle">Data Ingestion to Storage to RAG and LLM Agent to API and Explainability</text>
  <rect x="100" y="100" width="1000" height="100" fill="#f5f6f7" stroke="#16a085" stroke-width="2" rx="8"/>
  <text x="600" y="125" class="ae-label" text-anchor="middle">1. Data Ingestion</text>
  <rect x="140" y="140" width="280" height="45" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="280" y="162" class="ae-text" text-anchor="middle">Structured data (e.g. FHIR)</text>
  <rect x="460" y="140" width="280" height="45" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="600" y="162" class="ae-text" text-anchor="middle">Unstructured data, contracts</text>
  <rect x="780" y="140" width="280" height="45" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="920" y="162" class="ae-text" text-anchor="middle">Preprocessing, chunking</text>
  <path d="M 600 200 L 600 245" stroke="#16a085" stroke-width="2.5" fill="none" marker-end="url(#ae-arrowHead)"/>
  <rect x="100" y="245" width="1000" height="90" fill="#eef0f2" stroke="#16a085" stroke-width="2" rx="8"/>
  <text x="600" y="270" class="ae-label" text-anchor="middle">2. Storage — MongoDB (vector store for RAG)</text>
  <rect x="340" y="285" width="520" height="35" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="600" y="307" class="ae-text" text-anchor="middle">Processed data and embeddings (optional PHI redaction)</text>
  <path d="M 600 335 L 600 380" stroke="#16a085" stroke-width="2.5" fill="none" marker-end="url(#ae-arrowHead)"/>
  <rect x="100" y="380" width="1000" height="90" fill="#f5f6f7" stroke="#16a085" stroke-width="2" rx="8"/>
  <text x="600" y="405" class="ae-label" text-anchor="middle">3. Ingestion Pipeline — Chunking, embeddings, LangSmith tracing</text>
  <path d="M 600 470 L 600 515" stroke="#16a085" stroke-width="2.5" fill="none" marker-end="url(#ae-arrowHead)"/>
  <rect x="100" y="515" width="1000" height="110" fill="#eef0f2" stroke="#16a085" stroke-width="2" rx="8"/>
  <text x="600" y="540" class="ae-label" text-anchor="middle">4. Agent Service (RAG + LLM)</text>
  <rect x="140" y="555" width="220" height="55" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="250" y="578" class="ae-text" text-anchor="middle">Assessment intake, contract validation</text>
  <rect x="400" y="555" width="220" height="55" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="510" y="578" class="ae-text" text-anchor="middle">Retrieval (RAG) from MongoDB</text>
  <rect x="660" y="555" width="220" height="55" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="770" y="578" class="ae-text" text-anchor="middle">LLM (Azure OpenAI, HuggingFace, Ollama)</text>
  <rect x="920" y="555" width="160" height="55" fill="#ffffff" stroke="#16a085" stroke-width="2" rx="6"/>
  <text x="1000" y="578" class="ae-text" text-anchor="middle">AE detection, reasoning</text>
  <path d="M 600 625 L 600 665" stroke="#16a085" stroke-width="2.5" fill="none" marker-end="url(#ae-arrowHead)"/>
  <rect x="100" y="665" width="1000" height="45" fill="#f5f6f7" stroke="#16a085" stroke-width="2" rx="8"/>
  <text x="600" y="690" class="ae-label" text-anchor="middle">5. API and Explainability — FastAPI, REST, explainable outputs for compliance</text>
</svg>
</div>

---

## 2. Trade System — Order Matching Platform

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

![Trade System architecture]({{ '/assets/images/trade-system-architecture.svg' | relative_url }})

---

## 3. Payment Project — UPI-Style Application

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

## 4. BugHound — Bug Tracking System

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

![Bug Tracker RBAC]({{ '/assets/images/bug-tracker-rbac.svg' | relative_url }})

---

## 5. Cloud & Serverless Systems (Professional Work)

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
![UI → API Gateway → Gateway Lambda (BFF) → Step Functions / Services]({{ '/assets/images/hs-architecture.svg' | relative_url }})

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

## 6. Hospital Appointment System — Appointment Management Platform

**Repository:** [github.com/tallapallydheeraj/Hospital-Appointment](https://github.com/tallapallydheeraj/Hospital-Appointment)

A **Python-based hospital appointment management system** that simulates appointment booking workflows, patient scheduling, and administrative operations for healthcare facilities.

### Tech Stack
**Backend:** Python 3 · **Data:** SQLite database

### What It Does
- Manages patient appointments with scheduling and booking capabilities
- Handles patient records and appointment history
- Provides administrative functions for appointment management
- Stores and retrieves appointment data using SQLite database

### Why It Matters
- **Domain knowledge:** Healthcare operations and appointment workflows
- **Data persistence:** SQLite database integration for reliable data storage
- **Python proficiency:** Demonstrates backend development with Python
- **Real-world application:** Practical system for healthcare appointment management

---

## 7. Sentiment Analysis — Twitter Dataset Analysis

**Repository:** [github.com/tallapallydheeraj/Sentiment-Analysis](https://github.com/tallapallydheeraj/Sentiment-Analysis)

A **machine learning project** that performs sentiment analysis on Twitter datasets, classifying tweets as positive, negative, or neutral using data science and NLP techniques.

### Tech Stack
**Language:** Python · **Tools:** Jupyter Notebook · **Data:** CSV datasets (train/test tweets)

### What It Does
- Analyzes Twitter data to determine sentiment (positive, negative, neutral)
- Processes and preprocesses tweet data for machine learning
- Implements sentiment classification models
- Evaluates model performance on test datasets

### Why It Matters
- **Data science:** Machine learning and NLP application
- **Research:** Survey-level analysis of sentiment analysis techniques
- **Python ecosystem:** Jupyter Notebooks for exploratory data analysis
- **ML pipeline:** Data preprocessing, model training, and evaluation

---

## 8. Library Management System — Java Application

**Repository:** [github.com/tallapallydheeraj/Library-Management-System](https://github.com/tallapallydheeraj/Library-Management-System)

A **Java-based library management application** for managing books, members, borrowing, and returns in a library system.

### Tech Stack
**Backend:** Java

### What It Does
- Manages library inventory (books, authors, categories)
- Handles member registration and management
- Tracks book borrowing and return operations
- Maintains records of library transactions

### Why It Matters
- **Java expertise:** Object-oriented design and Java application development
- **System design:** Complete application lifecycle from design to implementation
- **Data management:** Efficient handling of library operations and records
- **Full application:** End-to-end system demonstrating software engineering principles

---

## What These Projects Show

| Area | Demonstrated In |
|------|------------------|
| **Backend & APIs** | Clinical AE Detection, Trade System, Payment Project, BugHound, Hospital Appointment, Library Management System, Cigna platform |
| **Full-stack** | Trade System, Payment Project, BugHound |
| **Data & correctness** | Order matching, payments, bug lifecycle, workflow state, appointment scheduling, library operations, AE detection |
| **Security & compliance** | SDN checks, RBAC, validation, auditability, PHI redaction |
| **Cloud & scale** | AWS serverless, EKS, Terraform, observability |
| **Data Science & ML** | Clinical AE Detection (RAG, LLM, NLP), Sentiment Analysis (NLP, machine learning, data analysis) |
| **Python development** | Clinical AE Detection, Hospital Appointment, Sentiment Analysis |
| **Java development** | Trade System, Payment Project, BugHound, Library Management System |
| **Healthcare & AI** | Clinical AE Detection (explainable adverse event detection), Cigna platform |
| **AI-assisted dev** | Cigna platform (faster delivery, quality-focused) |

---

*For resume, experience details, and contact information, see the [Resume](resume.md) and [Home](index.md) pages.*
