---
layout: post
title: "Handling Large Payloads in AWS Step Functions"
date: 2025-02-07 10:00:00 -0600
categories: engineering aws serverless
---

At Cigna we hit the **256 KB limit** when our specialty pharmacy workflows passed full patient and prescription data (including order-scheduling and drug-substitution payloads) through multiple steps. In some flows we were carrying around **~2 MB of data**—many fields and nested content that downstream states never used. After moving to S3 references and trimming each state’s output to only what the next step needed, we got payloads under 256 KB: **roughly 80–90% reduction** in state size. Here’s the approach that worked.

## The problem

- Each state’s **input** and **output** count toward the limit.
- Passing the same large object through many states multiplies the effective size.
- Often a big share of the payload is **unused**—optional fields, verbose metadata, or content that only one step needs but the whole workflow was carrying. Trimming that alone can cut size sharply.
- Failures show up as `States.DataLimitExceeded` or similar.

## Approaches that work

**1. Pass references, not payloads**

Store the full payload in **S3** or **DynamoDB**, and pass only an identifier through the state machine:

- State 1: Write payload to S3, output `{ "bucket": "...", "key": "..." }`.
- Later states: Call a Lambda that reads from S3, does work, and returns a small result (e.g., status, IDs).
- Next states only pass those small results.

**2. Trim at each step**

If you must keep some data in the state:

- Each Lambda returns only what the **next** state needs (IDs, status, errors).
- Use **JSONata** (or Lambda code) to drop fields you don’t need before passing to the next state.
- Avoid re-outputting the entire incoming payload.

**3. Chunk long-running work**

For large batches:

- One state writes the batch to S3/DynamoDB and outputs a **job ID** and maybe **chunk count**.
- Use **Map** (or a loop) to process chunks; each iteration gets a small input (e.g., chunk index, job ID).
- A final state aggregates results (or writes to a store) and returns a short summary.

## Practical checklist

- Store large data in S3/DynamoDB; pass keys/IDs through the workflow.
- Design each state’s output to be minimal.
- Use **ResultPath** and **Parameters** to avoid copying the whole input into the output.
- Monitor state payload sizes in CloudWatch or X-Ray if you’re close to the limit.

Doing this keeps workflows within limits, reduces cost, and makes debugging easier because state data stays small and readable.
