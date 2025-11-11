# Phase 2 - Methodology and Observations
**Project:** gemini-support-app  
**Region:** europe-west3 (Frankfurt)  
**Date:** November 2025  
**Objective:** Document methodology and summarize qualitative observations from the RAG prototype implementation.  

---

## Methodology and Workflow

### Objective
Describe the methodological approach used to implement and evaluate the cloud-native RAG prototype.  

### Methodological Approach
The work in Phase 2 followed an **explorative prototyping** approach.  
The goal was to practically validate how enterprise knowledge could be integrated into a Google Cloud-based LLM system.  
The process combined infrastructure setup, code-based experimentation and qualitative observation.  

### Workflow Summary
1. **Environment Setup**
   - Verified active project: `gemini-support-app`
   - Activated Vertex AI, Storage, IAM, BigQuery, Run APIs
   - Created service account (`rag-backend`) for programmatic access

2. **Corpus Creation and Data Import**
   - Defined a simulated enterprise corpus (`energy-support-corpus`)
   - Imported five German documents into Vertex AI RAG via Cloud Storage
   - Applied automatic chunking (`chunk_size=512`, `overlap=1000`)
   - Confirmed successful embedding and indexing in RagManagedDB (Spanner)

3. **Retrieval and Contextual Generation**
   - Verified retrieval quality using semantic queries
   - Connected the corpus to Gemini 2.5 Flash through RAG tool configuration
   - Observed accurate, grounded answers referencing the SOP documents

4. **Documentation and Verification**
   - All steps verified in Cloud Shell with logs and screenshots
   - Outcomes summarized in `setup_log_phase2.md` and GitHub README

### Outcome
A fully functional managed RAG setup was achieved, demonstrating end-to-end enterprise knowledge retrieval and contextual LLM generation within Google Cloud.  
This workflow serves as a baseline for evaluating Managed-RAG systems in contrast to potential on-premise implementation.  

---

## Qualitative Observation Summary

### Objective
Summarize key qualitative observation obtained during RAG setup, testing and first retrieval runs.  

### Observations

| Aspect | Observation | Interpretation |
|--------|-------------|----------------|
| **Retrieval Quality** | The semantic retrieval returned highly relevant SOP passages for German natural language queries. | The embedding model `text-embedding-005` handled German context robustly, even without fine-tuning. |
| **Grounding Accuracy** | Gemini 2.5 Flash generated factual, step-by-step responses aligned with the original SOP. | Effective grounding; hallucinations were not observed. |
| **Multilingual Handling** | German text was processed and retrieved correctly. | Confirms multilingual capability of Vertex AI RAG pipeline. |
| **Performance / Latency** | Initial query latency ranged from 3-5s, including retrieval. | Acceptable for a field support scenario; within practical reponse times. |
| **Scalability & Cost** | Managed RAG handled corpus creation automatically but generated storage and Spanner costs. | Illustrates trade-off between managed convenience and cost control. |
| **Developer Experience** | Service account and IAM roles worked as expected. | Shows managed IAM integration simplifies access control compared to self-hosted vector DBs. |

### Overall Impression
The managed RAG prototype provided a stable and transparent way to connect enterprise knowledge to Gemini.  
The workflow highlighted both **strengths (ease of integration, accuracy)** and **limitations (cost visibility, limited retrieval control)** of using a fully managed RAG service.  
These qualitative findings from the empirical basis for the following analytical and comparative work in Phase 3.  
