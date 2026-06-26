# Lessons Learned

## Overview

This document summarizes the key technical and operational lessons learned during the investigation of the SmartApeSG ClickFix campaign associated with Remcos RAT.

The purpose is to highlight how the investigation was performed, what indicators proved valuable, and how similar attacks can be detected earlier in the future.

---

# Lesson 1 — Never Trust a Single Indicator

One of the most important lessons from this investigation is that no single indicator was sufficient to conclude malicious activity.

For example:

- DNS queries alone do not indicate compromise.
- A newly observed domain is not automatically malicious.
- An external IP address may host both legitimate and malicious content.

Instead, confidence was achieved by correlating multiple independent sources of evidence.

Evidence correlation included:

- DNS
- HTTP
- TLS
- Endpoint statistics
- WHOIS
- VirusTotal

---

# Lesson 2 — Correlation Is More Valuable Than Individual Artifacts

The investigation demonstrated that meaningful conclusions come from correlating multiple observations.

Example:

DNS Query

↓

HTTP GET

↓

301 Redirect

↓

TLS Handshake

↓

Threat Intelligence

↓

Confirmed IOC

Each artifact individually provides limited information, but together they reconstruct the complete attack chain.

---

# Lesson 3 — HTTPS Does Not Mean Safe

The attacker used HTTPS to protect the delivery of the malicious payload.

Although the payload itself could not be inspected, encrypted communication still revealed valuable metadata such as:

- destination domains
- destination IPs
- TLS certificates
- traffic volume
- communication timing

Encrypted traffic should therefore always be investigated rather than ignored.

---

# Lesson 4 — Metadata Can Be More Valuable Than Payload

Because the malware payload remained encrypted, the investigation relied primarily on metadata.

Useful metadata included:

- DNS records
- User-Agent
- HTTP methods
- URI paths
- TLS certificates
- Connection statistics

This demonstrates that effective network investigations are still possible even without decrypting application data.

---

# Lesson 5 — Threat Intelligence Strengthens Confidence

Threat Intelligence did not initiate the investigation.

Instead, it was used to validate findings that had already been extracted from packet analysis.

This approach reduces false positives and improves confidence in the final assessment.

---

# Lesson 6 — Recently Registered Domains Require Attention

WHOIS analysis revealed that both malicious domains were registered immediately before the campaign.

Newly registered domains frequently appear in phishing campaigns, malware delivery, and command-and-control infrastructure.

Organizations should monitor newly observed domains in internal traffic.

---

# Lesson 7 — Small HTTP Requests Can Lead to Large Incidents

Only a few HTTP packets were observed.

However, those packets initiated the entire attack sequence.

The investigation highlights that attackers often require only minimal unencrypted communication before switching to encrypted channels.

---

# Lesson 8 — User-Agent Can Reveal Automation

The identified User-Agent

curl/8.18.0

suggested that communication was generated programmatically rather than through normal user browsing.

Unexpected command-line tools communicating over HTTP deserve additional investigation.

---

# Lesson 9 — Network Traffic Tells a Story

The packet capture showed that every protocol represented one stage of the attack.

DNS

↓

HTTP

↓

Redirect

↓

TLS

↓

Encrypted Communication

By reconstructing these stages, the complete attack chain became visible.

---

# Lesson 10 — Investigation Should End With Better Detection

The investigation should not end after identifying the malware.

Instead, findings should be converted into:

- IDS rules
- SIEM detections
- Threat Hunting queries
- IOC feeds
- Incident response playbooks

This ensures that future attacks can be detected more quickly.

---

# Analyst Reflection

This investigation reinforced the importance of evidence correlation, structured analysis, and Threat Intelligence validation.

Although the malware payload could not be decrypted, the combination of network artifacts provided sufficient evidence to reconstruct the attack chain with high confidence.

The investigation also demonstrated that effective incident response is not about finding a single malicious packet, but about connecting many small observations into one coherent story.

---

# Key Takeaways

- Correlate evidence before drawing conclusions.
- Treat HTTPS as an investigative opportunity, not a blind spot.
- Validate IOCs with Threat Intelligence.
- Monitor newly registered domains.
- Convert investigation findings into defensive detections.
- Focus on attacker behavior rather than individual packets.
