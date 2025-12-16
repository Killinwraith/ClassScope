# Personal Multi-Class Neural Study System

## 1. Overall Goal of the Application

The goal of this application is to build a **personal, class-aware neural study system** that allows users to:

* Create and manage **multiple classes/courses** (e.g., Class A, B, C, D, E)
* Upload **lecture materials per class** (PDFs, slides, notes)
* Automatically parse, embed, and store these materials in a **class-isolated neural memory**
* Study using a **Retrieval-Augmented Generation (RAG)** interface that:

  * Answers questions using *only* the selected class’s lecture notes
  * Generates quizzes, tests, and exam-style questions per class
  * Provides explanations grounded strictly in uploaded materials

Key design principle:

> **Each class acts as its own knowledge universe** — no unintended information leakage between classes.

This system is intended for **serious academic use**, exam preparation, and as a **portfolio-quality engineering + ML project**.

---

## 2. Core Functional Requirements

### User & Class Management

* User can create, rename, and delete classes
* Each class maintains its own:

  * Uploaded documents
  * Embeddings
  * Vector database / namespace

### Document Ingestion

* Accept common academic formats:

  * PDF
  * PPT/PPTX
  * DOCX
  * TXT
* Extract clean text
* Preserve metadata (class name, lecture number, topic, section headers)

### Neural Knowledge Representation

* Convert lecture text into **vector embeddings**
* Store embeddings in a **class-scoped vector database**
* Support efficient similarity search (top-k retrieval)

### RAG-Based Study Interface

* User selects a class before querying
* System retrieves only relevant chunks from that class
* LLM generates responses strictly from retrieved content
* If information is missing, system explicitly states so

### Testing & Quiz Mode

* Generate:

  * Recall questions
  * Conceptual questions
  * Exam-style problems
* Scope quizzes to:

  * Entire class
  * Specific lectures
  * Specific topics

---

## 3. Minimum Requirements

### 3.1 Knowledge Prerequisites

**Required**:

* Python programming
* Basic linear algebra:

  * Vectors
  * Dot products
  * Norms
* Basic machine learning concepts:

  * Embeddings
  * Similarity metrics

**Recommended (for deeper understanding)**:

* Transformers and self-attention
* Gradient-based optimization
* Prompt engineering for LLMs
* Basic database design

---

### 3.2 Hardware Requirements

#### Minimum (Development & Prototyping)

* CPU-only machine
* 16 GB RAM recommended
* Local storage for documents and embeddings

#### Recommended (Advanced / Fine-Tuning)

* NVIDIA GPU (8–16 GB VRAM)
* CUDA-compatible environment

> Note: The core RAG system does **not** require a GPU.

---

## 4. Recommended Tech Stack

### Backend & Infrastructure

* **Language**: Python
* **API Framework**: FastAPI
* **Authentication**: Basic JWT or session-based auth
* **Database (relational)**: PostgreSQL or SQLite

### Document Processing

* PyPDF2 / pdfplumber (PDF)
* python-pptx (slides)
* python-docx (Word files)

### Neural & ML Components

* **Embedding Models**:

  * SentenceTransformers
  * OpenAI embeddings (optional)
* **Vector Database**:

  * FAISS (local)
  * Chroma (local or persistent)

### Reasoning Layer

* LLM options:

  * OpenAI GPT models
  * Local models (Mistral, LLaMA via Ollama)

### Frontend (Optional but Recommended)

* Streamlit (fast prototyping)
* React + REST API (production-style)

---

## 5. System Architecture Overview

```
User
 ↓
Class Selector
 ↓
Class-Specific Vector DB
 ↓
Retriever (Top-k)
 ↓
LLM (RAG Prompt)
 ↓
Answer / Quiz / Explanation
```

Each class maintains **logical and data isolation** at the vector level.

---

## 6. Recommended Order to Build the System

### Phase 1 — Core Foundations

1. Implement user + class abstraction (even if single-user at first)
2. Create document upload + text extraction pipeline
3. Implement text chunking and metadata tagging

### Phase 2 — Neural Memory

4. Generate embeddings for chunks
5. Store embeddings in a **class-specific vector index**
6. Implement similarity search (top-k retrieval)

### Phase 3 — RAG Study Interface

7. Connect retriever to an LLM
8. Enforce strict class-scoped prompts
9. Build Q&A interface

### Phase 4 — Quiz & Testing Engine

10. Generate quizzes from retrieved chunks
11. Support lecture- and topic-specific tests
12. Add answer explanations grounded in notes

### Phase 5 — Advanced Enhancements (Optional)

13. Student performance tracking
14. Adaptive difficulty quizzes
15. Fine-tune embeddings or LLMs per domain

---

## 7. Stretch Goals / Future Extensions

* Fine-tuned embedding models per course
* Contrastive learning to separate similar classes
* Concept graphs (GNNs) for prerequisite tracking
* Multi-user deployment
* Exportable study guides and summaries

---

## 8. Final Notes

This project combines:

* Software engineering
* Applied machine learning
* Neural information retrieval
* Educational tooling

It is suitable as:

* A capstone project
* A serious personal study tool
* A strong ML + systems portfolio piece

---

**End of Document**
