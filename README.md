# Enterprise Knowledge – Cloud-Native AI Prototype  
**Author:** Michael Kerscher  
**Project:** Master’s Thesis – University of Applied Sciences Upper Austria  
**Status:** Phase 2 completed (RAG prototype operational)  
**Platform:** Google Cloud Vertex AI (Gemini 2.5 Flash)

---

## Overview  
This repository documents the design and evaluation of a **cloud-native Retrieval-Augmented Generation (RAG)** architecture for integrating **enterprise knowledge** into **LLM-based applications**.  
The work builds upon a *Mobile Support App* and extends it with a managed **Vertex AI RAG Engine** that retrieves contextual information from internal documents to improve response quality and reduce hallucinations.

---

## Objectives  

1. **Architecture Design**  
   - Develop a scalable, secure, and context-aware AI backend using Google Cloud Vertex AI.  
   - Demonstrate how enterprise documents can be linked to Gemini LLMs.  

2. **Implementation**  
   - Build a working RAG prototype using:  
     `Vertex AI RAG API + Cloud Storage + FastAPI Backend (Cloud Run)`  
   - Integrate multimodal, context-rich data (text, images, voice).  

3. **Evaluation**  
   - Compare Gemini responses **with vs. without enterprise knowledge**.  
   - Assess retrieval accuracy, latency, and qualitative relevance.  

---

## Architecture Overview  
*Cloud-Native RAG Architecture (Google Cloud Vertex AI)*  
The system consists of three main layers:  
- **Application Layer:** Mobile App capturing multimodal context data.  
- **Integration Layer:** FastAPI Backend on Cloud Run with IAM-based authentication.  
- **RAG Engine Layer:** Vertex AI RAG pipeline for retrieval and Gemini 2.5 Flash generation.

---

## Vertex AI RAG Engine Workflow  

*Vertex AI RAG Engine – Ingestion and Retrieval Workflow*  
Enterprise documents are stored in Cloud Storage, parsed, chunked and embedded using `text-embedding-005`.  
The embeddings are stored in a managed vector database (Spanner).  
When a query arrives, semantic retrieval and ranking select relevant context for Gemini 2.5 Flash to generate grounded responses.

---

## Phases
Phase 1 – Cloud Setup completed  
Phase 2 – RAG Prototype operational  
Phase 3 – Evaluation in progress  
Phase 4 – Architecture transfer (On-Prem concept, planned)  
Phase 5 – Paper writing & submission  

---

## Security and Compliance  
- All data in this repository are synthetic and for academic demonstration only.  
- No real enterprise data are included.  
- IAM roles and service accounts follow Google Cloud best practices.

---

