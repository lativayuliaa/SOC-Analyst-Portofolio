# Detection Engineering

## 📌 Overview

This document describes detection opportunities identified during the investigation of the **SmartApeSG ClickFix** campaign associated with **Remcos RAT**. The objective is to translate investigation findings into actionable detection logic that can be implemented within IDS, SIEM, or Threat Hunting workflows.

---

## 🎯 Detection Opportunities

### 1. Malicious DNS Requests

- **Detection Logic:** Alert when internal hosts perform DNS lookups for `forcebiturg.com` or `retrypoti.top`.
- **Severity:** 🔴 High

### 2. Suspicious HTTP Requests

- **Detection Logic:** Alert when HTTP requests contain `GET /boot` or `GET /proc` directed to `forcebiturg.com`.
- **Severity:** 🔴 High

### 3. Suspicious User-Agent

- **Detection Logic:** Monitor for `curl/8.18.0` or other `curl/*` User-Agent strings originating from internal workstation subnets.
- **Severity:** 🟡 Medium

### 4. HTTP 301 Redirect Pattern

- **Detection Logic:** Alert on the following sequence occurring within a short time window:

  ```
  HTTP Request
      ↓
  HTTP 301 Redirect
      ↓
  HTTPS Connection
      ↓
  Large TLS Session
  ```

- **Severity:** 🟡 Medium

### 5. High-Volume TLS Sessions

- **Detection Logic:** Monitor for unusually large or long-lived TLS sessions immediately following unencrypted HTTP requests.
- **Severity:** 🟡 Medium

### 6. Newly Registered Domains

- **Detection Logic:** Alert when internal endpoints communicate with recently registered domains that have low reputation scores.
- **Severity:** 🔴 High

---

## 🛡️ Suricata Detection Example

```suricata
alert http any any -> any any (
    msg:"Possible SmartApeSG ClickFix Activity";
    content:"forcebiturg.com";
    http.host;
    sid:1000001;
    rev:1;
)
```

---

## 🔍 SIEM & Threat Hunting Strategy

### SIEM Detection

Correlate events that exhibit the following behavioral chain:

- `curl` User-Agent observed
- Initial HTTP request
- HTTP 301 redirect
- Subsequent HTTPS connection
- Large outbound TLS session

This sequence may indicate automated payload retrieval associated with the ClickFix campaign.

### Threat Hunting

Analysts should pivot on the extracted **User-Agent** string (`curl/*`) and investigate:

- Other hosts using the same User-Agent.
- Connections to newly registered or low-reputation domains.
- Similar HTTP → HTTPS redirect patterns.
- Large outbound TLS sessions following HTTP requests.
- Additional indicators associated with the SmartApeSG ClickFix infrastructure.

---

## 🧩 MITRE ATT&CK References

| Tactic | Technique |
| :--- | :--- |
| Command and Control | T1071.001 – Application Layer Protocol: Web Protocols |
| Command and Control | T1071.004 – Application Layer Protocol: DNS |
| Command and Control | T1105 – Ingress Tool Transfer |
