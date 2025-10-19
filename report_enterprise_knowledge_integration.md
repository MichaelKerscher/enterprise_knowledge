# Integrating Enterprise Knowledge into Cloud-Native AI Systems using Google Cloud 

## Objective
Design and demonstrate a **cloud-native architecture** that connects enterprise knowledge with **Large Language Models (LLMs)**.  
The work extends the previous *Mobile Support App* project by implementing **Retrieval-Augmented Generation (RAG)** on **Google Cloud Vertex AI** with **Gemini 2.5 Flash**.  

---

## Motivation 
LLMs are powerful but isolated-they cannot access company-specific data such as manuals or incident logs.  
This project enables **secure, factual and context-aware** responses through integration with internal knowledge bases.  

---

## Cloud-Native Architecture
**Components**
- Vertex AI RAG Engine - vector database and semantical retrieval
- Cloud Storage - knowledge document repository
- Text Embedding Model (text-embedding-005) - semantic encoding
- Gemini 2.5 Flash - generation with enterprise grounding
- FastAPI Backend - interface to the mobile support app

**Pipeline**  
Mobile App -> FastAPI Backend -> Vertex AI RAG Engine -> Gemini 2.5 Flash -> Response

---

## Implementation Highlights
- Created and indexed **five German enterprise documents** (SOPs, manuals, checklists, incident logs)
- Verified successful semantic retrieval and context-grounded generation 

**Example query**
> "Wie wird bei einem Gasleck laut Notfallprozedur reagiert?"

**Grounded Answer (Gemini 2.5 Flash)**
1. Arbeiten sofort einstellen und Gefahrenbereich räumen
2. Keine elektrischen Geräte betätigen
3. Fenster und Türen öffnen, Hauptgashahn schließen
4. Leitwarte informieren, Notruf 112 absetzen

Matches the original SOP exactly - no hallucination

---

## Evaluation Summary
| Aspect | Observation |
|--------|-------------|
| Response Quality | High factual accuracy |
| Context Awareness | Correct document retrieval |
| Security | Managed access via Vertex AI |
| Scalability | Cloud-native, extensible pipeline |

---

## Outcome & Next Steps
**Outcome**  
A working proof-of-concept demonstrating integration of enterprise knowledge into Gemini-based AI systems.  
Improved factuality, explainability and operational value in support scenarios.  

**Next Steps**
- Connect the RAG pipeline to the FastAPI backend
- Compare model responses *with vs without* enterprise grounding
- Experiements & Data Collection with raw evaluation data
- Analysis & Writing with 5-page draft

---

**Keywords:** Vertex AI - RAG Engine - Gemini 2.5 Flash - Cloud Storage - Enterprise Knowledge - Context-Aware AI