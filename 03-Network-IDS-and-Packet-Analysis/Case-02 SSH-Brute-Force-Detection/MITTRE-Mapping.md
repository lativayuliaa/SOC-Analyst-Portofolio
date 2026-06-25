# MITRE ATT&CK Mapping

## Technique

### T1110 - Brute Force

Adversaries may attempt to gain access to accounts by systematically guessing passwords through repeated authentication attempts.

---

## Tactic

### Credential Access

The attacker attempts to obtain valid credentials through repeated login attempts.

---

## Detection Evidence

Observed Indicators:

* Multiple authentication failures
* Repeated SSH login attempts
* Excessive connections to TCP Port 22
* Password guessing activity

---

## Detection Sources

### Suricata IDS

* SSH Activity Monitoring
* Network-Based Detection

### Wireshark

* TCP Port 22 Analysis
* Connection Frequency Analysis
* Packet Inspection

### Linux Authentication Logs

* Failed Password Events
* Authentication Failures
* SSH Login Attempts

---

## Security Relevance

Brute force attacks are frequently used during the initial access phase of cyber attacks and may result in unauthorized access if successful.

---

## ATT&CK Mapping Summary

| Technique ID | Technique   |
| ------------ | ----------- |
| T1110        | Brute Force |

| Tactic            |
| ----------------- |
| Credential Access |
