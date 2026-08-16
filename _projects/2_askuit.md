---
layout: page
title: AskUIT AI Academic Assistant
description: An intelligent multi-agent chatbot combining hybrid retrieval RAG to assist students with university academic procedures and inquiries.
img: assets/img/profile.jpg
importance: 1
category: work
related_publications: false
---

> **Encouragement Prize Winner at SEApp 2025**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-Framework-009688?logo=fastapi&logoColor=white)
![RAG](https://img.shields.io/badge/Architecture-Hybrid%20RAG-orange)
![Multi-Agent](https://img.shields.io/badge/Agent-Multi--Agent-blue)

## Overview

**AskUIT AI Academic Assistant** is an intelligent conversational agent engineered to answer student inquiries about academic rules, schedules, course registration, and administrative procedures at the University of Information Technology (UIT - VNUHCM).

By combining a **Multi-Agent orchestration architecture** with a **Hybrid Search Retrieval-Augmented Generation (RAG)** pipeline, AskUIT delivers accurate, context-grounded, and verifiable responses while minimizing hallucinations.

## Key Features & Achievements

- **Award-winning project:** Awarded Encouragement Prize at **SEApp 2025**.
- **Hybrid Search RAG:** Merges dense vector embeddings with sparse keyword search (BM25) to accurately match Vietnamese academic terminology.
- **Multi-Agent System:** Routes queries to domain-specific agents (e.g., regulations, course metadata, schedules, general inquiry).
- **Verifiable Sources:** Links responses directly back to official university document sources and regulations.

## Technical Architecture

```text
User Inquiry
    │
    ▼
┌───────────────────────────────┐
│     Multi-Agent Router        │
└───────────────┬───────────────┘
                │
                ├───────────► [Academic Regulations Agent]
                ├───────────► [Schedule & Course Agent]
                └───────────► [General Inquiry Agent]
                                        │
                                        ▼
                            ┌──────────────────────┐
                            │  Hybrid RAG Pipeline │
                            │ (Vector + BM25 Search)│
                            └──────────────────────┘
```

## Tech Stack

| Component | Technology |
| --- | --- |
| LLMs / Fine-Tuning | OpenAI / Open-Source LLMs (LoRA fine-tuning) |
| Framework | FastAPI, LangChain / LlamaIndex |
| Search / Vector Store | Qdrant / ChromaDB + BM25 |
| Frontend / API | RESTful API |

## Related Links

- Research Focus: Multi-Agent Systems & RAG
- Institution: University of Information Technology (UIT - VNU-HCM)
