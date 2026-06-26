# Attack Timeline

## Overview

This timeline reconstructs the SmartApeSG ClickFix campaign based on evidence collected from packet capture analysis, DNS investigation, HTTP requests, TLS communications, and Threat Intelligence.

The timestamps shown below follow the sequence of attacker activity observed during the investigation.

---

# Attack Timeline

| Phase | Activity | Evidence |
|--------|----------|----------|
| 1 | Victim initiates DNS lookup for **forcebiturg.com** | DNS Query |
| 2 | DNS server resolves **forcebiturg.com** to **159.65.191.64** | DNS Response |
| 3 | Victim establishes an HTTP connection | TCP Handshake |
| 4 | Victim sends **HTTP GET /boot** | HTTP Request |
| 5 | Victim sends **HTTP GET /proc** | HTTP Request |
| 6 | User-Agent identified as **curl/8.18.0** | HTTP Header |
| 7 | Server responds with **HTTP 301 Moved Permanently** | HTTP Response |
| 8 | Victim follows redirect to HTTPS | HTTP Redirect |
| 9 | TLS Handshake begins | TLS Handshake |
|10 | TLS certificate reveals **retrypoti.top** | TLS Certificate |
|11 | DNS resolves **retrypoti.top** to **24.199.121.166** | DNS Response |
|12 | Large encrypted TLS Application Data is exchanged | TLS Stream |
|13 | High-volume PSH, ACK packets indicate encrypted payload transfer | TCP Stream |
|14 | Threat Intelligence confirms both domains as malicious | VirusTotal |
|15 | WHOIS shows domains were registered immediately before the campaign | WHOIS |

---

# Attack Chain

```text
Victim (10.3.12.101)
        │
        ▼
DNS Query
        │
        ▼
forcebiturg.com
159.65.191.64
        │
HTTP GET /boot
HTTP GET /proc
        │
301 Moved Permanently
        │
HTTPS Redirect
        ▼
TLS Handshake
        │
TLS Certificate
        ▼
retrypoti.top
24.199.121.166
        │
Encrypted TLS Communication
        │
Large Application Data Transfer
        ▼
Activity Consistent with SmartApeSG ClickFix Campaign
```

---

# Attack Phases

## Phase 1 — Infrastructure Discovery

The victim resolved the attacker-controlled domain using DNS.

Evidence:

- DNS Query
- DNS Response

Result:

The malicious infrastructure became reachable.

---

## Phase 2 — Initial Web Request

The victim initiated an HTTP connection.

Observed requests:

- GET /boot
- GET /proc

User-Agent:

```
curl/8.18.0
```

This suggests an automated request rather than normal browser activity.

---

## Phase 3 — Redirect to HTTPS

Instead of serving content directly over HTTP, the server instructed the victim to switch to HTTPS.

Evidence:

```
301 Moved Permanently
```

This behavior is commonly used to protect attacker infrastructure and conceal payload delivery.

---

## Phase 4 — Encrypted Communication

Following the redirect, the victim established an encrypted TLS session.

Evidence included:

- TLS Handshake
- TLS Certificate
- TLS Application Data
- PSH, ACK packets

Because all subsequent traffic was encrypted, the payload itself could not be inspected.

---

## Phase 5 — Infrastructure Expansion

TLS inspection identified a second attacker-controlled domain:

```
retrypoti.top
```

The domain resolved to:

```
24.199.121.166
```

This indicates that multiple domains were involved in the campaign.

---

## Phase 6 — Threat Intelligence Correlation

The extracted IOCs were validated using external Threat Intelligence.

Findings:

- Both domains were detected as malicious by multiple security vendors.
- WHOIS records showed that both domains were newly registered immediately before the attack.
- One domain was later suspended by its registrar.

These findings strengthened confidence in the investigation.

---

# Timeline Summary

The attack followed a structured sequence:

1. DNS Resolution
2. HTTP Communication
3. HTTP Redirection
4. TLS Encryption
5. Encrypted Data Transfer
6. IOC Validation
7. Attack Attribution

---

# Analyst Assessment

The reconstructed timeline demonstrates a coordinated malware delivery workflow.

The attacker initially exposed a web endpoint over HTTP before redirecting the victim to an encrypted TLS session.

The use of TLS prevented direct payload inspection, but the combination of network evidence, IOC correlation, and Threat Intelligence strongly indicates activity consistent with the SmartApeSG ClickFix campaign delivering Remcos RAT.
