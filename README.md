# RAG Retrieval Workflows

## Overview

This repository contains a series of hands-on Python projects exploring the core components of Retrieval-Augmented Generation (RAG).

The projects build progressively from text preparation and embedding generation to semantic search, lexical retrieval, and hybrid multi-index search.

Together, they demonstrate how information can be transformed, indexed, retrieved, and supplied as relevant context for AI-generated responses.

---

## Projects Included

### 1. Text Chunking

**File:** `Claude_RAG_Text_Chunking_v1.ipynb`

Explores how larger documents can be divided into smaller, usable text segments before retrieval.

Key concepts:

- Text preprocessing
- Document segmentation
- Chunk creation
- Preparing content for retrieval
- RAG pipeline foundations

Chunking is an important first step in a RAG system because retrieval quality depends heavily on how source material is divided and represented.

---

### 2. Text Embeddings

**File:** `Claude_RAG_Text_Embeddings_v1.ipynb`

Demonstrates how text chunks can be converted into numerical vector representations using an embedding model.

Key concepts:

- Text embeddings
- Vector representations
- Embedding APIs
- Semantic representation
- Preparing documents for similarity search

This project introduces the connection between natural-language content and the numerical representations used in semantic retrieval systems.

---

### 3. Vector Search

**File:** `Claude_RAG_Vector_Search_v1.ipynb`

Builds a semantic retrieval workflow using vector similarity.

The workflow:

- Converts documents into embeddings
- Stores document vectors
- Embeds a user query
- Compares the query against stored content
- Retrieves the most semantically relevant information
- Supplies retrieved context to Claude for response generation

Key concepts:

- Semantic search
- Vector similarity
- Query embeddings
- Retrieval ranking
- Context-grounded generation

This project demonstrates how a RAG system can locate information based on meaning rather than exact keyword matches.

---

### 4. BM25 Lexical Search

**File:** `Claude_RAG_BM25_Lexical_Search_v1.ipynb`

Explores keyword-oriented information retrieval using BM25.

Key concepts:

- Lexical search
- Keyword matching
- BM25 ranking
- Term frequency
- Document relevance scoring

Unlike vector search, which focuses on semantic similarity, BM25 emphasizes the presence and importance of specific words and phrases.

This makes lexical retrieval useful when exact terminology, identifiers, or domain-specific wording matters.

---

### 5. Multi-Index Hybrid Search

**File:** `Claude_RAG_Multi_Index_Hybrid_Search_v1.ipynb`

Combines multiple retrieval strategies into a hybrid search workflow.

The project demonstrates how semantic and lexical retrieval methods can complement one another when searching across indexed information.

Key concepts:

- Hybrid retrieval
- Multiple search indexes
- Vector search
- Lexical search
- Result combination
- Retrieval ranking
- Context selection

Hybrid search can improve retrieval quality by balancing semantic meaning with exact keyword relevance.

---

## RAG Workflow

The projects in this repository represent a progressive retrieval pipeline:

```text
Source Text
    ↓
Text Chunking
    ↓
Embeddings
    ↓
Vector Index
    ↓
Semantic Search
```

The repository then expands the retrieval strategy:

```text
                 ┌── Vector Search ──┐
User Query ──────┤                   ├── Relevant Context
                 └── BM25 Search ────┘
                           ↓
                    Hybrid Retrieval
                           ↓
                     Claude Response
```

This progression demonstrates that RAG is not a single technique, but a collection of components that work together to retrieve useful evidence before an AI system generates a response.

---

## Technologies and Concepts

Projects in this repository use or explore:

- Python
- Jupyter Notebook
- Anthropic Claude API
- Voyage AI embeddings
- Vector embeddings
- Semantic similarity
- BM25 lexical retrieval
- Hybrid search
- Retrieval-Augmented Generation
- Environment-variable credential management

---

## API Key Handling

API credentials are loaded from environment variables rather than stored directly in the notebooks.

Example:

```python
from dotenv import load_dotenv
import os

load_dotenv()

api_key = os.getenv("VOYAGE_API_KEY")
```

Local `.env` files containing credentials should never be committed to source control.

---

## Why Compare Retrieval Methods?

Different retrieval approaches solve different problems.

### Semantic Search

Vector retrieval is useful when the wording of a query differs from the wording of the source material but the underlying meaning is similar.

For example:

```text
Query:
"What type of work does this person do?"

Source:
"Software Engineering"
```

Semantic similarity can connect those concepts even without exact keyword overlap.

### Lexical Search

BM25 is useful when exact terms carry important meaning.

Examples include:

- Technical
