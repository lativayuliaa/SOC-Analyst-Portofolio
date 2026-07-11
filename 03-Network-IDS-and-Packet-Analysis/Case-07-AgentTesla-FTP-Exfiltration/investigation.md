# Investigation Report

## 📋 Case Information

| Item | Value |
| :--- | :--- |
| **Case ID** | Case-07 |
| **Investigation Title** | GuLoader Infection Leading to AgentTesla FTP Data Exfiltration |
| **Analyst** | Lativa Yulia Taviani |
| **Tool** | Wireshark |
| **Dataset** | GuLoader → AgentTesla Infection PCAP |
| **Investigation Type** | Network Forensics |
| **Status** | Completed |

---

# Investigation Objective

The objective of this investigation was to reconstruct the complete attack chain of a phishing campaign that delivered **GuLoader**, which subsequently downloaded and executed **AgentTesla**. The investigation focused on identifying the infection vector, attacker infrastructure, credential theft activity, FTP-based data exfiltration, and supporting Indicators of Compromise (IOCs) using packet capture analysis and Threat Intelligence.

---

# Investigation Methodology

The investigation followed a structured Digital Forensics and Incident Response (DFIR) workflow:

1. Email Analysis
2. Attachment Analysis
3. Packet Capture Triage
4. Protocol & Endpoint Analysis
5. DNS & HTTP Investigation
6. FTP Session Investigation
7. Threat Intelligence Validation
8. IOC Collection
9. MITRE ATT&CK Mapping

---

# Phase 1 — Email Analysis

The phishing campaign originated from an email impersonating a legitimate shipping notification.

**Email Details**

| Item | Value |
| :--- | :--- |
| **Subject** | `SHIPPING DOC \|\| INVOICE NO. USF/23-26/072 IGR23110` |
| **Sender** | `shipping@paramee.com` |
| **Attachment** | `inv.5234353.rar` |

![Phishing Email Structure Layout](assets/ss-02-email-overview.png)

### Analysis

The attacker used social engineering to convince the victim to open the attached archive, representing the **Initial Access** stage of the attack.

---

# Phase 2 — Attachment Analysis

The delivered attachment was:

```text
inv.5234353.rar
```

**File Size**

```text
331 KB
```

![Phishing Email Malicious RAR Attachment Details](assets/ss-03-email-attachment.png)

### Analysis

RAR archives are commonly used during phishing campaigns because they reduce antivirus detection rates and can bypass legacy email attachment filters. After extraction, the archive executed the GuLoader malware.

---

# Phase 3 — Packet Capture Overview

The investigation workspace was prepared before beginning packet analysis.

![Investigation Workspace Capture Directory](assets/ss-01-files-overview.png)

The packet capture was then opened in Wireshark.

![Wireshark Initial Capture Workspace](assets/ss-04-wireshark-overview.png)

### Capture Statistics

| Item | Value |
| :--- | :--- |
| **Total Packets** | 353 |
| **Capture Duration** | 132.308 Seconds |
| **Average Packet Size** | 822 Bytes |
| **Capture Size** | 295 KB |

![Wireshark Global Capture Properties Metrics](assets/ss-05-capture-properties.png)

### Analysis

The malware completed the entire infection and exfiltration process in approximately two minutes, which is characteristic of modern information-stealing malware.

---

# Phase 4 — Protocol & Endpoint Analysis

## Protocol Distribution

| Protocol | Percentage |
| :--- | ---: |
| **TCP** | 97.7% |
| **TLS** | 52.4% |
| **FTP** | 5.9% |
| **DNS** | 2.3% |
| **HTTP** | 0.6% |

![Wireshark Protocol Hierarchy Distribution Summary](assets/ss-06-protocol-hierarchy.png)

### Analysis

The protocol hierarchy highlights significant FTP traffic. Since FTP transmits authentication and transferred files without encryption, the complete session could be reconstructed from the packet capture.

The IPv4 endpoint statistics identified the primary internal victim system.

```text
Primary Internal Victim:
10.2.3.101
```

---

# Phase 5 — DNS & HTTP Investigation

The malware generated outbound DNS requests to locate external infrastructure.

**Observed Domains**

- drive.google.com
- drive.usercontent.google.com
- ip-api.com
- ftp.corwineagles.com

**Resolved FTP Server**

```text
162.241.123.75
```

### Analysis

The malware contacted Google infrastructure to retrieve payload components before querying `ip-api.com` to determine the victim's public IP address. It subsequently resolved the attacker-controlled FTP server used for data exfiltration.

---

# Phase 6 — FTP Authentication Investigation

Once the malware established the FTP connection, the authentication sequence was transmitted in plaintext.

**FTP Username**

```text
USER edunis@corwineagles.com
```

**FTP Password**

```text
PASS cCycU=91vup7
```

### Analysis

Because FTP does not provide encryption, both authentication credentials were fully recoverable directly from the packet capture.

---

# Phase 7 — Data Exfiltration Analysis

Following successful authentication, AgentTesla uploaded harvested information using multiple FTP `STOR` commands.

### Browser Credential Report

```text
PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html
```

### Thunderbird Contact List

```text
Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt
```

The entire FTP conversation was reconstructed using **Follow TCP Stream**, exposing the complete unencrypted communication between the victim and the attacker's FTP server.

### Host Artifacts Identified

**Hostname**

```text
DESKTOP-W7F98GR
```

**Username**

```text
tyler
```

### Analysis

The uploaded filenames revealed both the victim hostname and user account, confirming successful browser credential theft and Thunderbird contact collection prior to exfiltration.

---

# Phase 8 — Threat Intelligence Validation

The attacker infrastructure was validated using external Threat Intelligence sources.

**Target Domain**

```text
corwineagles.com
```

### Findings

- Detected by **18/91** VirusTotal security vendors.
- Historical reputation associated with phishing and malware delivery.
- FTP server resolved to:

```text
162.241.123.75
```

### Analysis

Although the hosting IP address itself had relatively few detections, the associated domain had a well-established history of malicious activity. This suggests the attacker abused an existing legitimate hosting environment rather than deploying newly registered infrastructure.

---

# Investigation Conclusion

The investigation successfully reconstructed the complete malware lifecycle from phishing delivery through successful FTP-based data exfiltration.

The collected evidence confirmed that:

- A phishing email delivered a malicious RAR archive.
- The archive executed **GuLoader**.
- GuLoader downloaded and launched **AgentTesla**.
- AgentTesla queried `ip-api.com` to determine the victim's public IP address.
- Browser credentials and Thunderbird contacts were harvested.
- Stolen information was uploaded through plaintext FTP using hardcoded credentials.
- The attacker-controlled infrastructure was identified as:

```text
ftp.corwineagles.com
162.241.123.75
```

The packet capture provided sufficient forensic evidence to reconstruct the entire attack sequence, recover attacker credentials, identify compromised host artifacts, and attribute the data exfiltration process with high confidence.
