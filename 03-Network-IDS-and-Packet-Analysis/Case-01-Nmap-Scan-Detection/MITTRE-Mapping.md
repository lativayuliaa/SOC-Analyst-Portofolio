# MITRE ATT&CK Mapping

## Technique

### T1046 - Network Service Discovery

Adversaries may scan networks and systems to identify open ports, active services, and potential attack surfaces.

---

## Tactic

### Discovery

The attacker gathers information about the target environment before attempting further actions.

---

## Detection Evidence

Observed Indicators:

* Multiple TCP SYN packets
* Sequential port probing
* Service enumeration attempts
* Network reconnaissance behavior

---

## Detection Sources

### Suricata IDS

* Reconnaissance Detection
* Network Scan Alerts

### Wireshark

* TCP SYN Analysis
* Port Enumeration Verification
* Packet Inspection

---

## Security Relevance

Reconnaissance is often one of the earliest stages of an attack lifecycle and may precede exploitation attempts.
