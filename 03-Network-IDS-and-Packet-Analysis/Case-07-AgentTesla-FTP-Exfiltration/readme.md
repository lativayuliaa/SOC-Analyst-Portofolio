# Case 07 — GuLoader Infection Leading to AgentTesla Credential Theft and FTP Data Exfiltration

## Overview
This investigation analyzes a phishing campaign that delivered GuLoader malware through a malicious email attachment. After execution, GuLoader downloaded and executed AgentTesla, an information-stealing malware capable of harvesting credentials and sensitive user information.

The malware communicated with external infrastructure, authenticated to an FTP server using hardcoded credentials, and exfiltrated stolen data including browser passwords and Thunderbird contact information. The investigation was performed using Wireshark together with Threat Intelligence sources such as VirusTotal.

---

## Lab Files Overview
Before commencing deep packet triage, the context of the investigation artifacts was baseline audited to account for the core capture file and the source phishing email package:

![Lab Environment Files Overview](assets/ss-01-files-overview.png)

---

## Investigation Objectives
* Analyze the phishing email structure and transmission context.
* Identify the malicious payload delivery attachment.
* Investigate outbound network communications.
* Map attacker-controlled staging and exfiltration infrastructure.
* Analyze unencrypted FTP authentication flows.
* Determine exactly what data files were exfiltrated.
* Build a granular post-compromise attack timeline.
* Map observed adversarial behavior to the MITRE ATT&CK Framework.

---

## Lab Environment

| Component | Purpose |
| :--- | :--- |
| **Wireshark** | Network Forensics & Protocol Dissection |
| **VirusTotal** | Threat Intelligence & Infrastructure Reputation |
| **WHOIS** | Domain Registration History Investigation |
| **Windows PCAP** | Malware Traffic Stream Analysis |

---

## Scenario
The victim received a phishing email containing a malicious RAR archive disguised as a shipping document. After opening the attachment:

* GuLoader executed
* AgentTesla was installed
* External services were contacted for public IP mapping
* Stolen credential reports were uploaded via plaintext FTP

---

## Investigation Workflow & Step-by-Step Packet Mapping

### Step 1: Phishing Email & Attachment Analysis
The initial access mechanism relies on deceptive email notifications impersonating logistics communications to manipulate end-users into running unverified archive attachments:

![Phishing Email Message Document Overview](assets/ss-02-email-overview.png)

Extracting the metadata of the archive payload confirms the delivery package naming convention:

```text
Attachment: inv.5234353.rar
```

---

### Step 2: Global Packet Capture Triage
Opening the raw transaction capture in Wireshark establishes the foundational baseline overview of the transmission window:

![Wireshark Initial Capture Workspace](assets/ss-04-wireshark-overview.png)

Auditing the core packet file properties defines the exact time boundaries and packet densities:

* Total Packets: 353
* Duration: 132.308 Seconds
* File Size: 295 KB

![Wireshark Global Capture Properties Metrics](assets/ss-05-capture-properties.png)

---

### Step 3: Protocol & Endpoint Isolation
The protocol hierarchy statistics identify the usage of multiple application layer protocols, highlighting unencrypted FTP traffic which represents a major investigative opportunity:

![Wireshark Protocol Hierarchy Distribution Summary](assets/ss-06-protocol-hierarchy.png)

Analyzing the IPv4 address endpoints isolates the internal local workstation endpoint from external destination servers:

![Wireshark IPv4 Endpoints Summary](assets/ss-07-endpoints.png)

```text
Internal Victim: 10.2.3.101
```

Reviewing the layer-4 transport conversations exposes active session routing mapping out to primary external endpoints:

![Wireshark TCP Conversation Analysis](assets/ss-08-conversations.png)

---

### Step 4: Infrastructure Staging & Public IP Discovery
The malware initiates automated DNS translation queries to resolve payload download sites, geo-location mapping APIs, and its hardcoded exfiltration gateway:

![Wireshark DNS Query Analysis](assets/ss-09-dns-query.png)

HTTP communication queries trace the low-level cleartext payload components fetching routes before shifting traffic channels:

![Wireshark HTTP Request Analysis](assets/ss-10-http-query.png)

A broader review of the unencrypted transport layer transactions shows the execution transition into the active exfiltration phase:

![Wireshark TCP Request Analysis](assets/ss-11-tp-request.png)

---

### Step 5: Plaintext FTP Session & Exfiltration Reconstruction
Because the malware utilized standard unencrypted FTP (Port 21), all adversarial session interaction logs were fully exposed in cleartext. The analyst captured the exact username submitted during authentication:

![FTP USER Command Analysis](assets/ss-12-ftp-user.png)

```text
USER: edunis@corwineagles.com
```

Following the username transmission, the malware sent the accompanying static pass-key validation token over the wire:

![FTP PASS Command Analysis](assets/ss-13-ftp-pass.png)

```text
PASS: cCycU=91vup7
```

Once authenticated, the AgentTesla payload executed an FTP STOR instruction to transmit the local browser credential store report:

![FTP STOR Browser Credential Upload](assets/ss-14-ftp-stor-pw.png)

```text
File Uploaded:
PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html
```

A subsequent FTP STOR command was recorded seconds later, exfiltrating the local Thunderbird contact list configuration files:

![FTP STOR Thunderbird Contact Upload](assets/ss-15-ftp-stor-thunderbird.png)

```text
File Uploaded:
Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt
```

Reassembling the conversation via Follow TCP Stream provides a comprehensive look at the sequential command-and-response exfiltration loop:

![Follow TCP Stream Reconstruction](assets/ss-16-follow-tcp-stream.png)

---

### Step 6: External Threat Intelligence Validation
The infrastructure indicators extracted from the packet flows were cross-checked against global reputation indexes to confirm adversarial association.

Domain Reputation (*corwineagles.com*): Extensively flagged as a malicious hosting entity linked to phishing distribution:

![VirusTotal Domain Reputation Analysis](assets/ss-17-virustotal-domain.png)

Exfiltration Server IP Reputation (162.241.123.75): Validated against network routing history tracking active infrastructure abuse:

![VirusTotal IP Reputation Analysis](assets/ss-18-virustotal-ip.png)

---

## Key Findings Summary

**Victim System**

* Hostname: `DESKTOP-W7F98GR`
* Username: `tyler`
* Internal IP: `10.2.3.101`

**Exfiltration Infrastructure**

* FTP Server: `ftp.corwineagles.com`
* IP Address: `162.241.123.75`

**Recovered Credentials**

```text
Username: edunis@corwineagles.com
Password: cCycU=91vup7
```

**Exfiltrated Artifacts**

* Browser credential reports (`PW_*.html`)
* Thunderbird contact database (`Contacts_Thunderbird*.txt`)

---

## Skills Demonstrated

* Network Traffic & Packet Dissection Analysis
* Malware Infrastructure Tracking
* Cleartext Protocol Forensics (FTP Session Reconstruction)
* DNS Domain Mapping & Translation Analysis
* Automated Public IP Discovery Profiling
* Threat Intelligence Enrichment & Indicator Extraction
* MITRE ATT&CK Tactic & Technique Attribution
