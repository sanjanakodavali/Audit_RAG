

# AuditRAG — Audit-Ready Retrieval-Augmented Generation Service

AuditRAG is a production-style RAG service designed for regulated environments. It emphasizes:
- **Traceability** (request IDs, evidence snippets, reproducible runs)
- **Reliability** (health checks, error handling, retries)
- **Evaluation** (precision@k, recall@k, MRR, latency)
- **Deployability** (Docker, Makefile, CI)

> ⚠️ Note: AuditRAG is a portfolio project. It does not contain real customer/bank data.

---

## Architecture (10 lines)

Client → **FastAPI** `/query`  
1) API validates request + assigns `request_id`  
2) Retriever fetches top-k evidence (vector / hybrid)  
3) Evidence returned with `doc_id`, `score`, `snippet`  
4) Generator produces grounded response using retrieved context  
5) Logs capture `request_id`, latency, errors (no PII)  
6) Evaluation harness computes ranking metrics + latency  
7) CI runs tests on every push  
8) Docker builds reproducible runtime  
9) Makefile provides one-command workflows  
10) Designed for audit-friendly observability + repeatability  

---

## Features
- **FastAPI endpoints**: `/health`, `/ingest`, `/query`
- **Request/response schemas** (Pydantic)
- **Evaluation harness**: precision@k, recall@k, MRR, avg latency
- **Structured logging** with request IDs
- **Retries** for transient failures (LLM / vector DB calls)
- **Dockerized deployment**
- **GitHub Actions CI** (pytest)

---

## Project Structure
```text
audit-rag/
  src/auditrag/
    api.py           # FastAPI endpoints
    rag.py           # retrieve() + generate_answer()
    schemas.py       # request/response models
    eval.py          # metrics + evaluation runner
    logging_utils.py # request_id logging
  tests/
  data/
  .github/workflows/
  Dockerfile
  Makefile
  requirements.txt
  README.md

```text
