# Non-Functional Requirements (NFR) for the Mobile Support App

## Overview
Non-functional requirements define the quality attributes and operational constraints of the Mobile Support App and its cloud-native RAG backend.  
They determine how well the system performs under real-world conditions in an energy utility company.

---

## NFR-1: Performance & Latency
The system should respond within:
- **3–6 seconds** for standard RAG queries  
- **<10 seconds** for multimodal queries (text + image)

Rationale: Field technicians require fast responses to avoid delays in resolving operational tasks.

---

## NFR-2: Reliability & Availability
The system should achieve:
- **High availability** through serverless infrastructure (Cloud Run, Vertex AI)  
- **Minimal downtime**, ideally <1%  
- Automatic scaling under varying query loads

Rationale: Technicians often work on tight schedules and cannot rely on unstable tools.

---

## NFR-3: Security & Authentication
The system must:
- Use Google IAM for authentication and authorization  
- Restrict access via service accounts with minimal privileges  
- Protect all data transfers using TLS  
- Ensure no sensitive customer or operational data is exposed

Rationale: Utility-sector data is security-critical and often regulated.

---

## NFR-4: Data Privacy & Compliance
The system must comply with:
- **GDPR** (EU data protection)  
- Company-specific IT and data-handling policies  
- Principles of data minimization and purpose limitation

Rationale: Technical documents may include sensitive operational information.

---

## NFR-5: Scalability
The backend must scale based on usage:
- Auto-scaling capabilities (Cloud Run, Vertex AI managed services)  
- Ability to handle multiple technicians querying in parallel  
- Elastic vector retrieval without manual resource management

Rationale: Workload varies strongly depending on incidents, weather conditions, or infrastructure failures.

---

## NFR-6: Extensibility
The architecture should support:
- Adding new document types to the knowledge corpus  
- Expanding to other departments (gas, water, district heating)  
- Optional extensions such as proactive anomaly detection or case file generation

Rationale: Enterprise knowledge grows over time; the architecture must grow with it.

---

## NFR-7: Maintainability
The system should:
- Use clean code and modular architecture  
- Provide clear logs for debugging  
- Use standard cloud services to reduce maintenance effort  
- Allow easy updates to the knowledge corpus

Rationale: IT teams in mid-sized utilities often have limited resources.

---

## NFR-8: Cost Transparency & Control
The solution must:
- Provide transparent monitoring of cloud usage  
- Allow disabling or pausing cost-intensive components (e.g., RagManagedDb)  
- Keep operational costs predictable and manageable  

Rationale: Utility companies operate with tight budgets and must justify AI-related costs.

---

## NFR-9: Interoperability
The system should be capable of integrating with:
- ERP, asset management, or GIS systems  
- Sensor data platforms  
- Incident management tools  
- Document management systems (DMS)

Rationale: Enterprise knowledge is distributed and must be accessible across systems.

---

## Summary
These non-functional requirements describe the quality attributes needed to ensure that the Mobile Support App and its cloud-native RAG backend are performant, secure, scalable, and maintainable.  
They provide a foundation for assessing the suitability of the developed prototype and identifying future improvements.
