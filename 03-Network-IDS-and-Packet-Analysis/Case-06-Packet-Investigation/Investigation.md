# Investigation Report

## Case Information

| Item | Value |
|------|-------|
| Case ID | Case-06 |
| Investigation Title | SmartApeSG ClickFix Campaign – Remcos RAT Investigation |
| Analyst | Lativa Yulia Taviani |
| Tool | Wireshark |
| Dataset | 2026-03-12 SmartApeSG ClickFix Activity for Remcos RAT |
| Investigation Type | Network Forensics |
| Status | Completed |

---

# Investigation Objective

The objective of this investigation was to analyze a real-world packet capture associated with a SmartApeSG ClickFix campaign that delivered Remcos RAT.

The investigation focused on identifying the victim system, malicious infrastructure, attack sequence, Indicators of Compromise (IOCs), and validating findings using Threat Intelligence.

---

# Scope

The investigation covered:

- Packet Capture (PCAP) Analysis
- HTTP Traffic Analysis
- DNS Investigation
- TLS Investigation
- IOC Extraction
- Threat Intelligence Validation
- Attack Timeline Reconstruction

---

# Initial Observations

The packet capture contained approximately:

- Total Packets: 70,237
- Capture Duration: 232 seconds
- File Size: 99 MB

Protocol analysis showed that TCP accounted for almost all observed traffic, while HTTP represented only a very small portion.

Most network communication occurred over encrypted TLS sessions.

This immediately suggested that the attack relied on encrypted channels after the initial web request.

---

# Phase 1 – Endpoint Identification

The IPv4 Endpoint statistics identified one internal host that generated the overwhelming majority of network traffic.

## Victim

| Item | Value |
|------|-------|
| IP Address | 10.3.12.101 |

Conversation statistics revealed that this host communicated extensively with an external IP address.

---

# Phase 2 – DNS Investigation

DNS analysis was performed to identify external infrastructure contacted by the victim.

Two domains were identified during the investigation.

| Domain | Resolved IP |
|---------|-------------|
| forcebiturg.com | 159.65.191.64 |
| retrypoti.top | 24.199.121.166 |

These domains became primary Indicators of Compromise (IOCs) because they appeared during malicious communication observed in the packet capture.

---

# Why forcebiturg.com Became the Primary IOC

The investigation did not classify the domain as malicious simply because it appeared in DNS traffic.

Instead, multiple independent pieces of evidence were correlated.

The domain:

- appeared within DNS traffic
- appeared as the HTTP Host header
- received HTTP GET requests
- returned an HTTP 301 redirect
- initiated encrypted TLS communication
- was later validated by Threat Intelligence as malicious

Because multiple sources independently supported the same conclusion, the confidence level for this IOC was considered High.

---

# Phase 3 – HTTP Investigation

HTTP analysis revealed that the victim initiated requests to:

```

GET /boot

GET /proc

```

Host:

```

forcebiturg.com

```

User-Agent:

```

curl/8.18.0

```

The User-Agent indicates that the requests were generated using cURL rather than a normal web browser.

This behavior is consistent with automated download activity commonly observed during malware execution.

---

# Phase 4 – HTTP Redirection

The web server responded with:

```

301 Moved Permanently

```

The response redirected the victim to HTTPS.

This represents the transition from unencrypted HTTP communication to encrypted TLS communication.

---

# Phase 5 – TLS Investigation

Following the HTTP redirect, Wireshark showed a large TLS conversation.

Evidence included:

- TLS Handshake
- TLS Application Data
- Large PSH, ACK packet sequences
- High-volume encrypted communication

Follow TCP Stream confirmed that the payload was encrypted and therefore could not be inspected directly.

---

# Additional Infrastructure

TLS certificate inspection identified another domain:

```

retrypoti.top

```

This domain appeared during encrypted communication and resolved to:

```

24.199.121.166

```

Although the payload itself remained encrypted, the appearance of this domain suggests additional attacker infrastructure used during the campaign.

---

# Threat Intelligence Validation

The extracted Indicators of Compromise were validated using VirusTotal and WHOIS.

## forcebiturg.com

- Multiple security vendors classified the domain as malicious.
- Registered on 12 March 2026.
- Registration date matched the observed attack timeline.

## retrypoti.top

- Multiple security vendors classified the domain as malicious.
- WHOIS status indicated that the domain had later been suspended.

Threat Intelligence strongly supported the findings obtained during packet analysis.

---

# Evidence Correlation

The investigation relied on evidence correlation rather than a single indicator.

Evidence included:

- DNS Queries
- HTTP Requests
- HTTP Redirect
- TLS Communication
- Threat Intelligence
- WHOIS Records

Because these independent artifacts supported one another, confidence in the findings was significantly increased.

---

# Findings

The investigation identified:

- One victim workstation
- Two malicious domains
- Two external IP addresses
- Automated HTTP requests using cURL
- HTTP redirection to HTTPS
- Encrypted TLS communication
- Multiple Indicators of Compromise

The observed behavior is consistent with a SmartApeSG ClickFix campaign delivering Remcos RAT.

---

# Limitations

The malware payload itself could not be extracted from the packet capture because all subsequent communication occurred over encrypted TLS.

Without server private keys or TLS session secrets, payload decryption was not possible.

Therefore, conclusions regarding the malware family rely on:

- Network evidence
- IOC validation
- Dataset context
- Threat Intelligence

---

# Conclusion

The investigation successfully reconstructed the attack chain from initial DNS resolution through encrypted command-and-control style communication.

Although the malware payload remained encrypted, network evidence combined with external Threat Intelligence provided sufficient confidence to conclude that the observed activity was consistent with a SmartApeSG ClickFix campaign delivering Remcos RAT.

The investigation demonstrates a complete network forensic workflow including traffic analysis, IOC extraction, evidence correlation, and Threat Intelligence validation.
