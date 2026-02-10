---
layout: post
title: "Designing Reusable Lambda APIs"
date: 2025-01-10 10:00:00 -0600
categories: engineering aws serverless api
---

At Cigna we have **dozens of Step Functions** that need to call services for patient data, prescription and order-scheduling, and drug-substitution logic (which involves complex rules and downstream systems). Rather than duplicate HTTP, auth, and retry logic in every workflow, we built a **reusable API Lambda layer** that routes and invokes based on a small input contract. Over a dozen workflows now use it, and new integrations are a single mapping instead of touching each state machine. Here’s the pattern.

## Why a generic API layer?

- Multiple workflows need to call internal or external APIs (patient data, prescription and order-scheduling, drug-substitution rules, etc.).
- Without a shared layer, each workflow embeds its own HTTP logic, error handling, and retries.
- Changes to auth, timeouts, or logging then have to be repeated everywhere.

A single Lambda (or a small set) that **routes and invokes** based on input keeps all of that in one place. The layer we built supports the following.

## Common API layer capabilities

- **Simple API call** — Single contract (action + payload) for all downstream calls.
- **Exception handling** — When the common API throws, errors are caught and normalized so workflows get a consistent failure shape.
- **ignoreStatusCode** — Option to treat certain HTTP status codes as success (e.g., 202 Accepted) so workflows don’t fail on expected non-2xx responses.
- **Wrap problem object in exception** — Downstream “problem” details (e.g., RFC 7807) are wrapped in a standard exception for consistent handling.
- **API details from Parameter Store** — URLs, timeouts, and feature flags are read from **SSM Parameter Store** so we can change config without redeploying.
- **Custom error messages** — Support for overriding or supplementing error messages returned to the caller.
- **Error messages from DynamoDB** — Custom error messages are fetched from **DynamoDB** with placeholder replacement (e.g., `{code}`, `{detail}`) so we can tailor messages per environment or product.
- **Multiple hosts and default host authentication** — Supports several hosts with a default auth scheme; per-call overrides when needed.
- **API-level custom authentication (optional)** — Some integrations use different auth (e.g., API keys, custom headers); the layer supports optional per-API auth.
- **URL encoding** — Request params and paths are correctly encoded for each downstream.
- **All content types** — For XML and JSON, the layer parses and returns **JSON**; for other content types it returns a **string**, so Step Functions always get a consistent shape and stay within payload limits when possible.
- **Large responses (>256 KB)** — If the downstream response exceeds the Step Functions state size limit, the layer writes the body to **S3** and returns the **S3 key** so the workflow can pass a reference instead of the raw payload (aligned with [Handling Large Payloads in AWS Step Functions](/2025/07/15/handling-large-payloads-aws-step-functions.html)).
- **Custom response type** — Handles mismatched headers and bodies (e.g., `Content-Type: application/xml` with a JSON body) so we can force the correct parsing and response type per API.

## Design principles

**1. Input as a contract**

Pass a small, stable payload into the layer:

- **Action / operation** (e.g., `schedule_prescription_order`, `evaluate_drug_substitution`).
- **Payload** (or a reference: S3 key, DynamoDB key).
- Optional: **correlation ID**, **tenant**, or **idempotency key**.

The layer translates “action + payload” into the right URL, headers, and body for each downstream.

**2. One place for cross-cutting concerns**

Inside the layer, handle once:

- **Auth:** Resolve tokens (e.g., from SSM/Secrets Manager), attach to requests.
- **Retries:** Exponential backoff, max attempts, and when to fail.
- **Logging:** Log action, duration, status code, and a request ID for tracing.
- **Timeouts:** Set and enforce timeouts so workflows don’t hang.

**3. Output shape that workflows can rely on**

Return a consistent structure, for example:

- `success` (boolean).
- `statusCode` (from downstream).
- `body` or `result` (parsed and trimmed).
- `error` (if failed).

Step Functions (or other Lambdas) can then branch on `success` and use `result` without knowing which service was called.

## Implementation sketch

- **API Gateway → Gateway Lambda (BFF):** UI calls land on API Gateway (HS Gateway) and are routed to a **Gateway Lambda** acting as a backend-for-frontend. For simple endpoints, the Gateway Lambda can validate/compose and return directly.
- **Step Functions (complex flows):** For workflows with more logic (multiple service calls, branching, retries), the Gateway Lambda starts a **Step Functions** execution and relies on JSONata to transform payloads and drive decisions.
- **Common API Lambda:** Step Functions use one “Invoke API” state that calls a reusable **common API Lambda** with `{ "action": "...", "payload": { ... } }`. The Lambda maps `action` → URL/method/auth, calls the downstream API, handles retries/errors, and returns a standard response shape (or an S3 reference for large payloads).
- **New integrations:** Add a new action and mapping in the layer instead of changing every workflow.

## Benefits

- **DRY:** One place for HTTP, auth, retries, and logging.
- **Easier testing:** Mock the layer or the downstream in tests.
- **Easier evolution:** New backends or changes to existing ones are centralized.

The layer stays manageable by keeping routing and invocation in one place, while the capabilities above (Parameter Store, DynamoDB error messages, S3 for large responses, content-type and custom response handling) make it robust enough for dozens of workflows and many downstream APIs without turning it into a monolith.
