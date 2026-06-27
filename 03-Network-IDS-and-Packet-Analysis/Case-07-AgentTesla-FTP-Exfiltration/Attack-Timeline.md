# Attack Timeline

---

# Overview

This timeline reconstructs the complete attack chain observed during the network investigation.

The analysis is based on packet captures, FTP sessions, DNS traffic, HTTP communications, and threat intelligence.

---

# Attack Timeline

| Phase | Activity | Evidence |
|--------|----------|----------|
| 1 | Phishing email delivered | Shipping-themed email with malicious attachment |
| 2 | Victim opens attachment | `inv.5234353.rar` executed |
| 3 | GuLoader executes | Initial malware loader begins execution |
| 4 | AgentTesla downloaded and executed | Follow-on malware activity observed |
| 5 | DNS resolution | `drive.google.com`, `drive.usercontent.google.com`, `ip-api.com`, `ftp.corwineagles.com` |
| 6 | Google infrastructure contacted | Malware retrieves payload/components |
| 7 | Public IP lookup | Connection to `ip-api.com` |
| 8 | FTP infrastructure resolved | `ftp.corwineagles.com` → `162.241.123.75` |
| 9 | FTP authentication | USER / PASS observed in plaintext |
| 10 | Password report uploaded | `PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html` |
| 11 | Thunderbird contacts uploaded | `Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt` |
| 12 | Data exfiltration completed | FTP STOR commands completed successfully |

---

# Detailed Timeline

---

## Phase 1 — Initial Access

The attack started with a phishing email impersonating a shipping notification.

Subject

```
SHIPPING DOC || INVOICE NO. USF/23-26/072 IGR23110
```

Attachment

```
inv.5234353.rar
```

Objective:

Convince the victim to execute the attachment.

---

## Phase 2 — Malware Execution

After the victim opened the archive, GuLoader executed.

GuLoader acted as a malware downloader responsible for delivering the final payload.

Observed malware family:

```
GuLoader
```

↓

```
AgentTesla
```

---

## Phase 3 — External Communication

Immediately after execution, outbound DNS requests were observed.

Resolved domains included:

```
drive.google.com

drive.usercontent.google.com

ip-api.com

ftp.corwineagles.com
```

Purpose:

- Retrieve payload
- Identify victim's public IP
- Resolve attacker infrastructure

---

## Phase 4 — FTP Authentication

The malware established an FTP session.

Recovered credentials

Username

```
edunis@corwineagles.com
```

Password

```
cCycU=91vup7
```

Because FTP is not encrypted, both credentials were visible directly inside the packet capture.

---

## Phase 5 — Credential Theft

The malware uploaded

```
PW_tyler-DESKTOP-W7F98GR_2026_02_03_16_13_59.html
```

This file strongly indicates harvested browser credentials.

Recovered victim artifacts

Hostname

```
DESKTOP-W7F98GR
```

Likely Windows username

```
tyler
```

---

## Phase 6 — Email Data Collection

A second upload followed only a few seconds later.

Uploaded file

```
Contacts_Thunderbird.txt_tyler-DESKTOP-W7F98GR_2026_02_03_16_14_02.txt
```

This indicates collection of Thunderbird contact information.

---

## Phase 7 — Data Exfiltration

The malware completed the attack by uploading stolen files through FTP using STOR commands.

Observed commands

```
USER

PASS

TYPE I

PASV

STOR
```

No evidence suggested that the upload failed.

The captured traffic indicates successful data exfiltration.

---

# Complete Attack Flow

```
Phishing Email
        │
        ▼
RAR Attachment
        │
        ▼
Victim Execution
        │
        ▼
GuLoader
        │
        ▼
AgentTesla
        │
        ▼
Google Infrastructure
        │
        ▼
Public IP Lookup
        │
        ▼
FTP Login
        │
        ▼
Credential Theft
        │
        ▼
Thunderbird Collection
        │
        ▼
FTP Data Exfiltration
```

---

# Conclusion

The investigation reconstructed the entire attack lifecycle from initial phishing delivery to successful FTP-based data exfiltration.

Every major stage of the attack was supported by network evidence, allowing investigators to identify attacker infrastructure, stolen data, victim host artifacts, and the exfiltration mechanism.
