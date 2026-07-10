# MITRE ATT&CK Mapping

## 🎯 Matrix Framework Classifications

| Framework Dimension | Classification Details |
| :--- | :--- |
| **Tactical Tactic Class** | Credential Access |
| **Technique ID Vector** | [T1003.008 - OS Credential Dumping: /etc/passwd and /etc/shadow](https://attack.mitre.org/techniques/T1003/008/) |
| **Observed Telemetry Footprint** | Unauthorized read hooks on local credential maps, execution of commands targeting administrative files |

---

## 🧩 Threat Profile Description
Adversaries execute credential dumping techniques to obtain cleartext passwords or local cryptographic hashes from operating system storage structures. By compromising these repositories, threat actors can bypass standard authentication barriers, perform offline dictionary guessing attacks, move laterally across shared network domains, or elevate their privileges to a full root-level shell context.

---

## 📊 Detection Evidence Alignment
Wazuh aggregates endpoint agent telemetry to surface indicators of compromise matching the standard matrix taxonomy:
* **File Access Identifiers:** Captures file system read attempts targeting `/etc/passwd` and `/etc/shadow`.
* **Process Attribution:** Maps the precise system user and binary tool utilized during the credential harvesting sequence.

## 🗃️ Telemetry Monitoring Source
The behavioral threat intelligence artifacts were collected and normalized through the following platform paths:
* **Log Ingestion Pipeline:** Wazuh Agent local endpoint monitoring service.
* **Host Telemetry Points:** Linux System Auditing Logs (`auditd`), Core System Event Streams, and File Integrity Event Managers.
