# Attack Timeline

## 📌 Overview

This timeline reconstructs the **SmartApeSG ClickFix** campaign based on evidence collected from packet capture analysis, DNS investigation, HTTP requests, TLS communications, and Threat Intelligence. The sequence below illustrates the observed attacker activities from initial access through encrypted communications.

---

## ⏱️ Attack Timeline

| Phase | Activity | Evidence |
| :---: | :--- | :--- |
| **1** | Victim initiates a DNS lookup for **forcebiturg.com** | DNS Query |
| **2** | DNS resolves **forcebiturg.com** to **159.65.191.64** | DNS Response |
| **3** | Victim establishes an HTTP connection | TCP Handshake |
| **4** | Victim sends **HTTP GET /boot** | HTTP Request |
| **5** | Victim sends **HTTP GET /proc** | HTTP Request |
| **6** | User-Agent identified as **curl/8.18.0** | HTTP Header |
| **7** | Server responds with **HTTP 301 Moved Permanently** | HTTP Response |
| **8** | Victim follows the redirect to HTTPS | HTTP Redirect |
| **9** | TLS handshake begins | TLS Handshake |
| **10** | TLS certificate reveals **retrypoti.top** | TLS Certificate |
| **11** | DNS resolves **retrypoti.top** to **24.199.121.166** | DNS Response |
| **12** | Large encrypted TLS Application Data is exchanged | TLS Stream |
| **13** | High-volume **PSH, ACK** packets indicate encrypted payload transfer | TCP Stream |
| **14** | Threat Intelligence confirms both domains as malicious | VirusTotal |
| **15** | WHOIS shows both domains were registered shortly before the campaign | WHOIS |

---

## 🔗 Attack Chain

```text
Victim (10.3.12.101)
        │
        ▼
    DNS Query
        │
        ▼
 forcebiturg.com (159.65.191.64)
        │
  HTTP GET /boot
  HTTP GET /proc
        │
301 Moved Permanently
        │
        ▼
 HTTPS Redirect
        │
        ▼
  TLS Handshake
        │
 TLS Certificate
        ▼
retrypoti.top (24.199.121.166)
        │
Encrypted TLS Communication
        │
Large Application Data Transfer
        ▼
Activity Consistent with SmartApeSG ClickFix Campaign
```

---

## 🔍 Attack Phases

### Phase 1 — Infrastructure Discovery

The victim resolved the attacker-controlled domain using DNS.

- **Evidence:** DNS Query & DNS Response
- **Result:** The malicious infrastructure became reachable.

---

### Phase 2 — Initial Web Request

The victim initiated an HTTP connection.

**Observed Requests**

- `GET /boot`
- `GET /proc`

**User-Agent**

- `curl/8.18.0`

This automated tool signature strongly suggests non-browser scripted activity.

---

### Phase 3 — Redirect to HTTPS

The server instructed the victim to switch to HTTPS by returning an **HTTP 301 Moved Permanently** response.

Attackers commonly employ this technique to protect delivery infrastructure and reduce visibility into unencrypted traffic.

---

### Phase 4 — Encrypted Communication

Following the redirect, the victim established an encrypted TLS session.

**Evidence**

- TLS Handshake
- TLS Certificate
- TLS Application Data

This transition significantly reduced visibility into the payload contents while maintaining observable metadata.

---

### Phase 5 — Infrastructure Expansion

TLS inspection identified a second attacker-controlled domain:

- **Domain:** `retrypoti.top`
- **Resolved IP:** `24.199.121.166`

This indicates additional attacker-controlled infrastructure supporting the campaign.

---

### Phase 6 — Threat Intelligence Correlation

The extracted Indicators of Compromise (IOCs) were validated using external Threat Intelligence sources.

**Findings**

- Both domains were identified as malicious.
- WHOIS records showed the domains were newly registered shortly before the campaign.
- The infrastructure characteristics were consistent with the **SmartApeSG ClickFix** activity.

---

## 📌 Investigation Summary

The observed attack sequence followed a typical malware delivery workflow:

1. DNS resolution of attacker-controlled infrastructure.
2. Initial HTTP communication.
3. HTTP 301 redirect to HTTPS.
4. Encrypted TLS communication.
5. Large encrypted data transfer.
6. Threat Intelligence confirmation of malicious infrastructure.

This timeline provides a complete reconstruction of the campaign and serves as a foundation for detection engineering, IOC extraction, and threat hunting activities.
