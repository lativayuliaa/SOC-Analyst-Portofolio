# MITRE ATT&CK Mapping

## Technique

### T1105 - Ingress Tool Transfer

Adversaries may transfer tools, payloads, scripts, or malware from external systems into a target environment.

---

## Tactic

### Command and Control

The attacker transfers content to a system in preparation for further actions.

---

## Detection Evidence

Observed Indicators:

* HTTP GET Requests
* File Transfer Activity
* Payload Download
* Server-to-Client Data Transfer
* Successful HTTP Responses

---

## Detection Sources

### Wireshark

* HTTP Traffic Analysis
* File Transfer Visibility
* Packet Inspection
* TCP Stream Analysis

### Suricata IDS

* HTTP Event Monitoring
* Network Visibility

---

## Security Relevance

File downloads are commonly observed during malware infections and post-exploitation activities.

Monitoring HTTP transfers can help identify suspicious payload delivery and unauthorized tool transfers.

---

## ATT&CK Mapping Summary

| Technique ID | Technique             |
| ------------ | --------------------- |
| T1105        | Ingress Tool Transfer |

| Tactic              |
| ------------------- |
| Command and Control |
