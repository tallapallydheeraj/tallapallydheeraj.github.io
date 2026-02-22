---
title: Resume
---

## Dheeraj Tallapally
Software Engineer — Backend & Cloud Systems  
Austin, TX  
📧 tallapallydheeraj99@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/tallapally-dheeraj) · [GitHub](https://github.com/tallapallydheeraj)

---

## Professional Summary

Software Engineer with a Master’s degree in Computer Science and experience
designing and operating **cloud-native, distributed backend systems** in
production environments.

Strong background in **AWS serverless architecture, workflow orchestration,
API development, and microservices**, with hands-on experience using
**Golang, Java, Node.js, Python, and Terraform**. Additional expertise in
**data science, machine learning, and AI**—including sentiment analysis, NLP, RAG/LLM applications, and AI-enabled platforms in production.

---

## Professional Experience

### Cigna Health Group (Evernorth / Accredo) — Software Engineering Analyst  
**Austin, TX | Dec 2024 – Present**

- Contribute to the design and development of a **cloud-native orchestration
platform** modernizing specialty pharmacy workflows for patients with complex
and chronic conditions.
- Develop **serverless microservices using AWS Lambda (Golang, Java, Node.js)** to
handle **patient data and prescription lifecycle**, **order scheduling for prescriptions**, **drug substitution** (complex logic for determining the eligibility for substitution), onboarding, and medication refills.
- Design and maintain **AWS Step Functions–based distributed workflows** to
coordinate asynchronous services with retries, state management, and
failure handling.
- Build and support services on **Amazon EKS (Kubernetes)** for containerized
workloads requiring orchestration and scaling.
- Design and develop **product APIs** that expose specialty pharmacy capabilities
to internal and partner systems, with clear contracts, versioning, and documentation; fronted by **API Gateway** and a **Gateway Lambda (BFF)** that either responds directly for simple calls or starts **Step Functions** for complex orchestration.
- Built a **reusable, generic API Lambda layer** with Parameter Store config, DynamoDB-driven error messages, exception handling (including ignoreStatusCode and problem-object wrapping), multi-host and optional per-API auth, all content types (JSON/XML/string), S3 offload for responses >256 KB, and custom response-type handling; reduces duplicated logic across dozens of workflows.
- Use **JSONata** for runtime payload transformation and conditional branching
inside workflow executions.
- Leverage **DynamoDB and MongoDB** for low-latency, schema-flexible data storage
and **Redis caching** to improve performance.
- Use **AI-assisted tooling** to accelerate implementation and reviews while maintaining code quality; configured automated PR review with custom team instructions.
- Provision and manage infrastructure using **Terraform**, enabling consistent
deployments across environments.
- Ensure secure handling of sensitive healthcare data using **IAM, KMS, SSM,
Secrets Manager, and OAuth 2.0**.
- Monitor and troubleshoot production systems using **CloudWatch, Dynatrace, and Splunk**,
improving reliability and observability.
- Collaborate with frontend engineers, architects, and business stakeholders
in an agile environment.

---

### DBS Tech — Full Stack Developer  
**Hyderabad, India | Jul 2021 – Jul 2022**

- Contributed to the modernization of enterprise applications by transitioning monolithic systems to **scalable microservices architecture**.
- Led migration of legacy monolith to **Spring Boot–based microservices**, improving deployment independence, fault isolation, and scalability.
- Designed and implemented **RESTful APIs** with clear contracts and versioning to support internal and external integrations.
- Built responsive frontend applications using **React and Angular**, enabling API-driven user workflows and improved user experience.
- Modeled relational schemas and optimized complex **SQL queries** using **Spring Data JPA** and **MariaDB**, improving performance for high-traffic workflows.
- Implemented **event-driven communication** using **Apache Kafka**, enabling asynchronous service coordination across distributed systems.
- Participated in architectural discussions, sprint planning, peer code reviews, and debugging sessions within an agile team.
- Improved **CI/CD practices** and supported environment deployments to ensure reliable production releases.

---

### Microsoft (via MAQ Software) — Associate Software Engineer  
**Hyderabad, India | Dec 2020 – Jul 2021**

- Worked on enterprise analytics and reporting systems supporting internal operational decision-making.
- Redesigned and optimized **Power BI dashboards**, improving reporting efficiency by **50%** and reducing manual analysis efforts.
- Built data transformation workflows using **Spark SQL**, enabling structured analytics across large datasets.
- Diagnosed and resolved **100+ production data issues**, performing root cause analysis and improving system stability.
- Automated recurring reporting processes to reduce manual intervention and improve data consistency.
- Gained hands-on exposure to **Azure cloud services**, **ML concepts**, and **NLP tooling**, contributing to data-driven experimentation initiatives.
- Collaborated with cross-functional teams to refine reporting requirements and deliver iterative improvements.

---

## Education

**California State University, Long Beach**  
Master of Science in Computer Science  
GPA: 3.5  
Aug 2022 – May 2024

---

## Technical Skills

**Languages:** Java, Golang, Node.js, Python, JavaScript, TypeScript, SQL  
**Cloud:** AWS (Lambda, Step Functions, EKS, DynamoDB, S3, IAM, CloudWatch), Azure Cloud  
**Frameworks:** Spring Boot, React, Angular  
**Data:** MySQL, PostgreSQL, MongoDB, Redis, Kafka, SQLite  
**Data Science & ML:** Jupyter Notebooks, Sentiment Analysis, NLP, RAG, LLMs  
**AI & practices:** AI-assisted development (Copilot, Cursor), automated PR review, explainable AI  
**Infra:** Terraform, Docker, Kubernetes  
**Practices:** Microservices, REST APIs, Distributed Systems, Agile

---

## Projects

**[Clinical Adverse Event Detection — AI for Healthcare](/projects/#1-clinical-adverse-event-detection---ai-for-healthcare)** — RAG and LLM-based system to detect and explain adverse events in clinical data for patient safety and compliance.

**[Trade System — Order Matching Platform](/projects/#2-trade-system---order-matching-platform)** — Full-stack trading app: orders matched by quantity and price with transactional correctness.

**[Payment Project — UPI-Style Application](/projects/#3-payment-project---upi-style-application)** — UPI-like payments with overdraft and SDN list checks for compliance.

**[BugHound — Bug Tracking System](/projects/#4-bughound---bug-tracking-system)** — Role-based bug tracking with workflows, validations, and scalable data models.

**[Cloud & Serverless Systems (Professional Work)](/projects/#5-cloud--serverless-systems-professional-work)** — Cloud-native orchestration platform for specialty pharmacy workflows at Cigna.

**[Hospital Appointment System — Appointment Management Platform](/projects/#6-hospital-appointment-system---appointment-management-platform)** — Python-based appointment management platform for healthcare facilities with SQLite persistence.

**[Sentiment Analysis — Twitter Dataset Analysis](/projects/#7-sentiment-analysis---twitter-dataset-analysis)** — Machine learning project analyzing Twitter datasets using NLP and sentiment classification.

**[Library Management System — Java Application](/projects/#8-library-management-system---java-application)** — Java application for managing library operations, books, members, and transactions.
