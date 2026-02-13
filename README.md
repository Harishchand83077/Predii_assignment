# Vehicle Specification Extraction from Service Manual

## Overview

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline to extract structured vehicle specifications such as torque values, fluid capacities, and part numbers from large automotive service manuals (PDF).  

It is built with **LangGraph orchestration**, **local embeddings**, and **vector-based retrieval**, and supports free-tier or local LLMs like **Groq Llama 3** or **Gemini**.  

The system is designed to be **modular, robust, and production-ready**, handling PDFs with hundreds of pages efficiently.

---

##  Architecture Flow
                 ┌────────────────────┐
                 │   Service Manual    │
                 │       PDF           │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │  PDF Text Extraction│
                 │  - PyMuPDF          │
                 │  - pdfplumber       │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │    Chunking Layer   │
                 │  - Section-aware    │
                 │  - Procedure/Table  │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Embedding & Vector │
                 │    Database (FAISS)│
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │     LangGraph       │
                 │   Orchestration     │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ LLM Extraction      │
                 │ - Groq / Gemini     │
                 │ - Structured JSON   │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │   JSON Output       │
                 │ - component         │
                 │ - spec_type         │
                 │ - value             │
                 │ - unit              │
                 └────────────────────┘

---

##  Dependencies

- **PDF Parsing**: `PyMuPDF`, `pdfplumber`
- **Embeddings**: `sentence-transformers` (e.g., `all-MiniLM-L6-v2`)
- **Vector DB**: `faiss-cpu`
- **LLM APIs**: `Groq` or `Gemini` (free tier or local)
- **Pipeline orchestration**: `LangGraph`
- **Validation & data**: `pydantic`
- **Utilities**: `numpy`, `json`, `re`

---

##  Requirements

```text
pymupdf
pdfplumber
sentence-transformers
faiss-cpu
langgraph
pydantic
groq  # if using Groq
google-generativeai  # if using Gemini
numpy



