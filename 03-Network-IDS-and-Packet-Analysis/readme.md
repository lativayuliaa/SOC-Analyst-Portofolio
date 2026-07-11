# Module 03 — Network IDS and Packet Analysis

## 📌 Overview
Welcome to the **Network IDS and Packet Analysis** hands-on laboratory. This module focuses on the core competencies of network forensics, traffic triage, security monitoring, and incident response. 

Through real-world packet captures (PCAPs) and logs, you will learn how to detect adversarial techniques, analyze unencrypted and encrypted protocols, identify indicators of compromise (IOCs), and reconstruct end-to-end attack chains.

---

## 🗺️ Lab Curriculum Directory

This module is structured into a logical progression, starting from environment setup to progressively complex attack investigations:

### ⚙️ Core Configuration
* **[00-Lab-Setup](./00-Lab-Setup)**: Documentation for environment baselining, tool configurations (Wireshark, Suricata/Zeek profiles), and verification of the investigation workspace.

### 🔍 Tactical Detection Cases
* **[Case-01-Nmap-Scan-Detection](./Case-01-Nmap-Scan-Detection)**: Identifying active network reconnaissance, mapping stealth/TCP/UDP scans, and profiling attacker discovery patterns.
* **[Case-02-SSH-Brute-Force-Detection](./Case-02-SSH-Brute-Force-Detection)**: Analyzing high-volume transport layer anomalies, isolating credential stuffing attempts, and tracking successful vs. failed authentications.
* **[Case-03-Suspicious-DNS-Requests](./Case-03-Suspicious-DNS-Requests)**: Investigating anomalous domain lookups, tracking potential Data Exfiltration over DNS, and identifying dynamic domain generation algorithms (DGA).
* **[Case-04-Suspicious-File-Download-Detection](./Case-04-Suspicious-File-Download-Detection)**: Tracking cleartext web layer downloads, carving files from packet streams, and calculating staging hashes for threat intelligence verification.
* **[Case-05-Reverse-Shell-Detection](./Case-05-Reverse-Shell-Detection)**: Catching active remote command-and-control (C2) channels, analyzing raw interactive TCP streams, and identifying post-exploitation activities.

### 🕵️‍♂️ Advanced Threat Investigations
* **[Case-06-Packet-Investigation](./Case-06-Packet-Investigation)**: Deep dive into the **SmartApeSG ClickFix Campaign**. Investigating HTTP 301 redirections, dissecting unencrypted Server Name Indication (SNI) strings from TLS certificates, and mapping short-lived infrastructure used to distribute the **Remcos RAT**.
* **[Case-07-AgentTesla-FTP-Exfiltration](./Case-07-AgentTesla-FTP-Exfiltration)**: End-to-end forensic reconstruction of an **AgentTesla** infection. Covers initial phishing email attachment delivery (`.rar`), public IP lookup discovery, plaintext FTP session parsing (`USER`/`PASS` extraction), and file carving of exfiltrated browser credentials and mail clients.

---

## 🛠️ Core Toolkit & Frameworks
During these investigations, you will leverage industry-standard DFIR tools and frameworks:
* **Network Forensic Analysis Windows:** Wireshark, Tshark
* **Threat Intelligence & Infrastructure Mapping:** VirusTotal, WHOIS databases, AbuseIPDB
* **Adversarial Mapping:** MITRE ATT&CK Framework for Enterprise
* **Detection Engineering:** Suricata IDS Rules & SIEM Correlation Strings

---

## 📊 Skills Profile Developed
By completing this module, you will demonstrate the following technical proficiencies:
1. **Packet Dissection:** Advanced proficiency in Wireshark display filters and stream reassembly.
2. **Cleartext Protocol Auditing:** Deep knowledge of extracting authentication tokens and payloads from unencrypted protocols like HTTP and FTP.
3. **Encrypted Traffic Triage:** Ability to extract contextual metadata from TLS handshakes (SNI, Certificates) without breaking encryption.
4. **Behavioral Mapping:** Translating raw alert telemetry and packet structures into actionable MITRE ATT&CK tactical matrices.
5. **Detection Engineering:** Developing defensive signatures to intercept commodity infostealers (AgentTesla) and remote access tools (Remcos RAT) before data exfiltration occurs.

---

## 🚦 Getting Started
1. Navigate to the **`00-Lab-Setup`** directory to ensure your environment variables and protocol dissectors are configured correctly.
2. Follow the cases sequentially (**Case-01** through **Case-07**) to build up your analytical methodologies from basic signature mapping to advanced heuristic session reconstruction.
3. Review the individual `README.md` and investigation reports inside each folder for deep-dive step-by-step screenshot walkthroughs.
