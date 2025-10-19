### Step 1 - Cloud Project & Permissions
- Verified active project: `gemini-support-app`
- Enabled required APIs:
    `aiplatform, storage, bigquery, run, iam`
- Created service account: `rag-backend@gemini-support-app.iam.gserviceaccount.com
- Roles granted: aiplatform.user, storage.objectViewer, bigquery.dataViewer
- Status: Complete (Cloud Shell)

### Step 2 - Cloud Storage Bucket and Folder Structure
- Create a Google Cloud Storage bucket to store the simulated enterprise knowledge base used by the Vertex AI RAG pipeline

**Actions performed**
*1 Create bucket in Frankfurt region*
gsutil mb -l europe-west3 gs://gemini-support-knowledge/

*2 Create logical sub-folders by uploading empty .keep files*
echo "" | gsutil cp - gs://gemini-support-knowledge/documents/sops/.keep
echo "" | gsutil cp - gs://gemini-support-knowledge/documents/manuals/.keep
echo "" | gsutil cp - gs://gemini-support-knowledge/documents/incidents/.keep
echo "" | gsutil cp - gs://gemini-support-knowledge/documents/specs/.keep
echo "" | gsutil cp - gs://gemini-support-knowledge/documents/checklists/.keep
echo "" | gsutil cp - gs://gemini-support-knowledge/metadata/.keep
echo "" | gsutil cp - gs://gemini-support-knowledge/evaluation/.keep

*3 Verify structure*
gsutil ls -r gs://gemini-support-knowledge/

**Results**
michael_kerscher@cloudshell:~ (gemini-support-app)$ gsutil ls -r gs://gemini-support-knowledge/
gs://gemini-support-knowledge/null
gs://gemini-support-knowledge/documents/:

gs://gemini-support-knowledge/documents/checklists/:
gs://gemini-support-knowledge/documents/checklists/.keep

gs://gemini-support-knowledge/documents/incidents/:
gs://gemini-support-knowledge/documents/incidents/.keep

gs://gemini-support-knowledge/documents/manuals/:
gs://gemini-support-knowledge/documents/manuals/.keep

gs://gemini-support-knowledge/documents/sops/:
gs://gemini-support-knowledge/documents/sops/.keep

gs://gemini-support-knowledge/documents/specs/:
gs://gemini-support-knowledge/documents/specs/.keep

gs://gemini-support-knowledge/evaluation/:
gs://gemini-support-knowledge/evaluation/.keep

gs://gemini-support-knowledge/metadata/:
gs://gemini-support-knowledge/metadata/.keep

**Outcome**
Bucket *gemini-support-knowledge* successfully created with the full folder hierarchy for RAG document types and metadata. This structure will host PDFs, CSVs and JSON/YAML files representing simulated enterprise knowledge. 

---

### Step 3 - Simulated Enterprise Documents
- Generate and upload realisitic, non-sensitive enterprise documents that simulate internal knowledge for the Vertex AI RAG corpus

---

#### 1. Create local working directory

```bash
mkdir -p ~/data/simulated_docs/{sops,manuals,incidents,specs,checklists}
cd ~/data/simulated_docs
```

---

#### 2. Generate five simulated documents in German

| Category | File | Format | Description |
|----------|------|--------|-------------|
| Safety procedure | `SOP_Gasleck_Notfallprozedur_v1.txt` | TXT | Standard-Arbeitsanweisung für Gasleck-Notfälle |
| Technical manual | `Handbuch_Wasserpumpe_Stoerung_v2.txt` | TXT | Fehlerdiagnose für Wasserpumpe PX-450 |
| Incident log | `vorfallsliste_2025.csv` | CSV | Historische Störungsmeldungen mit Fehlercodes |
| Device specification | `Geratespezifikation_SmartMeter_AQ500.json` | JSON | Gerätespezifikation eines Smart-Meters |
| Maintenance checklist | `Wartung_Checkliste_Pumpstation.yaml` | YAML | Routine-Wartungsschritte für Pumpstation PS-100 |

Example creation comman:

```bash
cat > sops/SOP_Gasleck_Notfallprozedur_v1.txt <<'EOF'
STANDARD-ARBEITSANWEISUNG (SOP)
Dokument-ID: SOP_001
Titel: Notfallprozedur bei Gasleck
Version: 1.0
Abteilung: Betrieb / Außendienst
Gültig ab: 01.01.2025
...
EOF
```

(Analogous commands executed for all five files.)

---

#### 3. Verify file creation

```bash
find ~/data/simulated_docs -type f
```

Expected results:
```bash
/home/michael_kerscher/data/simulated_docs/manuals/Handbuch_Wasserpumpe_Stoerung_v2.txt
/home/michael_kerscher/data/simulated_docs/checklists/Wartung_Checkliste_Pumpstation.yaml
/home/michael_kerscher/data/simulated_docs/specs/Geraetespezifikation_SmartMeter_AQ500.json
/home/michael_kerscher/data/simulated_docs/sops/SOP_Gasleck_Notfallprozedur_v1.txt
/home/michael_kerscher/data/simulated_docs/incidents/vorfallsliste_2025.csv
```

---

#### 4. Upload to Cloud Storage

```bash
gsutil -m cp -r ~/data/simulated_docs/* gs://gemini-support-knowledge/documents/
```
---

#### 5. Verify upload
```bash
gsutil ls -r gs://gemini-support-knowledge/documents/
```

Expected result:
```bash
gs://gemini-support-knowledge/documents/sops/SOP_Gasleck_Notfallprozedur_v1.txt
gs://gemini-support-knowledge/documents/manuals/Handbuch_Wasserpumpe_Stoerung_v2.txt
...
```

---

#### 6. Create and upload metadata index

```bash
cat > corpus_index.json <<'EOF'
[
  {
    "doc_id": "SOP_001",
    "title": "Notfallprozedur bei Gasleck",
    "type": "sop",
    "language": "de",
    "created": "2025-01-01",
    "safety_level": "hoch",
    "source_path": "gs://gemini-support-knowledge/documents/sops/SOP_Gasleck_Notfallprozedur_v1.txt"
  },
  {
    "doc_id": "MAN_002",
    "title": "Fehlerdiagnose Wasserpumpe PX-450",
    "type": "manual",
    "language": "de",
    "created": "2025-06-10",
    "source_path": "gs://gemini-support-knowledge/documents/manuals/Handbuch_Wasserpumpe_Stoerung_v2.txt"
  },
  {
    "doc_id": "INC_003",
    "title": "Vorfallsliste 2025",
    "type": "incident_log",
    "language": "de",
    "created": "2025-05-14",
    "source_path": "gs://gemini-support-knowledge/documents/incidents/vorfallsliste_2025.csv"
  },
  {
    "doc_id": "SPEC_004",
    "title": "Gerätespezifikation SmartMeter AQ-500",
    "type": "spec_sheet",
    "language": "de",
    "created": "2025-09-01",
    "source_path": "gs://gemini-support-knowledge/documents/specs/Geraetespezifikation_SmartMeter_AQ500.json"
  },
  {
    "doc_id": "CHK_005",
    "title": "Wartungs-Checkliste Pumpstation PS-100",
    "type": "maintenance_checklist",
    "language": "de",
    "created": "2025-10-01",
    "source_path": "gs://gemini-support-knowledge/documents/checklists/Wartung_Checkliste_Pumpstation.yaml"
  }
]
EOF

gsutil cp corpus_index.json gs://gemini-support-knowledge/metadata/
```

Verification:
```bash
gsutil ls gs://gemini-support-knowledge/metadata/
gsutil cat gs://gemini-support-knowledge/metadata/corpus_index.json
```

---

**Outcome**
Five realistic German enterprise documents successfully created and uploaded to Cloud Storage.
A corresponding metadata index (`corpus_index.json`) provides unified references for each file and ensures compatibility with Vertex AI RAG ingestion.
This step completes the simulated enterprise knowledge base used in the prototype.


