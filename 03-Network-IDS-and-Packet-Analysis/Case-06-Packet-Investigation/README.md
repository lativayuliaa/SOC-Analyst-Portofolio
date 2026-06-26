# Case 06 — SmartApeSG ClickFix Campaign (Remcos RAT)

## Overview

This project documents a network forensic investigation of a SmartApeSG ClickFix campaign that resulted in a Remcos RAT infection.

The investigation was performed using Wireshark by analyzing a real-world packet capture (PCAP). Evidence from HTTP, DNS, TLS, and Threat Intelligence sources was correlated to reconstruct the attack chain and identify indicators of compromise (IOCs).

---

## Investigation Objectives

- Identify the victim system
- Identify malicious infrastructure
- Extract Indicators of Compromise (IOCs)
- Reconstruct the attack timeline
- Analyze encrypted network communications
- Validate findings using Threat Intelligence
- Map attacker behavior to the MITRE ATT&CK Framework

---

## Lab Environment

| Component | Description |
|----------|-------------|
| Wireshark | Packet analysis |
| VirusTotal | IOC validation |
| WHOIS | Domain registration analysis |
| DNS Analysis | Infrastructure investigation |

---

## Investigation Workflow

1. Capture Overview
2. Protocol Analysis
3. Endpoint Identification
4. DNS Investigation
5. HTTP Investigation
6. TLS Investigation
7. IOC Extraction
8. Threat Intelligence Validation
9. Attack Timeline Reconstruction
10. MITRE ATT&CK Mapping

---

## Key Findings

### Victim

10.3.12.101

### Malicious Domains

- forcebiturg.com
- retrypoti.top

### Associated IP Addresses

- 159.65.191.64
- 24.199.121.166

### Initial Access

HTTP GET request to:

- /boot
- /proc

using:

```
curl/8.18.0
```

### Network Behavior

- HTTP 301 Redirect
- TLS encrypted communication
- Large encrypted data transfer
- Activity consistent with SmartApeSG ClickFix campaign

---

## Indicators of Compromise

| Type | Value |
|------|-------|
| Victim IP | 10.3.12.101 |
| Domain | forcebiturg.com |
| Domain | retrypoti.top |
| IP Address | 159.65.191.64 |
| IP Address | 24.199.121.166 |
| User-Agent | curl/8.18.0 |

---

## Threat Intelligence Summary

Threat Intelligence validation confirmed that both identified domains were classified as malicious by multiple security vendors.

Additional WHOIS analysis showed that the domains were registered immediately before the observed campaign, a behavior commonly associated with short-lived attacker infrastructure.

---

## Skills Demonstrated

- Network Traffic Analysis
- Packet Analysis
- DNS Investigation
- HTTP Analysis
- TLS Analysis
- IOC Extraction
- Threat Intelligence
- Digital Forensics
- Incident Investigation
- MITRE ATT&CK Mapping

---

## Conclusion

The investigation successfully reconstructed the observed attack chain and identified multiple malicious indicators associated with a SmartApeSG ClickFix campaign.

Although the malware payload itself was encrypted within TLS traffic and could not be extracted directly from the packet capture, network evidence and external Threat Intelligence strongly supported the assessment that the observed activity was consistent with Remcos RAT delivery.

The investigation demonstrates a complete workflow for conducting network-based incident response using Wireshark and publicly available Threat Intelligence resources.
