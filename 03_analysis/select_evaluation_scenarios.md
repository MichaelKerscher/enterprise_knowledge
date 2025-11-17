# Selection of Evaluation Scenarios

## Overview
To qualitatively evaluate the cloud-native RAG prototype built on Google Cloud Vertex AI, three realistic scenarios were selected.  
Each scenario reflects a typical information need of field technicians in an energy utility company and is based on one of the simulated enterprise knowledge documents created in Phase 1.

The scenarios cover:
- **Safety procedures (SOP)**
- **Technical troubleshooting (Manual)**
- **Operational history (Incident Log)**

These represent the three core knowledge domains essential for supporting technicians in the field.

---

## Scenario 1 – Emergency Response: Gas Leak Procedure (SOP)

### Description
A technician encounters a suspected gas leak near a service line and asks the system:

> *“Welche Schritte sollen bei einem Gasleck laut interner Notfallprozedur durchgeführt werden?”*

### Source Document
- `SOP_Gasleck_Notfallprozedur_v1.txt`  
- Contains emergency steps, safety rules, and escalation procedures.

### Purpose
This scenario evaluates:
- The system’s ability to retrieve safety-critical information  
- Grounded, step-based response generation  
- Avoidance of hallucinated or unsafe instructions  

---

## Scenario 2 – Troubleshooting: Water Pump PX-450 (Technical Manual)

### Description
A technician investigates a malfunctioning circulation pump and asks:

> *“Welche Schritte zur Fehlerdiagnose werden für die Wasserpumpe PX-450 empfohlen?”*

### Source Document
- `Handbuch_Wasserpumpe_Stoerung_v2.txt`  
- Contains troubleshooting instructions, common symptoms, and diagnostic steps.

### Purpose
This scenario evaluates:
- Retrieval of device-specific troubleshooting steps  
- Technical precision of the grounded response  
- Usefulness for on-site diagnostics  

---

## Scenario 3 – Operational History: Incident Log 2025

### Description
A technician wants to know whether a heating station has a history of failures and asks:

> *“Welche Störungen wurden laut Vorfallsliste 2025 am häufigsten gemeldet?”*

### Source Document
- `vorfallsliste_2025.csv`  
- Contains historical incident reports with error types and timestamps.

### Purpose
This scenario evaluates:
- Ability to extract structured information from CSV-like documents  
- Summarization of recurring faults  
- Relevance of RAG for situational awareness and decision-making  

---

## Summary
These three scenarios represent a balanced cross-section of knowledge types needed for field service operations.  
They are used in the next steps to perform a structured qualitative evaluation of the RAG prototype.
