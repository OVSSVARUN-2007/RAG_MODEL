# Custom RAG Engine

**A Retrieval-Augmented Generation system built from scratch using Python.**

Custom RAG Engine is a modular AI engineering project designed to retrieve relevant information from documents and generate grounded, context-aware answers using Large Language Models (LLMs).

The goal is to understand and implement the core components of RAG—including document ingestion, chunking, embeddings, similarity search, retrieval, context construction, generation, and evaluation—without relying on high-level RAG orchestration frameworks such as LangChain or LlamaIndex.

> **Project status:** Under development 🚧

## 🎯 Objectives

- Build a modular RAG pipeline from the ground up.
- Implement custom document processing and chunking strategies.
- Understand embeddings, vector representations, and similarity search.
- Develop dense and hybrid retrieval mechanisms.
- Generate answers grounded in retrieved document passages.
- Provide source citations for generated responses.
- Evaluate retrieval quality, answer quality, latency, and cost.
- Integrate the engine with a backend API and web interface.
- Develop a testable, secure, and deployable AI application.

## 🏗️ Architecture

The system consists of two primary pipelines.

### 1. Document Ingestion Pipeline

```text
Raw Documents
     |
     v
Document Loading
     |
     v
Text Extraction
     |
     v
Text Cleaning and Preprocessing
     |
     v
Chunking and Metadata Enrichment
     |
     v
Embedding Generation
     |
     v
Indexing and Storage
```

### 2. Query and Generation Pipeline

```text
User Query
     |
     v
Query Processing
     |
     v
Query Embedding
     |
     v
Document Retrieval
     |
     v
Ranking and Context Selection
     |
     v
Prompt Construction
     |
     v
LLM Generation
     |
     v
Citation and Grounding Validation
     |
     v
Answer with Sources
```

## 🧠 Core Components

| Component            | Responsibility                                                |
| -------------------- | ------------------------------------------------------------- |
| Document Ingestion   | Load and process supported document formats                   |
| Text Processing      | Clean extracted text while preserving meaningful structure    |
| Chunking Engine      | Split documents into searchable passages                      |
| Embedding Engine     | Convert text into vector representations                      |
| Vector Retrieval     | Retrieve relevant passages using similarity search            |
| Hybrid Retrieval     | Combine semantic and keyword-based search                     |
| Reranking            | Improve the ordering of retrieved passages                    |
| Context Builder      | Select and organize evidence within the model's context limit |
| Generation Engine    | Generate answers using retrieved evidence                     |
| Citation System      | Associate responses with their source passages                |
| Evaluation Framework | Measure retrieval quality and answer performance              |

## 🛠️ Technology Stack

### Backend and AI

- **Language:** Python
- **API Framework:** FastAPI
- **Data Processing:** NumPy
- **Document Parsing:** PyMuPDF and additional format-specific parsers
- **Embeddings:** Pretrained sentence embedding models
- **Language Models:** API-based or locally hosted LLMs
- **Validation:** Pydantic
- **Testing:** pytest

### Database and Retrieval

- PostgreSQL
- pgvector
- Dense vector similarity search
- BM25 keyword retrieval
- Custom retrieval and ranking logic

### Frontend and Deployment

- React
- TypeScript
- Tailwind CSS
- Docker
- Git and GitHub
- GitHub Actions for CI/CD

_Technologies will be introduced progressively as the project develops._

## 📂 Project Structure

```text
custom-rag/
├── backend/
│   ├── app/
│   │   ├── ingestion/
│   │   ├── embeddings/
│   │   ├── retrieval/
│   │   ├── generation/
│   │   ├── rag/
│   │   ├── evaluation/
│   │   ├── db/
│   │   ├── api/
│   │   └── security/
│   └── tests/
├── frontend/
│   └── src/
├── data/
│   ├── raw/
│   ├── processed/
│   └── evaluation/
├── scripts/
├── docs/
├── .env.example
├── .gitignore
├── docker-compose.yml
└── README.md
```

