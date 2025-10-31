## ⚙️ Environment Setup

This section outlines the technical setup and configuration process for the SOC Home Lab built using **Wazuh** and **Suricata** for endpoint and network monitoring.  
The focus is on demonstrating **structured implementation, environment design, and validation**.

---

## 💻 1. Host Machine Specifications
The project was built on a Windows 11 host system using **VMware Workstation Pro**, optimized to run multiple VMs simultaneously for SOC simulation.

- **Processor:** AMD Ryzen 7  
- **Memory:** 24 GB RAM  
- **Storage:** 1 TB SSD  
- **Virtualization:** VMware Workstation Pro  
- **Operating System:** Windows 11  

<img width="507" height="197" alt="host-specs" src="https://github.com/user-attachments/assets/b4ae4946-61ff-4c5c-9f53-f2fb7b51ab83" />

---

## 🧱 2. Virtual Machine Configurations
Each virtual machine served a specific purpose in the SOC architecture, simulating the attacker, detection, and monitoring components.

| VM Name                                       | Purpose                                | Memory | Disk  | Network Mode |
|-----------------------------------------------|----------------------------------------|--------|-------|--------------|
| **Ubuntu (Wazuh Manager)**                    | Centralized SIEM & log analysis        | 8 GB   | 80 GB | NAT          |
| **Windows Victim (Agent + Sysmon)**           | Endpoint telemetry & event collection  | 5 GB   | 50 GB | NAT          |
| **Ubuntu Victim (Suricata, auditd, osquery)** | Network IDS & Linux endpoint telemetry | 6 GB   | 50 GB | NAT          |
| **Kali Attacker**                             | Attack simulation & testing            | 3.5 GB | 60 GB | NAT          |

![vmware-overview](https://github.com/user-attachments/assets/3df9417d-d413-499e-8ac5-a7018f026699)

---

## 🌐 3. Network Topology & Design
The SOC environment was designed as an **isolated NAT network**, enabling controlled communication between systems while maintaining Internet access for updates.

- **Wazuh Manager:** 192.168.137.10  
- **Windows Victim:** 192.168.137.11  
- **Ubuntu Victim:** 192.168.137.12  
- **Kali Attacker:** 192.168.137.13  

📈 *Key Design Highlights:*
- NAT Network for Internet connectivity (tool updates, integrations)  
- Internal SOC traffic isolation for analysis  
- Static IP assignments for predictable communication  
- Validated routing and gateway consistency  

<img width="447" height="164" alt="network-topology" src="https://github.com/user-attachments/assets/a69ea766-e83c-49b8-a2d0-a9a6c06d877f" />

---


## 🧩 4. Step-by-Step Installation Process
All installations were performed manually following **official documentation** for Wazuh, Suricata, and supporting tools.  
LLM-based tools like **ChatGPT** and **GitHub Copilot** were used to refine configuration commands, troubleshoot issues, and accelerate workflow.

---

## 🛠️ 5. Software Installation & Configuration
Configured and integrated the following key components:
- **Wazuh Manager** for centralized log analysis and alerting  
- **Wazuh Agents** on Windows and Ubuntu endpoints  
- **Sysmon** on Windows for advanced event telemetry  
- **Suricata** for real-time network intrusion detection  
- **auditd** and **osquery** for Linux host monitoring  

<img width="921" height="545" alt="wazuh-dashboard" src="https://github.com/user-attachments/assets/c4152b10-8449-4532-ac37-b53e59f2507e" />

<img width="683" height="518" alt="suricata-config" src="https://github.com/user-attachments/assets/67565d85-ac0d-43e9-88d6-15dfa7c23a73" />

---

## 🌐 6. Network Connectivity Validation
Verified inter-VM communication and manager-agent connectivity using:
- ICMP ping tests  
- Wazuh agent registration checks  
- Suricata log forwarding validation  

<img width="521" height="416" alt="ping-validation" src="https://github.com/user-attachments/assets/3a8a31b9-6c07-4748-9193-4d3f736c4925" />

---

## ✅ 7. Pre-requisites Checklist
Before deployment, the following baseline checks were completed:
- Virtualization enabled in BIOS  
- Sufficient resource allocation for smooth parallel execution  
- Proper network configuration in VMware  
- Connectivity between all VMs validated  

---

## 🚀 8. Deployment Order & Dependencies
The deployment followed a **bottom-up architecture** to ensure dependency alignment:

1. **Host Machine Optimization**
2. **Wazuh Manager Installation**
3. **Ubuntu Victim Configuration** (Suricata, auditd, osquery)
4. **Windows Victim Setup** (Sysmon, Agent)
5. **Kali Attacker Setup** (Attack simulation)
6. **Connectivity & Detection Validation**

<img width="790" height="600" alt="final-env" src="https://github.com/user-attachments/assets/8f258982-b56b-44c9-9b99-9f54c45df40b" />

---

## 🧠 Knowledge Demonstrated
Through this environment setup, I gained hands-on experience in:
- Designing and configuring multi-VM SOC environments  
- Network topology planning for SIEM and IDS workflows  
- Installing and integrating open-source security tools  
- Verifying and troubleshooting communication flows  
- Using AI tools effectively for faster troubleshooting and configuration guidance  

---

⭐ *This setup built the foundation for subsequent detection engineering and incident analysis workflows documented in the later sections of this project.*





