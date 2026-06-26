# MITRE ATT&CK Mapping

## Overview

This document maps the observed attacker behavior to the MITRE ATT&CK Enterprise Framework.

The mapping is based solely on evidence recovered during network traffic analysis and supported by Threat Intelligence.

No assumptions were made beyond the available evidence.

---

# ATT&CK Summary

| Tactic | Technique | Technique ID | Evidence | Confidence |
|---------|-----------|--------------|----------|------------|
| Resource Development | Acquire Infrastructure: Domains | T1583.001 | Newly registered malicious domains | High |
| Resource Development | Acquire Infrastructure: Server | T1583.005 | Malicious VPS hosting infrastructure | Medium |
| Initial Access | Drive-by Compromise | T1189 | Victim accessed attacker-controlled web server | High |
| Command and Control | Application Layer Protocol | T1071 | HTTP and HTTPS communication | High |
| Command and Control | Web Protocols | T1071.001 | HTTP GET requests and HTTPS communication | High |
| Command and Control | Encrypted Channel | T1573 | TLS encrypted communication | High |
| Defense Evasion | Encrypted Channel | T1573 | Payload delivered through TLS | High |

---

# Technique Details

---

## T1583.001 — Acquire Infrastructure: Domains

### Evidence

The investigation identified two attacker-controlled domains.

- forcebiturg.com
- retrypoti.top

WHOIS analysis showed that both domains were registered on the same day as the observed campaign.

This behavior is consistent with attacker-owned infrastructure created specifically for a malware campaign.

### Evidence Source

- WHOIS
- DNS
- VirusTotal

Confidence:

**High**

---

## T1583.005 — Acquire Infrastructure: Server

### Evidence

Both domains resolved to publicly accessible cloud-hosted IP addresses.

Although ownership cannot be confirmed, the infrastructure appears to have been provisioned specifically for campaign delivery.

### Evidence Source

- DNS Resolution
- Threat Intelligence

Confidence:

**Medium**

Reason:

The hosting provider is observable, but direct attacker ownership cannot be confirmed from network evidence alone.

---

## T1189 — Drive-by Compromise

### Evidence

The victim initiated an HTTP request to an attacker-controlled domain.

Observed requests:

```
GET /boot

GET /proc
```

The server redirected the victim to HTTPS before subsequent encrypted communication.

This behavior is consistent with web-based malware delivery.

### Evidence Source

- HTTP
- DNS

Confidence:

High

---

## T1071 — Application Layer Protocol

### Evidence

The attacker communicated using standard web protocols.

Observed:

- HTTP
- HTTPS
- TLS

The use of legitimate application protocols helps attacker traffic blend with normal network activity.

### Evidence Source

- Protocol Hierarchy
- HTTP
- TLS

Confidence:

High

---

## T1071.001 — Web Protocols

### Evidence

The investigation identified:

- HTTP GET
- HTTP Redirect
- HTTPS
- TLS

The attacker relied entirely on web protocols for communication.

### Evidence Source

- HTTP Requests
- TLS Stream

Confidence:

High

---

## T1573 — Encrypted Channel

### Evidence

Following the HTTP redirect, all communication occurred through encrypted TLS.

Observed evidence:

- TLS Handshake
- TLS Certificate
- TLS Application Data
- Encrypted TCP Stream

Because the payload remained encrypted, content inspection was not possible.

This demonstrates attacker use of encrypted communication to protect malware delivery.

### Evidence Source

- TLS Stream
- Follow TCP Stream

Confidence:

High

---

# ATT&CK Matrix Summary

| Tactic | Techniques Observed |
|---------|--------------------|
| Resource Development | T1583.001, T1583.005 |
| Initial Access | T1189 |
| Command and Control | T1071, T1071.001, T1573 |
| Defense Evasion | T1573 |

---

# Investigation Notes

This investigation was performed using network evidence only.

No malware execution, memory analysis, endpoint telemetry, or host artifacts were available.

Therefore, techniques related to persistence, privilege escalation, credential access, discovery, lateral movement, or exfiltration could not be confirmed.

Only ATT&CK techniques directly supported by observed evidence were included.

---

# Analyst Assessment

The observed attack demonstrates a typical modern malware delivery workflow.

The attacker prepared dedicated infrastructure, exposed a web endpoint, redirected the victim to an encrypted TLS session, and concealed subsequent communication inside HTTPS traffic.

The MITRE ATT&CK mapping indicates that the campaign primarily focused on web-based delivery and encrypted command-and-control communication rather than techniques observable from endpoint telemetry.
