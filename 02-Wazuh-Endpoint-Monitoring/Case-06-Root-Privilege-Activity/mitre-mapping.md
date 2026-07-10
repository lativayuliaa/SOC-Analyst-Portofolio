# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Technique 1 | Technique 2 |
| :--- | :--- | :--- |
| **Tactical Tactic Class** | Privilege Escalation / Persistence | Privilege Escalation / Defense Evasion |
| **Technique ID Vector** | [T1078 - Valid Accounts](https://attack.mitre.org/techniques/T1078/) | [T1548.003 - Sudo and Sudo Caching](https://attack.mitre.org/techniques/T1548/003/) |
| **Observed Telemetry Footprint** | Execution of administrative commands using active user accounts | Abuse of sudo binary permissions to spawn root interactive shell contexts |

---

## 🧩 Threat Profile Description
Adversaries leverage valid local accounts and privilege elevation mechanics to blend malicious activity with normal day-to-day administrative operations. By utilizing default system binary tools like `sudo`, attackers can execute high-risk commands while evading simplistic signature detection layers that look exclusively for traditional binary malware payloads. Securing deep visibility into terminal shell loops is crucial for mapping behavioral anomalies after a privilege boundary is crossed.

---

## 📊 Detection Evidence Alignment
The telemetry gathered by Wazuh agents maps directly to specific components of the enterprise matrix taxonomy:
* **Privilege Elevation Vectors:** Logs the use of authorization management subsystems to shift active roles.
* **Post-Escalation Auditing:** Records actions targeting core operating system configuration maps and local credential files.

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were ingested and normalized through the following platform paths:
* **Log Collection Pipeline:** Wazuh Agent endpoint monitoring engine.
* **Host Telemetry Points:** Linux Core Subsystem Logs (`auth.log`), Sudo History Records, and PAM Session Verification Streams.
