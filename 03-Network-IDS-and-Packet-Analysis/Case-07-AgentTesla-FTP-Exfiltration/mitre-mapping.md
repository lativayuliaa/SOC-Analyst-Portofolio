# MITRE ATT&CK Mapping

## Overview
The observed threat behavior has been mapped to the MITRE ATT&CK Enterprise framework based strictly on network traffic analysis, phishing file structures, and forensic evidence collected during the investigation.

---

# ATT&CK Technique Mapping Matrix

| Tactic | Technique | Technique ID | Evidence | Confidence |
| :--- | :--- | :--- | :--- | :--- |
| **Initial Access** | Phishing: Spearphishing Attachment | T1566.001 | Email containing malicious archive `inv.5234353.rar` | High |
| **Execution** | User Execution: Malicious File | T1204.002 | Victim manually opened and executed the RAR payload | High |
| **Discovery** | System Owner/User Discovery | T1033 | Hostname `DESKTOP-W7F98GR` and user `tyler` in filenames | High |
| **Command and Control** | Application Layer Protocol | T1071 | Communications via standard HTTP, TLS, and FTP paths | High |
| **Credential Access** | Credentials from Password Stores | T1555 | Exfiltration of browser password report (`PW_*.html`) | High |
| **Collection** | Email Collection | T1114 | Collection and staging of Thunderbird contact databases | High |
| **Exfiltration** | Exfiltration Over Alternative Protocol | T1048 | Data exfiltrated to external server via plaintext FTP | High |

---

# Detailed Technique Analysis

## T1566.001 — Phishing: Spearphishing Attachment
The attack vector relied on a spearphishing email impersonating a shipping notification with a malicious archive attachment named `inv.5234353.rar`. This archive was designed to deliver the initial loader while evading standard gateway inspections.
* **Evidence Sources:** Phishing Email Analysis, Attachment Extraction

## T1204.002 — User Execution: Malicious File
Compromise completion required manual interaction by the victim to open the archive and execute the embedded payload. This triggered the GuLoader stager, which subsequently fetched the core AgentTesla payload.
* **Evidence Sources:** Phishing Attachment Architecture, PCAP Triage

## T1071 — Application Layer Protocol
The malware utilized common application layer protocols (`HTTP`, `HTTPS/TLS`, and `FTP`) to blend into standard outbound corporate network traffic and navigate external channels.
* **Evidence Sources:** Wireshark Protocol Hierarchy Analysis

## T1033 — System Owner/User Discovery
AgentTesla executed discovery routines to identify the system parameters of the infected host. The gathered environment metadata was appended directly into the exfiltrated file headers:
* **Recovered Hostname:** `DESKTOP-W7F98GR`
* **Recovered Username:** `tyler`
* **Evidence Sources:** FTP Packet Filename Inspection

## T1555 — Credentials from Password Stores
The primary objective of the AgentTesla payload was harvesting sensitive authentication data. The malware collected credentials stored within local browser databases and compiled them into an HTML report for transmission.
* **Evidence Sources:** FTP `STOR` Command Payload Inspection

## T1114 — Email Collection
The malware actively targeted local mail client data files, harvesting the victim's Thunderbird contact list to support potential follow-on phishing or infrastructure targeting.
* **Evidence Sources:** FTP `STOR` Thunderbird File Transmission Logs

## T1048 — Exfiltration Over Alternative Protocol
Stolen data assets were exfiltrated out of the corporate network using unencrypted FTP over Port 21, routing through an external server (`ftp.corwineagles.com`) using compromised hardcoded authentication credentials.
* **Evidence Sources:** Wireshark Follow TCP Stream Reconstruction
