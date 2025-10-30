### 🛡️ SOC Home Lab: Enterprise-Grade Threat Detection Simulation

> **A hands-on learning project** demonstrating real-world SOC workflows—log aggregation, threat detection, and incident investigation—using industry-standard tools. Built entirely through practical experimentation and strategic use of AI-assisted workflow optimization.

---

## ⚡ Project At a Glance

```
┌────────────────────────────────────────────────────────────────┐
│  🎯 PURPOSE: Learn SOC fundamentals through hands-on practice  │
│  🔍 FOCUS: Threat Detection (not response/remediation)         │
│  💻 PLATFORM: Linux-based lab environment                      │
│  🏆 OUTCOME: Production-grade detection workflow               │
│  📊 STATUS: Lab Simulation (Educational & Replicable)          │
└────────────────────────────────────────────────────────────────┘
```

| Aspect               |    Details                                                |
|----------------------|-----------------------------------------------------------|
| **Core SIEM**        | Wazuh (enterprise-grade, open-source)                     |
| **Lab Environment**  | 4 Linux VMs (Ubuntu-based)                                |
| **Data Sources**     | auditd, osquery, Suricata IDS                             |
| **Threat Detection** | SSH brute force, Nmap reconnaissance, malware detection   | 
| **API Integration**  | VirusTotal for automated file reputation lookup           |
| **Learning Focus**   | Log aggregation, correlation, detection rule engineering  |

---

## 🎓 What This Project Teaches

This is **not** a pre-built tutorial—it's a **learning-by-doing** journey showcasing:

✅ **Multi-source log aggregation** — Normalizing heterogeneous data streams  
✅ **SIEM rule engineering** — Writing custom detection logic for real attacks  
✅ **API-driven enrichment** — Automating threat intelligence lookups  
✅ **Incident investigation** — Correlating events across multiple sources  
✅ **Lab infrastructure design** — Building reproducible security environments  

---

## 🏗️ Architecture: The Lab Topology

```
┌──────────────────────────────────────────────────────────────────┐
│                    🖥️  ATTACK SIMULATOR                          │
│                   (Kali Linux VM)                                │
│                                                                  │
│  • SSH Brute Force Attempts    → Detected via auditd logs       │
│  • Nmap Network Scans          → Detected via Suricata IDS      │
│  • Malicious File Creation     → Detected via file integrity    │
└───────────────┬──────────────────────────────────────────────────┘
                │
    ┌───────────┴────────────────────┬──────────────────────┐
    │                                │                      │
    ▼                                ▼                      ▼
┌─────────────────┐        ┌──────────────────┐    ┌──────────────────┐
│ 🐧 LINUX AGENT 1│        │ 🐧 LINUX AGENT 2 │    │ 🐧 LINUX AGENT 3 │
│  (Ubuntu 22.04) │        │  (Ubuntu 22.04)  │    │  (Ubuntu 22.04)  │
├─────────────────┤        ├──────────────────┤    ├──────────────────┤
│ • auditd        │        │ • auditd         │    │ • osquery        │
│ • osquery       │        │ • Suricata IDS   │    │ • File Monitoring│
│ • File Monitor  │        │ • File Monitor   │    │                  │
└────────┬────────┘        └────────┬─────────┘    └────────┬─────────┘
         │                         │                       │
         │ Wazuh Agent (UDP 1514)  │                       │
         │                         │                       │
         └─────────────────┬───────┴───────────────────────┘
                           │
                ┌──────────▼──────────────┐
                │  🎯 WAZUH MANAGER      │
                │   (Ubuntu 22.04)       │
                ├───────────────────────┤
                │ ✨ Core Functions:    │
                │ • Log Parsing         │
                │ • Rule Matching       │
                │ • Alert Generation    │
                │ • API Integration     │
                │ • Dashboard (Web UI)  │
                └──────────┬────────────┘
                           │
                ┌──────────▼──────────────┐
                │  📊 DATA PIPELINE      │
                ├───────────────────────┤
                │ • Elasticsearch       │
                │ • Log Indexing        │
                │ • Alert Storage       │
                │ • Real-time Search    │
                └───────────────────────┘
```

### 📡 Data Flow: From Detection to Dashboard

```
┌──────────────────┐
│ Attack Events    │
│ (SSH, Nmap,      │
│  Malware)        │
└────────┬─────────┘
         │
         ▼
┌──────────────────────────────────────────┐
│ Data Sources (auditd, osquery, Suricata)│
└────────┬─────────────────────────────────┘
         │
         ▼ Wazuh Agent (log collection)
         │
┌────────┴────────────────────────────────┐
│ Wazuh Manager (log processing)          │
│ ├─ Parse & Normalize                    │
│ ├─ Match Custom Rules                   │
│ ├─ Call VirusTotal API (if needed)      │
│ └─ Generate Alerts                      │
└────────┬────────────────────────────────┘
         │
         ▼ ✅ Alert Triggered
         │
┌────────┴────────────────────────────────┐
│ Elasticsearch (storage & indexing)      │
└────────┬────────────────────────────────┘
         │
         ▼ 📊 Visible in Dashboard
         │
    👁️ Analyst Reviews Alert
```

