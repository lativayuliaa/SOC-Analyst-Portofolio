# Indicators of Compromise (IOC) Report

## Overview

This report documents all Indicators of Compromise (IOCs) identified during the investigation of the SmartApeSG ClickFix campaign associated with Remcos RAT.

The IOCs were extracted through network traffic analysis and validated using external Threat Intelligence sources.

---

# IOC Summary

| IOC | Type | Source | Confidence | Description |
|------|------|--------|------------|-------------|
| 10.3.12.101 | Victim IP | Endpoint Statistics | High | Internal host identified as the victim system |
| 159.65.191.64 | External IP | DNS Response | High | IP address hosting forcebiturg.com |
| 24.199.121.166 | External IP | DNS Response | Medium | IP address associated with retrypoti.top |
| forcebiturg.com | Domain | DNS + HTTP | High | Initial malicious domain contacted by the victim |
| retrypoti.top | Domain | TLS Certificate + DNS | High | Secondary malicious infrastructure observed during encrypted communication |
| GET /boot | URI | HTTP Request | High | Initial HTTP request issued by the victim |
| GET /proc | URI | HTTP Request | High | Secondary HTTP request observed before TLS redirection |
| curl/8.18.0 | User-Agent | HTTP Header | Medium | Indicates automated HTTP request rather than browser activity |
| HTTP 301 Moved Permanently | HTTP Response | HTTP | High | Redirect from HTTP to HTTPS |
| TLS Application Data | TLS | TLS Stream | High | Encrypted communication following initial web requests |

---

# Malicious Domains

## forcebiturg.com

| Property | Value |
|----------|-------|
| Type | Domain |
| Role | Initial Web Infrastructure |
| Resolved IP | 159.65.191.64 |
| Detection | Multiple security vendors classified the domain as malicious |
| Registration Date | 2026-03-12 |
| Confidence | High |

### Evidence

- DNS Query
- DNS Response
- HTTP Host Header
- HTTP GET Request
- VirusTotal
- WHOIS

---

## retrypoti.top

| Property | Value |
|----------|-------|
| Type | Domain |
| Role | Secondary Infrastructure |
| Resolved IP | 24.199.121.166 |
| Detection | Multiple security vendors classified the domain as malicious |
| Registration Date | 2026-03-12 |
| Confidence | High |

### Evidence

- TLS Certificate
- DNS Response
- VirusTotal
- WHOIS

---

# Network Indicators

## Victim

| IOC | Description |
|------|-------------|
| 10.3.12.101 | Internal workstation communicating with attacker infrastructure |

---

## External Infrastructure

| IOC | Description |
|------|-------------|
| 159.65.191.64 | Initial malicious web server |
| 24.199.121.166 | Additional infrastructure observed after HTTPS redirection |

---

# HTTP Indicators

## HTTP Requests

```
GET /boot
GET /proc
```

These requests represent the initial stage of communication between the victim and the attacker-controlled infrastructure.

---

## HTTP User-Agent

```
curl/8.18.0
```

The User-Agent indicates that the request was generated using cURL rather than a standard web browser.

This behavior is consistent with automated download activity or scripted execution.

---

## HTTP Response

```
301 Moved Permanently
```

The attacker redirected the victim from HTTP to HTTPS before delivering the encrypted payload.

---

# TLS Indicators

Evidence observed:

- TLS Handshake
- TLS Certificate
- TLS Application Data
- High-volume encrypted communication

Because the payload was encrypted, direct extraction was not possible.

---

# Threat Intelligence Validation

## VirusTotal

Both identified domains were detected by multiple security vendors.

Threat Intelligence supported the conclusion that both domains were malicious.

---

## WHOIS

WHOIS analysis revealed:

- Both domains were registered on the same day as the campaign.
- Newly registered infrastructure is consistent with short-lived attacker infrastructure.
- retrypoti.top was later suspended by the registrar.

---

# Confidence Assessment

| IOC | Confidence | Reason |
|------|------------|--------|
| Victim IP | High | Directly observed in PCAP |
| forcebiturg.com | High | DNS, HTTP, VirusTotal, WHOIS |
| retrypoti.top | High | TLS, DNS, VirusTotal, WHOIS |
| 159.65.191.64 | High | DNS resolution and HTTP communication |
| 24.199.121.166 | Medium | DNS and TLS evidence only |
| GET /boot | High | Direct HTTP request |
| GET /proc | High | Direct HTTP request |
| curl/8.18.0 | Medium | Indicates automation but not malware by itself |
| TLS Application Data | High | Clearly observed throughout encrypted communication |

---

# Analyst Conclusion

The extracted Indicators of Compromise collectively describe the infrastructure used during the SmartApeSG ClickFix campaign.

Although the malware payload remained encrypted, the combination of DNS artifacts, HTTP communication, TLS evidence, WHOIS records, and Threat Intelligence provides high confidence that the observed activity is consistent with the delivery of Remcos RAT.
