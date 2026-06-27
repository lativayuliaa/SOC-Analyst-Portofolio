# Indicators of Compromise (IOC)

---

# Overview

This document summarizes all Indicators of Compromise (IOCs) identified during the investigation of the GuLoader and AgentTesla malware infection.

The collected indicators include email artifacts, domains, IP addresses, FTP credentials, victim host information, and exfiltrated files.

---

# Email Indicators

| Type | Value |
|------|-------|
| Subject | SHIPPING DOC \|\| INVOICE NO. USF/23-26/072 IGR23110 |
| Sender | shipping@paramee.com |
| Attachment | inv.5234353.rar |

---

# Domain Indicators

| Domain | Description |
|---------|-------------|
| drive.google.com | Payload delivery infrastructure |
| drive.usercontent.google.com | Payload hosting |
| ip-api.com | External IP lookup performed by malware |
| ftp.corwineagles.com | FTP server used for data exfiltration |
| corwineagles.com | Parent domain associated with attacker infrastructure |

---

# IP Address Indicators

| IP Address | Description |
|------------|-------------|
| 162.241.123.75 | FTP server used for exfiltration |
| 142.251.186.132 | Google infrastructure |
| 142.250.115.138 | Google infrastructure |
| 208.95.112.14 | ip-api.com service |

---

# FTP Credentials

Username

```
edunis@corwineagles.com
```

Password

```
cCycU=91vup7
```

These credentials were transmitted over plaintext FTP and recovered directly from the packet capture.

---

# Victim Host Artifacts

Hostname

```
DESKTOP-W7F98GR
```

Likely Windows Username

```
tyler
```

Recovered from uploaded filenames.

---

# Exfiltrated Files

| Filename | Description |
|----------|-------------|
| PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html | Harvested browser passwords |
| Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt | Thunderbird contact information |

---

# Threat Intelligence

## Domain

```
corwineagles.com
```

Detection

```
18 / 91 Security Vendors
```

Creation Date

```
2019-01-17
```

Registrar

```
PublicDomainRegistry
```

Resolved IP

```
162.241.123.75
```

---

## Infrastructure Observation

Although the hosting IP was not detected as malicious, the domain itself has been linked to phishing activity and malware distribution.

This suggests the attacker abused an existing domain rather than relying on a newly registered malicious domain.

---

# Network Protocols Observed

- DNS
- HTTP
- HTTPS (TLS)
- FTP

---

# Malware Family

Observed Malware

```
GuLoader
```

Follow-on Payload

```
AgentTesla
```

---

# IOC Summary

| Category | Count |
|----------|------:|
| Email Indicators | 3 |
| Domains | 5 |
| IP Addresses | 4 |
| FTP Credentials | 2 |
| Victim Artifacts | 2 |
| Exfiltrated Files | 2 |

---

# Detection Opportunities

Security teams should monitor for:

- Outbound FTP authentication
- FTP STOR commands
- Connections to suspicious infrastructure
- Browser credential theft
- Thunderbird artifact collection
- Unexpected communication with ip-api.com following malware execution
