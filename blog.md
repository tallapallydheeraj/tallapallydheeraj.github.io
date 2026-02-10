---
layout: page
title: Blog
permalink: /blog/
---

Engineering notes on **serverless design, APIs, and migration** — things I’ve learned building and operating cloud-native systems.

---

## Posts

**[Handling Large Payloads in AWS Step Functions](/2025/02/07/handling-large-payloads-aws-step-functions.html)**  
*Feb 7, 2025* — How to stay under Step Functions’ 256 KB limit using S3 references, trimming output, and chunking.

**[Designing Reusable Lambda APIs](/2025/02/08/designing-reusable-lambda-apis.html)**  
*Feb 8, 2025* — A pattern for a generic API Lambda layer so multiple workflows can call downstream services without duplicating auth, retries, and logging.

**[Monolith to Microservices — Migration Lessons](/2025/02/09/monolith-to-microservices-migration-lessons.html)**  
*Feb 9, 2025* — Strangler fig, boundaries, contracts, and observability when moving from a monolith to microservices.

---

*More posts as I document patterns and lessons from production systems.*
