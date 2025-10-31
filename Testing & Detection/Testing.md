# 🧩 Testing & Detection

This section documents the **threat simulation** and **detection validation** performed in the SOC Home Lab.  
All simulations were executed from the **Kali attacker VM** against the **Ubuntu victim (agented)** to validate network
and host-based detections in Wazuh. The emphasis is on demonstrating detection engineering, log correlation,
and MITRE ATT&CK mapping for each scenario.

---

## 🔎 Test Summary (Simulations)
Performed 4 controlled simulations (lab-only):

| # | Simulation                           | Primary Detection Source                          | Purpose                                                       |
|---|--------------------------------------|---------------------------------------------------|---------------------------------------------------------------|
| 1 | Malicious file download              | Wazuh FIM + VirusTotal enrichment                 | Detect suspicious file writes and determine reputation        |
| 2 | Nmap port scan | Suricata (eve.json) | Detect network reconnaissance / scanning activity |
| 3 | File Integrity Monitoring (FIM)      | Wazuh FIM / auditd                                | Detect unauthorized file creation/modification                |
| 4 | SSH brute-force attack               | auditd / auth logs + Wazuh rules                  | Detect repeated failed auth attempts and possible brute-force |

---

## 🧪 For each simulation — What, How, Detection, MITRE Mapping & Screenshot

### 1) 🔸 Malicious File Download  
**What:** Simulated downloading/execution of a suspicious file on the Ubuntu victim.  
**How the simulation was performed:**  
- From Kali, triggered a controlled file transfer (HTTP/`wget` or `curl`) to the Ubuntu victim.  
- Ensured file write & execution events are generated (FIM + process events).  
**Detection Source:** Wazuh FIM module (auditd) → Wazuh Manager decodes FIM event → VirusTotal enrichment (hash lookup).  
**MITRE ATT&CK Mapping:**  
- **Tactic:** Execution (TA0002)  
- **Technique:** T1059 (Command and Scripting Interpreter) / T1204.002 (User Execution: Malicious File)  
**Validation:** Verified alert in **Wazuh → Malware Detection / FIM** with VirusTotal score attached.  

![VirusTotal_malicious file](https://github.com/user-attachments/assets/6ded9dbe-2139-414d-b7ca-a1618898c21b)

---

### 2) 🔍 Nmap Port Scan (Network Reconnaissance)  
**What:** Port scanning of the Ubuntu victim to generate Suricata alerts.  
**How the simulation was performed:**  
- From Kali: `nmap -T4 -A <victim IP>` or targeted scan to trigger Suricata signatures.  
**Detection Source:** Suricata `eve.json` alerts forwarded via Wazuh Agent.  
**MITRE ATT&CK Mapping:**  
- **Tactic:** Reconnaissance (TA0043) / Initial Access reconnaissance techniques  
- **Technique:** T1595 (Active Scanning) / T1046 (Network Service Discovery)  
**Validation:** Confirmed Suricata alert appears in Wazuh (Threat Hunting) and triggers custom network rule.  

![Nmap_Nmap scans](https://github.com/user-attachments/assets/0bc4ded4-edef-46e2-8fc7-2307837f9d09)

---

### 3) 🛡️ File Integrity Monitoring (FIM)  
**What:** Created/modified files to validate FIM detection and rule sensitivity.  
**How the simulation was performed:**  
- On Ubuntu, created or modified a protected file (simulated tamper) to generate auditd/FIM events.  
**Detection Source:** auditd → Wazuh FIM module → Manager rules.  
**MITRE ATT&CK Mapping:**  
- **Tactic:** Defense Evasion (TA0005) / Persistence (TA0003)  
- **Technique:** T1078 (Valid Accounts — related detection entry points) & T1490 (Inhibit System Recovery) as context for tamper detection  
**Validation:** FIM alert in Wazuh FIM module and correlated process/log activity in Discover.  

![FIM_FIM test](https://github.com/user-attachments/assets/97b6bf5a-f840-47c9-81d2-89fae923f185)

---

### 4) 🔐 SSH Brute-Force Attack  
**What:** Simulated repeated failed SSH authentications to detect credential-guessing behavior.  
**How the simulation was performed:**  
- From Kali used a controlled brute-force approach (scripted or `hydra`) against the Ubuntu victim’s SSH service (lab-only).  
**Detection Source:** auth.log / auditd events → Wazuh Agent → Wazuh Manager rules detecting repeated failures.  
**MITRE ATT&CK Mapping:**  
- **Tactic:** Credential Access (TA0006)  
- **Technique:** T1110 (Brute Force)  
**Validation:** Alert visible in **Wazuh → Threat Hunting / Security Events** with aggregated count and `src.ip` context.  

![bruteforce_SSH authentication](https://github.com/user-attachments/assets/653af38f-abdf-41a6-8765-54789151e380)

---

## ⚙️ Custom Rules & Correlation
- **Network rule:** Custom Wazuh rule to parse Suricata alerts and create high-confidence network alerts (`suricata.network.alert`).  
- **Auth rule:** Threshold-based rule to detect **X failed SSH logins** from one source within **Y time window** (configurable).  
- **Correlation approach:** Link Suricata alerts with host events (FIM or process creation) to increase alert confidence and reduce false positives.

![rules vt_rule-wazuh_rule 1_rule suricata](https://github.com/user-attachments/assets/abb84a54-73fb-4d35-a634-fea14bafbfc0)

---

## 🐉 Role of Kali (Attacker Machine)
- Kali acted as the **controlled adversary** to generate attack traffic: scanning (nmap), file delivery (wget/curl), and authentication attacks (hydra/scripted SSH attempts).  
- Purpose: produce reproducible telemetry for testing detection rules, tuning thresholds, and demonstrating triage workflow.

---

## 📈 Key Outcomes & Learnings
As a beginner, this phase demonstrated and reinforced:
- **Detection engineering:** designing reliable rules for network and host telemetry.  
- **Log correlation:** linking Suricata network alerts with auditd/FIM and process events for higher-fidelity alerts.  
- **Threat enrichment:** using VirusTotal to add context to file-related alerts.  
- **Tuning:** balancing sensitivity (catching attacks) vs. noise (reducing false positives).  
- **SOC workflow:** event → decode → rule → alert → triage in Wazuh.

<img width="1536" height="1024" alt="Alert flow" src="https://github.com/user-attachments/assets/b5d0a7a1-259e-4e1b-a436-4b881fc2448f" />

---

