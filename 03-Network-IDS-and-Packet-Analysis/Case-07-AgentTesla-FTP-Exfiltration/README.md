# Case 07 — GuLoader Infection Leading to AgentTesla Credential Theft and FTP Data Exfiltration

## Overview

This investigation analyzes a phishing campaign that delivered GuLoader malware through a malicious email attachment.

After execution, GuLoader downloaded and executed AgentTesla, an information-stealing malware capable of harvesting credentials and sensitive user information.

The malware communicated with external infrastructure, authenticated to an FTP server using hardcoded credentials, and exfiltrated stolen data including browser passwords and Thunderbird contact information.

The investigation was performed using Wireshark together with Threat Intelligence sources such as VirusTotal.

---

## Investigation Objectives

- Analyze the phishing email
- Identify the malicious attachment
- Investigate network communications
- Identify attacker infrastructure
- Analyze FTP authentication
- Determine exfiltrated files
- Build the attack timeline
- Map observed behavior to MITRE ATT&CK

---

## Lab Environment

| Component | Purpose |
|------------|--------------------------|
| Wireshark | Network Forensics |
| VirusTotal | Threat Intelligence |
| WHOIS | Domain Investigation |
| Windows PCAP | Malware Traffic Analysis |

---

## Scenario

The victim received a phishing email containing a malicious RAR archive disguised as a shipping document.

After opening the attachment:

- GuLoader executed
- AgentTesla was installed
- External services were contacted
- Stolen credentials were uploaded via FTP

---

## Key Findings

### Initial Access

- Email Subject:
  `SHIPPING DOC || INVOICE NO. USF/23-26/072 IGR23110`

- Attachment

```
inv.5234353.rar
```

---

### DNS Activity

Observed domains

```
drive.google.com

drive.usercontent.google.com

ip-api.com

ftp.corwineagles.com
```

---

### FTP Authentication

Username

```
edunis@corwineagles.com
```

Password

```
cCycU=91vup7
```

Authentication occurred over plaintext FTP.

---

### Exfiltrated Files

```
PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html
```

Contains harvested credentials.

```
Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt
```

Contains Thunderbird contact information.

---

### Victim Host

Hostname

```
DESKTOP-W7F98GR
```

Likely Windows username

```
tyler
```

---

## Threat Intelligence

Malicious Domain

```
corwineagles.com
```

Detection

```
18 / 91 Security Vendors
```

Resolved IP

```
162.241.123.75
```

Although the IP itself was not flagged, the domain has been associated with multiple malicious files and phishing campaigns.

---

## Investigation Workflow

1. Email Analysis
2. Attachment Analysis
3. Packet Capture Triage
4. DNS Investigation
5. HTTP Investigation
6. FTP Investigation
7. Threat Intelligence
8. MITRE ATT&CK Mapping
9. IOC Collection

---

## Skills Demonstrated

- Network Traffic Analysis
- Malware Traffic Investigation
- FTP Protocol Analysis
- DNS Investigation
- Threat Intelligence
- IOC Collection
- MITRE ATT&CK Mapping
- Digital Forensics
- Incident Response

---

## Conclusion

The investigation confirmed a complete malware infection chain beginning with a phishing email and ending with successful credential theft and data exfiltration.

Evidence demonstrated that AgentTesla authenticated to an attacker-controlled FTP server using hardcoded credentials and uploaded harvested browser passwords together with Thunderbird contact information.

This case illustrates how network forensics combined with threat intelligence can reconstruct an end-to-end malware intrusion and identify attacker infrastructure, exfiltration methods, and compromised assets.
