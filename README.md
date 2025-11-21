# Enterprise Knowledge – Cloud-Native RAG Prototype  
**Author:** Michael Kerscher  
**Context:** Master’s Thesis (University of Applied Sciences Upper Austria)  
**Technology Stack:** Google Cloud – Vertex AI (Gemini 2.5 Flash, RAG Engine)

---

## Project Overview  
This repository documents the design, implementation and qualitative evaluation of a **cloud-native Retrieval-Augmented Generation (RAG)** prototype.  
The project investigates how **enterprise knowledge**—such as SOPs, manuals, and incident logs—can be integrated into a **Vertex AI RAG** pipeline to support **field technicians in energy utilities**.

The work forms a substantial methodological and technical part of the master’s thesis and explores how managed cloud RAG services behave under realistic domain assumptions.

---

## Objectives

### 1. **Architecture & System Design**
- Develop a cloud-native, low-operations RAG architecture tailored for field support scenarios.  
- Align key architectural components with organisational requirements (IAM, compliance, latency, data residency).

### 2. **Prototype Implementation**
- Implement a functioning RAG pipeline using:
  - **Vertex AI RAG API**  
  - **Cloud Storage**  
  - **RagManagedDb vector store**  
  - **Gemini 2.5 Flash for grounded generation**
- Ingest a synthetic corpus representing utility-domain documents.

### 3. **Qualitative Evaluation**
- Observe ingestion robustness, retrieval plausibility and groundedness.  
- Evaluate system behaviour on realistic German-language emergency and troubleshooting queries.

### 4. **Platform Comparison**
- Contrast **Vertex AI RAG**, **Azure RAG**, and **On-Prem RAG** using a structured qualitative framework.

---

## Repository Structure
```graphql
ENTERPRISE_KNOWLEDGE/
│
├── 01_docs/                         # High-level documents, early drafts   
│
├── 02_setup/                        # Setup logs, configuration notes
│   ├── screenshots/
│   ├── setup_log_phase1.md
│   ├── setup_log_phase2.md
│   └── phase2_methodology_observation.md
│
├── 03_analysis/                     # Requirements, use cases, gap analysis
│   ├── functional_requirements.md
│   ├── non-functional_requirements.md
│   ├── use_case_definition.md
│   ├── gaps_future_potential.md
│   ├── map_requirements_to_prototype.md
│   └── select_evaluation_scenarios.md
│
├── 04_architecture/                 # Architecture diagrams & design models
│   ├── architecture_overview.drawio
│   ├── architecture_overview.png
│   ├── architecture_rag_engine_layer.drawio
│   └── architecture_rag_engine_layer.png
│
├── 05_paper/                        # Paper source & exported PDF
│   ├── paper_structure.md
│   └── term_paper_mkerscher.pdf
│
└── 06_related_work/                 # Curated related-work blocks
    ├── block 1 - RAG in Enterprise & Industrial Settings
    ├── block 2 - Cloud-Native RAG (GCP, Azure, AWS)
    ├── block 3 - Knowledge Management in Utilities
    ├── block 4 - Field-Service AI or Multimodal Support
    └── block 5 - On-Prem RAG & Vector Databases
```

---

## Architecture Overview

### **Three-Layer Cloud-Native Architecture**

1. **Application Layer**  
   - Mobile client capturing multimodal input (text, audio, images)  
   - Lightweight context (GPS, device ID)

2. **Integration Layer – Cloud Run Backend**  
   - Request validation  
   - Context enrichment  
   - IAM-authenticated calls to Vertex AI RAG

3. **RAG Engine Layer – Vertex AI**  
   - Managed ingestion (parsing, chunking, embedding)  
   - Vector retrieval via RagManagedDb  
   - Grounded generation using Gemini 2.5 Flash  

Architecture diagrams located in the `/04_architecture/` directory illustrate the full pipeline.

---

## RAG Workflow Summary

### **1. Document Ingestion**
- Input formats: TXT, CSV, JSON, YAML  
- Chunking: 512 tokens, 100-token overlap  
- Embeddings via `text-embedding-005`  
- Indexed in a managed **RagManagedDb** vector database  

### **2. Semantic Retrieval**
- Query evaluated with `top_k = 3`  
- No metadata filters or re-ranking  
- Evaluated with realistic emergency-procedure queries in German  

### **3. Grounded Generation**
- Gemini 2.5 Flash with retrieval tool attached  
- Automatic grounding enabled  
- Responses inspected for correctness and alignment with retrieved SOPs  

### **4. Evaluation**
- Focus on *technical feasibility*  
- Qualitative observations rather than numerical metrics  

---

## Security & Compliance

- All data in this repository are **synthetic** and created solely for academic experimentation.  
- No real enterprise documents or sensitive information are included.  
- IAM follows least-privilege principles and documented Google Cloud best practices.  
- The prototype is **not a production system**.

---

## Academic Paper  
The full academic paper—including methods, results, discussion and conclusions—can be found at:

`/05_paper/term_paper_mkerscher.pdf`

It details:

- Motivations and problem definition  
- Related work synthesis  
- System & methodology  
- Qualitative findings  
- Discussion and implications for energy utilities  
- Limitations and directions for future research  

---

## Prototype Status

The prototype demonstrates:

+ Managed cloud RAG is feasible for operational support tasks  
+ Heterogeneous document ingestion works without custom ETL  
+ Retrieval is plausible and contextually relevant for domain queries  
+ Responses remain grounded in source material without hallucination  

Not included in this phase:

- Quantitative retrieval performance benchmarks  
- Real-world enterprise data  
- User studies with field technicians  

---

## Notes  
This repository serves as the **technical and methodological foundation** for the master’s thesis.  
It captures the complete lifecycle from requirement analysis to architecture, implementation, evaluation, and scientific reporting.

---
