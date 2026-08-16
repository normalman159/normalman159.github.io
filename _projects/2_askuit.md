---
layout: page
title: AskUIT AI Academic Assistant
description: An intelligent multi-agent chatbot combining hybrid retrieval RAG to assist students with university academic procedures and inquiries.
img: assets/img/projects/2_project_cover.png
importance: 1
category: work
related_publications: false
---

> **Encouragement Prize Winner at SEApp 2025**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-Framework-009688?logo=fastapi&logoColor=white)
![RAG](https://img.shields.io/badge/Architecture-Hybrid%20RAG-orange)
![Multi-Agent](https://img.shields.io/badge/Agent-Multi--Agent-blue)
[![Demo Video](https://img.shields.io/badge/Watch_Demo-YouTube-red?logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=rfx6GomsOMY)
[![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?logo=github&logoColor=white)](https://github.com/eiyuumiru/AskUIT)
[![Poster](https://img.shields.io/badge/View_Poster-Google_Drive-4285F4?logo=google-drive&logoColor=white)](https://drive.google.com/file/d/1GBmri6AC2KHQ1zGGOlMZdXBGsKRB-kuX/view?usp=sharing)

## Overview

**AskUIT AI Academic Assistant** is an intelligent conversational agent engineered to answer student inquiries about academic rules, schedules, course registration, and administrative procedures at the University of Information Technology (UIT - VNUHCM).

By combining a **Multi-Agent orchestration architecture** with a **Hybrid Search Retrieval-Augmented Generation (RAG)** pipeline, AskUIT delivers accurate, context-grounded, and verifiable responses while minimizing hallucinations.

## Demo Video

See AskUIT in action through the project demo: [watch the YouTube demo](https://www.youtube.com/watch?v=rfx6GomsOMY).

## Project Poster

Explore the complete AskUIT project poster for an overview of its architecture, workflow, and technical implementation: [view the project poster on Google Drive](https://drive.google.com/file/d/1GBmri6AC2KHQ1zGGOlMZdXBGsKRB-kuX/view?usp=sharing).

## Key Features & Achievements

- **Award-winning project:** Awarded Encouragement Prize at **SEApp 2025**.
- **Hybrid Search RAG:** Merges dense vector embeddings with sparse keyword search (BM25) to accurately match Vietnamese academic terminology.
- **Multi-Agent System:** Routes queries to domain-specific agents (e.g., regulations, course metadata, schedules, general inquiry).
- **Verifiable Sources:** Links responses directly back to official university document sources and regulations.

## Technical Architecture

<p align="center">
  <img src="{{ '/assets/img/projects/2_project_workflow.jpg' | relative_url }}" alt="AskUIT RAG workflow" style="max-width: 100%;">
</p>

AskUIT follows an **agentic RAG architecture** composed of three main building blocks:

1. **RAG Service** — Real-time query processing backend (FastAPI + LangChain) that orchestrates multi‑agent reasoning, tool calling, and response generation.
2. **Data Ingestion Pipeline** — Offline pipeline that loads, chunks, embeds, and indexes academic PDF documents into a vector database for semantic retrieval.
3. **LLM Gateway & API Provider Layer** — Abstraction layer (LiteLLM Router + Gateway) that normalizes and routes LLM/embedding requests to multiple inference providers (Groq, FPT Cloud) for resilience and model diversity.

### Runtime Query Flow (RAG Service)

```text
(1) Send Query        : User → API (FastAPI)
(2) Check Valid Input  : API → Guardrails (input validation & safety)
(3) Send                : Guardrails → Generator (LangChain Agent)
(4) Tool Calling        : Generator → [Major Analysis | Search | Retrieval]
(5) Load History         : Generator → History (conversation memory)
(6) Receive               : Generator → Guardrails (output validation & safety)
(7) Response               : API → User
```

**Step‑by‑step:**
1. The user submits a query from the client (web/mobile) to the FastAPI endpoint.
2. FastAPI validates the input and forwards it to **Guardrails** for safety checks (prompt injection, toxicity).
3. Clean input reaches the **Generator** — a LangChain agent equipped with **tool‑calling** capabilities.
4. The agent decides which tools to invoke:
   - **Major Analysis** — internal reasoning module with evaluation checklist for deep query understanding.
   - **Search** — calls **Tavily API** for up‑to‑date web information when internal knowledge is insufficient.
   - **Retrieval** — queries **Qdrant VectorDB** for semantically relevant document chunks.
5. In parallel, the agent loads conversation **History** to maintain multi‑turn context.
6. The agent synthesizes tool results and calls an LLM via **LiteLLM** (routed to Groq or FPT Cloud) to produce the final answer, which passes back through Guardrails for output safety.
7. FastAPI returns the validated response to the user.

### Data Ingestion Workflow (Offline)

```text
PDF Raw Data → Loading → Chunking → Embedding → Storing → Qdrant VectorDB
```

- **Loading & Chunking:** `Unstructured` extracts and splits PDF content into semantically coherent chunks.
- **Embedding:** Each chunk is embedded via LiteLLM → API Provider (embedding models).
- **Storing:** Vectors + metadata are persisted in **Qdrant** for low‑latency semantic search at query time.

## Tech Stack

| Component | Technology | Role |
| --- | --- | --- |
| **Backend API** | FastAPI (Python) | High‑performance async REST API, auto OpenAPI docs, request validation |
| **Orchestration Framework** | LangChain | Agent framework, tool calling, memory management, RAG pipeline orchestration |
| **Input/Output Safety** | Guardrails | Input validation, output filtering, prompt‑injection & toxicity protection |
| **Vector Database** | Qdrant | High‑performance vector similarity search, metadata filtering, payload storage |
| **Web Search Tool** | Tavily API | Real‑time web search for factual grounding when internal KB is insufficient |
| **Data Parsing / Chunking** | Unstructured | PDF extraction, intelligent chunking, metadata preservation |
| **LLM Gateway** | LiteLLM (Router + Gateway) | Unified LLM/embedding interface, load‑balancing, fallback, provider abstraction |
| **Inference Providers** | Groq (LPU), FPT Cloud | High‑throughput LLM inference, model diversity, geo‑redundancy |
| **Session Memory** | Custom History Store | Conversation history per session for multi‑turn context |
| **Reasoning Module** | Major Analysis (checklist‑based) | Structured reasoning & insight generation for complex academic queries |


## Related Links

- Research Focus: Multi-Agent Systems & RAG
- Institution: University of Information Technology (UIT - VNU-HCM)