```text
custom-rag/
├── README.md
├── pyproject.toml
├── .env.example
├── .gitignore
├── docker-compose.yml
│
├── data/
│   ├── raw/                   # Original documents
│   ├── processed/             # Extracted and cleaned data
│   └── evaluation/            # Questions and reference answers
│
├── backend/
│   ├── pyproject.toml
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py            # FastAPI entry point
│   │   ├── config.py          # Environment configuration
│   │   │
│   │   ├── ingestion/
│   │   │   ├── loader.py      # Load documents
│   │   │   ├── parsers.py     # PDF, TXT, DOCX parsing
│   │   │   ├── cleaner.py     # Text preprocessing
│   │   │   ├── chunker.py     # Custom chunking algorithms
│   │   │   ├── metadata.py    # Document and chunk metadata
│   │   │   └── pipeline.py    # Ingestion orchestration
│   │   │
│   │   ├── embeddings/
│   │   │   ├── model.py       # Embedding model interface
│   │   │   └── encoder.py     # Generate document/query vectors
│   │   │
│   │   ├── retrieval/
│   │   │   ├── similarity.py  # Cosine similarity
│   │   │   ├── vector_store.py# Vector storage interface
│   │   │   ├── dense.py       # Dense vector retrieval
│   │   │   ├── bm25.py        # Keyword retrieval
│   │   │   ├── hybrid.py      # Combine retrieval results
│   │   │   ├── reranker.py    # Rerank candidates
│   │   │   └── retriever.py   # Retrieval orchestration
│   │   │
│   │   ├── generation/
│   │   │   ├── prompts.py     # Prompt templates
│   │   │   ├── llm.py         # LLM adapter
│   │   │   ├── context.py     # Context selection and assembly
│   │   │   ├── citations.py   # Source attribution
│   │   │   └── generator.py   # Answer generation
│   │   │
│   │   ├── rag/
│   │   │   ├── query.py       # Query processing
│   │   │   ├── pipeline.py    # End-to-end RAG orchestration
│   │   │   └── schemas.py     # RAG input/output models
│   │   │
│   │   ├── evaluation/
│   │   │   ├── dataset.py     # Load evaluation dataset
│   │   │   ├── retrieval.py   # Recall@k, MRR, nDCG
│   │   │   ├── generation.py  # Answer and citation evaluation
│   │   │   └── benchmark.py   # Run and compare experiments
│   │   │
│   │   ├── db/
│   │   │   ├── session.py     # Database connection
│   │   │   ├── models.py      # Database tables
│   │   │   ├── repository.py  # Persistence operations
│   │   │   └── migrations/    # Database migrations
│   │   │
│   │   ├── api/
│   │   │   ├── routes/
│   │   │   │   ├── documents.py
│   │   │   │   ├── chat.py
│   │   │   │   └── health.py
│   │   │   └── dependencies.py
│   │   │
│   │   └── security/
│   │       ├── auth.py
│   │       └── permissions.py
│   │
│   └── tests/
│       ├── unit/
│       │   ├── test_cleaner.py
│       │   ├── test_chunker.py
│       │   ├── test_similarity.py
│       │   └── test_retriever.py
│       ├── integration/
│       └── test_rag_pipeline.py
│
├── frontend/
│   ├── package.json
│   ├── index.html
│   └── src/
│       ├── main.tsx
│       ├── App.tsx
│       ├── api/
│       │   └── client.ts
│       ├── components/
│       │   ├── ChatWindow.tsx
│       │   ├── Message.tsx
│       │   ├── SourceCitation.tsx
│       │   └── FileUploader.tsx
│       ├── pages/
│       │   ├── Chat.tsx
│       │   ├── Documents.tsx
│       │   └── Settings.tsx
│       └── types/
│           └── index.ts
│
├── scripts/
│   ├── ingest.py
│   ├── build_index.py
│   └── evaluate.py
│
└── docs/
    ├── architecture.md
    ├── api.md
    └── experiments.md
```

## 🚀 Development Roadmap

- [ ] **Phase 1:** Document loading, parsing, and text preprocessing
- [ ] **Phase 2:** Custom chunking algorithms and metadata management
- [ ] **Phase 3:** Embedding generation and cosine similarity
- [ ] **Phase 4:** Top-k retrieval and vector indexing
- [ ] **Phase 5:** End-to-end RAG pipeline and LLM integration
- [ ] **Phase 6:** Source attribution and grounded response generation
- [ ] **Phase 7:** Hybrid search and reranking
- [ ] **Phase 8:** Retrieval and generation evaluation
- [ ] **Phase 9:** FastAPI backend and PostgreSQL integration
- [ ] **Phase 10:** React frontend and document management
- [ ] **Phase 11:** Automated testing, security, and Docker
- [ ] **Phase 12:** Deployment, monitoring, and performance optimization

## 📊 Evaluation Strategy

The system will be evaluated using a dedicated dataset containing questions, reference answers, and relevant source passages.

**Retrieval metrics**

- Recall@k
- Precision@k
- Mean Reciprocal Rank (MRR)
- Normalized Discounted Cumulative Gain (nDCG)

**Generation metrics**

- Answer correctness
- Faithfulness to retrieved evidence
- Answer relevance
- Citation accuracy

**System metrics**

- Query latency
- Document ingestion time
- Token consumption and inference cost
- Error rate and throughput

## 🔒 Engineering Principles

- Modular and testable architecture
- Explicit control over retrieval and generation
- Reproducible experiments and benchmarks
- Source-grounded answers and transparent citations
- Secure document access and input validation
- Separation of core RAG logic from API and UI layers
- No claims of accuracy without evaluation

## 🎓 Learning Outcomes

This project is intended to develop practical knowledge of:

- Natural Language Processing and embeddings
- Information retrieval and ranking algorithms
- Vector search and database integration
- LLM application engineering
- Backend API development
- Full-stack application architecture
- AI evaluation and experimentation
- Testing, deployment, and production reliability

## 📌 Current Status

The project is in its initial development stage. Components will be implemented and evaluated incrementally, beginning with document ingestion and chunking.

## 📄 License

A license will be selected before public release.
