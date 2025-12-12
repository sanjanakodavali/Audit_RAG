# AuditRAG

**AuditRAG** is a minimal **LangChain + ChromaDB** Retrieval-Augmented Generation (RAG) starter that:
1) builds a local Chroma vector database from your documents, and  
2) answers questions by retrieving relevant chunks and sending them to an LLM.

---

## What’s Inside

- `create_database.py` — ingests documents and creates/persists a ChromaDB index
- `query_data.py` — queries the database and prints an answer + supporting context (depending on your code)

---

## Prerequisites

- Python 3.9+ recommended  
- An OpenAI API key (set as an environment variable)

> **Environment variable**
- `OPENAI_API_KEY` must be set for querying (and sometimes embedding), depending on your configuration.

---

## Setup

### 1) Create a virtual environment (recommended)

**macOS / Linux**
```bash
python -m venv .venv
source .venv/bin/activate
