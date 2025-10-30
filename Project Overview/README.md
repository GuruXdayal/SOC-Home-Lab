## 🧠 Project Overview – SOC Home Lab

## 🔍 Brief Recap
This project simulates a **real-world Security Operations Center (SOC)** environment integrating **Wazuh** for endpoint monitoring and
**Suricata** for network intrusion detection.  
It focuses on **detecting, analyzing, and responding** to security incidents — from **malicious file activity** to **network scans and brute-force attacks** —
across both **Windows and Linux** systems.

---

## 🚀 Learning Journey
The journey began with setting up a **multi-VM lab** to simulate a real SOC workflow:  
- 🖥️ **Windows Victim (Wazuh Agent + Sysmon)** for endpoint telemetry  
- 🧱 **Ubuntu Victim (Wazuh Agent, Suricata, Auditd, Osquery)** for network and system visibility  
- 🌐 **Wazuh Manager Server (Ubuntu)** for central log collection, alerting, and rule creation  
- 🐉 **Kali Linux** as the **attacker machine** for simulating adversary actions  

Throughout the lab, I learned to:
- Configure agents, tune detection rules, and integrate **VirusTotal API** for file analysis.  
- Simulate attacks (malicious file download, port scans, SSH brute force) and validate detection accuracy.  
- Use **GenAI tools** for troubleshooting, automation, and clear documentation.

---

## 🧩 Skills Matrix – What I Gained

| Skill Area 🛠️                       | Tools / Concepts Used                   | Outcome                                               |
|-------------------------------------|-----------------------------------------|-------------------------------------------------------|
| **Endpoint Monitoring**             | Wazuh, Sysmon, Windows Event Logs       | Detected and analyzed malicious activities on Windows |
| **Network Threat Detection**        | Suricata IDS                            | Identified network scans, SSH brute-force attempts    |
| **Detection Engineering**           | Custom Wazuh Rules, Suricata Signatures | Built & tuned rules to improve alert fidelity         |
| **Threat Intelligence Integration** | VirusTotal API                          | Validated malicious file hashes automatically         |
| **Linux Security Auditing**         | auditd, osquery                         | Captured process and system-level audit data          |
| **Documentation & Automation**      | GenAI Tools (ChatGPT, Copilot)          | Streamlined setup, troubleshooting, and reporting     |

---

## ⚙️ Lab Scope & Constraints

**Scope:**
- Focuses on **SOC L1-level detections** and basic **rule creation**.
- Integrates **host-based** and **network-based** detection workflows.
- Covers **alert validation**, **log correlation**, and **incident triage**.

**Constraints:**
- Lab is designed for **training**, not production-scale workloads.  
- **No EDR/XDR integrations** (focused solely on open-source SOC tools).  
- Alerts simulated within **controlled virtual environment**.

---

## 🎯 Why This Lab Matters for a SOC Career

This lab mirrors what a **SOC Analyst (L1)** does in real-world scenarios:  
- 👀 Monitor dashboards and correlate alerts.  
- 🧠 Understand data sources (Sysmon, network IDS logs).  
- ⚡ Respond to incidents with quick triage and evidence validation.  
- 🧩 Build foundations for **detection engineering** and **GRC roles** later.

> 🏆 **Outcome:** A hands-on foundation in SOC monitoring, detection logic, and security automation — critical for any entry-level SOC or Blue Team role.

---

## 📘 Key Takeaways

- Gained confidence in **building a complete SOC environment** from scratch.  
- Learned to **write and test detection rules** that trigger on real threats.  
- Improved **log analysis** skills across multiple data sources.  
- Leveraged **AI for smarter configurations**, debugging, and documentation clarity.  
- Understood how to **validate detections end-to-end** in a SOC workflow.

---

## ⚖️ Lab Simulation vs. Real SOC Comparison

| Aspect                | SOC Home Lab 🧪          | Real-World SOC 🏢                        |
|-----------------------|---------------------------|------------------------------------------|
| **Scale**             | 3–4 VMs                   | 100s of endpoints & servers              |
| **Tools**             | Wazuh, Suricata, Sysmon   | SIEMs like Splunk, QRadar, Elastic, etc. |
| **Threat Simulation** | Manual & scripted attacks | Continuous real-world threats            |
| **Alert Volume**      | Controlled, low           | High, requiring prioritization           |
| **Response Workflow** | Manual triage             | Automated + tiered response teams        |
| **Goal**              | Learning & validation     | Business security & compliance           |

---

## 🧠 Summary
This project represents a **complete SOC learning capsule** — integrating tools, detection logic, and threat simulation to reflect real analyst workflows.  
It demonstrates not just **technical proficiency**, but also **analytical thinking** and **documentation discipline** —
all vital for launching a **career as a SOC Analyst**.

---
