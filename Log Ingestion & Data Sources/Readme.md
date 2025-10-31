# Log Ingestion & Data Sources

This section explains **what logs were collected**, **how they were forwarded** to the Wazuh Manager, and **how ingestion was validated**.
It focuses on ingestion and normalization.

---

## 🧩 Overview  
Collected endpoint and network telemetry was standardized and routed to the Wazuh Manager for correlation and analyst review. 
Sources include Windows endpoint telemetry (Sysmon + Windows Event Logs) and Linux telemetry (Suricata, auditd, osquery).

<img width="1536" height="1024" alt="Logs data flow" src="https://github.com/user-attachments/assets/38f3249d-b6bd-40d4-8f86-7ee441d1ac41" />

---
## 🖥️ Agent Connectivity Validation

To ensure successful log ingestion from both Windows and Ubuntu endpoints, agent connectivity was verified
through the **Wazuh Dashboard → Agents → Status** module. Both systems appeared as **active and connected**,
confirming secure communication with the Wazuh Manager.

**Purpose:**  
✅ Demonstrates multi-OS agent connectivity and successful deployment of both Windows and Linux endpoints.  
✅ Confirms that both agents are properly registered and communicating with the Wazuh Manager.  

<img width="548" height="289" alt="agents-connected" src="https://github.com/user-attachments/assets/3ef0b84e-3fc5-4be7-bbf2-37e3bff67470" />

---

## 🌐 Suricata (Network IDS) Ingestion  
**What:** `eve.json` alerts from Suricata — network scans, suspicious connections, signature matches.  
**How:** Suricata writes `eve.json` locally; Wazuh Agent is configured with a `<localfile>` entry to collect and forward these JSON alerts to the Manager for correlation.  
**Validation:** View Suricata alert in Discover and confirm JSON fields are parsed correctly.

<img width="917" height="544" alt="suricata-eve-sample" src="https://github.com/user-attachments/assets/a4988210-3588-42b1-8de5-4d26e12193df" />

---

## 🔗 Threat Enrichment (VirusTotal integration)  
**What:** File hash reputation lookups to add context to file-related events.  
**How:** Wazuh Manager enrichment module queries VirusTotal (configured without exposing keys in screenshots) and attaches a reputation score to relevant events.  
**Validation:** Shows an example enrichment result.

<img width="1803" height="1085" alt="VirusTotal" src="https://github.com/user-attachments/assets/c51d29ed-1a4e-4f49-8e2e-98d55351c21b" />

---

## ⚙️ Ingestion Health & Normalization  
**What to show:** Demonstrated that logs are decoded/normalized (fields extracted) and visible in Discover.  
**How validated:** Used Wazuh Discover to inspect fielded events (source, timestamp, hostname, event_type) and confirm decoders are applied.  
**Why it matters:** Normalized fields enable rule correlation and meaningful analyst investigation later.

<img width="918" height="543" alt="discover-field-view" src="https://github.com/user-attachments/assets/074c9c6e-28f7-4993-8e53-423e5a670927" />

---

## 🧠 Key Concepts Demonstrated (summary)  
- Multi-source ingestion: Windows (Sysmon/WinEvents) + Linux (auditd/osquery) + IDS (Suricata).  
- Forwarding pipeline: Agent → Manager → Discover / Dashboard.  
- Normalization: Decoders applied so events are fielded and searchable.  
- Enrichment: VirusTotal used for contextualizing file events.

<img width="920" height="543" alt="ingestion-summary" src="https://github.com/user-attachments/assets/03700ab6-54f8-4b97-92ee-ea23ba140452" />

---
