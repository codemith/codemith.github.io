---
title: "CosmosPapers — AI-Powered Research Aggregator"
excerpt: "A research discovery platform aggregating 54K+ papers from 15+ top-tier conferences, with semantic search, topic-trend exploration, and an AI Copilot for summaries, Q&A, and BibTeX.<br/><br/>[Visit CosmosPapers →](https://cosmospapers.com)"
collection: portfolio
---

## Overview

CosmosPapers is a full-stack research paper aggregation and discovery platform. It scrapes, indexes, and serves accepted papers from 15+ top-tier AI, Machine Learning, Computer Vision, and Security conferences spanning 2022 to 2026.

**[Live Website](https://cosmospapers.com/)** | **[GitHub](https://github.com/RunWang123/cosmospaper)** 

### Key Features
- **15+ top tier conferences** like CVPR, NeurIPS, ICLR, ICML, ICCV, ECCV, ACM CCS, ACM CHI, USENIX Security, IEEE S&P, IEEE VIS, NDSS, and SIGGRAPH, enabling users to semantically search and find more relevant results.
- **Semantic search** using `BAAI/bge-base-en-v1.5` embeddings and PostgreSQL `pgvector`.
- **BERTopic trend analytics** with 150 hierarchical topics and interactive visualizations.
- **AI Copilot** for paper summarization, Q&A, and BibTeX generation using user-provided keys via NVIDIA NIM or Microsoft AI Foundry.
- **Bookmarks and recommendations** - get recommendations of papers based on your bookmarks
- **All without sign-ups!**

### Technical Highlights
- Architected an end-to-end RAG pipeline for conference scraping, indexing, and retrieval.
- Built a multimodal AI layer with LiteLLM-based provider routing for flexible Copilot workflows.
- Optimized high-dimensional vector similarity search using PostgreSQL (pgvector), engineering multithreaded pipelines to process and ingest data efficiently for concurrent users.
- Containerized the full stack with Docker Compose for reproducible local and cloud deployment.

### Core Stack
- **Frontend:** Next.js, React, TypeScript
- **Backend:** Python, FastAPI, Uvicorn
- **Database:** PostgreSQL + pgvector
- **AI/ML:** LiteLLM, sentence-transformers (`BAAI/bge-base-en-v1.5`), BERTopic
- **Deployment:** Docker, Oracle Cloud
