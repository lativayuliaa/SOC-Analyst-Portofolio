# Wazuh Endpoint Monitoring and Threat Detection Lab

## 📌 Overview
This repository contains a comprehensive endpoint security engineering and threat hunting lab built on the **Wazuh XDR/SIEM platform**. The primary objective of this project is to model real-world adversarial execution techniques against a Linux ecosystem, validate centralized log ingestion pipelines, and construct programmatic SOC triaging workflows mapped to the **MITRE ATT&CK® framework**.

The project encompasses a wide vector of detections, including authentication exploitation, privilege escalation vectors, active kernel-level File Integrity Monitoring (FIM), persistence hooks, and post-compromise credential harvesting routines.

---

## 🏗️ Lab Architecture & Deployment
The defensive lab infrastructure is structured across an isolated server-agent topology designed for deep telemetry ingestion:

| Component | Operating System | Purpose |
| :--- | :--- | :--- |
| 🛡️ **Wazuh Server** | Ubuntu/Debian Cluster | Centralized log collection, real-time decoding, correlation, and alert generation. |
| 🖥️ **Wazuh Agent** | Kali Linux | Monitored target endpoint providing continuous host telemetry. |
| 📊 **Wazuh Dashboard**| Elastic-based Web UI | Security analytics, threat hunting interface, and incident visualization. |

---

## 📁 Laboratory Directory Navigation
Each subdirectory below represents a standalone engineering case file, featuring an independent **Attack Simulation**, an analytical **Investigation Report**, and formal **MITRE ATT&CK Mapping** documentation:

### ⚙️ [00-Lab-Setup](00-Lab-Setup/)
Focuses on deployment initialization, agent integration via centralized token authentication, system service verification, and master dashboard provisioning.

### 🔑 [Case 01 – Authentication Failures](Case-01-Authentication-Failures/)
* **Scenario:** Simulation of rapid authentication failure sequences via SSH/Local access pools to model brute-force patterns.
* **MITRE ATT&CK:** `T1110` – Brute Force

### 🛡️ [Case 02 – Suspicious Sudo Activity](Case-02-Suspicious-Sudo-Activity/)
* **Scenario:** Auditing anomalous non-privileged shell context transformations and unauthorized administrative configuration calls.
* **MITRE ATT&CK:** `T1548.003` – Abuse of Sudo and Sudo Caching

### 📁 [Case 03 – File Integrity Monitoring (Whodata)](Case-03-File-Integrity-Monitoring/)
* **Scenario:** Real-time host filesystem tracking using OS kernel-level auditing hooks to catch critical data mutation and system baseline deletion.
* **MITRE ATT&CK:** `T1565.001` – Stored Data Manipulation & `T1070.004` – File Deletion

### ⏳ [Case 04 – Persistence via Cronjob](Case-04-Persistence-via-Cronjob/)
* **Scenario:** Monitoring unauthorized scheduling modifications within systemic system crontabs and user spool layers designed to survive reboots.
* **MITRE ATT&CK:** `T1053.003` – Scheduled Task/Job: Cron

### 🔓 [Case 05 – Sensitive File Access](Case-05-Sensitive-File-Access/)
* **Scenario:** Catching post-exploitation reconnaissance lookups targeting local identity indexes and cryptographic password maps.
* **MITRE ATT&CK:** `T1003.008` – OS Credential Dumping: `/etc/passwd` and `/etc/shadow`

### 🔴 [Case 06 – Root Privilege Activity](Case-06-Root-Privilege-Activity/)
* **Scenario:** Intercepting live interactive shell commands executed under high-privilege root runspaces to map out adversarial execution patterns.
* **MITRE ATT&CK:** `T1078` – Valid Accounts & `T1548.003` – Sudo and Sudo Caching

### 📊 [Dashboard Visualizations Node](Dashboard/)
Contains custom centralized visualization setups combining alert timelines, distribution graphs by severity matrix level, rule hits, and dedicated threat tracking maps.

---

## 🗺️ Framework Alignment Matrix (MITRE ATT&CK)

| Tactic | Technique ID | Technique Name | Applied Use Case Module |
| :--- | :--- | :--- | :--- |
| **Credential Access** | `T1110` | Brute Force | Case 01 – Authentication Failures |
| **Privilege Escalation**| `T1548.003` | Sudo and Sudo Caching | Case 02 – Suspicious Sudo Activity |
| **Impact / Defense Evasion** | `T1565.001` | Stored Data Manipulation | Case 03 – File Integrity Monitoring |
| **Defense Evasion** | `T1070.004` | File Deletion | Case 03 – File Integrity Monitoring |
| **Persistence** | `T1053.003` | Scheduled Task/Job: Cron | Case 04 – Persistence via Cronjob |
| **Credential Access** | `T1003.008` | OS Credential Dumping | Case 05 – Sensitive File Access |
| **Privilege Escalation**| `T1078` | Valid Accounts | Case 06 – Root Privilege Activity |

---

## 🛠️ Cyber Engineering Core Skillset Demonstrated

### 🔍 Threat Detection & SIEM Operations
* **Log Decoding & Rule Parsing:** Deep comprehension of decoder logic models matching unformatted standard Linux audit strings.
* **SIEM Dashboard Optimization:** Constructing scannable dashboard views to streamline triage for front-line SOC analysts.
* **MITRE Matrix Integration:** Aligning technical log signatures with tactical threat intelligence matrices.

### 🖥️ Endpoint Security & Host Hardening
* **Linux Security Auditing:** In-depth log monitoring via Linux system PAM architectures, Sudo tracking loops, and structural auth stores.
* **File Integrity Monitoring (FIM):** Actively setting up real-time directory security monitors utilizing elevated Whodata system audit subsystems.
* **Privilege Interception:** Isolating unauthorized system access transitions across multi-tier local system profiles.

---
### 🏁 Project Status: `Completed & Certified`
