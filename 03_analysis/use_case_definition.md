# Use Case Definition: Mobile Support App for Field Technicians

## Overview
Field technicians in energy utility companies must frequently diagnose and resolve operational issues such as heating system anomalies, pump failures, sensor malfunctions, or emergency situations (e.g., gas leaks). These tasks require rapid access to distributed knowledge sources, which are typically stored in different systems (ERP, SCADA, GIS, network drives) and are not optimized for mobile access.  

## Current Challenges
- Knowledge is siloed across multiple IT systems
- Technicians rely on personal expertise or phone calls to colleagues
- Technical documents are difficult to access in the field
- Lack of structured feedback or incident documentation from field operations
- Inconsistent troubleshooting processes lead to inefficiency and safety risks

## Proposed Solution: Mobile Support App
The Mobile Support App serves as an intelligent interface between the technician and enterprise knowledge sources. It enables technicians to use multimodal communication channels and integrates contextual information to generate more accurate and situation-aware support responses.  

### Core Interaction Flow
1. Technician submits a query via:
   - **Text** (typed or dictation)
   - **Audio** (hands-free)
   - **Image** (photo of device, error message, damaged component)
2. App collects contextual metadata:
   - GPS location
   - Timestamp
   - Device or installation ID (if available)
   - Environment state or anomaly indicators
3. Backend forwards enriched request to the cloud-based RAG system
4. Technician receives a **grounded**, **document-backend** and **context-aware** response.

## Example Scenarios
### Scenario A - Device Troubleshooting
A technician notices unusual noise in a circulation pump (PX-450).  
The app retrieves:
- Troubleshooting steps from the technical manual
- Past incident records for similar issues
- Known sensor anomalies

### Scenario B - Emergency SOP Retrieval 
At a suspected gas leak, the technician requests:  
*"What should I do according to our SOP?"*  
The app delivers the exact SOP steps extracted from internal documents.  

### Scenario C - Historical Incident Lookup
The technician asks:  
*"Has this heating station had similar problems before?"*  
The app finds:  
- Incident logs 
- Notes from previous field technicians
- Repair history

## Future Potential ("Bonus Scenario")
The technician records a voice memo after resolving a problem.  
The system:  
- Summarizes the memo
- Stores it as a structured incident report ("case file")
- Makes it available for future retrieval and analytics

This capability would enable coninuous knowledge growth and improve internal documentation quality.  

## Purpose of Use Case Definition
This use case forms the foundation for:
- The architectural design of the cloud-native RAG system
- The qualitative evaluation of its usefulness
- The discussion of how enterprise knowledge can be operationalized in the field 
- The alignment with real needs of medium-sized energy utility
