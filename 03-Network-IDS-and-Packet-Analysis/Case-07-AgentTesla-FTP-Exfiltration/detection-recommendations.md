# Detection Recommendations

## 📌 Overview
This document provides security recommendations derived from the forensic investigation of the **GuLoader and AgentTesla malware campaign**. The objective is to translate investigative findings into actionable detection strategies that improve organizational visibility, strengthen defensive monitoring, and reduce the likelihood of future compromise.

---

## 🔍 Key Detection Opportunities

### 1. Detect Suspicious Email Attachments

**Observation**

The attack originated from a phishing email containing a compressed archive (`inv.5234353.rar`) designed to bypass traditional email filtering mechanisms.

**Detection Recommendation**

Monitor and generate alerts for inbound emails containing compressed archive attachments such as:

- `.rar`
- `.zip`
- `.7z`
- `.iso`

Increase alert severity when attachment delivery is combined with financial or logistics-related keywords in the email subject, including:

- Shipping
- Invoice
- Purchase Order
- Payment
- Quotation

---

### 2. Detect Plaintext FTP Authentication

**Observation**

The malware authenticated to the external FTP server `ftp.corwineagles.com` using plaintext `USER` and `PASS` commands over TCP Port 21.

**Detection Recommendation**

Generate high-priority alerts whenever internal endpoints initiate outbound FTP authentication sessions.

Because FTP is rarely required for modern workstation environments, outbound authentication attempts should be considered suspicious unless explicitly authorized.

---

### 3. Detect FTP File Upload Activity

**Observation**

The malware exfiltrated stolen information using the FTP `STOR` command, uploading files such as:

- `PW_*.html`
- `Contacts_Thunderbird.txt`

**Detection Recommendation**

Create IDS or SIEM detection rules that alert whenever:

- FTP `STOR` commands are observed
- Internal workstations upload files through FTP
- Multiple file uploads occur during a single FTP session

This behavior may indicate active data exfiltration.

---

### 4. Detect Credential & Email Client Harvesting

**Observation**

The malware accessed local browser credential databases and Thunderbird profile data to collect stored credentials and contact information.

**Detection Recommendation**

Deploy endpoint monitoring to detect unusual access to:

- Browser credential databases
- Password storage locations
- Thunderbird profile directories
- Microsoft Outlook PST files
- Email client address books

Unexpected process access to these locations should generate investigation alerts.

---

### 5. Detect Automated Public IP Lookups

**Observation**

Immediately after execution, the malware queried public IP lookup services to identify the victim's external IP address.

Examples observed include:

- `ip-api.com`

**Detection Recommendation**

Alert when newly spawned or untrusted processes communicate with public IP discovery services, including:

- `ip-api.com`
- `ipify.org`
- `ifconfig.me`
- `checkip.amazonaws.com`

This behavior is commonly observed during malware initialization and beacon preparation.

---

## 🌐 Threat Intelligence Enrichment

The investigation identified the domain **corwineagles.com** as malicious.

VirusTotal reported detections from multiple security vendors, indicating that the infrastructure has an established malicious reputation.

Security teams should continuously enrich DNS and network telemetry using Threat Intelligence sources such as:

- VirusTotal
- AbuseIPDB
- URLHaus

Threat intelligence enrichment enables earlier identification of malicious infrastructure before malware communication progresses further.

---

## 📊 SIEM Correlation Strategy

Rather than alerting on isolated events, correlate multiple related activities into a single high-confidence detection.

```text
Phishing Email Received (.rar Attachment)
                │
                ▼
Archive Extraction
                │
                ▼
Suspicious Process Execution
                │
                ▼
Public IP Lookup Request
                │
                ▼
Outbound DNS Resolution
                │
                ▼
FTP USER / PASS Authentication
                │
                ▼
FTP STOR File Upload
                │
                ▼
🚨 High-Severity SIEM Incident
```

Correlating multiple stages significantly reduces false positives while improving detection fidelity.

---

## 🛡️ Recommended Security Controls

- Implement advanced email filtering for compressed archive attachments.
- Block or restrict outbound FTP traffic from user workstations.
- Monitor FTP authentication and file upload activity.
- Enable endpoint monitoring for browser credential stores and email client data.
- Integrate DNS telemetry with Threat Intelligence feeds.
- Create correlation rules linking phishing, process execution, DNS, FTP authentication, and file transfer events.
- Continuously update IDS, SIEM, and EDR detection rules using newly discovered Indicators of Compromise (IOCs).

---

## 📌 Conclusion

The investigation demonstrates how **GuLoader** and **AgentTesla** leverage multiple stages—including phishing, credential harvesting, and FTP-based data exfiltration—to compromise victim systems.

Organizations should adopt layered detection strategies that combine **email security, endpoint telemetry, network monitoring, threat intelligence, and SIEM correlation**. Correlating multiple indicators across the attack lifecycle substantially increases the likelihood of detecting information-stealing malware before sensitive data is successfully exfiltrated.
