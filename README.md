# AI-QA API — LLM-Powered Question Answering System

## 📌 Overview
This project is a **JWT-protected Flask API** for **document-based question answering**.  
It allows authenticated users to:
1. Upload documents
2. Store embeddings in **FAISS** (vector database)
3. Ask questions and get answers powered by **OpenAI GPT models** via **RAG (Retrieval-Augmented Generation)**.

---

## Architecture Overview

```mermaid
flowchart TD
    A[User / Client App] -->|Login/Register| B[Flask API]
    B -->|JWT Authentication| C[User DB (SQLite/PostgreSQL)]
    B -->|Upload Document| D[Document Preprocessor]
    D -->|Chunk + Embed| E[FAISS Vector Store]
    B -->|Ask Question| F[Retriever + OpenAI GPT]
    E -->|Top Relevant Chunks| F
    F -->|Final Answer| A
---------
## Key Components

Authentication Layer — JWT-based auth for route protection

Vector Store — FAISS for efficient similarity search

RAG Pipeline — Retrieve → Augment → Generate answers

Modular Design — Blueprints + Factory Pattern
-----
Tech Stack Used
Backend Framework: Flask (Python)

Auth: Flask-JWT-Extended

Database: SQLite (dev) / PostgreSQL (prod) with SQLAlchemy

Vector DB: FAISS

LLM Provider: OpenAI API (Chat + Embeddings)

Deployment: Docker, Render/Railway (optional)
