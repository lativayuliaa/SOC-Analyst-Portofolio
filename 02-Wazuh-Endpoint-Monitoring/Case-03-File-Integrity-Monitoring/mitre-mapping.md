# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Technique 1 | Technique 2 |
| :--- | :--- | :--- |
| **Tactical Tactic Class** | Impact | Defense Evasion |
| **Technique ID Vector** | [T1565.001 - Stored Data Manipulation](https://attack.mitre.org/techniques/T1565/001/) | [T1070.004 - File Deletion](https://attack.mitre.org/techniques/T1070/004/) |
| **Observed Telemetry Footprint** | Content appending modifications on localized xlsx assets | Ingress file deletion, clearing target artifact footprint footprints |

---

## 🧩 Threat Profile Description
Adversaries use data manipulation and structural deletion techniques to compromise operational integrity or cover their tracks. During cleanup phases, actors purge staging directory areas, tool payloads, and system logs to hinder investigations. Utilizing kernel-level auditing hooks helps capture these operations, ensuring changes can be attributed back to an originating account even if the target file is destroyed.

---

## 📊 SIEM Framework Evidence Alignment
The Wazuh engine features built-in compliance visualization matrices that automatically align live client host alert signatures with the enterprise MITRE ATT&CK standard taxonomies. The parsed file creation and manipulation events successfully populated the corresponding technique blocks within the analytics engine panel:

![Wazuh MITRE ATT&CK Matrix FIM Mapping Console](assets/ss-7-mitre-att%26ck.png)

## 🗃️ Telemetry Monitoring Source
Threat intelligence data artifacts were ingested and normalized through the following pipeline paths:
* **Log Pipeline Layer:** Wazuh Agent Local File Integrity Monitoring (FIM) Daemon.
* **Host Telemetry Points:** Linux Kernel Auditing Framework (`auditd` hooks) & Whodata Security Audit Streams.
