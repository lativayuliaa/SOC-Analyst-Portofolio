# MITRE ATT&CK Mapping

## Technique

### T1003.008 - OS Credential Dumping: /etc/passwd and /etc/shadow

Adversaries may attempt to obtain credentials by accessing password storage files on Linux systems.

---

## Tactic

### Credential Access

The attacker attempts to obtain account credentials and password hashes for further exploitation.

---

## Detection Evidence

Observed Indicators:

* Access to /etc/passwd
* Access to /etc/shadow
* Credential-related file activity
* Privileged file access

---

## Detection Source

* Linux System Logs
* Wazuh Agent Telemetry
* File Monitoring Events