---

### 🤖 Integration of Generative AI Tools like ChatGpt, Claude, Grok in Project Workflow

## 🧩 1. Planning and Architecture Design
Generative AI tools such as ChatGPT and Claude played a key role in the **initial planning and design** of this SOC project. By providing detailed environment specifications, tool requirements, and security goals, I was able to use AI to draft a structured lab architecture, select compatible open-source tools, and validate the overall setup. This significantly reduced the research time and ensured every step was aligned with practical SOC workflows.

## ⚙️ 2. Configuration and Detection Engineering
During the configuration phase, AI tools assisted in **creating and refining detection mechanisms** for Wazuh and Suricata. I used context-rich prompts describing specific attack scenarios (e.g., brute-force attempts, malicious file executions, or suspicious network flows), and AI generated tailored rule logic and configuration syntax. Each suggestion was then verified manually within the lab environment to ensure accuracy and functionality, turning rule writing into a guided engineering process rather than guesswork.

## 🧠 3. Troubleshooting and Problem Solving
Whenever issues arose—such as agent-manager communication errors, service failures, or incorrect log parsing—AI tools helped structure the **troubleshooting approach**. Instead of random fixes, I used guided diagnostic prompts to receive systematic, step-by-step investigation paths. This method allowed me to isolate root causes faster and maintain a smooth workflow throughout the project.

## 💻 4. Technical Implementation Support
AI was also instrumental in generating **command-line syntax, configuration edits, and deployment steps**. By specifying environment details and intended outcomes, I obtained precise commands for Linux and Windows systems, reducing manual lookup time. AI responses were tested in the lab to ensure reliability and understanding before execution, maintaining a hands-on learning approach.

## 🧾 5. Documentation and Knowledge Structuring
Throughout the project, I utilized AI to produce **clear, professional documentation**—from SOC architecture outlines to technical writeups explaining rule logic and detection flow. AI helped convert technical jargon into readable, structured markdown suitable for both technical and non-technical audiences, ensuring effective communication of complex processes.

## 🎯 6. Prompt Engineering Strategy
To ensure consistent, high-quality results, I applied **prompt engineering principles**:
- Defined context and constraints (e.g., OS type, tool version, SOC use case)
- Requested structured outputs (step-by-step guides, rule syntax, command blocks)
- Iterated based on results and provided feedback to refine responses
- Validated all AI-generated suggestions through hands-on testing

By combining technical validation with AI-assisted reasoning, I was able to enhance efficiency, accuracy, and documentation quality across all project stages—turning AI into a true productivity partner in SOC project development.

---

## ⚡ Key Takeaways: AI as a Learning Accelerator

| Aspect                 | Without AI             | With AI Strategy            |
|------------------------|------------------------|-----------------------------|
| **Project Design**     | 3-4 hours research     | 30 mins guided design       |
| **Rule Development**   | Trial & error (days)   | Validated rules in hours    |
| **Troubleshooting**    | Stack Overflow hunting | Targeted explanations       |
| **Documentation**      | Manual formatting      | Structured, polished output |
| **Total Productivity** | Baseline               | **3-4x faster execution**   |

**Critical Learning:** AI was a **research & execution accelerator**, not a replacement for hands-on practice. Every command was tested, every rule was validated against real traffic, and deep understanding was built through iteration.

---

## 📂 What You'll Find in This Lab

| Folder                    |               Contains                                   |
|---------------------------|----------------------------------------------------------|
| **`/docs`**               | 📖 Detailed guides for each project phase               |
| **`/configs`**            | ⚙️ Sanitized Wazuh rules, agent configs, IDS signatures |
| **`/screenshots`**        | 📸 Dashboard & alert examples from live lab             |
| **`/attack-simulations`** | 🎯 Step-by-step guide for each attack scenario          |

---

## 📚 Documentation Structure

Navigate the complete project workflow:

