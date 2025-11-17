# Mapping Requirements to the Implemented Prototype

## Overview
This section provides a structured mapping between the functional and non-functional requirements of the Mobile Support App and the capabilities of the implemented cloud-native RAG prototype.  
It shows which requirements are **fully covered**, **partially supported** or **not yet addressed** by the current implementation.

---

## Requirements-to-Prototype Mapping Table

| Requirement Type | Requirement ID | Description | Prototype Coverage | Notes |
|------------------|----------------|-------------|--------------------|-------|
| **Functional** | FR-1 | Multimodal user input (text, audio, image) | **Partially supported** | The mobile app supports multimodal input; the backend prototype currently processes text queries only. |
| **Functional** | FR-2 | Context capture (GPS, device ID, environment) | **Not supported** | Context can be sent from the app, but backend/RAG system is not yet using it. |
| **Functional** | FR-3 | Knowledge retrieval via RAG | **Fully supported** | Vertex AI RAG correctly retrieves SOP, manuals, incidents. |
| **Functional** | FR-4 | Access to enterprise knowledge sources | **Partially supported** | Prototype uses 5 simulated knowledge documents; no real company data yet. |
| **Functional** | FR-5 | Grounded response generation | **Fully supported** | Gemini 2.5 Flash produced grounded SOP answers without hallucination. |
| **Functional** | FR-6 | Query history & repeatability | **Not supported** | Planned for future mobile app development. |
| **Functional** | FR-7 | “Case file” incident creation | **Not supported** | Identified as future potential. |
| **Functional** | FR-8 | Backend REST API | **Partially supported** | FastAPI concept exists; not yet fully integrated with RAG prototype. |
| **Functional** | FR-9 | Logging and monitoring | **Partially supported** | Logs available through Cloud Shell for RAG calls; no integrated logging pipeline yet. |

| Requirement Type | Requirement ID | Description | Prototype Coverage | Notes |
|------------------|----------------|-------------|--------------------|-------|
| **Non-Functional** | NFR-1 | Performance & latency | **Partially supported** | Retrieval latency ~3–5s observed in prototype. |
| **Non-Functional** | NFR-2 | Reliability & availability | **Partially supported** | Cloud services ensure availability; prototype not fully deployed. |
| **Non-Functional** | NFR-3 | Security & authentication | **Fully supported** | IAM + service accounts correctly set up. |
| **Non-Functional** | NFR-4 | Data privacy & compliance | **Fully supported** | Prototype uses synthetic data only; GDPR not violated. |
| **Non-Functional** | NFR-5 | Scalability | **Fully supported** | Cloud Storage, Vertex AI, Cloud Run are scalable by design. |
| **Non-Functional** | NFR-6 | Extensibility | **Partially supported** | RAG corpus can ingest new files; app missing integration. |
| **Non-Functional** | NFR-7 | Maintainability | **Partially supported** | Architecture is clean; long-term maintenance not implemented. |
| **Non-Functional** | NFR-8 | Cost transparency & control | **Partially supported** | Costs manageable; RagManagedDb had to be paused manually. |
| **Non-Functional** | NFR-9 | Interoperability | **Not supported** | No integration with ERP/GIS/SCADA yet. |

---

## Summary
- The prototype **fully covers core RAG functionality**, including retrieval, grounding, embeddings and architecture.  
- Functional requirements related to **field context, multimodal pipelines and incident feedback** remain outside the current scope.  
- Non-functional requirements like **security, privacy and scalability** are well covered due to native support of Google Cloud services.  
- Several requirements highlight clear directions for **future work**, especially integration with real enterprise systems.

This mapping forms the foundation for the Evaluation and Discussion chapters of the paper.
