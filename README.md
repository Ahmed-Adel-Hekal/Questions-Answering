# AI-QA API — LLM-Powered Question Answering System

## 📌 Overview
This project is a **JWT-protected Flask API** for **document-based question answering**.  
It allows authenticated users to:
1. Upload documents
2. Store embeddings in **FAISS** (vector database)
3. Ask questions and get answers powered by **OpenAI GPT models** via **RAG (Retrieval-Augmented Generation)**.

---

## Architecture Overview

flowchart TD
    A[User / Client App] -->|Login/Register| B[Flask API] <br>
    B -->|JWT Authentication| C[User DB (SQLite/PostgreSQL)] <br>
    B -->|Upload Document| D[Document Preprocessor] <br>
    D -->|Chunk + Embed| E[FAISS Vector Store] <br>
    B -->|Ask Question| F[Retriever + OpenAI GPT] <br>
    E -->|Top Relevant Chunks| F <br>
    F -->|Final Answer| A <br>
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
