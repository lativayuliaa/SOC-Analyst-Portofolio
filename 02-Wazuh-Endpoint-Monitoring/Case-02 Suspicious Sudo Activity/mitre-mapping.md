# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Privilege Escalation |
| **Technique ID Vector** | [T1548.003 - Sudo and Sudo Caching](https://attack.mitre.org/techniques/T1548/003/) |
| **Observed Telemetry Footprint** | Command execution via sudo, root-level shell creation, and PAM system access updates |

---

## 🧩 Threat Profile Description
Adversaries frequently attempt to elevate their system context after securing an initial low-privilege foothold. By exploiting permissive sudo rule sets or abusing cached active terminal sessions, threat actors can bypass application restriction layers, modify critical operating system kernel files, clear forensic log files, and install persistent rootkits.

---

## 📊 SIEM Framework Evidence Alignment
The Wazuh platform provides a native analytical visualization map that dynamically aligns active host agent alerts with the global industry-standard matrix taxonomy. The captured administrative execution parameters correctly populated the privilege escalation technique blocks within the management dashboard console:

![Wazuh MITRE ATT&CK Privilege Escalation Mapping Dashboard](assets/ss-4-mitre-att%26ck.png)

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were ingested and normalized across the following platform detection paths:
* **Log Collection Component:** Wazuh Agent local engine logging pipeline.
* **Host Telemetry Points:** Linux Authentication Subsystem (`auth.log`), Core Sudo Engine logs, and Pluggable Authentication Modules (PAM) logs.
