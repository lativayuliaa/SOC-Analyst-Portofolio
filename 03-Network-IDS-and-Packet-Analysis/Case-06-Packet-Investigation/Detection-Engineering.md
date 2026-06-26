# Detection Engineering

## Overview

This document describes detection opportunities identified during the investigation of the SmartApeSG ClickFix campaign associated with Remcos RAT.

The goal is to translate investigation findings into actionable detection logic that can be implemented in IDS, SIEM, or Threat Hunting workflows.

---

# Detection Opportunities

The investigation identified multiple artifacts that can be used to detect similar attacks in the future.

These artifacts include:

- DNS requests
- HTTP requests
- User-Agent
- TLS communication
- Network behavior
- Indicators of Compromise (IOCs)

---

# Detection Opportunity 1

## Malicious DNS Requests

### Detection Logic

Alert whenever internal hosts perform DNS lookups for:

```
forcebiturg.com
retrypoti.top
```

### Why

These domains were confirmed as malicious through:

- Packet Capture
- Threat Intelligence
- WHOIS

### Severity

High

---

# Detection Opportunity 2

## HTTP Requests

Alert when HTTP requests contain:

```
GET /boot

GET /proc
```

Especially if:

Host:

```
forcebiturg.com
```

### Why

These URIs represent the first observed communication with attacker infrastructure.

### Severity

High

---

# Detection Opportunity 3

## Suspicious User-Agent

Monitor for:

```
curl/8.18.0
```

or

```
curl/*
```

inside workstation traffic.

### Why

Most users normally browse using:

- Chrome
- Edge
- Firefox

Automated HTTP requests from workstations deserve additional investigation.

### Severity

Medium

---

# Detection Opportunity 4

## HTTP 301 Redirect

Alert when:

```
HTTP

↓

301 Redirect

↓

HTTPS

↓

Large TLS Session
```

occurs within a short time window.

### Why

The attacker redirected victims before encrypted payload delivery.

### Severity

Medium

---

# Detection Opportunity 5

## High Volume TLS Session

Monitor for:

- unusually large TLS conversations
- long TLS sessions
- large outbound encrypted traffic

especially immediately following HTTP requests.

### Why

Large encrypted transfers may indicate malware delivery or C2 communication.

### Severity

Medium

---

# Detection Opportunity 6

## Newly Registered Domains

Threat Intelligence should monitor domains that:

- are recently registered
- have low reputation
- suddenly receive internal traffic

### Why

Attackers frequently register domains shortly before campaigns begin.

### Severity

High

---

# Detection Opportunity 7

## Threat Intelligence Matching

Automatically compare:

- Domains
- IPs
- URLs

against Threat Intelligence feeds.

Known IOCs include:

```
forcebiturg.com

retrypoti.top

159.65.191.64

24.199.121.166
```

### Severity

High

---

# Suricata Detection Example

Example rule:

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

# SIEM Detection Ideas

Possible detection logic:

- DNS lookup for malicious domains
- HTTP GET to suspicious URI
- cURL User-Agent from workstation
- HTTP redirect followed by large TLS traffic
- Multiple Threat Intelligence IOC matches

---

# Threat Hunting Ideas

Threat hunters should search for:

- Other hosts contacting the same domains
- Same User-Agent across the environment
- Similar TLS communication patterns
- Connections to newly registered domains
- Similar HTTP URI patterns

---

# Defensive Recommendations

Following this investigation, defenders should:

- Block malicious domains
- Block malicious IPs
- Deploy IDS signatures
- Update Threat Intelligence feeds
- Create SIEM detection rules
- Hunt for historical IOC matches
- Monitor newly registered domains

---

# Analyst Notes

This investigation demonstrates that effective detection is achieved by combining multiple weak indicators rather than relying on a single IOC.

Although the malware payload remained encrypted, the attack generated numerous observable network artifacts that together provide reliable detection opportunities.
