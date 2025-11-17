# Functional Requirements for the Mobile Support App

## Overview
The Mobile Support App is intended to support field technicians by providing multimodal interaction, context capture, and intelligent access to enterprise knowledge via a cloud-native RAG backend.  
This section defines the **functional requirements (FR)** that the system must fulfill to support real-world operations in an energy utility company.

---

## FR-1: Multimodal User Input
The system must allow technicians to submit queries via:
- **Text input**
- **Dictated speech (audio-to-text)**
- **Images** (e.g., device photos, error codes, damaged components)

Rationale: Different field environments require flexible input modes.

---

## FR-2: Context Capture
The app should automatically capture contextual metadata, including:
- GPS location  
- Timestamp  
- Device or installation ID (if known)  
- Environmental indicators (e.g., sensor anomalies from external sources)

Rationale: Context improves retrieval relevance and LLM grounding.

---

## FR-3: Knowledge Retrieval via RAG
The backend must forward technician requests to the cloud-native RAG engine and return:
- Retrieved document chunks  
- Grounded answers  
- Confidence indicators (if available)

Rationale: Technicians require factually correct, document-backed responses.

---

## FR-4: Access to Enterprise Knowledge Sources
The system must support accessing the following knowledge types:
- Standard Operating Procedures (SOPs)  
- Technical manuals  
- Device specifications and datasheets (JSON/structured)  
- Historical incident logs  
- Maintenance checklists  

Rationale: Field workers rely on diverse knowledge sources stored across the company.

---

## FR-5: Response Generation and Delivery
The backend must:
- Generate grounded answers using Gemini (via Vertex AI RAG)  
- Provide step-by-step guidance when available  
- Return responses in structured JSON format

The app must:
- Display results clearly  
- Support follow-up questions  
- Show document references where applicable

---

## FR-6: Query History & Repeatability
The app should:
- Keep a local or backend-stored history of previous queries  
- Allow re-running queries  
- Enable follow-up interactions based on earlier responses

Rationale: Technicians often revisit a problem or compare prior states.

---

## FR-7: Optional “Case File” Generation (Future Functionality)
The system may optionally support:
- Summarizing technician’s voice notes or text notes  
- Storing them as incident reports  
- Linking reports to device IDs or locations  
- Making them retrievable in future RAG queries

Rationale: Enables continuous knowledge growth and improves documentation quality.

---

## FR-8: Backend API Integration
The backend must expose:
- A secure REST endpoint (e.g., `/ask`)  
- Accepting JSON requests with query + context  
- Returning grounded responses including source references

Rationale: Ensures Apps and external systems can integrate easily.

---

## FR-9: Logging and Monitoring
The backend must log:
- Query attempts  
- Retrieval results  
- Latency  
- Error states

Logs should support later analysis during evaluation.

---

## Summary
These functional requirements describe the core capabilities needed for the Mobile Support App to provide efficient, knowledge-grounded assistance to field technicians. They will be used later to assess:
- How well the cloud-native prototype fulfills them  
- Which requirements remain open for future development
