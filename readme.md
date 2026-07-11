# Blue Team & SOC Analyst Portfolio

## 👤 Profile
Welcome to my Security Operations Center (SOC) Analyst Portfolio. This repository serves as a centralized showcase of my technical capabilities in threat detection, endpoint monitoring, network forensics, and automated incident response.

The projects included here simulate real-world enterprise environments and adversarial campaigns, demonstrating a structured approach to the identification, analysis, and mitigation of modern cyber threats.

---

## 🗺️ Portfolio Architecture & Modules

The portfolio is structured into four specialized domains, moving from centralized log management and endpoint visibility to deep network traffic analysis and automated incident orchestration.

```text
                          ┌─────────────────────────────────────────┐
                          │        SOC Analyst Portfolio            │
                          └────────────────────┬────────────────────┘
                                               │
     ┌─────────────────────────────┬───────────┴───────────┬─────────────────────────────┐
     ▼                             ▼                       ▼                             ▼
┌─────────────────┐           ┌─────────────────┐     ┌─────────────────┐           ┌─────────────────┐
│    Module 01    │           │    Module 02    │     │    Module 03    │           │    Module 04    │
│ SIEM & Threat   │           │ Wazuh Endpoint  │     │ Network IDS &   │           │  SOAR n8n       │
│   Detection     │           │   Monitoring    │     │ Packet Analysis │           │  Automation     │
└─────────────────┘           └─────────────────┘     └─────────────────┘           └─────────────────┘
```

### 📊 [01-SIEM-Threat-Detection](./01-SIEM-Threat-Detection)

Focuses on enterprise centralized log management, security analytics, and security event correlation.

- **Core Components:** SIEM architecture setup, log ingestion pipelines, custom detection rule creation, and dashboard engineering.
- **Objective:** Centralizing disparate host logs into high-visibility dashboards to identify early indicators of compromise.

---

### 🛡️ [02-Wazuh-Endpoint-Monitoring](./02-Wazuh-Endpoint-Monitoring)

Focuses on Host-Based Intrusion Detection (HIDS), Endpoint Detection & Response (EDR), and endpoint security monitoring.

- **Core Components:** Deployment of Wazuh agents across Windows and Linux systems, File Integrity Monitoring (FIM), and vulnerability auditing.
- **Threat Mitigation:** Developing Active Response rules to automatically block malicious activity and monitor lateral movement attempts.

---

### 🔍 [03-Network-IDS-and-Packet-Analysis](./03-Network-IDS-and-Packet-Analysis)

Focuses on deep packet forensics, network intrusion detection, and protocol analysis.

- **Tactical Detection:** Detection of network reconnaissance (Nmap), SSH brute-force attacks, reverse shells, suspicious DNS activity, and malicious HTTP communications.
- **Advanced Investigations:** End-to-end forensic investigations of the **SmartApeSG ClickFix Campaign (Remcos RAT)** and **GuLoader → AgentTesla** credential theft and FTP data exfiltration.

---

### ⚡ [04-SOAR-n8n-Automation](./04-SOAR-n8n-Automation)

Focuses on Security Orchestration, Automation, and Response (SOAR) to automate repetitive SOC workflows.

- **Core Components:** n8n workflow automation, Elastic integration, Jira API, and Python Flask responders.
- **Automation Engineering:** Automatically ingesting Elastic detections, calculating contextual risk scores, generating Jira incidents, and executing PowerShell-based containment actions such as disabling compromised user accounts.

---

## 🛠️ Core Technology Stack

| Domain | Tools & Technologies |
| :--- | :--- |
| **SIEM & Endpoint** | Elastic Stack (Elasticsearch, Kibana), Wazuh EDR/HIDS, Sysmon, Windows/Linux Event Logs |
| **Automation & SOAR** | n8n Workflow Engine, Jira API, Python Flask, PowerShell |
| **Network Forensics** | Wireshark, Tshark, Suricata IDS, Zeek |
| **Threat Intelligence** | VirusTotal, WHOIS, AbuseIPDB, MITRE ATT&CK Framework |

---

## 🚀 Key Skills Demonstrated

1. **Log Aggregation & Normalization** – Building end-to-end log ingestion pipelines that transform raw telemetry into actionable security events.
2. **Behavioral Detection Engineering** – Mapping attacker behaviors from the MITRE ATT&CK framework into high-fidelity SIEM and EDR detections.
3. **Incident Reconstruction & Packet Analysis** – Reconstructing packet captures to identify malicious infrastructure, recover exposed credentials, and document attack progression.
4. **Security Automation (SOAR)** – Automating incident response workflows to reduce Mean Time to Respond (MTTR) through orchestration and containment playbooks.

---

## 🚦 How to Navigate This Portfolio

- Explore the modules sequentially (**01 → 04**) to follow a complete Blue Team workflow, from log collection and endpoint monitoring to network forensics and automated incident response.
- Each module contains a dedicated `README.md` describing the lab environment, investigation methodology, detection logic, MITRE ATT&CK mapping, and supporting evidence.
