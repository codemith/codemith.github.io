---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

You can also [download my resume as a PDF](/files/Mithilesh_Biradar_resume.pdf).

Education
======
* **M.S. in Computer Science**, Clemson University, SC — Aug 2024 – May 2026
  * Focus: Machine Learning, Data Science | GPA: 3.96
* **B.Tech in Computer Engineering**, MIT Academy of Engineering, Pune — June 2020 – May 2024
  * Focus: Artificial Intelligence | GPA: 3.8 (8.56/10)

Work Experience
======
* **Research Assistant** — Clemson University (Oct 2025 – Present)
  * Optimized the ACTOPO data structure on large-scale meshes (17.4M vertices), reducing cache misses by 99% and accelerating computation by 49%.

* **AI Engineer Intern** — TD SYNNEX, Greenville, SC (May 2025 – Sep 2025)
  * Led full SDLC for a distributed GenAI multimodal RAG solution with NVIDIA, using LangChain and NVIDIA NeMo with 98%+ query routing accuracy at 15ms latency.
  * Migrated RAG-platform vector store from Milvus to PostgreSQL with PGVector, improving performance and scalability.
  * Developed a scalable SQL-RAG pipeline with automated ELT framework, FastAPI text-to-SQL backend, and NVIDIA NeMo Guardrails.

* **Research Assistant** — Clemson University (Nov 2024 – Apr 2025)
  * Designed transformer-based NLP models for text classification and threat analysis, achieving 24% improvement in sentiment detection accuracy.
  * Built distributed data pipelines in PyTorch and Spark for large-scale text processing.

* **Machine Learning Engineer Intern** — TRUMPF Metamation, Chennai, TN (Jun 2023 – Sep 2023)
  * Developed a computer vision system for real-time bending angle analysis in hydraulic presses.
  * Achieved 98.7% accuracy in real-time angle detection across 10,000+ readings per minute using CNNs.

Skills
======
* **Languages:** Python, C++, C, SQL, JavaScript
* **AI/ML:** PyTorch, TensorFlow, Scikit-learn, LangChain, LLMs, RAG, NLP, VLMs, Agentic AI, NVIDIA NIMs
* **Development & DevOps:** AWS, Docker, Kubernetes, PostgreSQL, Milvus, FastAPI, Linux, CI/CD

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>
