# Lumina Enterprise Knowledge Copilot
### NASSCOM Agentic AI Hackathon — Use Case 2 | Team Lumina

![Python](https://img.shields.io/badge/Python-3.11-blue)
![LangChain](https://img.shields.io/badge/LangChain-LCEL-green)
![ChromaDB](https://img.shields.io/badge/VectorDB-ChromaDB-orange)
![Groq](https://img.shields.io/badge/LLM-Llama3.3_70B-purple)
![License](https://img.shields.io/badge/License-MIT-yellow)

---

## Problem Statement

Large IT services companies struggle with:
- Scattered documentation across PDFs, wikis, and SOPs
- Duplicate support tickets with known resolutions
- Slow onboarding of new engineers (4-8 weeks)
- Knowledge silos across teams

**Result:** Engineers waste 20% of their time searching for information that already exists.

---

## Solution — Lumina Copilot

An Enterprise Knowledge Copilot that:
- Answers internal employee queries instantly
- Retrieves relevant documents using semantic search
- Summarizes content and always cites sources
- Escalates when confidence is low
- Routes tickets to correct departments automatically

---

## Architecture

```
Employee Question
      |
      v
[Query Embedding]  <-- sentence-transformers/all-MiniLM-L6-v2
      |
      v
[ChromaDB Vector Store]  <-- Top-k Semantic Retrieval
      |
      v
[LangChain LCEL Chain]
      |
      v
[Llama 3.3 70B via Groq]  <-- Response Generation
      |
      v
[Source Citation + Escalation Logic]
      |
      v
[Gradio Web Interface]  <-- Employee sees answer
      
      +-- [ReAct Agent Layer] (Bonus)
              |
              |-- Tool 1: DocumentSearch
              |-- Tool 2: TicketClassifier  
              |-- Tool 3: IssueSummarizer
```

---

## Tech Stack

| Component | Technology |
|---|---|
| LLM | Llama 3.3 70B via Groq API |
| Vector Database | ChromaDB |
| Embeddings | sentence-transformers/all-MiniLM-L6-v2 |
| Orchestration | LangChain LCEL |
| Agentic Layer | LangGraph ReAct Agent |
| Web Interface | Gradio |
| Runtime | Google Colab (free) |
| License | MIT — fully open source |

---

## Features

- **RAG Pipeline** — Retrieval Augmented Generation with top-k semantic search
- **Source Citation** — Every answer cites the source document
- **Escalation Logic** — Auto-escalates with team email when confidence is low
- **ReAct Agent** — 3-tool agentic workflow for complex queries
- **Evaluation Metrics** — F1 Score, Precision, Recall measurement
- **Zero Cost** — Runs entirely on free tools (Colab + Groq free tier)
- **Offline Ready** — ChromaDB runs locally, no external DB dependency

---

## Evaluation Results

| Metric | Score |
|---|---|
| Retrieval Precision | 100% |
| Retrieval Recall | 100% |
| F1 Score | 100% |
| Test Cases | 5/5 correct source retrieval |

---

## Quick Start

### 1. Open in Google Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com)

Upload `Lumina_Copilot_FINAL.ipynb` to Google Colab.

### 2. Get Groq API Key (Free)
- Go to [console.groq.com](https://console.groq.com)
- Create account → API Keys → Create Key

### 3. Run All Cells
- Paste your Groq API key in Cell 2
- Runtime → Run all
- Wait ~5 minutes for setup
- Get public demo URL from last cell

---

## Knowledge Base

Currently includes 6 enterprise SOPs:

| Document | Category |
|---|---|
| kubernetes_sop.txt | Infrastructure |
| database_sop.txt | Database |
| security_sop.txt | Security |
| network_sop.txt | Network |
| application_sop.txt | Application |
| onboarding_guide.txt | Onboarding |

---

## Demo

**Live Demo URL:** Generated per session via Gradio share link

**Sample Interaction:**
```
User: PostgreSQL CPU is 90%, help!

Lumina: To resolve the PostgreSQL high CPU issue:
1. Connect: psql -U admin -d production
2. Find slow queries: SELECT pid,query FROM pg_stat_activity WHERE state!=idle
3. Terminate long queries: SELECT pg_terminate_backend(pid)
4. Add index: CREATE INDEX CONCURRENTLY idx ON table(col)
If issue persists, escalate to: dba-team@company.com

Source: SOP: PostgreSQL High CPU
Sources consulted: database_sop.txt, application_sop.txt
```

---

## Project Structure

```
lumina-enterprise-copilot/
|-- Lumina_Copilot_FINAL.ipynb   # Main notebook (run this)
|-- README.md                     # This file
|-- enterprise_docs/              # Knowledge base (auto-created)
|   |-- kubernetes_sop.txt
|   |-- database_sop.txt
|   |-- security_sop.txt
|   |-- network_sop.txt
|   |-- application_sop.txt
|   |-- onboarding_guide.txt
```

---

## Judging Criteria Coverage

| Criteria | Implementation |
|---|---|
| Accuracy & F1 Score | 100% on test suite |
| Technical Soundness | RAG + LCEL + LangGraph |
| Open Source Tools | ChromaDB, Llama3, LangChain |
| Agentic Enhancement | ReAct Agent with 3 tools |
| Ease of Use | One-click Gradio UI |
| Security | No PII sent externally, on-premise ready |
| Scalability | ChromaDB handles millions of vectors |
| Innovation | Source citation + auto-escalation |

---

## Team

**Team Lumina**
- Himanshu Sharma — Technical Specialist
- Globalxperts Networks Pvt. Ltd.
- 10+ Years Experience

---

## License

MIT License — Free to use, modify, and distribute.

---

*Built for NASSCOM Agentic AI Hackathon — AI-Code Sarathi 2026*
