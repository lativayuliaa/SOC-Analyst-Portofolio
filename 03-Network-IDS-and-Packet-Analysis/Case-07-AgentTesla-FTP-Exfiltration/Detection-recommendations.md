# Detection Recommendations

---

# Overview

This document provides security recommendations based on the findings of the investigation.

The objective is to improve detection capabilities and reduce the likelihood of future GuLoader and AgentTesla infections.

---

# Detection Opportunities

The investigation identified several observable behaviors that can be monitored by security teams.

These behaviors can be converted into IDS signatures, SIEM correlation rules, threat hunting queries, and endpoint detections.

---

# 1. Detect Suspicious Email Attachments

### Observation

The attack began with a phishing email containing a compressed archive.

Attachment

```
inv.5234353.rar
```

### Recommendation

Monitor inbound emails containing:

- .rar
- .zip
- .7z
- .iso

especially when combined with:

- Shipping
- Invoice
- Purchase Order
- Payment
- Quotation

subjects.

---

# 2. Detect FTP Authentication

### Observation

The malware authenticated to an external FTP server.

Recovered credentials

```
USER edunis@corwineagles.com
```

```
PASS cCycU=91vup7
```

### Recommendation

Generate alerts for:

- outbound FTP connections
- FTP USER commands
- FTP PASS commands

Many organizations do not require outbound FTP, making these events highly suspicious.

---

# 3. Detect FTP File Uploads

### Observation

The malware uploaded files using the FTP STOR command.

Observed commands

```
STOR
```

Uploaded files

```
PW_*.html

Contacts_Thunderbird.txt
```

### Recommendation

Alert whenever outbound FTP STOR commands are observed.

This behavior frequently indicates data exfiltration.

---

# 4. Detect Password Theft

### Observation

The malware generated

```
PW_tyler-DESKTOP-W7F98GR...
```

### Recommendation

Monitor endpoint activity involving:

- Browser credential stores
- Password export
- Credential dumping
- Password report generation

---

# 5. Detect Email Client Collection

### Observation

Thunderbird contacts were collected.

### Recommendation

Monitor unusual access to:

- Thunderbird profile directory
- Outlook PST files
- Address books
- Email databases

---

# 6. Detect Public IP Lookup

### Observation

The malware queried

```
ip-api.com
```

### Recommendation

Alert when newly executed processes immediately access:

- ip-api.com
- ipify.org
- ifconfig.me
- checkip.amazonaws.com

This behavior is common among commodity malware.

---

# 7. DNS Monitoring

Observed domains

```
ftp.corwineagles.com

drive.google.com

drive.usercontent.google.com

ip-api.com
```

### Recommendation

Monitor DNS queries to:

- newly observed domains
- low reputation domains
- attacker-controlled infrastructure

Correlate DNS activity with subsequent outbound connections.

---

# 8. Threat Intelligence Integration

The domain

```
corwineagles.com
```

was detected by

```
18 / 91
```

security vendors.

### Recommendation

Continuously enrich DNS logs using:

- VirusTotal
- AbuseIPDB
- URLHaus
- AlienVault OTX

to identify known malicious infrastructure.

---

# SOC Hunting Ideas

Threat hunters should search for:

- Outbound FTP sessions
- FTP authentication
- FTP STOR commands
- Browser credential collection
- Thunderbird profile access
- Connections to IP lookup services
- Newly observed DNS domains
- Google Drive downloads immediately followed by suspicious outbound connections

---

# Suricata Detection Ideas

Potential detection opportunities include:

- FTP USER command
- FTP PASS command
- FTP STOR command
- Excessive outbound FTP traffic
- Suspicious DNS queries
- Malware download followed by FTP activity

---

# SIEM Correlation Ideas

Example correlation sequence

```
Phishing Email

↓

RAR Attachment

↓

Google Download

↓

DNS Resolution

↓

FTP Login

↓

FTP Upload

↓

High Severity Alert
```

Rather than alerting on individual events, correlate multiple related activities to reduce false positives.

---

# Lessons Learned

This investigation demonstrates that even when malware binaries are unavailable, packet captures alone can provide sufficient evidence to reconstruct the attack.

By combining:

- Email analysis
- Network forensics
- FTP inspection
- DNS investigation
- Threat intelligence

analysts can successfully identify attacker infrastructure, recover stolen credentials, and understand the complete attack lifecycle.

---

# Conclusion

Organizations should prioritize monitoring outbound FTP traffic, phishing attachments, DNS activity, and credential theft behavior.

Combining multiple detection sources significantly increases the likelihood of detecting information-stealing malware such as GuLoader and AgentTesla before successful data exfiltration occurs.
