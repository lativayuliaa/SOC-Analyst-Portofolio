# MITRE ATT&CK Mapping

## Technique

### T1071.004 - Application Layer Protocol: DNS

Adversaries may use DNS traffic for command-and-control communications, infrastructure discovery, malware updates, or other malicious purposes.

---

## Tactic

### Command and Control

DNS can be leveraged as a communication channel between compromised systems and attacker-controlled infrastructure.

---

## Detection Evidence

Observed Indicators:

* DNS Queries
* DNS Responses
* NXDOMAIN Responses
* Domain Resolution Activity
* DNS Server Communication

---

## Detection Sources

### Wireshark

* DNS Packet Inspection
* Query Analysis
* Response Analysis

### Suricata IDS

* DNS Event Monitoring
* Network Visibility

---

## Security Relevance

DNS is frequently used by attackers because it is commonly allowed through firewalls and often receives less scrutiny than other protocols.

Monitoring DNS traffic is critical for identifying suspicious communication patterns.

---

## ATT&CK Mapping Summary

| Technique ID | Technique                       |
| ------------ | ------------------------------- |
| T1071.004    | Application Layer Protocol: DNS |

| Tactic              |
| ------------------- |
| Command and Control |
