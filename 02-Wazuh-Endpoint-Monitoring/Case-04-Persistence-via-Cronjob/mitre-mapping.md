# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Persistence |
| **Technique ID Vector** | [T1053.003 - Scheduled Task/Job: Cron](https://attack.mitre.org/techniques/T1053/003/) |
| **Observed Telemetry Footprint** | System spool modification events, write updates to core cron file architectures |

---

## 🧩 Threat Profile Description
Adversaries use scheduling utilities like the Linux `cron` subsystem to guarantee their malicious tooling executes automatically even after a server is restarted, system caches are flushed, or interactive administrative sessions are closed. Because native cron configurations routinely interface directly with high-privilege context shells, securing absolute visibility into system file integrity modifications over these specific configuration repositories is critical to interrupting systemic post-compromise lifecycles.

---

## 📊 SIEM Evidence Integration & Identification Sources
The security telemetry traces mapped to this incident were successfully gathered and aggregated via the following endpoint validation layers:
* **Log Ingestion Pipeline:** Wazuh Agent File Integrity Monitoring (FIM) Engine.
* **Host Telemetry Points:** Linux Core Task Scheduling File Arrays & Whodata Audit Monitoring Channels.

---
*For a complete operational breakdown, enterprise mitigation procedures, and sub-technique definitions, browse the official [MITRE ATT&CK T1053.003 Framework Reference](https://attack.mitre.org/techniques/T1053/003/).*