| Section                                                                     | 🎯 Focus                                    | 📖 Read Time |
|-----------------------------------------------------------------------------|----------------------------------------------|--------------|
| **[1️⃣ Project Overview](./docs/1-project-overview.md)**                    | Lab goals, skills learned, tech stack        | 5 min         |
| **[2️⃣ Environment & Setup](./docs/2-environment-setup.md)**                | VM deployment, network config, connectivity  | 15 min        |
| **[3️⃣ Log Ingestion & Data Sources](./docs/3-log-ingestion.md)**           | Agent setup, data collection, verification   | 20 min        |
| **[4️⃣ Detection, Testing & Validation](./docs/4-detection-validation.md)** | Attack scenarios, alert generation, analysis | 25 min        |
| **[5️⃣ Conclusion & Next Steps](./docs/5-conclusion.md)**                   | Skills gained, limitations, future scope     | 10 min        |
| **[🏗️ Architecture Deep Dive](./docs/ARCHITECTURE.md)**                    | Network topology, data flow, components      | 15 min        |

---

## 🎯 Attack Scenarios: What I Tested & Detected

### Scenario 1: 🔴 SSH Brute Force Attack
**Attack Method:** Multiple failed login attempts from attacker machine  
**Detection:** auditd captures failed authentication events  
**Wazuh Rule:** Custom correlation rule (5+ failed attempts in 5 min)  
**Result:** ✅ Alert triggered with attacker IP & timestamp  

### Scenario 2: 🔴 Nmap Network Reconnaissance
**Attack Method:** Network scan from attacker (nmap -AV target-network)  
**Detection:** Suricata IDS detects scanning traffic patterns  
**Wazuh Integration:** IDS alerts forwarded to Wazuh for correlation  
**Result:** ✅ Scan type & destination logged with confidence level  

### Scenario 3: 🔴 Malware Detection
**Attack Method:** Malicious file downloaded on monitored system  
**Detection:** Wazuh file integrity monitoring + VirusTotal API lookup  
**Enrichment:** API returns file hash reputation (malicious/clean)  
**Result:** ✅ File flagged, hash logged, verdict displayed in dashboard  

---

## 💡 Key Skills Demonstrated

| Competency                      | Proof Point                                           |
|-------------------------------- |-------------------------------------------------------|
| **🔍 Log Analysis**            | Multi-source event correlation across 3+ data sources |
| **🎯 Detection Engineering**   | Custom Wazuh rules matching real attack patterns      |
| **🔌 API Integration**         | VirusTotal enrichment for automated threat lookup     |
| **📊 SIEM Administration**     | Agent deployment, rule tuning, dashboard design       |
| **🏗️ Infrastructure Design**   | Multi-VM network topology for scalable log collection |
| **📖 Technical Documentation** | Reproducible setup guides for others to follow        |
| **🤖 AI-Assisted Workflow**    | Strategic use of LLMs for faster problem-solving      |

---

## 🚀 Getting Started

### Prerequisites
```
✓ VMware Workstation/Fusion or Hyper-V
✓ 16GB+ RAM available
✓ 100GB+ disk space
✓ Ubuntu 22.04 & Kali Linux ISOs

```
## 🎓 Who Should Use This Project?

- 🔰 **Cybersecurity Beginners** learning SOC fundamentals
- 📚 **Security Students** needing hands-on SIEM experience
- 🎯 **Interview Prep** for SOC analyst/engineer roles
- 🏗️ **System Architects** designing detection infrastructure
- 💼 **Hiring Managers** wanting to evaluate candidate SOC knowledge

---

## 🛠️ Technology Stack

| Layer                   | Technology      |          Purpose                         |
|-------------------------|-----------------|------------------------------------------|
| **Data Collection**     | Wazuh Agent     | Lightweight log forwarding from all VMs  |
| **Linux Monitoring**    | auditd          | System & authentication event tracking   |
| **Endpoint Querying**   | osquery         | Flexible SQL queries on system state     |
| **Network IDS**         | Suricata        | Real-time network traffic analysis       |
| **SIEM Platform**       | Wazuh Manager   | Log aggregation, rule matching, alerting |
| **Threat Intelligence** | VirusTotal API  | File reputation & hash lookup            |
| **Visualization**       | Wazuh Dashboard | Real-time alerts & custom dashboards     |

---

## 🔗 Useful Resources

- 📖 [Wazuh Official Docs](https://documentation.wazuh.com/)
- 🔍 [Suricata User Guide](https://suricata.io/documentation/)
- 🛡️ [auditd Documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_security_compliance/auditing-the-system_configuring-security-compliance)
- 🦠 [VirusTotal API Reference](https://developers.virustotal.com/reference)
- 📚 [MITRE ATT&CK Framework](https://attack.mitre.org/)

---

## ⭐ Lab Philosophy

> **"The best way to learn SOC is to build one yourself."**

This project embodies **hands-on learning**, **strategic AI usage**, and **documentation-first** methodology—proving you can take complex security concepts and make them reproducible, understandable, and impactful.

---

**Built with 💙 by someone passionate about cybersecurity fundamentals and AI-enhanced learning.**

*Last Updated: October 2025 | Lab Status: ✅ Complete | Difficulty: Intermediate*
