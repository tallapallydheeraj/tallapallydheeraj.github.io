---
layout: post
title: "Clinical Adverse Event Detection with RAG and LLMs"
date: 2025-10-15 10:00:00 -0600
categories: engineering healthcare ai ml python
---

Identifying adverse events in clinical data is critical for **patient safety** and **compliance**. I built a system that combines **retrieval-augmented generation (RAG)** with **large language models (LLMs)** to detect potential adverse events and produce **explainable** outputs—criteria, reasoning, next steps, and confidence—so healthcare teams and auditors can understand and act on each finding.

## Why this matters

- **Patient safety:** Catching adverse events early reduces harm and supports better outcomes.
- **Compliance:** Regulators and internal audit need clear, auditable reasoning—not black-box predictions.
- **Explainability:** Every detection comes with transparent reasoning, which builds trust and supports clinical decision-making.

## Architecture at a glance

The pipeline flows in stages:

1. **Data ingestion** — Structured data (e.g., FHIR QuestionnaireResponse) and unstructured data (contracts, knowledge base) are ingested and preprocessed.
2. **Storage** — Processed data and vector embeddings live in **MongoDB**, which also serves as the vector store for RAG.
3. **Ingestion pipeline** — Chunking, embedding, and optional **PHI redaction**; **LangSmith** can be used for tracing.
4. **Agent service** — Assessment intake and contract validation; **RAG** retrieves relevant chunks from MongoDB; an **LLM** (Azure OpenAI, HuggingFace, or Ollama) evaluates and returns an adverse-event decision with criteria, explanation, reasoning, next steps, and confidence.
5. **API and explainability** — A **FastAPI** REST API serves results and explanations for integration with external systems.

So: **ingestion → storage/embeddings → RAG + LLM (agent) → API + explainability**.

## Tech choices

- **Python 3.8+**, **FastAPI**, **uvicorn** for the API and agent.
- **MongoDB** for both document storage and vector store (RAG).
- **Multiple LLM and embedding providers** — Azure OpenAI, HuggingFace, Ollama — so you can swap models or run locally.
- **Docker** (optional) for containerized deployment.
- **LangSmith** for observability and tracing.

## What I built

- **Agent service** — Handles assessment intake, contract validation, and adverse event detection. It runs the RAG pipeline (retrieve relevant chunks, then call the LLM) and returns structured, explainable results.
- **Ingestion service** — Scripts and utilities for chunking, embedding, and loading data into MongoDB; supports both structured and unstructured healthcare data.
- **PHI redaction** — To reduce risk when feeding data into models.
- **Modular design** — Separate services for ingestion and detection make it easier to update, maintain, and integrate with existing systems.

## Takeaways

- **RAG** improves decision support by grounding the LLM in your actual contracts and knowledge base instead of generic knowledge.
- **Explainability** is non-negotiable in healthcare—every detection should come with clear reasoning for audits and trust.
- **Modularity** (ingestion vs. agent, pluggable LLM/embedding providers) makes the system easier to evolve and deploy.

The project is on GitHub: [ai-clinical-ae-detection](https://github.com/tallapallydheeraj/ai-clinical-ae-detection). You can try the **live app** at [Clinical AE Assessment](https://clinical-ae-agent-bmj4hszpwa-uc.a.run.app/). For a high-level overview and architecture diagram, see the [Projects](/projects/#1-clinical-adverse-event-detection---ai-for-healthcare) page.
