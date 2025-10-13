# Enterprise Knowledge - Cloud-Native AI Prototype

**Author:** Michael Kerscher  
**Project:** Part of Master's Thesis  
**Institution:** University of Applied Science Upper Austria  
**Status:** Phase 1 completed

---

## Project Overview

This repository documents the practical implementation of a cloud-native architecture for integrating **enterprise knowledge** into **LLM-based systems** using **Google Cloud Vertex AI (Gemini)**.

The project builds upon an existing **Mobile Support App** and **FastAPI backend**, extending the architecture with a **Retrieval-Augmented Generation (RAG)** pipeline that connects enterprise knowledge to Gemini 2.5 Flash.

---

## Objectives

1. **Design and Implementation**
   1. Develop a secure, cloud-native RAG architecture using Google Cloud.
   2. Integrate enterprise documents as structured knowledge sources
   
2. **Evaluation**
   1. Compare Gemini's response quality *with vs. without* enterprise knowledge.
   2. Measure accuracy, contextual relevance, security and scalability.

3. **Documentation**
   1. Provide reproducible setup and testing instructions for academic validation.

---

## Phase 1 - Setup and Data Preparation

**Goal:** Prepare the Google Cloud infrastructure and create a simulated enterprise knowledge base

### Step 1 - Cloud Project & Permissions
- Verified active project: `gemini-support-app`
- Enabled APIs: `aiplatform, storage, bigquery, run, iam`
- Created service account: `rag-backend@gemini-support-app.iam.gserviceaccount.com`
- Granted roles: `aiplatform.user`, `storage.objectViewer`, `bigquery.dataViewer`

### Step 2 - Cloud Storage Bucket & Folder Structure
- Bucket: `gs://gemini-support-knowledge/`
- Subfolders: `sops`, `manuals`, `incidents`, `specs`, `checklist`, `metadata`, `evaluation`
- Verified with `gsutil ls -r`

### Step 3 - Simulated Enterprise Documents
- Created 5 realistic German enterprise documents:
  - SOP (safety), manual (technical), incident log (CSV), spec sheet (JSON), checklist (YAML)
- Uploaded to Cloud Storage
- Created `corpus_index.json` metadata index

---

## Phase 2 - Knowledge Integration Prototype (In Progress)

**Goal:**  
Implement and test a Retrieval-Augmented Generation (RAG) architecture using:
- **Vertex AI Search / RAG Engine**
- **Gemini 2.5 Flash**
- **FastAPI Backend (Cloud Run)**

**Next Steps:**
- [ ] Create Vertex AI RAG index
- [ ] Connect backend to RAG API
- [ ] Run initial retrieval and query tests
- [ ] Log evaluation metrics

---

## Notes
This repository contains **synthetic data** for research and demonstration purposes only.  
No confidental or real enterprise information is included.

---






