# MITRE ATT&CK Mapping

## Technique 1

### T1565.001 - Stored Data Manipulation

Adversaries may modify files or stored data to alter system behavior, manipulate information, or hide malicious activity.

---

## Technique 2

### T1070.004 - File Deletion

Adversaries may delete files to remove evidence, disrupt operations, or evade detection.

---

## Tactics

### Impact

Modification or deletion of files can affect system integrity and availability.

### Defense Evasion

Attackers may delete files to remove forensic evidence and hinder investigations.

---

## Detection Evidence

Observed Indicators:

* File creation
* File modification
* File deletion
* File integrity alerts

---

## Detection Source

* Wazuh File Integrity Monitoring (FIM)
* Whodata Monitoring
* Linux File System Events
