---
layout: page
title: Blog
permalink: /blog/
---

Engineering notes on **serverless design, APIs, and migration** — things I’ve learned building and operating cloud-native systems.

---

## Posts

**[Designing Reusable Lambda APIs](/2025/01/10/designing-reusable-lambda-apis.html)**  
*Jan 10, 2025* — A pattern for a generic API Lambda layer so multiple workflows can call downstream services without duplicating auth, retries, and logging.

**[Monolith to Microservices — Migration Lessons](/2025/04/30/monolith-to-microservices-migration-lessons.html)**  
*Apr 30, 2025* — Strangler fig, boundaries, contracts, and observability when moving from a monolith to microservices.

**[Handling Large Payloads in AWS Step Functions](/2025/07/15/handling-large-payloads-aws-step-functions.html)**  
*Jul 15, 2025* — How to stay under Step Functions’ 256 KB limit using S3 references, trimming output, and chunking.

---

*More posts as I document patterns and lessons from production systems.*
