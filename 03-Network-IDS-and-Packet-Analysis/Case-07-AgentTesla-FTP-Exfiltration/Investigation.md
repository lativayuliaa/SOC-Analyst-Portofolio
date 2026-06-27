# Investigation Report — GuLoader Infection Leading to AgentTesla FTP Data Exfiltration

---

# Incident Summary

This investigation analyzes a phishing campaign that delivered GuLoader malware through a malicious RAR attachment.

After execution, the malware downloaded AgentTesla, harvested user credentials, and exfiltrated the stolen information to an external FTP server.

The objective of this investigation was to reconstruct the complete attack chain using packet capture analysis and threat intelligence.

---

# Investigation Methodology

The investigation followed a structured DFIR workflow:

1. Email Analysis
2. Attachment Analysis
3. Initial PCAP Triage
4. DNS Investigation
5. HTTP Investigation
6. FTP Investigation
7. Threat Intelligence
8. IOC Collection
9. MITRE ATT&CK Mapping

---

# Phase 1 — Email Analysis

## Email Subject

```

SHIPPING DOC || INVOICE NO. USF/23-26/072 IGR23110

```

Sender

```

shipping@paramee.com

```

Attachment

```

inv.5234353.rar

```

### Analysis

The phishing email impersonated a legitimate shipping notification.

Its objective was to convince the victim to open the attached archive.

This represents the Initial Access stage of the attack.

---

# Phase 2 — Attachment Analysis

The attachment delivered to the victim was:

```

inv.5234353.rar

```

Size

```

331 KB

```

### Analysis

The compressed archive served as the malware delivery mechanism.

RAR archives are frequently used in phishing campaigns because they reduce antivirus detection and bypass email filtering.

---

# Phase 3 — Packet Capture Overview

Capture Statistics

| Item | Value |
|------|------|
| Total Packets | 353 |
| Duration | 132.308 seconds |
| Average Packet Size | 822 Bytes |
| File Size | 295 KB |

### Analysis

The capture duration indicates that the malware completed its infection and exfiltration process within approximately two minutes.

This short execution window is typical of information-stealing malware.

---

# Phase 4 — Protocol Analysis

Observed Protocols

| Protocol | Percentage |
|----------|-----------|
| TCP | 97.7% |
| TLS | 52.4% |
| FTP | 5.9% |
| HTTP | 0.6% |
| DNS | 2.3% |

### Analysis

The presence of FTP traffic is particularly significant.

Unlike encrypted HTTPS communications, FTP transmits credentials in plaintext, allowing investigators to reconstruct the attack.

---

# Phase 5 — Endpoint Analysis

Most Active Victim

```

10.2.3.101

```

Most Active External Host

```

142.251.186.132

```

### Analysis

The victim generated network activity toward multiple external services before finally communicating with the attacker's FTP infrastructure.

---

# Phase 6 — DNS Investigation

Observed Domains

```

drive.google.com

drive.usercontent.google.com

ip-api.com

ftp.corwineagles.com

```

Resolved FTP Server

```

162.241.123.75

```

### Analysis

The malware first resolved the FTP hostname before establishing an outbound connection.

DNS resolution provides a reliable indicator of attacker intent and infrastructure.

---

# Phase 7 — HTTP Investigation

Observed HTTP Requests

```

GET /line/field/hosting

HTTP/1.1 200 OK

```

### Analysis

Minimal HTTP activity was observed.

Most communications occurred through encrypted TLS sessions or FTP.

---

# Phase 8 — FTP Investigation

The FTP session revealed the complete authentication process.

Username

```

edunis@corwineagles.com

```

Password

```

cCycU=91vup7

```

FTP Commands

```

USER

PASS

PWD

TYPE I

PASV

STOR

```

### Analysis

The attacker used hardcoded FTP credentials.

Because FTP does not encrypt authentication data, both the username and password were fully recoverable from the packet capture.

---

# Phase 9 — Data Exfiltration

Uploaded Files

```

PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html

```

```

Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt

```

### Analysis

The malware successfully uploaded harvested credentials together with Thunderbird contact information.

The filenames also revealed valuable host artifacts.

Victim Hostname

```

DESKTOP-W7F98GR

```

Likely Username

```

tyler

```

---

# Screenshot

FTP STOR Password

FTP STOR Thunderbird

---

# Phase 10 — Threat Intelligence

Domain

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

Domain Creation

```

2019-01-17

```

Registrar

```

PublicDomainRegistry

```

### Analysis

Although the IP address itself was not flagged as malicious, the domain has a long history of phishing-related activity and multiple malware samples associated with it.

This indicates that the attacker abused an established domain instead of registering a newly created malicious domain.

---

# Investigation Conclusion

The investigation successfully reconstructed the complete malware lifecycle.

Evidence confirmed that:

- The attack began with a phishing email.
- A malicious RAR archive delivered GuLoader.
- AgentTesla executed on the victim system.
- DNS queries resolved attacker infrastructure.
- The malware authenticated to an external FTP server.
- Harvested browser passwords and Thunderbird contacts were successfully exfiltrated.

The packet capture provided sufficient forensic evidence to attribute the data exfiltration process and identify attacker-controlled infrastructure.
